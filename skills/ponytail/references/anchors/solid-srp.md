# SOLID — Single Responsibility Principle

## Intent

A class should have only one reason to change. Each module or class
should be responsible for a single part of the software's functionality.

## When to Use

- A class has multiple unrelated responsibilities
- Changes to one feature require modifying unrelated code
- Unit testing requires complex setup due to tangled concerns

## Prompt Example

"Refactore diese Klasse nach dem SOLID-Single Responsibility Principle.
Trenne die Verantwortlichkeiten in separate Klassen."

## Related Anchors

- SOLID Principles (Umbrella)

> **Note (not from source, written for this library):** cited in this
> library as the counterweight when a Deep Modules argument would
> otherwise justify folding unrelated responsibilities into one class
> chasing interface depth. Not a mandate to split by every plausible axis
> of change — "one reason to change" is about cohesion, not about
> minimizing lines per class. Splitting a genuinely cohesive deep module
> into shallow pieces to satisfy a narrow reading of SRP re-creates the
> "classitis" anti-pattern Deep Modules warns against — the two
> principles bound each other, neither wins outright.

## Source

https://llm-coding.github.io/Semantic-Anchors/anchor/solid-srp
