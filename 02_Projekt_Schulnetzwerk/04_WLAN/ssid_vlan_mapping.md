# SSID-VLAN-Mapping

## Ziel

Das SSID-/VLAN-Mapping beschreibt, welchem logischen Netzwerk das WLAN zugeordnet ist. In meiner Umsetzung wird der WLAN-/Gastbereich dem VLAN 30 zugeordnet.

## Mapping

| SSID | VLAN | Bereich | Zweck |
| --- | --- | --- | --- |
| `30` | VLAN 30 | WLAN/Gast | drahtloser Zugang für Gast- oder BYOD-Geräte |

Die SSID ist im Screenshot der Access-Point-Konfiguration sichtbar. Dort ist als SSID der Wert `30` eingetragen. Diese Bezeichnung passt zum vorgesehenen VLAN 30 für WLAN/Gast.

Nachweis: [ap_guest_02_wpa2_config.png](../assets/screenshots/wlan/ap_guest_02_wpa2_config.png)

## Switch-Anbindung

Der Access Point ist mit der Switch-Infrastruktur verbunden. In der VLAN-Dokumentation ist VLAN 30 bereits als `WLAN/Gast` vorgesehen. Der Switchport zum Access Point muss deshalb so konfiguriert sein, dass der WLAN-Verkehr dem VLAN 30 zugeordnet wird.

Je nach Packet-Tracer-Gerät gibt es zwei mögliche Varianten:

| Variante | Beschreibung |
| --- | --- |
| Access-Port | Der AP-Port wird direkt als Access-Port im VLAN 30 konfiguriert. |
| Trunk-Port | Der AP kann mehrere SSIDs/VLANs transportieren; in diesem Projekt wird jedoch nur der Gastbereich benötigt. |

Für dieses Projekt genügt die Access-Port-Variante, da nur eine WLAN-/Gast-SSID dokumentiert ist.

## IP-Bereich

Der genaue IP-Bereich des WLAN-/Gastnetzes ist im Topologie-Screenshot nicht vollständig sichtbar. In der bestehenden VLAN-Struktur ist VLAN 30 als WLAN-/Gastbereich vorgesehen. Für eine vollständige produktive Umsetzung würde ich einen eigenen IP-Bereich definieren, zum Beispiel:

| VLAN | Beispielnetz | Gateway |
| --- | --- | --- |
| VLAN 30 | `192.168.30.0/24` | `192.168.30.1` |

Diese Adressen sind als sinnvolle Ergänzung dokumentiert. Sie müssen in Packet Tracer noch mit der tatsächlichen Konfiguration abgeglichen werden, falls ein WLAN-Client aktiv getestet wird.

## Fazit

Die SSID `30` ist fachlich dem VLAN 30 `WLAN/Gast` zugeordnet. Dadurch bleibt der drahtlose Zugang logisch getrennt von Lehrer-, Schüler-, Admin- und Servernetz.
