# Deep Modules

**Also known as:** Module Depth, Deep Classes
**Proponent:** John Ousterhout, *A Philosophy of Software Design* (2nd ed. 2021, ch. 4: "Modules Should Be Deep")

## Core Concept

A module's value is the ratio of benefit (functionality provided) to cost
(interface complexity it exposes). A deep module delivers powerful
functionality behind a small, stable interface. A shallow module exposes
nearly as much complexity as it contains — it shifts the complexity burden
onto callers instead of hiding it. Every element of a public interface
(parameters, types, config options, side effects) is cognitive cost every
caller pays; a deep module minimises that cost while maximising what it
delivers.

## When to Use

- Designing a module's public API — is the interface simpler than the
  implementation it hides?
- Reviewing a class decomposition for whether it reduces complexity or
  merely redistributes it across more files
- Flagging pass-through methods and wrapper chains that add interface cost
  without hiding detail
- Choosing between a general-purpose and a special-purpose API — prefer the
  deeper, more general option

## When NOT to Use

- Don't force unrelated responsibilities into one class chasing "depth" —
  Ousterhout's critics (Andrey Lebedev, "Not My Philosophy of Software
  Design") argue this can violate Single Responsibility and create coupling
  that resists composition. If a deep module needs internal decomposition to
  stay testable, decompose it — depth is about interface cost, not about
  minimizing class count.
- Depth is not purely line-count or class-count. `String.isEmpty()` is a
  trivial implementation with real depth: it provides semantic clarity and
  safe encapsulation despite one line of logic. Don't reject a small,
  well-named method as "shallow" just because its body is short.
- "Classitis" (many tiny shallow classes) is the anti-pattern this guards
  against — it is not an argument against multiple classes in general, only
  against ones that add interface cost without hiding anything.

## Source

https://llm-coding.github.io/Semantic-Anchors/anchor/deep-modules
