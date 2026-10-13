---
name: reflection
description: "Periodic reflection: the project and its scaffolding kept in tone — by traces, not by feelings. Looks for architecture drift, weak spots in design, redundant and repeated agent actions, conventions that are not followed, divergences between the project's life and the law in force. Modes: pulse — a quick pass after a series of tasks; review — a full one, periodically; either narrows to a subject — a module, a theme, a series of tasks. Started by the user on request («reflection», «audit», «pulse», «what can be improved»); a fitting moment is a reason to propose it, not to start it. The result is improvement points in the conversation. English triggers: reflection, audit, architecture review, pulse check, look for improvements."
---

# Reflection

A regular look at the project and the scaffolding around it: code, architecture, documents, the law in force, the way agents work. The goal is to keep things in tone: to find drift, weak spots in design and process before they become expensive.

The result is improvement points: what to fix and by which trace, or an honest "clean". An empty outcome is normal; findings are not invented for volume. Reflection changes nothing: changes are made by ordinary tasks.

## The tails, not the mean

The material is the period's slowest work, unwound one by one from its own records; a mean hides exactly what the pass is for — where work cost far more than it looked, the defect is in the process before it is in that work. A session spending most of its time inside its own steps is not slow — it is a process that hands it too many steps. The steps spent, how a task is cut, the price of a script, waiting and the landing are material for the analysis, never goals of their own; what a point must shorten is read by the law's own test — a change is counted by what it removes — and is not restated here.

## Modes

- **Pulse** — a quick pass after a series of tasks: whether something slipped. Consistency, hygiene, adherence to the law in force — without diving deep.
- **Review** — a full one: architecture, quality, process, scaffolding. More expensive; runs periodically or after a trace found by a pulse.
- **Subject** — either mode narrows: "on the plugin", "on the upload module", "after the gate tasks". Do not spread beyond the subject; something heavy noticed on the way goes as a separate item, without unwinding.

A mode not named — choose by the size of the request: "run through it" — a pulse, "audit", "reflection" — a review; in doubt — ask.

## By traces, not by feelings

The material is artifacts that left a trace:

- **git**: history and diffs for the period or the subject — what changed and how; a run of edits in one zone, rollbacks, returns to the same place — direct signals of process;
- **state**: files, documents, configs — against the law in force and what PROJECT.md claims;
- **journal**: if the environment keeps a journal of sessions and actions, it is the first material on process: steps, repeats, time;
- **session**: reflection right after the work sees it with its own eyes — do not re-ask what is already in front of them.

Go deep by trace: a suspicious place is unwound, the rest is not re-read. Every item carries a trace — a commit, a file, an output; without a trace the item does not exist: "it seems to have become more complex" is not a finding until shown where.

## Review

**Project.** Drift from the laid-down principles: bypassing owners and joints, connections that should not exist, modules that grew without reason, decisions that hold "because it was once decided". Design errors and non-obvious places: edges, silent failures, places where the next session will be mistaken. Documents against facts — PROJECT.md, specs.

**Law.** The project's life against the law in force: where the two diverge — a rule that left no trace in how the project works; compliance that is only formal; guesses, workarounds, re-clarifications where the law already gives the answer. Each item carries an address — the file, the rule — and the fix is the project's, not the law's.

**Process.** Redundant and repeated agent actions: reworks, rollbacks, double checks, circles around the same thing; tasks that cost more than they looked. The unspoken — what took shape by itself but is written nowhere — and what had to be clarified over and over: candidates for PROJECT.md. **Retold instead of read:** whether the load-bearing details of the work — a rule, a path, a number, a mechanism — were opened in their source or taken from a summary and from memory; a rule of the platform's behaviour or look, a path, a number the work rests on and nobody opened is a finding, and it is the class of defect that survives every review of the code itself.

**Scaffolding.** Skills: did they work, have they drifted from life. Files: are they turning into a log, a dump or a stale copy.

## Pulse

A short pass, minutes:

- consistency: documents against facts — PROJECT.md, specs, claims;
- hygiene: `tmp/` — laid out by work and without abandoned things; specs closed or deleted; nothing temporary left in the code;
- law: recent changes follow the law — commit messages, checks by the size of the change, derived artifacts in the same change;
- process: where a series of tasks ran noticeably more expensive than it should — leave a trace for the review.

## The question itself

A pass names, with the question it was given, the one whose answer would make the whole pass unnecessary. The asking side's own framing is material too: it is named in words, and where it presupposes a thing (that a guard must exist, that a document must be kept, that a number must be improved), the presupposition is named with it.

**A thesis of the asking side is a claim under test, never a premise.** It enters the pass with the command that confirms or refutes it, and where no such command exists the pass says so in those words instead of agreeing; the pass's own agreement is not a finding, and a word from the owner is the ground of a proposal, not of a landing.

The outcome is stated as an answer to that question; what the question left out is named as what it left out. A pass that finds the frame wrong says so and stops, rather than answering well inside it. The default direction of an improvement point is **subtraction** — what can go — and a proposal that only adds is refused.

Keep, and say that it is kept: a rule that holds and is paid for by a defect; a number whose artifact is a command; a door that a reader needs to act; a reason whose loss would make the next session decide wrongly. What is trimmed is the chronicle, the receipt, the repeated sentence and the number whose artifact has gone.

## Result

The outcome goes into the conversation, briefly: improvement points — the subject, the essence, the trace. Findings go to execution: reflection names only what is verified as an improvement, therefore "can wait" does not exist — a fix through an agent is cheap, a postponement is more expensive. The user's word is the one hold it knows: what the user puts off is named with its reason. Doubt that something is an improvement — not a finding: drop it or ask. "Clean" is an outcome too: name what was checked against. No file is started: an extract asked for while the work runs goes into `tmp/<slug>/`, and what survives a reflection is its conclusion — lifted into the picture or into the code — not a file.

**A declared budget, and a handover that is not optional.** Before the first step the pass fixes what it may spend — steps or credits — and what it hands over; reaching the budget ends the pass in its result, never in a continuation.

## Boundaries

- It changes nothing itself: findings are items, fixes are tasks.
- The user starts it; the agent may propose a moment — a series of tasks is closed, a review has not run for long — but does not start it.
- A report for the sake of a report is not assembled: reflection is about improvement points, not about a document.
- The laws are not a subject by default: they are taken as correct. The user's explicit request — «reflect on the laws», say against this project's knowledge — opens that subject as well; its findings go to the kit as ordinary proposals.
