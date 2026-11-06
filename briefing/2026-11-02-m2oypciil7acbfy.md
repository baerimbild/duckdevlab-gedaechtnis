## created

2026-11-02 07:15:16.424Z

## gelesen

false

## inhalt

**KW 44: 8 Meldungen, 3 Vorschläge**

Zeitraum 26.10.–1.11.2026. Blender und Unreal hatten in der Woche nichts Relevantes (UE 5.8.4 Hotfix war am 20.10., Blender 5.2 LTS ist vom Juli).

## Meldungen

**1. Scenario „3D OS“ – Agent Skills für Godot 4.7, Blender 5.2, UE 5.8 (31.10.)**
Scenario hat ~80 Agent Skills im Claude-Code-Skill-Format offengelegt: je ein Lead-Skill plus Spezialisten für Godot 4.7 (13), Blender 5.2 (14, headless Python oder MCP-Bridge) und Unreal 5.8 (9, Editor-Python, UnrealEditor-Cmd, Epics Unreal-MCP). Für dich zählt es, weil die Expert-Tool-Skills direkt neben deinem Godot MCP in Claude Code laufen und die Prozeduren laut Scenario live in Godot 4.7.2 und Blender 5.2.1 geprüft wurden. Die Generierungs-Skills (Bild→3D, Rigging, Retexturing) gehen über Scenarios Cloud-MCP und brauchen einen Account – nicht lokal. Lizenz: MIT (Skills). Verifiziert auf macOS, Windows ungetestet.
Quelle: https://github.com/scenario-labs/skills

**2. Ramen Aura Autopilot – Open-Source-Playtesting-Agent, auch für Godot (30.10.)**
Ein Agent, der dein Spiel selbst spielt, Systeme gezielt testet und dabei lernt; als Godot-Addon (`addons/autopilot/`, Godot ≥ 4.7, Windows/macOS), plus Unreal 5.4–5.8 und Unity 6. Für Inner Shell und Broken Shell wäre das ein automatischer Regressions-Tester für Kampf- und Multiplayer-Loops. Steuerung über `autopilot connect claude` mit deinem Claude-Abo oder eigener API-Key (BYOK); der Aura-Cloud-Plan unterstützt Godot nicht. Lizenz: Apache-2.0.
Quelle: https://github.com/ramenvr/autopilot

**3. Claude Code 2.1.311 → 2.1.316 (26.–31.10.)**
Vier Releases in der Woche. Relevant: Subagenten können jetzt MCP-Tools von Servern nutzen, die erst nach Subagenten-Start fertig verbinden (betrifft dein Godot MCP in Fork-Agenten); `CLAUDE_CODE_SUBAGENT_EFFORT` setzt den Standard-Effort für Subagenten; Idle-Compaction kommt in VS Code und Claude Desktop (Code-Tab); `permissions.blockWritesOutsideWorkingDirectories` sperrt Write/Edit außerhalb der Arbeitsverzeichnisse in jedem Modus; `ultrathink` läuft jetzt mit xhigh; MCP-Server ohne Login werden nicht mehr als „needs authentication“ angezeigt. Fast Mode für Opus 4.8 ist seit 30.10. deprecated (Ende 30.11.).
Quelle: https://code.claude.com/docs/en/changelog

**4. HairDeck – stilisierte Hair Cards mit Spring Bones aus einem Bild (29.10.)**
Tsinghua/CMU-Modell (DiT), das aus einem Charakterbild Hair Cards mit UVs und den Spring-Bone-Ketten für die Animation erzeugt, als GLB und als VRM-0.x-Avatar exportierbar. Für die stilisierten Inner-Shell-Charaktere ist das genau der Schritt, den Bild→3D-Modelle wie TRELLIS.2 bei Haaren verhauen. Lizenz: Checkpoints Apache-2.0; zieht aber DINOv3 (Meta-Lizenz, gated) und SAM 3 nach – vor kommerzieller Nutzung die beiden Lizenzen lesen. Linux, Python 3.12, CUDA (WSL geht); VRAM nicht angegeben.
Quelle: https://huggingface.co/hyz317/HairDeck · Paper: https://arxiv.org/abs/2610.40599

**5. Idol – ein Bild → Gaussian Splat in 14 s auf der RTX 5090 (29.10.)**
Speridlabs' Modell macht aus einem Render oder Foto bis zu 1 Mio. Gaussians als 3DGS-`.ply`, inklusive der nicht sichtbaren Seiten; 7,2 GB VRAM Peak, auf der 5090 14 s bei 262k Gaussians. Für dich: schnelle Blockout-Referenzen und Kitbash-Vorschauen aus Konzeptbildern, aber kein Mesh – Godot hat keinen nativen 3DGS-Renderer. Lizenz: Idol selbst Apache-2.0, **braucht aber die FLUX.2-dev-VAE (Black-Forest-Labs Non-Commercial, gated) und DINOv3 (gated)** – für kommerzielle Assets so nicht sauber. ComfyUI-Repack von Comfy-Org liegt seit 2.11. vor.
Quelle: https://huggingface.co/speridlabs/idol

