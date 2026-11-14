origin: the report of the Claude Code command `/doctor prompt-audit`, run in the session by Claude through the bundled prompt-audit guide; the proposed diff was not applied
date: 2026-11-14

# The audit of the instruction files (`/doctor prompt-audit`), the baseline

Nothing was changed. The report and the proposed diff.

## Assumptions

- **Scope:** the 60 files of Claude Code configuration in the project,
  295,907 characters in all: `CLAUDE.md` and `CLAUDE.local.md`; 32
  skills with six definitions of artefacts and five reference files;
  15 agents. The folders `rules/`, `commands/`, `output-styles/` and a
  file `AGENTS.md` do not exist. No user-level `CLAUDE.md` exists, no
  plugins. The settings files were not read.
- **Target model:** the session's model, Claude Fable 5.2. Every agent
  has `model: inherit`.
- **Provenance:** `git blame` was not run. Every finding is a
  contradiction with the repository; none rests on dating by idiom.

## Summary

The weightiest are three places where an instruction contradicts what
the repository does. Two are in the skill `/research`: the naming of
the notes and the return of a note to its agent. The third is a
reference to the wrong step in the skill `/forge`.

Counts by group: dated prompt text (group 1) 0; brittle configuration
files (group 2) 4; tool descriptions (group 3) 1; request
configuration (group 4) not applicable, the roster of agents without a
finding.

In group 1 the search was for emphasis words in capitals, "think step
by step", fixed word limits, bans on formatting and names of retired
models. Nothing was found.

## Findings

**1. The naming of research notes does not match the script**
- Location: `.claude/skills/research/SKILL.md:39` and `:152`.
- Evidence: "one note per card per engine, `<card>.<engine>.md`" and
  "`python scripts/forge-cite.py --independence <bundle>`".
- Pattern: group 2, volatile specifics.
- Why: `scripts/forge-cite.py:165` looks only for files `card-*.md`.
  A bundle named as the skill names it returns "no card with notes of
  two engines".
- Confidence: high. Action: rewrite.

**2. Returning a note to its agent cannot be done as written**
- Location: `.claude/skills/research/SKILL.md:146-148`.
- Evidence: "A note with a dead or mismatched citation goes back to
  its agent once, with the report, as a failed run".
- Pattern: group 2, volatile specifics.
- Why: step 5 of the same skill writes the second engine's note
  straight into the bundle, and `scripts/forge-engine.py:281` refuses
  to write over an existing note.
- Confidence: high. Action: rewrite.

**3. A reference to the wrong step**
- Location: `.claude/skills/forge/SKILL.md:21-22`.
- Evidence: "as `python scripts/forge-status.py --remote` of step 4
  reports it".
- Pattern: group 2, volatile specifics.
- Why: in the same file the state against the origin is run in step 5;
  step 4 is the recommendation.
- Confidence: high. Action: rewrite.

**4. A model's name written into prose**
- Location: `.claude/skills/setup/SKILL.md:68-73`.
- Evidence: "create it with `{ "model": "fable" }`, the strongest
  model … the session is set to Fable".
- Pattern: group 2, history narratives and pinned model names.
- Why: a name pinned in the text goes stale silently at the next
  release. The rule itself is "the strongest model".
- Confidence: medium. Action: rewrite.

**5. Two skill descriptions too short**
- Location: `.claude/skills/ledger/SKILL.md:2` and
  `.claude/skills/render/SKILL.md:2`.
- Evidence: "Report project state from the ledger" and "Regenerate a
  render from its recipe in recipes/".
- Pattern: group 3, under-described.
- Why: `CLAUDE.md:91-96` says a request in free words is the command.
  Routing to a skill goes by its description, and these two do not say
  when to reach for them.
- Confidence: medium. Action: add.

**For the record only, no edit proposed (low confidence)**
- Rules without enforcement: `CLAUDE.md` keeps two rules as sentences
  that no code enforces: a record into a history by the script alone,
  and the immutable documents.
- References into a repository the user does not have: the
  instruction files cite items of the forge's own project by ID, and
  that project is a repository of its own which a user of the engine
  does not have.

## Proposed diff

Not applied. Each finding is a hunk of its own.

```diff
--- .claude/skills/research/SKILL.md   (finding 1)
-and one note per card per engine, `<card>.<engine>.md` (shape
-`templates/research.md`). The bundle is immutable as
+and one note per card per engine, `card-<name>.<engine>.md` (shape
+`templates/research.md`; the name begins `card-`, which is what the
+independence measure of `scripts/forge-cite.py` looks for). The bundle is immutable as
```

```diff
--- .claude/skills/research/SKILL.md   (finding 2)
    `scripts/forge-engine.py` and `scripts/forge-cite.py`). A note with a
    dead or mismatched citation goes back to its agent once, with the
-   report, as a failed run; a note that comes back still failing is
+   report, as a failed run: the refused note is first moved out of the
+   bundle into `tmp/research/<run>/hold/first-run/`, since the engine
+   script refuses to write over a note; a note that comes back still failing is
```

```diff
--- .claude/skills/forge/SKILL.md   (finding 3)
      under git — as `python scripts/forge-status.py --remote` of step
-     4 reports it, a repository of its own or "not under git"
+     5 reports it, a repository of its own or "not under git"
```

```diff
--- .claude/skills/setup/SKILL.md   (finding 4)
-   - Otherwise create it with `{ "model": "fable" }`, the strongest
-     model, and tell the user in one sentence: the session is set to
-     Fable, which the forge including the blind reviewers runs on,
+   - Otherwise create it with the strongest model `/model` lists
+     (`{ "model": "fable" }` as this is written), and tell the user in
+     one sentence: the session is set to that model, which the forge
+     including the blind reviewers runs on,
```

```diff
--- .claude/skills/ledger/SKILL.md   (finding 5)
-description: Report project state from the ledger
+description: Report project state from the ledger — what exists at which version, what is stale, what waits on the principal; use when asked where a project stands or what is open
--- .claude/skills/render/SKILL.md   (finding 5)
-description: Regenerate a render from its recipe in recipes/
+description: Regenerate a render from its recipe in recipes/ — a README, release notes, a pitch, a deck or a picture made from the chain; use when a render is stale or a recipe changed
```

On finding 1: the script could be mended in place of the skill, so
that it takes any `<card>.<engine>.md`. The script is code, not an
instruction file, so it has no place in this diff.

## What the audit says of length

The audit does not count the length of `CLAUDE.md` as a finding by
itself: specific outdated instructions do harm, not volume. The text
of the instructions carries no emphasis words and no crutches for
older models.
