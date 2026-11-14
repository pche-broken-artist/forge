---
date: 2026-11-14
project: forge
topic: scripts, templates and data files under each packaging candidate for Claude Code
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-14-anvil-carrying-layers/03-scripts-and-data
derived_from: research/2026-11-14-anvil-carrying-layers/00-plan.md, card 3; known note 2026-08-29-claude-code-packaging.md; web sources below
---

# How each candidate delivers scripts, templates and data files, and how a skill, a hook or a subagent reaches them on Windows, Linux and macOS

## In short

Only two of the six candidates have a vendor-documented way to carry
scripts and templates and to address them by a path that does not
depend on where they lie: files inside the project itself (relative
paths, `${CLAUDE_PROJECT_DIR}`, `${CLAUDE_SKILL_DIR}`) and a plugin
(`${CLAUDE_PLUGIN_ROOT}`, `${CLAUDE_PLUGIN_DATA}`, a `bin/` directory
put on PATH). The plugin variables are substituted in the text of the
plugin's own skills, commands and agents and in hook commands; they
are not in the environment of commands Claude runs, and a project's
own skill does not get them, so a layer that lives in a project
reaches a plugin's scripts only as bare commands from the plugin's
`bin/`. A marketplace plugin is copied to
`~/.claude/plugins/cache/<marketplace>/<plugin>/<version>/` and
nothing outside its directory is copied; a plugin placed under
`.claude/skills/`, passed by `--plugin-dir` or listed by relative
path in a local marketplace loads in place, which is a development
loop without packaging. Python dependencies have no automatic
install anywhere (only Node packages have one); the documented way
is a hook that installs into `${CLAUDE_PLUGIN_DATA}`. Hooks run
outside the sandbox with the user's full access, and native Windows
has no sandbox at all. Confidence is high for what the vendor
documents (read today), lower for Windows: the disconfirming query
found many reports, as expected, and one of them (June 2026)
contradicts the current documentation on exec-form hooks, with no
statement of a fix found. The one unexpected thing: `--add-dir` now
loads subagents too, which the known note said it did not.

## Question

Card 3: Scripts, templates and data files under each candidate.

- **Question:** How does each candidate deliver Python scripts,
  templates and other data files, and how does a skill, a hook or a
  subagent reach them by a path that works on Windows, Linux and
  macOS: the variables Claude Code gives a plugin for its own root
  and its data, where an installed plugin lies on disk, whether a
  project's skill can address a file of a plugin or of a repository
  beside it? Where do a script's Python dependencies live in each
  case, and how do permission prompts, permission rules and the
  sandbox treat a script that lies outside the project directory?
- **The frame:** a framework on Claude Code (one always-on
  CLAUDE.md, skills, isolated subagents preloading a contract skill,
  hooks, templates, Python scripts, one public git repository) to be
  split into a general base, the present framework as the first
  operating layer, later layers, and a place for what a user makes
  for himself where an upgrade never writes. Candidates: (1) one
  repository with the layers as directories; (2) the base as a
  package of its own and each layer a repository of its own; (3) two
  repositories side by side joined by an import of one instruction
  file into the other; (4) a Claude Code plugin, possibly with a
  marketplace of its own; (5) Claude Code's own mechanisms without a
  plugin, user-level configuration and imports into CLAUDE.md; (6)
  the framework kept whole, a script separating the base at every
  release into a public repository from which other projects update.
  Judged by the development loop and the deployment loop.
- **Why it matters:** The base's mechanics are scripts and templates
  more than prompts; a way that delivers skills and loses the
  scripts they call does not deliver the base.
- **What would answer it:** The vendor's documentation of plugin
  structure, environment variables, permissions and sandboxing; the
  manifests of published plugins that ship scripts.
- **Where to look:** Anthropic's Claude Code documentation: plugins
  reference, hooks, permissions, sandboxing, settings; published
  plugins that carry scripts, read at source; the issue tracker for
  path variables on Windows. Must turn up: the plugin root variable,
  the plugin cache location, additional directories and their
  permissions.
- **Disconfirming query:** A search for reports that the plugin root
  variable or a hook's script path fails on Windows; expected: some.
