# Research Idea 1: Natural Safety Alignment Drift in Multi-Turn Conversations

> **One-line pitch:** LLM safety evaluations are run on single turns; real deployments accumulate conversation history — we show that benign conversation depth alone, without any adversarial intent, measurably erodes refusal behavior.

---

## Research Question

Does safety alignment degrade as a function of benign conversation depth, independent of adversarial escalation? If so, what are the degradation curves per model, domain, and conversation type — and how badly do single-turn safety evaluations underestimate real-world failure rates?

---

## Prior Work Landscape

The field breaks into four clusters, none of which occupies the precise gap:

| Paper | Venue | What they do | Why it's different |
|-------|-------|-------------|-------------------|
| Crescendo (Russinovich et al.) | USENIX Security 2025 | Attacker-crafted benign-looking escalation; 29–61% higher ASR than SOTA | Every turn is strategically designed by an attacker |
| Foot-in-the-Door (Weng et al.) | EMNLP 2025 | Gradual compliance escalation via bridge prompts; 94% ASR across 7 models | Adversarially designed escalation gradient |
| Many-Shot Jailbreaking (Anthropic) | NeurIPS 2024 | Fabricated in-context harmful demonstrations; power law with shots | Fake "assistant" turns, not real benign conversation history |
| State-Dependent Safety Failures (Li et al.) | arXiv 2603.15684, 2026 | STAR framework: monotonic drift from refusal representations under structured multi-turn interaction | Adversarially structured trajectories — not natural conversations |
| LongSafety (Lu et al.) | ACL 2025 | Safety drops below 55% in long-context conditions across 16 models | Conflates context *length* (documents) with multi-turn *interaction history* |
| Slow Drift (Cheng et al.) | arXiv 2601.14269, 2026 | Natural safety boundary violations in psychiatric dialogues from empathy dynamics | Single domain (mental health), not general; not controlled |
| Persistent Personas (de Araujo et al.) | EACL 2026 | Persona fidelity and indirectly safety behavior degrades over 100+ turn role-play | Role-play specific; safety is secondary to persona fidelity |
| Old Habits Die Hard (Simhi et al.) | arXiv 2603.03308, 2026 | Conversational history creates geometric trap; up to 73% performance drop | Constructs specific prior content, not purely benign history |

### Key Observation
Every paper that measures refusal rate as a function of turn count either (a) uses adversarially-crafted turn sequences, or (b) studies a stressed domain (mental health, role-play). **No paper holds the harmful probe constant and varies only the depth of benign, ordinary conversation history** as an isolated independent variable.

---

## Precise Gap / Novelty Claim

> **No existing paper asks: does safety alignment erode in perfectly ordinary conversations, without any user trying to manipulate the model?**

The specific contribution is: a controlled experiment where benign conversation depth is the *only* variable, the harmful probe is held constant, and refusal rates are measured as a function of turn count — separately from context *length* (long documents) and separately from adversarial *intent*.

Secondary novelty: distinguishing **semantic priming** (topic-related benign history causes faster drift) from **pure length dilution** (off-topic history dilutes safety attention in the context window). These are two different mechanisms that existing work conflates.

---

## Proposed Experimental Design

### Experimental Conditions

| Condition | Description |
|-----------|-------------|
| Zero-shot baseline | Harmful probe with no prior conversation |
| Benign related history | N turns of topic-adjacent benign conversation, then probe |
| Benign off-topic history | N turns of unrelated benign conversation, then probe |

The off-topic control isolates semantic priming from context-length dilution — a clean mechanistic separation that strengthens the paper significantly.

### Turn Depths
`N ∈ {0, 5, 10, 25, 50, 100}`

### Harmful Probe Categories
Use HarmBench / AdvBench categories (20 probes per category):

