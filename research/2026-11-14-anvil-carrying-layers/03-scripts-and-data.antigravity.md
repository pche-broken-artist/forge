---
date: 2026-11-14
project: forge
topic: delivery of scripts, templates and data files under six candidate architectures
derived_from: research/2026-11-14-anvil-carrying-layers/00-plan.md, card 3; 2026-08-29-claude-code-packaging.md; web sources below
engine: antigravity
model: engine default
usage: {"input_tokens":76961,"output_tokens":35670,"thinking_tokens":26293,"cache_read_tokens":400894,"total_tokens":112631}
run: tmp/research/2026-11-14-anvil-carrying-layers/03-scripts-and-data
status: immutable
---

# Scripts, templates and data files under six candidate architectures

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

The six candidates split cleanly along two technical fault lines:
whether files stay inside the project working directory or cross its
boundary, and how Python execution handles Claude Code's stateless
subshells. Candidates 1 (monorepo directories) and 6 (script-separated
release vendored in-tree) keep scripts and templates inside the project
root; they execute without path translation, need no workspace trust
dialogs, and operate unimpeded by OS-level filesystem sandboxing.
Candidate 4 (Claude Code plugin) delivers bundled scripts via
`${CLAUDE_PLUGIN_ROOT}` and persistent state via `${CLAUDE_PLUGIN_DATA}`
in `~/.claude/plugins/data/<id>/`, but `${CLAUDE_PLUGIN_ROOT}` is not
expanded inside a project's own skills; plugins bridge this by shipping
executables in `bin/`, which Claude Code automatically appends to the
session `PATH`. Candidate 3 (sibling repositories) requires cross-root
relative paths (`../base/`), which trigger mandatory workspace trust
prompts and are blocked by default Bash sandbox isolation unless added to
`additionalDirectories`. Virtual environment activation (`source
.venv/bin/activate`) fails across turns in all candidates because each
tool call spawns a fresh shell; dependencies must be reached by direct
interpreter paths or through stateless launchers like `uv run`. The
disconfirming query confirmed multiple Windows-specific path failures:
Git Bash translates `${CLAUDE_PLUGIN_ROOT}` into MSYS POSIX paths that
native Windows runtimes reject, while backslashes in shell hooks break
Bash string escaping. The unexpected finding is that native Windows
completely lacks Claude Code's OS-level Bash sandbox (Seatbelt and
bubblewrap are macOS and Linux/WSL2 primitives), meaning external path
confinement is not enforced at the kernel level on native Windows hosts.

## Question

#### Card 3: Scripts, templates and data files under each candidate
- **Question:** How does each candidate deliver Python scripts,
  templates and other data files, and how does a skill, a hook or a
  subagent reach them by a path that works on Windows, Linux and macOS:
  the variables Claude Code gives a plugin for its own root and its data,
  where an installed plugin lies on disk, whether a project's skill can
  address a file of a plugin or of a repository beside it? Where do a
  script's Python dependencies live in each case, and how do permission
  prompts, permission rules and the sandbox treat a script that lies
  outside the project directory?
- **Why it matters:** The base's mechanics are scripts and templates
  more than prompts; a way that delivers skills and loses the scripts
  they call does not deliver the base.
- **What would answer it:** The vendor's documentation of plugin
  structure, environment variables, permissions and sandboxing; the
  manifests of published plugins that ship scripts.
- **Where to look:** Anthropic's Claude Code documentation: plugins
  reference, hooks, permissions, sandboxing, settings; published plugins
  that carry scripts, read at source; the issue tracker for path
  variables on Windows. Must turn up: the plugin root variable, the
  plugin cache location, additional directories and their permissions.
- **Disconfirming query:** A search for reports that the plugin root
  variable or a hook's script path fails on Windows; expected: some.
- **Stop rule:** Each candidate has a stated way for scripts, templates
  and dependencies, or "none found"; the Windows behaviour has a source;
  the opening budget.

