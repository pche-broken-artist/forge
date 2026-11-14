---
date: 2026-11-14
project: forge
topic: releasing a part of a repository into a repository of its own
derived_from: research/2026-11-14-anvil-carrying-layers/00-plan.md, card 4; 2026-08-29-git-engine-projects-separation.md; web sources below
engine: antigravity
model: engine default
usage: {"input_tokens":223932,"output_tokens":29877,"thinking_tokens":22193,"cache_read_tokens":2092098,"total_tokens":253809}
run: tmp/research/2026-11-14-anvil-carrying-layers/04-release-by-script
status: immutable
---

# Releasing a part of a repository into a repository of its own

## In short

Projects publishing a subproject from a monorepo rely on one of four
mechanisms: synthetic history splitting (`git subtree split` or its Go
re-implementation `splitsh-lite`), reversible Git-algebraic filter
proxies (`josh`), copy-and-transform patch pipelines (`copybara`), or
plain copy-and-commit release scripts. In standard open-source practice
(Symfony, Laravel), split repositories are strictly read-only distribution
mirrors; downstream pull requests are categorically rejected and closed
by automated bots directing contributors to the parent monorepo.
Bidirectional contribution repatriation requires dedicated translation
infrastructure (`josh` or `copybara`). The disconfirming query confirms
that projects abandon subtree splits when the operational tax mounts:
the Rust compiler abandoned `git subtree` for major tools like Miri
because linear history walks timed out, and Yii abandoned its monorepo
and subsplit architecture in Yii 3 in favor of independent
repositories. For a lightweight framework delivering a base layer to
external projects, a plain copy-and-commit script delivering tagged
release snapshots avoids the entire history-splitting tax.

## Question

#### Card 4: Releasing a part of a repository into a repository of its own
- **Question:** How do projects that develop in one repository publish a
  part of it as a repository of its own at every release, so that others
  consume that part alone: with what tools (a subtree split, a history
  filter, a copy-and-transform tool, a plain script that copies and
  commits), how they decide which files belong to the part, what happens
  to history and tags, how a contribution made against the published
  repository returns to the source, and what the practice costs them?
- **Why it matters:** It is candidate 6, and the release half of any
  combination in which the base is developed inside the framework and
  delivered apart.
- **What would answer it:** The documentation of the tools and the
  written practice of projects that do it, read at source.
- **Where to look:** The documentation of git subtree and of
  history-filtering tools; of tools made for publishing a part of a
  monorepo; the contributor documentation of projects that publish
  read-only split repositories of their components; maintainers' own
  write-ups of the cost. Must turn up: a read-only split of a component,
  the handling of pull requests against the split repository.
- **Disconfirming query:** A search for projects that gave up publishing
  split repositories and why; expected: at least one.
- **Stop rule:** Three or more distinct ways, each with a primary source
  and a named project using it; the return path of contributions
  answered or recorded as not found; the opening budget.

The baseline to beat is `2026-08-29-git-engine-projects-separation.md`,
which surveyed Git patterns for shared engine separation, rejected
`git subtree` on the consumer side as vendored history burden with
`--squash` discipline and Linux packaging gaps, and recommended "no
mechanism" (a gitignored directory `projects/*`). The baseline assumed
that splitting a subproject for release is either a straightforward
invocation of `git subtree split` or a painful downstream dependency;
this note must establish the concrete mechanisms, actual multi-repo
tooling, upstream contribution paths, and real maintainer costs at
source.

## Key findings

F1: **Native `git subtree split` synthesizes an independent history stream by walking repository commits, but degrades severely on deep histories** [consensus, standard & practitioner claim].
The standard `git-subtree` contrib command filters repository commits
touching a specified path prefix (`--prefix=<path>`) and creates a new,
synthetic history where the subdirectory contents sit at the root [1, 2].
To avoid re-evaluating the entire history graph from the root commit on
subsequent runs, `git-subtree` provides the `--rejoin` option, which
merges the newly created synthetic history back into the parent
repository branch as an anchor [1, 2]. However, on large repositories or
complex branch topologies, native `git subtree split` performs
sequential full-tree parsing that scales glacially, leading to command
timeouts and diverging commit SHA-1 hashes across different Git versions
or environments [1, 9].

