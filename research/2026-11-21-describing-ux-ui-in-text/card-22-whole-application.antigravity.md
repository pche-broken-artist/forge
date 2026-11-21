---
date: 2026-11-21
project: forge
topic: What belongs to the whole application
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 22; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":50972,"output_tokens":20587,"thinking_tokens":10031,"cache_read_tokens":184253,"total_tokens":71559}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-22-whole-application
status: immutable
---

# Behaviour that belongs to the whole application rather than any single screen or linear path

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Across web standards, formal user-interface modeling languages, native
platform guidelines, and UX specification practice, six classes of
behaviour belong to the application as a whole rather than to any single
screen or linear user path: (1) the persistent navigation frame or
application shell, (2) address routing, navigation scope, and deep-link
back-stack synthesis, (3) multi-window and multi-pane spatial topology,
(4) asynchronous external events and system notifications, (5) network
interception, offline caching, and global degraded states, and (6)
context-of-use rules governing role and permission adaptation. Throughout
this note, the three senses of "design" are kept separate: *interface
design* (the layout and interaction artifact held in a UI tool or text
description), *technical design* (the architectural specification between
requirements and implementation tasks), and *design system identity* (the
shared visual tokens and component library). Platform standards and
modeling specifications converge on a hybrid placement rule: invariants of
the application shell, routing scope, window taxonomy, notification
channels, offline fallback policies, and role matrices are declared once
at the application level, whereas each screen or container declares only
its local parameter bindings, synthetic parent hierarchy, and local state
overrides. The disconfirming query found no standard or practitioner
source arguing that per-screen specifications alone suffice without an
application-level rules section; sources note only that teams sometimes
skip global rules in small prototypes at the cost of inconsistency and
rework. One unexpected finding reconfigures the boundary between "screen"
and "application": modern adaptive layout standards treat what appears to
be a two-screen transition on a compact viewport (list to detail) as a
single multi-pane container on an expanded viewport, meaning screen
boundaries themselves are a function of the application's window-size
state. All findings in this note rest on summarised fetches of the cited
sources.

## Question

- **Question:** Which behaviour of an application lies outside any single
  screen and any linear path (addresses and deep links, the persistent
  frame of navigation, several windows or tabs and their state,
  notifications and events that arrive unasked, offline and degraded
  states, one view differing by role and permission), how do platform
  guidelines and specification practice describe it, and where is it kept
  in a description: once for the application, or again on every screen?
- **Why it matters:** a description built only from screens, elements and
  paths has no place for it, and every candidate shape must say where it
  lives.
- **What would answer it:** the platform owners' guidelines and the web's
  standards on behaviour at the level of the application.
- **Where to look:** platform guidelines on navigation, deep links,
  notifications, windows and offline behaviour; web standards and guidance
  on routing and on working offline; specification templates that carry a
  section for the rules of the whole application. Search words from card
  1: "design specs", "wireframe annotations", "prototype specifications",
  "wireflows", "state matrix"; and the model-based words "abstract user
  interface", "concrete user interface", IFML's "view container", "view
  component", "interaction flow".
- **Disconfirming query:** "per-screen specification is enough", "global
  UI rules section unnecessary"; expected: nothing argues that it needs no
  place.
- **Stop rule:** nothing new from a differently worded query and every
  route has a primary source; ten to fifteen pages opened.

**Baseline to beat:** A naive textual UI description lists screens, the
components inside each screen, and step-by-step user flows between
screens, either omitting whole-application behaviour altogether or
repeating shell navigation, deep-link entry rules, offline banners, and
role-permission checks in the annotations of every single screen. To beat
that baseline, this note must identify the exact primitives used by formal
standards (OMG IFML, W3C, WHATWG) and platform guidelines (Android, Apple
HIG, Chrome Workbox) to separate application-level structure from
screen-level content, and state the division of responsibility between a
single application-wide specification and per-screen definitions.

## Key findings

