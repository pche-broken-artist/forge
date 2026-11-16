---
date: 2026-11-16
project: forge
check: single-source-of-truth
target: the engine root
reviewer: check single-source-of-truth (isolated context)
---

# Check (single-source-of-truth) — the engine root (C:\pche\_dev\forge-of-thought) — 2026-11-16

11 findings (7 new, 4 reopened in a residue: FND.4210, FND.4240, FND.2880, FND.4220); 120 files of the operating layer read from disk: CLAUDE.md, the 2 files of `.claude/reference/`, `.claude/settings.json`, 43 skill files (27 commands, 6 state files, 5 genres, 4 contracts, the walkthrough), 14 agent files, 31 templates (`html-player.html` by its header comment), the help headers of 28 scripts. Beside them: the single-source rows of the Findings table of C:\pche\_dev\forge-of-thought\projects\forge\ledger.md, my reports of 2026-11-08 and 2026-10-25 in full, and the headings of DEC.0170, DEC.0180, DEC.0340 and DEC.0460. Of the 2026-11-08 findings FND.4190, FND.4200, FND.4230, FND.4250, FND.4260, FND.4270, FND.4280, FND.4290, FND.4300 and FND.2890 stand resolved on disk.

## Findings

### FND.4790 — medium — The Handing over method is restated in the work skill and in three definitions, beside their citation of it
- **Where:** C:\pche\_dev\forge-of-thought\.claude\skills\work\SKILL.md:37-41 ("handed over, Claude works it alone from what he was given, from research and from the sources, and returns a proposal with his assumptions and choices listed, each choice with what it was chosen against"), nearly word for word C:\pche\_dev\forge-of-thought\CLAUDE.md:165-170, although the same skill says at :9-16 that the two ways of composing are "cited and never repeated here"; C:\pche\_dev\forge-of-thought\.claude\skills\forge\states\brd.md:169-178 (returns the draft with the list of what he assumed; "nothing is derived from the draft before the principal has judged it"); C:\pche\_dev\forge-of-thought\.claude\skills\forge\states\user-stories.md:99-101 (the same closing sentence); C:\pche\_dev\forge-of-thought\.claude\skills\forge\states\solution-design.md:100-101 ("A choice Claude made and the principal has not judged says so in plain words at the item, until he has judged it") against CLAUDE.md:170-173
- **Rule:** One owner per rule, cited by path (CLAUDE.md, prime directive 10; POS.1070); the owner is CLAUDE.md, Working methods, Handing over, which each of the four files already cites.
- **Fix:** Cut each passage to what is the file's own (the BRD's provenance map and list of what must be supplied, the stories' cut agreed first, the work skill's "the way he chooses") and the citation "(CLAUDE.md, Working methods, Handing over)", the proposal's content and the no-derivation rule standing in CLAUDE.md alone.

### FND.4800 — medium — The BRD check's Lens restates the rules of the BRD's definition beside its citations of it
- **Where:** C:\pche\_dev\forge-of-thought\.claude\agents\check-brd.md:34-43 (a BR and an NFR end with their parent `(REQ.NNNN)` or `(POS.NNNN)`, an NFR with its category where the parent named none; the place cited in a source is a turn of the principal's side) against C:\pche\_dev\forge-of-thought\.claude\skills\forge\states\brd.md:211-219; check-brd.md:51-56 (an ASM that answers what a TBC asks; a category carries a value or a TBC with an owner, never the skeleton's wording; a TBC has an owner, `unassigned` a valid open state, and says whether it blocks estimation) against brd.md:91-92, :206-210 and :174-176; check-brd.md:57-59 (no item depends on a link) against C:\pche\_dev\forge-of-thought\.claude\skills\forge\states\assignment.md:131-132
- **Rule:** A Lens names the owner of each rule and never restates it (C:\pche\_dev\forge-of-thought\.claude\skills\check-contract\SKILL.md:37-39; POS.1120; POS.1070). The sibling Lens, C:\pche\_dev\forge-of-thought\.claude\agents\check-user-stories.md:22-25 and :41-46, was cut to citations by FND.4200; this one was not part of that finding.
- **Fix:** Cut items 2 to 4 to what is verified and where the rule stands ("every item has its parent, every TBC its owner and its blocking, every category its value or TBC, as the Requirement style of `.claude/skills/forge/states/brd.md` has them; every breach a finding"), keeping only what is the check's own (what is read as a fact, what is residue).

### FND.4210 — low — The BRD template's comments still restate the definition in four other places
- **Where:** C:\pche\_dev\forge-of-thought\templates\brd.md:60-61 ("Steps in the active voice, present tense") against C:\pche\_dev\forge-of-thought\.claude\skills\forge\states\brd.md:221-223; templates\brd.md:98-100 (a mandatory area is never silent; `Roster: none` and one row) against brd.md:37-39 and :116-118; templates\brd.md:138-141 (Phasing mandatory, "even as everything in the first phase") against brd.md:57-58; templates\brd.md:164-167 (an entity says its states and its source system; "how it is taken is the solution design's, and no attribute stands here") against brd.md:123-126, nearly word for word
- **Rule:** POS.1070; the template says what comes out, the definition owns the rules (CLAUDE.md, Document chain); the template's own header at :11-12 names the definition as the owner of "the rules of every section". The three passages FND.4210 named are cut; these four are the same pattern in the comments it did not name.
- **Fix:** Cut each comment to what the section holds and one citation of the definition (Requirement style, Inputs, Aim, Map).
- **Known as:** FND.4210, reopened

