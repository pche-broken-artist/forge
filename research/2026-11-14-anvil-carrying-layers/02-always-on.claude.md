---
date: 2026-11-14
project: forge
topic: how always-on rules reach every session and every subagent under each of the six candidates
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-14-anvil-carrying-layers/02-always-on
derived_from: research/2026-11-14-anvil-carrying-layers/00-plan.md, card 2; research/2026-08-29-claude-code-packaging.md; research/2026-10-03-user-extensions-kept-apart-from-the-core.md; web sources below
---

# Always-on rules reach a session by a memory file in the tree under every candidate but the plugin, which has two partial channels of its own

## In short

A plugin still cannot ship a `CLAUDE.md` or a `rules/` directory: three
pages of the vendor's documentation say so, `claude plugin validate`
warns about it, and a maintainer wrote on 2026-08-17 "There's no
plugin-level `rules/` directory yet" [4][5][11]. The disconfirming
query did find something the two earlier notes do not have: a plugin
output style with `force-for-plugin: true` is applied automatically
whenever the plugin is enabled and is sent with every request [7]. It
is a real always-on channel for the main conversation, but it does not
reach a subagent, it overrides the user's own output style, and only
one plugin can hold it. The second plugin channel, a `SessionStart`
hook, is capped at 10,000 characters per string, above which Claude
receives a file path and a 2,000 character preview it is not asked to
read [3]. For every candidate in which the base's text lies inside the
working tree (1 and 6, and 2 if the base is copied in), an in-tree
`@` import or `.claude/rules/` delivers it with no dialog, and custom
subagents load the same hierarchy. An import that leaves the working
directory (3) needs a one-time approval per project, and a decline is
silent and permanent. Sure: the facts are the vendor's own pages,
read on 2026-11-14; less sure where a page was read through the fetch
tool's extraction, marked per source. Unexpected: the plugin `agent`
setting, the strongest substitute in the note of 2026-08-29, was
deprecated on 2026-11-12 [10], and a `SubagentStart` hook can inject
context into a subagent [3].

## Question

**Card 2: Always-on rules under each candidate.**

- **Question:** How does the content of an always-on instruction file
  reach every session of Claude Code under each of the six candidates:
  an `@` import into CLAUDE.md and its limits (depth, paths outside
  the project, approval), a rules directory, a hook at session start
  that injects text, a plugin's own means, user-level memory? What is
  loaded in an isolated subagent's context and what is not? How do
  hooks and settings of a base combine with those of a project, and
  can a plugin or an imported repository carry hooks and permission
  rules?
- **Frame:** a framework on Claude Code (one always-on instruction
  file, skills, isolated subagents that preload a contract skill,
  hooks, templates, scripts) to be split into a base, operating
  layers and a place for the user's own things. Candidates: (1) one
  repository with the layers as directories; (2) the base as a
  package and each layer a repository of its own; (3) two
  repositories side by side joined by an import of one instruction
  file into the other; (4) a Claude Code plugin, possibly with a
  marketplace; (5) Claude Code's own mechanisms without a plugin,
  user-level configuration and imports; (6) the framework kept whole,
  a script separating the base at every release into a public
  repository from which other projects update.
- **Why it matters:** The framework's conduct rests on rules that
  must hold in every session and every reviewer run; a candidate that
  cannot deliver them always-on is no candidate, whatever else it
  does.
- **What would answer it:** The vendor's documentation of memory and
  instruction files, of hooks, of settings precedence and of what a
  subagent receives.
- **Where to look:** Anthropic's Claude Code documentation: memory,
  CLAUDE.md imports, rules, hooks reference, settings, subagents,
  plugins; the changelog since August 2026; the issue tracker for
  imports across repositories and for instruction files in plugins.
  Must turn up: whether a CLAUDE.md at a plugin root is loaded today,
  the import depth limit, the SessionStart hook's output.
