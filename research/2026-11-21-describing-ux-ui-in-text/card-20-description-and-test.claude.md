---
date: 2026-11-21
project: forge
topic: what automated testing of interfaces learned about describing screens in modular text, and how a built interface is checked against its description
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-20-description-and-test
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 20; no known note named by the card; web sources below
---

# Interface testing defines elements and actions as layered units, the units last at the level of the task, and a build is checked against an approved state, a mock-up or tests made from a text, not against a text itself

<!-- Shape: templates/research.md -->

## In short

The pattern literature and the tools' own documentation agree on the
units and are sobering on the check. For testing, an interface is
described in layers: what the user achieves, the path through the
interface in terms of tasks, and the elements with the technical
steps on them. User paths refer to the middle layer, never to
elements. The element as a unit of its own exists in every pattern
read (a page component object, a named target, a harness that the
maker of a component ships with it, a robot per screen) and it is
small: a name and the way to find and work the thing. It is the layer
built to take a change of the interface in one place; what breaks is
a path written in terms of elements. A unit survives when it is
defined by what the user does or perceives, and breaks when it is
defined by layout, markup or the kind of widget. This is a consensus
of practitioners with little measurement behind it: one family of
controlled experiments found that the layer costs more than it
returns until a suite is about ten times larger, and one industrial
case study is known here only second-hand. The disconfirming queries
did not overturn the expected answer on survival under change, but
bent it three times: the critique of page objects is aimed mostly at
page-sized units that grow and mix duties; one vendor's critique also
calls a definition per element premature where the element serves a
single action; and a controlled experiment of 2025 found scenarios
written in terms of interface elements easier to write and to read,
above all for people who are not software practitioners. The
unexpected thing: nothing opened checks a build against a text
directly. A test bound to a text needs binding code, written by hand
or, in one tool's current documentation, generated and repaired by
agents from a Markdown plan; a picture is compared with an earlier
picture a person approved or, in research on mobile applications,
with the design's mock-up; and a textual template of a page's
structure (roles and names, in order) is the nearest thing to a
description that a machine can hold a build to.

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

**Card 20: The description and the test**

- **Question:** What has automated testing of interfaces learned
  about describing screens in modular text: how do the Page Object
  and Screenplay patterns and executable specifications define the
  elements of a screen and their actions as units of their own that
  user paths refer to, at which level of abstraction do such units
  survive a change of the interface and at which do they break, and
  how is a built interface checked against its description (tests
  bound to the text, comparison of pictures, inspection)?
- **Why it matters:** these are definitions per element kept in
  version control for twenty years, and the build needs a way to
  show that it built what was described.
- **What would answer it:** the pattern literature and the testing
  tools' own documentation.
- **Where to look:** the original descriptions of Page Object and
  Screenplay; specification by example and behaviour-driven
  development for interfaces; testing tools' guidance on the level
  of abstraction; visual regression testing.
- **Disconfirming query:** "page object anti-pattern", "BDD UI tests
  brittle"; expected: units at the level of an element are brittle,
  units at the level of a task last.
- **Stop rule:** nothing new from a differently worded query and
  every route has a primary source; ten to fifteen pages opened.

Known items: none; the card names no known note of the project.

The baseline the note must beat is what a practitioner would say
without looking anything up, which is also what the card expects:
page objects hide locators, scenarios should be declarative, visual
regression compares screenshots, and units at the level of an element
are brittle while units at the level of a task last. The note beats
it only where it says where the boundary of a unit lies, what each
unit carries, which of this is measured and which is claimed, and
what each kind of check in fact compares a build with.

## Key findings

The note was made in two rounds; why, and which queries and openings
belong to which, stands in the Search record. What the second round
added or changed is marked "Second round" in the finding it belongs
to; F10 is new in the second round.

Sources [3], [4], [8], [9], [13], [18], [21], [22] and [23] were read
through a summarising fetch. Every sentence quoted from them was then
checked against the text of the page itself; what is said of them
beyond the quotes rests on the summary and is marked "summarised
fetch" or, for the three research papers, "abstract". The other
sources were read in the text of the page.

**F1. Testing describes an interface in layers, and only the lowest
layer names elements.** [consensus; practitioner claims by the
patterns' authors and the tools' own documentation]

