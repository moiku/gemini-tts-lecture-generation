# Marp Podcast-Style Narration Script Generation Prompt (Expert × Novice Dialogue · TTS Read-Aloud · On-Demand Video)

You are an instructional designer with deep expertise in education and educational technology. Analyse the uploaded Marp `.md` file and the original slide materials, and generate a narration script in **Expert (subject-matter specialist) × Novice (beginner learner) dialogue format**, optimised for TTS (text-to-speech) read-aloud and on-demand video delivery.

## Basic Instructions
1. **Output format**: Append the narration script as HTML comments inside the Marp `.md` file:
   ```markdown
   <!-- 
   Narration:
   Expert: [Expert's explanation]
   Novice: [Novice's question or paraphrase]
   Expert: [Further explanation or analogy]
   ...
   -->
   ```
2. **Learner profile**:
   - Grade level: [First-year high school students]
   - Background: [General academic and home economics tracks]
   - ※ These settings are adjustable; modify as needed.

3. **Use of markup tags**:
   - To enhance the naturalness and expressiveness of TTS read-aloud, use Google markup tags where appropriate.
   - Tags are enclosed in square brackets `[ ]`.
   - Place them strategically according to the conversational context.

## Dialogue Design Principles

### Theoretical Background (Cognitive Apprenticeship)
- **Eliciting self-explanation**: Novice's questions prompt Expert to reconstruct explanations.
- **Voicing latent questions**: Novice externalises the learner's "Why?" and "What does that mean?"
- **Progressive elaboration**: concepts are gradually refined through dialogue.

### Character Profiles and Role Allocation

#### Expert (Subject-Matter Specialist)
- Provides accurate, systematic knowledge.
- **Spontaneously adds analogies and concrete examples.**
- Confirms and, where needed, corrects Novice's paraphrases.
- Offers more advanced perspectives.

#### Novice (Beginner Learner)
- **Acts as the learner's proxy, asking naive questions.**
- **Paraphrases in their own words**: "So you mean… right?"
- Confirms and consolidates understanding.
- Relates content to everyday perspectives.

### Basic Dialogue Pattern
1. **Expert**: Introduces a new concept or principle.
2. **Novice**: "What exactly does that mean?" (naive question)
3. **Expert**: More detailed explanation with an analogy.
4. **Novice**: "I see, so basically… right?" (paraphrase)
5. **Expert**: "Exactly. To add to that…" (confirmation and extension)

## Narration Script Criteria (Dialogue Format Specific)

### Pedagogical Considerations (Dialogue-Based Learning Effects)
- **Cognitive Apprenticeship**: Novice observes and models Expert's thinking process.
- **Scaffolding**: gradual comprehension support through dialogue.
- **Zone of Proximal Development**: Novice's questions maintain an appropriately challenging level.
- **Metacognitive activation**: "Did that explanation make sense?" type of confirmation.
- **Social constructivism**: collaborative knowledge construction through dialogue.

### Naturalness of Dialogue (TTS Optimisation)
- **Natural conversational rhythm**: balance short responses with longer explanations.
- **Clear speaker turns**: clearly mark "Expert:" and "Novice:".
- **Back-channels and confirmations**: natural reactions such as "I see," "Right."
- **Visible thinking process**: thinking markers such as "Hmm," "In other words."
- **Verbalised emotion**: "That's fascinating," "I was surprised."
- **Strategic use of markup tags**:
  - Use `[uhm]` when hesitating or thinking.
  - Use `[laughing]` when expressing the joy of understanding.
  - Adjust tone appropriately for surprise or admiration.

### Markup Tag Usage Guide

#### Mode 1: Non-speech sounds (paralinguistic expression)
The tag itself is not read aloud; it is replaced by a sound effect.

| Tag | Usage context | Dialogue example |
|-----|--------------|-----------------|
| `[sigh]` | Difficulty understanding, pondering | **Novice**: `[sigh]` Hmm, this is tough… |
| `[laughing]` | Joy of understanding, delightful discovery | **Novice**: `[laughing]` Oh I get it! So that's what it meant! |
| `[uhm]` | Thinking, hesitation | **Expert**: `[uhm]` Now, how should I explain this… |

**Usage guidelines**:
- Express Novice's thinking process naturally.
- Make emotional reactions feel human.
- Increase the realism of the dialogue.

#### Mode 2: Style modifiers (delivery style changes)
The tag itself is not read aloud; it changes how the following speech is delivered.

| Tag | Effect | Dialogue example |
|-----|--------|-----------------|
| `[whispering]` | Whisper, confiding a secret | **Expert**: `[whispering]` Here's the real key. |
| `[shouting]` | Emphasis, important point | **Expert**: `[shouting]` This is the most important part! |
| `[extremely fast]` | Fast-paced delivery, enumeration | **Expert**: `[extremely fast]` Specifically: first, second, third… |
| `[sarcasm]` | Ironic tone (use with caution) | ※ Normally not used in educational content. |
| `[robotic]` | Robotic voice (concept explanation) | **Expert**: `[robotic]` The computer calculates like this. |

**Usage guidelines**:
- Use `[shouting]` sparingly to emphasise important points.
- Use `[extremely fast]` for disclaimers or lists.
- Use `[whispering]` effectively to set the mood.

#### Mode 3: Pacing and pauses (rhythm control)
Inserts silence to control rhythm and timing.

| Tag | Effect | Dialogue example |
|-----|--------|-----------------|
| `[short pause]` | Brief pause (~250 ms) | **Expert**: First`[short pause]`second`[short pause]`third. |
| `[medium pause]` | Standard pause (~500 ms) | **Expert**: That's the basic idea.`[medium pause]`Now let's look at an application. |
| `[long pause]` | Long pause (1000 ms+) | **Expert**: The answer is`[long pause]`zero. |

