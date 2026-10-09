---
name: dsh-agent-team
description: "Team mode in DeepSeek Harness: the card board and its revisions, the refusal codes, the roster ceiling, what waiting means in this environment, and that `wait_agent` is not a tool of the project — the lead writes the next thing it owes, sends the question it is holding, or says in one line that the turn is idle until a report arrives. English triggers: agent team, team mode, task board, teammates, delegate."
---

# Team mode in DeepSeek Harness

**Only what exists here.** This procedure carries the environment: the tools, the board, the refusals, the ceilings — what exists in this mode and nowhere else.

**A procedure, not the platform.** It is read when the team is touched, and every line of it describes this mode only. The platform's own text and the tool schemas arrive in every request; this file carries what they do not say — the discipline of the board, the refusals, the ceilings, the two modes.

**Where this does not apply.** An ordinary dialogue and other environments are not this mode: there the work is handed over by that environment's own means. The two are not mixed — with the team bundle on, the ordinary `subagent` and `subagent_fork` doors are turned off, and the rules of one mode would name tools the other does not have.

**The mode is experimental,** like the platform packages it stands on: it is run by observation, and friction and benefit are named in the conversation.

**Who and when.** For the lead — the one who talks to the user. The moment: the team bundle is on, and the work is bigger than one action.

## The lead's own hands

- **Everything else is a card, however small it looks.** The picture, the backlog, the commit and the acceptance are the lead's; so is a repair in one file that needs no tree read, no probe and no second file, when it unblocks the lead's own commit.

## Tools

- **The set.** `spawn_teammate(name, description, prompt, context)` — `context: "fresh"` (default) or `"fork"`; `send_message(target, message)`; `team_task_create` / `_get` / `_list` / `_update` (the transition, with the current `expected_revision`); `list_agents`; `wait_agent`; `interrupt_agent`. Their schemas arrive in every request; the discipline stands below.

## The board

- **A stale revision is refused** (`TEAM_TASK_STALE_REVISION`): take the fresh revision, see what changed, repeat. The check is there to notice someone else's change, not for protection.
- **A card no longer needed leaves the board** (`delete`, by its owner or by the lead); only a card that still blocks another is refused (`TEAM_TASK_HAS_DEPENDENTS`). A tombstone stays in the log — out of the list and out of the count, still readable by its id, and only a change to it is refused — and, unlike the roster, it gives room back: it takes no `maxTasks`.
- **A cancelled card is closed by the lead with the reason in words:** interrupting a member is silent and leaves no record of why.
- **Parallel cards get separate working copies** (`git worktree add`); in a shared tree a commit names its paths (`git commit -- <paths>`). **An executor does not commit — the lead commits by paths** — so a card's files reach history only through the lead, and that is also where its cost is read. **An overlap is warned about and never refused** (`warnings`): keeping one zone to one writer is the lead's discipline, not the platform's.

## What a card costs

- **One reading, one tool:** a reader written for a card is designed before it is written, and prints every field the decision needs.

## Waiting and reporting

**`wait_agent` is not a tool of this project.** The platform's own prompt offers it as the move of a blocked lead, and the same prompt requires the lead to have its members' results before a final answer; that prompt is not the project's law, and the difference is the project's. What stands instead, in this order: write the next thing owed — a status to the user, the picture, the backlog, the ledger, the next brief; `send_message` the question being held, since a message starts or resumes a member's turn; or say in one line that the turn is idle until a report arrives. A prohibition that names no substitute loses to a tool that is one call away.

- **A report is a message, and a message starts the lead's next turn by itself** — nothing needs standing watch, and a lead standing in the conversation never waits.
- **The one narrow exception:** the user asks for an answer that only a member still running can settle. Then one `wait_agent` with the shortest useful ceiling, its reason named to the user in the same turn, and the board re-listed after it returns or times out.
- Waiting wakes on any team change — a status, a task update, an incoming message — and only a message carries a report. `inactive` means no turn is executing, not a task result: a required member that is inactive without a report is woken by a message, not waited for, and `wait_agent` answers `noProgress` when nobody is running.
- **Reporting is the executor's duty:** there is no separate "work finished" notice, and a report, being a message, starts the lead's next turn without anyone standing watch.

## The roster

- **A card goes to the member holding its subject; a fresh member earns its entry only where none can take it without judging its own work.**
- **No place comes back:** every creation counts for the life of the session, failed ones too, and the name is spent with it. The next is refused with `TEAM_MEMBER_LIMIT` ("Team member limit <n> reached").
- **The ceiling** is `maxMembers` in the team row's `config` — sixteen in the platform's code, and in an environment whatever its profile's patch declares. It is raised from that patch by an `id`-targeted entry that restates the **whole** `config`, since it is replaced and not merged (`maxMembers`, `maxTasks`, `maxPendingMessagesPerMember`, `maxMessageBytes`, `disposalTimeoutMs`); a restart applies it.
- A member that has exhausted its context is not revived: its subject moves to another member, and everything found on the way stays on disk for whoever takes the subject up.
- A spent roster and a changed subject are the two reasons to start a new session: a new session begins with an empty roster and an empty board, and nothing migrates between sessions.

## Refusals

Examples, not the whole list: `TEAM_TASK_STALE_REVISION`, `TEAM_TASK_ALREADY_CLAIMED`, `TEAM_TASK_BLOCKED`, `TEAM_TASK_UNAUTHORIZED` (a card is changed by its owner or by the lead), `TEAM_TASK_HAS_DEPENDENTS`, `TEAM_TASK_DELETED`, `TEAM_TASK_NOT_FOUND`, `TEAM_TASK_LIMIT`, `TEAM_LEAD_REQUIRED`, `TEAM_MEMBER_LIMIT`. A refusal is read and acted on, never muted: take the fresh state and repeat the step. An edit to a file changed since the last read is refused the same way: re-read, see what changed, repeat. The check, like the board's, is there to notice someone else's change.

## Facts of this environment

Observations about the harness, kept as reference rather than as rules: no check enforces them, and they age with the platform.

- **A member's road is its own.** A selection belongs to a session, and the default row only starts fresh ones: a member is created on whatever provider and model the session stands on at that moment and keeps them for its life. Work that must ride a new road needs a member created after the switch.
