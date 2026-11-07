# Studio · Lebendige Infrastruktur-Anzeige (Baum auf dem Monitor)

Projekt `studio` · id `kf4yao3yd9ahn1z` · aktualisiert 2026-11-06 20:54

## Stand

06.11.2026 21:54, Ergänzung Max: Endausbau irgendwann physisch – Baum/Schaltkreis aus Acryl mit LEDs über dem Schreibtisch. Claudes Einordnung: dritte Darstellung derselben Quelle; adressierbare LED-Streifen (WS2812) an einem ESP32 mit WLED, Ereignisse per MQTT/HTTP vom Sammler auf wombat, Adern = Lichtleiter in gravierter Acrylplatte. Werkzeuge dafür hat Max (3D-Druck, ESP32/M5Stick aus dem Smart-Garden-Projekt).

06.11.2026 21:52, Ergänzung Max: Hybrid aus Schaltkreis und Baum – verschiedene Farben, die durch die Adern laufen (Farbe = Art der Aktivität, Fluss = Datenweg). Zwei Fassungen: (1) sehr stilisierte, schlichte Web-Variante; (2) „Elden-Ring-Erdenbaum“-mäßige Game-Variante. Beide aus derselben Quelle (Ereignisstrom + Topologie-JSON), Web-Variante als erste Stufe im Werkbank-Panel, Game-Variante später in Godot mit Shadern.

06.11.2026 21:50, Idee von Max (geparkt): Stilisierte Visualisierung der Infrastruktur auf einem Monitor – wachsender Baum, wehende Blätter –, die zeigt, wenn Claude etwas macht. Datenquellen existieren: Server-MCP-Log befehle.jsonl, Gedächtnis-Export/PocketBase updated, Backup-Log, Tailscale-Status, Docker-Events, GitHub-Webhooks, später Werkbank-Registry. Sammler auf wombat bündelt zu einem Ereignisstrom; Anzeige-Modus des Werkbank-Panels.

## Offen

Welcher Monitor/wo, Mapping Ereignis → Farbe/Bewegung (kleine Tabelle), Abgrenzung zum Werkbank-Panel, Reihenfolge Web zuerst oder parallel. Physische Fassung ganz zum Schluss.

## Nächster Schritt

Erst, wenn Max es aufruft. Dann: Ereignisstrom + Topologie-JSON auf wombat als gemeinsame Grundlage, Web-Variante als erste Stufe.

## Ablage

noch nichts; Bezug: Faden Baernetz (Werkbank-Panel), Repo baerimbild/werkbank (Registry), Smart Garden (ESP32-Erfahrung)

## Chat

frühstück mit opus / IlluminaWS-Setup (Okt 2026)

## Prio

geparkt
