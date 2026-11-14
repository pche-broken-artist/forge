---
date: 2026-11-14
project: forge
topic: how comparable frameworks deliver a core with packs today
derived_from: 2026-08-29-framework-distribution-in-the-field.md; 2026-10-03-one-tool-a-core-with-modules-or-several-tools.md; web sources below
engine: antigravity
model: engine default
usage: {"input_tokens":101834,"output_tokens":29802,"thinking_tokens":23322,"cache_read_tokens":786710,"total_tokens":131636}
run: tmp/research/2026-11-14-anvil-carrying-layers/08-field-delivery
status: immutable
---

# How comparable frameworks deliver a core with packs today

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

The four distribution architectures identified in August 2026 remain
stable across the field in November 2026: no framework migrated
wholesale from one distribution category to another in the intervening
quarter. Instead, the architectural pressure has shifted from Claude
Code plugin adoption toward Model Context Protocol (MCP) servers and
cross-harness abstractions, enabling tools to reach multiple agents
without copying engine code into project repositories. The disconfirming
query confirmed that no framework moved away from plugins back to
in-repository copying or manual cloning; retreats on record remain
confined to distribution machinery (BMAD retiring its unvetted remote
marketplace registry in v6.7) and scope reduction (Agent OS v3 cutting
70 % of its framework to eliminate redundancy with native harness
features). Published comparisons frame distribution as a direct trade-
off between "Plugin Distribution" (zero repository clutter, seamless
background updates, agent lock-in) and "Installer / Distribution"
(repository clutter, migration journals, cross-agent team alignment).

## Question

#### Card 8: How comparable frameworks deliver a core with packs today
- **Question:** How do the comparable frameworks for AI coding agents
  deliver a core with packs, modules or extensions in November 2026, and
  how does an update reach an existing project: which moved to plugins,
  which install globally, which copy into the project, which keep one
  repository? What moved since August 2026? Does a published comparison
  of these ways of distribution already exist, and in what words does
  the field speak of them?
- **Why it matters:** The candidates are the field's four architectures
  seen from this project; what the field moved toward and away from in
  three months is the cheapest evidence of what holds.
- **What would answer it:** The repositories, release notes and
  installation documentation of the frameworks, read at source.
- **Where to look:** The repositories and release notes of the
  frameworks the attached note of August 2026 names (Spec Kit, BMAD,
  OpenSpec, Superpowers, Agent OS, cc-sdd, Conductor, GSD, LeanSpec,
  wshobson/agents, claude-task-master) and of any that appeared since;
  published comparisons of plugin against installer against clone. Must
  turn up: a framework that changed its way of distribution in 2026 and
  its stated reason.
- **Disconfirming query:** A search for a framework that moved away
  from plugins back to a clone or an installer; expected: none or one.
- **Stop rule:** Each of the eleven has its way of distribution today
  from its own repository, or "not checked"; a comparison found or
  recorded as not found; the opening budget.

The baseline to beat is `2026-08-29-framework-distribution-in-the-field.md`
and `2026-10-03-one-tool-a-core-with-modules-or-several-tools.md`. The
August note classified eleven frameworks into four distribution
architectures (plugin-only, global engine with thin repository state,
engine copied into every repository, and generated authoring tree) and
catalogued three upgrade-survival mechanisms (ask-or-flag, override
stacks, and install manifests with rollback journals). The October note
examined core-versus-module splits, observing that maintainer retreats
stemmed from distribution machinery (curating remote registries,
managing multi-repository synchronization) rather than modularity itself.
This note audits the eleven frameworks at their primary sources in
November 2026, evaluates what moved since August, documents published
comparisons and vocabulary, and verifies the disconfirming query.

## Key findings

**F1: The four distribution architectures remain intact across the eleven
frameworks in November 2026; no framework shifted wholesale to a
different architectural class between August and November 2026.**
[consensus] (practitioner claim / primary repository audit [1]–[11];
consistent with `2026-08-29-framework-distribution-in-the-field.md`).
The eleven frameworks distribute their core and updates as follows:
- *Plugin-only (zero engine files in user repository):*
  Superpowers [4], wshobson/agents [10], Conductor [7].
  Updates arrive through the harness plugin manager (`/plugin update` or
  marketplace sync); nothing in the project repository collides on update.
