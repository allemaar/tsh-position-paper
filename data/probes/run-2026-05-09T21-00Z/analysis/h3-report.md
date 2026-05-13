# H3 (Off-Token Route) Descriptive Analysis — run-2026-05-09T21-00Z

Pre-reg § 6.3 paired tests:

- **Test 1 (chat A vs chat C):** if H3 holds, the two cold states should look the same → Wilcoxon p > 0.05 (FAIL to reject equivalence) AND mean diff per near-neighbor within ±0.5
- **Test 2 (chat B vs chat C):** if H3 holds, post-intro distinguishability should NOT persist into the re-cold chat → Wilcoxon p < 0.01 (REJECT equivalence) AND chat B substantially higher than chat C

Per pre-reg α = 0.05 for Test 1, α = 0.01 for Test 2. Both must hold to support H3. **Combined:** Test 1 fails to reject AND Test 2 rejects → H3 supported. Reverse pattern → H3 falsified.

## H3 Test 1 — chat A vs chat C (cold replication on novel-targets, n=270 paired NN observations)

- mean cold (chat A) = **1.159**
- mean recold (chat C) = **1.210**
- mean diff (A − C) = **-0.051** (target: |Δ| < 0.5 per near-neighbor)
- Wilcoxon signed-rank: W = 6348.0, **p = 0.3450** (target: p > 0.05 = fail to reject)
- Paired t-test: t = -1.594, p = 0.1120

Per-near-neighbor breakdown:

| NN # | mean(A) | mean(C) | mean diff | Wilcoxon p |
|---|---|---|---|---|
| 1 | 1.193 | 1.174 | +0.019 | 0.5351 |
| 2 | 1.111 | 1.196 | -0.085 | 0.2130 |
| 3 | 1.174 | 1.259 | -0.085 | 0.2776 |

## H3 Test 2 — chat B vs chat C (post-intro vs re-cold on novel-targets, n=270)

- mean post-intro (chat B) = **2.981**
- mean recold (chat C) = **1.210**
- mean diff (B − C) = **+1.772**
- Wilcoxon signed-rank: W = 8.0, **p = 0.000000** (target: p < 0.01 = reject equivalence)
- Paired t-test: t = +63.041, p = 0.000000

Per-near-neighbor breakdown:

| NN # | mean(B) | mean(C) | mean diff | Wilcoxon p |
|---|---|---|---|---|
| 1 | 2.981 | 1.174 | +1.807 | 0.0000 |
| 2 | 2.989 | 1.196 | +1.793 | 0.0000 |
| 3 | 2.974 | 1.259 | +1.715 | 0.0000 |

## Reference: chat B vs chat A (W9 main effect, novel-targets, n=270)

- mean post (B) = 2.981 | mean cold (A) = 1.159 | mean diff (B − A) = **+1.822**
- Wilcoxon p = **0.000000** (target: p < 0.01)

If H3 holds we expect (B − C) ≈ (B − A) (introduction's effect doesn't carry into chat C) and (A − C) ≈ 0 (cold replication holds across fresh chats).

## H3 verdict (descriptive)

- Test 1 pass (|Δ| < 0.5 AND p > 0.05): **✓**
- Test 2 pass (p < 0.01 AND chat B > chat C): **✓**
- **Combined H3: **SUPPORTED****

## Positive-control sanity (n=54 paired NN observations)

- chat A vs chat C: mean(A) = 3.000, mean(C) = 3.000, mean diff = +0.000, Wilcoxon p = nan
- chat B vs chat C: mean(B) = 3.000, mean(C) = 3.000, mean diff = +0.000, Wilcoxon p = nan

(Positive-controls expected to be saturated at 3 across all three chats — all p values likely 1.0 / NaN.)

## Per-cell distinguishability across all three chats

