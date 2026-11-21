---
date: 2026-11-21
project: forge
topic: Changing and keeping an interface description after the first build
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 19; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":47589,"output_tokens":18168,"thinking_tokens":7841,"cache_read_tokens":126944,"total_tokens":65757}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-19-after-the-first-build
status: immutable
---

# How an interface description is changed, reconciled with build changes, varied across screens, and versioned after the first build

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Across spec-driven kits, design tools (where "design" means the visual
interface held in a canvas tool), and design systems (where "design"
means a shared visual identity and component library), keeping a text
description alive after the first build splits into three patterns:
*spec-first* (abandoned after build), *spec-anchored* (kept alongside
code), and *spec-as-source* (only the spec is edited). In spec-driven
kits (where "design" means the technical `design.md` between
requirements and tasks), changes to a specification are reviewed either
as direct git diffs or as structured delta specifications (`ADDED`,
`MODIFIED`, `REMOVED`) before merging into the canonical spec, while
changes made during the build come back into the specification only by
explicit human edit or an agent reconciliation command—confirming the
disconfirming query that unassisted synchronization fails through
specification drift. Systems of shared element definitions avoid copying
definitions for screen-level variations by separating the shared
element's schema (variants, boolean/text/swap/slot properties, and
settings) from page-level instance files (such as JSON templates) that
record only instance IDs, ordering, and property overrides; however,
neither Markdown spec kits nor component definitions show their own
page-level blast radius without an external static scanner or reference
index. One unexpected finding reconfigures the card's assumption that
text diffs should be read against the whole specification file: OpenSpec
isolates proposed edits into standalone delta files (`ADDED`,
`MODIFIED`, `REMOVED` requirements) specifically because line-by-line git
diffs on full living Markdown specifications obscure whether a change is
an intentional requirement change or incidental rewording. All web
sources in this note were read via summarised fetch (a tertiary
retrieval method in this environment).

## Question

#### Card 19: The description after the first build
- **Question:** How is a description of an interface changed and kept
  once the product exists: how is a change to it read and reviewed as a
  difference in text, how do changes made during the build get back into
  it, how do systems of shared definitions handle a screen that needs a
  variation of a shared element (variants, overrides, instances) and
  show which pages a change to a shared element touches, and how are
  such definitions versioned?
- **Why it matters:** the cycle runs again whenever the interface
  changes, and the idea of a definition per element stands or falls on
  variation and on the reach of a change.
- **What would answer it:** the documentation of systems that keep
  shared definitions, and of spec-driven kits, on how a change is made
  and carried.
- **Where to look:** design systems on versioning, breaking changes and
  variants; design tools on components, instances and overrides; block
  and section systems on variations; spec-driven kits on changing a
  specification after code exists and on bringing changes of the code
  back into it. Search words from card 1: "spec-driven development",
  "spec-first", "spec-anchored", "spec-as-source", "constitution",
  "steering files", "EARS", "DESIGN.md". Primary artefacts in public
  repositories (schemas, component and page files, agents' rules and
  prompt files, the schemas of servers for design tools, issue trackers)
  before commentary about them.
- **Disconfirming query:** "keeping specification in sync with code
  fails", "design system overrides chaos"; expected: bringing changes
  back is done by hand or not at all.
- **Stop rule:** nothing new from a differently worded query and every
  route has a primary source; ten to fifteen pages opened.

**Baseline to beat:** Without this research, the default assumption is
that keeping Markdown definitions per element and per page in git gives
clear text diffs for free, that an AI coding agent automatically keeps
the specification aligned when implementation details shift during the
build, and that a shared element definition can simply be edited in
place when one screen needs a local variation. This note must replace
those assumptions with the actual mechanisms used in spec-driven kits,
canvas design tools, block/section architectures, and component
libraries—and identify where synchronization and variation break down.

## Key findings

*(Note on evidence retrieval and terminology: Every web source below was
read via the environment's `search_web` grounding tool, which is a
summarised fetch—a tertiary retrieval mode—including where targeted
queries returned verbatim quotes from primary documentation or
preprints. Throughout these findings, "design" is disambiguated into
(1) technical design documents such as `design.md` between requirements
and tasks in spec-driven kits, (2) interface design held in a canvas
design tool such as Figma, and (3) the shared visual identity and
component library of a design system.)*

