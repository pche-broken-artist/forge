---
date: 2026-11-21
project: forge
topic: The description and the test
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 20; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":51269,"output_tokens":15855,"thinking_tokens":6478,"cache_read_tokens":196340,"total_tokens":67124}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-20-description-and-test
status: immutable
---

# How automated interface testing describes screens in modular text, where those units survive or break across interface changes, and how a built interface is checked against its description

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Twenty years of automated user-interface testing show that modular text
descriptions of screens survive interface changes only when they split
into three distinct layers: user intent (business tasks in user paths),
component semantics (accessibility roles, labels, and hierarchy), and
implementation bindings (DOM selectors or platform widget hooks). The
disconfirming queries ("page object anti-pattern" and "BDD UI tests
brittle") confirm the card's expectation and sharpen it: coupling user
paths directly to element-level mechanics ("click button X, fill field
Y") or bundling locators, workflows, and assertions into monolithic Page
Objects causes severe maintenance failure when layouts or workflows
change. What survives across redesigns of the visual interface (in the
sense of the interface design held in a design tool and the visual
identity of a design system) is a separation between stateless element
descriptors ("Lean Page Objects" or component specifications queried by
semantic role and accessible name) and actor-centred `Tasks` that
compose them. Checking a built interface against its textual description
now uses four mechanisms rather than three: functional assertions bound
to executable steps, isolated component interaction specs, pixel-based
visual regression snapshots, and declarative accessibility-tree (`ARIA`)
snapshots in structured text.

## Question

- **Question:** What has automated testing of interfaces learned about
  describing screens in modular text: how do the Page Object and
  Screenplay patterns and executable specifications define the elements
  of a screen and their actions as units of their own that user paths
  refer to, at which level of abstraction do such units survive a change
  of the interface and at which do they break, and how is a built
  interface checked against its description (tests bound to the text,
  comparison of pictures, inspection)?
- **Why it matters:** these are definitions per element kept in version
  control for twenty years, and the build needs a way to show that it
  built what was described.
- **What would answer it:** the pattern literature and the testing
  tools' own documentation.
- **Where to look:** the original descriptions of Page Object and
  Screenplay; specification by example and behaviour-driven development
  for interfaces; testing tools' guidance on the level of abstraction;
  visual regression testing.
- **Disconfirming query:** "page object anti-pattern", "BDD UI tests
  brittle"; expected: units at the level of an element are brittle,
  units at the level of a task last.
- **Stop rule:** nothing new from a differently worded query and every
  route has a primary source; ten to fifteen pages opened.

**Baseline to beat:** A generic summary saying that Page Objects put
selectors in classes and BDD uses Given/When/Then. To beat the baseline,
this note must identify the exact structural unit boundaries in Page
Object, Screenplay, and Storybook component specs, distinguish which
abstraction levels break under which kind of interface change (styling,
DOM refactoring, widget replacement, or workflow change), and document
how current test runners verify built interfaces against text and visual
baselines. Throughout this note, "design" is disambiguated between (1)
the interface design held in a design tool (layout, screens, and visual
flows), (2) the technical design between requirements and tasks in
spec-driven kits (software and test architecture), and (3) the visual
identity of a design system (tokens, typography, and styling).

## Key findings

- **F1. A Page Object wraps a whole screen or a reusable screen fragment
  behind an intent-revealing API, hiding HTML structure and assertions
  from user paths.** [consensus — practitioner claim and vendor
  documentation, resting on summarised fetches of [1, 2, 9]]. Martin
  Fowler's foundational 2013 formulation (building on Simon Stewart's
  WebDriver pattern, originally termed *Window Driver*) defines a Page
  Object as a software-architecture wrapper around an HTML page or
  significant page fragment (such as a header, panel, or reusable UI
  widget) that exposes an application-specific API for what a human user
  can see and do on that unit [1]. Both Fowler and official Selenium and
  Playwright documentation state two structural rules: first, raw driver
  calls and element locators must never leak into test scripts; second,
  Page Objects must remain free of test assertions (except verifying
  that the page or critical element itself has loaded), leaving
  verification to the calling test so that the same screen unit can
  serve both positive and negative user paths [1, 2, 9].

- **F2. Bundling element definitions and multi-step user workflows into
  single Page Object classes violates the Single Responsibility
  Principle and produces "God Page" anti-patterns as screens grow.**
  [consensus — practitioner claim, resting on summarised fetches of [3,
  4, 6]]. The disconfirming query `"page object anti-pattern"` shows
  that when a single class holds both every element locator on a complex
  screen and every method for interacting with it, the class bloats into
  thousands of lines, suffers frequent merge conflicts, and tightly
  couples navigation sequences through hardcoded page-return chaining
  [3, 4]. Furthermore, Gleb Bahmutov's 2019 Cypress engineering critique
  argues that using Page Objects to drive the UI through prerequisite
  screens (such as logging in or stepping through a multi-page wizard
  via DOM clicks just to reach page four) makes end-to-end suites slow
  and fragile; state setup should bypass the UI via internal
  "Application Actions" or API calls, reserving UI descriptions for the
  screen actually under test [6].

- **F3. The Screenplay pattern resolves Page Object bloat by separating
  static element descriptors ("Lean Page Objects") from reusable
  `Interactions`, business `Tasks`, and state `Questions`.** [consensus
  — practitioner claim and framework documentation, resting on
  summarised fetches of [3, 4, 5]]. Devised by Antony Marcano and Andy
  Palmer (2007–2008) and formalized with John Ferguson Smart and Jan
  Molak (2016), the Screenplay pattern refactors Page Objects along
  SOLID software-design principles into five distinct concepts: `Actors`
  who have `Abilities` (such as browsing the web), perform business-level
  `Tasks` composed of low-level UI `Interactions` (`Click.on`,
  `Enter.theValue`), and ask `Questions` (`Text.of`, `Value.of`) to
  assert system state [3, 4]. In Serenity/JS's Page Element Query
  Language (PEQL), the screen description itself shrinks to a **Lean
  Page Object**: a stateless collection of `PageElement` descriptors
  that defines only what elements exist on a screen or component and how
  they nest, while all actions live in `Tasks` and `Interactions` [4,
  5].

- **F4. Executable specifications in Gherkin/BDD break when written at
  the imperative element level and survive when written at the
  declarative task level.** [consensus — vendor documentation and
  practitioner claim, resting on summarised fetches of [3, 7]]. Both the
  official Cucumber documentation ("Better Gherkin") and the
  disconfirming query `"BDD UI tests brittle"` identify the primary
  cause of brittle text specifications: **imperative steps** that read
  like mechanical UI scripts (`When I type "alice" into the "#username"
  field And I click "#submit-btn"`) [7]. Imperative steps break whenever
  an interface design change (in the sense of a screen layout or flow
  change in a design tool) renames a button, replaces a text input with
  a select control, or moves a page into a modal dialog [7].
  **Declarative steps** (`When "alice" logs in with valid credentials`)
  express domain intent ("what" the user accomplishes) in the feature
  text and push the "how" into step definitions backed by Tasks or Page
  Objects, allowing the feature specification to survive complete UI
  redesigns unchanged [3, 7].

- **F5. Element definitions survive visual-identity and DOM refactoring
  changes when bound to accessibility roles and user-visible labels, and
  break when bound to DOM structure or CSS styling.** [consensus —
  vendor documentation, resting on summarised fetches of [8, 10]].
  Testing Library's Guiding Principles and Playwright's Locator
  documentation converge on a strict hierarchy of element identification
  resilience [8, 10]:
  1. **Semantic and accessible queries (`getByRole` with accessible
     `name`, `getByLabel`, `getByText`):** Query the browser's
     accessibility tree rather than HTML tag names or CSS classes. A
     button defined as `role=button, name="Submit"` survives changes to
     the visual identity of a design system (CSS classes, colors,
     layout) and technical DOM refactoring (`<button>` vs. `<div
     role="button">`), breaking only if the user-facing wording or
     semantic role changes [8, 10].
  2. **Explicit test identifiers (`data-testid` / `getByTestId`):**
     Survive wording, translation, and role changes, but are invisible
     to humans and assistive technologies; Testing Library classifies
     them as a last-resort escape hatch when semantic queries are
     impractical [8].
  3. **Structural and styling selectors (XPath paths, CSS class chains,
     DOM hierarchy):** Break on minor layout or styling edits and are
     explicitly discouraged across modern testing tools [8, 10].

- **F6. Empirical studies of industrial WebDriver suites show that
  modular Page Objects require higher initial authoring effort than flat
  scripts but substantially lower maintenance effort across releases.**
  [single source — controlled industrial case study, resting on
  summarised fetches of [1]]. As cited by Fowler [1] from Maurizio
  Leotta, Diego Clerissi, Filippo Ricca, and Cristiano Spadaro's 2013
  industrial case study (*Improving Test Suites Maintainability with the
  Page Object Pattern*), comparing equivalent WebDriver test suites with
  and without Page Objects across application evolution cycles showed
  that localizing element locators and screen mechanics inside Page
  Objects sharply reduced the lines of code modified and the repair time
  needed when the application's UI changed between releases [1].

- **F7. Component stories (Storybook) unify element description,
  functional interaction tests, and visual baseline capture in one
  modular unit per component state.** [emerging — vendor documentation,
  resting on summarised fetches of [13, 14]]. In Storybook's testing
  architecture, a component story acts as an executable specification of
  a single UI component in a named state: `args` declare its input
  properties, a `play` function scripts user interactions and DOM
  assertions using Testing Library queries (`within(canvasElement)`,
  `userEvent`, `expect`), and visual testing tools (such as Chromatic)
  automatically capture rendered snapshots of every story to detect
  visual regressions across commits without extra test code [13, 14].

- **F8. Built interfaces are verified against descriptions at three
  distinct fidelity levels: behavioral assertions, accessibility-tree
  (`ARIA`) YAML snapshots, and pixel-level visual comparisons.**
  [consensus — vendor documentation, resting on summarised fetches of
  [11, 12, 13]]. Modern test runners check a built screen against its
  specification through three complementary mechanisms:
  1. **Behavioral/functional assertions (`expect(locator)`):** Verify
     that specific elements exist, hold expected text/values, and
     respond to user actions [10, 14].
  2. **Declarative ARIA snapshots (`toMatchAriaSnapshot` / `.aria.yml`):**
     Introduced in Playwright, this mechanism serializes a page or
     component locator's accessibility tree into a concise, hierarchical
     YAML text template (`- role "accessible name" [attribute=value]`,
     supporting regexes and partial matching) and compares the live built
     interface against that text structure—verifying semantic hierarchy
     and content without breaking on CSS or pixel shifts [12].
  3. **Visual regression comparisons (`toHaveScreenshot` / Chromatic):**
     Compare rendered bitmap screenshots of a full page or individual
     component locator against versioned baseline images, catching
     visual-identity, layout reflow, and responsive styling bugs that
     text and DOM assertions cannot see, at the cost of requiring
     baseline updates (`--update-snapshots`) whenever visual appearance
     intentionally changes [11, 13].

## Unexpected

- **Playwright's ARIA snapshot format (`.aria.yml`) is already a modular
  textual screen description language used directly as an executable
  test oracle [12].** The card asks how a built interface is checked
  against its description ("tests bound to the text, comparison of
  pictures, inspection"). Playwright's `toMatchAriaSnapshot()` and
  `page.ariaSnapshot()` (documented in [12]) bridge textual screen
  descriptions and automated verification directly: a screen or region
  is described as an indented YAML tree of semantic roles, accessible
  names, and state attributes (for example, `banner`, `navigation`,
  `heading "Dashboard" [level=1]`, `button "Submit" [disabled=true]`).
  Because it supports partial matching (omitting dynamic children) and
  regular expressions, a human or AI agent can write or inspect a `.aria.yml`
  block as a readable structural description of a screen and execute it
  verbatim against the built browser DOM without writing imperative
  selector glue code [12].

- **Screenplay's "Lean Page Objects" validate the project's hypothesis
  by stripping actions out of element definitions [4, 5].** The card
  frames Page Objects and Screenplay as defining "the elements of a
  screen and their actions as units of their own". While classic Page
  Objects bundle elements and actions together [1, 2], the Screenplay
  literature found that bundling actions into element/page classes is
  precisely what makes them brittle when workflows span multiple
  components or modals [3, 4]. Screenplay separates **Lean Page
  Objects** (pure structural definitions of elements and how they nest on
  a page) from **Tasks/Interactions** (actions performed by an actor
  across those elements) [4, 5].

## Not found

- **Quantitative survival/breakage rates by locator type in open primary
  sources:** While empirical studies by Leotta, Ricca, and colleagues
  comparing locator fragility (such as XPath vs. ID vs. ROBULA+) and
  Page Object maintenance effort were identified in search summaries,
  direct HTTP access to full-text academic PDFs (`curl.exe`) was blocked
  by the workspace sandbox policy, so exact percentage figures from
  those papers could not be verified from the opened primary text and
  are omitted rather than estimated.
- **Native mobile and desktop Screenplay/ARIA snapshot parity:** Primary
  documentation opened via targeted domain queries focused predominantly
  on web and mobile-web DOM/accessibility trees (Selenium, Playwright,
  Testing Library, Storybook); no primary tool documentation was opened
  demonstrating YAML accessibility-tree snapshot matching equivalent to
  Playwright's `toMatchAriaSnapshot` on native desktop or native iOS/Android
  runners.

## Options

For designing the project's Markdown UX/UI description format and its
build-verification strategy, the findings present three structural
options:

1. **Option A: Classic Page-Object style (bundle element definitions and
   user actions inside each element/page Markdown unit).**
   - *How it works:* Each element or page definition lists both its
     structural properties and all user workflows/actions that happen on
     it.
   - *Trade-offs:* Simple for single-screen widgets, but repeats the
     known "God Page" failure mode [3, 4]: when a user flow spans
     multiple components, triggers a modal, or changes sequence, element
     definitions must be edited even though the individual elements did
     not change.

2. **Option B: Screenplay / Lean-Component split (stateless element and
   page definitions + separate declarative task paths).**
   - *How it works:* Element definitions in Markdown declare only
     semantic role, accessible label/name, states/variants (like
     Storybook stories [13]), and local affordances; page definitions
     compose elements hierarchically (like Lean Page Objects [4, 5] and
     ARIA trees [12]); user-path documents express declarative `Tasks`
     [3, 7] that reference those elements by semantic role and name.
   - *Trade-offs:* Requires maintaining two linked structures (structural
     units vs. task flows), but isolates breakage: visual styling edits
     break neither; layout/component swaps update only the page/element
     unit; workflow changes update only the task path.

3. **Option C: Three-tier verification binding (ARIA tree snapshots +
   component interaction specs + opt-in visual snapshots).**
   - *How it works:* The Markdown description's semantic element hierarchy
     compiles or maps directly to an accessibility-tree snapshot
     (`toMatchAriaSnapshot` [12]) to verify that the build contains the
     described elements in the described hierarchy; user paths map to
     declarative task/interaction tests (`getByRole` [8, 10]); visual
     screenshot comparison (`toHaveScreenshot` [11]) is used only after
     the visual identity (design system) is locked.
   - *Trade-offs:* Structural ARIA snapshots verify semantic presence and
     hierarchy immediately on the first build without failing on
     unapproved pixel styling, whereas pixel snapshots fail on every font
     or spacing tweak until a visual baseline exists.

## Relevance to this project

The project's candidate idea—that *"every element of a screen (a search
field, say) has a small definition of its own in Markdown that carries
its function, and a page definition names which elements it holds and
where they stand"*—is strongly supported by twenty years of UI test
architecture, **with one crucial refinement** from the Screenplay and
BDD literature [3, 4, 5, 7].

**Recommendation:** Adopt **Option B** for the Markdown description's
structure and **Option C** for verifying the built interface against the
description.
1. **Keep element and page definitions "Lean" (structural and semantic,
   not workflow-imperative):** In my inference from [4, 5, 8, 13], an
   element's Markdown unit should define its semantic **role** (e.g.,
   `searchbox`, `button`, `dialog`), its **accessible name/label** (what
   the user reads or hears), its **states/variants** (empty, filled,
   disabled, error—analogous to Storybook stories [13]), and its
   **primitive affordances** (can be typed into, clicked, cleared),
   without embedding multi-step business workflows or assertions.
