# Studio · Baernetz

Projekt `studio` · id `huylgax5w21yok1` · aktualisiert 2026-11-06 20:02 · fällig 2026-11-12

## Stand

06.11.2026 21:05: Lokales Backup auf dem vServer läuft jetzt: /usr/local/bin/backup-duckdevlab.sh täglich 03:30 (Cron /etc/cron.d/duckdevlab-backup) → /var/backups/duckdevlab/<datum>/ (PocketBase-SQLite-Snapshot per .backup-API, Planka pg_dumpall, Volumes, /opt, Library), 14 Tage, erster Lauf 1,1 GB in 77 s. Dazu Gedächtnis-Export /usr/local/bin/gedaechtnis-export.py → Git-Repo /opt/ops/gedaechtnis (Markdown je Bereich/Faden, BEREICHE.md/FAEDEN.md als Übersicht, Commit nur bei Änderung; erster Commit: 42 Bereiche, 25 Fäden). Remote baerimbild/duckdevlab-gedaechtnis eingetragen, Push wartet auf GitHub-Key. Server-Key /root/.ssh/id_ed25519_github_server (Alias github.com-server) angelegt – Max muss den Public Key einmal in GitHub hinterlegen (Deploy-Key mit Schreibrecht pro Repo oder Account-Key), dann kann der Server Docs/Gedächtnis selbst pushen und Claude braucht keine claude.ai-GitHub-Freigabe mehr. Doku server/backups + Changelog aktualisiert und gebaut (Server-Kopie /opt/ops/docs/src; Repo duckdevlab-docs hängt hinterher).

03.11.2026: Max hat drei Punkte als „irgendwann“ genannt: UniFi Express statt Starlink-Router in Randau einrichten; vServer ins Tailnet bringen; das Tailnet insgesamt reviewen und für alle Geräte sauber konfigurieren (Keys, Routen, MagicDNS, ACLs). Alle drei sind hier schon als offene Punkte geführt, jetzt ausdrücklich von Max bestätigt. manitu kündigen bleibt im Faden vServer-Umbau (6b2j9fs9widn4uy).

30.10.2026: Faden angelegt (Heim-Infrastruktur: Tailscale-Rest, Backups, KI-Server, Werkbank-Startseite). wombat (RPi 5) neu aufgesetzt und online, mit Tailscale und Jellyfin. Randau hängt am Starlink-Router. vServer-Ist (30.10.): / 63 GB, 38 GB frei; zu sichern ca. 4,6 GB roh. Auf dem vServer weder restic noch Tailscale installiert.

## Offen

NEU 06.11.: GitHub-Repo baerimbild/duckdevlab-gedaechtnis anlegen (privat, leer) + Public Key des Servers als Deploy-Key (write) eintragen; gleichen Key auch bei duckdevlab-docs, damit der Server Doku-Änderungen pushen kann. Repo duckdevlab-docs mit /opt/ops/docs/src abgleichen (Server ist aktueller). duckdevlab-ops\server\mcp\server.py nachziehen (Regel 12). Offsite-Kopie des Server-Backups (wombat per Pull über Tailscale oder Storage Box) weiterhin offen. — 1) Tailscale-Check: Key-Ablauf für wombat aus? Subnetz-Route fürs aktuelle Netz freigegeben? MagicDNS an? IlluminaWS als eigener Knoten? 2) Backups: Platz auf wombat klären (SN850X 2 TB, Filme drauf); vServer → wombat nächtlich mit restic über Tailscale (vServer muss dafür ins Tailnet; Vorschlag restic rest-server --append-only auf wombat, damit ein kompromittierter vServer keine Backups löschen kann); IlluminaWS E:\Studio → wombat nächtlich; einmal testweise zurückspielen; wöchentliche Offsite-Kopie (vServer oder Storage Box) bleibt offen. 3) KI-Server: Ollama, Open WebUI, Tailscale Serve (aus IlluminaWS-Faden). 4) Werkbank-Startseite auf wombat: WS-Status wach/schläft + Weck-Knopf, GPU/VRAM je Dienst, Links, später Jobs an ComfyUI- und TRELLIS-API. Aus „IlluminaWS einrichten“ umgehängt: UniFi Express als Router der Wohnung (Starlink in Bypass, statische Route 192.168.100.1); feste Adresse 192.168.1.121 für IlluminaWS – Starlink-Router kann laut Foren keine DHCP-Reservierung, also statische IP am Rechner außerhalb des Pools, Tailscale-Name oder erst mit UniFi; danach HOST in E:\Studio\Tools\comfy\api\*.py prüfen. Aus „vServer-Umbau“: proxy.innershell.dev und Portainer später nur über Tailscale. Frühjahr: Fritz!Box 4040 + Repeater in den Garten, Pi Zero 2 W als Knoten.

## Nächster Schritt

Max: Repo duckdevlab-gedaechtnis anlegen und Server-Key eintragen (5 Minuten), dann auf dem vServer `gedaechtnis-export.py` → erster Push. Danach wie geplant: Tailnet-Review, vServer ins Tailnet, UniFi Express, Backups vServer → wombat (Offsite).

## Ablage

Doku: https://docs.duckdevlab.com/netzwerk/ (Zielbild, wombat, Geräte & Backup), /werkbank/, /server/backups/ (Quelle /opt/ops/docs/src auf dem Server bzw. Repo baerimbild/duckdevlab-docs). Backups: /var/backups/duckdevlab, Log /var/log/backup-duckdevlab.log. Gedächtnis-Export: /opt/ops/gedaechtnis (git log). Skripte: E:\Studio\Tools\wombat\wombat_setup.sh, E:\Studio\Tools\setup\backup_nacht.ps1.

## Chat

frühstück mit opus / Studio · Baernetz (30.10.2026)

## Prio

normal
