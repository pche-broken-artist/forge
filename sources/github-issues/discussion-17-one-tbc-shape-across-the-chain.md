# GitHub discussion #17: Open questions in user stories should be TBC items — and one TBC shape across the chain

Source: https://github.com/pche-broken-artist/forge-of-thought/discussions/17  
Author: lukprusak  
Opened: 2026-11-24  
Category: Ideas  
State at download: open, no comments, downloaded 2026-11-24

## Summary

An open question is written in four different shapes across the chain, and the user stories carry theirs as free text that nothing can track. I propose (1) that a question in a user story becomes a TBC item, and (2) that every TBC carries one set of fields, whatever layer it stands in, with a single `blocker: yes | no` in place of the per-layer blocking fields.

## 1. Questions in user stories have no ID and are not tracked

Today a story carries its open questions inline, per POS.2010 and `templates/user-stories.md`:

```
**Questions:**
1. <question> → <owner>
```

The assignment, the BRD, the solution design and the work specification carry theirs as `TBC.NNNN` items. A question in a story is therefore:

- **not citable** — when its answer changes substance it goes to the parent first (POS.2000, intent-first), but the BR or NFR that takes the answer has no ID to cite for the question it closes;
- **not marked as blocking** — the definition says a story with a question that blocks the delivery is not done, but the template has no field to say which question blocks;
- **invisible in the ledger** — *Waiting on principal* (POS.1620, `templates/ledger.md`) reads TBC items and takes no free text without an ID, so an unowned or blocking question in a story is found only by reading every story.

POS.2010 gives the reason for the shape as the format of the export pasted into a wiki or tracker. But the export is a render (genre `user-stories-export`): the source can carry IDs while the render still prints each question under its story, exactly as today. The constraint is on the output, not on the source.

**Proposal:** keep the questions inside their story (the document still carries the stories only, the export keeps its shape), but as items in the shape of part 2:

```
**Questions:**
- **TBC.0010** (owner: Product owner; blocker: yes) How long is a basket kept for a visitor not logged in?
```

This would touch POS.2010 and POS.2020, `states/user-stories.md` and its template, the `user-stories` check, `forge-ledger.py` and the export genre.

## 2. One shape for a TBC across the chain

A TBC carries different fields in each layer:

| Layer | Fields |
|---|---|
| Assignment | owner |
| BRD | owner, `blocks estimation: yes \| no` |
| Solution design | owner, `Closed by:`, `Blocks realisation: yes \| no` |
| Work specification | owner, `Closed by:` |
| User stories (today) | owner only, no ID |

I found no stated reason for the differences; they read as accretion rather than design. The ledger rule (POS.1620) has to name the BRD's and the solution design's wording separately because of it.

The two blocking fields say the same thing: this question stops the document from being done. Only the word for "done" differs, and each layer's definition already says what done means — no TBC blocking estimation open for a BRD, none blocking realisation for a solution design, none blocking delivery for a story.

**Proposal:** one shape everywhere:

```
TBC.NNNN (owner: <who>; closed by: <what>; blocker: yes | no) <the question>
```

`blocker: yes` means the question stops this document from being done; what "done" means for each layer (estimation for a BRD, realisation for a solution design, delivery for a story) stays in that layer's definition, where it already is. It is a property of the question, not its priority. One yes/no field also lets the ledger read every layer the same way. Where a reader of the document needs the reason, the layer's Open questions section can say it once in its introduction ("a blocker stops estimation") instead of on every item.

## Questions to the maintainer

- Was the inline `question → owner` form in stories a deliberate choice beyond the export format?
- Is there a reason the layers' TBC fields differ that is not written down?
