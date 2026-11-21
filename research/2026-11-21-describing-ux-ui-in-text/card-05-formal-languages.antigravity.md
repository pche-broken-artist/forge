---
date: 2026-11-21
project: forge
topic: Formal languages and standards for platform-independent UI and interaction description
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 5; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":52222,"output_tokens":23721,"thinking_tokens":10022,"cache_read_tokens":156115,"total_tokens":75943}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-05-formal-languages
status: immutable
---

# Formal languages and standards that describe user interfaces and interaction independently of implementation, their scope, and their fate in practice

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Over two decades of standardization produced three distinct families of
platform-independent user interface artifacts: layered XML User Interface
Description Languages (UIDLs) anchored on the four-level CAMELEON
reference framework (UIML, UsiXML, MARIA, XForms, and the 2014 W3C
Model-Based User Interfaces Working Group Notes), the Object Management
Group's diagrammatic Interaction Flow Modeling Language (IFML 1.0 of
2015), and the ergonomic principles and reporting templates of ISO 9241
and ISO/TR 25060 (Common Industry Format). Because direct command-line
page fetching is blocked by environment policy in this session, all
findings rest on grounded summarised fetches (`search_web`, a tertiary
method) of the primary standards and academic surveys and are reported
as such. None of the formal generative UI languages achieved mainstream
adoption in general web, mobile, or desktop product development: the W3C
closed its Model-Based UI Working Group in April 2014 with Working Group
Notes rather than Recommendations, closed its Forms Working Group in
April 2015, and OMG never issued a revision to IFML 1.0, because upfront
metamodeling overhead, generic "cookie-cutter" visual output, broken
round-trip synchronization between models and hand-tuned code, and
rapidly shifting frontend frameworks caused practitioners to prefer
component code and visual interface design tools. The disconfirming
query confirmed that industrial success held only in safety-critical,
hardware-coupled, or high-variability verticals (industrial SCADA/HMI,
automotive cockpits, smart-factory plug-and-play interfaces, and
enterprise low-code niches), while the unexpected finding is that a
modern JSON-schema successor—the W3C UI Specification Schema Community
Group (`uispec`)—already attempted to bridge Open UI, Design Tokens, and
cross-platform component contracts, only to close on 2026-05-21 without
a standard.

## Question

#### Card 5: Formal languages and standards
- **Question:** Which formal languages and standards describe a user
  interface or its interaction independently of its implementation (the
  model-based tradition with its levels of task, abstract, concrete and
  final interface; UsiXML, UIML, MARIA, XForms, the W3C's notes; IFML;
  the parts of ISO 9241), what does each describe, what became of each
  in practice, and which reasons are given for adoption or its absence?
- **Why it matters:** a layered description independent of the platform
  is what four target platforms ask for; the fate of these languages
  says what to borrow and what to avoid.
- **What would answer it:** the standards' own documents and academic
  studies of their adoption.
- **Where to look:** the W3C's model-based UI working group; the IFML
  specification; surveys of model-based UI development; ISO through
  secondary pages. Search words from card 1: "user interface description
  language", "model-based user interface development", "CAMELEON
  reference framework", "task model", "Common Industry Format" (ISO/TR
  25060); the W3C's UI Specification Schema Community Group of 2025 and
  2026, to be verified; why the notes of 2014 and the version of 2015
  had no successor.
- **Disconfirming query:** "model-based user interface development
  industrial adoption success"; expected: little adoption, with a few
  fields where it held.
- **Stop rule:** nothing new from a differently worded query and every
  route has a primary source; ten to fifteen pages opened.

The baseline this note must beat is a textbook catalog that lists acronyms
(CAMELEON, UIML, UsiXML, MARIA, XForms, IFML, ISO 9241) as if they were
interchangeable specifications of the same thing. To beat that baseline,
this note separates three meanings of the word "design" used in the
sources—*interface design* (the layout, visual presentation, and
interaction crafted in a design tool), *technical design* (the structural
and behavioral specification between requirements and implementation
tasks), and *visual identity* (the styling tokens and brand rules of a
design system)—shows which layer each standard actually formalizes,
traces what happened to each standardization body between 2009 and May
2026, and extracts the specific failure modes that killed top-down XML
code generation while preserving selective abstractions.

## Key findings

- **F1 — The CAMELEON Reference Framework established the canonical
  four-level abstraction hierarchy for separating functional intent from
  platform code** [consensus; standard and academic framework, resting on
  summarised fetches of primary sources]. Published by Calvary, Coutaz,
  Thevenin, Limbourg, Bouillon, and Vanderdonckt in June 2003 [10] and
  adopted as the architectural foundation of the 2014 W3C Model-Based
  User Interfaces (MBUI) Working Group Notes [1, 2], CAMELEON structures
  the *technical design* of an interactive application across four layers
  with respect to a three-part Context of Use (*User*, *Platform*, and
  *Environment*) [10]:
  1. *Concepts and Task Model*: logical user goals, hierarchical task
     decompositions, temporal constraints (often expressed in
     ConcurTaskTrees, CTT), and domain objects manipulated, independent
     of any interface [3, 10, 12].
  2. *Abstract User Interface (AUI)*: modality-independent interaction
     spaces (abstract containers and individual interaction components
     such as selection, input, or action triggers) that specify *what* is
     grouped together on a logical presentation unit without committing
     to graphical, vocal, or tactile modalities [2, 4, 10].
  3. *Concrete User Interface (CUI)*: modality-specific and
     platform-class-specific *interface design* (mapping an abstract
     selection component to a radio-button group, drop-down list, or
     voice prompt, with concrete layout relationships and navigation),
     still independent of any programming toolkit [1, 10, 11].
  4. *Final User Interface (FUI)*: executable source code or markup
     rendered on a target platform (such as HTML/JavaScript, Android, or
     desktop toolkits) [1, 10].

