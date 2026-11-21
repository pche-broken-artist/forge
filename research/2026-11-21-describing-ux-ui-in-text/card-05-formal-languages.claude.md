---
date: 2026-11-21
project: forge
topic: Formal languages and standards that describe a user interface independently of its implementation, and what became of them
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-05-formal-languages
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 5; no known note named by the card; web sources below
---

# The formal languages and standards that describe a user interface independently of its implementation: what each describes, what became of it, and the reasons given

<!-- Shape: templates/research.md -->

## In short

Every language the card names exists as a document of a standards
body or of a research consortium, and none became a standard that
practice builds on. The W3C's model-based work ended in Working Group
Notes in 2014 and the group closed the day after the last one; UIML
stopped at OASIS, its committee marked completed with a committee
draft as the latest text; UsiXML and MARIA fed those W3C notes and
reached no standard of their own; the W3C Forms Working Group, the
home of XForms, closed in 2015; IFML stands at version 1.0 of
February 2015, the only version its publisher lists, with one
commercial tool named for it. ISO 9241 and the Common Industry Format
are of another kind: principles, guidance and the content of
documents, not a language in which an interface is written down. The
W3C community group of 2025 on a schema for the specification of
single interface elements was verified: it existed and was closed
for inactivity on 21 May 2026. The facts of status are sure, read
from the publishers' own pages. The reasons for the absence of
adoption are less sure: they rest on a W3C incubator report of 2010
and a position paper of 2017, both written by proponents, since the
academic surveys could not be opened. The disconfirming query found
no report of broad industrial success, only pockets claimed by those
who work in them. The unexpected thing: by the W3C group's own
account practitioners skip the upper levels and start at the concrete
interface, and the group's own advice was to agree on the model and
let the syntax vary.

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

