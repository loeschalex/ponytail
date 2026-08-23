# Locality of Behaviour

**Also known as:** Locality of Behavior (American spelling, *Hypermedia Systems*). Never abbreviate "LoB" alone — reads as "Line of Business."
**Proponent:** Carson Gross, ["Locality of Behaviour (LoB)"](https://htmx.org/essays/locality-of-behaviour/), 29 May 2020. Credits Richard P. Gabriel's *Patterns of Software* (1996) for the underlying notion.

## Core Concept

"The behaviour of a unit of code should be as obvious as possible by looking
only at that unit of code." The measure is read-time cost, not write-time
cost — how far a reader must travel to answer "what happens when this runs."
Behaviour at a distance (a handler in a remote file, a convention that binds
by name, an invisible framework hook) is the failure mode; co-location is
the remedy. **This is an explicit trade, not a law**: it argues against DRY
and Separation of Concerns specifically where they scatter one feature
across many files, and concedes the trade openly rather than claiming those
principles are wrong.

## When to Use

- Reviewing a design where understanding one element requires opening
  several unrelated files
- Deciding whether an abstraction earns its indirection or only moves code
  elsewhere (a subclass, a hidden `__getitem__`/property, a side-effecting
  iterator, a decorator that changes behaviour invisibly)
- Weighing convention-over-configuration, dependency injection, event
  buses, lifecycle hooks — all trade locality for other goods

## When NOT to Use

- Not anti-abstraction. A good abstraction leaves its invocation and effects
  obvious at the call site — that's compatible with this principle, not a
  violation of it.
- Not license to un-contain policy that Deep Modules/SSOT say belongs in one
  shared owner. LoB is a caller-visibility check ("can I tell what this does
  without leaving this file"), not an argument for scattering derivation
  logic back out into every caller.
- Contested: co-location makes behaviour *visible*, not necessarily
  *understandable* (John Freeman's critique) — naming things well still
  matters on top of this.
- Not the hardware "Locality of Reference" concept — unrelated, same name
  by coincidence.

## Source

https://llm-coding.github.io/Semantic-Anchors/anchor/locality-of-behaviour
