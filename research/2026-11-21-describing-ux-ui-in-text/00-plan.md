---
date: 2026-11-21
project: forge
topic: how a user interface and its use are described in text - standards, practice and options
status: immutable
engines: claude, antigravity
derived_from: the principal's word of 2026-11-21; the notes research/2026-09-28-artefact-layers-from-idea-to-handover.md, research/2026-10-13-what-a-brd-contains-and-how-it-is-found-today.md, research/2026-10-03-how-a-solution-design-is-built.md, research/2026-09-30-adding-a-new-type-to-the-engine.md; the second engine's review of the draft plan, tmp/research/2026-11-21-describing-ux-ui-in-text/plan-review/
---

# How a user interface and its use are described in text: standards, practice and options

<!-- Shape: templates/research-plan.md -->

## Summary

Forty-four notes on twenty-two cards, each card answered by two
engines of different model families whose notes the measure of
independence finds independent on every card.

What the research says. No finished way exists of describing a user
interface and its use in text so that an agent proposes it, a person
tunes it and a build takes it over. The field falls into communities
that do not cite each other, each with words of its own: the
model-based tradition and its standards, none of which practice
builds on; design practice, which hands over a design-tool file and a
ticket; design systems, which define a component once and are the
firmest ground found; and the AI tooling of 2025 and 2026, whose
"design" files are technical design or visual identity and never a
description of screens and behaviour. The document wanted lies in the
gap between them. What both engines found on every route is
fragments and warnings: a public Japanese guide with one identifier
per element shared by every table; flows written in words alone;
systems that hold a page as data naming blocks defined elsewhere; the
layers of interface testing; delta specifications of the spec-driven
kits. On the idea under test, a small definition per element and a
page that names its elements, both engines agree that it is no
outlier and that every system read is its relative, and that as heard
it lacks three things: the instance of an element on a page with what
differs there, a stated rule of variation, and a threshold for which
elements earn a definition at all. No team was found that publishes
the practice itself.

Where the engines differ and what that means. The session model's
notes are the more cautious and the better founded: all of their
citations open, they say which routes have no primary source, and
they report several rules as contested which the second engine gives
as consensus (that scenarios must name the business rule and not the
screen; that a five-state list of a screen is standard; that
interface work precedes user stories; that platform owners never
write a description per platform). The second engine's notes are
broader in names and figures and rest, in fourteen of twenty-two, on
at least one address that does not open; a figure that only it
reports is a lead until its source is opened. Where the two agree on
a fact from different sources, as on the measured studies of models,
the agreement carries weight.

What it suggests. Not one unit but a few kinds of item with stable
identifiers that cite each other: what belongs to the whole
application; paths in words; screens with named regions, the elements
they use, their states and their actions; and definitions for the
elements that recur. The text should claim less than "the source of
truth of the interface": purpose, paths, states, behaviour, wording
and what is cited from the documents above, with position left to a
named region, an order and a picture. A first preview can be a
reading of the description itself.

What was unexpected. The part of a textual description that failed
everywhere is the part that says where things stand on a screen. The
four target platforms are not four things of one kind but points on
three axes, the space available, the platform's idiom and the input.
And the practitioners of the model-based tradition, by its own
standards body's account, skipped the platform-independent level the
plan assumed four platforms would ask for.

## Plan (confirmed 2026-11-21)

### Purpose

The research serves a decision on how the user interface and the
user experience of an application are described in text, so that an
AI agent can propose the description from the documents above it
(what is wanted, the requirements, the user stories) after asking
what it lacks; a human tunes the proposal and sees it; and the
description goes, with the other documents, to a build stage (a
human developer, an AI coding agent, or both), the cycle running
again when the interface changes.

The first decision it feeds is a simple shape to try on one real
project, a web interface. Later decisions: whether the shape becomes
a layer of the framework's chain, or a tool of its own beside the
framework, with previews and a connection to a design tool. The
author of a description is one person working end to end in a small
project and a UX/UI specialist in a company. The targets are the
web, the mobile web, native mobile and the desktop. The aim is
breadth. The framework is one perspective on the answer and not a
constraint: if the best way asks the framework to change, it
changes.

One idea heard from practice is to be tested, not assumed: every
element of a screen (a search field, say) has a small definition of
its own in Markdown that carries its function; a page definition
names which elements it holds and where they stand; pages are worked
by changing and rearranging those references.

What the synthesis must give: the candidate shapes of a description
(by its unit: a screen, an object, an element, a path), each with
what it would mean for one author working with an agent, its
advantages and disadvantages across the four platforms, where the
user's paths live in it, how it reaches a visible preview, and a
recommendation of the simplest shape to try first. Where a candidate
shape is put together from fragments and is found whole nowhere, the
synthesis says so and marks which part was found where.

Already known in the project, four notes: the ladder of documents
between an idea and a handover in established disciplines
(`research/2026-09-28-artefact-layers-from-idea-to-handover.md`);
what a business requirements document contains, the forms of a use
case among it
(`research/2026-10-13-what-a-brd-contains-and-how-it-is-found-today.md`);
how a solution design is built and the rule against repeating a
layer above or below
(`research/2026-10-03-how-a-solution-design-is-built.md`); what
adding a layer to the framework costs
(`research/2026-09-30-adding-a-new-type-to-the-engine.md`). Nothing
on user interfaces.

### Perspectives

- The UX practitioner: what the discipline's outputs are and what a
  description must contain (cards 2, 3, 4, 14, 22).
- The standards bodies and the academic tradition of model-based
  user interfaces (cards 1, 5).
- The maintainer of a design system: an element defined once and
  used many times (cards 6, 7).
- The agent that proposes the description: what it reads, what it
  must ask (card 17).
- The builder, a human or an AI agent: what the description must
  hold to build without the author in the room (cards 8, 9, 21).
- The person who must see a proposal before it is built (card 10).
- The specialist who works in a design tool (card 11).
- The platforms (cards 12, 22).
- The user who is otherwise shut out: accessibility, wording,
  language (card 13).
- The reviewer: how a proposal is judged (card 15).
- The verifier: who checks that what was built is what was
  described (card 20).
- The one who changes the description on a later cycle (card 19).
- The sceptic: that an interface should not be described in text at
  all (card 16).
- The framework: where such a description would stand among its
  documents and how it cites them (card 18; the rest in the
  synthesis from cards 4, 14 and 16 and the four known notes).
- The end user as a subject of research (interviews, usability
  tests). No card, left out on purpose.

### Assumptions

- The answer lives in public sources, most of them in English.
  Working specifications of real products mostly lie in private
  wikis; what is public is often an introduction or a polemic, and
  a note says so where it rests on one. Two routes are taken against
  this: primary artefacts in public repositories are read before
  commentary about them, and practice outside English is looked at
  where it kept the textual specification of screens alive.
- ISO standards are behind sale and are read through secondary
  pages.
- The part on AI tooling moves by the month: sources of 2025 and
  2026 count, older ones are history.
- That a textual description can be the source of truth at all is
  the plan's own assumption; card 16 exists to attack it.
- The idea of a definition per element may have no public write-up
  under any name; card 7 looks for its relatives and says so if the
  thing itself is not found.
- No finished shape is assumed to exist. Earlier textual
  descriptions of interfaces were written by people for people, or
  for deterministic generators; a description that a person and a
  language model write together, that tolerates half-structured
  text and is shown as a preview at once, is a new situation. The
  sources are expected to give fragments and warnings; a card that
  finds a finished shape reports it as unexpected.
- "Design" stands for three things in the sources: the design of
  the interface held in a design tool, the technical design between
  requirements and tasks in spec-driven kits, and the visual
  identity of a design system. A card that searches by the word
  says which it means.
- Card 1 runs first; the words and any synthesis it finds may
  rewrite the other cards.

Premortem, Claude's own: "the research is done and missed the most
interesting thing: what was it?" That the best present practice
keeps no description of screens at all: the source of truth is a
running component library or a prototype and the text is derived
from it, or what is described is the objects of the domain and the
screens follow from them. Cards 4, 10, 16 and 21 are there to catch
both; if they return thin, the plan failed there.

### Left out

- Visual craft: how to make an interface beautiful. Only how visual
  decisions are recorded is in (card 6).
- Research with users as a method. Only how its results enter a
  description is in (card 14).
- A comparison of front-end frameworks, and of code generators'
  output by vendor.
- Voice and conversational interfaces, games, AR and VR, automotive
  and embedded interfaces.
- Prices and licences of tools.
- The detail of accessibility law beyond what a description must
  carry.

### Cards

**A. The field**

#### Card 1: The map of the field and its words
- **Question:** Does a synthesis already exist of how user interfaces and user experience are specified in text (a survey, a taxonomy, a comparison of approaches), and in which words do practice, the standards and the AI tooling of 2024 to 2026 speak of it (UI specification, functional specification, interaction specification, design handoff, design documentation, UI description language, design as code, spec-driven development)?
- **Why it matters:** every other card searches by the field's words, and a synthesis found here saves cards or rewrites them.
- **What would answer it:** survey and overview literature: academic surveys, standards bodies' overviews, overviews by practitioner organisations.
- **Where to look:** surveys of UI description languages and of model-based UI development; notes of the W3C; glossaries and overviews of practitioner organisations; recent overviews of spec-driven development that treat the interface. Must turn up: the W3C's model-based UI work, IFML, "design handoff".
- **Disconfirming query:** "why is there no standard for UI specification"; expected: several partial standards and no dominant one.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

**B. What is described, and in what shape**

#### Card 2: The description of one screen
- **Question:** What does an established description of a single screen or page contain (an annotated wireframe, a screen specification, a functional or UI specification): which fields recur (purpose, entry points, regions, elements, data, actions, states such as empty, loading and error, rules, responsive behaviour), how are elements identified and referred to, and how much is prose against structure?
- **Why it matters:** the first shape to try is a description of a few screens.
- **What would answer it:** published templates and guides of practitioners and organisations.
- **Where to look:** practitioner organisations on wireframe annotation; service manuals of public administrations; public templates of companies; the specification chapters of UX handbooks; the Japanese practice of screen design documents (gamen sekkeisho, within the basic design, kihon sekkei), read in Japanese or in translation; templates of public procurement and of systems engineering in Europe; specifications published by open-source products. Search words from card 1: "design specs", "wireframe annotations", "prototype specifications", "wireflows", "state matrix"; and the model-based words "abstract user interface", "concrete user interface", IFML's "view container", "view component", "interaction flow".
- **Disconfirming query:** "UI specification document is waste", "annotated wireframes are dead"; expected: criticism of heavy specifications and a preference for prototypes.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

#### Card 3: The user's path
- **Question:** How are the paths of a user described in text (use cases and essential use cases, task models, user flows, journey maps, story maps, scenarios, state machines): what is each for and at what level, and where does it live against the screens: a document of its own that the screens are cited from, a part of each screen, or both; and how are the links between a path and its screens kept?
- **Why it matters:** the author asks where the user's paths belong and whether they stand alone.
- **What would answer it:** the methods as their authors and their standards state them.
- **Where to look:** the original literature of use cases, essential use cases and story mapping; practitioner organisations on journey maps against user flows; IFML; statecharts and SCXML; task-model notations; breadboarding. The known note on business requirements for the forms of a use case. Search words from card 1: "design specs", "wireframe annotations", "prototype specifications", "wireflows", "state matrix"; and the model-based words "abstract user interface", "concrete user interface", IFML's "view container", "view component", "interaction flow".
- **Disconfirming query:** "user flows or screens first", "journey maps are useless"; expected: advice to describe flows before screens.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

#### Card 4: What stands above the screens
- **Question:** How do practice and literature describe the structure above single screens (the conceptual model of objects with their attributes, actions and relationships; the information architecture; the navigation and the map of screens), in which textual forms, and what do they claim follows from describing objects before screens?
- **Why it matters:** it decides what the unit of the description is: a screen, an object or an element.
- **What would answer it:** method literature by its authors.
- **Where to look:** the literature on conceptual models in interaction design; object-oriented UX; information architecture; how domain modelling is tied to interface design. Search words from card 1: "design specs", "wireframe annotations", "prototype specifications", "wireflows", "state matrix"; and the model-based words "abstract user interface", "concrete user interface", IFML's "view container", "view component", "interaction flow".
- **Disconfirming query:** "object-oriented UX criticism"; expected: little published criticism, some doubt about cost.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

