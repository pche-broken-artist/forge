---
date: 2026-11-21
project: forge
topic: what stands above the screens: objects, architecture, navigation, and what is claimed for objects first
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-04-above-the-screens
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 4; no known notes named by the card; web sources below
---

# Above the screens stand objects, places and paths, described in four traditions that disagree on the unit

<!-- Shape: templates/research.md -->

## In short

Practice and literature describe the structure above single screens in
four traditions, each with a unit of its own. The conceptual-model
literature and object-oriented UX take the object: a table or a map of
the objects the user sees, with their attributes, their operations and
their relationships, written before any screen. Information
architecture and the flow notations take the page or the place and the
paths between them: a diagram vocabulary, a wireflow, or a breadboard
written in words alone. Model-based engineering and its standards put
a task-and-domain model above an abstract interface and bind nested
view containers to a domain model. Concept design rejects the object
and takes a unit of behaviour. What is said to follow from describing
objects first (a simpler and more consistent interface, one
vocabulary, a first cut of the data model, less rework, navigation
through the content itself) is claimed by the methods' authors; no
source opened measures it, and the only evidence found is case studies
for the extreme variant that generates the interface from the domain
objects. How sure: each tradition is read from a primary source by its
author, but the book literature of information architecture and of
usage-centred design was not read. The disconfirming query found no
published criticism of object-oriented UX; the criticism that exists
is older, is aimed at pure and generated object-oriented interfaces,
and could be read only in its target's account. Unexpected: the one
workflow of 2025 for an AI builder that was opened makes the
conceptual model after the sketch of the screens and lets the model
derive it.

## Question

The frame, condensed from the packet: a framework carries an idea down
a chain of versioned Markdown documents, worked by a human with an AI
agent, and wants the same for the user interface and the user
experience of an application; a description in text is proposed by an
agent, tuned by a human and handed to a build stage. One idea from
practice is to be tested, not assumed: every element of a screen has a
small definition of its own, and a page definition names which
elements it holds and where they stand.

The card, verbatim:

> #### Card 4: What stands above the screens
> - **Question:** How do practice and literature describe the structure above single screens (the conceptual model of objects with their attributes, actions and relationships; the information architecture; the navigation and the map of screens), in which textual forms, and what do they claim follows from describing objects before screens?
> - **Why it matters:** it decides what the unit of the description is: a screen, an object or an element.
> - **What would answer it:** method literature by its authors.
> - **Where to look:** the literature on conceptual models in interaction design; object-oriented UX; information architecture; how domain modelling is tied to interface design. Search words from card 1: "design specs", "wireframe annotations", "prototype specifications", "wireflows", "state matrix"; and the model-based words "abstract user interface", "concrete user interface", IFML's "view container", "view component", "interaction flow".
> - **Disconfirming query:** "object-oriented UX criticism"; expected: little published criticism, some doubt about cost.
> - **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

Known items: none; the card names no known note of the project.

The baseline the note must beat is the answer given without research:
that the screen is the unit, that a site map and a flow diagram stand
above it, and that "object-oriented UX says objects first". The note
beats it only where it names the form each method's author prescribes,
keeps what is claimed apart from what was measured, and says where the
traditions disagree about the unit. In this note "design" means the
design of the interface, never the technical design of spec-driven
kits and never a visual identity.

## Key findings

**F1. A conceptual model is written as an object/operation analysis: a
table of the objects the user sees, their attributes and the
operations on them, with two kinds of relationship, a vocabulary and
scenarios beside it.** [single source; practitioner claim by the
method's authors] Johnson and Henderson define the conceptual model as
"the model of the application that the designers want users to
understand" and say that it "describes abstractly — in terms of tasks,
not keystrokes, mouse-actions, or screen graphics — what users can do
with the system and what concepts they need to be aware of" (section
"Conceptual Model: a Model for Users' Mental Model"). Its core is "an
enumeration of the user-visible object-types in the application, the
attributes of each object-type, and the operations that users can
perform on each object-type" (section "Object/Operation Analysis"),
shown as a table of three columns, Objects, Attributes, Operations. In
the example of an office calendar the row Event carries the attributes
"name, description, date, time, duration, location, repeat, type
(e.g., meeting)" and the operations "examine, print, edit
(attributes)" (Table 1). Objects "can usually be organized in a
type-hierarchy" and into a "containment hierarchy" (same section); the
article gives no notation for either. Kept out of the model: "Purely
presentational and purely implementation object-types have no place in
an application's conceptual model." The goal is a model "as simple as
possible" and "as focused on the task-domain as possible". The article
names neither task analysis as a step before the model nor metaphors
as a part of it [1]; the authors' article of 2002 [16] and their book,
which may say more, were not read.

