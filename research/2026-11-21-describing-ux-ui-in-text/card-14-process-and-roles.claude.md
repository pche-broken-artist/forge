---
date: 2026-11-21
project: forge
topic: the place of interface work between requirements and build, the order of its outputs, and what lean and solo practice keep
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-14-process-and-roles
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 14; research/2026-09-28-artefact-layers-from-idea-to-handover.md; research/2026-10-13-what-a-brd-contains-and-how-it-is-found-today.md; web sources below
---

# Interface work stands before the build as a stage of its own or as work a step ahead of it; lean practice keeps its rough outputs and drops the specification

<!-- Shape: templates/research.md -->

## In short

Established method places the work on the interface before the build
in two ways that contradict each other. The layered and the
human-centred models make it a stage of its own below the
requirements, its outputs ordered from structure to surface and,
where a specification is written, ending in it. Product practice
since 2011 makes it work that runs a step ahead of the build, in one
team. On user stories the sources split three ways: the stories
first and the interface drafted from them and checked against them,
the design first and the items to be built coming out of it, or
story and screen written together. Lean practice drops the
specification and the high-fidelity picture made as a contract, and
keeps the rough statement of what stands on a screen, the path
between screens, the prototype and the shared pattern library; it
pays for the cut with a team in constant conversation and brings the
document back where that is missing. A lone designer is told to keep
the methods and cut the finish. Confidence is moderate: the lean,
the dual-track and the hand-over routes rest on their authors' own
pages; the layered model and the human-centred design standard still
rest on secondary and tertiary pages, their primaries unreadable or
refused in both rounds of this run; one person who is author and
builder at once has no source. The disconfirming query, run in full
in the second round, found the expected strong current against
handing documents over, dated 2011 to 2023 in the pages opened; its
target is the hand-over between separate roles, not a description as
such, and each of its sources names a case where a document stays.
The unexpected thing: one practice writes a screen and its stories
as one unit, a page each, and a study of 2024 measures a model
checking a prototype against the stories.

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

**Card 14: The place in the process and the roles**

- **Question:** Where does the work on the interface stand between the requirements and the build in established processes: what does it take from requirements and user stories, what does it hand to the builders, in which order do its own outputs come (flows, structure, wireframes, visual design, prototype, specification), and how does the same output serve one person working end to end and a specialist in a team: which outputs do lean and solo practices drop, and which do they keep?
- **Why it matters:** it decides where the description stands among the framework's documents and how light the first shape can be.
- **What would answer it:** method literature and practitioner organisations.
- **Where to look:** the layered models of user experience work; lean UX; dual-track practice; the human-centred design standard through secondary pages; guides to design handoff. The known notes on the ladder of documents and on business requirements. Search words from card 1: "handoff" names the passage and a tool's features for it, not the document; for the document "design specs", "annotations", "ready for dev"; vendors' pages on their own market are to be expected and are left out by the brief.
- **Disconfirming query:** "UX deliverables are waste", "design handoff is dead"; expected: a strong current against handing over documents at all.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

What the note must beat. The note of 2026-09-28 on the ladder of
documents found that nearly every discipline has about three steps
between an idea and a hand-over, that the handed-over step has the
strictest rules, that one method holds wireframes too concrete and
words alone too abstract for work handed to a team, that one
spec-driven kit lists a document on user experience between its
requirements document and its architecture, and that whether a
handed-over document must stand without its author is contested. The
note of 2026-10-13 on business requirements found that screens lie
below the line of a business requirements document and that
usability is one of its quality categories. Neither says where the
methods of interface work themselves place that work, in what order
its outputs come, what reaches the builders, or what lean and solo
practice drop.

## Key findings

"Design" below means the design of the interface, its structure,
behaviour and look, unless said otherwise; "visual design" is its
surface alone. Every page was read through a fetch tool that returns
a small model's reading of the page, so every finding rests on a
summarised fetch; quotations were asked for verbatim, and those of
[5], [9], [10], [12], [13], [16], [18], [19], [20] and [21] were
read a second time and agree. The run had two rounds (Search
record); sources [15] to [21] are the second round's, and where a
finding changed with them it says so.

**F1. Established method places the interface work before the build
in two ways that contradict each other: as a stage of its own below
the requirements, or as work that runs beside the build, a step
ahead of it.** [contested; method literature and practitioner
claims, no measurement]

The stage. The layered model of Garrett's *The Elements of User
Experience* (2002), read here through two secondary pages, orders
five planes, Strategy, Scope, Structure, Skeleton and Surface, each
the ground of the next: "The more specific your answers for each
plane, the more likely you will provide a solid foundation for the
next" [1]. Scope asks "what kinds of content and functionality does
this experience need?" [1, Step 2], and the book's chapter on it is
named "The Scope Plane: Functional Specifications and Content
Requirements" [15, Chapters]: the scope is the requirements, and the
three planes above it are the interface work. The W3C's notes on the
user-centred design process, written on ISO 13407, give the steps as
"Analysis", "Design", "Evaluation (iterate back to Design)",
"Implementation" and "Deployment" [2, UCD Process Steps]: the
interface is designed in a step of its own before implementation and
entered again from evaluation. A page of a national standards
institute, which defines the approach by ISO 9241-210:2010, says
"There are four HCD activities that should take place during the
design of any interactive system.": "Understanding and specifying
the context of use.", "Specifying the user requirements.",
"Producing design solutions." and "Evaluating the design." [16,
Activities]. An encyclopaedia page gives the same four as phases and
holds them compatible with any life cycle: "Practical models include
the waterfall model, agile model or any other software engineering
practice." [3, User-centered design process]. The 2019 edition of
the standard was reached only as far as its scope, "to plan,
research, conceptualize, specify, design, develop, deploy and
maintain interactive systems throughout their life cycle" [4]. The
plainest form of the stage is an encyclopaedia page on the user
interface specification, with three steps, "Use case definition",
"Design draft creation" and "Writing the user interface
specification" [17, The process]; how thin its sources are is said
in F4.