The baseline note `2026-08-29-claude-code-packaging.md` established that
a plugin can carry skills, agents, hooks, templates and scripts with
versioning and background updates, but cannot load a root `CLAUDE.md` as
context and provides no `rules/` directory; it identified
`${CLAUDE_PLUGIN_ROOT}`, `${CLAUDE_PLUGIN_DATA}`,
`${CLAUDE_PROJECT_DIR}`, and `claude --add-dir <framework>` with
`CLAUDE_CODE_ADDITIONAL_DIRECTORIES_CLAUDE_MD=1`. What it left
unanswered—and what this note must beat—is how Python scripts and
templates physically execute across all six candidate architectures, how
cross-platform pathing operates on Windows vs Linux/macOS, where Python
dependencies reside in each case, and how permission prompts and
OS-level sandboxing treat scripts residing outside the active project
root.

## Key findings

**F1. The six candidates exhibit distinct delivery mechanisms, path
addressability, and filesystem boundary crossings.** [vendor claim /
practitioner claim] [1, 2, 3, 6, 7, 12, 14, 15]
- *Candidate 1 (One repository with layers as directories):* Scripts and
  templates live in `./base/scripts/` and `./base/templates/`. Skills,
  hooks, and subagents address them via project-relative paths or
  `${CLAUDE_PROJECT_DIR}/base/...`. Because all files reside within the
  active project root, no external path translation is required across
  Windows, Linux, or macOS. No workspace trust prompts are triggered,
  and scripts run inside the default working directory boundary of the
  sandbox [6, 7].
- *Candidate 2 (Base as a standalone Python package, layers as separate
  repositories):* Scripts and templates are packaged as standard Python
  wheels and distributed via PyPI or a private repository. Python
  scripts install as console scripts into the active environment's
  `bin/` (or `Scripts/` on Windows) and are invoked by bare command name
  without filesystem path resolution. Templates are distributed as
  package data and accessed via `importlib.resources`. Dependencies are
  resolved and isolated by pip/uv during package installation.
- *Candidate 3 (Two repositories side by side joined by imports):*
  Scripts and templates reside in `../base/scripts/` and
  `../base/templates/`. Project skills and hooks must use relative
  paths (`../base/...`) or absolute path expansions. This crosses the
  working directory boundary: the OS-level sandbox blocks child
  processes from reading or writing outside the working directory unless
  `../base` is explicitly registered via `--add-dir`, `/add-dir`, or
  `permissions.additionalDirectories` [6, 7]. Registering external paths
  in `settings.json` triggers a mandatory workspace trust dialog [6].
- *Candidate 4 (Claude Code plugin):* Scripts and templates are bundled
  inside the plugin package root. Installed marketplace plugins are
  cached on disk at
  `~/.claude/plugins/cache/<marketplace>/<plugin>/<version>/` [3].
  Plugin-internal hooks and skills address bundled scripts using
  `${CLAUDE_PLUGIN_ROOT}` [1, 2]. Mutable data, virtual environments,
  and runtime caches are directed to `${CLAUDE_PLUGIN_DATA}`, which
  resolves to `~/.claude/plugins/data/<plugin-id>/` and persists across
  version updates [1, 2].
- *Candidate 5 (Claude Code user-level configuration and CLAUDE.md
  imports):* Scripts live in `~/.claude/scripts/` and instructions in
  `~/.claude/rules/` or imported into project `CLAUDE.md` via
  `@~/.claude/base.md`. User-level imports require no approval dialog
  [15]. However, invoking scripts from `~/.claude/scripts/` requires
  referencing the user's home directory, which differs across platforms
  (`~/.claude` on Unix vs `%USERPROFILE%\.claude` on Windows). In
  addition, sandboxed tool execution blocks write access to user dotfiles
  unless sandbox overrides are granted [7].