2. **Compose pages as hierarchical semantic trees:** A page definition
   should name the landmark regions (`banner`, `navigation`, `main`,
   `complementary`) and which element units stand inside each region.
   This mirrors both Serenity/JS's Lean Page Objects [5] and
   Playwright's YAML ARIA snapshots [12].
3. **Write user paths at the declarative Task level, referencing elements
   by role and accessible name:** User paths should state business tasks
   (`When the user searches for "invoices"`), mapping down to primitive
   interactions on the named screen elements (`searchbox "Search"`). This
   prevents the classic imperative-BDD brittleness where every UI layout
   tweak breaks all user path documents [7].
4. **Verify the build against the Markdown description using ARIA
   snapshots first, interaction tests second, and pixel diffs last:**
   Because a fresh build from a text description has no prior screenshot
   baseline, pixel-based visual regression (`toHaveScreenshot` [11])
   cannot verify the first build; it only guards against unintended drift
   after a human approves a rendered state. By contrast, a hierarchical
   ARIA snapshot (`toMatchAriaSnapshot` [12]) and role-based interaction
   tests (`getByRole` [8, 10]) can be derived directly from the Markdown
   element and page definitions to prove automatically that the coding
   agent built every described element, with the right label and state,
   in the right region of the screen.

**Consult when:**
- Designing the schema of the per-element and per-page Markdown files
  (deciding what belongs in an element definition versus a user-path
  document).
