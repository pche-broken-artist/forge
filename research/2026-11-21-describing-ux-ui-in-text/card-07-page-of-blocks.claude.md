---
date: 2026-11-21
project: forge
topic: a page as a composition of defined blocks
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-07-page-of-blocks
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 7; no known note named by the card; web sources below
---

# A page is held as data that lists separately defined blocks: the systems, how they divide a block from its place, their troubles, and Markdown per element

<!-- Shape: templates/research.md -->

## In short

Seven kinds of system were read from their makers' own pages, and all
of them hold a page as data that names blocks defined elsewhere: a
theme's template of sections, a block editor's serialized document, a
structured-content page builder, a server-driven UI configuration, a
declarative card, an agent-to-interface format and a low-code tool's
source files [1][2][4][6][7][8][9]. They keep three things apart, not
two: the type of a block (what it is and does, defined once in code, in
a schema or in a catalog), its instance on a page (an ID or a position,
with this page's settings) and its placement (an order list, a layout
that cites IDs, or the position in the document). A page is rearranged
by changing the order or the layout, never the definition. The makers
report troubles of five kinds: pages that outlive the definitions they
cite, the growth of blocks and options, fixed limits, the cost of an
own framework, and a text source kept beside a visual editor. This
much is sure as far as each maker's word on its own product goes; no
measured comparison of such formats was found. The disconfirming
queries met the expected complaints about versioning, which the makers
answer with machinery of their own, and found little on what blocks
cannot express beyond counts and default layouts. On the idea to be
tested: a Markdown file per component written for AI agents is
published by one design system and by one practitioner, page files
that link to a Markdown file per component by one tool's
documentation, and no team was found that publishes definitions of
interface elements with page files that place them. The unexpected:
the design system that keeps such files tells its authors not to write
one for a simple component of a single element [11].

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

> #### Card 7: A page as a composition of defined blocks
> - **Question:** Which systems hold a page as data that lists
>   references to separately defined blocks with their placement and
>   settings (block editors with their patterns and templates, theme
>   templates made of sections, page builders on structured content,
>   server-driven UI, declarative card formats and formats by which an
>   agent sends an interface, page schemas of low-code tools), how
>   does each divide what a block is and does from where it stands on
>   a page, how is a page rearranged, and which troubles do they
>   report; and does any team publish a practice of one Markdown file
>   per interface element with page files that refer to them?
> - **Why it matters:** these are the direct relatives of the idea of
>   small definitions.
> - **What would answer it:** vendors' documentation of their own
>   formats, and engineering write-ups by teams that built such
>   systems.
> - **Where to look:** the documentation of block editors, of
>   section-based theme templates and of structured-content page
>   builders; engineering write-ups on server-driven UI; the
>   specifications of declarative card and agent-to-interface formats;
>   public repositories and write-ups for component specifications
>   kept in Markdown for AI agents. Search words from card 1:
>   "generative UI" for formats in which an agent emits an interface
>   at run time, kept apart from a description handed to a build;
>   "intermediate representation", "structured specification". Primary
>   artefacts in public repositories (schemas, component and page
>   files, agents' rules and prompt files, the schemas of servers for
>   design tools, issue trackers) before commentary about them.
> - **Disconfirming query:** "server-driven UI problems", "page
>   builder blocks limitations"; expected: complaints about versioning
>   and about what blocks cannot express.
> - **Stop rule:** nothing new from a differently worded query and
>   every route has a primary source; ten to fifteen pages opened.

The baseline, what this note must beat: without research one would say
that block editors, themes made of sections and server-driven UI all
keep a page as a list of blocks, and that small Markdown definitions
with a page file above them are the same thing written in Markdown.
That says neither how each system divides the definition from the
place, nor which troubles its own maker reports, nor whether anybody
publishes the Markdown practice. The note beats the baseline where it
shows the division from each maker's page, names the troubles with
their source, and gives a sourced yes or no on the practice.

## Key findings

How the pages were read: every page came through a fetch tool that
hands the page to a small model and returns that model's answer, which
is a summarised fetch. Each quote below was then checked word for word
against the raw page by a second fetch of the same address; what could
not be checked so is said without quotation marks and named as the
summary's.

