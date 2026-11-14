---
date: 2026-11-14
project: forge
topic: keeping a copy of a base in a user's repository in step with its source
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-14-anvil-carrying-layers/05-updating-a-copy
derived_from: research/2026-11-14-anvil-carrying-layers/00-plan.md, card 5; 2026-08-29-framework-distribution-in-the-field.md; web sources below
---

# Tools keep a copy in a user's repository in step with its source in five ways, and each pays for the user's changes differently

## In short

Five families of mechanism were found, each with a primary source
saying what it does with a file the user changed, but for one
(the declarative vendoring tool vendir, whose documentation is silent
on it). A template updater (Copier) replays the user's diff on a fresh
generation of the new version and leaves conflict markers or `.rej`
files; it records the template and version in an answers file and has
a command that says whether a newer version exists. A vendoring by
git itself (git subtree) and a plain clone pulled forward are a real
three-way merge: the user's changes stay, an overlap with uncommitted
work stops the pull before anything is touched. An installer with a
manifest (Spec Kit, GSD Core, OpenSpec) treats files as owned whole:
an unchanged managed file is replaced, a changed one blocks the
upgrade, is backed up, or is overwritten, depending on the tool and a
`--force`. A marker block lets a tool own a few lines inside a
user-owned file. A repository made from a GitHub template has no
update channel at all. The disconfirming query found what the card
expected for the installer and the marker families (two dated
reports of user content lost at an update, one maintainer's own
problem statement, one documented warning) and nothing for Copier or
cruft, which is a gap of this run, not evidence of safety. Every page
was read through a summarising fetch, so every quote below is as the
fetch relayed it and should be checked before it is quoted onward.
The unexpected thing: the losses found did not come from the ordinary
update of a changed file but from the edges, a missing marker, a
`--force` that an upgrade path passes on its own, and two installers
of one tool writing the same file.

## Question

#### Card 5: Keeping a copy in someone else's project in step with its source
- **Question:** When files of a base are copied or generated into a user's own repository, how do tools keep that copy in step with later versions of the source: template updaters, vendoring tools, installers with a manifest, a plain clone pulled forward? How does each treat files the user changed, files the user added beside them, and files the new version removes or renames? How does the project record which version of the base it holds, and how is the user told that a newer one exists?
- **Why it matters:** Wherever the base lands inside the user's project instead of beside it, this is the deployment loop, and the user's own things not being overwritten is the condition.
- **What would answer it:** The documentation of the update mechanisms of such tools, and the update procedure of frameworks that install into a user's repository.
- **Where to look:** The documentation of template-update tools and of vendoring tools; the upgrade documentation of AI coding frameworks that copy themselves into a project; the attached note on framework distribution for the eleven frameworks of August 2026. Must turn up: a three-way merge on update, a manifest of installed files, a marker block inside a user-owned file.
- **Disconfirming query:** A search for reports of user changes lost at an update of such a tool; expected: several.
- **Stop rule:** Each family of mechanism has a primary source saying what it does with a user-changed file; nothing new from a differently worded query; the opening budget.

The baseline is the attached note of 2026-08-29. It already names
three ways frameworks survive an upgrade (ask-or-flag, a sparse
override layer over never-edited files, an install manifest with a
file taxonomy), names OpenSpec's marker blocks and GSD Core's
managed / user-owned / unknown classes, and concludes that copying
the engine into projects is the shape to avoid. It does not cover
template updaters, vendoring or a plain clone, does not say per
mechanism what happens to a changed, an added and a removed file,
says little on how a version is recorded and nothing on how a user
learns of a newer one, and carries no report of an actual loss. The
note must add those.

## Key findings

**F1. A template updater replays the user's diff on the new version
and leaves conflicts for the user; it is a merge by patch, and the
documentation does not call it a three-way merge.** [single source;
vendor documentation, read through a summarising fetch] Copier's
update page describes the algorithm under "How the update works": it
"regenerates a fresh project from the current template version",
compares it with the user's project to get a diff, updates the
project to the latest template, and "re-applies the previously
obtained diff and then runs the post-migrations" [1]. A hunk it
cannot place becomes a conflict: `--conflict inline`, the default,
"Updates the file with conflict markers", and `--conflict rej`
"Creates a separate `.rej` file for each file with conflicts" [1].
The preconditions are a valid `.copier-answers.yml`, a template
"versioned with Git (with tags)" and a destination under git, with a
clean `git status` before the run [1]. The term three-way merge does
not stand on the page as fetched; the effect (old base, user's side,
new side) is that of one. An older version of the same page is
reported by a search summary to name `rej` as the default; that page
was not opened, so the change of default over versions is unverified.

