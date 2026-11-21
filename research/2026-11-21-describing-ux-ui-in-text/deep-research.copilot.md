origin: pasted into the conversation by the principal on 2026-11-21; the report of Microsoft Copilot's deep research on the single assignment written for built-in deep research tools from the plan of the research bundle `2026-11-21-describing-ux-ui-in-text` (`tmp/research/2026-11-21-describing-ux-ui-in-text/deep-research-prompt.md`, not in git); the style block of the page left out at the ingest, the rest word for word as it was pasted
date: 2026-11-21

Textual UI/UX Description Before Implementation
Evidence-led survey and pilot recommendation
Executive summary
<div class="insights-container">
 <div class="insight-card">
  <h4>No single finished method</h4>
  <p>Public practice is fragmented across screen-design documents, flows, object models, design systems, formal UI languages, page schemas, prototypes, and agent protocols.</p>
 </div>
 <div class="insight-card">
  <h4>Best pilot: screen-centred, not screen-only</h4>
  <p>Use one readable Markdown file per screen, small structured sections for regions, states and references, separate path diagrams, and links—not copies—to rules, objects and components.</p>
 </div>
 <div class="insight-card">
  <h4>Text is a contract, not the whole truth</h4>
  <p>Pair text with a generated visible preview and, later, design-system/Figma and implementation mappings. Visual, behavioral and runtime truths cannot safely remain in prose alone.</p>
 </div>
</div>


Main finding. I found no publicly documented, substantially complete workflow that starts with requirements, maintains human/AI-authored textual UI definitions, composes screens from per-element Markdown files, previews them, synchronizes them with design tooling, generates four-platform implementations, and verifies the result. The closest evidence is a set of fragments, not a finished shape:

Japanese gamen sekkeisho combines a numbered screen image with item tables, display conditions, validation, CRUD, actors and messages; related screen lists, transitions and message documents remain separate.
Mature design systems define reusable components and patterns, plus tokens and implementations; Carbon explicitly distinguishes foundations, components and goal-oriented patterns and exposes design-system knowledge to agents through MCP.
A2UI 1.0, dated 20 November 2025 / updated 8 June 2026, is the clearest direct analogue to “components plus a page referencing IDs”: flat component records, stable IDs, parent-child references, data bindings, actions, accessibility attributes, schemas and rendering.
Formal traditions already separated task/domain, abstract UI, concrete UI and final UI, but the W3C model-based UI group closed in 2014 and its UsiXML materials are archived.
Modern evidence argues against trusting text alone: 2025–2026 studies report better controllability from structured intermediate specifications, but persistent cross-screen inconsistency, inert controls, invented content and specification-to-behavior gaps.
Recommendation

Pilot a Screen Contract:

one Markdown file per screen/surface;
YAML front matter only for stable identity and machine-checkable references;
readable sections for purpose, actor/permissions, regions, content/actions, states, responsive intent and unresolved questions;
references to a small component catalogue—not separate files for every field instance;
Mermaid paths/state diagrams outside screens, referencing screen/action IDs;
one application-wide contract for shell, routes, notifications, offline/degraded behavior and window/tab rules;
generated low-fidelity previews and component stories treated as review evidence, not canonical truth.

Do not initially create a definition file for every search field. Define a reusable SearchField only when a genuine shared semantic contract exists; screen files should create named instances of it.

The following diagram shows that proposed boundary.

Figure 1: A layered pilot architecture: human-readable Markdown remains the review surface, while stable references connect screens, components, paths, shared concerns, previews, design tools, and platform-specific builds.

