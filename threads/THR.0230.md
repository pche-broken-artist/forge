---
id: THR.0230
concerns: intent
origin: the principal
owner: PCHe
priority: high
blocks: the plugin (THR.0190)
status: open
---

Can the forge be split into an engine and the rest?
One of three separate tasks the principal named on 2026-09-26, and
the only one this thread carries; the other two are THR.0420, the
derivations of the forge for other jobs, and THR.0300, everything
a user makes for himself. Opened
2026-09-03 at the principal's direction; a large rebuild if taken up,
to be worked out first and decided later — the principal is not sure
it is a good idea. The idea: whatever every framework needs alike is
lifted out of the forge into an engine they share — git through the
scripts, the ledger and its upkeep, versioning and Version History,
the ID scheme, isolated agents on the session model, recipes and
renders, sources and research with their indexes, `/save` and
`/check`, `/setup` and the instance facts — so that a new framework is
written as content only. Forge of Thought becomes the first framework
on that engine, not the engine itself; the picture is several small
cooperating frameworks on one engine, not one large one that absorbs
everything (much could be pushed into the forge, but CLAUDE.md is
already large — THR.0240 — and the separation helps there). The
frameworks that would sit on such an engine are THR.0420's, and
the boundary is drawn against its cases, outlined there in varying
depth: the product framework and the project-management one in
enough detail to draw it against, the test analysts' version so far
by its artefacts alone.
What they show about the boundary: the chain is the framework's
(its artefacts, their number, order and templates); "everything is
Markdown" is a forge rule — the engine carries recipe and render, the
framework names the output form; a dependency between frameworks is
the Dependencies mechanism across a framework boundary; the ledger's
tables are partly the framework's (tasks); agent types beyond the two
(a verifier) are the framework's.
*Agents.* Critic and challenger alike: the mechanism — isolated
subagent, ledger record, states, walkthrough — is the engine's, the
prompt content the framework's. Challenger personas are the
framework's (a UX challenger, a challenger of a work plan). For the
critic a nested point: what is generic (consistency, formal
correctness) and what is the framework's — in the forge the drift
brief → intent → assignment, perhaps further down.
*How the engine reaches a framework at every session* — no decision
now, every path recorded: one engine repository with the frameworks as
directories in it (simplest, one `forge-pull` upgrades everything, but
one CLAUDE.md and one command tree for all); the engine as a Claude
Code plugin with each framework a repository of its own (the cleanest
boundary; the finding of THR.0190 applies — a plugin carries no
CLAUDE.md, so a bootstrap skill by SessionStart hook — the largest
rebuild); engine and framework as two repositories joined by `@import`
and a clone alongside (CLAUDE.md travels, commands and agents do not —
copied or linked). THR.0190 is from now read as part of this question
and stays a thread of its own.
*Order of work.* The second framework must exist in outline before the
boundary can be drawn; the engine is not built ahead of it. Where the
engine is thought: decided 2026-09-07 — as a brief born in the forge
(`00-brief-<name>.md`, the way `00-brief-public-engine.md` was),
carrying the boundary list, the outline of the second framework and
the target shape; mined into the intent when the principal says so
(POS.0920). A project of its
own only afterwards, by spinoff of the decided part, if the decision
calls for one.
THR.0220 was settled on today's forge at 3.33 (POS.1100) as an engine
matter that carries over; THR.0210 stays open on the same
recommendation. CHL.0150 (2026-09-06, parked until after 4.0): since
3.0 every new position has been the engine's and the boundary is
being drawn by accretion; taken up after 4.0 if the split proves
useful.
2026-09-14 the principal drew a picture of three layers, and on
2026-09-26 corrected it into the three separate tasks named above.
What is left to this thread: an engine that owns the mechanics,
ideally a thing of its own, the technical shape unknown and a
further git-inside-git nesting unwanted, with the forge as one
framework on it, through which he releases substantial new
functionality on git. Whether that split is within our powers at
all is what the thread asks. It is worked as one brief
`engine-split` born in the forge (`/forge brief engine-split`)
together with THR.0190, which closes into it at its birth; the
name is his of 2026-09-26, after `layers` said nothing he could
read back and `frameworks` was overtaken the same day when the
three tasks parted. The two connections are one-way and
conditional: if the forge is split, the derivations of THR.0420
can live on the engine instead of each carrying a copy of the
mechanics, and nothing in THR.0300 waits for the split at all.
A matter for the brief, Claude's observation of 2026-09-26: the
word *engine* today means the forge's own repository against the
projects (SOL.0500), so the deeper engine this brief proposes
overloads it, and the brief settles that vocabulary before it
settles anything else. His reasons for
taking it up soon: every further change makes the split harder;
against it, the BRD layer and the field feedback (THR.0350) are
wanted quickly. Order agreed 2026-09-14: THR.0350 first, since the
brief is to be born by co-elicitation, the technique the
run record faulted. The order of the briefs is POS.1380's since
2026-09-28: `brd` first, then `engine-split`; the
brief brd born 2026-10-16. The brief's first item is research of its own into what Claude Code
offers today for an engine carrying several frameworks — the
packaging research of 2026-08-29 served the
engine/projects split and is not reused. Whether every new position
should name its layer waits for the brief to say what the layers
are. CHL.0150 stays parked with the brief.
2026-09-28, from `00-brief-elicitation.md`, material for the brief
`engine-split` and nothing decided. The two ideas of the split, a
thin engine of its own and a large forge into which frameworks are
installed like plugins, are one thing seen from two ends, and the
question they open is what the unit of installation is. A Claude
Code plugin cannot carry CLAUDE.md as always-on context and
carries everything else (research
`2026-08-29-claude-code-packaging.md`), which divides by itself:
the engine is the repository with CLAUDE.md and the mechanisms, a
framework is a package of instances (definition pairs, lenses,
personas, checks, genres). The cost is the one CHL.0110 named: the
rules of particular artefacts must first move from CLAUDE.md into
the definitions, which is what the elicitation per artefact does
(POS.1310). The installation mechanism is a research question.
How new types are added to the engine is THR.0480 (2026-09-30),
to be settled before this split.
The principal's word of 2026-10-04, unfinished and nothing decided,
said while the command `/new-artefact` was being found: today the
forge is a project made in the forge; what is the forge and what
is the distribution that goes to its users is open, and with it
how an artefact a user adds for himself is kept from colliding
with an upgrade of the engine. Version 1 adds to the engine
(POS.1430); where a user's own artefact lives waits for this
thread and for THR.0300.
2026-11-07, from the round over THR.0780, the principal's words for the
layers: *engine* is the universal mechanics alone; *forge framework* is
what makes the forge the forge, the agents, the reviewers, the
elicitation, the chain; the forge's own project is the thinking about
it. What a user clones today, engine and forge framework in one
repository, is said outward as the forge framework, one word for the
user; the inner division is the author's. The texts of the forge say
*engine* for the whole (SOL.0500); renaming them is this thread's, not
THR.0780's. The exercise of the day, every file a user clones sorted
into engine, forge framework and between, is
`research/2026-11-07-engine-and-forge-framework-by-file.md`: the
boundary is clean in the agents, the templates and most skills and
scripts, and runs through CLAUDE.md, the three scripts that know the
chain by name (ledger, check, migrate), the forge skill and the
walkthrough hook; every "between" is one shape, a mechanism that names
the forge's artefacts instead of reading them from the definitions.

