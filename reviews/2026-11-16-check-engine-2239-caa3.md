---
date: 2026-11-16
project: forge
check: engine
target: the engine root
reviewer: check engine (isolated context)
---

# Check (engine) — the engine — 2026-11-16

3 findings

## Findings

### FND.4760 — medium — The solution design still places the Commands table and the script entries of the layout in CLAUDE.md; neither the intent nor the design names `.claude/reference/`
- **Where:** C:\pche\_dev\forge-of-thought\projects\forge\40-solution-design.md:461-462 (SOL.0640: "`CLAUDE.md` carries the kind in the Document kinds table, `work/` in the layout and the command in the Commands table") and :634-636 (SOL.0950: "Where: `scripts/forge-record.py`, ... `CLAUDE.md` (Versioning & status, Repository layout)"); against C:\pche\_dev\forge-of-thought\CLAUDE.md:648-653 (Commands carries no table and names `.claude/reference/commands.md`) and :320-324 (Repository layout names `.claude/reference/repository-layout.md`, where `forge-record` now stands at :42-45). A grep for `.claude/reference`, `commands.md` and `repository-layout` over `10-intent.md` and `40-solution-design.md` finds nothing: the folder and its two files are recorded only in the thread C:\pche\_dev\forge-of-thought\projects\forge\threads\THR.0240.md:115-122.
- **Rule:** Core ↔ forge intent (this check's Lens, 2); CLAUDE.md, The system's own project: "A process change is complete only once that intent is updated and the README re-rendered"; POS.0120: where an item and what realises it say different things, that is a finding; POS.1780 lets the build come first, "never across a release".
- **Fix:** In the round that brings the intent and the design to the built state, before a release: repoint the two clauses of SOL.0640 and SOL.0950 to `.claude/reference/commands.md` and `.claude/reference/repository-layout.md`, and name the folder read on demand in the item of the design that realises the always-on pattern of POS.1170 and THR.0240.

### FND.4770 — low — The README's fixed text "Planned architecture" states as the plan two steps that no position of the intent holds
- **Where:** C:\pche\_dev\forge-of-thought\projects\forge\recipes\readme.md:443-465 (steps 3 and 4: "Next, the AI engine separated. The general base, Anvil, ... becomes a plugin of Claude Code"; "Then further forges ... Forge of Proof ... Forge of Form"), excepted from derivation at :34-37 ("the fixed text of Planned architecture"); rendered at C:\pche\_dev\forge-of-thought\README.md:291-313. Against C:\pche\_dev\forge-of-thought\projects\forge\10-intent.md:375-380 (POS.1380: what remains is the brief `engine-split`, the split "a decision about roots and installation" not yet made), :2372-2378 (POS.0700: "Nothing is approved for construction"), :2777-2782 (REJ.0150 names "a plugin as the only shape now" among the shapes rejected). `Anvil` appears in no position: only in `00-brief-engine-split.md` (the ledger's Briefs row: 0.6, draft, `pending`), THR.0850 and the recipe and render `forge-evolution`; neither the brief nor that render is among the readme recipe's Inputs (:15-24), though the fixed text embeds the render's picture.
- **Rule:** README ↔ CLAUDE.md and the intent (this check's Lens, 1): a claim in the README that the intent does not support is a recipe defect, fixed in the recipe; CLAUDE.md, The system's own project (a process change is complete once the intent is updated). The recipe marks the text as fixed on purpose, so the state may be the principal's deliberate one: then it needs a DEC to stand as accepted.
- **Fix:** Either mine the direction of the brief `engine-split` into a position the fixed text can cite (the plugin as a direction, the names as working names), or reword steps 3 and 4 in the recipe as a direction named and not decided, as POS.0780 allows; and declare `renders/forge-evolution.png` among the recipe's Inputs as a picture source.

### FND.4780 — low — The layout of the engine's root lists `.gitattributes` and `.mailmap` but not the root `.gitignore`
- **Where:** C:\pche\_dev\forge-of-thought\.claude\reference\repository-layout.md:33-37 (no `.gitignore` entry anywhere in :7-107), against C:\pche\_dev\forge-of-thought\.gitignore:1-29 on disk, which carries what POS.1980 and CLAUDE.md, Repository layout (:342-346, "gitignored (projects/*) but for its README") rest on.
- **Rule:** `.claude/reference/repository-layout.md`:3 ("The root of the engine, file by file"), named by CLAUDE.md, Repository layout; this check's Lens, 1 (the layout of the engine against what is on disk).
- **Fix:** immediate fix: add after the `.gitattributes` entry a line `.gitignore  # what never enters the engine's git: the instance file, the local settings, every project but the README of projects/ (POS.1980), Office lock files, byte-code caches`.
