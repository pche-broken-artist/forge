---
date: 2026-11-21
project: forge
topic: Text and the design tool
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 11; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":44598,"output_tokens":17809,"thinking_tokens":8692,"cache_read_tokens":127808,"total_tokens":62407}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-11-design-tool
status: immutable
---

# How textual or code sources and design tools connect today and what a text-first description must keep

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

In this note, "design" means the visual and structural representation of
an interface inside a design tool (such as Figma or Penpot), while
"design tokens" and "design system" name the shared visual identity
primitives and component catalog. All findings below rest on tertiary
summarised fetches of primary vendor documentation, W3C specifications,
and public repositories, because direct HTTP fetching is disabled in the
research environment.

Connections between text or code and design tools today split sharply by
layer: **design tokens and variables move bi-directionally** via the W3C
Design Tokens Community Group (DTCG) 2025.10 JSON standard, Git sync
plugins, and APIs, whereas **component links and screen layouts run
reliably in one direction at a time**. The disconfirming queries
confirmed that full layout and component round-tripping between code and
a design canvas fails in practice because canvases lack application
state machines, Code Connect mappings are static one-way templates into
Dev Mode, and DOM-to-canvas captures produce flattened layers that break
component hierarchies. The unexpected finding is that in 2025–2026 both
Figma and Penpot shipped official Model Context Protocol (MCP) servers
that expose their internal Plugin APIs to AI agents (`use_figma` in
Figma, shape and token tools in Penpot), allowing an agent to generate
and edit native canvas frames, component instances, and bound variables
directly from a structured text specification if that specification
preserves stable IDs, typed variant properties, Flexbox/Grid layout
semantics, and W3C DTCG token paths.

## Question

#### Card 11: Text and the design tool
- **Question:** How are a textual or code source and a design tool
  connected today (reading a design as structured data, writing a design
  from structured text, linking components to code, keeping tokens and
  variables in step), for the dominant design tool and for open
  alternatives: in which direction does each connection run, and what
  must a text-first description keep (identifiers, a vocabulary of
  components, tokens) so that such a connection can be added later?
- **Why it matters:** a specialist will need the design tool, and the
  first step must not close that path.
- **What would answer it:** the vendors' documentation of their own
  interfaces.
- **Where to look:** the design tools' programming interfaces, developer
  modes, component-to-code links and agent servers; token tools; the
  open design tool's format and interface. Search words from card 1:
  "handoff" names the passage and a tool's features for it, not the
  document; for the document "design specs", "annotations", "ready for
  dev"; vendors' pages on their own market are to be expected and are
  left out by the brief. Primary artefacts in public repositories
  (schemas, component and page files, agents' rules and prompt files,
  the schemas of servers for design tools, issue trackers) before
  commentary about them.
- **Disconfirming query:** "design to code round trip problems", "design
  tool or code as source of truth"; expected: the connection runs well
  in one direction only.
- **Stop rule:** nothing new from a differently worded query and every
  route has a primary source; ten to fifteen pages opened.

**Baseline to beat:** Before this note, the project might either assume
that a Markdown UI description can be round-tripped arbitrarily with
Figma and Penpot later, or assume that design tools are purely manual
drawing canvases that cannot be populated from structured text. This
note must replace both assumptions with the exact API boundaries,
directionality, plan restrictions, and structural fields required across
Figma, Penpot, and the W3C token standard.

## Key findings

- **F1. Figma's HTTP REST API reads the full canvas node tree as JSON
  but is strictly read-only for canvas geometry and layers.** [consensus
  — vendor documentation, resting on summarised fetches of [1][2]]
  Through `GET https://api.figma.com/v1/files/:key` and
  `GET https://api.figma.com/v1/files/:key/nodes?ids=:ids` (scope
  `file_content:read`), external tools read the hierarchical document
  tree (`DOCUMENT`, `CANVAS`, `FRAME`, `COMPONENT`, `INSTANCE`) along
  with node IDs, layout rules, styles, component properties, and bound
  variables [1]. The REST API provides no `POST`, `PUT`, or `PATCH`
  endpoints to create or modify canvas layers or frames; server-side
  writes are restricted to comments, webhooks, Dev Mode links
  (`dev_resources`), and Enterprise variables [1][2].

