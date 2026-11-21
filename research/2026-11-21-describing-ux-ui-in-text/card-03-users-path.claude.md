---
date: 2026-11-21
project: forge
topic: how a user's paths are described in text and where they live against the screens
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-03-users-path
derived_from: the plan: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 3; the known note research/2026-10-13-what-a-brd-contains-and-how-it-is-found-today.md; web sources below
---

# The user's paths in text: what each method is for, at what level, and where it lives against the screens

<!-- Shape: templates/research.md -->

## In short

The methods the card names describe a user's path at different
levels and do not compete for one place: a journey map stands above
any one product, a story map arranges a backlog, a use case, an
essential use case and a scenario state one goal without the
interface, a user flow and its relatives (the wireflow, the
breadboard, the flow shorthand) walk one task through the screens,
and a state machine holds the behaviour of a component or of the
application's modes. On where the path lives against the screens the
sources fall into two families. The authors of use cases, of
scenario-based design and of the model-based standards keep the path
free of the interface and put a second artefact between it and the
screens: in the Rational Unified Process a storyboard for a use
case, traced to it, and one navigation map for the system.
Product-design practice fuses the two: the screens are the steps of
the flow and there is no link left to keep. The third arrangement
the card asks about, the path as a part of each screen only, was
seen only in result lists of tool vendors' pages and in no source
opened, and no source measures one arrangement against another.
How sure: the statements on each method rest on its own author's or
standard's page, every one read through a summarising fetch; three
primaries could not be read (essential use cases in their authors'
own text, the IFML specification, the handbook chapter on
scenario-based design), so those routes stand on thinner ground. The
disconfirming query confirmed the expected advice, the path before
the screens; a second wording of it found a counter-position,
object-oriented UX, which puts the objects before the flows. The
one unexpected thing: the author of the textual flow notation calls
every such diagram disposable, which is the opposite of a kept,
versioned document.

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

#### Card 3: The user's path
- **Question:** How are the paths of a user described in text (use
  cases and essential use cases, task models, user flows, journey
  maps, story maps, scenarios, state machines): what is each for and
  at what level, and where does it live against the screens: a
  document of its own that the screens are cited from, a part of
  each screen, or both; and how are the links between a path and its
  screens kept?
- **Why it matters:** the author asks where the user's paths belong
  and whether they stand alone.
- **What would answer it:** the methods as their authors and their
  standards state them.
- **Where to look:** the original literature of use cases, essential
  use cases and story mapping; practitioner organisations on journey
  maps against user flows; IFML; statecharts and SCXML; task-model
  notations; breadboarding. The known note on business requirements
  for the forms of a use case. Search words from card 1: "design
  specs", "wireframe annotations", "prototype specifications",
  "wireflows", "state matrix"; and the model-based words "abstract
  user interface", "concrete user interface", IFML's "view
  container", "view component", "interaction flow".
- **Disconfirming query:** "user flows or screens first", "journey
  maps are useless"; expected: advice to describe flows before
  screens.
- **Stop rule:** nothing new from a differently worded query and
  every route has a primary source; ten to fifteen pages opened.

The baseline, what this note must beat: the known note of 2026-10-13
on business requirements gives the three forms of a use case (brief,
casual, fully dressed) and its three levels, sets a `UC` item at the
level of a user goal, and says that links live in the items while a
matrix is only a view of them. It says nothing of the interface, of
any other way of describing a path, or of where a path stands against
the screens. This note has to add the purpose and the level of each
method from its own source, and the arrangements of path against
screens that are documented, each with the way its links are kept.

## Key findings

How the pages were read: every page below was read through a
summarising fetch, a tool that hands the page to a small model which
answers questions about it. By the brief that makes each reading a
tertiary one. The quotes are as that fetch returned them, asked for
verbatim and with their place in the page, and were not compared with
the raw page; where the fetch paraphrased, this note says "as the
fetch reports it".

