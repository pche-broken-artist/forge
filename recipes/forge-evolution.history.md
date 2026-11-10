---
project: forge
document: recipes/forge-evolution.md
---

# History — recipes/forge-evolution.md

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

- 2026-11-09 | 0.1 | PCHe | recipes/forge-evolution.md | created
- 2026-11-10 | 0.2 | PCHe | recipes/forge-evolution.md | changed | the render of 0.1 judged not good by the principal: the blocks were not separated; each block a box of its own, step 4 with Anvil one long box at the left, the frameworks and the definitions in two columns beside it; the picture pinned as a plain figure in place of the mermaid grid, which spans columns only and cannot draw a box across rows (THR.0850) | Was: The diagram is pinned: a grid of equal boxes, three rows (definition, framework, Anvil), the steps left to right, a box holding a name only. A dashed outline marks a layer not yet separated from its neighbour.<br>\| solid outline \| a block of its own, its own repository \|<br>\| dashed outline \| a layer inside one block, not yet separated \|
- 2026-11-10 | 0.3 | PCHe | recipes/forge-evolution.md | changed | the figure of 0.2 was a check drawn in the conversation, not the output the principal wanted; the recipe renders a `png` drawn by the renderer (SOL.0940, POS.0590), the picture as tuned with the principal: the step headed on two lines so the number never reads as a version, the forges by their whole names, one fill per layer, the legend without box and line, the working names said | Was: The picture is pinned: the figure of the Template copied as it stands, character for character, in a plain code block, so that it draws the same on GitHub, in a terminal and through pandoc. A box is a block, a repository of its own; a line inside a box divides the layers of one block. Steps 1 to 3 stack the layers, definition above framework above Anvil, the steps left to right; step 4 turns: Anvil one box the whole height at the left, the frameworks in a column beside it, the definitions in a column at the right, one forge per row.<br>the Template's figure in characters, never saved to git<br>\| box \| a block: its own repository \|<br>\| line inside a box \| the boundary of two layers inside one block, not yet separated \|
- 2026-11-10 | 0.4 | PCHe | recipes/forge-evolution.md | changed | the width of the picture stated, 3840 px with the height from the content, the principal's word (SOL.0940); the equal height of the layers across steps cut, since with equal steps and gaps between blocks it cannot hold, as the renderer of 0.3 reported | Was: line. The three layers have one height in every step.
- 2026-11-10 | 0.5 | PCHe | recipes/forge-evolution.md | changed | Anvil bold, so that it reads as a name like the forges' names, the principal's word | Was: Anvil carries its name alone.
- 2026-11-10 | 0.6 | PCHe | recipes/forge-evolution.md | changed | "AI engine" above Anvil, plain, as "framework" stands above a forge's name, so that the base is named by its layer like the others, the principal's word | Was: Anvil carries its name alone, bold, as a forge's name is.
