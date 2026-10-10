---
name: reflection
description: "Periodic reflection: the project and its scaffolding kept in tone — by traces, not by feelings. Looks for architecture drift, weak spots in design, redundant and repeated agent actions, conventions that are not followed or that get in the way. Started by the user on request («reflection», «audit», «pulse», «what can be improved»); a fitting moment is a reason to propose it, not to start it. English triggers: reflection, audit, architecture review, pulse check, look for improvements."
---

# Reflection

A regular look at the project and the scaffolding around it: code, architecture, documents, conventions, the way agents work. The goal is to keep things in tone: to find drift, weak spots in design and process before they become expensive.

The result is improvement points: what to fix and by which trace, or an honest "clean". An empty outcome is normal; findings are not invented for volume. Reflection changes nothing: changes are made by ordinary tasks — conventions included.

## Modes

- **Pulse** — a quick pass after a series of tasks: whether something slipped. Consistency, hygiene, adherence to conventions — without diving deep.
- **Review** — a full one: architecture, quality, process, scaffolding. More expensive; runs periodically or after a trace found by a pulse.
- **Subject** — either mode narrows: "on the plugin", "on the upload module", "after the gate tasks". Do not spread beyond the subject; something heavy noticed on the way goes as a separate item, without unwinding.

A mode not named — choose by the size of the request: "run through it" — a pulse, "audit", "reflection" — a review; in doubt — ask.

## By traces, not by feelings

The material is artifacts that left a trace:

- **git**: history and diffs for the period or the subject — what changed and how; a run of edits in one zone, rollbacks, returns to the same place — direct signals of process;
- **state**: files, documents, configs — against the conventions and what PROJECT.md claims;
- **journal**: if the environment keeps a journal of sessions and actions, it is the first material on process: steps, repeats, time;
- **session**: reflection right after the work sees it with its own eyes — do not re-ask what is already in front of them.

Go deep by trace: a suspicious place is unwound, the rest is not re-read. Every item carries a trace — a commit, a file, an output; without a trace the item does not exist: "it seems to have become more complex" is not a finding until shown where.

## Review

**Project.** Drift from the laid-down principles: bypassing owners and joints, connections that should not exist, modules that grew without reason, decisions that hold "because it was once decided". Design errors and non-obvious places: edges, silent failures, places where the next session will be mistaken. Documents against facts — PROJECT.md, specs.

**Process.** Redundant and repeated agent actions: reworks, rollbacks, double checks, circles around the same thing; tasks that cost more than they looked. Conventions — from both sides: what was not followed and why; what was followed formally or got in the way — where guesses, workarounds and re-clarifications were needed. The unspoken — what took shape by itself but is written nowhere. Re-clarified and unspoken things are candidates for PROJECT.md. **Retold instead of read:** whether the load-bearing details of the work — a rule, a path, a number, a mechanism — were opened in their source or taken from a summary and from memory; a rule of the platform's behaviour or look, a path, a number the work rests on and nobody opened is a finding, and it is the class of defect that survives every review of the code itself.

**Scaffolding.** Skills: did they work, have they drifted from life. Files: are they turning into a log, a dump or a stale copy. Experimental rules of the kit: how the observation goes — benefit, friction or silence.

## Pulse

A short pass, minutes:

- consistency: documents against facts — PROJECT.md, specs, claims;
- hygiene: `tmp/` — laid out by work and without abandoned things; specs closed or deleted; nothing temporary left in the code;
- conventions: recent changes follow the rules — commit messages, checks by the size of the change, derived artifacts in the same change;
- process: where a series of tasks ran noticeably more expensive than it should — leave a trace for the review.

## The question itself

A pass answers the question it was given, and that is its blind spot: a clean answer to the wrong question reads as success. So the question is opened before the material — what is being asked, **and which question is not being asked**, the one whose answer would make the whole pass unnecessary. The asking side's own framing is material too: it is named in words, and where it presupposes a thing (that a guard must exist, that a document must be kept, that a number must be improved), the presupposition is named with it.

The outcome is stated as an answer to that question; what the question left out is named as what it left out. A pass that finds the frame wrong says so and stops, rather than answering well inside it. The default direction of an improvement point is **subtraction** — what can go — and a proposal that only adds is refused unless it removes more than it adds.

## Result

The outcome goes into the conversation, briefly: improvement points — the subject, the essence, the trace. Findings go to execution: reflection names only what is verified as an improvement, therefore "can wait" does not exist — a fix through an agent is cheap, a postponement is more expensive. The user's word is the one hold it knows: what he puts off is written down with its reason. Doubt that something is an improvement — not a finding: drop it or ask. What the reflection itself got wrong, or could not check, is named with it; a finding is read by someone who did not write it, and where the work allows no second reader, the report says so. "Clean" is an outcome too: name what was checked against. No file is started: an extract asked for while the work runs goes into `tmp/<slug>/`, and what survives a reflection is its conclusion — lifted into the picture or into the code — not a file.

Findings about conventions are named separately so that they do not drown among project ones: this is the shared layer, and a fix acts in every project.

## Boundaries


- The user starts it; the agent may propose a moment — a series of tasks is closed, a review has not run for long — but does not start it.
- A change that reaches the whole scaffolding — the law, the procedures, the documents as a class — is a sweep, `dsh-sweep`, not a reflection.
- A report for the sake of a report is not assembled: reflection is about improvement points, not about a document.

## The update loop

A run names what this shape made easy and what it cost, and corrects this file in the same commit as the law it serves.
