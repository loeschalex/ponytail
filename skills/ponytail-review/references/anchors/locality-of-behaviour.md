# Locality of Behaviour

**Also known as:** Locality of Behavior (American spelling, used in *Hypermedia Systems*)

## Core Concepts

- **The principle in one sentence**, from the essay that named it: "The
  behaviour of a unit of code should be as obvious as possible by looking
  only at that unit of code."
- **Read-time cost over write-time cost.** The measure is how far a reader
  must travel to answer "what happens when this runs", not how few
  characters the author typed.
- **Behaviour at a distance is the failure mode.** A handler registered in
  a remote file, a convention that binds by name, a framework hook that
  fires invisibly — each is correct code that cannot be understood locally.
- **Co-location as the remedy**: markup, handler, styling and validation
  for one element live where that element is.
- **An explicit trade, not a law.** The essay argues against DRY and
  Separation of Concerns **where they scatter one feature across many
  files**, and concedes the trade openly rather than claiming the other
  principles are wrong.

## When to Use

- Reviewing a design where understanding one element requires opening
  several unrelated files
- Deciding whether an abstraction earns its indirection, or only moves
  code elsewhere
- Weighing convention-over-configuration, dependency injection, event
  buses, decorators and lifecycle hooks — all of which trade locality for
  other goods
- Arguing about whether a repeated fragment should be extracted at all

## Common Misunderstandings

- **Reading it as anti-abstraction.** A good abstraction leaves its
  invocation and effects obvious at the call site; that is entirely
  compatible with the principle.
- **Confusing it with Locality of Reference.** That is a
  hardware-performance concept about memory access patterns (temporal and
  spatial locality). The name is a coincidence, not a lineage.
- **Treating co-location as sufficient.** Visible is not the same as
  understandable — see Criticism, below.
- **Using the abbreviation on its own.** "LoB" reads as "Line of Business"
  far more often than as this principle.

## Criticism

- **Co-location makes behaviour visible, not understandable.** John
  Freeman argues in ["Locality of Behavior on its own isn't enough"](https://www.eloquentarchitecture.com/locality-of-behavior/)
  (January 2023) that `<button hx-get="/clicked">` shows **that** something
  happens, not **what**: "One can only achieve behavior transparency to a
  certain extent without also taking a minute to name things well."
- **The principle is turned against its own tool.** Chris Done's
  ["A modest critique of Htmx"](https://chrisdone.com/posts/htmx-critique/)
  (August 2024) uses LoB to argue that htmx breaks it: attribute
  inheritance means behaviour "comes from all the way up there or some
  other module", so it "is not local". The same objection was raised
  inside the project in [htmx discussion #2835](https://github.com/bigskysoftware/htmx/discussions/2835).
- **The sharpest objection is that it renames a trade-off.** On
  [Hacker News](https://news.ycombinator.com/item?id=38241623), a
  commenter calls it "such a poorly defined rule — it's just an invented
  name for going against separation of concerns". Recorded because it
  states the strongest form of the counter-position, but the author is
  pseudonymous, which is weaker evidence than the named critiques above.
- **The documented counter-argument is thinner than the claim deserves.**
  For an essay that attacks Separation of Concerns directly, a search in
  English and German found no worked rebuttal from the established
  frontend or SPA side that names the principle. The critique that exists
  comes from inside the htmx camp or is constructive rather than opposing.
  That is an absence in the search, not a demonstrated absence.

## Current Status

- **Named in 2020, still the current formulation.** Carson Gross,
  ["Locality of Behaviour (LoB)"](https://htmx.org/essays/locality-of-behaviour/),
  29 May 2020. The essay does not claim the idea is new; it credits
  Richard P. Gabriel's *Patterns of Software* (Oxford University Press,
  1996) for the underlying notion of locality — a quotation verified in
  the essay but not in Gabriel's book itself.
- **Two spellings, one author.** The essay uses the British "Behaviour";
  the book [*Hypermedia Systems*](https://hypermedia.systems/client-side-scripting/)
  (2023) uses the American "Behavior". Both are primary. This entry
  follows the essay, which is also the spelling that measured stronger on
  weak models — see the [prior-test register](https://llm-coding.github.io/Semantic-Anchors/prior-tests).
- **Adopted beyond htmx, but within one family.** Django (Carlton Gibson,
  [2024](https://buttondown.com/carlton/archive/locality-of-behaviour/),
  calling it "a starting point, not a destination") and Laravel
  ([Freek Van der Herten, 2023](https://freek.dev/2513-locality-of-behaviour))
  have taken it up. These are server-rendered ecosystems adjacent to
  htmx; adoption into independent textbooks, standards or framework
  documentation is not established.

> **Note (not from source, written for this library):** not license to
> un-contain policy that Deep Modules/SSOT say belongs in one shared
> owner — LoB is a caller-visibility check, not an argument against a
> shared owner. Distinct from Law of Demeter: LoB is about caller
> visibility (can a reader tell what a call does without leaving the
> file), LoD is about coupling depth (how far a caller reaches through an
> object graph). A chain can violate one without the other.

## Source

https://llm-coding.github.io/Semantic-Anchors/anchor/locality-of-behaviour
