---
date: 2026-11-21
project: forge
topic: the description of an interface after the first build, its change, variation, reach and versioning
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-19-after-the-first-build
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 19; no known note named by the card; web sources below
---

# How a description of an interface is changed, kept, varied and versioned after the first build

<!-- Shape: templates/research.md -->

## In short

The systems opened answer the four parts of the card unevenly. A
change is read as text in two ways: as git's difference on a branch,
or as a delta that is a document of its own (requirements added,
modified, removed) which a command later merges into the standing
specification; one format for the visual identity of a design system
ships a structural difference of its tokens. Changes made during the
build come back by a person's decision in every kit opened: three
document only a check that reports drift or a button that marks
finished tasks; one, found in the second round, documents a named
procedure in which the agent that builds raises an amendment and the
developer confirms it; one vendor claims a button that rewrites the
specification from the code. A shared element varies in three grades:
a variant declared in its definition, an override at the place of use
limited to a declared surface and keyed by the name of the part, and
detachment, which ends the link. The reach of a change is shown only
by the design tool, to the user of the element when the update
arrives and to its owner as usage per file; of the text kits one has
a fixed checklist of artefacts to look at again, the others and the
block system's pages show none. Versioning is semantic versioning
with a declared table of bumps in a code library, publication with a
free description in the design tool, and in one kit a log of versions
inside the specification with the cause of each. This is sure as a
reading of documentation (twenty-three pages in two rounds, every
quote checked against the page text) and unsure as a statement about
practice: the one case with figures concerns formal specifications,
where ten weeks of work did not bring code and specification to
match. The disconfirming query, run as worded in the second round,
was borne out with one refinement: bringing changes back is done by
hand, and the best documented form of "by hand" is a proposal of the
agent that a person confirms. For overrides it returned the owners'
rules of containment, not reports of chaos, and the practice reports
tried did not open. Unexpected: the design tool, the block system and
that system's issue tracker all attach an override to the name of a
part inside the shared element, and the tracker says outright that
renaming the part can break the link.

## Question

The frame of the card, verbatim:

> A framework carries an idea down a chain of versioned Markdown
> documents kept in git: what is wanted and why, then business
> requirements, a solution design and user stories. A human works
> each document with an AI agent: the agent asks, proposes and
> writes, the human decides. Nothing is implemented there; the
> documents are handed on to be built. Its author wants the same for
> the user interface and the user experience of an application, and
> no such document exists yet: an AI agent reads the documents
> above, asks what it lacks and proposes a description of the
> interface in text; a human tunes the proposal and sees it; the
> description goes, with the other documents, to a build stage (a
> human developer, an AI coding agent, or both), and the cycle runs
> again when the interface changes. The author of a description is
> one person working end to end in a small project and a UX/UI
> specialist in a company. The targets are the web, the mobile web,
> native mobile and the desktop. Before anything is designed, a wide
> research asks how this is done elsewhere: which standards exist,
> what practice does, what the options are. One idea heard from
> practice is to be tested, not assumed: every element of a screen
> (a search field, say) has a small definition of its own in
> Markdown that carries its function, and a page definition names
> which elements it holds and where they stand. This card is one of
> twenty-two. The first card, already answered, found no synthesis
> across the field and a vocabulary that differs by community; the
> search words it gave are carried in the card below. In the sources
> the word "design" stands for three things (the design of the
> interface held in a design tool, the technical design between
> requirements and tasks in spec-driven kits, the visual identity of
> a design system): say which you mean. The other cards ask about
> the description of one screen, the user's paths, the structure
> above the screens, formal languages and standards, components in
> design systems, pages composed of defined blocks, behaviour of the
> whole application, descriptions written for an agent that builds,
> measured studies of models and interfaces, previews, design tools,
> the agent that proposes a description, declarative interface
> languages, the platforms, accessibility and wording, the place in
> the process, how a proposal is judged, where textual descriptions
> failed, what a description cites from other documents, its change
> after the first build, and automated testing of interfaces. Answer
> your own card and leave the others' questions to them.

The card, verbatim:

**Card 19: The description after the first build**

- **Question:** How is a description of an interface changed and kept
  once the product exists: how is a change to it read and reviewed as
  a difference in text, how do changes made during the build get back
  into it, how do systems of shared definitions handle a screen that
  needs a variation of a shared element (variants, overrides,
  instances) and show which pages a change to a shared element
  touches, and how are such definitions versioned?
- **Why it matters:** the cycle runs again whenever the interface
  changes, and the idea of a definition per element stands or falls
  on variation and on the reach of a change.
- **What would answer it:** the documentation of systems that keep
  shared definitions, and of spec-driven kits, on how a change is
  made and carried.
- **Where to look:** design systems on versioning, breaking changes
  and variants; design tools on components, instances and overrides;
  block and section systems on variations; spec-driven kits on
  changing a specification after code exists and on bringing changes
  of the code back into it. Search words from card 1: "spec-driven
  development", "spec-first", "spec-anchored", "spec-as-source",
  "constitution", "steering files", "EARS", "DESIGN.md". Primary
  artefacts in public repositories (schemas, component and page
  files, agents' rules and prompt files, the schemas of servers for
  design tools, issue trackers) before commentary about them.
- **Disconfirming query:** "keeping specification in sync with code
  fails", "design system overrides chaos"; expected: bringing changes
  back is done by hand or not at all.
- **Stop rule:** nothing new from a differently worded query and
  every route has a primary source; ten to fifteen pages opened.

Known items: none; the card names no known note of the project.

The baseline the note must beat is what a practitioner would say
unasked: keep the description in git and read its difference, version
shared components by semantic versioning, use variants and overrides
as the design tool does, and update the specification by hand when
the code moves. The note beats it only where it names the mechanism
in a primary source, says where that mechanism stops, and shows what
no system opened does.

## Key findings

How the findings were read: all twenty-three pages came through a
summarising fetch, which is a tertiary reading. Every quoted passage
below was afterwards checked against the text of its page by a
script, and a statement that a page does not say something is marked
"checked" where the page text was searched for it and "summarised
fetch" where it rests on the fetch alone. What the second round
added or changed is marked "(second round)"; the Search record says
why there was one. The word "design": in [2][3][5] `design.md` is the
technical design between requirements and tasks; in [4] DESIGN.md is
the visual identity of a design system; in [8][11][12][13] it is the
design of the interface held in a design tool.

