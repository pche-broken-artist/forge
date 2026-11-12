---
id: THR.0870
concerns: intent
origin: the principal
status: open
---

The priority of a thread. The principal's idea of 2026-11-10, when
the split of large files was set aside (THR.0860): a thread carries
a priority, high, medium or low, and low does what a parked thread
would; a state `parked` alone he finds of no use. Nothing is forced:
a thread without the field counts as medium, so that no project is
migrated; at the birth of a thread Claude asks for it; the threads
a project already has are sorted by a walkthrough where the
principal wants it, in the forge's own project first. The map of
`/forge <slug>` then shows the high ones, or the first five by
order. Open: which of the two the map shows, a count being what the
forge's rules avoid (kind, not count), Claude's remark. What it
would touch: POS.1680, the thread's template, the intent's
definition, the ledger script and the map. Not decided. Opened
2026-11-10.

2026-11-10: the skill is wanted, the principal's word: threads get a
skill of their own, `/thread`. What it does is open.

2026-11-11: the skill `/thread` taken up in conversation, unfinished,
nothing decided. The principal's words: the birth of a thread is what
the forge does most often and is to be standardised, since Claude
writes each as it comes and will do so for every other user; a thread
is to him, from the start, something to be done for which there is no
time or priority now, a task, a question, a decision, anything; the
forge is to be a framework that does not lace people in; the worth of
a thread is that a matter is set aside fast, which means no useless
questions, not no questions; one input may give several threads with
different fates (a comment with two ideas, one to be done, one to be
thought over and probably rejected); a priority so that Claude can
sort them, a walkthrough of thirty threads being no offer. What is to
be defined, his list: what a thread is, its template, what is held and
what is not, what Claude asks at the birth and what not, what Claude
keeps up by himself. Claude read all 67 threads of three projects on
the day: the header is uniform, the four fields of the template; the
body has no shape, the template giving one placeholder line. The first
sentence, which the ledger prints, is a label of a few words in about
half, a question in some, the whole matter in the newer ones; the date
of opening is missing in one project and stands in different places;
a continuation is written three ways, one of them inside the first
paragraph where the ledger does not read it; what is open goes under
two names or none; a setting aside under four words; the origin is
often repeated in the body; `Owner: principal` ends the threads of one
project only. The newer threads of the forge (THR.0730, THR.0760,
THR.0800 to THR.0830, THR.0880) share a shape nobody prescribed: the
matter in one whole sentence, the situation with its evidence, what is
to be settled, Claude's view marked, the date. Claude's remarks, his
own and not judged: work is not done in a thread, a matter grown into
a plan or a record of work under way moving to a brief or a work
product (THR.0640), which narrows POS.0120; one thread, one matter; a
thread says what will close it, a sentence and not a field. Open at
the break, the first of the five: Claude's wording of what a thread
is, shown and not judged: "A thread is one matter of a project set
aside to be taken up later: a task, a question, a decision to make,
an idea; the forge does not ask which. It says what the matter is,
where it came from, how much it matters and what will close it, and
carries what is known of it until it is taken up. Work is not done in
a thread: a matter that has grown into a plan or a record of work
under way moves to a brief or a work product, and the thread points
there."