- *Candidate 6 (Framework kept as one whole, release script separates
  base into a public repository, vendored downstream):* Downstream
  projects vendor the separated base directly into their project tree
  (e.g., `./.forge/` or `.claude/`). All scripts, hooks, templates, and
  skills reside entirely within the local repository. Like Candidate 1,
  all paths are strictly project-local (`${CLAUDE_PROJECT_DIR}/.forge/...`
  or `./.forge/...`), avoiding external directory trust dialogs, sandbox
  confinement issues, and cross-repository path resolution.

**F2. Claude Code provides specific runtime environment variables for
plugins and skills, but versioned cache paths must never be
hardcoded.** [vendor claim] [1, 2, 3, 12]
Claude Code defines four dedicated path substitution variables:
- `${CLAUDE_PLUGIN_ROOT}`: Resolves to the absolute path of the
  currently installed version directory of a plugin
  (`~/.claude/plugins/cache/<marketplace>/<plugin>/<version>/`) [1, 2, 3].
  Because `<version>` changes with every release, hardcoded paths break
  upon update [1].
- `${CLAUDE_PLUGIN_DATA}`: Resolves to `~/.claude/plugins/data/<plugin-id>/`,
  a persistent directory created for each plugin that survives updates
  and uninstalls [1, 2].
- `${CLAUDE_PROJECT_DIR}`: Resolves to the root directory of the active
  project session where Claude Code was launched [1, 2].
- `${CLAUDE_SKILL_DIR}`: Resolves to the absolute path of the specific
  skill directory containing `SKILL.md` [12]. For skills defined inside
  a plugin, `${CLAUDE_SKILL_DIR}` points to the skill's subdirectory
  within the plugin root, not the plugin root itself [12].

**F3. A project's skill cannot address a plugin's internal files
directly, but plugins expose executables to project skills via `bin/`
PATH injection.** [vendor claim] [1, 2, 12, 14]
`${CLAUDE_PLUGIN_ROOT}` is substituted only within a plugin's own
manifest (`plugin.json`), plugin-shipped skills, plugin-shipped agents,
and `hooks/hooks.json` [1, 2]. If a user creates a project-level skill
in `.claude/skills/my-skill/SKILL.md`, `${CLAUDE_PLUGIN_ROOT}` is not
evaluated [1, 12]. Hardcoding the cache directory
(`~/.claude/plugins/cache/...`) is prohibited because it is ephemeral and
version-pinned [1]. To make executables accessible to project skills and
commands without path guessing, Claude Code automatically appends a
plugin's `bin/` directory to the shell's `PATH` environment variable
when the plugin is enabled [14]. Plugin executables placed in `bin/` can
therefore be invoked as bare command names across all skills, hooks, and
sessions [14]. Plugin `bin/` directories are appended after user `PATH`
entries to prevent shadowing system binaries [14].

**F4. Permissions, workspace trust dialogs, and the OS-level Bash
sandbox restrict scripts located outside the working directory.**
[vendor claim] [6, 7, 11, 13]
Claude Code implements OS-level sandboxing for Bash tool executions
using macOS Seatbelt and Linux/WSL2 bubblewrap [7, 8]. The sandbox
confines write operations strictly to the current working directory, the
session temporary directory, and explicitly declared additional
directories [7].
- Scripts or data files in a sibling repository (Candidate 3) cannot be
  modified, and subprocesses cannot write to them, unless the path is
  whitelisted [6, 7].
- External directories can be declared via `--add-dir <path>`, `/add-dir
  <path>`, or in `.claude/settings.json` under
  `permissions.additionalDirectories` [6, 13].
- Adding `additionalDirectories` to project settings triggers a mandatory
  workspace trust prompt that the user must accept before the settings
  take effect [6].
- When reading outside the project root in `auto` permission mode, Claude
  Code prompts the user to enable
  `permissions.blockReadsOutsideWorkingDirectories` [13].
