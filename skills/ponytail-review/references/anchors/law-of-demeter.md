# Law of Demeter

**Also known as:** LoD, "Only talk to your immediate friends"
**Proponents:** Ian Holland & Karl Lieberherr (Northeastern University, Demeter Project, 1987); popularized by *The Pragmatic Programmer* (Hunt & Thomas)

## Core Concept

A method may call methods on: itself, its parameters, objects it creates,
and its direct component objects — but not on objects returned by those
calls. Chains like `a.getB().getC().doSomething()` ("train wrecks") reach
through intermediaries and couple the caller to a deep object graph. The
remedy is "tell, don't ask": push behaviour to the object that owns the
data instead of pulling data out and operating on it externally. This
limits how much of an object's internal structure leaks to its
collaborators, so internal changes don't ripple outward.

## When to Use

- Reviewing code for hidden coupling and fragile call chains
- Designing object APIs that hide their internal structure
- Guiding a refactor away from a train-wreck expression toward a method on
  the owning object

## When NOT to Use

- Fluent interfaces / builders, where chaining is the intended design
- Immutable value objects and data-query DSLs (e.g. `ChainMap`, ORM query
  builders) where traversal is the point, not a leak
- It's a heuristic, not an absolute — don't flag every method chain, only
  ones that reach through an object to touch what it doesn't own

## Distinct from Locality of Behaviour

Related but not the same failure: LoD is about **coupling depth** (how far
a caller reaches through an object graph). Locality of Behaviour is about
**caller-visibility** (can a reader tell what a call does without leaving
the file). A chain can violate LoD while still being locally visible in one
file, and a single call can be LoD-clean while still hiding behaviour
behind it (a property with a side effect).

## Source

https://llm-coding.github.io/Semantic-Anchors/anchor/law-of-demeter
