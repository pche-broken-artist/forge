---
date: 2026-11-14
project: forge
topic: a stranger's first day under each of the six candidates
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-14-anvil-carrying-layers/10-first-day
derived_from: research/2026-11-14-anvil-carrying-layers/00-plan.md, card 10; 2026-08-29-framework-distribution-in-the-field.md; web sources below
---

# What a stranger must do before the first prompt under each of the six candidates

## In short

Every candidate can be brought to two or three typed commands, and
published frameworks of every kind word the first step in two or
three lines. The candidates differ less in the count than in what
is asked of the stranger on the way and in what can go wrong without
a word. A clone to work in (candidates 1 and 6) costs a clone, a
start and one trust dialog, and leaves the base's plumbing among the
stranger's files. A plugin (candidate 4) costs two commands for a
third-party marketplace (one since v2.1.275), a details pane with a
trust warning, a choice among three scopes and an install summary
with four outcomes, and leaves nothing of the base in his
repository; it is also the kind with a documented silent failure,
still open at the vendor, and its updates are off by default for
every third-party marketplace. An import across two repositories
(candidate 3) adds a second clone and a second dialog whose refusal
is permanent and silent. User-level configuration (candidate 5)
needs no dialog at all but writes into the stranger's home. The
disconfirming query found what was expected: reports of plugin
installs that claim success and load nothing. Sureness: high for
the vendor's steps and prompts, read in full at source on
2026-11-14; lower for the frameworks' READMEs, read through a
summarising fetch. The unexpected: a plugin laid in the
repository's own `.claude/skills/` loads in place for whoever
clones and trusts the folder, with no install step at all.

## Question

#### Card 10: A stranger's first day under each candidate
- **Question:** What must a stranger arriving from GitHub do before the first prompt under each of the six candidates: what is cloned, what is installed and from where, what is registered or trusted, what must be on the machine, in how many steps and with which of them able to fail silently? What does he see in his project's repository afterwards: his own files alone, or the base's plumbing among them? How do published frameworks word this first step, and how long is it?
- **Why it matters:** The framework is public; a way that serves the author's update and loses the stranger at installation fails the perspective nobody else in the plan speaks for.
- **What would answer it:** The installation sections of published frameworks of each kind, read at source, and the vendor's documentation of installing a plugin and trusting a marketplace or a project.
- **Where to look:** The README and installation documentation of frameworks distributed as a plugin, as a global install, as a copy into the project and as a clone to work in; Anthropic's documentation of plugin installation, marketplace trust and project trust prompts. Must turn up: the exact steps of installing a plugin from a third-party marketplace, the prompts a first run shows.
- **Disconfirming query:** A search for reports of users failing at installation of a plugin-distributed framework; expected: some.
- **Stop rule:** Each candidate has a counted list of first-day steps from a primary source or from a framework of that kind; the opening budget.

The frame of the card: a framework on Claude Code (one always-on
instruction file, skills, isolated subagents, hooks, templates,
Python scripts, one public repository a user clones and works in) is
to be split into a general base, the present framework as the first
operating layer, later layers and a place for what a user makes for
himself; the six candidates are (1) one repository with the layers
as directories, (2) the base as a package and each layer a
repository, (3) two repositories joined by an import of one
instruction file into the other, (4) a Claude Code plugin, possibly
with its own marketplace, (5) Claude Code's own mechanisms without a
plugin, (6) the whole kept as one, a script separating the base at
every release into a public repository from which other projects
update.

The baseline to beat: the note of 2026-08-29 classified eleven
frameworks by where the engine lives and how an upgrade reaches a
project. It says nothing of the first day: no step is counted, no
prompt is named, no silent failure is recorded, and the vendor's own
documentation of installing and trusting is not read in it.

## Key findings

