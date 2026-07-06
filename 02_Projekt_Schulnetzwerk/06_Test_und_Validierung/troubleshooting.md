# Troubleshooting

## Vorgehen

Fehler werden systematisch analysiert. Das Vorgehen orientiert sich an folgendem Schema:

1. Symptom beschreiben
2. Mögliche Ursache formulieren
3. Test oder Diagnosebefehl ausführen
4. Ergebnis bewerten
5. Massnahme umsetzen
6. Funktion erneut validieren

## Mögliche Fehler und Massnahmen

### Fehler 1: Client erreicht anderes Gerät im gleichen VLAN nicht

| Punkt | Beschreibung |
| --- | --- |
| Symptom | Ping zwischen zwei Lehrer-Clients funktioniert nicht. |
| Mögliche Ursache | Falsche IP-Adresse, falsches VLAN am Switchport oder Port ist down. |
| Diagnose | `ipconfig` am Client, `show interfaces status`, `show interfaces fa0/1 switchport`, Ping zum Gateway. |
| Massnahme | IP-Adresse korrigieren, Switchport dem richtigen VLAN zuordnen, Kabel/Port prüfen. |
| Validierung | Ping erneut ausführen und Paketverlust kontrollieren. |

### Fehler 2: VLAN ist nicht vorhanden

| Punkt | Beschreibung |
| --- | --- |
| Symptom | Ein Port kann nicht korrekt einem VLAN zugeordnet werden oder VLAN erscheint nicht in der Übersicht. |
| Mögliche Ursache | VLAN wurde auf dem Switch nicht erstellt. |
| Diagnose | `show vlan brief` |
| Massnahme | VLAN anlegen, Namen vergeben und Konfiguration speichern. |
| Validierung | `show vlan brief` erneut prüfen. |

### Fehler 3: Trunk transportiert ein VLAN nicht

| Punkt | Beschreibung |
| --- | --- |
| Symptom | Geräte in einem VLAN funktionieren lokal, aber nicht über den Uplink. |
| Mögliche Ursache | VLAN ist auf dem Trunk nicht erlaubt oder Trunk ist nicht aktiv. |
| Diagnose | `show interfaces trunk` |
| Massnahme | Trunk aktivieren und erlaubte VLANs prüfen/anpassen. |
| Validierung | VLAN-Kommunikation über Uplink testen. |

### Fehler 4: Standortübergreifender Verkehr funktioniert nicht

| Punkt | Beschreibung |
| --- | --- |
| Symptom | Client der Aussenstelle erreicht den Server am Hauptstandort nicht. |
| Mögliche Ursache | Fehlende Default Route, falsches Gateway, VPN ACL passt nicht oder Tunnel ist inaktiv. |
| Diagnose | `show ip route`, Ping WAN-Peer, `show access-lists`, `show crypto isakmp sa`, `show crypto ipsec sa`. |
| Massnahme | Routing korrigieren, ACL prüfen, Crypto Map und Peer-Adresse kontrollieren. |
| Validierung | HTTPS-Test auf `https://192.168.0.10` wiederholen. |

### Fehler 5: VPN Phase 1 ist nicht aktiv

| Punkt | Beschreibung |
| --- | --- |
| Symptom | `show crypto isakmp sa` zeigt keine aktive Security Association. |
| Mögliche Ursache | Falsche Peer-Adresse, falscher Pre-Shared-Key, falsche ISAKMP-Parameter oder keine WAN-Erreichbarkeit. |
| Diagnose | Ping zur Peer-WAN-IP, `show crypto isakmp sa`, Kontrolle der ISAKMP-Konfiguration. |
| Massnahme | Peer-IP, Key und ISAKMP-Policy auf beiden Routern vergleichen und korrigieren. |
| Validierung | `show crypto isakmp sa` muss Status `ACTIVE` zeigen. |

### Fehler 6: VPN Phase 2 baut nicht auf

| Punkt | Beschreibung |
| --- | --- |
| Symptom | ISAKMP ist aktiv, aber `show crypto ipsec sa` zeigt keine oder keine steigenden Paketzähler. |
| Mögliche Ursache | ACL für interessanten Traffic ist falsch, Transform-Set passt nicht oder Crypto Map ist nicht am Interface aktiv. |
| Diagnose | `show access-lists`, `show crypto map`, `show crypto ipsec sa`. |
| Massnahme | ACL-Spiegelung prüfen, Transform-Set vergleichen und Crypto Map am WAN-Interface anwenden. |
| Validierung | Erneut Traffic erzeugen und Paketzähler prüfen. |

### Fehler 7: WLAN-/Gastgerät ist im falschen Netz

| Punkt | Beschreibung |
| --- | --- |
| Symptom | WLAN-Client erhält eine Adresse aus dem falschen Netz oder erreicht interne Ressourcen ungewollt. |
| Mögliche Ursache | AP-Port ist falschem VLAN zugeordnet oder SSID-/VLAN-Mapping ist falsch. |
| Diagnose | IP-Adresse des WLAN-Clients prüfen, Switchport-Konfiguration AP-Port prüfen. |
| Massnahme | AP-Port oder SSID dem richtigen VLAN zuordnen. |
| Validierung | Client neu verbinden und IP-Adresse/Zugriff erneut prüfen. |

## Fehlerdokumentation

Bei einem echten Fehler wird folgender Eintrag verwendet:

| Feld | Inhalt |
| --- | --- |
| Datum |  |
| Gerät |  |
| Symptom |  |
| Vermutete Ursache |  |
| Diagnosebefehle |  |
| Ergebnis |  |
| Massnahme |  |
| Validierung |  |

## Fazit

Die wahrscheinlichsten Fehlerquellen liegen bei VLAN-Zuordnung, Trunk-Konfiguration, Routing und VPN-Parametern. Mit den dokumentierten Diagnosebefehlen können diese Fehler strukturiert eingegrenzt und behoben werden.