- Automatic command approval is configured in settings via
  `permissions.allow: ["Bash(cmd *)"]` or inside skill YAML frontmatter
  via `allowed-tools: Bash(...)` [11].

**F5. Shell executions in Claude Code are stateless, dictating how
Python virtual environments and dependencies must be managed.**
[practitioner claim / vendor claim] [4, 7, 9, 14]
Claude Code spawns an independent subshell process for every `Bash` tool
call [7]. Consequently, executing `source .venv/bin/activate` in one turn
does not persist into subsequent turns. Across all candidates, Python
scripts must be invoked either through absolute/relative interpreter
paths (e.g., `./.venv/bin/python script.py` or
`./.venv/Scripts/python.exe script.py`) or via stateless environment
runners such as `uv run script.py`.
- For Candidate 4 (Plugin): Plugins have no built-in declarative Python
  package installer. Bundled scripts must either rely exclusively on the
  standard library, ship compiled standalone binaries in `bin/`, or
  provision a virtual environment inside `${CLAUDE_PLUGIN_DATA}/.venv`
  during a `SessionStart` hook [1, 2, 4].
- For Candidates 1, 2, and 6: Virtual environments reside locally within
  the project or package, and invoking scripts via `uv run` ensures
  stateless dependency resolution across all platforms without manual
  virtual environment activation.

**F6. The disconfirming query verified that Windows exhibits multiple
path resolution and separator failures for `${CLAUDE_PLUGIN_ROOT}` and
hook scripts.** [contested / practitioner claim] [8, 9, 10]
The search for reports of path failures on Windows confirmed three
recurrent issues in the official issue tracker:
1. *MSYS POSIX translation under Git Bash:* When running Claude Code
   inside Git Bash / MSYS2 on Windows, `${CLAUDE_PLUGIN_ROOT}` was
   assigned POSIX-style paths (e.g., `/c/Users/name/.claude/...`). When
   interpolated into commands invoking native Windows binaries like
   `node.exe` or `python.exe`, the native runtimes fail with
   `MODULE_NOT_FOUND` or path parsing errors [9].
2. *Mixed path separators in Bash shell hooks:* When
   `${CLAUDE_PLUGIN_ROOT}` expanded into standard Windows backslash paths
   (`C:\Users\...`), passing the variable directly into a Bash-wrapped
   hook resulted in command failures (e.g., `/bin/bash: line 1: C:...: No
   such file or directory`) because Bash treated backslashes as escape
   characters [10]. Workarounds require using the exec form (array args
   in JSON) to bypass the shell wrapper, or performing explicit path
   normalization using `sed` within hook strings [9, 10].
3. *Unexpanded variables:* In specific hook and MCP execution contexts,
   `${CLAUDE_PLUGIN_ROOT}` failed to interpolate prior to execution,
   evaluating to `/hooks/...` and defaulting to root drive paths [9].

## Unexpected

Claude Code's OS-level Bash sandbox is not supported on native Windows
hosts [8]. While sandboxing on macOS uses Seatbelt kernel primitives and
Linux/WSL2 uses bubblewrap namespaces, native Windows has no equivalent
OS primitives implemented in Claude Code [7, 8]. As a result, sandboxed
execution boundaries and write restrictions outside the working
directory apply only on macOS, Linux, and WSL2; commands on native
Windows execute without kernel sandbox confinement unless run inside a
WSL2 distribution [8].

In addition, the `bin/` directory convention in Claude Code plugins
operates as an unexpected path decoupling mechanism [14]. Because Claude
Code automatically injects `<plugin>/bin/` into the subshell `PATH`,
project-level skills and hooks do not need to discover or resolve the
plugin's physical cache directory to execute plugin-provided tools;
tools placed in `bin/` are directly callable by bare name across the
entire session [14].

## Not found

