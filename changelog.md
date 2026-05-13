# Changelog

All notable changes to this paper.

## v0.4.1 — 2026-05-13

**LaTeX bundle + data-path convention update.** Pre-Overleaf-render cleanup. No content changes to the paper's argument or empirics.

- **LaTeX bundle generated** at `latex/`. Overleaf-ready: `paper.tex` (with arXiv-friendly preamble modelled on EA's), `references.bib` (31 BibTeX entries derived from paper.md §References + 22 unique citation keys resolved across the body), and `latex/figures/` mirror of the six PNG figures. Compile sequence: `pdflatex → bibtex → pdflatex → pdflatex`. All three travel-units preserved verbatim in the LaTeX. Tables 1, 1a, 2 use `booktabs` formatting; figures 1/2/3 (infographic plates) use `\textwidth`, figures 4/5/6 (analysis charts) use `\columnwidth`.
- **Data bundle path convention updated.** Moved `wip/data/probes/run-2026-05-09T21-00Z/` (12 MB, 399 files) to `data/probes/run-2026-05-09T21-00Z/`. The vault and the public-repo paths now agree on the clean `data/probes/` path per publishing-guide convention; `wip/` is reserved for working-draft material that does not ship. Paper.md §A (L484) and Appendix C (L492) updated to match. Added a Path-convention note in Appendix C explaining that the locked pre-spec doc (deposited as the authoritative artifact) references the pre-deposit `wip/data/probes/{run_id}/` working layout at lock time (2026-05-08); the SHA-256 hash binds the document text, not the deposit-side directory layout. The dryrun and smoke-test subdirectories remain under `wip/data/probes/` (gitignored; do not ship).
- **Three small parallel polish edits** (author-direct, not in any worker scope): README.md L41 bibtex `version` bumped to `0.4.0`; paper.md L283 "the H2 interaction block" → "The H2 interaction block" (sentence-start capitalization); paper.md L386 "complements the v2 controls described in §8 generalization-beyond-the-boundary direction" tightened to "complements the v2 controls in §8 by testing downstream use rather than boundary distinguishability alone"; .zenodo.json version bumped to `0.4.0` in the same author-direct pass.
- **Frontmatter and CITATION.cff version bumped** to v0.4.1; README banner refreshed.
- **Three travel-units preserved verbatim** at L28 (Abstract Option δ closer), L396 (§7.1 standalone slogan), L432 (§9 not-X-but-Y opener).

v0.4.1 is the **LaTeX-ready publication candidate**. Next step: zip the `latex/` folder, upload to Overleaf, compile to PDF.

## v0.4.0 — 2026-05-13

**Final-polish RC bundle — last review-round catches resolved.** Two ChatGPT reviewers landed final mechanical and semantic catches. All 8 are valid and applied; one (Appendix C κ disambiguation) uses a more accurate rewrite than the reviewer suggested. Thesis, travel-units, and bounded-conclusion framing are untouched. This is the publication-candidate state.

- **Figure 2 caption rewritten.** Previous caption misassigned the P1–P6 protocol steps (claimed "cold elicitation P1–P3 → definition injected P4 → post-introduction P5–P6"; actual §3.2 is P1=cold question, P2=classification, P3=definition introduction, P4=boundary test, P5=scoring, P6=re-cold check). New caption uses the chat-A/B/C narrative the protocol is built around, with correct P-references.

- **"§8 internal-note" phrasing cleaned.** Wave-10 had replaced broken `§8.4` cross-references with `the Off-Token-Route v2 controls block in §8` — six occurrences. The phrase read as an internal note (§8 has no block with that title; it's flat). Replaced everywhere with `the v2 controls described in §8`.

- **"the the" typo fixed** at L386 (single residual from Wave-10 sed pass).

- **"Four orders of magnitude" magnitude claim corrected.** Two sites (§6 H2 disconfirmation paragraph; Appendix C Bonferroni paragraph). The math is ~2.1 orders, not four (log₁₀(0.0025 / 1.78×10⁻⁵) = 2.15; factor of ~140). Replaced with explicit ratio language ("fails it decisively, factor of ~140") in §6 and "crosses the family-wise significance threshold and therefore triggers the pre-specified H2 disconfirmation rule" in Appendix C.

- **H2 "passes" wording trap resolved** in Appendix C. Previously read "passes the family-wise threshold" which inverts the H2 verdict (H2 is *disconfirmed* by that crossing). Resolved jointly with the magnitude rewrite above.

- **Pre-spec hash claim honestly bounded** in Appendix C "Hash methodology" paragraph. Previous wording overclaimed cryptographic registration ("the substantive guarantee that the analyses reported in §5 are the analyses that were registered"); rewritten to "cryptographically auditable pre-specification rather than a public preregistration" — explicit acknowledgment that no public timestamping service (OSF / AsPredicted) was used. Consistent with the paper's own §3.6 framing at L221.

- **Appendix C κ threshold disambiguated.** The previous wording mashed together the pairwise judge-judge κ target with the panel-vs-author decision-rule cascade. The pre-spec (`wip/03-pre-registration.md` L94–95 and L105–108) establishes these as **two separate** thresholds: (a) panel-internal pairwise κ ≥ 0.7 across the cell panel, with "below 0.7 on any pair → flag as borderline + report divergence" decision rule; (b) panel-vs-author κ ≥ 0.7 as the decision rule for accepting panel-mean scores. Rewrite names both targets explicitly and reports each outcome (under (a) the panel is borderline with divergence reported in §6; under (b) κ = +0.712 above threshold, panel-mean accepted).

- **Vaswani 2017 restored.** Wave-10 audit had deleted as orphan, but §1.5 (L74) discusses transformer forward passes and the positive-control set includes "transformer-architecture" — there is a clean citation hook. Entry restored to References at alphabetical position; one inline cite added at L74 ("Transformer forward passes (Vaswani et al. 2017) do produce internal representations...").

- **DEFERRED to PDF render**: public-facing frontmatter cleanup (`status: wip` → `release-candidate` or removed; `doi: "{{TBD}}"` template; author wikilink → plain string). These are render-time concerns; the vault Markdown remains the canonical source with Obsidian-flavored YAML.

- **Three travel-units still preserved verbatim** at L28 (Abstract Option δ), L390 (§7.1 standalone slogan), L426 (§9 not-X-but-Y opener).

v0.4.0 is the publication candidate. Substantive content is locked from here through v1.0.0 Zenodo deposit — only PDF render, public-repo scaffolding, and DOI backfill remain as mechanical steps.

## v0.3.7 — 2026-05-13

**Infographic injection + figure renumber for narrative order.** Three Calm-Futurism-style infographic plates (Variant A "Boundary Shift", Variant B "Wittgenstein Flip", Variant C "Coinage Probe Shape" — per `figure-infographic-brief.md`) generated and embedded in the paper at their narrative positions. Existing analysis figures renumbered to preserve sequential-by-appearance ordering.

- **Figure renumber (Scheme 1 — full renumber, narrative order):**
  - `fig1-lr-strip` → `fig4-lr-strip` (§5.2 per-trial detail)
  - `fig2-model-boxplots` → `fig5-model-boxplots` (§5 per-model H2)
  - `fig3-stratum-boxplots` → `fig6-stratum-boxplots` (§6 stratified analysis)
- **New infographics embedded at narrative positions:**
  - `fig1-infographic-wittgenstein-flip` at §2 (after L86 architectural-flip paragraph) — Variant B
  - `fig2-infographic-coinage-probe-shape` at §3 (Methods overview, after first protocol-summary paragraph) — Variant C
  - `fig3-infographic-boundary-shift` at start of §5 Results (lede image) — Variant A (primary)
- **README hero added.** Variant A (boundary-shift) inserted at top of README.md as the GitHub-landing social tile. Matches the brief's recommendation to ship Variant A as v1.
- **README figure list updated** to reflect all six new filenames in two groups (infographics + analysis figures).
- **All inline `Figure N` cross-references updated** in paper.md (L195, L242, L354) to point at the new numbers (Figure 3 → Figure 6 in two locations; Figure 1 → Figure 4 in one location).
- **WebP web-optimised converts generated** alongside each PNG (3 analysis figures + 3 infographics × 2 formats = 9 new files). PNGs are the deposit asset; WebPs are for future web injection (deferred — separate decision).
- **Three travel-units still preserved verbatim** at locations L28 / L390 / L426.

The numbering scheme is now reader-stable: figures appear in numeric order through the paper. This is the **citation-stable** state — figure numbers will not change between v0.3.7 and v1.0.0 deposit. Reviewers can cite `Figure 3` and the reference will hold across the deposit lifecycle.

v0.3.7 is the deposit-ready state with the full infographic suite. Next steps: web-app injection (deferred — separate publishing decision), Overleaf PDF render, public-repo scaffold.

## v0.3.6 — 2026-05-13

**Wave-11 deposit-readiness bundle — closure of all deferred audit items.** Closes the five Wave-10-deferred items plus one polish, locking deposit-readiness.

- **Sapir-Whorf References anchors added** (P1, audit item). Body §2.1 (line 84) had named Heider, Rosch, Lupyan, and Casasanto without bibliographic anchors. Four canonical entries added to References: Heider 1972 (color-naming universals); Rosch 1973 (natural categories); Lupyan 2012 (label-feedback hypothesis); Casasanto & Boroditsky 2008 (time-in-the-mind, weak-Whorf reaction-time evidence). Inserted at alphabetical positions. Body prose unchanged — flow already locked.

- **d_cell SD recomputed with explicit formula** (P1, audit item). The Wave-9 reported value `between-cell SD = 1.371` could not be reproduced under any standard SD computation. Recomputed from 30 cell-mean LR values (built from raw `judging-{1,2,3}.json` files): sample SD (ddof=1) = 1.383, yielding Cohen's d_cell = 3.95 (was reported as 3.99). §5.2 now reads `between-cell sample SD = 1.383, ddof=1` with explicit divisor. Abstract / §5.2.1 / §9 / README / .zenodo.json / CITATION.cff updated in parallel. Headline d > 3 claim survives unchanged; the change is the third-decimal SD reproducibility lock-in.

- **Welch's t reproducibility resolved** (P1, audit item). The Wave-9 reported value `Welch's t = +1.91, p = 0.058` (GPT-judge own-family sanity check) reproduces *exactly* from raw `judging-{1,2,3}.json` files under full-sample observation-level Welch (n_own = 90, n_other = 180). The audit retro had checked `judge-kappa-data.json` (a different intermediate aggregation) and gotten t = +1.792 / p = 0.0743 — that was a wrong-intermediate-file artifact, not a paper drift. Method-clarifier annotation added to §6.2 so the reader can reproduce: `(full-sample observation-level; n_own = 90 vs n_other = 180)`. No number change.

- **Appendix C completeness** (P2). Added one sentence introducing the pre-specified stratified §6.6 analysis (Alex's M5 addition, defense against self-referential-term circularity). Appendix C now covers all of H1–H4 + Bonferroni + hash + stratification.

- **Whorf 1956 body citation added** (P2). References had Whorf 1956 entry but body never cited it by year. Added one inline `(Whorf 1956)` in §2 (or §1.4 — verify final placement).

- **Backup directory removed.** `figures/_pre_wave10_backup/` deleted; the Wave-10 commit `69b3891` is the rollback target if needed.

- **Three travel-units still preserved verbatim**: Abstract Option δ closer ("the externally writable in-context token sequence IS the cognitive substrate"), §9 not-X-but-Y opener, §7.1 standalone slogan.

v0.3.6 is the **post-audit deposit-ready state — all P0 + P1 + P2 items resolved**. Next step: paper.pdf render via Overleaf LaTeX route, then public-repo scaffolding for the Zenodo deposit.

## v0.3.5 — 2026-05-13

**Pre-deposit drift audit + Wave-10 micro-fix bundle.** A fresh-session new-session drift audit ([[../../Handoffs/TSH-paper/retros/2026-05-13-v0-3-4-pre-deposit-drift-audit-retro|retro]]) verified all 36 Table 1 cells, all four hypothesis verdicts, all three travel-units, and re-ran two Python scripts (cell-level Wilcoxon, pairwise κ) — all matched the paper exactly. Audit verdict: material-drift, fixable. Wave-10 applied the fix bundle.

- **Frontmatter version + date bumped.** `version: "0.3.0"` (stale since v0.3.1) → `"0.3.5"`; `date: "2026-05-12"` → `"2026-05-13"`. Worker GG's v0.3.4 scaffolding-sync wave had excluded paper.md frontmatter from scope; v0.3.5 closes that gap.

- **§5.2.1 Gemini cold-mean corrected.** Cited as `Gemini 1.26` was actually `1.23` per `h3-data.json` cell_summary (verified two ways: per-cell mean across 10 Gemini novel cells, and observation-level panel-mean across 90 near-neighbor obs). Single-number P0 fix.

- **Eleven broken §X.Y cross-references fixed.** Wave-5b body collapse flattened §6/§7/§8 (no subsections) but left §6.2, §6.5, §8.1, §8.4 references pointing into subsections that no longer exist. All eleven replaced with phrase identifiers naming the relevant flat-section block: `§8.4` → `the Off-Token-Route v2 controls block in §8` (6 occurrences); `§6.2` → `the H2 interaction block in §6` (3 occurrences); `§8.1` → `§8 (Limitations)` (1 occurrence); `§6.5` → `the stratified-analysis block in §6 (see Table 2 and Figure 3)` (1 occurrence). No information lost — content was always in the named flat section; the dead-link literals are gone.

- **Three References orphans deleted.** Bender et al. 2021 (Stochastic Parrots), Frankle & Carbin 2019 (Lottery Ticket Hypothesis), Vaswani et al. 2017 (Attention Is All You Need) — all listed in References but never cited in body. Deleted to clean the orphan-citation surface.

- **Appendix C convention residual cleaned.** One residual `pre-registered seed` at line 488 → `pre-specified seed` (Wave 7 Worker BB renamed 22 occurrences across the body; this one was missed).

- **Frontmatter wikilink repointed.** `[[../token-bound-automation/paper|...]]` pointed to a non-existent file; repointed to `[[../token-bound-automation/README|Token-Bound Automation (follow-up, planned)]]` (the README does exist).

- **Figures fig1 and fig3 regenerated with `author-prior` facet/tick labels.** Wave 7 v0.3.2 had renamed `alex-coinage → author-prior` in captions but the SVG facet labels (fig1) and x-axis tick labels (fig3) still showed `Alex-coinage`. Re-rendered both figures with the unified `Author-prior` label. Additionally, fig3 now drops the `Positive control` panel from `strata_order` to match the existing caption claim that positive-control is omitted (caption said omitted; SVG had plotted it). fig2 (per-model boxplots) regenerated identically for completeness.

- **README abstract collapsed to single paragraph.** README abstract was split into two paragraphs at the bolded closer; paper.md abstract has always been a single paragraph. Merged to match paper.md verbatim (per scaffolding-follows-source rule).

- **.zenodo.json description collapsed to single `<p>`.** Mirror fix for the README abstract paragraph-break drift. Both deposit-side carriers now match paper.md's single-paragraph presentation verbatim.

- **CITATION.cff version bumped** to `0.3.5` (abstract paraphrase unchanged).

- **Three travel-units still preserved verbatim**: abstract Option δ opener ("the externally writable in-context token sequence IS the cognitive substrate for category-use"), §9 not-X-but-Y opener, §7.1 standalone slogan ("Notation design IS brain design for LLMs.").

**Deferred to Wave-11** (post-audit author-decision items): (a) Heider/Rosch/Lupyan/Casasanto Sapir-Whorf references — body §2.1 names these authors without bibliographic anchors; author decides add-4-refs vs. soften-body-to-attribution-only; (b) `d_cell` SD = 1.371 reproducibility — source compute script not located; recompute with explicit formula and restate, or locate Worker AA's script; (c) GPT-judge Welch's t = +1.91 / p = 0.058 reproducibility — same; (d) Appendix C one-sentence stratified-analysis mention (P2 polish); (e) Whorf 1956 References entry — add body cite or delete (P2).

v0.3.5 is the post-audit deposit-ready state.

## v0.3.4 — 2026-05-13

**Outside-review hardening pass v4 — final cleanup before deposit.** A fifth external review pass (two ChatGPT reviewers, prompted by the author) flagged 7 cleanup issues + one substantive scope question on the pairwise κ data. All addressed.

- **Appendix C added** (~600 words). Substantive summary of the pre-specification protocol: hypothesis statements H1–H4 with falsification thresholds, sample sizes and stopping rules, judging rubric structure, Bonferroni correction, hash methodology, and Zenodo deposit pointer. The paper body references Appendix C six times (in §3, §4, §5); the section now exists. The full pre-specification document is deposited as a separate Zenodo bundle artifact.

- **Cell-level Wilcoxon p-value now explicitly reported in §5.2 H1.** The pre-spec conjunction required Wilcoxon p < 0.01; v0.3.3 reported observation-level p (10⁻⁴⁶) only. Computed under orchestrator one-time exception (third such; same pattern as pairwise κ and prior judge-family extractions): cell-level Wilcoxon signed-rank test on the 30 novel model×term cell-mean LR values yields W = 465 (all 30 cells positive), exact two-sided p = 1.86 × 10⁻⁹ (normal-approximation p = 1.73 × 10⁻⁶). Passes pre-spec α = 0.01 by wide margin. The pre-spec conjunction is now fully reported at the cell level.

- **Pairwise κ now reported at TWO scopes.** v0.3.3 reported novel-only κ (n=270, excluding positive controls): +0.29 / +0.27 / +0.49 — all below 0.7. The pre-spec threshold scope was "across the cell panel" which includes positive controls; the run-analysis report (`judge-kappa-report.md`, generated at data collection) has those values: +0.622 / +0.622 / +0.752 — two pairs borderline, one clears 0.7. v0.3.4 reports BOTH scopes side-by-side with explicit explanation that positive controls trivially agree at the ceiling and inflate the all-trials κ. Transparent and matches both pre-spec scope and the substantive measurement domain.

- **κ discretization method disclosed.** Standard practice for ordinal κ between fractional panel-mean and integer author scores is to round before computing κ. Added one sentence to §5.2 Panel reliability paragraph: "Panel-mean scores were rounded to the nearest rubric category (0/1/2/3) before computing quadratic-weighted Cohen's κ against the author's integer ratings, following the standard ordinal-κ discretization convention." Closes a statistical-method-clarity gap.

- **H4 wording softened consistently** (§6.1 Discussion). "Specific to low-attestation terms (H4)" overclaimed because H4 is ceiling-limited (already softened in §5.2). Now reads "absent on ceiling positive controls (H4)" — accurate at both reporting sites.

- **§1.4 Contributions item 2 parenthesized.** "3 frontier models × 10 low-attestation coined targets plus 2 positive controls = 36" parsed ambiguously. Now reads "3 frontier models × 12 terms, comprising 10 low-attestation coined targets and 2 positive controls, yielding 36 model×term cells."

- **§5.2 estimator phrase softened.** "Is what produces the reliable cell-level estimator" → "is therefore essential to the reported estimator; individual-judge scores are noisier and not the unit of inference." Honest about the pairwise κ context (panel-mean carries the inference, not individual judges).

- **Three travel-units still preserved** unchanged: abstract opener Option δ ("IS the cognitive substrate for category-use"), §9 closing-line rhythm ("not a channel to a deeper cognitive medium but the medium itself"), §7.1 standalone slogan ("Notation design IS brain design for LLMs.").

- **Scaffolding files synced** to v0.3.4 (README.md, CITATION.cff, .zenodo.json); paper.md abstract unchanged from v0.3.3.

This is the final substantive-content cycle; v0.3.4 is the deposit-ready state pending paper.pdf rendering and public-repo scaffolding (user-side hand-offs).

## v0.3.3 — 2026-05-13

**Outside-review hardening pass v3 + pairwise judge-judge κ computed and reported.** A third external review pass (ChatGPT, prompted by the author) flagged residual two-voices inconsistencies between the v0.3.2 abstract opener (Option δ: bold-and-precise) and several body locations that still carried the unqualified maximal claim. The hybrid plan applied here preserves every quotable IS-substring (the "must travel" criterion) while closing the two-voices reviewer attack across §1.4 Contributions, §9 Conclusion, and §Ethics Statement. A new pairwise judge-judge κ analysis (newly computed under orchestrator one-time exception) is also reported, honoring the §3.5/§4.1 promise made in v0.3.0 that the paper did not previously deliver.

- **Hybrid two-voices consistency** (preserves quote-shapes; closes attack):
  - §1.4 Contributions item 1: Option δ qualifier applied around "IS the cognitive substrate" + Nefdt re-attributed to match §2.5 (the "linguistic but not cognitive" phrase is now framed as a question from Nefdt, not as Nefdt's full characterization).
  - §9 Conclusion opener: trailing-qualifier added AFTER the "not X but Y" punch — *"... but the medium itself — at the level of what is externally writable, the medium through which session-level category-use is constituted."* The quotable substring "is not a channel to a deeper cognitive medium but the medium itself" survives intact for citation.
  - §Ethics statement: "arguing the substrate IS the cognition" → "arguing that externally writable vocabulary partly constitutes session-level cognition"; "shifts the alignment conversation" → "adds a vocabulary-level handle to the alignment conversation alongside weights-level work."
  - §7.1 slogan ("Notation design IS brain design for LLMs.") unchanged — already in body where supported.

- **Pairwise judge-judge κ NEW DATA**:
  - Computed from raw per-cell judging logs (n=270 per-neighbor paired observations per judge pair, spanning 30 novel-target cells × 3 trials × 3 near-neighbors). Cold-state distinguishability dimension.
  - Quadratic-weighted Cohen's κ: Claude × GPT-5.5 = +0.29; Claude × Gemini = +0.27; GPT-5.5 × Gemini = +0.49.
  - Unweighted Cohen's κ: +0.26, +0.19, +0.39 respectively.
  - All three pairwise judge-judge κ values are below the 0.7 reliability threshold conventionally used for individual-rater consistency.
  - Panel-mean-vs-author κ remains +0.712 (above threshold).
  - **Interpretation:** The aggregation discipline — three judges, panel-mean as the primary score — produces the reliable cell-level estimator; individual-judge precision is noisier. The panel works via aggregation, not via individual-judge agreement. The headline H1/H2/H3/H4 results all use panel-mean and are unaffected.
  - New paragraph "Pairwise judge-judge agreement" added in §5.2; §8.1 expanded to acknowledge per-judge variance.

- **Remaining bug fixes** (residuals from prior passes):
  - §1.4 Contributions item 2: "12 coined terms" → "10 low-attestation coined targets plus 2 positive controls" (Worker BB fixed abstract in v0.3.2 but missed this enumeration).
  - §5.1 Table 1 intro: "30 of 30 Claude and GPT-5.5 novel-target cells reach exactly 3.00" → accurate cell-level breakdown (Claude 10/10, GPT 9/10, Gemini 6/10; 25/30 at exact 3.00, remaining 5 near ceiling). Same bug Worker BB fixed in §5.2.1 but missed here.
  - §6.1: "twelve coined terms tested" → "ten low-attestation coined targets tested (alongside two positive controls)."

- **Conceptual softening** (honesty without losing position):
  - §6.1 H3+H4 threshold-raising paragraph rebalanced: H3 carries primary weight (boundary movement does not persist across sessions — direct evidence against latent-knowledge persistence); H4 acknowledged as ceiling-limited; v2 controls in §8.4 named as decisive separator from generic definition-following.
  - §2.4 closing line: "two framings generate different predictions at the boundary the probe targets" → "in the v2 control battery (§8.4) — particularly the definition-without-coined-label condition, which discriminates label-binding from generic definition-following." (Aligns with the v0.3.2 §2.4 rewrite that conceded ICL parity.)
  - §3.5 / §4.1 "pairwise inter-rater Cohen's κ is computed and reported" → "inter-rater agreement is computed at two levels — pairwise judge-judge Cohen's κ and panel-mean-vs-author Cohen's κ, both reported in §5.2" (now actually true after Worker DD's §5.2 insertion).
  - §8.1: "the panel is reliable on the primary dimension" → "panel-author agreement exceeded the pre-specified threshold on the primary dimension, so panel-mean scores are used for the primary analysis"; appended pairwise-κ context.

- **Three travel-units preserved** (the "quotable" criterion):
  - Abstract opener: "**IS the cognitive substrate for category-use**" (Option δ; v0.3.2).
  - §9 Conclusion opener: "is not a channel to a deeper cognitive medium but the medium itself" (closing-line rhythm intact).
  - §7.1 standalone slogan: "Notation design IS brain design for LLMs." (unchanged).

- **Scaffolding files synced** to v0.3.3 (README.md, CITATION.cff, .zenodo.json); paper.md abstract unchanged from v0.3.2; only the body changed.

## v0.3.2 — 2026-05-12

**Outside-review hardening pass v2.** A second external review pass (ChatGPT, prompted by the author) surfaced 14 residual issues spanning P0 bugs, P1 framing overclaims, P2 stylistic looseness, and a two-voices inconsistency between the abstract opener and the bounded closer added in v0.3.1. All 14 categories addressed.

**Abstract opener: bounded-and-precise (Option δ).** Retained "**IS** the cognitive substrate" verbatim (the user's preferred visceral framing) but added pre-empting qualifiers — "**externally writable**" before "in-context token sequence", "for category-use" scope, and a closing handle-clause ("the only handle that is movable from outside the weights"). This keeps the visceral declarative shape while closing off the easiest reviewer attack on the internal-substrate distinction (weights / activations / KV-cache).

**P0 bug fixes (terminology and arithmetic):**
- §1.1 residual "twelve coined terms with low training-attestation" corrected to "ten low-attestation coined targets, and two positive controls" (matches v0.3.1 abstract terminology; was missed in the prior pass).
- §5.1 Table 1 intro "ΔLR = Σ(D_post − D_cold) across three trials" corrected to "across the three near-neighbors per trial, averaged across the three trials in each model×term cell."
- §5.2.1 ceiling-effect numerical inconsistency corrected: prior "All 30 of 30 GPT-5.5 novel-target post-cells are exactly at 3.00" replaced with the accurate cell-level breakdown (Claude 10/10, GPT 9/10, Gemini 6/10; 25 of 30 at exact 3.00). Downstream "89 of 90" → "25 of 30" with corresponding prose adjustment.
- §5.2 H3 Test 2 "Mean post–recold ΔLR = +1.77" relabeled to "Mean post–recold per-near-neighbor distinguishability difference = +1.77 (equivalent to roughly +5.31 in summed-LR units across three neighbors)" — +1.77 was a per-NN value, not a summed LR value.
- §6.2 "a Wave 4 reviewer prompted by the author flagged..." line removed (informal; broke scholarly voice). Replaced with "an earlier constraint-derived version of this table overstated the judge-side bias pattern..."

**P1 conceptual-claim softening:**
- §2.4 ICL contrast paragraph rewritten to concede ICL parity ("TSH and a generic in-context-learning account both predict improvement after a supplied definition") and explicitly defer the decisive substrate-vs-style discrimination to the v2 controls in §8.4 — particularly the definition-without-coined-label condition.
- §5.2 H4 result softened from "confirms boundary movement in H1 is not a generic information-injection effect" to "supported under the pre-specified criterion, with a ceiling caveat... consistent with specificity but does not by itself rule out a generic information-injection account." The v2 control battery in §8.4 carries the decisive negative-test load.
- §7.2 alignment overclaim "There is nothing under the tokens to align with; there is only what the tokens carry" replaced with "There may be weights-level dispositions underneath the tokens, but there is no directly writable hidden intent that vocabulary simply reveals. At the session level, vocabulary is one of the few handles we can deliberately write into the system's working medium."
- §1.1 closing two-voices residue aligned with the new δ abstract opener (externally writable framing instead of "the substrate itself").

**P2 stylistic tightening:**
- Table 1, Table 2, Figure 1 caption, Figure 3 caption: `alex-coinage` data label → `author-prior` across 7 occurrences (matches the body-prose rename from v0.3.1).
- "zero real attestation" / "zero attestation" → "no public-web attestation found under exact-phrase searches at coinage time" across 3 occurrences (training-data attestation is unknowable from outside; the operational check is web-search-zero, not training-data-zero).
- **"Pre-registered" / "pre-registration" → "pre-specified" / "pre-specification"** across 22 occurrences. The analysis plan was locked locally on 2026-05-08 and SHA-256-hashed in the run manifest before data collection on 2026-05-09, but was not publicly timestamped until the (planned) Zenodo deposit at v1.0.0 — so it is *pre-specified and hashed* rather than *pre-registered* in the OSF / AsPredicted public-timestamp sense. New italic footnote in §4.5 explains the protocol.

**Wittgenstein 5.6 line kept in the abstract** per the author's voice preference (deliberate rhetorical reach; the line repeats in §1.2 where it's defended).

**Scaffolding files synced** (README.md, CITATION.cff, .zenodo.json) to match the new paper.md abstract and the v0.3.2 version tag.

## v0.3.1 — 2026-05-12

**Outside-review hardening pass.** External review (ChatGPT, prompted by the author) flagged seven correctness/framing issues plus a methodological red flag on derived cell values in §5.2. Author verified Nefdt 2026 quotes against the PhilArchive NEFWIL PDF (3/4 exact, 1 needed re-attribution).

- **Terminology bug fixed throughout.** Replaced "108 cells × 3 near-neighbors = 324" with the correct "36 model×term cells, 108 trials, 324 paired distinguishability measurements" across Abstract, §1.4, §4.4, README, CITATION.cff, .zenodo.json.
- **Table 1 caption corrected.** "Sum of (D_post − D_cold) across three trials" → "summed across the three near-neighbors per trial (max 9.0 per trial); cell-level ΔLR is the mean across the three trials" (math now matches).
- **Abstract closer bounded.** "The Token-Substrate Hypothesis is supported across the tested panel: notation design IS brain design for LLMs" → "These results support a bounded version of the Token-Substrate Hypothesis: in-context vocabulary functions as an externally writable substrate for LLM category use. For deployed LLM systems, notation is therefore not mere packaging; it is a design surface that shapes what distinctions the system can reliably use." The slogan "notation design IS brain design" remains as the §7.1 bolded lead.
- **Coined-targets count corrected.** "12 coined terms with low training-attestation" → "10 low-attestation coined targets plus 2 positive controls" (the positive controls are high-attestation by construction).
- **§5.2 cell-level d_cell = +3.99 promoted to primary headline.** Observation-level Wilcoxon p = 2.66 × 10⁻⁴⁶ and d = +3.08 relegated to a clustering-caveat follow-on flagged as inflation-vulnerable due to clustered observations being treated as independent.
- **§2.5 Nefdt passage re-attributed.** "Linguistic but not cognitive" now framed as a phrase from Nefdt's question (not as Nefdt's full characterization). Karpathy explicitly attributed as "quoted by Nefdt." Author verified all four quoted passages against PhilArchive NEFWIL PDF.
- **Author-rated audit framing.** "Validated against a pre-registered 22-trial human-rater sample" → "compared against an author-rated 22-trial audit sample (panel-vs-author Cohen's κ = +0.71)" across Abstract, §3.5, §4.5, §5.2, §8.1, README, CITATION.cff, .zenodo.json. §8.1 expanded to acknowledge the author-rater limitation and name 2–3 blind independent raters as v2 work.
- **§8.4 control battery added.** Named definition-without-coined-label as the critical v2 control distinguishing TSH from generic in-context learning. Complementary controls (wrong-definition, unrelated-definition, coined-label-without-definition, delayed-test-after-distractor-turns, downstream-use task) catalogued.
- **External/internal substrate distinction strengthened.** Five new occurrences of "externally writable" qualifier across §2.5, §6.6 to prevent reads of "tokens ARE the cognition" without qualification.
- **Sapir-Whorf softened.** "The strong form is the floor for LLMs" → "the architectural default." Unreachable-distinctions claim softened to acknowledge LLM compositional reach.
- **Mind-reading language softened in §1.1.** "Could not reach the concept" → "did not produce the relevant distinction cold"; "now held distinctions" → "now produced stable distinctions."
- **"Alex-coinage" → "author-prior coinage" in body prose.** Raw stratum labels in Table 1, Table 2, and Figure captions retained as "alex-coinage" (data labels).
- **"co0gnition" typo fixed** at §1.2.
- **Casto reference removed** (placeholder citation, not referenced in body).
- **Producer × judge-family Table 1a refreshed with raw direct measurements** from per-cell judging files (was constraint-derived per Worker G's Wave 3a analysis, which assumed symmetric off-diagonals). The full 3×3 cold table is now directly measured (n = 90 paired observations per cell).
- **H2 candidate-confounder narrative narrowed** under exact paired-t testing: none of the three same-family bias tests reach significance at α = 0.05 (Claude p = 0.80; GPT p = 0.28; Gemini p = 0.68). The judge-side bias account that v0.3.0 carried is therefore not empirically supported; producer-side response style (Constitutional AI / RLHF hedging; Bai et al. 2022) is the sole supported candidate confounder for the H2 interaction. §5.2 and §6.2 updated accordingly; §8.1 limitations adjusted.
- **§7.1 closing slogan added** as a standalone terminal line: *"Notation design IS brain design for LLMs."* (preserves the user's preferred framing on the body surface where the substrate-design argument supports it; the abstract retains the bounded version).

## v0.3.0 — 2026-05-12

- **Structural alignment with EA precedent.** Collapsed §1, §2, §6, §7, §8 from numbered subsections to flat EA-style sections with bolded leading phrases. Retained numbered subsections only in §3, §4, §5 per empirical-paper convention. Eliminated all depth-3 headings (former §2.1.1, §2.5.1, §5.2.1 promoted or merged).
- **Added §9 Conclusion** (~255 words, EA-style closing).
- **Added Acknowledgments and Ethics Statement** sections after §9, before References, matching EA precedent. Acknowledgments asserts intellectual ownership and names TSH/Coinage Probe/Lexical Reachability/Vocabulary Boundary/Off-Token Route as original contributions. Ethics Statement addresses the dual-use of substrate-level vocabulary handles (design and attack-surface).
- **Cut §7.3 SAI architecture** and **§8.6 Future paper teasers** — out-of-scope and territory-marking respectively per outside-reviewer feedback.
- **Voice fixes:** added rhetorical-question openers (§2 opener, §6.1, §7.1, §7.4); promoted buried summary lines to terminal beats (Wittgenstein 5.6, Symbol grounding, Off-Token Route, H3 substrate-ended, Notation-not-packaging); rewrote hedge-as-posture openers throughout.
- **Fixed-date treatment:** moved "On 2026-05-07" from §1.1 opener to a demo-provenance italic footnote at end of §1.1 block.
- **Coinage discipline:** tightened "Coinage Probe" → "the probe" after first definitional use per section; dropped OTR acronym (use "Off-Token Route" in full).
- **Frontmatter expansion:** added `domain: TSH`, `series-id: P1`, `type: position-and-empirical`, `priority`, `venue`, `github-repo`, `related` wikilinks, `tags` matching EA precedent.
- **References normalized** to EA bullet+URL-DOI format (italicized journal/book titles, `https://doi.org/` prefixes, alphabetical).
- **Figures embedded** in §5 with captions (Figure 1 in §5.1, Figure 2 in §5.2, Figure 3 in §6 Stratified analysis block). Figure files renamed `figure{N}-` → `fig{N}-` per publishing-guide §3.
- **Taxonomy:** TSH gets its own domain (separate from YON, separate from EA, paired with both via cross-citation). Folder move from `Papers/YON/token-substrate-hypothesis/` to `Papers/TSH/position-paper/` deferred to Worker U in Wave 5c.
- **Slug:** `tsh-position-paper` (GitHub repo: `allemaar/tsh-position-paper`).

## v0.0.1 — 2026-05-08 — Priming

- Paper folder scaffolded.
- Coined terminology locked: Token-Substrate Hypothesis (TSH), Off-Token Route, Coinage Probe, Lexical Reachability, Vocabulary Boundary.
- Working title set: "The Token-Substrate Hypothesis: Coinage Probes Across Frontier Models".
- Replaces YON-03 sketch entry "Sapir-Whorf for Silicon Minds" in the papers index.
- Sourced from allemaar.com episode 2026-E0037 ("I Caught an LLM at the Edge of Its World").