The clearest statement is [5] (section "Three levels of UI test
automation"): a "Business rule/functionality level: what is this
test demonstrating or exercising", a "User interface workflow level:
what does a user have to do to exercise the functionality through
the UI", and a "Technical activity level: what are the technical
steps required to exercise the functionality". The Screenplay pattern
has the same three under other names, and its authors say they took
them from the design of user experience: "we break down the way a
user interacts with an application into goals, tasks and actions"
([3], section "The Screenplay Pattern encourages strong layers of
abstraction"). The executable-specification tools carry the layers in
their formats: a scenario and its step definitions in Cucumber [6]; a
specification, a concept and a step in Gauge, where a concept is a
named group of steps kept in a file of its own that "presents the
summary of a business intent" ([8], section "Concepts"; summarised
fetch). [5] (section "Implementing this in practice") finds the same
layering in four tools of its day. The Page Object pattern gives two
of the layers, the services of a page over its widgets, and [5] says
of it that it "is a good start, but stops short of finishing the
job", the top layer being left to the team. In all of them a user
path is written in the units of the middle layer (tasks, services,
concepts, workflow steps) and reaches an element only through them.

Second round. The robot pattern of native mobile tests [19] and the
Markdown specifications of [24] repeat the split between what is done
and how; nothing in them changes the layers.

**F2. The element is a unit of its own in every pattern read, and a
small one; the patterns disagree on what belongs in it.** [consensus
on the unit, contested on its content; pattern literature, tool
documentation and one project's decision record]

[1] defines the unit: "A page object wraps an HTML page, or fragment,
with an application-specific API" (first paragraph), and says at once
that the unit is not the page: "these objects shouldn't usually be
built for each page, but rather for the significant elements on a
page" (third paragraph; its first note proposes "panel object" as the
better name). [2] carries this on as page component objects that
"represent discrete chunks of the page", nest in one another and may
stand for a component used throughout a site (section "Page Component
Objects": "They are built with components contained in a page."). In
the Page Object pattern the unit carries its actions: its methods are
"the services that the page or component offers" ([2], Summary),
typed by what the user does and not by the widget, so that a text
field takes and returns a string, a check box a boolean, and a button
is a method named after its action ([1], second paragraph). In the
Screenplay pattern the unit carries no action at all: a target
"associates a WebDriver selector with a human-readable label that
appears in the test reports", and "Targets are often stored in small
Page-Object like classes that are responsible for one thing", which
the page gives as knowing how to locate the elements of one component
([3], section "High-level tasks are composed of other lower-level
tasks or actions"). What is done with an element and what is read
from it are units of other kinds: interactions, "the low-level
activities an actor can perform using a given interface", tasks,
"sequences of activities as meaningful steps of a business workflow
in your domain", and questions ([4], section "The five elements of
the Screenplay Pattern"; summarised fetch). On one point the two
agree: what a path expects is kept out of the unit that describes the
element ([1], paragraph on assertions: "I favor having no assertions
in page objects."; [2], section "Assertions in Page Objects": "Page
objects themselves should never make verifications or assertions.").

Second round. Two more forms of the unit were read. A component
harness is the unit kept by whoever makes the component: "A component
harness is a class that allows tests to interact with components the
way an end user does via a supported API", written by "Developers who
maintain some reusable Angular components" for those who use them,
and one library "provides a test harness for each component in the
library" ([18], overview and its table of readers; summarised fetch,
these passages read in the page). In its example the test asks the
harness for the text of a button and makes the assertion itself. On
native mobile the unit is a robot per screen, and it holds more: the
tests say what is done, while the robots handle "how to find the
button view, how to click the button, and how to actually assert the
state" ([19], Context). So four answers to what the unit holds stand
side by side: a name and a locator only (Screenplay); actions and
readings without expectations (Page Object, and the harness as its
example shows it); actions and expectations (robot); and, in the
critique of [24], no unit at all, the locator living in the step that
uses it (F6).

**F3. A unit survives a change of the interface when it is defined by
what the user does or perceives; it breaks when it is defined by
layout, markup or the kind of widget. The element layer is where a
change is meant to land, in one place.** [consensus of practitioner
sources and tool documentation; one industrial measurement known
second-hand, and one experiment on finding elements again]

[5] (sections "Three levels of UI test automation" and "Relatively
inexpensive to maintain") ranks the layers by what each is tied to.
Tests at the technical level "tend to break with even the smallest
change in the UI". Tests at the workflow level were "a bit more
stable", and yet: "When the page workflow changes, or when the
underlying technology changes, such tests break." The business rule
level is not "tied to any particular web site design or activity
flow". And where change falls: "it is the technical level where
changes happen most frequently - layout, not the activity workflow".

[1] gives the test for the boundary of an element unit: "imagine
changing the concrete control - in which case the page object
interface shouldn't change" (second paragraph), and adds that
structure which exists only to lay the interface out is not to show:
"The rule of thumb is to model the structure in the page that makes
sense to the user of the application." (third paragraph). [6] gives
the same test for a sentence of a scenario: "Will this wording need
to change if the implementation does?" (section "Describe
behaviour"). [9] gives it for the way an element is found: "Your DOM
can easily change so having your tests depend on your DOM structure
can lead to failing tests." (section "Prefer user-facing attributes
to XPath or CSS selectors"; summarised fetch), its generator
"prioritizing role, text and test id locators" (section "Generate
locators").

The element layer is not expected to last; it is expected to hold the
change: "if the UI changes, the fix needs only to be applied in one
place" ([2], Overview), and the small classes of targets "tend to
remain unchanged unless the underlying web interface changes" ([3],
section "Page Objects become smaller and more specialized"). The one
measurement met on this point is second-hand: [1] (Further Reading)
reports of an industrial case study of 2013 that a team repairing two
versions of a suite after an upgrade "found the version with page
object took a bit longer for the first test case, but much faster for
the rest"; the study itself could not be read in this run [16].

Second round. The same is said of the two further units: harnesses
"make tests less brittle by insulating themselves against
implementation details of a component, such as its DOM structure"
([18], overview), and with robots "Small UX changes (e.g. polish)
generally only change the robot code" ([19], Context, list of pros).
One measurement bears on the weakest spot of the element layer,
finding an element again. In an experiment on "804 web element pairs
from 48 real-world web applications", letting a language model choose
among the candidates of a method that matches attributes brought the
failures down "from 70 to 39 (out of 804), a 44 percent reduction"
([23], abstract of 3 Oct 2023; the paper not opened). It measures the
finding of elements, not the survival of a description. It supports
the direction of F3 as far as the authors' own account of the older
methods goes: they "compare attributes but don't grasp the context
and meaning of elements and words".

**F4. "Declarative" is relative: every layer is the what of the layer
below. What makes a text brittle is the mixing of several domains in
it, and the interface is a legitimate domain of a text of its own.**
[single source, practitioner claim; not contradicted by the others]

[7] takes a login scenario that names a Name field, a Password field
and a Login button and counts the domains in its words:
authentication, authentication by password, "the domain of UI
widgets" and "the domain of web assets". The scenario breaks when the
way of authenticating changes, when the widget changes and when the
navigation changes; it is "vulnerable to change along a number of
axes" (paragraph after the example). The rule drawn is not "be
declarative" but a count of domains: "The simplest useful scenario
should involve exactly two domains", the problem and the outermost
interface of the solution (section "Unpacking the domain"), since
"Any layer is the what of the layer below, and the how of the layer
above" (section on chunking). For detail of the interface the article
does not say leave it out; it says put it elsewhere: "If you really
care about how the behaviour is implemented, you should probably be
specifying that elsewhere in a more fine-grained story" (last
section).

**F5. The layer of units is paid for first and returns only with size
and reuse.** [emerging; one family of controlled experiments by one
group, and practitioner claims]

[15] (abstract; undated page, the year 2020 only in its address): in
controlled experiments in which test cases were developed with and
without page objects, "the benefits of POs did not compensate for the
extra development effort they require in the limited experimental
setting of our study", while "results indicate that when the test
suite to be developed is at least 10x larger, test development
becomes more efficient with than without POs". The experiments
measure development, not repair after a change. [5] (opening
paragraph) reports of the teams its author worked with: "Almost all
of them have realised six to nine months after starting this effort
that the cost of maintaining UI level tests is higher than the
benefit they bring"; no figures are given. [5] (section "Beware of
programming in text") also names the price of keeping the middle
layer in plain text rather than in code: "there is no automated
refactoring, syntax checking or anything like that".

Second round. A project that chose the robot pattern wrote the same
into its decision: "Tests written with the Robot pattern should be
more maintainable but are expected to need more upfront design and
brain power", and among the cons, "Hard to write generic re-usable
code, as required by the robots" ([19], Consequences and Context).

**F6. What the disconfirming queries found: the expected answer holds
for survival under change and is contradicted on who can write and
read the text; the critique of page objects is aimed mostly at the
page-sized unit, and in one source at the unit per element as well.**
[contested; one controlled laboratory experiment against a
practitioner consensus, and two vendor claims]

"page object anti-pattern". Two of the critiques opened say that a
unit the size of a page grows and mixes duties. [3] (section "Page
Objects become smaller and more specialized"): "They tend to grow,
becoming bigger and harder to maintain as the test suite grows", and
such classes "violate both the Single Responsibility Principle (SRP)
and Open-Closed Principle (OCP)"; its remedy is smaller units per
component and separate units for tasks and questions (F2). [13]
(section "Page objects problems"; summarised fetch; a vendor's claim
on its own blog): "Page objects try to fit multiple cases into a
uniform interface, falling back to conditional logic" and "Page
objects make tests slow because they force the tests to always go
through the application user interface". Its remedy is to go around
the interface, which the author concedes moves "away from the way a
user would use our application" (section "Calling too many actions
too fast"), and the vendor later set a note above the article that
the pattern is "widely and successfully used in the Cypress
ecosystem". [5] adds, as the point of a co-author of the Screenplay
pattern, that "users think about business activities, not page
functionality". [13] is contradicted by [2], which lists the pattern
among encouraged practices, and by the vendor's own note.

Second round; this changes what the first round said, that no
critique reaches the unit per element. Run again, the query returned
the same list, and the page that carries its words as its title was
opened this time. [24] (a tool's blog on its own market; a vendor
claim) goes further than the two above and aims at the definition of
elements itself. Of a page class whose fields are elements annotated
with locators it says: "This pattern, prematurely designs UI elements
for reuse violating the YAGNI principle" (its first section), on the
ground that "elements on a webpage are usually linked to one action";
and of the remedy of [3]: "Breaking Page objects to smaller page
objects still violates SRP" (section "Everything in its right
place?"). Its own remedy is "Group by intent not page(s)": steps
named after what the user wants, each holding the locators it needs,
put in order in a Markdown specification. Its figure, "Not using page
objects in our tests reduced source code by 40%" (section "Less is
better"), is the vendor's count on its own example and no measurement
of maintenance. So no source says that a unit per element is brittle;
one says that it is premature where an element serves one action.
[18] stands against [24] for elements that are shared: there the unit
per component is written once by the component's maker and used by
every test of every application that has the component. That reuse
is what decides between the two is this agent's inference.

"BDD UI tests brittle". [5], [6] and [7] say so of scenarios written
in terms of elements (F3, F4); [12] says so of scenarios run through
the whole application: "These can be slow and brittle because the UI
is often tightly coupled with the rest of the application." (section
"How should the UI be tested?"). Contradicted in part by [14]
(abstract of a doctoral thesis of 2025; the thesis itself not
opened): in a controlled laboratory experiment, people who are not
software practitioners "found scenarios written in user interface
specific domain Gherkin to be significantly easier to document than
scenarios written in business domain Gherkin" and marginally easier
to comprehend; for software practitioners both differences were
marginal. The abstract reports nothing on how such scenarios fare
when the interface changes, so it contradicts the consensus on
writing and reading, not on survival. [6] concedes the same ground:
"Imperative tests communicate details, and in some contexts this
style of test is appropriate." (section "Consider a more declarative
style"). Second round: run again, the query returned the same list,
and nothing further was opened from it.

**F7. A test bound to a text checks the build only through binding
code. In the tools read first that code is written by hand for every
step; one tool's documentation now has agents generate it from a
Markdown plan and repair it when the interface changes. The text is
what stays, and it can exist before the interface does.** [consensus
on the binding by hand, from the tools' documentation and a
practitioner claim; emerging on the generated binding, one vendor's
documentation of its own product with nothing measured]

In Gauge the specification is a file whose "specifications are
written in a syntax similar to Markdown" (section "Specifications
(spec)"). Its steps are list items: "Steps are the executable
components of a specification that are written by using the Markdown
unordered list syntax", and "Every step implementation has an
equivalent code as per the language plugin used while installing
Gauge" (section "Step"); any other sentence "is seen as a comment in
a spec" and is not run (section "How to add comments in a
specification"; all [8], summarised fetch). In Cucumber the details
"are specified in the step definitions (the automation code that
interacts with the system)" ([6], section "Consider a more
declarative style"). [5] (section "Efficient to write") draws the
consequence for a description made before a build: "the business
rule and the workflow level can be written before the UI is actually
there", to serve as acceptance criteria. So a description that a test
is bound to is checked exactly as far as someone wrote the binding;
in these three sources nothing derives the check from the text.

Second round; this changes the last sentence above for one tool. [20]
documents three agents: the "planner explores the app and produces a
Markdown test plan", the "generator transforms the Markdown plan into
the Playwright Test files", and the "healer executes the test suite
and automatically repairs failing tests" (Introduction). The plan is
a Markdown file of scenarios with numbered steps and expected
results, "human-readable but precise enough for test generation"
(section on the planner). The generator "verifies selectors and
assertions live as it performs the scenarios", and the tests are
"aligned one-to-one with specs wherever feasible"; in the page's
example each test names its plan in a comment and repeats the plan's
steps as comments above the code (sections on the generator and on
conventions). Three things on the page limit what this gives a
description written before a build. The documented direction runs
from the build: the planner explores the running application, and a
requirements document is "(optional) A Product Requirement Document
(PRD) for context"; that "Specs can start from scratch" is said in
one clause. The steps of the example plan are written at the level of
elements, such as `Click in the "What needs to be done?" input
field`, the level F3 calls brittle. And the repair follows the build:
the healer "Inspects the current UI to locate equivalent elements or
flows" and "Re-runs the test until it passes or until guardrails stop
the loop", its output being "A passing test, or a skipped test if the
healer believes that functionality is broken" (section on the
healer). Whether a difference between plan and build is a change to
follow or a defect to report is thus left to the agent's judgement.
The page gives no measurement of any of this.

**F8. In the tools of practice a comparison of pictures checks a
build against an earlier build that a person approved, not against a
description; a person's inspection is where its truth comes from.**
[consensus; tool documentation and a practitioner article]

[11] (Introduction): "On first execution, Playwright test will
generate reference screenshots. Subsequent runs will compare against
the reference." The reference is kept in version control ("You should
commit this directory to your version control (e.g. git), and review
any changes to it.", section "Non-image snapshots") and it is bound
to the machine that made it: "Browser rendering can vary based on the
host OS, version, settings, hardware, power source (battery vs. power
adapter), headless mode, and other factors" (warning in the
Introduction), and "Screenshots differ between browsers and platforms
due to different rendering, fonts and more, so you will need
different snapshots for them" (section "Generating screenshots").
[12] (section "Is that all?") gives the general form, approval
testing: "The first time the test is run, the output is checked
manually.", and later runs are compared with the approved output. For
the interface (section "Does approval testing work for UIs?") a
failing visual test means that "manual investigation is required –
because not all failures indicate a defect in the code". What [12]
says in praise of machine learning for visual checks is left out
here: the page itself says the article first appeared on a blog under
an address that names a commercial visual testing product. Second
round: where the other side of the comparison is a design mock-up and
not an earlier build, see F10.