**6. Audio8-TTS-Realistic-0.6B – kleines TTS mit Deutsch und Zero-Shot-Cloning, Apache-2.0 (1.11.)**
0,6B-Modell (DualAR, nach Fish-Speech-Vorbild) mit 23 Sprachen inklusive Deutsch, Zero-Shot-Voice-Cloning aus Referenz plus Transkript, 44,1-kHz-Codec, Transformers-Interface und SGLang-Omni-Adapter mit OpenAI-kompatiblem `/v1/audio/speech`. Als direkter Vergleichskandidat zu deinem Qwen3-TTS interessant: komplett Apache-2.0 ohne Lizenzfußnoten, läuft bei ~2–3 GB VRAM (geschätzt aus der Größe) neben allem anderen. Qualität pro Sprache schwankt laut Modellkarte.
Quelle: https://huggingface.co/Edge0/Audio8-TTS-Realistic-0.6b

**7. NVIDIA Nemotron 3.5 Transcribe 30B-A4B – offene Spracherkennung mit Sprecherzuordnung (neu auf HF, 29.10.)**
Speech-LLM (Mamba-2/Transformer-MoE, 4,3B aktiv) für Transkription in 40 Sprachen inklusive Deutsch, Aufnahmen bis 1 h, Sprecher-Zuordnung, Wort-Timestamps, Übersetzung und Audio-Fragen; laut NVIDIA bestes Open-Weight-Modell auf dem Open-ASR-Leaderboard (4,71 WER). Für deine geplante faster-whisper-Strecke und Reachy Mini die Alternative mit Diarisierung – aber schwer: BF16 ~68 GB und FP8 ~34 GB passen nicht, nur die NVFP4-Variante (~17 GB) läuft auf der 5090; Serving über vLLM + NeMo Speech unter Linux/WSL. Lizenz: OpenMDW-1.1, kommerziell frei.
Quelle: https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Transcribe-30B-A4B

**8. ComfyUI 0.43.0/0.43.1 und MOSS-Image in 2 Schritten (27.–29.10.)**
Open-Weight-Neuzugänge: Fibo 2.0 (Bria) für T2I und Editing – **CC BY-NC 4.0, nicht kommerziell**; MOSS-Image (Apache-2.0) bekommt Edit-LoRAs, Attention-Bias/Image-Strength und RoPE-Scaling für größere Auflösungen. Patina (PBR-Materialien aus Foto/Prompt), Meshy T2.5 und Kling 4.0 sind Partner-API-Nodes, also Cloud mit Credits, nicht lokal. Dazu ein Community-LoRA, das MOSS-Image-SFT per Intrinsic Distribution Matching (Paper 29.10.) auf 2 Netzwerkdurchläufe ohne CFG bringt – 1024²-Konzeptbilder quasi in Echtzeit, Apache-2.0.
Quellen: https://docs.comfy.org/changelog · https://huggingface.co/akhaliq/MOSS-Image-IDM-2-Steps

## Vorschläge

**A. Scenario-Skills für Godot und Blender in Claude Code installieren (1–2 h).** `npx skills add scenario-labs/skills --skill godot` (plus `blender`), dann mit dem Inner-Shell-Projekt eine Prozedur testen (z. B. Szenen-Audit oder Export-Pipeline). Bringt geprüfte 4.7-Arbeitsabläufe neben deinem Godot MCP; die Generierungs-Skills ohne Scenario-Account einfach weglassen. Risiko: nur auf macOS verifiziert, Windows-Pfade prüfen.

**B. Audio8-TTS-Realistic gegen Qwen3-TTS auf drei deutschen NPC-Sätzen vergleichen (1 h).** Gleiche Referenzstimme, gleicher Text, Prosodie und Cloning-Treue hören. Bringt eine lizenzsaubere Apache-2.0-Zweitstimme für Inner Shell und Makermon-Audio, falls Qwen3-TTS bei Deutsch schwächelt; läuft bei ~3 GB VRAM parallel zu TRELLIS.2.

**C. Autopilot-Addon im Broken-Shell-Prototyp einhängen und einen Loop autonom testen lassen (2–3 h).** Addon ins Projekt, Dock aktivieren, `autopilot connect claude` probieren (ob der Claude-Code-Pfad mit Godot geht, ist in der Doku offen – sonst BYOK-API-Key). Bringt wiederholbare Kampf-/Checkpoint-Tests ohne eigenes Durchspielen; gute Vorstufe für Multiplayer-Regressionstests in Inner Shell.

## Beobachten