2026-11-12: the walkthrough of the five matters of the skill
`/thread`, unfinished: three agreed, the fourth shown and not judged,
the fifth not begun. Nothing of it stands in the intent, the template
or a skill yet; this thread is the only place. Agreed on the
principal's verdicts, the wordings below. One, what a thread is: the
wording of 2026-11-11 without its last sentence, "Work is not done in
a thread", which was Claude's and which the principal struck: a
thread may carry a new direction or a new feature with its plan, and
POS.0120 stays as it is. Two, the header and the template: three new
fields. `priority: high | medium | low` in every thread written from
now on; a thread without the field is read as medium, a fallback for
projects nobody has brought over and not a reason against a
migration, which the principal will run once on his own projects, how
being open (through `/migrate` or otherwise, every thread medium or
sorted on the way). `blocks`, optional and free text, a short name of
what waits on the thread, a layer, the next major, a new artefact;
without it nothing waits; the map shows the threads with `blocks`
first, then the rest by priority. Weighed and not taken: blocking as
a fourth degree of the priority, a fact and a judgement in one field;
`blocks` as the name of a layer only. `owner`, the handle of whoever
opened the thread, filled at the birth from the instance's Author
without a question, changed when the thread is handed over; not from
the git identity, which a project outside git lacks and which would
put a name and an address into a public file. The author of an issue
stays in `origin`, by the path of the source. The body: the template
below. Three, what a thread holds and what not: the wording below.
Open at the break, four, what Claude asks at the birth: the
principal's word is that Claude asks for the priority and for whether
anything waits on it, where Claude had proposed to suggest the
priority unasked; Claude's wording after that word, shown and not
judged, is the last below, its two points his own: the question
carries the priority Claude would give, and the answer is the consent
to write. Five, what Claude keeps up by himself, not begun. Also
open: where the definition stands (POS.0120, the intent's definition
or the skill), and the first paragraph of this thread, which still
says that no project is migrated.

What a thread is, agreed:

> A thread is one matter of a project set aside to be taken up later:
> a task, a question, a decision to make, an idea; the forge does not
> ask which. It says what the matter is, where it came from, how much
> it matters, what waits on it where something does, and what will
> close it, and carries what is known of it until it is taken up; an
> unfinished conversation on the matter is saved into it.

The template, agreed:

```
---
id: THR.NNNN
concerns: intent          # the artefact it concerns, as /forge names it; several, comma-separated
origin: the principal     # the principal (the default) | <a document by path> | Claude's synthesis
owner: <handle>           # whoever opened it, from the instance's Author; changed when the thread is handed over
priority: medium          # high | medium | low
# blocks: <what waits on it>   only where something does
status: open              # open | closed
---

<The matter in one whole sentence; the ledger prints it.> <The
situation and what is known of it.> <What is to be settled and what
will close the thread; for a thread from an issue, that the issue is
answered.> <Claude's view where he has one, marked as his.> Opened
YYYY-MM-DD.

YYYY-MM-DD: <a continuation, one dated paragraph each time the thread
is taken up; the ledger prints the last.>
```

What a thread holds and what not, agreed:

> A thread holds its one matter and what is known of it while it is
> unsettled: the situation and its evidence, what was said and tried,
> the plan of a change under way, the proposals that await a decision,
> an unfinished conversation, Claude's view marked as his. Every
> continuation says where the matter stands and what is open now.
>
> A thread does not hold: a second matter, which is a thread of its
> own; what has been decided, which goes into the artefact it
> concerns; the text of a source, which is cited by path; its origin a
> second time, which the header says; and the thing being made, a
> brief, a specification, a document, which lives in its own file with
> the thread pointing there.

What Claude asks at the birth, shown and not judged:

> At the birth of a thread Claude asks for what only the principal
> knows and for nothing else: its priority, and whether anything waits
> on it. He drafts the thread whole from what was said: the matter,
> what is known of it, what it concerns and where it came from; he
> shows the draft once and closes it with that one question, saying
> the priority he would give. The principal's answer is the consent to
> write the thread as shown; a change to the draft is said instead of
> the answer. An input that holds several matters is shown as several
> threads in the one draft, and the question is answered for each.
> Beyond that Claude asks only where the matter itself is unclear,
> what is being set aside or which of two readings is meant: one
> question, on the matter, never on the form. He does not ask for the
> kind of the matter, for what will close it where nobody knows yet,
> for the owner or the date, and does not confirm one field at a time.

<!-- A thread (POS.1680), one file per thread in threads/; the header
is its state: what it concerns, where it came from, whether it is
open. The rules of a thread, its life and its closing:
`.claude/skills/forge/states/intent.md`, Threads and files. -->
