---
date: 2026-11-21
project: forge
topic: what measurement shows about models and interface descriptions
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-09-measurement
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 9; no known note named by the card; web sources below
---

# Measured studies of 2025 and 2026 say what each input carries to an agent that builds an interface, and none measures a description written from pictures

<!-- Shape: templates/research.md -->

## In short

Measured work of 2025 and 2026 exists for the first direction and
hardly at all for the second, and all of it is on the web. For an
agent that builds: a picture added to prose moves where things stand,
not whether they work. In the one multi-page benchmark that varies
the input [1], prose alone located the expected controls at 0.489
against 0.507 to 0.615 with a snapshot, while the behaviour score
stayed between 0.305 and 0.329 under every input; structure from a
design tool on top paid only when the agent was free in its stack.
Behaviour does not travel in pictures: from static screenshots alone
the best of six models of 2026 reached 36.8 of 100 on inferred
interaction and 15.8 on state that persists across screens [2], and
human-written text on an interaction, added to pictures of its
states, was the largest gain of any input change found [4]. Scores
fall at every step from one page to several to a whole application
[3]. A structured specification beat a direct picture prompt in one
single-screen study by the authors of the system [6]. No study
compares prose with a structured specification, and none measures
tokens or a component library as an input. For a model that
describes: no study measured a specification written from pictures of
screens for what it gets right, misses and invents; the nearest
measurement has models of early 2025 at about half of the questions
on a page's look that people answer at 94 to 97 percent, failing on
alignment, size, position and spacing [5]. How sure: single sources
for nearly every finding, most of them preprints, all read through a
summarising fetch. The disconfirming queries found no study in which
text alone beat a picture for the look of a page ([5] has the picture
ahead for all three models), so that half of the expectation held;
but for behaviour and for changing an existing interface text was the
better input ([4], [8]), and the other half, that a description from
a picture invents behaviour, has no measurement for or against. The
unexpected thing: look and behaviour are scored apart and do not go
together, the model with the best visual fidelity ranking fourth of
six on interaction [2].

## Question

The frame of the card, verbatim:

> A framework carries an idea down a chain of versioned Markdown
> documents kept in git: what is wanted and why, then business
> requirements, a solution design and user stories. A human works
> each document with an AI agent: the agent asks, proposes and
> writes, the human decides. Nothing is implemented there; the
> documents are handed on to be built. Its author wants the same for
> the user interface and the user experience of an application, and
> no such document exists yet: an AI agent reads the documents
> above, asks what it lacks and proposes a description of the
> interface in text; a human tunes the proposal and sees it; the
> description goes, with the other documents, to a build stage (a
> human developer, an AI coding agent, or both), and the cycle runs
> again when the interface changes. The author of a description is
> one person working end to end in a small project and a UX/UI
> specialist in a company. The targets are the web, the mobile web,
> native mobile and the desktop. Before anything is designed, a wide
> research asks how this is done elsewhere: which standards exist,
> what practice does, what the options are. One idea heard from
> practice is to be tested, not assumed: every element of a screen
> (a search field, say) has a small definition of its own in
> Markdown that carries its function, and a page definition names
> which elements it holds and where they stand. This card is one of
> twenty-two. The first card, already answered, found no synthesis
> across the field and a vocabulary that differs by community; the
> search words it gave are carried in the card below. In the sources
> the word "design" stands for three things (the design of the
> interface held in a design tool, the technical design between
> requirements and tasks in spec-driven kits, the visual identity of
> a design system): say which you mean. The other cards ask about
> the description of one screen, the user's paths, the structure
> above the screens, formal languages and standards, components in
> design systems, pages composed of defined blocks, behaviour of the
> whole application, descriptions written for an agent that builds,
> measured studies of models and interfaces, previews, design tools,
> the agent that proposes a description, declarative interface
> languages, the platforms, accessibility and wording, the place in
> the process, how a proposal is judged, where textual descriptions
> failed, what a description cites from other documents, its change
> after the first build, and automated testing of interfaces. Answer
> your own card and leave the others' questions to them.

The card, verbatim:

