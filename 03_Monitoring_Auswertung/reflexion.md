# Reflexion

## Was ich gelernt habe

Beim Monitoring-Teil wurde mir klar, dass zwischen einer Simulation und echtem Betrieb ein wichtiger Unterschied besteht. In Cisco Packet Tracer kann ich Konfigurationen und Befehle testen, aber ich kann die Geräte nicht wie echte Router direkt mit Grafana überwachen.

Für eine schulische Abgabe ist Packet Tracer gut geeignet, um den technischen Zustand des VPNs mit CLI-Befehlen nachzuweisen. Für echtes Monitoring braucht es aber eine Umgebung, die Metriken bereitstellt.

## Entscheidung

Ich habe mich deshalb für zwei Ebenen entschieden:

1. Im Packet-Tracer-Projekt dokumentiere ich den VPN-Zustand mit Screenshots und CLI-Ausgaben.
2. Für eine realistische Monitoring-Erweiterung beschreibe ich WireGuard mit Prometheus und Grafana.

Diese Trennung ist für mich sinnvoll, weil sie ehrlich zeigt, was Packet Tracer kann und wo eine echte Monitoring-Lösung notwendig wird.

## Grenzen

Folgende Punkte konnte ich in Packet Tracer nicht realistisch messen:

- Langzeitverfügbarkeit
- echte Bandbreite
- CPU-Auslastung der Router
- Grafana-Dashboard mit Live-Daten
- echte SNMP- oder Prometheus-Metriken

## Verbesserung

Wenn ich mehr Zeit hätte, würde ich das WireGuard-/Grafana-Lab praktisch aufbauen und Screenshots eines Dashboards ergänzen. Damit könnte ich den Monitoring-Teil noch stärker belegen.

## Fazit

Der Monitoring-Teil ergänzt mein Projekt, weil ich nicht nur zeige, dass das VPN funktioniert, sondern auch erkläre, wie ich den Betrieb überwachen würde. Damit wird die Dokumentation näher an eine reale Netzwerkumgebung gebracht.