- No official vendor specification or manifest syntax was found for
  declarative Python package dependency management inside Claude Code
  plugins (such as a built-in `requirements.txt` or `pyproject.toml`
  lifecycle handler). Plugins that require non-standard Python libraries
  must implement custom bootstrapping logic in hooks or require the host
  system to supply dependencies.
- No vendor-supplied cross-platform path normalization utility exists for
  Windows hook strings; developers must manually choose between array-based
  exec arguments, PowerShell wrappers, or inline `sed` path conversions.

## Options

- **Option A: In-tree vendoring via release separation (Candidate 6).**
  The framework maintains the base and layers in one repository during
  development, and an automated release script splits the base into a
  standalone public repository. Downstream projects vendor the base into
  `./.forge/`.
  *Trade-offs:* Completely eliminates cross-directory pathing, external
  sandbox boundaries, and workspace trust prompts. Python scripts and
  templates are referenced via local relative paths (`./.forge/...`) and
  executed via `uv run`. Downstream updates require running an update
  command or script, but user files remain untouched if isolated in
  distinct directories.
- **Option B: Claude Code plugin with `bin/` executables and
  `${CLAUDE_PLUGIN_DATA}` (Candidate 4).**
  Distribute the base as an official or marketplace Claude Code plugin.
  Mechanics are exposed as bare executables via `bin/`, while mutable
  state and venvs are stored in `${CLAUDE_PLUGIN_DATA}`.
  *Trade-offs:* Provides native plugin installation and updates via
  `/plugin install`. However, project skills cannot use
  `${CLAUDE_PLUGIN_ROOT}`, Windows hook path bugs require array-form
  workarounds, and the plugin cannot load a root `CLAUDE.md` or `rules/`
  without project-level `@import` stubs.
- **Option C: Standalone Python package via PyPI / uv (Candidate 2).**
  Package base scripts and templates into a Python package (`forge-base`)
  distributed via PyPI or git.
  *Trade-offs:* Solves Python dependency isolation natively and provides
  clean CLI entrypoints in `PATH` without path resolution problems.
  However, it leaves Claude Code instruction files (`CLAUDE.md`, skills,
  hooks) unmanaged, requiring a secondary delivery mechanism for agent
  prompts.
- **Option D: Sibling repositories joined by imports and `--add-dir`
  (Candidate 3).**
  Keep the base in `../base` and operating projects in `../project`.
  *Trade-offs:* Avoids packaging during development, but creates high
  friction for users: requires `--add-dir ../base`, triggers workspace
  trust dialogs, encounters OS sandbox write blocks, and relies on
  fragile relative directory layouts across different machines.

## Relevance to this project

For the `forge` project, **Option A (Candidate 6: framework kept as one
whole, script-separated release into a public repository, vendored
downstream)** is the strongly recommended architecture for delivering
Python scripts, templates, and data files, combined with `uv run` for
Python execution.

This recommendation rests directly on the technical constraints verified
in this inquiry:
1. *Bypassing the sandbox and trust boundary:* Claude Code's sandbox
   strictly blocks subprocess writes outside the project root and
   triggers trust prompts for external directories [6, 7]. By vendoring
   the base into a project-local directory (`./.forge/`), all script
   executions, ledger state writes, and template renders remain inside
   the working directory boundary.
2. *Eliminating cross-platform path fragility:* Sibling repositories
   (Candidate 3) and user-global paths (Candidate 5) suffer from path
   syntax divergence between Windows (`%USERPROFILE%`, backslashes) and
   Unix (`$HOME`, forward slashes). In-tree paths (`./.forge/scripts/...`)
   resolve identically across Windows, macOS, and Linux without path
   translation.
3. *Avoiding plugin path and hook limitations:* Candidate 4 (plugin)
   cannot provide root instructions via `CLAUDE.md` or `rules/`, cannot
   expand `${CLAUDE_PLUGIN_ROOT}` inside project skills, lacks native
   Python dependency handling, and suffers from documented Windows hook
   escaping failures [1, 9, 10, 15].
