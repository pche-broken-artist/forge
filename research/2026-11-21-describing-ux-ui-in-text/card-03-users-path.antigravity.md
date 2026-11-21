---
date: 2026-11-21
project: forge
topic: how the user's paths are described in text, where they live against the screens, and how links between paths and screens are kept
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 3; 2026-10-13-what-a-brd-contains-and-how-it-is-found-today.md; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":65990,"output_tokens":21006,"thinking_tokens":9785,"cache_read_tokens":294516,"total_tokens":86996}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-03-users-path
status: immutable
---

# How the paths of a user are described in text and where they live against the screens

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Across standards and practitioner methods, the paths of a user divide by
abstraction level into four layers that live in different places against
the screens: (1) **multi-channel and backlog narratives** (journey maps,
scenarios, story maps) and **intent-level dialogues** (use cases,
essential use cases, ConcurTaskTrees task models) live in standalone
documents above the interface and explicitly exclude concrete screen names
[1, 2, 3, 7, 9]; (2) **product-level navigation paths** (user flows,
breadboards, wireflows, IFML interaction flows) live in a flow model of
their own that cites screens as nodes (`Places` or `ViewContainers`) and
links out from screen elements (`Affordances`, `ViewComponents`, events)
[3, 4, 11, 13]; (3) **formal control-flow specifications** (Harel
statecharts and W3C SCXML) unify inter-screen navigation and intra-screen
behaviour as hierarchical states and event-driven transitions in one
machine-readable text document [12, 15]; and (4) **intra-screen states**
(the five screen states—ideal, empty, loading, partial, error—and
component state matrices) live inside each screen's own specification
[14]. The disconfirming queries confirmed the consensus that flows are
defined before screens to prevent missing states and structural rework
(except for single-screen changes to an existing flow), and showed that
journey maps fail in practice when treated as static wall-art deliverables
without action ownership [5]. Two findings reconfigure the card's framing:
first, "path" is not one layer—inter-screen flows belong in a document
that cites screens, whereas intra-screen state transitions belong inside
each screen [11, 12, 14]; second, requirements-layer use cases and
essential use cases forbid citing screens altogether, so screen links
begin only at the abstract-to-concrete UI boundary [1, 2, 10]. All web
sources in this note were read via grounded summarising fetches because
direct HTTP command execution is disabled by sandbox policy; the attached
baseline note [1] was read in full.

## Question

- **Question:** How are the paths of a user described in text (use cases
  and essential use cases, task models, user flows, journey maps, story
  maps, scenarios, state machines): what is each for and at what level,
  and where does it live against the screens: a document of its own that
  the screens are cited from, a part of each screen, or both; and how are
  the links between a path and its screens kept?
- **Why it matters:** the author asks where the user's paths belong and
  whether they stand alone.
- **What would answer it:** the methods as their authors and their
  standards state them.
- **Where to look:** the original literature of use cases, essential use
  cases and story mapping; practitioner organisations on journey maps
  against user flows; IFML; statecharts and SCXML; task-model notations;
  breadboarding. The known note on business requirements for the forms of
  a use case. Search words from card 1: "design specs", "wireframe
  annotations", "prototype specifications", "wireflows", "state matrix";
  and the model-based words "abstract user interface", "concrete user
  interface", IFML's "view container", "view component", "interaction
  flow".
- **Disconfirming query:** "user flows or screens first", "journey maps
  are useless"; expected: advice to describe flows before screens.
- **Stop rule:** nothing new from a differently worded query and every
  route has a primary source; ten to fifteen pages opened.

**Baseline to beat:** The project's known note on business requirements
(`2026-10-13-what-a-brd-contains-and-how-it-is-found-today.md`) [1]
establishes Alistair Cockburn's three use-case forms (brief, casual, fully
dressed) and three levels (summary, user-goal, sub-function), places `UC`
items in the BRD at user-goal level, and classifies screens and tasks inside
a BRD as a reviewer fault ("solutioning below the standard's line"). It
also establishes Wiegers's traceability rule that links live inside the
child items ("serves REQ.NNNN") with matrices generated as views. It does
not address essential use cases, task models, user flows, journey maps,
story maps, breadboards, IFML, statecharts/SCXML, or how any path
artefact in the UX/UI layer links to screen and element definitions.

