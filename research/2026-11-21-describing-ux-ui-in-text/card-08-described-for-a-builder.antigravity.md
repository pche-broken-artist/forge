---
date: 2026-11-21
project: forge
topic: Descriptions written for an agent that builds
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 8; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":48448,"output_tokens":20208,"thinking_tokens":5888,"cache_read_tokens":94703,"total_tokens":68656}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-08-described-for-a-builder
status: immutable
---

# How AI coding and design tools of 2025 and 2026 want a user interface described so that an agent builds it

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Across the tools of 2025 and 2026, makers do not ask for a single monolithic
text document that describes every pixel of a screen; instead, they split the
interface description across four distinct artefacts corresponding to the three
senses of "design": (1) behavioural requirements and technical architecture in
spec-driven development kits (`requirements.md` using EARS syntax and
`design.md` or `plan.md` for component hierarchy and data flow), (2) a
persistent visual-identity and aesthetic contract in Markdown (`DESIGN.md`,
`CLAUDE.md`, `.kiro/steering/`, or on-demand skills like Anthropic's
`frontend-design`), (3) machine-readable component-inventory manifests served
over the Model Context Protocol (`registry-item.json` in shadcn/ui, Component
Manifests in Storybook MCP), and (4) spatial layout context extracted from a
design tool canvas or visual target (`get_design_context` and `get_screenshot`
in Figma MCP). Because direct HTTP fetches were blocked by the environment's
deny rules, all findings rest on summarised fetches (tertiary groundings) of
primary vendor documentation and practitioner reports. The disconfirming query
confirmed a wide practitioner consensus that pure prose specifications fail for
two-dimensional spatial layout, responsive wrapping, and visual hierarchy
("screenshots beat specifications"), leading teams to pair a lightweight text
"design contract" (tokens, existing components, and EARS behavioural rules)
with visual targets or render-and-critique loops. The unexpected finding is
that in spec-driven development kits (`spec-kit` and Kiro), the file named
`design.md` (or `plan.md`) is a software architecture document (data models,
API contracts, sequence diagrams) rather than a user-interface specification,
whereas Google Stitch's `DESIGN.md` defines the visual identity of a design
system rather than individual screen layouts.

## Question

- **Question:** How do the AI coding and design tools of 2025 and 2026 want a
  user interface described so that an agent builds it (the design file of
  spec-driven kits, a design file for agents, sections of agent instruction
  files, rules files, skills and prompts for interface work, servers that give
  an agent a design system, component documentation as an agent's context):
  which content and shape do their makers prescribe, and what do practitioners
  report works or fails?
- **Why it matters:** the build stage is an agent at least in part, and the
  description must be what an agent builds from.
- **What would answer it:** the tools' own documentation, and dated reports by
  practitioners.
- **Where to look:** the documentation of spec-driven development kits, of
  interface generators and of design tools' AI features; the makers' guidance
  on front-end work with coding agents; component registries and their agent
  integrations. Search words from card 1: "spec-driven development",
  "spec-first", "spec-anchored", "spec-as-source", "constitution", "steering
  files", "EARS", "DESIGN.md". Primary artefacts in public repositories
  (schemas, component and page files, agents' rules and prompt files, the
  schemas of servers for design tools, issue trackers) before commentary about
  them.
- **Disconfirming query:** "spec-driven development fails for UI", "screenshot
  beats specification"; expected: reports that a picture or a prototype steers
  an agent better than text.
- **Stop rule:** nothing new from a differently worded query and every route
  has a primary source; ten to fifteen pages opened.

**Baseline to beat:** The naive assumption that an AI coding agent builds an
interface from a single prose Markdown document describing screens, layouts,
and visual styling in natural language, or conversely that spec-driven
development kits already define a dedicated user-interface specification format
in their `design.md` files.

## Key findings

- **F1. Spec-driven development kits separate persistent project conventions
  from feature-level behavioural requirements, technical design, and task
  lists, using `design.md` or `plan.md` for software architecture rather than
  visual interface design** `[consensus — vendor documentation and practitioner
  analysis, resting on summarised fetches]`. In Kiro (2025–2026), feature
  specifications live in `.kiro/specs/{feature-name}/` across three Markdown
  files: `requirements.md` (user stories and acceptance criteria written in
  Easy Approach to Requirements Syntax, EARS: `WHEN [condition/event] THE
  SYSTEM SHALL [observable behavior]`), `design.md` ("Documents technical
  architecture, sequence diagrams, and implementation considerations" including
  component hierarchies, API contracts, and data models), and `tasks.md`
  (sequenced implementation checklist traced to requirements), alongside
  persistent repository context in `.kiro/steering/` (`product.md`, `tech.md`)
  [1, 2]. GitHub's `spec-kit` (2025–2026) prescribes an analogous four-artefact
  chain: `.specify/memory/constitution.md` for immutable project principles,
  `.specify/templates/spec-template.md` for observable user scenarios,
  `.specify/templates/plan-template.md` for technical architecture, and
  `.specify/templates/tasks-template.md` for execution [3, 4]. In October 2025,
  Birgitta Böckeler (Thoughtworks) classified these kits into three levels of
  permanence—"spec-first" (used to steer initial generation), "spec-anchored"
  (kept alive in git for maintenance), and "spec-as-source" (where humans edit
  only the spec, as in Tessl)—and warned that heavy text specifications carry
  overhead similar to historic model-driven development [5].

- **F2. Google Stitch's `DESIGN.md` standardises a plain-text "design file for
  agents" that captures the visual identity of a design system (sense 3 of
  "design") through YAML token frontmatter and Markdown prose guardrails**
  `[emerging — vendor documentation and open-source specification, resting on
  summarised fetches]`. Published by Google Labs for Stitch
  (`stitch.withgoogle.com/docs/design-md/specification` and
  `github.com/google-labs-code/design.md`, 2025–2026), `DESIGN.md` is positioned
  alongside `README.md` (for humans) and `AGENTS.md` or `SKILL.md` (for agent
  behaviour) to govern visual appearance across Stitch, Claude Code, and Cursor
  [6, 7]. It combines two layers: (1) machine-readable YAML frontmatter or
  structured sections defining exact design tokens (hex colours for `primary`,
  `surface`, `onSurface`, `error`; `typography` font families and base sizes;
  `spacing` units and numeric scales) and (2) Markdown prose stating the
  overall aesthetic direction ("Overview"), per-component styling rules
  ("Component Specifications", such as border radius and elevation rules for
  buttons and cards), and explicit negative constraints ("Do's and Don'ts",
  such as forbidding unapproved hex codes or nested cards) [6, 7, 8]. Companion
  CLI tooling (`@google/design.md`) lints generated code against these rules
  and exports Tailwind themes [7, 8].

