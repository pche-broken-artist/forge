---
date: 2026-11-21
project: forge
topic: methods of judging an interface design before it is built, their inputs, and language models as evaluators
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-15-judging-a-proposal
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 15; no known note named by the card; web sources below
---

# An interface design is judged before it is built by inspection methods that accept a detailed description; language models perform them with partial coverage and over-reporting

<!-- Shape: templates/research.md -->

## In short

The established methods are the usability inspection methods named
together in 1994 (heuristic evaluation, cognitive walkthrough,
consistency, standards and feature inspection, pluralistic walkthrough,
formal inspection), with the expert review and the design critique
beside them. By their own literature none needs a running system or a
picture: heuristic evaluation is described on "a prototype or a paper
description of the design", the walkthrough "does not require a fully
functioning prototype", the expert review may read "a set of
specifications". What each needs is detail and companions: the
walkthrough the users, a task and the complete written list of its
actions; the critique agreed objectives; a standards inspection the
standard. One difference between paper and a running system was
measured: what is missing from a design is harder to find on paper. No
page opened compares a prose description with a picture. Evaluators
disagree: a review of eleven studies puts the agreement of any two
between 5% and 65%, and the remedy is several independent evaluators.
Language models were measured as evaluators in nine studies of 2024 to
2026, one read as its abstract and one through a news item, on
screenshots, on a JSON form of a mockup, on source code and on screen
recordings, never on a prose description. They find real problems,
largely other ones than humans find; between about a sixth and two
fifths of what they report was judged wrong; their precision is below
the human's wherever both were measured; they are weakest across
screens and on conventions. A model finds as much as one human alone or
more; whether it finds more than a group of experts is contested. The
disconfirming queries found what was expected, with one correction:
inspection by heuristics over-reports in human hands too, by about
half against tests with users in a vendor's summary of three studies.
The unexpected: designers asked to rate a model's findings barely
agreed with each other; a model walking an interface completes the
tasks better than people do and so reports fewer points of failure;
and a long checklist is reported to narrow a model reviewer. Sureness
is moderate: every page was read through a summarising fetch and the
methods' original papers were not read. The run had two rounds, the
first cut short by the session's search allowance; after the second
the design critique and the review by checklist still have no primary
source.

## Question

The frame, abridged by the agent: a framework carries an idea down a
chain of versioned Markdown documents worked by a human with an AI
agent; its author wants the same for the interface of an application,
a description in text that an agent proposes, a human tunes and a
build stage receives; a wide research of twenty-two cards asks how
this is done elsewhere, and this card asks only how a proposal is
judged.

The card, verbatim:

> #### Card 15: How a proposal is judged before it is built
> - **Question:** By which established methods is a design of an
>   interface judged before it is built (heuristic evaluation,
>   cognitive walkthrough, design critique, expert review by
>   checklist, inspection of consistency): what does each look at,
>   what does it need as its input (can it be run on a textual
>   description, or only on a picture or a prototype), and what is
>   known about language models performing such an evaluation?
> - **Why it matters:** a proposal made by an agent is tuned by a
>   human and read by reviewer agents; the description must be
>   something that can be judged.
> - **What would answer it:** the original literature of the methods
>   and recent studies of automated evaluation.
> - **Where to look:** the literature of usability inspection
>   methods; writing on design critique; studies of 2024 to 2026 on
>   models as evaluators of interfaces.
> - **Disconfirming query:** "heuristic evaluation unreliable
>   evaluator effect", "LLM usability evaluation false positives";
>   expected: evaluators disagree, and models over-report.
> - **Stop rule:** nothing new from a differently worded query and
>   every route has a primary source; ten to fifteen pages opened.

Known items: none; the packet attaches no note.

The baseline the note must beat is what a reader already holds
without research: that heuristic evaluation and the cognitive
walkthrough exist, that reviewers disagree and that models invent
problems. The note beats it only where it says, per method and with a
source, what the method takes as input and whether text is enough, and
where it gives measured figures for models together with what the
model was shown.

## Key findings

How the pages were read: every page of this note was read through the
engine's fetch tool, which returns a small model's answer about the
page and not the page's text. By the brief that is a summarised fetch,
and every finding below rests on one. Quotes are the fragments the
tool returned when asked for verbatim text; figures are as the tool
reported them and deserve a look at the page before anything is built
on a single number. The findings keep the numbers of the first round;
what the second round added or changed is marked, and F13 and F14 are
its own.

**F1. The established methods are the family named "usability
inspection" in 1994, with the expert review and the design critique
beside it; of the card's five names, "expert review by checklist" has
no method of its own in the pages opened.** [consensus; two summaries
by the originator of heuristic evaluation, a textbook and a tutorial
by authors of the walkthrough, two practitioner articles; all
summarised fetches; confirmed in the second round by [14] and [15]]
The 1994 summary names eight methods: heuristic evaluation, heuristic
estimation, cognitive walkthrough, pluralistic walkthrough, feature
inspection, consistency inspection, standards inspection and formal
usability inspection [1]; the same author's tutorial of 1995 names
the same without heuristic estimation, in the same words [14]. What
each looks at and takes in:

| Method | What it looks at | What it needs as input | On a textual description? |
|---|---|---|---|
| Heuristic evaluation | every element of the dialogue against a short list of usability principles [1][14] | the interface in some form, the heuristics, several evaluators working alone, three to five [2][3] | yes: "a prototype or a paper description of the design" [3]; on paper what is missing is harder to find [16] |
| Cognitive walkthrough | whether a first-time user will try, see, recognise and understand each action of a task [3][15] | a description or a prototype, a task, the complete written list of its actions, an idea of the users [3][15] | yes, if "fairly detailed" [3]; it "does not require a fully functioning prototype" [15] |
| Pluralistic walkthrough | a scenario stepped through in a meeting, each dialogue element discussed [1] | a scenario; users, developers and human-factors people together [1][14] | not said in the pages opened |
| Feature inspection | the sequences of features used for typical tasks: long sequences, cumbersome steps [1] | typical tasks and the feature sequences that serve them [1][14] | not said in the pages opened |
| Consistency inspection | whether the interface does things as other designs do [1] | "designers representing multiple projects" [14] | not said in the pages opened |
| Standards inspection | compliance with an interface standard [1] | the standard and an expert on it [1][14] | not said in the pages opened |
| Formal usability inspection | individual and group inspection in a six-step procedure with defined roles [1][14] | the procedure and its roles [1] | not said in the pages opened |
| Expert review | compliance with heuristics and, beyond them, other guidelines, principles of neighbouring fields, the reviewer's experience [11] | a prototype of sufficient detail or a set of specifications; a reviewer who did not make the design [11] | yes: "a set of specifications or other more abstract versions of a user interface" [11] |
| Design critique | whether a design meets its objectives [10] | the work in whatever state, agreed objectives, a scope, a presenter, critics, a facilitator [10] | not said; the page prescribes no kind of artefact [10] |