**F1. Each of the seven kinds of system the card names holds a page as
data that lists blocks defined somewhere else.** [consensus across
independent makers; vendor documentation and one engineering write-up]
A theme's template of sections: "JSON templates are data files that
store a list of sections to be rendered, and their associated
settings." [1, opening paragraph]. A block editor: content is a
sequence of blocks, each serialized so that "the block grammar is an
HTML comment", in whose main tag "there can be a JSON object" [2,
Data and attributes]. A structured-content page builder: the page
carries an array of blocks, each an object or a reference [4].
Server-driven UI: "The configuration includes a list of views, each
with a unique identifier and a layout." [6, CHAOS Backend]. A
declarative card: "An Adaptive Card is a JSON-serialized card object
model.", whose body "is made up of building-blocks known as
`elements`" [8, opening and Adaptive Card structure]. An
agent-to-interface format: a surface "stores component instances in a
flat list where parent components reference child IDs" [7,
Components]. A low-code tool's source in git: "One file for each
screen, representing the screen.", beside "A folder containing one
file for each component" [9, File structure for canvas apps].

**F2. The systems keep three things apart, not two: the block's type,
its instance on a page with that page's settings, and its placement;
a page is rearranged in the third.** [consensus; vendor documentation
and one engineering write-up; the cells marked as inference are the
agent's]

| System | The type: what a block is and does | The instance on a page | The placement | How a page is rearranged |
|---|---|---|---|---|
| Theme template of sections [1] | a section file in the theme, named by the instance's `type`: "The filename of the section file to render, without the extension."; the section's schema declares its settings | an entry of the `sections` object under an ID, with `type`, `settings`, `blocks` and `block_order` | `order`: "An array of section IDs, listed in the order that they should be rendered." | "Merchants can add, remove, and reorder these sections using the theme editor."; a section without presets is put into the file by hand |
| Block editor [2] | a block type known to the editor; the page read describes the instance, not the registration of a type | the block's comment in the serialized content, with its attributes as a JSON object | the block's position in the document; no separate list | not described on the page read; a position in a document changes by moving the block (inference) |
| Structured-content page builder [4] | a block of the builder; its schema stands in a lesson not opened | an item of the page's array: an object, or a reference to a shared document | the item's position in the array | by reordering the array: the lesson names a page builder for content that is to be "reordered, have different layouts, or have different components" |
| Server-driven UI [6] | an element, a component or an action, of a versioned type such as `chaos.text.v1`, defined on the backend and supported or not by a client's platform and app version | an entry in the configuration's list of components, under an ID, with its parameters | the view's layout, which "organizes components into sections based on their component IDs" | the backend builds the configuration it returns; what the layout cites decides what stands where (the post describes the building, not a rearrangement as such) |
| Declarative card [8] | the element types of the card's schema (`TextBlock`, `Image`, `Input.Text` and others); the author of a card defines none | an object in `body` with a `type` and its properties | the order in `body`; `ColumnSet` and `Container` for side by side and for grouping | by reordering `body` (inference; the page read shows no rearrangement) |
| Agent-to-interface format [7] | a catalog: component schemas that the renderer pairs with its own native widgets and that the agent uses "to build the LLM system prompt and validate outgoing messages" | an entry of the surface's flat list of components, under an ID | a parent "Points to child components by ID"; `allowedParents` and `allowedChildren` (v1.0) limit "where the component can appear in the layout" | not on the page read |
| Low-code source files [9] | one `.pa.yaml` file per component in a `\Component` folder | one `[screen Name].pa.yaml` file per screen | inside the screen's file; the page read does not show its content | in the visual studio; in the file only "minor edits" |

**F3. Three unrelated systems split the page's own data once more: a
set of instances keyed by ID, and a separate structure that orders or
nests those IDs.** [emerging pattern; vendor documentation and one
engineering write-up] The theme template has a `sections` object keyed
by section IDs and an `order` array of the same IDs [1, Schema]. The
server-driven configuration lists components and actions "detailing
their settings as referenced by their respective IDs" while the layout
places component IDs [6, CHAOS Backend]. The agent-to-interface format
keeps a flat list in which a parent cites its children by ID, "so the
surface stays a flat list instead of a nested tree", for the reason of
"making layouts straightforward for an LLM to stream incrementally"
[7, Components]. The block editor and the card format do it the other
way: the placement is the position of the instance in the document
[2][8].

**F4. Sharing a block's type across pages is universal; sharing one
instance across pages is a separate decision, and the makers hedge
it.** [consensus on the distinction; vendor documentation] The theme
format forbids it: "You can't share section data across JSON theme
templates, so each section must have an ID that's unique within the
template." [1, Section data]. The block editor has both kinds and
names them apart: "once a pattern is inserted it doesn't remain in
sync with the original content", a reusable block is inserted in many
places "remaining in sync everywhere", and template parts are
"reusable areas within a template" [2, Patterns, Reusable blocks,
Templates]. The page builder's vendor warns: "Avoid making your entire
page builder an array of references", calls it "the number one mistake
I see in the wild", and advises an object "If there is not a clear
need to re-use content across many pages" [4, Use references
sparingly].

