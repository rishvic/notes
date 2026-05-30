# AsciiDoctor as the authoring format

We author every note in AsciiDoc (`.adoc`), rendered by Asciidoctor, as the
single source of truth for all three intents (Reference, Internalise, Track). We
chose it over Markdown for its single unambiguous specification (Markdown is
fragmented across CommonMark / GFM / MultiMarkdown / …), its richer semantics,
and its native `include::`, `xref:`, and document-attribute mechanisms — which
are exactly what the granularity (ADR-0003), cross-linking, and metadata
decisions rely on.

## Trade-off

AsciiDoc's note-app and spaced-repetition ecosystem is thinner than Markdown's:
Obsidian, Logseq, and Anki are Markdown-first, and the canonical toolchain is
Ruby (asciidoctor.js exists). We accept this because we value the authoring
richness, want notes to look good, and intend to learn AsciiDoctor deeply. If
automated spaced repetition is ever wanted, it is a **downstream export** from
these `.adoc` files (see ADR-0004) — never a reason to change the source format.
