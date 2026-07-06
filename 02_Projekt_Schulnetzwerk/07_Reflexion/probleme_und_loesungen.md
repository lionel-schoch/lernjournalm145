# Probleme und Lösungen

## Übersicht

Während des Projekts sind mehrere typische Netzwerkprobleme aufgetreten oder wurden als mögliche Fehlerquellen erkannt. Ich habe sie hier dokumentiert, damit nachvollziehbar ist, wie ich bei der Fehlersuche vorgehen würde.

## Problem 1: VLAN-Zuordnung

| Punkt | Beschreibung |
| --- | --- |
| Problem | Ein Client befindet sich im falschen VLAN oder erreicht andere Geräte nicht. |
| Ursache | Der Switchport ist dem falschen Access VLAN zugeordnet. |
| Analyse | `show interfaces switchport` und `show vlan brief` prüfen. |
| Lösung | Switchport korrekt als Access-Port konfigurieren und dem richtigen VLAN zuordnen. |
| Nachweis | VLAN-Screenshots im Screenshot-Ordner. |

## Problem 2: Trunk transportiert VLAN nicht

| Punkt | Beschreibung |
| --- | --- |
| Problem | VLANs funktionieren lokal, aber nicht über den Uplink. |
| Ursache | Der Trunk ist nicht aktiv oder erlaubt nicht alle benötigten VLANs. |
| Analyse | `show interfaces trunk` prüfen. |
| Lösung | Trunk konfigurieren und erlaubte VLANs kontrollieren. |
| Nachweis | Trunk-Screenshot von `SW-CORE-01`. |

## Problem 3: VPN baut nicht auf

| Punkt | Beschreibung |
| --- | --- |
| Problem | Die Standortverbindung funktioniert nicht. |
| Ursache | Falscher Peer, falsche ACL, fehlende Route oder nicht passende IPsec-Parameter. |
| Analyse | `show crypto isakmp sa`, `show crypto ipsec sa`, `show access-lists`, `show ip route`. |
| Lösung | Routing, ACL und Crypto Map kontrollieren und korrigieren. |
| Nachweis | VPN-Screenshots und HTTPS-Test. |

## Problem 4: WLAN-Client im falschen Bereich

| Punkt | Beschreibung |
| --- | --- |
| Problem | Ein WLAN-Client erhält eine falsche Netzzuordnung. |
| Ursache | SSID oder Switchport des Access Points ist nicht dem richtigen VLAN zugeordnet. |
| Analyse | AP-Konfiguration und Switchport prüfen. |
| Lösung | SSID/VLAN-Mapping korrigieren und AP-Port dem VLAN 30 zuordnen. |
| Nachweis | WLAN-Screenshots und WLAN-Dokumentation. |

## Problem 5: Monitoring mit Grafana in Packet Tracer

| Punkt | Beschreibung |
| --- | --- |
| Problem | Grafana kann Packet-Tracer-Router nicht direkt überwachen. |
| Ursache | Packet Tracer stellt keine echte Prometheus-, SNMP- oder API-Schnittstelle bereit. |
| Analyse | Unterschied zwischen Simulation und echter Monitoring-Umgebung prüfen. |
| Lösung | Packet Tracer mit CLI/Screenshots validieren und für Grafana ein separates WireGuard-Lab dokumentieren. |
| Nachweis | Monitoring-Konzept im Ordner `03_Monitoring_Auswertung`. |

## Fazit

Die wichtigsten Fehlerquellen liegen bei VLANs, Trunks, Routing, VPN-Parametern und WLAN-Zuordnung. Mit klaren Diagnosebefehlen kann ich diese Probleme strukturiert eingrenzen und beheben.
