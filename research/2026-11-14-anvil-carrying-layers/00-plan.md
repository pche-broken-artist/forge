---
date: 2026-11-14
project: forge
topic: how the base (Anvil) should carry several operating layers and a user's own things
status: immutable
engines: claude, antigravity
derived_from: the principal's word of 2026-11-14; the brief 00-brief-engine-split.md v0.1; the notes research/2026-08-29-claude-code-packaging.md, research/2026-08-29-framework-distribution-in-the-field.md, research/2026-08-29-git-engine-projects-separation.md, research/2026-10-03-one-tool-a-core-with-modules-or-several-tools.md, research/2026-10-03-user-extensions-kept-apart-from-the-core.md, research/2026-10-03-operating-layer-architecture-and-debt.md, research/2026-11-07-engine-and-forge-framework-by-file.md; the second engine's review of the draft plan, tmp/research/2026-11-14-anvil-carrying-layers/plan-review/
---

# How the base should carry several operating layers and a user's own things

## Summary

Twenty-one notes on eleven cards, ten of them answered by two engines
independently. What the research says:

- **The always-on rules decide more than the carrier does.** A plugin
  still cannot carry a `CLAUDE.md` or a rules directory; both engines
  read this at the vendor. The only door with no dialog, no cap and
  reach into the reviewers is a memory file inside the working tree.
  Whatever carries the base, its rule text has to lie in the tree of
  every project that uses it.
- **The plugin is the only carrier with a version range and the one
  with the worst recorded deployment.** Dependencies between plugins
  with ranges, and since 2026-11-12 a required Claude Code version,
  exist nowhere else. Against it stand an update that does not reach
  the user (open since January 2026), an install that reports success
  and loads nothing, auto-update off for every third-party
  marketplace, path trouble in hooks on Windows, and loading rules
  that changed three times in one week of November.
- **Separating the base by a script at release is established
  practice** (Laravel releases some thirty read-only repositories
  this way), with a known price: the published repository is
  read-only and strangers still send pull requests to it.
- **The cut costs nearly the same under every candidate.** Most base
  features name no artefact of the chain; three programs hold the
  real work (the ledger, the light check that loads it, the
  migration). What differs is whether the single root every script
  computes must be split: candidates 1 and 6 avoid it, 2 to 5 pay it
  in full.
- **The tree already runs a project without a chain** (the `library`
  kind), and already saves the whole as two repositories side by
  side.

Where the engines differ: the second engine rejects the plugin on
three cards and recommends it on the stranger's first day; the first
engine keeps it open pending trials. The second engine states that an
agent preloads another package's skill by its namespaced name; the
first read the same pages and found it not stated. The second engine
says the plugin manifest has no field for the host version; the
first found it added on 2026-11-12. On the release script the second
engine recommends a plain copy by manifest with one commit per
release; the first found no named project doing it without a split
tool.

What it suggests for the project, Claude's own view: candidate 1
first and candidate 6 on top of it, the plugin not now. Keep one
repository, mark what is base in it, let a project that is not the
forge be a kind of project in a clone of the whole, which gives the
central update at once through the pull that exists; then publish
the base by a manifest-driven release script into a repository of
its own for those who want it without the forge. The scores and the
reasons stand in Claude's view.

Unexpected: the `agent` setting of a plugin, the strongest way a
plugin could carry an always-on core, was deprecated on 2026-11-12;
a pull of the engine delivers the head of `main`, not a release; a
user's own file in the clone would stop the upgrade as the pull
script stands.

## Plan (confirmed 2026-11-14)

### Purpose

The research serves the brief `00-brief-engine-split.md` (0.1) and
the threads it carries (THR.0230, THR.0300, THR.0480, THR.0850,
THR.0240). It is to say by which way the base (working name Anvil)
should carry several operating layers and what a user makes for
himself, by comparing the ways Claude Code and git offer today, and
to recommend the best one. The way is chosen for Claude Code.

What the principal said the research must hold to:

- The key property is the central update. The base is wanted in
  every project of his, also in those that are not the forge; it is
  maintained in one place, and every such project can be brought to
  the latest version of the base. New features are developed in the
  forge (the thread skill of 2026-11-12 is the example) and must
  reach those projects by an update. A one-off export failed exactly
  there: the trial of 2026-11-13 served well and could not receive
  what was built after it.
- Everything is public on GitHub; an update must work for a
  stranger.
- A further nesting of git inside git is not wanted.
- The cut is weighed feature by feature: some features wanted in the
  base may be too entangled with the forge to cut out cheaply, and
  may stay in the forge or move later.
- News is released daily today; that is to change. Releasing the
  base by whole versions is one way of forcing the user to update
  less often, not of forcing nothing.
- The sixth candidate below is at the least a transitional state,
  not a rejected one.

Known already: a plugin carries commands, agents, templates and
scripts, but a CLAUDE.md at a plugin root is not loaded
(`2026-08-29-claude-code-packaging.md`); git's submodules, subtree
and worktrees model a pinned dependency
(`2026-08-29-git-engine-projects-separation.md`); eleven comparable
frameworks separate the framework from the user's content in four
architectures (`2026-08-29-framework-distribution-in-the-field.md`);
the field ends at a small core that owns mechanism and format with
the content outside it
(`2026-10-03-one-tool-a-core-with-modules-or-several-tools.md`);
only plugins are namespaced, artefact definitions and templates have
no Claude Code mechanism of their own, and whether a pack's agent
can preload the engine's contract skill by bare name was left
unverified
(`2026-10-03-user-extensions-kept-apart-from-the-core.md`); where the
boundary runs through the files today
(`2026-11-07-engine-and-forge-framework-by-file.md`) and where the
debt of the operating layer lies
(`2026-10-03-operating-layer-architecture-and-debt.md`).

### Candidates

1. One repository with the layers as directories in it.
2. The base as a package of its own, each layer a repository of its
   own.
3. Two repositories lying side by side, joined by an import of one
   instruction file into the other.