> #### Card 9: What measurement shows about models and interface descriptions
> - **Question:** What do measured studies of 2025 and 2026 show
>   about language models and interfaces in both directions: an
>   agent building an interface from a description (which input,
>   among prose, a structured specification, a wireframe, a
>   screenshot, tokens and a component library, gives the result
>   closest to what was wanted, above all across several screens and
>   their states), and a model writing a description from pictures
>   of existing screens (what it gets right, what it misses, what it
>   invents)? Single-shot benchmarks of 2023 and 2024 are read as
>   history only.
> - **Why it matters:** it is the one card that rests on measurement
>   and not on a maker's claim; it decides how much structure a
>   description needs for an agent, and whether a first description
>   can be written from pictures, as the first trial will do.
> - **What would answer it:** peer-reviewed papers, benchmarks and
>   preprints with a stated method.
> - **Where to look:** benchmarks of interface generation in agentic
>   and multi-page settings; studies of the understanding and the
>   description of screens; the proceedings of the main conferences
>   of 2025 and 2026; preprint servers. Search words from card 1:
>   "design to code", "UI to code", "image to code", "intermediate
>   representation".
> - **Disconfirming query:** "text specification outperforms
>   screenshot for UI generation", "screen description
>   hallucination"; expected: a picture beats text for layout, and a
>   description from a picture invents behaviour.
> - **Stop rule:** nothing new from a differently worded query and
>   every route has a primary source; ten to fifteen pages opened.

Known items: the card names no known note of the project.

The baseline the note must beat: the picture left by the single-shot
benchmarks of 2023 and 2024, read here as history, in which one
screenshot of one static page goes in, code comes out and the score
is visual similarity, with the conclusion that a picture is the best
input; a maker's claim that a screenshot or a design file is enough
for an agent; and the card's own expectation, that a picture beats
text for layout and that a description from a picture invents
behaviour. A note that only repeats these has added nothing.

## Key findings

Every page was read through a fetch tool that answers from the page
through a small model, so each finding below rests on a summarised
fetch of a primary page. Figures were asked for as rows of the
tables and stand here as returned; quotes likewise. Where the fetch
itself reported a mismatch inside a paper, it is said. "Design tool"
below means the tool that holds the design of the interface.

**F1. In the one multi-page benchmark that varies the input, a
picture added to prose improves where controls stand and leaves
behaviour where it was.** [single source; controlled study: a
benchmark, preprint, no venue shown] VISTA [1] has coding agents
build and launch a multi-page web application in ten categories (128
pages, 3,253 annotated interactions) under five input conditions,
and scores each critical interaction by a localisation score times a
behaviour score against human-annotated targets, with no model as
judge. Pooled over four pairs of model and harness (Table 3):

| Condition | Input | Stack | Localisation | Behaviour | Combined | CLIP |
|---|---|---|---|---|---|---|
| C0 | text prompt only | free | 0.489 | 0.315 | 0.242 | — |
| C1 | text + snapshot | three specified stacks | 0.577 | 0.305 | 0.229 | 0.802 |
| C2 | text + snapshot | free | 0.507 | 0.322 | 0.264 | 0.728 |
| C3 | text + snapshot + Figma JSON | one specified stack, with its template | 0.615 | 0.325 | 0.236 | 0.777 |
| C4 | text + snapshot + Figma JSON | free | 0.600 | 0.329 | 0.261 | 0.827 |

Among the three conditions with a free stack the combined score goes
from 0.242 (prose) to 0.264 (with a snapshot) to 0.261 (with the
design-tool structure as well); localisation goes from 0.489 to
0.507 to 0.600. The behaviour score moves by 0.024 across all five.
The fetch returned no variance and no test of significance;
differences of this size are small, and the level is low throughout,
about a quarter of the combined score attainable. Figures as of 11
Jun 2026.

**F2. The richest input is not reliably the best: structure from the
design tool helped only with a free stack.** [single source;
controlled study, the same benchmark] In [1] the two conditions with
a prescribed stack (C1, C3) scored below prose alone on the combined
measure (0.229 and 0.236 against 0.242) although they located
controls better. The authors, Section 4: "structural input
consistently improves grounding, but its functional payoff requires
implementation flexibility." Per model, pooled over the conditions,
the combined score ran from 0.223 to 0.261, a spread as wide as the
spread between the inputs.

**F3. Behaviour does not travel in pictures: from static screenshots
alone agents realise little of it, and least of all state that
crosses screens.** [emerging; two controlled studies by different
groups, both benchmarks and preprints] UI2App [2] gives a model 3 to
14 screenshots of the routes and states of one application (95 sets,
600 screenshots) and nothing else; where the task is defined it
says: "No action trace or interaction description is provided." Six
models of 2026, scores of 100:

| Model | Runs at first try (%) | Visual fidelity | Interaction inference |
|---|---|---|---|
| Claude Sonnet 4.6 | 95.8 | 71.3 | 36.8 |
| Gemini 3.1 Pro Preview | 89.5 | 73.2 | 8.1 |
| Kimi K2.5 | 73.7 | 55.5 | 19.7 |
| GPT-5.4 | 68.4 | 58.8 | 6.9 |
| Qwen3.5-397B-A17B | 71.6 | 58.5 | 15.3 |
| GLM-4.6V | 24.2 | 33.2 | 4.6 |

