---
date: 2026-11-21
project: forge
topic: where describing an interface in text failed
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 16; 2026-10-03-how-a-solution-design-is-built.md; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":96068,"output_tokens":34548,"thinking_tokens":18751,"cache_read_tokens":674825,"total_tokens":130616}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-16-where-text-failed
status: immutable
---

# Where describing an interface in text failed

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Textual descriptions of user interfaces failed across four documented
waves: upfront functional specification documents (which created an
illusion of agreement and froze interface decisions before screens were
seen), imperative behaviour-driven development (BDD) scripts coupled to
screen mechanics (which broke on minor layout edits), model-based user
interface (MBUI) and model-driven development (MDD) generators (which
suffered from high learning thresholds, low expressive ceilings, and
unpredictable layout heuristics), and static style guides or
spec-anchored Markdown files that drifted from the codebase. This
picture is consensus across practitioner post-mortems, tool
documentation, and academic surveys, read here through the project's
local baseline note and fifteen primary web sources fetched via a
summarising extraction tool. The confirming/disconfirming query (`"UI
specification as source of truth long-lived success"`) returned vendor
advocacy and 2026 Spec-Driven Development (SDD) frameworks rather than
independent long-lived post-mortems of prose screen specs; all surviving
textual descriptions relied on code generation, automated tests bound
through an abstraction layer, or a narrow scope (visual tokens,
component APIs, or domain rules) coupled with same-session maintenance.
Two 2026 empirical papers add an unexpected failure mode specific to AI
agents: in 36,906 lint-valid `DESIGN.md` files on GitHub (as of October
2026), 47.5% failed to formalise component specifications beyond prose
and 88.8% of component-token files contained unreferenced colours, while
in a 283-session study of a 108,000-line codebase, stale Markdown
specifications caused silent failures because coding agents trusted
outdated text unconditionally.

## Question

#### Card 16: Where describing an interface in text failed
- **Question:** Where did textual specifications of interfaces fail or
  get abandoned (heavy specification documents, descriptions that
  drifted from the product, generation from models), which reasons are
  recorded, what do those who argue against describing an interface in
  text propose in its place (the prototype as the specification, the
  code as the source of truth), and what kept true the textual
  descriptions that survive (generation from the product, tests bound
  to the text, a narrow scope)?
- **Why it matters:** the plan assumes text can be the source of truth;
  this card attacks that before a layer rests on it.
- **What would answer it:** critiques, post-mortems and reports of
  experience.
- **Where to look:** the criticism of design up front; living
  documentation and specification by example; reports of experience with
  behaviour-driven development for interfaces; writing on drift between
  design and product. The known note on the solution design for what is
  known of staleness. Search words from card 1: the fate of
  model-driven development beside the warning of 2025 that a
  specification as the only source repeats it ("review fatigue").
- **Disconfirming query:** here the confirming one: "UI specification as
  source of truth long-lived success"; expected: few documented cases,
  most of them generated or tested.
- **Stop rule:** nothing new from a differently worded query and every
  route has a primary source; ten to fifteen pages opened.

**Baseline to beat (`2026-10-03-how-a-solution-design-is-built.md`).**
The attached note on technical solution design [1] established that
software design documents split into the frozen "design of a change"
and the living "description of a system", that only the second tries to
stay true and is documented to go stale, that Boeckeler (2025) divides
spec-driven development into `spec-first`, `spec-anchored`, and
`spec-as-source` while likening `spec-as-source` to model-driven
development and warning of review fatigue over repetitive Markdown
files, and that living technical documentation survives only when it
holds what cannot be read off the code, links rather than copies, and is
verified by automated checks. It did not examine interface design (the
layout and behaviour of screens), visual design systems (tokens and
component libraries), model-based UI generation (Cameleon, MBUI, UIMS),
imperative vs. declarative Gherkin UI specifications, the "prototype as
spec" and "interface first" movements, or 2026 empirical measurements of
AI-agent specification drift. Throughout this note, "interface design"
means the layout and interactive behaviour of screens, "technical
design" means the architectural layer between requirements and tasks,
and "visual design system" means the shared visual identity and
component library.

## Key findings

Every web source below ([2]–[16]) was opened through a summarising
fetch tool that returns extracted metadata, headings, and verbatim
passages rather than the raw page; the attached local note [1] was read
in full.

