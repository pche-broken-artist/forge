---
date: 2026-11-21
project: forge
topic: The agent that proposes the description
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 17; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":50213,"output_tokens":20483,"thinking_tokens":10558,"cache_read_tokens":131599,"total_tokens":70696}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-17-proposing-agent
status: immutable
---

# How an AI agent gets from requirements, user stories and a solution design to a first proposal of an interface

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Functional requirements, user stories, and a technical solution design
specify what an application does and how its data and services work,
but leave four interface dimensions underspecified: physical context
and information density, spatial layout and navigation paradigm, the
non-happy-path state matrix (empty, loading, error, overflow), and
visual-identity or component-system tokens. Published 2025–2026
workflows bridge this gap through a gated Socratic loop capped at 3 to
5 questions per turn, ordered top-down from user/device context to
information architecture, key screen layout, state handling, and
accessibility, followed by a brief confirmation blueprint before
generating screen flows (high confidence across practitioner and vendor
sources, resting on summarised fetches in this environment). The
disconfirming queries confirmed that LLMs exhibit commitment bias and
statistical averaging when they do not ask or lack constraints,
defaulting to generic "AI slop" layouts. Unexpectedly, mainstream
spec-driven kits either fold interface structure into technical design
(`Kiro`, `github/spec-kit`) or place the textual interface
specification *before* technical architecture (`BMAD-METHOD`), and rely
on standing design-system files (`DESIGN.md`), anti-default self-audits
(Anthropic's `frontend-design` skill), and parameterized intermediate
specifications (`SpecifyUI`) rather than clarifying questions alone to
prevent arbitrary layout and interaction.

## Question

#### Card 17: The agent that proposes the description
- **Question:** How does an AI agent get from requirements, user stories and a solution design to a first proposal of an interface: what of an interface cannot be inferred from those documents and must be asked, which questions are asked and in which order before screens or flows are proposed, and how do the published workflows of 2025 and 2026 keep the agent from inventing arbitrary layout and interaction?
- **Why it matters:** the author expects the agent to read everything, ask what it lacks and make the proposal; this is the step an elicitation of the description would define.
- **What would answer it:** the published workflows, prompts and skills of AI design tools and spec-driven kits, read as primary artefacts in their repositories and documentation.
- **Where to look:** the steps from requirements to design in spec-driven kits and their prompt files; the question flows of AI interface generators and design assistants; public agent skills and rules for interface design. What human method prescribes for the same step is card 14's. Search words from card 1: "spec-driven development", "spec-first", "spec-anchored", "spec-as-source", "constitution", "steering files", "EARS", "DESIGN.md". Primary artefacts in public repositories (schemas, component and page files, agents' rules and prompt files, the schemas of servers for design tools, issue trackers) before commentary about them.
- **Disconfirming query:** "AI generated UI generic", "LLM design without clarifying questions"; expected: reports that an agent which does not ask produces a generic interface.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

**Baseline and terminology:** Because the word "design" stands for three
distinct things in the sources, this note distinguishes them explicitly
throughout: *interface design* means the structural and behavioral
description of screens, flows, and states (whether in text or a design
tool); *technical design* means the software architecture document
between requirements and tasks in spec-driven kits (`design.md` in
Kiro, `plan.md` in GitHub Spec Kit, `architecture.md` in BMAD); and
*design-system visual identity* means the tokens, typography, color
roles, and component rules held in files such as `DESIGN.md`. To beat
the baseline, this note must identify the exact gaps between upstream
documents and an interface proposal, give the concrete question
taxonomies, caps, and ordering used in 2025–2026 workflows, and name
the structural mechanisms that prevent arbitrary layout and interaction.
(All web sources in this run were read via the environment's grounded
`search_web` tool, which performs a summarised fetch; every finding
below rests on a summarised fetch and states so.)

## Key findings

