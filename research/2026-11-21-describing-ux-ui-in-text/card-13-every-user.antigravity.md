---
date: 2026-11-21
project: forge
topic: Accessibility, interface wording, and internationalisation in UI descriptions
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 13; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":50896,"output_tokens":17563,"thinking_tokens":7227,"cache_read_tokens":173722,"total_tokens":68459}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-13-every-user
status: immutable
---

# What the description of an interface owes every user across accessibility, interface wording, and internationalisation

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

A textual interface description prevents post-build rework only when it
specifies four non-visual contracts alongside layout: programmatic
semantics (role, accessible name, states, landmark region, and heading
level), interaction mechanics (sequential focus order, widget keyboard
bindings, focus destination after activation, and minimum 24x24 CSS
pixel pointer targets), deterministic interface wording (plain-language
labels, persistent hints instead of placeholders, and structured error
messages with hidden screen-reader prefixes), and string-level
internationalisation metadata (BCP 47 language tag, base direction,
bidirectional isolation for dynamic variables, non-concatenated message
templates, and layout expansion budgets). These requirements rest on
established W3C standards (WCAG 2.2, WAI-ARIA APG, `string-meta`, and
`international-specs`) and public design systems (GOV.UK, USWDS, and the
CVS Health/GitHub annotation toolkit), all examined here via summarised
fetches. The disconfirming queries confirmed the card's expectation:
there is no controlled empirical study measuring the defect-reduction
rate of design-time accessibility annotations, and existing evidence for
"shift-left" cost savings rests largely on vendor claims. The unexpected
finding is that W3C internationalisation guidance requires specifications
to separate machine-internal identifiers from human-readable strings and
to attach language and base-direction metadata directly to every natural
language string field rather than relying on document-level defaults or
runtime heuristics.

## Question

- **Card:** Card 13: What the description owes every user
- **Question:** What must a description of an interface carry so that
  accessibility, the wording in the interface and language versions are
  designed and not repaired: which accessibility properties are
  specified at design time (names, roles, states, focus order, keyboard,
  contrast, target sizes), how are the texts of the interface specified
  (content design, terminology), how is internationalisation prepared,
  and how do existing specification templates carry these?
- **Why it matters:** left out of the description they return as rework
  after the build, and accessibility is a legal duty in many markets.
- **What would answer it:** the standards themselves and their authors'
  guidance.
- **Where to look:** the web accessibility guidelines and the authoring
  practices for rich components; public accessibility annotation kits;
  content design guides of public administrations; the W3C's
  internationalisation guidance.
- **Known items:** None: the card names no known note of the project.
- **Disconfirming query:** "accessibility annotations do not work",
  "shift-left accessibility evidence"; expected: thin evidence either
  way.
- **Stop rule:** nothing new from a differently worded query and every
  route has a primary source; ten to fifteen pages opened.

