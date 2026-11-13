# Studio · Reachy Dock – Übersicht Zugänge & Abläufe (Besprechung 2.11.)

Projekt `studio` · id `l3b6zgbipp7t2rz` · aktualisiert 2026-11-12 11:24 · fällig 2026-11-16

## Stand

1.11.2026, Stand ca. 23 Uhr (wombat-Claude). Viel an einem Tag, Max wollte für morgen eine ruhige Übersicht. OPi ist ausgeschaltet (Kopf in Schlafposition, sauber heruntergefahren).

GERÄTE & WER WAS MACHT
- wombat (Pi 5, Heimnetz + Tailscale): Claude Code, Build-Maschine, Jellyfin (Docker), Werkbank-Panel (/opt/werkbank, uv-Python 3.12). Repo-Klon /home/max/reachy-repo. Alte OPi-Quelle /home/max/reachy/sw (kein Git, nur noch Dublette).
- reachy / OPi (192.168.1.108): Daemon :8000, Touch-UI :8080 (/opt/reachy/ui), Chromium-Kiosk. Kein Repo-Klon; Deploy per scp von wombat.
- IlluminaWS (192.168.1.121 LAN, 100.119.194.47 Tailscale): eigenes Claude Code, Reachy-Agent (WSL), Ollama :11434, TTS „Thor“ (Qwen3-TTS).
- entendrache = Surface (heute nur Taildrop-Empfänger).

ZUGÄNGE
- wombat → OPi: SSH als max, sudo ohne Passwort.
- wombat → GitHub baerimbild/reachy: Deploy-Key mit Schreibrecht (~/.ssh/reachy_deploy, SSH-Alias github-reachy). Standard-Key von wombat gilt nur für werkbank.
- wombat → IlluminaWS: KEIN SSH (Key abgelehnt, vermutl. administrators_authorized_keys fehlt). Nur Ollama-API und Taildrop (tailscale operator=max gesetzt).
- IlluminaWS → Repo: eigener Zugang (von Illumina-Claude eingerichtet).

REPO baerimbild/reachy (privat)
- main: Agent-Code im Root + OPI.md (Schnittstelle) + antworttext/; opi/ = kompletter OPi-Stand (UI, quiz, streicheln, kiosk, daemon-Wrapper, audio, systemd, sounds, setup.sh). Nicht drin: gst-webrtc-arm64.tgz (67 MB, auf wombat ~/).
- Workflow: Branch + Push, Max merged (auf Zuruf hat wombat auch selbst per Fast-Forward gemergt).

HEUTE ERLEDIGT
- Asgard-Szenen SG-1 S05E22 per Vision-Modell geschnitten (/home/max/asgard-szenen), per Taildrop auf IlluminaWS + Surface; S08E01/02 auf IlluminaWS.
- Ollama IlluminaWS: qwen3-vl:8b-instruct gezogen (Thinking-Variante wieder gelöscht).
- Dock-UI: Buttons Foto/Kamera (camera photo|live|stop), „✕ Kamera beenden“, Statuszeile „Agent nicht verbunden“, alte Events >30 s verworfen.
- streicheln.py: body_yaw auf alle Yaw-Ziele addiert (gemergt, deployt, am Roboter ungetestet).
- Antworttext-Anzeige nach UEBERGABE_WOMBAT.md (Auto-Schrift 28→20 px, Scroll ans Ende, wachsender Text, kind=reply, Stimme-aus-Symbol). Branch touch-antworttext, auf dem OPi schon aktiv.
- Übersetzer-Popup: Startoption wirkte nicht, jetzt Chromium-Richtlinie /etc/chromium/policies/managed/reachy-kiosk.json – Popup weg (Screenshot geprüft).
- Panne: uv-Python 3.12 auf wombat versehentlich entfernt (gehört zum Werkbank-Panel), sofort neu installiert.
- Tote Kamera-Taps lagen daran, dass auf IlluminaWS kein Agent lief.
- Aufgeräumt: doppeltes tgz in sw/, Caches, Job-Temp. wombat-CLAUDE.md verweist aufs Repo als Quelle.

## Offen

- NÄCHSTER TASK: Aus-Knopf auf dem Display (Rückfrage, goto_sleep, poweroff, Hinweis „Netzteile ziehen“; UI läuft als reachy → sudoers/polkit nur für poweroff, auch in setup.sh). Details in wombat-CLAUDE.md.
- Branch touch-antworttext mergen (OPi ist bis dahin weiter als main).
- Alte Kopien auflösen: wombat:~/reachy/sw und reachy:~/reachy-sw (OPi nur mit Rückfrage löschen).
- Deploy-Weg Repo → OPi klären (Klon auf dem OPi? Skript von wombat?).
- SSH wombat → IlluminaWS ja/nein (für GPU-Jobs).
- body_yaw-Korrektur beim Streicheln am Roboter testen.
- Liegt noch: uv-Cache wombat 1,5 GB (mit Werkbank-Panel geteilt, nur `uv cache prune` bei gestopptem Panel), llama3.2-vision:11b auf IlluminaWS (kaputt, 7,8 GB, Max' Modell), Taildrop-Dateien in den Downloads, OPi-Backups ~/ui-backup-20261101-*.

## Nächster Schritt

2.11.2026: Mit Max in Ruhe durchgehen und als Übersicht darstellen – wer hat welche Rechte, wer greift wo zu, wo wird was gemacht (Tabelle Geräte × Zugänge × Zuständigkeit), offene Punkte entscheiden. Danach als erster Task: Aus-Knopf auf dem Display.

## Ablage

Repo github.com/baerimbild/reachy (opi/, OPI.md) | wombat: /home/max/reachy-repo, /home/max/reachy/sw (alt), /home/max/reachy/CLAUDE.md, /home/max/asgard-szenen | OPi: /opt/reachy/ui, ~/ui-backup-* | IlluminaWS: Downloads (Taildrop)

## Chat

wombat Claude Code, Job 26f4e7e0 (1.11.2026)

## Prio

normal
