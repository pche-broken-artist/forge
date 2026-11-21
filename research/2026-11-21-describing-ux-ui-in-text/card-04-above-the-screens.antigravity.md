---
date: 2026-11-21
project: forge
topic: What stands above the screens
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 4; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":49428,"output_tokens":15143,"thinking_tokens":7799,"cache_read_tokens":161414,"total_tokens":64571}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-04-above-the-screens
status: immutable
---

# How practice and literature describe the structure above single screens

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Across four traditions—interaction-design conceptual modelling,
Object-Oriented UX (OOUX), information architecture (IA) with flow
mapping, and formal model-based user interface (MBUI) standards—the
structure above single screens is decomposed into two distinct layers
before any screen layout (interface design in a design tool) is drawn:
first, an object or concept layer (domain objects with their
attributes, user-facing actions, and relationships); second, a
container and topology layer (abstract view containers, sitemaps,
navigation rules, wireflows, and state matrices). These layers are
written in text as structured glossaries or concept specs, attribute
and call-to-action (CTA) matrices, indented hierarchy tables, state
transition tables, and XML/XMI serialisations. Authors across these
traditions claim that defining objects before screens prevents UI-driven
feature creep, aligns the user's mental model with the technical domain
model, and keeps terminology and component representations consistent
across screens. The disconfirming query confirmed practitioner doubts
about upfront cost, stakeholder friction, and rigidity on linear,
procedural workflows (such as wizards or checkout funnels), supporting
a hybrid unit where objects govern persistent domain entities and flows
govern transient procedures. Because direct HTTP fetches were blocked
by the environment's command policy, all findings rest on summarised
fetches from the search tool (tertiary summaries of primary method
literature and standards).

## Question

#### Card 4: What stands above the screens
- **Question:** How do practice and literature describe the structure
  above single screens (the conceptual model of objects with their
  attributes, actions and relationships; the information architecture;
  the navigation and the map of screens), in which textual forms, and
  what do they claim follows from describing objects before screens?
- **Why it matters:** it decides what the unit of the description is: a
  screen, an object or an element.
- **What would answer it:** method literature by its authors.
- **Where to look:** the literature on conceptual models in interaction
  design; object-oriented UX; information architecture; how domain
  modelling is tied to interface design. Search words from card 1:
  "design specs", "wireframe annotations", "prototype specifications",
  "wireflows", "state matrix"; and the model-based words "abstract user
  interface", "concrete user interface", IFML's "view container", "view
  component", "interaction flow".
- **Disconfirming query:** "object-oriented UX criticism"; expected:
  little published criticism, some doubt about cost.
- **Stop rule:** nothing new from a differently worded query and every
  route has a primary source; ten to fifteen pages opened.

**Baseline to beat:** A generic summary that merely defines
"information architecture" and "conceptual models" without naming the
specific layers above screens, the concrete textual and tabular
artefacts used to write them down, the formal model-based equivalents
(W3C MBUI and OMG IFML), or the boundary conditions where object-first
design breaks down in favour of screen- or flow-first design. Throughout
this note, the word "design" is disambiguated into three senses:
*interface design* (the layout and behaviour of the interface held in a
design tool or UI spec), *technical design* (the software and domain
architecture between requirements and implementation tasks), and
*design-system identity* (the visual tokens and reusable widget library
of a design system).

## Key findings

- **F1. Interaction-design literature separates the task-domain
  conceptual model from concrete interface design, specifying objects,
  attributes, actions, and relationships in structured text before
  screens are sketched** [consensus — practitioner claim, method
  literature; rests on a summarised fetch]. Jeff Johnson and Austin
  Henderson (2002, 2011) define a conceptual model as a high-level,
  medium-independent description of how a system is organised and
  operates, explicitly distinguishing it from interface design (screens,
  layout, and controls) [1][2]. Their "Objects/Operations Analysis"
  enumerates four elements in structured prose and tables: (1) task-domain
  *objects* (excluding implementation constructs such as database tables
  or dialog boxes), (2) user-visible *attributes* of each object, (3)
  user-initiated *actions/operations* on each object, and (4)
  *relationships* between objects, chiefly containment and type/subtype
  specialisation hierarchies [1][2]. They claim that writing this model
  first acts as a contract constraining interface design (nothing
  outside the conceptual model enters the UI), prevents exponential
  complexity from computer-centric concepts, and provides a single
  lexicon for interface labels and documentation [1][2].