- **F3. Agent instruction files (`CLAUDE.md`) and modular skills (Anthropic's
  `frontend-design` skill) steer interface generation by combining high-level
  aesthetic direction and explicit anti-patterns with strict token and
  component-reuse rules, rather than low-level pixel coordinates** `[consensus
  — vendor documentation and practitioner reports, resting on summarised
  fetches]`. Anthropic's `frontend-design` skill (`SKILL.md`, ~400 tokens,
  loaded on demand when UI tasks are detected, 2025) diagnoses "distributional
  convergence" ("In frontend design, this creates what users call the 'AI slop'
  aesthetic") and instructs the agent across four axes: typography (banning
  overused defaults like Inter, Roboto, Arial, and Open Sans in favour of
  high-contrast pairings and 3x+ heading scale jumps), colour and theme
  (requiring CSS variables and a dominant surface tone with sharp accents
  rather than purple-on-white gradients), motion (restricting non-triggered
  animation to a single orchestrated page-load or staggered reveal via CSS),
  and atmospheric backgrounds [9, 10]. In persistent `CLAUDE.md` files, makers
  and practitioners prescribe short declarative guardrails: reuse existing
  primitives in `src/components/ui` before creating new ones, pull all colours,
  spacing, and radii from theme tokens, never restyle base components inline,
  and run build/lint verification after edits [9, 11].

- **F4. Design-tool MCP servers (Figma MCP) feed coding agents a multi-modal
  bundle—a React/Tailwind structural tree, bound Code Connect component
  snippets, resolved design token definitions, a sparse XML node outline, and
  a rendered screenshot—rather than prose descriptions of screens** `[consensus
  — vendor documentation, resting on summarised fetches]`. The official Figma
  MCP Server (`developers.figma.com/docs/figma-mcp-server/`, 2025–2026) exposes
  four primary tools for coding agents: (1) `get_design_context`, which
  translates a selected canvas frame (sense 1 of "design") into an intermediate
  React + Tailwind CSS layout tree containing auto-layout, padding, typography,
  and component metadata, wrapping any repository-linked components in
  `<CodeConnectSnippet>` markers with exact import paths and prop mappings; (2)
  `get_variable_defs`, which extracts the exact design token names and values
  used in the frame; (3) `get_metadata`, which returns a sparse XML outline of
  layer IDs, names, types, positions, and sizes so the agent can inspect large
  screens without exhausting its context window before calling
  `get_design_context` on sub-nodes; and (4) `get_screenshot`, which supplies a
  visual rendering of the frame so vision-capable models preserve spatial
  fidelity [12, 13]. Makers note that because `get_design_context` defaults to
  React + Tailwind, prompts for non-React targets must explicitly instruct the
  agent to translate the structural blueprint into the target framework [12,
  14].

- **F5. Component registries and documentation tools (shadcn/ui MCP and
  Storybook MCP) expose the buildable component inventory to agents as strict
  JSON schemas and compiled component manifests rather than free-form prose**
  `[consensus — vendor documentation, resting on summarised fetches]`. With
  shadcn CLI 3.0+ (`npx shadcn@latest mcp`, 2025–2026), component libraries
  publish a root catalog (`https://ui.shadcn.com/schema/registry.json`) and
  per-component definitions (`https://ui.shadcn.com/schema/registry-item.json`)
  specifying exact file maps, npm dependencies, internal `registryDependencies`,
  and CSS/Tailwind variables, allowing agents to search, inspect source code,
  and install existing blocks rather than inventing markup [15, 16]. Similarly,
  Storybook's MCP server (`@storybook/addon-mcp`, 2025–2026) compiles component
  stories (Component Story Format) and MDX documentation into lightweight JSON
  Component Manifests containing component descriptions, strict TypeScript prop
  tables, default values, and canonical usage snippets, preventing agents from
  hallucinating props or inline styles [17, 18].

- **F6. Disconfirming evidence confirms that pure text specifications fail on
  two-dimensional spatial geometry, responsive states, and visual hierarchy,
  leading practitioners to pair text "design contracts" with screenshots or
  visual render-critique loops** `[consensus — practitioner reports, resting on
  summarised fetches]`. Queries for `"spec-driven development fails for UI"`
  and `"screenshot beats specification"` surfaced consistent practitioner
  reports (2025–2026) that while text specifications and EARS rules work well
  for backend logic, state transitions, and API contracts, translating spatial
  relationships, flex/grid wrapping, contrast, and viewport responsiveness into
  linear prose causes severe semantic loss and under-specification [19, 20].
  Practitioners report that vision-language models given a target screenshot or
  connected to a browser render-and-screenshot loop (Write -> Render ->
  Screenshot -> Critique -> Fix) outperform text-only specs on layout fidelity,
  and that the working pattern is a hybrid: a visual target (screenshot or
  Figma frame) for spatial layout combined with a concise text "design
  contract" specifying design tokens, component reuse, and behavioural states
  [19, 20, 21].