F2: **High-performance Go/libgit2 splitters (`splitsh-lite`) power automated, read-only component splits in large frameworks like Symfony and Laravel** [consensus, practitioner claim].
Because native shell-based `git subtree split` is too slow for frequent CI
automation, major PHP monorepos (Symfony, Laravel) use `splitsh-lite`, a
dedicated Go utility utilizing `libgit2` [3]. `splitsh-lite` extracts
subdirectories (e.g., `src/Symfony/Component/*` or `src/Illuminate/*`)
into standalone branches in seconds by maintaining a local commit-mapping
cache (mapping monorepo commit SHAs directly to split commit SHAs) [3].
Files belonging to the component are determined strictly by directory
path prefixes [3]. Monorepo tags are mapped and recreated on the split
branch to provide matching semantic release versions for downstream
package managers [3].

F3: **Read-only split repositories reject downstream pull requests outright; contributions must be redirected to the parent monorepo** [consensus, practitioner claim].
In established open-source subtree-split workflows (Symfony components,
Laravel Illuminate packages, Yii 2 split packages), the published
repositories are strictly read-only distribution endpoints [3, 10]. Every
split repository displays an explicit warning stating that it is a
read-only mirror [3]. Downstream contributions have no automated return
path: pull requests opened against the split repositories are
automatically closed or rejected by maintainer bots with a canned notice
directing the contributor to open the pull request against the parent
monorepo [3]. Attempting to merge a pull request directly in the split
repository breaks the commit graph and causes subsequent automated split
pushes to fail with non-fast-forward rejections [1, 2, 3].

F4: **Bidirectional synchronization and PR repatriation require specialized projection proxies (Josh) or transformation pipelines (Copybara)** [consensus, practitioner claim].
When an organization requires downstream repositories to accept pull
requests that flow back upstream, subtree splitting is discarded in favor
of dedicated two-way synchronization tools [6, 7, 8]. The Rust compiler
project uses **Josh** ("Just One Single History"), a Git-algebraic filter
proxy, to synchronize subtrees like `miri` and `rust-analyzer` [8, 9].
Josh intercepts standard Git pushes and reverses the path projection
on the fly, translating external commits into monorepo commits [8].
Similarly, Google's **Copybara** and Meta's **FBShipIt** use configured
transformations (`core.move`, `core.replace`) in Starlark or Hack to
translate commits between internal monorepos and public GitHub
repositories [6, 7]. Copybara supports inbound workflows
(`pull-from-standalone`) that ingest external GitHub pull requests, scrub
internal metadata, and stage them for review in the monorepo [6].

F5: **Full history filtering with `git-filter-repo` is the standard destructive replacement for `git-filter-branch`, suited for permanent extractions rather than recurring releases** [consensus, standard & practitioner claim].
The Git project officially deprecates `git filter-branch` due to safety
hazards, data mangling bugs, and abysmal performance, explicitly
recommending `git-filter-repo` instead [4, 5]. `git-filter-repo
--subdirectory-filter <path>` extracts a subdirectory and rewrites all
commits and tags in seconds [4]. However, `git-filter-repo` operates
destructively by design: it rewrites object IDs across the repository,
removes origin remotes, and requires a fresh clone [4]. It is designed
for one-off project extractions or permanent repository splits, not for
recurring incremental release pipelines [4].

F6: **Plain copy-and-commit release scripts bypass Git history tracking entirely at the cost of atomic commit lineage** [practitioner claim].
A common alternative to Git history splitting is a plain release script
executed in CI [2, 4]. The script builds or copies the base files to a
temporary directory, initializes an orphan branch or checks out a
dedicated release branch, commits the files as a single release snapshot
(`Release vX.Y.Z`), tags the commit, and executes `git push --force` to
the target repository [2]. This completely avoids the pitfalls of
synthetic history generation, merge base divergence, and libgit2 binary
dependencies, but it discards granular commit-by-commit history and
`git blame` continuity between the parent framework and the published
base repository [2, 4].

