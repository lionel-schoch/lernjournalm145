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

## Bezug zum Projekt

Im Schulnetzwerk sind besonders diese Werte relevant:

- Erreichbarkeit der Router und Server
- Latenz zwischen Hauptstandort und Aussenstelle
- Paketverlust bei Standortverbindungen
- Status der wichtigen Interfaces
- VPN-Verfügbarkeit
- WLAN-/Gastbereich als separater Netzwerkbereich

Dieser Bereich ergänzt die technische Projektdokumentation im Ordner [02_Projekt_Schulnetzwerk](../02_Projekt_Schulnetzwerk/README.md).
