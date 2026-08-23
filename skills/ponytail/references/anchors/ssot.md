# SSOT (Single Source of Truth)

**Also known as:** SSOT Principle
**Related:** DRY (the knowledge-layer cousin), SPOT (Single Point of Truth — the implementation-pattern sibling; SSOT is the architecture/organizational-level version)

## Core Concept

One canonical, trusted location owns each piece of data or policy. Every
consumer reads from — or derives from — that one source rather than keeping
its own copy. The source is definitive when conflicts arise; other
representations are derived from it, not independently maintained.

## When to Use

- Designing data or config architecture: one owner for a fact, others derive
- Consolidating fallback order, normalization, or derivation logic that was
  scattered across multiple call sites into one place
- Resolving disagreement between multiple sources holding the "same" data
- Establishing documentation or schema ownership so a change propagates
  instead of being copied

## When NOT to Use

- Not license to merge unrelated concerns into one object because "it's all
  config now." SSOT means one owner *per concern* — a single object that
  also owns unrelated state is a different mistake (see Deep Modules'
  "classitis"/SRP caveat), not a correct application of this principle.
- Don't use SSOT to argue against a caller-visible interface (see Locality
  of Behaviour) — the source can be centralized while still exposing a
  transparent, boring lookup at the boundary.

## Source

https://llm-coding.github.io/Semantic-Anchors/anchor/ssot-principle
