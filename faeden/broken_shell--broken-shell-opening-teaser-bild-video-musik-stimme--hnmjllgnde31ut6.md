# Broken Shell · Opening-Teaser (Bild, Video, Musik, Stimme)

Projekt `broken_shell` · id `hnmjllgnde31ut6` · aktualisiert 2026-11-06 19:48 · fällig 2026-11-09

## Stand

26./27.10.: Erster Teaser v1 (17,7 s) komplett lokal: 3 Standbilder Z-Image Turbo ueber ComfyUI-API (gen.py), 3 Clips Wan 2.2 i2v 4-Schritt (i2v.py), Schnitt ffmpeg mit ACE-Step-Track + TTS -> E:\Studio\Ausgaben\video\broken_shell_teaser_v1.mp4. ComfyUI erreichbar unter http://192.168.1.121:8188 (--listen 0.0.0.0); Skripte im Geraete-VM unter ~/comfy (gen.py, i2v.py, poll.py). Melodie 'Abendlied am Waldrand' als MIDI geschrieben (E:\Studio\Tools\setup\abendlied.py), gerendert; Max: 'abendlied_73 ist richtig gut' -> Melodie gesetzt, MIDI fuer Julia in E:\Studio\Ausgaben\audio. Saetze gekuerzt (opening.gd + GDD): 'Heb sie gut auf.' / [Ausatmen] '... ein schoener Abend ...' / 'Lass uns zurueckgehen. Wir kommen sonst noch zu spaet ...'. Stimme e: Qwen3-TTS VoiceDesign-Referenz + Base-Klon (Skripte 11-15 in Tools\setup); Richtung 'Greis' ok, Max will: spitz, hell, kristallin, kraechzt statt schreit, wuerde nie schreien; v10 klang gespielt-alt, v11 fehlte 'Mann'; v12 = 90 Jahre + Buehnendeutsch der 30er/40er + alte-Aufnahme-Klang. Max 27.10. 00:52: e_v12c_referenz 'sehr brauchbar' -> als e_REFERENZ_v1.wav (+ .txt mit Beschreibung/ref_text) in E:\Studio\Ausgaben\audio\stimme_e festgelegt; ab jetzt nur noch klonen. 27.10. 01:15: Teaser v2 (29 s) fertig: E:\Studio\Ausgaben\video\broken_shell_teaser_v2.mp4. 5 Standbilder Z-Image (teaser2/, e konsistent: kahl, Brille, Ledermantel, Hut; Kind Silhouette), Shot 0 als ffmpeg-Schwenk ueber Hochformatbild, 4 Clips Wan 2.2 i2v, Ton: abendlied_73 (Phrase A, endet natuerlich bei 10,4 s), e_v12c-Saetze einzeln geschnitten (satz1-3), Ausatmen aus gefiltertem Rauschen, Wind-Bett, Titel + 'der letzte mensch'. Kontaktbogen und Stills daneben. | 06.11. 20:50: Max meldet, eine andere Instanz findet Spielkonzept und e-Setzungen nicht – Ursache: GDD, opening.gd und Prototyp lagen nur im flüchtigen Chat-Container. Behoben: GDD + opening.gd in die Projektdoku (broken_shell/), Konzept + Figurenblatt e als Bereich broken_shell_spiel, Prototyp als Zip an Max.

## Offen

Shot 0 Himmel flacher als der Rest (v3: HiDream). Kind-Charakterblatt fehlt weiterhin. ComfyUI --output-directory greift nicht. 09_video.ps1 (offizielle i2v-LoRAs) nicht gelaufen. NEU 06.11.: GitHub-Repo baerimbild/broken-shell anlegen (Lore, GDD, Prototyp) – derzeit nur Projektdoku + Zip.

## Nächster Schritt

Max' Rueckmeldung zu v2 (Palette, Bewegungsmenge, e). Dann Charakterblaetter (e, Kind) als feste Referenzen, ggf. HiDream fuer Shot 0, und die Pipeline als wiederverwendbares Skript (Shotlist -> Stills -> Clips -> Schnitt). Zip nach E:\Studio\Projekte\broken-shell entpacken und Repo anlegen.

## Ablage

06.11. ergänzt: GDD + opening.gd dauerhaft in der Projektdoku von „frühstück mit opus“ (broken_shell/Broken_Shell_Spiel_GDD.md, broken_shell/opening.gd.md); Konzept + Figurenblatt e im Bereich broken_shell_spiel; Godot-Prototyp als Zip an Max (Ziel E:\Studio\Projekte\broken-shell). Vorher: E:\Studio\Ausgaben\{bilder,video,audio,tests}; E:\Data\Images\Text2Img\broken_shell\teaser (Standbilder), ...\video\broken_shell_teaser (Clips); Skripte E:\Studio\Tools\setup\07-15, E:\Studio\Tools\comfy (+api). Hinweis: /mnt/user-data/outputs im Chat-Container ist flüchtig und für andere Instanzen unsichtbar.

## Chat

frühstück mit opus / IlluminaWS-Setup (Okt 2026)

## Prio

normal
