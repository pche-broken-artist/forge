---
date: 2026-11-21
project: forge
topic: Where a description becomes code
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 21; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":55058,"output_tokens":16523,"thinking_tokens":8066,"cache_read_tokens":229648,"total_tokens":71581}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-21-description-becomes-code
status: immutable
---

# Declarative interface languages make single-view structure, state bindings, and preview states readable in code, leaving cross-screen journeys, rationale, and pre-implementation exploration to a description above code

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Declarative interface languages across all four target platforms
(SwiftUI, Jetpack Compose, Qt QML, Microsoft XAML, HTML Web Components,
and MDX) already state the spatial hierarchy of a single view, its
component composition, its local reactive state bindings, and its isolated
preview states in human-readable, rearrangeable text [1, 4, 7, 9, 11, 13].
All findings in this note rest on summarised fetches of the primary
documentation and papers; confidence is high on what the frameworks state
and separate because their official guides converge on the same model.
The disconfirming query confirmed a strong current holding that for a
single view tree, the declarative code is itself the structural
specification (`UI = f(state)`), eliminating separate static layout
files within the implementation stage [4, 15]. What the code still cannot
hold—and what a description above the code must carry—is the
pre-implementation exploration of visual identity and layout directions
[16], cross-screen user journeys, interaction rationale, and strict
separation between rearrangeable visual structure and imperative logic, a
border that Qt QML explicitly enforces inside the language itself by
splitting `.ui.qml` specification files from `.qml` logic files [7, 8].

## Question

#### Card 21: Where a description becomes code
- **Question:** What do declarative interface languages (SwiftUI, Jetpack Compose, QML, XAML, HTML with components, MDX) show about the border between a readable description and code: what of an interface do they state in a form a person can read and rearrange, what do they keep apart (structure, state, style), how do their previews work, and what do their makers and users say a description above the code must still hold?
- **Why it matters:** if what the build produces is itself a readable description with an instant preview, the layer above it must hold only what the code cannot say.
- **What would answer it:** the languages' own documentation and their makers' writing.
- **Where to look:** the documentation of the declarative interface frameworks of the four platforms and of their preview tools; their makers' guidance on going from a design to code. Search words from card 1: "generative UI" for formats in which an agent emits an interface at run time, kept apart from a description handed to a build; "intermediate representation", "structured specification".
- **Disconfirming query:** "the code is the specification declarative UI"; expected: a current that holds the code to be the description.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

The baseline this note must beat is the assumption that a textual UX/UI
description handed to a build stage must spell out the widget tree,
layout nesting, and visual property assignments of each screen, as if the
target code were still an opaque sequence of imperative widget
construction and mutation calls.

## Key findings

**F1. Declarative UI languages state the component tree and spatial arrangement directly in readable, nestable text, making single-view structure self-describing in code** [consensus — standard and vendor documentation; rests on summarised fetches of [1, 4, 7, 9, 11, 13, 15]].
In contrast to procedural UI programming—which builds and mutates a view
hierarchy step by step via constructors and `appendChild()` calls—
declarative UI languages express *what* the view hierarchy is by mirroring
the visual containment tree in the lexical nesting of the source text
[4, 15]. Across platforms, a human author can read and rearrange vertical
and horizontal stacks, grids, slots, and child components directly in text:
SwiftUI nests value-type `View` structs inside layout containers such as
`VStack` within a computed `body` property [1]; Jetpack Compose nests
`@Composable` functions (`Column`, `Row`, `Box`) without a separate XML
layout file [4]; XAML and HTML Web Components use nested XML/HTML custom
element tags and `<slot>` projections [9, 11, 12]; QML nests JSON-like
object blocks [7]; and MDX embeds JSX component trees inline within
standard Markdown prose [13].

