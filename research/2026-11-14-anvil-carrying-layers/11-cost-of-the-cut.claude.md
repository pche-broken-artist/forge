---
date: 2026-11-14
project: forge
topic: the cost of the cut feature by feature, and the two loops as they run in today's tree
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-14-anvil-carrying-layers/11-cost-of-the-cut
derived_from: research/2026-11-14-anvil-carrying-layers/00-plan.md, card 11; the known notes 2026-11-07-engine-and-forge-framework-by-file.md and 2026-10-03-operating-layer-architecture-and-debt.md; the repository's own files listed under Sources, no web source
---

# What ties each base feature to the chain today, what each candidate would have rebuilt, and how the two loops run

<!-- The research note: one card, one engine, one note. Read from the
repository's own files, not from the web: the sections that ask for
web sources cite files by path and line instead. Immutable from its
filing (CLAUDE.md, Document kinds). -->

## In short

Every feature the brief places in the base was read at source. The
ties are of five kinds, and only one of them is dear: a script that
names the chain's files and prefixes in its code. That kind sits in
three places, the ledger script, the light check's program (which
loads the ledger script whole) and the migration script. Everything
else is tied by a literal or two, by a rule's address in `CLAUDE.md`,
or by the test fixture, which is itself a small chain. Four ties run
across all features and are cheap one by one but many: the citations
of the forge's own project by ID, the citations of `CLAUDE.md` by
section name, the single root every script computes from its own
location, and the engine's version number, which is the forge
intent's. The disconfirming query did find features that name no
artefact of the chain anywhere: `/setup` with its script, the
instance facts, the report-naming script, and the git scripts in
their code (their tests do name chain files). The candidates differ
little in what the cut itself costs; they differ in whether the
single root must be split, which candidates 1 and 6 avoid and 2 to 5
all need. The unexpected thing: the tree already runs a project
without a chain on the base features, the `library` kind, and
already saves "the whole" as two repositories side by side. Sure as a
reading of files on the day; nothing was run but searches and one
listing of tags.

## Question

**Card 11: The cost of the cut, feature by feature.** In the frame of
the packet (a framework on Claude Code to be split into a general
base, the present framework as its first operating layer, and a
place for what a user makes for himself; six candidates of delivery,
judged by the development loop and the deployment loop).

- **Question:** For every feature the brief places in the base (git
  through the scripts, the ledger and its upkeep, versioning and
  history, the ID scheme, isolated agents with their contracts,
  recipes and renders, sources and research with their indexes,
  threads, the walkthrough and its hook, `/save`, `/check`, `/setup`,
  `/test`, the instance facts): what in today's tree ties it to the
  forge's chain, by file and by the kind of tie (a name of an
  artefact written into a script, a rule in CLAUDE.md, a template, a
  test), and what would each of the six candidates require to be
  rebuilt before the feature could live in the base? Which features
  are cheap to cut, which dear, and which are better left in the
  forge or moved later? How do the development loop and the
  deployment loop run in today's tree, step by step, from a change
  of a script to a user who has it?
- **Why it matters:** Whatever the way of delivery, the split holds
  only if the mechanics can be parted from the chain; the principal
  weighs the cut feature by feature and may leave a feature in the
  forge.
- **What would answer it:** The repository's own files, read at
  source; no web.
- **Where to look:** `CLAUDE.md`, `.claude/skills/`,
  `.claude/agents/`, `.claude/settings.json`, `scripts/`,
  `templates/`, `tests/`; the brief
  `projects/forge/00-brief-engine-split.md`; the two attached notes,
  checked against the tree as it stands.
- **Disconfirming query:** A search of the tree for a feature the
  brief places in the base that names no artefact of the chain
  anywhere, against the expectation that every one does somewhere.
- **Stop rule:** Every feature of the list has its ties named by
  file, or "none found" with what was searched; the two loops are
  written step by step from the scripts and skills that run them.

The baseline to beat: the note of 2026-11-07 sorts files into engine,
framework and between, and counts mentions per script, but names no
line, no kind of tie and no feature; the note of 2026-10-03 lists the
debt of the operating layer when the scripts were PowerShell and no
test existed. Neither says what a candidate would have rebuilt, and
neither writes the loops.

