# Schlieren v0.1

Schlieren is a Reasoning Schema under yosuga. [AGENTS.md](../AGENTS.md) is the canonical Core; this document defines responsibility boundaries and handoffs, not additional Core principles.

```text
AGENTS.md → Schlieren → Skills / Agent compositions
```

## Responsibilities

| Responsibility | Canonical Skill | Owns | Does not establish |
| --- | --- | --- | --- |
| Observe | [discrepancy-analysis](skills/discrepancy-analysis/SKILL.md) | Organizing meaningful observable differences | Causes or `core_state` |
| Infer | [hypothesis-falsification](skills/hypothesis-falsification/SKILL.md) | Candidate explanations, conditions, and falsification | `core_state` |
| Bound | [boundary-analysis](skills/boundary-analysis/SKILL.md) | Current judgment scope, dependencies, and evaluation/output of `core_state` | Unsupported certainty or authority to settle others' judgments |

The usual flow is Observe → Infer → Bound. Use only the responsibilities needed for the current purpose; a skipped responsibility does not count as performed. Bound can use available observations, falsification results, and human judgments without requiring a fresh Observe or Infer pass.

## Handoff semantics

Pass the current purpose or judgment, the relevant analysis, and the basis and limitations needed to interpret it. Keep observations distinguishable from hypotheses. If the purpose or a required input is missing, expose that gap rather than inventing it.

Output names in the Skills are a minimal vocabulary for readable analysis, not a required serialization format. Use only relevant detail; omitted or unassessed content must not be read as settled or absent.

- Observe hands off `observation`, `discrepancy`, and `missing`.
- Infer hands off `hypotheses`, `hidden_context_candidates`, `falsification_conditions`, `discarded_hypotheses`, and `unresolved`.
- Bound hands off `supported_scope`, `out_of_scope`, `unresolved`, `core_state`, and `human_review_required`, with the affected matter and basis where applicable.

Analysis that has not passed through Bound carries the qualifier `provisional`. It can support exploration, comparison, further observation, and inference; it is neither invalid nor a final judgment. A Bound evaluation covers only its stated scope and basis; passing through Bound does not finalize every input or resolve every item. New or revised analysis outside that evaluation remains provisional.

## State and unresolved content

`core_state` uses only the state vocabulary in AGENTS.md, particularly sections 2 and 8 and the Layer Contract. Bound evaluates and outputs applicable states against available evidence and that contract, identifying what each state describes and why. It does not invent states, automatically promote Observe/Infer output, or force distinct matters into one global state.

`human_review_required` is a Core state indicating a reasoning boundary, not failure. The output of the same name identifies the affected judgment and the reason human review is required under the Layer Contract; it is not a separate state system or an automatic approval requirement for unrelated work.

`unresolved` is a container for matters not currently settled. It is not a Core state and does not require every contained item to receive a Core state evaluation before scope is considered. `provisional` is a qualifier, not a Core state.

| Operation | What changes | Required basis |
| --- | --- | --- |
| Resolution | The state or understanding of the unresolved content itself | New observation, falsification, or human judgment under the Core's Layer Contract; retain the basis for the transition |
| De-scoping | Relevance to the current judgment; the content remains unresolved | Why the item does not materially constrain the current judgment |

Resolution and De-scoping are distinct. Bound assesses available grounds for a change; its evaluation does not itself cause Resolution. De-scoping neither marks content resolved/certain nor authorizes changing a substantive boundary or constraint.

## Materiality / dependency gate

Before requiring a full Core state evaluation of an unresolved item, Bound asks: **Does this item materially constrain the current judgment?** Consider whether the judgment's support, conditions, legitimate scope, or authority depends on it.

- **Material or depended upon:** Keep it in current scope and perform Bound evaluation under the Layer Contract. Limit dependent conclusions to what the unresolved basis supports.
- **Non-material with a supported basis:** De-scope it while preserving it as unresolved. Retain at least `item` and `basis`; the basis explains why it does not materially constrain this judgment. Reflect the exclusion in `out_of_scope` without implying Resolution.
- **Materiality or dependency cannot be determined:** Keep the item and this uncertainty in current scope for Bound evaluation. Lack of a demonstrated dependency is not evidence of independence.

Do not remove an item from scope while continuing to rely on it, including through a hypothesis or another premise. Narrowing the judgment is valid only if the resulting judgment no longer depends on that item; make the changed scope and basis explicit.

Downstream judgments inherit these limitations for the content they use. They must not treat a dependent unresolved item as resolved, an omission as clearance, or a previous De-scoping basis as automatically applicable to a different judgment. Reassess relevance when the purpose or dependencies change. This does not require resolving all items, stopping independent work, or maintaining a permanent backlog; no runtime persistence format is specified.

## Agent compositions

These are compositions, not additional Skills or physical Agent definitions.

| Composition | Responsibilities | Purpose and output boundary |
| --- | --- | --- |
| Discovery | Observe + Infer | Explore possible contexts behind differences; output is normally `provisional` |
| Triage | Observe + Bound | Evaluate materiality, dependency, and current scope; deep causal exploration is not its purpose |
| Review | Infer + Bound | Evaluate how far hypotheses or explanations are currently supported |
| Reasoner | Observe + Infer + Bound | Use all three responsibilities when needed; has no higher authority than other compositions |

Prefer the smallest composition sufficient for the current purpose.

## Extension policy

Maintain the three canonical Skills by default. Address new requirements in this order:

1. Use an existing Skill within its current responsibility.
2. Extend or revise an existing Skill.
3. Compose existing Skills as an Agent.
4. Consider a new Skill only when the requirement does not naturally fit Observe, Infer, or Bound.

Skill count is not a measure of architectural growth. v0.1 contains only the three canonical Skills above.