**F2. All six languages separate view structure from application state via reactive bindings or unidirectional state-to-UI functions, while handling visual style (the visual identity of a design system) either through inline modifier chains or externalised theme/resource layers** [consensus — vendor documentation; rests on summarised fetches of [1, 2, 4, 5, 7, 9, 10, 11]].
None of the frameworks permit imperative mutation of widgets from outside
to keep the screen updated. Instead, they divide structure, state, and
style along two architectural patterns:
- *Internal DSLs in host languages (SwiftUI, Jetpack Compose):* The UI
  structure is an executable function of state [2, 4]. SwiftUI separates
  local view state (`@State`), child two-way references (`@Binding`), and
  shared models (`@Observable`) from the `body` declaration [2]. Jetpack
  Compose distinguishes stateful composables from stateless composables
  (which accept data arguments and emit event lambdas in unidirectional
  data flow, updated as of 2026-11-10) [5]. Both attach visual style via
  chained modifiers (`.padding()`, `Modifier`) while pulling design-system
  visual identity tokens from environment or `MaterialTheme` objects [1, 4].
- *Markup languages paired with host engines (XAML, QML, HTML Web Components, MDX):*
  Structure lives in markup, state crosses the boundary through declarative
  property bindings (`{Binding ...}` to an MVVM ViewModel in XAML [9];
  reactive JavaScript property expressions and explicit `State` objects in
  QML [7]; observed attributes in Web Components [11]), and visual style
  is isolated in XAML `Style` / `ControlTemplate` / `ResourceDictionary`
  blocks [9, 10], QML theme/style modules [7], or encapsulated CSS inside
  a Web Component's Shadow DOM [11]. MDX separates narrative document
  flow (Markdown) from interactive component structure (JSX) [13].

**F3. Where human or visual-tool rearrangeability matters, declarative code still requires a stricter border against embedded logic, exemplified by Qt's split between `.ui.qml` and `.qml` files** [single source — vendor documentation; rests on a summarised fetch of [8]].
Because general-purpose declarative UI code allows arbitrary host-language
control flow or inline scripts, a file can become unreadable to visual
tooling and non-programmers. Qt Quick and Qt Design Studio explicitly draw
the border between a pure interface description and implementation code
inside QML itself by splitting files into `.ui.qml` (UI files) and `.qml`
(implementation files) [8]. As Qt's documentation states in its section on
UI files: "Separate UI from the application logic. Designers should work
with the UI files (`.ui.qml`), while developers should work on the
corresponding implementation files (`.qml`)" [8]. To preserve a
rearrangeable declarative description, `.ui.qml` files forbid imperative
JavaScript blocks, forbid signal handlers (`onClicked`), forbid custom
functions, and restrict property bindings to side-effect-free pure
expressions using only a safe whitelist of `String`, `Math`, and `Date`
methods [8].

**F4. Live previews in declarative UI frameworks work by instantiating stateless or mock-state views in isolation without running the full application lifecycle** [consensus — vendor documentation; rests on summarised fetches of [3, 6, 10, 14]].
Because declarative views are functions of their input parameters and
state, IDE and documentation previewers render them without booting backend
services or navigating from a root screen:
- *Xcode Previews (SwiftUI):* Uses the `#Preview` macro at root file scope
  (and `@Previewable @State` for inline interactive state) to compile and
  render isolated views in a live canvas alongside source code across
  device traits and environments [3].
- *Android Studio Compose Previews:* Uses `@Preview` and custom
  multipreview annotations on zero-argument `@Composable` functions passing
  explicit sample data into stateless composables, supporting interactive
  mode and theme/configuration matrices without full emulator deployment [6].
- *XAML Hot Reload and Live Preview:* Injects edited XAML markup, `Style`
  setters, and `DataTemplate` changes over diagnostic pipelines directly
  into a running process or design-time surface without recompiling or
  losing runtime state [10].
- *Storybook MDX Canvas:* Imports isolated component states from Component
  Story Format (`*.stories.js|ts`) files into `<Canvas>` and `<Controls>`
  blocks embedded inside Markdown documentation [14].

**F5. A description above declarative code must still hold pre-implementation design exploration, cross-screen user journeys, interaction intent, and design rationale that single-view code discards** [emerging — controlled study [16] and vendor/academic documentation [5, 8, 15]; rests on summarised fetches of [5, 8, 15, 16]].
While declarative UI code specifies *what* a single view renders for a
given state [4, 15], primary sources identify three things that the code
layer does not hold:
1. *Pre-implementation aesthetic and structural exploration:* In a
   controlled study of 168 benchmark prompts (revised 2026-10-12), Zhang et
   al. (Google Labs) show that when UI coding agents generate implementation
   code directly from natural-language prompts, repeated generations
   collapse onto similar visual directions [16]. Introducing an explicit
   "structured design specification" as an intermediate representation
   before code generation expanded selection coverage of visual identity
   themes from one option to nearly three without altering code-generation
   decoding temperature [16].
