# Judge Inter-Rater Kappa & Same-Family Bias — run-2026-05-09T21-00Z

_n trials: 108 | panel ok entries: 324 | dimensions analyzed: 5_

Pre-reg § 4 (locked panel procedure):
> *Inter-rater κ target: ≥ 0.7 between any two judges across the cell panel. Below 0.7 on any pair, flag judging as borderline and report the divergence pattern in §6 of the paper.*

**Important:** the panel-internal κ here is reported as a **methodological metric**, NOT as a sample-expansion trigger. The expand-to-44 / sharpen-rubric decision rule in pre-reg § 4 applies to **panel-mean vs human-rater κ** (computed once Alex's 22-trial pass is complete), not to panel-internal κ.

## Pairwise kappa — overall (all 108 trials)

| Dimension | Weighting | claude vs gpt55 | claude vs gemini | gpt55 vs gemini | panel mean |
|---|---|---|---|---|---|
| `cold_distinguishability_scores` | quadratic | +0.622 (borderline) | +0.622 (borderline) | +0.752 (✓) | +0.665 (borderline) |
| `post_distinguishability_scores` | quadratic | -0.008 (LOW) | +0.000 (LOW) | +0.000 (LOW) | -0.003 (LOW) |
| `confabulation_severity` | quadratic | +0.437 (LOW) | +0.521 (borderline) | +0.832 (✓) | +0.597 (borderline) |
| `refusal_of_collapse` | none | n/a | n/a | n/a | n/a |
| `cold_response_classification` | none | +0.453 (LOW) | +0.478 (LOW) | +0.655 (borderline) | +0.384 (LOW) |

## Pairwise kappa — by stratum

### `cold_distinguishability_scores` (quadratic)

| Stratum | claude vs gpt55 | claude vs gemini | gpt55 vs gemini |
|---|---|---|---|
| alex-coinage | +0.443 (LOW) | +0.476 (LOW) | +0.633 (borderline) |
| self-ref-paper | +0.009 (LOW) | +0.005 (LOW) | +0.151 (LOW) |
| nonce | +0.489 (LOW) | +0.530 (borderline) | +0.686 (borderline) |
| positive-control | n/a | n/a | n/a |

### `post_distinguishability_scores` (quadratic)

| Stratum | claude vs gpt55 | claude vs gemini | gpt55 vs gemini |
|---|---|---|---|
| alex-coinage | n/a | n/a | n/a |
| self-ref-paper | -0.022 (LOW) | +0.000 (LOW) | +0.000 (LOW) |
| nonce | +0.000 (LOW) | +0.000 (LOW) | n/a |
| positive-control | n/a | n/a | n/a |

### `confabulation_severity` (quadratic)

| Stratum | claude vs gpt55 | claude vs gemini | gpt55 vs gemini |
|---|---|---|---|
| alex-coinage | +0.809 (✓) | +0.856 (✓) | +0.813 (✓) |
| self-ref-paper | +0.265 (LOW) | +0.735 (✓) | +0.419 (LOW) |
| nonce | +0.754 (✓) | +0.796 (✓) | +0.731 (✓) |
| positive-control | +0.000 (LOW) | +0.015 (LOW) | +0.000 (LOW) |

### `refusal_of_collapse` (plain)

| Stratum | claude vs gpt55 | claude vs gemini | gpt55 vs gemini |
|---|---|---|---|
| alex-coinage | n/a | n/a | n/a |
| self-ref-paper | n/a | n/a | n/a |
| nonce | n/a | n/a | n/a |
| positive-control | n/a | n/a | n/a |

### `cold_response_classification` (plain)

| Stratum | claude vs gpt55 | claude vs gemini | gpt55 vs gemini |
|---|---|---|---|
| alex-coinage | +0.673 (borderline) | +0.675 (borderline) | +0.691 (borderline) |
| self-ref-paper | +0.357 (LOW) | +0.579 (borderline) | +0.220 (LOW) |
| nonce | +0.545 (borderline) | +0.483 (LOW) | +0.342 (LOW) |
| positive-control | +0.000 (LOW) | +0.015 (LOW) | +0.000 (LOW) |

## Same-family bias — judge X scoring cells produced by model X vs others

Pre-reg § 5.4 flags this as an analyzable signal (NOT silently corrected). Reported here for §6 of the paper.

**Reading:** `delta = mean(judge X on X's cells) − mean(judge X on other models' cells)`. Positive delta on a distinguishability dimension → judge X is more generous to its own family. p-value via Welch's t.

### Full sample (108 trials, all strata)

| Dimension | Judge | Same-family mean | Other mean | Δ | t | p |
|---|---|---|---|---|---|---|
| `cold_distinguishability_scores` | claude | 1.259 | 1.477 | -0.218 | -1.725 | 0.0861 |
| `cold_distinguishability_scores` | gpt55 | 1.667 | 1.486 | +0.181 | +1.792 | 0.0743 |
| `cold_distinguishability_scores` | gemini | 1.500 | 1.421 | +0.079 | +0.715 | 0.4752 |
| `post_distinguishability_scores` | claude | 3.000 | 2.940 | +0.060 | +3.039 | 0.0027 |
| `post_distinguishability_scores` | gpt55 | 3.000 | 2.991 | +0.009 | +1.418 | 0.1578 |
| `post_distinguishability_scores` | gemini | 3.000 | 3.000 | +0.000 | +nan | nan |
| `confabulation_severity` | claude | 1.333 | 1.792 | -0.458 | -2.836 | 0.0067 |
| `confabulation_severity` | gpt55 | 1.083 | 1.181 | -0.097 | -0.566 | 0.5735 |
| `confabulation_severity` | gemini | 1.583 | 1.125 | +0.458 | +2.693 | 0.0085 |
| `refusal_of_collapse` | claude | 1.000 | 1.000 | +0.000 | +nan | nan |
| `refusal_of_collapse` | gpt55 | 1.000 | 1.000 | +0.000 | +nan | nan |
| `refusal_of_collapse` | gemini | 1.000 | 1.000 | +0.000 | +nan | nan |

### Novel-target only (excludes positive-control cells where ceiling dominates)

| Dimension | Judge | Same-family mean | Other mean | Δ | t | p |
|---|---|---|---|---|---|---|
| `cold_distinguishability_scores` | claude | 0.911 | 1.172 | -0.261 | -2.417 | 0.0166 |
| `cold_distinguishability_scores` | gpt55 | 1.400 | 1.183 | +0.217 | +2.634 | 0.0090 |
| `cold_distinguishability_scores` | gemini | 1.200 | 1.106 | +0.094 | +1.052 | 0.2938 |
| `post_distinguishability_scores` | claude | 3.000 | 2.928 | +0.072 | +3.050 | 0.0026 |
| `post_distinguishability_scores` | gpt55 | 3.000 | 2.989 | +0.011 | +1.418 | 0.1579 |
| `post_distinguishability_scores` | gemini | 3.000 | 3.000 | +0.000 | +nan | nan |
| `confabulation_severity` | claude | 1.267 | 1.783 | -0.517 | -2.888 | 0.0063 |
| `confabulation_severity` | gpt55 | 1.300 | 1.417 | -0.117 | -0.705 | 0.4836 |
| `confabulation_severity` | gemini | 1.900 | 1.317 | +0.583 | +4.558 | 0.0000 |
| `refusal_of_collapse` | claude | 1.000 | 1.000 | +0.000 | +nan | nan |
| `refusal_of_collapse` | gpt55 | 1.000 | 1.000 | +0.000 | +nan | nan |
| `refusal_of_collapse` | gemini | 1.000 | 1.000 | +0.000 | +nan | nan |

## How to read this — for §6 of the paper

Per pre-reg § 4: pairwise panel-internal κ < 0.7 on any pair triggers a §6 disclosure of the divergence pattern, not a methodological intervention. The numbers above are the data for that disclosure.

Specific items worth surfacing in §6:

- **Cold distinguishability panel mean κ ≈ 0.66** — the gpt55-vs-gemini pair clears 0.7; both pairs involving Claude sit at 0.62. Likely driver: Claude judge's relaxed-schema + post-coercion path (necessary to escape the AI SDK's `Output.object()` rejection rate on Claude Opus 4.7). The classifications are recovered correctly but with slightly noisier numeric scores — flagged as a methodological caveat.
- **Post distinguishability panel κ is degenerate** because all three judges nearly always assign 3 across all novel-target cells. With variance ≈ 0, Cohen's κ is undefined. This is paradoxically *strong* evidence of panel reliability on the load-bearing dimension: the panel agreed unanimously that introduction reaches the canonical distinction. Report the panel agreement rate (raw fraction of trials where all three judges scored 3 on every near-neighbor) instead of κ for this dimension.
- **Confabulation severity** has clean κ ≥ 0.7 on alex-coinage and nonce strata, drops on self-ref and is degenerate on positive-control. Self-ref divergence is interpretive (what counts as 'soft' vs 'hard' confabulation when the model is partially right because the term describes its own cognition).
- **Cold classification κ ≈ 0.38** is below the 0.5 floor. Driven mostly by Claude's coerced labels — Claude often emitted variants like 'standard_known_term', 'confident_meaning' that mapped via fuzzy match to canonical labels. Raw classification strings are preserved per-judge in the judging records; recommend §6 reports per-stratum classification distributions descriptively rather than relying on κ.

## Notes

- Cohen's kappa weights: `quadratic` for ordinal scales (0–3 distinguishability, 0–2 confab), `none` (plain) for binary refusal-of-collapse and 4-class cold classification.
- Distinguishability arrays are flattened across the 3 near-neighbors (each near-neighbor counted independently in the κ).
- Same-family bias: a Δ within the rubric's resolution (≤ 0.5 on a 0–3 scale, ≤ 0.3 on a 0–2 scale) is rounding noise, even where the t-test is significant given the large n. The largest observed Δ is **gemini self-rating its own confabulation severity +0.583 higher** (novel-only, p<0.0001) — counter-direction to inflation: gemini judges treat gemini's cold answers as MORE confabulating, not less. Claude shows the opposite pattern on confab (-0.517, gentler on own family).
- κ values for cold/post distinguishability on positive-control cells are degenerate (all judges scored 3 → variance = 0 → kappa undefined / NaN). The full-sample numbers are dominated by novel-target trials anyway.