## Key findings

**F1. The ties are of five kinds, and they cost differently.**
[single source: the tree; the grouping is the agent's own] (a) A name
of an artefact or a prefix written into a script's code; (b) a rule
that lives in `CLAUDE.md` and is cited by its section name; (c) a
template or a contract whose text names the chain; (d) a test or the
fixture; (e) a literal naming the forge's own project, the slug
`forge` or the path `projects/forge`. Kind (a) is the only one whose
removal changes what a program computes; the others are text or
data.

**F2. Four ties run across every feature.** [single source: pattern
searches over the tree, counted; the counts are upper bounds]

- *Citations of the forge's own project by ID* (POS, SOL, THR, REJ,
  DEC, CHL with a number): 57 in `CLAUDE.md`, 177 in 39 files of
  `.claude/skills`, 25 in 9 agent files, 44 in 17 templates, 121 in
  21 scripts. The pattern also counts examples and placeholders, so
  the figures bound the citations from above. The note of 2026-10-03
  counted 93 in 33 operating files [31]; the kind of tie it named has
  grown. Since the forge's own project is a repository of its own
  and the engine ignores `projects/*` [32, lines 8-13 of
  `.gitignore`], a stranger's clone holds none of the cited items:
  the citations are addresses into a repository he does not have.
- *Citations of `CLAUDE.md` by section name*: 148 in 37 skill files,
  30 in 8 agent files, 43 in 24 templates, 43 in 16 scripts. Base
  rules stand under a heading that names the chain: external inputs,
  renders and documentation are sub-items of `## Document chain`
  [1, lines 230-374], and are cited as "CLAUDE.md, Document chain,
  Renders" and "Document chain, External inputs" (for instance
  [27], `render/SKILL.md:6-7`, `ingest/SKILL.md:39,58,77,111`;
  `templates/index.md:9`).
- *One root*: the engine root is the parent of the directory the
  shared module lies in (`scripts/forge_repos.py:37`); a project is
  `ENGINE_ROOT/projects/<slug>` (`forge_repos.py:288-298`); the
  templates are `ENGINE_ROOT/templates` (`scripts/forge_check.py:19`,
  `scripts/forge-ledger.py:73`); the definitions are
  `ENGINE_ROOT/.claude/skills/forge/states`
  (`scripts/forge-check.py:60`); the instance file is
  `ENGINE_ROOT/CLAUDE.local.md` (`scripts/forge-record.py:218`); the
  hooks run `${CLAUDE_PROJECT_DIR}/scripts/…`
  (`.claude/settings.json:21,35`); the skills and agents call
  `python scripts/<name>.py` relative to that root, 54 times in 23
  files; pytest puts `scripts` on its path (`pytest.ini:6-7`).
- *The version*: the engine has no version of its own. A release is
  named `release <intent version>` and tagged `v<major>` when the
  forge intent's version is an integer
  (`.claude/skills/release/SKILL.md:120-131`); `/save` proposes
  `v<intent version>` (`.claude/skills/save/SKILL.md:45-46`). The
  number lives in a document of another repository.

**F3. Feature by feature: the ties, by file and kind.** [single
source: the files read at the lines given]