Vocabulary and taxonomy
Term    Precise use hereUI description/specification    Any pre-build statement about visible structure, available actions, states or behavior.
Screen/page/surface contract    Human-reviewable description of one presentation context; “surface” avoids assuming a browser page.
Annotated wireframe    Spatial preview plus identifiers/callouts linked to explanatory text.
Component specification    Reusable control/pattern contract: purpose, anatomy, properties, variants, states, behavior, accessibility and content.
User flow    Typical/ideal interactions for a bounded goal inside a product; distinct from a cross-channel journey.
Task model    Platform-independent decomposition and temporal relationships among user/system activities; CTT is a formal example.
Journey map    High-level experience across time/channels, including thoughts and emotions—not a screen specification.
State machine    Formal states, events, guards and transitions; best for behavior with meaningful state, not page inventory.
Domain/conceptual model    Objects, attributes, relationships and actions independent of presentation.
Information architecture    Organization, labeling, navigation hierarchy and findability.
UIDL/model-based UI    Formal language intended for validation, transformation or generation; unlike ordinary descriptive Markdown.
Design tokens    Named indivisible visual decisions. DTCG 2025.10 is stable but is a Community Group report, not a W3C Recommendation.
Declarative UI    Executable code/schema describing desired UI state; SwiftUI, Compose, XAML, QML, HTML/MDX and A2UI sit on the code-like side of the boundary.
Wireflow    Screens or wireframes connected as a flow.
Executable specification    Specification connected to tests or rendering strongly enough to be automatically checked.
Research questions 1–22
1. Existing synthesis and vocabulary

No authoritative survey unifies UX mapping, screen documents, design systems, UIDLs, page schemas and AI-agent formats. Existing surveys are family-specific. Current vocabulary overlaps heavily: “spec,” “schema,” “design system,” “design language,” “UI DSL,” “wireflow” and “design-to-code” describe different abstraction levels.

Counter-search: searches for a complete textual-UI taxonomy returned partial comparisons and formal-language surveys, not an end-to-end method. Gap: terminology remains community-dependent.

2. One-screen specifications

The strongest public specimen was Japanese gamen sekkeisho: screen image, numbered mappings, labels/API names, type, I/O, lengths, required/default/format values, help, display conditions, validation, processing, actors, messages and CRUD. It is implementation-oriented and commonly spreadsheet-shaped.

European public procurement evidence was more contractual than screen-specific: 2025 Living-in.EU packages provide editable tender, technical and financial templates for user-facing applications/platforms, but not a public canonical screen-description method.

Counter: I found no reliable evidence that Japanese or European practice converged on Markdown or Git-first screen contracts.

3. Paths
Use case: actor goal, pre/postconditions, main and alternate success/failure courses.
Task model: activities, hierarchy, concurrency and allocation; independently useful before screens.
User flow: bounded in-product steps and system responses.
Journey: broader, cross-channel and emotional.
Story map: backlog organized around activities/tasks and releases.
Scenario: concrete narrative instance.
State machine: precise event/guard/state semantics.

Link paths to screens through stable screen-id, action-id and state IDs—not filenames or coordinates.

Counter: journeys and story maps are poor substitutes for interaction logic; state machines can overwhelm routine CRUD.

4. Above-screen descriptions

Object-Oriented UX’s ORCA materials describe object maps, CTA matrices, object guides, system models and navigation flows before screens; its promised comprehensive handbook was still marked “coming soon” on the opened page. Object-first work improves naming, cross-screen consistency and comprehension of relationships, but does not decide layout, prioritization or task sequencing.

Counter: object models can produce database-shaped interfaces and underrepresent episodic tasks, exceptions and system events.

5. Formal/model-based traditions
Cameleon/UsiXML: task/domain → abstract UI → concrete UI → final UI; explicitly multi-context, but public W3C material is archived.
CTT: formal task hierarchy, temporal operators and XML interchange; useful above screens.
IFML: formal 2015 OMG standard covering view containers/components, state objects, events, data bindings, actions and control flow.
XForms: separates model, intent-oriented controls and controller; device-neutral and accessibility-aware, but XForms 2.0 remains a 2012 Working Draft explicitly not complete or endorsed.
UIML/MARIA: historically important UIDLs; I did not find current public evidence of a broadly adopted contemporary workflow.
ISO 9241-110: current interaction-principles standard, confirmed in 2025; guidance framework, not artifact syntax.

Counter: W3C’s model-based UI group closed in 2014. Formal completeness did not establish mainstream product-design adoption.

6. Mature design systems

Mature systems specify purpose, anatomy, variants/properties, interaction and visual states, behavior, accessibility, content, examples and coded implementation. Patterns combine components around goals; tokens carry visual decisions. Carbon maintains Figma kits, coded components, patterns and agent-queryable guidance.