**F2. In a template updater a file the user deleted stays deleted,
a file marked skip-if-exists is only ever created, and a full
re-copy throws the user's changes away.** [single source; vendor
documentation, summarising fetch] Under "Handling of deleted paths":
"Template-based files/directories that were deleted in the generated
project are automatically excluded from updates"; paths matched by
`skip_if_exists` are the exception, their presence "is always
ensured, even during an `update` operation" [1]. `copier recopy`
"will discard all the smart update algorithm" and "The new template
will override any changes found in your local project" [1]. What the
update does with a file the user added beside the template's files,
and with a file the new template version removed or renamed, the
page as fetched does not say (see Not found).

**F3. A template updater records the template and the version in a
file in the project and offers a check that can fail a pipeline;
none of them tells the user on its own.** [consensus of two vendors'
documentation; summarising fetch] Copier keeps
`.copier-answers.yml`, warns "Never update `.copier-answers.yml`
manually", picks the newest git tag of the template compared by PEP
440, and has `copier check-update`, which prints "New template
version available." and with `--quiet` exits with code 2 when an
update exists [1]. Cruft keeps "a `.cruft.json` file that contains
the git hash of the template used"; `cruft check` returns "an error
and exit code 1" when the project is out of date, meant for CI, and
the README shows a scheduled GitHub Actions workflow that "runs
every Monday at 2am UTC and creates a new pull request if there are
changes detected" [2]. Cruft also carries a `skip` list of files
never updated and asks the user to review the changes before they
are applied [2]. How cruft applies a change to a file the user
edited the README as fetched does not say.

**F4. Vendoring through git itself, and a plain clone pulled
forward, are a true three-way merge: the user's committed changes
are merged, uncommitted ones that overlap stop the operation, and
renames are followed.** [consensus; the tool's own reference
documentation, summarising fetch] git's merge page, "Pre-merge
checks": "`git pull` and `git merge` will stop without doing
anything when local uncommitted changes overlap with files that
`git pull`/`git merge` may need to update"; under "True merge",
"It is possible to have modifications in the working tree as long as
they do not overlap; the update will preserve them", and on a
conflict the working tree files hold "3-way merge results with
familiar conflict markers" [3]. The `ort` strategy "can detect and
handle merges involving renames" [3]. The page still discourages a
merge over non-trivial uncommitted changes, since it "may leave you
in a state that is hard to back out of in the case of a conflict"
[3]. git subtree is the same merge applied to a subdirectory: a
subtree needs no "special constructions (like .gitmodules files or
gitlinks)", is "just a subdirectory that can be committed to,
branched, and merged along with your project", its `merge` "doesn't
remove your own local changes", `pull` is "Exactly like merge", and
`split` and `push` carry local changes of the subdirectory back
upstream [4]. Files the user added are simply files of the user's
history in both cases. The version held is the commit itself; what
the fetched pages say about being told of a newer one is nothing,
git has no notice short of a fetch.

**F5. A repository created from a GitHub template has no update
path.** [single source; platform documentation, summarising fetch]
"a repository created from a template starts with a single commit",
and "Branches created from a template have unrelated histories", so
"you cannot create pull requests or merge between the branches" [5].
The page describes no later synchronisation. A base handed out as a
template repository therefore needs one of the other mechanisms on
top to be updatable at all.