4. A Claude Code plugin, possibly with a marketplace of its own.
5. Claude Code's own mechanisms without a plugin: user-level
   configuration beside the project's, imports into CLAUDE.md.
6. The forge kept as one whole, in which new features are developed
   and from which a script separates the base at every release into
   a public repository of its own; the projects that are not the
   forge read the base from that repository and update from it.

The research may add candidates and combinations; the candidates do
not exclude each other.

### Perspectives

- The author and maintainer: development in one place, central
  update into every project. Cards 4, 5, 6, 8.
- The author at daily work, the development loop: a change of the
  base is tried in the forge itself, without packaging and a
  release; an improvement found in a project that is not the forge
  returns to the base. Cards 1, 3, 4, 11.
- The deployment of a change, the deployment loop: how a change of
  the base reaches the user of every layer and every project; how a
  layer says which version of the base it needs and what happens
  when the user does not have it; how often the user is forced to
  update, daily today, and how that is eased, for instance by
  releasing the base by whole versions. Cards 1, 5, 6.
- The user of a project that is not the forge: install, update, his
  own things never overwritten. Cards 1, 5, 7.
- A stranger arriving from GitHub: the entry threshold. Card 10.
- Claude Code itself: what is really loaded in every session and
  what is not. Cards 1, 2, 3.
- A project with a history at an update: what happens to its
  records, its ledger and its IDs when a new version of the base
  changes their shape. Card 7.
- The cut: the cost of cutting feature by feature, and a
  transitional path. Card 11.
- Time, within Claude Code: what happens when Claude Code changes
  its mechanisms. Cards 1, 9.

Every candidate and every combination is judged by both loops, the
development loop and the deployment loop, and the synthesis says for
each how the two look in it, step by step.

### Assumptions

The answer lives mostly in the vendor's documentation and changelog,
in the documentation of the tools of git and of releasing, and in
the repositories of comparable frameworks. Claude Code stays the
harness. The candidates do not exclude each other. The plan would be
rethought if card 1 found that Claude Code has, since October 2026,
a mechanism of its own for a base with layers that none of the six
candidates names.

The documentation may lag behind what Claude Code does. The cards
therefore read the issue tracker beside the documentation, and the
synthesis lists what only a trial in the tool can settle; such
trials are proposed to the principal afterwards as a step of their
own and are no part of this research.

Premortem, Claude's: the research is done and missed the most
interesting thing, which was that the best answer is a combination,
for instance a script that releases the base as a plugin, and that
the notes each judged one candidate and none the joins between them.

### Left out

- Other harnesses than Claude Code and the open standards above them
  (AGENTS.md, Agent Skills): by the principal's decision of
  2026-11-14 the way is chosen for Claude Code; what would survive
  outside it is not researched.
- How the forge is developed and released in general (branches,
  tests before a release, release notes): only as far as it changes
  the choice of the way; the whole is a research of its own.
- Nesting git inside git (submodules, nested repositories) as a
  candidate: not wanted; considered as a counter-example only.
- The division of one tool into a core with modules as such: the
  note of 2026-10-03 covers it; precedents of classic software are
  read only for versions and release rhythm, in card 6.
- Trials in the tool: see Assumptions.

### Cards

The frame every card is read in, carried by every packet with its
card:

> A framework built on Claude Code (Anthropic's agent for the
> command line) consists of one always-on instruction file
> (CLAUDE.md), skills (its commands), isolated subagents (reviewers
> that preload a shared contract skill), hooks, templates and Python
> scripts, in one public git repository that a user clones and works
> in. It carries a chain of versioned documents and the mechanics
> under it: git through scripts, a ledger of state, versioning and
> history, an ID scheme, isolated reviewers, recipes and renders,
> sources and research with indexes. Its author wants to split it
> into a general **base** that owns the mechanics, the present
> framework as the first **operating layer** on that base, later
> more layers, and a place for what a **user makes for himself**
> (agents, checks, definitions, templates), kept where an upgrade
> never writes. The key property wanted: the base is used in many
> projects that are not the present framework, it is maintained in
> one place, and every such project can be updated to its latest
> version; new features are developed in the present framework and
> must reach those projects by an update, never by a one-off export.
> Everything is public on GitHub and must work for a stranger. A
> further nesting of git inside git is not wanted. The candidates
> compared: (1) one repository with the layers as directories;
> (2) the base as a package of its own and each layer a repository
> of its own; (3) two repositories side by side joined by an import
> of one instruction file into the other; (4) a Claude Code plugin,
> possibly with a marketplace of its own; (5) Claude Code's own
> mechanisms without a plugin, user-level configuration beside the
> project's and imports into CLAUDE.md; (6) the framework kept as
> one whole from which a script separates the base at every release
> into a public repository of its own, from which other projects
> update. Combinations are legitimate. Every candidate is judged by
> two loops: the development loop (a change of the base is tried in
> the framework itself, without packaging and a release) and the
> deployment loop (how the change reaches every user, how a layer
> says which version of the base it needs, how often a user is
> forced to update). The way is chosen for Claude Code only.