## Unexpected

The card groups "the design file of spec-driven kits" and "a design file for
agents" as parallel ways of describing a user interface for an agent that
builds. Primary sources show that neither file actually describes the layout and
elements of an individual screen [1, 3, 6]. In spec-driven kits (`spec-kit` and
Kiro), `design.md` (or `plan.md`) is a software engineering architecture
document (sense 2 of "design": database schemas, API endpoints, sequence
diagrams, module boundaries), while user-facing behaviour stays in
`requirements.md` as event-driven EARS sentences [1, 3]. Conversely, in Google
Stitch, `DESIGN.md` describes the global visual identity and token system of an
application (sense 3 of "design": colour palette, typography scale, spacing
grid, and component styling guardrails), while individual screens are held on
the visual canvas or exported as code [6, 7]. Between system-wide visual
identity (`DESIGN.md`) and low-level component schemas (`registry-item.json` /
Storybook manifests), there is no established vendor standard in 2025–2026 for a
pure-text, human-authored screen-layout file; tools either use a visual
canvas/screenshot (`get_design_context`, `get_screenshot`) or jump straight
from user-story/EARS requirements and component manifests to generated code [1,
12, 19].

## Not found

- **No open-source schema or vendor standard for a pure-text, per-screen layout
  file in spec-driven kits:** Looked in Kiro documentation (`kiro.dev/docs`)
  and GitHub `spec-kit` (`.specify/templates/`), which define `requirements.md`
  / `spec-template.md` and architectural `design.md` / `plan-template.md`, but
  provide no dedicated schema for spatial page composition or per-element
  screen definitions [1, 3].
- **No direct raw page fetches:** Because the execution environment blocks
  outbound shell commands (`curl.exe` denied by user-configured rule), no page
  could be read in full raw HTML/Markdown; all sources were accessed through the
  engine's grounding `search_web` tool as summarised fetches.

## Options

1. **Adopt a three-part textual split aligned with agent tooling (Visual System
   `DESIGN.md` + Component Manifest/Contracts + Screen/Flow Requirements in
   EARS) and require a visual preview step for spatial layout.**
   - *Trade-offs:* Matches how 2025–2026 coding agents actually consume UI
     context (global tokens and guardrails in `DESIGN.md`/`CLAUDE.md`, reusable
     component APIs in a registry/manifest, and testable `WHEN/THE SYSTEM SHALL`
     behaviour in requirements), avoiding the high failure rate of prose spatial
     descriptions [1, 6, 15, 19]. However, it requires a live preview or
     wireframe generator (covered by other cards) to close the spatial loop.
