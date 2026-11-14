---
date: 2026-11-14
project: forge
topic: what Claude Code offers for composing a base package and layers on it (plugins, dependencies with version ranges, namespaces, precedence, cross-package skill preload) and what changed since early October 2026
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-14-anvil-carrying-layers/01-composing
derived_from: research/2026-11-14-anvil-carrying-layers/00-plan.md, card 1; research/2026-08-29-claude-code-packaging.md; research/2026-10-03-user-extensions-kept-apart-from-the-core.md; web sources below
---

# Claude Code composes a base and layers through plugins with dependencies and a namespace per plugin; the name under which one package preloads another's skill is not stated

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

The plugin system is the only mechanism of Claude Code that carries
"package A needs package B at version range R" and shows a failure:
`dependencies` in `plugin.json` with semantic-version ranges resolved
against git tags `<plugin>--v<version>`, a failed install or a
disabled dependent plugin with a named line when the range is not
met [1]. Since 2026-11-12 (v2.1.323) a plugin can also state the
Claude Code version it needs, `engines["claude-code"]`, per the
changelog [6]; the manifest reference read on 2026-11-14 does not
list that field yet [7]. Every plugin component is namespaced under
the plugin's manifest name, so a base, a layer and a user's own
things never collide by name when each is a plugin; outside plugins
the collision rules still run in opposite directions for skills
(personal over project) and agents (project over user) [2][3][4].
Hooks have no names: every enabled package's hooks fire, and only
two plugins of one manifest name exclude each other [4][5]. The
load-bearing sub-question, by what name an agent of one package
preloads a skill of another, is **not stated** in the vendor's
documentation as read today: the subagents page shows bare names
only and says a missing skill is skipped with a debug-log warning
[2]. The disconfirming query found three issues on exactly these
behaviours, all closed (one fixed, one closed "completed" with no
fix described, one closed unfixed by the stale bot) [8][9][10], and
one reportedly open issue that was not opened. Unexpected: the
plugin `agent` setting, the strongest way a plugin could carry an
always-on core, was deprecated on 2026-11-12 [6].

## Question

**Frame.** A framework built on Claude Code (Anthropic's agent for
the command line) consists of one always-on instruction file
(CLAUDE.md), skills (its commands), isolated subagents (reviewers
that preload a shared contract skill), hooks, templates and Python
scripts, in one public git repository that a user clones and works
in. Its author wants to split it into a general **base** that owns
the mechanics, the present framework as the first **operating
layer** on that base, later more layers, and a place for what a
**user makes for himself**, kept where an upgrade never writes. The
base is used in many projects, maintained in one place, and every
project can be updated to its latest version. Candidates: (1) one
repository with layers as directories; (2) the base as a package and
each layer a repository; (3) two repositories joined by an import of
one instruction file; (4) a Claude Code plugin, possibly with a
marketplace; (5) Claude Code's own mechanisms without a plugin;
(6) the framework kept whole, a script separating the base at every
release. Each is judged by the development loop and the deployment
loop.

**Card 1: Composing a base and layers in Claude Code.**

