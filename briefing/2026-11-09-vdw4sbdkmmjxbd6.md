## created

2026-11-09 07:14:29.415Z

## gelesen

false

## inhalt

**KW 45 (2.–8. Nov 2026): 7 Meldungen, 3 Vorschläge**

Ruhige Woche bei den Engines: kein Godot-Release (Stand bleibt 4.8 beta 2 vom 29.10.), kein Blender-Release, Unreal nur mit Ankündigung. Die Bewegung lag bei Claude Code und bei kleinen, lokal laufenden Modellen für 3D und Sprache.

## Meldungen

**1. Claude Code 2.1.314 → 2.1.319 (3.–7. Nov): MCP-Tasks, härtere Permissions, Sicherheitsfixes**
Fünf Releases in einer Woche: MCP-Tool-Aufrufe, die der Server als Task ausführt, laufen jetzt im Terminal im Hintergrund weiter und melden sich fertig (`CLAUDE_CODE_DISABLE_MCP_TASK_BACKGROUND=1` schaltet das ab); neu sind `permissions.denyInsteadOfPrompting` (statt auf eine Freigabe zu warten wird der Aufruf abgelehnt und der Turn läuft weiter) und `permissions.blockWritesOutsideWorkingDirectories`; dazu Fixes für eine `sed`-Umgehung der Permission-Prüfung, einen Sandbox-Escape beim Anlegen von Worktrees und Bash-Regeln, die Befehle mit Anführungszeichen übersehen haben. Seit 2.1.317 fragt Claude Code außerdem nach, bevor ein Web- oder Shell-Aufruf deine Account-Mail ins Netz schickt.
Warum: Genau die Schalter, die für unbeaufsichtigte Läufe (Scheduled Tasks, Godot-MCP-Sessions) fehlten; die Sicherheitsfixes sind ein Grund, jetzt zu aktualisieren.
Quelle: https://code.claude.com/docs/en/changelog

**2. Ollama 0.40.14/0.40.15 (3. Nov): YaRN-Long-Context für Qwen3/3.5, `ollama launch claude`**
Qwen3- und Qwen3.5-Modelle bekommen YaRN-Skalierung für lange Kontexte, GGUF-Vision- und rekurrente Modelle verarbeiten mehrere Anfragen parallel, `ollama launch claude` übernimmt das Output-Token-Limit des Modells. Neue Modelle: MiMo V2.6 (9B, Code/Agent) und AutoTrust (9B/35B/27B-VL).
Warum: Betrifft direkt deinen geplanten Ollama-Aufbau mit Qwen3-Coder-30B-A3B; langer Kontext ist für Godot-Projektdateien der Engpass. Kandidat daneben: Qwen3.8-27B (dicht, Apache 2.0, Vision, Terminal-Bench 73.0; Q4 ≈ 16–18 GB VRAM, lässt auf der 5090 Platz für ~100k Kontext, ist aber deutlich langsamer als das 30B-A3B-MoE).
Lizenz: Ollama MIT · Qwen3.8-27B Apache 2.0. Quelle: https://github.com/ollama/ollama/releases · https://huggingface.co/Qwen/Qwen3.8-27B

**3. CCORE GLB-3D-Coder 4B (5. Nov): Text → Three.js-Szene → GLB-Export für Godot**
Qwen3.5-4B-Finetune, das aus einem Prompt eine komplette HTML/Three.js-Seite mit „Export GLB“-Button schreibt; der System-Prompt zielt explizit auf den Godot-Editor. GGUF Q4_K_M/Q8_0 vorhanden, Trainingsdatensatz (3.918 validierte GLB-Beispiele, 40 Domänen) offen. Antworten sind lang (Ø ~20k Tokens, Thinking an, Output-Limit auf unbegrenzt).
Warum: Low-Poly-Props und Greybox-Assets per Prompt, editierbar in Blender, ohne Cloud; für Makermon-Objekte und Inner-Shell-Platzhalter interessant.
Lizenz: Apache 2.0 · VRAM: Q8 ≈ 5 GB, Q4 ≈ 3 GB plus Kontext. Quelle: https://huggingface.co/ccore/Qwen3.5-4B-GLB-3D-Coder

**4. LibreTRELLIS2-4b (6. Nov): TRELLIS.2-Geometrie in reinem PyTorch**
LibreYOLO packt die Geometrie-Netze von Microsofts TRELLIS.2-4B byte-identisch neu und führt sie ohne FlexGEMM, flash-attn oder o-voxel aus (`LibreGen("trellis2")`, läuft auf CUDA, MPS und CPU). Nur Shape, keine Texturnetze.
Warum: Deine WSL-TRELLIS.2-Installation hängt an genau diesen Custom-Kernels; das hier ist ein Fallback für Mesh-only-Durchläufe, falls die Umgebung wieder bricht.
Lizenz: MIT (TRELLIS.2) · DINOv3-Encoder unter Metas eigener Lizenz (gated, vor kommerzieller Nutzung prüfen). Quelle: https://huggingface.co/LibreYOLO/LibreTRELLIS2-4b