- **F2. Writing or mutating a Figma design from structured text or code
  requires the client-side Plugin API or the official Figma MCP Server
  wrapping it.** [consensus — vendor documentation, resting on
  summarised fetches of [3][4]]
  Figma's Plugin API runs JavaScript/TypeScript inside the active Figma
  runtime and exposes constructors and mutators including
  `figma.createFrame()`, `figma.createComponent()`,
  `figma.importComponentByKeyAsync()`, and `node.setBoundVariable()` [3].
  In 2025–2026, Figma exposed these capabilities to external AI agents
  through the official Figma MCP Server (`https://mcp.figma.com/mcp` and
  local desktop `http://127.0.0.1:3845/mcp`) via two distinct write
  tools: `use_figma`, which executes Plugin API JavaScript to build and
  edit native frames, Auto Layout structures, variants, and variables on
  the canvas; and `generate_figma_design`, which converts rendered web
  interfaces or specs into editable Figma layers [4]. Reading on the
  same MCP server uses `get_design_context`, `get_metadata`,
  `get_variable_defs`, `get_code_connect_map`, and `get_screenshot` [4].

- **F3. Figma Code Connect links design components to repository code
  in one direction only: from repository mapping files into Dev Mode and
  MCP code-generation output.** [consensus — vendor documentation and
  practitioner reports, resting on summarised fetches of [4][5][11]]
  In `@figma/code-connect` (`github.com/figma/code-connect`), developers
  write declarative mapping files that bind a code component to a
  specific Figma node URL (`?node-id=...`) and map Figma component
  properties to code props using `figma.string()`, `figma.boolean()`,
  `figma.enum()`, `figma.instance()`, and `figma.children()`, published
  via `npx figma connect publish` [5]. The Figma MCP server reads these
  mappings via `get_code_connect_map` and writes new mappings via
  `add_code_connect_map` and `send_code_connect_mappings` [4]. However,
  Code Connect is a one-way template layer: Figma does not execute
  repository code to update canvas graphics, so changing a component's
  implementation or props in Git never updates the visual component in
  Figma [5][11].

