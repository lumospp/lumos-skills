# Evidence Guide

Use this reference when the quality of a research answer depends on choosing evidence appropriate to the claim. The central rule is **evidence–question fit**, not a universal hierarchy of sources.

## 1. Match evidence to the claim

| Claim type / domain | Strong evidence often includes | Common traps |
|---|---|---|
| Definition / established concept | Standards, authoritative textbooks, canonical papers, professional bodies | Treating a popular blog definition as canonical |
| Current event / current fact | Official records, direct statements, primary documents, multiple independent reputable reports | Treating search snippets or reposts as independent confirmation |
| Causal intervention | Well-designed experiments, quasi-experiments, natural experiments, systematic reviews/meta-analyses where appropriate | Correlation, uncontrolled before/after comparisons, tiny convenience samples |
| Mechanism | Experiments that distinguish mechanisms, direct measurements, convergent evidence, domain theory | A plausible story presented as a demonstrated mechanism |
| Comparative effectiveness | Head-to-head evidence, comparable benchmarks, field studies, effect sizes and costs | Comparing results from different populations, metrics, or conditions |
| Engineering / robotics | Specifications, source code, logs, reproducible tests, benchmarks, failure reports, sensor/system models | Treating marketing material or a single lab demo as field reliability |
| Software / API / library | Official docs, release notes, source code, tests, issue trackers when relevant | Relying on stale tutorials or assuming old behavior is current |
| Company / market | Regulatory filings, audited reports, official data, reputable third-party datasets, investigative reporting | Vendor surveys, cherry-picked customer stories, revenue claims without definitions |
| Policy / law / regulation | Current statutes, regulations, regulator guidance, court decisions, official notices | Using old summaries after rules changed; confusing proposals with enacted rules |
| History | Primary documents, archival evidence, high-quality historical scholarship | Presentism, single memoirs, unsourced popular retellings |
| Public opinion / lived experience | Representative surveys for prevalence; qualitative interviews/community sources for experience | Using anecdotes to estimate population prevalence |

A systematic review is not automatically superior to a primary source for every question. A source is strong only insofar as its design and provenance support the specific claim being made.

## 2. Evaluate research evidence

When a paper or study is carrying a major conclusion, inspect what matters for that design:

- sample and population
- measurement validity
- comparison/control condition
- randomization or identification strategy where causal inference is claimed
- effect size, not only statistical significance
- uncertainty intervals where available
- attrition, missing data, researcher degrees of freedom, or multiple comparisons when material
- preregistration and replication where relevant
- external validity: whether the result transfers to the user's population, setting, task, or time horizon

Do not mechanically demand every item for every study. Focus on the failure modes capable of changing the conclusion.

## 3. Source lineage and independence

Multiple citations can still represent one piece of evidence.

Trace important claims toward their origin:

```text
Article A ─┐
Article B ─┼──> same company report ──> one evidence source
Article C ─┘
```

Count independent evidence streams, not links. Prefer the original source when accessible, while using secondary sources for context or critique.

## 4. Base rates and selection

For claims about success, failure, risk, behavior, or prediction, ask:

- What is the baseline rate before the proposed explanation or intervention?
- Who is missing from the observed sample?
- Why did these cases become visible?
- Are we studying only survivors, adopters, published successes, or companies willing to report results?

A compelling set of successful examples cannot establish how often a strategy succeeds.

## 5. Causal discipline

When evidence is observational, explicitly consider:

- reverse causality
- confounding variables
- selection into treatment/exposure
- measurement artifacts
- regression to the mean
- temporal trends

Prefer the weakest causal statement justified by the design. “Associated with” is not a stylistic downgrade; it may be the correct model.

## 6. Confidence calibration

Confidence is about the support for a claim, not how persuasive the prose sounds.

### High

Use when strong, reasonably independent evidence converges; relevant replications or triangulation exist; important alternatives are weak; and the claim does not overgeneralize beyond the evidence.

### Medium

Use when the direction is reasonably supported but important limitations remain: indirect evidence, limited samples, moderate disagreement, uncertain generalization, or a rapidly changing environment.

### Low

Use when evidence is sparse, weak, non-independent, strongly conflicted, or mainly inferential.

### Unknown

Use when available evidence cannot distinguish the important alternatives. “Unknown” is a valid research result.

Do not convert these labels into arbitrary percentages unless a defensible probabilistic model exists.

## 7. Claim–evidence ledger

For difficult work, maintain a compact internal ledger:

| Claim | Why it matters | Best support | Best challenge | Source independence | Confidence | What would change the judgment? |
|---|---|---|---|---|---|---|
| ... | ... | ... | ... | ... | ... | ... |

The ledger is a reasoning aid, not a mandatory output format. Expose it when the user needs auditability or when disagreements hinge on specific claims.

## 8. Failure modes to actively check

- confirmation-biased search queries
- search ranking treated as truth
- citation laundering through multiple secondary sources
- old evidence used for a fast-changing claim
- vendor-sponsored evidence treated as independent
- publication bias or survivorship bias
- statistical significance confused with practical importance
- subgroup or laboratory findings generalized to everyone
- a coherent mechanism invented after observing correlation
- a benchmark optimized to the metric rather than the real goal
- absence of evidence described as evidence of absence
- unsupported claims retained because they make the story cleaner

The purpose of this checklist is not to create skepticism theater. Spend attention on failure modes that could materially change the answer.