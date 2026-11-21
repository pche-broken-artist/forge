---
date: 2026-11-21
project: forge
topic: what a description of an interface owes every user (accessibility, wording, language versions)
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-13-every-user
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 13; no known note named by the card; web sources below
---

# A description of an interface owes every user its names, order, keyboard, contrast, wording and languages, decided before the build

<!-- Shape: templates/research.md -->

## In short

The standards state what must be true of the built interface, not what
a description written before the build must contain; no source opened
prescribes the content of such a description. The nearest authority is
the W3C's draft mapping of accessibility tasks to roles, which gives
about three fifths of its 266 tasks to UX design, visual design and
content authoring as primary owner [2][3]. With the success criteria
behind them [1] and the per-component pattern of the authoring
practices [4], they say what is decided at design time: for a kind of
element its role, states and keyboard behaviour; for each use of it
its name in context, its heading level and its texts, including the
texts no sighted user sees [19][20]; for a page its title, its order
of focus, its headings and regions; for the whole application
contrast, target size and the look of focus. Wording and language
stand inside the accessibility standard itself, not beside it [1].
Public-administration guidance specifies interface text by general
rules, a cited style guide and wording rules bound to the component
that shows the text [9][10][11][23]. The W3C defines
internationalisation as a step of design, gives a short checklist for
it and warns that short strings grow most in translation
[12][13][14]; a single text with a variable or a number is specified
whole, with its variants and a note for the translator, and a stable
standard exists for writing it [21][22]. Existing templates carry all
this in five shapes: stamps and tables laid over a frame in a design
tool, the pattern page, the component page of a design system, tables
or files of tasks and acceptance criteria, and a data declaration
under a schema [3][4][5][10][11][15][16][17][18][19]. Two schools
disagree on the wording: acceptance criteria that state an outcome and
refuse to name the solution [16][17], and declarations that name the
role, the state and the key [4][18][19].

How sure: what each route says rests on primary sources, all but one
read through a summarising fetch. That specifying early prevents
rework rests on one vendor's own audit, published without method [6].
The disconfirming query, run in both rounds in five wordings, found
practitioners' critiques that annotation kits fail on complex
components [8], the kit's own publisher conceding limits [20], and no
measurement either way, as the card expected. The unexpected thing: a
public library already keeps accessibility acceptance criteria as one
Markdown file per component, for the web and for native mobile [15],
which is the frame's idea in use on this card's ground. The note was
made in two rounds, because the session's search budget ended after
six queries in the first; the Search record says which queries and
pages belong to which.

In this note "design" means the design of the interface, the work done
before the build; "design system" is written in full where the
component library of an organisation is meant.

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

#### Card 13: What the description owes every user
- **Question:** What must a description of an interface carry so that accessibility, the wording in the interface and language versions are designed and not repaired: which accessibility properties are specified at design time (names, roles, states, focus order, keyboard, contrast, target sizes), how are the texts of the interface specified (content design, terminology), how is internationalisation prepared, and how do existing specification templates carry these?
- **Why it matters:** left out of the description they return as rework after the build, and accessibility is a legal duty in many markets.
- **What would answer it:** the standards themselves and their authors' guidance.
- **Where to look:** the web accessibility guidelines and the authoring practices for rich components; public accessibility annotation kits; content design guides of public administrations; the W3C's internationalisation guidance.
- **Disconfirming query:** "accessibility annotations do not work", "shift-left accessibility evidence"; expected: thin evidence either way.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

The card names no known note of the project.

The baseline the note must beat is the answer anyone gives unasked:
follow the accessibility guidelines, write alternative texts, check the
contrast, keep a style guide and take the strings out of the code. That
answer names duties of the finished product. The note has to say which
of them a description must already carry before the build, on whose
authority, at which level of the description each one belongs (an
element, a page, the whole application, a text), in what shape existing
templates carry them, and how well the claim "designed, not repaired"
is evidenced.

## Key findings

Every page but one was read through a summarising fetch: a small model
reads the page and returns what it was asked for. The quotes below are
the fragments it returned on a request for exact words, at most about
125 characters each, omissions marked with "…"; none was checked
against the raw page. Every finding below rests on such a fetch; the
one exception is [19], which came back as the page's own text.

F12 to F15 are of the second round. F4, F6, F7 and F11 were extended
by it; nothing of the first round was withdrawn.

**F1. The accessibility standard states outcomes of the built
interface, one or more for each property the card lists, and it states
nothing about what a design document must contain.** [consensus;
standard] The Web Content Accessibility Guidelines 2.2, a W3C
Recommendation dated 12 December 2024 as printed at its head, are
written as success criteria testable on content [1]. The pairing of
the card's properties with criteria in the table is this note's own;
the wording is the standard's.

| Property in the card | Success criterion (level) | Fragment as returned |
|---|---|---|
| names | 4.1.2 Name, Role, Value (A); 2.5.3 Label in Name (A) | "… the name and role can be programmatically determined …"; "the name contains the text that is presented visually." |
| roles, structure | 4.1.2 (A); 1.3.1 Info and Relationships (A) | "Information, structure, and relationships conveyed through presentation can be programmatically determined" |
| states and their changes | 4.1.2 (A), by its title, the clause on states not among the fragments returned; 4.1.3 Status Messages (AA) | "… status messages can be programmatically determined through role or properties …" |
| focus order | 2.4.3 Focus Order (A) | "focusable components receive focus in an order that preserves meaning and operability." |
| keyboard | 2.1.1 Keyboard (A); 2.4.7 Focus Visible (AA) | "All functionality of the content is operable through a keyboard interface"; "Any keyboard operable user interface has a mode of operation where the keyboard focus indicator is visible." |
| contrast | 1.4.3 Contrast (Minimum) (AA); 1.4.11 Non-text Contrast (AA) | "The visual presentation of text and images of text has a contrast ratio of at least 4.5:1, except for the following:"; "The visual presentation of the following have a contrast ratio of at least 3:1 against adjacent color(s):" |
| target sizes | 2.5.8 Target Size (Minimum) (AA) | "The size of the target for pointer inputs is at least 24 by 24 CSS pixels, except when:" |
| wording | 2.4.6 Headings and Labels (AA); 3.3.2 Labels or Instructions (A); 3.3.1 Error Identification (A); 3.3.3 Error Suggestion (AA); 3.2.4 Consistent Identification (AA) | "Headings and labels describe topic or purpose."; "Labels or instructions are provided when content requires user input."; "… the item that is in error is identified and the error is described to the user in text."; "Components that have the same functionality within a set of web pages are identified consistently." |
| language | 3.1.1 Language of Page (A); 3.1.2 Language of Parts (AA) | "The default human language of each web page can be programmatically determined." |

