# Studio · Plüsch-Meldeamt (pluesch.duckdevlab.com)

Projekt `studio` · id `ybeano97rjxld31` · aktualisiert 2026-11-03 07:12 · fällig 2026-11-16

## Stand

28.10.2026 abends: LIVE unter https://pluesch.duckdevlab.com, live getestet (Login, großes Foto, Verkleinerung, Thumbs, Löschen). Collections pluesch + pluesch_users angelegt (Backup vor-pluesch-2026-10-28.zip). Quelle als Git-Repo auf dem Server /opt/ops/src/pluesch (README, deploy.sh, pocketbase/setup.py). Doku docs.duckdevlab.com → Seiten → pluesch + Changelog. Dabei Vorfall: docker exec pocketbase superuser … löschte WAL des laufenden Servers → PB-Neustart, integrity ok, nichts verloren; neu /root/bin/pb-token, Doku umgestellt.

## Offen

Logins für Max und Julia fehlen noch (Max legt sie selbst in der Admin-UI an). Optional: GitHub-Repo baerimbild/pluesch (Max anlegen), dann Quelle pushen und Pipeline nutzen. Remote-Branch pluesch-doku in duckdevlab-docs ist veraltet und kann gelöscht werden (Claude konnte nicht löschen).

## Nächster Schritt

Max: pocketbase.innershell.dev/_/ → pluesch_users → New record (E-Mail, Name, Passwort, verified) für sich und Julia; dann loslegen. Änderungen an der App: in /opt/ops/src/pluesch committen, ./deploy.sh.

## Ablage

Quelle /opt/ops/src/pluesch (Server), live /opt/sites/library/pluesch, Doku docs.duckdevlab.com/seiten/pluesch

## Prio

normal