**F1. Heavy upfront textual specifications of interfaces failed and were
abandoned in product and UX practice because prose creates an "illusion
of agreement", hides usability flaws until code is built, locks in
screen decisions when the team has the least information, and encourages
feature bloat** [consensus | practitioner claims]. In *Getting Real*
(Chapter 59, "There's Nothing Functional about a Functional Spec"),
37signals records six reasons why textual functional specifications
"wind up having almost nothing to do with the finished product": they
are "fantasies" ("just words on paper"), serve "appeasement" rather
than exposing trade-offs, produce "an illusion of agreement" ("Everyone
may be reading the same thing but they're thinking something
different"), "force you to make the most important decisions when you
have the least information", cause "feature overload" ("There's no cost
to writing something down and adding another bullet point... And that's
how you wind up with an overloaded site that's got 30 tabs across the
top of the screen"), and prevent evolution once signed off [2]. In
*Smashing Magazine* (2011, under heading "Lean UX"), Jeff Gothelf states
that traditional UX had placed designers "in the deliverables business
— measured and compensated for the depth and breadth of their
deliverables instead of the quality and success of the experiences they
design", calling on teams to "forgo the hefty spec documents" and strip
documentation "down to their bare components, providing the minimum
amount of information necessary to get started on implementation" [4].
In *Revisiting the Product Spec* (2006), Marty Cagan notes that a
"50-page Word document that few will read and is impossible to test"
cannot validate usability or value before engineering begins [5]. In
2026, Deepak Babu Piskala (arXiv:2602.00180, Section VIII, "When to Use
SDD") repeats the same boundary for AI-assisted Spec-Driven Development:
"Exploratory coding suffers from premature specification that constrains
learning when you don't yet know what you're building" [11]. (Rests on
summarised fetches of [2], [4], [5], [11].)

**F2. Automatic generation of user interfaces from abstract textual or
declarative models (MBUI and MDD) failed to achieve wide industry
adoption because of a high learning threshold, a low ceiling on custom
interface expressiveness, unpredictable layout heuristics, and
unsustainable language and template maintenance costs** [consensus |
academic surveys and empirical study of 450 practitioners]. In their
survey of user interface software tools (*ACM TOCHI*, 2000, Section
2.3.4, "Model-Based and Automatic Generation Techniques", and Section 3,
"Discussion of Themes"), Brad Myers, Scott Hudson, and Randy Pausch
examine declarative and model-based UI generators (including Cousin,
Open-Dialogue, Mike, Jade, UIDE, ITS, and Humanoid) and state:
"Automatic and model based techniques have suffered from the problems of
unpredictability. In fact, because heuristics are often involved, the
connection between specification and final result can be quite difficult
to understand and control", adding that "model based systems have a low
ceiling. Because automatically generating interfaces is a very difficult
task, automatic and model based systems have each placed significant
limitations on the kinds of interfaces they can produce" [6]. By 2014,
when the W3C Model-Based User Interfaces Working Group published its
final Working Group Note (*Introduction to Model-Based User Interfaces*,
2014-01-07, Section 1), the editors recorded that although tools
followed the four-layer Cameleon Reference Framework (Tasks and
Concepts, Abstract UI, Concrete UI, Final UI), "none of them, so far,
implements the MBUID standard", and the document ended as a draft Working
Group Note without W3C endorsement [7]. Pierre Akiki, Arosha Bandara,
and Yijun Yu (*ACM Computing Surveys*, 2014/2015, Section 1 and
Outlook) note that early model-based UI systems fell victim to the
"moving targets problem" as interface platforms evolved faster than the
modelling tools and incurred high integration costs on existing systems
[9]. In a broader empirical study of Model-Driven Engineering across 450
survey respondents and 22 practitioner interviews (*IEEE Software*, May
2014, Section "Why MDE Efforts Succeed or Fail"), Jon Whittle, John
Hutchinson, and Mark Rouncefield conclude that "MDE can work, but it is
a struggle. MDE tools do not seem to support those who try", quoting
practitioners on the runaway cost of custom domain-specific languages
and code generation templates: "the complexity of these little [DSL]
languages started to grow and grow and grow... we were trying to share
the [code generation] templates across teams and versioning and
releasing of these templates was not under any kind of control at all",
and "the cost of sustaining just grows and it becomes eventually
unacceptable because a language requires maintenance, it requires
tooling, it requires education" [8]. (Rests on summarised fetches of
[6], [7], [8], [9].)

**F3. Whether AI-assisted "spec-as-source" overcomes or repeats the
failure of model-driven development is contested: advocates claim regeneration
eliminates drift by construction, whereas empirical reviewers report
repetitive Markdown bloat, review fatigue, and non-deterministic drift**
[contested | practitioner audit vs. technical report]. In her October
2025 evaluation of Kiro, spec-kit, and Tessl on *martinfowler.com*,
Birgitta Boeckeler warns that `spec-as-source`—where humans edit only
the specification and code is generated—parallels MDD: "The models in
MDD were basically the specs, albeit not in natural language, but
expressed in eg custom UML or a textual DSL" [10]. She reports that
spec-kit generated so many repetitive Markdown files across layers that
"To be honest, I'd rather review code than all these markdown files",
and that an agent misread descriptions of existing classes as instructions
to generate duplicates [1], [10]. Contradicted in part by Piskala
(2026-01-30, arXiv:2602.00180, Section II-C, "Spec-as-Source: Humans
Edit Specs, Machines Generate Code"), who argues that when manual code
editing is prohibited, "drift is eliminated by design: since code is
regenerated rather than manually edited, spec and code are always
aligned by construction", though Piskala adds the caveat in Section VIII
("The Golden Rule") to use `spec-as-source` "only when generation
tooling is mature and trusted" and warns in Section IX ("Common
Pitfalls") against **Over-specification**: "If your spec reads like
code, you've gone too far—you've constrained implementation
unnecessarily and lost the abstraction benefit that makes specs
valuable" [11]. (Rests on [1] in full and summarised fetches of [10],
[11].)

**F4. Textual behaviour-driven development (BDD) and Gherkin
specifications for user interfaces failed when written imperatively in
terms of screen mechanics, because UI layouts and selectors change far
more often than domain rules** [consensus | official tool documentation
and practitioner reports]. In the official Cucumber documentation
(*Writing better Gherkin*, section "Consider a more declarative style"),
the authors state why UI-coupled textual scenarios become brittle and
get abandoned: "Imperative tests communicate details, and in some
contexts this style of test is appropriate. On the other hand, because
they are so closely tied to the mechanics of the current UI, they often
require more work to maintain. Any time the implementation changes, the
tests need to be updated too" [14]. Martin Fowler (*Page Object*,
2013-09-10) records the same failure mode for test specifications wired
directly to markup: "if you write tests that manipulate the HTML
elements directly your tests will be brittle to changes in the UI" [15].
When Gherkin feature files specify field names, button clicks, and DOM
containers, a visual redesign breaks hundreds of textual scenarios even
when the underlying user capability is unchanged, destroying their role
as readable living documentation [14], [15]. (Rests on summarised
fetches of [14], [15].)

