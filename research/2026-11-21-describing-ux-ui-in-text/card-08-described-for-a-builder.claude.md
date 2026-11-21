---
date: 2026-11-21
project: forge
topic: descriptions of a user interface written for an agent that builds
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-08-described-for-a-builder
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 8; no known note named by the card; web sources below
---

# How the AI coding and design tools of 2025 and 2026 want a user interface described so that an agent builds it

<!-- Shape: templates/research.md -->

## In short

The makers' own documents, as read in this run, prescribe no single
description of an interface for an agent that builds. They prescribe
pieces that live in different files and mean different things by
"design". The design file of the two spec-driven kits read is technical
design beside a functional specification, with no place for the
interface [1][2]. The file called DESIGN.md is the visual identity,
tokens with prose around them, and knows no screen [3]. The makers'
skills and prompts for interface work carry taste rules and a process
and take the description as given [4][5]. Servers and registries hand
the agent structured data drawn from a design tool or from code, with a
screenshot beside it [6][7][8]. One artefact read, an older template of
a third kit, gives a screen and a component fixed fields in Markdown
and sends the picture to a design tool [9]. The disconfirming query
held in part: makers tell the user to hand the agent a picture of the
layout instead of describing it and to check the result against a
screenshot [6][10], while a measured study found that a picture
improves where things sit far more than whether the application works
[11]. How sure: what each artefact contains is read from the maker's
own page, through a summarising fetch with the quotes checked against
the raw text; what works rests on three practitioner reports
[12][13][14] and that one preprint, and is thin. Unexpected: in the
kits "design" is not about the interface at all, and two tools give
unrelated files the same name [1][3].

## Question

The frame, shortened from the plan: a framework carries an idea down a
chain of versioned Markdown documents, each worked by a human with an
AI agent; a description of the user interface in text is wanted as one
more document, proposed by an agent, tuned and seen by a human, and
handed to a build stage that is a human developer, an AI coding agent
or both. The card, verbatim:

**Card 8: Descriptions written for an agent that builds**

