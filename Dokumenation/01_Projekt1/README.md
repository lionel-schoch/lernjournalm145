# Projektdokumentation – Planung Schulnetzwerk mit VLAN, WLAN und VPN

## 1. Ausgangslage

Im Rahmen des Moduls 145 wird ein praxisnahes Netzwerkprojekt in Cisco Packet Tracer geplant und umgesetzt. Der Schwerpunkt dieses Projekts liegt auf den Themen **Netzwerkdokumentation**, **VLAN**, **WLAN** und **VPN beziehungsweise Standortverbindung**.

Für das Projekt wird ein Schulnetzwerk simuliert. Die Schule besteht aus einem Hauptstandort und einer kleinen Aussenstelle, zum Beispiel einer Sporthalle oder einem zweiten Schulgebäude. Innerhalb des Netzwerks sollen verschiedene Benutzergruppen sauber voneinander getrennt werden. Dazu gehören die Administration, Lehrpersonen, Schülerinnen und Schüler sowie Gäste.

Zusätzlich soll die Schule über ein internes WLAN und ein Gäste-WLAN verfügen. Die Aussenstelle soll über eine sichere Standortverbindung mit dem Hauptstandort verbunden werden.

Die Umsetzung in Cisco Packet Tracer wurde bereits begonnen. Diese Dokumentation beschreibt aktuell vor allem die **Planung**, das vorgesehene Konzept und die geplante technische Umsetzung. Die endgültigen Ergebnisse, Tests und Nachweise werden nach Abschluss der Konfiguration ergänzt.

---

## 2. Projektstatus

Das Projekt befindet sich aktuell in der Umsetzungsphase.

| Bereich | Status |
|---|---|
| Projektidee | abgeschlossen |
| Grobplanung | abgeschlossen |
| VLAN- und IP-Konzept | geplant |
| Cisco-Packet-Tracer-Topologie | in Bearbeitung |
| VLAN-Konfiguration | begonnen |
| WLAN-Konfiguration | noch offen |
| VPN-/Standortverbindung | noch offen |
| Tests und Nachweise | noch offen |
| Abschlussreflexion | noch offen |

Diese Dokumentation wird im Verlauf des Projekts weiter ergänzt. Screenshots, Testergebnisse und die endgültige Bewertung der Umsetzung folgen nach Abschluss der technischen Arbeiten.

---

## 3. Ziel des Projekts

Ziel des Projekts ist es, eine strukturierte und sichere Netzwerkinfrastruktur für eine Schule zu planen, in Cisco Packet Tracer umzusetzen und nachvollziehbar zu dokumentieren.

Der Fokus liegt auf folgenden Punkten:

- Erstellung einer vollständigen Netzwerkdokumentation
- Planung eines logischen Netzwerkaufbaus
- Erstellung eines IP-Adress- und VLAN-Konzepts
- Trennung verschiedener Benutzergruppen durch VLANs
- Umsetzung von Inter-VLAN-Routing
- Aufbau eines internen WLANs
- Aufbau eines separaten Gäste-WLANs
- sichere Trennung des Gäste-WLANs von internen Ressourcen
- Planung und Simulation einer Standortverbindung zur Aussenstelle
- fachliche Beschreibung eines VPN-Konzepts
- Durchführung und Dokumentation grundlegender Funktionstests nach Abschluss der Konfiguration

---

## 4. Projektfokus

Dieses Projekt behandelt hauptsächlich vier Themenbereiche aus dem Modul 145.

| Thema | Umsetzung im Projekt |
|---|---|
| Netzwerkdokumentation | Topologie, IP-Plan, VLAN-Tabelle, Portliste und geplante Testnachweise |
| VLAN | Trennung von Administration, Lehrpersonen, Schülerinnen und Schülern, Gästen, Servern und Management |
| WLAN | internes WLAN und separates Gäste-WLAN |
| VPN | simulierte Standortverbindung mit fachlicher VPN-Beschreibung |

Andere Themen wie Monitoring oder Troubleshooting stehen nicht im Zentrum dieses Projekts. Sie können später ergänzend erwähnt werden, falls sie während der Umsetzung relevant werden.

---

## 5. Projektszenario

