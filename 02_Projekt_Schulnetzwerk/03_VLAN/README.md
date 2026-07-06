# VLAN

In diesem Kapitel dokumentiere ich die VLAN-Umsetzung im Schulnetzwerk. Ziel ist die logische Trennung der Benutzergruppen Lehrer, Schüler, WLAN/Gast und Administration.

## Übersicht

| Datei | Inhalt |
| --- | --- |
| [konzept.md](konzept.md) | Fachliches VLAN-Konzept und Begründung der Segmentierung |
| [konfiguration.md](konfiguration.md) | Dokumentation der VLANs, Access-Ports und Switch-Konfiguration |
| [trunking.md](trunking.md) | Beschreibung des Trunk-Ports und der übertragenen VLANs |
| [inter_vlan_routing.md](inter_vlan_routing.md) | Erklärung des Inter-VLAN-Routing-Prinzips und der benötigten Bausteine |
| [tests.md](tests.md) | VLAN-Testfälle und Bewertung der Nachweise |

## Screenshot-Nachweise

Die VLAN-Screenshots befinden sich hier:

[VLAN-Nachweise](../assets/screenshots/README.md#vlan-nachweise)

## Zweck dieses Kapitels

Mit diesem Kapitel zeige ich, dass ich ein logisches Netzwerkkonzept entwickeln, umsetzen und testen kann. Die VLANs reduzieren Broadcast-Domänen und verbessern die Trennung zwischen den Benutzergruppen.
