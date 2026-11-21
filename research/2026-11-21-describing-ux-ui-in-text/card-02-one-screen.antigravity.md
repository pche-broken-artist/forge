---
date: 2026-11-21
project: forge
topic: The description of one screen
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 2; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":110447,"output_tokens":30949,"thinking_tokens":19180,"cache_read_tokens":1383838,"total_tokens":141396}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-02-one-screen
status: immutable
---

# What an established description of a single screen or page contains

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Across practitioner guides, public-sector design systems, Japanese basic
design documents (`gamen sekkeisho` within `kihon sekkei`), open-source
human interface guidelines, and formal model-based standards, an
established description of a single screen consistently contains six
recurring groups of fields: (1) screen identity and purpose (ID, name,
type, user goal, entry and exit points), (2) spatial regions and nested
containers, (3) an itemized element inventory (ID, label, control type,
data source, format, defaults, validation rules), (4) interaction and
action specifications (trigger, preconditions, system response, error
handling, target screen), (5) a screen- and element-level state matrix
(ideal, loading, empty/blank, partial, and error states, plus interactive
element states), and (6) layout and responsive adaptation rules. Elements
are identified either by callout numbers/letters (`①`, `[A]`) linking a
visual layout to a prose or tabular legend, by hierarchical typed IDs
(`SCR-USR-001`, `IN_01`, `BTN_01`) in Japanese specification tables, or by
nested component trees (`ViewContainer` / `ViewComponent`) in formal
models. The disconfirming query confirmed strong practitioner criticism of
heavy, prose-dense standalone specification documents—which fall out of
date and duplicate visual prototypes—and showed that surviving practice
replaces free-form prose with structured tables, state checklists, and
references to shared design-system components. One unexpected finding
emerged: in both Japanese `kihon sekkei` practice and European public
procurement (`V-Modell XT`), a screen description is treated not as a
developer-only handoff redline, but as the formal consensus boundary
between non-technical stakeholders and builders, requiring domain
vocabulary rather than implementation identifiers. All findings below rest
on grounded summarising fetches of the cited sources.

## Question

#### Card 2: The description of one screen
- **Question:** What does an established description of a single screen or page contain (an annotated wireframe, a screen specification, a functional or UI specification): which fields recur (purpose, entry points, regions, elements, data, actions, states such as empty, loading and error, rules, responsive behaviour), how are elements identified and referred to, and how much is prose against structure?
- **Why it matters:** the first shape to try is a description of a few screens.
- **What would answer it:** published templates and guides of practitioners and organisations.
- **Where to look:** practitioner organisations on wireframe annotation; service manuals of public administrations; public templates of companies; the specification chapters of UX handbooks; the Japanese practice of screen design documents (gamen sekkeisho, within the basic design, kihon sekkei), read in Japanese or in translation; templates of public procurement and of systems engineering in Europe; specifications published by open-source products. Search words from card 1: "design specs", "wireframe annotations", "prototype specifications", "wireflows", "state matrix"; and the model-based words "abstract user interface", "concrete user interface", IFML's "view container", "view component", "interaction flow".
- **Disconfirming query:** "UI specification document is waste", "annotated wireframes are dead"; expected: criticism of heavy specifications and a preference for prototypes.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

To beat the baseline, this note must move past generic advice to "annotate
wireframes clearly" and establish the concrete recurring fields, element
addressing schemes, and structural-versus-prose ratios across Western UX
practice, Japanese systems engineering, public-sector service manuals, and
formal UI metamodels, while keeping the three senses of "design" distinct:
(1) the interface design held in a visual tool, (2) the technical design
between requirements and tasks in a specification chain, and (3) the visual
identity and component rules of a design system.

## Key findings

