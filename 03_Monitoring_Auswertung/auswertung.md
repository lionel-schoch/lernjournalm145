# Auswertung

## Auswertung Packet Tracer

Im Packet-Tracer-Projekt wurde das VPN über CLI-Ausgaben und Funktionstests validiert. Die wichtigsten Nachweise sind:

- `show crypto isakmp sa`: VPN Phase 1 ist aktiv
- `show crypto ipsec sa`: VPN Phase 2 ist aktiv
- `show access-lists`: interessanter Traffic wird erkannt
- HTTPS-Test: Zugriff von der Aussenstelle auf den Server am Hauptstandort funktioniert

Damit ist nachgewiesen, dass die Standortverbindung nicht nur konfiguriert ist, sondern auch Datenverkehr verarbeitet.

## Bewertung der Ergebnisse

| Bereich | Ergebnis | Bewertung |
| --- | --- | --- |
| Erreichbarkeit | Server am Hauptstandort ist über VPN erreichbar | erfolgreich |
| Routing | Beide Router kennen ihre WAN-Route | erfolgreich |
| VPN Phase 1 | ISAKMP-SAs sind aktiv | erfolgreich |
| VPN Phase 2 | IPsec-SAs sind aktiv | erfolgreich |
| Datenverkehr | Paketzähler und HTTPS-Test zeigen Nutzung | erfolgreich |

## Grenzen der Auswertung

Packet Tracer ist eine Simulation. Deshalb fehlen echte Langzeitmessungen, echte Interface-Auslastung und direkte Grafana-Anbindung. Die CLI-Ausgaben reichen als technischer Nachweis für das Modulprojekt, ersetzen aber kein produktives Monitoring.

## Auswertung Grafana-Ansatz

Für ein echtes Monitoring würde ich WireGuard mit Prometheus und Grafana einsetzen. Dort könnten folgende Fragen beantwortet werden:

- Ist der VPN-Peer aktuell online?
- Wann war der letzte Handshake?
- Wie viel Traffic läuft über den Tunnel?
- Gibt es Paketverlust oder hohe Latenz?
- Ist der VPN-Server überlastet?

## Umgesetzter Stand

Ich konnte den WireGuard-Tunnel auf der Ubuntu-VM einrichten. Der Screenshot zeigt ein aktives `wg0`-Interface mit Listening Port `51820` und einem Peer.

![WireGuard VPN Status](assets/wireguard_vpn_status.png)

Bis zum Grafana-Dashboard bin ich nicht mehr gekommen. Deshalb kann ich in dieser Abgabe kein echtes Live-Dashboard zeigen. Fachlich ist aber dokumentiert, welche Metriken mit Prometheus und Grafana überwacht werden sollten.

## Fazit

Die Packet-Tracer-Auswertung zeigt, dass das VPN im Projekt funktioniert. Für produktionsnahes Monitoring ist eine echte Umgebung mit WireGuard, Prometheus und Grafana besser geeignet, weil dort Messwerte automatisch und über Zeit erfasst werden können.
