# Disagreement Diagnosis

Use this reference when credible sources appear to disagree materially.

Do not jump from “two results differ” to “the field is controversial.” First diagnose what kind of disagreement exists.

## 1. Construct mismatch

The sources use the same label for different things.

Examples:

- productivity = task time vs releases;
- learning = immediate recall vs delayed transfer;
- safety = incident rate vs compliance score.

Action: separate the constructs. Do not average or narratively reconcile unlike metrics.

## 2. Population mismatch

The sources study different people, organizations, systems, or environments.

Examples:

- novices vs experts;
- small teams vs large enterprises;
- laboratory subjects vs field users;
- one robot platform vs another sensor stack.

Action: report heterogeneity and external-validity limits before claiming contradiction.

## 3. Context / intervention mismatch

The treatment or conditions differ.

Examples:

- different model generations;
- different prompts or tool permissions;
- different task difficulty;
- supervised vs unsupervised usage;
- glass at different incidence angles or different LiDAR wavelengths.

Action: identify the condition that may moderate the result.

## 4. Temporal mismatch

The evidence comes from materially different periods.

This is especially important for:

- AI models and developer tools;
- APIs and software behavior;
- law and policy;
- market structure;
- fast-changing products.

Action: do not treat stale and current evidence as symmetric. Explain what changed between periods.

## 5. Methodological disagreement

The sources attempt to answer the same question but use designs with different biases or identifying assumptions.

Examples:

- observational vs randomized evidence;
- self-report vs behavioral measurement;
- benchmark vs production telemetry;
- simulation vs field test.

Action: compare which design better supports the specific claim. Do not count studies like votes.

## 6. Sampling / selection disagreement

Different selection processes create different observed worlds.

Examples:

- only successful adopters respond to a survey;
- published studies omit failed experiments;
- support tickets capture failures but not normal operation;
- GitHub studies capture open-source maintainers, not typical enterprise developers.

Action: identify the selection mechanism and ask what population the result can represent.

## 7. Genuine theoretical conflict

After accounting for construct, population, context, time, method, and selection, credible evidence still supports incompatible explanations or predictions.

Only then describe the issue as a genuine unresolved scientific/technical dispute.

## 8. Recommended synthesis pattern

Instead of:

> “Studies are mixed.”

Prefer:

> “The results differ mainly because A measures short bounded task completion among X, while B measures long-horizon production work among Y. Within each setting the evidence is more internally consistent than the headline conflict suggests. The unresolved question is whether the effect transfers across those settings.”

This turns apparent contradiction into a more precise research boundary.

## 9. Consensus labels

Use cautious distinctions:

- **Formal consensus** — explicit consensus statement, guideline, standards process, or equivalent authoritative synthesis.
- **Broad convergence** — multiple reasonably independent evidence streams point in the same direction, without a formal consensus process.
- **Research tendency** — literature leans one way but important heterogeneity or limitations remain.
- **Open question** — evidence cannot currently distinguish key alternatives.

Do not infer “consensus” merely because the first page of search results repeats the same claim.