2. **Encode per-screen structure as a lightweight hierarchical outline (similar
   to Figma MCP's `get_metadata` XML/tree outline) referencing named component
   definitions and tokens, paired with EARS behavioural rules.**
   - *Trade-offs:* Keeps the entire specification in git-versioned text and
     tests the project's hypothesis of composing pages from small element
     definitions while staying close to the tree structures coding agents parse
     in `get_design_context` and `get_metadata` [12, 15]. However, prose or tree
     outlines still under-specify responsive wrapping and visual balance unless
     paired with strict layout primitives (such as stack/grid tokens) and visual
     verification [19, 20].
3. **Rely purely on prose screen specifications inside a single spec-driven
   `spec.md` / `design.md` file without separate token contracts, component
   manifests, or visual targets.**
   - *Trade-offs:* Simplest document chain (one file), but directly contradicted
     by both vendor architectures and practitioner evidence, which report
     generic "AI slop" styling, hallucinated component props, and broken spatial
     layouts when agents build UI from unstructured prose alone [9, 17, 19].

## Relevance to this project

**Recommendation (agent inference):** When designing the project's textual UX/UI
description for an AI builder, do not overload a single prose document to do
all three jobs of "design". Instead, structure the specification so that it
cleanly feeds the four inputs coding agents of 2025–2026 are built to read:
1. **Visual identity and aesthetic guardrails (sense 3 of "design"):** Adopt a
   `DESIGN.md`-style section or file combining explicit design tokens (colours,
   typography, spacing scale) with high-level aesthetic direction and explicit
   "Do / Don't" anti-patterns (as prescribed by Google Stitch `DESIGN.md` and
   Anthropic's `frontend-design` skill) [6, 9].
2. **Reusable element/component definitions:** Align the project's proposed
   per-element Markdown definitions with the information carried in Storybook
   Component Manifests and shadcn's `registry-item.json`—specifically: purpose,
   allowed variants/states, strict prop/content inputs, and token bindings—so
   an agent treats elements as a constrained inventory rather than inventing
   ad-hoc markup [15, 17].
3. **Page composition and interactive behaviour:** Express page structure as a
   hierarchical tree of named elements and layout containers (mirroring the
   structural outline of `get_metadata`), and express all interactive states,
   loading/error handling, and navigation triggers in EARS syntax (`WHEN ... THE
   SYSTEM SHALL ...`, `WHILE ... THE SYSTEM SHALL ...`) rather than loose prose
   [1, 12].
4. **Visual verification hook:** Because practitioner reports show that text
   alone under-specifies 2D spatial geometry across viewports, pair the textual
   description with a rendered preview or screenshot check during the human
   tuning and agent build stages [19, 20].

This recommendation rests on the convergence across Kiro [1], GitHub `spec-kit`
[3], Google Stitch `DESIGN.md` [6], Anthropic's `frontend-design` skill [9],
Figma MCP [12], and shadcn/Storybook MCP servers [15, 17], and is chosen against
both unstructured prose prompts (which produce generic "AI slop" and prop
hallucinations) and 50-page monolithic text PRDs (which fail on spatial layout
and responsive states).

**Consult when:** Designing the schema and section structure of the UX/UI
markdown artefact, deciding what metadata a reusable UI element definition must
carry for a coding agent, or configuring MCP servers (`DESIGN.md`, Figma,
Storybook, shadcn) and agent instruction files (`CLAUDE.md`) for the build
stage.

## Sources

1. **Specs - Kiro Documentation** (`requirements.md`, `design.md`, `tasks.md`),
   AWS / Kiro (`kiro.dev`), 2025 (dated via secondary/practitioner citations of
   the 2025 launch documentation; page itself undated in summary),
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHWGIMNkYCYgksAKsr5bvI1YuUhWQPGWkwwRVQ8Ybr37btpp86c__s27h4eMQIVeNGx9NCJZXz6R-cQZx7RtkYGH8jnrN4u9uaqUtb2_n3YvQZo2xsibJoJHE7ejRVHAxAOmw==
   (and
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFaAZojYNRwsBg0L-wFfs09B3mUvpdXDbAY_qHTKEYud6oxUVktemXN_GW_DAkeJ89OZzSfDGLe-hO0fA9aEn2zCwBwMHtb6gG-eUbbdWnU1V9Z_iGU0ZS9j-7PcR1-oSkO4bJOPS36d52mhlE--I6N5a9vy_FfUg==);
   kind: primary vendor documentation (read via tertiary summarised fetch); how
   read: summarised fetch; original.
2. **From Chat to Specs: Deep Dive into AI-Assisted Development with Kiro**,
   `dev.to` practitioner report quoting Kiro documentation on `requirements.md`,
   `design.md`, `tasks.md`, and EARS, 2025 (dated by context of Kiro 2025
   release; undated in fetch summary),
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHyf6GvJleoQ8Kw1BYmFO-PfudHPfu4dWHj8wq-54bz4yAp4FU85GOCyFgBZsV67ieN0MLVkfTmRQ3XDjZnc_4TN1j7FCKjdP669mpE3gAiXYW1r9njjVnshFCKOM1zR_LgI4B4AwaCB77yORlZWXYJPpGpLdru_HNAQDqnqGhn9WrJJCrFXYHp480FZ0126gKsBqTRmzr2MNiVUcZHeW-m6E6kBbC9sqBxvazchCvDk4lkllvDLgUX3aQUmHo=;
   kind: secondary practitioner report quoting primary docs (read via tertiary
   summarised fetch); how read: summarised fetch; original report quoting Kiro
   docs.
3. **GitHub Spec Kit (`README.md`, `spec-driven.md`, `constitution.md`,
   `spec-template.md`, `plan-template.md`, `tasks-template.md`)**, GitHub
   (`github/spec-kit`), 2025 (undated in fetch summary; repository active
   2025–2026), https://github.com/github/spec-kit/blob/main/README.md (and
   https://github.com/github/spec-kit/blob/main/spec-driven.md,
   https://github.com/github/spec-kit/blob/main/.specify/memory/constitution.md,
   https://github.com/github/spec-kit/blob/main/.specify/templates/spec-template.md,
   https://github.com/github/spec-kit/blob/main/.specify/templates/plan-template.md,
   https://github.com/github/spec-kit/blob/main/.specify/templates/tasks-template.md);
   kind: primary repository artefacts (read via tertiary summarised fetch); how
   read: summarised fetch; original.
4. **GitHub Spec Kit repository grounding**, GitHub (`github.com`), 2025
   (undated in fetch summary),
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFYEbwRiXtnANAr09-c5r_tJFyoXbaPN9sXTnKBwhJ9xD5qBc9kmL7pKBLCeqVaR9vkwrEKisWiIcH5jOGunJmAxgFQEhX7tL7irQErjysaF7apkWv4enhESsQpWwikTKf5-T2PK9SANtXbigf80z46cqVVkfL-cQWfFwNkCDFwD0pk9hMeKg==;
   kind: primary repository (read via tertiary summarised fetch); how read:
   summarised fetch; original.
5. **Understanding Spec-Driven-Development: Kiro, spec-kit, and Tessl**,
   Birgitta Böckeler (Thoughtworks / `martinfowler.com`), October 2025 (dated by
   byline reported in search summary),
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGdxN-fgGFTpu0vFJ-yC6sJUC4ZchIL_fYS51rCIElky3ULB3hYIVMpEbL9_gzYKYzcrduumi8R8RMcZhpl8iNEw1_EnMKttYt4BnuuWNRv_-foZoV7ux_hS3r33yIbZDnNsqECude2KZ_zs-IMyNy_4nOl6O0vRO0npLMG1x-uz8b9qMnotuItlafwbowb
   (and
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGtL7xBoClAVkJ-CAODCE3zwZ3aYicwUbQF4zs22506ALlb1Nm3ontqcFrMjCAHcwUz_S9Cz_x_Tm7uqc839vSynitotDq9XPQc5-sfz3Hc-hMHr7dMZigVqRJRzWDUNxTzVANlz1vE15pfUgaCURqhtGYGu7BnALBir5bDZiwVgWgz9O9kSA==);
   kind: secondary practitioner evaluation and taxonomy (read via tertiary
   summarised fetch); how read: summarised fetch; original.
6. **Google Stitch `DESIGN.md` Specification and Open-Source Repository**,
   Google Labs (`stitch.withgoogle.com` and `google-labs-code/design.md`),
   2025–2026 (undated in fetch summary),
   https://stitch.withgoogle.com/docs/design-md/specification (and
   https://github.com/google-labs-code/design.md,
   https://stitch.withgoogle.com); kind: primary vendor specification and
   repository (read via tertiary summarised fetch); how read: summarised fetch;
   original.
7. **DESIGN.md specification and CLI practitioner/documentation reports**,
   `dev.to` and `substack.com` citing Google Labs `DESIGN.md` specification and
   `@google/design.md` CLI, 2025–2026 (undated in fetch summary),
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFxn2NpjA-qCAiB_hci_HsNHEcrQisPwhzOvSrOoVlzNTbSmlodPhS6HcWahPL9NYjRSYCsI7OH-1uGPeE0b1vuC2e73pIJ4ac9nH7lx3is7mfIE-b_tAfEtUhdFzAk7IpHYeDe983lWTjrvRSEvmPcCOAkzzk-xa9l-fjonfcCm2XnTBre42AGShjAG87mbEbtzDrBFiNpQxn3A9kEILmE
   (and
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFMv9fFsYYlaz9WKiofCHWebLuZz5OmMC7464qnnKdL6axCjO2aTrD48r2AXOU3jC07wWiHrNeaJpfC05ypHKdd1cLdRBJqgui5DavF-JJH-THCpcJX7d5RY5RJ8hBLqG4NMrw_fWSIVmh1wk3jj1eGne0aFKgDrhLfNxnwUDi4EveWhQ79FFUMMQkC_-s=);
   kind: secondary technical analyses of primary spec (read via tertiary
   summarised fetch); how read: summarised fetch; original.
8. **DESIGN.md structure and token/guardrail format**, `designproject.io` and
   `medium.com`, 2025–2026 (undated in fetch summary),
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHyPg1WO71IMHllg9f1CEHJ1XjrtT_cnfc687J6SVlvms_JkWpixUVF5LOTnUa5OXoKrmsXKXNNTW6p2zd6zfrteCdhhIB0yBREV0hOZc8fTUp4Ts7B7ZQr1UQxqIn5DyjDEsDZKdokBA==
   (and
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQF_wXI_jR2A0Pd69xGOG5zWl5VB-_QWCzWLoVipfEA5BMcVn0eqxNs-ehsu1YvESK0FbLLNqrwURX1XtiiZyUh25XTpp5MDYoLNWi-LBXMkTcWYM7wvINgjPeKoDP2thYSRGWwTPDx-vWniNNKuDikVNZ06JdHYuHzPy01YdxAuu3g3P8AsYUXh41qBbqNADZ5Rt8bWED8I3whmzDSAFwuFazVk2iy40JjIaf5EHVXYvLOFUUoaZA==);
   kind: secondary practitioner guide (read via tertiary summarised fetch); how
   read: summarised fetch; original.
9. **Improving frontend design through skills**, Anthropic (`claude.com/blog`),
   2025 (undated in fetch summary),
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHhHYMnRy7PD6GgVDuDEmOvpbt4GK4Y9_VtoEHavirCx6qv7KJjKsZQxrHRla6IQ-LKxKymdCBOIJPvAwPTMgQAlWvcc9ekhE-Mefi6NbpKYPTKVzcaJPkHqiRwv67KVFVNLi2bkEDWN2uMH96I-xBu1Wj1eSjy2H79dsoQ4jX24KFsHCerSQms
   (and
   https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGwGAnwbanETmUmwicckUQXOl2ovx1BCDF8eCjDXfveAQUNRc073_cZN8GtJTM3ioIJ5uyPV0qyzdBlPMHxhKi5Vug-0AjM7SrNddw-qx0DVc2eLxSoce7CX6USZL4wH_oc4Dg-Zu5332djFECW4Vid6aP6J-xDYZYaLtgCUpFIUmLzEtQwBZ1C);
   kind: primary vendor blog and documentation (read via tertiary summarised
   fetch); how read: summarised fetch; original.
10. **Anthropic `frontend-design` `SKILL.md` repository artefact**, Anthropic
    (`github.com/anthropics`), 2025 (undated in fetch summary),
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGzqtz_eJrKtkz6Fi0NHA6Y57JmRe6KHUt6Akx1bpQOP99yKu3IMbO4IR72JnPLNDhFpySSFr7DgljzSjEvqgBJ9xWmgZqJ9-NUdpKzYTgMkyOxahfAyoiv1Y5YjHkVpZVPRot_KlyalSg6TqadqfY_RViQWgKYtoU-IKLZQzSq0B88I_14s5LR7KfmlsycqVQwHd2cZsYdjFq2sAdxVgnFlVDzlfQrcdvfqwMn1w==
    (and
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFQdvxoEQLNx74LPa14u9Jz56mubsfM15IJEXu70i_NFk6EAk4ba-LEe8yvJ-r5o_uwC2FdbAxyQoBe3PgQ3He6c-QPCVBM3PXn_hG2Bi1Vu7t80SZtO7TzI9Mm98HxuuFcpyLdA1AO4BXeRxU_1PAh6U7WbgoqxwqWpL7Qd-UCBEFNwabxl2LnUYiliBWnejEhIIl-GRyG);
    kind: primary repository artefact (read via tertiary summarised fetch); how
    read: summarised fetch; original.
11. **UI & Design Rules in `CLAUDE.md`**, Subframe (`subframe.com`) and
    `rottoways.com`, 2025 (undated in fetch summary),
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGza1-NTZ47Jrw7j6PNDh3lOhXbsUlFpqqLCOTl9V2763HoLcClV-drVXtQsK-5QVVxmQCmRRUQZ0OGF9UF2SPVhb4YXga467vq2fTtEFdGUqWo8bmwQNmAiQhntPY3NNZjj-MtxiPp2Wqm2TNgciqGnpabGQ==
    (and
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEUuUDhn6fe8OtiIRrgpuR4xdm3B2AM1aeQzQllc71C7avmqPRK8avMtpb5oYesoaP6Amp2RWal_7SoAIBl7GMZo8537ZUM-2Z580Yv28gcQnkGOzK84Lby9mxlC9AVMxePnYlSEPomkzFnvuIfor8puA==);
    kind: secondary practitioner guidance (read via tertiary summarised fetch);
    how read: summarised fetch; original.
12. **Figma MCP Server Documentation (`get_design_context`, `get_variable_defs`,
    `get_metadata`, `get_screenshot`, Code Connect)**, Figma
    (`developers.figma.com/docs/figma-mcp-server`), 2025–2026 (undated in fetch
    summary),
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHjdENG_CV1pBN_sdxvELQ58Xn51Z8eGfmnIifMc_vri8ktd9h7Ru7_WbZCp3Rc1TMhKRS10k5N60FKWfJfMJC270zcw9rDoycjWHVDWCsGlKTXHNttYTwBcaTjrXz0suwPdlN19YXg5ysAfrsBznXMRDNu0vDcWdR4q6qmLd7ADw==
    (and
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHFPIwArc4FZT6u6BWTgbxuU0Lndui3VN7j_StgmuRDIAfBi-LFD6rcK3bot-Wl12a-eGpQpMbDbBAqMyLKOR4QuFJYwdAr3mJ82NR9M4JNrRRnEH4Vg-xOcYeqjuLxnf7FP7-bmvdIc1vePeVXGKP3vM0HEQMRTttdvzV8cTdfWddKgbZ3X-Mj,
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQE71zeoi9KntxisI9FBTQGIBmkJ81K-uU6UiBQywwgBki47HOYsXPjRZXUT7tgMx5kB8N1r7jmFnA8ksx99c9oZGncVP6s_gIJri-_fQ13c0J2DRoegooIdWl72DxpDfvJdu39RxwYkL0CyXDGltzoNXY1oFYMYIzJ8TBxvq31B4UWGT0M=,
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFj-PPKrqnAcmnrD7NgyhbGSZWFPehd0aUGvM94Tl6jOoBIUA1EEjLAzHhpgUTaW6hLbzd6CNXmxqYGgP8YGC-8nvf_bWSrFiPugkHtr0rGVW--bYaDjqWju8pnlcwZBF6xFxvv57C8dtd49Qcy02Jeh2qPSt9K8oefN_7XMuc0);
    kind: primary vendor documentation (read via tertiary summarised fetch);
    how read: summarised fetch; original.
13. **Figma Code Connect MCP Integration Documentation**, Figma
    (`developers.figma.com`), 2025–2026 (undated in fetch summary),
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQERMz7P4-WNblSGxaf0q-pJSMK2PCeK-hEES0V9BVIa6kWTf-GRhebr-OPHM5h-sUyqfTGy8OnRHh4icaETg_vlvb0NFniZlCTYsEh4tQf4V9JBqoYdoRdaF4se_GgcwrXdk_f1ek1HOjNAE4IL_C0fOiYa8n-1BBinKm5JlPx5QEGZPgRNJw==;
    kind: primary vendor documentation (read via tertiary summarised fetch);
    how read: summarised fetch; original.
14. **Figma MCP Server Guide Repository & Practitioner Usage Notes**, Figma
    (`github.com/figma/mcp-server-guide`) and `uichemy.com`, 2025–2026 (undated
    in fetch summary),
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHxCbOuhJjg6SPIGCcDQzLiyZSFZMRikXvvzTONU3wb8sYOr0NNG6P580kDElMay_1ZFsq4lZMBJneR-LWFtYFWvB4awkm0JY1LgTSXpqgaRXXugBZmDZyiMzTECUZsJdFDmQ==
    (and
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFO4YxsBjTMkbs5V-xbQrSar_ZOkUaWLt_fxAojVVjHeoRw2YWnRNWGbNDg24C8Oui7CCyjcNssnfQWq3b9w8-aiZb3lwxthUC3eOsgeZURjne7YeDpeTfD2b88NK4=);
    kind: primary repository and secondary practitioner guide (read via
    tertiary summarised fetch); how read: summarised fetch; original.
15. **shadcn/ui MCP Server and Registry Schemas (`registry.json`,
    `registry-item.json`)**, shadcn (`ui.shadcn.com`), 2025–2026 (undated in
    fetch summary), https://ui.shadcn.com/schema/registry.json (and
    https://ui.shadcn.com/schema/registry-item.json,
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGu6S_gZufaD42Ei6Y57saPmcTcA13ZFn3OQVlMZ4pjenfyoBu6qqdHhRIxgjHC6K5lOeyC8aVdIY5zcXFQ6i3PTV2UpzllMYbxYCRiy8GzRkDsPuSfzE3xQKVVzJC7FmwKEIB-B5pGxPNQFYmY9DNl8w==,
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEkgyKvS5RMcWYsguSR6_CI2niqyD3_7ZPTH3XtOpCHzm7snRmhKHA2w4mec1WhB5SeFQkDWDfU_xB9PUGKlSijPs1KhoPRwpIvGujon4Tuk3dMpRvLrob5jK5h2vNunJ856bRHyUdn);
    kind: primary schema and vendor documentation (read via tertiary summarised
    fetch); how read: summarised fetch; original.
16. **shadcn MCP CLI Tools Overview**, `uichemy.com` and `marmelab.com`,
    2025–2026 (undated in fetch summary),
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHXJrt-riwKXtsTNh1h3hNJQ-cktaDlfmX9iLH-le1Cc1EbaON_es9lg2b9lEOVuhCV1TN1-M_cL9oHkNFhXyG_a3ctl6KUUtP-v9xrpQsR_feH8e73Nek4jbm4v5w6szvQhutQ6kE=
    (and
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFMusWNUW7ARqs8hv37Ncp3QzWp31wkJJyQtb6_oWpnXh-mhliPaAuiZxRRUyb9KBQ3xrIY48drgqcLZEsdELO1vo_RJ-FrxhmjBNgn2CChEPEWOWHZvoiPrLVpG0MfzwNgB3Mh9n02r_WxuPZS1Sm4c9JUwwWL5BGm);
    kind: secondary practitioner documentation (read via tertiary summarised
    fetch); how read: summarised fetch; original.
17. **Storybook Addon MCP and Component Manifests Documentation**, Storybook
    (`storybook.js.org`), 2025–2026 (undated in fetch summary),
    https://storybook.js.org/addons/@storybook/addon-mcp (and
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQH02wwFMcQT2yT7TFV3hO1llD3lgt686B-CJkK_Ho81mwVN8ZGDVzyIFA4hXDQU2jI0xOV55uJZqYqyibbnL4kMyVcAZetivxn17VOFCSOKzYc1WgNwYROieSKiJdtxSgH6iEd_,
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQElh9m9-XZrPzBXKvJzRr1hu43qEKp_kBssA0BgM9QIMurhMd5139b2t-DunqrJXPEBJN91AyHsG95wITzo7oDgYJC54KEnFxRFqsJrV2zlA5G1r5PaEBNDLiJfAR5OnfH2LgNXUMl8rNT6ZqDxvll1Ub8=);
    kind: primary vendor documentation (read via tertiary summarised fetch);
    how read: summarised fetch; original.
