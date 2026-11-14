---
date: 2026-11-14
project: forge
topic: the release rhythm of a base others stand on
derived_from: research/2026-11-14-anvil-carrying-layers/00-plan.md, card 6; 2026-10-03-one-tool-a-core-with-modules-or-several-tools.md; web sources below
engine: antigravity
model: engine default
usage: {"input_tokens":174311,"output_tokens":30733,"thinking_tokens":22731,"cache_read_tokens":1807828,"total_tokens":205044}
run: tmp/research/2026-11-14-anvil-carrying-layers/06-release-rhythm
status: immutable
---

# The release rhythm of a base others stand on

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Ecosystems with dependent layers keep development apart from stability
either through timed train schedules (Rust's 6-week cadence, Go's
6-month window) or channel tiers (nightly, beta, stable). Dependent
pieces express base version requirements via manifest fields: either as
semantic version ranges (VS Code, npm, Terraform) or bare minimum
version numbers (Cargo, Go). When a host version mismatch occurs,
platforms overwhelmingly refuse execution rather than degrade
silently; only npm defaults to an advisory warning. Stability is
guaranteed through explicit source-compatibility promises (Go 1.x,
Terraform 1.x) and deprecation windows enforced before removal. The
disconfirming query confirms that for solo maintainers, multi-channel
branching and upper version bounds create unmanageable backporting
and dependency deadlock overhead. An unexpected gap is that Claude
Code's plugin manifest provides peer dependency resolution but lacks
any field to declare minimum host CLI requirements.

## Question

#### Card 6: The release rhythm of a base others stand on
- **Question:** How do projects with dependent packages and users
  choose how often they release, how they keep a stable line apart
  from a development line, how a dependent piece says which version
  of the base it needs (a range, a minimum, a compatibility number),
  and what they do with a user who does not have it: refuse, warn,
  degrade? What do they promise not to change between versions?
- **Why it matters:** News of the framework is released daily today;
  the choice of the way changes with how often and how forcibly a user
  must update, and a layer needs a way to say which base it needs.
- **What would answer it:** The written release and versioning policies
  of projects with dependants, and the specifications of version
  ranges.
- **Where to look:** The versioning specifications in use; the release
  policies of platforms with plugins or providers that declare the
  host version they need (editors with packages, infrastructure tools
  with providers, language toolchains with channels); the plugin
  manifest of Claude Code for what it lets a plugin declare. Must turn
  up: a stable and a development channel, a minimum-host-version
  field, a deprecation policy.
- **Disconfirming query:** A search for arguments that a small
  single-maintainer project should not keep channels or ranges at all;
  expected: some, and their reasons.
- **Stop rule:** Three or more written policies with a primary source
  each, the single-maintainer case among them or recorded as not
  found; the opening budget.

The baseline to beat is the attached note
`2026-10-03-one-tool-a-core-with-modules-or-several-tools.md`. That
note established that mature ecosystems converge on a core with typed
extension points and documented that distribution machinery (registries,
separate repositories) was where previous frameworks retreated.
However, it left unaddressed the operational mechanics of release
trains, how host mismatches are enforced at runtime, how deprecation
windows are defined, and how Claude Code's plugin system handles host
constraints.

## Key findings

**F1: Platforms separate development from stable lines using timed
release trains with strict feature gating.** [consensus, vendor
documentation]
Mature host platforms do not branch arbitrarily; they release on fixed
calendar rhythms. Rust operates a strict six-week train model where
changes land continuously on a daily Nightly channel, graduate to a
six-week Beta channel for regression triage, and advance to Stable
[4]. Experimental features remain locked behind compiler feature flags
(`#![feature(...)]`) and are strictly forbidden on Stable builds [4].
Go follows a predictable six-month major release cycle (typically
February and August), supporting each release for two active release
cycles (the N-2 policy, approximately one year of support per release)
[7]. Node.js runs an annual major release train where new versions
transition through Alpha and Current (six months) into Active Long
Term Support (LTS) lasting 30 months [12]. Kubernetes releases three
times a year (a four-month cadence), splitting API tracks into Alpha
(disabled by default), Beta (pre-release, enabled), and GA/Stable [13].

