---
date: 2026-11-14
project: forge
topic: composing a base and layers in Claude Code
derived_from: research/2026-11-14-anvil-carrying-layers/00-plan.md, card 1; research/2026-08-29-claude-code-packaging.md; research/2026-10-03-user-extensions-kept-apart-from-the-core.md; web sources below
engine: antigravity
model: engine default
usage: {"input_tokens":142349,"output_tokens":27594,"thinking_tokens":20529,"cache_read_tokens":679756,"total_tokens":169943}
run: tmp/research/2026-11-14-anvil-carrying-layers/01-composing
status: immutable
---

# Composing a base and layers in Claude Code: plugins, dependencies, namespaces, and precedence

## In short

In November 2026 Claude Code supports packaging a base mechanics
layer and upper content layers as separate plugins distributed via
marketplaces, connected by semantic version ranges in `dependencies`
that resolve against git tags. When a required version is missing or
in conflict, Claude Code disables the dependent plugin and records
structured error codes (`dependency-unsatisfied`, `range-conflict`,
`dependency-version-unsatisfied`, `no-matching-tag`) in
`claude plugin list --json`. Skills and agents shipped by plugins are
strictly namespaced (`plugin:skill`, `plugin:agent`), which avoids
collisions between base and layer components of the same name, while
hooks have no namespace and all registered hooks execute cumulatively.
An agent in one package can preload a skill from another package by
specifying its namespaced identifier (e.g. `base:contract`) in its
frontmatter `skills:` field (up to 32 skills), injecting the full
text at startup. Epistemic status is high certainty on documented
mechanics across vendor guides and releases through v2.1.311. The
disconfirming query confirmed that cross-plugin skill preloading
suffers from silent failure in the UI when resolution bugs hit
(falling back to `.claude/skills/` and skipping the skill with a
debug-log warning only), and that plugin auto-updates recently
required patches to reliably install newly added version dependencies.
The unexpected finding is that v2.1.295 introduced `onFailure: "block"`
for hooks, and 2.1.x added `agentId` to `tool.check`, providing a
deterministic execution-blocking gate for base contracts that
outperforms advisory agent preloading.

## Question

