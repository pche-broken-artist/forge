---
date: 2026-11-14
project: forge
topic: keeping a copy in someone else's project in step with its source
derived_from: 2026-08-29-framework-distribution-in-the-field.md; web sources below
engine: antigravity
model: engine default
usage: {"input_tokens":116750,"output_tokens":26908,"thinking_tokens":21039,"cache_read_tokens":799080,"total_tokens":143658}
run: tmp/research/2026-11-14-anvil-carrying-layers/05-updating-a-copy
status: immutable
---

# Keeping a copy in someone else's project in step with its source

## In short

Four distinct mechanisms keep a copied base in step with its source:
three-way merge template updaters, vendoring tools, manifest-driven
installers, and plain git clones pulled forward. Template updaters
(Copier, Cruft) reconstruct the original ancestor commit recorded in a
local state file and apply three-way merges or generate patch reject
files, leaving user-added files untouched. Vendoring tools divide into
git-integrated three-way merges (`git-subrepo`, `git-subtree`) and
declarative sync utilities (`vendir`) that destructively overwrite
managed directories on update. Manifest installers (Spec Kit, GSD Core,
shadcn/ui) track file paths explicitly and halt or dry-run before
overwriting user modifications, while in-file marker blocks (OpenSpec)
isolate engine instructions within user-owned files. The disconfirming
query confirmed repeated incidents of lost user customizations when
updaters fall back to full overwrite flags or when managed directories
are retired without strict file taxonomies. An unexpected finding is that
three-way template updaters critically depend on immutable upstream git
history to reconstruct merge ancestors; rebased or squashed upstream
tags break future automated updates.

## Question

#### Card 5: Keeping a copy in someone else's project in step with its source
- **Question:** When files of a base are copied or generated into a
  user's own repository, how do tools keep that copy in step with later
  versions of the source: template updaters, vendoring tools, installers
  with a manifest, a plain clone pulled forward? How does each treat
  files the user changed, files the user added beside them, and files the
  new version removes or renames? How does the project record which
  version of the base it holds, and how is the user told that a newer one
  exists?
- **Why it matters:** Wherever the base lands inside the user's project
  instead of beside it, this is the deployment loop, and the user's own
  things not being overwritten is the condition.
- **What would answer it:** The documentation of the update mechanisms of
  such tools, and the update procedure of frameworks that install into a
  user's repository.
- **Where to look:** The documentation of template-update tools and of
  vendoring tools; the upgrade documentation of AI coding frameworks that
  copy themselves into a project; the attached note on framework
  distribution for the eleven frameworks of August 2026. Must turn up: a
  three-way merge on update, a manifest of installed files, a marker
  block inside a user-owned file.
- **Disconfirming query:** A search for reports of user changes lost at an
  update of such a tool; expected: several.
- **Stop rule:** Each family of mechanism has a primary source saying
  what it does with a user-changed file; nothing new from a differently
  worded query; the opening budget.

The baseline to beat is the attached survey
`2026-08-29-framework-distribution-in-the-field.md`, which identified
four framework deployment architectures and three survival mechanisms
(ask-or-flag prompts, sparse override layers, and install manifests with
patch journals) across eleven AI coding frameworks. That note observed
that copying engine files into user repositories creates persistent
upgrade collisions. This note broadens the analysis to general-purpose
tooling across four specific families, categorizing concrete behaviors
for user-modified, user-added, and upstream-removed files, version
provenance storage, and notification channels.

## Key findings

**F1: Template updaters perform a three-way merge against a recorded
generation-commit ancestor, isolating conflicts in inline conflict
markers or patch reject files.** [consensus, vendor report]
Template updaters such as Copier and Cruft store the template source URL
and the exact git commit SHA in a metadata answers file
(`.copier-answers.yml` or `.cruft.json`) during initialization [1, 2, 3].
When `copier update` or `cruft update` executes, the tool fetches the
current upstream template, checks out the ancestor commit recorded in the
answers file, and performs a three-way diff between ancestor, latest
template, and local working tree [1, 3]. Files modified by the user merge
automatically if edits do not overlap. Overlapping modifications trigger
either inline git-style conflict markers (`<<<<<<<` / `>>>>>>>`) or
generate detached patch reject files (`.rej`) depending on CLI flags
(`--conflict inline` or `--conflict rej`) [1, 3]. Files added by the
user that are absent from the template are left untouched [1]. Files
removed by the template are deleted from the destination unless
explicitly protected by template settings such as `_skip_if_exists` [2].

