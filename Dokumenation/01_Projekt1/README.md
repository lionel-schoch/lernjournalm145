# Projektdokumentation - Schulnetzwerk mit VLAN, WLAN und Standortverbindung

## 1. Ausgangslage

Im Modul 145 wird ein Schulnetzwerk in Cisco Packet Tracer geplant, umgesetzt und dokumentiert. Das Projekt umfasst einen Hauptstandort und eine kleine Aussenstelle, zum Beispiel eine Sporthalle oder ein zweites Schulgebäude.

Das Netzwerk soll übersichtlich, sicher und nachvollziehbar aufgebaut sein. Verschiedene Benutzergruppen wie Administration, Lehrpersonen, Schülerinnen und Schüler sowie Gäste werden logisch voneinander getrennt. Zusätzlich werden ein internes WLAN, ein Gäste-WLAN und eine simulierte Standortverbindung geplant.

Die Dokumentation konzentriert sich auf die wichtigsten fachlichen Entscheide und Nachweise. Sie wird während der Umsetzung mit Screenshots, Tests und kurzen Reflexionen ergänzt.

## 2. Projektziel

Ziel ist eine funktionierende und sauber dokumentierte Netzwerklösung für eine Schule. Die Lösung soll zeigen, wie VLANs, WLANs und eine Standortverbindung sinnvoll kombiniert werden können.

Im Fokus stehen:

- klare Trennung der Benutzergruppen mit VLANs
- strukturiertes IP-Adresskonzept
- Inter-VLAN-Routing für erlaubte Verbindungen
- internes WLAN und separates Gäste-WLAN
- Isolation des Gäste-Netzes
- simulierte Standortverbindung zur Aussenstelle
- verständliche Netzwerkdokumentation mit Tests

## 3. Projektumfang

### Enthalten

- Hauptstandort mit Router, Core-Switch, Clients, Server und Access Points
- Aussenstelle mit Router, Switch und Clients
- VLAN- und IP-Konzept
- Switch-Ports für Access- und Trunk-Verbindungen
- Inter-VLAN-Routing
- WLAN-Konzept für interne Geräte und Gäste
- fachliche Beschreibung einer Site-to-Site-VPN-Verbindung
- grundlegende Verbindungstests

### Nicht im Fokus

- produktive Firewall- oder VPN-Konfiguration
- Hochverfügbarkeit
- zentrale Benutzerverwaltung
- umfassendes Monitoring
- echte Internetanbindung

Diese Punkte wären in einer realen Umgebung wichtig, werden in diesem Projekt aber bewusst nur am Rand erwähnt.

## 4. Projektstatus

| Bereich | Status |
|---|---|
| Projektidee | abgeschlossen |
| Grobplanung | abgeschlossen |
| VLAN- und IP-Konzept | geplant |
| Packet-Tracer-Topologie | in Bearbeitung |
| VLAN-Konfiguration | begonnen |
| WLAN-Konfiguration | offen |
| Standortverbindung | offen |
| Tests und Nachweise | offen |
| Abschlussreflexion | offen |

## 5. Anforderungen

| Nr. | Anforderung | Beschreibung |
|---:|---|---|
| F01 | VLAN-Trennung | Benutzergruppen werden logisch getrennt. |
| F02 | Inter-VLAN-Routing | Erlaubte Kommunikation zwischen VLANs ist möglich. |
| F03 | WLAN | Internes WLAN und Gäste-WLAN sind getrennt. |
| F04 | Gäste-Isolation | Gäste erreichen keine internen Schulressourcen. |
| F05 | Standortverbindung | Die Aussenstelle ist mit dem Hauptstandort verbunden. |
| F06 | Dokumentation | Aufbau, Adressen, Ports und Tests sind nachvollziehbar dokumentiert. |

| Nr. | Qualitätsanforderung | Beschreibung |
|---:|---|---|
| Q01 | Sicherheit | Interne und externe Benutzergruppen sind getrennt. |
| Q02 | Übersichtlichkeit | Namen, VLANs und IP-Adressen folgen einer klaren Struktur. |
| Q03 | Wartbarkeit | Die Lösung ist auch später verständlich und erweiterbar. |
| Q04 | Testbarkeit | Die wichtigsten Verbindungen können geprüft werden. |