F1. **A change to a text specification is read as a difference in two
ways in the kits opened: as git's difference on a branch, or as a
delta that is itself a document.** [emerging; vendor documentation of
two kits] In spec-kit, specifications are "expressed and versioned,
created in branches, and merged" (The SDD Workflow in Practice), and
`/speckit.specify` creates a branch and a `specs/[branch-name]/`
directory for each feature [1]; the document describes no review of
that difference, and the words "pull request" do not occur in it
(checked). In OpenSpec a change is a folder with a proposal, a
design, tasks and delta specs; a delta spec lists requirements under
`## ADDED Requirements`, `## MODIFIED Requirements` and
`## REMOVED Requirements` (Delta Specs) [2], and the commands page
names a `RENAMED` section as well [3]. A modified requirement is
restated whole with the old value as a note, "(Previously: 30
minutes)" in the page's example [2]. The reasons given: "A delta
shows exactly what's changing. Reading a full spec, you'd have to
diff it mentally against the current version." and "Reviewers see the
change, not the unchanged context." (Why Deltas Instead of Full
Specs) [2]. At the end of a change, "Each delta spec section
(ADDED/MODIFIED/REMOVED) is applied to the corresponding main spec"
and "The change folder moves to `changes/archive/` with a date prefix
for chronological ordering." (The Archive Process) [2]: the record of
changes is the dated archive of change folders, each with its
proposal.

F2. **One format for the visual identity of a design system ships a
structural difference of its own.** [single source; vendor
documentation of a format at version alpha] DESIGN.md holds design
tokens as YAML and the rationale as prose: "The tokens are the
normative values. The prose provides context for how to apply them."
(File Structure) [4]. Its command `diff` is to "Compare two DESIGN.md
files and report token-level changes." (CLI Reference): the example
output lists, for colors, typography, rounded, spacing and
components, the names `added`, `removed` and `modified`, the counts
of the linter's findings before and after, and `"regression": false`;
the command ends with "Exit code `1` if regressions are detected
(more errors or warnings in the "after" file)." [4]. Getting Started
says the command detects "token-level and prose regressions"; the
example shows no entry for prose, so what a regression of prose is
the README does not show. The difference covers the structured half
of the file only.

F3. **A change found during the build comes back into the
specification by a person's decision in every kit opened: three
document only a check or a mark of status, one a named procedure of
amendment in which the agent detects and proposes and the developer
confirms, and one vendor claims a button that rewrites the
specification from the code.** [emerging; the documentation of four
kits, one vendor claim, one practitioner analysis, one preprint; no
measurement behind any of them] Changed in the second round: the
first round, with three kits read, found no documented way back at
all; [16] and [17] are the new reading. The documented direction
remains specification, then code.
- Kiro (page updated 25 September 2026): to iterate, "Either modify
  the `requirements.md` file directly or initiate a spec session",
  ask for the design to be updated, then "Navigate to the tasks.md
  file and choose Sync Files. This will create new tasks that map to
  the new requirements." (How do I iterate on my Feature Specs?).
  Against existing code, Sync Files, or the request "Check which
  tasks are already complete", has the result that "Kiro will
  automatically mark completed tasks" (What if some tasks are already
  implemented?) [5]. What comes back from the code is the state of
  the tasks, not the content of requirements or design.
- OpenSpec: `/opsx:update` revises the artefacts of a change,
  "Planning artifacts only - it never edits code.", and "If the
  change was already implemented, follow up with `/opsx:apply` so the
  code matches the revised plan". `/opsx:verify` is to "Validate that
  implementation matches your change artifacts.", "Reports issues
  categorized as CRITICAL, WARNING, or SUGGESTION", "Does not block
  archive, but surfaces issues" and "Can reveal drift between
  artifacts and implementation" [3]. Of the implementation step the
  concepts page says only "Update artifacts as you learn" [2].
- spec-kit states the way back as a principle, "Production reality
  informs specification evolution" (Bidirectional Feedback), and
  "Production metrics and incidents don't just trigger hotfixes—they
  update specifications for the next regeneration." (The SDD Workflow
  in Practice) [1]. The document describes three commands that create
  artefacts (`/speckit.specify`, `/speckit.plan`, `/speckit.tasks`)
  and names `/speckit.analyze`; none is described as changing an
  existing specification after the build (the commands checked, the
  reading of each a summarised fetch).
- (second round) DevSquad Copilot, a kit published under Microsoft's
  organisation on GitHub, on a page last updated 20 November 2026
  that calls the project "under active development and subject to
  breaking changes", names the event: "When the two disagree, the
  framework treats it as a first-class event, not a deviation to
  hide." Its loop: the agent that implements "compares the emerging
  model against the current spec and ADRs" and returns a flag naming
  the affected section, the original statement and the observed
  reality; "The coordinator pauses the task instead of proceeding.";
  "The developer confirms, rejects, or defers."; then "The amendment
  is scoped: only the affected user story, conformance case, or ADR
  section is touched.", and the tasks are made again (The Amendment
  Loop). A rule says when: an amendment is raised where the discovery
  changes behaviour a user sees, the shape of stored data, the text
  of a requirement, the boundary of a story or a ranked priority, and
  not for internal structure, naming or the choice of a library (When
  to Amend). "It is not automatic. The developer confirms every
  amendment." (What This Is Not). The page names its own limits:
  other artefacts are only flagged, "The refine agent does not edit
  these artifacts in amendment mode."; "Reject and defer allow
  continuation under a known-stale spec"; "Multi-developer
  concurrency is not guarded." (Known Limitations) [16]. This is a
  discovery raised by the agent while it builds; a hand edit of the
  code made outside the kit is not treated on the page (the agent's
  reading of the page text).
- (second round) A vendor's blog on its own product (6 June 2026)
  claims the reverse direction on demand: "Remy provides a sync
  button that reconciles changes in either direction", "Click sync,
  and Remy updates the spec to reflect what the code now does.", and
  advises against leaning on it: "But the recommended discipline is
  always sync spec → code. Treat the spec as the reset point." [17].
  A vendor claim: the product's documentation was not opened, and the
  page states no limit of the reverse direction (summarised fetch).