The track. Cagan, 2012: "The Discovery track is all about quickly
generating validated product backlog items, and the Delivery track
is all about generating releasable software." [5, body]. He names
the stage, found inside Scrum, "little mini-waterfalls": "The
product manager does some kind of 'requirements' work, and that is
passed to a designer that does his designs and generates his
artifacts (usually annotated wireframes), and then that is handed
off to the delivery team to build and test." [5, body]. Patton,
2017: "Discovery work happens concurrently and continuously with
development work.", and "Myth: Discovery is a process that precedes
agile development. It shouldn't." [6, It's happening all at once;
Busting dual-track myths]. Interviews of 2014 by the Nielsen Norman
Group with eight people who had worked in Agile settings give the
same in an interviewee's words: "The UX designer must be at least
one step ahead of the sprint." [7, Tips for Running Smooth UX Agile
Teams]. Research on requirements takes the track as given: "Agile
requirements engineering attempts to address the changes that agile
methods bring with them, such as requirements engineering and design
activities being carried out continuously throughout development
projects." [18, Introduction].

Both placements have the interface of a thing worked out before the
code of that thing is written. They disagree on whether it is
finished before the build begins and on whether a separate role
holds it: [5] contradicts the stage outright, [3] denies that there
is a contradiction.

**F2. From above, the interface work takes the users, their tasks
and the content and functions in scope. On user stories the sources
split three ways: the stories or use cases come first and the
interface is drafted from them and checked against them; the design
work comes first and the items to be built come out of it; or the
two are written together, a story to a screen.** [contested; the
first way research literature and one tertiary page, the second
practitioner claims of one school, the third one practitioner's
guide. Changed in the second round: the first round had found no
source in which the interface work takes anything from user stories]

The input. In [2] the step before Design, Analysis, yields the lists
the design is made from: user categories, profiles and personas, a
task list and a user-task matrix, a content list, a hierarchy, a
workflow and scenarios [2, UCD Process Steps, as the fetch listed
them]. In [1] Structure arranges what Scope has listed [1, Step 3],
and under Scope stands Strategy, "Site Objectives and User Needs"
[15, Chapters].

Stories first. A paper of 2024 on prototyping describes the usual
course: "Requirements elicitation typically starts with an
elicitation interview with stakeholders and initial NL requirements
are often gathered in the form of user stories and cleansed
afterwards.", and "Subsequently, initial low-fidelity GUI prototypes
are created often using GUI prototyping tools, e.g. Figma" [18,
section III]; its own method then goes on "validating the current
GUI prototype state against the user story collection to show
missing user stories" [18, section III]. The page on the
specification has the same direction with use cases: "Use cases are
then used as basis for drafting the UI concept" [17, The process].

Design first. In [5] the designer is one of three who make the items
the build takes: "the product manager, designer and lead engineer
are working together, side-by-side, to create and validate backlog
items" [5, body]; the page does not use the words "user story". [6]
adds a third kind of work beside discovery and development: "If
you've validated the product is worth building, you'll likely need
to finish some detailed design work", done by designers ahead of the
code [6, OK, it's really 3 kinds of work…]. [7] does not mention
user stories.

Together. A guide of 2017 for a person with an idea for a mobile
application: "Start by sketching out wireframes for the
application." and "Once the wireframes are done, add two or more
user stories for each screen, describing what the user can do on
that screen." [19, Mixing Formats]. Its worked example turns the
order round, the stories written "screen by screen" and the picture
after them, "To avoid any ambiguity, we'll create a wireframe for
this screen." [19, Let's Practice]; the guide does not notice the
difference. The end is the same either way: "put the wireframes and
user stories together in one document, with each wireframe and its
respective story on its own page" [19, Let's Practice].

**F3. What reaches the builders is given in five forms, from the
most document to the least: a written specification, an annotated
design file, a set of deliverables, the prototype as the
specification, and no hand-over at all.** [contested; one survey,
practitioner claims and one tertiary page. The first form was added
in the second round]

- The written specification. It "is a document that captures the
  details of the software user interface into a written document"
  [17, lead]. Its example structure: change history, open issues,
  logical flow, display descriptions, error and exception cases [17,
  Structure, as the fetch listed them]; "The display description
  contains the screen contents and information about available
  functions", and "access points should be listed and the fields and
  controls on the screen should be described" [17, Display
  descriptions]. A lighter document of the kind closes the guide of
  [19]: "We have created two documents: a PDF with user stories and
  wireframes, and a screen map that complements the PDF." [19,
  Conclusion].
- The annotated file. A practitioner's guide of 2023 wants the file
  of the design tool to carry numbered flows ("The numbering and
  title pattern makes it easy for developers to understand which
  screen belongs to which flow immediately."), the detail of
  interaction ("include details like the hover state, initial state,
  max width/height"), links that show how the screens connect, the
  decisions behind the design, and a record of change ("Include a
  changelog in the handoff file to help developers understand the
  latest changes made to the design.") [8, sections 2, 3 and 5]; it
  holds the tool's automatic inspection of a design not to be
  enough.
- The set. A survey of 86 UX professionals by the Nielsen Norman
  Group, 2015, on what works for developers: "Top five are
  interactive prototype, flowchart, site map, style guide, and
  static wireframe." [9, 3. Developers and Engineers, the chart's
  alternative text], used "both for collaboration and for delivering
  specifications for implementation" [9, the same section].
- The prototype. "Rather than focus on artifacts, we focus on
  prototypes and validating those prototypes in Discovery, with the
  added benefit that the prototype serves as the spec for Delivery."
  [5, body]; "The prototype has now become your documentation." [10,
  Prototyping: The Fastest Way Between You and Your Customers];
  "With the process, the working prototype is the living spec of the
  project and a shared language for the team." [20, The "No Handoff"
  Method].
- Nothing handed over. "No Handoff is a working pattern that brings
  product and engineering into one team, eliminating handoff and
  reducing risk." [11, opening, undated]; "Once the designs are in
  the browser, they should stay in the browser." [12, In-browser
  iteration]; "From my personal experience, I can only testify that
  the best collaboration doesn't have any handoffs between teams."
  [20, The "Hot Potato" Process].

This note's own reading of the five: in each the builders get the
behaviour, how one moves between screens, what the states are and
what happens on an error, and not the still picture alone.

