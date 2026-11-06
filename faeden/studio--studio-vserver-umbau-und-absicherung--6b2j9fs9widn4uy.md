# Studio · vServer-Umbau und Absicherung

Projekt `studio` · id `6b2j9fs9widn4uy` · aktualisiert 2026-11-03 07:12 · fällig 2026-11-14

## Stand

27.10.2026 abends: Umbau abgeschlossen inkl. Gedächtnis-MCP und Ops-Doku (https://docs.duckdevlab.com, Login wie Sites-Panel, Quelle duckdevlab-ops\docs, Build ~/bin/docs-build). Audit-Protokoll Abschnitte 1–17. 30.10.: Backups (vServer → wombat) und „Proxy/Portainer nur über Tailscale“ laufen jetzt im Faden „Studio · Baernetz“.

## Offen

manitu kündigen (Max). innershell.dev läuft 10.12.2026 ab, Verlängerung prüfen. pocketbase.duckdevlab.com erst entfernen, wenn hcapi auf innershell.dev umgestellt. hcapi hat weiter docker.sock (Socket-Proxy später). Excalidraw-Volume und web/moneymoves-Volumes können nach Karenz weg. Claude-User auf dem Server nach Abschluss entfernen. (Backups + Tailscale-Zugang → Faden „Studio · Baernetz“.)

## Nächster Schritt

Godot-Template deployfähig, manitu kündigen, Claude-SSH-User entfernen (vorher docs-src + bin nach /home/max). Backups: siehe Faden „Studio · Baernetz“.

## Ablage

duckdevlab-ops\audit\befunde-2026-10-27.md; https://docs.duckdevlab.com (Changelog + Offen-Liste)

## Chat

frühstück mit opus / vServer-Umbau (27.10.2026)

## Prio

normal
