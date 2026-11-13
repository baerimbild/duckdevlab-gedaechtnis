# Studio · Entendrachen entmüllen (Platz schaffen)

Projekt `studio` · id `7mx0jh0mt8ey1w8` · aktualisiert 2026-11-12 12:08 · fällig 2026-11-16

## Stand

12.11.2026, 13:10 (Claude Cloud-Session): Versuch über die Computer-Steuerung (Windows-Einstellungen) abgebrochen, nichts gelöscht: Das Fenster kam nur als graue Fläche an, Max' andere Fenster wurden ausgeblendet. Max will das nicht und bevorzugt Shell und Skripte (Regel 13 in „allgemein“). Max hat fünf Posten zum Löschen freigegeben: Arduino-Download-Cache (Arduino15\staging), Rest-Datei in .u2net, doppelte Installer (xTool, Bambu), reachy_env im Drive-Ordner, Obsidian-Backups bis auf die zwei neuesten. Dafür liegt entmuellen-1.ps1 im Ordner _entmuellen: zeigt die Liste mit Größen, fragt einmal nach, löscht endgültig, leert den Papierkorb, schreibt entmuellen-log.txt. Nicht testgelaufen.

12.11.2026, 12:55 (Claude Cloud-Session): Platz-Report ist gelaufen (123 s, Datei platz-report.txt). C: 237,1 GB gesamt, 229,6 belegt, 7,5 frei. Größte Posten: Benutzerordner 88,3 GB (darin Google-Drive-Spiegel „Meine Ablage (Konto)“ 29,0 GB plus ein zweiter Ordner „Meine Ablage“ 1,5 GB; AppData 46,7 GB, darin Arduino15 7,8 GB), Program Files 79 GB (Steam 24,1 GB, davon Farthest Frontier 11,6; WindowsApps 16,5; JetBrains 6,6), Papierkorb 7,1 GB (vor allem acht alte Obsidian-Backups zu je 0,76 GB), Windows-Update-Reste 6,4 + 2,1 GB, Ruhezustandsdatei 6,3 GB, NVIDIA-Daten zusammen ca. 6,8 GB (davon 3,7 GB heruntergeladene Treiberpakete), Ubisoft ca. 4,6 GB, Battle.net/WoW ca. 4,4 GB, Overwolf ca. 2,1 GB, reachy_env (Python-Umgebung im Drive-Ordner) 2,8 GB, BrainDeadBackgroundRemover-Zip 2,1 GB. RimWorld ist installiert (0,9 GB, Steam). Vorschlag Claude: Stufe 1 ohne Verlust (Papierkorb, Windows-Bereinigung) bringt etwa 12 bis 15 GB; größte Entscheidung ist Google Drive von Spiegeln auf Streamen (bis 29 GB), vorher klären, warum es zwei Drive-Ordner gibt. Einordnung Claude: Auffällig sind die Obsidian-Backups ohne Rotation (0,77 GB je Zip, etwa wöchentlich), die im Drive landen; das gehört auch zur Grundbereinigung im Struktur-Audit.

--- früher ---

12.11.2026 (Claude Cloud-Session, Chat „RimWorld With You“): Max möchte den Entendrachen (Surface Pro 9) grob entmüllen, damit wieder Platz ist; Berechtigungen will er geben. Stand der Zugänge: Die Cloud-Session hat auf dem Entendrachen nur Datei-Tools (auflisten, holen, zurückschreiben), keine Shell; Terminals sind per Computer-Steuerung nicht tippbar. Der Freigabe-Dialog für den Benutzerordner C:\Users\maxst ließ sich nicht anzeigen, weil das Fenster der Claude-Desktop-App auf dem Gerät nicht offen war. Deshalb: reines Lese-Skript platz-report.ps1 abgelegt (löscht nichts; misst Benutzerordner bis Ebene 3, Program Files, ProgramData, Windows-Sonderposten, größte Dateien ab 300 MB, Steam-Spiele inkl. Prüfung, ob RimWorld installiert ist, installierte Programme laut Registry; Cloud-Platzhalter zählen nicht mit). Skript ist nicht testgelaufen (kein PowerShell in der Cloud-Umgebung), nur von Hand geprüft.

## Offen

Zwei Drive-Ordner im Benutzerordner klären, bevor auf Streamen umgestellt wird. Hängt am Surface eine NVIDIA-Karte (eGPU)? Sonst kann die NVIDIA App ganz weg. JetBrains: liegen alte IDE-Versionen herum? Ruhezustand abschalten nur, wenn Max darauf verzichten will. Ordner _entmuellen liegt vorübergehend im RimWorld-Projektordner und soll nach dem Aufräumen weg.

## Nächster Schritt

Max: entmuellen-1.ps1 starten (Einzeiler steht im Chat), danach neu starten und die Windows-Bereinigung über Einstellungen → System → Speicher machen. Dann entscheiden: Google Drive auf Streamen, Farthest Frontier, Launcher (Ubisoft, Battle.net/WoW, Overwolf), NVIDIA App, JetBrains. Außerdem Terminal-Zugriff für Claude auf dem Entendrachen einrichten (Empfehlung: Claude Code lokal).

## Ablage

Entendrachen: C:\Users\maxst\Documents\Projekte\rimworld_with_you_mod\_entmuellen\ (platz-report.ps1, später platz-report.txt). Dran: Claude Cloud-Session vom 12.11.2026.

## Prio

normal