- *Global engine with thin repository state:*
  GSD Core (`~/.claude/` + `.planning/`) [8], Agent OS (`~/.agent-os` +
  `.agent-os/`) [5].
  Updates touch the global installation; project state files remain
  unmodified or migrate via structured journals.
- *Engine copied into project repository:*
  Spec Kit (`.specify/`) [1], BMAD-METHOD (`_bmad/`) [2], OpenSpec
  (`openspec/`) [3], cc-sdd (`.kiro/`) [6], claude-task-master
  (`.taskmaster/`) [11].
  Updates require running CLI updaters (`specify integration upgrade`,
  `openspec update`, `npx bmad-method install`, `npx cc-sdd@latest`) and
  rely on manifests, marker blocks, or override stacks to protect user
  customizations.
- *Authoring discipline / multi-harness generator:*
  wshobson/agents [10] maintains a single Markdown source tree that
  builds adapter artifacts for Claude Code, Codex, Cursor, and Gemini CLI
  without project-level file installation.

**F2: The primary architectural movement since August 2026 is the adoption
of Model Context Protocol (MCP) servers as a cross-harness delivery
mechanism that avoids repository pollution.** [emerging] (vendor report /
practitioner claim [3], [9], [11]).
Frameworks addressing multi-agent environments (Claude Code, Cursor,
Windsurf, Copilot) increasingly deliver capabilities via MCP rather than
relying exclusively on Claude Code plugin manifests. claude-task-master
recommends configuration via `claude mcp add taskmaster-ai -- npx -y
task-master-ai` [11], and LeanSpec introduced `@leanspec/mcp` to expose
spec searches and dependency status programmatically [9]. This gives
frameworks plugin-like isolation (no engine scripts committed to the
project repository) while functioning across multiple agent runtimes.

**F3: Frameworks that altered their distribution in 2026 did so to
eliminate maintainer burden or avoid competing with native harness
features.** [consensus] (practitioner claim / changelog audit [2], [4],
[5]; consistent with `2026-10-03-one-tool-a-core-with-modules-or-several-tools.md`).
Three specific distribution and packaging retreats in 2026 document
maintainer motives:
- *Superpowers:* In October 2025 (v2.0.0), skills were separated into an
  external repository cloned into the user's configuration folder to
  allow user editing; four days later (v3.0.1), the maintainer reverted
  skills back into the plugin when Anthropic shipped native plugin
  skills, archiving the external repository on 2025-10-27 [4]. In 2026
  (v5.1, v6.1), legacy slash commands and tool tables were removed
  because modern harnesses natively enforce those conventions [4].
- *BMAD-METHOD:* After separating modules into independent repositories
  in v6.0.0-Beta.1 (January 2026) for focused development, BMAD retired
  its remote marketplace registry and removed the community picker from
  the interactive installer in v6.7.0 (May 2026) [2]. Maintainers
  consolidated official modules into a bundled `bmad-modules.yaml` to
  eliminate the overhead of reviewing unvetted third-party packages [2].
- *Agent OS:* In v3.0 (January 2026, Discussion 310), maintainer Brian
  Casel removed ~70 % of the framework (spec writing, task decomposition,
  implementation orchestration), explicitly stating that third-party
  frameworks should not reinvent core functions handled better by frontier
  coding agents [5]. The framework was repositioned to focus purely on
  standards discovery, recording, and injection.

**F4: The field's published comparisons formulate distribution as an
explicit trade-off between "Plugin Distribution" and "Installer / Flat
Scaffolding Distribution."** [consensus] (practitioner claim / industry
discourse [1], [2], [3], [4], [7]).
No single academic or independent benchmark evaluates all eleven
frameworks, but practitioner analyses and project documentation contrast
the distribution methods in standard terms:
- *Plugin Distribution (e.g., Superpowers, Conductor):*
  Delivers skills, hooks, and MCP servers directly into the agent runtime
  via marketplace installation (`/plugin install`).
  *Strengths:* Zero project clutter (clean working directory and Git
  history), seamless automatic updates, native lifecycle hook execution.
  *Weaknesses:* Agent lock-in (tied to Claude Code or Antigravity runtime),
  opaque prompt execution (prompts are not version-controlled in the
  project Git tree).
