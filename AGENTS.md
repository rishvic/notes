# AGENTS.md — Agent contract

The contract an AI agent follows when maintaining this notes corpus. The
human-facing method — how _you_ write and revisit notes — lives in
`README.adoc`; this file is the machine side of the same system: the operations
the agent runs and the data it owns. The decisions behind it are in `docs/adr/`.

## Operations

**Practice (Internalise).** Read `internalise/.srs/state.json`; for each item
with `next_due <= today`, show its prompt, take the produced answer, compare to
the response, ask for or infer a _grade_, append it to `log.jsonl`, and update
`state.json` with the active scheduler (below).

**Hygiene sweep (Reference).** Check for dead links, near-duplicate notes, and
contradictions; list notes whose `:review_by:` is past or whose `:updated:` is
old. Report — do not auto-edit.

**Triage (Track).** Present each Track note's items grouped by status; ask what
changed; move, promote, demote, and prune on instruction.

**Backlinks.** On request, find references to a note by searching the corpus for
its filename and anchors. Do not store them.

**Validate.** Check that each note's `:intent:` matches its folder, that
Reference notes have a `:source:`, that `xref:` targets resolve, and that every
Internalise item id in a `.adoc` has a `state.json` entry and vice-versa — a
newly created item being initialised per the active scheduler's new-item rule
(below).

## Internalise scheduling

The scheduler is a **pluggable component**: the framework fixes the _interface_
and ships Leitner as the default. The active scheduler is whatever this section
declares — currently **Leitner**. Why the seam sits here — why the grades are
fixed but the algorithm is not — is recorded in
[`docs/adr/0004`](docs/adr/0004-internalise-graded-log-leitner.md).

### Interface (fixed)

- **Reads:** the append-only graded log (`{item, date, grade}`, where
  `grade ∈ {again, hard, good, easy}`) plus the set of item ids declared in the
  `.adoc` files.
- **Writes:** a `next_due` per item, plus whatever internal state the scheduler
  needs, into `state.json` — whose schema is therefore scheduler-defined.
- **Invariant:** `state = f(log + item ids)`. The log is authoritative;
  `state.json` is derived and never hand-edited.
- **Fixed contract:** the four-grade vocabulary. A scheduler _must_ consume
  these grades; it may map them internally (e.g. SM-2's 0–5 quality scale).

### Default scheduler: Leitner

Interval ladder — the gap before an item is next due:

| Level    | 1     | 2      | 3      | 4       | 5        | 6        |
| -------- | ----- | ------ | ------ | ------- | -------- | -------- |
| Interval | 1 day | 3 days | 1 week | 3 weeks | 2 months | 6 months |

Grade → level move:

| Grade   | Move                            |
| ------- | ------------------------------- |
| `again` | reset to level 1 (due tomorrow) |
| `hard`  | stay at current level           |
| `good`  | +1 level                        |
| `easy`  | +2 levels                       |

If an item fails (`again`) ~4+ times, flag it to be **rewritten**, not
re-drilled — chronic failure usually means a bad prompt, not a scheduling
problem.

**New item (Leitner-specific).** A freshly created item has no log entries yet
still needs a `state.json` entry. It enters at **level 1, `reps` 0**, with
`next_due` = creation date + the level-1 interval (1 day), and is _not_ written
to `log.jsonl` until its first graded review. This is the uniform rule applied
everywhere: `next_due = anchor + interval[level]`, where the anchor is the
creation date for a new item and the last review date thereafter. `reps` 0 marks
an item as never-reviewed.

### Swapping the scheduler

Replace this section with the new algorithm, then replay `log.jsonl` to
regenerate `state.json`. The log, the prompts, and your practice are all
unchanged — only the derived schedule differs. Schedulers that consume the
grade-log directly: FSRS (native — the four grades are its native input), SM-2
(map the four grades to its quality scale), or a plain binary pass/fail (`again`
→ fail, the rest → pass).

## The `.srs/` sidecar

Machine-managed; never edited by hand.

`internalise/.srs/log.jsonl` — append-only, one JSON object per review:

```json
{"item":"english#need-action","date":"2026-05-30","grade":"good"}
```

`grade` is one of the lowercase constants `again | hard | good | easy`.

`internalise/.srs/state.json` — derived (recomputable from the log plus the set
of item ids declared in the `.adoc` files), one entry per item. Under the
Leitner default:

```json
{
  "english#need-action": { "level": 2, "next_due": "2026-06-02", "reps": 3 }
}
```

The log is the durable asset; the state and schedule are a function of it. A
different scheduler keeps its own per-item fields here, but the log it replays
is the same.
