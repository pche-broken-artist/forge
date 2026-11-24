# GitHub discussion #15: Commit messages: Conventional Commits type plus the seven rules of a good commit message

Source: https://github.com/pche-broken-artist/forge-of-thought/discussions/15  
Author: smidf-allwyn  
Opened: 2026-11-24  
Category: Ideas  
State at download: open, no comments, downloaded 2026-11-24

**What happens today.** `/save` and `/release` draft a one-line English commit message, and the commits of the engine and of the forge's own project carry the prefix `forge:` (CLAUDE.md, Persistence). In practice the line is often a long sentence that holds the whole round, several hundred characters wide. It reads well in the history companions, but `git log --oneline`, GitHub's commit list and most tools cut it off after the first few words.

**The idea.** Draft every commit message in one shape:
- **Subject:** `<type>: <description>`, the type from Conventional Commits (`feat`, `fix`, `docs`, `refactor`, `chore`, …). The description is in lower case, in the imperative, with no full stop, and the whole subject is at most 50 characters.
- **Body:** after a blank line, wrapped at 72 columns, saying what changed and why, not how. This follows the seven rules in Chris Beams, "How to Write a Git Commit Message" (https://cbea.ms/git-commit/).
- **No scope by default.** Conventional Commits makes the scope `(…)` optional, and here it is left out. A commit lives in one repository, and the repository already says what it is about: a commit in the engine's repository is the forge's, and so is a commit in the forge's own project. Writing `forge` again in every subject only repeats what the repository says. For the same reason the prefix `forge:` is dropped. A scope is added only where it tells apart parts of one repository that a reader would otherwise confuse.

**Why.** The history stays readable at a glance, the subject survives every tool that cuts it, and the shape is a common standard that tools such as commitlint check. Nothing else moves: the history companions stay the single primary record, and the release notes are still derived from them, not from commits.

**Example.** A recent engine commit, as it is today:
```
forge: the header reader strips a pair of quotes around a whole value and keeps a quote that only ends or only begins it (scripts/forge_docs.py, front_value, with its test), so that the ledger's Research table no longer drops the closing quotation mark of a derived_from; found by the light check of 2026-11-15 (intent 7.11); the tests green, 253 passed
```
and the same commit in the proposed shape:
```
fix: keep a lone quote in header values

The header reader stripped any quote at the edge of a value, so the
ledger's Research table dropped the closing quotation mark of a
derived_from. It now strips a pair of quotes around a whole value
and keeps a quote that only ends or only begins it
(scripts/forge_docs.py, front_value, with its test).

Found by the light check of 2026-11-15 (intent 7.11); the tests
green, 253 passed.
```

**Open for you.**
- Does anything depend on the `forge:` prefix (a script, a release step, a habit of reading the log) that dropping it would break?
- Should the shape be checked anywhere (for instance in `/save`), or only drafted?
- Should a `/release` commit have a type of its own (e.g. `chore(release): …`)?
- Are 50 and 72 too tight? Beams' limits come from the terminal and from email. Many teams use 80 or 100 today, and the proposer usually does too. Two facts to weigh: the forge already hard-wraps its own prose at about 72 columns (CLAUDE.md, Document kinds), so 72 for the body would match the house style; and GitHub cuts a subject in its lists at around 72 characters. A subject of up to 72 with a body of 80 or 100 is a possible middle way.
