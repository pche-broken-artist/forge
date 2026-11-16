---
project: forge
title: The engine split, the base under the forge and what a user makes for himself
author: PCHe
version: 0.6
status: draft
---

<!-- Only this header is fixed; the text below it is free-form. The
rules: its definition, `.claude/skills/forge/states/brief.md`; the
history companion:
templates/history.md. -->

## What this brief is for

The firm plan for making CLAUDE.md smaller and for trying the
division of the forge into the AI engine and the framework, in steps
taken one at a time (my word of 2026-11-16). The threads have carried
it since September task by task (THR.0230, THR.0240, THR.0850). The
plan is fixed; what stands around it is what the plan needs to be
understood, and nothing more.

What the AI engine is packaged into for my own projects is the
project forge-rollout's, not this brief's.

## Why

The forge works noticeably worse since the change of the model, and
one suspect is the size of CLAUDE.md (remark: a suspicion, not
measured): 920 lines against the vendor's advice of under 200
(source: `research/2026-11-14-anvil-carrying-layers/00-plan.md`,
card 2). The forge is to work better than today: a rule stands where
it is read when it is needed, and the context is spent on the work.

Whatever every framework needs alike is lifted out of the forge into
an AI engine they share: git through the scripts, the ledger and its
upkeep, versioning and history, the ID scheme, isolated agents on
the session model, recipes and renders, sources and research with
their indexes, `/save`, `/check`, `/setup` and the instance facts.
Forge of Thought becomes the first framework on it, not the AI
engine itself. One tool that does everything is not wanted (my word
of 2026-09-26). The AI engine is to be a standalone public project
as well (my word of 2026-11-15); a further git inside git is not
wanted.

## The plan

1. CLAUDE.md trimmed of what is low risk: what the tree or its owner
   already says is struck, and what holds only while one command
   runs moves to the skill, the template or the script that owns it.
   Nothing that must hold in every message leaves in this step. With
   it the per-prompt hook gains one line, that what a skill handles
   is done through the skill, at once.
2. CLAUDE.md cut in two as a trial: what we take for the AI engine's
   in a file of its own, included by the main one. The forge behaves
   as before; no skill, agent or script moves, and which file is
   which layer's is said by a list.
3. The AI engine exported by a script from that list into a
   repository of its own, which other projects read; I try it there
   and the cut is tuned in the forge, the export made anew each time
   and never mended in place.
4. The harder part of the optimisation: what must not fail into a
   hook, the rules loaded with a kind of file after a trial of that
   mechanism, the wording of what stays always loaded.

The physical separation comes much later, once the cuts are tried
and make sense.

People in the company work on the forge every day and nothing may
break under their hands: the work runs on a branch, and `main`,
which they pull, takes a step only once it has been tried.

What keeps it safe: the cases in which the forge went worse after
the change of the model, written down before the first step and read
again after each; every step saved on its own, so that it can be
traced and taken back; a trial whether an isolated agent sees the
included file, before the cut; a citation of CLAUDE.md by section
means the always-loaded text with the included file, and a rule that
moves takes its citations along in the same step. Neither the
documentation nor the manual grows poorer by the cut: what leaves
CLAUDE.md stands where `/document` and `/man` read it, the two
brought to read it there, and when `main` takes a step the
documentation is made again and what changed in it is read before
the release (my word of 2026-11-16).

## The parts and their names

Four layers, each called by its name (my word of 2026-11-15): the
AI engine, the general mechanics under every framework; the
framework, what makes one forge that forge (the elicitation, the
concrete lenses, personas and checks, the chain), Forge of Thought
being the first; the framework definition, the project in which a
framework is designed by its own process, today `projects/forge`;
and the projects, what a user makes. Later a family; Forge of Proof
for tests and Forge of Form for UX/UI and the prototype are working
names of 2026-11-09, temporary.

The word engine never stands alone: the AI engine is always written
in full, and any other engine carries its own qualifier, the
render engine, pandoc or Claude in a conversion, the model engine,
a model of another family.

Anvil stays a working name of the AI engine and does not stand as
its public name: at least fifteen tools for AI coding agents carry
the name, several of them for Claude Code (source:
`research/2026-11-15-the-name-anvil-for-a-standalone-ai-engine.md`).
The public name is open.