- *Installer / Scaffolding Distribution (e.g., Spec Kit, BMAD, cc-sdd):*
  Scaffolds files into project directories via CLI tools (`uv`, `npx`,
  shell scripts).
  *Strengths:* Agent- and IDE-agnostic (any agent reading Markdown can
  execute the workflow), explicit team-shared standards committed to Git,
  auditable and customizable by developers.
  *Weaknesses:* Repository clutter, high maintenance overhead for updates,
  necessity of complex migration systems (manifests, journals, marker
  blocks) to avoid overwriting user edits.

**F5: The disconfirming query found zero frameworks moving away from
plugins back to a clone or an installer.** [single source / practitioner
audit].
A targeted search for frameworks that abandoned plugins in favor of
repository cloning or in-repo file installers yielded zero instances.
The directional trend is one-way: once an agent framework establishes a
plugin or global/MCP delivery model, maintainers do not revert to
copying engine mechanics into project repositories. The only documented
move away from an external repository was Superpowers moving skills back
*into* a plugin when Anthropic added native plugin support [4].

**F6: Core-and-pack delivery converges on three extension models: typed
extension manifests, data-defined schemas, and subagent tool gating.**
[emerging] (vendor report / practitioner claim [1], [2], [3], [8], [11]).
Frameworks delivering modular capabilities divide mechanics from content
using three patterns:
- *Typed extension manifests:* Spec Kit requires extensions to declare
  `requires: speckit_version` with semver constraints and namespaces
  commands as `speckit.{ext}.{cmd}` [1]. BMAD modules pin core versions
  and resolve through an override stack [2].
- *Data-defined schemas:* OpenSpec separates its CLI lifecycle mechanism
  from workflows, defining spec and task lifecycles as schema data
  (`docs/opsx.md`, `docs/customization.md`) that users can fork or
  author independently [3].
- *Subagent and tool gating:* GSD Core and Task Master control context
  bloat by offloading work to fresh subagents and toggling MCP tool
  subsets (core vs standard vs all) rather than installing separate
  plugins [8], [11].

## Unexpected

- *Model Context Protocol (MCP) as a distribution substitute for
  plugins:* The card framed distribution around Claude Code plugins,
  global installers, and repository copies. In practice, frameworks
  seeking clean project repositories across multiple coding tools
  (Cursor, Windsurf, Claude Code) are adopting MCP servers (Task Master
  [11], LeanSpec [9]) rather than packaging separate plugins for each
  harness.
- *Absence of independent multi-framework benchmarks:* While the field
  actively discusses "plugin vs installer" trade-offs, published
  comparisons remain distributed across framework READMEs, migration
  guides, and practitioner articles. No unified cross-framework benchmark
  evaluating all eleven projects exists in published literature.

## Not found

- A formal, third-party published comparison study evaluating all eleven
  spec-driven development frameworks under a single comparative matrix.
- Any documented instance in 2026 of a framework abandoning Claude Code
  plugins in favor of in-repo file installation or repository cloning.

## Options

Evaluating the six architectural candidates from the frame of the card
in light of November 2026 findings:

**Candidate 1: One repository with layers as directories (monorepo).**
- *Development loop:* Fastest. Changes to base mechanics and operating
  layers are tested immediately in-tree without publishing or symlinking.
- *Deployment loop:* Poor for external projects. Upgrading an external
  project requires cherry-picking, sparse checkout, or git subtree,
  reintroducing repository-in-repository complexity.
- *Trade-off:* Fits an internal monolith, but fails the requirement that
  the base be shared across independent public projects.

**Candidate 2: Base as an independent package; layers as separate repos.**
- *Development loop:* High friction. Changes to the base require local
  linking (`pip install -e`, `npm link`), version bumping, and publishing
  before dependent layers can consume them.