- **Disconfirming query:** A search for a statement that a plugin can
  now ship always-on instructions, against the expectation that it
  still cannot.
- **Stop rule:** Every candidate has a named mechanism for always-on
  rules with the vendor's statement, or "none found"; nothing new
  from a differently worded query; the opening budget.

**The baseline.** The note of 2026-08-29 established that a plugin
root `CLAUDE.md` is not loaded, that imports go four hops deep with a
one-time approval for an external path, that `.claude/rules/` loads at
launch, and named four substitutes for a plugin (the `agent` setting,
a `SessionStart` hook, a skill, one import line per project). The note
of 2026-10-03 added `omitClaudeMd`, the skills-directory plugin and the
levels table. Neither says what a hook's output is capped at, whether
the hook survives compaction, what a subagent receives item by item,
how hooks from several sources combine, or what the plugin channel
`force-for-plugin` is. This note must beat them on those points and
check that what they say still holds.

## Key findings

**F1. A plugin still carries no always-on memory file and no rules
directory.** [consensus across the vendor's own pages and its
maintainer; vendor documentation and an issue comment] The manifest
reference, at the end of Standard layout: "A `CLAUDE.md` at the plugin
root isn't loaded as context, and `claude plugin validate` warns when
it finds one" [4]. The components page, under Skills: "To include
instructions in a plugin, write them as a skill", and for a rule that
"must hold every time" it sends the author to a hook [5]. The
manifest's field table and the standard layout list no `rules`
component [4]. On the feature request for plugin rules a collaborator
wrote on 2026-08-17: "There's no plugin-level `rules/` directory yet,
but plugins can get close today", naming a plugin skill with `paths:`
frontmatter; the request was closed on 2026-08-20 as a duplicate of an
older one [11]. That older request, opened 2025-12-16, is open, with
114 thumbs-up on its body and no maintainer comment visible on the
page as fetched (15 comments were collapsed) [12]. Youngest source:
2026-11-14 (docs as fetched).

**F2. A plugin does have one automatic instruction channel: an output
style forced by the plugin.** [single source, vendor documentation;
not in either earlier note] The output styles page, frontmatter
reference, field `force-for-plugin`: "Plugin output styles only. Set
to `true` to apply this style automatically whenever the plugin is
enabled, without requiring users to select it. Overrides the user's
`outputStyle` setting. If multiple enabled plugins set this, Claude
Code uses the first one loaded" [7]. Under How output styles work:
"Claude Code sends the active style's instructions with every
request"; a custom style drops the built-in software engineering
instructions unless `keep-coding-instructions: true` [7]. Its limits,
same page: "Output styles apply to the main conversation and to a
fork ... Other subagents run their own system prompt, so styles don't
change how they respond"; and the page's own note that a style "gives
Claude instructions to follow. It doesn't guarantee that something
always happens" [7]. A plugin ships styles in `output-styles/` or
through the manifest key `outputStyles` [4][5]. The page gives no
version for the field and no size limit; whether it applies to a
plugin loaded from a project's `.claude/skills/` is not stated.

**F3. A `SessionStart` hook injects text at every session start,
resume, clear and compaction, but each string is capped at 10,000
characters.** [vendor documentation; hooks reference] Matchers:
`startup`, `resume`, `clear`, `compact`, `fork` [3]. Output: "A
SessionStart hook can add context for Claude", through
`hookSpecificOutput.additionalContext` or plain stdout; the text is
wrapped in a system reminder "at the start of the conversation, before
the first prompt" [3]. The cap, JSON output section: "A hook's
`additionalContext`, `systemMessage`, and `initialUserMessage`
strings, and its plain stdout, are capped at 10,000 characters"; over
the limit Claude Code "saves the output to a file in the session
directory. It replaces the output with the file path and a preview of
up to the first 2,000 characters"; "this cap has no setting or
environment variable to raise it"; "Claude Code doesn't ask Claude to
read the file, so keep anything Claude must always see within the
cap" [3]. Each string is measured on its own, and "When several hooks
return `additionalContext` for the same event, Claude receives all of
the values" [3]; that several hooks could therefore carry a longer
text in pieces is this note's inference, not the vendor's statement.
The vendor steers away from this use: "For instructions that never
change, prefer CLAUDE.md", and warns that "Text framed as out-of-band
system commands can trigger Claude's prompt-injection defenses" [3].
Only `command` and `mcp_tool` hook types are supported on this event
[3]. This corrects the earlier note's inference that hook context
does not survive compaction: the hook runs again with source
`compact` [3].