18. **Storybook MCP Repository**, Storybook (`github.com/storybookjs`),
    2025–2026 (undated in fetch summary),
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFcZjhyb-J9ic9J7dC69M3C-yihIi938yhhrnVQ4hYyK3wJqjO-3d96O0-gN_riNnzrM9Y6lY10l1oDo7vcGeT_FuuRyCJkgEBgLlKvsd6StMZgtVuNJdV7oX9wiYMU5sP40ptw2mMKjFtnA-oTnlVlYzXWL3At-BOqx3tiXqxhS8Pg;
    kind: primary repository (read via tertiary summarised fetch); how read:
    summarised fetch; original.
19. **Why Spec-Driven Development Fails for UI / Screenshot Beats
    Specification**, `setproduct.com` and `medium.com`, 2025–2026 (undated in
    fetch summary),
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGP8vHLkYmnvqh-IR493UdBf3QLA3yGrKuXZVSKsXJZ0mAhnIWvTMkW0Dpe4k2Iffzh3l9UXyNTFracdujJ4XVPE6s0_GSSBxnQnWLn0Xr4nbGXfCvhSGd21F8oosUIlVMzmz6D42RCnY769ntHiND72IRTwzaCpVI=
    (and
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQG2gb3NWgByTVzAsXx4sAA0_RUaWUxCy8kI5uvyDwcB57gyoRyRs2Wteq16YzsrCGAsMbfUJ2jEYSQdg9iCBeFYH2bl3F5CZMe0H7h8VPG1zgeKRZ6Th49t2U8oH2KtqUroe3Pz-fZuK571GWCmVi42t2tMGWAy_rny197ay4keC8nKtryd9OXOM8BIQRMaAsqJkf6HH3BlclddLrs81EYz5w==);
    kind: secondary practitioner analysis (read via tertiary summarised fetch);
    how read: summarised fetch; original.