| Probe category | Matched benign history domain |
|---------------|------------------------------|
| Cybersecurity exploits | Software engineering / debugging |
| Violence / harm to persons | History / fiction / film analysis |
| Chemical / biological hazards | Chemistry education / cooking |
| Disinformation / propaganda | Media literacy / journalism |
| Hate speech | Cultural studies / sociology |

### Models
GPT-4o, Claude 3.5 Sonnet, Gemini 1.5 Pro, Llama 3.1 70B, Mistral Large — cross-family is essential for generalizability claims.

### Metrics

| Metric | Description |
|--------|-------------|
| Refusal rate | Binary per run |
| Safety classifier score | Continuous 0–1 from LlamaGuard 3 + WildGuard |
| Partial compliance rate | Gives some harmful information even mid-refusal |
| Refusal hedging score | Does refusal language soften over turns? (e.g., "I shouldn't..." vs. "Absolutely not") |

Partial compliance is the most novel metric — a model saying "I can't help with that, but here's adjacent info..." is a real-world safety failure that binary refusal rate misses entirely.

### Scale
`5 probe categories × 6 turn depths × 2 topic conditions × 5 models × 20 probes = 6,000 API calls`
Estimated cost: ~$150–250 in API credits. Feasible in one weekend.

### Analysis
- Plot refusal rate as a function of turn count — **survival curves** per model (borrow the epidemiological framing from arXiv:2510.02712)
- Fit degradation models (linear, logistic, exponential decay) and compare AIC across models
- Mixed-effects logistic regression: turn depth × topic condition × model × probe category
- Main claims: (1) degradation is statistically significant vs. baseline; (2) related history causes faster degradation than unrelated (semantic priming effect); (3) models vary significantly in degradation shape

---

## Feasibility Assessment

| Dimension | Rating | Notes |
|-----------|--------|-------|
| Experimental setup complexity | Low | Scripted API calls; no novel infrastructure needed |
| Data collection cost | Low | ~$200 in API credits; one weekend of compute |
| Analysis complexity | Low-Medium | Standard logistic regression + survival analysis; well-established methods |
| Risk of null result | Medium | If degradation is not statistically significant, paper doesn't exist — but the STAR paper (2026) finds mechanistic evidence of drift, so positive signal is likely |
| Differentiation from prior work | Medium | Requires carefully distinguishing from State-Dependent Safety Failures (2603.15684). The "benign natural conversation" vs. "adversarially structured" distinction must be the centerpiece |
| Reproducibility | High | Full experiment specification enables replication |

**Main risk:** State-Dependent Safety Failures (arXiv March 2026) is close enough that reviewers may see overlap. The differentiator must be crisp: *theirs studies adversarially structured trajectories; ours shows the same phenomenon in completely ordinary conversations with no attacker present.* This is a stronger result, not a weaker one — but the framing must make this clear.

---

## Probability of Success

| Outcome | Probability | Reasoning |
|---------|------------|-----------|
| Positive result (drift is significant) | 75% | Mechanistic evidence from STAR paper, Slow Drift, and LongSafety all point toward drift being real; benign natural variant likely shows same effect |
| Clean differentiation story | 65% | Requires negative control (off-topic history) to show semantic priming cleanly |
| Top-venue acceptance (NeurIPS/ICLR) | 30–35% | Space is competitive; STAR paper is a near-miss; strong empirical result + survival curve framing + partial compliance metric increases chances |
| Mid-tier venue acceptance (EMNLP/ACL/USENIX) | 65–70% | ACL or EMNLP safety track is very plausible with solid empirical results |

**Overall probability of a publishable outcome at a good venue: ~65–70%.**

---

## Recommended Positioning

> "We demonstrate that safety alignment erosion is not just an artifact of adversarial attack design — it occurs in completely ordinary multi-turn conversations. Our controlled study, the first to isolate benign conversation depth as the independent variable, shows [X]% degradation in refusal rates across 5 frontier models over 100 turns. Current single-turn safety benchmarks systematically underestimate real-world failure rates by [Y]%."

---

*Last updated: 2026-05-28*
