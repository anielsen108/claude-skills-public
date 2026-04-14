---
name: alignment-briefing
description: alignment-briefing diagnoses how a passage participates in competitive sensemaking — what moves it makes on public discourse, what split it exploits, what simulacrum level it operates at, what alignment shift it is bidding for — and delivers a prose briefing for a non-framework reader. diagnostic, not evaluative. always two-part.
---

## tl;dr

**alignment-briefing** asks:

> "if this passage is a *move* in a discourse game, what move is it, and what is it trying to do to public alignment?"

it treats a passage not as a proposition to be judged true/false, but as a **play** on shared maps — splitting populations, capturing vocabulary, shifting simulacrum level, recruiting a faction, bidding for an alignment change.

alignment-briefing is:

- **two-part, always** — part 1 is the structured diagnosis (tagged artifact); part 2 is the prose briefing derived from it. both are always produced.
- **diagnostic, not evaluative** — it names what the move *is*, not whether the author is right or bad
- **symmetric** — any passage is a candidate target, including ones the reader agrees with
- **tag-heavy in part 1, jargon-free in part 2** — the structured pass names moves with canonical tags; the briefing translates them into plain English for a reader who has never seen the framework
- **decline-capable** — if the passage isn't doing competitive-sensemaking work, it says so and stops (in this case part 2 is a one-line briefing noting the decline)

it's the `rhetoricize` of *alignment machinery*: where rhetoricize maps the spin-space of wording, alignment-briefing maps the move-space of what the passage is trying to do to *us* — and hands the reader a memo about it.

---

## when to use

run alignment-briefing when:

- a passage feels like it's *doing something* beyond stating facts
- a framing seems to be colonizing vocabulary ("defund," "woke," "alignment," "groomer," "based," "settler-colonial")
- a debate splits cleanly along unlikely lines and you want to know what the cleaving statement is actually indexing
- a piece slides between "here's what's true" and "here's whose side you're on" without flagging the switch
- an op-ed or post reads as reasonable but leaves you with the feeling that some vocabulary has been quietly relocated

don't use when:

- you want lexical/syntactic rhetorical forensics → `rhetoricize`
- you want the hidden assumption stack → `excavate`
- you want the rival worldview generated → `antithesize`
- the passage is pure technical / descriptive / private writing with no alignment stakes (math proof, changelog, journal entry) — alignment-briefing will triage it out anyway, but don't waste the pass

**rule of thumb:** alignment-briefing = "what is this passage *doing to* the shared map, and how do I tell a colleague about it in plain English?"

---

## the canonical moves (tags)

alignment-briefing classifies moves along **seven axes**. each axis has one or more tags. the axes are drawn directly from the competitive-sensemaking literature (Alignment Gone Strange; Hoffman, *Simulacra and Subjectivity*; *Discursive Warfare and Faction Formation*; *Postmodernism for STEM Types*).

### axis 1 — scissor work
does the passage exploit (or engineer) a statement that cleanly splits populations into irreconcilable camps, each of which sees the other's reading as obviously insane?

- **[SCISSOR]** — passage is (or deploys) a scissor: cleanly cleaves audience, each side finds the other's reading unintelligible
- **[PSEUDO-SCISSOR]** — performs scissor shape without real split; ritual polarization

### axis 2 — simulacrum level
at which of Hoffman's four levels is the passage operating? (see `source grounding` below for definitions.)

- **[L1]** — objectivity as subject: sincere map-making, referent-bearing
- **[L2]** — objectivity as object: lying that still treats the map as load-bearing
- **[L3]** — relating as subject: arguments-as-soldiers; claims function as calls-to-coordination, literal truth is secondary
- **[L4]** — relating as object: assertions are pure positional moves in a shifting game; the pseudo-correspondence itself is being played

a passage can be mixed. tag the dominant level and note secondary.

### axis 3 — map-territory drift
is the passage pointing at the world, at prior maps, or at the map-game itself?

- **[TERRITORY-REF]** — referent is something outside discourse (can in principle be checked)
- **[MAP-ON-MAP]** — referent is another map, framing, or discursive object, not territory
- **[HYPERREAL]** — all referents are maps-of-maps; no grounding test is available even in principle

