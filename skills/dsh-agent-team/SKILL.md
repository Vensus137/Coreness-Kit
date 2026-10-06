---
name: dsh-agent-team
description: "Team mode in DeepSeek Harness: how the lead sets and accepts work when the team bundle is enabled — a task board, cards with write zones, mail to members, waiting — and stays in the conversation with the user while executors work. This environment only: it does not apply in an ordinary dialogue or in other environments. The skill is experimental — friction and benefit go into the conversation. English triggers: agent team, team mode, task board, teammates, delegate."
---

# Team mode (DeepSeek Harness)

**Scope — this environment only.** The skill rests on tools that exist nowhere else: a task board with
card revisions, cards with write zones, mail to members, waiting. In an ordinary dialogue and in other
environments it does not apply: there the task is handed to a subagent by the ordinary conventions, and
mixing the two modes is not allowed — the rules would refer to tools that are not there.

**The skill is experimental.** The mode is young: it is run by observation and edited actively. No
separate reflection is started for it — friction and benefit go into the conversation, and `reflection`
looks at the findings.

## Who and when

For the lead — the one who talks to the user. The moment: the team bundle is enabled and there is more
work than one action. Small things the lead does alone: delegation has its own price — a brief, waiting,
acceptance.

Together with the bundle comes what the ordinary mode lacks: a board with card revisions, mail to any
member, waiting, and named members instead of nameless subagents.

## The lead stays in the conversation

That is the point of the mode: while executors work, the lead **does not drop out of the dialogue** —
clarifies, decides, sets the next thing, gives status. The user must be able to talk to the lead at any
moment rather than wait for the work to end.

- **Waiting is not a turn of work.** It stops the conversation until the first event, and an event
  arrives only when a member sends a message: the platform has no separate "work finished" notification.
  Therefore **reporting is the executor's duty**, not something that happens by itself.
- **Wait when the work cannot be finished without it.** Before the final answer to the user the lead must
  have the reports of the members that are needed: without them the work is not accepted. Inside the work
  waiting is not needed — the board, an answer to the user, the next card and acceptance take its place.
- **Work may become unnecessary while it runs.** The conversation is a source of edits too: if after a
  review the task turns out to be superfluous, the executor is stopped and the card is closed with the
  words "cancelled: reason". Waiting for a result only to throw it away is a loss of steps. Stopping a
  member tells the lead nothing: the cancellation is fixed by the lead — with a card and a record.
- **Status is the lead's:** what is in work, who is doing what, what awaits the user's decision. The lead
  is also the only one who talks to the user: an executor reports to the lead, not to the user.

## How a task is run

1. **A card before the work.** It holds the subject and the place, the acceptance criterion, the write
   zones, the evidence. After "done" a card means nothing: there is nothing to check against. The spec of
   the task is the contract of the lead and the user; the card is the executor's brief for one part of it
   and does not replace the spec.
2. **One subject per card.** Something noticed nearby goes into the report in words, not as a second task
   in the same brief: gluing subjects together gives a long run and no report until the end.
3. **The brief goes into the task in full.** The executor does not see the lead's conversation with the
   user. The fields of the brief come from the conventions; what matters here is that the brief travels
   as a task and is not retold along the way.
4. **Paths from the root of the project.** The working directory is shared by the members, so "where it
   was before" and relative landmarks do not work in a brief.
5. **One zone per executor.** Two people on a folder or a plugin are not started: the edits would collide,
   and sorting out a collision costs more than doing the work in sequence.
6. **The executor stays alive.** The next step of the same subject goes to the same executor: they have
   the context, and a new agent is more expensive. A new one is taken when the subject is different or a
   fresh view is needed.
7. **A milestone is named in the brief.** Not fitting into it means an intermediate report and a stop: a
   silent long run is indistinguishable from a slow executor.
8. **Members are created for the work.** "For the future" in advance — no: a living member costs attention,
   and a conversation with them costs steps.
9. **A card revision is a mechanical check.** An edit without a current revision is rejected with a
   refusal; on seeing it — take the fresh revision, check what changed and repeat. The discipline is
   needed not for protection but to notice someone else's change.
10. **A file is edited after a fresh read.** The tool refuses if the file changed since the read; the
    refusal is not muted: the file is re-read and the edit repeated.

## How work is accepted

- **Report by evidence** — from the conventions: what was done, what confirms it, what the check did not
  show, where the work stopped.
- The lead looks at the **named output**, not at the whole work re-read. Doubt is a reason to look at the
  diff and run a check, not to read everything in a row.
- **Rework returns to the same executor:** they have the context, and a repeated brief costs more than the
  edit.
- **A card is closed with evidence.** Work without evidence is not closed, even if it is done.

## What the mode does not change

The role of the lead, the brief, the report by evidence, acceptance, records, "a dead end is a report",
checks by the size of the change — all of it comes from the conventions. The skill does not repeat them:
it adds only what arrives together with the bundle.
