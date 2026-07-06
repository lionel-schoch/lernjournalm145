# Projektziele

## Hauptziel

Das Ziel des Projekts ist der Aufbau und die Dokumentation eines strukturierten Schulnetzwerks mit VLAN-Segmentierung, WLAN-/Gastbereich und sicherer VPN-Verbindung zwischen Hauptstandort und Aussenstelle.

## Fachliche Ziele

| Ziel | Beschreibung | Nachweis |
| --- | --- | --- |
| Netzwerk dokumentieren | Die physikalische und logische Topologie wird verständlich beschrieben. | Netzwerkdokumentation mit Topologie, Geräteliste und IP-Adressierung |
| VLANs umsetzen | Die Benutzergruppen werden logisch getrennt. | VLAN-Dokumentation und VLAN-Screenshots |
| Trunking prüfen | VLANs werden über den Uplink transportiert. | `show interfaces trunk` |
| VPN einrichten | Die Standortnetze werden sicher verbunden. | ISAKMP-, IPsec- und HTTPS-Nachweise |
| WLAN/Gastbereich planen | Der Access Point wird einem eigenen Bereich zugeordnet. | WLAN-Konzept und SSID-/VLAN-Mapping |
| Tests dokumentieren | Die Funktion wird mit Testplan und Testprotokoll überprüft. | Test- und Validierungsdokumente |
| Fehler behandeln | Typische Fehler werden beschrieben und mit Massnahmen versehen. | Troubleshooting-Dokument |

## Qualitätsziele

Die Abgabe soll nicht nur Konfigurationen zeigen, sondern begründen, warum die Lösung sinnvoll ist. Besonders wichtig sind:

- klare Struktur im Repository
- nachvollziehbare Markdown-Dokumentation
- Screenshots als Beweis der Funktionalität
- fachliche Begründung der VLAN- und VPN-Lösung
- dokumentierte Tests und mögliche Fehler
- Reflexion über Grenzen und Verbesserungen

## Abgrenzung

Das Projekt wird in Cisco Packet Tracer umgesetzt. Dadurch können einzelne produktive Funktionen nur simuliert werden. Beispielsweise können Monitoring-Werte, WLAN-Signalstärke oder echte VPN-Performance nur eingeschränkt realistisch gemessen werden. Diese Grenzen werden in der Dokumentation berücksichtigt.

## Erfolgskriterien

Das Projekt gilt als erfolgreich, wenn:

1. die Netzwerkstruktur verständlich dokumentiert ist,
2. VLANs angelegt und getestet sind,
3. der Trunk aktiv ist,
4. die VPN-Verbindung zwischen den Standorten funktioniert,
5. mindestens ein Dienst standortübergreifend erreichbar ist,
6. Tests und mögliche Fehler nachvollziehbar dokumentiert sind,
7. die Dokumentation den Anforderungen des Moduls 145 entspricht.
