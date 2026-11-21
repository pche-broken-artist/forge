---
date: 2026-11-21
project: forge
topic: Map of textual UI/UX specification syntheses, standards, and vocabulary
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 1; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":52348,"output_tokens":19437,"thinking_tokens":10232,"cache_read_tokens":152253,"total_tokens":71785}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/01-map-of-the-field
status: immutable
---

# How user interfaces and user experience are specified in text across standards, practice, and 2024–2026 AI tooling

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

No single cross-disciplinary synthesis unites how user interfaces and
user experience are specified in text; instead, three separate
traditions maintain their own surveys, standards, and vocabularies.
Academic and standards work (1990s–2015) speaks of *Model-Based User
Interface Development (MBUID)*, *User Interface Description Languages
(UIDLs)*, the four-layer *CAMELEON reference framework* (Task and
Concepts, Abstract UI, Concrete UI, Final UI), W3C *MBUI* notes, and
OMG's *Interaction Flow Modeling Language (IFML)* [1, 2, 3, 7].
Practitioner UX and design-system work (2016–2026) speaks of *UX
deliverables*, *prototype specifications (annotations)*, *wireflows*,
*design handoff*, *design as code*, and *design tokens* standardized by
the W3C Design Tokens Community Group [8, 9, 10]. AI tooling of
2025–2026 speaks of *Spec-Driven Development (SDD)* across three rigor
levels (*spec-first*, *spec-anchored*, *spec-as-source*) using Markdown
files (`specify.md` / `requirements.md`, `plan.md` / `design.md`,
`tasks.md`) and *EARS* syntax [11, 12, 13]. The disconfirming query
confirmed that no universal UI specification standard exists, only
partial standards for tokens, accessibility, and abstract flows. The
chief unexpected finding is that 2025–2026 SDD toolkits have no
dedicated textual UI/UX specification layer, and their analysts warn
that *spec-as-source* risks repeating the maintenance failure of earlier
Model-Driven Development [11].

## Question

> A framework carries an idea down a chain of versioned Markdown
> documents kept in git: what is wanted and why, then business
> requirements, a solution design and user stories. A human works
> each document with an AI agent: the agent asks, proposes and
> writes, the human decides. Nothing is implemented there; the
> documents are handed on to be built. Its author wants the same for
> the user interface and the user experience of an application, and
> no such document exists yet: an AI agent reads the documents
> above, asks what it lacks and proposes a description of the
> interface in text; a human tunes the proposal and sees it; the
> description goes, with the other documents, to a build stage (a
> human developer, an AI coding agent, or both), and the cycle runs
> again when the interface changes. The author of a description is
> one person working end to end in a small project and a UX/UI
> specialist in a company. The targets are the web, the mobile web,
> native mobile and the desktop. Before anything is designed, a wide
> research asks how this is done elsewhere: which standards exist,
> what practice does, what the options are. This card is the first
> of twenty-two and runs before the others: the words and any
> synthesis it finds may rewrite them.

- **Question:** Does a synthesis already exist of how user interfaces
  and user experience are specified in text (a survey, a taxonomy, a
  comparison of approaches), and in which words do practice, the
  standards and the AI tooling of 2024 to 2026 speak of it (UI
  specification, functional specification, interaction specification,
  design handoff, design documentation, UI description language, design
  as code, spec-driven development)?
- **Why it matters:** every other card searches by the field's words,
  and a synthesis found here saves cards or rewrites them.
- **What would answer it:** survey and overview literature: academic
  surveys, standards bodies' overviews, overviews by practitioner
  organisations.
- **Where to look:** surveys of UI description languages and of
  model-based UI development; notes of the W3C; glossaries and
  overviews of practitioner organisations; recent overviews of
  spec-driven development that treat the interface. Must turn up: the
  W3C's model-based UI work, IFML, "design handoff".
- **Disconfirming query:** "why is there no standard for UI
  specification"; expected: several partial standards and no dominant
  one.
- **Stop rule:** nothing new from a differently worded query and every
  route has a primary source; ten to fifteen pages opened.