- **F1. Formal UI modeling languages and web architectures separate the
  persistent navigation frame ("application shell" or top-level
  `ViewContainer`) from screen content and declare it once at the root of
  the interface design** [consensus — standards and vendor documentation;
  rests on summarised fetches]. In the Object Management Group's (OMG)
  *Interaction Flow Modeling Language (IFML)* 1.0 standard, the user
  interface is structured as a hierarchy of `ViewContainer` elements;
  top-level containers marked with the boolean property `isLandmark`
  are globally reachable from anywhere within the enclosing container
  without explicit point-to-point `InteractionFlow` arrows from every
  screen, while mutually exclusive child screens are grouped inside an XOR
  `ViewContainer` (`isXOR`) with one child marked `isDefault` [1]. On the
  web, Google's Chrome for Developers documentation on the *Application
  shell model* defines the equivalent technical-design and
  interface-design construct in its opening section: "In practice, this
  tends to be the header, navigation, and other common user interface
  elements that persist across all pages. When a service worker precaches
  this minimal UI's HTML and dependent assets, we call this the
  application shell" [6]. Both Android's `NavigationSuiteScaffold` [10]
  and Apple's Human Interface Guidelines (HIG) for *Sidebars* [13] specify
  that this persistent navigation frame mutates its concrete presentation
  by viewport size—switching automatically between a bottom navigation bar
  (or tab bar), a vertical navigation rail, and a full sidebar or drawer—
  without changing the underlying destination hierarchy [10, 13].

- **F2. Application entry points, navigation boundaries, and deep-link
  back-stack synthesis are governed by an application-level routing graph
  coupled with per-destination URI patterns and parent declarations**
  [consensus — standards and platform guidelines; rests on summarised
  fetches]. In the W3C *Web Application Manifest* specification (Working
  Draft, 2026-10-13), the application's entry address and navigation
  boundary are declared once for the whole application via `start_url` and
  `scope`: "The manifest's `scope` member is a string that represents the
  navigation scope of this web application's application context" (§
  `scope` member), and `start_url` "represents the start URL, which is URL
  that the developer would prefer the user agent load when the user
  launches the web application" (§ `start_url` member) [3]. Within a web
  application, the WHATWG *HTML Living Standard* (*Navigation and session
  history APIs*) centralizes address interception and session history state
  on a per-navigable `Window.navigation` object (`navigate` event), outside
  any individual DOM view [5]. In native mobile guidelines, Android's
  *Principles of navigation* (updated 2026-02-26) mandates a single "fixed
  start destination" for the application and establishes the rule that
  "Deep linking simulates manual navigation" [7]: when an external URI or
  Android App Link opens a deep destination directly, the navigation host
  synthesizes a realistic back stack from the navigation graph's parent
  hierarchy back to the root start destination so that pressing Back steps
  up the hierarchy rather than exiting the app [7, 8]. Thus, the routing
  mechanics and start destination live at the application level, while
  individual destinations carry their URI pattern, required parameters, and
  hierarchical parent [7, 8].

- **F3. Multi-window, multi-tab, and adaptive multi-pane behaviours belong
  above the screen level because a "screen" can either split into co-active
  panes inside one window or spawn auxiliary windows with restricted
  navigation** [consensus — platform guidelines and standards; rests on
  summarised fetches]. Apple's HIG for *Windows* defines a two-tier
  application window taxonomy in its opening section: "Conceptually, apps
  use two types of windows to display content: A primary window presents
  the main navigation and content of an app, and actions associated with
  them. An auxiliary window presents a specific task or area in an app.
  Dedicated to one experience, an auxiliary window doesn't allow
  navigation to other app areas, and it typically includes a button people
  use to close it after completing the task" [11]. On the web, the W3C
  *Web Application Manifest* defines the top-level window chrome via the
  application-wide `display` mode (`fullscreen`, `standalone`,
  `minimal-ui`, `browser`) [3]. Furthermore, Android's *Canonical layouts*
  guide (updated 2026-09-01) specifies that `ListDetailPaneScaffold` and
  `SupportingPaneScaffold` dynamically merge two separate compact-screen
  views into co-existing side-by-side panes within a single expanded
  window [9], corresponding to IFML's non-XOR (simultaneously active) peer
  `ViewContainer` composition [1].