- Choosing how an AI coding agent or test runner checks that a built UI
  matches the Markdown specification before a human visually inspects it.
- Deciding how stable identifiers (`role` + `accessible name` vs.
  `data-testid`) should be specified in the text description.

## Sources

1. **Page Object** — Martin Fowler (with contributions from Simon
   Stewart), 2013-09-10 (dated by byline),
   https://martinfowler.com/bliki/PageObject.html ; kind: tertiary (via
   summarised fetch of primary original); how read: summarised fetch
   (direct HTTP fetch via `curl.exe` denied by workspace sandbox
   policy); original pattern article.
2. **Page object models** — Selenium Project (Software Freedom
   Conservancy), undated (current Selenium 4 documentation as of 2026),
   https://www.selenium.dev/documentation/test_practices/encouraged/page_object_models/ ;
   kind: tertiary (via summarised fetch of primary vendor/project
   documentation); how read: summarised fetch (direct HTTP fetch denied
   by sandbox policy); original documentation.
3. **Beyond Page Objects: Next Generation Test Automation with Serenity
   and the Screenplay Pattern** — Andy Palmer, Antony Marcano, John
   Ferguson Smart, and Jan Molak (InfoQ), 2016-03-15 (dated by byline),
   https://www.infoq.com/articles/Beyond-Page-Objects-Serenity-Screenplay/ ;
   kind: tertiary (via summarised fetch of primary article by the
   pattern's creators); how read: summarised fetch (direct HTTP fetch
   denied by sandbox policy); original article.