**F6. An installer with a manifest owns whole files and decides by
hash: unchanged is replaced, changed is stopped, backed up or
overwritten, unknown is left.** [emerging; two vendors'
documentation that agree on the shape and differ in the detail,
summarising fetch] GSD Core's manifest `gsd-file-manifest.json` maps
"Relative path → SHA-256, for distribution-owned files only" and
records the installed package version; "hash mismatch means locally
modified managed file"; "Managed files can be replaced automatically
when unchanged", "If changed locally, they must be backed up or
merged"; a user-owned file "must never be removed just because [it
sits] under a GSD directory"; "Never remove an unknown file" [6].
Spec Kit's `specify integration upgrade <key>` "uses the install
manifest to detect local edits", and if a managed file changed "the
command stops and asks you to inspect the change" unless `--force`
is given; shared scripts and templates are refreshed "when they are
unchanged from the previous managed copy"; `specs/` "will never be
modified during upgrades" [7]. Spec Kit's state lives in
`.specify/integration.json`, `specify integration status` reports
"any modified or missing managed files", and `specify self check`
reports whether the tool is up to date [7].

**F7. In the installer family the removal and the move of a file
are a mechanism of their own, and the maintainers name it as the
dangerous part.** [single source for the design, vendor
documentation; summarising fetch] GSD Core: "Remove a path only when
it is known to be GSD-managed and unchanged from the previous
manifest", a changed managed path is backed up before removal, a
change of layout is a `move-managed` action, the run is a Plan shown
before any change and a Journal with rollback data, and the problem
the design answers is an installer that can "delete a user-created
file because it happens to live inside a GSD-managed directory"
[6]. Spec Kit does not remove obsolete files: after an upgrade
duplicate commands can remain and the page tells the user to
"Manually delete the old command files from your agent's folder"
[7]. OpenSpec's update has a `--dry-run` that "reports the files an
update would add, change or delete, and writes nothing", plans
"moves out of a tool's former directory" and cleans legacy files
only with `--force` [8].

**F8. A third variant stamps the version into each generated file
and declares generated files the tool's own.** [single source;
vendor documentation, summarising fetch] OpenSpec's skill files
record the version that generated them and the update compares it
with the installed CLI, so "a hand-edited file whose version still
matches is left alone", while command files carry no stamp, are
compared by content, and "edits to those files count as drift and
are overwritten"; the stated rule is "generated files are OpenSpec's
to own" [8]. OpenSpec is also the one tool found that tells the user
of a newer version without being asked: `openspec update` queries
the package registry, prints a notice of the newer CLI and in an
interactive terminal offers to upgrade, with an environment variable
to switch the check off [8]. It also warns of the reverse trap:
"running `openspec update` against a stale install reports
everything up to date" [8].

**F9. A marker block lets a tool own some lines of a user-owned
file; its weak point is the file that has no markers.** [consensus
on the mechanism, timeless module documentation; single source for
the failure, a vendor changelog; summarising fetch] Ansible's
`blockinfile` "will insert/update/remove a block of multi-line text
surrounded by customizable marker lines", default marker "# {mark}
ANSIBLE MANAGED BLOCK", places the block at the end of the file
when nothing says otherwise, and requires a different marker per
block: "When more than one block should be handled in one file you
must change the `marker` per task" [9]. The failure: Trellis, an AI
coding framework, introduced replacement of a managed block in
`AGENTS.md` between `<!-- TRELLIS:START -->` and `<!-- TRELLIS:END
-->`; when the markers were absent the fallback "returned the bare
Trellis template, which silently replaced the user's content"; the
next release, dated 2026-04-29, appends the block after the existing
content instead, and the recovery advised was `git checkout
<pre-update-commit> -- AGENTS.md` [10]. The attached note's claim
that OpenSpec uses marker blocks was not confirmed on the one
OpenSpec page opened in this run [8], which does not mention them;
this is not a contradiction, only a page that does not cover it.

**F10. The disconfirming query: losses are reported for the
installer and marker families, at the edges of the mechanism, and
none was found for the template updaters.** [emerging; two dated
primary reports, one vendor warning, one vendor problem statement;
summarising fetch] (a) Spec Kit issue #3849, opened and closed
2026-07-29, version 0.14.2: `integration upgrade` regenerated skill
files from the core templates and "removes the command content
supplied by installed extensions or presets"; the proposed fix was
itself a `force` flag passed by the upgrade path [11]. (b) Trellis,
F9 [10]. (c) Spec Kit's own upgrade page warns to "commit or back up
local customizations before using `init --here --force`" and gives
`git restore .specify/memory/constitution.md` as the way back [7].
(d) GSD Core's migration design opens from the deletion of a user's
file in a managed directory as a known danger [6]. Two searches for
reports of lost changes at a `copier update` or a `cruft update`
returned documentation and downstream guides, no report; no issue
tracker was searched directly. The card expected several; four were
found, all in tools that own whole files or blocks, none in the
tools that merge.

