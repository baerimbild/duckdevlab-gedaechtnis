# Studio · Baernetz

Projekt `studio` · id `huylgax5w21yok1` · aktualisiert 2026-11-12 11:24 · fällig 2026-11-16

## Stand

06.11.2026 21:50: Route 192.168.1.0/24 für wombat von Max freigegeben; vServer mit --accept-routes, erreicht wombat-LAN (192.168.1.144, Jellyfin) und damit das Baernetz. Entendrache: SSH-Config Host wombat → 100.82.163.121 (vorher LAN-IP), ssh wombat geht aus Leipzig. IlluminaWS: war an, weil Julia am 05.11. den Reachy-Agenten vorgeführt hat; `01` hatte „kein Standby“ gesetzt, also läuft er sonst durch. Max hat ihn per `ssh maxst@100.119.194.47 "shutdown /s /t 10"` heruntergefahren (Windows-OpenSSH auf IlluminaWS, Port 22 im Tailnet; Sunshine 47989). Entscheidung Standby-nach-30-min vs. Dauerlauf steht noch aus (Einzeiler mit powercfg + WakeToRun für die Nachtsicherung liegt im Chat). Julias Knoten: bosshuke (fester Rechner), laborbaer (Surface) – Konto hookeyhook, ok.

06.11.2026 21:35: vServer ist im Tailnet: Knoten „vserver“ 100.120.16.21, Tailscale 1.104.5, --ssh, --accept-dns=false, Key-Ablauf aus. Tailnet: vserver, entendrache 100.104.9.67, illuminaws 100.119.194.47, wombat 100.82.163.121 (LAN 192.168.1.144), reachy-mini, redmi-note-15, bosshuke, laborbaer. wombat bot keine Subnetz-Route an (Neuaufsetzen 30.10. ohne --advertise-routes) → per Tailscale-SSH vom vServer korrigiert (tailscale up --advertise-routes=192.168.1.0/24 --ssh --accept-dns=false --hostname=wombat --operator=max). Gedächtnis-Export pusht (duckdevlab-gedaechtnis), Repo broken-shell angelegt, Server hat Account-weiten GitHub-Key (s. Register).

06.11.2026 21:05: Lokales Backup auf dem vServer: /usr/local/bin/backup-duckdevlab.sh täglich 03:30 → /var/backups/duckdevlab/<datum>/ (PocketBase-SQLite-Snapshot, Planka pg_dumpall, Volumes, /opt, Library), 14 Tage. Gedächtnis-Export /usr/local/bin/gedaechtnis-export.py → /opt/ops/gedaechtnis (Git).

03.11.2026: Max bestätigt: UniFi Express statt Starlink-Router; vServer ins Tailnet; Tailnet-Review. 30.10.2026: Faden angelegt; wombat neu aufgesetzt (Tailscale, Jellyfin).

## Offen

Entscheidung IlluminaWS: Standby nach 30 min (powercfg, Nachtsicherung mit WakeToRun) oder Dauerlauf → Geräterollen-Doc entsprechend anpassen. Weck-Knopf fürs Werkbank-Panel auf wombat (auch für Julia/Reachy). Offsite-Backup vServer → wombat jetzt möglich: restic rest-server --append-only auf wombat (SN850X, Platz klären), nächtlich, einmal Restore testen. proxy.innershell.dev + Portainer nur noch über Tailnet (NPM-Hosts entfernen; Port 22 nach außen später zu). MagicDNS prüfen; ACL für Tailscale-SSH sichten. IlluminaWS E:\Studio → wombat nächtlich. KI-Server: Ollama, Open WebUI, Tailscale Serve. UniFi Express als Router (Starlink Bypass, statische Route 192.168.100.1); feste Adresse 192.168.1.121; danach HOST in E:\Studio\Tools\comfy\api\*.py prüfen. Frühjahr: Fritz!Box 4040 + Repeater in den Garten, Pi Zero 2 W als Knoten. duckdevlab-ops\server\mcp\server.py nachziehen (Regel 12). Repo broken-shell nach E:\Studio\Projekte\broken-shell klonen.

## Nächster Schritt

Backups vServer → wombat über das Tailnet (restic rest-server append-only auf wombat), dann Proxy/Portainer aus dem NPM nehmen. Vorher kurz mit Max: Standby-Entscheidung für IlluminaWS.

## Ablage

Doku: https://docs.duckdevlab.com/netzwerk/ (Zielbild, wombat, Geräte & Backup), /server/backups/ (Repo baerimbild/duckdevlab-docs, Klon /opt/ops/docs/src). Backups: /var/backups/duckdevlab, Log /var/log/backup-duckdevlab.log. Gedächtnis-Export: /opt/ops/gedaechtnis → github baerimbild/duckdevlab-gedaechtnis. Tailnet: login.tailscale.com/admin/machines. Skripte: E:\Studio\Tools\wombat\wombat_setup.sh, E:\Studio\Tools\setup\backup_nacht.ps1.

## Chat

frühstück mit opus / Studio · Baernetz (30.10.2026)

## Prio

normal
