---
date: 2026-11-17
project: forge
check: documentation
target: the engine (docs/ at the engine root, the map projects/forge/docs-map.md)
reviewer: the documentation run
---

# Check (documentation) — the engine — 2026-11-17

25 findings: 22 new, 3 known reported under their IDs; 2 findings resolved by this map. The run on `main` after step 1 of the cut of CLAUDE.md: 108 entries, 106 pages regenerated, 2 new (`docs/about/threads.md`, `docs/use/set-a-matter-aside.md`), none kept, none removed; the check of the pages found a long dash on four pages, each was regenerated once and the second check found no failure; one page, `docs/reference/commands.md`, was written a second time by its own writer on its report of a slip; the index derived at version 7.12. The planner's report, the map's Unowned and Did not fit sections and the writers' reports are the sources of what follows; what the run read again on disk is said in each finding, the rest stands as the agent reported it. The Unowned matters and the disagreements of map and owner are medium, an unrecorded reason is low.

## Findings

### FND.4910 — medium — Three items of the solution design say what the operating layer no longer does
- **Where:** `projects/forge/40-solution-design.md`, read again by the run: SOL.0010 (the core carries "the layout ... and the list of commands"), where CLAUDE.md, Repository layout and Commands, names `.claude/reference/repository-layout.md` and `.claude/reference/commands.md` for the engine's root and the table; SOL.0030 ("four lines of conduct"), where the header of `scripts/hook-walkthrough.py` says five; SOL.0510 ("`forge-save forge` is two commits ... the tag on the engine alone"), where the header of `scripts/forge-save.py` and POS.1980 put the tag on both repositories under one name. The pages `docs/about/how-the-rules-are-held.md`, `docs/extend/what-it-is-made-of.md`, `docs/about/projects-and-the-engine.md` and `docs/reference/scripts.md` take the operating layer's wording or say nothing.
- **Rule:** POS.0120: where an item and what realises it say different things, that is a finding.
- **Fix:** The three items brought to the operating layer's wording; SOL.0010 together with the folder `.claude/reference/`, which THR.0240 says is worked into the intent and the design when a phase of the slimming is done.

### FND.4920 — medium — POS.0950 says a subagent sees the session's whole context; CLAUDE.md, Isolated reviewers, says it sees nothing of the conversation
- **Where:** `projects/forge/10-intent.md`, POS.0950, its last sentence ("A subagent sees the session's whole context, CLAUDE.md as the session read it and the assistant's memory included"); CLAUDE.md, Isolated reviewers, the first paragraph ("it sees nothing of the conversation"). Both read again by the run. `docs/about/how-the-rules-are-held.md` says a subagent sees nothing of the conversation and receives the core as the session read it, the instance file and the assistant's memory.
- **Rule:** POS.0120.
- **Fix:** POS.0950 names what a subagent receives in place of "the session's whole context".

### FND.4930 — medium — SOL.0840 says the ledger script reports a version given twice; the ledger template lists no such report
- **Where:** `projects/forge/40-solution-design.md`, SOL.0840 ("A version given twice and an ID taken twice are settled as POS.1790 says, the ledger script reporting both"); `templates/ledger.md`, Reports (an ID defined twice, a closed thread touched by a later commit, a THR cited with neither a thread file nor a closed record). Both read again by the run; the map lists it under Did not fit.
- **Rule:** POS.0120.
- **Fix:** The owners say one thing: the template lists the report of a version given twice, or SOL.0840 names the ID alone.

### FND.4940 — medium — The header of forge-ledger.py and the ledger template name different sources for the Research table
- **Where:** `scripts/forge-ledger.py`, the header ("the resource indexes (Sources, Research)"); `templates/ledger.md`, Research ("one row per note in research/, or per bundle ... Date and Derived from out of the front-matter. What a note answers lives in research/00-INDEX.md, never here"). Both read again by the run. `docs/about/the-ledger.md` follows the header's wording.
- **Rule:** CLAUDE.md, Persistence, Portability: each script carries its help in its module docstring; prime directive 10.
- **Fix:** The header says what the script reads for the Research table, as the template has it.

### FND.4950 — medium — Two owners say different things on what the player page's sidebar lists for a video
- **Where:** `projects/forge/40-solution-design.md`, SOL.0660 ("a sidebar listing the files in the order of their names, by the title of each file's title card"); `.claude/skills/recipe/genres/screenplay.md`, point 11 ("the section the video belongs to and its name per language, what the viewer will learn, listed in place of the title card's title"). Both read again by the run. `docs/about/the-screenplay-and-its-player.md` states the grouping as its entry gives it and repeats the genre's wording.
- **Rule:** POS.0120.
- **Fix:** SOL.0660 says what the sidebar lists as the genre and the player's script have it.

