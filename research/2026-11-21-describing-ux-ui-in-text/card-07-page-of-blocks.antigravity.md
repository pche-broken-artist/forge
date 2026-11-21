---
date: 2026-11-21
project: forge
topic: A page as a composition of defined blocks
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 7; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":139657,"output_tokens":20803,"thinking_tokens":9758,"cache_read_tokens":321309,"total_tokens":160460}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-07-page-of-blocks
status: immutable
---

# Systems that hold a page as data referencing separately defined blocks, their division of block definition from placement, and Markdown component-to-page practices

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Across all six surveyed families—block editors, section-based theme
templates, structured-content page builders, server-driven UI (SDUI),
declarative card and agent-to-interface formats, and low-code page
schemas—systems converge on a two-layer contract: a reusable block
definition declares a type identifier, an input property schema, and
allowed child slots, while a page document holds an ordered list (or
keyed map plus order array, or flat adjacency list) of block instances
carrying an instance ID, a type reference, parameter values, and slot or
coordinate bindings. Rearrangement is performed either by mutating array
order or an explicit `"order"` array in page data, or by updating a
separate coordinate map. The disconfirming queries confirmed the
expected versioning and expressiveness limits—breaking a block contract
crashes older clients unless types are versioned (`chaos.button.v2`),
and block schemas struggle with custom cross-block animations, offline
state, and Git merge conflicts—while uncovering one unexpected shift:
low-code and agent-UI systems are abandoning monolithic nested JSON page
trees in favour of split files (markup vs. `.positions.json` coordinates
in Retool Toolscript) or streaming flat component lists (Google A2UI).
No established industry standard or audited multi-team practice was
found that pairs one Markdown file per UI element with Markdown page
files that compose them by reference; public repositories standardize
either single-file visual-identity specifications (`DESIGN.md`, covering
the visual identity of a design system) or per-component API reference
files (`docs/Button.md` indexed by `llms.txt`) without declarative
Markdown page-composition manifests.

## Question