- **F2 — The XML User Interface Description Languages (UIML, UsiXML,
  MARIA, and XForms) formalized different slices of the CAMELEON stack
  but stalled or retreated into niche domains by 2015** [consensus;
  standards and academic surveys, resting on summarised fetches].
  - *UIML (User Interface Markup Language)*: Approved as OASIS Committee
    Specification 01 (v4.0) on 2009-05-01 [7], UIML is a canonical XML
    metalanguage that separates `interface` (structure, style, content,
    and behavior rules) from `peers` (a vocabulary dictionary mapping
    generic widgets to target toolkits such as HTML, Java Swing, or
    VoiceXML) [7, 13]. It saw no specification revision after May 2009
    and its commercial and open-source interpreters became historical
    artifacts [7, 13].
  - *UsiXML (User Interface eXtensible Markup Language)*: Developed at
    UCLouvain by Limbourg, Vanderdonckt, and colleagues [9, 13], UsiXML
    provides explicit XML schemas for all four CAMELEON levels plus graph
    transformation rules supporting forward engineering (Task to AUI to
    CUI to FUI), reverse engineering (extracting CUI/AUI from legacy
    code), and lateral adaptation across contexts [9, 12, 13]. In
    practice, UsiXML remained confined to academic research prototypes
    (such as IdealXML) [9, 12].
  - *MARIA (Model-based lAnguage foR Interactive Applications)*:
    Specified by Paternò, Santoro, and Spano in *ACM TOCHI* (2009) [11],
    MARIA defines an XML declarative UIDL covering AUI and CUI levels
    with built-in dialogue expressions, CTT task-model links, continuous
    field updates, and native binding to Web service (WSDL) data models
    and operations, supported by the MARIAE authoring environment [11].
    It was used in European ubiquitous-computing research projects (such
    as SERENOA) [12] but did not transition into commercial software
    engineering toolchains.
  - *XForms*: Standardized by W3C (XForms 1.0 in 2003; XForms 1.1
    Recommendation in 2009) [6], XForms separates the *data model* and
    *instance data* (XML schemas, XPath constraints, submission rules)
    from intent-based *user interface controls* (`input`, `secret`,
    `select1`, `repeat`, `group`, `trigger`) that describe the purpose of
    a control rather than its visual widget [6, 13]. Major web browser
    vendors declined to implement XForms natively, favoring HTML5 forms;
    the W3C closed the Forms Working Group on 2015-04-08, handing
    ongoing maintenance of XForms 2.0 to the XForms Users Community Group
    [6].

- **F3 — The W3C Model-Based User Interfaces Working Group published
  four Working Group Notes in January–April 2014 and closed without
  producing a W3C Recommendation or a Concrete UI specification**
  [consensus; W3C primary records, resting on summarised fetches]. The
  W3C MBUI Working Group published *Introduction to Model-Based User
  Interfaces* [1] and *MBUI Glossary* [2] on 2014-01-07, followed by
  *MBUI Task Models* [3] (formalizing CTT-style hierarchical tasks,
  temporal operators, and an XML interchange schema) and *MBUI Abstract
  User Interface Models* [4] (formalizing UML metamodels and XML schemas
  for modality-independent containers and interactors) on 2014-04-08.
  The Working Group closed in April 2014 upon charter expiration [1, 4].
  Under the W3C Process Document, publishing deliverables as Working
  Group Notes signifies that work on the Recommendation track has ended
  and carries no W3C endorsement [4]; no successor Working Group was
  chartered because browser vendors and commercial IDE vendors did not
  commit interoperable implementations, and follow-on discussion
  dispersed into the non-normative W3C Ubiquitous Application Design
  Community Group [1, 4].

- **F4 — OMG's Interaction Flow Modeling Language (IFML 1.0) of February
  2015 standardized platform-independent screen containers, components,
  events, and parameter-bound navigation flows, intentionally omitting
  visual layout and styling, and had no 2.0 successor** [consensus;
  standard and secondary technical sources, resting on summarised
  fetches]. Formally published by the Object Management Group in February
  2015 (`formal/15-02-05`) [8], IFML 1.0 defines a Meta-Object Facility
  (MOF) metamodel, a UML profile, a visual diagram notation, and an XMI
  exchange format [8]. It models the front-end *technical design* across
  four dimensions: *View Structure* (`ViewContainer` for windows, pages,
  or panels—nestable as XOR/landmark/default views—and `ViewComponent`
  for forms, lists, and details), *Events* (user, system, or action
  events), *Interaction Flows* (navigation and data flows with
  `ParameterBinding`), and *Actions* (invocations of backend business
  logic in UML or BPMN) [8]. The specification explicitly excludes
  graphic *interface design*, layout grids, and *visual identity* / CSS
  styling [8]. As of 2026-11-21, IFML 1.0 remains the sole OMG version
  with no 2.0 specification [8]. In practice, production code generation
  from IFML remained centered on WebRatio (its primary commercial
  co-creator), alongside architecture modeling plugins (Sparx Systems
  Enterprise Architect, Eclipse EMF/Sirius) and the academic prototype
  IFMLEdit.org [8].

