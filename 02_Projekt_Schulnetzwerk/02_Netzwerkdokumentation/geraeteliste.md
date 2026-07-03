# Geräteliste

## Netzwerkgeräte

| Gerät | Typ | Standort | Aufgabe |
| --- | --- | --- | --- |
| `R-HQ-SCHULE-01` | Router | Hauptstandort | Gateway für den Hauptstandort, WAN-Anbindung, Routing zwischen internen Netzen und VPN-Endpunkt |
| `SW-CORE-01` | Cisco 2960-24TT Switch | Hauptstandort | Zentrale Switch-Infrastruktur für Server, Clients, Administration und WLAN/Gastzugang |
| `R-HQ-SCHULE-02` | Cisco 2911 Router | Aussenstelle | Gateway für die Aussenstelle, WAN-Anbindung und VPN-Endpunkt |
| `SW-CORE-02` | Cisco 2960-24TT Switch | Aussenstelle | Lokale Switch-Infrastruktur für die Clients der Aussenstelle |
| `Internet` | Router/WAN-Simulation | WAN | Simuliert die Verbindung zwischen den beiden Standorten |
| `AP-GUEST-01` | Access Point | Hauptstandort | WLAN-/Gastzugang am Hauptstandort |

## Endgeräte Hauptstandort

| Gerät | Typ | IP-Adresse | Zugeordneter Bereich |
| --- | --- | --- | --- |
| `Server0` | Server | `192.168.0.10` | Servernetz / zentrale Dienste |
| `PC-LEHRER-01` | PC | `192.168.10.10` | Lehrer |
| `PC-LEHRER-02` | PC | `192.168.10.11` | Lehrer |
| `PC-SCHUELER-01` | PC | `192.168.20.10` | Schüler |
| `PC-ADMIN-01` | PC | `192.168.40.10` | Administration |
| `AP-GUEST-01` | Access Point | nicht im Diagramm angegeben | WLAN/Gast |

## Endgeräte Aussenstelle

| Gerät | Typ | IP-Adresse | Zugeordneter Bereich |
| --- | --- | --- | --- |
| `PC-LEHRER-04` | Laptop | `10.10.0.10` | Lehrer / Aussenstelle |
| `PC-SCHUELER-03` | PC | `10.10.0.11` | Schüler / Aussenstelle |

## Hinweise

Die Gerätenamen und IP-Adressen wurden aus dem Topologie-Diagramm übernommen. Bei Ports, VLAN-Zuordnungen und nicht sichtbaren Management-Adressen sind nur die im Diagramm erkennbaren Informationen dokumentiert.

