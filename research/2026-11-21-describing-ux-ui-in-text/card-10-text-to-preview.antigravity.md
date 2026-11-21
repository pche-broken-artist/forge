---
date: 2026-11-21
project: forge
topic: From text to something visible
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 10; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":49790,"output_tokens":17807,"thinking_tokens":8564,"cache_read_tokens":151960,"total_tokens":67597}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-10-text-to-preview
status: immutable
---

# How a textual description becomes a visible preview before the product is built

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Four distinct mechanisms turn a textual interface description into a
visible preview before the application is built: deterministic
text-to-wireframe domain-specific languages (DSLs) and extended Markdown
compilers (`PlantUML Salt`, `WireMD`, `Wire-DSL`), AI-generated
low-fidelity wireframe tools (`Balsamiq`), AI-generated multi-screen
clickable prototypes or frontend code (`Uizard Autodesigner`, `Figma
First Draft`, `Vercel v0`), and isolated component workshops
(`Storybook`) or HTML prototyping kits (`GOV.UK Prototype Kit`). All
findings below rest on summarised fetches of primary vendor
documentation and practitioner process literature. Deterministic DSLs
and isolated component workshops have near-zero, local regeneration cost
and preserve surrounding layout on edit, whereas AI prompt-to-prototype
tools require credit-metered inference and either conversational
re-prompting or manual canvas editing in a design tool (the visual
interface artifact held in a tool such as Figma or Uizard). Established
processes (`Shape Up`, `NN/g`, `GOV.UK`) place low-fidelity structural
previews with the definition (shaping or alpha exploration) and defer
high-fidelity visual design (the visual identity of a design system and
pixel-accurate interface design) and production code to the build stage.
The disconfirming queries showed an active practitioner push claiming
that AI-coded prototypes replace written specifications ("the prototype
is the specification") and that mature design systems reduce the need
for low-fidelity wireframes on incremental features, while practitioner
consensus still defends low-fidelity previews for novel structure to
prevent premature surface feedback. One unexpected finding reconfigures
part of the card's premise: `Shape Up` explicitly rejects wireframes in
the definition document altogether because even low-fidelity wireframes
are judged too concrete for the build team, using text-and-arrow
"breadboards" and "fat marker sketches" instead.

## Question

#### Card 10: From text to something visible
- **Question:** By which ways does a textual description become a
  visible preview before the product is built (languages that draw a
  wireframe from text, generated low-fidelity wireframes, generated
  clickable prototypes, a component library rendered in isolation): what
  does each need as input, what does it cost to change and make again,
  and at which stage do processes place the preview: with the definition
  or with the build?
- **Why it matters:** the author must see a proposal to tune it, and a
  change of the interface must not mean rebuilding the product.
- **What would answer it:** the tools' own documentation, and process
  literature on the fidelity of prototypes.
- **Where to look:** text-to-wireframe languages and diagram tools;
  tools that render components in isolation; AI prototype generators;
  practitioner organisations on prototype fidelity; processes that
  sketch before they build.
- **Disconfirming query:** "low-fidelity wireframes obsolete", "the
  prototype is the specification"; expected: a claim that generated
  prototypes make wireframes needless.
- **Stop rule:** nothing new from a differently worded query and every
  route has a primary source; ten to fifteen pages opened.

**Baseline to beat:** Before this card is answered, the frame holds only
the untested idea that an AI agent proposes a textual description of the
interface—where every screen element has a small Markdown definition and
a page definition names which elements it holds and where they stand—and
a human tunes the proposal and sees it without rebuilding the product. To
beat this baseline, the note must specify the concrete input grammar,
rendering mechanism, and edit/regeneration cost of each of the four
preview routes from primary tool documentation, and establish from
process literature whether visible previews belong in the pre-build
definition stage or the build stage (distinguishing throughout between
interface design in a design tool, technical design in a specification,
and the visual identity of a design system).

## Key findings

- **F1. Text-to-wireframe DSLs and extended Markdown compilers render
  deterministic static or HTML previews from structured plain text with
  sub-second local re-rendering.** [consensus — vendor report, rested on
  summarised fetches]
  Tools in this category require strict syntactic text as input rather
  than free-form prose. `PlantUML Salt` requires diagrams wrapped in
  `@startsalt` / `@endsalt` blocks using ASCII punctuation tokens: curly
  braces `{ ... }` for windows and grid groups (`{#` for full grid
  lines), pipes `|` for cell separators, `[Label]` for buttons, `[ ]` /
  `[X]` for checkboxes, `( )` / `(o)` for radio buttons, `^Label^` for
  droplists, `{/ Tab 1 | Tab 2 }` for tabs, and `{T` with `+` depth
  markers for trees [1]. `WireMD` accepts valid Markdown extended with
  inline ASCII component patterns—such as `[Submit]{.primary}` for
  buttons, `[Email___]{type:email required}` for inputs, `[[ Logo | Sign
  In ]]` for navigation bars, and `::: grid-3 card` container blocks—and
  compiles them via CLI (`wiremd wireframe.md --watch --serve 3000`) or
  a real-time VS Code split-preview extension into HTML, JSON AST, or
  React/Tailwind components across switchable themes (`sketch`, `clean`,
  `wireframe`, `tailwind`, `material`, `brutal`) [2]. `Wire-DSL` uses
  `.wire` block files declaring `project`, `style` tokens, `screen`,
  layout containers (`stack`, `grid`, `split`, `panel`, `card`), and
  atomic `component` definitions, compiled via `@wire-dsl/cli` (`wire
  render input.wire -o output.svg`) into SVG, PNG, or PDF [3]. Because
  compilation is deterministic and local, the cost to change and make
  again is editing the text lines in place and saving; untouched screens
  and components remain unchanged [1, 2, 3].

- **F2. AI low-fidelity wireframe generators accept natural-language
  prompts or rough sketches and output editable canvas wireframes so
  reviewers debate structure rather than visual identity.** [vendor
  claim — vendor report, rested on summarised fetches]
  `Balsamiq` takes natural-language text descriptions, rough sketches,
  or screenshots (or manual keyboard-driven "Quick Add" selection from a
  pre-built UI library) and generates intentionally sketchy, grayscale
  wireframes [4]. As `Balsamiq` documentation states: *"You get an
  editable, intentionally low-fi wireframe in seconds, so the team
  debates the idea, not the pixels."* [4] Here "pixels" means both the
  polished interface design in a design tool and the visual identity of
  a design system. Changing the preview via AI consumes paid AI
  generation credits or conversational modification commands, or requires
  manual manipulation of the generated canvas objects inside the tool
  [4].

- **F3. AI clickable prototype and generative UI tools translate short
  natural-language prompts into multi-screen linked canvases or live
  frontend code, but trade instant first drafts for non-deterministic
  regeneration or manual editing costs.** [emerging — vendor report,
  rested on summarised fetches]
  These tools follow two sub-routes. First, canvas-based AI generators
  produce designs of the interface held in a design tool: `Uizard
  Autodesigner` takes a target device selection (mobile, tablet,
  desktop), a style tag (including a `"Hand-drawn"` keyword for
  low-fidelity output), and a plain-English prompt capped at 300
  characters to generate multi-screen connected UI flows that are linked
  into clickable prototypes on a canvas [5]; `Figma First Draft` takes a
  text prompt inside Figma Design and generates editable wireframes or UI
  frames [6]. Second, code-based generative UI tools produce live
  rendered code: `Vercel v0` takes a natural-language prompt or image
  and generates interactive React/Next.js views styled with Tailwind CSS
  and `shadcn/ui` components [7]. Across both sub-routes (as of 2026),
  regenerating from a modified top-level prompt risks re-synthesising
  the layout, so iterative changes are made either through targeted
  follow-up chat prompts, visual property controls on the canvas, or
  exporting the code (`npx v0 add`) into a repository [5, 6, 7].

- **F4. Component workshops and HTML prototyping kits render real
  design-system components in isolation or in lightweight page templates,
  requiring executable code and an existing component library as input.**
  [consensus — vendor report and standard, rested on summarised fetches]
  `Storybook` renders production UI components in a sandboxed local
  server (`localhost:6006`) separate from application routing, backend
  APIs, and business logic [8]. Its input is a pre-built view-layer
  component (React, Vue, Angular, Svelte, Web Components) plus a
  declarative story file written in Component Story Format (CSF, standard
  JavaScript/TypeScript ESM exports) defining `args` and `argTypes` for
  each component state [9, 10]. Changing a preview in `Storybook` costs
  only hot-module reload in milliseconds when editing `args` in code or
  zero code edits when toggling properties in the interactive Controls
  addon panel [8, 9]. At the full-journey level, the `GOV.UK Prototype
  Kit` uses Node.js and HTML templates styled with the visual identity of
  the `GOV.UK Design System` to render realistic, clickable multi-page
  prototypes for user research without production backend engineering
  [11].

- **F5. UX research and product processes place low-fidelity structural
  previews in the definition stage to test information architecture and
  prevent surface-level bias, reserving high-fidelity interface design
  and production code for later validation or the build stage.**
  [consensus — practitioner claim, rested on summarised fetches]
  Kara Pernice of the Nielsen Norman Group (`NN/g`) defines a prototype
  as a testable hypothesis: *"A user interface prototype is a hypothesis
  — a candidate design solution that you consider for a specific design
  problem. The most straightforward way to test this hypothesis is to
  watch users work with it."* [12] `NN/g` and `UXPin` report that
  low-fidelity prototypes (sketches, static wireframes) and
  high-fidelity prototypes uncover similar structural and task-flow
  usability problems, while premature high-fidelity visuals bias
  stakeholders and users toward commenting on colors and fonts (the
  visual identity of a design system) or forgiving structural flaws
  because the interface looks finished [12, 13]. In the UK Government
  Service Manual, low-fidelity sketches and throwaway HTML prototypes
  (`GOV.UK Prototype Kit`) belong to the Discovery and Alpha definition
  phases to test multiple hypotheses before production building in Beta,
  and online prototypes must be password-protected and never used as
  production software [11]. In Basecamp's `Shape Up`, Ryan Singer places
  structural interface definition entirely in the pre-build "shaping"
  phase (corresponding to technical and solution design before tasks are
  handed to builders) and places visual UI design and implementation in
  the build cycle [14, 15].

- **F6. Disconfirming evidence shows a contested practitioner shift on
  two fronts: mature design systems often skip low-fidelity wireframes
  for routine work, and AI coding workflows increasingly treat a coded
  prototype as the specification itself.** [contested — practitioner
  claim, rested on summarised fetches]
  First, on whether low-fidelity wireframes are obsolete: practitioner
  synthesis (`UXPin`) notes that when teams work inside an established
  design system (pre-built visual identity and component kit), assembling
  medium-to-high-fidelity layouts from existing components is as fast as
  drawing gray boxes and avoids stakeholder difficulty in picturing
  abstract wireframes; however, this is contradicted for 0-to-1 products
  and novel information architecture by `NN/g`, `Balsamiq`, and `UXPin`
  itself, which maintain that low-fidelity wireframes remain necessary to
  prevent premature aesthetic debate and emotional attachment [4, 12,
  13]. Second, on whether "the prototype is the specification": a
  September 2026 engineering report from `Opera` (*Inside Opera's
  Evolving Design Loop*) states that with rapid AI-assisted prototyping,
  *"The working prototype is often the spec"* and *"The prototype is the
  spec now"*, replacing static Figma handoffs and long written specs
  with a working interactive prototype that engineers then harden for
  production [16]. This directly contradicts `Shape Up` [14, 15] and
  `GOV.UK` [11], which warn that handing a high-fidelity prototype to
  builders either over-constrains engineering judgement or risks
  mistaking throwaway prototype code for production-ready software.

| Preview route | Primary examples | Required input | Output fidelity & interactivity | Cost to change and make again | Process stage placement |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Text-to-wireframe DSLs & Markdown compilers** | `PlantUML Salt` [1], `WireMD` [2], `Wire-DSL` [3] | Structured ASCII DSL (`.wire`, `@startsalt`) or extended Markdown (`.md`) | Static SVG/PNG/PDF or multi-theme HTML mockup; low-to-medium fidelity | Near-zero: edit text lines in git; instant local CLI/IDE live preview; deterministic | Definition stage (versioned alongside text specs in git) [1, 2, 3] |
| **AI-generated low-fidelity wireframes** | `Balsamiq` [4] | Natural-language prompt, rough sketch, or UI library Quick Add | Sketchy grayscale canvas wireframe; low fidelity | AI credit consumption per prompt or manual canvas editing in tool | Early definition / ideation stage [4, 12] |
| **AI-generated clickable prototypes & UI code** | `Uizard Autodesigner` [5], `Figma First Draft` [6], `Vercel v0` [7] | Natural-language prompt (e.g., $\le 300$ chars in `Uizard`) + device/style tags | Multi-screen clickable canvas (`Uizard`, `Figma`) or live React/Tailwind/shadcn UI (`v0`); mid-to-high fidelity | Credit-metered chat re-prompting (risk of layout drift) or manual canvas/code edits | Contested: definition ideation [5, 6] vs "prototype is the spec" build handoff [7, 16] |
| **Component library in isolation / HTML kit** | `Storybook` [8, 9, 10], `GOV.UK Prototype Kit` [11] | Pre-built UI components + CSF `.stories` files (`Storybook`) or HTML/Node templates (`GOV.UK`) | Pixel-accurate design system visual identity; full component or multi-page HTML interactivity | Milliseconds (HMR / interactive Controls panel) once component code exists; high initial setup | Build stage (`Storybook` frontend workshop) [8] or Alpha definition testing (`GOV.UK`) [11] |

## Unexpected

**`Shape Up` rejects wireframes in the definition handoff altogether.**
The card assumes that turning a textual description into a visible
wireframe or clickable preview during the definition stage helps the
author tune the proposal before handing it to the build stage. Ryan
Singer's `Shape Up` (`Basecamp`) explicitly warns against putting
wireframes into the shaped definition (the "pitch") handed to builders,
arguing that wireframes specify too much visual interface design too
early and strip builders of room to solve layout problems [14, 15].
Instead, `Shape Up` restricts visual definition to two deliberately
abstract techniques: **breadboards** (borrowed from electrical
engineering, drawing only text names for *Places*, *Affordances*, and
*Connection lines* with zero spatial layout) and **fat marker sketches**
(2D layouts drawn with strokes so broad that adding detail or wireframe
precision is impossible) [14]. In Chapter 4 (*Find the Elements*),
Singer writes: *"Breadboarding would just miss the point because the 2D
arrangement of elements is the fundamental problem. In that case, we
still don't want to waste time on wireframes or unnecessary fidelity.
Instead we use fat marker sketches."* [14] And in Chapter 10 (*Hand Over
Responsibility*), Singer adds: *"Splitting the project into tasks up
front is like putting the pitch through a paper shredder."* [15] For a
spec-driven framework, this implies that a preview used by the author to
see and tune a screen definition may need a lower level of visual
commitment—or an explicit non-binding status—when handed to the build
stage.