#### Card 7: A page as a composition of defined blocks
- **Question:** Which systems hold a page as data that lists references to separately defined blocks with their placement and settings (block editors with their patterns and templates, theme templates made of sections, page builders on structured content, server-driven UI, declarative card formats and formats by which an agent sends an interface, page schemas of low-code tools), how does each divide what a block is and does from where it stands on a page, how is a page rearranged, and which troubles do they report; and does any team publish a practice of one Markdown file per interface element with page files that refer to them?
- **Why it matters:** these are the direct relatives of the idea of small definitions.
- **What would answer it:** vendors' documentation of their own formats, and engineering write-ups by teams that built such systems.
- **Where to look:** the documentation of block editors, of section-based theme templates and of structured-content page builders; engineering write-ups on server-driven UI; the specifications of declarative card and agent-to-interface formats; public repositories and write-ups for component specifications kept in Markdown for AI agents. Search words from card 1: "generative UI" for formats in which an agent emits an interface at run time, kept apart from a description handed to a build; "intermediate representation", "structured specification". Primary artefacts in public repositories (schemas, component and page files, agents' rules and prompt files, the schemas of servers for design tools, issue trackers) before commentary about them.
- **Disconfirming query:** "server-driven UI problems", "page builder blocks limitations"; expected: complaints about versioning and about what blocks cannot express.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

**Baseline to beat:** A generic observation that modern web tools use
reusable components and JSON schemas. To beat that baseline, this note
must name the exact data structures each family uses to separate a
block's definition (its contract and behaviour) from its page-level
instance (its placement, settings, and nesting), show how rearrangement
is serialized in data, document the concrete engineering failure modes
reported by teams running these architectures, and test whether the
proposed pattern of one Markdown file per UI element referenced by a
page Markdown file exists in published practice. Throughout this note,
"design" is disambiguated into its three senses: (1) *interface design*
held in a visual design tool, (2) *technical design* between
requirements and implementation tasks in spec-driven development kits,
and (3) the *visual identity of a design system* (tokens, typography,
colour, and component styling rules).

## Key findings

All findings below rest on primary vendor documentation, engineering
write-ups, and an arXiv dataset paper accessed via grounded summarising
fetches (`search_web`) with verbatim excerpt extraction, as noted per
source in `## Sources`.

- **F1. Every surveyed block-composition family separates a static block
  type contract (schema, inputs, allowed children, renderer binding)
  from a page-level instance payload (instance ID, type reference,
  configured attributes, and structural position).** `[consensus —
  vendor reports and standards across 6 system families]`
  - *Block editors (WordPress Gutenberg):* A block's definition lives in
    a directory containing `block.json` (`"Starting with the WordPress
    5.8 release, we recommend using the block.json metadata file as the
    canonical way to register block types with both PHP (server-side)
    and JavaScript (client-side)"` [1, opening paragraph]), which
    declares `"name"`, `"attributes"`, `"supports"`, `"parent"`,
    `"ancestor"`, `"allowedBlocks"`, `"providesContext"`, and
    `"usesContext"` [1]. A block template or page stores a serialized
    list of block items (`"A block template is defined as a list of
    block items. Such blocks can have predefined attributes, placeholder
    content, and be static or dynamic"` [2, opening paragraph]) encoded
    as HTML comments (`<!-- wp:namespace/block-name {"attr":"value"} -->`)
    whose nesting and sequence define page placement [2].
  - *Section-based theme templates (Shopify Online Store 2.0):* A
    section definition lives in `sections/<name>.liquid`, combining
    Liquid markup with an embedded `{% schema %}` JSON block that
    declares section `"settings"`, allowed child `"blocks"`, and
    `"presets"` (`"Sections are Liquid files that allow you to create
    reusable modules of content that can be customized by merchants.
    They can also include blocks which allow merchants to add, remove,
    and reorder content within a section"` [4, opening paragraph]). A
    page template (`templates/*.json`) holds no markup; it stores a
    `"sections"` dictionary mapping unique instance IDs to `"type"`
    (the section filename), instance `"settings"`, child `"blocks"`,
    and `"block_order"`, alongside a top-level `"order"` array (`"JSON
    templates are data files that store a list of sections to be
    rendered, and their associated settings"` [3, opening paragraph]).
  - *Structured-content page builders (Storyblok, Prismic, Sanity):*
    Storyblok classifies schemas into standalone *Content Type Blocks*
    (such as a page), *Nestable Blocks* (`"In Storyblok, a block is a
    piece of content"` [5, opening paragraph]), and *Universal Blocks*,
    nesting child instances inside a parent's `bloks` array field [5, 6].
    Prismic separates a page type's immovable *Static Zone* from a
    *Slice Zone* (`type: "Slices"`), where each *Slice* is defined by
    `non-repeat` and `repeat` field schemas (`"Slices are sections of a
    website page — like a block of text, a hero, or a call to action.
    They are modeled using a collection of fields. Content writers build
    website pages using a stack of slices"` [7, opening paragraph]).
    Sanity models a page builder as an ordered `array` field on a page
    document whose `of` list references separately registered `object`
    or `reference` schemas (`"Schema type for arrays of other types. An
    ordered list of data. The of property specifies which value types
    the array may hold"` [8, opening paragraph]; [9]).
  - *Low-code and visual React editors (Puck, Retool):* Puck separates a
    code-side `Config` object (`"Puck's core behaviour is configured via
    the Config"` [14, opening paragraph]), which registers each
    component's editable `fields` and `render` function, from the page's
    `data` payload containing a top-level `content` array of component
    instances (`type`, `props.id`, and field values) and recursive
    `slot` arrays (`"Define a drag-and-drop area containing nested
    components"` [13, opening paragraph]). Retool serializes apps into
    **Toolscript** (`"Toolscript is a JSX-style markup language built to
    serialize Retool apps protected using Source Control"` [15, opening
    paragraph]), splitting component hierarchy and bindings in `.rsx`
    files from 2D grid coordinates (`row`, `col`, `height`, `width`) in
    `.positions.json` [15].

- **F2. Server-driven UI (SDUI) and agent-driven generative UI formats
  use the same block-reference-and-placement split over the network,
  adding explicit action bindings and client component catalogs to keep
  executable code off the wire.** `[consensus — practitioner claims and
  vendor specifications]`
  - *Server-Driven UI (Airbnb Ghost Platform, Yelp CHAOS, DoorDash
    Mosaic):* Airbnb's Ghost Platform returns a unified GraphQL payload
    organized into *Screens*, *Layouts* (`ILayout`), *Sections*,
    *Section Components*, and decoupled *Actions* [10, "Sections" and
    "Section schema"]. Yelp's CHAOS framework and DoorDash's Mosaic
    similarly shift page composition to backend JSON/GraphQL responses
    mapped to pre-compiled native client components (`"Mosaic,
    DoorDash's standard server-driven UI, or SDUI, framework offers an
    effective solution to these challenges by moving the UI definition
    to the backend, making the mobile app responsible only for rendering
    the UI components"` [11, body text]; [12]).
  - *Declarative card and agent-to-interface formats (Microsoft Adaptive
    Cards, Google A2UI):* An Adaptive Card is a static or data-bound
    JSON tree (`"An Adaptive Card is a JSON-serialized card object
    model"` [16, opening paragraph]) whose root `AdaptiveCard` holds a
    `body` array of typed elements (`TextBlock`, `Image`, `Container`,
    `ColumnSet`, `FactSet`, `Input.*`) and an `actions` array
    (`Action.OpenUrl`, `Action.Submit`, `Action.ShowCard`,
    `Action.ToggleVisibility`) rendered natively by the host [16].
    Google's A2UI (Agent-to-User Interface, open-sourced December 2025)
    adapts this pattern for streaming LLM agents (`"A2UI allows agents
    to generate the interface which best suits the current conversation
    with the agent, and send it to a front end application"` [17,
    opening paragraph]): the client advertises an allow-listed component
    catalog, and the agent streams JSON Lines messages (`createSurface`,
    `updateComponents`, `updateDataModel`) referencing only cataloged
    component types, separating component structure from a reactive data
    model [17].

- **F3. Page rearrangement is represented in data through one of three
  mechanisms: array sequence mutation, a detached order manifest, or a
  detached coordinate map.** `[consensus — vendor reports]`
  - *Array sequence mutation:* In WordPress templates [2], Storyblok
    `bloks` arrays [5], Prismic Slice Zones [7], Sanity `array` fields
    [8], Adaptive Cards `body` arrays [16], and Puck `content` and
    `slot` arrays [13], vertical or nested order is the literal index
    order of objects in the array; moving a block splices and re-inserts
    its object in the array, or moves it into another container's `slot`
    array [13].
  - *Detached order manifest:* Shopify JSON templates keep section
    instances in an unordered key-value map (`"sections": { "hero_1":
    {...} }`) and store sequence in a separate `"order": ["hero_1",
    "grid_2"]` array (with `"block_order"` inside each section) [3].
    Rearranging a page mutates only the `"order"` array without
    rewriting section objects [3].
  - *Detached coordinate map:* Retool's Toolscript keeps component
    declarations in `.rsx` files while storing 2D canvas positions in a
    separate `.positions.json` file keyed alphabetically by component ID
    (`"button1": { "row": 0, "col": 0, "height": 1 }`), isolating visual
    repositioning from component logic diffs [15].

- **F4. Disconfirming evidence confirms severe versioning, latency,
  testing, and expressiveness troubles across SDUI and block-based page
  builders.** `[consensus — practitioner claims and vendor reports]`
  - *Schema versioning across client releases:* Because mobile users do
    not update apps immediately [11], changing a block's contract breaks
    older clients unless every breaking change introduces a new versioned
    type. Yelp's CHAOS team reports incrementing component types on
    change (`"When changing a component or action, we increment the
    version. For example, adding style to the CHAOS button introduces
    chaos.button.v2"` [12, "Versioning components & actions"]) and
    tracking `"start: <app version>"` per platform [12].
  - *Payload bloat and network round-trips:* Returning deep UI trees and
    data together inflates payloads; DoorDash had to build pagination
    into Mosaic because returning 1,000+ store items in an SDUI payload
    caused severe latency [11], while Yelp's CHAOS bundles multiple
    views into a single configuration to avoid extra GraphQL round-trips
    over slow mobile networks [12].
  - *Multi-client manual verification overhead:* Yelp notes that backend
    engineers modifying an SDUI view must verify multiple platforms and
    app versions across simulators (`"manual testing is cumbersome for a
    backend developer who needs to verify multiple platforms or app
    versions"` [12, body text]).
  - *Rigidity, locking, and merge conflicts:* Block editors have to add
    explicit locking (`templateLock` in WordPress block templates [2])
    and slot allow-lists (`allow` in Puck slots [13], `choices` in
    Prismic Slice Zones [7]) to stop users from breaking visual layout
    invariants. In source-controlled low-code tools, editing the same
    page causes Git merge conflicts when two authors add or move
    blocks simultaneously [15].

- **F5. Public AI-agent repositories standardize single-file visual
  identity specifications (`DESIGN.md`) and occasionally per-component
  API reference Markdown files (`docs/Button.md`), but no published
  multi-team practice was found where a page Markdown file composes a
  screen by referencing one Markdown file per interface element.**
  `[emerging — audit / dataset study (2026-11-13) and single source
  practitioner artifact]`
  - The *DesignSpecs* study (Wei and Maalej, November 13, 2026,
    `arXiv:2611.17713`) mined 613,207 files named `DESIGN.md` across
    GitHub in October 2026 and curated 36,906 verified visual design
    specifications across 15,794 non-fork repositories [18, Abstract].
    These files follow Google Stitch's `DESIGN.md` format (open-sourced
    April 2026), which places machine-readable tokens (`colors`,
    `typography`, `rounded`, `spacing`, and small `components` token
    blueprints) in YAML frontmatter followed by Markdown prose in a
    *single* repository-wide file governing the visual identity of a
    design system (sense 3 of "design"), while other `DESIGN.md` files
    hold technical architecture plans (sense 2 of "design") [18,
    Abstract].
  - A few component libraries ship AI-oriented Markdown documentation
    using one Markdown file per component—for example, CleanPlate UI
    ships an `llms.txt` root index pointing to `"docs/ — One Markdown
    file per component (eg docs/Button.md, docs/PageHeader.md). Each doc
    includes props tables, TypeScript types, usage examples, behavior
    notes, and related components"` [19, "LLM / AI-friendly
    documentation"]. However, those files document a code library's API
    for coding assistants; they are not paired with declarative Markdown
    page files that assemble a screen by referencing element Markdown
    files.

## Unexpected

- **Low-code editors and agent-UI protocols are actively retreating from
  deeply nested single-file JSON trees.** Retool replaced its monolithic
  JSON/YAML app serialization with **Toolscript**, splitting JSX-style
  structural markup (`.rsx`) from a flat, alphabetically sorted
  coordinate file (`.positions.json`) specifically to make Git diffs
  human-readable and make layout merge conflicts resolvable [15].
  Similarly, Puck deprecated its separate global `<DropZone />` API in
  favour of inline typed `slot` fields [13], while Google's A2UI avoids
  deep nested JSON generation by streaming incremental JSONL messages
  and separating the component tree from a reactive data model to reduce
  LLM token overhead and syntax failures [17].

- **The filename `DESIGN.md` is massively overloaded across GitHub
  repositories.** In October 2026, Wei and Maalej found 613,207 files
  named `DESIGN.md` on GitHub, of which only 36,906 were valid visual
  design specifications (sense 3 of "design"); the vast majority used
  the same filename for software architecture and technical design plans
  (sense 2 of "design") [18, Abstract].

## Not found

- **A published team practice of one Markdown file per UI element paired
  with page Markdown files that compose pages by referencing them:**
  Searched across GitHub, arXiv, and web engineering blogs (`"one
  markdown file per component"`, `"page markdown" UI specification`,
  `"DesignSpecs" DESIGN.md`). While single-file `DESIGN.md` visual
  specifications [18] and per-component API reference docs (`docs/*.md`
  with `llms.txt` [19]) exist, no primary engineering write-up or
  standard was found in which pre-implementation UX/UI specifications
  decompose every screen element into its own functional Markdown file
  and define pages as Markdown manifests referencing those files.

## Options

1. **Adopt a two-layer Markdown-with-frontmatter architecture modeled on
   Shopify JSON templates / Puck Slots (Element `.md` definitions + Page
   `.md` manifests):**
   - *How it works:* Each reusable interface element (e.g., search field,
     pricing card) has a small Markdown file whose YAML frontmatter or
     structured table declares its ID, inputs/settings, states, and
     allowed child slots, and whose prose states its functional
     behaviour. Each page Markdown file declares an ordered list (or
     keyed map + `order` list) of element references, passing page-level
     setting overrides, slot assignments, and actions.
   - *Trade-offs:* Mirrors the battle-tested separation of concerns in
     Shopify [3, 4], Puck [13, 14], and Prismic [7]; keeps AI agent
     context small per element [19]; however, it is a novel convention
     for Markdown UX specs with no off-the-shelf linter (unlike
     single-file `DESIGN.md` [18]), and cross-element interactions or
     page-level state transitions can become fragmented across files
     (the same boundary leak seen in SDUI [11, 12]).

2. **Separate structural composition from spatial layout coordinates
   (the Retool Toolscript pattern):**
   - *How it works:* Keep the page's logical hierarchy, element
     references, and functional bindings in the page's main Markdown body
      while isolating 2D responsive placement (grid areas, zones, or row/
     column spans) in a dedicated layout block or companion table keyed
     by element instance ID.
   - *Trade-offs:* Prevents visual rearrangement from polluting diffs of
     functional behaviour and simplifies human-agent review [15], at the
     cost of maintaining two synchronized views of the same page.

3. **Keep global visual identity in a single `DESIGN.md` file and keep
   element/page Markdown files strictly functional:**
   - *How it works:* Use the open-source `DESIGN.md` format [18] for
     sense 3 of design (colours, typography, spacing tokens) and restrict
     per-element and per-page Markdown files to sense 1/2 (functional
     UX behaviour, states, data bindings, and slot composition).
   - *Trade-offs:* Aligns with the 36,906-file ecosystem documented in
     *DesignSpecs* [18] and prevents per-block styling drift reported in
     page builders.

## Relevance to this project

The principal's hypothesis—that every screen element can have a small
Markdown definition of its own carrying its function, while a page
definition names which elements it holds and where they stand—is
architecturally identical to the data model used across all six software
families examined here (F1, F2, F3), even though expressing that split
in *pre-build Markdown files* rather than JSON/Liquid/JSX is not yet a
published multi-team standard (F5).

*Recommendation (agent inference):* Keep the small-definition-plus-page-
composition model, and design its contract directly from the lessons of
Shopify OS 2.0 [3, 4], Puck Slots [13, 14], and Retool Toolscript [15]:
1. **In the element definition file:** Define the element's stable
   `type` slug, its configurable `settings`/`props`, its named child
   `slots` (with optional `allow` restrictions [13]), its local states,
   and its emitted `actions` [10, 16]. Keep visual-identity tokens out
   of element files and in a single visual-identity specification [18].
2. **In the page definition file:** Give each placed element a unique
   *instance ID* (distinct from its element *type*, as Shopify's
   `sections` map and Puck's `props.id` do [3, 14] so a page can hold
   two instances of the same element), bind its settings and child slot
   contents, and declare page-level state and cross-element action
   wiring explicitly at the page level so multi-element interactions do
   not fall into the SDUI gap between blocks (F4).
3. **For rearrangement:** Use either an explicit ordered list (or JSX-
   like nested list) for reading flow plus a keyed placement map when 2D
   grid positioning matters, following Retool's separation of structure
   from position [15].

**Consult when:** Designing the schema and file layout for element
Markdown files and page Markdown files; deciding how a page file
references multiple instances of the same element or nests elements
inside layout containers/slots; or mitigating versioning and cross-block
interaction limits in modular UI descriptions.

## Sources

1. **Metadata in block.json**, WordPress Developer Resources (Block
   Editor Handbook), undated (refers to WordPress 5.8+; how dated:
   undated reference documentation),
   https://developer.wordpress.org/block-editor/reference-guides/block-api/block-metadata/
   — kind: primary (vendor documentation); how read: summarised fetch
   (opening paragraph and section headings extracted verbatim);
   original.
2. **Templates**, WordPress Developer Resources (Block Editor Handbook),
   undated (how dated: undated reference documentation),
   https://developer.wordpress.org/block-editor/reference-guides/block-api/block-templates/
   — kind: primary (vendor documentation); how read: summarised fetch
   (opening paragraph and section headings extracted verbatim);
   original.
3. **JSON templates**, Shopify Developer Documentation, undated (how
   dated: undated reference documentation),
   https://shopify.dev/docs/themes/architecture/templates/json-templates
   — kind: primary (vendor documentation); how read: summarised fetch
   (opening paragraph and schema structure extracted verbatim);
   original.
4. **Sections**, Shopify Developer Documentation, undated (how dated:
   undated reference documentation),
   https://shopify.dev/docs/themes/architecture/sections
   — kind: primary (vendor documentation); how read: summarised fetch
   (opening paragraph and schema structure extracted verbatim);
   original.
5. **Blocks | Storyblok Documentation**, Storyblok, undated (how dated:
   undated reference documentation),
   https://www.storyblok.com/docs/developers/concepts/blocks
   — kind: primary (vendor documentation); how read: summarised fetch
   (opening quote and block classification extracted); original.
6. **Content modeling, explained | Storyblok Documentation**, Storyblok,
   undated (how dated: undated reference documentation),
   https://www.storyblok.com/docs/guide/essentials/content-structures
   — kind: primary (vendor documentation); how read: summarised fetch
   (opening paragraph and Stories/Bloks/Fields hierarchy extracted
   verbatim); original.
7. **Slices — Prismic Docs**, Prismic, undated (how dated: undated
   reference documentation),
   https://prismic.io/docs/slices
   — kind: primary (vendor documentation); how read: summarised fetch
   (opening paragraph and section headings extracted verbatim);
   original.
8. **Array**, Sanity Documentation, undated (how dated: undated
   reference documentation),
   https://www.sanity.io/docs/studio/array-type
   — kind: primary (vendor documentation); how read: summarised fetch
   (opening quote extracted verbatim); original.
9. **What is a page builder? (Content modeling for a page builder)**,
   Sanity Learn, undated (how dated: undated course documentation),
   https://www.sanity.io/learn/course/content-modeling-for-a-page-builder/lessons/what-is-a-page-builder
   — kind: primary (vendor documentation); how read: summarised fetch
   (page builder `array` of `object` and `reference` schema structure);
   original.
10. **A Deep Dive into Airbnb's Server-Driven UI System**, Ryan Brooks
    (The Airbnb Tech Blog on Medium), 2021-06-29 (how dated: byline),
    https://medium.com/airbnb-engineering/a-deep-dive-into-airbnbs-server-driven-ui-system-84224eeb8fcf
    — kind: primary (engineering write-up by system builder); how read:
    summarised fetch (Ghost Platform architecture and `"Sections"` /
    `"Section schema"` headings verified); original.
11. **Part 1: DoorDash 2024 Summer Intern Projects ("Why DoorDash needs
    a server-driven UI with mosaic")**, Yufan (Joy) Xiao / DoorDash
    Engineering, 2024 (how dated: byline/title),
    https://careersatdoordash.com/blog/part-1-doordash-2024-summer-intern-projects/
    — kind: primary (engineering write-up by system builder); how read:
    summarised fetch (three paragraphs on Mosaic SDUI and pagination
    extracted verbatim); original.
12. **CHAOS: Yelp's Unified Framework for Server-Driven UI**, Joshua
    Walstrom (Yelp Engineering Blog), 2024-03-14 (how dated: byline),
    https://engineering.yelp.com/2024/03/chaos-yelps-unified-framework-for-server-driven-ui.html
    — kind: primary (engineering write-up by system builder); how read:
    summarised fetch (four passages on component versioning, network
    round-trips, multi-client maintenance, and manual simulator testing
    extracted verbatim); original.
13. **Slot | Puck**, Measured (Puck Documentation), undated (how dated:
    undated reference documentation),
    https://puckeditor.com/docs/api-reference/fields/slot
    — kind: primary (vendor documentation); how read: summarised fetch
    (opening definition, `slot` field schema, `walkTree`, and migration
    from `DropZone` extracted verbatim); original.
14. **Component Configuration | Puck**, Measured (Puck Documentation),
    undated (how dated: undated reference documentation),
    https://puckeditor.com/docs/integrating-puck/component-configuration
    — kind: primary (vendor documentation); how read: summarised fetch
    (opening sentence and `config` vs. `data` structure extracted
    verbatim); original.
15. **Toolscript | Retool Docs**, Retool, undated (how dated: undated
    reference documentation),
    https://docs.retool.com/source-control/concepts/toolscript
    — kind: primary (vendor documentation); how read: summarised fetch
    (opening quote and `.rsx` vs. `.positions.json` / `.metadata.json`
    serialization details extracted verbatim); original.
16. **Getting Started - Adaptive Cards | Microsoft Learn**, Microsoft,
    2023-08-28 (how dated: byline),
    https://learn.microsoft.com/en-us/adaptive-cards/authoring-cards/getting-started
    — kind: primary (vendor specification documentation); how read:
    summarised fetch (opening sentence and root/body/actions schema
    elements extracted verbatim); original.
17. **Introducing A2UI: An open project for agent-driven interfaces**,
    Google A2UI Team (Google Developers Blog), 2025-12-15 (how dated:
    byline),
    https://developers.googleblog.com/introducing-a2ui-an-open-project-for-agent-driven-interfaces/
    — kind: primary (vendor engineering announcement and architecture
    overview); how read: summarised fetch (opening paragraph extracted
    verbatim; JSONL streaming, decoupled data model, and component
    catalog architecture); original.
18. **DesignSpecs: A DESIGN.md Dataset of Visual Design Specifications
    for AI Agents**, Jialiang Wei and Walid Maalej (arXiv), 2026-11-13
    (how dated: structured data / arXiv v1 submission date),
    https://arxiv.org/abs/2611.17713
    — kind: primary (empirical software-engineering dataset paper); how
    read: summarised fetch (full abstract extracted verbatim); original.
19. **Introduction / Installation - Docs · Storybook (CleanPlate UI)**,
    Sivadass, undated (how dated: undated documentation),
    https://sivadass.in
    — kind: primary (practitioner repository documentation artifact);
    how read: summarised fetch (`"LLM / AI-friendly documentation"`
    section on `llms.txt` and `docs/<ComponentName>.md` extracted
    verbatim); original.

## Opened and not used

- `https://www.storyblok.com/docs/concepts/components` — not opened:
  known dead URL (HTTP 404 from an earlier run); superseded by [5] and
  [6].
- `https://www.sanity.io/docs/page-builder` — left out: redirect/alias
  for Sanity's page-builder learning material; superseded by canonical
  schema reference [8] and lesson [9].
- `https://adaptivecards.io/explorer/` — left out: interactive schema
  explorer landing page; superseded by dated Microsoft Learn
  specification page [16].
- `https://a2ui.org` — left out: project landing page; superseded by the
  dated Google Developers Blog announcement with verbatim architectural
  quotes [17].

## Search record

- **Queries run (in order):**
  1. `WordPress block editor block.json templates patterns architecture documentation`
  2. `Shopify architecture JSON templates sections blocks schema documentation`
  3. `Storyblok components bloks Prismic slices Sanity page builder schema documentation`
  4. `server-driven UI engineering blog Airbnb Lyft Reddit DoorDash architecture`
  5. `Microsoft Adaptive Cards schema specification Google A2UI generative UI agent interface format`
  6. `low-code page schema JSON Retool Appsmith ToolJet Puck component tree`
  7. `"one markdown file per component" OR "page markdown" UI specification AI agent repository`
  8. `server-driven UI problems` *(disconfirming query 1)*
  9. `page builder blocks limitations` *(disconfirming query 2)*
  10. `Storyblok documentation components bloks schema visual editor` (`domain: storyblok.com`)
  11. `Prismic documentation slices slice zone page type model.json` (`domain: prismic.io`)
  12. `Sanity documentation page builder array of objects schema type` (`domain: sanity.io`)
  13. `"A Deep Dive into Airbnb's Server-Driven UI System" Ryan Brooks Medium`
  14. `Adaptive Cards schema explorer specification JSON elements` (`domain: adaptivecards.io`)
  15. `Puck documentation configuration data content zones components` (`domain: puckeditor.com`)
  16. `"DesignSpecs" DESIGN.md arxiv OR github UI component markdown specification`
  17–38. Targeted URL, date, author, and verbatim-excerpt verification
     queries across `developer.wordpress.org`, `shopify.dev`,
     `storyblok.com`, `prismic.io`, `sanity.io`, `medium.com`,
     `developers.googleblog.com`, `puckeditor.com`, `arxiv.org`,
     `learn.microsoft.com`, `sivadass.in`, `yelp.com`,
     `careersatdoordash.com`, and `docs.retool.com`.
- **Pages opened (via grounded summarising fetches with verbatim excerpt
  extraction):** 19 primary sources cited ([1]–[19]) plus 3 superseded
  pages listed in `## Opened and not used`. Direct shell `curl.exe` was
  blocked by the environment's command policy, so all fetches were
  performed through `search_web` and marked `summarised fetch`.
- **What the disconfirming queries found:** Both `"server-driven UI
  problems"` and `"page builder blocks limitations"` returned concrete
  practitioner reports confirming the card's expectations: strict
  component/action version proliferation across mobile app versions
  (`chaos.button.v2` in Yelp CHAOS [12]), payload size and network
  latency bottlenecks requiring custom pagination or multi-view bundling
  (DoorDash Mosaic [11], Yelp CHAOS [12]), cumbersome manual multi-
  platform simulator testing [12], layout rigidity vs. inconsistency in
  block editors requiring template locking and slot allow-lists [2, 13],
  and Git merge conflicts in serialized page trees [15].
- **Reason the run ended:** Both parts of the card's stop rule were met:
  every route in the question has at least one verified primary source
  ([1]–[19]) and differently worded queries for per-element + per-page
  Markdown specifications returned no additional primary architectures
  beyond `DESIGN.md` [18] and `llms.txt` + `docs/<Component>.md` [19].
