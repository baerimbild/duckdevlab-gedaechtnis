# Studio · Sites-Panel und Deploy-Pipeline

Projekt `studio` · id `wmiuiccuefp6cr6` · aktualisiert 2026-11-12 11:24 · fällig 2026-11-16

## Stand

06.11.2026: duckdevlab.com hatte seit dem ersten Pipeline-Deploy kein Hintergrundbild mehr (assets/img/background-img war per .gitignore vom Repo ausgeschlossen, rsync --delete hat es auf dem Server gelöscht). Bild aus /opt/ops/archiv/umbau-2026-10-27/backups/opt-sites-vor-panel.tar.gz direkt nach /opt/sites/library/duckdevlab zurückgelegt (live) und ins Repo übernommen (PNG + WebP, .gitignore raus); Hintergrund auf body::before fixed statt background-attachment:fixed (iOS/Android). Dazu Links zu Inner Shell, Wandering Shell, Makermon. makermon: Devkit-Button ohne festes #fff (Dunkelmodus), Linkfarbe Tinte + gelbe Unterstreichung. sites-deploy README: Tabelle der angeschlossenen Projekte, Hinweis auf --delete. Alles auf Branch ccr-2600e16c-jgvfft in duckdevlab.com, makermon, sites-deploy; PRs/Merge stehen aus.

## Offen

duckdevlab-ops\docs ist noch kein Git-Clone (Max: git init + remote). urschltarot: Repo + Touch-Steuerung. Godot-Template deployfähig. deploytest-Eintrag in der Library kann archiviert werden.

## Nächster Schritt

Max: die drei Branches ccr-2600e16c-jgvfft (duckdevlab.com, makermon, sites-deploy) nach main mergen, dann deployt die Pipeline. Danach wie gehabt: Godot-Template → urschltarot als erstes Godot-Deploy.

## Ablage

Server-Konfig: duckdevlab-ops\server\sites\ (Caddyfile, docker-compose, panel/). Seitenquellen: duckdevlab-ops\sites\ und die Repos baerimbild.de, inner_shell_main_client.

## Chat

frühstück mit opus / vServer-Umbau (27.10.2026)

## Prio

normal

## Aufwand

Claude Code Cloud, ca. 1 h
