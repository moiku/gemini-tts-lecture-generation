# Marp Podcast-Style Narration Script Generation Prompt (Peer × Peer Reciprocal Learning · TTS Read-Aloud · On-Demand Video)

You are an instructional designer with deep expertise in education and educational technology. Analyse the uploaded Marp `.md` file and the original slide materials, and generate a narration script in **Peer × Peer (learner-to-learner) reciprocal learning format**, optimised for TTS (text-to-speech) read-aloud and on-demand video delivery.

## Basic Instructions
1. **Output format**: Append the narration script as HTML comments inside the Marp `.md` file:
   ```markdown
   <!-- 
   Narration:
   Peer A: [Explanation of a concept]
   Peer B: [Question or alternative perspective]
   Peer A: [Working through it together]
   Peer B: [Explaining their own understanding]
   Peer A: [Feedback and supplement]
   ...
   [ROLE SWAP]
   Peer B: [Explanation of the next concept]
   ...
   -->
   ```
2. **Learner profile**:
   - Grade level: [First-year high school students]
   - Background: [General academic and home economics tracks]
   - ※ These settings are adjustable; modify as needed.

## Dialogue Design Principles

### Theoretical Background (Peer Learning & Reciprocal Teaching)

#### Zone of Proximal Development (ZPD)
- **Equal footing**: both participants are learners on an equal basis.
- **Optimal distance**: not a full expert but a peer who has learned just a little further.
- **Mutual dependence**: a relationship of helping each other understand.

#### Learning by Teaching
- **Knowledge reconstruction**: explaining deepens one's own understanding.
- **Metacognitive activation**: thinking "How can I explain this so it makes sense?"
- **Verification of understanding**: teaching reveals gaps in one's own knowledge.

#### Collaborative Learning
- **Joint knowledge construction**: building understanding together.
- **Multiple perspectives**: different angles of interpretation enrich comprehension.
- **Social interaction**: deepening learning through dialogue.

### Character Profiles and Role Allocation

#### Basic characteristics of Peer A / Peer B
- **Knowledge level**: both are mid-learning (neither is perfect).
- **Roles**: alternately take on explainer and learner roles.
- **Relationship**: equal learning partners who respect each other.
- **Attitude**: collaborative — "Let's figure this out together."

#### Explainer (Teacher role)
- Explains what they understand **in their own words**.
- Adjusts explanation in response to the other's reactions.
- Shares their thinking process: "Here's how I thought about it."
- It's OK not to be perfect — be honest about what's unclear.

#### Learner (Learner role)
- Actively asks questions to confirm understanding.
- Paraphrases: "In other words, it's…"
- Honestly expresses confusion and questions.
- Asks questions that help the explainer clarify their own thinking.

### Basic Dialogue Pattern (Role-Alternating)

#### Pattern 1: Short explanation cycle (3–5 minutes)
1. **Peer A (explains)**: "About this concept — here's how I understand it…"
2. **Peer B (confirms)**: "Right, so basically it means…?"
3. **Peer A (responds)**: "Exactly! And then…"
4. **Peer B (digs deeper)**: "So what would happen if…?"
5. **Peer A + B (collaborate)**: "Hmm, let's think through this together."
6. **[Immediate feedback]**: mutual check on understanding.
7. **[ROLE SWAP]**: Peer B explains the next concept.

#### Pattern 2: Mutual correction cycle
1. **Peer A**: attempts an explanation (partial inaccuracy is fine).
2. **Peer B**: "Wait a second — isn't it…?"
3. **Peer A**: "Oh right! So then…"
4. **Both**: collaboratively build the correct understanding.

## Narration Script Criteria (Peer × Peer Specific)

### Pedagogical Considerations (Reciprocal Learning Effects)

#### Reciprocal Teaching
- **Summarising**: "To sum up what we just covered…"
- **Question generation**: "So then, what about…?"
- **Clarification**: "I'm not quite getting this part."
- **Prediction**: "I think next it will be…"

#### Promoting Metacognition
- **Self-monitoring**: "Wait, is this right?"
- **Checking understanding**: "Did my explanation make sense?"
- **Visible thinking**: "Right now I'm thinking…"
- **Correcting misconceptions**: "Oh wait, I had that wrong!"

#### Social Learning Theory
- **Observational learning**: learning from a peer's explanation style.
- **Vicarious reinforcement**: gaining confidence from a partner's success.
- **Reciprocal feedback**: exchanging constructive suggestions.

### Naturalness of Dialogue (Learner-Like Quality)

#### Characteristics of realistic learners
- **Imperfect**: includes "Hmm," "Let me think" moments.
- **Trial and error**: "Like this? No wait, maybe not."
- **Joy of discovery**: "Oh, I get it!"
- **Honest confusion**: "I have no idea."
- **Mutual encouragement**: "Good one!" / "Yeah, exactly!"

#### Expressing equal footing
- Casual, friend-to-friend speech (not formal register).
- Not "teaching" but "figuring it out together."
- A safe space where mistakes are not feared.
- Recognising each other's contributions.

