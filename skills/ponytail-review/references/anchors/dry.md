# DRY (Don't Repeat Yourself)

**Also known as:** DRY Principle. Antonym: WET ("Write Everything Twice" / "We Enjoy Typing").
**Proponents:** Andy Hunt & Dave Thomas, *The Pragmatic Programmer* (1999)

## Core Concept

"Every piece of knowledge must have a single, unambiguous, authoritative
representation within a system." DRY targets duplicated **knowledge/intent**,
not coincidental textual similarity — two fragments that look alike but
change for different reasons are not a DRY violation, and collapsing them
couples unrelated concerns. Extract a shared abstraction after the
**third** occurrence, not the first (Fowler's Rule of Three) — premature
de-duplication guesses at an abstraction before the pattern is clear.

## When to Use

- Consolidating a business rule, constant, or schema that appears in
  several places into one authoritative definition
- Designing a single source of truth (config, types, API contract) that
  other artifacts derive from — see SSOT
- Reviewing code where one conceptual change currently requires edits in
  many unrelated spots

## When NOT to Use

- Before the third occurrence — resist abstracting on the first or second
- When two similar-looking fragments change for different reasons — merging
  them via a shared abstraction is worse than the duplication ("the wrong
  abstraction," Sandi Metz, 2016)
- As dogma over readability — a little duplication can beat a leaky,
  over-general abstraction
- The authors themselves say the principle is widely misread: in the 20th
  Anniversary Edition (2019) they wrote code deduplication is "a tiny and
  fairly trivial part" of DRY — it targets duplicated knowledge, not
  duplicated syntax

## Source

https://llm-coding.github.io/Semantic-Anchors/anchor/dry
