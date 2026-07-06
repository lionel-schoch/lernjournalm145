# Theorie

## Was ist Monitoring?

Monitoring bedeutet, dass ein Netzwerk laufend überwacht wird. Ziel ist es, Störungen früh zu erkennen, die Verfügbarkeit zu prüfen und technische Werte nachvollziehbar auszuwerten.

Im Modul 145 ist Monitoring wichtig, weil ein Netzwerk nicht nur aufgebaut, sondern auch betrieben werden muss. Dazu gehört, dass ich erkenne, ob wichtige Verbindungen, Geräte und Dienste verfügbar sind.

## Relevante Werte für mein Projekt

Für mein Schulnetzwerk sind besonders diese Werte sinnvoll:

| Wert | Bedeutung |
| --- | --- |
| Erreichbarkeit | Prüft, ob Router, Server oder VPN-Gegenstellen erreichbar sind. |
| Latenz | Zeigt, wie lange Pakete bis zur Gegenstelle benötigen. |
| Paketverlust | Zeigt, ob Pakete auf dem Weg verloren gehen. |
| Interface-Status | Zeigt, ob wichtige Ports aktiv sind. |
| VPN-Status | Zeigt, ob ein Tunnel aufgebaut ist. |
| VPN-Traffic | Zeigt, ob über den Tunnel Daten gesendet und empfangen werden. |

## Monitoring in Cisco Packet Tracer

Cisco Packet Tracer eignet sich gut zum Simulieren und Testen von Netzwerken. Für echtes Live-Monitoring mit Grafana ist Packet Tracer jedoch nur eingeschränkt geeignet, da die simulierten Geräte keine realistische SNMP-, API- oder Prometheus-Schnittstelle bereitstellen.

Deshalb überwache ich das VPN in Packet Tracer über CLI-Befehle und Funktionstests:

```text
show crypto isakmp sa
show crypto ipsec sa
show crypto map
show access-lists
show ip route
ping
```

Diese Befehle zeigen, ob Routing, VPN Phase 1, VPN Phase 2 und Datenverkehr funktionieren.

## Monitoring mit Grafana

Grafana visualisiert Messwerte. Grafana sammelt die Daten nicht selbst, sondern zeigt Daten aus anderen Quellen an. Typische Datenquellen sind:

| Datenquelle | Zweck |
| --- | --- |
| Prometheus | Zeitreihen-Monitoring und Metriken |
| Node Exporter | Systemwerte eines Linux-Servers |
| WireGuard Exporter | Messwerte eines WireGuard-VPNs |
| Loki | Logdaten |
| InfluxDB | Zeitreihendaten |

Für mein Projekt ist die sinnvollste Variante ein zusätzliches reales VPN-Lab mit WireGuard, Prometheus und Grafana. Packet Tracer bleibt die Netzwerksimulation, während WireGuard/Grafana als Monitoring-Erweiterung dient.

## Fazit

Packet Tracer zeigt mir, ob die Konfiguration grundsätzlich funktioniert. Grafana eignet sich dagegen für echtes Monitoring mit Messwerten über Zeit. Deshalb dokumentiere ich beide Ansätze: Packet-Tracer-Nachweise für das Schulnetzwerk und eine Schritt-für-Schritt-Anleitung für ein realistisches VPN-Monitoring mit Grafana.