**5. HairDeck (Code 30.10., Gewichte auf HF 6. Nov): stilisierte Hair Cards + Spring Bones aus einem Bild**
Tsinghua/CMU-Modell (Diffusion Transformer) erzeugt aus einem Charakterbild Hair Cards mit UVs, Farben und Spring-Bone-Ketten, exportiert GLB und VRM 0.x. Vier Varianten pro Lauf, Linux/Windows mit CUDA (Python 3.12, PyTorch 2.8).
Warum: Stilisierte Haare sind der teuerste Handarbeitsposten bei Inner-Shell-Charakteren; Spring Bones kommen direkt als animierbare Ketten mit. Trainiert auf Anime-Stil, für euren Look testen.
Lizenz: Apache 2.0 (Code und Gewichte) · benötigt SAM 3 und DINOv3 (beide gated, eigene Lizenzen). VRAM: nicht angegeben. Quelle: https://huggingface.co/OxBee/HairDeck · https://github.com/hyz317/HairDeck

**6. Audio8-TTS-Realistic-Air (2. Nov): 0,6B-TTS mit Zero-Shot-Cloning in 23 Sprachen, darunter Deutsch**
Edge0 veröffentlicht den Nachfolger des Audio8-Preview: gleiche Größe (601M), deutlich natürlichere Prosodie, 44,1-kHz-Codec, Cloning aus Referenzaudio plus Transkript, SFT-Skripte im Repo, SGLang-Omni-Adapter mit OpenAI-kompatibler `/v1/audio/speech`-API. Läuft in Transformers mit `trust_remote_code`.
Warum: Direkter Vergleichskandidat zu Qwen3-TTS für Broken-Shell-Hörfassungen und Reachy-Mini-Sprachausgabe, mit kleinerem VRAM-Bedarf.
Lizenz: Apache 2.0 · VRAM: 0,6B in BF16 ≈ 2–3 GB. Quelle: https://huggingface.co/Edge0/Audio8-TTS-Realistic-Air

**7. Claude Code verweigert Nachbauten bestehender Spiele (Prompt-Änderung ~27.10., bestätigt 30.10.)**
Anthropic hat dem Claude-Code-System-Prompt zwei Sätze hinzugefügt, die das Nachbauen eines konkreten fremden Spiels unterbinden (auch umbenannt); laut Addy Osmani bleiben eigene Spiele, Genre-Spiele und Arbeit mit eigenen Designs und Assets unberührt. Nicht abschaltbar.
Warum: Broken Shell ist ein eigener Souls-like-Prototyp, also nicht betroffen, aber bei Referenz-Formulierungen („wie in Spiel X“) kann Claude jetzt bremsen; Prompts auf eigene Mechaniken statt Vergleichstitel formulieren. Knapp vor dem Wochenfenster, wegen Relevanz aufgenommen.
Quelle: https://www.gamedeveloper.com/programming/anthropic-appears-to-have-ordered-ai-tool-claude-to-stop-remaking-video-games

## Vorschläge

**A. GLB-3D-Coder als Prop-Generator testen (1–2 h).** Q8-GGUF in LM Studio oder Ollama laden (Kontext ≥ 64k, Output unbegrenzt, Thinking an), 5 Makermon-/Inner-Shell-Props prompten, GLB in Godot 4.7 importieren und in Blender prüfen. Bringt: Einschätzung, ob Greybox-Props künftig per Prompt statt per Hand entstehen.

**B. Audio8-TTS gegen Qwen3-TTS auf Deutsch (1–2 h).** Drei Absätze aus einer Broken-Shell-Kurzgeschichte mit beiden Modellen und derselben Referenzstimme synthetisieren, auf Prosodie und Aussprache hören. Bringt: Entscheidung für die Hörfassungs-Pipeline und für die Reachy-Mini-Stimme; Audio8 ist kleiner und Apache-lizenziert.

**C. Claude-Code-Settings für unbeaufsichtigte Läufe (0,5 h).** Auf 2.1.319 aktualisieren, in den Projekt-Settings `permissions.blockWritesOutsideWorkingDirectories: true` und für Scheduled Tasks `permissions.denyInsteadOfPrompting: true` setzen. Bringt: Läufe hängen nicht mehr an Freigaben, Schreibzugriffe bleiben im Projektordner.

## Beobachten

