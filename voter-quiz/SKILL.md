---
name: voter-quiz
description: Build a personalized, shareable interactive voter quiz for any specific election and location. Use when the user wants to create a voter guide, voting recommendation tool, ballot quiz, or "should I vote yes/no" matcher for a particular election (federal, state, local, primary, general, special). Covers researching the actual ballot for the user's location, writing policy-level questions, scoring candidates and ballot measures, and assembling a self-contained HTML artifact users can share with friends and neighbors. Always policy-level questions only, never general orientation. Also use when user mentions "voter quiz", "ballot guide", "election quiz", "voting recommendations", or asks how they should vote in a specific election.
---

# Voter Quiz Builder

## Overview

Build a single-file interactive HTML quiz that asks 10–25 policy-specific yes/no questions, then matches answers to candidates and ballot measures on a specific election ballot. The output is a self-contained HTML file the user can share via download or hosting.

The matching is methodologically clean and honest:
- Only specific policy stances matter (no "are you progressive?" calibration)
- Recommendations are limited to viable candidates (no Peace & Freedom or Green party recs in major races)
- Direct-policy answers override aggregate scoring for ballot measures that map 1:1 to a question
- Reasons are extracted from the user's actual answers, not invented

## When to Use

- User asks to make a voter quiz, ballot guide, voter guide, or election matcher
- User wants to help friends/neighbors decide how to vote in a specific upcoming election
- User mentions an upcoming primary, general, or special election and wants a tool to share
- User invokes "voter-quiz" by name

## Process

Walk through these steps in order. Each one feeds the next.

### Step 1: Gather Inputs

