# Origin brief — Designing My Personal Notes Directory

> **Historical artifact — frozen, not maintained.** This is the original
> `/grill-with-docs` brief that produced this notes system. It records the
> _provisional_ thinking and the evidence bar going _into_ the design session;
> it is not a description of the system as it stands. Where this brief and the
> repository disagree, the repository is right. The decisions that resolved
> these questions live in `docs/adr/` (the _why_), `README.adoc` (the _how_),
> and `CONTEXT.md` (the vocabulary).

## What I want

This directory is where I keep notes on anything I might want to revisit later.
Right now it holds a couple of bare `.adoc` files. I want to land on a structure
that is **fast to reference**, **pleasant to author**, and **easy for an AI
agent to navigate and maintain** — and I want that structure justified by
evidence, not by whatever is fashionable in productivity blogs.

I want to run this as a `/grill-with-docs` session. Use the grilling to
co-design and stress-test the structure with me, and capture the decisions as we
make them.

## How to run this

`/grill-with-docs` is built to interrogate a _plan_ against a _domain model_,
one question at a time, recommending an answer for each. Adapt it to this repo
as follows:

- **I have a provisional plan below — challenge it.** Don't accept my leanings;
  pressure-test each one and tell me where I'm wrong.
- **Where the skill says "explore the codebase to answer a question," here that
  means: read the existing notes, and do real research.** The "domain" is my
  note-taking practice, not a software system.
- **Ground every recommended answer in high-quality primary sources** (see the
  evidence bar below). Surface the sources inline as we go, not in a dump at the
  end.
- **Capture decisions as they crystallise, using the skill's own artifacts:**
  - `CONTEXT.md` — a glossary of _my_ note-taking vocabulary (what counts as a
    "note", an "entry", a "topic", an "idea", a "revision"). Keep it a glossary
    and nothing else — no structure or tooling decisions here.
  - `docs/adr/` — Architecture Decision Records for the load-bearing, hard-to-
    reverse choices (e.g. AsciiDoctor as the format, file-granularity model,
    naming/dating convention, agent-facing metadata). Offer these _sparingly_,
    only when they clear the skill's three-part bar (hard to reverse, surprising
    without context, the result of a real trade-off).

## My current thinking (provisional — grill it)

- **Format: AsciiDoctor.** I want to author in AsciiDoc and lean on its features
  to make notes look good. (Also: spin up a note tracking that I want to learn
  AsciiDoctor more deeply — that's a real TODO, not an aside.)
- **Organisation: one file per topic.** Today that's `improve-eng.adoc` and
  `oss-contribs.adoc`. I'm not committed to this — challenge file-per-topic vs.
  atomic/linked notes (Zettelkasten-style) vs. a hybrid.
- **Authoring: AI-assisted.** I'll use agents to help write and clean up notes.
  This makes **agent-navigability a first-class constraint**: consistent
  structure, predictable file naming, and machine-readable metadata matter.
- **Goal: quick reference + a revision strategy** for updating notes over time.

## The existing notes (context for the domain)

- `improve-eng.adoc` — things I notice about my English that I want to improve
  but don't have time to dig into in the moment, so I jot them down for later.
- `oss-contribs.adoc` — open-source contribution ideas: ones I'm actively
  working on, and ones tabled for later exploration.

Both are deliberately bare. Expect to restructure them, and migrate them into
whatever structure we agree on (or leave me a concrete migration plan).

## The research I want, and the evidence bar

Do extensive research _before_ recommending a structure. Do not make
assumptions.

**The bar:**

- Prefer peer-reviewed cognitive-science and learning-science research. Where
  good academic evidence doesn't exist, say so and fall back to the most
  credible practitioner sources you can find.
- **For every claim, name the source and evaluate its quality** (study type,
  sample, replication status, whether it's primary research or secondary
  commentary).
- **Tier your claims explicitly.** Be honest about the asymmetry here: the
  _revision_ question rests on strong experimental evidence, while most _note-
  structure_ advice (Zettelkasten, PARA, "second brain") is practitioner
  convention, not validated science. Don't launder the latter as the former.

**Questions to resolve:**

- **How to write a note** — grammatical and semantic layout that aids later
  recall and fast scanning.
- **What to include and exclude** to keep notes effective (note that the
  evidence on summarising/highlighting as study acts is unflattering — let that
  inform the guidance).
- **A revision strategy** — when and how to revisit and update notes.

**Verified anchor sources to start from** (starting points, _not_ a substitute
for your own search and source evaluation):

- Roediger & Karpicke (2006), _Psychological Science_ 17(3):249–255 — the
  testing/retrieval-practice effect.
- Dunlosky, Rawson, Marsh, Nathan & Willingham (2013), _Psychological Science in
  the Public Interest_ 14(1):4–58 — rates practice testing and distributed
  practice as high-utility; summarising, highlighting, and rereading as
  low-utility.
- Cepeda, Pashler, Vul, Wixted & Rohrer (2006), _Psychological Bulletin_
  132(3):354–380 — spacing-effect meta-analysis; the optimal review interval
  scales with the intended retention interval.

The through-line these suggest: passive summarising/highlighting is weak; the
leverage is in **self-testing and spaced revisitation** — so the revision
strategy should probably be the centrepiece, not an afterthought.

## Definition of done

By the end of the session I want:

1. An agreed note structure: file granularity, naming convention, internal
   layout, cross-linking approach, and agent-facing metadata.
2. `CONTEXT.md` populated with the resolved glossary.
3. ADRs for the load-bearing decisions (per the skill's bar).
4. A concrete, evidence-grounded revision strategy.
5. The two existing notes migrated into the new structure (or a concrete plan
   to).
6. The AsciiDoctor-learning note created.
