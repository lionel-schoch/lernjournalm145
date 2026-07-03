# Konzept

## Ziel

Ziel der VPN-Umsetzung ist eine sichere Standortverbindung zwischen dem Hauptstandort und der Aussenstelle. Die beiden internen Netze sollen miteinander kommunizieren koennen, ohne dass der interne Datenverkehr ungeschuetzt ueber das simulierte Internet uebertragen wird.

## Ausgangslage

Das Projekt besteht aus zwei Schulstandorten:

| Standort | Router | Internes Netz | WAN-Adresse |
| --- | --- | --- | --- |
| Hauptstandort | `R-HQ-SCHULE-01` | `192.168.0.0/24` | `200.169.2.1` |
| Aussenstelle | `R-HQ-SCHULE-02` | `10.10.0.0/24` | `200.169.1.1` |

Zwischen den beiden Routern befindet sich ein simuliertes Internet-Segment. Die Kommunikation zwischen den Standorten wird ueber ein Site-to-Site-VPN abgesichert.

## VPN-Art

Umgesetzt wird ein IPsec Site-to-Site-VPN. Beide Router bilden dabei je einen festen VPN-Endpunkt. Sobald Verkehr zwischen den definierten internen Netzen entsteht, wird dieser Verkehr als interessanter Traffic erkannt und ueber den IPsec-Tunnel gesendet.

## Schutzbedarf

Der VPN-Tunnel schuetzt den Verkehr zwischen den Standorten. Besonders relevant ist dies fuer Zugriffe auf interne Dienste, zum Beispiel den HTTPS-Zugriff von einem Client der Aussenstelle auf den Server am Hauptstandort.

| Schutzaspekt | Umsetzung |
| --- | --- |
| Vertraulichkeit | Nutzdaten werden durch IPsec verschluesselt. |
| Integritaet | IPsec prueft, ob Pakete unveraendert ankommen. |
| Authentifizierung | Die VPN-Endpunkte authentifizieren sich in der ISAKMP-/IKE-Phase. |
| Zugriffseingrenzung | ACLs definieren, welche Netze den Tunnel verwenden duerfen. |

## Interessanter Traffic

Der interessante Traffic wird ueber Extended Access Lists definiert. Aus den Screenshots ist ersichtlich, dass vor allem der Verkehr zwischen `192.168.0.0/24` und `10.10.0.0/24` ueber den VPN-Tunnel laufen soll.

| Richtung | Quellnetz | Zielnetz |
| --- | --- | --- |
| Hauptstandort zu Aussenstelle | `192.168.0.0/24` | `10.10.0.0/24` |
| Aussenstelle zu Hauptstandort | `10.10.0.0/24` | `192.168.0.0/24` |

## Nachweis

Die erfolgreiche Umsetzung wird durch Screenshots belegt. Die Nachweise zeigen Routing, ACLs, Crypto Maps, ISAKMP Security Associations, IPsec Security Associations und einen funktionalen HTTPS-Test.

Die Screenshot-Uebersicht befindet sich unter [Screenshot-Nachweise](../assets/screenshots/README.md).