20. **Design Contracts and Visual Proof in UI Coding Agents**, `reddit.com`
    practitioner thread and `augmentcode.com`, 2025–2026 (undated in fetch
    summary),
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHwIngp6I50yV6l3EEOphGqweczElgudvVtTwCWhKfb1GjJk-XNhGfvZj_OI7TVMLpFXZ11gOrVdFBGncQtsypzkwvuy1SOX_s8hZXCZPlGuOk9uCECEBo4RwdKeB_4Ih5qSHshvTnVKmCdHdkGv-xC0aOvKvHu5f6AFScOv9GhLuiqh0P4FLACS3VyvBVsm36q3qa-ZV6gKMPuEaPAHqU=
    (and
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEQkrJotL1-YilQAUwrNTCSv0pXQ7GqlnqcVCpb2sHJlga81dP1ApOq7OGXtz6QW7sKrgDGmSxEJ7gC5TuutWx7VkdZxQG5vsYOeK9gTwwZqJzcNUDNxbNWrjLEN0rfdgNJIbRF1dMs_4J7Xqo2eQOo4unBs7UcJmww8u-Q);
    kind: secondary practitioner reports (read via tertiary summarised fetch);
    how read: summarised fetch; original.
21. **Agentic Visual Feedback Loops for UI Generation**, `mindstudio.ai`,
    2025–2026 (undated in fetch summary),
    https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGIRyOvByLzz4i-WtyBY6mTA6DATULXr-V3RvpQ0Gb_5TO_MHH1dHYgX4YQUUggsaOxyDFGCNh6HkQxN5IKm1pxBqSiV2umLMSlllckFG6uFaU_EdqusRBx_KHXiG1Skklv5VnbCd8es2-Py-PCdPCzeyNs8OPcL-QzmlWsFs408M3A0PG2XEDHaKbP6A==;
    kind: secondary technical summary (read via tertiary summarised fetch); how
    read: summarised fetch; original.