- **Question:** How do the AI coding and design tools of 2025 and 2026
  want a user interface described so that an agent builds it (the
  design file of spec-driven kits, a design file for agents, sections
  of agent instruction files, rules files, skills and prompts for
  interface work, servers that give an agent a design system,
  component documentation as an agent's context): which content and
  shape do their makers prescribe, and what do practitioners report
  works or fails?
- **Why it matters:** the build stage is an agent at least in part, and
  the description must be what an agent builds from.
- **What would answer it:** the tools' own documentation, and dated
  reports by practitioners.
- **Where to look:** the documentation of spec-driven development kits,
  of interface generators and of design tools' AI features; the makers'
  guidance on front-end work with coding agents; component registries
  and their agent integrations. Search words from card 1: "spec-driven
  development", "spec-first", "spec-anchored", "spec-as-source",
  "constitution", "steering files", "EARS", "DESIGN.md". Primary
  artefacts in public repositories (schemas, component and page files,
  agents' rules and prompt files, the schemas of servers for design
  tools, issue trackers) before commentary about them.
- **Disconfirming query:** "spec-driven development fails for UI",
  "screenshot beats specification"; expected: reports that a picture or
  a prototype steers an agent better than text.
- **Stop rule:** nothing new from a differently worded query and every
  route has a primary source; ten to fifteen pages opened.

What the note must beat: the assumption a reader brings without the
research, that each tool named in the card holds a ready shape for
describing an interface and that one of them can be borrowed. A list
of tool names with their slogans would not beat it. The note has to
say, route by route and from the maker's own artefact, what content
and what shape is prescribed and in which of the three senses of
"design", and to set dated reports of use against it.

## Key findings

Every source but [10] was read through a summarising fetch. Words in
quotation marks were afterwards found in the raw text of the page they
are cited from; whatever else is reported from those pages rests on
the summary and says "per the summary" where it carries weight.
"Design" is named by its sense each time: the design of the interface
held in a design tool, the technical design between requirements and
tasks, or the visual identity of a design system.

F1. **The design file of the two spec-driven kits read is technical
design, and their specification has no place for the interface.**
[consensus of the two kits read; vendor report: the makers' own
documentation and template] In Kiro a feature spec names
`requirements.md` and `design.md`; the second "documents technical
architecture, sequence diagrams, and implementation considerations",
and the design-first variant starts from "technical design
(architecture or low-level design)" [1]. Requirements are written in
EARS, "WHEN [condition/event] THE SYSTEM SHALL [expected behavior]"
[1]. The page, updated August 4, 2026, has nothing on screens, mockups
or visual design (per the summary); an interface enters only as a
behaviour inside a requirement. A practitioner's screenshot of a Kiro
design document shows, by its alt text, "a component architecture
diagram, and then collapsed sections titled Data Flow, Data Models,
Error Handling, Testing Strategy, Implementation Approach, Migration
Strategy" [12]. Spec Kit's specification template has the sections
User Scenarios & Testing, Requirements (Functional Requirements, Key
Entities), Success Criteria and Assumptions, and none for the
interface; its success criteria "must be technology-agnostic and
measurable", its scenarios are Given/When/Then, and a gap is marked
`[NEEDS CLARIFICATION: ...]` [2]. Of Spec Kit only this template was
read, not its plan template or its commands.

F2. **A third kit does prescribe an interface document in Markdown,
with fixed fields for a screen and for a component, and it sends the
picture to a design tool.** [single source; vendor report: a template
in the maker's published package, an older major version] The BMAD
method's package 4.35.0 carries a template named "UI/UX Specification"
that writes `docs/front-end-spec.md` [9]. Per the summary its sections
run: introduction with UX goals (personas, usability goals, design
principles), information architecture ("Site Map / Screen Inventory",
navigation structure), user flows, wireframes and mockups ("Key Screen
Layouts"), component library ("Core Components"), branding and style
guide, "Accessibility Requirements", "Responsiveness Strategy",
animation, performance, next steps [9]. A screen has four fields:
Purpose, "Key Elements", "Interaction Notes", "Design File Reference".
A component has four: Purpose, "Variants", "States", "Usage
Guidelines" [9]. The site map and the flows are Mermaid diagrams, and
the sections are filled by elicitation with the user [9]. Two
instructions set the boundary of the text: "Clarify where detailed
visual designs will be created (Figma, Sketch, etc.) and how to
reference them", and "detailed technical specs belong in
front-end-architecture" [9]. The text holds purpose, inventory, flows,
the elements of a screen and the states of a component; the design of
the interface stays in a design tool and is linked. Newer major
versions of the kit were not read.

F3. **The file made for agents under the name DESIGN.md describes the
visual identity, as tokens with prose around them, and has no notion
of a screen.** [single source; vendor report: the format's own
specification, version "alpha"] Google Labs' specification says: "The
tokens are the normative values; the prose provides context for how to
apply them." [3] Tokens are YAML, in front matter or in fenced blocks,
in the groups `colors`, `typography`, `rounded`, `spacing`, `motion`
and `components` [3]. The body has a fixed section order: Overview,
Colors, Typography, Layout, Elevation & Depth, Shapes, Motion &
Micro-interaction, Voice & Content Strategy, Components, Do's and
Don'ts (the first six checked in the raw text, the rest per the
summary) [3]. Components are style entries for atoms such as buttons
and inputs, a state such as hover being a separate key (per the
summary), and the specification says of itself: "The components
specification is actively evolving." [3] A reader of the file meets
unknown content with "Preserve; do not error" [3]. The tokens convert
to and from "`tokens.json`, Figma variables, and Tailwind theme
configs" [3]. The word "screens" does not occur in the specification
and "page" occurs only in passing (checked in the raw text): which
elements stand on which screen is outside the format. "Design" here is
the visual identity.

F4. **The makers' skills and prompts for interface work carry taste
rules and a process, not a format of description; the description is
taken as given.** [consensus of the two vendors read; vendor report]
Anthropic's skill for front-end work describes itself as "Guidance for
distinctive, intentional visual design when building new UI or
reshaping an existing one." [4] It has the agent plan before building,
"create a compact token system with color, type, layout, and
principles", the palette being four to six named colour values; hold a
floor, "responsive down to mobile, visible keyboard focus, reduced
motion respected"; and criticise its own work, "taking screenshots to
review if your environment supports it" [4]. It names the looks a
model falls into as "defaults rather than choices" [4]. It works from
"the client's design brief" and does not say what a brief holds; the
words "design system" do not occur in the file (checked in the raw
text). OpenAI publishes a prompt to paste, whose page says "These
instructions target GPT-5.5" [5]. Its content is standing rules, for
example "Cards are kept at 8px border radius or less unless the
existing design system requires otherwise."; they yield "If working
with an existing design or given a design framework in context"; and
they leave the states to the model: "You build feature-complete
controls, states, and views that a target user would naturally expect
from the application." [5] One of its rules, for three-dimensional
scenes, ends in a check "with Playwright screenshots" [5]. Both makers
treat the generic look and the missing state as the model's default
failure and answer it with rules, not with a prescribed description.

F5. **A design tool's server gives the agent structured context and a
screenshot together, and its maker asks for structure in the design
file and for rules in the agent's instruction file.** [vendor claim;
vendor report, one vendor] Figma's guide to its MCP server prescribes
an order of work: "Run get_design_context first to fetch the
structured representation for the exact node(s).", then "Run
get_screenshot for a visual reference of the node variant being
implemented.", and "Only after you have both get_design_context and
get_screenshot, download any assets needed and start implementation."
[6] What the server returns is to be read as a description, not as
code: "Treat the Figma MCP output (React + Tailwind) as a
representation of design and behavior, not as final code style." [6]
The rules are meant for the agent's instruction or rules file, "in
whatever format your MCP client uses for instruction files", and their
content is reuse and tokens: "Reuse existing components (e.g.,
buttons, inputs, typography, icon wrappers) instead of duplicating
functionality.", "Avoid hardcoded values, use design tokens from Figma
where available", and at the end "Validate the final UI against the
Figma screenshot for both look and behavior." [6] The description
itself is expected inside the design file: components for what is
reused, components linked to code, variables for spacing, colour,
radius and type, layers named by meaning, auto layout for responsive
intent, and annotations "to convey design intent that's hard to
capture from visuals alone" [6]. The stated limit is size: "Large
selections can slow the tools down, cause errors, or result in
incomplete responses" [6]. "Design" here is the design of the
interface held in a design tool.

