# AGENTS.md — work conventions

Rules of work and a map of what lives where; the details are in the add-ons, read on demand:

- `PROJECT.md` — the project picture: what it is and for whom, boundaries, stack and layout, how to run and check, what is settled. No file — build it (see "Project picture").
- `SPEC.md` — the contract of the active task; lives until acceptance.
- `tmp/` — drafts and runs; outside git.
- `NOTES.md` — the backlog of what is put off; read together with the picture. No file — started with the first item put off.

Project specifics live in PROJECT.md: it refines these conventions and may override them by naming the divergence explicitly. Silence leaves the conventions in force. The project lives in git: history is the ground for rollbacks and parallel tasks.

## Project picture

PROJECT.md is the living picture of the project. The reader is an agent: a cold session enters the work through the picture, not by re-reading the code. The picture holds what saves an entry: agreements, pitfalls, "why it is so"; what the code yields in a minute stays out. An outdated picture is worse than none: it lies with confidence.

The picture is not a log: no dates, no "what was done", no chronicles or progress lists. What is done lives in git; the picture describes the project as it is now.

A session starts with the picture. No file — build it: the visible part comes from code, configs and git history; questions are asked only about the unknowable, in a batch. When the file and the facts diverge, the fact wins and the file is brought to it in the same pass.

The picture is kept by whoever changed the project: a task is closed and something changed — update it in the same pass. There is one picture: no second picture file is started; parallel agents edit it along with the code, and git reconciles conflicts. When it stops being readable in one sitting, it is split, but the entry stays single.

## How the work goes

**Code after agreement.** Before implementation — a check of understanding: how the task is understood, what is proposed, where the doubts are.

**The shape before the code.** New work and rework begin with how the thing is done where it will live — the neighbouring code, the platform's or library's own way, the sample the previous attempt left — and not with the first draft that comes to mind. The shape is written down before the code: what it is, what it gives, what it depends on, what it refuses, and which alternatives lost and why. What is missing to answer this is found out in the same step: a decision that rests on a guess is a defect. The agreement is about the shape; the code follows it.

**Questions in a batch, with a default** — so that "yes, that way" answers them. Zero questions on a task that has a spec is suspicious. One round of questions before the code is cheaper than three reworks after it.

**Challenge is the norm.** Words are not taken as truth: verify, doubt, name the weak spots — in the decisions of the user and of the agent alike. Agreement out of politeness is a loss. The goal of the argument is truth, not agreement.

**Report by evidence.** A handover names: what was done; what confirms it — a command and its output, not "it works"; what the check did not show; where the work stopped if unfinished. The same holds for written texts: "works", "faster", "safe" are not written without a command, a measurement or a reference. Success is claimed after observation, not instead of it. A claim read off a tree another hand is writing names the revision and the state it was read at, because the same read taken twice inside a quarter of an hour gives two answers, and both are true. A reading that touches a live environment names what the environment gave it — an identifier the other side generates per call, a count of another program's own furniture — or says in its own words that the two cannot be told apart.

- **A dead end is a report, not a siege.** Signs of a dead end: the solution does not stand on the facts — it cannot be implemented, the inputs diverged, it went wrong; or several different approaches gave no progress. Once the dead end is recognised, the search stops: a short report goes up — where it stopped, what was tried, what is proposed; the addressee is the task setter, and under delegation the lead agent. The reverse boundary: the rule is about a dead end, not about the first difficulty; the executor makes reasonable attempts before reporting.

**A retelling is not a reading.** A rule, a path, a number or a mechanism the work will stand on is taken from its source at the moment it becomes load-bearing; a summary, a review's own words or the memory of the one who read it is a prompt to open the source, not a substitute for it.

**Checks by the size of the change.** The mapping "type of change → set of checks" lives in the project and is not chosen anew for every change; the full set is for changes that touched logic. Edits of texts and data are checked pointwise. A move or a rename is not a text edit: anything that depends on location is checked by a run. A check is written so that what is legitimate does not fall under it; a legitimate hit is named in the report and the check is corrected — the text is not edited to satisfy it.

**Agent steps are the main cost.** Related edits go in one pass; independent checks run in parallel and are designed as such; intermediate runs between small edits are not repeated. Large outputs live on disk — extracts come into the conversation.