4. **The Screenplay Pattern** — Jan Molak / Serenity/JS Project, undated
   (current Serenity/JS Handbook),
   https://serenity-js.org/handbook/design-patterns/screenplay-pattern/ ;
   kind: tertiary (via summarised fetch of primary framework
   documentation); how read: summarised fetch (direct HTTP fetch denied
   by sandbox policy); original documentation.
5. **Page Element Query Language** — Jan Molak / Serenity/JS Project,
   undated (current Serenity/JS Handbook),
   https://serenity-js.org/handbook/design-patterns/page-element-query-language/ ;
   kind: tertiary (via summarised fetch of primary framework
   documentation); how read: summarised fetch (direct HTTP fetch denied
   by sandbox policy); original documentation.
6. **Stop using Page Objects and Start using App Actions** — Gleb
   Bahmutov (Cypress.io), 2019-01-03 (dated by URL and byline),
   https://www.cypress.io/blog/2019/01/03/stop-using-page-objects-and-start-using-app-actions/ ;
   kind: tertiary (via summarised fetch of primary engineering blog post);
   how read: summarised fetch (direct HTTP fetch denied by sandbox
   policy); original article.
7. **Better Gherkin** — Cucumber / SmartBear Software, undated (current
   Cucumber BDD documentation),
   https://cucumber.io/docs/bdd/better-gherkin/ ; kind: tertiary (via
   summarised fetch of primary tool documentation); how read: summarised
   fetch (direct HTTP fetch denied by sandbox policy); original
   documentation.
