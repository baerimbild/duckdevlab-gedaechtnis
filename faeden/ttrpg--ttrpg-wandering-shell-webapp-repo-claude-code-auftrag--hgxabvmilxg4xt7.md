# TTRPG · Wandering Shell Webapp (Repo + Claude-Code-Auftrag)

Projekt `ttrpg` · id `hgxabvmilxg4xt7` · aktualisiert 2026-11-21 10:05 · fällig 2026-11-22

## Stand

21.11.2026, 11:05 (Cloud, Connector Server): Max' Korrekturen (keine Bindung Einträge↔Felder; Module dürfen eigenes Set mitbringen) eingearbeitet. Schritt 1 gebaut und gepusht: Branch `weltmodul` (Commit 8aa0359) mit WELTMODUL.md, Migration 1763700000_ws_welten.js (ws_welten, ws_eintraege, ws_eintraege_sl, ws_wissen, ws_runden.welt, Übernahme bestehender Runden), Hook „Runde anlegen“ legt oder wählt Welt, 9 neue Hook-Tests; alle 39 Hook-Tests und 40 Engine-Tests grün (Tests laufen auf dem Server in node:22-alpine per Docker, der Server hat kein Node). Worktree /opt/ops/src/wandering-shell-dev, Live-Klon unberührt. Außerdem: Max hat mit Gemini die „Weltbibel: Der Schwellenpunkt“ als ersten Modul-Prototyp eingebracht (Bereich wandering_shell_modul_schwellenpunkt), Claude hat sie kritisch gelesen, Rückmeldung im Chat.
— 21.11.2026 früh: Bestandsaufnahme; Max' Richtung fürs Weltmodul (Inhaltspaket, gleiche Struktur, One-Shot-Prämisse, Figuren-/Bürgerwissen). Konzept im Bereich wandering_shell_weltmodul.
— 20.11.2026 (Max): Fokus Wandering Shell, Weltmodul + Refactor, Arbeit im Dialog.
— 04.11.2026: Mail mit Link + ANLEITUNG.md an Jessi ist raus (Max).

## Offen

Echte Handys nicht getestet; Stufe 2 (Musik synchron, Tonaufnahme, PDF-Export).

## Nächster Schritt

Max: Rückmeldung zur Weltbibel-Kritik und ggf. Branch weltmodul ansehen (kein PR angelegt, Max sagt wann). Claude: Schritt 2 (Hooks: Saat → Einträge, Freigeben, „weiß jetzt“, Export), dann SL-Reiter zerlegen und Spieler-Weltseite; parallel Schwellenpunkt als module/schwellenpunkt aufbereiten (Tafel aus Matrix/Schwächen, Set-Motive, Wortbank aus Archetypen, Gegend je Hook).

## Ablage

github.com/baerimbild/wandering-shell, Branch weltmodul (Schritt 1), PRs #1–#3 gemerged; Live-Klon /opt/ops/src/wandering-shell, Dev-Worktree /opt/ops/src/wandering-shell-dev (Tests: docker run --rm -v $PWD:/app -w /app node:22-alpine sh -c "npm ci && npm test && npm run test:hooks"). Konzept: Bereich wandering_shell_weltmodul; Modul-Prototyp: Bereich wandering_shell_modul_schwellenpunkt. Dran: Claude Cloud über Connector Server.

## Chat

https://claude.ai/code/session_01A7KpPQqKicTCivomfo5fdY

## Prio

normal

## Aufwand

Claude Cloud, 21.11.: ca. 1,5 h (Konzept, Migration, Tests, Weltbibel lesen)