**F4. An `@` import goes four hops deep, resolves relative to the
importing file, and needs approval only when it leaves the working
directory.** [vendor documentation; memory page, read in full]
"Imported files can recursively import other files, with a maximum
depth of four hops"; "Relative paths resolve relative to the file
containing the import, not the working directory" [1]. "An import in
a project-level memory file is external when its path resolves outside
your working directory ... The first time Claude Code encounters
external imports in a project, it shows an approval dialog listing the
files. If you decline, the imports stay disabled and the dialog
doesn't appear again" [1]. User-scope files (`~/.claude/CLAUDE.md`,
`~/.claude/rules/`) load their imports "without the dialog", except in
Cowork sessions on the desktop, which skip a user-scope import that
leaves the working directory [1]. Imports are skipped inside code
spans and fenced blocks, and "don't reduce its context cost, because
imported files load together with the CLAUDE.md that imports them"
[1]. That an import staying inside the working directory raises no
dialog follows from the definition of "external" and is this note's
reading. Several third-party pages in the search results give five
hops; the vendor's page says four, and none of those pages was opened.

**F5. A rules directory is a second always-on door, in the project
and at user level, and a symlink out of the project is treated like
an external import.** [vendor documentation] "Rules without `paths`
frontmatter are loaded at launch with the same priority as
`.claude/CLAUDE.md`"; all `.md` files are "discovered recursively", so
subdirectories are allowed [1]. `~/.claude/rules/` applies "to every
project on your machine" and loads before project rules; "Neither set
overrides the other" [1]. "Claude Code treats a symlink whose target
is outside your working directory like an external import. The linked
rules don't load until you approve external imports for the project";
a symlink to a network path does not load at all [1]. On Windows the
page recommends the import over a symlink, since a symlink needs
Administrator rights or Developer Mode and git checks a committed one
out as a text file unless `core.symlinks` is on [1]. The only
frontmatter field a rule has is `paths` [1].

**F6. Memory files are also found above the working directory and,
on request, in an added directory.** [vendor documentation] "Claude
Code loads `CLAUDE.md` and `CLAUDE.local.md` from your current working
directory and every directory above it", concatenated from the
filesystem root down [1]. `--add-dir` does not load memory by default;
with `CLAUDE_CODE_ADDITIONAL_DIRECTORIES_CLAUDE_MD=1` it "loads the
additional directory's `CLAUDE.md`, `.claude/CLAUDE.md`,
`CLAUDE.local.md`, and `.claude/rules/*.md` files except rules that
set a `paths` field", and the variable can be kept on through the
`env` block of `~/.claude/settings.json` [1]. A user's report on the
open issue agrees: with that setup "unconditional rules load, but
`paths:` rules from the added directory never fired" [12]. From an
added directory's settings files only an `enabledPlugins` entry of
`true` is read [9]. `claudeMdExcludes` skips named files, the managed
one excepted [1].