- **Stop rule:** Each candidate has a stated way for scripts,
  templates and dependencies, or "none found"; the Windows behaviour
  has a source; the opening budget.

The baseline is the note of 2026-08-29 on packaging. It already has:
the three path variables by name, `bin/` on PATH, `userConfig`, the
three discovery walk-ups, `--add-dir` loading skills and commands
"but not agents", imports with their approval dialog, and that a
plugin's CLAUDE.md is not loaded. It does not have: where the
variables are and are not available, the cache layout, what is
copied, in-place loading, dependencies, permissions and sandbox for
a script outside the project, and any Windows behaviour. This note
must add those.

## Key findings

**F1. A plugin gets three path variables; they are substituted in
text and exported only to some processes, never to the commands
Claude runs.** [vendor claim; vendor documentation, read in full]
`${CLAUDE_PLUGIN_ROOT}` is the "Absolute path of the plugin's
installed version", `${CLAUDE_PLUGIN_DATA}` is
`~/.claude/plugins/data/<id>/`, "created on first reference and
kept across plugin updates", `${CLAUDE_PROJECT_DIR}` is the project
root [1, Environment variables]. They resolve anywhere in a hook's
`command` and `args`, in MCP and LSP server configuration, and
"Anywhere in the Markdown body" of skill, command and agent content;
they are exported to hook, MCP and LSP processes. The decisive
sentence for scripts: "The variables aren't present in the
environment of commands Claude runs through the Bash tool, in the
main session or in a subagent" [1, Where each variable resolves].
A script Claude is told to run must therefore get its path written
into the skill or agent text, where Claude Code substitutes it at
load. `${CLAUDE_PLUGIN_ROOT}` changes at every update, so state
belongs in the data directory [1][2].

**F2. A marketplace plugin lies in a versioned cache directory and
only its own directory is copied; three kinds of plugin load in
place.** [vendor claim; vendor documentation, read in full] The
plugins root is `~/.claude/plugins` unless
`CLAUDE_CODE_PLUGIN_CACHE_DIR` is set; a marketplace plugin is at
`cache/<marketplace>/<plugin>/<version>/`, its data at
`data/<plugin-id>/` [2, Find plugins on disk]. "Files outside the
plugin directory aren't copied", so a script reading `../shared`
finds nothing [2, In-place and copied plugins]. Component paths
that escape the plugin root are rejected, symlinks leading out
included, except links between plugins of one marketplace [2].
Loaded in place and never copied: a `--plugin-dir` plugin, a plugin
directory with `.claude-plugin/plugin.json` under `~/.claude/skills/`
or the project's `.claude/skills/`, and a relative-path plugin of a
marketplace added from a local path, whose edits "take effect at
the next session start or `/reload-plugins`" without a version bump
[2]. A previous version's directory is removed 14 days after an
update [2, Cleanup of previous versions]. A project-scope
skills-directory plugin loads only after the workspace trust check,
only from the primary working directory's `.claude/skills/` (no
parent search), and its monitors do not load [2].

**F3. A project's skill cannot address a plugin's root by variable;
the documented bridge is the plugin's `bin/`.** [vendor claim;
vendor documentation, summarised fetch for the skills page] The
skills page's substitution table says of `${CLAUDE_PLUGIN_ROOT}`
and `${CLAUDE_PLUGIN_DATA}`: "Substituted only in plugin skills"
[3, Available string substitutions]. Any skill gets
`${CLAUDE_SKILL_DIR}` (the directory of its SKILL.md; for a plugin
skill its subdirectory, not the plugin root) and
`${CLAUDE_PROJECT_DIR}`, both substituted in the skill's content
and in Bash rules of `allowed-tools` [3]. What does cross the
boundary: files in a plugin's `bin/` "are on the `PATH` of the Bash
tool's shell while the plugin is enabled, so Claude can run them as
bare commands"; they come after the user's own PATH entries; a
PowerShell-tool command outside the sandbox finds them too [4,
Executables]. A project skill, or a user's own skill, can therefore
call a base's script by its bare name. The agent's inference, not
tested: an extensionless Python file with a shebang in `bin/` runs
under Git Bash but not under PowerShell, and its shebang line meets
the `python` versus `python3` problem of F9.

