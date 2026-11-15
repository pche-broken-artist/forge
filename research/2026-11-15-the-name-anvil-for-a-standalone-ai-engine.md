---
date: 2026-11-15
project: forge
topic: carriers of the names Anvil, Hearth and Incus among developer and AI tools
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-15-the-name-anvil-for-a-standalone-ai-engine/card-1
derived_from: the principal's word of 2026-11-15 (a quick research of one card, no plan file, the card as he confirmed it that day); web sources below
---

# The name Anvil is already carried in the field of agent tooling for Claude Code; Hearth is carried there too, and Incus belongs to a container manager

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

By the card's own test the name Anvil does not stand. The
disconfirming query found what it looked for: on 2026-11-15 GitHub
holds at least fifteen public repositories named exactly `anvil` that
are tools for AI coding agents, nine of which name Claude Code (one
of them: Claude) in their own text, and several describe themselves
in the words of this project, a framework, an engine, a harness or an
orchestrator for Claude Code, one of them installing skills,
subagents and hooks [1][2][15][16]. All are small (the two largest,
154 and 89 stars, are an agent for another CLI and a desktop IDE; the
ones for Claude Code have 0 to 2 stars) and nearly all were created
since February 2026. Outside AI, Anvil is among the most reused names
of developer tools (4,917 repositories carry it in their name) [2].
Hearth is carried in the same field as well, by seven small
exact-name tools for Claude Code or coding agents, in another sense,
a home for sessions [3]. Incus is carried by no agent tool, but
belongs to one dominant project, a container and virtual machine
manager with 6,644 stars, which is itself used as the sandbox for
Claude Code [5][6]. The bare name is taken on PyPI and on npm for all
three [7]-[12]; none of the three appears in Anthropic's official
plugin marketplace of 317 plugins [13]. Carriers tell themselves
apart by a namespace and by a compound; a qualifier appears only in
prose. How sure: that the carriers exist is as sure as the
registries' own records; every count is a floor, since the listings
were read from the top and not to the end. The one unexpected thing:
not the word alone but the whole smithy vocabulary (forge, foundry,
anvil, bellows, temper, crucible) is already in use among tools for
Claude Code [1].

## Question

The frame of the card:

> An open-source framework built on Claude Code (Anthropic's agent for
> the command line) is being divided into parts. Its general part,
> the mechanics that any such framework needs alike (git through
> scripts, a ledger of state, versioning and history of documents,
> isolated reviewer agents, recipes and renders, research), is to
> become a standalone public open-source project of its own: an "AI
> engine" that runs on Claude Code as skills, agents, hooks and Python
> scripts, on which frameworks are then built. The frameworks carry
> names from the smithy ("Forge of Thought" is the first), and the
> working name of the engine is Anvil, the solid thing under every
> piece of work in a forge. Two alternatives from the same workshop
> are Hearth and Incus (Latin for anvil). The public repository of
> Forge of Thought already mentions Anvil as a working name in its
> README; that mention is the project's own and is not a collision.

The card, verbatim:

#### Card 1: does the name Anvil stand for a standalone public project
- **Question:** What already carries the name Anvil among public tools for developers and for AI, and how near is each carrier to the field of this project, an open-source AI engine that runs on Claude Code (skills, agents, hooks and scripts)? The same for the alternatives Hearth and Incus. And how do carriers of one word tell themselves apart: by a qualifier, a compound, or a namespace?
- **Why it matters:** the name of a standalone project must be findable, registrable and told apart; a name already carried in the same field is not taken.
- **What would answer it:** for each of the three names, the list of existing projects and products with what each is, shown by their own pages; and the state of the name in the places a project is found and registered.
- **Where to look:** GitHub; the package registries PyPI and npm; the listings of plugins for Claude Code; the own sites of the products found.
- **Disconfirming query:** expected: Anvil is carried by several developer tools and by none in the field of agent frameworks for Claude Code. The query looks for exactly such a project, an agent framework, a plugin or a skill set for Claude Code or for AI coding agents named Anvil; if one exists, the name falls.
- **Stop rule:** nothing new from a differently worded query, and each of the three names has its carriers read on their own pages; about ten to fifteen pages opened.