- **F2. Software concept design formalises the layer above the interface
  as independent, state-bearing "concepts" written in four-part textual
  blocks, treating the interface as a projection** [single source —
  method literature; rests on a summarised fetch]. Daniel Jackson
  (2021) bridges technical design and interface design by defining a
  *concept* as a reusable, UI-agnostic unit of behaviour specified in
  structured text with four sections: `purpose` (why the concept exists
  for the user), `state` (user-visible relational sets and mappings),
  `actions` (transactional state transitions with inputs and outputs),
  and `operational principle` (an archetypal scenario showing how the
  actions fulfil the purpose) [6]. Jackson argues that separating
  concept specifications from interface design prevents "concept
  corruption," where transient screen states or widget shortcuts distort
  the underlying behavioural rules [6].

- **F3. Object-Oriented UX (OOUX) replaces screen-first wireframing with
  the ORCA sequence (Objects, Relationships, Calls-to-Action,
  Attributes), captured in textual guides and tabular matrices**
  [emerging — practitioner claim; rests on a summarised fetch]. Sophia
  Voychehovski Prater (2015, 2016) introduced OOUX to address responsive,
  multi-device systems where static page hierarchies break down [3][4].
  Her ORCA methodology postpones screen and task-flow design until four
  structural artefacts are completed: an *Object Guide* (a structured
  textual glossary defining every domain entity), an *Object Map*
  (listing each object's core content, metadata attributes, and nested
  objects), a *Nested-Object Matrix* (a grid mapping containment and
  cardinality across objects), and a *CTA Matrix* (a table mapping user
  roles and calls-to-action to target objects) [3][4][5]. Prater claims
  that defining objects before actions and screens aligns interface
  design with human mental models, creates heterarchical (contextual
  "spiderweb") navigation rather than rigid page trees, and matches the
  object-oriented domain models used in technical design by engineers
  [3][4][5].

- **F4. Information architecture and interaction specifications represent
  the map of screens and cross-screen behaviour through alphanumeric
  sitemap tables, wireflows, and state transition matrices** [consensus
  — practitioner claim; rests on a summarised fetch]. Above individual
  screen layouts, IA and UX specification practice uses three primary
  representations: (1) *sitemaps and visual vocabularies* (Jesse James
  Garrett, 2002), which distinguish static information units ("pages")
  from dynamic functional units ("screenfuls") and map their hierarchy,
  conditional branches, and concurrent containers using unique
  alphanumeric IDs (`APP-01`, `APP-02`) in indented textual tables or
  node-link diagrams [7]; (2) *wireflows* (Page Laubheimer, 2016), which
  combine screen-state wireframes with flowchart connectors to document
  multi-step workflows and dynamic state changes in single-page or
  mobile apps where URLs do not map 1:1 to screens [8]; and (3) *state
  matrices* and *prototype specifications*, which use Markdown/HTML
  tables or YAML blocks to map screen or component IDs against trigger
  conditions, user permissions, and UI states (`Default`, `Loading`,
  `Empty`, `Error`, `Disabled/Read-Only`) [8].

