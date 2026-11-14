---
date: 2026-11-14
project: forge
topic: how comparable frameworks deliver a core with packs in November 2026 and how an update reaches a project
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-14-anvil-carrying-layers/08-field-delivery
derived_from: research/2026-11-14-anvil-carrying-layers/00-plan.md, card 8; 2026-08-29-framework-distribution-in-the-field.md; 2026-10-03-one-tool-a-core-with-modules-or-several-tools.md; web sources below
---

# Comparable frameworks deliver a core with packs in four old ways and one new one, and none left plugins

## In short

Ten of the eleven frameworks were read at their own repository on
2026-11-14; Agent OS is "not checked" (its README carries no
installation). Nobody changed architecture wholesale since August,
with one exception that matters: BMAD is leaving its own npm
installer for the generic Skills CLI (`npx skills add`, `npx skills
update`) in its v7 preview, each module a folder of one repository,
installed whole; its stated reason was not found. The same Skills
CLI now appears as an install route at LeanSpec and wshobson/agents,
so the field has a fifth way of delivery that the August note did
not have: a third-party package manager for skills. Plugins held and
spread: Superpowers (v7.0.2) and Conductor added native plugins for
more harnesses, wshobson added a Codex marketplace. The frameworks
that copy into the project (Spec Kit, OpenSpec, cc-sdd) stayed
there; Spec Kit added pinning of catalogue items to exact releases.
The disconfirming query found no framework of the eleven that moved
from plugins back to a clone or installer; the one case found
outside the eleven was a proposal closed without merge. No published
comparison of plugin against installer against clone was found.
Everything rests on summarising fetches, so every quotation below is
to be checked at its URL before it is quoted onward. Unexpected:
Superpowers, the August note's model of "nothing lands in the user
repo", now keeps a workspace in the user's repository.

## Question

> #### Card 8: How comparable frameworks deliver a core with packs today
> - **Question:** How do the comparable frameworks for AI coding agents deliver a core with packs, modules or extensions in November 2026, and how does an update reach an existing project: which moved to plugins, which install globally, which copy into the project, which keep one repository? What moved since August 2026? Does a published comparison of these ways of distribution already exist, and in what words does the field speak of them?
> - **Why it matters:** The candidates are the field's four architectures seen from this project; what the field moved toward and away from in three months is the cheapest evidence of what holds.
> - **What would answer it:** The repositories, release notes and installation documentation of the frameworks, read at source.
> - **Where to look:** The repositories and release notes of the frameworks the attached note of August 2026 names (Spec Kit, BMAD, OpenSpec, Superpowers, Agent OS, cc-sdd, Conductor, GSD, LeanSpec, wshobson/agents, claude-task-master) and of any that appeared since; published comparisons of plugin against installer against clone. Must turn up: a framework that changed its way of distribution in 2026 and its stated reason.
> - **Disconfirming query:** A search for a framework that moved away from plugins back to a clone or an installer; expected: none or one.
> - **Stop rule:** Each of the eleven has its way of distribution today from its own repository, or "not checked"; a comparison found or recorded as not found; the opening budget.

