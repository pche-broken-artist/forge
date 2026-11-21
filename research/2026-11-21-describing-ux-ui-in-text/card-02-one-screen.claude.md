---
date: 2026-11-21
project: forge
topic: what an established description of one screen contains
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-02-one-screen
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 2; no known note named by the card; web sources below
---

# An established description of one screen: what it contains, how its elements are identified, and how much of it is prose

<!-- Shape: templates/research.md -->

## In short

There is no shared standard for the description of one screen. The
established descriptions read here fall into three families: the
tabular screen design document of Japanese practice [2], the picture
with numbered notes of UX practice [1][5][8], and the prose functional
specification organised screen by screen [4][9][10]; the per-screen
template of one public administration sits between them [6]. What
recurs across them is an identity of the screen, a line on what it is
for, a picture that carries the layout, elements with a stable handle,
a type and a label, the data attributes of every input and output
item, the actions as event, processing and target screen, and the
conditions and error rules; what several screens share is written
once, outside the screen. Three items of the card's own list do not
recur as fields in the templates read: empty and loading states,
responsive behaviour and entry points. Elements are identified by an
ID shared between the picture and every table, by numbered markers on
the picture, or by names. In every source the layout is shown and not
told, data is tabulated and behaviour is written in short sentences.
The confidence is moderate: one guide and two standards were read in
their own text, the other sources through a summarising fetch, each
route rests on one or two sources, and nothing measured was found.
The disconfirming query found the criticism it expected, and that
criticism is aimed at the weight and the staleness of specifications,
not at their fields. The unexpected thing: no source read says in
text where the elements stand; the position is always a picture or a
named region.

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

#### Card 2: The description of one screen
- **Question:** What does an established description of a single screen or page contain (an annotated wireframe, a screen specification, a functional or UI specification): which fields recur (purpose, entry points, regions, elements, data, actions, states such as empty, loading and error, rules, responsive behaviour), how are elements identified and referred to, and how much is prose against structure?
- **Why it matters:** the first shape to try is a description of a few screens.
- **What would answer it:** published templates and guides of practitioners and organisations.
- **Where to look:** practitioner organisations on wireframe annotation; service manuals of public administrations; public templates of companies; the specification chapters of UX handbooks; the Japanese practice of screen design documents (gamen sekkeisho, within the basic design, kihon sekkei), read in Japanese or in translation; templates of public procurement and of systems engineering in Europe; specifications published by open-source products. Search words from card 1: "design specs", "wireframe annotations", "prototype specifications", "wireflows", "state matrix"; and the model-based words "abstract user interface", "concrete user interface", IFML's "view container", "view component", "interaction flow".
- **Disconfirming query:** "UI specification document is waste", "annotated wireframes are dead"; expected: criticism of heavy specifications and a preference for prototypes.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

The baseline the note must beat is the list the card itself carries
(purpose, entry points, regions, elements, data, actions, states,
rules, responsive behaviour) and the agreement of the vendor pages on
the first result page that an annotation says what an element is and
what it does. To beat it the note names primary templates and guides,
gives their fields as they stand, says how each identifies an
element, and says where the card's list departs from what the
templates hold.

## Key findings

Quotes from [2], [13] and [14] were read in the text of the PDF
itself. Every other quote is as a summarising fetch returned it,
asked for verbatim and not checked against the raw page; a finding
that rests on such sources says "summarised fetch". The word
"design" stands here for the design of the interface, but for two
uses: in "screen design document" and "external design" of [2] it is
the technical design of a system between requirements and build, and
in "style guide" of [5] and [13] it is the visual identity.

**F1. No shared standard shape exists; the established descriptions
read fall into three families that differ in how much is structure.**
[consensus among the sources read; one public guide, practitioner
claims and templates, no study; summarised fetch for all but [2]]

The tabular family. The guide of Japan's Information-technology
Promotion Agency [2] defines six deliverables (工程成果物) for the
screens of a system: 画面一覧 (screen list), 画面遷移 (screen
transitions), 画面レイアウト (screen layout), 画面入出力項目一覧
(list of input and output items), 画面アクション明細 (action
details) and 画面遷移・レイアウト共通ルール (common rules of
transition and layout). It calls the six "最低限のもの" (the
minimum, p. 13), leaves the unit and the composition of the design
documents to each project (p. 13), assumes a web application while
saying most of its advice holds for client-server and mainframe
interfaces (p. 7), and covers more than layout, behaviour and
attributes included (p. 7):
"レイアウトだけでなく、振舞い・属性も含む".