> #### Card 5: Formal languages and standards
> - **Question:** Which formal languages and standards describe a user interface or its interaction independently of its implementation (the model-based tradition with its levels of task, abstract, concrete and final interface; UsiXML, UIML, MARIA, XForms, the W3C's notes; IFML; the parts of ISO 9241), what does each describe, what became of each in practice, and which reasons are given for adoption or its absence?
> - **Why it matters:** a layered description independent of the platform is what four target platforms ask for; the fate of these languages says what to borrow and what to avoid.
> - **What would answer it:** the standards' own documents and academic studies of their adoption.
> - **Where to look:** the W3C's model-based UI working group; the IFML specification; surveys of model-based UI development; ISO through secondary pages. Search words from card 1: "user interface description language", "model-based user interface development", "CAMELEON reference framework", "task model", "Common Industry Format" (ISO/TR 25060); the W3C's UI Specification Schema Community Group of 2025 and 2026, to be verified; why the notes of 2014 and the version of 2015 had no successor.
> - **Disconfirming query:** "model-based user interface development industrial adoption success"; expected: little adoption, with a few fields where it held.
> - **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

What the note must beat: the expectation the card itself states, that
these languages exist and found little adoption. A note that only
repeats this adds nothing. This one has to say for each language,
from its publisher's own page, what it describes and where it stands
on the day of reading, and to give the reasons for adoption or its
absence with their sources and with the weight those sources can
bear.

## Key findings

How the pages were read holds for every finding below: each page was
read through a fetch tool that hands the page to a small model and
returns that model's answer. Verbatim extracts were asked for and
are given here in quotation marks as the tool returned them, in
fragments of at most about 125 characters; whatever stands outside
quotation marks rests on the tool's summary, and where a finding
depends on such a summary it says "the fetch's paraphrase".

F1. **The model-based tradition has one shared frame, the CAMELEON
Reference Framework, and the frame has four levels.** [consensus
within the model-based community; a standards body's note and its
incubator report] The W3C note of 2014 [1] defines the levels in its
Introduction. Task and domain: "the hierarchies of tasks that need
to be performed on/with domain objects". The abstract interface,
whose units "are independent of any implementation technology or
modality (e.g., graphical, vocal, gestural)". The concrete
interface, whose units are "modality-dependent, but implementation
technology independent, thus platform specific (PSM)" and which
"concretely defines how the UI is perceived and can be manipulated
by end users". The final interface, "implementation technology
dependent source code". The same note lists the benefits claimed for
the approach in seven groups and, by the fetch's report, has no
section on shortcomings [1]; the criticism stands in the incubator
report of 2010 [2] and is gathered in F8.

F2. **The W3C set out to make two Recommendations and ended with
Working Group Notes; the group closed the day after the last note.**
[consensus on the facts; the standards body's own pages] The charter
[3] begins its timeline with "November 2011: First teleconference.",
plans two deliverables on the Recommendation track (by the fetch's
paraphrase, meta-models for the front ends of context-aware
interactive applications, and a markup language and API) to reach
Recommendation in August 2013, and gives its end as "30 November
2013". The note on abstract interface models [4], dated 08 April
2014, says in its Status section that it was published as a Note "to
reflect the fact that the Model Based UI Working Group" "is no
longer progressing it along the W3C Recommendation Track." The
group's page [5] says: "The Model-Based User Interfaces Working
Group was closed on 9 April 2014." The two end dates differ: [3]
says 30 November 2013, [5] says "Chartered until 9 April 2014."; an
extension of the charter would explain it, which is this note's
inference. No opened page states why the Recommendation track was
left. Two statements stand near the answer: the incubator report had
written in 2010 that "the existence of interoperable implementations
will be critical in order to progress the specifications" [2]
(section not recorded), and the note of 2014 says of the tools
available, under Examples of Tools, that "none of them, so far,
implements the MBUID standard" [1]. That missing implementations
ended the track is this note's inference from the two, not a
source's statement.

F3. **An earlier W3C attempt had already failed, and the reasons
named for it are about who takes part, not about the technique.**
[single source; incubator report, a participants' account] By the
fetch's paraphrase of section 6.2, Challenges for Deployment, under
Standardization, the report [2] names the Web Application Formats
working group, launched by the W3C in 2006 to define a declarative
format for applications and user interfaces, and says it failed. The
causes are quoted: "the absence of contributions from big software
vendors that owned XML languages for UIs"; "Different interests in
the group concerning the platforms to be addressed (desktop, mobile,
...)."; "the HTML5 Community saw the new format as a competitor."

F4. **UIML is an abstract meta-language for any interface, and it
stopped at OASIS short of a standard.** [single source for each
fact; the standards body's page] The committee's page [6] gives its
purpose as "to develop a specification for an abstract
meta-language" "that can provide a canonical XML representation of
any user interface (UI)." The page is headed with the status
"Completed", gives no date for it, lists the latest draft of UIML
4.0 as a Committee Draft and lists no OASIS Standard. As fetched the
page is not consistent with itself: under the status "Completed" it
still carries a section of current activities. The incubator report
says UIML "was one of the first model-based languages for describing
UIs" [2].

F5. **UsiXML and MARIA are research languages over several levels
of abstraction; both fed the W3C notes and neither reached a
standard of its own.** [consensus on what they are; single source
on their fate; W3C documents and the funding programme's page] The
incubator report [2] says UsiXML "is an XML-compliant markup
language, which aims to describe the UI for multiple contexts of
use." and MARIA "is a universal, declarative, multiple abstraction
level language for service-oriented applications". The programme's
page of the UsiXML project [7] gives "Oct 2009 - Mar 2013", "25
partners", "6 countries" and "Winner ITEA Award of Excellence
Standardisation 2013". The W3C charter [3] names "UsiXML or UIML"
among the work to draw upon and "The MARIA Environment" under
external groups. The note on abstract interface models [4] says its
meta-model "is based on the review of the submissions and related
work" and, by the fetch's paraphrase, maps its concepts in a Related
Work section to UsiXML, MARIA and five further models. The route by
which both sought the standing of a standard is therefore the W3C
group of F2, and that route ended in a Note. What became of either
language after 2014 was not found.

F6. **XForms is the W3C's standard for forms, narrower than the
others, and its working group is closed.** [single source for the
claim of adoption, a W3C group on a W3C standard; the standards
body's page for the status] The incubator report wrote in 2010:
"XForms is a widely adopted W3C-standard targeting the next
generation of (web) form applications." [2] The group's page [8]
gives the mission "to develop specifications to cover forms on the
Web," and says: "The Forms Working Group was closed on 8 April
2015.", with "Chartered until 31 March 2012". No independent measure
of the use of XForms was opened, so "widely adopted" stands as the
word of one W3C group about another's standard.

F7. **IFML, the OMG's standard for the interaction flow of a front
end, stands at its first version, of February 2015.** [consensus on
the status, the standards body's page; single source on adoption, a
position paper] The OMG's page [9] gives the Interaction Flow
Modeling Language at version 1.0, publication date February 2015,
document number formal/15-02-05, and lists no other formal version
on the day of reading, 2026-11-21. It describes "the principal
dimensions of an application front-end": "the view part of the
application, made of view containers and view components;", the
objects that hold the state of the application with the references
to business logic, "the binding of view components to data objects
and events;", "the control logic that determines the actions to be
executed after an event occurrence;", and the distribution of
control, data and logic over the tiers. The copyright holders of
2014 listed on the page include a tool vendor, WebRatio Inc., among
seven companies; the page names no revision task force. Of use in
practice one paper was read [10]: "WebRatio is a powerful tool to
support the IFML visual modeling standard." and "WebRatio is the
current leader tool in the market within the context of MDWE
approaches."; of the model-driven web engineering approaches as a
whole its abstract says that "they have attracted little attention
from the Industry due to the mismatch between technical versus
research requirements." No source was found that says why IFML had
no version after 1.0.

F8. **The reasons given for the absence of adoption agree across
the two sources read, and all of them are claims of experts who
favour the approach, none a measurement.** [consensus among
proponents; expert and practitioner claim, no controlled study, no
survey with figures] The reasons, each with where it stands:

- The languages are many, unlike each other, proprietary or
  stopped. "Most UIDLs are limited in scope and/or usage, have been
  stopped or are the property of some companies" [2] (section 2.3);
  "Companies or developers might be reluctant to adopt MBUI if it is
  based on proprietary methods, models or languages." [2]; "the
  tools that exist rely on proprietary formats, or APIs specific to
  particular programming languages" [3].
- A model leaves less freedom than writing the application. "One of
  the main criticisms to MBUI is that there is no the same
  flexibility as developing an application" [2] (section 6.2, under
  Flexibility). The paper of 2017 names it "Lack of Control in
  Development and Deployment", with "creating a dependency between
  the MDWE tool and the development teams", and adds "Rigid
  Architecture" [10] (sections 2.1 and 2.6).
- The upper levels are skipped in practice. "practicioners often
  skip this stage, and directly produce CUIs using protyping tools
  such as Flash" "because of the lack of tools allowing rapid
  prototyping from task models" [2] (section 2.4.2, the stage being
  task modelling); "In the automotive industry UIs are developed
  starting at the CUI level." [1] (Use Case 6).
- The tools do not carry the author. The report asks for "advanced
  developing tools that shield authors from all the theoretical
  artefacts" [2]; the paper lists "Lack of Tools" and "Traceability
  and Debugability", the latter with "All these aspects make core
  engineers to avoid adopting MDWE tools" [10] (sections 2.5 and
  2.4).
- Community and cost. "there is a lack of consensus and
  documentation between approach designers" [10] (section 2.8), and
  licensing as a ninth challenge [10] (section 2.9).
- Those who would have to adopt it were not in the room. "It is
  necessary to attract mainstream web developers to MBUI" [2]; the
  interest in a standard in 2010 lay, beside the academic community
  (the fetch's paraphrase), with "a few telco companies and some
  niche SMEs (specialized in Model-Based technologies)" [2] (section
  6.4, Outlook).
- A syntax is harder to agree on than a model. By the fetch's
  paraphrase of section 6.3 the report calls it "rather challenging
  (and likely to fail)" to standardise meta-models and semantics
  together with a concrete syntax, and puts its advice in the words
  "One (standard) Model, Many Syntaxes" [2].

F9. **ISO 9241 and the Common Industry Format do not describe an
interface; they say what a good one obeys and which documents a
human-centred design leaves behind.** [single secondary source for
ISO 9241, a page that carries a notice asking for more citations; a
seller's copy of the abstract for the Common Industry Format; no
ISO text read in the original] The parts of ISO 9241 that concern
software, as the secondary page lists them [11]: 110 on dialogue or
interaction principles, 112 "Principles for the presentation of
information", 125 "Guidance on visual presentation of information",
129 on individualization, 143 "Forms", 151 "Guidance on World Wide
Web user interfaces", 154 on voice response applications, 161
"Guidance on visual user interface elements", 171 "Guidance on
software accessibility", and 210 "Human-centred design for
interactive systems". Part 110 gives seven principles: "Suitability
for the user's tasks", "Self-descriptiveness", "Conformity with user
expectations", "Learnability", "Controllability", "Use error
robustness", "User engagement" [11]. The page lists part 110 under
its older title, "Dialogue principles", and describes it by the
newer one; the note does not settle which is current. The general
framework of the Common Industry Format, ISO TR 25060:2023,
published 2023-04-06 by ISO/TC 159/SC 4, "describes information
items enabling systematic human-centred design for interactive
systems.", gives "the high-level content structure to be used for
documenting each information item." and "does not prescribe any kind
of method, life cycle or process." [12] The card writes "ISO/TR
25060"; the edition read of here is of 2023 and carries the
reference ISO TR 25060:2023 in the seller's catalogue.

F10. **The W3C's UI Specification Schema Community Group existed
and was closed for inactivity on 21 May 2026, with no deliverable
linked from its page.** [single source; the standards body's own
pages] The group's page [13] says: "The UI Specification Schema
Community Group was closed on 21 May 2026." Its stated aim: it "will
define a common, implementation-agnostic meta-model for specifying
the design, layout, behaviour, and constraints" of interface
elements and would "Produce and maintain a formal schema (JSON/JSON
Schema) for authoring and validating per-instance specifications";
by the fetch's paraphrase it meant to align its vocabulary with Open
UI and with the Design Tokens Community Group, and the page links no
report and no repository. The archive of its mailing list [14] holds
one message, from the W3C's staff, dated 2 April 2026, with the
subject "Planning to close UI Specification Schema Community Group
due to inactivity unless we hear from you". The page as fetched
gives no date of founding; pages in the search results, not opened,
date the proposal to August 2025.

F11. **The disconfirming query found no report of broad industrial
success; what the opened pages hold are pockets, each claimed by
those who work in them.** [single source each; proponents' and one
vendor's claims, no independent measurement] The pockets: interfaces
in the automotive industry, developed "starting at the CUI level"
[1]; useML, "a notation for specifying enhanced task models in
industrial environments", which "has shown its applicability and
usefulness in several other domains e.g. automotive or medicine"
[2]; a task-model language for consumer electronics, "ANSI/CEA-2018
defines a task model description language aimed at the user
interfaces for consumer electronic devices." [3]; web applications
of enterprises through the one tool built on IFML [10]; and a
vendor's claim that the W3C note quotes, "Integranova creates
customised solutions in half the time, personalised solutions for
half the price, and top-quality, error-free software." [1] (vendor
claim, 2012). The one academic overview whose record could be
opened says in its abstract: "After 30 years of research there has
been significant success in modeling user interfaces." [15]: success
in modelling, which is not adoption, and its full text could not be
read.

## Unexpected

The card assumes that a layered description independent of the
platform is what four target platforms ask for. The W3C's own
documents say that practitioners did not work in layers: they
skipped task modelling and began at the concrete interface [2], the
automotive industry likewise [1], and the incubator group itself
wrote "Nonetheless, we think that AUI and CUI should have priority
over other layers." [2] In the framework's own words the concrete
level is "platform specific" [1]; the level common to several
platforms is then the abstract one, the level that by these accounts
nobody in practice wrote. The last sentence is this note's reading,
not a source's.

The community group of F10 aimed at something close to the idea the
frame wants tested, a small definition of its own for every element:
a schema for "per-instance specifications" of interface elements
[13]. By its archive it drew no discussion at all before the W3C's
staff moved to close it [14]. The page names Open UI and the Design
Tokens Community Group as the neighbours it meant to align with
[13]; whether the living work is there is a lead for the cards on
components and on pages composed of blocks, not a finding here.

The notes of 2014 were a closing act, not a stage on a way: the last
of them is dated 08 April 2014 [4] and the group closed on 9 April
2014 [5]. No group was left to write a successor, which answers part
of the card's question of why there was none; why no new group was
chartered was not found.

The incubator report's advice, "One (standard) Model, Many Syntaxes"
[2], separates two things a description language fuses: what kinds
of statement a description holds, and the notation they are written
in. The report judged agreement on the first reachable and on the
second likely to fail.

A lead not opened: a search result list named ARINC 661, a standard
for cockpit display systems in avionics, as a field where the
definition of an interface is kept apart from the application that
uses it and is in use in aircraft programmes. The page was not
opened and nothing in this note rests on it.

## Not found

- No measured study of the industrial adoption of model-based
  interface development, or of any language the card names, was
  read. Two surveys the search results pointed to could not be
  opened ([16], HTTP 504; [17], HTTP 403), and the full text of the
  overview [15] came as an encrypted PDF the fetch could not read
  ([18], HTTP 405, for the publisher's copy).
- No statement by the W3C of why the model-based group left the
  Recommendation track or why no successor was chartered; looked for
  in [1], [4], [5].
- No statement by the OMG or by IFML's authors of why no version
  followed 1.0; looked for on [9], which names no revision task
  force.
- The state of XForms 2.0 after the closing of the Forms Working
  Group in 2015: [8] carries no word on it; search results, not
  opened, point to a community group of XForms users.
- The date on which the UIML committee closed and whether UIML 4.0
  rose above a Committee Draft: [6] gives neither; search results,
  not opened, point to a Committee Specification of May 2009 and a
  closing notice of March 2010.
- What became of UsiXML and of MARIA after 2014, in tools or in use:
  no page of their makers was opened; [7] lists a "success story" of
  2019 by its title only.
- The parts of ISO 9241 in ISO's own words, and the names of the
  single documents of the Common Industry Format (a user
  requirements specification among them, by a search result not
  opened): ISO's page returned HTTP 403 ([19]); the 2025 edition of
  part 161 is known here from a search result only.
- The founding date of the community group of F10 from an opened
  page.

## Options

1. **Take one of the languages as the notation of the description**
   (IFML for the flows, UsiXML or MARIA for the abstract and the
   concrete interface). It brings a defined meta-model. Against it:
   each stands still or is closed (IFML at 1.0 since February 2015
   [9]; the W3C notes off the Recommendation track [4]); the
   notations are XML and diagrams, not Markdown; one commercial tool
   is named for IFML [10]; and the tool chain of generation is where
   the criticism lands [2], [10].
2. **Borrow the vocabulary and the kinds of content, keep the
   project's own Markdown.** The four levels as names for what a
   statement is about [1]; IFML's list of dimensions as a list of
   what a description of a flow must cover [9]; the report's "One
   (standard) Model, Many Syntaxes" as the rule that the content is
   fixed and the notation free [2]. Against it: nothing is exchanged
   with any tool, though by F2 to F7 there is little to exchange
   with; the kinds of content must be defined by the project itself.
3. **Enter at the concrete level only**: a description of screens,
   graphical and independent of the technology, with no task level
   and no abstract level of its own, as practitioners did [1], [2].
   It is the shortest way to something that can be seen. Against it:
   the differences between platforms have no common level above
   them, since the framework calls the concrete level platform
   specific [1].
4. **Use the ISO documents as a frame around the description, not
   as its notation**: the seven principles of part 110 as criteria
   [11], and the Common Industry Format's way of fixing the content
   of a document without prescribing a process [12]. Against it: the
   texts are sold, and none was read in the original here.

## Relevance to this project

Borrow the concepts and leave the languages. The recommendation is
option 2 with the order of entry of option 3, and option 4 kept for
the cards that ask how a proposal is judged. It rests on F2 to F7:
on the day of reading none of the named languages is a living
standard with tools a build stage could be expected to have, so
adopting one would buy a notation and no neighbours. It rests on F8
too: the reasons given for the absence of adoption gather around the
dependence on a tool that generates, around the loss of freedom for
the one who builds, and around upper levels that authors skip. It is
chosen against option 1, and against inventing a schema for single
elements in the hope that a standard will meet it: the W3C group on
that very schema closed for inactivity in May 2026 (F10).

What to borrow, each this note's own inference from the findings:

- The names of the levels, as a way to say what a statement of a
  description is about, and the definition of the concrete level as
  bound to a modality and free of the technology [1].
- The thought that the task level need not be written anew: the
  chain of the frame already holds requirements and user stories,
  which is where the framework puts tasks and the things they act
  on. Whether they hold enough of it is a question for the card on
  what a description cites.
- The rule that the kinds of content are agreed and the notation is
  free [2].
- IFML's five dimensions as a check of what a description of
  interaction covers [9].

What to avoid, likewise inferred:

- A description whose worth depends on automatic generation from
  it; the criticism of F8 is aimed there, and the frame hands the
  description to a build stage that may be a human.
- A pass through the upper levels as a condition of seeing
  anything; the sources say authors skip it [1], [2], and the frame
  wants the human to see the proposal.
- Waiting for, or leaning on, a standard to come: three bodies, the
  W3C, OASIS and the OMG, each stopped at a first document.

The limits of this advice: the reasons of F8 come from two sources
written by proponents, the academic surveys were not read, and the
ISO texts were seen through a secondary page and a seller's
catalogue.

Consult when: the layers of the description of an interface are
decided; someone proposes to adopt UsiXML, MARIA, UIML, XForms or
IFML, or asks whether a standard for this exists; the levels are
named; a schema for single elements is considered; the question
comes up of what a description may leave to the documents above it.

## Sources

Every source marked "summarised fetch" was read through the fetch
tool described at the head of Key findings, with verbatim extracts
asked for; none was read in full by the agent itself.

1. Introduction to Model-Based User Interfaces. W3C, Model-Based UI
   Working Group. 07 January 2014, dated by the document's own date
   line (byline).
   https://www.w3.org/TR/mbui-intro/
   Kind: primary. Read: summarised fetch; the Status section, the
   Introduction with the four levels, the headings of the Benefits
   section, Examples of Tools, the headings of the use cases and one
   sentence of Use Case 6. Original.
2. Model-Based UI XG Final Report. W3C Incubator Group, Model-Based
   UI XG. 04 May 2010 (byline).
   https://www.w3.org/2005/Incubator/model-based-ui/XGR-mbui-20100504/
   Kind: primary for the group's own positions, secondary for the
   languages it surveys. Read: summarised fetch, the same page
   fetched twice; characters 0 to 100000 of 104495, the tail (the
   references) not read; sections 2.3, 2.4.2, 6.2, 6.3 and 6.4 by
   the fetch's attribution. Original.
3. Model-Based UI Working Group Charter. W3C. Undated as fetched;
   its timeline runs from November 2011 and its end date is 30
   November 2013.
   https://www.w3.org/2011/01/mbui-wg-charter.html
   Kind: primary. Read: summarised fetch; mission, rationale,
   deliverables and milestones, the work to draw upon, external
   groups. Original.
4. MBUI - Abstract User Interface Models. W3C, Model-Based UI
   Working Group. 08 April 2014 (byline).
   https://www.w3.org/TR/abstract-ui/
   Kind: primary. Read: summarised fetch; the Status section, part
   of the abstract, the definitions of the abstract interface and of
   its unit, the list of models in Related Work, the sentence on
   compliance. Original.
5. Model-Based User Interfaces Working Group, group page. W3C.
   Undated live page, read 2026-11-21.
   https://www.w3.org/groups/wg/mbuiwg/
   Kind: primary. Read: summarised fetch; status, mission, the line
   of the charter; the list of publications was not on the page as
   fetched. Original.
6. OASIS User Interface Markup Language (UIML) TC. OASIS. Undated;
   the footer reads "Copyright © 2020 OASIS®".
   https://www.oasis-open.org/committees/uiml
   Kind: primary. Read: summarised fetch; status, statement of
   purpose, the announcement of the Committee Draft, current
   activities. Original.
7. UsiXML, project page. ITEA. Undated; the project ran Oct 2009 to
   Mar 2013 by the page.
   https://itea4.org/project/usixml.html
   Kind: primary for the facts of the project, the funding
   programme's own page. Read: summarised fetch; dates, partners,
   description, award, the titles of the listed documents. Original.
8. Forms Working Group, group page. W3C. Undated live page, read
   2026-11-21.
   https://www.w3.org/groups/wg/forms/
   Kind: primary. Read: summarised fetch; status, mission, the line
   of the charter. Original.
9. IFML — Interaction Flow Modeling Language, specification page.
   Object Management Group. Undated live page, read 2026-11-21; the
   specification on it dated February 2015.
   https://www.omg.org/spec/IFML/
   Kind: primary. Read: summarised fetch; version, date, document
   number, the abstract, the version history, the copyright holders,
   the links to the issue trackers. Original.
10. Robles Luna, E., Domínguez-Mayo, F. J., Rivero, J. M.,
    García-García, J. A., Sánchez-Begines, J. M., Escalona, M. J.,
    Rossi, G.: Challenges for the Adoption of Model-Driven Web
    Engineering Approaches in Industry. Proceedings of WEBIST 2017,
    special session APMDWE, pages 415-421. 2017 (byline). DOI
    10.5220/0006382704150421, as printed on the page.
    https://scitepress.org/Papers/2017/63827/pdf/index.html
    Kind: primary, a position paper without measurement. Read:
    summarised fetch; the abstract, the introduction, the heading
    and one sentence of each of sections 2.1 to 2.9. Original, the
    publisher's HTML.
11. ISO 9241. Wikipedia. Last edited 3 September 2026, by the foot
    of the page.
    https://en.wikipedia.org/wiki/ISO_9241
    Kind: secondary; the page carries a notice asking for more
    citations. Read: summarised fetch; the list of parts, the
    descriptions of parts 110, 11 and 210. Original.
12. ISO TR 25060:2023, Systems and software engineering - Systems
    and software Quality Requirements and Evaluation (SQuaRE) -
    General framework for Common Industry Format (CIF) for
    usability-related information, catalogue entry. IEC Webstore.
    Publication date 2023-04-06, by the catalogue's data.
    https://webstore.iec.ch/publication/95674
    Kind: secondary. Read: summarised fetch; the abstract and the
    catalogue data. A copy: a seller's entry that carries the
    abstract of the standard, used because the publisher's page [19]
    could not be opened.
13. UI Specification Schema Community Group, group page. W3C.
    Undated live page, read 2026-11-21.
    https://www.w3.org/groups/cg/uispec
    Kind: primary. Read: summarised fetch; status, mission in
    fragments, the listed goals, the links. Original.
14. Archive of the mailing list public-uispec. W3C. One message,
    dated 2 April 2026, by the archive's index.
    https://lists.w3.org/Archives/Public/public-uispec/latest
    Kind: primary. Read: summarised fetch; the index of the archive,
    not the body of the message. Original.
15. Meixner, G., Paternò, F., Vanderdonckt, J.: Past, Present, and
    Future of Model-Based User Interface Development. i-com, 2011.
    Repository record of UCLouvain; DOI 10.1524/icom.2011.0026, as
    shown on the record. The record gives volume 3; other records in
    the search results, not opened, give volume 10, issue 3.
    https://research.dial.uclouvain.be/handle/2078.5/250448
    Kind: primary article, read here through a repository's record.
    Read: summarised fetch of the record; the abstract only, the
    full text not read. A copy of the abstract.
16. Not opened: HTTP 504. By the search results a survey of
    environments for model-based interface development (Ruiz,
    Serral, Snoeck, 2018); the identity is not verified.
    https://lirias.kuleuven.be/retrieve/640093
17. Not opened: HTTP 403. By the search results a survey of adaptive
    model-driven interface development systems (Akiki, Bandara, Yu);
    the identity is not verified.
    https://oro.open.ac.uk/39809
18. Not opened: HTTP 405. The publisher's copy of [15].
    https://www.degruyterbrill.com/document/doi/10.1524/icom.2011.0026/pdf
19. Not opened: HTTP 403. ISO's own page of ISO/TR 25060:2023.
    https://www.iso.org/standard/83763.html

## Opened and not used

- https://www.scitepress.org/Papers/2017/63827/63827.pdf — the PDF
  of [10], returned to the fetch as unreadable binary; superseded by
  the publisher's HTML [10].
- https://research.dial.uclouvain.be/bitstreams/1b75944b-ba3e-4a99-b22f-06f5c11faf96/download
  — the full text of [15], an encrypted PDF the fetch could not
  read; nothing was taken from it.

## Search record

Queries, in order:

1. model-based user interface development survey adoption
2. W3C Model-Based UI Working Group notes, Cameleon reference
   framework
3. W3C "UI Specification Schema" Community Group
4. IFML, OMG specification 1.0, adoption
5. "model-based user interface development" industrial adoption
   success (the card's disconfirming query)
6. user interface description language review, UsiXML, UIML, MARIA,
   XForms, comparison
7. XForms 2.0 status, W3C Forms Working Group closed, community
   group
8. OASIS UIML technical committee closed, UIML 4.0
9. UsiXML ITEA project results, standardisation, W3C, MARIA member
   submission
10. IFML systematic mapping study, adoption, industry, limitations
11. Meixner, Paternò, Vanderdonckt, "Past, Present, and Future of
    Model-Based User Interface Development", pdf
12. why model-based user interface development was not adopted by
    industry, reasons, criticism of generated interfaces
13. IFML industrial experience report, WebRatio, empirical
    evaluation, practitioners
14. ARINC 661 cockpit display system, interface definition, adoption
15. ISO 9241 parts list, 9241-161, 9241-110, ISO 25065
16. ISO/IEC TR 25060 Common Industry Format, general framework

Pages opened, in order, an opening being a fetch of a page: [1],
[5], [9], [13], [14], the PDF of [10] (unreadable), [10], [3], [6],
[7], [4], [15], [8], the full text of [15] (unreadable), [11], [2]
(fetched twice, counted once), [12]: seventeen openings, fifteen of
them readable. Four further fetches failed with an HTTP error and
opened nothing: [16], [17], [18], [19].

What the disconfirming query found: no page that reports broad
industrial success of model-based interface development. Its result
list held the W3C note [1], a slide deck and a workshop abstract of
proponents, and studies of model-driven engineering at large, none
of the latter opened. The pages opened afterwards agree with the
card's expectation, little adoption with a few fields where it held
(F8, F11), with the reservation that the fields are named by those
who work in them and no independent count was found. The expectation
was not disconfirmed.

Why the run ended: the opening budget. Seventeen openings stand
against the ten to fifteen of the card, two of them spent on PDFs
the fetch could not read. The card's stop rule was not met in full:
the route of the academic surveys has no source read beyond one
abstract, and the route of ISO has a secondary page and a seller's
copy in place of a primary source.
