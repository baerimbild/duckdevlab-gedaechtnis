# Investment Hub · Recherche: bestehende Lösungen, Daten, Modelle, Order-Wege

`key: investment_hub_recherche` · aktualisiert 2026-11-13 08:49 · id `zszk8pbq8wkqjhx`

## Kurzstand

ANGELEGT 13.11.2026, 09:45 – Web-Recherche durch Claude (Claude Code Cloud). Quellen im Feld links. Preise und Stände wie in den Quellen genannt, nicht selbst nachgemessen.
BESTEHENDE LÖSUNGEN – Einzelteile ja, das Ganze nein:
- Depot-Tracker als Dienst (DE): Parqet, getquin, Finanzfluss Copilot. Tracking, Performance, Dividenden, Auswertung; Parqet Plus ca. 12 €/Monat, Copilot Plus ca. 9 €/Monat; getquin hat eine kostenpflichtige KI-Depotanalyse. Lücke: Zahlen statt Einordnung, keine Berichte zur Nachrichtenlage, Daten beim Anbieter.
- Selbst gehostet: Ghostfolio (AGPL, Docker, braucht Postgres + Redis, Kurse u. a. von Yahoo Finance); Portfolio Performance (Desktop, Open Source, eher für Fortgeschrittene). Lücke: zusätzlicher Stack, kein Briefing.
- KI-Aktienanalyse Open Source: daily_stock_analysis (github.com/ZhuLinsen, MIT, rund 69.500 Sterne): Watchlist → Bericht nach Zeitplan, Versand per Mail/Telegram/Discord/Slack u. a., Web-Oberfläche, Docker, Ollama möglich. Märkte: A-Aktien, Hongkong, USA, Japan, Korea, Taiwan; Europa nicht genannt; README Chinesisch/Englisch; freie Datenquellen laut Projekt ohne Stabilitätsgarantie. Daneben viele kleine Demos (yfinance + Ollama + Streamlit/CrewAI).
- Daten-Schicht: OpenBB Open Data Platform (Open Source, MCP-Server). Auf der Website steht ein Hinweis, dass die gesamte Suite unter permissiver Lizenz geöffnet wird; Firmenlage NICHT geprüft.
- Allzweck-KI (Gemini, ChatGPT, Claude, Perplexity): kein Gedächtnis fürs Depot, kein Rhythmus, nicht auf eigener Infrastruktur.
Folgerung: Tracking nicht nachbauen, Briefing selbst bauen; daily_stock_analysis als Blaupause für den Ablauf.
DATEN: EODHD ist offizieller Vertriebspartner für Deutsche-Börse-Daten (Xetra), Pakete ab 19,99 $/Monat, Gratis-Tarif vorhanden; laut eigenem Blog ist die Xetra-Integration in die API noch im Aufbau. Nicht recherchiert: Goldpreis-Quelle, deutsche Nachrichten- und Pflichtmitteilungs-Feeds; beim Bauen klären.
LOKALE MODELLE (RTX 5090, 32 GB): Übersichtsseiten von Okt./Nov. 2026 nennen Qwen3.8 27B (Q6, ca. 25 GB, grob 50–60 Token/s) und Gemma 4 (27B bzw. 31B) als beste Allrounder, Qwen3.6 35B-A3B als schnellste Variante. Das sind Sammelseiten mit Schätzwerten → an echten deutschen Texten testen.
ORDER-WEGE (nur Kostenfakten, keine Empfehlung):
- Stiftung Warentest: online über Direktbank/Onlinebroker am günstigsten; Betreuung in der Filiale ist der teure Weg. Depotübertrag darf nichts kosten.
- PFOF-Verbot seit 1.7.2026: Trade Republic 1 € je Order (2 € bei selbst gewähltem Handelsplatz), Scalable Gratis-Tarif 0,99 €.
- Direktbanken online typisch rund 4,90 € + 0,25 % des Volumens.
- Telefon bei Direktbanken: Aufschlag je Auftrag, z. B. 9,50 € (Commerzbank Direktdepot, 2026); ältere Angabe rund 14,90 € bei comdirect/ING/maxblue, Preisverzeichnis prüfen.
- Bank und Ordergröße des Vaters unbekannt → erst seine echte Abrechnung ansehen.
- Für Max später (Order per Programm): Interactive Brokers API (auch über CapTrader); Consorsbank hat eine dokumentierte Trading-API (Zugang für Privatkunden ungeprüft); brokerize als Multi-Broker-Schnittstelle (eher für Plattformen).
Claude-Kommentar (09:45): Der Open-Source-Bereich kennt fast nur Demos nach dem Muster „KI sagt kaufen oder verkaufen“ auf yfinance. Genau das würde ich nicht nachbauen: Der Vater hat das Urteil, ihm fehlt die Vorarbeit.
NACHTRAG 13.11.2026, 09:55 – Ollama-Tags geprüft (registry.ollama.ai/library/gemma4): qwen3.8:27b (Standardbuild 18 GB), gemma4:31b (dicht, knapp 20 GB), gemma4:26b (MoE). Ein „Gemma 4 27B“ gibt es in der Ollama-Bibliothek nicht; die Angabe oben entsprechend lesen.

## Ablage

Lesefassung mit Tabelle: claude.ai-Projekt „Investment Hub“, Doc claude/investment-hub-konzept-v0.md, Abschnitte 2, 6 und 8. Konzept: Bereich investment_hub.

## Links

Faden 08ggx3c8blvm9wv | https://railway.com/deploy/ghostfolio.md | https://railway.com/deploy/ghostfolio-railway.md | https://www.broker-test.at/?p=36960 | https://www.justetf.com/de/academy/parqet-erfahrungsbericht.html | https://github.com/ZhuLinsen/daily_stock_analysis | https://openbb.co/products/odp/ | https://www.llamabuilds.ai/gpus/rtx-5090/best-models | https://openclawdc.com/blog/best-local-llm-32gb-vram/ | https://llmconfigurator.com/en/best-models/rtx-5090 | https://eodhd.com/financial-apis-blog/eodhd-becomes-official-deutsche-borse-market-data-distributor | https://www.biallo.de/fonds/news/pfof-aenderungen-neobroker/ | https://tradingforfuture.de/2026/08/30/neobroker-2026-gebuehren-und-handelsplaetze-werden-zum-geschaeftsmodell/ | https://www.test.de/Depotkosten-und-Wertpapierprovisionen-Tausende-Euro-sparen-4224822-0/ | https://www.bankdaten.de/commerzbank/depot.html | https://www.boerse-online.de/nachrichten/aktien/onlinebroker-im-test-versteckte-kosten-welche-heimliche-kosten-beim-traden-mit-onlinebrokern-anfallen-20314847.html | https://www.captrader.com/de/software/handel-via-api/ | https://developer.consorsbank.de/documentation/docs/how-to-use-the-trading-api
