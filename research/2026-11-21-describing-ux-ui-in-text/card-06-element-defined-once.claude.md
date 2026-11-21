---
date: 2026-11-21
project: forge
topic: an element defined once - component specifications, patterns and templates, design tokens, description kept true to the implementation
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-06-element-defined-once
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 6; no known note named by the card; web sources below
---

# Mature design systems define a component once, apart from any screen, and keep that definition true to the build only where a machine generates or checks it

<!-- Shape: templates/research.md -->

## In short

Mature design systems do define a component once, apart from any
screen, and the parts the card lists (anatomy, variants, properties,
states, behaviour, accessibility, rules of content) recur across a
vendor's component page, a public administration's content template,
a practitioner's specification and a community group's template, with
additions the card does not name: when to use and when not, research
and known issues, internationalisation, a version history. The
description is, however, two documents and not one: how to make the
component and how to use it, kept by different people. Patterns and
page templates are compositions a level above the component, in the
vocabulary of atomic design; visual decisions are named tokens in
tiers, and their exchange format reached a stable community report on
28 October 2025. There is no standard for the component specification
itself: the W3C group formed for it in August 2025 was closed on 21
May 2026 with no report listed. The disconfirming query confirmed
that drift is a known trouble and qualified the second half of what
was expected: what is generated from code is the reference of
properties and the examples, not the guidance, which is written by
hand wherever it was seen. Sureness is moderate: every page was read
through a summarising fetch with short verbatim quotes, the large
vendors are represented by two systems only, and the survey figures
are of 2022. The unexpected thing: in atomic design the frame's own
example, a search field, is not one element but a composition of
three.

## Question

The card, verbatim:

> **Card 6: An element defined once**
> - **Question:** How do mature design systems describe one component
>   so that it is defined once and used on many screens (the parts of
>   a component specification: anatomy, variants, properties, states,
>   behaviour, accessibility, rules of content), how are patterns and
>   page templates built from components, how are visual decisions
>   recorded as design tokens, and what do the maintainers say about
>   keeping the description and the implementation the same?
> - **Why it matters:** it tests the first half of the idea of small
>   definitions: an element with a definition of its own that carries
>   its function.
> - **What would answer it:** the design systems' own documentation
>   and their maintainers' writing.
> - **Where to look:** the public design systems of large vendors and
>   of public administrations; writing on component specifications;
>   atomic design; the design tokens format of the W3C community
>   group; documentation tools that render components in isolation.
>   Search words from card 1: "design tokens format module",
>   "component specification", "anatomy, states, variants"; the W3C's
>   UI Specification Schema Community Group of 2025 and 2026 and Open
>   UI. Primary artefacts in public repositories (schemas, component
>   and page files, agents' rules and prompt files, the schemas of
>   servers for design tools, issue trackers) before commentary about
>   them.
> - **Disconfirming query:** "design system documentation drift",
>   "component specification out of date"; expected: drift is a known
>   trouble and documentation is generated from code.
> - **Stop rule:** nothing new from a differently worded query and
>   every route has a primary source; ten to fifteen pages opened.

The frame, in the excerpt this card tests: "One idea heard from
practice is to be tested, not assumed: every element of a screen (a
search field, say) has a small definition of its own in Markdown that
carries its function, and a page definition names which elements it
holds and where they stand."

What the note must beat: the common account, repeated across the
search results, that a component page lists anatomy, variants, states,
properties and accessibility and that drift is cured by generating
the documentation from code. The note has to say from the systems'
own artefacts which parts recur and which do not, what a
machine-readable definition of one component carries, and what the
maintainers themselves say can and cannot be kept the same.

## Key findings

How the findings were read: every page was opened through a fetch
tool that passes the page to a small model and returns its answer;
verbatim quotes were asked for and came back short. Every finding
below therefore rests on summarised fetches of the publishers' own
pages, and a quote is as that tool returned it. "Design system" here
is the third sense of the frame, a library of components, tokens and
guidance; where the first sense is meant the note says "design tool".