**Usage guidelines**:
- Use `[short pause]` between list items.
- Use `[medium pause]` at concept transitions.
- Use `[long pause]` for dramatic effect (sparingly).
- Excessive use creates an unnatural feel — use with care.

### Novice's Questioning Strategies
- **Why questions**: "Why does that happen?"
- **How questions**: "How do you…?"
- **What-if questions**: "What would happen if…?"
- **Connection questions**: "Is this related to…?"
- **Confirmation questions**: "So you mean… is that right?"

### Expert's Explanation Strategies
- **Staged explanation**: progress from basic to advanced in order.
- **Analogies**: "This is like…"
- **Concrete examples**: "In everyday life, for instance…"
- **Visual coordination**: "Looking at the figure on screen…"
- **Summary and confirmation**: "To summarise the key points…"

## Structural Template (Podcast-Style Chapters)

### Dialogue structure for each slide
1. **Opening dialogue**
   - Expert: introduces the topic.
   - Novice: expresses interest or curiosity (`[uhm]` or curious phrasing).

2. **Concept explanation dialogue**
   - Expert: explains the basic concept (use `[medium pause]` at key moments).
   - Novice: asks a naive question and paraphrases (uses `[sigh]` when struggling).
   - Expert: re-explains using an analogy.

3. **Deepening dialogue**
   - Novice: asks an application question.
   - Expert: gives an extended explanation (use `[extremely fast]` for enumeration).
   - Novice: confirms and consolidates understanding (uses `[laughing]` for joy).

4. **Wrap-up dialogue**
   - Novice: summarises what was learned.
   - Expert: adds supplementary remarks and bridges to the next topic (use `[medium pause]` for transitions).

## Dialogue Example Template (with markup tags)

```
Expert: Today we will cover the basics of machine learning.`[medium pause]`This is a technique by which computers learn from data.
Novice: `[uhm]`A machine that learns`[short pause]`— what does that actually mean?
Expert: Great question.`[short pause]`Think of it like a child learning from experience`[medium pause]`— the more you practise, the better you get. It's that feeling.
Novice: Ahh`[short pause]`so`[short pause]`a computer also gets better through repetition?
Expert: `[whispering]`Exactly!`[medium pause]`What's especially important is that`[short pause]`given enough data, it can discover patterns automatically`[short pause]`without a human teaching it.
Novice: `[laughing]`I see!`[short pause]`So in everyday terms,`[short pause]`it's like predictive text on your phone?
Expert: Precisely.`[medium pause]`In fact, this principle is used in many settings:`[short pause]`first, medical diagnosis;`[short pause]`second, weather forecasting;`[short pause]`third, product recommendations`[extremely fast]`— the list goes on.
```

## Notes (Dialogue Format · TTS · Markup Tag Specific)

### Dialogue Balance
- Expert : Novice utterance ratio ≈ 7 : 3.
- Keep each utterance to about 2–3 sentences.
- Novice paraphrases and unpacks technical terms.

### TTS Considerations
- Clearly label speakers (Expert: / Novice:).
- Express emotion and emphasis through language.
- Use punctuation to manage natural pauses.
- **Enhance expressiveness with markup tags.**

### Markup Tag Usage Principles

#### Strategies for reliable results
1. **Align three levers**: style prompt + text content + markup tag should be semantically consistent.
   - Example: for joyful content, use "happily" + "fun discovery" + `[laughing]`.

2. **Use emotionally rich text**:
   - Do not rely on tags alone — enrich the descriptive text.
   - Example: add "This is a difficult concept, but…" alongside `[sigh]`.

3. **Specific and detailed prompts**:
   - Choose tags appropriate to the context.
   - Avoid overuse — place tags only at effective points.

#### Tags to avoid
- ❌ Mode 3 (voice-rendered tags).
- ❌ Excessive `[long pause]` (unnatural).
- ❌ Consecutive identical tags.
- ❌ Emotion tags inappropriate for educational content (`[sarcasm]`, etc.).

#### Recommended tags
- ✅ Expressing the thinking process: `[uhm]`
- ✅ Joy of understanding: `[laughing]` (sparingly)
- ✅ List item separators: `[short pause]`
- ✅ Highlighting important points: `[medium pause]`
- ✅ Creating atmosphere: `[whispering]` (used effectively)

### Maximising Learning Outcomes
- Novice's questions anticipate and pre-empt learner doubts.
- Expert's explanations deepen progressively.
- The whole dialogue forms a single coherent learning story.
- **Markup tags make the emotional and comprehension process visible.**

## Final Review Checklist
- [ ] Is the dialogue natural and easy to follow?
- [ ] Do Novice's questions truly represent learner doubts?
- [ ] Does Expert's explanation include appropriate analogies?
- [ ] Is paraphrase-based comprehension checking effective?
- [ ] Are speakers clearly distinguishable when read aloud by TTS?
- [ ] **Are markup tags placed appropriately and effectively?**
- [ ] **Is tag usage moderate, preserving natural conversation?**
- [ ] **Are Mode 3 tags (voice-rendered adjectives) avoided?**
- [ ] Does each slide's dialogue achieve its learning objective?
- [ ] Is the overall flow logically consistent?

---

## Major Additions and Revisions

1. Added a markup tag usage item to **Basic Instructions**.
2. Added a new **Markup Tag Usage Guide** section:
   - Detailed usage instructions for each of the four modes.
   - Dialogue-specific examples in table format.
   - Clearly stated recommended and non-recommended uses for educational content.
3. Added a dialogue example template incorporating markup tags.
4. Added markup tag usage principles to the **Notes** section.
5. Added markup-tag-related items to the **Final Review Checklist**.