8. **About Queries ( and Guiding Principles)** — Kent C. Dodds and
   Testing Library Contributors, undated (current Testing Library
   documentation), https://testing-library.com/docs/queries/about/ ;
   kind: tertiary (via summarised fetch of primary tool documentation);
   how read: summarised fetch (direct HTTP fetch denied by sandbox
   policy); original documentation.
9. **Page object models** — Microsoft Corporation (Playwright), undated
   (current Playwright documentation),
   https://playwright.dev/docs/pom ; kind: tertiary (via summarised
   fetch of primary tool documentation); how read: summarised fetch
   (direct HTTP fetch denied by sandbox policy); original documentation.
10. **Locators** — Microsoft Corporation (Playwright), undated (current
    Playwright documentation), https://playwright.dev/docs/locators ;
    kind: tertiary (via summarised fetch of primary tool documentation);
    how read: summarised fetch (direct HTTP fetch denied by sandbox
    policy); original documentation.
11. **Visual comparisons** — Microsoft Corporation (Playwright), undated
    (current Playwright documentation),
    https://playwright.dev/docs/test-snapshots ; kind: tertiary (via
    summarised fetch of primary tool documentation); how read: summarised
    fetch (direct HTTP fetch denied by sandbox policy); original
    documentation.
12. **Snapshot testing (Aria snapshots)** — Microsoft Corporation
    (Playwright), undated (current Playwright documentation, feature
    introduced 2024–2025), https://playwright.dev/docs/aria-snapshots ;
    kind: tertiary (via summarised fetch of primary tool documentation);
    how read: summarised fetch (direct HTTP fetch denied by sandbox
    policy); original documentation.
