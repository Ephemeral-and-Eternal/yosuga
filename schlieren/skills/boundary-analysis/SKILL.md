---
name: boundary-analysis
description: Evaluate what a current purpose or judgment supports, its unresolved dependencies, and its scope and reasoning limits. Use when analysis needs a scope decision or Core state evaluation, including whether an unsettled matter can be excluded from this judgment or requires human review.
---

# Boundary Analysis

Perform Schlieren's Bound responsibility. Read [AGENTS.md](../../../AGENTS.md), especially its Layer Contract, for the canonical Core state vocabulary and constraints; read [SCHEMA.md](../../SCHEMA.md) for handoff and scope semantics.

## Method

1. Identify the current purpose, proposed judgment, and legitimate scope or authority. Keep gaps in these inputs explicit; do not treat inferred authority or intention as established. Use available observations, hypotheses, falsification results, and human judgments without requiring all preceding Skills to run.
2. Apply the Schema's materiality / dependency gate to unresolved items before requiring a full Core state evaluation:
   - Keep material items and items the judgment depends on in current scope for evaluation. Include dependencies carried through hypotheses or other premises.
   - De-scope an item only with a supported basis that it does not materially constrain this judgment. Retain `item` and `basis` and keep the content unresolved.
   - If materiality or dependency cannot be determined, keep that uncertainty in current scope. Do not treat lack of evidence of dependency as independence.
3. Evaluate the in-scope matters against the available basis and the Core's Layer Contract. State what is supported, under which conditions, and where inference or judgment remains limited. Evaluate and output applicable `core_state` values with the matter and basis they describe; do not merge distinct matters into a global verdict or promote Observe/Infer outputs automatically.
4. Recognize changes in state or understanding only on grounds allowed by the Layer Contract, retaining the basis. Bound evaluates those grounds; it does not cause Resolution or gain authority to settle unresolved matters merely by being invoked. A scope change leaves the excluded content unresolved.
5. Return `human_review_required` for an affected judgment when the Layer Contract requires it, including when the Skill conflicts with the Core or provides no valid handling for an encountered state. Identify the reasoning boundary and what judgment is needed. Continue work independent of that matter; unresolved content alone does not require stopping all work.
6. Hand off the supported scope, conditions, and unresolved dependencies together. Narrow a judgment only when the resulting judgment no longer relies on excluded items, making the changed scope and basis explicit. Downstream judgments must not proceed as though their unresolved dependencies were resolved.

## Output

- `supported_scope`: What the current judgment can support, with its basis, conditions, and limits.
- `out_of_scope`: Matters outside this judgment. For each De-scoped unresolved matter retain at least `item` and `basis`, making its unresolved status explicit.
- `unresolved`: Matters still unsettled, distinguishing those retained in current scope from those De-scoped. Reference the corresponding `out_of_scope` entry rather than duplicating it when sufficient.
- `core_state`: Applicable Core states, each tied to the matter evaluated and its basis. Do not require a full state classification of De-scoped items or use `unresolved` or `provisional` as state values.
- `human_review_required`: When required, the affected judgment and reason for human review, corresponding to the Core state of the same name. This indicates a reasoning boundary, not failure or a separate approval system.

Use concise prose or lists, not a fixed runtime format. Make unassessed matters explicit where their omission could imply clearance. Bound's output is limited to the scope actually evaluated; it does not make all incoming analysis final.

## Boundary

Do not invent evidence, change substantive constraints by De-scoping, or decide beyond the available basis and legitimate authority. Non-material unresolved items can remain outside this judgment without permanent tracking. A later judgment that depends on such an item must reassess it; its earlier exclusion is not evidence of resolution.
