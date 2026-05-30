# File-per-topic, not atomic Zettelkasten

The default unit is one file per topic, split only when it stops being scannable
at a glance or grows two-or-more independently-referenced ideas. Filenames are
subject slugs (`lowercase-kebab.adoc`) with no timestamp IDs and no dates.
Cross-links are sparse, purposeful, and one-directional; backlinks are derived
by the agent on demand, never hand-maintained.

## Why

Zettelkasten's atomic notes, unique IDs, and dense link-web exist to solve a
_paper-era_ retrieval problem. There is no controlled evidence they aid thinking
(the method rests on Luhmann's personal output, proceduralised by Ahrens), and
full-text search plus an AI agent that reads the whole corpus already provide
the index they substitute for. Personal-information-management studies (Bergman
et al. 2008, 2013) further show people retrieve by navigating meaningful files
and treat search as a last resort — favouring navigable topic files over an
atomic-note soup.

## Considered and rejected

- **Atomic / Zettelkasten notes** — high link-maintenance tax, unproven benefit,
  retrieval value already covered by search + agent.
- **Timestamp-ID filenames** (`20260530T1432--slug.adoc`) — destroy
  subject-scannability (the cue you actually navigate by) to provide unique IDs
  we do not need.

## Consequence

This bundles the granularity, naming, and linking conventions under one
principle: _search and the agent replace the manual retrieval hacks Zettelkasten
was built around._ A future reader tempted to "atomise" the corpus should read
this first.