### axis 4 — strategic abstraction
is the passage capturing or redefining a vocabulary term such that future disputes are prejudged by the definition?

- **[ABSTRACTION-CAPTURE]** — seizes a contested term and installs a definition that advantages a position
- **[FRAMING-LOCK]** — installs a framing/category that constrains what future arguments can even be formulated

### axis 5 — faction work
what coalition is the passage building, marking membership in, or bidding for?

- **[FACTION-BID]** — recruits or rallies a coalition ("us" is being built)
- **[FACTION-MARK]** — performs in-group membership ("I am one of us")
- **[SHIBBOLETH]** — uses a phrase whose function is identification, not information

### axis 6 — mistake / conflict register
is the passage treating disagreement as a factual error to fix (mistake-frame) or as a power asymmetry to contest (conflict-frame)? does it switch between them?

- **[MISTAKE-FRAME]** — presents disagreement as fixable by evidence/argument
- **[CONFLICT-FRAME]** — presents disagreement as interest-conflict requiring power moves
- **[REGISTER-SWITCH]** — slides between frames within the passage, often to extract the credibility of mistake-frame while executing a conflict-frame move (or vice versa)

### axis 7 — alignment payload
if the passage succeeds, what shift in public alignment has it produced? this is the *point* of the pass.

- **[ALIGNMENT-PAYLOAD]** — always emit; structured sub-fields:
  - **direction:** what belief / category / coalition gets strengthened, and what gets weakened
  - **beneficiary:** who is advantaged if the move lands
  - **casualty:** who/what gets harder to defend, say, or coordinate around
  - **vocabulary-delta:** which terms change meaning, reach, or valence

### transverse tags (apply across any axis)

