# Supplementary Materials: Semi-Automated Dialogue-Based TTS Lecture Generation System

This repository provides the supplementary materials — generation notebook and narration-script prompts — for the following academic publications:

| # | Paper | Venue | Status |
|---|-------|-------|--------|
| 1 | *A Semi-Automated System for Generating Dialogue-Based TTS Lessons Using Large Language Models: An Exploratory Study of Educational Potential* | IEEE Access | Under Review |
| 2 | *Evaluating the Effects of Dialogue Format Variation on Learner Experience in LLM-Generated TTS Lessons: A Within-Subject Study* | IEEE Transactions on Learning Technologies | Under Review |

---

## ⚠ Language Note

> **The English-language prompts in `prompts/en/` are the canonical versions** (adopted as the formal specification for publication).  
> **The Japanese-language prompts in `prompts/ja/` are the as-used versions** — these are the actual prompts used during the study (N=245, first-year high school students, May–July 2025). The system was operated in Japanese to match the target audience and instructors.

---

## System Overview

The pipeline generates on-demand lecture videos fully automatically from slide decks (Marp/HTML or PDF) and narration scripts:

```
[Slide deck (Marp md)]
       │
       ▼ Stage 1 — Slide Generation
   LLM (Claude 3.5 Sonnet)
   Prompt: Marp slide generation
       │
       ▼ Stage 2 — Narration Script Generation
   LLM (Claude 3.5 Sonnet)
   Prompts: Expert / Expert-Novice / Peer-Peer / Expert-Facilitator
       │
       ▼ Stage 3 — TTS Synthesis & Video Assembly
   Gemini TTS (gemini-2.5-pro-preview-tts)
   Slide rendering: Selenium + headless Chrome (KaTeX-aware) / pdf2image
   Video: MoviePy + ffmpeg (libx264, aac, 30 fps)
       │
       ▼
   [Lecture video (.mp4)]
```

### Models Used

| Component | Model / Tool |
|-----------|--------------|
| Narration script generation (dialogue scripts) | **Claude 3.5 Sonnet** (Anthropic) via Claude API |
| TTS synthesis | **`gemini-2.5-pro-preview-tts`** (Google) via `google-genai` SDK |
| TTS voices | **Enceladus** (Expert / single-speaker) · **Autonoe** (Novice / Peer B / Facilitator) |
| Audio format | 24 kHz · mono · 16-bit WAV; 1 s silence padding per segment |
| TTS generation config | `response_modalities=["AUDIO"]` only; no temperature or speed parameters set — prosody controlled via inline tags (`[short pause]`, `[medium pause]`, `[long pause]`, `[uhm]`, etc.) |

### The Four Speaker-Switching Patterns

| Pattern | Label | Voices | Description |
|---------|-------|--------|-------------|
| 1 | Single (Teacher Solo / **TS**) | Enceladus | Single expert narrator; structured monologue optimised for TTS |
| 2 | Expert × Novice (**EN / TS** variant) | Enceladus + Autonoe | Cognitive apprenticeship dialogue; Expert explains, Novice asks and paraphrases |
| 3 | Peer × Peer (**SS**) | Enceladus + Autonoe | Reciprocal teaching between two learner peers; role alternation every 3–5 min |
| 4 | Expert × Facilitator (**TT**) | Enceladus + Autonoe | Subject-matter expert + pedagogical facilitator; periodic recaps every 5–10 min |

---

## Repository Structure

```
.
├── README.md
├── LICENSE                    # MIT (code) — see below for prompts
├── notebook/
│   └── tts_lecture_video_generator.ipynb
│       # Stage 3 pipeline: PDF + Marp MD → TTS synthesis → MP4 video
│       # Runs on Google Colab; requires a Google AI Studio API key
└── prompts/
    ├── en/                    # ★ Canonical versions (English)
    │   ├── expert.md                  # Pattern 1 — Single speaker (Teacher Solo)
    │   ├── expert-novice.md           # Pattern 2 — Expert × Novice
    │   ├── peer-peer.md               # Pattern 3 — Peer × Peer
    │   └── expert-facilitator.md      # Pattern 4 — Expert × Facilitator
    └── ja/                    # As-used versions (Japanese, original)
        ├── Expert.md
        ├── Expert-Novice.md
        ├── Peer-Peer.md
        └── Expert-Facillitator.md
```

---

## How to Use

### Prompts (Stages 1–2)
The prompts in `prompts/` are **system prompts** for Claude 3.5 Sonnet (or compatible LLM).  
Upload your Marp `.md` slide file and source material together with the chosen prompt to generate TTS-optimised narration scripts embedded as HTML comments in the Marp file.

1. Open Claude (claude.ai) or the Claude API with the prompt as a system message.
2. Attach/upload your Marp `.md` file (and optionally the original lecture material).
3. Adjust the learner profile at the top of the prompt (`学年` / `属性` or their English equivalents) if needed.
4. The model will output the Marp file with narration scripts added as `<!-- 口述原稿: ... -->` comments per slide.

### Notebook (Stage 3)
The notebook `notebook/tts_lecture_video_generator.ipynb` handles the full TTS + video pipeline and runs on **Google Colab**:

1. Mount Google Drive and set the working directory to your lecture folder.
2. Set your **Google AI Studio API key** (`api_key`).
3. Point `narration_file` to the Marp HTML (or PDF) output of your slides.
4. The notebook auto-detects the speaker pattern from the narration script markers (`Novice:`, `Peer`, `Facilitator:`, or plain text → single-speaker) and applies the matching `SpeechConfig`.
5. Output: `final_video.mp4` in the working directory.

---

## License

- **Code (notebook):** MIT License — see [LICENSE](LICENSE).
- **Prompts (`prompts/`):** [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/). You are free to use, adapt, and redistribute with attribution.

---

## Citation

If you use these materials, please cite the relevant paper(s):

> **(Paper 1 — IEEE Access)** Kumoi G., Watanabe F., Suko T., Ishida T., Kuma Y., Kobayashi M., Hirasawa S. (under review). *A Semi-Automated System for Generating Dialogue-Based TTS Lessons Using Large Language Models: An Exploratory Study of Educational Potential.* IEEE Access.

> **(Paper 2 — IEEE TLT)** (under review). *Evaluating the Effects of Dialogue Format Variation on Learner Experience in LLM-Generated TTS Lessons.* IEEE Transactions on Learning Technologies.

---

## Contact

Gendo Kumoi · Nagaoka University of Technology  
kumoi@vos.nagaokaut.ac.jp