**F4. The outputs come in the order from structure to surface; the
prototype is a medium at every step, not a step; and the
specification, where there is one, comes last, as an extension of
the draft before it.** [the order consensus among the stage sources,
secondary; strict sequence contested by [12]; on the specification
one tertiary page of thin sourcing against the practitioners who
reject it. Changed in the second round: the first round had found
the specification described only by those who reject it]

In [1] Structure comes first, then Skeleton, which holds "interface
design, information design, and navigation design", then Surface,
"visual identity, style, color, logo, etc." [1, Steps 3 to 5]; the
book's chapters put it the same way, "The Structure Plane:
Interaction Design and Information Architecture", "The Skeleton
Plane: Interface Design, Navigation Design, and Information Design",
"The Surface Plane: Visual Design" [15, Chapters]. [2] lists under
Design, in this order: conceptual model and design concepts,
navigation design, storyboards and wireframes, detailed design,
paper prototypes, online mockups, functional online prototypes [2,
as the fetch listed them]; the hierarchy and the workflow it has
already under Analysis. In the card's words: flows and structure
first, wireframes next, visual design after them. The prototype
stands in [2] at more than one fidelity, and [10] says "The fidelity
of the prototype ultimately doesn't matter, so create it the way you
know best." [10, Prototyping].

The specification. No specification stands in the list of [2]. The
one page that describes it as an output puts it last of three steps
and builds it on the step before: "The UI specification can be seen
as an extension of the design draft that provides a complete
description" [17, The process], its screens shown by what was
already made: "The screen contents may be wireframes, screen-shots
of a prototype, or UI mock-ups." [17, Display descriptions]. That
page cites three web sources and no method literature, a commercial
site and two archived pages of a phone maker's developer
documentation (the fetch's count), and marks its own claim of
purpose as needing a citation. Elsewhere the specification appears
as the last step of a process being rejected: "Write The Spec,
detailing every pixel and interaction", then "Hand off to
development for review, approval and start of implementation" [10,
opening]. [12] rejects the sequence itself, "The waterfall process
hinges on the premise that work must flow in a sequential order: the
UX designer's work must be completed before visual design can start;
the visual designer must finish their job before front-end
development can begin." [12, Death to the waterfall], in favour of
work that "can happen concurrently but shouldn't happen in
isolation" [12, Stop, collaborate, and listen]; its own order still
runs from rough to fine, starting "with lo-fi sketches that
establish what appears on a particular screen and in what general
order" [12, Establishing content and display patterns].

**F5. Lean practice drops the specification and the high-fidelity
picture made as a contract; it keeps the rough statement of what
stands on a screen, the path between screens, the prototype and the
shared pattern library.** [consensus among the lean sources read,
practitioner claims of 2011 to 2023; how far the cut should go is
contested by [14] and qualified by the survey [9]. Unchanged by the
second round]

Dropped. The long document: "Traditional documents are discarded or,
at the very least, stripped down to their bare components, providing
the minimum amount of information necessary to get started on
implementation." [10, Lean UX]. Its finish: "Eliminate waste by not
spending hours getting the pixels exactly right and the annotations
perfect." [10, Isn't This Just Design-By-Committee?]. The document
kept for maintenance: "The old kind of documentation is waste and
draws effort away from solving current design problems." [10,
Deliverables For Maintenance Don't Make Sense Anymore], the product
itself answering later questions. The picture made too early: "If we
start with wireframes or specific visual layouts, we'll get stuck on
unnecessary details and we won't be able to explore as broadly as we
need to." [13, Move at the right speed]. The picture as a contract:
"Static design comps cannot deal with all these considerations, so
they should be treated merely as hypotheses rather than set-in-stone
specifications." [12, In-browser iteration].

Kept. Words for what there is and how it connects: "We'll use words
for everything instead of pictures." [13, Breadboarding], in three
kinds of thing: "Places: These are things you can navigate to, like
screens, dialogs, or menus that pop up.", "Affordances: These are
things the user can act on, like buttons and fields." and
"Connection lines: These show how the affordances take the user from
place to place." [13, Breadboarding]. The rough sketch, made on "a
whiteboard, a napkin or a quick wireframe" [10, Lean UX]; an
interviewee of [7]: "My boss is encouraging us to not use wireframes
— go with sketches." [7, Agile Challenges Within Organizations]. The
prototype (F3). The pattern library, which the team of [12] leaves
behind as a style guide (by the fetch's summary of [12]) and which
stands among the five things that work for developers in [9].

Limits. The survey: "This is a clear indication that Agile isn't
deliverable-free", 83 % of its respondents working in an Agile or
hybrid setting and producing deliverables all the same [9, Most
Frequently Produced Deliverables; figures of 2015]. A reply to [10]
four years later: "we've taken this sound advice to an extreme
that's actually hurtful to the creation of good products", though
"The lean movement is right about the main reason for getting out of
the deliverables business"; what it keeps are the maps above the
screens, journey maps and content diagrams, because they "could
provide a better baseline to start designing wireframes and
prototypes from" and "could help with building up organizational
memory"; "Remember, deliverables aren't bad. Bad deliverables are
bad." [14, opening; And The Point Is?]. And [10] itself keeps
documents in two cases: a site of heavy content "will need some
up-front planning and documentation" [10, How Does Content Strategy
and Planning Fit In?], and of maintenance documentation it says
"While this may make sense for complex business rules, it doesn't
make sense for design." [10, Deliverables For Maintenance Don't Make
Sense Anymore].

**F6. The lean cut is paid for with a team in constant conversation,
and the same sources bring the document back where the conversation
is missing. A lone designer is told to keep the methods and cut the
finish; a person with an idea and no builder's skill is told to
write stories, wireframes and a screen map; one person who is author
and builder at once is the subject of no source read.** [single
sources and one panel of eight practitioners, practitioner claims.
Changed in the second round: the first round had only three passing
statements on the solo author]