Left out on purpose, not to be pursued: trademark registers and the
availability of domains.

The baseline the note must beat is the card's own expectation, which
is also what a first look at a search engine suggests: Anvil is a
name of several well-known developer tools in other fields, and
nobody in the field of Claude Code carries it. A note that only
repeats the well-known carriers adds nothing; it has to read the
registries themselves, for the field and for each of the three names.

## Key findings

**F1. At least fifteen public repositories named exactly `anvil` are
tools for AI coding agents; nine of them name Claude Code, or Claude,
in their own text.** [single source per carrier: GitHub's own
repository record, primary, each description the owner's own text;
two confirmed on the repository page; figures of 2026-11-15] Twelve
come from the search `anvil claude` [1], two from the search of
repositories with `anvil` in the name [2], one from a README [16].
The quotes stand in the `description` field of each record unless
said otherwise.

| Repository | Stars | Created | What it says it is | Nearness | Source |
|---|---|---|---|---|---|
| burkeholland/anvil | 154 | 2026-02-21 | "Evidence-first coding agent for GitHub Copilot CLI" | same field, another host CLI | [2] |
| zdenham/anvil | 89 | 2026-03-25 | "IDE for parallel agent work." | same field, a desktop IDE | [2] |
| esanmohammad/Anvil | 20 | 2026-04-17 | "Provider-agnostic AI dev pipeline" | same field, own pipeline | [1] |
| s0up4200/anvil | 2 | 2026-04-03 | "A desktop skills.sh client. Search, install, and manage skills across Claude Code, Codex, and 40+ other agents." | same field, skills for Claude Code | [1] |
| mulkatz/anvil | 1 | 2026-02-19 | "Adversarial thinking plugin for Claude Code. Stress-test ideas through structured debates." | same host, a plugin | [1][15] |
| parthreddyprojects/anvil | 1 | 2026-04-01 | "Strategic problem-solving engine for Claude Code." | same host, same word "engine" | [1] |
| belchman/Anvil | 1 | 2026-02-23 | "Anvil is a portable autonomous pipeline framework for Claude Code." | same host, same kind | [1] |
| ai-nhancement/Anvil | 1 | 2026-05-25 | "Anvil is a single, self-contained AI coding agent for the terminal." | same field | [1] |
| Huzy85/anvil | 1 | 2026-04-01 | "Two-model coding pipeline built on aider" | same field | [1] |
| martex-dev/anvil | 1 | 2026-09-25 | "Anvil: an AI code editor for quant, trading, crypto, ML and data work." | same field, an editor | [1] |
| yoriichiee/anvil | 1 | 2026-10-25 | "Works with Claude Code, Codex, any API key, or no AI." | same field, checks of AI-built apps | [1] |
| hchava/anvil | 0 | 2026-05-27 | "Evidence-gated AI agent harness for reliable Claude Code + Codex engineering workflows." | same host, same kind | [1] |
| juvilan/anvil | 0 | 2026-03-24 | "Anvil — Claude Code orchestrator combining GSD concepts with forge quality system" | same host, same kind | [1] |
| tacoda/anvil | 0 | 2026-07-17 | "A copy-and-fill template library for setting up Claude in any project." | same host | [1] |
| chonalchendo/anvil | 0 | not on the page | README: "A context management and workflow tool for agentic software development." | same host, same kind | [16] |

The count is a floor: [1] returned 73 repositories and the first 40
were read (the list is sorted by stars and had reached zero stars, so
the 33 unread have none); [2] returned 4,917 and the first 40 were
read, the last of them with 61 stars, so a tool for AI agents named
`anvil` that has fewer stars and does not say "claude" was seen by
neither search.

