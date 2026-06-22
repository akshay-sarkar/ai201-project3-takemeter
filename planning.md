# TakeMeter — planning.md
> Investment Discourse Quality Classifier

---

## 1. Community

**Chosen community:** r/valueinvesting + r/StockMarket + r/stocks + r/investing (Reddit)

**Why this community:**
These subreddits form a spectrum of investment discourse quality — from rigorous stock analysis to emotional market reactions. The discourse is almost entirely text-based (minimal videos or memes), posts are consistently long enough to classify meaningfully, and the quality gap between posts is obvious and community-recognized. Investors themselves already distinguish between "DD" (due diligence / analysis), "predictions" (speculation), and "venting" (reaction) — which means our labels are grounded in how participants actually talk about each other's posts.

**Why it's a good fit for classification:**
- Text-heavy: nearly every post has substantial original text
- Varied quality: the gap between a well-researched stock breakdown and a "this stock is going to moon" post is immediately obvious
- Balanced sourcing: r/valueinvesting (`stockanalysis` tag) provides clean `analysis` examples; r/StockMarket (`Opinion` tag) provides `speculation`; r/stocks and r/investing provide `reaction` during market events
- Domain labels are community-recognized: terms like "DD", "hopium", and "cope" already exist in these spaces

---

## 2. Label Taxonomy

### `analysis`
**Definition:** A post makes a structured investment argument backed by specific, verifiable data — earnings figures, valuation metrics, revenue growth, competitive positioning, or macro indicators. The reasoning could stand independently of the conclusion.

**Source:** Primarily r/valueinvesting posts tagged `stockanalysis`

**Example 1 (clear):**
> *"Adobe just reported a double beat, raised guidance, but dropped ~10%. A 12% FCF yield means the market is assuming not just slower growth, but actual permanent structural decline. I work in creative land and was buying around $250, but at ~$205 now I'm backing up the truck. I've been looking at their AI tools and the roadmap looks solid..."*
> — r/valueinvesting, $ADBE post

**Example 2 (clear):**
> *"Is UHS undervalued? Trailing P/E = 6.12, price to book = 1.20 (goes to 2.6 if you remove Goodwill), current ratio = 1.05. The business has been growing steadily, costs seem to be under control, with gross margins increasing. Cash flow is positive (in 2025 FCF is $824M plus $967M of buybacks) and growing."*
> — r/valueinvesting, UHS post

---

### `speculation`
**Definition:** A bold prediction or opinion about a stock, sector, or market movement stated with little or no supporting evidence. The post is confident in framing but the argument doesn't hold up if you remove the conclusion. May cite one surface-level stat to appear credible.

**Source:** r/StockMarket `Opinion` tag posts; r/stocks and r/investing via Manus AI

**Example 1 (clear):**
> *"$REPX trades at PDP liquidation value (~$34) despite 30% production growth in 2025, 25% guided for 2026, 147 MMBoe reserves, 1.0x leverage, and $100M buyback authorised. Base case intrinsic value $44–48. Bull case $56–61. Biggest risk is commodity price — this is an oil call, not a bond."*
> — r/valueinvesting, REPX post (price targets without valuation methodology)

**Example 2 (clear):**
> *"Wall Street is finally waking up. They are done treating nuclear like some outdated power source. They are actively repricing it as the single most scarce asset in the AI era: 24/7 low-carbon baseload power. Strip away the noise and the nuclear thesis comes down to three moving parts right now."*
> — r/StockMarket, nuclear energy post (narrative assertion without financial data)

---

### `reaction`
**Definition:** An immediate emotional response to a specific market event — earnings report, Fed decision, price crash, or breaking news. The post expresses a feeling in the moment rather than making an investment case.

**Source:** r/stocks and r/investing posts during/after major market events (real Reddit via Manus AI)

**Example 1 (clear):**
> *"I'm genuinely dumbfounded how you can be first to market at an injectable GLP-1, have tons of patients taking it, get first to market with the best oral GLP-1 with thousands of prescriptions for it… and still be only up 1.25% from 5 years ago. It's down 4% today and I just can't wrap my head around how this company isn't printing money."*
> — r/valueinvesting, NVO post (reacting to specific price event)

**Example 2 (clear):**
> *"Anthropic has updated its website to warn that any sale or transfer of its stock without company approval may be considered void. To me, this looks like a sign that private AI stock demand is getting very heated."*
> — r/StockMarket (reacting to a specific breaking news event)

