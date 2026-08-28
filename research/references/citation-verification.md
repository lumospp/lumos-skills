# Claim–Citation Verification

Use this reference when a research answer contains claims that materially affect the conclusion, especially quantitative, causal, consensus, safety, policy, or fast-changing claims.

The failure mode to prevent is:

> **The citation is real, but the cited source does not support the sentence at the strength written.**

## 1. Verify the claim, not the presence of a link

For each decisive claim, check:

1. What exactly is the claim?
2. What exact source supports it?
3. What did the source actually measure, observe, or state?
4. Is the claim stronger, broader, more causal, more current, or more universal than the source?
5. Does the source support the whole sentence or only one clause?

A useful internal classification is:

- **ENTAILED** — source evidence supports the claim at roughly the same strength and scope.
- **PARTIAL** — source supports only part of the claim or a weaker/narrower version.
- **NOT ENTAILED** — source exists but does not support the claim.
- **UNVERIFIABLE** — source content or provenance cannot currently be checked.

When status is PARTIAL, weaken or split the claim. When NOT ENTAILED, remove it or find better evidence. Never keep a strong sentence merely because a citation looks authoritative.

## 2. Check the common upgrades AI makes by accident

### Population upgrade

Source:
> 95 developers in one controlled task.

Bad claim:
> All software developers improve by 40%.

### Construct upgrade

Source measures:
> task completion time.

Bad claim:
> organizational software productivity improved by the same percentage.

### Causal upgrade

Source:
> X is associated with Y.

Bad claim:
> X causes Y.

### Magnitude upgrade

Source:
> small average effect with wide uncertainty.

Bad claim:
> large, reliable benefit.

### Scope upgrade

Source:
> effect under condition A.

Bad claim:
> effect in all contexts.

### Temporal upgrade

Source:
> API behavior in 2024.

Bad claim:
> API behaves this way now.

### Consensus upgrade

Source:
> one review or several agreeing papers.

Bad claim:
> scientific consensus is settled.

## 3. Verify quantitative claims more strictly

For numbers doing important rhetorical work, check:

- numerator / denominator;
- units;
- baseline;
- absolute vs relative change;
- mean vs median;
- subgroup vs whole sample;
- confidence interval / uncertainty when relevant;
- whether the result is adjusted or unadjusted;
- version/date/context.

Do not preserve a memorable percentage after removing the conditions that made it true.

## 4. Verify summaries of disagreement

A citation to one side of a debate cannot support a claim about the whole field.

Before writing:

> “The field is divided”

or:

> “There is broad consensus”

check whether the evidence actually represents the literature, a formal consensus process, a review, or merely selected sources.

When important sources disagree, read `disagreement-guide.md` before describing the disagreement.

## 5. Verification intensity should match risk

Do not verify every harmless sentence with equal effort.

Prioritize:

1. claims that determine the bottom line;
2. quantitative claims;
3. causal/mechanistic claims;
4. claims of consensus, prevalence, safety, legality, or current product behavior;
5. surprising or unusually strong claims;
6. claims that drive a recommendation.

For low-risk background statements, ordinary source matching is enough.

## 6. Final claim downgrade rule

Unsupported claims must degrade or disappear:

```text
Strong direct support
→ state at justified strength

Partial / indirect support
→ weaken, narrow, or label inference

Conflicting evidence
→ describe disagreement and boundaries

No verifiable support
→ remove or mark unknown
```

The goal is not citation density. The goal is that a skeptical reader could open the source and understand why the claim was written that way.