- **F5. Model-Based User Interface (MBUI) standards formalise the
  separation between domain objects, abstract screen containers, and
  concrete widgets using XML/XMI serialisations** [consensus — standard;
  rests on a summarised fetch]. Both the W3C MBUI Working Group Notes
  (2014, built on the Cameleon Reference Framework) and the Object
  Management Group's Interaction Flow Modeling Language (IFML 1.0,
  2015) codify a strict multi-layer hierarchy above concrete screens
  [9][10][11]. In W3C MBUI, *Task and Domain Models* (platform-independent
  objects and user goals) transform via "concretization" into an
  *Abstract User Interface (AUI)* composed of modality-independent
  Abstract Interaction Units (AIUs), then into a *Concrete User
  Interface (CUI)* bound to a modality and design-system widget class,
  and finally into the executable *Final User Interface (FUI)* [9][10].
  In OMG IFML 1.0, the structure above and across screens is modelled by
  binding a UML `DomainModel` to top-level or nested `ViewContainer`
  elements (windows, pages, or XOR/Landmark panels), populated by
  `ViewComponent` elements (`List`, `Details`, `Form`) connected by
  event-driven `InteractionFlow` and `DataFlow` edges, all serialised
  in textual `XMI` (`IFML-Metamodel.xmi`) [11].

- **F6. Criticisms of object-first UX (OOUX and upfront conceptual
  modelling) centre on upfront time cost, stakeholder resistance to
  abstract matrices, and friction with strictly linear or procedural
  tasks** [contested — practitioner claim; rests on a summarised fetch].
  While Prater and Johnson & Henderson argue that object-first modelling
  saves downstream rework [1][3][4], practitioner critiques identified
  by the disconfirming query highlight three failure modes: (1) heavy
  upfront cognitive load and "analysis paralysis" when applied to small
  MVPs, marketing pages, or 0-to-1 products with unvalidated domain
  models [5]; (2) communication barriers with visual-first stakeholders
  who cannot evaluate tabular object maps or CTA matrices without seeing
  screens [5]; and (3) awkwardness on strictly procedural, transient
  workflows (such as step-by-step onboarding wizards, checkout funnels,
  or conversational flows) where the user's primary mental model is a
  sequence of steps rather than a web of persistent objects (contradicting
  a pure object-only unit of description) [5].

## Unexpected

In formal model-based standards (OMG IFML 1.0 and W3C MBUI), the top-level
"screen" is not a fixed unit at all, but a recursive `ViewContainer` (or
Abstract Interaction Unit) qualified by containment semantics such as
`XOR` (mutually exclusive sub-views like tabs or wizard steps),
`Landmark` (globally reachable navigation targets), and `Default` [10][11].
This reconfigures the binary choice between "screen" and "element": a
page, a modal dialog, a tab pane, and a master-detail split pane are the
exact same structural primitive (`ViewContainer`) at different nesting
depths, with navigation (`InteractionFlow`) operating uniformly between
top-level pages and nested sub-containers [11].

## Not found

- **Empirical controlled studies comparing object-first vs. screen-first
  textual specifications:** No controlled empirical study measuring
  defect rates, build time, or LLM code-generation accuracy when
  handing off an OOUX/conceptual-model specification versus a screen-first
  specification was found across ACM, W3C, or practitioner searches
  (benefits and criticisms rest on author and practitioner reports).
- **A single canonical plain-text DSL for OOUX or IA:** While IFML 1.0
  and W3C AUI define formal XML/XMI schemas [10][11] and Daniel Jackson
  uses an Alloy-like textual block syntax for concepts [6], UX
  practitioners use ad-hoc Markdown tables, spreadsheets, or visual
  whiteboards rather than a standardised Markdown schema.

## Options

1. **Screen-first unit (Sitemap + Screen & Wireflow Specs):**
   - *Structure:* A textual sitemap table (`ID | Route | Parent | Auth`)
     above individual screen Markdown files, each holding element tables
     and a screen-level state matrix.
   - *Trade-offs:* Low upfront abstraction and immediately familiar to
     developers and visual stakeholders; works naturally for linear
     wizards and small apps [5][8]. However, domain objects (such as an
     `Invoice` or `Project`) that appear on five screens as cards, rows,
     detail views, and forms must be re-described five times, risking
     inconsistent attributes, labels, and actions across screens [1][3].
