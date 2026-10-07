---
name: dsh-agent-team
description: "Team mode in DeepSeek Harness: the tools a lead drives here — spawn_teammate, send_message, wait_agent, list_agents, team_task_update, interrupt_agent — the card board and its revisions, the refusal codes, the roster ceiling, and what waiting means in this environment. English triggers: agent team, team mode, task board, teammates, delegate."
---

# Team mode in DeepSeek Harness

**Only what exists here.** This procedure carries the environment: what the platform itself demands, the tools, the board, the refusals, the ceilings — and the working discipline of this mode.

**A procedure, not the platform.** It is read when the team is touched, and every line of it describes this mode only. The platform's own text and the tool schemas arrive in every request; this file carries what they do not say — the discipline of the board, the refusals, the ceilings, the two modes.

**Where this does not apply.** An ordinary dialogue and other environments are not this mode: there the work is handed over by that environment's own means. The two are not mixed — with the team bundle on, the ordinary `subagent` and `subagent_fork` doors are turned off, and the rules of one mode would name tools the other does not have.

**The mode is experimental,** like the platform packages it stands on: it is run by observation, and friction and benefit are named in the conversation.

**Who and when.** For the lead — the one who talks to the user. The moment: the team bundle is on — an enabled mode is the user's request, and nothing further is asked for — and the work is bigger than one action.

## Handing work over

- **A brief before the work:** the subject and the place, the acceptance criterion, and what confirms it; what the work stands on is in the brief or in a file it names, not in the conversation.
- **One subject — one executor;** what was noticed nearby goes into the report in words, not as a second task in the same brief.
- **One zone — one writer:** two executors are not put on one tree.
- **The same subject returns to the same executor** while its address lives; when the address is gone, the subject is rebuilt from the files left for it, not from memory.
- **A milestone is named,** and not fitting into it means an intermediate report and a stop: a silent long run is indistinguishable from a slow executor.
- **Acceptance is by evidence,** not by the report: work without evidence is not closed even when it is done, and the author does not accept their own work.
- **Work that has become unnecessary is stopped and closed with a reason.**
- **One voice to the user:** the lead names the state — what is in work, who is doing what, what awaits a decision; a member's report goes to the lead.

## Tools

- `spawn_teammate(name, description, prompt, context)` — a member; the brief is its `prompt`. `context: "fresh" | "fork"` — `fresh`, the default, starts without this conversation; `fork` inherits the completed turns of the lead.
- `team_task_create` / `_get` / `_list` / `_update` — the board; `_update` carries the transition (`claim`, `release`, `edit`, `set_dependencies`, `complete`, `reopen`, `reassign`, `delete`) with the current `expected_revision`. A card carries the brief, the write zones and the acceptance criterion.
- `send_message(target, message)` — mail; a member's report goes to `lead`. `list_agents` — the roster and who is running; `wait_agent` — the next team change (from ten seconds through one hour, thirty by default); `interrupt_agent` — stop a member's current turn.
- **Write zones are advisory, not a lock:** an overlap with a card already claimed is warned about and never refused — keeping one zone to one writer is the lead's discipline, not the platform's.

## The board

- **A stale revision is refused** (`TEAM_TASK_STALE_REVISION`): take the fresh revision, see what changed, repeat. The check is there to notice someone else's change, not for protection.
- **A card no longer needed leaves the board** (`delete`, by its owner or by the lead); only a card that still blocks another is refused (`TEAM_TASK_HAS_DEPENDENTS`). A tombstone stays in the log — out of the list, unaddressable — and, unlike the roster, it gives room back: it takes no `maxTasks`.
- **A cancelled card is closed by the lead with the reason in words:** interrupting a member is silent and leaves no record of why.
- **Parallel cards get separate working copies** (`git worktree add`); in a shared tree a commit names its paths (`git commit -- <paths>`).

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

Examples, not the whole list: `TEAM_TASK_STALE_REVISION`, `TEAM_TASK_ALREADY_CLAIMED`, `TEAM_TASK_BLOCKED`, `TEAM_TASK_UNAUTHORIZED` (a card is changed by its owner or by the lead), `TEAM_TASK_HAS_DEPENDENTS`, `TEAM_TASK_DELETED`, `TEAM_TASK_NOT_FOUND`, `TEAM_TASK_LIMIT`, `TEAM_LEAD_REQUIRED`, `TEAM_MEMBER_LIMIT`, `FS_STALE_VERSION`. A refusal is read and acted on, never muted: take the fresh state and repeat the step.

## Facts of this environment

Observations about the harness, kept as reference rather than as rules: no check enforces them, and they age with the platform.

- **A member's road is its own.** A selection belongs to a session, and the default row only starts fresh ones: a member is created on whatever provider and model the session stands on at that moment and keeps them for its life. Work that must ride a new road needs a member created after the switch.
