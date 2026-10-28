<h1 align="center">Lidaxiao Investment Strategy Skill</h1>

<p align="center"><a href="README.md">中文</a> | English</p>

An AI skill pack for immediate use — it distills the A-share market-timing methods from *Lidaxiao Investment Strategy* into 10 capability cards that can be triggered individually or combined.

It is not a book summary, nor a reading response — it breaks the reusable methodology in the book into skill modules that can be triggered, executed and tested.

## What these skills solve

- The index has fallen a long way and you want to buy the bottom, but "it has fallen enough" is your only reason and you cannot say whether this is a historic-bottom area at all
- You have PE, PB, dividend-yield and government-bond-yield readings, but you do not know which range to compare them against, nor that two different conventions must never be mixed
- Central Huijin buying, the social-security fund entering, IPOs paused, a trillion yuan of turnover with no price gain, foreign money turning — the headlines never stop, and you cannot tell which items count
- You are torn between leaving money in bond funds and switching to high-dividend assets, and you lack a computable stock-versus-bond yardstick
- You are unsure whether you should be in the market at all: is this money spare money, may you use leverage, should you climb the five fund steps first
- You sell on every dip and chase every rally, with no tick-box discipline checklist and no contrarian sentiment gauge — post-mortems end at "I should have followed the rules"

## What was distilled

10 capability cards in four groups, organized in the order "locate first, do the math second, pass the gates next, then land on what to buy and how to check your own sentiment":

- **Market position**: `position-posture-skill` (position-to-posture doctrine), `bottom-identification-skill` (five-dimension historic-bottom identification), `top-bubble-signals-skill` (tops, bubbles and weakening signals)
- **Money and allocation**: `wind-vane-tracking-skill` (wind-vane and cross-market money tracking), `bond-stock-spread-skill` (bond-stock spread contrarian allocation and high-dividend bull diagnosis), `fund-flow-policy-skill` (capital supply/demand flows and policy reading)
- **Eligibility and self-assessment**: `entry-qualification-skill` (market-entry self-check and the retail progression path), `strategy-fit-skill` (strategy positioning and capability self-check)
- **Instruments and sentiment**: `stock-selection-skill` (selection priority and exclusion), `sentiment-contrarian-skill` (contrarian sentiment and source screening)

## Two packaging modes: single and pack

The same 10 capability cards are compiled twice, at two granularities. The capability content is identical; the only difference is how many entries an agent can discover.

| | single (one entry) | pack (compact pack, multiple entries) |
|---|---|---|
| Discoverable entries | **1**: `lidaxiao-investment-strategy-skill` | **7**: one source router + 6 promoted standalone skills |
| Where the 10 cards live | All inside the entry's `references/capabilities/`, loaded 1–2 at a time by the routing table | 6 cards become standalone skills; the other 4 stay in the router's `references/` |
| Triggering | Only the entry description participates in matching; routing happens after entry | The 6 high-frequency capabilities are matched directly, one hop fewer |
| Upgrades | Replace 1 directory | Replace 7 directories |

The 6 cards promoted to standalone skills in the pack:

- `bottom-identification-skill` — five-dimension historic-bottom identification
- `top-bubble-signals-skill` — tops, bubbles and weakening signals
- `wind-vane-tracking-skill` — wind-vane and cross-market money tracking
- `bond-stock-spread-skill` — bond-stock spread allocation and high-dividend bull diagnosis
- `fund-flow-policy-skill` — capital flows and policy reading
- `stock-selection-skill` — selection priority and exclusion

The 4 cards left in the router, served through its routing table: `position-posture-skill` (position-to-posture doctrine), `entry-qualification-skill` (market-entry self-check), `strategy-fit-skill` (strategy positioning), `sentiment-contrarian-skill` (contrarian sentiment). These four either depend on another card's criteria to land a conclusion (position mapping depends on the bottom and top judgments), or are themselves the gate in front of every other capability — promoted on their own, they tend to answer without context.

### Which one to install

Pick by the way you work, and **install only one**:

| How you work | Recommended | Why |
|---|---|---|
| You use DSH / Codex / Claude Code with a skills directory and want a clean list | single | Takes 1 slot, loses no capabilities |
| Your daily questions concentrate on "is this a bottom / is this a top / what is the state money doing / how should stocks and bonds be split / what should I buy" | pack | Those are exactly the promoted standalone skills, matched directly |
| You distribute to several agents or teammates who pick what they need | pack | They can install only the standalone skills they want |
| You want to install once and maintain one directory | single | Upgrades replace a single directory |

