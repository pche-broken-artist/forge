---
date: 2026-11-08
project: forge
check: documentation
target: the engine (docs/ at the engine root, the map projects/forge/docs-map.md)
reviewer: the documentation run
---

# Check (documentation) — the engine — 2026-11-08

7 findings (6 new, FND.3630 reopened in part); 3 known findings reported under their IDs; 3 parked findings resolved by this map. The run of the release of 7.0: 106 entries, 75 pages regenerated, 31 kept, none new, none removed; the check of the pages found one long dash, the page was regenerated once and the second check found no failure; the index derived at version 7.0. The planner's report, the map's Unowned and Did not fit sections and the writers' reports are the sources of what follows; the Unowned matters and the disagreements of map and owner are medium, an unrecorded reason is low.

## Findings

### FND.4340 — medium — Two script headers lag behind the cut of the forge's own project
- **Where:** `scripts/forge-migrate.py`, the header: the slug `forge` is the engine's own project "whose repository is the engine"; `scripts/forge-ledger.py`, the header: a project's git is read from the engine "while the engine tracks it"; against CLAUDE.md, Persistence and The system's own project, `scripts/forge_repos.py` and SOL.0930 (projects/forge/40-solution-design.md), which say the project is a repository of its own since 2026-11-08, and against SOL.0680 of design 0.64, from which the clause "while the engine tracks it" was taken out tonight.
- **Rule:** CLAUDE.md, Persistence: each script is described in full by its own help header; one mechanism lives in one place (prime directive 10). The pages `docs/use/migrate-a-project.md`, `docs/about/upgrades-and-migration.md` and `docs/reference/scripts.md` take CLAUDE.md's shape and leave the headers' clauses out.
- **Fix:** The owner of the headers: in `forge-migrate.py` the slug `forge` names the forge's own project, a repository of its own beside the engine; in `forge-ledger.py` the clause on the engine tracking a project goes, a project's git being its own.

### FND.3920 — medium — The position on the harness says web access is approved by the user per domain; `.claude/settings.json` records no such rule
- **Where:** POS.1090 (projects/forge/10-intent.md) and SOL.0520 (projects/forge/40-solution-design.md) against `.claude/settings.json`, which carries three deny rules and two hooks and nothing on web access.
- **Rule:** POS.0120: where an item and what realises it say different things, that is a finding. The operating layer wins on the page: `docs/about/how-the-rules-are-held.md` says what the settings hold and makes no claim on web access.
- **Fix:** As filed on 2026-11-08: the owners say what the settings hold, or the settings carry the rule the positions claim.
- **Known as:** FND.3920, still open

### FND.3940 — medium — Two terms of the glossary are defined from use, no owner defines them in one sentence
- **Where:** `docs/reference/glossary.md`, the rows of "session" and "harness", marked "defined from use" with the files the use stands in; `docs/about/persistence-in-git.md` and `docs/about/how-the-rules-are-held.md`, which gloss the harness. Of the five terms the finding named on 2026-11-08, three have an owner's sentence now, named among the glossary's inputs: the forge's engine (SOL.0500; CLAUDE.md, The system's own project), isolation (CLAUDE.md, Isolated reviewers, its first paragraph), the format file (the header of `scripts/md2video.py`, POS.1550).
- **Rule:** The documentation contract: a term of the forge is glossed once on a page that needs it, from its owner; a fact without an owner waits for the principal to give it a home.
- **Fix:** One sentence each, in the owner the principal names: what a session is (CLAUDE.md, What this workspace is, or POS.1090) and what the harness is (CLAUDE.md, What this workspace is, or POS.1090).
- **Known as:** FND.3940, still open for session and harness; resolved for the forge's engine, isolation and the format file

### FND.4350 — medium — Three entries of the map carried a claim no named input carries
- **Where:** `docs/about/working-methods.md`, the entry's `says` gives a reason for Intent-first ("a lower layer that takes a change the intent does not carry drifts from it") that stands in neither POS.0140 nor POS.0900 nor CLAUDE.md, Working methods; `docs/start/what-it-is.md`, the entry's `says` calls the videos "real sessions cut to a few minutes", where the pinned facts of the readme recipe say only what each video shows and that it is made from a screenplay render; `docs/use/settle-a-conflict.md`, the entry's `says` names a conflict "in a resource index" among the two-tail cases settled by keeping both, where CLAUDE.md, Persistence and SOL.0840 name the record files alone (the sentence stands in POS.1750, which is not among the entry's inputs). Each writer left the claim off the page and said so.
- **Rule:** The documentation contract: every claim of a `says` has an input that carries it; the map is remade from the owners at the next run.
- **Fix:** At the next run of the planner: the reason of Intent-first cut from the entry or POS.0140 given a reason by the principal; "real sessions cut to a few minutes" cut or carried by a pinned fact of the readme recipe; the resource index cut from the entry of `settle-a-conflict` or POS.1750 added to its inputs.

