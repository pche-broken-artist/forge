---
version: 0.6
status: draft
project: forge
file: work/engine-map.xlsx
---

# Engine map — Work specification

## Task
A map of everything the forge does, for the principal and Claude, to
work the plan of the brief `engine-split` over (its section The
plan; THR.0240): the functionality of the forge laid out in its
smallest meaningful pieces, each with what it is, where it lives
today, where it would belong, in which step of the plan it is first
touched and at what risk, so that the whole is seen before any piece
of it is decided. The file shows one row per piece, the principal's
verdict on the row beside it, and a summary of how much of CLAUDE.md
would go where.

## Inputs
- CLAUDE.md of the engine, as it stands (920 lines at commit e0deca3)
- the engine's tree at that commit: `.claude/skills/`, `.claude/agents/`, `.claude/settings.json`, `scripts/`, `templates/`, `tests/`, the files of the root
- 00-brief-engine-split.md: the sections The plan, The boundary, The parts and their names
- research/2026-11-07-engine-and-forge-framework-by-file.md (which file is which layer's)
- 10-intent.md and 40-solution-design.md: the titles of the positions and of the parts, for the origin of a row
- threads/THR.0240.md (what the first try at the cut said and left undecided)
- the verification of step 1 of 2026-11-16: six isolated read-only agents on the session model, one per group of sections of CLAUDE.md, each piece checked against its proposed owner and against whoever cites or reads it; their reports are not kept, the file carries what they found

## Method
The unit is a row: one smallest meaningful piece of what the forge
does or says, a rule, a fact, the description of a mechanism, a
catalogue or a pointer that could be moved on its own. The map has
two depths. CLAUDE.md is taken apart to that unit, and every line of
it belongs to exactly one row, blank lines, headings and the fences
of code blocks aside. Everything else is one row per mechanism: a
skill, a definition with its template, a genre with its skeleton, an
agent, a script, a hook, a template, a setting, the tests, a file of
the root.

The columns, their names and values carried by the file's legend:
- the number of the row, a plain running number that is the row's
  address in conversation and not an ID of the forge's scheme;
- the area, a theme that runs across the carriers; the name; what
  the piece is;
- the kind: conduct, a rule about files, the description of a
  mechanism, the shape of a file, a fact, a catalogue, a pointer;
  and in the second depth a mechanism, an instance, a skeleton, a
  file of the repository;
- the origin, the positions and the parts of the solution design the
  piece comes from, empty where none was found;
- today: the carrier, the place, the lines of CLAUDE.md with their
  count, and where the same is said a second time;
- when it must hold: in every message, when a command runs, when a
  kind of file is worked, without exception, on demand;
- the target: the layer (the AI engine, the framework, the framework
  definition, the repository, to be parted, the user's), the carrier
  (always loaded, a hook, a rule loaded with its kind of file, a
  skill, a script, a template, an agent, nowhere) and the place;
- the certainty of the target, the effort of the move, its impact,
  and the rows that move with it;
- the step of the plan in which the row is first touched, and the
  risk of that;
- for a piece of step 1, its verification: the verdict, and the
  evidence, the owner's file and line and whoever cites or reads the
  piece;
- the state of a piece, struck, moved or deferred, empty while it
  waits for its step, and what was done to it, when and in which
  batch;
- the verdict and the note, which are the principal's.

The rules of filling:
- The target layer follows the boundary of the brief, the AI engine
  the mechanics and the framework the logic; a mechanism that names
  the chain is to be parted.
- The target carrier of a piece of CLAUDE.md is one of the five
  places of the brief, the skill that owns it widened to the owner
  whatever it is: a skill, the header of a script, the comment of a
  template, the contract of an agent. What must hold in every
  message stays always loaded; what must not fail is a hook; what
  is tied to a kind of file is a rule loaded with it; a procedure
  goes to its owner; a catalogue the tree already says goes nowhere.
- A mechanism keeps its carrier; only its layer is judged.
- Certainty is high where the inputs agree, medium where the target
  is Claude's judgement, low where the inputs disagree or the target
  needs a new convention.
- Effort is none, small for a move of text, medium for text with a
  change in its owner or a new hook, large where scripts change.
- The risk of a piece of CLAUDE.md that leaves the always-loaded
  text is low where the tree or its owner already says it, or where
  it holds only while a command runs or a kind of file is worked and
  goes to the owner read at that moment; it is higher where it goes
  to a hook or to a rule loaded with its kind of file, where it must
  hold in every message or without exception, and wherever a doubt
  is named in its impact.
- The step follows from that: 1 for a piece that leaves at low risk,
  4 for a piece that leaves at higher risk, 2 for a piece that stays
  always loaded, sorted into one of two files by its layer and its
  wording judged again in step 4, 3 for a mechanism, which the list
  of the export names by its layer.
- The verification of a piece of step 1 has one of four verdicts: a
  clean strike, where its owner says all of it, nothing reads it in
  CLAUDE.md, and neither the documentation nor the manual would lose
  anything by it; a strike with citations to repoint; the owner to
  be completed first; not low risk, where a reader depends on the
  text standing in CLAUDE.md or the rule must hold when its owner is
  not being read. A piece found not low risk goes to step 4 at the
  higher risk, but for a catalogue that is not low risk only because
  the manual, a check or a page of the documentation reads it: it
  stays in step 1 as its last batch, moved together with its
  readers.
- A piece is struck by its sentences, not by its lines: the lines
  say where it stands, and several pieces share a line.
- A line on the border of two pieces is counted to one of them.
- Every step done on the cut is recorded in the file in the same
  step: the state of each piece it touched and what was done to it,
  and one row of the log for the step itself, also where the step
  belongs to no one piece.
- A deferred piece is left for now and not decided: it is neither a
  solution nor a judgement that the piece stays, and the reason and
  the step it returns in stand beside it.
- Everything in the target, the certainty, the effort, the impact,
  the step and the risk is a proposal of Claude's until the
  principal's verdict stands beside it; the verification is what the
  agents found, checked by nobody else.

The map decides nothing: a verdict is the principal's judgement of a
row, and what follows from the verdicts is written where it belongs,
the brief `engine-split` first.

## Assumptions
- **ASM.0200** The file is in Czech, its addresses (files, sections, IDs, commands) as they are, chosen by Claude for a working tool the principal reads row by row; against English, the language of the project, in which a row could be quoted into the brief without translation and the file would read like the rest of a public repository.
- **ASM.0210** Where one piece ends and the next begins is Claude's cut of a first version: the repository layout is taken block by block, the table of commands and the table of kinds as one row each, the table of prefixes by layer.
- **ASM.0220** Where the inputs disagree on a layer, the row follows the brief or Claude's reading, says so in its impact and carries medium or low certainty: the walkthrough and the working methods (the brief gives the shape of the conversation to the AI engine, the research of 2026-11-07 the methods to the framework), the threads, the recipe genres, the critic's contract.
- **ASM.0230** A rule loaded with its kind of file and every hook named as a candidate are untried here: a row that names one proposes a place and does not claim the mechanism works (the trial of rules loaded on demand: TBC.0200).
- **ASM.0240** The second place a piece is said in and the origin of a piece are filled from what CLAUDE.md itself cites and from what the reading showed, never from a search of every file: an empty cell does not say the piece is stated once or has no position. The counts of mentions of the chain in three scripts are those of the research of 2026-11-07, not counted again.
- **ASM.0250** The first try at the cut of 2026-11-14 (THR.0240; its drafts in the engine's working folder, outside git, nothing in them agreed) was read; a row that follows it or departs from it says so in its impact as the earlier draft.
- **ASM.0260** The layer of the rows outside the areas read on 2026-11-15, conduct and the reviewers, was filled by the earlier rule, mechanism against instance, and has not been read again by the boundary of the brief 0.5.
- **ASM.0270** The tree of a project and of a library in Repository layout is raised to the higher risk by a named doubt: the tree on disk shows the files and not what each is for, and the notes stand in no one other place; chosen against the rule alone, by which a catalogue read on demand is low.
- **ASM.0280** The verification read `.claude/`, `templates/`, `scripts/`, `tests/` and the recipes of the forge's own project, and ran nothing: a reader in the documentation map, in the intent or in another project is not in the evidence, and what the agents say of code they read and did not run.
- **ASM.0290** A clean strike holds while the other lines of CLAUDE.md it rests on stay; the evidence names them, and a later step that moves those lines judges the piece again.
- **ASM.0300** Four pieces the agents found a clean strike, whose wording stands nowhere else (117, 145, 157, 171), are entered as the owner to be completed first, by the rule that the documentation loses nothing; Claude's judgement, said in their evidence, chosen against the agents' verdict as it came.

## Open
- **TBC.0300** (owner: PCHe) The first version is to be judged: whether the unit is right, which columns are missing or not needed, and the language of the file (ASM.0200, ASM.0210). Closed by: the principal's look at the file and the write of this specification that follows.

## Making
Claude makes `work/engine-map.xlsx`, one workbook of five sheets, in
Czech (ASM.0200). `Mapa` has one row per piece in the columns of the
Method: filters on, the first three columns frozen, a list of the
allowed values on every column that has them, the principal's two
columns marked. `Souhrn` sums `Mapa` by formula, so that it moves as
the map is worked: the lines of CLAUDE.md by target carrier and
layer, the rows by today's carrier and target layer, the certainty,
the verdicts, the steps of the plan with their risk, the
verification of step 1 by verdict, the pieces by their state, done
and waiting. `Ověření` carries what the
verifying agents noted beside the rows, group by group: the pieces
that move together, the templates not to be touched, what was not
established. `Deník` is the log of the steps done on the cut, one
row per step: the date, the step of the plan and its batch, what was
done, where, the rows of the map it touched and what came of it.
`Legenda` says what each column and value means, which
columns are the principal's and that the targets are proposals. Of
this specification the file carries the names of the columns and
their values and the rule on what is a proposal, and nothing else.

The first making writes the file from the inputs by a script of
Claude's, which checks before it writes that every content line of
CLAUDE.md belongs to exactly one row. From then on the file is the
single truth and has no second copy: a later making reads the file,
keeps the principal's verdicts, notes and whatever else he changed,
and changes rows in place, never writing the file anew over his
work. The number of a row is stable: a new row takes the next
number, and the number of a removed row is not given again.