- **F4. Design tokens have a stable standard (W3C DTCG 2025.10) and are
  the only artifact class with mature bi-directional synchronisation
  between git text files and design tools, though Figma gates its
  Variables REST API behind Enterprise plans.** [consensus — standard
  and vendor documentation, resting on summarised fetches of
  [2][6][7][8][9]]
  On 2025-10-28, the W3C Design Tokens Community Group published stable
  specification version `2025.10` (`https://www.designtokens.org/TR/2025.10/`,
  schema `https://www.designtokens.org/schemas/2025.10/format.json`),
  standardising JSON token files around `$value`, `$type`, and
  curly-brace alias references (`{color.base.black}`) [6]. Both Figma
  and Penpot now support native file import and export of W3C DTCG JSON
  token files [7][11]. For automated pipelines, Tokens Studio
  synchronises W3C DTCG JSON bi-directionally with GitHub, GitLab,
  Bitbucket, and Azure DevOps repositories [9], and Style Dictionary
  compiles DTCG JSON into platform code (CSS variables, Tailwind, iOS,
  Android) [8]. Figma's native Variables REST API (`GET` and `POST
  /v1/files/:file_key/variables`, scopes `file_variables:read` and
  `file_variables:write`) supports transactional bulk reads and writes
  of `variableCollections`, `variableModes`, `variables`, and
  `variableModeValues` in Figma's internal ID-based schema, but is
  restricted to Figma Enterprise organisations (as of 2026) [2].

- **F5. Penpot (the leading open-source alternative) uses native CSS
  Grid, Flexbox, SVG, and W3C DTCG tokens in its data model and exposes
  both read and write tools through its Plugin API and MCP server.**
  [consensus — vendor documentation, resting on summarised fetches of
  [7][10]]
  Unlike Figma's proprietary layout tree, Penpot models layout directly
  with CSS Grid and Flexbox concepts (`help.penpot.app/user-guide/flexible-layouts/`)
  and stores design tokens natively in W3C DTCG format with sets and
  themes (`help.penpot.app/user-guide/design-tokens/`) [7]. Its official
  MCP server (`help.penpot.app/mcp-server/`) connects via a browser
  WebSocket plugin to the active design file and exposes bidirectional
  tools: `get_shape_tree`, `get_shape_details`, `get_shape_css`, and
  `get_design_tokens` for reading, alongside `create_frame`,
  `create_rectangle`, `set_fill`, `set_layout`, and programmatic
  `TokenCatalog`/`TokenSet`/`TokenTheme` mutations for writing [10].

- **F6. Disconfirming evidence confirms that screen-level and
  component-level round-tripping between a design tool and code breaks
  on layout semantics, component hierarchy, interactive states, and
  branch merging.** [consensus — practitioner reports and vendor
  documentation, resting on summarised fetches of [11][12]]
  The disconfirming queries (`"design to code round trip problems"` and
  `"design tool or code as source of truth"`) showed four structural
  barriers that prevent lossless two-way sync of screens:
  1. *Layout mismatch:* freeform or visually grouped layers on a canvas
     do not map deterministically to responsive CSS Flexbox/Grid trees
     unless constrained to strict Auto Layout / Flexbox rules [12].
  2. *State and logic loss:* production components manage asynchronous
     and edge states (`loading`, `error`, `empty`, `partial-data`, race
     conditions) that have no representation in static canvas variants
     [12].
  3. *Code-to-canvas flattening:* importing rendered HTML/DOM back into
     a design canvas (such as `generate_figma_design` or DOM capture
     plugins) produces flattened layer trees ("layer soup") detached
     from the design system's master components and variables unless
     reconstructed programmatically via component keys and variable
     bindings [4][12].
  4. *Version control incompatibility:* Git tracks line-level branches
     and merges in text, whereas design tools hold monolithic document
     states that cannot auto-merge concurrent structural refactors from
     code [12].

- **F7. To preserve a future connection to Figma or Penpot, a text-first
  Markdown UI description must keep five structural invariants: stable
  IDs with external node-link slots, a five-primitive property
  vocabulary, W3C DTCG token paths, Flexbox/Grid layout rules, and a
  boundary between visual variants and runtime state.** [emerging —
  synthesised from primary interface constraints in [1][3][4][5][6][7][10]]
  Because every programmatic bridge to Figma and Penpot requires
  specific keys and types:
  1. *Identifiers:* Each reusable component and screen element needs a
     stable text slug plus an optional external mapping slot (`figma_url`
     / `node_id` / `component_key` or Penpot shape UUID) required by
     Code Connect (`figma.connect`), REST `nodes?ids=`, and
     `importComponentByKeyAsync` [1][3][5].
  2. *Component property vocabulary:* Component definitions must type
     their configurable properties using the five primitives supported
     by Code Connect and design tool component properties: text strings
     (`figma.string`), booleans (`figma.boolean`), discrete variant
     enums (`figma.enum`), nested component instances
     (`figma.instance`), and named child slots (`figma.children`) [5].
  3. *Token references:* All visual values (colour, spacing, typography,
     radius, shadow) must be written as semantic paths compatible with
     W3C DTCG 2025.10 (`{color.text.primary}`) rather than raw hex or
     pixel literals, so they bind directly to Figma variables
     (`setBoundVariable`) and Penpot's `TokenCatalog` [3][6][7].
  4. *Layout containers:* Page and element compositions must specify
     flow direction, alignment, gap, padding, and grid tracks (mapping
     to Penpot CSS Grid/Flexbox and Figma Auto Layout) rather than
     2D coordinates [4][7][10].
  5. *Variant vs. state separation:* Static visual variants (`size`,
     `intent`, `disabled`) and theme modes (`light`, `dark`) must be
     stored separately from behavioural state machines and data-fetching
     rules that design canvases cannot hold [5][12].

## Unexpected

The card expected that the connection between text/code and design tools
runs well in one direction only (either reading a design to generate
code or pushing tokens). While lossless two-way syncing of arbitrary
edits remains broken [12], both Figma and Penpot launched official MCP
servers in 2025–2026 (`use_figma` and `generate_figma_design` in Figma
[4]; shape and token creation tools in Penpot [10]) that expose their
client-side Plugin APIs to AI agents. This creates a viable
**Text-to-Design generation path** that did not exist in earlier
REST-only workflows: an AI agent can read a Markdown UI description and
call `use_figma` or the Penpot MCP server to instantiate library
components, configure Auto Layout / Flexbox frames, and bind variables
on a live canvas for a UX/UI specialist to inspect and refine [4][10].

A second unexpected operational constraint is **tier gating on token
automation**: Figma's server-side Variables REST API (`GET` and `POST
/v1/files/:file_key/variables`) is restricted to Figma Enterprise plans
[2]. For solo developers and small companies (a target persona of this
project's frame), automated token synchronisation cannot use Figma's
REST API and must instead rely on native W3C DTCG JSON file
import/export, the Figma MCP Server (`use_figma` / `get_variable_defs`),
Tokens Studio Git sync, or Penpot [2][4][7][9][11].

## Not found

- **No open, vendor-neutral standard for full UI screen and component
  canvas trees:** While the W3C DTCG `2025.10` specification standardises
  design tokens [6], searches across W3C, Figma, and Penpot
  documentation found no equivalent cross-vendor standard schema for
  component hierarchies, variant definitions, or screen layouts.
- **No headless server-side canvas write API for either Figma or
  Penpot:** Neither Figma's REST API [1] nor Penpot's documented MCP
  architecture [10] allows writing shapes or frames to a design file
  purely headless in CI without an active client session or plugin
  runtime bridging the write operations (`use_figma` and Penpot's MCP
  plugin both execute through an active session runtime) [4][10].

## Options

1. **Option A: Text-first source of truth with one-way export to design
   tools (via MCP + W3C DTCG tokens) and Code Connect for existing
   component libraries.**
   - *How it works:* The Markdown UI specification in Git is the primary
     source of truth for screen composition, user flows, and behavioral
     states. Visual primitives are kept in a W3C DTCG `2025.10` JSON
     file in Git. When a UX/UI specialist wants to work in Figma or
     Penpot, an agent uses `use_figma` or the Penpot MCP server to
     materialise the Markdown screen specification onto the canvas using
     bound tokens and library components. If a specialist updates a
     screen in the design tool, an agent reads the delta via
     `get_design_context` / `get_shape_tree` and proposes a Markdown
     diff in Git for human review.
   - *Trade-offs:* Avoids automated two-way merge conflicts by routing
     any canvas-to-text change through an agent-proposed Git diff; works
     on non-Enterprise Figma plans and Penpot; never loses behavioral
     states kept in Markdown. Requires discipline that canvas edits are
     pulled back into Markdown via agent review rather than treated as
     silent overrides.

2. **Option B: Dual source of truth split by layer (Design tool owns
   visual layout and tokens; Markdown owns requirements, flows, and
   state logic).**
   - *How it works:* Markdown defines only what elements exist, their
     functional rules, states, and copy, while linking each element via
     `node_id` to a Figma or Penpot frame that owns all spatial layout
     and styling.
   - *Trade-offs:* Familiar to traditional design-led teams, but breaks
     the solo-builder workflow when no design tool is used, and creates
     immediate drift whenever layout changes in code or text without
     updating the canvas [12].

3. **Option C: Strict W3C DTCG + Code Connect vocabulary in Markdown now,
   deferring live MCP canvas sync to an optional adapter.**
   - *How it works:* The Markdown schema enforces the five structural
     invariants from **F7** (stable IDs with optional `node_id` slots,
     the five Code Connect prop types, W3C DTCG token references,
     Flexbox/Grid container semantics, and separated runtime states)
     from day one, without building a Figma/Penpot sync adapter in the
     first version.
   - *Trade-offs:* Zero initial integration maintenance while
     guaranteeing that no element or page definition written today needs
     to be rewritten when a Figma or Penpot MCP bridge is added later.

## Relevance to this project

*(Inferences and recommendations in this section are the agent's own,
drawn from the findings above.)*

The project should adopt **Option C immediately as the structural rule
for the Markdown specification**, designed to support **Option A** when
a UX/UI specialist connects Figma or Penpot. This recommendation is
chosen against Option B (which would force every solo developer to
maintain a design canvas and split layout from structure) and against
unconstrained prose Markdown (which would fail to map to Code Connect
props, W3C tokens, or Auto Layout / Flexbox containers later).

Specifically, the project's proposed idea—that *every element of a
screen has a small definition of its own in Markdown that carries its
function, and a page definition names which elements it holds and where
they stand*—aligns cleanly with both Figma and Penpot **if and only if**
the Markdown format enforces five rules:
1. **Element definitions** must separate their *visual variant and
   content properties* (restricted to `string`, `boolean`, `enum`,
   `instance`, and `children` slots so they map 1:1 to Figma Code
   Connect [5] and component properties) from their *behavioural states
   and interaction rules* (`loading`, `error`, validation, events),
   which remain in Markdown because design tools cannot represent them
   [12].
2. **External link metadata** on each element and page definition must
   reserve optional fields for `design_link` (carrying a Figma file key
   + `node-id` or Penpot file/shape UUID) and `code_component` (carrying
   the repository import path and component name used by Code Connect's
   `get_code_connect_map`) [4][5].
3. **Page definitions** ("where they stand") must express spatial
   arrangement using **Flexbox and Grid container terminology**
   (direction, wrap, justify, align, gap, padding, grid columns/rows)
   rather than prose ("top right") or pixel coordinates, so an agent can
   translate them directly into Penpot's native CSS Flexbox/Grid layouts
   [7] or Figma's Auto Layout via `use_figma` [4].
4. **Visual tokens** referenced anywhere in element or page definitions
   must use **W3C DTCG `2025.10` token path syntax** (`{color...}`,
   `{spacing...}`, `{font...}`) [6] and never raw hex codes or pixel
   numbers.
5. **Reconciliation direction** when a specialist uses a design tool
   must be **agent-mediated diffing, not blind overwrite**: an agent can
   materialise a Markdown page onto a Figma/Penpot canvas via MCP
   (`use_figma` / Penpot MCP) and can read a specialist's canvas edits
   back via `get_design_context` / `get_shape_tree` to propose a
   targeted update to the layout/variant sections of the Markdown file
   without erasing its behavioural state specifications [4][10][12].

**Consult when:**
- Designing the schema and frontmatter of element definitions, component
  catalogs, and page layout definitions in the Markdown UX/UI framework.
- Deciding how design tokens and theme modes (`light`/`dark`) are named
  and stored alongside the Markdown specifications.
- Building or prompting an AI agent to push Markdown screen descriptions
  into Figma (`use_figma`) or Penpot (`penpot-mcp`), or to pull a
  specialist's canvas changes back into Markdown via `get_design_context`.

## Sources

1. **REST API Introduction & File Endpoints | Developer Docs** — Figma;
   undated (living vendor documentation, accessed 2026-11-21);
   https://developers.figma.com/docs/rest-api/ ; kind: primary (vendor
   documentation, read via tertiary summarised fetch); how read:
   summarised fetch (covering base URL, authentication, `GET
   /v1/files/:key`, `GET /v1/files/:key/nodes`, read-only constraint on
   canvas nodes, and resource endpoint list); original.
2. **Variables Endpoints | Developer Docs** — Figma; undated (living
   vendor documentation, accessed 2026-11-21);
   https://developers.figma.com/docs/rest-api/variables-endpoints/ ;
   kind: primary (vendor documentation, read via tertiary summarised
   fetch); how read: summarised fetch (covering `GET
   /v1/files/:file_key/variables/local`, `GET
   /v1/files/:file_key/variables/published`, `POST
   /v1/files/:file_key/variables`, `file_variables:read` and
   `file_variables:write` scopes, and the Enterprise plan restriction);
   original.
3. **Figma Plugin API Documentation (`createFrame`, `createComponent`,
   `setBoundVariable`, `importComponentByKeyAsync`)** — Figma; undated
   (living vendor documentation, accessed 2026-11-21);
   https://www.figma.com/plugin-docs/api/properties/figma-createframe/
   (alongside
   https://www.figma.com/plugin-docs/api/properties/figma-createcomponent/
   ,
   https://www.figma.com/plugin-docs/api/properties/nodes-setboundvariable/
   , and
   https://www.figma.com/plugin-docs/api/properties/figma-importcomponentbykeyasync/
   ); kind: primary (vendor documentation, read via tertiary summarised
   fetch); how read: summarised fetch (covering client-side canvas node
   creation, library component import by key, and variable binding);
   original.
4. **Tools and prompts | Figma MCP Server Developer Docs** — Figma;
   undated (living vendor documentation, accessed 2026-11-21);
   https://developers.figma.com/docs/figma-mcp-server/tools-and-prompts
   ; kind: primary (vendor documentation, read via tertiary summarised
   fetch); how read: summarised fetch (covering remote
   `https://mcp.figma.com/mcp` and local desktop endpoints, read tools
   `get_design_context`, `get_variable_defs`, `get_code_connect_map`,
   `get_metadata`, `get_screenshot`, and write/generation tools
   `use_figma`, `generate_figma_design`, `add_code_connect_map`,
   `send_code_connect_mappings`, `create_design_system_rules`);
   original.