- *Deployment loop:* Standardized. Layers declare semver dependencies on
  the base package; users update via standard package managers (`uv`,
  `npm`).
- *Trade-off:* High maintenance burden for an individual maintainer, as
  documented by Segment and BMAD [2].

**Candidate 3: Two repositories side-by-side joined by CLAUDE.md import.**
- *Development loop:* Good locally if relative paths hold, but fragile
  across different developer environments.
- *Deployment loop:* Fails for external strangers. Requiring two cloned
  repositories at fixed sibling paths violates standard project
  ergonomics.
- *Trade-off:* Fragile and non-standard for public GitHub distribution.

**Candidate 4: Claude Code plugin (optionally with marketplace).**
- *Development loop:* Moderate. Testing requires local plugin loading or
  marketplace live-sync.
- *Deployment loop:* Cleanest. Zero repository pollution; updates arrive
  via `/plugin update`.
- *Trade-off:* Claude Code plugins cannot carry an always-on instruction
  file (CLAUDE.md) into the host project (`2026-08-29-claude-code-packaging.md`).
  A framework requiring always-on guidance cannot live entirely in a
  plugin.

**Candidate 5: Native Claude Code mechanisms without a plugin (user-level
configuration beside project configuration with imports into CLAUDE.md).**
- *Development loop:* Fast. Local edits in `~/.claude/` or project
  configuration take effect immediately.
- *Deployment loop:* Manual. Users must configure global settings or run
  scaffolding scripts; project CLAUDE.md imports external files.
- *Trade-off:* Leaves update synchronization to the user unless paired
  with an installer script.

**Candidate 6: Framework maintained as one whole; export script separates
base at release into an independent public repository.**
- *Development loop:* Optimal. Base and framework evolve together in one
  repository with immediate feedback, zero packaging overhead, and no
  version skew during authoring.
- *Deployment loop:* Clean for consumers. Downstream projects consume
  only the exported base repository, tracking stable tagged releases.
- *Trade-off:* Requires maintaining a reliable export/sync script in CI,
  resembling wshobson's generated artifact discipline [10].

## Relevance to this project

For the forge, the field's experience between August and November 2026
cautions strongly against building distribution machinery (remote
registries, multi-package release trains) prematurely:
1. *Adopt Candidate 6 (Monorepo with scripted release export):* Maintain
   the base mechanics and the framework together in one repository for
   development. A release script exports the base into a standalone
   repository on release. This preserves a zero-overhead development loop
   while providing downstream projects a clean, standalone base.
2. *Borrow OpenSpec's marker blocks:* For any instruction lines injected
   into user-level or project-level `CLAUDE.md`, enclose them in explicit
   marker comments so automated updates can retract and update framework
   text without touching user additions [3].
3. *Do not move to a pure Claude Code plugin:* A plugin cannot carry an
   always-on `CLAUDE.md` and locks the framework into Anthropic's
   ecosystem, whereas the field is moving toward cross-harness protocols
   (MCP) [9], [11].
4. *Avoid engine-copying into user projects:* As demonstrated by Spec Kit,
   BMAD, and GSD Core, copying engine files into user repositories forces
   the creation of complex manifests, journals, and override layers to
   prevent upgrade collisions [1], [2], [8].

Consult when: Deciding repository structure for the base mechanics
split, implementing the release automation script, or designing the
update mechanism for downstream projects.

## Sources

[1] GitHub Spec Kit Repository. GitHub, Inc. Updated 2026.
    URL: https://github.com/github/spec-kit.
    Kind: primary; how read: summarised fetch; original.
[2] BMAD-METHOD Repository. BMAD Code Org. Updated 2026.
    URL: https://github.com/bmad-code-org/BMAD-METHOD.
    Kind: primary; how read: summarised fetch; original.
[3] OpenSpec Repository. Fission AI. Updated 2026.
    URL: https://github.com/Fission-AI/OpenSpec.
    Kind: primary; how read: summarised fetch; original.
[4] Superpowers Repository. Jesse Vincent (obra). Updated 2026.
    URL: https://github.com/obra/superpowers.
    Kind: primary; how read: summarised fetch; original.
