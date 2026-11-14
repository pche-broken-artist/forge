---
project: forge
document: 00-brief-engine-split.md  # the versioned document this history belongs to
---

# History — 00-brief-engine-split.md

<!-- The history of a versioned document: CLAUDE.md, Versioning &
status. One record per change, one line each, appended at the end,
never rewritten:
- <date> | <version> | <author> | <subject> | <kind> | <reason> | Action: <what the user must do> | Was: <wording that ceased to hold>
Kinds: created | changed | closed | removed | approved. The subject
is an ID, several IDs where the whole line holds for each, or a
place without an ID: a section, the file, or in the forge's own
project the operating layer. Reason is left out on
`created`; `Action` and `Was` only where the record has them, `Was`
always last, paragraphs in it divided by `<br>`; a thread that
closes gets a `closed` record, no `Was` (the rules of a thread:
`.claude/skills/forge/states/intent.md`, Threads and files). At the birth of a
document, one record of the file and one naming every item born
with it. Lines are not wrapped. The author is the handle the
instance file gives its principal (CLAUDE.md, Versioning & status);
where it gives none, a write that would append a record stops before
it writes and offers `/setup`, which adds the line (POS.1050); the
handle is never guessed.
A record of state only carries the current version and does not
raise it (POS.1630). Its shapes: the mining of a brief, in the
intent's history with the brief's file as subject,
`00-brief-<name>.md | changed | mined: pending | partial | mined |
dropped, <note>`; a finding or a challenge settled, `FND.NNNN |
closed | <what fixed it>`, in the history of the artefact whose
version settled it, or of the intent where no version did or the
check was of the engine, resolved for a finding, accepted for a
challenge; a work product's state in its specification's history:
the making's record `<file> | changed | state: current; made <date>
from <the inputs with their versions>`, a write of the specification
after a making `<file> | changed | state: stale`, the principal's
word `<file> | changed | state: by hand`.
`rejected`, `parked` and `obsolete` are a decision's Verdict
(templates/decisions.md), never a record here (POS.1610). -->

- 2026-11-13 | 0.1 | PCHe | 00-brief-engine-split.md | created
- 2026-11-14 | 0.2 | PCHe | The ways the base could reach a layer | changed | The eight ways compared by the research of 2026-11-14 (research/2026-11-14-anvil-carrying-layers/) put into the brief as a section of its own, each in a few sentences with the research's score, and what every way needs and the forge lacks; the principal's word of 2026-11-14, since the ways will be returned to. None decided. | Was: The three ways the base could reach a layer at every session, none decided: one repository with the layers as directories in it; the base as a package of its own with each layer a repository of its own; two repositories joined by an import and a clone alongside.
- 2026-11-14 | 0.2 | PCHe | The ways the base could reach a layer | changed | Scored again the same day with the sustainability of the context added and function first, out of 85; a ninth way added, one repository with the rules of a kind of project loaded only in its projects; the order by the new score; two scores moved by one when the rules of scoring were written down (the base as a plugin 52, a plugin alone 44). The principal's word of 2026-11-14: with every kind of project the context swells, and CLAUDE.md is long already. | Was: Compared in the research of 2026-11-14 (source: `research/2026-11-14-anvil-carrying-layers/00-plan.md`), none decided. The score in brackets is the research's own judgement out of 65, the central update counted three times and the cost of the cut twice (remark: a judgement, not a measurement).<br>1. **One repository, the layers as directories (58).** The forge stays one repository; what is base and what is the forge layer is marked in it. A project that is not the forge lives in a clone of the whole as a kind of project without a chain. The central update exists today through the pull; the base is not a thing of its own and such a project carries the forge layer too. 2. **The whole kept, the base released apart by a script (56).** As 1, and at every release a script writes the files marked as base into a public repository of its own, from which projects that are not the forge pull. Established practice; two public repositories, the base's read-only; the mixed files must be parted first. 3. **The same, the base released in the form of a plugin (40).** Claude Code checks the version a layer needs; the always-on rules still have to be written into every project, and a plugin's updates have been seen not to arrive. 4. **A plugin for the executable parts, the rule text in the project's tree (40).** An update writes into no file a user or a layer owns; two things are kept in step and every call of a script is rewritten. 5. **Two repositories side by side joined by an import (37).** The layer's CLAUDE.md imports the base's from the folder beside it. No packaging; a dialog on the first run whose refusal is silent and permanent, and the neighbour's hooks and settings do not load. 6. **The base a package, each layer a repository (36).** The cleanest picture; no carrier of its own in Claude Code, so it ends as 3, 4, 5 or a copy; the field retreated from it twice. 7. **A plugin alone (32).** The user's repository stays clean; the rules reach the session or the reviewers, not both. 8. **User-level configuration (31).** No dialog; one base per machine for every project and no channel of update.
- 2026-11-14 | 0.2 | PCHe | How the ways are scored | changed | A section of its own: the ten measures with their weights, what each score from 1 to 5 means, and the breakdown per way; the principal's word of 2026-11-14 that the ways are scored by the same rules every time, or they cannot be worked with.
- 2026-11-14 | 0.2 | PCHe | The order I see | changed | The steps to walk one at a time added, the ways scored again as what is tried develops, and the bare kind of project placed after the division of CLAUDE.md; the principal's word of 2026-11-14.