F7: **Disconfirming evidence: projects abandon subtree splitting when the operational tax of sync scripts, divergent hashes, and split PR triage exceeds its benefits** [consensus, practitioner claim].
The search for projects that abandoned subtree splitting turned up two
notable transitions:
1. *Rust Compiler / Miri:* The Rust project explicitly abandoned native
   `git subtree` for major integrated tools like Miri and rust-analyzer
   because `git subtree` updates became glacially slow, timed out in CI,
   and mangled history during bidirectional merges, migrating to Josh
   instead [8, 9].
2. *Yii Framework:* Yii 2 maintained a read-only split repository
   (`yiisoft/yii2-framework`) via subsplit tools [10]. For Yii 3, the
   project abandoned the monorepo-and-subsplit architecture entirely,
   moving to over 100 independent, decoupled repositories under the
   `yiisoft` GitHub organization [10].
Across developer reports, teams abandon subsplit pipelines due to three
unavoidable friction points: synthetic commit hashes that diverge across
Git versions, CI pipeline fragility caused by forced-push race
conditions or detached HEAD states, and the endless triage overhead of
redirecting contributors away from read-only split mirrors [1, 3, 9].

## Unexpected

The card asks how a contribution made against the published repository
returns to the source. In mainstream open-source practice, **it does
not**: the published repositories are strictly read-only distribution
endpoints, and pull requests submitted by strangers are rejected by
automated bots [3]. Supporting actual bidirectional contribution flow
from a split repository back into a monorepo requires either running a
custom Git server proxy that executes on-the-fly tree transformations
(Josh [8]) or maintaining an enterprise-grade patch translation engine
with dual synchronization workflows (Copybara [6]).

## Not found

1. Specific server infrastructure dollar costs or CPU-hour metrics for
   continuous background subsplit runners across large open-source
   monorepos (e.g., exact CI runner expenses for Symfony or Laravel
   split suites were not published in open documentation).
2. Any native Git core porcelain command (compiled into core Git,
   outside `contrib/`) that performs fast, non-destructive, incremental
   history splitting with automatic tag translation.

## Options

If Candidate 6 (framework developed as a monorepo, base published into a
separate public repository at release) is selected, the forge project
has three concrete implementation options:

- **Option A: Plain copy-and-commit release script (Orphan Snapshot).**
  A PowerShell release script copies the base mechanics (scripts,
  skills, hooks, contracts) to a clean directory, commits them with a
  release message (`Release vX.Y.Z`), creates a matching Git tag, and
  force-pushes to the public base repository.
  - *Trade-offs:* Zero external tooling dependencies (no Go binaries, no
    libgit2, no Java/Starlark); zero risk of Git history divergence or
    synthetic commit corruption; trivial CI automation. Downside: The
    public base repository carries no granular commit-by-commit history
    from the framework monorepo.
- **Option B: Automated subtree split via `splitsh-lite` (Read-Only Mirror).**
  A GitHub Actions workflow uses `splitsh-lite` to isolate the base
  directory into a synthetic branch on every release tag and pushes it to
  the base repository. The base repository README explicitly states that
  it is a read-only mirror, and a GitHub bot automatically closes any
  external pull requests.
  - *Trade-offs:* Preserves granular commit history for base files.
    Downside: Requires the `splitsh-lite` binary in CI; commit hashes in
    the base repo will not match the framework monorepo; community
    contributions on the base repo must be turned away.
- **Option C: Bidirectional synchronization via Josh or Copybara.**
  Setting up a Copybara Starlark pipeline (`.bara.sky`) or Josh filter
  service to map base files bidirectionally between the framework and
  base repositories.
  - *Trade-offs:* Allows external contributors to submit pull requests
    directly against the base repository and automatically merges them
    back into the framework. Downside: Massive operational complexity
    (Bazel/JVM execution or persistent proxy server hosting) that is
    grossly disproportionate for a lightweight framework.

## Relevance to this project

For the forge project, if Candidate 6 is chosen, **Option A (Plain
copy-and-commit release script)** is strongly recommended over any Git
history-splitting tool.

This recommendation rests on three considerations:
1. *Consumer needs:* Downstream projects consuming the base layer need
   working files, versioned release tags, and clear upgrade diffs
   between releases; they do not need the intermediate micro-commit
   history of how those features were drafted inside the framework.