Ask the user (use `ask_user_input_v0` if available — it's faster on mobile):

1. **Which election?** (e.g., "California June 2, 2026 Statewide Direct Primary"; "November 5, 2024 General Election in NYC"; "Massachusetts March 2026 Special Election")
2. **Where do you live?** Be specific — city + county or specific district. The more specific, the better the ballot match.

If the user already supplied this in conversation, skip the questions and confirm.

### Step 2: Research the Ballot

Use `web_search` and `web_fetch` to find the actual ballot for the user's location. Sources to prioritize:

- **County Registrar of Voters** (or equivalent local elections office) — most authoritative for local races and measures
- **Secretary of State** for the relevant state — for state/federal races and statewide propositions
- **Ballotpedia** — good summaries, but verify against official sources
- **Local news** (Patch, local newspapers) — useful for context, candidate profiles, race coverage

Identify and list:
- **Federal races** (US House, US Senate when applicable)
- **Statewide partisan offices** (Governor, Lt Gov, AG, SoS, Controller, Treasurer, Insurance Commissioner, etc., if applicable)
- **State legislature** (State Senate, State Assembly for the user's district)
- **Nonpartisan state offices** (Superintendent of Public Instruction, judges, BoE)
- **County offices** (Supervisor for user's district, Sheriff, DA, etc.)
- **City offices** (Mayor, City Council — these may not be on this specific ballot)
- **School board races** (often local-only)
- **Ballot measures** (statewide propositions and local measures)

For each contested race, list candidates with: name, party preference, ballot designation (the brief description that appears next to their name on the ballot), and an initial viability assessment.

For each measure, capture: the official designation (Measure A / Prop 12 / etc.), what it does, the funding mechanism if any, and the threshold to pass.

### Step 3: Determine Question Count and Axes

**Question count scales with ballot complexity:**

| Ballot type                                       | Questions |
|---------------------------------------------------|-----------|
| Sparse (1–3 contested races, maybe 1 measure)     | 10–14     |
| Standard primary (5–10 contested + 1–2 measures)  | 14–18     |
| General election (10–20 contested + multi measures) | 18–25   |

Hard limits: 10 minimum (need enough to discriminate), 28 maximum (completion drops past this).

**Axes must be derived from the actual races on this ballot — not picked from a generic list.**

The axes exist to discriminate between viable candidates. The right axes are the dimensions on which viable candidates on this specific ballot actually disagree. Different axes for different elections — sometimes radically different.

Workflow:
1. Pull up the viable candidate list from Step 2.
2. For each contested race, identify the axes of *real* disagreement among the viable candidates. ("Both Ds agree on climate but split on housing." → housing matters here, climate doesn't discriminate.)
3. Pool the axes across all races. Some will be common (progressive/conservative ideology shows up almost everywhere). Some will be race-specific (a school board race might surface "traditional curriculum vs progressive pedagogy" that doesn't appear anywhere else on the ballot).
4. Pick 4–7 axes total, prioritizing those that discriminate in the *most* contested races.

A sample list of common axes is in `references/question-design.md` — use it as a starting menu only. Add custom axes whenever the ballot needs them. Drop standard axes the ballot doesn't need.

**Examples of when to deviate from defaults:**

- Ballot with no transit measure and no candidates with sharp transit positions → drop `transit`
- School board race featured prominently → add `educationTraditional` axis, possibly `parentRights`
- Big-city race with sharp policing-reform divide → split `safetyHawk` into `policeFunding` and `prosecutorReform`
- Ballot with a major water/growth measure → add a `growth` or `waterPolicy` axis
- Race featuring a notable abortion-rights candidate → add `abortion` axis even though it's usually settled in California
- Coastal commission seat → add `coastalDevelopment` axis

**Bad axis design** (avoid):
- Axes that score the same for every viable candidate (no discrimination)
- Generic axes that don't appear in any specific race ("trustworthiness")
- Axes that double-count the same disagreement under different labels

### Step 4: Write Policy Questions

Read `references/question-design.md` for full guidance.

**Hard rule: every question is policy-specific.** No general orientation, identity, or salience questions allowed. Each question asks about a specific government action.

For each ballot measure that has a substantive policy stance behind it, write a question that maps directly to the measure (this enables direct-answer-first logic in Step 6). Example: SMART tax extension → "The SMART train should be expanded and continued."

### Step 5: Research and Score Candidates

Read `references/candidate-scoring.md` for full guidance.

For each candidate in each contested race:
- Score on each axis (-100 to +100)
- Mark `viable: true` (default) or `viable: false` for fringe / dropped-out / very low-profile
- Include `party`, `desc` (ballot designation), `name`

Track which candidates dropped out — these get `viable: false` AND should be noted in the artifact intro if the user might wonder.

### Step 6: Assemble the Artifact

Use the template at `assets/quiz-template.html`. Read it once to understand the structure, then customize these placeholders (clearly marked with `// CUSTOMIZE:` comments):

1. **AREA** — location info (city label, district numbers)
2. **QUESTIONS** — the 10–25 policy questions
3. **CANDIDATES** — all the candidate slates
4. **UNCONTESTED** — uncontested seats
5. **DIRECT_MAPPINGS** — which questions map directly to which measures
6. **STATE_RACES** array — order of state races to display
7. **Welcome screen text** — masthead title, lede, location-specific copy
8. **Verify URL** — link to the official voter guide

Save as a single HTML file in `/mnt/user-data/outputs/`.

The template includes everything else: editorial styling (Fraunces + DM Sans, warm cream background, terracotta accent), the welcome → quiz → results flow, normalized weighted-Euclidean matching, viable-only filter, reason extraction, plain-text cheat sheet download with party labels.

### Step 7: Test and Present

Sanity-check by running a coherent voter profile through the quiz logic. Use Node.js to extract the script and simulate:

```javascript
const ctx = /* run the script */;
ctx.startQuiz();
const answers = { /* a coherent progressive answer set */ };
for (let i = 0; i < ctx.QUESTIONS.length; i++) {
  ctx.answer(answers[ctx.QUESTIONS[i].q] || 'skip');
}
console.log(ctx.buildResultsText());
```

Confirm:
- Progressive answers → progressive viable candidates
- Conservative answers → conservative viable candidates
- Measure recommendations match the direct-mapped question's answer
- No third-party / dropped-out candidates appear

Present the file with a brief summary: location, election, question count, races covered.

## Critical Design Principles

These all came from iteration. Don't compromise on them.

### 1. Policy questions only, no general orientation

Forbidden patterns:
- "How would you describe yourself politically?" (identity)
- "What's your top concern this election?" (salience)
- "Do you prefer more services or lower taxes?" (broad disposition)
- "Is climate change real?" (general agreement, not action)

Required pattern: each question asks about a specific, contested government action.

The reason: identity calibration contaminates the test. It lets the quiz match candidates based on what someone *says they are* rather than what they actually want done.

### 2. Direct-answer-first for ballot measures

When a quiz question maps directly to a ballot item (e.g., "SMART should be expanded" ↔ Measure B), the user's direct answer wins. Aggregate scoring is only a fallback for skipped questions.

This is a methodological fix to a real bug: aggregating across mixed signals can produce a recommendation that contradicts what the user explicitly said about that very policy.

### 3. Viable candidates only

Filter to viable major-party candidates by default. Third-party candidates (Peace & Freedom, Green, Libertarian, American Independent) and dropped-out candidates excluded. The on-screen disclaimer notes this filter is on. Users can still vote however they want — the recommendation is just for viable candidates.

### 4. Normalized scoring

User scores get smaller in magnitude as you cut questions. Both sides need to be on a comparable scale before computing distance, otherwise the matching biases toward moderate candidates. The template handles this automatically — don't disable it.

### 5. Reasons extracted from actual answers

For each top match, surface the user's actual quiz answers that aligned best with that candidate. Format: `[YES] California should aim for net-zero emissions sooner than 2045.` No abstract rationales like "matches your environmental views."

### 6. Simple cheat sheet for download

The downloaded text is a clean list:
```
Federal:
U.S. House Representative, 2nd District: Jared Huffman (Democratic)

State:
Governor: Katie Porter (Democratic)
...

Nonpartisan State:
Superintendent of Public Instruction: Frank Lara
```

Party shown for partisan races (matches what's on the actual ballot). Omitted for nonpartisan races.

### 7. Editorial styling

The template uses Fraunces serif headlines + DM Sans body, warm cream background, terracotta accent. The aesthetic signals "trustworthy civic tool" rather than "AI generated." Don't redesign it — the visual identity is part of the credibility.

## Failure Modes

**Adding orientation questions back in.** Tempting to add "How progressive are you?" because it gives a strong signal. But it contaminates the test. Don't.

**Too many redundant questions on one axis.** If five questions all just measure "are you progressive?", four of them are noise. Aim for diverse policy areas.

**Recommending non-viable candidates.** Don't push Peace & Freedom for a major race. Mark them `viable: false`.

**Ignoring direct-mapping for measures.** If the ballot has a measure that's basically the same yes/no question as one in the quiz, link them via DIRECT_MAPPINGS. Don't just aggregate.

**Skipping the local research.** Generic templates don't work. Each ballot is different. Use web_search for the actual local races, candidates, and measures.

**Including non-viable candidates in the slate without marking them.** The viable filter only kicks in when `viable: false` is explicitly set. Default is viable=true, so unmarked fringe candidates will get recommended.

**Letting the quiz get too long.** Each question past ~25 lowers completion. Be ruthless about cuts.

## Reference Files

- `references/question-design.md` — Detailed guidance on policy-question writing, axis design, question-pairing for opposing signals
- `references/candidate-scoring.md` — Scoring rubric, viability rules, how to research candidate positions
- `assets/quiz-template.html` — The HTML/JS template to customize. Read this in full before starting Step 6.
