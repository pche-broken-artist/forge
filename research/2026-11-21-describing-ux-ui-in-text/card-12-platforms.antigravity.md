---
date: 2026-11-21
project: forge
topic: Describing interfaces across web, mobile web, native mobile, and desktop platforms
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 12; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":68912,"output_tokens":22594,"thinking_tokens":10705,"cache_read_tokens":207636,"total_tokens":91506}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-12-platforms
status: immutable
---

# Describing interfaces across the web, the mobile web, native mobile, and the desktop

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Platform owners (Apple, Google, Microsoft, W3C) and multi-platform design
systems do not write a separate specification per platform; they write one
semantic description of a component or screen structure and attach platform
adaptations along two orthogonal axes: runtime capability traits (window size
classes, container width, pointer precision, hover availability, viewport
chrome) and host-OS conventions (navigation chrome, system back behaviour,
windowing, input shortcuts, and native control idioms). Across guidelines and
design systems, responsive and adaptive behaviour is specified using a finite
set of structural verbs (`Reposition`, `Resize`, `Reflow`, `Show/hide`,
`Replace`, `Re-architect`) over discrete size classes (`Compact`, `Medium`,
`Expanded`, `Large`, `Extra-large`) and three canonical multi-pane blueprints
(`List-Detail`, `Supporting Pane`, `Feed`). The disconfirming queries confirm
that forcing a single visual and behavioural UI across all platforms fails
when it overrides host-OS muscle memory, while wholly separate per-platform
designs fail by multiplying maintenance and fracturing product identity;
modern systems resolve this by keeping domain structure, content hierarchy,
and semantic design tokens unified while varying navigation scaffolding,
input density, and system chrome per platform. The one unexpected finding is
that all major native and web specifications now explicitly forbid branching
layout or input descriptions on platform or device labels ("mobile" vs
"desktop"), because desktop zoom (400% = 320 CSS px), tablet trackpads,
touchscreen laptops, and resizable mobile/tablet windowing mean every platform
can experience both compact/coarse-touch and expanded/fine-pointer states.

## Question