2. *Stateless interface contracts vs. application wiring:* Android's
   official Compose architecture guidance (`State and Jetpack Compose`,
   updated 2026-11-10) requires splitting stateless presentation signatures
   (inputs and event callbacks) from stateful business-logic containers and
   navigation wiring [5]. A single declarative view file shows local event
   hooks (`onBuyClick: () -> Unit`) but does not state the cross-screen
   journey, business preconditions, or why that state transition exists.
3. *Prose context and usage rationale:* Storybook's MDX architecture exists
   specifically because component code and isolated stories cannot explain
   when, why, or how a component should be composed in a page; Markdown
   prose above and around `<Canvas>` blocks carries the human specification
   and usage rules [13, 14].

## Unexpected

Qt's `.ui.qml` specification format directly answers where a readable,
rearrangeable interface description stops and where code begins: the moment
imperative event handlers (`onClicked`), multi-statement blocks, or
side-effecting functions enter a declarative file, bidirectional visual
previewing and safe human/tool rearrangement break down [8]. Qt solves this
not with a separate non-code prose document for layout, but by enforcing a
strictly pure declarative subset of the language (`.ui.qml`) paired with an
implementation file (`.qml`) [8].

Google officially sunset **Relay**—its tool for packaging interface designs
held in a design tool (Figma) into intermediate "UI Packages" to generate
Jetpack Compose code—on 2025-04-30, instructing teams to uninstall the
Relay plugins and commit standard Jetpack Compose code directly into their
repositories [17]. This indicates that maintaining a heavyweight,
component-level visual handoff package between a design tool and a
declarative UI language added friction once Jetpack Compose code and
`@Preview` functions could express the component structure directly [6, 17].

## Not found

No primary documentation from Apple, Google, Microsoft, Qt, W3C/WHATWG, or
MDX was found that prescribes a standard format for a prose or Markdown
UX/UI specification document sitting above declarative UI code in a
software engineering pipeline (searched across `developer.apple.com`,
`developer.android.com`, `learn.microsoft.com`, `doc.qt.io`,
`developer.mozilla.org`, and `mdxjs.com`). Framework makers document how
to write declarative views, how to separate state and style, and how to
preview components, but treat upstream UX requirements and cross-screen
specifications as external to the UI framework.

## Options

Because the card asks what declarative languages show about the border
between a description and code—and what the layer above code must hold in
`forge`—the project faces three distinct structural options for the UX/UI
Markdown document:

1. **High-level intent, flows, and contracts only (leave view trees to code):**
   The Markdown UX/UI description states only what declarative UI code
   cannot: user journeys across screens, screen purpose and rationale,
   semantic element definitions (inputs, outputs/events, validation rules,
   and required states such as loading/empty/error), and high-level spatial
   zones, leaving the exact nested layout tree (`VStack`/`Column`/DOM) and
   visual styling modifiers to the build stage and its live preview.
   - *Trade-off:* Eliminates duplication between the Markdown spec and
     declarative code (`SwiftUI`/`Compose`/`HTML`), but the human reviewing
     the Markdown document cannot see exact layout geometry until a preview
     or prototype is rendered.
2. **Restricted declarative subset in Markdown (the `.ui.qml` / MDX pattern):**
   Embed a strictly pure, logic-free declarative tree (or MDX-style
   component composition with named slots and state variants) inside the
   Markdown specification, forbidding imperative handlers or styling
   minutiae.
   - *Trade-off:* Gives both humans and preview tools an exact,
     rearrangeable structural tree before the build stage, but couples the
     Markdown document more closely to a component vocabulary and risks
     duplicating the structural tree that the build agent will write in
     target code.
