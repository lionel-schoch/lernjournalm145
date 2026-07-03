# VLAN-Übersicht

## Ziel der VLAN-Struktur

Die VLAN-Struktur trennt die Benutzergruppen am Hauptstandort logisch voneinander. Dadurch können Lehrpersonen, Schüler, Administration, Server und WLAN/Gastzugang getrennt verwaltet und mit passenden Sicherheitsregeln versehen werden.

## VLANs am Hauptstandort

| VLAN | Name / Bereich | Netz | Geräte | Zweck |
| --- | --- | --- | --- | --- |
| VLAN 10 | Lehrer | `192.168.10.0/24` | `PC-LEHRER-01`, `PC-LEHRER-02` | Arbeitsnetz für Lehrpersonen |
| VLAN 20 | Schüler | `192.168.20.0/24` | `PC-SCHUELER-01` | Arbeitsnetz für Schülergeräte |
| VLAN 30 | WLAN/Gast | nicht im Diagramm angegeben | `AP-GUEST-01` | WLAN- oder Gastzugang, getrennt von internen Bereichen |
| VLAN 40 | Administration | `192.168.40.0/24` | `PC-ADMIN-01` | Administratives Netz für Verwaltung und Administration |
| Servernetz | Server | `192.168.0.0/24` | `Server0`, Gateway `192.168.0.1` | Zentrale Dienste am Hauptstandort |

## VLANs an der Aussenstelle

Die Aussenstelle ist im Diagramm als einfaches Netz `10.10.0.0/24` dargestellt. Eine VLAN-Aufteilung ist im Bild nicht ersichtlich. Die Clients `PC-LEHRER-04` und `PC-SCHUELER-03` befinden sich beide im gleichen Standortnetz.

## Switch-Anbindung

`SW-CORE-01` verbindet die Endgeräte am Hauptstandort. Die im Diagramm beschrifteten VLAN-Leitungen zeigen, dass unterschiedliche Ports oder Portgruppen verschiedenen VLANs zugeordnet sind. Die Verbindung zum Router dient als Uplink für die Weiterleitung zwischen den Netzen und zum WAN.

`SW-CORE-02` verbindet die beiden Clients der Aussenstelle mit `R-HQ-SCHULE-02`. Da keine VLAN-Beschriftungen sichtbar sind, wird dieser Standort als flaches Access-Netz dokumentiert.

## Hinweise und Annahmen

VLAN 10, VLAN 20 und VLAN 40 sind im Diagramm erkennbar. Das WLAN-/Gastnetz wird aus dem eingezeichneten Access Point `AP-GUEST-01` abgeleitet; die genaue VLAN-ID oder IP-Adresse des Access Points ist im Diagramm nicht angegeben.