**F2: Vendoring tools divide into git-integrated merge workflows that
preserve local edits and declarative sync engines that overwrite
managed directories destructively.** [consensus, vendor report]
Git-native vendoring tools (`git-subrepo`, `git-subtree`) maintain an
integrated commit history inside a project subdirectory [4, 5]. In
`git-subrepo`, metadata is written to `.gitrepo` inside the subrepo
directory (recording remote URL, branch, and upstream commit SHA) [4].
Running `git subrepo pull` performs a standard git three-way tree merge;
user modifications inside the directory merge with upstream commits, and
unresolved conflicts halt as git merge conflicts [4, 5]. In contrast,
declarative directory managers such as Carvel `vendir` treat the target
directory as an ephemeral build artifact [7, 8]. `vendir sync` reads
`vendir.yml`, pins resolved commit SHAs in `vendir.lock.yml`, and
replaces target directory contents wholesale [7, 8]. Local user
modifications within a vendir-managed directory are wiped on update
unless redirected using the `--directory` local development override [8].

**F3: Manifest-driven installers track individual managed files,
guarding against overwrites via dry-run diffs, interactive flags, or
migration patch journals.** [consensus, vendor report]
Tools that copy individual assets into user projects (such as shadcn/ui
and GitHub Spec Kit) record managed files in a manifest (`components.json`
or `.specify/integration.json`) [9, 10]. User-added files beside
installed assets are ignored because they are absent from the manifest
[9, 10]. When updating assets, shadcn/ui provides `npx shadcn diff` to
compare local files against upstream registry definitions; it leaves
user-edited files untouched unless the user explicitly invokes
`--overwrite` [9]. Spec Kit halts and refuses to overwrite modified
managed files without `--force` [10]. GSD Core classifies files into a
three-way taxonomy (managed, user-owned, unknown); on update, it backs up
local edits to `gsd-local-patches/` and provides a reapplication command
(`/gsd-update --reapply`) [10]. When an upstream version removes a file,
manifest diffs identify and delete obsolete files, though GSD Core
specifically notes the risk of accidentally deleting user-created files
nested inside managed directories [10].

**F4: In-file marker blocks partition shared instruction documents into
managed engine blocks and protected user sections without external
manifests.** [single source, audit]
Frameworks that inject instructions into single user-owned root files
(such as OpenSpec injecting into `CLAUDE.md` or `AGENTS.md`) delimit
managed content between comment markers (`<!-- BEGIN ... -->` and
`<!-- END ... -->`) [10]. When the CLI updates installed definitions, it
parses the file, replaces only the text bounded by the marker blocks, and
preserves all surrounding user modifications and additions intact [10].
This eliminates the need for external manifest files or three-way merge
resolution when maintaining instructions inside user-owned files.

**F5: A plain downstream clone pulled forward relies on native git
three-way tree merges, tracking provenance through the commit graph.**
[consensus, standard]
When a downstream repository maintains a base fork or upstream remote,
updates are pulled via `git fetch` and `git merge` (or `git rebase`) [6].
Git calculates the common ancestor (merge base) between the local branch
and upstream tracking ref [6]. User-modified files merge automatically
via git's recursive/ort merge strategies, prompting conflict markers only
on overlapping line changes [6]. User-added files remain untouched unless
an incoming upstream commit adds a file with the identical path (add/add
conflict). Renames and deletions are resolved via git tree diff heuristics
[6]. Version provenance is stored in the git DAG commit history rather
than in a configuration file, and update availability is signaled when
tracking branches diverge (`git status`) [6].

**F6: Version provenance is recorded in local configuration files or git
trees, but update notification requires active polling or scheduled CI
workflows.** [consensus, practitioner claim]
Across all four families, version provenance is captured locally:
- Template updaters: `.copier-answers.yml` (`_commit`, `_src_path`) [1]
  or `.cruft.json` (`commit`, `template`) [3].
- Vendoring tools: `.gitrepo` (`commit`, `parent`, `remote`) [4] or
  `vendir.lock.yml` (`commit`, `version`) [7].
- Manifest installers: `components.json` [9],
  `.specify/integration.json` [10], or lockfiles.