---

## 3. Hard Edge Cases

### Anticipated ambiguous case: "Stat-decorated speculation"

**Description:** A post that cites one real data point (a revenue figure, a P/E ratio, a price target from an analyst) but uses it purely to support a preloaded price prediction rather than to build a reasoned argument.

**Example:**
> *"Apple is going to $250. Their services revenue is up 14% and nobody is talking about it."*

**Which labels it could belong to:** `analysis` (cites a real stat) or `speculation` (the stat doesn't build an argument — it just decorates a price prediction)

**Decision rule:**
> If the data presented would logically lead a neutral reader to the same conclusion even without the opinion framing — label it `analysis`. If the data is cited to support a preloaded conclusion but doesn't actually construct the argument — label it `speculation`. One stat + a price target = `speculation`. A breakdown of margins, growth trajectory, and comparative valuation = `analysis`.

---

### Anticipated ambiguous case: "Reaction with a prediction"

**Description:** A post that starts as an emotional response to a market event but then adds a forward-looking opinion.

**Example:**
> *"The Fed just raised rates again, I'm sick of this. I'm moving everything to cash until this is over."*

**Decision rule:**
> If the primary content is emotional and event-triggered, label it `reaction` — even if it ends with a brief opinion. Only upgrade to `speculation` if the forward-looking claim is the main point of the post, not a frustrated afterthought.

---

### Anticipated ambiguous case: "Technical price observation"

**Description:** A post that cites specific price levels (SPY 681, QQQ 610) in the style of technical analysis but is written in real-time emotional framing about a specific market session.

**Example:**
> *"On Monday I was focused on SPY 681–680 and 692 above. 681 held. That's the main thing. Every push toward 690–692 just kind of fades. Feels more like positioning than commitment."*

**Decision rule:**
> Technical price levels alone do not make a post `analysis`. If the post has no fundamental metrics (earnings, P/E, FCF, margins) and is written in real-time emotional framing ("feels like", "I'm assuming"), label it `reaction`.

---

### Difficult examples encountered during annotation

**Hard case 1 — AAII sentiment post:**
- Post: *"The indexes have continued to grind out new highs after an extended rally since late March. AAII survey: Bullish 36.3% vs 37.5% historical average. Bearish 37% vs 31% historical average. Bearishness has run above its historical average for 17 consecutive weeks..."*
- Could be: `analysis` vs `reaction` (it cites weekly survey data, which feels reactive)
- Decision: **`analysis`** — cites specific historical averages, builds conditional thresholds to watch (bulls >40%, bears retreating to 31%), and is not emotionally triggered by a single event. The data constructs a framework, not a gut check.

**Hard case 2 — Nuclear energy "bid" post:**
- Post: *"Wall Street is finally waking up. They are actively repricing nuclear as the single most scarce asset in the AI era. Data center power demand is projected to skyrocket by 2030 — some estimates show a 160% jump. CEG, VST, OKLO are being repriced as premium infrastructure plays."*
- Could be: `analysis` (has some data points) vs `speculation` (broad narrative with no company-level valuation)
- Decision: **`speculation`** — no P/E, no revenue figures, no DCF, no company-level financial data. The statistics cited (160% demand growth) are vague projections used as narrative decoration. Remove the conclusion and the argument collapses.

**Hard case 3 — SPY/QQQ/IWM midweek thoughts:**
- Post: *"681 held. That's the main thing. Every push toward 690–692 just kind of fades. Feels more like range trade, not trend. No acceleration zones have triggered. Feels more like positioning than commitment."*
- Could be: `analysis` (has specific price levels) vs `reaction` (real-time emotional gut check)
- Decision: **`reaction`** — technical price levels without fundamental metrics = reaction when written in real-time emotional framing. The post is processing a feeling about where the market is right now, not making an investment case.

---

## 4. Data Collection Plan

**Final sources used:**

| Label | Source | Method | Final Count |
|---|---|---|---|
| `analysis` | r/valueinvesting (`stockanalysis` tag) | 35 manually collected real posts + 52 Gemini-generated synthetic posts | 88 |
| `speculation` | r/StockMarket (`Opinion` tag) + r/stocks + r/investing | 50 real Reddit posts (manually collected + Manus AI) + 16 synthetic to reach 200 | 66 |
| `reaction` | r/stocks + r/investing + r/wallstreetbets | 47 real Reddit posts (manually collected + Manus AI) — all synthetic removed | 47 |
| **Total** | | | **200** |

**Data origin breakdown:**

| Label | Real Reddit | Synthetic/AI-generated | Total |
|---|---|---|---|
| `analysis` | 35 | 52 (Gemini — high quality, kept) | 87 |
| `speculation` | 50 | 16 (kept to reach 200 minimum) | 66 |
| `reaction` | 47 | 0 — all synthetic removed | 47 |
| **Total** | **132 (66%)** | **68 (34%)** | **200** |

**Collection phases:**

**Phase 1 — Initial build (218 examples):**
Manually collected ~57 real Reddit posts. Supplemented with AI-generated synthetic data for `speculation` (66 posts) and `reaction` (54 posts) due to difficulty finding real posts at scale. Resulting dataset was ~74% synthetic.

**Phase 2 — Real data upgrade:**
95 real Reddit posts were collected via Manus AI with verified URLs. After quality review and label correction (5 posts relabeled, 5 skipped as duplicates or ambiguous), 92 net new posts were added. All 54 synthetic `reaction` posts were removed and replaced with real ones. Synthetic `speculation` posts were reduced from 66 to 16 — only the minimum needed to keep total at 200. Real data proportion rose from ~26% to 66%.

**Collection order:** `analysis` first (hardest to find in volume), then `speculation`, then `reaction`.

**Exclusion rules applied:**
- Skipped any post under ~20 words of original text
- Skipped posts that are primarily external links with no original argument
- Skipped image/video posts with no substantial text body
- Skipped posts that are purely questions with no opinion expressed
- Skipped posts that were genuine duplicates of existing entries
- Skipped posts where the label was genuinely ambiguous between two classes and could not be resolved with existing decision rules

**Relabeling decisions made during Phase 2 review:**
- 2 Manus posts relabeled `speculation → analysis`: contained structured historical market statistics building a genuine argument, not a bold assertion
- 1 Manus post relabeled `reaction → analysis`: detailed earnings transcript breakdown with specific financial metrics — clearly analysis
- 6 Manus posts relabeled `reaction → speculation`: forward-looking strategy/portfolio opinion posts, not immediate emotional responses to specific events

**Final label distribution:**

| Label | Count | Percentage |
|---|---|---|
| `analysis` | 88 | 40.4% |
| `speculation` | 70 | 32.1% |
| `reaction` | 60 | 27.5% |
| **Total** | **218** | **100%** |

No label exceeds 70% of the dataset. All labels meet the 20-example minimum.

---

## 5. Evaluation Metrics

**Primary metric: Per-class F1 score**

Accuracy alone is insufficient here because:
- Even with a balanced dataset, a model could learn to predict `reaction` or `speculation` more reliably than `analysis` — accuracy hides this
- The cost of misclassifying `analysis` as `speculation` (or vice versa) is asymmetric — it matters which direction errors go
- F1 captures both precision and recall per class, revealing whether the model is being conservative or aggressive about each label

**Metrics I will report:**

| Metric | Why |
|---|---|
| Overall accuracy (both models) | Baseline comparison |
| Per-class F1 (both models) | Main evaluation signal |
| Per-class precision & recall | Understand direction of errors |
| Confusion matrix | Identify which label pair is hardest |

**What I expect to be hardest:** The `analysis` vs `speculation` boundary — both involve investment claims, but one is evidence-based and one isn't. I expect the model to struggle when posts cite stats but lack genuine reasoning. The `analysis` vs `reaction` boundary may also be tricky for short posts that contain price observations but no fundamental data.

---

## 6. Definition of Success

**Minimum viable performance (for deployment in a real community tool):**
- Overall accuracy ≥ 70% on test set
- Per-class F1 ≥ 0.65 for all three labels — no single label left behind
- Fine-tuned model must meaningfully outperform the zero-shot Groq baseline (at least +10% overall accuracy)

**What "good enough" looks like:**
A classifier that correctly identifies `analysis` posts at least 65% of the time is genuinely useful — it could power a community tool that surfaces high-quality DD posts or flags low-effort speculation. Perfect classification isn't the goal; consistent signal is.

**Red flags that would indicate failure:**
- Any label with F1 < 0.40 — the model isn't learning that boundary at all
- Fine-tuned model performs worse than or equal to the zero-shot baseline — fine-tuning added nothing
- Confusion matrix shows >50% of `analysis` being called `speculation` — the most critical error type

**Revised concern with real data:** With 66% real Reddit posts now in the dataset, the model faces more noise and boundary ambiguity than a purely synthetic dataset would produce. This is intentional — the goal is generalization to real posts. The risk is that training signal is noisier, which may slightly lower accuracy but should improve real-world performance.

---

## 7. AI Tool Plan

### Label stress-testing (before annotation)
**What was done:** Fed the three label definitions and edge case descriptions to Claude. Asked it to generate boundary posts between `analysis` and `speculation`. This revealed the "stat-decorated speculation" edge case — posts that cite one metric to support a preloaded price target — and led to the explicit decision rule in Section 3.

### Annotation assistance (during collection)

**Phase 1 — Initial build:**

1. **Real Reddit collection (~57 posts):** Manually collected and labeled posts from r/valueinvesting, r/StockMarket, r/stocks, and r/investing. Each post was read, labeled, and reviewed independently.

2. **AI-curated speculation sets (~66 posts):** Three pre-built synthetic datasets (Sets 1, 2, 3) were provided via Claude conversation. These were described as *"structurally accurate, high-fidelity synthetic data"* mirroring Reddit financial community patterns. Each post was reviewed for label accuracy before inclusion.

3. **Gemini-generated analysis batch (40 posts):** A structured prompt was used with Gemini to generate 40 analysis posts across 8 sectors with required financial metrics, explicit bear cases, and varied conclusions (bullish/bearish/neutral). Each post was reviewed before inclusion.

4. **Reaction dataset (54 synthetic posts):** A pre-built synthetic dataset was provided via Claude conversation. Gemini confirmed when asked directly that these were AI-generated synthetic posts designed to mirror the linguistic patterns of r/wallstreetbets and r/stocks. Each post was reviewed for label accuracy. *These posts were subsequently removed in Phase 2.*

**Phase 2 — Real data upgrade attempt via Manus AI (reverted):**

A structured prompt was written specifying exact label definitions, exclusion rules, decision rules for edge cases, and required CSV format with verified Reddit URLs. Manus AI collected 100 real Reddit posts from r/StockMarket, r/stocks, and r/investing. After auditing, 38 of 50 "reaction" posts were mislabeled — Manus applied `reaction` to pre-earnings speculation, valuation questions, and news summaries rather than emotional event-triggered posts. Two fine-tuning runs on the corrected dataset produced accuracy of 46.67% and 54.55%, significantly worse than the 93.94% achieved with the original synthetic dataset.

Root cause: real Reddit posts sit much closer to label boundaries than synthetic ones. Real speculation frequently cites financial data; real reactions often contain price-level observations. With only ~215 training examples, the model cannot learn to handle this ambiguity. The synthetic dataset was restored. This experiment is documented as a key finding in the README evaluation report.

**All posts (real and synthetic) were reviewed for label accuracy before inclusion. No post was accepted without reading.**

### Failure analysis (after evaluation)
**What was done:** After running evaluation in Colab, pasted both misclassified test examples into Claude and asked it to identify systematic patterns. Claude identified the "analysis gravity problem" — both wrong predictions were pulled toward `analysis` because they contained financial language or structured formatting despite not being genuine analysis. This pattern was verified manually and documented in the evaluation report.

---

## 8. Stretch Features (update before starting each)

- [ ] Inter-annotator reliability — have at least one other person label 30+ examples independently
- [ ] Confidence calibration — analyze whether model confidence scores are meaningful
- [ ] Error pattern analysis — identify systematic error patterns beyond individual wrong predictions
- [ ] Deployed interface — build a simple UI that classifies new posts with label + confidence

---

## Changelog

| Date | Update |
|---|---|
| June 16, 2026 | Initial planning.md written — Milestones 1 & 2 complete |
| June 16, 2026 | Updated after dataset completion — Milestone 3 complete. Added real examples, hard cases, final counts, synthetic data disclosure, and revised AI Tool Plan |
| June 18, 2026 | Attempted Phase 2 real data upgrade via Manus AI. Collected 100 posts, audited, corrected 38 mislabeled reaction posts. Two fine-tuning runs on corrected dataset produced 46.67% and 54.55% accuracy vs 93.94% baseline — reverted to original synthetic dataset. Finding documented in README reflection section as key project insight. |