The expert review is not sharply apart from heuristic evaluation:
"Expert reviews usually expand on heuristic evaluations by assessing
the design not only for compliance with heuristics", and the line
between the two is called "blurry in many organizations" (both under
the headings "Expert Reviews" and "What Is a Design Review?" of [11]).
Neither [11] nor [1] nor [14] names a checklist or a guideline review;
the nearest things in the pages opened are the list of heuristics and
the standards inspection. The design critique is not among the
inspection methods of [1] and [14]; it comes from design practice and
is defined as "analyzing a design, and giving feedback on whether it
meets its objectives" (heading "What Is a Critique?" of [10]).

**F2. Heuristic evaluation is a judgement by several people working
alone, and its output is a list of candidate problems, not of
confirmed ones.** [consensus; originator's summaries, textbook,
practitioner guide; summarised fetches; the figures of [16] added in
the second round] It is "the most informal method" and has specialists
judge whether each dialogue element follows the principles [1]. The
textbook's procedure: several evaluators, "analyzing either a
prototype or a paper description of the design" (Section 4.3 of [3]),
and "Each evaluator should do the analysis alone" (same section). The
reason is stated there: "no single evaluator will find every problem
with an interface". The figures the textbook reports from the method's
authors: three to five evaluators with interface expertise catch "75
percent of the total heuristically identifiable problems", while of
novices "it might take as many as 15 of them to find 75 percent of the
problems" (Section 4.3 of [3]). The originator's own figures from six
case studies: one evaluator finds a given major problem with a
probability of 42% and a minor one with 32%, and the lists are
"dominated by minor problems", 59 major and 152 minor across six
interfaces (the opening text of [16]). The 2023 guide repeats the
count, "Ideally, three to five people should independently evaluate
the same interface" (heading "Choose and Train Your Team" of [2]), and
limits the claim: a violation of a heuristic "does not necessarily
mean it's a problem", and "heuristic evaluations cannot replace user
research" [2]. Against tests with users the two are complements:
"each finds usability problems overlooked by the other method"
(heading "Alternating Heuristic Evaluation and User Testing" of [16]).
Developers may serve as evaluators, with better results from usability
specialists [1][14].

**F3. The cognitive walkthrough judges one thing, whether a person
using the interface for the first time gets through a task, and it
cannot start without a written sequence of actions.** [consensus; a
textbook and a conference tutorial, both by authors of the method;
summarised fetches; [15] added in the second round, and it turns the
first round's inference into a sourced statement] It is "a formalized
way of imagining people's thoughts and actions when they use an
interface for the first time" (Section 4.1 of [3]), "a technique for
evaluating the design of a user interface" with "special attention to
how well the interface supports 'exploratory learning,' i.e.,
first-time use without formal training" [15]. Four things are needed
(Section 4.1.2 of [3]): "a description or a prototype of the
interface", which "doesn't have to be complete, but it should be
fairly detailed"; "a task description"; "a complete, written list of
the actions needed to complete the task with the interface"; and "an
idea of who the users will be and what kind of experience they'll
bring to the job". The tutorial lists the same three companions: "a
general description of who the users will be and what relevant
knowledge they possess", "a specific description of one or more
representative tasks" and "a list of the correct actions required to
complete each of these tasks" [15]. At each action four questions are
asked (Section 4.1.3 of [3]): "Will users be trying to produce
whatever effect the action has?", "Will users see the control (button,
menu, switch, etc.) for the action?", "Once users find the control,
will they recognize that it produces the effect they want?", "After
the action is taken, will users understand the feedback they get, so
they can go on to the next action with confidence?". The tutorial
names the same four as criteria: "the user's goal", the accessibility
of the correct control, "the quality of the match between the
control's label and the goal" and "the feedback provided after the
control is acted on" [15]. So a description can be walked only if it
gives, per action, the control the user sees, the words on it and the
feedback that follows. The method "can be performed by the system's
designers in the early stages of design, before empirical user testing
is possible" and is "typically performed by the interface designer and
a group of his or her peers" [15]; a designer of a small piece may
walk it alone, "in your head" [3]. Its limits are stated: "the
walkthrough DOES NOT TEST REAL USERS ON THE SYSTEM" [3], and it is
"specifically limited to considering whether the user will select each
of the correct actions along the solution path" [15].

**F4. By the methods' own literature a detailed description is a
sufficient input; against a running system one loss is measured, that
what is missing is harder to find on paper; a prose description is
compared with a picture in none of the pages opened.** [consensus for
the first part, five pages of the methods' side; a controlled
comparison reported by its author for the second; the third is a gap;
summarised fetches; changed in the second round by [16], [14] and
[15]] The 1994 summary says of inspection methods that they "lend
themselves to the inspection of user interface specifications" not yet
implemented, so that inspection "can be performed early in the
usability engineering lifecycle" (the summary paragraph at the head of
[1]; the same words in [14]). The textbook names "a paper description
of the design" for heuristic analysis and "a prototype or a detailed
design description of the interface" for the walkthrough (Sections 4.3
and 4.1 of [3]); the tutorial says the walkthrough "does not require a
fully functioning prototype, or the involvement of users" [15]. The
expert review may examine "a set of specifications or other more
abstract versions of a user interface" ([11]; the fetch returned the
sentence without its heading). The 2023 guide speaks only of
"prototypes" and of use "early in the design process" (heading "When
to Conduct a Heuristic Evaluation" of [2]). What was measured: in
heuristic evaluation, problems of interface elements that are missing
and ought to be there were "much harder to find than other problems in
paper prototypes" than in running systems, so that "one should look
harder for missing dialogue elements when evaluating paper mock-ups";
the explanation offered is that an evaluator on a running system gets
stuck where an element is missing, while "evaluators of a paper
'implementation' just turn to the next page" (the opening text of
[16], which cites a paper of 1990 by the same author for it). That
compares screens on paper with a running system, not prose with a
picture. The one measured hint on prose-like input comes from the
models' side: a model reading a textual form of a mockup "cannot
capture violations that would require processing the rendered image of
a UI", overlap and alignment among them (Section 5.4.7 of [5]).