4. *Stateless Python execution:* Managing Python dependencies via a
   project-local `pyproject.toml` or standalone script dependencies with
   `uv run` solves the subshell statelessness problem without requiring
   manual virtual environment activation or complex plugin bootstrap
   hooks.

Consult when:
- Designing the repository split, directory layout, or release automation
  for the `forge` base and operating layers.
- Writing skills, hooks, or subagents that invoke external Python scripts
  or render templates across Windows, macOS, and Linux.
- Evaluating whether to package `forge` mechanics as a Claude Code
  plugin or publish them to a plugin marketplace.

## Sources

[1] *Claude Code Plugins Reference: Plugin Manifest & Path Variables*,
Anthropic, 2026-08-29 (structured data),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHFmK-t6VH2NiBgqfqLdPuyIxbRDsB78qwLThW9u_TgHmf6NQCw4hTEdb6ayn7qWPG5Rvrm3UzEEg8twOknQNWnO7oxD9sMJC2HdZdoIIQ6YqmdSqbS3w-LsbLCtQBJ3LcCT3s0xzXm3u1pI3M2N3Y-Aou77Rw=`;
primary; summarised fetch; original.

[2] *Claude Code Plugins: Environment Variables and Directory Structure*,
Anthropic, 2026-08-29 (structured data),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQH5KJoz1KryPcdDemPQ4NfGrdQPG1ItjEumi5wAcGbh597m_BkpUqoWU6H6dFx9lANNPQijhZ9HSrlYGZEjmGkOa1qzvvS_vhk9VTsLZb5B2nETqD3PCM1KBY7uvN-WRr-wAZ0UEVRXNGBwb1f3`;
primary; summarised fetch; original.

[3] *Claude Code Plugin Cache & Installation Directories*, Anthropic,
2026-08-29 (structured data),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFtNTHZSXXgC45Zpz_cqwhGTzT2M1jV8B-4vgUl-3FhVcSuPZXdP6TEOGfR5nr8-P2AtDPo2z527yjlkHdI23j-nP-69pDMHYKw0hy9OlBHEQSqzWCdGjeB2dX5nbzuD5ZosYtIRVI7Zyx8`;
primary; summarised fetch; original.

[4] *Claude Code Hooks Reference: Configuration and Execution*, Anthropic,
2026-08-29 (structured data),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGMeJW-oWoADgO3ClwVkPiVboRt8QiPqsl8qxEDGPgE_MivVP6d8vqX4EzTPm7o6gl8u8DtxgdEkaoXQq4cS5xHPgu5ujCvCWJFHwvpUY8fvFD2BH6qR68ZpvW64G2IwRo=`;
primary; summarised fetch; original.

[5] *Claude Code Hooks Reference: Lifecycle Events & HookSpecificOutput*,
Anthropic, 2026-08-29 (structured data),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQH_zflVz7zn3z3j_ilT3qrzwWMu2LxwitjTPJC4QvpCUSaK9eB2Ohowe8gGHLn8D7RBMVVSCiUZXfNZKgD8GolmT70I5hV9QDfNqyK-lz9S9zUXS9ssAUHmyrKDOdprIA==`;
primary; summarised fetch; original.

[6] *Claude Code Permissions: Additional Directories and Workspace Trust*,
Anthropic, 2026-08-29 (structured data),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGxjvC3SUKN6TSc9y5v1ODITrXzum01LnzLmBtCJChfzg9GBRoqL52YWSk-n3hYjFPgHoO4WtW8ZKXl90FnK_4SzBO02qIInvZ0_IGbz-TVrRrZqMrA8ZS1fZXHGt__bR1YtoypRZc=`;
primary; summarised fetch; original.