**F4. Inside the project (candidate 1) scripts and templates need
no mechanism: they are reached relative to the project root or by
`${CLAUDE_PROJECT_DIR}` and `${CLAUDE_SKILL_DIR}`.** [vendor claim;
vendor documentation, summarised fetch for hooks and skills] Hooks
have the placeholder `${CLAUDE_PROJECT_DIR}`, "the project root
where the session started", which stays put when Claude changes
directory or enters a worktree, while the hook's working directory
follows Claude [5, Reference scripts by path]. A skill bundles
scripts in its own directory ("executed, not loaded") and addresses
them as `${CLAUDE_SKILL_DIR}/scripts/...`; the same variable in
`allowed-tools` "lets a skill run a bundled script without a
permission prompt" during the turn that invokes the skill [3].
Dependencies: nothing is managed; the scripts run on whatever
`python` the user's PATH gives. The sandbox, where it exists,
allows writes in the working directory by default [6].

**F5. A repository beside the project (candidate 3) is reached as
an additional directory: file access always, skills, commands and
now subagents when added by flag or command, never hooks or
settings.** [vendor claim; vendor documentation, permissions page
read in the relevant sections from a full copy] "Adding a directory
extends where Claude can read and edit files. It doesn't make that
directory a full configuration root" [7, Additional directories
grant file access, not configuration]. From a directory added with
`--add-dir` or `/add-dir`: skills (with live reload), commands and
subagents (without), `enabledPlugins` and `extraKnownMarketplaces`
only of its settings, CLAUDE.md only with
`CLAUDE_CODE_ADDITIONAL_DIRECTORIES_CLAUDE_MD=1`; a directory in
`permissions.additionalDirectories` of a settings file grants "file
access only" and loads none of this [7]. Hooks and other settings
keys load from the working directory's `.claude/` with no fallback
[7]. No variable names an added directory; the project's own hook
or skill must spell the sibling's path, relative to
`${CLAUDE_PROJECT_DIR}` or absolute. A skill loaded from the sibling
gets its own `${CLAUDE_SKILL_DIR}` [3], from which the sibling's
scripts are reachable by a relative step up; that step is the
agent's inference, not a documented pattern. An import in CLAUDE.md
carries instructions only, as the baseline note has it; it delivers
no script.

**F6. Python dependencies have no automatic install in any
candidate; a plugin's documented way is a hook installing into the
data directory.** [vendor claim; vendor documentation, read in
full] When Claude Code copies a plugin into the cache it installs
Node packages, only with a `package.json` and an npm or Bun text
lockfile, registry packages only, no lifecycle scripts [2, Node.js
package dependencies]. For the rest: "install it from a hook into
the persistent data directory. That includes packages that need
their lifecycle scripts to build, Python dependencies" [2, When the
dependency install fails or is skipped]. The data directory is
described as the place for "`node_modules`, virtual environments,
and caches" [4]; the only worked example is npm in a `SessionStart`
hook [4]. For a plugin loaded in place nothing is installed into
the source directory [2]. No vendor example of a Python virtual
environment in the data directory was found. Outside Claude Code, a
script can declare its own dependencies inline (`# /// script`,
`dependencies = [...]`), a packaging specification "conditionally
approved through PEP 723" in October 2023, which a script runner
must honour or fail [8]; it needs such a runner installed. A script
with standard-library imports only needs none of this.

**F7. Permissions treat a script outside the project by the text of
the command and by where its files lie; a plugin skill can
pre-approve its own script, and hooks need no approval at all.**
[vendor claim; vendor documentation] Bash rules "match the whole
command text"; a rule does not match "the same program invoked in a
different form", so `python C:/.../x.py` and a bare `x` are
different commands to a rule [7, Bash]. Reads by the file tools are
free of prompts only "within the working directory and additional
directories" [7, Permission system]; a template in a plugin cache
or in a sibling repository that is not added is outside them.
`allowed-tools` accepts `${CLAUDE_SKILL_DIR}` and, in plugin
skills, `${CLAUDE_PLUGIN_ROOT}` in Bash rules, and the grant lasts
for the turn that invokes the skill [3]. Path rules for Read and
Edit: `//path` absolute, `~/path` home, `/path` relative to the
settings source (in user settings that is `~/.claude`, not the
project); "On Windows, paths are normalized to POSIX form before
matching", `C:\Users\alice` becoming `/c/Users/alice` [7, How path
patterns match]. Project allow rules and additional directories of
a project's settings apply only after the workspace trust dialog
[7]. Hook commands are configuration, not tool calls: they run
without a permission prompt, subject to the trust rule for project
hooks [5][7]. Whether Claude's Read of a file inside a loaded
skill's own directory outside the project prompts was not found
stated.