**F1. Each method the card names has a purpose and a level that its
own source states, and the methods do not compete for one place.**
[consensus within each method's own community; practitioner claims
and standards; the ordering into one table is the agent's own]

| Method | What it is for | Level | What its source says of screens | Source |
|---|---|---|---|---|
| Journey map | understanding a whole experience toward a high-level goal: actions, thoughts, emotions, channels | "Macro: Broad and high-level"; many touchpoints over days, weeks or months | nothing; it stands above any one product | [1] |
| Story map | arranging a backlog so that the whole stays in view; planning releases | activities over user tasks over stories | nothing | [2] |
| Use case | requirements: "an actor trying to achieve a goal by using the system", failure included | one goal; the forms and levels of the known note | the design of the interface is kept out | [3] |
| Essential use case (task case) | the same, reduced to intention: two columns, the user's intention and the system's responsibility | one goal, free of technology | written to avoid assumptions about "the user interface yet to be designed" | [4], [3] |
| Scenario | envisioning and discussing use: "narrative descriptions of specific task episodes" | one concrete episode, at the level "people construe their work to themselves" | the tasks first, the interface after | [5] |
| Task model | "the hierarchies of tasks that need to be performed on/with domain objects" | the top level of a four-level framework, above any interface | mapped downward to abstract, then concrete interaction units | [6] |
| User flow | "the typical or ideal set of steps needed to accomplish a common task" | "Micro: Specific and granular"; one product, minutes or hours | documented as "Wireflows, flow charts, or task diagrams" | [1] |
| Wireflow | a user flow drawn through wireframes, "a design-specification format" | one task; a step is a screen or a state of one | the screens are the steps | [7] |
| Flow shorthand, breadboard | a flow in words: what the user sees and does; places, affordances, connection lines | one goal, before any layout | names the places, not their look | [8], [9] |
| IFML | a model of "the content, user interaction and control behaviour of the front-end" | the whole front end | view containers "representing UI windows or Web pages" hold components and events | [10], [11] |
| State machine (statechart, SCXML) | behaviour as states, events and transitions | one component, up to the modes of an application | the standard: nothing; practice: top states as "modes" of the interface | [12], [13] |

The practitioner organisation read states the relation between the
top and the middle of the table in so many words: "User flows can be
thought of as a deep dive into specific areas of the high-level user
journey" ([1], under "Combining User Journeys and User Flows"). The
forms and levels of a use case are the known note's and are not
repeated here; [3] adds why a level is marked at all: it "alerts the
reader" to the writer's focus, between a goal "up in the clouds" and
one "down in the mud".

**F2. The authors of the goal-level methods keep the interface out
of the path.** [consensus among the method authors read;
practitioner claims from the original literature; essential use
cases only through a secondary]

The author of the standard book on use cases: "Use cases should not
be used to describe UI designs for several reasons, even though the
use case form permits it" ([3]). His reasons, as the fetch reports
them: a use case is a requirements document and the interface is a
design made after it by trained people; a UI design is "brittle,
changing often", so a use case that holds it is rewritten with it;
and under "Avoid the Standard Mistakes" UI specifics are one of the
two most costly mistakes. He words the steps in verbs neutral to
technology and points elsewhere for the interface: "Other forms of
description, statecharts, Constantine's task cases, and screen shots
do a better job" ([3]). The essential use case goes further by its
construction: it "is based on the purpose or intentions of a user"
and not on "the concrete steps or mechanisms", because system use
cases "typically contain too many built-in assumptions" about
technology and about "the user interface yet to be designed" ([4],
"Why business use cases?"; a secondary on Constantine and Lockwood,
whose own text could not be opened [18]). Scenario-based design says
the same of order: its approach "concentrates on developing a
coherent set of basic tasks first and only then developing an
effective user interface to these tasks", and its authors warn of
the gap between specification and implementation that "a focus on
detailed narratives of user interaction may widen it anew" ([5],
"Scenario-based development" and Introduction).

**F3. One published process defines a separate artefact between the
path and the screens and names the link: the Rational Unified
Process.** [single source; a process framework's own documentation,
read from two hosted copies of different editions, their footers
dated 2001 and 2006]