- **F1. Post-build specification maintenance divides into three
  distinct regimes—spec-first, spec-anchored, and spec-as-source—and
  current spec-driven kits operate as spec-first or manually triggered
  spec-anchored systems rather than automatic spec-as-source.**
  [emerging — practitioner claim and preprints, read via summarised
  fetch]
  In a comparison of Kiro, GitHub `spec-kit`, and Tessl published on
  2025-10-15, Birgitta Böckeler defines the three levels verbatim in the
  paradigm taxonomy section [1]:
  - *"Spec-first: A well thought-out spec is written first, and then
    used in the AI-assisted development workflow for the task at hand."*
  - *"Spec-anchored: The spec is kept even after the task is complete,
    to continue using it for evolution and maintenance of the respective
    feature."*
  - *"Spec-as-source: The spec is the main source file over time, and
    only the spec is edited by the human, the human never touches the
    code."*
  Piskala (2026-01-30) adopts the same three-tier classification in the
  abstract and architecture sections, noting verbatim that
  *"Spec-anchored development treats the spec as a living document that
  evolves with the codebase. When a feature changes, the spec is updated
  first or simultaneously with the code"* [2]. In practice, Böckeler
  notes that `spec-kit` and Kiro focus primarily on generating tasks and
  initial code from feature specs (`requirements.md`, technical
  `design.md`, and `tasks.md`), leaving long-term post-build upkeep to
  explicit user or agent action rather than automatic regeneration [1,
  5, 6].

- **F2. Changes to specifications after the first build are reviewed
  either as standard git diffs on static Markdown files or as explicit
  delta specifications (`ADDED`, `MODIFIED`, `REMOVED`) that separate
  the change proposal from the canonical specification until archival.**
  [emerging — vendor report and repository documentation, read via
  summarised fetch]
  GitHub `spec-kit` and Kiro store feature specifications (`spec.md` or
  `requirements.md`, technical `design.md`, `tasks.md`) and global rules
  (`constitution.md` or `.kiro/steering/*.md`) as versioned Markdown in
  git, relying on standard line-level pull-request diffs when files are
  edited [5, 6]. By contrast, `Fission-AI/OpenSpec` separates the
  canonical specification tree (`openspec/specs/`) from active change
  proposals (`openspec/changes/<change-name>/`) [4]. Inside a change
  folder, OpenSpec writes delta spec files grouped under explicit
  headings—`ADDED Requirements`, `MODIFIED Requirements`, `REMOVED
  Requirements`, and `RENAMED Requirements`—alongside `proposal.md`,
  technical `design.md`, and `tasks.md` [4]. Reviewers read the delta
  spec to see what behavioral contracts are added, altered, or deleted
  before running `/opsx:sync` or `/opsx:archive` (or `openspec archive
  <change-name>`) to merge the delta into `openspec/specs/` and move the
  change record to `openspec/changes/archive/YYYY-MM-DD-<name>/` [4].

- **F3. Changes made directly to code during the build do not flow back
  into textual specifications automatically; bringing them back requires
  explicit agent verification/reconciliation commands or manual editing,
  and otherwise fails through specification drift.**
  [consensus — practitioner claim, preprints, and repository
  documentation, read via summarised fetch]
  The disconfirming query (`"keeping specification in sync with code
  fails"`) confirms the card's expectation: because updating prose or
  structured Markdown alongside code imposes a double-entry maintenance
  tax and exploratory coding alters edge cases mid-build, unassisted
  specifications rapidly diverge from implementation [2, 3]. Spec-driven
  kits address this post-build gap only through explicit, on-demand
  reconciliation steps:
  - In `Fission-AI/OpenSpec`, the developer runs `openspec validate
    <change-name>` or `/opsx:verify` to compare implementation against
    the active delta spec and `tasks.md`; if the build diverged
    intentionally, the human or agent edits the delta spec under
    `openspec/changes/<change-name>/specs/` before archiving [4].
  - In GitHub `spec-kit`, `/speckit.analyze` (and convergence checks)
    audits consistency across `spec.md`, technical `design.md`,
    `tasks.md`, and the codebase, requiring the user to prompt the agent
    to rewrite stale specification sections [5].
  - In Kiro, specs do not auto-rewrite on every code edit; users prompt
    Kiro to scan the codebase to check off completed items in `tasks.md`
    or propagate code changes back into `requirements.md` and technical
    `design.md`, or configure event-driven Agent Hooks on file save or
    commit to prompt for alignment [6].
  - Piskala (2026-01-30) and Grabowski (2026) argue that spec-anchored
    systems only prevent drift when coupled with automated executable
    checks or commit-level drift gates that fail the build when code and
    spec diverge [2, 3].