The last two rows matter for the card: the wording of labels, headings
and errors and the language of a page are success criteria of the
accessibility standard, so the card's three subjects overlap in the
standard itself [1].

**F2. The W3C's own draft mapping gives most accessibility tasks to
design and content roles; it is the nearest thing to an authoritative
list of what is decided at design time, and it is guidance, not a
requirement.** [single source, a draft; guidance of the standard's
publisher] The Accessibility Roles and Responsibilities Mapping is
titled "[Draft]" and marked "Updated: 28 October 2026"; it says of
itself "ARRM helps you assign responsibilities for digital
accessibility to appropriate roles early in projects." [2] and "This
resource does not set requirements to meet WCAG." [3]. Its task tables
have the columns "ID / Status", "WCAG SC", "Task", "Primary Ownership",
"Secondary Ownership", "Contributor", in ten sections (Images and
Graphs, Semantic Structure, Input Modalities, Form Interactions, CSS
and Presentation, Navigation, Data Tables, Animation and Movement,
Static Content, Dynamic Interactions) [3]; primary means "accountable
for an accessibility task" [2]. The page states no totals. Two tallies
made by the summarising fetch, which differ by one row and were not
checked by hand, give of 266 task rows 96 or 97 to UX design, 29 or 30
to visual design, 42 to content authoring, 97 to front-end development
and one to business analysis [3]; by this note's arithmetic 168 rows,
about 63%, have a primary owner who works before the build. Examples,
with the mapping's own IDs [3]:

| Owner (primary) | ID | Criterion | Task as worded |
|---|---|---|---|
| Content Authoring | INP-021 | 2.5.3 (A) | "Text or images of text that is usually included in a user interface control is part of its accessible name." |
| Content Authoring | NAV-028 | 3.2.4 (AA) | "The accessible name of user interface components used across the site or application are defined consistently." |
| Content Authoring | NAV-018 | 2.4.4 (A) | "Link text and alternate text for images, when used as links, describe the destination or purpose of the link." |
| Content Authoring | SEM-022 | 2.4.6 (AA) | "Heading text meaningfully describes the content's topic or purpose." |
| Content Authoring | SCT-019 | 3.1.1 (A) | "The language definition of the document uses the correct value for language and locale." |
| UX Design | NAV-014 | 2.4.3 (A) | "A logical and predictable focus order is defined for complex interactions." |
| UX Design | FRM-023 | 3.3.1 (A) | "Inline error messages are displayed next to their related form controls." |
| UX Design | FRM-024 | 3.3.1 (A) | "Error messages are grouped as a list at the top of the form." |
| UX Design | INP-014 | 2.1.4 (A) | "Single-key keyboard shortcuts can be disabled or remapped, unless they are only active on keyboard focus." |
| Visual Design | CSS-011 | 1.4.3 (AA) | "Regular-sized text is sufficiently contrasted against its background, with a luminosity ratio of at least 4.5:1." |
| Visual Design | CSS-028 | 2.5.8 (AA) | "A minimum height and width of 24 CSS pixels is provided for each interactive target that is not an inline link or control." |
| Visual Design | INP-017 | 2.4.7 (AA) | "Every element that receives keyboard focus is designed to display a visible focus indicator." |