- A practitioner's comparison of three kits (15 October 2025) sorts
  them by whether "The spec is kept even after the task is complete"
  and finds spec-kit "still what I would call spec-first only, not
  spec-anchored over time"; a third kit, in private beta then, "is
  the only one of these three tools that explicitly aspires to a
  spec-anchored approach", marks generated code "// GENERATED FROM
  SPEC - DO NOT EDIT", and its command line was used by the author to
  reverse engineer a specification from an existing file [6]. That
  kit's own documentation was not opened.
- A preprint (technical report, 30 January 2026, not peer reviewed)
  names the failure, "Specification rot affects spec-anchored
  approaches when teams fail to update specs as code changes.", and
  its remedy, "automated enforcement through tests that fail when
  spec and code diverge" (Common Pitfalls) [7]; it gives no data for
  either.

This agrees with what the disconfirming query expected, by hand or
not at all, with one refinement: in [16] "by hand" is a proposal of
the agent that a person confirms, and [17] is a claim of more.

F4. **What the specification is after the build differs by kit: the
record of one change, ending with it, or a standing text of current
behaviour into which changes are merged.** [contested; vendors'
documentation against a practitioner's reading] In OpenSpec the main
specs "are the source of truth — they describe how your system
currently behaves" and changes "live in separate folders until you're
ready to merge them" (The Big Picture) [2]. spec-kit makes a branch
and a numbered directory for each feature [1] and speaks of living
specifications, "pivots become systematic regenerations rather than
manual rewrites" [1]; contradicted by [6], which reads the branch per
specification as a specification that lives "for the lifetime of a
change request, not the lifetime of a feature". Kiro is "mostly
spec-first" for [6] in October 2025, while Kiro's own page as updated
in September 2026 calls its Feature Specs "designed for continuous
refinement" [5]; whether the judgement of [6] holds for the kit as
documented eleven months later was not established. The same source
names the cost of reviewing such text: the files of one kit "were
repetitive, both with each other, and with the code that already
existed", "To be honest, I’d rather review code than all these
markdown files.", and "An effective SDD tool would have to provide a
very good spec review experience." (Reviewing markdown over reviewing
code?) [6]. One practitioner's experience, not a measurement.

F5. **A design tool lets a use of a shared element differ in three
grades, and the grade decides what survives a change.** [single
vendor; its documentation] In Figma an instance of a component may be
overridden in named properties: "Figma lets you change text, fill,
stroke, and effect properties.", besides swapping nested instances
and renaming a layer; under "You can’t override:" stand the order of
layers, their position, their constraints and the bounds of text
layers. Beyond that the link is cut or the definition changed: "For
changes like reordering layers, you must detach the instance, or make
the changes directly to the main component" [8]. The third grade is
the variant, chosen on the instance and declared with the component
(the vendor's page on variants was not opened). A local change is
carried across a switch by the name of the layer: "Figma attempts to
preserve your changes when you select a different variant or swap
between instances." and "The layer names of the current instance and
the variant or instance you’re selecting must match." (Change
preservation) [8]. A local change becomes the shared one only within
one file: "You can only push changes if the main component is in the
same file as the instance.", and "It’s not possible to push changes
to components in another file, including published libraries." [8].
What happens to an override when the main component itself is changed
and the update accepted is stated neither on [8] (summarised fetch)
nor on [12], where the word "override" does not occur (checked).

F6. **A block system draws the same line in its definitions: a
variation is a named set of initial attributes over one block, an
override a named slot of content in a shared pattern.** [single
project; its handbook, its developer blog, a developer note and its
issue tracker] Changed in the second round in its limits and in what
the tracker says of names. In WordPress "A block variation differs
from the original block by a set of initial attributes or inner
blocks.", while a block style "just applies a CSS class to the
block"; a variation's `attributes` are "Values that override block
attributes", and without `isActive` the editor cannot tell an
instance of the original block from one of a variation (Using
isActive) [9]. What happens to blocks already placed when a variation
is redefined the page does not say (summarised fetch). A synced
pattern is one shared definition, "all pattern instances are kept
synchronized whenever you make additional changes"; with overrides,
"Users can only modify (or override) the content of specific blocks
within the pattern or reset it to the original. Access to block
settings and styles is disabled." (So, what are overrides?) [10].
Each block open to an override is named: "The modal will prompt you
to input a unique name for the override.", since "This requirement
enables WordPress to map the user-created content to the correct
block within the pattern." A later change of the pattern "updates
each instance while retaining your content changes" [10]. Two limits
stood on 18 June 2024: "The number of supported blocks and attributes
is limited, and there is currently no opt-in mechanism for custom
blocks." and "Synced Patterns are only stored in the database and
cannot be packaged as pattern files in your theme." [10]. (second
round) The first has gone: a developer note of 16 March 2026 says
that from WordPress 7.0 an attribute that supports block bindings
supports overrides, "So now, you can use Pattern Overrides for any
block you want — even custom blocks", on opting in through the
`block_bindings_supported_attributes` filter [21]. The second is not
shown to have gone: the tracking issue of the feature, opened 13
March 2024 and closed as completed, lists "Add support for synced
theme patterns (with overrides)" among the items left open [20], the
note of 2026 does not mention it, and a reader's comment under that
note still asks for it [21]; the shared definition with overrides is
then not established as a file under version control. The same issue
states the price of the key: "Renaming the block could potentially
break the connection, so it's not recommended in that case.", and of
choosing the block's name as the key, "the change also has some
side-effects, such as the inability to rename blocks." [20].
DESIGN.md has the weakest form: "Variants (hover, active, pressed)
are expressed as separate component entries with a related key name."
(Component Tokens), so `button-primary-hover` stands beside
`button-primary` and the name alone carries the relation; the words
"extends" and "inherit" do not occur in the README (checked) [4].