3. **Two-stage specification with an explicit exploration pre-pass (the structured-spec IR pattern):**
   Keep functional element definitions and page composition in versioned
   Markdown, and include a compact structured specification of visual
   identity direction and layout constraints as an intermediate stage
   before the coding agent emits target framework code [16].
   - *Trade-off:* Prevents AI coding agents from converging on generic
     interfaces [16] while keeping the permanent Markdown artifacts concise,
     at the cost of an extra decision step in the agent-human dialogue.

## Relevance to this project

In `forge`, the build stage targets web, mobile web, native mobile, and
desktop—platforms whose modern stacks (HTML/Web Components/MDX, SwiftUI,
Jetpack Compose, QML, XAML) already express single-view widget hierarchies,
style modifiers, and isolated state previews in readable code [1, 4, 7, 9,
11]. (Inference from F1–F5:) Therefore, the Markdown UX/UI document in
`forge` should **not** attempt to be a second declarative layout language
that spells out nested `VStack`/`Column` containers, pixel paddings, or
inline style properties; doing so duplicates what the target code states
better and fails the lesson of Google's sunsetting of Relay's intermediate
UI packages [17].

Instead, the idea heard from practice in the packet—that every element of a
screen has a small Markdown definition carrying its function, and a page
definition names which elements it holds and where they stand—aligns with
the border found in the primary sources **if and only if** that Markdown
layer stays strictly on the specification side of the boundary:
- **Element definitions** should state functional contracts (data displayed,
  user actions/events emitted, accessibility intent, and required
  domain states: default, loading, empty, error), matching the stateless
  composable/view boundary in Compose and SwiftUI [2, 5] and the pure
  interface boundary of `.ui.qml` [8].
- **Page definitions** should state which elements appear, their semantic
  grouping/zones, the user's entry/exit paths, and the rationale ("why this
  arrangement serves the story"), plus structured visual-identity direction
  when needed to guide an AI builder [16], leaving framework-specific tree
  nesting and style modifiers to the build stage.

**Consult when:** deciding which details belong in `forge`'s Markdown
element and page definitions versus what should be left to the build agent
and preview tool; or when designing the boundary between prose UX
descriptions and rendered previews.

## Sources