- **F4. Canvas design tools and declarative block/section architectures
  handle screen-level variations of a shared element through a strict
  hierarchy—predefined variants, exposed component properties/settings,
  constrained slots/blocks, and local instance overrides—while treating
  detachment as a last resort that breaks future updates.**
  [consensus — vendor documentation, read via summarised fetch]
  Both Figma (for canvas interface design) and Shopify Online Store 2.0
  (for text-based page and section files in git) separate the shared
  element definition from its per-screen instantiation:
  - In Figma Help Center documentation, a shared Main Component defines
    *Variants* (grouped into component sets by state, size, or style)
    and explicit *Component Properties* (*Text*, *Boolean* visibility,
    *Instance Swap* with curated preferred instances, and *Slot* regions
    for child content) [7, 8]. Placing the component creates an
    *Instance* that allows local *Overrides* (text, fills, strokes,
    visibility, nested swaps) while still receiving non-overridden
    structural and style updates from the Main Component [9]. Calling
    *Detach instance* converts the instance into an independent Frame
    and permanently severs update propagation from the Main Component
    [10].
  - In Shopify's Online Store 2.0 architecture, each shared element
    lives in `sections/<name>.liquid` or `blocks/<name>.liquid` with an
    embedded JSON `{% schema %}` defining configurable `settings`,
    allowed child `blocks`, and `presets` [11]. Each screen or page
    template (`templates/index.json`, `templates/product.json`, or an
    alternate template like `product.custom.json`) is a pure JSON file
    containing a `sections` map (keyed by unique instance IDs, naming
    the section `type`, local `settings` overrides, and child `blocks`)
    and an `order` array [11]. Modifying a shared section file updates
    every page template that references its `type`, while page-specific
    copy, settings, and block ordering stay isolated in the page's JSON
    template [11].
  - The second disconfirming query (`"design system overrides chaos"`)
    shows a recurring failure mode: when shared component definitions
    are either too rigid (too few properties/slots) or allow unrestricted
    deep overrides, authors detach instances or pile up local overrides,
    recreating visual inconsistency and breaking update propagation [7,
    9, 10].

- **F5. Neither a shared element's own file nor a Markdown page
  specification natively displays the blast radius of a change; showing
  which pages a change touches requires an inverse reference index or
  static AST/template scanner paired with design-to-code mapping.**
  [emerging — repository documentation and vendor documentation, read
  via summarised fetch]
  Because dependency pointers in component and template systems point
  upward—from the page or screen (`templates/*.json` or application
  route file) to the shared element (`sections/*.liquid` or UI
  component)—opening the shared element's definition does not list its
  consumers [11, 12, 13]. In practice, teams compute the reach of a
  change ("blast radius") with two complementary tools:
  - `moroshko/react-scanner` statically crawls application source files
    to extract a JSON inventory of every component instance, which
    files/routes render it, and which props/variants are passed to each
    instance [13].
  - `figma/code-connect` links Figma component URLs and variant
    properties to production component files (`figma.config.json`),
    surfacing the canonical code snippet in Figma Dev Mode, while Figma's
    own library analytics tracks insertion counts and detachment rates
    across design files [12].

- **F6. Shared component definitions are versioned either globally
  (monolithic version for the whole library), independently per
  component (semantic versioning via change logs such as Changesets), or
  in a hybrid model (global tokens and primitives, independent complex
  components), with breaking changes mitigated by deprecation flags and
  automated codemods.**
  [consensus — repository documentation and practitioner claim, read via
  summarised fetch]
  Adding a new variant or optional property is treated as a backward-
  compatible minor change, whereas removing/renaming a property,
  changing a default variant, or altering the structural slot contract is
  a breaking (major) change [14]. In git-hosted component libraries,
  `changesets/changesets` stores markdown changeset files alongside pull
  requests declaring whether each touched package receives a `patch`,
  `minor`, or `major` bump, then resolves cross-component dependency
  graphs at release time [14]. To avoid breaking pages on major bumps,
  design systems mark old props/variants as `@deprecated` for a
  transition window and ship AST codemods (assisted by usage data from
  scanners like `react-scanner`) to rewrite page-level instances [13,
  14].

