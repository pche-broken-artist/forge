---
id: THR.0880
concerns: intent
origin: the principal
status: open
---

A script for every write that only appends. The principal's word of
2026-11-10, after a record was put above the last line of a history
instead of after it: Claude writes the records of a history and the
decisions through the text editor, which can place a line anywhere,
and misses the end often enough that the rule of an append-only file
should be held by a mechanism, not by conduct. The want: a record is
appended at the end of its file by a script and by nothing else.
Claude's proposal, not decided: one script, its subjects the history
companions and `decisions.md`, which takes the fields of a record,
the date, the version from the document's header, the author from the
instance file, the subject, the kind, the reason, `Action` and `Was`,
checks them against the shape `templates/history.md` owns, writes one
line at the end and nothing else; a DEC the same way in the shape of
`templates/decisions.md`. Open: whether the text editor is then denied
on these files, as the git hook denies git, or only the script is the
rule; whether the reflection before a write shows the records as the
script will write them. Opened 2026-11-10.

<!-- A thread (POS.1680), one file per thread in threads/; the header
is its state: what it concerns, where it came from, whether it is
open. The rules of a thread, its life and its closing:
`.claude/skills/forge/states/intent.md`, Threads and files. -->
