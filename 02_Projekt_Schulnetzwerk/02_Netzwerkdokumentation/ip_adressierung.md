# IP-Adressierung

## Adresskonzept

Das Netzwerk verwendet getrennte IPv4-Netze fuer die Standorte und Benutzergruppen. Der Hauptstandort arbeitet mit mehreren `192.168.x.0/24`-Netzen. Die Aussenstelle verwendet das Netz `10.10.0.0/24`. Die WAN-Verbindungen zwischen den Routern und dem simulierten Internet sind mit `200.169.x.x` adressiert.

## WAN-Adressen

| Geraet | Interface | IP-Adresse | Netz | Beschreibung |
| --- | --- | --- | --- | --- |
| `R-HQ-SCHULE-02` | `Gig0/0` | `200.169.1.1` | `200.169.1.0/30` | WAN-Anbindung der Aussenstelle |
| `Internet` | `Gig0/0` | `200.169.1.2` | `200.169.1.0/30` | Gegenstelle zur Aussenstelle |
| `R-HQ-SCHULE-01` | `Gig0/0` | `200.169.2.1` | `200.169.2.0/30` | WAN-Anbindung des Hauptstandorts |
| `Internet` | `Gig0/1` | `200.169.2.2` | `200.169.2.0/30` | Gegenstelle zum Hauptstandort |

## Interne Adressen Hauptstandort

| Geraet | Interface | IP-Adresse | Netz | Beschreibung |
| --- | --- | --- | --- | --- |
| `R-HQ-SCHULE-01` | `Gig0/0` laut Diagramm | `192.168.0.1` | `192.168.0.0/24` | Gateway am Hauptstandort |
| `Server0` | `Fa0` | `192.168.0.10` | `192.168.0.0/24` | Server |
| `PC-LEHRER-01` | `Fa0` | `192.168.10.10` | `192.168.10.0/24` | Lehrer-Client |
| `PC-LEHRER-02` | `Fa0` | `192.168.10.11` | `192.168.10.0/24` | Lehrer-Client |
| `PC-SCHUELER-01` | `Fa0` | `192.168.20.10` | `192.168.20.0/24` | Schueler-Client |
| `PC-ADMIN-01` | `Fa0` | `192.168.40.10` | `192.168.40.0/24` | Administrations-Client |
| `AP-GUEST-01` | `Fa0` | nicht angegeben | WLAN-/Gastnetz | Access Point |

## Interne Adressen Aussenstelle

| Geraet | Interface | IP-Adresse | Netz | Beschreibung |
| --- | --- | --- | --- | --- |
| `R-HQ-SCHULE-02` | `Gig0/1` | `10.10.0.1` | `10.10.0.0/24` | Gateway der Aussenstelle |
| `PC-LEHRER-04` | `Fa0` | `10.10.0.10` | `10.10.0.0/24` | Lehrer-Laptop |
| `PC-SCHUELER-03` | `Fa0` | `10.10.0.11` | `10.10.0.0/24` | Schueler-PC |

## Default Gateways

| Netz | Default Gateway | Zweck |
| --- | --- | --- |
| `192.168.0.0/24` | `192.168.0.1` | Servernetz am Hauptstandort |
| `192.168.10.0/24` | nicht im Diagramm angegeben | Lehrer-Netz am Hauptstandort |
| `192.168.20.0/24` | nicht im Diagramm angegeben | Schueler-Netz am Hauptstandort |
| `192.168.40.0/24` | nicht im Diagramm angegeben | Administrationsnetz am Hauptstandort |
| `10.10.0.0/24` | `10.10.0.1` | Aussenstelle |

## Hinweis zu nicht sichtbaren Adressen

Im Diagramm ist nur `192.168.0.1` als Gateway des Hauptstandorts sichtbar. Fuer die VLAN-Netze `192.168.10.0/24`, `192.168.20.0/24` und `192.168.40.0/24` sind die Gateway-Adressen im Bild nicht angegeben. Bei einer vollstaendigen Router-on-a-Stick- oder Layer-3-Konfiguration wuerden diese Netze jeweils ein eigenes Gateway benoetigen.
