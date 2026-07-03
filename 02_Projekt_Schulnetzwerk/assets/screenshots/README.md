# Screenshot-Nachweise

Diese Screenshots dokumentieren die Umsetzung und Validierung der VPN-Konfiguration im Packet-Tracer-Projekt. Die Bilder dienen als Arbeitsnachweis und zeigen sowohl die Konfiguration als auch die erfolgreiche Funktion des Site-to-Site-VPNs.

## VPN-Nachweise

| Screenshot | Beschreibung | Nachweis |
| --- | --- | --- |
| [httpsconnectionovervpc.png](vpn/httpsconnectionovervpc.png) | Zeigt den Webbrowser von `PC-LEHRER-04` mit erfolgreichem HTTPS-Zugriff auf `https://192.168.0.10`. | Belegt, dass die Kommunikation zur Gegenseite funktioniert und ein Dienst im entfernten Netz erreichbar ist. |
| [show_access-lists_von_R-HQ-SCHULE-01.png](vpn/show_access-lists_von_R-HQ-SCHULE-01.png) | Zeigt die Extended Access List 100 auf `R-HQ-SCHULE-01`. Erlaubt wird der Verkehr vom Netz `192.168.0.0/24` zum Netz `10.10.0.0/24`. | Belegt, welcher Datenverkehr als interessanter Traffic für den VPN-Tunnel definiert wurde. |
| [show_access-lists_ovn_R-HQ-SCHULE-02.png](vpn/show_access-lists_ovn_R-HQ-SCHULE-02.png) | Zeigt die Extended Access List 100 auf `R-HQ-SCHULE-02`. Neben internem Verkehr ist auch die Regel zum Netz `192.168.0.0/24` sichtbar, inklusive Trefferzähler. | Belegt, dass passende ACL-Regeln auf der Gegenseite vorhanden sind und bereits Verkehr über die Regel erkannt wurde. |
| [show_crypto_isakmp_sa_von_R-HQ-SCHULE-01.png](vpn/show_crypto_isakmp_sa_von_R-HQ-SCHULE-01.png) | Zeigt die ISAKMP Security Association auf `R-HQ-SCHULE-01` mit Peer `200.169.1.1` und Status `ACTIVE`. | Belegt, dass Phase 1 des IPsec-VPNs auf Router 1 erfolgreich aufgebaut wurde. |
| [show_crypto_isakmp_sa_von_R-HQ-SCHULE-02.png](vpn/show_crypto_isakmp_sa_von_R-HQ-SCHULE-02.png) | Zeigt die ISAKMP Security Association auf `R-HQ-SCHULE-02` mit Peer `200.169.2.1` und Status `ACTIVE`. | Belegt, dass Phase 1 des IPsec-VPNs auch auf Router 2 aktiv ist. |
| [show_crypto_ipsec_sa_von_R-HQ-SCHULE-01.png](vpn/show_crypto_ipsec_sa_von_R-HQ-SCHULE-01.png) | Zeigt die IPsec Security Association auf `R-HQ-SCHULE-01`. Sichtbar sind die geschützten Netze `192.168.0.0/24` und `10.10.0.0/24`, aktive ESP-SAs sowie Paketzähler für verschlüsselte und entschlüsselte Pakete. | Belegt, dass Phase 2 aktiv ist und Daten über den IPsec-Tunnel verarbeitet werden. |
| [show_crypto_ipsec_sa_von_R-HQ-SCHULE-02.png](vpn/show_crypto_ipsec_sa_von_R-HQ-SCHULE-02.png) | Zeigt die IPsec Security Association auf `R-HQ-SCHULE-02`. Sichtbar sind lokale und entfernte Netze, Peer-Adresse, ESP-SAs und Paketzähler. | Belegt die funktionierende IPsec-Aushandlung und Datenverarbeitung auf der Gegenseite. |
| [show_crypto_map_von_R-HQ-SCHULE-01.png](vpn/show_crypto_map_von_R-HQ-SCHULE-01.png) | Zeigt die Crypto Map `VPN-MAP` auf `R-HQ-SCHULE-01` mit Peer `200.169.1.1`, ACL 100, Transform-Set und Interface `GigabitEthernet0/0`. | Belegt, dass die VPN-Parameter auf dem ausgehenden Interface von Router 1 angewendet sind. |
| [show_crypto_map_von_R-HQ-SCHULE-02.png](vpn/show_crypto_map_von_R-HQ-SCHULE-02.png) | Zeigt die Crypto Map `VPN-MAP` auf `R-HQ-SCHULE-02` mit Peer `200.169.2.1`, ACL 100, Transform-Set und Interface `GigabitEthernet0/0`. | Belegt, dass die VPN-Parameter auf Router 2 korrekt zugeordnet sind. |
| [show_ip_route_von_R-HQ-SCHULE-01.png](vpn/show_ip_route_von_R-HQ-SCHULE-01.png) | Zeigt die Routing-Tabelle von `R-HQ-SCHULE-01`. Sichtbar sind das lokale Netz `192.168.0.0/24`, das WAN-Netz `200.169.2.0/30` und die Standardroute via `200.169.2.2`. | Belegt, dass Router 1 die lokalen und WAN-seitigen Routen kennt und einen Default Gateway gesetzt hat. |
| [show_ip_route_von_R-HQ-SCHULE-02.png](vpn/show_ip_route_von_R-HQ-SCHULE-02.png) | Zeigt die Routing-Tabelle von `R-HQ-SCHULE-02`. Sichtbar sind das lokale Netz `10.10.0.0/24`, das WAN-Netz `200.169.1.0/30` und die Standardroute via `200.169.1.2`. | Belegt, dass Router 2 die lokalen und WAN-seitigen Routen kennt und einen Default Gateway gesetzt hat. |

