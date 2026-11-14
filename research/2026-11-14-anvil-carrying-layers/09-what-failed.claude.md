---
date: 2026-11-14
project: forge
topic: what failed - plugin distribution, user content at an update, splits taken back, Claude Code changing under frameworks
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-14-anvil-carrying-layers/09-what-failed
derived_from: research/2026-11-14-anvil-carrying-layers/00-plan.md, card 9; 2026-08-29-framework-distribution-in-the-field.md; 2026-10-03-one-tool-a-core-with-modules-or-several-tools.md; web sources below
---

# What has been seen to fail: plugin distribution, user content at an update, splits taken back, and Claude Code moving under frameworks

## In short

Three of the four kinds of trouble have two or more first-hand
reports. (1) Plugin distribution: an update that does not reach the
user is the best documented trouble of all, open in Claude Code's
tracker since January 2026 with reports up to October 2026 and no
maintainer answer on the page; the mechanism is a local marketplace
clone that is not refreshed and a cache keyed on the version string,
so a change without a version bump is never delivered. A maintainer
(Superpowers) also records a release that "broke plugin installs for
some users". (2) User content at an update: Spec Kit has two filed
and fixed cases, one of a user's own file overwritten, one of
extension and preset content removed by an upgrade; BMAD removed its
custom-content installation in a release with no migration advice.
(3) A split taken back: little new beyond the two retreats the
project already knows; one new small case (a part moved out of a
plugin because it broke installs) and one reversal without a stated
reason (an npm installer deprecated for the plugin, then
un-deprecated). (4) Claude Code changing a mechanism: one maintainer
followed the same change twice (hook execution on Windows), one
regression silently dropped every command file for two versions,
and the current changelog shows plugin loading rules changing
release by release. The disconfirming query found projects that
moved from an installer to a plugin, but none whose maintainer says
in words that it removed upgrade trouble: weaker than expected.
Unexpected: Claude Code recently stopped loading `.claude/skills`
folders nested inside plugin folders in two situations, which bears
on any design that keeps a plugin in the tree of the repository it
is developed in. Every page was read through a summarising fetch;
quotations are to be checked at the URL before they are quoted
onward.

## Question

> #### Card 9: What failed
> - **Question:** What trouble is reported with distributing a
>   framework for Claude Code through plugins or marketplaces, with
>   user content overwritten or broken at an update of a framework,
>   and with a division of a tool into a core and separately released
>   parts that was later taken back? What broke when Claude Code
>   itself changed a mechanism such frameworks stood on?
> - **Why it matters:** Each candidate will be scored by what it has
>   been seen to cost, not by what its documentation promises.
> - **What would answer it:** Reports by those it happened to: issues,
>   post-mortems, maintainers' release notes that explain a retreat.
> - **Where to look:** The issue trackers of Claude Code and of the
>   frameworks named in card 8; maintainers' write-ups and release
>   notes; discussion threads where a maintainer answers, cited to the
>   maintainer's own words. Must turn up: a plugin update that did not
>   reach users or reached them broken, a breaking change of Claude
>   Code that frameworks had to follow.
> - **Disconfirming query:** A search for reports that plugin
>   distribution removed a class of upgrade trouble a framework had
>   before; expected: some.
> - **Stop rule:** Each of the three kinds of trouble has two or more
>   first-hand reports or is recorded as not found; the opening
>   budget.

The frame: a framework on Claude Code (one always-on instruction
file, skills, isolated subagents, hooks, templates, scripts, one
public repository) is to be split into a base, operating layers and
a place for the user's own, compared over six candidates and two
loops (development, deployment), for Claude Code only.

What the note must beat. The note of 2026-08-29 says which
frameworks copy the engine into the user's repository and what
apparatus that forced on them, with two cautionary tales in the
maintainers' words (BMAD's override file that locks old values,
OpenSpec's passive file). The note of 2026-10-03 records the
retreats: Superpowers' separate skills repository taken back after
four days, BMAD's remote registry retired, Agent OS cut back, and
the older analogies. Neither has a report from a user or maintainer
of a plugin update that failed to arrive, of a specific overwrite
at an update, or of a Claude Code change that a framework had to
follow. Those are what this note adds.

## Key findings