### FND.4240 — low — The two reviewer contracts still carry their own rule on a rejected finding, and the critic's differs from the owner
- **Where:** C:\pche\_dev\forge-of-thought\.claude\skills\critic-contract\SKILL.md:60-62 ("A rejected finding is re-raised only where the document changed in a way that materially alters the situation") against C:\pche\_dev\forge-of-thought\CLAUDE.md:587-590 ("a rejected one is not raised again"); C:\pche\_dev\forge-of-thought\.claude\skills\check-contract\SKILL.md:64-66 ("an older record's overruled ... reads as rejected") against C:\pche\_dev\forge-of-thought\templates\ledger.md:107-108, the owner of the state words CLAUDE.md names; critic-contract\SKILL.md:63-65 and :93-96 say twice in one file that a new finding carries no ID and the command numbers it
- **Rule:** POS.1070; the fix of FND.4240 (CLAUDE.md, Isolated reviewers, owns the conduct toward a filed finding, the contracts keep only the form of their output). Two descriptions of one rule have drifted: never again, against again where the document changed.
- **Fix:** Decide which holds and state it once in CLAUDE.md, Isolated reviewers; the critic's contract cites it, the check's contract drops the `overruled` gloss for "the state words: `templates/ledger.md`", and the critic's contract says the no-ID rule once, under Output.
- **Known as:** FND.4240, reopened

### FND.2880 — low — The research skill still restates two things the script headers own, beside its citations of them
- **Where:** C:\pche\_dev\forge-of-thought\.claude\skills\research\SKILL.md:149-150 ("An unverifiable URL (403, a timeout) is said so and never counted as a failure") against C:\pche\_dev\forge-of-thought\scripts\forge-cite.py:21-22 and :44-46, five lines after the skill's own "what a dead or mismatched citation means: the headers" (:143-145); research\SKILL.md:121-129 (the hold folder the other engine's profile denies; independence resting on the deny rules and the order of filing, never on the place of the run) against C:\pche\_dev\forge-of-thought\scripts\forge-engine.py:25-45, cited twice within the passage
- **Rule:** POS.1070; a script is described by its header and the skill that runs it cites it (CLAUDE.md, Persistence, Portability); the fix of FND.2880.
- **Fix:** immediate fix: drop the sentence at :149-150, and cut :121-129 to where the return is written, when it moves into the bundle, and "(why: `scripts/forge-engine.py`, header 2a)".
- **Known as:** FND.2880, reopened

### FND.4810 — low — The order of the Waiting list is stated in the ledger skeleton, the ledger script's header and the thread skill
- **Where:** C:\pche\_dev\forge-of-thought\templates\ledger.md:122-126 (the owner: "the open threads, those something waits on first, then by priority, each by its priority and what waits on it in brackets"); C:\pche\_dev\forge-of-thought\scripts\forge-ledger.py:33-37 (the same words, straight after "follow the rule and the list of templates/ledger.md, where each is defined"); C:\pche\_dev\forge-of-thought\.claude\skills\thread\SKILL.md:14-16 ("those something waits on first, then by priority, high to low")
- **Rule:** POS.1070; the pattern of FND.2200, a rule in full beside the sentence that names its owner.
- **Fix:** immediate fix: the header keeps "follow the rule and the list of templates/ledger.md"; the thread skill says "print the open threads from it, in the ledger's order".

### FND.4820 — low — The docs writer restates two clauses of its contract
- **Where:** C:\pche\_dev\forge-of-thought\.claude\agents\docs-writer.md:39-43 ("a reason the inputs do not give is said to be not recorded. An example that shows the shape an owner defines, plainly generic and taken from no project, is a mirror of that owner") against C:\pche\_dev\forge-of-thought\.claude\skills\docs-contract\SKILL.md:44-47 and :52-54, the second word for word
- **Rule:** The docs contract is the one owner of what the two documentation agents share (docs-contract\SKILL.md:7-11; POS.1070); the pattern of FND.2940, in a passage that finding did not name.
- **Fix:** immediate fix: cut the two sentences to "what may and may not reach the page: the contract", keeping the writer's own addition that a diagram drawn from what the owners say is the same.

### FND.4830 — low — The history skeleton restates the closing record of a thread and cites a file that is not its owner
- **Where:** C:\pche\_dev\forge-of-thought\templates\history.md:17-19 ("a thread that closes gets a `closed` record, no `Was` (the rules of a thread: `.claude/skills/forge/states/intent.md`, Threads and files)") against C:\pche\_dev\forge-of-thought\.claude\skills\thread\SKILL.md:81-86, the owner; the cited section, C:\pche\_dev\forge-of-thought\.claude\skills\forge\states\intent.md:92-94, itself hands the rules of a thread to the thread skill
- **Rule:** POS.1070; a reminder names its owner and does not restate it (FND.1150).
- **Fix:** immediate fix: the comment says "the records a thread's birth and closing get: `.claude/skills/thread/SKILL.md`".