**F2. Its authors claim six consequences of designing the conceptual
model before the interface, and the article measures none of them.**
[single source; practitioner claim] Under "Summary: Six Benefits of
Conceptual Models": laying out objects and operations lets designers
notice shared operations, and "Common operations across objects make
the UI simpler for users to learn and remember"; it forces thought
about the relative importance of concepts, their relevance to the task
domain and the two hierarchies; it is "a starting point for the
development of a product vocabulary", which "helps ensure that terms
are used consistently"; it allows scenarios that "describe tasks and
goals without revealing the UI-level user interactions", reusable as
use cases, in documentation and as tasks of a usability test; it
"provides a first cut at the app's object-model"; and it is said to
"reduce development resources by reducing rework". The order is
stated, "the user interface is designed after the conceptual model has
been designed", and so is the way back: "Designing the UI from the
conceptual model may expose problems in the conceptual model" (section
"A Conceptual Model Provides a Foundation for the App and the
Project") [1].

**F3. Object-oriented UX writes the same content as an object map made
from the nouns of the goals and adds a matrix of calls to action; its
present process is named in the open but not described there.**
[single author and the author's own site; practitioner claim, vendor
documentation] Prater's article of 2015 gives four steps, "Step 1:
Extract objects from goals", "Step 2: Define core content of objects",
"Step 3: Nest objects for cross-linking", "Step 4: Forced ranking",
worked on colour-coded sticky notes (objects, core content, metadata,
nested objects) into what she calls an object map [2]. Her article of
2016 adds the "CTA Inventory", "just a fancy list of potential CTAs
organized around your objects", first as sticky notes on the map and
then as a table: "Using a Google spreadsheet, I create a matrix" [3].
The author's site names the present process ORCA, "Objects,
Relationships, CTAs, and Attributes", running "from Object Discovery
to Attribute Prioritization, Sketching, Prototyping, & Testing" [5],
and calls it a "repeatable OOUX design methodology" [4]; neither page
lists its steps or its artefacts, and the same site sells the training
[4]. The ancestry is acknowledged: the 2015 article cites Collins's
book "Designing Object Oriented User Interfaces" of 1995 and the
practice of content modelling [2].

**F4. What object-oriented UX claims for objects before actions and
screens, and the limits its author states herself.** [single author;
practitioner claim, no measurement] The order: "putting object design
before procedural action design" and "We determine the actions after
first defining the objects" (section "Mobile first, content first, and
objects first") [2]; the fault of beginning with flows is put as "We
are designing our actions without a clear picture of what is being
acted on" [3]. The claims (section "OOUX is powerful"): to "match your
user's mental model", to "ensure simplicity", that "objects can be
iterated on without affecting the rest of the system", to "build
better APIs with portable, independent objects", navigation through
the content ("The content is the navigation"), and a shared language,
since defining the objects "provides a scaffolding for team
communication" [2]; later also to "write project estimates with
greater accuracy" [3]. The limits: "it's a new ingredient to add to
your current process" and the ranking is "the most diabolically
difficult step" [2]; "OOUX and a CTA Inventory will not help you
design the interactions themselves", and "be prepared to iterate" [3].

