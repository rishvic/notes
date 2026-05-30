# Notes are typed by intent, not stored uniformly

Every note has exactly one _intent_ — Reference (look up on demand), Internalise
(move into your head), or Track (actionable backlog) — and each intent gets its
own folder, internal structure, and revision cadence. Capture is a transient
inbox state, not an intent.

## Why

Intent is what scopes the evidence. The strong retrieval-practice and spacing
findings (Roediger & Karpicke 2006; Cepeda et al. 2006; Dunlosky et al. 2013)
govern _Internalise_ notes only — they are about getting information _into_
memory. Applying spaced repetition to a Reference note, which you deliberately
externalised so you would _not_ have to remember it, is a category error. A
single uniform structure would force one revision model onto three jobs that
each want a different one.

## Consequences

- Revision workflows are intent-scoped globs (`internalise/*`, `reference/*`,
  `track/*`).
- A subject that spans intents (e.g. AsciiDoctor → drill syntax / look-up
  cheatsheet / things to build) _spawns_ one note per intent, connected by
  `xref:`.