Eine Schule möchte ihr Netzwerk besser strukturieren. Bisher befinden sich viele Geräte im gleichen Netzwerk. Dadurch ist die Trennung zwischen Administration, Lehrpersonen, Schülerinnen und Schülern sowie Gästen nicht ausreichend sichergestellt.

Neu sollen die verschiedenen Benutzergruppen logisch voneinander getrennt werden. Die Administration benötigt Zugriff auf interne Systeme und Netzwerkgeräte. Lehrpersonen sollen auf schulische Dienste zugreifen können. Schülerinnen und Schüler benötigen Zugriff auf das Schulportal, sollen aber keinen Zugriff auf administrative Systeme erhalten. Gäste sollen nur einen eingeschränkten Netzwerkzugang erhalten und dürfen keine internen Ressourcen erreichen.

Zusätzlich besitzt die Schule eine kleine Aussenstelle. Diese kann zum Beispiel eine Sporthalle oder ein weiteres Schulgebäude sein. Diese Aussenstelle soll mit dem Hauptstandort verbunden werden. In Cisco Packet Tracer wird diese Verbindung technisch als WAN-Verbindung dargestellt. Fachlich wird sie als VPN-Standortverbindung beschrieben.

---

## 6. Projektumfang

### 6.1 Im Projekt enthalten

Folgende Punkte sind für das Projekt vorgesehen:

- Hauptstandort der Schule
- Aussenstelle / Sporthalle / Schulhaus B
- VLAN-Konzept für verschiedene Benutzergruppen
- IP-Adresskonzept
- Switch-Konfiguration mit Access-Ports und Trunk-Ports
- Inter-VLAN-Routing
- internes WLAN
- Gäste-WLAN
- Trennung des Gäste-Netzes von internen Netzen
- Standortverbindung zwischen Hauptstandort und Aussenstelle
- VPN-Konzept als fachliche Beschreibung
- Netzwerkdokumentation mit Tabellen und Nachweisen
- grundlegende Verbindungstests nach Abschluss der Umsetzung

### 6.2 Nicht im Hauptumfang enthalten

Folgende Punkte sind nicht Schwerpunkt dieses Projekts:

- professionelles Monitoring
- ausführliche Troubleshooting-Dokumentation
- produktive Firewall-Konfiguration
- echte Internetanbindung
- echte produktive VPN-Verschlüsselung
- Hochverfügbarkeit
- zentrale Benutzerverwaltung

Diese Punkte können optional erwähnt werden, sind aber nicht Hauptbestandteil dieses Projekts.

---

## 7. Anforderungen

### 7.1 Funktionale Anforderungen

| Nr. | Anforderung | Beschreibung |
|---:|---|---|
| F01 | VLAN-Trennung | Die Benutzergruppen müssen durch VLANs logisch getrennt werden. |
| F02 | Inter-VLAN-Routing | Erlaubte Kommunikation zwischen VLANs muss möglich sein. |
| F03 | Trunk-Verbindungen | VLANs müssen zwischen Switch und Router beziehungsweise zwischen Switches übertragen werden können. |
| F04 | Access-Ports | Endgeräte müssen dem korrekten VLAN zugewiesen werden. |
| F05 | Internes WLAN | Interne Geräte sollen sich mit einem geschützten WLAN verbinden können. |
| F06 | Gäste-WLAN | Gäste sollen ein separates WLAN verwenden. |
| F07 | Gäste-Isolation | Gäste dürfen nicht auf interne Schulressourcen zugreifen. |
| F08 | Standortverbindung | Die Aussenstelle soll mit dem Hauptstandort verbunden werden. |
| F09 | VPN-Konzept | Die Standortverbindung soll fachlich als VPN beschrieben werden. |
| F10 | Dokumentation | Die Netzwerkinfrastruktur muss nachvollziehbar dokumentiert werden. |

---

### 7.2 Nicht-funktionale Anforderungen

| Nr. | Anforderung | Beschreibung |
|---:|---|---|
| N01 | Sicherheit | Interne und externe Benutzergruppen müssen getrennt sein. |
| N02 | Übersichtlichkeit | VLANs, IP-Adressen und Gerätenamen müssen klar strukturiert sein. |
| N03 | Wartbarkeit | Die Netzstruktur soll einfach nachvollziehbar sein. |
| N04 | Erweiterbarkeit | Weitere VLANs oder Standorte sollen später ergänzt werden können. |
| N05 | Nachvollziehbarkeit | Die Konfiguration muss mit Tabellen und Screenshots dokumentiert werden. |
| N06 | Testbarkeit | Die Umsetzung muss mit Verbindungstests überprüfbar sein. |

