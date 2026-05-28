# Research Idea 2: User-Injected Stereotype Propagation in Multi-Turn Conversations

> **One-line pitch:** When users introduce demographic stereotypes into conversation, LLMs don't just echo them — they compound and propagate them across subsequent turns, producing downstream biases that single-turn fairness benchmarks completely miss.

---

## Research Question

When a user introduces a demographic stereotype at turn T, how does it affect the model's demographic-relevant outputs at turns T+1, T+2, ..., T+N? Does bias magnitude grow, decay, or oscillate? Does the effect vary by demographic group, stereotype type, model family, and conversation domain?

---

## Prior Work Landscape

### What Already Exists

| Paper | Venue | What they do | Gap relative to this idea |
|-------|-------|-------------|--------------------------|
| FairMT-Bench (multiple authors) | ICLR 2025 | First multi-turn fairness benchmark: 10K dialogues, 6 bias attributes, 3 task stages | Measures bias in *final turn* vs. single-turn baseline; does NOT provide per-turn accumulation curves or study user-injected stereotypes |
| SYCON Bench (Hong et al.) | EMNLP 2025 | Measures sycophantic stance shift across turns; "Turn of Flip" and "Number of Flip" metrics | Studies opinion conformity, not demographic stereotype propagation |
| User-Assistant Bias (NeurIPS 2025) | NeurIPS 2025 | Formalizes stubborn vs. agreeable bias in multi-turn; 8K conversation dataset | Measures over-reliance on user input generally, not demographic stereotype injection specifically |
| Fairness Feedback Loops (FAccT 2024) | FAccT 2024 | Synthetic training data amplifies bias across model *generations* | Training-time amplification, not conversational turn-by-turn amplification |
| B-score (ICML 2025) | ICML 2025 | Measures bias *decrease* when model sees its own response history | Shows self-consistency reduces bias in constrained settings; opposite direction from injection scenario |
| Spoken Dialogue Bias (arXiv 2510.02352) | arXiv 2025 | Bias in speech LLMs; tracks tone across turns for different demographic groups | Healthcare domain only; measures pre-existing bias persistence, not injected stereotype propagation |
| Bias Amplification via Synthetic Training | IJCNLP-AACL 2025 | Bias amplifies across training rounds | Training-time, not conversational |
| BBQ, WinoBias, CrowS-Pairs, StereoSet | Various | Single-turn demographic bias benchmarks | No multi-turn extension exists for any of these canonical benchmarks |

### The Critical Finding on FairMT-Bench
FairMT-Bench (ICLR 2025) is the closest prior work. It is important to understand exactly what it does and does not do:
- **What it does:** Creates 10K multi-turn dialogues, measures bias in the last turn vs. single-turn baseline, shows bias is higher in multi-turn settings.
- **What it does NOT do:**
  - Does not provide per-turn accumulation curves (how bias magnitude changes at each individual turn)
  - Does not study what happens when the *user* introduces a stereotype (all its dialogues have the model as the potential bias source)
  - Does not measure cross-attribute amplification (gender stereotype in turn 1 → race-relevant bias in turn 5)
  - Does not extend BBQ/WinoBias/StereoSet — it creates its own dataset from scratch

This means FairMT-Bench establishes the phenomenon but does not characterize its **dynamics** (the turn-by-turn trajectory) or its **source** (user-injected vs. model-intrinsic bias).

---

## Precise Gap / Novelty Claim

> **The user-injection angle is entirely uncovered:** What happens when a user (not the model) introduces a demographic stereotype, and the model's downstream responses are measured for stereotype uptake, amplification, and propagation?

This is a realistic deployment scenario: users make biased statements, and models that sycophantically conform to conversational context amplify and legitimize those stereotypes in subsequent turns. This is distinct from studying whether models produce biased outputs unprompted.

**Three specific contributions not in FairMT-Bench or any existing paper:**
1. **Per-turn accumulation curves** — measure stereotype bias score at each turn T, not just first vs. last
2. **User-injection dynamics** — the bias source is the *user*, not the model; measures how much the model absorbs and amplifies user-introduced stereotypes
3. **Cross-attribute spillover** — does a gender stereotype in turn 1 produce measurable race-relevant bias by turn 5? (no existing paper measures this)

---

## Proposed Experimental Design

### Setup: The Injection-and-Propagation Paradigm

**Turn 1 (Injection):** User makes a statement containing a demographic stereotype (e.g., "Women aren't as good at technical work as men" / "People from [group X] tend to be [negative trait]").

**Turns 2–N (Propagation measurement):** Continue with a benign conversation in which demographic group membership becomes relevant (job recommendations, capability assessments, educational advice, etc.). Measure the bias in model outputs at each turn.

**Control condition:** Same conversation with the stereotype statement replaced by a neutral statement (e.g., "People have different strengths in different areas").

### Stereotype Categories and Demographic Groups

| Stereotype type | Demographic groups |
|----------------|-------------------|
| Competence | Gender (women, men), Race (Black, Asian, Latino, White), Age (elderly, young) |
| Criminality | Race, Socioeconomic status |
| Work ethic | Race, National origin, Socioeconomic status |
| Emotional traits | Gender, Race |
| Cultural / religious | Religion, National origin |