- **F4. Notifications and unasked background events originate outside any
  active screen context and require an application-level event receiver, an
  interruption classification, and a deep-link target contract** [consensus
  — standards and platform guidelines; rests on summarised fetches]. The
  W3C *Service Workers* specification (Candidate Recommendation Draft,
  2026-09-17) explains in its Abstract why unasked events cannot belong to
  a screen: "To react to a push message, or completion of a persistent
  download, the context that originally registered interest may no longer
  exist. In these cases, the service worker is the ideal event
  destination" [4]. In formal UI modeling, IFML represents these via
  `CatchingEvent` and `SystemEvent` elements that trigger an
  `InteractionFlow` or `Action` independently of user-initiated
  `ViewElementEvent` triggers [1]. In interface design guidelines, Apple's
  HIG for *Notifications* defines a notification as providing "timely,
  high-value information they can understand at a glance" [12], categorizes
  delivery by system interruption levels (*Passive*, *Active*,
  *Time-Sensitive*, *Critical*), supports inline background actions that
  mutate state without foregrounding a window, and requires tapping a
  notification to route directly to the relevant window and view context
  rather than a generic launch screen [11, 12].

- **F5. Offline operation and network degradation are governed by an
  application-wide interception layer paired with a cross-screen UI state
  matrix** [consensus — standards, vendor documentation, and practitioner
  guidelines; rests on summarised fetches]. At the technical-design level,
  W3C *Service Workers* intercept HTTP requests via the functional `fetch`
  event (`FetchEvent`), returning cached `Response` objects when the
  network is unreachable [4], while the Workbox *Application shell model*
  ensures the persistent shell renders offline even when dynamic screen
  payloads fail [6]. At the interface-design specification level, Nielsen
  Norman Group's (NN/g) *Use Good Prototype Specifications to Empower Team
  Collaboration* (2022-06-05) distinguishes *Element Specifications*,
  *Functionality Specifications*, and *Content Specifications*, placing
  feature constraints, loading behavior, error handling, and component
  states under Functionality Specifications [14]. Rather than inventing
  offline, loading, empty, and error behavior ad hoc on each wireframe,
  specification practice defines global feedback rules (such as global
  offline banners, retry policies, and skeleton timeouts) once and maps
  view-specific empty, loading, error, and degraded states in a structured
  state matrix per view or data component [14, 15].

- **F6. Role-based and permission-dependent variations of a single view
  are modeled as parameters of the global "Context of Use" coupled with a
  role-by-view state matrix, rather than duplicating screen definitions**
  [consensus — standard and practitioner claims; rests on summarised
  fetches]. The W3C *MBUI - Glossary* (Working Group Note, 2014-01-07)
  formally places user role outside the screen model inside the global
  *Context of use*, defined as runtime and design-time information about
  "(1) the user (or set of users) who is (are) intended to use, or is
  actually using, the interactive system (eg, capabilities/functional
  limitations, preferences/needs, profile, idiosyncrasies, current tasks
  and activities, role); (2) the platform to be used or is actually used;
  (3) the social and physical environment" (§ Context of use), while the
  *Abstract User Interface (AUI)* is the "Composition of Abstract
  Interaction Units along with their abstract behaviour" that adapts to
  that context [2]. In practical UX deliverables, NN/g's *Wireflows*
  (2016-12-04) defines wireflows as "a design-specification format that
  combines wireframe-style page layout designs with a simplified
  flowchart-like way of representing interactions" to document conditional
  branches and dynamic state changes without cloning entire screen packs
  for each role [15], while prototype functionality specifications [14]
  record permission-restricted states (hidden, disabled with explanation,
  or read-only) as state rules on the shared view.

