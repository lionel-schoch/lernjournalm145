# Konzept

## Ziel

Für das Schulnetzwerk habe ich einen WLAN-/Gastbereich vorgesehen. Dieser Bereich soll drahtlosen Geräten den Zugriff auf das Netzwerk ermöglichen, ohne dass sie direkt im gleichen Bereich wie Lehrer-, Schüler-, Admin- oder Servergeräte arbeiten.

Der WLAN-Bereich ist deshalb als eigener Bereich geplant und wird dem VLAN 30 `WLAN/Gast` zugeordnet.

## Ausgangslage

Im Hauptstandort ist ein Access Point eingezeichnet. In den Screenshots ist zusätzlich der Access Point `AP-GUEST-02` ersichtlich. Dieser Access Point stellt das WLAN bereit und ist mit der Switch-Infrastruktur verbunden.

Der WLAN-Bereich ergänzt die bestehende VLAN-Struktur:

| Bereich | VLAN | Zweck |
| --- | --- | --- |
| Lehrer | VLAN 10 | Geräte der Lehrpersonen |
| Schüler | VLAN 20 | Geräte der Schüler |
| WLAN/Gast | VLAN 30 | drahtlose Gast- oder BYOD-Geräte |
| Administration | VLAN 40 | administrative Geräte |

## Begründung

Ein eigener WLAN-/Gastbereich ist sinnvoll, weil drahtlose Geräte oft nicht gleich stark kontrolliert werden können wie feste Schulgeräte. Gäste oder private Geräte sollen nur die Dienste erreichen, die wirklich benötigt werden.

Die Trennung über VLAN 30 bringt drei Vorteile:

- Gastgeräte sind vom internen Schulnetz getrennt.
- Fehler oder Broadcasts im WLAN betreffen nicht direkt die anderen VLANs.
- Zugriffe können später gezielt über ACLs oder Routing-Regeln eingeschränkt werden.

## Eingesetzte WLAN-Einstellungen

Aus dem Screenshot der AP-Konfiguration ergeben sich folgende Einstellungen:

| Einstellung | Wert |
| --- | --- |
| Access Point | `AP-GUEST-02` |
| SSID | `30` |
| 2.4-GHz-Kanal | 6 |
| Reichweite | 140 Meter |
| Authentifizierung | WPA2-PSK |
| Verschlüsselung | AES |
| PSK Passphrase | `TBZ12345` |

Nachweis: [ap_guest_02_wpa2_config.png](../assets/screenshots/wlan/ap_guest_02_wpa2_config.png)

## Fazit

Mit dem WLAN-Konzept wird der Gast-/WLAN-Zugang bewusst von den übrigen Bereichen getrennt. Für eine Schulumgebung ist diese Trennung wichtig, weil dadurch interne Ressourcen besser geschützt und drahtlose Geräte kontrollierter eingebunden werden.