**F9. A textual snapshot of structure stands between the two: a text
per page that lists the elements by role and name, in order and
nesting, and is matched against the built page.** [single source; a
vendor's documentation of its own product]

[10] (Overview): "With Playwright's Snapshot testing you can assert
the accessibility tree of a page against a predefined snapshot
template." The template is YAML, one line per element in the form
`- role "name" [attribute=value]`, nested by indentation, for
instance (section "Lists with items"; the indentation restored here):

```yaml
- list "Main Features":
  - listitem: Feature 1
  - listitem: Feature 2
```

"A template is a constraint, not necessarily a complete serialization
of the accessibility tree." (section "Aria snapshots"): names and
attributes may be left out, the children given may be a subset, a
name may be a regular expression, and "The comparison is
order-sensitive" (section "Snapshot matching"). Templates can live in
files of their own, ending in .aria.yml, and unlike pictures they are
one per page for all browsers: "As snapshots should be the same
across browsers, only one snapshot is saved even if testing with
multiple browsers." (section "Snapshots as separate files"). The page
names the weakness of every stored snapshot: "It can be tempting to
accept changes to snapshots without fully understanding them,
potentially hiding bugs." (section "Snapshot testing"). What the
template does not hold: where an element stands on the screen, how it
looks, and anything outside a web page; [10] documents it for web
pages only.

**F10. Second round, new. Where the description is itself a picture,
a built screen is compared with the design's mock-up directly; this
is research on mobile applications, with one industrial use
claimed.** [emerging; two research papers read in their abstracts,
the evaluations being the authors' own]

[21] (abstract; accepted to a software engineering conference of
2018, by the comment of its record) starts from the practice it means
to replace: "the time-consuming and laborious task of design teams
verifying that each screen of an app was implemented according to
intended design specifications", the mock-up being "a static image
delineating the proper layout and style of GUI widgets that satisfy
requirements". Its approach "uses computer vision techniques to
identify common errors in the implementations of mobile GUIs", and
the authors state that the tool is "currently used by over
one-thousand industrial designers and developers at Huawei" (their
claim, 2018). [22] (abstract of 9 Jun 2025, version 1, no venue on
its record) compares more than looks. It abstracts every screen into
widgets, each of which "is represented by its position, width,
height, and type", aligns the widgets of the mock-up with those of
the build, and checks the transitions that the mock-up specifies on
its labelled widgets by acting on the screen, a vision-language model
inferring the actions. The authors report "94.5% precision and 99.6%
recall in detecting screen inconsistencies" on "80 mobile
applications and 160 design mock-ups", and an industrial case study
with nine confirmed bugs (figures of version 1 of 9 Jun 2025; a
result list pointed to another copy with other figures, not opened).
In both, the other side of the comparison is a mock-up, a picture
with the geometry of its widgets and labels on them, not a text; and
neither abstract speaks of the web or the desktop.

## Unexpected

The card assumes that a built interface is checked against its
description. In the tools of practice two of the three ways the card
names have no description on their other side: a comparison of
pictures compares a build with an earlier build, and what made the
earlier build right was a person looking at it ([11], [12]). The
second round found the other side filled in two ways, neither of them
with the text itself: a design mock-up, compared with the built
screen in research on mobile applications (F10), and test code
generated from a Markdown plan (F7), where the plan in the documented
flow is drawn from the running application. The card is answered as
put in F7 to F10; the lead is that "checked against its description"
may have to be said per kind of content, not for the description as a
whole.

The page definition of the frame, which "names which elements it
holds", has a near twin in testing: the template of F9 [10], a text
per page that names elements by role and accessible name in order and
nesting, kept in version control and matched by a machine. [10] says
such snapshots verify that the structure "remains consistent or meets
defined expectations"; that a template could be written from a
description before the build, rather than recorded from the build, is
this agent's inference and stands nowhere in the page. It covers
which elements a page holds and in what order, not where they stand.

Second round. "Where they stand" has a checkable form in research,
and it is geometry, not words: [22] holds a screen as widgets with
position, width, height and type, an order among them and costs for
replacing, inserting and deleting one, and takes these from a
mock-up. A lead for the cards on previews and on design tools: the
part of a page definition that says where elements stand may be
better given and checked as a picture than as text.

Second round. With an agent that repairs the element layer, the
reckoning of F3 and F5 may shift: the example plan of [20] is written
at the level of elements, the level [14] found the easiest to write
and read and F3 the first to break, and the healer is what [20]
offers against the breaking. Nothing measured was found on whether
that holds, and the same repair can make a test follow a defect (F7).
The reckoning is this agent's inference; the page claims none of it.

Second round. In [18] the definition per component is kept by the
maker of the component and shipped with it, so that it is written
once for all who use the component. A lead for the card on components
in design systems: a definition per element may belong with whoever
keeps the shared element, not with each project that uses it.

The thesis behind [14] built, by its abstract, "a framework that
comprises standardised low level Gherkin scenario steps and the
associated acceptance test functions": a fixed vocabulary of steps on
interface elements, bound to test code once. Read with F7 it is a
lead: where the vocabulary of the element layer is standard, the
binding is written once and not per project. Abstract only; how far
the framework reaches was not read.

The strongest remedy testing has for brittleness is to go around the
interface: [1] notes that patterns which move logic out of the
interface "reduce the need for page objects" (paragraph before the
last), [12] advises testing the interface as a component with the
rest stubbed out, [13] dispatches actions to the application's
internals. That advice lowers the cost of testing and says nothing on
how to describe an interface; it marks how much of the testing
literature this card cannot use.

## Not found

- The first article on the Screenplay pattern [17]: its publisher's
  page answered HTTP 403. [3], a later article by the pattern's four
  authors, stands in for it.
- The industrial case study of 2013 on page objects and repair [16]:
  the address answered with a PDF that the fetch returned as
  unreadable binary. Its figures are not cited; only the sentence of
  [1] about it.
- A measured comparison of how units at the level of an element and
  units at the level of a task survive a change of the interface:
  none in the pages opened in either round. [14] measures writing and
  reading, [15] development effort, [23] the finding of elements; the
  claim of F3 about which layer lasts rests on practitioner sources.
- A check of a built interface against a description in prose that
  goes through neither test code nor a mock-up: none in the pages
  opened in either round. The query aimed at it, not run in the first
  round, ran in the second: it returned general pages on acceptance
  testing and two papers on generating tests from screen mock-ups,
  both PDF files and not opened; a follow-up query led to [21] and
  [22].
- Any measurement of the agents of [20]: none on the page; not
  searched further.
- The talk that introduced the robot pattern [25]: its host did not
  resolve. [19], one project's decision record, stands in for the
  pattern on native mobile.
- The desktop: no primary source opened in either round. [1] says
  only that "the same pattern applies equally well to any UI
  technology" (paragraph after the assertions) and names a desktop
  toolkit. The comparison with a mock-up (F10) was found for mobile
  applications only.
- The book on specification by example: not opened; only its author's
  article [5]. The earliest description of page objects on the wiki
  of the Selenium project: not opened; [1] says of it only that it
  "favors assertion-free page objects".
- Whether the tool behind [8] and [24] is maintained today: not
  checked; [8] is undated.

## Options

The ways the project could act on the findings, as this agent sees
them; the first four are about the units, the fifth about the check.

1. **Three layers, paths refer to tasks.** Definitions of elements;
   tasks in the user's words that name the elements they use; user
   paths composed of tasks. For it: the form all sources converge on
   (F1), and the one in which a change of layout touches the element
   layer alone (F3). Against it: three kinds of units to keep, and
   the cost comes first (F5).
2. **Element definitions and page definitions only**, as the idea
   from practice was heard, with user paths written against pages and
   elements. For it: the fewest kinds of units, and text of this kind
   was the easiest to write and read for people outside software
   (F6, [14]). Against it: this is the two-layer form of which [5]
   says that it stops short, and a path in terms of elements is the
   form F3 and F4 call brittle.
3. **Page-sized definitions without units per element.** For it: the
   cheapest start for a small project (F5), and what [24] argues for
   in tests, the element living where it is used. Against it: an
   element that recurs is described in several places and a change is
   made in each, the situation [2] (Overview) shows for tests without
   page objects; and the page-sized unit is what the other critiques
   of F6 are aimed at.
4. **Units only for what is shared** (second round). A definition of
   its own for an element or component that recurs across pages or
   projects, kept with whoever keeps the shared element ([18]); an
   element that serves one action on one page is described where it
   is used ([24]). For it: the cost of F5 is paid only where reuse
   returns it. Against it: someone has to judge what is shared, and
   an element that starts to recur has to be lifted out later.
5. **What the build returns as proof**, each for a different kind of
   content, none for all: scenarios bound to the tasks by code (F7:
   behaviour; the binding written by hand, or generated from a
   Markdown plan by an agent, whose repair can follow the build; one
   vendor, nothing measured); a template of structure per page (F9:
   which elements, their names and order; web only in [10]; nothing
   on looks or position); approved pictures (F8: looks; one baseline
   per browser and platform; a person approves the first); a
   comparison with a mock-up where one exists (F10: looks and
   geometry; research, mobile only); inspection by a person against
   the description, which F8 and [21] show to be the practice
   everything else starts from.

## Relevance to this project

The recommendation, this agent's own inference from F1 to F10: keep
the idea of a small definition per element, and give it the
boundaries testing found.

- An element definition says what the user can do and see through
  the element and what it is called, in the user's terms (F2, F3). It
  does not say which widget it is, where it stands or how it is
  found. The test to take over from [1]: if the concrete control
  changed, would the definition have to change?
- A definition of its own is for an element that recurs; an element
  that serves one action on one page can be described there (option
  4; F5, F6). Second round.
- A page definition names the elements it holds in the structure that
  makes sense to the user (F3, [1]), in order and nesting. Where they
  stand in the layout is the content that changes most often (F3,
  [5]); it is kept apart from which elements there are, and may be
  better held as a picture (F10).
- User paths refer to tasks and tasks to elements (F1, option 1);
  nothing above the element layer names a widget or a position.
- The words of the interface are in place in this document: it is the
  "more fine-grained story" of [7]. The documents above it stay free
  of them (F4).
- The element layer will change most often, and that is its job, not
  a defect of the description (F3).
- Nothing is promised about an automatic check of the description as
  a whole. The build stage is asked for what option 5 lists, and the
  approval of a first picture stays a human's act (F8). Where an
  agent makes the tests from the text, the text stays the reference:
  a test repaired until it passes shows a change of the interface for
  a human to judge, not a proof (F7). Second round.
- For a project of one person the layer of element units may cost
  more than it returns (F5): it is a layer a project may leave out.

It rests on a consensus of the patterns' authors, practitioners and
tool documentation, on one family of experiments for the cost, on one
experiment for the reading, and in the second round on one project's
decision record, one vendor's documentation of its agents and the
abstracts of three research papers. Its weakest part is that which
layer lasts is claimed and not measured in anything opened here.

It is chosen against three things: page-sized definitions that hold
elements, behaviour and expectations together, the form most
critiques of F6 are aimed at; user paths written in terms of elements
(F3, F4); and a promise that a build is verified against the text
(F7, F8).

Consult when: the unit of the interface description is being decided
(element, component, page); it is asked whether position and layout
belong in the same definition as function; it is decided what a user
path may refer to; the proof the build stage returns is being
defined; screenshots or a mock-up are proposed as the check of a
description; an agent is to make or repair tests from the
description; a small project asks whether it needs element
definitions at all.

## Sources

Sources 1 to 17 are of the first round, 18 to 25 of the second.

1. "Page Object", Martin Fowler; 10 September 2013 (byline).
   https://martinfowler.com/bliki/PageObject.html
   Primary: the description of the pattern under this name, by the
   author who, as the page says, first described it as Window Driver.
   Read in full. Original. The site is its author's own and carries
   his employer, a software consultancy, in its navigation.
2. "Page object models", Selenium project documentation; last
   modified September 16, 2026 (page footer).
   https://www.selenium.dev/documentation/test_practices/encouraged/page_object_models/
   Primary: a tool's own documentation. Read partially: every prose
   section in the text of the page, the code examples not. Original.
3. "Beyond Page Objects: Next Generation Test Automation with
   Serenity and the Screenplay Pattern", John Ferguson Smart, Antony
   Marcano, Andy Palmer, Jan Molak; InfoQ, Mar 15, 2016 (byline).
   https://www.infoq.com/articles/Beyond-Page-Objects-Test-Automation-Serenity-Screenplay/
   Primary for the pattern: its four authors describe it; what they
   claim for its maintainability is their own claim about their own
   pattern and tools. Summarised fetch; the quoted sentences and the
   passages on targets and on the layers read in the text of the
   page. Original, and not the first article on the pattern (see 17).
4. "Screenplay Pattern", Serenity/JS Handbook, Jan Molak; last
   updated Oct 10, 2026 (page footer).
   https://serenity-js.org/handbook/design/screenplay-pattern/
   Primary: the documentation of a tool, kept by a co-author of the
   pattern, whose company the page's copyright line names. Summarised
   fetch; the quoted sentences checked in the text of the page.
   Original.
5. "How to implement UI testing without shooting yourself in the
   foot", Gojko Adzic; Apr 13, 2010 (byline).
   https://gojko.net/2010/04/13/how-to-implement-ui-testing-without-shooting-yourself-in-the-foot-2/
   Primary: the author of the book on specification by example on the
   levels of a test of an interface, from teams he worked with and
   interviewed. Read in full. Original. The site sells its author's
   workshops and books.
6. "Writing better Gherkin", Cucumber documentation, The Cucumber
   Open Source Project; last updated Nov 17, 2026 (page footer).
   https://cucumber.io/docs/bdd/better-gherkin/
   Primary: a tool's own documentation. Read in full. Original.
7. "Whose domain is it anyway?", Dan North, Dan North & Associates;
   31 Jan 2011 (byline).
   https://dannorth.net/blog/whose-domain-is-it-anyway/
   Primary: a practitioner's article on its author's own site, a
   consultancy; its author is commonly credited with naming
   behaviour-driven development (from this agent's memory, not
   verified in this run). Read in full. Original.
8. "Writing specifications", Gauge documentation; undated.
   https://docs.gauge.org/writing-specifications
   Primary: a tool's own documentation of its file format. Summarised
   fetch; the quoted sentences checked in the text of the page.
   Original.
9. "Best Practices", Playwright documentation, Microsoft; undated
   (footer year 2026).
   https://playwright.dev/docs/best-practices
   Primary: a tool's own documentation. Summarised fetch; the quoted
   sentences checked in the text of the page. Original.
10. "Snapshot testing", Playwright documentation, Microsoft; undated
    (footer year 2026).
    https://playwright.dev/docs/aria-snapshots
    Primary: a tool's own documentation. Read in full. Original.
11. "Visual comparisons", Playwright documentation, Microsoft;
    undated (footer year 2026).
    https://playwright.dev/docs/test-snapshots
    Primary: a tool's own documentation. Read in full. Original.
12. "UI Development with BDD and Approval Testing", Seb Rose;
    Overload, 33(188):12-13, August 2025 (byline).
    https://accu.org/journals/overload/33/188/rose/
    Secondary: a practitioner's article in the journal of a
    programmers' association; for approval testing it cites earlier
    descriptions that were not opened. Read in full. A republication,
    reviewed and updated: the page says it first appeared on 8
    February 2023 on a blog under an address that names a commercial
    visual testing product, so its passages on machine learning are
    not used.
13. "Application Actions: Use Them Instead of Page Objects", Gleb
    Bahmutov; Cypress blog, January 3, 2019 (byline).
    https://www.cypress.io/blog/stop-using-page-objects-and-start-using-app-actions
    A vendor's blog on its own tool, used only as the critique the
    disconfirming query returned and marked as a vendor claim; primary
    for that position alone. Summarised fetch; the quoted sentences
    checked in the text of the page. Original.
14. "On the use of user interface specific domain Gherkin in
    behaviour driven development", Abdullah Alshammari; PhD thesis,
    University of Glasgow, 2025; deposited 13 Jun 2025 (repository
    record); the record shows the DOI 10.5525/gla.thesis.85190.
    https://theses.gla.ac.uk/85190/
    Primary: the abstract of the thesis on its repository record.
    Read: the record with the abstract in full; the thesis itself not
    opened. Original.
15. "A family of experiments to assess the impact of page object
    pattern in web test suite development", Maurizio Leotta, Matteo
    Biagiola, Filippo Ricca, Mariano Ceccato, Paolo Tonella; undated
    on the page, no venue shown; the year 2020 stands only in the
    address.
    https://profs.scienze.univr.it/ceccato/papers/2020/icst2020po.html
    Primary: the abstract of the paper on an author's page at a
    university. Read: the page in full, which is the abstract; the
    paper itself not opened. Original.
16. "Improving test suites maintainability with the page object
    pattern", Leotta et al., ICSTW 2013 (title, authors and venue as
    [1] cites them).
    https://sepl.dibris.unige.it/publications/2013-leotta-ICSTW.pdf
    Not opened for content: the address answers, but with a PDF that
    the fetch returned as unreadable binary. Cited for nothing; known
    here only through the sentence of [1].