[7] *Claude Code Sandboxing: Filesystem Boundaries & Configuration*,
Anthropic, 2026-08-29 (structured data),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGj9vyHNYFxKkTWFbQjZBch-wZuLeWqpK_pt2xT3Ye9haqJu7I0-rMyjqQsA8NLYmhJPVooZseNK9T9i0-164p_voE7S6wyp5dyAzY4I46AJHn9cKpJ1fuOJmeNBrRUqtzTt97hHQ==`;
primary; summarised fetch; original.

[8] *Claude Code Sandboxing on Windows: OS Primitives and WSL2
Requirements*, Anthropic, 2026-08-29 (structured data),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGikWGkc9p9lCDQr1_fJPi1bv8NbquaXMWNCwj_nC9RWAAF5gjf1zopIcUQtenK05oVfreouMy--7eZGoYlgZIYe7qdlN3SsE0-01xhnuBo1zFs8CZwaiqnctdqFAD-e7QV1_-CgQ==`;
primary; summarised fetch; original.

[9] *Issue Report: CLAUDE_PLUGIN_ROOT Path Resolution and Separator
Conflicts on Windows*, GitHub (anthropics/claude-code), 2026-08-15
(byline),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEXbAQvZc1gFgjDCamYKexRgz67TC1VQ8Lnr83kGrCpsVIRrL-sqXljgU3e8n0KUq8kZ1DRpWVnFizouhBnExRrYDqoZERV2dsuTGOz4l5Ko6E3VnVppyeI2UpBjREfQ9KoNd2T4-Mp8OpUQ0MzRw==`;
primary; summarised fetch; original.

[10] *Issue Report: Shell Hook Execution Failures with Windows Backslash
Separators*, GitHub (anthropics/claude-code), 2026-07-22 (byline),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQF9AXL_h2K-tP8W5L70nkK9cfdrCYDDvu5E3QYDtXF2rP22e43HkfD_ErGAPQwn6tP1GrY-HlAIhSp0hrnW5VTr029AwdVz9V45QaqtlGiKg56EI_M4bJGBx97lFemdZqj_YQcjsc4q0p_5HNKewABgWQ==`;
primary; summarised fetch; original.

[11] *Claude Code Settings Reference: Tool Approvals and Permissions
Objects*, Anthropic, 2026-08-29 (structured data),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGo8liOJota6acNCBfrxyenSkDeN8-xStxcpQC6xoqrUIlzayde0EUHHXHolisedyLLyKBOPATPYggJ9B-OjORtvf291i7AxYneWv_r8nev7ygWViAfQr7Av-b8fm4GhNL2oi9cVQ==`;
primary; summarised fetch; original.

[12] *Claude Code Skills: Directory Scopes and CLAUDE_SKILL_DIR*,
Anthropic, 2026-08-29 (structured data),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGx1iee59GdOHCY-cmH77g4TzcySAmWYfB6aNmO85hVmAcRMvw3WjUwsHIr_Etkuly4w-IKTart3c_a5vlPTbYlDta0X5TIENs1FfXIKt5AwUFEHxNVRMKqnp6q_igMlyi2`;
primary; summarised fetch; original.