**F5. The troubles the makers themselves report are of five kinds.**
[consensus on the first two, each reported by two or more independent
sources; the other three rest on one or two sources each; vendor
documentation, an engineering write-up and one consultancy's
practitioner claim]

- *Pages outlive the definitions they cite.* In the block editor a
  stored page holds the block's old markup, so on a change of markup
  or attributes "block authors need to consider existing posts using
  the old versions of their block"; the ways out are "Do not deprecate
  the block and create a new one (a different name)" or a deprecated
  version kept in the code, where "A deprecation will be tried if the
  current state of a parsed block is invalid" and "Deprecations do not
  operate as a chain of updates" [3, opening section]. In the theme
  format a section named in a template "must exist in the theme", else
  the template fails with an error [1, the Caution after the example
  template]. The server-driven framework gives every element a
  versioned type and keeps a record of "which components and actions
  supported by a given client platform type and app version"; "If no
  register qualifies, the feature is omitted from the final response."
  [6, Check Registers]. The agent format fixes the catalog of a
  surface, "locked for the lifetime of that surface", and a component
  without a catalog is rejected: "the renderer rejects that component
  or function call rather than falling back" [7, Catalog negotiation
  and multi-catalog surfaces]. The declarative card carries "the
  schema version required to render it" [8, Adaptive Card structure].
- *Blocks and their options multiply.* "If a block has too many
  variations, you're going to run into a lot of edge cases."; "if you
  have more than two variations of a block" it should be split; "Too
  many choices can confuse and overwhelm"; unused blocks gather, and
  "You should prune them regularly to eliminate technical debt." [4,
  The pitfalls]. A consultancy says the same of server-driven UI from
  its own projects: "horrendous, overly configurable messes" (entries
  of March and October 2022) and the risk of "a "god-protocol" that
  becomes difficult to maintain" (entry of April 2026) [5].
- *Fixed limits.* "JSON templates can render up to 25 sections, and
  each section can have up to 50 blocks.", and a theme holds up to
  1,000 JSON templates [1, opening section and Supported features]. In
  the card format "All Adaptive Card elements **stack vertically** and
  **expand to the width of their parent**"; side by side needs a
  `ColumnSet` [8, Type property].
- *An own framework costs.* For server-driven UI the consultancy wrote
  in October 2022 that "it also requires a substantial investment in
  building and maintaining a complex proprietary framework", and in
  April 2026, moving the technique back to its Trial ring, recommends
  "applying it to highly dynamic areas of an application rather than
  as a blanket replacement for all UI development" [5]. The framework's
  own team isolates failures feature by feature: "If an exception
  occurs, the individual feature is dropped, and the rest of the view
  remains unaffected.", unless the feature is marked essential [6,
  What About Error Handling?].
- *A text source beside a visual editor is edited with care.* The
  low-code vendor calls its files "human-readable and designed for use
  with source control", and in the same page: "Avoid making significant
  changes directly in the `.pa.yaml` files."; "Resolve conflicts
  carefully to avoid corrupting the `.pa.yaml` files."; an app with
  code components cannot be edited in the files at all; and the JSON
  files beside them "aren't stable between save and load cycles" [9,
  Accessing source code files, File structure for canvas apps, Editing
  `.pa.yaml` files, Known limitations, Troubleshooting].