## Opened and not used

- `thebcms.com` SDD overview (https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFTBAlY-e_SaIjVHsBmBLM3DqDXP2GrPYP9UZhQxzPkikayAN5qfXAQz5l9mXu-egEV10drHPujMRKVK608_9D0lbDbArpORvhI6PCO-q7G9KvmJvHdLiLJMbQiQP3CzgKspioaRL2Yc3yx-lE2rcb0): superseded by primary Kiro and `spec-kit` sources [1, 3] and Böckeler [5].
- `daily.dev` SDD summary (https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFDxUCQiGYe-YGE3olcS8o0ODpf_AmA5sBsoB3Tm4SdWN5tvWrGMAGHxQGCqkizNUXfV4H5VMf0y_C2c6Zf-aqPyFrkjQHZ4hgF0uskm1FmFrMPVX4UpgJarqVphB7sag9zjILqSVRR9prNwPpdLDy16qy2hlDb76QCmYYylvX1eImcdDNHmPqzdgy_yys6Wp8=): secondary aggregator superseded by [3, 5].
- `truefoundry.com` SDD summary (https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGL8950jTXTEuO3hNh8JkQzWn1Q6PRr4fMrQVYBnGmQEuuW6Mltg-AhwUzx-WJo4k-FfdrPeCu77i_q1L2QaRT8EmFVlHZaK3aPspMu0kfgEAG0uOLkEHrdK0C_s_BYIR0h9jxK2EftXJOHalK1bm-eXP4AUSqFkXZd_VtH4Q==): secondary restatement of Böckeler's Martin Fowler article, superseded by [5].
- `skywork.ai` Storybook MCP summary (https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQF6gl_apvVuGe1MQbGpHiI2LK-HYWMhBfHOfSxY48TR0-_lvHVid-2f9ggdHA8Nq-L78biKLPK061NfWcxg4mQlBrmQEyHHOTu2yeIe9QmDPKL9xloA72i7qpGtvS1CvIl6QB-t1HKx_-l_89xgJTqZnKgpayCPHKu8m6JH_P6lCMlG6D9FkL8=): secondary overview superseded by official Storybook documentation [17, 18].