---

## 8. Geplante Netzwerkarchitektur

Das Netzwerk besteht aus zwei Standorten.

### 8.1 Hauptstandort

Am Hauptstandort befinden sich:

- Administration
- Lehrpersonen
- Schülerinnen und Schüler
- Gäste-WLAN
- internes WLAN
- Servernetz
- Managementnetz
- zentrale Netzwerkgeräte

### 8.2 Aussenstelle

Die Aussenstelle enthält:

- einen Router
- einen Switch
- einzelne Clients
- optional einen Access Point
- ein eigenes Subnetz

Die Aussenstelle wird über eine simulierte Standortverbindung mit dem Hauptstandort verbunden.

---

## 9. Geplante Geräte

| Gerät | Anzahl | Zweck |
|---|---:|---|
| Router Hauptstandort | 1 | Inter-VLAN-Routing und Verbindung zur Aussenstelle |
| Router Aussenstelle | 1 | Verbindung der Aussenstelle mit dem Hauptstandort |
| Core-Switch | 1 | zentrale Verteilung am Hauptstandort |
| Access-Switches | 1–2 | Anschluss von Clients und Access Points |
| Switch Aussenstelle | 1 | Anschluss der Geräte in der Aussenstelle |
| Server | 1 | interner Dienst, zum Beispiel Schulportal |
| Access Points | 2 | internes WLAN und Gäste-WLAN |
| PCs / Laptops | mehrere | Testgeräte für die verschiedenen Netze |

---

## 10. Vorgesehene Gerätenamen

| Gerät | Name |
|---|---|
| Router Hauptstandort | R-HQ-SCHULE |
| Router Aussenstelle | R-BR-SPORT |
| Core-Switch | SW-CORE-01 |
| Access-Switch Administration | SW-ACCESS-ADMIN |
| Access-Switch Klassenzimmer | SW-ACCESS-CLASSROOM |
| Switch Aussenstelle | SW-BR-SPORT |
| Server | SRV-INTRANET |
| Access Point intern | AP-INTERN-01 |
| Access Point Gäste | AP-GUEST-01 |

Die Gerätenamen werden sprechend gewählt, damit die Netzwerkdokumentation verständlich und professionell bleibt.

---

## 11. VLAN-Konzept

Die Netzwerkinfrastruktur wird in verschiedene VLANs aufgeteilt. Jedes VLAN erfüllt einen klaren Zweck.

| VLAN | Name | Subnetz | Gateway | Zweck |
|---:|---|---|---|---|
| 10 | Management | 192.168.10.0/24 | 192.168.10.1 | Verwaltung der Netzwerkgeräte |
| 20 | Administration | 192.168.20.0/24 | 192.168.20.1 | Sekretariat und Schulleitung |
| 30 | Lehrer | 192.168.30.0/24 | 192.168.30.1 | Geräte der Lehrpersonen |
| 40 | Schüler | 192.168.40.0/24 | 192.168.40.1 | Geräte der Schülerinnen und Schüler |
| 50 | Gäste | 192.168.50.0/24 | 192.168.50.1 | Gäste-WLAN und externe Geräte |
| 60 | Server | 192.168.60.0/24 | 192.168.60.1 | interne Serverdienste |
| 70 | WLAN-Intern | 192.168.70.0/24 | 192.168.70.1 | interne WLAN-Geräte |
| 80 | Aussenstelle | 192.168.80.0/24 | 192.168.80.1 | Geräte in der Aussenstelle |
| 99 | Native-Blackhole | kein DHCP | - | Native VLAN und ungenutzte Ports |

---

## 12. Begründung der VLAN-Aufteilung

Die VLAN-Aufteilung dient dazu, das Netzwerk logisch zu strukturieren und die Sicherheit zu erhöhen.