- **F1. Every established screen specification separates static layout from
  three specification layers: element attributes, interactive behaviour,
  and content/data rules** [consensus — practitioner claims and public
  templates, resting on summarised fetches]. Nielsen Norman Group (NN/g)
  divides prototype and screen specifications (sense 1: interface design
  annotations) into *Element specifications* (visual attributes, dimensions,
  alignment, and active/inactive states), *Functionality specifications*
  (interaction triggers, gestures, validation logic, and system responses),
  and *Content specifications* (copy rules, contextual tips, placeholder
  constraints, and error messages) [1]. In *The Web Project Guide* (drawing
  on Dan Brown's *Communicating Design*), screen documentation similarly
  groups annotations into *Points of attention* (visual hierarchy and
  focus), *Points of interaction* (controls, triggers, and success/failure
  feedback), and *Wayfinding* (navigation, breadcrumbs, and calls to action
  confirming location) [4]. Atlassian's Product Requirements blueprint
  embeds these alongside scope metadata, user stories, and open questions
  in a single structured table [10].

- **F2. The most complete tabular schema for a single screen comes from
  Japanese basic design (`kihon sekkei` / external design), which splits a
  screen design document (`gamen sekkeisho`) into three cross-referenced
  tables** [consensus — public engineering agency guide, resting on
  summarised fetches]. In the Information-technology Promotion Agency (IPA)
  Software Engineering Center's *Guide for Consensus Building on Functional
  Requirements* (`機能要件の合意形成ガイド`, Vol. 3 *Screen Edition*
  `画面編`), a single screen specification (sense 2: technical design
  between requirements and build) comprises: (a) a **Screen Layout**
  (`画面レイアウト`) showing spatial placement of controls alongside screen
  metadata (Screen ID, Screen Name, Screen Type such as normal page, modal,
  or popup, and purpose); (b) a **Screen Input/Output Item List**
  (`画面入出力項目一覧`), a table with columns for Item ID (`項目ID`),
  display label (`項目名`), physical/data-model field name, required/optional
  flag (`必須/任意`), control/data type, character length and format,
  initial/default value (`初期値`), and validation rules; and (c) a **Screen
  Action Specification** (`画面アクション明細`), a table listing every event
  trigger (e.g., page load, button click), preconditions, step-by-step
  processing logic, validation/error behaviour, and the destination screen
  ID in the companion screen transition diagram (`画面遷移図`) [8].

- **F3. Screen-level states are standardized around a five-state "UI Stack"
  (Ideal, Loading, Partial, Empty/Blank, Error), supplemented by
  element-level interactive states** [consensus — practitioner guides and
  open-source HIGs, resting on summarised fetches]. Practitioner guides on
  wireframe annotations warn that static wireframes default to showing only
  the "happy path" [1, 3]. Scott Hurff's "UI Stack" codifies five mandatory
  screen-level states that every screen description must specify: (1) *Ideal
  State* (fully populated, normal operation), (2) *Loading State* (skeleton
  screens, spinners, or optimistic updates while fetching data), (3)
  *Partial State* (sparse data, such as a single item or incomplete profile,
  where the layout would otherwise look broken), (4) *Blank / Empty State*
  (zero data on first launch or empty search results), and (5) *Error State*
  (network failure, server crash, or validation failure, with human-readable
  recovery actions) [3]. Open-source interface guidelines further codify the
  internal structure of non-ideal states: the GNOME Human Interface
  Guidelines specify *Placeholder Pages* (`AdwStatusPage`) with four
  explicit fields—a graphic (colorful illustration for an empty primary view
  or monochrome symbolic icon for a secondary/search view), a mandatory
  heading, an optional description, and an optional call-to-action button
  [12]. At the individual element level, NN/g and EightShapes require
  specifying default, hover, focus, active/pressed, disabled/inactive, and
  inline error/success states [1, 5].

- **F4. Entry points, exit paths, and conditional screen transitions are
  specified either as tabular transition matrices or as "wireflows" rather
  than isolated single-screen notes** [consensus — practitioner claims and
  standards, resting on summarised fetches]. NN/g defines *wireflows* as a
  hybrid specification format that replaces abstract flowchart nodes with
  screen layouts (or screen states) linked by directional arrows carrying
  trigger and branching conditions [2]. This format emerged from mobile app
  design (where compact screens fit inside flow diagrams) and is used on
  desktop and web for multi-step workflows or dynamic in-page state changes
  [2]. In Japanese `kihon sekkei` [8] and OMG's Interaction Flow Modeling
  Language (IFML 1.0) [14], each screen description explicitly cross-links
  its action triggers to incoming and outgoing transition flows, including
  back-button behaviour, modal invocations, and error-branch destinations.

- **F5. Three distinct element-identification schemes recur across practice:
  numbered visual callouts, typed tabular IDs, and nested container trees**
  [consensus — practitioner guides and formal standards, resting on
  summarised fetches].
  1. *Numbered or lettered callout markers*: In Western wireframe
     annotations (NN/g [1], Dan Brown / *The Web Project Guide* [4], and
     Nathan Curtis's *EightShapes Specs* [5]), elements on a canvas receive
     sequential badges (`①`, `②` or `[1]`, `[2]`) that index into a side
     margin or companion table; EightShapes Specs automates this as an
     *Anatomy* frame that labels nested layers and dependencies [5].
  2. *Typed hierarchical IDs*: In Japanese screen design documents [8],
     screens and elements receive stable alphanumeric identifiers (`SCR-001`
     for a screen; `IN_01`, `OUT_01`, `BTN_01` for input, output, and action
     elements) so that the layout diagram, the item-definition table, the
     action table, and the data model refer to the exact same token without
     ambiguity.
  3. *Nested structural containers and components*: In formal model-based
     standards, W3C's Model-Based User Interfaces (MBUI) framework separates
     a modality-independent *Abstract User Interface* (`AUI`, made of
     Abstract Interaction Units) from a modality-specific, toolkit-neutral
     *Concrete User Interface* (`CUI`, made of Concrete Interaction Units)
     [15, 16]; OMG's IFML 1.0 models any screen as a hierarchical
     `ViewContainer` (window, page, or sub-panel, marked as XOR/landmark/
     default) containing `ViewComponents` (such as `Form`, `List`, or
     `Details`) with typed `DataBinding`, `Parameter` passing, and
     `Event` / `InteractionFlow` connections [14].

- **F6. Public-sector service manuals and open-source HIGs define screens by
  reusable page archetypes, named spatial regions, and responsive rules,
  delegating element-level mechanics to a design system** [consensus —
  public administration manuals and open-source specifications, resting on
  summarised fetches]. The U.S. Web Design System (USWDS) [7], the UK
  Government Digital Service's GOV.UK Design System [6], and Japan's Digital
  Agency Design System [9] (all sense 3: design systems) specify screens at
  two levels: (a) a boilerplate *Page Template* dividing the viewport into
  named landmark regions (skip link, government/phase banner, header,
  navigation, main content region, footer) with responsive grid breakpoints
  [6, 7], and (b) task-oriented *Page Patterns* or *Templates* (such as
  GOV.UK's Question pages, Check answers pages, Confirmation pages, and 404
  pages [6]; or USWDS's Landing, Documentation, Authentication, Form, and
  404 templates [7]). Similarly, the KDE Human Interface Guidelines define
  screen descriptions through spatial region roles, Kirigami grid spacing
  units, and adaptive layout shifts across desktop and mobile widths [13].
  In European public procurement under Germany's *V-Modell XT* (version
  2.4), when the project tailoring flag "Is the user interface a success
  criterion?" (`Ist die Benutzerschnittstelle ein Erfolgskriterium?`) is
  enabled, screen-level ergonomic and visual rules are factored out of the
  system requirement specification (`Gesamtsystemspezifikation`) into a
  mandatory cross-screen UI `Styleguide` owned by an ergonomics lead
  (`Ergonomieverantwortlicher`) [11].

- **F7. Across surviving specification formats, structured tables, key-value
  lists, and component/token references heavily outweigh continuous prose,
  which is criticized as wasteful when it duplicates prototypes or design
  systems** [contested on standalone wireframe specs; consensus on
  structured over prose format — practitioner claims, resting on summarised
  fetches]. The disconfirming query surfaced long-standing practitioner
  criticism—exemplified by Neil Turner's "Wireframes are dead, long live
  rapid prototyping" (2010) [17]—arguing that standalone, heavily annotated
  wireframe documents take too long to write, cannot convey dynamic feel,
  are rarely read in full by developers or clients, and become obsolete as
  soon as coding starts ("Wireframes, your time is up... replaced by that
  young upstart called rapid prototyping" [17]). NN/g (2022) [1] and
  EightShapes (2023) [5] directly address this critique: they advise against
  paragraph-length prose annotations and against re-specifying standard
  design-system components (sense 3), restricting screen annotations to
  concise bulleted/tabular rules, non-standard interactions, state matrices,
  and component property/token bindings (`Props`, `Anatomy`, and `Layout`).

## Unexpected

In both Japanese `kihon sekkei` guidebooks (IPA SEC's *Guide for Consensus
Building on Functional Requirements*) [8] and German public-procurement
systems engineering (*V-Modell XT*) [11], a screen specification is framed
primarily as a **contract of agreement with non-technical domain
stakeholders** before it serves as an engineering build spec. IPA explicitly
warns against writing screen item tables and action tables in developer
jargon or physical database column names alone; it requires domain/business
vocabulary (`業務用語`) and groups related fields into named semantic blocks
so that the commissioning stakeholder can verify completeness across three
maturity stages (`仕掛レベル` work-in-progress, `充実レベル` enriched table
review, and `完成レベル` cross-checked completion) [8]. This reconfigures a
common assumption in software tooling that a textual screen spec only needs
to be readable by a developer or coding agent: in human-in-the-loop review
(like the principal's workflow), the human reviewer judges the screen
description in domain terms while the builder needs unambiguous structural
IDs and state rules.

## Not found

- **Measured empirical ratios of prose word count to tabular fields:** No
  controlled study or quantitative audit measuring the exact percentage of
  prose versus structured tables in industrial screen specifications was
  found across queries on UX handbooks, NN/g, or software engineering
  repositories. The preference for tabular/bulleted structure over prose is
  documented as a qualitative practitioner rule [1, 5, 8].
- **Single pan-European public procurement screen template:** While national
  standards such as Germany's *V-Modell XT* (`Gesamtsystemspezifikation` and
  `Styleguide`) [11] and the UK's GOV.UK Service Manual / Design System [6]
  publish explicit structure, no unified European Union procurement template
  dictating the exact fields of a single UI screen specification was found.

## Options

Because the card asks what an established screen description contains in
order to inform the first shape to try for the project, three distinct
structural options follow from the findings:

1. **Option A: Three-table `kihon sekkei` (`gamen sekkeisho`) screen
   specification** [8].
   - *Shape:* Each screen Markdown document has (1) a header block (Screen
     ID, name, archetype/type, user goal, entry/exit screen IDs), (2) a
     hierarchical Region & Element Inventory table (`Item ID`, `Label`,
     `Component/Type`, `Data/Source`, `Required`, `Default`, `Validation`),
     and (3) an Actions & Events table (`Trigger`, `Precondition`, `System
     Response`, `Error Handling`, `Next Screen/State`), plus a 5-state UI
     Stack checklist [3, 8].
   - *Trade-offs:* Highest completeness and cross-referenceability (every
     element has a stable ID like `IN_01` or `BTN_01` that user stories,
     data models, and tests can cite); heavier to author for simple screens
     and can feel rigid if every standard component attribute is repeated.

2. **Option B: Archetype + Component-reference (`AUI`/`CUI` & Design System)
   screen composition** [5, 6, 7, 14, 15].
   - *Shape:* A screen document declares its page template/archetype (e.g.,
     Question page, Form, Details, Dashboard) [6, 7], nests named regions
     (`ViewContainers`) and referenced element definitions (`ViewComponents`
     with `Props`/variants and data bindings) [5, 14], and writes explicit
     rules only for screen-specific states (empty, loading, partial, error)
     [3, 12] and custom interaction flows.
   - *Trade-offs:* Directly matches the idea heard from practice in the
     card's frame (each element has its own small definition; the page
     definition names which elements it holds and where they stand) and
     avoids the "death by documentation" criticized by the disconfirming
     evidence [1, 17]; requires a companion catalogue of reusable element
     definitions.

3. **Option C: Annotated wireflow / prose callout document** [1, 2, 4].
   - *Shape:* An ASCII/text layout or diagram with numbered markers (`[1]`,
     `[2]`) followed by numbered prose/bullet notes covering attention,
     interaction, and wayfinding [1, 4].
   - *Trade-offs:* Quickest to sketch for a single screen in isolation, but
     weakest for machine parsing, cross-document citation, and systematic
     state coverage.

## Relevance to this project

In my judgement (inference from F1–F7), the project should adopt a hybrid of
**Option B and Option A**: a structured Markdown screen document that uses
Option B's **region-and-element composition** (naming which reusable elements
stand in which spatial regions, with their screen-specific props, data
bindings, and validation rules) combined with Option A's **stable element IDs,
action/event table, and five-state UI Stack section**.