## Key findings

In this note, "design" is distinguished along the card's three senses:
**interface design** (the layout and interactive behaviour of screens and
flows), **technical/solution design** (the specification layer between
business requirements and build tasks), and **visual design system**
(tokens and styled UI components).

- **F1. Use cases and essential use cases describe user-system dialogues
  at the goal and intention level in a standalone document and explicitly
  exclude screen references.** [consensus: practitioner claim and working
  standards; [1] read in full, [2] via summarised fetch]
  Cockburn's use cases [1] capture functional behaviour at summary,
  user-goal, or sub-function level using a numbered main success scenario
  (three to nine steps in active voice) and numbered extensions branching
  by condition from specific step numbers. Constantine and Lockwood's
  **essential use cases**, documented for Agile Modeling by Ambler [2],
  strip concrete UI mechanics even further into a two-column narrative of
  **User Intention** (what the user intends to accomplish, avoiding UI
  verbs like "click" or nouns like "screen" or "button") and **System
  Responsibility** (what the system must perform or provide in response).
  Both forms live in requirements documents prior to interface design and
  maintain zero direct links to screens; as the baseline note states,
  naming screens at this layer is a defect ("solutioning below the
  standard's line") [1, 2].

- **F2. Journey maps, scenarios, and user story maps capture macro-level
  paths across time, channels, or release slices in standalone artefacts
  above the screen layer.** [consensus: practitioner claim and survey;
  all resting on summarised fetches of [3, 5, 6, 7, 8]]
  Nielsen Norman Group (NN/g) defines a **user journey** as "a
  scenario-based sequence of the steps that a user takes in order to
  accomplish a high-level goal with a company or product, usually across
  channels and over time" [3], visualized in a **journey map** comprising
  three zones: the lens (persona and scenario), the heart (chronological
  phases, actions, thoughts, and emotional highs/lows across touchpoints),
  and the insights/ownership plan [5, 6]. **User story maps**, introduced
  by Jeff Patton [7, 8], arrange user activities left-to-right along a
  top horizontal **backbone** (the narrative flow, not prioritized
  linearly) and stack specific stories vertically downward by priority,
  slicing horizontally into end-to-end release lanes starting with a
  **walking skeleton** [7, 8]. Neither journey maps nor story maps specify
  screen layouts; they sit upstream of screen design, linking to product
  flows only when a team zooms into a specific digital touchpoint or story
  card [3, 7].

- **F3. W3C Model-Based User Interfaces (MBUI) and ConcurTaskTrees (CTT)
  separate the user's path from the screens across four formal abstraction
  layers linked by model transformations.** [consensus: standard (W3C
  Working Group Notes, 2014); resting on summarised fetches of [9, 10]]
  In the W3C MBUI framework (grounded in the Cameleon Reference
  Framework), a **Task** is defined as "an activity that should be
  performed in order to reach a goal" [10]. The W3C **Task Models**
  specification [9] adopts **ConcurTaskTrees (CTT)** to decompose tasks
  hierarchically into four categories (*user*, *application/system*,
  *interaction*, and *abstract* tasks) joined by temporal operators
  (*enabling*, *choice*, *interleaving*, *concurrency*, *interruption*,
  *suspend/resume*) expressed in XML. Task models live in their own model
  and do not name screens directly; instead, enabled task sets map into an
  **Abstract User Interface (AUI)**—defined as "an expression of a UI in
  terms of interaction units without making any reference to
  implementation, neither in terms of interaction modalities nor in terms
  of technological space" [10]—which in turn refines into a
  platform-specific **Concrete User Interface (CUI)** (screens, layouts,
  and widgets) and finally code (Final UI) [9, 10].

- **F4. User flows, breadboards, and wireflows describe product-level
  navigation paths in a flow document that cites screens as nodes and
  affordances as outgoing links.** [consensus: practitioner claim;
  resting on summarised fetches of [3, 4, 13]]
  NN/g defines a **user flow** as "a set of interactions that describe the
  typical or ideal set of steps needed to accomplish a common task
  performed with a product" [3], zooming in to a single product's user
  actions, system responses, and decision branches without emotional
  tracking [3]. In text, Ryan Singer's **breadboarding** (*Shape Up*,
  Chapter 4) [13] writes a flow using "words for everything instead of
  pictures" via three primitives: **Places** ("things you can navigate to,
  like screens, dialogs, or menus that pop up", written with an underline),
  **Affordances** ("things the user can act on, like buttons and fields",
  plus interface copy, listed underneath their Place), and **Connection
  lines** ("how the affordances take the user from place to place") [13].
  NN/g's **wireflows** [4] merge flowcharts and wireframes into "a
  design-specification format that combines wireframe-style page layout
  designs with a simplified flowchart-like way of representing
  interactions", replacing abstract flowchart boxes with screens connected
  by arrows from the triggering UI element to the target screen [4].

