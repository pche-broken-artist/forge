# GitHub issue #16: forge-engine.py: the per-run profile does not carry the antigravity login, so every run stops at "Authentication required"

Source: https://github.com/pche-broken-artist/forge-of-thought/issues/16  
Author: smidf-allwyn  
Opened: 2026-11-24  
State at download: open, 0 comments, downloaded 2026-11-26

**What I ran.** `/research --deep --engine antigravity`, which runs `python scripts/forge-engine.py antigravity --packet <run>/plan-review --out <run>/plan-review/antigravity.md --allow-all --sandbox`. To isolate it, I also ran a one-sentence packet ("Reply with the word OK and nothing else.") the same way, then with `--no-profile`.

**What I expected.** The engine finds the login I made once in `agy` itself and answers, as the script's header says was verified on 2026-10-24 ("the login is found").

**What happened.** Through the profile, every run ends with `Authentication required. Please visit the URL to log in: …` and `Waiting for authentication`. The run is non-interactive with stdin closed (header, step 3), so there is no place to enter the authorisation code and it waits until the timeout. The same packet with `--no-profile` passed at once (one turn, about 16 s) while my login was valid.

Cause, as far as I can see: `agy` keeps its login in files at the root of `~/.gemini` (`oauth_creds.json`, `jetski-standalone-oauth-token`), but the profile the script builds under `tmp/research/.home/.gemini` holds only `antigravity-cli/` and `config/`, so the engine never sees the login. I do not know why the check of 2026-10-24 found it; perhaps the place of the login moved between agy versions, or Windows keeps it elsewhere.

Two suggestions: make the profile reach the login files without opening the deny rules, and recognise an authentication answer so that a run stops at once with a plain message instead of waiting for a code it cannot get.

**Version.** Forge 7.0 (`main` at 8948075, intent 7.11); agy 1.5.4, 1.5.13 and 1.5.16 (it updated itself between runs), all the same.

**Operating system.** macOS 27.2.1, Python 3.15.2.