To beat the baseline of generic advice ("make the UI accessible, write
clear copy, and support translation"), this note must identify the exact
properties, thresholds, and structural fields that standards and public
specification templates require at the technical specification stage
(design sense 2: the technical design between requirements and build
tasks), translating what visual mockups in a design tool (design sense
1) and component libraries in a design system (design sense 3) leave
implicit or carry only as visual stamps.

## Key findings

- **F1. Accessibility standards require seven categories of interface
  properties to be fixed before implementation: programmatic semantics
  (name, role, state/value), structural relationships (headings,
  landmarks, labels), keyboard operability, sequential focus order,
  unobscured focus visibility, minimum contrast ratios, and minimum
  pointer target sizes.** [consensus — standard; rests on summarised
  fetch of [1]]. In W3C's *Web Content Accessibility Guidelines (WCAG)
  2.2* (12 December 2024), Success Criterion (SC) 4.1.2 (*Name, Role,
  Value*, Level A) states that for all UI components, "the name and role
  can be programmatically determined; states, properties, and values
  that can be set by the user can be programmatically set" [1]. SC 1.3.1
  (*Info and Relationships*, Level A) requires that structure and
  relationships conveyed visually be programmatically determinable or in
  text, and SC 3.3.2 (*Labels or Instructions*, Level A) requires labels
  or instructions whenever content requires user input [1]. For
  navigation, SC 2.1.1 (*Keyboard*, Level A) requires all functionality
  to be operable through a keyboard interface; SC 2.4.3 (*Focus Order*,
  Level A) requires focusable components to receive focus in an order
  preserving meaning and operability; and SC 2.4.11 (*Focus Not Obscured
  (Minimum)*, Level AA) requires that a component receiving keyboard
  focus is "not entirely hidden due to author-created content" (such as
  sticky headers or modals) [1]. Visually and physically, SC 1.4.3
  (*Contrast (Minimum)*, Level AA) sets a 4.5:1 contrast ratio for
  normal text and 3:1 for large text; SC 1.4.11 (*Non-text Contrast*,
  Level AA) sets a 3:1 contrast ratio against adjacent colours for active
  UI component boundaries, state indicators, and graphical objects; and
  SC 2.5.8 (*Target Size (Minimum)*, Level AA) mandates that pointer
  inputs measure "at least 24 by 24 CSS pixels" unless exempted by a
  24-pixel spacing circle, inline text context, equivalent control, user
  agent default, or essential presentation [1]. WCAG 2.2 also adds flow-
  level requirements that belong to screen and flow specifications: SC
  3.2.6 (*Consistent Help*, Level A, requiring repeated help mechanisms
  to stay in the same relative page order), SC 3.3.7 (*Redundant Entry*,
  Level A, requiring previously entered session data to be auto-
  populated or selectable), and SC 3.3.8 (*Accessible Authentication
  (Minimum)*, Level AA, prohibiting cognitive function tests such as
  memorising passwords or solving puzzles unless an alternative or
  assistance mechanism is provided) [1].

- **F2. For composite or custom widgets, a specification must define an
  explicit keyboard-to-action mapping table, focus movement rules after
  activation, and dynamic ARIA state transitions.** [consensus —
  standard; rests on summarised fetches of [2], [3]]. The W3C *ARIA
  Authoring Practices Guide (APG)* patterns hub [2] and its component
  specifications such as the *Button Pattern* [3] structure every rich
  component specification into two normative behavioural blocks beyond
  visual description: *Keyboard Interaction* and *WAI-ARIA Roles,
  States, and Properties*. In the *Button Pattern*, the specification
  explicitly defines key bindings (`Space` and `Enter` activate the
  button) and four distinct post-activation focus rules depending on
  context: moving focus inside an opened dialog, returning focus to the
  trigger button when closing a dialog, retaining focus on the button
  for in-context actions (such as "Apply"), or moving focus to the
  starting point of a new context in a wizard [3]. It simultaneously
  specifies how accessible names are computed (`aria-label` or `aria-
  labelledby` when visible text is insufficient), how auxiliary
  descriptions bind via `aria-describedby`, how unavailability is
  signalled (`aria-disabled="true"`), and how stateful variants transition
  (`aria-pressed="true"` or `"false"` for toggle buttons) [3].

- **F3. Public accessibility annotation kits and design system templates
  operationalise standards at design time by annotating six structural
  layers that visual mockups omit: semantic headings, landmark regions,
  reading order, focus order, control semantics (link vs. button,
  accessible names, states), and form grouping/error wiring.** [consensus
  — practitioner claim and standard documentation; rests on summarised
  fetches of [6], [10], [11]]. The GitHub Annotation Toolkit—open-sourced
  in September 2025 under CC-BY-4.0 as a direct evolution of the CVS
  Health Inclusive Design team's *Web Accessibility Annotation Kit* [6]—
  and the U.S. Web Design System (USWDS) component accessibility test
  specifications [10] codify design-time (sense 1: interface design tool
  artefacts handed over as sense 2 technical specifications) annotations
  into repeatable categories. In these kits, designers specify: (a)
  programmatic heading levels (`H1`–`H6`) independent of visual font
  size; (b) landmark regions (`header`, `nav`, `main`, `aside`,
  `footer`); (c) screen-reader reading order where visual layout uses
  multi-column grids or CSS reordering; (d) sequential keyboard focus
  order and focus traps; (e) explicit accessible names, roles (marking
  whether an element is a navigation link or an action button), and
  states; and (f) form fieldset/legend groupings [6]. In USWDS (sense 3:
  design system documentation), component specifications pair build
  guidance with a structured verification checklist divided into
  *General tests* (visible labels and instructions, WCAG 3.3.2 and
  2.4.6), *Keyboard navigation tests* (visible focus outline, logical
  tab order, Space/Enter selection, WCAG 2.4.7, 2.4.3, 2.1.1), and
  *Screen reader tests* (announcing group question before individual
  item labels and checked state, matching visible text to accessible
  name under WCAG 4.1.2 and 2.5.3) [10].

- **F4. Public administration content design guides treat interface
  wording as an architectural specification: they prohibit placeholder
  text, mandate persistent sentence-case labels and hints, require
  action-specific button verbs, and enforce a deterministic structure
  and DOM wiring for validation errors.** [consensus — standard and
  public administration guidance; rests on summarised fetches of [7],
  [8], [9], [10]]. The GOV.UK Service Manual (*Writing for user
  interfaces*, updated April 2018) states: *"If you find yourself having
  to explain how the user interface works, that's a sign something has
  gone wrong. Fix the interface so it doesn't need explaining"* and
  mandates sentence case across all headings and input labels [7]. Both
  GOV.UK [7], [8] and the GOV.UK Design System [9], [10] specify strict
  rules for UI text elements:
  1. **Labels and hints:** Every input requires a persistent visible
     label; placeholder text inside inputs is avoided because it
     disappears on input and harms cognitive and screen-reader usability.
     Supplemental formatting guidance is placed in persistent hint text
     wired to the control via `aria-describedby` [9].
  2. **Buttons:** Primary action buttons appear once per page and use
     concise verbs stating the exact outcome (for example, "Continue" or
     "Save and continue") rather than generic labels like "Submit" [10].
  3. **Error messages:** Inline error messages must incorporate the
     words of the field's label, state plainly what went wrong and how
     to fix it, and forbid technical jargon ("form post error",
     "valid/invalid"), blame, humour ("oops"), and "please" or "sorry"
     [9]. Structurally, the GOV.UK Design System specifies exact DOM
     order (Label, Hint, Error Message, Form Control), prepends `"Error:
     "` to the page `<title>`, places a focusable Error Summary at the
     top of the page linking to each invalid field, wires the inline
     error ID into the input's `aria-describedby`, and prepends a
     visually hidden prefix (`<span class="govuk-visually-hidden">Error:</span>`)
     so screen readers announce *"Error: The date your passport was
     issued must be in the past"* [9].

- **F5. W3C internationalisation specifications require UI and data
  descriptions to attach explicit language and base-direction metadata
  to natural language strings, isolate dynamic bidirectional substrings,
  use non-concatenated positional templates with plural/gender rules,
  and budget layout space for text expansion and logical directional
  mirroring.** [consensus — standard; rests on summarised fetches of
  [4], [5]]. W3C's *Strings on the Web: Language and Direction Metadata*
  (`string-meta`, 17 October 2024) [4] and *Internationalization Best
  Practices for Spec Developers* (`international-specs`, 16 July 2026)
  [5] establish that:
  1. **Language and direction metadata:** Every natural language string
     requires determinable language (BCP 47 tag, mapped to WCAG 3.1.1
     and 3.1.2 [1]) and base direction (`ltr`, `rtl`, or `auto`), which
     must be kept independent because a language can be written in
     multiple scripts or directions, and must not rely on fragile
     first-strong character heuristics [4], [5].
  2. **Bidirectional (bidi) isolation:** Dynamic variables (such as user
     names, file paths, or numbers) injected into translated sentences
     must be directionally isolated (in HTML via `<bdi>` or explicit
     `dir` attributes rather than raw Unicode control characters) to
     prevent spillover corruption in right-to-left (RTL) scripts [4],
     [5].
  3. **Non-concatenation and culturally neutral schemas:** Strings must
     never be concatenated from substrings in code; specifications must
     use full-sentence templates with positional parameters, plural/
     gender grammar rules, translator context notes, locale-neutral ISO
     serialisation for dates/times/numbers, and culturally neutral form
     schemas (such as "Given name(s)" / "Family name(s)" without rigid
     character limits instead of "First name" / "Last name") [5].
  4. **Layout expansion and logical geometry:** Container specifications
     must avoid fixed pixel widths to accommodate 30%–50% text expansion
     when translating from English to languages such as German or
     Russian, and must specify geometry using logical flow properties
     (`inline-start` / `inline-end`) rather than physical (`left` /
     `right`) coordinates so RTL interfaces mirror without layout rewrites
     [5].

- **F6. Evidence that design-time accessibility annotations reduce post-
  build defects is thin: quantitative ROI figures in industry circulate
  as unverified vendor claims, while academic HCI literature highlights
  persistent training gaps and handoff friction between visual annotations
  and developer workflows.** [contested / thin evidence — vendor report
  vs. workshop study; rests on summarised fetches of [12] and search
  summaries]. The disconfirming queries found no controlled empirical
  trial measuring defect rates with versus without design-time
  accessibility annotations. Quantitative claims in industry—such as a
  "67% cost reduction" from shifting accessibility left—originate in
  vendor marketing pages (such as TestParty and Siteimprove) adapting
  general software-engineering bug-cost multipliers rather than measured
  accessibility annotation studies. Conversely, academic research such
  as Parthasarathy et al. (September 2025) [12] documents a persistent
  foundational training gap in accessibility practices among software
  professionals and educators, and HCI handoff literature notes that
  when accessibility annotations live as detached visual stamps on a
  canvas rather than structured component requirements, developers
  frequently overlook them under sprint velocity pressures.

## Unexpected

The card frames internationalisation primarily around preparing the UI
for "language versions" (translation of interface copy). W3C's
*Strings on the Web: Language and Direction Metadata* [4] and
*Internationalization Best Practices for Spec Developers* [5]
reconfigure this assumption: in a specification, internationalisation is
first a data-typing separation between machine-internal identifiers
(enumerated values, keys, tokens, which must be marked locale-neutral or
`zxx` for non-linguistic content) and human-readable display strings,
where every natural language field (even in a single-language
application that accepts user input or displays names) must carry a
tuple of `(string, language, base_direction)` so mixed-script and
bidirectional user data do not corrupt the interface layout [4], [5].

## Not found

- **Controlled empirical studies measuring the defect-reduction rate of
  accessibility annotation kits:** Looked for in ACM CHI, ASSETS, and
  arXiv (`arxiv.org`) using queries for `"accessibility annotations" UX
  design handoff study CHI ASSETS paper empirical developers ignore OR
  fail` and `"shift-left accessibility evidence"`. While general UX-to-
  developer handoff studies and accessibility education workshops [12]
  exist, no controlled experiment comparing code accessibility compliance
  with and without design-time annotation kits was found.
- **A single unified specification template covering accessibility,
  content design, and internationalisation together:** Looked for across
  W3C, GOV.UK, USWDS, and public Figma annotation toolkits [1], [5],
  [6], [7], [11]. In practice, these three concerns are split across
  separate artefacts (visual annotation stamps for accessibility [6],
  style/component guides for content design [7], [9], and i18n developer
  checklists for localisation [5]).

## Options

When designing the textual UX/UI specification format (design sense 2)
for the `forge` framework, there are three distinct ways to carry
accessibility, wording, and internationalisation requirements:

1. **Option A: Inline element-level and screen-level fields (Embedded
   Contract).** Every element definition in Markdown carries mandatory
   structured fields for its role, accessible name source, dynamic
   states, keyboard bindings, target-size floor, exact copy (label,
   hint, error message with problem + fix), translator context, and
   string direction/isolation rules; every screen definition carries
   landmark structure, heading hierarchy (`H1`–`H6`), sequential focus
   order, post-action focus destinations, and layout expansion rules.
   - *Trade-offs:* Eliminates cross-document lookup for human developers
     and AI coding agents and makes missing properties immediately
     visible during agent-human review; increases per-element verbosity
     unless standard design-system defaults (design sense 3) can be
     inherited by reference.
2. **Option B: Separate annex or overlay tables per screen (Visual-
   Annotation Mirror).** Keep element and screen descriptions focused on
   layout and functional behaviour, and attach a separate "Accessibility,
   Copy, and i18n Annex" table at the bottom of the document (mirroring
   how visual Figma annotation layers sit on top of mockups in design
   sense 1).
   - *Trade-offs:* Keeps the primary layout description shorter to read;
     reproduces the exact fragmentation hazard identified in handoff
     research, where developers or coding agents implement the layout
     first and treat the annex as an optional afterthought.