## Unexpected

The losses found are not the case the card's question centres on, a
user-changed file met by a new version. They are edge cases of
ownership: content that a second mechanism of the same tool
(extensions, presets) wrote into a file the first mechanism believes
it owns [11]; a fallback for the absent marker [10]; and a `--force`
whose meaning widens over time, in [11] as the fix itself. The lead:
where a base and a layer above it both write into one path, the
upgrade of the base is the likeliest place for the layer's content
to vanish, which is exactly the base-and-layers shape of the frame.

The tool that notifies best [8] does it because its updater is a
program installed from a package registry that it can query. A copy
that is updated by git or by a template tool has no such channel
unless something polls: a scheduled job that opens a pull request
[2], or a check with an exit code in a pipeline [1][2]. The lead:
"how the user is told" follows from where the updater itself lives,
not from the update mechanism.

Git's own merge refuses to start over overlapping uncommitted work
[3], and Copier asks for a clean tree first [1]; the installers
found make no such demand in the pages read [6][7][8]. Recovery in
every loss report was git [7][10]. The lead: a clean, committed
working tree before an update is the one safeguard common to the
mechanisms that did not lose anything.

## Not found

- What a declarative vendoring tool does with a file changed or
  added inside a managed directory. vendir's overview says it
  "allows to declaratively state what should be in a directory" [12]
  and its sync page says the lock file records the resolved
  reference, "for `git`, resolved SHAs are recorded" [13]; neither
  page as fetched says whether a sync replaces the directory's
  contents. That it does is the natural reading of "declaratively"
  and is this note's inference, not a finding.
- What Copier does with a file the new template version removed or
  renamed, and with a file the user added; looked for in [1].
- How cruft applies an update to a file the user changed (a
  three-way apply, reject files); looked for in [2].
- The field names inside `.copier-answers.yml` that hold the
  template and the version; not on [1] as fetched.
- How git subtree with `--squash` records which upstream commit the
  subdirectory holds; not on [4] as fetched.
- A general re-apply of backed-up local edits in GSD Core, which the
  attached note reports (`gsd-local-patches/`, `/gsd-update
  --reapply`); [6] as fetched mentions `gsd-local-patches/` for one
  runtime only. Not contradicted, not confirmed here.
- Any report of user changes lost at an update by Copier or cruft;
  two searches, no issue tracker opened.
- Any figure on how often such losses happen; no source gives one.
- An interactive per-file prompt at update (the overwrite / keep /
  diff question of older scaffolders); not looked for within the
  budget.

## Options

1. **Keep the base beside the project, never inside it.** Nothing to
   keep in step; the attached note's conclusion. Trade-off: the card
   is about the case where this is not possible, and whatever the
   user's own things need from the base must still be reachable.
2. **A plain clone pulled forward by git, the user's things in paths
   the base never ships.** A real three-way merge, renames followed,
   an overlap with uncommitted work refused before anything changes
   [3]; the version is the commit. Trade-off: the user's project and
   the base share one history or one working tree, a changed base
   file is a conflict the user must resolve at every pull that
   touches it, and nobody is told of a newer version without a
   fetch.
3. **git subtree: the base as a subdirectory merged in.** The same
   merge, the user's repository stays one plain repository with no
   nested git [4], and local changes can be sent back by `split` and
   `push`. Trade-off: the base must live under one prefix, which the
   layout of a tool that expects its files at fixed paths of the
   root may not allow; the recording of the held version under
   `--squash` was not verified here.
4. **A template updater (Copier) over a tagged base.** The user's
   edits to base files survive as a replayed diff, deletions are
   remembered, the version is in an answers file, a check command
   exists [1]. Trade-off: a dependency on a third-party tool for
   every user, conflicts land as markers in working files, and the
   treatment of removed and renamed files is undocumented on the
   page read.