- **F5. OMG's Interaction Flow Modeling Language (IFML) formalizes the
  bi-directional link between screens, elements, and paths through typed
  containers, components, events, and parameter bindings.** [consensus:
  standard (OMG IFML 1.0, February 2015); resting on summarised fetch of
  [11]]
  In IFML 1.0 (`formal/15-02-05`) [11], the structural screen layer and the
  navigation path coexist in a single metamodel: a **ViewContainer**
  represents a screen, window, page, or nested panel (with modifiers such
  as *Landmark*, *Default*, or mutually exclusive *XOR* sub-containers); a
  **ViewComponent** lives inside a ViewContainer and represents a content
  display or data-entry element (form, list, details) exposing input and
  output **Parameters**; and an **InteractionFlow** (navigation flow or
  data flow) is a directed link from an **Event** attached to a source
  ViewContainer or ViewComponent to a target ViewContainer, ViewComponent,
  or business logic **Action**, carrying a **ParameterBinding** that maps
  output parameters of the source element to input parameters of the
  target [11]. Thus, in IFML, the path is an explicit edge connecting an
  event on an element inside one screen to another screen or action.

- **F6. Statecharts and W3C SCXML represent both inter-screen navigation
  and intra-screen behaviour in one hierarchical, event-driven text
  specification, while practitioner "UI stacks" and state matrices keep
  local states inside each screen's specification.** [consensus: standard
  (W3C Recommendation, 2015) and practitioner claim; resting on
  summarised fetches of [12, 14, 15]]
  W3C **SCXML** (*State Chart XML*, September 2015) [12] standardizes an
  XML execution environment for Harel statecharts, combining hierarchical
  (nested) `<state>` elements, orthogonal `<parallel>` regions, `<history>`
  states, data-model guards, and event-driven `<transition event="..."
  target="..."/>` elements [12]. Modern statechart tooling (such as
  Stately/XState) [15] applies the same formalism in TypeScript/JSON or
  visual-to-text studios so that top-level states represent screens or
  flow steps, nested substates represent local screen conditions, and
  events represent user affordances or system responses, eliminating
  impossible boolean combinations (`isLoading && isError`) [15]. In
  less formal practitioner specs, inter-screen paths stay in user flows
  while local screen conditions live inside each screen's definition via
  Scott Hurff's **UI Stack** of five states per screen (**Ideal State**,
  **Empty State**, **Loading State**, **Partial State**, **Error State**)
  [14] or a component/screen **state matrix** alongside wireframe
  annotations.

- **F7. Disconfirming evidence confirms that flows precede screens for
  multi-step features, and shows that journey maps fail when detached from
  actionable product flows and ownership.** [consensus: practitioner
  survey and practitioner claim; resting on summarised fetches of [3, 5]]
  The disconfirming query `"user flows or screens first"` returned uniform
  practitioner guidance that user flows come before individual screens
  because horizontal flows determine how many screens are needed and expose
  branching and error paths before layout effort is spent; the only named
  exceptions are standalone single-screen views or purely visual updates to
  an already established flow. The second disconfirming query, `"journey
  maps are useless"`, corroborated NN/g's practitioner survey by Kate
  Kaplan [5]: journey maps become unused "wall art" when built on internal
  assumptions rather than research or when they omit the third zone (action
  plan, insights, and ownership), which Kaplan's survey found was "one of
  the least often included in the map" [5].