3. **Option C: Inheritance from a component baseline plus inline delta
   overrides (Hybrid Contract).** Define standard WCAG 2.2 AA baselines
   (4.5:1 text contrast, 3:1 non-text contrast, 24x24px target size,
   logical CSS properties, `bdi` isolation on dynamic variables) and
   standard WAI-ARIA APG keyboard/role patterns once at the application
   or design-system level (sense 3), and require every element and
   screen definition in the technical specification (sense 2) to declare
   only context-specific values: heading level, landmark container,
   sequential tab index/focus order, post-activation focus target, exact
   interface strings (label, persistent hint, error message), string
   expansion budget, and translator notes.
   - *Trade-offs:* Minimises repetitive boilerplate while keeping all
     context-dependent accessibility, content design, and i18n decisions
     bound directly to the element and screen being built; requires a
     well-defined baseline contract that the build agent reads alongside
     the screen specification.

## Relevance to this project

**Recommendation:** Adopt **Option C (Inheritance from a component
baseline plus inline delta overrides)** for the `forge` textual UI
specification format. Specifically, (Inference) because `forge` passes
versioned Markdown documents to human developers and AI coding agents
without relying on a visual canvas, the textual specification itself is
the only place where non-visual semantics, wording, and i18n rules can
live. Relying on post-build testing or detached annexes (Option B)
invites the rework the card warns against, whereas repeating static WCAG
ratios and standard APG key tables on every button (Option A) bloats the
Markdown and obscures screen-specific logic.

