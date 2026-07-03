# Konzept

## Ziel

Ziel der VLAN-Umsetzung ist die logische Trennung der verschiedenen Benutzergruppen im Schulnetzwerk. Dadurch können Lehrpersonen, Schüler, Administration sowie WLAN-/Gastgeräte getrennt verwaltet und besser abgesichert werden.

## Ausgangslage

Am Hauptstandort werden mehrere Endgeräte über den zentralen Switch `SW-CORE-01` angebunden. Ohne VLANs würden alle Geräte in derselben Broadcast-Domain arbeiten. Das wäre für ein Schulnetz unübersichtlich und sicherheitstechnisch ungeeignet.

Durch VLANs entstehen getrennte logische Netze auf derselben physischen Switch-Infrastruktur.

## VLAN-Struktur

| VLAN | Name | Zweck | Beispielgeräte |
| --- | --- | --- | --- |
| 10 | `LEHRER` | Netz für Lehrpersonen | `PC-LEHRER-01`, `PC-LEHRER-02` |
| 20 | `SCHUELER` | Netz für Schülergeräte | `PC-SCHUELER-01` |
| 30 | `WLAN/Gast` | WLAN- oder Gastzugang | `AP-GUEST-01` |
| 40 | `Administration` | Administratives Netz | `PC-ADMIN-01` |

Der Screenshot [show_vlan_brief_SW-CORE-01.png](../assets/screenshots/vlan/show_vlan_brief_SW-CORE-01.png) zeigt, dass diese VLANs auf `SW-CORE-01` angelegt und aktiv sind.

## Vorteile

| Vorteil | Beschreibung |
| --- | --- |
| Trennung von Benutzergruppen | Lehrpersonen, Schüler, Administration und Gäste befinden sich in getrennten logischen Netzen. |
| Weniger Broadcast-Verkehr | Broadcasts bleiben im jeweiligen VLAN und belasten nicht das ganze Schulnetz. |
| Bessere Sicherheit | Zugriffe zwischen VLANs können gezielt über Routing und ACLs gesteuert werden. |
| Übersichtlichere Verwaltung | Ports können klar einer Benutzergruppe zugeordnet werden. |

## Portrollen

Im VLAN-Konzept werden zwei wichtige Porttypen verwendet:

| Porttyp | Aufgabe |
| --- | --- |
| Access-Port | Verbindet ein Endgerät mit genau einem VLAN. |
| Trunk-Port | Transportiert mehrere VLANs über eine Verbindung, zum Beispiel zwischen Switch und Router oder zwischen Switches. |

Der Screenshot [show_interfaces_fa0-1_switchport_SW-CORE-01.png](../assets/screenshots/vlan/show_interfaces_fa0-1_switchport_SW-CORE-01.png) zeigt einen Access-Port im VLAN 10. Der Screenshot [show_interfaces_trunk_SW-CORE-01.png](../assets/screenshots/vlan/show_interfaces_trunk_SW-CORE-01.png) zeigt einen aktiven Trunk auf `Gig0/1`.

## Fazit

Die VLAN-Struktur bildet die Grundlage für ein sauber getrenntes Schulnetz. Die Benutzergruppen sind logisch getrennt, können aber bei Bedarf über Routing kontrolliert miteinander kommunizieren.

