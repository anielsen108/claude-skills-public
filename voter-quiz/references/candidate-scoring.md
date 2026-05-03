# Candidate Scoring

Detailed guidance for the CANDIDATES object.

## Candidate Object Format

```javascript
{
  name: 'Jared Huffman',
  party: 'D',                          // see party codes below
  desc: 'U.S. Representative (incumbent)',  // ballot designation
  viable: true,                        // optional, defaults to true
  s: {                                 // axis scores, -100 to +100
    progressive: 65,
    taxServices: 60,
    transit: 70,
    environment: 80,
    yimby: 30,
    safetyHawk: -20
  }
}
```

For nonpartisan races (judges, school board, county supervisor, etc.), set `party: ''` (empty string). The artifact won't show party labels for these.

## Party Codes

The template's `partyLabel()` function recognizes:

| Code   | Display          |
|--------|------------------|
| `D`    | Democratic       |
| `R`    | Republican       |
| `G`    | Green            |
| `P&F`  | Peace and Freedom |
| `L`    | Libertarian      |
| `AI`   | American Independent |
| `NPP`  | No Party Preference |
| `''`   | (no party shown) |

If a state uses different party labels, extend `partyLabel()` in the template.

## Scoring the Six Standard Axes

Use a -100 to +100 scale. Most viable candidates fall in -75 to +75.

### `progressive`

The big one. Measures left/right ideology.

| Score    | Profile |
|----------|---------|
| +60 to +80 | Bernie/AOC-style progressive. Strong support for single-payer, wealth tax, climate action, criminal justice reform. |
| +40 to +60 | Standard progressive Democrat. Supports most progressive priorities but more moderate on taxes/regulation. |
| +20 to +40 | Mainstream Democrat. Pro-choice, pro-climate, but cautious on economic policy. |
| 0 to +20   | Centrist/moderate Democrat. Pro-business, fiscally cautious. |
| -20 to 0   | Independent/conservative Democrat or moderate independent. |
| -40 to -20 | Mainstream Republican. Lower taxes, deregulation, traditional positions. |
| -60 to -40 | Standard conservative Republican. Pro-life, anti-immigration, pro-police. |
| -80 to -60 | Hard conservative / MAGA-aligned. Trump endorsements, sheriff/military background. |

### `taxServices`

How much they support taxing-and-spending.

- +60 to +80: Strong support for new taxes to fund expanded services
- +40 to +60: Generally supportive of public investment, willing to raise taxes
- +20 to +40: Mixed — supportive of some programs, resistant to broad tax increases
- 0 to +20: Status quo
- -40 to 0: Skeptical of new spending, prefers cuts
- -60 to -40: Anti-tax, pro-shrinking-government
- -80 to -60: Hard libertarian or anti-government

### `environment`

Environmental protection priority.

- +70 to +80: Climate-focused candidates, environmental lawyers, dedicated organizers
- +50 to +70: Strong environmentalist, pro-regulation
- +30 to +50: Generally pro-environment but balances with business interests
- 0 to +30: Status quo
- -30 to 0: Skeptical of environmental regulation
- -60 to -30: Pro-business, anti-regulation
- -80 to -60: Climate skeptic, drilling/extraction advocate

### `safetyHawk`

Police-and-prosecution stance.

- +60 to +80: Sheriff, police union endorsements, "back the blue"
- +30 to +60: Tough-on-crime, pro-police-funding
- 0 to +30: Pro-police but not focused
- -30 to 0: Mixed signals
- -60 to -30: Reform-minded, supports oversight
- -80 to -60: Defund/abolish, alternatives-to-policing focus

### `yimby`

Pro-density housing preference.

- +60 to +80: Strong YIMBY, pro-development, pro-density
- +30 to +60: Supports more housing including denser zoning
- 0 to +30: Wants more housing but cautious about zoning changes
- -30 to 0: Skeptical of density, neighborhood-character-focused
- -60 to -30: Strong NIMBY, anti-growth, preservationist
- -80 to -60: Hard preservationist, no-growth

### `transit`

Transit/bike vs roads/cars.

- +60 to +80: Transit advocate, pro-rail, pro-bike, anti-highway
- +30 to +60: Supports transit and pedestrian infrastructure
- 0 to +30: Mixed support
- -30 to 0: Roads-first
- -60 to -30: Strong highway/car prioritization
- -80 to -60: Anti-transit, pro-highway-expansion