**F5. Information architecture describes the structure above pages as
a diagram of pages and their relationships, kept apart from the
navigation and from the interface; its unit is the page.** [single
source; the notation's author, a web-era practitioner standard dated
2002] Garrett's visual vocabulary, version 1.1b, serves "to describe,
at a high level, the structure and/or flow of the user experience of a
Web site" (section "Initial considerations"). It draws the
"macrostructure" and leaves the page-level "microstructure" to "other
documents"; "Note that conceptual structure is not the same as
navigational structure", and "if you find yourself drawing buttons and
fields, you're probably loading the diagram down with excess detail"
(section "Conceptual underpinnings"). "The basic unit of user
experience on the Web is, of course, the page", which is "a unit of
presentation, not (necessarily) a unit of implementation" (section
"Simple elements"). The elements are the page, the file, stacks of
both, connectors and arrows, concurrent sets, continuation points,
areas and iterative areas, flow areas with references, and the
conditional elements. What is textual in it are the unique labels, the
"Unique numeric identifiers and type designations" and the notes in a
footnote or an appendix cited as "(3a)". It is a visual notation, made
to be "Whiteboard-compatible" and "Tool-independent", not a textual
form. It holds no objects: its own model is that "The system presents
the user with paths", along which the user moves by actions that
produce results [6]. Whether it is still in use was not checked.

**F6. The map of screens has two forms of flow: the wireflow, a
diagram with the screens in it, and the breadboard, written in words
alone.** [two sources, each the publisher of its form; practitioner
claims] "Wireflows are a design-specification format that combines
wireframe-style page layout designs with a simplified flowchart-like
way of representing interactions"; flowcharts alone "lack the page
context"; wireflows "are well suited for representing dynamic changes
on one or few pages inside an app, and work less well for capturing
flows through a large number of relatively static pages linked
together" (Conclusion) [7]. The breadboard of Shape Up is the opposite
choice: "We'll use words for everything instead of pictures." It has
three things: "Places: These are things you can navigate to, like
screens, dialogs, or menus that pop up", "Affordances: These are
things the user can act on, like buttons and fields", and "Connection
lines: These show how the affordances take the user from place to
place". The notation is a name underlined ("We draw it by writing the
name of the place and underlining it"), under which "Affordances go
below the line to indicate they can be found at that place" (section
"Breadboarding"). The claim: "If we start with wireframes or specific
visual layouts, we'll get stuck on unnecessary details"; where the
idea itself is visual, a "fat marker sketch" takes the breadboard's
place. The chapter speaks of no object and no domain model [8]. The
agent's own inference: the breadboard is the one form found that is
text as it stands, a name, a list under it and a target per item.

**F7. Model-based engineering and its standards put a model of tasks
and of the domain above an abstract interface, and describe the map of
screens as nested view containers bound to a domain model; these are
metamodels with diagrams, not prose, and by the W3C note's own account
of 2014 no tool implemented its standard.** [standard; a W3C Working
Group Note of 2014 that calls itself work in progress, and an OMG
formal specification of 2015] The W3C note names four levels, Task and
Domain, Abstract UI, Concrete UI and Final UI: "The Task and Domain
models correspond to the hierarchies of tasks that need to be
performed on/with domain objects (or domain concepts)", and "The
Abstract UI (AUI) model expresses the UI in terms of Abstract
Interaction Units (AIU)", which "can be grouped logically to map
logically connected tasks or domain objects" (Introduction). Of the
tools it lists, "none of them, so far, implements the MBUID standard",
and the note's status says "It is inappropriate to cite this document
as other than work in progress" [9]. IFML describes "the view part of
the application, made of view containers and view components; the
objects that embody the state of the application", and "the binding of
view components to data objects and events" (clause 1, Scope). Its
top-level model "contains an InteractionFlowModel, a DomainModel, and
may optionally contain ViewPoints", where "DomainModel represents the
business domain view of the application" (clause 8, at Figure 8.1).
Containers nest; in a container marked XOR the contained elements are
"presented to the user only one at a time"; a landmark container
"represents an implicit link between all the other ViewElements and
the ViewContainer"; and "ViewComponents exist only inside
ViewContainers" [10]. The depth of these languages is another card's.