The condition. [10] is written for a team that sits together: "one
of the immediate casualties of Lean UX is the stereotypical solitary
designer, working silently in a corner for a period of time" [10,
Lean UX]. Where its author comes to one person serving several
clients, the document returns: "Consultants are, in essence, an
agency of one. In this case, falling back on a slightly deeper level
of documentation makes sense to keep concurrent projects moving
forward." [10, I'm a Consultant/Freelancer. Does This Make Sense for
Me?]. The advocate of no hand-over at all says of his own advice:
"Of course, the process works well for small product teams. But what
if a part of the product is outsourced to an external agency?" [20,
Create As Many Overlaps As Possible]. [13] lets its rough outputs be
made by one, "Either we're working alone or with a trusted partner
who can keep pace with us." [13, Move at the right speed], and says
what they are not: "This isn't a spec. It's more like the boundaries
and rules of a game." [13, Room for designers]; the rest is left to
people who design during the build: "By leaving details out, the
breadboard and fat marker methods give room to designers in
subsequent phases of the project." [13, Room for designers].

The lone designer. A column of 2017 put the question to eight
practitioners: "As the lone UX designer working on a project, should
I still use the same methods I would if I were part of a UX team?"
[21]. The methods stay: "You absolutely, 100%, no question, should
use the same methods you would if you were on a UX team," (Julien);
"Doing each step is maybe more important when working alone because
it forces me to analyze the design decisions I'm making, instead of
letting me fall in love with my first solution." (Hoober). The
finish goes: "However, there are some things—namely, formal,
nice-looking deliverables or outputs—that you can skip." and "You
want to document your decisions along the way, but you don't need to
worry about formatting." (Baldino); "Creating formal documentation
such as personas often goes by the wayside.", and reports are
"usually redundant because the team already shares a common
perspective and is aligned on UCD goals" (Gabriel-Petit). And the
lone designer goes straight to the builder: "collaborate closely
with a front-end developer to do prototyping in code" (Gabriel-Petit)
[21]. This designer is alone in the craft, not alone on the project.

The author who is no specialist. [19] is written for the reader of
whom it says "you want to produce a mobile app, but you don't have
the programming skills" [19, opening]; what that reader writes is
the paired document of F2, and "We can go ahead and send that to our
developer." [19, Conclusion]. The fuller form the guide puts beyond
that reader: "The person who composes the FSD should have strong
experience in software development and should know the specifics of
the mobile or other platform for which you are building." [19,
Functional Specification Document].

One output in two uses. [9]: "static wireframes were the most
frequently produced deliverable overall" yet "were not chosen in the
top 4 most effective deliverables for any audience", being
"artifacts that UX professionals produce for their own benefit" [9,
Lessons Learned]; and "Even if you're a solitary UX person who
produces a document for your own delectation, it's a deliverable."
[9]. The principles of the human-centred approach presume more than
one person, "The design team includes multi-disciplinary skills and
perspectives." [16, the list of principles; the same in 3, Models
and approaches]; which standard the list belongs to the two pages do
not agree on (Not found).

This note's own reading: an output is either a tool of thought for
its maker (the wireframe, the breadboard) or a message to others
(the prototype, the flow, the style guide), and the sources that cut
documents cut the second kind on the condition that the others are
in the room.

**F7. The disconfirming query found the expected current against
handing documents over, strong and dated 2011 to 2023 in the pages
opened, and found beside it that the current aims at the hand-over
between roles and that each of its sources keeps a document
somewhere.** [that the current exists: consensus; how far it
reaches: contested. Run in part at the end of the first round and in
full in the second; the finding held]

The current. 2011: "The old kind of documentation is waste" [10].
2012: "the work flow is not characterized by each role delivering
artifacts on to the next step" [5, body]. 2016: "They slip the
approved design under the door" [12, Death to the waterfall]. 2023:
"Design handoffs are inefficient and painful." [20, opening].
Undated and online today: the handoff as "that universally hated
period of inefficiency, disruption, and blame", with a call to "stop
guessing a spec into existence so you can do your job" [11,
opening]. The two halves of the query returned further titles of the
same current, among them "UX deliverables are dead — long live
collaboration", "Only one deliverable matters", "The death of the
deliverable", "Handoff is dead", "The design handoff is dying" and
"Stop trying to fix the handoff process"; none was opened and
nothing is cited from them [26].

Its target and its limits. What these sources attack is the passing
of finished artefacts from one role to the next, and the document as
a stand-in for conversation; their remedy is one team and a
prototype, "Harnessing the power of prototyping as a shared language
between all stakeholders." [11, opening]. Against them stand the
reply of 2015 [14], the survey of 2015 [9] and the guide of 2023,
which asks for more written detail in what the developers get, not
less, and holds the hand-over to be no single moment: "In an ideal
world, the design would be completely finalized before developers
start coding. But in reality, design is always subject to
adjustments, even after development has already begun." [8]. Each
source of the current keeps a document somewhere or names where its
remedy ends: [10] for heavy content, business rules and the
consultant with several clients; [12] the pattern library; [13] the
written pitch that follows its rough outputs ("After that we'll see
how to wrap up the shaped concept into a write-up for pitching."
[13, Not deliverable yet]); [20] the small team as the place where
it works, the outsourced part as the open case, and a team that
cannot work together as a case no document mends: "And if they can't
collaborate particularly well, chances are high that a design
hand-off won't make it any better, and a major change in the team
culture will need to happen first." [20, Wrapping Up].

What it does to the answer: it does not move the interface work from
its place before the build; it denies that the place is a hand-over
of finished documents between separate roles. No page opened
considers a builder who cannot be spoken to. The titles returned in
the second round show a newer strand that argues the hand-over away
because an AI agent builds from the design directly; all of it
stands on sellers' pages and unsigned posts, none was opened, and
nothing is concluded from it [27].

## Unexpected

**In one practice the screen and its stories are one unit.** The
card asks what the interface work takes from user stories, and F2
answers it with three orders. The third is not an order at all: [19]
ends with one page per screen, the wireframe and the stories of that
screen together, and a map of the screens beside them. For a chain
in which user stories are a document of their own this is a lead on
how the two could be tied: by the screen. From one guide, whose own
example contradicts its stated order.