#### Card 5: Formal languages and standards
- **Question:** Which formal languages and standards describe a user interface or its interaction independently of its implementation (the model-based tradition with its levels of task, abstract, concrete and final interface; UsiXML, UIML, MARIA, XForms, the W3C's notes; IFML; the parts of ISO 9241), what does each describe, what became of each in practice, and which reasons are given for adoption or its absence?
- **Why it matters:** a layered description independent of the platform is what four target platforms ask for; the fate of these languages says what to borrow and what to avoid.
- **What would answer it:** the standards' own documents and academic studies of their adoption.
- **Where to look:** the W3C's model-based UI working group; the IFML specification; surveys of model-based UI development; ISO through secondary pages. Search words from card 1: "user interface description language", "model-based user interface development", "CAMELEON reference framework", "task model", "Common Industry Format" (ISO/TR 25060); the W3C's UI Specification Schema Community Group of 2025 and 2026, to be verified; why the notes of 2014 and the version of 2015 had no successor.
- **Disconfirming query:** "model-based user interface development industrial adoption success"; expected: little adoption, with a few fields where it held.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

#### Card 6: An element defined once
- **Question:** How do mature design systems describe one component so that it is defined once and used on many screens (the parts of a component specification: anatomy, variants, properties, states, behaviour, accessibility, rules of content), how are patterns and page templates built from components, how are visual decisions recorded as design tokens, and what do the maintainers say about keeping the description and the implementation the same?
- **Why it matters:** it tests the first half of the idea of small definitions: an element with a definition of its own that carries its function.
- **What would answer it:** the design systems' own documentation and their maintainers' writing.
- **Where to look:** the public design systems of large vendors and of public administrations; writing on component specifications; atomic design; the design tokens format of the W3C community group; documentation tools that render components in isolation. Search words from card 1: "design tokens format module", "component specification", "anatomy, states, variants"; the W3C's UI Specification Schema Community Group of 2025 and 2026 and Open UI. Primary artefacts in public repositories (schemas, component and page files, agents' rules and prompt files, the schemas of servers for design tools, issue trackers) before commentary about them.
- **Disconfirming query:** "design system documentation drift", "component specification out of date"; expected: drift is a known trouble and documentation is generated from code.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