**Baseline the note must beat:** A surface list of buzzwords ("UIDL",
"design handoff", "spec-driven development") that treats them as
synonyms without distinguishing which layer of the interface each
tradition actually specifies, which standards reached formal adoption
versus Working Group Note retirement, and how 2025–2026 AI specification
workflows structure their Markdown artifacts.

## Key findings

*Note on evidence method: All findings below rest on summarised fetches
conducted via the environment's web-search grounding tool (`search_web`),
which retrieves and summarises source pages rather than returning raw
full-page HTML.*

- **F1. Academic syntheses of textual UI specification exist within the
  Model-Based User Interface Development (MBUID) tradition and classify
  User Interface Description Languages (UIDLs) along the four-layer
  CAMELEON taxonomy.** [consensus — academic surveys and standards body
  notes, via summarised fetch]
  Surveys by Guerrero-Garcia et al. (2009) [1] and Akiki, Bandara, and
  Yu (2014) [2], along with the W3C Model-Based User Interfaces (MBUI)
  Working Group Notes (2014) [3, 4], synthesis textual and XML-based UI
  specifications (such as UIML, UsiXML, MARIA, and XUL) along two main
  axes:
  1. *Abstraction levels (the CAMELEON reference framework)*: (a) *Task
     and Concepts*, capturing user goals, task hierarchies (often in
     ConcurTaskTrees, CTT), and domain objects [3, 5]; (b) *Abstract
     User Interface (AUI)*, defining modality- and platform-independent
     interaction containers and abstract interaction units [3, 6]; (c)
     *Concrete User Interface (CUI)*, binding elements to a specific
     modality and widget toolkit class while remaining independent of
     source code [3, 4]; and (d) *Final User Interface (FUI)*, the
     rendered markup or source code [3, 4].
  2. *Architectural facets*: presentation (structure and layout),
     dialogue/behavior (state transitions and event sequencing), domain
     data binding, and context-of-use adaptation (user, platform, and
     environment) [1, 2, 3].

- **F2. Formal standards for high-level UI and interaction specification
  stopped at W3C Working Group Notes (2014) and OMG's IFML 1.0 (2015),
  whereas low-level visual primitives achieved a stable Community Group
  specification in 2025 via W3C Design Tokens.** [consensus — standards
  documents, via summarised fetch]
  The W3C MBUI Working Group closed after publishing four Working Group
  Notes in January and April 2014 (*Introduction to Model-Based User
  Interfaces* [3], *MBUI Glossary* [4], *Task Models* [5], and *Abstract
  User Interface Models* [6]) rather than advancing them to formal W3C
  Recommendations [3]. In February 2015, the Object Management Group
  (OMG) published *Interaction Flow Modeling Language (IFML)* Version
  1.0 [7], a formal standard (derived from WebML) that specifies *View
  Containers*, *View Components*, *Events*, *Actions*, *Interaction
  Flows*, and *Parameter Bindings* across web, mobile, and desktop
  front-ends, while explicitly excluding visual presentation, layout
  coordinates, and graphic styling [7]. Conversely, at the lowest visual
  layer, the W3C Design Tokens Community Group (DTCG) published the
  first stable release (`Version 2025.10`, October 28, 2025, with draft
  updates through September 8, 2026) of the *Design Tokens Format
  Module* [8], standardizing platform-agnostic JSON representations of
  colors, typography, spacing, and sizing for "design as code" pipelines
  [8].

- **F3. Practitioner UX organisations (up to 2024–2026) reject standalone
  text-only "functional specification" documents for interfaces,
  replacing them with visual-plus-text hybrids: "prototype
  specifications (annotations)", "wireflows", and "design handoff"
  bundles.** [consensus — practitioner organisation glossaries and
  guides, via summarised fetch]
  According to the Nielsen Norman Group (NN/g) *UX Deliverables
  Glossary* by Huei-Hsin Wang (August 9, 2024) [9] and Page Laubheimer's
  NN/g report on *Wireflows* (December 4, 2016) [10], heavyweight text
  *functional specifications* have largely been superseded in UX
  practice by:
  1. *Wireframes* (skeletal page structure and hierarchy) [9];
  2. *Wireflows* (flowchart-style combinations of wireframes and process
     diagrams documenting multi-screen paths and dynamic states) [10];
  3. *Prototype specifications (or annotations)*, defined as text notes
     attached to wireframes or interactive prototypes to specify click
     effects, component states (default, hover, active, focus, disabled,
     error, loading, empty), edge cases, and business rules [9]; and
  4. *Design handoff* and *design documentation*, the practitioner terms
     for the designer-to-developer specification package combining
     component state tables, token references, responsive breakpoint
     rules, and accessibility (WCAG/ARIA) annotations [8, 9].

