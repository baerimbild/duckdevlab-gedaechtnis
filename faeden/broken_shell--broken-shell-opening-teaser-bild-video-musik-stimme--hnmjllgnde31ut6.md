# Broken Shell · Opening-Teaser (Bild, Video, Musik, Stimme)

Projekt `broken_shell` · id `hnmjllgnde31ut6` · aktualisiert 2026-11-20 09:04

## Stand

20.11.2026 (Max): Hängt am PC-Setup in Randau; der Wanddurchbruch ist erfolgt, das Setup wird gerade abgeschlossen. Danach wieder dran (Vertonung / Trailer), aber nachrangig hinter Wandering Shell.
— 26./27.10.: Teaser v1 (17,7 s) und v2 (29 s) komplett lokal: Standbilder Z-Image Turbo über ComfyUI-API (gen.py), Clips Wan 2.2 i2v (i2v.py), Schnitt ffmpeg mit ACE-Step-Track + TTS → E:\Studio\Ausgaben\video\broken_shell_teaser_v1/v2.mp4. Melodie „Abendlied am Waldrand“ (abendlied_73) gesetzt, MIDI für Julia in E:\Studio\Ausgaben\audio. Sätze gekürzt (opening.gd + GDD). Stimme e: Qwen3-TTS, e_v12c_referenz „sehr brauchbar“ → e_REFERENZ_v1.wav in E:\Studio\Ausgaben\audio\stimme_e; ab jetzt nur noch klonen. v2: 5 Standbilder (e konsistent: kahl, Brille, Ledermantel, Hut; Kind Silhouette), Shot 0 ffmpeg-Schwenk, 4 Clips, Ton mit Ausatmen, Wind-Bett, Titel + „der letzte mensch“.
— 06.11.: GDD, opening.gd, Prototyp lagen nur im flüchtigen Chat-Container → behoben; alles dauerhaft im Repo baerimbild/broken-shell (Commit 9c01e32, Klon /opt/ops/src/broken-shell), Bereich broken_shell_spiel.

## Offen

Shot 0 Himmel flacher als der Rest (v3: HiDream). Kind-Charakterblatt fehlt weiterhin. ComfyUI --output-directory greift nicht. 09_video.ps1 (offizielle i2v-LoRAs) nicht gelaufen. Repo broken-shell auf IlluminaWS klonen (E:\Studio\Projekte\broken-shell), Zip von 06.11. damit obsolet.

## Nächster Schritt

Sobald IlluminaWS in Randau steht: Max' Rückmeldung zu v2 (Palette, Bewegungsmenge, e), dann Charakterblätter (e, Kind), ggf. HiDream für Shot 0, Pipeline als Skript. Arbeit im Repo broken-shell.

## Ablage

Repo baerimbild/broken-shell (Quelle der Wahrheit für Dateien, seit 06.11.); Bereich broken_shell_spiel (Konzept, Figurenblatt e, Ablage-Liste); Projektdoku „frühstück mit opus“ broken_shell/ (GDD, opening.gd – Kopien). Medien: E:\Studio\Ausgaben\{bilder,video,audio,tests}; E:\Data\Images\Text2Img\broken_shell\teaser (Standbilder), ...\video\broken_shell_teaser (Clips); Skripte E:\Studio\Tools\setup\07-15, E:\Studio\Tools\comfy (+api).

## Chat

frühstück mit opus / IlluminaWS-Setup (Okt 2026)

## Prio

normal
