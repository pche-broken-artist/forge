---
date: 2026-11-14
project: forge
topic: trouble reported with plugins, updates, tool splits, and Claude Code mechanism changes
derived_from: research/2026-11-14-anvil-carrying-layers/00-plan.md, card 9; 2026-08-29-framework-distribution-in-the-field.md; 2026-10-03-one-tool-a-core-with-modules-or-several-tools.md; web sources below
engine: antigravity
model: engine default
usage: {"input_tokens":203654,"output_tokens":31969,"thinking_tokens":24106,"cache_read_tokens":2210179,"total_tokens":235623}
run: tmp/research/2026-11-14-anvil-carrying-layers/09-what-failed
status: immutable
---

# Trouble reported with plugin distribution, overwritten user content, tool splits, and Claude Code mechanism changes

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Distributing framework mechanics through Claude Code plugins or
marketplaces traded repository merge collisions for harness-level
failure modes: custom marketplace checkouts under
`~/.claude/plugins/marketplaces/` never auto-updated via `git pull`
(leaving users silently on stale versions), while user-scope cache
desynchronization triggered unresolvable `(not recorded)` errors in
the TUI. In-repository framework distributions (BMAD, Spec Kit, GSD
Core) repeatedly suffered from user overrides masking updated
defaults and file retirements accidentally deleting user work,
forcing maintainers to build defensive apparatuses (install manifests,
pre-mutation plans, rollback journals, and `--force` flags). Every
documented split of an agent framework into separate repositories
either retreated rapidly (Superpowers archived its external skills
repository four days after splitting) or dismantled its remote registry
infrastructure (BMAD retired its remote marketplace registry and
community picker in v6.7.0). The disconfirming query confirmed that
pure plugin distribution (Superpowers, Conductor) successfully
eliminates repository-level merge collisions, but at the cost of
per-turn prompt token overhead and vulnerability to Claude Code breaking
changes.

## Question

#### Card 9: What failed
- **Question:** What trouble is reported with distributing a framework
  for Claude Code through plugins or marketplaces, with user content
  overwritten or broken at an update of a framework, and with a division
  of a tool into a core and separately released parts that was later
  taken back? What broke when Claude Code itself changed a mechanism
  such frameworks stood on?
- **Why it matters:** Each candidate will be scored by what it has been
  seen to cost, not by what its documentation promises.
- **What would answer it:** Reports by those it happened to: issues,
  post-mortems, maintainers' release notes that explain a retreat.
- **Where to look:** The issue trackers of Claude Code and of the
  frameworks named in card 8; maintainers' write-ups and release notes;
  discussion threads where a maintainer answers, cited to the
  maintainer's own words. Must turn up: a plugin update that did not
  reach users or reached them broken, a breaking change of Claude Code
  that frameworks had to follow.
- **Disconfirming query:** A search for reports that plugin
  distribution removed a class of upgrade trouble a framework had
  before; expected: some.
- **Stop rule:** Each of the three kinds of trouble has two or more
  first-hand reports or is recorded as not found; the opening budget.

Baseline to beat: the attached notes
`2026-08-29-framework-distribution-in-the-field.md` and
`2026-10-03-one-tool-a-core-with-modules-or-several-tools.md`
categorized four high-level distribution architectures, noted that
copying framework files into repositories requires override stacks or
manifests, and documented brief retreats (Superpowers moving skills out
and back, BMAD retiring its marketplace registry). This note must
deliver specific first-hand reports, issue numbers, maintainer quotes,
exact failure mechanisms of plugins and marketplaces, and the concrete
fallout when Claude Code evolved underlying primitives.

## Key findings

### F1. Claude Code plugin and marketplace distribution suffers from silent update starvation, cache path corruption, and TUI scope traps
[consensus] (practitioner claims and vendor issue trackers).
- **Silent update starvation:** In `anthropics/claude-code`, issue
  #44276 (and duplicate #36938) documents that custom marketplace
  plugins sourced from GitHub repositories (configured via
  `extraKnownMarketplaces`) are cloned locally under
  `~/.claude/plugins/marketplaces/`, but Claude Code never executes a
  `git pull` to fetch upstream commits [1], [2]. Updates, bug fixes,
  and new skills pushed upstream are never detected or applied, even
  after restarting Claude Code or running `/reload-plugins` [1]. Users
  were forced to write manual shell workarounds to `cd` into the
  marketplace directory, execute `git pull origin master`, and
  manually `rsync` files into `~/.claude/plugins/cache/` [1].
