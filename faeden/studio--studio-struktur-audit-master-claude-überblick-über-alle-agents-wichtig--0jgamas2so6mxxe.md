# Studio · Struktur-Audit + Master-Claude (Überblick über alle Agents) – WICHTIG

Projekt `studio` · id `0jgamas2so6mxxe` · aktualisiert 2026-11-06 06:50 · fällig 2026-11-10

## Stand

06.11.2026 (Cloud, Briefing-Session): Max präzisiert die Vision und bittet, das Thema im Blick zu behalten („on track“). ZIEL: alle wesentlichen Daten lokal, modell-/anbieter-agnostisch, ein kuratierter Stand (Wiki/Obsidian), bei dem sicher ist: das ist aktuell – entweder Claude fragen oder dort nachschauen. ROLLEN: wombat = Master-Claude, behält alles im Blick, startet/ergänzt Dienste; IlluminaWS = Hilfs-KI-Suite für Medienproduktion + Spezial-KIs (Aufräumen, Medienklassifikation), die der Master anweist und überwacht; Entendrache = mobiler Zugangspunkt von überall; später Julias Rechner und Garten (Solar, Sensorik). Vorher gewünscht: grundständige Bereinigung des Datenstands. PROBLEM (Max): zwei Gedächtnisse (Anthropic-intern ~80 Dateien mit Dubletten vs. PocketBase-Gedächtnis), stand_schreiben überschreibt `stand`, Instanzen priorisieren teils falsche Quelle. Max denkt sprunghaft, mehrere Themen pro Chat → Struktur muss das abfangen (Themen als Fäden parken, Einordnung zuerst). BEST-PRACTICE-RECHERCHE (Claude): Karpathy „LLM Wiki“ (04/2026: Rohquellen unveränderlich, LLM pflegt Markdown-Wiki, Schema-Datei, Workflows ingest/query/lint, Git + Obsidian), OpenClaw-Muster (MEMORY.md ≤200 Zeilen für Stabiles + append-only Tageslogs, Konsolidierung: neues ersetzt in MEMORY.md, altes bleibt im Log), Markdown/SQLite statt Vektor-DB für Einzelnutzer. Max ist diese Woche in Leipzig ohne Hardware-Zugriff.

04.11.2026: Assistenz-Kram (Repo duckdevlab-assistenz, PRs aus AUFTRAG.md) ist mit dem Cloud-Guthaben gebaut, aber noch nicht implementiert/deployt (Max). Cloud-Guthaben ist verbraucht; weitere Arbeit läuft über lokale Instanzen (wombat, WSL) oder Connector „Server“.

03.11.2026, 9:30: Repo baerimbild/duckdevlab-assistenz angelegt und befüllt (main): mcp/ (server.py = Produktionsstand, Dockerfile, compose, env.example), schema/ (claude_stand, claude_bereich, neu claude_health, claude_bericht), prompts/ (Morgen-Briefing, Wochenschluss), ARCHITEKTUR.md, AUFTRAG.md (PR 1 MCP+Schema+Tests, PR 2 Master auf wombat, PR 3 Controller+Übersicht), CLAUDE.md, docs/konzept.md, docs/ENTSCHEIDUNGEN.md, deploy.sh.

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

## Nächster Schritt

Diese Woche (Leipzig, ohne Hardware): Konzept-Iteration als Doku im Repo duckdevlab-assistenz (docs/gedaechtnis-struktur.md: Schichten Rohquellen/kuratiert/Schema, verlauf-Collection, Export, Lint, Rollen wombat/Illumina/Entendrache) + PRs prüfen. Ab Randau: PR 1 deployen, verlauf + Export umsetzen, Hooks auf wombat/WSL, dann Grundbereinigung.

## Ablage

Repo: https://github.com/baerimbild/duckdevlab-assistenz (bis PR 3 gehört es Claude Code Cloud). Server: /opt/ops/src/duckdevlab-assistenz (noch nicht geklont), /opt/mcp (läuft), Konzept /opt/ops/notizen/assistenz-konzept-2026-11-02.md.

## Prio

hoch

## Aufwand

Claude Code Cloud (Briefing-Session 06.11.), ca. 20 min