## Unexpected

The card's framing asks how a change to an interface description is read
and reviewed as a difference in text, implicitly assuming that reviewers
read a standard git diff of the canonical screen or element Markdown
files. `Fission-AI/OpenSpec` [4] reconfigures this assumption: when a
specification is kept as a living document after the first build, raw
line-by-line git diffs on full Markdown specification files make it hard
to distinguish intentional scope changes from structural edits or
context shifts. OpenSpec therefore introduces an explicit intermediate
artefact—a *delta spec* inside `openspec/changes/<name>/specs/` with
dedicated `ADDED Requirements`, `MODIFIED Requirements`, and `REMOVED
Requirements` sections—so that human and agent reviewers approve the
delta as a first-class document before `/opsx:sync` or `/opsx:archive`
compiles those changes into the permanent specification tree [4].

A second lead is Kiro's distinction between feature-evolution specs and
bug-fix specs [6]: rather than forcing post-build fixes through the full
`requirements.md` $\rightarrow$ technical `design.md` $\rightarrow$
`tasks.md` chain, Kiro uses a dedicated `bugfix.md` structured around
*current behavior*, *expected behavior*, and *unchanged behavior* (a
regression guard in text) [6].

## Not found

- **Automated reverse-compilation from UI code back into Markdown UX/UI
  screen descriptions:** While OpenSpec (`/opsx:verify`), GitHub
  `spec-kit` (`/speckit.analyze`), and Kiro (`tasks.md` scanning and
  prompted spec updates) provide agent commands to flag drift or ask an
  LLM to edit Markdown specs from code [4, 5, 6], no primary source in
  any queried repository or arXiv search showed a deterministic tool
  that parses modified UI layout/component code and automatically
  synthesizes updated page-level and element-level UX/UI Markdown
  definitions without human or LLM authoring.
- **Measured empirical failure rates of spec-anchored sync in UI
  workflows:** Searches across `arxiv.org`, `martinfowler.com`, and
  `github.com` returned architectural taxonomies [1, 2, 3] and tool
  workflows [4, 5, 6], but no controlled empirical study measuring how
  often developers or agents fail to run post-build sync commands in
  production UI repositories.

## Options

Because the project (`forge`) aims to carry versioned Markdown
descriptions of elements and pages in git across repeated build cycles,
it faces four concrete design choices on how post-build changes,
variations, impact analysis, and versioning work:

1. **How changes to the description are authored and reviewed in text:**
   - *Option 1A: Direct in-place edits reviewed via git diff.* Authors
     and agents edit element and page Markdown files directly on a
     branch.
     - *Trade-off:* Zero extra tooling or merge step, and matches
       standard git workflows (`spec-kit`, Shopify JSON templates) [5,
       11]; however, in prose-heavy Markdown files, line diffs mix
       cosmetic rephrasing with substantive behavioral or layout
       changes.
   - *Option 1B: Delta-spec change folders merged on archive.* Follow
     OpenSpec [4] by staging changes in a change directory using
     explicit `ADDED`, `MODIFIED`, and `REMOVED` sections for elements
     and pages, then merging them into the canonical element/page tree
     upon approval.
     - *Trade-off:* Makes intent and breaking changes unmistakable
       during human/agent review, at the cost of requiring a sync/merge
       command to update the canonical files.

