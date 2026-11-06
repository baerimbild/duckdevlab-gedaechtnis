# Studio · Crafting Apps (PhotoCraft & Co.) – Einordnung Werkbank

Projekt `studio` · id `wupu64r7zaoyhvv` · aktualisiert 2026-11-03 07:12 · fällig 2026-11-10

## Stand

02.11.2026: Max meinte die Crafting Apps (nicht das ArtCraft-KI-Studio). Einordnung: 3 Betriebsarten. (1) Desktop nativ auf IlluminaWS (MSI) + Surface – zum Arbeiten. (2) Web-Build = statisches ZIP (photocraft-web-<ver>.zip), läuft komplett im Browser → passt direkt in Sites-Panel/Caddy (/opt/sites), kein Docker nötig; nur bei konkretem Anlass (Julia/Laura, Workshops). (3) photocraft-cli (run/batch/mcp) als Werkbank-Dienst in WSL auf IlluminaWS bzw. aarch64-Build auf wombat – Kandidat für Asset-Pipeline (PSD→PNG, Nachbearbeitung ComfyUI-Ausgaben). Early alpha, sehr schnelle Releases → Versionen pinnen, PSD als Austauschformat behalten.

## Offen

Testen: Kann photocraft-cli Ebenen einzeln exportieren (PSD → Einzel-PNGs für Godot-Cutout-Rig)? MCP-Transport (stdio?) mit Claude Code in WSL. Web-Build: Browser-Anforderungen, Update-Automatik (Release-Check → /opt/sites).

## Nächster Schritt

Max: PhotoCraft per MSI/Launcher auf IlluminaWS installieren und mit einer echten PSD testen; danach CLI in WSL + MCP an Claude Code hängen.

## Chat

loser Chat 02.11.2026 „ArtCraft + Tech-Stack“ → weiter in frühstück mit opus

## Prio

normal