2. **Object-first unit (OOUX / Concept Catalog only, screens derived):**
   - *Structure:* Define only domain objects/concepts (attributes,
     states, actions, relationships, and miniature/detail representations)
     in Markdown; treat screens merely as auto-generated or lightly
     configured containers for object views.
   - *Trade-offs:* Eliminates cross-screen drift and aligns directly
     with backend domain models [2][3][6]. However, it struggles with
     procedural, multi-step flows (wizards, onboarding, checkout) and
     cross-object dashboard layouts where screen-level spatial
     orchestration and step sequencing are primary [5][8].
3. **Hybrid layered unit (Conceptual/Object Model + View-Container
   Topology + Screen/Element Composition):**
   - *Structure:* Combine a lightweight textual *Object & Concept
     Model* (objects, attributes, actions, relationships) above the
     screens with a *View-Container Map & Flow Specification* (hierarchical
     `ViewContainer` sitemap with `XOR`/`Landmark` qualifiers and
     interaction flows), where individual screen definitions reference
     object views (`List`, `Details`, `Form` bound to a named object)
     alongside standalone UI elements and a state matrix.
   - *Trade-offs:* Captures both persistent domain entities (via objects)
     and procedural journeys or layout containers (via view containers
     and wireflows), matching W3C MBUI and IFML [9][11] as well as
     pragmatic OOUX practice [3][5], at the cost of maintaining an
     explicit binding layer between objects and screens.

## Relevance to this project

For `forge`—where an AI agent reads requirements, solution design, and
user stories in git-versioned Markdown and proposes a textual UX/UI
description for human review and downstream build—**Option 3 (the hybrid
layered unit)** is recommended. In the agent's inference, a pure
screen-or-element decomposition (the hypothesis mentioned in the packet
frame where a page simply lists standalone UI elements like a search
field) misses the intermediate layer identified across all four
literature streams: most screen regions are not arbitrary widgets, but
projections (`List`, `Details`, `Form`, or card views) of persistent
domain objects [2][3][11]. Conversely, because `forge` already carries a
technical solution design and user stories upstream in the Markdown
chain, the UX/UI description does not need a heavyweight standalone
database schema; instead, it should start with an **Above-the-Screens**
section containing:

1. **User-Facing Object & Concept Glossary (Markdown tables/blocks):**
   Deriving from the upstream domain model, each user-visible object
   lists its exposed attributes, user actions (CTAs), and containment or
   specialisation relationships [2][3][6].
2. **View-Container Hierarchy & Navigation Map (Indented table):**
   A textual sitemap using stable container IDs, route/context,
   container type (`Page`, `Modal`, `XOR Tab/Step`, `Landmark`), and
   entry/exit interaction flows [7][8][11].
3. **Cross-Screen State & Permission Matrix (Markdown table):**
   Mapping user roles and global system states (`Loading`, `Empty`,
   `Error`, `Read-Only`) to object actions and view containers [5][8].

Individual screen definitions below this layer can then compose both
*object-bound views* (referencing the object glossary so attributes and
CTAs are defined once) and *standalone UI elements* (such as a global
search field or navigation toggle).

**Consult when:**
- Deciding the top-level sections of the UX/UI Markdown template in
  `forge` and whether objects, screens, or elements are the primary unit.
- Designing how the UX/UI Markdown document links upstream to the
  solution design's domain model and user stories.
- Specifying how the AI agent should ask clarifying questions before
  proposing individual screens (asking about objects, attributes, CTAs,
  and navigation topology first).

## Sources

1. **Conceptual Models: Begin by Designing What to Design**, Jeff
   Johnson and Austin Henderson, Jan/Feb 2002 (dated by byline / issue
   metadata, *Interactions*, Vol. 9, Issue 1, ACM),
   https://dl.acm.org/doi/10.1145/503355.503366; kind: primary (read via
   tertiary summarised fetch); how read: summarised fetch; original.