**F7. A custom subagent loads the whole memory hierarchy of the main
conversation, and nothing of the conversation; a hook can add to
it.** [vendor documentation; subagents page read through the fetch
tool's extraction, quotes as it returned them, and the hooks
reference] In a subagent's context: its own system prompt "plus basic
environment details like the working directory, not the Claude Code
system prompt"; "every level of the CLAUDE.md hierarchy the main
conversation loads, including `~/.claude/CLAUDE.md`, project rules,
`CLAUDE.local.md`, managed policy files"; the full content of every
skill named in its `skills` field; a git status snapshot [2]. Not in
it: the conversation, skills already invoked, files already read, the
main conversation's auto memory, the output style (a fork excepted)
[2][7]. Exceptions: "Explore and Plan start without your CLAUDE.md
files", and an agent with `omitClaudeMd: true` loads only managed
policy files; for both, a subdirectory's `CLAUDE.md` and matching
path-scoped rules still load when the subagent works with files there
[2]. Hooks: "Hooks from settings files, managed policy settings, and
plugins all apply inside subagents" [2]. New against the baseline:
"SubagentStart hooks can't block subagent creation, but they can
inject context into the subagent", by `additionalContext` "added to
the subagent's context at the start of its conversation, before its
first prompt", re-injected after the subagent's auto-compaction [3];
the 10,000 character cap of F3 applies to it [3]. A plugin's agent
supports `skills` and `omitClaudeMd` and ignores `permissionMode`,
`hooks`, `mcpServers` and `initialPrompt` [5]. Whether text reached by
an `@` import is part of "the hierarchy the main conversation loads"
for a subagent is implied by that wording and not stated in so many
words.

**F8. Settings stack by precedence, lists and hooks merge across the
stack, and nothing lets one settings file include another.** [vendor
documentation; settings page and hooks reference] Precedence, highest
first: managed, command line (`--settings`), project local, shared
project, user [6]. "When you set the same list key, such as
`permissions.allow`, in more than one file, Claude Code combines the
lists instead of picking one" [6]. "Hook entries merge across settings
levels rather than replacing each other"; "If you define the same
handler in more than one settings file, it runs once. A plugin's or
skill's copy of the same handler stays separate" [3], so a hook
present in both a settings file and a plugin "runs twice each time its
event fires" [8]. The shared `.claude/settings.json` is read "from the
session's primary working directory", with no parent lookup [6].
Trust: in an interactive session hooks from every settings file are
held back "until you accept the workspace trust dialog", a `-p` or SDK
session "treats the folder as trusted" [3]; committed
`permissions.allow` rules wait for trust, "`deny` and `ask` rules
apply right away" [6]. `disableAllHooks` follows precedence, and a
managed `allowManagedHooksOnly` blocks user, project, local and plugin
hooks [3]. The settings page describes no include or extends
mechanism; none was found on any page read.

**F9. A plugin can carry hooks; no page read lets a plugin carry
permission rules; an imported file carries text only.** [vendor
documentation for the hooks; absence for the rest] Plugin hooks live
in `hooks/hooks.json` or the manifest's `hooks` key, and "Claude Code
registers them when a session loads the plugin, and they fire on
their events from then on" [5]; "When a plugin is enabled, its hooks
merge with your user and project hooks" [3]. The manifest's field
table has no field for permission rules [4]; what comes nearest is
`allowedTools` on a command of the manifest's `commands` map [4], and
a `PreToolUse` hook, which the memory page names as the way "to block
an action regardless of what Claude decides" [1]. An `@` import is
expanded "into context alongside the CLAUDE.md that references" it
[1]: memory text, no hooks, no settings. The plugin setting `agent`,
which made a plugin agent the main thread, is on its way out:
changelog 2.1.323 of 2026-11-12, "Deprecated a plugin's `agent`
setting: it still applies, and now warns at startup, in `claude
plugin list` and in `claude plugin validate`" [10]. The three plugin
pages read today (manifest reference, components, create) no longer
mention a `settings.json` at the plugin root at all [4][5][8].

