# Testplan

## Ziel

Der Testplan beschreibt, wie die Funktion des Schulnetzwerks überprüft wird. Getestet werden VLANs, Trunking, Routing, VPN, WLAN/Gastbereich sowie typische Fehlersituationen.

Die Tests orientieren sich an den Anforderungen des Moduls 145: Konfigurationen sollen nicht nur umgesetzt, sondern auch validiert, dokumentiert und bei Fehlern systematisch analysiert werden.

## Testumgebung

| Bestandteil | Beschreibung |
| --- | --- |
| Simulationsumgebung | Cisco Packet Tracer |
| Hauptstandort | `R-HQ-SCHULE-01`, `SW-CORE-01`, Server, Clients, Access Point |
| Aussenstelle | `R-HQ-SCHULE-02`, `SW-CORE-02`, Clients |
| WAN | Simuliertes Internet mit den Netzen `200.169.1.0/30` und `200.169.2.0/30` |
| Nachweise | Screenshots unter `02_Projekt_Schulnetzwerk/assets/screenshots/` |

## Testfälle

| Nr. | Bereich | Test | Erwartetes Ergebnis | Nachweis |
| --- | --- | --- | --- | --- |
| T-01 | VLAN | `show vlan brief` auf `SW-CORE-01` | VLAN 10, 20, 30 und 40 sind aktiv vorhanden. | Screenshot VLAN |
| T-02 | VLAN | Access-Port `Fa0/1` prüfen | Port ist Access-Port im VLAN 10 `LEHRER`. | Screenshot VLAN |
| T-03 | Trunking | `show interfaces trunk` prüfen | `Gig0/1` ist Trunk und transportiert relevante VLANs. | Screenshot VLAN |
| T-04 | VLAN-Kommunikation | Ping innerhalb Lehrer-VLAN | Ping zwischen Lehrer-Clients funktioniert ohne Paketverlust. | Screenshot VLAN |
| T-05 | Routing | `show ip route` auf beiden Routern | Lokale Netze, WAN-Netze und Default Routes sind sichtbar. | Screenshot VPN |
| T-06 | VPN ACL | `show access-lists` prüfen | Interessanter Traffic für den VPN-Tunnel ist definiert. | Screenshot VPN |
| T-07 | VPN Phase 1 | `show crypto isakmp sa` | ISAKMP Security Association ist `ACTIVE`. | Screenshot VPN |
| T-08 | VPN Phase 2 | `show crypto ipsec sa` | ESP-SAs sind aktiv und Paketzähler steigen. | Screenshot VPN |
| T-09 | VPN Funktion | HTTPS-Zugriff von Aussenstelle auf `192.168.0.10` | Webseite am Hauptstandort ist erreichbar. | Screenshot VPN |
| T-10 | WLAN/Gast | Access Point und VLAN-Zuordnung prüfen | AP ist dem vorgesehenen WLAN-/Gastbereich zugeordnet. | Konfiguration / Screenshot falls vorhanden |
| T-11 | Sicherheit | Gast-/Schülerbereich gegen Admin-Bereich prüfen | Ungewollter Zugriff ist nicht möglich oder wird dokumentiert eingeschränkt. | Testprotokoll |
| T-12 | Fehleranalyse | Typische Fehlkonfiguration simulieren | Symptom, Ursache und Massnahme werden dokumentiert. | Troubleshooting |

## Prüfkriterien

Ein Test gilt als bestanden, wenn:

- das erwartete Ergebnis erreicht wird,
- ein Screenshot oder CLI-Auszug vorhanden ist,
- die Beobachtung im Testprotokoll beschrieben wird,
- bei Fehlern eine Massnahme dokumentiert wird.

## Mögliche Fehlerquellen

| Fehlerquelle | Erwartetes Symptom | Prüfmethode |
| --- | --- | --- |
| Falsches VLAN am Access-Port | Client erreicht Geräte im erwarteten VLAN nicht. | `show interfaces switchport`, Ping |
| Trunk transportiert VLAN nicht | VLAN-Kommunikation über Uplink funktioniert nicht. | `show interfaces trunk` |
| Falsches Default Gateway | Client erreicht andere Netze nicht. | IP-Konfiguration Client, Ping Gateway |
| Fehlende Route | Standortübergreifender Verkehr bricht ab. | `show ip route`, Traceroute |
| Falsche VPN ACL | IPsec-Tunnel baut nicht für den gewünschten Traffic auf. | `show access-lists`, `show crypto ipsec sa` |
| Falscher VPN Peer | ISAKMP bleibt inaktiv. | `show crypto isakmp sa` |
| WLAN falschem VLAN zugeordnet | WLAN-Client landet im falschen Netz. | AP-Konfiguration, IP-Adresse des Clients |

## Reihenfolge

1. Physische und logische Verbindungen prüfen
2. VLANs und Access-Ports prüfen
3. Trunk prüfen
4. Routing prüfen
5. VPN prüfen
6. End-to-End-Zugriff testen
7. Fehlerfälle dokumentieren
