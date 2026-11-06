# Server-Zugang für Claude (MCP-Connector „Server“)

Projekt `studio` · id `1arllrx6jy8uxa8` · aktualisiert 2026-11-03 07:12

## Stand

28.10.2026: Läuft. Root-Zugang über den Connector „Server“ funktioniert. User claude auf dem Server gelöscht, sein Material liegt jetzt unter /opt/ops: docs/src und docs/builder, Notfallskript /usr/local/bin/docs-build, hcapi-patch, Archiv archiv/umbau-2026-10-27 mit 1,1 GB. Doku-Repo baerimbild/duckdevlab-docs ist die Quelle (Push auf main → Pipeline). Commit 5c53b19 erklärt Server-MCP und neue Pfade, Pipeline erfolgreich.

## Nächster Schritt

Optional: Host- und Origin-Check und Log-Rotation für shell-mcp. Kopie von /opt/shell-mcp nach duckdevlab-ops\server\shell-mcp. /opt/ops/docs/src ist auf dem Stand vor 5c53b19, also nur Notfall.

## Ablage

Server /opt/shell-mcp, /opt/ops; Doku docs.duckdevlab.com → Dienste → Server-MCP; Repo baerimbild/duckdevlab-docs

## Prio

geparkt