**F3. For a rich component the authoring practices give the shape of a
definition of its own: what it is, its keyboard interaction, and its
roles, states and properties.** [consensus; guidance of the standard's
publisher] The combobox pattern of the ARIA Authoring Practices Guide,
the pattern behind a search field with suggestions, has the sections
"About This Pattern", "Examples", "Keyboard Interaction" and "WAI-ARIA
Roles, States, and Properties" [4]. It defines the element in a
sentence ("A combobox is an input widget that has an associated
popup."), states keyboard behaviour key by key ("Escape: Dismisses the
popup if it is visible."; "Tab: The combobox is in the page Tab
sequence.") and lists what the element exposes ("The element that
serves as an input and displays the combobox value has role combobox.";
"When the combobox popup is not visible, the element with role combobox
has aria-expanded set to false.") [4]. The keyboard section splits by
the kind of popup (listbox, grid, tree, dialog) [4]; this note infers
that a description of such an element must at least name the pattern
and the kind of popup, because the keyboard behaviour follows from that
choice.

**F4. Public annotation kits carry accessibility as stamps by kind of
element, laid over a frame in a design tool, with checklists beside
them; they give a vocabulary of what to state, and one of them a small
table per element, but no textual format of their own.** [emerging;
two vendors' documentation of their own products] GitHub describes its
kit as "a Figma library of stamps (annotations) that you can drop into
your designs" [6]; the repository says it "is a fork of the CVS Health
Inclusive Design team’s" Web Accessibility Annotation Kit and is
"licensed under the terms of the CC-BY 4.0 license" [5]. Its tutorials
name the kinds of annotation: Basic Notes, Button, Flow Lines, Form
element, Heading, Landmark, Link, List, Mobile Annotations, Media,
Metadata, Ordering, Primer components, System Feedback, Table and User
Interactions; beside them stand checklists for the designer, for
engineering and for mobile, and "The components in this library
support web as well as mobile (iOS and Android) platforms." [5] The
publisher adds "It's not about replacing conversations." [6] By this
note's reading the kinds line up with F1: Heading, Landmark, List and
Table with structure, Ordering with focus order, Button, Link and Form
element with names and roles, Media with alternative texts, System
Feedback with status messages.

Second round: a platform vendor's training unit on design
specifications, dated 14 February 2025, teaches the same matters under
the headings Focus order, Name, role, and state, Shortcut keys,
Headings, Landmarks, Alerts, error message, live region, Focus
management and Alternative text, with the "A11y Focus Order Plugin and
Fluent Accessibility Design Toolkit" [19]. It asks the designer to
"Indicate the sequence in which interactive elements should receive
focus when navigating with the tab key.", to state focus management
("when modal dialogs or menus are opened or closed then focus lands
back to component from where it was triggered") and to list shortcut
keys that are not standard [19]. Its examples include a desktop chat
application and application shortcuts, and its pictured specification
is a table of numbered elements with a name, a role and a state each,
described on the page as "Element #4: Name – Login, Role- Button,
State – Disabled." [19] Two kits of two publishers thus agree on what
is stated; the agreement is of practice, not of a standard.

**F5. The one figure in favour of specifying accessibility before the
build is a vendor's own audit data, published without sample or
method.** [vendor claim; internal audit] GitHub's post of 18 November
2025 says of its own audits that "nearly half of accessibility audit
issues (48%) could have been prevented if design intent had been better
documented upfront" [6]; the post gives no sample size and no method.
A survey of 110 mobile developers in 43 countries, listed for the
research track of the 48th IEEE/ACM International Conference on
Software Engineering, reports that developers "typically perform
compliance testing" "late in the development process" [7]: evidence
that accessibility is handled late in practice, not evidence that
handling it early works. Only the abstract of [7] was read. The
second round's three queries on evidence added no figure with a
method; the earlier post of the same publisher [20] contains none.

**F6. The disconfirming query found opinion against annotation kits,
not measurement, and the objection bites on complex components.**
[contested; practitioner claim] An accessibility practitioner's essay
of 13 November 2023 accepts kits for "situations where you need to
describe relatively straightforward interactions" and argues that "a
limited vocabulary will lead to an approximate description of a
complicated topic", that developers "will probably interpret the
annotations literally", that design tools "cannot programmatically
communicate reliable, detailed accessibility-related information" to
the developer's tools, and that "If misunderstood or misused,
accessibility annotation kits are poised to create more harm than good"
[8]. It offers the author's observation ("I see this output all the
time.") and no data [8]. The conflict stands: [6] says nearly half of
audited issues were preventable by documenting intent in annotations,
[8] says annotations can do harm where the component is complex;
neither publishes a measurement. A second critique returned by the
search in both rounds, an article in a design publication titled "Why
UX annotations are a poor band-aid for web accessibility", did not
open (refused by its host in the second round).

Second round: the publisher of the kit states limits of its own. Its
post of 9 May 2025 (updated 24 November 2025) calls it a common
misconception that accessible components make an accessible design:
"Access barriers can still slip through the cracks and make it into
production.", and "The accessibility of any component isn't binary."
[20] The literal wording of the card's disconfirming query returned
the same two critiques, talks, and posts of other vendors on their own
kits; no study of whether annotations are followed.

**F7. The texts of an interface are specified in three layers: general
rules for interface writing, a style guide that is cited and not
repeated, and wording rules bound to the component that shows the
text.** [consensus across the administrations opened; public guidance]
The GOV.UK Service Manual's page on writing for user interfaces
(published 10 October 2017, last updated 16 April 2018) asks for
"using the same language as your users", says "Headings should
describe the purpose of the text that follows", "make the purpose of
the link clear from the link text alone.", "Headings and input field
labels are sentence case, but not punctuated.", "only add help text if
user research shows that you need it." and sends the writer on:
"Follow the GOV.UK style guide on how to write times and dates,
spelling, punctuation, acronyms and other conventions." [9] The GOV.UK
Design System binds wording to a component: for an error message
"Describe what has happened and tell them how to fix it.", the same
message next to the field and in the error summary, instructions for
an empty field ("Enter your name"), and templates of messages kept
with the components they belong to; the page says such messages "have
been tested with all types of users in live services, including tax
credits" [10]. The U.S. Web Design System does the same for its search
component: "Always include the word “search” inside the `<button>`
element for screen readers." and "Use a label even if it’s visually
hidden." [11] Terminology appears in these sources only as the users'
own words [9], the cited style guide [9] and the consistent naming of
F1 and F2 [1][3].

Second round: a UK department's accessibility manual lists what its
content designer considers, by heading: Page title, Page URL, Write in
plain English, Unique headings, Alternative text for non-text content,
Captions and transcripts, Consistent content, Link text, Error
messages, Heading hierarchy, Obscure sensitive information [23]. It
says "Titles should describe the purpose and content of the page.",
"Every page should have a single H1." and "The content should be
consistent across the service.", names success criterion 3.3.3 for
error messages, and has the content designer work with a front-end
developer and a tester on page titles and error messages [23]. It adds
the title of a page to what a description owes, and it confirms the
layers above; it names no stage of a project at which the texts are
written.

**F8. A component has texts that are never shown, and they are part of
its wording and of its language versions.** [consensus across the two
design systems opened; public guidance] The GOV.UK error message
"includes a hidden ‘Error:’ before the error message", and "If your
error message is written in another language, you can change the prefix
as needed."; the Welsh example uses "Gwall:" [10]. The U.S. search
component keeps the word "search" in the button for screen readers
where only an icon shows, and its Spanish variants carry "Buscar" as
label, button text and alternative text [11]. This is the accessible
name of F1 seen from the side of content: a description that lists
only the visible texts leaves these out, in every language.

**F9. The W3C defines internationalisation as a step of design, and
its checklist for the web is short and concrete.** [consensus;
guidance of the W3C's internationalisation work] "Internationalization
is the design and development of a product, application or document
content that enables easy localization for target audiences that vary
in culture, region, or language."; it entails "Designing and developing
in a way that removes barriers to localization or international
deployment." and "Separating localizable elements from source code or
content"; and "ideally, internationalization occurs as a fundamental
step in the design and development process" "rather than as an
afterthought that can often involve awkward and expensive
re-engineering." [12] Localization, by the same page, may touch
"Numeric, date and time formats", "Collation and sorting", "Symbols,
icons and colors" and "Address and contact information formats (postal
codes, phone numbers, name ordering)" [12]. The quick tips that bear
on a description of an interface [13]:

| Tip | Text as returned |
|---|---|
| Language | "Declare the language of documents and indicate internal language changes." |
| Images, animations & examples | "Check for translatability and inappropriate cultural bias." |
| Forms | "Use UTF-8 on both form and server. Support local formats of names/addresses, times/dates, etc." |
| Text authoring | "Use simple, concise text. Use care when composing sentences from multiple strings." |
| Navigation | "On each page include clearly visible navigation to localized pages or sites, using the target language." |
| Right-to-left text | "For HTML, add dir="rtl" to the html tag. Only re-use it to change the base direction." |

**F10. Translated interface text grows, short strings most, and the
guidance answers with a flexible layout, not with a size to design
to.** [consensus on the direction; the figures single source and
undated] The W3C's article says text translated from English or
Chinese "will typically be longer in the translation than the
original" and reproduces averages it attributes to "IBM in their
Guidelines to design global solutions", no date in the text fetched
[14]:

| No. of characters in English source | Average expansion |
|---|---|
| Up to 10 | 200–300% |
| 11–20 | 180–200% |
| 21–30 | 160–180% |
| 31–50 | 140–160% |
| 51–70 | 151–170% |
| Over 70 | 130% |

Its advice: "In general, the more flexibly you can design your layout,
the better." and "Allow text to reflow and avoid small fixed-width
containers or tight squeezes where possible."; it warns of long
compound nouns that do not wrap, of scripts with "much taller
characters than Latin text" and of abbreviating to fit [14]. The U.S.
Web Design System gives a different figure in one sentence: "Romance
languages are about 20% longer than English, so account for text swell
on multilingual websites." [11] The two disagree on the size and are
both cited; [14]'s table suggests why, since the growth depends on the
length of the string, and by this note's inference the texts of an
interface (labels, buttons, headings) fall in its upper rows.

**F11. Existing templates carry these matters in five shapes, and
language versions appear in them only as a variant of a component, a
single criterion and a remark on growing text.** [emerging; this
note's reading across the sources opened, each a primary source for
its own template] The first round found four shapes; the second added
the fifth and filled the fourth.

| Shape | Where it lives | What it carries | Seen in |
|---|---|---|---|
| annotation stamps, tables and checklists | on a frame in a design tool | by kind of element: names, roles, states, headings, regions, order, shortcuts, feedback; mobile separately | [5][6][19] |
| pattern page | text, one page per kind of component | definition, keyboard interaction key by key, roles, states and properties | [4] |
| component page of a design system | text and examples, one page per component | when to use, usability guidance with wording rules, accessibility guidance, language variants, test status against the standard, research | [10][11] |
| task table and acceptance criteria | a table with IDs, a list of "must" sentences, scenarios, or one Markdown file per component | a task or criterion per row, worded as an outcome, with the success criterion or the owner | [3][15][16][17] |
| data declaration under a schema | a data file per component | role, interaction purposes, focus, keyboard, criteria that apply, announcements of states, in a vocabulary of no platform | [18] |

The U.S. search page shows the third shape whole: headings "When to
use the search component", "Usability guidance", "Accessibility
guidance", six previews of which three are Spanish, and an
"Accessibility test status" with the columns "Total tests", "Passed",
"Passed with exceptions", "Conditional", "Failed" and the sentence
"The USWDS team did 22 tests based on WCAG 2.1 AA success criteria."
[11] The fourth shape in Markdown is a public repository whose
documentation lies in
`public/content/documentation/<section>/<category>/<filename>.md`,
with the sections `native`, `web` and `how-to-test`, licensed
Apache-2.0 [15]; only its front page was read, not a criterion. One
source contradicts the third shape as the carrier: the essay of F6
recommends to "Eschew referencing web design system documentation as a
primary reference for accessibility" [8]. Where a language version
shows in these templates: the Spanish variants and the Welsh prefix of
F8 [10][11], one acceptance criterion ("The translation navigation
links must identify the language of the link for correct screen reader
pronunciation") [16], and the remark that an announcement in the data
declaration is "a template hint, not a final user-facing string" [18].

**F12. (Second round.) What a reusable element carries once and what
each use of it must state are different things, and the name is of the
second kind.** [emerging; two vendors' documentation of their own
practice] GitHub's post says "Arranging a series of accessible
components on a page does not automatically create an accurate and
informative heading hierarchy."; for its accordion "All of this is
built into the component," while each use must still state the
optional title and "The heading level of each item within the
accordion."; alternative text, visually hidden text and whether a
button submits data are likewise stated per use [20]. It calls the
stamps that ask for exactly these "Preset annotations" ("Because the
prompts for specific component details are pre-set in the annotation,
we call them Preset annotations."), which "only work if you're also
using the design system they're made for." [20] The training unit of
F4 draws the same line from the other side: "For the library
components, "Name" will be same as per the design and same will be
announced by the screen reader.", whereas "For custom components we
need to do everything, selecting correct control type, review all the
flows, set relevant properties, shortcuts."; and a name that repeats
on a screen is overridden per use: "When we have multiple components
with the same visual name than we should override the visual name."
[19] The data declaration of F14 fits: the fetch found in it no field
for a name [18]. This note's inference for the idea under test: the
definition of an element can carry its role or pattern, its states and
its keys once; the page that uses it must carry its name in that
place, its heading level, its alternative and hidden texts and its
place in the order.

**F13. (Second round.) Acceptance criteria are the textual carrier in
use at two public bodies: written before development, kept per
component, worded as outcomes and told not to name the solution.**
[consensus across the two public bodies opened; their own guidance,
one page marked by its publisher as possibly out of date] The
developer documentation of GOV.UK's publishing components, last
updated 9 May 2022 and carrying its publisher's warning that it "has
not been updated for a while now", defines them: "Accessibility
acceptance criteria are a list of criteria that a user interface must
meet to be considered accessible." and "They are a record of
accessibility decisions." [16] Its reason is the card's own: "By
drafting accessibility acceptance criteria upfront we are forced to
think about accessibility from the start." [16] Its rules: "Identify
where there is a high risk of introducing an accessibility barrier and
include criteria that prevent them.", "Do the hard work to extract
rules specific to what you're building and link back to the guidelines
to give context." and "Good acceptance criteria describe an outcome
rather than the solution." [16] A public broadcaster's team guide sets
the time and the form: "Write accessibility acceptance criteria where
relevant, for new components and iterations of existing components
before the development phase", after an accessibility design review
and with the documented visual and screen-reader experience in hand
("If something is missing, ask UX for all the required documentation
before proceeding to the next step."), the risks listed by "a business
analyst, designer and accessibility champion", each criterion a
scenario ("Given I use a screen reader / When navigating to an ordered
list / Then it should be announced as a list") under the rules "Don't
specify a solution" and "Your aim isn't to reproduce guidelines." [17]
The conflict is with F3, F4 and F14: there the description names the
role, the state and the key; here it is told to state what the user
must be able to do and to leave the means open. Both are primary
sources for a practice; neither is measured against the other.

**F14. (Second round.) A draft specification of a design system
declares a component's accessibility as data, in a vocabulary that
belongs to no platform, and leaves the translation to each platform.**
[single source, a draft; a vendor's documentation of its own
specification] The accessibility chapter of Adobe's Spectrum Design
Data Specification, version `1.0.0-draft`, undated, says "A
component's accessibility declaration expresses intent" and does so
"without encoding platform-specific APIs" [18]. The declaration is an
optional object with the fields `role` (from a canonical vocabulary),
`intents` (the purposes of interaction the component supports),
`focusable`, `keyboardIntents` and `wcag` (the success criteria that
apply, each with number and level); a state may carry `announce`,
`communicates` and `blocksInteraction` [18]. The role "is not a direct
ARIA attribute. Platform adapters perform the translation"; rule words
bind the data ("`criterion` MUST be a valid WCAG 2.x criterion
number") [18]. Its example declares a button with role `button`,
intent `trigger`, keyboard intent `activate`, the criteria 4.1.2 and
1.4.3, and the states disabled and loading with their announcements
[18]. For a description that goes to the web, native mobile and the
desktop this is the one template found that separates what is meant
from how one platform says it; it is a draft of one vendor, and
whether anything is built from it was not read.

**F15. (Second round.) A single text is specified whole, with its
variables named, its variants for number stated and a note for the
translator; a stable standard exists for writing such messages.**
[consensus; W3C guidance and a Unicode standard] The W3C's article on
composite messages opens with "Designers must be very careful about
how they split up and reuse text on-screen", because "the linguistic
differences between languages can lead to real headaches for
localizers" [22]. Its recommendations: "implement sentence-like
messages such that the text and substrings can be easily repositioned
in any order", "using format strings for output in such a way that
each variable is uniquely identified", for numbers "it is better to
always express messages containing numbers like this as a
topic-comment arrangement" (a label and its value in place of a
sentence), and "Provide information to the translator, where needed,
to clarify what a substring represents" [22]. Unicode Technical
Standard #35, Part 9: MessageFormat, CLDR Version 49, dated 2026-10-21
at its head, says of itself "This is a stable document and may be used
as reference material or cited as a normative reference by other
specifications." [21] It defines a message as "the complete template
for a specific message formatting request.", a placeholder as "an
expression or markup that appears inside of a pattern and which will
be replaced during the formatting", and a matcher that "allows runtime
selection of the pattern to use for formatting."; its example states
both variants of one message [21]:

```
.input {$count :number}
.match $count
one {{You have {$count} notification.}}
*   {{You have {$count} notifications.}}
```

Selection by number follows the plural rules of the locale ("If the
`select` option value is `plural`, the rules applied to selection
SHOULD be the CLDR plural rule data of type `cardinal`."), "grammatical
matching (such as plurals or genders)" is a stated goal, and values
set into a text are by default isolated against the mixing of writing
directions [21]. The standard names as a non-goal to "Make the syntax
intuitive enough for non-technical translators to hand-edit." and
assumes "that most translators will work with MessageFormat by means
of GUI tooling, CAT workbenches etc." [21]; this note infers that the
syntax is the build's notation and that a description owes the
substance behind it: the whole sentence, the names of its variables,
the cases by number, the context.

## Unexpected

**The card's three subjects are one in the standard.** The card treats
accessibility, wording and language versions as three things a
description owes. The accessibility standard holds criteria for the
wording of headings, labels and errors and for the language of a page
and of its parts [1], and the W3C's mapping gives those tasks to the
content author [3]. A split of the description into an accessibility
part and a content part would cut through items that are the same
item.

**The card assumes that properties are specified; two public bodies
say a criterion should not name the solution.** (Second round.) The
card asks which accessibility properties are specified at design time
and lists names, roles and states. The acceptance criteria of F13 are
told to "describe an outcome rather than the solution" [16] and
"Don't specify a solution" [17]. The question is answered above as
put; the find says that "what the description carries" has two
answers in practice, a declared property and a required outcome, and
that a chain which already has user stories with acceptance criteria
has a place for the second kind outside the description of the
interface. The last clause is this note's inference.

**A ready checklist with stable IDs and owners exists and is being
maintained.** The mapping of F2 was updated on 28 October 2026, has an
ID per task and names the success criterion and the owner [2][3]. It
is a draft and says it sets no requirements; as a list an agent could
walk when it proposes a description, and a list a description could
cite by ID, it is closer to the framework's own way of working than
the standard is. That use is this note's speculation, not a practice
found.

**The frame's idea is already practised on this card's ground.** A
public repository keeps accessibility material as one Markdown file
per component, for the web and for native mobile, with separate files
on how to test [15]. The frame asks to test, not assume, that every
element has a small Markdown definition of its own; here is one
instance of it, for acceptance criteria. What a file contains was not
read, so this is a lead for the cards on components and on testing.
The second round adds the limit of the idea from two vendors' own
words (F12): the definition of an element cannot hold what differs at
every use.

**For native targets practitioners do not start from the web
guidelines.** The survey of F5 reports that mobile developers "often
rely on platform-specific guidelines" [7]. The card's list of
properties is worded in the web's terms (roles, CSS pixels); the frame
names native mobile and the desktop as targets. The draft of F14 is
the one source found that words a component's accessibility for no
platform [18]. A lead for the card on platforms; [7] abstract only.

**The objection to annotations points at the pattern, not at silence.**
The essay of F6 does not conclude that accessibility cannot be
specified before the build; it asks for "Carrying intent all the way
from design, to development, to the browser", for knowledge of the
common interaction patterns and for tests with assistive technology
[8]. Read with F3, the weak point is a description of a complex
element made of loose labels; naming the pattern is the stronger form.
The second half of that sentence is this note's inference.

**A package of an agentic framework lists an accessibility checklist
in Markdown among its templates for UX.** (Second round.) Seen as a
title in a result list only; not opened, nothing is known of its
content, and no address is given here. A lead for the card on
descriptions written for an agent that builds.

## Not found

- No controlled or independent study of whether accessibility specified
  before the build lowers defects or rework. Looked for with five
  disconfirming or evidence-seeking queries over both rounds; they
  returned vendors' posts and fact sheets on their own market (not
  opened, excluded by kind), an internal blog of a platform vendor
  with a cost multiple and no study behind it (not opened), university
  pages without figures, and the essay [8].
- No study of whether developers, or coding agents, follow
  accessibility annotations or a textual accessibility specification.
  The second round's query for empirical work on the handoff returned
  an interview study of accessibility experts in large companies and a
  thesis on one organisation, neither on annotations (neither opened).
- No standard or guidance of a standard's author that says what a
  design specification must contain for accessibility. The standard
  states outcomes [1]; the mapping "does not set requirements" [3].
- Who writes the texts of an interface and at which point of the
  process: found only in part. For acceptance criteria the time is
  "before the development phase" and the people are named [17]; for
  the texts themselves the content designer's list was found [23] and
  no stage [9][23].
- Nothing on terminology as a thing of its own (a glossary of the
  interface's terms, kept and cited) beyond the users' own words, the
  cited style guide and consistent naming [1][3][9][23].
- On the level of the single string the first round had one line
  [13]; the second found F15. Still not found: guidance on
  grammatical gender beyond its mention as a goal [21], and where in
  the standard a note for the translator is kept (not in the parts of
  [21] that were read; its last 22025 characters were not).
- No source on how a design specification records texts for
  localization (keys, the translator's context, the language of a
  part): the differently worded query of the second round returned
  nothing on it.
- No template opened has a place for internationalisation beyond what
  F11 lists.
- Platform values for native mobile and the desktop (target sizes,
  the platforms' accessibility interfaces, the W3C's guidance on
  applying the guidelines outside the web) were not looked for; the
  card on platforms asks about them.
- The law: the card's statement that accessibility is a legal duty in
  many markets was not checked; no act or harmonised standard was
  opened.
- The kit GitHub forked from was not opened, nor the other kits the
  searches named (a testing vendor's, a browser-testing vendor's, a
  software vendor's kit described on its design blog, a consultancy's
  kit named by a UK department's guidance, a browser maker's
  annotations page).
- Three pages of the second round did not open: a university's
  "Expectations for wireframe accessibility annotations" (its host
  did not resolve, and its other address redirected to another host's
  front page, not followed), the second critique of F6 (refused by
  its host), and a software vendor's "accessibility specification for
  design" in its design system (refused by its host). The last might
  hold a named template of exactly what this card asks; it stays
  unread.
- Dates of the W3C internationalisation pages [12][13][14][22]: not
  shown in the text fetched.

## Options

All seven are this note's; none was found as a recommendation in a
source. F and G are of the second round, and A was reworded by it.

- **A. Split by level.** The definition of an element carries what it
  is at every use (role or pattern, states, keys: F3, F12); its use on
  a page carries what differs there (its name in that place, heading
  level, texts shown and hidden: F8, F12); the page's definition
  carries what exists only between elements (title, focus order,
  headings, regions, where errors appear); one application-wide place
  carries what is decided once (contrast, target size, the look of
  focus, the languages and directions served, the formats of names,
  addresses and dates). Trade-off: every item has one home and the
  per-element idea of the frame is kept; four places must be kept
  consistent, and a small project may find it heavy.
- **B. A checklist walked, not fields filled.** The description gets
  no fixed fields; the agent that proposes it walks a task list such
  as the mapping of F2 and asks what is missing. Trade-off: cheap, and
  it rides on a list that is maintained elsewhere; the list is a draft
  worded for the web, and a checklist verifies a description after the
  fact where the card asks that these matters be designed.
- **C. Name the pattern, state the deviations.** For a rich element
  the definition names the authoring-practices pattern and its variant
  (F3) and writes only what differs. Trade-off: short, and it answers
  the objection of F6; the patterns are the web's, and a native target
  needs its platform's equivalent.
- **D. Texts in a catalogue of their own.** Every text, shown or
  hidden, has a key, its wording per language, its variables and
  cases by number (F15) and a note on where it stands; elements cite
  keys; a style guide and the project's terms are cited. Trade-off:
  language versions and consistent naming become checkable, and F9's
  separation of localizable elements is met in the description
  already; the reader of an element's definition no longer sees its
  words in place, and one person working end to end pays for a table
  he may not need.
- **E. Texts in place, variants beside them.** Each element's
  definition holds its texts with the language variants next to each
  other, as the component pages of F8 show them. Trade-off: readable
  and light; consistent naming across elements (3.2.4) is then nobody's
  table and has to be checked.
- **F. Outcomes in place of properties.** The description, or the
  acceptance criteria of the user stories beside it, states per
  element what a user of a keyboard or a screen reader must be able to
  do and hear, and names no role or attribute (F13). Trade-off: the
  wording survives a change of platform and of technique and can be
  tested as written; the builder, human or agent, must find the
  pattern alone, which is where F6 sees the harm, and a reader cannot
  check a proposal against a pattern.
- **G. A vocabulary of no platform.** Roles and purposes of
  interaction are written in a small fixed vocabulary of the
  framework's own, translated per target at the build (F14).
  Trade-off: one description serves the web, native mobile and the
  desktop; the vocabulary is one more thing to define and keep, and
  the only model found is a vendor's draft.

## Relevance to this project

The recommendation, as this agent's own inference from the findings: a
description of an interface should carry these matters at the level
where each is decided (option A), with the pattern named for rich
elements (option C), and should treat every text as content of the
description, the hidden texts included, with its language variants
(option D or E by the size of the project). It rests on four things
found: the standard's criteria fall apart cleanly by level (F1), the
W3C's own mapping gives about three fifths of the tasks to roles that
work before the build (F2), the authoring practices already have the
shape of an element's definition (F3), and two vendors say in their
own words that an element's definition cannot hold what differs at
every use (F12). It is chosen against three alternatives: an overlay
of annotations alone, which the sources show working for simple
elements and contested for complex ones (F4, F6); a checklist alone,
which checks what was written without causing it to be written; and
outcomes alone (option F), which belong, by this agent's reading, to
the acceptance criteria the chain already has and complement the
description without replacing it. The frame's idea under test holds
on this card's ground in part: role, states and keys are properties
of an element and fit a definition of its own; its name, its heading
level and its texts belong to its use on a page; focus order, title,
headings and regions belong to the page; contrast, target size and
the languages served belong to none of them. The second round changed
this paragraph in one point: the first round had placed the name in
the element's definition.

What the recommendation does not rest on: evidence that describing
these matters early lowers rework. That is one vendor's figure and a
plausible argument (F5), and neither round found a measurement.

What a first draft of the template could ask, each traceable to a
finding: per kind of element the role or the pattern followed (F3),
the states and what announces their change (F1, F14), the keys it
answers to (F3); per use of an element its accessible name and whether
that contains the visible label (F1, F2, F12), its heading level, and
every text including the hidden ones (F8), each text whole with its
variables, its cases by number and a note for the translator (F15);
per page the title, the order of focus, the headings and regions,
where errors appear and how they are worded (F2, F7); once per
application the contrast and target-size floor, the look of focus,
the languages and writing directions, the formats of names, addresses
and dates in forms, the rule that layouts let text grow (F9, F10),
and the style guide and terms cited (F7).

Consult when: the template of an element's or a page's definition is
drafted; it is decided where the texts of an interface live, or how a
text with a number or a variable is written down; a project takes a
second language or a right-to-left one; it is decided whether
accessibility is stated as properties in the description or as
outcomes in the acceptance criteria; a reviewer or a check for
accessibility of a description is defined; the output of a build is
judged against the description; someone proposes to leave
accessibility to the build stage or to the component library.

## Sources

Sources 1 to 15 are of the first round, 16 to 23 of the second.

1. Web Content Accessibility Guidelines (WCAG) 2.2. W3C. W3C
   Recommendation, 12 December 2024 (dated by the document's own
   head).
   https://www.w3.org/TR/WCAG22/
   Kind: primary (the standard). How read: summarised fetch, in two
   parts covering characters 0 to 200000 of 269706; the success
   criteria quoted lie in those parts, the remainder (not read) lies
   after the criteria quoted. Original.
2. [Draft] Accessibility Roles and Responsibilities Mapping (ARRM).
   W3C Web Accessibility Initiative, developed through the ARRM
   Community Group. "Updated: 28 October 2026" (byline on the page).
   https://www.w3.org/WAI/planning/arrm/
   Kind: primary (the publisher's own guidance; a draft). How read:
   summarised fetch, the overview page in full. Original.
3. ARRM, Tasks. W3C Web Accessibility Initiative. "Updated: 28
   October 2026" (byline on the page).
   https://www.w3.org/WAI/planning/arrm/tasks/
   Kind: primary (a draft). How read: summarised fetch, twice, the
   whole page; the totals are the fetch's tallies, not the page's.
   Original.
4. Combobox Pattern, ARIA Authoring Practices Guide (APG). W3C Web
   Accessibility Initiative. Undated; footer copyright 2026.
   https://www.w3.org/WAI/ARIA/apg/patterns/combobox/
   Kind: primary. How read: summarised fetch; headings of the whole
   page, quotes from "About This Pattern", "Keyboard Interaction" and
   "WAI-ARIA Roles, States, and Properties". Original.
5. github/annotation-toolkit, repository front page and README.
   GitHub. Undated in the text fetched (135 commits, no date shown).
   https://github.com/github/annotation-toolkit
   Kind: primary (a vendor's documentation of its own product). How
   read: summarised fetch, the README. Original.
6. Level up design-to-code collaboration with GitHub's open source
   Annotation Toolkit. Andrea Griffiths, GitHub Blog. 18 November 2025
   (byline).
   https://github.blog/enterprise-software/collaboration/level-up-design-to-code-collaboration-with-githubs-open-source-annotation-toolkit/
   Kind: primary for the product, a vendor claim for the 48% figure.
   How read: summarised fetch, the whole post. Original.
7. Practitioner Views on Mobile App Accessibility: Practices and
   Challenges. Amila Indika, Rick Kazman, Anthony Peruma. arXiv
   2601.14131 [cs.SE], submitted 20 January 2026, v1 (dated by the
   arXiv listing); listed there for the 48th IEEE/ACM International
   Conference on Software Engineering, Research Track.
   https://arxiv.org/abs/2601.14131
   Kind: primary (a research paper). How read: summarised fetch,
   partially: the listing page with the abstract only, the paper not.
   Original as a preprint; the conference version was not opened.
8. Accessibility annotation kits only annotate. Eric Bailey, the
   author's own site. 13 November 2023 (byline).
   https://ericwbailey.website/published/accessibility-annotation-kits-only-annotate/
   Kind: primary as a practitioner's own argument; opinion, no data.
   How read: summarised fetch, the whole essay. Original. The page's
   text carries an instruction addressed to automated readers (to
   print a word a great many times); it was not followed and has no
   bearing on what is cited.
9. Writing for user interfaces. GOV.UK Service Manual. Published 10
   October 2017, last updated 16 April 2018 (the page's own dates).
   https://www.gov.uk/service-manual/design/writing-for-user-interfaces
   Kind: primary (a public administration's guidance). How read:
   summarised fetch, the whole page. Original.
10. Error message, GOV.UK Design System. GOV.UK Design System team.
    Undated; the latest entry under "Recent changes" is January 2024.
    https://design-system.service.gov.uk/components/error-message/
    Kind: primary. How read: summarised fetch, the whole page; the
    linked message templates of other components were not opened.
    Original.
11. Search, U.S. Web Design System (USWDS). U.S. General Services
    Administration. Undated in the text fetched.
    https://designsystem.digital.gov/components/search/
    Kind: primary. How read: summarised fetch, twice, the whole page;
    the linked page of accessibility tests was not opened. Original.
12. Localization vs. Internationalization. W3C Internationalization
    (the host; author and date not shown in the text fetched).
    Undated.
    https://www.w3.org/International/questions/qa-i18n
    Kind: primary. How read: summarised fetch, the whole page.
    Original.
13. Internationalization Quick Tips for the Web. W3C
    Internationalization (the host; author and date not shown in the
    text fetched). Undated; the page says it "will be updated from
    time to time."
    https://www.w3.org/International/quicktips/
    Kind: primary. How read: summarised fetch, the whole page.
    Original.
14. Text size in translation. W3C Internationalization (the host;
    author and date not shown in the text fetched). Undated.
    https://www.w3.org/International/articles/article-text-size
    Kind: primary for the advice; secondary for the table, which it
    attributes to IBM's "Guidelines to design global solutions" (not
    opened). How read: summarised fetch, the whole page. Original.
15. tmobile/magentaA11y, repository front page and README. T-Mobile
    (the owning account). Undated in the text fetched (1,269 commits,
    no date shown).
    https://github.com/tmobile/magentaA11y
    Kind: primary (the publisher's own repository). How read:
    summarised fetch, partially: the front page and README, which show
    the layout of the files; no criterion file and not the live site.
    Original.
16. Accessibility acceptance criteria, GOV.UK Developer Documentation
    (from the repository of the GOV.UK publishing components).
    Government Digital Service. Last updated 9 May 2022 (the page's
    own date); the page warns that it may be out of date.
    https://docs.publishing.service.gov.uk/repos/govuk_publishing_components/accessibility_acceptance_criteria.html
    Kind: primary (a public administration's own guidance). How read:
    summarised fetch, the whole page; of the examples one criterion
    was returned in full. Original.
17. Team guide, How to write accessibility acceptance criteria
    (Accessibility, Your Team and You). BBC. Undated; footer "© 2025
    BBC".
    https://bbc.github.io/accessibility-news-and-you/guides/accessibility-acceptance-criteria.html
    Kind: primary (a public broadcaster's own team guidance). How
    read: summarised fetch, the whole page. Original.
18. Accessibility, Spectrum Design Data Specification. Adobe. Version
    `1.0.0-draft`; undated.
    https://opensource.adobe.com/spectrum-design-data/spec/accessibility/
    Kind: primary (a vendor's documentation of its own specification;
    a draft). How read: summarised fetch, the whole chapter. Original.
19. Annotations for keyboard and screen reader navigation, a unit of
    the training module "Accessibility design specs with annotations".
    Microsoft Learn. 14 February 2025 (structured data of the page).
    https://learn.microsoft.com/en-us/training/modules/accessibility-design-specs-with-annotations/3-annotations-for-keyboard-screen-reader-navigation
    Kind: primary (a vendor's training on its own practice and kit).
    How read: in full; the fetch returned the page's own text, the
    pictures by their descriptions only. Original.
20. Design system annotations, part 1: How accessibility gets left out
    of components. Jan Maarten, GitHub Blog. 9 May 2025, updated 24
    November 2025 (byline).
    https://github.blog/engineering/user-experience/design-system-annotations-part-1-how-accessibility-gets-left-out-of-components/
    Kind: primary (a vendor on its own design system and kit). How
    read: summarised fetch, the whole post; its second part was not
    opened. Original.
21. Unicode Technical Standard #35, Part 9: MessageFormat. Unicode
    Consortium. CLDR Version 49, 2026-10-21 (dated by the document's
    own head); stable by its own statement.
    https://www.unicode.org/reports/tr35/49/tr35-messageFormat.html
    Kind: primary (the standard). How read: summarised fetch, in two
    parts covering characters 0 to 200000 of 222025; the last part,
    in the interchange data model and after, was not read. Original.
22. Working with Composite Messages. W3C Internationalization (the
    host; author and date not shown in the text fetched). Undated.
    https://www.w3.org/International/articles/composite-messages/
    Kind: primary. How read: summarised fetch, the whole page.
    Original.
23. Content Designer, DWP Accessibility Manual. Department for Work
    and Pensions (by the site's name). Undated.
    https://accessibility-manual.dwp.gov.uk/guidance-for-your-job-role/content-designer
    Kind: primary (a public administration's guidance by role). How
    read: summarised fetch, the whole page. Original.

Named in the note and not opened, therefore without an address and
cited for no content: "Why UX annotations are a poor band-aid for web
accessibility" (an article in a design publication, returned by the
disconfirming queries of both rounds; left for the opening budget in
the first round, refused by its host with status 403 in the second);
a testing vendor's blog posts and fact sheet on shifting accessibility
left, and a platform vendor's internal blog on the same (a vendor's
writing on its own market, excluded by kind); the Web Accessibility
Annotation Kit of CVS Health (the fork [5] was read in its place); a
university's "Expectations for wireframe accessibility annotations"
(host not resolved; the other address redirected elsewhere); a
software vendor's "accessibility specification for design" (status
403); an interview study of accessibility experts and a thesis,
returned by the query for empirical work and off the question by
their titles; a consultancy's slides on reusable acceptance criteria.

## Opened and not used

None: each of the twenty-three pages opened is cited above. The three
pages that did not open are named at the end of Sources.

## Search record

The note was made in two rounds. In the first the session's search
budget ended after six queries, so three planned queries could not be
run and the stop rule could not be tested; when search worked again
the run was taken up for those queries, the disconfirming query in
the card's own wording and one differently worded query, with an
allowance of eight further pages.

First round, queries run, in order:

1. accessibility annotations design handoff kit
2. W3C WAI accessibility roles and responsibilities mapping designer
   tasks
3. W3C internationalization guidance designing for localization text
   expansion
4. "accessibility annotations" do not work criticism developers ignore
   (disconfirming)
5. shift-left accessibility evidence study defects originate in design
   (disconfirming)
6. content design guide government writing interface text error
   messages style guide

First round, pages opened: fifteen, by eighteen fetches (the standard
in two parts, the task table and the U.S. search component twice
each, the second time to check a count and a quote), in the order
[1], [4], [2], [6], [3], [5], [9], [10], [11], [13], [14], [12], [8],
[7], [15]. Seven came from the result lists ([2], [6], [7], [8], [9],
[13], [14]); two were followed from links on pages opened ([3] from
[2], [5] from [6]); six were opened by an address the agent knew
([1], [4], [10], [11], [12], [15]), each cited only after it opened
under that address. This corrects the count of the first round's
note, which said nine came from the result lists.

Second round, queries run, in order:

7. accessibility acceptance criteria component specification template
   design system documentation (planned, not run in the first round)
8. study designers accessibility annotations handoff developers
   empirical interview CHI (planned, not run; disconfirming in kind)
9. Unicode MessageFormat 2 specification plural gender localizable
   strings translators context (planned, not run)
10. "accessibility annotations" "do not work" OR "don't work" OR "not
    enough" designers developers (the card's disconfirming query in
    its own wording)
11. shift-left accessibility evidence peer-reviewed study early design
    phase accessibility requirements fewer defects (the card's
    disconfirming query, second half)
12. UI design spec handoff what to document screen reader labels focus
    order microcopy localization strings (the differently worded query
    for the stop rule)

Second round, pages opened: eight, by nine fetches (the message
standard in two parts), in the order [18], [16], [21], [22], [20],
[17], [19], [23]. Six came from this round's result lists ([16],
[17], [18] from query 7, [21] from query 9, [20] from query 10, [19]
from query 12); [23] came from the result list of query 6 of the
first round; [22] was opened by an address the agent knew. Three
further pages were tried and did not open, in four attempts; they are
named under Not found and at the end of Sources.

What the disconfirming query found, both rounds: for "accessibility
annotations do not work", two critiques by practitioners, of which
one opened [8] and one was refused by its host, talk abstracts, the
kit publisher's own statement of limits [20], posts of other vendors
on their own kits, and one research paper that turned out to be a
survey of mobile developers and not about annotations [7]; no study
measuring whether annotations are followed. For "shift-left
accessibility evidence", vendors' posts and fact sheets with figures
of their own, a platform vendor's internal blog with a cost multiple,
university pages repeating the principle, and no independent or
peer-reviewed measurement. The query for empirical work returned an
interview study of accessibility experts and a thesis, neither on
annotations. The evidence is thin either way, as the card expected;
the one figure in favour is [6]'s.

What the differently worded query found: annotation guidance of a
platform vendor [19] and of a software vendor's design system (not
opened, refused), checklists for designers of a university and of a
state administration, a testing vendor's talk, and nothing on how a
specification records texts for localization. These are the kinds of
source the note already held; the one page opened from it confirmed
F4 and, with [20], gave the refinement F12.

Why the run ended: the first round by the opening budget, fifteen
pages; the second by its allowance of eight pages. The card's stop
rule is met on both of its conditions: the differently worded query
returned no new kind of source and no new route, and every route the
card names has a primary source. With one reserve said plainly:
twenty-three pages were opened in all, above the card's ten to
fifteen, by the second round's own allowance; and one result of that
query, a vendor's page that may hold a named specification template,
could not be opened.
