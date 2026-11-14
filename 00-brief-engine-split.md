---
project: forge
title: The engine split, the base under the forge and what a user makes for himself
author: PCHe
version: 0.2
status: draft
---

<!-- Only this header is fixed; the text below it is free-form. The
rules: its definition, `.claude/skills/forge/states/brief.md`; the
history companion:
templates/history.md. -->

## What this brief is for

To think the split of the forge as one whole and decide it: a base
that owns the mechanics, the forge as the first operating layer on
it, and a place for what a user makes for himself. The threads have
carried it since September task by task (THR.0230, THR.0300,
THR.0480, THR.0850, THR.0240); this brief is to make us think of it
as a concept, and the plan of the work comes out of it. Nothing in
it is decided yet.

What the split is packaged into for my own projects is the project
forge-rollout's, not this brief's.

## The idea

Whatever every operating layer needs alike is lifted out of the
forge into a base they share: git through the scripts, the ledger
and its upkeep, versioning and history, the ID scheme, isolated
agents on the session model, recipes and renders, sources and
research with their indexes, `/save`, `/check`, `/setup` and the
instance facts. Forge of Thought becomes the first operating layer
on that base, not the base itself. A new layer is then written as
content only. The picture is several small cooperating layers on one
base, not one large tool that absorbs everything; one tool that does
everything is not wanted (my word of 2026-09-26).

Whether the split is within our powers at all is the question. The
technical shape is unknown; a further git-inside-git nesting is not
wanted; the base should ideally be a thing of its own, through which
I release substantial new functionality on git.

Two ideas of the split, a thin base of its own and a large forge
into which layers are installed, are one thing seen from two ends;
what they open is the unit of installation (from the brief
`elicitation`, 2026-09-28).

## The parts and their names

Three parts, later a family: a general base under every forge; an
operating layer per forge (the elicitation, the concrete lenses,
personas and checks, the chain); and the project in which an
operating layer is designed by its own process. Working names of
2026-11-09, temporary: Anvil for the base, Forge of Proof for
tests, Forge of Form for UX/UI and the prototype. Proposed and not
decided: `framework` for an operating layer, `definition` for its
project; the word `engine` no longer for the base or the
repository, kept where it means a model or a converter. Today
`engine` means the whole repository, a model of another family and
a converter at once; `core` stands beside it and the operating
layer has no name. The vocabulary is settled before anything else
is, and not hurried (THR.0850).

What a user clones today, base and forge layer in one repository,
is said outward as the forge framework, one word for the user; the
inner division is the author's (my word of 2026-11-07).

## The boundary

The boundary is mechanism against instance. The base owns the
mechanism: the dispatchers, the shape of a definition, the contract
of a template, the shape of the conversation, the numbering of
layers, the isolated subagent with its record, states and
walkthrough. An instance is content: one pair of files, a definition
with its template, a lens, a persona, a check, a genre. The base
never defines an instance; the user never changes the mechanism. The
test: does CLAUDE.md have to change for it? If not, it is an
instance; if yes, it is a derivation (THR.0420).

What the cases of the derivations showed: the chain is the layer's
(its artefacts, their number, order and templates); the base carries
recipe and render, the layer names the output form; challenger
personas are the layer's; for the critic a nested point, what is
generic (consistency, formal correctness) and what is the layer's
(the drift brief to intent to assignment).

Where the boundary runs today, every file a user clones sorted
(`research/2026-11-07-engine-and-forge-framework-by-file.md`): clean
in the agents, the templates and most skills and scripts; through
CLAUDE.md, the three scripts that know the chain by name (ledger,
check, migrate), the forge skill and the walkthrough hook. Every
"between" is one shape: a mechanism that names the forge's artefacts
instead of reading them from the definitions.

The cost, named early (CHL.0110): the rules of particular artefacts
had to move from CLAUDE.md into the definitions first. That move is
done (intent 4.49, POS.1310); what must be always-on beyond it is
still open (THR.0240: 815 lines on 2026-10-22, a rule moved into a
skill is weaker late in a long session).