**F6. A Markdown file per component, written for AI agents, is
published as a practice: by one design system inside its package and
by one practitioner as a proposal with a tool. Both stop at the
component; neither has a file for a page.** [emerging; a primary
artefact in a published package, and a practitioner claim] The design
system: "Every component package that an agent is expected to use
gets its own `CLAUDE.md`", with the rule "Not one per sub-component"
[11, What this layer is, Where these files live]. The file is read
last, "only after the surface classifier, surface rules, and feature
pattern have already been read", and a rule that holds on one kind of
page is kept out of it: "That rule belongs in the surface rules file,
not here." [11, What this layer is, How this layer defers to surface
rules]. Its sections, as the summarised fetch listed them and as their
names stand in the raw file: what the package is, what it is not, the
component hierarchy, token usage, states, composition rules, and
prohibitions. Missing such a file, "The agent re-implements
functionality that already exists in a dependency" [11, What happens
if this layer is missing or incomplete]. Whether the "feature pattern"
of that reading order describes a page was not established: that file
was not opened. The practitioner: "One markdown
file per component. Platform-agnostic.", with a schema of an API
specification, a structural one, colour assignment, a voice and
screen-reader one and a behavioural one, and the caveat "It sits
alongside the Figma file, not in place of it." [12, the section headed
Component.md and later in the post; dated 2026-04-28].
He names no team; his evidence is his own side-by-side examples, and
the post says nothing of pages, screens or layouts (the summary's
reading of the whole post).

**F7. Page files that refer to a Markdown file per component stand in
one tool's documentation; no team was found that publishes the
practice as the card puts it.** [single source; a tool's documentation
of its own method, undated, no evidence of use] The tool sets three
levels of Markdown: an architecture file, a page or feature file,
"What this page does, its folder structure, and the components it
uses.", and a component file, "Granular logic and responsibilities of
a single component." [10, The 3-Level Hierarchy]. The page file
"describes what the page does and maps out the folder structure with
links to each component spec" [10, Level 2: The Page Spec]. The files
are written first, "Write the markdown before the code.", and lie in
the source tree beside the code they describe: the specification and
the "implementation file are always siblings" [10, opening and What
It Looks Like in Practice]. What a page file refers to there is the
code components in its folder, not the place of an element on the
screen: the nearest thing to placement is the folder structure. That
last reading is the agent's.

**F8. A team that measured a Markdown description of its design system
for agents reports that one file for everything costs more than
guidance fetched per component, and that it led agents to rebuild
components.** [single source; a vendor's report of its own test, which
it calls not conclusive; figures as of 2026-06-15] The single file
"loads everything, every time", while the team's own server lets an
agent "fetch guidance only for a specific component"; the server draws
on "about 2.5 MB of guidance", and "The resulting file is 80 KB, or
roughly 19,800 LLM tokens" after the usage guidance for "50+
components" was cut down [13, Limitation #1, Limitation #2]. On a
log-in screen the single file "required ~92% more tokens" and "had
~2.7x the variance in token consumption between runs"; agents given
only the file went on to "read through component implementations" and
were "more likely to re-create components rather than use the existing
system" [13, The trade-offs using DESIGN.md in production,
Limitation #2 and, by the summary's placing, Limitation #3]. The
authors add: "These results should not be seen as conclusive; this
blog is not a research paper." The comparison is of a format made by
others against the team's own tooling, so the team has a side in it.
What it means for the size of a definition is the agent's inference:
guidance that can be read one component at a time did better there
than one file read whole.

## Unexpected

The card asks how each system divides what a block is and does from
where it stands on a page. The systems read divide three things:
between the definition and the place stands the instance, the block as
it is on this page with this page's settings [1][6][7]. The idea as
heard, an element definition and a page definition that names which
elements it holds and where they stand, has no said place for what
differs from page to page, such as a label, a source of data or a
variant. The question is answered above as put; this is a lead for
whoever shapes the page file.

The design system that keeps a Markdown file per component package
sets a floor under it: "Do NOT create one for simple, single-element
components with no configuration surface." [11, When to create a
component CLAUDE.md]. The idea as heard gives every element of a
screen, a search field for one, a definition of its own. One team's
rule is no proof against that, but it is the only published rule found
on which elements earn a file.

