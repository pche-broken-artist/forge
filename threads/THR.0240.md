---
id: THR.0240
concerns: intent
origin: the principal
owner: PCHe
priority: high
status: open
---

The size of CLAUDE.md. 523 lines on 2026-09-03 and
growing with every iteration; THR.0190 already records that a split
moves rules from always-on to on-demand and is a behaviour change, not
a cut. To be dealt with sooner or later whatever becomes of THR.0230,
which would help. Opened 2026-09-03 at the principal's direction. To
think through: what must be always-on, what can live in commands,
skills and templates and be read when its situation arises, and how
the effect is measured — by behaviour, never by line count. Measured
2026-09-06 at the THR.0270 trial (POS.1120): every reviewer subagent
receives, in its first user message before the task, the whole
CLAUDE.md together with `CLAUDE.local.md` (then still carrying the
git identities, since moved out, POS.0950), the assistant's memory
file and the git status — about 600 lines, the largest block of its
context, several times its own agent body and contract together; the
instance facts of `CLAUDE.local.md` (principal, language, git
identities) thereby reach an isolated reviewer that needs none of
them. The cost of CLAUDE.md is paid once per reviewer run, not once
per session. The single-source-of-truth check of 2026-09-06 (history
3.49) took CLAUDE.md from 636 to 584 lines by citation alone; what
must be always-on is still this thread's question. First instance
of the answer, 2026-09-14: the walkthrough paragraph became one
sentence and a pointer to a skill, with a hook repeating the hard
sentence at every prompt (POS.1170) — always-on is one sentence and
a pointer, the detail a file read when its situation arises.
The single-source-of-truth check of 2026-09-20 found seventeen
restatements; nine were settled the same day (history 4.16) and
eight low ones deferred until after THR.0390, whose condition fell
when that thread closed on 2026-09-26 — they are on the table
again, with no date set. They reach
into the wording of CLAUDE.md and into the Commands table the
README and `/man` derive from: state vocabularies enumerated in
three places, the critic contract restating prime directive 8, the
brief's rules restated in two state files, genre checklists beside
their skeletons, index fields and ledger columns restated by
`/ingest` and `/research`, the bundle index entry as a declared
copy, sentences echoed inside CLAUDE.md and in skills, rosters
written out by name. The report is not filed; a re-run of the check
gives them again.
2026-09-28: the elicitation per artefact (POS.1310) is the move of
the rules of particular artefacts out of CLAUDE.md into their
definitions. The brief's estimate is 43 to 53 lines fewer of 663
in the always-on part, the state files growing by about as much;
the line count is an effect, the proof is conduct (POS.1380).
2026-10-02: the move is done, by walkthrough (intent 4.49). The
eight low restatements, filed that day as findings of the check,
are settled with it; one stays parked, FND.0650, the genre
checklists beside their skeletons. What must be always-on beyond
that is still this thread's question.

2026-10-22: 815 lines, the first release of the brief collaboration
and the hook on git among what grew it; FND.0650 stays parked.

2026-11-13: worked in the brief `00-brief-engine-split.md` (0.1),
sections The boundary and The order I see: CLAUDE.md cleaned and
the include made is the first step the principal pictures, and what
must be always-on stays among the brief's open points. This thread
closes when the brief is mined.

2026-11-14: a first try at the cut, in progress, nothing decided.
Drafts only, in `tmp/split/` (not in git): `CLAUDE.anvil.md`, the
rules of every project, 171 lines; `forge-layer.md`, the rules of the
forge alone, 91 lines; `kam-co-slo.cs.md`, where each section of
today's 920 lines went. Said in the conversation and not decided: a
division of the rules of conduct between the base and the forge
layer, with one write per round in the base and elicitation in the
layer; intent-first widened to what is built from an intent outside
the chain. The principal stopped the walk: the division was made
without being shown whole and was then put to him as isolated
decisions; he doubts this is the right way and is thinking it over.
Next: his word on how to go on, before any item of the draft is taken
up again. Nothing here is to be read as agreed.