Counter: accessible individual components do not guarantee an accessible composition; Carbon explicitly places responsibility on product usage as well as components.

7. Composition from blocks

Structured-content systems, page builders, server-driven UI, Adaptive Cards and A2UI separate block definitions from placement. Adaptive Cards uses a versioned schema, typed body elements, actions and fallback text. A2UI uses a catalogue plus flat component instances connected by ID references.

Failure modes: over-generic blocks, layout escape hatches, schema migration, host differences, inaccessible combinations and logic leaking into presentation.

Counter: these are runtime/build formats, not evidence that designers should author the same schema upstream.

8. Application-wide concerns

Routes/deep links, shell/navigation, windows/tabs, unsolicited events, offline/degraded modes and role visibility should be centralized in an application contract, then referenced from screens and flows. Screen-local consequences still belong in each screen state table.

Counter: complete centralization hides local impact; complete repetition drifts. No public universal schema was found.

9. AI design/coding tooling, 2025–2026

Maker guidance increasingly supplies agents with design files, component catalogues, schemas, examples and instruction files. Figma describes Dev Mode, Code Connect and MCP—including code/design component mapping and bidirectional canvas interaction—but warns automation does not capture intent and reproduces poor file structure. Carbon exposes design-system knowledge through MCP. A2UI prescribes prompt → schema/catalogue-constrained generation → validation/correction.

Counter: marketplace claims exceed independent evidence; the opened Figma source is first-party guidance.

10. Measured AI studies

SpecifyUI (9 September 2025) reports that a hierarchical structured intermediate representation improved intent fidelity and controllability over prompt baselines; its study involved 16 professional designers. MobileForge (2026) evaluates 29 apps/309 screens/701 navigation specifications: builds succeeded, but navigation, visual fidelity and maintainability remained deficient; cross-screen consistency was a dominant bottleneck. Screenshot interpretation captured screens/page relations better than detailed test cases before human review.

Counter: these studies do not prove durable enterprise workflows; one is a research prototype, one uses a web-rendering proxy for mobile.

11. Text-to-preview

Options progress from:

Markdown + Mermaid;
ASCII/text wireframes;
generated static wireframes;
schema renderer;
Storybook/component previews;
clickable prototype;
executable declarative preview.

Compose previews can render device, locale, font-scale and theme variants interactively, but are executable code and lack network/file access.

Counter: preview beside the definition improves feedback, but making preview code canonical moves the artifact into implementation.

12. Text/code and Figma

Current practical connection is mostly design-file → inspection/context → mapped code, with emerging bidirectionality through MCP. Preserve stable IDs, component names, variant/property names, token references, data roles, action IDs and hierarchy. Do not expect coordinates to round-trip cleanly.

Counter: Figma warns inconsistent layers and missing Auto Layout produce inconsistent automated output.

13. Agent-proposed interfaces

A safe sequence is: user/goal → domain objects → tasks/paths → permissions/data → states/errors → platform/context → component vocabulary → layout alternatives → preview/evaluation. Agents must ask about unresolved policy, priority, content, destructive actions, legal consent, accessibility exceptions and cross-role handoffs.

A2UI constrains invention through schemas, catalogues, allowed parent/child relationships and validation loops.

Counter: a 2026 audit found generic compliance instructions did not reliably prevent manipulative UI behavior.

14. Declarative UI boundary

SwiftUI, Compose, QML, XAML, HTML components and MDX are readable descriptions but also executable implementation. Their previewability demonstrates the value of explicit state inputs and event outputs; Compose recommends exactly that for previewable screens. Upstream still owes purpose, policy, content intent, states, permissions and acceptance—not widget syntax.

Counter: code may become the most trustworthy visual source late in lifecycle.

15. Platform-specific needs

Use one abstract screen/task contract when goals, objects and state semantics are shared; add platform variants for navigation, input, windowing, lifecycle, permissions, density, gestures and OS conventions. Desktop needs multi-window/keyboard/density; native mobile needs lifecycle and OS integration; mobile web needs browser/responsive constraints; web needs URL/history/resizing.

