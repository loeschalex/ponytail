# Law of Demeter

**Key Proponents:** Ian Holland & Karl Lieberherr (Northeastern University, Demeter Project, 1987); popularized by *The Pragmatic Programmer* (Hunt & Thomas)

## Core Concepts

**Only talk to your immediate friends** — a method may call methods on:
itself, its parameters, objects it creates, and its direct component
objects — but not on objects returned by those calls.

**Train-wreck calls** — chains like `a.getB().getC().doSomething()` reach
through intermediaries and couple the caller to a deep object graph — the
classic LoD violation.

**Tell, don't ask** — push behaviour to the object that owns the data
instead of pulling data out and operating on it externally.

**Encapsulation boundary** — LoD limits how much of an object's internal
structure leaks to its collaborators, so internal changes don't ripple
outward.

**Pragmatic limits** — it is a heuristic, not an absolute; fluent builders
and some data-pipeline/query DSLs chain deliberately and are reasonable
exceptions.

## When to Use

- Reviewing code for hidden coupling and fragile call chains
- Designing object APIs that hide their internal structure
- Teaching encapsulation and "tell, don't ask"
- Guiding refactorings away from train-wreck expressions

## When NOT to Use

- For fluent interfaces / builders where chaining is the intended design
- For immutable value objects and data-query DSLs where traversal is the
  point

## Related Anchors

- SOLID Principles — complementary coupling/cohesion guidance
- GRASP — Low Coupling and Information Expert overlap with LoD
- Cohesion Criteria — the cohesion side of the same design concern

> **Note (not from source, written for this library):** distinct from
> Locality of Behaviour. LoD is about **coupling depth** (how far a caller
> reaches through an object graph). Locality of Behaviour is about
> **caller-visibility** (can a reader tell what a call does without
> leaving the file). A chain can violate LoD while still being locally
> visible in one file, and a single call can be LoD-clean while still
> hiding behaviour behind it (a property with a side effect).

## Source

https://llm-coding.github.io/Semantic-Anchors/anchor/law-of-demeter