**F2: Dependent pieces express base requirements via manifest
constraints, utilizing either SemVer ranges or bare lower bounds.**
[consensus, standard / vendor specification]
Host requirements are declared in explicit manifest fields. VS Code
extensions require an `engines.vscode` property in `package.json`,
specifying compatibility via Semantic Versioning ranges (commonly
caret ranges like `^1.80.0`) [3]. Node.js packages use `engines.node`
in `package.json` to define semver version constraints [11]. Terraform
configurations and modules declare required CLI versions in the
`terraform` settings block via `required_version`, supporting standard
comparison operators (`>=`, `<`) and a pessimistic constraint operator
(`~> 1.5`, which allows patch/minor increments of the rightmost
element while blocking the next major) [1]. In contrast, Cargo
packages specify `rust-version` (Minimum Supported Rust Version, MSRV)
in `Cargo.toml` as a bare version number without range operators or
pre-release identifiers (e.g., `1.75`) [5]. Go modules declare the
minimum language/toolchain version as a bare version on the `go`
directive in `go.mod` (e.g., `go 1.22`) [8].

**F3: Host version mismatches result in hard refusal; silent degradation
is universally avoided.** [consensus, vendor documentation]
When an environment does not satisfy the declared base version,
systems overwhelmingly refuse to run rather than degrade features:
- *VS Code:* The Marketplace and the editor refuse to install or
  update an extension if the running VS Code build does not satisfy
  `engines.vscode` [3].
- *Terraform:* The CLI emits an unsupported Core version error and
  immediately halts all `plan` and `apply` operations without
  touching state [1].
- *Cargo:* The compiler halts with an explicit error when invoked on a
  toolchain older than `rust-version`, though it provides an escape
  hatch via `--ignore-rust-version` [5].
- *Go:* Starting in Go 1.21, the toolchain strictly refuses to compile
  a module whose `go` directive specifies a newer version, or
  transparently invokes automated toolchain downloading to switch to
  the required toolchain [8].
- *npm (advisory exception):* npm defaults to logging a non-fatal
  warning on `engines.node` mismatch during package installation,
  refusing only when the user or project has explicitly enabled the
  `engine-strict=true` configuration flag [11].
No reviewed ecosystem implements automatic runtime degradation to an
inferior feature subset when the base is outdated [1, 3, 5, 8, 11].