17. "Page Objects Refactored: SOLID Steps to the Screenplay/Journey
    Pattern" (title as [4] lists it). Not opened: the publisher's
    page answered HTTP 403, and no address is given here for that
    reason. Cited for nothing.
18. "Component harnesses overview", Angular documentation; undated
    (the footer carries a copyright range to 2026).
    https://angular.dev/guide/testing/component-harnesses-overview
    Primary: a framework's own documentation. Summarised fetch; the
    overview and the table of readers read in the text of the page.
    Original.
19. "ADR 2: Robot Pattern in UI Tests", an architecture decision
    record of one native application project whose tests are written
    in Kotlin, shown by a source code index of Mozilla; undated (the
    page carries only the date of its indexing).
    https://searchfox.org/mozilla-mobile/source/firefox-tv/docs/architecture/adr-0002-robot-pattern.md
    Primary for that project's decision and its reasons; not the
    origin of the pattern (see 25). Read in full. Original.
20. "Playwright Test Agents", Playwright documentation, Microsoft;
    undated (it names an editor release of October 9, 2025, so it is
    not older).
    https://playwright.dev/docs/test-agents
    Primary: a tool's own documentation of its own product; what it
    says the agents do is the vendor's description, with no
    measurement. Read in the text of the page, but for its last two
    short sections, which rest on the summarised fetch with the
    quoted sentence checked. Original. Found in the navigation of
    [10] and [11], not by a query.