**A model checking an interface against the stories has been
measured.** [18] has a language model find the user stories that a
prototype does not serve, "ACC scores of .852 (ZS), .848 (FS5) and
.829 (CoTt=1)" [18, section V-A], and reports that matching a story
to the components that serve it is harder (a score of .681 by the
first reading of its section V-B). The data are mobile: "Rico GUIs
present a sample of free mobile applications from the Google Play
store." [18, section VI]. A preprint of 2024, its venue not stated
on the page. A lead for the cards on measured studies, on how a
proposal is judged and on what a description cites.

**Two kinds of design work are argued about under one word.** [6]
separates discovery, which asks whether a thing is worth building
and in which "we substantially change and kill lots of ideas" [6,
tl;dr], from the "detailed design work" that is finished once that
is known. The current against documents (F7) is argued mostly about
the first; the description the frame wants is the second. A lead,
from one page.

**The author of the dual-track term withdrew it.** "I stopped using
the term 'Dual-track Agile' because the phrase made people focus far
too much on process, and not enough on the principles." [5, update
note at the top, undated]. A place in a process read off these
sources is read against their author's warning.

**An established practice already describes an interface in words
alone, and says of it that it is not a specification.** The
breadboard of [13] names places, the affordances on each and the
connections between them, without layout. It is near the idea the
frame wants tested, a page definition naming its elements, but it
has no definition per element and leaves detail out on purpose. The
display description of [17] is its opposite at the other end: the
fields and controls of each screen described in full. A lead for the
cards on one screen and on pages composed of blocks.

**What works on every audience is seen, not read.** In [9] the
interactive prototype is the one deliverable among the top five for
managers, clients and developers alike (by the fetch's summary of
its Lessons Learned), and the most produced document, the static
wireframe, is in nobody's top four. A lead for the card on previews:
a description in text would be judged through a preview of it.

## Not found

- **Garrett's own diagram and book.** In the first round the
  author's site answered with a certificate error, the publisher's
  excerpt of the chapter on the planes led to a list of other
  articles, and two pages refused (403). In the second a search
  found a copy of the diagram at a university's site; it came back
  as PDF bytes the fetch tool could not read. The planes are cited
  from one secondary page [1] and the elements on each plane from a
  review's list of the chapter titles [15]. Whether the book wants
  work on one plane ended before the next begins, or only before the
  next ends, was looked for and not found. [22]
- **ISO 9241-210 through a page that gives its activities and
  principles as its own.** The standards body's page refused (403);
  a table of contents at a national standards body and a sample of
  the standard came back as PDF bytes the tool could not read; a
  paper on the standard stands behind a login. What was read: the
  predecessor through the W3C's notes [2]; a page of a national
  standards institute that defines the approach by the 2010 edition
  and lists four activities without saying whose they are [16]; two
  encyclopaedia pages [3], [4]. The six principles are given to
  ISO 9241-110 by [16] and to a government usability site by [3]. A
  search engine's summary of the standard's table of contents places
  both lists in ISO 9241-210 itself and names a sub-clause on
  communicating the design solution to those responsible for
  implementation; a summary is not a reading, and the point stays
  unverified. [23]
- **Sy's paper of 2007 at source**, by [6] the origin of the two
  tracks. The journal's address tried in the first round was not
  found (404); the address a search gave in the second opens a
  listing of a current issue, without the article. Copies on
  document-sharing sites were not opened. Known through [6] only.
  [24]
- **One person who is author and builder at once.** [21] is a lone
  designer among developers, [19] a person with an idea who briefs a
  developer. The publisher's page of the best-known book on a user
  experience team of one refused (403) [25].
- **Method literature that describes the specification as an output
  with contents of its own.** Found only on an encyclopaedia page
  that rests on a phone maker's documentation [17]. The
  form-and-behaviour specification of goal-directed design is from
  memory and was not opened.
- **Any measurement of outcomes with and without handed-over
  documents.** [9] measures what 86 respondents find effective
  (2015); [7] reports eight interviews (2014); [18] measures a
  model, not a process.
- **A reliable page from 2024 to 2026 on the place of interface work
  where an AI coding agent builds.** The second round's query on it
  returned the pages of design-tool and builder-tool sellers,
  unsigned posts on community platforms, a consultancy's blog and a
  design-tool forum; none was opened, by kind [27]. The one page of
  2024 opened is a research preprint on another question [18]. The
  matter is left to the cards on descriptions written for an agent
  and on the agent that proposes.
- **Guides to design handoff beyond the two opened** ([8], [20]).
  The query with the words of card 1 ("design specs", "annotations",
  "ready for dev") returned sellers of design and whiteboard tools
  almost alone, as card 1 foretold; the one page of a company's own
  design system among the results refused (403) [27]. No list of
  what "ready for dev" requires was found outside a seller's page.
- **Differences of the process by platform.** [19] is written for
  mobile applications and [18] measured on mobile screens; no source
  read says the place or the order of the interface work differs for
  native mobile or for the desktop.
- **A limit of method.** Every page was read through a fetch tool
  that returns a small model's reading; a quotation is as the tool
  returned it on a request for verbatim wording, typographic
  apostrophes given as straight ones and inner quotation marks as
  single ones. Ten pages were read twice and the readings agree
  ([5], [9], [10], [12], [13], [16], [18], [19], [20], [21]); every
  other quotation rests on one reading. Longer quotations came back
  in consecutive fragments and are joined here. Where the fetch gave
  no place in the page for a quotation, none is given.

## Options

**A. A layer of its own below the business requirements and above
the user stories, complete before the build of what it describes.**
*For:* the stage models place it there (F1) and name what it takes
(F2); it is the written specification of F3 and F4; the one
spec-driven kit of the note of 2026-09-28 that has such a document
places it so. *Against:* it is the "mini-waterfall" of [5]; a
complete description is the specification every lean source drops
(F5), and the one page that describes it rests on a phone maker's
documentation (F4); the note of 2026-09-28 lists "the upper layer
becomes a specification" among the known failures.

**B. No layer: the interface lives in a prototype and in the
stories.** *For:* the current of F7; the prototype is what works on
every audience [9]. *Against:* it presumes one team in constant
conversation (F6), which is not the frame's case, and its own
advocate stops at the small team [20]; it leaves nothing versioned
to iterate on or to review; [14] on organisational memory.