**F1. Four interface dimensions cannot be inferred from functional
requirements, user stories, or a technical design and must be elicited
or supplied via standing files** [consensus — practitioner claims and
vendor documentation, resting on summarised fetches]. Upstream product
requirements and user stories state *who* acts and *what* outcome is
achieved, while a technical design states data models, APIs, and
service boundaries; neither determines:
1. *Environment, device posture, and information density* — whether the
   persona works in a high-density desktop triage environment or a
   distracted mobile on-the-go context, and whether the user is a
   power user needing keyboard shortcuts or a first-time user needing
   guided onboarding [1, 3].
2. *Spatial layout and navigation paradigm* — whether a view uses a
   master-detail split screen, a dashboard card grid, or a multi-step
   wizard, and how navigation collapses across responsive breakpoints
   (such as a desktop sidebar versus a mobile drawer or bottom sheet)
   [1, 6].
3. *The non-happy-path state matrix and feedback loops* — what the
   interface renders during empty/zero-data states, loading states
   (skeleton screens versus spinners), network or validation errors,
   long-string text overflow, and destructive-action guardrails (inline
   confirmation, modal dialog, or undo toast) [1, 3, 6].
4. *Design-system visual identity and component bindings* — which
   existing component library (such as shadcn/ui, Material UI, or
   custom primitives), color tokens, typographic scale, and WCAG
   accessibility tier (AA or AAA) govern the interface [1, 6, 9].

**F2. GitHub Spec Kit isolates ambiguity resolution into a dedicated
`/speckit.clarify` gate that scans nine categories and caps questioning
at five sequential questions** [single source — primary repository and
documentation, resting on summarised fetches]. In `github/spec-kit`
(2025), the workflow moves from `/speckit.constitution`
(`.specify/memory/constitution.md`) to `/speckit.specify` (which
populates `spec.md` from `spec-template.md` with user stories and
acceptance criteria), then to `/speckit.clarify`, and only afterward to
`/speckit.plan` (which creates `plan.md`, the technical design) [4, 5].
During `/speckit.clarify`, the agent evaluates `spec.md` against a
nine-part ambiguity taxonomy: *Scope*, *Data Model*, *UX Flow*, *NFRs*,
*Integrations*, *Edge Cases*, *Tradeoffs*, *Terminology*, and
*Completion Signals* [5]. To prevent user fatigue, `/speckit.clarify`
enforces a strict cap of at most 5 clarification questions per pass,
presents them sequentially (supporting early exit if the user replies
"done", "good", or "no more"), and writes the resolved decisions
directly back into `spec.md` under a `## Clarifications` heading before
technical planning begins [4, 5].

**F3. Dedicated UX specification workflows and AI interface generators
ask 3 to 4 questions per turn in a six-stage top-down order, then
confirm a short "UX Blueprint" before proposing screens** [emerging —
practitioner claims and vendor documentation, resting on summarised
fetches]. In workflows dedicated to interface design—specifically the
`ux-expert` persona running `create-ux-design` to produce
`front-end-spec.md` in `BMAD-METHOD` [6, 7] and pre-generation question
flows in AI UI generators such as Flowstep and UX Pilot [1, 3]—the
agent does not ask about individual widgets first. Instead, it
interrogates and builds the specification in six ordered stages:
1. *UX overview, context of use, and design direction* (device target,
   user expertise, and tone) [3, 7].
2. *Target personas and the single primary action per view* [3, 7].
3. *Information architecture and screen-to-screen navigation flow*
   (sitemap/node tree and responsive navigation pattern) [3, 7].
4. *Key/anchor screen and component layout patterns* (master-detail,
   grid, form wizard) [1, 7].
5. *Interactive behaviors and the state matrix* (default, loading,
   empty, error, success, and micro-interactions) [1, 6, 7].
6. *Accessibility and responsive breakpoint standards* (WCAG contrast,
   ARIA labels, touch targets) [6, 7].
Across conversational SDD prompts and UI generators, questioning is
capped at 3 to 4 high-impact questions at a time, paired with
suggested default option pills for one-tap selection, while any
unasked details are logged explicitly as `ASSUMPTION: [detail]` [1, 3].
Before generating screen descriptions or wireframes, the agent outputs
a 2-sentence *UX Blueprint* summarizing the chosen device target,
layout pattern, and numbered core screens for human confirmation, then
proposes an information-architecture map and a single anchor screen
before expanding derivative flow screens [3].

