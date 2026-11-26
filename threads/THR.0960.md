---
id: THR.0960
concerns: solution-design
origin: sources/github-issues/issue-16-profile-without-login.md
owner: PCHe
priority: medium
status: open
---

The per-run profile of `scripts/forge-engine.py` does not carry the
engine's login, so that on macOS every run through it stops at
"Authentication required" and waits until the timeout. Issue 16
reports it with `agy` 1.5.4 to 1.5.16: the same packet passes at once
with `--no-profile`, and the reporter found the login in files at the
root of `~/.gemini`. Read in the script on 2026-11-26: `profile_for`
writes the settings file alone and starts the engine with HOME and
USERPROFILE pointing at the run's `.home`; nothing of the login is
brought there. The header and SOL.0870 say that the login is found,
verified 2026-10-24, without saying on which system. Not verified:
where `agy` keeps its login, on macOS or on Windows.

To be settled: how the engine finds the user's login under the
profile, the deny rules kept and the forge keeping no key (POS.1880;
the profile stays as the run's record, so a login copied into it
would stay there too); whether a run that answers with a request to
log in stops at once with a plain message, the reporter's second
suggestion; and what the header and SOL.0870 say of the check of
2026-10-24. Closed when the script is changed and tried on macOS and
on Windows, or the matter is dropped, the header and SOL.0870 say
what holds, and the issue is answered. The principal's word of
2026-11-26: he does not know how he is to solve a problem on macOS.

Claude's view, his own: the two halves part. Stopping at once is
small, can be built and tested here with the engine stood in for, and
is worth doing first. The login needs the vendor's documentation read
first and a trial on a Mac, which this machine cannot give; the way
open is to ask the reporter, who has the system and found the cause,
for a pull request or for a trial of a change. A hypothesis,
unverified: the check of 2026-10-24 ran on Windows, where `agy` finds
its login in a place the two variables do not move. THR.0740 is the
open thread of the link itself and holds what was built on
2026-10-24. Opened 2026-11-26.

2026-11-26: answered in the issue
(https://github.com/pche-broken-artist/forge-of-thought/issues/16#issuecomment-7204036530):
the cause confirmed from the script, stopping at once agreed, the
constraint on the login said, a pull request for the login half
invited, and a change promised for the reporter to try when the
thread is taken up. Open now: both halves, nothing built yet.

<!-- Shape: templates/thread.md -->