> Both builds come from the same bundle and carry identical capabilities. **Installing both will double-trigger**, so pick one.

## Examples

### Example 1: the index is near 2,700 — is this a historic bottom, can I buy?

**User question**

"The Shanghai Composite is near 2,700 and the PE looks low. Is this a historic bottom? Can I start buying?"

**How the skill reasons**

- Enter `bottom-identification-skill` and fix the convention first: the book gives two historical-bottom comparison tables that are not interchangeable — the Shanghai Composite trailing-PE convention (325 → 11.58, 998 → 14.56, 1664 → 12.5, 1849 → 10.85, a range of roughly 10.85–14.56) and the all-A-share convention (998 → 14.37, 1664 → 13.11, 1849 → 10.86, 2440 → 12.25, a range of roughly 10.86–14.37; PB 1.54 / 1.91 / 0.77 / 1.23, a range of roughly 0.77–1.91). The two must not be mixed, and every row of the comparison table carries its convention and source year
- Check five dimensions one by one: (1) valuation (2) bond-stock spread (3) wind vanes and money behaviour (4) sentiment extremes (5) supply and policy. Each is marked "matches / does not match / no data"; a missing item goes on the open-items list and is **never silently treated as satisfied**
- Aggregate: 4 or more aligned → "historic-bottom-area characteristics are significant"; 3 → "suspected, keep tracking"; 2 or fewer → "not enough to call this a bottom area"
- Stop branch: if valuation clearly sits outside the range (PE well above the comparison ceiling), the only permitted output is "atypical historic bottom", even when every other dimension aligns — the book anchors on valuation, and all 7 historical lows were extreme on it
- The output must carry the book's own boundary clause and hand off to `position-posture-skill` for what to actually do

**Sample answer**

> Do not turn "2,700" into the conclusion — the level is not the criterion. The book makes the point itself: 3,000 was 34× PE and 5× PB in 2007 and 11.6× and 1.24× in 2022, entirely different positions. First fix the convention: is your PE the Shanghai Composite trailing figure or the all-A-share figure? The two ranges differ (about 10.85–14.56 and 10.86–14.37), and mixing them produces a wrong answer. Then tick the five dimensions: valuation (inside the range? is the dividend yield of large-cap constituents above the one-year deposit rate?), bond-stock spread (dividend yield of quality stocks minus the 10-year or 50-year treasury yield — is it at a historical high?), wind vanes and money (has industrial capital flipped from net selling to net buying, does buyback plus increase exceed total financing, have Central Huijin and the social-security fund stepped in?), sentiment extremes (one-sided bearishness, nobody talking about stocks), and supply and policy (IPOs paused or clearly tightened). You gave me the level and the PE only, so treasury yields, insider flows and sentiment must be marked "no data" and put on the open-items list — I cannot count them as satisfied. Four or more aligned is what earns "bottom-area characteristics are significant"; three is only "suspected". One hard rule: when valuation clearly sits above the ceiling, every other dimension can look right and the answer is still "atypical historic bottom". Two gaps in the book, stated honestly: it never gives a complete quantitative screen for "cheapest and highest quality" stocks, and it never fully defines which dividend yield to use in the spread — declare your own convention and do not present it as the book's. Last point: "bottom area" is an area, not a date — the author's own phrase for it is a "thaw journey", not "it goes up now".

### Example 2: keep the money in bond funds, or switch to high dividend?

**User question**

"Should the money stay in bond funds or go into high-dividend stocks? Has the bond-stock spread already reached a historical high?"

**How the skill reasons**