Under Option C, the `forge` UI specification should enforce:
1. **An application-wide baseline contract** locking in WCAG 2.2 AA
   visual/physical floors (4.5:1 text contrast, 3:1 UI/graphical
   contrast, 24x24 CSS px minimum target size, unobscured focus under SC
   2.4.11) [1], WAI-ARIA APG standard widget keyboard tables [2], [3],
   and W3C `string-meta` / `international-specs` defaults (logical CSS
   properties, `<bdi>` isolation on all interpolated variables, no
   string concatenation, locale-neutral internal enums) [4], [5].
2. **Mandatory screen-level fields** for: document `<title>` (including
   its `"Error: "` prefix state [9]), landmark region tree (`header`,
   `nav`, `main`, `aside`, `footer`), heading hierarchy (`H1`–`H6`)
   independent of visual typography, sequential focus and reading order
   across regions, flow-level accessibility rules (consistent help
   placement under SC 3.2.6, session data auto-population under SC
   3.3.7, and cognitive-test-free authentication under SC 3.3.8) [1],
   [6], and container expansion rules for 30%–50% translated string
   growth [5].
3. **Mandatory element-level fields** for: semantic role (explicitly
   distinguishing navigation link vs. action button [6]), accessible
   name (either bound to visible label or explicit `aria-label` when
   icon-only [1], [3]), dynamic state mappings (`aria-expanded`, `aria-
   pressed`, `aria-disabled` [3]), focus target after activation [3],
   and a structured copy block containing the sentence-case label,
   optional persistent hint text (forbidding placeholders), actionable
   error message template (with visually hidden `"Error:"` prefix and
   `aria-describedby` binding) [7], [9], plural/gender parameter notes,
   and translator context [5].