**F8. The sandbox covers shell commands only, never hooks, and does
not exist on native Windows.** [vendor claim; vendor documentation,
summarised fetch] "On native Windows, Claude Code runs commands
unsandboxed"; the sandbox runs on macOS, Linux and WSL2 [6]. It
applies to "Bash, PowerShell, and Monitor commands and the
processes they start"; hooks, MCP servers, plugin monitors and LSP
servers "run with your full access" [6]. By default a sandboxed
command reads most of the machine and writes to the working
directory, a per-user temp directory and added directories; most of
`~/.claude` and the project's `.claude/skills`, `.claude/agents`,
`.claude/commands`, `.claude/hooks` and settings files stay
write-denied [6, Protected paths]. So where a sandbox is on, a
script lying in the plugin cache or in a sibling repository can be
read and run, can write into the project, and cannot write into
its own install directory or into the project's `.claude/` skills
and agents; a script that scaffolds or updates files there fails
sandboxed and goes through the unsandboxed retry or an excluded
command [6]. This last consequence is the agent's reading of the
defaults, not a sentence of the page.

**F9. Windows: the documentation now states the separator
behaviour, but the issue tracker shows the path variable failing in
hooks through 2026, and one report contradicts the documentation.**
[contested; vendor documentation against practitioner reports] The
documentation: "On Windows, most substituted paths use forward
slashes, as in `C:/Users/you/...`. They keep their native
backslashes in an exec-form hook and in a hook that runs through
PowerShell" [1, Quoting and path separators]. A shell-form hook
runs in Git Bash on Windows, or PowerShell when Git Bash is not
installed; exec form (`args` set) spawns the executable directly,
needs "a real executable such as a `.exe`", and "No shell
tokenization happens on any platform"; the advice is to use exec
form for any hook that references a path placeholder, and in shell
form to wrap the placeholder in double quotes [5, Exec form and
shell form]. Against this: issue 21878 (opened 2026-01-30, Claude
Code 2.1.23, Git Bash) shows the expanded backslash path garbled to
`C:Usersusername.claudeplugins...` and the hook not found; it was
closed by the inactivity bot as not planned, with no maintainer
statement [9]. Issue 70150 (opened 2026-06-22, Claude Code 2.1.186)
reports the same garbling in exec form, `bash` with the script path
in `args`, which the documentation says cannot happen; it too was
closed by the inactivity bot on 2026-08-04 without a maintainer
word [10]. Both rest on summarised fetches of the issue pages. No
changelog entry or maintainer statement naming a fixed version was
found, so whether the current behaviour matches [1] or [10] on a
given version is open. Separately, the interpreter's name: the
hooks of Anthropic's own `hookify` plugin on its main branch read
`python3 "${CLAUDE_PLUGIN_ROOT}/hooks/pretooluse.py"` [11], and
issue 24550 (2026-02-10, Claude Code 2.1.37) reports it failing on
Windows with "'python3' is not recognized as an internal or
external command", closed as a duplicate of three earlier reports
[12]. Youngest source for this finding: the documentation as
fetched 2026-11-14.

**F10. Candidates 2 and 6 have no way of their own in Claude Code;
each resolves into one of the ways above.** [single source by
absence; vendor documentation] The documentation names three routes
for sharing configuration across projects: user-level
configuration, plugins, and launching from the directory that holds
the `.claude/` configuration [7, Where output styles, hooks, and
local settings load from]. Nothing in the pages read describes a
package other than a plugin, or a mechanism that updates files in a
project from an upstream repository. The agent's inferences: "the
base as a package" is either a plugin (F1 to F3, F6) or a Python
package installed by the user's own tool, which puts scripts on
PATH as commands and keeps dependencies in its own environment but
delivers no skill, agent or hook; "a separate public repository
from which projects update" delivers scripts either as files copied
into each project (then F4 holds and the update is the framework's
own script or git) or as a plugin source (then F1 to F3 hold).
Candidate 5 without a plugin: a user-level skill under
`~/.claude/skills/` carries scripts in its own directory and reaches
them by `${CLAUDE_SKILL_DIR}` [3]; no update channel for it was
found, unless that directory is itself a plugin loaded in place
[2], which needs no marketplace and no trust check.