**F5. Evaluators disagree, in every method, whatever their
experience; so do two models.** [consensus; a review of eleven studies
read as its abstract only, a textbook, two controlled studies;
summarised fetches; [17] added in the second round] The review covers
the cognitive walkthrough, heuristic evaluation and thinking-aloud
studies and finds that "multiple evaluators evaluating the same
interface with the same UEM detect markedly different sets of
problems"; the agreement between any two evaluators ranges from 5% to
65%, no method is consistently better, and the effect holds for
novices and for experienced evaluators [4]. The causes it names are
vague goal analyses, vague evaluation procedures and vague problem
criteria; it holds that the effect cannot be removed and that several
evaluators are the simplest remedy [4]. Two studies of 2025 show the
same in fresh data: one expert alone found about 18% and 17% of a
master set of issues in two apps, five experts together 57% and 63%
[7]; four experienced inspectors reported between 17 and 37
discrepancies each on one prototype and 72 distinct defects together
[17]. In [17] the two models disagreed with each other in the same
way: of 55 and 52 distinct defects they shared 18, and their findings
taken together reached a recall of 0.701 where each alone had 0.433
and 0.409.

**F6. Measured as heuristic evaluators, language models find real
problems that largely differ from those humans find, and report many
that are not problems; a model finds as much as one human alone or
more, and whether it finds more than a group of experts is
contested.** [contested; five controlled studies, each on few
interfaces, one of them read as its abstract, and one news item on a
sixth; summarised fetches; figures of 2024 and 2025 models, the
youngest source dated 6 Jul 2026; rows [17], [18] and [20] and the
reading of the conflict added in the second round]

| Study | Model | What the model was given | Measured against | Result |
|---|---|---|---|---|
| [5], 19 Mar 2024 | GPT-4, text only | a JSON form of a UI mockup with the text of the guidelines, one static screen at a time | three designers rating its suggestions on 51 UIs; twelve experts' own evaluations of 12 UIs | 52% of suggestions rated accurate, 19% partially, 29% not; precision 0.603 and recall 0.380, the average human 0.829 and 0.336; of 100 distinct violations 62 found by humans only, 29 by both, 9 by the model only |
| [18], abstract only, first version 1 Nov 2024 | a vision-language model in a tool that can also inspect source code | views of two open-source iOS apps | two usability experts; a usability test and an expert review of the same apps | precision 0.61 to 0.66, recall 0.35 to 0.38; "failing to capture the majority of issues" |
| [6], 19 Jun 2025 | GPT-4o | 20 screenshots of one web system, one prompt per screenshot, Nielsen's ten heuristics | 66 issues found earlier by three human experts | 111 issues reported: 43 duplicates (38.7%), 27 false positives (24.3%), 41 kept; 14 of the experts' 66 found (21.2%), 27 new ones |
| [7], 3 Jul 2025 | GPT-4; then Gemini-1.5-pro and Claude 3.5 Sonnet | the screenshots of a task in order with one line of user scenario; two mobile apps | a master set built from five experts per app, GPT-4's own findings and five trained assistants | GPT-4 73% and 77% of the master set, the five experts together 57% and 63%; Gemini 59% and 59%, Claude 57% and 58% |
| [17], 19 Oct 2025 | GPT-4o and Gemini 2.5 Flash | 16 screenshots of a student-built prototype, one at a time in order of use, Nielsen's ten heuristics | four experienced inspectors, all findings consolidated by the authors | false positives 18% and 17.11% of what the models reported, the inspectors' 9 of 108; distinct defects 52 and 55, the inspectors together 72; the models matched 33.33% and 27.78% of the inspectors' defects; precision 0.820 and 0.829 against 0.917, recall 0.409 and 0.433 against 0.567 |
| [20], 6 Jul 2026, a news item; the paper not read | GPT-4o with a short instruction | the code of 15 screens of open-source Flutter apps | 15 professional Flutter developers | "roughly twice as many usability issues per screen" as human reviewers; the developers agreed a flagged issue was real "about 82 percent of the time" |

The authors' conclusions run one way in four: "GPT-4 is less
comprehensive than a group of 6 human experts" (Section 5.2 of [5]);
the model "should not be treated as a replacement for human experts
but rather as a complement" [6]; "AI, in its current stage, cannot
replace human inspectors" (abstract of [17]); the tool "cannot fully
replace traditional usability evaluation methods but serves as a
valuable supplement" (abstract of [18]). They are contradicted by [7],
which concludes that "synthetic heuristic evaluations outperform the
average human evaluator" and may do better than five, and by the
report of [20]. The agent's own reading of the six, not any one
source's: three things hold in all that measured them. The overlap
between a model's findings and the humans' is small (29 of 100 in [5],
14 of 66 in [6], a third or less in [17]), so the two together find
more than either: inspectors with one model reached a recall of 0.843
in [17]. The model's precision is below the human's (0.603 against
0.829 in [5], 0.82 against 0.917 in [17]). And a model finds as much
as one human alone or more (recall 0.380 against 0.336 in [5]; an
"effectiveness" near 60% against 34.38% for the average inspector in
[17]; 73% against about 18% in [7]). What differs is the comparison
with a group, where [7] stands alone; its master set included the
model's own accepted findings, while [5], [6] and [17] measured
against what humans had found or what the authors consolidated. The
share judged wrong runs from about a sixth to two fifths: 17% and 18%
[17], 18% not agreed by developers [20], 24.3% of the 111 reported in
[6], which by the agent's arithmetic is about 40% of the 68 left once
duplicates are removed, 29% not accurate in [5], and a precision of
0.61 to 0.66 in [18]. In [7] the model produced 43 and 52 issues of
severity 0, that is, not usability problems, in the two apps; the
fetch returned no total against which they stand.

