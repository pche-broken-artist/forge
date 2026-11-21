---
date: 2026-11-21
project: forge
topic: how an agent gets from requirements to a first interface proposal
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-17-proposing-agent
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 17; no known notes named by the card; web sources below
---

# An agent gets from requirements to a first interface proposal by reading first, asking only what the documents leave open and marking what it assumed

<!-- Shape: templates/research.md -->

## In short

The published workflows of 2025 and 2026 that were read agree on a
pattern more than on a questionnaire. The agent reads what stands
upstream (requirements, earlier decisions, the codebase and its
component library) before it asks anything; what those already answer
is pre-filled and put to the human for confirmation, not asked again;
what is left is asked by impact, each question carrying the agent's
own recommended answer; what is still open is written down as a
marked assumption; the result lands in a file every later step reads,
and nothing is built before the human has approved it. What is asked
falls into a few kinds: who the product is for and what it must do,
the behaviour the requirements are silent on (journeys, the empty,
error and loading states, accessibility), the visual identity (or
which existing design system binds), the words, and the devices. No
source read prescribes a fixed, ordered list of questions for screens
and flows: screens are proposed as alternatives and judged by seeing
them, not asked about. This is moderately sure: it rests on prompt
files and vendors' own documentation, all read through a summarising
fetch, and on no measurement of the pattern's effect. The
disconfirming query confirmed the direction (vague input gives
inconsistent output; vendors' own skill files name the sameness of
generated interfaces) but found no study that compares an agent that
asks with one that does not. The unexpected thing: the one open
format in the search words, DESIGN.md, describes the visual identity
of a design system only, and two of the tools read split the
description in two documents, how it looks and how it works; the
second has no shared format in the sources read.

## Question

The frame: a framework carries an idea down a chain of versioned
Markdown documents (what is wanted and why, business requirements, a
solution design, user stories); a human works each document with an
AI agent that asks, proposes and writes while the human decides; the
author wants the same for the interface of an application, described
in text, proposed by an agent that reads the documents above and asks
what it lacks, for the web, the mobile web, native mobile and the
desktop.

The card, verbatim:

> **Card 17: The agent that proposes the description**
>
> **Question:** How does an AI agent get from requirements, user
> stories and a solution design to a first proposal of an interface:
> what of an interface cannot be inferred from those documents and
> must be asked, which questions are asked and in which order before
> screens or flows are proposed, and how do the published workflows
> of 2025 and 2026 keep the agent from inventing arbitrary layout and
> interaction?
>
> **Why it matters:** the author expects the agent to read
> everything, ask what it lacks and make the proposal; this is the
> step an elicitation of the description would define.
>
> **What would answer it:** the published workflows, prompts and
> skills of AI design tools and spec-driven kits, read as primary
> artefacts in their repositories and documentation.
>
> **Where to look:** the steps from requirements to design in
> spec-driven kits and their prompt files; the question flows of AI
> interface generators and design assistants; public agent skills and
> rules for interface design. What human method prescribes for the
> same step is card 14's. Search words from card 1: "spec-driven
> development", "spec-first", "spec-anchored", "spec-as-source",
> "constitution", "steering files", "EARS", "DESIGN.md". Primary
> artefacts in public repositories (schemas, component and page
> files, agents' rules and prompt files, the schemas of servers for
> design tools, issue trackers) before commentary about them.
>
> **Disconfirming query:** "AI generated UI generic", "LLM design
> without clarifying questions"; expected: reports that an agent
> which does not ask produces a generic interface.
>
> **Stop rule:** nothing new from a differently worded query and
> every route has a primary source; ten to fifteen pages opened.

The baseline the note must beat: the bare instruction "read
everything and ask clarifying questions". The note has to say, from
primary artefacts, what kinds of things are asked, in what order and
form, and by which concrete mechanisms a workflow keeps the agent
from filling the rest with invention.

## Key findings