- **F4. Between 2025 and 2026, AI coding workflows converged on the term
  "Spec-Driven Development (SDD)" and a three-level taxonomy of
  specification persistence, using a four-stage Markdown chain.**
  [emerging — practitioner analysis, vendor documentation, and arXiv
  preprints, dated September 2025 to January 2026, via summarised fetch]
  In *Spec-Driven Development: From Code to Contract in the Age of AI
  Coding Assistants* (arXiv:2602.00180, January 30, 2026), Piskala
  writes in the Abstract: "Spec-driven development (SDD) inverts the
  traditional workflow by treating specifications as the source of truth
  and code as a generated or verified secondary artifact." [13]
  Birgitta Böckeler's analysis on `martinfowler.com` (October 15, 2025)
  [11], adopted by Piskala (January 30, 2026) [13], defines three levels
  of SDD across tools such as GitHub's `spec-kit` (introduced by Den
  Delimarsky on September 2, 2025 [12]), Amazon's `Kiro`, and `Tessl`:
  1. *Spec-first*: a specification is authored in text before coding to
     guide an AI agent on one task and then discarded [11, 13];
  2. *Spec-anchored*: the specification is kept under version control
     alongside code as a living artifact for ongoing maintenance and
     evolution [11, 13];
  3. *Spec-as-source*: humans edit only the specification, and source
     code is treated as a regenerable build output [11, 13].
  Across `spec-kit` and `Kiro`, the canonical Markdown chain is:
  (a) a *Constitution* or *Steering* files (`constitution.md`,
  `product.md`, `tech.md`) for global non-negotiable guardrails;
  (b) a *Specification* (`specify.md` or `requirements.md`, often using
  *EARS* — Easy Approach to Requirements Syntax — and acceptance
  criteria);
  (c) a *Plan* (`plan.md` or `design.md`) for technical architecture;
  and (d) *Tasks* (`tasks.md`) for implementation breakdown [11, 12,
  13].

- **F5. Vocabulary map across the field (1990s–2026): the same problem
  is indexed under distinct terms depending on the community and level
  of abstraction.** [consensus — synthesis of [1–14], via summarised
  fetch]
  Every subsequent research card must query using the terms native to
  the target sub-literature:
  - *Whole-workflow AI/git paradigm (2025–2026)*: **Spec-Driven
    Development (SDD)**, **spec-first**, **spec-anchored**,
    **spec-as-source**, **constitution.md**, **steering files**,
    **EARS syntax** [11, 12, 13].
  - *Academic & formal standards (2000–2015)*: **Model-Based User
    Interface Development (MBUID)**, **User Interface Description
    Language (UIDL)**, **CAMELEON reference framework**, **Task Model
    (CTT)**, **Abstract User Interface (AUI)**, **Concrete User
    Interface (CUI)**, **Interaction Flow Modeling Language (IFML)**
    [1, 2, 3, 5, 6, 7].
  - *Practitioner UX & handoff (2016–2026)*: **UX deliverables**,
    **prototype specifications**, **wireframe annotations**,
    **wireflows**, **interaction specification**, **UI specification**,
    **design handoff**, **design documentation** [9, 10].
  - *Design systems & machine-readable styling (2024–2026)*: **design as
    code**, **W3C Design Tokens (DTCG)**, **component specifications**,
    **variant/state matrix** [8, 9].
  - *AI UI generation benchmarks (2024–2026)*: **Image-to-Code**,
    **Design2Code**, **UI-to-Code**, **NL2UI** [14].