- **Question:** What does Claude Code offer in November 2026 for one
  package (a base) carrying mechanism and other packages (layers, a
  user's own things) carrying content on it: plugins and
  marketplaces, dependencies between plugins with version ranges and
  what happens when a required version is missing, namespaces, and
  the precedence when a base, a layer and a user define a skill, an
  agent or a hook of the same name? Can an agent of one package
  preload a skill of another package, and by what name? What changed
  since early October 2026?
- **Why it matters:** It decides whether the plugin, the
  package-per-layer and the no-plugin candidates can carry a shared
  reviewer contract and a required version of the base at all.
- **What would answer it:** The vendor's own statements of
  behaviour: the documentation pages of plugins, marketplaces,
  skills, subagents and settings, and the changelog entries since
  October 2026.
- **Where to look:** Anthropic's Claude Code documentation; the
  changelog and release notes of Claude Code; the reference of the
  plugin manifest and the marketplace file; the issue tracker of
  Claude Code for the behaviours the documentation leaves unsaid.
  Must turn up: plugin dependencies, the namespace rule of plugin
  skills, the `skills` field of a subagent.
- **Disconfirming query:** A search for reports that cross-plugin
  skill preloading or plugin dependency version ranges do not work
  as documented; expected: at least one open issue.
- **Stop rule:** Every sub-question has a statement from the
  vendor's documentation or changelog, or is recorded as not stated
  there; nothing new from a differently worded query; the opening
  budget of the brief.

**Baseline.** The note of 2026-08-29 established that a plugin
carries no always-on `CLAUDE.md` and listed four substitutes; the
note of 2026-10-03 (changelog to v2.1.288) recorded plugin
dependencies with ranges in one paragraph, the opposite collision
rules of skills and agents, the skills-directory plugin, and left
open whether an agent can preload a skill across packages, quoting
from a fetch summary the example `my-plugin:security-patterns`.
This note must beat them on: the full behaviour of dependencies
(resolution, failure, update, local development), the preload name
read at source, and everything from v2.1.289 on.

## Key findings

**F1. A plugin declares the plugins it needs, with a
semantic-version range, in `plugin.json`.** [vendor claim; vendor
documentation, page returned whole] "List dependencies in the
`dependencies` array of your plugin's `.claude-plugin/plugin.json`"
(section "Declare a dependency with a version constraint"). An entry
is `"name"`, `"name@marketplace"` or an object with `name`,
`version` ("A semantic-version range such as `~2.1.0`, `^2.0`,
`>=1.4`, or `=2.1.0`") and `marketplace`. Without a range "a
dependency moves to each new release its marketplace publishes the
next time users update". A plugin of nothing but `name` and
`dependencies` is valid and installs the whole set ("Bundle plugins
for a team") [1][7].

**F2. A range resolves against git tags named
`<plugin-name>--v<version>`; the base's maintainer must tag.**
[vendor claim; vendor documentation] "The dependency installs at
the highest git tag that satisfies this range". The tag sits on the
plugin's own repository for a `github`, `url` or `git-subdir`
source, on the marketplace repository for a relative-path source;
`claude plugin tag --push` builds it from the manifest. "Constraint
checks use the tag's version rather than the `version` in
`plugin.json`". Ranges do not match pre-releases without a
pre-release suffix [1].

**F3. A missing or conflicting version is detected and named, in
four different ways by case.** [vendor claim; vendor documentation]
(a) Dependency with its own repository and no satisfying tag: the
install fails with `Dependency "…" has no git tag satisfying`.
(b) Dependency referenced by a relative path: "the install uses the
marketplace's current copy instead, and the constraint is checked
when the plugin loads. If that copy is outside the range, the
dependent plugin stays disabled and `claude plugin list` shows
`Requires "secrets-vault@your-marketplace" ~2.1.0, installed
3.0.0`". (c) Two installed plugins with ranges that do not overlap:
installing the second "fails with a `has conflicting version
requirements` message"; under auto-update the dependency stays at
its version with an entry in the `/plugin` Errors tab.
(d) Dependency disabled or absent: the dependent plugin is disabled
at the next load with an error ending `is disabled — enable it or
remove the dependency` [1]. Contradicted in part by [8]: a report
on v2.1.237 that a range declared in the *marketplace entry* rather
than in `plugin.json` "is silently ignored. `~2.1.0` installs
`3.0.0`, with no error anywhere"; closed "not planned" by the stale
bot on 2026-10-11, no maintainer reply (see F12).

**F4. A dependency in another marketplace is refused unless the
root marketplace allows it, or the user installed it himself.**
[vendor claim; vendor documentation] "By default, Claude Code
doesn't install a dependency from a different marketplace than the
declaring plugin's own, unless the user already has that dependency
installed and enabled at the same scope." The allowlist is
`allowCrossMarketplaceDependenciesOn` in the root marketplace's
`marketplace.json`. Declared in `plugin.json` without the
allowlist, "the install completes without the dependency and your
plugin then fails to load" [1]. For a base in one repository and
layers in others this means either one marketplace that lists all
of them, or an allowlist entry in every layer's marketplace.

**F5. The development loop has a documented form: local copies
satisfy dependencies and no version is checked.** [vendor claim;
vendor documentation] `claude --plugin-dir ./my-dependency
--plugin-dir ./my-plugin`: "The local copy of the dependency
satisfies your plugin's dependency entry"; "a version constraint
isn't checked against a local copy"; an entry naming a marketplace
also matches the local copy on v2.1.242 or later; one parent folder
of several plugins can be passed once (v2.1.265 or later) [1].
`--plugin-dir` and skills-directory plugins load "in place and
\[are\] never copied"; a relative-path plugin of a marketplace added
from a local path also loads in place, edits taking effect "at the
next session start or `/reload-plugins`, and you don't need to
increase the version" [5]. Whether a skills-directory plugin
(`<name>@skills-dir`) satisfies another plugin's dependency entry
is not stated on the pages read. A fixed defect bears on this loop:
dependencies never resolved for plugins loaded by `--plugin-dir` in
the desktop app; a maintainer wrote "Fixed in Claude Code 2.1.243"
on 2026-10-23 [9].

**F6. The deployment loop: updates are pulled by version, and
outside Anthropic's own marketplaces they are off until switched
on.** [vendor claim; vendor documentation] The version is the
manifest's `version`, else the marketplace entry's, else the commit
SHA; "a manifest that pins `"version": "1.0.0"` keeps every user on
the cached copy until its author changes the string". Auto-update
is by default "on for Anthropic's official marketplaces … and off
for every other marketplace"; a user turns it on per marketplace,
or a settings file declares `autoUpdate` on the marketplace's
`extraKnownMarketplaces` entry. With auto-update on, the pass runs
after the first message of an interactive session, and a
constrained dependency is fetched "at the highest git tag that
satisfies every installed plugin's range, rather than at the
marketplace's latest version" [5][1]. A plugin enabled only in a
project's committed `.claude/settings.json` "doesn't load at
session start until you install it on your machine", except a
relative-path plugin of a marketplace added from a local path [5].
Nothing read forces a user to update: a layer that needs a newer
base says so by a wider range in its own new version, and a user
who updates neither keeps both old copies (the agent's reading of
[1], not a vendor sentence).

**F7. Since v2.1.323 (2026-11-12) a plugin can state the Claude
Code version it needs.** [vendor claim; changelog, read through a
summarising fetch, quote as the fetch gave it] "Added
`engines["claude-code"]` to `plugin.json`: plugins outside their
stated Claude Code version range are not installed, updated or
loaded, and install and update pick the newest version that fits"
[6]. Conflict to name: the manifest reference, returned whole on
2026-11-14, has no `engines` row in its Fields table and says of
unknown keys "the field is stripped and the plugin loads" [7]. The
two are one day apart; the reference may lag. That a client older
than 2.1.323 strips the key and loads the plugin regardless is the
agent's inference from [7], not a vendor statement.

**F8. Namespaces: every component of a plugin is named
`<plugin>:<name>`, and the prefix comes from the manifest name.**
[vendor claim; vendor documentation] "Claude Code namespaces every
component under it, so an agent `reviewer` in plugin `deploy-tools`
appears as `deploy-tools:reviewer`" [7]. Skills and commands:
`/<plugin>:<directory>`; "If you set `name` in the frontmatter, it
replaces the last segment and the plugin prefix stays" [4]. "The
bare `/fancy` also invokes the skill unless another command already
uses that name" [3, through a summarising fetch]. Agents:
`<plugin>:<name>`, subfolders joined by colons
(`my-plugin:review:security`); an agent's own `name` "can't contain
`:`" [2][4]. When the marketplace entry name and the manifest name
differ, "`enabledPlugins` uses the entry name, and components are
namespaced under the manifest name" [7]. A plugin name may not
start with `claude-` or `anthropic-` (a validation error; the
plugin still loads) [7].

**F9. Precedence by component when a base, a layer and a user
define the same name.** [vendor claim; vendor documentation; the
skills and subagents pages through a summarising fetch]

- *Skills.* "Enterprise over personal, and personal over project."
  "A plugin skill and a skill at any of the locations above: Both
  load, because plugin skills are namespaced as
  `/plugin-name:skill-name`." A skill in an added directory that
  clashes runs under `<folder>:<name>` (v2.1.309 or later); a
  nested skill under its path (`/apps/web:deploy`) [3].
- *Agents.* "When multiple subagents share the same name, Claude
  Code uses the one from the higher-priority location": managed,
  `--agents`, project `.claude/agents/`, user `~/.claude/agents/`,
  "Plugin's `agents/` directory … 5 (lowest)". Plugin agents are
  listed and invoked under their scoped name, and "If multiple
  plugins provide agents with the same name, pass the scoped name
  to disambiguate". Two files of one name inside one
  `.claude/agents/` tree are resolved "by filesystem read order
  rather than a documented precedence" [2].
- *Hooks.* No names and no precedence: a plugin's hooks are
  registered "when a session loads the plugin, and they fire on
  their events from then on" [4]. The one exclusion: "When you
  install and enable two plugins with the same manifest name from
  different marketplaces … the hooks of one of them are left out",
  with a note in the `/plugin` Errors tab (v2.1.296 or later) [5].
  That hooks present in both the project and a plugin run twice was
  verified in the note of 2026-10-03 and not re-read today.
- *Plugins of one name from several origins.* Managed, then
  `--plugin-dir` and its kin, then an installed marketplace plugin,
  then a skills-directory plugin (personal over project), then a
  plugin synced from the account; the loser is reported, except
  that a `--plugin-dir` copy replaces an installed marketplace
  plugin "silently" [5].
- *Whether a plugin is on.* `enabledPlugins` merges key by key
  across `--add-dir`, user, project, local, flag and managed
  sources, "the highest-precedence source that mentions the id"
  winning [5].

**F10. An agent's `skills` field preloads full skill content; the
documentation does not say by what name a plugin's skill is listed
there.** [vendor claim for what is stated; "not stated" verified on
the section reproduced in full by the fetch, the last 16,580
characters of the page unread] Stated: "The full content of each
listed skill is injected into the subagent's context at startup, up
to the first 32 distinct names in the list"; "preloading draws from
the same set of skills Claude can invoke", so a skill with
`disable-model-invocation: true` cannot be preloaded; "If a listed
skill is missing or disabled … Claude Code skips it and logs a
warning to the debug log". The only example lists bare names
(`api-conventions`, `error-handling-patterns`). `skills` is among
the "Supported fields" of a plugin agent's frontmatter [2][4]. Not
stated: whether a plugin skill is written `plugin:skill` or bare,
and whether an agent of one plugin, or of the project, may list a
skill of another plugin. The example `my-plugin:security-patterns`
that the note of 2026-10-03 quoted from a fetch summary was not on
the page as read today; whether the page changed or the earlier
summary added it cannot be told from here. That `base:contract`
works, because plugin skills are in the invocable set under their
scoped name, is the agent's inference and needs a trial. An issue
of February 2026 reported that preloading "silently fails when
plugin-deployed agents reference plugin skills", for the bare and
the `plugin-name:my-skill` form alike, "0/17" agents; it was closed
"completed" on 2026-02-17 with no reply describing the fix [10].

**F11. What changed between v2.1.288 (2026-10-02) and v2.1.325
(2026-11-13) that bears on composing packages.** [vendor claim;
changelog through a summarising fetch, quotes as the fetch gave
them; versions 2.1.289 to 2.1.294 and parts of 2.1.295, 2.1.303,
2.1.304 and 2.1.319 not read] [6]

- 2.1.295 (2026-10-08): "Changed subagents to preload at most 32
  skills from the `skills` field, each once".
- 2.1.296 (2026-10-09): a note in `/plugin` for a plugin whose
  hooks are left out by a same-named plugin; "Fixed a plugin synced
  from claude.ai being disabled when the marketplace dependency it
  declares was also synced from claude.ai"; `--debug` names
  unrecognised frontmatter fields of custom agent files.
- 2.1.299 (2026-10-14): "Changed `UserPromptSubmit` hooks to run
  before a skill or custom slash command expands"; skills and
  commands with hidden or blank-like characters, `<` or `>` in
  their names are no longer offered.
- 2.1.309 (2026-10-22): a skill of an `--add-dir` folder whose name
  is taken "is now offered as `<folder>:<name>`".
- 2.1.319 (2026-11-06): "`--add-dir` directories … register plugin
  marketplaces only once that directory's own trust dialog has been
  accepted"; nested skills under the Bash sandbox load only when
  Claude Code is started or moved there.
- 2.1.321 (2026-11-09): "`.claude/skills` folders inside
  `~/.claude/plugins` no longer load when Claude works on files
  there".
- 2.1.323 (2026-11-12): `engines["claude-code"]` (F7); "Deprecated
  a plugin's `agent` setting: it still applies, and now warns at
  startup, in `claude plugin list` and in `claude plugin
  validate`"; "Fixed plugins with a version list in
  `enabledPlugins` staying off with no message"; installs fail when
  a git submodule is not on its recorded commit; in an untrusted
  folder "the repository's settings can no longer disable your
  hooks or turn plugins on or off".
- 2.1.325 (2026-11-13): "Changed marketplace `ref` to accept the
  full ID of any commit on a branch or tag; clients before this
  version can't clone such a pin"; "`.claude/skills` folders in
  `--plugin-dir` plugins no longer load from a session started
  above them"; plugin loading skips some unsafe paths and links.

**F12. Still holding, re-read today.** [vendor claim; vendor
documentation, pages returned whole] "A `CLAUDE.md` at the plugin
root isn't loaded as context, and `claude plugin validate` warns
when it finds one" [7]. A plugin agent ignores `permissionMode`,
`hooks`, `mcpServers` and `initialPrompt` [4]. A project-scope
skills-directory plugin loads only from the `.claude/skills/` of
the session's primary working directory, after the trust dialog,
without background monitors, and Claude Code "doesn't scan a
project's `.claude/plugins/` directory" [5]. Files outside a copied
plugin's directory are not copied, and a component path that
resolves outside the plugin root is rejected [5]: a layer cannot
reach into the base by a relative path once both are installed from
a marketplace.

## Unexpected

**The strongest plugin route to an always-on core is being
withdrawn.** The note of 2026-08-29 ranked a plugin's `settings`
with `{"agent": …}`, a main-thread agent, first among the
substitutes for a plugin-borne `CLAUDE.md`. The changelog of
2.1.323 says "Deprecated a plugin's `agent` setting: it still
applies, and now warns" [6], and the manifest reference read today
has no `settings` key in its Fields table [7]. The card assumes
nothing about this, but candidate (4) loses one of its three ways
of carrying the instruction file; a `SessionStart` hook and an
import line written into the project's `CLAUDE.md` remain, neither
re-read today.

**A user-side version pin may exist in `enabledPlugins`.** The
changelog of 2.1.323 speaks of "plugins with a version list in
`enabledPlugins`" [6]. The note of 2026-08-29 said users cannot pin
a plugin version. The settings reference entry was not reached (the
fetch stopped before it), and an issue on the array form (#46934)
was not opened; a lead only.

**A range's place of declaration changes its meaning.** The
documentation lets dependencies be declared in `plugin.json` or in
the marketplace entry; the unfixed report [8] says only the
manifest form is honoured by everything that reads the graph,
`uninstall --prune` included. A lead for the design: declare in
`plugin.json`.

**Marketplace pins by full commit ID break older clients.**
"clients before this version can't clone such a pin, so a
marketplace pinned this way stops loading there" (2.1.325) [6]. A
public base that pins this way sets a floor of 2.1.325 for every
stranger.

## Not found

- By what name a plugin's skill is listed in an agent's `skills`
  field, and whether an agent of one plugin or of the project may
  preload a skill of another plugin: not stated on the subagents
  page (first 100,000 of 116,580 characters, the section itself in
  full), the skills page (first 100,000 of 119,637), the components
  page or the manifest reference.
- Whether a skills-directory plugin satisfies a `dependencies`
  entry, and whether its own `dependencies` are enforced: not
  stated on the dependencies or loading pages.
- A documentation entry for `engines`: not on the manifest
  reference; a search returned only the old feature request.
- The documented form and behaviour of a version list in
  `enabledPlugins`: settings reference not reached.
- The changelog entries of 2.1.289 to 2.1.294, the fix list of
  2.1.295, and the cut parts of 2.1.303, 2.1.304 and 2.1.319: not
  read; a change of late 2026-10-02 to 2026-10-08 would be missed.
- An open issue read at source: the three issues opened are all
  closed. An issue reported by the search as open and current
  (#108130, `skills:` not preloaded when an agent runs as the main
  session, "still present in 2.1.319") was not opened.
- Any vendor statement that a dependency range forces or schedules
  an update on the user's side.
- The marketplace reference and the troubleshooting page of
  dependency errors: not opened.

## Options

Read against the card's "why it matters": can each candidate carry
a shared reviewer contract and a required version of the base.

**A. Base and every layer as plugins, joined by `dependencies`
(candidates 2 and 4).** Carries the required version natively
(F1 to F3), shows a break, has a documented development loop with
no packaging (F5) and an update channel (F6). Costs: the reviewer
contract crosses a plugin boundary by a name the vendor does not
document (F10); the always-on instruction file has no plugin home
and its strongest substitute is deprecated (Unexpected); every
command becomes `/<plugin>:<name>` with the bare form only while
free (F8); strangers must switch auto-update on; one marketplace
for all packages or an allowlist per layer (F4); the base must be
tagged at every release (F2).

**B. No plugin: user-level and project-level configuration with
imports (candidates 3 and 5).** The contract preload works by bare
name, as it does today. Carries no required version at all: nothing
read detects a base older than a layer needs, and a missing
contract is skipped with a debug-log line only (F10). Collision
rules run opposite ways for skills and agents (F9), so a user's
own thing can silently replace or be replaced.

**C. One repository, the layers as plugin folders inside it
(candidate 1 with A's mechanism).** A marketplace file at the root
listing base and layers by relative path, or the folders passed to
`--plugin-dir`: in-place loading, no version bump in development
(F5), one place to tag (F2, the marketplace repository creates the
tags for relative-path plugins). For relative-path dependencies a
missing version is found at load, not at install (F3 b). Each
package still gets its own namespace.

**D. The base as a plugin, the framework staying a cloned
repository that enables it (candidates 4 and 6 mixed).** The
project's committed settings can declare the marketplace and enable
the base, but each user still installs it (F6); the framework's own
`.claude/agents/` would preload the base's contract across the
project-to-plugin boundary, the same unstated name as in A.

## Relevance to this project

Recommendation, the agent's own reading: the card's two tests have
different answers. *A required version of the base* is carried by
plugins and by nothing else in Claude Code; this rests on the
dependencies page returned whole [1] and is weakened only by
reports about the marketplace-entry form [8] and a defect fixed in
2.1.243 [9]. *A shared reviewer contract* across packages rests on
one unstated behaviour (F10): no vendor sentence says how a
plugin's skill is named in another package's agent, an old report
says it once failed in both forms [10], and a failure is silent. So
the plugin and package-per-layer candidates can be chosen only
after a trial, and the trial is small: two folders with a manifest
each, the layer's agent listing the base's contract skill once as
`<base>:<skill>` and once bare, loaded by `--plugin-dir`, then
installed from a local marketplace, the agent asked to quote a
sentence only the contract holds; the same from a project-level
agent. This is chosen against deciding from the documentation
alone, which cannot answer it, and against the no-plugin
candidates, which pass the contract test today and fail the
version test by construction. If the trial fails, the contract can
live in each layer (a copy the base's release writes, which the
frame rules out as a one-off export) or be read from disk by path
at the agent's start instead of preloaded; neither was researched
here. The instruction file remains the plugin candidates' second
open point, now with one substitute fewer.

Consult when: choosing between the plugin and the no-plugin
candidates; writing a `dependencies` or `engines` line; deciding
where the reviewer contract lives; setting the minimum Claude Code
version a stranger needs (2.1.243 for dependencies under
`--plugin-dir`, 2.1.265 for a folder of plugins, 2.1.296 for the
same-name hooks note, 2.1.323 for `engines`, 2.1.325 for commit-ID
pins); designing the release step that tags the base.

## Sources

1. "Plugin dependencies", Anthropic, Claude Code documentation;
   undated page, version notes to v2.1.265;
   https://code.claude.com/docs/en/plugins/dependencies.md;
   primary; read in full (page text returned whole by the fetch);
   original.
2. "Subagents" (sub-agents), Anthropic, Claude Code documentation;
   undated page, version notes to v2.1.296;
   https://code.claude.com/docs/en/sub-agents.md; primary;
   summarised fetch, twice, the first 100,000 of 116,580
   characters: the frontmatter reference, "Choose the subagent
   scope", "Preload skills into subagents" (reproduced by the fetch
   as in full), "Invoke subagents explicitly"; original.
3. "Skills", Anthropic, Claude Code documentation; undated page,
   version notes to v2.1.309;
   https://code.claude.com/docs/en/skills.md; primary; summarised
   fetch, twice, the first 100,000 of 119,637 characters: "Choose
   where skills load", "Resolve skills that share a name", "How a
   skill gets its command name", "Run a same-named skill from an
   added directory"; original.
4. "Add components to a plugin", Anthropic, Claude Code
   documentation; undated page, version notes to v2.1.310;
   https://code.claude.com/docs/en/plugins/components.md; primary;
   read in full (page text returned whole); original.
5. "Plugin loading reference", Anthropic, Claude Code
   documentation; undated page, version notes to v2.1.324;
   https://code.claude.com/docs/en/plugins/loading.md; primary;
   read in full (page text returned whole); original.
6. "Changelog", Anthropic, Claude Code documentation; entries dated
   on the page, newest 2.1.325 of 2026-11-13;
   https://code.claude.com/docs/en/changelog.md; primary;
   summarised fetch in three parts, characters 0 to 300,000 of
   1,275,367: versions 2.1.325 down to 2.1.295, with 2.1.319,
   2.1.304, 2.1.303 and 2.1.295 cut at the part boundaries;
   original.
7. "Plugin manifest reference", Anthropic, Claude Code
   documentation; undated page, version notes to v2.1.288;
   https://code.claude.com/docs/en/plugins/manifest-reference.md;
   primary; read in full (page text returned whole); original.
8. "[BUG] Marketplace-entry dependencies: version constraints
   silently ignored, prune deletes live dependencies", issue 88170,
   anthropics/claude-code, a user's report; opened 2026-08-20,
   closed "not planned" by the stale bot 2026-10-11 (dates as shown
   on the page);
   https://github.com/anthropics/claude-code/issues/88170; primary
   for the report, a practitioner claim; summarised fetch; original.
9. "[BUG] Plugin `dependencies` never resolve when the desktop app
   loads plugins via `--plugin-dir` …", issue 77801,
   anthropics/claude-code; opened 2026-07-15, closed completed
   2026-10-23 with a maintainer's "Fixed in Claude Code 2.1.243"
   (dates as shown on the page);
   https://github.com/anthropics/claude-code/issues/77801; primary;
   summarised fetch; original.
10. "Plugin agent skills: frontmatter silently fails to inject
    skill content", issue 25834, anthropics/claude-code, a user's
    report; opened 2026-02-15, closed completed 2026-02-17 (dates
    as shown on the page);
    https://github.com/anthropics/claude-code/issues/25834;
    primary for the report, a practitioner claim; summarised fetch;
    original.
11. "[BUG] `skills:` frontmatter not preloaded when agent runs as
    main session via `--agent` (still present in 2.1.319, follow-up
    to #67251)", issue 108130, anthropics/claude-code;
    https://github.com/anthropics/claude-code/issues/108130; not
    opened, the opening budget; named in Not found by its title
    from the search result only, cited for no content.
12. "claude plugin update does not resolve newly-declared plugin
    dependencies (install does)", issue 88663, and "enabledPlugins
    version constraints (array format) don't work", issue 46934,
    anthropics/claude-code;
    https://github.com/anthropics/claude-code/issues/88663 and
    https://github.com/anthropics/claude-code/issues/46934; not
    opened, the opening budget; cited for no content.

## Opened and not used

- "Settings reference", Anthropic,
  https://code.claude.com/docs/en/settings-reference.md: the fetch
  returned the first 100,000 of 457,162 characters, which end
  before the entries of `enabledPlugins` and its neighbours;
  nothing on the question in the part read.

## Search record

Queries, in order: (1) Claude Code plugin dependencies version
range plugin.json; (2) Claude Code subagent "skills" field preload
plugin skill namespace; (3) on github.com, anthropics/claude-code
issue, plugin agent "skills" frontmatter, plugin skill not
preloaded, namespace; (4) on github.com, anthropics/claude-code
issue, plugin dependencies version constraint not resolved;
(5) Claude Code plugin.json engines "claude-code" version range
plugin not loaded.

Openings, fifteen: the dependencies page; the subagents page,
twice; the skills page, twice; the components page; the loading
reference; the changelog, three parts; the manifest reference;
issues 88170, 77801 and 25834; the settings reference.

The disconfirming query (3 and 4) found reports on both behaviours.
Read at source: version ranges in a marketplace entry silently
ignored (closed unfixed by the stale bot) [8]; dependencies never
resolving under `--plugin-dir` in the desktop app (fixed in
2.1.243) [9]; preload of plugin skills by plugin agents failing in
both name forms (closed "completed", fix not described) [10]. The
expectation "at least one open issue" was not confirmed at source:
all three opened are closed; the search listed one as open and
current (#108130) that was not opened.

The run ended on the opening budget of the brief. By the card's
stop rule every sub-question has a vendor statement or is recorded
as not stated, with two remainders said under Not found: the
changelog of 2.1.289 to 2.1.294 and the settings entry of
`enabledPlugins`.