F6. **Component documentation for agents is prescribed as structured
data generated from code, the authored description being the part a
human adds.** [emerging; vendor report, two vendors, one in preview]
Storybook generates "JSON objects that describe the contents of your
Storybook in a concise, structured way": a components manifest from
"static analysis of the CSF files" and the types of the props, and a
docs manifest from the MDX pages [7]. An entry carries, per the
summary, the component's id, name and path, its import, its
description, its props with type, default and description, and its
stories as usage snippets [7]. The author's part is prose in the code:
"We highly recommend adding JSDoc comments to your components and
their props", and a tag decides what enters the manifest [7]. The
feature is a preview and its schema "not yet stable" [7]. The MCP
server of shadcn/ui "works out of the box with any shadcn-compatible
registry", and what its maker asks of a registry's author is four
things: "Add concise, informative descriptions that help AI assistants
understand what a registry item is for", accurate dependencies,
declared dependencies between items, consistent names [8]. Its example
of use composes a page from named items: "Create a landing page using
items from the acme registry" [8].

F7. **A maker of a coding agent tells users to hand over a picture
instead of describing it, to say the scope in words, and to keep the
standing instruction file short.** [vendor claim; vendor report, one
vendor, undated] The best-practice page of Claude Code says "If you
already have the thing Claude needs, hand it over instead of
describing it", and lists "An image: paste the screenshot of the
design or the error into the prompt." [10] Its example of a prompt for
an interface leaves the layout to the picture and puts in words what
the picture does not show: "build the settings page from the mockup.
be ambitious: empty and error states, the save flow wired up, keyboard
navigation, not just the layout" [10]. Among the checks an agent can
run it lists "A browser screenshot next to the mockup" [10]. For work
not yet thought through it has the agent interview the user into a
specification file and build from it in a fresh session, "so the build
begins with a clean context and a written definition of done" [10].
Of the standing instruction file it says "every line in it takes a
little of Claude's attention on every task", and it lists "Describe
your architecture and file layout" among advice to drop: "Claude reads
the repo itself. Only write down what isn't in there." [10] The page
says nowhere how an interface is described in text.