Counter: aggressive abstraction creates lowest-common-denominator UX. Separate descriptions are justified when task topology differs.

16. Accessibility, content and localization

Every interactive instance should carry accessible name/description requirements, keyboard/focus intent, status/error announcement, copy key/default text, truncation/pluralization notes and locale-sensitive examples. A2UI models label, description, live-region and hidden semantics cross-platform. XForms directly associates labels/help/hints/alerts with controls.

Counter: metadata cannot prove contrast, focus order or screen-reader usability; rendered evaluation remains necessary.

17. Position between requirements and build

Consume intent, business rules, domain/service models, roles and stories. Hand off screen contracts, paths, states, content, component references, platform deltas, previews and unresolved decisions. Lean practice can keep screen + flow + preview; specialist practice adds IA, research evidence, design system and high-fidelity prototypes.

Counter: document-heavy handoff creates queues; Figma recommends earlier developer visibility rather than final-package handoff.

18. Pre-build evaluation
Text alone: requirement review, completeness checklist, some cognitive walkthrough.
Picture needed: visual hierarchy, responsive composition, heuristic evaluation.
Interactive prototype needed: timing, focus, navigation, recovery and multi-step behavior.

A 2025 study found multimodal synthetic heuristic evaluation identified many issues but struggled with conventions, component recognition and cross-screen violations.

Counter: AI evaluators are useful reviewers, not acceptance authorities.

19. Failure and abandonment

Failure drivers include stale duplicate documents, excessive formality, no preview, weak identity/mapping and implementation divergence. Alternatives are prototype-as-specification, design-file-as-source and code-as-source. Figma identifies version drift and naming mismatch as structural handoff problems.

Counter: prototypes/code underdescribe rationale, absent states and policy; text still survives where it records decisions that pixels cannot.

20. Referencing models/rules

Reference canonical object, field, permission, validation and service-error IDs. Screen documents add only presentation consequence and contextual copy. XForms shows the principle of binding controls to model nodes rather than duplicating constraints.

Counter: indirect references reduce duplication but increase navigation cost. Generated dependency views and link checking are needed; quantitative drift evidence was not found.

21. Lifecycle/change handling

Git provides diff/review/versioning; stable IDs enable reference validation, impact analysis and “where used” reports. Treat generated previews and Figma/code exports as derived unless ownership is explicitly reversed. Version shared components and record breaking semantic changes.

Counter: textual diffs do not reveal visual regressions; pair them with rendered snapshots and path tests.

22. UI test abstractions

Page Object organizes test interaction around pages; Screenplay around actor abilities/tasks. A description can generate locators/action contracts, but should reference stable semantic/test IDs—not CSS/layout. Executable examples can verify paths, states and accessibility assertions.

Counter: generated tests can merely restate the same incorrect specification. I found no reliable 2025–2026 evidence that Page Object or Screenplay alone prevents description/implementation drift.

Candidate shapes
Shape    Appearance / users    Strengths    Weaknesses    Platforms / paths / app-wide    Preview, AI and changeScreen-first    Markdown per screen; BA, UX, dev, QA    Concrete, reviewable, suits enterprise CRUD    Duplication; weak cross-screen logic    Variants per platform; paths separate; app contract central    Easy wireframe; excellent AI input; Git diff straightforward
Object-first    Object map + attributes/actions/relations    Stable vocabulary; strong cross-platform core    Can become database-shaped    Screens derived per platform; paths connect object actions    Object diagrams; good agent grounding; strong impact analysis
Component-first    Catalogue + instance references    Reuse, consistency, design-system/Figma fit    Premature abstraction; instance context lost    Platform implementations under shared semantics    Component stories; highly machine-readable; version shared contracts
Path-first    Flows/use cases/state machines    Exposes branches, recovery and sequencing    Poor spatial/content detail    Excellent shared behavior; platform-specific transitions    Clickable flow; agent-friendly if IDs are stable
Formal UIDL    XML/JSON/metamodel    Validation, transformation, generation    High learning/tooling cost; code-like    Potentially multi-platform    Renderer required; precise diffs but brittle schema evolution
Hybrid screen + path + catalogue + app contract [synthesis]    Markdown/YAML/Mermaid    Balanced readability and traceability    Requires conventions and link tooling    Abstract core plus controlled variants    Fast preview; strong AI fit; supports later Figma/test mapping