Die Administration wird in einem eigenen VLAN geführt, da dort besonders schützenswerte Systeme genutzt werden. Lehrpersonen und Schülerinnen beziehungsweise Schüler werden getrennt, damit unterschiedliche Berechtigungen umgesetzt werden können. Das Gäste-Netz wird vollständig vom internen Schulnetz getrennt, weil Gäste private und nicht verwaltete Geräte verwenden.

Das Server-VLAN enthält zentrale Dienste wie ein internes Schulportal. Dadurch können Zugriffe auf Server gezielt gesteuert werden. Das Management-VLAN wird für Netzwerkgeräte verwendet und soll nur von berechtigten administrativen Geräten erreichbar sein.

Das VLAN 99 wird als Native- und Blackhole-VLAN verwendet. Ungenutzte Ports können diesem VLAN zugewiesen werden, damit sie nicht versehentlich Zugriff auf produktive Netze ermöglichen.

---

## 13. IP-Adresskonzept

Für das Projekt wird der private IPv4-Adressbereich `192.168.0.0/16` verwendet.

Jedes VLAN erhält ein eigenes `/24`-Subnetz. Dadurch ist die Struktur einfach verständlich und gut dokumentierbar.

| Bereich | Subnetz | Anzahl nutzbare Hosts |
|---|---|---:|
| Management | 192.168.10.0/24 | 254 |
| Administration | 192.168.20.0/24 | 254 |
| Lehrer | 192.168.30.0/24 | 254 |
| Schüler | 192.168.40.0/24 | 254 |
| Gäste | 192.168.50.0/24 | 254 |
| Server | 192.168.60.0/24 | 254 |
| WLAN intern | 192.168.70.0/24 | 254 |
| Aussenstelle | 192.168.80.0/24 | 254 |

Die Gateway-Adresse ist jeweils die erste nutzbare Adresse im Subnetz, zum Beispiel `192.168.20.1`.

---

## 14. Geplante Portstruktur

Die Portstruktur wird während der Umsetzung überprüft und bei Bedarf angepasst. Der aktuelle Plan sieht wie folgt aus:

| Gerät | Port | Verbindung | Modus | VLAN |
|---|---|---|---|---|
| SW-CORE-01 | G0/1 | R-HQ-SCHULE | Trunk | 10,20,30,40,50,60,70,99 |
| SW-CORE-01 | F0/1 | PC-ADMIN | Access | 20 |
| SW-CORE-01 | F0/2 | PC-LEHRER | Access | 30 |
| SW-CORE-01 | F0/3 | PC-SCHUELER | Access | 40 |
| SW-CORE-01 | F0/4 | SRV-INTRANET | Access | 60 |
| SW-CORE-01 | F0/5 | AP-INTERN-01 | Access | 70 |
| SW-CORE-01 | F0/6 | AP-GUEST-01 | Access | 50 |
| SW-BR-SPORT | F0/1 | R-BR-SPORT | Access | 80 |
| SW-BR-SPORT | F0/2 | PC-BR-LEHRER | Access | 80 |
| SW-BR-SPORT | F0/3 | PC-BR-SCHUELER | Access | 80 |

---

## 15. WLAN-Konzept

Im Projekt werden zwei WLANs geplant.

### 15.1 Internes WLAN

| Einstellung | Wert |
|---|---|
| SSID | SCHULE-INTERN |
| VLAN | 70 |
| Subnetz | 192.168.70.0/24 |
| Gateway | 192.168.70.1 |
| Sicherheit | WPA2-PSK |
| Zweck | WLAN für berechtigte interne Geräte |

Das interne WLAN ist für Lehrpersonen und autorisierte schulische Geräte vorgesehen. Es darf auf ausgewählte interne Dienste zugreifen.

### 15.2 Gäste-WLAN

| Einstellung | Wert |
|---|---|
| SSID | SCHULE-GUEST |
| VLAN | 50 |
| Subnetz | 192.168.50.0/24 |
| Gateway | 192.168.50.1 |
| Sicherheit | WPA2-PSK |
| Zweck | Netzwerkzugang für Gäste |

Das Gäste-WLAN wird vom internen Netzwerk getrennt. Gäste dürfen keine Server, Administrationsgeräte oder Management-Systeme erreichen.

---

## 16. Begründung des WLAN-Konzepts

Die Trennung zwischen internem WLAN und Gäste-WLAN ist aus Sicherheitsgründen notwendig.

