---
date: 2026-11-08
project: forge
lens: clarity
target: all
reviewed: 10-intent.md v6.23 (read whole); 40-solution-design.md v0.63
  (read whole); 00-brief-tests.md v0.1, 00-brief-user-stories.md v0.6
  and 00-brief-pptx-gitignore.md v0.2 (read whole, born or changed
  since the last run); 00-brief-brd.md v0.5, 00-brief-research.md
  v0.3, 00-brief-collaboration.md v0.9, 00-brief-next-gen.md v0.4,
  00-brief-public-engine.md v1.0, 00-brief-elicitation.md v1.0,
  00-brief-documentation.md v0.1 and 00-brief.md (placeholder,
  DEC.0010) unchanged in version since the last run by the Briefs
  table and not reread; threads/ by header (status, concerns, origin)
  and THR.0780 whole; decisions.md DEC.0300 to DEC.0400 read,
  DEC.0410 to DEC.0430 by heading; ledger.md (made 2026-11-08:
  Briefs, Documents, Findings FND.2700 to FND.3190, Waiting);
  reviews/2026-10-25-critique-clarity-1315-18b0.md (FND.2760 to
  FND.2840, regression); 10-intent.history.md searched for FND.2760
  (the sixteen positions of 5.38); the check reports of 2026-11-01 to
  2026-11-08 by name only; .claude/skills/forge/states/{intent,
  solution-design,brief}.md and templates/{intent,solution-design}.md
  for the Aim each artefact is judged against and the sections each
  template requires.
reviewer: critic lens clarity (isolated context)
---

# Critique (clarity) - 2026-11-08

## Delta summary
- **New:** 7, numbered by the command: FND.4070, FND.4080, FND.4090,
  FND.4100, FND.4110, FND.4120, FND.4130
- **Verified resolved:** FND.2770, FND.2780, FND.2790, FND.2800,
  FND.2810, FND.2820, FND.2830, FND.2840
- **Still open:** FND.2760 (reopened below, in a narrower shape)
- **Newly obsolete:** none
- **Respected:** FND.0090 (rejected, DEC.0090); FND.3520 (rejected,
  DEC.0360: the skip clause of POS.1590 is not raised).