## Not found

- **Controlled quantitative studies measuring the exact time or token
  cost of regenerating AI-generated prototypes versus editing text DSLs
  across multiple revision cycles:** Looked for in `nngroup.com`,
  `dl.acm.org` via general web queries, and vendor documentation
  (`uizard.io`, `help.figma.com`, `v0.app`). Vendor docs describe pricing
  mechanisms (credit consumption and character limits such as `Uizard`'s
  300-character prompt cap [5]) but publish no controlled benchmarks of
  multi-turn edit drift or rework time.
- **Native multi-platform preview rendering (native iOS/Android and
  desktop alongside web) from a single text-to-wireframe DSL:** Looked
  for in `plantuml.com`, `wiremd.dev`, and `wire-dsl.org`. While
  `Wire-DSL` and `Uizard` offer mobile/desktop viewport frames [3, 5],
  all surveyed text-to-wireframe compilers render to SVG, PNG, PDF, or
  web HTML/React [1, 2, 3], not to native mobile or desktop runtime
  views.

## Options

1. **Compile extended Markdown or a wireframe DSL directly into a
   deterministic low-fidelity HTML/SVG preview during the definition
   stage (`WireMD` / `Wire-DSL` / `PlantUML Salt` model).**
   - *Trade-offs:* Keeps the single source of truth in git-versioned
     Markdown or text (`WireMD`, `Wire-DSL`, `PlantUML Salt`) [1, 2, 3];
     regenerates locally in milliseconds with zero token cost and zero
     layout drift on unrelated elements; avoids premature debates over
     the visual identity of a design system [4, 12]; but shows static or
     basic HTML mockups rather than real design-system components or
     complex runtime state.