**F8. The strongest claim, and the only evidence found, belongs to the
variant that ties the interface straight to the domain model: naked
objects show the domain objects themselves and generate the interface
from them.** [single source; a doctoral thesis with case studies;
contested] In Pawson's thesis "the domain objects (such as Customer,
Product and Order) are exposed explicitly, and automatically, to the
user, such that all user actions consist of viewing objects, and
invoking behaviours that are encapsulated in those objects" (1.3). The
style is object-action or "noun-verb", set against "the more
widely-used 'verb-noun' style, where the user selects a task from a
menu and then specifies the data on which that task is to operate"
(chapter 8). Four benefits are claimed as demonstrated: systems that
are "more agile", "a more empowering style of interaction", a
development cycle "significantly shortened", and "a common language
between application developers and users" (1.3). The evidence is case
studies, among them a benefits system of a government department
(chapter 4, read here by its headings only). The thesis limits its own
claim: "It is not suggested that OOUIs are universally better than
other forms of user interface" (3.3). It also reports its critic:
Constantine, in December 2002, "objected both to the idea of
auto-generated user interfaces and to the advocacy of pure
object-oriented user interfaces", both "on the grounds of usability"
(8.3) [11]. That critique was not read in the original, so its
argument is known here only from the account of the one criticised.

**F9. Concept design denies that the object is the unit: a concept is
a unit of behaviour with a purpose, and neither a class nor a widget
is one.** [single author; method literature, a tutorial of 2023 on the
site of the author's book] For Jackson "a concept is a coherent unit
of functionality" (section "Two sides of a coin"); "Concepts are
always experienced by the user of an application", and "A concept can
be understood by itself without reference to other concepts" (section
"The criteria"). What does not qualify: "A user interface widget is
not a concept, nor is a color scheme or a UI skin" (same section), and
"Classes in OOP (and similarly abstract data types) are not generally
user-facing, and are rarely independent" (section "Distinctions").
Against the reading of a concept as a class of things: "In concept
design, however, concepts are defined by their dynamic behavior"
(section "A new kind of mental construct"). A concept is told in
"three essential parts", the name, the purpose and the operational
principle. The claims: independence makes concepts "reusable in
different contexts, not only at the design level but at the
implementation level too", and familiarity "is what makes it possible
for users to start using a new app without reading a manual". The page
says nothing of screens or of the map between them [12]. This
contradicts F3 and F4 on the unit: there the system is cut by nouns
("Instead of slicing up a system by verbs, OOUXers slice by nouns"
[4]), here by behaviour.

**F10. Usage-centred design places an abstract prototype between the
task model and a realistic prototype; its content model and its
navigation map could not be read in a primary source.** [single
source, the abstract only] Constantine's abstract prototypes are "a
form of representation for specification and exploration of visual and
interaction design ideas that is intermediate between abstract task
models and realistic or representational prototypes", with "a formal
vocabulary for expressing visual and interaction designs without
concern for details of appearance and behavior" (abstract) [13]. The
finding rests on the abstract alone.

**F11. In one workflow of 2025 for an AI builder the conceptual model
is a file beside the sketch, made after the sketch and by the
model.** [single source; practitioner article of 2025-10-03, one
worked example, no measurement] Gilyov sketches the screens first,
annotates them, and then lets a model "generate a comprehensive
description of the conceptual model based on the sketch", by a prompt
that says "Generate the conceptual model description in the Mermaid
format using a UML class diagram"; the result is kept as `Model.md`,
and "our intent is fully expressed in two files: Sketch.png and
Model.md". He would write the model himself only "in the case of a
more complex application, where the model cannot be simply derived
from the UI". His claims: "a clear understanding of all objects, their
attributes, and relationships between them is key to good design", and
a prototype made this way "is built from a stable, unambiguous
specification". The article cites neither the conceptual-model
literature nor object-oriented UX [14]. This contradicts F2 and F4 on
the order, not on the worth of the model.

