# Question Design

Detailed guidance for writing the QUESTIONS array.

## The Hard Rule

Every question must ask about a **specific government action**. The user is telling us what they want done, not what they are.

### Forbidden patterns

These contaminate the matching and must be avoided:

| Pattern              | Example                                                         | Why it's bad |
|----------------------|-----------------------------------------------------------------|--------------|
| Identity             | "How would you describe yourself politically?"                  | Lets the test match on self-description rather than policy |
| Issue salience       | "What's your top concern?"                                      | Measures attention, not stance |
| Broad disposition    | "Do you prefer more services or lower taxes?"                   | Too vague — every candidate claims to want both |
| General agreement    | "Is climate change a serious problem?"                          | Doesn't distinguish — almost everyone says yes |
| Affect / values      | "Do you care about working people?"                             | Empty signal |
| Identity proxy       | "Are you concerned about wokeness in schools?"                  | Same problem as identity question |

### Required pattern

Each question names a specific, contested government action. The user can imagine concrete officials voting yes or no on it.

| Action area          | Good question example                                                       |
|----------------------|----------------------------------------------------------------------------|
| Housing              | "Single-family neighborhoods should allow duplexes and ADUs by right."    |
| Environment          | "California should aim for net-zero emissions sooner than 2045."          |
| Transit              | "The SMART train should be expanded and continued."                       |
| Public safety        | "The Sonoma County Sheriff should get more funding."                      |
| Public safety reform | "Mental health teams (not police) should respond to most crisis calls."   |
| Taxes                | "Top earners should pay higher state taxes."                              |
| Healthcare           | "California should move toward single-payer healthcare."                  |
| Education            | "More charter schools should be allowed."                                 |
| Civil rights         | "Voter ID should be required."                                            |
| Immigration          | "Local police should NOT cooperate with federal immigration enforcement." |
| Agriculture          | "Pesticide use in agriculture should be more strictly regulated."         |

Notice the pattern: subject + action verb + specific scope. Not "do you support X?" but "X should happen."

## Question Format

Each question is an object in the QUESTIONS array:

```javascript
{
  c: 'Housing & Cost of Living',     // category for grouping in the quiz
  q: 'More housing should be built in [City].',  // the question text
  d: { yimby: 8, progressive: 2 }    // axis deltas when answered "yes"
}
```

When answered "yes", the deltas are added to the user's score. When answered "no", the deltas are negated.

## Axis Design

**The axes must be derived from this ballot's actual contested ground — not picked from a generic list.**

The whole point of an axis is to discriminate between viable candidates. If two candidates differ on a dimension, you need an axis that captures that difference. If all viable candidates agree on a dimension, an axis for it is wasted. Generic axis lists can hide the work of figuring out what's actually being contested in *this* election.

### Workflow for deriving axes

1. **List the viable candidates** in each contested race (from Step 2 of the main workflow).
2. **For each race, ask: where do these candidates actually differ?** Read endorsements, voting records, public statements. Look for the specific dividing lines — not generic ideology, but the concrete policy disagreements.
3. **Pool the dividing lines across races.** Some will repeat across multiple races (broad ideology, taxes). Some will be race-specific (a specific local zoning fight, a school board curriculum debate).
4. **Pick 4–7 axes that, taken together, discriminate the most viable candidates across the most races.** Drop axes that don't carry their weight; add custom axes whenever a real disagreement isn't captured by anything in the default menu.

### Default menu — starting point only, not canonical

These are the axes that recur across many California elections. Use them as inspiration, but don't reach for them reflexively. Add and drop based on what the actual ballot needs.

```
progressive    — left/right ideological signal
taxServices    — preference for higher taxes / more services
environment    — environmental protection priority
safetyHawk     — police-and-prosecution stance
yimby          — pro-density housing preference
transit        — transit/bike vs roads/cars
```

### Axes you might add for specific races

The right axis to add depends on the race. Some patterns:

