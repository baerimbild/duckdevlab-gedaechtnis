# Studio · Baernetz

Projekt `studio` · id `huylgax5w21yok1` · aktualisiert 2026-11-03 07:55 · fällig 2026-11-12

## Stand

03.11.2026: Max hat drei Punkte als „irgendwann“ genannt: UniFi Express statt Starlink-Router in Randau einrichten; vServer ins Tailnet bringen; das Tailnet insgesamt reviewen und für alle Geräte sauber konfigurieren (Keys, Routen, MagicDNS, ACLs). Alle drei sind hier schon als offene Punkte geführt, jetzt ausdrücklich von Max bestätigt. manitu kündigen bleibt im Faden vServer-Umbau (6b2j9fs9widn4uy).

30.10.2026: Faden angelegt (Heim-Infrastruktur: Tailscale-Rest, Backups, KI-Server, Werkbank-Startseite). wombat (RPi 5) neu aufgesetzt und online, mit Tailscale und Jellyfin. Randau hängt am Starlink-Router. vServer-Ist (30.10.): / 63 GB, 38 GB frei; zu sichern ca. 4,6 GB roh. Auf dem vServer weder restic noch Tailscale installiert.

## Offen

1) Tailscale-Check: Key-Ablauf für wombat aus? Subnetz-Route fürs aktuelle Netz freigegeben? MagicDNS an? IlluminaWS als eigener Knoten? 2) Backups: Platz auf wombat klären (SN850X 2 TB, Filme drauf); vServer → wombat nächtlich mit restic über Tailscale (vServer muss dafür ins Tailnet; Vorschlag restic rest-server --append-only auf wombat, damit ein kompromittierter vServer keine Backups löschen kann); IlluminaWS E:\Studio → wombat nächtlich; einmal testweise zurückspielen; wöchentliche Offsite-Kopie (vServer oder Storage Box) bleibt offen. 3) KI-Server: Ollama, Open WebUI, Tailscale Serve (aus IlluminaWS-Faden). 4) Werkbank-Startseite auf wombat: WS-Status wach/schläft + Weck-Knopf, GPU/VRAM je Dienst, Links, später Jobs an ComfyUI- und TRELLIS-API. Aus „IlluminaWS einrichten“ umgehängt: UniFi Express als Router der Wohnung (Starlink in Bypass, statische Route 192.168.100.1); feste Adresse 192.168.1.121 für IlluminaWS – Starlink-Router kann laut Foren keine DHCP-Reservierung, also statische IP am Rechner außerhalb des Pools, Tailscale-Name oder erst mit UniFi; danach HOST in E:\Studio\Tools\comfy\api\*.py prüfen. Aus „vServer-Umbau“: proxy.innershell.dev und Portainer später nur über Tailscale. Frühjahr: Fritz!Box 4040 + Repeater in den Garten, Pi Zero 2 W als Knoten. Hinweis: Cloud-Guthaben verfällt 5.11.2026.

## Nächster Schritt

Nach der Leipzig-Woche: Tailnet-Review als eigener Block (Geräte-Liste, Key-Ablauf, Routen, MagicDNS, ACLs), dabei vServer ins Tailnet; danach UniFi Express einrichten (Starlink Bypass); dann Backups vServer → wombat.

## Ablage

Doku: https://docs.duckdevlab.com/netzwerk/ (Zielbild, wombat, Geräte & Backup), /werkbank/, /server/backups/ (Quelle duckdevlab-ops\docs bzw. Repo baerimbild/duckdevlab-docs). Skripte: E:\Studio\Tools\wombat\wombat_setup.sh, E:\Studio\Tools\setup\backup_nacht.ps1.

## Chat

frühstück mit opus / Studio · Baernetz (30.10.2026)

## Prio

normal
