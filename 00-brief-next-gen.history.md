---
project: forge
document: 00-brief-next-gen.md
---

# History — 00-brief-next-gen.md

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

- 2026-10-03 | 0.1 | PCHe | 00-brief-next-gen.md | created
- 2026-10-03 | 0.2 | PCHe | 00-brief-next-gen.md | changed | The eighteen researches of 2026-10-03 run and cited under the sections they serve, each with a line or two on what it found and, where it limits a thought of the brief or leaves a question to the principal, saying so; no need reworded. THR.0520, opened from the talk over the brief, linked under what already stands in the intent and in the two sections that rest on it. What is still open rewritten: where the researches disagree and what they rest on. | Was: - What Claude Code itself already carries of all this.<br>- Research, proposed and not yet run: how comparable frameworks and Claude Code itself solve extensions kept apart from the core, upgrade, several people on one project, the testing of behaviour, and documentation with news. So that we do not invent the wheel.
- 2026-10-09 | 0.3 | PCHe | section Documentation and news | changed | The documentation and the cut of the README are a whole of their own and left for the brief `documentation`, born the same day from THR.0340; the section keeps the news, which the principal set apart as a round of its own, and is renamed News. | Was: The README is today the documentation, and that is not good: it is very long and poor as documentation. The README is to be short: what the forge is and what it is for, perhaps the current news. The documentation is a normal series of documents on single topics, separate linked pages on which a topic can be described well. It is for people inside the company and outside it, so that they understand the forge and use its potential in full.<br>Research: `research/2026-10-03-how-project-documentation-is-built.md` and […]. The README orients and points; one page, one topic; plain pages in `docs/`, the reference derived from the definitions; no need to wait for the split.
- 2026-10-22 | 0.4 | PCHe | section Where it stands on 2026-10-22 | created
- 2026-10-22 | 0.4 | PCHe | 00-brief-next-gen.md | changed | The plan of THR.0620 folded into the new section, the thread closed; the principal's word that the brief is worked through again before it is mined.
- 2026-11-13 | 0.5 | PCHe | sections The shape of the whole and User modifications, What already stands in the intent, Where it stands on 2026-10-22, Still open | changed | The shape of the whole and the user modifications are a whole of their own and left for the brief engine-split, born the same day from the two sections; the threads they carried (THR.0300, THR.0480, THR.0230, THR.0420) and the first open point go with them; What the forge is keeps one sentence pointing there. | Was: ### The shape of the whole<br>One question that frames the others: one general forge, a core with frameworks on it, or several forges that hand artefacts to each other. I see the split on two levels: the forge as it is today, to which a user adds things of his own, and beneath it a core that is separate from the artefacts. Whether to divide it or to call it a generalisation of the forge is open; the measure is to be found. The ambition itself may need revisiting: whether we are not heading somewhere that cannot be managed. Open too is how this stands to my word of 2026-09-26 against one tool that does everything.<br>Research: research/2026-10-03-one-tool-a-core-with-modules-or-several-tools.md. Everyone surveyed ended at a small core that owns mechanism and format, with the content outside it; nobody runs several equal tools with a designed hand-over, and retreats from too much division are common. It advises not to divide now and to try first on one real case. This section rests on THR.0520: where the solution lives decides what the core is.<br>### User modifications<br>The forge is to be highly customisable. It comes as a base framework: the core is kept and maintained centrally, and every user can add artefacts, elicitations, challengers, critics and checks of his own. What is central and what is the user's is never mixed; the user's ideally lives in his own git. There is one place with the list of every type that can be created, and skills or commands by which a user creates new types of his own. Naming conventions are needed with it, also against a collision of names. A possible support: the boundary between mechanism and instance.<br>Research: research/2026-10-03-user-extensions-kept-apart-from-the-core.md. The user's things live where an upgrade never writes; the field is split on whether a user's thing may shadow a core one of the same name or may only be added beside it. When the engine renames a contract, a user's agent runs without it and nobody is told. Claude Code has no mechanism for artefact definitions and templates.<br>Threads this brief carries whole: THR.0340, THR.0300, THR.0480, THR.0230, THR.0420, THR.0500, THR.0090, THR.0240, THR.0150, THR.0460.<br>[...] a user's own extensions (THR.0300, THR.0480) before the engine split (THR.0230, THR.0190); [...]<br>- Whether user modifications are the engine split or a level of their own; the field treats them as a level of their own on the same mechanism.
