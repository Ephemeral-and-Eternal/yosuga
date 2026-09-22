---
name: hypothesis-falsification
description: Form alternative hypotheses from discrepancies or other available evidence, examine their conditions, and identify what would falsify them. Use to explore possible hidden context or test an explanation before evaluating how far a current judgment is supported.
---

# Hypothesis Falsification

Perform Schlieren's Infer responsibility. Read [AGENTS.md](../../../AGENTS.md) for the Core and [SCHEMA.md](../../SCHEMA.md) for responsibility and handoff contracts.

## Method

1. Identify the discrepancy or explanation under examination and the available observations. Preserve their sources and limits separately from inferred claims; a prior Observe pass is not required.
2. Form plausible alternative hypotheses. Consider hidden assumptions, context, conditions, dependencies, and differences in boundaries or viewpoints. Do not converge prematurely on one explanation or invent alternatives solely to reach a fixed count.
3. For each hypothesis, identify what it explains, the conditions it needs, and what remains unsupported. Keep hidden context as a candidate, not an observed fact.
4. State observations or conditions that would reject or require revising each hypothesis, including your own reasoning. Distinguish proposed checks from checks actually performed and their results. If no usable falsification condition can be identified, state that limitation.
5. Discard hypotheses incompatible with available evidence or demonstrated constraints, keeping the reason and basis. Lack of an observation alone does not show that a necessary condition is absent. Preserve remaining uncertainty without requiring exhaustive explanation or testing.

## Output and handoff

- `hypotheses`: Candidate explanations, their observational basis, and conditions of support.
- `hidden_context_candidates`: Possible assumptions, contexts, conditions, dependencies, or boundary differences behind the discrepancy; these may be recorded with the related hypotheses.
- `falsification_conditions`: What would reject or revise each hypothesis, and any available results, clearly distinguished from proposed checks.
- `discarded_hypotheses`: Excluded explanations with the reason and basis for exclusion.
- `unresolved`: Questions or competing explanations that remain unsettled.

Keep output proportional to the inquiry, without a fixed record format. Mark the analysis `provisional`. It can guide further observation or inference; hand it to Bound when the current judgment's support or scope needs evaluation.

## Boundary

Do not promote a hypothesis into an observation or establish `core_state`. `unresolved` is a container, not a Core state. An actual falsification result can supply grounds for a change in understanding; a proposed test, unsupported dismissal, or surviving hypothesis does not establish certainty. Core state evaluation and De-scoping belong to Bound.
