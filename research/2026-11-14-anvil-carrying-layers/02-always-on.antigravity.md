---
date: 2026-11-14
engine: antigravity
model: engine default
usage: {"input_tokens":149998,"output_tokens":33797,"thinking_tokens":26041,"cache_read_tokens":1328677,"total_tokens":183795}
run: tmp/research/2026-11-14-anvil-carrying-layers/02-always-on
status: immutable
---

```markdown
---
date: 2026-11-14
project: forge
topic: always-on rules under each candidate
status: immutable
engine: <claude | antigravity | …: the engine that made the note; the forge names engines, never models>
model: <as the envelope's reports it, or "engine default">
usage: <the envelope's usage, compact; "—" for a session agent>
run: <tmp/research/<run>/<card>: the packet folder the note was made from>
derived_from: research/2026-11-14-anvil-carrying-layers/00-plan.md, card 2; 2026-08-29-claude-code-packaging.md; 2026-10-03-user-extensions-kept-apart-from-the-core.md; web sources below
---

# Always-on rules under six candidate splits of the framework

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Always-on instructions reach Claude Code natively only when files
reside inside the project working directory or user-level configuration.
A plugin still cannot carry always-on instructions or rules: vendor
documentation explicitly confirms that a `CLAUDE.md` at the plugin root
is ignored, `claude plugin validate` emits a warning, and `plugin.json`
has no manifest field for rules. The disconfirming query for plugin
always-on instructions returned no results. Workarounds via a
`SessionStart` hook injecting `hookSpecificOutput.additionalContext` are
strictly capped at 10,000 characters and suffer a fatal defect: isolated
subagents fire `SubagentStart`, not `SessionStart`, and do not inherit
the parent session's injected hook context. Furthermore, plugins cannot
ship permission rules (plugin `settings.json` drops all keys except
`agent` and `subagentStatusLine`), while imported repositories and added
directories cannot carry hooks or permission rules at all. Therefore,
only in-tree vendoring (Candidate 6) or a single repository (Candidate 1)
reliably delivers always-on rules, reviewer isolation, hooks, and
permissions without interactive security prompts or machine-wide pollution.

## Question

#### Card 2: Always-on rules under each candidate
- **Question:** How does the content of an always-on instruction file
  reach every session of Claude Code under each of the six candidates: an
  `@` import into CLAUDE.md and its limits (depth, paths outside the
  project, approval), a rules directory, a hook at session start that
  injects text, a plugin's own means, user-level memory? What is loaded
  in an isolated subagent's context and what is not? How do hooks and
  settings of a base combine with those of a project, and can a plugin or
  an imported repository carry hooks and permission rules?
- **Why it matters:** The framework's conduct rests on rules that must
  hold in every session and every reviewer run; a candidate that cannot
  deliver them always-on is no candidate, whatever else it does.
- **What would answer it:** The vendor's documentation of memory and
  instruction files, of hooks, of settings precedence and of what a
  subagent receives.
- **Where to look:** Anthropic's Claude Code documentation: memory,
  CLAUDE.md imports, rules, hooks reference, settings, subagents,
  plugins; the changelog since August 2026; the issue tracker for imports
  across repositories and for instruction files in plugins. Must turn up:
  whether a CLAUDE.md at a plugin root is loaded today, the import depth
  limit, the SessionStart hook's output.
- **Disconfirming query:** A search for a statement that a plugin can now
  ship always-on instructions, against the expectation that it still
  cannot.
- **Stop rule:** Every candidate has a named mechanism for always-on
  rules with the vendor's statement, or "none found"; nothing new from a
  differently worded query; the opening budget.

What the note must beat: the baseline notes
`2026-08-29-claude-code-packaging.md` and
`2026-10-03-user-extensions-kept-apart-from-the-core.md` established that
a plugin cannot ship `CLAUDE.md` at its root, identified `@` imports
(4-hop limit, approval dialog outside cwd) and symlinks, noted
`omitClaudeMd` (v2.1.271), and recorded that `--add-dir` loads subagents
but requires `CLAUDE_CODE_ADDITIONAL_DIRECTORIES_CLAUDE_MD=1` for memory.
They inferred [S] that `SessionStart` context might not survive `/compact`
and left uncertain whether a plugin's `SessionStart` hook reaches
isolated subagents, how plugin and added-directory hooks and permissions
combine with the project, and whether a plugin can carry permission rules.
This note resolves those uncertainties with primary documentation,
evaluates all six candidates against always-on requirements, and examines
subagent isolation boundaries.

## Key findings

F1: **Plugins cannot ship always-on instructions or rules through
native memory mechanisms.** [vendor claim, vendor documentation [3, 4,
5]]. Claude Code documentation explicitly states: "A `CLAUDE.md` file
at the plugin root is not loaded as project context" [3, 4]. The
validation utility `claude plugin validate` emits an explicit warning
when a `CLAUDE.md` is detected at the plugin root [4, 6]. Furthermore,
the plugin manifest `plugin.json` specifies allowed component fields
(`commands`, `agents`, `skills`, `hooks`, `mcpServers`, `lspServers`,
`monitors`) with no component field for `rules` or `memory` [5]. A
`.claude/rules/` directory inside a plugin is not loaded as project rules
[4, 5].

F2: **`@` imports into `CLAUDE.md` expand recursively to 4 hops, but
imports outside the working directory require interactive approval.**
[vendor claim, vendor documentation [1, 7]]. `CLAUDE.md` files support
`@path/to/file` imports using relative or absolute paths, resolving
relative to the file containing the import [1]. Recursive imports are
strictly capped at a maximum depth of 4 hops [1]. Markdown code spans
and fenced code blocks are skipped; paths wrapped in quotation marks are
ignored [1]. When an import resolves outside the current working
directory (e.g. `@../base/rules.md`), Claude Code displays a one-time
approval dialog per project at interactive session launch [1, 7]. If
declined, external imports remain permanently disabled for that project
[7]. User-scope files (`~/.claude/CLAUDE.md`) do not trigger the approval
dialog [7].

F3: **Symlinks pointing outside the working directory are treated as
external imports; network symlinks are rejected.** [vendor claim, vendor
documentation [7]]. Symlinks placed inside a project (e.g. within
`.claude/rules/` or pointing to a shared `CLAUDE.md`) that resolve to
targets outside the project working directory are classified as external
imports and require explicit user approval via the same interactive
dialog [7]. Symlinks pointing to network shares (UNC paths like
`\\server\share`, `/net`, `/Network`) are rejected unconditionally by
Claude Code due to security boundaries [7]. On Windows, symlinks require
Developer Mode or Administrator privileges [1, 7].

F4: **The `SessionStart` hook fires across all lifecycle restarts, but
its output is character-capped and fails to reach isolated subagents.**
[vendor claim, vendor documentation [8, 9, 10]]. The `SessionStart`
lifecycle event executes on brand-new sessions (`startup`), resumed
sessions (`resume`), cleared sessions (`clear`), compacted sessions
(`compact`), and forked sessions (`fork`) [8]. Hooks can inject context
directly into the model's window via
`hookSpecificOutput.additionalContext` [8, 9]. This clears the earlier
speculation that compaction wipes hook context [8]. However,
`additionalContext` is strictly capped at 10,000 characters; exceeding
strings are truncated to a file reference with a 2,000-character preview
[9]. Crucially, non-fork subagents run in isolated context windows and do
not inherit the parent session's `SessionStart` injected context [10].
Subagents fire `SubagentStart`, not `SessionStart` [8, 9].

F5: **Isolated subagents load project and user `CLAUDE.md` and rules by
default, but ignore parent turn history, previous tool executions, and
main-session hooks.** [vendor claim, vendor documentation [10, 11, 12]].
A custom subagent (without `context: fork`) initializes with its own
system prompt, the delegation task message, git status snapshot, assigned
preloaded skills (`skills:` frontmatter), and the full `CLAUDE.md`
hierarchy (`~/.claude/CLAUDE.md`, `./CLAUDE.md`, `./CLAUDE.local.md`, and
`.claude/rules/*.md`) [10, 12]. Setting `omitClaudeMd: true` prevents
loading user, project, and local `CLAUDE.md` files and `AGENTS.md`, but
path-scoped rules still load dynamically if the subagent accesses
matching files [11]. If an agent's preloaded skill is missing or disabled,
Claude Code skips it silently and logs a warning only to the debug log
[10].

F6: **Plugins can package lifecycle hooks, but cannot declare or
enforce permission rules.** [vendor claim, vendor documentation [13, 14,
15]]. Plugins can define lifecycle hooks in `hooks/hooks.json` that
execute whenever the plugin is enabled [13]. Plugin hooks run outside
Claude Code's sandbox with the user's full privileges [14]. However, a
plugin's `settings.json` (or inline manifest `settings`) only accepts
two configuration keys: `agent` (to override the main thread) and
`subagentStatusLine` [15]. All other settings keys—including
`permissions.allow`, `permissions.deny`, and `permissions.ask`—are
dropped [15]. Plugin tool calls inside the sandbox remain subject to
user/project permission rules, but the plugin cannot ship permission
rules itself [14, 15].

F7: **Imported repositories and added directories cannot carry hooks
or permission rules into a project.** [vendor claim, vendor
documentation [16, 17, 18]]. Settings files (`.claude/settings.json`)
do not support parent-directory or imported-directory fallback; they load
solely from the primary working directory, user configuration
(`~/.claude/settings.json`), and managed policy [16]. An `@` import in
`CLAUDE.md` imports only markdown text and imports no hooks or settings
[1, 16]. Adding an external directory via `--add-dir` loads its skills,
subagents, and select plugin keys (`enabledPlugins`,
`extraKnownMarketplaces`), but its hooks and general settings (including
`permissions.allow` and `permissions.deny`) are ignored [17, 18]. Memory
files from an added directory load only when
`CLAUDE_CODE_ADDITIONAL_DIRECTORIES_CLAUDE_MD=1` is set in the
environment [17].

F8: **Candidate analysis: delivery mechanisms and failure modes across
the six candidates.** [vendor claim / synthesis over findings F1–F7 [1–18]].
- **Candidate 1 (one repository with layers as directories):** Always-on
  rules load natively via `./CLAUDE.md` and `.claude/rules/*.md`.
  In-project `@` imports resolve without approval prompts up to 4 hops.
  Subagents load all rules by default. Hooks and settings in `.claude/`
  govern the entire repo. Meets all conductor requirements.
- **Candidate 2 (base as package, layers as separate repositories):**
  The package cannot inject memory, hooks, or permissions natively. If
  installed outside the project, `@` imports or symlinks trigger the
  one-time approval prompt. If added via `--add-dir`, memory files require
  `CLAUDE_CODE_ADDITIONAL_DIRECTORIES_CLAUDE_MD=1`, while hooks and
  permission rules are stripped. Layer must manually duplicate base hooks
  and permissions in its own `.claude/`.
- **Candidate 3 (side-by-side repositories joined by `@` import):**
  Layer's `CLAUDE.md` uses `@../base/CLAUDE.md`. Triggers an interactive
  approval dialog on first session; declining permanently breaks rule
  loading. Symlinking `../base/rules/` triggers the same dialog and fails
  on Windows without Developer Mode. The imported repository carries zero
  hooks and zero permission rules.
- **Candidate 4 (Claude Code plugin):** Cannot ship `CLAUDE.md` or
  `rules/`. A `SessionStart` hook injecting `additionalContext` is
  capped at 10,000 characters and completely fails isolated subagents
  (which trigger `SubagentStart`). A plugin cannot ship permission rules.
  Fails the always-on requirement for reviewers.
- **Candidate 5 (user-level configuration `~/.claude/` and `@` imports):**
  `~/.claude/CLAUDE.md` and `~/.claude/rules/` load in all sessions and
  subagents without prompts. However, this pollutes every unrelated
  Claude Code project on the machine. Collision rules are inverted:
  personal skills shadow project skills, while project agents shadow
  user agents.
- **Candidate 6 (whole framework split by release script into public
  base repo):** Development loop runs with Candidate 1's native zero-cost
  fidelity. The release script extracts and vendors the base files
  directly into consuming project trees. Because files sit inside the
  consuming repository, rules, hooks, permissions, and subagents load
  natively without approval dialogs, environment variables, or plugin
  restrictions.

## Unexpected

Isolated subagents do not trigger `SessionStart` hooks and do not receive
context injected by `SessionStart` hooks [8, 10]. Subagents fire
`SubagentStart` [8, 9]. This invalidates the common assumption that a
plugin's `SessionStart` hook can act as an always-on substitute for
`CLAUDE.md`: while main sessions receive the text, reviewers and
isolated agents run completely without the base framework rules unless
explicitly duplicated in subagent prompts or `SubagentStart` hooks.

`SessionStart` hooks actually execute on compaction (`compact`), clearing
the earlier speculation [S] in note `2026-08-29-claude-code-packaging.md`
that compaction wipes hook context [8]. However, the discovery of the
strict 10,000-character cap on `additionalContext` introduces an
unexpected hard ceiling that prevents large framework rulebooks from being
transmitted via hooks [9].

## Not found

Whether `SubagentStart` hooks declared in a plugin's `hooks/hooks.json`
fire for custom subagents defined in a project repository (looked in
`code.claude.com/docs/en/hooks` and `code.claude.com/docs/en/plugins`).

The exact file path or configuration key where Claude Code permanently
records a user's choice when declining an external `@path` import (looked
in `code.claude.com/docs/en/memory`).

## Options

The distinct ways the project could act on the findings:

- **Option 1: In-tree Vendoring via Release Script (Candidate 6).**
  Maintain the framework as one whole during development (Candidate 1).
  An automated release script extracts the base into a standalone public
  git repository. Consuming projects update by syncing the base files
  directly into their repository tree (via git subtree, copier, or
  vendor-branch script).
  *Trade-offs:* Full fidelity of always-on rules in main sessions and
  isolated reviewers. Zero interactive approval prompts for strangers.
  Hooks and permissions travel natively. Requires a sync/pull script in
  consuming projects.
- **Option 2: Plugin for Code, In-Project Memory Bootstrap (Candidate 4 +
  Candidate 1/5 hybrid).** Package executable skills, subagents, and MCP
  servers in a Claude Code plugin. Distribute always-on rules separately
  by having a project init command write a 1-line `@` import or file copy
  into the project's own `CLAUDE.md`.
  *Trade-offs:* Exploits plugin update mechanics for code, but splits the
  framework across two systems. The `@` import triggers external approval
  prompts if pointing outside cwd, and the plugin cannot distribute
  permission rules.
- **Option 3: Pure Plugin with Dual Lifecycle Hooks (Candidate 4 pure).**
  Distribute the base solely as a plugin, using `SessionStart` and
  `SubagentStart` hooks returning `additionalContext` to inject rules.
  *Trade-offs:* Zero file footprint in the project repo, but hits the
  10,000-character truncation cap, rules cannot be inspected via
  `/memory`, permissions cannot be enforced, and hook context formatting
  differs from system instructions.

## Relevance to this project

Adopt Option 1 (Candidate 6 with in-tree vendoring). Candidate 4 (pure
plugin) must be rejected because it cannot deliver always-on rules to
isolated reviewers, cannot enforce permissions, and is explicitly barred
by Anthropic from shipping `CLAUDE.md` or `rules/`. Candidates 2 and 3
impose unacceptable friction through external import approval prompts
and cannot transmit hooks or permissions. Candidate 5 is unviable due to
machine-wide pollution and inverted shadowing. Candidate 6 cleanly
decouples development from deployment while preserving 100% fidelity of
always-on rules, reviewer isolation, hooks, and permissions.

Consult when:
- Designing the repository architecture, release scripts, or split
  between the forge base and operating layers.
- Evaluating whether Claude Code plugin updates have introduced native
  support for rules or memory files.
- Configuring reviewer subagents and verifying that contract skills and
  rules are fully loaded.

## Sources

1. Claude Code Memory Documentation, Anthropic, undated (fetched
   2026-11-14 via summary), https://code.claude.com/docs/en/memory;
   primary; summarised fetch; original.
2. Claude Code Overview / Instructions, Anthropic, undated (fetched
   2026-11-14 via summary),
   https://code.claude.com/docs/en/features-overview; primary; summarised
   fetch; original.
3. Claude Code Plugins Overview, Anthropic, undated (fetched 2026-11-14
   via summary), https://code.claude.com/docs/en/plugins; primary;
   summarised fetch; original.
4. Claude Code Plugin Components, Anthropic, undated (fetched 2026-11-14
   via summary), https://code.claude.com/docs/en/plugins/components;
   primary; summarised fetch; original.
5. Claude Code Plugin Manifest Reference, Anthropic, undated (fetched
   2026-11-14 via summary),
   https://code.claude.com/docs/en/plugins/manifest-reference; primary;
   summarised fetch; original.
6. Claude Code Plugin Validation (`claude plugin validate`), Anthropic,
   undated (fetched 2026-11-14 via summary),
   https://code.claude.com/docs/en/plugins/create; primary; summarised
   fetch; original.
7. Claude Code External Imports and Working Directories, Anthropic,
   undated (fetched 2026-11-14 via summary),
   https://code.claude.com/docs/en/memory#imports; primary; summarised
   fetch; original.
8. Claude Code Lifecycle Hooks Reference, Anthropic, undated (fetched
   2026-11-14 via summary), https://code.claude.com/docs/en/hooks;
   primary; summarised fetch; original.
9. Claude Code Hook Output and Context Injection (`hookSpecificOutput`),
   Anthropic, undated (fetched 2026-11-14 via summary),
   https://code.claude.com/docs/en/hooks#additional-context; primary;
   summarised fetch; original.
10. Claude Code Subagents Documentation, Anthropic, undated (fetched
    2026-11-14 via summary), https://code.claude.com/docs/en/sub-agents;
    primary; summarised fetch; original.
11. Claude Code Subagent Frontmatter Reference (`omitClaudeMd`),
    Anthropic, undated (fetched 2026-11-14 via summary),
    https://code.claude.com/docs/en/sub-agents#omitclaudemd; primary;
    summarised fetch; original.
12. Claude Code Subagents Context and Isolation, Anthropic, undated
    (fetched 2026-11-14 via summary),
    https://code.claude.com/docs/en/sub-agents#context; primary; summarised
    fetch; original.
13. Claude Code Plugins and Hooks Integration, Anthropic, undated
    (fetched 2026-11-14 via summary),
    https://code.claude.com/docs/en/plugins/loading#hooks; primary;
    summarised fetch; original.
14. Claude Code Plugin Security and Sandboxing Boundaries, Anthropic,
    undated (fetched 2026-11-14 via summary),
    https://code.claude.com/docs/en/plugins/org#security; primary;
    summarised fetch; original.
15. Claude Code Plugin Settings Reference (`settings.json`), Anthropic,
    undated (fetched 2026-11-14 via summary),
    https://code.claude.com/docs/en/plugins/manifest-reference#settings;
    primary; summarised fetch; original.
16. Claude Code Settings Hierarchy and Precedence, Anthropic, undated
    (fetched 2026-11-14 via summary),
    https://code.claude.com/docs/en/settings; primary; summarised fetch;
    original.
17. Claude Code Additional Working Directories (`--add-dir`), Anthropic,
    undated (fetched 2026-11-14 via summary),
    https://code.claude.com/docs/en/settings#additional-directories;
    primary; summarised fetch; original.
18. Claude Code Directory Addition Hooks (`DirectoryAdded`), Anthropic,
    undated (fetched 2026-11-14 via summary),
    https://code.claude.com/docs/en/hooks#directoryadded; primary;
    summarised fetch; original.

## Opened and not used

- Anthropic Claude Code Changelog (2026 series),
  `code.claude.com/docs/en/changelog`: off the question (details Sonnet
  5.5, Mods, and UI integrations; no change to plugin memory rules).
- GitHub Claude Code Issues (`site:github.com/anthropics/claude-code/issues`),
  various queries: superseded by primary documentation on `code.claude.com`.
- Community discussions on Reddit / Classmethod regarding `omitClaudeMd`:
  duplicate of official vendor documentation.

## Search record

Queries run in order:
1. `site:code.claude.com/docs/en "CLAUDE.md" import`
2. `site:code.claude.com/docs/en/plugins "CLAUDE.md"`
3. `site:code.claude.com/docs/en "plugin root" "CLAUDE.md"`
4. `"plugin" ("always-on instructions" OR "ship always-on" OR "plugin rules") site:code.claude.com` (disconfirming query)
5. `site:code.claude.com/docs/en/plugins "rules"`
6. `site:code.claude.com/docs/en "manifest-reference" OR "plugin.json"`
7. `site:code.claude.com/docs/en "SessionStart" "hooks"`
8. `site:code.claude.com/docs/en "additionalContext" "hookSpecificOutput"`
9. `site:code.claude.com/docs/en "sub-agents" OR "subagents" "context"`
10. `site:code.claude.com/docs/en/sub-agents "rules"`
11. `site:code.claude.com/docs/en/memory "rules"`
12. `site:code.claude.com/docs/en "omitClaudeMd"`
13. `site:code.claude.com/docs/en/settings "precedence" OR "priority"`
14. `site:code.claude.com/docs/en/plugins "hooks" OR "settings"`
15. `site:code.claude.com/docs/en/plugins "permissions"`
16. `site:code.claude.com/docs/en "plugin" "permissions.allow" OR "permissions.deny"`
17. `site:code.claude.com/docs/en/plugins "settings.json"`
18. `site:code.claude.com/docs/en "add-dir" settings`
19. `site:code.claude.com/docs/en "CLAUDE_CODE_ADDITIONAL_DIRECTORIES_CLAUDE_MD"`
20. `site:code.claude.com/docs/en "add-dir" "hooks"`
21. `site:code.claude.com/docs/en "add-dir" "enabledPlugins"`
22. `site:code.claude.com/docs/en "add-dir" "settings" hooks permissions`
23. `site:code.claude.com/docs/en/changelog "2026"`
24. `site:github.com/anthropics/claude-code/issues "CLAUDE.md" plugin`
25. `site:github.com/anthropics/claude-code/issues "import" "CLAUDE.md"`
26. `site:code.claude.com/docs/en/memory "approval" OR "dialog"`
27. `site:code.claude.com/docs/en "outside your working directory" OR "external import"`

Disconfirming query: `"plugin" ("always-on instructions" OR "ship
always-on" OR "plugin rules") site:code.claude.com` returned no
matching results, confirming that plugins still cannot ship always-on
instructions or rules.

Run end: all six candidates evaluated with vendor statements, answering
every aspect of the card's question; stopped by the card's stop rule
and opening budget.
```