The baseline is the note of 2026-08-29, which found four
architectures (plugin only; engine installed once globally with a
thin state file; engine copied into every repository; one source
tree with generated artefacts) and three mechanisms for surviving an
upgrade, and the note of 2026-10-03, which found a core with typed
modules everywhere and retreats from distribution machinery (BMAD's
remote registry, Superpowers' skills repository). This note must say
what moved in the eleven since, not repeat them.

## Key findings

**F1. BMAD is changing its way of distribution: from its own npm
installer to the generic Skills CLI, with modules as folders of one
repository.** [single source; vendor documentation and changelog,
read through a summarising fetch] The README gives two lines: the
stable v6.12 by `npx bmad-method install`, described as "frozen
aside from bug fixes", and a "V7 Preview Alpha" installed by `npx
skills add bmad-code-org/BMAD-METHOD/skills/core-tools --skill '*'`
and the same for `skills/method`, after which the `bmad` skill runs
`bmad setup` inside the coding tool [1]. The unreleased section of
the changelog says "Each module ships in its own folder:
`skills/core-tools/`, `skills/method/`, `skills/toolsmith/` and
`skills/founder/`", and that the Builder module, which the note of
2026-10-03 found in a repository of its own, "joins this repository
as Toolsmith, a first draft for v7" [2]. An update reaches a project
by asking the `bmad` skill for `bmad setup`, which "checks each
module's version and runs `npx skills update` for you when there is
a newer one"; a v6 project is brought over by `bmad migrate method`
[2][3]. The project still receives `_bmad/` (shared runtime and
module scripts), `_bmad/custom/` and `_bmad-output` [3]; the copy
into the project stays, only the carrier changed. The README's ETA
for the release is "mid-November 2026" [1]. The reason for the move
is stated nowhere in what was read [1][2][3]. Conflict: a search
engine's digest said the BMAD install documentation also offers a
plugin marketplace route with two plugins; the page as opened shows
none [3], and the README mentions none [1]. The August note's
finding of a `.claude-plugin/marketplace.json` in the repository was
not re-verified.

**F2. A generic Skills CLI is now an install route at three of the
eleven; in August it was at none as a primary route.** [emerging;
vendor documentation of three projects, summarising fetch] BMAD v7
(F1), LeanSpec (`npx skills add codervisor/leanspec@leanspec`, beside
`npm install -g @leanspec/cli && leanspec init` and an MCP server)
[4], and wshobson/agents, which offers `gh skill install
wshobson/agents <skill>` and `npx skills add wshobson/agents --skill
<skill>` as a route that carries skills only, without the plugins'
agents, commands or hooks [5]. That the route carries skills and
nothing else is the limit that matters for a framework with hooks,
agents and scripts: BMAD gets around it by letting a skill install
"the shared runtime and module scripts" into the project afterwards
[3]. That this is a trend is the agent's own inference from three
repositories, not a statement of any of them.

**F3. The plugin frameworks stayed plugins and widened to more
harnesses' native plugin systems.** [consensus among the three
plugin-first projects; vendor release notes and READMEs, summarising
fetch] Superpowers is at v7.0.2 (2026-11-03), with v7.0.0 on
2026-10-09; its notes since August record a native Antigravity
plugin ("`agy plugin install https://github.com/obra/superpowers`
now installs Superpowers as a native Antigravity plugin", where
before the harness "fell back to importing the repo as a Gemini CLI
extension"), a native manifest for one more harness and an extension
install for another [6]. Conductor describes itself as "a plugin for
AI coding agents (including Antigravity and Claude Code)", installed
in Claude Code by `/plugin marketplace add
gemini-cli-extensions/conductor` and `/plugin install conductor`,
with a developer route of a clone linked by symlink into the
harness's plugin directory so that edits load live; no update
command is documented [7]. wshobson/agents has 94 plugins ("92 local
plugins and 2 external entries"), a Claude Code marketplace, a
native Codex marketplace, a Cursor registry, and a clone with `make
install-<tool>` for four further harnesses, where "Each target
generates the artifacts and links all local plugins into that tool's
user configuration" [5]. None of the three documents how an update
reaches a user beyond the harness's own plugin update.

**F4. The frameworks that copy an engine into the project stayed
there, and the two with a separate CLI keep the two-part update.**
[consensus among the three; vendor documentation and changelog,
summarising fetch] Spec Kit is at 1.4.0 (2026-11-10), twenty-eight
releases after 1.0.1 of 2026-08-21; nothing in the changelog after
August mentions a Claude Code plugin or a change of distribution;
what moved is the catalogue: "select exact catalog releases" for
extensions (1.1.0, 2026-10-02), presets (1.1.1) and bundles (1.1.2),
"allow newer packaged patch releases with warnings" for bundles
(1.2.0, 2026-10-13) and "Require HTTPS consistently for catalog
sources" (1.4.0) [8]. Only the first 100,000 characters of that
changelog were read. OpenSpec now leads with a standalone installer
(`curl -fsSL https://openspec.dev/cli/install.sh | sh`, a PowerShell
equivalent, Homebrew, and npm), keeps the split of tool and project
("Run this inside each project to regenerate AI guidance and refresh
the installed skills", `openspec update`), delivers its commands as
skills, lists community schemas as "Third-party schema bundles
distributed via standalone repositories", and has Stores still in
beta [9]; the August note recorded npm only, so the standalone
installer and Homebrew appear to be new, undated here. cc-sdd is
still `npx cc-sdd@latest` run in the project, one flag per harness,
`--dry-run` as the guard, no plugin [10]; its version and date were
not shown on the page.

**F5. GSD: the original repository is archived, the successor
installs by npx globally or locally, and a plugin route was proposed
by users repeatedly and never taken by the maintainers.** [single
source each; repository pages, summarising fetch] The page of
discussion 3432 in `gsd-build/get-shit-done` shows that repository
archived and read-only since 2026-06-26; the discussion (opened
2026-05-12 by a community member) proposes a `--claude-plugin`
install mode, counts six earlier issues and pull requests asking the
same, reports one of them rejected as "too hacky", and has no
maintainer reply; a second community member lists traps met in his
own plugin fork (the plugin root variable unset in the shell tool's
environment, dependencies that must be bundled) [11]. The successor
`open-gsd/gsd-core` installs by `npx @opengsd/gsd-core@latest`,
asking "globally or locally"; its file listing shows a
`.claude-plugin` folder, but no plugin install is documented on the
page [12]. Conflict, not resolved: the page links "What's new in
1.7.0", while the August note recorded v1.11.0 for the same
repository; the version today is not established.

**F6. claude-task-master leads with MCP, not with its plugin.**
[single source; vendor README, summarising fetch] The README's
"Option 1: MCP (Recommended)" comes before the command line (`npm
install -g task-master-ai`), with `claude mcp add taskmaster-ai --
npx -y task-master-ai` for Claude Code; the page as fetched does not
describe a marketplace install [13]. The plugin document the August
note read (`CLAUDE_CODE_PLUGIN.md`) was not re-opened; a search
listing still shows its marketplace commands, which is not a
finding.

**F7. Agent OS: not checked.** The README as fetched carries no
installation at all and points to the maintainer's documentation
site, which was not opened; no archive notice on the repository
[14]. The August finding (base install in the home directory plus a
project install script) stands unverified for November.

**F8. Superpowers no longer leaves the user's repository empty.**
[single source; vendor release notes, summarising fetch; the
inference marked] The notes of v7.0.0 and v7.0.2 speak of an
`sdd-workspace` that keeps a workspace under `.superpowers/sdd/` of
the repository ("`sdd-workspace` leaves a repo's own
`.superpowers/sdd/.gitignore` alone"; "Outside a repository,
`sdd-workspace` used to write its workspace into whatever directory
the agent was in, often the plugin cache"; the agent "will need to
run `git init` and make a first commit before it can start") [6].
That this is working state and not engine files is the agent's
reading; the August sentence "nothing lands in the user repo" no
longer holds as written.

**F9. No published comparison of the ways of distribution was
found; the field's words are those of the harnesses and of the
package managers.** [not found; searches and one opened comparison]
The one comparison opened (a personal blog, 2026-05-18, three
frameworks) compares workflow only and says nothing of installing or
updating [15]. Others in the result lists compare method, not
delivery, and were not opened. The words the primary sources use:
"plugin" and "plugin marketplace" [5][7]; "installer" [2][11];
"skills" and the "Skills CLI" [3]; "module", each "installed whole"
[1][2]; "catalog" with "exact catalog releases" for extensions,
presets and bundles [8]; "globally or locally" and "project and
global installation scopes" for where an install lands [12][3];
"schema bundles distributed via standalone repositories" [9];
"stable" against "preview alpha" for release lines [1]. No source
read uses a shared name for the architectures as such; the August
note's four names remain the project's own.

**F10. The disconfirming query found none among the eleven and one
unmerged proposal outside them.** [single source; a pull request
page, summarising fetch] In `databricks-solutions/ai-dev-kit`, pull
request 548, "retire .claude-plugin/: a-d-k stops being a Claude
Code plugin" (commits of 2026-05-24), was closed without merge on
2026-07-02; its reasons were local ("With nothing useful to declare,
the file goes too", "The plugin-install path for MCP was always
niche"), and its replacement was the vendor's own CLI plus a plugin
marketplace in another repository, so even the proposal was a move
between carriers, not away from plugins [16]. BMAD's move (F1) is
from an installer to a skills package manager, not from a plugin.

## Unexpected

- The card's list of ways (plugin, global install, copy, one
  repository) has no place for the Skills CLI, which is none of
  them: a third-party package manager that copies skills into the
  project or the user scope and updates them by one command, with
  per-module addressing by a path inside one repository [1][3][5].
  It carries skills only; BMAD needs a second step inside the
  session to install scripts and configuration [3]. For a framework
  whose core is an always-on instruction file, hooks, agents and
  scripts this is a lead on what the field found cheap, not a
  candidate as it stands. The candidates of the frame do not name
  it.
- BMAD brought a module back from a repository of its own into the
  main repository in the same move (Builder as Toolsmith) [2], the
  reverse of its January split recorded on 2026-10-03: one
  repository, modules as directories, each installable alone. This
  is the frame's candidate 1 with a per-directory install on top.
- Conductor's developer install is a clone linked by symlink into
  the harness's plugin directory, edits loading live [7]: a
  development loop without packaging, documented by a plugin
  framework for the other harness. Whether Claude Code has an
  equivalent was not checked in this card.
- The community's own experience with turning an installer framework
  into a Claude Code plugin lists concrete traps (plugin root
  variable absent in the shell tool, dependencies to bundle, path
  rewriting) [11]; a practitioner claim, from a fork, undated beyond
  May 2026.

## Not found

- BMAD's stated reason for moving to the Skills CLI: not in the
  README, the install page, or the first 100,000 characters of the
  changelog [1][2][3]. The card's "must turn up: a framework that
  changed its way of distribution in 2026 and its stated reason" is
  met in the first half only; the one reason BMAD states nearby
  concerns web bundles, not the installer [2].
- A published comparison of plugin against installer against clone:
  none in two searches and one opened article [15].
- How an update of a plugin reaches users, in the words of any of
  the three plugin frameworks: none documents it [5][6][7].
- Agent OS's installation today; versions and dates of the newest
  releases of OpenSpec, cc-sdd, Conductor, LeanSpec, task-master and
  GSD Core (the fetched repository pages showed empty release
  sections).
- A framework new since August that belongs beside the eleven: none
  was opened; names in result lists (not opened) are not findings.
- Any framework of the eleven moving to a Claude Code plugin since
  August: none; GSD Core has a `.claude-plugin` folder whose purpose
  is undocumented on the page read [12].

## Options

The card asks for facts; the choice among the frame's candidates is
the bundle's synthesis. What this card lets the project do with
them:

- Read candidate 4 (plugin) as the one way the field kept and
  widened in three months, with no retreat on record, at the price
  the plugin frameworks all pay: no documented update story of their
  own and, at Superpowers, working state in the user's repository
  after all.
- Read candidate 1 (one repository, layers as directories) as the
  shape BMAD just moved back to for its modules, made deliverable by
  per-directory installation; the carrier there is the Skills CLI,
  which cannot carry what the present framework consists of.
- Treat copy-into-project with a separate CLI (Spec Kit, OpenSpec)
  as stable but still paying for it: exact-release pinning of
  catalogue items is the newest instalment.
- Take Conductor's symlinked clone as a pattern for the development
  loop, to be checked against Claude Code's own mechanisms by the
  card that owns them.

## Relevance to this project

The agent's own inferences, on F1 to F10. The field did not move
away from any of the August architectures; it added carriers. What
held without a single retreat is delivery through the harness's own
plugin system, and what changed hands is the home-made installer:
BMAD is giving its own up for a generic package manager, as
Superpowers gave up its home-made skills repository a year earlier
for the harness's native one. The pattern across both, said as an
inference: distribution machinery a framework writes itself is what
gets replaced, and it is replaced by whatever the harness or a
common tool provides. For a split into a base, layers and a user's
own place, that speaks for a carrier the project does not have to
maintain, and against a script of its own that separates and ships
the base, unless that script only feeds such a carrier. It is chosen
here against the reading that the field is "moving to plugins":
three of the eleven moved toward a skills package manager, not
toward plugins, and the copy-into-project frameworks did not move at
all. How a layer says which version of the base it needs has one new
data point only, Spec Kit's exact-release selection; nothing in this
card measures how often users are forced to update. The evidence is
thin where it matters most: every page came through a summarising
fetch, and no maintainer's reason for the one real change was found.

Consult when: the candidates of the split are weighed and someone
asks what the neighbours do today; a carrier for the base is chosen
(plugin, package manager, installer of one's own); BMAD v7 is
released and its reasons may be published; the claim "nothing lands
in the user's repository" is used as a design goal.

## Sources

1. BMAD-METHOD, repository page with README, bmad-code-org; undated
   (page as served 2026-11-14);
   https://github.com/bmad-code-org/BMAD-METHOD; primary; summarised
   fetch of the whole page; original.
2. BMAD-METHOD CHANGELOG.md, bmad-code-org; newest dated release
   v6.12.0, 2026-09-03, dated by the file's own headings, with an
   undated Unreleased section above it;
   https://raw.githubusercontent.com/bmad-code-org/BMAD-METHOD/main/CHANGELOG.md;
   primary; summarised fetch, partially: the first 100,000 of
   164,079 characters (Unreleased to about v6.11.0); original.
3. "How to Install BMad", BMAD documentation, bmad-code-org;
   undated; https://docs.bmad-method.org/start/install-bmad/;
   primary; summarised fetch of the whole page; original.
4. LeanSpec, repository page with README, codervisor; undated;
   https://github.com/codervisor/leanspec; primary; summarised fetch
   of the whole page; original.
5. wshobson/agents, repository page with README; undated;
   https://github.com/wshobson/agents; primary; summarised fetch of
   the whole page; original.
6. Superpowers RELEASE-NOTES.md, obra; newest v7.0.2, 2026-11-03,
   dated by the file's own headings;
   https://raw.githubusercontent.com/obra/superpowers/main/RELEASE-NOTES.md;
   primary; summarised fetch, partially: the first 100,000 of
   120,464 characters (v7.0.2 back past v6.4.1); original.
7. Conductor, repository page with README, gemini-cli-extensions;
   undated; https://github.com/gemini-cli-extensions/conductor;
   primary; summarised fetch of the whole page; original.
8. Spec Kit CHANGELOG.md, github; newest 1.4.0, 2026-11-10, dated by
   the file's own headings;
   https://raw.githubusercontent.com/github/spec-kit/main/CHANGELOG.md;
   primary; summarised fetch, partially: the first 100,000 of
   152,456 characters (1.4.0 back past 1.0.2); original.
9. OpenSpec, repository page with README, Fission-AI; undated;
   https://github.com/Fission-AI/OpenSpec; primary; summarised fetch
   of the whole page; original.
10. cc-sdd, repository page with README, gotalab; undated;
    https://github.com/gotalab/cc-sdd; primary; summarised fetch of
    the whole page; original.
11. "Claude Code plugin packaging (--claude-plugin install)",
    discussion 3432, gsd-build/get-shit-done; opened 2026-05-12,
    replies 2026-05-13, dated by the page's own timestamps as the
    fetch reported them;
    https://github.com/gsd-build/get-shit-done/discussions/3432;
    primary for the proposal and the archive notice, practitioner
    claims for the traps; summarised fetch of the whole page;
    original.
12. GSD Core, repository page with README, open-gsd; undated;
    https://github.com/open-gsd/gsd-core; primary; summarised fetch
    of the whole page; original.
13. claude-task-master, repository page with README, eyaltoledano;
    undated; https://github.com/eyaltoledano/claude-task-master;
    primary; summarised fetch of the whole page; original.
14. Agent OS, repository page with README, buildermethods; undated;
    https://github.com/buildermethods/agent-os; primary; summarised
    fetch of the whole page; original. Cited only for what the page
    lacks.
15. "Comparing SDD Frameworks: spec-kit vs OpenSpec vs
    get-shit-done", Kai Hendry, 2026-05-18 (byline as the fetch
    reported it);
    https://dabase.com/blog/2026/sdd-framework-comparison/;
    secondary, a personal blog; summarised fetch of the whole page;
    original. Cited only for not comparing distribution.
16. "retire .claude-plugin/: a-d-k stops being a Claude Code
    plugin", pull request 548, databricks-solutions/ai-dev-kit;
    commits 2026-05-24, closed unmerged 2026-07-02, dated by the
    page's own timestamps as the fetch reported them;
    https://github.com/databricks-solutions/ai-dev-kit/pull/548;
    primary; summarised fetch of the whole page; original.

## Opened and not used

- https://docs.bmad-method.org/how-to/install-bmad/ : a redirect
  notice only, superseded by [3].

## Search record

Queries, in order:
1. spec-driven frameworks, Claude Code plugin against installer
   against clone, distribution comparison 2026.
2. Spec Kit release notes November 2026, Claude Code plugin
   marketplace install.
3. The disconfirming query: a framework that "moved away from" a
   Claude Code plugin back to an installer or a clone, with reason.
4. BMAD v6 changelog, plugin marketplace, installer, October 2026.
5. BMAD v7 `npx skills add`, why skills instead of the installer,
   announcement.
6. task-master, LeanSpec, wshobson/agents, Conductor: Claude Code
   plugin install, 2026 release.

Pages opened (seventeen fetches, one of them a bare redirect): the
sixteen sources above and the redirect listed under Opened and not
used. All fetches returned a small model's summary, not the page;
three changelogs were read in their first 100,000 characters only.

The disconfirming query found no framework of the eleven that left
plugins; outside them, one proposal to retire a plugin manifest,
closed without merge [16]. Two further hits of that search were not
opened: a pull request of a skills installer described in the result
list as moving from Claude Code plugins to a multi-agent skills
installer, and a pull request moving an install script to the plugin
system (the opposite direction).

The run ended on the opening budget, slightly exceeded, with the
stop rule met in substance: ten of the eleven have their way of
distribution today from their own repository, Agent OS is "not
checked", and a comparison is recorded as not found.
