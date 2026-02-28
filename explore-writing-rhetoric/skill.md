---
name: explore-writing-rhetoric
description: Analyze the rhetoric of a passage by marking up text with interstitial **[bold bracket]** annotations identifying classical and modern rhetorical devices, followed by a glossary with definitions and pronunciation guides for non-English terms. Use when asked to analyze rhetoric, identify rhetorical devices, mark up rhetorical figures, analyze prose style, or perform syntactic analysis following Virginia Tufte's methodology. Also use when user pastes a passage and asks for rhetorical markup, or requests a public domain passage for analysis.
---

# Rhetorical Analysis

Analyze passages by inserting **[bold bracket]** annotations identifying rhetorical devices inline with the text, followed by a glossary of all terms used.

## Workflow

1. If user requests a passage by name, search for it (assume public domain)
2. Read the full passage to grasp its rhetorical strategy
3. Mark up the text with inline annotations
4. Append the glossary with all devices identified

For comprehensive device definitions and pronunciations, consult `references/devices.md`.

## Inline Markup Format

Insert device identifications immediately after the word, phrase, or clause exhibiting the device:

> To be, or not to be **[antithesis]**—that is the question **[hypophora: question posed and answered by speaker]**

For devices spanning multiple words, place the annotation at the end of the construction:

> It was the best of times, it was the worst of times **[anaphora: "it was"; antithesis: "best/worst"]**

When multiple devices overlap, combine them in a single bracket or use sequential brackets as clarity demands.

## Device Categories

### Classical Tropes (Figures of Thought)

**Repetition patterns:**
- anaphora (repetition at start)
- epistrophe (repetition at end)
- symploce (anaphora + epistrophe combined)
- anadiplosis (end of one clause begins next)
- epanalepsis (beginning repeated at end)
- polyptoton (same root, different forms)

**Structural patterns:**
- chiasmus (ABBA structure)
- antithesis (contrasting ideas in parallel)
- isocolon (parallel clauses of equal length)
- tricolon (three parallel elements)
- climax/auxesis (ascending order of importance)
- anticlimax/bathos (descending, often for irony)

**Comparison & substitution:**
- metaphor, simile, analogy
- metonymy (substitution by association)
- synecdoche (part for whole or reverse)
- personification/prosopopoeia
- apostrophe (address to absent person/thing)

**Amplification & diminution:**
- hyperbole (exaggeration)
- litotes (understatement via negation)
- meiosis (understatement)
- pleonasm (redundancy for emphasis)

**Omission & compression:**
- ellipsis (omission of expected words)
- zeugma (one word governing unlike elements)
- syllepsis (zeugma with semantic shift)
- asyndeton (omission of conjunctions)
- polysyndeton (excess of conjunctions)
- brachylogia (extreme compression)

**Sound devices:**
- alliteration, assonance, consonance
- onomatopoeia
- homoioteleuton (similar endings)

**Argument & address:**
- rhetorical question/erotema
- hypophora (question posed and answered)
- aporia (feigned doubt)
- praeteritio/paralipsis (mentioning by claiming not to)
- enthymeme (implied premise)

### Syntax as Style (Tufte Methodology)

**Sentence architecture:**
- periodic sentence (main clause delayed to end)
- cumulative/loose sentence (main clause first, modifiers follow)
- balanced sentence (parallel independent clauses)
- freight-train sentence (coordinate clauses linked by conjunctions)

**Modification strategies:**
- left-branching (modifiers before head)
- right-branching (modifiers after head)
- mid-branching/embedding (modifiers interrupt)
- absolute phrase (noun + participle, grammatically independent)
- appositive (noun phrase renaming another)
- participial phrase (verb-derived modifier)

**Voice, tense, aspect:**
- passive voice (agent backgrounded)
- progressive aspect (ongoing action)
- perfect aspect (completed with present relevance)
- historical present (present tense for past events)

**Coordination & subordination:**
- parataxis (coordinate, minimal hierarchy)
- hypotaxis (subordinate, hierarchical)
- syndetic (with conjunction)
- asyndetic (without conjunction)

**Syntactic effects:**
- inversion (non-standard word order)
- fronting (moving element to sentence start)
- cleft sentence ("it was X that...")
- extraposition (moving element to end)
- compression (dense packing of information)
- expansion (elaborative extension)

## Glossary Format

After the marked passage, include:

```
## Glossary

**device-name** (pronunciation if non-English): Definition. Example if helpful.
```

Sort alphabetically. Include pronunciation for Greek and Latin terms using IPA or phonetic respelling.

## Example

**Input:** Analyze the rhetoric of this passage from Churchill:

"We shall fight on the beaches, we shall fight on the landing grounds, we shall fight in the fields and in the streets, we shall fight in the hills; we shall never surrender."

**Output:**

We shall fight on the beaches, **[anaphora: "we shall fight"]** we shall fight on the landing grounds, we shall fight in the fields and in the streets, we shall fight in the hills **[climax: ascending from beaches through streets to hills; isocolon: parallel clause lengths; polysyndeton: repeated "and" in "fields and in the streets"]**; we shall never surrender **[epistrophe: final clause varies the pattern; litotes-adjacent: "never surrender" rather than "always fight"]**. **[Sentence architecture: freight-train cumulative sentence; paratactic coordination builds momentum]**

## Glossary

**anaphora** (uh-NAF-er-uh, Greek ἀναφορά): Repetition of a word or phrase at the beginning of successive clauses.

**climax** (Greek κλῖμαξ, "ladder"): Arrangement of words, phrases, or clauses in order of increasing importance.

**epistrophe** (eh-PIS-troh-fee, Greek ἐπιστροφή): Repetition at the end of successive clauses; the reverse of anaphora.

**freight-train sentence**: A cumulative sentence built from coordinate clauses linked in series, creating forward momentum.

**isocolon** (eye-SOH-koh-lon, Greek ἰσόκωλον): Parallel structure with clauses of approximately equal length.

**litotes** (LYE-toh-teez, Greek λιτότης): Understatement by negating the contrary; here "never surrender" approaches this by avoiding direct positive assertion.

**parataxis** (PAIR-uh-TAK-sis, Greek παράταξις): Coordination of clauses without subordination, creating a sense of equality among ideas.

**polysyndeton** (pol-ee-SIN-deh-ton, Greek πολυσύνδετον): Deliberate use of multiple conjunctions in close succession.
