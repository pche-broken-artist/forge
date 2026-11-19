---
id: THR.0930
concerns: intent, solution-design
origin: sources/github-issues/discussion-13-fork-cannot-follow-the-engine.md
owner: PCHe
priority: low
status: open
---

On a fork the forge says "up to date" while the engine has moved on.
Reported in discussion #13 on 2026-11-13 by stasidom-allwyn:
`scripts/forge-pull.py` and the state it reads ask the remote
`origin` alone, on a fork the fork, which does not move when the
engine does. Confirmed in the code on 2026-11-19, answered and closed
the same day: bringing the upgrade into a fork stays by hand, "Sync
fork" on GitHub and then `/pull`, the forge being no wrapper around
GitHub, and CONTRIBUTING says so (its recipe 0.12). Left to be
considered, the principal's word in the discussion: whether the forge
at least says it. Tried on 2026-11-19 by reading only: `git ls-remote
<address> refs/heads/main` gives the commit of the original's main
with git alone, no `gh` and no second remote, and `git merge-base
--is-ancestor` says whether the clone holds it. So one line of
`forge-status --remote` could say that the origin is not the engine's
own address and that the engine has moved there, not by how many
commits; the shared state and its four readers stay untouched and
the thing can be tested on the fixture. It needs one new fact, the
engine's own address, which the engine keeps nowhere today (POS.0830,
no remote URL in the scripts). Not tried: a clone that does not hold
the original's commit at all, and addresses in different forms. The
two larger ways, weighed and not wanted now: GitHub's `gh` for the
fork and its sync, an optional tool today; a second remote in the
clone, a state against two remotes in each command that reads it and
a clash with the state word `no upstream`. Closed when the principal
decides whether the forge says it, the position then standing in the
intent or the matter dropped. Opened 2026-11-19.

<!-- Shape: templates/thread.md -->