- Enter `bond-stock-spread-skill` and run the precondition stop first: does this money meet both spare-money conditions (no use for 30–50 years, and able to absorb NAV swings), and is the allocation in line with the user's risk tolerance? If not → terminate with "complete the spare-money and risk-fit self-check first". If the user never states the nature of the money, do not terminate outright — give a conditional conclusion and label it "precondition unverified"
- Compute the spread = dividend yield of quality stocks − 10-year (or 50-year) treasury yield, in percentage points to two decimals, reporting **both maturities side by side and never averaging them**
- Locate the historical percentile, with only three permitted conclusions: high zone (stocks extremely cheap relative to bonds) / neutral / low zone (stocks extremely expensive relative to bonds). Reference readings in the book: on 2024-02-05 the 10-year yield hit 2.4002% (a low since 2002-04-15) and the 50-year hit a record low of 2.7064%; on 2024-03-06 both made new lows (10-year 2.2650%, 50-year 2.5978%)
- Check overheating at both ends of the seesaw: the bond end — has a money-market fund spiked or even hit the daily limit (an asset yielding about 2% chased at a 10% premium means a bond bubble), are bond funds restricting purchases; the equity end — are star equity funds restricting purchases, is allocation by lottery. If either end shows overheating, that end's "chase it" conclusion is downgraded to an overheating warning
- To diagnose a "high-dividend bull", all three conditions must hold: (1) asset famine (2) low rates (3) high payout — and it applies **only to good companies**; bad ones do not benefit
- Optional step: buyback/increase arbitrage room = sector dividend yield − borrowing cost for buybacks and increases (the book's 2024-10 example: SSE 50 dividend yield 3.65% − borrowing cost 2.25% = 1.40%; CSI 300 3.06% − 2.25% = 0.81%), with a reminder to verify actual buyback execution rather than counting "bought one lot" as evidence

**Sample answer**

> Put the precondition first: is this money unused for 30–50 years, and can you absorb NAV swings? If it is not spare money, the correct answer to "how should I split stocks and bonds" is "do not allocate yet". Once it is spare money, do the arithmetic: spread = dividend yield of quality stocks − treasury yield, computed for both the 10-year and the 50-year, reported side by side, never averaged. Declare the convention too: the book's example uses large-cap index dividend yields (the October 2024 piece cites 3.65% for the SSE 50 and 3.06% for the CSI 300), but the book never fully defines "dividend yield of quality stocks", so whatever convention you use must be stated — do not pass an all-market yield off as a large-cap yield. Then read the three states: a high zone means stocks are extremely cheap relative to bonds, a low zone means extremely expensive — the author's rule is that the best time to allocate to stocks is at a historical high in the spread, not a historical low, and most people do the opposite. Next, check overheating at both ends: the bond end for money-market funds spiking or hitting the limit and for bond funds restricting purchases; the equity end for star equity funds restricting purchases or allocating by lottery. Overheating at either end downgrades that end's "chase it" conclusion to a warning. If your real question is whether the high-dividend bull is still alive, all three conditions must hold — asset famine, low rates, high payout — and only for good companies. One honest caveat: the book gives no formula for an exact stock/bond ratio, so no, it cannot tell you "allocate 37%". What it gives is a directional contrarian rule.

## How these skills were generated

These skills were produced with the **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** RIA-TV++ pipeline, in six stages:

1. **Whole-book comprehension (Adler analysis)** — apply Mortimer Adler's analytical reading method to the book: structure, interpretation, criticism, application. This is also where the distillation bias is fixed: the user wants it to assist stock investment analysis
2. **Parallel extraction** — several specialized extractors (frameworks, principles, cases, counter-examples, terminology) mine candidate methodology units from the source text: 372 candidates in total (49 frameworks, 145 principles, 76 cases, 51 counter-examples, 51 terms)
3. **Triple verification** — every candidate must pass three checks: at least two independent in-book supports (cross-domain), the ability to answer questions the book never explicitly addresses (predictive power), and not being common sense (distinctiveness). Of the 372, 307 were verified, 62 were demoted to reference material, 3 were left for review, and 0 were invented; about 110 individual numbers were traced back to the source text one by one
4. **RIA++ construction** — structure each unit along R (quotation) / I (restatement in own words) / A1 (in-book case) / A2 (future trigger scenario) / E (executable steps) / B (boundaries and blind spots), clustered into 10 capability units, one card each
5. **Zettelkasten linking** — map dependencies, contrasts and combinations between cards, producing the capability index and the routing table, and writing into each card's A2 section how it differs from its neighbours
6. **Trigger and output testing** — run one representative task plus one negative/boundary case per card, with missing data always handled by the card's stop rules and never silently guessed; failing cards go back for rework

One boundary clause runs through every card: in the introduction the author states that forecasts are subject to many factors, including force majeure, and will deviate — and that the content must never be used as a basis for trading. That clause is written into the B section of every card and into the entry's stop rules.

## Repository layout

```text
lidaxiao-investment-strategy-skill/
├── README.md                      ← Chinese version
├── README.en.md                   ← you are reading this
├── LICENSE                        ← MIT
├── BOOK_OVERVIEW.md               ← whole-book comprehension (Adler four-step, stage 0 output)
├── verified.md                    ← triple-verification and 10-unit clustering of the 372 candidates
├── single/                        ← single-entry build
│   └── lidaxiao-investment-strategy-skill/
│       ├── SKILL.md               ← entry: triggers + routing table + loading rules
│       ├── BUILD_MANIFEST.json    ← build manifest and file hashes
│       └── references/
│           ├── overview.md        ← whole-book overview
│           ├── capability-index.md  ← full intent and keyword index
│           ├── cheatsheet.md      ← decision-rule quick reference
│           ├── glossary.md        ← glossary
│           └── capabilities/      ← 10 capability cards
├── pack/                          ← multi-entry build (compact pack)
│   ├── BUILD_MANIFEST.json
│   ├── capability-destinations.json
│   ├── lidaxiao-investment-strategy-skill-router/
│   │   ├── SKILL.md               ← source router entry
│   │   └── references/            ← 10 cards + indexes, called by the router
│   ├── bottom-identification-skill/
│   │   └── SKILL.md
│   ├── top-bubble-signals-skill/
│   │   └── SKILL.md
│   ├── wind-vane-tracking-skill/
│   │   └── SKILL.md
│   ├── bond-stock-spread-skill/
│   │   └── SKILL.md
│   ├── fund-flow-policy-skill/
│   │   └── SKILL.md
│   └── stock-selection-skill/
│       └── SKILL.md
```

## Usage

Clone the repository first:

```bash
git clone https://github.com/raphael-y7/lidaxiao-investment-strategy-skill.git
```

### Install single (recommended first try)

```bash
# macOS / Linux
cp -r lidaxiao-investment-strategy-skill/single/lidaxiao-investment-strategy-skill ~/.agents/skills/
```

```powershell
# Windows
Copy-Item -Recurse .\lidaxiao-investment-strategy-skill\single\lidaxiao-investment-strategy-skill "$env:USERPROFILE\.agents\skills\"
```

### Install pack

Copy only the directories that contain a `SKILL.md`; do not copy the two JSON files under `pack/` into your skills directory:

```bash
# macOS / Linux
cd lidaxiao-investment-strategy-skill/pack
cp -r lidaxiao-investment-strategy-skill-router \
      bottom-identification-skill \
      top-bubble-signals-skill \
      wind-vane-tracking-skill \
      bond-stock-spread-skill \
      fund-flow-policy-skill \
      stock-selection-skill ~/.agents/skills/
```

```powershell
# Windows
$pack = ".\lidaxiao-investment-strategy-skill\pack"
$dest = "$env:USERPROFILE\.agents\skills"
@('lidaxiao-investment-strategy-skill-router','bottom-identification-skill','top-bubble-signals-skill','wind-vane-tracking-skill','bond-stock-spread-skill','fund-flow-policy-skill','stock-selection-skill') |
  ForEach-Object { Copy-Item -Recurse -LiteralPath (Join-Path $pack $_) -Destination $dest }
```

> `~/.agents/skills` is the DSH skills directory; with another agent, use its own skills directory (for example `~/.claude/skills` for Claude Code).

### How to verify the install

Ask: "Does the current level count as a historic bottom, and which items should I check?" If the agent enters the five-dimension check of `bottom-identification-skill` and asks for your PE/PB convention, dividend yield, treasury yields and insider-flow data instead of giving generic "buy in batches near the bottom" commentary, the install works. With the single build it reads the entry first and then routes to a card; with the pack build the matching capability is hit directly.

## Sources

- *Lidaxiao Investment Strategy* by Li Daxiao
- Distilled from the whole book, producing 10 capability cards

## Notice

This repository publishes distilled skills, indexes and rule quick references only. It contains no PDF, EPUB, OCR files, screenshots or full-book transcripts of the source book. Quotations that appear in the capability cards serve solely to attribute methodology and keep the material auditable.

All numeric criteria in the book (the PE/PB ranges for historic bottoms, dividend-yield and treasury-yield readings, the Buffett-indicator tiers, the number of days a trillion-yuan turnover can stall, the ten-person survey, etc.) are case- and experience-based rules without statistical backtesting; every reading is a snapshot from the book's own period, so recompute with current data and declare the convention you use. The criteria are inductions from 7 historical lows and 5 highs and carry no guarantee. Nothing in this repository is investment advice.

## License

[MIT](./LICENSE)