#### Card 1: Composing a base and layers in Claude Code
- **Question:** What does Claude Code offer in November 2026 for one package (a base) carrying mechanism and other packages (layers, a user's own things) carrying content on it: plugins and marketplaces, dependencies between plugins with version ranges and what happens when a required version is missing, namespaces, and the precedence when a base, a layer and a user define a skill, an agent or a hook of the same name? Can an agent of one package preload a skill of another package, and by what name? What changed since early October 2026?
- **Why it matters:** It decides whether the plugin, the package-per-layer and the no-plugin candidates can carry a shared reviewer contract and a required version of the base at all.
- **What would answer it:** The vendor's own statements of behaviour: the documentation pages of plugins, marketplaces, skills, subagents and settings, and the changelog entries since October 2026.
- **Where to look:** Anthropic's Claude Code documentation; the changelog and release notes of Claude Code; the reference of the plugin manifest and the marketplace file; the issue tracker of Claude Code for the behaviours the documentation leaves unsaid. Must turn up: plugin dependencies, the namespace rule of plugin skills, the `skills` field of a subagent.
- **Disconfirming query:** A search for reports that cross-plugin skill preloading or plugin dependency version ranges do not work as documented; expected: at least one open issue.
- **Stop rule:** Every sub-question has a statement from the vendor's documentation or changelog, or is recorded as not stated there; nothing new from a differently worded query; the opening budget of the brief.

#### Card 2: Always-on rules under each candidate
- **Question:** How does the content of an always-on instruction file reach every session of Claude Code under each of the six candidates: an `@` import into CLAUDE.md and its limits (depth, paths outside the project, approval), a rules directory, a hook at session start that injects text, a plugin's own means, user-level memory? What is loaded in an isolated subagent's context and what is not? How do hooks and settings of a base combine with those of a project, and can a plugin or an imported repository carry hooks and permission rules?
- **Why it matters:** The framework's conduct rests on rules that must hold in every session and every reviewer run; a candidate that cannot deliver them always-on is no candidate, whatever else it does.
- **What would answer it:** The vendor's documentation of memory and instruction files, of hooks, of settings precedence and of what a subagent receives.
- **Where to look:** Anthropic's Claude Code documentation: memory, CLAUDE.md imports, rules, hooks reference, settings, subagents, plugins; the changelog since August 2026; the issue tracker for imports across repositories and for instruction files in plugins. Must turn up: whether a CLAUDE.md at a plugin root is loaded today, the import depth limit, the SessionStart hook's output.
- **Disconfirming query:** A search for a statement that a plugin can now ship always-on instructions, against the expectation that it still cannot.
- **Stop rule:** Every candidate has a named mechanism for always-on rules with the vendor's statement, or "none found"; nothing new from a differently worded query; the opening budget.

#### Card 3: Scripts, templates and data files under each candidate
- **Question:** How does each candidate deliver Python scripts, templates and other data files, and how does a skill, a hook or a subagent reach them by a path that works on Windows, Linux and macOS: the variables Claude Code gives a plugin for its own root and its data, where an installed plugin lies on disk, whether a project's skill can address a file of a plugin or of a repository beside it? Where do a script's Python dependencies live in each case, and how do permission prompts, permission rules and the sandbox treat a script that lies outside the project directory?
- **Why it matters:** The base's mechanics are scripts and templates more than prompts; a way that delivers skills and loses the scripts they call does not deliver the base.
- **What would answer it:** The vendor's documentation of plugin structure, environment variables, permissions and sandboxing; the manifests of published plugins that ship scripts.
- **Where to look:** Anthropic's Claude Code documentation: plugins reference, hooks, permissions, sandboxing, settings; published plugins that carry scripts, read at source; the issue tracker for path variables on Windows. Must turn up: the plugin root variable, the plugin cache location, additional directories and their permissions.
- **Disconfirming query:** A search for reports that the plugin root variable or a hook's script path fails on Windows; expected: some.
- **Stop rule:** Each candidate has a stated way for scripts, templates and dependencies, or "none found"; the Windows behaviour has a source; the opening budget.

#### Card 4: Releasing a part of a repository into a repository of its own
- **Question:** How do projects that develop in one repository publish a part of it as a repository of its own at every release, so that others consume that part alone: with what tools (a subtree split, a history filter, a copy-and-transform tool, a plain script that copies and commits), how they decide which files belong to the part, what happens to history and tags, how a contribution made against the published repository returns to the source, and what the practice costs them?
- **Why it matters:** It is candidate 6, and the release half of any combination in which the base is developed inside the framework and delivered apart.
- **What would answer it:** The documentation of the tools and the written practice of projects that do it, read at source.
- **Where to look:** The documentation of git subtree and of history-filtering tools; of tools made for publishing a part of a monorepo; the contributor documentation of projects that publish read-only split repositories of their components; maintainers' own write-ups of the cost. Must turn up: a read-only split of a component, the handling of pull requests against the split repository.
- **Disconfirming query:** A search for projects that gave up publishing split repositories and why; expected: at least one.
- **Stop rule:** Three or more distinct ways, each with a primary source and a named project using it; the return path of contributions answered or recorded as not found; the opening budget.

#### Card 5: Keeping a copy in someone else's project in step with its source
- **Question:** When files of a base are copied or generated into a user's own repository, how do tools keep that copy in step with later versions of the source: template updaters, vendoring tools, installers with a manifest, a plain clone pulled forward? How does each treat files the user changed, files the user added beside them, and files the new version removes or renames? How does the project record which version of the base it holds, and how is the user told that a newer one exists?
- **Why it matters:** Wherever the base lands inside the user's project instead of beside it, this is the deployment loop, and the user's own things not being overwritten is the condition.
- **What would answer it:** The documentation of the update mechanisms of such tools, and the update procedure of frameworks that install into a user's repository.
- **Where to look:** The documentation of template-update tools and of vendoring tools; the upgrade documentation of AI coding frameworks that copy themselves into a project; the attached note on framework distribution for the eleven frameworks of August 2026. Must turn up: a three-way merge on update, a manifest of installed files, a marker block inside a user-owned file.
- **Disconfirming query:** A search for reports of user changes lost at an update of such a tool; expected: several.
- **Stop rule:** Each family of mechanism has a primary source saying what it does with a user-changed file; nothing new from a differently worded query; the opening budget.

#### Card 6: The release rhythm of a base others stand on
- **Question:** How do projects with dependent packages and users choose how often they release, how they keep a stable line apart from a development line, how a dependent piece says which version of the base it needs (a range, a minimum, a compatibility number), and what they do with a user who does not have it: refuse, warn, degrade? What do they promise not to change between versions?
- **Why it matters:** News of the framework is released daily today; the choice of the way changes with how often and how forcibly a user must update, and a layer needs a way to say which base it needs.
- **What would answer it:** The written release and versioning policies of projects with dependants, and the specifications of version ranges.
- **Where to look:** The versioning specifications in use; the release policies of platforms with plugins or providers that declare the host version they need (editors with packages, infrastructure tools with providers, language toolchains with channels); the plugin manifest of Claude Code for what it lets a plugin declare. Must turn up: a stable and a development channel, a minimum-host-version field, a deprecation policy.
- **Disconfirming query:** A search for arguments that a small single-maintainer project should not keep channels or ranges at all; expected: some, and their reasons.
- **Stop rule:** Three or more written policies with a primary source each, the single-maintainer case among them or recorded as not found; the opening budget.

#### Card 7: Migrating a user's data when the base changes its shape
- **Question:** When a new version of a base changes the shape of files a user's project already holds (records, a state file, identifiers, front-matter), how do tools bring an existing project forward: a migration run once with a recorded version, an automatic rewrite of sources, reading old and new shapes side by side, refusing to run until migrated? How is a project told it is behind, what is done about a project that skipped several versions, and how is a migration made safe to repeat?
- **Why it matters:** The base owns records, a ledger and an ID scheme that live in the user's project for months; an update that reaches the code and not the data breaks the project.
- **What would answer it:** The documentation of migration mechanisms of tools whose users hold data in the tool's format in their own repositories.
- **Where to look:** The upgrade and migration documentation of tools with versioned state or schema held by the user (infrastructure state, configuration formats with a version field, static-site and documentation generators, automated source rewrites); the migration commands of AI coding frameworks that have one. Must turn up: a version field in the user's file, a migration that is idempotent, a chain of migrations across skipped versions.
- **Disconfirming query:** A search for tools that deliberately have no migration and keep reading every old shape, and what that costs them; expected: at least one.
- **Stop rule:** Three or more distinct mechanisms with a primary source each; the skipped-versions case answered or recorded as not found; the opening budget.

#### Card 8: How comparable frameworks deliver a core with packs today
- **Question:** How do the comparable frameworks for AI coding agents deliver a core with packs, modules or extensions in November 2026, and how does an update reach an existing project: which moved to plugins, which install globally, which copy into the project, which keep one repository? What moved since August 2026? Does a published comparison of these ways of distribution already exist, and in what words does the field speak of them?
- **Why it matters:** The candidates are the field's four architectures seen from this project; what the field moved toward and away from in three months is the cheapest evidence of what holds.
- **What would answer it:** The repositories, release notes and installation documentation of the frameworks, read at source.
- **Where to look:** The repositories and release notes of the frameworks the attached note of August 2026 names (Spec Kit, BMAD, OpenSpec, Superpowers, Agent OS, cc-sdd, Conductor, GSD, LeanSpec, wshobson/agents, claude-task-master) and of any that appeared since; published comparisons of plugin against installer against clone. Must turn up: a framework that changed its way of distribution in 2026 and its stated reason.
- **Disconfirming query:** A search for a framework that moved away from plugins back to a clone or an installer; expected: none or one.
- **Stop rule:** Each of the eleven has its way of distribution today from its own repository, or "not checked"; a comparison found or recorded as not found; the opening budget.

#### Card 9: What failed
- **Question:** What trouble is reported with distributing a framework for Claude Code through plugins or marketplaces, with user content overwritten or broken at an update of a framework, and with a division of a tool into a core and separately released parts that was later taken back? What broke when Claude Code itself changed a mechanism such frameworks stood on?
- **Why it matters:** Each candidate will be scored by what it has been seen to cost, not by what its documentation promises.
- **What would answer it:** Reports by those it happened to: issues, post-mortems, maintainers' release notes that explain a retreat.
- **Where to look:** The issue trackers of Claude Code and of the frameworks named in card 8; maintainers' write-ups and release notes; discussion threads where a maintainer answers, cited to the maintainer's own words. Must turn up: a plugin update that did not reach users or reached them broken, a breaking change of Claude Code that frameworks had to follow.
- **Disconfirming query:** A search for reports that plugin distribution removed a class of upgrade trouble a framework had before; expected: some.
- **Stop rule:** Each of the three kinds of trouble has two or more first-hand reports or is recorded as not found; the opening budget.

#### Card 10: A stranger's first day under each candidate
- **Question:** What must a stranger arriving from GitHub do before the first prompt under each of the six candidates: what is cloned, what is installed and from where, what is registered or trusted, what must be on the machine, in how many steps and with which of them able to fail silently? What does he see in his project's repository afterwards: his own files alone, or the base's plumbing among them? How do published frameworks word this first step, and how long is it?
- **Why it matters:** The framework is public; a way that serves the author's update and loses the stranger at installation fails the perspective nobody else in the plan speaks for.
- **What would answer it:** The installation sections of published frameworks of each kind, read at source, and the vendor's documentation of installing a plugin and trusting a marketplace or a project.
- **Where to look:** The README and installation documentation of frameworks distributed as a plugin, as a global install, as a copy into the project and as a clone to work in; Anthropic's documentation of plugin installation, marketplace trust and project trust prompts. Must turn up: the exact steps of installing a plugin from a third-party marketplace, the prompts a first run shows.
- **Disconfirming query:** A search for reports of users failing at installation of a plugin-distributed framework; expected: some.
- **Stop rule:** Each candidate has a counted list of first-day steps from a primary source or from a framework of that kind; the opening budget.

#### Card 11: The cost of the cut, feature by feature
- **Question:** For every feature the brief places in the base (git through the scripts, the ledger and its upkeep, versioning and history, the ID scheme, isolated agents with their contracts, recipes and renders, sources and research with their indexes, threads, the walkthrough and its hook, `/save`, `/check`, `/setup`, `/test`, the instance facts): what in today's tree ties it to the forge's chain, by file and by the kind of tie (a name of an artefact written into a script, a rule in CLAUDE.md, a template, a test), and what would each of the six candidates require to be rebuilt before the feature could live in the base? Which features are cheap to cut, which dear, and which are better left in the forge or moved later? How do the development loop and the deployment loop run in today's tree, step by step, from a change of a script to a user who has it?
- **Why it matters:** Whatever the way of delivery, the split holds only if the mechanics can be parted from the chain; the principal weighs the cut feature by feature and may leave a feature in the forge.
- **What would answer it:** The repository's own files, read at source; no web.
- **Where to look:** The engine's tree from its root: `CLAUDE.md`, `.claude/skills/`, `.claude/agents/`, `.claude/settings.json`, `scripts/`, `templates/`, `tests/`; the brief `projects/forge/00-brief-engine-split.md`; the attached notes on the boundary by file and on the debt of the operating layer, checked against the tree as it stands, since both are older than it. This card is read from disk by the session model's agent alone: the agent reads these paths in the repository it runs in, cites files by their path relative to the repository root with line numbers, and opens no web page.
- **Disconfirming query:** A search of the tree for a feature the brief places in the base that names no artefact of the chain anywhere, against the expectation that every one does somewhere.
- **Stop rule:** Every feature of the list has its ties named by file, or "none found" with what was searched; the two loops are written step by step from the scripts and skills that run them.

### Output of the synthesis

For every candidate and every combination found: a description; what
it would mean for the forge; the development loop and the deployment
loop in it, step by step; its advantages and its disadvantages; a
score by the measures, the central update the heaviest and the cost
of the cut next, then the user's own things kept from an update, the
shared contract and the required version of the base, always-on
rules, scripts and templates delivered on three systems, the
stranger's first day, the migration of a project with a history, and
what Claude Code's own changes would do to it; and a recommendation.
The comparison of all of them stands side by side in one table. The
scores and the recommendation are Claude's judgement and stand in
Claude's view, marked as his; the facts they rest on stay in the
sections before it. The synthesis also lists what only a trial in
the tool can settle.

### Agents

One isolated agent per card per engine, none for a question another
card answers: eleven agents on the session model, and ten runs of
the second engine, `antigravity`, for cards 1 to 10. Card 11 is read
from the engine's own tree and goes to the session model alone: the
second engine's profile denies it the tree, and must. Every packet
carries the frame of the Cards section with its card. A second round
only for gaps the notes name, on the principal's word.

### The second engine's review of the draft

The review of `antigravity`, 2026-11-14, item by item, with what the
principal took of it:

- Missing, the upstream development loop: how the author edits and
  tries the base inside a layer without packaging, and how
  improvements return. Taken: a perspective of its own, widened by
  the principal with the deployment loop, and the rule that every
  candidate is judged by both.
- Missing, the migration of state when the base changes a schema.
  Taken: a perspective and card 7.
- Missing, the runtime and the permission boundary: where Python
  dependencies live, how prompts and the sandbox treat scripts
  outside the project. Taken into card 3.
- Missing, precedence across three tiers (base, layer, user). Taken
  into card 1.
- Assumption, that the documentation reflects the tool's behaviour;
  the answer lives in small trials against the tool. Taken in part:
  the cards read the issue tracker, the synthesis lists what only a
  trial settles, and trials are a later step on the principal's
  word, no card.
- Assumption, that a mature field of comparable frameworks exists;
  the precedents are in classic software (git's plumbing and
  porcelain, providers of infrastructure tools, editor packages).
  Taken in part: read for versions and release rhythm in card 6; the
  division as such is the note of 2026-10-03's.
- Assumption, that delivery is the bottleneck and not the internal
  coupling. Not taken as a change of the plan: card 11 stands for
  it, and the synthesis weighs the cost of the cut second only to
  the central update.
- A perspective without a card, the stranger from GitHub. Taken:
  card 10.
- A card to cut, the dependence on one harness. Taken: the card is
  cut, on the principal's word that the way is chosen for Claude
  Code.

## Deviations from the plan

- The session model's agents were given the path of their packet
  with the instruction to read it whole and nothing else, not the
  packet's text in the prompt. The content they received is the
  same.
- The notes are named `<NN-slug>.<engine>.md`. The independence
  measure of `scripts/forge-cite.py` looks for files named
  `card-*.md`, so it was run on copies under that name in the run
  folder; the skill and the script do not agree on the name of a
  note.
- A session agent's return reached the session as a hand-back
  message; each note was written to the hold folder from the
  agent's transcript by a helper script with the header's `engine`,
  `model`, `usage` and `run` filled, the text untouched.
- Seven notes of the second engine (cards 3 to 9) had dead
  citations, one of them a path of this machine in its Sources. On
  the principal's word of 2026-11-14 each went back once with its
  dead URLs named. `scripts/forge-engine.py` refuses to write over
  an existing note, so the seven were removed from the bundle before
  the second run; the first versions are kept in the run folder
  under `hold/first-run/`. The second run was made after the first
  engine's notes of those cards were filed, which the skill allows;
  its independence is the measure below.
- After the second run cards 3, 8 and 9 are clean; cards 4, 5, 6 and
  7 still cite pages that do not open and are filed as they are. The
  findings that rest on them are named under Completeness.
- The instance scan flags four lines in the two notes of card 3:
  sample Windows paths of the vendor's documentation with a made-up
  user name, no fact of this instance. Filed as they are.
- The two notes of cards 1 and 2 of the session model and the note
  of card 11 carry the template's comment under their title, as
  their agents returned it.

## Synthesis (2026-11-14)

### Completeness, card by card

| Card | Answered | Stop rule | Disconfirming query |
|---|---|---|---|
| 1 Composing | yes, but for one sub-question: by what name an agent of one package preloads a skill of another is not stated by the vendor (claude); stated as working by antigravity | met; opening budget | three closed issues on exactly these behaviours, none open read at source |
| 2 Always-on | yes, every candidate has a named mechanism | budget; second half of the rule untested | no memory file or rules in a plugin; found a forced output style, main conversation only |
| 3 Scripts and data | yes | met | many Windows reports; one contradicts the documentation on exec-form hooks |
| 4 Release by script | yes, four ways with a named project each; a plain copy script has no named project (claude) | met | one project gave the practice up (Symplify, claude); Yii and Rust's move off subtree (antigravity) |
| 5 Updating a copy | yes for four families; a declarative vendoring tool's treatment of a changed file not found | budget | four losses, all in tools that own whole files or blocks, none in tools that merge |
| 6 Release rhythm | yes | met | arguments against parallel lines and upper bounds, none against a minimum |
| 7 Data migration | yes, five mechanisms; skipped versions answered with a conflict named | met | tools with no migration exist; their price is a limit on change |
| 8 Field delivery | ten of eleven frameworks; Agent OS not checked | budget, slightly over | none of the eleven left plugins |
| 9 What failed | three of four kinds with two or more first-hand reports; a split taken back: nothing new | budget | moves to plugins found, no maintainer saying it removed upgrade trouble |
| 10 First day | yes, counted per candidate; candidate 3 from the vendor's pages alone | budget | silent plugin install failures, one open at the vendor |
| 11 Cost of the cut | yes, every feature by file; both loops written | met | found: several base features name no artefact |

Without support, since the page cited did not open in either run,
all in notes of the second engine: card 5, F1 (template updaters)
and F2 (vendoring by git) in part; card 6, F2 and F3 (how a
dependant declares a version, what happens on a mismatch) in part
and F5 (the plugin manifest has no host-version field); card 7, F1
to F4 in part; card 4, the reference documentation of `git subtree`
as cited there. Card 6's F5 is also contradicted by the first
engine's reading of the changelog. Where the first engine's note of
the same card makes the point from a page that opens, the point
stands on that note.

Nearly every web page was read through a summarising fetch; the
notes say so. A quotation is to be checked at its URL before it is
quoted onward.

### Answers side by side

**Independence.** By `forge-cite.py --independence` after the second
run: nine of ten cards independent (shared URLs 0 to 3, identical
sentences 0 to 9 of about a hundred). Card 8 is marked dependent by
its sources, 9 URLs shared of 12, with 2 identical sentences of 109:
the card names the eleven repositories to read, so both engines read
the same pages; it counts as one set of sources read twice, not as
one text copied.

**Card 1.** Both: plugins with `dependencies` and ranges resolved
against git tags are the only mechanism of Claude Code that carries
a required version and names a failure; every plugin component is
namespaced; hooks have no names and all fire; skills and agents
outside plugins collide in opposite directions. *Differ:*
antigravity states that an agent preloads another package's skill by
`plugin:skill`; claude read the subagents page and found bare names
only, the cross-package name not stated, an old report of it failing
in both forms, and a missing skill skipped with a debug-log line
only. Antigravity read the changelog to 2.1.311 and proposes a
blocking hook as the stronger enforcement; claude read to 2.1.325
and found `engines["claude-code"]` added and the plugin `agent`
setting deprecated on 2026-11-12.

**Card 2.** Both: no memory file and no rules directory in a plugin;
a `SessionStart` hook is capped at 10,000 characters and does run
again after compaction; an import that leaves the working directory
needs an approval whose refusal is silent and permanent; a custom
subagent loads the memory hierarchy. *Differ:* antigravity concludes
the plugin must be rejected and only candidates 1 and 6 deliver;
claude rules no candidate out, adds the forced output style and the
`SubagentStart` hook as partial channels, and leaves standing one
combination: text in the tree, hooks in a plugin.

**Card 3.** Both: the plugin root variable is substituted only in a
plugin's own components; a plugin's `bin/` on PATH is the bridge to
a project's skill; no Python dependency is installed by Claude Code;
native Windows has no sandbox; hooks with the root variable fail on
Windows in reports through 2026. *Differ:* antigravity recommends
candidate 6 with the base vendored into each project and `uv run`;
claude recommends a plugin with `bin/`, developed in place in the
framework's repository, and finds `--add-dir` now loads subagents.

**Card 4.** Both: a history split (`git subtree split`,
`splitsh-lite`), a bot with rules, a copy-and-transform tool, a
two-way sync; published repositories are read-only and pull requests
are sent back to the source. *Differ:* antigravity recommends a
plain copy-and-commit script with a manifest and one commit per
release; claude found no named project that publishes so, and names
Laravel's two shell scripts over `splitsh-lite` as the nearest
shape, with the condition that the part is a directory or a few.

**Card 5.** Both: template updaters replay the user's diff; git
merges; manifest installers own whole files; marker blocks own lines
of a shared file; losses happen at the edges (a retired file, a
forced overwrite, two writers of one path). Both recommend ownership
by path: the base's files never edited by the user, the user's in
paths the base never ships, a marker block for the one shared file.
*Differ:* claude adds that under that rule a plain pull by git is
enough wherever the project is a clone of the base; antigravity
adds that three-way updaters break when the source's history is
rewritten.

**Card 6.** Both: one line, a minimum version and no upper bound,
no parallel maintained branches for one maintainer; a stable line is
a delayed pointer on the same history. *Differ:* on the mismatch,
claude and antigravity's second note both say refuse (antigravity's
first said warn); on the host, see card 1.

