# Monitoring-Konzept

## Ziel

Ich möchte die VPN-Verbindung überwachen und nachvollziehbar auswerten. Da Cisco Packet Tracer keine echte Schnittstelle für Grafana bereitstellt, trenne ich das Monitoring-Konzept in zwei Teile:

1. Monitoring im Packet-Tracer-Projekt über CLI und Funktionstests
2. echtes Monitoring-Lab mit WireGuard, Prometheus und Grafana

## Variante 1: Monitoring im Packet Tracer

Im Packet-Tracer-Projekt prüfe ich den VPN-Zustand direkt auf den Routern.

| Prüfpunkt | Befehl | Aussage |
| --- | --- | --- |
| Routing | `show ip route` | Prüft, ob lokale Netze, WAN-Netze und Default Routes vorhanden sind. |
| VPN Phase 1 | `show crypto isakmp sa` | Prüft, ob die ISAKMP Security Association aktiv ist. |
| VPN Phase 2 | `show crypto ipsec sa` | Prüft, ob IPsec-SAs aktiv sind und Paketzähler steigen. |
| VPN-Regeln | `show access-lists` | Prüft, ob der interessante Traffic erkannt wird. |
| VPN-Zuordnung | `show crypto map` | Prüft Peer, ACL, Transform-Set und Interface. |
| Funktion | Ping oder HTTPS-Test | Prüft, ob ein Dienst über die Standortverbindung erreichbar ist. |

## Variante 2: Grafana-Monitoring mit WireGuard

Für echtes Grafana-Monitoring verwende ich ein separates Mini-Lab mit WireGuard. WireGuard eignet sich gut, weil es einfach einzurichten ist und klare Messwerte liefert.

### Aufbau

```text
VPN-Client  <---- WireGuard ---->  Ubuntu-VM
                                      |
                                      +-- Prometheus
                                      +-- Grafana
                                      +-- Node Exporter
                                      +-- WireGuard Exporter
```

## Messwerte

| Messwert | Bedeutung | Beispiel-Grenzwert |
| --- | --- | --- |
| Peer online/offline | Zeigt, ob der VPN-Peer erreichbar ist. | Alarm, wenn länger als 5 Minuten kein Handshake erfolgt |
| Last Handshake | Zeitpunkt der letzten VPN-Kommunikation | Warnung ab 300 Sekunden |
| Received Bytes | Empfangener Traffic über VPN | Auffälligkeit bei dauerhaft 0 Bytes |
| Transmitted Bytes | Gesendeter Traffic über VPN | Auffälligkeit bei dauerhaft 0 Bytes |
| Latenz | Antwortzeit zur Gegenstelle | Warnung ab 100 ms im Lab |
| Paketverlust | Stabilität der Verbindung | Warnung ab 1 % Verlust |
| CPU/RAM Server | Belastung des VPN-Servers | Warnung ab 80 % CPU |

## Schritt-für-Schritt-Anleitung: WireGuard + Grafana

### Schritt 1: Ubuntu-VM vorbereiten

Eine kleine Ubuntu-VM reicht aus. Empfehlung:

| Ressource | Empfehlung |
| --- | --- |
| CPU | 2 Kerne |
| RAM | 2 GB |
| Speicher | 20 GB |
| Netzwerk | Bridged oder NAT mit Portweiterleitung |

Danach System aktualisieren:

```bash
sudo apt update
sudo apt upgrade -y
```

### Schritt 2: Docker installieren

```bash
sudo apt install -y docker.io docker-compose-plugin
sudo systemctl enable --now docker
sudo usermod -aG docker $USER
```

Danach einmal abmelden und wieder anmelden.

### Schritt 3: WireGuard installieren

```bash
sudo apt install -y wireguard
```

Server-Schlüssel erstellen:

```bash
wg genkey | tee server_private.key | wg pubkey > server_public.key
```

Client-Schlüssel erstellen:

```bash
wg genkey | tee client_private.key | wg pubkey > client_public.key
```

### Schritt 4: WireGuard-Server konfigurieren

Datei `/etc/wireguard/wg0.conf` erstellen:

```ini
[Interface]
Address = 10.50.0.1/24
ListenPort = 51820
PrivateKey = <SERVER_PRIVATE_KEY>

[Peer]
PublicKey = <CLIENT_PUBLIC_KEY>
AllowedIPs = 10.50.0.2/32
```

VPN starten:

```bash
sudo systemctl enable --now wg-quick@wg0
sudo wg
```

### Schritt 5: Client konfigurieren

Auf dem Client wird eine WireGuard-Konfiguration erstellt:

```ini
[Interface]
Address = 10.50.0.2/24
PrivateKey = <CLIENT_PRIVATE_KEY>

[Peer]
PublicKey = <SERVER_PUBLIC_KEY>
Endpoint = <SERVER_IP>:51820
AllowedIPs = 10.50.0.0/24
PersistentKeepalive = 25
```

Nach dem Verbinden testen:

```bash
ping 10.50.0.1
```

### Schritt 6: Prometheus und Grafana starten

Projektordner erstellen:

```bash
mkdir ~/vpn-monitoring
cd ~/vpn-monitoring
```

Datei `docker-compose.yml` erstellen:

```yaml
services:
  prometheus:
    image: prom/prometheus
    container_name: prometheus
    ports:
      - "9090:9090"
    volumes:
      - ./prometheus.yml:/etc/prometheus/prometheus.yml

  grafana:
    image: grafana/grafana
    container_name: grafana
    ports:
      - "3000:3000"
```

Datei `prometheus.yml` erstellen:

```yaml
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: "prometheus"
    static_configs:
      - targets: ["prometheus:9090"]
```

Starten:

```bash
docker compose up -d
```

Grafana öffnen:

```text
http://localhost:3000
```

Standard-Login:

```text
Benutzer: admin
Passwort: admin
```

### Schritt 7: WireGuard-Metriken ergänzen

Für die Abgabe reicht es, das Konzept und die Schritte zu dokumentieren. Für echte WireGuard-Metriken kann zusätzlich ein WireGuard Exporter eingebunden werden. Dieser liest Werte wie Handshake, Traffic und Peer-Status aus und stellt sie Prometheus bereit.

Alternativ können Messwerte zuerst manuell erfasst werden:

- `sudo wg`
- Ping-Zeiten
- Paketverlust
- gesendete/empfangene Bytes

Diese Werte können anschliessend in `messwerte.md` dokumentiert und in Grafana oder Excel visualisiert werden.

## Fazit

Für Packet Tracer nutze ich CLI-Nachweise. Für echtes Monitoring mit Grafana ist ein zusätzliches WireGuard-Lab am sinnvollsten. Damit kann ich den Unterschied zwischen Simulation und produktionsnahem Monitoring sauber erklären.