What this rests on:
- It directly operationalizes the recurring fields found across all surveyed
  traditions: Purpose & Entry/Exit points [2, 8], Named Regions (`ViewContainer`
  / landmarks) [6, 7, 13, 14], Element Inventory with stable IDs and data
  rules [1, 5, 8], Action/Interaction table [1, 8, 14], the five-state UI
  Stack (Ideal, Loading, Partial, Empty, Error) [3, 12], and Responsive
  adaptation rules [7, 13].
- By referencing element definitions rather than re-describing standard widget
  mechanics in prose, it neutralizes the primary failure mode identified by
  the disconfirming query (bloated static specifications that go stale and
  repeat what a design system or prototype already knows) [1, 5, 17].
- Using domain labels paired with stable symbolic IDs satisfies both the
  human reviewer (who checks domain completeness, as highlighted by IPA [8])
  and the downstream coding agent or developer (who binds IDs to components,
  routes, and tests).

What it is chosen against:
- Chosen against free-form prose screen descriptions or unindexed bullet
  lists (Option C), which omit partial/loading/empty states [3] and lack
  stable identifiers for cross-referencing from user stories or tests [8].
- Chosen against exhausting every visual redline (pixel padding, colors, font
  sizes) inside each screen document (sense 1/3), which belongs in the design
  system or component definitions [1, 5, 11].

