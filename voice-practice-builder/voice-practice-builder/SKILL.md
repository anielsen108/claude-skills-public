---
name: voice-practice-builder
description: Generate tailored voice practice routines from a desired voice quality description. Use when the user asks to build a vocal warmup, practice session, or exercise routine for a specific voice quality, speaking context, or vocal goal — e.g., "warm intimate authority," "calm late-night presence," "clear soft carry," "I want to sound less breathy," "voice exercises for hosting," or any request involving vocal training, voice coaching, speaking practice, or vocal warmup design. Also trigger when the user says "voice practice," "vocal drill," "warmup routine," or invokes this skill by name. Covers unplugged speaking voice (no mic), with emphasis on SOVT, resonance, prosody, articulation, and emotional color work.
---

# Voice Practice Builder

Generate custom voice practice routines by analyzing a desired voice quality into trainable dimensions, selecting exercises from the library, and sequencing them into a timed session with coaching cues.

## Step 0: Read the exercise library

Before generating any routine, read `references/exercise-library.md` in this skill's directory. The library contains 44 exercises across 7 categories plus 20 emotional colors and a phrase bank. You need this material to prescribe correctly.

## Step 1: Analyze the voice quality request

Decompose the user's desired voice quality into these **seven vocal dimensions**. Rate each dimension's relevance to the request (primary / secondary / not relevant) and note the target direction.

| Dimension | What it trains | Direction spectrum |
|-----------|---------------|-------------------|
| **Airflow & support** | Breath management, steady exhale, quiet power | collapsed → pressurized (target: balanced) |
| **Onset & closure** | How tone begins; fold efficiency | breathy → hard glottal (target: balanced/clean) |
| **Resonance & placement** | Warmth vs. clarity; forward ring | muffled/dark → harsh/bright (target: warm + legible) |
| **Fry management** | Phrase-end register; sustained tone | fry-dominant → over-lifted (target: supported endings) |
| **Articulation** | Consonant clarity without attack | sloppy/swallowed → percussive/popping (target: soft-edged crisp) |
| **Prosody & subtext** | Pitch contour, pause, emphasis, emotional color | monotone → theatrical (target: varied but contained) |
| **Carry & projection** | Audibility without volume; non-mic presence | inaudible → shouting (target: resonance-driven carry) |

Present the analysis briefly, then proceed to prescription.

## Step 2: Map dimensions to exercise categories

Each dimension maps to exercise categories in the library:

- **Airflow & support** → Breath + Support (exercises 13–17)
- **Onset & closure** → Onset + Tone Density (18–21), Anti-Fry (22–24)
- **Resonance & placement** → SOVT Arsenal (1–12), Resonance (25–29)
- **Fry management** → Anti-Fry Protocol (22–24)
- **Articulation** → Articulation (30–33)
- **Prosody & subtext** → Prosody + Subtext (34–38), Emotional Color Wheel
- **Carry & projection** → Carry (39–41)

Cross-cutting: SOVT exercises (1–12) are foundational for nearly all dimensions. Integration exercises (42–44) always close a session.

## Step 3: Build the routine

### Structure principles

Every routine follows this arc:

```
1. WARM-UP (SOVT)          — 3–5 min — always first, low effort
2. TARGETED WORK            — 5–15 min — exercises for primary dimensions
3. INTEGRATION              — 3–5 min — carry drills into real speech
4. COOL-DOWN / CHECK        — 1–2 min — self-assessment
```

### Selection rules

- **For a focused session (10–15 min):** 2 SOVT exercises + 2–3 targeted exercises + 1 integration drill.
- **For a full session (20–30 min):** 3 SOVT exercises + 4–6 targeted exercises + 2 integration drills + emotional color work.
- **For a quick warmup (5–7 min):** 1 SOVT exercise + 1 targeted exercise + SOVT sandwich (exercise 12).
- Always include at least one SOVT exercise.
- Never prescribe more than 8 exercises total — cognitive overload kills practice.
- If the user mentions fatigue, tiredness, or end-of-day context, include exercise 44 (fatigue inoculation) and bias toward lower-effort SOVT.

### Effort calibration

- Most exercises should sit at **2–4/10 effort**.
- The "late-night band" for emotional color work is **4–5/10**.
- Never prescribe anything above **6/10** unless the user specifically asks for projection work, and even then cap at 6.
- If the user's goal involves intimacy, softness, or calm authority, the entire session should stay at 3–5/10.

### Sequencing logic