2. **Generate an interactive code or canvas prototype from the Markdown
   definition via an AI generator (`Vercel v0` / `Uizard` / `Opera`
   "prototype is the spec" model).**
   - *Trade-offs:* Produces high-fidelity, clickable multi-screen views
     or working React/Tailwind code immediately without a pre-existing
     component library [5, 7, 16]; makes stakeholder validation and
     animation/state review concrete [12, 16]; but introduces AI
     inference cost and non-deterministic layout changes on regeneration,
     splits the source of truth if the human edits the generated canvas
     or code directly, and biases reviewers toward surface styling over
     information architecture [12, 13].
3. **Render the textual page definition against an isolated component
   library (`Storybook` CSF / `GOV.UK Prototype Kit` model).**
   - *Trade-offs:* Previews the exact visual identity and interactive
     states of the production design system with instant hot-reload [8,
     9, 11]; eliminates visual drift between preview and build; but
     requires the component library and view-layer runtime to be built
     and maintained first, making it unavailable for greenfield (0-to-1)
     projects that have only Markdown specifications and no code yet [8,
     13].
4. **Two-tier preview pipeline: breadboard + deterministic text-to-wireframe
   DSL in the definition stage, optionally switching to isolated
   design-system component rendering once a project has a component
   library.**
   - *Trade-offs:* Combines `Shape Up` breadboarding/low-fi discipline
     [14] and deterministic Markdown-to-HTML previewing (`WireMD`) [2]
     during definition with `Storybook`-style component mapping [8, 10]
     for mature products; requires the textual description format to
     separate abstract element roles/layout from optional design-system
     component bindings.

