# GitHub discussion #19: Change The Conversation Paradigm

Source: https://github.com/pche-broken-artist/forge-of-thought/discussions/19  
Author: Entir-42  
Opened: 2026-11-25  
Category: Ideas  
State at download: open, no comments, downloaded 2026-11-26

Proposal: working method "Overview" beside the Walkthrough (to choose one of modes)

A list of open items (findings, challenges, threads, TBC items) can
today be worked only as a Walkthrough (POS.0850): one item per message,
in Claude's order of weight. Many items cannot be decided by the
principal alone; the answer lies with a stakeholder offline. To reach
the right person efficiently, the principal needs to see the whole list
first and decide what to take up, when, and with whom.

## Requirements found by forge itself

1. **The principal can see all open items at once, one line each, with
   the file that holds the full text.**
   Why: duplicates, dependencies and items for the same person are
   visible only across the list, never one item at a time.
   Why it works: the items already stand in files (`reviews/`,
   `challenges/`, `threads/`, the artefacts) and the ledger already
   gathers their states; the overview is a reading, not a new store.

2. **The principal can group the items by the person who can answer
   them.**
   Why: one meeting or one message per stakeholder instead of a stream
   of interruptions; stakeholders' time is as scarce as the
   principal's attention.
   Why it works: TBC items already carry an owner; for the others the
   principal names the addressee at the moment of grouping.

3. **The principal selects which items to work now, and in what order.
   A selection is not a verdict.**
   Why: what can be decided now and what must wait for a stakeholder
   is the principal's judgement, not a ranking by weight.
   Why it works: nothing changes and nothing is written by a
   selection, so no rule of the record is touched.

4. **Every verdict is still given in a Walkthrough, one item per
   message.**
   Why: the one-item rule exists because bulk decisions drifted
   (history of POS.0850, 3.15); the Overview must not reopen that.
   Why it works: the Overview ends where a decision starts; the
   selected items enter the existing Walkthrough unchanged.

5. **Items not selected stay open, not parked.**
   Why: `park` is a verdict with a record; an item nobody looked at has
   no verdict.
   Why it works: the ledger keeps showing them as open, so nothing is
   lost, and nothing is recorded that was not decided.

Answers obtained offline come back through the existing door:
`/ingest` of the notes, then the intent by the principal's explicit
act, with provenance.