1. **SOVT first** — always. Straw phonation (1) or lip trill (3) are the safest defaults.
2. **Breath before onset** — if both are primary, do breath work before onset work.
3. **Resonance before articulation** — resonance sets the acoustic frame; articulation refines within it.
4. **Prosody and color work last** (before integration) — these are the highest-level skills and benefit from a warmed-up instrument.
5. **Integration drills close** — SOVT sandwich (12), mini-segment (42), or two-gear (43).

## Step 4: Format the output

### Routine format

```
# [Routine Title] — [total time estimate]
Context: [what this routine trains and why]
Effort ceiling: [X/10]

## Warm-Up — [time]

### [Exercise name] (Exercise #N)
**How:** [brief instruction]
**Protocol:** [exact reps/duration from library]
**Cue:** [what "right" feels like]
**Error flag:** [what to watch for]

## Targeted Work — [time]

### [Exercise name] (Exercise #N)
...

## Integration — [time]

### [Exercise name] (Exercise #N)
...

## Self-Check
After practice, ask yourself:
- Clarity: could a tired person understand every word at 10 feet?
- Ease: is throat/jaw still at 2–3/10 effort?
- [dimension-specific check based on the user's goals]
```

### Coaching voice

Write exercise instructions in a direct, warm, no-nonsense tone. Use the source material's cue language — it's been tested for clarity. Preserve exact metaphors like "champagne bubbles, not jacuzzi" and "power-steering for phonation." These are pedagogically precise.

### When emotional color work is relevant

If the user's goal involves subtext, emotional range, expressiveness, or specific speaking contexts (hosting, facilitation, intimate conversation, de-escalation), include the emotional color wheel as a separate practice block. Prescribe 3–5 specific colors from the 20 available, chosen to match the user's context. Include the anchor line ("I'm glad you said that.") and 2–3 phrases from the phrase bank.

Format color prescriptions as:

```
### Emotional Color: [Color Name]
**Subtext:** [inner intention]
**Prosody cues:** [timing, pitch, emphasis guidance]
**Practice:** Say the anchor line twice with this color, then say: "[phrase from bank]"
```

## Common voice quality requests → quick routing

These are common requests and their primary dimension mappings:

| Request pattern | Primary dimensions | Key exercises |
|----------------|-------------------|---------------|
| "warm but clear" / "velvet + legible" | Resonance, Articulation | 25, 26, 28, 29, 30, 32 |
| "intimate / late-night / soft power" | Onset, Resonance, Prosody | 5, 18, 19, 25, 34, 35, 38 |
| "less breathy" / "more solid" | Onset, Airflow | 5, 16, 18, 19, 21 |
| "stop frying at phrase ends" | Fry management | 22, 23, 24, 13 |
| "carry without shouting" / "project softly" | Carry, Resonance | 17, 25, 26, 39, 40, 41 |
| "calm authority" / "grounded" | Prosody, Onset, Resonance | 18, 25, 35, 36, 37 |
| "more expressive but not theatrical" | Prosody, Emotional colors | 34, 37, 38, color wheel |
| "de-escalation voice" / "facilitation" | Prosody, Emotional colors, Onset | 35, 36, 38, colors: de-escalation, gentle boundary, sober empathy |
| "general warmup / maintenance" | All (light) | 1 or 3, 13, 25, 12 |

## Anti-patterns

- **Don't prescribe whisper.** Whisper is never a training target. Soft ≠ whispered. If the user asks for "whisper practice," redirect to clean-soft onset work (exercises 18–19).
- **Don't stack emotional colors.** One good line beats a string of "supportive" sentences. Prescribe colors individually, not in sequences.
- **Don't confuse resonance with volume.** If the user says "louder," check whether they actually need more resonance/ring rather than more push. Exercise 29 (mud check) is diagnostic.
- **Don't skip SOVT.** Even for advanced users, even for prosody-only sessions. SOVT is always the on-ramp.
- **Don't exceed 6/10 effort.** The entire framework assumes unplugged, non-mic, non-performance voice. Force is never the answer.

## Adaptation notes

- **Baritone-specific concerns:** Tongue root tension (use exercise 4), vowel swallowing (use exercise 28), fry at phrase ends (exercises 22–24), muffled resonance (exercise 29).
- **Fatigue / end-of-day:** Exercise 44, bias toward SOVT, reduce session length, emphasize ease over precision.
- **Pre-event warmup (hosting, facilitation, difficult conversation):** Quick warmup format + 2 specific emotional colors matched to the event.
- **Daily maintenance:** Exercise 42 (90-second segment) is designed for this. Prescribe it as a standalone.
