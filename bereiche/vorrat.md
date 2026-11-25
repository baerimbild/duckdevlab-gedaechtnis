# Vorrats- & Einkaufs-App (Max & Julia)

`key: vorrat` · aktualisiert 2026-11-24 13:09 · id `nlxqdmidurcd8gp`

## Kurzstand

24.11.2026: Stufe 1 live unter https://vorrat.duckdevlab.com. Eigener Container `vorrat` (python:3.12-alpine, Stdlib) mit SQLite /opt/vorrat/data/vorrat.db, Quelle /opt/ops/src/vorrat (lokales Git), Doku dienste/vorrat.md. Kein PocketBase, kein Grocy (Max' Entscheidung). Alle Geräte Android. Offen: Passwort/Sicherung durch Max, Artikelliste.

## Regeln

Ziel: Lebensmittel + Verbrauchskram von Max & Julia erfassen. Oberfläche maximal simpel. Fester Artikelstamm (kaum Variation). Julia kauft eher zu viel, Max vergisst eher.

Architektur (umgesetzt 24.11.2026):
- Ein Container `vorrat` liefert PWA (web/) und API (/api/*), SSE-Sync (/api/events), Login per Haushaltspasswort + Cookie 400 Tage, „Wer bin ich“ (Max/Julia) im Browser.
- SQLite-Tabellen: artikel (name, kategorie, einheit, mindest, soll, bestand≈) | barcode (code→artikel, produkt, marke, inhalt, packung, bild) | ereignis (kauf/verbrauch/leer/korrektur/bedarf/bedarf_weg, menge, bestand danach, wer, zeit) | liste (artikel_id oder freitext, menge, von Max/Julia/auto, erledigt) | produkt_cache.
- Kernidee: Bestand ist nur Näherung; Hauptsignale „brauchen wir“ (1 Tap auf Kachel) und Käufe (Abhaken/Scan). Bestand < Mindest -> automatisch auf Liste (gegen Vergessen). Liste zeigt „noch X da · Soll Y“ bzw. „Genug da“ (gegen Zuvielkauf). Abhaken = Kauf, Vorschlag Soll−Bestand.
- Barcode: BarcodeDetector (Android Chrome), unbekannter Code -> Open Food/Beauty/Products Facts -> einem Stammartikel zuordnen oder neu anlegen, Packungsgröße pro Scan. Bekannter Code -> „+n gekauft“ (hakt Listeneintrag ab) / aufgebraucht / leer.
- Import-Format: `# Kategorie` dann `Name; Einheit; Mindest; Soll`.
- Nächste Stufen: 2 Kassenzettel-Foto -> Vision-Modell -> Zeilen auf Artikel (lernende Bon-Zuordnung); 3 Verbrauchsraten + Einkaufsrhythmus aus ereignis.

## Ablage

Quelle /opt/ops/src/vorrat (Git main, README.md), Betrieb /opt/vorrat (docker-compose.yml, vorrat.env 600, data/, sicherung/, passwort-setzen.sh, sicherung.sh, sicherung-einrichten.sh). Lokale Kopie in der Claude-Sitzung ist flüchtig. Doku https://docs.duckdevlab.com dienste/vorrat.md. Live https://vorrat.duckdevlab.com.