### FND.4960 — medium — Claims the map asked for and no named input carries, in eighteen entries
- **Where:** as the writers report, each having left the claim off the page or kept it to the owner's words:
  - `docs/about/the-check.md`: "`/save` runs `light` unless told otherwise", "`/release` runs `light`", "for the engine `engine` too", a check "for a single kind of artefact"; what a save and a release run left CLAUDE.md for the save and the release skills, which are not among the entry's inputs.
  - `docs/about/where-it-is-going.md`: "one principal per instance for now".
  - `docs/about/persistence-in-git.md`: the three ways of merging.
  - `docs/use/settle-a-conflict.md`: "as for any change" after the `changed` record; "by a merge request where it needs no hand", whose owner the entry's must-not excludes.
  - `docs/use/work-on-a-branch.md`: a documentation run and a publish made from `main` only; only the release has an input.
  - `docs/use/upgrade-the-engine.md`: "the findings are walked one at a time".
  - `docs/about/sources-and-research.md`: "one note per card per engine", where CLAUDE.md, Document kinds, says "per question"; "immutable from its filing"; "how it is planned and checked".
  - `docs/about/versioning-and-history.md`: a major "of an intent", where POS.0300 speaks of the forge's own intent.
  - `docs/about/the-tests.md`: "a red test stops it" and "before anything else" for the release; "thousands of lines of Python".
  - `docs/about/the-challenger.md`: "no stake in the principal being right" of every challenger, which POS.0420 says of the first persona; "healthy" for a rejected challenge.
  - `docs/start/install.md`: `/ingest` as the command that needs the conversion tool; "the state map" as the home of the line on what waits on GitHub.
  - `docs/reference/scripts.md`: for `forge-save.py` "the tag on the engine alone", against the script's header (FND.4910).
  - `docs/about/the-brief.md`: the See also sentence for Languages, "why a brief keeps its language", while both pages say that reason is not recorded.
  - `docs/about/renders-and-recipes.md`: "a work product is not a render"; the security policy and the code of conduct as "no render either"; what the published companion holds.
  - `docs/start/what-it-is.md`: "by interview"; outputs "for every audience".
  - `docs/about/working-together.md`: the first reason, "the ledger was the one file present at every collision", where the intent names the ledger and the record files.
  - `docs/about/the-brd.md`: the user stories, of which no input of the entry says anything.
  - `docs/about/projects-and-the-engine.md`: "access per project" as a stated reason; the tag of a release, on which POS.1980 and SOL.0510 differ (FND.4910).
- **Rule:** The documentation contract: every claim of a `says` has an input that carries it; the map is remade from the owners at the next run.
- **Fix:** At the next run of the planner: each claim cut from its entry, or the owner that carries it added to the entry's inputs.

### FND.4970 — medium — Claims cut from the map because no input carries them since the cut of CLAUDE.md
- **Where:** the planner's report, Did not fit: why the record of the mining stands in the intent's history (`docs/about/the-brief.md`); the count of the hook's lines of conduct (`docs/about/working-methods.md`, `docs/about/how-the-rules-are-held.md`); "document skills", "expensive" and the offer of `/pull` (`docs/use/publish-a-designed-file.md`); the parts of a report's name (`docs/use/critique-the-documents.md`, `docs/use/challenge-the-thinking.md`); the companion and the library lines (`docs/reference/document-kinds.md`). Not read again by the run.
- **Rule:** The documentation contract: every claim of a `says` has an input that carries it. A rule that leaves CLAUDE.md stands at its new owner (THR.0240, step 1 of the cut).
- **Fix:** The principal's judgement of each: the fact has an owner today and the entry names it as an input, or the fact is no longer the documentation's to say.

### FND.4980 — medium — Unowned: a sentence saying what Claude is
- **Where:** `docs/start/what-it-is.md`; the map, Unowned. The outline asks for "an AI assistant"; the owners say "Anthropic's agent for the command line" of Claude Code (CLAUDE.md, What this workspace is) and "AI" of the reviewers alone. The page follows the entry's wording.
- **Rule:** Nothing is invented to fill a gap; a fact without an owner waits for the principal to give it a home (the document skill, step 7).
- **Fix:** One sentence in the owner the principal names.

### FND.4990 — medium — Unowned: that the teaching videos are real sessions cut to a few minutes, as a pinned fact
- **Where:** the map, Unowned; `docs/start/what-it-is.md`, from whose entry the claim was cut (FND.4350). The pinned facts of `projects/forge/recipes/readme.md` say what each video shows; the writer of `docs/start/first-result.md` found the sentence that every video is a real session in the recipe's Instructions.
- **Rule:** As FND.4980.
- **Fix:** A pinned fact of the readme recipe, or the Instructions' sentence named as an input of the entry, or the claim stays cut.

