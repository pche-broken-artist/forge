---
date: 2026-11-14
project: forge
topic: migrating a user's data when the base changes the shape of files
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-14-anvil-carrying-layers/07-data-migration
derived_from: research/2026-11-14-anvil-carrying-layers/00-plan.md, card 7; no known notes; web sources below
---

# How tools bring a user's project forward when a new version changes the shape of its files

## In short

Five distinct mechanisms were found, each with the tool's own
documentation behind it: (a) a migration run at update time, selected
by the window between the recorded old version and the new one
(Copier, Nx, Django); (b) a one-off rewrite command per major version,
with the rule that majors are not skipped (Terraform 0.13); (c) an
upgrade at read time, the file on disk keeping its old version stamp
and a chain of upgrade functions run in memory (OpenTimelineIO);
(d) a permanent opt-in version key in the user's file, every old value
read for good (Rust editions, SQLite's file format); (e) no migration
of the user's content at all, because the tool overwrites only its own
managed files and declares the user's directories out of reach
(Spec Kit, OpenSpec, BMAD). The skipped-versions case is answered and
the answers conflict: Copier and Django's in-progress squash walk the
whole window, while Terraform, Nx and Django's advice to third-party
projects tell the user to go through every release in order, and Nx
documents a case where a jump over several majors silently applies
only the last major's migrations. The disconfirming query found what
it expected: SQLite and Rust editions deliberately have no migration,
and the price they name is a limit on what may ever change, not a
maintenance figure. Sureness: moderate. Every page was read through a
summarising fetch that returned quotations; the quotations below are
as that fetch gave them and were not checked against the raw page. The
unexpected thing: the AI coding frameworks nearest to the framed
project mostly avoid the problem by never owning the shape of the
user's documents, which is the opposite of a base that owns records, a
ledger and an ID scheme.

## Question

**Card 7: Migrating a user's data when the base changes its shape**

- **Question:** When a new version of a base changes the shape of
  files a user's project already holds (records, a state file,
  identifiers, front-matter), how do tools bring an existing project
  forward: a migration run once with a recorded version, an automatic
  rewrite of sources, reading old and new shapes side by side,
  refusing to run until migrated? How is a project told it is behind,
  what is done about a project that skipped several versions, and how
  is a migration made safe to repeat?
- **Why it matters:** The base owns records, a ledger and an ID scheme
  that live in the user's project for months; an update that reaches
  the code and not the data breaks the project.
- **What would answer it:** The documentation of migration mechanisms
  of tools whose users hold data in the tool's format in their own
  repositories.
- **Where to look:** The upgrade and migration documentation of tools
  with versioned state or schema held by the user (infrastructure
  state, configuration formats with a version field, static-site and
  documentation generators, automated source rewrites); the migration
  commands of AI coding frameworks that have one. Must turn up: a
  version field in the user's file, a migration that is idempotent, a
  chain of migrations across skipped versions.
- **Disconfirming query:** A search for tools that deliberately have
  no migration and keep reading every old shape, and what that costs
  them; expected: at least one.
- **Stop rule:** Three or more distinct mechanisms with a primary
  source each; the skipped-versions case answered or recorded as not
  found; the opening budget.

The frame: a framework on Claude Code (one instruction file, skills,
isolated subagents, hooks, templates, Python scripts) in a public git
repository, to be split into a general base owning the mechanics, the
present framework as the first operating layer, later layers, and a
place for what a user makes for himself where an upgrade never writes;
the base used in many projects and each updatable to its latest
version.

Baseline: the packet attached no known notes. The note has to beat
only the general knowledge that "tools have migrations"; it does so
where it names which mechanism each tool documents, what it says
about skipped versions and repetition, and where the documentation is
silent.

## Key findings

**F1. A migration selected by the window between the old and the new
version, run only on update, is a documented mechanism of a template
tool whose output lives in the user's repository.** [single source |
vendor documentation, read through a summarising fetch] Copier
declares migrations in the template; each may carry a `version`,
"the version that the template update has to go through to trigger
this migration", and the rule is "they will only run when *new
version >= declared version > old version*", in the order declared
[2]. "Migrations will also only run when updating (not when copying
for the 1st time)" [2]. A migration receives the version before and
after as variables (`VERSION_FROM`, `VERSION_TO`) and a stage,
`before` or `after`; in the update, pre-migrations run before the new
template is applied and post-migrations after the user's own diff is
re-applied [1][2]. The old version is read from the project's answers
file, which the documentation forbids editing by hand: "Never update
`.copier-answers.yml` manually" [1]; the update works best when the
template is "versioned with Git (with tags)" and the destination is
under git [1]. That the field holding the template's commit is named
`_commit` rests on a search snippet only; the page opened did not
name it.

