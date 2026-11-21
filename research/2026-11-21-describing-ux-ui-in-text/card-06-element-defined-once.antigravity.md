---
date: 2026-11-21
project: forge
topic: Component specifications, patterns, templates, and design tokens in design systems
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 6; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":68752,"output_tokens":23088,"thinking_tokens":13269,"cache_read_tokens":258272,"total_tokens":91840}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-06-element-defined-once
status: immutable
---

# Mature design systems define a component once across seven specification parts, compose components into task patterns and page templates, record visual decisions as tiered design tokens, and generate or bind documentation to code to prevent drift

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Mature vendor and public-administration design systems (meaning here the
visual identity and reusable component library of a system, distinct from
an interface mockup in a design tool or a technical design document
between requirements and tasks) converge on a seven-part specification for
a single component: anatomy, variants, properties/API, states, behaviour,
accessibility, and rules of content [1, 3, 6, 8, 12, 13]. Above the single
component, practice departs from Brad Frost's five-level Atomic Design
hierarchy (atoms, molecules, organisms, templates, pages) [9] in favour of
a three-tier operational structure: reusable Components, task-oriented
Patterns (or Compositions), and structural Page Templates [2, 4, 5, 6, 8].
Visual decisions are separated from component structure as three-tier
design tokens (primitive, semantic, and component-specific) exchanged via
the W3C Design Tokens Community Group (DTCG) JSON Format Module (`$value`,
`$type`, aliases, and composite types, stabilised in October 2025) [7, 10].
The disconfirming queries confirm that standalone specifications routinely
drift from both design-tool libraries and production code; maintainers
counter this by extracting API tables and live examples directly from source
code via Storybook Autodocs and the Custom Elements Manifest [13, 14] and
by binding design-tool nodes directly to code via Figma Code Connect [15].
Unexpectedly, the W3C UI Specification Schema Community Group (`uispec`),
chartered to standardise an implementation-agnostic JSON Schema for UI
component specifications across platforms, closed on 2026-05-21 without
publishing a final specification [11].

## Question

#### Card 6: An element defined once
- **Question:** How do mature design systems describe one component so that it is defined once and used on many screens (the parts of a component specification: anatomy, variants, properties, states, behaviour, accessibility, rules of content), how are patterns and page templates built from components, how are visual decisions recorded as design tokens, and what do the maintainers say about keeping the description and the implementation the same?
- **Why it matters:** it tests the first half of the idea of small definitions: an element with a definition of its own that carries its function.
- **What would answer it:** the design systems' own documentation and their maintainers' writing.
- **Where to look:** the public design systems of large vendors and of public administrations; writing on component specifications; atomic design; the design tokens format of the W3C community group; documentation tools that render components in isolation. Search words from card 1: "design tokens format module", "component specification", "anatomy, states, variants"; the W3C's UI Specification Schema Community Group of 2025 and 2026 and Open UI. Primary artefacts in public repositories (schemas, component and page files, agents' rules and prompt files, the schemas of servers for design tools, issue trackers) before commentary about them.
- **Disconfirming query:** "design system documentation drift", "component specification out of date"; expected: drift is a known trouble and documentation is generated from code.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

**Baseline to beat:** A generic list of component documentation headings
or a textbook restatement of Atomic Design without testing how live vendor
and government design systems structure component specifications, how they
separate patterns from page templates, how the W3C DTCG 2025.10 token
schema encodes visual decisions, what became of the W3C UI Specification
Schema Community Group in 2026, and what mechanisms maintainers use in
repositories to prevent documentation drift.

## Key findings