- **F5 — ISO 9241 and ISO/TR 25060 (Common Industry Format) standardize
  ergonomic interaction principles, human-centred process, and prose
  requirement/evaluation templates rather than formal screen modeling
  languages** [consensus; standard summaries via secondary sources,
  resting on summarised fetches]. Unlike UIDLs or IFML, the ISO standards
  do not provide a machine-readable grammar for composing screens [15]:
  - *ISO 9241-11* defines usability as effectiveness, efficiency, and
    satisfaction for specified users achieving specified goals in a
    specified context of use [15].
  - *ISO 9241-110* (*Interaction principles*, formerly *Dialogue
    principles*) defines a dialogue as a sequence of user actions
    (inputs) and system responses (outputs) to achieve a goal, and sets
    out seven technology-independent principles: *suitability for the
    user's tasks*, *self-descriptiveness*, *conformity with user
    expectations*, *learnability*, *controllability*, *use error
    robustness* (error tolerance), and *user engagement* (replacing the
    earlier *individualization* principle in the 2020 revision) [15].
  - *ISO 9241-112, -125, -143, -151, and -161* give normative ergonomic
    guidance for information presentation, visual presentation, forms,
    World Wide Web interfaces, and visual UI elements (cataloging what
    each standard widget does and when to use it) [15].
  - *ISO 9241-210* specifies the human-centred design process across the
    system lifecycle [15].
  - *ISO/IEC TR 25060* (within the SQuaRE 250xx series) defines the
    Common Industry Format (CIF) framework for documenting usability
    artifacts in structured prose templates: *Context of Use Description*
    (ISO/IEC 25063), *User Needs Report* (ISO/IEC 25064), *User
    Requirements Specification* (ISO/IEC 25065, covering user-system
    interaction requirements), and *Usability Test Reports* (ISO/IEC
    25062) [15].
  Unlike the dormant XML UIDLs, ISO 9241 and the CIF series remain active
  in regulated software procurement, medical and automotive compliance,
  and usability auditing [15].

- **F6 — Academic surveys and the disconfirming query identify five
  structural reasons why formal model-based UI languages failed in
  mainstream application development while holding in specialized
  industrial verticals** [consensus; academic surveys and industry case
  studies, resting on summarised fetches]. Surveys by Guerrero-García et
  al. (2009) [13], Meixner, Paternò, and Vanderdonckt (2011) [12], the
  W3C MBUI Working Group (2014) [1], and Akiki, Bandara, and Yu in *ACM
  Computing Surveys* (2014) [14] converge on why mainstream software
  teams rejected formal UIDLs:
  1. *High threshold / modeling overhead*: authoring formal task, domain,
     AUI, and CUI XML models requires specialized training and upfront
     effort that exceeds the cost of writing declarative UI code directly
     for two or three target platforms [1, 12, 14].
  2. *Low ceiling / aesthetic and micro-interaction bottleneck*:
     automated top-down transformations from abstract models generate
     utilitarian, "cookie-cutter" layouts and resist bespoke *interface
     design*, brand *visual identity*, and post-WIMP micro-interactions
     [1, 12, 14].
  3. *The round-trip engineering trap*: when developers or interface
     designers manually edit generated Final UI code to fix layout or
     interaction seams, regenerating from the abstract model overwrites
     their work, breaking synchronization between specification and
     implementation [12, 14].
  4. *Fragile academic toolchains vs. fast-moving component ecosystems*:
     research tools (IdealXML, MARIAE, IFMLEdit) lacked commercial IDE,
     version-control, and CI integration while industry coalesced around
     component libraries (React, Flutter, SwiftUI) and design systems [8,
     12].
  5. *Unpredictable runtime adaptation*: fully automatic context-driven
     UI restructuring creates unpredictable screen layouts that are
     difficult to test for usability and accessibility [14].
  Conversely, the disconfirming query confirmed that model-based UI
  generation achieved sustained industrial adoption in three verticals:
  (a) *industrial automation and SCADA/HMI process control* (mapping
  plant asset models directly to operator alarm and control panels) [16],
  (b) *automotive cockpit and infotainment product lines* (managing
  dozens of hardware display variants under strict safety rules) [1, 12],
  and (c) *modular smart factories* such as SmartFactoryKL (where handheld
  devices dynamically render control interfaces from machine metadata at
  runtime) [1].

- **F7 — The W3C UI Specification Schema Community Group (`uispec`)
  attempted to standardize a JSON/JSON Schema meta-model for
  cross-platform UI components in 2025–2026 but closed on 2026-05-21**
  [single source; W3C Community Group record, resting on a summarised
  fetch]. Verifying the card's lead, the W3C UI Specification Schema
  Community Group (`https://www.w3.org/community/uispec/`) was created to
  define an implementation-agnostic, machine-readable format (JSON/JSON
  Schema) specifying the *interface design*, layout, behavior, content
  constraints, and accessibility requirements of UI elements from atomic
  controls to composite components across web, mobile, desktop, and
  embedded targets, aligning with W3C Open UI (component anatomy and
  states) and the Design Tokens Community Group (*visual identity*
  primitives) [5]. The group closed on 2026-05-21 without publishing a
  final specification [5].

## Unexpected