F7. **Only the design tool shows the reach of a change to a shared
element, and at two moments: to the user of the element when the
update arrives, and to its owner as usage.** [single vendor; its
documentation; the absence elsewhere rests partly on summarised
fetches] In Figma a change to a library stays local, "those changes
will only appear in the current file until you publish them.", and
the publisher is shown what was "added, modified, or removed" and may
leave assets out [11]. Then "Figma makes the updates available in
every file where the component, style, or variable is used."; the
file shows a badge, "By default, Figma shows a Side by side view of
the change.", and the user may "Click Update next to an individual
asset, or Update all to apply all updates." [12]. The reach is thus
seen file by file by those who use the element, and each decides when
to take the change. The owner's view is library analytics: for a
component, "Total number of teams that use this component", "Number
of files that use instances of this component.", and per file "The
number of instances of the component or variant in the file"; "Figma
logs a detach any time someone uses the" Detach instance setting. Its
limits: it is offered on the Organization and Enterprise plans among
others, not on all (the list of plans a summarised fetch); "Library
analytics update daily, and Figma tracks up to one year of library
analytics data prior to the current day."; and "You can only see
component usage for files in teams that are open to anyone in the
organization" or in teams the viewer has access to [13]. In three of
the text kits no listing of what refers to a changed requirement or
definition is described [1][2][3][5] (summarised fetch). (second
round) The fourth comes nearer: its flag of a drift names the
requirements and stories affected, and on an amendment of high impact
"The refine agent runs a propagation checklist" over the plan, the
data model, the contracts, the research and the related decisions,
and flags what is to be looked at again [16]: a fixed list of kinds
of artefact, not a computed list of what cites the changed item.
DESIGN.md's linter checks references in both directions,
`broken-ref` for unresolved
token references and `orphaned-tokens` for "Color tokens defined but
never referenced by any component", but the README names no command
that lists which components a changed token touches [4]. The pages
of the block system say nothing on where a pattern or a variation is
used [9][10][20][21] (summarised fetch).

F8. **Shared definitions are versioned in three unlike ways: a code
library by semantic versioning with a declared table of which change
is which bump, a design-tool library by publication with a
description, each user of it accepting the update, and in one kit a
specification by a log of versions written into it.** [consensus for
semantic versioning in code libraries, on one policy opened and
several more seen in a result list and not opened; vendor
documentation; one practitioner article of 2018] Changed in the
second round by the last of its points.
- Carbon "aims to follow" semantic versioning "for each of the
  packages that we ship" and gives a table for its React components:
  "A new prop is added to a component" is minor, "An existing prop is
  deprecated" minor, "An existing prop is removed" major, a prop type
  made more specific major, more generic minor [14]. It names what
  the promise leaves out: TypeScript definitions are "not bound to
  semver", and a change of the node a `data-testid` stands on is
  "semver bump: **minor**, but ideally **major**" [14]. The table
  speaks of the programming interface of a component alone: the
  words "visual", "style" and "class" do not occur in the document
  (checked). The table gives a change of typings as patch and the
  example beneath it as minor; the source disagrees with itself.
- A practitioner's article names the two grains: versioning by
  library "applies the same version number to all system assets
  simultaneously", versioning by component "enables adopting teams to
  mix and match button version 5.3.1 with form checkbox 3.1.0". On
  design assets: "Using a linked library, designers can be completely
  unaware how assets changed", and "Designers mixing and matching
  versions drive developers bonkers." (Align Design Assets Versions
  with Code); and "Deprecation warns that feature use should be
  discontinued and support will be removed in the future." [15].
  Dated 2018; the tools have changed since, the two grains have not.
- In Figma a publication carries a description, "Figma shows
  descriptions when accepting updates from a library, as well as in
  the file's version history." [11]; no number of a version of a
  component or of a library is described: the word "version" occurs
  once on [11], in that sentence, and not at all on [12] (checked).
- DESIGN.md's `version` field is "optional, current: "alpha"" and
  names the version of the format, "The DESIGN.md format is at
  version `alpha`." (Status) [4]; a version of the file itself the
  README does not name (checked for the field, summarised fetch for
  the rest). OpenSpec gives its specifications no version number: the
  history is the dated archive [2] (the word "version" occurs once in
  the page, in the sentence quoted in F1; checked).
- (second round) One kit numbers the specification itself and writes
  the cause beside the number: "Every feature and migration spec
  carries a Spec Evolution Log section.", a table with a row for each
  version, the version a "Semantic version of the spec (`1.0` at
  creation, increments per amendment)", beside it the date, a
  sentence on the change, its author and a trigger from a fixed list,
  one of them `drift`, "Reconciling the spec with implementation
  reality discovered during the work". The page calls the log "the
  durable record of what changed about the spec and why" [16].

F9. (second round) **Where keeping a specification and its code in
step was attempted by machine, the one case with figures failed for a
specification written after the code and worked for tests generated
from a small one; a practitioner of formal methods calls
synchronisation unaffordable for most and the specification worth
having all the same.** [single case reported by one of its authors;
one practitioner's position; both on formal specifications of
algorithms, neither on a prose description of an interface]
- At a database company an attempt to check traces of the running
  server against its formal specification ended thus: "Our traces
  never matched our specification.", after "10 weeks of effort
  without successfully trace-checking one spec", and was dropped: "We
  estimated that the marginal cost of implementing trace-checking for
  more specs wasn’t worth the marginal value". The reasons given are
  the difficulty of recording the state of a concurrent program and a
  specification written after most of the code at another level of
  abstraction (the reasons a summarised fetch). The second attempt
  generated tests from a specification of 30,184 states: "These 4913
  tests immediately achieved 100% branch coverage of the
  implementation", against "handwritten tests (21%)" and a fuzzer at
  92% [18]. The figures are of a paper of 2020, not opened, retold by
  one of its authors on 3 June 2025.
- "To synchronize spec and code, you need to bring the spec closer to
  the level of code"; "Synchronization is not affordable for most
  companies."; and "Even if you can't keep the spec in sync, it's
  still a net benefit." (19 March 2024) [19].

What this carries over to a description of an interface is the
agent's inference, not the sources' claim: the cost of keeping two
texts in step grows with their distance in abstraction, and a
description written after the build is harder to match than one the
build was made from.

