# RimWorld With You – Familien-Mod (Konzept, Entscheidungen, Ablage)

`key: rimworld_with_you` · aktualisiert 2026-11-13 11:58 · id `b5g10ual3t7wupl`

## Kurzstand

13.11.2026 (Claude Cloud-Session): Der Fragebogen ist als Webapp live, https://kolonie.duckdevlab.com (Kolonisten-Meldeamt): 60 Aussagen, Fremdeinschätzung, Aussehen mit Vorschau, Foto-Vorschlag gebaut, aber ohne API-Schlüssel noch aus. Daten in PocketBase rwy_*, Export als Profil-YAML ins Pack, die Mod liest die Datenbank nicht. Gruppe „Familie Weihnachten 2026“ angelegt. Die Mod selbst ist seit 12.11. weit gebaut (Engine, Pack Familie, Testrunde gespielt); der laufende Stand steht im Repo in docs/STAND.md, weil stand_schreiben am Faden scheitert: Feld stand fasst 4000 Zeichen, der Faden steht bei 3527. — 12.11.2026, 12:55: RimWorld ist auf dem Entendrachen installiert (Steam, 0,9 GB; laut Platz-Report). Dort kann also gebaut und getestet werden; die Platte ist aber fast voll (7,5 GB frei, Faden 7mx0jh0mt8ey1w8). — 12.11.2026: Konzept v0.1 angelegt. Richtung von Max bestätigt: RimWorld 1.6, wahrscheinlich ein Bildschirm, RimPsyche (Core + Disposition) und Harmony als Unterbau. RimPsyche ist selbst Big Five mit 15 Facetten und lässt sich per Code und per Preset-Datei befüllen; wir bauen Fragebogen, Generator, kleinen Engine-Mod und das Content-Pack Familie. Erster Einsatz Weihnachten 2026. Noch kein Code, noch kein Repo.

## Regeln

KONZEPT v0.1 (12.11.2026, Claude Cloud-Session; Einordnungen von Claude sind als solche markiert)

ZIEL: Reale Personen als RimWorld-Kolonisten, so treffend, dass man sie wiedererkennt. Erster Einsatz: Familienrunde Weihnachten 2026 (5 bis 8 Personen, ein Bildschirm). Engine wiederverwendbar für andere Gruppen; alles Familienspezifische im Content-Pack.

ENTSCHEIDUNGEN (Max, 12.11.2026):
- Zielversion RimWorld 1.6 mit allen DLCs. 1.7 (Waylith-Engine) liegt nur im Unstable-Zweig.
- Wahrscheinlich ein Bildschirm, kein Multiplayer.
- Abhängigkeiten sind ok: RimPsyche (Core und Disposition) und Harmony als Unterbau.

BEFUND RIMPSYCHE (am Quellcode geprüft; Core v1.0.45 und Disposition v1.0.21, beide 30.10.2026, nur 1.6; keine Lizenzdatei im Repo → nur als Abhängigkeit nutzen, keinen Code übernehmen):
- Modell ist Big Five: 5 Domänen × 3 Facetten = 15 Facetten, je −50 bis +50. Offenheit: Imagination, Intellect, Curiosity. Gewissenhaftigkeit: Industriousness, Orderliness, Integrity. Extraversion: Sociability, Assertiveness, Enthusiasm. Verträglichkeit: Compassion, Cooperation, Humbleness. Neurotizismus: Volatility, Pessimism, Insecurity.
- Daraus 35 „Persönlichkeiten“ (z. B. Talkativeness) als gewichtete Summen der Facetten.
- Setzen per Code: PsycheDataUtil.InjectPsycheData(pawn, data, ...), pawn.compPsyche().InjectPsycheData(...), Personality.SetFacetValue(Facet, float).
- Setzen ohne Code: 15 benannte Preset-Slots in Rimpsyche_PsycheDataSlots.xml im Config-Ordner, im Bearbeiten-Fenster ladbar.
- Traits klemmen Facetten in Bereiche („Gates“): Kind → Compassion 0..+50; Industrious/Hard Worker → Industriousness 0..+50; Lazy/Slothful → −50..0; Optimist/Sanguine → Pessimism −50..0; Pessimist/Depressive → 0..+50; Steadfast/Iron-willed → Volatility −50..0; Neurotic → Orderliness 0..+50; Too Smart → Intellect 0..+50; Bloodlust → Compassion −50..0.
- Gesprächsthemen sind XML (InterestDomainDef mit Themen, Kontroversität, Gewichten). Eigene Traits wirken per XML-Patch auf Persönlichkeiten (scopes).
- Disposition koppelt Persönlichkeit an Verhalten: Arbeitstempo, Qualität, Schwelle für Nervenzusammenbrüche, Panik und Flucht, Freizeitvorlieben, Verhandeln; Teile einzeln abschaltbar.
- Persönlichkeit verändert sich durch Gespräche (gegenseitiger Einfluss).
Einordnung Claude: Die Persönlichkeitsschicht müssen wir nicht bauen. Der Projektname „Big 5 personality mod“ beschreibt etwas, das es schon gibt; unser Mehrwert sind Datenerhebung, Mapping und Wiedererkennbarkeit (Skills, Macken, Beziehungen, Insider).