**Ritual into a tool.** A command sequence that repeats time and again is reduced to a single command: the tool keeps the order, not memory. Final checks of a task are the same ritual. A third one-off script on the same subject is a reason to make a command.

**Commit and push are part of the work.** A finished and verified piece is committed at once, without "should I commit?": history provides the rollback. The message follows the style of the repository. Only the work of the task goes into the commit. Closing the task goes to the remote in the same pass, without a question — if a remote exists; a push may be held back for a named reason, named where the work is reported and standing in the backlog while it holds, so that an unpushed commit is not read as a forgotten one. Intermediate commits accumulate locally. A pull request and rewriting history — on an explicit request. The one who holds the task commits it; where a project separates the writer from the committer, the project names it.

**A commit carries what it stands on.** An artifact the message names is in the commit, or the message states the ground itself: `tmp/` is not carried, and a ledger there is gone by the time the message is read.

## In DeepSeek Harness

Only in DeepSeek Harness: in another environment, skip this section whole.

- **Work with other agents here goes through the add-on `dsh-agent-team`.** Read it before the first team action: the board and its revisions, the refusal codes and the ceilings live there and not in this file, and a compaction does not bring them back.
- **A pass over a project's scaffolding goes through the procedure `dsh-sweep`** — loaded by name before the first area is cut; its subject and its shape are in it.
- **The lead does not stand watch, and `wait_agent` is not a tool of this project.** A member's report arrives as a message and starts the next turn by itself, so nothing is gained by waiting for it. A lead with nothing to write does, in this order: writes the next thing it owes — a status to the user, the picture, the backlog, the ledger, the next brief; sends a member the question it is holding (a message starts or resumes a turn); or says in one line that it is idle until a report arrives, and ends the turn. The single exception is narrow: the platform requires the lead to have its members' results before a final answer, so when the user's question can only be settled by a member still running, one wait is taken with the shortest useful ceiling and its reason named in the same message. **The harness's own prompt offers `wait_agent` as the move of a blocked lead; that prompt is not this project's law.** A prohibition that names no substitute loses to a tool that is one call away, which is why the substitute stands in the same sentence.

## Spec

A spec is the contract of one task: SPEC.md in the root, living exactly for the duration of the task. Parallel tasks in one tree are separated by write zones: one area — one executor. A separate working copy is taken when the work goes outside the shared tree — another machine, a separate clone. It is written for an agent: it holds context between sessions and is handed to subagents, and replaces the planning mode — the scaffolding is kept in the project, not borrowed from the environment. By the start of the work everything needed is collected in it, including the non-obvious; what is missing is clarified with the user. The file is self-sufficient for someone who has not seen the discussion.