**F10. A plugin can live inside the repository and load without a
marketplace, after the trust check and only from the launch
directory.** [vendor documentation; plugin loading reference] "To
share a plugin through a repository, list it under `enabledPlugins`
in `.claude/settings.json` or place it under `.claude/skills/`" [9].
A plugin under the project's `.claude/skills/<name>/` "loads only
after the same trust check that applies to project allow rules";
"Trusting a parent folder or running with `-p` isn't enough"; its
background monitors do not load and its MCP servers need per-server
approval; hooks are not among the restricted components [9]. Claude
Code "doesn't search parent directories for plugins" [9]. It loads in
place and is never copied, so an edit is live at the next session
start or `/reload-plugins` [9]. A marketplace plugin enabled only by
the project's settings "doesn't load at session start until you
install it on your machine", and auto-update is "off for every other
marketplace" than the vendor's own [9].

**F11. The mechanism per candidate.** [this note's synthesis over F1
to F10; the statements are the vendor's, the mapping is the note's]

| Candidate | Always-on text arrives by | Dialog or limit | Hooks and permission rules arrive by |
|---|---|---|---|
| 1 one repository, layers as directories | root `CLAUDE.md` with in-tree `@` imports of the base's and the layer's files, or files under `.claude/rules/` [1] | none for in-tree paths; four hops; no context saved by splitting | the one `.claude/settings.json` of the launch directory [6] |
| 2 base as a package, layer a repository | only once the base's text is in the layer's tree (then as 1), or outside it (then as 3), or installed at user level (then as 5); the vendor names no package mechanism for memory files, none found | as the chosen door | settings have no include; hooks copied into the layer's settings or carried by a plugin [3][6] |
| 3 two repositories joined by an import | `@../base/<file>` in the layer's `CLAUDE.md` [1]; or `--add-dir` with the environment variable [1] | external import: one approval per project, decline is permanent and silent [1]; the added directory's hooks and settings do not load [9] | not by the import; each repository's own settings, and only the launch directory's are read [6] |
| 4 plugin | no memory file [4]; a forced output style [7]; a `SessionStart` and a `SubagentStart` hook [3]; skills with `paths:` [11]; or one import line the plugin's skill writes into the project | style: main conversation only, one plugin wins, replaces the user's style; hook: 10,000 characters per string | plugin hooks, merged with the user's and the project's [3][5]; no permission rules found |
| 5 user-level configuration and imports | `~/.claude/CLAUDE.md`, `~/.claude/rules/`, their imports without a dialog [1] | applies to every project on the machine; no dialog; skipped in part in Cowork desktop sessions | `~/.claude/settings.json`, lowest precedence, hooks merged everywhere [6][3] |
| 6 whole framework, base separated by a script | in the framework as 1; in a consuming project as whatever the update writes: files in its tree (as 1) or a plugin (as 4) | as the chosen door | as the chosen door |

## Unexpected

**The vendor's own instruction loader is a built-in plugin.** Reading
`AGENTS.md` as project instructions (since 2.1.277) is done by "the
built-in plugin that reads `AGENTS.md`", id
`cc-plugin-agents-md@builtin`, configured under `pluginConfigs` [1].
So a plugin that loads instruction files at launch exists inside the
product, while the documented plugin surface offers third parties no
such component. Whether that surface will open is not said anywhere
read; this is a lead only.

**A plugin can now state the Claude Code version it needs.**
Changelog 2.1.323, 2026-11-12: "Added `engines["claude-code"]` to
`plugin.json`: plugins outside their stated Claude Code version range
are not installed, updated or loaded" [10]. It bears on the
deployment loop of the frame, not on this card.

**"Mods": plugin hooks written as code that runs inside Claude
Code.** The components page: a `modules` key in `hooks/hooks.json`
makes the plugin a mod, with "hooks as JavaScript functions that run
inside Claude Code" [5]; the changelog of November names mod hooks on
`tool.list` and `tool.check` [10]. On the open issue a user's commit
is titled "load rules from each plugin via a hooks module" [12]. The
mods pages were not opened, so whether a mod can add text to every
request is unknown here.

