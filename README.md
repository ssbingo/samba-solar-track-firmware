# Samba Solar Track – Firmware

**© Silvio Sternitzke, 10/2026** · Samba Solar Track · Lizenz CC BY-NC-SA 4.0 (keine kommerzielle Verwendung,
Nachbau für private Zwecke erlaubt), siehe [LICENSE](LICENSE)

Hier liegen nur die fertig kompilierten Dateien der Firmware von Samba Solar Track, kein Quelltext. Das Repository ist
die Release-Quelle unter <https://firmware.samba-solar.de/>: Die 10-Zoll-Version (Waveshare ESP32-P4-WIFI6-Touch-LCD-10.1
mit der Platine RearCircuitBoard_10) sieht hier einmal am Tag nach neuer Firmware und installiert sie nur nach
Bestätigung. Unterlagen für den Nachbau (Platinen, Gehäuse, Handbuch): <https://github.com/ssbingo/samba-solar-track>.

**Aktuell: Firmware 0.7.4 (11.11.2026)**, Werksabbild 0.7.4

| Datei | Wofür |
|---|---|
| `v1/waveshare_10/manifest.txt` | signierte Beschreibung der aktuellen Firmware (Version, Größe, SHA-512, Signatur Ed25519); liest das Gerät |
| `v1/waveshare_10/samba-solar-track-0.7.4-waveshare_10.bin` | Abbild für das Update über das Internet oder das Netz; behält die Einstellungen |
| `erstinstallation/samba-solar-track-10zoll-0.7.4-factory.bin` | Werksabbild für das erste Aufspielen über USB an Adresse 0x0, zum Beispiel mit <https://web.esphome.io/>; **löscht alle Einstellungen** |
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
einem Neustart); mit 0.5.7 springt die Anzeige nach der Bestätigung des Resets direkt zum
Startbildschirm; mit 0.5.8 heißt die Bewegung der Elevation am Display und in der Weboberfläche
STEILER / FLACHER statt RAUF / RUNTER; 0.5.9 zeigt diese Tasten auf Französisch, Spanisch und
Portugiesisch zweizeilig, damit nichts abgeschnitten wird; 0.6.0 beschriftet die Prozentzahl am Sonnensensor als
„Abweichung der Sonne“ (Rand des Kreises = 30 %) und zeigt die Neigung der Paneele als Skizze mit Winkel in Grad;
0.7.0 berechnet Sonnenstand, Sonnenauf- und -untergang aus Standort und Uhrzeit, fährt nach Sonnenuntergang in die
Nachtstellung (bei zwei Achsen auf Wunsch nach Osten), bringt eine eingebaute Standortkarte und ein geführtes
Setup-Programm, das alle Funktionen und Fahrwege am Rack einmal prüft; 0.7.1 teilt den Speicher des Boards neu auf
(beide Plätze für die Firmware unter 16 MB); 0.7.2 bildet im Setup-Programm in der Simulation die Handgriffe am Rack
nach; 0.7.3 zeigt nach dem bestandenen Schritt Windmesser die Taste WEITER (fehlte seit 0.7.0); 0.7.4 zeigt im
Setup-Programm die Wartezeit, wenn die Antriebe eine Pause brauchen (Einschaltdauer), und den Ablauf des Resets. Alle sind nur auf dem PC getestet.

**Wichtig – einmal per USB:** Bis Firmware 0.7.0 war der Speicher so aufgeteilt, dass eine Firmware über etwa 3,4 MB
nur in einen der beiden Plätze passte; das Update auf 0.7.0 scheiterte deshalb meist mit
`ESP_ERR_OTA_VALIDATE_FAILED` (die bisherige Firmware lief weiter). Die neue Aufteilung kommt nur über das USB-Kabel aufs
Board: einmal das Werksabbild `erstinstallation/samba-solar-track-10zoll-0.7.4-factory.bin` an Adresse 0x0 aufspielen
(löscht die Einstellungen). Danach kommen alle Versionen wieder über das Internet. Ältere Firmware (bis 0.4.6) kennt
den heutigen Schlüssel ohnehin nicht; auch dort hilft das Werksabbild.

---

© Silvio Sternitzke, 10/2026 · Samba Solar Track · Lizenz CC BY-NC-SA 4.0 (keine kommerzielle Verwendung,
Nachbau für private Zwecke erlaubt); für die Bibliotheken anderer Hersteller gelten ihre eigenen Lizenzen, siehe
[DRITTANBIETER.md](DRITTANBIETER.md)
