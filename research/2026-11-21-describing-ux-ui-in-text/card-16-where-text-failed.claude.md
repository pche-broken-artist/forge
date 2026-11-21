---
date: 2026-11-21
project: forge
topic: where describing an interface in text failed, what is proposed in its place and what kept the surviving descriptions true
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-16-where-text-failed
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 16; the known note 2026-10-03-how-a-solution-design-is-built.md; web sources below
---

# Textual specifications of interfaces failed where they were a second copy of the product, and survived where they were narrow, generated or tested

<!-- Shape: templates/research.md -->

## In short

The note was made in two rounds. In the first the search tool refused
every query and fifteen pages were opened by addresses the agent
already knew; in the second eight queries ran, the confirming one
among them, and eight further pages were opened on what they
returned. Together: the heavy written specification of an interface
is recorded as failing by practitioners between 2000 and 2011 for six
reasons (it does not match the finished product, words do not carry
how an interface behaves, agreement on paragraphs is illusory, it
decides too early, adding to it costs nothing, it is slow to write,
seldom read and cannot be tested); its one defender read here does
not deny the drift, blames the process, and freezes his own
specification at code complete. Generation of interfaces from models
is recorded as not accepted, in a research retrospective of 1999 and
a paper of 2017 (unpredictable result, loss of control, a new
language, a low ceiling, hand changes lost at each regeneration); a
W3C working group on it closed with Notes and no standard; writing of
2025 and 2026 draws the same line to specifications written for
coding agents, the newest asking that such a specification be
temporary. The critics propose the prototype as the specification,
the interface built first and the product as its own documentation;
each keeps some text and each presumes a team that talks. What
survived as text is narrow: a description generated from the same
source as the product and judged by a machine, scenarios bound to
tests, pattern guidance that disclaims being normative. The second
round changed two things. The rule that such scenarios name the
business rule and not the screen, a consensus in the first round, is
contested: a doctoral thesis of 2025 finds no academic evidence
behind it and shows that people outside software write scenarios in
the words of the interface more easily, and a survey of 75
practitioners finds that text bound to tests has the maintenance
problems of any test suite. And the confirming query ran: it returned
proposals of new formats and one practitioner's warnings, and no
documented case of a textual specification of a whole interface kept
as the source of truth over years. Unexpected: the sources place the
failure in a second copy that is costly to update, whatever its
medium; the part that broke everywhere is the part that says where
things stand on a screen; and a practitioner of design systems argues
in 2026 that Markdown cannot be the contract, since nothing in it can
be judged invalid by a machine.

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

#### Card 16: Where describing an interface in text failed
- **Question:** Where did textual specifications of interfaces fail
  or get abandoned (heavy specification documents, descriptions that
  drifted from the product, generation from models), which reasons
  are recorded, what do those who argue against describing an
  interface in text propose in its place (the prototype as the
  specification, the code as the source of truth), and what kept true
  the textual descriptions that survive (generation from the product,
  tests bound to the text, a narrow scope)?
- **Why it matters:** the plan assumes text can be the source of
  truth; this card attacks that before a layer rests on it.
- **What would answer it:** critiques, post-mortems and reports of
  experience.
- **Where to look:** the criticism of design up front; living
  documentation and specification by example; reports of experience
  with behaviour-driven development for interfaces; writing on drift
  between design and product. The known note on the solution design
  for what is known of staleness. Search words from card 1: the fate
  of model-driven development beside the warning of 2025 that a
  specification as the only source repeats it ("review fatigue").
- **Disconfirming query:** here the confirming one: "UI specification
  as source of truth long-lived success"; expected: few documented
  cases, most of them generated or tested.
- **Stop rule:** nothing new from a differently worded query and
  every route has a primary source; ten to fifteen pages opened.

What the note must beat. The known note of 2026-10-03 on the solution
design established, for the technical design between requirements and
tasks, that there are two families of design document (the design of
a change, frozen when accepted, and the description of a system,
meant to stay current), that the second is the one whose staleness is
documented, and that a living description is kept alive by holding
only what cannot be read off the thing, by linking and not copying,
and by a check against the thing (its findings 1, 4, 5 and 9). Its
evidence on staleness was practitioners' reports and studies not read
at source, every page was read through a summarising fetch, it has
nothing on the interface, and the parallel with model-driven
development reaches it through another note. This note has to add the
interface: where descriptions of interfaces failed and why, what is
proposed in their place, and what kept the survivors true, each from
a primary source with its quotations checked against the page.

## Key findings

In this note "design" is named by its meaning each time: the design
of the interface (held in a prototype, a mock-up or a design tool),
the technical design, or a design system. Quotations are verbatim but
for typographic apostrophes and quotation marks, which are written
plain; how each page was read stands under Sources. Sources [1] to
[14] are of the first round, [15] to [20] of the second; what the
second round added to a finding is marked "Second round".

**F1. The heavy written specification of an interface is recorded as
failing for six reasons, all of them from practitioners; no measured
study of it was found.** [consensus among the practitioner sources
read that it fails; practitioner claim]

- *It does not match the product that is built.* "These blueprint
  docs usually wind up having almost nothing to do with the finished
  product" (first paragraph of [1]). In 2000 the complaint was
  already common enough to be quoted back by a defender of
  specifications: "specs are useless, because nobody follows them,
  they're always out of date, and they never reflect the product."
  (section "Specs Need To Stay Alive" of [4]). For deliverables of
  user-experience design kept for reference: they "become obsolete
  almost as soon as they are completed" (section "Deliverables For
  Maintenance Don't Make Sense Anymore" of [3]).
- *Words do not carry how an interface behaves.* A specification
  "must accurately represent the behavior of the software" and
  "words and pretty pictures are just too limited in their ability to
  describe this behavior" (list of requirements for a specification
  in [2]). "Unlike paragraphs of text that are open to alternate
  interpretations, interface designs are common ground that everyone
  can agree on." (closing part of [1]).