## 6. Netzwerkarchitektur

Das Netzwerk besteht aus zwei Standorten.

| Standort | Inhalt |
|---|---|
| Hauptstandort | Router, Core-Switch, Server, Clients, internes WLAN, Gäste-WLAN |
| Aussenstelle | Router, Switch, Clients, eigenes Subnetz |

Die Aussenstelle wird in Packet Tracer über eine WAN-Verbindung dargestellt. Fachlich entspricht dies einer Site-to-Site-VPN-Verbindung.

## 7. Geräte und Namen

| Gerät | Name | IP |
|---|---|---|
| Router Hauptstandort | R-HQ-SCHULE | Routing und Verbindung zur Aussenstelle |
| Router Aussenstelle | R-BR-SPORT | Verbindung zum Hauptstandort |
| Core-Switch | SW-CORE-01 | zentrale Verteilung |
| Switch Aussenstelle | SW-BR-SPORT | Anschluss der Geräte vor Ort |
| Server | SRV-INTRANET | interner Dienst, zum Beispiel Schulportal |
| Access Point intern | AP-INTERN-01 | internes WLAN |
| PC | PC-LEHRER-01 | 192.168.10.10 |
| PC | PC-LEHRER-02 | 192.168.10.11 |
| PC | PC-LEHRER-03 | 192.168.10.12 |
| PC | PC-SCHUELER-01 | 192.168.20.10 |
| PC | PC-SCHUELER-02 | 192.168.20.11 |
| PC | PC-ADMIN-01 | 192.168.40.10 |
| PC | AP-GUEST-01 | 192.168.10.10 |
| PC | AP-GUEST-02 | 192.168.10.11 |


Die Namen sind bewusst kurz und sprechend gewählt, damit die Dokumentation auch ohne zusätzliche Erklärung verständlich bleibt.

## 8. VLAN- und IP-Konzept

Für das Projekt wird der private Adressbereich `192.168.0.0/16` verwendet. Jedes VLAN erhält ein eigenes `/24`-Subnetz. Die Gateway-Adresse ist jeweils die erste nutzbare Adresse.

| VLAN | Name | Subnetz | Gateway |
|---:|---|---|---|
| 10 | Lehrer | 192.168.10.0/24 | 192.168.10.1 |
| 20 | Schüler | 192.168.20.0/24 | 192.168.20.1 |
| 30 | Gäste | 192.168.30.0/24 | 192.168.30.1 |
| 40 | Admin | 192.168.40.0/24 | 192.168.40.1 |


## 9. Portstruktur

Die Portstruktur wird während der Umsetzung bei Bedarf angepasst.

| Gerät | Port | Verbindung | Modus | VLAN |
|---|---|---|---|---|
| SW-CORE-01 | G0/1 | R-HQ-SCHULE | Trunk | - |
| SW-CORE-01 | F0/1 | PC-LEHRER-01 | Access | 10 |
| SW-CORE-01 | F0/2 | PC-SCHUELER-01 | Access | 20 |
| SW-CORE-01 | F0/3 | AP-GUEST-01 | Access | 30 |
| SW-CORE-01 | F0/4 | PC-ADMIN-01 | Access | 40 |
| SW-CORE-01 | F0/5 | PC-LEHRER-02 | Access | 10 |
| SW-BR-SPORT | F0/1 | PC-LEHRER-03 | Access | 10 |
| SW-BR-SPORT | F0/2 | PC-SCHUELER-02 | Access | 20 |
| SW-BR-SPORT | F0/3 | AP-GUEST-01 | Access | 30 |

## 10. WLAN-Konzept

| WLAN | SSID | VLAN | Subnetz | Sicherheit | Zweck |
|---|---|---:|---|---|---|
| Intern | SCHULE-INTERN | 70 | 192.168.70.0/24 | WPA2-PSK | berechtigte interne Geräte |
| Gäste | SCHULE-GUEST | 50 | 192.168.50.0/24 | WPA2-PSK | separater Gastzugang |

