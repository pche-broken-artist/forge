---
date: 2026-11-21
project: forge
topic: From a textual description to a visible preview before the build; the routes, their inputs, their cost of change, their stage
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-10-text-to-preview
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 10; no known note named by the card; web sources below
---

# A textual description becomes visible before the build by four routes, and the cheap preview is placed with the definition

<!-- Shape: templates/research.md -->

## In short

Four routes from text to something visible are documented by their
makers, and they differ most in what they need as input. A language
that draws a wireframe takes a text file in its own notation and
redraws it at the cost of one command, in low fidelity only
[1][2][3]. A generator of wireframes or of clickable prototypes takes
a description of any length, a long specification included, and
spends metered credits on every prompt [4][5]. A component library
rendered in isolation takes coded components and so belongs to the
build [6]. Process literature places a cheap preview with the
definition and keeps it apart from the build, and disagrees on how
concrete that preview may be [9][10]. What each route is and needs is
well sourced, from the tools' own documentation; what a change costs
is not: no comparable figure was found, and the two evaluations of
generators are a practitioner test and a case study that calls itself
no controlled experiment [7][8]. The disconfirming query found the
claim it expected, that prototypes have made wireframes needless, as
an opinion piece and as a vendor's account of its own practice,
neither with a measurement [12][13]; the sources that tested
generators place them in early exploration and keep static previews
and written notes beside them [7][8][14]. The unexpected thing: one
method makes its preview at the definition stage of words alone and
argues that a picture at that stage does harm [10].

## Question

Card 10 of the plan, verbatim:

> #### Card 10: From text to something visible
> - **Question:** By which ways does a textual description become a
>   visible preview before the product is built (languages that draw a
>   wireframe from text, generated low-fidelity wireframes, generated
>   clickable prototypes, a component library rendered in isolation):
>   what does each need as input, what does it cost to change and make
>   again, and at which stage do processes place the preview: with the
>   definition or with the build?
> - **Why it matters:** the author must see a proposal to tune it, and
>   a change of the interface must not mean rebuilding the product.
> - **What would answer it:** the tools' own documentation, and
>   process literature on the fidelity of prototypes.
> - **Where to look:** text-to-wireframe languages and diagram tools;
>   tools that render components in isolation; AI prototype
>   generators; practitioner organisations on prototype fidelity;
>   processes that sketch before they build.
> - **Disconfirming query:** "low-fidelity wireframes obsolete", "the
>   prototype is the specification"; expected: a claim that generated
>   prototypes make wireframes needless.
> - **Stop rule:** nothing new from a differently worded query and
>   every route has a primary source; ten to fifteen pages opened.

The frame, in this note's words: a framework carries an idea down a
chain of versioned Markdown documents kept in git, each worked by a
human with an AI agent, and nothing is implemented there. A
description of the user interface in text is wanted as one more
document: proposed by an agent, tuned and seen by a human, handed to
a build stage, and worked again when the interface changes. The
targets are the web, the mobile web, native mobile and the desktop.
One idea is to be tested: a small Markdown definition for every
element of a screen, and a page definition that names which elements
it holds and where they stand. Known items: none, the card names no
known note.

The word "design" in this note means the design of the interface, as
a design tool holds it or a prototype shows it; "design system" means
a component library with its visual identity. The technical design of
spec-driven kits does not occur here.

What the note must beat: the answer anyone gives unasked, that rough
wireframes come early and polished prototypes late, and that AI tools
now make a prototype from a prompt. The note beats it only where it
says, route by route and from the maker's own documentation, what the
route takes as input and what kind of cost a change carries, where a
named process puts the preview, and whether the claim that generated
prototypes end the wireframe has anything behind it.

## Key findings

**F1. Four routes exist, each documented by its maker, and they
differ first in what they need as input.** [consensus that the routes
exist; evidence: the tools' own documentation, one tool opened per
route, two for the first] The table gathers what the findings below
say; a cell marked "inference" is this note's own reading, not a
source's.