The agent-to-interface format gives as the reason for its flat list
with references by ID that it is "making layouts straightforward for
an LLM to stream incrementally" [7, Components]: the shape of the data
was chosen for the writer being a model. That is a format for an
interface sent at run time, not for a description handed to a build,
and whether the reason carries over to a description an agent proposes
and a human tunes is open.

## Not found

- No team was found that publishes a practice of one Markdown file per
  interface element together with page files that name the elements
  and say where they stand. Looked for with six differently worded
  queries (6, 10, 13, 14, 16 and 17 of the Search record) and in [10],
  [11], [12] and [13]; the nearest are F6 and F7.
- No measured comparison of page-of-blocks formats, and no figure on
  how often a change of a block's definition broke stored pages. The
  one set of figures found is [13], on another matter, and its authors
  call it not conclusive.
- No primary source that says what a block model could not express,
  the second complaint the disconfirming query expected, beyond fixed
  counts [1] and a default layout [8].
- The engineering write-up on the best-known server-driven UI system
  with sections, screens and layouts [14] could not be opened (HTTP
  403 to the fetch), so its model is not cited here; [15], the earlier
  post on the framework read as [6], was not opened either.
- How a block type is registered in the block editor (its metadata
  file) and how a theme's template files are stored were not on the
  page read [2] and are not claimed.
- Seen in result lists and not opened, so nothing is claimed of them:
  a messaging platform's block format, three further structured-content
  page builders, a page builder's documented data structure, two
  open-source low-code tools with YAML or JSON page files, a catalog-
  bound generative UI library, a design system's machine-readable
  component files with a specification for agents, a W3C community
  group on a schema for describing interface elements, and a YAML
  format proposed for interface specifications.

## Options

The card asks for facts; the options below are the agent's own
ordering of them, limited to how a page and its blocks are held.

- **A. The idea as heard.** One Markdown definition per element; a
  page file names the elements and where they stand. Nearest relative:
  the page file with links to component files of [10]. Price: a file
  for every trivial element, which the one team with a rule declines
  [11]; no place for what differs per page (Unexpected); and the
  question F5 puts first, what happens to the pages when a definition
  changes, is left open.
- **B. Three parts, as the systems have them.** Definitions of types
  (what the element is and does, which settings it takes); in the page
  file the instances under stable IDs with their settings; and apart
  from them an order or layout that cites the IDs [1][6][7]. Gain: a
  rearrangement touches the order alone, and the definition stays
  general. Price: more structure to keep, and IDs to keep stable.
- **C. A threshold for definitions.** A definition only for an element
  that has settings, states or rules of composition; a simple element
  is described where it stands in the page [11]. Gain: fewer files.
  Price: a judgement per element, and two places to look.
- **D. No definitions of its own.** The page description uses the
  types of a catalog owned elsewhere, as the declarative card format
  and the agent format do, where the author of a page defines no type
  [7][8]. Gain: nothing
  to keep in step. Price: it needs such a catalog to exist, and a
  version of it to cite (F5).

## Relevance to this project

The idea of small definitions is no outlier: every system read is its
relative, and they agree on the division. The recommendation, the
agent's own inference from F2 to F5 and from the two leads, is option
B with the threshold of C: keep the type, the instance and the
placement apart; give an instance a stable ID and say the order apart
from it; write a definition only for an element that has settings,
states or behaviour of its own; and decide before the first page is
written what a page cites of a definition and what happens to it when
the definition changes. It is chosen against A, because A as heard
has two parts where every system has three and defines every element
where the one published rule does not, and against D as the only way,
because D presupposes a catalog that a small project of one person
may not have, though where a design system exists its components are
the natural types. What it rests on is vendors' documentation of
their own products and two write-ups by teams; nothing measured
supports the choice between B and A, and the Markdown practice itself
is documented by one tool, one package and one practitioner.

Sharing one instance across pages (F4) is better left out until a
need shows: the makers that allow it warn about it.

Consult when: the shape of the page file and of an element definition
is drafted; the question comes up whether every element needs a file;
a rule is needed for what happens to pages when a definition changes;
somebody proposes to reuse one block's content on several pages; the
description is to be edited both as text and through a visual tool.

## Sources