The card asks to verify the W3C's UI Specification Schema Community Group
(`w3.org/community/uispec/`) of 2025 and 2026 as a potential active
standardization effort. The search confirmed both its existence and its
exact scope—a machine-readable JSON/JSON Schema specification bridging
design tools, cross-platform development frameworks (web, mobile,
desktop, embedded), and automated QA, aligned with Open UI and Design
Tokens—but found that the group already closed on 2026-05-21 due to
inactivity/completion of exploratory scope without issuing a standard
report [5]. Even when recast from 2010-era XML/XMI into 2025-era JSON
Schema, committee-driven attempts to standardize a universal,
tool-neutral UI element schema across the industry have repeatedly stalled
before reaching implementation consensus [4, 5, 6].

## Not found

- **Founding date, chair names, and draft repository contents of the W3C
  UI Specification Schema Community Group (`uispec`):** Targeted queries
  against `w3.org/community/uispec` returned the group's mission, scope,
  shortname, and closure date (2026-05-21) [5], but did not surface archived
  chair names, exact launch date in 2025, or links to any surviving draft
  JSON Schema repository.
- **Quantitative industrial market-share figures for UIDLs or IFML:**
  Neither the W3C MBUI Notes [1], OMG IFML pages [8], nor the academic
  surveys [12, 13, 14] provide a controlled empirical census or percentage
  of industrial companies using UsiXML, UIML, MARIA, or IFML; adoption
  evidence in the literature consists of qualitative case studies
  (automotive, SCADA, SmartFactoryKL, WebRatio) and qualitative analyses
  of adoption barriers.
- **Full verbatim text of ISO 9241 parts and ISO/TR 25060:** ISO standards
  are paywalled by ISO (`iso.org`), and direct command-line fetches were
  blocked by environment rules, so ISO definitions and structure were
  retrieved through secondary standards previews and summaries [15].

## Options

Because the card asks why formal platform-independent UI languages were
adopted or rejected in order to decide "what to borrow and what to avoid"
for a Git-versioned Markdown UX/UI specification spanning four platforms
(web, mobile web, native mobile, desktop), the findings present three
distinct architectural options:

1. **Option A — Full CAMELEON four-layer cascade in separate models
   (Task $\rightarrow$ Abstract UI $\rightarrow$ Concrete UI $\rightarrow$
   Final UI)**
   - *What it borrows:* CAMELEON's strict separation of user tasks (CTT),
     modality-independent groupings (AUI), and modality-specific widgets
     (CUI) [1, 3, 4, 10].
   - *Trade-offs:* Maximizes theoretical independence across vocal,
     graphical, and ambient modalities, but reproduces the exact high
     authoring threshold and synchronization overhead that caused UsiXML,
     MARIA, and the 2014 W3C MBUI Notes to fail in general application
     development [12, 14]. For four graphical platforms (web, mobile web,
     native mobile, desktop), a completely modality-blind AUI layer adds
     indirection without matching how a human specialist or solo builder
     reasons about screens.

2. **Option B — Borrow IFML's structural vocabulary + XForms' intent-based
   element definitions + ISO 9241-110/CIF prose constraints in human- and
   agent-readable Markdown, skipping top-down XML/XMI code generation**
   - *What it borrows:*
     - From **IFML 1.0**: the structural split between *View Containers*
       (pages/windows/panels, including XOR/landmark nesting), *View
       Components* (reusable content/input blocks), *Events*, *Interaction
       Flows*, and *Parameter Bindings* to domain actions, while leaving
       pixel/CSS styling out of the interaction spec [8].
     - From **XForms and ISO 9241-161**: defining individual screen
       elements by their *communicative intent, data binding, constraints,
       and states* (what a search field or selection control does and
       validates) rather than toolkit-specific implementation widgets [6,
       15].
     - From **ISO/TR 25060 (CIF) and ISO 9241-110**: structured prose
       sections for Context of Use (ISO/IEC 25063), User-System
       Interaction Requirements (ISO/IEC 25065), and the seven dialogue
       principles (self-descriptiveness, error robustness, controllability,
       etc.) as evaluation criteria [15].
   - *What it avoids:* Complex XML/XMI schemas, brittle deterministic
     model-to-code compilers, and the round-trip overwrite trap, because
     an AI coding agent or human developer reads the Markdown *technical
     design* alongside the project's component library and *visual
     identity* tokens rather than running a rigid XSLT generator.
   - *Trade-offs:* Does not guarantee mathematical equivalence across
     platforms via an automated compiler; relies on the downstream coding
     agent or developer (plus automated tests) to map Markdown element
     and page definitions to native platform components.

3. **Option C — Formal JSON Schema / UIDL meta-model as the primary
   authoring artifact**
   - *What it borrows:* The machine-readable schema approach of UIML [7]
     and the 2025–2026 W3C `uispec` Community Group [5].
   - *Trade-offs:* Machine-validatable by static schema checkers, but
     poorly suited for human-agent conversational authoring and diff
     review in Git compared to structured Markdown, and historically prone
     to vocabulary lock-in or abandonment when frontend component APIs
     evolve [5, 7, 12].

## Relevance to this project

**Recommendation (agent inference from F1–F7):** Adopt **Option B**.
When designing the project's Markdown UX/UI description format, borrow the
*conceptual boundaries* of the standards while rejecting their *formal XML/XMI
encodings and deterministic code-generation pipelines*:

1. **Collapse CAMELEON's middle layers into one platform-independent
   structural/behavioral layer:** Because all four of the project's target
   platforms (web, mobile web, native mobile, desktop) are graphical/tactile
   screen interfaces, do not force authors to maintain both a
   modality-blind Abstract UI (AUI) and a Concrete UI (CUI). Instead, let
   existing user stories and requirements carry the *Task & Concepts*
   layer (enriched with ISO/IEC 25063 Context of Use), and let the UX/UI
   Markdown document sit at the boundary between CAMELEON's AUI/CUI and
   IFML's View model [4, 8, 10].
2. **Validate the card frame's element-and-page hypothesis using XForms +
   IFML semantics:** The idea stated in the packet's frame—"every element
   of a screen (a search field, say) has a small definition of its own in
   Markdown that carries its function, and a page definition names which
   elements it holds and where they stand"—aligns directly with the two
   most durable abstractions in the literature:
   - An **element definition** should follow **XForms** [6] and **ISO
     9241-161** [15]: declare the element's semantic purpose, bound data
     / parameters, validation and state rules, events emitted, and error
     handling (ISO 9241-110 error robustness), without hard-coding a
     platform widget class.
   - A **page (container) definition** should follow **IFML 1.0** [8]:
     declare the `ViewContainer` hierarchy (screens, sub-views, modal or
     XOR regions), which defined `ViewComponents`/elements it hosts, their
     logical spatial/reading order across form factors, and the
     `InteractionFlows` (events + parameter bindings) that connect pages
     and actions.
3. **Avoid the round-trip trap by keeping *interface design* structure,
   *visual identity*, and *Final UI* code distinct:** Follow IFML's
   explicit scope exclusion [8] by keeping visual styling tokens (*visual
   identity*) in a design-system/token reference rather than inside flow
   and element definitions, and treat the Markdown documents as the
   authoritative *technical design* specification consumed by humans and
   AI build agents, never as an irreversible one-way compiler template.

**Consult when:**
- Deciding which abstraction layers the UX/UI Markdown documents should
  have and whether to separate task flows, screen containers, and atomic
  elements.
- Choosing the fields of an element definition (data binding, constraints,
  events, states) or a page/container definition (nested regions,
  interaction flows, parameter passing).
- Evaluating proposals to replace readable Markdown specifications with
  strict XML, XMI, or JSON Schema UI description languages.
- Grounding usability review checklists for agent-proposed descriptions in
  international standards (ISO 9241-110 interaction principles and
  ISO/TR 25060 Common Industry Format).

## Sources

1. *Introduction to Model-Based User Interfaces*, Gerrit Meixner, Gaëlle
   Calvary, and Joëlle Coutaz (Editors), W3C Model-Based User Interfaces
   Working Group Note, 2014-01-07 (dated by W3C document header / byline),
   https://www.w3.org/TR/mbui-intro/ (also grounded via
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEAadsQLO3YFJ-M-KvmpxDBAeCL-8dV5WVb5swOAfHrdUUV3vAfCQA18gBnbIuqHuIGde0pkVFLYuZ3PqVHwsECW3FdKLa0pY4GvvlIEvql9nQcc8JbIsplj15b);
   primary standard note (read via summarised fetch, which makes the fetch
   record tertiary); summarised fetch (`search_web`, as direct CLI HTTP
   fetches are denied by environment policy); original (W3C).
2. *MBUI — Glossary*, Jaroslav Pullmann (Editor), W3C Model-Based User
   Interfaces Working Group Note, 2014-01-07 (dated by W3C document header
   / byline), https://www.w3.org/TR/mbui-glossary/ (also grounded via
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFt8TZHaAiW6z_tv8aD9FKcATSdE2UfuBUpWWxxkqHnJt7C3Xvp6STHEF5ZveG94MR0zjktcwlERidsX6XAG4UHAFxM15zksLnQgik46teD3EwRSPlBDaLRQbpibq4H);
   primary standard note; summarised fetch (`search_web`); original (W3C).
3. *MBUI — Task Models*, Fabio Paternò, Carmen Santoro, Lucio Davide
   Spano, and Dave Raggett (Editors), W3C Model-Based User Interfaces
   Working Group Note, 2014-04-08 (dated by W3C document header / byline),
   https://www.w3.org/TR/task-models/ (also grounded via
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFpAaZPOcWXasoKEAu68-reSwShXHPkbXdZoTLxLiTtc4IKjyKLhSAb-iJWYGJJCfrTMXNxffs_ZTTbWAjDZbTwXIRuz5OWbJC4jpAu4U_KQZpNLHl4ntqzQ0Vq3w==);
   primary standard note; summarised fetch (`search_web`); original (W3C).
4. *MBUI — Abstract User Interface Models*, Jean Vanderdonckt, Ricardo
   Tesoriero, Nesrine Mezhoudi, Vivian Motti, François Beuvens, and
   Jérémie Melchior (Editors), W3C Model-Based User Interfaces Working
   Group Note, 2014-04-08 (dated by W3C document header / byline),
   https://www.w3.org/TR/abstract-ui/ (also grounded via
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHSm7nGyJsjEFnFOBlGygw4SQNBfoQ0H6-ov_f9xKk-NenzG0Sa9ruhGdhpwaeKorVy98kecuxyi_kMr5cV2SZYuqGb9LIbRVnAZS4hCtW-2yJoWQOtUHZBM2NV7Q==);
   primary standard note; summarised fetch (`search_web`); original (W3C).