21. "Automated Reporting of GUI Design Violations for Mobile Apps",
    Kevin Moran, Boyang Li, Carlos Bernal-Cárdenas, Dan Jelf, Denys
    Poshyvanyk; arXiv:1802.04732, submitted 13 Feb 2018, revised 5
    Apr 2018 (arXiv record); the record's comment says it was
    accepted to ICSE'18.
    https://arxiv.org/abs/1802.04732
    Primary: the abstract on the arXiv record; the paper itself not
    opened. Summarised fetch that returned the abstract sentence by
    sentence; the quoted sentences checked in the text of the page.
    Original, the preprint of the conference paper.
22. "GUIPilot: A Consistency-based Mobile GUI Testing Approach for
    Detecting Application-specific Bugs", Ruofan Liu, Xiwen Teoh, Yun
    Lin, Guanjie Chen, Ruofei Ren, Denys Poshyvanyk, Jin Song Dong;
    arXiv:2506.07385, version 1 of 9 Jun 2025 (arXiv record); no
    venue on the record.
    https://arxiv.org/abs/2506.07385
    Primary: the abstract on the arXiv record, read in the text of
    the page; the paper itself not opened. Original.
23. "Improving web element localization by using a large language
    model", Michel Nass, Emil Alegroth, Robert Feldt;
    arXiv:2310.02046, version 1 of 3 Oct 2023 (arXiv record); no
    venue on the record.
    https://arxiv.org/abs/2310.02046
    Primary: the abstract on the arXiv record; the paper itself not
    opened. Summarised fetch that returned the abstract sentence by
    sentence; the quoted sentences checked in the text of the page.
    Original.