**F2. The same window rule answers skipped versions by construction
in Copier, and a migration with no version runs on every update.**
[single source | vendor documentation, summarising fetch] Since the
condition is a comparison against the old and the new version, a
project three releases behind runs every migration whose version lies
in between, in declared order [2]. "If no version is specified the
migration will run on every update" [2]: the agent's inference is
that such a migration must be safe to repeat, the documentation
opened does not say so in those words. The update page gives no
advice against skipping versions [1].

**F3. Where the migrations are written per major version, the tools
tell the user not to skip, and one documents what goes wrong
otherwise.** [consensus among three tools | vendor documentation,
summarising fetch] Terraform: "Terraform supports upgrade tools and
features only for one major release upgrade at a time" and "please
upgrade through the latest minor releases of all of the intermediate
versions first" [3]. Nx: "The recommended process is to update, at
most, one major version at a time" [5], "the safest path and is what
Nx recommends", and when an update crosses more than one major the
tool "asks how far to jump" [4]. The documented failure, under a
caution about Angular: "If you try to update over multiple major
versions, only the migrations for the latest major version will be
applied" [5]. Django, to a maintainer who removes old migrations
after squashing: "if you're a third-party project, ensure your users
upgrade releases in order without skipping any" [6]. This conflicts
with F2 only in appearance: the tools that keep every migration and
select by window can walk a long gap; the tools that drop or do not
ship old migrations cannot, and push the walk onto the user.

**F4. A one-off rewrite command per release, and a state that is
upgraded on the first run and cannot be read by the older version
afterwards.** [single source | vendor documentation of an old
release, summarising fetch] Terraform 0.13 shipped
`terraform 0.13upgrade`, which "will automatically modify the
configuration of your current module" [3]. The state held by the user
is upgraded by ordinary use: Terraform updates the state "the first
time you run `terraform apply` after upgrading", and the result is
one-way: "Terraform v0.12 cannot parse a state snapshot that was
created by this command" [3]. This is the case of a project shared by
several people: once one of them has upgraded the state, the others
are forced to follow. The page is the guide of a release several
years old; it shows the mechanism, not the tool's present practice.

**F5. Generated migrations kept in a file in the user's repository
and run as a second step, repeatable.** [single source | vendor
documentation, summarising fetch] Nx splits the update into two
phases: `nx migrate` updates the versions "and writes a
`migrations.json` file", which "only contains the migrations
appropriate for the update you are currently applying";
`nx migrate --run-migrations` then runs them [4]. The file is the
record of what is pending: "If this file does not exist, then there
are no migrations to run"; it may be kept so that others can apply
the same process to code merged from other branches, and removed
afterwards [4]. Repetition is stated outright: "you can run
`nx migrate --run-migrations` as many times as you want", and
"Running the command again runs the migration again, which is also
how you restart it after an interruption" [5]. Nx computes what must
run from what is installed: "By default, Nx uses currently installed
packages to calculate what migrations need to run" [5]; the version
record is thus the user's dependency file, not a stamp of its own.

**F6. Upgrade at read time: the version is stamped on each object in
the user's file and a chain of upgrade functions runs in memory.**
[single source | project documentation, summarising fetch]
OpenTimelineIO: every serialisable object "has `schema_name` and
`schema_version` fields"; on reading, "it will upgrade the schemas to
the version supported by the library before instantiating the
concrete in-memory object", and "will call each upgrade function in
order in an attempt to get to the current version" [7]. The chain may
be sparse: the functions "need not cover every version number" [7].
Downgrades exist for writing a file an older reader can take, and
there "must be called in order with no gaps" [7]. The page does not
say whether a file on disk is ever rewritten in place; as read, the
old shape stays on disk until the user saves. This is the
side-by-side reading the card asks about, and it handles skipped
versions with no act of the user.

**F7. A graph of migrations with dependencies, and squashing as the
way a long chain is shortened without stranding a project that is
behind.** [single source | vendor documentation, summarising fetch]
Django migrations name the migrations they depend on [6]. A squashed
migration is "marked to say they replace the previously-squashed
migrations, so they can coexist with the old migration files"; a
system part-way through "will keep using them until it hits the end
and then switch to the squashed history, while new installs will use
the new squashed migration and skip all the old ones" [6]. The old
files are removed only after waiting "until all systems are upgraded
with the new release" [6]. Django also refuses work on an
inconsistent record: where a migration is applied and its
dependencies are not, "Django will refuse to run migrations or make
new migrations until it's fixed" [6]. The page opened does not
describe how applied migrations are recorded; that record lives in
the user's database, not in his repository, so this is the mechanism
by analogy.