| Race feature                                          | Axis to consider           |
|-------------------------------------------------------|----------------------------|
| Sanctuary city debate, immigration prominence         | `immigration`              |
| School board with curriculum fights                   | `educationTraditional`, possibly `parentRights` |
| Strong abortion-rights candidate or measure           | `abortion`                 |
| Big policing-reform divide                            | split `safetyHawk` into `policeFunding` and `prosecutorReform` |
| Major water/growth measure                            | `growth`, `waterPolicy`    |
| Coastal commission seat                               | `coastalDevelopment`       |
| Strong labor/union fight                              | `laborUnion`               |
| Cannabis or psychedelic measure                       | `drugLiberalization`       |
| Rent control, eviction protections                    | `tenantProtection`         |

These are not exhaustive. Whenever you find viable candidates disagreeing on something not captured by your current axes, add a new axis.

### Axes to drop

- **Doesn't discriminate**: every viable candidate scores the same → drop
- **Double-counts another axis**: questions on it always co-vary with questions on another axis → fold them
- **Doesn't appear in any specific race**: an axis floating without races to anchor it → drop
- **Generic feel-good labels**: "trustworthiness," "experience," "leadership" — these aren't policy axes

### Number of axes

4–7 total is the sweet spot. Fewer than 4 and the test under-discriminates. More than 7 and you need too many questions to score each axis reliably (you need 2–4 questions per axis, so 8 axes means at least 16 questions just for axis coverage, leaving no room for race-specific or measure-specific direct mappings).

## Delta Magnitudes

Use these rough magnitudes for axis deltas:

| Strength    | Magnitude | When to use |
|-------------|-----------|-------------|
| Anchor      | 8–10      | Strongest signal for that axis (e.g., "single-payer healthcare" → progressive 10) |
| Strong      | 6–8       | Clear policy stance on the axis |
| Moderate    | 4–6       | Some signal but not the primary axis |
| Weak        | 2–4       | Tangential — secondary axis bonus |

Sum-of-absolute-deltas per axis will determine the maximum possible user score on that axis. Higher = more discrimination.

## Question Pairing for Opposing Signals

For each axis, include questions that signal in BOTH directions. This produces honest scoring for users on both sides.

Example for `safetyHawk`:
- "The Sheriff should get more funding." → safetyHawk +8 (yes pushes hawkish)
- "Mental health teams should respond to crisis calls." → safetyHawk -6 (yes pushes reform)

Without an opposing question, the user can't push the axis in the other direction.

## Number of Questions Per Axis

Aim for **2–4 questions per axis**. Fewer than 2 means the axis can't be reliably scored. More than 4 is usually redundant.

If you find yourself writing 5+ questions on one axis, you're probably re-asking the same question with different wording. Cut to the most distinctive 2–3.

## Local Salience

