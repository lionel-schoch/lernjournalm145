# Monitoring und Auswertung

Dieser Bereich ist für den Kompetenzteil **Überwachung und Auswertung** vorgesehen. Hier dokumentiere ich Monitoring-Grundlagen, mein Monitoring-Konzept, Messwerte, Auswertung und Reflexion.

## Dateien

| Datei | Inhalt |
| --- | --- |
| [theorie.md](theorie.md) | Grundlagen zu Monitoring und relevanten Netzwerkparametern |
| [monitoring_konzept.md](monitoring_konzept.md) | geplante Überwachung, Datenquellen und Grenzwerte |
| [messwerte.md](messwerte.md) | erfasste oder simulierte Messwerte |
| [auswertung.md](auswertung.md) | Interpretation der Messwerte |
| [reflexion.md](reflexion.md) | persönliche Auswertung des Monitoring-Teils |

## Schritt-für-Schritt-Anleitung

Die konkrete Anleitung für ein VPN-Monitoring mit WireGuard, Prometheus und Grafana ist hier dokumentiert:

[Monitoring-Konzept: WireGuard + Grafana](monitoring_konzept.md#schritt-für-schritt-anleitung-wireguard--grafana)

## Umsetzungsstand

Ich konnte ein WireGuard-VPN auf der Ubuntu-VM erstellen und starten. Der Befehl `sudo wg` zeigt das Interface `wg0`, den Public Key, den Listening Port `51820` sowie einen Peer mit der erlaubten IP `10.50.0.2/32`.

![WireGuard VPN Status](assets/wireguard_vpn_status.png)

Das eigentliche Monitoring mit Grafana konnte ich zeitlich nicht mehr vollständig umsetzen. Deshalb dokumentiere ich in diesem Bereich, wie das Monitoring fachlich aufgebaut worden wäre und welche Messwerte für eine spätere Umsetzung relevant sind.

## Bezug zum Projekt

Im Schulnetzwerk sind besonders diese Werte relevant:

- Erreichbarkeit der Router und Server
- Latenz zwischen Hauptstandort und Aussenstelle
- Paketverlust bei Standortverbindungen
- Status der wichtigen Interfaces
- VPN-Verfügbarkeit
- WLAN-/Gastbereich als separater Netzwerkbereich

Dieser Bereich ergänzt die technische Projektdokumentation im Ordner [02_Projekt_Schulnetzwerk](../02_Projekt_Schulnetzwerk/README.md).
