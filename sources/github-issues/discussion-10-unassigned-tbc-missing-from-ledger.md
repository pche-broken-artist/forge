# GitHub discussion #10: BRD questions with unassigned owners are missing from the ledger

Source: https://github.com/pche-broken-artist/forge-of-thought/discussions/10  
Author: Pomalanoha  
Opened: 2026-11-09  
Category: Ideas  
State at download: open, 1 comment, downloaded 2026-11-19

Hi, I ran into something while working on my first BRD (`30-brd.md`), generated from `10-intent.md`.

Claude created 7 open questions (`TBC.0010` to `TBC.0070`). Four came from open threads in the intent, so those topics are already visible in `ledger.md` through their THR entries. The other three came up while drafting the BRD: who approves it, what the NFR target values should be, and how success will be measured.

Six of the seven TBCs have `owner: unassigned`, and three block estimation. That's where I am at the moment as the analyst: I still need to find the right people or get answers from stakeholders.

But none of these TBCs show up under `Waiting on principal`. Only the four original THR entries are there, so the questions added during the BRD stage don't appear in that overview.

I checked the rules and the script, and I think I see why:

- `.claude/skills/forge/states/brd.md` says to use a roster or stakeholder role as the owner, or `unassigned` until the principal names one.
- `scripts/forge-ledger.py`, around line 466, only picks up TBCs with `owner: principal` or `owner: the principal`. The ledger template says the same thing.
- `blocks estimation: yes` doesn't affect whether a TBC is included.

So the script seems to be doing what the ledger template asks for, but that leaves a gap between how BRD questions are created and what the overview shows. Since `/forge` gets its waiting items from the ledger, it misses them too.

If I closed the remaining intent threads and had no other open findings or challenges, the overview could say nothing is waiting on me, even though I still have six BRD questions without an owner.

Would it make sense to include `owner: unassigned` in `Waiting on principal`? Even if I'm not the person who can answer the question, assigning it is still something I need to do.

For questions that already have an owner but block estimation, perhaps a separate `Estimation blockers` section would help. I'd mainly like to avoid losing sight of these questions once I move beyond the intent.

---

## Comment by pche-broken-artist, 2026-11-11 22:04 UTC

Thanks for this, and for tracing it down to the rule and the script. I'm working on it and will come back here with what changes.