F10. (second round) **The owners of shared definitions contain
overrides by declaring the surface that may be overridden, and read a
repeated override as a missing variant.** [emerging; the
documentation of one design system added in the second round, in
line with [8], [10] and [13]; no practice report opened] A state's
design system exposes, on a few components, variables meant to be
overridden: "if a variable is safe to override, it will appear on the
component’s documentation page under CSS Variables", and "most
components will NOT have overridable variables" (Public vs. Private
Tokens). The purpose: "They allow overrides for legitimate edge cases
without introducing dozens of one-off variants." (Balancing
Flexibility and Control). An override does not carry to the related
states: who overrides the background of a button is told to "remember
to override the hover and active variants too". And the override is
read as evidence: "When multiple teams consistently override the same
token in the same way, it suggests a gap in the system.", so that a
recurring one "might deserve to become an official variant" (When
(and Why) Overrides Inform the System) [22]. The same shape stands in
the design tool, which limits overrides to named properties [8] and
counts detachments [13], and in the block system, where each block
is opened to overrides one by one and by name [10]. To "design system
overrides chaos" the search returned such rules of containment and
commentary; the one practice report tried did not open, so the chaos
itself is documented here by no one who lived it.

## Unexpected

The difference as the thing that is written. The card asks how a
change to a description is read as a difference in text; [2] turns
this round: the difference is the document a person and an agent
write and review, and the full specification is what a command
computes from it at the end. For a description of an interface this
would mean a reviewer sees only the screens and elements a change
touches, with the reason beside them, at the price named under
Options.

The name of a part is the key of a variation. In the design tool a
local change survives where the names of the layers "must match" [8];
in the block system an override needs "a unique name" so that content
is mapped "to the correct block within the pattern" [10]; and the
block system's tracker says what follows: "Renaming the block could
potentially break the connection" [20] (second round). Two unrelated
systems arrived at the same thing: what a page may vary in a shared
element is addressed by a stable name of a part of that element, and
a renamed part loses its variations. The inference for element
definitions written in Markdown is the agent's own.

The owner of the shared definitions counts the exits. The design tool
logs every detachment as a statistic of the library [13], and a
design system in code reads a repeated override as "a gap in the
system" [22] (second round). An exit is the user's verdict that the
shared definition did not fit, and two owners treat it as data.
Whether a text system has an equivalent (a page that copies an
element instead of naming it) nothing opened says.

The field moved under the secondary source. The comparison [6] is of
October 2025; the page of one of the kits it judges was updated in
September 2026 and describes steps that [6] does not mention [5],
another kit documents a current set of commands beside a set it calls
legacy [3] (summarised fetch), and the kit with the procedure of
amendment last changed its page the day before this run [16]. A
judgement about these kits older than a year should be read again
against the kit's present documentation.

A specification out of step may still pay (second round). The card
assumes that a description is to be kept in step with the product;
[19] says, of formal specifications, that keeping in step is
"not affordable for most companies" and that the specification is
"still a net benefit", because with it a fault is either in the
building or in an assumption, not in the design. Whether that holds
for a description of an interface, whose worth lies largely in being
what the next change starts from, nothing opened says.

The same question stands open in another project's tracker (second
round). A work item of an open content system's AI initiative asks
that design system metadata can be "overridden or added to by a
specific theme", "in a structured manner so that with overrides, its
still possible to update the underlying" metadata, in "3 levels. Core
metadata, Custom Code Overrides, Site Config Overrides.", with the
AI told to prefer the higher level and with those who use overrides
kept apart from those who edit them [23]. The item is undated on the
page and its proposed resolution is empty: a need stated, not an
answer.

## Not found

- No measured study or figure on how often a prose specification
  drifts from its code, how often overrides are lost at an update, or
  how often instances are detached. Looked for in the result lists of
  queries 1, 5 and 11 and in [6], [7], [18] and [19]; the only
  figures found concern formal specifications [18], and [7] rests its
  claims on argument and illustrative cases (summarised fetch).
- No kit that writes a change of the code back into the specification
  without a person. Looked for in [1][2][3][5][16]: in [16] the agent
  proposes and the developer confirms; [17] is a vendor's claim of a
  button, its documentation not opened. The reverse engineering of a
  specification from code named in [6] is known only through [6];
  that kit's own documentation was not opened.
- No procedure, in any kit opened, for a hand edit of the code made
  outside the kit's own run.
- No rule, in the two pages of the design tool read for it [8][12],
  for what becomes of an override when the main component changes and
  the update is accepted.
- No practice report on overrides that could be opened: a thread of
  the design tool vendor's forum in the first round and an article of
  a company's design team in the second both returned HTTP 403. What
  stands in their place is an issue tracker [20] and the owners' own
  rules [8][13][22].
- No design system's own policy that counts a change of appearance as
  a breaking change: two such pages named by the result list of query
  3 did not open (HTTP 403; an empty body), and the second round did
  not search for it again. [14] does not treat appearance at all;
  [15] points to a separate article on it, not opened.
- No statement, in the pages of the block system, of where a shared
  pattern is used across a site [9][10][20][21].
- No full specification of the DESIGN.md format read: the README
  points to it and it was not opened in either round.
- Nothing on section systems of shop or site builders, on other
  design tools, on component workshops, on the versioning of design
  token files, or on the issue trackers of the spec-driven kits: no
  query of either round was aimed at them.
- Nothing specific to native mobile or the desktop: every system
  opened is of the web or of a design tool.

## Options

For reading a change:
- The difference of the description in git, as it stands. Nothing new
  to build; the reviewer reads the change inside unchanged text, the
  reason for the change is not in the difference, and the cost [6]
  names grows with the length of the documents.
- A delta written as a document and merged at the end [2]. The change
  can be reviewed alone and two changes to one document collide less;
  it needs headings stable enough to address an item, a merge that
  must be exact, and a second kind of document with a life of its
  own.
- A structural difference made by a tool for the structured part of a
  description [4]. Exact where the content is data (tokens, lists of
  elements); silent on prose.

For changes made during the build:
- A rule of direction: the description changes first and the build
  follows, a deviation found while building being raised as a change
  to the description [3]. Costs only discipline, and nothing enforces
  it.
- An amendment raised by whoever builds and confirmed by a person
  [16]: what the description says, what the build found, which item
  would change; confirmed, rejected or deferred; written into the
  affected item only and logged with its cause. It needs a rule of
  which discoveries count, and a rejected or deferred amendment
  leaves the build running on a description known to be stale.
