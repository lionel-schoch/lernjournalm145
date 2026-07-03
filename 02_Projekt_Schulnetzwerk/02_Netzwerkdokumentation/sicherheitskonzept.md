# Sicherheitskonzept

## Grundidee

Das Sicherheitskonzept basiert auf Segmentierung, kontrolliertem Routing und verschluesselter Standortverbindung. Die einzelnen Benutzergruppen werden am Hauptstandort durch VLANs getrennt. Die beiden Standorte kommunizieren ueber ein Site-to-Site-VPN, damit interne Daten nicht ungeschuetzt ueber das WAN-/Internet-Segment uebertragen werden.

## Segmentierung

Die Benutzergruppen werden logisch voneinander getrennt:

| Bereich | Sicherheitsziel |
| --- | --- |
| Lehrer | Zugriff auf benoetigte interne Dienste, getrennt von Schueler- und Gastgeraeten |
| Schueler | Zugriff auf Unterrichtsdienste, aber keine direkte Verwaltung des Netzwerks |
| Administration | Separater Bereich fuer administrative Arbeiten |
| Server | Zentraler Dienstbereich, Zugriff nur fuer berechtigte Netze |
| WLAN/Gast | Trennung vom internen Schulnetz, damit Gastgeraete nicht direkt auf interne Ressourcen zugreifen |

## VPN-Schutz zwischen den Standorten

Die Router `R-HQ-SCHULE-01` und `R-HQ-SCHULE-02` dienen als VPN-Endpunkte. Der standortuebergreifende Verkehr wird ueber das WAN-/Internet-Segment transportiert und per IPsec geschuetzt.

Die VPN-Nachweise sind unter [Screenshot-Nachweise](../assets/screenshots/README.md) dokumentiert. Dort sind unter anderem die Ausgaben zu ACLs, Crypto Maps, ISAKMP Security Associations und IPsec Security Associations beschrieben.

## Zugriffskontrolle

Fuer den VPN-Verkehr werden Access Control Lists verwendet. Diese ACLs definieren den interessanten Traffic, der ueber den Tunnel gesendet werden soll. Aus den vorhandenen Nachweisen geht hervor:

| Router | Erlaubter VPN-Traffic |
| --- | --- |
| `R-HQ-SCHULE-01` | Verkehr von `192.168.0.0/24` zu `10.10.0.0/24` |
| `R-HQ-SCHULE-02` | Verkehr zwischen der Aussenstelle und den Netzen des Hauptstandorts, unter anderem zu `192.168.0.0/24` |

## Routing und Begrenzung

Die Router verwenden Default Routen in Richtung WAN-/Internet-Segment. Interner Verkehr bleibt innerhalb des jeweiligen Standortnetzes, solange kein anderes Netz erreicht werden muss. Standortuebergreifender Verkehr wird ueber das VPN geleitet.

## Empfohlene Schutzmassnahmen

| Massnahme | Nutzen |
| --- | --- |
| VLANs konsequent dokumentieren und beschriften | Erleichtert Wartung und Fehlersuche |
| Nur benoetigte Netze ueber ACLs erlauben | Reduziert ungewollten Zugriff zwischen Standorten |
| Gast-WLAN vom internen Netz trennen | Schuetzt Server, Lehrer- und Administrationsgeraete |
| Router- und Switch-Zugriff mit sicheren Passwoertern schuetzen | Verhindert unberechtigte Konfigurationsaenderungen |
| Management-Zugriff nur aus dem Admin-Netz erlauben | Begrenzung administrativer Rechte auf vertrauenswuerdige Clients |
| Konfigurationen regelmaessig sichern | Wiederherstellung bei Fehlkonfiguration oder Geraeteausfall |

## Fazit

Durch die Kombination aus VLAN-Trennung, IPsec-VPN und gezielter Zugriffskontrolle ist das Schulnetz logisch strukturiert und gegen ungewollte Zugriffe besser geschuetzt. Die vorhandenen Screenshots belegen, dass die VPN-Komponenten konfiguriert und aktiv sind.