**Consult when:**
- Designing the Markdown schema or template for a single screen or page
  specification.
- Deciding which sections and fields the AI agent must ask for or propose
  when a screen description is incomplete (especially the five screen states
  and action/validation rules).
- Choosing how a page definition identifies, numbers, and references the
  elements it holds.

## Sources

[1] "Use Good Prototype Specifications to Empower Team Collaboration",
Leeloo Tang and Feifei Liu (Nielsen Norman Group), 2022-06-05 (byline),
https://www.nngroup.com/articles/prototype-specifications/ ; primary
(practitioner research organisation guide); summarised fetch; original.

[2] "Wireflows: A UX Deliverable for Workflows and Apps", Page Laubheimer
(Nielsen Norman Group), 2016-12-04 (byline),
https://www.nngroup.com/articles/wireflows/ ; primary (practitioner research
organisation guide that coined/codified the term); summarised fetch;
original.

[3] "Why Your User Interface Is Awkward: You're Ignoring the UI Stack",
Scott Hurff, 2015-08-17 (byline),
https://www.scotthurff.com/posts/why-your-user-interface-is-awkward-youre-ignoring-the-ui-stack/
; primary (practitioner guide and excerpt from *Designing Products People
Love*, O'Reilly); summarised fetch; original.

[4] "Chapter 13: Develop the Graphic and Interface Design" (*The Web Project
Guide*), Corey Vilhauer and Deane Barker (Blend Interactive), 2021 (byline /
book copyright), https://webproject.guide/graphic-and-interface-design/ ;
primary (open-access UX and web project handbook chapter synthesising Dan
Brown's *Communicating Design* wireframe annotation model); summarised
fetch; original.

[5] "EightShapes Specs", Nathan Curtis (EightShapes), 2023 (structured
data / release),
https://www.figma.com/community/plugin/1205622541257680263/eightshapes-specs
; primary (practitioner specification tool and documentation schema);
summarised fetch; original.

[6] "Patterns — GOV.UK Design System", Government Digital Service (UK),
undated (living official manual),
https://design-system.service.gov.uk/patterns/ ; primary (public
administration service manual and design system); summarised fetch;
original.

[7] "Page templates — U.S. Web Design System (USWDS)", U.S. General Services
Administration (Technology Transformation Services), undated (living
official documentation), https://designsystem.digital.gov/templates/ ;
primary (public administration design system); summarised fetch; original.

[8] *Guide for Consensus Building on Functional Requirements* (`機能要件の合意形成ガイド`,
Vol. 3 *Screen Edition* `分冊3 画面編`), Information-technology Promotion
Agency, Japan — Software Engineering Center (IPA SEC / 独立行政法人情報処理推進機構),
2010-03 (byline of report series archived on IPA portal),
https://www.ipa.go.jp/archive/publish/ ; primary (national software
engineering agency guide on `kihon sekkei` / external screen design
documents); summarised fetch; original.

