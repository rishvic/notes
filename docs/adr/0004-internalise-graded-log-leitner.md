# Internalise scheduling: graded review log + Leitner now, replay later

Spaced retrieval for Internalise notes is driven by an **append-only, graded
review log** — one entry per attempt, `date · item · grade` where grade ∈
`{again, hard, good, easy}` (lowercase constants, as stored in the log).
Scheduling today uses a simple Leitner ladder (1d → 3d → 1w → 3w → 2m → 6m):
`good` promotes one level, `easy` promotes two, `hard` repeats the level,
`again` resets to level 1. The log and derived state live in a machine-only
`internalise/.srs/` sidecar; per-item `[[anchors]]` bind log entries to prompts.

The **scheduler is a pluggable component**, not a fixed feature. The four-grade
vocabulary is the _fixed interface_ — what practice produces and what any
scheduler consumes — while the algorithm above it (Leitner being the default) is
swappable. The interface and the Leitner default are specified in `AGENTS.md`.

## Why

The review log is the only hard-to-reverse asset: you cannot reconstruct grades
you never recorded. The scheduling _algorithm_ and the _derived state_ (`level`,
`next_due`) are, by contrast, a function of the log **plus the set of item ids
declared in the `.adoc` files** — an item with no log entries is simply "new"
(level 1, due one interval after creation) — and can be recomputed at will. So
we protect the log and keep the scheduler swappable. The day we want FSRS — the
machine-learning scheduler that replaced SM-2 as Anki's default in 23.10, and
which fits itself to exactly this kind of review history — or classic SM-2, we
replay the log through it with zero loss.

## Considered and rejected

- **Binary pass/fail** — lossy; forecloses any later model-based scheduler.
- **Hand-running full SM-2 or FSRS now** — ease factors and model parameters
  need hundreds of reviews to behave (SM-2's "ease hell" at small scale), and
  reimplementing them by hand duplicates a library far better run _on the log_
  later. Overkill for a handful of items.
- **A pluggable grade vocabulary** — letting each scheduler define its own grade
  set would destroy the log as a stable interlingua and foreclose the lossless
  replay that makes the scheduler swappable at all. The four grades are
  deliberately the fixed seam: FSRS consumes them natively, SM-2 and binary map
  cleanly onto them.
