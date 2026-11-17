---
bundle: github-issues
project: forge
date: 2026-10-21
origin: the issues of the engine's GitHub repository, downloaded with their comments through the GitHub API
---

# Index — bundle `github-issues`

<!-- Catalogue of one bundle (sources/<slug>/): the rules are
CLAUDE.md's (Document chain, External inputs). This skeleton is the one owner of the
bundle index (POS.1070): the header and the opening paragraph are its
own, the per-file entry is the sources entry of templates/index.md,
cited and not copied. The opening paragraph says whether the bundle
arrived whole or grows (POS.0180). -->

The issues and the discussions visitors open on the engine's GitHub
repository, one file per issue or discussion with the comments it
carried when it was downloaded. A growing bundle: a new issue or
discussion is added as its own file and entry when the principal
ingests it, each file immutable from its registration (POS.0180).

### `issue-3-repo-detection.md`
- **What:** GitHub issue #3, "Repository detection tests for `<path>/.git` instead of asking git": the scripts test `projects/<slug>/.git` and assume the project directory is the top of its repository, so a project that is a subdirectory of a larger repository (reached through a symlink in the reporter's case) is reported as "not under git" by every script, the ledger's `tracked` guard included; nine sites listed with lines on `main` at `c0b0f3c`; a helper `repo_root` asking `git rev-parse --show-toplevel` proposed, with the project directory and its repository kept apart. With the principal's reply of 2026-10-21: accepted for work, intent first; the engine-root exclusion of the helper holds only while the engine is the top of its own repository; `.gitignore` and `.gitattributes` may stay in the project directory.
- **Origin:** https://github.com/pche-broken-artist/forge-of-thought/issues/3, opened by a contributor on 2026-10-21; downloaded with its one comment on 2026-10-21.
- **Date:** 2026-10-21, from the content
- **Form:** text
- **Role:** the report from which the thread on a project inside a larger repository was opened; the author's layout, the nine sites and his proposed helper, with the principal's reply of 2026-10-21.
- **Use for:** the layout that fails today and why; the list of detection sites in the scripts; the proposed helper and the two remarks on it.

### `discussion-6-record-of-what-was-sent.md`
- **What:** GitHub discussion #6 (Ideas), "A record of what was sent out, pinned to the exact version": a project-level record of what the principal sent out of the forge, which file, made from what, to whom, by which channel and when, each entry pinned to the commit that holds the file, since a render is overwritten by the next `/render` and a commit hash or a hand-set tag says nothing of where the file went; a sketch of `sent.md` in the project root, append-only, one line per sending, written on the principal's word only, born at the first sending; two open questions, whether a sending also sets a tag and whether an entry belongs in the ledger.
- **Origin:** https://github.com/pche-broken-artist/forge-of-thought/discussions/6, opened by a visitor on 2026-11-02; downloaded without comments on 2026-11-08.
- **Date:** 2026-11-02, from the content
- **Form:** text
- **Role:** the request from which the thread on a record of what was sent out of a project is opened; the author's sketch of a `sent.md` and his two questions, a tag and a ledger row.
- **Use for:** what is wanted and why, in the author's words; the sketched shape of the record and its line; the two questions to answer when the thread is settled.

### `issue-14-unreachable-origin.md`
- **What:** GitHub issue #14, "/pull reports "up to date" when git cannot reach the origin (e.g. git's proxy not set), and blames a diverged history when the pull itself fails": behind a corporate proxy that git had not been given, `forge-status.py --remote` printed `remote: up to date` with exit code 0 while a plain `git fetch` failed, and `forge-pull.py` reported the failed pull as a diverged history; reproduced by giving git a dead proxy for one process; two causes named, the discarded result of the fetch in `remote_state()` of `scripts/forge_repos.py` and every non-zero exit of `git pull --ff-only` read as diverged in `scripts/forge-pull.py`; a fix proposed, a state for an origin that could not be reached, with tests on an origin that does not exist, and a pull request offered. With the principal's reply of 2026-11-17: the cause confirmed, the finding wider than reported since the gate of `/release`, `/publish` and `/document`, the migration and the save read the same state; the position in the intent first, then the fix.
- **Origin:** https://github.com/pche-broken-artist/forge-of-thought/issues/14, opened by a visitor on 2026-11-16; downloaded with its one comment on 2026-11-17.
- **Date:** 2026-11-16, from the content
- **Form:** text
- **Role:** the report from which the thread on an unreachable origin read as "up to date" was opened; the reporter's reproduction, the two causes he names and his proposed fix, with the principal's reply of 2026-11-17.
- **Use for:** how the failure shows and how to reproduce it; the two sites in the scripts; the proposed state word and tests; what was promised to the reporter.
