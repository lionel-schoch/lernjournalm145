# VPN

In diesem Kapitel dokumentiere ich die sichere Standortverbindung zwischen Hauptstandort und Aussenstelle. Die Verbindung wird als IPsec Site-to-Site-VPN umgesetzt.

## Übersicht

| Datei | Inhalt |
| --- | --- |
| [konzept.md](konzept.md) | Ziel, Schutzbedarf und Grundidee der VPN-Verbindung |
| [ipsec_site_to_site.md](ipsec_site_to_site.md) | Beschreibung von Phase 1, Phase 2, ACLs und Crypto Maps |
| [konfiguration.md](konfiguration.md) | Dokumentierte Konfigurationsbestandteile anhand der Screenshots |
| [tests.md](tests.md) | VPN-Testfälle mit Routing, ISAKMP, IPsec und HTTPS-Test |

## Screenshot-Nachweise

Die VPN-Screenshots befinden sich hier:

[VPN-Nachweise](../assets/screenshots/README.md#vpn-nachweise)

## Zweck dieses Kapitels

Mit diesem Kapitel zeige ich, dass die beiden Standorte sicher miteinander verbunden sind. Die Screenshots belegen, dass Routing, ACLs, ISAKMP, IPsec und der praktische Zugriff auf einen entfernten Dienst funktionieren.