- **F7. Specification practice and formal standards divide storage between
  a single application-level manifest/shell specification and lightweight
  per-screen declarations ("declare invariants once, bind parameters
  locally")** [consensus — standards and practitioner guidance; rests on
  summarised fetches]. None of the examined standards or specification
  frameworks store whole-application behaviour exclusively per screen or
  exclusively in a monolithic global prose block. Instead:
  1. **Stored once for the whole application:** the root container
     hierarchy and landmark navigation shell [1, 6, 10, 13]; global
     navigation scope, start destination, and display mode [3, 7]; window
     types (primary vs. auxiliary) and adaptive breakpoint/size-class
     rules [9, 10, 11]; notification categories, interruption levels, and
     background action handlers [4, 12]; offline caching strategy and
     global network-loss feedback rules [4, 6]; and the catalog of user
     roles/permissions in the context of use [2].
  2. **Stored on each screen (or view container):** its parent container
     in the hierarchy and whether it participates in an XOR or multi-pane
     split [1, 9]; its local route/deep-link URI pattern and required
     parameters [7, 8]; whether it opens in the primary window or an
     auxiliary/modal window [11]; which notification events deep-link into
     it [12]; its local cells in the state matrix (empty, loading,
     cached/offline, error) [14]; and its local role/permission visibility
     or editability overrides [2, 14].

## Unexpected

The card's framing treats "a single screen" as a fixed unit of an
interface description and asks what lies outside any single screen.
However, Android's *Canonical layouts* [9], Apple's *Sidebars* and *Split
Views* guidelines [13], and OMG's *IFML* container hierarchy [1] show that
a "screen" is not a stable unit across viewports: on a compact phone
viewport, a master list and an item detail are two sequential full-screen
views linked by a navigation transition, whereas on an expanded tablet or
desktop viewport they are two simultaneous peer panes (`ViewContainer`
children without `isXOR`) inside a single window scaffold [1, 9]. A
textual UI description that takes the "screen" as its atomic container
breaks when targeting web, mobile, and desktop simultaneously; the stable
atomic unit in both IFML and Material 3 adaptive design is the *view
container* (or *pane*), which an application-level layout scaffold
composes into one or more simultaneous panes depending on window size
class [1, 9, 10].

## Not found

- **A single standardized industry template for textual UX/UI
  specifications that unifies all six whole-application behaviours in one
  schema:** while OMG IFML 1.0 [1] formalizes containers, landmarks, events,
  and flows, and W3C Web Application Manifest [3] plus Service Workers [4]
  standardize web installability and offline lifecycle, no single W3C,
  ISO, or practitioner Markdown template was found in searches across
  `w3.org`, `omg.org`, and `nngroup.com` that combines routing, adaptive
  windowing, notifications, offline states, and RBAC permission matrices
  into one canonical document format.
- **Empirical controlled studies measuring defect rates of per-screen
  versus application-level UI specifications:** queries on `nngroup.com`
  and general web search returned practitioner guidance [14, 15] and
  standards [1, 2], but no controlled experiment quantifying handoff bugs
  between the two specification shapes.

## Options

Because the project (`forge`) is designing a versioned Markdown format for
describing UX/UI across web, mobile web, native mobile, and desktop, the
findings present three structural options for where whole-application
behaviour lives in the Markdown artifact chain:

1. **Option A: Dedicated Application Shell & Global Rules document
   (`app.md` or `shell.md`) plus per-view-container documents.**
   - *How it works:* One top-level document defines the application
     manifest (start destination, scope, window taxonomy), the persistent
     navigation shell (`isLandmark` destinations and how the shell adapts
     across Compact/Medium/Expanded window size classes), the global
     notification catalog, the offline/degraded policy, and the global
     role/permission vocabulary. Each view container (pane, not viewport
     screen) has its own definition declaring only its route pattern,
     parent container, multi-pane pairing rules, local state matrix rows
     (loading, empty, offline, error), and local role overrides.
   - *Trade-offs:* Matches IFML [1], W3C Manifest/MBUI [2, 3], and
     Android/Apple adaptive architecture [7, 9, 11]; eliminates repetition
     across screens and handles multi-pane desktop/mobile adaptation
     cleanly. Requires human authors and AI agents to load two levels of
     context (the application file plus the target view container file)
     when editing or building a view.