| Cell | Stratum | A (cold) | B (post) | C (recold) | LR_BA | LR_BC | LR_CA |
|---|---|---|---|---|---|---|---|
| claude.cogalent-pruning | nonce | [0.11, 0.11, 0.11] | [3.00, 3.00, 3.00] | [0.78, 0.78, 0.89] | +8.67 | +6.56 | +2.11 |
| claude.coinage-probe | self-ref-paper | [1.67, 1.11, 1.11] | [3.00, 3.00, 3.00] | [1.44, 1.00, 1.33] | +5.11 | +5.22 | -0.11 |
| claude.eggf | author-coinage | [0.44, 0.44, 0.33] | [3.00, 3.00, 3.00] | [1.00, 1.00, 1.00] | +7.78 | +6.00 | +1.78 |
| claude.elastic-automator | author-coinage | [1.00, 1.00, 1.33] | [3.00, 3.00, 3.00] | [1.00, 0.67, 1.22] | +5.67 | +6.11 | -0.44 |
| claude.gradient-descent | positive-control | [3.00, 3.00, 3.00] | [3.00, 3.00, 3.00] | [3.00, 3.00, 3.00] | +0.00 | +0.00 | +0.00 |
| claude.lexical-reachability | self-ref-paper | [1.44, 1.22, 1.44] | [3.00, 3.00, 3.00] | [1.00, 1.00, 1.00] | +4.89 | +6.00 | -1.11 |
| claude.off-token-route | self-ref-paper | [1.11, 1.11, 1.11] | [3.00, 3.00, 3.00] | [1.22, 1.22, 1.22] | +5.67 | +5.33 | +0.33 |
| claude.prismatic-affinity | nonce | [1.56, 1.56, 1.89] | [3.00, 3.00, 3.00] | [1.00, 1.22, 1.11] | +4.00 | +5.67 | -1.67 |
| claude.token-substrate | self-ref-paper | [1.56, 1.33, 1.44] | [3.00, 3.00, 3.00] | [1.56, 1.56, 1.33] | +4.67 | +4.56 | +0.11 |
| claude.token-tax | author-coinage | [0.78, 0.89, 0.89] | [3.00, 3.00, 3.00] | [1.00, 1.11, 1.00] | +6.44 | +5.89 | +0.56 |
| claude.transformer-architecture | positive-control | [3.00, 3.00, 3.00] | [3.00, 3.00, 3.00] | [3.00, 3.00, 3.00] | +0.00 | +0.00 | +0.00 |
| claude.yon-notation | author-coinage | [0.11, 0.11, 0.11] | [3.00, 3.00, 3.00] | [0.89, 1.11, 1.00] | +8.67 | +6.00 | +2.67 |
| gemini.cogalent-pruning | nonce | [2.00, 1.33, 2.22] | [3.00, 3.00, 3.00] | [1.11, 1.00, 1.67] | +3.44 | +5.22 | -1.78 |
| gemini.coinage-probe | self-ref-paper | [2.78, 2.22, 1.33] | [2.78, 2.78, 2.78] | [2.33, 2.11, 1.56] | +2.00 | +2.33 | -0.33 |
| gemini.eggf | author-coinage | [0.89, 0.89, 0.89] | [3.00, 3.00, 3.00] | [1.00, 1.00, 1.00] | +6.33 | +6.00 | +0.33 |
| gemini.elastic-automator | author-coinage | [1.00, 1.00, 1.00] | [3.00, 3.00, 3.00] | [1.00, 1.00, 1.00] | +6.00 | +6.00 | +0.00 |
| gemini.gradient-descent | positive-control | [3.00, 3.00, 3.00] | [3.00, 3.00, 3.00] | [3.00, 3.00, 3.00] | +0.00 | +0.00 | +0.00 |
| gemini.lexical-reachability | self-ref-paper | [1.67, 1.44, 1.44] | [3.00, 3.00, 3.00] | [1.00, 1.00, 1.00] | +4.44 | +6.00 | -1.56 |
| gemini.off-token-route | self-ref-paper | [0.89, 0.89, 0.89] | [2.89, 2.89, 2.78] | [1.00, 1.00, 1.00] | +5.89 | +5.56 | +0.33 |
| gemini.prismatic-affinity | nonce | [1.11, 0.78, 1.00] | [3.00, 3.00, 2.78] | [1.22, 1.00, 1.22] | +5.89 | +5.33 | +0.56 |
| gemini.token-substrate | self-ref-paper | [1.11, 1.11, 1.11] | [3.00, 3.00, 2.89] | [1.00, 1.00, 1.00] | +5.56 | +5.89 | -0.33 |
| gemini.token-tax | author-coinage | [1.22, 1.11, 1.00] | [3.00, 3.00, 3.00] | [1.00, 1.22, 1.11] | +5.67 | +5.67 | -0.00 |
| gemini.transformer-architecture | positive-control | [3.00, 3.00, 3.00] | [3.00, 3.00, 3.00] | [3.00, 3.00, 3.00] | +0.00 | +0.00 | +0.00 |
| gemini.yon-notation | author-coinage | [0.78, 1.00, 0.89] | [3.00, 3.00, 3.00] | [1.00, 1.00, 1.00] | +6.33 | +6.00 | +0.33 |
| gpt55.cogalent-pruning | nonce | [1.33, 1.33, 2.11] | [3.00, 3.00, 3.00] | [1.33, 1.56, 2.11] | +4.22 | +4.00 | +0.22 |
| gpt55.coinage-probe | self-ref-paper | [2.00, 1.67, 1.22] | [3.00, 3.00, 3.00] | [1.78, 1.67, 1.33] | +4.11 | +4.22 | -0.11 |
| gpt55.eggf | author-coinage | [1.44, 1.56, 1.56] | [3.00, 3.00, 3.00] | [1.33, 1.56, 1.67] | +4.44 | +4.44 | +0.00 |
| gpt55.elastic-automator | author-coinage | [1.22, 1.22, 1.22] | [3.00, 3.00, 3.00] | [1.00, 1.00, 1.00] | +5.33 | +6.00 | -0.67 |
| gpt55.gradient-descent | positive-control | [3.00, 3.00, 3.00] | [3.00, 3.00, 3.00] | [3.00, 3.00, 3.00] | +0.00 | +0.00 | +0.00 |
| gpt55.lexical-reachability | self-ref-paper | [1.11, 1.11, 1.11] | [3.00, 3.00, 3.00] | [1.00, 1.00, 1.00] | +5.67 | +6.00 | -0.33 |
| gpt55.off-token-route | self-ref-paper | [1.11, 1.11, 1.11] | [2.78, 3.00, 3.00] | [1.33, 1.33, 1.44] | +5.44 | +4.67 | +0.78 |
| gpt55.prismatic-affinity | nonce | [1.00, 1.00, 1.00] | [3.00, 3.00, 3.00] | [1.00, 1.00, 1.00] | +6.00 | +6.00 | +0.00 |
| gpt55.token-substrate | self-ref-paper | [1.22, 1.22, 1.22] | [3.00, 3.00, 3.00] | [1.33, 1.22, 1.44] | +5.33 | +5.00 | +0.33 |
| gpt55.token-tax | author-coinage | [1.11, 1.44, 2.00] | [3.00, 3.00, 3.00] | [1.56, 2.44, 3.00] | +4.44 | +2.00 | +2.44 |
| gpt55.transformer-architecture | positive-control | [3.00, 3.00, 3.00] | [3.00, 3.00, 3.00] | [3.00, 3.00, 3.00] | +0.00 | +0.00 | +0.00 |
| gpt55.yon-notation | author-coinage | [1.00, 1.00, 1.11] | [3.00, 3.00, 3.00] | [1.00, 1.11, 1.11] | +5.89 | +5.78 | +0.11 |

**LR_BA** = post − cold (the W9 headline LR).  
**LR_BC** = post − recold (how much of the introduction effect *was* in fact erased by removing the introduction).  
**LR_CA** = recold − cold (cold replication across fresh chats; should be near zero per H3).

## Per-stratum H3 summary

| Stratum | mean LR_BA | mean LR_BC | mean LR_CA |
|---|---|---|---|
| author-coinage | +6.08 | +5.49 | +0.59 |
| self-ref-paper | +4.90 | +5.06 | -0.17 |
| nonce | +5.37 | +5.46 | -0.09 |
| positive-control | +0.00 | +0.00 | +0.00 |

## Cold-vs-recold classification consistency (cross-chat, same judge)

Per pre-reg § P6: chat-C classification should match chat-A classification on primary label.

**Overall match rate:** 260/324 = **80.2%**

| Stratum | Match rate |
|---|---|
| author-coinage | 90/108 = 83.3% |
| self-ref-paper | 90/108 = 83.3% |
| nonce | 43/54 = 79.6% |
| positive-control | 37/54 = 68.5% |