2026-11-08: a trial kit of the core without the chain stands beside the
engine since 2026-10-29 (`forge-core-trial`; the brief `plugin` of the
project forge-rollout is the principal's text of what he wants). It
stands outside the forge on purpose: a test, made where it cannot touch
the forge's files or become a position by accident. It decides nothing
of this thread: what it shows on a real project enters the chain as a
source and is weighed in the brief `engine-split` (POS.1380), where the
split is decided (CHL.0680).

2026-11-13: the brief is born, `00-brief-engine-split.md` (0.1),
and this thread is worked there: it carries the split and what a
user makes for himself (THR.0300) as one whole, the vocabulary
(THR.0850) and the adding of types (THR.0480) with them, the
material of this thread and of the brief `next-gen` folded in. What
is settled goes into the brief and, at its mining, the intent; this
thread closes when the brief is mined.

2026-11-15: the boundary between the AI engine and the framework
taken up as a walkthrough over the map (`work/engine-map.xlsx`, of
THR.0240); unfinished, nothing of it in the brief yet. The
principal's word of that day: the AI engine is the mechanics, the
history made, the ledger counted, git looked into so that nothing
tangles, speech put so that the verdict line can answer it; it gives
functions and forces no conduct, since a project may be anything, a
budget or an analysis of network logs. The framework is the logic:
how the conversation runs, what is to be drawn out, that there is an
artefact. A rule such as "Claude only proposes, the principal
approves everything" is not the AI engine's; `??`, the verdict line,
a recommendation, the walkthrough and work step by step written at
once are. The check is the AI engine's, the critic and the challenger
the framework's. The map carries this as Claude's proposal in 29
rows, each saying so in its impact (the records of
`work/engine-map.spec.history.md`): 25 rows to the framework, three
to be parted, one with a note. The principal took the rows of
conduct as a first shot and has not judged the rest. Open: whether
the mechanism of definitions and of an artefact (`/forge`,
`/new-artefact`; rows 68, 70, 71, 73, 223, 230) goes with his word on
the artefact; the groups not walked yet, the threads, the recipe
genres, the tables of kinds and of prefixes, the kinds of project
with `/new-project`, the mechanisms that carry both layers, what is
the framework definition's; the areas of git, renders, documentation,
tests, the tree and the public face not read by this rule. Claude's
remarks, his own: a second framework is then no longer written as
content only, as the brief's idea has it; the walkthrough hook would
print lines the framework supplies; a text of conduct per project
rests on rules loaded per project, untried (TBC.0200 of
`work/ways-scoring.spec.md`). Not written yet: the brief's section
The boundary and the rule of filling in the map's specification.
Next: the principal's verdict on the rows of the reviewers, then the
definitions.

2026-11-16: the principal's firm plan stands in the brief
`00-brief-engine-split.md` (0.5), section The plan, and the boundary
as it is understood now in its section The boundary; the matter is
worked from there. The walkthrough of the map over the boundary,
begun 2026-11-15, is not continued row by row: until the separation
the boundary is a way of sorting. Who owns the run of a reviewer and
the dispatchers was put to him today and withdrawn; it waits for the
separation. Next: step 1 of the plan (THR.0240).

2026-11-17: step 1 of the plan is done and saved on the branch
(THR.0240); `main` has not taken it, and steps 2 to 4 are not begun.
The rules loaded with a kind of file, of the plan's step 4, were
tried that day ahead of step 2, on the principal's word, and dropped
for the shape of a file (THR.0240). Next by the plan: `main` takes
step 1, then step 2.

2026-11-18: `main` took step 1 on 2026-11-17, after the paragraph
above was written, and it was released as 7.13 (THR.0240). Steps 2 to
4 are not begun. Next by the plan: step 2.

<!-- A thread (POS.1680), one file per thread in threads/; the header
is its state: what it concerns, where it came from, whether it is
open. The rules of a thread, its life and its closing:
`.claude/skills/forge/states/intent.md`, Threads and files. -->