**F1. A component is described once, apart from any screen, in a set
of parts that recurs across unlike sources; the card's list holds,
with additions.** [consensus; vendor documentation [1], practitioner
article [2], community group's template [3], vendor's draft schema
[4], a public administration's team post [5], survey [14]; by
summarised fetch]

| Part | Vendor's component page [1] | Practitioner's spec [2] | Open UI template [3] | Draft JSON declaration [4] | Public administration's page [5] |
|---|---|---|---|---|---|
| Purpose, when to use and when not | Overview: When to use, When not to use | left to guidelines, not the spec | Overview, Use Cases, Non-goals | `description` | what it is, when to use it, when not to use it |
| Anatomy, the named parts | Formatting: Anatomy | Anatomy | Anatomy: diagram, DOM structure, slots, CSS parts | `anatomy`, `slots` | not named |
| Variants and properties | Overview: Variants; Button sizes; Modifiers | Properties | APIs: properties and attributes, methods, events | `options` | not named (in the code repository: `params` [6]) |
| States | Universal behaviors: States | under Behavior, the state an event changes | States and Interactions | `states` | not named (named examples per state [6]) |
| Behaviour | Universal behaviors: Interactions by mouse and keyboard, Loading | Behavior, Motion | States and Interactions | no field | how it works |
| Accessibility | a tab of its own | Accessibility | Accessibility: keyboard and focus, form input, assistive technology | `accessibility` | not named |
| Rules of content | Content: button label, overflow content | no section of its own | none | none | not named |
| Internationalisation | Content: Internationalization (RTL) | none | Globalization | none | not named |
| Layout and spacing | Formatting: alignment, button groups | Layout and spacing | Appearance | no field | not named |
| Tokens | not on the tab opened | Component tokens | none | a separate relationships file | none |
| Evidence and history | status "Stable", Feedback | Version history | Prior Art, Resources | `lifecycle` | research, "Known issues" |

"Not named" means the source opened does not name it, not that the
system lacks it. The anatomy is defined alike in [2], "An anatomy
breaks down a component into parts, itemizes and names each one"
(section What specs include), and in [3], "Outline the component's
structure with a diagram of its render tree" (section Anatomy). The
states are asked for in [3] as "List key component states, valid
state transitions, and how interactions trigger state transitions"
(section States and Interactions). What the card's list lacks and the
sources carry: when to use and when not ([1], [5]; in [3] as use
cases and non-goals); the research behind a component and its known
issues [5]; internationalisation ([1], [3]); slots, the named places
where content is put in ([3], [4]); a version history or a lifecycle
([2], [4]). The rule of content is the weakest part in practice: of
219 systems surveyed in 2022, 85% had component documentation, 57%
accessibility guidelines and 45% content guidelines [14]. None of
the five, as far as the headings and fields returned show, says where
a component stands on a named screen; [1] gives general rules of
alignment and grouping only.

**F2. The description of one component is two documents with two
purposes, how to make it and how to use it, and the sources keep them
apart.** [consensus among the sources opened; practitioner claim
[2][13], vendor documentation [1], team post [5], template [3]; by
summarised fetch] The practitioner writes: "Specs are largely
concerned with how to make a component, not how to use a component in
practice" (section Specs ≠ Design guidelines [2]). The vendor's page
separates a Guidelines tab from a Specifications tab and sends the
reader across: "The default and interactive states of buttons should
follow the button Specifications tab guidelines" (section States
[1]). The public administration's content template is about use
alone: "what it is", "when to use it", "when not to use it", "how it
works", "research" [5]. The Open UI template addresses the developer
who writes the component [3]. In 2026 the same practitioner says
specifications cover the making, while tables of properties and the
documentation of use come from code and are another team's work
(section "From specs to docs? Some, but not much" [13], paraphrased
by the fetch).