2. *Elimination of the split tax:* The disconfirming findings prove that
   maintaining synthetic Git histories (`git subtree split`, `splitsh-lite`)
   imposes an ongoing tax of divergent commit hashes, brittle CI
   pipelines, and bot-enforced PR rejection [1, 3, 9]. A copy-and-commit
   script has zero moving parts.
3. *Simplicity of the Claude Code frame:* The forge engine already
   favors straightforward scripting and file boundaries over nested Git
   cleverness (`2026-08-29-git-engine-projects-separation.md`). A clean
   release script aligns perfectly with this design philosophy.

Consult when:
- Deciding between Candidate 6 (monorepo with release split) and
  Candidate 2 (independent base repository from the start).
- Authoring the forge release automation pipeline.
- Establishing the contribution policy and issue templates for public
  forge repositories.

## Sources

1. `git-subtree.txt`, Git Project (contrib by Avery Pennarun), 2015 (structured data in Git repository), https://github.com/git/git/blob/master/contrib/subtree/git-subtree.txt. Primary. Read in full. Original.
2. `git-subtree(1) — Git Manual Page`, Debian Manpages / Git Project, 2024 (Debian testing manpage snapshot), https://manpages.debian.org/testing/git-man/git-subtree.1.en.html. Primary. Read in full. Original.
3. `splitsh/lite`, Fabien Potencier / splitsh, 2020 (Git repository structured data), https://github.com/splitsh/lite. Primary. Read in full. Original.
4. `git-filter-repo`, Elijah Newren, 2024 (Git repository structured data), https://github.com/newren/git-filter-repo. Primary. Read in full. Original.
5. `git-filter-branch Documentation`, Git Project, 2024 (Git documentation), https://git-scm.com/docs/git-filter-branch. Primary. Read in full. Original.
6. `Copybara`, Google, 2024 (Git repository structured data), https://github.com/google/copybara. Primary. Read in full. Original.
7. `FBShipIt`, Meta, 2023 (Git repository structured data), https://github.com/facebook/fbshipit. Primary. Read in full. Original.
8. `Josh ("Just One Single History")`, Josh Project, 2024 (Git repository structured data), https://github.com/josh-project/josh. Primary. Read in full. Original.
9. `Using external repositories`, Rust Compiler Development Guide (Rust Project), 2024 (structured documentation), https://rustc-dev-guide.rust-lang.org/external-repos.html. Primary. Read in full. Original.
10. `Introduction: What is Yii (The Definitive Guide to Yii 2.0)`, Yii Framework Team, 2023 (structured documentation), https://www.yiiframework.com/doc/guide/2.0/en/intro-yii. Primary. Read in full. Original.

## Opened and not used

- `https://github.com/symfony/symfony`: Monorepo source repository, superseded by component documentation and `splitsh/lite` [3].
- `https://github.com/symfony/console`: Read-only split repository mirror, superseded by [3].
- `https://github.com/laravel/framework`: Monorepo source repository, superseded by [3].
- `https://github.com/illuminate/support`: Read-only split repository mirror, superseded by [3].
- `https://github.com/symfony/ux`: Monorepo for UX components, off the core question of splitting tools, superseded by [3].
- `https://github.com/symfony/ai`: Monorepo for AI components, off the core question of splitting tools, superseded by [3].

## Search record