- A check after the build that compares what was built with the
  description and reports, without blocking [3]. It finds drift only
  as well as an agent reads code and an interface; no source measures
  how well that is, and the one measured attempt at checking by
  machine failed where the two texts lay far apart [18].
- A report of state only: which tasks are done [5]. Cheap; the
  content of the description is not corrected by it.
- A description rewritten from the code on demand [6][17]. Known from
  a secondary account and a vendor's claim only; the description
  would follow the code and could lose what was wanted, and the
  vendor itself advises the other direction.
- Accepting drift [19]: the description is kept for what it settles
  and is not promised to match. Free; it gives up the description as
  the place the next change starts from.

For a screen that needs a shared element differently:
- Variants listed in the element's definition [4][8]. The reach of a
  variant is everything that names it; the definition grows with each
  page's need.
- Overrides stated by the page, limited to a surface the element
  declares, by named parts and to content or appearance
  [8][10][22]. Needs stable names of parts and a list of what may be
  overridden; a rename breaks the link [20], related states are not
  carried along [22], and a change of structure still needs a variant
  or a copy.
- A copy with its origin recorded, the detachment [8]. Free in what
  it changes; the reach of later changes to the element is lost, and
  the count of copies becomes the signal [13][22].

For the reach of a change:
- A list of the pages that name an element, computed from the text
  and shown when a change to the element is proposed, after the model
  of [12] and [13]. That text makes this cheap is the agent's
  inference; no text kit opened does it.

For versions:
- One version for the whole description, git as its record: the grain
  [15] calls by library. Fits pages and elements that live and change
  together.
- A version for each element's definition with a declared table of
  what breaks a page [14][15]. Pays where elements are taken up by
  others at their own time; a table and a discipline to keep.
- A log of versions with the cause of each, kept with the document
  [16]. Tells a later reader which clauses are the first intent and
  which answer what the build found; one more thing to write at every
  change.

## Relevance to this project

The recommendation is the agent's own inference from the findings,
not a finding.

The idea of a definition per element is workable only together with a
stated rule of variation in the three grades of F5 and F6: variants
listed in the element, overrides by a page limited to named parts and
to a surface the element declares, and a recorded copy as the exit.
Every system of shared definitions that was opened ended there
[8][9][10][22], and the two that key a variation by the name of a
part pay for a rename [8][20], so the parts of an element need stable
names before a page may vary them. This is chosen against letting a
page override anything, which the design tool refuses for structure
[8] and the design system in code refuses for most components [22].

The reach of a change should be computable from the text: a page
names its elements by a stable identifier, and the pages touched by a
change to an element are listed when the change is proposed. It rests
on [12] and [13] as the only model found, and is chosen against
leaving the reach to the reviewer's memory, which is what the text
kits opened do, one fixed checklist apart [16].

No kit brings the build's changes back without a person:
[1][3][5][6][7][16] agree, and [17] is a claim. The form worth taking
is that of [16], which is also the form the framework of the frame
already works in, the agent proposing and the human deciding: whoever
builds raises a discovery as a proposed change to a named item of the
description, saying what the description states and what the build
found; a person confirms, rejects or defers; the cause is recorded. A
rule of which discoveries count belongs with it, as in [16]: what a
user sees and what the description states, not how the code is laid
out. This is chosen against any automatic return from code, for which
no documentation of a product was opened and no measurement found,
and against accepting drift [19], since here the description is what
the next cycle starts from.

For reading a change, git's difference serves one person working end
to end; the written delta of [2] is the option for the specialist
whose change others review before it enters the standing description.
Nothing measured decides between them; the choice is the principal's.

The description is better versioned as a whole; a version per element
[14][15] pays only if elements come to be shared across projects that
take updates at their own time.

What all of this rests on: the documentation of nine systems (four
kits, one format, one design tool, two design systems, one block
system with its tracker), one vendor's claim, one item of another
project's tracker, three practitioner pieces, one preprint and one
case with figures on formal specifications; no measurement on prose
specifications or on overrides; no practice report on overrides
opened.

Consult when: deciding how a page refers to a shared element and what
it may override; deciding whether a change to the description is a
difference or a document of its own; deciding what the build stage
reports back and who writes it into the description; deciding whether
element definitions carry versions of their own; and whenever
automatic synchronisation of a description with code is proposed.

## Sources

Sources 1 to 15 were opened in the first round, 16 to 23 in the
second; the numbers of the first round are kept.

1. `spec-driven.md`, the kit's own account of its method, repository
   github/spec-kit (GitHub). Undated: the file at the head of the
   repository, read 2026-11-21.
   https://raw.githubusercontent.com/github/spec-kit/HEAD/spec-driven.md
   Kind: primary. Read: summarised fetch of the whole file; the
   quoted passages and the absences marked "checked" verified against
   the file's text. Original.
2. "Concepts", documentation of OpenSpec, repository
   Fission-AI/OpenSpec. Undated: the file on the main branch, read
   2026-11-21.
   https://raw.githubusercontent.com/Fission-AI/OpenSpec/main/docs/concepts.md
   Kind: primary. Read: summarised fetch of the whole file; quotes
   verified against the file's text, the sections Delta Specs, Why
   Deltas Instead of Full Specs and Archive read in the text itself.
   Original.
3. "Commands", documentation of OpenSpec, repository
   Fission-AI/OpenSpec. Undated: the file on the main branch, read
   2026-11-21.
   https://raw.githubusercontent.com/Fission-AI/OpenSpec/main/docs/commands.md
   Kind: primary. Read: summarised fetch of the whole file; quotes
   verified against the file's text. Original.
4. "DESIGN.md", README of the repository google-labs-code/design.md.
   Undated: the file on the main branch, read 2026-11-21; the format
   declares itself at version alpha.
   https://raw.githubusercontent.com/google-labs-code/design.md/main/README.md
   Kind: primary. Read: summarised fetch of the whole file; quotes
   verified against the file's text, the sections `diff`, Component
   Tokens and Status read in the text itself; the full specification
   it points to was not opened. Original.
