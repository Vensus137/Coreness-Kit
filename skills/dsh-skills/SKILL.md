---
name: dsh-skills
description: "How a procedure is added in DeepSeek Harness: the short road — copy into a scanned root and call by name; the roots a session scans for file procedures, their ranks; the row that turns the file door on only when no mounted layer provides it; which root to choose; how to check that a procedure has arrived; and where a rule — as opposed to a procedure — must live so that a compaction does not lose it. English triggers: dsh skills, add skill, skill roots, install a skill."
---

# Procedures in DeepSeek Harness

A procedure reaches agents by one of two doors: a file in a scanned root, or a registration by a plugin. The first is the door of this kit; the second belongs to the platform's own delivery and is named here only so that it is not confused with the first.

## File skills

**The short road.** Put `<name>/SKILL.md` (or `<name>.md`) at the top of a scanned root and call the procedure by name. The provider watches the roots, so a new file is live without a restart. If the name loads and its base directory is the root you chose, the door is open; stop there. The profile patch below is needed only when the name does not load because no mounted layer provides `skill-filesystem`.

The provider `@deepseek-ai/dsh-skill-filesystem` scans four roots in rank order, and two more exist when a row configures them:

| Rank | Root | Source |
| --- | --- | --- |
| 100 | `<project>/.dsh/skills` | `project-dsh` |
| 200 | `<project>/.agents/skills` | `project-agents` |
| 300 | the folders a row names | `customSkillDirs` |
| 400 | `<dsh home>/skills` | `user-dsh` |
| 500 | `~/.agents/skills` | `user-agents` |
| 600 | a folder shipped inside a package | `bundledSkillDir` |

A procedure is a folder `<name>/SKILL.md` or a flat file `<name>.md` at the top of a root; nested `**/SKILL.md` are deliberately not discovered. The project root is the nearest ancestor holding `.git`; the user DSH root skips its `.system` child. The provider watches the roots, so a new, renamed or deleted procedure reaches the next catalogue without a restart.

**The door.** The web-surface bundle turns the **host** row of this provider off — «presets own local discovery» — so a session sees only what a mounted layer provides. A preset may mount its own `skill-filesystem`; when it does, the host row being off does not by itself close the door — the preset's provider answers for the roots it configures. Check by calling the procedure by name before patching: if it loads and its base directory is the chosen root, the door is open. Only when no mounted layer provides `skill-filesystem` does the profile patch turn the host row back on:

```yaml
- id: skill-filesystem
  disabled: false
```

A patch is read at start: this way needs one restart of the application. A file added to a scanned root does not. The catalogue is the platform's own publication: it may stay away while the pre-step returns the decision unchanged and nothing is logged, so whether it arrives is measured by the name, not assumed.

## Procedures inside a package

The platform carries procedures of its own inside packages: a row points the provider's `customSkillDirs` at a folder of the package, and a package can also register a procedure by code on load of its layer. Both doors exist, both are the platform's own, and a product may need them for its own delivery. This kit does not use either: its procedures are files in a root the environment scans, and a body in code is a procedure whose text no one edits as text. A folder in the root of a repository is not a door at all.

## Which door to choose

- Needed in every project of the machine, or carried by the environment rather than by one repository — a file in `<dsh home>/skills`.
- Needed by one repository — a file in `<project>/.dsh/skills`, or in `.agents/skills` when the procedure is shared with other agents.

## Where a rule must live

A procedure is not a home for a rule. A compaction takes a span of the visible surface out of the model's sight; what re-derives itself after it is the instruction chain, the runtime snapshot and the skill catalogue — a skill's body does not come back, and a body over the pruner's limit is cut in the transaction that writes the checkpoint. So the homes are three: a rule that must be **in force** belongs in a **prompt section**; a rule that must be **re-readable** belongs in an **instruction file** on the session's chain — the project's AGENTS.md; and a **skill carries a procedure, not a rule** — what its reader must **do**, kept under the limit. The limit and the cut are the platform's own numbers, read where they stand.

## The check

Call the procedure by name: it is named, it loads, and its base directory points at the root it came from. The base directory is the proof of the root. A session's catalogue is the platform's to publish, not this provider's, so a name is the door that is always there.

## What not to do

- Do not assume a file has arrived without checking: a file in a root that is not scanned is a silent substitution. The check is the name; the catalogue is the platform's publication and may lag.
- Do not keep the same procedure in two doors at once: the text gets one owner.
- Do not copy both language mirrors of one procedure into the same root: the names collide and one text wins silently.