Synthesis sources: Japanese screen documents, CTT/IFML/XForms, Carbon, DTCG tokens, Figma mapping and A2UI composition—not a discovered finished method.

Verdict: “definition per element + page references”
For

The structural idea has strong direct relatives:

A2UI’s components are individual records with IDs; containers reference child IDs, catalogues define allowed components, and data/actions are separate.
Japanese screen layouts number elements and map them to item definitions.
Design systems separate component contracts from patterns/templates.
Adaptive Cards and structured page builders compose typed blocks.
Against

I found no direct published precedent for the exact claimed practice of “one Markdown definition per every screen element, with Markdown pages arranging those files” as a complete design workflow. Per-instance files create fragmentation, navigation overhead and false reuse. Layout is relational and contextual; a search field’s suggestion behavior, scope, result destination and mobile treatment often belong to the screen/path, not a universal field.

Verdict: retain the reference model, reject the granularity. Use:

catalogue entries for genuinely reusable semantic components;
named component instances inside screen files;
separate path/state definitions;
stable IDs everywhere.
Simplest pilot
---
id: screen.customer-search
route: /customers
platforms: [web, mobile-web]
actors: [customer-service-agent]
objects: [Customer]
paths: [path.find-customer]
---

# Customer search

## Purpose
Find an existing customer and open the correct customer record.

## Regions
1. `search` — primary task entry
2. `results` — matching customers
3. `actions` — permitted follow-up actions

## Components

### `customer-query`
Uses: `component.search-field`
Label: Search customers
Searches: customer name, customer number
Action: `action.search-customers`
Accessibility: visible label; result count announced
States: empty, entering, searching, no-results, results, service-error

### `customer-results`
Uses: `component.result-list`
Data: `CustomerSearchResult[]`
Selection: opens `screen.customer-detail`

## Responsive intent
- Web: search and results remain in one task surface.
- Mobile web: preserve the same task and states; layout may stack.
- Native/desktop: not yet designed.

## Open decisions
- Minimum query length?
- May inactive customers appear?
- What distinguishes customers with identical names?


Reusable component entry:

---
id: component.search-field
kind: semantic-component
---

# Search field

**Function:** accepts a query and initiates or refines retrieval.

Required properties:
- accessible label
- query value
- submit/change action
- searching, disabled and error states

Does not decide:
- searched domain
- minimum length
- suggestion policy
- result destination
- visual implementation


Pilot success criteria: humans can review it, an agent can lint references, a renderer can create a low-fidelity preview, paths can exercise states, and implementation changes can be traced back without making the Markdown executable code.

What surprised me
The strongest precedent is not Markdown but separation of concerns: task/domain, abstract interaction, concrete surface and implementation recur across old formal methods and new agent protocols.
Stable identity matters more than syntax. IDs enable composition, Figma/code mapping, impact analysis, testing and AI constraints.
Multi-screen consistency is still a major AI weakness, even when compilation succeeds.
A visual source and text source are both incomplete. Figma itself says automated specs do not capture intent.
The likely durable model is therefore multiple synchronized authorities: text for intent/behavior, design system/tokens for reusable decisions, preview/design file for visual composition, and code/tests for runtime truth.
Source list

Primary: W3C CTT submission (2012); W3C UsiXML archive; W3C MBUI closure notice; W3C XForms 2.0 Working Draft; OMG IFML 1.0; ISO 9241-110:2020; DTCG 2025.10; Carbon documentation; Adaptive Cards schema; A2UI 1.0 specification; Figma handoff guidance; Living-in.EU procurement notice; SpecifyUI paper; MobileForge paper; synthetic heuristic-evaluation paper; agentic specification-failure study; Android Compose preview documentation.

Secondary/fragmentary practice evidence: Japanese screen-design template; Nielsen Norman Group journey/flow comparison; ORCA handbook announcement.
