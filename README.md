# Gedächtnis-Export

Automatischer Markdown-Export des PocketBase-Gedächtnisses (`pocketbase.innershell.dev`, Collections
`claude_bereich`, `claude_stand`, `claude_briefing`). Quelle der Wahrheit ist PocketBase; dieses Repo ist
Lesekopie, Versionierung (Git-Historie) und Backup. Nicht hier editieren – Änderungen über den
Gedächtnis-MCP (`bereich_schreiben`, `stand_schreiben`).

- [BEREICHE.md](BEREICHE.md) – Dauerwissen pro Bereich
- [FAEDEN.md](FAEDEN.md) – offene und abgeschlossene Arbeitsfäden
- `briefing/` – Wochenbriefings

Export: `/usr/local/bin/gedaechtnis-export.py`, täglich per Cron (siehe `/etc/cron.d/duckdevlab-backup`).
Letzter Lauf: 2026-11-12 03:31