- Unreal Engine 5.9 Preview: am 3.11. auf der Unreal Fest Tokyo angekündigt, Preview „nächste Woche“ (also diese), mit „improved AI workflows“ und Web als Zielplattform; relevant für die MCP/Python-Seite der Cutscene-Pipeline. https://runtimewire.com/article/epic-unreal-engine-5-9-preview-web-target
- GodotFest 2026 (3.–4.11., München): Foundation-Q&A, Fireside „Godot's Next Milestones“ (Rémi Verschelde, Matt Ellis), Clay Johns Renderer-Talk, Multiplayer-Talks (Ichor Online, Dome Keeper); Aufzeichnungen folgen auf dem GodotFest-YouTube-Kanal. https://godotfest.com/schedule/
- Godot 4.8: beta 2 vom 29.10. ist der letzte Snapshot, kein RC in Sicht; Blog diese Woche nur ein Showcase. https://godotengine.org/blog/
- Idol (speridlabs, 29.10.): Bild → Gaussian Splat in <2 s bei 7,2 GB VRAM, Apache 2.0, zieht aber die FLUX.2-dev-VAE (nicht-kommerzielle Lizenz) und DINOv3; für kommerzielle Inner-Shell-Assets erst nach Klärung der Lizenzkette. https://huggingface.co/speridlabs/idol
- Underdog Woof (6.11.): 40-MB-CPU-TTS mit 1,4 % WER, nur Englisch und Non-Commercial-Lizenz; kommerziell nicht nutzbar. https://huggingface.co/ConwayResearch/Underdog-Woof
- Blender 5.2 LTS bleibt aktuell, kein 5.3-Beta-Termin veröffentlicht. Open WebUI (0.12.4 vom 25.10.), ComfyUI (0.43.0 vom 27.10.), ACE-Step, Qwen3-TTS, Luanti: keine Releases im Fenster.


## planka_card

1904355320491148560

## quellen

[{"titel": "Claude Code Changelog", "url": "https://code.claude.com/docs/en/changelog"}, {"titel": "Ollama Releases (0.40.14/0.40.15)", "url": "https://github.com/ollama/ollama/releases"}, {"titel": "Qwen3.8-27B Modellkarte", "url": "https://huggingface.co/Qwen/Qwen3.8-27B"}, {"titel": "CCORE Qwen3.5-4B-GLB-3D-Coder", "url": "https://huggingface.co/ccore/Qwen3.5-4B-GLB-3D-Coder"}, {"titel": "LibreTRELLIS2-4b", "url": "https://huggingface.co/LibreYOLO/LibreTRELLIS2-4b"}, {"titel": "HairDeck Modellkarte", "url": "https://huggingface.co/OxBee/HairDeck"}, {"titel": "HairDeck Code", "url": "https://github.com/hyz317/HairDeck"}, {"titel": "Audio8-TTS-Realistic-Air", "url": "https://huggingface.co/Edge0/Audio8-TTS-Realistic-Air"}, {"titel": "Game Developer: Claude Code und Spiel-Nachbauten", "url": "https://www.gamedeveloper.com/programming/anthropic-appears-to-have-ordered-ai-tool-claude-to-stop-remaking-video-games"}, {"titel": "Runtimewire: UE 5.9 Preview angekündigt", "url": "https://runtimewire.com/article/epic-unreal-engine-5-9-preview-web-target"}, {"titel": "GodotFest 2026 Schedule", "url": "https://godotfest.com/schedule/"}, {"titel": "Godot Blog", "url": "https://godotengine.org/blog/"}, {"titel": "Idol (speridlabs)", "url": "https://huggingface.co/speridlabs/idol"}, {"titel": "Underdog Woof", "url": "https://huggingface.co/ConwayResearch/Underdog-Woof"}]

## titel

KI und Tools · KW 45 2026

## updated

2026-11-09 07:14:29.415Z

## vorschlaege

**A. GLB-3D-Coder als Prop-Generator testen (1–2 h).** Q8-GGUF in LM Studio oder Ollama laden (Kontext ≥ 64k, Output unbegrenzt, Thinking an), 5 Makermon-/Inner-Shell-Props prompten, GLB in Godot 4.7 importieren und in Blender prüfen. Bringt: Einschätzung, ob Greybox-Props künftig per Prompt statt per Hand entstehen.

**B. Audio8-TTS gegen Qwen3-TTS auf Deutsch (1–2 h).** Drei Absätze aus einer Broken-Shell-Kurzgeschichte mit beiden Modellen und derselben Referenzstimme synthetisieren, auf Prosodie und Aussprache hören. Bringt: Entscheidung für die Hörfassungs-Pipeline und für die Reachy-Mini-Stimme; Audio8 ist kleiner und Apache-lizenziert.

**C. Claude-Code-Settings für unbeaufsichtigte Läufe (0,5 h).** Auf 2.1.319 aktualisieren, in den Projekt-Settings `permissions.blockWritesOutsideWorkingDirectories: true` und für Scheduled Tasks `permissions.denyInsteadOfPrompting: true` setzen. Bringt: Läufe hängen nicht mehr an Freigaben, Schreibzugriffe bleiben im Projektordner.

## woche

2026-W45