[9] "Digital Agency Design System (`デジタル庁デザインシステム`)", Digital Agency of
Japan (デジタル庁), undated (living official documentation),
https://www.digital.go.jp/policies/servicedesign/designsystem/ ; primary
(public administration design system and screen template standard);
summarised fetch; original.

[10] "Product Requirements Template", Atlassian, undated (living company
template),
https://www.atlassian.com/software/confluence/templates/product-requirements
; primary (public company specification template); summarised fetch;
original.

[11] "V-Modell XT", WEIT e.V. (Verein zur Weiterentwicklung des V-Modell XT
e.V. / German Federal IT Standard version 2.4), undated (living standard
portal), https://www.weit-verein.de/ ; primary (European public procurement
and systems engineering standard); summarised fetch; original.

[12] "Placeholder Pages — GNOME Human Interface Guidelines", GNOME Project,
undated (living open-source specification),
https://developer.gnome.org/hig/patterns/feedback/placeholder-pages.html ;
primary (open-source product interface guideline); summarised fetch;
original.

[13] "Layout and Navigation — KDE Human Interface Guidelines", KDE
Community, undated (living open-source specification),
https://develop.kde.org/hig/layout_and_navigation/ ; primary (open-source
product interface guideline); summarised fetch; original.

[14] "About the Interaction Flow Modeling Language Specification Version
1.0", Object Management Group (OMG), 2015-02 (structured data /
specification release date), https://www.omg.org/spec/IFML/1.0/About-IFML ;
primary (formal standard); summarised fetch; original.

