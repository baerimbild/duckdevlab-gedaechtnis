# Magic-Sammlung (MTG) · Self-hosted App: Erfassung, Wert, 1v1-Commander-Matching

`key: magic` · aktualisiert 2026-11-25 12:05 · id `vpbuoeqtppedpyp`

## Kurzstand

25.11.2026: Stufe 1 LIVE unter https://magic.duckdevlab.com (Haushaltspasswort = das der Vorrat-App). Container `magic` (python:3.12-alpine, Stdlib) auf dem vServer, Quelle /opt/ops/src/magic (lokales Git), Betrieb /opt/magic, Doku dienste/magic.md (docs PR #7 gemerged). 16 Commander-Precons importiert (Teysa als Kommandant von Call the Spirits, Jarad von Plunder the Graves gesetzt), Behälter Rares-Ordner + Common-Kiste angelegt, aber noch leer. MCP-Endpunkt /mcp/<MAGIC_MCP_TOKEN> läuft, als claude.ai-Connector noch nicht eingetragen. Offen: Jumpstart-Halbdecks (J22, je 16 en/20 de; Variante 1–4 pro Thema unbekannt), Rares erfassen, Connector.

## Regeln

AUSGANGSLAGE (Max, 25.11.2026): Max und Julia spielen casual Commander, oft zu zweit; ca. 11+ Precons der letzten Jahre, die als Decks intakt bleiben sollen. Wollen spontan, ohne Metagaming, faire 1v1-Partien. Sammlung soll Datenbasis sein, aus der Claude Decks baut und matcht. Keine fremde Datenbank/kein Account. Wert grob wissen.

VORSCHLAG (Claude, 25.11.2026, unbestätigt):
- Hosting wie Vorrat: ein Container (Python Stdlib) + SQLite auf dem vServer, z. B. magic.duckdevlab.com, Haushaltspasswort.
- Kartendaten: Scryfall-Bulk (default_cards) nächtlich ziehen, schlanke Tabelle druck (scryfall_id, oracle_id, name, set, nr, sprache, typ, cmc, farbidentität, oracle_text, commander-legal, eur/eur_foil = Cardmarket-Trend, bild-URL). Regenerierbar, gehört nicht zum Besitz.
- Precons: Listen aus MTGJSON (Deck-Dateien) per Auswahl importieren, danach Abweichungen markieren.
- Lose Karten: Schnelleingabe „Setcode Nummer“ (z. B. „MKM 123“, mit Autocomplete) + Namenssuche; CSV-Import aus alten Apps (Manabox/Moxfield/Delver). Stufe 2: Foto -> Vision liest Setcode/Nummer.
- Datenmodell: exemplar (druck, anzahl, foil, sprache, zustand, heimat=behaelter) | behaelter (art: precon/kiste/binder; geschuetzt) | deck (Entwurf/aktiv, Kommandant) + deckkarte (Bedarf) | leihe (exemplar aus behaelter -> deck, offen/zurück) | partie (deck A, deck B, Sieger, Datum, Notiz).
- Precon-Schutz: Exemplare haben eine Heimat; Decks reservieren nur. Standard: neue Decks nur aus losem Bestand, Precons nur als Ganzes oder per Leihschein mit Rückgabeliste.
- Fairness: Kennzahlen je Deck (Ramp, Draw, Removal, Tutoren, Kurve, bekannte Combos via Commander-Spellbook-Daten, Preis als schwaches Signal) + Elo aus geloggten Partien; Claude bewertet per MCP mit. 1v1-Anpassung: Tausch weniger Multiplayer-Karten aus dem losen Bestand.
- Claude-Zugang: MCP-Endpunkt im selben Container (Token), Tools z. B. bestand_suchen, deck_lesen, deck_entwurf_speichern, partie_loggen.
- Datenbesitz: SQLite + nächtlicher CSV-Export im Moxfield/Manabox-kompatiblen Format (Count, Name, Edition, Collector Number, Foil, Condition, Language) in die Sicherung.

## Ablage

Quelle /opt/ops/src/magic (api/app.py, api/karten_laden.py, web/, README.md, deploy.sh, nacht.sh). Betrieb /opt/magic (docker-compose.yml, magic.env 600 mit MAGIC_PASSWORT/SECRET/MCP_TOKEN, data/magic.db = Besitz, data/karten.db = Cache, data/export/sammlung.csv + decks.json, sicherung/). Cron /etc/cron.d/magic 03:40 -> nacht.sh. Caddy @magic in /opt/sites/Caddyfile. Doku https://docs.duckdevlab.com dienste/magic.md. MCP-URL: grep MAGIC_MCP_TOKEN /opt/magic/magic.env.