- **F6. Disconfirming finding: no unified standard for end-to-end UI
  specification exists because interfaces span subjective human factors,
  proprietary platform idioms, and decoupled abstraction layers.**
  [consensus — standards notes and disconfirming query synthesis, via
  summarised fetch]
  Running the disconfirming query (`"why is there no standard for UI
  specification"`) and examining the closure of the W3C MBUI Working
  Group [3] and the scope exclusions of OMG IFML [7] confirm that the
  field never converged on a single standard. Standards succeeded only
  when restricted to one narrow slice: visual tokens (*W3C Design
  Tokens* [8]), accessibility rules (*WCAG / WAI-ARIA*), or
  style-agnostic interaction flows (*IFML* [7]).

## Unexpected

**The card's frame assumes SDD or adjacent AI workflows may already have
a pattern for a dedicated textual UI/UX specification document in git;
primary 2025–2026 SDD sources show a gap where the UI document should
be, and warn against pure `spec-as-source` regeneration.** Across
Böckeler's evaluation of `Kiro`, `spec-kit`, and `Tessl` [11],
Delimarsky's `spec-kit` documentation [12], and Piskala's SDD survey
[13], the specification chain jumps directly from product requirements
(`specify.md` / `requirements.md`) to software architecture (`plan.md` /
`design.md`) and implementation tasks (`tasks.md`). User interfaces are
either folded into brief acceptance criteria, delegated to visual
mockups (`Image-to-Code` pipelines [14]), or inspected via live HTML
previews. Furthermore, Böckeler [11] explicitly cautions that treating
extensive Markdown specifications as the sole regenerable source
(*spec-as-source*) recreates the historical failure modes of
Model-Driven Development (MDD) [1, 2, 3]—specifically, severe "review
fatigue" when humans must audit verbose multi-file Markdown specs, and
compliance drift when coding agents ignore granular rules across long
documents [11].

## Not found

1. **A single cross-disciplinary survey uniting MBUID/UIDLs, UX design
   handoff, and 2025–2026 AI Spec-Driven Development:** Looked for across
   academic search indices (arXiv, IEEE, ACM), W3C notes, and
   practitioner hubs (`martinfowler.com`, `nngroup.com`). Each community
   synthesises only its own tradition without cross-citing the others.
2. **A formal standard or dominant practitioner schema for full-stack
   textual UI/UX specification in Markdown:** Looked for in W3C
   specifications, OMG standards, and 2025–2026 SDD toolkits (`spec-kit`,
   `Kiro`). None defines a standard Markdown schema covering screen
   anatomy, user flows, component states, and design tokens together.

## Options

Because this card maps the vocabulary and structural layers for the
twenty-one cards that follow and for the framework's target document,
the project faces three choices in how it frames its investigation and
design:

1. **Option A: Adopt the CAMELEON + IFML + DTCG layered separation Inside
   an SDD *Spec-Anchored* Markdown structure.**
   - *How it works:* Map the framework's existing documents (*what/why*,
     *business requirements*, *user stories*) to the *Task & Domain*
     layer, and scope the new textual UX/UI document explicitly to the
     three missing layers: (1) *Interaction Flows / Navigation* (IFML
     / wireflow concepts), (2) *Abstract & Concrete Screen/Component
     Structure and States* (AUI/CUI + practitioner state annotations),
     and (3) *Design Tokens / Constitutional UI Guardrails* (DTCG + SDD
     `constitution.md`). Maintain the document as *spec-anchored*
     (versioned in git alongside code) rather than pure
     *spec-as-source*.
   - *Trade-offs:* Aligns directly with where partial standards succeeded
     [3, 7, 8] and avoids MDD review fatigue [11], but requires
     designing a synthesis across traditions that do not natively talk to
     each other.

2. **Option B: Treat UI/UX purely as EARS requirements and acceptance
   criteria inside existing user stories (`spec-kit` / `Kiro` style).**
   - *How it works:* Follow current 2025–2026 SDD tools [11, 12] by
     embedding UI states and interactions as `WHEN/THE SYSTEM SHALL`
     clauses inside feature specifications without a dedicated UI/UX
     architecture document.
   - *Trade-offs:* Zero new document types to invent, but loses spatial
     hierarchy, cross-screen navigation structure, and component reuse
     across screens—the exact reasons MBUID [3] and UX wireflows [10]
     separated UI models from functional requirements.