**F12. The disconfirming query found no published criticism of
object-oriented UX.** [the absence is the finding; two result lists
and one page opened] Two wordings of the query returned explanatory
and promotional pages. The one page whose title sets objects against
tasks sides with objects ("using tasks as a basis for interface design
adds another layer for users to work through"), states no
disadvantage, and carries its only doubt in a reader's comment: "What
should be noun-verb vs. verb-noun should be conscious decision" [15].
The criticism that was found is older and is aimed at the pure and
generated variant (F8). Doubt about cost appears only as the author's
own caveats (F4), not as a doubt published by anyone else. The
expectation of the card held for "little published criticism"; "some
doubt about cost" was not found as a published doubt.

**F13. The sources disagree on the unit, and none of them argues for
the element.** [contested; the agent's reading across the method
literature above, not a statement of any one source] The unit is the
object in [1], [2] and [11]; the page or the place with its paths in
[6], [7] and [8]; the concept in [12]; the task with the domain model,
and below it the nested container, in [9] and [10]. Wherever a source
goes below the screen, the element is either kept out of the
structural description or defined inside its place: [6] wants no
buttons and fields in the diagram, [1] wants no presentational objects
in the model, [8] lists affordances under their place, and in [10]
"ViewComponents exist only inside ViewContainers". No source opened
gives an element a definition of its own above the screens; components
of design systems are another card's and were not looked at.

## Unexpected

The card assumes that the unit is a screen, an object or an element;
three sources describe a unit that is none of the three. The concept
of [12] is a unit of behaviour that spans screens. The place of [8] is
wider than a screen ("screens, dialogs, or menus that pop up"). The
view container of [10] nests, so that a screen is one level of
containment among several. This is a lead on the question of the unit,
not an answer to it.

The order "objects before screens" is not the order of the one recent
workflow for an AI builder that was opened: there the screens are
sketched first and the model is derived from them by a language model,
the author keeping the reverse order for complex applications only
[14]. One article by one practitioner; whether this is where practice
is going was not established.

The present state of object-oriented UX is not described on the open
pages that were opened: the site of its author names the process and
its four letters and sells the training [4] [5]. Whoever takes the
method as a reference takes either two articles of 2015 and 2016 or a
body of knowledge that was not found in the open.

The foreword to [11], by the author of the model-view-controller
pattern, says of the pattern that "Its purpose was to bridge the gap
between the user's mind and the computer-held data" and that "The most
important participant in the original MVC architecture, the user's
mind, was somehow forgotten". A lead only: the split between a model
of objects and a view of them began as a claim about the user's mental
model, which is the claim F1 and F4 make again.

## Not found

- No controlled study and no measured comparison of describing objects
  first against describing screens first, on usability, on rework or
  on the quality of what is built: not in any page opened and not in
  the result lists of the queries below. The two controlled
  experiments [11] mentions concern coupling and ease of change of the
  code, as the thesis reports them (1.1), not the interface.
- No published criticism of object-oriented UX by a researcher or by a
  practitioner writing against it: looked for with the card's query
  and one rewording.
- Constantine's critique of naked objects of December 2002 in the
  original: the host that held his papers now serves a registrar's
  parked page; searched for by title in two queries.
- The content model and the navigation map of usage-centred design in
  a primary source: the working paper on the same host is gone, the
  book is not online, and the publisher's page of [13] shows the
  abstract only.
- The steps and the artefacts of the ORCA process: not on the two
  pages of the author's site that were opened.
- The components of a conceptual model as the article of 2002 lists
  them, and its place after task analysis: the copy [16] came back
  from the fetch as unreadable binary.
- A textual form for a site map or an information architecture from a
  method's author: [6] is a visual vocabulary; no outline or Markdown
  convention was found in the pages opened, and the result list of the
  one query on it was not searched further.
- Not looked at, the opening budget being spent: the book literature
  of information architecture and an article on its principles that
  the search results named, content modelling, the books on
  object-oriented user interfaces that [2] and [15] cite, and
  domain-driven design beyond the route of [11].

## Options

1. **The screen as the unit, with a light map above it.** A list of
   places, what the user can act on in each, and where each action
   leads, as in [8]. Cheapest, and a visible result soonest. Nothing
   in it holds the objects the same from screen to screen, and the
   vocabulary is left to drift.
2. **The object as the unit above the screens.** A table of the
   user-visible objects with attributes, operations and the two
   relationships, as in [1], or an object map with a matrix of calls
   to action, as in [2] and [3]; screens then cite the objects. Gives
   the build stage one vocabulary and a first cut of the data model.
   Costs a round before anything is seen, rests on unmeasured claims,
   and by its own author's word does not describe the interactions
   [3].
3. **Both: objects, and places with paths, side by side.** The split
   [10] makes between a domain model and an interaction-flow model,
   kept in words. Covers what each form alone leaves out. Two
   descriptions to keep in step, and a rule is needed for which of
   them changes first.
4. **The concept as the unit.** A name, a purpose and an operational
   principle per concept, as in [12]. Strong on purpose and on
   behaviour that spans screens. One author's method; the page read
   says nothing of screens or of navigation.
5. **Screens first, the model derived from them.** The order of [14]:
   a first draft of the screens, then the objects read out of it.
   Quick; the model takes over whatever the sketch got wrong, and its
   own author keeps it for simple applications.
6. **A standard's metamodel as the form.** The levels of [9] or the
   containers of [10]. Complete and precise. Diagram languages and
   interchange formats, not prose, and little adopted by the account
   of [9].

## Relevance to this project

The recommendation is the agent's own inference from the findings, not
the result of any one source. Let the description carry two things
above its screens, both in words. First the objects: a table of the
objects the user sees, with their attributes, their operations and
their relationships, in the vocabulary of the documents above, citing
those documents wherever an object is already defined there rather
than describing it again. Then the places and the paths: each place
with what the user can act on there and where each action leads. A
screen then names the objects it shows and the place it is. This is
option 3.

It rests on the form and the order of [1], on the words-only map of
[8], on the split that the standard [10] makes between a domain model
and an interaction-flow model, and on the statement of [3] that the
objects do not describe the interactions, so that neither half does
alone. The agent's own inference: where requirements, a solution
design and user stories already stand above the description, most
objects can be read from them, and the cost that speaks against
objects first, a round before anything is seen, is smaller than in the
practice the sources describe.

It is chosen against the screen alone (option 1), which leaves the
vocabulary unguarded; against the object alone (option 2), which
leaves the paths undescribed; against the concept (option 4), whose
one page read does not reach the screens; and against a standard's
metamodel (option 6), which is not text a human tunes. Against option
5 it is chosen only weakly: the order is contested by [14], nothing
measures either order, and a first draft of screens made before the
table is finished contradicts no source read here.

For the idea under test, that every element has a small definition of
its own and a page names its elements: nothing read here places the
element above the screens. The forms that reach the element define it
inside its place ([8], [10]), and the forms above the screens keep it
out ([1], [6]). That is the agent's reading of four sources, and the
card on components in design systems may read otherwise.

What stays uncertain: every consequence claimed for objects first is
an author's claim; the present practice of object-oriented UX and the
book literature of information architecture were not read.

Consult when: the unit of the interface description is being decided;
it is asked whether the objects get a document of their own, a section
or a citation of the documents above; a form for the map of screens is
chosen; someone proposes object-oriented UX, ORCA or concept design as
the method; the order of first draft and object table is argued; the
element-first idea is weighed.

## Sources

How the pages were read: [1] to [5], [7] to [9], [12], [14] and [15]
through a fetch that returns a summary by a small model, which is a
tertiary reading; every phrase quoted from them above was then checked
word for word against the text of the page fetched directly, curly
quotes and dashes set aside. [6], [10], [11] and [13] were read from
the page or the PDF text directly.

1. "Conceptual Models in a Nutshell", Jeff Johnson and Austin
   Henderson, Boxes and Arrows, 2013-01-22 (byline).
   https://boxesandarrows.com/conceptual-models-in-a-nutshell/
   Kind: primary (the method's authors). Read: summarised fetch, the
   quotes checked against the page text. Original.
2. "Object-Oriented UX", Sophia V. Prater, A List Apart, 2015-10-20
   (byline).
   https://alistapart.com/article/object-oriented-ux/
   Kind: primary (the method's author). Read: summarised fetch, the
   quotes checked against the page text. Original.
3. "OOUX: A Foundation for Interaction Design", Sophia V. Prater, A
   List Apart, 2016-04-19 (byline).
   https://alistapart.com/article/ooux-a-foundation-for-interaction-design/
   Kind: primary. Read: summarised fetch, the quotes checked against
   the page text. Original.
4. "What is Object Oriented UX | OOUX", the site of the method's
   author, undated.
   https://www.ooux.com/what-is-ooux
   Kind: primary, a vendor's documentation of its own method; the page
   sells training. Read: summarised fetch, the quotes checked against
   the page text. Original.
5. "The ORCA Series", the same site, undated.
   https://ooux.com/hi/orcaseries
   Kind: primary, vendor documentation; a listing of a podcast series.
   Read: summarised fetch of the first 100,000 characters of about
   111,500, the two quotes checked against the page text. Original.
6. "A visual vocabulary for describing information architecture and
   interaction design", Jesse James Garrett, version 1.1b, 2002-03-06
   (version line on the page).
   http://www.jjg.net/ia/visvocab/
   Kind: primary (the notation's author). Read: directly, partially:
   from the summary through "Commonalities: areas and iterative
   areas"; the sections on flow areas, references and the conditional
   elements by their titles in the table of contents only. Original.
   The page answers over plain HTTP; over HTTPS the host's certificate
   does not match its name.
7. "Wireflows: A UX Deliverable for Workflows and Apps", Page
   Laubheimer, Nielsen Norman Group, 2016-12-04 (byline).
   https://www.nngroup.com/articles/wireflows/
   Kind: primary for the form as this publisher defines it. Read:
   summarised fetch, the quotes checked against the page text.
   Original.
8. "Find the Elements", chapter 4 of "Shape Up", Ryan Singer, published
   by the company whose method it is; undated on the page, which
   carries a copyright line only.
   https://basecamp.com/shapeup/1.3-chapter-04
   Kind: primary (the method's author). Read: summarised fetch, the
   quotes checked against the page text. Original.
9. "Introduction to Model-Based User Interfaces", W3C Working Group
   Note, 2014-01-07 (document header); editors Gerrit Meixner, Gaëlle
   Calvary, Joëlle Coutaz.
   https://www.w3.org/TR/mbui-intro/
   Kind: primary (standards body). Read: summarised fetch, the quotes
   checked against the page text. Original.
10. "Interaction Flow Modeling Language", version 1.0, Object
    Management Group, document formal/2015-02-05, February 2015 (title
    page).
    https://www.omg.org/spec/IFML/1.0/PDF
    Kind: primary (the standard). Read: directly, partially: the title
    page, clause 1 Scope, and by text search of the 144 pages the
    passages on ViewContainer, ViewComponent, DomainModel and the
    attributes isLandmark and isXOR. Original.
11. "Naked objects", Richard Pawson, thesis submitted to the University
    of Dublin, Trinity College, June 2004 (title page), in the
    electronically published version with a foreword by Trygve
    Reenskaug.
    https://causeway.apache.org/docs/2.0.0/_attachments/Pawson-Naked-Objects-thesis.pdf
    Kind: primary (the approach's author); secondary for Constantine's
    critique, which it reports. Read: directly, partially: the title
    page, the foreword, the contents, section 1.3, the opening of
    section 3.3, and by text search of the 223 pages the passages on
    the noun-verb style and on Constantine in chapter 8. A copy, kept
    among the documentation of an open-source project; the record of
    the thesis in the university's repository is [17].
12. "Concept criteria: what's a concept?", Daniel Jackson, the site of
    his book "The Essence of Software", 2023-09-11 (byline).
    https://essenceofsoftware.com/tutorials/concept-basics/criteria/
    Kind: primary (the method's author). Read: summarised fetch, the
    quotes checked against the page text. Original.
13. "Canonical Abstract Prototypes for Abstract Visual and Interaction
    Design", Larry L. Constantine, in "Interactive Systems. Design,
    Specification, and Verification", Springer, 2003, pages 1 to 15,
    DOI 10.1007/978-3-540-39929-2_1 (structured data of the page).
    https://link.springer.com/chapter/10.1007/978-3-540-39929-2_1
    Kind: primary. Read: directly, partially: the metadata and the
    abstract; the full text is not on the page. Original (publisher's
    page). The page redirects through a cookie check before it shows.
14. "Intent Prototyping: A Practical Guide To Building With Clarity
    (Part 2)", Yegor Gilyov, Smashing Magazine, 2025-10-03 (byline).
    https://www.smashingmagazine.com/2025/10/intent-prototyping-practical-guide-building-clarity/
    Kind: primary for the author's own practice. Read: summarised
    fetch, the quotes checked against the page text; part 1 of the
    series not opened. Original.
15. "Object-focused vs Task-focused Design", Everyl Yankee, UX Mastery,
    2012-12-07 (byline), with readers' comments to 2021.
    https://uxmastery.com/object-focused-vs-task-focused/
    Kind: secondary (a practitioner's article on others' work). Read:
    summarised fetch, the quotes checked against the page text.
    Original.
16. "Conceptual Models: Begin by Designing What to Design", Jeff Johnson
    and Austin Henderson, the article of 2002 as the search results
    name it; a copy among the materials of a university course.
    https://courses.dubberly.com/frameworks_2024_fall/Conceptual_ModelsInteractionsPaper.pdf
    Kind: primary, a copy. Not opened as text: the fetch returned the
    PDF as unreadable binary; never cited for content.
17. The record of [11] in the repository of the university, found by
    search.
    https://edepositireland.ie/handle/2262/86687
    Kind: primary, the original of [11]. Not opened: found after the
    opening budget was spent; never cited for content.

## Opened and not used

Every page opened is cited above; [5] for little more than the
expansion of the acronym. Fetched and yielding nothing to read:

- The copy of the 2002 article [16]: returned as unreadable binary;
  superseded by [1].
- The page of [6] over HTTPS, the same path on the author's other
  host, and an archive snapshot of it: a certificate that does not
  match, a 404 and a host the fetch tool may not reach; [6] was then
  read over plain HTTP.
- The working paper on canonical abstract components on its authors'
  former host: a registrar's parked page, nothing to read.
- The page of [13] through the fetch tool: a redirect to a cookie
  check; read directly afterwards.

## Search record

Queries, in order:

1. conceptual model interaction design objects attributes actions
   relationships
2. object-oriented UX
3. object-oriented UX criticism (the card's disconfirming query)
4. Johnson Henderson "Conceptual Models" "begin by designing what to
   design" objects/actions analysis
5. information architecture site map navigation deliverables visual
   vocabulary Garrett
6. naked objects criticism Constantine, task-oriented versus
   object-oriented user interface
7. breadboarding places affordances connection lines Shape Up
8. OOUX limitations doubts, not worth cost, task-first critique (the
   disconfirming query reworded)
9. Constantine Lockwood usage-centered design content model navigation
   map canonical abstract prototypes
10. Daniel Jackson "Essence of Software" concept design, purpose,
    state, actions, operational principle
11. IFML "view container" "view component" "interaction flow" domain
    model OMG specification
12. wireflows UX deliverable workflows apps user flow screen map
13. Constantine "The Emperor Has No Clothes" "Naked Objects Meet the
    Interface"
14. object map conceptual model before screens AI coding agent prompt
    OOUX 2025
15. Dan Brown "Eight Principles of Information Architecture" "principle
    of objects"
16. ORCA process objects relationships calls-to-action attributes,
    object map, matrices, object guide
17. essenceofsoftware.com tutorials concept structure "operational
    principle" concept criteria familiarity
18. Constantine "Canonical Abstract Prototypes for Abstract Visual and
    Interaction Design" pdf
19. Larry Constantine naked objects "emperor" interface critique
20. "ORCA" "Objects, Relationships, CTAs, Attributes", limited to the
    domains of the method's author
21. Richard Pawson "Naked objects" PhD thesis 2004, original
    publication

Pages opened, fifteen, in order: [2], [8], [1], [7], [3], [6], [13],
[5], [12], [9], [14], [15], [4], [11], [10]. Six further fetches
returned nothing to read and are listed under Opened and not used.
Pages already opened were fetched again to check the quotes; no new
page was opened for that.

The disconfirming query: run as put (query 3) and reworded (query 8).
Both result lists held explanatory and promotional pages on
object-oriented UX and no critique of it. Of the two results whose
titles suggested doubt, one was opened [15] and sides with objects;
the other, a practitioner's post of 2023 on unintuitive objects, was
not opened. Queries 6, 13 and 19 found that a critique of the pure and
generated object-oriented interface exists and could not reach its
text.

The run ended by the opening budget: fifteen pages opened. Of the
card's stop rule at that moment: a differently worded disconfirming
query had brought nothing new, and the routes of conceptual models,
object-oriented UX, information architecture, the map of screens and
domain modelling each had a primary source by its author; the route of
usage-centred design had an abstract only, and the book literature of
information architecture had not been opened.
