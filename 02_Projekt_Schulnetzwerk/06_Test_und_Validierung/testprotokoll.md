# Testprotokoll

## Übersicht

Dieses Testprotokoll fasst die durchgeführten und geplanten Validierungen des Schulnetzwerks zusammen. Die Tests beziehen sich auf VLAN, Trunking, Routing, VPN und WLAN/Gastbereich.

## Durchgeführte Tests

| Nr. | Test | Ergebnis | Bewertung | Nachweis |
| --- | --- | --- | --- | --- |
| T-01 | VLAN-Liste prüfen | VLAN 10 `LEHRER`, VLAN 20 `SCHUELER`, VLAN 30 `WLAN/Gast` und VLAN 40 `Administration` sind aktiv. | Bestanden | [show_vlan_brief_SW-CORE-01.png](../assets/screenshots/vlan/show_vlan_brief_SW-CORE-01.png) |
| T-02 | Access-Port prüfen | `Fa0/1` ist als `static access` konfiguriert und VLAN 10 zugeordnet. | Bestanden | [show_interfaces_fa0-1_switchport_SW-CORE-01.png](../assets/screenshots/vlan/show_interfaces_fa0-1_switchport_SW-CORE-01.png) |
| T-03 | Trunk prüfen | `Gig0/1` ist als 802.1Q-Trunk aktiv. VLANs 10, 20, 30 und 40 sind sichtbar. | Bestanden | [show_interfaces_trunk_SW-CORE-01.png](../assets/screenshots/vlan/show_interfaces_trunk_SW-CORE-01.png) |
| T-04 | Interface-Status prüfen | Mehrere FastEthernet-Ports und `GigabitEthernet0/1` sind `up/up`. | Bestanden | [show_ip_interface_brief_SW-CORE-01.png](../assets/screenshots/vlan/show_ip_interface_brief_SW-CORE-01.png) |
| T-05 | Ping im Lehrer-VLAN | Pings zu `192.168.10.10` und `192.168.10.11` funktionieren ohne Paketverlust. | Bestanden | [ping_test_lehrer_vlan.png](../assets/screenshots/vlan/ping_test_lehrer_vlan.png) |
| T-06 | Routing Hauptstandort | `R-HQ-SCHULE-01` kennt lokales Netz, WAN-Netz und Default Route. | Bestanden | [show_ip_route_von_R-HQ-SCHULE-01.png](../assets/screenshots/vpn/show_ip_route_von_R-HQ-SCHULE-01.png) |
| T-07 | Routing Aussenstelle | `R-HQ-SCHULE-02` kennt lokales Netz, WAN-Netz und Default Route. | Bestanden | [show_ip_route_von_R-HQ-SCHULE-02.png](../assets/screenshots/vpn/show_ip_route_von_R-HQ-SCHULE-02.png) |
| T-08 | VPN ACL prüfen | ACLs definieren den interessanten Traffic zwischen den Standortnetzen. | Bestanden | [Screenshot-Nachweise](../assets/screenshots/README.md) |
| T-09 | VPN Phase 1 prüfen | ISAKMP Security Associations sind auf beiden Routern `ACTIVE`. | Bestanden | [Screenshot-Nachweise](../assets/screenshots/README.md) |
| T-10 | VPN Phase 2 prüfen | IPsec ESP-SAs sind aktiv und Paketzähler sind sichtbar. | Bestanden | [Screenshot-Nachweise](../assets/screenshots/README.md) |
| T-11 | HTTPS über VPN | `PC-LEHRER-04` erreicht `https://192.168.0.10`. | Bestanden | [httpsconnectionovervpc.png](../assets/screenshots/vpn/httpsconnectionovervpc.png) |
| T-12 | WLAN-Topologie prüfen | Access Point und WLAN-Clients sind im Packet-Tracer-Projekt sichtbar. | Bestanden | [wlan_topologie_ap_clients.png](../assets/screenshots/wlan/wlan_topologie_ap_clients.png) |
| T-13 | WLAN-Sicherheit prüfen | `AP-GUEST-02` ist mit WPA2-PSK und AES konfiguriert. | Bestanden | [ap_guest_02_wpa2_config.png](../assets/screenshots/wlan/ap_guest_02_wpa2_config.png) |

## Noch zu ergänzende Tests

| Nr. | Test | Grund |
| --- | --- | --- |
| T-14 | WLAN-/Gast-Client erhält korrekte IP-Adresse | Als zusätzlicher Nachweis wäre ein Client-IP-Screenshot aus dem WLAN-/Gastnetz sinnvoll. |
| T-15 | Zugriff Gast/WLAN auf interne Netze prüfen | Sicherheitskonzept soll nachweisen, dass Gastgeräte nicht unnötig interne Ressourcen erreichen. |
| T-16 | Inter-VLAN-Kommunikation gezielt prüfen | Es soll dokumentiert werden, welche VLANs miteinander kommunizieren dürfen. |
| T-17 | Monitoring-Werte erfassen | Für den Kompetenzbereich Überwachung sollten Latenz, Paketverlust oder Interface-Status ausgewertet werden. |

## Beobachtungen

Die vorhandenen Tests zeigen, dass die wichtigsten Grundfunktionen funktionieren:

- VLANs sind vorhanden.
- Access-Ports sind den VLANs zugeordnet.
- Der Trunk ist aktiv.
- Routing zwischen Standort und WAN ist vorhanden.
- VPN Phase 1 und Phase 2 sind aktiv.
- Ein End-to-End-Zugriff über HTTPS funktioniert.
- WLAN ist vorhanden und mit WPA2-PSK/AES abgesichert.

## Bewertung

Die technische Umsetzung ist für VLAN, WLAN und VPN mit Screenshots belegt. Für eine noch vollständigere Abgabe sollten ein WLAN-Client-IP-Test, Inter-VLAN-Regeln und Monitoring zusätzlich mit eigenen Screenshots oder Messwerten ergänzt werden.