5. **Figma Code Connect (`figma/code-connect`)** — Figma; undated
   (public GitHub repository and README, accessed 2026-11-21);
   https://github.com/figma/code-connect ; kind: primary (public
   software artefact and documentation, read via tertiary summarised
   fetch); how read: summarised fetch (covering `figma.connect()`, node
   URL mapping, property helpers `figma.string`, `figma.boolean`,
   `figma.enum`, `figma.instance`, `figma.children`, v2 template
   literals, and `npx figma connect publish`); original.
6. **Design Tokens Format Module (Version 2025.10)** — W3C Design Tokens
   Community Group (DTCG); 2025-10-28 (dated by specification header /
   structured release date); https://www.designtokens.org/TR/2025.10/
   (schema: https://www.designtokens.org/schemas/2025.10/format.json );
   kind: primary (technical standard, read via tertiary summarised
   fetch); how read: summarised fetch (covering `$value`, `$type`, type
   inheritance, and `{group.token}` curly-brace alias syntax); original.
7. **Design Tokens & Flexible Layouts | Penpot Help Center** — Penpot
   (Kaleidos); undated (living vendor documentation, accessed
   2026-11-21); https://help.penpot.app/user-guide/design-tokens/ (and
   https://help.penpot.app/user-guide/flexible-layouts/ ); kind: primary
   (vendor documentation, read via tertiary summarised fetch); how read:
   summarised fetch (covering native W3C DTCG JSON import/export, token
   sets and themes, and native CSS Grid and Flexbox layout model);
   original.
8. **Design Tokens Community Group | Style Dictionary** — Style
   Dictionary; undated (living project documentation, accessed
   2026-11-21); https://styledictionary.com/references/tokens/dtcg/ ;
   kind: primary (project documentation, read via tertiary summarised
   fetch); how read: summarised fetch (covering Style Dictionary
   ingestion and compilation of W3C DTCG format tokens); original.
9. **GitHub - Git Sync Provider | Tokens Studio Documentation** — Tokens
   Studio; undated (living vendor documentation, accessed 2026-11-21);
   https://docs.tokens.studio/sync/remotes/github ; kind: primary
   (vendor documentation, read via tertiary summarised fetch); how read:
   summarised fetch (covering bi-directional Git repository push/pull of
   W3C DTCG token JSON files); original.
10. **MCP Server Documentation | Penpot Help Center** — Penpot
    (Kaleidos); undated (living vendor documentation, accessed
    2026-11-21); https://help.penpot.app/mcp-server/ ; kind: primary
    (vendor documentation, read via tertiary summarised fetch); how
    read: summarised fetch (covering the 3-tier MCP client, server, and
    WebSocket browser plugin architecture and exposed shape, layout, and
    token read/write tools); original.
11. **Native W3C Design Tokens Import/Export and Code Connect One-Way
    Architecture** — Builder.io / Pegasus Design System / Obra Studio
    practitioner reports; 2025–2026 (dated via search index context);
    https://www.pegasusdesignsystem.com/ ; kind: secondary (practitioner
    analyses of Figma native W3C JSON token import/export and Code
    Connect Dev Mode boundaries, read via tertiary summarised fetch);
    how read: summarised fetch (covering Figma native DTCG JSON zip
    import/export and why Code Connect does not sync repository code
    changes back to the Figma canvas); original.