| Feature | Ties found | Kind | Weight |
|---|---|---|---|
| Git through the scripts | no artefact named in code; the slug `forge` and `projects/forge` hard-wired as "the whole" (`forge_repos.py:345,349-360,371`; `forge-save.py:111,148,179-183`; `forge-branch.py:55`; `forge-status.py:123`); the layout `projects/` (`forge_repos.py:385-391`, `forge-clone.py:51-57`, `forge-status.py:133-136`); the tests change `10-intent.md` and `00-brief.md` of the fixture (`tests/test_git_scripts.py:20,86,109`) and build the forge pair (`tests/conftest.py:137-178`); the rule is `CLAUDE.md` Persistence (lines 579-674), cited by `scripts/hook-git.py:58,77` | e, d, b | cheap |
| The ledger and its upkeep | `scripts/forge-ledger.py`: the Briefs table reads `00-brief*.md` and the mining records of `10-intent.history.md` (163-181); Documents excludes `00-brief` (184-196); a Renders row writes `10-intent.md v…` (253); Waiting knows TBC, a critic's FND, CHL and the threads (473-510); the reports search THR (513-565); FND, CHL and DEC shapes as regexes (76-78, 136); old thread files by name (455, 572); `templates/ledger.md:26-43` owns the Briefs and Documents tables; `tests/test_forge_ledger.py:25-28,65` asserts them | a, c, d | dear |
| Versioning and history | `forge-record.py` takes any document by path, the chain only in its examples (26, 62-64, 89); `forge-history.py` treats the intent as the unmarked case (230, 253, 259); `forge_check.py:147-166` finds briefs by name and falls back to the template `intent` (160); `templates/history.md:19,27-32` cites the intent's definition and the mining record; the rule is `CLAUDE.md` Versioning & status (675-729), which names no artefact | a (literals), c, b | middle |
| The ID scheme | the format is content-blind (`forge_docs.py:18`, `forge-history.py:69`, `forge_check.py:134-144`); single prefixes are written into code (`forge-check.py:63`; `forge_docs.py:21`; `forge-ledger.py:76-78`; `forge-record.py:81`); the table of prefixes is one table in `CLAUDE.md` (730-767) holding the layer's prefixes beside THR, FND, CHL and DEC | a (literals), b | cheap for the format, middle for the table |
| Isolated agents with their contracts | the dispatchers scan agent files and name no artefact (`check/SKILL.md:6-23`); the contracts do: the critic's Inputs are "the briefs (`00-brief*.md`), `10-intent.md`, the threads" and its calibration cites the definitions of the assignment and the solution design (`critic-contract/SKILL.md:45-48,68-80`); the challenger's Inputs the same files (`challenger-contract/SKILL.md:37-40,50,65`); the check contract names the forge intent and `projects/forge/ledger.md` (`check-contract/SKILL.md:38,61`); `CLAUDE.md` Isolated reviewers (777-844) says a Lens may narrow a contract and never replace it | c, b, e | middle |
| Recipes and renders | `render/SKILL.md` and `recipe/SKILL.md` name no artefact; `templates/recipe.md:19-20` gives `10-intent.md` as the sample input; the conversions cite nothing (`md2pptx.py`, `md2docx.py`, `md2video.py`: no ID, no chain name found); `forge-ledger.py:203-217` knows the engine root as a render target; the two genres every project gets, README and release notes, are scaffolded by `new-project/SKILL.md:50-63`; the rule stands under `## Document chain` (F2) | c, b | cheap |
| Sources and research with their indexes | `ingest/SKILL.md` names the kinds `thought` and `library` (18-23) and the intent once, as what a source may add to (109-117); `templates/index.md`, `index-bundle.md` name nothing of the chain; `research/SKILL.md:29-30,46-48,178` cites a brief of the forge's project and "an artefact of the chain" as what a research may serve; `templates/research-plan.md:118` names `/forge <state>`; `forge-cite.py` cites nothing | c, b | cheap |
| Threads | a thread has no history of its own: its birth and closing are records in the intent's history, or the brief's (`thread/SKILL.md:36-38,81-85`; `forge-check.py:421-433`); `concerns` defaults to `intent` (`forge_docs.py:213,234`; `templates/thread.md:3`) and is checked against the listing of the definitions (`forge-check.py:363,402-409`); `tests/test_forge_check_light.py:49-66` and `tests/test_forge_ledger.py:70-83` | a, c, d | middle |
| The walkthrough and its hook | `hook-walkthrough.py:30-47` prints six constant lines and names no artefact, only the skill's path and `scripts/forge-*.py`; `walkthrough/SKILL.md:7` cites a position in `projects/forge/10-intent.md` and line 107 says a rejected proposal "becomes a REJ in the intent"; the hook is configured in `.claude/settings.json:13-24` | c, e | cheap |
| `/save` | `save/SKILL.md`: the pair `forge` (9-12), the light check through `/check` (26-34), the tag from the intent's version (45-46); the message is drafted from the histories, any document's (35-38) | e, and what `/check light` carries | cheap by itself |
| `/check` | the dispatcher is clean but for the special case "the engine's own project is `forge`" (`check/SKILL.md:25-31,39`); the light check's program is the dear part: it loads `forge-ledger.py` whole (`forge-check.py:87-91,95-99`) and so inherits every tie of the ledger, and adds the thread clauses; `check-light.md:13,38` and `check-project.md` (the README and release-notes recipes, "a brief whose mining record says `mined` is cited somewhere in the intent") | a, c, e | dispatcher cheap, program dear |
| `/setup` | none found: `setup/SKILL.md` names no artefact; it writes `CLAUDE.local.md` at the engine root (15), a model into `.claude/settings.local.json` (65-75) and points at `/new-project` (76-78); `forge-config.py` roots at `ENGINE_ROOT` (74) and names no artefact | root only | cheapest |
| `/test` | the command runs pytest and names no artefact but a brief of the forge's project as its citation (`test/SKILL.md:6`); the fixture every test copies is a thought project with `00-brief.md`, `10-intent.md` and `threads/` (`tests/fixture/`, `tests/conftest.py:10-15`); 83 test functions were counted in 11 files | d | command cheap, fixture middle |
| The instance facts | none found: `templates/CLAUDE.local.md:1-10` holds three lines and names no artefact; the Author line is read by `forge_docs.py:262-271` for `forge-record.py:218`; `docs-check.py:84` reads the file for its scan | root only | cheap |

