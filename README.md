---
project: forge
render: readme-project
generated: 2026-11-08
recipe: recipes/readme-project.md v0.2
inputs:
  - ledger.md
  - 10-intent.md v7.1
---

# Forge of Thought: the design record 7.1

*The intent, the solution design, the decisions and the reviews behind the engine, kept as a project of the engine's own process.*

If you want to use the forge, you need the engine,
https://github.com/pche-broken-artist/forge-of-thought, not this
repository: a user clones the engine alone, and nothing he runs reads
this project.

## What this repository is

This is Forge of Thought run through its own process. The engine
specifies how a thought travels a chain of versioned documents under
isolated adversarial review; this repository is that chain applied to
the engine itself. It holds the briefs, one per whole the engine
grew by; the intent, with the positions the author holds and the
directions he rejected; the solution design, which says how the
positions are realised; the threads, one file per open or closed
matter; the decisions; the research; and the reviews and challenges
the isolated reviewers returned.

It also holds the recipes whose renders are the engine's own README,
release notes and CONTRIBUTING. Those recipes send their output into
the engine root, so a release of the engine lands in two commits: one
here, one in the engine. What is special about this project lives in
its recipes, not in the engine's scripts; otherwise it is one project
among the others, under git like them.

## Who clones it, and how

Whoever develops the engine clones this repository beside it, as
`projects/forge`, with `/import-project
https://github.com/pche-broken-artist/forge.git`. The author's
commands read it from there: the engine check, the documentation run,
the release of the forge, the addition of a new artefact and the
renders of the README, the release notes and CONTRIBUTING. The paths
`projects/forge/...` that the documentation cites are the paths of
that clone. A release of the engine then lands in two commits, one
here and one in the engine, with one tag of the same name on both.

## Where it stands

| File | Version | Status | Date |
|---|---|---|---|
| 10-intent.md | 7.1 | draft | 2026-11-08 |
| 40-solution-design.md | 0.64 | draft | 2026-11-08 |

31 threads are open.

## Where to say something

This repository has no Discussions, Issues or policies of its own;
everything goes to the engine.

- Discussions: https://github.com/pche-broken-artist/forge-of-thought/discussions
- Issues: https://github.com/pche-broken-artist/forge-of-thought/issues
- How to contribute: https://github.com/pche-broken-artist/forge-of-thought/blob/main/CONTRIBUTING.md
- Security: https://github.com/pche-broken-artist/forge-of-thought/blob/main/SECURITY.md

## About this README

This README is a render of `recipes/readme-project.md`, regenerated
at every release and never edited by hand; fixes go into the recipe
or the inputs. Reading this repository needs nothing beyond a
Markdown viewer. Maintaining and evolving it needs **Forge of
Thought** — the engine this project is run under:
https://github.com/pche-broken-artist/forge-of-thought.

_Last updated: 2026-11-08_