5. "Best practices" (Docs, Specs), Kiro. Dated 25 September 2026 by
   the page's own line "Page updated" and by its structured data.
   https://kiro.dev/docs/specs/best-practices/
   Kind: primary. Read: summarised fetch of the whole page; quotes
   verified against the page text, the two questions quoted read in
   the text itself. Original.
6. "Understanding Spec-Driven-Development: Kiro, spec-kit, and
   Tessl", Birgitta Böckeler, martinfowler.com. Dated 15 October 2025
   by byline.
   https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html
   Kind: secondary (a practitioner's analysis of three kits from her
   own trials). Read: summarised fetch of the whole page; quotes
   verified against the page text. Original.
7. "Spec-Driven Development: From Code to Contract in the Age of AI
   Coding Assistants", Deepak Babu Piskala, arXiv:2602.00180v1
   [cs.SE]. Dated 30 January 2026 by the arXiv stamp on the page; the
   page calls itself a technical report; not peer reviewed.
   https://arxiv.org/html/2602.00180
   Kind: secondary. Read: summarised fetch of the whole page; quotes
   and the identifier verified against the page text. Original.
8. "Apply changes to instances", Figma Help Center. Undated.
   https://help.figma.com/hc/en-us/articles/360039150733-Apply-changes-to-instances
   Kind: primary. Read: summarised fetch of the whole page; quotes
   verified against the page text, the passage on what cannot be
   overridden and on change preservation read in the text itself.
   Original.
9. "Variations", Block Editor Handbook, WordPress.org. First
   published 21 April 2021 by the page's date field; the date of its
   last update not read.
   https://developer.wordpress.org/block-editor/reference-guides/block-api/block-variations/
   Kind: primary. Read: summarised fetch of the whole page; quotes
   verified against the page text. Original.
