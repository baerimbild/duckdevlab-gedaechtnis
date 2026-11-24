# Luanti-Dialoge: Rollen und Gruppen (Variante A)

Projekt `historycraft` · id `ivljb46sdc292fo` · aktualisiert 2026-11-24 10:17

## Stand

24.11.2026: Variante A gebaut, noch nicht gemerged/deployt. API (Branch rollen-gruppen, 75a1912): Rolle je Server-Recht admin/mitglied, Gruppen = Kennungspräfix (brunnen → brunnen_*.json, audio/brunnen_*.ogg), Prüfung bei check/publish, gefilterte Dateiliste, GET /v1/servers/<name>/files/<datei>, DELETE fremder Dateien 403, /v1/me mit role/groups, CLI group add/remove/list, user add --rolle --gruppe, join/leave, grant --rolle; alte DB bekommt Spalte role automatisch (bestehende Rechte = admin). 55 pytest grün. Editor (Branch claude/magical-tesla-45cj1h, 1303406): Knopf „Vom Ziel holen…“ (API und Ordner, neue Dateien dazu, abweichende nur nach Rückfrage), Rollen-Hinweis nach Login, role/groups im Ziel gespeichert; 51 Headless-Tests und E2E mit Mitglied clara grün. Doku: API-README, editor-schnittstelle.md, redaktion.md, admin.md, CLAUDE.md.

## Offen

Thomas' Token-Korrektur auf dem Akademie-Server; Skins über Editor-ZIP/API; Tobias' Entscheidung.

## Nächster Schritt

Auf Max' „PR und merge“ warten (beide Repos), danach API auf dem vServer deployen (/opt/dialoge-api: compose build + up; Migration läuft beim Start), Gruppe und Mitglieds-Konten nach Bedarf anlegen; Editor 0.1.3 bauen und auf die Download-Seite legen.

## Ablage

Server: /root/beispieldialoge-vertont-2026-11-23.zip, /root/vertonung-einspielen.sh; Download-Seite dialoge-editor.duckdevlab.com; Ops-Doku dienste/luanti-dialoge.md „Vertonte Beispiele“

## Prio

normal

## Aufwand

Claude Code Cloud, ca. 1,5 h