The annotated picture. The Nielsen Norman Group defines prototype
specifications as "a few lines of text written next to a prototype
and describing details that may be ambiguous in the design" and gives
"prototype redlines" and "prototype annotations" as other names
(introduction) [1]. Brown defines annotations as "the words adjacent
to a picture that provide further description of the design or
concepts" [8]. Hoober puts numbered annotations on the left and the
drawing on the right [5].

The prose specification by screen. Spolsky's functional specification
has the parts Disclaimer, Author, Scenarios, Nongoals, Overview,
Details, Open Issues and Side notes; the screens stand in Details,
with the rule to "give every possible screen a canonical name" [4].
The specification template of the OpenOffice.org project has the
headings Abstract, References, Contacts, Acronyms and Abbreviations,
Detailed Specification, Accessibility, Migration, Configuration, File
Format and Open Issues, the Detailed Specification being a free field
[9]; its help page asks "Is each UI element specified in detail (e.g.
default values, input and output ranges...)?" and "Is the error
handling specified in detail?" [10].

Between them. The template of a provincial administration for one
screen of its system has fixed headings and bullets beneath: Secured
By; Header Elements; for every control of the action toolbox Access
Rules, Processing for {Control} and Validation Rules; for every
section of the screen Data Fields and then its controls under the
same three headings [6].

The families also differ in their reader. [2] is written for
agreement between the party that orders a system and the party that
develops it, before the end of external design (p. 1). [1] and [8]
are written for hand-over inside a team; [8] says a product owner is
served by broad descriptions and a developer needs more detail.

**F2. The fields that recur are identity, purpose, a picture,
identified elements, the data of each item, actions, conditions and
errors; access, ways in and out, responsive behaviour and
accessibility each appear in one or two sources only.** [consensus on
the first group among the sources read; public guide, templates and
practitioner claims; summarised fetch for all columns but the first]

"Not found" in the table means not found in the parts read.

| Field | Tabular guide [2] | Per-screen template [6] | Annotation guidance [1][5][8] | Prose specification [4][9][10] |
|---|---|---|---|---|
| Identity of the screen | 画面ID and 画面の名称 on every deliverable | one page per screen, under its name | a code per view, such as "K4b" [5] | a "canonical name" [4] |
| Purpose | 概要: what the screen is for | a purpose statement | not found | an abstract of the whole specification [9] |
| Picture of the layout | 画面レイアウト: rectangles or an image near the finished screen (p. 26) | an image of the screen | the wireframe or the prototype itself | mock-ups [10] |
| Regions | named areas of the page, in the common rules (p. 36) | Header Elements and named sections | a screen broken into components, annotated apart [8] | not found |
| Elements | 識別ID, ラベル, 画面部品の種類, 表示範囲, 画面部品の説明, 操作手順 (p. 24) | controls and fields under their names | numbered elements [5][8]; visual attributes [1] | every element "in detail" [10] |
| Data of an item | enabled, editable, display length, input length, data type, character kind, input constraint, initial display, output format, required, note (pp. 28-29) | a table: Field, Description, Field Format, Data Access Rules | character counts, the source field in the database [8]; constraints [1] | default values, input and output ranges [10] |
| Actions | アクション名, イベント名, summary, input, detail with its conditions, target screen with its ID, output (p. 32) | Processing for {Control} | how interactive elements work [1]; behaviours such as onHover and onClick [8] | interactions [10] |
| Conditions and states | a mark per item: always, on a condition, never (pp. 28-29) | not found | "Different states of UI components" [1]; display conditions [5][8] | not found |
| Errors and messages | the way errors are shown and their messages, in the common rules (p. 35); branches in the action detail (p. 33); 異常系 in the transitions (p. 21) | links to validation rules | messages [1]; error scenarios [8] | error cases of a screen [4]; error handling [10] |
| Who may see or do it | classes of users, in the common rules (p. 35) | Secured By for the screen, Access Rules per control | not found | not found |
| Ways in and out | a deliverable of its own, 画面遷移: start, end, event, branch (pp. 19-21) | not found | "The user flow for complex interactions" [1]; a task flow before any view [5] | not found |
| Responsive behaviour | not found | not found | among the common standards, not per view [5] | not found |
| Accessibility | not found | not found | not found | a checklist of seven items [9] |
| Open questions | not found | not found | not found | Open Issues [4][9] |

