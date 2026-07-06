# Screenshot-Nachweise

In diesem Ordner sammle ich die Screenshots, mit denen ich die technische Umsetzung im Packet-Tracer-Projekt belege. Die Screenshots sind nach Themen geordnet und dienen als Nachweis für Konfiguration, Tests und Funktionalität.

## Übersicht

| Bereich | Ordner | Inhalt |
| --- | --- | --- |
| VLAN | [vlan](vlan/) | VLAN-Liste, Trunk, Access-Port, Interface-Status und Ping-Test |
| WLAN | [wlan](wlan/) | WLAN-Topologie und Access-Point-Sicherheit |
| VPN | [vpn](vpn/) | ACLs, Crypto Maps, ISAKMP, IPsec, Routing und HTTPS-Test |

## VLAN-Nachweise

| Screenshot | Beschreibung | Nachweis |
| --- | --- | --- |
| [show_vlan_brief_SW-CORE-01.png](vlan/show_vlan_brief_SW-CORE-01.png) | Zeigt die VLAN-Übersicht auf `SW-CORE-01`. Sichtbar sind VLAN 10 `LEHRER`, VLAN 20 `SCHUELER`, VLAN 30 `WLAN/Gast` und VLAN 40 `Administration`. | Die benötigten VLANs sind auf dem Switch angelegt und aktiv. |
| [show_interfaces_trunk_SW-CORE-01.png](vlan/show_interfaces_trunk_SW-CORE-01.png) | Zeigt den Trunk-Status auf `Gig0/1` mit 802.1Q. | Der Uplink transportiert die relevanten VLANs. |
| [show_interfaces_fa0-1_switchport_SW-CORE-01.png](vlan/show_interfaces_fa0-1_switchport_SW-CORE-01.png) | Zeigt `Fa0/1` als Access-Port im VLAN 10 `LEHRER`. | Die Access-Port-Zuordnung für das Lehrer-VLAN ist korrekt. |
| [show_running_config_interfaces_SW-CORE-01.png](vlan/show_running_config_interfaces_SW-CORE-01.png) | Zeigt die Interface-Konfiguration mit Access-Zuordnungen für VLAN 10, 20, 30 und 40. | Die Ports sind den vorgesehenen VLAN-Bereichen zugeordnet. |
| [show_ip_interface_brief_SW-CORE-01.png](vlan/show_ip_interface_brief_SW-CORE-01.png) | Zeigt aktive FastEthernet-Ports und `GigabitEthernet0/1` im Status `up/up`. | Die relevanten physischen Verbindungen sind aktiv. |
| [ping_test_lehrer_vlan.png](vlan/ping_test_lehrer_vlan.png) | Zeigt erfolgreiche Pings von `PC-LEHRER-01` zu `192.168.10.10` und `192.168.10.11`. | Die Kommunikation im Lehrer-VLAN funktioniert. |

## WLAN-Nachweise

| Screenshot | Beschreibung | Nachweis |
| --- | --- | --- |
| [wlan_topologie_ap_clients.png](wlan/wlan_topologie_ap_clients.png) | Zeigt den Access Point `AP-GUEST-02`, WLAN-Clients und die Anbindung an die Switch-Infrastruktur. | Der WLAN-/Gastbereich ist im Packet-Tracer-Projekt umgesetzt. |
| [ap_guest_02_wpa2_config.png](wlan/ap_guest_02_wpa2_config.png) | Zeigt die AP-Konfiguration mit SSID `30`, Kanal 6, WPA2-PSK, AES und Passphrase `TBZ12345`. | Das WLAN ist konfiguriert und mit WPA2-PSK/AES abgesichert. |

## VPN-Nachweise

| Screenshot | Beschreibung | Nachweis |
| --- | --- | --- |
| [httpsconnectionovervpc.png](vpn/httpsconnectionovervpc.png) | Zeigt den Webbrowser von `PC-LEHRER-04` mit erfolgreichem HTTPS-Zugriff auf `https://192.168.0.10`. | Die Kommunikation von der Aussenstelle zum Server am Hauptstandort funktioniert. |
| [show_access-lists_von_R-HQ-SCHULE-01.png](vpn/show_access-lists_von_R-HQ-SCHULE-01.png) | Zeigt die Extended Access List 100 auf `R-HQ-SCHULE-01`. | Der interessante Traffic für den VPN-Tunnel ist definiert. |
| [show_access-lists_ovn_R-HQ-SCHULE-02.png](vpn/show_access-lists_ovn_R-HQ-SCHULE-02.png) | Zeigt die Extended Access List 100 auf `R-HQ-SCHULE-02` inklusive Trefferzähler. | Die Gegenseite erkennt passenden VPN-Traffic. |
| [show_crypto_isakmp_sa_von_R-HQ-SCHULE-01.png](vpn/show_crypto_isakmp_sa_von_R-HQ-SCHULE-01.png) | Zeigt eine aktive ISAKMP Security Association auf `R-HQ-SCHULE-01`. | VPN Phase 1 ist aufgebaut. |
| [show_crypto_isakmp_sa_von_R-HQ-SCHULE-02.png](vpn/show_crypto_isakmp_sa_von_R-HQ-SCHULE-02.png) | Zeigt eine aktive ISAKMP Security Association auf `R-HQ-SCHULE-02`. | VPN Phase 1 ist auf der Gegenseite aufgebaut. |
| [show_crypto_ipsec_sa_von_R-HQ-SCHULE-01.png](vpn/show_crypto_ipsec_sa_von_R-HQ-SCHULE-01.png) | Zeigt aktive IPsec Security Associations auf `R-HQ-SCHULE-01`. | VPN Phase 2 verarbeitet Datenverkehr. |
| [show_crypto_ipsec_sa_von_R-HQ-SCHULE-02.png](vpn/show_crypto_ipsec_sa_von_R-HQ-SCHULE-02.png) | Zeigt aktive IPsec Security Associations auf `R-HQ-SCHULE-02`. | Die Gegenseite verarbeitet IPsec-Traffic. |
| [show_crypto_map_von_R-HQ-SCHULE-01.png](vpn/show_crypto_map_von_R-HQ-SCHULE-01.png) | Zeigt die Crypto Map `VPN-MAP` auf `R-HQ-SCHULE-01`. | Peer, ACL, Transform-Set und Interface sind zugeordnet. |
| [show_crypto_map_von_R-HQ-SCHULE-02.png](vpn/show_crypto_map_von_R-HQ-SCHULE-02.png) | Zeigt die Crypto Map `VPN-MAP` auf `R-HQ-SCHULE-02`. | Die VPN-Parameter sind auf Router 2 zugeordnet. |
| [show_ip_route_von_R-HQ-SCHULE-01.png](vpn/show_ip_route_von_R-HQ-SCHULE-01.png) | Zeigt die Routing-Tabelle von `R-HQ-SCHULE-01`. | Lokale Route, WAN-Route und Default Route sind vorhanden. |
| [show_ip_route_von_R-HQ-SCHULE-02.png](vpn/show_ip_route_von_R-HQ-SCHULE-02.png) | Zeigt die Routing-Tabelle von `R-HQ-SCHULE-02`. | Lokale Route, WAN-Route und Default Route sind auf der Aussenstelle vorhanden. |

## Fazit

Die Screenshots zeigen, dass ich die zentralen Projektteile nicht nur beschrieben, sondern auch überprüft habe: VLAN-Segmentierung, WLAN-Konfiguration und VPN-Verbindung sind mit Nachweisen dokumentiert.
