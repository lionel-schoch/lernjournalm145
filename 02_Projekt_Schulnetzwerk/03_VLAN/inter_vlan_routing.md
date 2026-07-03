# Inter-VLAN-Routing

## Ziel

Inter-VLAN-Routing ermöglicht die Kommunikation zwischen unterschiedlichen VLANs. Da VLANs getrennte Layer-2-Broadcast-Domains sind, können Geräte aus verschiedenen VLANs nur über ein Layer-3-Gateway miteinander kommunizieren.

## Rolle im Projekt

Im Projekt sind mehrere VLANs für unterschiedliche Benutzergruppen vorgesehen:

| VLAN | Netz / Bereich | Zweck |
| --- | --- | --- |
| 10 | Lehrer | Kommunikation der Lehrer-Clients |
| 20 | Schüler | Kommunikation der Schüler-Clients |
| 30 | WLAN/Gast | WLAN- oder Gastgeräte |
| 40 | Administration | Administrationsgeräte |

Die VLAN-Screenshots zeigen die Switch-Konfiguration und den Trunk. Sie zeigen jedoch keine vollständige Router-on-a-Stick- oder Layer-3-SVI-Konfiguration für alle VLAN-Gateways. Deshalb wird hier dokumentiert, was für Inter-VLAN-Routing benötigt wird und welche Nachweise bereits vorhanden sind.

## Notwendige Bausteine

| Baustein | Zweck | Nachweis im Projekt |
| --- | --- | --- |
| VLANs auf dem Switch | Logische Trennung der Netze | [show_vlan_brief_SW-CORE-01.png](../assets/screenshots/vlan/show_vlan_brief_SW-CORE-01.png) |
| Access-Ports | Endgeräte werden einem VLAN zugeordnet | [show_running_config_interfaces_SW-CORE-01.png](../assets/screenshots/vlan/show_running_config_interfaces_SW-CORE-01.png) |
| Trunk-Port | Transportiert mehrere VLANs zum Router oder Layer-3-Switch | [show_interfaces_trunk_SW-CORE-01.png](../assets/screenshots/vlan/show_interfaces_trunk_SW-CORE-01.png) |
| Default Gateways je VLAN | Leiten Verkehr zwischen VLANs weiter | Nicht vollständig als Screenshot vorhanden |
| Routing-Regeln / ACLs | Steuern erlaubte Kommunikation zwischen VLANs | Nicht vollständig als Screenshot vorhanden |

## Erwartetes Routing-Prinzip

Bei Router-on-a-Stick wuerde ein Router-Interface als Trunk angebunden. Pro VLAN wird eine Subinterface-Konfiguration mit 802.1Q-Tagging und Gateway-Adresse erstellt.

Beispielhaftes Prinzip:

```text
interface GigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0

interface GigabitEthernet0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0
```

Diese Beispielkonfiguration ist als Prinzip dokumentiert. Die konkrete vollständige Gateway-Konfiguration ist in den vorhandenen VLAN-Screenshots nicht sichtbar.

## Sicherheit beim Inter-VLAN-Routing

Inter-VLAN-Routing sollte nicht bedeuten, dass alle VLANs uneingeschraenkt miteinander kommunizieren dürfen. Besonders für ein Schulnetz sind Regeln sinnvoll:

| Richtung | Empfehlung |
| --- | --- |
| Lehrer zu Server | Erlauben, wenn für Unterricht oder Administration notwendig |
| Schüler zu Server | Nur benötigte Dienste erlauben |
| Gast/WLAN zu intern | Stark einschraenken oder blockieren |
| Administration zu Netzwerkgeräten | Erlauben, aber nur aus dem Admin-Netz |

## Fazit

Die vorhandenen Screenshots belegen die Layer-2-VLAN-Grundlage und den Trunk. Für einen vollständigen Nachweis des Inter-VLAN-Routings wären zusaetzlich Screenshots der Router-Subinterfaces oder Layer-3-SVIs sowie Tests zwischen verschiedenen VLANs sinnvoll.