**F5. Static textual descriptions, style guides, and spec-anchored
documents drift from the product within weeks unless enforced; in AI
agent workflows, stale specifications actively cause silent implementation
failures** [consensus | practitioner reports and 2026 observational
study]. In *Atomic Design* (2016, Chapter 5, "Maintaining Design
Systems"), Brad Frost writes: "There's a very real risk that a style
guide will end up in the trash can right alongside all the PSDs, PDFs
and those other static artifacts of the design process" when treated as
a static deliverable rather than a living product [16]. Piskala
(2026-01-30, arXiv:2602.00180, Section X, "SDD vs Traditional Design
Documents") summarizes the lifecycle of unanchored specifications: "The
problem is not the absence of specs—it's that they drift. By Sprint 3,
the HLD is outdated. By release 2, the SRS no longer matches the
product. The code becomes the de facto truth, and the documents become
historical artifacts that nobody trusts or updates" [11]. In an
empirical study of 283 agentic coding sessions on a 108,000-line C#
system using 34 on-demand Markdown specifications (~16,250 lines total),
Aristidis Vasilopoulos (2026-02-24, arXiv:2602.20478, Section 5.1,
Guideline G6, and Section 5.2, "Maintenance Cost") reports:
"Specification staleness was the primary failure mode", and formulates
Guideline G6 ("Stale specs mislead efforts"): "Agents trust
documentation, and out-of-date specs can mislead sessions and lead to
silent failures" [12]. (Rests on summarised fetches of [11], [12],
[16].)

**F6. Critics of describing interfaces in text propose two replacements:
(a) the interactive prototype or live HTML screen as the specification
during discovery and handoff, accompanied by at most a one-page story or
a supplementary list of edge cases, and (b) production component code as
the single source of truth during maintenance** [consensus |
practitioner claims and vendor documentation].
- *The prototype or real screen as the specification:* 37signals
  (*Getting Real*, Chapters 46 and 59) replaces the functional spec with
  a one-page plain-language story ("If it takes more than a page to
  explain it, then it's too complex. This process shouldn't take more
  than one day") followed immediately by paper sketches and live HTML
  screens: "the interface will be the alternative to the functional
  spec... Unlike paragraphs of text that are open to alternate
  interpretations, interface designs are common ground that everyone can
  agree on" [2], [3]. Marty Cagan (*SVPG*, 2006) names this pattern
  "prototype as spec": "The primary way we communicate what needs to be
  built by the engineers is via the prototype we created in product
  discovery. This is referred to as 'prototype as spec.' That said,
  there are often additional aspects of the specification that are not
  easily communicated in a prototype, and these are spelled out in the
  PRD. This is usually an enumeration of specific use cases, and
  non-functional requirements" [5].
- *Production code as the source of truth:* Storybook's official
  documentation (*Why Storybook*, section "Document UI for your team to
  reuse") positions the rendered component code and its stories as the
  authoritative specification: "Storybook is the single source of truth
  for your UI. Stories index all your components and their various
  states, making it easy for your team to find and reuse existing UI
  patterns" [17]. (Rests on summarised fetches of [2], [3], [5], [17].)

**F7. The textual interface descriptions that survive and stay true rely
on four mechanisms: generation from production code, automated tests
bound to declarative text via an abstraction layer, a narrow structural
scope (tokens, component contracts, or non-obvious decisions), and
same-session update discipline** [consensus | official documentation,
audit, and 2026 empirical studies].
1. *Generation from the product and programmatic binding:* Storybook
   auto-generates component documentation and prop tables directly from
   production component stories and types ("Storybook also
   auto-generates documentation from those stories") [17]. Figma's Code
   Connect (*Code Connect Introduction*) prevents drift between design
   tool components and code by linking repository components directly
   into Dev Mode and MCP servers: "Code Connect is a bridge between your
   codebase and Figma's Dev Mode, connecting components in your
   repositories directly to components in your design files... giving
   them direct references to your actual code" [18].
2. *Tests bound to declarative text through an abstraction layer:*
   Piskala (2026-01-30, Section IX) states that for `spec-anchored`
   documentation, "The solution is automated enforcement through tests
   that fail when spec and code diverge, making drift visible and
   painful rather than silent and accumulating" [11]. For interfaces,
   Cucumber (*Writing better Gherkin*) and Fowler (*Page Object*, 2013;
   *Subcutaneous Test*, 2011) show that textual specifications survive UI
   redesigns only when written declaratively around user behaviour ("When
   Free Frieda logs in with her valid credentials") while pushing HTML
   selectors into a `PageObject` wrapper or testing via a subcutaneous
   layer just beneath the UI [14], [15], [19].
3. *A narrow scope:* In the baseline note [1], BMad's architecture spine
   and ADRs stay true by recording only non-obvious trade-offs while
   leaving file trees and schemas to the code ("the code owns them"). In
   UI practice, Cagan restricts text alongside the prototype to specific
   use cases and non-functional requirements not visible in the
   prototype [5]; 37signals restricts pre-UI text to a one-page story
   [2].
4. *Same-session co-maintenance with agent diagnostics:* In
   Vasilopoulos's 283-session study (2026-02-24, Section 5.2), 34
   Markdown specifications (~16,250 lines) were kept current across a
   108,000-line codebase by updating the specification in the same
   session as the code change ("typically one or two prompts directing
   the AI to update the relevant document, adding roughly 5 minutes per
   session when a specification was affected"), supplemented by a
   30–45 minute biweekly review pass (totalling 1–2 hours per week) and
   using agent confusion as a trigger that a spec had drifted [12].
   (Rests on [1] in full and summarised fetches of [2], [5], [11], [12],
   [14], [15], [17], [18], [19].)

## Unexpected

**In AI-agent visual design specifications (`DESIGN.md`), textual
specification of UI components fails at authoring time before temporal
drift even begins** [13]. The card asks where textual descriptions
drifted from the product over time and tests the idea that every screen
element has a Markdown definition of its own. Jialiang Wei and Walid
Maalej (2026-11-13, arXiv:2611.17713, Abstract and Section IV-C, "What
the Specifications Contain") collected 613,207 `DESIGN.md` files from
GitHub in October 2026 and analysed the 36,906 files (17,240 unique
contents across 15,794 repositories) that passed the official
`@google/design.md` linter v0.4.0. They found that while visual design
tokens for colours and typography were structured in nearly all files,
fewer than half contained structured component tokens; 47.5% (8,181
unique contents) had a `Components` heading with zero recognized
component tokens, falling back to unstructured prose. Furthermore,
68.7% of repository files (49.1% of unique contents) triggered linter
warnings inside the specification itself: among the 7,817 unique
contents that defined component tokens, 88.8% declared colour tokens
referenced by no component, 43.2% specified component text/background
pairs failing the 4.5:1 contrast threshold, and 30.6% invented
unrecognized component properties. In addition, 53.3% of all lint-valid
`DESIGN.md` files on GitHub were byte-identical copies (Section V, RQ2).
(Rests on a summarised fetch of [13].)

**In agentic workflows, stale textual specifications are not passive
dead weight; they actively cause silent failures in generated code**
[12]. Pre-agent critiques of functional specs (37signals [2], Frost
[16], Ubl in [1]) treat outdated specifications as "dead documents"
that human developers simply ignore in favour of the code. Vasilopoulos
(2026-02-24, arXiv:2602.20478, Section 5.1, Guideline G6) shows that
this assumption does not hold when an AI coding agent is in the build
loop: "treat specifications as load-bearing, because agents trust
documentation absolutely and out-of-date specs cause silent failures". A
drifted textual UI specification handed to a coding agent will lead the
agent to overwrite valid code changes with the obsolete specification.
(Rests on a summarised fetch of [12].)

## Not found

- **Long-lived, ungenerated prose specifications of screen layouts and
  flows as a source of truth:** The confirming/disconfirming query (`"UI
  specification as source of truth long-lived success"`) and targeted
  searches across ACM/IEEE repositories and arXiv returned no empirical
  post-mortem of a prose or Markdown document describing full screen
  layouts and interactive flows that remained an accurate source of
  truth over multiple releases without either (a) generating the code
  from the model/spec or (b) binding executable acceptance tests or
  component extractors to it.
- **Commercial implementations of the W3C MBUI standard:** The W3C MBUI
  Working Group Note (2014-01-07) explicitly records that zero tools
  implemented the MBUID standard at publication [7]; no subsequent W3C
  Recommendation was found.
- **Measured longitudinal drift rates between `DESIGN.md` files and CSS
  or component code across commits:** Wei and Maalej (2026-11-13,
  Section V, RQ5, and Section VI, "Limitations") note that their October
  2026 dataset captures a single commit snapshot per repository and
  identifies measuring design-to-implementation drift between
  `DESIGN.md` tokens/components and CSS/Tailwind code as an open,
  unmeasured research question [13].
- **Verbatim body text from Gojko Adzic's 2010 blog post on `gojko.net`:**
  A fetch of `gojko.net/2010/04/13/how-to-implement-ui-testing-without-shooting-yourself-in-the-foot-2/`
  returned only the title, date, and three layer names ("Business
  Rules", "Workflow", "Technical Activity") via a secondary reference
  without verbatim body paragraphs from the original host.

## Options

The project's frame proposes a versioned Markdown UX/UI description kept
in git, co-authored by a human and an AI agent, handed to a build stage,
and updated when the interface changes, testing the idea that every
screen element has a small Markdown definition carrying its function and
a page definition names which elements it holds and where they stand.
Against the failure modes recorded in F1–F7, four structural options
exist:

1. **Option A: Full `spec-as-source` in Markdown (per-element and
   per-page Markdown definitions as the sole edited artefact; UI code is
   generated and never edited by hand).**
   - *For:* Eliminates code-to-spec drift by construction [11]; gives a
     complete textual inventory in git.
   - *Against:* Directly repeats the historical failure of Model-Based
     UI (MBUI) and MDD (F2)—high threshold, low ceiling on custom micro-
     interactions, and unpredictable layout heuristics [6], [8]—while
     adding the 2025–2026 failure modes of repetitive Markdown volume,
     review fatigue [1], [10], over-specification into pseudo-code [11],
     and high authoring error rates on component definitions (47.5%
     failing to structure components and 88.8% unreferenced tokens in
     `DESIGN.md` files [13]). Any manual hotfix in UI code immediately
     breaks the regime.
2. **Option B: `Spec-first` disposable proposal + rendered prototype/code
   as the source of truth.** The agent reads the upstream documents and
   proposes a concise textual UX/UI specification (one-page story and
   initial screen/element proposal) strictly to drive an immediate
   rendered preview or prototype; once the human tunes and approves the
   rendered interface and code is built, the component code (and
   Storybook/generated docs) owns the current state, and the prose
   proposal is archived as the history of the change (matching Family 1
   in [1]).
   - *For:* Avoids the #1 failure mode in Vasilopoulos (2026)—stale
     specs misleading coding agents into silent regressions [12];
     aligns with 37signals ("Interface First" [2], [3]), Lean UX [4],
     Cagan ("prototype as spec" [5]), and OpenSpec's archive rule [1].
   - *Against:* Leaves no single human-written Markdown document in git
     that describes the whole current interface for an agent or human to
     read without inspecting the codebase or running a generator.
3. **Option C: Narrow-scope `spec-anchored` Markdown + bidirectional
   code/test binding.** Keep the persistent Markdown UX/UI layer narrow:
   it records (a) visual design tokens, (b) declarative user
   capabilities and screen-level intent/constraints (why a screen exists,
   which requirements it fulfils, non-obvious UX trade-offs, and edge-case
   states that a static screen cannot show [1], [5]), and (c) stable
   element/screen IDs linked to production component file paths. Exclude
   imperative UI mechanics (selectors, pixel placements, low-level DOM
   structure) that belong to the component code [1], [14], [15]. Bind the
   Markdown to the build via automated checks (a linter for internal
   consistency [13], declarative acceptance tests behind a Page Object /
   subcutaneous layer [14], [15], [19], and auto-generated component
   inventories from code [17], [18]), and update the Markdown in the
   same agent session as every UI code change [12].
   - *For:* The only long-lived textual model supported by surviving
     evidence across BDD [14], living documentation [1], and 2026
     agentic context studies [11], [12]; keeps maintenance overhead
     bounded (~5 minutes per session plus periodic review in [12]).
   - *Against:* Requires discipline and automated fitness checks; does
     not let a reader reconstruct exact visual layout from Markdown
     alone without opening the preview or component stories.
4. **Option D: Granular per-element Markdown definitions + spatial page
   composition in prose (`spec-anchored` without code generation).**
   Every screen element (e.g. a search field) has its own Markdown
   definition file and every page file lists which elements it holds and
   where they stand, maintained manually alongside the code.
   - *For:* Matches the raw hypothesis heard from practice in the card's
     frame.
   - *Against:* Combines the dual-maintenance trap of imperative UI
     Gherkin (F4, where renaming or moving an element forces parallel
     updates to text and code [14], [15]), the repetitive file explosion
     reported by Boeckeler on spec-kit (`I'd rather review code than all
     these markdown files` [1], [10]), and the silent-regression hazard
     when an element is adjusted in code and its Markdown file is missed
     [12].

## Relevance to this project

**Recommendation:** Adopt **Option C** (narrow-scope `spec-anchored`
Markdown bound to automated checks and same-session agent updates) for
what must stay true across the application's life, combined with
**Option B**'s rule that the human judges the interface through a
rendered preview/prototype rather than signing off on unrendered prose.
Reject **Option A** (pure `spec-as-source` UI generation without manual
code ownership) and **Option D** (manual per-element and spatial layout
inventories duplicated in prose).

What this recommendation rests on:
1. **Test the "every element in Markdown / where they stand on the page"
   idea against the evidence:** Writing down every UI element and its
   spatial placement in prose and maintaining it alongside code is the
   exact structural equivalent of imperative UI Gherkin [14], [15] and
   spec-kit's repetitive file trees [1], [10]. In Wei and Maalej's
   November 2026 study of 36,906 `DESIGN.md` files, even basic
   component-level token specifications in Markdown failed in 47.5% of
   cases (dropping back to untyped prose) and produced 88.8% unreferenced
   colour warnings when attempted [13]. *This note's inference:* if a
   small definition of a reusable element exists, it should be either
   generated from / linked to the production component file (as in
   Storybook Autodocs [17] and Figma Code Connect [18], or the file-path
   citation rule of the baseline solution-design note [1]) or scoped
   strictly to the element's functional contract and domain state—never
   a manual prose copy of its DOM props or pixel coordinates.
2. **Never ask the human to approve a UX/UI proposal from text alone:**
   37signals [2], [3], Gothelf [4], and Cagan [5] agree that text creates
   an "illusion of agreement" about an interface. The project's frame
   already states that "a human tunes the proposal and sees it"; this
   research confirms that *seeing* the rendered preview or interactive
   prototype is mandatory before decisions harden, because exploratory
   interface work suffers from premature specification [11].
3. **Keep UI mechanics out of behavioural text:** Where the UX/UI
   document specifies user flows or acceptance criteria, it must use
   declarative domain and user-intent language rather than imperative UI
   mechanics ("click button X", "type in field Y"), leaving the mapping
   to UI elements inside the test/component layer [14], [15].
4. **Make same-session updates and automated drift checks mandatory:**
   Because AI coding agents trust Markdown specifications unconditionally
   and stale specs cause silent regressions [12], any UX/UI Markdown
   document that stays alive after the first build (`spec-anchored`)
   must (a) be updated by the coding agent in the same session as any UI
   code change [12], and (b) be checked by a linter and fitness check
   that verifies referenced component paths, tokens, and acceptance
   scenarios against the codebase [1], [11], [13].

**Consult when:**
- deciding how granular the Markdown UX/UI specification should be (in
  particular, whether individual screen widgets and their spatial layout
  belong in hand-maintained Markdown or in code/previews);
- designing the workflow that keeps the UX/UI document in sync after the
  first build;
- writing rules for what the AI agent puts into screen, flow, or
  component descriptions vs. what it leaves to the component code.

## Sources

1. **How a solution design is built** (`2026-10-03-how-a-solution-design-is-built.md`),
   forge project research note, 2026-10-03 (dated by YAML front matter),
   local workspace file; kind: secondary (project baseline note); how
   read: in full; original.
2. **Getting Real, Chapter 59: There's Nothing Functional about a
   Functional Spec**, 37signals (Jason Fried, David Heinemeier Hansson,
   and Matthew Linderman), undated on page (book first published 2006),
   `https://basecamp.com/gettingreal/59-theres-nothing-functional-about-a-functional-spec`;
   kind: primary (read through a tertiary summarised fetch); how read:
   summarised fetch (returned full chapter headings and verbatim text);
   original.
3. **Getting Real, Chapter 46: Interface First**, 37signals (Jason
   Fried, David Heinemeier Hansson, and Matthew Linderman), undated on
   page (book first published 2006),
   `https://basecamp.com/gettingreal/46-interface-first`; kind: primary
   (read through a tertiary summarised fetch); how read: summarised
   fetch (returned full chapter heading and verbatim text); original.
4. **Lean UX: Getting Out Of The Deliverables Business**, Jeff Gothelf
   (*Smashing Magazine*), 2011-03-07 (dated by URL and byline),
   `https://www.smashingmagazine.com/2011/03/lean-ux-getting-out-of-the-deliverables-business/`;
   kind: primary (read through a tertiary summarised fetch); how read:
   summarised fetch (section headings and verbatim quotes); original.
5. **Revisiting the Product Spec**, Marty Cagan (Silicon Valley Product
   Group / SVPG), 2006-10-12 (dated by byline),
   `https://www.svpg.com/revisiting-the-product-spec/`; kind: primary
   (read through a tertiary summarised fetch); how read: summarised
   fetch (verbatim quotes on 50-page specs and "prototype as spec");
   original.
6. **Past, Present, and Future of User Interface Software Tools**, Brad
   A. Myers, Scott E. Hudson, and Randy Pausch (*ACM Transactions on
   Computer-Human Interaction*, Vol. 7, No. 1, pp. 3–28), 2000-03
   (dated by publication header),
   `http://www.cs.cmu.edu/~amulet/papers/futureofhci.pdf`; kind: primary
   (read through a tertiary summarised fetch); how read: summarised
   fetch (Section 2.3.4 "Model-Based and Automatic Generation
   Techniques" and Section 3 "Discussion of Themes" verbatim quotes);
   original (authors' CMU repository PDF).
7. **Introduction to Model-Based User Interfaces**, Gerrit Meixner,
   Gaëlle Calvary, and Joëlle Coutaz (eds., W3C Model-Based User
   Interfaces Working Group Note), 2014-01-07 (dated by W3C document
   header), `https://www.w3.org/TR/mbui-intro/`; kind: primary (read
   through a tertiary summarised fetch); how read: summarised fetch
   ("Status of This Document" and Section 1 on Cameleon Reference
   Framework and lack of MBUID standard implementations); original.
8. **The State of Practice in Model-Driven Engineering**, Jon Whittle,
   John Hutchinson, and Mark Rouncefield (*IEEE Software*, Vol. 31,
   No. 3, pp. 79–85, via University of Sheffield ReMoDeL repository),
   2014-05 (dated by journal metadata),
   `https://www.shef.ac.uk/remodel/whatismde/reading`; kind: primary
   (read through a tertiary summarised fetch); how read: summarised
   fetch (outline and verbatim quotes from practitioner interviews on
   MDE tool and DSL maintenance failures); original.
9. **Adaptive Model-Driven User Interface Development Systems**, Pierre
   A. Akiki, Arosha K. Bandara, and Yijun Yu (*ACM Computing Surveys*,
   Vol. 47, No. 1, via Open University Open Research Online), 2014-05
   (dated by repository metadata; print issue March 2015),
   `https://oro.open.ac.uk/40240/1/Akiki-Surveys-Manuscript.pdf`; kind:
   primary (read through a tertiary summarised fetch); how read:
   summarised fetch (Section 1, Section 2, and Outlook verbatim quotes);
   original (authors' accepted manuscript).
10. **Understanding Spec-Driven-Development: Kiro, spec-kit, and Tessl**,
    Birgitta Boeckeler (*martinfowler.com*), 2025-10-15 (dated by
    byline),
    `https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html`;
    kind: primary (read through a tertiary summarised fetch and [1]);
    how read: summarised fetch (verbatim quotes on `spec-as-source`,
    MDD parallels, and Markdown review fatigue); original.
11. **Spec-Driven Development: From Code to Contract in the Age of AI
    Coding Assistants**, Deepak Babu Piskala (*arXiv*,
    `arXiv:2602.00180`), 2026-01-30 (dated by arXiv v1 submission
    record), `https://arxiv.org/abs/2602.00180`; kind: primary (read
    through a tertiary summarised fetch); how read: summarised fetch
    (Abstract, Section II "The Specification Spectrum", Section VIII
    "When to Use SDD", Section IX "Common Pitfalls", and Section X "SDD
    vs Traditional Design Documents" verbatim quotes); original.
12. **Codified Context: Infrastructure for AI Agents in a Complex
    Codebase**, Aristidis Vasilopoulos (*arXiv*, `arXiv:2602.20478`),
    2026-02-24 (dated by arXiv v1 submission record),
    `https://arxiv.org/abs/2602.20478`; kind: primary (read through a
    tertiary summarised fetch); how read: summarised fetch (Abstract,
    Section 5.1 Guideline G6, and Section 5.2 "Maintenance Cost"
    verbatim quotes); original.
13. **DesignSpecs: A DESIGN.md Dataset of Visual Design Specifications
    for AI Agents**, Jialiang Wei and Walid Maalej (*arXiv*,
    `arXiv:2611.17713`), 2026-11-13 (dated by arXiv v1 submission
    record), `https://arxiv.org/abs/2611.17713`; kind: primary (read
    through a tertiary summarised fetch); how read: summarised fetch
    (Abstract, Section IV-C "What the Specifications Contain", Section V
    "Research Opportunities", and Section VI "Limitations" verbatim
    quotes); original.
14. **Writing better Gherkin**, Cucumber Documentation (*Cucumber.io*),
    undated, `https://cucumber.io/docs/bdd/writing-better-gherkin/`;
    kind: primary (vendor/tool documentation, read through a tertiary
    summarised fetch); how read: summarised fetch (section "Consider a
    more declarative style" verbatim quotes); original.
15. **Page Object**, Martin Fowler (*martinfowler.com*), 2013-09-10
    (dated by byline), `https://martinfowler.com/bliki/PageObject.html`;
    kind: primary (read through a tertiary summarised fetch); how read:
    summarised fetch (opening paragraph verbatim quote on UI brittleness
    and page object wrapping); original.
16. **Atomic Design, Chapter 5: Maintaining Design Systems**, Brad
    Frost, undated on chapter page (book published 2016),
    `https://atomicdesign.bradfrost.com/chapter-5/`; kind: primary (read
    through a tertiary summarised fetch); how read: summarised fetch
    (opening section verbatim quotes on static style guides and living
    systems); original.
17. **Why Storybook**, Storybook Documentation (*storybook.js.org*),
    undated, `https://storybook.js.org/docs/get-started/why-storybook`;
    kind: primary (tool documentation, read through a tertiary
    summarised fetch); how read: summarised fetch (headings and section
    "Document UI for your team to reuse" verbatim quote); original.
18. **Code Connect Introduction**, Figma Developer Documentation
    (*figma.com*), undated,
    `https://www.figma.com/developers/docs/code-connect/intro`; kind:
    primary (vendor documentation, read through a tertiary summarised
    fetch); how read: summarised fetch (headings and introductory
    verbatim quotes); original.
19. **Subcutaneous Test**, Martin Fowler (*martinfowler.com*),
    2011-02-14 (dated by byline),
    `https://martinfowler.com/bliki/SubcutaneousTest.html`; kind:
    primary (read through a tertiary summarised fetch); how read:
    summarised fetch (opening paragraph verbatim quote); original.

## Opened and not used

- **How to implement UI testing without shooting yourself in the foot**,
  Gojko Adzic (`http://gojko.net/2010/04/13/how-to-implement-ui-testing-without-shooting-yourself-in-the-foot-2/`,
  2010-04-13): summarised fetch returned only the URL, date, and three
  layer names via a secondary blog without verbatim body text from
  `gojko.net`; superseded by [14] and [15].
- **Automatic documentation and Storybook (Autodocs)**, Storybook
  Documentation (`https://storybook.js.org/docs/writing-docs/autodocs`,
  undated): summarised fetch returned section headings only; superseded
  by [17].

## Search record

**Queries run (in order):**
1. `UI specification document failure drift prototype source of truth`
2. `BDD Gherkin user interface specification failure brittle maintenance`
3. `model-driven UI generation failure MBUI MDD review fatigue spec-as-source`
4. `UI specification as source of truth long-lived success` (disconfirming query)
5. `"Functional Specs" "Getting Real" Basecamp 37signals interface specification`
6. `"Past, Present, and Future of User Interface Software Tools" Myers model-based automatic generation failure`
7. `Gojko Adzic "UI" "Specification by Example" OR "How to implement UI testing without shooting yourself in the foot"`
8. `Cucumber anti-patterns UI imperative declarative Gherkin brittle`
9. `"Functional Specs" "Getting Real" basecamp exact URL verbatim quotes headings` (`domain: basecamp.com`)
10. `"Past, Present, and Future of User Interface Software Tools" Myers Hudson Pausch 2000 "Model-Based" verbatim quotes exact URL` (`domain: cmu.edu`)
11. `"Cucumber Anti-Patterns" OR "imperative" "declarative" UI brittle exact URL date author verbatim quotes` (`domain: cucumber.io`)
12. `"How to implement UI testing without shooting yourself in the foot" Gojko Adzic 2010 exact URL verbatim quotes headings` (`domain: gojko.net`)
13. `"Lean UX" Gothelf OR "Marty Cagan" "prototype" specification deliverables drift source of truth`
14. `"Storybook" OR "Brad Frost" OR "Nathan Curtis" design system drift "source of truth" code vs specification`
15. `"Past, Present, and Future of User Interface Software Tools" "Model-Based" "unpredictable" OR "limitations" OR "threshold" OR "ceiling" verbatim quotes exact URL` (`domain: cmu.edu`)
16. `"Understanding Spec-Driven-Development: Kiro, spec-kit, and Tessl" Boeckeler "model-driven" OR "MDD" OR "spec-as-source" OR "review" verbatim quotes` (`domain: martinfowler.com`)
17. `"atomicdesign.bradfrost.com/chapter-5" spec style guide drift outdated source of truth verbatim quotes` (`domain: bradfrost.com`)
18. `Marty Cagan prototype specification PRD失敗 OR fail verbatim quotes exact URL date` (`domain: svpg.com`)
19. `"how-to-implement-ui-testing-without-shooting-yourself-in-the-foot" verbatim quotes three levels business rules workflow` (`domain: gojko.net`)
20. `"spec-driven" OR "UI specification" "source of truth" drift agent 2025 2026 exact arXiv ID title authors` (`domain: arxiv.org`)
21. `"Lean UX: Getting Out Of The Deliverables Business" Jeff Gothelf 2011 exact URL headings verbatim quotes` (`domain: smashingmagazine.com`)
22. `"2602.00180" "Spec-Driven Development: From Code to Contract" Piskala date abstract sections verbatim quotes` (`domain: arxiv.org`)
23. `"Better Gherkin" "Imperative tests communicate details" "Declarative style describes" exact URL headings` (`domain: cucumber.io`)
24. `"shooting yourself in the foot" OR "UI testing" OR "Specification by Example" UI brittle change verbatim quotes` (`domain: gojko.net`)
25. `"Why Storybook" OR "Autodocs" source of truth out of date documentation verbatim quotes exact URL headings` (`domain: storybook.js.org`)
26. `"The State of Practice in Model-Driven Engineering" Whittle OR "Adaptive Model-Driven User Interface Development Systems" Akiki failure adoption verbatim quotes`
27. `"The State of Practice in Model-Driven Engineering" Whittle Hutchinson Rouncefield exact URL year journal headings` (`domain: shef.ac.uk`)
28. `"Adaptive Model-Driven User Interface Development Systems" Akiki Bandara Yu exact URL year journal headings verbatim quotes` (`domain: open.ac.uk`)
29. `"PageObject" OR "SubcutaneousTest" Fowler brittle UI tests specification exact URL date verbatim quotes` (`domain: martinfowler.com`)
30. `"2602.00180" Piskala "spec-as-source" OR "drift" OR "UI" OR "challenges" OR "limitations" verbatim quotes sections` (`domain: arxiv.org`)
31. `"Autodocs" "storybook.js.org/docs/writing-docs/autodocs" exact URL headings verbatim quotes` (`domain: storybook.js.org`)
32. `"basecamp.com/gettingreal" "Functional Specs" exact URL chapter number title` (`domain: basecamp.com`)
33. `"There’s Nothing Functional about a Functional Spec" "Interface First" basecamp.com/gettingreal exact URLs verbatim text` (`domain: basecamp.com`)
34. `"2602.00180" "Spec-Driven Development: From Code to Contract" section headings verbatim quotes from arxiv.org pdf html` (`domain: arxiv.org`)
35. `"2010/04/13" OR "Specification by Example" UI user interface tests documentation gojko.net exact URL date verbatim quotes` (`domain: gojko.net`)
36. `"Code Connect" "source of truth" drift design system documentation exact URL date headings verbatim quotes` (`domain: figma.com`)
37. `"spec" OR "specification" "drift" UI model-driven code generation exact URL title authors year verbatim quotes` (`domain: openreview.net` — returned no summary)
38. `"2602.00180" "WHEN TO USE SDD" "COMMON PITFALLS" "SDD VS TRADITIONAL DESIGN DOCUMENTS" verbatim quotes` (`domain: arxiv.org`)
39. `"UI specification" OR "user interface" "drift" "source of truth" prototype 2024 2025 2026 exact arXiv ID title authors` (`domain: arxiv.org`)
40. `"how-to-implement-ui-testing-without-shooting-yourself-in-the-foot-2" verbatim quotes gojko.net` (`domain: gojko.net` — returned no candidates)
41. `"Introduction to Model-Based User Interfaces" "w3.org/TR/mbui-intro" Cameleon date authors status verbatim quotes` (`domain: w3.org`)
42. `"2602.00180" "IX. COMMON PITFALLS" "X. SDD VS TRADITIONAL DESIGN DOCUMENTS" verbatim quotes` (`domain: arxiv.org`)
43. `"2602.20478" "Codified Context" Vasilopoulos date abstract sections drift verbatim quotes` (`domain: arxiv.org`)
44. `"2611.17713" "DesignSpecs" "DESIGN.md" Wei Maalej date abstract sections verbatim quotes` (`domain: arxiv.org`)
45. `"w3.org/TR/mbui-intro" "Status of This Document" Working Group Note closed verbatim quotes` (`domain: w3.org`)
46. `"2602.00180" "Specification rot" "X. SDD VS TRADITIONAL DESIGN DOCUMENTS" "VIII. WHEN TO USE SDD" UI prototype exploratory verbatim quotes` (`domain: arxiv.org`)
47. `"2602.20478" "Codified Context" Vasilopoulos date of submission v1 specification drift maintenance verbatim quotes` (`domain: arxiv.org`)
48. `"2611.17713" "DesignSpecs" "IV-C. What the Specifications Contain" "V. Research Opportunities" "VI. Limitations" drift commits verbatim quotes` (`domain: arxiv.org`)

**Pages opened (20 total: 18 used in Sources [2]–[19], plus 2 in Opened and not used):**
1. `https://basecamp.com/gettingreal/59-theres-nothing-functional-about-a-functional-spec` [2]
2. `https://basecamp.com/gettingreal/46-interface-first` [3]
3. `https://www.smashingmagazine.com/2011/03/lean-ux-getting-out-of-the-deliverables-business/` [4]
4. `https://www.svpg.com/revisiting-the-product-spec/` [5]
5. `http://www.cs.cmu.edu/~amulet/papers/futureofhci.pdf` [6]
6. `https://www.w3.org/TR/mbui-intro/` [7]
7. `https://www.shef.ac.uk/remodel/whatismde/reading` [8]
8. `https://oro.open.ac.uk/40240/1/Akiki-Surveys-Manuscript.pdf` [9]
9. `https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html` [10]
10. `https://arxiv.org/abs/2602.00180` [11]
11. `https://arxiv.org/abs/2602.20478` [12]
12. `https://arxiv.org/abs/2611.17713` [13]
13. `https://cucumber.io/docs/bdd/writing-better-gherkin/` [14]
14. `https://martinfowler.com/bliki/PageObject.html` [15]
15. `https://atomicdesign.bradfrost.com/chapter-5/` [16]
16. `https://storybook.js.org/docs/get-started/why-storybook` [17]
17. `https://www.figma.com/developers/docs/code-connect/intro` [18]
18. `https://martinfowler.com/bliki/SubcutaneousTest.html` [19]
19. `http://gojko.net/2010/04/13/how-to-implement-ui-testing-without-shooting-yourself-in-the-foot-2/` (opened and not used)
20. `https://storybook.js.org/docs/writing-docs/autodocs` (opened and not used)

**What the disconfirming query found:**
The query `"UI specification as source of truth long-lived success"`
returned vendor blog posts (`intent-driven.dev`, `augmentcode.com`,
`uxpilot.ai`, `mindstudio.ai`, `shiplight.ai`, `scalablepath.com`), an
IBM overview page, and the 2026 arXiv preprint by Piskala (`arXiv:2602.00180`
[11]). Confirming the card's expectation, it surfaced no independent
case studies of ungenerated, untested prose screen specifications
surviving long-term; every documented long-lived pattern relied on
machine-readable tokens, code generation (`spec-as-source`), or
automated test/linter enforcement (`spec-anchored`).

**Reason the run ended:**
Both parts of the card's stop rule were met ("nothing new from a
differently worded query and every route has a primary source") and the
opening budget was reached.