The vocabulary holds for what is written from now on. Older texts
are brought to it by what the old word can harm, in this order:
first where it bears on how the forge functions, the instructions
Claude acts on; second where it bears on development, the texts
Claude reads when the forge is worked on, the intent and the
solution design among them, which must not mislead him; third where
it bears on understanding, the README, the documentation and
whatever else a user reads. The intent and the solution design are
brought to it only once the cut is made and found to hold (my word
of 2026-11-15). The names of scripts and identifiers are no
priority. Records and immutable documents are never changed. In
texts written before 2026-11-15 the bare word engine means the whole
repository.

What a user clones today, the AI engine and the framework in one
repository, is said outward as the forge framework, one word for the
user; the inner division is the author's (my word of 2026-11-07).
(remark: framework now names the second layer alone; what the whole
is called is open.)

## The boundary

A way of sorting for now; it is decided when the separation is taken
up. The AI engine is the mechanics: the history made, the ledger
counted, git looked into so that nothing tangles, speech put so that
the verdict line can answer it. It gives functions and forces no
conduct, since a project may be anything, a budget or an analysis of
network logs. The framework is the logic: how the conversation runs,
what is to be drawn out, that there is an artefact. The check is the
AI engine's, the critic and the challenger the framework's (my word
of 2026-11-15).

The whole sorted piece by piece is the map, `work/engine-map.xlsx`:
CLAUDE.md in 215 pieces and the rest of the tree in 108 mechanisms,
each with where it would go, a proposal until I have judged it.
Where the boundary runs today: clean in the agents, the templates
and most skills and scripts; through CLAUDE.md, the three scripts
that know the chain by name (ledger, check, migrate), the forge
skill and the walkthrough hook (source:
`research/2026-11-07-engine-and-forge-framework-by-file.md`).

## What is known

- Everyone surveyed ended at a small core that owns mechanism and
  format, with the content outside it; retreats from too much
  division are common; the advice is to try first on one real case
  (source:
  `research/2026-10-03-one-tool-a-core-with-modules-or-several-tools.md`).
- Tried on one real case, 2026-11-13: a kit of the core without the
  chain, made outside the forge, served as the base of a project of
  a completely different kind (the operations of my own machine),
  and served well; more cannot be added to it in that form. (source:
  the run is to be registered in `sources/` before it is cited by
  the intent.)
- The plan takes the first of nine ways compared, the whole kept and
  the AI engine released apart by a script (source:
  `research/2026-11-14-anvil-carrying-layers/00-plan.md`; the
  scores: `work/ways-scoring.md`).
- An included file is loaded with the file that includes it: the cut
  in two saves no context by itself, only what leaves CLAUDE.md
  does; whether an isolated agent sees an included file is not known
  (source:
  `research/2026-11-14-anvil-carrying-layers/02-always-on.claude.md`).
- Today's state was measured on 2026-11-14; the measurements are
  kept in `sources/engine-split/`.

## The other two priorities

Beside this plan I want two more things solved: what a user makes
for himself (THR.0300) and how a new type is added (THR.0480). They
stood in this brief as my priorities, not as parts of the split;
each is a matter of its own, worked in its thread (my word of
2026-11-16).

## Threads this brief carries

Whole: THR.0230, THR.0240, THR.0850. My other two priorities, in
their own threads: THR.0300, THR.0480. As context: the derivations,
THR.0420, which can live on the AI engine if the forge is split.
Parked with the brief: CHL.0150 (every position since 3.0 has been
the engine's and the boundary is drawn by accretion).

## Still open

- The public name of the AI engine.
- What the whole a user clones is called.
- Whether the AI engine has a definition of its own beside that of
  Forge of Thought.
- Whether the skills are parted into directories of their own, or
  the list alone says which is whose.
- What stays always loaded in CLAUDE.md, judged in step 4.
- Whether every new position should name its layer.
- What the AI engine needs before others than me read it: a version
  number of its own, today it is the intent's; a minimum a project
  declares; a pull that delivers a release, not the head of `main`.