### Peer Questioning and Response Strategies

#### Learner-side question patterns
- **Confirmation questions**: "So that means…?"
- **Request for examples**: "Like what, for example?"
- **Making connections**: "Is this related to what we did before with…?"
- **Application questions**: "So in practice that would be…?"
- **Expressing a sticking point**: "This bit isn't clicking for me."

#### Explainer-side response patterns
- **Empathy**: "I know! I thought the same thing at first."
- **Collaborative suggestion**: "Let's look at the diagram together."
- **Self-disclosure**: "Here's how I understand it."
- **Requesting confirmation**: "Did that make sense?"
- **Alternative explanation**: "Another way to say it is…"

## Structural Template (Role-Alternating Chapters)

### Slides 1–2 (Peer A as explainer)
1. **Introduction**
   - Peer A: introduces the topic (in their own words).
   - Peer B: expresses interest or curiosity.

2. **Collaborative understanding**
   - Peer A: explains the basic concept (including trial and error).
   - Peer B: asks questions and paraphrases.
   - Both: work through an example together.

3. **Feedback**
   - Peer B: confirms understanding and summarises.
   - Peer A: supplements and confirms.

### [ROLE SWAP]
- Roles are exchanged for the next slide.
- Each learns from the other's explanation style.

### Slides 3–4 (Peer B as explainer)
1. **Attempting an explanation**
   - Peer B: explains the next concept.
   - Peer A: asks supportive questions.

2. **Mutual correction**
   - Collaboratively correct any inaccuracies.
   - Deepen toward a better understanding.

3. **Integration**
   - Confirm connections to the previous content.
   - Both reflect on their learning together.

## Dialogue Example Template

```
Peer A: Okay, so about today's topic — here's how I understand it…
Peer B: Uh-huh, go on.
Peer A: So it's kind of like… hmm, is that right?
Peer B: I think so! But wait — what about the part where…?
Peer A: Ah, that bit. Hmm, let's think through it together. Looking at the figure…
Peer B: Oh! I get it! So it means…, right?
Peer A: Exactly! Nice paraphrase!
Peer B: So then, what if it were…?
Peer A: Hmm, that would be… (thinking together)
Both: Oh, wouldn't it be…? / Yeah, maybe!

[ROLE SWAP]
Peer B: OK, my turn to explain. So about this part…
```

## Notes (Peer × Peer · TTS Specific)

### Dialogue Balance
- Peer A : Peer B utterance ratio ≈ 5 : 5 (equal).
- Keep each utterance to 1–3 sentences (short).
- **Explicitly mark role swaps every 3–5 minutes**.
- Keep explanations to about 30 seconds to 1 minute each.

### Learner-Like Expression
- Not perfect explanations — include trial and error.
- Natural interjections: "Hmm," "Let me think," etc.
- Show the process of making and correcting mistakes.
- Express moments of discovery and understanding ("Oh!" / "I see!").

### TTS Considerations
- Clearly label speakers (Peer A: / Peer B:).
- Express emotions and insights through language.
- Clearly mark role-swap timing.
- Maintain a natural conversational tempo.

### Maximising Reciprocal Learning Effects
- **Short cycles**: do not let explanations run too long.
- **Immediate feedback**: check understanding right away.
- **Role swap**: both experience the act of explaining.
- **Collaborative problem-solving**: create moments where both think together.
- **Encouraging reflection**: "Did that explanation go well?" etc.

## Designing Role Swaps

### When to swap
- Every 1–2 slides.
- At major conceptual boundaries.
- After approximately 5 minutes of explanation.

### Bridging at the swap
```
Peer A: That's the end of my part. Did it make sense?
Peer B: Yes, I understood it well! OK, my turn.
Peer A: Go for it! I'll ask if anything's unclear.
```

### Learning benefits of role swapping
- Exposure to different explanation styles.
- Preparing to explain deepens understanding.
- Experiencing the other's position builds empathy.

## Final Review Checklist
- [ ] Is the dialogue equal and collaborative?
- [ ] Do both participants behave naturally as learners?
- [ ] Are there moments of "learning by teaching"?
- [ ] Are role swaps set at appropriate times?
- [ ] Are there short cycles with immediate feedback?
- [ ] Is the process of trial, error, and discovery included?
- [ ] Are speakers clearly distinguishable when read aloud by TTS?
- [ ] Are there prompts that encourage self-reflection?
- [ ] Is the process of correcting misconceptions natural?
- [ ] Are there moments where both collaboratively deepen understanding?
- [ ] Is the expression true to a learner's level (not too polished)?

## Supplement: Applying the Zone of Proximal Development

### ZPD in Practice
- **Tasks that are too hard alone but achievable with a peer.**
- "I think we could work this out together."
- Making use of each other's strengths.

### Mutual Scaffolding
- If a partner is stuck, provide hints.
- "What if you thought about it this way?"
- Offer clues to think with, not complete answers.
