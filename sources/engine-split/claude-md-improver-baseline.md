origin: the quality report of the skill `claude-md-improver` of Anthropic's plugin `claude-md-management` (version 1.0.0), run as an audit only in the session; the rubric is the plugin's, the scores were given by Claude applying it; nothing was edited
date: 2026-11-14

# CLAUDE.md quality report, the baseline before the rebuild

## Summary

- Files found: 2 (`CLAUDE.md` and `CLAUDE.local.md` at the engine
  root). `templates/CLAUDE.local.md` is a skeleton and is loaded into
  no session; not assessed. Everything under `projects/` and `tmp/`
  was left out.
- Files scored: 1.
- Nothing was updated: the run was a baseline measurement.

## File-by-file assessment

### 1. `CLAUDE.md` (project root)

**Score: 82/100 (grade B)**

| Criterion | Score | Notes |
|-----------|-------|-------|
| Commands/workflows | 18/20 | A table of 27 commands, the ways of saving, releasing and pulling, how the scripts are called. No single block of commands to copy. |
| Architecture clarity | 20/20 | A complete map of the repository, the kinds of documents, the chain. |
| Non-obvious patterns | 13/15 | Many reasons and pitfalls; a part of the reasons is only a reference by ID into another repository. |
| Conciseness | 5/15 | 920 lines; repeats what the skills own and describes a tree that can be listed. |
| Currency | 14/15 | Every named path and script exists. |
| Actionability | 12/15 | Commands and paths are concrete; the rules stand in dense paragraphs with many cross-references. |

**Issues:** length; content of the skills repeated.

**Recommended additions (the rubric's):** a short block of commands
to start with.

### 2. `CLAUDE.local.md` (local)

Three lines of instance facts. The rubric does not fit it: it would
score about 40/100 for having no commands and no architecture, and
the number says nothing, since the file does exactly what it is for.

## A note on reading this score after the rebuild

The rubric gives full marks for the map of the repository and nearly
full marks for the table of commands, about 240 lines the rebuild
means to take out of the always-loaded file. After it the scores for
architecture and commands will fall and the score for conciseness
will rise; the sum may hardly move. The breakdown by criterion is
what compares, not the sum.
