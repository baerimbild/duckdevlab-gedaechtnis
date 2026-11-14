# Investment Hub · Ansatz, Recherche, Anforderungen (Papa)

Projekt `sonstiges` · id `08ggx3c8blvm9wv` · aktualisiert 2026-11-13 08:49 · fällig 2026-11-16

## Stand

13.11.2026, 09:45 (Claude Code Cloud, claude.ai-Projekt „Investment Hub“): Thema neu angelegt. Max ist bis Mo 16.11. bei seinen Eltern und will dort eine KI-gestützte Informations-App für seinen Vater (Aktien, Gold) bauen. Recherche gemacht: Kein fertiges Produkt deckt das ab (Tracker liefern Zahlen, Open-Source-KI-Analyse deckt Europa nicht ab). Konzept v0 als Vorschlag abgelegt: Briefing statt Dashboard, vServer + bestehende PocketBase, Zahlen nur aus Daten, RTX 5090 als zweites Backend. Interviewleitfaden für den Vater liegt vor. Von Max ist noch nichts davon bestätigt.
NACHTRAG 13.11.2026, 09:50 – Max (09:47): Repo moneymoves ist etwas anderes, ignorieren. IlluminaWS kann er starten, hat dort SSH-Zugang und Claude Code. → Lokale Modelle können schon am Wochenende mitlaufen. Vorschlag Claude dazu (unbestätigt): IlluminaWS als Arbeiter, der sich Rohdaten aus der PocketBase holt und fertige Briefings zurückschreibt (nur ausgehende Verbindungen, kein Tunnel nötig); der Sammler bleibt auf dem vServer. Ist die Kiste aus, schreibt der vServer ersatzweise mit einem Cloud-Modell auf öffentlichen Daten.

## Offen

GEKLÄRT 13.11., 09:47: moneymoves = anderes Thema, ignorieren; IlluminaWS startbar, SSH + Claude Code vorhanden. | NOCH OFFEN: Wann läuft IlluminaWS für die Briefings (hängt an der Standby-Entscheidung, Faden „Studio · Baernetz“)? | Zustellweg (WhatsApp-Link, E-Mail, Startbildschirm) | Cloud-Modell + Budget für den Ersatzweg | Name/Subdomain | Projekt-Zuordnung sonstiges oder studio | Antworten des Vaters aus dem Interview

## Nächster Schritt

Max: Interview mit dem Vater (Leitfaden im Bereich investment_hub_anforderungen bzw. im Projekt-Doc), Titel-Liste und Antworten in den Chat geben; nebenbei IlluminaWS starten und die Kandidaten-Modelle laden. Dann Claude: Beispiel-Briefing von Hand für die echten Titel, Vater streicht an; danach Pipeline v0 bauen (Sa/So). Mo: Übergabe und Stand sichern.

## Ablage

Bereiche: investment_hub (Konzept, Regeln), investment_hub_recherche (Markt, Quellen), investment_hub_anforderungen (Ausgangslage, Leitfaden, später Antworten). Lesefassung: claude.ai-Projekt „Investment Hub“, Doc claude/investment-hub-konzept-v0.md. Instanz am 13.11.: Claude Code Cloud (dieser Chat). Noch kein Repo, noch kein Code.

## Chat

https://claude.ai/code/session_01A7KpPPZ8rWzWaBCSRkmboq

## Prio

normal

## Aufwand

Claude Code Cloud, ca. 30 min (Recherche, Konzept, Ablage)