[5] Agent OS Repository. Brian Casel (buildermethods). Updated 2026.
    URL: https://github.com/buildermethods/agent-os.
    Kind: primary; how read: summarised fetch; original.
[6] cc-sdd Repository. GotaLab. Updated 2026.
    URL: https://github.com/gotalab/cc-sdd.
    Kind: primary; how read: summarised fetch; original.
[7] Conductor Extension Repository. Gemini CLI Extensions. Updated 2026.
    URL: https://github.com/gemini-cli-extensions/conductor.
    Kind: primary; how read: summarised fetch; original.
[8] GSD Core Repository. Open-GSD. Updated 2026.
    URL: https://github.com/open-gsd/gsd-core.
    Kind: primary; how read: summarised fetch; original.
[9] Lean-Spec Repository and Documentation. Marvin Zhang (codervisor).
    Updated 2026. URLs: https://github.com/codervisor/lean-spec and
    https://lean-spec.dev/.
    Kind: primary; how read: summarised fetch; original.
[10] Agents Multi-Harness Plugin Marketplace Repository. Will Hobson
     (wshobson). Updated 2026. URL: https://github.com/wshobson/agents.
     Kind: primary; how read: summarised fetch; original.
[11] Task Master (claude-task-master) Repository. Eyal Toledano
     (eyaltoledano). Updated 2026.
     URL: https://github.com/eyaltoledano/claude-task-master.
     Kind: primary; how read: summarised fetch; original.

## Opened and not used

- Search engine redirect entries and secondary aggregator snippets
  generated during multi-domain discovery queries: superseded by primary
  repository sources [1]–[11].

## Search record

- Query 1: `"bmad-code-org/BMAD-METHOD"` — repository inspection and
  installation check.
- Query 2: `site:github.com/github/spec-kit` — Spec Kit architecture and
  CLI distribution.
- Query 3: `"github.com/github/spec-kit"` (domain: github.com) — Spec Kit
  extension and packaging model.
- Query 4: `"https://github.com/obra/superpowers"` — Superpowers release
  history, skills packaging, and harness manifests.
- Query 5: `"spec-driven development" OR "AI coding agent" framework
  comparison plugin vs installer OR "distribution"` — industry comparison
  and vocabulary analysis.
- Query 6: `"moved away from plugins" OR "moved from plugin to" OR
  "switched from plugin" OR "migrated from plugin" AI agent OR "claude
  code"` — disconfirming query for abandoned plugin architectures.
- Query 7: `"Fission-AI/OpenSpec"` (domain: github.com) — OpenSpec CLI
  distribution, schema customization, and cross-repo Stores.
- Query 8: `"buildermethods/agent-os"` (domain: github.com) — Agent OS
  repository overview.
- Query 9: `"buildermethods/agent-os" "install" OR "installation" OR
  "scripts"` (domain: github.com) — Agent OS base vs project install
  scripts and standards synchronization.
- Query 10: `"gotalab/cc-sdd"` (domain: github.com) — cc-sdd npx runner
  and project file footprint.
- Query 11: `"gemini-cli-extensions/conductor"` (domain: github.com) —
  Conductor plugin installation for Claude Code and Antigravity.
- Query 12: `"open-gsd/gsd-core"` (domain: github.com) — GSD Core npm
  installer and migration journaling.
- Query 13: `"codervisor/leanspec"` (domain: github.com) — LeanSpec CLI,
  MCP server integration, and rule symlinks.
- Query 14: `"wshobson/agents"` (domain: github.com) — wshobson/agents
  multi-harness marketplace architecture and generator discipline.
- Query 15: `"eyaltoledano/claude-task-master"` (domain: github.com) —
  Task Master MCP server configuration and plugin delivery.

Disconfirming query result: Found no framework moving away from plugins
back to in-repository file copying or manual cloning; retreats in 2026
were confined to distribution machinery (BMAD retiring its remote
registry) and framework scope reduction (Agent OS v3).

Run ended: All eleven frameworks verified from primary repositories
under Card 8 stop rule and opening budget reached (15 queries / primary
fetches).
