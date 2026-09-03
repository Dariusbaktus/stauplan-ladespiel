# Stauplan — das Ladespiel

Ein Browserspiel für Global Shipping & Logistics GmbH, Bremen.
Ladung in einen Bulk Carrier stauen, ohne dass er Schlagseite bekommt.

Ein Kran lädt Break Bulk, Schwergut und Schüttgut in den Laderaum. Wer die
schweren Kolli nach oben oder einseitig legt, bekommt Krängung — und ab fünf
Grad rutscht loses Gut nach Lee, was die Krängung weiter verschlimmert. Ist der
Raum voll, entscheidet eine Seereise mit zufälligem Wetter, ob die Stauung hält.

## Ausprobieren

`index.html` im Browser öffnen. Mehr ist nicht nötig — keine Installation,
kein Server, keine Fremdbibliothek, keine Cookies.

Steuerung: ◀ ▶ bewegen · ▲ drehen · ▼ senken · Leertaste fallen lassen.
Am Handy wahlweise über Gesten direkt auf dem Spielfeld (Wischen nach links/rechts/unten, Tippen zum Drehen) oder über die Daumen-Steuerung unter der Anzeige (inkl. Dauerbewegung bei Gedrückthalten).

## Dateien

| Datei | Zweck |
|---|---|
| `index.html` | das Spiel, eigenständige Seite (automatisch responsiv auf Mobilgeräten) |
| `mobile.html` | dedizierte Handy-Fassung als Web-App (Zero-Scroll-Layout, Daumenleiste, Vollbild-optimiert) |
| `wordpress-block.html` | dasselbe Spiel als `<div>` für den WordPress-Block „Individuelles HTML" |
| `archiv/stauplan_v1.html`, `_v2.html` | frühere Stände; v2 war zu leicht, praktisch jeder Lauf ging gut aus |

## Was daran echt ist

Die Stabilitätsrechnung benutzt die richtigen Formeln, nur mit entschärften Grenzwerten:

- Krängung aus `atan(Quermoment / (Verdrängung × GM))`, mit `GM = KM − KG`
- Schiffsdaten eines Handysize-Bulkers: Leergewicht 9.000 t, Tragfähigkeit 26.000 t, KM 8,8 m
- Rollamplitude aus GM und Wetterfaktor — ein zu großes GM macht das Schiff steif und lässt es hart rollen, ein zu kleines macht es rangig
- Broken Stowage als tatsächlich ungenutzter Raum unter der obersten belegten Lage
- Laderaum im Querschnitt eines Bulk Carriers, mit Topside- und Hopper-Tanks

Vereinfachte Darstellung zu Anschauungszwecken. Ersetzt keine Stabilitätsberechnung.

## Wo geschraubt wird

Alles steckt in `index.html`:

| Was | Wo |
|---|---|
| Schwierigkeit | `SHIFT_START` (5°, ab hier rutscht loses Gut), `HEEL_FAIL` (13°, Bruch) |
| Schiffsdaten | `KM`, `LIGHTSHIP`, `KG_LIGHT`, `DWT_MAX`, `HOLD_DEPTH` |
| Wetter | `WEATHER` — drei Stufen mit Faktor |
| Ladungsarten | `PIECES` — Form, Gewicht, Farbe, Beschreibung |
| Laderaumform | `isStruct()` |
| Ladungsverschiebung | `shiftOnce()`, `cargoShift()`, `bulkFall()`, `seaTick()` |

Wer die Schwierigkeit ändert, sollte beide Spielweisen durchtesten — sorgfältig
und sorglos. Sonst verschiebt man nur die Streuung, nicht die Schwierigkeit.

## Technik

Ein einzelnes HTML mit Canvas 2D, rund 74 KB. Kein Framework, kein Build.
Einziger externer Bezug sind zwei Schriften von Google Fonts (Inter, DM Sans);
ohne Netz greifen die Ersatzschriften. Das Logo steckt als base64-PNG in der Datei.
Die Bestenliste gilt nur für die laufende Sitzung und wird bewusst nirgends gespeichert.

## Rechte

Logo, Firmenname und Adresse gehören der Global Shipping & Logistics GmbH.
Der Code steht bislang unter keiner Lizenz — alle Rechte vorbehalten, bis
etwas anderes vereinbart ist. Vor einer öffentlichen Veröffentlichung ist das zu klären.