**Card 7.** Both: a version stamp in the project and a chain of
migrations between the recorded version and the new one, repeatable,
is the mechanism that carries a project that slept through several
releases; reading old and new shapes side by side is rejected for a
tool with several readers. Claude adds that the nearest frameworks
avoid the problem by never parsing the user's documents, which is
not the forge's case.

**Card 8.** Both: nobody left plugins; nobody changed architecture
wholesale since August; copying into the project still forces
manifests and migration apparatus. *Differ:* claude reports BMAD
leaving its own installer for a generic skills package manager in
its v7 preview and that manager appearing at three of the eleven;
antigravity reports servers of the Model Context Protocol as a
rising channel and recommends candidate 6 with marker blocks, no
plugin.

**Card 9.** Both: a plugin update that does not reach the user, a
stale cache; user content lost at an update in Spec Kit; the two
known retreats from a split and nothing new. *Differ:* antigravity
concludes "do not distribute the base as a plugin" and "monolith
first, extract by script at release"; claude concludes the plugin is
neither to be dropped nor to be trusted alone, and adds that Claude
Code changed nested skill loading inside plugin folders twice in
November.

**Card 10.** Both: a clone costs a clone, a start and one trust
dialog; a plugin leaves the repository clean and has a documented
silent install failure; an import across repositories is the worst
first day. *Differ:* antigravity ranks the plugin first for the
stranger; claude ranks the clone first and finds a plugin directory
inside the repository loading in place for whoever clones it.