Two notes on reading. Every source was read through a summarising
fetch: the tool returns a small model's answer to a targeted prompt,
with the short passages it marked as verbatim; every finding below
rests on such fetches, and the quotes are as the fetch returned them.
And "design" is said as the frame asks: in spec-kit and Kiro it is
the technical design between requirements and tasks; in DESIGN.md it
is the visual identity of a design system; in Claude Design and Figma
it is the design of the interface held in a design tool.

**F1. Of the four spec-driven kits read, two have an interface step
of their own; in the other two the interface appears only as one
category of clarification, or not at all.** [emerging; prompt files
and vendor documentation, summarised fetch] In spec-kit's two prompt
files read, the interface is one category of the ambiguity scan of
the clarify command, "Interaction & UX Flow", with three points:
"Critical user journeys / sequences", "Error/empty/loading states",
"Accessibility or localization notes" [1]; the specify command says
"Focus on **WHAT** users need and **WHY**." and to "Avoid HOW to
implement (no tech stack, APIs, code structure)." and is silent on
layout [2]. Kiro's specs page names three files, and its design file
is technical: "design.md - Documents technical architecture, sequence
diagrams, and implementation considerations"; the page says nothing
of interface, wireframes or mock-ups, and the only question it
documents is "Kiro will ask if you are developing a Feature or fixing
a Bug" (page updated 2026-11-12) [3]. BMAD has a skill `bmad-ux` that
writes two documents, "`DESIGN.md` for how the product looks (tokens,
typography, components)" and "`EXPERIENCE.md` for how it works
(structure, states, interactions, accessibility, key flows)", run
"when the interface matters to the outcome; skip it for back-end
work" [4]. GSD has an agent whose front-matter says it "Produces
UI-SPEC.md design contract for frontend phases." and whose question
is "What visual and interaction contracts does this phase need?" [5].