**Consult when:** Designing the schema or template for screen and
element definitions in the UX/UI Markdown document; defining the prompts
and checklists used by the proposing AI agent to interview the human
author about a screen; or writing the acceptance criteria generator that
hands the UI description to a developer or coding agent.

## Sources

1. *Web Content Accessibility Guidelines (WCAG) 2.2*, Alastair Campbell,
   Chuck Adams, Rachael Bradley Montgomery, Michael Cooper, and Andrew
   Kirkpatrick (Editors), W3C (World Wide Web Consortium), 2024-12-12
   (dated by structured data / W3C document header),
   https://www.w3.org/TR/WCAG22/ ; primary (read via summarised fetch,
   which is a tertiary mode of access: editors and verbatim text of SC
   1.3.1, 1.4.3, 1.4.11, 2.1.1, 2.4.3, 2.4.11, 2.5.8, 3.1.1, 3.2.6,
   3.3.2, 3.3.7, 3.3.8, and 4.1.2); original.
2. *Design Patterns and Widgets – ARIA Authoring Practices Guide (APG)*,
   W3C Web Accessibility Initiative (WAI), undated (living W3C Working
   Group Note resource), https://www.w3.org/WAI/ARIA/apg/patterns/ ;
   primary (read via summarised fetch: pattern index and standard pattern
   structure); original.
