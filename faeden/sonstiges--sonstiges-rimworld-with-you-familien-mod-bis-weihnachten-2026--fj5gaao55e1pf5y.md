# Sonstiges · RimWorld With You (Familien-Mod bis Weihnachten 2026)

Projekt `sonstiges` · id `fj5gaao55e1pf5y` · aktualisiert 2026-11-12 12:30 · fällig 2026-11-13

## Stand

12.11.2026, 13:35 (Claude Cloud-Session): Die Entwicklung zieht auf eine lokale Claude-Code-Instanz auf dem Entendrachen um (Umgebung „Local“, Ordner rimworld_with_you_mod), weil Spiel und .NET SDK 8 dort liegen und die Cloud-Session dort keine Shell hat. Übergabe vorbereitet: CLAUDE.md (Ziel, Entscheidungen, Umgebung, erste Aufgabe), docs/konzept.md und .gitignore liegen im Projektordner. Geplant: privates GitHub-Repo baerimbild/rimworld-with-you als Austausch zwischen den Instanzen (legt Max an). Max' Idee vom 12.11.: Arbeit zwischen Instanzen grundsätzlich über GitHub-Repos lösen.

12.11.2026, 12:45 (Claude Cloud-Session): Max bestätigt die Richtung: wahrscheinlich ein Bildschirm; Abhängigkeiten sind ok → RimPsyche (Core + Disposition) und Harmony als Unterbau, Zielversion 1.6. RimPsyche am Quellcode geprüft (Core v1.0.45, Disposition v1.0.21, beide 30.10.2026, nur 1.6, keine Lizenzdatei): Das Modell ist selbst Big Five mit 15 Facetten (−50 bis +50); Facetten per Code setzbar (PsycheDataUtil.InjectPsycheData, SetFacetValue) und über 15 Preset-Slots in Rimpsyche_PsycheDataSlots.xml auch ohne Code; Traits klemmen Facetten (Gates); Gesprächsthemen und Trait-Wirkungen per XML erweiterbar. Folge: Persönlichkeitsschicht nicht selbst bauen; unser Anteil = Fragebogen, Generator (Profil → Defs), kleiner Engine-Mod (feste Pawns, Beziehungen, Szenario), Content-Pack Familie. Konzept v0.1 abgelegt (Bereich rimworld_with_you, Kopie als Projekt-Doc). Einordnung Claude: Der Mehrwert liegt in Datenerhebung und Wiedererkennbarkeit (Skills, Macken, Beziehungen, Insider-Themen), nicht in der Psychometrie.

--- früher ---

12.11.2026: Kickoff. Ziel: RimWorld-Mod, mit der reale Personen als Kolonisten gespielt werden, Charakter möglichst treffend abgebildet; Test zu Weihnachten 2026 mit Dietmar, Petra, Julia, Max, Laura, evtl. auch Hans-Jürgen, Sigrid, Kimberly. Wünsche von Max: Big Five → Traits (bestehende oder neue), Insider, ernste Ente und Plüschtiere im Spiel, Storyteller-Anpassung, abstrakte Engine für andere Gruppen (Kollegen, Freunde). Vor 2 Jahren schon einmal mit Vanilla gespielt.

Recherche 12.11.: (1) RimWorld 1.7 (Waylith-Engine statt Unity) seit 12.10.2026 nur im Unstable-Zweig, Hauptzweig bleibt 1.6, kein Termin für stabil. Laut Ludeon laufen die meisten Mods unverändert, ein inoffizieller Character-Editor-Port brauchte aber UnityStubs und .NET 10. (2) RimPsyche (Autor Maux, Workshop-ID 3535112473, Quellcode auf GitHub) liefert für 1.6 bereits eine Persönlichkeitsschicht mit Facetten, Meinungsbildung aus Persönlichkeit, Modul Disposition für Verhalten; Persönlichkeit ist im Startbildschirm editierbar. (3) Storyteller lässt sich über StorytellerDef (XML) anlegen. (4) 1-2-3 Personalities ist nicht auf 1.6 aktualisiert.

Vorschlag Claude (am 12.11. mittags von Max in den Punkten Bildschirm und Abhängigkeiten bestätigt): Zielversion 1.6. Trennung in Engine-Mod (generisch: Profilformat, Generator Profil → Defs, feste Pawns und Beziehungen beim Spielstart) und Content-Pack Familie (ernste Ente als Storyteller, Plüschtiere, Insider-Texte). Profil = Big Five + Skills/Leidenschaften + verweigerte Arbeit + Macken. Mapping offline im Generator, C# im Spiel minimal. RimPsyche als Laufzeit-Schicht nutzen statt selbst bauen. Kritischer Pfad sind die Daten von 8 Personen: Fragebogen bis Ende November verschicken.

Einordnung Claude: Big Five allein auf Vanilla-Traits ist zu grob (wenige diskrete Schalter pro Pawn); Wiedererkennung kommt aus Skills, Macken, Beziehungen und Texten.

## Offen

Fragebogen: Selbsttest, Fremdeinschätzung oder beides; Länge; deutsche Itemtexte (IPIP-NEO oder BFI-2) prüfen. Wo bauen und testen (RimWorld auf dem Entendrachen?). Persönlichkeitsdrift durch Gespräche: gewollt, abschaltbar? API-Details des Spiels (Start-Pawns, Beziehungen) am dekompilierten Spiel prüfen. Plüsch-Meldeamt als Datenquelle für Plüschtiere? Sprites für Ente und Plüschtiere. Fahrplan: bis 22.11. Profilformat + Fragebogen, bis 6.12. Content-Pack, bis 16.12. Testpartie, danach nur Bugfixes.

## Nächster Schritt

Max: leeres privates Repo baerimbild/rimworld-with-you anlegen und Claude Code lokal im Projektordner starten (Umgebung Local). Lokale Instanz: erste Aufgabe laut CLAUDE.md (Minimal-Mod mit zwei festen Pawns). Offen bei Max: Fragebogen-Zuschnitt (60 Aussagen plus Regler, oder nur Regler).

## Ablage

Konzept: Gedächtnis-Bereich rimworld_with_you (maßgeblich); Kopien: Projekt-Doc claude/konzept.md im claude.ai-Projekt und docs/konzept.md im Projektordner. Code: Entendrachen C:\Users\maxst\Documents\Projekte\rimworld_with_you_mod (CLAUDE.md, docs/, .gitignore; _entmuellen nur vorübergehend). GitHub-Repo baerimbild/rimworld-with-you geplant. Dran ab jetzt: lokale Claude-Code-Instanz auf dem Entendrachen. RimPsyche-Quellen: github.com/jagerguy36/Rimpsyche und Rimpsyche_Disposition.

## Prio

normal

## Aufwand

Claude Cloud-Session, ca. 45 min (Recherche, RimPsyche-Quellcode, Konzept v0.1)
