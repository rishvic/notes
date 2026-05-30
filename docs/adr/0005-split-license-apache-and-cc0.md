# Split license: Apache-2.0 for the framework, CC0 for the example notes

The framework — the methodology and everything that teaches it (`README.adoc`,
`AGENTS.md`, `CONTEXT.md`, `docs/adr/`, `docs/origin-brief.md`) — is
**Apache-2.0**. The example notes shipped to illustrate it (`reference/`,
`internalise/`, `track/`, including the `.srs/` data) are **CC0 1.0**. The split
is declared per-path in `REUSE.toml`.

## Why

Two kinds of artifact in one tree, wanting different terms.

The framework is effectively a reusable _agent skill_ — it carries an explicit
agent contract (`AGENTS.md`) — and that ecosystem licenses permissively:
Anthropic's own `anthropics/skills` repo is Apache-2.0, and prompt/skill
libraries default to MIT/Apache. Apache signals "adopt and adapt freely, keep
the notice."

The example notes are seeds meant to be copied, so any attribution obligation is
friction. CC0 puts them in the public domain — the same split `prompts.chat`
uses (permissive framework, CC0 content) — and keeps personal sample data out of
any credit expectation.

## Considered and rejected

- **One Creative Commons license for everything** (CC BY/BY-SA) — the on-the-
  merits choice for a prose-heavy work and what CC/FSF endorse for
  documentation, but it diverges from the AI-skills convention and fits the
  functional template/format snippets poorly.
- **One permissive license over everything** — simpler, but forces adopters to
  carry a notice through sample notes that are meant to be copied freely.

## Consequences

- A root `LICENSE` duplicates the Apache-2.0 text solely so GitHub/GitLab detect
  a license (they can't read REUSE). It carries Apache-2.0, not the
  more-permissive CC0, so the repo isn't mislabelled public domain.
- Relicensing the framework later needs the consent of any outside contributors
  — the hard-to-reverse part this ADR exists to pin down.