### FND.4220 — low — The presentation skeleton restates the meaning of `output:` that `templates/recipe.md` owns
- **Where:** C:\pche\_dev\forge-of-thought\templates\recipe-presentation.md:6 ("optional — overrides the default renders/<recipe>.md") against C:\pche\_dev\forge-of-thought\templates\recipe.md:6; the screenplay skeleton, C:\pche\_dev\forge-of-thought\templates\recipe-screenplay.md:6, already carries the citation alone
- **Rule:** POS.1070; the fix of FND.4220 (the two header comments of `templates/recipe.md` own what `languages:` and `output:` mean).
- **Fix:** immediate fix: the comment becomes `# templates/recipe.md`.
- **Known as:** FND.4220, reopened

### FND.4840 — low — The sentence on a question that asks the principal to decide stands word for word in CLAUDE.md and in the walkthrough skill
- **Where:** C:\pche\_dev\forge-of-thought\CLAUDE.md:136-140 against C:\pche\_dev\forge-of-thought\.claude\skills\walkthrough\SKILL.md:48-53 ("a proposition with Claude's recommendation as what `accept` means ... only a question for information Claude lacks closes with the question alone"); the hook C:\pche\_dev\forge-of-thought\scripts\hook-walkthrough.py:44-48 repeats it by design (POS.1170) and is not part of the finding
- **Rule:** POS.1070; the walkthrough skill is the one owner of the verdict's shape (C:\pche\_dev\forge-of-thought\.claude\skills\check\SKILL.md:56-58). DEC.0340 kept the neighbouring pair, the verdict line and the yes that carries a question, in both places on the reason that CLAUDE.md is in context at every prompt; this sentence is younger than that decision and not named in it.
- **Fix:** Either extend DEC.0340 to this sentence by a record, or let the skill say "as CLAUDE.md, Working methods, Step by step, has it" and keep the sentence in CLAUDE.md alone.

### FND.4850 — low — Six one-liners have a second home
- **Where:** (1) "never pulls or merges on its own (POS.1490)": C:\pche\_dev\forge-of-thought\CLAUDE.md:479-480, C:\pche\_dev\forge-of-thought\.claude\skills\pull\SKILL.md:8-9, C:\pche\_dev\forge-of-thought\scripts\forge-status.py:30-32, C:\pche\_dev\forge-of-thought\scripts\forge-pull.py:19-20. (2) The full name of a filed report with its `-HHMM-<hash>` tail: CLAUDE.md:410-417, :618, :626, :633, C:\pche\_dev\forge-of-thought\.claude\skills\critic-contract\SKILL.md:94, C:\pche\_dev\forge-of-thought\.claude\skills\challenger-contract\SKILL.md:82, against the owner of the tail C:\pche\_dev\forge-of-thought\scripts\forge-report.py:14-18. (3) What a quick research leaves out, twice in one file: C:\pche\_dev\forge-of-thought\.claude\skills\research\SKILL.md:15-19 and :73-74. (4) "only prefixes and terms actually used": C:\pche\_dev\forge-of-thought\templates\assignment.md:64-65 against C:\pche\_dev\forge-of-thought\.claude\skills\forge\states\assignment.md:112-113. (5) What a TBC of a solution design carries: C:\pche\_dev\forge-of-thought\templates\solution-design.md:34-35 against C:\pche\_dev\forge-of-thought\.claude\skills\forge\states\solution-design.md:102-103. (6) What the Briefs table reads: C:\pche\_dev\forge-of-thought\.claude\skills\forge\states\brief.md:150-152 and C:\pche\_dev\forge-of-thought\.claude\skills\forge\states\intent.md:102-104 against C:\pche\_dev\forge-of-thought\templates\ledger.md:26-31.
- **Rule:** POS.1070; a reminder names its owner and does not restate it (FND.1150); the pattern of FND.0620 for the repetition inside CLAUDE.md.
- **Fix:** immediate fix: (1) the two headers and the skill keep the POS citation without the sentence, or cite CLAUDE.md, Persistence; (2) CLAUDE.md, Isolated reviewers, and the two contracts name the directory and "the name completed by `scripts/forge-report.py`", the pattern standing in Repository layout; (3) step 2 says "a quick research as the opening says"; (4) and (5) the comments cite the definition; (6) the two definitions say "the ledger's Briefs table: `templates/ledger.md`".

## Facts
- FND.0650 (genre checklists repeat the rules their skeletons carry) is parked and stands as filed; nothing new since the last naming.
- FND.2920 (the verdict line written out in CLAUDE.md beside the walkthrough skill) is rejected by DEC.0340 and not raised; FND.0710 (DEC.0170) and the caveat part of FND.0720 (DEC.0180) likewise.