10. "An introduction to overrides in Synced Patterns", Nick Diego,
    WordPress Developer Blog. Dated 18 June 2024 by byline.
    https://developer.wordpress.org/news/2024/06/an-introduction-to-overrides-in-synced-patterns/
    Kind: primary (the project's own blog on its own feature). Read:
    summarised fetch of the whole page; quotes verified against the
    page text. Original.
11. "Publish a library", Figma Help Center. Undated.
    https://help.figma.com/hc/en-us/articles/360025508373-Publish-a-library
    Kind: primary. Read: summarised fetch of the whole page; quotes
    verified against the page text. Original.
12. "Review and accept library updates", Figma Help Center. Undated.
    https://help.figma.com/hc/en-us/articles/360039234193-Review-and-accept-library-updates
    Kind: primary. Read: summarised fetch of the whole page; quotes
    verified against the page text, the opening and the passage on
    reviewing updates read in the text itself. Original.
13. "View and explore library analytics", Figma Help Center. Undated.
    https://help.figma.com/hc/en-us/articles/360039238353-View-and-explore-library-analytics
    Kind: primary. Read: summarised fetch of the whole page; quotes
    verified against the page text. Original.
14. "Versioning" (`docs/guides/versioning.md`), Carbon Design System,
    repository carbon-design-system/carbon. Undated: the file on the
    main branch, read 2026-11-21.
    https://raw.githubusercontent.com/carbon-design-system/carbon/main/docs/guides/versioning.md
    Kind: primary. Read: summarised fetch of the whole file; quotes
    verified against the file's text, the Overview and the table of
    changes read in the text itself. Original.
15. "Versioning Design Systems: Communicating Change Clearly to
    People Using Systems", Nathan Curtis, the author's newsletter on
    Substack. Dated 17 September 2018 by byline.
    https://nathanacurtis.substack.com/p/versioning-design-systems-48cceb5ace4d
    Kind: secondary (a practitioner's article; the author's firm
    advises on design systems, which is the agent's knowledge and was
    not verified in this run). Read: summarised fetch of the whole
    page; quotes verified against the page text. The author's own
    publication; a page of the same title on the author's company
    site did not open, and which of the two is the first was not
    established. In this run the host answered a client that
    identified itself with the default name of a Python standard
    library with HTTP 403, and every other client tried with 200.
16. "Spec Amendment During Implementation", documentation of DevSquad
    Copilot, published under Microsoft's organisation on GitHub.
    Dated 20 November 2026 by the page's own line "Last updated".
    https://microsoft.github.io/devsquad-copilot/concepts/spec-amendment/
    Kind: primary. Read: summarised fetch of the whole page; quotes
    verified against the page text, the page from "When to Amend" to
    "Spec Evolution Log" read in the text itself. Original.
17. "The Spec Is the Program. The Code Is What Gets Compiled.", Luis
    Chavez-Mattos, MindStudio blog. Dated 6 June 2026 by byline.
    https://www.mindstudio.ai/blog/spec-is-the-program-code-is-compiled
    Kind: a vendor's blog on its own product, used only for what the
    vendor claims of that product and marked as a vendor claim where
    cited; not documentation. Read: summarised fetch of the whole
    page; quotes verified against the page text. Original.
18. "Conformance Checking at MongoDB: Testing That Our Code Matches
    Our TLA+ Specs", A. Jesse Jiryu Davis, the author's own site.
    Dated 3 June 2025 by byline.
    https://emptysqua.re/blog/mongodb-conformance-checking/
    Kind: secondary (one author of the paper it retells, "eXtreme
    Modelling in Practice", VLDB 2020; the paper was not opened).
    Read: summarised fetch of the whole page; quotes and figures
    verified against the page text. A copy: the page says it is
    cross-posted from the engineering blog of the author's employer;
    that original was not opened, the eight openings of the round
    being spent.
19. "What if the spec doesn't match the code?", Hillel Wayne, the
    newsletter Computer Things. Dated 19 March 2024 by byline.
    https://buttondown.com/hillelwayne/archive/what-if-the-spec-doesnt-match-the-code
    Kind: secondary (a practitioner's position; that the author
    consults and teaches on formal methods is the agent's knowledge,
    not verified in this run). Read: summarised fetch of the whole
    page; quotes verified against the page text. Original. As at
    [15], the host answered the default client of a Python standard
    library with HTTP 403 and every other client tried with 200.
20. "Introduce overrides in synced patterns iteration for WP 6.6",
    issue 59819 of the repository WordPress/gutenberg (GitHub).
    Created 13 March 2024 by the page's data; closed as completed.
    https://github.com/WordPress/gutenberg/issues/59819
    Kind: primary (issue tracker). Read: summarised fetch of the
    whole page; quotes verified against the page's data, the passage
    on renaming and the list of open items read in the text itself.
    Original.
21. "Pattern Overrides in WP 7.0: Support for Custom Blocks", Bernie
    Reiter, Make WordPress Core. Dated 16 March 2026 by byline.
    https://make.wordpress.org/core/2026/03/16/pattern-overrides-in-wp-7-0-support-for-custom-blocks/
    Kind: primary (a developer note of the project). Read: summarised
    fetch of the whole page with its comments; quotes verified
    against the page text. Original.
22. "How CSS Variables Power the NYS Design System", Emily Gorelik,
    New York State Design System. Dated 21 April 2026 by byline.
    https://designsystem.ny.gov/about/updates/css-variables/
    Kind: primary (a design system's own account of its rules).
    Read: summarised fetch of the whole page; quotes verified against
    the page text. Original.
23. "Enable Site and Page Specific Design System Metadata Overrides
    and Additions", work item 3545815 of the project ai_initiative on
    Drupal's GitLab. Undated on the page as read.
    https://git.drupalcode.org/project/ai_initiative/-/work_items/3545815
    Kind: primary (issue tracker; a statement of a need, its proposed
    resolution empty). Read: summarised fetch of the whole page;
    quotes verified against the page text. Original.

## Opened and not used

None: each of the twenty-three pages opened is cited above.

## Search record

There were two rounds on the same day. In the first the search tool
refused every query after the fourth, the web search budget of the
session being used up, so the disconfirming query was not run as
worded and no differently worded query could test the stop rule. The
second round was ordered by the coordinator of the research once the
search worked again: to run the queries refused or not run, the
disconfirming query as worded among them, and one differently worded
query, and to open at most eight further pages.

First round. Queries run, in order:
1. spec-driven development, updating the spec after code exists, keep
   spec in sync.
2. OpenSpec delta specs, added, modified, removed, archive of a
   change.
3. design system versioning, breaking changes, components, semantic
   versioning policy.
4. Figma instances, overrides, changes of the main component, which
   overrides are preserved.

Queries sent and refused in the first round: the OpenSpec repository
on deltas and the source of truth; Kiro's documentation on updating a
specification after implementation; WordPress synced pattern
overrides; DESIGN.md on lint, diff and versioning.

Pages opened in the first round, in order, fifteen in all: [1], [2],
[5], [6], [8], [14], [4], [9], [10], [12], [3], [7], [13], [11],
[15]. Of these [1], [7], [8] and [15] were taken from the result
lists of the queries; the others were reached by address, from the
agent's knowledge of where the documentation of the kits, of the
design tool, of the block system and of the design system lies, since
the search had ended; each is cited only for what the page said when
opened. Attempts that returned no page, not counted as openings and
used for nothing, their addresses left out because every address of
this note is opened by a script: a thread of the design tool vendor's
community forum on overrides lost when a library is updated (HTTP
403); the versioning page of a financial data company's design system
(HTTP 403); the versioning page of a city's design system (an empty
body); the article of [15] on its author's company site (HTTP 500).
The first round ended by the opening budget of the card.

Second round. Queries run, in order, seven in all:
5. keeping specification in sync with code fails (the disconfirming
   query, as worded).
6. design system overrides chaos (the disconfirming query, as
   worded).
7. The OpenSpec repository, README, delta, specs, archive, source of
   truth, changes folder (refused in the first round).
8. Kiro's documentation, updating requirements after implementation,
   update tasks, sync spec with codebase (refused in the first
   round).
9. WordPress synced pattern overrides, block bindings, handbook,
   content of an instance (refused in the first round).
10. DESIGN.md, the repository, spec, lint, diff, versioning (refused
    in the first round).
11. Differently worded, for the stop rule: living spec, drift
    detection, carrying hand edits in code back into the spec, an
    agent hook or a reconcile command.

What they returned: query 5, [18] and [19], older academic papers on
generating specifications and tests, and posts of vendors and
practitioners, not opened; query 6, [22] and [23] among commentary;
query 7, the repository and its mirrors, nothing beyond [2] and [3];
query 8, the page [5] under several addresses and a further page of
the same documentation, not opened, nothing that describes a return
from code into requirements; query 9, [10] again, [20] and [21];
query 10, mirrors of [4] and commentary, nothing on a version of the
file; query 11, [16] and [17] among posts and guides excluded by
kind.

Pages opened in the second round, in order, eight in all: [16], [21],
[23], [18], [17], [20], [22], [19]; all eight were taken from the
result lists of the round's queries. Attempts that returned no page,
not counted and used for nothing, their addresses left out: an
article of a company's design team on the failure of its design
system, on a blogging platform (HTTP 403); the older address of [22],
which returned only a notice of redirection.

After the reading of each round, each cited address was requested
again by a script to confirm that it opens and that each quoted
passage stands in the page's text; the irregularities are recorded at
[15] and [19].

What the disconfirming query found. Its first half, run as worded,
bore out the expectation: in [1][2][3][5][6][7] the way back from
code is by hand, by a request to the agent, or a check; [18] is a
case in which ten weeks of work did not make code and specification
match; [19] holds that synchronisation is beyond most companies. The
refinement came from query 11, not from the disconfirming query: [16]
documents a procedure in which the agent proposes and a person
confirms, and [17] claims a button. Nothing opened shows a return
from code without a person. Its second half, run as worded, returned
no report of chaos that could be opened: it returned the rules by
which owners contain overrides [22] and a stated need for layered
overrides [23], and query 9 gave the limit that a rename breaks an
override [20]. The expectation of the card speaks of bringing changes
back and is silent on overrides; on overrides the query disconfirmed
nothing and confirmed nothing from practice.

Why the run ended and where the stop rule stands. The second round
ended by its limit of eight openings. Of the card's stop rule, "every
route has a primary source" is met: design systems [14][22], design
tools [8][11][12][13], block systems [9][10][20][21], spec-driven
kits [1][2][3][5][16]. "Nothing new from a differently worded query"
is not met: query 11 returned [16] and [17], which changed F3 and F8,
so a further differently worded query could still bring something
new.