**F7. What models miss and what they over-report has a recognisable
kind.** [emerging; four controlled studies agreeing in kind, one news
item; summarised fetches; [17] and [20] added in the second round]
Missed: what spans screens (GPT-4 found 3 of 7 and 3 of 6 cross-screen
violations, experts 6 of 7 and 5 of 6 [7]), "global" violations of a
design [5], and consistency with standards (46% against 54% and 40%
against 60% for experts [7]). Over-reported: guidelines applied "too
literally", such as demanding labels on universally known icons
(Section 5.4.5 of [5]); conventions of an app read as faults (42% and
38% of the severity-0 issues of [7]); elements misread, such as the
status bar of the phone taken for the app (42% and 27% of them [7]);
the same remark repeated per screen or per element (duplicates in [5],
[6], [7], and 30 of ChatGPT's 100 reports in [17]); and risks the
developers held trivial, where the tool "sometimes overreacted" [20].
Where models did better than experts in [7] was small layout and
visual hierarchy, "aesthetic and minimalist design": 86% and 74%
against 38% and 42%.

**F8. A model's repeated runs agree with each other moderately, and
agreement is not correctness.** [emerging; two controlled studies with
different measures; summarised fetches] On the source code of 30
websites, three sessions of GPT-4o agreed on whether an issue exists
with a Cohen's kappa of about 0.50 (exact agreement 82% to 85%) and on
severity with a weighted kappa of 0.60 to 0.67 (exact agreement about
56%); the agreement was lowest for "Consistency and Standards" and
"Help and Documentation", about 0.08 each; Krippendorff's alpha was
near zero, which the authors put down to the measure under class
imbalance [9]. The study has no human comparison and says so: "The
consistency shown does not imply correctness" [9]. On screenshots,
GPT-4 runs over three months covered about 94% of what its first run
had found [7]. [6] and [17] did not measure repetition; [17] names it
as a limit, that the models "may produce slightly different results
across executions" (Section 6).

**F9. As a walker, a model is not a first-time user: it completes
more, by shorter paths, and reports fewer points of failure, unless it
is asked to predict them with the history of the walk.** [single
source; a controlled study accepted to a 2026 conference; summarised
fetch, read twice] Given a task description, a start screen and the
screenshots of two mobile apps with the navigation between them, GPT-4
completed 100% of tasks and Gemini-2.5-pro 97.20%, ten human
participants 88.20%; the models took about 7.5 steps where the humans
took 10.37 [8]. A potential failure point was coded wherever a
rationale showed "confusion or uncertainty" (Section 4.2 of [8]): "all
human users identified 10 potential failure points, whereas all GPT
and Gemini runs aggregated only found 3" (Section 4.4 of [8]). In a
second study, prompted further and given the whole history of the
walk, every run of both models predicted the failure points humans had
identified, with a pairwise Cohen's kappa of 0.64 and 0.63 between
runs; shown one screen and task at a time, only one run of each model
did [8]. The authors tested mobile interfaces only and set up the
screens and transitions by hand [8].

**F10. Models have been run as evaluators on four kinds of input,
none of them a prose description.** [emerging; nine studies, one as
its abstract and one through a news item; summarised fetches; the
youngest source dated 6 Jul 2026; [17], [18], [20] and the result of
a query worded for exactly this added in the second round] A JSON form
of a mockup [5]; source code, of a site in HTML, CSS and JavaScript
[9] and of single screens of Flutter apps [20]; screenshots
[6][7][8][17], in [18] with access to source code; screen recordings
with a description of the app and of a persona and task [13]. Two of
the four are text. In [5] text was a choice of its time: "Since LLMs
can only accept text as input, the plugin takes in a JSON
representation of the UI" (Section 3.3), and the multimodal models
tried then did "considerably worse" on the screenshot; that is a
statement of March 2024 and most later studies feed pictures. A query
of the second round worded for a model judging an interface from a
textual description or a specification returned no such study. The
context a model is given beside the interface grows through the
studies: guidelines only [5], a role and a rubric [6][17], a line of
user scenario [7], the task [8], the app's description with persona
and task [13].

**F11. A model's feedback on one design gets worse over rounds of the
same design, and examples of human critique make it better.** [single
source each; one controlled study, one abstract; summarised fetches]
In the iterative use of [5], ratings fell from 52% accurate and 20%
not accurate on the first version to 39% and 35% in later rounds, a
"general trend of decreasing performance per round" (Section 5.3 of
[5]); after a suggestion was dismissed the model sometimes raised the
same issue under another guideline (Section 5.4.9 of [5]). A dataset
of 3,059 critiques of 983 mobile UIs by seven designers, used for
few-shot and visual prompting, is reported to raise the quality of a
model's UI feedback by 55%; its abstract holds that model-based
evaluation does not yet match human evaluators ([12], abstract only).

**F12. People who receive a model's findings rate them plausible, and
that rating has not been checked against a ground truth.** [single
source; a user study of subjective ratings; summarised fetch] 95
people of software engineering background rated the three top-ranked
issues of a scenario, 285 in all, produced by gemini-2.0-flash-001
from screen recordings under Nielsen's ten heuristics: plausibility
4.04 of 5, 73.7% judged complete, and of 33.0% the rater said he
would not have noticed the issue alone [13]. No expert compared the
findings, no share of wrong findings is given, and the authors name a
possible novelty effect [13].

**F13. Inspection by heuristics over-reports in human hands too; how
much depends on the yardstick.** [single source for the figure against
tests with users, a vendor claim: a usability firm's newsletter
summing three published studies that were not opened; controlled
studies for the figures against experts; summarised fetches; added in
the second round] Against tests with users, the newsletter's sum over
three studies of 1998 and 1999: "about 43% of the 'problems' that were
identified by the heuristic evaluators did not turn out to be problems
at all", about a third were hits and about 21% of the problems users
had were missed; in its second reckoning, "46% were hits and 54% were
false alarms" ([19], in its body; the fetch gave no heading and noted
that the two reckonings are not reconciled on the page). Against the
judgement of experts the human figure is far lower: 9 false positives
in 108 reports of four inspectors, by the agent's arithmetic 8.3%
[17], and a precision of 0.829 for the average expert of [5]. The
originator's own page says only that a violation "does not necessarily
mean it's a problem" [2] and gives no rate [16]. A reader who holds to
the exclusion of vendors' pages should drop the figures of [19] and
keep the rest.

