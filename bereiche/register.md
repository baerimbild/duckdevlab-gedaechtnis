# Register – Geräte, Claude-Instanzen, Rechte, Repos (vor „ich kann das nicht“ lesen)

`key: register` · aktualisiert 2026-11-12 12:08 · id `5sr5fbfrkowiwwr`

## Kurzstand

12.11.2026: Nachtrag zur Entendrachen-Bridge (keine Shell, Computer-Steuerung unerwünscht) und zu stand_schreiben. — 06.11.2026: vServer hat jetzt ausgehendes SSH/Git zu GitHub (account-weiter Key, Max' Entscheidung 06.11.); /opt/ops/docs/src ist ein echter Klon von duckdevlab-docs; tägliches Backup + Gedächtnis-Export laufen. — 03.11.2026 angelegt im Audit. Jede Instanz liest dieses Register, bevor sie behauptet, etwas nicht zu können, und trägt sich ein, wenn sie neu eingerichtet wird. Rechte-Entscheidungen von Max vom 03.11.: wombat volles sudo; WSL darf KI-Dienste starten/stoppen, Pakete installieren, Reachy-Agent deployen; Desktop-App auf IlluminaWS für Ordnerzugriff E:\Studio und Computer-Steuerung (Godot, Blender, ComfyUI). Repos: Stand 03.11. keine offenen PRs, aber viele gemergte Branches liegen herum.

## Regeln

NACHTRAG 12.11.2026 (Erfahrung Cloud-Session mit Entendrachen-Bridge): Die Cloud-Session hat auf dem Entendrachen nur Datei-Tools (auflisten, holen, zurückschreiben), keine Shell. Die Computer-Steuerung kann Terminals nicht betippen, das Einstellungen-Fenster kam nur als graue Fläche an, und sie blendet Max' übrige Fenster aus; Max will sie nicht (Regel 13 in „allgemein“). Bewährter Weg bis dahin: Skript in einen freigegebenen Ordner legen, Max startet es mit einem Einzeiler, Ergebnisdatei zurücklesen. Offen: echter Terminal-Zugriff auf dem Entendrachen (Claude Code lokal), siehe Faden 7mx0jh0mt8ey1w8. Außerdem: stand_schreiben schreibt das Feld stand immer mit (leer = Fehler); einzelne Felder lassen sich verlustfrei nur per PATCH über die PocketBase-API ändern (TOK=$(/root/bin/pb-token)).

NACHTRAG 06.11.2026 (Max' Entscheidung: Zugang vor Vorsicht):
- vServer (Zeile 1) DARF jetzt ausgehend per SSH/Git zu GitHub: Key /root/.ssh/id_ed25519_github_server, Host-Alias `github.com-server` (git@github.com-server:baerimbild/<repo>.git), als SSH-Key im Account baerimbild hinterlegt → Lesen und Pushen auf ALLE baerimbild-Repos. Damit braucht Claude für Repo-Arbeit keine claude.ai-GitHub-Freigabe mehr: über den Connector „Server“ klonen, committen, pushen. Repos ANLEGEN geht per SSH nicht (nur Max, GitHub-UI).
- /opt/ops/docs/src ist seit 06.11. ein Klon von duckdevlab-docs (vorher stale Kopie, Divergenz behoben, Backup /opt/ops/docs/src.bak-2026-11-06). Doku ändern = dort editieren, committen, pushen; `docs-build` baut zusätzlich sofort.
- Backup: /usr/local/bin/backup-duckdevlab.sh täglich 03:30 → /var/backups/duckdevlab/<datum>, 14 Tage. Gedächtnis-Export: /usr/local/bin/gedaechtnis-export.py → /opt/ops/gedaechtnis (Git, Remote baerimbild/duckdevlab-gedaechtnis – Repo muss Max noch anlegen).

GERÄTE UND INSTANZEN (Gerät | Instanz | Zuständigkeit | Rechte | Darf nicht)

1. vServer 89.58.10.130 (Netcup, Debian, Docker) | Connector „Server“ in jeder Claude-Session (Tools befehl, datei_lesen, datei_schreiben) | Deploys nach /opt/sites, Container, PocketBase, NPM/Caddy, Doku-Build | Root über /opt/shell-mcp (nsenter PID 1), Log /opt/shell-mcp/log/befehle.jsonl; PocketBase-Superuser-Token nur über TOK=$(/root/bin/pb-token) | Repos anlegen, GitHub-Secrets setzen, kein gh auf dem Server; (ausgehendes SSH zu GitHub seit 06.11. erlaubt, s. Nachtrag); nie docker exec pocketbase gegen den laufenden Server (WAL-Vorfall 28.10.)

2. Claude Code Cloud (Guthaben-Sessions, auch diese Wiedervorlage-Session) | Repos bauen, PRs, Server-Umbau über Connector „Server“, Gedächtnis | GitHub push auf baerimbild-Repos nach add_repo (Max bestätigt jede Freigabe; seit 06.11. besser über den Server pushen), Connector „Server“, Connector „Gedächtnis“, Google-Kalender/Gmail/Drive, Claude Docs | Repos anlegen, Branches löschen (Proxy 403), SSH, Geräte im Heimnetz (nur über Entendrachen-Bridge, wenn gekoppelt)

3. wombat (Raspberry Pi 5, Always-on, Heimnetz, Tailscale) | Claude Code lokal (seit 01.11.) | Heimnetz-Arbeiten: Orange Pi/Reachy-Starter, Backups vom vServer, Mediaserver, künftig Master-Claude Stufe 1 | VOLLES SUDO (Entscheidung Max 03.11.), SSH ins Heimnetz (OPi), gh vorhanden | Hinter Starlink-CGNAT, von außen nur über Tailscale erreichbar

4. IlluminaWS, WSL Ubuntu (RTX 5090) | Claude Code lokal (seit 01.11.) | KI-Dienste (TTS, Agent, ComfyUI-Start), Reachy-Agent, Werkbank-Agent | DARF (Max 03.11.): KI-Dienste starten und stoppen, Pakete installieren (apt/pip/npm), Reachy-Agent auf den Orange Pi deployen und dort neu starten; Zugriff auf Windows-Ollama | Nur im LAN erreichbar (192.168.1.121 ComfyUI, 192.168.1.144 Werkbank-Panel)

5. IlluminaWS, Windows | Claude Desktop-App | Ordnerzugriff auf E:\Studio (CLAUDE.md, Tools, Ausgaben) und Computer-Steuerung für Godot, Blender, ComfyUI (Max 03.11.) | Ordner nach Freigabe, Computer-Use nach Freigabe | Keine Server-Umbauten von dort (dafür Connector „Server“ in jeder Session)

6. Entendrachen (Surface Pro 9, mobiler Hauptrechner) | Claude Desktop-App, claude.ai, Fernsteuerung von Cloud-Sessions | Planung, Gespräche, Ordner auf dem Surface (z. B. Desktop\wandering shell, duckdevlab-ops) | Ordner nach Freigabe; Bridge zu Cloud-Sessions | `!`-Präfix im Chat kommt bei Fernsteuerung nur als Text an

7. Orange Pi 3 LTS (Reachy Dock) | kein Claude | Reachy-Daemon, Touch-UI (Browser-Kiosk) | wird von wombat per SSH bedient, Deploy aus WSL | —

8. Julia | noch kein Zugang | Soll eigene, widerrufbare Tokens für Connector „Server“ und „Gedächtnis“ bekommen (Audit-Punkt, Stufe 3) | — | —

KONVENTIONEN
- Ein Repo, eine Instanz pro Tag. Der Faden nennt im Feld ablage, wer dran ist.
- Wer mergen kann, merged (Bereich allgemein).
- Secrets nie im Chat; Max tippt Tokens selbst in UIs.
- Jede neue Instanz trägt sich hier ein (Gerät, Tool, Rechte), bevor sie arbeitet.
- Zugang vor Vorsicht (Max, 06.11.): Max nimmt Risiken durch breiten Werkzeug-Zugang bewusst in Kauf; keine Sicherheitsbelehrungen, Sicherheitsrelevantes einmal nüchtern nennen, dann machen.

REPOS (Stand 03.11.2026, geprüft über GitHub-API; alle privat unter baerimbild)
Aktiv mit Claude-Code-Cloud-Guthaben, alle PRs gemerged, KEINE offenen PRs:
- reachy: 10 PRs gemerged (zuletzt #10 fix/hold-zombie, 02.11.). 12 alte Branches liegen; fix/streicheln-pause und streicheln-body-yaw sind ohne PR, aber 0 ahead → nur löschen. Kein Workflow.
- werkbank: 8 PRs gemerged (Agent, Panel, TTS, IlluminaWS-Registry, Registry-Editor). 8 alte Branches. CI ci.yml.
- luanti-dialoge: 10 PRs gemerged (Arbeitspakete 0–4c, Editor-Release). 10 alte Branches. Workflows editor-release.yml, tests.yml.
- luanti-dialoge-api: nur main, Workflows image.yml (ghcr), tests.yml.
- luanti-dialoge-testserver: nur main, kein Workflow (Deploy von Hand auf dem Zielhost).
- makermon-world: PR #1 gemerged (02.11., Web-Export, Touch, Devkit). Branch claude/web-update liegt noch. Workflow deploy.yml (Pipeline → makermon-world.duckdevlab.com).
- makermon: nur main, deploy.yml.
- sites-deploy: nur main, deploy.yml (zentrale Pipeline, Caller-Workflows in den Site-Repos).
- duckdevlab-docs: main + toter Branch pluesch-doku (1 ahead, 9 behind). deploy.yml → docs.duckdevlab.com. 06.11.: Commit d12ed71 vom Server (Backups, Regel 12, Wandering Shell).
- duckdevlab-gedaechtnis: NOCH ANZULEGEN (privat, leer) – Ziel des Gedächtnis-Exports.
Weitere (nicht im Audit geprüft): innershell-landing, moneymoves, duckdevlab.com, historycraft-site, inner_shell_main_client, baerimbild.de, duckdevlab_godot_template, testing, massive_igel, innercore_animation, historycraft_manager, duckdevlab_vault, character_generator, innershell.dev, gtpRossTaskPlanner, rossTaskPlanner. Kein Repo für Broken Shell (Lore, GDD, Prototyp) – anlegen (broken-shell).
Aufräumen (nur Max kann Branches löschen, Claude bekommt 403): gemergte Branches in reachy, werkbank, luanti-dialoge, makermon-world; pluesch-doku in duckdevlab-docs.

DEPLOY-WEGE
- Statische Sites und Godot-Web: Repo mit site.json + Caller-Workflow → sites-deploy → /opt/sites/library/<name> → <name>.duckdevlab.com (Panel sites.duckdevlab.com).
- Kleine Apps ohne GitHub: /opt/ops/src/<name> mit deploy.sh (Beispiel pluesch).
- Gedächtnis-MCP: heute lose Dateien in /opt/mcp (server.py, Dockerfile, compose, mcp.env), KEIN Git → soll ins Repo duckdevlab-assistenz.
- Docs: Push auf main in duckdevlab-docs → Pipeline; Notfall /usr/local/bin/docs-build (Quelle = Klon /opt/ops/docs/src).
- Git-Arbeit vom Server aus (seit 06.11.): git clone git@github.com-server:baerimbild/<repo>.git, committen als claude-vserver, pushen.

## Ablage

Quelle für Serverdetails: Bereich studio. Quelle für Reachy-Zugänge: Faden l3b6zgbipp7t2rz. Werkbank-Registry (Dienste auf IlluminaWS): Repo baerimbild/werkbank, registry/ im Panel editierbar.

## Links

https://github.com/baerimbild | https://sites.duckdevlab.com | https://docs.duckdevlab.com