### FND.3630 — low — The roster page of the scripts carries a "run by" column the headers do not state for seven scripts
- **Where:** `docs/reference/scripts.md`: the writer took "run by" from the map's `says`, CLAUDE.md's command table and the headers' own mentions for `forge-status.py` (`/forge`, `/pull`, `/setup`), `forge-ledger.py` (`/ledger` and every command that changes state), `forge-config.py` (`/setup`), `doc2md.py` (`/ingest`), `docs-check.py` (`/document`), `md2video.py` (`/render`), and lists `forge-branch.py` and `forge-check.py` as run by hand; the entry says the column is each header's own sentence on the command it serves.
- **Rule:** The documentation contract: a roster page asks for no column its owners do not state. DEC.0380 parked this finding until the next documentation run; the run has come.
- **Fix:** Each header names the command that runs it, in one sentence, or the column goes from the page's entry.
- **Known as:** FND.3630, reopened in part: the columns "when it fits" of the lenses and personas pages and the creating command of the templates page rest on the owners now (the `description` of each agent file, the skeletons' comments and the new-project skill); the scripts page does not yet

### FND.4360 — low — Reason not recorded: why the blindness of a reviewer is the source of its value, and why a repository of its own was preferred over a filtered branch for the forge's own project
- **Where:** `docs/about/isolated-reviewers.md`: POS.0400 asserts that the blindness is the source of the reviewers' value and says no more; the page gives REJ.0080's clean-context reason beside it as the nearest recorded one. `docs/about/projects-and-the-engine.md`: SOL.0930 records what made a repository of its own possible (the ledger made at read time, the user's path reading nothing of the project), not why it was preferred over a filtered branch of the engine for users.
- **Rule:** The documentation contract: a page says that a reason is not recorded rather than inventing one.
- **Fix:** The principal's reasons, one sentence each, in POS.0400 and in SOL.0930's Choice.

### FND.4370 — low — Reason not recorded: three rules of the document kinds, one rule of the chain, one of the working conversation
- **Where:** `docs/about/documents-and-records.md`: why the three kindless files (a file of `tmp/`, the player page of `docs/videos/`, the principal's own file in `renders/` or `published/`) have no kind, why the documents fall into six groups, why corrections to an immutable document go downstream (CLAUDE.md, Document kinds and Versioning & status, give the rules only). `docs/about/the-document-chain.md`: why wording alone may be fixed in a lower layer directly (POS.0140 states the rule). `docs/about/the-principal-and-claude.md`: why "written" must mean a file (CLAUDE.md, prime directive 9, states the rule).
- **Rule:** As FND.4360.
- **Fix:** The principal's reasons, one sentence each, in the owners named.

### FND.4380 — low — Reason not recorded: why a paid subscription is needed
- **Where:** `docs/start/install.md`: the pinned facts of `projects/forge/recipes/readme.md` state that Claude Code needs a paid subscription and give no reason; the page states it without one.
- **Rule:** As FND.4360.
- **Fix:** One sentence in the pinned facts of the readme recipe, or the fact left as it is by the principal's word.

## Resolved by this map
- FND.3600, FND.3610 and FND.3620, parked by DEC.0380 until the next documentation run: the planner's report says the rule was applied to every entry (every claim of a `says` has an input that carries it, a part is named only where its heading, its ID or its bold label stands on disk, the entry of `docs/use/upgrade-the-engine.md` names no check before the migration), and the state script isolated every part it was given; the hashing notes of the map's Did not fit say which parts end where. Verified by the planner's report and the state script's run, not by a reading of the 106 entries.
- FND.3930 and FND.3950 of the report of 2026-11-08: `docs/extend/how-a-change-is-made.md` links `docs/extend/change-a-documentation-page.md`; `templates/recipe-user-stories-export.md` is among the inputs of `docs/about/the-user-stories.md`.
- FND.4060: "the driver" is gone from POS.1680 since 6.24; "today's bracket" stands, and the entry of `docs/about/the-intent.md` takes a thread's header from the intent definition and the thread template, keeping POS.1680 for the reason only.

## Not raised
- FND.3580 (parked, DEC.0390): how a merge request's branch is fetched onto the integrator's clone; the map lists it under Unowned and the pages say the merge is git's by hand.
- FND.3400 (open): a reason for the rule that a project records no engine version; the map lists it under Unowned and `docs/about/upgrades-and-migration.md` says the reason is not recorded.
- The reasons the two earlier reports list as wanted (FND.3180 to FND.3500, FND.3960 to FND.4050): every page that reads such an owner says the reason is not recorded; nothing new of them.