Das Gäste-WLAN wird vom internen Netzwerk getrennt. Gäste dürfen keine Server, Administrationsgeräte oder Management-Systeme erreichen.

## 11. Zugriffskonzept

| Quelle | Ziel | Zugriff | Grund |
|---|---|---|---|
| Administration | interne Netze | erlaubt | administrative Aufgaben |
| Lehrer | Servernetz | erlaubt | Zugriff auf interne Dienste |
| Schüler | Servernetz | erlaubt | Zugriff auf Schulportal |
| Schüler | Administration | gesperrt | Schutz administrativer Daten |
| Gäste | interne Netze | gesperrt | Schutz der Schulressourcen |
| Gäste | Gateway / Internet | erlaubt | Gastzugang |
| Management | Netzwerkgeräte | erlaubt | Verwaltung der Infrastruktur |

Die technische Umsetzung erfolgt über Routing und Access Control Lists. Die genaue Konfiguration wird nach der Umsetzung ergänzt.

## 12. Standortverbindung

Die Aussenstelle wird über zwei Router mit dem Hauptstandort verbunden. In Packet Tracer wird dies als WAN-Verbindung simuliert. In einer echten Umgebung würde dafür ein verschlüsseltes Site-to-Site-VPN, zum Beispiel mit IPsec, eingesetzt.

| Bereich | Netz |
|---|---|
| WAN-Verbindung | 10.0.0.0/30 |
| Hauptstandort | 192.168.10.0/24 bis 192.168.70.0/24 |
| Aussenstelle | 192.168.80.0/24 |

| Gerät | Interface | IP-Adresse |
|---|---|---|
| R-HQ-SCHULE | WAN | 10.0.0.1/30 |
| R-BR-SPORT | WAN | 10.0.0.2/30 |
| R-BR-SPORT | LAN | 192.168.80.1/24 |

## 13. Geplante Topologie

```text
                         [R-BR-SPORT]
                              |
                        [SW-BR-SPORT]
                         /          \
                 Lehrer-PC       Schüler-PC

                         WAN / VPN
                        10.0.0.0/30

                         [R-HQ-SCHULE]
                              |
                        [SW-CORE-01]
                    /     |      |      \
             Admin-PC  Lehrer-PC Schüler-PC SRV-INTRANET
                              |
                    AP-INTERN / AP-GUEST
```

## 14. Testplan

| Test | Erwartetes Ergebnis |
|---|---|
| Client erhält korrekte IP-Adresse | IP-Adresse passt zum VLAN |
| Ping innerhalb eines VLANs | Verbindung funktioniert |
| Erlaubter Zugriff auf Servernetz | Verbindung funktioniert |
| Schüler zu Administration | Verbindung wird blockiert |
| Gast zu internem Netz | Verbindung wird blockiert |
| Hauptstandort zu Aussenstelle | Verbindung funktioniert |

Die Testergebnisse werden nach der Konfiguration mit kurzen Notizen und Screenshots ergänzt.

## 15. Zeitplanung

Das Projekt ist für drei Wochen mit je vier Lektionen geplant.

| Woche | Lektionen | Inhalt | Ergebnis |
|---:|---:|---|---|
| 1 | 4 | Planung, Topologie, VLAN- und IP-Konzept | klare Grundlage für die Umsetzung |
| 2 | 4 | VLANs, Routing, Ports und erste Tests | Grundnetz funktioniert |
| 3 | 4 | WLAN, Standortverbindung, Tests und Dokumentation | Projekt abgeschlossen und dokumentiert |

## 16. Aktueller Zwischenstand

Die Grundidee und die Planung des Schulnetzwerks sind erstellt. Die wichtigsten Bereiche wie VLANs, IP-Adressierung, WLAN, Aussenstelle und Zugriffskonzept sind definiert. In Cisco Packet Tracer wurde die Umsetzung bereits begonnen.

Aktuell liegt der Fokus auf dem Aufbau der Topologie und der VLAN-Konfiguration am Core-Switch. Erste Nachweise wurden mit Screenshots festgehalten. Die Dokumentation wird parallel zur technischen Umsetzung laufend ergänzt.

