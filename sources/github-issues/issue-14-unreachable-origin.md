# GitHub issue #14: /pull reports "up to date" when git cannot reach the origin (e.g. git's proxy not set), and blames a diverged history when the pull itself fails

Source: https://github.com/pche-broken-artist/forge-of-thought/issues/14  
Author: pavel576  
Opened: 2026-11-16  
State at download: open, downloaded 2026-11-17

**The situation**

I work behind a corporate proxy. The machine's internet connection
worked normally (browser, everything else), but git had no proxy
configured, so git itself could not reach github.com. Nothing told me:
`/pull` answered that every repository was up to date, so the forge
looked current while in fact it was not pulling anything. The point is that the
failure is invisible exactly when the rest of the machine is online:
there is no reason to suspect the network, and the forge's own status
line confirms that all is well.

**What I ran**

`/pull` (and its scripts directly). Reproduced on purpose by giving
git a dead proxy, set for one process only, which fails the same way
as a missing proxy behind a corporate firewall:

```
GIT_CONFIG_COUNT=1 GIT_CONFIG_KEY_0=http.proxy GIT_CONFIG_VALUE_0=http://127.0.0.1:9 \
  python scripts/forge-status.py --remote forge
GIT_CONFIG_COUNT=1 GIT_CONFIG_KEY_0=http.proxy GIT_CONFIG_VALUE_0=http://127.0.0.1:9 \
  python scripts/forge-pull.py forge
```

**What I expected**

Both scripts say that the origin could not be reached, with git's
reason, and the status does not report a state against the remote it
could not see.

**What happened**

1. `forge-status.py --remote` printed `remote: up to date` for the
   engine and the forge's own project, no error, exit code 0, while a
   plain `git fetch origin main` in the same setting fails with
   `fatal: unable to access ... Failed to connect to github.com:443
   over proxy ... Could not connect to server` (exit 128). Step 1 of
   `/pull` therefore tells the user everything is current when it may
   be several commits behind.
2. `forge-pull.py forge` failed, but with `ERROR: Pull failed in forge
   (engine) - local and remote history diverged; nothing pulled. Merge
   by hand, or scripts/forge-save.py rebases your commits onto the
   remote.` The history had not diverged; the advice sends the user
   the wrong way. Without a slug, the first unreachable repository
   ends the whole run.

**Cause**

- `scripts/forge_repos.py`, `remote_state()`: the result of
  `git(["fetch", "origin", branch], path)` is discarded, and the state
  is then computed from the last remote-tracking ref already on disk,
  i.e. from whatever the previous successful fetch saw.
- `scripts/forge-pull.py`: every non-zero exit of
  `git pull --ff-only` is read as a diverged history.

**Proposed fix**

- `remote_state()` checks the fetch; on failure it returns
  `could not reach origin: <first line of git's error>` instead of a
  state. `forge-status.py` shows it as a warning and exits non-zero.
- `forge-pull.py` fetches first; when the fetch fails it says the
  origin could not be reached, with git's line. With a slug it stops
  with an error; bare, it skips that repository, goes on with the
  others and exits non-zero at the end. The "diverged" message stays
  for a history that has diverged.
- Tests in `tests/test_git_scripts.py` with an origin pointing to a
  path that does not exist, covering both messages.

This adds a state word to the ones POS.1490 lists, so it may need a
position in the intent first; I leave that to you. Happy to send the
pull request if you want it.

**Version**

Forge of Thought 7.0 (engine at `8948075`), Windows 11, git 2.55.0,
Python 3.13.


---

## Comment by pche-broken-artist, 2026-11-17 21:16 UTC

Thank you for the report, and for the careful reproduction. Setting a dead proxy for one process made it easy to confirm.

We checked the cause against the code and it is as you describe. We think the finding is larger than the issue says, though.

**What we confirmed**

- `scripts/forge_repos.py`, `remote_state()`: the result of `git fetch origin <branch>` is discarded and the state is computed from the remote-tracking ref already on disk.
- `scripts/forge-pull.py`: every non-zero exit of `git pull --ff-only` is reported as a diverged history.

**Why it is larger**

`remote_state()` is not only behind `/pull`. The same function is read by:

- `forge-status.py --remote`, which is the gate of `/release`, `/publish` and `/document`. These refuse a repository that is behind or diverged from its origin. With an unreachable origin they see "up to date" and let it through, so a derived file can be made and released from a stale `main`.
- `forge-migrate.py`, which refuses a migration on a branch behind or diverged, by the same reading.
- `forge-save.py`, which reads the state to decide whether remote changes are integrated before the push.

So the question is not only what `/pull` says, but what each of these commands should do when the origin cannot be reached: refuse, warn and go on, or something else. That is a decision per command, not one message.

**What it touches**

- A new state beside the ones POS.1490 lists, as you noted, so the intent changes first.
- `remote_state()` and `forge-pull.py`, along the lines you propose.
- The behaviour of the release gate, the migration and the save on that state.
- Tests in `tests/test_git_scripts.py`, and the wording of the `/pull` skill and the `/forge` map, which list the state words.

We will take this up: the position in the intent first, then the fix. Your offer of a pull request is welcome; we will come back to it here once the position is written, so that the code has something to follow.