2. **Option B: Pure per-screen specification with embedded global-rule
   imports or repeated sections.**
   - *How it works:* Every screen document is self-contained and repeats
     (or includes by template) its navigation frame, deep-link entry
     behavior, window mode, offline state, and role visibility rules.
   - *Trade-offs:* Easy for a coding agent to read a single file in
     isolation for a tiny MVP, but directly violates the DRY structure of
     platform navigation graphs [7, 8] and app shells [6], breaks when two
     screens merge into a multi-pane layout on larger viewports [9], and
     creates high maintenance drift when a global rule changes [14].

3. **Option C: Separated cross-cutting concern matrices (one document each
   for routing/navigation, state matrix, and role/permission matrix)
   alongside screen definitions.**
   - *How it works:* Keeps view definitions purely about layout and local
     elements, while placing all routes/deep links, all loading/error/offline
     states, and all role permissions into separate application-wide matrix
     tables.
   - *Trade-offs:* Centralizes auditing for security (roles) and resilience
     (offline/error states), but scatters the specification of a single
     view across four or five files, increasing cognitive load during
     interactive human-agent editing compared to Option A's inheritance
     model.

## Relevance to this project

*Inference applied to the `forge` framework:* Option A is the strongest
fit for `forge`'s versioned Markdown chain and its four target platforms
(web, mobile web, native mobile, desktop). A candidate shape built only
from "screens, elements, and linear paths" cannot represent landmark
navigation shells [1, 6], synthetic back stacks on deep links [7, 8],
primary versus auxiliary windows [11], background notifications [4, 12],
or multi-pane canonical layouts that fuse two mobile screens into one
desktop window [9]. In `forge`, the UX/UI description should therefore
introduce a top-level **Application Specification** above the view
definitions, and replace the naive notion of a "page/screen" with a **View
Container (Pane)** definition:

- **In the Application Specification (once per application):**
  - *Context of use & roles:* declared user roles and permission tiers [2].
  - *Window & adaptive scaffold:* primary vs. auxiliary window rules [11],
    window size classes (Compact, Medium, Expanded), and how the
    persistent navigation frame adapts across them (bottom bar, rail,
    sidebar/drawer) [10, 13].
  - *Global navigation & routing root:* the fixed start destination, URL
    scope, and global `isLandmark` destinations [1, 3, 7].
  - *Asynchronous events & notifications:* system/push notification types,
    interruption levels, inline background actions, and target containers
    [1, 4, 12].
  - *Global resilience & feedback rules:* app-shell offline caching
    behavior, global connectivity indicators, validation timing, and
    confirmation rules [4, 6, 14].
- **In each View Container / Pane definition (once per container):**
  - *Placement & address:* parent container, canonical pairing (e.g.,
    whether it pairs as the detail pane or supporting pane alongside
    another container on Expanded viewports) [1, 9], and local route/deep
    link URI pattern with parameters [7, 8].
  - *Local state matrix:* specific behaviour for Populated, Loading,
    Empty, Offline/Cached, and Error states where they specialize the
    global rules [14].
  - *Role & permission delta:* which elements or actions are hidden,
    disabled, or read-only for specific roles from the global role list
    [2, 14].

**Consult when:** designing the top-level schema of the UX/UI Markdown
description; deciding whether the unit of description is a "page/screen"
or a "view container/pane"; specifying routing, deep links, multi-window
desktop/tablet behavior, notifications, offline states, or role-based UI
variations; or prompting an AI agent to ask what whole-application rules
are missing before generating screen descriptions.

## Sources

1. **Interaction Flow Modeling Language (IFML), Version 1.0** — Object
   Management Group (OMG); February 2015 (dated by structured metadata on
   the specification page); `https://www.omg.org/spec/IFML/1.0`; primary
   (formal standard, accessed via summarised fetch, which is a tertiary
   retrieval mode); read via summarised fetch covering `ViewContainer`,
   `isLandmark`, `isXOR`, `isDefault`, `InteractionFlow`, and event types;
   original.
