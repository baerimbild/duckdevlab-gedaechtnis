# Wandering Shell · Weltmodul (Konzept, Stand 21.11.2026)

`key: wandering_shell_weltmodul` · aktualisiert 2026-11-21 09:56 · id `3r675csjp1bb66b`

## Kurzstand

21.11.2026: Konzept aus Max' Vorgaben (20./21.11.) festgehalten, Datenmodell als Vorschlag von Claude, noch nicht gebaut. Repo baerimbild/wandering-shell, Klon /opt/ops/src/wandering-shell (= Live-Deploy, Container seit 06.11. up).

## Regeln

PRÄMISSE (Max, 21.11.2026): Wandering Shell ist für schnelle One-Shots: Leute, die noch nie Pen-and-Paper gespielt haben, starten ohne lange Vorbereitung, auch die Spielleitung. Das Szenario entsteht in Minuten aus den drei Statuen (Tafelsätze → Saat). Aus den Notizen eines Abends bildet sich langsam eine Spielwelt heraus: die Gruppe baut ihre Welt dynamisch, sie wächst mit. Weltmodule sind fertige Spielwelten mit derselben Struktur; auch die Entwicklung der Szenarien folgt dieser Struktur. Ein Modul ist ein Inhaltspaket, das die Regeln nutzt und eventuell anpasst bzw. umfangreicheren Hintergrund liefert. Spieler wissen nur, was ihre Figuren wissen oder was jeder Bürger weiß (Beispiel Max: dass die Erde ein Planet ist, dass es Länder und Kontinente gibt, dass wir Sauerstoff atmen).

ABLEITUNGEN (Claude, Vorschlag):
1. Welt = eigene Entität, nicht Teil des Abends. Eine Runde zeigt auf eine Welt; mehrere Runden können dieselbe Welt bespielen. Was eine Gruppe spielt, IST ein Modul im Werden: Export einer Welt ergibt ein Modul, Import eines Moduls ergibt eine Welt. Gleiche Struktur in beide Richtungen.
2. Drei Wissensstufen je Eintrag: geheim (nur SL), buerger (jeder in der Welt, „Allgemeinwissen“), figur (nur Figuren, die es erfahren haben). Serverseitig durchgesetzt (PocketBase-Regeln mit Rückrelation), nicht nur in der Oberfläche – wie REGELN 10.
3. Je Abend bleibt nur, was wirklich zum Abend gehört: Statuen-Sätze, Saat, Bogen, Auslage. Gegend, Klammer-Hintergrund, Weltblatt, Orte, Figuren, Ereignisse gehören zur Welt.
4. Module passen Daten an, nicht Mechanik (v1): eigene Tafeln (A/B/C-Sätze), Sets/Bilder, Wellen-Namen und Deutungen, Saat-Vorlagen, Weltblatt-Lücken, Wortbank für Startwörter, Allgemeinwissen. Würfel, Pool, Marken, Bogen-Schwellen bleiben Regelwerk. Mechanik-Anpassung erst, wenn ein Modul sie wirklich braucht.
5. Auslage und Welt bleiben getrennt (Felder sind abstrakt und je Abend neu). Ein Eintrag KANN optional an ein Feld des Abends gehängt werden (Statue → Figur/Ort), muss aber nicht.

DATENMODELL (Vorschlag):
- ws_welten: name, sl (Besitzer), beschreibung, modul (Slug der Herkunft oder leer), daten (json: Tafel-/Set-/Wellen-/Saat-/Weltblatt-Overrides, leer = Standard), allgemeinwissen (text), erstellt_aus (runde, optional).
- ws_eintraege: welt, typ (gegend|ort|figur|ding|ereignis|begriff), name, kurz (eine Zeile), text_sl (geheim), text_buerger (Allgemeinwissen), stufe (geheim|buerger|figur), eig (json: Gegensatzpaare, „will“), verbindungen (json: [{zu, verb}]), quelle (saat|sl|spiel|modul), runde/abend der Entstehung.
- ws_wissen: eintrag, figur, abend, wie (frei/Protokoll-Verweis). Leseregel für Spieler: stufe = buerger ODER eigene Figur in ws_wissen. SL sieht alles.
- ws_runden: + welt (rel). ws_welt_sl behält statuen, saat, bogen, notizen; ws_welt (Weltblatt, Klammer-Text, Gegend-Text) wandert in die Welt (Weltblatt = Einträge vom Typ begriff mit stufe buerger, oder weiter als json an ws_welten; Entscheidung beim Bau).
- Saat schreibt Orte und Figuren als echte Einträge (stufe geheim), SL gibt frei (→ buerger) oder lässt Figuren es erfahren (→ ws_wissen).
- Modul-Format: module/<slug>/modul.json (Name, Beschreibung, Regel-Daten-Overrides) + eintraege.json (+ optional img/). Import/Export über Hook-Aktionen; Export einer gewachsenen Welt ist dasselbe Format.
- Migration: je bestehender Runde eine Welt aus ws_welt/ws_welt_sl erzeugen (Gegend, Klammer, Weltblatt, Figurennetz → Einträge). Jessis Runde läuft so ohne Bruch weiter.

OBERFLÄCHE: SL-Reiter Welt wird in Teile zerlegt (Statuen+Saat je Abend / Welt-Einträge mit Freigabe / Weltblatt / Bogen). Spieler bekommen eine Weltseite: Allgemeinwissen, Weltblatt, Orte und Figuren, die sie kennen; neu Erfahrenes markiert. Ziel: etwas, das in Testrunden funktioniert, nicht Feature-Vollständigkeit.

OFFEN: Wie ein Spieler Wissen erhält (SL tippt „weiß jetzt“ je Figur; automatisch bei Chronik-Erwähnung?). Ob das Weltblatt als Einträge oder als json weiterlebt. Ob eine Welt mehreren SLs gehören kann (Julia und Max).

## Ablage

Repo baerimbild/wandering-shell (REGELN.md, ARCHITEKTUR.md, ENTSCHEIDUNGEN.md); Klon /opt/ops/src/wandering-shell. Konzept soll als WELTMODUL.md ins Repo (Branch weltmodul), sobald Max das Modell bestätigt. Faden: hgxabvmilxg4xt7.

## Links

https://github.com/baerimbild/wandering-shell