[15] "Introduction to Model-Based User Interfaces", Gerrit Meixner, Gaëlle
Calvary, and Joëlle Coutaz (W3C Model-Based User Interfaces Working Group),
2014-01-07 (byline), https://www.w3.org/TR/mbui-intro/ ; primary (formal
standard / W3C Working Group Note); summarised fetch; original.

[16] "MBUI - Abstract User Interface Models", Jean Vanderdonckt, Ricardo
Tesoriero, Nesrine Mezhoudi, Vivian Motti, François Beuvens, and Jérémie
Melchior (W3C Model-Based User Interfaces Working Group), 2014-04-08
(byline), https://www.w3.org/TR/abstract-ui/ ; primary (formal standard /
W3C Working Group Note); summarised fetch; original.

[17] "Wireframes are dead, long live rapid prototyping", Neil Turner (UX for
the Masses), 2010-11-18 (byline),
https://uxforthemasses.com/wireframes-are-dead-long-live-rapid-prototyping/
; primary (practitioner essay — disconfirming query source); summarised
fetch; original.

## Opened and not used

- https://design-system.service.gov.uk/styles/page-template/ — GOV.UK Design
  System HTML/Nunjucks boilerplate page template; superseded by [6] and [7]
  for screen-level pattern structure.
- https://www.ipa.go.jp/jinzai/skill-standard/plus-it-ui/ — IPA ITSS+ skill
  standard overview page; off the specific question of single-screen
  document fields compared to [8].

## Search record