**The loading of `.claude/skills` below or beside the launch
directory changed three times in one week.** Changelog 2.1.319,
2.1.321 and 2.1.325 (2026-11-06 to 2026-11-13) each narrow where
nested skill folders load, the last: "`.claude/skills` folders in
`--plugin-dir` plugins no longer load from a session started above
them" [10]. A design that leans on nested discovery leans on ground
that is moving.

**The card treats the instruction file as one deliverable; the vendor
treats its length as a defect.** The memory page: "target under 200
lines per CLAUDE.md file. Longer files consume more context and
reduce adherence" [1]. No hard limit on a memory file was found, so
this does not close any candidate, but every door that is not a
memory file (F2, F3) has a tighter limit or a narrower reach.

## Not found

- A statement that a plugin can ship a `CLAUDE.md`, a rules directory
  or any memory file: none, in the documentation, the changelog entries
  read or the two issues. Looked: manifest reference, components,
  create, loading, output styles, the newest changelog entries, issues
  72687 and 14200.
- What happens to an external import in a non-interactive (`-p`)
  session, where no dialog can be shown: the memory page speaks only
  of "a dialog at the start of an interactive session".
- Whether an import written in a `CLAUDE.md` that itself lies above
  the working directory, pointing at a sibling directory, counts as
  external.
- Whether `force-for-plugin` works for a plugin loaded in place from a
  project's `.claude/skills/`, since which version it exists, and how
  long a style may be.
- A field or a file by which a plugin contributes `permissions`
  rules; the permissions page was not opened, so this is "not found on
  the plugin pages", not "does not exist".
- The plugin root `settings.json`: absent from the three plugin pages
  read; only the deprecation line of its `agent` key in the changelog.
  Whether `subagentStatusLine` remains its only live key was not
  established, beyond a 2.1.319 fix that mentions it.
- The changelog between about 2.1.230 and 2.1.318: the page is over a
  million characters and only its first 100,000 were read (2.1.319 to
  2.1.325).
- Whether `SubagentStart` fires for a skill run with `context: fork`,
  and whether a subagent sees imported files exactly as the main
  conversation does.
- No issue about imports across repositories was found by the one
  tracker query run; the tracker was sampled, not swept.

## Options

Ways the always-on rules can be delivered, each a reading of the
findings, not a design:

- **A. The rules stay memory files inside the working tree.** The
  root `CLAUDE.md` imports, or `.claude/rules/` holds, one file the
  base owns, one the layer owns and one gitignored file the user owns.
  No dialog, loads in custom subagents, survives compaction, visible
  in `/context`. Cost: the base's text must be physically in every
  project's tree, so an update is a write into that tree; the total
  context cost is unchanged by the split.
- **B. The rules lie outside the tree and are imported.** One line per
  project. Cost: an approval per project that, once declined, never
  asks again and fails silently; a stranger's first act decides it;
  behaviour without a dialog not documented.
- **C. The rules are installed at user level.** No dialog, no line in
  the project. Cost: they govern every project on the machine, one
  version for all, and a stranger must let the framework write into
  his home configuration.