12. **Design-to-Code Round-Trip Problems and Source-of-Truth Trade-offs**
    — UXPin / Eleken / practitioner analyses; undated / 2025–2026
    (accessed via disconfirming query summarised fetches on 2026-11-21);
    https://www.uxpin.com/studio/blog/single-source-of-truth-design-system/
    ; kind: secondary (practitioner and industry analyses surfaced by
    the disconfirming queries, read via tertiary summarised fetch); how
    read: summarised fetch (covering layout box-model mismatch, missing
    runtime state machines on static canvases, DOM-to-canvas layer
    flattening, and Git vs. canvas merge conflicts); original.

## Opened and not used

- **Webex / Glama / Scalekit / Warp third-party guides on setting up
  Figma MCP** — left out: secondary setup tutorials superseded by
  Figma's primary MCP documentation [4].
- **Zeroheight / Atomize / TheAfrodity blog posts on Figma Variables vs.
  Tokens Studio** — left out: secondary comparisons superseded by the
  primary W3C DTCG 2025.10 specification [6], Figma Variables REST API
  docs [2], and Tokens Studio docs [9].
- **DEV Community / UIchemy / SVGMaker overviews of Penpot MCP** — left
  out: secondary commentary superseded by Penpot's official Help Center
  and MCP documentation [7][10].

