---
project: forge
render: readme-project
generated: 2026-11-08
recipe: recipes/readme-project.md v0.1
inputs:
  - ledger.md
  - 10-intent.md v6.23
---

# Forge of Thought, the forge's own project 6.23

*The thinking behind the engine, kept as a project of the engine's
own process*

Whoever wants to use Forge of Thought needs the engine,
https://github.com/pche-broken-artist/forge-of-thought, not this
repository: a user clones the engine alone, and nothing he runs reads
this project.

## What this repository is

This is Forge of Thought run through its own process. The engine is a
place for forging thoughts: an idea travels a chain of versioned
documents, from a brief through an intent to the layers a project
needs, under isolated adversarial review, with the principal deciding
every piece of content and Claude owning structure, order and
discipline. The engine's own design went the same way, and this
repository is that chain.

It holds the briefs of the engine's parts, the intent with its
positions and rejected directions, the solution design, the threads
that are still open, the decisions, the research, the reviews of the
critics and the checks, and the challenges of the peer reviewers. It
also holds the recipes whose renders are the engine's own README,
release notes and CONTRIBUTING: those three files are generated from
this project and land in the engine's root.

## Who clones it, and how

Whoever develops the engine clones this project beside it, as
`projects/forge`, with `/import-project
https://github.com/pche-broken-artist/forge.git` run in the engine;
the repository is named `forge` so that the import needs no rename.
The author's commands read it there: the engine check, the
documentation run, the release of the engine and the renders of the
README, the release notes and CONTRIBUTING. A release of the engine
then lands in two commits, one in this repository and one in the
engine. The repository starts clean, its first commit naming the
engine commit it was cut from; the history before that is the
engine's.

## Where it stands

| File | Version | Status | Date |
|---|---|---|---|
| 10-intent.md | 6.23 | draft | 2026-11-08 |
| 40-solution-design.md | 0.61 | draft | 2026-11-08 |

Thirty threads of the intent are open, each one file under
`threads/`.

## Where to say something

This repository has no discussions, issues or policies of its own;
everything goes to the engine:

- Discussions:
  https://github.com/pche-broken-artist/forge-of-thought/discussions
- Issues:
  https://github.com/pche-broken-artist/forge-of-thought/issues
- How to contribute and how to report a vulnerability:
  https://github.com/pche-broken-artist/forge-of-thought/blob/main/CONTRIBUTING.md
  and
  https://github.com/pche-broken-artist/forge-of-thought/blob/main/SECURITY.md

## About this README

This file is a render of `recipes/readme-project.md`, regenerated at
every release and never edited by hand; fixes go into the recipe or
the inputs. Reading this repository needs nothing beyond a Markdown
viewer. Maintaining and evolving it needs **Forge of Thought** — the
engine this project is run under:
https://github.com/pche-broken-artist/forge-of-thought.

_Last updated: 2026-11-08_