**Card 11.** One engine. Most base features name no artefact of the
chain; the ledger, the light check's program and `CLAUDE.md` are the
dear part; four ties run across everything (citations of the forge's
own project by ID, citations of `CLAUDE.md` by section, one root,
the version number borrowed from the forge intent).

### Unexpected, gathered

Finds that reconfigure a question or bring a mechanism:

- The base without the chain already runs in the tree as the
  `library` kind; a project on the base could be a further kind
  (card 11).
- A plugin directory under the repository's own `.claude/skills/`
  loads in place for whoever clones and trusts the folder, and the
  same directory could be listed in a marketplace: candidates 1 and 4
  at once, unverified for the publishing side (cards 3, 10).
- The always-on text and the executable parts need not travel
  together: text in the tree, hooks and scripts by another carrier
  (card 2).
- A pull of the engine delivers the head of `main`, eleven commits
  past the last release on the day; the engine's version number is
  the forge intent's (card 11).
- For a plugin the user's machine decides whether an update is
  received, by a version string and a cached clone; the problem of
  "how often a user is forced" may be the opposite one (card 9).
- A user's own untracked file in the clone stops `forge-pull`, read
  from the code and not tried (card 11).
- The published base is where strangers arrive; the one account of
  leaving split repositories is about contributions refused there
  (card 4).