F8. **Practitioners report that long specifications are followed
incompletely and are tedious to review, and that for components
structured data with deterministic scripts holds better than
inference.** [contested; practitioner claims, three reports, none
controlled] A consultant who tried three spec-driven tools (15 October
2025) names three levels, the first being spec-first: "A well
thought-out spec is written first, and then used in the AI-assisted
development workflow for the task at hand." [12] Of her use she writes
"I frequently saw the agent ultimately not follow all the
instructions", that she would "rather review code than all these
markdown files", that for a small task the workflow was "like using a
sledgehammer to crack a nut", and "I frequently got confused when to
stay on the functional level, and when it was time to add technical
details" [12]. Her one task with an interface, a modal summarising
data of an existing dashboard, is her example of a workflow too heavy
for its size; she says nothing of interfaces as such [12]. A
design-systems practitioner (14 August 2026), who makes the tooling he
reports on, describes component specifications as structured data
generated from the design tool: "API declares component names, props
and elements, serving as the exposed surface to configure and override
it", with variants as layered rules [13]. What the design tool does
not hold is written by hand in Markdown beside it: "Designers I work
with don't use Figma to express behaviors or accessibility." [13] He
turns specifications into code and back by script, since "inference
comes with costs and risks" and "Specs data is layered and
complicated, and imprecision and loss through inference is
inevitable"; the code so generated "isn't intended for production"
[13]. A developer's report (1 April 2026) of a front-end redesign run
through a spec-driven workflow: "The new front-end looked almost
identical to the original"; a plain instruction file was faster and
its result "still wasn't perfect" [14]. Tool and model changed between
his attempts and no picture was given in any of them (per the
summary), so the report compares weights of process, not text against
a picture.

F9. **A measured study found that a picture added to text improves
where things sit far more than whether the application works.**
[single source; controlled study, a preprint dated 11 June 2026] A
benchmark of coding agents building multi-page web applications (128
pages; four models in two harnesses and underspecified text prompts,
per the summary) compared a text prompt alone (C0) with text and a
snapshot of the site (C1, C2) and with text, snapshot and the design
tool's data as JSON (C3, C4); C1 and C3 pin the technology, the others
leave it to the agent [11]. Its table of results, read in the raw
text:

| Condition | Localisation | Behaviour | Combined |
|---|---|---|---|
| C0: text | 0.489 | 0.315 | 0.242 |
| C1: text, snapshot, pinned stack | 0.577 | 0.305 | 0.229 |
| C2: text, snapshot | 0.507 | 0.322 | 0.264 |
| C3: text, snapshot, design data, pinned stack | 0.615 | 0.325 | 0.236 |
| C4: text, snapshot, design data | 0.600 | 0.329 | 0.261 |

Placement moves with the richer input, from 0.489 to 0.615 at most;
behaviour moves from 0.315 to 0.329 at most. The authors: "visual
fidelity and functional correctness are partially decoupled across
both input conditions and agents", and "structural input consistently
improves grounding, but its functional payoff requires implementation
flexibility" [11]. They caution that "a high CLIP score does not imply
pixel- or design-system-faithful output" [11]. No condition holds a
detailed textual description of the interface, so the study does not
say that a picture beats a specification; it says what a picture and
design data add to a short text.

## Unexpected

The card assumes that the design file of spec-driven kits is a place
where an interface is described; [1] and [2] say it is not. In those
kits "design" is the technical design, and the interface has no file
of its own. The question is still answered as put (F1, F2).

One file name carries two unrelated meanings: Kiro's `design.md` is
the technical design of a feature [1], DESIGN.md is the visual
identity of a product [3], and the names differ by case alone. A
project that takes either, or adds a third document called "design"
for the interface, inherits the clash.