A spec matches the size of the task: a large one (a rework or new logic, several modules, new entities, data, integrations, a change of someone else's behaviour) — with a spec; a local edit and an unambiguous trifle — without: an agreed paragraph suffices. Doubt about the size goes to the questions.

Implementation only by an approved spec; the status in the header moves together with the fact. It is committed together with the task; after acceptance the project part moves into PROJECT.md and the file is deleted; for an abandoned task the file is deleted at once.

The frame has two parts.

The user part is the only one that goes into the chat. "What changes" — what the user will see and feel: a shift in the order of work, capabilities gone and appeared. "Risks" — one line per risk: the measure, what it consists of, whether it is reversible; the rollback is part of the risk. Short and to the point: technical implementation, retelling of decisions and credit-spend estimates do not go here. The user does not open the spec — the essence itself goes into the chat, and approval follows it; in the file these sections are kept for completeness.

```markdown
# SPEC — <task name>
Status: draft | approved <date> | handed over

## What changes
## Risks
```

The rest is the contract of the executor, read in full:

```markdown
## Context
## Requirements
## Solution
## Steps
## Acceptance criteria
## Out of scope
```

**Completeness checklist** — collect as much as possible, including what the user has not thought about; what is unknown goes to the questions: scenarios and the user; edges and failures (empty/many, no rights, an integration down, a repeated request); data and constraints; live steps (what goes into the live environment and who performs it); consequences and risks; acceptance criteria — verifiable; what is out of scope.

**The user approves and accepts.** The author does not accept their own work: "done" is said by the acceptance criterion, verified by a run, not by the author. What is accepted is the merged result, not the reports alone.

Technical conventions of the project live in PROJECT.md: stack, storage, patterns. When building a spec — check against the picture: propose what fits and name the reason; a deviation is voiced, the default is not applied silently.

## Solution invariants

They hold on any stack. A violation is a defect, not a "style": it is fixed, not worked around.

**Do not mute, do not substitute.** If it does not work, that is visible: the error goes outward — a log, a status. No "just in case" fallbacks and no stubs instead of a result: better to fall than to work wrongly in silence. Silent degradation turns an explicit failure into a hidden bug. The check stands where the entity appears, not where it leaves: a guard at the exit mutes an already assembled defect.

**Debug by a run, not by an edit.** A hypothesis is checked by a reproducible run — in a transaction with a rollback or on a copy of the data — and not by a one-off edit of live state: a run is repeatable, live data stays intact.

**One instrument per comparison.** A before-and-after pair is valid only when one instrument took both sides; a tool changed between them makes the pair a reading about the tool, and a comparison whose instrument is unknown is not taken.

**A plant proves reach.** A plant that silently fails to land is worse than none — its clean result is read as proof of a change it never touched. What is refused is the proof by absence: "nothing moved, therefore the change is safe" is not a proof.

**A plant lives in the run's own copy.** Where the artifact under test is copied before it is served, the plant goes into the copy, between the copy and the boot: no shared tree is frozen, no other run can see it, and a plant that does not land is refused and named.

## Form

**Explicit joints.** A module talks to its neighbour through an explicit entry — a function, an interface — and does not dig into its internals; the form of the joint is a question of the task.

**One owner.** Data and knowledge of place have one owner: the rest go through it. A path, a root, a layout live in one place: a copy drifts silently on a move.

**Derived in the same change.** A generated artifact is rebuilt by the same change as its source: the content of the generation is part of the diff, not a separate ritual.

**Simple before complex.** A solution starts simple; if it grows complex, that is a signal to stop and find where to simplify or split instead of piling up. Technique — dependencies, caches, extra layers — comes on proven need.

**Tests by risk, not by ritual.** A test goes where an error is expensive and a regular run cannot see it: complex pure logic, rare edges. Glue and the obvious are checked by a run. Tests do not multiply: each must answer a question that would otherwise stay blind; a test is a check of behaviour, not a number.

## Environment

Secrets live only in `.env`: a file outside git, values never appear in chats, logs or commits. How the environment of the project is obtained and restored is described in PROJECT.md: with the accesses available the agent restores it, otherwise the user.

## Texts

The documents of the project are read by an agent: a cold session must enter the work quickly and not be mistaken. The user reads the conversation; of the documents, the project picture is their door, and a README where the project has one.

- **One language per project.** Neighbouring documents set it; a new document is written in the same one. The snapshot of the kit is a document of the kit: its language does not set the project's.
- **The text is impersonal.** "I", "we", "you" do not appear: the text speaks of its subject. "We decided" ages together with its authors; "it is decided" does not.
- **One subject, one place, one line, one writer.**
- **Nothing that ages is kept.** What ages cannot be kept true, and a kept thing that is not true is worse than its absence: a log, an archive, a chronicle, a report, a copy of a number or of a state, a trace of history — "it used to be so", a commented-out block, "temporarily". History is git, and git is enough: what is done stays there, and the diff carries it. Work in flight is `tmp/`. A document lives only while something updates it, and one without an update loop is not started; the memory of the project is PROJECT.md, and contracts live in the code.
- **Description speaks of the subject, not of its consumers.** It answers "what this is and what it means", not "who uses it and where".
- **Lists are not exhaustive.** A full enumeration ages on the first change; an example suffices.
- **A number lives where it is verified.** A number lives in an artifact checked by a command; other texts speak of it in words. An unverified number lies silently. A number whose artifact was a reading has no home left when the reading goes: it moves into the picture or into the code, or it is not written.
- **A paragraph is one line.** A break inside a sentence hides the phrase from a search, and nothing reads it otherwise; where such breaks already stand, they go as the document is touched.
- **Documents are not started.** The project keeps the picture, the backlog, a spec for the duration of its task and a README where one exists; the kit keeps this file, its procedures and its own README. Everything else a session learns lives in `tmp/` and is dissolved there, and what survives is the conclusion — lifted into the picture or into the code, where the knowledge is fixed. A document says what it is, why it exists and why it stays; one that cannot answer this is worth neither its place nor the reading. A document the user asks for is an exception and is named as his request.
- **No references.** A document speaks of its subject, not of where a foreign thing lies: a reader is not sent elsewhere to understand what stands here. A place of the work's own may be named — the work's own place is knowledge a reader may be given — but no reader is required to walk to it. A reference is an exception named in the report, not a style.
- **A document names its owner when the work that made it closes** — the name stands in the document or beside it; an ownerless document is handed on.

## What is not done

- **Temporary only in `tmp/` and in its own folder.** Drafts, runs and experiments live in `tmp/<slug>/` — one work, one folder: a task, a session or an experiment; the name says what is inside. Cleanup comes down to deleting the folder; nothing temporary stays in the code; `tmp/` is in `.gitignore` (not there — add it).
- **Prose in the code.** A comment or a docstring is the non-derivable "why", an invariant or a boundary of a decision, not a retelling of the code. Test: delete the phrase — would the next session make a wrong decision? No — the phrase is extra.
- **No address in the code.** A comment names no document, no path and no line, not even in passing: code carries the facts of its own place — an invariant, a boundary, the price of a decision — and never a pointer to where something is written down. A comment that says where to read instead of what holds is a defect, and a check may fail the run on one.

## Experimental rules

In full force, like the main ones. Friction or benefit noticed — say it in the conversation.

**Handing work over**

- **A brief before the work:** the subject and where it lives, named as the executor will see it; the acceptance criterion with what confirms it; what the work stands on — in the brief or in a file it names.
- **A brief for anything a reader will look at carries measured values.** The sizes, the fills, the separator, the rule behind a number — taken from the source of what is being copied before the code is written. An adjective ("like the host's", "as in the neighbouring screen") leaves nothing to draw from and nothing to check against, and settles only by a rework.
- **One brief — one subject.** What is noticed nearby does not become a second task in the same brief: it goes back in words to whoever handed the work over.
- **A subject returns to whoever did it** while that one is still there; when it is gone, the subject is rebuilt from the files left for it, not from memory.
- **A milestone is named in the brief, and not fitting inside it means a report and a stop:** a silent long run is indistinguishable from a slow executor.
- **Work that is no longer needed is stopped and closed with a reason** by whoever handed it over: a silent stop leaves no record for whoever reads the history after.
- **One voice to the user.** Reports go to whoever handed the work over, not to the user; that one names the state — what is in work, who does what, what waits for a decision.

**Notes**

- **`NOTES.md` is the backlog of what is not done now** — noticed in passing and deliberately put off rather than forgotten: an improvement, a debt, a doubt. Whoever notices one names it and proposes: done now, written down for later, or dropped; taking it silently into the current work is not one of the three. An item is one subject: what is to be done, why it is put off, what confirms it, when it was written — the fact as it was noticed, not retold.
- **The file is read, not worked on.** Nothing is taken up from it unless it is handed to someone: a suspicion about an item costs a glance and, if it holds, a question or a proposal to whoever decides — not a detour into the work.
- **An item is deleted by whoever sees that it no longer holds** — done, dropped by a decision, or outdated — in the same pass, and the closure is named where that work is reported. A backlog is not a log: nothing closed stays in the file, and an empty one is the goal. Age alone closes nothing.

---

Kit: https://github.com/Vensus137/Coreness-Kit.

The kit is `AGENTS.md` and the folder `skills/` from the kit's repository. The file goes into the project, the skills into the user's home directory (for example `~/.dsh/skills`); where a project has its own place for the skills, that is the one used. A fresh kit is taken from the repository, not from a copy on disk; the file and the skills are updated together.

Rules are taken as a complete snapshot. Pulling a fresh one — first show what will change, then replace.

Version: 1.21 (2026-10-10)
