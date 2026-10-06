---
name: dsh-skills
description: "How environment procedures are set up in DeepSeek Harness: the body lives with the layer and is registered by code, while a file layout never reaches the agents. This environment only: it does not apply in an ordinary dialogue or in other environments. Use it when a procedure has to be added, edited or removed. English triggers: dsh skills, register skill, environment skill."
---

# Environment procedures in DeepSeek Harness

In this environment a skill is an effect of the layer, not a file: the plugin registers it on load.

The evidence is a probe in a live session: a skill registered by the conventions layer is visible in the
session catalogue (`coreness-map`), while files that lay in the skill directory of the home are unknown to
the catalogue (`spec`, `reflection`). The reason: the roots of the catalogue are set by presets, and the
file subsystem line is muted by the web-surface bundle.

## Adding

- **The body lives with the layer**, next to the code: the text lives in a module of the layer, as
  `coreness-map` does for the conventions. A file in the skill directory will not make the procedure
  appear.
- **The service is declared**: a layer that needs the registry names it (`inject: ['skills']`); without the
  service the plugin does not come up at all and says so through a platform refusal instead of half the
  work.
- **Registration**: `ctx.skills.register(<procedure>)` on load of the layer. The name is kebab-case: the
  harness registry checks it, so a check of one's own is not needed.
- **An application restart** is the price of a change in the composition: the registration happens on load
  of the layer.
- **The check**: the procedure is named in the session catalogue and can be invoked. In the old house this
  was `skills.test.mjs`.

## Removing

In the same change: drop the registration and the body. Removing the layer takes its procedures away
without traces — they do not remain in anyone else's files.

## Storage

Bodies that arrived with the kit live as the master copy in `skills/` of the repository, and they reach the
layer as a copy — in the same change as the registration: the content of the copy is part of the diff. A
divergence of the copies is caught by comparing an imprint: the old house did this for the environment
block (`npm run block -- --check`).

## What not to do

- Do not put a file into the skill directory and assume the procedure has arrived: a silent substitution.
- Do not duplicate a procedure as a file: the text has one owner — the layer.
- Do not start a skill directory of the environment: the procedures of the environment live with the layer
  and are removed together with it.