**F14. A long checklist is reported to narrow a model reviewer.**
[single source; a university's news item on its researchers' paper,
the paper not read; summarised fetch; added in the second round] In
the study behind [20], GPT-4o read the code of a screen under a short
instruction in plain English; given an elaborate checklist instead it
became "better at routine box-checking" but "worse at catching the
deeper, more creative problems" [20]. The item offers a reason and
marks it as likely, not shown: a model that already knows the practice
is boxed in by over-instruction [20]. It is the only thing found, in
either round, on a review by checklist performed by a model.

## Unexpected

The yardstick is as unreliable as what it measures. In [5] three
designers rated whether each suggestion of the model was accurate and
agreed with a Fleiss' kappa of 0.112, and 0.100 on helpfulness. A
reported share of "false positives" is therefore itself one group's
judgement; [6] says its disagreements were settled by discussion,
which it names as a source of subjectivity. Lead: a figure for how
often a reviewer agent is wrong may not be obtainable more exactly
than within the disagreement of the people judging it.

The card asks whether a method runs on text or only on a picture; the
sources put the weight elsewhere. [3], [15], [10] and [1] make the
binding requirement not the medium but what stands beside the
description: the users, a task and its written actions for the
walkthrough, agreed objectives for the critique ("any feedback is
subjective and baseless" without them [10]), the standard for a
standards inspection, designers of other projects for a consistency
inspection. In plain words: the card assumes a description is judged
by itself; [3], [15] and [10] say it is judged against something, and
the something has to be written down too. The question is still
answered as put, in F1 and F4.

The card expects that models over-report; [19] says heuristic
evaluation by people does too, by about half against tests with users
(second round). In plain words: over-reporting looks like a property
of judging by heuristics without users, which a model shares and
worsens, not a defect peculiar to models. It is one vendor's sum of
three studies not opened here, and a lead until one of them is read.

Consistency is the weakest point of a model twice over: lowest
coverage against experts on "consistency and standards" [7] and lowest
agreement between a model's own runs [9]; and in the method's original
form it is not a reading of one design at all but a meeting of
designers from several projects [1][14]. Lead, the agent's inference:
of all the judgements, consistency may be the one least suited to a
reviewer's reading and best served by how the description is built.

What is absent is what an inspection on paper misses [16], and a model
that walks a path does not stumble where a person would [8]. Lead, the
agent's inference from the two together (second round): a description
in text, read by a model, is exposed twice to the same blind spot, the
thing that ought to be there and is not.

A human evaluator tires and a model does not: in [7] the experts'
performance fell across the tasks (reported as a significant decline)
while the model's stayed level. And a human evaluator is not a clean
reference either: the average expert of [5] had a precision of 0.829
against the pooled judgement, not 1.

## Not found

- The original papers of the methods were not read in either round.
  The reference lists of [14] and [15] name them: the 1990 paper of
  heuristic evaluation by Nielsen and Molich, the 1994 practitioner's
  guide to the cognitive walkthrough by Wharton, Rieman, Lewis and
  Polson, the 1994 chapter on inspections and design reviews by Wixon,
  Jones, Tse and Casaday. The query for the guide, refused in the
  first round, ran in the second and returned a course's copy of the
  chapter as a PDF; the fetch reads no PDF, as two attempts of the
  first round showed, so it was not opened. The methods stand on [1],
  [2], [3], [14], [15] and [16], all by the methods' authors but [2].
- An expert review "by checklist" as a method with a source of its
  own. Searched in the second round: the result list held a standards
  body's slide deck as a PDF, university service pages and vendors'
  glossaries; none was opened, the first unreadable by the fetch, the
  rest below the bar. [14] was opened to look for a guideline review
  in the family's list and names none, as [1] and [11] name none.
- Research on the design critique, and the practice's own book.
  Searched twice in the second round: the result lists held studies of
  crowd critique and of the studio critique in design education, as
  PDFs, not opened, and the book of the practice, whose chapter page
  at its publisher refused the fetch with HTTP 403. The route still
  rests on one practitioner article [10].
- A comparison of an inspection run on a prose description with one
  run on a picture or a prototype, for humans or for models: none.
  [16] compares screens on paper with a running system only; the 1990
  paper it cites for that was not opened.
- A study of a language model judging a prose description of an
  interface, as distinct from a JSON form of a mockup, source code,
  screenshots or recordings: none, after a query of the second round
  worded for it.
- A model in the place of a consistency inspection across a whole
  application, or of a critique against stated objectives: not found;
  the cross-screen figures of [7] are the nearest.
- The rate of false alarms of human heuristic evaluation against tests
  with users from a primary source: only the vendor's sum [19]; the
  three studies it names were not opened.
- Measurements of models released in 2026: none; the news item of July
  2026 [20] reports GPT-4o, the study of April 2026 [13]
  gemini-2.0-flash-001, the 2026 conference paper [8] GPT-4 and
  Gemini-2.5-pro.
- The full texts behind three sources: the article of [4], read as its
  abstract; the papers of [12] and [18], read as their abstract pages;
  and the paper behind [20], which the item links at a publisher's
  library and which was not opened.

## Options

Left out: the card asks for a fact, not a choice. What the findings
suggest for the project stands under Relevance to this project.

## Relevance to this project

A description of an interface in text can be judged before it is
built, by the same methods that judge a prototype, on three
conditions the sources give.

First, the description has to carry or cite what the methods take as
input: who the users are, the tasks, for each task the written
sequence of actions, and for each action the control the user sees,
its wording and the feedback that follows (F3, now sourced by [15]);
the objectives the design is to meet, without which a critique is
opinion [10]; the conventions or standard it claims to follow [1]. The
agent's inference: these are requirements on the shape of the
description, and a description that names only screens and their
elements can be read for heuristics and nothing else. Since what is
missing is the hardest thing to find on paper [16], a reviewer of a
description should be asked outright what ought to be there and is
not; the agent's inference is that a walk along the written actions of
a task is the method that brings an absence to the surface, because
the walker needs the missing thing at a known step.

Second, a reviewer agent's report is a list of candidates, as a human
heuristic evaluation is (F2, F13), with a lower precision: on the
models of 2024 and 2025, between about a sixth and two fifths of
findings were judged wrong and duplicates were frequent (F6, F7). It
rests on [5], [6], [7], [17] and [18]. It follows, as the agent's
inference, that several independent reviewers with their findings
merged serve better than one, and reviewers of different kinds better
than of one kind, a model beside a human or two different models (F5,
F6: the unions of [17]); that a human judges every finding; that a
re-review of a changed description may be worse than the first (F11);
and that agreement between a model's runs is no evidence that it is
right [9]. A model that walks the paths is not a first-time user and
must be asked where people would fail, with the whole walk before it
(F9). A reviewer agent's instruction is better kept to a short list of
principles than grown into a long checklist, on the single report of
F14; that is a lead, not a rule.

Third, some judgements do not belong to the text. What only shows when
rendered, overlap, alignment, visual hierarchy, is out of reach of a
reading of text [5], and consistency across screens is where models
are weakest (F7, F8). The agent's inference: the first belongs to
whatever shows the proposal to the human, the second is better secured
by construction, one definition of a thing referred to wherever it
stands, than by review. That speaks for the idea the research is to
test, small definitions of elements cited by pages, on this one count
only; whether it holds otherwise is other cards' question.

This is chosen against three alternatives: one reviewer, human or
model, whose single report is taken as the judgement (against F5);
judging only once a picture or a prototype exists (against F4, since
function, wording, flow and feedback can be judged earlier); and a
model's review standing in place of the human's (against [5], [6],
[9], [17] and [18]). The contrary results of [7] and [20] are the
reason not to dismiss model reviewers: against one human they find
more, and what they find is mostly what the human did not.

Consult when: the fields of the interface description are decided,
and it is asked what a reviewer needs to find there; reviewers for the
description are designed, and their number, kind, independence and the
handling of their findings are set; someone proposes that an agent's
review replace the human's, or quotes a rate of false positives; it is
decided what is judged on the text and what waits for a picture.

## Sources

Sources 1 to 13 were opened in the first round, 14 to 20 in the
second.

1. "Summary of Usability Inspection Methods", Jakob Nielsen, Nielsen
   Norman Group, 1 Nov 1994 (byline).
   https://www.nngroup.com/articles/summary-of-usability-inspection-methods/
   Kind: primary for heuristic evaluation, the author's own method;
   secondary for the others, which it summarises. Read: summarised
   fetch of the whole page. Original. The publisher sells UX training
   and consulting; used for the definitions of the methods only.
2. "How to Conduct a Heuristic Evaluation", Kate Moran and Kelley
   Gordon, Nielsen Norman Group, 25 Jun 2023 (byline).
   https://www.nngroup.com/articles/how-to-conduct-a-heuristic-evaluation/
   Kind: secondary, a practitioner guide. Read: summarised fetch of
   the whole page. Original. Publisher as [1].
3. "Task-Centered User Interface Design: A Practical Introduction",
   Chapter 4, "Evaluating the Design Without Users", Clayton Lewis and
   John Rieman, 1993, 1994 (copyright line of the page).
   https://hcibib.org/tcuid/chap-4.html
   Kind: primary for the cognitive walkthrough, both authors being
   among the authors of the method's papers as [15] lists them;
   secondary for heuristic analysis. Read: summarised fetch of the
   whole page, fetched twice, the second time for exact wording. A
   hosted copy of the authors' book; whether the host is its first
   publisher was not checked.
4. "The evaluator effect: A chilling fact about usability evaluation
   methods", Morten Hertzum and Niels E. Jacobsen, International
   Journal of Human-Computer Interaction 15(1), 183-204, 2003 (the
   bibliographic record).
   https://forskning.ruc.dk/da/publications/the-evaluator-effect-a-chilling-fact-about-usability-evaluation-m/
   Kind: primary, abstract only. Read: summarised fetch of the record;
   the abstract came back as a paraphrase with short quotes, the
   article itself was not read. A university research portal's record
   of an article first published by the journal.
5. "Generating Automatic Feedback on UI Mockups with Large Language
   Models", Peitong Duan, Jeremy Warner, Yang Li, Bjoern Hartmann,
   arXiv:2403.13139v1, 19 Mar 2024 (the arXiv stamp on the page; no
   venue stated on the page).
   https://arxiv.org/html/2403.13139v1
   Kind: primary. Read: summarised fetch of characters 0 to 100,000 of
   139,183, through Section 5 and part of Section 6; the authors' own
   section on limitations was not read. Original (preprint).
6. "Can GPT-4o Evaluate Usability Like Human Experts? A Comparative
   Study on Issue Identification in Heuristic Evaluation", Guilherme
   Guerino, Luiz Rodrigues, Bruna Capeleti, Rafael Ferreira Mello,
   André Freire, Luciana Zaina, arXiv:2506.16345v1, 19 Jun 2025 (the
   arXiv stamp; no venue stated on the page).
   https://arxiv.org/html/2506.16345v1
   Kind: primary. Read: summarised fetch of the whole page. Original
   (preprint).
7. "Synthetic Heuristic Evaluation: A Comparison between AI- and
   Human-Powered Usability Evaluation", Ruican Zhong, David W.
   McDonald, Gary Hsieh, arXiv:2507.02306v1, 3 Jul 2025 (the arXiv
   stamp; no venue confirmed on the page).
   https://arxiv.org/html/2507.02306v1
   Kind: primary. Read: summarised fetch of characters 0 to 100,000 of
   112,614, the whole body; the cut fell in the references. Original
   (preprint).
8. "Synthetic Cognitive Walkthrough: Aligning Large Language Model's
   Performance with Human Cognitive Walkthrough", Ruican Zhong, David
   W. McDonald, Gary Hsieh, arXiv:2512.03568v1, 3 Dec 2025 (the arXiv
   stamp); the page names the CHI Conference on Human Factors in
   Computing Systems, CHI '26, 13 to 17 April 2026.
   https://arxiv.org/html/2512.03568v1
   Kind: primary. Read: summarised fetch of the whole page, fetched
   twice, the second time for the figures on failure points. Original
   (preprint).
9. "Catching UX Flaws in Code: Leveraging LLMs to Identify Usability
   Flaws at the Development Stage", Nolan Platt, Ethan Luchs, Sehrish
   Nizamani, arXiv:2512.04262v1, 3 Dec 2025 (the arXiv stamp; no venue
   stated on the page).
   https://arxiv.org/html/2512.04262v1
   Kind: primary. Read: summarised fetch of the whole page. Original
   (preprint).
10. "Design Critiques: Encourage a Positive Culture to Improve
    Products", Sarah Gibbons, Nielsen Norman Group, 23 Oct 2016
    (byline).
    https://www.nngroup.com/articles/design-critiques/
    Kind: secondary, a practitioner article. Read: summarised fetch of
    the whole page. Original. Publisher as [1]; opened by an address
    the agent knew, not from a result list.
11. "UX Expert Reviews", Aurora Harley, Nielsen Norman Group, 25 Feb
    2018 (byline).
    https://www.nngroup.com/articles/ux-expert-reviews/
    Kind: secondary, a practitioner article. Read: summarised fetch of
    the whole page. Original. Publisher as [1]; opened in the first
    round by an address the agent knew, and present in a result list
    of the second.
12. "UICrit: Enhancing Automated Design Evaluation with a UICritique
    Dataset" (the title as the fetch returned it; its spacing may
    differ on the page), Peitong Duan, Chin-yi Chen, Gang Li, Bjoern
    Hartmann, Yang Li, arXiv:2407.08850, v1 of 11 Jul 2024, v3 of 13
    Aug 2024 (the arXiv record); comment field: accepted to ACM UIST
    2024.
    https://arxiv.org/abs/2407.08850
    Kind: primary, abstract only. Read: summarised fetch of the
    abstract page; the abstract came back as a paraphrase with one
    short quote, the paper itself was not read. Original (preprint
    record). Opened by an identifier the agent recalled and confirmed
    on the page.
