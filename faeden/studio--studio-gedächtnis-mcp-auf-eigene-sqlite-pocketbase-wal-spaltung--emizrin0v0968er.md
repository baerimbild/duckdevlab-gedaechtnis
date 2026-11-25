# Studio · Gedächtnis-MCP auf eigene SQLite, PocketBase-WAL-Spaltung

Projekt `studio` · id `emizrin0v0968er` · aktualisiert 2026-11-24 13:11

## Stand

24.11.2026, 14:10: PocketBase repariert. Kolonie-Crons pausiert, gelöschte WAL über Prozess-Handle gesichert, gestoppt, data.db/auxiliary.db durch zusammengeführte Stände ersetzt (/root/pbdiag/rescue3-20261124-140811), gestartet. Keine (deleted)-Handles, alle Collections lesbar, keine Fehler, kein Datenverlust. Changelog gepusht. Max will Postgres/NocoDB/Uptime-Kuma-Umbau vorerst NICHT (Mehrwert nicht überzeugend); Gedächtnis bleibt auf eigener SQLite im MCP. Davor (24.11.): Gedächtnis-MCP auf eigene SQLite /opt/mcp/data/gedaechtnis.db umgezogen, 0 Abweichungen.

## Offen

Wochenbriefing-Routine schreibt per curl in PocketBase claude_briefing, umstellen auf briefing_schreiben. Altbestand claude_*/dailylog/is_benachrichtigung in PocketBase entfernen (Max will, dass nur noch drin ist, was PB braucht); characters/ws_characters: Max fragen. Port 8090 öffentlich. Wächter-Cron für (deleted)-Handles fehlt. Auslöser der Spaltung unbekannt.

## Nächster Schritt

Max fragen, ob Altbestand-Aufräumen, Port-Fix und Wächter-Cron gemacht werden sollen.

## Ablage

Analyse: https://claude.ai/artifact/3RggDa7GzaEHZVpdrC4wk9 · Server /opt/mcp (Rückweg *.bak-2026-11-24-pocketbase) · /root/pbdiag/

## Prio

normal

## Aufwand

Claude Code Cloud, ca. 1,5 h