**F3. Machine-readable definitions of one component exist in public
repositories, as JSON and as YAML, and they carry the surface that
can be enumerated, not the guidance.** [emerging; primary artefacts:
a vendor's draft schema [4], a public administration's data file [6],
a community schema [7]; by summarised fetch] The draft of [4],
marked "Draft Specification (v1.0.0-draft)" with the notice that
"Normative text and schemas may change before the stable 1.0.0
release", declares one component as a JSON object: required `$id`
("Canonical identifier for this component declaration"), `name`,
`displayName`, `meta`; optional `specVersion`, `description`,
`implementations`, `options`, `slots`, `anatomy`, `states`,
`lifecycle`, `documentBlocks`, `accessibility`; any other field "MUST
cause a Layer 1 schema error". Its stated use is to check the names
of tokens (their component, variant, anatomy and state fields)
against what the component declares, so that a token naming an
unknown variant is caught; the tokens themselves are bound in a
separate file per component. The data file of [6] sits in the
component's own source folder and has two keys: `params`, twelve for
the button, each with name, type, required and description, and
`examples`, thirty-eight, named after variants and states ("default
hover state", "disabled", "secondary"). The schema of [7] is "A file
format for describing custom elements", at version 2.1.0 dated
2024-05-06, written because "Many tools need some machine-readable
descriptions of custom elements": editors, viewers of documentation
and demos, linters, framework wrappers, catalogues, tests of a
changed public interface. In none of the three does a field hold when
to use the component or its rules of content; [4] reserves prose for
`documentBlocks`, which the page marks as a later phase.

**F4. Patterns and page templates are compositions named a level
above the component; the shared vocabulary is atomic design's five
levels, and a public design system publishes templates as
combinations of components.** [consensus on the layering;
practitioner's book [8], a public administration's documentation [9],
team post [5]; by summarised fetch] The book defines molecules as
"relatively simple groups of UI elements functioning together as a
unit", organisms as "relatively complex UI components composed of
groups of molecules and/or atoms and/or other organisms", templates
as "page-level objects that place components into a layout" that
"focus on the page's underlying content structure rather than the
page's final content", and pages as "specific instances of templates
that show what a UI looks like with real representative content in
place" (chapter 2 [8]). Variation is said at the level of the page:
"Pages also provide a place to articulate variations in templates."
The book warns twice against reading the levels as steps: "atomic
design is not a linear process" and "It would be foolish to design
buttons and other elements in isolation." A federal design system's
templates "represent common component combinations", are "a mix of
components — some modified — and utilities", and are five: a 404
page, a documentation page, a landing page, authentication pages and
form templates [9]; the words "some modified" say that a component
defined once is not always used unchanged. The other public
administration documents a pattern in the same content template as a
component and names a pattern by what it does, "check answers" [5].

**F5. Visual decisions are recorded as named tokens in tiers, and
the format for exchanging them reached a stable community report in
October 2025.** [standard of a community group, not a W3C Standard
[10]; vendor documentation [11]; practitioner claim [2]; survey [14];
by summarised fetch, [10] read to its section 9.6] The report
"Design Tokens Format Module 2025.10" is a "Final Community Group
Report" of 28 October 2025, "considered stable" and, by its own
status section, not a W3C Standard [10]. It defines a token as
"information associated with a human readable name, at minimum a
name/value pair" (section 3.1), in JSON, with properties that all
begin with a dollar sign: `$value`, `$type`, `$description` ("A plain
text description explaining the token's purpose", section 5.2.1),
`$extensions`, `$deprecated`. Tokens are grouped ("a set of tokens
belonging to a specific category", section 3.7), may refer to one
another ("A design token's value can be a reference to another
token", section 3.8) and may be composite ("made up of multiple,
named child values", section 3.9). The types read were color,
dimension, fontFamily, fontWeight, duration, cubicBezier and number,
and the composites strokeStyle, border, transition and shadow;
gradient and typography were seen in the table of contents only. The
media type is `application/design-tokens+json` and the recommended
file extensions `.tokens` and `.tokens.json` (sections 4.1, 4.2). A
vendor's design system calls tokens "a methodology for expressing
reusable design decisions as structured data" and names three tiers:
"Primitive tokens define the available values in the design
language", "Semantic tokens define how design decisions are used
throughout the system", "Component-specific tokens represent design
decisions that apply to a specific component or implementation"; an
alias is "A token that references another token instead of a final
value", and the foundational tokens are "the source of truth across
products, platforms, and implementations" [11]. The practitioner's
specification records which tokens a component's parts take: "Specs
document those mappings" (section Why specs matter [2]). Of 219
systems surveyed in 2022, 69% had design tokens [14].

**F6. Divergence between the description and the implementation is a
standing trouble by the maintainers' own account; what stays the same
without effort is what a machine generates or checks, and in the
systems opened that is the reference of properties and the examples,
never the guidance.** [drift as a trouble: consensus, a consultancy's
survey [14] and practitioner claim [2][13]; generation and checking:
vendor documentation [12] and primary artefacts [4][6][7]; the limit
of generation: single practitioner source [13] with the agent's own
reading of [1], [5] and [12]; by summarised fetch]

- The survey of 2022 [14]: among maintainers (162 answers) "Parity
  between design & code" is a challenge for 37%, second after
  technical and creative debt at 43%; among those who use a system
  (31 answers, a small group) "It's documented poorly" 39%, "It's
  unclear what is old, broken, or coming soon" 35%, "It's out of
  date" 19%. The survey asks nothing about how documentation is made.
- The practitioner in 2023 [2]: "Component specs usually aren't
  handed off once"; they are kept through a redesign and adjusted as
  the component is built for several code platforms, with a version
  added "each time a branch is merged that changes the specs". The
  specification there is one file in the design tool, one component
  to a page, edited by few.
- The documentation tool [12], at its version 10.6: a page is
  generated from what the tool "infers", "the relevant metadata
  (e.g., args, argTypes, parameters)", the aim being "transforming
  your stories into living documentation"; for anything beyond it:
  "We recommend combining MDX alongside Storybook's Doc Blocks for
  such cases to author your documentation", which is writing by hand.
- The artefacts of F3: [6] keeps properties and named examples as
  data in the component's source folder; [7] names the detection of
  a changed public interface among its uses; [4] checks instead of
  generating, failing any field the schema does not know.
- The practitioner in 2026 [13] calls specifications a place that
  "normalizes, synchronizes, and versions the intent expressed across
  the many origins-of-truth", and of the single source of truth: "To
  many, that probably sounds like THE source-of-truth. Well, kinda."
  He favours "generated over authored", prefers deterministic scripts
  because "imprecision and loss through inference is inevitable",
  tests a round trip from specification to the design tool and back
  for identical output, and says "the edges are where it gets hard".
- The public administration in 2018 [5] describes no procedure that
  keeps the guidance in line with the code. It answers with candour
  instead: a "Known issues" heading, a link from each page to an
  issue in a public backlog, and "Being honest about gaps is the
  first step to filling them."

The card expected "drift is a known trouble and documentation is
generated from code". The first half held. The second held in part:
generated are the tables of properties and the examples; the guidance
of [1] and [5], and whatever [12] sends to hand-written pages, is
authored. That reading of [1], [5] and [12] is the agent's own.

**F7. No standard exists for the specification of a component: the
W3C group formed for it in 2025 was closed in May 2026 and lists no
report.** [single source, the group's own page at the W3C [15], with
[3] and [10]; by summarised fetch] The UI Specification Schema
Community Group was proposed on 2025-08-11 and launched with a call
for participation dated 13 August 2025, its one post. Its mission
was "a common, implementation-agnostic meta-model for specifying the
design, layout, behaviour, and constraints" of interface components,
with the tasks to "Produce and maintain a formal schema (JSON/JSON
Schema) for authoring and validating per-instance specifications" and
to "Align vocabulary with related W3C efforts such as Open UI
(anatomy, states, variants)". The page says "This group was closed
on 2026-05-21", names no chair ("The group must now choose a chair")
and lists no report, draft or repository [15]. Open UI's template for
specifying a component shows "Last Updated" 2023-10-31 and is a
template for proposals, not a format [3]. The one stable report in
this field covers tokens alone [10].

**F8. A newer current puts a structured specification between the
design tool and the code, generated more than written, and read by
agents as well as by people.** [emerging; single practitioner source
[13] and one vendor's draft [4]; by summarised fetch] In [13], dated
Aug 14, 2026, specifications are extracted from the design tool
through its plugin and REST interfaces into one file per component
holding the interface (names, properties, elements), the variants as
"layered rules (much like CSS)" and examples; requirements that
cannot be extracted are written beside them in Markdown files (the
article names "configurations.md" and
"card.accessibility.android.md"), often worded with "MUST, SHOULD,
COULD"; engineers' tooling and agents consume them to produce style
sheets, a typed contract, scaffolds and stories. These are the only
Markdown files of one component met in this run. The draft of [4]
names known implementations per platform in the declaration so that
generators can resolve them. Whether this current lasts is
speculation; [13] itself asks whether one code implementation should
be the reference and whether designers will go on working in the
design tool.

## Unexpected

The description is two documents. The card treats the description of
a component as one thing with seven parts; [2] and [13] say it is two
things kept by different people, a specification of how to make it
and a guideline of how to use it, and [13] says the second comes from
code and another team. A small definition "that carries its function"
sits on the border between the two: function, use and behaviour
belong to the guideline in [1] and [5], properties and tokens to the
specification in [2] and [4]. The card is answered as put (F1); the
split is a lead for what the definition should hold.

The frame's example is a composition. In [8] "a form label, search
input, and button can join together to create a search form
molecule": the search field of the frame is three elements joined,
and [8] adds that "Burdening a single pattern with too much
complexity makes software unwieldy" and that elements are not
designed in isolation. At which level a thing counts as one element
with one definition is a choice the sources do not make for the
reader.

A component defined once is not always used as defined. The federal
templates are made of components "some modified" [9], and [8] puts
variation at the level of the page. A page definition that only names
its elements and their places would have no room for this.

Why the W3C group closed is not on the page opened [15]. The search
results list a message in the group's mailing list archive whose
title speaks of inactivity; it was not opened and is no finding.

## Not found

- No standard, of the W3C or of another body, for the specification
  of one component: looked for at the W3C group's page [15] and in
  Open UI's template [3]; the group lists no report and the template
  is not a format.
- No figure on how many design systems generate their documentation
  from code: the survey opened [14] has no such question, and no
  other survey was opened.
- No procedure, stated by a design system's own team, for keeping
  hand-written guidance the same as the code: looked for in [5],
  which describes none; no other team's account was opened.
- No mature design system that keeps one Markdown file per element as
  its definition: the artefacts opened were web pages ([1], [5]), a
  file in a design tool [2], JSON ([4], [7], [10]) and YAML [6]; the
  only Markdown per component is the supplement of [13].
- No definition, in the post opened [5], of the difference between a
  component and a pattern, and no settled boundary between a pattern
  and a page template; other public administrations' pages on it
  appeared in the search results and were not opened.
- No list, on the templates page opened [9], of which components each
  template holds; the pages of the single templates were not opened.
- Not looked at for lack of openings: the component pages of the
  other large vendors' design systems; the tab of specifications of
  [1]; the anatomy and state pages of [4]; the resolver report beside
  [10]; a first-hand maintainers' retrospective and an older vendor
  survey seen in the search results.
- What rendering a component in isolation adds to its description:
  the one page opened [12] covers the generated documentation page
  and does not define a story.

## Options

- **A definition modelled on the guideline.** Fixed headings from the
  pages of use ([1], [5]): what it is, when to use it and when not,
  how it works, states, behaviour, accessibility, rules of content,
  known issues. It carries the function and reads well to a human
  and to an agent; nothing checks it against the build, and it is
  silent on properties.
- **A definition modelled on the specification.** The parts of [2]
  and [3]: anatomy, properties, layout, behaviour, accessibility,
  tokens, version history. It tells a builder how to make the
  element; it duplicates what the code will hold, which is where the
  sources report drift (F6).
- **A definition as data under a schema, with prose beside it.** In
  the manner of [4] and [6]: declared parts, options, states and
  named examples that a script can check, the guidance in prose.
  Checkable and fit for generation; a schema to design and keep, the
  public precedents being a draft and data files, and no standard to
  lean on (F7).
- **Two layers kept apart.** The description holds what a build
  cannot derive (purpose, use, behaviour, states, content,
  accessibility, tokens by name); the reference of properties is the
  build's and is generated from code. This follows the split of F2
  and the limit of generation of F6; it needs a rule for what flows
  back from the build.
- **Citing a library's component.** Where the build uses an existing
  design system, the description names its component and says only
  what differs. This option is the agent's own inference from the
  fact that such systems already carry the definitions (F1); it
  depends on a choice of library that may not be the description's
  to make.

## Relevance to this project

The first half of the idea stands on firm practice: an element with a
definition of its own, written once and used from many screens, is
what every design system opened does (F1), and the level above it,
where a page names its elements, has an established vocabulary (F4).
The recommendation, the agent's own inference from the findings, is
to take the headings of an element definition from that practice
rather than invent them: purpose with when to use and when not, the
named parts, variants and properties, states, behaviour with its
events and keyboard, accessibility, rules of content, and the tokens
it takes, by name. It rests on F1 and F5.

Three things the idea as heard does not yet settle. First, which of
the two documents the definition is (F2): for a description handed
to a build stage the agent would keep to use, behaviour and what a
build cannot derive, and leave the reference of properties to the
code, because that part is the one the sources regenerate (F6).
Second, the level of an element (the search field of the frame is a
composition in [8]). Third, how a page says that an element is used
with a difference ([9], [8]). Each is a decision for the author of
the framework, not a finding.

Visual decisions are better recorded as tokens named in the
vocabulary of [10] than as values inside an element; the format is
stable and a description can cite a token without owning its value.
This is the agent's inference; the card on tokens' use in a build is
another's.

Chosen against: a definition as JSON under a schema of its own,
because the public precedents are a draft [4] and the group that
would have standardised one is closed [15]; and a full hand-written
specification including the properties, because that is the part
maintainers report as drifting and tools regenerate (F6). Drift
should be expected, and what is checked or regenerated after a build
planned for; how, is the question of the card on change after the
first build.

Consult when: the template of an element definition is drafted; the
level at which a thing counts as one element is decided; the page
definition's way of naming and varying its elements is designed;
tokens enter the description; a schema-based format is weighed
against Markdown; the route from the build back to the description
is designed.

## Sources

1. Button, usage (the Guidelines tab). Carbon Design System, IBM.
   "Last updated Oct 15, 2026", byline (the page's own date line).
   https://carbondesignsystem.com/components/button/usage/
   Kind: primary, a vendor's documentation of its own component. How
   read: summarised fetch, all headings of the tab and short quotes;
   the other three tabs not opened. Original.
2. Component Specifications. Nathan Curtis. Feb 20, 2023, byline.
   https://nathanacurtis.substack.com/p/component-specifications-1492ca4c94c
   Kind: primary for the author's own practice, a practitioner's
   article. How read: summarised fetch, headings and short quotes.
   The author's own publication; the address carries an identifier
   in the style of another platform, so it may be his re-publication
   of an earlier post (the agent's inference; the page does not say).
3. Component Spec Template. Open UI. "Last Updated" 2023-10-31,
   byline (the page's own date line).
   https://open-ui.org/component-spec-template
   Kind: primary, the community group's own template. How read:
   summarised fetch, all headings with their instructions. Original.
4. Component format, Spectrum Design Data specification. Adobe.
   Undated; marked "Draft Specification (v1.0.0-draft)".
   https://opensource.adobe.com/spectrum-design-data/spec/component-format/
   Kind: primary, a vendor's own draft schema. How read: summarised
   fetch, the fields and the notices; the example JSON and the linked
   pages of the specification not read. Original.
5. How we document components and patterns in the GOV.UK Design
   System. Amy Hupe, GOV.UK Design System team, Design in government
   blog. 5 November 2018, byline.
   https://designnotes.blog.gov.uk/2018/11/05/how-we-document-components-and-patterns-in-the-gov-uk-design-system/
   Kind: primary, the maintainers' own writing. How read: summarised
   fetch, whole post. Original.
6. button.yaml, govuk-frontend repository, branch main. alphagov.
   Undated; the file as it stood on 2026-11-21.
   https://raw.githubusercontent.com/alphagov/govuk-frontend/main/packages/govuk-frontend/src/govuk/components/button/button.yaml
   Kind: primary artefact, a data file in a public repository. How
   read: summarised fetch, keys, parameters and the names of the
   first ten examples; the first 25 lines returned verbatim.
   Original.
7. custom-elements-manifest, README. webcomponents (GitHub
   organisation). Schema version 2.1.0 dated 2024-05-06 in the
   README's version table.
   https://github.com/webcomponents/custom-elements-manifest
   Kind: primary, the schema's own repository. How read: summarised
   fetch, the README; the schema file not opened. Original.
8. Atomic Design, chapter 2, Atomic Design Methodology. Brad Frost.
   Undated; copyright line 2016.
   https://atomicdesign.bradfrost.com/chapter-2/
   Kind: primary, the author's own book online. How read: summarised
   fetch, the definitions and short quotes. Original.
9. Templates. U.S. Web Design System, General Services
   Administration. Undated.
   https://designsystem.digital.gov/templates/
   Kind: primary, a public administration's documentation of its own
   system. How read: summarised fetch, the index page of templates
   only. Original.
10. Design Tokens Format Module 2025.10, Final Community Group
    Report. Design Tokens Community Group, W3C. 28 October 2025,
    byline (the report's status line).
    https://www.w3.org/community/reports/design-tokens/CG-FINAL-format-20251028/
    Kind: primary, the specification. How read: summarised fetch,
    partially: the first 100,000 of 113,491 characters, through
    section 9.6; sections 9.7 and 9.8 seen in the table of contents
    only. Original.
11. Design tokens. Spectrum, Adobe. Undated.
    https://spectrum.adobe.com/page/design-tokens/
    Kind: primary, a vendor's documentation of its own system. How
    read: summarised fetch, definitions and short quotes. Original.
12. Autodocs, a page of the Storybook documentation (its title was
    not returned by the fetch), version 10.6. Storybook. Undated.
    https://storybook.js.org/docs/writing-docs/autodocs
    Kind: primary, a tool's documentation of its own feature. How
    read: summarised fetch, short quotes. Original.
13. Spec-Driven UI Component Development. Nathan Curtis. Aug 14,
    2026, byline.
    https://nathanacurtis.substack.com/p/spec-driven-ui-component-development
    Kind: primary for the author's own practice, a practitioner's
    article. How read: summarised fetch, headings and short quotes,
    the article open to its end. Original.
14. 2022 Design Systems Survey, fifth edition. Sparkbox. 2022, from
    the page's title and copyright line.
    https://designsystemssurvey.seesparkbox.com/
    Kind: primary for its own data; the publisher is a consultancy
    that sells work on design systems, so the figures are a vendor's
    report. How read: summarised fetch, figures with their headings.
    The fetch returned 219 responses and, beside it, 183 maintainers
    and 37 subscribers, which do not add up; not resolved. Original.
15. UI Specification Schema Community Group. W3C Community and
    Business Groups. Launched 13 August 2025, closed 2026-05-21, both
    from the page.
    https://www.w3.org/community/uispec/
    Kind: primary, the group's own page. How read: summarised fetch,
    whole page. Original.
16. Design Tokens Resolver Module 2025.10. Design Tokens Community
    Group, W3C.
    https://www.w3.org/community/reports/design-tokens/CG-FINAL-resolver-20251028/
    Not opened: the openings were spent. Not cited for content.
17. Anatomy format, and State model, Spectrum Design Data
    specification. Adobe.
    https://opensource.adobe.com/spectrum-design-data/spec/anatomy-format/
    https://opensource.adobe.com/spectrum-design-data/spec/state-model/
    Not opened: the openings were spent. Not cited for content.
18. Component Contracts and Schemas. Nathan Curtis.
    https://nathanacurtis.substack.com/p/component-contracts-and-schemas
    Not opened: the openings were spent. Not cited for content.
19. The State of Design Systems: 2020. Material Design, Google.
    https://m2.material.io/blog/research-state-of-design-systems-2020
    Not opened: the openings were spent. Not cited for content.
20. Lessons learned while maintaining Contentful's design system.
    Contentful.
    https://contentful.com/blog/lessons-maintaining-forma36-system
    Not opened: the openings were spent. Not cited for content.
21. DESIGN_SYSTEM_CONTENT_PATTERN.md, govuk-design-system-backlog
    repository. alphagov.
    https://github.com/alphagov/govuk-design-system-backlog/blob/master/docs/DESIGN_SYSTEM_CONTENT_PATTERN.md
    Not opened: the openings were spent. Not cited for content.
22. Designing components. Codex, Wikimedia.
    https://doc.wikimedia.org/codex/latest/contributing/designing-components.html
    Not opened: the openings were spent. Not cited for content.

## Opened and not used

None: all fifteen pages opened are cited above.

## Search record

Queries, in order:

1. component specification anatomy states variants design system
   documentation
2. design tokens format module
3. W3C UI Specification Schema Community Group
4. design system documentation drift (the disconfirming query)
5. component specification out of date design system single source
   of truth code (the disconfirming query, second wording)
6. Open UI component anatomy states behaviors research template
7. atomic design atoms molecules organisms templates pages, chapter 2
8. GOV.UK Design System components patterns, contribute, write
   guidance, "When to use this component"
9. Storybook Autodocs documentation generated from component code
10. design systems survey results, biggest challenges, documentation
    up to date
11. design system team blog, documentation generated from component
    source, props table, custom elements manifest, "source of truth"
12. design system patterns vs components vs page templates,
    definition, public sector
13. keeping design system documentation in sync with code,
    maintainers, lessons

Pages opened, fifteen, in order: [10], [4], [2], [3], [15], [5], [8],
[12], [1], [9], [14], [13], [7], [6], [11].

The disconfirming query: both wordings returned many pages, most of
them vendors' and agencies' blogs on their own market, which were not
opened; they agree, as far as their titles go, that drift is a named
trouble. Of what was opened for it, the survey [14] confirms the
trouble with figures, and [12], [6], [7] and [13] show what is
generated or checked. The expectation held for the trouble and held
in part for the generation: the reference and the examples are
generated, the guidance is not (F6).

Why the run ended: the opening budget. Fifteen pages were opened, the
upper bound of the card's stop rule. Every route of the card has a
primary source among them. The two last queries, worded differently,
returned no new kind of answer but did return further instances that
could not be opened (other public administrations' pages on patterns
and templates, a maintainers' retrospective, an older vendor survey),
so "nothing new from a differently worded query" is not claimed.