**C. A layer in two weights.** A first shape that is rough: the
places of the application, what stands on each and in what order,
and how one gets from place to place, in words; detail (states,
limits, wording, errors) added where and when the build asks for it;
the look not in it but cited from a design system. *For:* structure
comes before surface in every order found (F4); the rough statement,
the path and the pattern library are exactly what lean practice
keeps (F5); the third kind of work of [6]; a lone author keeps the
steps and cuts the finish (F6); the sources themselves answer how
light a first shape can be. *Against:* it needs a rule saying when
the detail is owed; [13] leaves that detail to designers who work
during the build, a role the frame does not have.

**D. No layer of its own: screen and stories as one unit.** Each
screen on a page with the stories it serves, and a map of the
screens (F2, F3, Unexpected). *For:* the lightest hand-over found
that a person who is no specialist can write [19]; the tie between
story and screen is explicit and can be checked [18]. *Against:* one
guide, inconsistent in its own order; it fuses two documents the
frame's chain keeps apart; nothing in it carries the structure above
the screens beyond the map.

## Relevance to this project

**Recommendation, the agent's own inference from F1 to F7: option C,
standing where option A stands, with the tie of option D.** A
document of its own below the business requirements and beside the
solution design (the technical design), its first shape light as in
C, the visual design kept out of it, and every screen tied to the
user stories it serves. The second round did not move the
recommendation; it changed one of its grounds, said below.

What it rests on. Every source, of both placements, has the
interface of a thing worked out before its code (F1). Structure
precedes surface in every order found (F4), so a first shape may
stop at structure and skeleton and still be whole. What lean
practice keeps is what C's first shape holds (F5). The sources that
cut documents bring them back where the builder cannot be spoken to
(F6): a developer outside the room or a coding agent is that case.
That last step is the agent's inference; no page opened speaks of
such a builder.

What changed. The first round held that the user stories would cite
the description and not the reverse. The sources do not decide that
(F2): research on requirements writes the stories first and checks
the interface against them, product practice has the design first,
one guide writes them together. What all three share is that story
and screen are tied one to the other. The agent's inference: in a
chain whose last document is the user stories, the description
stands before them by the chain's own order, and what the sources
ask for is the tie, in whichever direction, stated so that it can
be checked.

What it is chosen against. Against B, because its condition, one
team in one conversation, is not the frame's, and because a
framework of versioned documents would have nothing to version.
Against a full A, because the description complete to the pixel is
what the whole current attacks and what F5 shows dropped, and
because the hand-over criticised in F7 is that of a finished
document between roles, which a document iterated in a repository
and remade when the interface changes need not be. Against D alone,
because it rests on one guide and gives up the document of the
interface as a whole.

What the sources leave open. Whether the layer stands above the
solution design or beside it: no source read sets interface work
against technical design. Whether the two authors need two shapes:
[21] says of a lone designer that the steps stay and the finish
goes, which supports one document and one order for both, the person
working end to end stopping at the rough shape plus what the build
asks, the specialist carrying the same document on into states and
annotations; for an author who is also the builder this is the
agent's inference alone. That people judge an interface by what they
see [9] suggests the text needs a preview to be judged at all; that
belongs to another card.

Consult when: the place of the interface layer among the chain's
layers is decided; the least content of its first shape is decided;
the tie between user stories and the description is designed;
someone holds that such a layer is waste or that hand-over documents
are dead; the same document is to serve a solo author and a
specialist.

## Sources

Sources 1 to 14 were opened in the first round and are numbered in
the order first cited there; 15 to 21 were opened in the second
round; 22 to 27 were not opened and are cited for no content.