## Fazit

Die Screenshots zeigen zusammen den kompletten Nachweis der VPN-Umsetzung: Routing ist vorhanden, interessanter Traffic wird per ACL definiert, die Crypto Maps sind auf den Interfaces aktiv, ISAKMP und IPsec Security Associations sind aufgebaut, und der HTTPS-Test bestätigt die praktische Erreichbarkeit eines entfernten Dienstes.

## VLAN-Nachweise

| Screenshot | Beschreibung | Nachweis |
| --- | --- | --- |
| [show_vlan_brief_SW-CORE-01.png](vlan/show_vlan_brief_SW-CORE-01.png) | Zeigt die VLAN-Übersicht auf `SW-CORE-01`. Sichtbar sind VLAN 10 `LEHRER`, VLAN 20 `SCHUELER`, VLAN 30 `WLAN/Gast` und VLAN 40 `Administration`. | Belegt, dass die benötigten VLANs auf dem Switch angelegt und aktiv sind. |
| [show_interfaces_trunk_SW-CORE-01.png](vlan/show_interfaces_trunk_SW-CORE-01.png) | Zeigt den Trunk-Status auf `Gig0/1`. Der Port trunked mit 802.1Q, Native VLAN 1, erlaubt VLANs `1-1005` und aktive VLANs `1,10,20,30,40`. | Belegt, dass der Uplink als Trunk konfiguriert ist und die VLANs 10, 20, 30 und 40 übertragen werden. |
| [show_interfaces_fa0-1_switchport_SW-CORE-01.png](vlan/show_interfaces_fa0-1_switchport_SW-CORE-01.png) | Zeigt die Switchport-Konfiguration von `Fa0/1`. Der Port ist im Modus `static access` und dem Access VLAN 10 `LEHRER` zugeordnet. | Belegt die korrekte Access-Port-Zuordnung für das Lehrer-VLAN. |
| [show_running_config_interfaces_SW-CORE-01.png](vlan/show_running_config_interfaces_SW-CORE-01.png) | Zeigt die Interface-Konfiguration des Switches. Sichtbar sind Access-Zuordnungen für VLAN 10, 20, 30 und 40 sowie ein Trunk-Port, der VLAN 20 ausschliesst. | Belegt die konkrete Port-Konfiguration für die verschiedenen VLAN-Bereiche. |
| [show_ip_interface_brief_SW-CORE-01.png](vlan/show_ip_interface_brief_SW-CORE-01.png) | Zeigt den Interface-Status von `SW-CORE-01`. Mehrere FastEthernet-Ports und `GigabitEthernet0/1` sind `up/up`; `Vlan1` hat die Management-IP `10.10.0.2`, ist aber administratively down. | Belegt, welche Switchports aktiv verbunden sind und dass der Trunk-Uplink aktiv ist. |
| [ping_test_lehrer_vlan.png](vlan/ping_test_lehrer_vlan.png) | Zeigt erfolgreiche Pings von `PC-LEHRER-01` zu `192.168.10.10` und `192.168.10.11`. | Belegt die Erreichbarkeit innerhalb des Lehrer-Netzes beziehungsweise VLAN 10. |

## Gesamtfazit

Die VPN- und VLAN-Screenshots dokumentieren zusammen die zentrale Projektumsetzung: Das Netzwerk ist logisch segmentiert, der Trunk transportiert die benötigten VLANs, Access-Ports sind den passenden VLANs zugeordnet, und die Standortverbindung über VPN wurde erfolgreich getestet.

