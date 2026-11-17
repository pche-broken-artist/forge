---
version: 0.1
status: draft
project: forge
file: work/conduct-measure.md
---

# Conduct measure — Work specification

<!-- Shape: templates/work.md -->

## Task
One table of how the forge behaved toward the principal, counted
again after each step of the plan of the brief `engine-split`, for
the principal and Claude: a step is judged by the same two shares
each time, and the row of every measurement stands beside the rows
before it.

## Inputs
- sources/engine-split/conduct-baseline.md: the first measurement, of 2026-11-16, and the way of counting
- 00-brief-engine-split.md: the section The plan, what keeps it safe
- threads/THR.0240.md
- the session logs of Claude Code on the principal's machine, outside the project and never copied into it

## Method
A row is one period of the principal's messages on one model. A
message is what he typed, counted by the model that answered just
before it; a command, the text of a skill, a message of an agent, the
summary a continued session opens with and a tool's result are left
out. Two shares are counted. The first is the share of his messages
that carry a strong sign of dissatisfaction, a word or phrase of a
fixed list. The second is the share of modify and reject among his
verdicts, a verdict being a message that opens with one of the five
letters.

The periods are cut by the steps of the plan: before a step began,
while it was done, after it was saved, by the time of a message in
UTC as the logs carry it.

The rules of the table:
- A row is added and never counted again: the logs go with time, and
  a row says what was counted on its day.
- A row says how it was got, the script's own output or the
  difference of two of its runs.
- The rows of the baseline are its figures, cited and not counted
  again.
- What limits a measurement stands under the table, by its day.

## Assumptions
- **ASM.0400** Where the counts of an earlier measurement cannot be repeated from the logs of the day, the periods are compared inside the logs of that day and not against the earlier figures; chosen against scaling one to the other.
- **ASM.0410** A text the principal pastes from another session counts as a message of his, as it did in the baseline; chosen against sieving it out, which would change the way of counting between rows.
- **ASM.0420** After the baseline only the model of the sessions is counted; a second model gets rows when sessions run on it.

## Open
- **TBC.0400** (owner: PCHe) Where the script and its list of words live: they stand in the engine's working folder, outside git, and the list is the principal's own words of displeasure, which a public repository may not be the place for. Closed by: his word on a place, or that the working folder is enough.

## Making
Claude runs `tmp/conduct-logs/logs_rate.py` of the engine's working
folder, read-only, over the folder of the forge's session logs, once
for each bound of a period (`--since`), and writes
`work/conduct-measure.md` in English: the table, one row per period,
and under it the limits of each measurement by its day. Of this
specification the file carries the names of the columns and one
sentence on what is counted. A later making adds rows and limits and
changes nothing that stands.
