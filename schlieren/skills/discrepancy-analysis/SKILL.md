---
name: discrepancy-analysis
description: Organize meaningful differences among observations, records, rules, expectations, and outcomes. Use when a mismatch needs to be made explicit before explaining it or evaluating its significance for a current judgment.
---

# Discrepancy Analysis

Perform Schlieren's Observe responsibility. Read [AGENTS.md](../../../AGENTS.md) for the Core and [SCHEMA.md](../../SCHEMA.md) for responsibility and handoff contracts.

## Method

1. Identify the current purpose and the observations, records, rules, expectations, or outcomes being compared. If the purpose is unspecified, keep the comparison exploratory and make that limitation explicit.
2. Separate what each source records from what is expected or inferred. Retain source, observer, viewpoint, and conditions where they affect interpretation. A report of an intention records what was said and does not by itself establish the intention.
3. Describe meaningful discrepancies between the compared accounts or conditions. Note why a difference may matter to the purpose without deciding its materiality for a final judgment. Do not amplify cosmetic or plainly irrelevant differences, or manufacture a discrepancy when none is supported.
4. Identify missing observations or context needed to interpret the comparison. Distinguish information not recorded from evidence that something did not occur.

## Output and handoff

- `observation`: What the available sources show, with relevant observation conditions and limits.
- `discrepancy`: The specific difference, what is being compared, and its possible relevance.
- `missing`: Information not available that limits the comparison.

Use concise prose or lists; do not fill fields with invented content. Mark the analysis `provisional`. Pass it to Infer when explanations are needed, or Bound when current scope or judgment support needs evaluation. Neither handoff is mandatory for exploratory output.

## Boundary

Do not establish causes, infer intentions as observations, or automatically classify a discrepancy as failure, violation, or anomaly. Do not establish `core_state`. Formal De-scoping and evaluation of the current judgment belong to Bound; selecting meaningful comparisons does not clear unresolved dependencies.
