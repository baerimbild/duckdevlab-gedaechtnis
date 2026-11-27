# Magic · Charakterdecks Max & Julia + Plüsch-Commander (Custom)

`key: magic_charakterdecks` · aktualisiert 2026-11-26 23:49 · id `okn70gj9dgytjml`

## Kurzstand

26.11.2026 (Claude, Entwurf, noch nicht von Max/Julia abgenommen): Zwei Charakter-Commander-Decks aus dem losen Bestand als Entwurf in der Magic-App: Deck 53 „Max · Niv's Werkstatt“ (Niv-Mizzet, Izzet; Stärke 9,4) und Deck 54 „Julia · Sumpfkreislauf“ (Grakmaw, Golgari; Stärke 7,9). Fraglich nur Putrefy. Custom-Alternativ-Commander „Niv, die ernste Ente“ und „Urschl, das Kosmodil“ sind seit 26.11. abends fertige Kartenbilder (eigener Rahmen, Artwork basisEnte bzw. cosmodile_urschl aus Drive Inner Shell/assets/characters) und werden in der App im Deck-Dialog angezeigt (web/custom/karten.json). Nur Commander custom, die 99 bleiben echt (Max, 25.11.).

## Regeln

NIV, DIE ERNSTE ENTE – {1}{U}{R}, Legendäre Kreatur — Ente Berater, 2/3. Fliegend. Immer wenn du in einem Zug deine zweite Karte ziehst: 1 Schaden an ein Ziel. Strenger Blick — {1}{U}, {T}: Neutralisiere eine aktivierte oder ausgelöste Fähigkeit (1× pro Zug). Flavor: „Mau.“ Er hat nicht gelacht. Er hat noch nie gelacht. Trotzdem lacht der ganze Tisch.

URSCHL, DAS KOSMODIL – {2}{B}{G}, Legendäre Kreatur — Krokodil Geist, 3/5. Schläfrig — enttappt nicht wie üblich; zu Beginn des Versorgungssegments ein Essen opfern, um es zu enttappen. Getappt unzerstörbar. Einmal pro Zug, wenn eine Kreaturenkarte in deinen Friedhof gelangt: ein Teig (Essen). Orakel — {T}, opfere ein Essen: Kartentyp nennen, oberste Karte aufdecken; falscher Typ → Hand, richtiger Typ → Friedhof + zwei +1/+1-Marken auf eine Kreatur. Flavor: Es beantwortet jede Frage. Nur nie die, die du gestellt hast.

DER BÄR (27.11.2026, Max' Wunsch „noch einen Bär Commander“; zweite Alternative für Deck 53) – {2}{U}{R}, Legendäre Kreatur — Bär Avatar, 1/2. +1/+1 je Kartentyp unter Karten in allen Friedhöfen. Winterschlaf — kann nur angreifen, wenn du in diesem Zug schon einen Spontanzauber oder eine Hexerei gewirkt hast. Alles strebt zum Bären — wenn du deinen zweiten Zauberspruch im Zug wirkst: oberste zwei Karten ansehen, eine auf die Hand, eine in den Friedhof. Flavor: Alles strebt zum Omnibären. Ob er einer ist, sagt der Bär nicht. Artwork baer.png (Drive). Offen: ob der Bär lieber ein eigenes Deck/andere Farben bekommen soll.

HERR RIMMELE, DER FUCHS (27.11.2026, Max' Wunsch für Julia; zweite Alternative für Deck 54) – Figur: sehr ehrenvoll, schnell pikiert, mag keinen Weltraum/Science-Fiction, Musketier. {1}{B}{G}, Legendäre Kreatur — Fuchs Ritter, 2/2. Erstschlag. Satisfaktion — zu Beginn des Kampfes im eigenen Zug kann er eine gegnerische Kreatur mit Stärke ≥ seiner fordern: +1/+1-Marke auf ihn, dann kämpfen beide (fordert nie Schwächere). Pikiert — immer wenn ein Gegner einen Artefaktzauber wirkt, +1/+1-Marke auf ihn (Technik = Sci-Fi). Flavor: „Raumschiffe? Mein Herr, ich bitte Sie. Ein Degen genügt.“ Artwork: KI-Bild Musketier-Fuchs nach dem Plüschfoto ferdinand_rimmele.jpg (Drive); im Drive heißt er Ferdinand Rimmele. Running Gag möglich: verträgt sich nicht mit dem Kosmodil.

FAIRNESS: Max' Deck für 1v1 gedrosselt; App-Heuristik zählt Draw/Counter stark, Brettdruck kaum; echte Partien loggen und per Elo nachjustieren.

## Ablage

Magic-App (magic.duckdevlab.com): Entwürfe Deck 53 und 54, Kartenbilder unter /opt/ops/src/magic/web/custom/, Renderer /opt/ops/src/magic/werkzeuge/custom-karten (render.py + bauen.sh; neue Karte: Eintrag in render.py, Artwork daneben, ./bauen.sh, karten.json ergänzen; art_crop für ganze Szenen), Commits fafaf3a, e7a1b98, be3343e, 35de339 (Rimmele mit echtem Plüschfoto). Regel (Max 27.11.): Plüsch-Commander müssen wie das echte Plüschtier aussehen, also freigestellte Fotos statt KI-Bilder. Rimmele-Fotos: Uploads fenn_haer_rimely(_1).png, freigestellt in /mnt/project-files/magic/pluesch-commander/rimmele-freigestellt.png; es gibt auch eine gezeichnete Ritterversion (fenn_justicebound.png). Projektdateien: /mnt/project-files/magic/pluesch-commander/ (pluesch-commander.md, karte-*.png). Doku-PR baerimbild/duckdevlab-docs #27, noch nicht gemergt.
