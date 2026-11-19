---
id: THR.0920
concerns: intent, solution-design
origin: sources/github-issues/discussion-10-unassigned-tbc-missing-from-ledger.md
owner: PCHe
priority: high
blocks: the answer promised in discussion 10
status: open
---

The open questions of a BRD that have no owner stand nowhere under
Waiting on principal. Reported in discussion #10 on 2026-11-09 by
Pomalanoha, from a first BRD: seven TBC, six of them `owner:
unassigned` and three blocking estimation, none shown by the ledger
or by the `/forge` map, which reads the ledger, so that with the
threads of the intent closed the overview would say that nothing
waits. Confirmed in the engine on 2026-11-19: the script does what
the rule says and the gap is the rule's. Waiting on principal takes
"the TBCs whose owner is the principal" (POS.1620,
`templates/ledger.md`), `scripts/forge-ledger.py` reads that as the
words `principal` or `the principal` after `owner:`, while the BRD's
definition gives a TBC `owner: unassigned` "until the principal
names the role" (`.claude/skills/forge/states/brd.md`, POS.1810);
`blocks estimation` is read by nothing. The finding is wider than
the discussion: a TBC whose owner is written as the principal's
handle is left out the same way, six of them on 2026-11-19 in the
work specifications of `forge` and `forge-rollout`. To be settled,
one decision each: whether a TBC with `owner: unassigned` waits on
the principal, the author's first proposal; whether the ledger shows
the questions that have another owner and block estimation, in a
section of their own, `Estimation blockers`, his second, a new
section of the ledger; and how the rule knows the principal's own
TBC where its owner is his handle. Then POS.1620 in the intent
first, the ledger's template, the script with its tests and the
wording of the `/forge` map where it changes. Promised in the
discussion on 2026-11-11: an answer with what changes. Closed when
the position stands in the intent, the script is built and tested,
and the discussion is answered. Claude's view: the first is right
and small, since by the BRD's own definition the naming of the
owner is the principal's; the second is a decision of its own, since
a TBC with an owner waits on someone else and Waiting on principal
is not its place; on the third, a script whose output is rendered
into a public file cannot know whose handle the principal's is, so
either the owner of a TBC is written as a role by rule or the
overview shows the questions by owner, neither tried. Opened
2026-11-19.

2026-11-19: decided the same day and written into the intent 7.15
(POS.1620) and the design 0.76 (SOL.0680), all three questions with
it, the way in the record of POS.1620; built the same day,
`templates/ledger.md`, `scripts/forge-ledger.py` and its test, the
suite green. Open now: the answer in the discussion.

<!-- Shape: templates/thread.md -->