- *Agreement on text is not agreement.* "A bunch of people agreeing
  on paragraphs of text isn't a true agreement." (heading "Functional
  specs only lead to an illusion of agreement" of [1]). The existence
  of the document works as "a false indicator to management and the
  product team" that all is well (second paragraph of [2]).
- *It decides too early and cannot move.* "You know the least about
  something when you begin to build it."; "Specs don't deal with the
  reality that once you start building something, everything
  changes." (two headings of [1]).
- *Adding to it costs nothing.* "There's no pushback during spec
  phase. There's no cost to writing something down and adding another
  bullet point." (heading "Functional specs lead to feature overload"
  of [1]).
- *It is slow to write, seldom read and cannot be tested.* "most
  specs take too long to write, they are seldom read" and, of a long
  document, "few will read and is impossible to test" (second and
  last paragraphs of [2]); "Waste is defined as anything that is
  ultimately not used in the development of the working product."
  and a designer "spending six weeks creating a design-requirements
  document and pixel-perfect specs" (opening and prototyping sections
  of [3]).

The youngest of these sources is of 2011. The same charges return in
2025 and 2026 against specifications written by agents (F6).

**F2. Whether the failure belongs to the text or to the way it is
kept is contested.** [contested; practitioner claims on both sides]
Spolsky defends exactly the document the others attack: a functional
specification "describes how a product will work entirely from the
user's perspective"; "It specifies screens, menus, dialogs, and so
on." (opening of [4]); not writing one is "the single biggest
unnecessary risk you take in a software project" [5]. He does not
deny the drift; he assigns it to a team that writes the specification
once and hands it over: "Maybe your specs are out of date and don't
reflect the product. My specs are updated frequently." What he names
as keeping it true: updating "as the product is developed and new
decisions are made", one current copy on a server for the team, and
printed copies with revision marks at milestones. And he sets its
end: "The spec is only frozen when the product is code complete"
(all from the section "Specs Need To Stay Alive" of [4]). Contradicted
by [1], for which the form itself is the fault. Neither side offers
more than its own experience. The defended specification is thus the
specification of one build; nothing in [4] or [5] claims it is kept
true after the product ships.

**F3. Those who argue against the text put a prototype, the interface
itself or the finished product in its place, and each of them keeps a
remainder of text.** [consensus among the three critics read;
practitioner claim]

- *The prototype as the specification* (2006): "the majority of the
  product spec should be the high-fidelity prototype, representing
  the functional requirements, the information architecture, the
  interaction design, and the visual design of the user experience";
  the reason given first is that, unlike a paper document, it "can be
  tested" with users before engineering starts. Kept in text beside
  it: release and platform requirements such as reliability,
  performance and scalability, "use cases, describing the most
  important flows through the product", and notes on a wiki, so that
  nobody works from "various random versions of documents floating
  around" [2].
- *The interface first* (undated on the page): "Write a one page
  story about what the app needs to do.", then paper sketches, then
  HTML: "the interface will be the alternative to the functional
  spec" [1].
- *The prototype, then the product* (2011): "The prototype has now
  become your documentation.", and after the build "The final product
  is the documentation." Where the author keeps documentation: for
  "complex business rules", for sites that are mostly content, for a
  designer on several projects at once, and where an outside vendor
  "requires a certain level of documentation in order to produce
  work" [3].

None of the three says how a prototype is kept true to the product
once the product exists; [3] holds that it need not be, since one can
walk the flow in the product. All three assume the prototype is
explained in person: "you're there to answer any questions that come
up" [3].