1. "JSON templates", Shopify developer documentation. Undated. URL:
   https://shopify.dev/docs/storefronts/themes/architecture/templates/json-templates.md
   Kind: primary (a vendor's documentation of its own format). How
   read: summarised fetch of the whole page, the quotes checked against
   the raw Markdown. Original.
2. "Key Concepts", Block Editor Handbook, WordPress.org. First
   published 2021-03-09, last updated 2026-11-05; dated by the page's
   own line (byline). URL:
   https://developer.wordpress.org/block-editor/explanations/architecture/key-concepts/
   Kind: primary. How read: summarised fetch of the whole page, the
   quotes checked against the raw page. Original.
3. "Deprecation", Block Editor Handbook, Block API reference,
   WordPress.org. First published 2021-04-21, last updated 2026-10-14;
   byline. URL:
   https://developer.wordpress.org/block-editor/reference-guides/block-api/block-deprecation/
   Kind: primary. How read: summarised fetch of the whole page, the
   quotes checked against the raw page. Original.
4. "Scaling page builders and pitfalls", a lesson of the course "Build
   landing pages with Next.js", Sanity Learn; author not named, written
   in the first person. Undated. URL:
   https://www.sanity.io/learn/course/page-building/scaling-page-builders-and-pitfalls
   Kind: primary (a vendor's teaching material on its own product; the
   advice is the vendor's). How read: summarised fetch of the whole
   lesson, the quotes checked against the raw page. Original.
5. "Server-driven UI", Technology Radar, Thoughtworks; three entries,
   March 2022 (Trial), October 2022 (Assess), April 2026 (Trial);
   dated by each entry's own line (byline). URL:
   https://www.thoughtworks.com/en-gb/radar/techniques/server-driven-ui
   Kind: secondary (a consultancy's opinion from its own projects; it
   sells consulting). How read: summarised fetch of the three entries,
   the quotes checked against the raw page. Original.
6. "Exploring CHAOS: Building a Backend for Server-Driven UI", Jonathan
   Baird and Xin Shen, Yelp Engineering Blog. 2025-07-08; byline. URL:
   https://engineeringblog.yelp.com/2025/07/chaos-inside-yelps-sdui-framework.html
   Kind: primary (a write-up by the team that built the system). How
   read: summarised fetch of the whole post, the quotes checked against
   the raw page. Original.
7. "Catalogs", A2UI documentation, Concepts; describes the
   specification's v1.0, marked current, and v0.9.1. Undated. URL:
   https://a2ui.org/concepts/catalogs/
   Kind: primary (the project's documentation of its own format). How
   read: summarised fetch of the whole page, the quotes checked against
   the raw page. Original.
8. "Getting Started", Adaptive Cards documentation, Microsoft Learn.
   Dated 2017-11-09 and updated 2025-07-03 by the page's metadata
   (structured data). URL:
   https://learn.microsoft.com/en-us/adaptive-cards/authoring-cards/getting-started
   Kind: primary. How read: in full (the fetch returned the page's
   text whole), the quotes checked against the raw page. Original.
9. "Source control for canvas apps", Power Platform documentation,
   Microsoft Learn. Dated 2025-10-08 by the page's metadata (structured
   data). URL:
   https://learn.microsoft.com/en-us/power-platform/alm/git-integration/canvas-apps-git-integration
   Kind: primary. How read: in full (the fetch returned the page's
   text whole), the quotes checked against the raw page. Original.
10. "MD-First Development", ContextKit documentation; no author named,
    the page links to the repository github.com/nolrm/contextkit, which
    was not opened. Undated. URL:
    https://contextkit-docs.vercel.app/docs/md-first
    Kind: primary (a tool's documentation of its own method; no
    evidence of use by a team was looked at). How read: summarised
    fetch of the whole page, the quotes checked against the raw page.
    Original.
11. "Layer 3 — Component CLAUDE.md files", a file of the npm package
    @spark-web/design-system, version 5.1.2; the organisation behind
    the package was not established. Undated. URL:
    https://unpkg.com/@spark-web/design-system@5.1.2/ai-context/layer-3-component.md
    Kind: primary (an artefact shipped in a published package). How
    read: summarised fetch of the whole file, the quotes checked
    against the raw file. A copy: the package's file as served by a
    package CDN.
12. "Component.md", Ian Guisard, on his own newsletter. 2026-04-28;
    byline. URL: https://ianguisard.substack.com/p/componentmd
    Kind: primary for the proposal (a practitioner's claim about his
    own method and tool; no team named). How read: summarised fetch of
    the whole post, the quotes checked against the raw page. Original.
13. "Atlassian's DESIGN.md is here: what we learned testing portable
    design context in practice", Kylor Hall and Andrew Campbell,
    Atlassian blog, How We Build. 2026-06-15; byline. URL:
    https://www.atlassian.com/blog/how-we-build/atlassians-design-md-is-here-what-we-learned-testing-portable-design-context-in-practice
    Kind: primary (a team's write-up of its own test; it compares a
    format made by others with its own tooling). How read: summarised
    fetch of the whole post, the quotes and figures checked against the
    raw page. Original.
14. "A Deep Dive into Airbnb's Server-Driven UI System", Airbnb
    engineering blog on Medium. Date not read. URL:
    https://medium.com/airbnb-engineering/a-deep-dive-into-airbnbs-server-driven-ui-system-842244c5f5
    Kind: primary. How read: not opened, the server answered HTTP 403
    to the fetch; cited for no content. Original.
15. "CHAOS: Yelp's Unified Framework for Server-Driven UI", Yelp
    Engineering Blog, March 2024 by its address. URL:
    https://engineeringblog.yelp.com/2024/03/chaos-yelps-unified-framework-for-server-driven-ui.html
    Kind: primary. How read: not opened, the opening budget went to
    the later post [6], which names it as its predecessor; cited for
    no content. Original.

## Opened and not used

- https://a2ui.org/concepts/components/ : a redirect notice only,
  pointing to the page read as [7]; superseded by [7].

## Search record

Queries, in order:

1. page as JSON list of blocks, sections, template schema
2. server-driven UI engineering blog, sections, screens, layout
3. "server-driven UI problems" (the disconfirming query)
4. "page builder blocks limitations" (the disconfirming query)
5. A2UI specification, components, adjacency list, catalog
6. one Markdown file per component, spec for an AI coding agent, pages
   that reference components
7. page builder pitfalls, structured content, presentation, blocks
   array
8. low-code app source files in git, page, widgets, JSON or YAML
9. Adaptive Cards schema, body, elements, containers, actions,
   templating
10. repositories with components and pages as Markdown specs, a search
    field's file, page spec that lists components
11. block editor: block metadata, template parts, patterns,
    serialization, validation, deprecation
12. generative UI, intermediate representation, JSON catalog, a model
    emitting an interface specification
13. "component.md", a spec per component, "page spec" or "screen spec"
    in Markdown, design system practice
14. screen specs in Markdown in a repository, screens and components
    folders, spec-driven frontend
15. the server-driven framework of [6]: view, layout, components,
    actions, configuration
16. "UI-Spec", an open format for interface specifications, screens,
    components, Markdown repository
17. "one markdown file per component", design system, AI agents, page
    composition that references components

Pages opened, fifteen openings, in order: [1], [2], [3], [4]; [14]
(refused, HTTP 403); the redirect notice listed under Opened and not
used; [8], [9], [5]; [7], [6], [10], [11]; [12], [13]. Not counted as
openings: the same addresses fetched raw once more, some twice, to
check the quotes word for word and to read dates and authors.

The disconfirming queries. "server-driven UI problems" returned talks,
vendors' posts and the consultancy's page [5], which was opened: its
complaints are the cost of an own framework and over-configuration,
softened in its entry of April 2026; versioning appears there not as
a complaint but, in the makers' pages, as machinery they built ([3],
[6], [7]). "page builder blocks limitations" returned vendors' lists
of limits by count and of unsupported cases, none opened, and led to
[4], which was: its troubles are variations, too many choices, the
over-use of references and unused blocks. So the expectation held for
versioning and held only weakly for what blocks cannot express: fixed
counts [1] and a default layout [8], and no write-up of a block model
that failed to express something.

The run ended on the opening budget: fifteen openings, the upper end
of the card's ten to fifteen. Both other parts of the card's stop rule
held at that point: every route of the card had a primary source read
([1], [2] and [3], [4], [6], [7] and [8], [9], and [10] to [13] for
Markdown per element), and the last two differently worded queries,
16 and 17, returned no new route, only further instances of those
already seen. One gap stayed: [14] could not be opened.