3. *Button Pattern – ARIA Authoring Practices Guide (APG)*, W3C Web
   Accessibility Initiative (WAI), undated (living W3C Working Group Note
   resource), https://www.w3.org/WAI/ARIA/apg/patterns/button/ ; primary
   (read via summarised fetch: *Keyboard Interaction* and *WAI-ARIA
   Roles, States, and Properties* sections); original.
4. *Strings on the Web: Language and Direction Metadata*, Addison
   Phillips and Richard Ishida (Editors), W3C Internationalization
   Working Group, 2024-10-17 (dated by W3C document header),
   https://www.w3.org/TR/string-meta/ ; primary (read via summarised
   fetch: *Abstract* and recommendations on language tags, base
   direction, `zxx`/`und`, and heuristics); original.
5. *Internationalization Best Practices for Spec Developers*, W3C
   Internationalization Working Group, 2026-07-16 (dated by W3C document
   header), https://www.w3.org/TR/international-specs/ ; primary (read
   via summarised fetch: *Abstract* and checklist sections on strings,
   language/direction metadata, localization, logical properties, dates,
   and personal names); original.
6. *Open sourcing the GitHub Annotation Toolkit*, GitHub, 2025-09-22
   (dated by byline and URL),
   https://github.blog/changelog/2025-09-22-open-sourcing-the-github-annotation-toolkit/
   ; primary (vendor documentation of its own open-source toolkit; read
   via summarised fetch: attribution to CVS Health Inclusive Design team
   and annotation categories); original.
7. *Writing for user interfaces*, Government Digital Service (GOV.UK
   Service Manual), 2018-04-16 (published 2017-10-10, last updated
   2018-04-16, dated by page metadata/byline),
   https://www.gov.uk/service-manual/design/writing-for-user-interfaces
   ; primary (read via summarised fetch: table of contents and verbatim
   guidelines under *Think about alternatives before you add more
   words*, *Keep copy short and direct*, and *Style*); original.
8. *Writing for GOV.UK (Content design: planning, writing and managing
   content)*, Government Digital Service (GOV.UK), 2016 (dated by page
   metadata),
   https://www.gov.uk/guidance/content-design/writing-for-gov-uk ;
   primary (read via summarised fetch: headings and core writing
   principles); original.
9. *Error message – GOV.UK Design System*, Government Digital Service,
   undated,
   https://design-system.service.gov.uk/components/error-message/ ;
   primary (read via summarised fetch: wording rules, DOM hierarchy,
   `aria-describedby` wiring, and verbatim screen reader hidden-prefix
   guidance); original.