13. "Recommending Usability Improvements with Multimodal Large
    Language Models", Sebastian Lubos, Alexander Felfernig, Damian
    Garber, Viet-Man Le, Manuel Henrich, arXiv:2604.25420v1, 28 Apr
    2026 (the arXiv stamp); the page names PACMSE, Volume 3, FSE.
    https://arxiv.org/html/2604.25420v1
    Kind: primary. Read: summarised fetch of the whole page; the
    prompts are figures and were not read. Original (preprint).
14. "Usability Inspection Methods", Jakob Nielsen, SunSoft, a tutorial
    summary in the proceedings of CHI '95 (dated by the proceedings'
    name on the page; no other date).
    https://chi1995.chistatic.hosting.acm.org/proceedings/tutors/jn_bdy.htm
    Kind: primary for heuristic evaluation, secondary for the other
    methods; its reference list names the originals. Read: summarised
    fetch of the whole page. Original, on the conference's own pages.
    Second round.
15. "Usability Evaluation with the Cognitive Walkthrough", John
    Rieman, Marita Franzke, David Redmiles, a tutorial summary in the
    proceedings of CHI '95 (dated by the proceedings' name on the
    page).
    https://chi1995.chistatic.hosting.acm.org/proceedings/tutors/jr_bdy.htm
    Kind: primary, by authors of the method's papers, which its
    reference list names. Read: summarised fetch of the whole page.
    Original, on the conference's own pages. Second round.
