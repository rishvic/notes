# Personal Notes — Context

This is a personal notes directory: a place to record things worth revisiting
later. The glossary below fixes what each kind of note _is_ — not how it is
structured, named, or tooled. Those decisions live in `docs/adr/`, never here.

## Language

**Note**:
A single self-contained record of something worth revisiting. Every note has
exactly one _intent_: Reference, Internalise, or Track.
_Avoid_: entry, doc, page — use "note" for the unit.

**Intent**:
The single job a note serves — Reference, Internalise, or Track. A note's intent
fixes which folder it lives in, how it is written, and how (or whether) it is
revisited. One subject may spawn notes of several intents.
_Avoid_: "type", "kind" — use "intent".

**Reference note**:
A note kept so you can _look something up on demand_ — knowledge deliberately
externalised so you do not have to hold it in your head. Success = findability
and accuracy.
_Avoid_: "second brain", "resource" (PARA term).

**Internalise note**:
A note for material you want to move _into your own head_ — to recall unaided or
to change your own behaviour — not merely look up. Success = durable
retention/transfer. This is the only intent the spacing/retrieval-practice
evidence governs.
_Avoid_: "study note", "flashcard" (a flashcard is one possible form, not the
intent).

**Track note**:
A note that holds _actionable items with a lifecycle_ (e.g. idea → active →
tabled → done). Success = staying current and triaged; never memorised.
_Avoid_: "todo", "project". ("Backlog" is fine informally.)

**Capture**:
A transient _state_, not an intent: a raw, undigested jotting sitting in an
inbox until it is processed into a Reference, Internalise, or Track note (or
discarded).
_Avoid_: "fleeting note" (Zettelkasten term), "draft".

**Topic**:
The subject a note is about (e.g. "AsciiDoctor syntax", "git rebase"). The
default Reference unit is one file per topic.
_Avoid_: "category", "area" (PARA term), "tag".

**Idea**:
A single self-contained point inside a note. When one note accumulates two or
more _independently-referenced_ ideas, that is the signal to split it.
_Avoid_: "atom" (Zettelkasten term), "card".

**Process** (verb):
To convert a Capture-state jotting into a typed Reference/Internalise/Track note
— or discard it. The deliberate work (selecting, rephrasing, turning an
observation into a production prompt) happens here, not at capture time.
_Avoid_: "file", "sort".

**Spawn** (verb):
When one subject — or one capture — produces several notes of _different
intents_ (e.g. a phrasing observation spawns an Internalise drill and a
Reference cheatsheet). The spawned notes are connected by `xref:`, never merged
into one.
_Avoid_: "split", "derive", "decompose".

**Prompt / Response**:
The two halves of an Internalise item: the _prompt_ states a situation or cue;
the _response_ is the form you want to produce unaided — a single canonical
answer for a fact-like item, or a worked _exemplar_ for a skill item, where a
faithful variant of the same move still counts. The response stays hidden until
you have attempted it.
_Avoid_: "front/back" (Anki term), "flashcard".

**Grade**:
Your own assessment of a single retrieval attempt on an Internalise item, on a
fixed four-value scale: _again_ (couldn't produce), _hard_ (laboured), _good_
(clean), _easy_ (instant). You record a grade after each attempt; it is the
stable vocabulary all revisit-scheduling builds on, whatever method does the
spacing.
_Avoid_: "score", "rating", "button" (Anki term).

## Flagged ambiguities

**Revision** — used in two incompatible senses, with two different evidence
bases. Keep them apart:

- _Revising **from** a note_ = studying it to get it into your head (British
  "exam revision" sense). Applies to **Internalise** notes only. Governed by the
  retrieval-practice and spacing research.
- _Revising **a** note_ = editing/updating/pruning it so it stays correct and
  useful ("gardening", maintenance). Applies to **Reference** and **Track**
  notes. The memory research says nothing about this.

Resolution: keep **"revision strategy"** as the umbrella term for the whole
"when and how do I revisit notes" question, but inside it always say
**practice** (from a note) or **maintenance / gardening** (of a note) so it is
unambiguous which activity — and which evidence — is in play.

**"Lookup-able"** — used to decide what to _exclude_ from a Reference note, and
easy to misread as "exists online". It does not mean that. The test is
**transformation value to you**: exclude only what you would regenerate faster
than you would find it in your own notes, with no selection, distillation, or
provenance value. A curated, sourced distillation is worth keeping even when the
raw facts are a web search away.

## Example dialogue

> **You:** Is the "learn AsciiDoctor more deeply" thing a Reference note?
>
> **Agent:** Depends what you want from it. The part where you _drill the syntax
> until you can write it unaided_ is an **Internalise** note. The part where you
> _paste blocks you'll look up mid-edit_ is a **Reference** note. And "things I
> might build once I know it well" is a **Track** note — a backlog with a
> lifecycle, not something you memorise or look up.
>
> **You:** So one subject can spawn three notes?
>
> **Agent:** Yes. The subject is the same; the _intent_ differs, and intent is
> what fixes the note's structure and how (or whether) you revisit it.
