# Ausgangslage

## Projektszenario

Für das Modul 145 wurde ein Schulnetzwerk in Cisco Packet Tracer aufgebaut und dokumentiert. Das Netzwerk besteht aus einem Hauptstandort und einer Aussenstelle. Beide Standorte sollen miteinander kommunizieren können, dabei aber logisch getrennte Benutzergruppen, eine nachvollziehbare IP-Adressierung und eine sichere Standortverbindung verwenden.

Der Hauptstandort enthält mehrere Bereiche für Lehrpersonen, Schüler, Administration, Server und WLAN/Gastzugang. Die Aussenstelle enthält ein kleineres Standortnetz mit Lehrer- und Schülergerät. Die Verbindung zwischen den Standorten erfolgt über ein simuliertes Internet-/WAN-Segment.

## Modulbezug

Das Projekt orientiert sich an den Anforderungen des Moduls 145. Gemäss Modulbeschreibung im GitLab-Repository steht im Zentrum, die Performance und Verfügbarkeit eines Netzwerks zu überwachen, Ergebnisse zu interpretieren, Netzwerke mit WLAN/VLAN zu erweitern und entfernte lokale Netze sicher zu verbinden.

Quelle: [GitLab Modul 145](https://gitlab.com/ch-tbz-it/Stud/m145)

## Bewertungsbezug

Aus dem Bewertungsraster ergeben sich folgende zentrale Kompetenzbereiche:

| Bereich | Bedeutung für dieses Projekt |
| --- | --- |
| Netzwerkdokumentation | Topologie, Geräteliste, IP-Adressierung, VLAN-Übersicht und Sicherheitskonzept müssen nachvollziehbar dokumentiert sein. |
| Überwachung und Auswertung | Relevante Netzwerkparameter sollen gemessen, beobachtet oder begründet werden können. |
| Behandlung von Fehlersymptomen | Fehler sollen systematisch beschrieben, analysiert und mit passenden Massnahmen behoben werden. |
| VLAN | Das Netzwerk soll logisch segmentiert und fachgerecht umgesetzt werden. |
| WLAN | Der WLAN-/Gastbereich soll geplant, einem VLAN zugeordnet und sicher beschrieben werden. |
| VPN | Die entfernten Standortnetze sollen sicher über eine VPN-Verbindung verbunden werden. |
| Dokumentation | Die Resultate sollen strukturiert, nachvollziehbar und mit Beweisen dokumentiert sein. |

## Ausgangsnetz

Das geplante Schulnetz nutzt folgende Standorte:

| Standort | Zweck | Wichtige Komponenten |
| --- | --- | --- |
| Hauptstandort | Zentrale Schulumgebung mit mehreren Benutzergruppen | `R-HQ-SCHULE-01`, `SW-CORE-01`, Server, Lehrer-PCs, Schüler-PC, Admin-PC, Access Point |
| Aussenstelle | Kleiner zweiter Standort | `R-HQ-SCHULE-02`, `SW-CORE-02`, Lehrer-Laptop, Schüler-PC |
| WAN/Internet | Verbindung zwischen den Standorten | Simulierter Internet-Router |

## Problemstellung

Ohne saubere Struktur würden alle Geräte in einem gemeinsamen Netz liegen. Das hätte mehrere Nachteile:

- Broadcasts und Fehler könnten mehrere Benutzergruppen betreffen.
- Schüler-, Lehrer-, Admin- und Gastgeräte wären nicht sauber getrennt.
- Standortübergreifender Verkehr wäre ohne VPN nicht geschützt.
- Fehleranalyse wäre schwieriger, weil Dokumentation und Tests fehlen würden.

Deshalb wird das Netzwerk fachlich dokumentiert, segmentiert, getestet und mit Nachweisen ergänzt.