**F4. Published 2025–2026 workflows prevent arbitrary layout and
interaction through four structural constraints: standing `DESIGN.md`
and steering files, EARS behavioral rules, two-pass anti-default
planning, and parameterized intermediate specifications** [consensus —
controlled study, primary repositories, and vendor documentation,
resting on summarised fetches]. Rather than relying on clarifying
questions alone to stop hallucinated layouts, 2025–2026 tools apply
four constraints:
1. *Standing steering files and `DESIGN.md` contracts*: AWS Kiro stores
   persistent project rules in `.kiro/steering/` (`product.md`,
   `tech.md`, `structure.md`) [8]. For design-system visual identity,
   Google Stitch and the `voltagent/awesome-design-md` repository
   (2025–2026) define a 9-section `DESIGN.md` file with a two-layer
   structure: a machine-readable YAML header (`tokens.colors`,
   `tokens.typography`, `tokens.spacing.scale_base`, `tokens.radius`)
   followed by Markdown rules covering *Visual Theme & Atmosphere*,
   *Color Palette & Roles*, *Typography Rules*, *Component Stylings*
   (default/hover/active), *Layout Principles*, *Depth & Elevation*,
   *Do's and Don'ts*, *Responsive Behavior*, and an *Agent Prompt
   Guide* [2, 9]. The `/speckit.plan` or implementation agent maps
   components strictly to `DESIGN.md` tokens and surface-hierarchy
   rules rather than inventing CSS values [2, 9].
2. *EARS notation for deterministic UI interaction*: In Kiro's
   `requirements.md`, user-facing interaction and state transitions are
   locked using Easy Approach to Requirements Syntax (EARS)—specifically
   event-driven (`WHEN [user action] THE SYSTEM SHALL [UI response]`)
   and state-driven (`WHILE [request pending] THE SYSTEM SHALL [disable
   control and show spinner]`) clauses—which the technical `design.md`
   and `tasks.md` must trace to [8].