## Viability Rules

Mark `viable: false` if any of these apply:

### Always non-viable
- **Third-party candidates in major races** (Peace & Freedom, Green, Libertarian, American Independent) when there are clear D/R alternatives. These never win California top-two primaries in major races.
- **Dropped-out candidates** — confirmed via news that they exited the race
- **Candidates with no statement AND no elected position** — typically just names that filed paperwork
- **"Joke" candidates** — known protest candidates with no campaign

### Often non-viable (use judgment)
- **Lowest-tier candidates in crowded primaries** — e.g., in a 60-candidate Governor race, only ~10 are realistically viable
- **Candidates with no fundraising and no endorsements** in races where institutional backing matters
- **Major-party candidates running purely as protest** with zero name recognition

### Always viable
- **Incumbents** (always)
- **Candidates with significant fundraising or endorsements**
- **Candidates with elected experience** (current or former officeholders)
- **Anyone who has polled above ~5% in major races**

### When in doubt
- For small races (Sup, Assembly, Senate with 2-3 candidates), all candidates are usually viable. Don't filter.
- For statewide races with crowded fields, be selective. Aim for the realistic top 5-10.

## How to Research Candidates

For each candidate:

1. **Search their name + the office** to find their campaign site, news coverage, endorsements
2. **Check Ballotpedia** for voting records, prior offices, key positions
3. **Look at endorsements** — labor unions (progressive signal), chambers of commerce (moderate/conservative signal), specific advocacy groups (issue-specific signals)
4. **Read their candidate statement** in the official Voter Information Guide
5. **For incumbents, check their voting record** on relevant bills

Don't spend forever on each candidate. For a primary with 60 governor candidates, spend 80% of research time on the 10 viable ones, 20% on quick scoring of the rest (so they can be rejected via viable: false).

## CANDIDATES Object Structure

Organize by race key. Use these conventions:

```javascript
const CANDIDATES = {
  // Federal
  cd2: [...],          // US House, district 2
  cd1: [...],          // US House, district 1
  
  // State partisan
  governor: [...],
  ltgov: [...],
  sos: [...],          // Secretary of State
  controller: [...],
  treasurer: [...],
  ag: [...],           // Attorney General
  insurance: [...],    // Insurance Commissioner
  boe2: [...],         // State Board of Equalization, district 2
  
  // State legislature
  ss2: [...],          // State Senate, district 2
  ad12: [...],         // State Assembly, district 12
  
  // Nonpartisan state
  suptpi: [...],       // Superintendent of Public Instruction
  
  // County
  sup2: [...],         // County Supervisor, district 2
  
  // Local (city, school board, etc.) — name freely
  citycouncil: [...],
  schoolboard: [...],
};
```

Race keys are referenced from the rendering code, so use clear names.

## UNCONTESTED Object

For seats with only one candidate filed (no race), use:

```javascript
const UNCONTESTED = {
  judge10: { 
    name: 'David Kim', 
    desc: 'Superior Court Commissioner — only candidate' 
  },
  csupt: { 
    name: 'Amie Carter', 
    desc: 'County Superintendent of Schools (incumbent) — only candidate' 
  },
  // ...
};
```

These display in the artifact with "(uncontested)" label and no matching logic.

## Sanity Check

Before finalizing CANDIDATES:

- [ ] Every viable candidate has scores on every axis
- [ ] Score ranges are reasonable (no candidate at +100/-100 unless truly extreme)
- [ ] Third-party candidates marked `viable: false`
- [ ] Dropped-out candidates marked `viable: false` AND noted in artifact intro if recently
- [ ] Each contested race has at least 2 viable candidates (otherwise mark uncontested)
- [ ] Party codes are consistent
- [ ] Ballot designations match the official voter guide format

## When Public Data is Limited

For very local races (school board, special district, small-county supervisor), candidate positions may be hard to find. Two options:

1. **Score conservatively from limited info** — use ballot designation, brief news coverage, and any endorsements. Score in the +/-30 range rather than +/-70 (low confidence).
2. **Note this in the artifact disclaimer** — "For very local races, public position data is limited; please read each candidate's statement before voting."

Both is fine. Don't fabricate positions you can't substantiate.