3. **Option C: Build a formal XML/JSON UIDL (`Spec-as-Source` / MBUID
   style).**
   - *How it works:* Define a strict machine schema akin to UsiXML,
     UIML, or W3C AUI XML [1, 6] from which UI code is deterministically
     compiled.
   - *Trade-offs:* High machine determinism, but decades of MBUID history
     [2, 3] and 2025 SDD critiques [11] show that human authors and UX
     specialists resist authoring and reviewing verbose formal schemas,
     violating the project's human-in-the-loop Markdown goal.

## Relevance to this project

*Recommendation (agent inference from [1–13]):* Proceed with **Option A**
both to orient the remaining twenty-one research cards and to frame the
eventual UX/UI Markdown specification.

1. **How this rewrites or sharpens the remaining cards:**
   - Cards investigating *one screen*, *paths*, and *structure above the
     screens* should query both practitioner terms (*wireframe
     annotations*, *prototype specifications*, *wireflows*, *state
     matrix* [9, 10]) and MBUID/OMG terms (*Abstract User Interface*,
     *Concrete User Interface*, *IFML View Containers / View Components /
     Interaction Flows* [6, 7]).
   - Cards investigating *design systems and tokens* should anchor on the
     *W3C Design Tokens Format Module (`2025.10`)* and *design as code*
     [8].
   - Cards investigating *descriptions written for an agent that builds*,
     *the place in the process*, and *change after the first build*
     should query *Spec-Driven Development (SDD)*, *spec-anchored vs.
     spec-as-source*, *constitution.md / steering files*, and *EARS
     syntax* [11, 12, 13].
   - Cards investigating *where textual descriptions failed* should
     cross-examine MBUID/UIDL adoption barriers [2, 3] alongside
     Böckeler's 2025 critique of SDD review fatigue and MDD parallels
     [11].
2. **What it is chosen against:** Rejects Option B (which leaves global
   navigation, screen layout hierarchy, and design-system bindings
   unspecified) and Option C (which repeats the readability and
   adoption failures of XML-based UIDLs).

**Consult when:**
- Selecting search terms and primary standards for Cards 2–22 of the
  `2026-11-21-describing-ux-ui-in-text` bundle.
- Defining the terminology and section boundaries of the proposed UX/UI
  Markdown document so it complements (rather than duplicates) business
  requirements, solution design, and user stories.
- Deciding whether the UX/UI Markdown document operates as *spec-first*,
  *spec-anchored*, or *spec-as-source* across iterative post-build
  changes.

## Sources

1. **A Theoretical Survey of User Interface Description Languages:
   Preliminary Results** — Julio Guerrero-Garcia, Juan Manuel
   Gonzalez-Calleros, Jean Vanderdonckt, and Jaime Muñoz-Arteaga. 2009
   (dated by structured data / IEEE publication record).
   `https://doi.org/10.1109/LA-WEB.2009.40` | Secondary (academic survey
   and taxonomy) | Read via summarised fetch | Original publication.
2. **Adaptive Model-Driven User Interface Development Systems** — Pierre
   A. Akiki, Arosha K. Bandara, and Yijun Yu (*ACM Computing Surveys*,
   Vol. 47, No. 1, Article 64). 2014 (dated by structured data / ACM
   publication record). `https://doi.org/10.1145/2597999` | Secondary
   (comprehensive academic survey) | Read via summarised fetch |
   Original publication.
3. **Introduction to Model-Based User Interfaces** — Gerrit Meixner,
   Gaëlle Calvary, and Joëlle Coutaz, eds., W3C Model-Based User
   Interfaces Working Group Note. 2014-01-07 (dated by byline and W3C
   document header). `https://www.w3.org/TR/mbui-intro/` | Primary
   (standards body Working Group Note and overview) | Read via
   summarised fetch | Original publication.
4. **MBUI - Glossary** — Jaroslav Pullmann, ed., W3C Model-Based User
   Interfaces Working Group Note. 2014-01-07 (dated by byline and W3C
   document header). `https://www.w3.org/TR/mbui-glossary/` | Primary
   (standards body glossary) | Read via summarised fetch | Original
   publication.