Queries run in order:
1. `wireframe annotations design specification elements states NN/g`
2. `"画面設計書" 項目 基本設計 テンプレート`
3. `IFML "view container" "view component" "interaction flow" OMG W3C MBUI "abstract user interface" "concrete user interface"`
4. `"UI specification document is waste" OR "annotated wireframes are dead"` (disconfirming query)
5. `scotthurff "ui stack" awkward user interface`
6. `developer.gnome.org/hig placeholder empty state view` (on `developer.gnome.org`)
7. `"Communicating Design" Dan Brown wireframe specification elements annotations`
8. `"wireflows" nngroup Laubheimer`
9. `GOV.UK service manual design prototype screen specification OR USWDS page templates`
10. `EightShapes "Nathan Curtis" spec annotations wireframe OR Atlassian UI specification template`
11. `European public procurement OR V-Modell XT "Maskenspezifikation" OR "Dialogspezifikation" OR "spécification d'interface" écran`
12. Targeted verification queries (`site:...`) across `nngroup.com`, `scotthurff.com`, `developer.gnome.org`, `develop.kde.org`, `w3.org`, `omg.org`, `designsystem.digital.gov`, `design-system.service.gov.uk`, `atlassian.com`, `webproject.guide`, `figma.com`, `weit-verein.de`, `ipa.go.jp`, `digital.go.jp`, and `uxforthemasses.com` to verify live URLs, dates, authors, and section contents.

Pages opened (via grounded summarising fetches; 19 openings across the
surveyed routes, 17 used and 2 not used):
1. `https://www.nngroup.com/articles/prototype-specifications/` [1]
2. `https://www.nngroup.com/articles/wireflows/` [2]
3. `https://www.scotthurff.com/posts/why-your-user-interface-is-awkward-youre-ignoring-the-ui-stack/` [3]
4. `https://webproject.guide/graphic-and-interface-design/` [4]
5. `https://www.figma.com/community/plugin/1205622541257680263/eightshapes-specs` [5]
6. `https://design-system.service.gov.uk/patterns/` [6]
7. `https://design-system.service.gov.uk/styles/page-template/` (opened and not used)
8. `https://designsystem.digital.gov/templates/` [7]
9. `https://www.ipa.go.jp/archive/publish/` (IPA SEC *Guide for Consensus Building on Functional Requirements*, Vol. 3 *Screen Edition*) [8]
10. `https://www.ipa.go.jp/jinzai/skill-standard/plus-it-ui/` (opened and not used)
11. `https://www.digital.go.jp/policies/servicedesign/designsystem/` [9]
12. `https://www.atlassian.com/software/confluence/templates/product-requirements` [10]
13. `https://www.weit-verein.de/` [11]
14. `https://developer.gnome.org/hig/patterns/feedback/placeholder-pages.html` [12]
15. `https://develop.kde.org/hig/layout_and_navigation/` [13]
16. `https://www.omg.org/spec/IFML/1.0/About-IFML` [14]
17. `https://www.w3.org/TR/mbui-intro/` [15]
18. `https://www.w3.org/TR/abstract-ui/` [16]
19. `https://uxforthemasses.com/wireframes-are-dead-long-live-rapid-prototyping/` [17]

What the disconfirming query found:
The query `"UI specification document is waste" OR "annotated wireframes are dead"`
returned practitioner critiques (notably Neil Turner on *UX for the Masses*
[17] and agile/design-system discussions) arguing that heavy, static
annotated wireframe documents take excessive time to produce, fail to
communicate interactive feel, are ignored by developers once code diverges,
and have been displaced by interactive prototypes and living design systems
(Storybook, Figma components). Rather than refuting the need for screen-level
specifications altogether, recent primary guides (NN/g [1], EightShapes [5])
show that modern specs narrow their scope to structured tables, state
matrices, and non-standard interaction logic while delegating standard
visual/component attributes to the design system.

Reason the run ended:
Both parts of the card's stop rule (`templates/research-plan.md`) were met:
every route in "Where to look" (practitioner organisations, public
administration service manuals, company templates, UX handbook chapters,
Japanese `gamen sekkeisho` / `kihon sekkei` practice, European systems
engineering / procurement standards, open-source product HIGs, and formal
MBUI/IFML standards) had a verified primary source that opens, and
differently worded queries yielded the same recurring six field groups.