2. **Conceptual Models: Core to Good Design**, Jeff Johnson and Austin
   Henderson, 2011 (dated by structured data / publication metadata,
   Morgan & Claypool / Synthesis Lectures on Human-Centered
   Informatics),
   https://dokumen.pub/conceptual-models-core-to-good-design-9781608455201-9781608455218.html;
   kind: primary (read via tertiary summarised fetch); how read:
   summarised fetch; copy of the 2011 Morgan & Claypool monograph.
3. **Object-Oriented UX**, Sophia Voychehovski (Prater), 2015-10-20
   (dated by byline on *A List Apart*; note: one secondary citation
   reported 2015-09-08),
   https://alistapart.com/article/object-oriented-ux/; kind: primary
   (read via tertiary summarised fetch); how read: summarised fetch;
   original.
4. **OOUX: A Foundation for Interaction Design**, Sophia Voychehovski
   (Prater), 2016-04-19 (dated by byline on *A List Apart*),
   https://alistapart.com/article/ooux-a-foundation-for-interaction-design/;
   kind: primary (read via tertiary summarised fetch); how read:
   summarised fetch; original.
5. **OOUX — Object-Oriented UX & The ORCA Process**, Sophia V. Prater
   (Rewired UX / OOUX.com), undated (evergreen method documentation and
   articles accessed via search index), https://www.ooux.com/; kind:
   primary vendor/author documentation (read via tertiary summarised
   fetch); how read: summarised fetch; original.
6. **The Essence of Software: Why Concepts Matter for Great Design**,
   Daniel Jackson, November 2021 (dated by book release metadata on
   companion site, Princeton University Press / MIT),
   https://essenceofsoftware.com/; kind: primary (read via tertiary
   summarised fetch); how read: summarised fetch; original.
7. **A Visual Vocabulary for Describing Information Architecture and
   Interaction Design**, Jesse James Garrett, 2002-03-06 (dated by
   byline, initially published 2000 and updated through 2002),
   http://www.jjg.net/ia/visvocab/; kind: primary (read via tertiary
   summarised fetch); how read: summarised fetch; original.
8. **Wireflows: A UX Deliverable for Workflows and Apps**, Page
   Laubheimer (Nielsen Norman Group), 2016-12-04 (dated by byline; first
   published 2016-09-11 / 2016-12-04),
   https://www.nngroup.com/articles/wireflows/; kind: primary (read via
   tertiary summarised fetch); how read: summarised fetch; original.
9. **Introduction to Model-Based User Interfaces**, Gerrit Meixner,
   Gaëlle Calvary, and Joëlle Coutaz (eds., W3C Model-Based User
   Interfaces Working Group Note), 2014-01-07 (dated by W3C document
   header), https://www.w3.org/TR/mbui-intro/; kind: primary standard
   note (read via tertiary summarised fetch); how read: summarised
   fetch; original.
10. **MBUI - Abstract User Interface Models**, Jean Vanderdonckt,
    Ricardo Tesoriero, Nesrine Mezhoudi, Vivian Motti, François Beuvens,
    and Jérémie Melchior (eds., W3C Model-Based User Interfaces Working
    Group Note), 2014-04-08 (dated by W3C document header),
    https://www.w3.org/TR/abstract-ui/; kind: primary standard note
    (read via tertiary summarised fetch); how read: summarised fetch;
    original.
11. **Interaction Flow Modeling Language (IFML) Specification, Version
    1.0**, Object Management Group (OMG, authored by Marco Brambilla,
    Piero Fraternali, et al.), February 2015 (adopted March 2013, formal
    1.0 published February 2015, dated by OMG specification metadata),
    https://www.omg.org/spec/IFML/; kind: primary standard (read via
    tertiary summarised fetch); how read: summarised fetch; original.

## Opened and not used

- `https://www.ooux.com` (via `curl.exe -sI` in shell): not opened,
  blocked by environment command deny rule; accessed via `search_web`
  summarised fetch instead.