- A generic skills package manager and servers of the Model Context
  Protocol as carriers the candidates do not name; the first carries
  skills only (card 8).
- The plugin `agent` setting deprecated; `engines["claude-code"]`
  added; nested `.claude/skills` loading narrowed three times
  between 2026-11-06 and 2026-11-13 (cards 1, 2, 9).
- A blocking hook as a stronger gate than a preloaded contract
  (card 1, antigravity).

Finds that add a source to a point already made: no sandbox on
native Windows; `--add-dir` loads subagents now; the 32-skill
preload limit; Copier's two-stage migrations; Terraform's serial and
lineage; file retirement as the dangerous part of an installer.

### Not found, gathered

- A vendor statement of the name under which a plugin's skill is
  preloaded by another package's agent.
- Whether a plugin directory in the repository satisfies another
  plugin's dependency entry, and whether a forced output style works
  for it.
- What happens to an external import in a session with no dialog.
- A named project that publishes a part of its repository by a plain
  copy script, and any practice for a part spread over several
  top-level directories.
- BMAD's reason for leaving its installer; any published comparison
  of the ways of distribution.
- A maintainer saying that a move to plugins removed upgrade
  trouble; any vendor answer or fixed version for the stale plugin
  cache; a fixed version for the Windows hook path failures.