**F3. Empty and loading states are not fields of the templates read;
conditions per item and rules for errors are. The list of five states
of a screen is younger and comes from product design, not from
specification practice.** [the absence: consensus among the templates
read; the five states: single source, practitioner claim in a book
excerpt, summarised fetch]

In [2] a state is a mark on an item: 有効 (enabled) and 入力
(editable) take ○ always, △ on a condition, × never; 初期表示有無
(initial display) and 必須 (required) are marked the same way (pp.
28-29). Errors stand in three places: the way of showing them and
their messages in the common rules (2.6, p. 35), a numbered branch in
the action detail (p. 33, the example's step for the case that no
matching data exists, which shows an error message:
"③-2 合致するデータが存在しなかった場合 エラーメッセージを表示する")
and the abnormal path 異常系 of a transition (2.11, p. 21). The fetch
of [6] found no empty state, no loading state and no messages
section. [1] lists "Different states of UI components" without naming
them. The five states are Hurff's: ideal, empty, error, partial and
loading, with "every screen can have up to five states"; of the
loading state he says that many designers insert it "as an
afterthought" [11].

**F4. Elements are identified in three ways; the strongest gives one
ID to an element in the picture and uses it in every table.**
[consensus that an element needs a stable handle, the schemes differ;
public guide and practitioner claims; summarised fetch for all but
[2]]