24. "The Page Objects anti pattern", Soumya Swaroop; Gauge blog, Jun
    13, 2017 (byline).
    https://gauge.org/2017/06/13/the-page-objects-anti-pattern/
    The blog of a testing tool on its own market, the tool of [8]:
    used only as the critique the disconfirming query returned and
    marked as a vendor claim; primary for that position alone. Read
    in full. Original.
25. The talk that introduced the robot pattern, as [19] lists it
    ("Presentation introducing the pattern"). Not opened: its host
    did not resolve, and no address is given here for that reason.
    Cited for nothing.

## Opened and not used

None, in either round. Every page that opened with readable content
is cited. Four fetches gave no readable page, three in the first
round and one in the second; they are in the Search record.

## Search record

### First round

Queries, in order:

1. Page Object pattern, original description.
2. Screenplay pattern, actors, tasks, interactions, questions,
   original article.
3. Declarative against imperative Gherkin, UI scenarios, brittle.
4. "page object anti-pattern" (the card's disconfirming query).
5. "BDD UI tests brittle" (the card's disconfirming query).
6. Executable specification in Markdown, Gauge, concepts and steps.
7. Visual regression testing, screenshot comparison, aria snapshot.
8. Locator robustness, web test breakage, page object, empirical.
9. The three levels of UI test automation, by title and author.
10. Page object pattern, industrial case study or family of
    experiments.
11. Component test harness, page object per component (differently
    worded).
12. Mobile UI test, robot pattern or screen object (differently
    worded).
13. A built interface checked against a specification text: not run,
    the search budget of the session was spent.

Openings, in order, an opening being a fetch of a page: [1]; [2];
[4]; [6]; [17], answered HTTP 403; [9]; [10]; [11]; [13]; [3]; [8];
[16], a PDF returned as unreadable binary; [14]; [7] at an older
address that returned no content; [7]; [5]; [12]; [15]. Eighteen
fetches, fifteen pages read. Afterwards each of the fifteen pages was
requested once more directly, to confirm that it opens and to check
every quoted sentence against the text of the page; the pages marked
"read in full" were read in that text. Three hosts (cucumber.io,
dannorth.net, cypress.io) answered that request with 403 when the
client named itself as a default Python library and with 200
otherwise.

What the disconfirming queries found in the first round: support for
the expected answer on survival under change ([5], [6], [7]); a
critique of page objects that is about page-sized units and about
going through the interface at all ([3], [13]); one experiment that
contradicts the consensus on writing and reading, not on survival
([14]); and one family of experiments on the cost of the layer
([15]). Details in F5 and F6.

The first round ended by the opening budget. Every route of the card
had a primary source, but the other half of the stop rule was not
met: the two differently worded queries had returned something new
(units per component published with a component library; a robot
pattern for native mobile tests), which stayed unopened, and the last
query could not be run.

### Second round

Why there was one: the first round ended with its last query not run,
the search tool having refused it when the session's search budget
was spent. When searching worked again a second round was asked for:
the query that was not run, the card's disconfirming queries once
more, a differently worded query for the stop rule, and at most eight
further pages.

Queries of the second round, in order:

14. A built interface checked against a specification text, the
    query not run in the first round, in its first wording.
15. "page object anti-pattern", the card's disconfirming query, run
    again.
16. "BDD UI tests brittle", the card's disconfirming query, run
    again.
17. Which layer survives a redesign, user intent and tasks against
    element locators (differently worded).
18. Detection of design violations, an implemented screen compared
    with the design mock-up (a follow-up to 14).
19. Keeping end-to-end tests of an interface maintainable when it
    changes: screen models, user journeys, snapshot and visual
    checks, what breaks (differently worded, the check of the stop
    rule).

Six queries ran; none was refused.

Openings of the second round, in order: [18]; [20]; [23]; [21]; [22];
[25], whose host did not resolve; [24]; [19]. Eight fetches, seven
pages read. Where they came from: [18] and the robot pattern of [19]
and [25] were what the first round's queries 11 and 12 had returned
and left unopened; [20] was found in the navigation of [10] and [11];
[23] came from query 17, [21] and [22] from query 18, [24] from query
15. Afterwards each of the seven pages was requested once more
directly, as in the first round; all seven answered 200 to each of
the three client names tried.

What the disconfirming queries found in the second round: both
returned the lists of the first round. From the first, [24] was
opened, and it changed F6: one critique does reach the unit per
element, as premature where an element serves one action. From the
second nothing further was opened.

How the run ended: by the card's stop rule, with more pages than the
card allows. Query 17 still returned something new, the finding of
elements by their meaning with a language model, which was followed
into [23]. Query 19, the last, returned nothing that the note does
not hold: few journeys, a layer of flows above the models of screens,
the brittleness of snapshots and visual checks; and vendors' pages on
visual checks of single components in isolation, which repeat F8 at
the grain of a component and were not opened, being vendors' blogs on
their own market. Every route of the card has a primary source. The
pages read are twenty-two in the two rounds, above the card's
fifteen by the further pages granted for the second round.