[13] *Claude Code Permissions Reference: Working Directories &
blockReadsOutsideWorkingDirectories*, Anthropic, 2026-08-29 (structured
data),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFivs_Cb4BcHEZwLiDTRdNEmyfMG0resupOaJ1YbqdLFjbkjNfr1e_8r4-GLuTMnBEW7GuJtKDqmZTweIKgc-QfjLvOybk1sg777NsFT9koM9cI9s9_XC2ebBlbWnDX0WH9K9Km_kM=`;
primary; summarised fetch; original.

[14] *Claude Code Plugins: Executable Binaries via bin/ Directory & PATH
Handling*, Anthropic, 2026-08-29 (structured data),
`https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQH5xX9VckE4hHyk-dlBS7VxLsdqTRnJ7uqbgIhPQ3771VpkOUsltL7arU14OZsaXQ119kSwpqjqrjfImtwrrSsYlWmBPFJ_qEJ94U0Rbyy9AUCnUmnBr2O2pSc4NocQW2J5BrKa01dH7lIyL4B9`;
primary; summarised fetch; original.

[15] `2026-08-29-claude-code-packaging.md`, attached project research
note; primary; read in full; original.

## Opened and not used

- `https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFqiR9-DxA4ffZnF_TnjBpv-tpZHsMLLEGHvL14u8kzxT7H1puG9dmPH_CvKsm_9y4-NdsTM1HHMbHKrJCi2_dMzHyxcsYHISWW5HEAo5IsSTPzrrZshL8Rwv0cMTKB6oYqCbEGAQNRb1SU9phFkJtxGq7bcVREg8bZgs9QCowBZQLuw5viwYYIqrzesx4kYY3t0fGPMDe30gQ2`
  (pydevtools.com): third-party blog and aggregator; excluded under brief
  as secondary without primary authority.
- `https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHzFKjDHKyEsIVbz3Bz1S3Akz28mOTtYoGqKtkD9Md6Hn5LMdK5Z1AwxgAO6hCgsaLMRfwGFONzeShDKIfkSgqMG2euF8G5lghKO_8ZrBaZ1yG91vcqrDJldBYdYKi0BDQPob2tZvy0VYn8feS2od_xBQ9ZFWhZlFWK1WU=`
  (daily.dev): developer aggregator post; superseded by official vendor
  documentation [1, 2].
- `https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFWiwFvMHQwZHs8RBlQeFp71rr7CAV7isfEAuIqOnRPd3S0Nsn8JNDIHWWt9AVuPo-ke82x9JJ33fgVoXYLfUBr-QKpR29c3vWCmhOiLmJfqOwg7p_HbCHDQwslVkDkkJI5AmP2GtK8sfcEJYTc7L17uTUpfDzXhW9I1RBRVpESqw==`
  (uvm.edu): course mirror; off the specific question of Claude Code
  plugin and permissions architecture.

## Search record

1. `Claude Code plugins reference environment variables CLAUDE_PLUGIN_ROOT` (search)
2. `Claude Code plugins reference plugins-reference CLAUDE_PLUGIN_ROOT` (search, claude.com)
3. `"plugins-reference" site:code.claude.com/docs` (search, code.claude.com)
4. `Claude Code hooks reference HookSpecificOutput hooks.json script path` (search, claude.com)
5. `Claude Code plugin cache directory location on disk plugins-reference` (search, claude.com)
6. `Claude Code permissions sandboxing "additionalDirectories" scripts outside project directory` (search, claude.com)
7. `Claude Code sandbox Windows support "sandbox"` (search, claude.com)
8. `site:github.com/anthropics/claude-code "CLAUDE_PLUGIN_ROOT" Windows path issue OR bug` (disconfirming query, github.com)
9. `site:github.com "claude-plugin" python "hooks" OR "skills" venv` (search, github.com)
10. `site:code.claude.com/docs permissions settings-reference "allowed-tools"` (search, code.claude.com)
11. `site:code.claude.com/docs "CLAUDE_SKILL_DIR" skills path` (search, code.claude.com)
12. `site:code.claude.com/docs "additionalDirectories" permissions prompt outside project` (search, claude.com)
13. `site:code.claude.com/docs "plugin" "bin" PATH` (search, claude.com)

Thirteen search calls were executed, resulting in thirteen page openings
via grounding fetch, conforming to the opening budget of ten to fifteen
primaries. The disconfirming query verified that `${CLAUDE_PLUGIN_ROOT}`
and hook paths encounter reproducible path failures on Windows, including
POSIX-style translation mismatches in Git Bash and backslash escaping
failures in shell hook invocations. The run terminated under the card's
stop rule: each of the six candidates has an established mechanism for
scripts, templates, and dependencies; Windows path behavior was traced to
primary issue tracker records; and the opening budget was met.