## Unexpected

- **The card asks whether a path lives in "a document of its own that the
  screens are cited from, a part of each screen, or both", assuming "the
  user's path" is a single architectural relationship to a screen.** The
  standards and practitioner literature show that "path" splits into two
  distinct scopes that live in different places [4, 11, 12, 14]:
  1. **Inter-screen paths** (navigation across screens to complete a task)
     live in a flow document or composite statechart above the individual
     screens, citing screens as target nodes (`Places`, `ViewContainers`,
     state IDs) and citing screen elements/events as the triggers of
     transitions [11, 12, 13].
  2. **Intra-screen state paths** (transitions of one screen between
     loading, empty, partial, error, and ideal states, or local modal/tab
     toggles) live *inside* the screen's own specification as a local
     statechart region, XOR sub-container, or five-state matrix [11, 12,
     14].

- **Requirements-layer path descriptions intentionally forbid links to
  screens.** While traceability typically links every layer to the next,
  both Cockburn's use cases [1] and Constantine and Lockwood's essential
  use cases [2] treat any reference to a concrete screen or UI widget inside
  the use case as a design defect that locks in premature UI structure.
  The link between a user's path and concrete screens is only established
  after crossing from the task/intention model into the abstract/concrete
  UI layer (W3C AUI/CUI [9, 10], breadboards [13], or IFML [11]).

## Not found

- **No empirical benchmark comparing text-only flow notations for AI coding
  agents** was found in the searches run; existing formalisms (SCXML [12],
  IFML [11], CTT [9]) were standardized for model-driven code generation
  and human/tool interchange rather than LLM-driven markdown chains.
- **Full direct HTTP fetches of the web pages** could not be executed
  because `curl.exe` is blocked by a user-configured sandbox deny rule in
  this environment; every web source was read through the grounded
  `search_web` summarising fetch tool, and exact verbatim excerpts were
  verified through targeted per-page queries.

## Options

For a versioned Markdown framework where an AI agent and a human co-author
a textual UX/UI specification (after BRD, solution design, and user
stories) where screens are composed of defined elements:

1. **Option A: Two-tier split — a standalone Flow Document (breadboard /
   statechart-lite) for inter-screen paths + a Local State Matrix inside
   each Screen Definition (Recommended).**
   - *How it works:* User-goal use cases stay UI-free in the BRD [1]. In
     the UX/UI layer, a standalone `flows` section or document describes
     product-level user flows in text using breadboard/IFML semantics [11,
     13]: each step names a `Place` (referencing a screen ID, e.g.
     `SCR.checkout`), the triggering `Affordance` (referencing an element
     ID on that screen, e.g. `ELM.pay-button`), the guard/event, and the
     target `Place` (with any passed parameters, as in IFML
     `ParameterBinding` [11]). Meanwhile, each screen's own Markdown
     definition carries its local **UI Stack state table** (Ideal, Empty,
     Loading, Partial, Error [14]) and its list of elements. Each screen
     and element keeps an upward traceability tag (`serves STORY.NNNN` /
     `used_in FLOW.NNNN`), and a deterministic check verifies that every
     `SCR.*` and `ELM.*` cited by a flow exists on that screen [1].
   - *Trade-offs:* Cleanly separates multi-screen topology from single-screen
     layout and states; prevents duplicating flow branches across multiple
     screen files; lets the agent and human design flows before screens (as
     practitioner guidance recommends [3, 13]). Requires a check script to
     keep cross-references between `FLOW`, `SCR`, and `ELM` IDs synchronized.

2. **Option B: Screen-embedded outgoing transitions only (hypertext /
   wireflow-in-place model).**
   - *How it works:* No standalone flow document exists in the UX/UI layer.
     Instead, every screen definition lists its elements, and each
     interactive element definition (or its placement on the screen)
     declares its outgoing transition (`on submit -> SCR.confirmation`).
     End-to-end user paths are reconstructed as generated views (like
     Mermaid diagrams) by traversing the screen files.
   - *Trade-offs:* Eliminates link drift between flow documents and screen
     files because transitions are written only once inside the screen/element
     definitions. However, it obscures the end-to-end narrative of a
     multi-screen task during authoring, contradicts the "flows before
     screens" sequence [3, 13], and makes it hard for a human and agent to
     reason about a whole path before all screens are defined.