## Unexpected

- The known note of 2026-08-29 says `--add-dir` loads skills and
  commands and that "agents are not loaded". The permissions page
  as fetched today lists "Subagents in `.claude/agents/`: Yes,
  without live reload" for flag-added directories, and the
  subagents page says the same [7][13]. Candidate 3 is stronger
  than the baseline had it: only hooks and settings do not come
  from the sibling.
- The documentation was reorganised since the baseline: the address
  of the plugins reference now serves a "Plugin manifest reference"
  with separate pages for loading, components, dependencies between
  plugins and troubleshooting [1][2][4]. The baseline's sentence on
  CLAUDE.md at the plugin root stands, and `claude plugin validate`
  now warns about one [1].
- One repository can be both the development copy and the published
  source of a plugin. A plugin directory under the project's
  `.claude/skills/` loads in place [2], and the version table names
  a `git-subdir` marketplace source and a "Relative path inside a
  Git-hosted marketplace" [2, How Claude Code computes the version].
  This reads as a combination of candidates 1 and 4 with no second
  repository and no git inside git; the marketplace side of it was
  not opened in this run and belongs to another card.
- A plugin manifest has a `dependencies` field for plugins that
  "must be enabled for this one to work", with an optional
  `version` per entry [1]. It bears on how a layer says which base
  it needs; the page on dependency constraints was not opened.
- A plugin with a top-level `bin/` is not installed by claude.ai and
  Cowork [1][4]. Out of scope for a Claude Code only choice, noted
  because `bin/` is the bridge of F3.

## Not found

- No vendor statement of which Claude Code version fixed the
  backslash failures of `${CLAUDE_PLUGIN_ROOT}` in Windows hooks,
  and no maintainer answer on issues 21878 and 70150 (looked in:
  the two issues, two web searches; the changelog itself was not
  opened).
- No vendor example of Python dependencies or a virtual environment
  installed into `${CLAUDE_PLUGIN_DATA}`; only the sentence that it
  is the way, and an npm example (components and loading pages).
- No statement whether substitutions (`${CLAUDE_SKILL_DIR}`,
  `${CLAUDE_PLUGIN_ROOT}`) apply to a skill's content when it is
  preloaded into a subagent through the `skills` field, nor whether
  a project subagent can preload a plugin's skill by its namespaced
  name (subagents page, first 100,000 characters of a summarised
  fetch).
- No statement whether `${CLAUDE_PROJECT_DIR}` is substituted in the
  content of a project (non-plugin) subagent; the manifest reference
  covers plugin components only.
- No statement how a relative `command` of a frontmatter hook in a
  skill or a subagent is resolved, beyond that hooks run in the
  current directory.
- No statement whether the Read tool prompts for a supporting file
  of a loaded skill or plugin that lies outside the working
  directories.
- No variable or setting that names an additional directory for use
  in a skill or a hook.
- No published third-party plugin with Python dependencies was read
  at source; the one manifest read is the vendor's own, with
  standard-library scripts only so far as its hook file shows.

## Options

1. **Scripts stay files of the project (candidates 1 and 6 by
   copy).** Paths are relative or `${CLAUDE_PROJECT_DIR}`; no
   Windows path variable is involved in hooks beyond the project
   root; permissions and the sandbox treat everything as inside.
   Price: every project holds a copy, and the update of those
   copies is the framework's own mechanism, not Claude Code's.
2. **The base as a plugin, scripts in its root, called from its own
   skills by `${CLAUDE_PLUGIN_ROOT}`.** Versioned cache, an update
   channel, pre-approval through `allowed-tools`. Price: the
   operating layer's skills must be plugin skills too, or reach the
   base through `bin/` only; hooks carry the Windows risk of F9;
   templates lie outside the working directories; Python
   dependencies need a hook of one's own.
