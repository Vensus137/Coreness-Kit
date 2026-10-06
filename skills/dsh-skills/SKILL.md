---
name: dsh-skills
description: "How a procedure is added in DeepSeek Harness: the roots a session scans for file procedures, their ranks, the row that turns the file door on, which root to choose, and how to check that a procedure has arrived. English triggers: dsh skills, add skill, skill roots, install a skill."
---

# Procedures in DeepSeek Harness

A procedure reaches agents by one of two doors: a file in a scanned root, or a registration by a plugin. The first is the door of this kit; the second belongs to the platform's own delivery and is named here only so that it is not confused with the first.

## File skills

The provider `@deepseek-ai/dsh-skill-filesystem` scans four roots in rank order:

| Rank | Root | Source |
| --- | --- | --- |
| 100 | `<project>/.dsh/skills` | `project-dsh` |
| 200 | `<project>/.agents/skills` | `project-agents` |
| 400 | `<dsh home>/skills` | `user-dsh` |
| 500 | `~/.agents/skills` | `user-agents` |

A procedure is a folder `<name>/SKILL.md` or a flat file `<name>.md` at the top of a root; nested `**/SKILL.md` are deliberately not discovered. The project root is the nearest ancestor holding `.git`; the user DSH root skips its `.system` child. The provider watches the roots, so a new, renamed or deleted procedure reaches the next catalogue without a restart.

**The door has to be open.** The web-surface bundle turns the host row of this provider off — «presets own local discovery» — and then a session sees only what a layer registers. The row is turned back on from the profile patch:

```yaml
- id: skill-filesystem
  disabled: false
```

After one restart the roots work for every project of the profile. Verified in the workshop profile: without the row the files stay invisible to the session, with it `reflection` loads from `<dsh home>/skills`.

## Procedures inside a package

The platform carries procedures of its own inside packages: a row points the provider's `customSkillDirs` at a folder of the package, and a package can also register a procedure by code on load of its layer. Both doors exist, both are the platform's own, and a product may need them for its own delivery. This kit does not use either: its procedures are files in a root the environment scans, and a body in code is a procedure whose text no one edits as text. A folder in the root of a repository is not a door at all.

## Which door to choose

- Needed in every project of the machine, no repository involved — a file in `<dsh home>/skills`.
- Needed by one repository — a file in `<project>/.dsh/skills`, or in `.agents/skills` when the procedure is shared with other agents.

## The check

Ask the session catalogue, or call the procedure by name: it is named, it loads, and its base directory points at the root it came from.

## What not to do

- Do not assume a file has arrived without asking the catalogue: a file in a root that is not scanned is a silent substitution.
- Do not keep the same procedure in two doors at once: the text gets one owner.