- **[LIVE]** — move is firing in current discourse (adapting `handlize`'s live/dormant)
- **[DORMANT]** — move is structurally present but not currently pressurizing
- **[HIGH]** / **[MED]** / **[LOW]** — analyst confidence in the tag
- **[NOT-APPLICABLE]** — axis was examined and no finding; must be explicit

### triage output (step 0 only)

- **[NO-COMPETITIVE-WORK-DETECTED]** — the passage is not doing competitive sensemaking; alignment-briefing declines and stops (part 2 becomes a one-line briefing noting the decline)

---

## signature

```
alignment-briefing(passage, depth?, charity?, scope?, verdict?) → {
  // part 1 — always produced
  analysis: {
    fingerprint, fact_ledger, moves[], alignment_payload,
    counter_reading, caveats
  },
  // part 2 — always produced
  briefing: {
    what_it_is, surface_argument, what_it_is_actually_doing,
    advantaged_disadvantaged, posture, conspicuous_omissions,
    confidence_note, bottom_line
  }
}
```

- **passage:** the text to analyze (tweet-length to long-form, single-author)
- **depth:** `quick` | `medium` | `deep` — see dials
- **charity:** `high` | `symmetric` | `low` — see dials
- **scope:** `text-local` | `discourse-context` — see dials
- **verdict:** `diagnosis-only` | `net-effect` — see dials

alignment-briefing is a **two-part operation and both parts are always produced**. Part 1 is the tagged structured analysis (the diagnostic artifact, framework-native). Part 2 is a prose briefing derived from Part 1, readable by someone who does not know the framework. The briefing is always downstream of the analysis, never written independently — the structured pass is what keeps the briefing honest.

---

## dimensionalization: the dials

four dials. orthogonal. each with failure modes per setting.

### dial 1 — depth

| setting | behavior | failure mode |
|---|---|---|
| **quick** | top-3 moves only; no counter-reading | miss structural context; scissor/L4 pattern-matching with no ballast |
| **medium** *(default)* | all 7 axes, brief; counter-reading one paragraph | the "medium-article" trap — readable but axes get compressed into vibes |
| **deep** | all axes + sub-evidence + extended counter-reading + faction-genealogy | analyst fatigue; risk of over-reading; risk of letting charity dial drift |

### dial 2 — charity

| setting | behavior | failure mode |
|---|---|---|
| **high** | assume sincere L1 mapping unless strong evidence of competitive work | false negatives; sanitizing genuinely coordinative moves as "just making a point" |
| **symmetric** *(default)* | apply same priors to both in-group-coded and out-group-coded passages | equal-opportunity miscalibration if the analyst's priors are bad in both directions |
| **low** | assume competitive work unless strong evidence of sincere mapping | pattern-match everything as L4; becomes ideology-critique; diagnostic stance collapses |

**failure mode shared across settings:** the analyst lets the dial *drift* during the pass, starting symmetric and ending charitable-toward-ingroup. counter this by running the counter-reading (step 5) *at the end*, when the temptation to launder is strongest.

### dial 3 — scope

| setting | behavior | failure mode |
|---|---|---|
| **text-local** *(default)* | only what's on the page; no assumed faction knowledge | miss shibboleth moves that require discourse context to see |
| **discourse-context** | includes known faction codes, scissor-cycle context, vocabulary-capture history | "galaxy-brain" reading; attributing moves the author couldn't reasonably have made |

always state the scope. if `discourse-context`, cite the specific context you're assuming.

### dial 4 — verdict suppression

| setting | behavior | failure mode |
|---|---|---|
| **diagnosis-only** *(default)* | stop at the tagged report; no "net effect" line | user may want a bottom line; refuses to give one |
| **net-effect** | append one evaluative sentence: "the net effect of this passage on public alignment is..." | smuggles in the analyst's values; violates the diagnostic stance unless explicitly opted in |

*note:* output mode is **not a dial**. Both the structured analysis and the prose briefing are always produced. The briefing is always derived from the analysis — Part 1 is run before Part 2, always, because a briefing written without the structured pass behind it drifts toward op-ed.

---

## process (step by step)

### step 0 — triage

ask: *is this passage doing alignment work at all?*

criteria for competitive-sensemaking work being present (any one sufficient):
- passage references, uses, or contests a **vocabulary term** with faction valence
- passage makes a **normative claim** about a collective (what "we" should do / who "they" are)
- passage **frames a disagreement** — asserting not just a fact but a reading of why the other side holds the opposing view
- passage deploys a term or phrase that **carries social accounting** beyond its denotation

if none apply: emit `[NO-COMPETITIVE-WORK-DETECTED]`, briefly state why, stop.

### step 1 — fingerprint

one-sentence, **literal-minded** restatement of what the passage propositionally says. no spin, no reading between lines. this is the L1-charitable gloss. if you can't write it without editorializing, that is itself a finding.

### step 2 — fact ledger

borrowing the idiom from `rhetoricize`:

- **facts:** atomic factual commitments the passage makes (would be falsifiable if probed)
- **normatives:** value claims / ought-statements
- **non-claims:** things the passage conspicuously does *not* assert while implying
- **drift budget:** how much semantic drift from the literal gloss is permissible in your analysis (keep low)

### step 3 — run the 7 axes

for each axis 1–7:

1. name the move (or `[NOT-APPLICABLE]`)
2. assign the tag
3. **quote the fragment** that evidences it (verbatim, short)
4. note confidence `[HIGH]` / `[MED]` / `[LOW]`
5. note liveness `[LIVE]` / `[DORMANT]`

do not force-fit. an empty axis is data.

### step 4 — alignment payload

emit the `[ALIGNMENT-PAYLOAD]` block with all four sub-fields populated:
- direction
- beneficiary
- casualty
- vocabulary-delta

if the passage is doing competitive-sensemaking work, *some* payload exists. if you can't name it, either the move is weaker than you think or you're reading through too partisan a lens — downgrade confidence and note it.

### step 5 — counter-reading (charity check)

write a short paragraph: *what would this passage look like if read as sincere L1 mapping — the author honestly trying to describe the territory?* then name the **delta** between that reading and your diagnosis.

this step is the neutrality safety valve. run it *after* the diagnosis, not before, so the diagnosis stays uncolored and the charity gets its own dedicated pass.

if the counter-reading is indistinguishable from your diagnosis, the diagnosis was probably uncontroversial — fine. if it differs sharply, either the diagnosis is over-reading or the passage is genuinely doing L3/L4 work. the delta itself is diagnostic output.

### step 6 — caveats

- confidence band for the overall reading
- which dial settings were used
- scope limits (what this pass did and didn't look at)
- **flip conditions:** what single piece of new information would most change the diagnosis

### step 7 — briefing (always)

convert the structured analysis into a prose briefing that a reader unfamiliar with this skill's framework can comprehend. this step is mandatory — every invocation of alignment-briefing produces Part 2. the briefing is a **translation**, not a fresh analysis: every claim in it must be traceable to a finding in part 1.

if step 0 triaged the passage out, Part 2 is a one-line briefing stating that the passage is not doing competitive-sensemaking work and briefly why — nothing further.

translation rules:

- **no analysis-specific jargon whatsoever.** the briefing must not contain: tag syntax (`[SCISSOR]`, `[L4]`, `[ABSTRACTION-CAPTURE]`, etc.); level labels (`L1`, `L2`, `L3`, `L4`); axis names ("axis 4," "simulacrum level," "map-territory drift"); framework terms ("abstraction-capture," "faction-bid," "framing-lock," "shibboleth," "scissor," "pseudo-scissor," "register-switch," "alignment payload," "hyperreal," "territory-ref," "map-on-map," "mistake-frame," "conflict-frame"); or any meta-reference to "the analysis," "the axes," or "the framework." a reader who has never seen this skill should be unable to tell one exists.
- **translate each concept into plain description:**
  - *scissor / pseudo-scissor* → "engineered to split readers into two camps that find each other's reading unintelligible" / "divisive in shape but without the clean split"
  - *L1* → "sincere description of the world"
  - *L2* → "lying within a game that still treats description as load-bearing"
  - *L3* → "statements functioning as coordination calls rather than propositions; arguments-as-soldiers"
  - *L4* → "pure positional moves with no underlying referent; speech as pure positioning"
  - *map-territory drift / hyperreal* → "referring to other commentary rather than to the world itself"
  - *abstraction-capture* → "quietly binding a prestige term to a specific policy bundle so that defending one defends the other"
  - *framing-lock* → "installing a binary or category that forecloses alternative readings"
  - *faction-bid / faction-mark / shibboleth* → "building or rallying a coalition" / "signaling membership in one" / "using a phrase whose primary job is identification"
  - *mistake-frame / conflict-frame / register-switch* → "treating disagreement as correctable error" / "treating it as a power conflict" / "sliding between the two"
  - *alignment payload* → "what it is trying to shift in public understanding"
- keep quoted evidence in its existing form (quotes survive translation unchanged)
- retain confidence calibration, but in prose ("high confidence that…", "medium confidence on…") — without referencing axes or tags
- retain the counter-reading as an honesty check ("the charitable reading is X; the delta is Y")
- do not add new findings the analysis didn't contain
- keep it terse — the briefing should be shorter than the analysis, not longer
- write for an intelligent generalist who does not share the author's framework or the analyst's

**jargon audit (mandatory pre-emit step):** before emitting the briefing, scan it for any term from the forbidden list above. if any appear, rewrite in plain English. a briefing that includes even a single `[TAG]` or level-label (`L1`, `L2`, `L3`, `L4`) has failed the translation and must be revised.

the briefing's canonical section order:

1. **What it is.** One paragraph: who wrote it, where, and the surface argument.
2. **The surface argument.** One short paragraph — what the passage claims on its face.
3. **What it is actually doing.** The 2–4 moves that matter most from the analysis, each named in plain language with quoted evidence. This is the payload of the briefing.
4. **Who gets strengthened, who gets weakened.** A compressed prose version of the alignment-payload block: advantaged, disadvantaged, vocabulary shifts.
5. **Posture.** Mistake-frame vs. conflict-frame, any register-switch, any scissor shape — all in plain language.
6. **What is conspicuously missing.** The non-claims from the fact ledger, translated into "here is what you would expect this piece to address and it doesn't." Label these as structural to the rhetorical role, not as failures.
7. **How confident to be in this read.** Calibration in prose plus the single flip condition that matters most.
8. **Bottom line.** One short paragraph the reader can carry into a meeting: what to take seriously from the piece, and what to notice so that assent to the data does not drag assent to the conclusion.

the briefing section headings should be written as natural English (e.g. "What It Is Actually Doing"), not with the tag-name form. assume the reader has not read part 1.

---

## output schema

the output is a single markdown document with a specific top-matter format.

**header (required, in this exact order):**

```markdown
[Skip to briefing](#part-2--briefing)

# alignment-briefing — "<passage title or short descriptor>"

**Source:** <author(s), venue, date, full title>

**Dials:** depth=... charity=... scope=... verdict=...

---
```

two rules about the header:

- **no "Skill:" line.** Do not include a `**Skill:**` metadata line. The H1 already names the skill; a separate Skill line is redundant.
- **the "Skip to briefing" link is the very first line of the document** — above the H1, above the source block, above everything. it is a markdown link pointing at the anchor of the Part 2 heading (`#part-2--briefing` for GitHub-flavored markdown auto-anchors from `# PART 2 — BRIEFING`). if the rendering target uses different anchor conventions, adjust accordingly, but the link is always present and always first.

**body (the analytical content) uses this schema:**

```
# PART 1 — ANALYSIS

PASSAGE FINGERPRINT
  [one sentence, literal]

FACT LEDGER
  facts: ...
  normatives: ...
  non-claims: ...
  drift budget: low | med | high

MOVES

  [axis 1 — scissor work]
    tag: [SCISSOR] | [PSEUDO-SCISSOR] | [NOT-APPLICABLE]
    evidence: "<quoted fragment>"
    confidence: [HIGH|MED|LOW]    liveness: [LIVE|DORMANT]
    note: ...

  [axis 2 — simulacrum level]
    dominant: [L1|L2|L3|L4]
    secondary: [L1|L2|L3|L4] or none
    evidence: "<quoted fragment>"
    confidence: ...    liveness: ...
    note: ...

  [axis 3 — map-territory drift]
    ...

  [axis 4 — strategic abstraction]
    ...

  [axis 5 — faction work]
    ...

  [axis 6 — mistake / conflict register]
    ...

  [axis 7 — alignment payload]
    direction: ...
    beneficiary: ...
    casualty: ...
    vocabulary-delta: ...

COUNTER-READING
  sincere-L1 gloss: ...
  delta from diagnosis: ...

CAVEATS
  dials used: depth=... charity=... scope=... verdict=...
  confidence: ...
  flip conditions: ...

[optional if verdict=net-effect]
NET EFFECT
  one sentence.

[always — Part 2 is mandatory; the `# PART 2 — BRIEFING` heading is the anchor target of the "Skip to briefing" link in the header]
# PART 2 — BRIEFING

  ## What It Is
    [one paragraph: who wrote it, where, surface argument.]

  # The Surface Argument
    [one short paragraph in plain English.]

  # What It Is Actually Doing
    [2–4 subsections, each named in plain language,
     each containing quoted evidence and a short explanation.]

  # Who Gets Strengthened, Who Gets Weakened
    - Advantaged: ...
    - Disadvantaged: ...
    - Vocabulary shifts: ...

  # Posture
    [mistake-frame / conflict-frame / register-switch / scissor shape,
     all in plain language — no tag names, no level labels.]

  # What Is Conspicuously Missing
    [the non-claims from the fact ledger, translated.]

  # How Confident to Be in This Read
    [prose calibration + single most important flip condition.]

  # Bottom Line
    [one short paragraph the reader can carry into a meeting.]
```

---

## quality checklist

- [ ] step 0 was actually run — either a triage-out or a stated reason to proceed
- [ ] every tag is backed by a *quoted* fragment, not paraphrase
- [ ] every axis has an entry, including `[NOT-APPLICABLE]` where nothing was found
- [ ] counter-reading was written *after* diagnosis and names a non-trivial delta
- [ ] alignment payload names both a beneficiary *and* a casualty (not just one)
- [ ] drift budget stayed low — the diagnosis is traceable to the literal text
- [ ] confidence is calibrated, not uniformly HIGH or uniformly LOW
- [ ] the analyst's own priors about who is right are not in the output
- [ ] flip conditions are stated (what evidence would flip the reading)

**header checks:**

- [ ] the very first line of the document is a markdown "Skip to briefing" link pointing at the Part 2 anchor
- [ ] there is no `**Skill:**` metadata line in the header
- [ ] the header contains `**Source:**` and `**Dials:**` lines only (in that order, after the H1)

**Part 2 checks (always required, since the briefing is always produced):**

- [ ] the briefing passes the jargon audit: no tag syntax, no level labels (L1/L2/L3/L4), no axis names, no framework terms from the forbidden list, no meta-reference to "the analysis" or "the framework"
- [ ] every claim in the briefing traces to a finding in the structured analysis (no new material invented in translation)
- [ ] the briefing is shorter than the analysis, not longer
- [ ] quoted evidence is preserved verbatim in the briefing
- [ ] a reader with no exposure to this skill can read the briefing end-to-end and not notice a framework exists behind it
- [ ] triage-out passages have a one-line Part 2, not a full briefing

---

## anti-patterns / failure modes

- **simulacrum-creep.** tagging everything interesting as `[L4]`. most political writing is `[L3]` — coordinative, arguments-as-soldiers — without reaching the pure-positional self-awareness of `[L4]`.
- **scissors everywhere.** real scissors are rare and structurally specific. most divisive statements are `[PSEUDO-SCISSOR]` — polarizing shape without the clean irreconcilable-readings property.
- **faction-code ≠ bad faith.** shibboleths and faction-marks are structural features of group communication. tagging `[SHIBBOLETH]` is a description, not an indictment. the passage can be sincere and still factionally coded.
- **conflict-frame moralism.** it is not a flaw for a passage to operate in `[CONFLICT-FRAME]`. conflict theory is sometimes correct. the diagnostic finding is the register, not a demerit.
- **abstraction-capture inflation.** every argument uses vocabulary. tag `[ABSTRACTION-CAPTURE]` only when the passage is *installing or contesting* the definition, not merely using one.
- **charity drift.** starting symmetric and ending ingroup-friendly. counter with: run the counter-reading last, and write the delta even when it embarrasses the diagnosis.
- **triage refusal.** forcing a reading onto a passage that is genuinely L1/technical/private. `[NO-COMPETITIVE-WORK-DETECTED]` is a first-class output.
- **galaxy-brained discourse-context.** attributing moves the author couldn't plausibly have made; requires `scope=discourse-context` *and* named, specific context.
- **net-effect smuggling.** sneaking an evaluative line into the diagnosis section rather than under the explicit `net-effect` block.

---

## worked examples

### example 1 — scissor-heavy culture-war tweet

**passage:**
> "If you still think it's 'just a policy disagreement,' you're either lying or you haven't been paying attention. They've told us who they are. Believe them."

**diagnosis (medium, symmetric, text-local):**

- FINGERPRINT: "people who describe the current disagreement as merely about policy are either dishonest or uninformed; the opposing group's intentions are clear and have been stated."
- FACT LEDGER: facts: near-zero (no specific referent); normatives: "you should stop treating this as policy disagreement"; non-claims: *who* "they" are, *what* they said.
- [axis 1 SCISSOR] `[SCISSOR] [HIGH] [LIVE]` — evidence: "you're either lying or you haven't been paying attention." the construction makes dissent from the reading unintelligible-as-good-faith.
- [axis 2 SIM] dominant `[L3]`, secondary `[L4]` `[HIGH]` — evidence: "Believe them." The imperative functions as a coordination call, not a proposition about beliefs.
- [axis 3 DRIFT] `[MAP-ON-MAP] [MED]` — referent is a prior interpretive claim about the opposition, not a first-order fact about the world.
- [axis 4 ABSTRACT] `[FRAMING-LOCK] [MED]` — the binary "policy disagreement vs. knowing-who-they-are" is installed as exhaustive.
- [axis 5 FACTION] `[FACTION-BID]` + `[FACTION-MARK]` `[HIGH] [LIVE]` — "you" is hailed into the knowing in-group; "they" is consolidated.
- [axis 6 REGISTER] `[CONFLICT-FRAME] [HIGH]` — disagreement is treated as dishonesty or inattention, not correctable error.
- [axis 7 ALIGNMENT-PAYLOAD]
  - direction: weaken "disagreement is about policy" frame; strengthen "opponent has bad intentions" frame
  - beneficiary: in-group coalition cohesion
  - casualty: mistake-frame interlocutors of any affiliation; anyone advocating de-escalation
  - vocabulary-delta: "policy disagreement" acquires a dismissive connotation (naïve/complicit)

**counter-reading:** sincere-L1 gloss: "I believe my opponents have made their intentions clear and it is epistemically irresponsible to continue treating this as a policy dispute." delta: the sincere reading would name what was said, by whom, when. the omission is what moves this from L1 to L3/L4.

**caveats:** confidence HIGH on scissor/faction; MED on framing-lock (could be read as summary rather than installation). flip condition: the preceding tweet in a thread that names specific statements and speakers would move this substantially toward L1.

---

### example 2 — policy op-ed quietly doing abstraction-capture under mistake-frame surface

**passage (excerpted):**
> "The evidence is now unambiguous: resilience — the capacity of communities to absorb shocks and continue functioning — is the single most important policy outcome. Any serious plan must be evaluated on whether it builds resilience."

**diagnosis (medium, symmetric, text-local):**

- FINGERPRINT: "evidence shows resilience is the most important policy outcome; plans should be evaluated on whether they build it."
- FACT LEDGER: facts: an implicit empirical claim about evidence; normatives: "policy must be evaluated on resilience"; non-claims: what specifically counts as "absorbing shocks," what trade-offs are accepted.
- [axis 1 SCISSOR] `[NOT-APPLICABLE]`
- [axis 2 SIM] dominant `[L1]`, secondary `[L3]` `[MED]` — presents as sincere, but the evaluative frame does coordinative work.
- [axis 3 DRIFT] `[TERRITORY-REF] [MED]` — appeals to "evidence," though the evidence isn't cited.
- [axis 4 ABSTRACT] `[ABSTRACTION-CAPTURE] [HIGH] [LIVE]` — evidence: "resilience — the capacity of communities to absorb shocks and continue functioning." the parenthetical installs a definition that quietly privileges stasis-friendly policies over transformation-oriented ones.
- [axis 5 FACTION] `[NOT-APPLICABLE]` or `[FACTION-BID] [LOW]` — bid is soft; "serious plan" is mild gatekeeping.
- [axis 6 REGISTER] `[MISTAKE-FRAME]` surface with `[REGISTER-SWITCH] [MED]` — frames as evidence-driven but the operative move is definitional, not empirical.
- [axis 7 ALIGNMENT-PAYLOAD]
  - direction: strengthen policies legible as "resilience-building"; weaken policies framed as transformation, redistribution, or acceptable-loss
  - beneficiary: incumbents whose assets are shock-absorbed rather than reallocated
  - casualty: reformers whose plans accept disruption as the point
  - vocabulary-delta: "resilience" becomes the default evaluative axis; alternative axes (equity, speed, transformation) require extra justification

**counter-reading:** sincere-L1 gloss: "empirical work supports resilience as a key policy metric and i'm advocating for its use." delta: the sincere reading would be unchanged by which definition of resilience is installed; this passage tucks a specific definition into the premise. the abstraction-capture is the active ingredient.

**caveats:** confidence MED overall — op-ed could be read as informal exposition. flip condition: if the author elsewhere explicitly considers competing definitions, downgrade the capture tag to `[LOW]`.

---

### example 3 — technical passage, triaged out

**passage:**
> "In finite groups, Lagrange's theorem states that the order of every subgroup divides the order of the group. This follows from partitioning the group by cosets of the subgroup."

**diagnosis (medium, symmetric, text-local):**

- step 0 triage: no vocabulary term with faction valence; no normative claim about a collective; no framing of disagreement; terms carry no extra-denotational social accounting.
- `[NO-COMPETITIVE-WORK-DETECTED]`
- stop.

caveat: if this passage were embedded in a piece arguing "mathematics is apolitical" or "mathematics is inherently political," the *framing* around this passage would be competitive — but the passage itself isn't.

---

## integration with other skills

alignment-briefing composes. typical chains:

- **upstream: `rhetoricize`** — if you want lexical-level / syntactic spin analysis before the move-level analysis
- **upstream: `excavate`** — dig the assumption stack a faction needs to be true for the move to land
- **upstream: `rhyme`** — find what prior discourse-move the current passage structurally echoes
- **downstream: `antithesize`** — given the diagnosed alignment-payload, generate the rival alignment bid (symmetric pressure test)
- **downstream: `synthesize`** — when running alignment-briefing on multiple competing passages, synthesize a frame that explains each one's move
- **sibling: `negspace`** — what the passage conspicuously *doesn't* say about its own faction stakes; alignment-briefing diagnoses the move, negspace finds the missing disclosure

quick decision: if you're asking "how is this passage spun?" use `rhetoricize`. if you're asking "what hidden premises does this need?" use `excavate`. if you're asking "what is this passage *trying to do to us*, and how do I brief someone on it?" — that's alignment-briefing.

---

## source grounding

alignment-briefing uses a specific vocabulary drawn from four source streams. brief glosses so the skill is self-contained:

- **scissor statement** (Scott Alexander; elaborated in *Alignment Gone Strange* Part 4) — a statement engineered or selected such that one population reads it as obviously true and another as obviously false, with each side finding the other's reading unintelligible. the canonical example is "The Dress." scissors are weaponized by algorithms that preferentially surface high-engagement splits.
- **simulacrum levels 1–4** (Hoffman, *Simulacra and Subjectivity*, after Baudrillard and J. Taylor) —
  - L1: *Objectivity as Subject.* "words were used to maintain shared accounting... describe reality intersubjectively in order to build shared maps."
  - L2: *Objectivity as Object.* "taking the shared map as an object to be manipulated... the map drifts from reality."
  - L3: *Relating as Subject (power relation / ritual).* "the map becomes a sort of command language for coordinating actions and feelings... arguments become soldiers." claims function as calls-to-coordination; literal truth is secondary.
  - L4: *Relating as Object (postmodernity).* "the pseudostructure itself becomes perceptible as an object that can be manipulated... all assertions are nothing but moves in an ever-shifting game."
  - Zack Davis's illustrative case: "'God doesn't exist' isn't a nonexistence claim about deities; it's a bid to undermine the monotheism coalition and give their stuff to the atheism coalition" — to a speaker who reads all speech as L4, this is how L1 mapping looks.
- **map-territory drift / hyperreality** (*Alignment Gone Strange* Parts 2 and 4) — as persuasion becomes adversarial, maps stop pointing at territory and start pointing at other maps; eventually the game is entirely among maps-of-maps.
- **strategic abstraction** (*Alignment Gone Strange* Part 1) — deliberate control of the conceptual layer (definitions, vocabularies, framings) as meta-strategy. winning the definition pre-decides many future arguments.
- **mistake theory vs. conflict theory** (Scott Alexander; *Postmodernism for STEM Types*) — mistake-theory treats disagreement as factual error fixable by argument; conflict-theory treats disagreement as interest-conflict requiring power moves. the sliding between them is its own move.
- **faction work and discursive warfare** (*Discursive Warfare and Faction Formation*) — discursive tactics produce and maintain factional identity. shibboleths, faction-bids, and faction-marks are the mechanisms.
- **PvP epistemology / HyperAmericana** (*Alignment Gone Strange* Part 4) — the end state where all public discourse is adversarial, all assertions are positional, and the operative question shifts from "is it true" to "whose side does it build."

---

## lexicon (quick reference)

| term | one-line gloss |
|---|---|
| scissor statement | cleaves audience into camps that find each other's readings unintelligible |
| simulacrum L1 | sincere mapping of territory |
| simulacrum L2 | lying within the mapping game |
| simulacrum L3 | arguments-as-soldiers; claims as coordination calls |
| simulacrum L4 | pure positional play; pseudo-correspondence itself is gamed |
| map-territory drift | referent shifts from world to prior maps |
| hyperreality | maps-of-maps-of-maps; no grounding test available |
| strategic abstraction | controlling the conceptual layer to prejudge future disputes |
| abstraction-capture | installing a definition that advantages a position |
| framing-lock | installing a category that constrains what arguments can be formed |
| mistake-frame | disagreement = factual error, fixable by argument |
| conflict-frame | disagreement = interest conflict, resolved by power |
| faction-bid | recruiting / rallying a coalition |
| faction-mark | performing in-group membership |
| shibboleth | phrase whose primary function is identification, not information |
| alignment payload | the shift in public mindshare the passage bids for |
| PvP epistemology | the end-state where all speech is adversarial positioning |

---

## meta-note

alignment-briefing is **about the move, not the mover**. a passage can do competitive-sensemaking work without the author being cynical — most L3 writing is sincere participation in a coordination game. the skill names the shape of the play. whether that shape is good, bad, or warranted is a separate question, deliberately outside the diagnostic stance. if you want the evaluative answer, opt into `verdict=net-effect` and own the judgment explicitly.