3. **The base as a plugin with its commands in `bin/`.** Every
   skill, in the project, in the user's own place or in another
   plugin, calls the base by bare command names; Bash rules are
   short and independent of the install path. Price: executables
   must run under both Git Bash and PowerShell on Windows, the
   interpreter's name is the script's own problem, and templates
   still need a path, which the command can find from its own file
   location.
4. **The base as a repository beside the project, added by
   `--add-dir`.** Skills, commands and subagents load from it;
   scripts are reached by a spelled path. Price: hooks and settings
   do not load, the path is the user's to keep right, and
   `additionalDirectories` in settings does less than the flag.
5. **Option 2 or 3 developed in place.** The base lives in the
   framework's repository as a plugin directory under
   `.claude/skills/` or is loaded with `--plugin-dir`, so a change
   is tried without packaging; the same directory is what a
   marketplace entry publishes. Price: the project-scope trust
   check, no monitors, and the publishing side unverified here.

## Relevance to this project

The recommendation, the agent's own: carry the base's scripts and
templates in a plugin, expose the scripts as commands through
`bin/` as well as by `${CLAUDE_PLUGIN_ROOT}` in the base's own
skills, and develop that plugin in place inside the framework's
repository (option 5 over options 2 and 3). It rests on F1 to F3:
the plugin is the only candidate with variables for its own root
and data, and `bin/` is the only documented bridge by which a
layer's or a user's own skill outside the plugin reaches the base.
It is chosen against the sibling repository (F5), which loads
skills and agents but neither hooks nor settings and has no path
variable, and against user-level configuration (F10), which has no
update channel of its own.

What the choice must carry with it, from the findings: the two
hooks of the framework become plugin hooks and should be written in
exec form with `python` as the command and the script path in
`args`, and tested on Windows on the version in use, since F9 is
unresolved; scripts should keep to the standard library or the
dependency question of F6 has to be answered by a hook into the
data directory; anything a script writes must go to the project or
the data directory, never beside itself (F2, F8); templates are
read by the scripts rather than by Claude's file tools where
possible, because the cache lies outside the working directories
(F7); the interpreter is named `python`, as the framework already
requires, not `python3` (F9). What a user makes for himself stays
in the project's or the user's `.claude/`, where no plugin update
writes, and calls the base by its commands.

The parts marked as inference above (shebang files under
PowerShell, the relative step from a sibling's skill, the sandbox
consequence) are to be tried before they are relied on.

Consult when: deciding where the base's scripts and templates lie;
writing a hook or a skill that calls a script outside the project;
a hook fails on Windows; choosing how Python dependencies are
installed; writing permission rules for the base's commands;
judging whether a sibling repository or a plugin carries the base.

## Sources

1. "Plugin manifest reference", Anthropic, Claude Code
   documentation; undated, mentions Claude Code up to v2.1.288,
   fetched 2026-11-14;
   https://code.claude.com/docs/en/plugins-reference.md (the
   address of the former plugins reference, which now serves this
   page); primary; read in full, through a fetch tool that returned
   the page text; original.
2. "Plugin loading reference", Anthropic, Claude Code
   documentation; undated, mentions up to v2.1.324, fetched
   2026-11-14; https://code.claude.com/docs/en/plugins/loading.md;
   primary; read in full, through a fetch tool that returned the
   page text; original.
3. "Skills", Anthropic, Claude Code documentation; undated, fetched
   2026-11-14; https://code.claude.com/docs/en/skills.md; primary;
   summarised fetch of the first 100,000 of 119,637 characters,
   quotes as the fetch returned them; original.
4. "Add components to a plugin", Anthropic, Claude Code
   documentation; undated, fetched 2026-11-14;
   https://code.claude.com/docs/en/plugins/components.md; primary;
   read in full, through a fetch tool that returned the page text;
   original.
5. "Hooks reference", Anthropic, Claude Code documentation;
   undated, fetched 2026-11-14;
   https://code.claude.com/docs/en/hooks.md; primary; summarised
   fetch of the first 100,000 of 293,734 characters (the sections
   on script paths, exec and shell form, command hook fields,
   hooks in skills and agents); original.
