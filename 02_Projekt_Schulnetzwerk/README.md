# Projekt Schulnetzwerk

In diesem Projekt habe ich ein Schulnetzwerk mit Hauptstandort und Aussenstelle aufgebaut und dokumentiert. Die Umsetzung erfolgte in Cisco Packet Tracer. Ziel war es, ein strukturiertes Netzwerk mit VLAN-Segmentierung, WLAN-/Gastbereich und sicherer VPN-Verbindung zwischen den Standorten zu planen, umzusetzen und zu validieren.

## Kurzüberblick

| Bereich | Inhalt | Link |
| --- | --- | --- |
| Ausgangslage und Ziele | Szenario, Projektziele und Anforderungen aus Modul 145 | [01_Ausgangslage_und_Ziele](01_Ausgangslage_und_Ziele/README.md) |
| Netzwerkdokumentation | Topologie, Geräteliste, IP-Adressierung, VLAN-Übersicht und Sicherheitskonzept | [02_Netzwerkdokumentation](02_Netzwerkdokumentation/README.md) |
| VLAN | VLAN-Konzept, Konfiguration, Trunking, Inter-VLAN-Routing und Tests | [03_VLAN](03_VLAN/README.md) |
| WLAN | WLAN-Konzept, SSID-/VLAN-Mapping, Sicherheit und Tests | [04_WLAN](04_WLAN/README.md) |
| VPN | IPsec Site-to-Site-VPN, Konfiguration und Nachweise | [05_VPN](05_VPN/README.md) |
| Test und Validierung | Testplan, Testprotokoll und Troubleshooting | [06_Test_und_Validierung](06_Test_und_Validierung/README.md) |
| Reflexion | Lernprozess, Probleme/Lösungen und Fazit | [07_Reflexion](07_Reflexion/README.md) |
| Screenshots | Beweise zu VLAN, WLAN und VPN | [assets/screenshots/README.md](assets/screenshots/README.md) |
| Diagramme | Netzwerk-Topologie | [assets/diagramme](assets/diagramme/) |
| Packet Tracer | Finale Projektdatei | [../04_PacketTracer/projekt_schulnetzwerk.pkt](../04_PacketTracer/projekt_schulnetzwerk.pkt) |

## Netzwerkidee

Das Netzwerk besteht aus:

- einem Hauptstandort mit Server, Lehrer-, Schüler-, Admin- und WLAN-/Gastbereich
- einer Aussenstelle mit eigenem Standortnetz
- einem simulierten WAN-/Internet-Bereich
- einer Site-to-Site-VPN-Verbindung zwischen den beiden Standorten

Die Benutzergruppen werden über VLANs logisch getrennt. Der WLAN-/Gastbereich ist einem eigenen Bereich zugeordnet, damit Gastgeräte nicht unnötig Zugriff auf interne Ressourcen erhalten. Die Standortverbindung wird über IPsec abgesichert.

## Wichtigste Nachweise

| Nachweis | Beschreibung |
| --- | --- |
| [Netzwerk-Topologie](assets/diagramme/netzwerk_topologie.png) | Übersicht über Hauptstandort, Aussenstelle, WAN, VLANs und Geräte |
| [Draw.io-Diagramm](assets/diagramme/netzwerk_diagram.drawio) | Bearbeitbare Version des Netzwerkdiagramms |
| [Packet-Tracer-Datei](../04_PacketTracer/projekt_schulnetzwerk.pkt) | Finale Projektdatei für die technische Umsetzung |
| [VLAN-Screenshots](assets/screenshots/README.md#vlan-nachweise) | VLAN-Liste, Trunk, Access-Ports und Ping-Test |
| [WLAN-Screenshots](assets/screenshots/README.md#wlan-nachweise) | WLAN-Topologie und Access-Point-Sicherheit |
| [VPN-Screenshots](assets/screenshots/README.md#vpn-nachweise) | ACLs, Crypto Maps, ISAKMP, IPsec und HTTPS-Test |
| [Testprotokoll](06_Test_und_Validierung/testprotokoll.md) | Zusammenfassung der durchgeführten Tests |
| [Troubleshooting](06_Test_und_Validierung/troubleshooting.md) | Mögliche Fehler und passende Massnahmen |

## Stand der Umsetzung

| Thema | Stand |
| --- | --- |
| Netzwerkdokumentation | ausgearbeitet |
| VLAN | konfiguriert, dokumentiert und mit Screenshots belegt |
| WLAN | dokumentiert und mit AP-Screenshots belegt |
| VPN | konfiguriert, dokumentiert und mit Screenshots belegt |
| Test und Validierung | Testplan, Testprotokoll und mögliche Fehler dokumentiert |
| Monitoring | separat im Repository vorgesehen |

## Bewertungsbezug

Mit diesem Projekt decke ich die zentralen Kompetenzbereiche aus Modul 145 ab: Netzwerkdokumentation, VLAN, WLAN, VPN, Validierung und Behandlung von Fehlersymptomen. Die Dokumentation ist so aufgebaut, dass die technische Umsetzung und die Beweise direkt auffindbar sind.