The makers divide the work between picture and words, and say so. The
layout goes by picture [6][10]; the words are asked for what a picture
hides: "empty and error states, the save flow wired up, keyboard
navigation" [10], "design intent that's hard to capture from visuals
alone" [6], and behaviours and accessibility that the design tool does
not hold [13]. A textual description could be scoped to exactly that
remainder; this is a lead, not a conclusion.

A practitioner sets spec-as-source beside model-driven development,
which she used: her figure, recreated from memory, shows a parseable
language in which a screen "Write Message" instantiates an
"InputScreen", and her judgement is that the approach never took off
for business applications [12]. It is a lead for the cards on formal
languages and on failures.

By a maker's own account the standing instruction file is a poor home
for a long description: each of its lines costs attention on every
task, and rules scoped to a path and skills loaded on demand are
offered for anything specific [10]. Where a description of the
interface is put for the builder is therefore a question of its own.

## Not found

- A maker's documentation that prescribes how one screen is described
  in text for an agent that builds: not in the kits, the file for
  agents, the skills, the prompts or the servers read. [9] is the one
  artefact with fields for a screen.
- A dated report by a practitioner that sets a textual description of
  an interface against a picture on the same task with the same agent:
  none in the result lists of the two disconfirming queries. [14] is
  uncontrolled and used no picture.
- The documentation of interface generators on what a project's
  knowledge file or design system should contain: seen in a result
  list, not opened, the openings being spent.
- The design tool's own documentation page for the tool that writes
  design-system rules into an agent's instruction file: the address a
  search result gave returned 404. What such rules contain was read
  from the examples of the guide [6] alone.
- Whether the convention for agent instruction files prescribes a
  section for the interface: its own site was not opened; nothing read
  here prescribes one.
- The plan template, the constitution and the commands of Spec Kit,
  the steering files of Kiro, the current major version of the BMAD
  method's interface workflow, and two further kits named in result
  lists: not opened.
- Community extensions that add wireframes to a kit, and community
  templates for a per-screen specification with a wireframe in text:
  seen in result lists, not opened, their authors unknown.
- A second, unrelated use of the file name DESIGN.md, for architectural
  intent: seen in a result list, not opened.
- Any measurement of how closely agents follow a DESIGN.md, a rules
  file or a component manifest: no source.
- A date on the vendor pages [2][3][4][5][6][7][8][9][10]: none
  printed; they are read as they stood on 2026-11-21.

## Options

1. **No interface document.** The interface stays inside requirements
   and stories, as in the two kits read [1][2]. Nothing new to
   maintain; the builder invents the interface, and what the makers
   offer against a builder's defaults is taste rules [4][5], not
   content.
2. **A description in text in three parts.** The visual identity as
   tokens with prose [3], a definition per element, a description per
   screen with fixed fields [9]. It fits a chain of Markdown documents
   and a diff; no maker prescribes it whole; long specifications are
   reported as incompletely followed and tedious to review [12]; it
   still wants a picture beside it [10][11].
3. **Structured data for the element layer.** Generated, validated
   against a schema, turned into code by script [7][8][13]. Precise
   and checkable; it presupposes a design tool or code to generate
   from, asks for tooling, is harder for a human to tune by hand, and
   behaviour and accessibility are still written by hand [13].
4. **Picture first.** A mock or a prototype carries the layout and the
   text carries only what the picture hides [6][10]. It is what the
   makers prescribe to a builder; a picture does not diff in git and
   was measured to carry placement, not function [11].

## Relevance to this project

What follows is the agent's own inference from F1 to F9. The three
senses of "design" are three kinds of content with three homes, and
only one of them lacks a prescribed shape. For the visual identity a
shape exists: tokens as the binding values, prose for their use [3];
it is alpha and one vendor's, so the idea is worth taking and the
dependency is not. For the elements, makers generate the documentation
from code or from the design tool and ask a human only for the
description [7][8][13]; a hand-written definition per element is a
fair shape before the first build ([9] gives purpose, variants,
states, usage) and should afterwards yield to, or be checked against,
what is generated. For the screens and the behaviour nothing is
prescribed; the nearest prior art is the per-screen fields of [9], and
the content that words are asked for is the content a picture hides:
states, flows, keyboard, accessibility, wording [6][10][13]. So the
idea under test, a small definition per element and a page definition
that names its elements, is supported in its shape by [8] and [9] and
qualified in its authorship by [7] and [13].