- **Cache path corruption and scope desync:** In issue #60292, plugins
  installed at user scope (`~/.claude/settings.json`) lose physical
  directory tracking, generating the error
  `Plugin "<name>" not cached at (not recorded)` under the `/plugins`
  Errors tab [3]. The built-in TUI defaults to project scope and fails
  to refresh or reinstall the unrecorded path [3]. CLI commands executed
  from the home directory falsely report project-scope conflicts,
  forcing users to manually edit `settings.json`, wipe
  `~/.claude/plugins/cache/`, and reinstall using an explicit
  `--scope user` argument [3].
- **Marketplace registry abandonment:** In BMAD-METHOD v6.7.0
  (2026-05-17), maintainers completely retired the remote marketplace
  registry [4]. The installer deleted its network client classes
  (`RegistryClient`, `CommunityModuleManager`) and dropped the
  community module picker from the interactive installer, establishing
  a local bundled `bmad-modules.yaml` as the sole source of truth [4],
  [5].

### F2. In-repository framework distribution causes silent drift and destructive file collisions, requiring complex defensive apparatus
[consensus] (maintainer warnings, issue discussions, and tool manuals).
- **Silent drift through full overrides:** BMAD maintainers documented
  that copying entire configuration files into override locations
  (`customize.toml`) is "actively harmful: the next update ships new
  defaults, but your override file locks in the old values. You'll
  silently drift out of sync with every release" [4], as noted in
  `2026-08-29-framework-distribution-in-the-field.md`.
- **Destructive file retirement:** GSD Core (`open-gsd/gsd-core`)
  documented that the primary danger during framework upgrades is file
  retirement: the installer risk was "delete a user-created file because
  it happens to live inside a GSD-managed directory" [8]. To survive
  updates without destroying user work, GSD Core constructed an
  elaborate multi-phase migration system: classifying every file as
  managed, user-owned, or unknown; printing a pre-mutation `Plan`;
  writing an audit `Journal` with rollback data; and automatically
  backing up local edits to `gsd-local-patches/` [8].
- **Refusal to upgrade modified files:** GitHub Spec Kit enforces an
  install manifest (`.specify/integration.json`) [7]. If a user modifies
  any managed integration file in `.specify/` or `.claude/skills/`,
  `specify integration upgrade <key>` halts and throws an error,
  refusing to proceed unless the user explicitly passes `--force` [7].
