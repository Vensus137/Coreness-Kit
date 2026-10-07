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
  Therefore **reporting is the executor's duty**, not something that happens by itself — and a report,
  being a message, starts the lead's next turn without anyone standing watch.
- **The lead accepts on reports; he does not wait for them.** The platform's own collaboration policy says
  the lead must have the needed reports before the final answer, and this mode reads that sentence as
  **acceptance**, not as leave to block a turn: a result is not claimed without its reports, while the
  dialogue goes on — the lead answers, sets the next card, gives status, and is woken by the report when it
  arrives. Standing still over a report that is already on its way buys nothing and costs the conversation,
  which is the one thing the mode exists to keep. Waiting is left for the case where the user's own answer
  *is* the report; then it is named as what it is and not passed off as work.
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
   and a conversation with them costs steps. The roster never gives a place back: every creation is counted
   for the life of the session — failed ones too, and the name is spent with it — and the next is refused
   with `Team member limit <n> reached`. The ceiling is a config field of the team's own row — sixteen by
   default in the platform's code, and in an environment whatever its profile's patch declares. It is raised
   from that patch by an `id`-targeted entry that restates the **whole** `config`, since it is replaced and
   not merged (`maxMembers`, `maxTasks`, `maxPendingMessagesPerMember`, `maxMessageBytes`,
   `disposalTimeoutMs`); an application restart applies it. A member that has
   exhausted its context is not revived: its subject moves to another member, and everything found on the
   way — notes, helpers — stays on disk, where whoever takes the subject up reads it. A spent roster and a
   subject that has changed are the two reasons to start a new session: a new session begins with an empty
   roster and an empty board, while the old team stays whole inside its own session log, and nothing
   migrates from one session to another.
9. **A card revision is a mechanical check.** An edit without a current revision is rejected with a
   refusal; on seeing it — take the fresh revision, check what changed and repeat. The discipline is
   needed not for protection but to notice someone else's change.
10. **A file is edited after a fresh read.** The tool refuses if the file changed since the read; the
    refusal is not muted: the file is re-read and the edit repeated.
11. **The board has a bottom.** A card that is no longer needed leaves the board: `delete` is implemented
    and is called by the card's owner or by the lead; only a card that still blocks another one is refused
    (`TEAM_TASK_HAS_DEPENDENTS`). What stays in the log is a tombstone, not a card: out of the list, out of
    the count, and unaddressable afterwards. The board's own ceiling is a count of cards that are not
    deleted, and unlike the roster it gives room back.
12. **A card for anything a reader will look at carries measured values.** The sizes, the fills, the
    separator, the rule behind a number — taken from the source of what is being copied before the code is
    written. An adjective ("like the host's", "as in the neighbouring screen") leaves the executor unable
    both to draw it and to check it, and settles only by a rework; measured values let them do both.
13. **Cards that run at the same time get separate working copies** (`git worktree add`): one tree with two
    executors has one index and one set of write zones, and a commit takes what a neighbour left staged. One
    zone — one writer stays the rule; the working copy is what makes parallel work real. In a shared tree a
    commit names its paths (`git commit -- <paths>`).

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