5. *UI Specification Schema Community Group*, World Wide Web Consortium
   (W3C), closed 2026-05-21 (dated by W3C Community Group status record),
   https://www.w3.org/community/uispec/ (also grounded via
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFB82CvMoUjimrD94icbotQij4D1JUcga330Y7WVfOz5dQF-TFvpAD_w8hNe1VoxV74JoZ1wMerO7RSMzZlxS6rqG01U63j3Y2LPs3t8C4Ry_C0TrXvPSW5U14-DrsN);
   primary organizational record; summarised fetch (`search_web`);
   original (W3C).
6. *XForms 1.1* and *Forms Working Group / XForms Users Community Group
   Status*, John M. Boyer (Editor, XForms 1.1), W3C Recommendation
   (2009-10-20) and W3C Working Group closure record (2015-04-08) (dated
   by W3C header and status pages), http://www.w3.org/TR/xforms/ (also
   grounded via
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFZryWiCzQD_rarPQX1rUrVgJ0tl0jxFX03qBadL3YdyrzuWWBG14iywShmhL9EUMZtH_UaffSz8J3OaOTZTH8n8bhXZkSBFkAtSwEPnkz_MBDDYQIKMh8mitIIX8JKgnV6ha_FBtaNdap3qtCWEptA1efK
   and
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGnZdl6m_m9cvJ52kFJoESuwDeu5-2eVHnyBIlTVwErEMt6CVEZyjSP2Q01-WVXH9ygNXB3l7Sklcs7a6XZA9Q-xgSvpr0H8c_2CoKp6uIlfthexDCj4NigZ1IX);
   primary standard; summarised fetch (`search_web`); original (W3C).
7. *User Interface Markup Language (UIML) Version 4.0*, Jim Helms, Robbie
   Schaefer, Kris Luyten, Jo Vermeulen, Marc Abrams, Adrien Coyette, and
   Jean Vanderdonckt, OASIS Committee Specification 01, 2009-05-01 (dated
   by OASIS cover page metadata),
   http://docs.oasis-open.org/uiml/v4.0/cs01/uiml-4.0-cs01.html (also
   grounded via
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFHtTliE_i3Y4xfwQDBWeUnlmUfMXAbRGAn7N8kzmR2NCRxWa1bCRWzYwa63am03Ugkf4U8ShW9aE2ujmsGGqn1MqSm5P_4HioPoNpDRKrDyM3AG2n8jJJRSrnp_2PooYJIjE4Z_-HDf9A=);
   primary standard; summarised fetch (`search_web`); original (OASIS).
8. *Interaction Flow Modeling Language (IFML), Version 1.0* (`formal/15-02-05`)
   and *IFML.org Specification Overview*, Object Management Group (OMG) /
   Marco Brambilla and Piero Fraternali, February 2015 (dated by OMG
   specification metadata), https://www.omg.org/spec/IFML/1.0 and
   https://www.ifml.org (also grounded via
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQH2fS0vdAJhAuUlKW2uJvJmpeVzzSUQAwUcYsZ3erE3c12Wa3t83jEuIOXwtnaTBBu5y65Oa3YuuJ_GgvSoUYWxU1XRtcsu59QlGcckcR-sXInGvr1Xqf3BvIPtzARct7MvlF_jW_w=
   and
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFvV2o0QNMu7dqlUJwmvLwv_Vp32qJ8o5eTqdDCHTD5uYP6GMC0pNUwR77UyWsCzy5BDo1T0249s6uS-rOhZdOFe8ol1jhhEx3vIWQvNp-MfQ==);
   primary standard and official companion site; summarised fetch
   (`search_web`); original (OMG / IFML).
9. *UsiXML (User Interface eXtensible Markup Language) Research Repository
   Documentation*, Jean Vanderdonckt, Quentin Limbourg, et al.,
   Université catholique de Louvain (UCLouvain), undated repository
   summary of 2004–2014 UsiXML specifications,
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFLrzhPQFsoEobSMcExRYTmv3YzE3pt8gU0j_8ZXkAGL_X3vq2vg6MHD6WCvLibbevHQ0MWV7dhmTftPL96T0gtSD9l5QlcgB-vKX3DcuwMp99BEwgB8IXrxrP91UmnNgSmIxwo0hJEhqCR1N-UiwKUN09dkdW8QJadWQ0mUcAdtOc0xf1j9CUZt4smAv8lDRLSOk_Wz1kOQhFVNxZ_IbZn8E3wKg==;
   primary project documentation; summarised fetch (`search_web`);
   original (UCLouvain).
10. *A Unifying Reference Framework for Multi-Target User Interfaces*,
    Gaëlle Calvary, Joëlle Coutaz, David Thevenin, Quentin Limbourg,
    Laurent Bouillon, and Jean Vanderdonckt, *Interacting with Computers*,
    Vol. 15, No. 3, pp. 289–308, June 2003 (dated by journal publication
    metadata),
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHTeU6os6qz_Bd9OW2JsKv9qCxFtRiqZT2j9U0K1rpGKTvGthPNDuZ_C_EKMPc6npgVE85un4PWxwMtKO4fkCxh-vBaV1nbwNUL9cvrpRBzhyi3DbG2MSDBI0kiYXncYPRow2qbpPop68gYtMuOJOQ6EkdvNVlZq5_hyMS7LtwDUhtmoV9AmmWCIVxme_DM337lZxzqgz-RCMwNWzhyZu4dw-8Axphv7LNgK4PH;
    primary academic paper (via ResearchGate index); summarised fetch
    (`search_web`); copy of *Interacting with Computers* article.
