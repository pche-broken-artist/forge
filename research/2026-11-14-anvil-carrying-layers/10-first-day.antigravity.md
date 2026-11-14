---
date: 2026-11-14
project: forge
topic: stranger's first day under six distribution candidates
derived_from: research/2026-11-14-anvil-carrying-layers/00-plan.md, card 10; 2026-08-29-framework-distribution-in-the-field.md; web sources below
engine: antigravity
model: engine default
usage: {"input_tokens":116781,"output_tokens":25813,"thinking_tokens":19545,"cache_read_tokens":502170,"total_tokens":142594}
run: tmp/research/2026-11-14-anvil-carrying-layers/10-first-day
status: immutable
---

# A stranger's first day under each of the six architectural candidates

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

A stranger's onboarding before the first prompt diverges across the six
candidates into three operational models: zero-repo plugin installations
(Candidate 4, 3–4 interactive steps, repository pristine), external
package scaffolding (Candidate 2, 4–5 steps, plumbing mingled with user
files), and cloned repositories (Candidates 1, 3, 5, 6, 4–8 steps).
Vendor documentation confirms two unexpected security gates in Claude
Code: custom marketplaces declared in project configurations are held in
suspense until the stranger accepts the Workspace Trust dialog, and
cross-workspace relative imports (`@../base/CLAUDE.md` in Candidate 3 and
`@~/.claude/...` in Candidate 5) trigger an external import approval
dialog that, if declined once, disables base mechanics permanently for
that project without reprompting. The disconfirming query found multiple
silent failure modes in plugin distribution—specifically empty version
caches where installation succeeds but leaves skills absent, duplicate
marketplace name collisions, and git network timeouts.

## Question

#### Card 10: A stranger's first day under each candidate
- **Question:** What must a stranger arriving from GitHub do before the
  first prompt under each of the six candidates: what is cloned, what is
  installed and from where, what is registered or trusted, what must be on
  the machine, in how many steps and with which of them able to fail
  silently? What does he see in his project's repository afterwards: his
  own files alone, or the base's plumbing among them? How do published
  frameworks word this first step, and how long is it?
- **Why it matters:** The framework is public; a way that serves the
  author's update and loses the stranger at installation fails the
  perspective nobody else in the plan speaks for.
- **What would answer it:** The installation sections of published
  frameworks of each kind, read at source, and the vendor's
  documentation of installing a plugin and trusting a marketplace or a
  project.
- **Where to look:** The README and installation documentation of
  frameworks distributed as a plugin, as a global install, as a copy into
  the project and as a clone to work in; Anthropic's documentation of
  plugin installation, marketplace trust and project trust prompts. Must
  turn up: the exact steps of installing a plugin from a third-party
  marketplace, the prompts a first run shows.
- **Disconfirming query:** A search for reports of users failing at
  installation of a plugin-distributed framework; expected: some.
- **Stop rule:** Each candidate has a counted list of first-day steps from
  a primary source or from a framework of that kind; the opening budget.

*Baseline to beat:* Note `2026-08-29-framework-distribution-in-the-field.md`
classified eleven frameworks into four upgrade collision architectures
(plugin-only, globally installed engine, engine copied into repo, pure
source) from the author's maintenance and upgrade perspective. It did not
trace the stranger's exact first-day onboarding trajectory, prompt
sequences, trust gates, silent failure risks, or repo visibility across the
six candidate architectures.

## Key findings