## Search record

**Queries run (in order):**
1. `Figma REST API Plugin API Code Connect MCP server documentation`
2. `Figma Variables REST API W3C design tokens Tokens Studio`
3. `Penpot open format API design tokens MCP server documentation`
4. `design to code round trip problems` *(disconfirming query 1)*
5. `design tool or code as source of truth` *(disconfirming query 2)*
6. `"developers.figma.com/docs/rest-api" files nodes variables endpoints read write exact URL and specification` (domain: `developers.figma.com`)
7. `"developers.figma.com/docs/figma-mcp-server" tools get_design_context get_variable_defs get_code_connect_map use_figma generate_figma_design exact URL` (domain: `developers.figma.com`)
8. `"figma/code-connect" README figma.string figma.enum figma.instance figma.children publish parse exact URL` (domain: `github.com`)
9. `"tr.designtokens.org/format" W3C Design Tokens Format Specification 2025.10 $value $type alias exact URL and date` (domain: `tr.designtokens.org`)
10. `"help.penpot.app" design tokens W3C JSON CSS Grid Flexbox plugin API MCP server exact URLs` (domain: `help.penpot.app`)
11. `"developers.figma.com/docs/plugins" createFrame createComponent setBoundVariable importComponentByKeyAsync exact URL` (domain: `developers.figma.com`)
12. `"developers.figma.com/docs/figma-mcp-server/tools-and-prompts" OR "developers.figma.com/docs/rest-api" exact page titles URLs tools list` (domain: `developers.figma.com`)
13. `"help.penpot.app/user-guide/design-tokens" "help.penpot.app/technical-guide" file format W3C DTCG JSON import export exact page titles and details` (domain: `help.penpot.app`)
14. `"styledictionary.com" DTCG W3C design tokens format AND "docs.tokens.studio" Git sync bi-directional exact URLs and page titles`
15. `"Figma" native W3C Design Tokens import export JSON 2025 OR 2026 AND "Code Connect" limitation one-way Dev Mode`