- Secondary blog summaries on `riversagency.com`, `logrocket.com`,
  `aufaitux.com`, `uxtweak.com`, `designyourway.net`, and
  `sureprompts.com` returned in `search_web` grounding results: left out
  as secondary/vendor blog summaries superseded by the primary method
  authors and standards [1]–[11].

## Search record

- **Queries run (in order):**
  1. `conceptual models interaction design Johnson Henderson`
  2. `object-oriented UX ORCA Sophia Prater`
  3. `information architecture wireflows state matrix specification`
  4. `abstract user interface concrete user interface IFML view container interaction flow`
  5. `"object-oriented UX criticism"` (disconfirming query)
  6. `"Conceptual Models: Begin by Designing What to Design" Johnson Henderson 2002 interactions`
  7. `"Object-Oriented UX" "A List Apart" Sophia Voychehovski Prater 2015`
  8. `"Wireflows: A UX Deliverable for Workflows and Apps" Nielsen Norman Group Laubheimer 2016`
  9. `OMG IFML specification "Interaction Flow Modeling Language" "ViewContainer" "ViewComponent"`
  10. `"Object-Oriented UX" "OOUX: A Foundation for Interaction Design" Sophia Voychehovski URL date object map CTA matrix` (domain: `alistapart.com`)
  11. `"Conceptual Models: Core to Good Design" Johnson Henderson 2011 textual description objects attributes actions relationships`
  12. `"Model-Based User Interface" "Abstract User Interface" "Concrete User Interface" Cameleon Domain Model W3C Note 2014` (domain: `w3.org`)
  13. `"Interaction Flow Modeling Language" IFML 1.0 2015 ViewContainer ViewComponent InteractionFlow DomainModel XMI` (domain: `omg.org`)
  14. `"design specs" "wireframe annotations" "prototype specifications" "state matrix" information architecture sitemap textual format`
  15. `"object-oriented-ux" "ooux-a-foundation-for-interaction-design" Voychehovski "Object Map" objects attributes actions relationships` (domain: `alistapart.com`)
  16. `"The Essence of Software" Daniel Jackson concept specification "purpose" "operational principle" state actions user interface`
  17. `"jjg.net/ia/visvocab" OR "nngroup.com/articles/wireflows" OR "w3.org/TR/mbui-intro" OR "w3.org/TR/abstract-ui" exact date title author`
  18. `ORCA "Object Map" "CTA Matrix" "Object Guide" criticism OR objections OR "when not to use" Prater` (domain: `ooux.com`)
  19. `"omg.org/spec/IFML" OR "alistapart.com/article/object-oriented-ux" OR "essenceofsoftware.com" exact URL title date`
- **Pages opened (budget counting openings):** Direct HTTP fetches via
  command line were blocked by a user-configured deny rule (`curl.exe`
  denied); 11 primary sources [1]–[11] were examined via targeted
  `search_web` summarised fetches (within the 10–15 primary source
  budget).
- **What the disconfirming query found:** Running `"object-oriented UX
  criticism"` and the targeted follow-up on `ooux.com` confirmed that
  there is little academic refutation of object-oriented UX, while
  practitioner critiques focus on (a) high upfront time and cognitive
  cost ("analysis paralysis" on small or 0-to-1 projects), (b) friction
  with visual-first stakeholders who resist abstract matrices, and (c)
  poor fit for strictly linear, procedural workflows (such as wizards,
  onboarding, or checkout funnels) that are verb/step-driven rather than
  noun/object-driven.
- **Reason the run ended:** Both parts of the card's stop rule were met:
  every route in the card (conceptual models in interaction design,
  OOUX, information architecture and wireflows/state matrices, domain
  modelling/concept design, and W3C MBUI / OMG IFML standards) had a
  primary source (11 primary sources examined via summarised fetch, within
  the 10–15 budget), and differently worded queries returned no new
  structural concepts or textual formats.