## How a new type is added

Settled before the split, which inherits the answer (THR.0480). One
table of rules for how each type is created, led centrally, not a
sentence in every dispatcher; very easy for a future user to add
artefacts, a whole chain and elicitors of his own; the elicitors on
that list. Done so far: an artefact of the chain by `/new-artefact`,
and whatever can be added by a command has a definition with the
skeleton `templates/<type>-definition.md`. The friction found: the
rosters written into CLAUDE.md's sentences while the dispatchers
scan the same names from disk; a layer costs two files and about
eleven places because the operating layer writes "assignment" where
it means "the last layer".

## What a user makes for himself

Everything a user makes for his own use, with no ambition of
contributing it: agents, checks, critics, challengers, artefacts,
elicitations, genres, research. Instances only, never the
mechanism; a user-defined artefact of the chain is conceivable (my
word of 2026-11-13). It lives in the user's own git, at a place the
base does not know and `forge-pull` never overwrites, on the pattern
of `CLAUDE.local.md`; for me, my own repository beside the forge.
The rosters of `/critique`, `/challenge`, `/check`, `/forge` and
`/recipe` list what lies there beside the base's own: if the
mechanism is one, every dispatcher reads both roots. What is central
and what is the user's is never mixed; one place lists every type
that can be created; naming conventions against a collision of
names. Open: how a local agent takes the shared contract skill, what
happens when the base renames or reshapes it, whether Claude Code's
own user-level agents already serve (THR.0300).

Research:
`research/2026-10-03-user-extensions-kept-apart-from-the-core.md`.
The user's things live where an upgrade never writes; the field is
split on whether a user's thing may shadow a core one of the same
name or may only be added beside it; when the engine renames a
contract, a user's agent runs without it and nobody is told; Claude
Code has no mechanism for artefact definitions and templates.

## What the split and the user's own things have in common

One boundary and one mechanics: the boundary of mechanism against
instance, and every dispatcher and script reading instances from
disk, from more than one root, instead of names written into
CLAUDE.md and into the three scripts. For the user the second root
is his own repository; for the split the second root is the forge
layer as a package of instances beside the base. The same work, two
consumers; that is why they are one brief (2026-11-13).

## What is known

Research
`research/2026-10-03-one-tool-a-core-with-modules-or-several-tools.md`:
everyone surveyed ended at a small core that owns mechanism and
format, with the content outside it; nobody runs several equal tools
with a designed hand-over; retreats from too much division are
common; it advises not to divide now and to try first on one real
case.

Tried on one real case, 2026-11-13: a kit of the core without the
chain, made outside the forge, served as the base of a project of a
completely different kind (the operations of my own machine), and
served well; more cannot be added to it in that form. (source: the
run is to be registered in `sources/` before it is cited by the
intent.)

Every further change makes the split harder; against it, other
things were wanted quickly. The order of the briefs was `brd` first,
then this one (POS.1380); `brd` was born 2026-10-16.

## The order I see

First the division: what is base, what is the forge layer, what is
the user's, and the names. Then where and how the plan and the
solution are made. The steps as I picture them, nothing decided:
CLAUDE.md cleaned and the include made at once; the forge kept as
one monolith from which Anvil can be separated automatically; then
the separation. The first item of the work is research of its own
into what Claude Code offers today for a base carrying several
layers; the packaging research of 2026-08-29 served the
engine/projects split and is not reused.

The steps to walk, one at a time, each looked at when it is reached
and the ways scored again as what is tried develops (my word of
2026-11-14): CLAUDE.md divided into a small always-on base and the
rules of the forge layer, measured by conduct; a trial whether the
rules of a kind of project can be loaded only in its projects, the
reviewers included; then the base released apart by a script from a
list of its files. A bare kind of project, one that uses no feature
of the forge and works otherwise, is wanted and tempting to run; it
comes after the division, since before it such a project carries the
whole context for nothing.