5. **MBUI - Task Models** — Fabio Paternò, Carmen Santoro, Lucio Davide
   Spano, and Dave Raggett, eds., W3C Model-Based User Interfaces
   Working Group Note. 2014-04-08 (dated by byline and W3C document
   header). `https://www.w3.org/TR/task-models/` | Primary (standards
   body Working Group Note) | Read via summarised fetch | Original
   publication.
6. **Abstract User Interface Models** — Jean Vanderdonckt, Ricardo
   Tesoriero, Nesrine Mezhoudi, Vivian Motti, François Beuvens, and
   Jérémie Melchior, eds., W3C Model-Based User Interfaces Working Group
   Note. 2014-04-08 (dated by byline and W3C document header).
   `https://www.w3.org/TR/abstract-ui/` | Primary (standards body
   Working Group Note) | Read via summarised fetch | Original
   publication.
7. **Interaction Flow Modeling Language (IFML), Version 1.0** — Object
   Management Group (OMG). February 2015 (dated by structured data / OMG
   formal specification catalog). `https://www.omg.org/spec/IFML/1.0` |
   Primary (formal standard specification) | Read via summarised fetch |
   Original publication.
8. **Design Tokens Format Module (Version 2025.10)** — Louis Chenais,
   Kathleen McMahon, Drew Powers, Matthew Ström-Awn, and Donna Vitan,
   eds., W3C Design Tokens Community Group (DTCG). 2025-10-28 (stable
   release; iterative draft update 2026-09-08; dated by W3C Community
   Group Report header). `https://tr.designtokens.org/format/` | Primary
   (Community Group specification) | Read via summarised fetch |
   Original publication.
9. **UX Deliverables: Glossary** — Huei-Hsin Wang, Nielsen Norman Group
   (NN/g). 2024-08-09 (dated by byline).
   `https://www.nngroup.com/articles/ux-deliverables-glossary/` |
   Secondary (practitioner organisation glossary and synthesis) | Read
   via summarised fetch | Original publication.
10. **Wireflows: A UX Deliverable for Workflows and Apps** — Page
    Laubheimer, Nielsen Norman Group (NN/g). 2016-12-04 (dated by
    byline). `https://www.nngroup.com/articles/wireflows/` | Primary
    (practitioner organisation methodology definition) | Read via
    summarised fetch | Original publication.
11. **Understanding Spec-Driven-Development: Kiro, spec-kit, and Tessl**
    — Birgitta Böckeler (Thoughtworks / `martinfowler.com`, *Exploring
    Gen AI* series). 2025-10-15 (dated by byline).
    `https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html`
    | Secondary (practitioner comparative analysis and taxonomy) | Read
    via summarised fetch | Original publication.
12. **Spec-driven development with AI: Get started with a new open
    source toolkit** — Den Delimarsky, The GitHub Blog (`github.blog`).
    2025-09-02 (dated by byline).
    `https://github.blog/ai-and-ml/generative-ai/spec-driven-development-with-ai-get-started-with-a-new-open-source-toolkit/`
    | Primary (first-party documentation/announcement of GitHub Spec
    Kit) | Read via summarised fetch | Original publication.
13. **Spec-Driven Development: From Code to Contract in the Age of AI
    Coding Assistants** — Deepak Babu Piskala (arXiv:2602.00180v1
    [cs.SE]). 2026-01-30 (dated by arXiv submission header).
    `https://arxiv.org/abs/2602.00180` | Secondary (academic/practitioner
    survey and guide) | Read via summarised fetch | Original
    publication.
14. **Software Development Life Cycle Perspective: A Survey of
    Benchmarks for CodeLLMs and Agents** — Kaixin Wang, Tianlin Li,
    Xiaoyu Zhang, and Chong Wang (arXiv:2505.05283v1 [cs.SE]).
    2025-05-08 (dated by arXiv submission header).
    `https://arxiv.org/abs/2505.05283` | Secondary (academic survey of
    SDLC and agentic benchmarks) | Read via summarised fetch | Original
    publication.

## Opened and not used