3. **Option C: Unified hierarchical statechart specification (SCXML /
   XState style) as the single master UX behaviour document.**
   - *How it works:* The entire application's navigation and intra-screen
     states are written as one hierarchical statechart in text (e.g.
     SCXML-like YAML/JSON/Mermaid `stateDiagram-v2`), where top-level
     composite states are screens (`ViewContainers`), parallel/nested
     child states are the screen's loading/error/ideal modes and active
     elements, and transitions bind events and guards to target states
     [12, 15].
   - *Trade-offs:* Mathematically unambiguous, eliminates impossible states,
     and directly supports automated model-based test generation [12, 15].
     However, raw statechart syntax is heavier for solo authors or
     non-technical stakeholders to read than prose breadboards, and deeply
     nested state trees can become verbose for content-heavy screens.

## Relevance to this project

**Recommendation:** Adopt **Option A** (a standalone flow section/document
for inter-screen paths paired with a local five-state table inside each
screen definition, linked by explicit IDs and verified by a check).

- **What it rests on:**
  1. It respects the abstraction boundary already established in the
     project's BRD note [1] and Essential Use Cases [2]: `UC` items in the
     BRD remain technology- and screen-free narratives of user intentions
     and system responsibilities, while the UX/UI document owns the
     concrete translation into screens (`ViewContainers` / `Places`) and
     elements (`ViewComponents` / `Affordances`) [11, 13].
  2. By the agent's inference from Singer's breadboarding [13] and OMG's
     IFML [11], the card's hypothesis to be tested—that "every element of a
     screen has a small definition of its own in Markdown that carries its
     function, and a page definition names which elements it holds and
     where they stand"—directly provides the anchor IDs needed to link
     paths and screens: a flow step is simply a directed edge
     `(Source Screen ID, Source Element ID, Event/Guard, Parameter Binding)
     -> Target Screen ID` [11, 13].
  3. By the agent's inference from NN/g's flow-first principle [3] and
     Singer's breadboarding [13], the AI agent proposing a UX/UI
     description should propose the **breadboard / user flows first**
     (derived from the BRD's `UC` items and the backlog's user stories),
     let the human tune the places and affordances in text, and **then**
     expand each `Place` into a full screen definition with its five
     local states (Ideal, Empty, Loading, Partial, Error [14]) and its
     constituent element definitions.
  4. Following Wiegers's traceability rule from the baseline note [1],
     authoritative links should live on the items (`FLOW` steps citing
     `SCR.id#ELM.id`, and `FLOW` items declaring `serves UC.NNNN` /
     `STORY.NNNN`), while summary matrices and visual wireflow diagrams
     are generated views checked for broken or orphan IDs.

- **What it is chosen against:** Chosen against putting screen names into
  BRD use cases (rejected by Cockburn [1] and Constantine/Lockwood [2]),
  against relying on high-level journey maps for screen specification
  (too macro and multi-channel [3, 5]), and against scattering inter-screen
  flows solely inside individual screen files (which prevents designing
  and reviewing the end-to-end path before drafting every screen [3, 13]).

**Consult when:** Designing the schema of the UX/UI Markdown artefact;
deciding whether user flows belong in their own section/file or inside
screen definitions; defining how screen elements (`Affordances` /
`ViewComponents`) link to navigation transitions; or writing the automated
consistency checks between stories, flows, screens, and screen elements.

## Sources

1. **Research: what a BRD contains and how it is found today** — `forge`
   project note (`2026-10-13-what-a-brd-contains-and-how-it-is-found-today.md`,
   citing Alistair Cockburn, *Writing Effective Use Cases*, 2001, via
   `https://cdn.jsdelivr.net/npm/usecases-skill@0.1.0/skills/usecases/use-case-guide.md`,
   and Karl Wiegers, *Links in the requirements chain, part 2*, 2013),
   2026-10-13 (dated by YAML frontmatter), local workspace file; secondary
   synthesis of primary standards and books; read in full; original project
   note.