- **Unmanaged schema abandonment:** In Agent OS v3 (January 2026,
  Discussion #310), maintainers removed roughly 70 % of the framework
  (spec writing, task breakdown, and execution orchestration) [9].
  Community feedback on the release reported that users were left with
  no migration path for legacy v2 files and that projects broke until
  unresolved pull requests were merged [9].

### F3. Dividing a framework into a core with separate external repositories or microservices creates divergence and rapid retreats
[consensus] (maintainer release notes, historical post-mortems, and
architectural audits).
- **The four-day repository split:** In Superpowers v2.0.0 (2025-10-12),
  maintainers moved all skills out of the main plugin into an external
  repository (`obra/superpowers-skills`), cloning it into user config
  directories on session startup to enable user forking [10]. Just four
  days later, in v3.0.1 (2025-10-16), maintainers reversed the split
  and merged skills back into the plugin ("We now use Anthropic's
  first-party skills system!"), archiving `obra/superpowers-skills` on
  2025-10-27 [10], [12].
- **Library divergence in distributed components:** Segment's
  post-mortem "Goodbye Microservices" (2018-07-10) recorded the failure
  of splitting destination handling across 140 separate repositories
  and services [13]. Shared libraries diverged rapidly, testing changes
  across dozens of independent codebases became prohibitive, and
  operational maintenance scaled linearly, forcing a total consolidation
  back into a single monolithic codebase [13].
- **Premature boundary failure:** Martin Fowler's "MonolithFirst"
  (2015-06-03) established that system boundaries drawn before several
  concrete implementations exist are almost invariably drawn wrong,
  imposing a distributed complexity tax without delivering reuse [14].

### F4. Claude Code mechanism evolutions broke legacy commands, formatting validation, and hook pipelines
[vendor report] (official changelog and platform documentation).
- **Deprecation of slash command paths:** Early Claude Code frameworks
  relied on `.claude/commands/` for custom tooling. The introduction of
  first-party skills (`SKILL.md`) and the deprecation of legacy slash
  command directories forced frameworks to re-architect their layout
  (Superpowers v5.1.0 removed legacy commands and a named agent [10];
  Agent OS and task-master underwent major migrations [9]).
- **Security rejection of control and directional characters:** Claude
  Code introduced strict name and character filtering in its engine
  [15]. Custom commands and skills containing unescaped shell control
  characters or folders featuring directional-changing Unicode and
  `<`/`>` characters are ignored or refused outright at runtime [15].
- **Hook re-sequencing and recursion capping:** Anthropic modified hook
  lifecycles so that `UserPromptSubmit` hooks run strictly before slash
  command expansion, while capping plugin hooks and workflows at a hard
  28,000-level nesting limit to prevent recursive engine crashes [15].
- **Structural inability to ship always-on instructions:** Claude Code
  plugins are strictly constrained to packaging skills, agents, hooks,
  and MCP servers [16]. A plugin cannot carry an always-on root
  `CLAUDE.md`, forcing frameworks to either scaffold project-level
  instruction files or rely on user-level prompt injection [16], [17].

### F5. Plugin distribution eliminates repository merge collisions but substitutes harness-level failure modes
[consensus] (practitioner claim and comparative audit; disconfirming
query confirmed).
- Frameworks adopting pure plugin architecture (Superpowers, Conductor)
  completely eliminate repository merge collisions, git merge conflicts,
  and the need for file manifests or `--force` flags [10], [18]. Because
  nothing is copied into the user's repository, an update to the plugin
  never mutates project files [10].
- However, this immunity replaces repository collisions with
  harness-level failure modes: silent update starvation due to Git
  cloning bugs [1], local cache directory corruption [3], permanent
  context token overhead (loading skill and agent names on every turn
  [16]), and immediate vulnerability to upstream Claude Code breaking
  changes.

## Unexpected

- **Every enabled plugin taxes every session turn:** Claude Code's
  plugin architecture loads the name and description of every skill and
  agent across all active plugins into the context window on every turn,
  regardless of whether they are invoked [16]. Distributing extensive
  frameworks as plugins imposes a mandatory context penalty on every
  interaction.
- **Plugins cannot carry root instruction files:** The research card
  assumed a framework could be cleanly distributed as a Claude Code
  plugin. However, Claude Code plugins cannot package an always-on root
  `CLAUDE.md` [16], [17]. Any framework relying on persistent behavioral
  rules must still touch the user's repository or require manual
  user-level configuration outside the plugin.

## Not found

- **No sustainable independent remote marketplace:** No AI agent
  framework was found operating an independent, remote marketplace
  registry over time. BMAD attempted one and retired it in v6.7.0; all
  other frameworks distribute directly via GitHub repositories or local
  manifests.
- **No quantified churn metrics:** No public dataset or maintainer
  post-mortem provided precise figures measuring user churn or drop-off
  attributable to framework upgrade breakage.

## Options

### 1. Unified repository with directory boundaries (Monolith First)
- **Trade-offs:** Retains one CLAUDE.md, a single release train, and
  zero distribution machinery; avoids marketplace caching and Git pull
  bugs entirely. Downside: secondary project layers must live in the same
  repository or be cloned alongside it.
- **Evidence:** Directly supported by Fowler [14], Segment's
  consolidation [13], and Superpowers' retreat from a multi-repo split
  [10].

### 2. Pure Claude Code plugin distribution
- **Trade-offs:** Eliminates repository-level merge conflicts and file
  taxonomies. Downside: cannot ship an always-on `CLAUDE.md`, subjects
  users to silent marketplace update failures (issue #44276 [1]), and
  taxes session context tokens on every turn [16].

### 3. Engine installed globally outside the repository with a thin state file
- **Trade-offs:** Avoids copying engine code into user projects while
  retaining full CLI control. Downside: requires an external package
  manager or global installer (`uv tool` or `npm`) and separate CLI
  upgrade commands (as seen in Spec Kit [7] and GSD Core [8]).

### 4. Release-time scripted separation from a single source tree
- **Trade-offs:** Retains a single fast development loop while
  publishing release-tagged standalone artifacts for external projects,
  avoiding multi-repo maintenance drag during feature development.

## Relevance to this project

- **Do not distribute the forge base as a Claude Code plugin or custom
  marketplace.** The field's evidence proves that custom marketplace
  distribution suffers from silent update starvation (issue #44276),
  cache path corruption (issue #60292), context consumption on every
  turn, and the inability to supply an always-on `CLAUDE.md`.
- **Do not copy engine mechanics into user repositories.** Frameworks
  that copy files into user trees (BMAD, Spec Kit, GSD Core) are forced
  to engineer extensive defensive systems (install manifests, rollback
  journals, `--force` flags) to survive updates without destroying
  customizations.
- **Follow Monolith First:** Keep the base mechanics and initial
  operating layer within one repository using clear directory boundaries
  (Option 1). If external consumption is required, extract standalone
  releases via an automated script at release time (Option 4), rather
  than splitting into separate repositories prematurely.

Consult when: deciding whether to package framework components as a
Claude Code plugin, evaluating multi-repository splits versus a single
repository, or designing upgrade mechanics for user-facing templates and
skills.

## Sources

[1] anthropics/claude-code contributors. "Marketplace plugins from
GitHub repos are not auto-updated (Issue #44276)". GitHub Issues.
2025-2026, structured data.
https://github.com/anthropics/claude-code/issues/44276. Primary. Read
via summarised fetch. Original.

[2] anthropics/claude-code contributors. "Marketplace plugins from
GitHub repos are not auto-updated / refreshed (Issue #36938)". GitHub
Issues. 2025-2026, structured data.
https://github.com/anthropics/claude-code/issues/36938. Primary. Read
via summarised fetch. Original.

[3] anthropics/claude-code contributors. "[BUG] User-scope plugins show
'not cached at (not recorded)' — /plugins TUI cannot refresh or
reinstall (Issue #60292)". GitHub Issues. 2026, structured data.
https://github.com/anthropics/claude-code/issues/60292. Primary. Read
via summarised fetch. Original.

[4] bmad-code-org. "BMAD-METHOD Changelog". GitHub repository raw file.
2026-05-18, structured data.
https://raw.githubusercontent.com/bmad-code-org/BMAD-METHOD/main/CHANGELOG.md.
Primary. Read via summarised fetch. Original.

[5] bmad-code-org. "BMAD-METHOD Repository README". GitHub repository.
2026, structured data.
https://github.com/bmad-code-org/BMAD-METHOD. Primary. Read via
summarised fetch. Original.

[6] `2026-08-29-framework-distribution-in-the-field.md`. Internal
forge research note. 2026-08-29. Primary. Read in full. Original.

[7] GitHub. "Spec Kit Upgrade Guide (docs/upgrade.md)". GitHub
repository. 2026, structured data.
https://github.com/github/spec-kit/blob/main/docs/upgrade.md. Primary.
Read via summarised fetch. Original.

[8] open-gsd. "GSD Core Repository and Documentation". GitHub
repository. 2026, structured data.
https://github.com/open-gsd/gsd-core. Primary. Read via summarised
fetch. Original.

[9] CasJam (buildermethods). "Agent OS v3 - Leaner and more aligned for
2026 (Discussion #310)". GitHub Discussions. 2026-01-20, byline.
https://github.com/buildermethods/agent-os/discussions/310. Primary.
Read via summarised fetch. Original.

[10] Jesse Vincent (obra). "Superpowers Release Notes". GitHub
repository. 2026-09-25, structured data.
https://github.com/obra/superpowers/blob/main/RELEASE-NOTES.md.
Primary. Read via summarised fetch. Original.

[11] Jesse Vincent (obra). "Superpowers Repository README". GitHub
repository. 2026, structured data.
https://github.com/obra/superpowers. Primary. Read via summarised
fetch. Original.

[12] Jesse Vincent (obra). "superpowers-skills Repository (Archived)".
GitHub repository. 2025-10-27, structured data.
https://github.com/obra/superpowers-skills. Primary. Read via
summarised fetch. Original.

[13] Alexandra Noonan (Segment / Twilio). "Goodbye Microservices: From
100s of problem children to 1 superstar". Twilio Blog. 2018-07-10,
byline.
https://www.twilio.com/en-us/blog/developers/best-practices/goodbye-microservices/.
Primary. Read via summarised fetch. Original.

[14] Martin Fowler. "MonolithFirst". martinfowler.com. 2015-06-03,
byline.
https://martinfowler.com/bliki/MonolithFirst.html. Primary. Read via
summarised fetch. Original.

[15] Anthropic. "Claude Code Changelog". GitHub repository. 2026,
structured data.
https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md.
Primary. Read via summarised fetch. Original.

[16] Anthropic. "Claude Code Plugins Overview". Anthropic
Documentation. 2026, structured data.
https://code.claude.com/docs/en/plugins. Primary. Read via summarised
fetch. Original.

[17] Anthropic. "Claude Code Plugin Dependencies". Anthropic
Documentation. 2026, structured data.
https://code.claude.com/docs/en/plugins/dependencies. Primary. Read
via summarised fetch. Original.

[18] Anthropic. "Claude Code Marketplaces". Anthropic Documentation.
2026, structured data.
https://code.claude.com/docs/en/plugins/anthropic-marketplaces.
Primary. Read via summarised fetch. Original.

## Opened and not used

- None: all 14 web resources and attached notes opened during the run
  met quality requirements and were cited directly in the text.

## Search record

1. Broad query on Claude Code plugin issues and breaking changes
   (`claude code plugin issues breaking change github`).
2. Broad query on Claude Code plugin documentation
   (`code.claude.com/docs plugins`).
3. Targeted search on Superpowers repository and release history
   (`site:github.com/obra/superpowers RELEASE-NOTES.md OR issues`).
4. Query on Claude Code plugin cache and update errors
   (`claude plugin update failed OR error OR bug OR cache`).
5. Targeted query on plugin cache missing paths
   (`not cached at (not recorded) claude`).
6. Query on Claude Code issue repository for cache errors
   (`not cached at (not recorded) site:github.com/anthropics/claude-code`).
7. Query on marketplace update failures
   (`site:github.com/anthropics/claude-code/issues marketplace OR plugin update`).
8. Targeted query on Claude Code breaking changes for commands and skills
   (`site:github.com/anthropics/claude-code breaking change OR deprecated commands skills`).
9. Targeted query on Claude Code changelog breaking changes
   (`claude-code changelog breaking changes commands skills`).
10. Query on BMAD-METHOD documentation and changelog
    (`site:github.com/bmad-code-org/BMAD-METHOD customize OR upgrade`).
11. Query on BMAD-METHOD remote registry retirement
    (`Remote marketplace registry fully retired OR Community modules picker removed`).
12. Targeted verification query on Spec Kit upgrade guide
    (`site:github.com/github/spec-kit upgrade.md OR integration upgrade`).
13. Targeted query on Spec Kit `--force` flag on modified files
    (`site:github.com/github/spec-kit modified integration upgrade OR --force`).
14. Disconfirming query on plugin distribution eliminating upgrade
    issues
    (`plugin distribution upgrade claude code OR superpowers OR conductor`).
15. Verification fetch of Issue #44276 (`https://github.com/anthropics/claude-code/issues/44276`).
16. Verification fetch of Issue #36938 (`https://github.com/anthropics/claude-code/issues/36938`).
17. Verification fetch of Issue #60292 (`https://github.com/anthropics/claude-code/issues/60292`).
18. Verification fetch of BMAD raw changelog (`https://raw.githubusercontent.com/bmad-code-org/BMAD-METHOD/main/CHANGELOG.md`).
19. Verification fetch of Spec Kit upgrade guide (`https://github.com/github/spec-kit/blob/main/docs/upgrade.md`).
20. Verification fetch of Agent OS Discussion #310 (`https://github.com/buildermethods/agent-os/discussions/310`).
21. Verification fetch of Twilio/Segment post-mortem (`https://www.twilio.com/en-us/blog/developers/best-practices/goodbye-microservices/`).
22. Verification fetch of Martin Fowler MonolithFirst (`https://martinfowler.com/bliki/MonolithFirst.html`).
23. Verification fetch of Superpowers release notes (`https://github.com/obra/superpowers/blob/main/RELEASE-NOTES.md`).
24. Verification fetch of superpowers-skills repository (`https://github.com/obra/superpowers-skills`).
25. Verification fetch of Claude Code plugins documentation (`https://code.claude.com/docs/en/plugins`).
26. Verification fetch of Claude Code dependencies documentation (`https://code.claude.com/docs/en/plugins/dependencies`).
27. Verification fetch of Claude Code marketplaces documentation (`https://code.claude.com/docs/en/plugins/anthropic-marketplaces`).

Disconfirming query finding: confirmed that pure plugin distribution
completely eliminates repository-level file merge collisions, but
substitutes harness-level marketplace synchronization bugs, cache
corruption, context taxation, and breaking changes.

Run ending: the stop rule was met (each of the three kinds of trouble
has two or more first-hand reports documented) and the opening budget of
14 verified external URLs was respected.