**F2. What the workflows treat as not inferable and ask or have
confirmed falls into five kinds: who and what for, the behaviour the
requirements are silent on, the visual identity, the words, the
devices.** [emerging; prompt files and vendor documentation,
summarised fetch; the grouping into five kinds is this note's own]

| What is asked or put for confirmation | Where |
|---|---|
| "who the product is for, what it needs to do, the constraints" | Impeccable, `init` [6] |
| Subject, audience and primary job, proposed by the agent "as a proposal" and confirmed | Anthropic's frontend-design skill [7] |
| "User roles / personas differentiation"; critical journeys; error, empty and loading states; accessibility and localisation; "Ambiguous adjectives ("robust", "intuitive") lacking quantification" | spec-kit, clarify [1] |
| The audience; "Mention whether your design needs to work on mobile, tablet, and desktop." (advice to the prompt's author, not a question of the tool) | Claude Design, getting started [8] |
| Spacing, typography, colour, copy (primary call to action, empty state, error state, destructive actions), third-party component blocks; whether to set up a component library | GSD, UI researcher [5] |
| The user's own vision of look and behaviour, with "creative tools such as color themes, design directions, wireframes, and key-screen mocks" | BMAD, `bmad-ux` coaching path [4] |

Not found among the things asked: the layout of a given screen and
the structure of navigation. Those are proposed, not asked (F5, h).

**F3. The order is "read, pre-fill, then ask by impact"; no source
read prescribes a fixed sequence of questions for screens and
flows.** [emerging; prompt files, summarised fetch] GSD's agent reads
the requirements file, the file of earlier decisions and the research
file first, detects the component library and the styling
configuration in the codebase, and asks only what those left open:
if upstream answers a question, "do NOT re-ask it. Pre-populate the
contract and confirm."; its own questions run in the order spacing,
typography, colour, copy, registry [5]. Impeccable's `init` "reads
your code, asks only what it can't infer." [6]. spec-kit's clarify
ranks by weight: "If more than 5 categories remain unresolved, select
the top 5 by (Impact * Uncertainty) heuristic.", with "Maximum of 5
total questions across the whole session." and the rule to "Exclude
questions already answered, trivial stylistic preferences, or
plan-level execution details (unless blocking correctness)." [1];
its specify step allows fewer still, "LIMIT: Maximum 3 [NEEDS
CLARIFICATION] markers total", ordered "scope > security/privacy >
user experience > technical details" [2]. The brainstorming skill of
superpowers asks only when the answer would change what gets built
and the request and the project do not already answer it, the
biggest unsettled point first, open questions about goals before
options (summary of the fetch, not a quote) [9]. The sources
disagree on pacing: clarify says "Present EXACTLY ONE question at a
time." [1] and superpowers asks one at a time [9], while specify says
"Present all questions together before waiting for responses" [2]
and GSD batches where it can [5].

**F4. A question comes with the agent's own answer: asking, in these
workflows, is mostly proposing and having it confirmed.** [emerging;
prompt files, summarised fetch] spec-kit's clarify: "Present your
**recommended option prominently** at the top with clear reasoning
(1-2 sentences explaining why this is the best choice)."; answers are
a choice of two to five options or a phrase of at most five words,
and each is written back into the specification under a
"Clarifications" heading as "- Q: <question> → A: <final answer>."
[1]. specify presents its questions as a table "| Option | Answer |
Implications |" [2]. superpowers describes each named choice with its
trade-offs and says which it would pick (summary) [9]. GSD pre-fills
and has each value confirmed or overridden, the source of a
pre-filled answer noted [5]. Anthropic's skill tells the agent to
"identify it yourself before designing, and confirm with the client."
[7].

**F5. Invention is contained by eight mechanisms, none of which is
"ask more".** [emerging for the mechanisms, read in prompt files and
vendor documentation; vendor claim for their effect, which no source
read measures; summarised fetch]

- a. *Upstream first, pre-fill with provenance.* [5], [6] as in F3.
- b. *Assumptions said out loud.* spec-kit: "Make informed guesses
  based on context and industry standards" and "Use reasonable
  defaults for unspecified details (document assumptions in
  Assumptions section)" [2]; BMAD's fast path drafts both documents
  with `[ASSUMPTION]` tags [4]; GSD notes a default as a default [5].
- c. *One persistent file every later step reads.* Impeccable: "Run
  `/impeccable init` once per project", "Every later command reads
  it." [6]; DESIGN.md is defined as "a self-contained, plain-text
  representation of a design system." whose overview serves for
  "guiding the agent's high-level stylistic decisions when a specific
  rule or token isn't explicitly defined." [10]; Claude Design: "When
  you create a project, it automatically inherits your organization's
  design system." [8]; Figma's guide: "Set project-level guidance to
  keep output consistent." [11].
- d. *Binding to what exists.* GSD reads the component library's
  configuration and does not re-specify what the project has [5];
  Figma's example rules read "IMPORTANT: Always use components from
  `/path_to_your_design_system` when possible" and "Avoid hardcoded
  values, use design tokens from Figma where available", under a
  heading "Required flow (do not skip)", and without the mapping of
  components to code "the model is guessing." [11].
- e. *A gate before building.* superpowers builds nothing until the
  human has approved the design document (summary) [9]; Lovable's
  plan mode writes a plan first, asks before it ("Lovable often asks
  clarifying questions to understand your goals and constraints
  before it proposes a plan."), lists "Key decisions, assumptions,
  and constraints" and builds only what is approved [12].
- f. *A rule of precedence between text and picture.* BMAD: "When
  either conflicts with a mock, the document wins." [4].
- g. *Named defaults to stay away from.* Anthropic's skill:
  "AI-generated design right now clusters around some traits" and
  "Where it leaves an axis free, don't spend that freedom on one of
  these defaults." [7]; Impeccable names "Inter for everything.
  Purple-to-blue gradients. Cards nested in cards, gray text on
  colored backgrounds." [6].
- h. *Alternatives shown, not one answer given.* superpowers proposes
  two or three approaches with a recommendation and offers mock-ups
  in a browser tab only where seeing helps, in its own message:
  "Want me to open a browser tab with some mockups?" [9]; BMAD's
  coaching path works with design directions, wireframes and
  key-screen mocks [4]; Claude Design is refined on a canvas:
  "Inline comments let you click directly on a specific part of the
  canvas and request a targeted change." [8].

**F6. Two of the tools read split the description in two documents,
and the open format covers one of the two.** [emerging; vendor
documentation and a draft specification, summarised fetch] BMAD
separates how the product looks from how it works [4]; Impeccable
writes a product file at `init` and a visual one ("`/impeccable
document` to capture your existing visual system in `DESIGN.md`.")
[6]; GSD keeps one contract per phase [5]. The DESIGN.md
specification is marked `version:
alpha`, describes "the visual identity of a brand and product." in
ten ordered sections (overview, colours, typography, layout,
elevation, shapes, motion, voice and content, components, do's and
don'ts) and holds no screens, flows or navigation [10].

**F7. Asking is not the only published answer, and the sources
disagree on how much of it is right.** [contested; prompt files and
vendor documentation, summarised fetch] BMAD offers a fast path that
drafts at once with tagged assumptions beside a coaching path that
elicits, and says of its agent that it "records your vision, and
never volunteers its own." [4]. Anthropic's skill has the agent infer
the subject and fill gaps itself, confirming only the subject [7].
spec-kit caps the questions at three markers and five questions and
otherwise guesses with a record [1], [2]. superpowers asks only what
would change the build [9]. None argues for a long interview.

**F8. The disconfirming query confirmed the direction and found no
measurement of asking.** [emerging; one practitioner evaluation, one
abstract of a peer-reviewed study, vendor statements; summarised
fetch] A practitioner evaluation of interface generators (2025-12-05)
reports that "a detailed prompt yielded quality results resembling
what a human designer created" while "a vague prompt generated
inconsistent and unpredictable outcomes across the board", with
"designs that feel randomly pieced together instead of thoughtfully
structured." and tools that "generate more elements than necessary in
response to broadly scoped prompts."; it also says "writing long,
detailed text prompts is rarely the default strategy in practice";
the fetch found in it no sentence on a generic look and nothing on
tools asking questions [13]. The abstract of a CHI '26 paper says
users "struggle to articulate design intent and evaluate or refine
results" and that making design semantics explicit "enhances users'
perceived control over intent expression and outcome interpretation";
the number of participants is not in the abstract and the paper's
body was not read [14]. The sameness of unsteered output is stated by
two skill files themselves [6], [7]: a vendor claim, not a
measurement. Two generators document that they ask: "Claude will also
ask clarifying questions if it needs more information." [8] and
Lovable's plan mode [12]; neither says what is asked.

**F9. A workflow that pushes for visuals can itself make the agent
invent.** [single source; an issue report, open, labelled a bug, no
maintainer's answer; summarised fetch] An issue against BMAD 6.12.0,
opened 2026-10-06, reports that the fast path of `bmad-ux` says "skip
creative tools" while its closing step renders key-screen mocks with
no condition, and that the skill's rubric rates "Color tokens missing
hex … are critical"; on a project whose visual identity is not yet
decided the run would therefore produce invented visuals, and an
honestly empty visual document would be rated a critical defect. The
reporter asks for a verdict for an identity deliberately deferred,
apart from one that is missing [15].

## Unexpected

**Screens are the question, not what follows the questions.** The
card assumes questions are asked "before screens or flows are
proposed". In [4], [8] and [9] the screens, mock-ups and directions
are themselves the device of elicitation: the human is shown two or
three and reacts. What is asked in words beforehand is the context
and the identity (F2); the layout is found by showing. The question
is still answered as put (F2 to F4), but an elicitation that tries to
settle layout by questions alone would have no precedent among the
workflows read.

**DESIGN.md is not a description of an interface.** The search word
carried from card 1 names a format that, by its own draft
specification, is "a self-contained, plain-text representation of a
design system." with no screens, flows or navigation [10]. BMAD pairs
it with a second document for behaviour [4]; that second half has no
shared format in the sources read.

**"Not decided yet" needs a state of its own.** The issue in [15]
shows a workflow with no way to say that the visual identity is
deferred on purpose: the tool either invents it or reports a defect.
A lead for how a description marks what is open.

**Extensions to spec-kit for wireframes.** A search result, not
opened, describes a community extension that puts the making and the
sign-off of wireframes between spec-kit's clarify and plan steps, and
a fork with interface artefacts. Unverified; it suggests the missing
interface step of F1 is felt by the kit's users.

## Not found

- No workflow read takes requirements, user stories and a solution
  design together as its named inputs for an interface. GSD's agent
  reads a requirements file, a decisions file and a research file
  [5]; BMAD's documentation does not list what `bmad-ux` reads [4].
- No fixed, ordered list of questions for screens, flows or
  navigation in any source read.
- No study comparing an agent that asks before proposing an interface
  with one that does not. A Graphics Interface 2026 paper on
  question-guided input seems to be one; its PDF opened but the fetch
  could not read it (Opened and not used).
- No question about platform conventions (web against native mobile
  against desktop) in any workflow read; the nearest is the advice in
  [8] to mention the devices.
- No workflow read writes a definition per element with a page
  definition that places the elements; the outputs are one or two
  documents per product [4], [6] or one per phase [5].
- The prompt file of BMAD's `bmad-ux` itself: three paths in the
  repository answered "not found" and a registry's copy "gone"; BMAD
  is described from its documentation [4] and an issue that quotes
  the file [15]. The reference file of Impeccable's `init` (formerly
  "teach"): not found at the path tried; only the README was read
  [6]. Figma's documentation page of the skill that writes
  design-system rules: not found at the address the search gave; the
  guide's README was read instead [11].
- Kiro's steering files, its "Design-First" variant (named, not
  described in [3]) and the question flows of v0 and Stitch were not
  opened; nothing is claimed of them.
- Dates of the prompt files: the raw files carry none; they were read
  from the main branch on 2026-11-21.

## Options

- **A. Ask what is left.** The agent reads the chain, marks against a
  fixed list of kinds (F2) what is answered, pre-fills it with where
  it came from, and asks the rest by impact, one question with a
  recommendation at a time ([1], [5]). Cheap for the human, keeps
  provenance; depends on the list of kinds being right, and a cap on
  questions can cut what matters.
- **B. Draft first, assumptions marked.** A proposal at once, every
  guess tagged in the text until judged ([2], [4] fast path). Fast,
  and concrete text sharpens the reaction; the draft anchors, and
  where the identity is undecided it invites invention [15].
- **C. Show to ask.** Layout and flow are put as two or three
  alternatives to be seen and chosen ([4], [8], [9]). Fits what
  cannot be asked in words; needs a preview, and a rule that the text
  wins over the picture [4].
- **D. Two descriptions.** Identity (how it looks) elicited once per
  product and reused, behaviour (how it works) per feature ([4],
  [6]). One half meets an open draft format [10]; the other has none.
- **E. A and C together, B as the short way.** Words for context,
  behaviour and identity; alternatives for layout; a drafted proposal
  with marked assumptions where the human hands the work over.

## Relevance to this project

The recommendation, as this note's own inference from F2 to F5:
define the elicitation as option E. The agent reads the documents
above first and tells the human what they already settle; it works a
fixed list of kinds of things an interface description must settle
(who and what for, behaviour where the requirements are silent with
the empty, error and loading states, identity or the binding design
system, the words, the devices and platforms), asks only the kinds
left open, by weight, each question with its recommendation; it
proposes screens and flows as alternatives to be seen rather than
asking about layout; every guess stays marked in the description
until the human has judged it, with a way to say "deferred on
purpose"; and the text wins over any picture. This rests on prompt
files and on vendors' documentation, not on a measured effect. It is
chosen against the bare "ask clarifying
questions" (no list of kinds, so the agent asks what is easy and
invents the rest), against a long fixed interview (no source
prescribes one, and two cap the questions), and against drafting
alone (F9). Whether identity and behaviour are one document or two is
left to the cards on the screen and on design systems; F6 only says
that two of the tools read keep them apart and one does not. The
platforms are the weakest part:
nothing read asks about them.

Consult when: the elicitation of the interface description is
defined; the list of what the agent must ask is drawn up; it is
decided how an assumption or a deferred decision is marked in a
description; a first proposal comes out generic and the cause is
looked for; the question of one document or two comes up.

## Sources

1. "clarify" command prompt, spec-kit, GitHub; undated (raw file,
   main branch, read 2026-11-21);
   https://raw.githubusercontent.com/github/spec-kit/main/templates/commands/clarify.md
   ; primary; summarised fetch of the whole file (taxonomy, limits,
   question format, write-back); original.
2. "specify" command prompt, spec-kit, GitHub; undated (raw file,
   main branch, read 2026-11-21);
   https://raw.githubusercontent.com/github/spec-kit/main/templates/commands/specify.md
   ; primary; summarised fetch of the whole file (clarification
   markers, defaults and assumptions, question table); original.
3. "Specs", Kiro documentation; 2026-11-12, dated by the page's own
   "Page updated" line (byline);
   https://kiro.dev/docs/specs/ ; primary (vendor's documentation of
   its own product); summarised fetch of the whole page; original.
4. "Design UX and Architecture", BMAD Method documentation,
   bmad-code-org; undated;
   https://docs.bmad-method.org/plan/design-ux-and-architecture/ ;
   primary (the project's own documentation); summarised fetch of the
   whole page, the section "Design the Experience" used; original.
5. "gsd-ui-researcher" agent definition, get-shit-done, gsd-build;
   undated (raw file, main branch, read 2026-11-21);
   https://raw.githubusercontent.com/gsd-build/get-shit-done/main/agents/gsd-ui-researcher.md
   ; primary; summarised fetch of the whole file, which declined to
   reproduce long passages and gave short quotes; original.
6. README of the repository "impeccable", pbakaus; undated (read
   2026-11-21); https://github.com/pbakaus/impeccable ; primary (the
   author's description of his own tool: its claims of effect are the
   author's own); summarised fetch of the README; original.
7. "frontend-design" skill, repository "skills", Anthropic; undated
   (raw file, main branch, read 2026-11-21);
   https://raw.githubusercontent.com/anthropics/skills/main/skills/frontend-design/SKILL.md
   ; primary; summarised fetch of the whole file; original.
8. "Get started with Claude Design", Claude Help Center, Anthropic;
   undated (the page says only "Updated over 3 weeks ago");
   https://support.claude.com/en/articles/14604416 ; primary
   (vendor's documentation of its own product); summarised fetch of
   the whole page; original.
9. "brainstorming" skill, repository "superpowers", obra; undated
   (raw file, main branch, read 2026-11-21);
   https://raw.githubusercontent.com/obra/superpowers/main/skills/brainstorming/SKILL.md
   ; primary; summarised fetch of the whole file, which declined to
   reproduce it verbatim: two short quotes, the rest paraphrase;
   original.
10. "DESIGN.md" format specification, `docs/spec.md`, repository
    "design.md", Google Labs; undated, marked `version: alpha` (raw
    file, main branch, read 2026-11-21);
    https://raw.githubusercontent.com/google-labs-code/design.md/main/docs/spec.md
    ; primary (a draft specification); summarised fetch of the whole
    file; original.
11. README of the repository "mcp-server-guide", Figma; undated (read
    2026-11-21); https://github.com/figma/mcp-server-guide ; primary
    (vendor's guide to its own server); summarised fetch of the
    README, the section "Add custom rules" used; original.
12. "Plan mode", Lovable documentation; undated;
    https://docs.lovable.dev/features/plan-mode.md ; primary
    (vendor's documentation of its own product); summarised fetch of
    the whole page; original.
13. "Prompt to Design Interfaces: Why Vague Prompts Fail and How to
    Fix Them", Huei-Hsin Wang, Nielsen Norman Group; 2025-12-05
    (byline); https://www.nngroup.com/articles/vague-prototyping/ ;
    primary for its own evaluation, which is qualitative and not a
    controlled study (the publisher sells training and consulting in
    the field); summarised fetch of the whole article, fetched twice
    with different prompts; original.
14. "Bridging Gulfs in UI Generation through Semantic Guidance",
    Seokhyeon Park, Soohyun Lee, Eugene Choi, Hyunwoo Kim, Minkyu
    Kweon, Yumin Song, Jinwook Seo; arXiv:2601.19171, v1 2026-01-27,
    v2 2026-02-09 (the page's submission history), comment "In
    Proceedings of the 2026 CHI Conference on Human Factors in
    Computing Systems (CHI '26)"; https://arxiv.org/abs/2601.19171 ;
    primary; partially: the abstract page only, by summarised fetch,
    the paper's body not read; original (preprint of the proceedings
    paper).
15. Issue 3053, "[6.12.0] bmad-ux pushes for visuals regardless of
    working mode: unconditional key-screen mocks, and missing tokens
    rated critical", repository BMAD-METHOD, bmad-code-org; opened
    2026-10-06, labelled 2026-10-10 (the page's own dates), open;
    https://github.com/bmad-code-org/BMAD-METHOD/issues/3053 ;
    primary (issue tracker; a user's report, not the maintainers'
    position); summarised fetch of the whole issue; original.

## Opened and not used

- https://cs.uwaterloo.ca/~dvogel/gi2026/papers/1076b.pdf : a
  Graphics Interface 2026 paper on question-guided input for building
  interfaces, by the search result's description; the PDF opened but
  the fetch returned compressed bytes and no text, so nothing is
  cited from it.

## Search record

Queries, in order: spec-driven development and a UX step that asks
before proposing; spec-kit clarify and its "Interaction & UX Flow"
category; BMAD's UX design workflow and its steps; agent skills for
interface design that ask first; "AI generated UI generic" with
"distributional convergence" (disconfirming); interface generation
without clarifying questions, studies (disconfirming); Impeccable's
teach command and its questions; the DESIGN.md specification of
Stitch; spec-kit issues on a missing interface step; the
brainstorming skill of superpowers and its visual companion;
Lovable's plan mode, Figma Make's guidelines, v0's instructions;
Kiro's specs, design file and steering files; GSD's UI researcher and
UI-SPEC.md; the steps of BMAD's UX workflow in its repository;
Figma's server and its design-system rules; a paper on
question-guided prompting for interfaces, by an identifier a search
result gave; BMAD's `bmad-ux` skill file, limited to GitHub;
Impeccable's product file in its repository; Claude Design and its
clarifying questions; the practitioner article on vague prompts; the
question-guided paper by its title.

Pages opened, sixteen: sources 1 to 15 and the PDF under Opened and
not used; source 13 was fetched a second time with a narrower prompt,
which is the same page. Six further fetches opened nothing and are
not counted: three guessed paths to BMAD's `bmad-ux` prompt file and
its directory (not found), a registry's copy of that file (gone), a
guessed path to Impeccable's teach reference (not found), and
Figma's documentation page for the design-system-rules skill (not
found).

The disconfirming query: it found the expected direction in one
practitioner evaluation [13], one abstract [14] and two vendors' own
skill files [6], [7], and it found no report that measures an agent
that does not ask against one that does; the phrase about a generic
look that a search summary attributed to [13] was not found in the
page by the fetch. It also found the opposite failure, a workflow
that makes the agent invent by insisting on visuals [15].

The run ended by the opening budget, not by the card's stop rule: the
last queries still returned new material, and three routes (BMAD's
and Impeccable's prompt files, Figma's rules skill) are covered by a
primary description of the tool but not by the prompt file itself.