The recommendation: make the new document the description of screens
and behaviour, keep the visual identity and the elements as separate
content, pair every screen with the preview the human saw, and hand
the builder description, picture and a check together [10]. It is
chosen against folding the interface into requirements, which leaves
it to the builder's defaults [1][2][4][5]; against a specification as
the single source of the interface, which the practitioner evidence
warns of [12]; and against text alone, which the makers' own advice
and the one measurement speak against [6][10][11]. It rests on vendor
documentation, strong for what is prescribed, and on thin evidence for
what works. The word "design" alone should not name the new document
[1][3].

Consult when: the interface layer is defined; its file is named; it is
decided what the build stage is handed and where the builder's rules
live; element definitions are to be written by hand or generated;
DESIGN.md or a kit's design file is about to be borrowed.

## Sources

1. "Feature Specs", Kiro documentation, Kiro; "Page updated: August 4,
   2026" (dated by the page's own line).
   https://kiro.dev/docs/specs/feature-specs/
   Kind: primary. Read: summarised fetch, quotes checked in the raw
   text. Original.
2. "Feature Specification" template (`templates/spec-template.md`),
   Spec Kit, GitHub; undated (the file at the head of the main branch
   on 2026-11-21).
   https://raw.githubusercontent.com/github/spec-kit/main/templates/spec-template.md
   Kind: primary. Read: summarised fetch, quotes checked in the raw
   text. Original.
3. "DESIGN.md Format" (`docs/spec.md`), Google Labs; version "alpha";
   undated (the file at the head of the main branch on 2026-11-21).
   https://raw.githubusercontent.com/google-labs-code/design.md/main/docs/spec.md
   Kind: primary. Read: summarised fetch, quotes checked in the raw
   text. Original.
4. "frontend-design" skill (`SKILL.md`), Anthropic; undated (the file
   at the head of the main branch on 2026-11-21).
   https://raw.githubusercontent.com/anthropics/skills/main/skills/frontend-design/SKILL.md
   Kind: primary. Read: summarised fetch, quotes checked in the raw
   text. Original.
5. "Frontend prompt instructions", OpenAI developer documentation;
   undated.
   https://developers.openai.com/api/docs/guides/frontend-prompt
   Kind: primary. Read: summarised fetch, quotes checked in the raw
   text. Original.
6. Guide to the Figma MCP server (`README.md` of the repository
   `figma/mcp-server-guide`), Figma; undated (the file at the head of
   the repository on 2026-11-21).
   https://raw.githubusercontent.com/figma/mcp-server-guide/HEAD/README.md
   Kind: primary. Read: summarised fetch, quotes checked in the raw
   text. Original.
7. "Manifests", Storybook documentation (version 10.6 shown),
   Storybook; undated; marked as a preview.
   https://storybook.js.org/docs/ai/manifests
   Kind: primary. Read: summarised fetch, quotes checked in the raw
   text. Original.
8. "MCP Server" (registry documentation), shadcn/ui; undated.
   https://ui.shadcn.com/docs/registry/mcp
   Kind: primary. Read: summarised fetch, quotes checked in the raw
   text. Original.
9. "UI/UX Specification" template, version 2.0
   (`front-end-spec-tmpl.yaml`), BMAD method, package `bmad-method`
   4.35.0; undated (the package version alone).
   https://unpkg.com/bmad-method@4.35.0/bmad-core/templates/front-end-spec-tmpl.yaml
   Kind: primary. Read: summarised fetch, quotes checked in the raw
   text. Original: the maker's published package as served by the
   package registry's file host; an older major version.
10. "Best practices for Claude Code", Claude Code documentation,
    Anthropic; undated.
    https://code.claude.com/docs/en/best-practices
    Kind: primary. Read: partially, as raw text: the first two
    thousand characters and everything from character 4000 to the
    end; the two thousand characters between were not read. Original.