**F1. A plugin update can fail to reach the user, and the report has
stood open for ten months.** [emerging; practitioner reports in the
vendor's issue tracker, several independent reporters, no vendor
answer on the page] Issue 17361 of Claude Code, opened 2026-01-10,
still open and labelled duplicate when read: "Plugin cache is never
refreshed after initial install, even with `autoUpdate: true`
enabled. Claude Code reads from stale cache instead of the updated
marketplace folder." Later comments report the same on versions
2.1.187 (June), 2.1.220 (July) and 2.1.286 (2026-10-02). No reply
of an Anthropic staff member appears on the page; a bot added
labels [1]. A second report, issue 37252 of 2026-03-21: "`claude
plugin update` reports a plugin is already at the latest version
when a newer version exists, because it checks the local marketplace
clone without first pulling from the remote"; the bot named three
more issues of the same content and the author closed it as a
duplicate the same day [2]. Both read through a summarising fetch.

**F2. The cause, as commenters worked it out, is two separate
mechanisms, one of them documented behaviour.** [single source;
practitioner diagnosis in comments of [1], not confirmed by the
vendor on that page] (a) the local clone of the marketplace is not
brought forward before the version is compared; (b) the cache is
keyed on the version string, so a change of content without a
version bump is never extracted again. A commenter quotes the
documentation for (b): "a plugin gets a new copy only when its
computed version changes — bump version on each release, or omit it
so users track commits". The same commenter says the automatic
update runs only in an interactive session after the first message.
The workarounds reported: delete the cache folder; uninstall and
install again (said to drop `autoUpdate` from the settings in
silence); `claude plugin marketplace update` followed by `claude
plugin update` and a restart, which one commenter calls "reliable";
bump the version at every change [1]. The documentation page itself
was not opened in this run; the quotation is the commenter's.

**F3. A plugin release reached users broken, by the maintainer's own
record.** [single source; maintainer's release notes] Superpowers
v6.0.2 (2026-06-16): "It broke plugin installs for some users, so
the eval harness now lives in its own repo, separate from the
published plugin." v6.4.1 (2026-09-18) opens "v6.4.0 was never
shipped." and fixes skills whose commands failed with `Permission
denied` when a packager stripped the executable bits [3]. A second
project's changelog, metaswarm 0.14.0: "The plugin hook works when
the plugin path contains a space" and "Every command has
`description:` frontmatter, so plugin installs list all 16 commands
for the model, not only 4" [4]; that changelog carries no dates.
What these share is my reading: what is published in the plugin's
tree is installed whole, so a development-only part or a file mode
becomes a defect at the user's.

**F4. Leaving the plugin road strands those who have the marketplace
cached.** [single source; a contributor's pull request, closed
without merge] A pull request to a vendor's development kit
(2026-05-26) proposed that the project stop being a Claude Code
plugin, and warned that without a period of overlap "users with the
a-d-k marketplace cached locally get cut off with no in-product
hint", and that users had to "run `/plugin update` at least once" to
see the notice of the move. It was closed unmerged on 2026-07-02;
its author carries the label Contributor, not maintainer [5]. It is
a proposal that names the cost, not a retreat that happened.

**F5. A user's own file was overwritten by a re-run of the
installer, and it took a move of the file to stop it.** [consensus
within the project: filed, assigned and closed by a maintainer;
practitioner report] Spec Kit issue 1541 (2026-01-31): the default
constitution lay at the path of the user's own, which "causes
user-customized constitutions to be overwritten when spec kit is
reinitialized"; closed as completed on 2026-02-09 through pull
request 1553, the maintainer leaving no written comment [6]. The
pull request was not opened.

**F6. An upgrade removed what extensions and presets had supplied,
though they stayed installed.** [single source; practitioner report,
closed by a maintainer the same day] Spec Kit issue 3849
(2026-07-29, version 0.14.2): "`integration upgrade` rewrites skills
from the core command templates only", which "removes active
extension and preset command overrides, even though those assets
remain installed and registered"; closed as completed the same day
through pull request 3853 [7]. This is the failure of the layered
shape itself: the upgrade of the core regenerated a file that a
layer had also written into. Six months lie between F5 and F6 in the
same project, after the manifest the note of 2026-08-29 describes
was in place; that the manifest did not prevent F6 is my inference.

**F7. A framework removed its way of installing custom content in a
release, with no advice for those who had used it.** [single source;
maintainer's release notes] BMAD v6.3.0 (10 April; the page gave no
year in my reading), under breaking changes: "Remove custom content
installation feature; use marketplace-based plugin installation
instead". The page gives no reason and no migration steps; a fix in
the same notes reads "Preserve local custom module sources during
quick update" [8]. No issue by an affected user was found (Not
found).

**F8. Claude Code changed how hooks run on Windows and the same
framework had to follow twice.** [single source; maintainer's
release notes] Superpowers v4.2.0 (2026-02-05): "Claude Code 2.1.x
changed how hooks execute on Windows: it now auto-detects `.sh`
files in commands and prepends `bash`." v4.3.1 (2026-02-21): "Claude
Code's `.sh` auto-detection on Windows was prepending `bash` to the
hook command, breaking execution." v6.2.0 (2026-07-23) settles it by
declaring `shell: "bash"`, which needs Claude Code 2.1.81 or newer.
Two further follow-ups of the same kind: v6.0.3 (2026-06-18) "Claude
Code treats `.git/` as a protected path and denies agent writes
there"; v6.4.2 (2026-09-25) "Claude Code now reads `AGENTS.md`
directly, but only when no `CLAUDE.md` exists" [3].

**F9. One release of Claude Code silently stopped loading every
command file; it was a packaging defect, fixed two versions later,
and the users read it as a breaking change.** [consensus on the
facts: several reporters and the vendor's collaborator; vendor
report] Issue 41864 (2026-04-01): "Custom project-level slash
commands from `.claude/commands/` are not loaded in Claude Code
v2.1.89." A collaborator of the repository answered on 2026-04-18:
"This was fixed in **v2.1.91** — The bundled ripgrep binary now
ships with execute permissions, restoring discovery of project
commands in .claude/commands/." [9]. Issue 42073 of the same day
shows how it looked from outside: "The only error shown is `Unknown
skill: <name>` with no guidance on what changed or how to migrate";
its author moved every file to the skills folder as a workaround
before the cause was known [10]. The discovery of a framework's
commands rested on one bundled binary; a framework cannot test for
that from its side.

**F10. The rules of plugin loading are still changing release by
release.** [vendor claim; the vendor's own changelog, a primary
source on its product] From the newest part of the changelog, read
on 2026-11-14 (the entries carried no dates in my reading): 2.1.325
"Changed marketplace `ref` to accept the full ID of any commit on a
branch or tag; clients before this version can't clone such a pin,
so a marketplace pinned this way stops loading there"; 2.1.323
"Changed marketplace and plugin installs to fail when a git
submodule isn't on the commit its repository records"; 2.1.323
"Deprecated a plugin's `agent` setting"; 2.1.325 "Changed plugin
loading to skip, and `claude plugin validate` to report, some unsafe
paths and links in a plugin's folder" [11]. Only the first 100,000
characters of a page of about 1.3 million were read, so older
breaking entries are not covered.

**F11. A split taken back: one small new case, one reversal without
a reason.** [single source each; maintainers' release notes] New
beyond the note of 2026-10-03: Superpowers moved its eval harness
out of the published plugin into a repository of its own because it
broke installs (F3) [3], which is a split made, not taken back.
metaswarm 0.9.0 replaced the npm installer by the marketplace
plugin, and 0.10.0 "un-deprecated" the npm package with no reason
given [4]: both roads are kept. Superpowers also records retreats of
features with reasons, none of them a core split: v5.0.6 a review
loop that "doubled execution time (~25 min overhead) without
measurably improving plan quality"; v6.2.0 "The v6.1.0 removal (on
the news that Google had EOLed the Gemini CLI) was premature" [3].
The two retreats already known (Superpowers' skills repository,
BMAD's registry) remain the only first-hand cases of a core and
separately released parts taken back in this field.

## Unexpected

Skills folders nested in plugin folders stopped loading in two
situations. Changelog 2.1.325: "Changed nested skill loading:
`.claude/skills` folders in `--plugin-dir` plugins no longer load
from a session started above them; start Claude Code in the plugin
folder instead"; 2.1.321: "Changed nested skill loading:
`.claude/skills` folders inside `~/.claude/plugins` no longer load
when Claude works on files there" [11]. A design that develops the
base as a plugin inside the tree of the framework and tries it
through `--plugin-dir` from the repository root stands on exactly
this ground. Whether the plugin's own `skills/` folder is touched
is not said by the entries as read; this is a lead to verify, not a
conclusion.

A plugin can now state which Claude Code it needs. Changelog
2.1.323: "Added `engines["claude-code"]` to `plugin.json`: plugins
outside their stated Claude Code version range are not installed,
updated or loaded, and install and update pick the newest version
that fits" [11]. This is the vendor's answer to the kind of trouble
in F8, and it exists for plugins only; the other candidates of the
card have no such declaration from the harness.

The card assumes an update is something the framework sends and the
user receives. F1 and F2 say that for a plugin the user's machine
decides, by a version string and a cached clone, whether anything
is received at all, and that the framework's maintainer sees
nothing of it. "How often a user is forced to update" may have the
opposite problem: a user who cannot be made to update even when he
asks.

## Not found

- A maintainer's statement, in words, that moving to plugin
  distribution removed upgrade trouble the framework had before.
  Looked for by search and in two primaries [4][12]; see the Search
  record.
- An issue by a user of BMAD or of GSD whose content an update
  overwrote or deleted. Two searches returned mirrors, documentation
  and unrelated trackers; neither project's issue tracker was opened
  directly.
- A new first-hand account of a framework for Claude Code that
  divided itself into a core and separately released parts and took
  it back, beyond the two in the note of 2026-10-03. A vendor's
  changelog that folds several plugins into one was found by search
  but its page returned 404 and is not cited.
- An answer by Anthropic staff on the stale-cache issue [1], or a
  version of Claude Code in which it is fixed. The mirror of the
  tracker lists related issues as closed; none was opened.
- An intended, announced breaking change of Claude Code with a
  framework's maintainer naming the cost of following it, other than
  the Windows hook change [3]. The case most cited by users [9][10]
  was a defect.
- Any figure: how many users were affected by any of the above. The
  one count read is 12 comments and about 32 thumbs-up on [1].

## Options

Left out: the card asks what has been seen to fail, not for a
choice. What the findings mean for the candidates is under
Relevance.

## Relevance to this project

All of this paragraph is my inference from the findings above.

- **The plugin candidate (4).** Its recorded cost is in the
  deployment loop, not where the documentation puts it: an update
  that does not arrive (F1, F2), a release that installs broken
  because the whole tree is shipped (F3), and no clean way back out
  (F4). What it has been seen to need: a version bump at every
  change as a rule held by a script, nothing in the published tree
  that a user must not get, and an update instruction of two
  commands and a restart written into the framework's own
  `/pull`-like door, since `autoUpdate` cannot be relied on. The
  development loop is touched by the Unexpected entry on nested
  skills and must be tried on the current version before the
  candidate is scored.
- **Any candidate with layers that write into the same files (1, 2,
  6 with an update script).** F6 is the precedent: the core's
  upgrade regenerated a file from its own templates and removed what
  a layer had put there, in a project that already had a manifest.
  F5 is the simpler rule: a default and the user's own must never
  share a path. The wanted property "a place an upgrade never
  writes" is the right one; the evidence says it has to be enforced
  by where files lie, not by the updater's care.
- **Every candidate.** F8 to F10 are the standing cost of building
  on Claude Code at all, and they fall hardest on hooks and on
  loading rules. A base that many projects update from multiplies
  the reach of each such break; a test run of the base against the
  newest Claude Code before a release of the base, and a stated
  minimum version, are what the reports argue for. The plugin
  manifest's `engines` field is the only harness-level form of that
  statement found.
- **Chosen against.** The findings do not support dropping the
  plugin candidate: no report says the mechanism is unusable, one
  commenter calls the explicit two-command update reliable, and
  projects keep moving to it (Search record). They do not support
  trusting it alone either: one project kept its installer beside
  the plugin after having deprecated it (F11).

How sure. Every page came through a summarising fetch, with
quotations capped short; the facts of dates, states and wording are
to be checked at the URL before they travel. The picture of the
stale cache rests on reporters, not on the vendor.

Consult when: the plugin candidate is scored for the deployment
loop; the update door of the base is designed (what it runs, what it
tells the user); the place of the user's own files is drawn; a
release procedure of the base is written; anyone proposes relying on
automatic plugin updates.

## Sources

1. "Plugin cache never refreshes - autoUpdate doesn't update what
   Claude reads", issue 17361, anthropics/claude-code; opened
   2026-01-10 (page date), comments to 2026-10-02;
   https://github.com/anthropics/claude-code/issues/17361 ; primary
   (reporters' own accounts); summarised fetch of the whole thread;
   original.
2. "claude plugin update does not refresh marketplace clone before
   version check", issue 37252, anthropics/claude-code; 2026-03-21
   (page date);
   https://github.com/anthropics/claude-code/issues/37252 ; primary;
   summarised fetch; original.
3. Superpowers, RELEASE-NOTES.md, the project's maintainer; entries
   dated in the file, 2026-02-05 to 2026-11-03;
   https://raw.githubusercontent.com/obra/superpowers/main/RELEASE-NOTES.md
   ; primary; summarised fetch, partially: the first 100,000 of
   about 120,000 characters, the oldest entries unread; original.
4. metaswarm, CHANGELOG.md, the project's maintainer; undated (the
   entries carry versions, no dates);
   https://github.com/dsifry/metaswarm/blob/main/CHANGELOG.md ;
   primary; summarised fetch; original.
5. "retire .claude-plugin/: a-d-k stops being a Claude Code plugin",
   pull request 548, databricks-solutions/ai-dev-kit; opened
   2026-05-26, closed unmerged 2026-07-02 (page dates);
   https://github.com/databricks-solutions/ai-dev-kit/pull/548 ;
   primary (a contributor's proposal, not a maintainer's decision);
   summarised fetch; original.
6. "Constitution template should be in .specify/templates/ to
   prevent overwrites during reinitialization", issue 1541,
   github/spec-kit; 2026-01-31, closed 2026-02-09 (page dates);
   https://github.com/github/spec-kit/issues/1541 ; primary;
   summarised fetch; original.
7. "[Bug]: `integration upgrade` overwrites extension-and preset-
   provided Copilot skills", issue 3849, github/spec-kit; 2026-07-29
   (page date); https://github.com/github/spec-kit/issues/3849 ;
   primary; summarised fetch; original.
8. BMAD-METHOD release v6.3.0, the project's maintainers; 10 April,
   year not shown in the fetch (2026 by the changelog dates in the
   note of 2026-10-03);
   https://github.com/bmad-code-org/BMAD-METHOD/releases/tag/v6.3.0
   ; primary; summarised fetch; original.
9. "Project commands from .claude/commands/ not loaded in v2.1.89",
   issue 41864, anthropics/claude-code; 2026-04-01, collaborator's
   reply 2026-04-18 (page dates);
   https://github.com/anthropics/claude-code/issues/41864 ; primary;
   summarised fetch; original.
10. "~/.claude/commands/ no longer recognized in v2.1.89 — breaking
    change without migration path", issue 42073,
    anthropics/claude-code; 2026-04-01, closed as duplicate
    2026-04-18 (page dates);
    https://github.com/anthropics/claude-code/issues/42073 ;
    primary; summarised fetch; original.
11. Claude Code changelog, Anthropic; undated as read (versions
    2.1.319 to 2.1.325), read 2026-11-14;
    https://code.claude.com/docs/en/changelog ; primary (vendor on
    its own product); summarised fetch, partially: the first 100,000
    of about 1,275,000 characters, the newest releases only;
    original.
12. "refactor!: migrate from install/uninstall to Claude Code plugin
    system", pull request 2, ory/lumen; merged 2026-03-03 (page
    date); https://github.com/ory/lumen/pull/2 ; primary; summarised
    fetch; original.

## Opened and not used

- A vendor's changelog page for its Claude plugins, version 3.0.0
  (several plugins folded into one): the address from the search
  redirected and the target returned 404; nothing read, nothing
  cited, the address left out since it does not open.

## Search record

Queries, in order:
1. Claude Code plugin update not reaching users, stale cache,
   marketplace.
2. Claude Code breaking change that broke plugins, hooks, skills.
3. Framework update overwrote customisations, by framework names.
4. GSD update deleted or overwrote user files.
5. SuperClaude plugin repository merged back, deprecated or
   archived.
6. Disconfirming: migrated to a Claude Code plugin, installer no
   longer needed, upgrade simpler.
7. Plugins merged back or consolidated into one, hard to keep in
   sync.
8. BMAD update overwrote custom agents, lost customisations.
9. metaswarm migration from npx to marketplace plugin, the reason.

Pages opened (14 openings, two of them the same file twice): [1],
[2], [10], [7], [6], [3] twice, [5], [12], [9], the vendor's
changelog page that returned a redirect and then 404, [11], [4],
[8]. A mirror site of Claude Code's issue tracker led most search
results; it was not opened and each issue was read at its origin.

What the disconfirming query found: projects that moved from an
installer of their own to the plugin system, [12] merged with the
words "All configuration is now declarative" and [4] at version
0.9.0, neither naming an upgrade trouble that the move removed; [4]
later un-deprecated its installer. One search result described a
package going the other way, an npx package replacing a deprecated
plugin distribution; not opened, not cited. Expected "some"; found
the moves, not the statement.

Why the run ended: the opening budget (about ten to fifteen). By
the stop rule, plugin distribution trouble and user content at an
update each have two or more first-hand reports; a split taken back
is recorded as not found beyond what the project's notes already
hold.