16. "Characteristics of Usability Problems Found by Heuristic
    Evaluation", Jakob Nielsen, Nielsen Norman Group, 1 Jan 1995
    (byline).
    https://www.nngroup.com/articles/usability-problems-found-by-heuristic-evaluation/
    Kind: primary, the author reporting his own studies of 1990 and
    1992, which were not opened. Read: summarised fetch of the whole
    page. Original. Publisher as [1]. Second round.
17. "Will AI also replace inspectors? Investigating the potential of
    generative AIs in usability inspection", Luis F. G. Campos,
    Leonardo C. Marques, Walter T. Nakamura, arXiv:2510.17056v1, 19
    Oct 2025 (the arXiv stamp); the page names the Brazilian Symposium
    on Software Quality, 4 to 7 Nov 2025.
    https://arxiv.org/html/2510.17056v1
    Kind: primary. Read: summarised fetch of the whole page; the fetch
    noted two small inconsistencies inside the paper, a count of 54
    against 55 and an introduction at odds with its table on
    precision. Original (preprint). Second round.
18. "Does GenAI Make Usability Testing Obsolete?", Ali Ebrahimi
    Pourasad and Walid Maalej, arXiv:2411.00634, v1 of 1 Nov 2024, v3
    of 13 Jan 2026 (the arXiv record); comment field: accepted at the
    47th IEEE/ACM International Conference on Software Engineering,
    ICSE 2025.
    https://arxiv.org/abs/2411.00634
    Kind: primary, abstract only. Read: summarised fetch of the
    abstract page; the paper itself was not read. Original (preprint
    record). Second round.
19. "Heuristic evaluations vs. usability testing", newsletter of Human
    Factors International, January 2001 (date on the page); no author
    named, the text speaking in the first person of an article of 1992
    by Bailey, Allan and Raiello.
    https://humanfactors.com/newsletters/heuristic_evaluations_vs_usability_testing_the_relative_effectiveness.asp
    Kind: secondary, and a vendor's page: the publisher sells
    usability services. A write-up of three studies by others (Catani
    and Biers 1998; Rooden, Green and Kanis 1999; Stanton and
    Stevenage 1998), cited as such because the studies themselves were
    not opened. Read: summarised fetch of the whole page. Second
    round.