- Plain clones: Git commit parent SHAs [6].
No mechanism provides passive background notifications. Update
detection is strictly active: interactive CLI commands (`cruft check`,
`npx shadcn diff`, `git fetch && git status`) or automated CI jobs (such
as GitHub Actions workflows running `cruft check` or `vendir sync` and
opening pull requests) [3, 8, 9].

## Unexpected

The three-way merge updater model breaks if upstream git history is
rewritten [1, 3]. Because Copier and Cruft store the raw commit SHA of
the base template at generation time, git must be able to fetch that exact
object from the remote template repository during subsequent updates. If
the upstream template repository force-pushes, squashes releases, or
prunes historical tags, the ancestor commit cannot be resolved, causing
the three-way merge to fail and forcing users into manual reconciliations
or destructive re-copies (`copier recopy`) [1].

## Not found

No tool was found that provides semantic or AST-aware merge resolution
when applying template updates to code files; all evaluated updaters rely
exclusively on line-based diff3, unified diff patches, or git merge-file
algorithms [1, 3, 6]. Furthermore, no tool was found that offers ambient,
in-editor notifications of base engine updates without explicit command
execution or automated CI polling [3, 9].

## Options

Where an engine must be copied into a user repository, three primary
options exist for managing updates:

1. **Three-way merge template updater (Copier model):** The project
   adopts a template configuration (`copier.yml`), tracking base commits
   in `.copier-answers.yml`. Updates run via three-way merge, applying
   non-conflicting upstream changes and creating inline markers for
   conflicts.
   - *Trade-offs:* Full support for arbitrary user edits to template
     files; requires Python/Copier tooling and an enforced discipline of
     clean git working trees before updating.
2. **Strict file manifest with sparse override directory (GSD / BMAD
   model):** Shipped base files are marked immutable and tracked in an
   installation manifest. User customizations are restricted to dedicated
   override files (e.g., `_config/custom.toml` or `templates/overrides/`).
   Updates overwrite base files wholesale and reject modifications to
   managed paths.
   - *Trade-offs:* Eliminates merge conflict markers in engine files;
     prevents users from patching engine mechanics directly; requires
     authoring an override resolution engine.
3. **Marker block injection for shared entry points (OpenSpec model):**
   Engine commands inject bounded blocks into `CLAUDE.md`, while skills
   and scripts reside in a dedicated, unedited directory.
   - *Trade-offs:* Minimal implementation complexity; zero collision on
     user documentation; cannot support customized variations of shipped
     engine skills without full file shadowing.

## Relevance to this project

For a framework built on Claude Code, copying the base engine directly
into the user's repository creates ongoing maintenance liabilities,
mirroring the issues documented in
`2026-08-29-framework-distribution-in-the-field.md`. Destructive
vendoring (`vendir`) and copy-paste registries without diff tracking
(`shadcn add --overwrite`) risk overwriting user modifications.

If the base engine must live inside the user's repository, the
recommended approach combines two mechanisms:
1. **Marker blocks in `CLAUDE.md`** (OpenSpec pattern) to inject framework
   instruction pointers, leaving all user prompt engineering and project
   rules outside the markers untouched.
2. **A dedicated, unedited base directory with sparse user overrides**
   (BMAD pattern) rather than three-way merging. Base mechanics, skills,
   and hooks should reside in an isolated directory (e.g., `.forge/base/`)
   replaced wholesale during upgrades, while user extensions reside in a
   sibling directory (e.g., `.forge/user/`) that the upgrade script never
   writes to.

Consult when: Designing the distribution and update scripts for the base
mechanics; deciding whether to use template engines (Copier) versus
manifest scripts; establishing file boundaries between engine code and
user-authored Claude Code agents and skills.

## Sources

[1] Updating a project, Copier Documentation, undated (structured data /
live documentation), https://copier.readthedocs.io/en/latest/updating/ ;
primary; read in full; original.

[2] Configuring a template, Copier Documentation, undated (structured
data / live documentation),
https://copier.readthedocs.io/en/latest/configuring_a_template/ ;
primary; read in full; original.

[3] Cruft Documentation, Cruft maintainers, undated (live documentation),
https://cruft.github.io/cruft/ ; primary; read in full; original.

[4] git-subrepo repository and manual, Ingy döt Net, undated (structured
data / live repository README), https://github.com/ingydotnet/git-subrepo ;
primary; read in full; original.

