# Anforderungen

## Quellen

Die Anforderungen wurden aus folgenden Quellen abgeleitet:

- Modulrepository: [ch-tbz-it/Stud/m145](https://gitlab.com/ch-tbz-it/Stud/m145)
- Kompetenzmatrix im GitLab-Repository
- Bewertungsraster `M145-Bewertungsraster-Protected 1 (1).xlsx`

## Modulanforderungen

Das Modul 145 verlangt, dass ein Netzwerk betrieben und erweitert wird. Dazu gehören gemäss GitLab-Repository insbesondere:

- Netzwerk überwachen und Ergebnisse interpretieren
- Netzwerk nach Vorgabe mit VLAN erweitern
- Netzwerk nach Vorgabe mit WLAN erweitern
- entfernte lokale Netze sicher verbinden
- Fehlersymptome systematisch behandeln
- Resultate dokumentieren und reflektieren

## Bewertungsanforderungen

| Kompetenz | Erwartung | Umsetzung im Projekt |
| --- | --- | --- |
| A1 Netzwerkdokumentation | Selbständig eine Netzwerkdokumentation nach gängigen Standards erstellen. | Topologie, Geräteliste, IP-Adressierung, VLAN-Übersicht und Sicherheitskonzept wurden dokumentiert. |
| B1 Überwachung und Auswertung | Relevante Datenquellen und Parameter bestimmen, Grenzwerte begründen und Ergebnisse interpretieren. | Monitoring wird über Test- und Validierungsdokumentation vorbereitet; mögliche Parameter werden beschrieben. |
| C1 Fehlersymptome | Fehler systematisch erfassen, analysieren und Massnahmen einleiten. | Typische Fehlerfälle werden im Troubleshooting dokumentiert. |
| D1 VLAN | Logische Netzwerkkonzepte entwickeln und umsetzen. | VLANs für Lehrer, Schüler, WLAN/Gast und Administration wurden dokumentiert und getestet. |
| E1 WLAN | WLAN-Infrastruktur evaluieren, konfigurieren und Sicherheitsstandards berücksichtigen. | WLAN-/Gastbereich ist als eigener Bereich mit VLAN-Zuordnung dokumentiert und mit AP-Screenshots belegt. |
| F1 VPN | VPN-Lösungen beurteilen und eine sichere Standortverbindung in Betrieb nehmen. | Site-to-Site-IPsec-VPN wurde dokumentiert und mit Screenshots nachgewiesen. |
| Z1 Dokumentation | Themen strukturiert, handlungsorientiert und mit Resultaten dokumentieren. | Repository ist nach Themen gegliedert und enthält Screenshots als Beweise. |

## Funktionale Anforderungen

| Nr. | Anforderung | Muss / Soll | Status |
| --- | --- | --- | --- |
| FA-01 | Hauptstandort und Aussenstelle müssen über Router verbunden sein. | Muss | umgesetzt |
| FA-02 | Das Hauptnetz muss in mehrere Benutzergruppen segmentiert sein. | Muss | umgesetzt |
| FA-03 | VLAN 10 muss für Lehrergeräte verwendet werden. | Muss | umgesetzt |
| FA-04 | VLAN 20 muss für Schülergeräte verwendet werden. | Muss | umgesetzt |
| FA-05 | VLAN 30 soll für WLAN/Gast verwendet werden. | Soll | dokumentiert / umgesetzt |
| FA-06 | VLAN 40 muss für Administration verwendet werden. | Muss | umgesetzt |
| FA-07 | Ein Trunk-Port muss die relevanten VLANs transportieren. | Muss | umgesetzt |
| FA-08 | Der VPN-Tunnel muss zwischen den Standortroutern aufgebaut werden. | Muss | umgesetzt |
| FA-09 | Ein Client der Aussenstelle muss einen Dienst am Hauptstandort erreichen. | Muss | umgesetzt |
| FA-10 | Tests müssen dokumentiert werden. | Muss | umgesetzt / in Bearbeitung |

## Nichtfunktionale Anforderungen

| Bereich | Anforderung |
| --- | --- |
| Sicherheit | Interne Bereiche sollen logisch getrennt werden. Gast- und WLAN-Geräte sollen nicht unnötig Zugriff auf interne Bereiche erhalten. |
| Nachvollziehbarkeit | Alle wichtigen Konfigurationen und Testergebnisse sollen mit Markdown und Screenshots dokumentiert werden. |
| Wartbarkeit | IP-Adressen, VLANs und Geräte sollen so dokumentiert sein, dass spätere Änderungen möglich sind. |
| Verfügbarkeit | Die Standortverbindung soll über Routing und VPN nachvollziehbar funktionieren. |
| Qualität | Die Dokumentation soll strukturiert sein und den Aufbau des Repositories widerspiegeln. |

## Offene oder eingeschränkte Punkte

Einige Bereiche sind in Packet Tracer nur eingeschränkt realistisch abbildbar:

- echtes Monitoring mit Langzeitwerten
- reale WLAN-Signalstärke und Kanalplanung
- produktive VPN-Performance
- echte Sicherheitsprüfung mit Firewall-Logs

Diese Punkte werden als Grenzen des Projekts dokumentiert und im Test- sowie Reflexionsteil berücksichtigt.