#### Card 1: Composing a base and layers in Claude Code
- **Question:** What does Claude Code offer in November 2026 for one
  package (a base) carrying mechanism and other packages (layers, a
  user's own things) carrying content on it: plugins and marketplaces,
  dependencies between plugins with version ranges and what happens
  when a required version is missing, namespaces, and the precedence
  when a base, a layer and a user define a skill, an agent or a hook
  of the same name? Can an agent of one package preload a skill of
  another package, and by what name? What changed since early
  October 2026?
- **Why it matters:** It decides whether the plugin, the package-per-layer
  and the no-plugin candidates can carry a shared reviewer contract
  and a required version of the base at all.
- **What would answer it:** The vendor's own statements of behaviour:
  the documentation pages of plugins, marketplaces, skills, subagents
  and settings, and the changelog entries since October 2026.
- **Where to look:** Anthropic's Claude Code documentation; the
  changelog and release notes of Claude Code; the reference of the
  plugin manifest and the marketplace file; the issue tracker of
  Claude Code for the behaviours the documentation leaves unsaid. Must
  turn up: plugin dependencies, the namespace rule of plugin skills,
  the `skills` field of a subagent.
- **Disconfirming query:** A search for reports that cross-plugin
  skill preloading or plugin dependency version ranges do not work as
  documented; expected: at least one open issue.
- **Stop rule:** Every sub-question has a statement from the vendor's
  documentation or changelog, or is recorded as not stated there;
  nothing new from a differently worded query; the opening budget of
  the brief.

The baseline the note must beat: the research notes of 2026-08-29 and
2026-10-03 established that plugins cannot carry an always-on root
`CLAUDE.md` or a `rules/` directory; that skills and agents follow
conflicting precedence orders (skills: enterprise > personal > project;
agents: managed > CLI > project > user > plugin); that plugin
dependencies exist with semantic version ranges; and that subagents
preload skills at startup via `skills:` but silently skip missing
skills with a debug-log entry. The baseline left unverified whether an
agent in one plugin can preload a skill from another plugin by
qualified name, how bare skill names resolve when two plugins collide,
what specific runtime errors Claude Code produces on unsatisfied version
ranges, and what changed between v2.1.288 (2026-10-02) and mid-November
2026.

## Key findings

**F1: Plugin dependencies enforce semantic version ranges against git
tags and disable failing plugins with explicit machine-readable error
codes.** [vendor claim, vendor report]
Dependencies are declared in `.claude-plugin/plugin.json` under
`dependencies` as a list of strings (`"plugin-name"` or
`"plugin-name@marketplace"`) or objects with semver ranges (e.g.
`{"name": "forge-base", "version": "^1.0.0", "marketplace": "forge"}`)
[1, 2]. Version ranges resolve against git repository tags formatted as
`{name}--v<version>` [2]. Claude Code manages dependency installation
and enablement automatically at the matching scope [1]. When a
dependency cannot be satisfied, Claude Code disables the dependent
plugin and reports one of four specific error states:
`dependency-unsatisfied` (dependency missing or disabled),
`dependency-version-unsatisfied` (installed version falls outside the
required semver range), `range-conflict` (conflicting version ranges
demanded by multiple plugins), or `no-matching-tag` (upstream
repository lacks the required `{name}--v*` git tag) [2]. In
`claude plugin list --json`, broken plugins expose an `errors` field
containing the error code and resolution instructions, whereas healthy
plugins omit the field entirely [2]. Cross-marketplace dependencies are
blocked unless the root marketplace's `marketplace.json` explicitly
declares the dependency target under `allowCrossMarketplaceDependenciesOn`
[1].

**F2: Automatic component namespacing isolates plugin skills and agents
by plugin name, preventing collisions between base and layer packages.**
[vendor claim, standard / vendor report]
Claude Code automatically namespaces every skill and agent shipped in a
plugin using the plugin's manifest `name` [3, 5]. A skill named `verify`
in a plugin named `forge-base` becomes `/forge-base:verify`, and an
agent named `reviewer` becomes `forge-base:reviewer` (subfolders become
`forge-base:folder:reviewer`) [3, 5]. The colon `:` is reserved by
Claude Code as a namespace delimiter; plugin manifest names cannot
contain colons [5]. If a base plugin and a layer plugin each define a
skill or agent with the same basename, no collision occurs in their
qualified names: `forge-base:check` and `forge-layer:check` coexist as
independent, invocable components [3, 4].

**F3: Subagents preload cross-package skills via fully qualified names,
injecting full text at startup up to a hard limit of 32 skills.**
[vendor claim, vendor report]
When configuring a custom subagent, the YAML frontmatter `skills:` field
bypasses progressive disclosure by injecting the full text of listed
skills directly into the subagent's initial context window [6, 7]. A
subagent in a layer plugin can preload a contract skill from a base
plugin by specifying its namespaced identifier (e.g.
`skills: ["forge-base:contract"]`) [6, 7]. Project and user skills are
referenced by their bare names [6]. Documentation specifies a hard
cap: at most the first 32 distinct names listed in `skills:` are
preloaded into the subagent [7]. Subagents retain access to unlisted
skills via the built-in `Skill` tool during execution unless restricted
by tool permissions [6]. Skills declaring `disable-model-invocation: true`
cannot be preloaded [7].

**F4: Missing or invalid preloaded skills fail silently in interactive
sessions, executing the subagent without its contract.** [vendor claim,
audit / practitioner claim]
When an agent's `skills:` list references a skill that is missing,
disabled, or cannot be resolved, Claude Code does not abort execution or
display an error banner in the user's terminal [7, 8]. Instead, it
silently skips the skill and writes a warning solely to the debug log
[7, 8]. As a result, an isolated reviewer agent whose preloaded base
contract skill fails to resolve will run unconstrained, completely
undetected in the conversation UI unless checked via `/doctor` or debug
logs [8, 9]. The disconfirming query identified reports on GitHub where
plugin-scoped skill preloads (`plugin:skill`) failed to resolve due to
the loader mistakenly checking project-level `.claude/skills/` paths
instead of the plugin cache [8].

**F5: Skills and agents follow inverted precedence orders across
configuration tiers.** [vendor claim, vendor report]
For bare skills and commands, precedence runs: Managed (Enterprise) >
Personal/User (`~/.claude/skills/`) > Project (`.claude/skills/`) >
Plugin (lowest, accessed via bare name only if unshadowed) [10, 11].
For subagents, precedence is reversed: Managed > CLI flag (`--agents`)
> Project (`.claude/agents/`) > User (`~/.claude/agents/`) > Plugin
`agents/` (lowest) [10]. A user's personal skill overrides a project's
same-named skill, but a project's subagent overrides a user's personal
subagent [10, 11]. Furthermore, plugin agents cannot declare `hooks`,
`mcpServers`, or `permissionMode` [10].

**F6: Hooks carry no namespace and accumulate across base, layer,
project, and user tiers.** [vendor claim, vendor report]
Hooks do not shadow or collide [10, 12]. When a base plugin, a layer
plugin, a user configuration (`~/.claude/settings.json`), and a project
configuration register hooks for the same event (e.g. `SessionStart`,
`PreToolUse`, `PostToolUse`), all registered hooks execute in succession
[10, 12]. Hooks declared by plugins execute alongside local hooks [10].

**F7: Additions between early October and mid-November 2026 (v2.1.288
to v2.1.311) introduced blocking hooks, subagent hook IDs, and dependency
update fixes.** [vendor claim, vendor report]
Across versions 2.1.289 through 2.1.311:
1. *Hook failure blocking (v2.1.295, 2026-10-08):* Added `onFailure: "block"`
   to custom command and HTTP hooks, ensuring that hook timeouts or
   nonzero exits halt tool execution rather than silently passing [13].
2. *Subagent identification in hooks (2.1.x):* Added `agentId` to the
   `tool.check` hook event payload, enabling hooks to distinguish
   permission checks made by a subagent from those made by the main
   thread [14].
3. *Dependency update bugfixes (2.1.x):* Fixed bugs where
   `claude plugin update` and background auto-updates failed to install
   newly added dependencies introduced by newer plugin versions [15].
4. *Plugin CLI enhancements:* Added `--marketplace <source>` to
   `claude plugin install`, and updated `claude plugin validate` to
   verify hook gating sites and avoid false collisions on sibling
   directories [14].
5. *Context and token controls (v2.1.299, 2026-10-14):* Added terminal
   idle compaction for sessions over 200K tokens idle for ~54 minutes,
   and `CLAUDE_CODE_DISABLE_FILE_MENTIONS` [13].

## Unexpected

*Lead 1: Deterministic contract enforcement via `onFailure: "block"`
hooks.* [13, 14] The card assumes that cross-package contract
enforcement between a base and layers must rely on subagent `skills:`
preloading or system prompts. However, v2.1.295 introduced
`onFailure: "block"` for hooks [13], and 2.1.x added `agentId` to
`tool.check` [14]. A base plugin can register a `PreToolUse` or
`tool.check` hook that intercepts tool calls, verifies compliance
against the base ledger or contract rules, and strictly aborts
violating actions. Because hooks cannot be disabled by subagents and run
cumulatively across all plugins, hook-based enforcement provides a
guarantee that prompt-based skill preloading cannot match.

*Lead 2: The 32-skill subagent preloading limit.* [7] Subagent
frontmatter enforces a documented ceiling of 32 preloaded skills. While
adequate for a single reviewer preloading a base contract, composite
architectures that fan out multiple modular layer skills into a single
subagent context cannot scale past 32 distinct skills.

## Not found

- Official documentation specifying which plugin wins a bare command
  invocation when two installed plugins define the same skill name (e.g.
  `/check` when both `base:check` and `layer:check` exist) and no
  local project/user skill exists. The documentation states that bare
  names resolve "unless another command uses that name", but does not
  clarify whether it falls back to registration order or raises an
  ambiguity error. Looked in `code.claude.com/docs/en/plugins/*` and
  `skills`.
- Documentation explicitly verifying whether a plugin-defined subagent
  can preload a project-level skill by its bare name without knowing
  the project directory structure. Looked in
  `code.claude.com/docs/en/sub-agents`.

## Options

The findings offer three distinct architectures for separating a base
mechanics package from operating layers and user additions:

**Option 1: Two independent plugins (Base Plugin + Layer Plugin) linked
by native semver dependencies.**
- *Mechanics:* Base is packaged as `forge-base` (shipping mechanics
  skills, reviewer subagents, scripts, and validation hooks). Operating
  layers are packaged as separate plugins (`forge-layer`), declaring
  `dependencies: [{"name": "forge-base", "version": "^1.0.0"}]` in
  `plugin.json`. Layer subagents preload base contracts via
  `skills: ["forge-base:contract"]`.
- *Trade-offs:* Native version enforcement: Claude Code disables
  incompatible layers and reports `dependency-version-unsatisfied` via
  `claude plugin list --json`. Automatic installation of base
  dependencies. Costs: Plugins cannot carry always-on `CLAUDE.md` or
  `rules/`; cross-plugin skill preloading is vulnerable to silent
  skipping on resolution bugs; auto-update is off by default for
  third-party marketplaces.

**Option 2: Single composite development repository, split into Base
and Layer plugins at release.**
- *Mechanics:* Base mechanics and operating layers remain in a single
  repository during development, preserving the local zero-friction
  iteration loop. A release script generates standalone plugin
  distributions for `forge-base` and `forge-layer` with matching git
  tags (`forge-base--v1.0.0`) and publishes them to a GitHub marketplace.
- *Trade-offs:* Solves the dual-loop problem: developers test changes
  instantly across base and layer without packaging overhead, while
  external users receive version-pinned plugins with automated
  dependency checks. Costs: Release script maintenance; still requires
  substitutes for always-on memory.

**Option 3: Repository-level composition via `@import` and `--add-dir`,
dispensing with plugins.**
- *Mechanics:* The base repository is cloned locally; projects import
  base memory via `@~/.claude/base/CLAUDE.md` and load mechanics via
  `--add-dir <base-path>`.
- *Trade-offs:* Preserves always-on `CLAUDE.md` context and rules
  without plugin workarounds. Costs: No automated version checking; a
  missing or incompatible base breaks silently without Claude Code
  raising an error; requires manual launch flags or launcher wrappers.

## Relevance to this project

The findings directly resolve the card's framing for the forge:

1. **Native plugin dependencies work and provide the only built-in
   version-gating mechanism in Claude Code.** A layer plugin can declare
   a semver dependency on the base plugin (`^1.0.0`). When the base is
   missing or out of range, Claude Code disables the layer and exposes
   `dependency-unsatisfied` or `dependency-version-unsatisfied` in
   `claude plugin list --json`.
2. **Do not rely on subagent `skills:` preloading as the sole contract
   enforcement boundary.** Because Claude Code silently swallows missing
   or unresolved preloaded skills and executes subagents unconstrained
   without user warning, a broken contract skill is invisible in the
   session.
3. **Use the new `onFailure: "block"` hooks for base contract
   enforcement.** Combining plugin dependencies (which prevent loading
   incompatible layers) with a base `PreToolUse` hook configured with
   `onFailure: "block"` (v2.1.295) creates a reliable enforcement gate
   for the forge's mechanics that cannot be bypassed by prompt drift or
   subagent preloading resolution bugs.
4. **Recommendation:** Adopt Option 2 (single repository for development,
   separated into `forge-base` and `forge-layer` plugins at release).
   This preserves fast internal iteration while giving external users
   managed updates and explicit dependency validation.

Consult when: designing the split between the forge base mechanics and
operating layers, authoring `plugin.json` manifests and marketplace
files, implementing cross-package reviewer subagents, or writing
enforcement hooks.

## Sources

[1] Plugin Dependencies, Anthropic, undated (fetched 2026-11-14 via
    search retrieval summary),
    https://code.claude.com/docs/en/plugins/dependencies; primary;
    summarised fetch; original.
[2] Plugin Manifest Reference and Dependency Error States, Anthropic,
    undated (fetched 2026-11-14 via search retrieval summary),
    https://code.claude.com/docs/en/plugins/manifest-reference;
    primary; summarised fetch; original.
[3] Plugins Overview and Component Namespaces, Anthropic, undated
    (fetched 2026-11-14 via search retrieval summary),
    https://code.claude.com/docs/en/plugins; primary; summarised
    fetch; original.
[4] Skills in Claude Code and Collision Rules, Anthropic, undated
    (fetched 2026-11-14 via search retrieval summary),
    https://code.claude.com/docs/en/skills; primary; summarised
    fetch; original.
[5] Create a Plugin, Anthropic, undated (fetched 2026-11-14 via search
    retrieval summary),
    https://code.claude.com/docs/en/plugins/create; primary; summarised
    fetch; original.
[6] Sub-agents in Claude Code, Anthropic, undated (fetched 2026-11-14
    via search retrieval summary),
    https://code.claude.com/docs/en/sub-agents; primary; summarised
    fetch; original.
[7] Subagent Frontmatter and Skills Preloading Reference, Anthropic,
    undated (fetched 2026-11-14 via search retrieval summary),
    https://code.claude.com/docs/en/sub-agents; primary; summarised
    fetch; original.
[8] Issue Tracker: Namespaced skill preloading resolution bug,
    Anthropic, undated (fetched 2026-11-14 via search retrieval
    summary), https://github.com/anthropics/claude-code/issues;
    primary / practitioner claim; summarised fetch; original.
[9] Claude Code Diagnostics and Troubleshooting, Anthropic, undated
    (fetched 2026-11-14 via search retrieval summary),
    https://code.claude.com/docs/en/troubleshooting; primary;
    summarised fetch; original.
[10] Settings, Precedence, and Permissions, Anthropic, undated
     (fetched 2026-11-14 via search retrieval summary),
     https://code.claude.com/docs/en/settings; primary; summarised
     fetch; original.
[11] User extensions kept apart from the core, forge project research
     note, dated 2026-10-03 (structured data), local repository file
     `2026-10-03-user-extensions-kept-apart-from-the-core.md`;
     primary / internal research note; read in full; original.
[12] Claude Code Hooks Guide, Anthropic, undated (fetched 2026-11-14
     via search retrieval summary),
     https://code.claude.com/docs/en/hooks; primary; summarised
     fetch; original.
[13] Claude Code Changelog: releases 2.1.289 through 2.1.311,
     Anthropic, entries dated 2026-10-08 through 2026-11-14
     (structured data),
     https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md;
     primary; summarised fetch; original.
[14] Claude Code Plugin Hook Typings and Validation Updates, Anthropic,
     entries dated October 2026 (structured data),
     https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md;
     primary; summarised fetch; original.
[15] Bugfix logs: Plugin dependency update and marketplace sync,
     Anthropic, entries dated October-November 2026 (structured data),
     https://github.com/anthropics/claude-code/issues; primary;
     summarised fetch; original.

## Opened and not used

- Anthropic Claude Code CHANGELOG.md entries for vim mode `%` motions
  and voice dictation limits: off the question of packaging and
  layering.
- Third-party web tutorials on Claude Code skills (shiplight.ai,
  scrimba.com, plugwiki.com): below the bar, secondary summaries
  superseded by vendor documentation [3, 4, 6].

## Search record

- Queries run, in order:
  1. `claude code changelog October November 2026 site:code.claude.com`
  2. `site:code.claude.com/docs/en/plugins/dependencies`
  3. `site:code.claude.com/docs/en/plugins "dependencies" "version" range unsatisfied missing`
  4. `site:code.claude.com/docs/en/sub-agents "skills" preload plugin namespace`
  5. `site:code.claude.com/docs/en/sub-agents "skills" preloaded cross-plugin`
  6. `site:code.claude.com/docs/en "skills:" "plugin:" subagents preload`
  7. `site:code.claude.com/docs/en "precedence" OR "priority" skills agents hooks`
  8. `site:code.claude.com/docs/en/plugins "bare" skill collision namespace`
  9. `site:code.claude.com/docs/en/plugins "namespace" OR "prefix" OR "colon" OR ":"`
  10. `"skills:" site:code.claude.com/docs/en "sub-agents" OR "plugins"`
  11. `"claude code" "skills" preload OR preloading issue OR bug OR "not found" OR "debug log" site:github.com/anthropics/claude-code` (disconfirming query)
  12. `site:github.com/anthropics/claude-code/issues "skills" preload OR namespace OR dependencies`
  13. `site:github.com/anthropics/claude-code/issues "dependencies" "version" OR "plugin"`
  14. `"CHANGELOG.md" site:github.com/anthropics/claude-code "2.1." "plugin"`
  15. `"anthropics/claude-code" "2.1." "October" OR "November" 2026 CHANGELOG`
- Pages opened: 15 summaries retrieved from Anthropic documentation,
  official changelog, and GitHub repository issues.
- Disconfirming query findings: Confirmed that cross-plugin skill
  preloading via `plugin:skill` has documented failure modes where
  resolution bugs cause "skill not found" errors (falling back to
  project `.claude/skills/` instead of plugin cache paths), and the
  agent runs silently without the skill; also confirmed recent bugfixes
  in 2.1.x where plugin updates failed to install newly added version
  dependencies.
- Reason run ended: All sub-questions in Card 1 answered from vendor
  documentation, changelog, and issue tracker; stop rule satisfied
  within the opening budget.
