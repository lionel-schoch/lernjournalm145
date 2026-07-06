# Lernprozess

## Einstieg

Zu Beginn des Projekts habe ich zuerst die Grundstruktur des Schulnetzwerks aufgebaut. Dabei ging es vor allem darum, die Standorte, Geräte und Netze sinnvoll zu ordnen. Die Topologie war für mich die wichtigste Grundlage, weil daraus die restliche Dokumentation entstanden ist.

## VLAN

Beim VLAN-Teil habe ich gelernt, wie wichtig eine klare logische Trennung ist. Durch VLAN 10, 20, 30 und 40 konnte ich die Bereiche Lehrer, Schüler, WLAN/Gast und Administration strukturieren. Besonders hilfreich waren die Befehle `show vlan brief`, `show interfaces trunk` und `show interfaces switchport`, weil sie direkt zeigen, ob die Konfiguration wirklich stimmt.

## WLAN

Beim WLAN-Teil habe ich den Access Point als eigenen Gast-/WLAN-Bereich dokumentiert. Mir wurde dabei klar, dass WLAN nicht nur “verbinden” bedeutet, sondern auch Sicherheit und Segmentierung umfasst. Deshalb habe ich WPA2-PSK/AES dokumentiert und den WLAN-Bereich dem VLAN 30 zugeordnet.

## VPN

Der VPN-Teil war technisch am anspruchsvollsten. Ich musste verstehen, dass IPsec aus mehreren Teilen besteht: ACL für interessanten Traffic, ISAKMP Phase 1, IPsec Phase 2 und Crypto Map. Die Screenshots haben mir geholfen, die Funktion des Tunnels Schritt für Schritt nachzuweisen.

## Dokumentation

Ich habe gemerkt, dass eine gute Dokumentation nicht nur aus Screenshots besteht. Wichtig ist, dass die Screenshots erklärt werden und der Leser versteht, was damit bewiesen wird. Deshalb habe ich für die Themenordner eigene README-Dateien erstellt und die wichtigsten Nachweise verlinkt.

## Fazit

Ich habe in diesem Projekt gelernt, ein Netzwerk nicht nur technisch aufzubauen, sondern auch nachvollziehbar zu dokumentieren und zu testen. Besonders wichtig war für mich die Verbindung zwischen Planung, Umsetzung, Nachweis und Reflexion.