Interne WLAN-Geräte gehören zur Schule oder zu berechtigten Benutzern. Diese Geräte benötigen Zugriff auf interne Dienste. Gäste verwenden hingegen private Geräte, die nicht durch die Schule verwaltet werden. Deshalb erhalten Gäste nur eingeschränkten Zugriff.

Durch die Zuordnung der WLANs zu unterschiedlichen VLANs kann die Trennung technisch sauber umgesetzt werden. Das Gäste-WLAN wird dem Gäste-VLAN zugewiesen. Das interne WLAN wird einem separaten internen WLAN-VLAN zugewiesen.

---

## 17. Zugriffskonzept

Die Kommunikation zwischen den VLANs wird gezielt eingeschränkt.

| Quelle | Ziel | Zugriff | Begründung |
|---|---|---|---|
| Administration | interne Netze | erlaubt | administrative Aufgaben |
| Lehrer | Servernetz | erlaubt | Zugriff auf interne Dienste |
| Schüler | Servernetz | erlaubt | Zugriff auf Schulportal |
| Schüler | Administration | verboten | Schutz administrativer Daten |
| Gäste | interne Netze | verboten | Schutz der Schulressourcen |
| Gäste | Gateway / Internet | erlaubt | Gastzugang |
| Management | Netzwerkgeräte | erlaubt | Verwaltung der Infrastruktur |

Die technische Umsetzung erfolgt über Routing und Access Control Lists. Besonders wichtig ist die Isolation des Gäste-Netzes.

Die konkrete ACL-Konfiguration wird nach Abschluss der VLAN- und Routing-Konfiguration ergänzt.

---

## 18. VPN- und Standortkonzept

Die Schule besitzt eine kleine Aussenstelle. Diese kann zum Beispiel eine Sporthalle oder ein zweites Schulgebäude sein.

Die Aussenstelle soll mit dem Hauptstandort verbunden werden. In Cisco Packet Tracer wird diese Verbindung als WAN-Verbindung zwischen zwei Routern simuliert. Fachlich entspricht diese Verbindung einer Site-to-Site-VPN-Verbindung.

### 18.1 Geplante Netze

| Verbindung / Bereich | Netz |
|---|---|
| WAN-Verbindung zwischen den Routern | 10.0.0.0/30 |
| Hauptstandort | 192.168.10.0/24 bis 192.168.70.0/24 |
| Aussenstelle | 192.168.80.0/24 |

### 18.2 Geplante Router-Adressen

| Gerät | Interface | IP-Adresse |
|---|---|---|
| R-HQ-SCHULE | WAN-Interface | 10.0.0.1/30 |
| R-BR-SPORT | WAN-Interface | 10.0.0.2/30 |
| R-BR-SPORT | LAN-Interface | 192.168.80.1/24 |

---

## 19. Begründung des VPN-Konzepts

Eine Standortverbindung ermöglicht es, eine entfernte Aussenstelle sicher mit dem Hauptstandort zu verbinden.

In einer realen Umgebung würde diese Verbindung über ein verschlüsseltes VPN aufgebaut werden. Dafür könnte zum Beispiel IPsec verwendet werden. Das Ziel eines VPNs ist es, Daten zwischen zwei Standorten über ein unsicheres Netz geschützt zu übertragen.

In Cisco Packet Tracer wird diese Verbindung vereinfacht als direkte WAN-Verbindung dargestellt. Die fachliche Idee bleibt jedoch gleich: Die Aussenstelle wird logisch mit dem Hauptstandort verbunden und kann definierte Ressourcen erreichen.

---

## 20. Geplante Topologie

Die geplante Topologie besteht aus einem Hauptstandort und einer Aussenstelle.

```text
                          [R-BR-SPORT]
                               |
                         [SW-BR-SPORT]
                         /           \
                  Lehrer-PC       Schüler-PC


                          WAN / VPN
                     10.0.0.0/30


                         [R-HQ-SCHULE]
                               |
                         Trunk-Verbindung
                               |
                         [SW-CORE-01]
                         /     |      \
              Admin-PC   Lehrer-PC   Schüler-PC
                  |          |           |
             SRV-INTRANET  AP-INTERN   AP-GUEST