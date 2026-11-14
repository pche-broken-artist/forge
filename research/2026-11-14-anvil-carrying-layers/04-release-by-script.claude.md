---
date: 2026-11-14
project: forge
topic: releasing a part of a repository into a repository of its own
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-14-anvil-carrying-layers/04-release-by-script
derived_from: research/2026-11-14-anvil-carrying-layers/00-plan.md, card 4; known note 2026-08-29-git-engine-projects-separation.md; web sources below
---

# Projects that develop in one repository publish a part of it as a repository of its own in four distinct ways

## In short

Four ways were found, each read at its own source. (1) A split of a
directory's history, by `git subtree split` or its faster equal
`splitsh-lite`, pushed to a read-only repository and tagged by a
second script; Laravel does exactly this with two short shell
scripts. (2) A bot that filters and cherry-picks commits by a rules
file; Kubernetes publishes its `staging/` directories so. (3) A
copy-and-transform tool with one repository declared authoritative;
Copybara at Google, and ShipIt at Meta, the latter now unmaintained.
(4) A two-way sync, by `git subtree` or by josh; the Rust project
runs both. A fifth tool, `git filter-repo`, extracts a path with its
history but no opened page shows it used at every release. The
return path of contributions has three answers: refuse them at the
published repository and send people to the source (the common
one), import them by the tool, or run a true two-way sync at a
standing cost to maintainers. The disconfirming query found one
project that gave the practice up, Symplify in 2023, because
contributors' pull requests against the read-only packages were
closed and releases bundled unrelated packages. The unexpected
thing: no opened source shows a named project publishing by "a plain
script that copies and commits" without a split tool. Every page was
read through a summarising fetch, so the quotes below are as that
fetch returned them, not checked against the raw page by eye.

## Question

> #### Card 4: Releasing a part of a repository into a repository of its own
> - **Question:** How do projects that develop in one repository publish a part of it as a repository of its own at every release, so that others consume that part alone: with what tools (a subtree split, a history filter, a copy-and-transform tool, a plain script that copies and commits), how they decide which files belong to the part, what happens to history and tags, how a contribution made against the published repository returns to the source, and what the practice costs them?
> - **Why it matters:** It is candidate 6, and the release half of any combination in which the base is developed inside the framework and delivered apart.
> - **What would answer it:** The documentation of the tools and the written practice of projects that do it, read at source.
> - **Where to look:** The documentation of git subtree and of history-filtering tools; of tools made for publishing a part of a monorepo; the contributor documentation of projects that publish read-only split repositories of their components; maintainers' own write-ups of the cost. Must turn up: a read-only split of a component, the handling of pull requests against the split repository.
> - **Disconfirming query:** A search for projects that gave up publishing split repositories and why; expected: at least one.
> - **Stop rule:** Three or more distinct ways, each with a primary source and a named project using it; the return path of contributions answered or recorded as not found; the opening budget.

The frame of the card is the packet's: a framework on Claude Code to
be split into a base, operating layers and a user's own part, six
candidates compared, candidate 6 being the framework kept whole with
a script separating the base at every release into a public
repository of its own.