## Regression
- **FND.2760: reopened.** The sixteen positions of 5.38 keep one date
  but for POS.0220, which carries two again since 6.x ("since
  2026-11-02 ... Present shape 2026-11-08") with the way to it ("the
  scripts that matched three letters alone were the one limit,
  widened with the ledgers of three projects unchanged"); and the
  positions born or rewritten since follow the old model. The first
  finding below carries it.
- **FND.2770: verified resolved.** SOL.0830 says what holds of the
  fixture: `tests/fixture`, synthetic, the `projects/fixture` of the
  cutover deleted (DEC.0360); SOL.0670 cites it for the flag; SOL.0530
  names no exception to a bare `/save` and none exists.
- **FND.2780: verified resolved.** SOL.0200 carries no sentence on
  `last_change` written by the model; SOL.0210 "the ledger script
  finds them as citations (SOL.0690)"; SOL.0220 "by its modification
  time against the Date of its index entry"; SOL.0230 has no split
  into a ledger row; SOL.0640 "its row in the Work table, made by the
  ledger script from its first record".
- **FND.2790: verified resolved.** POS.0400 owns the target by its
  path with the why; POS.0410 and POS.0420 carry no copy of the
  paragraph.
- **FND.2800: verified resolved.** `/migrate` stands in the list of
  POS.1090.
- **FND.2810: verified resolved.** POS.0230 names SOL and TBC in the
  solution design (POS.1420), ASM and TBC in a work specification
  (POS.1520), US in the user stories (POS.2010).
- **FND.2820: verified resolved** in the design: SOL.0720 "a thread
  is never in a record file (way 1)", Choice "so that no merge handles
  a block with an inner state"; SOL.0460 "the migration, the branches
  and the step of a conflict get entries of the map". The intent's
  own copy of the reason was not mended: a new finding below
  (POS.1680).
- **FND.2830: verified resolved.** SOL.0180 at diverged names `/save`
  with the step of a conflict (SOL.0840) or a branch where the work is
  to stay apart, POS.1690 cited for the roles.
- **FND.2840: verified resolved.** POS.1360 names no End Game; the
  rule stands alone.

## Findings

### FND.2760 [medium] [contradiction] - POS.0120 says a position is dated once and carries no trial, measurement, count or plan; POS.0220 carries two dates again and most positions born or rewritten since 5.38 carry two to five, with counts, trials and the plan of a change under way
- **Known as:** FND.2760 (reopened)
- **Location:** 10-intent.md POS.0120 ("it is dated once ... What does
  not belong in it is the way to it: why it was changed, what was said
  on the way, trials, measurements, counts, findings settled ... Dated
  once means one date, the day the position took its present shape";
  a thread "carries ... the plan of a change under way") against:
  POS.0220 (2026-11-02 and 2026-11-08, the widening of the scripts);
  POS.0250 ("The English word held in every language until
  2026-11-08, when a Czech BRD read ... to its stakeholders"); POS.0400
  ("decided 2026-09-05" and "the principal's answer, 2026-11-01");
  POS.0710 ("the principal's word, 2026-11-01"); POS.0830 (October
  2026, 2026-11-07, 2026-10-02, 2026-10-09, 2026-11-01); POS.0940
  ("Decided 2026-08-29, the exception lifted 2026-11-08"); POS.1040
  (2026-09-14, 2026-10-09, 2026-10-17, 2026-11-01); POS.1100
  (2026-11-01 twice, 2026-09-05, 2026-11-06); POS.1190 (2026-09-18,
  2026-11-01, "six trial questions"); POS.1590 ("2026-11-07; the
  design had said the opposite of the skip since 0.39"); POS.1750
  ("Present shape 2026-10-23 ..., the tests since 2026-11-07");
  POS.1880 ("Decided 2026-10-24; built and verified by probes the same
  day", "2026-11-01"); POS.1930 ("some 7 000 lines of Python", "built
  2026-11-06 and 2026-11-07, 221 tests at the mining"); POS.1970 ("a
  pull request from a stranger waited three days unseen ...
  (discussion #7, pull request #8, 2026-11-06)"); POS.1980 ("verified
  on 2026-11-07 on a clone without it, the tests, the status, the
  ledger, the light check of a project and both hooks unchanged"; "The
  order: this round written, the engine prepared with the project
  still inside and the cut tried on a copy, the project's repository
  born before the engine lets the directory go, then the first
  release"; "The principal's word of 2026-11-01, decided 2026-11-07");
  POS.1990 ("Present shape 2026-11-02 ... accepted into the engine
  from pull request #8 on 2026-11-08"). Older positions the fix of
  5.38 did not reach and that carry the same: POS.0190 (2026-09-26,
  2026-09-14), POS.0950 (2026-09-16, 2026-09-18, 2026-10-04,
  2026-10-09), POS.1460 (2026-09-14, 2026-10-03, 2026-09-05,
  2026-10-09, with the incident of 2026-10-03 told in full), POS.1470
  (2026-09-05, 2026-09-29, 2026-10-09).
- **Issue:** The rule and the practice cannot both hold, as at 5.37;
  the fix of 5.38 moved sixteen positions and the next thirteen
  positions written followed the thirty that were not moved. Two of
  them carry what POS.0120 sends to a thread in so many words: the
  plan of the cut in POS.1980 reads as an order still ahead, while
  POS.0940, three positions above, says the exception was lifted on
  2026-11-08; a reader cannot tell from the intent whether the cut has
  happened. POS.1930 carries a count that was true on one day ("221
  tests at the mining") and will be false at the next test added.
- **Why it matters:** POS.0120 is the one place that says what a
  position may carry, and the model in front of the writer of the next
  position is the positions, not the rule; the history, which
  POS.0310 makes the single primary of the way to an item, holds less
  than the positions do. A plan of a change inside a position is the
  case the rule names first, since it goes stale the day the change
  lands.
- **Suggested fix:** The way chosen at 5.38, carried through: each
  position named keeps the date of its present shape alone, and the
  earlier dates, the counts, the trials and the plan of the cut go to
  its history at the next write that touches it, `Was` carrying the
  words (the plan of POS.1980 to THR.0780, where it already stands);
  or, if the dates per clause are wanted after all, POS.0120 reworded
  to what is wanted, so that the rule stops failing at every round.
  Which of the two is the principal's; the second is the smaller
  write, the first the one he took last time.

### FND.4070 [medium] [contradiction] - POS.1090 says `/check`, `/critique`, `/challenge` and `/research` "stay Claude's to start"; POS.0400 and POS.1140 say a reviewer runs on the principal's word alone and never on Claude's judgement
- **Location:** 10-intent.md POS.1090 ("Maps, reports and rosters
  (`/forge`, `/ledger`, `/check`, `/critique`, `/challenge`,
  `/research`, bare `/recipe`, the roster) stay Claude's to start,
  since he is meant to propose them") against POS.0400 ("A reviewer
  runs on the principal's word alone because a run costs tokens ...;
  what is ruled out is a run on Claude's own judgement"), POS.1140 ("a
  run by hand"; `single-source-of-truth` "run on the principal's
  word"), POS.0540 ("a run by hand"), POS.1860 (the plan shown and
  confirmed "before anything is searched").
- **Issue:** One position makes the four commands Claude's to start,
  the others make every run of them the principal's. The sentence of
  POS.1090 may mean that the four need no guard because Claude is
  meant to propose them, but "stay Claude's to start" is what it says,
  and two competent readers act differently on it: one proposes a
  critique, the other runs it.
- **Why it matters:** This is the line between proposing and acting
  that the whole Review group rests on, and the one position of the
  harness contradicts it in the place a reader goes to learn which
  commands start on whose word.
- **Suggested fix:** POS.1090: "Maps and rosters (`/forge`, `/ledger`,
  bare `/check`, bare `/critique`, bare `/challenge`, bare `/recipe`)
  stay Claude's to start, since he is meant to propose them; a run of
  a reviewer or a research is proposed by him and started on the
  principal's word (POS.0400, POS.1140, POS.1860), unguarded because
  the word is in the procedure."

### FND.4080 [medium] [contradiction] - The design says the forge's own project is a repository of its own beside the engine, and that the cut is pending
- **Location:** 40-solution-design.md SOL.0500 ("The forge's own
  project, `projects/forge`, is a repository of its own beside it,
  public under the same account and named `forge` (SOL.0930)"),
  SOL.0680 ("`projects/<slug>/.gitignore`, the forge's own project's
  like any other's, POS.1980"), SOL.0510 ("the forge's own project
  before its cut and nothing after it") against SOL.0930 ("Prepared
  2026-11-08 on the branch `cut-forge-project`: the scripts, the
  tests, CLAUDE.md, the skills and the recipes; the cut and the first
  release pending (THR.0780)") and SOL.0730 ("the lines on
  `projects/forge/renders/**` and its published files leave it at the
  cut of POS.1980, when the forge's own project takes
  `templates/gitattributes` like every project").
- **Issue:** Three items describe the cut as made, in the present
  tense; the item that owns it says it is pending, and the item on the
  attributes speaks of it as a moment to come. The design is "the
  solution as it stands today", so one of the two tenses is wrong, and
  the reader of SOL.0930 alone, the owner, is told the wrong one if
  the present tense of SOL.0500 is right.
- **Why it matters:** Whoever rebuilds the engine from the design must
  know whether `.gitignore` re-includes the project and whether
  `.gitattributes` carries the project's lines; the two states of the
  design give opposite answers.
- **Suggested fix:** SOL.0930 says the state of the cut once, as it
  is on the day of the write ("cut on <date>; the first release in
  the new shape pending" or "pending"), and SOL.0730 is worded in the
  tense of what holds ("left it at the cut of POS.1980; the forge's
  own project carries `templates/gitattributes` like every project",
  or the future kept if the cut is not made); SOL.0500 and SOL.0680
  then agree with the owner.

### FND.4090 [low] [contradiction] - POS.1680 still gives the record driver, let go in REJ.0340, as a reason for threads as files
- **Location:** 10-intent.md POS.1680 ("Why: two people on different
  threads never conflict, Claude reads only the threads he needs, and
  the driver need not handle blocks with an inner state") against
  POS.1560 ("A way of its own for the record files, a driver merging
  them as sets of records, is not taken (REJ.0340)") and REJ.0340.
- **Issue:** The third reason of the position rests on a mechanism the
  same document says the forge does not have. FND.2820 mended the
  design's copy (SOL.0720: "so that no merge handles a block with an
  inner state"); the intent's copy stayed.
- **Why it matters:** A reason that cites a dropped mechanism reads as
  a reason the position still rests on; the next reader of REJ.0340
  asks which of the two is true.
- **Suggested fix:** POS.1680: "and no merge need handle a block with
  an inner state", as SOL.0720 has it.

### FND.4100 [low] [contradiction] - SOL.0520 says the git hook's cases are its own `--test`; SOL.0900 says they moved out of the hook into the suite
- **Location:** 40-solution-design.md SOL.0520 ("Its cases are its own
  `--test`, run before it is registered and after every change;
  `--judge` prints the verdict of one command") against SOL.0900
  ("`test_hook_git.py`, the 171 built-in cases of the git hook with
  their verdict, moved out of the hook").
- **Issue:** The item of the wall and the item of the tests describe
  two places for the same cases; one of them no longer exists.
- **Why it matters:** A contributor who changes the hook reads
  SOL.0520 first and looks for a flag the script has lost.
- **Suggested fix:** SOL.0520: "Its cases are `tests/test_hook_git.py`
  (SOL.0900), run at every push; `--judge` prints the verdict of one
  command."

### FND.4110 [low] [contradiction] - SOL.0130 counts four genres and SOL.0920 adds a fifth; SOL.0120 lists the BRD's pair among its files and not the user stories'
- **Location:** 40-solution-design.md SOL.0130 ("The genres today are
  `presentation`, `readme`, `release-notes` and `screenplay`
  (POS.1530), each invoked as `/recipe <genre>`") against SOL.0920
  ("the recipe genre `user-stories-export` with its skeleton
  `templates/recipe-user-stories-export.md`"); SOL.0120 Where
  (`states/brd.md`, `templates/brd.md` listed; `states/user-stories.md`
  and `templates/user-stories.md` not) against SOL.0920 ("one more
  definition the dispatcher reads from disk" in the shape of
  SOL.0120).
- **Issue:** The roster item of the genres was brought to four at the
  last fix and the fifth was added in a member's item without the
  roster following; the roster item of the definitions took the BRD's
  files and not the user stories'. Two readers of the design get two
  lists of what `/recipe` and `/forge` dispatch to.
- **Why it matters:** The roster items are what a reader opens to
  learn what the dispatchers know; a member's item is found only by
  one who knows the member.
- **Suggested fix:** SOL.0130 lists five, or says "the genres are the
  files of `.claude/skills/recipe/genres/`, one per genre, listed
  nowhere else", as POS.1080 says of the definitions; SOL.0120's Where
  either names both new pairs or neither, the members' items (SOL.0850,
  SOL.0920) owning their files, and says which it does.

### FND.4120 [low] [contradiction] - POS.0760 defines the engine as the core together with `projects/forge`; POS.0940 and POS.1980 say the engine tracks no project and the forge's own project is one among the others
- **Location:** 10-intent.md POS.0760 ("The engine, the core together
  with `projects/forge`, is public and contains nothing sensitive and
  no instance facts") against POS.0940 ("The engine does not know the
  projects ... The engine's own project was the one exception to
  this, tracked by the engine; it is one repository among the others
  since POS.1980") and POS.1980 ("`projects/forge` is one project among
  the others, under git like them ... the last exception to POS.0940
  goes with it").
- **Issue:** What "the engine" is, a term of fifty positions, is given
  two extents in the same document: with the forge's own project
  inside it, and without any project.
- **Why it matters:** POS.0980 and POS.0950 draw the public boundary
  by "the engine"; which files it covers depends on which definition
  the reader took.
- **Suggested fix:** POS.0760: "The forge is split into a public
  engine, the forge's own project as a public repository beside it
  (POS.1980) and user projects in repositories of their own. The
  engine and the forge's own project contain nothing sensitive and no
  instance facts (POS.0950, POS.0980) ..."

### FND.4130 [low] [ambiguity] - POS.0060, the owner of the language rule, places the work specification in neither of its two lists
- **Location:** 10-intent.md POS.0060 ("the artefacts of the chain,
  intent, assignment and every later layer, are written in the
  language its project file declares ... Everything else a project
  holds, records, state, research and recipes, is always English")
  against POS.1520 ("The specification is written in the project's
  language as the artefacts are, the file in whatever language the
  work needs, which `## Making` says").
- **Issue:** A work specification is not an artefact of the chain and
  is none of the four kinds the second list names; a reader of the
  owner is left to choose, and the two readings differ. POS.1520
  decides it, but in the member and not in the owner.
- **Why it matters:** The language of a document is read off POS.0060
  by whoever creates one; the one kind it does not place is the one
  most often created by hand.
- **Suggested fix:** POS.0060, after the sentence on the artefacts: "a
  work specification follows the artefacts, its file the language its
  `## Making` says (POS.1520)".

## Recommendations
<!-- Not findings, not gates: wording that is hard to test, groups that
overlap, items that could be split. The principal may ignore these
without recording anything. -->
- POS.0100 gives the solution design and the BRD as the layers added
  without renaming ("was ... was"); the user stories,
  `35-user-stories.md` (POS.1990), are the third and the doubled verb
  could go.
- The section "Candidate structure for the layer below" stands with a
  note that the layer exists; its template says the section is
  "deleted once the layer exists and leads". Either "leads" means
  something the design, a draft, does not yet do, which the section
  could say in half a sentence, or its content (no assignment is
  derived; the engine itself is the handover) belongs in a position.
- POS.1940 and POS.1590 both state that the fixture's project file
  carries `fixture: true`; one could own and the other cite.
- POS.1750 "a conflict in a history, in `decisions.md` or in an index
  is two tails and is settled by keeping both" against REJ.0290, where
  the same index entry changed on both sides is settled in the step of
  a conflict. From the last run.
- POS.1430: who says whether a kind "needs a trial on real work" and so
  takes the order of POS.1780 rather than the position first is not
  said. From the last run.
- POS.0850 and POS.1460 both carry the rule that a yes with a question
  is not a yes, each with an incident of its own; one could own the
  rule. From the last run.
- POS.0850 gives six verdict words and a line of five letters; how
  `obsolete` is given is not said. From the last runs.
- SOL.0460's sentence "After the first and the second release of the
  brief `collaboration` the pages ... are regenerated and the
  migration, the branches and the step of a conflict get entries of
  the map" is a plan whose moment has passed by the ledger's
  documentation runs of 2026-11-01; the item could say what holds or
  drop it.
- SOL.0840 repeats SOL.0780's sentence on the push of a clean
  repository that is ahead and a branch without an upstream, word for
  word; SOL.0510 cites SOL.0780 for it and SOL.0840 could too.
- SOL.0530 cites TBC.0020 for the walk of the parts marked "Not built",
  where TBC.0020 is about the check that keeps the design true against
  what realises it; and no item of 0.63 carries the mark, so the rule
  of the head stands for a future release, which the head could say.
  From the last run.
- `00-brief-tests.md` 0.1 cites POS.1760 for "a red test before a
  release stops it"; the intent carries no POS.1760 since REJ.0350.
  The brief is the principal's text and stands; a reader who follows
  the address finds nothing, and POS.1750 is where the sentence now
  lives.
- The brief `collaboration` 0.9 and the brief `brd` 0.5 stand as at
  the last run; the two remarks made on them then still apply.