5. **An installer of the base's own with a manifest of hashes.**
   Whole files owned by the base, replaced when unchanged, the
   upgrade stopped when changed, unknown files never touched, a
   plan shown first, removal and move as explicit actions [6][7].
   Trade-off: it is a program to write and maintain, the removal
   path is where the danger sits [6], and `--force` must never be
   passed by the upgrade path itself [11].
6. **A marker block, for the one file both sides must write.**
   Only for a file the user owns and the base must add lines to, the
   always-on instruction file being the obvious one. Trade-off: the
   no-marker case must append and never replace [10], and each
   writer needs its own marker [9].

Options 2 to 5 exclude one another per file; option 6 combines with
any of them.

## Relevance to this project

The agent's own inferences, marked as such throughout this section.

The findings sort the mechanisms by one question: does the base own
whole files, or does it merge into files the user may also change.
The mechanisms that merge (git, subtree, Copier) lost nothing in
this run's evidence but hand the user conflicts; the mechanisms
that own (installers, marker blocks) are quiet in the normal case
and lose content at their edges. For a base whose stated condition
is that an upgrade never writes where the user keeps his own things,
ownership by path is the fitting rule, and it rests on F6, F7 and
F10: the base's files are never edited by the user, the user's
agents, checks, definitions and templates live in paths the base
never ships, and the one shared file gets a marker block with an
append fallback (F9). Under that rule the transport matters less
than it seems: a plain pull by git (option 2) already gives refusal
over uncommitted overlap, rename following and the commit as the
version for nothing, and is what the frame's present "a user clones
and works in" already is; a manifest installer (option 5) buys the
same guarantees at the cost of a program, and becomes necessary
only when the base must land inside a repository that is not a
clone of it. This is chosen against a template updater (option 4),
whose strength, keeping the user's edits to base files, is a
strength the ownership rule makes unnecessary.

Three things the findings say to carry whatever the transport:
record the held version of the base in one file of the project and
let a layer state the version it needs against that file (F3, F6);
make removal and renaming of a base file an explicit, listed action
of a release, never a side effect of "this directory is ours"
(F7); and give the user a check that says a newer base exists, run
by something that already runs, a status command or a scheduled
job, since no merging mechanism notifies by itself (F3, F8). The
lead under Unexpected applies directly to layers: a layer that
writes into a path of the base is the Spec Kit failure waiting to
repeat (F10a).

How sure: every source is a primary read through a summarising
fetch, one page per tool, so the per-tool statements are single
sources and the quotes need a check against the pages before they
are relied on word for word. The shape of the families is firm; the
gaps listed under Not found are real.

Consult when: deciding whether the base lands inside or beside a
user's project; designing an install or update script and its
manifest; deciding what an upgrade may delete or rename; writing
into a user-owned instruction file; deciding how a project records
the base's version and how a user learns of a newer one; a layer
and the base are about to share a directory.

## Sources

1. "Updating a project", Copier documentation, Copier project.
   Undated living documentation (latest), read 2026-11-14.
   https://copier.readthedocs.io/en/latest/updating/ Primary.
   Summarised fetch of the whole page. Original.
2. cruft README, cruft project on GitHub. Undated living README,
   read 2026-11-14. https://github.com/cruft/cruft Primary.
   Summarised fetch of the whole README. Original.
3. "git-merge", Git reference documentation, the Git project.
   Undated living documentation, read 2026-11-14.
   https://git-scm.com/docs/git-merge Primary. Summarised fetch;
   sections Description, Pre-merge checks, True merge, How conflicts
   are presented, merge strategies. Original.
4. "git-subtree", contrib documentation in the Git repository, the
   Git project. Undated living file, read 2026-11-14.
   https://github.com/git/git/blob/master/contrib/subtree/git-subtree.adoc
   Primary. Summarised fetch of the whole file. Original.
5. "Creating a repository from a template", GitHub Docs, GitHub.
   Undated living documentation, read 2026-11-14.
   https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template
   Primary. Summarised fetch of the whole page. Original.
