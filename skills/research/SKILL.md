---
name: research
description: "Research kept in the repository: how a question about someone else's code is answered by reading it once and keeping the answer — one question per file, the version that was read, the answer with addresses in the code, what could not be checked, and the verification a review passes before work rests on it. Applies where a project keeps reviews in a folder (for instance `research/`); stack-agnostic, works in any environment that can read files. English triggers: research, review, write a review, read the code, check against the code."
---

# Research (a question answered by reading the code)

**When it applies.** A question about a codebase that is not ours — a platform, a library, a neighbour's
module — whose answer will be relied on more than once: how something is addressed, what happens on a
failure, where the limit is, what the platform does before we do anything. The answer is read out of the
code; a model's memory is not an answer, and a decision resting on a guess is a defect.

**Why a file.** The answer outlives the session that found it. Written down, it is read by the next session
in a minute; asked again, it costs the same search again and drifts with every retelling.

## The frame

```markdown
# <the subject, said as a title>

Question: <the one question the review answers, one line>
Platform: <what was read, and its version>
Read by: <the archive / the sources / the live system>; no changes were made
Addresses: <how an address in this file resolves>

<the answer; then the evidence — addresses in the code, commands, numbers; then what could not be checked>
```

- One review — one question: `<folder>/<topic>.md`.
- The version is not decoration: without it the review lies a month later.
- The answer comes first and stands alone; the evidence follows it, so a reader may stop at the answer and a
  doubter has somewhere to go.

## Rules

- **Read-only.** A review changes nothing — not the code it reads, not the system it watches.
- **Every claim carries an address**: a file and a line, a command and its output, a number with the way it
  was taken. A claim without an address is not written at all; its place is "what could not be checked".
- **Quotations are verbatim**, in the language of the code — they are retold only as a translation, never in
  place of the original.
- **A negative result is a result.** "Not found" is written as searched-and-not-found, with what was searched;
  never as absence.
- **The conclusion leaves, the review stays.** What entered the work is lifted into the project picture; the
  review remains as the trace.
- **A review that lies is worse than none.** Before work rests on a review, a fresh reader — not its author —
  takes a sample of the addresses and checks them against the code.

## Price

A review costs one reading; a guess costs the rework that follows it, and a review that lies costs everything
built on it.