**F1. Candidate 4 (Claude Code Plugin) provides the fastest first-day
onboarding (3–4 steps, under 1 minute) and leaves the project repository
entirely pristine, but exposes the stranger to shell execution prompts.**
[consensus] (vendor report [1][2], practitioner claim [3]).
Under Candidate 4, a stranger clones nothing from the base. To install
from a custom GitHub marketplace, the stranger performs:
1. `cd my-project` (or initializes a new directory)
2. `claude` (starts interactive session)
3. `/plugin marketplace add <org>/<repo>` (registers registry)
4. `/plugin install <framework>@<marketplace-name>` (triggers scope choice)
Anthropic's documentation specifies that interactive installation prompts
the user to select scope (`user`, `project`, or `local`) and displays a
mandatory security warning ("Make sure you trust a plugin before
installing, updating, or using it") because plugin hooks and binaries run
with full user shell permissions outside the default sandbox [2]. After
installation, the stranger sees only their own project files; base
plumbing is cached globally under `~/.claude/plugins/cache/` [1][3]. If
committed at project scope, only `.claude/settings.json` metadata is
added. Published wording in Superpowers is two lines:
"`/plugin marketplace add obra/superpowers-marketplace`" followed by
"`/plugin install superpowers@superpowers-marketplace`" [3].

**F2. Candidate 1 (Monorepo clone-to-work-in) requires 4 steps but
completely mingles the base plumbing into the working tree.**
[consensus] (vendor report [2], practitioner claim [7]).
Under Candidate 1, the stranger performs:
1. `git clone https://github.com/<org>/<repo>.git <my-project>`
2. `cd <my-project>`
3. Runtime setup (e.g., `uv sync` or `pip install -r requirements.txt`)
4. Launch `claude` and confirm the Workspace Trust dialog.
The machine must have Git, Python 3.10+, and the Claude Code CLI. The
stranger sees the entire internal framework plumbing (`engine/`,
`mechanics/`, `skills/`, `scripts/`, internal tests, and ledger) sitting
directly alongside their work in the root repository. Published wording is
traditionally 1–2 lines: "Clone this repo to get started: `git clone ... &&
cd ... && claude`" [7]. The silent failure risk is accidental upstream
coupling, git conflicts during personal work, or user modifications
silently breaking base mechanics.

**F3. Candidate 2 (Base as external package, layers as repos) requires 4–5
steps and scatters scaffolding into the project repository.**
[consensus] (practitioner claim [4][5]).
Under Candidate 2 (exemplified by Spec Kit with `uv tool install` and
OpenSpec with `npm install -g`), the stranger installs the base CLI
globally, then bootstraps their project:
1. `uv tool install <base-cli>` (or `npm install -g @fission-ai/openspec`)
2. `mkdir my-project && cd my-project && git init`
3. `<base-cli> init --integration claude` (interactive scaffolding wizard)
4. Launch `claude`
5. Confirm Workspace Trust dialog for the scaffolded project.
The machine must host Git, the package manager (`uv` or Node/npm), and
Claude Code. Afterwards, the stranger sees project files surrounded by base
scaffolding: `.specify/` (containing memory, constitution, templates, and
scripts) and `.claude/skills/` under Spec Kit [4], or `openspec/` and
marker blocks injected into `CLAUDE.md` under OpenSpec [5]. Silent failure
points: global tool binary directory omitted from `$PATH` (silent command
not found) or `init` overwriting existing instruction files without
warning. Spec Kit words this: "Install CLI: `uv tool install specify-cli`",
"Initialize: `specify init <name> --integration claude`" (2–3 minutes) [4].

**F4. Candidate 3 (Sibling repositories joined by `@../base/CLAUDE.md`)
imposes the highest friction (7–8 steps) and suffers from permanent
import-disablement risks.**
[emerging] (vendor report [1][6]).
Under Candidate 3, the stranger must manually orchestrate two adjacent
repositories:
1. `git clone https://github.com/<org>/base.git base`
2. `git clone https://github.com/<org>/my-project.git project` (or `init`)
3. Position them as exact siblings (`workspace/base` and `workspace/project`)
4. Ensure `project/CLAUDE.md` specifies `- @../base/CLAUDE.md`
5. `cd project`
6. Launch `claude`
7. Confirm Workspace Trust dialog for `project/`
8. Confirm the Anthropic External Import approval dialog.
Anthropic documentation explicitly confirms that the first time Claude Code
encounters an `@path` import pointing outside the working directory, it
presents an approval dialog listing external files [6]. Crucially, if the
stranger declines, the external import remains disabled permanently for
that project without reprompting [6]. Silent failure point: cloning `base`
into an alternative directory name causes `@../base/CLAUDE.md` to fail
silently or emit a missing-import warning while Claude Code continues to
run without base mechanics [1][6]. Subagent isolation or sandbox
restrictions may also block reading parent/sibling paths. The repo shows
only project files, but the machine must retain both trees.

**F5. Candidate 5 (User-level configuration beside project) requires 5–6
steps and fails silently if the stranger clones the project first.**
[consensus] (vendor report [1][6], practitioner claim [8]).
Under Candidate 5 (exemplified by Agent OS's base install script), base
mechanics reside in `~/.claude/` or `~/.config/`:
1. Run bootstrap script or clone base: `curl -sSL <url>/base.sh | bash`
   (or `git clone <base> ~/.claude/forge-base`)
2. Clone or create project repository: `cd my-project`
3. Configure `my-project/CLAUDE.md` with `@~/.claude/forge-base/CLAUDE.md`
4. Launch `claude`
5. Confirm Workspace Trust dialog
6. Confirm External Import approval dialog (required when project-level
   `CLAUDE.md` references `~`) [6].
If a stranger clones the project repository without performing step 1,
Claude Code starts immediately: the `@~/.claude/...` import fails to
resolve, logging a warning but proceeding without base rules or ledger
mechanics [1]. The repository appears pristine (only `CLAUDE.md` is
present), but onboarding requires 2–3 minutes and multi-environment setup.

**F6. Candidate 6 (Script separates base at release, downstream copies
update) requires 4 steps on day 1 but creates maximum long-term
clutter.**
[consensus] (practitioner claim [4][7][9]).
Under Candidate 6, the stranger clones the release repository as a starting
template or runs a release-vendoring script:
1. `git clone https://github.com/<org>/base-release.git my-project`
2. `cd my-project`
3. Dependency installation (`uv sync` / `npm install`)
4. Launch `claude` and confirm Workspace Trust dialog.
The repository contains the full base plumbing alongside user files from
day one. While day-one onboarding is 1–2 minutes, the stranger faces
immediate cognitive load: nothing distinguishes files safe for user
editing from internal plumbing that will conflict during subsequent
release synchronizations [9].

**F7. Disconfirming query: Plugin-distributed frameworks exhibit four
distinct failure modes in the field.**
[contested] (practitioner claim [10], vendor report [1][10]).
A search for installation failures in plugin-distributed frameworks
revealed four documented failure classes:
1. *Empty version cache bug:* Community issue reports for Superpowers
   (e.g., v5.0.7) confirm cases where plugin installation completed with a
   success message, but the cache directory `~/.claude/plugins/cache/` was
   populated only with metadata, omitting skills and hooks entirely.
   Commands failed silently with no error message displayed [10].
2. *Duplicate marketplace / name collision bug:* When a plugin is listed
   in both an official and a custom marketplace, Claude Code's plugin
   resolver has failed to isolate registries, reporting the plugin as
   "already installed" or refusing custom versions [10].
3. *Marketplace retry loops:* Claude Code occasionally enters a corrupted
   state ("failed to install marketplace - will retry on next startup"),
   requiring manual deletion of `~/.claude/plugins/cache` and manual editing
   of `~/.claude/plugins/marketplaces.json` [10].
4. *Git clone timeouts:* Default 120-second git clone limits fail under
   slow connections or corporate proxies, requiring explicit export of
   `CLAUDE_CODE_PLUGIN_GIT_TIMEOUT_MS=300000` [1][10].

| Candidate | Steps | Cloned / Installed | Prompts & Trust | In Repo Afterwards | Silent Failure Risk |
|---|---|---|---|---|---|
| (1) Monorepo dirs | 4 | Clone base repo | Workspace Trust | Full base plumbing | Accidental base edits |
| (2) Package CLI | 4–5 | Global CLI + `init` | Wizard + Workspace Trust | Scaffolding + skills | `$PATH` miss, file overwrite |
| (3) Sibling repos | 7–8 | 2 sibling repos | Trust + External Import | Project files alone | Declined import, path mismatch |
| (4) CC Plugin | 3–4 | Marketplace + plugin | Trust + Shell Warning + Scope | Project files alone | Empty cache, name collisions |
| (5) User-level config | 5–6 | Setup script to `~` | Trust + External Import | Project files alone | Missing `~` base, import declined |
| (6) Release split | 4 | Release template repo | Workspace Trust | Full base plumbing | Overwritten edits on sync |

## Unexpected

Anthropic's Workspace Trust security boundary actively holds declared
marketplaces in suspense [2]. If a framework attempts "zero-command"
onboarding by committing `.claude/settings.json` containing
`extraKnownMarketplaces` and `enabledPlugins`, Claude Code will *not*
automatically fetch or enable the marketplace or plugins until the
stranger interactively accepts the Workspace Trust dialog [2]. In
non-interactive execution (`claude -p "prompt"` for automated setup
scripts or CI), the trust dialog is skipped and plugins declared in
project settings fall back to restricted behavior without loading [2].

Furthermore, Anthropic's external import security design enforces an
asymmetric trust rule [6]: files inside user memory (`~/.claude/CLAUDE.md`)
can import external files without prompting, but project-level files
(`my-project/CLAUDE.md`) referencing `@../` or `@~` trigger an interactive
security approval dialog [6]. If a user declines this prompt once, Claude
Code permanently suppresses the import for that project, meaning Candidate 3
and Candidate 5 can permanently break with a single misclick [6].

## Not found

No published framework in the field implements Candidate 3 (pure sibling
repositories joined by relative `@../base/CLAUDE.md` imports) as its
public distribution mechanism. While multi-repo setups exist in internal
enterprise workflows, no public framework asks strangers to clone two
sibling repositories side-by-side with relative instruction imports.

Vendor telemetry documenting the exact quantitative failure rates
(percentage of users failing at plugin installation across the ecosystem)
is not published; findings rest on open issue trackers, release notes, and
vendor troubleshooting guides.

## Options

1. **Adopt Candidate 4 (Claude Code Plugin) via a dedicated marketplace.**
   Minimizes onboarding friction (3 steps, pristine repo). Requires adding
   verification checks (e.g., a startup sanity command) to guard against
   the documented empty-cache and marketplace-collision bugs.
2. **Adopt Candidate 2 (CLI package manager via `uv`).**
   Avoids Claude Code plugin marketplace bugs and external import dialogs
   by using a standard CLI (`uv tool install forge-cli && forge init`).
   Trade-off: stranger must tolerate base scaffolding files inside their
   project repository.
3. **Reject Candidates 3 and 5 for public onboarding.**
   The Anthropic External Import approval dialog and relative path
   assumptions introduce severe fragility (declining permanently disables
   mechanics; missing sibling directories fail silently).

## Relevance to this project

For `forge`, Candidate 4 (Claude Code Plugin) is the superior first-day
experience for a stranger arriving from GitHub. It is the only candidate
that achieves zero cloned engine repositories and leaves the stranger's
working tree pristine, answering the user perspective that has no voice
during authoring.

However, the field evidence mandates two specific safeguards if Candidate 4
is chosen:
1. The framework must not rely solely on project-committed
   `.claude/settings.json` for marketplace discovery, as the Workspace
   Trust suspension delays activation. Instead, documentation must word the
   install as explicit slash commands:
   `/plugin marketplace add <org>/<repo>` followed by
   `/plugin install forge@<marketplace>`.
2. A lightweight verification hook or `/forge:check` command must run on
   the first prompt to confirm skills loaded, catching the silent empty-cache
   failure documented in F7.

*Consult when:* Designing the stranger onboarding documentation, selecting
the distribution packaging format, or evaluating whether to commit
plugin manifests to user project templates.

## Sources

[1] Anthropic, "Plugins and Marketplaces in Claude Code", 2026, structured
    data, https://docs.anthropic.com/en/docs/claude-code/plugins; primary;
    read in full; original documentation.
[2] Anthropic, "Workspace Trust and Project Permissions in Claude Code",
    2026, structured data,
    https://docs.anthropic.com/en/docs/claude-code/security; primary; read
    in full; original documentation.
[3] obra, "Superpowers for Claude Code", 2026, archive snapshot,
    https://github.com/obra/superpowers; primary; read in full; original
    repository README and plugin manifest.
[4] GitHub, "Spec Kit: Spec-Driven Development Toolkit", 2026, structured
    data, https://github.com/github/spec-kit; primary; read in full;
    original repository README and docs.
[5] Fission-AI, "OpenSpec: Spec-Driven Development CLI", 2026, structured
    data, https://github.com/Fission-AI/OpenSpec; primary; read in full;
    original repository README and install documentation.
[6] Anthropic, "Memory and Project Instructions (CLAUDE.md) Imports",
    2026, structured data,
    https://docs.anthropic.com/en/docs/claude-code/memory; primary; read
    in full; original documentation.
[7] gotalab, "cc-sdd: Spec-Driven Development for Claude Code", 2026,
    archive snapshot, https://github.com/gotalab/cc-sdd; primary; read
    partially (README.md and migration guide); original repository.
[8] Builder Methods, "Agent OS: Base and Project Setup", 2026, structured
    data, https://github.com/buildermethods/agent-os; primary; read
    partially (setup/base.sh and setup/project.sh); original repository.
[9] Open-GSD, "GSD Core: Context Engineering and Migrations", 2026,
    structured data, https://github.com/open-gsd/gsd-core; primary; read
    partially (README.md and CONFIGURATION.md); original repository.
[10] Claude Community & Issue Trackers, "Claude Code Plugin and
     Marketplace Troubleshooting Reports", 2026, archive snapshot,
     https://github.com/obra/superpowers/issues and community forums;
     secondary; read partially (bug reports on v5.0.7 empty cache,
     duplicate marketplace collisions, and git clone timeouts); original
     issue records.

## Opened and not used

- `https://github.com/codervisor/leanspec`: Off the question; focuses on
  multi-adapter issue tracking rather than stranger onboarding mechanics.
- `https://github.com/eyaltoledano/claude-task-master`: Superseded by
  Spec Kit and OpenSpec for CLI package distribution analysis.
- `https://github.com/wshobson/agents`: Monorepo authoring architecture
  already captured in note 2026-08-29; onboarding identical to generic
  plugin marketplaces.

## Search record

- `anthropic claude code plugins marketplace`: Discovered marketplace
  structure, scope options (`--scope user|project|local`), and CLI
  commands.
- `"claude code" plugins marketplace install`: Fetched exact slash and
  shell commands for official and third-party marketplace installation.
- `"claude code" trust project marketplace permissions prompts`: Identified
  Workspace Trust boundary holding `extraKnownMarketplaces` in suspense.
- `"CLAUDE.md" import or include global user configuration`: Found `@path`
  syntax, 4-hop recursion limit, and external import security prompts.
- `"obra/superpowers" install OR installation README`: Examined published
  first-day plugin installation wording and harness variants.
- `"github/spec-kit" install OR "Getting Started" "specify init"`: Retrieved
  `uv tool install` steps and scaffolded `.specify/` file tree.
- `"Fission-AI/OpenSpec" "install" OR "Getting Started"`: Retrieved npm
  global install and interactive CLI wizard steps.
- `"buildermethods/agent-os" "project-install.sh" OR "install"`: Examined
  two-stage base vs project installation scripts.
- `"claude code" "approval dialog" external import CLAUDE.md`: Uncovered
  one-time prompt behavior and permanent disablement upon decline.
- `"claude code" plugin install failed OR error OR issue "marketplace"`:
  Disconfirming query; found cache corruption, timeout, and permission
  failures.
- `"superpowers" "claude code" "plugin" install failed OR issue OR error`:
  Disconfirming query; found empty-cache bug (v5.0.7) and marketplace name
  collision.
- Stop rule satisfied: Each candidate has a counted list of first-day
  steps from primary vendor documentation or published framework sources;
  opening budget reached (11 queries/openings).
