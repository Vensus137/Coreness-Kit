---
name: dsh-skills
description: "How a procedure is added in DeepSeek Harness: file skills from the user, project or shared roots, and environment skills registered by a layer. Covers the roots and their ranks, the profile row that turns file discovery on, which door to choose, and how to check that a procedure has arrived. English triggers: dsh skills, add skill, skill roots, environment skill."
---

# Procedures in DeepSeek Harness

A procedure reaches agents by one of two doors: a file in a scanned root, or a registration by a layer.

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

## Environment skills

A procedure that must live and die together with the environment is registered by code: the body lives in a module of the layer, the layer declares the service it needs (`inject: ['skills']`), the registration is `ctx.skills.register(...)` on load of the layer. The price is a restart, and the procedure disappears together with the layer without leaving anything in someone else's files. This is how `coreness-map` and `coreness-health` live.

## Which door to choose

- Needed in every project of the machine, no repository involved — a file in `<dsh home>/skills`.
- Needed by one repository — a file in `<project>/.dsh/skills`, or in `.agents/skills` when the procedure is shared with other agents.
- Part of the environment, must go away with it — a registration by the layer.

## The check

Ask the session catalogue, or call the procedure by name: it is named, it loads, and its base directory points at the root it came from. For a layer procedure the provider shows as `runtime`.

## What not to do

- Do not assume a file has arrived without asking the catalogue: a file in a root that is not scanned is a silent substitution.
- Do not keep the same procedure in two doors at once: the text gets one owner.
