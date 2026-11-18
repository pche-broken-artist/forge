---
id: THR.0910
concerns: solution-design
origin: Claude's synthesis
owner: PCHe
priority: low
status: open
---

The forge's scripts do not handle an output that is cut. When whoever
reads a script's output stops reading before the script has finished,
`head` or PowerShell's `Select-Object -First` after a pipe, the next
print fails and Python ends the script with a traceback and exit 1.
Seen on 2026-11-18 with `forge-history.py` on Windows, its output cut
by `Select-Object -First`: `OSError: [Errno 22] Invalid argument`. No
script in `scripts/` handles it, read that day; none was tried but
the one. For a script that only reads, the harm is the ugly end and
the exit code. A script that writes, `forge-save.py` or
`forge-migrate.py --apply`, would stop in the middle of its work; that
is reasoned, not tried. In daily use it does not happen: Claude's
tools take the output whole and a terminal has no pipe. To be settled:
whether it is mended, and how. Claude's view, not judged: one place in
`forge_tools.py`, the output dropped once nobody reads it and the
script run to its end, so that no script stops halfway for a reader
that went away, with a test that cuts the output. Closed when the
handling is built and tested, or the matter is dropped. Opened
2026-11-18.

<!-- Shape: templates/thread.md -->