6. "installer-migrations.md", GSD Core documentation, open-gsd on
   GitHub. Dated by the fetch from the page's own text as corrected
   2026-08-10 (page text, not a byline; unverified).
   https://github.com/open-gsd/gsd-core/blob/main/docs/installer-migrations.md
   Primary. Summarised fetch of the whole file. Original.
7. "upgrade.md", Spec Kit documentation, github/spec-kit. Undated
   living file, read 2026-11-14.
   https://github.com/github/spec-kit/blob/main/docs/upgrade.md
   Primary. Summarised fetch of the whole file. Original.
8. "cli.md", OpenSpec documentation, Fission-AI/OpenSpec. Undated
   living file, read 2026-11-14.
   https://github.com/Fission-AI/OpenSpec/blob/main/docs/cli.md
   Primary. Summarised fetch; the part on `openspec update`.
   Original.
9. "ansible.builtin.blockinfile module", Ansible documentation, the
   Ansible project. Undated living documentation (latest), read
   2026-11-14.
   https://docs.ansible.com/ansible/latest/collections/ansible/builtin/blockinfile_module.html
   Primary. Summarised fetch; synopsis, parameters, notes. Original.
10. "v0.5.0-beta.19", Trellis changelog, the Trellis project's
    documentation site; publisher not named on the page. Dated
    2026-04-29 by the page's own release date.
    https://docs.trytrellis.app/changelog/v0.5.0-beta.19 Primary (a
    vendor's changelog about its own product). Summarised fetch of
    the whole page. Original.
11. "[Bug]: `integration upgrade` overwrites extension-and preset-
    provided Copilot skills", issue #3849, github/spec-kit. Opened
    and closed 2026-07-29, dated by the issue page.
    https://github.com/github/spec-kit/issues/3849 Primary (a user's
    report with the maintainer's automated assessment). Summarised
    fetch of the whole thread. Original.
12. vendir documentation, overview, v0.46.x, Carvel project.
    Undated, versioned documentation, read 2026-11-14.
    https://carvel.dev/vendir/docs/v0.46.x/ Primary. Summarised
    fetch of the whole page. Original.
13. "Sync command", vendir documentation v0.46.x, Carvel project.
    Undated, versioned documentation, read 2026-11-14.
    https://carvel.dev/vendir/docs/v0.46.x/sync/ Primary. Summarised
    fetch of the whole page. Original.

## Opened and not used

- https://carvel.dev/vendir/docs/latest/sync/ : the fetch returned
  only a redirect to [13], no content; superseded by [13].

## Search record

Queries, in order:
1. Copier update, three-way merge, conflicts, answers file.
2. cruft update, `.cruft.json`, check, diff.
3. vendoring tool vendir, sync, lock file, local changes
   overwritten.
4. Disconfirming: update lost or overwrote customisations, Copier,
   cruft, Spec Kit, BMAD.
5. OpenSpec update, managed block markers, AGENTS.md overwritten.
6. Disconfirming: Copier update issue, silently lost, deleted,
   overwrote.
7. Disconfirming: BMAD installer update overwrote custom agent
   files.
8. GSD Core installer migrations, managed, user-owned, unknown,
   manifest.
9. Disconfirming: Copier issues, file deleted, removed from
   template, renamed, data loss.

Pages opened, fifteen openings: [1], [2], the vendir "latest" sync
URL (redirect only), [7], [11], [6], [10], [13], [3], [5], [8], [4],
[9], [12]; fourteen distinct pages and one failed opening. Every
opening was a summarising fetch.

The disconfirming query (queries 4, 6, 7 and 9): found a dated
report of content lost at a Spec Kit upgrade [11], a dated
changelog admitting user content silently replaced at a Trellis
update [10], Spec Kit's own warning to back up before a forced
re-init [7], and GSD Core's problem statement on deleting a user's
file [6]. For Copier and cruft it found nothing; for BMAD it found
only documentation and third-party mirrors, none opened. A search
summary's mention of a Spec Kit "known issue" overwriting the
constitution came from a mirror that was not opened and is not
cited for content.

The run ended on the opening budget. The stop rule's first part was
met for four of the five families (template updater, git merge and
subtree, manifest installer, marker block) and not for the
declarative vendoring tool, whose two pages are silent on a
user-changed file.
