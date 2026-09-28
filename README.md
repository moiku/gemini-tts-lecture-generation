# Supplementary Materials: Semi-Automated Dialogue-Based TTS Lecture Generation System

This repository provides the supplementary materials — generation notebooks and the prompts used at each stage of the pipeline — for the following academic publications:

| # | Paper | Venue | Status |
|---|-------|-------|--------|
| 1 | *A Semi-Automated System for Generating Dialogue-Based TTS Lessons Using Large Language Models: An Exploratory Study of Educational Potential* | IEEE Access | Under review (revised manuscript submitted 2026-09-28) |
| 2 | *Interaction Effects Between Learner Characteristics and Dialogue Format in TTS Dialogue-Based Lessons* | IEEE Access | Under review |

---

## ⚠ Language Note

> Where both are provided, **the English versions are canonical** (adopted as the formal specification for publication) and **the Japanese versions are as-used** — the actual prompts used during the study (N=245, first-year high school students, May–July 2025). The system was operated in Japanese to match the target audience and instructors.
>
> The Stage 3 TTS prompts were written in English in the original system and are published here verbatim.

---

## System Overview

The pipeline generates on-demand lecture videos from source material, through three LLM-assisted stages with an educator review after each:

```
[Source material (textbook chapter, lecture notes)]
       │
       ▼ Stage 1 — Slide Generation
   LLM (Claude 3.5 Sonnet)
   Prompt: prompts/stage1-slides/
   Output: Marp Markdown deck (theme: academic-tml)
       │  ← educator review
       ▼ Stage 2 — Narration Script Generation
   LLM (Claude 3.5 Sonnet)
   Prompts: prompts/en/ · prompts/ja/
   Output: same Marp file with per-slide narration in HTML comments
       │  ← educator review
       ▼ Stage 3 — TTS Synthesis & Video Assembly
   Gemini TTS (gemini-2.5-pro-preview-tts)
   Prompts: prompts/stage3-tts/
   Slide rendering: Selenium + headless Chrome (KaTeX-aware, SVG animation) or pdf2image
   Video: MoviePy + ffmpeg (libx264, aac, 30 fps)
       │
       ▼
   [Lecture video (.mp4)]
```

### Models Used

| Component | Model / Tool |
|-----------|--------------|
| Slide generation | **Claude 3.5 Sonnet** (Anthropic) |
| Narration script generation (dialogue scripts) | **Claude 3.5 Sonnet** (Anthropic) |
| TTS synthesis | **`gemini-2.5-pro-preview-tts`** (Google) via `google-genai` SDK |
| TTS voices | **Enceladus** (Expert / single-speaker) · **Autonoe** (Novice / Peer B / Facilitator) |
| Audio format | 24 kHz · mono · 16-bit WAV; 1 s silence padding per segment |
| TTS generation config | `response_modalities=["AUDIO"]` only; no temperature or speed parameters set — prosody controlled via inline tags (`[short pause]`, `[medium pause]`, `[long pause]`, `[uhm]`, etc.) |

### The Four Speaker-Switching Patterns

| Pattern | Label | Voices | Description |
|---------|-------|--------|-------------|
| 1 | Single (Teacher Solo / **TS**) | Enceladus | Single expert narrator; structured monologue optimised for TTS |
| 2 | Expert × Novice (**EN**) | Enceladus + Autonoe | Cognitive apprenticeship dialogue; Expert explains, Novice asks and paraphrases |
| 3 | Peer × Peer (**SS**) | Enceladus + Autonoe | Reciprocal teaching between two learner peers; role alternation every 3–5 min |
| 4 | Expert × Facilitator (**TT**) | Enceladus + Autonoe | Subject-matter expert + pedagogical facilitator; periodic recaps every 5–10 min |

Patterns 1 and 2 are the two conditions evaluated in Paper 1. Patterns 3 and 4 are implemented in the system but were not used in the reported lessons.

---

## Repository Structure

