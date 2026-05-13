# Phase 2 Formal Analysis — run-2026-05-09T21-00Z

Pre-registration: v1.0 (2026-05-08). Analysis plan §§ 6.1–6.6.
Run date: 2026-05-12.

> **Leakage scan:** no cells excluded. All novel-target cells included in H1/H2 primary analysis.

## H1 — TSH-core (§6.1)

Novel-target trials: n = 90 | paired near-neighbor observations: n = 270.

| Test | Value | Pre-reg threshold | Pass |
|---|---|---|---|
| Mean panel LR | **+5.467** [95% CI: +5.129, +5.804] | ≥ +3.0 | [ok] |
| Wilcoxon signed-rank (cold vs post) | W = 0.0, p = **< 0.0001** | < 0.01 | [ok] |
| Cohen's d (cold=>post delta) | **+3.084** | ≥ 0.8 | [ok] |
| Bonferroni-corrected p (0.01/4 = 0.0025) | < 0.0001 | < 0.0025 | [ok] |

Mean cold: 1.159 · Mean post: 2.981

**H1 verdict: [ok] SUPPORTED** (all three tests must pass simultaneously)

## H2 — Model-invariance (§6.2)

### Per-model LR (novel targets only)

| Model | n trials | Mean LR | 95% CI | Within ±50% cross-mean |
|---|---|---|---|---|
| Claude Opus 4.7 | 30 | **+6.156** | [+5.528, +6.783] | [ok] |
| GPT-5.5 | 30 | **+5.089** | [+4.630, +5.548] | [ok] |
| Gemini 2.5 Pro | 30 | **+5.156** | [+4.564, +5.747] | [ok] |

Cross-model mean: **+5.467** · Cross-model CV: **0.109** (threshold < 0.5)

### ANOVA / interaction test

Two-way OLS ANOVA (Type II), factors: model x state (cold/post).

| Source | p-value |
|---|---|
| model (main effect) | 0.0002 |
| state (main effect) | < 0.0001 |
| model x state (interaction) | **< 0.0001** |

| Test | Value | Threshold | Pass |
|---|---|---|---|
| All per-model LR > 0 | True | all > 0 | [ok] |
| All within ±50% of cross-model mean | True | all ≤ 50% | [ok] |
| Cross-model CV < 0.5 | 0.109 | < 0.5 | [ok] |
| ANOVA interaction p ≥ 0.01 (no model-dep. effect) | < 0.0001 | ≥ 0.01 | [x] |
| Bonferroni-corrected interaction p ≥ 0.0025 | < 0.0001 | ≥ 0.0025 | [x] |

**H2 verdict: [x] NOT FULLY SUPPORTED** (all four tests must pass)

## H3 — Off-Token Route (§6.3)

Formal table promoted from h3_analysis.py (descriptive) results. Bonferroni correction applied.
Chat-C coverage: 100% of cells (all 108 trials). n = 270 paired near-neighbor observations (novel targets).

> **Pre-reg deviation:** Chat-C scoring added post-hoc beyond HANDOFF-W9 scope to close the H3 rubric gap. Methodology consistent with pre-reg § 6.3. Disclosed in paper §5 as deviation-by-elaboration.

| Test | Value | Pre-reg threshold | Pass | Bonf threshold (0.05/4 = 0.0125) | Bonf pass |
|---|---|---|---|---|---|
| Test 1: chat A vs chat C (fail to reject) | W = 6348.0, p = 0.3450, Δ = -0.051 | p > 0.05, |Δ| < 0.5 | [ok] | p > 0.0125 | [ok] |
| Test 2: chat B vs chat C (reject) | W = 8.0, p = < 0.0001, Δ = +1.772 | p < 0.01 | [ok] | p < 0.0125 | [ok] |

Cold ↔ recold classification match rate: 80.2%

**H3 verdict (pre-registered): [ok] SUPPORTED**
**H3 verdict (Bonferroni-corrected): [ok] SUPPORTED**

## H4 — Positive-control negative test (§6.4)

Positive-control trials: n = 18 | paired observations: n = 54.

| Test | Value | Pre-reg threshold | Pass |
|---|---|---|---|
| Mean panel LR | **+0.000** [95% CI: +0.000, +0.000] | < +1.0 | [ok] |
| Wilcoxon p (cold vs post, fail to reject) | W = nan, p = **1.0000** | ≥ 0.05 | [ok] |
| Bonferroni p ≥ 0.0125 | 1.0000 | ≥ 0.0125 | [ok] |

Mean cold: 3.000 · Mean post: 3.000

**H4 verdict: [ok] SUPPORTED** (both tests must pass)
> H4 failure would invalidate H1 interpretation regardless of H1 outcome.

## Panel-vs-human kappa (pre-reg §4)

Based on **22 human-rated trials** (pre-reg seed `0x4D29_8B1F_6E07_C3A2`, 20% sample).

| Dimension | Weighting | kappa | n observations | Status |
|---|---|---|---|---|
| Cold distinguishability | quadratic | +0.712 [ok] | 66 | [ok] reliable (kappa ≥ 0.7) |
| Post distinguishability | quadratic | n/a | 66 | n/a (degenerate) |
| Confabulation severity | quadratic | +0.412 LOW | 22 | [x] LOW (< 0.5) |
| Refusal of collapse | none | n/a | 66 | n/a (degenerate) |

**Panel decision rule (primary dim: cold distinguishability):** `panel-reliable`

Decision rules: kappa ≥ 0.7 => panel reliable, primary report uses panel-mean scores; kappa ∈ [0.5, 0.7) => expand to 44 trials; kappa < 0.5 => sharpen rubric.

## Stratified analysis — §6.6

Per-stratum mean LR with 95% CI.

| Stratum | n trials | Mean LR | 95% CI | Within-stratum CV |
|---|---|---|---|---|
| alex-coinage | 36 | **+6.083** | [+5.598, +6.568] | 0.244 |
| self-ref-paper | 36 | **+4.898** | [+4.465, +5.331] | 0.271 |
| nonce | 18 | **+5.370** | [+4.410, +6.331] | 0.387 |
| positive-control | 18 | **+0.000** | [+0.000, +0.000] | nan |

**Cross-stratum F-test (three novel strata):** F = 5.225, p = **0.0072**
Cross-stratum CV: **0.109** | Mean within-stratum CV: **0.301**
Novel-strata indistinguishability prediction (p > 0.05 AND cross-CV < 0.5 x within-CV): **[x] novel strata show systematic differences — see §6 discussion**

_Interpretive note: even if p < 0.05 on the F-test (strata differ), this is reported as a §6 finding, not as a disconfirmation of H1 — H1 is tested on the full novel-target pool, not per-stratum._

## Verdict summary

| Hypothesis | Pre-registered verdict | Bonferroni verdict |
|---|---|---|
| H1 — TSH-core | [ok] SUPPORTED | p < 0.0025 |
| H2 — Model-invariance | [x] NOT FULLY SUPPORTED | interaction p < 0.0025 |
| H3 — Off-Token Route | [ok] SUPPORTED | [ok] SUPPORTED |
| H4 — Positive control | [ok] SUPPORTED | [ok] |

Panel reliability: **panel-reliable** (primary kappa = +0.712 [ok])

Figures: `figures/figure1-lr-strip.{png,svg}`, `figure2-model-boxplots.{png,svg}`, `figure3-stratum-boxplots.{png,svg}`
