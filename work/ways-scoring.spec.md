---
version: 0.1
status: draft
project: forge
file: work/ways-scoring.md
---

# Ways scoring — Work specification

## Task
The scoring of the ways the base could reach a layer, for the
principal and Claude: every way of the brief `engine-split` scored by
the same measures and the same rules at every scoring, so that the
ways can be compared and the comparison repeated as what is tried
develops. The file shows, for the day of the scoring, each way with
its score on every measure and its sum.

## Inputs
- 00-brief-engine-split.md: the section The ways the base could reach a layer (what each way is)
- research/2026-11-14-anvil-carrying-layers/00-plan.md with its notes (the facts the first scoring rests on)
- sources/engine-split/ (the measurements made as the work goes on)

## Method
Ten measures, each from 1 to 5 by the rules below, the same rules at
every scoring; the first three count three times, the fourth twice,
the rest once; the most is 85. A score changes only when a fact
behind it changes: a trial, a release of Claude Code, a part built.
Every change of a score is a record in this specification's history
naming the way, the measure, the old and the new score and the fact.
A way is added or dropped only with the brief. A rule is changed only
by a write of this specification, and every way is then scored again
by it.

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

## Assumptions
- **ASM.0100** The way "one repository, the rules of a kind loaded only in its projects" is scored 4 on Function, not 5, because it rests on loading documented by the vendor and not yet tried here; whether rules loaded so reach the reviewers is unproven.

## Open
- **TBC.0200** (owner: PCHe) Four trials in the tool can move scores: whether an agent of one package preloads the contract skill of another and by which name; whether a plugin directory in the repository serves the base's scripts to project skills on Windows; whether a user's untracked file in the clone stops the pull; whether rules of a kind loaded on demand reach session and reviewers. Closed by: each trial run and its result recorded here.

## Making
Claude makes `work/ways-scoring.md` in English from the Method and
the facts of the Inputs: the day of the scoring, one table of the
ways against the ten measures with the sum, ordered by the sum, and
under it one line per way saying what it is in the brief's words. Of
this specification the file carries the names of the measures and
their weights and nothing else.