The baseline to beat is the known note of 2026-08-29. It surveyed
git's mechanisms for a different relation, an engine beside
independent project repositories, and rejected subtree there as a
way of *vendoring* the engine into each project ("N copies to
upgrade"). It says nothing of subtree used the other way round, to
*publish* a part outward, nothing of split tools, copy-and-transform
tools, tags of a published part, or the return of contributions.
This note covers that ground.

## Key findings

**F1. The commonest way is a split of one directory's history into
a synthetic history, pushed to a repository marked read-only.**
[consensus; tool documentation and two projects' own files]
`git subtree split` is documented to "Extract a new, synthetic
project history from the history of the <prefix> subtree", holding
"only the commits (including merges) that affected <prefix>", with
the directory's content at the root, "suitable for export as a
separate git repository" [1, split]. `splitsh-lite` states that it
"replaces the `subtree split` Git built-in command" for "splitting a
monolithic repository to read-only standalone repositories", and
that "both tools generate the same `sha1`s" [2]. Laravel's
`bin/split.sh` is a plain shell script over it: one function runs
`./bin/splitsh-lite --prefix=$1` and pushes the result with `git
push $2 "$SHA1:refs/heads/$CURRENT_BRANCH" -f`, once per component,
to `illuminate/<name>` [3]. The published repository describes
itself as "[READ ONLY] Subtree split of the Illuminate Database
component (see laravel/framework)" [5]. Symfony's component
repository points issues and pull requests to the main repository in
its README [6]; that Symfony's split is made by `splitsh-lite` was
not confirmed on any opened page.

**F2. The split is repeatable without stored state, which is what
makes it fit for every release.** [consensus; tool documentation]
"Repeated splits of exactly the same history are guaranteed to be
identical (i.e. to produce the same commit IDs) as long as the
settings passed to 'split' (such as '--annotate') are the same" [1].
`splitsh-lite` says the same in its own words, "two splits of the
same code always results in the same history and the same `sha1`s
for each commit", and adds a cache that makes later runs faster [2].
`git subtree` has `--rejoin` for the same purpose, at the price of a
merge commit in the source: "future splits can search only the part
of history that has been added since the most recent '--rejoin'"
[1].

**F3. A second way is a bot that distils commits by a rules file and
cherry-picks them into the published repository.** [single source
per claim; the project's own documentation] In Kubernetes "The code
in the staging/ directory is authoritative, i.e. the only copy of
the code", and "The content here will be periodically published to
respective top-level k8s.io repositories" [7]. The publishing-bot
uses `git filter-branch` to "distill the commits that affect a
staging repo", cherry-picks merged pull requests into the target,
and records its position in `Kubernetes-sha: <sha>` lines of the
commit messages; the rules live in `staging/publishing/rules.yaml`,
one `branches` stanza per repository [8]. It also rewrites the
module files of the target, so the published repository is not a
pure subset of the source [8].

**F4. A third way is a copy-and-transform tool with one repository
declared the source of truth.** [vendor claim for both; the tools'
own READMEs] Copybara "is a tool used internally at Google. It
transforms and moves code between repositories", "requires you to
choose one of the repositories to be the authoritative repository",
and names the use case "Importing sections of code from a
confidential repository to a public repository" [9]. It is
stateless: "it stores the state in the destination repository (As a
label in the commit message)" [9]. Its weekly releases come "without
any manual testing, version compatibility or correctness guarantees"
[9]. Meta's ShipIt, "a library written in Hack for copying commits
from one repository to another", carries the line "NOTE: This
project is no longer maintained", says Meta moved to a closed-source
successor, and points its users to Copybara [10]. No opened page
names an open-source project outside the two vendors that publishes
by either tool.

**F5. A fourth way keeps both repositories writable and syncs in
both directions, and the project that documents it also documents
its cost.** [single source; a project's contributor guide] The Rust
project lists Clippy under `git subtree` and nine components,
rust-analyzer, miri and rustfmt among them, under the josh tool
[13]. Josh describes itself as "fast, reversible Git history
transformation" and says it "enables you to represent a subfolder of
your monorepo as an independent repository" [12]. The guide's own
words on the cost: for subtree, "you will need to modify your local
git installation and follow a very precise set of instructions";
"you may have to redo the conflict resolution if your PR doesn't get
merged fast enough"; "If you specify the wrong directory or
repository you'll get very fun merges"; for josh, "Specific tooling
is required" [13]. The syncs "are typically handled by the
respective tool maintainers" [13].

**F6. A history filter extracts a path with its history, but no
opened source shows it run at every release.** [single source; tool
documentation] `git filter-repo` gives the example `git filter-repo
--path src/ --to-subdirectory-filter my-module --tag-rename
'':'my-module-'` and is "now recommended by the git project" over
`filter-branch` [11]. It bails "if we're not in a fresh clone"
unless forced [11]. The page says nothing of repeated or incremental
runs; that it is a tool for a one-time extraction is this note's
inference, not the page's statement. Kubernetes's bot does use the
older `filter-branch` repeatedly [8].

**F7. Which files belong to the part is decided by one of three
kinds of rule: a directory prefix, a rules file, or globs with
transformations.** [consensus across the tool documentation] A
prefix: `git subtree split --prefix` [1]; `splitsh-lite` widens it
with `from:to` ("move the split content to a sub-directory on the
target"), `from:to:exclude` and "multiple `--prefix` flags" [2];
Laravel's list is one directory per component [3]. A rules file:
Kubernetes, one staging directory per repository plus the branches
to publish [7][8]. Globs and transformations: Copybara's example
config moves paths (`core.move`), rewrites text (`core.replace`) and
protects destination files by `glob` [9]; ShipIt's `stripPaths` is
to "remove any modifications to paths matching `$patterns`, unless
they match something in `$exception_patterns`" [10].

**F8. A split carries commits, not tags; the tags of the published
repository are made by a separate step.** [single source for the
practice; a project's own script] Laravel's `bin/release.sh` tags
the source, then for each component clones the split repository,
checks out the release branch, runs `git tag $VERSION` and `git push
origin --tags` [4]; the tag therefore lands on the tip of the split
branch at that moment, by position and not by a mapping of commits.
`splitsh-lite`'s only word on it is `--target`, which "creates a
reference for the tip of the split" [2]. `git subtree`'s
documentation mentions tags only for `--squash` merges inward [1].
How the Kubernetes bot tags was not on the page opened [8]. Laravel
pushes the split with `-f` [3], so the published branch is
overwritten, never merged into.

**F9. The return path has three answers, and the commonest is to
refuse.** [consensus for the refusal; single sources for the rest]
(a) Refuse and redirect: Laravel's "[READ ONLY]" label [5];
Symfony's README sending issues and pull requests to the main
repository [6]; Kubernetes's checklist that a staging repository's
files "mention that PRs are not directly accepted to the repo" [7];
at Symplify a pull request to a split package "was closed instantly
because that package was read-only" [14]. The label does not stop
them arriving: the Laravel split repository showed seven open pull
requests on the day it was read, 2026-11-14 [5]. (b) Import by the
tool: Copybara names "Importing a change from a non-authoritative
repository into the authoritative repository" and says "the tool
allows contributions to any repository" [9]; ShipIt can "restore
original authors for GitHub pull requests" [10]. (c) A true two-way
sync, as in F5, where the published repository is where tool fixes
"should be filed" [13].

**F10. The costs the sources name are of four kinds.**
[practitioner claims and project documentation; no figures] To
contributors: pull requests closed and a source repository whose
shape is hard to enter, "When you want to contribute to ECS, it's
crazy" [14]. To consumers: "When a new release comes, there is 10
other package upgrade you don't use as well" [14]. To maintainers of
a two-way sync: the quotes of F5 [13]. To the source's tracker: the
Kubernetes bot's README warns that its account must not be able to
close issues upstream, since published commits carrying `Fixes
kubernetes/kubernetes#123` would otherwise close them [8]. To the
tool's owner: ShipIt's abandonment left its users to migrate [10].
One more is this note's own inference from the script, not a
source's statement: Laravel's release script runs under `set -e`
across some thirty repositories, so a failure midway leaves some
tagged and some not [4].

**F11. The disconfirming query found one project that gave the
practice up, and one partial case.** [single source; a maintainer's
own write-up] Symplify's maintainer wrote on 2023-01-28 that from
November 2022 the packages were moved into repositories of their
own; the reasons are those of F10, and "These problems have been
here for at least the past 4 years". After the move: "There were no
complaints. Quite the contrary - more people started to contribute
fixes!" He also names what was lost: "One commit and single pull
request improve 30 packages at once" [14]. Neos in 2019 archived two
split repositories that "will no longer be updated by the mono-repo
splits" and stopped splitting unmaintained branches, but this was a
renaming of packages, the practice kept [15]. ShipIt's end is the
end of a tool, not of the practice [10].

## Unexpected

The published repository is where strangers arrive. The one
write-up of leaving the practice reports that contributions rose
once the packages were real repositories [14], and a repository
labelled read-only still collects pull requests [5]. The card's
frame says everything "must work for a stranger"; a read-only base
repository works for a stranger who consumes and not for one who
wants to mend something, unless the redirect to the source is as
plain as the label.

The Rust arrangement runs the other way round from candidate 6:
development of a component happens in the component's own
repository and the large repository holds a synced copy [13]. The
card assumes the source is the whole; the best documented two-way
practice has the part as the place of work.

Commit messages travel with the commits. The Kubernetes warning
about issue-closing words [8] means that whatever a commit message
of the source says, references to issues included, is published
with a history-preserving split.

## Not found

- A named project that publishes a part by a plain script that
  copies files and commits, with no split tool; looked for in the
  two searches on read-only splits and in the pages opened. Laravel's
  script is plain, but it rests on `splitsh-lite` [3].
- Symfony's own description of how its components are split and of
  how pull requests against them are closed; the component's README
  [6] gives only the redirect, and a guessed path to a pull-request
  template returned 404.
- The mechanism by which any project closes pull requests against a
  split repository automatically; a workflows directory was visible
  in [5], its files were not.
- Any figure of cost: time per split, hours of maintenance, failure
  rates. The only number seen was in a search result not opened.
- How the Kubernetes bot carries tags, and how often it runs; not on
  the pages opened [7][8].
- An open-source project outside Google that publishes by Copybara,
  and Copybara's workflow modes; not on its README [9].
- Whether `git filter-repo` suits repeated runs [11].
- Anything on a split of a repository whose part is not one
  directory but files spread over several top-level directories, as
  a Claude Code framework's are; only `splitsh-lite`'s multiple
  prefixes touch it [2].

## Options

1. **A history split by prefix, with a tagging script** (Laravel's
   shape [3][4]). No state to keep, the same result on every run, a
   real history in the published repository. It asks that the part be
   a directory, or a few with `splitsh-lite`'s `from:to` mapping [2];
   it needs one more binary; commit messages are published as they
   are; the published branch is force-pushed.
2. **A bot with a rules file** (Kubernetes's shape [7][8]). Handles
   several branches and rewrites files on the way. Its own service to
   run and its own failure modes; out of proportion below many
   repositories. This judgement of proportion is this note's
   inference.
3. **Copybara** [9]. The only tool read that both selects by globs,
   transforms content and names the import of a contribution from the
   published repository as a use case. A Java tool built with Bazel,
   released without guarantees, with the fate of its sibling ShipIt
   as a caution [10].
4. **A two-way sync by josh or `git subtree`** [12][13]. The
   published repository takes contributions. A standing cost to
   maintainers that the one project documenting it describes in plain
   words, and, for subtree, the nesting of one history in another
   that the frame does not want.
5. **A copy-and-commit script of one's own**, one commit per release
   from a list of paths. Simplest to write and free of the prefix
   limit; no primary source or named project was found for it, so
   its cost is unknown from this research and it is an option on this
   note's inference alone.

In every option the return path is a separate choice among the three
of F9.

## Relevance to this project

What follows is the agent's own inference from the findings.

Candidate 6 is an established practice, not an invention: Laravel
releases some thirty read-only repositories from one with two short
scripts [3][4]. For a framework whose scripts already are the door
to git, that shape is the nearest: a split at the release, a tag in
the published repository by the same script, and a read-only label
with the redirect to the source. It is chosen against Copybara and a
publishing bot, whose weight fits organisations with many
repositories, and against a two-way sync, whose cost [13] buys
something the frame does not ask for.

Two things stand in the way and both should be settled before the
choice. First, a prefix split needs the base to be a directory; a
Claude Code framework keeps its parts under `.claude/`, `scripts/`
and `templates/` side by side, so either the base moves under one
directory in the source, which is candidate 1 inside candidate 6, or
the split takes several prefixes [2], or the release copies by a
list of paths (option 5, unsupported by any source read). Second,
the published base is where a stranger will arrive, and the only
account of leaving the practice [14] is about exactly that; the
redirect must be said in the published repository's own README and
contributing file, and pull requests there will still come [5].

A history-preserving split publishes the source's commit messages
[8]; a project whose messages name its own items should decide
whether the base's history is wanted in public as it stands or one
commit per release is enough.

Consult when: candidate 6 or a combination with it is weighed; the
release script of a base is designed; someone proposes accepting
pull requests on a published part; a tool for the split is chosen;
the question arises whether the base must be one directory.

## Sources

1. git-subtree(1), "git-subtree.adoc", the Git project,
   contrib/subtree; undated (a file of a repository's master
   branch);
   https://raw.githubusercontent.com/git/git/master/contrib/subtree/git-subtree.adoc
   ; primary; summarised fetch of the whole file; original.
2. "splitsh-lite" README, the splitsh project; undated (a file of
   the master branch);
   https://raw.githubusercontent.com/splitsh/lite/master/README.md ;
   primary; summarised fetch of the whole file; original.
3. `bin/split.sh`, laravel/framework, branch 12.x; undated;
   https://raw.githubusercontent.com/laravel/framework/12.x/bin/split.sh
   ; primary; summarised fetch, the script returned nearly verbatim
   with the middle of its list elided; original.
4. `bin/release.sh`, laravel/framework, branch 12.x; undated;
   https://raw.githubusercontent.com/laravel/framework/12.x/bin/release.sh
   ; primary; summarised fetch, the script returned verbatim;
   original.
5. illuminate/database, repository page on GitHub; undated, state as
   of 2026-11-14; https://github.com/illuminate/database ; primary;
   summarised fetch, the About text and the navigation only;
   original.
6. symfony/console, repository page on GitHub; undated, state as of
   2026-11-14; https://github.com/symfony/console ; primary;
   summarised fetch, the About text and the README's Resources
   section only; original.
7. "staging/README.md", kubernetes/kubernetes, master; undated;
   https://raw.githubusercontent.com/kubernetes/kubernetes/master/staging/README.md
   ; primary; summarised fetch of the whole file; original.
8. "Kubernetes Publishing Bot" README, kubernetes/publishing-bot,
   master; undated;
   https://raw.githubusercontent.com/kubernetes/publishing-bot/master/README.md
   ; primary; summarised fetch of the whole file; original.
9. "Copybara" README, google/copybara, master; undated;
   https://raw.githubusercontent.com/google/copybara/master/README.md
   ; primary, a vendor's documentation of its own tool; summarised
   fetch of the whole file; original.
10. "FBShipIt" README, facebook/fbshipit, main; undated;
    https://raw.githubusercontent.com/facebook/fbshipit/main/README.md
    ; primary, a vendor's documentation of its own tool; summarised
    fetch of the whole file; original.
11. "git filter-repo" README, newren/git-filter-repo, main; undated;
    https://raw.githubusercontent.com/newren/git-filter-repo/main/README.md
    ; primary; summarised fetch of the whole file; original.
12. "Josh" README, josh-project/josh, master; undated;
    https://raw.githubusercontent.com/josh-project/josh/master/README.md
    ; primary; summarised fetch of the whole file; original.
13. "Using External Repositories", Rust Compiler Development Guide,
    the Rust project; undated;
    https://rustc-dev-guide.rust-lang.org/external-repos.html ;
    primary; summarised fetch of the whole page; original.
14. "Good Bye, Monorepo", Tomas Votruba, 2023-01-28, dated as the
    summarised fetch reported the page's date;
    https://tomasvotruba.com/blog/good-bye-monorepo/ ; primary, the
    maintainer's own write-up; summarised fetch of the whole post;
    original.
15. "Changes to the handling of our read-only split repositories",
    Karsten Dambekalns, Neos project forum, 2019-09-26, dated as the
    summarised fetch reported the post's date;
    https://discuss.neos.io/t/changes-to-the-handling-of-our-read-only-split-repositories/4579
    ; primary; summarised fetch of the first post; original.

## Opened and not used

- https://raw.githubusercontent.com/symfony/console/HEAD/.github/PULL_REQUEST_TEMPLATE.md
  : a guessed path, HTTP 404, nothing read.

## Search record

Queries, in order:

1. read-only subtree split repository, monorepo, pull requests
   closed.
2. stopped publishing split repositories, abandoned, why (the
   disconfirming query).
3. Kubernetes staging, publishing-bot, published repository,
   contributions.
4. read-only split repositories discontinued, announcement (the
   disconfirming query, second wording).
5. Symplify monorepo split, packages to standalone repositories, why
   (the disconfirming query, a lead followed).

Pages opened, sixteen fetches, one of them a 404: sources [1] to
[15] and the page under Opened and not used. Every opening was a
summarising fetch; none was read raw.

The disconfirming query: its first wording returned general essays
on monorepos and nothing on point; the second returned the Neos
thread [15]; the third led to the Symplify write-up [14], the one
project found that gave the practice up, with its reasons. The
expectation of at least one was met by exactly one, a single
maintainer's account.

The run ended on the opening budget, with the stop rule met in the
same step: four distinct ways each with a primary source and a
named project (Laravel, Kubernetes, Google and Meta as the vendors'
own claim, Rust), and the return path answered.