2. **MBUI - Glossary** — W3C Model-Based User Interfaces Working Group
   (ed. Jaroslav Pullmann, Fraunhofer FIT); 2014-01-07 (dated by W3C
   Working Group Note header); `https://www.w3.org/TR/mbui-glossary/`;
   primary (W3C Working Group Note, accessed via summarised fetch); read
   via summarised fetch covering the entries *Abstract User Interface
   (AUI)*, *Concrete User Interface (Concrete UI)*, and *Context of use*;
   original.
3. **Web Application Manifest** — W3C Web Applications Working Group (ed.
   Marcos Cáceres, Daniel Murphy, Christian Liebel); 2026-10-13 (dated by
   W3C Working Draft header); `https://www.w3.org/TR/appmanifest/`;
   primary (W3C standard draft, accessed via summarised fetch); read via
   summarised fetch covering Abstract, `start_url` member, `scope` member,
   and `display` modes; original.
4. **Service Workers** — W3C Web Applications Working Group (ed. Monica
   Chintala, Yoshisato Yanagisawa); 2026-09-17 (dated by W3C Candidate
   Recommendation Draft header); `https://www.w3.org/TR/service-workers/`;
   primary (W3C standard draft, accessed via summarised fetch); read via
   summarised fetch covering Abstract and Functional `fetch` event
   (`FetchEvent`); original.
5. **HTML Living Standard — Navigation and session history APIs** —
   WHATWG; undated living standard (accessed 2026-11-21);
   `https://html.spec.whatwg.org/multipage/nav-history-apis.html`; primary
   (web standard, accessed via summarised fetch); read via summarised
   fetch covering the `Navigation` interface and `navigate` event
   interception; original.
6. **Application shell model** — Chrome for Developers (Google); undated
   documentation page;
   `https://developer.chrome.com/docs/workbox/app-shell-model`; primary
   (platform/vendor documentation for Workbox, accessed via summarised
   fetch); read via summarised fetch covering the opening definition and
   caching architecture of the application shell; original.
7. **Principles of navigation** — Android Developers (Google); 2026-02-26
   (dated by page last-updated metadata);
   `https://developer.android.com/guide/navigation/design/principles`;
   primary (platform owner guideline, accessed via summarised fetch); read
   via summarised fetch covering fixed start destination, back stack vs. Up
   navigation, and synthetic back stacks for deep links; original.
8. **Create a deep link for a destination** — Android Developers (Google);
   2026-10-28 (dated by page last-updated metadata);
   `https://developer.android.com/guide/navigation/design/deep-link`;
   primary (platform owner guideline, accessed via summarised fetch); read
   via summarised fetch covering URI pattern matching, implicit/explicit
   deep links, and back stack construction; original.
9. **Canonical layouts** — Android Developers (Google); 2026-09-01 (dated
   by Adaptive apps hub last-updated metadata);
   `https://developer.android.com/develop/ui/compose/layouts/adaptive/canonical-layouts`;
   primary (platform owner guideline, accessed via summarised fetch); read
   via summarised fetch covering list-detail (`ListDetailPaneScaffold`),
   supporting pane (`SupportingPaneScaffold`), and feed layouts across
   window size classes; original.
10. **Build adaptive navigation** — Android Developers (Google);
    2026-09-01 (dated by Adaptive apps hub last-updated metadata);
    `https://developer.android.com/develop/ui/compose/layouts/adaptive/build-adaptive-navigation`;
    primary (platform owner guideline, accessed via summarised fetch);
    read via summarised fetch covering `NavigationSuiteScaffold` and
    switching between navigation bar, rail, and drawer; original.