- **W3C Incubator Group Reports Index (`https://www.w3.org/2005/Incubator/`)** — Superseded by the final 2014 W3C MBUI Working Group Notes [3, 4, 5, 6].
- **Constitutional Spec-Driven Development: Enforcing Security by Construction in AI-Assisted Code Generation (`https://arxiv.org/abs/2602.02584`)** — Off the question: focuses on security compliance constraints rather than UI/UX specification or general SDD taxonomy.
- **A Lean and Spec-Driven AI-Assisted Software Development Lifecycle for Applied AI Education (`https://arxiv.org/abs/2609.24348`)** — Off the question: focuses on educational pedagogy rather than UI/UX specification.

## Search record

**Queries run (in order):**
1. `user interface description language survey taxonomy`
2. `W3C model-based user interfaces incubator working group note`
3. `IFML OMG Interaction Flow Modeling Language specification`
4. `design handoff UI specification interaction design documentation`
5. `spec-driven development UI UX 2025 2026`
6. `"why is there no standard for UI specification"` *(disconfirming query)*
7. `"Introduction to Model-Based User Interfaces" "Glossary" "Task Models" "Abstract User Interface Models" W3C Working Group Note URL editors date` (domain: `w3.org`)
8. `"Interaction Flow Modeling Language" IFML 1.0 specification URL publication date formal` (domain: `omg.org`)
9. `"Spec-Driven Development" Birgitta Böckeler URL date UI UX specification` (domain: `martinfowler.com`)
10. `"spec-driven development" OR "user interface specification" survey taxonomy 2024 2025 2026 arxiv URL title authors date` (domain: `arxiv.org`)
11. `"User Interface Description Languages" survey taxonomy Guerrero-Garcia OR Vanderdonckt OR Meixner OR Akiki DOI URL title authors year`
12. `"design handoff" OR "UI specification" OR "interaction specification" OR "functional specification" OR "design documentation" URL author date` (domain: `nngroup.com`)
13. `"Model-Based User Interfaces Incubator Group Final Report" W3C 2010 URL editors date UIDL survey`
14. `"2602.00180" OR "A Survey on Image-to-Code for Software Engineering" exact arxiv ID URL title authors date abstract` (domain: `arxiv.org`)
15. `"UX Deliverables" OR "Wireflows" OR "Anatomy of a" specification handoff wireframe article URL author date` (domain: `nngroup.com`)
16. `"Spec-driven development" spec-kit URL author date` (domain: `github.blog`)
17. `"Design Tokens Format Module" W3C Community Group URL editors date "design as code"`
18. `"sdd-3-tools.html" "2602.00180" "spec-driven-development-with-ai" user interface UI UX wireframe mockup markdown`
19. `"Adaptive Model-Driven User Interface Development Systems" Akiki ACM Computing Surveys 2014 DOI URL authors date`
20. `"UX Deliverables" glossary survey functional specification wireframe prototype URL author date` (domain: `nngroup.com`)
21. `"XGR-mbui-20100504" OR "tr.designtokens.org/format" exact URL editors publication date`

**Pages opened (summarised fetches):** 15 targeted source-verification
fetches (queries 7–21) covering 14 used primary/secondary sources [1–14]
and 3 unused sources. (Direct shell `curl` was blocked by environment
policy; all openings were performed as targeted `search_web` summarised
fetches.)

**What the disconfirming query found:** Confirmed the card's expectation:
there is no single overarching standard for UI specification because UI
design bridges human perceptual/cognitive factors, brand differentiation,
and incompatible platform rendering models; instead, partial standards
exist at isolated layers (W3C Design Tokens [8], WCAG/WAI-ARIA for
accessibility, OMG IFML [7] for style-agnostic interaction flows, and
W3C MBUI Notes [3–6] for abstract models).

**Why the run ended:** Both parts of the card's stop rule were met at 15
targeted openings—every route specified in "Where to look" (academic
UIDL/MBUID surveys, W3C MBUI notes, IFML, practitioner glossaries on
design handoff/UX deliverables, and 2025–2026 SDD overviews) had
verified primary or canonical survey sources, and differently worded
queries ceased turning up new syntheses or terms.