**F4: Stability guarantees protect public APIs within major lines;
deprecations require formal grace periods before removal.**
[consensus, standard / vendor policy]
Semantic Versioning (SemVer 2.0.0) mandates that within a major
version number, MINOR releases only add backward-compatible
functionality and PATCH releases only add backward-compatible bug fixes;
breaking public API changes require a MAJOR version bump [14]. Go's
foundational compatibility promise ("Go 1 and the Future of Go
Programs") guarantees source-level backward compatibility across the
entire Go 1.x lifecycle: valid code written for Go 1.0 must compile and
run correctly on subsequent releases, with narrow exceptions reserved
strictly for security vulnerabilities, compiler specification fixes,
and unspecified runtime behavior [6]. Terraform v1.x guarantees
compatibility across configuration syntax, core automation CLI commands
(`init`, `plan`, `apply`), and the provider wire protocols across all
v1.x releases [2]. Deprecation policies enforce transition periods:
Kubernetes mandates that Beta APIs must remain supported for at least
nine months or three minor releases after deprecation before removal,
serving HTTP `Warning` headers to calling clients [13], while
non-API features must remain functional for at least one year [13].
Node.js requires that deprecated APIs emit runtime warnings and
prohibits removal until the next SemVer-major release [12].

**F5: Claude Code's plugin manifest supports peer-plugin dependencies
but provides no mechanism to declare host version requirements.**
[vendor claim, vendor documentation]
Claude Code's plugin specification (`.claude-plugin/plugin.json`)
provides a `dependencies` array allowing plugins to declare dependencies
on other plugins hosted in the same or permitted marketplaces,
specifying semantic version ranges matched against git tags (e.g.,
`<plugin>--v<version>`) [10]. It also supports empty meta-plugins that
bundle multiple dependencies [10]. However, `plugin.json` defines no
property for declaring a minimum Claude Code CLI version or engine
requirement [9]. Host compatibility requirements must be communicated
via external prose documentation or fail unhandled at runtime when an
unsupported hook or capability is evaluated [9].

**F6: For solo maintainers, multi-channel pipelines and upper version
bounds create disproportionate maintenance debt and failure modes.**
[practitioner claim / emerging consensus, expert analysis]
The disconfirming investigation demonstrates that enterprise release
machinery harms small, single-maintainer projects:
- *Channel overhead:* Trunk-Based Development guidance documents that
  maintaining multiple long-lived release branches or channels imposes
  heavy cherry-picking, backporting, and context-switching overhead
  [16]. High-velocity and solo projects operate more sustainably
  by releasing directly from trunk ("release from trunk"), relying on
  continuous integration, feature flags, and a "fix-forward" strategy
  rather than maintaining historical maintenance lines [16].
- *Upper bound hazards:* In his analysis "Semantic Versioning Will Not
  Save You", Hynek Schlawack demonstrates that treating SemVer major
  version caps (e.g., `<2.0` or `^1.0`) as guarantees creates severe
  failure modes in practice [15]. Upper version bounds on dependencies
  frequently cause dependency resolution deadlocks across ecosystems
  and lock users out of critical bug fixes, while failing to prevent
  breakage caused by differing definitions of "breaking" or human
  error [15]. Schlawack recommends that libraries declare open lower
  bounds (minimum required version) without upper bounds, leaving
  pinning to application-level lockfiles [15].

## Unexpected

Claude Code's plugin manifest completely omits host-level version
constraints [9]. While ecosystems like VS Code (`engines.vscode`) [3],
Node (`engines.node`) [11], Cargo (`rust-version`) [5], and Terraform
(`required_version`) [1] consider host engine declarations essential
to prevent runtime crashes, Claude Code's `plugin.json` only provides
peer-to-peer plugin dependencies [10]. A plugin author has no native
manifest mechanism to assert that their plugin requires a specific
minimum version of Claude Code.

Go 1.21 transformed the `go` directive from an advisory documentation
tag into a self-healing toolchain management system [8]. If a module
declares a newer Go version than the running binary, modern Go does
not merely error out; it transparently downloads, unpacks, and executes
the required toolchain version on the fly [8]. Host version mismatch
is thus addressed via automated just-in-time provisioning rather than
manual user intervention.

## Not found

- No official Anthropic documentation or schema field in `plugin.json`
  for constraining the host Claude Code version was found; search
  confirmed the manifest schema lacks this property [9].
- No production framework or plugin architecture was found that
  implements automatic, graceful *degradation* (silent feature
  downscaling) when running on an outdated host. Every reviewed
  system implements either hard refusal (error and abort) or non-fatal
  warnings.

## Options

**Option 1: Trunk release with git tags and open lower bounds.**
A single `main` branch with no separate stable/beta branches. Releases
are git tags (`vX.Y.Z`). Dependent layers declare a bare minimum base
version (`base_min_version = "1.4.0"`) with no upper cap. A startup
hook checks the installed base version and halts with an explicit
remediation message (`Run /update-base`) if outdated.
- *Gives:* Minimal maintenance overhead for a solo maintainer; eliminates
  branch backporting; avoids dependency deadlocks caused by upper caps.
- *Costs:* Requires users to update their base when consuming newer
  layers; breaking changes in base must be accompanied by major
  migration guides.

**Option 2: Dual-channel release model (Stable and Edge).**
Two release lines: `main` (edge/nightly) and a `stable` branch (tagged
periodically). Layers pin to stable releases or declare SemVer ranges.
- *Gives:* Higher stability buffer for conservative users; mirrors
  enterprise release trains.
- *Costs:* High operational overhead for a single maintainer; requires
  cherry-picking bug fixes across branches; diverts time from core
  development to release bookkeeping.

**Option 3: Claude Code peer-plugin bundle.**
Package the base and layers as Claude Code plugins within a custom
marketplace, using the `dependencies` array in `plugin.json` to manage
layer-on-base version ranges.
- *Gives:* Leverages native Claude Code plugin installation tooling
  and automatic dependency resolution.
- *Costs:* Claude Code cannot enforce host CLI version requirements;
  a plugin cannot ship always-on instructions (`CLAUDE.md`); subject
  to the distribution friction documented in the baseline note.

## Relevance to this project

For `forge`, a single-maintainer project releasing rapidly, adopting
multi-channel release trains or complex version ranges would replicate
the distribution debt that forced BMAD and Superpowers to retreat
(as noted in `2026-10-03-one-tool-a-core-with-modules-or-several-tools.md`).
The evidence indicates that `forge` should adopt **Option 1**:

1. **Release rhythm:** Maintain a single trunk (`main`) and release
   via lightweight git tags adhering to SemVer 2.0.0 [14]. Avoid
   separate release channels (beta/nightly branches); trunk development
   with fix-forward patches is the proven sustainable pattern for solo
   maintainers [16].
2. **Version specification:** Have layers declare an open lower bound
   (a bare minimum base version, e.g. `requires_base: "1.2.0"`) rather
   than an upper bound or tight range, preventing the deadlock and
   maintenance traps documented by Schlawack [15].
3. **Mismatch handling:** When a layer detects that the installed base
   is below `requires_base`, it must **refuse** execution immediately
   with a clear, actionable error message (e.g., `Base version 1.1.0
   detected; this layer requires >= 1.2.0. Run git pull in the base
   directory to upgrade.`), following the consensus practice of VS Code
   [3], Cargo [5], and Terraform [1]. Never degrade silently.
4. **Host constraint workaround:** Because Claude Code's `plugin.json`
   lacks a host version field [9], enforce host CLI and base version
   checks through a pre-execution contract check in the shared
   initialization hooks or scripts rather than relying on the harness.

**Consult when:**
- Defining the manifest schema for separating the base framework from
  specialized operating layers.
- Designing the upgrade script or hooks that verify compatibility across
  cloned repositories.
- Deciding whether to create a `beta` or `nightly` release branch.

## Sources

[1] Terraform Block Settings, HashiCorp Developer, undated (structured
data), https://developer.hashicorp.com/terraform/language/settings/terraform;
primary; read in full via summarised fetch; original documentation.
Defines `required_version`, comparison operators, pessimistic `~>`
constraint, and immediate execution halt on version mismatch.

[2] Terraform v1.x Compatibility Promises, HashiCorp Developer,
undated (structured data),
https://developer.hashicorp.com/terraform/language/v1-compatibility-promises;
primary; read in full via summarised fetch; original documentation.
Details v1.x guarantees for language configuration, CLI automation
commands, and provider wire protocols.

[3] Extension Manifest Reference, Visual Studio Code Documentation,
Microsoft, undated (structured data),
https://code.visualstudio.com/api/references/extension-manifest;
primary; read in full via summarised fetch; original documentation.
Documents required `engines.vscode` property, SemVer caret ranges,
and marketplace/editor refusal on engine mismatch.

[4] Appendix 7: How Rust is Made and “Nightly Rust”, The Rust
Programming Language, Rust Project, undated (structured data),
https://doc.rust-lang.org/book/appendix-07-nightly-rust.html;
primary; read in full via summarised fetch; original documentation.
Specifies the 6-week train release model across Nightly, Beta, and
Stable channels and unstable feature gating.

[5] The Manifest Format: The `rust-version` field, The Cargo Book,
Rust Project, undated (structured data),
https://doc.rust-lang.org/cargo/reference/manifest.html; primary;
read partially (the `rust-version` section) via summarised fetch;
original documentation. Details bare version format for MSRV,
compilation refusal on mismatch, and `--ignore-rust-version` bypass.

[6] Go 1 and the Future of Go Programs, Go Authors, 2012 (byline),
https://go.dev/doc/go1compat; primary; read in full via summarised
fetch; original policy document. Defines Go's source-level backward
compatibility guarantees and narrow exceptions.

[7] Go Release History and Release Policy, Go Authors, undated
(structured data), https://go.dev/doc/devel/release; primary; read
in full via summarised fetch; original documentation. Specifies the
6-month major release cadence and N-2 support window.

[8] Go Modules Reference: go directive, Go Authors, undated
(structured data), https://go.dev/doc/modules/gomod-ref; primary;
read partially (the `go` directive section) via summarised fetch;
original documentation. Documents mandatory toolchain enforcement
and automated toolchain downloading starting in Go 1.21.

[9] Plugin Manifest Reference, Claude Code Documentation, Anthropic,
undated (structured data),
https://code.claude.com/docs/en/manifest-reference; primary; read
in full via summarised fetch; original documentation. Defines top-level
fields in `plugin.json` and verifies absence of host version field.

[10] Plugin Dependencies, Claude Code Documentation, Anthropic, undated
(structured data),
https://code.claude.com/docs/en/plugins/dependencies; primary; read
in full via summarised fetch; original documentation. Specifies peer
plugin dependencies, SemVer ranges against git tags, and bundles.

[11] package.json: engines, npm Documentation, npm, Inc. / GitHub,
undated (structured data),
https://docs.npmjs.com/cli/v10/configuring-npm/package-json; primary;
read partially (the `engines` section) via summarised fetch; original
documentation. Documents `engines.node` behavior: advisory warning
by default and refusal under `engine-strict=true`.

[12] Node.js Release Working Group, Node.js Foundation, 2026 (structured
data / repository metadata), https://github.com/nodejs/Release; primary;
read in full via summarised fetch; original policy document. Defines
Alpha, Current, Active LTS (30-month duration), and SemVer-major
deprecation enforcement.

[13] Kubernetes Deprecation Policy, Kubernetes Documentation, The Linux
Foundation, undated (structured data),
https://kubernetes.io/docs/reference/using-api/deprecation-policy/;
primary; read in full via summarised fetch; original documentation.
Details deprecation requirements for Alpha, Beta (9 months / 3 releases),
and GA APIs, alongside HTTP `Warning` headers.

[14] Semantic Versioning 2.0.0, Tom Preston-Werner, 2013 (byline),
https://semver.org/spec/v2.0.0.html; primary; read in full via
summarised fetch; original standard specification. Defines SemVer
MAJOR.MINOR.PATCH increment rules and public API guarantees.

[15] Semantic Versioning Will Not Save You, Hynek Schlawack, 2021-03-02
(byline), https://hynek.me/articles/semver-will-not-save-you/; primary;
read in full via summarised fetch; practitioner analysis. Explains why
upper version bounds on libraries cause dependency deadlock and
recommends open lower bounds.

[16] Release from Trunk, Trunk-Based Development, Paul Hammant /
Contributors, undated (structured data),
https://trunkbaseddevelopment.com/release-from-trunk/; primary; read
in full via summarised fetch; original documentation. Argues against
release branches and channels for high-throughput/solo projects,
advocating trunk release with fix-forward.

## Opened and not used

- https://developer.hashicorp.com/terraform/language: General landing
  page for Terraform language documentation, superseded by specific
  settings [1] and compatibility promises [2] pages.
- https://code.visualstudio.com/api/working-with-extensions/publishing-extension:
  Extension publishing overview, superseded by extension manifest
  reference [3].

## Search record

Queries run:
1. "Claude Code plugin manifest plugin.json dependencies"
2. "Terraform required_version language settings documentation"
3. "terraform language settings configuration block required_version"
4. "developer.hashicorp.com/terraform/language/settings OR developer.hashicorp.com/terraform/language URL"
5. "terraform compatibility promises v1.0 1.0"
6. "site:developer.hashicorp.com/terraform/language terraform block required_version URL"
7. "VS Code extension manifest package.json engines vscode minimum version"
8. "site:code.visualstudio.com/api/references/extension-manifest engines.vscode"
9. "code.visualstudio.com/api/references/extension-manifest"
10. "VS code engines.vscode mismatch install refuse error update version"
11. "site:doc.rust-lang.org release channels nightly beta stable stability"
12. "https://doc.rust-lang.org/book/appendix-07-nightly-rust.html OR https://doc.rust-lang.org/rustc release channels"
13. "site:doc.rust-lang.org/cargo rust-version minimum supported rust version"
14. "site:doc.rust-lang.org/cargo/reference/manifest.html the rust-version field"
15. "site:go.dev Go 1 and the Future of Go Programs compatibility promise release policy"
16. "site:go.dev/doc/go1compat Go 1 and the Future of Go Programs"
17. "site:go.dev/doc/devel/release Release History OR release policy major release cadence"
18. "site:go.dev/doc/modules/gomod-ref go directive minimum version"
19. "site:code.claude.com/docs plugin.json manifest minimum host version claude code"
20. "site:code.claude.com/docs plugin.json reference manifest fields"
21. "site:code.claude.com/docs/en/ plugin.json reference URL"
22. "site:nodejs.org Release schedule Current LTS Maintenance deprecation policy"
23. "site:github.com/nodejs/Release README.md release schedule"
24. "site:docs.npmjs.com/cli package.json engines npm warn error engine-strict"
25. "site:kubernetes.io/docs/reference/using-api/deprecation-policy/ Kubernetes Deprecation Policy"
26. "site:semver.org/spec/v2.0.0.html Semantic Versioning 2.0.0 MAJOR MINOR PATCH"
27. "single maintainer release channels OR version ranges overhead OR don't need OR burden" (disconfirming)
28. "Hynek Schlawack Semantic Versioning OR upper version bounds" (disconfirming)
29. "site:hynek.me Semantic Versioning Will Not Save You" (disconfirming)
30. "site:trunkbaseddevelopment.com release branches OR trunk-based development single maintainer OR small teams" (disconfirming)
31. "site:trunkbaseddevelopment.com/release-from-trunk/" (disconfirming)
32. "site:developer.hashicorp.com/terraform/language/v1-compatibility-promises Terraform v1.x Compatibility Promises"
33. "site:developer.hashicorp.com/terraform/language The terraform Block required_version URL"
34. "site:developer.hashicorp.com/terraform/language/settings/terraform required_version"

Pages opened: 18 pages fetched via summarised fetch; 16 cited as primary
sources [1-16] and 2 recorded as opened and not used.

Disconfirming query: The disconfirming query found strong, documented
practitioner and architectural arguments against release channels and
version ranges for solo maintainers: Trunk-Based Development documents
that multi-branch/channel pipelines impose severe cherry-picking and
backporting overhead on small teams, favoring single-trunk releases with
fix-forward patching [16]; Hynek Schlawack demonstrates that upper
version bounds (`<2.0`) in libraries cause dependency resolution
deadlocks and maintenance friction, arguing that libraries should
declare open lower bounds only [15].

Reason run ended: The card's stop rule was satisfied (three or more
written policies with a primary source each across Rust, Go, Node.js,
Kubernetes, and Terraform; the single-maintainer case documented with
primary sources [15, 16]; opening budget respected).
