# Screenshot-Nachweise

Diese Screenshots dokumentieren die Umsetzung und Validierung der VPN-Konfiguration im Packet-Tracer-Projekt. Die Bilder dienen als Arbeitsnachweis und zeigen sowohl die Konfiguration als auch die erfolgreiche Funktion des Site-to-Site-VPNs.

## VPN-Nachweise

| Screenshot | Beschreibung | Nachweis |
| --- | --- | --- |
| [httpsconnectionovervpc.png](vpn/httpsconnectionovervpc.png) | Zeigt den Webbrowser von `PC-LEHRER-04` mit erfolgreichem HTTPS-Zugriff auf `https://192.168.0.10`. | Belegt, dass die Kommunikation zur Gegenseite funktioniert und ein Dienst im entfernten Netz erreichbar ist. |
| [show_access-lists_von_R-HQ-SCHULE-01.png](vpn/show_access-lists_von_R-HQ-SCHULE-01.png) | Zeigt die Extended Access List 100 auf `R-HQ-SCHULE-01`. Erlaubt wird der Verkehr vom Netz `192.168.0.0/24` zum Netz `10.10.0.0/24`. | Belegt, welcher Datenverkehr als interessanter Traffic fuer den VPN-Tunnel definiert wurde. |
| [show_access-lists_ovn_R-HQ-SCHULE-02.png](vpn/show_access-lists_ovn_R-HQ-SCHULE-02.png) | Zeigt die Extended Access List 100 auf `R-HQ-SCHULE-02`. Neben internem Verkehr ist auch die Regel zum Netz `192.168.0.0/24` sichtbar, inklusive Trefferzaehler. | Belegt, dass passende ACL-Regeln auf der Gegenseite vorhanden sind und bereits Verkehr ueber die Regel erkannt wurde. |
| [show_crypto_isakmp_sa_von_R-HQ-SCHULE-01.png](vpn/show_crypto_isakmp_sa_von_R-HQ-SCHULE-01.png) | Zeigt die ISAKMP Security Association auf `R-HQ-SCHULE-01` mit Peer `200.169.1.1` und Status `ACTIVE`. | Belegt, dass Phase 1 des IPsec-VPNs auf Router 1 erfolgreich aufgebaut wurde. |
| [show_crypto_isakmp_sa_von_R-HQ-SCHULE-02.png](vpn/show_crypto_isakmp_sa_von_R-HQ-SCHULE-02.png) | Zeigt die ISAKMP Security Association auf `R-HQ-SCHULE-02` mit Peer `200.169.2.1` und Status `ACTIVE`. | Belegt, dass Phase 1 des IPsec-VPNs auch auf Router 2 aktiv ist. |
| [show_crypto_ipsec_sa_von_R-HQ-SCHULE-01.png](vpn/show_crypto_ipsec_sa_von_R-HQ-SCHULE-01.png) | Zeigt die IPsec Security Association auf `R-HQ-SCHULE-01`. Sichtbar sind die geschuetzten Netze `192.168.0.0/24` und `10.10.0.0/24`, aktive ESP-SAs sowie Paketzaehler fuer verschluesselte und entschluesselte Pakete. | Belegt, dass Phase 2 aktiv ist und Daten ueber den IPsec-Tunnel verarbeitet werden. |
| [show_crypto_ipsec_sa_von_R-HQ-SCHULE-02.png](vpn/show_crypto_ipsec_sa_von_R-HQ-SCHULE-02.png) | Zeigt die IPsec Security Association auf `R-HQ-SCHULE-02`. Sichtbar sind lokale und entfernte Netze, Peer-Adresse, ESP-SAs und Paketzaehler. | Belegt die funktionierende IPsec-Aushandlung und Datenverarbeitung auf der Gegenseite. |
| [show_crypto_map_von_R-HQ-SCHULE-01.png](vpn/show_crypto_map_von_R-HQ-SCHULE-01.png) | Zeigt die Crypto Map `VPN-MAP` auf `R-HQ-SCHULE-01` mit Peer `200.169.1.1`, ACL 100, Transform-Set und Interface `GigabitEthernet0/0`. | Belegt, dass die VPN-Parameter auf dem ausgehenden Interface von Router 1 angewendet sind. |
| [show_crypto_map_von_R-HQ-SCHULE-02.png](vpn/show_crypto_map_von_R-HQ-SCHULE-02.png) | Zeigt die Crypto Map `VPN-MAP` auf `R-HQ-SCHULE-02` mit Peer `200.169.2.1`, ACL 100, Transform-Set und Interface `GigabitEthernet0/0`. | Belegt, dass die VPN-Parameter auf Router 2 korrekt zugeordnet sind. |
| [show_ip_route_von_R-HQ-SCHULE-01.png](vpn/show_ip_route_von_R-HQ-SCHULE-01.png) | Zeigt die Routing-Tabelle von `R-HQ-SCHULE-01`. Sichtbar sind das lokale Netz `192.168.0.0/24`, das WAN-Netz `200.169.2.0/30` und die Standardroute via `200.169.2.2`. | Belegt, dass Router 1 die lokalen und WAN-seitigen Routen kennt und einen Default Gateway gesetzt hat. |
| [show_ip_route_von_R-HQ-SCHULE-02.png](vpn/show_ip_route_von_R-HQ-SCHULE-02.png) | Zeigt die Routing-Tabelle von `R-HQ-SCHULE-02`. Sichtbar sind das lokale Netz `10.10.0.0/24`, das WAN-Netz `200.169.1.0/30` und die Standardroute via `200.169.1.2`. | Belegt, dass Router 2 die lokalen und WAN-seitigen Routen kennt und einen Default Gateway gesetzt hat. |

## Fazit

Die Screenshots zeigen zusammen den kompletten Nachweis der VPN-Umsetzung: Routing ist vorhanden, interessanter Traffic wird per ACL definiert, die Crypto Maps sind auf den Interfaces aktiv, ISAKMP und IPsec Security Associations sind aufgebaut, und der HTTPS-Test bestaetigt die praktische Erreichbarkeit eines entfernten Dienstes.