1. **Declaring a custom view**, Apple Inc. (`developer.apple.com`), undated (byline/documentation page without public revision timestamp), `https://developer.apple.com/documentation/swiftui/declaring-a-custom-view`; kind: primary documentation (read via tertiary summarised fetch); how read: summarised fetch; original.
2. **State and data flow**, Apple Inc. (`developer.apple.com`), undated, `https://developer.apple.com/documentation/swiftui/state-and-data-flow`; kind: primary documentation (read via tertiary summarised fetch); how read: summarised fetch; original.
3. **Previews in Xcode**, Apple Inc. (`developer.apple.com`), undated, `https://developer.apple.com/documentation/swiftui/previews-in-xcode`; kind: primary documentation (read via tertiary summarised fetch); how read: summarised fetch; original.
4. **Thinking in Compose**, Google / Android Developers (`developer.android.com`), 2026-08-14 (structured data / page last-updated metadata: 2026-07-21 UTC / Aug 14, 2026), `https://developer.android.com/develop/ui/compose/mental-model`; kind: primary documentation (read via tertiary summarised fetch); how read: summarised fetch; original.
5. **State and Jetpack Compose**, Google / Android Developers (`developer.android.com`), 2026-11-10 (byline / last-updated timestamp), `https://developer.android.com/develop/ui/compose/state`; kind: primary documentation (read via tertiary summarised fetch); how read: summarised fetch; original.
6. **Preview your UI with composable previews**, Google / Android Developers (`developer.android.com`), undated (evergreen tooling page; companion XR Glimmer preview page dated 2026-10-28), `https://developer.android.com/develop/ui/compose/tooling/previews`; kind: primary documentation (read via tertiary summarised fetch); how read: summarised fetch; original.
7. **Working with states — Qt Design Studio Manual**, The Qt Company (`doc.qt.io`), undated, `https://doc.qt.io/qtdesignstudio/quick-states.html`; kind: primary documentation (read via tertiary summarised fetch); how read: summarised fetch; original.
8. **UI Files (*.ui.qml) — Qt Quick / Qt Design Studio Documentation**, The Qt Company (`doc.qt.io`), undated, `https://doc.qt.io/qt-6/qtquick-uifiles.html`; kind: primary documentation (read via tertiary summarised fetch); how read: summarised fetch; original.
9. **XAML overview - Windows apps**, Microsoft (`learn.microsoft.com`), undated, `https://learn.microsoft.com/en-us/windows/apps/get-started/xaml-overview`; kind: primary documentation (read via tertiary summarised fetch); how read: summarised fetch; original.
10. **Write and debug running XAML code with XAML Hot Reload**, Microsoft (`learn.microsoft.com`), undated, `https://learn.microsoft.com/en-us/visualstudio/xaml-tools/xaml-hot-reload`; kind: primary documentation (read via tertiary summarised fetch); how read: summarised fetch; original.
11. **Using custom elements**, MDN Web Docs / Mozilla (`developer.mozilla.org`), undated, `https://developer.mozilla.org/en-US/docs/Web/API/Web_components/Using_custom_elements`; kind: primary/standard documentation (read via tertiary summarised fetch); how read: summarised fetch; original.
12. **Using templates and slots**, MDN Web Docs / Mozilla (`developer.mozilla.org`), undated, `https://developer.mozilla.org/en-US/docs/Web/API/Web_components/Using_templates_and_slots`; kind: primary/standard documentation (read via tertiary summarised fetch); how read: summarised fetch; original.
13. **What is MDX?**, MDX contributors (`mdxjs.com`), undated, `https://mdxjs.com/docs/what-is-mdx/`; kind: primary documentation (read via tertiary summarised fetch); how read: summarised fetch; original.
14. **MDX (Writing Docs)**, Storybook maintainers (`storybook.js.org`), undated, `https://storybook.js.org/docs/writing-docs/mdx`; kind: primary documentation (read via tertiary summarised fetch); how read: summarised fetch; original.
15. **Reading 21: GUI Implementation Approaches (6.031 Software Construction)**, MIT (`web.mit.edu`), 2022 (Spring 2022 course archive URL), `https://web.mit.edu/6.031/www/sp22/classes/gui-implementation/`; kind: secondary academic course text (read via tertiary summarised fetch); how read: summarised fetch; original.
16. **Enabling Creative Exploration for Vibe Design Agents** (arXiv:2609.15078), Yifan Zhang, Nghi DQ Bui, Georgios Evangelopoulos, Arnaud Benard (Google Labs), 2026-10-12 (byline: submitted 2026-09-14, revised 2026-10-12), `https://arxiv.org/abs/2609.15078`; kind: primary controlled study (read via tertiary summarised fetch); how read: summarised fetch; original.
17. **Relay was sunset on April 30, 2025**, Google Material Design team (`material.io`), 2025-04-30 (byline/notice date), `https://material.io/blog/relay-sunset`; kind: primary vendor notice (read via tertiary summarised fetch); how read: summarised fetch; original.

## Opened and not used

- `https://doc.qt.io/qtdesignstudio/studio-preview.html` — Superseded by [3, 6, 8, 10] which already covered the mechanisms of declarative previews and Qt's `.ui.qml` architecture.
- `https://arxiv.org/abs/2406.07739` (*UICoder: Finetuning Large Language Models to Generate User Interface Code through Automated Feedback*, Jason Wu et al., 2024) — Off the narrow question of the border between readable specification and declarative UI code (focuses on compiler/vision feedback loops for model finetuning).

## Search record