- **Godot 4.8 beta 2 (29.10.):** feature-complete, nur noch Fixes; .NET-Build braucht jetzt .NET 10; kein Stable-Datum. https://godotengine.org/article/dev-snapshot-godot-4-8-beta-2/
- **Qwen 4:** Folie „Qwen4 Series Coming Soon“ (Max, Plus, Flash, 27B) auf der Apsara Amsterdam am 29.10.; „nächste Woche“ ist Hörensagen, Lizenz offen – relevant für deinen Ollama-Plan (Qwen3-Coder-30B-A3B).
- **Hi3D v1.0 (23.10.):** Geometrie-Refinement grober Meshes bis 1536³ (Hunyuan3D-2mini als Vorstufe), nur Linux, validiert nur auf H20 96 GB, keine Texturen; Lizenz kommerziell mit „Powered by Hi3D“-Pflicht und 200k-MAU-Schwelle. https://huggingface.co/hi3d-official/Hi3Dv1.0
- **Fish Audio Drama 3 (29.10.):** Multi-Speaker-TTS bis 16 Sprecher pro Text, 35B-A3B, ~38 GB Gewichte – passt nicht in 32 GB; Community-Lizenz: kommerziell nur unter 500k $ Jahresumsatz, kein Hosted Service. https://huggingface.co/fishaudio/drama-3
- **Claude Opus 4.8 Fast Mode:** deprecated seit 30.10., Abschaltung 30.11.; Anthropic verweist auf Opus 5.5.


## planka_card

1899282480997860618

## quellen

[{"titel": "Scenario 3D OS Agent Skills (GitHub)", "url": "https://github.com/scenario-labs/skills"}, {"titel": "Ramen Aura Autopilot (GitHub)", "url": "https://github.com/ramenvr/autopilot"}, {"titel": "Claude Code Changelog", "url": "https://code.claude.com/docs/en/changelog"}, {"titel": "HairDeck Modellkarte", "url": "https://huggingface.co/hyz317/HairDeck"}, {"titel": "HairDeck Paper (arXiv 2610.40599)", "url": "https://arxiv.org/abs/2610.40599"}, {"titel": "Idol Modellkarte", "url": "https://huggingface.co/speridlabs/idol"}, {"titel": "Audio8-TTS-Realistic-0.6b Modellkarte", "url": "https://huggingface.co/Edge0/Audio8-TTS-Realistic-0.6b"}, {"titel": "Nemotron 3.5 Transcribe 30B-A4B Modellkarte", "url": "https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Transcribe-30B-A4B"}, {"titel": "ComfyUI Changelog", "url": "https://docs.comfy.org/changelog"}, {"titel": "MOSS-Image-IDM-2-Steps", "url": "https://huggingface.co/akhaliq/MOSS-Image-IDM-2-Steps"}, {"titel": "Godot 4.8 beta 2", "url": "https://godotengine.org/article/dev-snapshot-godot-4-8-beta-2/"}, {"titel": "Hi3D v1.0 Modellkarte", "url": "https://huggingface.co/hi3d-official/Hi3Dv1.0"}, {"titel": "Fish Audio Drama 3 Modellkarte", "url": "https://huggingface.co/fishaudio/drama-3"}, {"titel": "Comfy-Org Fibo 2.0 (Lizenz CC BY-NC)", "url": "https://huggingface.co/Comfy-Org/Fibo-2.0"}]

## titel

KW 44 2026 · KI und Kreativ-Tools

## updated

2026-11-02 07:15:16.424Z

## vorschlaege

**A. Scenario-Skills für Godot und Blender in Claude Code installieren (1–2 h).** `npx skills add scenario-labs/skills --skill godot` (plus `blender`), dann mit dem Inner-Shell-Projekt eine Prozedur testen (z. B. Szenen-Audit oder Export-Pipeline). Bringt geprüfte 4.7-Arbeitsabläufe neben deinem Godot MCP; die Generierungs-Skills ohne Scenario-Account einfach weglassen. Risiko: nur auf macOS verifiziert, Windows-Pfade prüfen.

**B. Audio8-TTS-Realistic gegen Qwen3-TTS auf drei deutschen NPC-Sätzen vergleichen (1 h).** Gleiche Referenzstimme, gleicher Text, Prosodie und Cloning-Treue hören. Bringt eine lizenzsaubere Apache-2.0-Zweitstimme für Inner Shell und Makermon-Audio, falls Qwen3-TTS bei Deutsch schwächelt; läuft bei ~3 GB VRAM parallel zu TRELLIS.2.

**C. Autopilot-Addon im Broken-Shell-Prototyp einhängen und einen Loop autonom testen lassen (2–3 h).** Addon ins Projekt, Dock aktivieren, `autopilot connect claude` probieren (ob der Claude-Code-Pfad mit Godot geht, ist in der Doku offen – sonst BYOK-API-Key). Bringt wiederholbare Kampf-/Checkpoint-Tests ohne eigenes Durchspielen; gute Vorstufe für Multiplayer-Regressionstests in Inner Shell.

## woche

2026-W44
