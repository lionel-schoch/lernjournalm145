# Konfiguration

## Übersicht

Die VLAN-Konfiguration wurde auf `SW-CORE-01` umgesetzt. Die Nachweis-Screenshots zeigen, dass die VLANs angelegt, Ports zugeordnet und ein Trunk-Uplink eingerichtet wurde.

## Angelegte VLANs

Die Ausgabe `show vlan brief` zeigt folgende aktive VLANs:

| VLAN | Name | Status |
| --- | --- | --- |
| 10 | `LEHRER` | active |
| 20 | `SCHUELER` | active |
| 30 | `WLAN/Gast` | active |
| 40 | `Administration` | active |

Nachweis: [show_vlan_brief_SW-CORE-01.png](../assets/screenshots/vlan/show_vlan_brief_SW-CORE-01.png)

## Access-Port-Konfiguration

Die Interface-Konfiguration zeigt die Zuordnung mehrerer FastEthernet-Ports zu VLANs.

| Interface | Modus | VLAN | Zweck |
| --- | --- | --- | --- |
| `FastEthernet0/1` | Access | 10 | Lehrer-Netz |
| `FastEthernet0/2` | Access | 20 | Schüler-Netz |
| `FastEthernet0/3` | Access | 30 | WLAN/Gast |
| `FastEthernet0/4` | Access | 40 | Administration |
| `FastEthernet0/5` | Access | 10 | weiterer Lehrer-Port |

Nachweis: [show_running_config_interfaces_SW-CORE-01.png](../assets/screenshots/vlan/show_running_config_interfaces_SW-CORE-01.png)

## Beispiel: Port Fa0/1

Der Screenshot `show interfaces fa0/1 switchport` zeigt die Detailkonfiguration von `Fa0/1`:

| Eigenschaft | Wert |
| --- | --- |
| Administrative Mode | `static access` |
| Operational Mode | `static access` |
| Access Mode VLAN | `10 (LEHRER)` |
| Trunking Native VLAN | `1 (default)` |

Nachweis: [show_interfaces_fa0-1_switchport_SW-CORE-01.png](../assets/screenshots/vlan/show_interfaces_fa0-1_switchport_SW-CORE-01.png)

## Trunk-Konfiguration

Der Uplink `Gig0/1` ist als Trunk aktiv. Dadurch können mehrere VLANs über dieselbe physische Verbindung transportiert werden.

| Interface | Modus | Encapsulation | Status | Native VLAN |
| --- | --- | --- | --- | --- |
| `Gig0/1` | `on` | `802.1q` | `trunking` | 1 |

Nachweis: [show_interfaces_trunk_SW-CORE-01.png](../assets/screenshots/vlan/show_interfaces_trunk_SW-CORE-01.png)

## Interface-Status

Die Ausgabe `show ip interface brief` zeigt, dass die relevanten FastEthernet-Ports und `GigabitEthernet0/1` aktiv sind. Damit sind die Endgeräte und der Uplink physisch verbunden.

Nachweis: [show_ip_interface_brief_SW-CORE-01.png](../assets/screenshots/vlan/show_ip_interface_brief_SW-CORE-01.png)

## Fazit

Die Konfiguration zeigt eine funktionierende VLAN-Grundstruktur: VLANs sind angelegt, Access-Ports sind zugeordnet und der Trunk-Port ist aktiv.

