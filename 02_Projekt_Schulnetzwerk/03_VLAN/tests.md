# Tests

## Ziel der Tests

Die VLAN-Tests prüfen, ob die VLANs auf dem Switch existieren, die Ports korrekt zugeordnet sind, der Trunk funktioniert und Clients innerhalb eines VLANs miteinander kommunizieren können.

## Testübersicht

| Nr. | Test | Erwartetes Ergebnis | Nachweis |
| --- | --- | --- | --- |
| 1 | VLANs anzeigen | VLAN 10, 20, 30 und 40 sind aktiv vorhanden. | `show vlan brief` |
| 2 | Trunk prüfen | `Gig0/1` ist als 802.1Q-Trunk aktiv. | `show interfaces trunk` |
| 3 | Access-Port prüfen | `Fa0/1` ist Access-Port im VLAN 10. | `show interfaces fa0/1 switchport` |
| 4 | Interface-Konfiguration prüfen | Ports sind den vorgesehenen VLANs zugeordnet. | `show running-config | section interface` |
| 5 | Interface-Status prüfen | Relevante Ports und Uplink sind `up/up`. | `show ip interface brief` |
| 6 | Client-Kommunikation testen | Ping innerhalb des Lehrer-Netzes funktioniert. | Ping-Test |

## Test 1: VLANs anzeigen

Der Screenshot zeigt die VLAN-Liste auf `SW-CORE-01`. Die VLANs `LEHRER`, `SCHUELER`, `WLAN/Gast` und `Administration` sind vorhanden und aktiv.

Nachweis: [show_vlan_brief_SW-CORE-01.png](../assets/screenshots/vlan/show_vlan_brief_SW-CORE-01.png)

Bewertung: Bestanden.

## Test 2: Trunk prüfen

Der Screenshot zeigt `Gig0/1` als aktiven Trunk mit 802.1Q. Die aktiven VLANs `1,10,20,30,40` sind auf dem Trunk sichtbar.

Nachweis: [show_interfaces_trunk_SW-CORE-01.png](../assets/screenshots/vlan/show_interfaces_trunk_SW-CORE-01.png)

Bewertung: Bestanden.

## Test 3: Access-Port prüfen

Der Screenshot zeigt `Fa0/1` im Modus `static access`. Der Port ist dem Access VLAN 10 `LEHRER` zugeordnet.

Nachweis: [show_interfaces_fa0-1_switchport_SW-CORE-01.png](../assets/screenshots/vlan/show_interfaces_fa0-1_switchport_SW-CORE-01.png)

Bewertung: Bestanden.

## Test 4: Interface-Konfiguration prüfen

Der Screenshot der Interface-Konfiguration zeigt mehrere Access-Port-Zuordnungen:

| Interface | VLAN |
| --- | --- |
| `Fa0/1` | 10 |
| `Fa0/2` | 20 |
| `Fa0/3` | 30 |
| `Fa0/4` | 40 |
| `Fa0/5` | 10 |

Nachweis: [show_running_config_interfaces_SW-CORE-01.png](../assets/screenshots/vlan/show_running_config_interfaces_SW-CORE-01.png)

Bewertung: Bestanden.

## Test 5: Interface-Status prüfen

Der Screenshot `show ip interface brief` zeigt mehrere FastEthernet-Ports sowie `GigabitEthernet0/1` im Status `up/up`. Dadurch ist erkennbar, dass die benötigten physischen Verbindungen aktiv sind.

Nachweis: [show_ip_interface_brief_SW-CORE-01.png](../assets/screenshots/vlan/show_ip_interface_brief_SW-CORE-01.png)

Bewertung: Bestanden.

## Test 6: Ping im Lehrer-VLAN

Der Ping-Test wurde auf `PC-LEHRER-01` ausgefuehrt. Die Pings zu `192.168.10.10` und `192.168.10.11` waren erfolgreich, jeweils ohne Paketverlust.

Nachweis: [ping_test_lehrer_vlan.png](../assets/screenshots/vlan/ping_test_lehrer_vlan.png)

Bewertung: Bestanden.

## Fazit

Die Tests zeigen, dass die VLAN-Grundkonfiguration funktioniert. VLANs sind angelegt, Ports sind korrekt zugeordnet, der Trunk ist aktiv und die Kommunikation innerhalb des Lehrer-VLANs ist erfolgreich getestet.