It has three artefacts. The use case, free of the interface. The
use-case storyboard, "a logical and conceptual description of how a
use case is provided by the user interface" ([14], opening), which
holds a "Flow of Events - Storyboard", "A high-level textual
description of the interaction between the user and the system during
the use case", diagrams of the boundary classes that take part,
usability requirements, optional references to the parts of the
user-interface prototype (windows) that correspond to those classes,
and a trace dependency to the use case that is storyboarded ([14],
Properties). And the navigation map: "There is one Navigation Map per
system", its purpose "to express the principal user interface paths
through the system", "the main pathways through the screens of the
system and not necessarily all of the possible paths" ([15],
Purpose). The division of labour in one sentence: "The Navigation Map
conveys the structure of the system's user interface, and the
Storyboards convey the dynamics" ([15]). As the fetch reports it, the
storyboard is the user-interface designer's, made once its use case
is given priority and before the interface is prototyped. The process
itself makes it optional: "Decide whether Use Case Storyboards are
useful for your project" ([14], Tailoring). The form of the map is
free: "A variety of representations may be used for the Navigation
Map" ([15]); the examples given are diagrams. The page does not say
"one storyboard for one use case" outright; it speaks of "the
corresponding use case" ([14]).

**F4. Product-design practice fuses the path and the screens: the
screens, or named places, are the steps of the flow.** [consensus in
the practice read; practitioner claims]

The wireflow is "a design-specification format" that "combines
wireframe-style page layout designs" with a flowchart of the
interactions ([7], "Wireflows as a Deliverable for Workflows"). Each
step is a screen and the arrow leaves from "the specific UI component
where the user takes action"; a step "need not be a separate page or
screen", since applications "have few overall pages, but change the
content and layout dynamically"; wireflows "work less well for
capturing flows through a large number of relatively static pages"
([7]). The same organisation: "Wireflows document the ideal or
typical pathway through screens or pages" ([1]).

Two forms of this family are text already. The flow shorthand:
"Above the bar is what the user sees. Below the bar is what they
do.", with an arrow from an action to the next screen, a dashed line
between alternative actions and several arrows where one action has
several results; as the fetch reports it, the author advises one flow
for one goal, not for one screen ([8]). The breadboard has three
elements: places, "things you can navigate to, like screens, dialogs,
or menus that pop up"; affordances, "things the user can act on, like
buttons and fields"; and connection lines, which "show how the
affordances take the user from place to place". A place is a name
underlined, and "Affordances go below the line to indicate they can
be found at that place". The reason for words: "We'll use words for
everything instead of pictures", because "If we start with wireframes
or specific visual layouts, we'll get stuck on unnecessary details"
([9], Breadboarding). Where the arrangement in two dimensions is
itself the problem, the same book leaves words for a rough sketch:
"Breadboarding would just miss the point because the 2D arrangement
of elements is the fundamental problem" ([9], Fat marker sketches).

**F5. The model-based standards keep the path and the screens as
separate models on separate levels and join them by mappings; IFML
models the flow inside the containers.** [single source each;
standards: a W3C Working Group Note, which is not a Recommendation,
and the standard body's site for IFML; the IFML specification itself
not read]

The W3C note gives four levels: the task and domain models, "the
hierarchies of tasks that need to be performed on/with domain
objects"; the abstract interface, in units "independent of any
implementation technology or modality"; the concrete interface,
"modality-dependent, but implementation technology independent"; and
the final interface, in source code ([6], introduction). The link
from task to interface is the grouping of abstract units, which "can
be grouped logically to map logically connected tasks or domain
objects"; one model is made from another by a transformation
(concretization is "an operation that transforms a particular model
into another one of a lower level of abstraction"; abstraction and
translation are the others), and, as the fetch reports it, the note
warns against changing a transformed model by hand. Of the tools the
note lists, "none of them, so far, implements the MBUID standard",
and by its own status "Publication as a Working Group Note does not
imply endorsement by the W3C Membership" ([6]).