F1. **Installing a plugin from a third-party marketplace is two
typed commands and four things to read or choose; one command since
v2.1.275.** [vendor claim; vendor documentation of its own product,
read in full] The marketplace is added first
(`/plugin marketplace add owner/repo`, or a git URL, a local path
or a hosted `marketplace.json`), then `/plugin install
<plugin>@<marketplace>`. In a session the install command "doesn't
install right away": it opens the details pane, where the stranger
reads what will be installed, chooses one of three scopes (user,
project, local), then reads an install summary whose last sentence
is one of four outcomes: active now, active but a server needs
setup, reload needed, load failed. The vendor's own walkthrough
numbers this as five steps, the fifth being to confirm that the
skills appear under `/<plugin>:<skill>`. Both steps fold into one
with `/plugin install <plugin> --marketplace owner/repo` (needs
v2.1.275 or later; asks to confirm the resolved source), or
`claude plugin install <plugin> --marketplace owner/repo` from the
shell (v2.1.292 or later; "adds the marketplace without a
confirmation step") [1]. The marketplace page puts the promise in
one sentence: anyone with access "registers it in Claude Code with
one command and installs your plugins from it" [2].

F2. **The prompts of a plugin install are one fixed trust warning
and nothing that verifies the plugin.** [vendor claim; vendor
documentation, read in full] The details pane shows the same warning
for every marketplace, opening "Plugins can run code on your
computer, with access to your files and shell." The page opens
with: "A Claude Code plugin you install can execute arbitrary code
on your machine with your user privileges." Hooks, monitors and
servers of a plugin run outside the sandbox and outside the
permission rules. For a plugin of a custom marketplace the pane may
show only "Components will be discovered at installation", so the
stranger is told that a hook exists at most, never what it runs
[1][3].

F3. **Nothing of a marketplace plugin lands in the stranger's
repository, unless he chooses project scope.** [vendor claim; vendor
documentation, read in full] A marketplace plugin is copied to
`~/.claude/plugins/cache/<marketplace>/<plugin>/<version>/`; the
marketplace's clone lies under `~/.claude/plugins/marketplaces/`;
user scope writes `enabledPlugins` into `~/.claude/settings.json`.
Only project scope writes into the repository, one entry in
`.claude/settings.json` [1][4]. Two consequences for a base shipped
this way, both the vendor's words: "Files outside the plugin
directory aren't copied", and `${CLAUDE_PLUGIN_ROOT}` "changes with
every version", so durable files belong in `${CLAUDE_PLUGIN_DATA}`
[4].

F4. **A repository cannot install its plugin for the stranger who
clones it; it can only declare it, and the gap shows on an Errors
tab.** [vendor claim; vendor documentation, read in full] "Committing
that entry turns the plugin on for your collaborators but doesn't
download it to their machines. Each collaborator also runs `claude
plugin install <name>@<marketplace> --scope project` once per clone"
[1]. A plugin enabled only in project settings "doesn't load at
session start until you install it on your machine"; the message is
on the `/plugin` Errors tab, not in the conversation. A plugin with
an external source is fetched only when user settings, an untracked
local settings file, the `--settings` flag or managed settings turn
it on, never on the repository's word. The marketplaces a repository
names in `extraKnownMarketplaces` are used only after the workspace
trust dialog for that exact folder; trusted through a parent folder
they are "Not used, and no dialog is offered" [4][5]. The same page
[4] also says that a marketplace settings declare and the machine
lacks is cloned in the background and enabled plugins not yet
cached are downloaded; the two statements are read together here as
"the marketplace arrives, an external-source plugin still waits for
the install", which is this note's reading, not the vendor's
sentence.

F5. **A clone to work in costs a clone, a start and one trust
dialog, and the dialog names what the folder would switch on.**
[vendor claim; vendor documentation, the sections on trust read in
full from the page's text] Project allow rules and additional
directories of `.claude/settings.json` apply "only after you accept
the workspace trust dialog for that folder", and the dialog lists
them. Trust is keyed on the root of the git repository and covers
it "apart from any git repository nested inside it"; a nested
repository gets a dialog of its own in an interactive session. The
dialog appears in interactive terminal sessions, "but not in
`claude -p` or SDK sessions". Hooks of the settings files are used
even where only a parent folder was trusted and in `-p` runs [5].
What the dialog's own text reads was not found on the pages opened.

F6. **An import that crosses out of the working directory adds a
second dialog, and a refusal is permanent and silent.** [vendor
claim; vendor documentation, the sections on imports read in full
from the page's text] `@path` imports may be relative or absolute,
recursive to "a maximum depth of four hops". An import of a
project-level file whose path resolves outside the working
directory is external: "The first time Claude Code encounters
external imports in a project, it shows an approval dialog listing
the files. If you decline, the imports stay disabled and the dialog
doesn't appear again." A symlinked rule file pointing outside the
working directory is treated the same way, one approval per
project. On Windows a committed symlink is checked out "as a plain
text file unless `core.symlinks` is enabled", which leaves a
one-line file in place of the instructions [6]. For candidate 3
this means: two clones in a relation the import's path must match,
a start, the trust dialog and the import dialog; an import carries
instruction text only, the skills, agents and hooks of the other
repository do not come with it (the last clause is this note's
inference from what the page says an import is, not a sentence of
it).

F7. **User-level configuration needs no dialog at all.** [vendor
claim; vendor documentation, same reading] User-scope files, such
as `~/.claude/CLAUDE.md` and `~/.claude/rules/`, "are files you
wrote yourself"; their imports load without the dialog, and rules
in `~/.claude/rules/` "apply to every project on your machine" [6].
A plugin folder under the stranger's own `~/.claude/skills/` is
exempt from the trust check and the component limits that hold for
one in a repository [4]. The price is the other side of the same
fact: whatever puts the base there writes into the stranger's home,
and it reaches every project of his, not the one he came for.

F8. **Published frameworks word the first step in two or three
lines, whatever their kind.** [practitioner claim; the frameworks'
own READMEs, each read through a summarising fetch, so the counts
are the fetch's reading of the page]
- Plugin (Superpowers): two commands through its own marketplace,
  `/plugin marketplace add obra/superpowers-marketplace` and
  `/plugin install superpowers@superpowers-marketplace`, or one
  through the official marketplace; no prerequisite named, no step
  to verify, and on updates only that they "are often automatic"
  [7].
- Global install (GSD Core): one command, `npx
  @opengsd/gsd-core@latest`; the installer then asks which runtime
  and whether globally or locally; a second command starts a
  project (`/gsd-new-project` or `/gsd-onboard`). Node.js is
  assumed, with a link for those without it; the README warns
  against copying the files by hand [8].
- Package plus a copy into the project (Spec Kit): prerequisites
  Python 3.11+, uv and a supported agent; `uv tool install
  specify-cli`, `specify init my-project --integration <agent>`,
  `cd my-project`, then the agent is started: three commands and a
  start. Troubleshooting is a page of its own [9].
- Clone to work in, later updated from its origin (Claudesidian):
  clone the repository under a name of one's own or download the
  ZIP, start `claude` in it, run `/init-bootstrap`: three steps.
  The bootstrap installs dependencies, disconnects the copy from
  the original repository, writes a personal CLAUDE.md and
  initialises git; later `/upgrade check` and `/upgrade` bring the
  system files up to date with a backup and a diff per file, the
  content folders left alone [10].

F9. **Counted first-day steps per candidate.** [this note's
synthesis of F1 to F8; the counts are the note's own, each resting
on the source named] Common to all six: Claude Code installed and
signed in, git, and `python` on PATH for the framework's scripts.

| Candidate | Typed steps before the first prompt | Dialogs and choices | In the stranger's repository | Rests on |
|---|---|---|---|---|
| 1 one repository, layers as directories | clone, `cd`, `claude`: 3 | trust dialog: 1 | everything: base, layer and his own files in one tree | [5], [10] |
| 2 base a package, each layer a repository | install the base, then clone or initialise the layer, start: 3 to 4 | trust dialog; the package manager's own | his files and the layer; the base outside, or copied in as with [9] | [9], [5] |
| 3 two repositories joined by an import | two clones in a fixed relation, start: 4 | trust dialog and external-import dialog: 2 | the layer's files; the base beside it, outside | [6], [5]; no framework of this kind found |
| 4 plugin, own marketplace | add marketplace, install: 2 (1 since v2.1.275); plus whatever scaffolds the project | details pane with warning, scope, install summary, possibly reload | nothing of the base; one settings entry at project scope | [1], [3], [4], [7] |
| 5 user-level configuration and imports | one install or copy into `~/.claude`, start: 2 | none from Claude Code; the installer's own questions | nothing of the base, or a thin state file | [6], [4], [8] |
| 6 the whole kept, the base separated at release | as 1 for the framework; for a project on the base: clone or copy the base's repository, start, bootstrap: 3 | trust dialog: 1 | the base's plumbing among his files | [10], [5] |

F10. **Which steps can fail without a word.** [vendor claim for the
mechanisms; single source for the field report]
- Plugin: an install that reports success and loads nothing. The
  vendor's tracker carries it as issue 14815, opened 2025-12-20 and
  still open as read on 2026-11-14: "No error messages displayed.
  The installation appears to succeed silently but the plugins are
  not loaded." Later comments report it on v2.1.19 and v2.1.66; a
  maintainer wrote on 2026-03-05 that the team was investigating
  why installs sometimes fail silently [11].
- Plugin: updates. Auto-update is off by default for "every other
  marketplace, including the community marketplace, third-party
  marketplaces, and local development marketplaces"; "There's no
  command that updates every plugin at once" [1]. A manifest that
  pins a version "keeps every user on the cached copy until its
  author changes the string, however many commits they push" [4].
  The stranger of a third-party plugin stays on his first day's
  version until he acts.
- Plugin: a plugin folder skipped under an organisation's managed
  settings shows "no plugin and no error"; a `--plugin-dir` copy
  replaces an installed plugin of the same name "silently", visible
  only in the debug log [4].
- Plugin: Node dependencies. They are installed only where a
  `package.json` and a supported lockfile lie in the plugin's root,
  lifecycle scripts never run, and after a failed install "the
  plugin still loads" with a note in `/plugin`; Python dependencies
  are not installed at all and are left to a hook [4].
- Import: a declined external-import dialog never returns (F6).
- Clone: in a folder trusted only through its parent, the
  repository's marketplaces and a project plugin's hooks are "Not
  used, and no dialog is offered" [5].
- All six: a missing `python` on PATH is this note's own inference
  as a silent failure of hooks and scripts; no source was read on
  how Claude Code reports a hook whose command is not found.

F11. **One published framework keeps its installation steps behind
an email form.** [single source; the page itself, summarised fetch]
The installation page of Agent OS showed no command on 2026-11-14,
only "Enter your email for instant access and setup instructions"
[12]. The steps the note of 2026-08-29 gives for it were read from
its repository's scripts, not from this page.

## Unexpected

A plugin needs no marketplace and no install when it lies in the
repository itself. A directory with `.claude-plugin/plugin.json`
under the project's `.claude/skills/` loads in place as
`<name>@skills-dir` for whoever clones the repository and accepts
the trust dialog; it is never copied to the cache. The limits are
the vendor's: its MCP servers go through per-server approval, its
background monitors do not load, it is read only from the session's
primary working directory (not from a subdirectory start), and a
copy of the same name under `~/.claude/skills/` shadows it [4].
The card treats "plugin" and "one repository" as separate
candidates; this mechanism is both at once on the first day, and
the same plugin directory could also be listed in a marketplace for
projects that are not the framework. That last sentence is a lead,
not a finding: no source was read on one directory serving both
ways.

The vendor documents a development loop for a plugin that needs no
packaging: a marketplace added from a local path loads a
relative-path plugin in place, edits taking effect "at the next
session start or when you run `/reload-plugins`", with no change of
version; `--plugin-dir` loads a plugin for one session [2][4]. This
answers part of the frame's development loop, which is another
card's question.

Trust is keyed on the git repository's root and does not extend
into a git repository nested inside it [5]. A framework whose
projects are repositories of their own inside the working clone
meets a second trust dialog the first time a session is started in
one of them. A lead only: what happens when a session started in
the outer repository merely reads the inner one was not read.

A user's report in the tracker of the plugin framework read here is
titled "Superpowers Appeared Without My Consent and AI Agents
Overrode My Instructions in Two Projects" (closed 2026-11-10) [13].
Read from an issue list through a summarising fetch, the issue
itself not opened: the opposite failure to the one the card looks
for, a plugin present in every project of the user where he
expected it in one.

## Not found

- The wording of the workspace trust dialog itself: the pages
  opened say when it appears and what it lists, not its text.
- A sentence of the vendor saying whether a plugin can or cannot
  supply an always-on instruction file (a CLAUDE.md). The component
  lists read name skills, commands, agents, hooks, monitors, mods,
  MCP and LSP servers and `bin/`, and no instruction file [3][4];
  that is an absence in a list, not a statement.
- The full entries of `extraKnownMarketplaces` and `enabledPlugins`
  in the settings reference: the page was opened and its first
  hundred thousand characters did not reach them.
- A published framework of candidate 3's kind, two repositories
  joined by an import of one instruction file: none was looked up
  by name and none turned up in the three queries run.
- A published framework of candidate 6's kind in the strict sense,
  a base separated by a script at every release into its own
  repository: Claudesidian stands in for the consumer's side only
  (clone, cut loose, upgrade later); where its `/upgrade` fetches
  from the README does not say, as the fetch read it.
- Any measurement of how many strangers fail at installation, of
  any kind of framework: no figure, only single reports.
- Installation failures specific to Claude Code in the Superpowers
  tracker: the first page of a search with 113 results showed none
  that clearly was one [13].

## Options

1. **Clone to work in, the base as a plugin directory inside the
   repository** (`.claude/skills/<base>/`). First day: clone,
   start, one trust dialog. No marketplace, no install, no Errors
   tab. Price: the base's files are in the stranger's tree, and the
   limits of a repository plugin hold (no monitors, per-server MCP
   approval, start from the root).
2. **A plugin from the author's own marketplace, plus a command
   that scaffolds the project.** First day: one or two commands, a
   warning, a scope, a summary, then the scaffold. Nothing of the
   base in the repository. Price: the documented silent failure
   [11], updates off until the stranger turns them on, Python
   dependencies and files outside the plugin directory not carried,
   a root path that changes with every version.
3. **Both: the plugin directory in the framework's repository for
   its own stranger, the same directory listed in a marketplace for
   projects that are not the framework.** First day as option 1
   here and as option 2 there. Price: unverified that one directory
   serves both ways (Unexpected).
4. **User-level install into `~/.claude`.** No dialog, shortest of
   all. Price: writes into the stranger's home and reaches every
   project of his; an installer of the author's own to maintain.
5. **Two repositories and an import.** The longest first day, two
   dialogs, a refusal that never asks again, a path relation the
   stranger must get right, and only instruction text carried.

## Relevance to this project

For the stranger alone, the shortest and least breakable first day
is the one the framework already has: a clone, a start, one trust
dialog (candidates 1 and 6). The plugin (candidate 4) is nearly as
short and is the only one that keeps the base out of his
repository, but it is the one kind where the vendor's own tracker
holds an open report of an install that says it succeeded and
loaded nothing, and where a third-party marketplace leaves him on
his first day's version by default. Candidate 3 is the worst first
day of the six by the vendor's own description of the import
dialog. This rests on the vendor's documentation read in full and
on four READMEs read through a summarising fetch; it is chosen
against the reading of the 2026-08-29 note, which ranks the plugin
cleanest because nothing lands in the repository and does not weigh
what the stranger meets on the way.

The agent's own inference, marked as such: the repository-local
plugin directory of Unexpected deserves a look before the choice is
made, because it gives the framework's own stranger the first day
of a clone and may give the base the form of a plugin at the same
time; whether a release then still needs a separating script
(candidate 6) or only a marketplace entry pointing at a
subdirectory (`git-subdir` is a documented source type [2]) is a
question for the cards on the deployment loop, not answered here.
Whatever is chosen, two sentences belong in the README's first
step, both from the vendor's pages: that the trust dialog will
appear and what it will list, and, if a plugin is involved, that
the stranger checks the Installed tab or `claude plugin list`
after installing, since the summary alone has been wrong.

Consult when: the README's installation section is written or
re-rendered; a plugin or a marketplace is considered for the base;
an import across repositories is proposed; a stranger reports that
commands are missing after an install; the question arises whether
a project can make its collaborators' machines install something.

## Sources

1. "Install and manage plugins", Anthropic, Claude Code
   documentation; undated, read 2026-11-14, youngest version named
   on the page v2.1.292.
   https://code.claude.com/docs/en/discover-plugins.md
   Kind: primary (vendor on its own product). Read: in full.
   Original.
2. "Create a marketplace", Anthropic, Claude Code documentation;
   undated, read 2026-11-14.
   https://code.claude.com/docs/en/plugin-marketplaces.md
   Kind: primary. Read: in full. Original.
3. "Plugin security and trust", Anthropic, Claude Code
   documentation; undated, read 2026-11-14.
   https://code.claude.com/docs/en/plugins/security.md
   Kind: primary. Read: in full. Original.
4. "Plugin loading reference", Anthropic, Claude Code
   documentation; undated, read 2026-11-14, youngest version named
   v2.1.324.
   https://code.claude.com/docs/en/plugins/loading.md
   Kind: primary. Read: in full. Original.
5. "Configure permissions", Anthropic, Claude Code documentation;
   undated, read 2026-11-14.
   https://code.claude.com/docs/en/permissions.md
   Kind: primary. Read: partially: the sections "Project allow
   rules and workspace trust", "When your local settings file needs
   trust" and "What runs before you trust a folder", from the
   page's full text by a search for "trust". Original.
6. "How Claude remembers your project", Anthropic, Claude Code
   documentation; undated, read 2026-11-14.
   https://code.claude.com/docs/en/memory.md
   Kind: primary. Read: partially: "Import additional files", "Load
   from additional directories", "Share rules across projects with
   symlinks", the user-level rules and the symlink constraints,
   from the page's full text by a search. Original.
7. Superpowers, README, obra (GitHub); undated, read 2026-11-14.
   https://github.com/obra/superpowers
   Kind: primary (the framework on itself). Read: summarised fetch,
   the installation and updating sections. Original.
8. GSD Core, README, open-gsd (GitHub); undated, read 2026-11-14.
   https://raw.githubusercontent.com/open-gsd/gsd-core/main/README.md
   Kind: primary. Read: summarised fetch, the quickstart. Original.
9. Spec Kit, README, GitHub; undated, read 2026-11-14.
   https://raw.githubusercontent.com/github/spec-kit/main/README.md
   Kind: primary. Read: summarised fetch, the Get Started section.
   Original.
10. Claudesidian, README, heyitsnoah (GitHub); undated, read
    2026-11-14.
    https://raw.githubusercontent.com/heyitsnoah/claudesidian/main/README.md
    Kind: primary. Read: summarised fetch, getting started, the
    bootstrap and the upgrade. Original.
11. "[BUG] Plugins show as '(installed)' in marketplace but don't
    appear in Installed tab", issue 14815, anthropics/claude-code;
    opened 2025-12-20 (dated by the issue page), comments to
    2026-03-05.
    https://github.com/anthropics/claude-code/issues/14815
    Kind: primary (a user's report and a maintainer's reply). Read:
    summarised fetch, the whole thread. Original.
12. Agent OS, installation page, Builder Methods; undated.
    https://buildermethods.com/agent-os/installation
    Kind: primary. Read: summarised fetch, the whole page, which
    holds no steps. Original. Cited only for the fact of the gate.
13. Superpowers, issue search "install plugin not found", obra
    (GitHub); list read 2026-11-14, issues dated by the list.
    https://github.com/obra/superpowers/issues?q=is%3Aissue+install+plugin+not+found
    Kind: primary (a tracker's list). Read: summarised fetch, the
    first page of results; no issue of the list opened. Original.

## Opened and not used

- "Settings reference", Anthropic,
  https://code.claude.com/docs/en/settings-reference.md : the first
  hundred thousand characters did not reach the two entries looked
  for; nothing taken from it.

## Search record

Queries, in order:
1. Claude Code discover and install plugins, marketplace add, trust
   (to find the vendor's pages).
2. Claude Code plugin install fails, marketplace, plugin not loading
   after install, GitHub issue (the disconfirming query).
3. Claudesidian, clone, Claude Code, Obsidian vault, getting
   started, upgrade (a framework cloned to work in).

Pages opened, fourteen: [1] to [13] and the settings reference.

The disconfirming query found what the card expected. The result
list named a series of reports of failed or silently failed plugin
installs, most of them on a mirror of the vendor's tracker, which
was not opened; one original was opened, issue 14815 [11], a
silent failure with a custom marketplace, open for eleven months
with a maintainer's acknowledgement. The tracker of the plugin
framework read here showed, on the first page of its search, no
installation failure specific to Claude Code [13]. So: failures at
installation of a plugin are reported and at least one kind is
silent; how often is not known.

The run ended on the opening budget. The stop rule's first part is
met for candidates 1, 2, 4, 5 and 6 from a primary source or a
framework of the kind, and for candidate 3 from the vendor's
documentation alone, no framework of that kind having been found.
