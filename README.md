# Coreness Kit

Work conventions an agent follows, kept as a kit: the rules themselves and the procedures for special
cases. Taken into a project as a snapshot, in full.

## What is inside

- `AGENTS.md` — the rules of work: how a task is set up and accepted, how texts and checks are treated,
  what is not done.
- `skills/` — procedures for special cases. Each one says in its own description when it applies and in
  which environments it works.
- `LICENSE` — MIT.

## How it is used

A project keeps a snapshot of the kit: the file `AGENTS.md` and the folder `skills/`, copied whole. Where
the environment carries the procedures itself, the snapshot is the file `AGENTS.md`, and the procedures
live with the environment at the same revision. The address of the kit and the version of the snapshot are
in the tail of `AGENTS.md`. A fresh snapshot replaces the previous one in full, and what will change is
shown before the replacement.

This repository is the canon. A fix made in a project is brought back here in the same pass, so that the
next snapshot does not overwrite it. Local specifics of a project never live here: they belong to the
`PROJECT.md` of that project.

## Where it applies

The rules are written to hold on any stack. Some procedures are specific to DeepSeek Harness and are
marked as such in their own descriptions; the rest apply anywhere.

## Version

The current version is a line at the end of `AGENTS.md`; it moves with the change that alters the rules.