10. *Button – GOV.UK Design System*, Government Digital Service,
    undated, https://design-system.service.gov.uk/components/button/ ;
    primary (read via summarised fetch: usage and wording guidance);
    original.
11. *Checkbox accessibility tests*, U.S. Web Design System (USWDS), U.S.
    General Services Administration, undated,
    https://designsystem.digital.gov/components/checkbox/accessibility-tests/
    ; primary (read via summarised fetch: *General tests*, *Keyboard
    navigation tests*, and *Screen reader tests* checklists and WCAG
    mappings); original.
12. *Scaling Accessibility Education: Reflections from a Workshop
    Targeting CS Educators and Software Professionals*, PD
    Parthasarathy, Anshu M Mittal, and Swaroop Joshi, arXiv, 2025-09
    (dated by arXiv submission metadata),
    https://arxiv.org/abs/2509.22759 ; primary (read via summarised
    fetch: title, authors, and *Abstract*); original.

## Opened and not used

- *ARIA Authoring Practices Guide (APG) Index by Roles, States, and
  Properties* (https://www.w3.org/WAI/ARIA/apg/index/): superseded by
  [2] and [3], which directly show how widget patterns structure roles,
  states, and keyboard interactions.

## Search record

**Queries run (in order):**
1. `WCAG 2.2 WAI-ARIA authoring practices guide accessibility properties name role value focus order target size contrast`
2. `accessibility annotation kit design handoff specification template CVS Health Intopia Deque`
3. `GOV.UK content design planning writing managing content interface wording specification`
4. `W3C internationalization techniques authoring HTML UI specification string translation layout expansion bidi`
5. `accessibility annotations do not work` (disconfirming query 1)
6. `shift-left accessibility evidence` (disconfirming query 2)
7. `"Web Content Accessibility Guidelines (WCAG) 2.2" exact URL publication date 4.1.2 2.4.3 2.5.8 1.4.3 1.4.11 3.2.6 3.3.7 3.3.8 verbatim text` (`domain: w3.org`)
8. `"ARIA Authoring Practices Guide (APG)" w3.org/WAI/ARIA/apg/ patterns keyboard interaction roles states properties exact URL date` (`domain: w3.org`)
9. `"Strings on the Web: Language and Direction Metadata" OR "Internationalization Best Practices for Spec Developers" w3.org/TR/ exact URL date verbatim` (`domain: w3.org`)
10. `"Setting the standard for accessibility annotations" OR accessibility annotation kit CVS Health GitHub exact URL author date verbatim` (`domain: github.blog`)
11. `"Content design: planning, writing and managing content" OR "Service Manual" content design interface wording exact URL date verbatim` (`domain: gov.uk`)
12. `error message label hint text button accessibility wording specification exact URL verbatim` (`domain: design-system.service.gov.uk`)
13. `"accessibility annotations" UX design handoff study CHI ASSETS paper empirical developers ignore OR fail`
14. `accessibility test status component guidance content specification USWDS exact URL date` (`domain: designsystem.digital.gov`)
15. `"Web Content Accessibility Guidelines (WCAG) 2.2" editors "1.3.1 Info and Relationships" "2.1.1 Keyboard" "2.4.11 Focus Not Obscured" "3.1.1 Language of Page" "3.3.2 Labels or Instructions" verbatim text` (`domain: w3.org`)
16. `"ARIA Authoring Practices Guide" "w3.org/WAI/ARIA/apg/patterns/button/" OR "w3.org/WAI/ARIA/apg/patterns/" editors title verbatim "Keyboard Interaction" "WAI-ARIA Roles, States, and Properties"` (`domain: w3.org`)
17. `"Strings on the Web: Language and Direction Metadata" "w3.org/TR/string-meta/" AND "Internationalization Best Practices for Spec Developers" "w3.org/TR/international-specs/" editors abstract verbatim text` (`domain: w3.org`)
18. `"https://github.blog/changelog/2025-09-22-open-sourcing-the-github-annotation-toolkit/" full text verbatim quotes CVS Health categories stamps` (`domain: github.blog`)
19. `"https://www.gov.uk/service-manual/design/writing-for-user-interfaces" AND "https://www.gov.uk/guidance/content-design/writing-for-gov-uk" exact title dates headings verbatim quotes` (`domain: gov.uk`)
20. `"https://design-system.service.gov.uk/components/error-message/" AND "https://design-system.service.gov.uk/components/button/" exact title headings verbatim quotes` (`domain: design-system.service.gov.uk`)
21. `"w3.org/TR/string-meta/" AND "w3.org/TR/international-specs/" editors section headings verbatim quotes language direction expansion concatenation` (`domain: w3.org` — tool error, no candidates returned)
22. `"https://designsystem.digital.gov/components/checkbox/accessibility-tests/" exact title headings verbatim quotes keyboard screen reader zoom` (`domain: designsystem.digital.gov`)
23. `"https://github.blog/changelog/2025-09-22-open-sourcing-the-github-annotation-toolkit/" OR "Web Accessibility Annotation Kit" CVS Health categories headings landmarks reading order focus order verbatim`
24. `"accessibility" "design" "handoff" OR "annotations" UX developers CHI ASSETS exact arxiv URL title authors year abstract verbatim` (`domain: arxiv.org`)
25. `Strings on the Web Language and Direction Metadata string-meta editors recommendations language directionverbatim` (`domain: w3.org`)
26. `Internationalization Best Practices for Spec Developers international-specs editors checklist strings localization layout` (`domain: w3.org`)
27. `accessibility annotations design.va.gov headings landmarks reading order focus order exact URL title verbatim` (`domain: va.gov`)

**Pages opened (13 unique primary pages examined via targeted `search_web`
summarised fetches; direct `curl` was blocked by environment sandbox
policy):**
1. https://www.w3.org/TR/WCAG22/ [1]
2. https://www.w3.org/WAI/ARIA/apg/patterns/ [2]
3. https://www.w3.org/WAI/ARIA/apg/index/ (opened and not used)
4. https://www.w3.org/WAI/ARIA/apg/patterns/button/ [3]
5. https://www.w3.org/TR/string-meta/ [4]
6. https://www.w3.org/TR/international-specs/ [5]
7. https://github.blog/changelog/2025-09-22-open-sourcing-the-github-annotation-toolkit/ [6]
8. https://www.gov.uk/service-manual/design/writing-for-user-interfaces [7]
9. https://www.gov.uk/guidance/content-design/writing-for-gov-uk [8]
10. https://design-system.service.gov.uk/components/error-message/ [9]
11. https://design-system.service.gov.uk/components/button/ [10]
12. https://designsystem.digital.gov/components/checkbox/accessibility-tests/ [11]
13. https://arxiv.org/abs/2509.22759 [12]

**What the disconfirming query found:**
- `"accessibility annotations do not work"` returned technical
  troubleshooting documentation (such as hidden annotation layers in
  Figma Dev Mode, mobile `isAccessibilityElement` container conflicts in
  iOS/Android, and PDF tag-tree omissions) rather than empirical studies
  evaluating design-time annotations. A follow-up query targeting CHI
  and ASSETS HCI literature (`"accessibility annotations" UX design
  handoff study CHI ASSETS paper empirical developers ignore OR fail`)
  surfaced qualitative workflow friction (annotations ignored when
  detached from component code or deprioritised under sprint pressure)
  and training gaps [12], but no controlled study measuring annotation
  efficacy.
- `"shift-left accessibility evidence"` returned vendor blog claims
  (such as a "67% cost reduction" cited by accessibility testing vendors
  extrapolating from general NIST/IBM software bug-cost curves) rather
  than peer-reviewed empirical audits, confirming the card's expectation
  of thin evidence either way.

**Reason the run ended:** Both parts of the card's stop rule were met at
13 unique pages opened (within the 10-to-15-page budget): every route in
the card ("web accessibility guidelines and the authoring practices for
rich components; public accessibility annotation kits; content design
guides of public administrations; the W3C's internationalisation
guidance") had at least one verified primary source, and differently
worded queries returned no new specification categories.