## The ways the base could reach a layer

Compared in the research of 2026-11-14 (source:
`research/2026-11-14-anvil-carrying-layers/00-plan.md`), none
decided. The scores were judged again the same day with what the
research did not weigh, the sustainability of the context, and with
function first; the rules and the breakdown stand under How the ways
are scored (remark: a judgement, not a measurement, to be judged
again as what is tried develops; the research's own scores stand in
its synthesis).

1. **The whole kept, the base released apart by a script (71).**
   The forge stays one repository in which everything is developed;
   at every release a script writes the files marked as base into a
   public repository of its own, from which projects that are not
   the forge pull. A clone of the base carries the base's rules
   alone. Established practice; two public repositories, the base's
   read-only; CLAUDE.md and the mixed files must be parted first.
2. **One repository, the rules of a kind loaded only in its
   projects (68).** The root CLAUDE.md carries the base alone; the
   rules of a kind of project lie in a file of their own that the
   project's CLAUDE.md imports. The central update exists today
   through the pull (remark: a hypothesis until tried, whether the
   rules loaded this way reach the reviewers).
3. **One repository, everything in one CLAUDE.md (66).** As today, a
   project that is not the forge a further kind of project. Works at
   once and is the cheapest; every kind added lengthens what every
   session and every reviewer carries, 916 lines today against the
   vendor's advice of under 200 (source: the same research, card 2).
4. **A plugin for the executable parts, the rule text in the
   project's tree (54).** An update writes into no file a user or a
   layer owns; two things are kept in step and every call of a
   script is rewritten.
5. **The base released in the form of a plugin (52).** Claude Code
   checks the version a layer needs; the always-on rules still have
   to be written into every project, and a plugin's updates have
   been seen not to arrive.
6. **Two repositories side by side joined by an import (51).** The
   layer's CLAUDE.md imports the base's from the folder beside it.
   No packaging; a dialog on the first run whose refusal is silent
   and permanent, and the neighbour's hooks and settings do not
   load.
7. **The base a package, each layer a repository (49).** The
   cleanest picture; no carrier of its own in Claude Code, so it
   ends as 4, 5, 6 or a copy; the field retreated from it twice.
8. **A plugin alone (44).** The user's repository stays clean; the
   rules reach the session or the reviewers, not both.
9. **User-level configuration (40).** No dialog; one base per
   machine for every project and no channel of update.

What every way needs and the forge lacks: a version number of the
base that is its own, today it is the intent's; a minimum a
project or a layer declares; a pull that delivers a release, not
the head of `main`; a place for a user's own things the pull does
not look at.

## How the ways are scored

Ten measures, each from 1 to 5 by the rules below, the same rules at
every scoring; the first three count three times, the fourth twice,
the rest once; the most is 85. A score changes only when a fact
behind it changes: a trial, a release of Claude Code, a part built.

- **Function (×3).** 5: the rules reach the session and the
  reviewers with no dialog and no cap, scripts and hooks run on
  three systems, by means the forge uses today. 4: the same, resting
  on a documented mechanism not yet tried here. 3: works with a
  documented limit or with a copy kept in step. 2: a part does not
  arrive without an act of the user, or has reported failures. 1:
  the rules cannot reach both the session and the reviewers.
- **Central update (×3).** 5: one command of the user, proven here,
  reaches every project. 4: the same for more than one repository.
  3: a channel exists, with reports of updates not arriving or with
  its carrier not chosen. 2: the user's machine decides whether
  anything arrives, or no channel exists.
- **Context (×3).** 5: a session carries the rules of the base and
  of what the project uses, held by the carrier. 4: the same, held
  by where the files lie. 2: the rules of everything on the machine
  are loaded in every project. 1: one always-on file that grows with
  every kind of project.
