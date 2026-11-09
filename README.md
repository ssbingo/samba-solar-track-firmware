# Samba Solar Track – Firmware

**© Silvio Sternitzke, 10/2026** · Samba Solar Track · Lizenz CC BY-NC-SA 4.0 (keine kommerzielle Verwendung,
Nachbau für private Zwecke erlaubt), siehe [LICENSE](LICENSE)

Hier liegen nur die fertig kompilierten Dateien der Firmware von Samba Solar Track, kein Quelltext. Das Repository ist
die Release-Quelle unter <https://firmware.samba-solar.de/>: Die 10-Zoll-Version (Waveshare ESP32-P4-WIFI6-Touch-LCD-10.1
mit der Platine RearCircuitBoard_10) sieht hier einmal am Tag nach neuer Firmware und installiert sie nur nach
Bestätigung. Unterlagen für den Nachbau (Platinen, Gehäuse, Handbuch): <https://github.com/ssbingo/samba-solar-track>.

**Aktuell: Firmware 0.5.6 (09.11.2026)**, Werksabbild 0.4.7

| Datei | Wofür |
|---|---|
| `v1/waveshare_10/manifest.txt` | signierte Beschreibung der aktuellen Firmware (Version, Größe, SHA-512, Signatur Ed25519); liest das Gerät |
| `v1/waveshare_10/samba-solar-track-0.5.6-waveshare_10.bin` | Abbild für das Update über das Internet oder das Netz; behält die Einstellungen |
| `erstinstallation/samba-solar-track-10zoll-0.4.7-factory.bin` | Werksabbild für das erste Aufspielen über USB an Adresse 0x0, zum Beispiel mit <https://web.esphome.io/>; **löscht alle Einstellungen** |
| `DRITTANBIETER.md` | Bibliotheken anderer Hersteller in der Firmware, mit Fassung, Lizenz, Quelle und vollständigen Lizenztexten |

Wie die Firmware zum ersten Mal aufgespielt wird, steht im Handbuch der 10-Zoll-Version (Kapitel „Die Firmware zum
ersten Mal aufspielen“).

Die Firmware 0.5.0 brachte die Anzeige in sieben Sprachen (Englisch, Deutsch, Französisch, Spanisch, Niederländisch,
Portugiesisch, Polnisch; ein schon eingerichtetes Gerät bleibt deutsch), die Ladeanzeige des Akkus und die Anzeige der
pausierten Automatik am Schalter. Die Firmware 0.5.1 bringt dasselbe in die Weboberfläche: Wahl der Sprache unter
EINRICHTUNG, Akku mit Ladeanzeige in der Kopfzeile und die Pause am Schalter AUTOMATIK. Die Firmware 0.5.2 fährt
vor dem Schreiben eines Updates die Elevation in die Flachstellung (Sturmstellung) und danach, wenn der Selbsttest
bestanden ist oder das Gerät zur bisherigen Firmware zurückgekehrt ist, wieder in die Stellung von vorher; kommt sie
nicht in die Flachstellung, wird das Update abgebrochen. Das gilt ab dem nächsten Update nach 0.5.2. Die Firmware
0.5.3 bringt Warnungen in der Kopfzeile, wenn die 24 V oder die 5 V fehlen, und eine Plausibilitätsprüfung der
Ladesperre des Akkus. Beides braucht die Platine RearCircuitBoard_10 ab Entwurf 0.11; mit einer älteren Platine meldet
das Display „LADESPERRE UNGEPRÜFT“. Die Warnungen sind nur Anzeige und wirken nicht auf die Steuerung. Die Firmware
0.5.3 ist nur auf dem PC getestet und noch nicht am Gerät erprobt. Die Firmware 0.5.4 bringt die Funktion
„Synchronsteuerung zurücksetzen“ (Reset-Kontakt RST für Synchronsteuerungen der Antriebe, Einstellung unter WERTE →
INBETRIEBNAHME, ab Werk aus). Die Firmware 0.5.5 zeigt den Ablauf dieses Resets am Display und in der
Weboberfläche (Phase, Restzeit, Ergebnis); 0.5.6 macht die Reset-Kontakte robuster (sicher offen nach
einem Neustart). Alle drei sind nur auf dem PC getestet. Sie lässt sich ab Firmware 0.4.7 über das
Internet installieren. Ältere Firmware (bis 0.4.6) kennt den
heutigen Schlüssel nicht: Dort zuerst 0.4.7 über die Weboberfläche (EINRICHTUNG) oder per USB aufspielen.

---

© Silvio Sternitzke, 10/2026 · Samba Solar Track · Lizenz CC BY-NC-SA 4.0 (keine kommerzielle Verwendung,
Nachbau für private Zwecke erlaubt); für die Bibliotheken anderer Hersteller gelten ihre eigenen Lizenzen, siehe
[DRITTANBIETER.md](DRITTANBIETER.md)
