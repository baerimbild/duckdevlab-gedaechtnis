# Sonstiges · Randauer Wohnung: PC im Abstellraum + Kabeldurchbruch

Projekt `sonstiges` · id `fq3kz34qnpaf9nj` · aktualisiert 2026-11-04 21:00

## Stand

04.11.2026: Illumina kommt in den Abstellraum neben dem Arbeitszimmer, Schreibtisch direkt daneben. Durchbruch durch zweischalige Innenwand (Luftspalt, vermutlich nicht tragend); Pilotloch durch beide Schalen ist gebohrt. Tisch an der Beton-Außenwand ist per Stützbein gelöst. Klärung mit der Hausverwaltung zum Durchbruch laut Max erledigt.
22:00: ALLES BESTELLT (Lieferung nach Leipzig, wird nach Randau mitgenommen).
Bohrplan: rundes Loch, kein Langloch. Pro Schale von beiden Seiten mit dem UniversalDrill stufenweise 8 → 12 → 16 (Bosch EXPERT HEX-9 MultiConstruction), dann auf ca. 18 mm aufweiten (Bohrer kreisen lassen oder Rundfeile/Steinraspel). Vorher 18er-Kreis per gedruckter Anzeichenscheibe mit Zentrierzapfen (passend zum aktuellen Vorbohrloch, z. B. 8 mm) mit Bleistift anzeichnen und bis zur Linie aufweiten. Engpass: zweiter Mini-DP-Stecker (11,6×9,2 mm) neben dem ersten 5,5-mm-Kabel, theoretisches Minimum ca. 17 mm; am Ende mit echtem Stecker oder gedrucktem Querschnitt-Dummy durch beide Schalen testen (Loch kann nach innen konisch enger werden). Durchzug-Reihenfolge: erst beide Mini-DP, dann USB-C.
Kabel: RTX-DP-Ausgang → VMOJO-Adapter (DP-Stecker → Mini-DP-Buchse, DP 1.4, 2er-Pack) → KabelDirekt Mini-DP→DP 3 m (2er-Set, 4K@60, Kabel 5,5 mm) → DP-Ende direkt in den Monitor. Hub: TP-Link UH720 (7× USB-A 5 Gbit/s + 2 Ladeports, 12 V/4 A Netzteil, Eingang USB 3.0 Micro-B). Kabel PC→Hub: deleyCON USB-C auf USB 3.0 Micro-B 2 m, 5 Gbit/s (Nylon, 6 mm, C-Stecker 12 mm breit). Alle kleinen Enden vom Schreibtisch Richtung Abstellraum durchschieben.
Werkzeug: EXPERT HEX-9 MultiConstruction 7-tlg. (4–12) + HEX-9 16×150; für die EasySaw 18V-70: Stichsägeblatt-Set Wood and Metal 10-tlg. (2 607 011 170) + T 308 B.

## Offen

Lüftung Abstellraum (PC 700–850 W Abwärme: Zuluft unten, Abluft oben Richtung Flur); runde Kabelblende für ca. 18 mm selbst drucken (PLA/PETG-Rahmen + TPU-Lamellen, OpenSCAD-Modell angeboten); Halterung für den UH720 unter der Tischplatte (3D-Druck).

## Nächster Schritt

In Randau: Bildkette testen (PC → VMOJO → KabelDirekt → Monitor, 3840×2160 bei 60 Hz), dann Loch auf ca. 18 mm aufweiten und Kabel durchziehen.

## Prio

normal
