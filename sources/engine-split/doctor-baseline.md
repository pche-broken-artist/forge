origin: the report of the Claude Code command `/doctor`, run read-only in the session and written by Claude, with the counts its checks read; nothing was applied; paths replaced by `<engine>` and `<config>` before registration
date: 2026-11-14

# The `/doctor` checkup, the baseline before the rebuild of CLAUDE.md

The checkup ran read-only. It was a baseline measurement: nothing was
changed and no cleanup was put forward for confirmation.

The configuration is healthy and nothing in it is broken. The one
large item is `CLAUDE.md`. Claude Code's own measurement over the last
seven days attributes 21 % of the usage to it.

## What costs context

| Component | Kind | Uses, total | Used in the window | Estimated tokens in every session | Verdict |
|---|---|---|---|---|---|
| `CLAUDE.md` | project instructions | n/a | always | 14.8k (estimate from disk; `/context` measures 18.8k) | shorten |
| `CLAUDE.local.md` | local instructions | n/a | always | 65 | fine, nothing repeated |
| 32 skills of the forge | project skills | 253 | 16 of them | about 1.2k for the listing | keep, they are the forge's commands |
| 15 agents of the forge | project agents | n/a | yes | 1.7k | keep |
| MCP servers | connections to tools | none of the project's own | no calls | deferred, 0 | nothing to clean |

Window: the 50 most recent sessions over 27 days (2026-10-18 to
2026-11-14) in two projects.

## Findings by check

- **Installation (0):** in order. One native installation, every
  settings file parses, 15 agents and 32 skills with no error in their
  front-matter and no collision of names.
- **Unused extensions (1):** none that the user installed himself.
- **Local instructions (2):** `CLAUDE.local.md` has three lines and
  repeats nothing. No user-level `CLAUDE.md` exists.
- **Derivable content in `CLAUDE.md` (3):** the repository layout, 204
  lines, can be derived by listing directories. The table of commands,
  35 lines, is the same as the listing of skills. The file has 59,023
  characters and 920 lines. On a model with a context of a million
  tokens it does not trip the size warning; on a model with 200k
  tokens it does (the threshold is 40,000 characters).
- **Moving to loading on demand (4):** the rules of single commands
  into their skills, the rules bound to a kind of file into rules with
  a path filter. Estimate: about 690 of 920 lines, roughly 11k tokens
  out of every session and every run of an agent.
- **Slow hooks (5):** none. The walkthrough hook ran 1,930 times,
  median 45 ms, maximum 699 ms. The git hook ran 19 times, median
  71 ms, maximum 103 ms.
- **Version (7):** 2.1.325, the latest on the channel `latest`.
  Background auto-updates are switched off.
- **Default permission mode (8):** no settings file sets one; the
  session ran in auto mode. No proposal.
- **Frequently denied commands (9):** 20 denials in 27 days, nearly
  all by a rule of the project on compound commands. No purely
  read-only command repeats. No proposal.

## What `/usage` flagged for the last 7 days

- 61 %: start a fresh session when the task changes (`/clear`).
- 21 %: trim `<engine>/CLAUDE.md`, 15k tokens per request.
- 15 %: agents of the type `general-purpose`, in that week the
  research agents, which run on the session model by the forge's rule.

## Estimate of `CLAUDE.md` section by section

An estimate from reading the sections, not a line-by-line
measurement.

| Section | Lines | What it holds | Must stay always loaded |
|---|---|---|---|
| What this workspace is, Roles | 32 | conduct and orientation | about 22 |
| Prime directives | 66 | conduct; the item on assignments is a rule of the layer | about 55 |
| Working methods | 89 | conduct | about 80 |
| Document kinds | 40 | the table of 15 kinds is a catalogue; "immutable" and "append-only" are conduct | about 8 |
| Document chain | 145 | inputs 43, renders 59, documentation 13; the head on the chain is general | about 15 |
| Repository layout | 204 | catalogue | 0 |
| Persistence (git) | 96 | one rule of conduct; the rest is commands and script headers | about 12 |
| Versioning & status | 55 | the version scheme is conduct; the mechanics of records are the template's and the script's | about 20 |
| ID scheme | 38 | the format is conduct; the table of 20 prefixes is a catalogue | about 10 |
| Isolated reviewers | 68 | the contracts and three commands; the first paragraph is general | about 10 |
| Requirement style, Spin-off, Ledger | 33 | pointers and rules of one command | 0 to 3 |
| Commands | 35 | repeats the listing of skills | 0 |
| The system's own project, Templates | 18 | catalogue | 0 |
| **Total** | **920** | | **about 235** |

## Use of the forge's skills

Claude Code's counters: total uses since installation; in the window =
calls through the Skill tool and by slash command in the 50 most
recent sessions; listing = estimated tokens of the name and
description; body = estimated tokens of the whole file.

| Skill | Total | In the window | Listing | Body |
|---|---|---|---|---|
| challenge | 3 | 1 | 25 | 845 |
| challenger-contract | 0 | 0 | 67 | 1324 |
| check | 12 | 3 | 26 | 889 |
| check-contract | 0 | 0 | 59 | 1109 |
| critic-contract | 0 | 0 | 61 | 1474 |
| critique | 3 | 0 | 21 | 699 |
| docs-contract | 0 | 0 | 84 | 1340 |
| document | 2 | 0 | 32 | 1372 |
| end | 22 | 17 | 24 | 242 |
| forge | 74 | 24 | 21 | 1063 |
| history | 0 | 0 | 47 | 365 |
| import-project | 0 | 0 | 35 | 415 |
| ingest | 6 | 3 | 35 | 1807 |
| ledger | 3 | 0 | 10 | 159 |
| man | 2 | 0 | 62 | 1020 |
| manual | 0 | 0 | 17 | 64 |
| migrate | 0 | 0 | 44 | 494 |
| new-artefact | 0 | 0 | 36 | 1222 |
| new-project | 3 | 1 | 33 | 1054 |
| publish | 1 | 1 | 29 | 676 |
| pull | 13 | 12 | 39 | 506 |
| recipe | 7 | 2 | 23 | 604 |
| release | 4 | 0 | 62 | 2290 |
| render | 16 | 6 | 13 | 1491 |
| research | 10 | 3 | 32 | 3318 |
| save | 62 | 33 | 26 | 840 |
| setup | 1 | 0 | 73 | 1131 |
| spinoff | 0 | 0 | 23 | 505 |
| test | 3 | 3 | 31 | 371 |
| thread | 0 | 0 | 33 | 1189 |
| walkthrough | 0 | 0 | 62 | 1359 |
| work | 6 | 6 | 33 | 964 |

The four contracts and `walkthrough` are not invocable by the user;
agents and the hook load them, so the counter says nothing of them.
`thread` was born on 2026-11-12.

Agents dispatched in the window: docs-writer 360, general-purpose 81,
check-light 65, check-engine 12, check-project 8, docs-planner 6,
critic-clarity 4, critic-essence 4, claude-code-guide 3.