BAUSTEINE:
1. Fragebogen (Web): Facetten, Skills, verweigerte Arbeit, Macken je Person.
2. Profil: eine Datei je Person, spielunabhängig (YAML: id, name, alter, facetten, skills, leidenschaften, verweigert, macken, beziehungen, themen, hintergrund).
3. Generator (Python, außerhalb des Spiels): Profil → XML-Defs; Mapping-Regeln ohne Neukompilieren änderbar.
4. Engine-Mod (C#, klein): liest Personen-Defs, erzeugt beim Start feste Pawns (Name, Aussehen, Hintergrund, Traits, Skills), setzt Beziehungen, übergibt Facetten an RimPsyche; Start-Szenario für die ganze Gruppe.
5. Content-Pack Familie (XML und Bilder): ernste Ente als Storyteller, Plüschtiere, Insider-Themen, Macken.
Rückfallebene ohne C#: Generator schreibt die RimPsyche-Slot-Datei, Pawns von Hand im Startbildschirm.

MAPPING (Entwurf):
- Fragebogen → Facette: Mittelwert m (1..5) → (m − 3) × 25.
- Kontrast: Werte teilweise an der Gruppe zentrieren, damit Unterschiede innerhalb der Familie sichtbar werden; Stärke mit echten Daten einstellen.
- Facette → Vanilla-Trait (höchstens drei, stärkste zuerst): Industriousness ≥ +35 Industrious, ≥ +20 Hard Worker, ≤ −20 Lazy, ≤ −35 Slothful; Pessimism ≥ +35 Depressive, ≥ +20 Pessimist, ≤ −20 Optimist, ≤ −35 Sanguine; Volatility ≥ +35 Volatile, ≥ +20 Nervous, ≤ −20 Steadfast, ≤ −35 Iron-willed; Orderliness ≥ +30 Neurotic; Compassion ≥ +30 Kind; Intellect ≥ +35 Too Smart.
- Gate-Ausgleich: Bei Trait mit Gate den Rohwert zurückrechnen, damit der wirksame Wert dem Profil entspricht.
- Macken → Vanilla-Traits (Night Owl, Gourmand, Ascetic, Undergrounder, Body Purist, Transhumanist, Jogger, Quick Sleeper) oder eigene Traits.
- Verweigerte Arbeit → eigene BackstoryDef je Person mit gesperrten Arbeitstypen.

FRAGEBOGEN (Entwurf, Quellen noch zu prüfen):
- Selbsttest 60 Aussagen, 4 je Facette, ca. 10 min. Kandidat IPIP-NEO-Items (gemeinfrei; Facetten passen fast 1:1). Alternative BFI-2 deutsch (60 Items, 15 Facetten, 12 passen direkt).
- Fremdeinschätzung: 15 Schieberegler mit den Polen aus RimPsyche, ca. 2 min je Person.
- RimWorld-Teil: Skills mit Alltagsankern, Leidenschaften, verweigerte Arbeit, Macken, drei Insider als Freitext.

CONTENT-PACK (Haken): Ernste Ente als Storyteller (StorytellerDef, XML): dichte, eher soziale Ereignisse in den ersten Tagen, mildere Überfälle wegen 8 Start-Kolonisten. Insider als Gesprächsthemen mit hoher Kontroversität. Plüschtiere als Gegenstände oder Tiere, Datenquelle evtl. Plüsch-Meldeamt.

FAHRPLAN: bis 13.11. Minimal-Mod mit zwei festen Pawns (braucht installiertes Spiel) · bis 22.11. Profilformat, Fragebogen, Mapping v1, Fragebogen an die Familie · bis 6.12. Content-Pack · bis 16.12. Testpartie, danach nur Bugfixes.

OFFEN: RimWorld auf dem Entendrachen installiert? Wo bauen und testen? · Selbsttest, Fremdeinschätzung oder beides; Länge · Soll sich Persönlichkeit im Spiel verändern dürfen, abschaltbar? · API-Details (Start-Pawns, Beziehungen) am dekompilierten Spiel prüfen · Sprites · Falls 1.7 vor Weihnachten stabil wird: voraussichtlich per Steam-Zweig auf 1.6 bleiben.

## Ablage

Maßgeblich: dieser Bereich. Kopie: claude.ai-Projekt „rimworld with you / big 5 personality mod“, Projekt-Doc claude/konzept.md. Code (noch leer, kein Repo): Entendrachen C:\Users\maxst\Documents\Projekte\rimworld_with_you_mod. Faden: fj5gaao55e1pf5y. Verwandt: Faden 7mx0jh0mt8ey1w8 (Entendrachen entmüllen), Faden ybeano97rjxld31 (Plüsch-Meldeamt). | Seit 12./13.11.2026: Code im Repo baerimbild/baerimbild-rimworld-with-you (privat, main), laufender Stand dort in docs/STAND.md, Beschreibung in CLAUDE.md. Webapp: Ordner webapp/ im Repo, Klon auf dem vServer /opt/ops/src/rimworld-with-you, Server-Doku dienste/kolonie.md.

## Links

https://github.com/jagerguy36/Rimpsyche | https://github.com/jagerguy36/Rimpsyche_Disposition | https://github.com/jagerguy36/Rimpsyche/wiki/For-Modders | https://steamcommunity.com/sharedfiles/filedetails/?id=3535112473 | https://ludeon.com | https://kolonie.duckdevlab.com | https://github.com/baerimbild/baerimbild-rimworld-with-you