## Relevance to this project

**Recommendation:** Base the framework's definition-stage preview on
**Option 1, extended toward Option 4**: the AI agent and human author
work in versioned Markdown definitions that compile deterministically
into a low-fidelity visual preview (following the `WireMD` and
`Wire-DSL` pattern of extended Markdown/DSL with switchable themes from
sketch/wireframe to clean HTML [2, 3]), paired with a `Shape Up`-style
breadboard view of places, affordances, and connections [14]. *(Agent
inference:)* Because the framework's core premise is a chain of
versioned Markdown documents kept in git where nothing is built yet, a
preview mechanism that depends on a pre-existing React codebase
(`Storybook` [8]) fails on greenfield projects, and an AI
prompt-to-canvas/code generator (`Uizard` [5], `v0` [7]) breaks git
text-diffing whenever a regeneration rewrites untouched screen regions or
a human edits the visual canvas directly. Deterministic compilation from
Markdown element and page definitions into HTML/SVG lets the author tune
a single element definition or page composition in text and see the
updated preview instantaneously in an IDE or browser (`--watch --serve`
[2]) without rebuilding the product or paying LLM token costs on every
tweak. When a project later enters or returns from the build stage with
an established component library, the same element definitions can map
to isolated component stories (`Storybook` CSF [10]) or a theme stylesheet
without changing the underlying Markdown structure.