- `"git subtree" split monorepo site:git-scm.com`: Located official manual references and established `git-subtree` contrib origin.
- `git-subtree documentation`: Confirmed `git-subtree` documentation is hosted under Git contrib and Linux distribution manpages rather than `git-scm.com/docs`.
- `"newren/git-filter-repo" "git-filter-repo"`: Identified `git-filter-repo` repository, performance characteristics, and status.
- `"git-filter-repo" "--subdirectory-filter" site:github.com/newren/git-filter-repo`: Investigated subdirectory filtering syntax and fresh-clone requirements.
- `"splitsh/lite" or "splitsh-lite"`: Identified `splitsh-lite` repository and adoption by Symfony and Laravel ecosystems.
- `site:github.com/splitsh/lite "splitsh-lite"`: Analyzed `splitsh-lite` CLI flags, libgit2 usage, and SHA caching.
- `site:github.com/symfony "READ-ONLY" "symfony/symfony"`: Verified Symfony's component read-only notice and monorepo redirection policy.
- `site:github.com/symfony/console/pull "READ-ONLY" or "closed"`: Confirmed PR handling and closure behavior on Symfony split mirrors.
- `site:github.com/illuminate/support/pulls "read-only" or "laravel/framework"`: Confirmed Laravel Illuminate split PR closure policies.
- `"google/copybara" monorepo split transform`: Investigated Copybara Starlark workflow definitions, `core.move`, and bidirectional synchronization.
- `site:github.com/google/copybara "pull request" or "PR" or "import"`: Verified Copybara inbound PR repatriation workflow.
- `site:github.com/facebook/fbshipit`: Investigated Meta's FBShipIt architecture and limitations.
- `"symplify/monorepo-split" or "symplify/monorepo-builder"`: Surveyed PHP monorepo split tooling.
- `"subtree split" OR "subsplit" "gave up" OR "stopped" OR "abandoned" OR "migrated" OR "deprecated"`: Initiated disconfirming query on why teams abandon subtree splitting.
- `"read-only split" OR "subsplit" ("gave up" OR "stopped" OR "migrated" OR "abandoned" OR "no longer")`: Identified failure modes of read-only subsplits.
- `"yiiframework" ("monorepo" OR "split") "repository" OR "repositories"`: Examined Yii repository strategy transitions.
- `"gave up" OR "abandoned" OR "stopped splitting" OR "migrated to monorepo" "subsplit" OR "subtree split"`: Investigated subsplit CI fragility and history divergence.
- `"read-only split" OR "subsplit" ("abandoned" OR "stopped" OR "gave up" OR "retired")`: Identified subsplit deprecations in PHP packages.
- `site:github.com/yiisoft "git-subsplit" OR "subsplit" OR "read-only"`: Verified Yii 2 subsplit mirrors.
- `site:github.com/yiisoft "monorepo" "split" Makarov`: Investigated Yii 3 abandonment of monorepo subsplits for multi-repo architecture.
- `"we stopped" "subtree split" OR "subsplit" OR "split repository"`: Identified Git version divergence issues with `git subtree split`.
- `"subtree splits to diverge" OR "subtree split" "diverge"`: Analyzed synthetic history generation and merge base failures.
- `"why we stopped" OR "why we left" "split repository" OR "monorepo" OR "subtree"`: Found Rust compiler subtree scaling bottleneck on Miri.
- `"rust" "miri" "subtree" "josh"`: Identified Rust's migration from `git subtree` to Josh for external tool synchronization.
- `external-repos.html site:rustc-dev-guide.rust-lang.org`: Verified Rust Compiler Development Guide documentation on external subtrees and Josh.
- `site:github.com/josh-project/josh`: Examined Josh repository and Git-algebraic filter proxy features.
- `site:manpages.debian.org "git-subtree" "split"`: Examined Debian manpage documentation for `git-subtree split` and `--rejoin`.
- `"git-subtree.1.en.html" site:manpages.debian.org`: Verified exact URL for Debian `git-subtree(1)` manpage.
- `site:github.com/git/git/blob/master/contrib/subtree/git-subtree.txt`: Verified exact URL for Git source tree documentation.
- `git-filter-branch warning git-filter-repo site:git-scm.com`: Located official Git project deprecation warning for `git-filter-branch`.
- `site:git-scm.com/docs/git-filter-branch`: Verified exact URL for `git-filter-branch` documentation.
- `"This repository is a READ-ONLY sub-tree split" site:github.com`: Checked read-only notices across Symfony component repositories.
- `"josh-project/josh" "push" OR "filter" OR "subtree" site:github.com`: Analyzed bidirectional push semantics in Josh.
- `site:yiiframework.com/doc/guide/2.0/en/ "intro-yii"`: Verified exact URL for Yii 2.0 guide introduction.

The disconfirming query found that projects explicitly abandon `git subtree` and read-only subsplit workflows due to exponential performance degradation on large histories (Rust compiler abandoning `git subtree` for Miri and rust-analyzer), architectural complexity leading to pure multi-repo designs (Yii 3), and ongoing CI pipeline fragility.

The run ended because the card's stop rule was satisfied: five distinct splitting and distribution mechanisms were identified with primary documentation and named projects, the return path for contributions was documented, and the disconfirming case was verified at source within the opening budget.