**F8. The AI coding frameworks opened migrate their own installed
files and declare the user's documents out of reach; none documents a
versioned migration of the user's content.** [emerging | vendor
documentation of three tools, summarising fetch; the field moves, the
pages are undated and were read 2026-11-14] Spec Kit: "The `specs/`
directory is completely excluded from template packages and will
never be modified during upgrades"; its upgrade "uses the install
manifest to detect local edits" and "blocks when manifest-tracked
integration files were modified locally, unless you pass `--force`"
[8]. OpenSpec: active changes are "Completely preserved", archived
changes and main specs "Untouched"; `openspec init` and
`openspec update` "detect legacy files and guide you through the same
cleanup process", by the presence of the old paths and not by a
version stamp; in files shared with the user, "Only the OpenSpec
marker blocks are removed; everything you wrote stays"; one file of
the old shape is left for the user to move by hand; without a
terminal the tool stops with "Legacy files detected in
non-interactive mode" unless forced [9]. BMAD: customisations "live
under `_bmad/custom/` and survive setup refreshes"; setup "moves your
`_bmad/custom/` files when a skill was renamed" and "checks whether a
migration applies and asks whether to run it"; the page warns of its
preview that "updates can break an existing setup" [10]. What the
BMAD migration does and how it is recorded the page does not say.

**F9. How a project is told it is behind: by the update command
itself, never by a separate notice, in every tool opened.**
[consensus among the tools opened | vendor documentation, summarising
fetch] Copier compares the recorded version with the template's tags
at `copier update` [1][2]; Nx computes pending migrations when
`nx migrate` is run [4]; OpenSpec detects legacy files during `init`
or `update` and prompts "Upgrade and clean up legacy files? (Y/n)"
[9]; BMAD's setup "checks each module's version" and asks [10];
Terraform's older binary fails to parse the newer state [3]. No
source opened describes a tool that checks at every ordinary run and
refuses all work until a migration is done (see Not found).

**F10. Disconfirming query: tools that deliberately have no migration
exist, and the cost they name is a limit on change.** [consensus |
vendor and project documentation, summarising fetch] SQLite: since
3.0.0 "the file format has been fully backwards compatible", and the
developers "are committing to supporting those files for decades into
the future"; the price is paid on the other side, where older
versions read newer files only "as long as the database does not make
use of newer features that are unknown to that older version" [11]
(page last updated 2022-09-13 by its own footer). Rust editions: the
version key sits in the user's manifest, "Each crate chooses its
edition within its `Cargo.toml` file", editions are opt-in, and
"crates in one edition **must** seamlessly interoperate with those
compiled with other editions"; the stated cost: "this required
compatibility implies some limits on the kinds of changes that can be
featured in an edition. As a result, changes found in new Rust
editions tend to be 'skin deep'" [12]. Neither page gives a figure
for the cost of carrying the old shapes.

## Unexpected

The card assumes the base must migrate the user's data. The three AI
coding frameworks opened [8][9][10] get by without it because they
own only installed files (commands, skills, templates) and treat the
user's documents as free text they never parse. A base whose scripts
parse the user's records, front-matter and identifiers is in the
position of Copier, Django or OpenTimelineIO, not of those
frameworks; their upgrade guides are a model for the "never writes
into the user's place" half of the frame and no model for the data
half. This is a lead on which comparison class fits, not a
conclusion.

Spec Kit's install manifest [8] is a mechanism for a neighbouring
question: it lets an upgrade tell a file the tool installed and the
user left alone from one the user edited, and block on the second.
That is the upgrade of code and templates, not of data, and may
belong to another card of the bundle.

OpenSpec's marker blocks inside files the user also writes
(`CLAUDE.md`, `AGENTS.md`) [9] show a way to own a part of a shared
file and remove or replace only that part.

## Not found

- No primary source opened states in words that a migration "must be
  idempotent". What was found is repetition by construction: a window
  that excludes versions already passed [2], a run that may be
  repeated at will [5], an upgrade in memory that leaves the file
  alone [7]. Pages on idempotent migration patterns appeared in the
  search results and were not opened.