1. "How to Design an Educational User Experience with The Garrett
   Method", Marc Raymond, Columbia Center for New Media Teaching and
   Learning, 2013-04-29 (byline).
   https://ccnmtl.columbia.edu/enhanced/noted/how_to_design_an_educational_user_experience.html
   Kind: secondary (on Garrett's book of 2002). Read: summarised
   fetch of the whole page. Original.
2. "Notes on User Centered Design Process (UCD)", eds. Shawn Lawton
   Henry and Justin Thorp, W3C Web Accessibility Initiative,
   Education and Outreach Working Group, version 2004.03.31 (shown
   on the page; file last updated 2008-04-18).
   https://www.w3.org/WAI/redesign/ucd
   Kind: secondary (on ISO 13407:1999). Read: summarised fetch of
   the whole page. Original.
3. "User-centered design", Wikipedia, last edited 2026-09-08 (page
   footer).
   https://en.wikipedia.org/wiki/User-centered_design
   Kind: tertiary. Read: summarised fetch, the sections on the
   process, the principles and the further reading. Original.
4. "ISO 9241", Wikipedia, last edited 2026-09-03 (page footer).
   https://en.wikipedia.org/wiki/ISO_9241
   Kind: tertiary. Read: summarised fetch, the part on ISO 9241-210
   and ISO 13407. Original.
5. "Dual-Track Agile", Marty Cagan, Silicon Valley Product Group,
   2012-09-17 (header), with an undated update note at the top.
   https://www.svpg.com/dual-track-agile/
   Kind: primary. Read: summarised fetch of the whole page, read
   twice. Original.
6. "Dual Track Development is not Duel Track", no byline, the site
   of Jeff Patton & Associates, written in the first person; the
   page shows 2017-05-10 and 2023-04-12.
   https://jpattonassociates.com/dual-track-development/
   Kind: primary for its own argument, secondary for Sy's paper
   [24]. Read: summarised fetch of the whole page, read twice (the
   second reading returned the long passages in paraphrase).
   Original.
7. "Doing UX in an Agile World: Case Study Findings", Hoa Loranger,
   Nielsen Norman Group, 2014-05-26 (byline).
   https://www.nngroup.com/articles/doing-ux-agile-world/
   Kind: primary (the author's own interviews, eight people). Read:
   summarised fetch of the whole page. Original.
8. "Designing A Better Design Handoff File In Figma", Ben Shih,
   Smashing Magazine, 2023-05-26 (byline).
   https://www.smashingmagazine.com/2023/05/designing-better-design-handoff-file-figma/
   Kind: primary (a practitioner's guide; the publisher sells no
   design tool). Read: summarised fetch of the whole page. Original.
9. "Which UX Deliverables Are Most Commonly Created and Shared?",
   Page Laubheimer, Nielsen Norman Group, 2015-10-18 (byline).
   https://www.nngroup.com/articles/common-ux-deliverables/
   Kind: primary (the publisher's own survey, 86 respondents; the
   time of the survey is not stated). Read: summarised fetch of the
   whole page, read twice. Original.
10. "Lean UX: Getting Out Of The Deliverables Business", Jeff
    Gothelf, Smashing Magazine, 2011-03-07 (byline).
    https://www.smashingmagazine.com/2011/03/lean-ux-getting-out-of-the-deliverables-business/
    Kind: primary. Read: summarised fetch of the whole page, read
    twice. Original.
11. "No Handoff – We can stop throwing our work over the fence", the
    site of the No Handoff method, no byline (the contact link
    names Shamsi Brinn), undated.
    https://www.nohandoff.org/
    Kind: primary (the method's own site). Read: summarised fetch
    of the landing page only; the article it points to for the full
    method was not opened. Original.
12. *Atomic Design*, chapter 4, "The Atomic Workflow", Brad Frost;
    dated by the page's copyright notice, 2016.
    https://atomicdesign.bradfrost.com/chapter-4/
    Kind: primary. Read: summarised fetch of the whole chapter, read
    twice. Original.
13. *Shape Up*, chapter 4, "Find the Elements", Ryan Singer,
    Basecamp; undated.
    https://basecamp.com/shapeup/1.3-chapter-04
    Kind: primary. Read: summarised fetch of the whole chapter, read
    twice. Original.
14. "Getting Back Into The (Right) Deliverables Business", Rian van
    der Merwe, Smashing Magazine, 2015-12-04 (byline).
    https://www.smashingmagazine.com/2015/12/getting-back-into-right-deliverables-business/
    Kind: primary. Read: summarised fetch of the whole page.
    Original.
15. "The Elements of User Experience", a review of Garrett's book
    (New Riders, 2002) by Jeff Lash, Boxes and Arrows, 2002-10-21
    (byline).
    https://boxesandarrows.com/the-elements-of-user-experience/
    Kind: secondary (a review; it lists the book's chapter titles).
    Read: summarised fetch of the whole page. Original.
16. "Human Centered Design (HCD)", National Institute of Standards
    and Technology, Information Technology Laboratory; created
    2021-04-12, updated 2026-05-27 (shown on the page), with the
    notice "This page is no longer being updated and the information
    may be out of date."
    https://www.nist.gov/itl/iad/visualization-and-usability-group/human-factors-human-centered-design
    Kind: secondary (on ISO 9241-210:2010 and ISO 9241-110). Read:
    summarised fetch of the whole page, read twice. Original.
17. "User interface specification", Wikipedia, last edited
    2025-06-13 (page footer).
    https://en.wikipedia.org/wiki/User_interface_specification
    Kind: tertiary; it cites three web sources, a commercial site
    and two archived pages of a phone maker's developer
    documentation, and no method literature. Read: summarised fetch
    of the whole page. Original.
18. "Interlinking User Stories and GUI Prototyping: A Semi-Automatic
    LLM-based Approach", Kristian Kolthoff, Felix Kretzer, Christian
    Bartelt, Alexander Maedche, Simone Paolo Ponzetto (University of
    Mannheim; Karlsruhe Institute of Technology), arXiv:2406.08120v1
    [cs.SE], 2024-06-12 (as printed on the page); venue not stated.
    https://arxiv.org/html/2406.08120v1
    Kind: primary (a research preprint). Read: summarised fetch of
    the whole page, read twice. Original.
19. "From Idea To Development: How To Write Mobile Application
    Requirements That Work", Eduard Khorkov, Smashing Magazine,
    2017-05-08 (byline); the author heads an agency that builds
    mobile applications, so the guide speaks of his own trade, at a
    publisher that is not his.
    https://www.smashingmagazine.com/2017/05/writing-mobile-application-requirements/
    Kind: primary (a practitioner's guide). Read: summarised fetch
    of the whole page, read twice. Original.
20. "The Best Handoff Is No Handoff", Vitaly Friedman, Smashing
    Magazine, 2023-03-27 (byline); the page also advertises the
    publisher's own workshops.
    https://www.smashingmagazine.com/2023/03/best-handoff-is-no-handoff/
    Kind: primary for its author's position, secondary for the two
    methods it reports (No Handoff, the "hot potato" process). Read:
    summarised fetch of the whole page, read twice. Original.
21. "What to Do When You're the Only UX Designer on a Project?", the
    column Ask UXmatters by Janet M. Six, UXmatters, 2017-07-24
    (byline); eight practitioners answer a reader's question, the
    magazine's publisher among them.
    https://www.uxmatters.com/mt/archives/2017/07/what-to-do-when-youre-the-only-ux-designer-on-a-project.php
    Kind: primary (practitioners' statements). Read: summarised
    fetch of the whole page, read twice. Original.
22. Jesse James Garrett, "The Elements of User Experience", the
    diagram of 2000 and the book of 2002. Kind: primary. Not opened:
    the author's site returned a certificate error, the publisher's
    excerpt is gone, the book's page at an online library refused
    (403), a university's copy of the diagram came back as PDF bytes
    the tool could not read. Not cited for content; known through
    [1] and [15].
23. ISO 9241-210, "Human-centred design for interactive systems"
    (2010, updated 2019). Kind: primary. Not opened: the standard is
    sold; the standards body's page refused (403); a table of
    contents and a sample came back as PDF bytes the tool could not
    read; a practitioner's article was not found at the address
    tried (404); a paper on the standard stands behind a login. Not
    cited for content.
24. Desirée Sy, "Adapting Usability Investigations for Agile
    User-centered Design", Journal of Usability Studies, 2007. Kind:
    primary. Not opened: not found at the journal's addresses tried.
    Known through [6] only.
25. Leah Buley, *The User Experience Team of One*, Rosenfeld Media.
    Kind: primary. Not opened: the publisher's page refused (403).
    Not cited for content.
26. The results of the disconfirming query other than [10], [14] and
    [20]: "UX deliverables are dead — long live collaboration" and
    "The death of the deliverable" (a design publication on a
    blogging platform), "Only one deliverable matters" (a design
    studio's site), "Handoff is dead" (a design agency's blog), "UX
    designers: why are we wasting time" (a consultancy's blog), "The
    design handoff is dying" and "Stop trying to fix the handoff
    process" (personal and community pages), "The Designer-Developer
    Handoff Is Still Broken — why?" (a web magazine). Not opened:
    most are a seller's page on its own market or unsigned; the
    budget went to primaries. Titles only; not cited for content.
27. The results of the second round's queries on handoff guides and
    on AI coding agents: pages of the sellers of design, whiteboard,
    prototyping and builder tools, a design-tool forum, unsigned
    posts on community platforms, a consultancy's blog on designing
    by specification, and a company's design system page on handing
    designs to development (refused, 403). Not opened, by kind or
    because refused. Not cited for content.

## Opened and not used

- First round. Peachpit, the address a search gave for the book
  excerpt "Meet the Elements of Web User Experience": opened, with
  and without "www"; it now leads to a listing of other articles,
  the excerpt is gone.
  https://www.peachpit.com/articles/article.aspx?p=30220
- Second round. The address a search gave for Sy's paper at the
  Journal of Usability Studies: opened; it leads to the listing of a
  current issue of the journal, without the article.
  https://uxpajournal.org/?p=1523

## Search record

The run had two rounds. In the first the search tool refused every
query after the third, the session's search budget being used up,
and the note said what could not be searched. The second round was
ordered by the run's coordinator once search worked again: to run
the queries that had been refused or not run, the disconfirming
query among them, and one differently worded query for the stop
rule, and to open at most eight further pages.

First round, queries in order:

1. UX design process deliverables, order, handoff: the result list
   read; it gave [9].
2. Garrett, elements of user experience, the five planes: the result
   list read; it gave [1] and the addresses of [22] that failed.
3. Lean UX, "getting out of the deliverables business": the result
   list read; it gave [10] and [14].
4. Dual-track agile, discovery and delivery, one sprint ahead:
   refused.
5. ISO 9241-210, the activities of human-centred design: refused.
6. "design handoff is dead": refused, twice.
7. "UX deliverables are waste" OR "design handoff is dead": performed
   at the end of the round, the budget having refilled.

First round, pages opened, fifteen: [1] to [14] and the Peachpit
page; the routes of queries 4 to 6 were walked by opening addresses
the agent knew beforehand, each cited only because it opened. Five
pages ([5], [9], [10], [12], [13]) were fetched a second time for
the wording of the quotations, and [6] for a link and its long
passages. Eight further addresses did not open: the journal's page
of [24] (404), the author's site of [22] twice (certificate error),
the book's page of [22] at an online library (403), a practitioner's
article on [23] (404), an open textbook's page on the planes (403),
a practitioner's article on a process without hand-over (404), and
the publisher's page of [25] (403). The round ended by the opening
budget.

Second round, queries in order, twelve:

8. Dual-track agile, one sprint ahead, Sy's paper by its title: the
   result list read; sellers' glossaries and an analyst's report,
   nothing opened.
9. ISO 9241-210, activities, context of use, user requirements,
   design solutions: the result list read; the standards body's
   page, tables of contents, a paper.
10. "design handoff is dead": the result list read; it gave [20].
11. "UX deliverables are waste": the result list read; the titles of
    [26], with [10], [14] and [9] among them.
12. Design handoff guide, "design specs", annotations, "ready for
    dev": the result list read; sellers' pages almost alone [27].
13. Sy 2007, the paper by title and journal: the result list read;
    it gave the address that leads to a listing.
14. Garrett's diagram, by the labels remembered from it: the result
    list read; it gave [15] and a copy of the diagram.
15. "UX team of one", which deliverables to skip and keep: the
    result list read; it gave [21].
16. The differently worded query for the stop rule, where interface
    design fits between requirements and development, user stories
    with wireframes attached, acceptance criteria, design before the
    sprint: the result list read; it gave [17], [18] and [19].
17. Designer and developer handoff with an AI coding agent, 2026,
    whether a design specification is still needed: the result list
    read; nothing opened, by kind [27].
18. ISO 9241-210, the six principles and four activities, by two
    phrases remembered from it: the result list read; tables of
    contents and a sample, all PDF files.
19. Sy's paper at the journal's new addresses: the result list read;
    nothing new.

Second round, pages opened, eight: [15], [16], [17], [18], [19],
[20], [21] and the journal's listing page. Five of them ([16], [18],
[19], [20], [21]) were fetched a second time for the wording. Six
further addresses did not open or could not be read and are not
counted as pages: a paper on [23] (redirect to a login), a
university's copy of the diagram of [22], a national standards
body's table of contents of [23] and a sample of [23] (each
delivered as PDF bytes the fetch tool could not read; the saved
bytes were not opened), the standards body's page of [23] (403), and
a company's design system page (403).

The disconfirming query. Its two halves, run apart in the second
round (queries 10 and 11), found what the card expected: a current
against handing documents over, by the titles of [26] and by [20],
beside [5], [10], [11] and [12] of the first round. They also
returned the reply [14] and the survey [9]. What it did to the
answer is F7, which held.

The differently worded query (16) did bring something new: the three
sources by which F2, F3 and F4 changed.

Why the run ended. The second round ended by its budget of eight
pages. The card's stop rule is still not met, on both of its parts:
the differently worded query brought new material, so that nothing
new from such a query has not yet been seen; and the layered model
has no primary source in this note, Garrett's own text and diagram
being unreadable or refused in both rounds. The human-centred design
standard is read through secondary pages, as the card asked, with
the attribution of its principles left open; the lean, the
dual-track, the hand-over and the solo routes have their authors'
own pages.