2. **How changes made during the build get back into the description:**
   - *Option 2A: Spec-anchored with an explicit post-build verify/sync
     step.* Allow developers or coding agents to adjust UI details
     during the build, followed by a mandatory verification step
     (analogous to `/opsx:verify` or `/speckit.analyze`) where an agent
     compares the built UI code against the page/element Markdown and
     proposes a patch to the Markdown before the branch closes [2, 4,
     5].
     - *Trade-off:* Accommodates real-world implementation discoveries
       without blocking developers, but relies on a CI or workflow gate
       so the back-port step is never skipped [2, 3].
   - *Option 2B: Strict spec-as-source.* Prohibit any UI or interaction
     deviation during the build that is not first written into the
     element/page Markdown description [1, 2].
     - *Trade-off:* Eliminates reverse-sync drift by construction, but
       creates high friction when minor layout or platform constraints
       surface only while coding [1].

3. **How page-level variations of shared elements and blast-radius
   checks are represented:**
   - *Option 3A: Constrained schema properties, named variants, and
     slots on the element; instance overrides only in the page file;
     automated back-link index.* Each shared element Markdown file
     declares its allowed `variants`, configurable `properties`
     (text/boolean/swap), and child `slots` (mirroring Figma component
     properties and Shopify `{% schema %}`) [7, 8, 11]. A page Markdown
     file instantiates the element by ID, selects a variant, and passes
     only declared property values or slot children—never ad-hoc
     structural overrides. If a page needs an undeclared structural
     change, the author must either add a variant/property to the shared
     element or explicitly fork ("detach") it into a new element [10].
     A lightweight script or agent index (analogous to `react-scanner`)
     scans all page Markdown files to maintain a `Used on pages` list
     (including which variants/properties each page uses) and surfaces
     affected pages whenever a shared element changes [13].
     - *Trade-off:* Prevents "override chaos" and gives instant blast-
       radius visibility in git diffs, while requiring upfront schema
       discipline in element definitions.
   - *Option 3B: Free-form prose overrides in page files.* Let page
     Markdown files describe arbitrary prose exceptions ("same as
     `search-bar.md`, except move the clear button outside the input").
     - *Trade-off:* Fast to write for a single screen, but makes it
       impossible to validate whether a change to the shared element
       breaks the page's local exception, reproducing the detached-
       instance maintenance trap [9, 10].

4. **How shared element and page definitions are versioned:**
   - *Option 4A: Repository-wide (monolithic) git versioning with
     breaking-change annotations in change proposals.* Keep all element
     and page definitions at the repository's git commit/tag version,
     using structured change records (like Changesets or OpenSpec
     `MODIFIED`/`REMOVED` markers) to flag when an element edit changes
     its required properties or slots and therefore requires updating
     consumer page files in the same commit [4, 14].
     - *Trade-off:* Avoids cross-file version-matrix complexity within a
       single application repository, while still forcing breaking
       element changes to update every affected page in lockstep.
   - *Option 4B: Independent per-element semantic version numbers.* Each
     element Markdown file carries `version: X.Y.Z`, and page files pin
     `element: search-bar@1.2.0` [14].
     - *Trade-off:* Useful only when shared element definitions are
       published across multiple independent product repositories; inside
       one application, allowing different screens to pin different major
       versions of the same UI element fragments the user experience.

## Relevance to this project

*Inference from the findings applied to `forge`:* The idea tested by the
research bundle—giving every shared screen element its own small
Markdown definition and composing page definitions that name and place
those elements—is viable after the first build **only if** `forge`
adopts three structural guardrails drawn from Figma, Shopify Online
Store 2.0, OpenSpec, and AST scanners:

1. **Separate element schema from page instance data (Option 3A):** An
   element definition in `forge` should explicitly declare its allowed
   **variants** (e.g., `size: compact | full`), **properties** (text
   labels, boolean toggles, icon/component swaps), and **slots** (named
   regions where a page can inject child elements) [7, 8, 11]. A page
   definition should reference the element by ID and supply only variant
   selections, property values, and slot contents—just as Shopify's
   `templates/*.json` configures `sections/*.liquid` [11]. Free-form
   prose overrides inside a page file ("use `search-field`, but change
   its internal layout") should be disallowed; if a screen genuinely
   requires a new structure, the agent should prompt the human either to
   promote a new variant/property onto the shared element or to detach
   it as a distinct element definition [8, 10].
2. **Generate or maintain a reverse-reference index ("Used by pages") so
   every element change shows its blast radius (F5, Option 3A):**
   Because a page names the elements it holds, the raw dependency arrow
   points from page to element. When an author or agent edits an element
   definition, the agent (or a pre-commit check) should scan all page
   definitions—just as `react-scanner` scans component imports [13]—to
   list every page and variant combination touched by the change, and
   either keep a generated `used_by` block in the element file or
   require the change proposal to list and reconcile affected pages.
3. **Use spec-anchored delta reviews and a post-build convergence step
   (Options 1B, 2A, 4A):** Rather than assuming the first build matches
   the initial Markdown verbatim, `forge` should treat the UX/UI
   description as *spec-anchored* [1, 2]. When a feature or screen
   changes after the first build, staging the change with explicit
   `ADDED` / `MODIFIED` / `REMOVED` sections (or a structured diff
   summary like OpenSpec [4]) lets the human judge both the local
   screen change and any ripple across shared elements. After the build
   stage finishes, a dedicated reconciliation step (analogous to
   `/opsx:verify` or `/speckit.analyze` [4, 5]) should compare the
   implemented UI components and routes against the element and page
   Markdown files and commit back any build-time adjustments before the
   cycle closes. Within a single product repository, monolithic git
   versioning with lockstep page updates (Option 4A) should be chosen
   against per-element semantic version pinning (Option 4B) so a product
   never specifies two incompatible versions of the same element across
   different screens.

**Consult when:**
- Designing the schema of element Markdown files (specifically how
  variants, configurable properties, slots, and overrides are written).
- Designing how page Markdown files instantiate shared elements and how
  an agent computes which pages are affected when an element definition
  changes.
- Designing the post-build workflow step that brings implementation
  changes back into the UX/UI Markdown documents and prepares the next
  change cycle.

## Sources

1. **Understanding Spec-Driven-Development: Kiro, spec-kit, and Tessl**
   — Birgitta Böckeler (*martinfowler.com*), 2025-10-15 (byline),
   `https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html`;
   kind: secondary (practitioner analysis and tool audit, read via
   summarised fetch [tertiary retrieval]); how read: summarised fetch
   (including verbatim quotes from the taxonomy section defining
   *Spec-first*, *Spec-anchored*, and *Spec-as-source*); original.
2. **Spec-Driven Development: From Code to Contract in the Age of AI
   Coding Assistants** — Deepak Babu R Piskala (*arXiv*,
   arXiv:2602.00180), 2026-01-30 (byline / arXiv v1 submission date),
   `https://arxiv.org/abs/2602.00180`; kind: primary (preprint, read via
   summarised fetch [tertiary retrieval]); how read: summarised fetch
   (including verbatim quotes from the abstract and spec-anchored
   section); original.
3. **The Spec Growth Engine: Spec-Anchored, Code-Coupled,
   Drift-Enforced Architecture for AI-Assisted Software Development** —
   Hartwig Grabowski (*arXiv*, arXiv:2606.27045), 2026 (byline / arXiv
   year), `https://arxiv.org/abs/2606.27045`; kind: primary (preprint,
   read via summarised fetch [tertiary retrieval]); how read: summarised
   fetch; original.
4. **OpenSpec (`Fission-AI/OpenSpec`)** — Fission-AI (*GitHub*), undated
   (repository README and workflow documentation, accessed 2026-11-21),
   `https://github.com/Fission-AI/OpenSpec`; kind: primary (repository
   artefact and tool documentation, read via summarised fetch [tertiary
   retrieval]); how read: summarised fetch (covering `openspec/specs/`,
   `openspec/changes/<name>/`, delta spec headings `ADDED`/`MODIFIED`/
   `REMOVED`/`RENAMED`, and `/opsx:verify`, `/opsx:sync`,
   `/opsx:archive`); original.
5. **Spec Kit (`github/spec-kit`)** — GitHub (*GitHub*), undated
   (repository README and command documentation, accessed 2026-11-21),
   `https://github.com/github/spec-kit`; kind: primary (repository
   artefact and tool documentation, read via summarised fetch [tertiary
   retrieval]); how read: summarised fetch (covering `specify`, `plan`,
   `tasks`, `implement`, `/speckit.analyze`, and convergence workflows);
   original.
6. **Kiro Documentation: Specs and Steering (`.kiro/specs/`,
   `.kiro/steering/`)** — Amazon Web Services / Kiro (*kiro.dev* /
   *aws.com*), undated (vendor documentation, accessed 2026-11-21),
   `https://kiro.dev`; kind: primary (vendor documentation of its own
   product, read via summarised fetch [tertiary retrieval]); how read:
   summarised fetch (covering `requirements.md`, `bugfix.md`,
   `design.md`, `tasks.md`, `.kiro/steering/`, task scanning, and
   code-to-spec sync); original.
7. **Create and use variants** — Figma (*Figma Help Center*), undated
   (vendor documentation, accessed 2026-11-21),
   `https://help.figma.com/hc/en-us/articles/360056447834-Create-and-use-variants`;
   kind: primary (vendor documentation of its own product, read via
   summarised fetch [tertiary retrieval]); how read: summarised fetch;
   original.
8. **Explore component properties** — Figma (*Figma Help Center*),
   undated (vendor documentation, accessed 2026-11-21),
   `https://help.figma.com/hc/en-us/articles/4404855722135-Explore-component-properties`;
   kind: primary (vendor documentation of its own product, read via
   summarised fetch [tertiary retrieval]); how read: summarised fetch
   (covering text, boolean, instance swap, variant, and slot
   properties); original.
9. **Apply overrides to instances** — Figma (*Figma Help Center*),
   undated (vendor documentation, accessed 2026-11-21),
   `https://help.figma.com/hc/en-us/articles/360039150733-Apply-overrides-to-instances`;
   kind: primary (vendor documentation of its own product, read via
   summarised fetch [tertiary retrieval]); how read: summarised fetch
   (covering supported overrides, update propagation from main
   components, and resetting overrides); original.
10. **Detach an instance from the component** — Figma (*Figma Help
    Center*), undated (vendor documentation, accessed 2026-11-21),
    `https://help.figma.com/hc/en-us/articles/360038665754-Detach-an-instance-from-the-component`;
    kind: primary (vendor documentation of its own product, read via
    summarised fetch [tertiary retrieval]); how read: summarised fetch;
    original.
11. **JSON templates (`templates/*.json`) and Theme Architecture** —
    Shopify (*Shopify Developer Documentation*), undated (vendor
    documentation, accessed 2026-11-21),
    `https://shopify.dev/docs/storefronts/themes/architecture/templates/json-templates`;
    kind: primary (vendor documentation of its own product, read via
    summarised fetch [tertiary retrieval]); how read: summarised fetch
    (covering `sections/*.liquid`, `blocks`, `{% schema %}`, `settings`,
    `presets`, and `templates/*.json` `sections` and `order` keys);
    original.
12. **Figma Code Connect (`figma/code-connect`)** — Figma (*GitHub*),
    undated (repository documentation, accessed 2026-11-21),
    `https://github.com/figma/code-connect`; kind: primary (repository
    artefact and vendor documentation, read via summarised fetch
    [tertiary retrieval]); how read: summarised fetch; original.
13. **react-scanner (`moroshko/react-scanner`)** — Misha Moroshko et al.
    (*GitHub*), undated (repository documentation, accessed 2026-11-21),
    `https://github.com/moroshko/react-scanner`; kind: primary
    (repository artefact, read via summarised fetch [tertiary
    retrieval]); how read: summarised fetch; original.
14. **Changesets (`changesets/changesets`)** — Atlassian / Changesets
    contributors (*GitHub*), undated (repository documentation, accessed
    2026-11-21), `https://github.com/changesets/changesets`; kind:
    primary (repository artefact, read via summarised fetch [tertiary
    retrieval]); how read: summarised fetch; original.

## Opened and not used

- `https://supernova.io` (grounding result on design system component
  versioning and Code Connect) — vendor blog commentary on its own
  market; superseded by primary documentation [7, 12, 13, 14].
- `https://uxpin.com` (grounding result on Figma instance overrides and
  design system governance) — vendor blog commentary on a competitor's
  product; superseded by Figma Help Center primaries [7, 8, 9, 10].
- `https://sparkfabrik.com` (grounding result summarizing OpenSpec CLI
  commands) — secondary write-up; superseded by `Fission-AI/OpenSpec`
  primary repository documentation [4].
- `https://augmentcode.com` (grounding result on spec-driven development
  and spec drift) — vendor blog commentary on its own market; superseded
  by [1, 2, 5].
- `https://htmltoliquidconverter.com` and
  `https://vihadigitalcommerce.com` (grounding results on Shopify Online
  Store 2.0 sections and JSON templates) — third-party summaries;
  superseded by Shopify's official developer documentation [11].

## Search record

**Queries run (in order):**
1. `"spec-driven development" "spec-anchored" "spec-as-source"`
2. `"spec-kit" OR "OpenSpec" update specification after build sync code changes`
3. `design system component versioning breaking changes variants usage tracking`
4. `Figma components instances overrides detach properties documentation`
5. `"keeping specification in sync with code fails"` *(disconfirming
   query 1)*
6. `"design system overrides chaos"` *(disconfirming query 2)*
7. `Shopify theme architecture sections blocks schema overrides presets json`
8. `"Code Connect" Figma OR "react-scanner" component usage across pages blast radius`
9. `Kiro steering files specs sync code changes "spec-driven" documentation`
10. `domain:martinfowler.com "Spec-Driven Development" Birgitta Böckeler Kiro spec-kit Tessl exact URL date verbatim quotes "spec-first" "spec-anchored" "spec-as-source"`
11. `domain:github.com "Fission-AI/OpenSpec" README workflow delta specs ADDED MODIFIED REMOVED verify archive sync exact URL verbatim quotes`
12. `domain:github.com "github/spec-kit" README specify plan tasks implement analyze constitution exact URL verbatim quotes`
13. `domain:kiro.dev Kiro documentation specs requirements.md design.md tasks.md steering update spec from code exact URL verbatim quotes`
14. `domain:help.figma.com "Create and use variants" OR "Component properties" OR "Apply overrides to instances" detach instance exact URL verbatim quotes`
15. `domain:shopify.dev "sections" "blocks" "JSON templates" theme architecture schema settings presets exact URL verbatim quotes`
16. `domain:martinfowler.com "Understanding Spec-Driven-Development: Kiro, spec-kit, and Tessl" publication date exact verbatim quotes "spec-first" "spec-anchored" "spec-as-source"`
17. `domain:arxiv.org "spec-driven development" OR "specification drift" "spec-anchored" "spec-as-source" exact arxiv URL title authors date verbatim quote`
18. `domain:shopify.dev "JSON templates" "sections" exact URL "shopify.dev/docs/storefronts/themes/architecture" verbatim quote`
19. `domain:github.com "figma/code-connect" OR "changesets/changesets" OR "moroshko/react-scanner" exact github URL README verbatim quote`

**Pages opened (budget count):**
Direct HTTP fetches via `curl.exe` were blocked by the workspace
sandbox deny rule; consequently, 14 sources (`[1]`–`[14]`, comprising 13
primaries and 1 practitioner audit on `martinfowler.com`) were opened
via targeted `search_web` summarised fetches (queries 10–19 above,
within the 10–15 primary source budget).

**What the disconfirming queries found:**
- Query 5 (`"keeping specification in sync with code fails"`) confirmed
  the expected baseline: specifications routinely rot after the first
  build because of the double-entry maintenance tax, exploratory build
  changes that bypass upfront specs, and the absence of automated
  compilation or test gates for prose/Markdown specifications [2, 3].
  Even in AI spec-driven kits, bringing code changes back into the spec
  requires manually invoking verification/sync commands (`/opsx:verify`,
  `/speckit.analyze`, or prompting Kiro) or editing the spec by hand [4,
  5, 6].
- Query 6 (`"design system overrides chaos"`) found both meanings of the
  phrase: while design systems aim to replace UI inconsistency ("chaos")
  with shared tokens and components, poorly governed overrides or overly
  rigid components cause authors to detach instances or stack local
  overrides, re-introducing inconsistency and breaking update
  propagation from the shared definition [7, 9, 10].

**Reason the run ended:**
Both parts of the card's stop rule and the opening budget were met:
every route in "Where to look" (spec-driven kits, design tools on
components/instances/overrides, block/section systems on variations, and
design systems on versioning and blast radius) was backed by primary
sources (`[2]`–`[14]`), differently worded queries ceased returning new
mechanisms, and 14 sources were opened via targeted summarised fetch
(within the 10–15 target).