Prefer questions that name local entities and policies when they distinguish viable candidates:
- "More housing should be built in **Petaluma**." (better than "in California")
- "The **Sonoma County** Sheriff should get more funding." (better than "Sheriffs in general")
- "**The SMART train** should be expanded and continued." (specific to NorCal)
- "**Petaluma and Santa Rosa** should keep their urban growth boundaries." (only ask if the ballot has a UGB measure or a candidate who's notably for/against)

Local naming helps the user feel the question is about their actual ballot, and it forces specificity.

## Direct-Mapping for Ballot Measures

For each ballot measure that has a substantive policy stance behind it, write at least one question that maps directly to it.

Example: Sonoma's Measure B is the SMART tax extension. Question that maps:
- "The SMART train should be expanded and continued." (yes ↔ YES on Measure B)

In the artifact, the DIRECT_MAPPINGS object connects this question to the measure recommendation. The user's direct answer to this question will drive the recommendation, with aggregate scoring as fallback for skipped questions.

Format in the template:
```javascript
const DIRECT_MAPPINGS = [
  {
    measureId: 'measureB',
    question: 'The SMART train should be expanded and continued.',
    yesMeansYes: true   // 'yes' answer → vote YES on the measure
  }
];
```

If a measure is more complex (e.g., a multi-part bond), you may not be able to direct-map. That's fine — fall back to aggregate scoring with a thoughtful explanation.

## Quality Checks

Before finalizing the QUESTIONS array, run through this checklist:

- [ ] Every question is a specific government action (not identity, salience, or general agreement)
- [ ] Every axis has 2–4 questions
- [ ] Each axis has at least one question that signals in each direction
- [ ] Questions name local entities/policies where it sharpens the test
- [ ] Each ballot measure with a substantive stance has at least one direct-mapped question
- [ ] No redundant questions (if two questions always get the same answer from the same person, cut one)
- [ ] Total question count is in the range determined by ballot complexity

## Worked Example: Petaluma 16-Question Set

```javascript
const QUESTIONS = [
  // HOUSING (2)
  { c: 'Housing & Cost of Living', q: 'More housing should be built in Petaluma.',
    d: { yimby: 8, progressive: 2 } },
  { c: 'Housing & Cost of Living', q: 'Single-family neighborhoods should allow duplexes and ADUs by right.',
    d: { yimby: 10, progressive: 4 } },

  // ENVIRONMENT (2)
  { c: 'Environment & Climate', q: 'Wildfire prevention spending should be increased.',
    d: { environment: 6, taxServices: 4 } },
  { c: 'Environment & Climate', q: 'Pesticide use in agriculture should be more strictly regulated.',
    d: { environment: 8, progressive: 4 } },

  // TRANSPORTATION (2) — opposing pair, drives Measure B
  { c: 'Transportation', q: 'The SMART train should be expanded and continued.',
    d: { transit: 10, environment: 4 } },
  { c: 'Transportation', q: 'Highways should be widened to reduce traffic.',
    d: { transit: -6, environment: -4 } },

  // PUBLIC SAFETY (2) — opposing pair
  { c: 'Public Safety', q: 'The Sonoma County Sheriff should get more funding.',
    d: { safetyHawk: 8, progressive: -4 } },
  { c: 'Public Safety', q: 'Mental health teams (not police) should respond to most crisis calls.',
    d: { safetyHawk: -6, progressive: 6 } },

  // ECONOMY & TAXES (1)
  { c: 'Economy & Taxes', q: 'Top earners should pay higher state taxes.',
    d: { progressive: 8, taxServices: 8 } },

  // HEALTHCARE (1)
  { c: 'Healthcare', q: 'California should move toward single-payer healthcare.',
    d: { progressive: 10, taxServices: 6 } },

  // EDUCATION (2) — opposing pair, drives SPI race
  { c: 'Education', q: 'K–12 schools should get more state funding.',
    d: { progressive: 6, taxServices: 6 } },
  { c: 'Education', q: 'More charter schools should be allowed.',
    d: { progressive: -6 } },

  // GOVERNMENT REFORM (1)
  { c: 'Government & Reform', q: 'Voter ID should be required.',
    d: { progressive: -6 } },

  // SOCIAL (1) — Sonoma sanctuary salience
  { c: 'Social Issues', q: 'Local police should NOT cooperate with federal immigration enforcement.',
    d: { progressive: 8 } },

  // AGRICULTURE & LOCAL (2)
  { c: 'Agriculture & Local', q: 'Cannabis cultivation rules should be loosened to allow more growers.',
    d: { progressive: 4 } },
  { c: 'Agriculture & Local', q: 'Dairy farms should face stricter environmental rules.',
    d: { environment: 8, progressive: 4 } },
];
```

Note: 16 questions, 6 axes (progressive, taxServices, environment, transit, yimby, safetyHawk), opposing pairs on the most important axes, two questions specific to Sonoma agriculture. Direct mapping: SMART question → Measure B.