**F2. The nearest carriers describe the very thing this project is:
mechanics installed into Claude Code as skills, agents and hooks.**
[single source per carrier: its own description or README; the two
READMEs read through a summarising fetch] chonalchendo/anvil installs
skills to `~/.claude/skills` and subagents to `~/.claude/agents` and
registers SessionStart, PreCompact and SessionEnd hooks; its README
says "Hooks are Claude Code only." and, of its state, "**Status:**
alpha, unreleased." [16] (summarised fetch). mulkatz/anvil ships
commands, a Stop hook and scripts as a plugin, installed with
`/plugin install anvil@mulkatz` and invoked as `/anvil:anvil` [15]
(summarised fetch; its description also read raw in [1]). belchman,
hchava, juvilan and parthreddyprojects use the words "framework",
"harness", "orchestrator" and "engine" for Claude Code in their
descriptions [1]. None of them has traction by stars (0 to 1).

**F3. Around the exact name stands a ring of compounds in the same
field, and the existing Anvil products already have Claude Code
skills of their own.** [single source: GitHub's repository records
[1], 2026-11-15] Compounds: zawatton/anvil.el (90 stars, "An MCP
server written in Elisp — a token-efficient workbench for AI
agents."), allut/claude-anvil (3, "Evidence-first coding agent for
Claude Code CLI. Port of burkeholland/anvil from GitHub Copilot
CLI."), queelius/claude-anvil (2, "A forge for Claude Code plugins"),
two more repositories named `claude-anvil` without a description,
Alexanderdunlop/anvil-skills (2, "Claude Code skills that learn from
your corrections."), superduke/ganvil (3, "A Claude Code plugin."),
LioraRndr/SkillAnvil, czydyq/AnvilCode, the marketplace
urda-anvil/claude-plugins, and the organisation Anvil-Code, whose two
tools for SKILL.md files sign as "by Anvil & Code". Two plugin
collections carry a plugin named anvil inside them:
samuel-stidham/smithy ("anvil manages Nix environments") and
BananaSpaGetti/claude-skills ("anvil and anvil2 — interview, plan,
then execute through subagents"). Skills for products already named
Anvil: anvilco/anvil-plugins ("Claude code skill for Anvil") and
matshoppenbrouwers/anvil-uplink-cli ("A terminal bridge to Anvil apps
via the Server Uplink.", topics `claude-code`, `codex`). The words
"Anvil skill for Claude Code" therefore already point three ways.

**F4. Outside AI, Anvil is one of the most reused names among
developer tools.** [consensus of the registry record and the
carriers' own pages; 2026-11-15] 4,917 repositories on GitHub carry
`anvil` in their name [2]. The carriers with the most stars, each in
its own words: anvil-ui/anvil (1,438, "Minimal UI library for Android
inspired by React"), square/anvil (1,403, "A Kotlin compiler plugin
to make dependency injection with Dagger 2 easier."),
anvil-works/anvil-runtime (1,024, "The runtime engine for hosting
Anvil web apps"), GPUOpen-Archive/Anvil (611, "Anvil is a
cross-platform framework for Vulkan"), matter-labs/anvil-zksync
(309), anvil-verifier/anvil (253, a framework for formally verified
cluster controllers), anviljs/anvil.js (146, "A Convention over
Configuration Build System"), 0xjuanma/anvil (119, a CLI installing
a developer's tool-chain) [2]. The local Ethereum node of the Foundry
toolkit is named Anvil and started by the command `anvil`: "Anvil is
a fast local Ethereum node for development and testing." (under the
heading "Anvil") [14] (summarised fetch); a wrapper names it "Foundry
Anvil" [2]. All of these are far from the field of this project; what
they share with it is the audience, developers, and the search word.

**F5. The bare name is taken on PyPI and on npm for all three
names.** [single source per name: the registry's own record, primary,
read raw; dates are the registries' structured data]

| Registry | Name | Holder's summary | Dates | Source |
|---|---|---|---|---|
| PyPI | anvil | "Provider-aware cloud task runner for schema v2 multi-cloud targets", version 0.37.0 | 14 releases, uploads 2026-07-30 to 2026-11-14: active | [7] |
| PyPI | hearth | "a collection tools and extensions for working with pytorch", version 0.5.0 | 6 releases, 2021-12-18 to 2022-04-24: dormant | [8] |
| PyPI | incus | "Acoustic FDTD Simulator", version 0.0 | one upload, 2023-02-15: dormant | [9] |
| npm | anvil | "Anvil is a library of useful interactive tools.", 0.0.6 | created 2018-11-22, record modified 2022-04-11 | [10] |
| npm | hearth | "Stupid simple json test data stream generator", 1.0.2 | created 2014-12-04, record modified 2022-06-18 | [11] |
| npm | incus | no description; repository js-incus, 1.0.8 | created and modified 2023-11-08 | [12] |

A project that wants a package on either registry needs another name
under any of the three words.

**F6. None of the three names is in Anthropic's official plugin
marketplace.** [single source: the marketplace file itself, primary,
read in full by a script; undated, as served on 2026-11-15] The file
lists 317 plugins; none has `anvil`, `hearth` or `incus` in any field
[13]. The in-field carriers of F1 to F3 live in their owners' own
marketplaces and repositories.

**F7. Hearth is carried in the same field too, by small and recent
tools, in another sense: a home for sessions.** [single source per
carrier: GitHub's repository records [3][4]; 2026-11-15] The search
`hearth claude` returned 43 repositories; the first 30 were read [3].
Seven are named exactly `hearth` and are tools for Claude Code or
coding agents, none above 8 stars, all created between June and
November 2026: skeletor-js/Hearth (8, "A self-evolving macOS desktop
client for coding agents (Claude Code, Codex) over ACP."),
zmilojevic/hearth (1, "Keep your Claude Code sessions warm."),
emmaweg/hearth (1, "Small, honest tools for running a fleet of Claude
Code agents in tmux"), promilek2/hearth (1, "A local-first coding
agent for VS Code"), spezzuti/Hearth (0, "A Windows-first, local
desktop home for Claude Code work, project review, agents, and
continuity."), BobStrogg/hearth (0) and veelvoer/hearth (0). Compounds
in the field: alexandr352/hearthwork (6, "A plan → execute → judge
loop for Claude Code"), BorisNikolic/hearthvault (4, memory for Claude
Code), c0reyx/hearthkit, TheColliery/CoalHearth,
ChristopherAparicio/AgentHearth, hearth-project/hearth-cli (1, "A
portable workspace for coding agents"), and a pack named hearth in
revenantworks/claude-skills. No framework or engine named Hearth with
traction was found. Outside the field, 8,340 repositories carry
`hearth` in their name, the top of the list being tools for the game
Hearthstone; the carriers of the bare word are rudra-avatar/Hearth
(368, a home screen for LG webOS TVs), THORCollective/HEARTH (363, a
repository of threat hunting), ondreu/Hearth (237, a homepage for
Obsidian), kubuszok/hearth (166, "The first Scala macros' standard
library") and aheart/hearth (97, server monitoring) [4].

**F8. Incus is carried by no agent tool, and belongs to one dominant
project that stands next to this field.** [consensus of the registry
records [5][6]; 2026-11-15] 673 repositories carry `incus` in their
name; the first is lxc/incus (6,644 stars, "Powerful system container
and virtual machine manager"), and nearly all the rest of the 25 read
are its ecosystem: lxc/incus-os (1,204), zabbly/incus (573),
lxc/terraform-provider-incus (231), incus-deploy, incus-compose,
incus-ui. One older unrelated carrier stands among them: Imgur/incus
(360, "incus is a middleware for distributing messages via
websockets, long polling, and push notifications") [6]. The search
`incus claude` returned 15 repositories, all read, and every one is
about running Claude Code or other coding agents inside Incus
containers or virtual machines, none a framework named Incus:
coipond/coi (787 stars, "Each AI coding agent gets its own isolated
machine"), bketelsen/clincus ("Secure container runtime for AI coding
tools on Incus"), mathijs81/inca, pood0g/InClaudeUs ("A hardened,
ephemeral Incus container for running Claude Code."),
NandorKovacs/incus-claude, phuesler/agent-sandbox [5]; and
Sanne/incus-spawn (54, "Give your AI coding agents their own
machines") [6]. In this field the word already means the sandbox the
agent runs in.

**F9. Carriers of one word tell themselves apart by a namespace and
by a compound; a qualifier appears only in prose.** [the agent's
reading of the listings [1]-[6] and of [15]; practitioner practice,
not a stated rule]
- *Namespace.* On GitHub the owner is the namespace: the fifteen
  repositories of F1 are all `<owner>/anvil`, and the carriers with
  traction sit under an organisation that carries the word
  (`anvil-works`, `anvil-ui`, `anviljs`, `anvil-verifier`,
  `Anvil-Code`, `hearth-project`, `lxc`) [1][2][3][6]. The account
  `Anvil` itself is taken [2]. In Claude Code a plugin is told apart
  at installation by its marketplace, `anvil@mulkatz`, and its
  commands carry the plugin's name as a prefix, `/anvil:anvil` [15].
- *Compound.* The word joined to its host or its function:
  `claude-anvil`, `anvil-skills`, `anvil.el`, `anvil.js`,
  `anvil-zksync`, `kotlin-inject-anvil`, `TLS-Anvil`, `kernel-anvil`;
  `hearthwork`, `hearthvault`, `hearthkit`, `hearth-cli`,
  `AgentHearth`; `incus-os`, `incus-compose`, `incus-spawn`, `clincus`
  [1]-[6]. On the registries the bare word has one holder (F5), so a
  later carrier has only this way.
- *Qualifier.* The family or the publisher said before the word, in
  running text only: "Foundry Anvil", "Anvil web apps", "Anvil &
  Code", "Urda Anvil" [1][2]. No carrier relies on the bare word
  alone to be found.

No two sources disagreed on anything the card asks.

## Unexpected

The whole smithy is in use, not the one word. The card's frame takes
the workshop vocabulary as what marks this family of frameworks; [1]
shows the same figure in several unrelated tools for Claude Code:
queelius/claude-anvil is "A forge for Claude Code plugins";
samuel-stidham/smithy is a marketplace of six plugins named forge,
foundry, draft, anvil, bellows and temper ("forge runs the
engineering workflow: tasks, proofs, reviews, PRs, releases");
lorenzofamiglini/The-Forge-Protocol-Agent has "Four modes: Forge,
Anvil, Crucible, Executor"; juvilan/anvil combines "GSD concepts with
forge quality system"; rjwalters/repo describes its skills as
"installed per-repo like Anvil and Loom". A lead: another word from
the same workshop may meet the same crowd, and the pair "forge" with
"anvil" is not this project's alone.

The pair Forge and Anvil may already belong to one toolkit. Verified
in this run: Anvil is the local Ethereum node published on the
Foundry site, started by `anvil` [14], and others call it "Foundry
Anvil" [2]. Not verified in this run, the agent's own recollection
only: the same toolkit's command for building and testing is named
`forge`. If that holds, a search for "forge anvil" leads to that
toolkit first. A lead to be checked on the toolkit's own page, not a
finding.

The name is being taken fast. Fact: of the fifteen repositories of
F1, fourteen carry a creation date, and all fourteen fall between
2026-02-19 and 2026-10-25 [1][2]; the seven of F7 between 2026-06-02
and 2026-10-24 [3]. Speculation: at that rate more carriers of both
words could appear before this project is public, whichever of the
two it took.

## Not found

- No plugin named Anvil, Hearth or Incus in Anthropic's official
  marketplace (317 plugins searched in every field) [13].
- No agent framework, plugin or skill set named Incus: two web
  queries and the two GitHub searches [5][6] returned only tools that
  run agents inside Incus containers.
- No carrier of Anvil in the field with traction: the largest is an
  agent for another CLI with 154 stars [2]; nothing for Claude Code
  above 2 stars under the exact name [1].
- No framework or engine named Hearth with traction; the largest
  exact-name carrier in the field has 8 stars [3].
- Not looked at, the openings being spent: the third-party
  directories of plugins and skills for Claude Code (several appeared
  in result lists with entries named anvil and hearth; they are
  aggregators of others' repositories and were not opened); the 33
  results of [1] and the 13 of [3] beyond those read; whether the
  GitHub account names `hearth` and `incus` are free; scoped names on
  npm; the own site of the Python web-app platform Anvil, which
  appears here only through its runtime's description on GitHub [2];
  the own site of Incus, which appears only through its repository's
  description [6].
- No source was looked for on what Claude Code does when two
  installed plugins from different marketplaces share the name
  `anvil` and so the command prefix `/anvil:`.
- Trademark registers and domains: left out by the card.

## Options

1. **Anvil, bare.** Against it: it falls by the card's own test (F1,
   F2); the bare name is taken on PyPI by an active project and on
   npm (F5); a plugin named `anvil` shares its command prefix with
   existing plugins (F2). For it: no carrier in the field has
   traction, so nobody would be displaced.
2. **Anvil in a compound or with a qualifier.** The way every carrier
   with traction goes (F9). The compound then carries all of the
   findability and registrability; in speech the bare word still
   points at fifteen tools of the same field and at the well-known
   carriers of F4.
3. **Hearth.** Carried in the field by seven small tools in the sense
   of a home for sessions (F7), which is not the sense of this
   project; the bare registry names are held by dormant packages
   (F5); on GitHub the word is drowned by Hearthstone. It leaves the
   smithy's working surface for its fire, which is the principal's
   matter of meaning, not of this note.
4. **Incus.** The only one of the three with no carrier of the same
   kind (F8), and the least findable: the word belongs to a project
   with 6,644 stars that stands next to the field, so an "Incus for
   Claude Code" reads as something about containers. Bare registry
   names held by dormant packages (F5).
5. **A fourth word.** Outside the card; it would need a card of its
   own, and the first lead under Unexpected says the workshop
   vocabulary as a whole is crowded in this field.

## Relevance to this project

The agent's own inference, from F1, F2 and F5: the card set the rule
that a name already carried in the same field falls, and Anvil is
carried there many times over, by tools of the same kind on the same
host; so the working name does not stand as a bare public name. It is
chosen against the reading that small carriers do not count: none has
traction, but the test of the card is about being found and told
apart, and fifteen same-named tools of the same field, with more
arriving each month, defeat both whatever their size. Of the two
alternatives neither is clean: Hearth is carried in the field in
another sense and by fewer and smaller tools, Incus by none of the
kind but by a large neighbour whose meaning it would borrow. On the
evidence of this note alone, Hearth collides least in kind and Incus
least in number; which weighs more is the principal's to say. If the
smithy word is kept at all, the findings say it will have to be told
apart the way every carrier does it, by a compound or a namespace,
and that the package name on PyPI and npm cannot be the bare word in
any of the three cases. All star counts and dates are of 2026-11-15
and move.

Consult when: the public name of the engine is decided; a package
name, a plugin name or a command prefix is chosen for it; another
smithy word is proposed for the engine or for a framework built on
it; someone asks why Anvil was or was not kept.

## Sources

1. GitHub REST API, repository search, query `anvil claude`, sorted
   by stars. GitHub. Dated by structured data (each record's
   `created_at` and `pushed_at`); retrieved 2026-11-15.
   https://api.github.com/search/repositories?q=anvil+claude&sort=stars&order=desc&per_page=40
   Kind: primary (the registry's own record; each description is the
   repository owner's text). How read: partially, the first 40 of 73
   results, the fields name, stars, created, pushed, licence, topics
   and description (cut at 300 characters), raw JSON read by a script
   with no summarising model. Original.
2. GitHub REST API, repository search, query `anvil in:name`, sorted
   by stars. GitHub. Dated by structured data; retrieved 2026-11-15.
   https://api.github.com/search/repositories?q=anvil+in:name&sort=stars&order=desc&per_page=40
   Kind: primary. How read: partially, the first 40 of 4,917 results
   (down to 61 stars), the fields name, stars, created, pushed,
   licence, language and description (cut at 260 characters), raw
   JSON. Original.
3. GitHub REST API, repository search, query `hearth claude`, sorted
   by stars. GitHub. Dated by structured data; retrieved 2026-11-15.
   https://api.github.com/search/repositories?q=hearth+claude&sort=stars&order=desc&per_page=30
   Kind: primary. How read: partially, the first 30 of 43 results,
   the same fields, raw JSON. Original.
4. GitHub REST API, repository search, query `hearth in:name`, sorted
   by stars. GitHub. Dated by structured data; retrieved 2026-11-15.
   https://api.github.com/search/repositories?q=hearth+in:name&sort=stars&order=desc&per_page=30
   Kind: primary. How read: partially, the first 30 of 8,340 results
   (down to 82 stars), the same fields, raw JSON. Original.
5. GitHub REST API, repository search, query `incus claude`, sorted
   by stars. GitHub. Dated by structured data; retrieved 2026-11-15.
   https://api.github.com/search/repositories?q=incus+claude&sort=stars&order=desc&per_page=25
   Kind: primary. How read: in full for the fields named above, all
   15 results, raw JSON. Original.
6. GitHub REST API, repository search, query `incus in:name`, sorted
   by stars. GitHub. Dated by structured data; retrieved 2026-11-15.
   https://api.github.com/search/repositories?q=incus+in:name&sort=stars&order=desc&per_page=25
   Kind: primary. How read: partially, the first 25 of 673 results
   (down to 17 stars), the same fields, raw JSON. Original.
7. PyPI, project record `anvil`. Python Package Index. Dated by
   structured data (upload times of the releases, youngest
   2026-11-14). https://pypi.org/pypi/anvil/json Kind: primary. How
   read: partially, the fields name, version, summary, project URLs
   and the upload dates of all releases, raw JSON. Original.
8. PyPI, project record `hearth`. Python Package Index. Dated by
   structured data (youngest upload 2022-04-24).
   https://pypi.org/pypi/hearth/json Kind: primary. How read:
   partially, the same fields, raw JSON. Original.
9. PyPI, project record `incus`. Python Package Index. Dated by
   structured data (one upload, 2023-02-15).
   https://pypi.org/pypi/incus/json Kind: primary. How read:
   partially, the same fields, raw JSON. Original.
10. npm registry, package record `anvil`. npm. Dated by structured
    data (created 2018-11-22, modified 2022-04-11).
    https://registry.npmjs.org/anvil Kind: primary. How read:
    partially, the fields name, latest version, description, times,
    number of versions, repository and homepage, raw JSON. Original.
11. npm registry, package record `hearth`. npm. Dated by structured
    data (created 2014-12-04, modified 2022-06-18).
    https://registry.npmjs.org/hearth Kind: primary. How read:
    partially, the same fields, raw JSON. Original.
12. npm registry, package record `incus`. npm. Dated by structured
    data (created and modified 2023-11-08).
    https://registry.npmjs.org/incus Kind: primary. How read:
    partially, the same fields, raw JSON. Original.
13. `claude-plugins-official`, the marketplace file
    `.claude-plugin/marketplace.json`. Anthropic. Undated (the file
    on the main branch as served on 2026-11-15).
    https://raw.githubusercontent.com/anthropics/claude-plugins-official/main/.claude-plugin/marketplace.json
    Kind: primary. How read: in full by a script, all 317 plugin
    entries searched in every field for `anvil`, `hearth` and
    `incus`, case-insensitive; the entries themselves not read by
    eye. Original.
14. "Anvil", overview page of the documentation published on
    getfoundry.sh. The Foundry project. Undated.
    https://getfoundry.sh/anvil/overview Kind: primary (a project's
    documentation of its own tool). How read: summarised fetch, the
    quotes asked for verbatim. Original.
15. mulkatz/anvil, repository page and README. The repository's
    owner. Dated by the structured data of [1]: created 2026-02-19,
    last push 2026-02-23. https://github.com/mulkatz/anvil Kind:
    primary. How read: summarised fetch, the quotes asked for
    verbatim; the description also read raw in [1]. Original.
16. chonalchendo/anvil, repository page and README. The repository's
    owner. Undated (no date on the page as fetched).
    https://github.com/chonalchendo/anvil Kind: primary. How read:
    summarised fetch, the quotes asked for verbatim. Original.

## Opened and not used

None: every page opened is cited.

## Search record

Queries, in order:

1. `Anvil Claude Code plugin`: the disconfirming query, first
   wording.
2. `Anvil AI coding agent framework GitHub`: the disconfirming query,
   second wording.
3. `Anvil developer tool`: the wide query for the carriers outside
   AI.
4. `Hearth Claude Code plugin OR skills OR agent framework`.
5. `Hearth open source developer tool GitHub`.
6. `Incus Claude Code plugin OR agent OR AI framework`.
7. `Incus software project`.
8. `"Anvil" engine for Claude Code skills agents hooks open source
   harness`: the disconfirming query, third wording, after the
   openings.
9. `"Hearth" AI agent platform OR SDK OR framework`.
10. `"Incus" AI agent framework OR SDK -LXD -container`.

Pages opened, sixteen, in order: the six GitHub searches [1], [2],
[3], [4], [5], [6]; the six registry records [7], [8], [9], [10],
[11], [12]; the official marketplace file [13]; the Foundry page
[14]; the repository mulkatz/anvil [15]; the repository
chonalchendo/anvil [16]. Sources [1] to [13] were read as raw JSON by
a script that printed named fields; [14] to [16] through a fetch that
summarises, which is a tertiary reading of a primary page, said at
each finding that rests on it.

Seen in result lists and not opened, so the base of no finding: the
own site of the Python web-app platform Anvil, with a page on AI
agents in its editor; the PyPI packages anvil-harness, anvil-agent,
fableforge-anvil-agent and mcanvil; a scoped npm package
@heznpc/anvil on a third party's page; the repositories
ppazosp/anvil, heznpc/anvil and gebl/claude-plugins; launch pages of
products named Anvil; third-party directories of plugins and skills
for Claude Code with entries named anvil and hearth; an IDE named
Anvil of a telephony platform; an OpenStack tool named Anvil; the
Linux Containers site and press on Incus; a tool running Claude Code
on Incus.

What the disconfirming query found: the opposite of what was
expected. All three wordings returned tools for Claude Code or for AI
coding agents named Anvil; the registry confirmed fifteen under the
exact name (F1), two of them read on their own pages [15][16], and
the third wording still returned one that the earlier two had not
shown (chonalchendo/anvil). By the card's rule the name falls.

Why the run ended: the opening budget, at sixteen openings. The
first half of the stop rule was not met, since a differently worded
query still brought a new carrier, so the list of carriers in the
field is open at its small end; the second half was met for what
decides the card, each of the three names having its carriers read
in the registries' own records and Anvil's nearest two on their own
pages, while the own sites of the largest carriers outside the field
were not opened.
