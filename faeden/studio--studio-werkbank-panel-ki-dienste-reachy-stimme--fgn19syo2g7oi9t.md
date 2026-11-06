# Studio · Werkbank-Panel (KI-Dienste + Reachy-Stimme)

Projekt `studio` · id `fgn19syo2g7oi9t` · aktualisiert 2026-11-03 07:12 · fällig 2026-11-06

## Stand

02.11.2026 abends: werkbank main = 980cf25, deployt auf wombat (/opt/werkbank, systemd) und IlluminaWS (C:\werkbank, Aufgabe „Werkbank-Agent“). Gemergt: #6 Registry-Editor, #7 Unit ReadWritePaths für registry/, #8 EchtesBackend.registry_aktualisieren (Reload gab 500). Agent läuft mit --registry http://192.168.1.144:8070/api/registry, Panel und Agent synchron. Panel: LAN 192.168.1.144:8070, Tailscale wombat.tail4ee8d4.ts.net:8070. wombat: sudo NOPASSWD für systemctl restart werkbank-panel + daemon-reload; gh unter ~/.local/bin; Deploy-Key mit Schreibrecht; SSH maxst@IlluminaWS geht.

## Offen

- pin in panel/config.yaml noch nicht gesetzt (jeder im LAN/Tailnet kann Startbefehle ändern).
- icacls für administrators_authorized_keys auf IlluminaWS mit SIDs nachziehen (deutsches Windows: *S-1-5-32-544, *S-1-5-18).
- Rest der Prüfliste docs/handbuch.md Abschnitt 9.

## Nächster Schritt

PIN setzen (Max entscheidet den Wert), dann Prüfliste Abschnitt 9.

## Ablage

Repo github.com/baerimbild/werkbank; IlluminaWS: C:\werkbank (Agent, Logs C:\werkbank\logs), WSL ~/werkbank (Symlink), Stimmen C:\werkbank\services\tts\voices; Aufgabe „Werkbank-Agent“, Firewall-Regel „Werkbank-Agent“. wombat: /opt/werkbank (systemd werkbank-panel, Port 8070, Update = git pull), Deploy-Key read-only.

## Chat

loser Chat 01.11.2026 „KI-Dashboard + Reachy-Stimme“ → weiter in frühstück mit opus

## Prio

normal