IFML is "designed for expressing the content, user interaction and
control behaviour of the front-end of software applications" ([10]).
"an IFML diagram consists of one or more top-level view containers,
representing UI windows or Web pages"; the containers hold view
components, which stand for the publication of content or for data
entry, and "A view container and a view component can be associated
with events, to denote that they support the user's interaction"
([11]). Here the path and the screens are one model. The
specification's file came back undecoded; only its outline was
legible, which lists metamodel classes named Action, DataFlow,
DomainModel, InteractionFlow, NavigationFlow, ParameterBinding,
ViewComponent, ViewComponentPart and ViewContainer, a clause on
modularization and annexes that map IFML to three platforms ([16]);
their definitions were not read. The two pages read show a diagram
and name no textual syntax.

**F6. A state machine describes behaviour, not the path of one user,
and its standard says nothing of screens; practice ties its top
states to the modes of the interface.** [single source each; a
standard for the notation, a practitioner claim for its use on
interfaces]

SCXML, a W3C Recommendation of 1 September 2015, is "a
general-purpose event-based state machine language that combines
concepts from CCXML and Harel State Tables": states that are atomic
or compound, parallel states, transitions triggered by events and
guarded by conditions, history, a data model ([12], Overview and
sections 3 and 5). The part read, the first 100,000 of about 229,000
characters, through section 6.1, says nothing of user interfaces,
screens or views; its origin is call control and voice. For the
interface, a community reference site places the statechart between
the event and the action ("Statecharts inject themselves between the
event being generated and the action being performed") and says "the
states in the statechart to (at least at the highest level)
correspond to “modes” of the user interface" ([13]). It presents the
statechart mainly as code that runs; its sentence that this "makes it
easier when showing e.g. a statechart to non-developers, like QA or
designers" stands in a section the page marks as unfinished ([13]).
The author of [3] names statecharts first among the forms that
describe an interface better than a use case does. The agent's own
reading: the path of one user is one run through such a machine,
which is why the machine sits at the level of a component or of the
whole application and not at the level of a goal.

**F7. Journey maps and story maps stand above the screens, and their
sources tie them to no screen.** [single source each; practitioner
claims by a practitioner organisation and by the method's own author]

A user journey is "A scenario-based sequence of the steps that a user
takes in order to accomplish a high-level goal", across "many
touchpoints over a long time (days, weeks, or months)"; its map
captures "The user's actions, emotions, and thoughts, as well as
channels", where a flow captures "Product-based interactions (key
user actions and system responses)" ([1], definitions and comparison
table). A story map has a backbone of activities ("An activity is
sort of a big thing that people do") over user tasks ("A user task is
what users do to reach their goals") over stories; it runs left to
right in the order of use ("I’ll put the early thing on the left, and
the later thing on the right") and top to bottom by necessity ("Place
them high to indicate they’re absolutely necessary, lower to indicate
they’re less necessary"); it is made to understand the whole and to
plan releases ("Building a story map helps you initially understand
the functionality"). The article does not speak of screens or of the
design of the interface ([2]).

**F8. On order, every method author read puts the path before the
layout; one school puts the objects before both.** [contested;
practitioner claims on each side; no measured comparison found]

For the path first: words before wireframes ([9]), the tasks before
the interface ([5]), the storyboard before the prototype ([14]), one
flow for one goal ([8]). Against it: "That's OOUX: putting object
design before procedural action design", written against "the
traditional actions-first process that jumps straight into flows,
interactions, and features"; "We determine the actions after first
defining the objects" ([17], "Mobile first, content first, and
objects first"). The same article calls its method "a new ingredient
to add to your current process" and, as the fetch reports it, does
not say when flows are then drawn ([17]).

**F9. Three ways of keeping the link between a path and its screens
were found, and none is a standard for text.** [each a single source
or a single family of sources; the grouping is the agent's own]

1. A trace. The artefact on the interface's side points to the path
   it realises and, optionally, to the windows that show it: the
   use-case storyboard with its trace dependency and its references
   to the prototype ([14]).
2. Identity. The screens or places are the nodes of the flow, so
   there is no link to keep, and no path apart from the screens
   either: the wireflow, the shorthand, the breadboard, the IFML
   container ([7], [8], [9], [11]).
3. Derivation. One model is transformed into the next and the link
   is the mapping, with the warning against changing the derived
   model by hand ([6]).

A weaker fourth pattern is the reference in place of the copy: the
business use case shown in [4] carries identifiers and "refers to
business rules but does not embed the rule in the use case". It is
shown there for rules, not for screens. No source read says how such
links are kept current in text files under version control.

## Unexpected

The author of the textual flow notation treats it as disposable. In
[8] he writes that "all diagrams are destined for the garbage" and,
as the fetch reports it, that the real work is the screens and the
code; a commenter reports that the format gets "messy fast" on a
screen with many edit controls, and the author answers that such a
screen probably mixes several flows. A kept, versioned document of
flows goes against the grain of the practice that invented the
notation; that practice writes a flow to think, not to hand on.

A step is not a screen. [7] says a step of a flow "need not be a
separate page or screen", because applications change content and
layout within few pages. A link from a path to "its screens" would
then often need to name a state of a screen, not the screen alone.
This touches the cards on the behaviour of the whole application and
on the description of one screen.

The card assumes two things to relate, the path and the screens.
[17] says a third, the objects the user thinks in, is designed before
both, and that the flows follow from it. The question is answered
above as put; the lead belongs to the card on the structure above the
screens.

The standards' route did not arrive. The W3C text that defines the
levels from task to final interface is a Working Group Note which
says of the tools it lists that "none of them, so far, implements the
MBUID standard" ([6], 2014). Whether that changed after 2014 was not
looked for; it is the business of the card on formal languages.

Even the process that defines the linking artefact lets a project
drop it: "Decide whether Use Case Storyboards are useful for your
project" ([14]).

## Not found

- The own text of Constantine and Lockwood on essential use cases
  and on how they are tied to the interface (their content model and
  navigation map): the site refused the connection twice and the
  fetch cannot reach the web archive [18]. Essential use cases rest
  here on a secondary [4] and on one sentence of [3].
- The text of the IFML specification: the file came back undecoded
  [16]. The definitions of navigation flow, data flow, parameter
  binding and module were not read, and whether IFML has a textual
  form is not said on the two pages read.
- The handbook chapter on scenario-based design with its kinds of
  scenario: the file came back undecoded (Opened and not used). The
  kinds were seen only in a search result and are not cited.
- The 2023 article by the two originators of use cases, which a
  search result describes as saying that use cases can drive the
  design of the user experience: refused the fetch [19].
- The W3C note on task models and the operators of its notation: not
  opened, the budget being spent [20]. The primary literature of
  statecharts (the original paper, the book on constructing
  interfaces with them) was not opened either; the book did not
  appear online.
- A reliable source that journey maps are useless: the result list
  held vendors' and consultants' pages on why journey maps fail, none
  opened by the rule of kind, and one practitioner survey, not
  opened.
- The path as a part of each screen only: seen only in result lists,
  on tool vendors' pages about annotating wireframes, none opened.
- Any measurement of one arrangement against another (a path
  document of its own, the path in each screen, both), and any
  standard or convention for a path written in Markdown with links to
  screens: nothing in any result list.
- "State matrix" and "wireframe annotations", the search words of
  card 1: the results were vendors' pages on the states of one
  component, the business of another card; none opened.

## Options

1. **A path document of its own, free of the interface, which the
   screens cite.** The arrangement of [3], [4] and [14]: paths as
   items at the level of a user goal, worded as intention and
   responsibility, and each screen naming the paths it serves. It
   survives a change of the interface, which is the argument of [3].
   It needs a link that is kept, and the builder reads two documents
   to know what happens on a screen.
2. **The path inside the screens only.** Each screen says what can be
   done on it and where each thing leads; the flow is whatever the
   links add up to. There is nothing to keep in step. There is also
   no place for the goal, for what happens on failure or for the path
   as a whole, and a path over several screens is scattered and
   changes with every change of a screen. No source opened describes
   it.
3. **Both, in two layers with one direction of citing.** The goal
   level stays free of the interface; the description of the
   interface carries flows as items of their own, in words as places
   and what is done there ([8], [9]), each flow citing the path it
   realises and naming the screens it passes; a picture of the whole
   is generated. This is the three artefacts of F3 in text. It is the
   most complete and has the most to keep in step.
4. **A formal model as the source** (IFML, a task model, a
   statechart). Precise, checkable by a machine and, for a
   statechart, runnable. Heavy, tied to tools, not prose a human
   tunes in conversation, and by [6] without implementing tools in
   2014. It could serve one complicated component and not the whole
   description.

## Relevance to this project

The recommendation: option 3, lightly. The path at the level of a
goal stays where the chain already has it and stays free of the
interface. The description of the interface carries its flows as
items of their own, one for one goal, written in words as places,
what can be done at each and where it leads; each flow cites the
path it realises and names each screen it passes by that screen's
identifier, with the state of the screen where the step is a state
and not a page. The picture of the whole, a navigation map or a
wireflow, is generated from those items and not kept by hand. Journey
maps and story maps are no part of the description of the interface:
the first stands above the product, the second arranges stories.

What it rests on: interface detail inside a path description is
brittle and costly ([3]); the one documented arrangement with a kept
link has exactly these parts, a path, a storyboard traced to it and
one map of the whole ([14], [15]); a flow can be written in words
with no layout ([8], [9]); a step is a state of a screen as often as
a screen ([7]).

What it is chosen against: the path inside each screen only, which
has no home for the goal, the failures and the whole, and which no
source opened describes; the fused picture as the source of truth,
whose text forms their own author calls disposable ([8]); a formal
model as the source, for its weight and for what [6] says of its
tools.

The agent's own inferences, none stated by a source:

- That the links are citations of identifiers in the items and that
  a check finds the dangling ones. This carries over the known
  note's rule that links live in the items and a matrix is a view;
  no source read prescribes it for text.
- That the citing runs one way, the flow citing the path above it
  and the screens beside it, so that the more changeable thing cites
  the more stable. It is read out of the brittleness argument of [3]
  and the direction of the trace in [14].
- On the idea heard from practice, an element with its own
  definition and a page that names its elements: a breadboard is the
  same shape at a lower fidelity, a place with its affordances, and
  it has a third thing that the idea lacks, the connection, which
  says where an affordance leads. Definitions of elements alone do
  not carry the path.
- That one question stays open and the sources do not settle it for
  text: whether the target of an affordance is stated in the flow,
  in the screen or in the element. The two families of F2 to F4
  differ in exactly this, and stating it in two places invites
  drift.

Consult when: deciding where flows sit in the description of an
interface and whether they are items of their own; deciding whether
a use case may name a screen; choosing a notation in text for a
flow; deciding what links a flow, a screen and a use case and which
way the citing runs; asking whether a journey map or a story map
belongs in the interface layer; weighing IFML, a task model or a
statechart as the source form; arguing whether the path or the
objects come first.

## Sources

1. "User Journeys vs. User Flows", Kate Kaplan, Nielsen Norman
   Group; 16 April 2023 (byline);
   https://www.nngroup.com/articles/user-journeys-vs-user-flows/ ;
   primary (a practitioner organisation's own definitions);
   summarised fetch; original.
2. "The New User Story Backlog is a Map", Jeff Patton; 8 October
   2008 as the page shows, updated 12 April 2023 (byline; a
   bibliographic record in a search result, not opened, says August
   2008); https://www.jpattonassociates.com/the-new-backlog/ ;
   primary; summarised fetch; original, on the author's own site.
3. "Use Cases, Ten Years Later", Alistair Cockburn; "Published in
   STQE magazine, Mar/Apr 2002" as the page states (byline);
   https://www.dsc.ufcg.edu.br/~garcia/cursos/ger_processos/seminarios/Crystal/Use%20Cases,%20Ten%20Years%20Later.htm ;
   primary text; summarised fetch; a copy on a university course
   site: the author's own site did not appear in the results of a
   search made for it, and a listing of the magazine's publisher was
   not opened.
4. "Business Use Cases: An Agile Introduction", Scott W. Ambler,
   Agile Modeling; undated (footer copyright 2002-2026; the page
   says it is excerpted from chapter 5 of the author's book The
   Object Primer, third edition);
   https://agilemodeling.com/artifacts/essentialUseCase.htm ;
   secondary on essential use cases, primary on the author's own
   business use case; summarised fetch; original.
5. "Integrating Task and Software Development for Object-Oriented
   Applications", Mary Beth Rosson and John M. Carroll; CHI '95
   Proceedings, 1995 (the page's banner);
   https://chi1995.chistatic.hosting.acm.org/proceedings/papers/mbr1body.htm ;
   primary; summarised fetch; original, the conference's electronic
   proceedings.
6. "Introduction to Model-Based User Interfaces", W3C Working Group
   Note, editors Gerrit Meixner, Gaëlle Calvary and Joëlle Coutaz; 7
   January 2014 (byline); https://www.w3.org/TR/mbui-intro/ ;
   primary (a Note, not a Recommendation); summarised fetch;
   original.
7. "Wireflows: A UX Deliverable for Workflows and Apps", Page
   Laubheimer, Nielsen Norman Group; 4 December 2016 (byline);
   https://www.nngroup.com/articles/wireflows/ ; primary; summarised
   fetch; original.
8. "A shorthand for designing UI flows", signed "Ryan" (Ryan
   Singer), Signal v. Noise; 17 September 2009 (byline);
   https://signalvnoise.com/posts/1926-a-shorthand-for-designing-ui-flows ;
   primary; summarised fetch, the comments included; original.
9. Shape Up, chapter 4, "Find the Elements", Ryan Singer, Basecamp;
   undated on the page; https://basecamp.com/shapeup/1.3-chapter-04 ;
   primary; summarised fetch; original.
10. "IFML: The Interaction Flow Modeling Language", the site of the
    standard, Object Management Group; undated (footer copyright
    1997-2018; the page says IFML 1.0 "has been published in March
    2015"); https://www.ifml.org/ ; primary; summarised fetch;
    original.
11. "IFML primer", the same site; undated (the page says the
    specification was adopted in March 2013, which differs from the
    date on [10]; neither was checked against the specification);
    https://www.ifml.org/ifml-primer/ ; primary; summarised fetch;
    original.
12. "State Chart XML (SCXML): State Machine Notation for Control
    Abstraction", W3C Recommendation, editor-in-chief Jim Barnett; 1
    September 2015 (byline); https://www.w3.org/TR/scxml/ ; primary;
    partially, by summarised fetch: the first 100,000 of about
    229,000 characters, through section 6.1; original.
13. "Statecharts in User Interfaces", the Statecharts project; no
    author named, undated;
    https://statecharts.dev/use-case-statecharts-in-user-interfaces.html ;
    primary for a practitioner's claim (a community reference site,
    several sections marked unfinished); summarised fetch; original.
14. "Artifact: Use-Case Storyboard", Rational Unified Process;
    undated (footer "Copyright © 1987 - 2001 Rational Software
    Corporation");
    https://cin.ufpe.br/~if682/RUP/process/artifact/ar_ucstb.htm ;
    primary text; summarised fetch; a copy on a university server,
    no copy of the publisher's own having appeared in the results.
15. "Artifact: Navigation Map", Rational Unified Process; undated
    (footer "Copyright IBM Corp. 1987, 2006");
    https://swi.cs.vsb.cz/RUPLarge/core.base_rup/workproducts/rup_navmap_73AF74E2.html ;
    primary text; summarised fetch; a copy on a university server,
    of a later edition than [14].
16. The IFML 1.0 specification, Object Management Group; title page,
    date and document number not read;
    https://www.omg.org/spec/IFML/1.0/PDF ; primary; opened, the file
    returned undecoded: only the outline of its clauses was legible
    and only that is cited; original.
17. "Object-Oriented UX", Sophia V. Prater, A List Apart; 20 October
    2015 (byline); https://alistapart.com/article/object-oriented-ux/ ;
    primary; summarised fetch; original.
18. "Structure and Style in Use Cases for User Interface Design",
    Larry Constantine and Lucy Lockwood; date not read;
    https://www.foruse.com/articles/structurestyle2.pdf ; primary;
    not opened: the connection was refused on two attempts and the
    fetch cannot reach the web archive; never cited for content.
19. "Use Cases are Essential", Ivar Jacobson and Alistair Cockburn,
    ACM Queue, as the search result lists it; date not read;
    https://queue.acm.org/detail.cfm?id=3631182 ; primary; not
    opened: HTTP 403; never cited for content.
20. The W3C Working Group Note on task models; date not read;
    https://www.w3.org/TR/task-models/ ; primary; not opened: the
    opening budget was spent; never cited for content.

The known note of the project,
`2026-10-13-what-a-brd-contains-and-how-it-is-found-today.md`, was
read in full from the packet's folder.

## Opened and not used

- A file said by a search result to be the handbook chapter
  "Scenario-Based Design" by Rosson and Carroll,
  https://cfacaa.human.cornell.edu/dea.arl/linked%20docs/Scenario-Based%20Design%20John%20Carrol.pdf :
  returned undecoded; its metadata name neither the title nor the
  authors, so not even its identity was confirmed.

## Search record

Queries, in order:

1. user flows vs user journeys vs use cases vs scenarios difference
2. essential use cases Constantine Lockwood, the title of their
   paper on structure and style
3. IFML interaction flow modeling language specification view
   container view component OMG
4. W3C task models MBUI ConcurTaskTrees abstract user interface
   concrete user interface
5. Jeff Patton "the new user story backlog is a map"
6. wireflows UX deliverable workflows apps
7. Shape Up breadboarding places affordances connection lines
8. "user flows or screens first" (the disconfirming query, first
   half)
9. "journey maps are useless" (the disconfirming query, second half)
10. "A shorthand for designing UI flows" Ryan Singer Signal v. Noise
11. Rosson Carroll scenario-based design, the kinds of scenario
12. statecharts user interface screens flow Horrocks SCXML
13. Cockburn "Writing Effective Use Cases" user interface out of the
    use case, hub, link to UI design
14. Jacobson Cockburn "Use Cases Are Essential"
15. essential use case "user intention" "system responsibility"
    abstract use case vs system use case
16. navigation map screen flow specification use case storyboard,
    which screens realize a use case, traceability
17. task flow vs user flow vs wireflow text description, happy path,
    alternate paths
18. object-oriented UX objects before actions, flows, objects first
    (a second wording of the disconfirming query)
19. statechart screens states transitions application navigation
    flow text format, user flow documentation
20. Cockburn "Use cases, ten years later" on the author's own site
21. UX "state matrix" OR "wireframe annotations" user flow screens
    design specs
22. RUP "use-case storyboard" boundary classes user interface use
    case realization

Pages opened, an opening being a fetch, in order: [1]; [7]; [9]; [8];
[18] (connection refused); [2]; [16] (returned undecoded, outline
only); [6]; the web archive's copy of [18] (the fetch cannot reach
that host); [10]; [12]; [11]; [18] again under the bare host
(connection refused); [19] (HTTP 403); the handbook chapter
(returned undecoded); [3]; [15]; [4]; [5]; [17]; [13]; [14].
Twenty-two fetches: sixteen pages read, two returned undecoded, four
attempts that reached no page.

The disconfirming query. Its first half, "user flows or screens
first", returned a list of vendors' and tool makers' pages advising
flows before screens, the expected advice; none was opened, by the
rule of kind, and the advice is carried here by primaries opened for
other reasons ([5], [8], [9], [14]). A second wording, objects
first, found [17], opened: a counter-position, the objects before
the flows (F8). Its second half, "journey maps are useless", returned
vendors' and consultants' pages on why journey maps fail and one
practitioner survey; none was opened and nothing is cited from them:
no reliable source that journey maps are useless.

Why the run ended: the opening budget. Sixteen pages were read, one
more than the card's fifteen, the two undecoded files and the four
failed attempts having brought nothing. The stop rule was not met:
the later, differently worded queries (16, 18, 22) each still turned
up something new, and three routes have no primary that could be
read: essential use cases, the IFML specification, the handbook
chapter on scenario-based design.