- Any figure: how often updates fail, how many users were affected,
  what a split or a kept old shape costs.
- In the tree: any declaration of a base version or of a minimum a
  layer needs; any test of an instruction.

### Claude's view

Everything in this section is Claude's own judgement on the notes
above; the scores are a judgement, not a measurement.

**The measures and their weights.** The central update counts three
times, the cost of the cut twice, the rest once: the development
loop, the user's own things kept from an update, the shared contract
with a required version, always-on rules, scripts and templates on
three systems, the stranger's first day, the migration of a project
with a history, and exposure to Claude Code's own changes. Each from
1 (worst) to 5; the most is 65.

| | Update ×3 | Cut ×2 | Dev loop | Own things | Contract, version | Always-on | Scripts | First day | Migration | Claude Code changes | Sum |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 One repository, layers as directories | 5 | 5 | 5 | 3 | 3 | 5 | 5 | 4 | 4 | 4 | 58 |
| 6 The whole kept, the base released apart by a script | 5 | 4 | 5 | 3 | 3 | 5 | 5 | 4 | 4 | 4 | 56 |
| 6 with the released base in the form of a plugin | 3 | 3 | 4 | 4 | 4 | 2 | 3 | 3 | 3 | 2 | 40 |
| 4 with the rule text in the tree, a plugin for the executables | 3 | 2 | 3 | 5 | 4 | 4 | 3 | 3 | 3 | 2 | 40 |
| 3 Two repositories joined by an import | 4 | 2 | 4 | 4 | 2 | 2 | 2 | 1 | 3 | 3 | 37 |
| 2 The base a package, each layer a repository | 3 | 2 | 2 | 4 | 3 | 2 | 3 | 3 | 3 | 3 | 36 |
| 4 A plugin alone | 2 | 2 | 3 | 5 | 3 | 1 | 3 | 3 | 3 | 1 | 32 |
| 5 User-level configuration and imports | 2 | 2 | 3 | 2 | 2 | 4 | 2 | 3 | 2 | 3 | 31 |

**Candidate 1, one repository with the layers as directories.**
*What it is:* the repository stays one; what is base and what is the
forge layer is marked in it, by directories or by a manifest of
paths; a project that is not the forge lives under `projects/` of a
clone of the whole as a further kind of project, as a library does
today. *What it means for the forge:* nothing of the root moves; the
cheap group of card 11 is renamed where it says `forge`, the ledger
and the light check stay in the layer. *Development loop:* edit,
`/test`, try on any project, `/save`; unchanged. *Deployment loop:*
`/release`, the user's `/pull`, the Action required lines,
`/migrate`; unchanged, and it reaches every project in every clone.
*For:* the central update exists today and is proven; the cheapest
cut; every always-on rule, hook and script arrives as now; one trust
dialog on the first day. *Against:* the base is not a thing of its
own; a project that is not the forge carries the forge layer and
its commands; a second layer by someone else has no place but this
repository; a user's own agents need a place the pull does not look
at.