13. **How to test UIs with Storybook** — Chroma Software / Storybook
    Maintainers, undated (current Storybook 8/9 documentation),
    https://storybook.js.org/docs/writing-tests/ ; kind: tertiary (via
    summarised fetch of primary tool documentation); how read: summarised
    fetch (direct HTTP fetch denied by sandbox policy); original
    documentation.
14. **Interaction tests** — Chroma Software / Storybook Maintainers,
    undated (current Storybook documentation),
    https://storybook.js.org/docs/writing-tests/interaction-testing ;
    kind: tertiary (via summarised fetch of primary tool documentation);
    how read: summarised fetch (direct HTTP fetch denied by sandbox
    policy); original documentation.

## Opened and not used

- **Improving Test Suites Maintainability with the Page Object Pattern:
  An Industrial Case Study** (Maurizio Leotta et al., IEEE ICSTW 2013,
  queried on `sepl.dibris.unige.it`) — summarised fetch confirmed the
  study's design and qualitative conclusions already cited via Fowler
  [1], but full-text PDF tables and exact repair-hour numbers could not
  be opened directly under sandbox policy; left out as a separate source
  to avoid citing unverified secondary numerical summaries.

## Search record

**Queries run (in order):**
1. `Martin Fowler PageObject Selenium Page Object Model` (broad query)
2. `Screenplay pattern Page Objects Refactored Marcano Molak Serenity`
   (broad query)
3. `"page object anti-pattern"` (disconfirming query 1)
4. `"BDD UI tests brittle"` (disconfirming query 2)
5. `Playwright documentation page object models locators visual comparisons aria snapshots`
   (broad query)
6. `Cucumber documentation declarative imperative Gherkin UI abstraction`
   (broad query)
7. `"PageObject" Martin Fowler 10 September 2013 URL quotes window-driver HTML wrapper assertions`
   (domain-targeted summarising fetch on `martinfowler.com`)
8. `"Page object models" documentation test_practices encouraged page_object_models URL quotes assertions`
   (domain-targeted summarising fetch on `selenium.dev`)
9. `"Page Objects Refactored: SOLID Steps to the Screenplay/Journey Pattern" Antony Marcano Andy Palmer John Ferguson Smart Jan Molak URL date quotes`
   (domain-targeted summarising fetch on `infoq.com`)
10. `"Page object models" "Locators" "Aria snapshots" "Visual comparisons" docs URLs toMatchAriaSnapshot toHaveScreenshot getByRole`
    (domain-targeted summarising fetch on `playwright.dev`)
11. `"Stop using Page Objects and Start using App Actions" Gleb Bahmutov URL date quotes anti-pattern`
    (domain-targeted summarising fetch on `cypress.io`)
12. `"Better Gherkin" OR "Anti-patterns" declarative imperative UI steps Cucumber documentation URL quotes`
    (domain-targeted query on `cucumber.io`, returned no summary)
13. `PageObject bliki Martin Fowler 2013 WindowDriver Simon Stewart assertions page elements fragment`
    (domain-targeted summarising fetch on `martinfowler.com`)
14. `Screenplay Pattern PageElement Lean Page Objects Actors Tasks Interactions Questions handbook`
    (domain-targeted summarising fetch on `serenity-js.org`)
15. `bdd better gherkin declarative imperative step definitions page objects`
    (domain-targeted summarising fetch on `cucumber.io`)
16. `Guiding Principles About Queries Priority getByRole accessible name data-testid`
    (domain-targeted summarising fetch on `testing-library.com`)