11. **Human Interface Guidelines — Windows** — Apple Inc.; undated living
    platform documentation;
    `https://developer.apple.com/design/human-interface-guidelines/windows`;
    primary (platform owner guideline, accessed via summarised fetch);
    read via summarised fetch covering primary vs. auxiliary windows,
    adaptive resizing, and multiwindow multitasking; original.
12. **Human Interface Guidelines — Notifications** — Apple Inc.; undated
    living platform documentation;
    `https://developer.apple.com/design/human-interface-guidelines/notifications`;
    primary (platform owner guideline, accessed via summarised fetch);
    read via summarised fetch covering notification definition, best
    practices, interruption levels, and deep-linking into window contexts;
    original.
13. **Human Interface Guidelines — Sidebars** — Apple Inc.; undated living
    platform documentation;
    `https://developer.apple.com/design/human-interface-guidelines/sidebars`;
    primary (platform owner guideline, accessed via summarised fetch);
    read via summarised fetch covering sidebar definition, space
    requirements, and `sidebarAdaptable` transitions between sidebars and
    tab bars across iOS, iPadOS, and macOS; original.
14. **Use Good Prototype Specifications to Empower Team Collaboration** —
    Leeloo Tang and Feifei Liu (Nielsen Norman Group); 2022-06-05 (dated
    by byline);
    `https://www.nngroup.com/articles/prototype-specifications/`;
    secondary (UX research and practice synthesis, accessed via summarised
    fetch); read via summarised fetch covering Element, Functionality, and
    Content specification categories and state documentation; original.
15. **Wireflows: A UX Deliverable for Workflows and Apps** — Page
    Laubheimer (Nielsen Norman Group); 2016-12-04 (dated by byline);
    `https://www.nngroup.com/articles/wireflows/`; secondary (UX research
    and practice synthesis, accessed via summarised fetch); read via
    summarised fetch covering the definition of wireflows and how
    multi-state workflows are documented; original.

## Opened and not used

- **Abstract User Interface Models** — W3C Model-Based User Interfaces
  Working Group (ed. Jean Vanderdonckt et al., 2014-04-08,
  `https://www.w3.org/TR/abstract-ui/`): superseded by [1] (OMG IFML 1.0)
  and [2] (W3C MBUI Glossary) for concrete container and context-of-use
  definitions.

## Search record

