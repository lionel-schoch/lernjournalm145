# Trunking

## Zweck

Trunking wird verwendet, um mehrere VLANs über eine einzige physische Verbindung zu transportieren. Im Projekt ist dies wichtig, weil die VLANs des Hauptstandorts über den Uplink weitergeleitet werden muessen.

## Trunk-Port

Der Screenshot `show interfaces trunk` zeigt den Port `Gig0/1` als aktiven Trunk.

| Eigenschaft | Wert |
| --- | --- |
| Interface | `Gig0/1` |
| Mode | `on` |
| Encapsulation | `802.1q` |
| Status | `trunking` |
| Native VLAN | 1 |

Nachweis: [show_interfaces_trunk_SW-CORE-01.png](../assets/screenshots/vlan/show_interfaces_trunk_SW-CORE-01.png)

## Erlaubte VLANs

Die Ausgabe zeigt, dass auf dem Trunk grundsaetzlich VLANs `1-1005` erlaubt sind. Im Management-Domain-Abschnitt sind die aktiven VLANs `1,10,20,30,40` sichtbar.

| Kategorie | VLANs |
| --- | --- |
| Erlaubt auf dem Trunk | `1-1005` |
| Aktiv und erlaubt | `1,10,20,30,40` |
| Forwarding State / nicht gepruned | `1,10,20,30,40` |

Damit transportiert der Trunk die projektrelevanten VLANs 10, 20, 30 und 40.

## Trunk-Einschraenkung in der Running Config

Im Screenshot der Interface-Konfiguration ist bei einem Trunk-Port folgende Zeile sichtbar:

```text
switchport trunk allowed vlan 1-19,21-1005
```

Diese Zeile schliesst VLAN 20 auf diesem Trunk aus. Das kann sinnvoll sein, wenn das Schüler-VLAN bewusst nicht über diese bestimmte Verbindung weitergeleitet werden soll. Gleichzeitig zeigt `show interfaces trunk` für `Gig0/1`, dass dort VLAN 20 aktiv erlaubt ist. Deshalb ist wichtig, die genaue Portzuordnung im Packet-Tracer-Projekt zu kontrollieren, falls mehrere Uplinks oder Trunk-Konfigurationen verwendet werden.

Nachweis: [show_running_config_interfaces_SW-CORE-01.png](../assets/screenshots/vlan/show_running_config_interfaces_SW-CORE-01.png)

## Bewertung

Der Trunk auf `Gig0/1` ist aktiv und transportiert die benötigten VLANs. Damit ist die Grundlage geschaffen, um VLAN-Verkehr zwischen Switch und weiterfuehrender Infrastruktur zu übertragen.