## Search record

**Queries run (in order, 15 `search_web` calls total; direct shell `curl.exe`
was tested once and blocked by a user-configured deny rule, so all openings
were performed as `search_web` summarised fetches):**
1. `"DESIGN.md" agent UI design system specification`
2. `"spec-driven development" UI design file Kiro "spec-kit" EARS`
3. `Figma MCP server "get_design_context" coding agent documentation`
4. `shadcn registry MCP server "registry-item.json" OR Storybook MCP agent context`
5. `Anthropic "frontend-design" skill OR CLAUDE.md UI prompt rules`
6. `"spec-driven development fails for UI" OR "screenshot beats specification" UI coding agent` (disconfirming query)
7. `site:kiro.dev/docs specs requirements.md design.md tasks.md steering EARS exact URL and quotes` (domain: `kiro.dev`)
8. `site:github.com/github/spec-kit spec-driven.md OR README.md constitution spec.md plan.md tasks.md exact URL and quotes` (domain: `github.com`)
9. `site:martinfowler.com "spec-first" "spec-anchored" "spec-as-source" Birgitta Böckeler Kiro spec-kit date URL quotes` (domain: `martinfowler.com`)
10. `"stitch.withgoogle.com" OR "DESIGN.md" Google Stitch official documentation design system markdown format URL date quotes`
11. `site:github.com/anthropics "frontend-design" SKILL.md exact URL quotes typography color motion` (domain: `github.com`)
12. `site:developers.figma.com/docs/figma-mcp-server get_design_context get_variable_defs get_metadata get_screenshot Code Connect exact URL quotes` (domain: `developers.figma.com`)
13. `site:ui.shadcn.com/docs mcp registry-item-json registry.json exact URL quotes schema` (domain: `ui.shadcn.com`)
14. `site:storybook.js.org blog OR docs MCP server component manifest addon-mcp exact URL date quotes` (domain: `storybook.js.org`)
15. `site:martinfowler.com/articles/exploring-gen-ai "Understanding Spec-Driven-Development: Kiro, spec-kit, and Tessl" exact URL date quotes UI frontend workflow` (domain: `martinfowler.com`)
16. `site:claude.com/blog "Improving frontend design through skills" exact URL date author quotes "frontend-design"` (domain: `claude.com`)

**Pages opened (16 summarised-fetch searches grounding 21 cited primary and
practitioner sources):** Because `curl.exe` was denied by environment policy,
each targeted `search_web` call served as a summarised fetch over the grounded
URLs listed in `## Sources` and `## Opened and not used`.

**What the disconfirming query found:** Query 6 (`"spec-driven development
fails for UI" OR "screenshot beats specification" UI coding agent`) found
strong practitioner consensus that linear text specifications lose spatial
relationships, responsive breakpoint behaviour, and visual hierarchy, and that
feeding a screenshot or running a render-and-screenshot critique loop with a
vision-language model beats text specifications for spatial layout unless the
text is scoped as a lightweight "design contract" (tokens, existing components,
and behavioural EARS rules) alongside a visual target [19, 20, 21].

**Reason the run ended:** Both parts of the card's stop rule and the opening
budget were reached simultaneously at 16 `search_web` calls: every route in the
card (spec-driven kits, `DESIGN.md`, agent instructions/skills, design-system
MCP servers, component registries, and disconfirming practitioner reports) had
primary documentation grounded, and differently worded queries returned no new
artefact kinds.