#### Card 7: A page as a composition of defined blocks
- **Question:** Which systems hold a page as data that lists references to separately defined blocks with their placement and settings (block editors with their patterns and templates, theme templates made of sections, page builders on structured content, server-driven UI, declarative card formats and formats by which an agent sends an interface, page schemas of low-code tools), how does each divide what a block is and does from where it stands on a page, how is a page rearranged, and which troubles do they report; and does any team publish a practice of one Markdown file per interface element with page files that refer to them?
- **Why it matters:** these are the direct relatives of the idea of small definitions.
- **What would answer it:** vendors' documentation of their own formats, and engineering write-ups by teams that built such systems.
- **Where to look:** the documentation of block editors, of section-based theme templates and of structured-content page builders; engineering write-ups on server-driven UI; the specifications of declarative card and agent-to-interface formats; public repositories and write-ups for component specifications kept in Markdown for AI agents. Search words from card 1: "generative UI" for formats in which an agent emits an interface at run time, kept apart from a description handed to a build; "intermediate representation", "structured specification". Primary artefacts in public repositories (schemas, component and page files, agents' rules and prompt files, the schemas of servers for design tools, issue trackers) before commentary about them.
- **Disconfirming query:** "server-driven UI problems", "page builder blocks limitations"; expected: complaints about versioning and about what blocks cannot express.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

#### Card 22: What belongs to the whole application
- **Question:** Which behaviour of an application lies outside any single screen and any linear path (addresses and deep links, the persistent frame of navigation, several windows or tabs and their state, notifications and events that arrive unasked, offline and degraded states, one view differing by role and permission), how do platform guidelines and specification practice describe it, and where is it kept in a description: once for the application, or again on every screen?
- **Why it matters:** a description built only from screens, elements and paths has no place for it, and every candidate shape must say where it lives.
- **What would answer it:** the platform owners' guidelines and the web's standards on behaviour at the level of the application.
- **Where to look:** platform guidelines on navigation, deep links, notifications, windows and offline behaviour; web standards and guidance on routing and on working offline; specification templates that carry a section for the rules of the whole application. Search words from card 1: "design specs", "wireframe annotations", "prototype specifications", "wireflows", "state matrix"; and the model-based words "abstract user interface", "concrete user interface", IFML's "view container", "view component", "interaction flow".
- **Disconfirming query:** "per-screen specification is enough", "global UI rules section unnecessary"; expected: nothing argues that it needs no place.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

**C. The agent and the build**

#### Card 8: Descriptions written for an agent that builds
- **Question:** How do the AI coding and design tools of 2025 and 2026 want a user interface described so that an agent builds it (the design file of spec-driven kits, a design file for agents, sections of agent instruction files, rules files, skills and prompts for interface work, servers that give an agent a design system, component documentation as an agent's context): which content and shape do their makers prescribe, and what do practitioners report works or fails?
- **Why it matters:** the build stage is an agent at least in part, and the description must be what an agent builds from.
- **What would answer it:** the tools' own documentation, and dated reports by practitioners.
- **Where to look:** the documentation of spec-driven development kits, of interface generators and of design tools' AI features; the makers' guidance on front-end work with coding agents; component registries and their agent integrations. Search words from card 1: "spec-driven development", "spec-first", "spec-anchored", "spec-as-source", "constitution", "steering files", "EARS", "DESIGN.md". Primary artefacts in public repositories (schemas, component and page files, agents' rules and prompt files, the schemas of servers for design tools, issue trackers) before commentary about them.
- **Disconfirming query:** "spec-driven development fails for UI", "screenshot beats specification"; expected: reports that a picture or a prototype steers an agent better than text.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

#### Card 9: What measurement shows about models and interface descriptions
- **Question:** What do measured studies of 2025 and 2026 show about language models and interfaces in both directions: an agent building an interface from a description (which input, among prose, a structured specification, a wireframe, a screenshot, tokens and a component library, gives the result closest to what was wanted, above all across several screens and their states), and a model writing a description from pictures of existing screens (what it gets right, what it misses, what it invents)? Single-shot benchmarks of 2023 and 2024 are read as history only.
- **Why it matters:** it is the one card that rests on measurement and not on a maker's claim; it decides how much structure a description needs for an agent, and whether a first description can be written from pictures, as the first trial will do.
- **What would answer it:** peer-reviewed papers, benchmarks and preprints with a stated method.
- **Where to look:** benchmarks of interface generation in agentic and multi-page settings; studies of the understanding and the description of screens; the proceedings of the main conferences of 2025 and 2026; preprint servers. Search words from card 1: "design to code", "UI to code", "image to code", "intermediate representation".
- **Disconfirming query:** "text specification outperforms screenshot for UI generation", "screen description hallucination"; expected: a picture beats text for layout, and a description from a picture invents behaviour.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

#### Card 10: From text to something visible
- **Question:** By which ways does a textual description become a visible preview before the product is built (languages that draw a wireframe from text, generated low-fidelity wireframes, generated clickable prototypes, a component library rendered in isolation): what does each need as input, what does it cost to change and make again, and at which stage do processes place the preview: with the definition or with the build?
- **Why it matters:** the author must see a proposal to tune it, and a change of the interface must not mean rebuilding the product.
- **What would answer it:** the tools' own documentation, and process literature on the fidelity of prototypes.
- **Where to look:** text-to-wireframe languages and diagram tools; tools that render components in isolation; AI prototype generators; practitioner organisations on prototype fidelity; processes that sketch before they build.
- **Disconfirming query:** "low-fidelity wireframes obsolete", "the prototype is the specification"; expected: a claim that generated prototypes make wireframes needless.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

#### Card 11: Text and the design tool
- **Question:** How are a textual or code source and a design tool connected today (reading a design as structured data, writing a design from structured text, linking components to code, keeping tokens and variables in step), for the dominant design tool and for open alternatives: in which direction does each connection run, and what must a text-first description keep (identifiers, a vocabulary of components, tokens) so that such a connection can be added later?
- **Why it matters:** a specialist will need the design tool, and the first step must not close that path.
- **What would answer it:** the vendors' documentation of their own interfaces.
- **Where to look:** the design tools' programming interfaces, developer modes, component-to-code links and agent servers; token tools; the open design tool's format and interface. Search words from card 1: "handoff" names the passage and a tool's features for it, not the document; for the document "design specs", "annotations", "ready for dev"; vendors' pages on their own market are to be expected and are left out by the brief. Primary artefacts in public repositories (schemas, component and page files, agents' rules and prompt files, the schemas of servers for design tools, issue trackers) before commentary about them.
- **Disconfirming query:** "design to code round trip problems", "design tool or code as source of truth"; expected: the connection runs well in one direction only.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

#### Card 17: The agent that proposes the description
- **Question:** How does an AI agent get from requirements, user stories and a solution design to a first proposal of an interface: what of an interface cannot be inferred from those documents and must be asked, which questions are asked and in which order before screens or flows are proposed, and how do the published workflows of 2025 and 2026 keep the agent from inventing arbitrary layout and interaction?
- **Why it matters:** the author expects the agent to read everything, ask what it lacks and make the proposal; this is the step an elicitation of the description would define.
- **What would answer it:** the published workflows, prompts and skills of AI design tools and spec-driven kits, read as primary artefacts in their repositories and documentation.
- **Where to look:** the steps from requirements to design in spec-driven kits and their prompt files; the question flows of AI interface generators and design assistants; public agent skills and rules for interface design. What human method prescribes for the same step is card 14's. Search words from card 1: "spec-driven development", "spec-first", "spec-anchored", "spec-as-source", "constitution", "steering files", "EARS", "DESIGN.md". Primary artefacts in public repositories (schemas, component and page files, agents' rules and prompt files, the schemas of servers for design tools, issue trackers) before commentary about them.
- **Disconfirming query:** "AI generated UI generic", "LLM design without clarifying questions"; expected: reports that an agent which does not ask produces a generic interface.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

#### Card 21: Where a description becomes code
- **Question:** What do declarative interface languages (SwiftUI, Jetpack Compose, QML, XAML, HTML with components, MDX) show about the border between a readable description and code: what of an interface do they state in a form a person can read and rearrange, what do they keep apart (structure, state, style), how do their previews work, and what do their makers and users say a description above the code must still hold?
- **Why it matters:** if what the build produces is itself a readable description with an instant preview, the layer above it must hold only what the code cannot say.
- **What would answer it:** the languages' own documentation and their makers' writing.
- **Where to look:** the documentation of the declarative interface frameworks of the four platforms and of their preview tools; their makers' guidance on going from a design to code. Search words from card 1: "generative UI" for formats in which an agent emits an interface at run time, kept apart from a description handed to a build; "intermediate representation", "structured specification".
- **Disconfirming query:** "the code is the specification declarative UI"; expected: a current that holds the code to be the description.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

**D. The breadth of the target**

#### Card 12: The platforms
- **Question:** What differs in describing an interface for the web, the mobile web, native mobile and the desktop: what do the platform guidelines prescribe (navigation, input, windows, the system's conventions), how is responsive and adaptive behaviour specified, and how do products and design systems on several platforms describe one thing: one abstract description with platform variants, or a description per platform?
- **Why it matters:** the targets are four platforms, and the unit and the layering of the description must carry them.
- **What would answer it:** the platform owners' guidelines and the documentation of design systems that span platforms.
- **Where to look:** the human interface guidelines of the mobile and desktop platforms; the adaptive-layout guidance of the large design systems; web standards on responsive design.
- **Disconfirming query:** "one design for all platforms fails", "platform conventions against cross-platform consistency"; expected: both camps exist.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

#### Card 13: What the description owes every user
- **Question:** What must a description of an interface carry so that accessibility, the wording in the interface and language versions are designed and not repaired: which accessibility properties are specified at design time (names, roles, states, focus order, keyboard, contrast, target sizes), how are the texts of the interface specified (content design, terminology), how is internationalisation prepared, and how do existing specification templates carry these?
- **Why it matters:** left out of the description they return as rework after the build, and accessibility is a legal duty in many markets.
- **What would answer it:** the standards themselves and their authors' guidance.
- **Where to look:** the web accessibility guidelines and the authoring practices for rich components; public accessibility annotation kits; content design guides of public administrations; the W3C's internationalisation guidance.
- **Disconfirming query:** "accessibility annotations do not work", "shift-left accessibility evidence"; expected: thin evidence either way.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

**E. The process and the judgement**

#### Card 14: The place in the process and the roles
- **Question:** Where does the work on the interface stand between the requirements and the build in established processes: what does it take from requirements and user stories, what does it hand to the builders, in which order do its own outputs come (flows, structure, wireframes, visual design, prototype, specification), and how does the same output serve one person working end to end and a specialist in a team: which outputs do lean and solo practices drop, and which do they keep?
- **Why it matters:** it decides where the description stands among the framework's documents and how light the first shape can be.
- **What would answer it:** method literature and practitioner organisations.
- **Where to look:** the layered models of user experience work; lean UX; dual-track practice; the human-centred design standard through secondary pages; guides to design handoff. The known notes on the ladder of documents and on business requirements. Search words from card 1: "handoff" names the passage and a tool's features for it, not the document; for the document "design specs", "annotations", "ready for dev"; vendors' pages on their own market are to be expected and are left out by the brief.
- **Disconfirming query:** "UX deliverables are waste", "design handoff is dead"; expected: a strong current against handing over documents at all.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

#### Card 15: How a proposal is judged before it is built
- **Question:** By which established methods is a design of an interface judged before it is built (heuristic evaluation, cognitive walkthrough, design critique, expert review by checklist, inspection of consistency): what does each look at, what does it need as its input (can it be run on a textual description, or only on a picture or a prototype), and what is known about language models performing such an evaluation?
- **Why it matters:** a proposal made by an agent is tuned by a human and read by reviewer agents; the description must be something that can be judged.
- **What would answer it:** the original literature of the methods and recent studies of automated evaluation.
- **Where to look:** the literature of usability inspection methods; writing on design critique; studies of 2024 to 2026 on models as evaluators of interfaces.
- **Disconfirming query:** "heuristic evaluation unreliable evaluator effect", "LLM usability evaluation false positives"; expected: evaluators disagree, and models over-report.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

#### Card 16: Where describing an interface in text failed
- **Question:** Where did textual specifications of interfaces fail or get abandoned (heavy specification documents, descriptions that drifted from the product, generation from models), which reasons are recorded, what do those who argue against describing an interface in text propose in its place (the prototype as the specification, the code as the source of truth), and what kept true the textual descriptions that survive (generation from the product, tests bound to the text, a narrow scope)?
- **Why it matters:** the plan assumes text can be the source of truth; this card attacks that before a layer rests on it.
- **What would answer it:** critiques, post-mortems and reports of experience.
- **Where to look:** the criticism of design up front; living documentation and specification by example; reports of experience with behaviour-driven development for interfaces; writing on drift between design and product. The known note on the solution design for what is known of staleness. Search words from card 1: the fate of model-driven development beside the warning of 2025 that a specification as the only source repeats it ("review fatigue").
- **Disconfirming query:** here the confirming one: "UI specification as source of truth long-lived success"; expected: few documented cases, most of them generated or tested.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

#### Card 18: What the description cites and does not repeat
- **Question:** How does a description of an interface refer to what is defined elsewhere (the data model and its fields, validation and business rules, permissions and roles, the states and errors of the services behind it) without repeating it: which mechanisms of reference does established specification practice use (identifiers of requirements, a data dictionary, a contract between systems, a shared glossary), what is kept in the description of the interface and what is only cited, and what is reported about the two drifting apart?
- **Why it matters:** the description will stand beside requirements, a solution design and user stories, and the framework lets no layer repeat another.
- **What would answer it:** requirements engineering and specification practice as its standards and handbooks state it.
- **Where to look:** the literature on traceability from requirements to the design of an interface; specification templates that keep a data dictionary apart from the screens; interface descriptions bound to a service contract or a schema. The known notes on the solution design and on business requirements.
- **Disconfirming query:** "traceability matrix is waste", "business rules duplicated in UI specification"; expected: traceability kept by hand decays.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

#### Card 19: The description after the first build
- **Question:** How is a description of an interface changed and kept once the product exists: how is a change to it read and reviewed as a difference in text, how do changes made during the build get back into it, how do systems of shared definitions handle a screen that needs a variation of a shared element (variants, overrides, instances) and show which pages a change to a shared element touches, and how are such definitions versioned?
- **Why it matters:** the cycle runs again whenever the interface changes, and the idea of a definition per element stands or falls on variation and on the reach of a change.
- **What would answer it:** the documentation of systems that keep shared definitions, and of spec-driven kits, on how a change is made and carried.
- **Where to look:** design systems on versioning, breaking changes and variants; design tools on components, instances and overrides; block and section systems on variations; spec-driven kits on changing a specification after code exists and on bringing changes of the code back into it. Search words from card 1: "spec-driven development", "spec-first", "spec-anchored", "spec-as-source", "constitution", "steering files", "EARS", "DESIGN.md". Primary artefacts in public repositories (schemas, component and page files, agents' rules and prompt files, the schemas of servers for design tools, issue trackers) before commentary about them.
- **Disconfirming query:** "keeping specification in sync with code fails", "design system overrides chaos"; expected: bringing changes back is done by hand or not at all.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

#### Card 20: The description and the test
- **Question:** What has automated testing of interfaces learned about describing screens in modular text: how do the Page Object and Screenplay patterns and executable specifications define the elements of a screen and their actions as units of their own that user paths refer to, at which level of abstraction do such units survive a change of the interface and at which do they break, and how is a built interface checked against its description (tests bound to the text, comparison of pictures, inspection)?
- **Why it matters:** these are definitions per element kept in version control for twenty years, and the build needs a way to show that it built what was described.
- **What would answer it:** the pattern literature and the testing tools' own documentation.
- **Where to look:** the original descriptions of Page Object and Screenplay; specification by example and behaviour-driven development for interfaces; testing tools' guidance on the level of abstraction; visual regression testing.
- **Disconfirming query:** "page object anti-pattern", "BDD UI tests brittle"; expected: units at the level of an element are brittle, units at the level of a task last.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

### Agents

One isolated agent per card per engine: twenty-two cards on two
engines of different model families, the session model and
`antigravity`, the latter run with the model word the principal
named, recorded in each note. Card 1 runs first on both; where its
return rewrites other cards, the rewrite is shown to the principal
before the rest is dispatched. A second round only for gaps the
notes name.

### The second engine's review of the draft

The review of `antigravity`, 2026-11-21, on a draft of sixteen
cards, item by item, with what the principal took of it:

- Missing, the agent that proposes the description: the draft had
  the agent as builder and as reviewer only. Taken: a perspective
  and card 17.
- Missing, the contract with the neighbouring layers: how a
  description of an interface refers to data, rules, permissions and
  the states of services without repeating them; the framework's
  perspective, left to the synthesis, had no evidence for it. Taken:
  card 18, and the framework's perspective now names it.
- Missing, the change on a later cycle: reading a difference in
  text, bringing changes of the build back, a variation of a shared
  element, the reach of a change to one. Taken: a perspective and
  card 19.
- Missing, two fields where modular textual descriptions of screens
  are kept in version control: automated testing of interfaces (the
  Page Object and Screenplay patterns, executable specifications),
  with the verifier's perspective, and declarative interface
  languages. Taken: a perspective and cards 20 and 21.
- Missing, behaviour of the whole application outside single screens
  and linear paths. Taken: card 22.
- Assumption, that the answer lies in public literature in English
  and in commentary: working specifications lie in private wikis,
  practice outside English kept textual screen specifications alive
  (the Japanese screen design documents, public procurement in
  Europe), and the mechanics of design systems and AI tooling lie in
  primary artefacts in repositories. Taken: the first assumption
  rewritten, a route added to card 2, and the reading of primary
  artefacts before commentary added to cards 6, 7, 8, 11, 17 and 19.
- Assumption, that a working shape already exists and waits to be
  catalogued: a description written by a person and a language
  model together is a new situation, and the sources will give
  fragments and warnings. Taken: an assumption added, and the
  synthesis told to mark what it put together from fragments.
- Cut, card 9, for contradicting the plan's own rule of recency, for
  resting on single-shot benchmarks on superseded models, and for
  the direction from a picture to a description running against the
  work. Not taken: the principal kept the card, narrowed to studies
  of 2025 and 2026 and to agentic and multi-page settings, the older
  benchmarks read as history; the direction from pictures stays,
  since the first trial describes existing pictures, and the card is
  the one that rests on measurement.

## Deviations from the plan

- Card 1 rewrote the search words of the other cards, as the plan
  foresaw. Its two notes found no synthesis across the field and a
  vocabulary that does not carry from one community to another, two
  of the plan's own words misleading ("handoff" names the passage,
  not the document; "design" stands for three things). On the
  principal's word of 2026-11-21 an assumption on the word "design"
  was added and a sentence of search words was added to "Where to
  look" in cards 2, 3, 4, 5, 6, 7, 8, 9, 11, 14, 16, 17, 19, 21 and
  22. No question of a card changed, and no card was cut.
- The notes are named `card-NN-<slug>.<engine>.md`, the form
  `scripts/forge-cite.py --independence` reads. The two notes of
  card 1 were first filed without the prefix and renamed on the same
  day, their text unchanged; their `run` names the packet folder,
  which kept its name `01-map-of-the-field`.
- The notes of card 1 on both engines rest on summarising fetches
  and say so; neither read a raw page.
- From card 2 on, the agent on the session model writes its own
  note into the run folder's `hold/` and returns one line, against
  the skill's rule that an agent writes no file and Claude writes
  its return down: the agent's return reaches the session only as a
  message, and the note of card 1 had to be typed over by hand. On
  the principal's word of 2026-11-21. The packet is unchanged; the
  exception stands in the sentence the agent is started with. The
  second engine cannot read `hold/`. The note of card 1 on the
  session model is the one typed over by hand.
- Six notes had dead citations at the first check and went back
  once with the dead addresses named, as the skill has it: the
  session model's note of card 2, corrected by its own agent, which
  dropped the two addresses, no finding having rested on them; and
  the second engine's notes of cards 2, 3, 6, 7 and 22, run a second
  time, the first versions kept in the run folder under
  `hold/first-run/` since `scripts/forge-engine.py` writes over no
  existing note. After the second run card 6 is clean; cards 2, 3, 7
  and 22 still cite pages that do not open (four, one, six and one)
  and are filed as they are.
- Ten further notes of the second engine have dead citations (cards
  8, 10, 11, 12, 14, 16, 18, 19, 20 and 21: three, one, six, four,
  one, five, two, two, three and three) and were not sent back,
  against the skill, on the principal's word of 2026-11-21. Over the
  five notes that had gone back the dead citations numbered eleven
  before the second run and twelve after it: this engine cites
  addresses out of the summaries of its search tool without opening
  the pages, and a second run brings other addresses of the same
  kind. The findings that rest on a dead citation are named under
  Completeness.
- The agent of card 4 on the session model wrote its note twice, the
  second time with five small corrections of its own; the second
  writing is the one filed.
- The second engine's runs of the cards of group C and four of its
  second runs started about half an hour late, a batch command of
  the session having started only the first of them; no run was
  lost.
- The web search of the session ran out during the third wave. The
  eight agents of the session model on cards 12 to 16 and 18 to 20
  had their queries refused after none to six of them (card 16 none,
  cards 14 and 18 three, card 15 five, cards 12 and 13 six, cards 19
  and 20 a part of theirs), while the opening of pages went on; the
  search answered again later the same day. On the principal's word
  of 2026-11-21 a second round was run for those eight notes, as the
  plan allows for gaps the notes name: each agent went on from its
  first run, ran the refused queries, opened at most eight further
  pages and rewrote its note, and the rewritten notes took the place
  of the first ones in the bundle. No query was refused in the
  second round. After it the stop rule is met for cards 13, 16 and
  20, in part for card 15, and not for cards 12, 14, 18 and 19,
  where a differently worded query still brought new material or a
  route still has no primary source. These notes opened up to
  twenty-three pages over the two rounds against the card's ten to
  fifteen.
- The agents of the session model ended on the budget of openings in
  every card of the first run; where the card's stop rule was met as
  well, the note says so.
- The scan for the instance's facts flags one line in the session
  model's note of card 18, a bibliographic reference that names a
  university by its country; no fact of this instance. Filed as it
  is. The second engine's first note of card 7 was flagged for a
  sample path out of a vendor's schema; its second run is not.
- The citation check counts as dead one address in the session
  model's note of card 20, which answers 406, and one in the second
  engine's note of card 11, which answers 405: the host refuses the
  script's request, which is not the page being gone. Both are named
  under Completeness with the others.
- The report of an outside deep research on the same assignment was
  first registered as a source of the project and, on the principal's
  word of 2026-11-21, moved into the bundle as
  `deep-research.copilot.md` after the synthesis was filed, so that
  every output of the research lies in one directory. The synthesis
  does not rest on it. With the move, the sentence on the report at
  the head of the Synthesis, a line of the Notes and this entry were
  written into the head after its filing.
- A second outside report, of Gemini's deep research, was placed in
  the bundle by the principal after the synthesis and registered
  there on the same day as `deep-research.gemini.md`, under the same
  rule: no part of the synthesis, with a line of the Notes and this
  entry written into the head after its filing. It is not in English
  and stays in the language it arrived in; the rule that research is
  written in English is not applied to an outside report kept word
  for word.

## Synthesis (2026-11-21)

Made by Claude in the session from the notes of the bundle alone. Each
note was read in its In short, the head of each of its key findings,
its Unexpected, Not found and Relevance and the end of its Search
record, not in the full text of every finding. The two reports of
outside deep researches that lie in the bundle,
`deep-research.copilot.md` and `deep-research.gemini.md`, are no part
of it.

### Completeness, card by card

"Claude" is the note of the session model, "antigravity" that of the
second engine. "Reports the stop rule met" is the note's own word.

**Card 1, the map of the field and its words.**
Answered by both engines: no synthesis across the field
exists. Claude: ended on the budget of openings; the second half of
the stop rule not met, two routes having no primary read for content
(the surveys of description languages, a practitioner glossary for
"design handoff"). Antigravity: reports both halves met at fifteen
openings, every one a summarising fetch of its search tool. The
disconfirming query found no page that answers why there is no
standard; with claude it led to a W3C community group named for the
matter, called in August 2025 and closed on 21 May 2026 without a
listed report. No dead citation; the W3C pages are unverifiable by the
script (403).

**Card 2, the description of one screen.**
Answered by both. Claude: no shared standard; three
families (the tabular screen design document of Japanese practice, the
picture with numbered notes, the prose functional specification); the
budget of openings ended the run, the stop rule not met; went back
once for two dead citations, both dropped, no finding having rested on
them. Antigravity (second run): six recurring groups of fields;
reports the stop rule met; four dead addresses, cited by five of its
seven findings. The disconfirming query found with both the expected
criticism of heavy specifications; claude adds that it is aimed at
weight and staleness, not at the fields.

**Card 3, the user's path.**
Answered by both. Claude: ended on the budget, the stop
rule not met, three routes without a primary that could be read
(essential use cases in their authors' text, the IFML specification, a
handbook chapter). Antigravity (second run): reports the stop rule
met; one dead address, cited by F6 (the five states of a screen). The
disconfirming query confirmed with both that the path comes before the
screens; with claude a second wording found the counter-position that
objects come before both.

**Card 4, what stands above the screens.**
Answered by both. Claude: ended on the budget; the
routes of usage-centred design and of the book literature of
information architecture have no primary read. Antigravity: reports
the stop rule met, every finding resting on a summarising fetch; no
dead citation. The disconfirming query: antigravity reports
practitioner doubts about cost, resistance and rigidity on linear
tasks; claude found no published criticism of object-oriented UX at
all, only an older criticism of generated object-oriented interfaces,
read in its target's account. The engines disagree on what the same
query found.

**Card 5, formal languages and standards.**
Answered by both. Claude: ended on the budget (seventeen
openings, two unreadable); the route of the academic surveys rests on
one abstract and the ISO route on a secondary page and a seller's
copy. Antigravity: reports the stop rule met, all by summarising
fetch; no dead citation; fifteen of its thirty addresses unverifiable.
The disconfirming query found with both no broad industrial success,
only pockets (automotive, industrial control, low-code), each claimed
by those who work in them.

**Card 6, an element defined once.**
Answered by both. Claude: ended on the budget; every
route has a primary source; further instances turned up that could not
be opened, so "nothing new" is not claimed. Antigravity (second run):
reports the stop rule met; clean on citations. The disconfirming query
confirmed with both that drift between a component's description and
its implementation is a known trouble; claude qualifies what was
expected: what is generated from code is the reference of properties
and the examples, never the guidance, which is written by hand
wherever it was seen.

**Card 7, a page as a composition of defined blocks.**
Answered by both, the idea under test included. Claude:
ended on the budget with the other parts of the stop rule holding; one
engineering write-up on the best-known server-driven system could not
be opened; clean on citations. Antigravity (second run): reports the
stop rule met; six dead addresses, three of them cited by F1 and F3,
three standing under Opened and not used. The disconfirming queries
met with both the expected complaints about versioning; claude found
little on what blocks cannot express beyond fixed counts and default
layouts.

**Card 8, descriptions written for an agent that builds.**
Answered by both. Claude: ended on the budget; every
route has a primary source, the last queries still returned kinds of
material not opened; clean on citations, the quotes checked against
the raw text. Antigravity: reports the stop rule met; three dead
addresses, all one source (template paths of a spec-driven kit), cited
by F1. The disconfirming query held in part with claude: makers tell
the user to hand the agent a picture of the layout and to check
against a screenshot, while a measured study found that a picture
improves where things sit far more than whether the application
works. Antigravity reports a wide practitioner consensus that prose
fails for spatial layout ("screenshots beat specifications").

**Card 9, what measurement shows.**
Answered by both for the first direction; for the second
the engines disagree on whether it was answered at all. Claude: ended
on the budget, two routes without a primary source (tokens and a
component library as an input; a measured description from pictures);
clean on citations. Antigravity: reports the stop rule met; all
thirteen addresses open. The disconfirming queries: with claude no
study in which text alone beat a picture for the look of a page, but
text the better input for behaviour and for changing an existing
interface; that a description from a picture invents behaviour has no
measurement for or against. With antigravity both halves of the
expectation confirmed.

**Card 10, from text to something visible.**
Answered by both. Claude: ended on the budget, every
route with a primary source, one variant (wireframes kept as plain
HTML files) left unopened; clean on citations. Antigravity: reports
the stop rule met; one dead address, a vendor's blog, cited by F5. The
disconfirming query found with both the claim that generated
prototypes make wireframes needless, as opinion and as vendors'
accounts, with no measurement behind it; the sources that tested
generators place them in early exploration.

**Card 11, text and the design tool.**
Answered by both. Claude: ended on the budget, every
route with a primary source, later leads unopened; clean on citations,
the quoted phrases matched in the page text. Antigravity: reports the
stop rule met; six addresses counted dead, one of them an endpoint
that answers 405 and is not gone; they are cited by six of its seven
findings, so that its note rests in good part on addresses that do not
open. The disconfirming query's expectation, that the connection runs
well in one direction only, held in a weaker form with both: both
directions now exist as documented interfaces, and no source shows a
round trip without loss.

**Card 12, the platforms.**
Answered by both. Claude (two rounds): the second half of
the stop rule met, every route with a primary source; the first not,
a differently worded query still returning new sources; twenty-three
openings over the two rounds; clean on citations. Antigravity: reports
the stop rule met; four dead addresses, three of them cited by F1,
F2, F3 and F7. The disconfirming query found both camps with both
engines, and a mixed position on which the sources end.

**Card 13, what the description owes every user.**
Answered by both. Claude (two rounds): the stop rule met
on both conditions; twenty-three openings; fifteen of its addresses
open and eight unverifiable, none dead. Antigravity: reports the stop
rule met; clean, six unverifiable. The disconfirming query confirmed
with both that no controlled study measures whether accessibility
specified before the build lowers defects; the one figure in favour
is a vendor's own audit published without method.

**Card 14, the place in the process and the roles.**
Answered by both, with one part unanswered by both: one
person who is author and builder at once is the subject of no source
read. Claude (two rounds): the stop rule not met; a differently
worded query still brought new material, and the layered model has no
primary source, its author's text and diagram unreadable or refused
in both rounds; the human-centred design standard is read through
secondary pages; clean on citations. Antigravity: reports the stop
rule met; one dead address, cited by F1 and F3. The disconfirming
query found with both the strong current against handing documents
over; claude adds that the current is dated 2011 to 2023 in the pages
opened, aims at the hand-over between separate roles and not at a
description as such, and that each of its sources names a case where
a document stays.

**Card 15, how a proposal is judged before it is built.**
Answered by both. Claude (two rounds): the stop rule met
in its first part only; the design critique and the expert review by
checklist still have no primary source, and the methods' original
papers were not read; twenty-two openings; all twenty-two addresses
open. Antigravity: reports the stop rule met; clean, five
unverifiable. The disconfirming queries confirmed with both that
evaluators disagree (any two between 5% and 65% in a review of eleven
studies) and that models over-report; claude adds a correction:
inspection by heuristics over-reports in human hands too.

**Card 16, where describing an interface in text failed.**
Answered by both; the confirming half found nothing with
either: no documented case of a textual specification of a whole
interface kept as the source of truth of a product over years. Claude
(two rounds): the stop rule met on both conditions; twenty-three
openings; clean, two unverifiable; in the first round no query ran
and fifteen pages were opened by addresses the agent knew. Antigravity:
reports the stop rule met; five dead addresses, cited by five of its
seven findings (F1, F2, F4, F6, F7), among them its sources for the
critique of functional specifications and for the rule on scenarios.

**Card 17, the agent that proposes the description.**
Answered by both; no study compares an agent that asks
with one that does not. Claude: ended on the budget, the stop rule not
met, three routes covered by a description of the tool and not by its
prompt file; all sixteen addresses open. Antigravity: reports the stop
rule met; clean. The disconfirming query confirmed the direction with
both: vague input gives inconsistent and generic output.

**Card 18, what the description cites and does not repeat.**
Answered by both, with one gap in both: no study of a
written description of an interface drifting from the documents it
cites. Claude (two rounds): every route has a primary source; the
stop rule still not met, a differently worded query returning new
sources; twenty-three openings; clean on citations (one line flagged
by the scan for the instance's facts, a bibliographic reference).
Antigravity: reports the stop rule met; two dead addresses, cited by
F1 and F2. The disconfirming queries found with both that a
traceability matrix kept by hand decays and is called not worth its
cost outside regulated work; claude adds that this leaves citation by
identifier standing and argues only against a matrix kept beside the
documents.

**Card 19, the description after the first build.**
Answered by both in four parts unevenly, as the systems
themselves answer them. Claude (two rounds): every route has a primary
source; the stop rule not met, a differently worded query having
changed two findings; twenty-three openings, every quote checked
against the page; all addresses open. Antigravity: reports the stop
rule met; two dead addresses, both help articles of a design tool,
cited by F4 (variants and properties of a shared component). The
disconfirming query was borne out with both: changes of the code come
back into a specification by hand or not at all; claude refines it:
the best documented form of "by hand" is a proposal of the agent that
a person confirms. For overrides claude found the owners' rules of
containment, not reports of chaos.

**Card 20, the description and the test.**
Answered by both. Claude (two rounds): the stop rule met
on both conditions; twenty-two pages; one address counted dead, a
repository browser that answers 406 to the script and that the agent
opened, cited by F1, F2, F3 and F5; one industrial case study known
only second-hand. Antigravity: reports the stop rule met; three dead
addresses, two of them its sources for the Screenplay pattern, cited
by F2, F3 and F4. The disconfirming queries did not overturn the
expected answer with either; claude reports that they bent it three
times.

**Card 21, where a description becomes code.**
Answered by both, one part by assembly only: no maker's
page says outright what a description above its declarative code must
still hold. Claude: ended on the budget, every route with a primary
source, the last queries still returning new material; clean, two
unverifiable. Antigravity: reports the stop rule met; three dead
addresses, two cited by F1, F2 and F5 (the XAML overview and a
university course page used for the claim that the code is the
specification). The disconfirming query found with both the current
that holds the code to be the description; claude adds that its
classical text itself keeps two kinds of document above the code.

**Card 22, what belongs to the whole application.**
Answered by both, one part thinly: a view that differs
by role was found in a modelling standard only, in no platform
guideline. Claude: ended on the budget; the first half of the stop
rule met, the second not in full (the route of role and permission);
clean, three unverifiable. Antigravity (second run): reports the stop
rule met; one dead address, cited by F2 and F7. The disconfirming
query found nothing with either: nobody was found arguing that the
rules of the whole application need no place.

**Findings that cite an address the citation check found dead.**
By the script's mapping of each dead address to its source number and
of the number to the key findings that cite it. A finding may cite
other sources as well.
A finding named here is without support to the extent that it rests
on that address.

- card 2, antigravity (second run): F1, F5 (webproject.guide); F3, F5,
  F7 (the EightShapes plugin page); F3 (GNOME placeholder pages); F6
  (KDE layout and navigation).
- card 3, antigravity (second run): F6 (the UI stack article).
- card 7, antigravity (second run): F1, F3 (two Storyblok pages), F1
  (a Sanity course page); three more dead addresses stand under
  Opened and not used and support nothing.
- card 8, antigravity: F1 (three spec-kit template paths, one source).
- card 10, antigravity: F5 (a vendor's blog on prototype fidelity).
- card 11, antigravity: F2, F3, F6, F7 (the Figma MCP endpoint, which
  answers 405 and is not gone); F2, F7 (a plugin API page); F4 (Style
  Dictionary, Tokens Studio); F5, F7 (Penpot MCP page); F6, F7 (a
  vendor's blog).
- card 12, antigravity: F1, F2, F3 (Material layout overview); F1, F2,
  F7 (Flutter platform adaptations); F1, F7 (an NN/g article); one
  dead address (Windows title bar) cited in no finding.
- card 14, antigravity: F1, F3 (Shape Up, chapter 4).
- card 16, antigravity: F1, F6, F7 and F6 (two Getting Real chapters);
  F2 (a university reading list); F4, F7 (a Cucumber page); F7 (a
  Figma Code Connect page).
- card 18, antigravity: F2 (a DOI); F1, F2 (the uiSchema page of a
  form library).
- card 19, antigravity: F4 (two Figma help articles).
- card 20, antigravity: F2, F3, F4 (an InfoQ article); F2, F3 and F3
  (two Serenity/JS handbook pages).
- card 20, claude: F1, F2, F3, F5 cite the address that answers 406
  (a repository browser refusing the script; the agent opened it).
- card 21, antigravity: F1, F2 (a Microsoft XAML overview); F1, F5 (a
  university course page); one dead address cited in no finding.
- card 22, antigravity (second run): F2, F7 (Android navigation
  principles).

### Answers side by side

Agreement is reported as consistency, never as validation. The measure
of independence of step 6 closes each card: the share of addresses
the two notes have in common and the ratio of common text.

**Card 1, the map of the field and its words.**
Consistent: no survey spans the communities; the
academic model-based tradition (four levels from task to final
interface, the W3C's notes of 2014, IFML 1.0 of 2015), design
practice, and the AI tooling of 2025 and 2026 ("spec-driven
development", three levels of keeping a specification) each map their
own slice; the spec-driven kits have no layer for the interface. Both
draw the three levels and the warning that a specification as the only
source may repeat the fate of model-driven development from the same
article of October 2025: one source, not two. Claude alone: the
standards as a fourth community with ISO/TR 25060:2023; "design specs"
as practice's word, the thing handed over being a design-tool file
with a ticket; DESIGN.md as a format for the visual identity only; the
closed W3C group; "design" standing for three things and "handoff" for
the passage. Antigravity alone: wireflows and prototype
specifications as practice's words; the design tokens format as the
one stable specification at the lowest layer; EARS and the kits' file
names; a recommendation of its own for a layered frame. They differ on
one fact: antigravity states that the W3C's model-based working group
closed after its notes; claude found that not stated on the page it
opened and left it unverified. Independence: 1 of 16 addresses shared,
text ratio 0.02, independent.

**Card 2, the description of one screen.**
Consistent: the recurring core is an identity and a
purpose of the screen, identified elements with their data, actions as
event, processing and target, conditions and errors; structure
outweighs prose; elements are identified by markers on a picture, by
typed IDs shared with the tables, or by a tree of containers; what
several screens share is written once, outside the screen. Both rest
their fullest specimen on the same Japanese public guide. They differ
on three points. States: antigravity gives a five-state list of a
screen as standard; claude finds empty and loading states absent from
the templates it read and the five states a younger list from product
design, one practitioner's book. Position: claude finds that no source
says in text where elements stand, the position being a picture or a
named region; antigravity lists layout and responsive rules as a
recurring field. Europe: antigravity reads a German process model as
carrying a screen specification; claude read the same model and found
no product for a single screen. Antigravity alone: the screen
description as a contract of agreement with stakeholders who are not
technical, written in the words of the business. Claude alone: a
breadboard as the least detailed textual form of a screen; a rule that
an element's code is never renumbered. Independence: 3 of 19, ratio
0.07, independent.

**Card 3, the user's path.**
Consistent: the methods do not compete for one place;
journey maps and story maps stand above the product; use cases and
essential use cases keep the interface out; user flows, wireflows and
breadboards walk a task through screens or places; a state machine
holds behaviour. They differ in what they make of it. Antigravity
splits "path" in two: paths across screens live in a document of
their own that cites the screens, while the states of one screen live
inside that screen's description. Claude finds two families: the
method authors keep the path free of the interface and put a second
artefact between it and the screens (one process names it, a
storyboard traced to the use case, with one navigation map); product
practice fuses path and screens so that no link is left to keep; the
path as a part of each screen only was seen in no source opened.
Claude alone: a step of a flow is often a state of a screen and not a
screen; the author of the textual flow notation calls such diagrams
disposable; three ways of keeping the link (a trace, identity, a
mapping between models), none a standard for text. Independence: 6 of
18, ratio 0.01, independent.

**Card 4, what stands above the screens.**
Consistent: four traditions describe the structure above
screens (the conceptual model as a table of objects with attributes,
operations and relationships; object-oriented UX with its map of
objects and matrix of calls to action; information architecture with
its map of pages and the flow notations; the model-based standards
with nested view containers bound to a domain model); a further school
takes a unit of behaviour, the concept, in place of the object; what
is said to follow from objects first is claimed by the methods'
authors and measured by nobody; no plain-text standard exists for any
of it. Both recommend a hybrid: objects first, then places and paths.
Antigravity alone: in the standards a "screen" is no fixed unit but a
container that nests, so that a page, a dialog and a tab are one
primitive at different depths. Claude alone: the sources disagree on
the unit and none argues for the element; the one workflow of 2025 for
an AI builder that was opened sketches the screens first and lets a
model derive the conceptual model from the sketch; the present process
of object-oriented UX is sold as training and not described in the
open; the only evidence found belongs to the variant that generates
the interface from domain objects (case studies in a thesis).
Independence: 5 of 12, ratio 0.08, independent.

**Card 5, formal languages and standards.**
Consistent, and on facts of status: the model-based
tradition shares one frame of four levels; the W3C's group ended in
Working Group Notes in 2014 and closed; UIML stopped at OASIS short of
a standard; UsiXML and MARIA reached no standard of their own; the
W3C's forms group closed in 2015; IFML stands at 1.0 of February 2015
with no successor; ISO 9241 and the Common Industry Format state
principles and the content of documents, not a language; the W3C
community group of 2025 on a schema for single interface elements
existed and closed on 21 May 2026 without a deliverable. Both: borrow
the concepts, leave the languages. They differ on the reasons for the
absence of adoption. Antigravity gives five structural reasons as the
consensus of academic surveys (modelling overhead, generic output,
broken round trip between model and hand-tuned code, shifting
frameworks). Claude could open none of those surveys and rests the
reasons on a W3C incubator report of 2010 and a position paper of
2017, both by proponents: claims, not measurement; it adds that an
earlier W3C attempt of 2006 failed for who took part, not for
technique. Claude alone, and against the plan's own assumption: by the
W3C group's account practitioners skipped the upper levels and began
at the concrete interface, the level the framework itself calls
platform specific, so that the level common to several platforms is
the one nobody in practice wrote; the group's own advice was to agree
on the model and let the syntax vary. Independence: 2 of 21, ratio
0.06, independent.

**Card 6, an element defined once.**
Consistent: mature design systems define a component
once, apart from any screen, in parts that recur (anatomy, variants,
properties, states, behaviour, accessibility, rules of content);
patterns and page templates are compositions a level above; visual
decisions are named tokens in tiers, their exchange format a stable
community report of 28 October 2025 and not a W3C standard; no
standard exists for the specification of a component, the W3C group
formed for it having closed on 21 May 2026. Both: the first half of
the idea of small definitions stands on firm practice. They differ on
the layering above the component: antigravity says practice compressed
atomic design's five levels into three (components, patterns, page
templates); claude reports the five levels as the shared vocabulary.
Claude alone: the description of a component is two documents kept by
different people, how to make it and how to use it, and a definition
"that carries its function" sits on the border between them; machine-
readable definitions exist as JSON and YAML and carry what can be
enumerated, not the guidance; in atomic design the frame's own
example, a search field, is a composition of three elements; a
component defined once is not always used as defined; a newer current
generates a structured specification from the design tool, read by
agents; no design system was found that keeps one Markdown file per
element as its definition. Antigravity alone: the maintainers' remedy
for drift named by tool (documentation generated from source, design
nodes bound to code). Independence: 4 of 17, ratio 0.02, independent.

**Card 7, a page as a composition of defined blocks.**
Consistent: every family read (block editors, theme
templates of sections, page builders on structured content,
server-driven UI, declarative cards, formats by which an agent sends
an interface, low-code page schemas) holds a page as data that names
blocks defined elsewhere; a page is rearranged by changing an order
or a layout, never a definition; a page outlives the definitions it
cites unless types are versioned; no team was found that publishes one
Markdown file per interface element with page files that place them.
Both: the idea is no outlier, every system read is its relative. They
differ on the count of things kept apart. Antigravity describes two:
the block's type and the page's list of instances. Claude describes
three: the type, the instance on a page with that page's settings,
and the placement; the idea as heard has no said place for what
differs from page to page (a label, a source of data, a variant).
Claude alone: three unrelated systems split the page's data once more
into instances keyed by ID and a separate structure that orders them;
sharing a type across pages is universal, sharing one instance is a
separate decision the makers hedge; one design system publishes a
Markdown file per component package for agents and tells its authors
not to write one for a simple component of a single element, the only
published rule found on which elements earn a file; one tool's
documentation has page files that refer to a Markdown file per
component, with no evidence of use; one team that measured reports
that a single file for everything cost more than guidance fetched per
component and led agents to rebuild components. Antigravity alone:
low-code and agent formats moving from one nested tree to split files
or flat lists, for readable differences in git and for a model as the
writer; a study of October 2026 counting files named DESIGN.md, most
of them technical design and not visual. Independence: 1 of 16, ratio
0.02, independent.

**Card 8, descriptions written for an agent that builds.**
Consistent: no maker prescribes one textual description
of an interface for an agent that builds; the pieces lie in different
files and mean three things by "design"; the design file of the
spec-driven kits is technical design and has no place for the
interface; DESIGN.md is the visual identity as tokens with prose and
knows no screen; skills and instruction files carry taste and process
and take the description as given; servers and registries hand the
agent structured data from a design tool or from code with a
screenshot beside it; between the visual identity and the component
data no vendor prescribes a textual file for a screen. Claude alone:
one older template of a third kit does give a screen and a component
fixed fields in Markdown and sends the picture to a design tool; the
makers divide the work between picture and words and say so, the
words being asked for what a picture hides (empty and error states,
flows, keyboard, accessibility, intent); practitioners report that
long specifications are followed incompletely and are tedious to
review; one file name carries two unrelated meanings. Antigravity
alone: the kits' requirement files written in EARS sentences as the
home of user-facing behaviour; a recommendation to feed the four
inputs agents are built to read. Independence: 0 of 14 addresses
shared, ratio 0.06, independent.

**Card 9, what measurement shows.**
Consistent: no input wins on every axis; a picture
moves the look and where things stand, structure and words move
behaviour, routing and state; look and behaviour are scored apart and
do not go together; results fall from one page to several to a whole
application, with cross-page inconsistency; structured data from a
design tool raises visual fidelity and lowers the quality of the code,
models copying literal values; everything measured is on the web,
nothing for native mobile or the desktop; no single study varies all
the inputs the card names. The two notes rest on almost wholly
different studies (one address shared), which makes the agreement
worth more than usual. They differ on the second direction. Claude: no
study measured a specification written from pictures of screens for
what it gets right, misses and invents; the nearest has models of
early 2025 at about half of the questions on a page's look that people
answer at 94 to 97 percent, failing on alignment, size, position and
spacing. Antigravity: reads benchmarks of change detection and of
screen parsing as that measurement, with models missing most fine
changes of style and inventing widgets and changes. The second reading
answers a neighbouring question (does a model see what is on a
screen), not the card's (how good is a description it writes).
Claude alone: human-written text on an interaction, added to pictures
of its states, was the largest gain of any input change found; for
changing an existing interface text is the better context; the harness
around a model moved the scores as much as the input; left to
themselves models seldom build in components. Antigravity alone:
prose alone fails about four in ten multi-page workflows on the
strongest agents of 2026; an explicit hierarchical intermediate
representation beats direct translation. Independence: 1 of 13, ratio
0.07, independent.

**Card 10, from text to something visible.**
Consistent: four routes lead from text to something
visible (a language that draws a wireframe from text; a generator of
wireframes; a generator of clickable prototypes or code; a component
library rendered in isolation); the first is the only one whose input
is a text file git can compare and whose redraw costs a command, in
low fidelity; the generators spend metered credits on every prompt
and are changed by further prompting or by hand inside the vendor's
tool; the component library needs coded components and so belongs to
the build; process literature places a cheap preview with the
definition and keeps it apart from the build; no comparable figure
for the cost of a change by each route was found. Both note the
method that makes its preview at the definition stage of words alone,
places, affordances and connections, and argues that a picture at
that stage narrows what follows. They differ in how much they make of
the text languages: antigravity recommends building the preview on
deterministic compilation from Markdown definitions; claude calls the
evidence for those languages the weakest of the four routes (an
undated page and a small repository) and a direction to examine, not
a tool to adopt. Claude alone: a practitioner organisation's test of
generators (output follows the detail of the prompt and varies; early
exploration, not something to ship) and a case study in which a
generated clickable prototype moved the test of a complex interaction
from after the build to before it; a page definition that names its
elements is close to a breadboard, so a first preview may be a
reading of the description itself. Independence: 4 of 14, ratio 0.06,
independent.

**Card 11, text and the design tool.**
Consistent: a design is read as structured data over a
documented interface, which does not write layers; writing a design
runs through the tool's plugin interface, lately through the vendors'
servers for agents, at the dominant tool and at the open alternative
alike; components are linked to code by mapping files kept in the
code repository, one way; tokens are the one thing with a neutral
exchange format (the community report of October 2025) and with
movement both ways; bulk access to variables at the dominant tool is
gated to its highest plan; capturing a rendered interface yields flat
layers without components. Both: a text-first description keeps the
path open if it carries identifiers of its own, names of components
and of their properties and values, and tokens by name. Claude alone:
none of the connections is a synchronisation, each a one-way transfer
that someone starts; writing has no document format at either tool,
it is an agent running scripts with an instruction file, in beta by
the vendor's own word, so that a text-first description need not
anticipate a tool's file format; the tools assign their identifiers
at creation, so a binding to them can only be recorded afterwards and
is best kept apart from the description; no counterpart of the
component-to-code link was found at the open alternative. Antigravity
alone: five invariants stated as rules for the Markdown format, among
them layout in the terms of flexible boxes and grids and a boundary
between visual variants and runtime state; its own synthesis, and
resting on the addresses named above. Independence: 1 of 15, ratio
0.02, independent.

**Card 12, the platforms.**
Consistent: the owners prescribe different things per
platform for navigation, input, windows and the system's conventions;
adaptive behaviour is specified by named size classes of the app's
window and never by device, with a small vocabulary of operations
(reposition, resize, reflow, show or hide, replace, re-architect) and
a few named layouts; the web standards name no platform, only
conditions on a viewport or a container and on the kind of pointer;
the behaviours of the system and the controls of input follow the
platform while identity and content stay shared. Both, and against the
plan: the four targets are not four things of one kind. The space
available, the platform's idiom and the input are separate axes, and
the mobile web is the web in a narrow window with a coarse pointer.
Both recommend one description with a rule per size class and a block
of platform considerations held to the idiom. They differ on how
settled the shape is. Antigravity: platform owners and design systems
"do not write a separate specification per platform", one dominant
pattern across five systems. Claude: both shapes are documented in
primary sources, one description with platform variants and one
design language with documentation per platform, the latter called
"not uncommon" by one owner's own guide; the one account of a change
of shape runs toward one definition; no source compares the two by a
measured outcome. Claude alone: the owners' size classes differ in
number and unit (two, five and three), so no one vocabulary can be
borrowed for all; the borders moved within the year of the research;
no owner's guideline for the web as a platform was found.
Independence: 1 of 15, ratio 0.05, independent.

**Card 13, what the description owes every user.**
Consistent: the properties decided at design time are
the name, role and states of an element, its keyboard behaviour,
focus order, headings and regions, contrast and target size; the
authoring practices give a rich component a definition of its own
(keyboard interaction; roles, states and properties); public
annotation kits state these as stamps laid over a frame in a design
tool; public administrations specify interface text by general rules,
a cited style guide and wording bound to the component, placeholders
refused and errors given a fixed structure; internationalisation is a
step of design: a text with a variable is specified whole and never
concatenated, translated text grows, direction and language are
stated. Antigravity packages this as four contracts beside the layout
and recommends an application-wide baseline with deltas per element.
Claude differs on the premise: the standards state what must be true
of the built interface, not what a description written before the
build must contain, and no source opened prescribes the content of
such a description. Claude alone: the W3C's draft mapping gives about
three fifths of its accessibility tasks to design and content roles;
the three subjects of the card are one in the standard, wording and
language standing inside the accessibility criteria; what a reusable
element carries once and what each use must state are different
things, the name being of the second kind; a component has texts that
are never shown; two public bodies write accessibility as acceptance
criteria that state an outcome and refuse to name the solution,
against declarations that name role, state and key; one public
library already keeps accessibility acceptance criteria as one
Markdown file per component, for the web and for native mobile, which
is the idea under test in use on this card's ground. Independence: 3
of 13, ratio 0.02, independent.

**Card 14, the place in the process and the roles.**
Consistent: the interface is worked out before its code
in every source; inside the work, structure and flows come before
surface; what reaches the builders splits into the visual and spatial
part, now largely carried by tokens and inspection tools, and the
rules of behaviour and state, which still need words; lean and solo
practice drops the high-fidelity picture made as a contract and the
heavy specification and keeps the rough statement of what stands on a
screen, the path between screens, the prototype and the shared
library. Both recommend a document of its own below the business
requirements and beside the solution design, light in its first
shape. They differ on user stories. Antigravity: in dual-track
practice and in the spec-driven methods the interface work precedes
the stories and the stories are sliced around the agreed screens, so
the description belongs before the user stories in the chain. Claude:
the sources split three ways, the stories first and the interface
drafted from them and checked against them, the design first and the
items to be built coming out of it, or story and screen written
together; in one practice the screen and its stories are one unit, a
page each. The engines also differ on the frame: antigravity presents
one order of work; claude finds that established method places the
work in two ways that contradict each other, as a stage of its own
below the requirements or as work that runs beside the build a step
ahead of it. Claude alone: the lean cut is paid for with a team in
constant conversation and the same sources bring the document back
where the conversation is missing, which is the case of a builder who
cannot be spoken to (its own inference for a coding agent); a study
of 2024 measures a model checking a prototype against the user
stories. Independence: 4 of 15, ratio 0.09, independent.

**Card 15, how a proposal is judged before it is built.**
Consistent: the established methods are the usability
inspections (heuristic evaluation, cognitive walkthrough, inspection
of consistency and of standards), with the expert review and the
design critique beside them; by their own literature none needs a
running system or a picture, a detailed description being a
sufficient input; what each needs is what stands beside the
description, the users, a task and the written sequence of its
actions for the walkthrough, agreed objectives for the critique, the
standard for a standards inspection; models as evaluators find real
problems, report many that are none, with precision below the
human's, and are weakest across screens and on conventions; a model
walking an interface completes the tasks better than people do and so
under-reports the points of failure unless asked to predict them. Both
cite the same review for the disagreement of evaluators and the same
family of studies for the models: partly one body of sources. They
differ on text as an input for a model. Antigravity reads one study,
in which a mockup was turned into a structured text form before a
model inspected it, as showing that structured text out-performs a
picture for a model's inspection. Claude: models were run as
evaluators on four kinds of input, a structured form of a mockup,
source code, screenshots and recordings, and never on a prose
description; no page opened compares a prose description with a
picture. Claude alone: one difference between paper and a running
system was measured, that what is missing from a design is harder to
find on paper; designers asked to rate a model's findings barely
agreed with each other, so the yardstick is as unreliable as what it
measures; a model's feedback on one design worsens over rounds; a
long checklist is reported to narrow a model reviewer; "expert review
by checklist" has no method of its own in the pages opened.
Independence: 1 of 15, ratio 0.03, independent.

**Card 16, where describing an interface in text failed.**
Consistent: the heavy written specification of an
interface is recorded as failing by practitioners (it does not match
the product, agreement on paragraphs is illusory, it decides too
early, it is seldom read and cannot be tested); generation of
interfaces from models did not find acceptance (unpredictable result,
loss of control, a new language, a low ceiling), and the W3C's group
on it closed without a standard; writing of 2025 and 2026 draws the
same line to specifications written for coding agents; the critics
put the prototype, the interface itself or the code in the place of
the text, and each keeps a remainder of text; a description kept
beside the product drifts when updating it is a second piece of work;
what survives as text is narrow: generated from the same source as
the product, bound to tests, or held to a small scope. Both recommend
narrowing what the text is the source of truth of. They differ on the
rule for scenarios bound to tests. Antigravity gives it as consensus
that text written in terms of screen mechanics breaks and text at the
level of the business rule holds. Claude held the same after its
first round and found it contested in the second: a doctoral thesis
of 2025 finds no academic evidence behind the rule and shows that
people outside software write scenarios in the words of the interface
more easily, and a survey of 75 practitioners finds that text bound to
tests has the maintenance troubles of any test suite. Claude alone:
whether the failure belongs to the text or to the way it is kept is
contested, the one defender read not denying the drift and freezing
his own specification at code complete; the sources place the failure
in a second copy that is costly to update, whatever its medium, so
that moving to a design tool or a prototype does not remove it; the
part that broke everywhere is the part that says where things stand
on a screen; the critics' own exceptions (a builder with little
contact with the designers) describe a coding agent; the sources use
"behaviour" for two things, how an interface responds in use and the
rule the system keeps; a practitioner argues in 2026 that Markdown
cannot be the contract since nothing in it can be judged invalid by a
machine. Antigravity alone: a study of November 2026 over 36,906
valid DESIGN.md files, nearly half with a components heading and no
structured component tokens and most with unreferenced tokens, and an
observation of 283 agent sessions in which stale Markdown
specifications caused silent failures, the agents trusting outdated
text. Independence: 4 of 20, ratio 0.04, independent.

**Card 17, the agent that proposes the description.**
Consistent: what the documents above leave open falls
into a few kinds (who the product is for and the context of use, the
behaviour the requirements are silent on with the empty, error and
loading states, navigation and layout, the visual identity or the
design system that binds, accessibility and devices); the published
workflows contain invention less by asking more than by standing
files for the visual identity, by assumptions written down and
marked, and by a gate of approval before anything is built; a
question comes with the agent's own recommended answer; the open
format for agents covers the visual identity only; the spec-driven
kits fold the interface into other documents or, in one method, give
it a document of its own made before or beside the technical design.
They differ on the order of asking. Antigravity: a top-down sequence
of stages, three to five questions a turn, then a short blueprint to
confirm. Claude: the pattern is read, pre-fill, then ask by impact; no
source read prescribes a fixed, ordered list of questions for screens
and flows, and screens are not asked about at all but proposed as two
or three alternatives and judged by seeing them. Claude alone: the
sources disagree on how much asking is right, one skill having the
agent infer and confirm only the subject; a workflow that pushes for
visuals can itself make the agent invent (an open issue against one
method); "not decided yet" needs a state of its own; no workflow read
takes requirements, user stories and a solution design together as
its named inputs, asks about platform conventions, or writes a
definition per element with a page that places them. Antigravity
alone: the cap on questions as a published rule of one kit; the
tendency of a model to commit to a guess instead of asking, named in
preprints. Independence: 1 of 16, ratio 0.01, independent.

**Card 18, what the description cites and does not repeat.**
Consistent: established practice gives each thing an
interface description would otherwise repeat a home of its own and a
handle to cite it by (a glossary for terms; a data model and
dictionary for fields; a list of business rules; requirements on
access; a contract for the service behind the screen, its errors
included); where an interface is described in a form bound to a
schema, the reference is a path into the data definition and the
constraints stay with the data; the description keeps the control and
its place, its label, help and error wording, the trigger and the
response to an action, and what a rule or a permission does on the
screen (shown, hidden, enabled, read-only); where a condition of
showing or enabling lives is placed differently from source to
source, in the interface's description or in the data model. Both
recommend citation at the element by the identifier the cited thing
already has, checked by a script, with no matrix. Claude alone:
citations are themselves copied, "reference" being the second most
often cloned kind of content in a study of 28 industrial
specifications (13.6 per cent of their text cloned on average, the
interface among the three kinds most often cloned), so a citation
should be a bare identifier; the flow also runs upward, a rule first
seen while a screen is described having no home above yet; one rule
is applied at several moments of an interface, which is where a
description is drawn into restating it; from requirements to the
elements of an interface the link is described as missing or made by
hand; a language model found unimplemented user stories in a
prototype at .85 accuracy and matched stories to components at .68
(a preprint of 2024); developers who fear drift leave a constraint
out of the interface altogether. Antigravity alone: one requirements
method that inverts the direction and derives the data from early
screens. Independence: 4 of 19, ratio 0.05, independent.

**Card 19, the description after the first build.**
Consistent: a change to a text specification is read in
two ways, as git's difference on a branch or as a delta that is a
document of its own (added, modified, removed) which a command later
merges into the standing specification; nothing in the kits opened
writes a change of the code back without a person; a shared element
varies in grades, a variant declared in its definition, an override
at the place of use limited to a declared surface, and detachment,
which ends the link; the text kits and the component files do not
show the reach of a change by themselves; shared definitions in code
are versioned by semantic versioning. Both conclude that a definition
per element is workable only with a stated rule of variation and with
a reach of change that can be computed from stable identifiers.
Claude alone: the design tool does show the reach, to the user of the
element when the update arrives and to its owner as usage; two
unrelated systems key an override to the name of a part inside the
shared element, and renaming the part breaks the link, so the parts
need stable names before a page may vary them; owners read a repeated
override as a missing variant and count the detachments; what a
specification is after the build differs by kit, the record of one
change or a standing text; one kit documents a procedure in which the
agent that builds raises an amendment and the developer confirms it;
the one case with figures concerns formal specifications, where ten
weeks of work did not bring code and specification to match.
Antigravity alone: the delta read as the answer to line-by-line
differences that hide whether a change is meant; one kit's separate
shape for a fix (present behaviour, expected behaviour, unchanged
behaviour). Independence: 1 of 20, ratio 0.03, independent.

**Card 20, the description and the test.**
Consistent: testing describes an interface in layers,
what the user achieves, the path in terms of tasks, and the elements
with the technical steps on them; user paths refer to the middle
layer, never to elements; the element is a small unit of its own in
every pattern read, a name and the way to find and work the thing; a
unit survives a change of the interface when it is defined by what
the user does or perceives (a role, an accessible name) and breaks
when it is defined by layout, markup or the kind of widget; a page
object the size of a page that mixes locators, workflows and
assertions grows unmaintainable; a textual template of a page's
structure, roles and names in order and nesting, matched by a machine
against the built page, is the nearest thing to a description a build
can be held to. Both recommend keeping the small definition per
element within these boundaries: what the user can do and perceive
through it and what it is called, not where it stands or how it is
found. They differ on the evidence and on one rule. Antigravity gives
as measured that the layer of units costs more to write and
substantially less to maintain, from one industrial case study cited
second-hand, and as consensus that scenarios written at the level of
elements break while those at the level of tasks survive. Claude
could not read that case study; the one family of controlled
experiments it read found that the layer costs more than it returns
until a suite is about ten times larger; and a controlled experiment
of 2025 found scenarios written in terms of interface elements easier
to write and to read, above all for people who are not software
practitioners. Claude alone: nothing opened checks a build against a
text directly; a test bound to a text needs binding code, written by
hand or, in one tool's current documentation, generated and repaired
by agents from a Markdown plan; a comparison of pictures checks a
build against an earlier build a person approved, not against a
description; one vendor calls a definition per element premature
where the element serves a single action; "declarative" is relative,
every layer being the what of the layer below, and the interface is a
legitimate domain of a text of its own. Antigravity alone: component
stories as a unit that joins the description of an element in a named
state, its interaction test and its visual baseline. Independence: 5
of 14, ratio 0.02, independent.

**Card 21, where a description becomes code.**
Consistent: the declarative languages of all four
platforms state readably which elements a screen holds, how they
nest, how they look and what data each shows, and their makers call
this a description; previews render one component or screen in
isolation from parameters and sample data declared in code; what the
code does not hold, and a layer above must, is what precedes it and
spans it: the purpose and the rationale, the paths across screens,
the names, the wanted differences between platforms. Both recommend
that the description above not restate the nesting, the layout and
the values of the look, which the code states readably and shows at
once. They differ on what the languages keep apart. Antigravity: all
six separate view structure from state, and one of them enforces a
border inside the language by splitting a purely declarative file
from the file with logic. Claude: that holds for the markup family
only; the component languages hold structure, style and local logic
together on principle and keep apart only who owns the state, one
maker calling separation by file type a misreading of separation of
concerns; a description above may have to choose between the two
cuts, by concern or by component. Claude alone: the border runs where
a general programming language enters the notation; the isolated
preview has stated limits, and its maker turns them into a rule for
how a screen is written, state in and events out; a second kind of
preview changes the running application because real state is hard to
imitate before the build; formats in which an agent emits an
interface at run time share the anatomy (a declarative tree over a
catalogue of approved components) and are not a description handed to
a build; one research prototype puts a storyboard, a data model and
skeletons of screens above the code. Antigravity alone: a vendor
withdrew in 2025 its tool for packaging designs into an intermediate
form for its declarative language (its source for this does not open
and is cited in no finding). Independence: 4 of 15, ratio 0.03,
independent.

**Card 22, what belongs to the whole application.**
Consistent: the persistent frame of navigation,
addresses and deep links, windows and tabs, notifications and events
that arrive unasked, and offline or degraded states are written by
the platform owners and the standards as rules about the application
and not about a screen; role is a context declared once; the rule of
placement is to say a thing once at the level where it holds and let
the lower level refer upward; no template of an interface
specification with a named section for all of it was found. Both
recommend a place above the screens that a screen cites. They differ
on what stands between. Antigravity: the screen is not a stable unit
across window sizes, a list and its detail being two screens on a
narrow window and two panes of one on a wide one, so the unit should
be the view container or pane, composed by a layout of the
application. Claude: the sources have three levels and not two; a
section stands between the application and the screen (a nested
layout, a nested navigation graph, a nested container), and a frame
that holds for one area only has its place there. The two finds are
compatible and neither engine has the other's. Claude alone: much of
this behaviour is the platform's to decide and not the application's
to describe, so a description may owe, per target, a line saying
which conventions it takes as they are, writing only where it
departs; in the modelling standard the role, the device and the
position are one mechanism. Independence: 1 of 15, ratio 0.06,
independent.

### Unexpected, gathered

Shown before any judgement, sorted by one test.

Finds that reconfigured a question or brought a mechanism from
elsewhere:

- The unit. A "screen" is not a stable unit: a list and its detail
  are two screens in a narrow window and two panes of one in a wide
  one, and the standards model a nested container of which a page, a
  dialog and a tab are one kind at different depths (cards 4 and 22,
  antigravity). Between the application and the screen stands the
  section, and a rule lives at the highest level where it holds (card
  22, claude). A step of a path is as often a state of a screen as a
  screen (card 3, claude). One school takes a unit of behaviour that
  spans screens (card 4, both).
- Three things, not two. Systems that hold a page as blocks keep apart
  the type of a block, its instance on a page with that page's
  settings, and its placement; the idea under test names two (card 7,
  claude). What a reusable element carries once and what each use must
  state are different things, the accessible name being of the second
  kind (card 13, claude). Two unrelated systems key a page's override
  to the name of a part inside the shared element, and a renamed part
  loses its overrides (card 19, claude).
- Position. No source read says in text where the elements of a
  screen stand; the position is a picture or a named region (card 2,
  claude). The part of textual specifications that broke everywhere is
  the part that says where things stand (card 16, claude).
- The second copy. What fails is a second copy that is costly to
  update, whatever its medium, so that moving from text to a design
  tool or a prototype does not remove the trouble and staying with
  text does not cause it (card 16, claude).
- The platforms. The four targets are points on three axes, the space
  available, the platform's idiom and the input; the mobile web is the
  web in a narrow window with a coarse pointer (card 12, both). Much
  behaviour of the whole application is the platform's to decide and
  not the application's to describe (card 22, claude).
- The level nobody wrote. By the W3C group's own account practitioners
  of the model-based tradition skipped the upper levels and began at
  the concrete interface, the level the framework calls platform
  specific (card 5, claude).
- "Design". The word stands for three things, and none of the three
  files so named in the AI tooling describes screens and behaviour
  (cards 1, 8 and 17, both).
- Picture and words. Look and behaviour are scored apart and do not go
  together (card 9, both); the makers divide the work, the layout by
  picture and the words for what a picture hides (card 8, claude).
- Asking. In the published workflows screens are not asked about but
  proposed as alternatives and judged by seeing them (card 17,
  claude); a workflow that insists on visuals can itself make the
  agent invent, and "not decided yet" needs a state of its own (card
  17, claude).
- A preview of words. One method makes its preview at the definition
  stage of words alone and argues that a picture at that stage narrows
  what follows (card 10, both); a page that names its elements is
  close to it (card 10, claude).
- Judging. A description is judged against something that has to be
  written down too: the users, a task and its actions, the objectives
  (card 15, claude). A model walking an interface completes tasks
  better than people and so under-reports the points of failure (card
  15, both).
- The design tool. Writing a design into the tool is an agent running
  scripts with an instruction file, not an import of a format (card
  11, claude; the second engine has the same servers as a new path).
- Two documents. The description of a component is two documents kept
  by different people, how to make it and how to use it (card 6,
  claude).
- User stories. In some processes the interface work precedes the
  user stories and they are sliced around the agreed screens (card 14,
  antigravity); in one practice a screen and its stories are one unit
  (card 14, claude).
- Outcome or declaration. Two public bodies write accessibility as
  criteria that state an outcome and refuse to name the solution,
  against declarations of role, state and key; and the three subjects
  of card 13 are one in the standard (card 13, claude).
- The delta. In one kit the difference is the document a person and
  an agent write and review, and the standing specification is what a
  command computes from it (card 19, both).
- Upward. A rule is sometimes first seen while a screen is described
  and has no home above yet (card 18, claude).
- A text a build can be held to. A template of a page's structure,
  roles and accessible names in order and nesting, is matched by a
  machine against the built page (card 20, both).
- Which elements earn a file. One design system that keeps a Markdown
  file per component package for agents forbids one for a simple
  component of a single element (card 7, claude); one vendor calls a
  definition per element premature where the element serves a single
  action (card 20, claude); one public library keeps accessibility
  criteria as one Markdown file per component, for the web and for
  native mobile (card 13, claude).

Finds that add a source to a point already made:

- The W3C community group on a schema for single interface elements,
  called in August 2025 and closed on 21 May 2026 without a report,
  stands in the notes of cards 1, 5 and 6 on both engines: one fact.
- The warning that a specification as the only source may repeat
  model-driven development stands in the notes of cards 1, 8, 16, 18
  and 19: one article of October 2025, cited by many.
- A study of files named DESIGN.md on a code host (cards 7 and 16,
  antigravity only), a vendor's withdrawal of an intermediate design
  package (card 21, antigravity, its source not opening), a generator
  that put a stage of text before its own preview (card 10, claude).

### Not found, gathered

- No synthesis across the field, and no standard for describing an
  interface in text as a whole (card 1); no standard for the
  specification of one component (cards 5 and 6); no file for a
  screen in text prescribed by any maker for an agent that builds
  (card 8); no template with a named section for the behaviour of the
  whole application (card 22); no plain-text standard for objects,
  information architecture or flows (cards 3 and 4).
- No team that publishes one Markdown file per interface element with
  page files that name the elements and say where they stand (card
  7, both engines, the session model with six differently worded
  queries).
- No documented case of a textual specification of a whole interface
  kept as the source of truth of a product over years (card 16).
- Nothing measured on: objects first against screens first (card 4);
  one description with platform variants against one per platform
  (card 12); prose against a structured specification as the only
  input, and tokens or a component library as an input (card 9); a
  specification written by a model from pictures of screens (card 9,
  where the engines disagree whether neighbouring benchmarks count);
  the cost of a change by each route to a preview (card 10); whether
  accessibility specified before the build lowers defects (card 13);
  an agent that asks against one that does not (card 17); a written
  description of an interface drifting from the documents it cites
  (card 18); how often a prose specification drifts from its code or
  overrides are lost (card 19); units at the level of an element
  against units at the level of a task under change (card 20); a
  model evaluating a prose description (card 15).
- Nothing measured for native mobile or the desktop in the studies of
  models building interfaces (card 9), and no preview of the text
  wireframe languages for a native platform (card 10).
- No round trip of a layout without loss between a text or code source
  and a design tool (card 11).
- No source on one person who is author and builder at once (card
  14); no workflow that takes requirements, user stories and a
  solution design together as its named inputs for an interface, or
  that asks about platform conventions (card 17).
- No owner's guideline for the web as a platform (card 12); no
  platform guideline on a view that differs by role (card 22).
- Primary texts that could not be read and on which the notes
  therefore rest on secondary pages or abstracts: the ISO standards,
  which are sold (cards 1, 5, 14); the layered model of user
  experience in its author's text (card 14); essential use cases in
  their authors' text and the academic surveys of description
  languages (cards 3 and 5, session model); the original papers of
  the inspection methods and a source for design critique and for
  review by checklist (card 15); one industrial case study on page
  objects (card 20).

### Claude's view

What follows is Claude's own and is marked so; nothing in it is a
finding of a note. Where a statement is verified, the check is named;
the rest is a reading or a hypothesis.

On the evidence. Verified by the scripts of step 6: every card has
two notes the measure finds independent; the session model's notes
cite no address that is gone (one answers 406 to the script); the
second engine's notes cite addresses that do not open in fourteen of
twenty-two. Not verified by anything: the content of the pages, which
both engines read through summarising tools; the session model's
notes say in several cards that the quotes were compared with the
page, the second engine's do not. My reading: the facts of status
(which standard ended where, what a format covers) are firm, since
both engines give them from different pages; the rules of thumb of
practice are claims, most of them never measured; and a figure that
only the second engine reports is a lead.

The answer in one sentence, a reading: the thing wanted does not
exist ready, its parts do, and the parts agree with each other more
than their communities know.

What the text should be the source of truth of, a reading of cards 8,
9, 10, 16 and 21 together. Not the layout. Where things stand broke
in every textual specification, travels better in a picture, and is
stated readably by the declarative code of every target platform. The
text should hold what a picture hides and what spans screens: what
the application and each screen are for; the terms and objects, cited
from the documents above; the paths; for each screen its regions by
name and order, the elements it uses, its states with the empty, the
loading and the failed among them, its actions as event, response and
target; the wording, the hidden texts included; what each use of an
element must state for accessibility; the differences between
platforms that are wanted; and what is still open, with "deferred on
purpose" as a state of its own.

A candidate shape, put together from fragments and found whole
nowhere; a hypothesis to be tried, with where each part was found:

- An application part: the frame of navigation, addresses, roles,
  notifications, offline behaviour, and per target platform a line on
  which conventions are taken as they are (card 22; the levels and
  "once, cited from below" from platform guidelines and one
  modelling standard). A section between it and the screens where an
  area has a frame of its own.
- Paths as items of their own, in words: places, what can be done at
  each, where it leads; each citing the goal it realises in the
  documents above and the screens, or states of screens, it passes
  (card 3; the breadboard, and one process's storyboard traced to a
  use case).
- A screen as an item: identity, purpose, named regions in order, the
  elements it uses as named instances with what differs here, states,
  actions, citations of rules and data by their identifiers (card 2,
  the public Japanese guide for the identifier shared by every table
  and for the action table; card 7 for the instance; card 18 for the
  citation).
- An element definition only for an element that recurs or has
  settings, states or behaviour of its own: what the user can do and
  perceive through it, its named parts, its variants, and the surface
  a page may override (card 6 for the parts; card 19 for the grades
  of variation and the stable names of parts; cards 7 and 20 for the
  threshold; card 20 for defining it by what the user does and not by
  the widget).
- Identifiers of its own for all of these, stable and never derived
  from position or wording, with any binding to a design tool kept
  apart and empty at first (card 11).

On the idea of a definition per element, a reading: it stands as a
model of reference and not at the grain of "every element". As heard
it has two parts where the systems that live by it have three; it
needs the instance, a rule of variation and a threshold. "Where they
stand" reduces in text to a named region and an order.

On the user's paths, a reading: they stand apart and inside, at
different levels. Journey maps and story maps are no part of the
description. A path at the level of a goal belongs to the documents
above and stays free of the interface. The description carries the
flows through the interface as items of their own that cite screens.
The states of one screen live with the screen.

On seeing it, a hypothesis: the cheapest preview is the description
read as a breadboard, and it costs nothing. A drawn low-fidelity
preview made from the text belongs to the side of the definition and
not of the build; the tools for it are small and their evidence the
weakest in the bundle, so it is a direction to examine and not a tool
to adopt. A generated clickable prototype earns its cost where a
still picture cannot answer. Every preview is derived, and none
becomes the source.

On the agent that proposes, a reading with one observation of my own:
the pattern the published workflows share (read what stands above,
say what it already settles, ask what is left by weight with a
recommendation, mark every assumption until it is judged, show
screens as alternatives) is the way this framework already works
between its principal and its agent. The observation is mine and
unverified against the framework's own text in this note.

On keeping it true, a hypothesis: citations as bare identifiers that
a script checks; the reach of a change to a shared element computed
from the identifiers; a change reviewed as a delta with its reason,
which the framework's records of history already are; and, once
something is built, a template of structure by role and name as the
one text a machine can hold a build to.

Open, and the principal's to decide; the notes give material and no
answer: where the description stands against user stories, before
them or tied to them screen by screen (card 14, the engines differ);
whether accessibility is written as declarations or as outcomes (card
13); where a condition of showing or enabling lives, in the
description or with the data (card 18); and whether the whole is a
layer of the framework or a tool beside it. On the last my view, a
hypothesis: the description, its citations, its reviewers and its
records are the framework's kind of work; previews and the connection
to a design tool are tooling that can be added to either.

What I propose, through the framework's own commands and on the
principal's word, never silently: to try the candidate shape on the
first project before anything of the framework changes, starting
from the pictures that project already has and describing a few
screens with the application part and the paths; to see what a
builder asks back; and only then to write the brief of a new kind of
artefact in the framework's own project, in the order the framework
has for a kind that needs a trial first.

## Notes

The files of the bundle, each with the packet folder under
`tmp/research/2026-11-21-describing-ux-ui-in-text/` it was made from.
The notes of the second engine of cards 2, 3, 6, 7 and 22 are second
runs; the notes of the session model of cards 12 to 16 and 18 to 20
are those of the second round; the note of the session model of card
1 was typed over by hand from the agent's return.

- `card-01-map-of-the-field.antigravity.md`: folder `01-map-of-the-field`.
- `card-01-map-of-the-field.claude.md`: folder `01-map-of-the-field`.
- `card-02-one-screen.antigravity.md`: folder `card-02-one-screen`.
- `card-02-one-screen.claude.md`: folder `card-02-one-screen`.
- `card-03-users-path.antigravity.md`: folder `card-03-users-path`.
- `card-03-users-path.claude.md`: folder `card-03-users-path`.
- `card-04-above-the-screens.antigravity.md`: folder `card-04-above-the-screens`.
- `card-04-above-the-screens.claude.md`: folder `card-04-above-the-screens`.
- `card-05-formal-languages.antigravity.md`: folder `card-05-formal-languages`.
- `card-05-formal-languages.claude.md`: folder `card-05-formal-languages`.
- `card-06-element-defined-once.antigravity.md`: folder `card-06-element-defined-once`.
- `card-06-element-defined-once.claude.md`: folder `card-06-element-defined-once`.
- `card-07-page-of-blocks.antigravity.md`: folder `card-07-page-of-blocks`.
- `card-07-page-of-blocks.claude.md`: folder `card-07-page-of-blocks`.
- `card-08-described-for-a-builder.antigravity.md`: folder `card-08-described-for-a-builder`.
- `card-08-described-for-a-builder.claude.md`: folder `card-08-described-for-a-builder`.
- `card-09-measurement.antigravity.md`: folder `card-09-measurement`.
- `card-09-measurement.claude.md`: folder `card-09-measurement`.
- `card-10-text-to-preview.antigravity.md`: folder `card-10-text-to-preview`.
- `card-10-text-to-preview.claude.md`: folder `card-10-text-to-preview`.
- `card-11-design-tool.antigravity.md`: folder `card-11-design-tool`.
- `card-11-design-tool.claude.md`: folder `card-11-design-tool`.
- `card-12-platforms.antigravity.md`: folder `card-12-platforms`.
- `card-12-platforms.claude.md`: folder `card-12-platforms`.
- `card-13-every-user.antigravity.md`: folder `card-13-every-user`.
- `card-13-every-user.claude.md`: folder `card-13-every-user`.
- `card-14-process-and-roles.antigravity.md`: folder `card-14-process-and-roles`.
- `card-14-process-and-roles.claude.md`: folder `card-14-process-and-roles`.
- `card-15-judging-a-proposal.antigravity.md`: folder `card-15-judging-a-proposal`.
- `card-15-judging-a-proposal.claude.md`: folder `card-15-judging-a-proposal`.
- `card-16-where-text-failed.antigravity.md`: folder `card-16-where-text-failed`.
- `card-16-where-text-failed.claude.md`: folder `card-16-where-text-failed`.
- `card-17-proposing-agent.antigravity.md`: folder `card-17-proposing-agent`.
- `card-17-proposing-agent.claude.md`: folder `card-17-proposing-agent`.
- `card-18-cites-not-repeats.antigravity.md`: folder `card-18-cites-not-repeats`.
- `card-18-cites-not-repeats.claude.md`: folder `card-18-cites-not-repeats`.
- `card-19-after-the-first-build.antigravity.md`: folder `card-19-after-the-first-build`.
- `card-19-after-the-first-build.claude.md`: folder `card-19-after-the-first-build`.
- `card-20-description-and-test.antigravity.md`: folder `card-20-description-and-test`.
- `card-20-description-and-test.claude.md`: folder `card-20-description-and-test`.
- `card-21-description-becomes-code.antigravity.md`: folder `card-21-description-becomes-code`.
- `card-21-description-becomes-code.claude.md`: folder `card-21-description-becomes-code`.
- `card-22-whole-application.antigravity.md`: folder `card-22-whole-application`.
- `card-22-whole-application.claude.md`: folder `card-22-whole-application`.
- `deep-research.copilot.md`: no note of a card and made from no
  packet. The report of an outside deep research (Microsoft Copilot)
  that the principal ran on one assignment written from this plan for
  the deep research built into such tools; pasted on 2026-11-21, the
  style block of the page left out, the rest word for word. Its
  sources carry no addresses and were checked by no script.
- `deep-research.gemini.md`: no note of a card and made from no
  packet. The output of Gemini's deep research, by the principal's
  word, placed in the bundle by him on 2026-11-21 and kept word for
  word, in the language it arrived in, which is not English. It names
  no source and carries no address, and it does not have the shape of
  report that the assignment written from this plan asks for; whether
  it was run on that assignment was not verified.
- `deep-research-prompt.md`: no note. The one assignment written from
  this plan on 2026-11-21, on the principal's word, for the deep
  research built into outside tools: the frame, the twenty-two
  questions in the order of their groups, the rules for sources and
  the shape of report asked for. The two reports beside it are what
  came back. Placed in the bundle after the synthesis, with them.