- **F1. Mature design systems specify a single component across seven
  recurring parts—anatomy, variants, properties/API, states, interactive
  behaviour, accessibility, and content/usage rules—separating human prose
  guidelines from machine-readable API contracts.** [consensus — primary
  design system documentation and standard schemas; rests on summarised
  fetches of [1, 3, 6, 8, 12, 13]]
  Across IBM Carbon Design System [1], the GOV.UK Design System [3], the
  U.S. Web Design System (USWDS) [6], Shopify Polaris [8], and the W3C
  Open UI Community Group [12], a component definition is divided into:
  1. *Anatomy:* A structural breakdown of named internal sub-parts and
     slots. For example, Carbon's `Text input` anatomy defines the label,
     field container, input value, optional/required indicator, helper
     text, and character counter [1]. Open UI normalises anatomy part names
     across design systems so each part maps to a DOM element, Shadow DOM
     `<slot>`, or CSS pseudo-element such as `::picker(select)` [12].
  2. *Variants:* Stylistic or structural axes of the same base component,
     such as Carbon's `Default` versus `Fluid` styles and `xs`, `sm`, `md`,
     and `lg` sizes [1], or button hierarchy variants (`Primary`,
     `Secondary`, `Tertiary`, `Danger`, `Ghost`) [1].
  3. *Properties and programmatic API:* In the Web Components Custom
     Elements Manifest (`custom-elements.json`, schema version `2.1.0`), a
     component declaration formally records `tagName`, `attributes`,
     `properties`, `events`, `slots`, `cssProperties`, and `cssParts` [13].
     Shopify Polaris exposes camelCase properties and kebab-case slots
     (such as `slot="primary-action"`) on encapsulated web components
     (`s-button`, `s-badge`) while forbidding external CSS selectors from
     targeting internal DOM nodes [8].
  4. *States:* Interactive and system conditions. Carbon specifies eight
     states for `Text input`: `Enabled`, `Active`, `Focus`, `Error`,
     `Warning`, `Disabled`, `Skeleton` (loading), and `Read-only` [1].
  5. *Behaviour and usage:* When to use and when not to use the component
     (for example, Carbon and GOV.UK forbid free-form text inputs when
     users must pick from a known list, directing authors to radios or
     selects) [1, 3], plus validation, sizing, and layout alignment rules.
  6. *Accessibility:* Mandatory visible labels, programmatic associations
     (`aria-describedby` for helper and error text, `aria-required`),
     contrast requirements, and explicit keyboard bindings (`Tab` for
     focus, `Enter`/`Space` for activation, `Esc` to dismiss) [1, 3, 6].
  7. *Rules of content:* Voice, tone, label phrasing, helper text, and
     error message copywriting rules embedded directly in the component
     specification [1, 3, 8].

- **F2. Operational design systems compress Brad Frost's five-level Atomic
  Design taxonomy into three compositional tiers: Components, task-oriented
  Patterns (or Compositions), and structural Page Templates.** [consensus —
  practitioner methodology and primary design system documentation; rests
  on summarised fetches of [2, 4, 5, 6, 8, 9]]
  Brad Frost's *Atomic Design* defines five hierarchical levels: *Atoms*
  (foundational HTML tags such as `<label>`, `<input>`, `<button>`),
  *Molecules* (small functional groups such as a search form combining a
  label, input, and button), *Organisms* (standalone interface sections
  such as a site header), *Templates* (content-agnostic page wireframes and
  layout grids), and *Pages* (concrete instances populated with real
  content to test layout resilience) [9]. Contradicting the strict
  separation of atoms, molecules, and organisms in Frost's model [9],
  IBM Carbon [2], GOV.UK [4, 5], USWDS [6], and Shopify Polaris [8] do not
  expose separate catalogue tiers for atoms, molecules, and organisms.
  Instead, they group all reusable interactive widgets—from a single button
  to a modal or data table—under **Components** [1, 3, 6, 8], and build
  upward in two distinct ways:
  1. *Patterns (or Compositions):* Repeatable combinations of components
     and choreography rules organized around a user goal or workflow rather
     than a visual widget. Carbon documents patterns for forms, filtering,
     login, empty states, and search [2]; GOV.UK organises patterns into
     "Ask users for…" (names, addresses, dates, bank details) and "Help
     users to…" (check answers, recover from validation errors, exit a page
     quickly) [4]; USWDS defines patterns for multi-step user tasks such as
     creating a profile, completing a complex form, or selecting a language
     [6]; Shopify Polaris defines Compositions for empty states and setup
     guides [8].
  2. *Page Templates:* Structural blueprints that fix page-level regions
     (skip links, header, phase banner, main content grid, footer) and
     demonstrate whole-screen layouts such as GOV.UK's standard page
     template [5], USWDS's landing, documentation, form, sign-in, and 404
     page templates [6], and Shopify Polaris's homepage, index, detail, and
     settings templates [8].

