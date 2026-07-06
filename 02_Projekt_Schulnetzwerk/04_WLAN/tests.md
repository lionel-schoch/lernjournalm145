# Tests

## Ziel

Die WLAN-Tests prüfen, ob der Access Point vorhanden ist, ob die WLAN-Sicherheit korrekt gesetzt wurde und ob der WLAN-/Gastbereich nachvollziehbar dokumentiert ist.

## Testübersicht

| Nr. | Test | Erwartetes Ergebnis | Nachweis |
| --- | --- | --- | --- |
| W-01 | WLAN-Topologie prüfen | Access Point und WLAN-Clients sind im Projekt sichtbar. | [wlan_topologie_ap_clients.png](../assets/screenshots/wlan/wlan_topologie_ap_clients.png) |
| W-02 | SSID prüfen | Auf `AP-GUEST-02` ist die SSID `30` gesetzt. | [ap_guest_02_wpa2_config.png](../assets/screenshots/wlan/ap_guest_02_wpa2_config.png) |
| W-03 | Sicherheit prüfen | WPA2-PSK ist aktiv und AES wird verwendet. | [ap_guest_02_wpa2_config.png](../assets/screenshots/wlan/ap_guest_02_wpa2_config.png) |
| W-04 | Kanal prüfen | Der AP verwendet den 2.4-GHz-Kanal 6. | [ap_guest_02_wpa2_config.png](../assets/screenshots/wlan/ap_guest_02_wpa2_config.png) |
| W-05 | VLAN-Zuordnung prüfen | WLAN/Gast ist dem VLAN 30 zugeordnet. | VLAN- und WLAN-Dokumentation |

## Durchgeführte Tests

### W-01: WLAN-Topologie

Der Screenshot zeigt den Access Point `AP-GUEST-02` sowie drahtlose Clients im Packet-Tracer-Projekt. Damit ist sichtbar, dass der WLAN-Bereich im Netzwerkmodell vorhanden ist.

Bewertung: Bestanden.

### W-02: SSID

In der AP-Konfiguration ist als SSID `30` eingetragen. Diese SSID verwende ich als Zuordnung zum VLAN 30 `WLAN/Gast`.

Bewertung: Bestanden.

### W-03: WLAN-Sicherheit

Der Access Point ist mit WPA2-PSK konfiguriert. Als Verschlüsselung wird AES verwendet. WEP ist nicht aktiviert.

Bewertung: Bestanden.

### W-04: Funkkanal und Reichweite

Der Access Point nutzt den 2.4-GHz-Kanal 6 und eine Reichweite von 140 Metern. Für Packet Tracer ist dies ausreichend, damit die Clients im Modell mit dem Access Point verbunden werden können.

Bewertung: Bestanden.

## Noch sinnvoller Zusatztest

Für eine noch vollständigere WLAN-Abgabe wäre ein zusätzlicher Screenshot eines verbundenen WLAN-Clients sinnvoll. Idealerweise sollte der Client eine IP-Adresse aus dem WLAN-/Gastnetz erhalten und einen Ping-Test zum Gateway ausführen.

## Fazit

Die vorhandenen Screenshots belegen, dass der WLAN-Bereich im Projekt vorhanden ist und der Access Point mit WPA2-PSK/AES abgesichert wurde. Die Zuordnung zum VLAN 30 ist in der WLAN- und VLAN-Dokumentation beschrieben.