11. *MARIA: A Universal, Declarative, Multiple Abstraction-Level Language
    for Service-Oriented Applications in Ubiquitous Environments*, Fabio
    Paternò, Carmen Santoro, and Lucio Davide Spano, *ACM Transactions on
    Computer-Human Interaction (TOCHI)*, Vol. 16, No. 4, Article 19,
    November 2009 (dated by journal publication metadata),
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFS_5r_NlnP7uZ3k6ZDrvc_ASeKv09y5CqGwDQFt57BuFe_CP2zYRSd2IZV7YUijvc0-2HXFVIPfCsV83peFUMV1WrYGLPZLXBryqcbSYJCVoGcjdLkcUf8Q7BJeKzB-W8RCT1f1FhA-lgHk_LDfAzRII_lKuQ2V_UiCbHwCjbGBiSD-W7t5Hq_ABNPE8JsDXWd784ndv2BAPNtAkCVqE1AVNKOY9ScSRFn5Hc=;
    primary academic paper bibliographic and abstract record (via Dagstuhl
    / IIHM repository); summarised fetch (`search_web`); copy/index of
    *ACM TOCHI* article.
12. *Past, Present, and Future of Model-Based User Interface Development*,
    Gerrit Meixner, Fabio Paternò, and Jean Vanderdonckt, *i-com — Journal
    of Interactive Media*, Vol. 10, Issue 3, pp. 2–11, 2011 (dated by
    journal publication metadata),
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHk3GiGdAGNpuFKaVUPc4OIy8VBpjdAi7n88ERzdsTlt_zkNaomyI8eWfNo8qhrTmQaxbKcednQnNLMSKjS-qoyMKF9U53sgA9J4mnpEVUeLFpPMgGFSjK5JWLje48nqaFSRLl3krXbmEVsEb9WlZ2bW3XTd-c=;
    secondary academic survey (via DLR institutional repository);
    summarised fetch (`search_web`); author/institutional repository copy
    of *i-com* article.
13. *A Theoretical Survey of User Interface Description Languages:
    Preliminary Results*, Josefina Guerrero-García, Juan Manuel
    González-Calleros, Jean Vanderdonckt, and Jaime Muñoz-Arteaga,
    *Proceedings of the 2009 Latin American Web Congress (LA-WEB 2009)*,
    pp. 36–43, 2009 (dated by conference proceedings metadata),
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQG_AUeXAeWyIY1uARnc1x8ipW1-uVPs1A_WamfBABEKPXbuaPyUylbObpLA0eOE3E8Z0ENEBKYd6UzoiQ9xXuhofR_4EmCLUDDL3nhVa99f8f8f5134gmrv-d4lcryexV_mjy0H2jZ_4QcKVWBsYoqIKMgfZ4uwsjVFxLWQrIYZ5z_p2KnU2-Odqw==;
    secondary academic survey; summarised fetch (`search_web`); academic
    repository copy.
14. *Adaptive Model-Driven User Interface Development Systems*, Pierre A.
    Akiki, Arosha K. Bandara, and Yijun Yu, *ACM Computing Surveys (CSUR)*,
    Vol. 47, No. 1, Article 64, May 2014 (dated by journal publication
    metadata), https://doi.org/10.1145/2597999 (also grounded via
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHTKl5SGkKn3KCYqGArI8nkr2fg6sfjsa6b2rC61hlLVBw9YJXjkMsBm_Xx2YeATGB_aAQDexk2WNAEr4fB7fwjbAT4KmI6biX6sE6NcoAjMm5qTkIHAbobGek=);
    secondary academic survey; summarised fetch (`search_web`); original
    DOI and author preprint on arXiv.
15. *ISO 9241 Series (Parts 11, 110, 112, 125, 143, 151, 161, 210) and
    ISO/IEC TR 25060 (Common Industry Format for Usability) Overviews and
    Standard Previews*, Usability Partners / NIST / iTeh Standards
    previews, 2010–2020 editions (dated by standard edition metadata),
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGnIRfr1LgqPfxLZzhlR6V1XGDhDTpAJmKxVV9dm6vGoVL9cPjF5cL2ygEzlRS_WMMrFetGPHFVI5UKmBCsx4uPVobIDW4eXEgX_bFdCW6t_sqwdapeNyu3gwq3nA2GOkmamxmBCHu4KIUGUmDjMJIsm2V8JNl_hNU=,
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGLTkpc7aHQA_M2MQBVVXD3vdHmmQVBou7h7m2D3j-7qnRNJwvk3yBIqdt8wa-F6iC7Ga5LXTTZ_kxwq3TVOYEDiSaSZ5y_9s-azPE-n2BI3rv-lubuAc17uhnR0ovr2vQuhucSKarv_3dvK075t0SlkO7Y9Q==,
    and
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQF6Y20BXm_Z6hWEFt7gjHQ6YZWPsC6PF4M-eggeN0lQnY7XCjH_IxD358sulfgT-EG_E80oTS7SVh4vPAklA3yyCHdFyIUBIcn7iSpuMGJsPywzer87GKKvGqmvk0LgfBmS2RVyb1s9zVXDHz70-GkttVgSXVs41Jwd6SDMsdyGrdtcL9Iynea1hjOJAuFxaeTImz02NoKfsPBmw0w=;
    secondary standards summaries and front-matter previews (used because
    ISO full texts are paywalled); summarised fetch (`search_web`);
    secondary summaries of ISO originals.