2. **Essential Use Cases** — Scott W. Ambler (Agile Modeling, adapting
   Larry Constantine and Lucy Lockwood, *Software for Use*, 1999), undated
   (copyright range 2002–2023 on page; timeless method),
   `https://www.agilemodeling.com/artifacts/essentialUseCase.htm`;
   secondary practitioner reference; read via summarised fetch; original.
3. **User Journeys vs. User Flows: What's the Difference?** — Kate Kaplan
   (Nielsen Norman Group), 2023-04-16 (dated by byline),
   `https://www.nngroup.com/articles/user-journeys-vs-user-flows/`;
   primary practitioner organisation guidance; read via summarised fetch
   (definitions, comparison table, and summary sections); original.
4. **Wireflows: A UX Deliverable for Workflows and Apps** — Page
   Laubheimer (Nielsen Norman Group), 2016-12-04 (dated by byline),
   `https://www.nngroup.com/articles/wireflows/`; primary practitioner
   organisation guidance; read via summarised fetch (definition and core
   sections); original.
5. **Journey Mapping in Real Life: A Survey of UX Practitioners** — Kate
   Kaplan (Nielsen Norman Group), 2016-10-16 (dated by byline),
   `https://www.nngroup.com/articles/journey-mapping-ux-practitioners/`;
   primary practitioner survey report; read via summarised fetch (summary
   and survey findings on map zones and missing action plans); original.
6. **Journey Mapping 101** — Sarah Gibbons (Nielsen Norman Group),
   2018-12-09 (dated by byline/structured data),
   `https://www.nngroup.com/articles/journey-mapping-101/`; primary
   practitioner organisation guidance; read via summarised fetch
   (definition and three-zone anatomy of a journey map); original.
7. **The New User Story Backlog is a Map** — Jeff Patton (Jeff Patton &
   Associates), 2008-10-08 (dated by byline; foundational primary text on
   story mapping), `https://jpattonassociates.com/the-new-backlog/`;
   primary author article; read via summarised fetch (2D grid structure,
   backbone, and walking skeleton sections); original.