**Candidate 6, the whole kept and the base released apart by a
script.** *What it is:* candidate 1, plus a release step that writes
the files a manifest names as base into a public repository of its
own, tagged; a project that is not the forge lives in a clone of
that repository and pulls it. *What it means:* a manifest of which
file is base; for each mixed file the work of card 11 done first or
the file left out of the base; `CLAUDE.md` divided so that the
base's half stands alone; a README and a contributing file in the
published repository that send strangers to the source.
*Development loop:* unchanged, in the whole. *Deployment loop:* the
forge as today; the base by the release script, then the user's
pull of the base's repository, the same pull as today. *For:* the
key property with a base of its own; established practice; the
released base is the first real test of the boundary; nothing of
Claude Code's packaging is leaned on. *Against:* two public
repositories and a read-only one that will still receive pull
requests; the forge is not installed on the base, it contains it, so
the layering is shown outward and not used inward; whether history
is split or one commit per release is made has to be chosen, and the
plain copy has no named precedent; the release grows by a step.

**Candidate 6 with the released base in the form of a plugin.**
*What it is:* the release script writes the base as a plugin with a
marketplace entry. *For:* a version range between a layer and the
base, checked by the harness; nothing of the base in a project's
tree. *Against:* the rule text still has to be written into every
project; the recorded troubles of the plugin deployment; the
contract preload across packages unverified; hooks on Windows.

**Candidate 4 with the rule text in the tree.** *What it is:* a
plugin carries skills, agents, hooks and scripts; its setup writes
the base's rule files and one import line into the project. *For:*
the one combination in which an update writes into no file the user
or a layer owns but the base's own rule files. *Against:* two things
kept in step, the plugin's version and the copied text; every script
call by a relative path rewritten; the plugin deployment's troubles
as above.

**Candidate 3, two repositories joined by an import.** *For:* the
git scripts already save a pair side by side. *Against:* a dialog on
the stranger's first run whose refusal is silent and permanent; the
sibling's hooks and settings do not load; no variable names the
sibling's path.

**Candidate 2, the base a package and each layer a repository.**
*For:* the cleanest picture. *Against:* it has no carrier of its own
in Claude Code and resolves into 3, 4 or a copy; the full split of
the root; the field's two retreats were from this shape.

**Candidate 4, a plugin alone.** *For:* the clean repository and the
version range. *Against:* no channel that delivers the rules to the
session and the reviewers alike; the worst recorded deployment; the
ground moved three times in a week.

**Candidate 5, user-level configuration.** *For:* no dialog.
*Against:* one base per machine for every project, no update
channel, collisions that replace silently.

**Recommendation.** Take candidate 1 now and candidate 6 as the step
after it, and leave the plugin until Claude Code can carry rules in
one (the vendor's open request) or a trial shows the contract
crossing packages.

1. In the present repository, mark the base: a manifest of paths,
   the literals `forge`, `intent` and `brief` of the cheap group
   replaced by what a project declares, and a kind of project
   without a chain that is not a library. From that day every
   project of the principal's that is not the forge has the base
   with the central update, through the pull that exists. This is
   chosen against waiting for the split to deliver it.
2. Settle what every candidate needs and the tree lacks: a version
   number of the base that is its own; a minimum base version a
   project or a layer declares, checked by a script that refuses a
   write and names the one command that updates; a pointer to the
   last release that `/pull` follows by default, so that a user is
   moved release by release and not commit by commit; a place for a
   user's own things that the pull does not look at; a rule that the
   base and a layer never write one path.
3. Then the release script of candidate 6, driven by the same
   manifest, publishing the base to its own repository, read-only,
   with the redirect said plainly.

It rests on cards 2, 3, 9 and 11 for the plugin's limits and the
cost of the cut, on card 4 for the release script, on cards 5, 6
and 7 for step 2. It is chosen against the plugin now (cards 1, 2,
9) and against the split into two working repositories (card 9's
retreats, card 11's root). It is a hypothesis in two places: that a
further kind of project is enough for the principal's own projects,
which no note tested, and that a base published by a plain copy by
manifest holds up, which has no named precedent.

**What only a trial in the tool can settle**, each small, proposed
as a step of its own:

- Whether an agent of one package preloads the contract skill of
  another, by which name, from a project agent and from a plugin
  agent.
- Whether a plugin directory under `.claude/skills/` with a `bin/`
  serves the base's scripts to project skills on Windows, and
  whether its hooks run there in exec form.
- Whether a user's untracked agent in the clone stops `forge-pull`.
- Whether a forced output style and a `SubagentStart` hook together
  carry the rules to session and reviewers.

**Proposed for the chain**, through `/forge brief engine-split`,
never silently: the open point "the three ways the base could reach
a layer" answered by this comparison; the order of the brief's steps
checked against step 1 to 3 above; the two new matters, the base's
own version and what a pull delivers, taken into the brief. The
further kind of project is the matter of the thread on a third kind
of project (THR.0750).

## Notes

The files of the bundle, each made from the packet folder of its
card under `tmp/research/2026-11-14-anvil-carrying-layers/`:

- `01-composing.claude.md`, `01-composing.antigravity.md`: folder
  `01-composing`.
- `02-always-on.claude.md`, `02-always-on.antigravity.md`: folder
  `02-always-on`.
- `03-scripts-and-data.claude.md`,
  `03-scripts-and-data.antigravity.md` (second run): folder
  `03-scripts-and-data`.
- `04-release-by-script.claude.md`,
  `04-release-by-script.antigravity.md` (second run): folder
  `04-release-by-script`.
- `05-updating-a-copy.claude.md`,
  `05-updating-a-copy.antigravity.md` (second run): folder
  `05-updating-a-copy`.
- `06-release-rhythm.claude.md`,
  `06-release-rhythm.antigravity.md` (second run): folder
  `06-release-rhythm`.
- `07-data-migration.claude.md`,
  `07-data-migration.antigravity.md` (second run): folder
  `07-data-migration`.
- `08-field-delivery.claude.md`,
  `08-field-delivery.antigravity.md` (second run): folder
  `08-field-delivery`.
- `09-what-failed.claude.md`, `09-what-failed.antigravity.md`
  (second run): folder `09-what-failed`.
- `10-first-day.claude.md`, `10-first-day.antigravity.md`: folder
  `10-first-day`.
- `11-cost-of-the-cut.claude.md`: folder `11-cost-of-the-cut`; the
  session model alone, read from the engine's tree.