2026-11-15: the principal's word on how to go on: a map of the whole
first, so that the division is seen whole before any piece is
decided. Made the same day as a work product, `work/engine-map.xlsx`
with its specification: 323 rows, CLAUDE.md taken apart into 215
pieces and the rest of the tree into 108 mechanisms, the targets
Claude's proposals until judged. The work runs on the branch
`claude-md-optimisation` of both repositories. Open: the principal's
judgement of the map (TBC.0300), then the boundary.

2026-11-16: the cut is steps 1 and 4 of the plan in the brief
`00-brief-engine-split.md` (0.6), section The plan. Done today: the
cases in which the forge went worse written down
(`sources/engine-split/conduct-baseline.md`), the line on skills
added to the per-prompt hook, and step 1 verified piece by piece in
the map (`work/engine-map.xlsx`): 102 pieces and 412 lines of 866,
26 a clean strike, 35 a strike with citations to repoint, 38 with
their owner to be completed first, and three catalogues last, with
their readers. The first batch is struck the same day: 23 of the 26
clean strikes, CLAUDE.md from 920 lines to 863, the tests green.
Three were left standing, the reason beside each in the map: 27, the
whole of prime directive 8, whose strike would renumber directives
cited by their number; 114, three lines of the layout tree that a
page of the documentation mirrors; 215, a rule whose wording stands
nowhere else. Before the strike the documentation map and the
citations of a directive by its number were read, which the agents
had not read; the recipes that take CLAUDE.md whole were not, and are
covered by the renders made again on `main` and read before a
release. The rest of step 1 is then taken by the sections of CLAUDE.md
and no longer by the kind of verification, since the sentences of a
section are interleaved: whatever of step 1 remains in a section is
done together, a strike, a citation repointed, an owner completed.
Step 1 is walked whole that day, no piece of it left untouched. Done:
41 pieces struck and 15 moved, CLAUDE.md from 920 lines to 671, the
tests green at every save. The last batch went the principal's way of
that day: the table of commands and the layout of the engine's root
moved word for word into files of their own read on demand,
`.claude/reference/commands.md` and
`.claude/reference/repository-layout.md`, which CLAUDE.md names by a
path written as text, never as an import, and which their readers
read there, the manual, the engine check and the documentation's
planner. Not verified: that Claude Code loads nothing of that folder
by itself; a new session on the branch will show. Deferred and not
decided, the principal's word of that day, 46 pieces and about 152
lines: they wait for three decisions and not for more striking. First,
how the reviewers get the rules of isolation without three copies in
their contracts: the section Isolated reviewers is the one owner about
thirty-five citations point to. Second, where the checks read their
rules if not in CLAUDE.md: the light check reads Versioning & status,
the project check the ID scheme and prime directive 6, every rule
there; a file CLAUDE.md names may be the answer, at a higher risk,
since a rule must hold when the file is not open. Third, how a
template comment copied into the files of the projects is changed:
most of what is deferred in Document chain cites one or would be owned
by one. The map carries the record of what is done
(`work/engine-map.xlsx`: the state of each piece, what was done to it,
and a log of the steps), and its log names the pages of the
documentation to be looked at when it is made again on `main`. Next:
the principal's word on the three decisions, or step 2 of the plan.
First in the next session, on the branch: look that nothing of
`.claude/reference/` is loaded, and run the engine check as the test
of the day's changes. Seen that day, for the measure: the line on
skills in the per-prompt hook did not stop one case of a skill's work
done by hand, the tests run beside another command in the middle of a
turn, where the hook's reminder does not reach.

<!-- A thread (POS.1680), one file per thread in threads/; the header
is its state: what it concerns, where it came from, whether it is
open. The rules of a thread, its life and its closing:
`.claude/skills/forge/states/intent.md`, Threads and files. -->