11. "VISTA: An End-to-End Benchmark for Visual Spec-to-Web-App Coding
    Agents", JunJia Guo, Yuhang Yao, Jiawei (Joe) Zhou, Jingdi Chen;
    arXiv 2605.26144v2, 11 Jun 2026 (dated by the page); a preprint.
    https://arxiv.org/html/2605.26144v2
    Kind: primary. Read: summarised fetch; the quotes and the table
    of results checked in the raw text. Original.
12. "Understanding Spec-Driven-Development: Kiro, spec-kit, and
    Tessl", Birgitta Böckeler, martinfowler.com; 15 October 2025
    (byline).
    https://www.martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html
    Kind: primary as a practitioner's report, secondary on the tools.
    Read: summarised fetch, quotes checked in the raw text, two of
    them in the alt text of images. Original.
13. "Spec-Driven UI Component Development", Nathan Curtis, the
    author's newsletter; 14 August 2026 (byline and structured data).
    https://nathanacurtis.substack.com/p/spec-driven-ui-component-development
    Kind: primary as a practitioner's report; the author makes the
    tooling he reports on. Read: summarised fetch, quotes checked in
    the raw text. Original.
14. "OpenSpec (Spec-Driven Development) Failed My Experiment —
    Instructions.md Was Simpler and Faster", the author "Incomplete
    Developer", DEV Community; 1 April 2026 (structured data; the page
    prints the day without the year).
    https://dev.to/incomplete_developer/openspec-spec-driven-development-failed-my-experiment-instructionsmd-was-simpler-and-faster-3a5d
    Kind: primary as a practitioner's report, a single uncontrolled
    case; it summarises the author's own video series. Read:
    summarised fetch, quotes checked in the raw text. Original.

## Opened and not used

- The design tool's developer documentation page for the skill that
  creates design-system rules: HTTP 404 at the address a search result
  gave; no content read; superseded by [6]. Its address is left out,
  since it does not open.

## Search record

Queries, in order:

1. DESIGN.md design file for coding agents specification
2. spec-driven development UI design, spec kit, Kiro design.md,
   front-end
3. Figma MCP server design system rules Code Connect documentation
4. frontend-design skill SKILL.md coding agent aesthetics guidance
5. spec-driven development fails for UI (disconfirming)
6. screenshot beats specification, coding agent, UI mockup instead of
   text spec (disconfirming)
7. Storybook MCP component manifest agents documentation, shadcn MCP
   registry
8. OpenAI frontend guidance coding agent design prompt design system
9. spec-kit issue UI UX design mockups wireframes specify frontend
10. BMAD method UX design specification front-end-spec template
11. Böckeler spec-driven development Kiro spec-kit Tessl spec-first
    spec-anchored spec-as-source
12. Claude Code best practices screenshot design mock official docs
13. how to describe a screen in markdown for an AI coding agent, UI
    spec file per screen, components, states (differently worded, run
    after the openings)
14. v0 Lovable Bolt documentation knowledge file design system
    instructions (differently worded, run after the openings)

Pages opened: fifteen openings, [1] to [14] and the page under Opened
and not used. Page [10] came back too long to read and was fetched
three times, the third time from character 4000 on. After the
openings each cited page was fetched again outside the fetch tool, to
confirm that it opens and to look for the quoted words in its raw
text; no further page was opened by that.

The disconfirming queries: query 5 returned opinion posts and one
dated report of a spec-driven workflow failing on a front-end
redesign, opened as [14]; it used no picture. Query 6 returned no
study and no report that sets a screenshot against a written
specification on the same task; it returned the benchmark opened as
[11], which measures what a snapshot and design data add to a short
text. The expected reports exist as the makers' own instructions to
hand over and to check against a picture [6][10]; the measured
result limits them to placement [11]. Posts arguing the reverse, that
a mock hides states and edge cases, appeared in the result list and
were not opened.

The run ended by the opening budget: fifteen openings were spent.
Every route named in the question has a primary source. The two
differently worded queries run last still returned material of kinds
not yet opened (community templates for a screen, the documentation
of interface generators), so the first half of the card's stop rule
was not met.