[5] git-subtree Documentation, Git Project (git-scm.com), undated (live
manual page), https://www.git-scm.com/docs/git-subtree ; primary; read in
full; original.

[6] git-merge Documentation, Git Project (git-scm.com), undated (live
manual page), https://git-scm.com/docs/git-merge ; primary; read in full;
original.

[7] Carvel vendir Documentation, Carvel maintainers, undated (live
documentation), https://carvel.dev/vendir/docs/latest/ ; primary; read in
full; original.

[8] Carvel vendir sync command, Carvel maintainers, undated (live
documentation), https://carvel.dev/vendir/docs/latest/sync/ ; primary;
read in full; original.

[9] shadcn/ui CLI Documentation, shadcn, undated (live documentation),
https://ui.shadcn.com/docs/cli ; primary; read in full; original.

[10] 2026-08-29-framework-distribution-in-the-field.md, forge project
attached note, 2026-08-29 (byline / frontmatter), attached file (named by
file name alone); primary; read in full; original.

## Opened and not used

- StackOverflow and Hacker News discussions on `git-subrepo` workflows;
  secondary discussions, superseded by [4].
- PyPI and Homebrew packaging pages for Cruft and vendir; distribution
  metadata, superseded by primary documentation in [3] and [7].
- Community Reddit threads discussing shadcn `--overwrite` data loss;
  practitioner discussions, superseded by CLI documentation in [9] and
  findings in the search record.

## Search record

- `copier update three-way merge` — search; identified Copier three-way
  merge algorithm, answers file tracking, and conflict resolution flags.
- `site:copier.readthedocs.io updating a project` — search and page
  fetch; examined prerequisites, update steps, regeneration, and diff
  application at `https://copier.readthedocs.io/en/latest/updating/`.
- `site:github.com/ingydotnet/git-subrepo` — search; overview of
  git-subrepo capabilities and repository structure.
- `"git-subrepo" site:github.com/ingydotnet/git-subrepo` — search;
  examined `.gitrepo` metadata file and command syntax.
- `site:cruft.github.io/cruft/ "update"` — search and page fetch;
  examined `cruft check`, `cruft update`, `.rej` conflict handling, and
  `.cruft.json` tracking at `https://cruft.github.io/cruft/`.
- `"git-subrepo" README ingydotnet` — search and page fetch; examined
  `git-subrepo` synopsis, `.gitrepo` tracking file, and pull/merge
  behavior at `https://github.com/ingydotnet/git-subrepo`.
- `site:git-scm.com/docs git-subtree` — search and page fetch; examined
  subtree pull, squash merging, and history tracking at
  `https://www.git-scm.com/docs/git-subtree`.
- `site:git-scm.com/docs git-merge` — search and page fetch; examined
  merge base, 3-way merge strategies, and conflict handling at
  `https://git-scm.com/docs/git-merge`.
- `site:copier.readthedocs.io/en/latest/configuring_a_template/` — search
  and page fetch; verified `_answers_file`, `_skip_if_exists`, and
  settings schema at
  `https://copier.readthedocs.io/en/latest/configuring_a_template/`.
- `site:carvel.dev/vendir/docs/latest/` — search and page fetch; examined
  declarative directory vendoring, `vendir.yml`, and `vendir.lock.yml` at
  `https://carvel.dev/vendir/docs/latest/`.
- `site:carvel.dev/vendir/docs/latest/sync` — search and page fetch;
  examined `vendir sync`, `-l` lock enforcement, and `--directory`
  overrides at `https://carvel.dev/vendir/docs/latest/sync/`.
- `site:ui.shadcn.com/docs/cli "diff" OR "components.json"` — search and
  page fetch; examined `components.json`, `diff`, and `--overwrite`
  behavior at `https://ui.shadcn.com/docs/cli`.
- `"copier update" "overwrite" OR "lost" OR "conflict" issue github` —
  disconfirming query; evaluated reports of lost changes, inline
  conflict marker hazards, and `copier recopy` overwrite risks.
- `"shadcn" "overwrite" OR "lost" components diff update issue github` —
  disconfirming query; evaluated reports of overwritten local component
  customizations and the rationale for `shadcn diff`.

The run ended because the stop rule was met: each of the four families of
mechanisms (template updaters, vendoring tools, manifest installers, and
plain clones) had primary sources documenting their handling of user
modifications, additions, and deletions, and the disconfirming query
turned up multiple reports of lost user changes.