| Bereich | Zwischenstand |
|---|---|
| Planung | Grundstruktur ist definiert |
| IP-Adressierung | VLAN-Netze und Gateways sind festgelegt |
| Topologie | in Packet Tracer aufgebaut bzw. in Bearbeitung |
| Core-Switch | erste Konfiguration begonnen |
| WLAN | geplant, Umsetzung noch offen |
| Standortverbindung | geplant, Umsetzung noch offen |
| Tests | Testplan vorhanden, Durchführung folgt |

## 17. Offene Fragen

Mit zwei Fragen beschäftige ich mich schon seit Längerem:
- Werden die VLAN auf dem Router oder dem Switch hinterlegt? Ich habe gesehen, dass beides möglich ist, aber ich habe immer wieder die Lösung mit dem Switch gesehen. Ich finde es jedoch besser, wenn die VLANs auf dem Router schon definiert werden.
-  Werden zwischen den VLANs verschiedene Subnets gebraucht oder oder spielt das keine Rolle?


## Testfälle Projekt 1

### Testfall 1: Admin-PC erreicht das Gateway

| Punkt | Beschreibung |
|---|---|
| Ziel | Prüfen, ob VLAN 20 korrekt funktioniert |
| Quelle | PC-ADMIN, 192.168.20.10 |
| Ziel | Gateway, 192.168.20.1 |
| Befehl | `ping 192.168.20.1` |
| Erwartung | Ping funktioniert |

Ich habe zuerst den Admin-PC getestet. Die IP-Adresse, Subnetzmaske und das Gateway waren korrekt eingetragen. Danach habe ich das Gateway angepingt.

**Ergebnis:** Der Ping war erfolgreich. Der Admin-PC ist im richtigen VLAN und erreicht sein Gateway.

### Testfall 2: Schüler-PC darf den Admin-PC nicht erreichen

| Punkt | Beschreibung |
|---|---|
| Ziel | Prüfen, ob das Administrationsnetz geschützt ist |
| Quelle | PC-SCHUELER, 192.168.40.10 |
| Ziel | PC-ADMIN, 192.168.20.10 |
| Befehl | `ping 192.168.20.10` |
| Erwartung | Ping wird blockiert |

Ich habe vom Schüler-PC aus den Admin-PC angepingt. Dieser Zugriff sollte nicht möglich sein, weil das Schülernetz keinen Zugriff auf administrative Geräte haben darf.

**Ergebnis:** Der Ping wurde blockiert. Die Trennung zwischen Schülernetz und Administration funktioniert.

### Testfall 3: Verbindung zur Aussenstelle

| Punkt | Beschreibung |
|---|---|
| Ziel | Prüfen, ob Hauptstandort und Aussenstelle verbunden sind |
| Quelle | PC-ADMIN, 192.168.20.10 |
| Ziel | PC-BR-LEHRER, 192.168.80.10 |
| Befehl | `ping 192.168.80.10` |
| Erwartung | Ping funktioniert |

Ich habe vom Admin-PC einen Client in der Aussenstelle angepingt. Damit wollte ich prüfen, ob die WAN-Verbindung und das Routing zwischen den Routern korrekt funktionieren.

**Ergebnis:** Der Ping war erfolgreich. Die Aussenstelle ist vom Hauptstandort aus erreichbar.

## 19. Persönlicher Lernprozess

Ich persönlich habe bei diesem Projekt schon sehr viel über VLANs und den Cisco Paket Tracer gelernt. Für das Modul habe ich mir bewusst vorgenommen, alles mit dem Cisco Packet Tracer zu machen, da ich bisher noch nicht wirklich die Gelegenheit hatte, mich mit diesem Programm vertraut zu machen. Daher lerne ich bei der Arbeit mit dem Programm sehr viel über diese Applikation.
Auch mit VLANs hatte ich bisher noch nie zu tun und in der Schule wurde das Thema nie ausführlich behandelt. Daher ist dies auch ein ziemlich neues Terrain für mich.