- **Queries run (in order):**
  1. `IFML OMG specification view container xor landmark interaction flow`
  2. `Android developer guide app architecture navigation principles deep links`
  3. `W3C Web Application Manifest Navigation API service workers offline`
  4. `Apple Human Interface Guidelines going deeper windows notifications`
  5. `Material Design 3 navigation canonical layouts adaptive design`
  6. `UI specification template wireframe annotations global rules state matrix`
  7. `"per-screen specification is enough" OR "global UI rules section unnecessary"` (disconfirming query)
  8. `site:developer.apple.com/design/human-interface-guidelines "Going deeper" OR "Windows" OR "Notifications" exact URL path`
  9. `site:m3.material.io/foundations/layout "Understanding layout" OR "Canonical layouts" OR "Applying layout" exact URL path`
  10. `site:developer.chrome.com/docs/workbox "service worker" OR "app shell" OR "caching strategies" exact URL path`
  11. `site:developer.android.com/guide/navigation "Principles of navigation" "Create a deep link" exact URL path last updated date`
  12. `site:w3.org/TR "Web Application Manifest" "Service Workers" exact URL date editor`
  13. `site:omg.org/spec/IFML "Interaction Flow Modeling Language" version 1.0 date exact URL`
  14. `site:developer.apple.com/design/human-interface-guidelines "tab-bars" OR "sidebars" OR "split-views" OR "modality" exact URL`
  15. `"https://m3.material.io/foundations/layout/" exact URL overview canonical-layouts applying-layout`
  16. `site:w3.org/TR/service-workers "Service Workers" exact URL date editors`
  17. `site:w3.org/TR "mbui-glossary" OR "abstract-ui" Model-Based User Interfaces exact URL date editors`
  18. `site:html.spec.whatwg.org/multipage "nav-history-apis.html" OR "browsing-the-web.html" Navigation API exact URL`
  19. `site:nngroup.com "wireflows" OR "wireframe annotations" OR "design specifications" OR "permission" exact URL author date`
  20. `"m3.material.io/foundations/layout/understanding-layout/overview" OR "m3.material.io/foundations/layout/canonical-layouts/overview" exact URL`
  21. `site:developer.android.com/develop/ui/compose/layouts/adaptive "canonical-layouts" OR "build-adaptive-navigation" exact URL date title`
  22. `site:developer.chrome.com/docs/workbox/app-shell-model title date author verbatim quote "application shell"`
  23. `site:developer.apple.com/design/human-interface-guidelines/windows AND site:developer.apple.com/design/human-interface-guidelines/notifications verbatim quotes`
  24. `site:nngroup.com/articles/wireflows "Wireflows: A UX Deliverable for Workflows and Apps" author date verbatim quote`
  25. `site:nngroup.com/articles "Use Good Prototype Specifications to Empower Team Collaboration" exact URL author date verbatim quote`
  26. `site:developer.android.com/guide/navigation/design/principles AND site:developer.android.com/guide/navigation/design/deep-link verbatim quote last updated date`
  27. `site:developer.android.com/develop/ui/compose/layouts/adaptive/canonical-layouts AND site:developer.android.com/develop/ui/compose/layouts/adaptive/build-adaptive-navigation verbatim quote last updated date`
  28. `site:w3.org/TR/appmanifest AND site:w3.org/TR/service-workers verbatim quote abstract scope start_url fetch event`
  29. `site:w3.org/TR/mbui-glossary "Abstract User Interface" "Concrete User Interface" "Context of Use" verbatim quote`
  30. `site:nngroup.com/articles/prototype-specifications verbatim quote "element" "functionality" "content" state role permission`
  31. `site:developer.apple.com/design/human-interface-guidelines/tab-bars AND site:developer.apple.com/design/human-interface-guidelines/sidebars verbatim quote`
- **Pages opened (16 openings via summarised fetch, 15 used in Sources
  and 1 in Opened and not used):**
  1. `https://www.omg.org/spec/IFML/1.0`
  2. `https://www.w3.org/TR/mbui-glossary/`
  3. `https://www.w3.org/TR/abstract-ui/` (opened and not used)
  4. `https://www.w3.org/TR/appmanifest/`
  5. `https://www.w3.org/TR/service-workers/`
  6. `https://html.spec.whatwg.org/multipage/nav-history-apis.html`
  7. `https://developer.chrome.com/docs/workbox/app-shell-model`
  8. `https://developer.android.com/guide/navigation/design/principles`
  9. `https://developer.android.com/guide/navigation/design/deep-link`
  10. `https://developer.android.com/develop/ui/compose/layouts/adaptive/canonical-layouts`
  11. `https://developer.android.com/develop/ui/compose/layouts/adaptive/build-adaptive-navigation`
  12. `https://developer.apple.com/design/human-interface-guidelines/windows`
  13. `https://developer.apple.com/design/human-interface-guidelines/notifications`
  14. `https://developer.apple.com/design/human-interface-guidelines/sidebars`
  15. `https://www.nngroup.com/articles/prototype-specifications/`
  16. `https://www.nngroup.com/articles/wireflows/`
- **What the disconfirming query found:** Running `"per-screen
  specification is enough" OR "global UI rules section unnecessary"`
  returned no standard, platform guideline, or practitioner article
  arguing that application-wide UI rules are unnecessary; the only result
  discussed how small MVPs sometimes start with isolated screen specs
  before incurring design debt and inconsistency when scaling without
  shared rules.
- **Reason the run ended:** Both parts of the card's stop rule were met at
  sixteen pages opened via summarised fetch: every route in the question
  (navigation frame/shell, addresses and deep links, multi-window and
  adaptive panes, unasked notifications/events, offline/degraded states,
  and role/permission variation) had primary standard or platform-owner
  sources, and differently worded queries yielded no new structural
  categories.
