# GitHub discussion #13: A forked repo cannot follow the original one from the Forge in terminal: "/pull" reads the fork only

Source: https://github.com/pche-broken-artist/forge-of-thought/discussions/13  
Author: stasidom-allwyn  
Opened: 2026-11-13  
Category: Ideas  
State at download: closed as resolved, 2 comments, downloaded 2026-11-19

Hello! I would like to open a discussion on solving a following problem of mine.

CONTRIBUTING.md sends a contributor to a fork and says that the
fork's main "stays clean for the upgrades of the engine". The forge
has no way to bring those upgrades in.

What I ran: I forked both repositories, pointed both clones at my
forks and ran /pull forge.

What I expected: that /pull, the upgrade channel, brings a new
version of the engine, as it does on a direct clone.

What happens: scripts/forge-pull.py reads the remote named origin
and no other. On a fork, origin is my fork, and a fork does not
move when the engine does. So /pull will say "up to date" while the
engine has gone on, until I open GitHub and click "Sync fork" on
both forks, or run git by hand against a second remote. Neither is
a way of the forge, and the second is a write of git outside the
scripts.

My forks are a day old, so I have not been left behind yet. I read
this from the script and from how a fork works, not from a release
I missed.

What I wish for: that a fork follows the engine through the forge's
own door, or at least that /pull says the origin is a fork and
cannot tell whether the engine has moved.

Version: release 7.0 by RELEASE-NOTES.md, main at 6533c65 (the intent at 7.8). Windows 11.

---

## Comment by pche-broken-artist, 2026-11-19 18:58 UTC

Sorry for the week of silence, and thank you for the finding: it is real. I confirmed it in the code. `scripts/forge-pull.py` asks the remote named `origin` and no other, so on a fork `/pull` compares your clone with your fork and says "up to date" while the engine has moved on; and CONTRIBUTING promises more than the forge does.

A real solution is not small, though. Git itself does not know what a fork is: that is a notion of GitHub. So the forge would either lean on GitHub's own tool, `gh`, which is optional today and needed by nothing the forge does at its core, or keep a second remote in the clone of every fork and say the state of every repository against two remotes, in each command that reads it.

Right now I do not know whether I want that in the forge at all. The forge is a workshop for thought: its work is the chain of documents and their review, and git is only how that work is kept. I want to spend the effort there, and not grow a wrapper around GitHub beside it; what GitHub already does well, the forge does not need to do again.

So for now nothing changes in what `/pull` does, and a fork is kept current by hand: "Sync fork" on GitHub, on both forks, and then `/pull`, which brings the synced `main` down. I will correct CONTRIBUTING so that it says this and no longer promises what the forge does not do. The smaller half of your wish, that the forge at least says when the origin is a fork and the engine has moved on, I will consider, but not now.

---

## Comment by pche-broken-artist, 2026-11-19 19:04 UTC

CONTRIBUTING is corrected on `main` (61cb49a): it no longer says that the fork's `main` stays clean for the upgrades of the engine, and it says how a fork is kept current by hand. Closing with this; reopen if it still reads wrong.