17. `aria snapshots toMatchAriaSnapshot YAML accessibility tree template page.ariaSnapshot`
    (domain-targeted summarising fetch on `playwright.dev`)
18. `writing tests interaction testing visual tests play function component specifications`
    (domain-targeted summarising fetch on `storybook.js.org`)
19. `"Page Object" empirical study maintenance fragility Leotta Ricca WebDriver locators`
    (targeted query for empirical maintenance studies)
20. `exact URL "Screenplay Pattern" "Page Element Query Language" handbook design`
    (domain-targeted URL verification on `serenity-js.org`)
21. `exact URL "About Queries" "Guiding Principles" docs queries about`
    (domain-targeted URL verification on `testing-library.com`)
22. `exact URL "Beyond Page Objects: Next Generation Test Automation with Serenity and the Screenplay Pattern" infoq.com/articles/`
    (domain-targeted URL verification on `infoq.com`)
23. `exact URL "Stop using Page Objects and Start using App Actions" cypress.io/blog/`
    (domain-targeted URL verification on `cypress.io`)
24. `exact URL "Better Gherkin" cucumber.io/docs/bdd/better-gherkin/`
    (domain-targeted URL verification on `cucumber.io`)
25. `exact URL "Interaction tests" "Visual tests" storybook.js.org/docs/writing-tests/`
    (domain-targeted URL verification on `storybook.js.org`)
26. `exact URL "Snapshot testing" "Aria snapshots" playwright.dev/docs/aria-snapshots`
    (domain-targeted URL verification on `playwright.dev`)
27. `Leotta Ricca "Improving Test Suites Maintainability with the Page Object Pattern" 2013 ICSTW figures effort`
    (domain-targeted summarising fetch on `sepl.dibris.unige.it`)

**Pages opened (14 primary sources examined via domain-targeted
summarising fetches [1–14], plus 1 not used; direct `curl.exe` HTTP
fetch attempted once and denied by workspace sandbox policy):**
- `martinfowler.com/bliki/PageObject.html` [1]
- `selenium.dev/documentation/test_practices/encouraged/page_object_models/` [2]
- `infoq.com/articles/Beyond-Page-Objects-Serenity-Screenplay/` [3]
- `serenity-js.org/handbook/design-patterns/screenplay-pattern/` [4]
- `serenity-js.org/handbook/design-patterns/page-element-query-language/` [5]
- `cypress.io/blog/2019/01/03/stop-using-page-objects-and-start-using-app-actions/` [6]
- `cucumber.io/docs/bdd/better-gherkin/` [7]
- `testing-library.com/docs/queries/about/` [8]
- `playwright.dev/docs/pom` [9]
- `playwright.dev/docs/locators` [10]
- `playwright.dev/docs/test-snapshots` [11]
- `playwright.dev/docs/aria-snapshots` [12]
- `storybook.js.org/docs/writing-tests/` [13]
- `storybook.js.org/docs/writing-tests/interaction-testing` [14]
- `sepl.dibris.unige.it` (Leotta et al. 2013 summary; opened and not
  used)

**What the disconfirming queries found:**
- `"page object anti-pattern"` found five recurring failure modes in
  Page Object implementations: (1) embedding test assertions inside page
  objects [1, 2], (2) "God Page" classes that violate the Single
  Responsibility Principle by mixing element definitions and all user
  workflows for a complex screen instead of decomposing into component
  objects or Screenplay tasks [3, 4], (3) leaking raw element locators
  to test scripts, (4) rigid page-transition return chaining that breaks
  when modals or error states intervene, and (5) using slow UI Page
  Objects to set up state across prerequisite screens instead of using
  direct Application Actions or APIs [6].
- `"BDD UI tests brittle"` confirmed that executable specifications
  written in imperative, element-by-element steps (`When I type X into
  field Y and click button Z`) break on minor UI refactoring or flow
  changes, and that surviving specifications must be written
  declaratively at the level of user intent/tasks (`When the user logs
  in with valid credentials`) while binding elements at the lower layer
  via semantic accessibility roles and labels (`getByRole`) rather than
  DOM structure or CSS selectors [3, 7, 8, 10].

**Why the run ended:** Both parts of the card's stop rule were met:
every route in the card (original Page Object and Screenplay
descriptions, BDD/executable specifications, testing tools' abstraction
and locator guidance, and visual/structural verification) had primary
sources, differently worded queries returned no new structural patterns,
and the opening budget of ten to fifteen sources (14 used, 1 not used)
was reached.
