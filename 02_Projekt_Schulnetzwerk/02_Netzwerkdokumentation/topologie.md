# Topologie

## Übersicht

Das Projekt bildet ein Schulnetzwerk mit zwei Standorten ab. Der Hauptstandort ist rechts im Diagramm dargestellt und arbeitet mit mehreren logisch getrennten Netzen für Lehrpersonen, Schüler, Administration und WLAN/Gastzugang. Der zweite Standort ist links dargestellt und ist über ein WAN-/Internet-Segment mit dem Hauptstandort verbunden.

![Netzwerk-Topologie](../assets/diagramme/netzwerk_topologie.png)

## Standort Hauptschule

Am Hauptstandort werden die internen Endgeräte über den Switch `SW-CORE-01` angebunden. Der Router `R-HQ-SCHULE-01` ist das zentrale Gateway des Standorts und verbindet das interne Netz mit dem WAN-/Internet-Segment.

Die Verbindung zwischen `R-HQ-SCHULE-01` und `SW-CORE-01` nutzt das interne Gateway `192.168.0.1`. Der Router ist ausserdem über `200.169.2.1` mit dem WAN verbunden. Am Switch sind mehrere Endgeräte und ein Access Point angeschlossen. Die eingezeichneten VLANs trennen die verschiedenen Benutzergruppen voneinander.

## Standort Aussenstelle

Die Aussenstelle verwendet den Switch `SW-CORE-02` und den Router `R-HQ-SCHULE-02`. Die internen Clients befinden sich im Netz `10.10.0.0/24`. Der Router stellt mit `10.10.0.1` das lokale Gateway bereit und ist über `200.169.1.1` mit dem WAN verbunden.

An `SW-CORE-02` sind ein Lehrer-Laptop und ein Schüler-PC angeschlossen. Die Aussenstelle ist damit als kleiner zweiter Standort aufgebaut, der über das WAN mit dem Hauptstandort kommunizieren kann.

## WAN-/Internet-Segment

Zwischen den beiden Routern befindet sich ein simuliertes Internet-Segment. Dieses Segment verbindet die beiden WAN-Netze:

| Verbindung | Lokales Interface | Gegenstelle | Zweck |
| --- | --- | --- | --- |
| Aussenstelle zu Internet | `R-HQ-SCHULE-02` mit `200.169.1.1` | Internet-Router `200.169.1.2` | WAN-Anbindung der Aussenstelle |
| Hauptstandort zu Internet | `R-HQ-SCHULE-01` mit `200.169.2.1` | Internet-Router `200.169.2.2` | WAN-Anbindung des Hauptstandorts |

## Kommunikationsprinzip

Die Clients kommunizieren lokal über ihren Switch und verwenden jeweils den Router als Default Gateway. Standortübergreifender Verkehr wird über das WAN-/Internet-Segment geleitet. Für die sichere Verbindung zwischen den Standorten wird ein Site-to-Site-VPN eingesetzt, damit die internen Netze geschützt miteinander kommunizieren können.

