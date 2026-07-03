# Sicherheitskonzept

## Grundidee

Das Sicherheitskonzept basiert auf Segmentierung, kontrolliertem Routing und verschlüsselter Standortverbindung. Die einzelnen Benutzergruppen werden am Hauptstandort durch VLANs getrennt. Die beiden Standorte kommunizieren über ein Site-to-Site-VPN, damit interne Daten nicht ungeschützt über das WAN-/Internet-Segment übertragen werden.

## Segmentierung

Die Benutzergruppen werden logisch voneinander getrennt:

| Bereich | Sicherheitsziel |
| --- | --- |
| Lehrer | Zugriff auf benötigte interne Dienste, getrennt von Schüler- und Gastgeräten |
| Schüler | Zugriff auf Unterrichtsdienste, aber keine direkte Verwaltung des Netzwerks |
| Administration | Separater Bereich für administrative Arbeiten |
| Server | Zentraler Dienstbereich, Zugriff nur für berechtigte Netze |
| WLAN/Gast | Trennung vom internen Schulnetz, damit Gastgeräte nicht direkt auf interne Ressourcen zugreifen |

## VPN-Schutz zwischen den Standorten

Die Router `R-HQ-SCHULE-01` und `R-HQ-SCHULE-02` dienen als VPN-Endpunkte. Der standortübergreifende Verkehr wird über das WAN-/Internet-Segment transportiert und per IPsec geschützt.

Die VPN-Nachweise sind unter [Screenshot-Nachweise](../assets/screenshots/README.md) dokumentiert. Dort sind unter anderem die Ausgaben zu ACLs, Crypto Maps, ISAKMP Security Associations und IPsec Security Associations beschrieben.

## Zugriffskontrolle

Für den VPN-Verkehr werden Access Control Lists verwendet. Diese ACLs definieren den interessanten Traffic, der über den Tunnel gesendet werden soll. Aus den vorhandenen Nachweisen geht hervor:

| Router | Erlaubter VPN-Traffic |
| --- | --- |
| `R-HQ-SCHULE-01` | Verkehr von `192.168.0.0/24` zu `10.10.0.0/24` |
| `R-HQ-SCHULE-02` | Verkehr zwischen der Aussenstelle und den Netzen des Hauptstandorts, unter anderem zu `192.168.0.0/24` |

## Routing und Begrenzung

Die Router verwenden Default Routen in Richtung WAN-/Internet-Segment. Interner Verkehr bleibt innerhalb des jeweiligen Standortnetzes, solange kein anderes Netz erreicht werden muss. Standortübergreifender Verkehr wird über das VPN geleitet.

## Empfohlene Schutzmassnahmen

| Massnahme | Nutzen |
| --- | --- |
| VLANs konsequent dokumentieren und beschriften | Erleichtert Wartung und Fehlersuche |
| Nur benötigte Netze über ACLs erlauben | Reduziert ungewollten Zugriff zwischen Standorten |
| Gast-WLAN vom internen Netz trennen | Schuetzt Server, Lehrer- und Administrationsgeräte |
| Router- und Switch-Zugriff mit sicheren Passwoertern schuetzen | Verhindert unberechtigte Konfigurationsaenderungen |
| Management-Zugriff nur aus dem Admin-Netz erlauben | Begrenzung administrativer Rechte auf vertrauenswuerdige Clients |
| Konfigurationen regelmässig sichern | Wiederherstellung bei Fehlkonfiguration oder Geräteausfall |

## Fazit

Durch die Kombination aus VLAN-Trennung, IPsec-VPN und gezielter Zugriffskontrolle ist das Schulnetz logisch strukturiert und gegen ungewollte Zugriffe besser geschützt. Die vorhandenen Screenshots belegen, dass die VPN-Komponenten konfiguriert und aktiv sind.

