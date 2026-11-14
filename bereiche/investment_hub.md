# Investment Hub (Anlage-Briefing für Max' Vater) · Konzept, Architektur, Entscheidungen

`key: investment_hub` · aktualisiert 2026-11-13 08:49 · id `7curnkmjzz3h6en`

## Kurzstand

ANGELEGT 13.11.2026, 09:45 – Quelle: Chat im claude.ai-Projekt „Investment Hub“ (Claude Code Cloud). Status: Vorschlag Claude, von Max NICHT bestätigt.
Max (13.11., 09:35): Will bis Mo 16.11. bei seinen Eltern eine KI-gestützte, auf seinen Vater zugeschnittene Informations-App für Aktien und Wertanlage (z. B. Gold) bauen. Nichts Hochtrabendes, aber ein Schritt über „Google-Suche mit Gemini-Ergebnissen“ hinaus. Läuft auf Max' Infrastruktur, von Max wartbar; der Vater sieht nur eine einfache Oberfläche. Wunsch: RTX 5090 + lokale Modelle bereiten regelmäßige Reports auf, Cloud-Modelle dürfen ergänzen. Perspektivisch auch für Max' eigene Investitionen. Order-Anbindung für den Vater nicht nötig, für Max später schon.
ZIELBILD (Claude): Regelmäßiges deutsches Briefing zu genau seinen Titeln und Themen, mit Quellen; der Vater entscheidet und ordert selbst. Mehrwert gegenüber Google+Gemini: (1) kennt seine Titel und die Vorwoche, (2) kommt von selbst, (3) jede Aussage mit Quelle, Zahlen aus Daten, (4) kein Werbe-/SEO-Müll, festes Format.
ARCHITEKTUR v0 (Claude):
- Ort: vServer (öffentlich, immer an; der Vater ist nicht im Heimnetz). Eigene Subdomain, Login wie pluesch (PocketBase-Nutzer).
- Daten: bestehende PocketBase, Collections mit Präfix invest_ (titel, quellen, rohdaten, berichte, rueckmeldungen).
- Sammler: Python per Cron auf dem vServer – Kurse/Kennzahlen, Nachrichten (RSS/Suche), Termine. Start mit kostenlosen Quellen; Ausweichquelle EODHD (offizieller Deutsche-Börse-Datenvertrieb, ab 19,99 $/Monat).
- Schreiber: ein Modellaufruf pro Titel (filtern, zusammenfassen, übersetzen) + einer fürs Gesamtbriefing. Das Modell hängt an EINER OpenAI-kompatiblen Adresse in der Konfiguration: jetzt Cloud, später Ollama auf IlluminaWS.
- Ausgabe: ruhige Seite (Heute / Diese Woche / Archiv), große Schrift, druckbar; Link per WhatsApp oder Symbol auf dem Startbildschirm.
- RTX 5090: Fleißarbeit und alles mit Depotbezug; Kandidaten Qwen3.8 27B, Gemma 4 (27–31B), an deutschen Texten testen. Im Wochenend-Stand zweites Backend, kein Pflichtteil (IlluminaWS nur im LAN, Standby-Frage offen, Max nicht in Randau).
WOCHENENDPLAN: Fr vormittags Interview (Leitfaden: investment_hub_anforderungen); Fr nachmittags Beispiel-Briefing von Hand für seine echten Titel, der Vater streicht an (= Spezifikation); Sa Pipeline v0; So Cron + zweite Runde; Mo Übergabe + Stand sichern. Bewusst NICHT am Wochenende: Rückfrage-Chat, Charts, Depot-Performance, Order-Anbindung, lokale Modelle als Pflicht.
OFFEN: IlluminaWS an und im Tailnet? | Repo moneymoves (im Register, ungeprüft) = Vorarbeit? | Zustellweg | Cloud-Modell + Budget | Name/Subdomain | Projekt-Zuordnung sonstiges oder studio.
Claude-Kommentar (09:45): Das Produkt ist das Briefing, nicht das Dashboard. Ein Mittsiebziger mit gutem Urteil braucht keine Wand aus Charts, sondern einen verlässlichen, gut redigierten Text, dem er trauen kann. Der Engpass dafür ist Datenqualität und Quellenangabe, nicht Modellgröße. Für den Vater ist die 5090 nicht nötig; sinnvoll ist sie für Max' Ziele (lokal, anbieterunabhängig, Depotdaten privat). Größtes Risiko am Wochenende: zu viel bauen, bevor der Vater ein Beispiel gesehen hat.
NACHTRAG 13.11.2026, 09:50 – Max (09:47): moneymoves ignorieren (anderes Thema). IlluminaWS startbar, SSH + Claude Code vorhanden. Vorschlag Claude (unbestätigt): Schreiber von Anfang an lokal auf IlluminaWS als Arbeiter (holt Rohdaten aus der PocketBase, schreibt Briefings zurück, nur ausgehend); Sammler bleibt auf dem vServer; ist die Kiste aus, schreibt der vServer ersatzweise per Cloud-Modell.

## Regeln

Gestaltungsregeln (Vorschlag Claude, 13.11.2026, von Max noch nicht bestätigt):
1. Zahlen kommen nie aus dem Modell. Kurse, Kennzahlen und Termine liefert der Sammler; das Modell bekommt sie als Eingabe und schreibt nur Text. Ein Prüfschritt vergleicht die Zahlen im Text mit den Eingabedaten.
2. Jede Aussage trägt ihre Quelle (Link). Ohne Quelle fliegt sie raus.
3. Keine Kauf-/Verkaufs-Ampel. Das Briefing sagt, was passiert ist, was es für seine Titel heißt und was ansteht. Die Entscheidung bleibt beim Vater.
4. Positionsgrößen bleiben lokal: Stückzahlen und Depotwerte gehen nicht an Cloud-Modelle; die Cloud sieht nur öffentliche Informationen zu Tickern.
5. Kein neues Werkzeug (Regel 7 in allgemein): vServer, PocketBase, Deploy-Weg wie pluesch. Ghostfolio erst, wenn Max für sich selbst Performance-Tracking will.

## Ablage

Lesefassung: claude.ai-Projekt „Investment Hub“, Doc claude/investment-hub-konzept-v0.md (13.11.2026). Recherche + Quellen: Bereich investment_hub_recherche. Ausgangslage + Interviewleitfaden + Antworten: Bereich investment_hub_anforderungen. Code/Repo: noch keins.

## Links

Faden 08ggx3c8blvm9wv | Chat https://claude.ai/code/session_01A7KpPPZ8rWzWaBCSRkmboq