**Pages opened (budget counting):**
Direct HTTP page fetching (`curl.exe`) was blocked by a sandbox
permission deny rule; 15 `search_web` grounding fetches were executed
(5 broad/disconfirming queries followed by 10 domain-targeted fetches
against primary documentation and specifications), yielding 12 cited
source groups and 3 excluded secondary source groups.

**What the disconfirming queries found:**
The disconfirming queries (`"design to code round trip problems"` and
`"design tool or code as source of truth"`) confirmed the card's
expectation for screen layouts and components: full visual-to-code
round-tripping breaks because static canvases do not model runtime
application state machines (`loading`, `error`, `empty`), Code Connect
mappings are static one-way templates into Dev Mode rather than two-way
component synchronisers, DOM-to-canvas captures produce flattened layers
detached from design system masters, and monolithic canvas files cannot
merge concurrent Git branch refactors. Only atomic design tokens achieve
true bi-directional synchronisation via W3C DTCG JSON.

**Reason the run ended:**
Both parts of the card's stop rule and the opening budget were reached
simultaneously at 15 fetches: every route in the question (Figma REST
API, Plugin API, Code Connect, Variables API, MCP Server; W3C DTCG
2025.10, Tokens Studio, Style Dictionary; Penpot layouts, native tokens,
and MCP Server) had a primary source, and differently worded queries
returned no new connection mechanisms.