**Consult when:**
- Designing the syntax of element and page Markdown definitions so they
  can be parsed deterministically into a visual preview.
- Deciding whether the preview shown to the human author during
  specification should be low-fidelity (wireframe/sketch theme) or
  high-fidelity (design-system theme).
- Defining the boundary of what the UI/UX Markdown specification hands to
  the build stage (mandatory structural elements and flows vs non-binding
  visual layout).

## Sources

1. **Salt (Wireframe)** — PlantUML team, undated (undated reference
   documentation), `https://plantuml.com/salt`; kind: tertiary
   (summarised fetch of primary vendor documentation); how read:
   summarised fetch; original.
2. **WireMD – Text-first UI Design Tool (Documentation & README)** —
   WireMD contributors (`wiremd.dev`), undated (undated project
   documentation, active 2025–2026), `https://wiremd.dev`; kind:
   tertiary (summarised fetch of primary vendor documentation); how
   read: summarised fetch; original.
3. **Wire-DSL Documentation** — Wire-DSL contributors (`wire-dsl.org`),
   undated (undated project documentation, active 2025–2026),
   `https://wire-dsl.org`; kind: tertiary (summarised fetch of primary
   vendor documentation); how read: summarised fetch; original.
4. **Balsamiq Documentation (Why Low-Fidelity Wireframes & AI
   Wireframing)** — Balsamiq Studios, LLC, undated (undated product
   documentation), `https://balsamiq.com`; kind: tertiary (summarised
   fetch of primary vendor documentation); how read: summarised fetch;
   original.