- No documentation of a tool that refuses every ordinary command
  until the project is migrated. The nearest: Django's refusal on an
  inconsistent migration record [6], OpenSpec's stop in
  non-interactive mode [9], and Terraform's older binary failing on a
  newer state [3].
- No figure, from any source, for what it costs to keep reading every
  old shape. A search result attributed to Apache Lucene's developer
  notes the claim that this is among the hardest problems of file
  formats; the page was not opened and is not cited.
- Static-site and documentation generators, named in the card, were
  not reached within the budget.
- Automated source rewrites as a class of their own (codemods, the
  Rust edition's own rewrite command, Angular's update schematics)
  were reached only through Nx [4][5] and the Terraform command [3].
- Jupyter's notebook format version and git's repository format
  version, both candidates for a version field in the user's file,
  were not opened.
- How Copier names the field of the recorded version, and how Django
  stores its record of applied migrations: not on the pages opened.

## Options

1. **A version stamp in the project and a kept chain of migrations
   selected by window** (the Copier shape, F1, F2). The project file
   records the shape it is in; every migration declares the version
   it belongs to; an update runs those between old and new, in order.
   Handles skipped versions with no act of the user; costs keeping
   every migration for as long as any project may be that far behind,
   or a declared floor below which the user must step through an
   older release (F3, F7).
2. **One migration per release that changes the shape, majors not
   skipped** (the Terraform and Nx shape, F3, F4). Cheapest for the
   maintainer; pushes the walk onto the user, and Nx documents a
   silent partial migration when the rule is broken [5]. For a
   stranger cloning a public repository months later this is the
   weakest point.
3. **Read old and new shapes, rewrite only on write** (the
   OpenTimelineIO shape, F6). No blocking step and nothing to tell
   the user; every reader in the base (scripts, checks, and the
   instructions an agent reads) must carry the chain of upgrade
   functions, and files in git stay in mixed shapes for an unbounded
   time, which is hard on checks that compare a file with a template.
4. **Never change the shape incompatibly; a permanent opt-in key**
   (the SQLite and Rust shape, F10). No migration at all; the price
   is a standing limit on what the base may change, "skin deep" in
   Rust's words [12].
5. **Own less** (the Spec Kit and OpenSpec shape, F8). Narrow what
   the base parses in the user's project so that fewer changes are
   shape changes at all; where a file is shared, own a marked block.
   Does not remove the need for one of options 1 to 4 for what
   remains.

Combinations are natural: 5 to shrink the surface, 1 for what
remains, 4 as a discipline between majors.

## Relevance to this project

The recommendation, the agent's own inference from the findings:
option 1 as the mechanism, with option 5 applied first and the
squashing discipline of F7 as the way the chain is later shortened.
It rests on three things found. First, the property the frame asks
for, every project updatable to the latest version of the base,
including one that slept through several releases, is delivered by
construction only where the migrations are selected by a window
between a recorded version and the new one [2] or chained at read
time [7]; the tools that migrate per major tell the user not to skip
[3][5][6]. Second, the framed project's files are parsed by scripts
and compared with templates, which makes it unlike the AI coding
frameworks that need no migration [8][9][10] and makes mixed shapes
on disk (option 3) costly. Third, a recorded version in the user's
own file is what every windowed mechanism reads [1][2][7][12].

Chosen against: option 2, because of the documented silent partial
migration [5] and because a stranger cannot be relied on to step
through releases; option 3, because the readers here are several and
one of them is an agent reading instructions, not a library with one
deserialiser; option 4 alone, because the frame says new features
keep arriving in the base.

Points the findings add for whoever designs it, each the agent's
inference unless cited: a migration with no version runs every time
and must be repeatable [2]; a migration that may be interrupted
should be restartable by running it again [5]; a shared project is
forced forward by the first clone that migrates [3], so migrating on
one clone and handing the result over through git is the safe order;
old migrations may be dropped only when no project can still need
them, or with a stated floor [6]; the upgrade should be able to tell
its own untouched files from those the user edited [8].

Limits: every source was read through a summarising fetch; the
quotations should be checked against the pages before any is quoted
onward. The AI framework pages are undated and their tools move
fast.

Consult when: the base first changes the shape of a record, the
ledger's inputs, the front-matter or the ID scheme; when deciding
where a project records the version of the base it is in; when a
layer must say which version of the base it needs; when an old
migration is proposed for removal; when choosing whether a script
should refuse to write into a project that is behind.

## Sources