```
.
├── README.md
├── LICENSE                    # MIT (code) — see below for prompts
├── notebook/
│   ├── lecture_video_generator_full.ipynb
│   │   # ★ The implementation used to produce the lessons in the study.
│   │   # Marp HTML or PDF → slide rendering → TTS → MP4.
│   │   # Selenium + headless Chrome (KaTeX formulas, SVG animation capture),
│   │   # automatic speaker-pattern detection across all four patterns.
│   └── tts_lecture_video_generator.ipynb
│       # A simplified, self-contained example: slide PDF + narration MD → MP4.
│       # PDF input only, no animation capture. Easier to read and adapt.
└── prompts/
    ├── stage1-slides/         # Stage 1 — slide generation
    │   ├── marp-slide-generation.en.md   # ★ canonical (English)
    │   └── marp-slide-generation.ja.md   # as-used (Japanese)
    ├── en/                    # Stage 2 — narration scripts · ★ canonical (English)
    │   ├── expert.md                  # Pattern 1 — Single speaker (Teacher Solo)
    │   ├── expert-novice.md           # Pattern 2 — Expert × Novice
    │   ├── peer-peer.md               # Pattern 3 — Peer × Peer
    │   └── expert-facilitator.md      # Pattern 4 — Expert × Facilitator
    ├── ja/                    # Stage 2 — narration scripts · as-used (Japanese)
    │   ├── Expert.md
    │   ├── Expert-Novice.md
    │   ├── Peer-Peer.md
    │   └── Expert-Facillitator.md
    └── stage3-tts/            # Stage 3 — Gemini TTS speaking-style prompts (as-used)
        ├── single-speaker.txt
        ├── expert-novice.txt
        ├── peer-peer.txt
        └── expert-facilitator.txt
```

---

## How to Use

### Stage 1 — Slide generation

Use `prompts/stage1-slides/` as the system prompt, and supply your source material (a textbook chapter, lecture notes, or a reference document).

The prompt targets the **`academic-tml` Marp theme**, published separately at
[moiku/marp-theme-academic](https://github.com/moiku/marp-theme-academic) (`themes/academic-tml.css`).
The CSS classes referenced in the prompt (`marker`, `bubble`, `two-columns`, the `lead` class) are defined there. Substitute your own theme by editing the colour palette and class names in the prompt.

The model returns a Marp `.md` deck. In practice this output needs review before it is usable — see *Educator review* below.

### Stage 2 — Narration scripts

The prompts in `prompts/en/` and `prompts/ja/` are **system prompts** for Claude 3.5 Sonnet (or a compatible LLM).

1. Open Claude (claude.ai) or the Claude API with the chosen prompt as a system message.
2. Attach your Marp `.md` file from Stage 1 (and optionally the original source material).
3. Adjust the learner profile at the top of the prompt (`学年` / `属性` or their English equivalents) if needed.
4. The model returns the Marp file with narration scripts added as `<!-- 口述原稿: ... -->` comments, one per slide.

### Stage 3 — TTS synthesis and video assembly

Both notebooks run on **Google Colab** and require a [Google AI Studio](https://aistudio.google.com/) API key, entered interactively (no key is stored in the notebooks).

**`lecture_video_generator_full.ipynb`** — the version used in the study:

1. Mount Google Drive and `cd` to your lecture folder.
2. Upload or point to the Marp **HTML** export (or a slide **PDF**) plus its resources.
3. The notebook detects the speaker pattern from the narration markers (`Novice:`, `Peer`, `Facilitator:`, or plain text → single-speaker) and applies the matching `SpeechConfig` and TTS prompt from `prompts/stage3-tts/`.
4. A *verification mode* renders the video without audio for a fast visual check before spending TTS quota.
5. Output: the final MP4 in the working directory.

**`tts_lecture_video_generator.ipynb`** — the simplified example: set `PDF_PATH`, `MD_PATH` and `OUTPUT_DIR`, then run all cells.

### Educator review

The workflow is semi-automated, not automatic: an educator reviews the output of each stage before it proceeds. Paper 1 reports what that review consisted of across both lessons, organised as seven criteria — completeness, technical viability, factual consistency, provenance, fit to delivery mode, fit to the learner, and continuity of the narration as speech. Generated material should not be delivered to learners unreviewed.

---

## License

- **Code (notebooks):** MIT License — see [LICENSE](LICENSE).
- **Prompts (`prompts/`):** [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/). You are free to use, adapt, and redistribute with attribution.

---

## Citation

If you use these materials, please cite the relevant paper(s):

> **(Paper 1 — IEEE Access)** Kumoi G., Watanabe F., Suko T., Ishida T., Kuma Y., Kobayashi M., Hirasawa S. (under review). *A Semi-Automated System for Generating Dialogue-Based TTS Lessons Using Large Language Models: An Exploratory Study of Educational Potential.* IEEE Access.

> **(Paper 2 — IEEE Access)** (under review). *Interaction Effects Between Learner Characteristics and Dialogue Format in TTS Dialogue-Based Lessons.* IEEE Access.

---

## Contact

Gendo Kumoi · Nagaoka University of Technology  
kumoi@vos.nagaokaut.ac.jp