5. **Uizard Autodesigner & Help Center Documentation** — Uizard
   Technologies ApS, undated (undated product documentation),
   `https://uizard.io/autodesigner/`; kind: tertiary (summarised fetch
   of primary vendor documentation); how read: summarised fetch;
   original.
6. **Use First Draft with Figma AI** — Figma Help Center (`Figma`),
   undated (undated help center documentation),
   `https://help.figma.com`; kind: tertiary (summarised fetch of primary
   vendor documentation); how read: summarised fetch; original.
7. **v0 by Vercel (Generative UI Platform & Documentation)** — Vercel
   Inc., undated (undated product documentation), `https://v0.app`;
   kind: tertiary (summarised fetch of primary vendor documentation and
   secondary ecosystem summaries); how read: summarised fetch; original.
8. **Why Storybook? | Storybook docs** — Storybook maintainers
   (`storybook.js.org`), undated (undated official documentation),
   `https://storybook.js.org/docs/get-started/why-storybook`; kind:
   tertiary (summarised fetch of primary vendor documentation); how
   read: summarised fetch; original.
9. **What's a story? | Storybook docs** — Storybook maintainers
   (`storybook.js.org`), undated (undated official documentation),
   `https://storybook.js.org/docs/get-started/whats-a-story`; kind:
   tertiary (summarised fetch of primary vendor documentation); how
   read: summarised fetch; original.
10. **Component Story Format (CSF) | Storybook docs** — Storybook
    maintainers (`storybook.js.org`), undated (undated official
    documentation), `https://storybook.js.org/docs/api/csf`; kind:
    tertiary (summarised fetch of primary vendor documentation); how
    read: summarised fetch; original.
