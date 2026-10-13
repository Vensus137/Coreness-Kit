# Coreness Kit

Work conventions an agent follows, kept as a kit: the rules themselves and the procedures for special
cases. Taken into a project as a snapshot, in full.

## What is inside

- `AGENTS.md` — the rules of work: how a task is set up and accepted, how texts and checks are treated,
  what is not done.
- `skills/` — procedures for special cases. Each one says in its own description when it applies and in
  which environments it works.
- `AGENTS.ru.md`, and `SKILL.ru.md` beside each procedure — the same texts in Russian.
- `LICENSE` — MIT.

## How it is used

A project keeps a snapshot of the kit: the file `AGENTS.md` and, under `skills/`, the English text of each
procedure — `<name>/SKILL.md`. The Russian counterparts, `AGENTS.ru.md` and `SKILL.ru.md`, are the canon's
own: the kit is worked on in that language, and both texts of a pair move in one change. Where the
environment carries the procedures itself, the snapshot is the file `AGENTS.md`, and the procedures live
with the environment at the same revision. The address of the kit and the version of the snapshot are in
the tail of `AGENTS.md`. A fresh snapshot replaces the previous one in full, and what will change is shown
before the replacement.

This repository is the canon. A fix made in a project is brought back here in the same pass, so that the
next snapshot does not overwrite it. Local specifics of a project never live here: they belong to the
`PROJECT.md` of that project.

A change to the law or to a procedure goes through the door of any other work: a spec, the diff shown to
the owner, and the challenge before the edit; a word of the owner's is the ground of a proposal, never of
a landing. The version moves with the change the commit carries.

## Where it applies

The rules are written to hold on any stack. Rules that concern one platform live in the procedure that
serves it and not in the law: the procedures specific to DeepSeek Harness say so in their own
descriptions, and the rest apply anywhere.

## Version

The current version is a line at the end of `AGENTS.md`; it moves with the change that alters the rules.