- **D. The rules travel in a plugin.** Either a forced output style
  (main conversation only, displaces the user's style, one plugin
  wins) plus a `SubagentStart` hook for the reviewers (10,000
  characters), or `SessionStart` hooks alone (10,000 characters per
  string, against the vendor's advice for static text). Cost: no
  single channel reaches both the session and the subagents, and both
  are documented as something other than a home for standing rules.
- **E. A plugin for the executable parts, A for the text.** The
  plugin carries skills, agents, hooks and scripts; its setup skill
  writes the base's rule files into the project's tree and the import
  line into its `CLAUDE.md`. Cost: two things to keep in step, the
  plugin's version and the copied text.

## Relevance to this project

Read against the card's own test ("a candidate that cannot deliver
them always-on is no candidate"), the findings say this, as the
agent's inference from the vendor's statements:

1. **No candidate is ruled out, but the plugin alone (4) delivers
   least.** It has no channel that reaches the main session and the
   reviewers alike with a text of a full instruction file's length.
   A framework whose reviewers must run under the same rules would
   need the forced style and a `SubagentStart` hook together, or
   would keep the rules where F7 says a custom subagent already finds
   them: in the memory hierarchy.
2. **The memory hierarchy inside the tree is the only door with no
   dialog, no cap and subagent reach** (F4, F5, F7). Candidates 1 and
   6 have it by construction. Candidate 2 has it only if the base's
   rule files are copied into the layer's tree by the update; the
   same holds for a consuming project under 6.
3. **Candidate 3 as worded, an import across two repositories, puts a
   stranger's first run behind an approval that fails silently for
   good if declined** (F4). It is chosen against here; if side-by-side
   repositories are wanted, `--add-dir` with the environment variable
   is the documented alternative, and it brings no hooks.
4. **Hooks and deny rules do not travel with the text.** Under every
   candidate they arrive through the launch directory's settings file
   or through a plugin (F8, F9). A base that owns a hook must
   therefore either write into the project's `.claude/settings.json`,
   which an upgrade then touches, or be a plugin for that part. The
   split "text in the tree, hooks in a plugin" (option E) is what the
   findings leave standing as the one combination in which an upgrade
   writes into no file the user or the layer owns except the base's
   own rule files; this is the agent's inference.
5. **Three things the earlier notes rest on have moved**: the `agent`
   setting is deprecated (F9), a hook's context does return after
   compaction (F3), and a hook can now inject into a subagent (F7).

Recommended, in plain words: keep the always-on rules as memory files
in the working tree under whichever candidate is chosen, split by
owner into base, layer and user files joined by in-tree imports or a
rules directory, and judge the candidates by how the base's file gets
into that tree and is updated there, not by whether a plugin can hold
it. Chosen against: the plugin as the home of the rules, and the
cross-repository import. What it rests on: F1, F3, F4, F7.

Consult when: deciding where the base's rule text lives in a
consuming project; weighing a plugin for the base; a reviewer run
seems not to know a rule; a `SessionStart` hook is proposed as the
carrier of rules; a hook or a deny rule of the base must reach a
project; the vendor announces plugin rules (issue 14200) or changes
`force-for-plugin`.

## Sources

1. "How Claude remembers your project" (memory), Anthropic, Claude
   Code documentation. Undated; names versions up to 2.1.285; fetched
   2026-11-14. https://code.claude.com/docs/en/memory.md . Primary.
   Read: page text returned whole; the sections from "Choose where to
   put CLAUDE.md files" through "Migrate instructions from other
   tools" in full, the rest (auto memory, troubleshooting) by search.
   Original.
2. "Create custom subagents" (sub-agents), Anthropic, Claude Code
   documentation. Undated; names 2.1.271; fetched 2026-11-14.
   https://code.claude.com/docs/en/sub-agents.md . Primary. Read:
   summarised fetch, the fetch tool's extraction of quoted passages
   from the first 100,000 of 116,580 characters; quotes as it gave
   them. Original.
3. "Hooks reference", Anthropic, Claude Code documentation. Undated;
   names versions up to 2.1.300; fetched 2026-11-14.
   https://code.claude.com/docs/en/hooks.md . Primary. Read:
   partially, in four fetches: characters 0 to 100,000 twice and
   100,000 to 200,000 as the fetch tool's extraction of quoted
   passages (locations, merging, the cap, Add context for Claude,
   SessionStart, InstructionsLoaded); from 200,000 to the end as page
   text, the SubagentStart and Workspace trust sections read there by
   search. Original.
4. "Plugin manifest reference", Anthropic, Claude Code documentation.
   Undated; names versions up to 2.1.288; fetched 2026-11-14.
   https://code.claude.com/docs/en/plugins/manifest-reference.md .
   Primary. Read in full (page text returned whole). Original.
5. "Add components to a plugin", Anthropic, Claude Code
   documentation. Undated; names versions up to 2.1.310; fetched
   2026-11-14. https://code.claude.com/docs/en/plugins/components.md .
   Primary. Read in full. Original.
6. "Settings files and precedence", Anthropic, Claude Code
   documentation. Undated; names versions up to 2.1.319; fetched
   2026-11-14. https://code.claude.com/docs/en/settings.md . Primary.
   Read in full. Original.
7. "Output styles", Anthropic, Claude Code documentation. Undated;
   names versions up to 2.1.269; fetched 2026-11-14.
   https://code.claude.com/docs/en/output-styles.md . Primary. Read in
   full. Original.
8. "Create a Claude Code plugin", Anthropic, Claude Code
   documentation. Undated; names versions up to 2.1.281; fetched
   2026-11-14. https://code.claude.com/docs/en/plugins/create.md .
   Primary. Read in full. Original.
9. "Plugin loading reference", Anthropic, Claude Code documentation.
   Undated; names versions up to 2.1.324; fetched 2026-11-14.
   https://code.claude.com/docs/en/plugins/loading.md . Primary. Read
   in full. Original.
10. "Changelog", Anthropic, Claude Code documentation. Dated per
    entry; newest entry 2.1.325 of 2026-11-13.
    https://code.claude.com/docs/en/changelog.md . Primary. Read:
    partially, the first 100,000 of about 1,275,000 characters
    (versions 2.1.319 to 2.1.325), as the fetch tool's extraction;
    entries quoted as it gave them. Original.
11. "[Feature Request] Add plugin-level rules support for shared code
    standards", issue 72687, anthropics/claude-code, GitHub. Opened
    2026-07-01, collaborator comments 2026-08-17 and 2026-08-20, closed
    as duplicate (dates as the page shows them).
    https://github.com/anthropics/claude-code/issues/72687 . Primary
    for the maintainer's statement. Read: summarised fetch, the
    comments quoted as the fetch gave them. Original.
12. "[FEATURE] Add rules support to Plugins", issue 14200,
    anthropics/claude-code, GitHub. Opened 2025-12-16, open, last
    comment 2026-10-26 (dates as the page shows them).
    https://github.com/anthropics/claude-code/issues/14200 . Primary
    for the request and its state; practitioner claims for the
    workarounds. Read: summarised fetch; 15 comments were collapsed on
    the page and not seen. Original.

## Opened and not used

None. Every page opened is cited.

## Search record

Queries, in order:

1. Claude Code plugin CLAUDE.md always-on instructions loaded
2. Claude Code memory CLAUDE.md import depth, external imports
   approval, rules directory
3. Claude Code plugin ship rules always-on context, plugin now
   supports CLAUDE.md 2026 (the disconfirming query)
4. anthropics/claude-code issues: plugin CLAUDE.md, rules directory,
   always-on instructions, feature request (GitHub only)

Pages opened, 15 fetches of 12 pages: memory; sub-agents; hooks
reference (four fetches: two of the first part, one of the middle, one
of the end); plugin manifest reference; plugin components; settings;
output styles; create a plugin; issue 72687; changelog; issue 14200;
plugin loading reference.

The disconfirming query: the search itself returned no statement that
a plugin can ship always-on instructions, and the expectation held for
memory files and rules (F1). Following it into the documentation
turned up `force-for-plugin` (F2), a documented way for a plugin to
apply instructions to every request of the main conversation without
the user selecting anything. The expectation "it still cannot" is
therefore confirmed for a `CLAUDE.md` and for rules, and contradicted
in part for instructions as such.

The run ended on the opening budget. By then every candidate had a
named mechanism with the vendor's statement or "none found" (F11);
the second part of the stop rule, nothing new from a differently
worded query, was not tested beyond the four queries above.
