---
name: dsh-agent-team
description: "Team mode in DeepSeek Harness: the tools a lead drives here — spawn_teammate, send_message, wait_agent, list_agents, team_task_update, interrupt_agent — the card board and its revisions, the refusal codes, the roster ceiling, and what waiting means in this environment. English triggers: agent team, team mode, task board, teammates, delegate."
---

# Team mode in DeepSeek Harness

**Only what exists here.** This procedure carries the environment: the tools, the board, the refusals, the ceilings — what exists in this mode and nowhere else.

**A procedure, not the platform.** It is read when the team is touched, and every line of it describes this mode only. The platform's own text and the tool schemas arrive in every request; this file carries what they do not say — the discipline of the board, the refusals, the ceilings, the two modes.

**Where this does not apply.** An ordinary dialogue and other environments are not this mode: there the work is handed over by that environment's own means. The two are not mixed — with the team bundle on, the ordinary `subagent` and `subagent_fork` doors are turned off, and the rules of one mode would name tools the other does not have.

**The mode is experimental,** like the platform packages it stands on: it is run by observation, and friction and benefit are named in the conversation.

**Who and when.** For the lead — the one who talks to the user. The moment: the team bundle is on, and the work is bigger than one action.

## Tools

- `spawn_teammate(name, description, prompt, context)` — a member; the brief is its `prompt`. `context: "fresh" | "fork"` — `fresh`, the default, starts without this conversation; `fork` inherits the completed turns of the lead.
- `team_task_create` / `_get` / `_list` / `_update` — the board; `_update` carries the transition (`claim`, `release`, `edit`, `set_dependencies`, `complete`, `reopen`, `reassign`, `delete`) with the current `expected_revision`. A card carries the brief, the write zones and the acceptance criterion.
- `send_message(target, message)` — mail; a member's report goes to `lead`. `list_agents` — the roster and who is running; `wait_agent` — the next team change (from ten seconds through one hour, thirty by default); `interrupt_agent` — stop a member's current turn.
- **An overlap is warned about and never refused** (`warnings`): keeping one zone to one writer is the lead's discipline, not the platform's.

## The board

- **A stale revision is refused** (`TEAM_TASK_STALE_REVISION`): take the fresh revision, see what changed, repeat. The check is there to notice someone else's change, not for protection.
- **A card no longer needed leaves the board** (`delete`, by its owner or by the lead); only a card that still blocks another is refused (`TEAM_TASK_HAS_DEPENDENTS`). A tombstone stays in the log — out of the list and out of the count, still readable by its id, and only a change to it is refused — and, unlike the roster, it gives room back: it takes no `maxTasks`.
- **A cancelled card is closed by the lead with the reason in words:** interrupting a member is silent and leaves no record of why.
- **Parallel cards get separate working copies** (`git worktree add`); in a shared tree a commit names its paths (`git commit -- <paths>`).

## A challenge round

A round is a refuter turned on lines that are about to become irreversible — a version number, a law line, a picture paragraph — not a sweep over everything just written. Words are not taken as truth (`AGENTS.md`, "Challenge is the norm"); what is added here is the price.

- **The brief names** the artifact and its revision (a commit or a version, not "the file"), the decisions to answer, what acceptance means, the boundary — its own file only — and the budget. The card carries them, as every card does.
- **A verdict is one line:** `<claim> — confirmed | refuted | unclear — <file:line> — <what changes, who applies>`. A verdict that cannot name its source says `unclear`; a confirmation is not written at all.
- **The report is no longer than the text it checks.** The failure mode is prose: verdicts that confirm lines which do not change still cost their bytes, and the report is measured by its length, not by the number of its verdicts.
- **It is not spent** where a command answers — a duplicate, a stale address, a version — nor on one line of text, nor while the verdicts of an earlier round lie unapplied.
- **One refuter, not a second round:** a round over the previous round's verdicts is not scheduled; a second refuter is taken where the text is expensive to undo, and not earlier.
- **The text's owner applies the verdicts in the same pass** — the lead, for the law; a challenger owns no line of it. A verdict nobody applied is named where the work is reported, and if it is put off it is a note with a holder.

## Waiting and reporting

- Waiting wakes on any team change — a status, a task update, an incoming message — and only a message carries a report. `inactive` means no turn is executing, not a task result: a required member that is inactive without a report is woken by a message, not waited for, and `wait_agent` answers `noProgress` when nobody is running.
- **Reporting is the executor's duty:** there is no separate "work finished" notice, and a report, being a message, starts the lead's next turn without anyone standing watch. Waiting is left for the case where the user's own answer is the report, and is named as what it is.

## The roster

- **Members are created for the work** — a living member costs attention, and a conversation with them costs steps.
- **No place comes back:** every creation counts for the life of the session, failed ones too, and the name is spent with it. The next is refused with `TEAM_MEMBER_LIMIT` ("Team member limit <n> reached").
- **The ceiling** is `maxMembers` in the team row's `config` — sixteen in the platform's code, and in an environment whatever its profile's patch declares. It is raised from that patch by an `id`-targeted entry that restates the **whole** `config`, since it is replaced and not merged (`maxMembers`, `maxTasks`, `maxPendingMessagesPerMember`, `maxMessageBytes`, `disposalTimeoutMs`); a restart applies it.
- A member that has exhausted its context is not revived: its subject moves to another member, and everything found on the way stays on disk for whoever takes the subject up.
- A spent roster and a changed subject are the two reasons to start a new session: a new session begins with an empty roster and an empty board, and nothing migrates between sessions.

## Refusals

Examples, not the whole list: `TEAM_TASK_STALE_REVISION`, `TEAM_TASK_ALREADY_CLAIMED`, `TEAM_TASK_BLOCKED`, `TEAM_TASK_UNAUTHORIZED` (a card is changed by its owner or by the lead), `TEAM_TASK_HAS_DEPENDENTS`, `TEAM_TASK_DELETED`, `TEAM_TASK_NOT_FOUND`, `TEAM_TASK_LIMIT`, `TEAM_LEAD_REQUIRED`, `TEAM_MEMBER_LIMIT`. A refusal is read and acted on, never muted: take the fresh state and repeat the step.

## Facts of this environment

Observations about the harness, kept as reference rather than as rules: no check enforces them, and they age with the platform.

- **A member's road is its own.** A selection belongs to a session, and the default row only starts fresh ones: a member is created on whatever provider and model the session stands on at that moment and keeps them for its life. Work that must ride a new road needs a member created after the switch.