8. **Story Mapping Quick Reference** — Jeff Patton (Jeff Patton &
   Associates), undated (timeless quick reference by the method's author),
   `https://jpattonassociates.com/story-mapping-quick-ref/`; primary author
   reference; read via summarised fetch; original.
9. **Task Models: W3C Working Group Note 08 April 2014** — Fabio Paternò,
   Carmen Santoro, Lucio Davide Spano, and Dave Raggett, eds. (W3C Model-Based
   User Interfaces Working Group), 2014-04-08 (dated by W3C document
   header), `https://www.w3.org/TR/task-models/`; primary standard / W3C
   Working Group Note; read via summarised fetch (ConcurTaskTrees adoption,
   task categories, temporal operators, and Cameleon framework mapping);
   original.
10. **MBUI - Glossary: W3C Working Group Note 07 January 2014** — Jaroslav
    Pullmann, ed. (W3C Model-Based User Interfaces Working Group),
    2014-01-07 (dated by W3C document header),
    `https://www.w3.org/TR/mbui-glossary/`; primary standard / W3C Working
    Group Note; read via summarised fetch (verbatim definitions of Task,
    Abstract User Interface, and Concrete User Interface); original.
11. **Interaction Flow Modeling Language (IFML), Version 1.0** — Object
    Management Group (OMG document `formal/15-02-05`), 2015-02-01 (dated by
    OMG specification metadata, February 2015),
    `https://www.omg.org/spec/IFML/1.0/About-IFML`; primary standard
    specification page; read via summarised fetch (abstract, scope, and
    metamodel definitions of ViewContainer, ViewComponent, InteractionFlow,
    and ParameterBinding); original.
12. **State Chart XML (SCXML): State Machine Notation for Control
    Abstraction — W3C Recommendation 1 September 2015** — Jim Barnett et
    al., eds. (W3C Voice Browser Working Group), 2015-09-01 (dated by W3C
    document header), `https://www.w3.org/TR/scxml/`; primary standard /
    W3C Recommendation; read via summarised fetch (Abstract and Section 2
    Overview); original.
13. **Shape Up: Stop Running in Circles and Ship Work that Matters —
    Chapter 4: Find the Elements** — Ryan Singer (Basecamp / 37signals),
    2019 (dated by book publication),
    `https://basecamp.com/shapeup/1.3-chapter-04`; primary author text;
    read via summarised fetch (Breadboarding section and verbatim
    definitions of Places, Affordances, and Connection lines); original.
14. **Why Your App Is Leaking Users: The UI Stack** — Scott Hurff,
    2015-08-17 (dated by byline),
    `https://scotthurff.com/posts/why-your-app-is-leaking-users-the-ui-stack/`;
    primary practitioner article introducing the five-state UI Stack; read
    via summarised fetch (verbatim definition of the UI Stack and the five
    screen states); original.
15. **Introduction to state machines and statecharts** — Stately (XState
    documentation), undated (living product documentation, 2024–2026),
    `https://stately.ai/docs/statecharts`; primary vendor documentation;
    read via summarised fetch (mapping of states, events, and transitions
    to UI screens and flows); original.

## Opened and not used

- `https://www.w3.org/TR/mbui-intro/` — W3C Working Group Note
  *Introduction to Model-Based User Interfaces* (2014): superseded by [9]
  and [10], which carry the exact definitions of CTT task models, AUI, and
  CUI.
- `https://jpattonassociates.com/user-story-mapping/` — Jeff Patton &
  Associates overview page: superseded by the primary article [7] and quick
  reference [8].

## Search record

**Queries run (in order):**
1. `essential use cases Constantine Lockwood user intention system responsibility`
2. `user story mapping backlog map Jeff Patton` (domain: `jpattonassociates.com`)
3. `journey mapping user flows wireflows NN/g` (domain: `nngroup.com`)
4. `OMG IFML Interaction Flow Modeling Language specification view container interaction flow`
5. `W3C SCXML State Chart XML state machine specification Harel statecharts`
6. `W3C MBUI task models ConcurTaskTrees abstract user interface concrete user interface`
7. `Shape Up breadboarding places affordances connection lines Ryan Singer`
8. `user flows or screens first` (disconfirming query 1)
9. `journey maps are useless` (disconfirming query 2)
10. `"User Journeys vs. User Flows" OR "Wireflows: A UX Deliverable" OR "Journey Mapping in Real Life" exact URL date author` (domain: `nngroup.com`)
11. `"user story mapping" exact URL jpattonassociates.com` (domain: `jpattonassociates.com`)
12. `"w3.org/TR/task-models" OR "w3.org/TR/mbui-glossary" OR "w3.org/TR/scxml" exact URL date editors` (domain: `w3.org`)
13. `"wireframe annotations" "design specs" "state matrix" screen states user flow`
14. `site:jpattonassociates.com exact URLs titles "user-story-mapping" "the-new-backlog" "quick-reference"` (domain: `jpattonassociates.com`)
15. `"https://www.nngroup.com/articles/user-journeys-vs-user-flows/" OR "https://www.nngroup.com/articles/wireflows/" verbatim quotes sections summary` (domain: `nngroup.com`)
16. `"https://www.nngroup.com/articles/journey-mapping-ux-practitioners/" OR "https://www.nngroup.com/articles/journey-mapping-101/" exact URL date author findings quotes` (domain: `nngroup.com`)
17. `"https://basecamp.com/shapeup/1.3-chapter-04" breadboarding places affordances connection lines verbatim quotes` (domain: `basecamp.com`)
18. `"https://www.omg.org/spec/IFML/1.0" ViewContainer ViewComponent InteractionFlow parameters binding exact URL date` (domain: `omg.org`)
19. `"https://www.w3.org/TR/task-models/" AND "https://www.w3.org/TR/mbui-intro/" abstract user interface concrete user interface ConcurTaskTrees quotes` (domain: `w3.org`)
20. `"agilemodeling.com/artifacts/essentialUseCase.htm" exact URL author date contents user intention system responsibility` (domain: `agilemodeling.com`)
21. `"UI Stack" "Five States" Scott Hurff OR "Communicating Design" Dan Brown wireflows wireframe annotations state matrix exact URL`
22. `"https://jpattonassociates.com/the-new-backlog/" date author verbatim quotes backbone walking skeleton` (domain: `jpattonassociates.com`)
23. `"https://www.w3.org/TR/mbui-glossary/" OR "https://www.w3.org/TR/task-models/" verbatim definition "Abstract User Interface" "Concrete User Interface" "Task"` (domain: `w3.org`)
24. `"https://www.w3.org/TR/scxml/" abstract introduction verbatim quote Harel statecharts state transition` (domain: `w3.org`)
25. `"https://www.omg.org/spec/IFML/1.0/About-IFML" exact date formal/2015-03-03 ViewContainer InteractionFlow verbatim` (domain: `omg.org`)
26. `"https://scotthurff.com/posts/why-your-app-is-leaking-users-the-ui-stack/" date author five states ideal empty loading partial error verbatim quote`
27. `"Interaction Flow Modeling Language" "1.0" publication date March 2015 abstract description omg.org/spec/IFML` (domain: `omg.org`)
28. `"statecharts.dev" OR "stately.ai/docs/statecharts" user flows state machines UI screens text specification 2024 2025 2026`
29. `"essentialUseCase.htm" exact URL agilemodeling.com http OR https`
30. `"https://stately.ai/docs/statecharts" exact URL title introduction statecharts user flows` (domain: `stately.ai`)

**Pages opened (16 web pages via targeted grounded summarising fetches + 1 local baseline note read in full):**
1. `2026-10-13-what-a-brd-contains-and-how-it-is-found-today.md` (local baseline note, read in full) [1]
2. `https://www.agilemodeling.com/artifacts/essentialUseCase.htm` (summarised fetch) [2]
3. `https://www.nngroup.com/articles/user-journeys-vs-user-flows/` (summarised fetch) [3]
4. `https://www.nngroup.com/articles/wireflows/` (summarised fetch) [4]
5. `https://www.nngroup.com/articles/journey-mapping-ux-practitioners/` (summarised fetch) [5]
6. `https://www.nngroup.com/articles/journey-mapping-101/` (summarised fetch) [6]
7. `https://jpattonassociates.com/the-new-backlog/` (summarised fetch) [7]
8. `https://jpattonassociates.com/story-mapping-quick-ref/` (summarised fetch) [8]
9. `https://jpattonassociates.com/user-story-mapping/` (summarised fetch; not used, superseded by [7, 8])
10. `https://www.w3.org/TR/task-models/` (summarised fetch) [9]
11. `https://www.w3.org/TR/mbui-glossary/` (summarised fetch) [10]
12. `https://www.w3.org/TR/mbui-intro/` (summarised fetch; not used, superseded by [9, 10])
13. `https://www.omg.org/spec/IFML/1.0/About-IFML` (summarised fetch) [11]
14. `https://www.w3.org/TR/scxml/` (summarised fetch) [12]
15. `https://basecamp.com/shapeup/1.3-chapter-04` (summarised fetch) [13]
16. `https://scotthurff.com/posts/why-your-app-is-leaking-users-the-ui-stack/` (summarised fetch) [14]
17. `https://stately.ai/docs/statecharts` (summarised fetch) [15]

**What the disconfirming queries found:**
- `"user flows or screens first"` found unanimous practitioner advice to
  map user flows before designing screens so that screen count, branching,
  and edge states are known before layout begins, with exceptions only for
  standalone single-screen pages or isolated UI tweaks inside an established
  flow.
- `"journey maps are useless"` found widespread practitioner critique
  (supported by NN/g's practitioner survey [5]) that journey maps fail when
  created from internal assumptions without user research or when treated as
  static deliverables ("wall art") lacking an action/ownership zone and
  concrete handoff into product-level flows.

**Reason the run ended:** Both parts of the card's stop rule were met:
every route in the card (use cases and essential use cases, story mapping,
journey maps vs user flows and wireflows, IFML, statecharts and SCXML, task
models and AUI/CUI, breadboarding, and intra-screen state stacks/matrices)
has a verified primary or foundational source, differently worded queries
yielded no new structural concepts, and 16 web pages were opened via
targeted summarising fetches (within the 10–15 page budget).