11. **GOV.UK Prototype Kit Documentation & Service Manual Prototyping
    Guidance** — Government Digital Service (UK Government), undated
    (undated official government manual and toolkit documentation),
    `https://prototype-kit.service.gov.uk`; kind: tertiary (summarised
    fetch of primary institutional documentation); how read: summarised
    fetch; original.
12. **UX Prototypes: Low Fidelity vs. High Fidelity** — Kara Pernice,
    Nielsen Norman Group (`NN/g`), 2016-12-18 (byline),
    `https://www.nngroup.com/articles/ux-prototype-hi-lo-fidelity/`;
    kind: tertiary (summarised fetch of primary practitioner research
    organisation article); how read: summarised fetch; original.
13. **What is the difference between low-fidelity and high-fidelity
    prototypes?** — UXPin Studio Blog, undated (undated practitioner
    guide),
    `https://www.uxpin.com/studio/blog/what-is-the-difference-between-low-fidelity-and-high-fidelity-prototypes/`;
    kind: tertiary (summarised fetch of secondary practitioner
    synthesis); how read: summarised fetch; original.
14. **Shape Up: Stop Running in Circles and Ship Work that Matters —
    Chapter 4: Find the Elements** — Ryan Singer (`Basecamp`), 2019
    (structured book publication date; page itself undated),
    `https://basecamp.com/shapeup/1.3-chapter-04`; kind: tertiary
    (summarised fetch of primary process book); how read: summarised
    fetch; original.
15. **Shape Up: Stop Running in Circles and Ship Work that Matters —
    Chapter 10: Hand Over Responsibility** — Ryan Singer (`Basecamp`),
    2019 (structured book publication date; page itself undated),
    `https://basecamp.com/shapeup/3.1-chapter-10`; kind: tertiary
    (summarised fetch of primary process book); how read: summarised
    fetch; original.
16. **Inside Opera's Evolving Design Loop** — Opera Mobile Blog
    (interviews with Oleksii, Alexander, Alex, and Ronan), 2026-09-18
    (byline),
    `https://blogs.opera.com/mobile/2026/09/inside-operas-evolving-design-loop/`;
    kind: tertiary (summarised fetch of primary practitioner engineering
    report); how read: summarised fetch; original.

## Opened and not used

None — all sixteen targeted sources opened via summarised fetch were
used and cited above; third-party listicles (`onelittleweb.com`,
`zapier.com`, `storyflow.so`, `wpmanageninja.com`) that appeared in
initial broad search summaries were not opened.

## Search record

**Queries run (in order):**
1. `text to wireframe DSL language diagram tool documentation` (broad
   discovery query)
2. `render UI components in isolation documentation Storybook` (broad
   discovery query)
3. `AI text to wireframe clickable prototype generator documentation`
   (broad discovery query)
4. `low fidelity vs high fidelity prototypes UX process Nielsen Norman Group Shape Up`
   (broad discovery query)
