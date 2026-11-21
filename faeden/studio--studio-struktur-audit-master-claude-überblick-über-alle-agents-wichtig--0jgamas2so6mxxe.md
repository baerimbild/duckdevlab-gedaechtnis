# Studio · Struktur-Audit + Master-Claude (Überblick über alle Agents) – WICHTIG

Projekt `studio` · id `0jgamas2so6mxxe` · aktualisiert 2026-11-20 09:04 · fällig 2026-11-30

## Stand

20.11.2026 (Max, Briefing-Rückmeldung): Dringend nötig, weil Claude nicht sicher weiß, was abgearbeitet ist, verschiedene Instanzen verschiedene Stände haben und PocketBase aus Max' Sicht nicht optimal genutzt wird → fragmentierte Stände. Aber: Max hat keine Lust darauf; Zwang nur, wenn aus Claudes Sicht alles im Chaos versinkt. Solange die Struktur funktioniert, gehen Wandering Shell, dann Dil-Sekte / Broken Shell vor. Beleg aus dem Briefing 20.11.: 19 Fäden „fällig“, davon rund die Hälfte in Wahrheit erledigt, pausiert oder wartend – die Fälligkeiten wurden am 12.11. pauschal auf 16.11. gesetzt und nie nachgezogen. Heute per Rückmeldung bereinigt (10 Fäden).
— 06.11.2026 (Cloud, Briefing-Session): Max präzisiert die Vision. ZIEL: alle wesentlichen Daten lokal, modell-/anbieter-agnostisch, ein kuratierter Stand (Wiki/Obsidian), bei dem sicher ist: das ist aktuell. ROLLEN: wombat = Master-Claude; IlluminaWS = Hilfs-KI-Suite für Medienproduktion + Spezial-KIs; Entendrache = mobiler Zugangspunkt; später Julias Rechner und Garten. Vorher: grundständige Bereinigung des Datenstands. PROBLEM: zwei Gedächtnisse (Anthropic-intern ~80 Dateien mit Dubletten vs. PocketBase), stand_schreiben überschreibt `stand`, Instanzen priorisieren teils falsche Quelle. Max denkt sprunghaft → Struktur muss das abfangen. BEST-PRACTICE-RECHERCHE: Karpathy „LLM Wiki“ (Rohquellen unveränderlich, LLM pflegt Markdown-Wiki, Schema, ingest/query/lint, Git + Obsidian), OpenClaw-Muster (MEMORY.md ≤200 Zeilen + append-only Tageslogs), Markdown/SQLite statt Vektor-DB.
— 04.11.2026: Assistenz-Kram (Repo duckdevlab-assistenz, PRs aus AUFTRAG.md) mit Cloud-Guthaben gebaut, nicht deployt. Weitere Arbeit über lokale Instanzen oder Connector „Server“.
— 03.11.2026: Repo baerimbild/duckdevlab-assistenz angelegt (mcp/, schema/, prompts/, ARCHITEKTUR.md, AUFTRAG.md mit PR 1–3, docs/konzept.md, docs/ENTSCHEIDUNGEN.md, deploy.sh).

## Offen

- NEU 06.11.: Gedächtnis-Umbau (Iteration 1, geht ohne Hardware über Connector „Server“/Repo): Collection `verlauf` (faden, datum, instanz, text) append-only, `stand` = neuester Eintrag, stand_lesen zeigt letzte 5; Felder instanz/quelle; nächtlicher Markdown-Export aller Fäden/Bereiche in den Vault (Git) als lesbarer, anbieterfreier Stand; Lint-Lauf (Widersprüche, Dubletten, verwaiste Fäden) als Wochenschluss. Entscheidung Max offen: Anthropic-Memory („Generate memory from chats“) abschalten oder nur auf Stil beschränken.
- NEU 06.11.: Grundbereinigung Datenstand (Anthropic-Memory-Dubletten, alte claude.ai-Projekte, Vault, Planka-Reste) → erst Zielstruktur festlegen (Wiki-Schema wie Karpathy: Rohquellen / kuratiert / Schema), dann migrieren. Braucht Max’ Zeit, Hardware nicht zwingend.
- NEU 06.11.: Ablauf erzwingen: Claude-Code-Hooks (SessionStart stand_liste+Bereich, Stop „Faden geschrieben?“) auf wombat/WSL; Projektanweisung für claude.ai mit Dreischritt Einordnen → Arbeiten → stand_schreiben.
- Repo duckdevlab-assistenz (Max legt leer an): /opt/mcp als Quelle hineinnehmen, PocketBase-Migration, Briefing-Prompt, später wombat-Master-Skripte. Claude-Code-Auftrag dafür schreiben (Guthaben 83 $).
- Kalender: Max trägt feste Termine ein oder nennt sie, Claude trägt sie ein.
- Branches aufräumen (nur Max, gh auf wombat).
- MCP-Token rotieren (Max entscheidet).
- Stufe 2 später: Wochenschluss-Auftrag, wombat als Master Stufe 1, Julias Tokens, Werkbank-Panel als Kommandozentrale, Controller über aufwand.
- Alte Audit-Punkte 1–8 (Backups auf wombat, Git-Spiegel, Headscale, Google-Ausstieg) unverändert offen.
- Faden l3b6zgbipp7t2rz (Reachy Dock Zugänge) ist durch das Register weitgehend abgedeckt → abschließen oder Rest hierher.
- NEU 12.11.2026 (Max, aus dem Chat „RimWorld With You“): Arbeit zwischen Instanzen grundsätzlich über GitHub-Repos austauschen (Code, Skripte, Doku); Stand und Entscheidungen bleiben im Gedächtnis. Zu klären: Maschinen- und Ops-Skripte brauchen ein Repo ohne Zugangsdaten (duckdevlab-ops enthält zugaenge). Dazu Regel 13 in „allgemein“ (Terminal statt Klick-Fernsteuerung) und der Nachtrag im Register.

## Nächster Schritt

Kleinster wirksamer Schritt ohne Max' Zeit: Briefing-Lauf pflegt Fälligkeiten nach Max' Rückmeldung nach (wie heute). Großer Schritt bleibt: verlauf-Collection (append-only), Export, Lint; PR 1 deployen; Hooks auf wombat/WSL. Wiedervorlage 30.11.

## Ablage

Repo: https://github.com/baerimbild/duckdevlab-assistenz (bis PR 3 gehört es Claude Code Cloud). Server: /opt/ops/src/duckdevlab-assistenz (noch nicht geklont), /opt/mcp (läuft), Konzept /opt/ops/notizen/assistenz-konzept-2026-11-02.md.

## Prio

hoch

## Aufwand

Claude Code Cloud (Briefing-Session 06.11.), ca. 20 min