| Route | Needs as input | To change and make again | Stage | Sources |
|---|---|---|---|---|
| A language that draws a wireframe from text | A text file in the tool's own notation, written by a person or by a model | Edit the text and run the renderer; a watch mode redraws on save | No process source places it; the definition, by its low fidelity (inference) | [1][2][3] |
| A generated low-fidelity wireframe | A prompt, pasted code, a long specification, a file, a screenshot or a photo of a sketch | A further prompt on selected elements, or editing by hand in the tool; credits per action | Reviews and planning meetings, on the vendor's word; no process source | [4] |
| A generated clickable prototype | A prompt, the more detailed the better; optionally design files, images, the styles of a component library | A further prompt, or editing the preview and the code; credits per prompt; output that varies | Early: ideation, concept exploration, early tests with users | [5][7][8] |
| A component library rendered in isolation | Coded components in a supported framework, and stories that supply properties and mock data | Change the component's code or its story | The build | [6] |

**F2. A language that draws a wireframe from text is the one route
whose input is itself a text file that git can compare and whose
redraw costs a command; it is low fidelity by intent, and the two
opened are an undated page and a small repository.** [single source
per tool; evidence: tool documentation; the judgement of maturity is
this note's] PlantUML's Salt calls itself "a subproject of PlantUML
that may help you to design graphical interface or Website Wireframe
or Page Schematic or Screen Blueprint" and speaks of "emphasizing
functionality over aesthetics" (opening paragraph, under the heading
"Salt (Wireframe)") [1]. A screen is written between `@startsalt` and
`@endsalt`, each widget by punctuation, `[This is my button]` being a
button; the page documents buttons, radio buttons, checkboxes, text
fields, drop lists, grids, trees, tabs, menus and scroll bars (the
list as the fetch summarised it) and says nothing of clicking from
one screen to the next [1]. wiremd "converts Markdown with extended
wireframing syntax into visual HTML mockups", and its README adds
that "Every wireframe is version-controlled, diff-able, and readable
by any LLM" (opening lines) [3]. The command `wiremd login.md --serve
3000 --watch` serves a file, and "the preview live-reloads as you
edit" (Getting started) [3]. The README also names a JSON tree, React
and Tailwind as outputs, seven visual styles with a hand-drawn
"sketch" as the default, an editor extension whose preview follows
the typing, and an import of the JSON into a design tool as editable
frames [3]. It ships a skill for a coding agent and notes that
"Rendering requires CLI execution" [3]: a model can write the text
anywhere, the picture needs the renderer. Whether the same text
always gives the same picture is stated on neither page; that it
does, a renderer being a parser and not a model, is this note's
inference. As to maturity: [1] carries no date and no version; the
repository opened for wiremd is a fork with 6 stars on 2026-11-21,
its README points to breaking changes of the notation in a version
0.4 with a migration script, and its upstream was not opened [3].

**F3. A generator of wireframes or of prototypes takes a description
of any length, spends metered credits on every prompt, and is changed
by further prompting or by hand inside the vendor's tool.** [vendor
claim; evidence: vendor documentation of two products] Balsamiq's
help page: "You can type a prompt, paste code, paste a long spec, or
upload a file directly into the chat" (introduction), and "The AI
will return an editable wireframe made up of Balsamiq UI elements"
(Generate a single wireframe from text) [4]. A screenshot or "a photo
of a hand-drawn sketch" is converted the same way [4]. A change is
made by selecting elements and typing an instruction, a feature that
"allows you to make quick changes without rebuilding from scratch"
(Edit existing wireframes with AI), and "Balsamiq AI actions use
credits from your Space's shared monthly pool" (note in the
introduction) [4]. Figma Make's help page: "With Figma Make, you can
use the chat interface to create functional prototypes, web apps,
interactive UI, and more" (opening) [5]. A prompt may carry attached
designs of the interface, pasted frames and images, the styles of a
library of the design tool and context from connected tools; the
result is changed "by continuing the conversation, as well as edit
the preview and code directly" (opening) [5]. "AI credits in Figma
Make are consumed each time you send a prompt", the amount varying
with the model, the task and the context (Best practices, Optimizing
usage) [5]. Neither page gives a price per action. What is made lives
in the vendor's tool and not in the text it was made from; that the
description and the preview can therefore drift apart is this note's
inference, stated by neither page.

**F4. Tested by a practitioner organisation, generators follow the
detail of the prompt, give output that varies, and are placed early
in the process, not as something to ship.** [emerging; evidence:
practitioner evaluation by heuristic review, one real project, no
controlled study; youngest date 2026-08-19, the page's last review]
NN/g redesigned one page of its own with three kinds of tool, those
that make static wireframes or mock-ups, coding tools that make
interactive prototypes, and general chatbots, at three levels of
prompt: a broad text, a detailed text naming components, design
language and interaction states, and text with design artefacts
[7]. "AI prototyping tools follow general directions but lack the
judgment and nuance of an experienced designer" (summary line) [7].
"longer prompts with clear, detailed design requirements consistently
yield better results", and with attachments "The higher the fidelity
of the attached file, the more accurately the design was translated"
[7]. Under a broad prompt the outputs "varied widely", since "general
prompts leave room for AI tools to make assumptions about the design
requirements and fill in the gaps" [7]. The placement is explicit:
"best suited for ideation, concept exploration, and early-phase
prototype testing, rather than later stages" (When to Use AI
Prototyping), and the results "still require validation, iteration,
and hands-on refinement before anything ships" [7]. That a detailed
textual description of an interface is, by this test, the input a
generator serves best is this note's inference from [7], not a
sentence of it.

**F5. A generated clickable prototype moves the test of a complex
interaction from after the build to before it; for a simpler
interface a static preview still answers.** [single source; evidence:
a sequential case study of one project, by its own word not a
controlled experiment; dated 2026-09-11] In the case NN/g reports, a
university team first drew low-fidelity wireframes by hand in a
design tool and "couldn't observe how people would interact with the
filters because the prototype was static"; it then had two generators
build an interactive prototype of a filter over data with 27
attributes per event [8]. The article's claim on cost: "AI tools
bring speed to the design process, enabling designers to create a
realistic working prototype in a day" (Interactive Prototypes, Fast)
[8]. On placement: before such tools most teams would test a simple
prototype "and wait until developers built the product to see how
users interacted with it" [8]. On the limit of the claim: "For less
complex interfaces, static prototypes are still useful for answering
many research questions" (before the contents list), and "This was a
sequential case study focused on a single project rather than a
controlled experiment" [8]. On the risk: "AI-generated prototypes may
look complete while introducing all sorts of assumptions and
inaccuracies", and "The danger is that its polish might cause people
to stop working to improve it" [8]. That the prompt carried design
requirements and a synthetic data file, and that a first output needs
going back and forth, rests on the fetch's summary of [8].

**F6. A component library rendered in isolation shows what is built,
not what is described: it needs coded components, so its preview sits
with the build.** [consensus within its community; evidence: the
tool's own documentation, version label 10.6 on 2026-11-21] Storybook
"is packaged as a small, development-only, workshop that lives
alongside your app" and renders a component so that "You can render a
specific variation in isolation by passing in props, mocking data, or
faking events" (before the heading on stories) [6]. A saved variation
is a story: "Stories are a declarative syntax for supplying props and
mock data to simulate component variations" [6]. The page sets the
route against a picture: "Stories show how UIs actually work, not
just a picture of how they're supposed to work", and "Publish
Storybook to get sign-off from teammates" (Share how the UI actually
works) [6]. The judgement by a human is therefore made here on the
built component. That a project with a component library already
built could preview a new page at the definition stage by composing
existing components is this note's inference; the page does not say
it.

**F7. Process literature places a cheap preview with the definition
and keeps it apart from the build; it disagrees on how concrete that
preview may be.** [consensus on the placement, contested on the
fidelity; evidence: a government service manual, a published product
method, a practitioner article] The service manual of the British
government: "You must use prototypes in the alpha phase of your
service to explore and test different approaches to the design of the
service", and "Continue to use prototypes in the beta and live stages
of your service to explore potential new features or improvements"
(When to use prototypes) [9]. The kind is left open, "from a quick
pen and paper sketch to a code prototype that works like a fully
interactive website", and "You should use the prototype that best
meets your needs at the time" (Types of prototype) [9]. The preview
is kept apart from the product: "The code in a prototype does not
need to meet the same standards as production code", and "Do not just
copy prototype code into production" [9]. Shape Up places its preview
in shaping, before a team is given the work, and bars the concrete:
"If we start with wireframes or specific visual layouts, we'll get
stuck on unnecessary details and we won't be able to explore as
broadly as we need to" (Move at the right speed) [10]. Its two means
are the breadboard, of which it says "We'll use words for everything
instead of pictures", and the fat marker sketch, "a sketch made with
such broad strokes that adding detail is difficult or impossible"
[10]. The reason given is the effect on those who come after: "any
specific mockups are going to bias what other people do after you",
while the two means "give room to designers in subsequent phases of
the project"; and "This isn't a spec" (Room for designers) [10]. The
two sources conflict on fidelity at the definition: [9] holds that
"Code prototypes are better for user research because they're more
realistic", [10] that a wireframe is already too much. They speak of
different acts, a test with users in [9] and the setting of bounds
for a team in [10]; that this explains the conflict is this note's
reading. A third source takes the single dial apart: "The fidelity of
the prototype refers to how closely it matches the look-and-feel of
the final system", and it varies separately in interactivity, visuals
and content [11]. On the cost of change it says that with a static
preview a designer can "erase or change part of design between test
sessions (or during a session) without worrying about linking the new
page in the interactive prototype", while "With interactive
prototypes, the designer must set a response for each possible user
action before the test happens" [11]. This is the cost that [8] says
generators now cut.

**F8. The disconfirming query found the claim it expected, as an
opinion and as a vendor's account of its own practice, with no
measurement behind either; the sources that tested generators do not
carry it.** [contested; evidence: an opinion piece and a vendor claim
against practitioner evaluation and practitioner research; youngest
date 2026-09-11] The claim in its plainest form: "Wireframes are
dead, and prototypes killed them", and "AI is the final nail in the
coffin" (opening, and the section on AI) [12]. The piece names tools
and companies and gives no data, as the fetch read it, and it keeps
the low-fidelity prototype, which it says serves the old purpose of
the wireframe better [12]. The second form comes from a vendor of a
design tool about its own product managers: "prototypes have started
to replace Product Requirements Documents (PRDs) altogether"
(introduction) [13]. Its evidence is the practice of five of its own
employees with its own generator; its body does not speak of
wireframes; and its own sentence on the handover is "The spec to our
engineering teams today is often a Figma Make file plus designs"
[13], which is a prototype with designs of the interface beside it,
not a prototype alone. Against the claim: [8] keeps the static
preview for less complex interfaces, [7] keeps generators to the
early phases, and NN/g's research with practitioners describes notes
that are "a few lines of text written next to a prototype and
describing details that may be ambiguous in the design" and says a
good one "Describes the prototype, rather than replacing it" [14].
The same source holds the reverse as well, that "A text description
of a design will be more difficult to understand than a wireframe"
[14]: neither text nor picture stands alone there. What the claim has
on its side is cost: a clickable prototype "in a day" [8] removes
much of the old price of interactivity [11]. What it does not answer
is the argument from judgement, the bias of a concrete mock-up [10]
and the polish that stops improvement [8].

## Unexpected

The card assumes that a preview is a picture; [10] has a preview at
the definition stage that is made of words alone, the breadboard, of
three things: places a user can navigate to, affordances the user can
act on, and lines that connect them. It is still a preview, a thing
read to judge a flow before anything is built, and its authors argue
that a picture at that stage narrows what follows. The question is
answered above as put. The lead for this project: a page definition
that names which elements a page holds is close to a breadboard's
places and affordances, so a first preview may be a reading of the
description itself and not a drawing; this nearness is the note's
own observation.

The site of one text-to-wireframe language presents the notation as
a layer of specification, not as a drawing tool: "Write wireframes in
your PRD. Your PM writes it, your LLM reads it" [2], with a chain
drawn from idea through the notation and a design tool to a coding
agent. There the wireframe text stands inside the requirements
document, not in a document of its own. The lead: whether a block
that draws belongs inside the description or beside it is a choice
the project will meet.

A generator has put a stage of text before its own preview: a mode
that makes "a structured plan to review and refine before any code is
written" [5]. The lead: the route that seems furthest from a written
description is growing one of its own.

The first query returned the names of further small languages built
so that a model writes the wireframe text and a renderer draws it
(Wireloom, wirecannon, Wrafjs, Wire-DSL, WireScript, Boceto), and the
last query added wireframes kept as plain HTML files in a repository.
None was opened; nothing is claimed of them beyond that the result
lists show a crop of such projects.

## Not found

- A comparable figure for the cost of one change by each route, in
  time, money or credits. The two vendor pages say that credits are
  consumed and give no number [4][5]; the one figure of time, "in a
  day", is an article's claim for a first prototype, not a measured
  cost of a change [8]. Looked for in the pages opened.
- A controlled comparison of the routes by the quality of the
  decisions made on them. The one comparison found is a sequential
  case study that says so itself [8]. Looked for with the query on
  evaluations of generators.
- A process source that names a text-to-wireframe language and gives
  it a stage. The tools' pages say what they draw, not when [1][3].
- Evidence of adoption or upkeep of the text-to-wireframe languages:
  [1] is undated, [3] is a fork with 6 stars, the upstream repository
  was not opened.
- Whether edits made by hand in a generated wireframe or prototype
  survive a new generation from a changed text. Stated on neither
  vendor page [4][5].
- A preview from text for native mobile or the desktop. [1] draws
  generic widgets and [3] renders HTML; the pages opened say nothing
  of native targets, and the platforms were not searched, being
  another card's.
- A standard on the fidelity of prototypes. None surfaced in the
  query on fidelity; none was searched for by name.
- Whether the best-known text-to-diagram tool draws wireframes. Not
  checked; [3] calls itself "Mermaid for wireframes", which suggests
  a gap and proves nothing.

## Options

1. **A text notation that draws, inside or beside the description.**
   The preview is redrawn by a command from a file in git, nothing is
   metered, and a change shows as a difference of text [3]. Against
   it: low fidelity only and, in [1], no path from screen to screen;
   the tools found are small and one has just broken its notation
   [3]; a second notation stands beside the element definitions, and
   the question which of the two is the description must be settled.
2. **A generated low-fidelity wireframe made from the description.**
   The generator takes "a long spec" as it is and returns something a
   human can edit by hand [4]. Against it: the result lives in the
   vendor's tool, credits are spent per action, and nothing found
   says how a later change of the text reaches a wireframe already
   edited.
3. **A generated clickable prototype made from the description.** The
   only route that shows a complex interaction before the build [8],
   and the detailed description is the input it serves best [7].
   Against it: output that varies [7], credits per prompt [5], the
   polish that ends improvement [8], and code that tempts reuse where
   [9] says not to copy it.
4. **A component library rendered in isolation.** The truest preview,
   since it is the built thing [6]. Against it: it needs code, so it
   comes with the build, or presupposes a library built before.
5. **A preview in words alone at the definition, pictures left to
   those who build.** The cheapest, and the one [10] argues for.
   Against it: the card's own reason, that the author must see a
   proposal to tune it, and [14], which finds text harder to read
   than a wireframe.
6. **Routes by stage.** A cheap redraw from text at every round of
   the definition, a generated clickable prototype on demand where an
   interaction is too complex to judge on a still picture, component
   isolation at the build. Against it: two or three mechanisms to
   keep, and the least mature of them at the centre.

## Relevance to this project

The recommendation, this note's own inference from the findings: keep
the description as the text in git and treat every preview as
something made from it, never as its replacement; make the everyday
preview the cheapest one to make again; and reach for a generated
clickable prototype only where a still picture cannot answer. It
rests on three things the sources agree on from different sides: that
a prototype is kept apart from the product [9], that a written note
describes a prototype and does not replace it while text alone is
hard to read [14], and that a generated prototype belongs to early
exploration and can look more finished than it is [7][8]. Of the
routes found, only the text notation has the property the card asks
for, a change that does not mean a rebuild, on its maker's own word
[3]; the evidence for it is the weakest, tool pages alone and small
projects, so it is a direction to examine, not a tool to adopt. It is
chosen against making the generated prototype the specification
[13], which no source that tested generators supports, and against
leaving the preview to the build [6], which would put the author's
judgement after the cost.

Two things stay open and are the principal's to decide, not this
note's. How concrete the preview at the definition should be: [9]
and [10] disagree, and the author here is both a single person
working end to end and a specialist in a company, for whom the
answer may differ. And whether the notation that draws is the
description or a companion to it: the idea under test, a definition
per element and a page that places them, is nearer to the words of a
breadboard [10] than to a drawing language, and a drawing could be
made from it by any of the routes above; that it could is an
inference, tested by no source here.

Consult when: the way a proposal of the interface is shown to its
author is chosen; a generated prototype is proposed as the thing
handed to the build in place of text; the stage of the preview and
whether it is kept or thrown away is decided; someone argues that
wireframes are obsolete; a notation that draws is weighed for use
inside the description.

## Sources

Every page was read through a fetch that returns a small model's
answer about the page, a summarised fetch; the passages quoted in
this note were then matched word for word against the raw text of the
same page in the same run. Quotation marks, apostrophes and dashes
stand here in their plain forms where a page has typographic ones.
What rests on the fetch's summary alone is said so in the finding.

1. "Salt (Wireframe)", PlantUML project. Undated: no date and no
   version on the page.
   https://plantuml.com/salt
   Primary, the tool's own documentation. Summarised fetch of the
   whole page, quotes matched against the raw text. Original.
2. "wiremd", project site of the wiremd language. Undated.
   https://akonan.github.io/wiremd/
   Primary, the tool's own site. Summarised fetch of the landing
   page, which is short; quotes matched against the raw text.
   Original. The site's repository link leads to [3].
3. "wiremd", README of the repository teezeit/wiremd on GitHub, a
   fork of akonan/wiremd by the page's own label. Undated: no release
   and no commit date read; 6 stars on 2026-11-21.
   https://github.com/teezeit/wiremd
   Primary, the tool's own documentation. Summarised fetch of the
   README, quotes and commands matched against the raw text. A fork;
   the upstream repository was not opened.
4. "Wireframing with Balsamiq AI", Balsamiq help centre. Undated.
   https://balsamiq.com/support/creating-and-editing/wireframing/
   Primary, a vendor's documentation of its own product. Summarised
   fetch of the whole page, quotes matched against the raw text.
   Original. Reached by redirect from the address the search gave.
5. "Create a Figma Make file", Figma help centre. Undated.
   https://help.figma.com/hc/en-us/articles/31304485164695-Create-a-Figma-Make-file
   Primary, a vendor's documentation of its own product. Summarised
   fetch of the whole page, quotes matched against the raw text.
   Original.
6. "Why Storybook?", Storybook documentation. Undated; version label
   10.6 on the page on 2026-11-21.
   https://storybook.js.org/docs/get-started/why-storybook
   Primary, the tool's own documentation. Summarised fetch of the
   whole page, quotes matched against the raw text. Original.
7. "Good from Afar, But Far from Good: AI Prototyping in Real Design
   Contexts", Huei-Hsin Wang and Megan Brown, Nielsen Norman Group.
   October 24, 2025, last reviewed August 19, 2026 (byline).
   https://www.nngroup.com/articles/ai-prototyping/
   Primary for its own evaluation; the publisher sells training and
   consulting in user experience. Summarised fetch of the whole
   article, quotes matched against the raw text. Original.
8. "Test Complex Interactions Earlier with AI Prototyping", Megan
   Chan, Nielsen Norman Group. September 11, 2026 (byline).
   https://www.nngroup.com/articles/test-earlier-with-ai/
   Secondary for the university case it reports, primary for its own
   advice. Summarised fetch of the whole article, quotes matched
   against the raw text. Original.
9. "Making prototypes", Service Manual, GOV.UK. Published 18 October
   2016 (the page's own date line).
   https://www.gov.uk/service-manual/design/making-prototypes
   Primary, a government's guidance for its own services. Summarised
   fetch of the whole page, quotes matched against the raw text.
   Original.
10. "Find the Elements", chapter 4 of "Shape Up: Stop Running in
    Circles and Ship Work that Matters", Ryan Singer, Basecamp.
    Undated on the page.
    https://basecamp.com/shapeup/1.3-chapter-04
    Primary, a method published by the company that uses it and sells
    a product built by it. Summarised fetch of the whole chapter,
    quotes matched against the raw text. Original.
11. "UX Prototypes: Low Fidelity vs. High Fidelity", Kara Pernice,
    Nielsen Norman Group. December 18, 2016 (byline).
    https://www.nngroup.com/articles/ux-prototype-hi-lo-fidelity/
    Secondary, a practitioner article. Summarised fetch of the whole
    article, quotes matched against the raw text. Original.
12. "From Wireframes to Prototypes: Why Designers Need to Grow Up",
    Alex Harper, Web Designer Depot. November 24, 2025 (byline).
    https://webdesignerdepot.com/from-wireframes-to-prototypes-why-designers-need-to-grow-up/
    Tertiary as evidence: an opinion piece of a trade blog with no
    data; cited only as the claim the disconfirming query looked for.
    Summarised fetch of the whole article, quotes matched against the
    raw text. Original.
13. "Prototypes Are the New PRDs", Emma Webster, Figma blog. December
    15, 2025 (byline).
    https://www.figma.com/blog/prototypes-are-the-new-prds/
    Primary only for the vendor's own claim: a vendor's blog on its
    own market, cited as the first publisher of the claim and never
    for its truth. Summarised fetch of the whole article, quotes
    matched against the raw text. Original.
14. "Use Good Prototype Specifications to Empower Team
    Collaboration", Leeloo Tang and Feifei Liu, Nielsen Norman Group.
    June 5, 2022 (byline).
    https://www.nngroup.com/articles/prototype-specifications/
    Primary for its own study with practitioners. Summarised fetch of
    the whole article, quotes matched against the raw text. Original.

## Opened and not used

- The Storybook page of [6] under the shorter path the search gave,
  without the segment "get-started": answered 404; superseded by [6].

## Search record

Queries, in order:

1. text to wireframe language, Markdown, a notation that renders
2. prototype fidelity, low and high, when to use
3. "low-fidelity wireframes" obsolete, AI prototypes (disconfirming)
4. "the prototype is the specification" (disconfirming)
5. PlantUML Salt wireframe syntax
6. Storybook documentation, components "in isolation", why
7. Figma Make, prompt to prototype, help centre
8. Shape Up, breadboarding, fat marker sketches, wireframes too
   concrete
9. GOV.UK service manual, making prototypes, alpha
10. Figma First Draft, wireframes from a prompt
11. NN/g, AI prototyping tools, evaluation, 2025
12. Balsamiq AI, wireframe from text, documentation
13. NN/g, prototypes of low and high fidelity
14. "prototypes are the new PRDs", wireframes skipped (disconfirming,
    reworded)
15. wireframe as code, plain text, git diff, a model generates, a
    preview before coding (reworded)

Pages opened, fifteen openings, in order: [1]; [2]; the Storybook
page that answered 404; [7]; [6]; [3]; [10]; [9]; [4]; [5]; [8];
[12]; [13]; [14]; [11]. After the fifteenth no new page was opened;
the fourteen cited pages were fetched again by a script, for their
status and for matching the quoted passages against the raw text.

What the disconfirming query found: the expected claim, twice. An
opinion piece says wireframes are dead and AI the last blow, with no
data [12]; a vendor says prototypes have started to replace
requirements documents altogether, on the practice of its own staff
with its own product [13]. Neither measures anything, [13] does not
speak of wireframes, and both keep something beside the prototype: a
low-fidelity prototype in [12], designs of the interface in [13].
The reworded query returned further pieces of the same kind in its
result list, vendor and advocacy posts, none opened.

Why the run ended: the opening budget, fifteen openings. Of the
card's stop rule, every route had a primary source by then, and the
last reworded query brought names of the same kind as the first, but
also one variant not yet seen, wireframes kept as plain HTML files,
which the budget left unopened.