5. `"low-fidelity wireframes obsolete"` (disconfirming query 1)
6. `"the prototype is the specification"` (disconfirming query 2)
7. `domain:plantuml.com` — `"salt" PlantUML Salt wireframe documentation exact URL title syntax tree widgets`
   (targeted summarised fetch #1: `plantuml.com/salt`)
8. `domain:storybook.js.org` — `"Why Storybook" "What's a story" Component Story Format documentation exact URL title quotes`
   (targeted summarised fetch #2–#4: `storybook.js.org` docs pages)
9. `domain:nngroup.com` — `"UX Prototypes: Low Fidelity vs. High Fidelity" Kara Pernice exact URL date verbatim quotes`
   (targeted summarised fetch #5: `nngroup.com`)
10. `domain:basecamp.com` — `Shape Up Ryan Singer "Find the Elements" breadboarding "fat marker sketches" exact URL chapter quotes`
    (targeted summarised fetch #6: `basecamp.com/shapeup` Ch. 4)
11. `domain:help.figma.com` — `"First Draft" OR "Figma Make" AI text prompt wireframe prototype documentation exact URL date`
    (targeted summarised fetch #7: `help.figma.com`)
12. `domain:balsamiq.com` — `low-fidelity wireframes documentation why low-fidelity UI library quick add AI exact URL date quotes`
    (targeted summarised fetch #8: `balsamiq.com`)
13. `domain:wiremd.dev` — `WireMD markdown wireframe syntax documentation CLI VS Code live preview exact URL quotes`
    (targeted summarised fetch #9: `wiremd.dev`)
14. `domain:wire-dsl.org` — `Wire-DSL wireframe language documentation syntax CLI render exact URL quotes`
    (targeted summarised fetch #10: `wire-dsl.org`)
15. `domain:uizard.io` — `Autodesigner text prompt to clickable prototype wireframe documentation exact URL quotes`
    (targeted summarised fetch #11: `uizard.io/autodesigner/`)
16. `domain:gov.uk` — `"service-manual" prototyping alpha discovery low fidelity sketches HTML prototype kit exact URL date quotes`
    (targeted summarised fetch #12: `gov.uk` / `service.gov.uk`)
17. `domain:basecamp.com` — `"1.3-chapter-04" OR "2.2-chapter-07" OR "3.1-chapter-10" Shape Up Ryan Singer exact URL "No wireframes" "Hand Over Responsibility" quotes`
    (targeted summarised fetch #13: `basecamp.com/shapeup/3.1-chapter-10` URL verification)
18. `domain:uxpin.com` — `"low-fidelity" "high-fidelity" wireframes prototypes obsolete design systems exact URL title date quotes`
    (targeted summarised fetch #14: `uxpin.com`)
19. `domain:basecamp.com` — `"3.1-chapter-10" "Hand Over Responsibility" "No wireframes" "Assign projects, not tasks" Shape Up Ryan Singer verbatim quotes`
    (follow-up summarised fetch on source #13 for verbatim quotes)
20. `domain:service.gov.uk` — `"prototype-kit.service.gov.uk" "About the Prototype Kit" OR "making prototypes" exact URL quotes alpha beta`
    (follow-up summarised fetch on source #12: `prototype-kit.service.gov.uk`)
21. `domain:opera.com` — `"the prototype is the specification" OR "working prototype becomes the spec" exact URL title author date verbatim quotes`
    (targeted summarised fetch #15: `blogs.opera.com`)
22. `domain:v0.dev` — `v0 documentation prompt UI generation React Tailwind Shadcn iteration edit regenerate exact URL quotes`
    (targeted summarised fetch #16: `v0.app`)

**Pages opened:** 16 distinct pages (counting the 3 `storybook.js.org`
documentation pages and 2 `basecamp.com/shapeup` chapters across 14
targeted domain fetches; direct `curl` in the sandbox was blocked by a
permission deny rule, so all openings were performed as targeted
domain-scoped summarised fetches via `search_web`).

**What the disconfirming queries found:**
- `"low-fidelity wireframes obsolete"` found practitioner debate
  (`UXPin`, `Reddit r/UXDesign`, `Slickplan`) arguing that mature design
  systems, pre-built UI kits, and AI generators make low-fidelity
  wireframes unnecessary for incremental feature work, while confirming
  that practitioners still defend low-fidelity wireframes for 0-to-1
  products and novel information architecture to prevent aesthetic bias.
- `"the prototype is the specification"` found recent engineering and
  product literature (including `Opera`'s September 2026 engineering
  blog *Inside Opera's Evolving Design Loop*) arguing that AI coding and
  prototyping tools allow teams to skip static written specs and Figma
  handoffs by building a working interactive prototype that serves
  directly as the specification for production engineering.

**Reason the run ended:** Both parts of the card's stop rule were met at
the top of the 10–15 opening budget (14 targeted domain fetches covering
16 pages): every route named in the card had primary vendor or
institutional documentation, the disconfirming queries were run and
verified against specific sources, and differently worded queries ceased
to return new preview routes.
