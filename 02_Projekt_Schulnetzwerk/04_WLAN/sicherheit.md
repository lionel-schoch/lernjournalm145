# Sicherheit

## Ziel

Der WLAN-Zugang soll so eingerichtet sein, dass drahtlose Geräte nicht ungeschützt auf das Netzwerk zugreifen können. Gleichzeitig soll der WLAN-/Gastbereich vom internen Schulnetz getrennt bleiben.

## Eingesetzter Sicherheitsstandard

Im Screenshot ist ersichtlich, dass `AP-GUEST-02` mit WPA2-PSK und AES konfiguriert ist.

| Einstellung | Wert | Bewertung |
| --- | --- | --- |
| Authentifizierung | WPA2-PSK | für Packet Tracer und ein einfaches Schulprojekt geeignet |
| Verschlüsselung | AES | sicherer als veraltete Verfahren wie WEP |
| PSK Passphrase | `TBZ12345` | im Projekt als Testpasswort verwendet |
| WEP | deaktiviert | sinnvoll, da WEP veraltet und unsicher ist |

Nachweis: [ap_guest_02_wpa2_config.png](../assets/screenshots/wlan/ap_guest_02_wpa2_config.png)

## Begründung

WPA2-PSK mit AES ist für diese Packet-Tracer-Umsetzung eine sinnvolle Wahl, weil es im Vergleich zu offenen WLANs oder WEP deutlich sicherer ist. Für eine produktive Schulumgebung wäre ein stärkeres Passwort oder eine zentrale Authentifizierung mit 802.1X/RADIUS besser.

## Trennung vom internen Netz

Der WLAN-/Gastbereich ist VLAN 30 zugeordnet. Dadurch kann ich den WLAN-Verkehr getrennt von anderen Bereichen behandeln.

| Bereich | Schutzidee |
| --- | --- |
| Lehrer-VLAN | kein direkter Zugriff für Gastgeräte |
| Schüler-VLAN | getrennt vom Gastzugang |
| Admin-VLAN | besonders schützenswert, Zugriff nur administrativ |
| Servernetz | nur benötigte Dienste freigeben |
| WLAN/Gast | Zugriff begrenzen und getrennt führen |

## Risiken und Massnahmen

| Risiko | Massnahme |
| --- | --- |
| Schwaches WLAN-Passwort | in einer echten Umgebung stärkeres Passwort verwenden |
| Gäste erreichen interne Ressourcen | Zugriff über ACLs oder Firewall-Regeln einschränken |
| AP-Port im falschen VLAN | Switchport-Konfiguration kontrollieren |
| Veraltete Verschlüsselung | WEP vermeiden, WPA2/WPA3 verwenden |

## Fazit

Das WLAN ist im Projekt mit WPA2-PSK und AES abgesichert. Zusätzlich sorgt die Zuordnung zum VLAN 30 dafür, dass der WLAN-/Gastbereich logisch vom internen Schulnetz getrennt werden kann.