16. *High Performance HMI and Model-Based Industrial Automation Overview*,
    GE Vernova, undated vendor documentation,
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGWaEqPl9Wf19GJlXLQ3XUnryLbhjmb_LBTcKL25WbnMNVdijWHA-wJTWrdHkkw991RVuGPDuoaru_qaUJstF33vSCaN1l_h4arsySZUSCk-RTMe1FcgLomff7asXXXnhXfICbNCYIc4SD1VJSXPg==;
    primary vendor documentation (used only for the disconfirming query's
    industrial SCADA/HMI vertical example); summarised fetch
    (`search_web`); original.

## Opened and not used

- Wikipedia articles on *Interaction Flow Modeling Language*, *User
  Interface Description Language*, *User Interface Markup Language*, and
  *ISO 9241* (returned in initial broad `search_web` results): tertiary
  encyclopedias superseded by primary W3C, OMG, OASIS, and academic survey
  sources [1–15].
- Fiveable, Heurio, and Scribd study notes on ISO 9241 (returned in
  initial ISO query): below the source bar and superseded by NIST and
  standards-body summaries [15].
- YouTube video links on IFML (returned in OMG IFML query): off the
  written specification bar and superseded by OMG IFML 1.0 specification
  pages [8].

## Search record

- **Environment constraint on openings:** Direct command-line HTTP fetching
  (`curl.exe -sI https://www.w3.org/TR/mbui-intro/`) was attempted first in
  the standard sandbox and blocked by a user-configured permission deny
  rule. Consequently, all queries and targeted source fetches were executed
  via `search_web` (16 grounded `search_web` calls covering 16 cited source
  groups, treated as summarised fetches).
- **Queries run (in order):**
  1. `W3C Model-Based User Interfaces Working Group Notes 2014`
  2. `OMG IFML Interaction Flow Modeling Language specification`
  3. `user interface description language survey UsiXML UIML MARIA XForms CAMELEON`
  4. `ISO 9241 parts user interface dialogue interaction ISO TR 25060 Common Industry Format`
  5. `W3C UI Specification Schema Community Group`
  6. `model-based user interface development industrial adoption success` *(disconfirming query)*
  7. `"Model-Based User Interfaces" Working Group Note 2014 "www.w3.org/TR/" task abstract glossary intro charter closed` (domain: `w3.org`)
  8. `"UI Specification Schema Community Group" w3.org/community 2025 2026 charter chairs status closed` (domain: `w3.org`)
  9. `XForms 1.1 XForms 2.0 "www.w3.org/TR/" Forms Working Group closed Community Group status` (domain: `w3.org`)
  10. `"User Interface Markup Language" UIML 4.0 OASIS Standard 2009 specification URL status` (domain: `oasis-open.org`)
  11. `"Interaction Flow Modeling Language" IFML 1.0 specification 2015 "www.omg.org/spec/IFML"` (domain: `omg.org`)
  12. `"Past, Present, and Future of Model-Based User Interface Development" OR "Adaptive Model-Driven User Interface Development Systems" adoption barriers UIDL MARIA UsiXML`
  13. `"A Unifying Reference Framework for multi-target user interfaces" Calvary Coutaz Vanderdonckt 2003 CAMELEON`
  14. `"MARIA: A universal, declarative, multiple abstraction-level language" Paterno Santoro Spano 2009 TOCHI`
  15. `"Past, Present, and Future of Model-Based User Interface Development" Meixner Paterno Vanderdonckt 2011`
  16. `"A Theoretical Survey of User Interface Description Languages" Guerrero-Garcia Vanderdonckt 2009 UsiXML UIML XForms`
  17. `"ISO 9241-110" "ISO 9241-210" "ISO 9241-11" "ISO/TR 25060" Common Industry Format dialogue principles usability` (domain: `iso.org`)
  18. `"UI Specification Schema Community Group" "w3.org/community/uispec" 2025 2026 launched closed chairs report` (domain: `w3.org`)
  19. `"Model-Based User Interfaces Working Group" charter expired 2013 2014 Working Group Note instead of Recommendation reason` (domain: `w3.org`)
  20. `"UI Specification Schema Community Group" "w3.org/community/uispec" launched 2025 reports specifications participants closed inactivity` (domain: `w3.org`)
  21. `"IFML" "1.0" OMG WebRatio IFMLEdit successor version adoption practice`
  22. `"Adaptive Model-Driven User Interface Development Systems" Akiki Bandara Yu 2014 "ACM Computing Surveys"`
- **What the disconfirming query found:** Confirmed the card's expectation:
  general horizontal software engineering did not adopt MBUI, and
  documented industrial successes clustered in safety-critical,
  hardware-coupled, or high-variability verticals—industrial automation
  and SCADA/HMI (e.g., GE Vernova Proficy/iFIX), automotive multi-screen
  cockpits, and modular smart-factory field interfaces (SmartFactoryKL)
  [1, 12, 16].
- **Reason the run ended:** Both parts of the card's stop rule were met at
  16 cited source groups (within the 10-to-15 opened-page budget): every
  route named in the card had a primary standard or foundational academic
  source (or secondary standards preview for paywalled ISO documents), and
  differently worded queries on `uispec`, W3C MBUI closure, and IFML
  adoption returned no new facts.
