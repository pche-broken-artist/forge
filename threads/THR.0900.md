---
id: THR.0900
concerns: intent, solution-design
origin: sources/github-issues/issue-14-unreachable-origin.md
owner: PCHe
priority: high
blocks: the fix of issue 14 and the reporter's offered pull request
status: open
---

An origin that cannot be reached is read as "up to date". Reported
in issue #14 on 2026-11-16 by pavel576, behind a corporate proxy
that git had not been given: `/pull` said every repository was
current while nothing was fetched. Confirmed in the code on
2026-11-17: `remote_state()` of `scripts/forge_repos.py` discards
the result of the fetch and computes the state from the
remote-tracking ref on disk, and `scripts/forge-pull.py` reports
every failed `git pull --ff-only` as a diverged history. The finding
is wider than the issue: the same state is read by
`forge-status.py --remote`, the gate of `/release`, `/publish` and
`/document`, by `forge-migrate.py` and by `forge-save.py`, so a
derived file can be made and released from a stale `main`. The
states `behind` and `diverged` got their tests in THR.0650; a failed
fetch has none. To be settled: a state word for an origin that could
not be reached, beside those POS.1490 lists, and what each of the
commands does on it, refuse, warn and go on, or other, one decision
per command; then the fix, the tests with an origin on a path that
does not exist, and the wording of the `/pull` skill and of the
`/forge` map. Promised in the issue on 2026-11-17: the position in
the intent first, then the fix, the reporter's pull request taken up
once the position is written. Closed when the position stands in the
intent, the fix is built and tested, and the issue is answered and
closed. Opened 2026-11-17.

<!-- Shape: templates/thread.md -->