- **Card 12: The platforms**
- **Question:** What differs in describing an interface for the web, the
  mobile web, native mobile and the desktop: what do the platform guidelines
  prescribe (navigation, input, windows, the system's conventions), how is
  responsive and adaptive behaviour specified, and how do products and design
  systems on several platforms describe one thing: one abstract description
  with platform variants, or a description per platform?
- **Why it matters:** the targets are four platforms, and the unit and the
  layering of the description must carry them.
- **What would answer it:** the platform owners' guidelines and the
  documentation of design systems that span platforms.
- **Where to look:** the human interface guidelines of the mobile and desktop
  platforms; the adaptive-layout guidance of the large design systems; web
  standards on responsive design.
- **Disconfirming query:** "one design for all platforms fails", "platform
  conventions against cross-platform consistency"; expected: both camps exist.
- **Stop rule:** nothing new from a differently worded query and every route
  has a primary source; ten to fifteen pages opened.

**Terminology disambiguation ("design"):** In this note, "interface design"
refers to the structural and behavioural specification of the user interface
(what the project seeks to represent in versioned Markdown and what tools
like Figma hold visually); "technical design" refers to the architectural
artefact between requirements and implementation tasks in spec-driven kits;
and "design system" refers to the shared visual identity, token catalogue,
and reusable component library.

**Baseline to beat:** A naive text specification either writes one desktop-
or mobile-biased screen description and assumes a developer or coding agent
will "make it responsive", or duplicates every screen and component
definition four times for web, mobile web, native mobile, and desktop. This
note must identify the exact axes on which the four targets diverge, the
formal vocabulary used by standards and platform owners to specify adaptation,
and the layering architecture that avoids both under-specification and four-way
duplication.

## Key findings

*(Note on source access: direct shell/HTTP fetches were blocked by the
environment's permission rules, so all findings below rest on summarised
fetches of the cited upstream specifications and documentation via the web
search grounding tool.)*

- **F1. Platform guidelines diverge across four structural axes: navigation
  topology, input mechanics and target density, windowing and modal
  containment, and host-OS interaction conventions.** `[consensus — standards
  and platform guidelines, resting on summarised fetches]`
  - *Navigation:* Apple's Human Interface Guidelines (HIG) prescribe bottom
    tab bars, top navigation bars with a leading back chevron, and a left-edge
    swipe-to-pop gesture on iOS, with no persistent system-level back button;
    on iPadOS and macOS, HIG prescribes adapting flat hierarchies into leading
    sidebars (`NavigationSplitView`) and, on macOS, integrating global commands
    into the persistent system Menu Bar [1, 2, 13]. Android and Material Design
    3 (M3) rely on a unified system-wide back stack triggered by swiping from
    either the left or right screen edge, pair bottom navigation bars on
    compact screens with primary Floating Action Buttons (FABs), and swap to
    a leading vertical `Navigation Rail` or `Navigation Drawer` on wider
    windows [3, 5, 16]. Microsoft's Windows design guidelines prescribe
    `NavigationView` (adapting between `Left`, `LeftCompact` icon strip,
    `LeftMinimal` hamburger button, and `Top` modes), `BreadcrumbBar`, and
    `TabView` [7]. Web and mobile web sit inside browser chrome that supplies
    its own address bar, history stack, and deep-linkable URLs [9, 17].
  - *Input mechanics and target sizing:* Mobile touch guidelines require large
    coarse-pointer hit targets — at least `44 x 44 pt` in Apple HIG [2],
    `48 x 48 dp` in Android/M3 [3, 5], and `24 x 24 CSS px` as the mandatory
    Level AA floor in W3C WCAG 2.2 Success Criterion 2.5.8 (published December
    12, 2024) [12]. Desktop guidelines (macOS at a typical 1-to-3-foot viewing
    distance, Windows, and desktop web) assume fine pointers (`mouse` /
    `trackpad`), hover states, right-click context menus, keyboard focus rings,
    and tighter control density — such as `28 pt` standard push-button height
    on macOS [13] and Adobe Spectrum's `32 px` desktop `medium` base height
    versus `40 px` mobile `large` base height (a 1.25x scale shift) [14].
  - *Windows and modal surfaces:* Native iOS and compact Android default to a
    single full-screen container where secondary tasks slide up as bottom
    sheets or full-screen modals [2, 5, 13]. Desktop platforms (macOS, Windows)
    and tablet/desktop multitasking environments (iPadOS Stage Manager and
    Split View, Android free-form desktop windowing) operate in overlapping,
    user-resizable windows with customisable title bars and drag regions [1,
    3, 8, 13]; on macOS, sheets attach modal-to-window from the document title
    bar rather than sliding from the bottom of the screen [13].
  - *System conventions:* Flutter's platform adaptation audit documents OS-level
    micro-behaviours that users expect to remain native to the host OS: scroll
    physics and overscroll feedback (iOS dynamic friction and spring bounce vs
    Android higher static friction and overscroll indicator), route transitions
    (iOS horizontal parallax push vs Android vertical/zoom transition), picker
    haptics (light impact knock on iOS vs silent scroll on Android), and
    platform-specific text selection toolbars and keyboard cursor gestures [16].

- **F2. Responsive and adaptive behaviour is specified against discrete
  window size classes (breakpoints) and local container queries, never by
  device category or locked orientation.** `[consensus — standards and platform
  guidelines, resting on summarised fetches]`
  All three native platform owners (Apple, Google, Microsoft) and W3C web
  standards explicitly forbid hardcoding layouts to hardware categories (such
  as "phone" vs "tablet" vs "desktop") or locking screen orientation unless
  essential to the task (WCAG 2.2 SC 1.3.4 Level AA) [1, 3, 6, 12, 16].
  Instead, macro-layout adaptation is specified against discrete viewport
  width and height classes:
  - *Apple HIG:* Two trait size classes — `Compact` (constrained space) and
    `Regular` (expansive space) — evaluated independently across horizontal
    and vertical axes [1].
  - *Android and Material Design 3:* Three core width size classes in Android
    (`Compact` `< 600dp`, `Medium` `600–839dp`, `Expanded` `>= 840dp`) [3],
    extended in M3 Foundations into five width breakpoints by splitting out
    `Expanded` (`840–1199dp`), `Large` (`1200–1599dp`), and `Extra-large`
    (`>= 1600dp`) [5].
  - *Microsoft Windows:* Three width breakpoints in effective pixels (`epx`):
    `Small` (`<= 640px`), `Medium` (`641–1007px`), and `Large` (`>= 1008px`) [6].
  - *Web standards (W3C):* WCAG 2.2 SC 1.4.10 (`Reflow`, Level AA) requires
    vertical-scrolling interfaces to reflow without loss of information or
    functionality down to `320 CSS px` width (which equals a `1280 CSS px`
    desktop window at 400% browser zoom) [12]. For component-level adaptation
    independent of the global viewport, W3C CSS Containment Module Level 3
     defines `@container` queries (`container-type: inline-size`) so a child
    component adapts to the width of the pane holding it rather than the screen
    width [11].

- **F3. Layout transformation across size classes is specified through six
  structural operations and three canonical multi-pane blueprints.**
  `[consensus — platform guidelines, resting on summarised fetches]`
  Rather than describing unrelated screens per breakpoint, platform guidelines
  define how a single logical screen mutates as available space changes:
  - Microsoft's Windows responsive design specification defines six formal
    transformation techniques across breakpoints: `Reposition` (shift stacked
    elements into side-by-side columns), `Resize` (scale element dimensions
    and margins), `Reflow` (change item wrapping from a single column to a
    multi-column grid), `Show/hide` (condense secondary metadata or toolbars
    on `Small` viewports and reveal them on `Medium`/`Large`), `Replace` (swap
    one control for another, such as collapsing an open navigation pane into a
    compact icon strip or hamburger button), and `Re-architect` (split a
    sequential single-pane drill-down into concurrent multi-pane views) [6].
  - Android and Material Design 3 codify the `Re-architect`, `Show/hide`, and
    `Reflow` patterns into three reusable `Canonical layouts` composed of panes:
    `List-Detail` (one pane with sequential push navigation on `Compact`; two
    side-by-side panes on `Expanded`+), `Supporting Pane` (a primary workspace
    plus a secondary contextual inspector/comment pane that hides in a bottom
    sheet on `Compact` and docks as a side panel on `Expanded`+), and `Feed`
    (a single-column stream on `Compact` that reflows into multi-column card
    grids on wider size classes) [4, 5].

- **F4. Describing interfaces for the web and mobile web requires explicit
  rules for input capability queries, browser display modes, dynamic viewport
  chrome, and single-pointer gesture fallbacks.** `[consensus — W3C standards,
  resting on summarised fetches]`
  Unlike native mobile or desktop toolkits where the target OS implies a
  default window shell, web specifications must declare:
  - *Input capabilities independent of viewport width:* W3C Media Queries Level
    5 (Working Draft updated February 19, 2026) specifies `pointer` (`none |
    coarse | fine`), `hover` (`none | hover`), `any-pointer`, and `any-hover`
    to separate layout width from pointing precision and hover capability [9].
  - *Browser vs installed app shell:* W3C Media Queries Level 5 defines
    `display-mode` (`browser`, `standalone`, `minimal-ui`, `fullscreen`,
    `picture-in-picture`) to adapt UI navigation when a web app runs inside a
    mobile/desktop browser tab versus an installed standalone window [9].
  - *Dynamic mobile web viewport chrome:* W3C CSS Values and Units Module Level
    4 (Working Draft, March 12, 2024) defines `svh` (Small Viewport Height,
    assuming mobile browser address/navigation bars and virtual keyboards are
    expanded), `lvh` (Large Viewport Height, assuming browser chrome is
    retracted), and `dvh` (Dynamic Viewport Height) so fixed bottom bars and
    full-height screens are not clipped by mobile browser toolbars [10].
  - *Single-pointer fallbacks:* W3C WCAG 2.2 SC 2.5.1 (`Pointer Gestures`,
    Level A) requires that any multipoint gesture (pinch-to-zoom) or path-based
    gesture (swipe carousel, drag) also be operable with a single non-path
    pointer action (such as tap/click buttons) [12].

- **F5. Multi-platform design systems describe one abstract component with a
  platform-variant matrix or "Platform considerations" section, not separate
  component documents per platform.** `[consensus — practitioner and vendor
  documentation across 5 design systems, resting on summarised fetches]`
  Auditing how multi-platform design systems structure their documentation
  shows a single dominant pattern:
  - *Apple HIG* organises every component page (`Buttons`, `Menus`, `Sheets`,
    `Tab bars`, `Windows`) with one universal conceptual section (purpose,
    anatomy, general best practices) followed by a structured `Platform
    considerations` section with subsections for `iOS, iPadOS`, `macOS`,
    `tvOS`, `visionOS`, and `watchOS` that specify where a component changes
    density, presentation mode (e.g., bottom modal sheet on iOS vs title-bar
    document sheet on macOS), or transforms into another pattern (e.g., iOS
    bottom tab bar becoming a macOS/iPadOS sidebar) [13].
  - *Microsoft Fluent 2* (`fluent2.microsoft.design`) defines a component such
    as `Tablist` around a shared conceptual overview, semantic anatomy (`tablist`,
    `tab`, `tabpanel`), variants (orientation, appearance, overflow), and
    design tokens, and maps that single specification to platform-specific
    controls (`@fluentui/react-components` on Web, `TabView`/`NavigationView`
    in WinUI 3 on Windows, and native iOS/Android toolkits) [18].
  - *Adobe Spectrum* (`spectrum.adobe.com`), *IBM Carbon*
    (`carbondesignsystem.com`), and *Atlassian Design System*
    (`atlassian.design`) likewise maintain one component specification split
    into functional tabs (`Usage`, `Style`/Tokens, `Code`, `Accessibility`),
    handling platform differences through scale providers (`.spectrum--medium`
    for desktop pointer vs `.spectrum--large` for mobile touch) [14] and
    responsive wrapper rules rather than duplicating component definitions
    [19, 20].

- **F6. Multi-platform visual and spatial parameters are abstracted through
  tiered Design Tokens (W3C DTCG 2025.10) that compile one semantic name into
  platform-native units.** `[consensus — standard and practitioner tooling,
  resting on summarised fetches]`
  The W3C Design Tokens Community Group (DTCG) `Design Tokens Format Module
  2025.10` (published October 28, 2025) and transformation engines such as
  Style Dictionary v4 formalise a three-tier token hierarchy (global/primitive,
  alias/semantic, and component-specific tokens) in a single JSON format [15,
  20]. A component description references semantic tokens (for example,
  spacing, typography scale, or component height), and platform build targets
  resolve those tokens into CSS Custom Properties (`px`/`rem`) for Web, Swift
  (`pt`) for iOS/macOS, XML/Jetpack Compose (`dp`/`sp`) for Android, and
  effective pixels (`epx`) for Windows [14, 15].

- **F7. Disconfirming evidence confirms that pure "one design for all
  platforms" (visual and behavioural uniformity) fails usability standards,
  while pure per-platform divergence fractures brand and logic; practice
  settles on a layered split.** `[consensus — usability heuristics and
  framework guidelines, resting on summarised fetches]`
  Running the disconfirming queries (`one design for all platforms fails` and
  `platform conventions against cross-platform consistency`) confirms both
  camps and shows where the boundary is drawn:
  - *Why strict uniformity fails:* Jakob Nielsen's Usability Heuristic #4
    (`Consistency and Standards`) distinguishes internal consistency (within a
    product family) from external consistency (established platform conventions)
    [17]. When a cross-platform product overrides external OS conventions —
    such as placing an Android navigation drawer on iOS, breaking iOS edge-swipe
    or Android system back navigation, or shipping desktop-sized hit targets on
    touchscreens — users face cognitive friction because their ingrained OS
    muscle memory fails [16, 17]. Furthermore, Raluca Budiu's NN/g research on
    mobile web versus native apps shows that mobile web users expect browser
    conventions (links, scrolling, minimal chrome) and are penalised when a
    mobile site mimics heavy native-app chrome inside a browser viewport [17].
  - *How multi-platform products resolve the tension:* Both UX research [17]
    and cross-platform toolkits like Flutter [16] separate *product/domain
    consistency* (information architecture, terminology, workflows, brand
    tokens, and core content elements) from *platform-native adaptation* (app
    shell navigation, back mechanics, input density, scroll physics, and
    atomic OS controls such as switches, alerts, and pickers via `.adaptive()`
    variants).

## Unexpected

The card frames the target space as four discrete platforms ("the web, the
mobile web, native mobile and the desktop"), implying that a platform label
identifies the form factor and interaction mode. Primary sources across all
four ecosystems state that this assumption no longer holds [1, 3, 6, 9, 12,
16]:
- On native mobile and tablet OSes, iPadOS Stage Manager/Split View, Android
  multi-window and desktop windowing, and macOS running iPhone/iPad apps mean a
  "native mobile" app can be resized dynamically from a narrow compact pane to
  a wide desktop window with a hardware keyboard and trackpad attached [1, 3].
- On the desktop web, WCAG 2.2 Success Criterion 1.4.10 (`Reflow`) mandates
  that a `1280 CSS px` desktop viewport zoomed to 400% (`320 CSS px` effective
  width) must collapse into a single-column mobile-width layout without horizontal
  scrolling [12], and touchscreen laptops expose both `pointer: fine` and
  `any-pointer: coarse` simultaneously [9].
Consequently, modern specifications never bind layout structure or input
affordances directly to the platform name ("mobile" vs "desktop"); they bind
layout structure to *window/container size classes* and input affordances to
*pointer/hover capabilities*, while reserving the *platform* axis strictly for
host-OS conventions (system back stack, menu bar, window chrome, browser
viewport bars, and native control idioms) [1, 3, 9, 16].

## Not found

- **No formal standard for a declarative, human-authored Markdown specification
  of multi-platform UI screens:** While W3C DTCG 2025.10 standardises
  cross-platform *design tokens* in JSON [15] and W3C CSS/WCAG standardise
  responsive *implementation rules* [9, 10, 11, 12], no standard or primary
  design system documentation was found that defines a textual Markdown grammar
  for page-level and element-level multi-platform UI descriptions (searched
  across `w3.org`, `designtokens.org`, `m3.material.io`, `developer.apple.com`,
  `learn.microsoft.com`, and `fluent2.microsoft.design`).
- **No controlled quantitative study measuring developer or AI coding-agent
  build accuracy when handed a single abstract multi-platform UI specification
  versus separate per-platform specifications:** Searches across practitioner
  and design-system documentation returned architectural consensus and
  usability heuristics [16, 17], but no controlled experiment comparing single
  abstract vs per-platform text specifications for code generation.

## Options

Because the project targets four platforms (web, mobile web, native mobile,
desktop) and tests the idea of small Markdown definitions per element composed
into page definitions, the findings support three distinct ways to structure the
description:

1. **Option A: One platform-agnostic description + an application-level
   platform-mapping profile + optional `Platform considerations` overrides
   (Recommended).**
   - *How it works:*
     - **Element definitions** (e.g., a search field, a date picker, a primary
       action button) are written once in abstract, semantic terms: purpose,
       data/state contract, content rules, keyboard/pointer/gesture semantics
       (with single-pointer fallbacks per WCAG 2.5.1 [12]), and optional local
       `@container` adaptation rules [11]. An element only includes a `Platform
       considerations` block (following Apple HIG [13] and Flutter `.adaptive()`
       [16]) when its native control idiom genuinely diverges (e.g., modal
       sheet vs attached window sheet vs inline popover).
     - **Page definitions** name the elements they hold, group them into logical
       *panes* (`primary`, `detail`, `supporting`), and specify macro-layout
       adaptation across standard *window size classes* (`Compact`, `Medium`,
       `Expanded`/`Large` [3, 5]) using the canonical blueprints (`List-Detail`,
       `Supporting Pane`, `Feed` [4, 5]) and Microsoft's six transformation
       verbs (`Reposition`, `Resize`, `Reflow`, `Show/hide`, `Replace`,
       `Re-architect` [6]) — rather than branching on "web" vs "mobile" vs
       "desktop".
     - **An application-level platform profile** (one document per project, not
       repeated on every page or element) declares which target environments
       are in scope (Web, Mobile Web, iOS, Android, Windows, macOS) and maps
       abstract shell concepts to host conventions: how top-level navigation
       renders across size classes (`Bottom Bar` on Compact -> `Navigation Rail`
       on Medium -> `Sidebar`/`NavigationView` on Expanded + macOS `Menu Bar`
       [2, 5, 7]), how back/dismissal works, which scale/token sheet applies
       (`medium` fine-pointer vs `large` coarse-touch [14, 15]), and how mobile
       web dynamic viewport height (`svh`/`dvh` [10]) and `display-mode` [9]
       are handled.
   - *Trade-offs:* Eliminates 4x duplication across screens and elements;
     aligns directly with how Apple HIG, Material 3, Fluent 2, Spectrum, and
     W3C standards separate size classes and input capabilities from OS chrome;
     requires the author and agent to think in panes and size classes rather
     than fixed device screens.

2. **Option B: One abstract description with mandatory 4-column platform
   matrices on every page and element.**
   - *How it works:* Every element and page Markdown file stays a single file,
     but carries an explicit 4-row or 4-column table (`Web`, `Mobile Web`,
     `Native Mobile (iOS/Android)`, `Desktop (Windows/macOS)`) spelling out its
     layout, input, and container rules on each target.
   - *Trade-offs:* Makes platform differences immediately visible in every file
     without consulting an application-level profile; however, it conflates
     viewport size classes with OS conventions (forcing authors to repeat
     `Compact` layout rules under both "Mobile Web" and "Native Mobile", and
     failing when a desktop browser zooms to 400% or a tablet runs in split
     view [1, 3, 12]), and creates heavy boilerplate when 80–90% of domain
     elements behave identically once scale tokens are applied.

3. **Option C: Separate page and element descriptions per platform.**
   - *How it works:* Maintain separate folders or documents for Web, Mobile
     Web, iOS, Android, and Desktop, allowing each to be authored in its native
     vocabulary (`UIKit`/`SwiftUI`, `Compose`/M3, `WinUI`, HTML/CSS).
   - *Trade-offs:* Gives UX specialists complete freedom to tailor every screen
     to a specific OS without abstraction overhead; however, it violates the
     architecture of every multi-platform design system studied [13, 14, 18,
     19, 20], causes requirements and user-story drift across platforms whenever
     the interface changes, and quadruples the review burden for a solo
     developer or small team.

## Relevance to this project

**Recommendation:** Adopt **Option A** (one semantic description per element
and per page, parameterised by *panes*, *window size classes*, and *input
capabilities*, backed by a single application-level *platform convention
profile* and optional `Platform considerations` blocks).

**What this rests on and what it is chosen against:** This recommendation rests
directly on the convergence of Apple HIG [1, 13], Android/Material Design 3
[3, 4, 5], Microsoft Windows Design Guidelines [6, 7], W3C CSS/WCAG standards
[9, 10, 11, 12], W3C Design Tokens [15], and Adobe Spectrum [14]. All of these
sources separate (a) *spatial and input adaptation* (driven by `Compact` /
`Medium` / `Expanded` size classes, `@container` width, and `pointer` / `hover`
capabilities) from (b) *host-OS conventions* (navigation chrome, back stack,
window title bars, browser dynamic toolbars, and native picker/sheet idioms).
It is chosen against Option B (per-component 4-platform tables that conflate
screen size with OS type) and Option C (per-platform specifications that
multiply maintenance and drift).

**Agent's inferences (marked as inference):**
- *Inference 1 (testing the packet's element-and-page hypothesis):* The idea
  heard from practice — that every screen element has a small Markdown
  definition of its own and a page definition names which elements it holds and
  where they stand — holds up across all four platforms **only if** "where they
  stand" is expressed in terms of *panes* (`List-Detail`, `Supporting Pane`,
  `Feed`) and *transformation verbs* (`Reposition`, `Resize`, `Reflow`,
  `Show/hide`, `Replace`, `Re-architect`) across size classes, rather than
  fixed coordinates or a single platform's layout grid.
- *Inference 2 (what the proposing AI agent must ask):* When the AI agent
  proposes a UI description from requirements and user stories, it should not
  ask the human to design four separate platform screens; it should ask (1)
  which target platforms are in scope for the application profile, (2) which
  canonical pane pattern each page follows across `Compact` and `Expanded` size
  classes, and (3) whether any element requires a platform-specific override
  beyond standard scale tokens and native shell chrome.

**Consult when:**
- Designing the schema or template for page-level and element-level Markdown
  definitions in the UX/UI specification stage.
- Deciding how a single UI description handles web, mobile web, iOS, Android,
  and desktop targets without duplicating documents.
- Defining the vocabulary for responsive breakpoints, multi-pane layouts,
  navigation adaptation, or input/accessibility constraints in the specification
  framework.

## Sources

1. **Human Interface Guidelines: Layout** — Apple Inc.; undated (evergreen
   living documentation, accessed 2026-11-21);
   https://developer.apple.com/design/human-interface-guidelines/layout ;
   kind: tertiary (underlying primary platform guideline read via summarised
   fetch); how read: summarised fetch; original.
2. **Human Interface Guidelines: Designing for iOS** — Apple Inc.; undated
   (evergreen living documentation, accessed 2026-11-21);
   https://developer.apple.com/design/human-interface-guidelines/designing-for-ios ;
   kind: tertiary (underlying primary platform guideline read via summarised
   fetch); how read: summarised fetch; original.
3. **Use window size classes — Jetpack Compose Adaptive Layouts** — Android
   Developers (Google); undated (living documentation, accessed 2026-11-21);
   https://developer.android.com/develop/ui/compose/layouts/adaptive/use-window-size-classes ;
   kind: tertiary (underlying primary platform documentation read via
   summarised fetch); how read: summarised fetch; original.
4. **Canonical layouts — Large screens / Adaptive design** — Android Developers
   (Google); undated (living documentation, accessed 2026-11-21);
   https://developer.android.com/develop/ui/compose/layouts/adaptive/canonical-layouts ;
   kind: tertiary (underlying primary platform documentation read via
   summarised fetch); how read: summarised fetch; original.
5. **Material Design 3: Foundations — Layout (Understanding layout,
   Breakpoints / Window size classes, and Canonical layouts)** — Google;
   undated (living specification, accessed 2026-11-21);
   https://m3.material.io/foundations/layout/understanding-layout/overview ;
   kind: tertiary (underlying primary design system specification read via
   summarised fetch); how read: summarised fetch; original.
6. **Responsive design techniques for Windows apps (Layout overview)** —
   Microsoft Learn; undated (living documentation, accessed 2026-11-21);
   https://learn.microsoft.com/en-us/windows/apps/design/layout/responsive-design ;
   kind: tertiary (underlying primary platform documentation read via
   summarised fetch); how read: summarised fetch; original.
7. **Navigation design basics for Windows apps** — Microsoft Learn; undated
   (living documentation, accessed 2026-11-21);
   https://learn.microsoft.com/windows/apps/design/basics/navigation-basics ;
   kind: tertiary (underlying primary platform documentation read via
   summarised fetch); how read: summarised fetch; original.
8. **Title bar design for Windows apps** — Microsoft Learn; undated (living
   documentation, accessed 2026-11-21);
   https://learn.microsoft.com/windows/apps/design/layout/title-bar ;
   kind: tertiary (underlying primary platform documentation read via
   summarised fetch); how read: summarised fetch; original.
9. **Media Queries Level 5** — W3C (Editors: Dean Jackson, Florian Rivoal, Tab
   Atkins Jr., Daniel Libby, Luke Warlow); 2026-02-19 (dated by W3C document
   header / structured status, first Working Draft 2021-12-18);
   https://www.w3.org/TR/mediaqueries-5/ ;
   kind: tertiary (underlying primary W3C standard read via summarised fetch);
   how read: summarised fetch; original.
10. **CSS Values and Units Module Level 4** — W3C (Editors: Tab Atkins Jr.,
    Elika J. Etemad / fantasai); 2024-03-12 (dated by W3C Working Draft header);
    https://www.w3.org/TR/css-values-4/ ;
    kind: tertiary (underlying primary W3C standard read via summarised fetch);
    how read: summarised fetch; original.
11. **CSS Containment Module Level 3** — W3C (Editors: Tab Atkins Jr., Florian
    Rivoal, Miriam E. Suzanne); 2022-08-18 (dated by W3C Working Draft header);
    https://www.w3.org/TR/css-contain-3/ ;
    kind: tertiary (underlying primary W3C standard read via summarised fetch);
    how read: summarised fetch; original.
12. **Web Content Accessibility Guidelines (WCAG) 2.2** — W3C; 2024-12-12
    (dated by W3C Recommendation header);
    https://www.w3.org/TR/WCAG22/ ;
    kind: tertiary (underlying primary W3C Recommendation read via summarised
    fetch); how read: summarised fetch; original.
13. **Human Interface Guidelines: Platforms (and Designing for macOS /
    iPadOS)** — Apple Inc.; undated (evergreen living documentation, accessed
    2026-11-21);
    https://developer.apple.com/design/human-interface-guidelines/platforms ;
    kind: tertiary (underlying primary platform guideline read via summarised
    fetch); how read: summarised fetch; original.
14. **Adobe Spectrum: Theming and Design Tokens (Platform Scale)** — Adobe
    Inc.; undated (living design system documentation, accessed 2026-11-21);
    https://spectrum.adobe.com/page/theming/ ;
    kind: tertiary (underlying primary design system documentation read via
    summarised fetch); how read: summarised fetch; original.
15. **Design Tokens Format Module 2025.10** — W3C Design Tokens Community Group
    (DTCG); 2025-10-28 (dated by W3C Final Community Group Report header);
    https://www.designtokens.org/TR/2025.10/format/ ;
    kind: tertiary (underlying primary specification read via summarised
    fetch); how read: summarised fetch; original.
16. **Automatic platform adaptations (and Adaptive and responsive design in
    Flutter)** — Flutter Documentation (Google); undated (living framework
    documentation, accessed 2026-11-21);
    https://docs.flutter.dev/ui/adaptive-designs/platform-adaptations ;
    kind: tertiary (underlying primary framework documentation read via
    summarised fetch); how read: summarised fetch; original.
17. **Usability Heuristic 4: Consistency and Standards (and Mobile: Native
    Apps, Web Apps, and Hybrid Apps)** — Jakob Nielsen and Raluca Budiu,
    Nielsen Norman Group (NN/g); 2016-01-19 / 2023-01-12 (dated by byline);
    https://www.nngroup.com/articles/consistency-standards/ ;
    kind: tertiary (underlying secondary/practitioner research synthesis read
    via summarised fetch); how read: summarised fetch; original.
18. **Fluent 2 Design System — Components (Tablist)** — Microsoft; undated
    (living design system documentation, accessed 2026-11-21);
    https://fluent2.microsoft.design/components/web/react/core/tablist/usage ;
    kind: tertiary (underlying primary design system documentation read via
    summarised fetch); how read: summarised fetch; original.
19. **Carbon Design System — Component Documentation Structure** — IBM; undated
    (living design system documentation, accessed 2026-11-21);
    https://carbondesignsystem.com/components/tile/usage/ ;
    kind: tertiary (underlying primary design system documentation read via
    summarised fetch); how read: summarised fetch; original.
20. **Atlassian Design System — Foundations and Components** — Atlassian;
    undated (living design system documentation, accessed 2026-11-21);
    https://atlassian.design/ ;
    kind: tertiary (underlying primary design system documentation read via
    summarised fetch); how read: summarised fetch; original.

## Opened and not used

- **UXPin blog articles on Apple HIG vs Material Design and cross-platform
  consistency** — returned in broad search summaries; left out as secondary
  vendor blog write-ups superseded by the upstream primary guidelines [1, 2, 3,
  5].
- **Medium / third-party blog summaries on M3 canonical layouts and size
  classes** — returned in broad search summaries; left out as copies/secondary
  re-statements superseded by Android Developers [3, 4] and Material Design 3
  [5].
- **Adalo, Nilebits, Gluestack, and BolderApps blog posts on cross-platform
  consistency** — returned in disconfirming search summaries; left out as
  vendor/agency marketing blogs below the primary-source bar and superseded by
  Flutter [16] and NN/g [17].

## Search record

- **Queries run (in order):**
  1. `human interface guidelines platform differences navigation input windows`
     (broad query)
  2. `adaptive layout responsive design specification breakpoints canonical layouts`
     (broad query)
  3. `multi-platform design system component documentation web mobile desktop variants`
     (broad query)
  4. `one design for all platforms fails` (disconfirming query 1)
  5. `platform conventions against cross-platform consistency` (disconfirming
     query 2)
  6. `domain:developer.apple.com` — `"Human Interface Guidelines" "Platforms" OR "Layout" "Designing for iOS" "Designing for macOS" "Designing for iPadOS" exact URL quotes`
  7. `domain:developer.android.com` — `"Window size classes" "Canonical layouts" adaptive layout navigation rail bottom bar pointer input exact URL quotes`
  8. `domain:m3.material.io` — `"Applying layout" OR "Canonical layouts" OR "Window size classes" Material Design 3 adaptive navigation exact URL quotes`
  9. `domain:w3.org` — `"Media Queries Level 5" OR "CSS Containment Module Level 3" pointer hover container queries responsive exact URL date quotes`
  10. `domain:learn.microsoft.com` — `"Windows app" design guidelines navigation basics Fluent responsive layout inputs windowing exact URL date quotes`
  11. `domain:developer.apple.com` — `"size classes" "compact" "regular" "Designing for iOS" "Designing for iPadOS" "Designing for macOS" viewing distance pointer touch navigation`
  12. `domain:learn.microsoft.com` — `"Responsive design techniques" "Reposition" "Resize" "Reflow" "Show/hide" "Replace" "Re-architect" 640 1007 windows apps design layout`
  13. `domain:w3.org` — `"Media Queries Level 5" "pointer" "hover" "display-mode" AND "CSS Values and Units Module Level 4" "dvh" "svh" "lvh" AND "CSS Containment Module Level 3" "@container"`
  14. `domain:fluent2.microsoft.design` — `components web iOS Android Windows macOS documentation tabs variants tokens anatomy`
  15. `domain:carbondesignsystem.com` — `component documentation usage style code accessibility responsive variants platform`
  16. `domain:nngroup.com` — `"mobile web" "native app" OR "cross-platform" consistency platform conventions responsive design`
  17. `domain:w3.org` — `What are the publication dates, editors, and definitions of pointer, hover, any-pointer, and display-mode in W3C Media Queries Level 5, dvh svh lvh in CSS Values and Units Module Level 4, and container queries in CSS Containment Module Level 3?`
  18. `domain:w3.org` — `What does WCAG 2.2 (W3C Recommendation date and URL) specify for Reflow 1.4.10, Orientation 1.3.4, Target Size Minimum 2.5.8, and Pointer Gestures 2.5.1 across mobile and desktop?`
  19. `domain:m3.material.io` — `How does Material Design 3 specify window size classes (compact, medium, expanded, large, extra-large), canonical layouts (list-detail, supporting pane, feed), and adaptive navigation in Foundations Layout?`
  20. `domain:atlassian.design` — `How does Atlassian Design System document components and foundations across web and mobile platforms, and what is its URL and structure?`
  21. `domain:nngroup.com` — `Nielsen Norman Group articles by Jakob Nielsen or Raluca Budiu on Mobile Web vs Native App, responsive web design, and cross-platform consistency vs platform conventions with author, date, and URL`
  22. `domain:developer.apple.com` — `How does Apple Human Interface Guidelines structure component pages (such as Buttons, Menus, Sheets, Tab bars, Windows) with "Platform considerations" for iOS, iPadOS, and macOS?`
  23. `domain:spectrum.adobe.com` — `How does Adobe Spectrum document platform scale (desktop medium pointer vs mobile large touch 1.25x) and multi-platform component specifications? Exact URLs and details`
  24. `domain:docs.flutter.dev` — `What does Flutter's "Automatic platform adaptations" and "Adaptive and responsive design" documentation prescribe for iOS vs Android vs Web vs Desktop conventions? Exact URLs and details`
  25. `"Design Tokens Format Module" W3C "designtokens.org" AND "Style Dictionary" multi-platform iOS Android Web Desktop token transformation exact URL date`
- **Pages opened (via domain-targeted summarised fetches):** 15 primary/upstream
  documentation sets and standards opened via summarised fetch (Apple HIG
  Layout/iOS/Platforms, Android Window Size Classes/Canonical Layouts, Material
  Design 3 Layout, Microsoft Learn Responsive Design/Navigation/Title Bar, W3C
  Media Queries 5, W3C CSS Values 4, W3C CSS Containment 3, W3C WCAG 2.2, W3C
  DTCG 2025.10, Adobe Spectrum, Flutter Platform Adaptations, Fluent 2, Carbon,
  Atlassian Design System, and NN/g); direct `curl.exe` HTTP opening in the
  shell was denied by the environment's permission rules.
- **What the disconfirming queries found:** Both queries (`one design for all
  platforms fails` and `platform conventions against cross-platform
  consistency`) confirmed the expected split: forcing a single platform's UI
  idioms across all OSes fails usability when it violates host-OS conventions
  (back navigation, gesture physics, input density, native pickers/dialogs),
  while full per-platform divergence fractures brand identity and multiplies
  specification overhead; modern teams and frameworks resolve the conflict by
  keeping brand tokens, domain logic, and content structure consistent while
  adapting navigation shells, input density, and OS-level mechanics to the host
  platform.
- **Why the run ended:** Both parts of the card's stop rule were met — every
  route (mobile/desktop HIGs, adaptive-layout guidance of large design systems,
  web standards on responsive design, and the disconfirming route) had
  upstream primary sources, differently worded queries yielded no new structural
  patterns, and the budget of fifteen primary domain openings was reached.
