---
date: 2026-11-14
project: forge
topic: the release rhythm of a base others stand on - cadence, stable and development lines, how a dependant names the base version it needs, what happens to a user without it, what is promised not to change
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-14-anvil-carrying-layers/06-release-rhythm
derived_from: research/2026-11-14-anvil-carrying-layers/00-plan.md, card 6; 2026-10-03-one-tool-a-core-with-modules-or-several-tools.md; web sources below
---

# A base others stand on releases on one line, names a minimum, and promises a deprecation window

## In short

Seven written policies were read at their publisher. They agree on
four things. A dependant names the base it needs most often as a
**minimum** (VS Code `engines.vscode`, Obsidian `minAppVersion`,
Terraform's advice for reusable modules); full ranges with an upper
bound are kept for the end of the chain, the application or root
configuration. A "stable channel" in the cheap form is not a second
maintained branch but **the same line delayed** (Claude Code's own
stable is "typically about one week old"; Rust's stable is the same
train six weeks later). What happens to a user without the needed
version differs by project and all three answers exist: refuse
(Terraform, Claude Code plugin dependencies), withhold the update
(VS Code), fall back to the newest compatible older version
(Obsidian), warn and go on (npm's engine check). What is promised is
a declared public surface and a deprecation window counted in
releases, never "nothing changes". For Claude Code itself the
finding is sharp: the plugin manifest lets a plugin declare ranges
on **other plugins** only; it has no field for the host version, no
release-channel concept and no deprecation state, and says so in its
own words. The disconfirming query found what was expected: written
arguments, one from a single maintainer's decision record, against
parallel maintained lines and against upper bounds; none against a
minimum-version declaration. Certainty: high for the Claude Code
pages (five arrived as full text), medium for the rest (read through
a summarising fetch, quotes short). The unexpected thing: a version
constraint of a Claude Code plugin is not checked against a local
copy, so the development loop is untouched by whatever range the
deployment loop uses.

## Question

#### Card 6: The release rhythm of a base others stand on
- **Question:** How do projects with dependent packages and users
  choose how often they release, how they keep a stable line apart
  from a development line, how a dependent piece says which version
  of the base it needs (a range, a minimum, a compatibility number),
  and what they do with a user who does not have it: refuse, warn,
  degrade? What do they promise not to change between versions?
- **Why it matters:** News of the framework is released daily today;
  the choice of the way changes with how often and how forcibly a
  user must update, and a layer needs a way to say which base it
  needs.
- **What would answer it:** The written release and versioning
  policies of projects with dependants, and the specifications of
  version ranges.
- **Where to look:** The versioning specifications in use; the
  release policies of platforms with plugins or providers that
  declare the host version they need (editors with packages,
  infrastructure tools with providers, language toolchains with
  channels); the plugin manifest of Claude Code for what it lets a
  plugin declare. Must turn up: a stable and a development channel,
  a minimum-host-version field, a deprecation policy.
- **Disconfirming query:** A search for arguments that a small
  single-maintainer project should not keep channels or ranges at
  all; expected: some, and their reasons.
- **Stop rule:** Three or more written policies with a primary
  source each, the single-maintainer case among them or recorded as
  not found; the opening budget.

The frame: a framework on Claude Code to be split into a general
base, the present framework as its first operating layer, later
layers and a user's own additions; the base maintained in one place
and every project updatable to its latest version; six candidate
ways compared by a development loop and a deployment loop; Claude
Code only.

The baseline to beat is the note of 2026-10-03 on how ecosystems
divide the whole. It established that "modules declare the core
version they need" is consensus (Spec Kit's `requires:
speckit_version` range, Claude Code plugin dependencies, BMAD's
stable and bleeding-edge channels with per-module pinning) and
recommended, as its fifth point, to "state what does not change
between versions and have packages declare the version they need".
It did not say which form of declaration, what a channel costs, what
is done with a user who lacks the version, what a deprecation window
looks like, or what the Claude Code manifest can and cannot declare
about the host. This note answers those.

## Key findings

**F1. The Claude Code plugin manifest has no field for the host
version; a plugin can declare versions of other plugins only.**
[single source, vendor documentation of its own product, read in
full] The manifest's field table lists `name`, `version`,
`dependencies` and the component keys; none names a Claude Code
version [2]. Host requirements appear only as prose notes per
feature ("Requires Claude Code v2.1.265 or later" [1]) and one
consequence is stated outright: "If you declare `options` on any
field, users on Claude Code versions before v2.1.271 can't load the
plugin" [2]. An unrecognised top-level key "is stripped and the
plugin loads", with a validator warning; a free-form `metadata`
object exists that "Claude Code doesn't read" [2]. So a
minimum-host-version field must turn up for the card and does not:
for Claude Code it is recorded as absent. A layer's own key under
`metadata` would be carried but enforced by nobody but the layer's
own code (the second half is this note's inference).

**F2. Between plugins, Claude Code offers full semantic-version
ranges, resolved against git tags, and refuses or disables on a
miss.** [single source, vendor documentation, read in full] A
dependency entry takes a range "such as `~2.1.0`, `^2.0`, `>=1.4`,
or `=2.1.0`", installed "at the highest git tag that satisfies this
range"; tags are named `<plugin-name>--v<version>` [1]. With no
constraint, "a dependency moves to each new release its marketplace
publishes" and "If that release renames an MCP tool your plugin
calls, your plugin breaks for everyone who updates" [1]. On a miss
the behaviour is refusal, in three shapes: no tag in range, "the
install fails"; ranges of two plugins that do not overlap,
"Installing plugin B fails with a `has conflicting version
requirements` message"; an installed copy outside the range, "the
dependent plugin stays disabled" and the list shows `Requires ...
~2.1.0, installed 3.0.0` [1]. There is no warn-and-continue and no
fallback to an older dependant. Pre-releases are excluded from a
range unless opted into [1].

**F3. Claude Code says of itself that it has no release-channel
concept for plugins and no deprecation state.** [single source,
vendor documentation, read in full] "Claude Code has no
release-channel concept, and one marketplace serves one version of
each plugin at a time"; the documented workaround for "stable and
early-access tracks" is two marketplaces with different names
"whose entries point at different refs of the same plugin" [3].
"Mark a plugin deprecated: there is no deprecation state"; the
nearest option is removing the entry and mapping its name to `null`
in an append-only `renames` map [3]. The one built-in marker of
instability is the manifest's `experimental` container, for keys
"whose manifest shape may still change" [2].

**F4. How often a plugin's user is moved is the author's choice of
one string, and nobody is forced.** [single source, vendor
documentation, read in full] A set `version` "keeps every user on
the cached copy until its author changes the string, however many
commits they push"; leaving `version` out of manifest and entry
makes users "track your commits instead" [3][4]. Background
auto-update is "off for your marketplace by default, and
`marketplace.json` has no field to turn it on"; a user or an
administrator turns it on [3]. Without it, changes arrive when the
user runs the update command [3]. A daily release rhythm is
therefore compatible with the mechanism either way (bump daily, or
omit the version); what a range adds is the duty to tag every
release a dependant may need to resolve [1] (the last clause is
this note's inference from the tag rule).

**F5. The host's own two channels are one line and a delay, not two
maintained branches.** [vendor documentation, read in full; Rust
through a summarising fetch] Claude Code: `"latest"`, the default,
"receive new features as soon as they're released"; `"stable"`, "a
version that is typically about one week old, skipping releases
with major regressions" [5]. Rust: three channels on a train,
"Rust releases every six weeks, like clockwork", unstable features
"behind a feature flag" usable on nightly only, and "The Rust
project supports the most recent stable version", each version
"supported for six weeks" [9]. In both, stable is a later point of
the same history and nothing is back-ported to an older stable as a
matter of policy. Contrast, a line that is maintained apart: Django
keeps feature branches with security fixes for up to three years
[8]. The host also shows the cost on the dependant's side: "A
newly launched model can require a Claude Code version newer than
the stable channel serves" [5].

**F6. Hosts with a real minimum-host-version field use a minimum,
and differ in what the user without it gets.** [emerging across
vendors; vendor documentation through a summarising fetch, quotes
short] VS Code: `engines.vscode`, where "`^1.8.0` means that your
extension is compatible with VS Code `1.8.0` and onwards", and the
store withholds: "your new extension version will only be available
on VS Code `>=1.9.0`" [6]. Obsidian: `minAppVersion` in the
manifest plus `versions.json`, a map of plugin version to the app
version it needs, so an older app gets the newest plugin release
that still fits; "You only need to update `versions.json` if you
change the `minAppVersion`" [7]. Terraform: `required_version` and
provider constraints with seven operators, `~>` allowing "only the
right-most version component to increment"; when unmet, Terraform
"does not proceed with any `terraform plan`, `terraform apply`, or
`terraform state` operations" [10]. Warn-and-continue exists too:
on a Node.js older than a package's declared engine, "npm by
default prints an `EBADENGINE` warning and completes the install
rather than failing" [5] (a vendor's remark about its own package
on npm, not npm's specification). Refuse, withhold, degrade and
warn are all in production use; no source read ranks them.

**F7. Where a policy says which form of declaration belongs where,
the reusable piece gets a minimum and the end of the chain gets the
upper bound.** [contested; one vendor's best-practice text and one
practitioner's essay, both through a summarising fetch] Terraform:
"Reusable modules should constrain only their minimum allowed
versions of Terraform and providers, such as `>= 0.12.0`", while
"Root modules should use a `~>` constraint to set both a lower and
upper bound" [10]. A Python maintainer's essay argues the same from
the other side: "Don't ever pin major versions, unless you know
they're broken", because a cap in a library is passed on to its
users and "there's no practical way for them to remove your pin"
[11]. Contradicted in practice by [1], whose own examples use `~`
and `^` ranges on a plugin others depend on, and by the Spec Kit
range of the baseline note; neither of those states a reason
against a bare minimum.

**F8. The versioning specification defines numbers and duties, not
ranges.** [consensus, standard; through a summarising fetch]
Semantic Versioning requires that software "MUST declare a public
API", says "Major version zero (0.y.z) is for initial development",
and that the minor number "MUST be incremented if any public API
functionality is marked as deprecated" [12]. Caret and tilde ranges
are not in it; they are conventions of package managers, and Claude
Code names the one it follows by linking the range grammar of
Node's semver package [1]. Claude Code's own `version` field is "A
version string, not checked against semver" [2].

**F9. A deprecation policy, where written, is a window counted in
releases with a warning inside it.** [emerging; two project
policies and the standard, through a summarising fetch] Django: a
feature deprecated in `A.x` "will continue to work in all `A.x`
versions ... but raise warnings", removal arranged so that
"deprecations are done over at least 2 feature releases"; from its
2028 scheme, deprecated in `YYYY`, working with warnings in
`YYYY+1`, removed in `YYYY+2` [8]. Semantic Versioning's answer is
a minor release "with the deprecation in place" before the major
that removes [12]. Rust promises more: "you should never have to
fear upgrading to a new version of stable Rust" [9]. VS Code's
deprecation of an extension is a visible mark and a Migrate button,
and "will not automatically migrate or uninstall" [6]. Django also
shows a project changing its rhythm in the open: feature releases
"every eight months or so" up to 6.2, then "One feature release
will be made each calendar year" with year numbers and no separate
long-term line [8] (as the page stood on 2026-11-14).

**F10. The single-maintainer case is on record: one line, latest
only, with the reason written down.** [single source, a project's
own decision record through a summarising fetch; supported by one
practitioner essay] A solo-maintained test tool recorded on
2023-06-28 the decision that only the latest major version is
maintained and that a new major may break, because maintaining
several versions is costly for one person; changes and migration
notes are still written, and the decision is to be revisited if
adoption or the number of maintainers grows [13]. The essay of
[11] states the general case: "Most open source projects don't
have the capacity to maintain multiple major branches."

## Unexpected

A version constraint of a Claude Code plugin is not checked in the
development loop. With both plugins loaded from local folders,
"the local `plugin.json` doesn't need a `version` either, because a
version constraint isn't checked against a local copy" [1], and a
plugin loaded in place from a marketplace added by local path
"loads your current files at every session start, whatever its
version string says" [3]. Whatever range discipline the deployment
loop takes, it costs the development loop nothing under the plugin
candidate.

The card assumes a layer can say which base it needs through the
plugin manifest. [1] and [2] say it can only where the base is
itself a plugin, and that the base's always-on instruction file
cannot be in it: "A `CLAUDE.md` at the plugin root isn't loaded as
context" [2]. For any candidate in which the base is not a plugin,
the declaration and its check have to be the base's own (a file the
layer carries and a script of the base that reads it); no mechanism
of the harness does it. This is a lead for the cards on the
candidates, not a conclusion here.

The host under the base moves fast and declares its own minimums
feature by feature. The five Claude Code pages read name nine
different host versions as feature minimums, from v2.1.238 to
v2.1.324 [1][2][3][4], and the host offers an organisation a hard
gate the plugin author does not have: `requiredMinimumVersion` and
`requiredMaximumVersion` "make Claude Code refuse to start outside
a version range" [5]. A base on this host has two version questions,
not one: which base a layer needs, and which host the base needs.

## Not found

- No manifest field, in Claude Code, for the host version a plugin
  needs; looked for in the manifest reference [2] and the
  dependencies page [1]. The settings reference behind
  `requiredMinimumVersion` was not opened.
- No measurement of how often users of any of these systems
  actually update, or of breakage with and without ranges; no
  source read gives a figure.
- No source arguing that a single maintainer should declare no
  minimum version at all, and none arguing against a delayed stable
  pointer; the arguments found are against parallel maintained
  lines and against upper bounds (Search record).
- No written release-cadence or backport statement for curl on the
  page opened [14]; its release procedure page was not opened.
- npm's own specification of the engine check and Cargo's
  `rust-version` field were not opened; the npm behaviour above
  rests on [5] alone.
- Kubernetes' deprecation policy and Node.js' release schedule were
  not opened; the deprecation finding rests on [8], [9] and [12].

## Options

**A. One line, a minimum, no channel.** The base is released as
often as it changes; a layer carries one number, the lowest base it
was made against; the base checks it. No second pointer, no tags
beyond the releases themselves.
- Gives: what F6, F7 and F10 describe as the cheapest working form;
  nothing to maintain twice; fits a daily rhythm.
- Costs: a minimum says nothing when the base later removes
  something the layer uses; that gap is closed only by a
  deprecation window (F9) or by tests of the layer against the new
  base.

**B. One line with a delayed stable pointer, and a minimum.** As A,
plus a branch or tag `stable` moved to a release that has stood for
a soak period; users choose which they follow.
- Gives: F5's form, the one the host itself uses; strangers get a
  line that skips a bad day without the author back-porting
  anything. In plugin terms it is two marketplaces at two refs [3].
- Costs: one more thing to move at a release; a layer may need
  something newer than stable serves, the cost [5] names for the
  host.

**C. Full ranges between tagged releases.** The base and each layer
are plugins; a layer declares `^N` on the base; every release of
the base is tagged.
- Gives: the harness resolves, intersects and refuses by itself
  (F2); a breaking major cannot reach a layer that has not said it
  is ready.
- Costs: only where the base is a plugin, which its always-on file
  cannot be (Unexpected); a tag per release under a daily rhythm; a
  refusal with no fallback for the user; and the upper bound that
  F7's sources advise against in a reusable piece.

**D. No versions: track commits.** `version` omitted, every user on
the newest commit at the next update.
- Gives: the least ceremony; it is what a clone that pulls already
  is.
- Costs: the breakage [1] describes in its first paragraph, for
  everyone who updates, with nothing to tell a layer and a base
  apart.

What to do with a user below the minimum is a separate choice on
top of A to C: refuse (Terraform, Claude Code), withhold the new
layer (VS Code), fall back to the newest layer that fits (Obsidian,
at the price of a version map kept by hand), or warn (npm).

## Relevance to this project

The recommendation, as this note's own inference from the findings:
take A now and keep B ready for the day strangers follow the base.

- A layer names a **minimum** base version, not a range. It rests
  on F6 and F7 (the form hosts with a real field use, and the one
  advised for the reusable piece) and on F10 (one maintainer, one
  line). It is chosen against C's caret ranges because their upper
  bound buys safety only if majors are cut honestly and old majors
  are kept alive, which F10 and [11] say one maintainer does not
  do.
- The check is the base's own, in a script, since F1 shows the
  harness has no host-version field and the Unexpected section
  shows the plugin range is unavailable wherever the base is not a
  plugin. This holds for every candidate of the frame and decides
  between none of them.
- For the user below the minimum, **refuse a write and say the one
  command that updates** follows the two closest precedents
  (Terraform stops its operations; Claude Code disables the
  dependant). Obsidian's fallback is kinder and costs a map kept by
  hand at every change of the minimum; a warning alone is what the
  framework's present practice of stopping an unmigrated project
  already rejects. This is inference, not a finding.
- The daily rhythm need not change for the mechanism's sake (F4):
  nobody is forced, updates are pulled. What a daily rhythm cannot
  carry is a daily change of **shape**. The promise worth writing
  is F9's kind: name the surface layers may rely on, mark the rest
  as the harness marks `experimental`, and keep a removed thing
  working with a warning for a stated number of releases. The
  baseline note already asked for this statement; this note adds
  that every policy read counts the window in releases, so under a
  daily rhythm the window has to be counted in something slower
  than a release (inference).
- A stable line, when wanted, is a pointer moved after a soak
  period, F5's form, never a second branch with back-ports.

What is uncertain: seven of the fourteen sources came through a
summarising fetch and their quotes are short; the single-maintainer
case rests on one small project's record and one essay; nothing
read measures outcomes.

Consult when: the candidates of the split are compared on the
deployment loop; a layer's header or manifest is designed and the
question is which version field it carries; a first release of the
base to strangers is prepared and a stable line is considered; a
change of shape in the base is planned and the question is how long
the old shape must keep working; the plugin candidate is weighed
and the question is what its manifest can declare.

## Sources

1. "Plugin dependencies", Claude Code documentation, Anthropic;
   undated living documentation, read 2026-11-14;
   https://code.claude.com/docs/en/plugin-dependencies.md ; primary
   (vendor on its own product); read in full (the page arrived as
   full text); original.
2. "Plugin manifest reference", Claude Code documentation,
   Anthropic; undated, read 2026-11-14;
   https://code.claude.com/docs/en/plugins-reference ; primary; read
   in full; original.
3. "Host and maintain a marketplace", Claude Code documentation,
   Anthropic; undated, read 2026-11-14;
   https://code.claude.com/docs/en/plugins/host-marketplace.md ;
   primary; read in full; original.
4. "Plugin loading reference", Claude Code documentation,
   Anthropic; undated, read 2026-11-14;
   https://code.claude.com/docs/en/plugins/loading.md ; primary;
   read in full; original.
5. "Advanced setup", Claude Code documentation, Anthropic; undated,
   read 2026-11-14; https://code.claude.com/docs/en/setup ; primary
   for the host's channels and version settings, secondary for the
   remark on npm's engine warning; read in full; original.
6. "Publishing Extensions", Visual Studio Code documentation,
   Microsoft; undated, read 2026-11-14;
   https://code.visualstudio.com/api/working-with-extensions/publishing-extension
   ; primary; summarised fetch (sections on compatibility,
   pre-release extensions, deprecation; short verbatim fragments);
   original.
7. "Versions", Obsidian developer documentation; undated, read
   2026-11-14; https://docs.obsidian.md/Reference/Versions ;
   primary; summarised fetch (whole page, one verbatim sentence);
   original.
8. "Django's release process", Django documentation, development
   version; undated, read 2026-11-14;
   https://docs.djangoproject.com/en/dev/internals/release-process/
   ; primary; summarised fetch (cadence, deprecation policy,
   supported versions, numbering; verbatim passages); original.
9. "Appendix G: How Rust is Made and 'Nightly Rust'", The Rust
   Programming Language; undated, read 2026-11-14;
   https://doc.rust-lang.org/book/appendix-07-nightly-rust.html ;
   primary (the project's own book); summarised fetch (channels,
   train, feature flags, maintenance; short verbatim quotes);
   original.
10. "Version constraints", Terraform language documentation,
    HashiCorp; undated, read 2026-11-14;
    https://developer.hashicorp.com/terraform/language/expressions/version-constraints
    ; primary; summarised fetch (operators, best practices, unmet
    constraint, pre-releases; short verbatim quotes); original.
11. "Semantic Versioning Will Not Save You", Hynek Schlawack,
    2021-03-02 (byline, as the fetch reported it);
    https://hynek.me/articles/semver-will-not-save-you/ ; secondary
    (a practitioner's argument, the maintainer of several Python
    libraries); summarised fetch (short verbatim quotes); original.
12. "Semantic Versioning 2.0.0", semver.org; undated specification,
    read 2026-11-14; https://semver.org/ ; primary (the standard);
    summarised fetch (items 1, 4, 5, 7, 8 and four FAQ answers;
    short verbatim quotes); original.
13. "0012 No backwards compatibility", architecture decision record
    of the testy project, dated 2023-06-28 in the record;
    https://github.com/ngarbezza/testy/blob/main/doc/decisions/0012-no-backwards-compatibility.md
    ; primary (a project's own decision); summarised fetch (the
    whole record, paraphrased by the fetch, no verbatim quote
    taken); original.
14. "Version numbers", curl documentation; undated, read
    2026-11-14; https://curl.se/docs/versions.html ; primary;
    summarised fetch (whole page); original. Listed for Not found
    only.

## Opened and not used

- [14] curl "Version numbers": opened for a small-team policy of
  one line and no back-ports; the page states numbering only, no
  cadence, no support statement. Cited under Not found alone.

## Search record

Queries, in order:
1. Claude Code plugin manifest, version, dependencies, minimum
   host version field.
2. Single maintainer, no release branches or LTS, argument against
   version ranges and upper bounds (the disconfirming query, first
   run).
3. Obsidian plugin manifest `minAppVersion`, `versions.json`.
4. Solo maintainer, "only the latest release is supported", no
   backports, why (the disconfirming query, second run).

Pages opened, fifteen openings: [1], [2], [7], [12], [3], [4], [5],
[6], [10], [8], [9], [11], [14], [13]; fourteen pages, the count of
fifteen including one page of the first batch read alongside. Five
arrived as full text ([1] to [5]); the rest as a small model's
summary with short verbatim quotes, and are marked so.

What the disconfirming query found: some, as expected. The first
run returned no essay that says "a single maintainer should keep no
channels or ranges"; it led to [11], which argues that most
projects cannot maintain several major branches and that libraries
should not cap their dependencies. The second run led to [13], a
single maintainer's written decision to keep one line and fix only
the latest, with capacity as the reason, and to two further pages
with the same policy that were not opened (a server project citing
limited maintenance time; a logging daemon moving to latest-only)
and are not cited for content. Nothing found argues against a
minimum-version declaration or against a delayed stable pointer.
The result narrows the card's expectation: the reasons are against
parallel lines and upper bounds, not against channels or version
declarations as such.

The run ended on both parts of the stop rule at once: more than
three written policies with a primary source each (Claude Code,
VS Code, Obsidian, Terraform, Django, Rust, Semantic Versioning),
the single-maintainer case among them ([13]), and the opening
budget spent.