- **F3. Visual decisions are decoupled from component specifications through
  a three-tier token hierarchy and exchanged in the W3C Design Tokens
  Community Group (DTCG) JSON format (`2025.10`).** [consensus — W3C
  Community Group report and primary design system documentation; rests on
  summarised fetches of [1, 7, 8, 10]]
  As of October 2025 (`2025.10` stable release), the W3C DTCG Design Tokens
  Format Module defines a vendor-neutral JSON structure where reserved
  properties use a `$` prefix to prevent collisions with user token names
  [10]. An object is a token if and only if it carries a mandatory `$value`
  property alongside an explicit, group-inherited, or alias-resolved
  `$type` (plus optional `$description` and vendor `$extensions`) [10]. The
  specification supports hierarchical token groups, curly-brace references
  / aliases (`{group.token}`), primitive types (`color`, `dimension`,
  `fontFamily`, `fontWeight`, `duration`, `cubicBezier`, `number`), and
  multi-property composite types (`typography` bundling `fontFamily`,
  `fontSize`, `fontWeight`, `letterSpacing`, and `lineHeight`; `shadow`
  bundling `color`, `offsetX`, `offsetY`, `blur`, `spread`, and optional
  `inset`; `border` bundling `color`, `width`, and `style`; `strokeStyle`;
  `transition`; and `gradient`) [10]. In production systems (Carbon [1],
  USWDS [7], and Shopify Polaris [8]), tokens are organized into three
  semantic layers so components never hard-code raw visual values:
  1. *Primitive / global tokens* holding raw palette and grid steps;
  2. *Semantic / contextual tokens* expressing UI intent across themes or
     page layers (such as Carbon's `$field` and `$border-strong` or
     Polaris's `--p-color-bg-surface` and `--p-color-text-critical`) [1, 8];
  3. *Component tokens* bound to specific anatomy parts of an element [1, 8].

- **F4. Standalone component specifications suffer from documentation drift;
  maintainers prevent drift by making source code the single source of
  truth for component APIs and binding design-tool assets to code.**
  [consensus — primary tool documentation and repository artefacts; rests
  on summarised fetches of [13, 14, 15]]
  The disconfirming queries (`"design system documentation drift"` and
  `"component specification out of date"`) confirm that manually maintained
  documentation diverges from both design files (the interface design held
  in a design tool) and production code when properties, states, or tokens
  change under delivery pressure. Maintainers address this split through two
  architectural mechanisms:
  1. *Code-extracted documentation and isolated story rendering:* In
     Storybook, maintainers co-locate Component Story Format (`*.stories.ts`)
     files with component code and opt into automatic documentation via
     `tags: ['autodocs']` [14]. Storybook's `docgen` compilers parse
     TypeScript interfaces, PropTypes, and JSDoc annotations (`@default`,
     `@deprecated`) directly from source files to render live interactive
     canvases (`<Canvas>`) and property tables (`<Controls>`), while
     companion `.mdx` files hold narrative usage guidelines next to the
     code [14]. For Web Components, tools generate `custom-elements.json`
     manifests directly from source classes and JSDoc tags (`@slot`,
     `@csspart`, `@cssprop`, `@fires`) [13].
  2. *Declarative bindings between design tools and code:* Figma's Code
     Connect (`@figma/code-connect`) keeps declarative `.figma.ts` mapping
     files inside the code repository (`figma.connect(...)`) that map Figma
     component variants and properties (`figma.enum`, `figma.string`) to
     actual production component imports and JSX/HTML templates [15].
     These mappings feed both Figma Dev Mode and the Figma Model Context
     Protocol (MCP) server so developers and AI coding agents receive exact
     repository component signatures rather than guessed markup or stale
     prose specifications [15].

- **F5. Cross-platform UI specification standardisation remains split:
  Open UI succeeds by standardising component anatomy and native web
  primitives, whereas the W3C UI Specification Schema Community Group
  (`uispec`) closed on 2026-05-21 without publishing a schema.** [single
  source / W3C record — standard body records; rests on summarised fetches
  of [11, 12]]
  The W3C UI Specification Schema Community Group (`uispec`) was chartered
  to create an implementation-agnostic JSON/JSON Schema meta-model
  describing UI component design, layout, behaviour, and constraints across
  web, mobile, desktop, and embedded platforms, aligned with Open UI and
  the DTCG [11]. According to W3C records as of 2026-05-21, the `uispec`
  group closed on May 21, 2026 without publishing a final specification or
  W3C Community Group Report [11]. Conversely, the W3C Open UI Community
  Group continues to publish component anatomy audits and explainers by
  targeting browser standards directly [12].

## Unexpected

- **Closure of the W3C UI Specification Schema Community Group (`uispec`).**
  The card points to the W3C UI Specification Schema Community Group of
  2025 and 2026 as a primary venue for formalising component specifications.
  W3C's community group directory reports that `uispec` closed on May 21,
  2026 without completing or publishing a formal JSON Schema specification
  [11]. Any text-based UI specification framework designed today cannot rely
  on an existing W3C `uispec` standard and must instead compose existing
  adjacent schemas (such as W3C DTCG for tokens [10] and Custom Elements
  Manifest [13] or Storybook CSF [14] for component APIs).

- **Pivot from custom element tags to native HTML progressive enhancement
  and encapsulated Web Components.** Earlier Open UI work proposed new
  standalone HTML elements for complex controls (iterating from
  `<selectmenu>` to `<selectlist>` at `selectlist.explainer`, which no
  longer opens). Open UI and browser vendors abandoned a separate tag in
  favour of upgrading the existing HTML `<select>` element via CSS
  `appearance: base-select`, the `::picker(select)` pseudo-element, and the
  `<selectedcontent>` element [12]. In parallel, Shopify Polaris migrated
  its active component specifications from React-specific components on
  `polaris.shopify.com` to Shadow DOM-encapsulated standard Web Components
  (`s-button`, `s-badge`) documented at `shopify.dev/docs/api/polaris` [8].

## Not found

- **Published JSON Schema from the W3C UI Specification Schema Community
  Group (`uispec`):** Looked on `w3.org/community/uispec/` [11] and GitHub
  (`"ui-schema"`, `"ui-specification-schema"`, `"uispec"`). The group closed
  on 2026-05-21 with no published final report or schema artefact.
- **Empirical measurements of specification drift rates:** Looked via the
  disconfirming queries `"design system documentation drift"` and
  `"component specification out of date"`. While practitioner guides and
  tool documentation [14, 15] universally cite asynchronous code changes
  and manual maintenance as the cause of drift, no controlled study or
  quantitative audit measuring the percentage of out-of-date component
  specifications across organisations was found.

## Options

For `forge`—where an AI agent and a human co-author versioned Markdown
documents in git that describe an application's UX/UI before handing them
to a build stage—the findings present three distinct ways to structure the
definition of reusable UI elements:

1. **Option 1: Seven-part Markdown component cards + three-tier composition
   (Components, Task Patterns, Page Templates) + W3C DTCG token JSON.**
   Each reusable element is defined once in a small Markdown file carrying
   the seven parts proven in mature design systems (anatomy/slots,
   variants, properties, states, behaviour/when-to-use, accessibility, and
   content rules) [1, 3, 6, 8], while visual tokens live in a separate W3C
   DTCG `2025.10` JSON file (`$value`, `$type`, semantic aliases) [10].
   Screens and journeys reference components either directly in Page
   Templates (layout regions) or via task-oriented Patterns [2, 4, 5, 6].
   - *Trade-offs:* Matches how human UX/UI specialists and public design
     systems actually write specifications; keeps visual styling tokens out
     of structural Markdown; avoids the artificial "molecule vs. organism"
     boundary debates of strict Atomic Design [9]. However, after the first
     build, a purely narrative Markdown file will drift from code unless
     paired with a synchronisation step [14, 15].

2. **Option 2: Strict five-level Atomic Design hierarchy in Markdown (Atoms,
   Molecules, Organisms, Templates, Pages).**
   Every element is classified into one of Brad Frost's five levels [9],
   with separate directories or specification templates for atoms,
   molecules, and organisms.
   - *Trade-offs:* Provides a well-known mental model for bottom-up UI
     assembly [9], but forces authors and agents to make arbitrary
     classification choices between molecules and organisms—a distinction
     that mature systems (Carbon, GOV.UK, USWDS, Polaris) have dropped in
     favour of flat Components plus workflow Patterns [2, 4, 6, 8].

3. **Option 3: Hybrid Markdown + contract-bound specification (pairing
   human prose with code-extracted / schema-validated API blocks).**
   Before the first build, the Markdown component definition specifies both
   human intent (purpose, when to use, content rules, accessibility, state
   behaviour) and a structured API block (anatomy slots, properties, events,
   and semantic token bindings modelled on `custom-elements.json` [13] and
   Storybook CSF [14]). Once built, the structured API table is generated
   or validated from code (as in Storybook Autodocs [14] and Figma Code
   Connect [15]), while the Markdown file remains the owner of narrative UX
   intent, usage rules, and content constraints.
   - *Trade-offs:* Directly solves the documentation drift found by the
     disconfirming query [14, 15]; gives AI coding agents deterministic
     property, slot, and token names during build cycles; requires a lightweight
     schema convention for the structured block in Markdown.

## Relevance to this project

**Recommendation:** Adopt **Option 3** (structured along the three-tier
component/pattern/template architecture of **Option 1**), and reject
**Option 2** (strict five-level Atomic Design) as well as purely prose
component descriptions that duplicate visual token values inline.

Specifically (marking the following synthesis as the agent's inference from
the evidence):
1. **Confirm the "defined once" hypothesis with seven mandatory sections:**
   A single UI element definition in `forge` should carry: (a) Purpose &
   When to use / not use, (b) Anatomy (named sub-parts and content slots),
   (c) Variants, (d) Properties & Events, (e) States (including loading,
   empty, error, read-only, and disabled), (f) Behaviour & Accessibility
   (keyboard map, focus order, ARIA roles/descriptions), and (g) Rules of
   content (labels, helper text, error copy) [1, 3, 6, 8, 12, 13].
2. **Use three compositional tiers, not five:** Above individual
   **Components**, `forge` should define **Patterns** (multi-component
   task choreography such as error recovery, filtering, or asking for an
   address, as in GOV.UK [4], Carbon [2], and USWDS [6]) and **Page
   Templates** (structural screen regions and layout grids [5, 6, 8, 9]),
   rather than splitting components into atoms, molecules, and organisms.
3. **Separate visual identity into W3C DTCG tokens:** Component Markdown
   files should reference semantic or component token names (for example,
   `$field` or `--color-bg-surface`), while actual visual values (`color`,
   `dimension`, composite `typography`, `shadow`, `border`) live in a W3C
   DTCG `2025.10` token file [7, 8, 10].
4. **Prevent post-build drift by splitting ownership between prose and
   code:** When `forge` runs on a second cycle after initial implementation,
   the component's API surface (props, slots, events) should be verified
   against or extracted from the implementation (following the Storybook
   Autodocs [14], Custom Elements Manifest [13], and Code Connect [15]
   pattern), while the Markdown specification remains the source of truth
   for UX rationale, usage boundaries, and content rules.

**Consult when:**
- Designing the template or schema for a single component specification in
  `forge`.
- Deciding how individual component definitions compose into multi-component
  workflow patterns and screen/page definitions.
- Choosing how visual styling and theme tokens are recorded and referenced
  from text specifications.
- Designing the round-trip workflow that keeps `forge` Markdown UX/UI
  descriptions synchronized with implemented code across subsequent change
  cycles.

## Sources

1. **Text input — Usage (with Style, Code, and Accessibility tabs)**, IBM
   Carbon Design System, undated (living documentation; copyright 2026),
   `https://carbondesignsystem.com/components/text-input/usage/`; primary
   (vendor design system documentation); summarised fetch; original.
2. **Patterns — Overview**, IBM Carbon Design System, undated (living
   documentation; copyright 2026),
   `https://carbondesignsystem.com/patterns/overview/`; primary (vendor
   design system documentation); summarised fetch; original.
3. **Text input**, GOV.UK Design System (Government Digital Service),
   undated (living documentation),
   `https://design-system.service.gov.uk/components/text-input/`; primary
   (public administration design system documentation); summarised fetch;
   original.
4. **Patterns**, GOV.UK Design System (Government Digital Service), undated
   (living documentation),
   `https://design-system.service.gov.uk/patterns/`; primary (public
   administration design system documentation); summarised fetch; original.
5. **Page template**, GOV.UK Design System (Government Digital Service),
   undated (living documentation),
   `https://design-system.service.gov.uk/styles/page-template/`; primary
   (public administration design system documentation); summarised fetch;
   original.
6. **Components (with Patterns and Templates architecture)**, U.S. Web
   Design System (USWDS / U.S. General Services Administration), undated
   (living documentation),
   `https://designsystem.digital.gov/components/`; primary (public
   administration design system documentation); summarised fetch; original.
7. **Design tokens**, U.S. Web Design System (USWDS / U.S. General Services
   Administration), undated (living documentation),
   `https://designsystem.digital.gov/design-tokens/`; primary (public
   administration design system documentation); summarised fetch; original.
8. **Polaris Web Components**, Shopify, undated (living developer
   documentation), `https://shopify.dev/docs/api/polaris`; primary (vendor
   design system documentation); summarised fetch; original.
9. **Atomic Design, Chapter 2: Atomic Design Methodology**, Brad Frost,
   2016 (byline / book publication date),
   `https://atomicdesign.bradfrost.com/chapter-2/`; primary (foundational
   methodology text by its author); summarised fetch; original.
10. **Design Tokens Format Module (Version 2025.10)**, W3C Design Tokens
    Community Group (editors: Louis Chenais, Kathleen McMahon, Drew Powers,
    Matthew Ström-Awn, Donna Vitan), 2025-10 (byline / W3C Final Community
    Group Report date), `https://tr.designtokens.org/format/`; primary
    (community group specification); summarised fetch; original.
11. **UI Specification Schema Community Group**, World Wide Web Consortium
    (W3C), 2026-05-21 (structured data / closure date on group record),
    `https://www.w3.org/community/uispec/`; primary (standards body group
    record); summarised fetch; original.
12. **Home | Open UI (Component Research and Customizable Select / Switch
    Proposals)**, W3C Open UI Community Group, undated (living community
    group portal), `https://open-ui.org/`; primary (standards community
    group documentation); summarised fetch; original.
13. **webcomponents/custom-elements-manifest (Custom Elements Manifest JSON
    Schema `2.1.0`)**, Web Components Community Group, undated (living GitHub
    repository), `https://github.com/webcomponents/custom-elements-manifest`;
    primary (public repository artefact and schema); summarised fetch;
    original.
14. **Automatic documentation (Autodocs)**, Storybook (`storybook.js.org`),
    undated (living tool documentation),
    `https://storybook.js.org/docs/writing-docs/autodocs`; primary (tool
    maintainer documentation); summarised fetch; original.
15. **figma/code-connect (`@figma/code-connect` CLI and MCP integration)**,
    Figma, undated (living GitHub repository),
    `https://github.com/figma/code-connect`; primary (public repository
    artefact and maintainer documentation); summarised fetch; original.

## Opened and not used

- `https://github.com/design-tokens/community-group` — W3C Design Tokens
  Community Group repository README; superseded by [10] which is the
  published Format Module specification itself.

## Search record

**Queries run (in order):**
1. `"component specification" anatomy states variants design system`
2. `"design tokens format module" W3C`
3. `"UI Specification Schema Community Group" W3C`
4. `Open UI component specification anatomy`
5. `atomic design Brad Frost organisms templates pages`
6. `"design system documentation drift"` (disconfirming query 1)
7. `"component specification out of date"` (disconfirming query 2)
8. `"anatomy, states, variants" OR "anatomy" "variants" "states" "accessibility" Carbon Design System OR Material Design OR Polaris component`
9. `GOV.UK Design System OR USWDS components patterns page templates`
10. `Storybook autodocs single source of truth component documentation code`
11. `Figma "Code Connect" design system documentation drift implementation`
12. `github "ui-schema" OR "ui-specification-schema" W3C community group`
13. `w3.org "UI Specification Schema Community Group" uispec exact URL dates mission github`
14. `open-ui.org exact URLs anatomy component specification selectlist select switch radio-button`
15. `designtokens.org "Design Tokens Format Module" tr.designtokens.org exact URL date editors "$value" "$type"`
16. `carbondesignsystem.com components text-input OR button usage style code accessibility anatomy variants states exact URLs`
17. `design-system.service.gov.uk components patterns page-template text-input exact URLs`
18. `designsystem.digital.gov components patterns templates design-tokens exact URLs`
19. `atomicdesign.bradfrost.com chapter-2 atoms molecules organisms templates pages exact URL`
20. `storybook.js.org/docs/writing-docs/autodocs exact URL tags autodocs docgen MDX`
21. `site:open-ui.org exact page title and URL for select research and radio-button research and homepage`
22. `site:w3.org/community/uispec exact page title text dates reports repositories chairs`
23. `site:github.com/figma/code-connect exact title README description Code Connect CLI MCP`
24. `site:github.com/webcomponents/custom-elements-manifest exact title README schema slots cssParts cssProperties attributes events`
25. `site:carbondesignsystem.com/components/text-input/usage AND /accessibility AND /code AND /style exact headings content rules tokens`
26. `site:polaris.shopify.com components patterns tokens content guidelines exact URLs and titles`
27. `designtokens.org "Design Tokens Format Module" exact URL "tr.designtokens.org/format" OR "www.designtokens.org/tr" lowercase uppercase`
28. `open-ui.org "selectlist.explainer" moved redirect OR current URL on open-ui.org "customizable-select" OR "selectmenu"`
29. `site:carbondesignsystem.com/patterns/overview/ exact URL title headings patterns vs components`
30. `site:shopify.dev/docs/api/polaris exact URL title components patterns web components properties content rules`
31. `designtokens.org "https://tr.designtokens.org/format/" OR "https://www.designtokens.org/tr/drafts/format/" exact URL composite types typography shadow border`
32. `site:github.com/design-tokens/community-group README exact links tr.designtokens.org/format`

**Pages opened (16 total openings via domain-targeted summarised fetches; 15 cited in Sources, 1 in Opened and not used):**
1. `https://www.w3.org/community/uispec/` [11]
2. `https://open-ui.org/` [12]
3. `https://tr.designtokens.org/format/` [10]
4. `https://carbondesignsystem.com/components/text-input/usage/` [1]
5. `https://design-system.service.gov.uk/components/text-input/` [3]
6. `https://design-system.service.gov.uk/patterns/` [4]
7. `https://design-system.service.gov.uk/styles/page-template/` [5]
8. `https://designsystem.digital.gov/components/` [6]
9. `https://designsystem.digital.gov/design-tokens/` [7]
10. `https://atomicdesign.bradfrost.com/chapter-2/` [9]
11. `https://storybook.js.org/docs/writing-docs/autodocs` [14]
12. `https://github.com/figma/code-connect` [15]
13. `https://github.com/webcomponents/custom-elements-manifest` [13]
14. `https://carbondesignsystem.com/patterns/overview/` [2]
15. `https://shopify.dev/docs/api/polaris` [8]
16. `https://github.com/design-tokens/community-group` (opened and not used; superseded by [10])

**What the disconfirming queries found:**
- `"design system documentation drift"` found widespread practitioner and
  tool-vendor consensus that standalone documentation drifts from code and
  Figma libraries because updates happen asynchronously under delivery
  pressure and squads create local "shadow variants". It surfaced the two
  primary remedies documented in [13, 14, 15]: automatic API/prop extraction
  from code (Storybook Autodocs, Custom Elements Manifest) and declarative
  component-to-code mapping (Figma Code Connect + MCP).
- `"component specification out of date"` returned mostly general API/schema
  (OpenAPI/Swagger) and hardware datasheet version mismatches, confirming
  that in UI engineering the phenomenon is tracked under "documentation
  drift" or "design-code drift" rather than "component specification out of
  date".

**Reason the run ended:** Both parts of the card's stop rule were met:
every route in "Where to look" (vendor and public-administration design
systems, component specifications, Atomic Design, W3C DTCG format module,
W3C UI Specification Schema CG, Open UI, isolated documentation tools, and
primary repository artefacts) had a primary source opened, differently
worded queries returned no new structural concepts, and the opening budget
reached fifteen cited primary pages.
