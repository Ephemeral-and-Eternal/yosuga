# yosuga

**yosuga** is a model-neutral reasoning architecture for working with incomplete, conflicting, or ambiguous information.

It provides a shared reasoning core for AI systems without binding that core to a specific model, domain, or runtime.

yosuga is designed to help AI:

- distinguish observation from inference,
- preserve uncertainty without manufacturing certainty,
- use discrepancies as signals for further reasoning,
- form and falsify hypotheses,
- limit conclusions to what the available basis supports,
- and continue useful work without requiring every unresolved matter to be resolved.

## Architecture

```text
yosuga
│
├── AGENTS.md
│   └── Canonical reasoning Core
│
└── Schlieren
    ├── SCHEMA.md
    │   └── Reasoning Schema
    │
    └── skills/
        ├── discrepancy-analysis/
        ├── hypothesis-falsification/
        └── boundary-analysis/
```

### Core

[`AGENTS.md`](AGENTS.md) defines the model-neutral reasoning constraints shared across yosuga.

It is the canonical source for how observation, uncertainty, hypothesis, judgment scope, conflict, and unresolved matters are handled.

### Schlieren

[`schlieren/SCHEMA.md`](schlieren/SCHEMA.md) defines the reasoning schema used to operationalize the Core.

Its three responsibilities are:

```text
Observe → Infer → Bound
```

| Responsibility | Canonical Skill | Purpose |
| --- | --- | --- |
| Observe | `discrepancy-analysis` | Organize meaningful observable differences |
| Infer | `hypothesis-falsification` | Form and falsify candidate explanations |
| Bound | `boundary-analysis` | Evaluate the supported scope and reasoning boundary of the current judgment |

These responsibilities can be composed as needed; the full sequence is not required for every task.

## Model integration

Canonical Skills live only under:

```text
schlieren/skills/
```

Runtime-specific discovery paths reference those same canonical directories.

```text
.agents/skills/   → Codex
.claude/skills/   → Claude Code
```

No model-specific copies of the canonical Skills are maintained.

Both runtimes use the repository-root `AGENTS.md` as the shared reasoning Core.

## Design principle

yosuga does not aim to resolve every uncertainty or force every discrepancy into a single conclusion.

Its operating principle is:

> **Observe the discrepancy.  
> Infer what may be hidden.  
> Falsify the hypothesis.  
> Bound the conclusion.  
> Preserve what remains unknown.**

In practical terms:

> **Work only within the scope currently required, avoid deciding more than the available basis supports, and allow unresolved space to remain unresolved when it does not constrain the current judgment.**

## Status

**v0.1**

Current canonical assets:

- yosuga Core
- Schlieren Reasoning Schema
- 3 canonical Skills
- Codex runtime integration
- Claude Code runtime integration

The architecture is intentionally small. New capabilities should preferentially extend or compose the existing responsibilities rather than introduce new Skills without a demonstrated need.