6. "Sandboxing", Anthropic, Claude Code documentation; undated,
   fetched 2026-11-14; https://code.claude.com/docs/en/sandboxing.md;
   primary; summarised fetch of the first 100,000 of 110,890
   characters; original.
7. "Configure permissions", Anthropic, Claude Code documentation;
   undated, mentions up to v2.1.314, fetched 2026-11-14;
   https://code.claude.com/docs/en/permissions.md; primary;
   partially: the full page text was returned and the sections
   Permission system, Bash, How path patterns match, Working
   directories, Additional directories, How permissions interact
   with sandboxing and Project allow rules were read; original.
8. "Inline script metadata", Python Packaging Authority, Python
   Packaging User Guide; history note October 2023 (dated by the
   page's own history section);
   https://packaging.python.org/en/latest/specifications/inline-script-metadata/;
   primary (a specification); summarised fetch; original.
9. "Hook scripts fail on Windows: backslash paths misinterpreted by
   Git Bash", issue 21878 of anthropics/claude-code, a user report;
   opened 2026-01-30, closed as not planned 2026-03-05 (dated by
   the page); https://github.com/anthropics/claude-code/issues/21878;
   primary (practitioner report); summarised fetch; original.
10. "Windows: exec-form hook args with ${CLAUDE_PLUGIN_ROOT} lose
    backslashes (path mangled)", issue 70150 of
    anthropics/claude-code, a user report; opened 2026-06-22,
    closed as not planned 2026-08-04 (dated by the page);
    https://github.com/anthropics/claude-code/issues/70150; primary
    (practitioner report); summarised fetch; original.
11. `plugins/hookify/hooks/hooks.json`, Anthropic,
    anthropics/claude-plugins-official, main branch; undated,
    fetched 2026-11-14;
    https://raw.githubusercontent.com/anthropics/claude-plugins-official/main/plugins/hookify/hooks/hooks.json;
    primary; read in full; original.
12. "[BUG] Hookify plugin hardcodes "python3" command, fails on
    Windows where only "python" is available", issue 24550 of
    anthropics/claude-code, a user report; opened and closed as
    duplicate 2026-02-10 (dated by the page);
    https://github.com/anthropics/claude-code/issues/24550; primary
    (practitioner report); summarised fetch; original.
13. "Create custom subagents", Anthropic, Claude Code
    documentation (title not confirmed from the page; the page at
    this address is the subagents page); undated, fetched
    2026-11-14; https://code.claude.com/docs/en/sub-agents.md;
    primary; summarised fetch of the first 100,000 of 116,580
    characters; original.

## Opened and not used

None. Every page opened is cited.

## Search record

Queries, in order:

1. Claude Code plugins reference, plugin root and data variables,
   cache directory.
2. `CLAUDE_PLUGIN_ROOT` Windows hook fails, issue tracker (the
   disconfirming query).
3. Claude Code permissions, additional directories, sandbox, script
   outside the project directory.
4. Claude Code changelog, Windows plugin hooks, forward slashes
   fixed (the disconfirming query, second pass, looking for a fix).
5. Plugin hook `python3` on Windows not found, hookify.

Pages opened, thirteen: sources 1 to 13 above, in the order 1, 5,
7, 2, 6, 4, 3, 9, 11, 13, 10, 12, 8.

The disconfirming query found what was expected and more: result
lists with some twenty reports of `${CLAUDE_PLUGIN_ROOT}` failing in
Windows hooks (backslashes stripped under Git Bash, paths with
spaces unquoted, the variable left unexpanded in the desktop app),
most of them on a mirror of the issue tracker, which was not opened
and is not cited. Two were opened at the tracker itself [9][10];
the younger one contradicts the current documentation on exec form.
The second pass found no changelog entry or maintainer statement of
a fix. A further cluster reports `python3` not found on Windows in
the vendor's own plugins; one was opened [12].

The run ended by the card's stop rule: each candidate has a stated
way for scripts, templates and dependencies or a "none found", and
the Windows behaviour has a source on both sides; thirteen openings
were spent of the budget of about ten to fifteen.
