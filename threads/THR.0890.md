---
id: THR.0890
concerns: solution-design
origin: Claude's synthesis
owner: PCHe
priority: low
status: open
---

The light check reads every ID a work file cites as a reference to
an input of its specification and does not tell the file's own
items apart, so a BRD made as a work product is found to cite the
TBC items it raised itself. Seen on 2026-11-13 in agentic-platform,
`work/brd-from-geap-transcript.md` citing TBC.0090 to TBC.0180, the
finding FND.0530 rejected there by DEC.0120; the same shape was
settled before in the forge's own project, `work/
collaboration-cutover.md` and TBC.0090, FND.2380. What is to be
settled: whether the check (`scripts/forge-check.py`, the clause of
POS.1520 on a work file) takes an ID defined in the file itself as
its own and not as an input, and what the rule of the work product
(`.claude/skills/work/SKILL.md`, POS.1520) says of items a work file
creates. Closed when the check tells the two apart or the rule says
it should not, with a test either way. Claude's view: the check
should skip IDs whose definition stands in the file, since a
specification cannot name among its inputs what did not exist
before the file was made. Opened 2026-11-13.

<!-- A thread (POS.1680), one file per thread in threads/; the header
is its state: what it concerns, where it came from, whose it is, when
it is taken up, what waits on it, whether it is open. The rules of a
thread, its birth, its upkeep, its life and its closing:
`.claude/skills/thread/SKILL.md`. -->
