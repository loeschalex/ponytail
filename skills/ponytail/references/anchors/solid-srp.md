# SOLID — Single Responsibility Principle

**Also known as:** SRP
**Proponent:** Robert C. Martin, part of SOLID Principles (umbrella)

## Core Concept

A class should have only one reason to change. Each module or class is
responsible for a single part of the software's functionality.

## When to Use

- A class has multiple unrelated responsibilities
- Changes to one feature require modifying unrelated code
- Unit testing requires complex setup because unrelated concerns are
  tangled together
- Cited as the counterweight when a "Deep Modules" argument would otherwise
  justify folding unrelated responsibilities into one class chasing
  interface depth

## When NOT to Use

- Not a mandate to split by every plausible axis of change — "one reason to
  change" is about cohesion, not about minimizing lines per class. Splitting
  a genuinely cohesive deep module into shallow pieces to satisfy a narrow
  reading of SRP re-creates the "classitis" anti-pattern Deep Modules warns
  against — the two principles bound each other, neither wins outright.

## Source

https://llm-coding.github.io/Semantic-Anchors/anchor/solid-srp