3. *Two-pass planning with an explicit anti-default blacklist*:
   Anthropic's official `frontend-design` skill (`SKILL.md`, reproduced
   verbatim in [10]) instructs the agent to work in two passes. In
   Pass 1, the agent drafts a concise design plan specifying: (1)
   *Color* (4–6 named hex values), (2) *Type* (deliberate typeface
   roles and scale), (3) *Layout* ("using one-sentence prose
   descriptions and ASCII wireframes to ideate and compare", plus
   alignment rules), and (4) *Principles* [10]. Crucially, before
   Pass 2 builds the interface, the skill forces the agent to audit its
   plan against an explicit list of "common AI template defaults":
   "Cream and terracotta palettes with rounded cards", "The standard
   SaaS card kit (three feature cards in a row with subtle borders)",
   "Template chrome (subtle gradient background, centered badge, pill
   button)", "Generic tech sans-serif fonts used everywhere", and
   "Predictable spacing and symmetrical centering on every section"
   ("If any part of your plan matches what you would produce for any
   similar page, revise it and explain the change") [10].
4. *Hierarchical parameterized intermediate specifications (`SPEC`)*:
   In a controlled study with 16 professional UI designers (Sep 2025),
   Chen et al. (`SpecifyUI`, arXiv:2509.07334) demonstrated that
   free-text conversational prompts fail to preserve layout structure
   across iterations because small prompt edits trigger global layout
   shifts [11]. `SpecifyUI` introduces `SPEC`, a hierarchical,
   parameterized intermediate representation encoding *Regions*,
   *Styles*, and *Layouts* at global, regional, and component levels;
   compared against conversational baselines including Google Stitch,
   `SPEC` significantly improved intent alignment and controllability
   while reducing user text input by ~73% overall and up to ~80% for
   component-level edits [11].

**F5. Disconfirming evidence confirms that agents which do not ask
clarifying questions or lack specification constraints suffer from
commitment bias and produce homogenized interfaces** [consensus —
academic preprints and practitioner reports, resting on summarised
fetches]. The query `"LLM design without clarifying questions"`
confirmed that standard instruction-tuned LLMs exhibit a *commitment
bias*: they guess missing parameters and hallucinate unstated workflows
rather than pausing to ask follow-up questions [15]. When clarifying
questions are omitted by design (for latency or autonomous execution),
prompts must force the agent either to declare explicit assumptions at
the top of its output or to generate branched multi-hypothesis
proposals [1, 15]. Similarly, the query `"AI generated UI generic"`
confirmed widespread practitioner consensus (2025–2026) that one-shot
UI generation without clarification or a design-system contract
computes the statistical mean of training data, yielding uniform
Tailwind blue/purple gradients, `Inter`/`Roboto` typography,
symmetrical `rounded-xl` card grids, and missing edge-case states [14].

## Unexpected

**The card assumes the interface-proposing agent sits *after* technical
solution design (`design.md` / `plan.md`); primary spec-driven kits
either omit a separate interface document or place it *before*
technical architecture.** In AWS Kiro (`kiro.dev`) and GitHub Spec Kit
(`github/spec-kit`), the document between requirements and tasks
(`design.md` or `plan.md`) is the *technical design*, and there is no
downstream textual UX/UI specification stage after it—interface
components and EARS interaction rules are embedded directly inside
`requirements.md`/`spec.md` and technical `design.md`/`plan.md` [4, 8].
Conversely, in `BMAD-METHOD`, which *does* define a dedicated textual
interface specification (`front-end-spec.md` / `ux-design.md` produced
by the `ux-expert` agent), that document is generated from the product
requirements (`prd.md`) *before or alongside* the technical solution
architecture (`architecture.md`), so that component hierarchy, state
management, and API contracts in the technical design are informed by
the agreed screens and user flows rather than precedes them [6, 7].

**Anthropic's `frontend-design` skill uses ASCII wireframes plus
one-sentence prose in its planning pass rather than pure prose alone.**
While the card frames the output as a description of the interface in
text, Anthropic's `frontend-design/SKILL.md` explicitly pairs
"one-sentence prose descriptions and ASCII wireframes to ideate and
compare" during Pass 1 before any code is written, treating spatial
alignment and container rhythm as properties that benefit from rough
2D character sketches alongside text [10].

## Not found

- **No multi-turn question script in Anthropic's `frontend-design`
  skill:** Searched `anthropics/skills` (`frontend-design/SKILL.md`)
  expecting a structured multi-question interview protocol. Instead,
  the skill contains only a single conditional instruction for missing
  context ("If the brief does not identify what the product or subject
  matter is, identify it yourself before designing, and confirm with
  the client. You can come up with one concrete subject, the design's
  audience, and the design's primary job, as a proposal") and
  immediately relies on its two-pass design plan and anti-default audit
  [10].
- **No direct raw file fetches outside grounded summaries:** Direct
  HTTP fetches via `curl.exe` were blocked by the environment's
  terminal deny rules, so exact line numbers inside repository files
  could not be inspected directly; only content and verbatim excerpts
  returned by `search_web` summarised fetches could be verified.

## Options

1. **Two-stage gated elicitation with standing `DESIGN.md` + Socratic
   feature Q&A (Combine `DESIGN.md`, `spec-kit`/`BMAD` ordering, and
   Anthropic Pass 1):** Separate project-wide visual identity into a
   standing `DESIGN.md` file (tokens, typography, component states,
   do's/don'ts) so the agent never has to ask visual-token questions on
   every feature. When proposing a feature's interface from
   requirements and user stories, have the agent run a Socratic loop
   (capped at 3–5 questions per turn, ordered from device/density
   context $\rightarrow$ navigation/IA $\rightarrow$ layout paradigm
   $\rightarrow$ non-happy-path state matrix $\rightarrow$ a11y), mark
   unasked defaults as `ASSUMPTION:`, confirm a short *UX Blueprint*
   (screen list + anchor layout), and run an anti-default self-audit
   before writing the full screen and element descriptions.
   *Trade-offs:* Keeps per-feature questioning short (1–2 turns) and
   prevents generic styling, at the cost of requiring an initial
   project-level `DESIGN.md` setup step.
2. **Propose-first with explicit assumptions and multi-option ASCII
   sketches (Anthropic `frontend-design` / best-effort pattern):** Have
   the agent read requirements, user stories, and technical design and
   immediately output a Pass 1 interface blueprint (declaring explicit
   `ASSUMPTION:` tags for any unstated device/state details and
   comparing 2 layout concepts in one-sentence prose + ASCII
   wireframes) for the human to tune, asking clarifying questions only
   when the core subject or primary job is missing.
   *Trade-offs:* Minimizes conversational friction before the first
   proposal is seen, but risks wasted drafting if a foundational
   assumption (such as mobile vs. desktop posture or master-detail vs.
   wizard flow) is wrong.
3. **Place the interface description *before* or *co-equal with* the
   technical solution design (`BMAD-METHOD` sequence):** Elicit the
   interface specification immediately after business requirements and
   user stories, before finalizing the technical solution design, or
   allow the interface proposal to feed back into technical design.
   *Trade-offs:* Avoids the trap where a technical design locks in API
   shapes or pagination models that conflict with the chosen UI
   interaction pattern (e.g., infinite scroll vs. server-paged table,
   optimistic inline edits vs. modal forms), but alters the linear
   document chain assumed in the card's frame.

## Relevance to this project

*(Agent's inference marked as its own.)* For `forge`, Option 1 combined
with Option 3's feedback awareness is recommended over single-shot
generation or unconstrained open-ended interviewing. Specifically, the
elicitation skill for `forge`'s interface description document should:
1. Read the upstream requirements, user stories, solution design, and a
   standing project-level visual-identity file (analogous to
   `DESIGN.md`) so visual tokens are not re-asked per feature.
2. Scan for missing interface decisions across the six-stage hierarchy
   (device/density context, primary action per screen, IA/navigation
   flow, layout pattern, empty/loading/error/confirmation state matrix,
   and a11y/responsive rules).
3. Ask at most 3 to 5 clarifying questions per turn in that top-down
   order, offering recommended default choices and recording unasked
   items as explicit `ASSUMPTION:` entries.
4. Pause at a brief *UX Blueprint* confirmation (list of screens,
   navigation structure, and anchor layout concept) and run an explicit
   anti-default checklist before generating the element- and page-level
   Markdown definitions.

**Consult when:** Designing the prompt, workflow, question taxonomy, or
stop conditions of the agent that elicits and proposes the textual
UX/UI description from upstream documents, or deciding whether visual
system tokens (`DESIGN.md`) should live separately from per-feature
interface descriptions.

## Sources

[1] "Spec-Driven UI/UX Requirement & Clarification Prompt Framework"
(synthesizing SDD clarification workflows from Medium, Microsoft, and
Martin Fowler SDD guides), Multiple authors, 2025–2026 (dated via
search index metadata; individual grounding targets undated in fetch),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFVnk2oJmMHJMJ1XuXcbvaALvtx3QfQB4BssejDibCwPa_7q6_0trro5bJ9OlVpkWOxM_GZmL-gjzRzm9ZMmagmusDzKyqcJ3JRK4VSFSWXI_T0vgt0OyPOY9bWAv4XD2F58ionrVdQJgbrTnU1Zf8-5uzI8IO_foC7-_I4kRVhaxuRgq4pwU1d0EILjjeRZ-443lwG44XeBhV7CnVkvMIHPXAIL5ZPxaVdMAg4Rqg4NrvtJo9VKi4=`;
kind: tertiary (grounded synthesis of practitioner guides); how read:
summarised fetch; original synthesis of practitioner sources.

[2] "DESIGN.md, Steering Files, and Spec-Kit UI Design Agent Workflow"
(grounded synthesis of GitConnected, Augment Code, and Shiplight AI on
SDD UI pipelines), Multiple authors, 2025–2026 (dated via search index
metadata; undated in fetch),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGEfSrPdIBRcalvtXBcOJLsDkv8KsI5b4t4xkSPKK1gyiRoJauEi37qrPEbXxzmAWwdIXP_8FSsVTcpgtWszIM7nGD4zex_w7BqnPH9jGNGveiBDXuxsgq41q9ausyk7Fbw1xjWbn-iDUGz_jpTK9IPWGD28EkI9-vdXRWqDYO1AiJ0HdrODm6NYTu10Eusy8LnMUypEiCyPY7UmA==`;
kind: secondary / tertiary; how read: summarised fetch; original
practitioner analyses.

[3] "AI UI Generator Clarifying Questions Workflow Before Generating
Screens and Flows" (Flowstep AI and UX Pilot documentation/guides),
Flowstep AI / UX Pilot, 2025 (dated via search index metadata; undated
in fetch),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFR29VyBMgyArmuhOqamvsqXwAAbyKMBVIkqxDuAzSVswiSujuuu-tB2ETkqPHLEQ-B0z3IfwHZdLP1Bg9bd7C5n-b-uH7FQ-ipuxUcHqn6Tmo7LgjA6epZX30D2V-sKXR7JSk=`;
kind: primary (vendor documentation/workflow guides); how read:
summarised fetch; original.

[4] `github/spec-kit` repository (`.specify/templates/` and
`/speckit.specify`, `/speckit.clarify`, `/speckit.plan` command
workflows), GitHub, 2025 (structured data / repository metadata),
`https://github.com/github/spec-kit`; kind: primary; how read:
summarised fetch; original.

[5] "`github/spec-kit` `clarify.md` and `specify.md` Question Cap,
Execution Order, and 9-Category Ambiguity Taxonomy" (GitHub
`github/spec-kit` command templates and RunMaestro analysis), GitHub /
RunMaestro, 2025–2026 (undated in fetch),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEebwh-W-cl9EAJmMz-uZ1OBbwvW7TuYbl80K9HgdBc9qiO3UGdnYkCfHiHjGqfFFOa9GTxeetz6XqqGPS0AfII-MpC5aIy6xkksYrD8yY_x7BrctQC8Vlq4Pgj8VympaNatlmBekYoeIASHu5giqoLO4of5PcGvA==`;
kind: primary / secondary; how read: summarised fetch; original and
secondary commentary on `github/spec-kit`.

[6] "BMAD-METHOD Advanced Elicitation (`*elicit`) and UX-Expert /
Front-End Specification Workflow", BMad Code Org / Medium practitioner
guides, 2025 (undated in fetch),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGBhtwL4-5QGB9JFfo-Gf-VAW0OvAUb-jOHJuoZJbNtpyrGVJr3UH0BOJjL3kYjKhO2lh5pflj8EC63mLbV3afmsULLzmV2GG0NVtyJ-mNnhoIDkuZkI8obdhPWrX79U0oDtRusNBlahURLcukT7wKVIoNafEE_L7FvQeHqn4v7zxAtk_fYXeXlX-Og_JpghajTXN8IZe94ZiPFVDNP3OCkYXKuVT1maDQ_0fVa7E5TqXUexkSAY7Kf9uA9jfmcyC_43iHU9ycID4kb2w==`;
kind: secondary; how read: summarised fetch; practitioner write-up of
`bmad-code-org/BMAD-METHOD`.

[7] `bmad-code-org/BMAD-METHOD` (`ux-expert` agent, `create-ux-design`
workflow, and `front-end-spec` template section sequence), BMad Code
Org, 2025 (undated in fetch),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFzJuti4hpQvGJAwR6D9wTC3MdanI4Hg3lazRREjVV5rQRsevyAyS7T9sjaMFGNRzrqOaIhR8oEcSqay7XI5h9g0nLPLC7GegIc460YJtqDjm_Etfnqkf3JFGAMcG1RP5ISqawb`;
kind: primary; how read: summarised fetch; original repository.

[8] Kiro Documentation: "Specs" (`requirements.md`, `design.md`,
`tasks.md`, EARS notation) and "Steering" (`.kiro/steering/`), AWS /
Kiro, 2025 (undated in fetch), `https://kiro.dev/docs/specs/`; kind:
primary (vendor documentation); how read: summarised fetch; original.

[9] `voltagent/awesome-design-md` (`DESIGN.md` 9-section specification
introduced by Google Stitch and YAML token header format), VoltAgent /
Google Stitch community, 2025–2026 (undated in fetch),
`https://github.com/voltagent/awesome-design-md`; kind: primary; how
read: summarised fetch; original repository.

[10] `frontend-design/SKILL.md` (verbatim reproduction of Anthropic's
`anthropics/skills` `frontend-design` skill file via TrueFoundry),
Anthropic (hosted via TrueFoundry), 2025–2026 (undated in fetch),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGJam31nQoQ1jLJhkNbhqewjukXADQ-5J0HFV-5ssalMT7D_PJGVlf60q8LAYN97Whc8JCv1yp3N7O7hyXLz70maMwA1U0xucD2eKcraDTEU5CBTLUHt2lBuVsiN4ZvD2otyJkOAqaUcJfC_dfR5jq3RGukO911TM0a2l4J6hvOCY0FOysA48eEdlTwA9aF`;
kind: primary text reproduced in secondary host; how read: summarised
fetch (returned full verbatim Markdown of `SKILL.md`); copy of
`anthropics/skills/blob/main/skills/frontend-design/SKILL.md` (used
because direct GitHub blob fetch was blocked by sandbox rules).

[11] "SpecifyUI: Supporting Iterative UI Design Intent Expression
through Structured Specifications and Generative AI", Yunnong Chen,
Chengwei Shi, Liuqing Chen, 2025-09 (byline / arXiv submission metadata,
arXiv:2509.07334), `https://arxiv.org/abs/2509.07334`; kind: primary
(controlled study); how read: summarised fetch; original.

[12] "Generative Interfaces for Language Models", Jiaqi Chen, Yanzhe
Zhang, Yutong Zhang, Yijia Shao, Diyi Yang (Stanford University),
2025-08-26 (v1 byline; v3 revised 2026-05-01, arXiv:2508.19227),
`https://arxiv.org/abs/2508.19227`; kind: primary (controlled study);
how read: summarised fetch; original.

[13] "A Formative Study to Explore the Design of Generative UI Tools to
Support UX Practitioners and Beyond", Xiang 'Anthony' Chen, Tiffany
Knearem, Yang Li (Google DeepMind), 2025-01 (byline / arXiv metadata,
arXiv:2501.13145), `https://arxiv.org/abs/2501.13145`; kind: primary
(formative practitioner study); how read: summarised fetch; original.

[14] "Why AI-Generated UI Looks Generic and How Structured Design
Tokens Fix It" (disconfirming query synthesis from `alexlavaee.me` and
`aivancity.ai`), Alex Lavaee / Aivancity, 2025–2026 (undated in fetch),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEexo-gAP17ZxV3PeJV1NrADE-6io78wYylzvo-vaz70m-U5LOzQNt2sB3RaNrjhqIdTRigdjXILeiGx3lzSw2-G6QhPDjPlf0BRelYpQNa9OLxuZugEfl9T-8efhcs1cPhD1hY3nYOc3llI2JUKjxMpiCPjpw-Zg==`;
kind: secondary (practitioner analysis); how read: summarised fetch;
original.

[15] "LLM Design Without Clarifying Questions: Commitment Bias and
Ambiguity Mitigation Patterns" (disconfirming query synthesis of arXiv
studies on LLM ambiguity and tool-calling), Multiple authors, 2025
(undated in fetch),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFAnTBHvZRz87Oqhej1SUaGUCpTakn01VgaSseKj65tWSP8vLfyhMbipJFsgwrsW7N0fMgyFeNpOQbdNJMV0JBNnuFEb2WmEeomfxzgD-_Bd5V4mDDxmDcj0XqRkaE=`;
kind: secondary / tertiary (grounded synthesis of arXiv papers); how
read: summarised fetch; original.

## Opened and not used

- `https://arxiv.org/abs/2505.15049` ("Towards a Working Definition of
  Designing Generative User Interfaces", Kyungho Lee, May 2025) —
  superseded by [11] and [12] for concrete specification parameters.
- `https://kiro.dev/docs/steering/` (Kiro Steering documentation) —
  superseded by [8], which already covered `.kiro/steering/` files.

## Search record

Queries run in order (via `search_web`; direct terminal `curl.exe` was
attempted once on `https://github.com/github/spec-kit` and blocked by
the sandbox deny rule, so each targeted `search_web` call served as a
summarised-fetch opening):
1. `spec-driven development requirements to design prompt UI UX clarifying questions` (broad search & summarised fetch [1])
2. `"DESIGN.md" OR "steering files" OR "spec-kit" UI design agent prompt workflow` (broad search & summarised fetch [2])
3. `AI UI generator clarifying questions workflow before generating screens flows` (broad search & summarised fetch [3])
4. `"AI generated UI generic"` (disconfirming query 1 & summarised fetch [14])
5. `"LLM design without clarifying questions"` (disconfirming query 2 & summarised fetch [15])
6. `"github/spec-kit" "clarify.md" OR "specify.md" OR "plan.md" templates commands` (route 1 opening: `github/spec-kit` [4])
7. `"BMAD-METHOD" "ux-expert" OR "front-end-spec" OR "ux-design" workflow elicit questions` (route 1 opening: `BMAD-METHOD` `*elicit` [6])
8. `"anthropics/skills" "frontend-design" SKILL.md` (route 3 opening: Anthropic `frontend-design` overview)
9. `"kiro.dev" "requirements.md" "design.md" UI interface EARS steering files` (route 1 opening: Kiro workflow)
10. `"github/spec-kit" "clarify.md" "specify.md" exact URL verbatim text taxonomy max questions order` (domain `github.com`, opening [5])
11. `"BMAD-METHOD" "front-end-spec-tmpl" OR "ux-expert" OR "create-ux-design" exact URL sections order questions` (domain `github.com`, opening [7])
12. `"anthropics/skills" "frontend-design/SKILL.md" exact URL verbatim text instructions` (domain `github.com`, opening [10] returning full verbatim `SKILL.md`)
13. `"kiro.dev/docs/specs" "requirements.md" "design.md" "steering" exact URL verbatim text EARS` (domain `kiro.dev`, opening [8])
14. `"DESIGN.md" "Stitch" OR "awesome-design-md" exact URL format sections tokens layout rules` (domain `github.com`, opening [9])
15. `arxiv UI design generation LLM clarifying questions OR spec-driven requirements interface 2025 2026 exact arxiv ID title authors date` (domain `arxiv.org`, opening [12, 13])
16. `"2509.07334" "SpecifyUI" AND "2501.13145" abstract findings dimensions structured specifications UI design intent` (domain `arxiv.org`, opening [11])
17. `"github/spec-kit" "templates/commands/clarify.md" "Functional Scope" OR "Interaction & UX" verbatim taxonomy table AND "BMAD-METHOD" "front-end-spec-tmpl.yaml"` (domain `github.com`, cross-check of exact file paths)

**What the disconfirming queries found:** Both disconfirming queries
returned strong confirming evidence for the card's expectation:
`"AI generated UI generic"` returned practitioner analyses documenting
that one-shot UI prompts without clarifying questions or design-system
tokens regress to the statistical mean of web training data (blue/purple
gradients, `Inter`/`Roboto`, uniform `rounded-xl` card grids, missing
edge states) [14]; `"LLM design without clarifying questions"` returned
research on LLM commitment bias showing that unprompted models guess
missing parameters rather than ask, requiring explicit assumption
declarations or multi-hypothesis branching when interactive Q&A is
absent [15].

**Why the run ended:** Both parts of the card's stop rule and the
opening budget were met simultaneously—every route (spec-driven kits,
AI UI generator question flows, public design skills/`DESIGN.md`, and
controlled academic studies) had primary sources opened via summarised
fetches (15 distinct sources across 12 targeted openings after the 5
initial searches), and the final cross-check query returned no new
mechanisms or categories.