An ID per part, shared by the documents. [2], layout, 2.2 識別ID
(p. 24), in two sentences:
"図表内で識別するため、画面部品ごとにIDを振る。"
"画面遷移や画面入出力項目一覧、画面アクション明細などと連携して用いる。"
An ID is given to every part of the screen and used together with the
transitions, the item list and the action details. Screens carry IDs
of their own (the example's S-05-01), actions too (A-05-001, p. 33),
the screen list ties each screen to the ID of a function (機能ID,
p. 16), and a transition should name the action detail it starts
(2.10, p. 21).

A number on the picture. Brown places "small circles with numbers or
letters" beside each interactive element, without covering it [8].
Hoober codes a view by section letter, view number and variant
letter, numbers the elements within it, and makes the codes
permanent: "They must never, ever change", "B17a #6 is always B17a
#6"; the code of a removed element is retired and a new element is
added at the end [5].

A name. Spolsky's canonical name of a screen [4]; in [6] the name of
a control is its heading, and a rule is a link to its own page
("Rule XXXXX"), as are permissions and data elements. [1] gives no
scheme: "Some designers write specifications below each design, while
others annotate details on specific elements."

**F5. The layout is always shown and never told; data is tabulated;
behaviour is written in short sentences.** [consensus among the
sources read; public guide and practitioner claims; summarised fetch
for all but [2]]

[2] gives the layout as a figure, "図にてレイアウト案を提示" (2.1,
p. 24), the items as a table, "表形式で詳細化したもの" (p. 27), and
the actions as text, "画面の動作仕様を簡潔な文章で表わす" (p. 31:
the behaviour of the screen in concise sentences), in practice a row
per action with numbered steps and branches (p. 33). [1]: "A text
description of a design will be more difficult to understand than a
wireframe"; specifications "need to be brief, or people won't read
them"; "Rather than being bound to a fixed format, these
specifications usually have greater flexibility". [8]: the words
"should complement the picture, supplying an appropriate balance
between show and tell", and too many notes on one screen look like
"chicken pox". [5]: "the part of a UX specification that is the most
unambiguous and testable is its text", with lists and tables inside
the annotations. [10]: "Each statement shall be as short and simple
as possible"; "Use graphics when concepts, designs, or processes are
too complex or cumbersome to describe with words." The only position
given in words is the named region: the areas of a page in the common
rules of [2] (header, navigation, utility, content main and sub,
footer, their sizes a guide in a figure, p. 36) and the sections of
[6].

**F6. What several screens share is written once, outside the screen,
and an inventory of the kinds of element is part of it; the function
of an element on a given screen stays with the screen.** [consensus
across a public guide, a process model and two practitioners;
summarised fetch for [5], [6] and [8]]

The common rules of [2] hold the areas of a page, colours, fonts and
sizes, the overall structure and navigation, the patterns of
transition, the way errors are shown, the classes of users and the
constraints (2.1 to 2.8, p. 35); the guide also lists ten kinds of
screen part, from text box to image (p. 25). Hoober's specification
is a cascade in which a view inherits from a project style guide,
corporate standards, a list of common standards and an optional
pattern library, whose entries a view cites by code [5]. The German
federal process model has a product for this alone,
Mensch-Maschine-Schnittstelle (Styleguide), with the topic
"Identifikation und Aufbau der Benutzungselemente": "Identifikation
aller am Aufbau der Schnittstelle beteiligten Benutzungselemente",
and "Für zusammengesetzte Benutzungselemente wird der Aufbau
beschrieben"; design rules are then assigned to every element
identified (C.1.11.10.2 and C.1.11.10.3, p. 155) [13]. Brown would
"rather break a screen up into components and annotate each piece
separately" [8]. What a part does on one screen is still written with
that screen: 画面部品の説明 in the layout of [2] (2.6, p. 24),
Processing for {Control} in [6].

**F7. The one European public process model read has no product for
a single screen.** [single source; standard, read partially by a
keyword search over its whole text]

V-Modell XT Bund 2.3 [13] has the style guide of F6, a user task
analysis (Anwenderaufgabenanalyse: profiles of the users, the
physical environment, the users' tasks, C.1.10.9, pp. 120-121) and
mentions the graphical interface only inside the interface
description of a software element ("wie die grafische
Benutzerschnittstelle", C.1.12.3.2, p. 163). Its one method for
dialogs models the structure of a dialog and sets the layout aside:
"Das Layout der Bildschirmmasken bleibt hierbei unberücksichtigt"
(Dialog Design Modellierung, p. 275). A search of all 348 pages for
Maske, Bildschirm and Dialog found nothing else at the level of a
screen.

**F8. The model-based vocabulary names what a screen holds and, in
the parts read, says nothing of where it stands.** [standard, read
partially; the standard itself is another card's]

IFML 1.0 [14] describes "the view part of the application, made of
view containers and view components" (clause 1). "ViewElements are
divided into ViewContainers and ViewComponents. ViewContainers are
aggregations of other ViewContainers and/or ViewComponents." (8.3.55)
"A ViewComponent is an element of the user interface that displays
content or accepts input." (8.3.52) A view element may carry events
of the user's interaction (8.3.56) and an expression that decides
whether it is active (8.3.55). The focus is "the structure and
behavior of the application as perceived by the end user" (7.1).

**F9. The disconfirming query found the criticism it expected; the
criticism is aimed at weight and staleness, and what the critics put
in the place of a specification still describes the screens.**
[contested; practitioner claims on both sides, no measurement;
summarised fetch]

Against specifications. Gothelf: the design phase ends in "Write The
Spec, detailing every pixel and interaction"; "The old kind of
documentation is waste"; "The prototype has now become your
documentation. It is 'The Spec.'" He keeps a remainder: documents
"stripped down" to "the minimum amount of information necessary to
get started on implementation", and more of them for sites heavy in
content, for a consultant with several clients and for work given to
offshore vendors [7]. Shape Up: "If we start with
wireframes or specific visual layouts, we'll get stuck on unnecessary
details"; what its shaping produces "isn't a spec" [3]. The service
manual of the United Kingdom's government requires prototypes ("You
must make prototypes of your service to explore, share and test
different designs") and, on that page, names neither specifications
nor annotations [12]. A team of the same government reported in 2025
that journeys kept in a design tool and in slides "don't always
reflect the latest version" and replaced them with an HTML prototype
kept in a repository with release notes, a page index and a library
of unexpected journeys and error paths, to "maintain a single source
of truth" [15].

For them. [1]: "Only a good combination of prototype specifications
and prototypes could enable others to understand your design
better", with the limit "But not every design needs detailed
prototype specifications". [5]: "Prototypes can be misleading as
design documents", because a prototype or a wireframe shows a single
instance of the design.

What replaces the specification is still a description. Shape Up's
breadboard is one in words alone: places ("things you can navigate
to, like screens, dialogs, or menus that pop up"), affordances
("things the user can act on, like buttons and fields") and
connection lines, under the rule "We'll use words for everything
instead of pictures" [3].

## Unexpected

No source says in text where the elements stand. The frame's idea
has a page definition name "which elements it holds and where they
stand". In every source read the position is a picture ([2], [1],
[5], [8], [6], [10]), and the only positions given in words are named
regions of a page ([2] p. 36, [6]). IFML, in the parts read, gives
containment and no position [14]. A lead for the cards on pages
composed of blocks and on previews: position in text may reduce to a
region and an order within it. This is the agent's reading of an
absence, not a statement of any source.

The card lists "states such as empty, loading and error" among the
fields that may recur. Empty and loading do not recur in the
templates read; they hold conditions per item and rules for errors
(F3). A description built from the older templates alone would miss
the empty, partial and loading states of [11]; one built from [11]
alone would miss the per-item conditions of [2].

The critics of specifications arrived at a description in words. The
breadboard of [3] is the least detailed established textual form of a
screen found: a name, the things that can be acted on, where each
leads, and deliberately no layout.

The description may be the running page. In [15] the documentation of
a service is an HTML prototype in a repository, changed by pull
request, its release notes serving as the record of change. It is a
lead for the card on previews, since the frame has the human "see"
the proposal.

A permanent code for every element is a published rule: [5] forbids
renumbering, retires the code of a removed element and appends new
ones.

## Not found

- No chapter of a UX handbook was read in full. Brown's Communicating
  Design, chapter 7 on wireframes, appeared in a result list as a
  publisher's preview and was not opened; Brown is represented by an
  interview [8] and Hurff by a book excerpt [11].
- No European template of public procurement or systems engineering
  with a specification of a single screen. One process model was read
  and has none (F7). The Swiss HERMES method was searched and nothing
  of it opened; ECSS, the European Commission's project method and
  national templates other than the German were not searched.
- No specification of an open-source product with its screens. The
  two pages of the Ubuntu wiki that were to hold the specification of
  its software centre (the pages named SoftwareCenter and AppCenter)
  returned HTTP 404; a further query found no new location, and the
  Internet Archive's copies could not be reached by the fetch tool.
  The two pages are therefore cited nowhere in this note. No finding
  rested on them; what stays unsupported is the route's own question,
  how an open-source product writes the specification of one of its
  screens. The template pages for the table of interface elements of
  [9] were not opened, and [9] itself holds only a placeholder under
  Detailed Specification.
- The sample specification that [4] links to was not opened, so how
  it writes one screen is not known here.
- No current public template of a product company for a screen
  specification; the company sources are a method [3] and an essay
  [4].
- Responsive behaviour as a field of one screen: in no template read;
  only [5] names it, among the standards common to all views.
- Entry points as a field of one screen: in no template read; ways in
  and out stand in a separate deliverable [2] or diagram [5].
- A source that says where native mobile or desktop screens differ in
  their description: none read; [2] assumes the web (p. 7).
- "State matrix" as a named part of a specification: the search
  returned no source that uses the term so.
- A manual of the United States' digital services on the description
  of a screen: the search returned none.
- A measured comparison of the forms: none found, and none was looked
  for beyond the queries listed; it is another card's question.
- A standard, by number, on the content of a screen specification was
  not searched; it is the card on formal languages and standards.

## Options

A. The tabular document of [2] carried into Markdown: per screen a
head (ID, name, purpose), a table of parts with IDs, a table of
items, a table of actions; the common rules in a document of their
own. It is the most complete and the most checkable, and its IDs fit
a chain of items with stable IDs. It is heavy, it was made for
agreement between a client and a contractor, and its layout is a
figure for which it offers no text.

B. The annotated picture: a preview or wireframe with numbered notes.
It is the lightest and the form UX specialists know. It needs a
picture before there is a description, its notes have no fixed
fields, and a number on a picture holds only while the codes are kept
permanent as in [5].

C. The prose specification, screen by screen under canonical names
[4]. It reads well and carries reasons. It is weak for the data of
items and for any mechanical check.

D. The breadboard first [3]: every screen as a place, its
affordances and where each leads, in words, the detail added
afterwards. It is the cheapest first shape and defers the layout; it
is a skeleton, not a description to build from.

E. A hybrid: per screen the fields that recur (F2) as items with IDs,
actions as short numbered sentences, conditions and the states of
[11] as a group of their own; what is shared and the kinds of element
in a separate document; the layout carried by named regions and by a
preview, not told.

## Relevance to this project

The recommendation: try the first few screens as option E, begun from
the skeleton of option D. It rests on [2] for which fields a screen
holds and for one ID that ties an element to everything said of it,
on [5] for codes that never change, on [11] for the states the older
templates lack, on [3] for a skeleton in words that needs no picture,
and on [1] for keeping the text short and beside what is seen. It is
chosen against option A alone, whose weight and whose origin in
contract agreement do not fit one person working end to end, and
against option B alone, which needs a picture first and leaves the
notes without fields.

The agent's own inferences, not findings of any source:

- The idea under test is half supported. A separate inventory of
  elements is established practice ([13], [5], [2] p. 25), but what
  it defines is the kind of element and the rules all its uses share.
  The function of an element on a given screen is written with the
  screen in both templates that go to that depth ([2], [6]). A small
  definition per element that "carries its function" matches the
  sources for reusable kinds and not for an element that exists on
  one screen.
- "Where they stand" has no established textual form (Unexpected).
  The nearest are named regions and order, with a picture beside
  them.
- The fields of F2 marked as rare (access, ways in and out,
  responsive behaviour, accessibility) are rare in the templates read
  because those were written for the web of their time or for one
  system; their rarity is no evidence that a description can do
  without them.
- Every template read is at least several years old, the youngest
  practice source being [15] of 2025, which describes no fields. That
  the practice has not moved since is not shown.

Consult when: the first template of a screen description is drafted;
the scheme of IDs for screens, elements and actions is decided; it is
decided what is written per screen and what once for all screens; the
question comes up whether element definitions stand apart from page
definitions; someone proposes to drop the description in favour of a
prototype.

## Sources

1. "Use Good Prototype Specifications to Empower Team Collaboration",
   Leeloo Tang and Feifei Liu, Nielsen Norman Group, 2022-06-05
   (byline). https://www.nngroup.com/articles/prototype-specifications/
   Primary (a practitioner organisation's own guidance). Summarised
   fetch. Original.
2. "機能要件の合意形成ガイド(ver.1.0)
   ～「発注者ビューガイドラインver.1.0」改訂版～ 分冊３ 画面編",
   Information-technology Promotion Agency, Japan, Software
   Engineering Center, working group on techniques of agreeing
   functional requirements, 2010-03-31 (printed on the title page).
   https://www.ipa.go.jp/files/000004521.pdf
   Primary (a public agency's guide). Read partially: the title page
   and printed pages 1 to 7, 9 to 13, 15, 16, 19 to 21, 23 to 29 and
   31 to 36 of 197 PDF pages, the opening of each page where a page
   is filled by an example, in the text extracted from the PDF as the
   fetch saved it; part 3, the tips (pp. 45 to 193), not read.
   Original.
3. "Find the Elements", chapter 4 of Shape Up, Ryan Singer, 37signals.
   Undated on the page (a copyright line 1999-2026 only).
   https://basecamp.com/shapeup/1.3-chapter-04
   Primary (a company's own method). Summarised fetch. Original.
4. "Painless Functional Specifications – Part 2: What's a Spec?", Joel
   Spolsky, 2000-10-03 (byline).
   https://www.joelonsoftware.com/2000/10/03/painless-functional-specifications-part-2-whats-a-spec/
   Primary (a practitioner's own essay). Summarised fetch; the sample
   specification it links to not opened. Original.
5. "Cascading UX Specifications", Steven Hoober, UXmatters, 2018-01-08
   (byline).
   https://www.uxmatters.com/mt/archives/2018/01/cascading-ux-specifications.php
   Primary (a practitioner's own method in a practitioner magazine).
   Summarised fetch. Original.
6. "PASIprep Functionality (Template)", PASI Knowledge Base,
   Government of Alberta. Undated (a footer copyright of 2026 only).
   https://extranet.education.alberta.ca/pasidevnet/docs/Business/pasiprep_functionality.html
   Primary (a public administration's own template). Summarised
   fetch. Original.
7. "Lean UX – Getting Out Of The Deliverables Business", Jeff Gothelf,
   Smashing Magazine, 2011-03-07 (byline).
   https://www.smashingmagazine.com/2011/03/lean-ux-getting-out-of-the-deliverables-business/
   Primary (the author's own position). Summarised fetch. Original.
8. "Harnessing the Power of Annotations—An Interview with Dan Brown",
   Jared M. Spool, UX Articles by Center Centre, 2009-04-03 (byline).
   https://articles.centercentre.com/?p=191
   Primary (an interview, the handbook author's own words). Summarised
   fetch. Original.
9. "Specification Template", Apache OpenOffice Wiki, last edited
   2009-06-18 (page footer); the page marks its status as preliminary.
   https://wiki.openoffice.org/wiki/Specification_Template
   Primary (an open-source project's own template). Summarised fetch.
   Original.
10. "Specification Template Help", Apache OpenOffice Wiki, last edited
    2010-03-28 (page footer).
    https://wiki.openoffice.org/wiki/Specification_Template_Help
    Primary. Summarised fetch. Original.
11. "How to fix a bad user interface", Scott Hurff, 2015-08-17
    (byline); the page says it is an excerpt of his book Designing
    Products People Love (O'Reilly, January 2016).
    https://www.scotthurff.com/posts/why-your-user-interface-is-awkward-youre-ignoring-the-ui-stack/
    Primary (the author's own text on his own site). Summarised
    fetch. Original, an excerpt of the book.
12. "Making prototypes", Service Manual, GOV.UK, Design community,
    published 2016-10-18 (date on the page).
    https://www.gov.uk/service-manual/design/making-prototypes
    Primary (a public administration's manual). Summarised fetch.
    Original.
13. "V-Modell XT Bund. Das Referenzmodell für
    Systementwicklungsprojekte in der Bundesverwaltung", version 2.3,
    Informationstechnikzentrum Bund, copyright 2019 (printed in the
    imprint).
    https://www.itzbund.de/static/download/Produkte/VMXT/V-Modell-XT-Bund-2.3.pdf
    Primary (a public process standard). Read partially: title and
    imprint, C.1.10.9 (pp. 120-121), C.1.11.10 (pp. 154-155), the
    dependencies of C.1.12.1 and C.1.12.3 with C.1.12.3.2 (pp. 158,
    163), the method reference Dialog Design Modellierung (p. 275),
    found by a keyword search over the text of all 348 pages extracted
    from the PDF as the fetch saved it. Original.
14. "Interaction Flow Modeling Language", version 1.0, Object
    Management Group, February 2015, OMG document number
    formal/2015-02-05 (both printed on the title page).
    https://www.omg.org/spec/IFML/1.0/PDF
    Primary (a standard). Read partially: title page, clause 1, the
    first paragraph of 7.1, classes 8.3.52 to 8.3.56, in the text
    extracted from the PDF as the fetch saved it. Original.
15. "Creating interactive design documentation for GOV.UK One Login",
    Arindra Das and Matthew Ashton, Government Digital Service blog,
    2025-04-01 (byline).
    https://gds.blog.gov.uk/2025/04/01/creating-interactive-design-documentation-for-gov-uk-one-login
    Primary (the team's own account). Summarised fetch. Original.
16. "Wireflows", Nielsen Norman Group.
    https://www.nngroup.com/articles/wireflows/
    Not opened: it belongs to the card on the user's paths. Never
    cited for content.
17. "Why wireframes should be left to die", Creative Bloq.
    https://www.creativebloq.com/netmag/why-wireframes-should-be-left-die-31411165
    Not opened: the openings were spent; a title in the result list of
    the disconfirming query. Never cited for content.
18. "Against wireframes", jarango.com.
    https://jarango.com/2019/03/14/against-wireframes/
    Not opened: the openings were spent; a title in the result list of
    the disconfirming query. Never cited for content.
19. "Eliminate unnecessary paperwork", Getting Real, Basecamp.
    https://basecamp.com/gettingreal/11.2-dont-do-dead-documents
    Not opened: the openings were spent; a title in the result list of
    the disconfirming query. Never cited for content.

## Opened and not used

None: every page opened is cited above. Three fetches opened nothing:
the two pages of the Ubuntu wiki named under Not found, which
returned HTTP 404 and are cited nowhere, and the first fetch of [5],
which returned a redirect.

## Search record

Queries, in order:

1. wireframe annotations, what to include, guide
2. screen specification template, fields, UI specification document
3. 画面設計書 記載項目 画面項目定義 IPA 機能要件の合意形成ガイド
   画面編
4. Nielsen Norman Group, wireflows, annotations, design
   specifications, handoff
5. "annotated wireframes" or "UI specification", dead or waste,
   prototypes instead of specifications (the disconfirming query,
   first wording)
6. V-Modell XT, Mensch-Maschine-Schnittstelle, Spezifikation, Maske,
   Dialog, Pflichtenheft, Benutzungsoberfläche
7. open-source project, UI specification, wiki, screen spec
8. government service manual, documenting designs, wireframes,
   annotations, developers
9. "getting out of the deliverables business", Lean UX,
   specifications
10. Shape Up, breadboarding, places, affordances, connection lines
11. the Ubuntu wiki, specification, user interface, software centre
12. UI states empty, loading, error, partial, ideal, "UI stack" or
    "state matrix"
13. V-Modell XT, product "Mensch-Maschine-Schnittstelle (Styleguide)",
    Dialogspezifikation, Maskenentwurf
14. Dan Brown, "Communicating Design", wireframes chapter, annotations
15. V-Modell XT, "Mensch-Maschine-Schnittstelle (Styleguide)", Themen
16. HERMES, Detailspezifikation or Systemanforderungen,
    Benutzerschnittstelle, Vorlage
17. wiki specification template, "User Interface", dialog, "UI
    element" table, open-source office suite
18. "annotated wireframes are dead" (the disconfirming query as the
    card words it)
19. "UI specification document is waste" (the disconfirming query as
    the card words it)
20. 画面設計書 不要 プロトタイプ アジャイル 画面仕様書 書かない (the
    disconfirming query in Japanese)
21. the Ubuntu wiki, software centre, design specification, moved or
    archived (in the correction of two citations, below)

Pages opened, fifteen, in order: [1], [2], [3], [4], [5], [6], [7],
[8], [9], [11], [12], [10], [13], [14], [15]. Three further fetches
opened nothing: two pages of the Ubuntu wiki failed with HTTP 404,
and the first fetch of [5] returned a redirect and was repeated at
the address it gave. The three PDFs ([2], [13], [14]) came back from
the fetch as binary and were read in the text extracted from the
saved copy; every HTML page was read through the fetch tool's
summarising model.

What the disconfirming query found. As the card words it, no page
carries either phrase. The result lists held opinion pieces against
wireframes and against documents nobody reads ([17], [18], [19], not
opened), vendor pages defending specifications, and the sources read
as [5] and [7]. Opened under this query: [7], [3], [12] and [15],
which give the expected criticism of heavy specifications and the
preference for prototypes, and [1] and [5], which answer it (F9). The
Japanese wording returned, in its result list only, pages that keep a
screen design document beside a prototype and none that recommends
writing no document; none of them was opened.

Seen in result lists and not opened: Markdown templates of a screen
specification published in 2026 for coding agents (a wireframe
specification template in an npm package named aiwg, a "screen spec"
in an npm package named micro-contracts), which belong to the card on
descriptions written for an agent that builds; a paper on the
annotation of prototypes on a preprint server; the screen
specification templates of a university's information systems group
and of a state health department in the United States.

The run ended by the opening budget: fifteen pages opened and three
fetches that opened nothing. The first part of the card's stop rule
was not reached. The last differently worded queries still returned
material not seen before (the opinion pieces and the 2026 templates
above), and two routes ended thin: the UX handbooks, with an
interview and an excerpt in place of a chapter, and the European
templates, with a negative from one process model.

The correction of two citations. The note first listed the two pages
of the Ubuntu wiki as sources not opened, with their addresses; the
citation check found that neither opens. Query 21 found no new
location for them, and two fetches of the Internet Archive's copies
were refused by the fetch tool, so both citations were dropped, the
entry under Not found says what stays unsupported, and the sources
after them were renumbered. Nothing else of the note was changed.