- **Cut (×2).** 5: nothing moves. 4: a list of the base's files and
  the cheap renames. 3: also CLAUDE.md divided and the mixed files
  parted. 2: also the single root split in every script and every
  call of a script.
- **Development loop.** 5: a change is live at once in the clone.
  4: live at once in two places, or by loading in place as
  documented. 3: loading in place under rules that changed lately.
  2: an install or a link before a change can be tried.
- **A user's own things.** 5: where no update writes, names kept
  apart by a namespace. 4: where no update writes, names kept apart
  by convention. 3: inside the clone, in a place still to be made
  that the pull does not look at. 2: a same name replaces silently.
- **Version and contract.** 5: Claude Code checks the version a
  layer needs and the shared reviewer contract crosses the boundary,
  both documented. 4: the version by Claude Code, the contract
  across packages unverified. 3: the contract as today, the version
  by a script still to be written. 2: neither without work of its
  own.
- **First day.** 5: clone, start, one dialog, the user's files alone
  in his tree. 4: the same with the base's files among his. 3:
  short, with choices to make, a reported silent failure or a write
  into the user's home. 1: two clones and two dialogs, one whose
  refusal is permanent.
- **Migration.** 5: a version in the project and migrations chained
  from it. 4: a migration command exists, once per project. 3: to be
  built with the carrier. 2: none possible per project.
- **Claude Code's changes.** 5: stands on memory files, skills and
  agents in the tree alone. 4: also on hooks in the project's
  settings. 3: also on imports across directories or added
  directories. 2: in part on plugin loading. 1: wholly on plugin
  loading and a marketplace.

| Way | Function | Update | Context | Cut | Dev | Own | Version | First day | Migration | Changes | Sum |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 The whole kept, the base released apart | 5 | 5 | 4 | 3 | 5 | 3 | 3 | 4 | 4 | 4 | 71 |
| 2 One repository, rules of a kind on demand | 4 | 5 | 4 | 3 | 5 | 3 | 3 | 4 | 4 | 4 | 68 |
| 3 One repository, one CLAUDE.md | 5 | 5 | 1 | 5 | 5 | 3 | 3 | 4 | 4 | 4 | 66 |
| 4 Plugin for the executables, text in the tree | 3 | 3 | 4 | 2 | 3 | 5 | 4 | 3 | 3 | 2 | 54 |
| 5 The base released as a plugin | 2 | 3 | 4 | 2 | 4 | 5 | 4 | 3 | 3 | 2 | 52 |
| 6 Two repositories and an import | 2 | 4 | 4 | 2 | 4 | 4 | 2 | 1 | 3 | 3 | 51 |
| 7 The base a package | 2 | 3 | 4 | 2 | 2 | 4 | 3 | 3 | 3 | 3 | 49 |
| 8 A plugin alone | 1 | 2 | 4 | 2 | 3 | 5 | 4 | 3 | 3 | 1 | 44 |
| 9 User-level configuration | 3 | 2 | 2 | 2 | 3 | 2 | 2 | 3 | 2 | 3 | 40 |

## Threads this brief carries

Whole: THR.0230, THR.0300, THR.0480, THR.0850, THR.0240. As
context, one-way and conditional: THR.0420, the derivations, which
can live on the base if the forge is split. Parked with the brief:
CHL.0150 (every position since 3.0 has been the engine's and the
boundary is drawn by accretion). Whether every new position should
name its layer waits for this brief to say what the layers are.

## Still open

- Whether user modifications are the engine split or a level of
  their own; the field treats them as a level of their own on the
  same mechanism.
- Whether to divide at all, or to call it a generalisation of the
  forge; the measure is to be found. Whether the ambition is heading
  somewhere that cannot be managed.
- The unit of installation, and how a user's own artefact is kept
  from colliding with an upgrade of the base.
- What must be always-on in CLAUDE.md, measured by conduct and never
  by line count.