### FND.3920 — medium — The position on the harness says web access is approved by the user per domain; `.claude/settings.json` records no such rule
- **Where:** POS.1090 and SOL.0520 against `.claude/settings.json`; the map, Did not fit. `docs/about/how-the-rules-are-held.md` says what the settings hold and makes no claim on web access.
- **Rule:** POS.0120.
- **Fix:** As filed on 2026-11-08.
- **Known as:** FND.3920, still open

### FND.3940 — medium — Two terms of the glossary have no owner that defines them in one sentence
- **Where:** "session" and "harness": the map, Unowned. Both left the glossary's tables; `docs/reference/glossary.md` names them in a closing note without a gloss, and the pages that need "harness" gloss it in the writer's own words (`docs/about/how-the-rules-are-held.md`, `docs/about/the-principal-and-claude.md`, `docs/extend/change-a-documentation-page.md`).
- **Rule:** The documentation contract: a term of the forge is glossed once on a page that needs it, from its owner.
- **Fix:** As filed on 2026-11-08: one sentence each, in the owner the principal names.
- **Known as:** FND.3940, still open

### FND.3630 — low — The roster page of the templates carries a creating command the skeletons do not name for nine templates
- **Where:** `docs/reference/templates.md`: no skeleton comment and no skill names a creating command for `CLAUDE.local.md`, the intent, the assignment, the BRD, the user stories, the solution design and the three definition skeletons; the page says "no procedure is named in the skeleton". On `docs/reference/scripts.md` the column is gone from the entry, which asks for a command only where a docstring names one; which command runs each script stays in the map's Unowned.
- **Rule:** The documentation contract: a roster page asks for no column its owners do not state.
- **Fix:** Each skeleton's comment names the command that makes a file from it, or the field goes from the page's entry.
- **Known as:** FND.3630, still open for the templates page; resolved for the scripts page by this map

### FND.5000 — low — The writer's definition does not say how a page that exists is overwritten, and one writer read its old page whole
- **Where:** `.claude/agents/docs-writer.md`; the writers' reports. The tool that writes a file refuses to overwrite a file not read; most writers read the first line of the old page and said so, the writer of `docs/about/working-methods.md` read the old page and names what of it the inputs no longer support.
- **Rule:** `.claude/agents/docs-writer.md`: a writer sees no other page; a page is made from its entry and its inputs alone.
- **Fix:** The definition says that an existing page is opened at its first line only, or the run removes the pages to be regenerated before the writers start.

### FND.5010 — low — Owner wording the writers had to read around
- **Where:** as the writers report, not read again by the run: `.claude/skills/recipe/SKILL.md`, where a genre file's arguments are "those following the genre name" and the `argument-hint` puts the project slug second (`docs/extend/add-a-recipe-genre.md`); `scripts/forge-cite.py`, whose header says "most of its sources or a third of its sentences" where the code counts against the note that has fewer (`docs/about/another-model-family.md`); `.claude/skills/forge/states/solution-design.md`, Map, the last area, "and left to the file or to the one who realises", and its reading of what realises a thing "as it stands" beside POS.1400's "never a source of its own design" (`docs/about/the-solution-design.md`); POS.1450, "the map and the intent", where the document skill says map and owner (`docs/about/the-documentation.md`); "the map" without a qualifier in POS.1740, SOL.0800 and CLAUDE.md, Persistence (`docs/about/upgrades-and-migration.md`, `docs/about/working-methods.md`, `docs/about/the-ledger.md`); "the three conversions" of the solution design beside the four converters the layout lists (`docs/extend/add-a-script.md`).
- **Rule:** POS.0120; prime directive 10.
- **Fix:** The principal's judgement of each; a mend lands in the owner.

### FND.5020 — low — Reason not recorded: rules of a thread
- **Where:** `docs/about/threads.md`, `docs/about/stable-ids.md`: why a thread is born on the principal's command only; why it has no version and no history of its own; why it is never moved, renamed or deleted; why the history records only its birth and its closing; why a thread has a prefix of its own (POS.1680, POS.0230, `.claude/skills/thread/SKILL.md`, SOL.0960).
- **Rule:** The documentation contract: a page says that a reason is not recorded rather than inventing one.
- **Fix:** The principal's reasons, one sentence each, in the owners named.

### FND.5030 — low — Reason not recorded: two rules of the critic and two of the reviewers
- **Where:** `docs/about/the-critic.md`: why sharp and few beats thorough and long; why each artefact is judged against its own definition. `docs/about/isolated-reviewers.md`: why nothing blocks; why a new lens, persona or check comes only by the principal's decision.
- **Rule:** As FND.5020.
- **Fix:** As FND.5020.

