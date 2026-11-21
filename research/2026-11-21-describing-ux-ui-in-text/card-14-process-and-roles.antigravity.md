---
date: 2026-11-21
project: forge
topic: the place of interface work in the process and how its outputs serve solo builders and specialists
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 14; 2026-09-28-artefact-layers-from-idea-to-handover.md; 2026-10-13-what-a-brd-contains-and-how-it-is-found-today.md; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":78648,"output_tokens":23494,"thinking_tokens":12531,"cache_read_tokens":348649,"total_tokens":102142}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-14-process-and-roles
status: immutable
---

# Where interface work stands between requirements and build, the order of its outputs, and what lean and solo practices keep

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Across standards, layered UX models, Dual-Track Agile, and spec-driven AI
frameworks, work on the user interface takes its input from business and
functional requirements, resolves user flows, information structure, and
screen elements in tandem with technical design, and feeds validated
interface decisions into user stories and the build. Within interface work
itself, outputs progress from abstract to concrete: task flows and
structure first, then screen skeletons (wireframes or text breadboards),
interactive prototypes, visual design tokens, and developer annotations.
The disconfirming queries ("UX deliverables are waste", "design handoff is
dead") confirm a strong practitioner consensus against heavy standalone
specification books and one-way handoffs, but empirical survey data and AI
spec-driven kits show that artefacts do not disappear: lean and solo
practices drop pixel-perfect static wireframes, redline specs, and
standalone reports while keeping structural flows, named places and
affordances, rough spatial sketches, and reusable design tokens. The one
unexpected finding reconfigures the document chain: in both Dual-Track
Agile and AI spec-driven methods, interface design precedes user stories
rather than consuming them, because stories are sliced and given acceptance
criteria around the agreed screens, states, and flows.

## Question

- **Question:** Where does the work on the interface stand between the
  requirements and the build in established processes: what does it take
  from requirements and user stories, what does it hand to the builders, in
  which order do its own outputs come (flows, structure, wireframes, visual
  design, prototype, specification), and how does the same output serve one
  person working end to end and a specialist in a team: which outputs do
  lean and solo practices drop, and which do they keep?
- **Why it matters:** it decides where the description stands among the
  framework's documents and how light the first shape can be.
- **What would answer it:** method literature and practitioner
  organisations.
- **Where to look:** the layered models of user experience work; lean UX;
  dual-track practice; the human-centred design standard through secondary
  pages; guides to design handoff. The known notes on the ladder of
  documents and on business requirements. Search words from card 1:
  "handoff" names the passage and a tool's features for it, not the
  document; for the document "design specs", "annotations", "ready for
  dev"; vendors' pages on their own market are to be expected and are left
  out by the brief.
- **Disconfirming query:** "UX deliverables are waste", "design handoff is
  dead"; expected: a strong current against handing over documents at all.
- **Stop rule:** nothing new from a differently worded query and every
  route has a primary source; ten to fifteen pages opened.

**Baseline to beat and disambiguation of "design".** The two known notes
(`2026-09-28-artefact-layers-from-idea-to-handover.md` [1] and
`2026-10-13-what-a-brd-contains-and-how-it-is-found-today.md` [2])
establish a three-step ladder from raw trigger to worked understanding to
handed-over specification, define what a BRD and its use cases (`UC`) carry
while keeping screens out of the BRD ("Solutioning below the standard's
line: schemas, endpoints, screens, tasks" [2]), and survey Shape Up and
four spec-driven AI tools (spec-kit, Kiro, BMad, OpenSpec) without
examining where UX/UI artefacts stand or how their internal outputs are
ordered and pared down. Throughout this note, the three senses of "design"
in the sources are kept apart: **interface design** (the structure, layout,
and behaviour of the user interface, whether held in a design tool or in
text), **technical design** (the engineering architecture between
requirements and tasks in spec-driven kits), and **visual identity** (the
tokens, typography, colour, and component styling of a design system). All
external web sources below ([3]–[12]) were read through the environment's
summarising web fetch tool (tertiary readings of primary and secondary
pages), whereas the attached notes [1, 2] were read in full.

## Key findings

**F1. In both the international human-centred design standard and the
five-plane UX model, interface design sits directly below functional and
user requirements and must settle flows and structure before screen layout
and visual identity.** [consensus — standard via secondary preview and
practitioner claim; rests on summarised fetches of [3, 4] and full reading
of [2]]
ISO 9241-210:2019 (Clause 7, read via the iTeh standards preview [3])
orders human-centred design into four iterative activities: understanding
and specifying the context of use (Clause 7.2), specifying the user
requirements (Clause 7.3), producing design solutions to meet user
requirements (Clause 7.4, covering task and interaction design in 7.4.2,
concrete prototypes and mock-ups in 7.4.3, iterative refinement in 7.4.4,
and communicating specifications to implementers in 7.4.5), and evaluating
the design against requirements (Clause 7.5). Jesse James Garrett's
*The Elements of User Experience* (2000 [4], read via summarised fetch)
places these in five dependency planes moving from abstract at the bottom
to concrete at the top: (1) **Strategy** ("User Needs" and product
objectives), (2) **Scope** ("Functional Specifications: 'feature set':
detailed descriptions of functionality the site must include in order to
meet user needs" and content requirements), (3) **Structure**
("Interaction Design: development of application flows to facilitate user
tasks" and "Information Architecture: structural design of the information
space"), (4) **Skeleton** ("Interface Design", "Navigation Design", and
"Information Design"), and (5) **Surface** ("Visual Design: graphic
treatment of interface elements (the 'look' in 'look-and-feel')") [4].
In terms of the known BRD note [2], Strategy and Scope correspond to the
brief and the BRD (business objectives, functional requirements, and
user-goal use cases), while interface work begins at the Structure plane.

**F2. Across Agile and AI-assisted processes, interface work takes its
input from business requirements or PRDs and precedes — rather than
follows — the slicing of delivery user stories.** [consensus — practitioner
claim and vendor documentation; rests on full reading of [1] and
summarised fetches of [5, 6, 7]]
Neither Dual-Track Agile nor spec-driven AI frameworks treat delivery user
stories as the primary input to interface design. In Dual-Track Agile
(Marty Cagan, 2012 [5]; Anna Kaley at NN/g, 2023 [6]; both via summarised
fetch), product discovery runs ahead of delivery: the product manager,
interface designer, and lead engineer take business problems and
hypotheses, test low-to-high-fidelity prototypes with users in the
Discovery track to resolve value, usability, feasibility, and viability
risks, and only convert validated designs into delivery user stories and
acceptance criteria once discovery succeeds [5, 6]. In the BMad Method's
spec-driven workflow ([1]; BMad documentation [7] via summarised fetch),
the Product Requirements Document (`bmad-prd`) answers "what should we
build and why" and explicitly states: "It does not say how; that is Design
UX and Architecture. It does not divide work into stories; that is Break
Work into Stories and Track It" (section "PRD: Agree on What and Why" [7]).
Between interface design (`bmad-ux`) and technical design
(`bmad-architecture`), BMad states: "At the initiative and on each epic, UX
goes first and architecture second, so the design can inform the technical
choices... BMad doesn't enforce the order, so swap them when a technical
constraint has to settle what the screens can do" (section "Design UX and
Architecture" [7]). Only after `PRD`, `UX`, and `Architecture` are settled
does `bmad-create-epics-and-stories` package their decisions into story
files for the build agent [7].

**F3. The internal outputs of interface work follow the order flows and
structure -> wireframes -> interactive prototypes -> visual identity ->
handoff specifications, but practitioners often fuse flows with wireframes
and use static wireframes primarily as a private thinking tool.**
[consensus — practitioner survey and practitioner claim; rests on
summarised fetches of [4, 8, 9]]
In Page Laubheimer's Nielsen Norman Group survey of 86 UX professionals
(2015 [8], read via summarised fetch), the most frequently produced
deliverables ("often" or "sometimes") were static wireframes (71% produced
them "often"), interactive prototypes, flowcharts, site maps, usability and
analytics reports, and style guides or pattern libraries (61% "often" or
"sometimes") [8]. However, when asked to pick up to four deliverables most
effective for communicating with specific audiences, static wireframes did
not place in the top four for any audience (internal management, clients,
or developers): Laubheimer notes that "static wireframes were the most
frequently produced deliverable overall (71% of respondents produced static
wireframes 'often'), but were not chosen in the top 4 most effective
deliverables for any audience. This suggests that noninteractive wireframes
tend to be artifacts that UX professionals produce for their own benefit"
(section on audience effectiveness [8]). For communicating with developers,
respondents preferred interactive prototypes alongside structural artefacts
— flowcharts, site maps, and style guides [8]. For web, mobile, and desktop
applications where a few dynamic screens change state rather than linking
many static pages, Laubheimer (2016 [9], read via summarised fetch)
documents **wireflows** ("Wireflows are a design-specification format that
combines wireframe-style page layout designs with a simplified
flowchart-like way of representing interactions", section "Wireflows as a
Deliverable for Workflows" [9]), collapsing Structure and Skeleton into a
single artefact.

**F4. What interface work hands to builders splits into two parts: visual
and spatial properties (now largely carried by design tokens and inspection
tools) and behavioural and state rules (which still require explicit text
specifications or annotations).** [consensus — vendor documentation and
practitioner claim; rests on summarised fetches of [7, 10]]
In tool-centred handoff (Figma's "Guide to Dev Mode" [10], read via
summarised fetch), designers mark completed frames, components, or sections
as "Ready for dev"; developers use the Inspect panel to read measurements,
layout properties, design-system variables, and code snippets, or pull
mapped component code via Code Connect [10]. Because static visual frames
depict only a single state, Figma's Dev Mode provides text **annotations**
pinned to components to convey context and non-visual properties [10] —
specifically interactive states (default, hover, focus, active, disabled),
system states (loading, empty, error, success), trigger-and-transition
logic, content truncation rules, responsive breakpoint behaviour, and
accessibility semantics (tab order, ARIA labels). BMad's AI workflow
formalises this exact division purely in Markdown ([7], section "Design UX
and Architecture", via summarised fetch): `bmad-ux` writes "two peer
documents: `DESIGN.md` for how the product looks (tokens, typography,
components) and `EXPERIENCE.md` for how it works (structure, states,
interactions, accessibility, key flows). When either conflicts with a mock,
the document wins" [7].

**F5. The disconfirming queries confirm a widespread rejection of heavy
handoff documentation in favour of continuous collaboration and shared
component libraries, yet empirical data and agentic workflows show that
artefacts are pared down and refocused rather than eliminated.**
[contested — practitioner claim vs practitioner survey and vendor
documentation; rests on full reading of [1] and summarised fetches of
[8, 11, 12]]
Running the disconfirming queries ("UX deliverables are waste", "design
handoff is dead") surfaced two strong currents against traditional
deliverables:
- Jeff Gothelf's Lean UX manifesto in *Smashing Magazine* (2011 [11], read
  via summarised fetch) argues that "this deliverables-heavy process has
  put UX designers in the deliverables business — measured and compensated
  for the depth and breadth of their deliverables instead of the quality
  and success of the experiences they design" (introduction [11]), and
  prescribes that "Traditional documents are discarded or, at the very
  least, stripped down to their bare components, providing the minimum
  amount of information necessary to get started on implementation"
  (section on Lean UX principles [11]).
- Dan Mall and Brad Frost's "Hot Potato Process" (described in secondary
  practitioner write-up [12], read via summarised fetch) replaces the
  one-way handoff ("chucking Zeplin or Figma links over the wall to
  developers") with a continuous rapid loop in which rough layouts and
  coded prototypes pass back and forth between designer and developer
  throughout the build cycle.

Contradicting the stronger claim that Agile and Lean dispense with
deliverables altogether, Laubheimer's NN/g survey (2015 [8], read via
summarised fetch) found that "even the 83% of respondents who worked in an
Agile environment… still regularly produced deliverables in their
workflow," concluding: "This is a clear indication that Agile isn't
deliverable-free — it just refocuses those efforts towards more useful
deliverables and away from reports that tended to not be widely read" [8].
Furthermore, as known note [1] (finding 7) established, a human team can
rely on a live briefing or "hot potato" pairing to fill gaps in a rough
pitch, whereas an AI coding agent or external builder cannot ask unscripted
questions mid-build and requires an explicit specification contract [1, 7].

**F6. Lean and solo practices drop high-fidelity static wireframes, formal
research reports, and pixel-level redline specs, while keeping three light
artefacts: text-based place-and-affordance flows (breadboards), rough
spatial sketches when 2D layout is the core problem, and reusable design
tokens.** [consensus — practitioner claim and vendor documentation; rests
on full reading of [1] and summarised fetches of [6, 7, 8, 13]]
When a single person works end to end or a lean team shapes work before
handing it to builders, the literature converges on what is dropped and
what is kept:
- **Dropped in lean/solo work:** pixel-perfect static wireframes (which
  Shape Up rejects as defining "too much detail too early" [1, 13]), long
  research and usability report decks [8, 11], and manual visual redlines
  when a design system or component library already holds the visual
  identity [7, 8, 10]. BMad also drops separate UX documents entirely for
  routine work: "Use this page to decide whether the work needs UX or
  architecture before stories are planned. Most changes need neither" —
  skipping `bmad-ux` for "A clear, local change with established patterns"
  and for "back-end work and internal tools with no real interface"
  (section "Design UX and Architecture" [7]).
- **Kept in lean/solo work:** Basecamp's *Shape Up* (Chapter 4 [13], read
  via summarised fetch) keeps **breadboards** written entirely in text
  ("We'll use words for everything instead of pictures") made of three
  primitives: **Places** ("things you can navigate to, like screens,
  dialogs, or menus that pop up"), **Affordances** ("things the user can
  act on, like buttons and fields. We consider interface copy to be an
  affordance, too"), and **Connection lines** ("how the affordances take
  the user from place to place") [13]. When 2D spatial arrangement is
  itself the problem, Shape Up uses **fat marker sketches** ("a sketch made
  with such broad strokes that adding detail is difficult or impossible"
  [13]). From these, the shaper extracts a list of named **Elements** [13].
- **How the same output serves both roles:** For one person working end to
  end, the place-and-affordance map (or wireflow [9]) serves the private
  cognitive role that static wireframes served for 71% of practitioners in
  [8], while giving an AI build agent bounded screen and element rules
  without requiring a visual mock [7]. For a specialist in a team, the
  same structural skeleton is augmented with state, edge-case, and
  accessibility annotations (`EXPERIENCE.md` in BMad [7], Dev Mode
  annotations in Figma [10]) so that downstream engineers or agents do not
  guess behaviour.

## Unexpected

**The card's frame places user stories upstream of or alongside the build
inputs and asks what interface work takes from requirements and user
stories; both Dual-Track Agile [5, 6] and spec-driven AI methods [7] invert
the relationship between interface work and user stories.** In those
processes, interface work takes its input from the business requirements or
PRD (and the user-goal use cases inside the BRD [2]), works out the
screens, flows, and states alongside technical design, and *produces* the
context from which user stories and acceptance criteria are sliced [5, 7].
In BMad's words, the PRD "does not say how; that is Design UX and
Architecture. It does not divide work into stories; that is Break Work into
Stories and Track It" [7]. Placing the interface description *before* user
stories in the framework's chain (between BRD/solution design and user
stories) means user stories can cite defined places, elements, and states
directly in their acceptance criteria rather than inventing UI assumptions
story by story.

**A direct precedent exists in both human shaping [13] and AI spec-driven
development [7] for describing interfaces purely in words that take
precedence over visual mocks.** Shape Up's breadboarding explicitly states,
"We'll use words for everything instead of pictures," reducing an interface
to Places, Affordances (including copy), and Connection lines [13].
Independently, BMad splits its textual UX specification into `DESIGN.md`
(visual identity tokens and components) and `EXPERIENCE.md` (structure,
states, interactions, accessibility, and key flows) and rules that "When
either conflicts with a mock, the document wins" [7]. This directly
supports the card's test hypothesis of defining screens and their elements
in versioned Markdown.

## Not found

- **The full text of ISO 9241-210:2019 at source.** The standard is sold
  by ISO (`iso.org/standard/77520.html`); only Clause 7's headings and
  summaries through the iTeh standards preview [3] were read.
- **A standalone primary article by Brad Frost or Dan Mall on
  `bradfrost.com` defining "The Hot Potato Process".** A domain search on
  `bradfrost.com` returned no standalone primary post; the concept is cited
  through a secondary practitioner article [12].
- **Raw HTML character-by-character verification of web sources.** In this
  execution environment, direct shell HTTP fetching (`curl`) is blocked by
  a sandbox deny rule; all external web pages ([3]–[13]) were read via the
  environment's grounded web search tool (`summarised fetch`).
- **Any quantitative study measuring defect rates or build speed of
  text-only UX specifications against visual mockups in human or AI builds.**
  Looked for across NN/g and spec-driven development sources; no empirical
  benchmark was found.

## Options

The findings open three distinct ways to place and shape the interface
description in the framework's document chain:

- **Option A: Place the interface description between the BRD and User
  Stories, as a peer to Solution Design, with a two-tier fidelity rule
  (lean breadboard vs annotated specification).**
  - *Shape:* The interface document reads the BRD (specifically its actors,
    business rules, and user-goal use cases `UC` [2]), runs alongside
    Solution Design (allowing UX and technical design to inform each other
    as in BMad [7]), and feeds User Stories. Its mandatory core (used by a
    solo builder and as the first draft for a specialist) is a text
    breadboard [13]: named Places (screens/dialogs), named Elements /
    Affordances on each place, and Connection flows between them, plus a
    reference to visual design tokens (`DESIGN.md` style [7]). Its
    specialist/handoff tier adds state tables (loading, empty, error,
    disabled), responsive rules, and accessibility annotations [7, 10].
  - *Trade-offs:* Matches both Dual-Track Agile [5, 6] and BMad [7]; keeps
    the first shape as light as Shape Up's breadboard [13] while giving
    user stories concrete screens and elements to reference. Requires
    updating the user-story step so stories cite interface elements rather
    than precedes them.

- **Option B: Place the interface description after User Stories, as a
  pre-build handoff specification.**
  - *Shape:* Keep the existing chain (`brief -> BRD -> solution design ->
    user stories`) untouched and attach the interface description after
    user stories as a "ready for dev" annotation layer [10].
  - *Trade-offs:* Zero disruption to existing upstream documents, but
    contradicts Dual-Track Agile [5, 6], Garrett's planes [4], and BMad
    [7], where stories cannot be cleanly sliced or given UI acceptance
    criteria before the screens and flows exist.

- **Option C: Split the interface description into two separate artefacts —
  a project-wide visual identity file (`DESIGN.md`) and a per-feature
  interaction/screen file (`EXPERIENCE.md`) — with a bypass rule for
  backend or pattern-local changes.**
  - *Shape:* Following BMad [7] and NN/g's separation of style guides from
    wireflows [8, 9], keep visual tokens and component catalog rules in a
    stable project-level document, and write only flows, places, elements,
    and state annotations per feature, skipping the feature UX document
    when a change is back-end only or reuses an existing screen pattern.
  - *Trade-offs:* Avoids repeating visual identity rules across every
    feature and prevents ceremony on small changes (fixing the
    one-size-fits-all failure mode noted in [1], finding 10), at the cost
    of maintaining two document kinds instead of one.

## Relevance to this project

**Recommendation: Combine Option A and Option C (author's inference from
[1, 2, 4, 7, 8, 13]).**

1. **Where it stands in the chain:** Place the interface description
   after the BRD (`brd`) and alongside Solution Design, *before* User
   Stories. By the BRD standard in [2], the BRD already holds actors,
   business rules, non-functional usability/accessibility targets, and
   user-goal use cases (`UC`), while forbidding screen-level solutioning.
   The interface document takes those `UC` scenarios as its input (the
   Scope-to-Structure transition in Garrett [4] and Clause 7.3-to-7.4 in
   ISO 9241-210 [3]), exchanges constraints with Solution Design (technical
   design [7]), and hands named screens, elements, and flows to User
   Stories so each story can be sliced around real interface behaviour.
2. **Order of sections inside the document (and order of elicitation by the
   agent):** Follow the dependency order established in F1 and F3:
   - First, **Flows and Structure** (how the user moves across the
     application to fulfil the BRD's use cases; Garrett's Structure plane
     [4]).
   - Second, **Places and Elements** (each screen, dialog, or state, the
     defined interactive elements/affordances it holds, and where they
     stand; Garrett's Skeleton plane [4] and Shape Up's breadboard + fat
     marker sketch [13]).
   - Third, **States, Variations, and Accessibility Annotations** (loading,
     empty, error, validation, responsive breakpoints, keyboard/ARIA rules;
     Figma Dev Mode annotations [10] and BMad's `EXPERIENCE.md` [7]).
   - Keep **Visual Identity** (tokens, typography, colour, shared component
     styling) in a reusable project-level section or companion file rather
     than re-specifying it on every screen [7, 8, 10].
3. **How it scales from one person working end to end to a specialist in a
   team:** Make the first two steps (Flows + Places and Elements, equivalent
   to a Shape Up breadboard [13] or NN/g wireflow [9]) the minimum viable
   shape. For a solo builder working with an AI coding agent, this light
   shape is sufficient to think through the interface (replacing the
   private static wireframe [8]) and to steer the coding agent when paired
   with a component library or token file. For a UX/UI specialist handing
   off to a team or an autonomous build agent, the third step (explicit
   state, edge-case, and accessibility annotations) completes the contract
   so builders never guess [1, 7]. Include BMad's right-sizing gate [7]: if
   a change has no user interface or strictly follows an already-defined
   screen pattern, the document is skipped or recorded as a delta.

**Consult when:** deciding the sequence of artefacts in the framework's
workflow; designing the minimum viable template for a UX/UI description;
defining what the UX/UI agent reads from the BRD and what it hands to User
Stories and the build stage; or deciding which sections are mandatory for a
solo builder versus a specialist team handoff.

## Sources

1. *Artefact layers from idea to handover*, project `forge` research note
   (`2026-09-28-artefact-layers-from-idea-to-handover.md`), 2026-09-28
   (dated by frontmatter), local workspace file; kind: primary (project
   baseline note); how read: in full; original.
2. *Research: what a BRD contains and how it is found today*, project
   `forge` research note
   (`2026-10-13-what-a-brd-contains-and-how-it-is-found-today.md`),
   2026-10-13 (dated by frontmatter), local workspace file; kind: primary
   (project baseline note); how read: in full; original.
3. *ISO 9241-210:2019 — Ergonomics of human-system interaction — Part 210:
   Human-centred design for interactive systems*, International
   Organization for Standardization (preview hosted by iTeh Standards),
   2019-07 (dated by structured standard metadata),
   https://standards.iteh.ai/catalog/standards/iso/76be2260-3669-45a2-a42e-051f2ef71186/iso-9241-210-2019 ;
   kind: secondary (catalogue preview and clause breakdown of the sold ISO
   standard); how read: summarised fetch (Clause 7: 7.2, 7.3, 7.4, 7.5);
   copy/preview of ISO 9241-210:2019.
4. *The Elements of User Experience*, Jesse James Garrett, 2000-03-30
   (dated by document byline), http://www.jjg.net/ia/elements.pdf (and book
   overview at https://www.jjg.net/elements/ ); kind: primary; how read:
   summarised fetch; original.
5. *Dual-Track Agile*, Marty Cagan, Silicon Valley Product Group (SVPG),
   2012-09-17 with post-2018 author update note (dated by byline),
   https://www.svpg.com/dual-track-agile/ ; kind: primary; how read:
   summarised fetch; original.
6. *Scaling Discovery in Agile*, Anna Kaley, Nielsen Norman Group (NN/g),
   2023-02-05 (dated by byline),
   https://www.nngroup.com/articles/discovery-in-agile/ ; kind: primary;
   how read: summarised fetch; original.
7. *Design UX and Architecture* (with *Choose a Planning Path* and *Define
   Requirements and a Specification*), BMad Method documentation, undated,
   https://docs.bmad-method.org/plan/design-ux-and-architecture/ (and
   https://docs.bmad-method.org/plan/choose-a-planning-path/ ,
   https://docs.bmad-method.org/plan/define-requirements-and-a-specification/ );
   kind: primary (official framework documentation); how read: summarised
   fetch; original.
8. *Which UX Deliverables Are Most Commonly Created and Shared?*, Page
   Laubheimer, Nielsen Norman Group (NN/g), 2015-10-18 (dated by byline),
   https://www.nngroup.com/articles/common-ux-deliverables/ ; kind: primary
   (practitioner survey report, n=86); how read: summarised fetch;
   original.
9. *Wireflows: A UX Deliverable for Workflows and Apps*, Page Laubheimer,
   Nielsen Norman Group (NN/g), 2016-12-04 (dated by byline),
   https://www.nngroup.com/articles/wireflows/ ; kind: primary; how read:
   summarised fetch; original.
10. *Guide to Dev Mode*, Figma Learn / Help Center, undated,
    https://help.figma.com/hc/en-us/articles/15023124644247-Guide-to-Dev-Mode ;
    kind: primary (vendor documentation of its own product); how read:
    summarised fetch; original.
11. *Lean UX: Getting Out Of The Deliverables Business*, Jeff Gothelf,
    Smashing Magazine, 2011-03-07 (dated by byline),
    https://www.smashingmagazine.com/2011/03/lean-ux-getting-out-of-the-deliverables-business/ ;
    kind: primary; how read: summarised fetch; original.
12. *The Hot Potato Process* (coverage of Dan Mall and Brad Frost's
    collaborative handoff workflow), Vitaly Friedman / Smart Interface
    Design Patterns and UX Planet, undated in search extract,
    https://smart-interface-design-patterns.com/articles/design-handoff/ ;
    kind: secondary (practitioner synthesis of Mall and Frost's model); how
    read: summarised fetch; original secondary write-up (no standalone
    primary article found on `bradfrost.com`).
13. *Shape Up: Stop Running in Circles and Ship Work that Matters — Chapter
    4: Find the Elements*, Ryan Singer, Basecamp, undated,
    https://basecamp.com/shapeup/1.3-chapter-04 (also indexed at
    https://basecamp.com/shapeup/web/chapter-4 ); kind: primary; how read:
    summarised fetch; original.

## Opened and not used

- Interaction Design Foundation (IxDF), *The 5 Planes of UX Design*
  (`https://www.interaction-design.org/literature/article/the-5-planes-of-ux-design`):
  superseded by Garrett's primary document [4].
- UXPin,Supernova, and ModeInspect blog posts on design handoff and "design
  handoff is dead" (`uxpin.com`, `supernova.io`, `modeinspect.com`): left
  out by the brief as vendor blogs writing on their own market, superseded
  by Figma's product documentation [10] and NN/g [8, 9].

## Search record

**Queries run (in order):**
1. `elements of user experience planes Garrett deliverables order`
2. `dual track agile UX discovery delivery requirements user stories`
3. `ISO 9241-210 human-centred design activities outputs requirements`
4. `design handoff design specs annotations ready for dev nngroup`
5. `"UX deliverables are waste"` (disconfirming query 1)
6. `"design handoff is dead"` (disconfirming query 2)
7. `site:nngroup.com UX deliverables survey wireframes flows prototypes specifications`
8. `site:nngroup.com dual track agile UX discovery delivery user stories`
9. `site:nngroup.com lean UX solo designer team of one deliverables`
10. `"hot potato process" Brad Frost design handoff`
11. `BMad method UX design workflow PRD architecture stories`
12. `Shape Up chapter 4 "Find the Elements" breadboarding fat marker sketches`
13. `site:nngroup.com "Which UX Deliverables Are Most Commonly Created" OR "Wireflows: A UX Deliverable" Page Laubheimer exact URL date quotes`
14. `site:smashingmagazine.com "Lean UX: Getting Out Of The Deliverables Business" Jeff Gothelf exact URL date verbatim quotes`
15. `site:basecamp.com "Find the Elements" shapeup breadboarding "fat marker" places affordances connection lines exact URL verbatim quotes`
16. `site:bradfrost.com "The Hot Potato Process" OR "hot potato" design handoff Brad Frost Dan Mall exact URL date verbatim quotes`
17. `site:svpg.com "Dual-Track Agile" OR "Product Discovery" Marty Cagan discovery delivery prototypes user stories exact URL date quotes`
18. `site:help.figma.com "Dev Mode" "Ready for dev" annotations measurements specs developer handoff exact URL`
19. `site:nngroup.com "common-ux-deliverables" "wireflows" Page Laubheimer publication dates percentages survey numbers verbatim quotes`
20. `site:help.figma.com "15023124644247-Guide-to-Dev-Mode" "Ready for dev" annotations measurements inspect verbatim quotes sections`
21. `site:interaction-design.org "The 5 Planes" OR "Elements of User Experience" Jesse James Garrett Strategy Scope Structure Skeleton Surface exact URL date quotes`
22. `"ISO 9241-210:2019" "77520.html" clauses "7.2" "7.3" "7.4" "7.5" context of use user requirements design solutions evaluate`
23. `site:docs.bmad-method.org UX design PRD architecture stories planning path exact URL verbatim quotes`
24. `site:nngroup.com "UX Team of One" OR "solo" OR "Dual-Track" agile discovery delivery exact URL author date verbatim quotes`
25. `site:docs.bmad-method.org "Run bmad-ux when the interface matters" "DESIGN.md" "EXPERIENCE.md" exact URL path`
26. `site:nngroup.com "https://www.nngroup.com/articles/wireflows/" Page Laubheimer date verbatim quotes`
27. `site:jjg.net "The Elements of User Experience" Jesse James Garrett exact URL date verbatim quotes`

**Pages opened (14 openings: 2 local files read in full + 12 targeted web
page fetches; direct `curl` in the shell was denied by the environment's
sandbox rule):**
1. Local file `2026-09-28-artefact-layers-from-idea-to-handover.md` [1] (in
   full).
2. Local file `2026-10-13-what-a-brd-contains-and-how-it-is-found-today.md`
   [2] (in full).
3. `jjg.net/ia/elements.pdf` (Garrett, *The Elements of User Experience*)
   [4] (summarised fetch).
4. `interaction-design.org` (*The 5 Planes of UX Design*) (summarised
   fetch; opened and not used, superseded by [4]).
5. `standards.iteh.ai` preview of `ISO 9241-210:2019` Clause 7 [3]
   (summarised fetch).
6. `nngroup.com/articles/common-ux-deliverables/` (Laubheimer 2015) [8]
   (summarised fetch).
7. `nngroup.com/articles/wireflows/` (Laubheimer 2016) [9] (summarised
   fetch).
8. `svpg.com/dual-track-agile/` (Cagan 2012) [5] (summarised fetch).
9. `nngroup.com/articles/discovery-in-agile/` (Kaley 2023) [6] (summarised
   fetch).
10. `smashingmagazine.com/2011/03/lean-ux-getting-out-of-the-deliverables-business/`
    (Gothelf 2011) [11] (summarised fetch).
11. `basecamp.com/shapeup/1.3-chapter-04` (Singer, *Shape Up* Ch. 4) [13]
    (summarised fetch).
12. `docs.bmad-method.org/plan/design-ux-and-architecture/` (with planning
    path and PRD pages) [7] (summarised fetch).
13. `help.figma.com/hc/en-us/articles/15023124644247-Guide-to-Dev-Mode`
    [10] (summarised fetch).
14. `smart-interface-design-patterns.com/articles/design-handoff/` (after
    checking `bradfrost.com` for the Hot Potato Process) [12] (summarised
    fetch).

**What the disconfirming query found:**
`"UX deliverables are waste"` and `"design handoff is dead"` returned a
substantial practitioner literature (Gothelf's Lean UX [11], Mall and
Frost's Hot Potato Process [12], and recent design-systems / AI
design-to-code commentary) arguing that heavy specification decks and
one-way "over the wall" handoffs expire immediately and impede
collaboration. Cross-checking against NN/g's survey [8] and AI spec-driven
kits [1, 7] showed that this movement strips deliverables down to minimal
structural, behavioural, and token artefacts rather than eliminating them,
and that asynchronous or AI-agent builders still require an explicit
written specification.

**Reason the run ended:** Both parts of the card's stop rule and the
opening budget were met at once — every route named in the card had a
primary source (or secondary preview for the sold ISO standard), differently
worded queries returned the same recurring models and distinctions, and 14
pages (within the 10-to-15 opening budget) had been opened.