**F4. The disconfirming query found features that name no artefact.**
[single source: pattern search for the chain's file names, definition
names and prefixes over `scripts/`, `.claude/`, `templates/`] The
expectation was that every base feature names an artefact somewhere.
It does not hold for `/setup` and `forge-config.py`, for the instance
facts, for `forge-report.py` (the chain only in two example lines of
its help, 32-33), for `forge-clone.py` and `forge_tools.py` (no ID
citation at all), and for the code of the git scripts and of
`hook-git.py`. It holds for the ledger, the light check's program,
the threads, the contracts, the history template and the tests. Read
with F2: nearly every one of the clean files still cites the forge's
own project by ID or `CLAUDE.md` by section, so "names no artefact"
is true and "cites nothing of the forge" is not.

**F5. What the cut itself needs, whatever the candidate.** [the
agent's own inference from F2 and F3] Five pieces of work recur and
none depends on the way of delivery: (1) `CLAUDE.md` divided, with
the base's rules lifted out from under the heading `Document chain`,
and the roughly 264 citations by section name kept resolvable;
(2) the ledger's tables that know the chain (Briefs with mining, the
intent's version in a row, which prefixes wait) either declared by
the layer or left in the layer beside a base ledger of the generic
tables; (3) the literals `intent`, `brief` and `forge` in
`forge_docs.py`, `forge-history.py`, `forge_check.py` and
`forge_repos.py` replaced by something a layer or a project
declares; (4) the Inputs and calibration paragraphs of the two
reviewer contracts turned into something a layer supplies, which
today's rule on a Lens forbids; (5) a fixture for the base's tests
that is not a chain, or the tests of the chain-aware scripts moved
with them. Whether (1) keeps the conduct it carries is not something
the tree can show: nothing in `tests/` tests an instruction.

**F6. What each candidate adds to that.** [the agent's own inference
from the tree; what Claude Code itself offers for each candidate was
not looked up here and is other cards' to say]

| Candidate | Rebuilt beyond F5, as the tree shows it |
|---|---|
| 1. One repository, layers as directories | nothing of the root (F2) moves; where definitions or templates move into a layer's directory, the two single-path constants (`forge_check.py:19`, `forge-check.py:60`) become a list of roots. Both loops stay as they are. A project that is not the forge clones the whole. |
| 2. The base a package, each layer a repository | every root of F2 splits into "where the base is installed" and "where the work lies": the 54 calls `python scripts/…` in 23 skill and agent files, the two hook commands, the templates and definitions paths, the instance file, `pytest.ini`; `forge-pull.py`, whose upgrade channel is the clone the scripts lie in (lines 3-4, 10), no longer upgrades the base; a declaration of the base's version, of which nothing exists today (F8). |
| 3. Two repositories side by side joined by an import | the same split of the root as 2; the scripts already treat "the whole" as two repositories side by side, two commits and one tag in both (`forge_repos.py:349-360`, `forge-save.py:183`), so the git layer has the pattern; `CLAUDE.md` is divided as in F5 and one half imports the other. |
| 4. A plugin | the same split of the root as 2; the two hooks, the three deny rules and the attribution switch move out of `.claude/settings.json` (lines 2-11, 12-41) or stay behind in every project; `/setup` writes into the clone's root and `.claude/` (15, 65) and would need a new target. |
| 5. User-level configuration and imports | the same split of the root as 2; one base per machine for every project on it, so two layers cannot hold different versions of it; the instance file is one per clone today (`setup/SKILL.md:15`). |
| 6. The whole kept, the base separated by a script at release | nothing moves and the development loop is untouched; needs a manifest of which file is base, and for each mixed file (the ledger script, the light check's program, the contracts, `CLAUDE.md`, `templates/ledger.md`, `templates/history.md`, the fixture) either the work of F5 done first or an export that ships it with the chain inside; the citations of F2 exported as they stand point into a project the base's users do not have. `/release` is already the one place derived files are made, on `main` only (`CLAUDE.md`, lines 640-646). |

**F7. Cheap, dear, left, later.** [the agent's own ranking from F3]
*Cheap to cut*: the instance facts and `/setup`; the git scripts with
the git hook; `/save`; `forge-report` and `forge-record`; the format
of an ID; recipes, renders and the conversions; sources, the indexes
and `/ingest`; research; the walkthrough and its hook; the `/check`
dispatcher; `/test` as a command. *Middle*: versioning and history
(three literals and a template comment); threads, because they
borrow the intent's history; the reviewer contracts; the fixture.
*Dear*: the ledger; the light check as a program, since it stands on
the ledger; `CLAUDE.md`. *Better left in the forge*: `forge-migrate`
(it brings past shapes of the chain's own files forward: lines
25-47, 174-180, 272-288, 399-449), the Briefs table with mining, the
checks that read the forge intent (`check-engine.md:14-16`),
`new-artefact`, `spinoff`. *Moved later*: the ledger, once a layer
can declare its tables; the thread's records, once it is settled
whose history they go into where a project has no intent.

**F8. The development loop in today's tree.** [single source: the
skills and scripts at the lines given]
1. A script is edited in the clone the session runs in. It is live
   at once: skills call it by relative path and the hooks by
   `${CLAUDE_PROJECT_DIR}` (F2). No packaging step exists.
2. `/test` runs `python -m pytest -q` from the root on copies of the
   fixture in a temporary directory (`test/SKILL.md:6-21`).
3. The change is tried on any project, by slug under `projects/` or
   by path (`forge_repos.py:288-298`).
4. The change is recorded: a process change "is complete only once
   that intent is updated and the README re-rendered" (`CLAUDE.md`,
   The system's own project, lines 904-915), the record through
   `forge-record.py`.
5. `/save forge`: the state from `forge-status.py`, the light check
   on `projects/forge` (`save/SKILL.md:21-34`), a message drafted
   from the histories (35-42), then `forge-save.py` commits and
   pushes the engine and the forge's own project, each its own
   commit (`save/SKILL.md:9-12`). CI runs the tests on the push
   (`.github/workflows/tests.yml:6-8,19-22`).

**F9. The deployment loop in today's tree.** [single source: as F8]
6. `/release forge`, on `main` only, refused when behind or diverged
   (`release/SKILL.md:29-39`): the tests (40-50); the checks
   `engine`, and `light` and `project` on `projects/forge` (51-56);
   the offer of one critic lens (72-78); the documentation's age
   against the intent's version and the offer of `/document`
   (79-91); the README and the release notes rendered from the
   recipes of the forge's project (92-103); the state render
   (107-111); `/save --quick` with `release <intent version>: …` and
   the tag `v<major>` at an integer (117-131). The tags `v3.0` to
   `v7` exist [33].
7. A user has cloned the repository and run `/setup`
   (`README.md:205-207`). He runs `/pull`: `forge-status.py
   --remote`, then `forge-pull.py`, fast-forward only, a repository
   with unsaved changes skipped or refused
   (`pull/SKILL.md:14-24`; `forge-pull.py:10-20,63-71`).
8. After a pull of the engine he is shown the Action required lines
   of every release crossed, offered the two checks on each of his
   projects, and `/migrate` where a line names a migration
   (`pull/SKILL.md:25-33`).
- *How a layer says which base it needs*: not found. A project says
  only whether it is of the current shape, by the presence of
  `project.md` (`forge_repos.py:313-336`): a yes or no, not a
  version.
- *How often a user is forced to update*: never by the tree; the
  forge "never pulls or merges on its own judgement" (`CLAUDE.md`,
  Persistence, lines 646-650) and `/pull` only offers.
- *What a pull delivers*: the head of the branch, not a release:
  `forge-pull.py:71` pulls `origin <branch>`, and `/save` pushes on
  whatever branch is checked out (`save/SKILL.md:6-7`). In the log
  read on the day, eleven commits lie after the commit `release 7.0`
  [33]. A user who pulls between releases receives them without
  release notes.

## Unexpected

**The base without the chain already runs in the tree.** A project of
kind `library` has no chain and still has the ledger, the checks,
`/ingest`, `/research`, a README render and `/save`: the ledger
drops the chain's tables for it by one tuple
(`forge-ledger.py:75,582-583`), `/new-project` scaffolds it without a
brief (`new-project/SKILL.md:36-42`), the map stops before the chain
(`forge/SKILL.md:25-28`), the project check reduces its structure
(`check-project.md`, item 0). The card assumes the base must be
carved out of a tree where everything knows the chain; the kind of a
project is already the switch for "a project with fewer tables", and
a base project could be a third kind beside the two. A lead, not a
conclusion: no library was read, the mechanism only.

**A user's own file inside the clone would stop the upgrade.**
`forge-pull.py:63-69` skips or refuses a repository when
`git status --porcelain` prints anything, and that command lists
untracked files that are not ignored. A user's own agent or skill
placed in the clone's `.claude/` under a new name is such a file.
The place "where an upgrade never writes" is therefore not enough:
it must also be a place the upgrade does not look at, as `projects/*`
and the two local files are through `.gitignore` [32]. Read from the
code, not tried.

**The two known items disagree on the walkthrough.** The brief places
"the shape of the conversation, … states and walkthrough" in the
base (`projects/forge/00-brief-engine-split.md:72-76`); the note of
2026-11-07 places the skill `walkthrough` and the method paragraphs
in the forge framework and calls the hook a base mechanism carrying
framework text [31, F2 and F3]. The tree decides neither: the hook's
six lines name no artefact (F3).

**The by-file note is older than the tree in three places.** It
names five definitions; the directory holds six (`brief`, `intent`,
`assignment`, `brd`, `solution-design`, `user-stories`). It lists no
`thread` skill, no `forge-record.py`, no `check-boundary` and no
`check-user-stories`; all four exist. Its "between" list stands
otherwise.

## Not found

- Any declaration of the base's version, of a minimum version a
  project or a layer needs, or of a compatibility range: searched
  `templates/project.md`, `forge_repos.py` (project_file),
  `release/SKILL.md`, `pull/SKILL.md`; only the shape, yes or no.
- Any test of an instruction, a skill or `CLAUDE.md`: `tests/` holds
  tests of scripts only.
- The kit of the core the brief says was tried on 2026-11-13
  (`00-brief-engine-split.md:163-168`): no file of it lies in the
  tree read; the brief itself says the run is not yet registered.
- How much of `CLAUDE.md` each layer owns by lines: the headings
  were located (lines 3 to 916), the body was not sorted line by
  line.
- What Claude Code offers for a second root of skills, agents or
  templates, for a plugin's paths and for imports: not looked up, by
  the terms of this card.
- Whether the ID counts of F2 hold exactly: the pattern cannot tell
  a citation of the forge's intent from an example.

## Options

**A. Cut the cheap group first and leave the rest in the forge.** The
features F7 calls cheap leave with the literals renamed and the root
handled per candidate; the ledger, the light check's program, the
threads' records and the contracts stay in the layer for now. The
base is then real and small, and a project on it has git, records,
renders, sources and research but no ledger and no light check. The
price: `/save` runs the light check by default
(`save/SKILL.md:26-29`), so the base's `/save` is the `--quick` one
until a base check exists.

**B. Declare first, then cut.** The work of F5 is done inside
today's tree before anything moves: a layer or a project declares
its trunk document, its prefixes and its ledger tables, and the
scripts read the declaration. Every candidate is then cheap for
every feature. The price: the dear work comes first, in the most
reworked scripts, with the fixture rebuilt alongside; and the
declaration is a new convention to decide.

**C. A third kind of project.** The existing switch of the kind
(Unexpected, first lead) is widened: a project without a chain that
is not a library. Nothing is cut; the base is what such a project
uses. Cheapest of all and reaches none of the brief's aims for
delivery: other projects still clone the whole, and the layer is
still the tree.

**D. Order by the root.** Whatever is chosen above, the one cost that
differs by candidate is the split of the single root (F2, F6).
Candidates 1 and 6 do not pay it; 2 to 5 pay it in full, and it is
mechanical: one resolver in `forge_repos.py` and one way for a skill
to name a script, with the tests already running scripts by path
(`tests/conftest.py:10-15`).

## Relevance to this project

The agent's own reading, offered once. The cut is cheaper than the
note of 2026-11-07 suggests by its list of files and dearer than it
suggests by its one shape: most base features name no artefact at
all, but three programs hold nearly all of the real work, and the
light check cannot leave before the ledger does. The recommendation
is A with D's order: take the cheap group, leave the ledger, the
light check's program and `forge-migrate` in the forge, and choose
the candidate by the two loops, since the cost by feature barely
separates the candidates. It rests on F3, F4 and F6. It is chosen
against B, which does the dearest work before anything is seen to
serve, and against C, which changes nothing a stranger receives. Two
things want settling before any candidate is taken, both from F9:
what a pull delivers (a release or the head of `main`), and where
the base's version number lives once it cannot be the forge
intent's.

Consult when: a feature is weighed for the base or left in the
forge; a script is about to learn a name of the chain; the ledger's
tables are opened; the root resolver of `forge_repos.py` is touched;
a version of the base is defined; a user's own agents get a place;
the walkthrough is assigned to a layer.

## Sources

All sources are files of the repository, read on 2026-11-14 at the
checked-out state; kind primary, original, undated but by the tree.

1. `CLAUDE.md`; read in full as the session's instructions, headings
   located at lines 3, 28, 35, 101, 190, 230, 375, 579, 675, 730,
   768, 777, 845, 852, 869, 904, 916.
2. `.claude/settings.json`, lines 1-42; in full.
3. `scripts/forge_repos.py`; partially: lines 1-100 and 280-392.
4. `scripts/forge-save.py`; partially: lines 95-189, the header by
   pattern search.
5. `scripts/forge-pull.py`, lines 1-91; in full.
6. `scripts/forge-ledger.py`; partially: lines 1-75, 160-260,
   470-512, the rest by pattern search with line numbers.
7. `scripts/forge-check.py`; partially: lines 1-175, 360-440, the
   rest by pattern search.
8. `scripts/forge_check.py`; partially: lines 130-177 and by pattern
   search.
9. `scripts/forge_docs.py`; partially: lines 255-271 and by pattern
   search.
10. `scripts/forge-history.py`; partially: lines 215-262 and by
    pattern search.
11. `scripts/forge-record.py`; partially: lines 84-125 and by pattern
    search.
12. `scripts/forge-migrate.py`; by pattern search only, the matching
    lines read.
13. `scripts/hook-walkthrough.py`, lines 1-49; in full.
14. `scripts/hook-git.py`; by pattern search only.
15. `scripts/forge-report.py`, `forge-config.py`, `forge-clone.py`,
    `forge-branch.py`, `forge-status.py`, `forge_tools.py`,
    `forge-cite.py`, `forge-engine.py`, `md2pptx.py`, `md2docx.py`,
    `md2video.py`, `doc2md.py`, the `docs-*` scripts; by pattern
    search only (chain names, IDs, root reads).
16. `.claude/skills/save/SKILL.md`, lines 1-57; in full.
17. `.claude/skills/check/SKILL.md`, lines 1-65; in full.
18. `.claude/skills/setup/SKILL.md`, lines 1-78; in full.
19. `.claude/skills/test/SKILL.md`, lines 1-28; in full.
20. `.claude/skills/thread/SKILL.md`, lines 1-86; in full.
21. `.claude/skills/release/SKILL.md`, lines 1-141; in full.
22. `.claude/skills/pull/SKILL.md`, lines 1-34; in full.
23. `.claude/skills/forge/SKILL.md`, lines 1-74; in full.
24. `.claude/skills/walkthrough/SKILL.md`; partially: lines 88-109
    and by pattern search.
25. `.claude/skills/critic-contract/SKILL.md` (lines 36-82),
    `challenger-contract/SKILL.md` and `check-contract/SKILL.md` (by
    pattern search).
26. `.claude/agents/check-light.md` (lines 1-65, in full),
    `.claude/agents/check-project.md` (lines 10-74),
    `.claude/agents/check-engine.md` (by pattern search).
27. `.claude/skills/render/SKILL.md` (lines 1-40),
    `recipe/SKILL.md` (lines 5-44), `new-project/SKILL.md` (lines
    36-79), `research/SKILL.md` (lines 36-70 and by pattern search),
    `ingest/SKILL.md` (lines 14-26 and by pattern search),
    `history/SKILL.md`, `ledger/SKILL.md`, `end/SKILL.md` (in full).
28. `templates/ledger.md`, `history.md`, `thread.md`, `project.md`,
    `index.md`, `index-bundle.md`, `recipe.md`, `research.md`,
    `research-plan.md`, `decisions.md`, `work.md`, `gitattributes`
    (by pattern search); `templates/CLAUDE.local.md` (in full).
29. `tests/conftest.py` (lines 1-60 and by pattern search), the test
    files by pattern search, the listing of `tests/fixture/`,
    `pytest.ini` and `.github/workflows/tests.yml` (in full).
30. `projects/forge/00-brief-engine-split.md`, lines 1-211; in full.
31. The two attached notes in the packet folder,
    `2026-11-07-engine-and-forge-framework-by-file.md` and
    `2026-10-03-operating-layer-architecture-and-debt.md`; in full;
    secondary, notes of the same project about an older tree.
32. `.gitignore` and `.gitattributes` of the root (in full);
    `README.md`, lines 153, 199-239 by pattern search only.
33. The repository's tags and the subjects of its last forty
    commits, read through git on the day; primary.

## Opened and not used

- `.claude/skills/end/SKILL.md`, `history/SKILL.md`,
  `ledger/SKILL.md`: read, no tie beyond what F3 names for their
  scripts.
- `.gitattributes` of the root: read, off the question.

## Search record

Queries, in order: the listing of the packet folder; the tracked
files of the tree with line counts; a pattern search of `scripts/`
for the chain's file names, definition names, prefixes and the slug
`forge`; a search of the scripts for reads of the engine root, the
templates and the definitions; the base skills read; a search of the
remaining skills for chain names; counts of ID citations and of
citations of `projects/forge` per directory, repeated once without
byte-code caches; a search of the base templates; the tests'
shared file and their chain names; the light check's agent and the
forge skill; the instance template and the readers of the instance
file; the pull and save scripts and the README's install lines; the
tags and the last forty commit subjects; counts of script calls, of
citations of `CLAUDE.md` and of the definitions' path outside the
forge skill. No web page was opened; the opening budget does not
apply to a card read from disk.

The disconfirming query: found. `/setup` with `forge-config.py`, the
instance facts, `forge-report.py`, `forge-clone.py`, `forge_tools.py`
and the code of the git scripts and of the git hook name no artefact
of the chain; the expectation that every base feature does somewhere
is false for them and true for the rest (F4).

The run ended on the card's stop rule: every feature of the list has
its ties named by file or "none found" with what was searched, and
both loops are written from the scripts and skills that run them.