### FND.5040 — low — Reason not recorded: two rules of the assignment and two of the brief
- **Where:** `docs/about/the-assignment.md`: why the forge names no word of another language; why success criteria are wanted and not compulsory. `docs/about/the-brief.md`: why the record of the mining stands in the intent's history; why how much of a brief is mined is a judgement and never a metric.
- **Rule:** As FND.5020.
- **Fix:** As FND.5020.

### FND.5050 — low — Reason not recorded: what the tests leave untested
- **Where:** `docs/about/the-tests.md`: why the skills, the agents, the text of CLAUDE.md, the run of the screenplay script and what the outside tools return are not tested (the design says "by the brief"); why no test runs on a live repository; why the tests are in proportion.
- **Rule:** As FND.5020.
- **Fix:** As FND.5020.

### FND.5060 — low — Reason not recorded: why a work product is two files
- **Where:** `docs/about/the-work-product.md`: POS.1520 gives the division, the file the content and the specification the way and the why, and no reason for it; the page's own `line` asks the question.
- **Rule:** As FND.5020.
- **Fix:** As FND.5020.

### FND.5070 — low — Reason not recorded: the player page's choice, and the format of a picture
- **Where:** `docs/about/the-screenplay-and-its-player.md`: why the fixed page with the embedded list was chosen over a generated index file, a course recipe with an outline or folders as sections; no price is recorded for three of the four choices of the conversion. `docs/about/renders-and-recipes.md`: why the picture's format is the principal's choice recipe by recipe.
- **Rule:** As FND.5020.
- **Fix:** As FND.5020.

### FND.5080 — low — Reason not recorded: two rules of a record, one of the intent
- **Where:** `docs/about/versioning-and-history.md`: why a record is written in the same step as the change; why what the reader must do (`Action`) is never derived. `docs/about/the-intent.md`: why the intent is never finished.
- **Rule:** As FND.5020.
- **Fix:** As FND.5020.

### FND.5090 — low — Reason not recorded: what a project wants documented, and feedback from the recipients
- **Where:** `docs/about/the-documentation.md`: why what a project wants documented beyond what the planner reads is no setting of its own (REJ.0500). `docs/about/how-a-thought-travels.md`: why feedback from the recipients has no channel of its own (CLAUDE.md, Document chain).
- **Rule:** As FND.5020.
- **Fix:** As FND.5020.

### FND.5100 — low — Reason not recorded: the edges of the forge's scope
- **Where:** `docs/about/what-it-is-and-is-not.md`: why Claude is an extension and not a supplier; why delivery lies outside the scope. `docs/about/where-it-is-going.md`: why the question of a delivery side is deliberately undecided (POS.0780).
- **Rule:** As FND.5020.
- **Fix:** As FND.5020.

### FND.5110 — low — Reason not recorded: four rules of the BRD and the user stories
- **Where:** `docs/about/the-brd.md`: why the phasing is always stated. `docs/about/the-user-stories.md`: why the solution design cites the stories and never the reverse; why the five labels of a story are fixed in English. `docs/about/the-document-chain.md`: why user stories made from someone else's document are a work product, the reason being recorded for the BRD only.
- **Rule:** As FND.5020.
- **Fix:** As FND.5020.

### FND.5120 — low — Reason not recorded: why those two sensitive paths and no others
- **Where:** `docs/about/how-the-rules-are-held.md`: the deny rules of `.claude/settings.json` name two paths; SOL.0520 names them and gives no reason for the choice.
- **Rule:** As FND.5020.
- **Fix:** As FND.5020.

## Resolved by this map
- FND.4350: the reason of Intent-first is cut from the entry of `docs/about/working-methods.md`, which asks the page to say none is recorded; "real sessions cut to a few minutes" is cut from the entry of `docs/start/what-it-is.md` (the fact itself: FND.4990); POS.1750 is among the inputs of `docs/use/settle-a-conflict.md` and the two-tail case is worded as it has it. By the planner's report; the claims of the same kind found in this run are FND.4960.
- FND.4900 of the project check of 2026-11-17: the map's heading is `# Documentation map — engine` and nothing stands between it and `## Paths`. Read by the run.

## Not raised
- FND.3580 (parked, DEC.0390): how a merge request's branch is fetched onto the integrator's clone; the map lists it under Unowned.
- FND.3400 (open): a reason for the rule that a project records no engine version; the map lists it under Unowned and `docs/about/upgrades-and-migration.md` says the reason is not recorded.
- The reasons the four earlier reports list as wanted (FND.3180 to FND.3500, FND.3690 to FND.3800, FND.3960 to FND.4050, FND.4360 to FND.4380): every page that reads such an owner says the reason is not recorded; nothing new of them.