1. "Updating a project", Copier documentation (copier-org), latest
   version; undated.
   https://copier.readthedocs.io/en/latest/updating/ ; primary;
   summarised fetch of the whole page, quotations as the fetch
   returned them; original.
2. "Configuring a template", Copier documentation (copier-org),
   latest version; undated.
   https://copier.readthedocs.io/en/latest/configuring/ ; primary;
   summarised fetch, the section on migrations only; original.
3. "Upgrading to Terraform v0.13", HashiCorp, Terraform documentation
   as kept under the v1.1.x tree; undated on the page.
   https://developer.hashicorp.com/terraform/language/v1.1.x/upgrade-guides/0-13
   ; primary; summarised fetch of the whole page; original. The
   unversioned address of the same guide returned 404.
4. "Automate updating dependencies", Nx documentation (Nrwl);
   undated.
   https://nx.dev/docs/features/automate-updating-dependencies ;
   primary; summarised fetch of the whole page; original.
5. "Advanced update process", Nx documentation (Nrwl); undated.
   https://nx.dev/docs/guides/tips-n-tricks/advanced-update ;
   primary; summarised fetch of the whole page; original.
6. "Migrations", Django documentation, version 5.2 (Django Software
   Foundation); dated by the version in the address only.
   https://docs.djangoproject.com/en/5.2/topics/migrations/ ;
   primary; summarised fetch, the sections Dependencies, History
   consistency, Squashing migrations and Supporting multiple Django
   versions; original.
7. "Versioning Schemas", OpenTimelineIO documentation (Academy
   Software Foundation), latest; undated.
   https://opentimelineio.readthedocs.io/en/latest/tutorials/versioning-schemas.html
   ; primary; summarised fetch of the whole page; original.
8. "Upgrade Guide", Spec Kit documentation (GitHub); undated.
   https://github.github.com/spec-kit/upgrade.html ; primary;
   summarised fetch of the whole page; original.
9. "Migration guide", OpenSpec (Fission-AI), the file
   docs/migration-guide.md of the main branch; undated.
   https://raw.githubusercontent.com/Fission-AI/OpenSpec/main/docs/migration-guide.md
   ; primary; summarised fetch of the whole file; original. The
   address https://openspec.dev/docs/migration-guide returned 404.
10. "Install BMad", BMAD Method documentation (bmad-code-org);
    undated.
    https://docs.bmad-method.org/start/install-bmad/ ; primary;
    summarised fetch, the passages on setup, updating and
    customisations; original. The address
    https://docs.bmad-method.org/how-to/upgrade-to-v6/ redirects
    here.
11. "File Format Changes in SQLite", SQLite project; last updated
    2022-09-13 by the page's own footer.
    https://www.sqlite.org/formatchng.html ; primary; summarised
    fetch of the whole page; original.
12. "What are Editions?", The Rust Edition Guide (Rust project);
    undated.
    https://doc.rust-lang.org/edition-guide/editions/index.html ;
    primary; summarised fetch of the whole page; original.

## Opened and not used

- https://developer.hashicorp.com/terraform/language/upgrade-guides/0-13
  : returned 404; superseded by [3].
- https://openspec.dev/docs/migration-guide : returned 404;
  superseded by [9].
- https://docs.bmad-method.org/how-to/upgrade-to-v6/ : a redirect
  notice only; superseded by [10].

## Search record

Queries, in order:

1. schema version field in user file, migration idempotent, chain,
   skipped versions (general): mostly small projects' own pages and
   mass-produced guides; gave the OpenTimelineIO lead.
2. Copier update, migrations, answers file: the Copier documentation
   across versions.
3. Spec Kit, BMAD, OpenSpec upgrade of an existing project: the three
   vendors' pages and several mirrors, the mirrors left alone.
4. The disconfirming query: file formats kept backward compatible
   with no migration, what it costs: SQLite, DuckDB, HDF5, Icechunk,
   Fuchsia, Lucene in the results; SQLite opened, Rust editions
   opened from a known address.

Pages opened: fifteen fetches, of which twelve are the sources above
and three failed or redirected (listed under Opened and not used).

The disconfirming query found what was expected: two tools that
deliberately have no migration and keep reading every old shape
(SQLite's file format, Rust editions), each naming its cost as a
limit on what may change, neither giving a figure.

The run ended on the opening budget, with the stop rule also met:
five distinct mechanisms with a primary source each, and the
skipped-versions case answered with its conflict named (F2, F3, F6,
F7).