### Turn Depths Measured
Per-turn measurement at T = 1, 2, 3, 5, 8, 10, 15, 20 (exponential spacing captures both early and late dynamics)

### Bias Measurement Metrics

| Metric | How measured |
|--------|-------------|
| Stereotype uptake rate | Does the model's response incorporate or validate the injected stereotype? (LLM-as-judge + human annotation) |
| Demographic disparity score | Delta between model outputs for different demographic groups (e.g., job recommendation quality for Group A vs. Group B after stereotype injection) |
| Stereotype persistence | How many turns after injection is bias still detectable? |
| Cross-attribute spillover | After gender stereotype in turn 1, does race-relevant bias appear in later turns? |
| Recovery rate | If user explicitly corrects the stereotype at turn N, how quickly does bias decay? |

### Existing Benchmarks to Extend
Use BBQ, WinoBias, and StereoSet probe questions as the "measurement turns" — take the existing single-turn probes, insert them at positions T+1, T+3, T+5, T+10 after a stereotype injection, and measure the score. This creates **multi-turn versions of canonical benchmarks** as a direct, comparable contribution.

### Models
GPT-4o, Claude 3.5 Sonnet, Gemini 1.5 Pro, Llama 3.1 70B, Mistral Large + one RLHF-heavy model (Claude) vs. one instruction-tuned (Llama) to test whether RLHF amplifies sycophantic stereotype uptake (predicted from SYCON bench findings).

### Scale
`5 stereotype categories × 8 turn depths × 5 models × 30 prompts per cell × 2 conditions (injected vs. control) = 12,000 runs`
Estimated cost: ~$300–400 in API credits.

---

## Feasibility Assessment

| Dimension | Rating | Notes |
|-----------|--------|-------|
| Experimental setup complexity | Medium | Requires careful stereotype injection prompt design and per-turn measurement instrumentation |
| Data collection cost | Low-Medium | ~$350 API credits; one to two weeks of data collection |
| Human annotation need | Medium | LLM-as-judge needs spot-check human annotation for stereotype uptake measurement; ~500 human annotations |
| Risk of null result | Low-Medium | SYCON bench shows sycophancy grows with turns; RLHF amplifies conformity — injection-and-propagation likely to show a significant effect |
| Differentiation from FairMT-Bench | High | The user-injection angle and per-turn accumulation curves are explicitly not in FairMT-Bench; reviewers will see the distinction clearly |
| Ethical review considerations | Medium | Involves explicitly constructing stereotypical statements; paper must include safeguards discussion |
| Venue fit | High | FAccT is the ideal venue; this is exactly the kind of measurement+implications paper FAccT rewards |

**Main risk:** FairMT-Bench at ICLR 2025 is recent and well-known. Reviewers will ask "how is this different?" The user-injection framing, per-turn curves, and extension of BBQ/WinoBias to multi-turn must be foregrounded clearly in the paper. The cross-attribute spillover finding (if it exists) would be the headline result — genuinely novel and surprising.

---

## Probability of Success

| Outcome | Probability | Reasoning |
|---------|------------|-----------|
| Positive result (significant propagation) | 75–80% | SYCON bench and FairMT-Bench both show multi-turn amplification; user-injection variant very likely to show same |
| Cross-attribute spillover finding | 40% | Genuinely uncertain — this could go either way; if confirmed, it's the headline result |
| Clear differentiation from FairMT-Bench | 80% | The user-injection angle is not covered; differentiation story is strong |
| FAccT acceptance | 40–50% | FAccT is competitive but this is a strong fit; reproducibility, societal implications, measurement focus all align |
| EMNLP/ACL acceptance as backup | 65–70% | Solid empirical paper with benchmark contribution |

**Overall probability of a publishable outcome at a good venue: ~70–75%.**

---

## Target Venue and Timeline

| Target | Deadline (est.) | Fit |
|--------|----------------|-----|
| FAccT 2027 | January 2027 | Ideal fit — fairness, accountability, measurement |
| ACL 2026 | February 2026 | Strong fit; requires fast execution |
| EMNLP 2026 | June 2026 | Good backup with more time |
| AIES 2026 | March 2026 | AI Ethics and Society; strong thematic fit |

**Recommended primary target: FAccT 2027 or EMNLP 2026** — FAccT is the highest-prestige venue for this topic. If timeline is tight, EMNLP 2026 is the fallback.

**Estimated time to submission-ready:** 12–14 weeks (3 weeks study design + annotation guidelines, 2 weeks data collection, 2 weeks annotation + analysis, 5–7 weeks writing).

---

## Recommended Positioning

> "We study the user-injection angle of multi-turn bias — not whether models produce biased outputs unprompted, but whether they absorb, amplify, and propagate stereotypes that users introduce. Using a controlled injection-and-propagation paradigm across 5 models and 5 stereotype categories, we find [X]. We extend BBQ, WinoBias, and StereoSet to multi-turn settings for the first time, enabling direct comparison with existing single-turn results. The gap between single-turn fairness scores and deployed multi-turn bias rates is [Y]%."

---

*Last updated: 2026-05-28*