20. "Can AI Spot Problems with Apps' User Interface Design Better than
    Users?", Elsa Hahne, Louisiana State University, 6 Jul 2026
    (byline).
    https://lsu.edu/blog/2026/07/ai-beats-users-on-user-design.php
    Kind: secondary, a university's news item on a paper of its own
    researchers; the item links the paper at a publisher's library,
    which was not opened and whose identifier is therefore not given
    here. Read: summarised fetch of the whole page. Second round.

## Opened and not used

- https://www.colorado.edu/ics/sites/default/files/attached-files/93-07.pdf
  First round. An address the agent tried for the technical-report
  form of the 1994 practitioner's guide to the cognitive walkthrough.
  A scanned PDF was delivered that the fetch could not read; what it
  holds is unconfirmed and it is cited for nothing. Superseded by [3]
  and [15].
- https://mortenhertzum.dk/publ/IJHCI2003.pdf
  First round. An address the agent tried for an author's copy of the
  article of [4]. A PDF was delivered that the fetch could not read;
  cited for nothing. Superseded by [4], the abstract.
- Second round, one fetch that opened nothing: the page of the second
  chapter of the book "Discussing Design" by Adam Connor and Aaron
  Irizarry at its publisher's library, taken from a result list,
  refused with HTTP 403. Its address is not given because it did not
  open; nothing is cited from it.

## Search record

Why there were two rounds. In the first round the search tool refused
every query after the fifth: the allowance of web searches shared by
the session was spent. The note of that round said what could not be
searched. When search worked again the coordinator of the research
ordered a second round: the queries refused or not run, a differently
worded query for the stop rule, and at most eight further pages on
what they returned. This note is the first round's with the second
brought in.

Queries of the first round, in order:

1. usability inspection methods summary heuristic evaluation cognitive
   walkthrough consistency inspection
2. LLM heuristic evaluation user interface study 2025
3. heuristic evaluation unreliable evaluator effect (the card's
   disconfirming query)
4. LLM usability evaluation false positives (the card's disconfirming
   query)
5. cognitive walkthrough large language model automated study
6. the practitioner's guide to the cognitive walkthrough as a
   technical report: refused, not performed

Queries of the second round, in order, all performed:

7. cognitive walkthrough practitioner's guide Wharton Rieman Lewis
   Polson technical report pdf (the query refused in the first round)
8. design critique research study feedback quality designers
9. usability expert review checklist guideline review method
10. LLM evaluate usability from textual description of user interface
    specification requirements
11. heuristic evaluation false alarms validity compared with usability
    testing (the first disconfirming query in other words)
12. generative AI automated UX review accuracy compared to experts
    hallucinated usability problems study 2026 (the second
    disconfirming query in other words)
13. design critique framework objectives elements Connor Irizarry
    Discussing Design
14. paper versus prototype heuristic evaluation specification
    inspection comparison problems found
15. automated usability inspection large language model precision
    recall versus human inspectors (differently worded, for the stop
    rule)
16. agreement between evaluators usability inspection reliability
    review of studies (differently worded, for the stop rule)

Pages opened in the first round, fifteen, in order: [1]; [2]; the
unreadable PDF tried for the walkthrough's guide; the unreadable PDF
tried for [4]'s article; [3]; [4]; [5]; [6]; [7]; [8]; [9]; [10];
[11]; [12]; [13]. Two of them, [3] and [8], were fetched a second time
for exact wording, which makes seventeen fetches of fifteen pages.
Four addresses came from the agent's own knowledge and not from a
result list: the two PDFs, [10] and [11]; [12] from a recalled
identifier confirmed on its page.

Pages of the second round, eight fetches, seven pages opened, in
order: [16]; [15]; [14]; [17]; [18]; the book chapter that refused
with HTTP 403; [19]; [20]. [14] and [15] came from the result list of
query 1 and of query 7, [16] from queries 11 and 14, [17], [18] and
[20] from query 12, [19] from query 11, the refused chapter from
query 13. No PDF was tried: the fetch had read none in the first
round.

What the disconfirming queries found. In the first round, "heuristic
evaluation unreliable evaluator effect" led to [4]: the expectation
that evaluators disagree holds, for all three methods the review
covers and with a range, 5% to 65%, wider than a reader might expect.
"LLM usability evaluation false positives" led to [6], with [7] and
[9] in the same list: the expectation that models over-report holds in
[5], [6] and [7], with one complication, that in [7] the
over-reporting model also covered more of the pooled issues than five
experts together. In the second round, the two queries in other words
(11 and 12) confirmed both and added a correction: [17] and [18] show
a model's precision below the human's, and [19] reports that human
heuristic evaluation, set against tests with users, raised about as
many false alarms as true problems. Nothing found in either round
contradicts either expectation outright.

What the differently worded queries of the stop rule found. Query 15
returned [17], [18] and [9] and nothing else on the question: nothing
new. Query 16 returned the review of [4] again, with single studies of
low agreement between evaluators, which were not opened and point the
same way: nothing new in kind.

Why the run ended. The first round ended by the opening budget,
fifteen pages, with the searches spent after five queries. The second
round ended by the coordinator's limit of eight further fetches. Of
the card's stop rule, "nothing new from a differently worded query" is
met by queries 15 and 16. "Every route has a primary source" is met
for heuristic evaluation ([1], [14], [16]), the cognitive walkthrough
([3], [15]) and models as evaluators ([5] to [9], [13], [17]); for the
evaluator effect it rests on an abstract [4]; for the consistency
inspection on its definition by the family's editor ([1], [14]), the
chapter itself unread; and it is not met for the design critique,
whose book refused the fetch, nor for the expert review by checklist,
for which no source of a method was found. "Ten to fifteen pages
opened" was passed by order: twenty-two pages opened in the two
rounds together. The stop rule is therefore met in its first part and
not in its second.