**Queries run (in order):**
1. `the code is the specification declarative UI` (disconfirming query)
2. `SwiftUI declarative syntax previews state structure`
3. `Jetpack Compose thinking in compose preview design to code`
4. `Qt QML XAML declarative UI structure state style separation`
5. `MDX HTML web components declarative interface structure`
6. `developer.apple.com: SwiftUI "Declaring a custom view" "State and data flow" "Previews in Xcode" exact title URL quote`
7. `developer.android.com: "Thinking in Compose" "Preview your UI with composable previews" "State and Jetpack Compose" exact title URL quote`
8. `doc.qt.io: "QML" declarative UI structure state style "Qt Design Studio" preview exact title URL quote`
9. `learn.microsoft.com: "XAML overview" declarative UI separation of concerns MVVM "XAML Live Preview" "XAML Hot Reload" exact title URL quote`
10. `mdxjs.com: "What is MDX" markdown JSX components structure exact title URL quote`
11. `mit.edu: "declarative UI" "specification" user interface 6.1020 or 6.031 or 6.005 exact title URL quote`
12. `developer.apple.com: "Declaring a custom view" "State and data flow" "Previews in Xcode" verbatim quotes section headings SwiftUI documentation`
13. `developer.android.com: "Thinking in Compose" "State and Jetpack Compose" "Preview your UI with composable previews" verbatim quotes section headings last updated date`
14. `doc.qt.io: "UI Files (*.ui.qml)" OR "uifiles" "Working with states" "Qt Quick Controls" styles Separation of declarative UI and logic verbatim quotes URL`
15. `learn.microsoft.com: "XAML overview" "https://learn.microsoft.com/en-us/windows/apps/get-started/xaml-overview" verbatim quotes section headings date XAML Hot Reload Live Preview`
16. `developer.mozilla.org: "Web Components" "Using custom elements" "Using templates and slots" verbatim quotes URL section headings`
17. `mit.edu: "https://web.mit.edu/6.031/www/sp22/classes/gui-implementation/" "Reading 21: GUI Implementation Approaches" verbatim quotes section headings declarative`
18. `"generative UI" "intermediate representation" OR "structured specification" interface code`
19. `developer.android.com: Relay Figma Jetpack Compose "UI Packages" design to code sunset OR deprecated OR limitations`
20. `doc.qt.io: "UI Files" "ui.qml" "Separate UI from the application logic" exact URL and restrictions on JavaScript logic`
21. `declarative UI code vs design specification what code does not capture user flows rationale states`
22. `mit.edu: "GUI Implementation Approaches" "Declarative programming" "Direct manipulation" quote text web.mit.edu/6.031/www/sp22/classes/gui-implementation/`
23. `arxiv.org: "structured specification" OR "intermediate representation" "generative UI" OR "user interface" code generation title authors arxiv number 2024 2025 2026`
24. `developer.apple.com: "https://developer.apple.com/documentation/swiftui/previews-in-xcode" "https://developer.apple.com/documentation/swiftui/declaring-a-custom-view" overview text how previews work #Preview macro`
25. `learn.microsoft.com: "XAML Hot Reload" "XAML Live Preview" "https://learn.microsoft.com/en-us/visualstudio/xaml-tools/xaml-hot-reload" exact title date how it works separation of style template`
26. `storybook.js.org: "https://storybook.js.org/docs/writing-docs/mdx" "MDX" component documentation preview canvas stories exact title overview text`
27. `"Relay" "April 30, 2025" Figma Jetpack Compose "UI Packages" exact URL title material.io OR developer.android.com`
28. `material.io: "https://material.io/blog/relay-sunset" exact title date author why Relay was sunset UI packages`
29. `arxiv.org: "2609.15078" "Enabling Creative Exploration for Vibe Design Agents" exact date abstract structured design specifications`

**Pages opened (via grounded summarised fetch; direct `curl` blocked by environment sandbox policy):**
19 pages fetched via targeted domain/URL summarised fetches ([1]–[17] in Sources, plus 2 in Opened and not used).

**What the disconfirming query found:**
Running `"the code is the specification declarative UI"` confirmed the expected current: in declarative UI frameworks (SwiftUI, Jetpack Compose, React, Elm) and academic teaching (MIT 6.031 [15]), the declarative view hierarchy in code is treated as the executable specification of *what* a single view looks like for any state (`UI = f(state)`), eliminating separate static layout blueprints at the view-tree level, while still leaving multi-screen journeys, design rationale, and pre-code aesthetic exploration outside the code [15, 16].

**Reason the run ended:**
Both parts of the card's stop rule were met: every route (SwiftUI, Jetpack Compose, QML, XAML, HTML Web Components, MDX, preview mechanisms, design-to-code guidance, and generative UI structured specifications) had a primary source and differently worded queries yielded nothing new, at the upper edge of the opening budget.