**F4. A description of an interface kept beside the product drifts
when updating it is a second piece of work; this is recorded for the
pattern libraries and component specifications of design systems,
shown by one project's own list of its specifications, and, for
mock-ups held as images, reported in one study.** [consensus among
the sources read that it happens: practitioner claims [6] [16], a
project's own page [15]; one controlled and industrial study read in
its abstract only [7]]
For the pattern library of a design system (2016): "Once the pattern
library ceases to reflect the current state of the products it
serves, it becomes obsolete."; the cause named is the cost of
updating: "Many systems fall into a state of disrepair because the
effort required to make updates is far too high."; and a delivered
style guide risks ending "in the trash can right alongside all the
PSDs, PDFs and those other static artifacts of the design process"
(sections "What is it we're making again?", "Make it maintainable"
and the opening of [6]). For the design of the interface held as an
image (2018): between a mock-up and the code "developers often
introduce mistakes related to the GUI", "such mistakes are common in
the evolutionary context of rapidly changing apps", and checking each
screen against its design is a "time-consuming and laborious task";
the checking tool the paper presents was by then used by "over
one-thousand industrial designers and developers" at one company
(abstract of [7]; the paper's counts of violations were not read).
The second half matters for the card because the artefact that
drifted there was not text.

Second round. A named case: the developer site of the image editor
GIMP, a desktop application, keeps "a list of specifications for
interaction with the graphical interface, containing interaction
logic, reasoning and rationale", one document per topic, on a page
edited in the project's repository. Eight are listed without a
warning, dated between November 2025 and October 2026; nine further
documents stand under "Documents to Review" with the sentence "They
may be incomplete drafts, outdated, or in need of updates. Please
read them critically." and a reason each, among them "review reason:
likely outdated", "review reason: draft from before finale specs" and
"review reason: very old doc pre-2.4 document" (sic) [15]. Not all
nine are specifications of the interface. The page shows two things
at once: textual specifications of interaction are still written for
a desktop application, per topic and with their reasons, and the
project marks the stale ones and does not claim they are true. For
specifications of components in design systems the cost argument of
[6] returns in 2026: "a contract too costly to maintain will rot. A
rotted contract is worse than no contract at all, because people
trust contracts." (principle 6 of [16]).

**F5. Generating the interface from a model or a high-level
specification did not find acceptance, the reasons are recorded by
researchers of the field, and a standards group on it closed without
a standard.** [consensus between the two sources read on the loss of
control: a research retrospective [8] and a paper of academics with
an industrial partner resting on small experiments and a review of
literature [17]; the closure is the standards body's own notice [9]]
The retrospective of user interface tools by Myers, Hudson and
Pausch (draft of September 1999, "To appear in ACM TOCHI") lists
model-based and automatic techniques among "Promising Approaches That
Have Not Caught On" and gives the reasons in its section 2.3.4:

- "Automatic and model based techniques have suffered from the
  problems of unpredictability. In fact, because heuristics are often
  involved, the connection between specification and final result can
  be quite difficult to understand and control."
- "Programmers must also learn a new language for specifying the
  models, which raises the threshold of use."
- "model based systems have a low ceiling", each placing "significant
  limitations on the kinds of interfaces they can produce".
- "the generated user interfaces were generally not as good as those
  that could be created with conventional programming techniques".

Of the earlier attempt to specify interfaces at a higher level and
hide the detail (section 2.3.1): "this separation has not worked out
well in practice. For every user interface, it is important to
control the low-level pragmatics of how the interactions look and
feel". The same paper expects the need to return with the diversity
of devices [8]. That need was the mission of the W3C working group on
model-based user interfaces, "to develop standards as a basis for
interoperability across authoring tools for context aware user
interfaces"; its home page is headed "[CLOSED]" and says: "This group
has now closed and its specifications have been republished as
Working Group Notes." The page lists no Recommendation, gives no
reason, and its last news item is of 07 January 2014 [9].

Second round. For the model-driven engineering of web applications,
navigation and interface included, a paper of 2017 states that these
approaches, "after 20 years of development, they have attracted
little attention from the Industry due to the mismatch between
technical versus research requirements", on the strength of "small
experiments to apply MDWE in a company in addition to exhaustive
literature review". Its reasons meet those of [8] at the loss of
control: "the derivation process feels like a "magic wand" that
obtains an application from a set of models", engineers avoid the
tools "as they lack control over the system under development", and
what the models do not cover is changed by hand in the generated code
and lost again: "As none of the MDWE tools provide a roundtrip
between the generated code and the models, these "technological"
tweaks have to be adjusted every time the application is derived."
(abstract, introduction, sections 2.1, 2.4 and 2.7 of [17]).

**F6. In 2025 and 2026 the same line is drawn to specifications
written for coding agents, and the newest source asks that such a
specification be temporary; the phrase "review fatigue" was not found
in any page opened.** [emerging; practitioner claims]
Böckeler (15 October 2025), who worked on projects of model-driven
development: "Ultimately, MDD never took off for business
applications, it sits at an awkward abstraction level and just
creates too much overhead and constraints."; language models remove
the fixed language and the code generators at the price of
non-determinism, and "I wonder if spec-as-source, and even
spec-anchoring, might end up with the downsides of both MDD and LLMs:
Inflexibility and non-determinism." (section "Spec-anchored and
spec-as-source: Are we learning from the past?" of [10]). On the
reading of what the tools write: the files were "very verbose and
tedious to review", "I'd rather review code than all these markdown
files", and the tools risk "amplifying existing challenges like
review overload and hallucinations" [10]. The Technology Radar of
November 2025 places spec-driven development in "Assess": some tools
"generate lengthy spec files that are hard to review", and "We may be
relearning a bitter lesson — that handcrafting detailed rules for AI
ultimately doesn't scale."; the one tool it names as keeping the
specification and not the code as the maintained artefact was "still
in private beta as of September 2025" [11]. On 2026-11-21 the page
marks the entry as not on the current edition and carries no later
assessment.

Second round. Eisele (17 August 2026) describes a repository "after
six months of spec-driven agent work", where "you may find a second
system sitting next to the code", and names the fault: "The mistake
is treating a specification as a permanent natural-language copy of
the software." His rule: "A change specification should be temporary
by default."; "But as soon as the change ships, most of it should be
removed.", and what lasts "moves into code, schemas, tests, policies,
and operational signals"; he keeps a small number of decision records
for what has no other place. On first versions written by agents: it
"generates a lot more material to be reviewed and approved" and "This
results in an even higher burden on the human reviewer and makes it
endlessly harder to keep the various documents aligned."; on
exhaustive specifications: "We called this waterfall back in the day,
and the approach still has the same negative side effects today."
[18]. He does not mention model-driven development. None of [10],
[11] and [18] contains the words "review fatigue"; the nearest are
"review overload" [10] and the "burden on the human reviewer" [18].
None of the three speaks of interfaces in particular.

**F7. Text bound to tests through the interface is reported as
abandoned where it named the mechanics of the interface and as stable
one level up, at the business rule; a thesis of 2025 contests the
evidence for that rule, and a survey shows that binding text to tests
does not by itself keep it maintainable.** [contested since the
second round: a practitioner's report across teams and a tool's own
documentation [12] [13] against a doctoral thesis with three case
studies and a controlled experiment [20]; a survey of practitioners
[19]]
Adzic (2010), on teams that automated tests through the interface:
"Almost all of them have realised six to nine months after starting
this effort that the cost of maintaining UI level tests is higher
than the benefit they bring. Many have thrown away the tests at that
point and effectively lost all the effort they put into them." He
separates three levels at which such a test can be written (the
business rule, the workflow of the user through the interface, the
technical activity) and reports what each is tied to: "The business
rule level isn't tied to any particular web site design or activity
flow, so it remains stable and unchanged during most web user
interface changes"; the workflow level breaks when "the page workflow
changes"; the technical level "is tied to the layout of the pages".
His rule: even where the workflow is written in plain text, "put one
level of abstraction above it and describe business rules directly"
[12]. The documentation of Cucumber (updated 17 November 2026) says
the same of scenarios in Gherkin: "Your scenarios should describe the
intended behaviour of the system, not the implementation."; scenarios
that name fields and buttons, "because they are so closely tied to
the mechanics of the current UI, they often require more work to
maintain"; the test it offers: "Will this wording need to change if
the implementation does?"; and scenarios in the other style "read
better as "living documentation"" [13]. By these two accounts the
text that tests have kept true is the text that leaves the interface
out. Neither gives a count.

Second round. Binamungu, Embury and Konstantinou (SANER 2018): "We
surveyed 75 BDD practitioners from 26 countries". The specifications
are text that runs as tests, and still: "When the number of examples
grows, BDD specifications can become costly to maintain and extend.";
they "suffer the same maintenance challenges found in automated test
suites more generally"; in some teams "parts of the system are
effectively frozen"; one respondent: "We decided to not use BDD any
more because it was hard to maintain it." The causes the survey names
are size and duplication, not the level of the wording, and it asks
nothing about interfaces [19]. Alshammari's doctoral thesis
(University of Glasgow, May 2025) takes the rule of [13] head on: of
the advice to write declaratively, "to date there has not been
academic research to provide support for this advice" (chapter 1),
and "without empirical validation, these guidelines rely on hearsay"
(section 7.1). It builds a Gherkin vocabulary in the words of the
interface (buttons, text entry fields) with a fixed library of steps,
applies it in three case studies and compares it with scenarios in
business terms in a laboratory experiment. People who are not
software practitioners found the interface-level scenarios
"significantly easier to document" and, like software practitioners,
"marginally easier to comprehend"; of the comprehension result the
thesis says it has "no statistical significance" (abstract, section
8.4). It names its limits: "the controlled nature of the laboratory
study, the small number of case studies, and the need for broader
industry validation" (section 8.3) [20]. The thesis does not test
what happens to such scenarios when the interface changes, which is
the claim of [12] and [13]. So the two sides do not meet: one reports
from practice, without counts, that text at the level of the
interface breaks under change; the other shows by experiment, without
change, that it is easier to write and no harder to read.

**F8. Four things are seen to keep a textual description true, and
each of them narrows what the text claims.** [emerging; the grouping
is the agent's synthesis over practitioner claims, a standards body's
page and a research retrospective; [16] is by the maker of the
tooling it describes]

- *One source feeds the description and the product.* "The holy
  grail of design systems is an environment where making changes to a
  UI pattern updates both the pattern library and production
  applications simultaneously."; one company is named as having built
  it, through an interface from which both the library and production
  take the patterns. The limit is stated: "sharing CSS and
  presentational JavaScript with production environments is
  relatively easy, while sharing markup is tough" [6]. Here the truth
  is the code and the description a view of it. Second round: for
  specifications of components, Curtis (28 July 2026) regenerates
  them from the design file by a command and asks that the making be
  repeatable: "Generate the spec twice with nothing changed, and your
  diff should be empty". He warns of the copy inside the description
  itself: "Be wary of contracts positioned as a "single source of
  truth" that then encode decisions in multiple locations."; "The
  moment a decision lives in two places, the contract risks
  disagreeing with itself."; and of taking the design file for the
  truth: a definition lifted from it unchanged "is testimony, not a
  contract". His practice is of "the past 18 months" [16].
- *Tests bind the text* (F7, with what F7 says against trusting that
  alone).
- *A machine can judge the text.* Second round: "Reading is review,
  not verification."; of a description of a component in Markdown:
  "A format where nothing is invalid is a format where nothing is
  verifiable."; his own descriptions are typed data under a schema
  (principles 1 and 4 of [16]).
- *The scope is narrow and the claim modest.* The ARIA Authoring
  Practices Guide of the W3C is a library of interface patterns in
  text: "Each pattern describes its purpose, keyboard interaction
  model, accessibility semantics, and is complemented by one or more
  illustrative functional example implementations." It says of
  itself: "The APG does not specify normative requirements and thus
  does not have a conformance model."; its examples are "intended to
  be illustrative, not prescriptive"; "it's objectives do not include
  providing a comprehensive design system or production-ready code"
  (sic); how assistive technologies work with the patterns "is
  assessed by" a separate project [14]. The retrospective [8] names
  the same condition for tools: those that succeeded "helped (just)
  where they were needed", and constraints were accepted for layout
  alone because there they came "in a way that was easier to learn
  and more predictable".

Beside these stand two regimes that do not keep a description true
but end it: the discipline of F2 (one owner updating one copy until
code complete) [4], and its counterpart of 2026, in which the
description of a change is discarded after the change and its lasting
facts move into code, schemas and tests [18].

**F9. The sources use "behaviour" for two things, and they agree once
the two are told apart.** [contested on the surface; the resolution
is the agent's reading]
[2] holds that words cannot describe the behaviour of software and
wants a prototype; [12] and [13] hold that behaviour is exactly what
the text should describe. In [2] the word means how the interface
responds and feels in use; in [12] and [13] it means the rule the
system keeps ("Free delivery is offered to customers who order two or
more books" is the example of [12]). [3] draws the same line from the
critics' side: documentation "may make sense for complex business
rules, it doesn't make sense for design". Read together: across these
sources text held for rules and failed for look, feel and layout.
Second round: [20] qualifies the reading on one side. The level at
which text is reported as stable (the rule, by [12] and [13]) and the
level at which people outside software write it most easily (the
words of the interface, by [20]) are not the same level.

**F10. The confirming query, run in the second round, returned no
documented case of a textual specification of a whole interface kept
as the source of truth of a product over years.** [single source:
this run; absence in one result list and twenty-three pages is weak
evidence]
Its result list held definitions of the term, proposals of 2025 and
2026 for new formats of specification, articles that name a design
tool as the source of truth, and one practitioner's essay with
warnings, the only one opened from it [16]. The nearest cases each
fall short of the query in one respect. The guide of [14] is a living
text and disclaims being normative or complete; the page opened gives
no date of origin. The specification of [4] is frozen at code
complete. The tool of [11] that keeps the specification as the
maintained artefact was in private beta in September 2025 and no
record of use over time was read. The list of [15] belongs to a named
desktop application and holds specifications per topic, current ones
beside ones marked as possibly outdated; the page does not say how
long any of them has held. The contracts of [16] are eighteen months
old, cover components and not screens, and are generated and
validated, not written by hand. What was expected (few cases, most of
them generated or tested) is not contradicted: no case of a whole
interface was found, and the partial ones are narrow, generated or
marked.

## Unexpected

The card asks where text failed; the sources say that what fails is a
second copy that is costly to update, in whatever medium. A mock-up
held as an image diverges from the built interface often enough to
have a checking tool built for it [7]; a pattern library fails when
"the effort required to make updates is far too high" [6]; and the
description that stays true in [6] and [16] is one that is not a copy
at all. If this holds, moving from text to a design tool or a
prototype does not remove the problem the card attacks, and staying
with text does not cause it.

The critics' own exceptions describe the build stage of the frame.
[3] keeps documentation where an outside vendor has little contact
with the designers and needs it "in order to produce work"; [2] keeps
flows and non-functional requirements in text; all three critics
assume someone present to explain the prototype. A coding agent, or a
developer who receives documents and nothing else, is that exception
and not the rule the critics wrote for. This is the agent's
inference, not a statement of any source.

The reasons recorded in 1999 for the failure of generated interfaces
read as a description of a language model at the build stage: "the
connection between specification and final result can be quite
difficult to understand and control" [8], which [10] names
non-determinism and [17] a "magic wand". The remedy recorded there
was not a better specification language but a smaller, predictable
scope.

The four targets of the frame (web, mobile web, native mobile,
desktop) are the motive [8] expected to bring model-based techniques
back, and the mission of the group that closed with Notes [9]. One
description for several kinds of device is the promise on which the
abandoned standard was founded.

The complaint about reading is the same in 2006, 2025 and 2026 for
opposite causes: then the specification was "seldom read" because it
was slow to write and long [2]; now because an agent writes more of
it than a person will review [10] [11] [18].

Second round. The frame keeps its documents in Markdown; [16] argues
that, for the description of a component, Markdown cannot be the
contract: "Reading a markdown file answers none of that", the
questions being whether the description is validly built and
precisely implemented. The card assumes the choice is between text
and something else; this source puts the line inside text, between
prose a person reviews and typed data a machine can reject. Its
author makes and sells the tooling he describes, and his practice is
eighteen months old.

Second round. The card assumes that the description is the thing to
be kept true. [18] says that for work with coding agents this is the
mistake: the written description should be of the next change and
leave when the change ships. The frame's cycle that "runs again when
the interface changes" could be read either way, as a standing
description revised or as a new description of each change.

Second round. The thesis [20] rests on the idea that the interface is
the vocabulary all parties share, whatever their business terms. For
a frame in which a human tunes a proposed description, this is a lead
on wording: the level a person outside software finds easiest to
write is the one the practitioners of F7 report as the least stable.

## Not found

- In the first round, any result of a search: the tool refused every
  query. The second round's queries stand in the Search record. No
  lateral reading of the publishers was done beyond their own pages
  and the result lists.
- A documented long-lived textual source of truth of a whole
  interface (F10).
- Where the phrase "review fatigue" comes from. It is on none of
  [10], [11] and [18]. The query for it returned one result whose
  summary by the search engine carries the phrase, a company's
  engineering newsletter on replacing its design review with Markdown
  specifications; it was not opened, the eight openings of the round
  going to the card's routes, so the origin stays unconfirmed.
- A post-mortem of a named product or organisation that abandoned a
  textual specification of its interface. The nearest is the list of
  [15]. A case study on managing specifications of user interfaces in
  distributed development was returned by the first query and could
  not be opened, the host refusing the request; nothing is cited from
  it.
- A measured study of how long a textual description of an interface
  stays true, or of one form against another under change. [20]
  measures writing and reading, [19] the maintenance of text bound to
  tests in general, [7] the checking of mock-ups, read in its
  abstract only.
- A study that measures the drift of the documentation of a design
  system. The result list of that query held practitioners' and
  vendors' blog posts only; none was opened.
- The books on specification by example and on living documentation;
  not opened.
- Why the W3C group closed. The page gives no reason [9]. A
  retrospective of model-based interface development of 2011,
  returned by the third query and possibly more favourable to the
  field, could not be opened at its publisher, the server refusing
  the request; nothing is cited from it.
- The published version of [8]; the draft was read and not compared
  with it. The publisher's version of [19]; a copy of the accepted
  paper was read.
- Anything specific to native mobile. For the desktop there is [15]
  alone.
- A source in which the critic of the functional specification later
  describes interfaces in a deliberately rough, partly worded form.
  The agent recalls such writing from the publisher of [1] and did
  not open it; nothing is cited from it.

## Options

**A. Text as the single source of truth of the whole interface,
layout included.** The plan as the card states it. *For:* one medium
down the whole chain, read and written by an agent, versioned and
compared like the documents above it. *Against:* it is the form for
which every failure of F1, F4, F5 and F7 is recorded; nothing read
keeps the part about layout true by hand; the human would judge
paragraphs, which is where F1 places the illusion of agreement; a
permanent copy of the product in natural language is what [18] calls
the mistake.

**B. Text as the source of truth of a named, narrow part, the rest
shown and not described.** In text: what each element and each screen
is for, the rules it keeps, its states, what it cites from the
documents above, and the reasons. Look and position: carried by a
preview made from the description or by the built interface, and
judged there. *For:* it is the side on which text held in F8 and F9,
and the question of [13] gives a test for each sentence. *Against:*
two media to keep in step; the line between a rule and a layout has
to be drawn and will be argued case by case; the evidence for the
line is practice and not study (F7); the preview needs a maker, which
other cards ask about.

**C. The prototype as the specification, text as its annotation and
remainder.** The form of [2] and [3]. *For:* the critics agree on it;
it can be tried with users before anything is built. *Against:* it
leaves the chain of documents; it presumes a team in conversation
(F3), and the build stage of the frame is the critics' own exception;
a prototype has no items to cite; nothing read says how it stays true
after the build.

**D. Text as the specification of one build, frozen or discarded when
built; the current state is read off the product.** The regime of [4]
and of [18] and, in the known note's terms, the design of a change.
After a build, what stands is generated from the product or checked
against it (F8), and a change to the interface is a new description
of that change. *For:* it claims least; it has a defender who
practised it and, since the second round, an advocate for work with
agents. *Against:* the next cycle needs a current description to
start from, which must then come from the product, and generation
from the product is recorded as easy for styles and hard for
structure [6].

**E. The checkable part as typed data, prose only for purpose and
reasons.** The form of [16], found in the second round: what a
machine can judge (which elements, which properties and states, what
refers to what) is held as data under a schema and validated; the
prose says what cannot be typed. *For:* it is the one form read here
in which a description is rejected when wrong and not merely
reviewed; it removes the copy inside the document. *Against:* a
schema has to be designed and kept; the source is the maker of such
tooling, with eighteen months of practice and components only; part
of the description stops being prose a person composes.

B, D and E can be held together: B says what the text covers, E in
what form its checkable part stands, D what it is after the build.

## Relevance to this project

The recommendation is not to rest the layer on the sentence "the text
is the source of truth of the interface" as it stands, and to decide
first what the text is the source of truth of. It rests on
practitioner claims of 2000 to 2026, a research retrospective of
1999, a paper of 2017, a survey of 2018, a thesis of 2025 and a
standards body's pages; it is chosen against option A, the plan as
assumed, and against option C taken whole. The points below are the
agent's own inferences from the findings.

1. **Narrow the claim (option B).** The text is the source of truth
   for what an element or a screen is for, the rules it keeps and the
   reasons; the test for a sentence is the one of [13], whether the
   wording would have to change if the realisation did. Since the
   second round this rule stands as practice and not as a measured
   result (F7), and the wording a person outside software writes most
   easily is the wording of the interface [20]; the layer may need
   both levels and should say which one binds.
2. **Let position and look be seen, not agreed in paragraphs.** The
   frame already has the human see the proposal. F1 says agreement on
   text about an interface is the illusion; the seeing is then the
   place of judgement, and a description of where things stand is
   either the input of a preview or provisional.
3. **Decide the regime after the first build before any template
   (option D or a living description).** No source read shows a
   description of an interface kept current by hand. A living
   description needs one of the mechanisms of F8, and the known
   note's three protections apply unchanged; the newest source read
   argues for the other regime outright [18].
4. **Hold the volume to what a person will read.** "Seldom read"
   (2006) and "hard to review" (2025) are the same failure; a proposal
   of an agent that exceeds the reader repeats it, and [18] names the
   first version written by an agent as the risk.
5. **The idea heard from practice, tested against this card.** A
   small definition per element that carries its function is on the
   side that survived: it is the shape of a pattern in [14] (purpose,
   interaction, semantics, with an example beside it) and of a
   specification per topic in [15]. A page definition that names
   which elements a page holds is structure and may hold. The clause
   "and where they stand" is the level recorded as breaking: tied to
   layout in [12], the hardest to share in [6], the "low-level
   pragmatics" a higher description failed to isolate in [8]. The
   idea is therefore not refuted; its last clause is the part to
   generate, to check or to leave to the preview; and, by [16], a
   definition in Markdown alone can be reviewed and not verified, so
   whatever of it is to be checked needs a form a machine can judge
   (option E).
6. **Do not count on tests alone.** Binding the text to tests is one
   of the mechanisms of F8 and not a guarantee: at size it has the
   maintenance problems of any test suite [19].

What would still change this: a documented long-lived case, which the
confirming query did not return, and a study of text at the level of
the interface under change, which neither side of F7 has.

Consult when: deciding what the interface layer's text claims to be
(source of truth, specification of a build, or record); deciding what
an element or a page definition may contain and what it leaves to a
preview; choosing between prose and typed data for the part of a
definition that is to be checked; designing the check that keeps a
description true after the first build; someone proposes that the
specification be the only thing edited; deciding whether tests are
bound to the description and at which level of wording; judging an
argument that a prototype or a design tool would not drift.

## Sources

How the pages were read. Each page was first opened through a fetch
tool that returns a small model's extraction of the page (a
summarised fetch). Each cited page was then requested once more
directly, every quotation of this note was matched word for word
against the page's text, and the passages named below were read
directly in that text. "Checked" below means that second reading.
[8], [17], [19] and [20] are PDFs the fetch tool could not decode;
their text was extracted from the files the fetch returned and read
directly in the parts named. [1] to [14] were opened in the first
round, [15] to [20] in the second.

1. There's Nothing Functional about a Functional Spec, chapter 59 of
   Getting Real, 37signals (Basecamp). Undated on the page (a
   copyright line 1999-2026 only).
   https://basecamp.com/gettingreal/11.1-theres-nothing-functional-about-afunctional-spec
   Primary. Read in full, the whole chapter directly. Original.
2. Revisiting the Product Spec, Marty Cagan, Silicon Valley Product
   Group. October 12, 2006 (byline).
   https://www.svpg.com/revisiting-the-product-spec/
   Primary. Summarised fetch for the whole; checked: the second
   paragraph, the list of requirements, the paragraph on the
   prototype and the closing paragraph. Original.
3. Lean UX – Getting Out Of The Deliverables Business, Jeff Gothelf,
   Smashing Magazine. Mar 7, 2011 (byline).
   https://www.smashingmagazine.com/2011/03/lean-ux-getting-out-of-the-deliverables-business/
   Primary. Summarised fetch for the whole; checked: the end of the
   section on prototyping and the section "Deliverables For
   Maintenance Don't Make Sense Anymore"; the other quotations
   matched. Original.
4. Painless Functional Specifications – Part 2: What's a Spec?, Joel
   Spolsky, Joel on Software. October 3, 2000 (byline; the page also
   shows an update of 2016).
   https://www.joelonsoftware.com/2000/10/03/painless-functional-specifications-part-2-whats-a-spec/
   Primary. Summarised fetch for the whole; checked: the definitions
   at the opening and the section "Specs Need To Stay Alive" in full.
   Original.
5. Painless Functional Specifications – Part 1: Why Bother?, Joel
   Spolsky, Joel on Software. October 2, 2000 (byline).
   https://www.joelonsoftware.com/2000/10/02/painless-functional-specifications-part-1-why-bother/
   Primary. Summarised fetch; one quotation, checked with its
   paragraph. Original.
6. Atomic Design, chapter 5, Maintaining Design Systems, Brad Frost.
   Undated but for the copyright line of 2016.
   https://atomicdesign.bradfrost.com/chapter-5/
   Primary (a practitioner's book, online at its author's site).
   Summarised fetch for the whole; checked: the opening, the passage
   on the obsolete pattern library, the passage on disrepair, the
   opening of "In search of the holy grail" and the sentence on
   sharing markup. Original.
7. Automated Reporting of GUI Design Violations for Mobile Apps,
   Kevin Moran, Boyang Li, Carlos Bernal-Cárdenas, Dan Jelf, Denys
   Poshyvanyk. arXiv 1802.04732, submitted 13 Feb 2018, revised 5 Apr
   2018 (the arXiv record); accepted to ICSE'18 per its comments.
   https://arxiv.org/abs/1802.04732
   Primary. Partially: the abstract, in full and directly; the paper
   itself not opened. Original (the preprint's record).
8. Past, Present and Future of User Interface Software Tools, Brad
   Myers, Scott E. Hudson, Randy Pausch, Carnegie Mellon University.
   Draft 10, September 15, 1999 (title page), "To appear in ACM
   TOCHI" (running head).
   https://www.cs.cmu.edu/~amulet/papers/futureofhci.pdf
   Primary. Partially: sections 2.1 and 2.3 (2.3.1 to 2.3.4) in full
   and directly; the rest not read. The authors' draft, not the
   published article, with which it was not compared.
9. Model-Based User Interfaces (MBUI) Working Group, home page, W3C.
   Undated; the last news item is of 07 January 2014.
   https://www.w3.org/2011/mbui/
   Primary. Read directly from the top to the list of news. Original.
10. Understanding Spec-Driven-Development: Kiro, spec-kit, and Tessl,
    Birgitta Böckeler, martinfowler.com. 15 October 2025 (byline).
    https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html
    Primary (a practitioner's review of three tools). Summarised
    fetch for the whole; checked: the section on the past in full,
    the passage on reviewing markdown and the sentence of the
    conclusions; the page searched for "review fatigue", absent.
    Original.
11. Spec-driven development, Technology Radar, Thoughtworks. Published
    Nov 05, 2025 (the page), ring "Assess".
    https://www.thoughtworks.com/radar/techniques/spec-driven-development
    Primary (a consultancy's assessment, not the tools' vendor). The
    entry's text read in full and directly. Original.
12. How to implement UI testing without shooting yourself in the
    foot, Gojko Adzic, gojko.net. Apr 13, 2010 (byline).
    https://gojko.net/2010/04/13/how-to-implement-ui-testing-without-shooting-yourself-in-the-foot-2/
    Primary. Summarised fetch for the whole; checked: the opening,
    the section on the three levels, the section on the cost of
    maintenance and the closing list. Original.
13. Writing better Gherkin, Cucumber documentation. Last updated on
    Nov 17, 2026 (the page).
    https://cucumber.io/docs/bdd/better-gherkin/
    Primary (a tool's own documentation). Summarised fetch for the
    whole; checked: the section "Describe behaviour" and the opening
    of "Consider a more declarative style". Original.
14. Introduction, ARIA Authoring Practices Guide (APG), W3C Web
    Accessibility Initiative. Undated (a copyright line of 2026
    only).
    https://www.w3.org/WAI/ARIA/apg/about/introduction/
    Primary. Summarised fetch for the whole; checked: the end of
    "Purpose of the APG", the sections "APG is Not a Normative
    Standard", "Exercise Caution If Deviating from APG Patterns" and
    "APG is not a UI Design System", and the row "Patterns" of the
    table. Original.
15. UX Team Specifications, GIMP Developer website, the GIMP project.
    "Last updated on November 17, 2025" (the page; entries on it
    carry dates up to Oct 21, 2026).
    https://developer.gimp.org/core/specifications/
    Primary (a project's own list of its specifications). Summarised
    fetch, then the whole list read directly; the listed documents
    themselves not opened. Original.
16. Component Contracts and Schemas, Nathan Curtis, his newsletter.
    Jul 28, 2026 (byline).
    https://nathanacurtis.substack.com/p/component-contracts-and-schemas
    Primary (a practitioner's essay; its author makes the tooling it
    describes and uses it for clients, by his own account).
    Summarised fetch for the whole; checked: the opening, the
    definition of the contract and the passages under principles 2,
    4, 5 and 6. Original.
17. Challenges for the Adoption of Model-Driven Web Engineering
    Approaches in Industry, Esteban Robles Luna, F. J.
    Domínguez-Mayo, José Matías Rivero, J. A. García-García, J. M.
    Sánchez-Begines, M. J. Escalona, G. Rossi. Proceedings of WEBIST
    2017, pages 415-421 (as printed on the paper).
    https://www.scitepress.org/Papers/2017/63827/63827.pdf
    Primary. Partially: the abstract, the introduction, the headings
    of section 2 and passages of 2.1, 2.2, 2.4, 2.7 and 2.8, directly;
    the rest not read. Original (the publisher's copy).
18. When AI Writes the Code, Specifications Need an Exit Strategy,
    Markus Eisele, O'Reilly Radar. August 17, 2026 (byline).
    https://www.oreilly.com/radar/when-ai-writes-the-code-specifications-need-an-exit-strategy/
    Primary (a practitioner's essay). Summarised fetch for the whole;
    checked: the opening, the start of "Code is the fact", the
    passage on waterfall and on first versions written by agents, and
    the five steps of the lighter model. The page says the article is
    extended and rewritten by its author from an earlier piece in his
    own newsletter; that earlier piece was not opened.
19. Maintaining Behaviour Driven Development Specifications:
    Challenges and Opportunities, Leonard Peter Binamungu, Suzanne M.
    Embury, Nikolaos Konstantinou, University of Manchester. SANER
    2018 (as printed on the first page).
    https://lepebina.github.io/maintaining.pdf
    Primary. Partially: the abstract, the introduction and the
    passages on maintenance challenges and on duplication, directly;
    the rest not read. A copy: the accepted paper on a personal site,
    by its address the first author's; the publisher's version not
    opened.
20. On the use of user interface specific domain Gherkin in behaviour
    driven development, Abdullah Alshammari. PhD thesis, School of
    Computing Science, University of Glasgow, May 2025 (title page).
    https://theses.gla.ac.uk/85190/2/2025AlshammariPhD.pdf
    Primary. Partially: the abstract, the passages on the best
    practice and its evidence in chapters 1, 2 and 5, section 7.1 on
    the research questions and chapter 8, directly; chapters 3, 4 and
    6 not read. Original (the university's repository).

## Opened and not used

- Getting Real, table of contents, 37signals (Basecamp),
  https://basecamp.com/gettingreal : opened in the first round only
  to find the address of [1], a first guess at which had returned
  "not found"; nothing is cited from it.
- The problem with UI specs, an archived blog post of 2007 on
  Microsoft Learn,
  https://learn.microsoft.com/en-us/archive/blogs/shanemo/the-problem-with-ui-specs
  : opened in the second round for its title; the post is a few lines
  pointing to a video interview and says nothing on the question in
  text.
- How Uber Built an Agentic System to Automate Design Specs in
  Minutes, Uber's engineering blog, March 11, 2026: opened and read
  in the second round and left out. Its point, that specifications of
  components written by hand drift and are therefore generated from
  the design file, is carried by [16]; and its address answered only
  requests that name HTML in their Accept header and refused the
  plain requests of script clients, so it is not given here, every
  address in this note having to open for a check.

## Search record

**First round.** Queries, in order; none was performed, each call
being refused because the session's search budget was spent:

1. UI specification document failed, abandoned, out of date, critique.
2. Spec-driven development 2025, the warning of model-driven
   development, "review fatigue", specification as source of truth.
3. Model-based user interface development, why it failed, not adopted
   by industry.
4. The confirming query of the card, sent after the pages were read:
   "UI specification" "source of truth" long-lived success.

Since no result list existed, the pages were chosen from addresses
the agent knew before the run, one or more per route of the card.
This selects for well-known, older, English writing on the web and
against what a search of 2024 to 2026 would have returned.

Pages opened in the first round, in order (fifteen; a sixteenth call,
a first guess at the address of [1], returned "not found" and opened
nothing): [2], [10], [11], [9], the table of contents of Getting
Real, [8], [6], [5], [13], [1], [4], [12], [7], [14], [3]. That round
ended on the opening budget, with the first half of the card's stop
rule untested for want of a search.

**Second round.** Why there was one: the first round ran without any
search, so the card's queries, the confirming one among them, had not
been run; once the search tool worked again the round was ordered,
with an allowance of eight further pages. Queries run, in order
(eight, all performed):

1. UI specification document failed, abandoned, out of date, critique.
2. Spec-driven development 2025, the warning of model-driven
   development, "review fatigue", specification as source of truth.
3. Model-based user interface development, why it failed, not adopted
   by industry.
4. The confirming query: "UI specification" "source of truth"
   long-lived success.
5. Behaviour-driven development, user interface scenarios,
   maintenance, empirical study, practitioners' challenges.
6. Drift between design and implemented product, design system
   documentation out of sync, study.
7. "review fatigue", spec-driven development, Markdown
   specifications, AI agents.
8. The differently worded query for the stop rule: why written
   interface descriptions go stale, prototype instead of spec, code
   as source of truth, lessons learned.

Pages opened in the second round, in order (eight): the archived post
of 2007, the engineering blog post of 2026 (both under Opened and not
used), [18], [16], [19], [20], [15], [17]. Two further calls opened
nothing: the retrospective of 2011 at its publisher and the case
study of the first query at a document-sharing site, both refused by
the server. The cited pages of both rounds were requested once more
each to check the quotations; no further page was opened. Every
address in this note answered the default requests of common script
clients at the end of the second round; the hosts of [1], [2], [13]
and [16] refuse a request that carries the default User-Agent of
Python's standard library and answer other clients.

What the disconfirming query found (here the confirming one, query 4
of the second round): no documented long-lived success. Its result
list held definitions, proposals of 2025 and 2026 for new formats,
articles naming a design tool as the source of truth and one essay
with warnings [16]; F10 says what the nearest cases lack.

What the differently worded query found: the same themes as the
queries before it (a specification goes stale unless something
regenerates or checks it; code against specification as the source of
truth), from practitioners' posts of 2025 and 2026, and as its first
result the page already returned by query 7 and opened as [18].
Nothing of a new kind.

Why the run ended: the second round's allowance of eight pages. The
card's stop rule now holds in both halves: the differently worded
query brought nothing new, and every route has a primary source
(heavy specifications [1] to [5] and [15]; drift [6], [7], [15],
[16]; models [8], [9], [17]; what is proposed instead [1] to [3] and
[18]; what kept the survivors true [12] to [14], [16], [19], [20]).
Its count of pages is exceeded: twenty-three opened over the two
rounds against the card's ten to fifteen, the second round having
been ordered with its own allowance.
