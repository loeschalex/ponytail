# Deep Modules

**Proponent:** John Ousterhout, *A Philosophy of Software Design* (2nd ed., Yaknyam Press, 2021; 1st ed. 2018 — Chapter 4: "Modules Should Be Deep")

## Core Concepts

**Module depth** — the ratio of benefit (functionality provided) to cost
(interface complexity). A deep module delivers powerful functionality
behind a small, stable interface; a shallow module exposes nearly as much
complexity as it contains.

**Shallow module** — a module whose public interface is almost as complex
as its implementation. Shallow modules shift the complexity burden onto
callers rather than hiding it — adding interface cost without proportional
abstraction benefit.

**Interface as cost** — every element of a public API (parameters, types,
configuration options, side effects) is cognitive cost that every caller
must pay. Deep modules minimise this cost while maximising what they
deliver.

**Information hiding** — modules should encapsulate design decisions likely
to change: data structures, algorithms, file formats, protocols. Those
decisions remain invisible to callers, so the interface stays stable even
as the implementation evolves.

**Classitis** — Ousterhout's term for the anti-pattern of decomposing a
system into many tiny, shallow classes. Each class adds its own interface
to the collective cognitive load without reducing overall implementation
complexity.

**Different layer, different abstraction** — each architectural layer
should offer abstractions meaningfully different from the layer below. A
layer that only renames lower-level calls without adding substance is a
shallow passthrough and a sign of poor design.

## When to Use

- Designing a module's public API — evaluate whether the interface is
  simpler than the implementation it hides
- Reviewing a proposed class decomposition for whether it reduces
  complexity or merely redistributes it
- Identifying pass-through methods and wrapper chains that add interface
  cost without hiding detail
- Instructing an LLM to design APIs or class boundaries with minimal
  caller-visible surface area
- Choosing between a general-purpose and a special-purpose API — prefer
  the deeper, more general option

## Criticism

- Andrey Lebedev, ["Not My Philosophy of Software Design"](https://andremoniy.medium.com/not-my-philosophy-of-software-design-13d9f1e09451)
  (Medium) — argues that forcing depth into a single class violates the
  Single Responsibility Principle; the Java I/O example conflates file
  reading with buffering, two genuinely separate concerns; deep
  general-purpose classes also resist composition and create coupling that
  contradicts domain-driven design practice.
- ["Modules Should Be Deep!"](https://softengbook.org/articles/deep-modules)
  (Software Engineering: A Modern Approach) — adds nuance: `String.isEmpty()`
  provides semantic clarity and safe encapsulation despite its trivial
  implementation, challenging a purely quantitative interpretation of
  depth; Bertrand Meyer's iceberg metaphor — small visible tip over large
  submerged base — is cited as a complementary framing.

> **Note (not from source, written for this library):** the Lebedev
> critique is the practical caution to apply here — don't force unrelated
> responsibilities into one class chasing "depth." If a deep module needs
> internal decomposition to stay testable, decompose it; depth is about
> interface cost, not about minimizing class count.

## Source

https://llm-coding.github.io/Semantic-Anchors/anchor/deep-modules