By the reach of the state involved, the leader scored 39.9 on state
of the interface, 37.8 on state of the data and 15.8 on state that
persists across routes; the other five scored 3.5 or less on the
last (Table 3; Section 4.3, Finding 3: "Cross-route state remains a
challenging dimension of interaction inference."). The score counts
how much was realised of the behaviour that a reference inventory
reads from the screenshots and does not count what a model added: it
measures what is missed, not what is invented. Vision2Web [3], whose
agents do get text beside the pictures, reports the same weak place
(Section 4.2, Finding 6): "agents exhibit systematic weaknesses in
complex, state-dependent operations." Figures of [2] as of 4 Oct
2026.

**F4. Text about an interaction, added to pictures of its states, is
the largest measured gain of any input change found.** [single
source; controlled study: a benchmark of 127 pages and 374
interactions; models of 2024] Interaction2Code [4] gives a model a
screenshot before and one after an interaction and compares pictures
alone with pictures plus a description of the interaction written by
a human annotator. For GPT-4o under the direct prompt (Table VIII),
on the part of the page the interaction changes: CLIP 0.3737 to
0.6735, SSIM 0.1793 to 0.5612, text 0.2539 to 0.3919, position
0.3951 to 0.7157. Under a prompt that marks the place of the
interaction in the picture the gain is smaller and one measure falls
(SSIM 0.4520 to 0.4336). Text alone, without the pictures, was mixed
and generally below pictures with text. The usual failures without
it: no interaction built, an interaction built in part, the
interactive element missing, the wrong function. The benchmark has
no back end, so nothing bound to a server was tested. First posted
in November 2024 by its number; the version read is of 1 Mar 2026.

**F5. Prose alone loses to a picture for the look of a single page,
by a modest margin.** [single source; controlled study: a benchmark,
preprint; models of early 2025] FullFront [5] scores code written
from a screenshot (200 tasks) and code written from a detailed
description in text (50 tasks). Table 3, picture then text:

| Model | Code score | Visual score of 10 | CLIP |
|---|---|---|---|
| Claude 3.7 Sonnet | 0.64 / 0.60 | 8.93 / 7.84 | 0.89 / 0.87 |
| Gemini 2.5 Flash | 0.63 / 0.52 | 8.64 / 6.83 | 0.88 / 0.83 |
| GPT-4.1 | 0.61 / 0.54 | 8.89 / 7.42 | 0.88 / 0.86 |

Section 4.2: "The Text to Code task, requiring autonomous design
from textual descriptions, proves the most difficult". Two limits:
the paper does not say that the two sets are the same pages, so the
comparison is not matched; and the descriptions were written by a
model from the rendered pages and reviewed by the authors (Appendix
B.2). The version read is of 26 May 2025; a search result indicated
a later revision with newer models, which was not opened.

**F6. A structured specification taken from a picture and handed to
the generator reproduced a single screen more closely than the
picture prompted directly.** [single source; a controlled study and
a user study, both by the authors of the system; preprint]
SpecifyUI [6] defines a specification in JSON: a global part
(layout, colour, shape, usage scenario) and a page composed as page,
section, component, each component with type, function, layout and
colour. A detector cuts the reference screenshot into regions, a
multimodal model writes the specification region by region, and a
code model generates from the specification. On reconstructing a
reference screen (Table 2):

| Method | MSE (lower is better) | CLIP | SSIM |
|---|---|---|---|
| Direct prompt | 57.4214 | 0.7024 | 0.688 |
| Prompt with self-revision | 50.8570 | 0.7553 | 0.787 |
| Specification alone | 45.1431 | 0.8628 | 0.8166 |
| The whole pipeline | 40.9930 | 0.8871 | 0.854 |

In a study with 16 participants against a prompt-driven generator of
designs, three experts rated layout consistency 4.99 against 3.73
and component correctness 5.69 against 4.20 of 7; ease of use was no
better (5.31 against 5.88, not significant). Limits: one screen, no
states, no behaviour, no navigation, which the authors name as
future work (Section 8.3); the data of the technical evaluation was
not described in the part read; the fetch found the percentages in
the text not to match the table; no accuracy is reported for the
step that writes the specification from the picture.

**F7. Structured data from the design tool raises visual fidelity
over a picture and lowers the quality of the code, because models
copy literal values from it.** [single source; controlled study: a
benchmark; "ICLR 2026" by the comment on its arXiv page]
Figma2Code [7] pairs the picture of a design with the metadata of
its design file (213 curated single pages, ten models). For one open
model under direct prompting (Table 3) the visual similarity was
0.5653 from the picture alone, 0.6801 from the metadata alone and
0.6923 from both. Two measures of code quality that the paper
abbreviates APR and AVU, lower being better, stood near zero from
the picture (0.01 and 0.00) and rose to 5.01 and 6.09 from the
metadata and to 2.83 and 2.06 from both; the fetch did not expand
the abbreviations, and that they count absolute positioning and
literal values is the agent's reading of the paper's own
explanation. Among ten models given both inputs, the one with the
highest visual similarity (GPT-5, 0.8405) was among the worst on the
two measures (14.35 and 37.72). The Introduction names the cause:
"models' tendency to directly map absolute coordinates and primitive
visual attributes from the metadata". Single pages only; no flows,
no states.

**F8. Scores fall at every step from one static page to several
pages to a whole application, and later pages come out worse than
earlier ones.** [emerging; controlled study [3], with [1] and [2]
pointing the same way; preprints] Vision2Web [3] has three levels:
one static page from prototype images (100 tasks); an interactive
front end of several pages from 5.9 prototypes on average and about
a thousand tokens of text on how the pages relate (66 tasks); a
full-stack site from a requirements document and prototypes (27
tasks). Rows selected from Table 3, scores of 100:

| Model, harness | One static page | Several pages: visual / functional | Whole application: visual / functional |
|---|---|---|---|
| Claude-Opus-4.5, OpenHands | 53.4 | 46.5 / 66.7 | 38.4 / 57.6 |
| Gemini-3-Pro-Preview, OpenHands | 55.8 | 29.7 / 40.7 | 11.7 / 22.6 |
| GPT-5, OpenHands | 49.6 | 23.9 / 61.4 | 18.3 / 49.7 |
| GPT-5, Claude Code | 43.1 | 23.3 / 64.7 | 9.6 / 23.4 |

Section 4.2, Finding 1: "Agent performance degrades consistently as
task complexity increases across the three task levels." The
analysis of failures (Section 4.3) places the loss between the
modules: fidelity drops on later pages, with "missing or misaligned
components" and "broken navigation links", and what is built drifts
from what was specified. The measures differ by level, so the
columns are not one scale. The paper compares no kinds of input.
Figures as of 27 Mar 2026.

**F9. For changing an interface that exists, text is the better
context than a picture.** [single source; controlled study: a
benchmark; models of early 2025; venue not confirmed] DesignBench
[8] (900 samples in React, Vue, Angular and plain HTML with CSS)
asks for an edit by instruction and for the repair of a display
fault, with the picture of the page, its code, or both as context
(Table 7, the score of a model judge of 10). Claude-3.7: an edit
7.68 from the picture, 8.43 from the code, 8.43 from both; a repair
5.81, 6.70 and 6.85. The three other models show the same order
between picture and code; both together added little and sometimes
lost. Finding 6: "Code-only input consistently outperforms
image-only input." The text here is the code, not a description:
that a description would serve the same is the agent's inference,
not the paper's.

**F10. Left to themselves, models seldom build in components.**
[single source; controlled study, the same benchmark] In [8] the
share of generated code built in a component-based way averaged 0.24
percent for React, 5 percent for Vue and 19 percent for Angular
(Table 9, as the fetch returned it; the definition of the measure
was not read), and Finding 8 says that models "show critical
deficiencies in component-based implementation and
framework-specific syntax." Plain HTML with CSS scored best
(Finding 4). This is components as output; no study found measures
what a component library or design tokens given as input change.

**F11. For a wireframe the only measurement is of 2024 and says that
models misread rough sketches.** [single source; controlled study,
read by its abstract only; history by the card's rule]
Sketch2Code [9], ten models: "even the most capable models struggle
to accurately interpret sketches" (abstract). No study of 2025 or
2026 was found that sets a wireframe beside a finished picture of
the same target.

**F12. Models read the look of a page far below people, and what
they fail on is alignment, size, position and spacing.** [single
source; controlled study: a benchmark, preprint; models of early
2025] In [5] 1,800 multiple-choice questions on screenshots of pages
were put to models. On the subset where people were measured,
experts answered 97, 96 and 94 percent of three kinds of question;
the best models answered 52.5, 50.0 and 56.0 percent (Claude 3.7
Sonnet) and 52.0, 58.0 and 48.0 percent (Gemini 2.5 Pro). Of 200
questions that most models got wrong, 21.5 percent were on
alignment, 19.5 on size, 18.5 on position and 15.5 on spacing
(Section 5.1: "MLLMs exhibit a particular difficulty in accurately
understanding the alignment (21.5%)"). In [8], models asked to find
the design faults in a rendered page found them at an average rate
of 0.27 (Table 10; Finding 9). These are answers to closed
questions, not a description written freely; that they show which
statements of a description from pictures are least to be trusted is
the agent's inference.

**F13. No study measured a description written from pictures; the
three papers that produce one report no accuracy for it.** [single
sources: a case study, a description of a system, and the study of
F6] In [10], a case study, an unnamed model writes user stories from
a screenshot of an application and a high-fidelity mockup of a
change; five kinds of requirement were scored 1 to 5 by raters the
paper does not identify: 3, 3, 4, 3, 3 without the project's
glossary and 5, 5, 4, 5, 5 with it. The one error analysed is a
word of the domain read in its everyday sense ("points" as a score).
No invented function is reported, and none was looked for; there are
two examples and no repeated runs. [11], by a single author and read
by its abstract only, is a system that writes a design specification
of 19 sections from screenshots of a public web page and labels each
claim as measured, observed, inferred or unknown; by its own
abstract its evaluation checks the run of the system and the form of
the output, not whether the specification is visually or
semantically right. [6] writes its specification from the picture by
a model and reports no accuracy for that step.

**F14. Everything measured is on the web, most of it is preprint,
and the judges are models with an error of their own.** [consensus
of the sources opened: an observation of this note over [1] to [8],
not a claim of any one of them] Every benchmark opened generates
HTML or code for a web framework; none builds for native mobile or
the desktop. The pages of [1], [2], [3], [5] and [6] show no venue;
[7] names ICLR 2026 in its comment; [8] carries a conference line
the fetch could not confirm. In [3] the verifier agreed with people
on 218 of 250 checks (87.2 percent) and the visual judge correlated
with people at 0.66 on average; in [2] the judge agreed with two
engineers on 81.8 to 91.1 percent of the labels over 45
applications; [1] uses no model as judge and says of its own visual
measure (Section 6): "a high CLIP score does not imply pixel- or
design-system-faithful output." That a difference of a few points
between two inputs lies within what such instruments blur is the
agent's reading.

## Unexpected

The card asks which input gives the result closest to what was
wanted, as if closeness were one scale. [1] and [2] say it is two:
look and behaviour are scored apart and do not go together. In [2]
the model with the best visual fidelity (73.2) ranks fourth of six
on interaction (8.1), and the leader on interaction scores 4.5 times
as much; the abstract of [1] says that "visual fidelity and
functional correctness are partially decoupled across both input
conditions and agents". The question is answered above as put; a
design that follows it would ask which input carries which of the
two.

The harness around a model moved the scores as much as the input
did. In [3] the same model built whole applications at 23.4
functional under one harness and at 49.7 under another (F8); [1]
says in its limitations (Section 6): "the same model paired with a
different harness could obtain a meaningfully different score." A
measurement of the best input holds for the pair of model and
harness it was made with.

Text that a generating tool writes about its own interface is often
untrue of it. [12], read by its abstract only, took 120 interfaces
from five generative tools over 24 tasks and compared the design
reasons each tool stated with what it built: on average over 25
percent of the stated reasons were not implemented, 34 percent for
functional requirements; the abstract calls them "plausible and
confident design rationales that have little relationship to the
actual implementation." This is not a description from pictures, but
it is the nearest measurement found of a model's text about an
interface asserting what the interface does not do. How
"implemented" was judged is not in the abstract.

In [9], read by its abstract only, experts in interface design
preferred an agent that asks questions to one that waits for
feedback ("a significant preference for proactive question-asking
over passive feedback reception"), and the same abstract says that
the models asked poorly. A lead for the cards on the agent that
proposes; nothing rests on it here.

The text-to-code task of [5] is in effect a round trip: a model
wrote the descriptions from rendered pages, people reviewed them,
and models built from them. Against building from the picture the
round trip lost 0.02 to 0.05 of CLIP and one to two points of ten on
the visual score (F5). This reading is the agent's; the paper does
not present it so, and the pages of the two tasks are not known to
be the same.

## Not found

- A comparison of prose with a structured specification as the only
  input, for the same target and the same agent. Looked for with
  queries 5, 13 and 16 of the Search record and in [1] and [3]. [1]
  varies pictures and design-tool structure beside a text prompt,
  not the form of the text; [6] compares a structured specification
  with a picture prompt, not with prose.
- Any measurement of design tokens or of a component library as an
  input, with and without. Looked for with queries 8 and 13; the
  results were makers' guidance and practitioners' posts, excluded
  by kind.
- A wireframe against a finished picture of the same target, of 2025
  or 2026 (query 11).
- A study of a description or a specification written by a model
  from pictures of existing screens that counts what is right, what
  is missed and what is invented (queries 4, 7, 9, 10, 12 and 14).
  The result lists held benchmarks of invented elements when an
  agent is asked to point at something on a screen: a different
  task, seen by title and not opened.
- Any measurement of building for native mobile or for the desktop;
  every benchmark opened builds for the web.
- Variance over repeated runs or a test of significance for the
  input conditions of [1]: not in what the fetch returned.
- A peer-reviewed publication of [1], [2], [3], [5], [6], [10] or
  [11]: none shown on the pages opened.

## Options

What the description gives the one who builds:

- **A. Text alone.** It carries behaviour and state (F3, F4) and is
  versioned like the other documents; measured weaker on where
  things stand (F1) and on the look of a page (F5).
- **B. Text for behaviour, for states and for what holds between
  screens, with a picture of each screen or state beside it.** The
  reading that fits F1, F3 and F4 together; the picture's gain is on
  position only, and pictures have to be made and kept current.
- **C. B with machine-readable structure from the design tool as
  well.** Better localisation and visual similarity (F1, F7); no
  gain for behaviour, a loss where the stack is prescribed (F2),
  code that copies literal values (F7); it binds the chain to a
  design tool.
- **D. A structured specification of each screen in text: page,
  section, component, with typed fields.** One study in its favour,
  on a single screen and without behaviour (F6); nothing measured
  sets prose against it.

How a first description comes about:

- **E. Written by a model from pictures, each statement on
  behaviour marked as inferred and settled by a human.** No
  measurement of its accuracy (F13); its weak points are known
  (F12, F3).
- **F. Written from the code of the application where there is
  one.** Text was the better context for change in F9; a study of
  describing from code was not looked for by this card.
- **G. Found by questions alone.** Not measured here; the fourth
  paragraph of Unexpected is a lead.

## Relevance to this project

The recommendation: let the description say in words everything a
picture does not carry, and let a picture stand beside it for where
things are. It states for each screen what every control does, which
states the screen has and what persists from one screen to the next,
because that is what agents failed at with pictures alone (F3), what
gained most when it was written out (F4) and where results fall as
the screens multiply (F8); a picture is attached where position
matters (F1, F5); no gain for behaviour is expected from the
structure of a design tool (F1, F2). This is option B, chosen
against handing on pictures or a design file alone (F3, F7) and
against prose with no picture (F1, F5).

A first description can be written from pictures, as the first trial
will do, within known limits: a model's reading of alignment, size,
position and spacing is unreliable (F12), behaviour is not in the
picture at all (F3), and nobody has measured how much such a
description invents (F13). The agent's own inference: such a
description is a draft of what is visible, and every statement in it
on behaviour is a guess that the human settles; the labelling of
[11] is a model for marking it, itself unmeasured.

On the idea to be tested, a small definition for every element and a
page definition that names its elements: no measurement found tests
it, for or against. The nearest are F6 (a hierarchy of page, section
and component helped on one screen) and F10 (models do not build in
components on their own). The agent infers from F10 only that a
description naming shared elements would have to tell the builder to
reuse them; whether the idea helps stays open.

How much structure a description needs for an agent is not decided
by measurement: the one comparison that would decide it, prose
against a structured specification, was not found.

The limits of all of it: the web only; models of early 2025 in F5,
F9, F10 and F12 and of 2024 in F4; a single source for nearly every
finding; everything read through a summarising fetch.

Consult when: deciding what the description must say in words and
what may be left to a picture; deciding whether the first trial may
start from screenshots and how its result is checked; someone holds
that a screenshot or a design file is enough for an agent; choosing
how a build is judged against a description, look and behaviour
apart; a native or a desktop target is first described, since
nothing here covers it; a newer version of [1], [2], [3] or [5]
appears.

## Sources

1. "VISTA: An End-to-End Benchmark for Visual Spec-to-Web-App Coding
   Agents". JunJia Guo and Jingdi Chen (University of Arizona),
   Yuhang Yao (Zoom), Jiawei Zhou (Stony Brook University). arXiv
   2605.26144v2, 11 Jun 2026 (byline: the version stamp of the
   page). https://arxiv.org/html/2605.26144v2 Kind: primary, a
   preprint. How read: summarised fetch of the whole page (Sections
   3 to 6, Tables 1 to 3, Appendix B as returned). Original.
2. "UI2App: Benchmarking Visual Interaction Inference in Executable
   Web Application Generation". Grace Man Chen and seven others, The
   Hong Kong University of Science and Technology (Guangzhou). arXiv
   2607.06306, v1 of 7 Jul 2026, v2 of 4 Oct 2026 (byline: the
   submission history of the abstract page).
   https://arxiv.org/abs/2607.06306 and
   https://arxiv.org/html/2607.06306v2 Kind: primary, a preprint.
   How read: summarised fetch; the abstract page in full, of the
   full text characters 0 to 100000 of 170209 (the tables by
   category of application and what follows them were not read).
   Original.
3. "Vision2Web: A Hierarchical Benchmark for Visual Website
   Development with Agent Verification". Zehai He and others,
   Tsinghua University and Zhipu AI. arXiv 2603.26648v1, 27 Mar 2026
   (byline: the version stamp of the page).
   https://arxiv.org/html/2603.26648v1 Kind: primary, a preprint.
   How read: summarised fetch of the whole page. Original.
4. "Interaction2Code: Benchmarking MLLM-based Interactive Webpage
   Code Generation from Interactive Prototyping". Jingyu Xiao and
   others, The Chinese University of Hong Kong and four other
   universities. arXiv 2411.03292v3, 1 Mar 2026 (byline: the version
   stamp of the page). https://arxiv.org/html/2411.03292v3 Kind:
   primary; no venue stated on the page. How read: summarised fetch
   of the whole page; the frequencies of the kinds of failure stand
   in a figure the fetch could not read. Original.
5. "FullFront: Benchmarking MLLMs Across the Full Front-End
   Engineering Workflow". Haoyu Sun (Tongji University), Huichen
   Will Wang (University of Washington), Jiawei Gu (Sun Yat-sen
   University), Linjie Li (Microsoft), Yu Cheng (The Chinese
   University of Hong Kong). arXiv 2505.17399v2, 26 May 2025
   (byline: the version stamp of the page).
   https://arxiv.org/html/2505.17399v2 Kind: primary, a preprint.
   How read: summarised fetch of the whole page. Original; a later
   revision may exist and was not opened.
6. "SpecifyUI: Supporting Iterative UI Design Intent Expression
   through Structured Specifications and Generative AI". Yunnong
   Chen and Liuqing Chen (Zhejiang University), Chengwei Shi
   (Beihang University). arXiv 2509.07334v1, 9 Sep 2025 (byline: the
   version stamp of the page). https://arxiv.org/html/2509.07334v1
   Kind: primary, a preprint. How read: summarised fetch, characters
   0 to 100000 of 119665 (the end of the references and the
   appendices of prompts were not read). Original.
7. "Figma2Code: Automating Multimodal Design to Code in the Wild".
   Yi Gui and eleven others. arXiv 2604.13648, v1 of 15 Apr 2026,
   comment "ICLR 2026" (byline: the submission history of the
   abstract page). https://arxiv.org/abs/2604.13648 and
   https://arxiv.org/html/2604.13648v1 Kind: primary. How read:
   summarised fetch; the abstract page in full, of the full text
   characters 0 to 100000 of 134580 (the later appendices were not
   read). Original, the authors' copy of a conference paper whose
   proceedings page was not opened.
8. "DesignBench: A Comprehensive Benchmark for MLLM-based Front-end
   Code Generation". Jingyu Xiao and others (The Chinese University
   of Hong Kong), Yintong Huo (Singapore Management University).
   arXiv 2506.06251v3, 15 Mar 2026 (byline: the version stamp of the
   page). https://arxiv.org/html/2506.06251v3 Kind: primary; the
   conference line on the page is a template with empty fields. How
   read: summarised fetch, characters 0 to 100000 of 104867; the
   frequencies of the kinds of failure stand in a figure the fetch
   could not read. Original.
9. "Sketch2Code: Evaluating Vision-Language Models for Interactive
   Web Design Prototyping". Ryan Li, Yanzhe Zhang, Diyi Yang. arXiv
   2410.16232, v1 of 21 Oct 2024, comment "preprint, 9 pages"
   (byline: the submission history of the abstract page).
   https://arxiv.org/abs/2410.16232 Kind: primary. How read:
   summarised fetch of the abstract page only; the paper itself was
   not opened. Original.
10. "Exploring LLMs for User Story Extraction from Mockups". Diego
    Firmenich and four others, Universidad Nacional de la Patagonia
    and other Argentine and Ecuadorian institutions. arXiv
    2602.16997v1, 19 Feb 2026 (byline: the version stamp of the
    page). https://arxiv.org/html/2602.16997v1 Kind: primary, a
    preprint. How read: summarised fetch of the whole page.
    Original.
11. "Secret MCP: Evidence-Bounded and Context-Isolated Design
    Specification Generation from Web Screenshots". Yeongjin Jo.
    arXiv 2608.24944, v1 of 24 Aug 2026 (byline: the submission
    history of the abstract page). https://arxiv.org/abs/2608.24944
    Kind: primary, a preprint. How read: summarised fetch of the
    abstract page only; the paper itself was not opened. Original.
12. "Design Theater: Evaluating the Gap Between User-Facing Design
    Reasoning and Implementation in Generative UI Tools". Kashif
    Imteyaz and five others. arXiv 2607.22928, v1 of 24 Jul 2026, v2
    of 31 Jul 2026, comment "Accepted at AAAI/AIES" (byline: the
    submission history of the abstract page).
    https://arxiv.org/abs/2607.22928 Kind: primary. How read:
    summarised fetch of the abstract page only. A copy: the authors'
    preprint of a conference paper whose publisher's page refused
    the fetch.

## Opened and not used

- "MUIAnno: An Expert-Annotated Dataset and Evaluation Benchmark for
  Mobile UI Understanding", arXiv 2605.17656, abstract page,
  https://arxiv.org/abs/2605.17656 : off the question, a data set
  for detecting the elements of mobile screens, with no description
  written and no behaviour read.
- The publisher's proceedings page of [12]: it refused the fetch
  (access denied by a filter against automated clients), so it is
  given no address here; the arXiv copy [12] was opened in its
  place.

## Search record

Queries, in order:

1. design to code benchmark multi-page 2025
2. UI to code benchmark agentic 2026 arXiv
3. text specification outperforms screenshot for UI generation (the
   card's first disconfirming query)
4. screen description hallucination vision language model UI (the
   card's second disconfirming query)
5. intermediate representation UI code generation LLM screenshot
   ablation textual description improves
6. benchmark web application generation from natural language
   requirements agents multi-page 2025 PRD
7. LLM generate UI specification from screenshots evaluation missing
   invented behaviour requirements reverse engineering
8. design system component library LLM UI generation adherence study
   design tokens empirical
9. MLLM web UI understanding benchmark perception element
   description accuracy 2025 screenshots what models miss
10. generating user stories or requirements from GUI screenshots
    with LLM empirical study hallucinated functionality
11. wireframe sketch to code benchmark 2025 2026 MLLM low-fidelity
    vs high-fidelity input comparison
12. MLLM screenshot to functional description of screen accuracy
    study omissions fabricated elements UI summarization evaluation
    2025 2026
13. structured specification versus natural language prompt coding
    agent frontend generation controlled experiment 2026 design
    tokens component library input
14. screen summarization widget captioning evaluation 2025
    hallucinated UI elements human evaluation mobile screens
    description
15. "Design Theater" generative UI tools stated design rationale
    implementation mismatch
16. image-to-code versus text description to code web generation
    comparison "text-only" input ablation layout 2025
17. UI-Lens assessing general MLLMs CVPR 2026 UI understanding
    benchmark
18. FullFront benchmark webpage perception QA image to code text to
    code results human accuracy

Pages opened, sixteen fetches, fifteen of which returned a page: the
full text of [1], [3], [4], [5], [6], [8] and [10]; the abstract
page and the full text of [2] and of [7], two fetches each; the
abstract pages of [9], [11] and [12]; the abstract page of the data
set named under Opened and not used; the publisher's page of [12],
which refused the fetch.

Seen in the result lists by title and not opened, so cited for
nothing: WebGen-Bench, WebCoderBench, WebCompass, MRWeb,
TaoD2C-Bench, 1D-Bench, Athena, ScreenCoder, SchemaGUI, WebUIBench,
WebMMU, GUI-HalluBench, UI-Lens, LaTCoder, LayoutCoder, Design2Code.

The disconfirming queries. "Text specification outperforms
screenshot for UI generation" (query 3, reworded in 16) found no
study in which text alone beat a picture for the look of a page; the
one comparison found has the picture ahead for all three models
(F5), which is what the card expected for layout. It also found what
the expectation does not cover: for behaviour, text added to
pictures gave the largest gain (F4), with prose alone the behaviour
score was no lower than with pictures (F1), and for changing an
existing interface code as text beat the picture (F9). "Screen
description hallucination" (query 4, reworded in 7, 12 and 14) found
benchmarks of elements invented when an agent points at a screen,
and nothing that measures behaviour invented in a description
written from pictures: the second half of the expectation is neither
confirmed nor refuted by measurement.

The run ended by the opening budget, not by the card's stop rule:
the openings were spent with two routes still without a primary
source of their own (tokens and a component library as input; a
measured description from pictures), and the last differently worded
queries were still returning titles not seen before.
