---
date: 2026-11-21
project: forge
topic: the map of the field of textual UI/UX specification and its words
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/01-map-of-the-field
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 1; no known note named by the card; web sources below
---

# No synthesis spans how user interfaces and user experience are specified in text; four communities each map their own slice in their own words

<!-- Shape: templates/research.md -->

## In short

No survey, taxonomy or comparison was found that covers the
specification of interfaces in text as a whole. Four communities each
have an overview of their own slice, in their own words: the academic
model-based tradition (surveys of user interface description languages
of 2003 to 2009, an overview of 2011, the W3C's notes of 2014), the
formal standards (OMG's IFML 1.0 of 2015, ISO/TR 25060:2023), design
practice ("design specs" and "handoff": a design-tool file and a
ticket, not a text document), and the AI coding tooling of 2025 and
2026 ("spec-driven development", DESIGN.md), where the one overview
read does not treat the interface as part of a spec at all. How sure:
moderately. The absence is the negative result of twenty queries, not
a published statement; every page was read through a summarising
fetch; and two routes (the surveys of description languages, a
practitioner glossary for "design handoff") have no primary read for
content. The disconfirming query found no page that answers it, and
what it led to confirmed the expectation of several partial standards
and no dominant one: a W3C community group named for exactly this, the
UI Specification Schema Community Group, was called in August 2025 and
closed on 21 May 2026 with no published report listed. The one
unexpected thing: the word "design" stands for three different things
in the sources (the interface design of practice, the technical design
document of spec-driven tools, the visual identity of DESIGN.md), and
none of the three is a description of screens and behaviour in text.

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
> what practice does, what the options are. This card is the first
> of twenty-two and runs before the others: the words and any
> synthesis it finds may rewrite them. The other cards ask about the
> description of one screen, the user's paths, the structure above
> the screens, formal languages and standards, components in design
> systems, pages composed of defined blocks, behaviour of the whole
> application, descriptions written for an agent that builds,
> measured studies of models and interfaces, previews, design tools,
> the agent that proposes a description, declarative interface
> languages, the platforms, accessibility and wording, the place in
> the process, how a proposal is judged, where textual descriptions
> failed, what a description cites from other documents, its change
> after the first build, and automated testing of interfaces.

The card, verbatim:

#### Card 1: The map of the field and its words
- **Question:** Does a synthesis already exist of how user interfaces and user experience are specified in text (a survey, a taxonomy, a comparison of approaches), and in which words do practice, the standards and the AI tooling of 2024 to 2026 speak of it (UI specification, functional specification, interaction specification, design handoff, design documentation, UI description language, design as code, spec-driven development)?
- **Why it matters:** every other card searches by the field's words, and a synthesis found here saves cards or rewrites them.
- **What would answer it:** survey and overview literature: academic surveys, standards bodies' overviews, overviews by practitioner organisations.
- **Where to look:** surveys of UI description languages and of model-based UI development; notes of the W3C; glossaries and overviews of practitioner organisations; recent overviews of spec-driven development that treat the interface. Must turn up: the W3C's model-based UI work, IFML, "design handoff".
- **Disconfirming query:** "why is there no standard for UI specification"; expected: several partial standards and no dominant one.
- **Stop rule:** nothing new from a differently worded query and every route has a primary source; ten to fifteen pages opened.

The baseline the note must beat: the assumption a reader would hold
without the research, that the field has one recognised overview and
a settled vocabulary, so that the card's own list of words is the
right search vocabulary for the twenty-one cards that follow. A list
of terms from memory is that baseline; the note beats it only where a
word is tied to a page opened in this run and where the existence or
the absence of a synthesis rests on searches that are recorded.

## Key findings

Every page of this note was read through a fetch that summarises: it
was asked for verbatim extracts and the place of each, and the quotes
below are as the fetch returned them, not checked against the raw
page. Each finding therefore rests on a summarised fetch; where a
finding rests on less (a record without an abstract, an abstract
without the text), it says so.

F1. **No survey, taxonomy or comparison was found that covers the
specification of interfaces in text across the academic languages,
the standards, design practice and the AI tooling.** [single source:
the negative result of this run's twenty queries; no publication
states it] Each overview found stays inside one community: [1], [3]
and [10] inside the model-based tradition, [6] inside the ISO's
human-centred design standards, [4] inside design practice, [5]
inside AI-assisted coding, [9] inside research on language models in
design. None of them cites or orders the others, as far as the parts
read show. Three differently worded queries late in the run (design
to code surveys; systematic reviews of UI specification notations;
taxonomies of textual notations) returned single systems and the same
old surveys, no synthesis.

F2. **The academic tradition has syntheses of its own, and those
found date from 2003 to 2014.** [consensus within that literature;
survey records and a standards body's note] A survey under the name
"User Interface Description Languages" was published in 2009 [3];
only its repository record was read, which shows no abstract, so its
content is not reported here. An overview of model-based user
interface development of 2011 says of itself: "This article aims to
give a comprehensive overview of the history, describes important
aspects and current approaches," (abstract) [10]; only the abstract
was read. The W3C's Introduction to Model-Based User Interfaces is a
"W3C Working Group Note 07 January 2014" (header) [1], a note and not
a recommendation. It orders descriptions by abstraction with the
CAMELEON Reference Framework, which "makes explicit a set of UI
models (e.g., Tasks, Abstract UI, Concrete UI, Final UI)"
(Introduction), the last of which "expresses the UI in terms of
implementation technology dependent source code" (Introduction). It
names as languages UIML 4.0, the Useware Dialog Modeling language,
ConcurTaskTrees and MARIA, points to "A separate glossary of terms
for the Model-Based User Interface domain" (Glossary of Terms), and
says of the tools it lists that "none of them, so far, implements the
MBUID standard." (Examples of Tools). Two readings of the same
tradition stand side by side: [10] says "After 30 years of research
there has been significant success in modeling user interfaces."
(abstract), while a practitioner writing in 2025 says of the wider
family that "MDD never took off for business applications" [5]. The
first speaks of research, the second of adoption; neither gives a
figure.

F3. **Formal standards exist for slices of the matter, and none of
those found is a standard for describing an interface in text as a
whole.** [consensus; the standards bodies' own pages] OMG's
Interaction Flow Modeling Language stands at version 1.0, February
2015, document formal/15-02-05, and its page lists no later version
[2]. Its aim is "the definition of Interaction Flow Models that
describe the principal dimensions of an application front-end"
(About the specification), among them "the view part of the
application, made of view containers and view components;" and "the
control logic that determines the actions to be executed after an
event occurrence;". It is published with a metamodel, a profile and a
diagram interchange file as XMI: a model, not prose (the last four
words are this agent's reading). ISO/TR 25060:2023, a Technical
Report of ISO/TC 159/SC 4 published in April 2023, "describes
information items enabling systematic human-centred design for
interactive systems." and gives "the high-level content structure to
be used for documenting each information item."; it adds: "This
document does not prescribe any kind of method, life cycle or
process." (abstract) [6]. Only the catalogue page was read; which
information items it names is not on that page (see Not found). The
W3C's model-based work ended in notes [1].

F4. **Practice speaks of "design specs" and of "handoff", and what is
handed over is a design-tool file with a ticket, not a text
document.** [practitioner claim [4]; vendor documentation [12]] A
practitioner organisation that sells training and consulting writes
in June 2025: "Design specifications (specs) are documents that
provide all relevant information" (What Are Design Specs?) and "The
design file is what designers typically think of when they hear the
phrase 'design spec.'" (The Components of a Design Spec) [4]. The
written part is "a development issue or ticket in a development tool,
like GitHub or Linear" (What Are Design Specs?), and "For many teams,
this documentation takes the form of a Figma (or other design tool)
link" (heading not reported by the fetch). The design file carries
interaction flows, visual design, layout, content and accessibility
needs; the issue carries the goal, the scope, functional and
nonfunctional requirements, use cases and risks (the two lists as the
fetch summarised them). The article gives no mandatory template and
says the arrangement "may vary depending on the team". The design
tool's own documentation supplies the other word: Dev Mode is "a
developer-focused workspace for inspecting designs.", with a section
headed "Manage dev handoff", statuses such as "ready for dev",
"annotations to markup designs" and an inspect panel that "displays
design specs" [12]. That page is undated and was read on 2026-11-21.

F5. **"Spec-driven development" is the AI tooling's word, its
definition was unsettled in October 2025, and the overview read does
not treat the interface as part of a spec.** [emerging; one
practitioner's analysis of three tools, single source] The overview
[5], dated 15 October 2025, defines: "Spec-driven development means
writing a “spec” before writing code with AI." (Definition), says
"the definition of “spec-driven development” (SDD) is still in flux."
(place not reported by the fetch) and, in its Conclusions, that the
term "isn’t very well defined yet". A spec is "a structured,
behavior-oriented artifact - or a set of related artifacts - written
in natural language" (What is a spec?). Three levels are told apart:
spec-first, "A well thought-out spec is written first, and then used
in the AI-assisted development workflow for the task at hand.";
spec-anchored, "The spec is kept even after the task is complete";
spec-as-source, "only the spec is edited by the human, the human
never touches the code." (Definition). Beside the spec stand general
context files under the names "memory bank", "constitution" and
"steering". In one of the three tools the chain is "Requirements →
Design → Tasks", one Markdown file each, and the design file there is
technical (data flow, data models, error handling, testing strategy,
as the fetch summarised its example). The fetch found no mention of
mockups, of user experience or of the front end as part of any spec.
The source is thirteen months old in a field that moves; the result
lists showed overviews of 2026 that were not opened.

F6. **The one AI-tooling format found that describes design in text
for a coding agent covers the visual identity, not screens, paths or
behaviour.** [vendor claim; the vendor's own documentation of its own
format, single source] DESIGN.md calls itself "A format specification
for describing a visual identity to coding agents." (README, opening)
[11]. It pairs "machine-readable design tokens (YAML front matter or
interleaved YAML code blocks)" with "human-readable design rationale
(markdown prose)" under prescribed headings (Overview, Colors,
Typography, Layout, Elevation & Depth, Shapes, Components, Do's and
Don'ts among them, as the fetch listed them). "The DESIGN.md format
is at version `alpha`." and "DESIGN.md tokens are inspired by the W3C
Design Token Format." The fetch found no mention of screens, user
flows or navigation. The page is a live repository without a date
shown; the state is as read on 2026-11-21.

F7. **The newest attempt at a standard under the very name "UI
specification" lasted nine months and left no listed output.**
[single source; the standards body's own pages] The call of 13 August
2025 for the W3C's UI Specification Schema Community Group set out to
"define a common, implementation-agnostic meta-model for specifying"
the design, layout, behaviour and constraints of user interface
elements, to "Produce and maintain a formal schema (JSON/JSON
Schema)" and to "Align vocabulary with related W3C efforts such as
Open UI" [7]. Its unit is the single element or component, not the
screen or the application. The group's page now carries the notice
"The UI Specification Schema Community Group was closed on 21 May
2026." and lists no published report and no repository [8]. A
community group is not a W3C working group; the call itself says the
hosting implies no endorsement (as the fetch summarised it).

F8. **The academic synthesis of the language-model era that was found
maps models across the design lifecycle; its abstract names neither
specification nor handoff.** [single source; systematic literature
review, a preprint, abstract only] The review [9] (arXiv 2507.04469,
second version of 17 July 2025) describes itself as "synthesizing
findings from 38 peer-reviewed studies published between 2022 and
2025." and maps the models' "integration across the design lifecycle,
from ideation to evaluation." Whether its body treats textual
descriptions of interfaces was not read.

F9. **The field's words sort by community, and the same thing is
rarely called by the same word in two of them.** [emerging; compiled
by this agent from the sources above, the compilation its own]

| Word | Who speaks it | What it stands for there | Source |
|---|---|---|---|
| User Interface Description Language (UIDL) | academic surveys; the W3C note | the name under which such languages are surveyed and compared | [3] [1] |
| Model-Based User Interface Development (MBUID); Task and Domain models, Abstract UI, Concrete UI, Final UI | W3C working group, academic overview | describing an interface as models at levels of abstraction, the last being source code | [1] [10] |
| Interaction Flow Model; view container, view component, event, binding | OMG | a model of the front end: composition, interaction, control logic | [2] |
| information item; Common Industry Format (CIF) for usability-related information | ISO | the documents of human-centred design and their content structure | [6] |
| design specifications (specs); design file; development issue, ticket; annotations | practitioner organisation | what a designer gives a developer: a design-tool file and a written issue | [4] |
| design handoff, dev handoff, developer handoff; ready for dev; inspect; annotations | design-tool vendor's documentation | the passage from design to development and the tool's features for it | [12] |
| spec-driven development (SDD); spec; spec-first, spec-anchored, spec-as-source; memory bank, constitution, steering | AI coding tooling, as a practitioner analyses it | a natural-language artefact written before code and given to a coding agent | [5] |
| DESIGN.md; visual identity; design tokens; design rationale | AI tooling, a vendor's open format | a design system in text for a coding agent | [11] |
| UI Specification schema; meta-model; anatomy, states, variants | W3C community group, closed | a machine-readable specification of one interface element | [7] [8] |

Of the card's eight words: "UI description language" lives in the
academic sources [3] [1]; "UI specification" was the name of the
closed W3C group and meant one element [7]; "design handoff" lives in
the vendor's documentation [12], and the practitioner organisation's
article of 2025 does not use it at all, as the fetch reported [4];
"spec-driven development" lives in the AI tooling [5]; "design
documentation" appears only as the loose word "documentation" [4];
"functional specification", "interaction specification" and "design
as code" appear in no page opened (see Not found).

## Unexpected

"Design" means three things. In practice it is the interface design
held in a design tool [4] [12]; in the spec-driven tool described in
[5] the design file is the technical design between requirements and
tasks; in DESIGN.md it is the visual identity of a design system
[11]. A query by "design spec" or "design.md" mixes the three, and
none of the three is a description of screens and behaviour in text.
This is a lead for the wording of every later card that searches by
"design".

The card assumes "design handoff" is practice's word for the thing
described; [4] and [12] say otherwise. "Handoff" names the passage
and the tool's features around it [12]; the thing handed over is
called "design specs" [4], and it is a design-tool file with a
ticket. The result lists for "design handoff" were filled with
vendors' pages on their own market, which the brief excludes by kind,
so a card that searches by "handoff" will land mostly on pages it
cannot use. The question is still answered as put: the word turned
up, in [12].

The newest route points back at the oldest. The overview of
spec-driven development [5] itself draws the parallel to model-driven
development, the family the model-based interface work of [1], [2]
and [10] belongs to: "MDD never took off for business applications",
and "I wonder if spec-as-source, and even spec-anchoring, might end
up with the downsides of both MDD and LLMs." That the two are one
family is this agent's reading; the warning is the source's. It is a
lead for the cards on formal languages and on where textual
descriptions failed.

Two families of words surfaced in result lists only, nothing opened:
formats in which an agent emits an interface at run time for a client
to render (the lists named an open project of that kind and called it
"generative UI"), which is a different thing from a description
handed to a build stage; and research prototypes of 2025 that speak
of "intermediate representation" and "structured specification"
between an intent and generated interface code. Both are leads for
the cards on declarative interface languages, on the agent that
proposes and on measured studies, as search words, not as findings.

## Not found

- A survey, taxonomy or comparison across the four communities:
  looked for with twenty queries on a general web search; none in
  any result list. A synthesis behind a paywall or under words not
  tried cannot be excluded.
- The content of the surveys of user interface description
  languages: the repository record of the 2009 survey [3] shows no
  abstract; the publisher's page returned only its header; a
  repository file came back as an unreadable PDF and was not
  identified; the publisher's page of the 2003 review of XML-compliant
  languages redirected to a sign-in. Which languages they compare and
  by which criteria is not reported here. A survey of 1989 from a
  university programming research group appeared in a result list and
  was not opened.
- The names of the information items of ISO/TR 25060:2023: the
  catalogue page [6] does not list them and the text is sold. A
  search summary said the 2023 edition has a section titled
  "User-system interaction and user interface specification" and the
  withdrawn 2010 edition separate items "User interaction
  specification" and "User interface specification"; this is
  unverified and no finding. If it holds, these are the ISO's words
  for the document the project wants.
- Whether the W3C's Model-Based User Interfaces Working Group is
  closed, and the status of its Task Models and Abstract User
  Interfaces specifications: not on the page opened [1]. A search
  summary said the group closed in April 2014; unverified.
- Any figure on the adoption of IFML, of a description language or of
  the model-based approach: no source. The two statements in F2 are
  claims without numbers.
- "Functional specification", "interaction specification" and "design
  as code" as living terms of 2024 to 2026: in no page opened. The
  result lists showed vendors' blogs, an encyclopaedia article on
  "User interface specification", practitioner articles of 2009 and
  2010 and, for "design as code", pieces that mean a design system
  kept in code; none opened. No authoritative definition of
  "interaction specification" appeared in any list.
- An overview of spec-driven development that treats the interface:
  none found; [5] does not. The tools' own documentation was not
  opened, so that they offer nothing for the interface is not
  claimed.
- A glossary entry of a practitioner organisation for "design
  handoff": none opened. A topic page "Design Specifications" of a
  design education organisation appeared in the last result list,
  after the openings were spent.
- A page that answers "why is there no standard for UI specification"
  directly: none.

## Options

Left out: the card asks for a fact, not a choice.

## Relevance to this project

The recommendation: treat the map of this field as something the
bundle has to draw itself, and rewrite the search words of the later
cards by community before they run. It rests on F1 (no synthesis to
adopt), F9 (the words do not carry across communities) and the first
two entries under Unexpected. It is chosen against taking one of the
existing frames as the map, whether IFML, the ISO's information items
or the spec-driven tools' file sets, because each covers one slice
(F3, F5, F6) and the newest attempt at a common schema closed without
output (F7).

In plain words, for the cards that follow:

- Formal languages and standards: search by "user interface
  description language", "model-based user interface development",
  "CAMELEON reference framework", "abstract user interface", "task
  model", "IFML", "Common Industry Format"; do not expect a dominant
  standard, and ask why the notes of 2014 and the version of 2015 had
  no successor found here.
- Practice, design tools and the place in the process: search by
  "design specs", "annotations", "ready for dev", "development
  issue"; use "handoff" for the passage, not for the document, and
  expect vendors' pages.
- Descriptions written for an agent that builds, and the agent that
  proposes: search by "spec-driven development", "spec", "DESIGN.md",
  "design tokens", and, as unverified leads, "intermediate
  representation", "structured specification", "generative UI".
- Every card: say which "design" is meant.

This agent's own inferences, marked as such: the levels of the
CAMELEON framework (task, abstract, concrete, final) are the only
frame found that orders descriptions of an interface by abstraction,
and may serve the bundle's synthesis as an ordering; the document the
project wants sits where none of the four communities has a text
artefact of its own, between the technical design of the spec-driven
tools and the design-tool file of practice; and the name of that
document is open, since "UI specification" was last used for a
per-element schema and "design spec" means a design-tool file.

Consult when: the search words of a later card are chosen or
rewritten; someone proposes to adopt an existing standard or tool
format as the frame of the new document; the new document or layer is
named; the bundle's synthesis is written and needs to say what
existed before it.

## Sources

1. Introduction to Model-Based User Interfaces. W3C, Model-Based User
   Interfaces Working Group. 7 January 2014, dated by the document
   header. https://www.w3.org/TR/mbui-intro/ Kind: primary. How read:
   summarised fetch of the whole page, verbatim extracts requested.
   Original.
2. IFML: Interaction Flow Modeling Language, specification page.
   Object Management Group. Version 1.0, February 2015, dated by the
   page's own version listing. https://www.omg.org/spec/IFML Kind:
   primary. How read: summarised fetch of the whole page, verbatim
   extracts requested; the specification PDF not opened. Original.
3. A Theoretical Survey of User Interface Description Languages:
   Preliminary Results. J. Guerrero-García, J. M. González-Calleros,
   J. Vanderdonckt. 2009, dated by the repository record, whose
   conference dates (November 2010) disagree with its year; not
   resolved. The record prints DOI 10.1109/LA-WEB.2009.40, not
   resolved in this run.
   https://research.dial.uclouvain.be/handle/2078.5/274659 Kind:
   primary (an academic survey). How read: partially, the repository
   record only (title, authors, venue, pages 36 to 43); the record
   shows no abstract and the full text was not read. A repository
   record of a paper in conference proceedings: a copy of the
   bibliographic data.
4. Creating Design Specs for Development. Kelley Gordon, Nielsen
   Norman Group. 20 June 2025, dated by byline.
   https://www.nngroup.com/articles/creating-design-specs-for-development/
   Kind: primary for the organisation's own guidance, secondary for
   what teams do. How read: summarised fetch of the whole article,
   verbatim extracts requested. Original. The publisher sells
   training and consulting in this field.
5. Understanding Spec-Driven-Development: Kiro, spec-kit, and Tessl.
   Birgitta Böckeler, on martinfowler.com. 15 October 2025, dated by
   byline.
   https://www.martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html
   Kind: secondary (a practitioner's analysis of three tools she
   tried). How read: summarised fetch of the whole article, verbatim
   extracts requested. Original. The author's employer sells software
   consulting.
6. ISO/TR 25060:2023, Systems and software engineering, Systems and
   software Quality Requirements and Evaluation (SQuaRE), General
   framework for Common Industry Format (CIF) for usability-related
   information. ISO, ISO/TC 159/SC 4. Edition 1, published April
   2023, dated by the catalogue's stage log.
   https://committee.iso.org/standard/83763.html Kind: primary. How
   read: partially, the catalogue page with the abstract; the report
   itself is sold and was not read. Original (the standards body's
   own catalogue).
7. Call for Participation in UI Specification Schema Community Group.
   W3C Community and Business Groups. 13 August 2025, dated by the
   post.
   https://www.w3.org/community/uispec/2025/08/13/call-for-participation-in-ui-specification-schema-community-group
   Kind: primary. How read: summarised fetch of the whole post,
   verbatim extracts requested. Original.
8. UI Specification Schema Community Group, group page. W3C. Closure
   notice of 21 May 2026, dated by the notice on the page.
   https://www.w3.org/groups/cg/uispec Kind: primary. How read:
   summarised fetch of the whole page, verbatim extracts requested.
   Original.
9. The role of large language models in UI/UX design: A systematic
   literature review. Ammar Ahmed, Ali Shariq Imran. arXiv
   2507.04469, first version 6 July 2025, second version 17 July
   2025, dated by the submission history.
   https://arxiv.org/abs/2507.04469 Kind: primary (a preprint; no
   journal reference shown). How read: partially, the abstract page
   only; the paper itself was not read. Original.
10. Past, Present, and Future of Model-Based User Interface
    Development. Gerrit Meixner, Fabio Paternò, Jean Vanderdonckt.
    i-com, vol. 10, no. 3, pages 2 to 11, 2011, dated by the record.
    https://dl.gi.de/items/03a6f13c-a935-4407-8553-d89d1a63b8bf/full
    Kind: primary (an academic overview). How read: partially, the
    digital library's record with the abstract; no full text linked
    there and none read. A library record of a journal article: a
    copy of the bibliographic data and the abstract.
11. DESIGN.md, repository and README. google-labs-code. Undated on
    the page; read on 2026-11-21.
    https://github.com/google-labs-code/design.md Kind: primary (the
    vendor's own documentation of its own format). How read:
    summarised fetch of the repository page with the README, verbatim
    extracts requested; the format specification file not opened.
    Original.
12. Guide to Dev Mode in Figma. Figma Help Center. Undated; read on
    2026-11-21. https://help.figma.com/hc/en-us/articles/15023124644247
    Kind: primary (the vendor's own documentation of its own
    product). How read: summarised fetch of the whole article,
    verbatim extracts requested. Original.

## Opened and not used

- https://www.iso.org/standard/83763.html: returned HTTP 403; the
  same catalogue entry was read at [6].
- https://computer.org/csdl/proceedings-article/la-web/2009/05341626/12OmNBSBkiO:
  the publisher's page of [3]; the fetch returned only the site
  header, nothing read.
- https://link.springer.com/doi/10.1007/978-3-540-39929-2_26: the
  publisher's page of a 2003 review of XML-compliant user interface
  description languages; redirected to a sign-in, nothing read.
- https://research.dial.uclouvain.be/bitstreams/089753bd-0856-4139-9fbe-d525dbc27fab/download:
  a PDF from the repository of [3]; the fetch could not extract its
  text, the document was not identified, nothing read.

## Search record

Queries, in order:

1. survey user interface description languages
2. W3C model-based user interfaces introduction glossary
3. IFML Interaction Flow Modeling Language OMG specification
4. design handoff definition designers developers
5. why is there no standard for UI specification (the disconfirming
   query)
6. spec-driven development overview 2025 tools Kiro spec-kit
7. survey LLM user interface generation UI representation taxonomy
   2025 arXiv
8. Nielsen Norman Group design handoff annotations specification
   documentation
9. ISO/IEC 25060 Common Industry Format "user interface
   specification" "user interaction specification"
10. DESIGN.md specification format coding agents design system open
    source
11. model-based user interface development past present future survey
    adoption industry failed
12. W3C UI Specification Schema Community Group
13. "design handoff" Interaction Design Foundation OR nngroup what is
    design handoff
14. survey design-to-code UI code generation LLM intermediate
    representation DSL 2025 2026
15. "user interface specification" OR "UI specification" systematic
    review notations practice interviews practitioners
16. Figma Dev Mode documentation handoff "ready for dev" annotations
    help center
17. "user interface description language" 2024 OR 2025 OR 2026 LLM
    agents generative UI declarative specification A2UI overview
18. text-based wireframe DSL comparison overview textual notation for
    specifying user interfaces taxonomy of approaches
19. "design as code" user interface design system 2025
20. "interaction specification" OR "functional specification" user
    interface document UX what is

Pages opened: seventeen fetches. Twelve returned content and are
sources [1] to [12]; one more returned content only as a refusal
(HTTP 403) and three returned nothing readable, the four listed under
Opened and not used. All three items the card said must turn up did:
the W3C's model-based work [1], IFML [2], "design handoff" [12].

The disconfirming query (5) found no page that answers why there is
no standard. Its result list led to the W3C's UI Specification Schema
Community Group, opened as [7] and [8]: called in August 2025, closed
on 21 May 2026, no report listed. With the note status of [1], the
single version of [2] and the report status of [6], this matches what
was expected, several partial standards and no dominant one; nothing
found contradicts it.

Why the run ended: the opening budget. Of the card's stop rule, the
first half was met in substance (queries 14, 15 and 18, differently
worded, brought single systems and the same surveys, no synthesis);
the second half was not: the route of the surveys of description
languages has a bibliographic record only [3], and the route of the
practitioner glossaries has no entry for "design handoff", only the
vendor's documentation [12].
