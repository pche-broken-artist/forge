---
date: 2026-11-21
project: forge
topic: what a description of an interface cites and does not repeat - the mechanisms of reference, what is kept and what is cited, and what is reported about drift
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-18-cites-not-repeats
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 18; the known notes 2026-10-03-how-a-solution-design-is-built.md and 2026-10-13-what-a-brd-contains-and-how-it-is-found-today.md; web sources below
---

# A description of an interface cites what is defined elsewhere by its identifier and keeps what the user sees and does

<!-- Shape: templates/research.md -->

## In short

Established specification practice gives each thing an interface
description would otherwise repeat a home of its own and a handle to
cite it by: a glossary for terms, a data model and data dictionary
for fields, a list of business rules, access requirements, and a
controlled interface document or a machine-readable contract for the
service behind the screen; requirements are cited by identifier and
traced to a parent. Where an interface is described in a form bound
to a schema or a domain model (one W3C Recommendation, three
products, two research prototypes), the reference is a path or a tag
into the data definition, the constraints stay with the data, and
the description keeps the control, its place, its label, help and
error wording and the response to an action; where a condition of
showing or enabling lives is placed differently from source to
source. The mechanisms are well founded (standards, a handbook, a
template, a handbook author's guidance; most pages read through a
summarising fetch, the quotes then compared with the pages). On
drift there is evidence at two levels and a gap between them: one
large industrial study measured duplication inside requirements
specifications (13.6 per cent clone coverage on average, the
interface among the three most often cloned kinds of content), and
one study of six interviews reports that restating in a built
interface what other parts of a system define is a common cause of
defects that static checks miss; no study was found of a written
description of an interface drifting from the documents it cites.
From requirements to the elements of an interface, the two primaries
opened describe the link as missing or made by hand; one of them
(June 2024) has a language model find unimplemented user stories in
a prototype at .85 accuracy and match stories to components at .68.
The disconfirming query, run in both rounds, found named
practitioners calling a hand-kept traceability matrix not worth its
cost outside regulated work and proposing one copy in place of
linked copies, and the research literature saying that tracing is
done after the fact and leaves links incomplete; that leaves
citation by identifier standing and argues against a matrix kept
beside the documents. Unexpected: citations are themselves copied;
one established interface model is used to find rules, not only to
cite them; and developers who fear drift leave a constraint out of
the interface altogether. The note was made in two rounds because
the search tool refused four of seven queries in the first; all were
run in the second. Every route of the card now has a primary source;
the card's stop rule is still not met, since the differently worded
query returned sources that were new.

## Question

The frame of the card:

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

The card:

#### Card 18: What the description cites and does not repeat
- **Question:** How does a description of an interface refer to what
  is defined elsewhere (the data model and its fields, validation
  and business rules, permissions and roles, the states and errors
  of the services behind it) without repeating it: which mechanisms
  of reference does established specification practice use
  (identifiers of requirements, a data dictionary, a contract
  between systems, a shared glossary), what is kept in the
  description of the interface and what is only cited, and what is
  reported about the two drifting apart?
- **Why it matters:** the description will stand beside
  requirements, a solution design and user stories, and the
  framework lets no layer repeat another.
- **What would answer it:** requirements engineering and
  specification practice as its standards and handbooks state it.
- **Where to look:** the literature on traceability from
  requirements to the design of an interface; specification
  templates that keep a data dictionary apart from the screens;
  interface descriptions bound to a service contract or a schema.
  The known notes on the solution design and on business
  requirements.
- **Disconfirming query:** "traceability matrix is waste", "business
  rules duplicated in UI specification"; expected: traceability kept
  by hand decays.
- **Stop rule:** nothing new from a differently worded query and
  every route has a primary source; ten to fifteen pages opened.

What the note must beat. The two known notes already hold the
general rule. The note on the solution design (2026-10-03, findings
4 and 9): upward a document cites by identifier at the item and
keeps no matrix by hand, downward it names the place and leaves the
detail there, and the hand-kept matrix is the form known to decay,
on the strength of an encyclopedia article. The note on the business
requirements document (2026-10-13, findings 5 and 7): links are
recorded as the work is done by whoever knows them, good tools flag
a link as suspect when either end changes, a matrix is a view made
from links that live in the items, and screens inside a requirements
document are solutioning below its line. This note has to add what
those lack: the mechanisms particular to an interface (what its
description can point at in a data definition, a list of rules, a
model of permissions and a service contract), where the line runs
between what it keeps and what it cites, and evidence on duplication
and drift from a primary source.

## Key findings

How the pages were read. The note was made in two rounds; F9 to F11
and the passages marked "second round" come from the second.
Eighteen of the twenty-two sources cited were opened through a fetch
tool that returns a small model's reading of the page; each is a
summarised fetch. Every sentence quoted from them below was
afterwards compared with the text of the page itself and stands
there word for word; what is not in quotation marks is the tool's
reading. Four sources, [11], [14], [19] and [20], were read in full.

**F1. Established practice gives each thing an interface description
would otherwise repeat a home of its own, and each home a handle to
cite it by.** [consensus; evidence: a requirements template, a
systems engineering handbook, two standards, a handbook author's
guidance, two practitioner claims; summarised fetches, quotes
compared, [19] read in full]

| What is defined elsewhere | Its home in the sources | The handle it is cited by |
|---|---|---|
| Terms | the glossary: section 4, "Naming Conventions and Terminology" [1] | the term |
| Data and its fields | the data model and the data dictionary: section 7, apart from the functional requirements (9), look and feel (10) and usability (11) [1]; an appendix or a document of its own [19]; one entry per record and field [2] | the entry's name [19] |
| Business rules | a list of their own: 5b [1]; "record the business rule once" [3] | a reference from the other artefact [3]; no form of identifier is given in the sources opened |
| Permissions and roles | access requirements: 15a under Security [1]; per operation in a service contract [4] | the scope or role name [4] |
| The service behind the interface | a controlled interface document [5]; a machine-readable contract [4] | the operation's identifier [4]; for an error, the URI of its problem type [6] |
| Requirements | the specification above | the requirement's identifier, traced to its parent [7] |

- The template keeps the four homes apart from the sections on the
  product's functions and its look. Its authors on the glossary:
  "Names are very important. They invoke meanings that, if carefully
  defined, can save hours of explanations", and "The glossary
  produced during requirements is used and extended throughout the
  project" (section 4) [1]. The page is the authors' extract; the
  full template is sold, and the extract shows "7b. Data Dictionary"
  and "5b. Business Rules" as headings with no text.
- Second round. The guidance that goes with a standard handbook of
  requirements gives the reason for the separate home: "A data
  dictionary is a shared repository that defines the meaning,
  composition, allows values, and other information for all data
  elements used in an application"; it "can be stored as an appendix
  to the SRS or as a separate document", and "A separate data
  dictionary makes it easy to find the data information readers
  need, and it avoids redundancy and inconsistencies". An entry
  holds the element's name, its description, its composition or data
  type, its length and its values, the last being a "list of allowed
  values, default, rules governing legal values, and any other
  description of the data values"; reference inside the dictionary
  is by name, "Each data item that appears in a structure must
  itself be defined in the data dictionary", and by hypertext from
  one entry to another [19]. The document does not speak of screens.
- One practitioner states the replacement outright: a data
  dictionary "is intended to replace individual detail requirements
  representing those needs" (under "Data Dictionary Information vs
  Detail Requirements"); his template gives an entry about
  twenty-five property columns and a "Comments / Other Business
  Rules" column, so in that practice the rules of a field live in
  the dictionary [2]. The article does not say how a screen refers
  to an entry; it announces a next article on "detail requirements
  for user interfaces and reports", which was not found.
- On rules, a second practitioner: describe a rule in a use case,
  again in a rule specification and again in code and there are
  three versions to maintain; better to "record the business rule
  once" and "reference it from any other artifact as appropriate"
  [3].
- The contract between systems is a document of its own under change
  control: "Types of interface documentation include the Interface
  Requirements Document (IRD), Interface Control Document/Drawing
  (ICD), Interface Definition Document (IDD), and Interface Control
  Plan (ICP)", they are "maintained and approved using the
  Configuration Management Process", and "For interfaces that
  require approval from all sides, unanimous approval is required"
  (6.3.1.3) [5]. The page does not define the four one by one and
  does not say that each side cites the document instead of copying
  it; that reading is this note's.
- The machine-readable form of such a contract gives each operation
  an identifier, "The id MUST be unique among all operations
  described in the API", keeps shared definitions in one place, a
  Components Object that "Holds a set of reusable objects for
  different aspects of the OAS", cites them through a Reference
  Object, "A simple object to allow referencing other components in
  the OpenAPI Description, internally and externally", and states
  who may call an operation: the Security Requirement Object "Lists
  the required security schemes to execute this operation", with
  scope names, or "a list of role names which are required for the
  execution, but are not otherwise defined or exchanged in-band"
  (4.8.30) [4].

**F2. Where an interface is described in a form bound to a schema or
a domain model, the reference is a path or a tag into the data
definition and the constraints stay with the data.** [consensus
across independent forms; evidence: one standard, three products'
own documentation, two research prototypes; summarised fetches,
quotes compared, [11] read in full]

- XForms 1.1, a W3C Recommendation of 20 October 2009, describes
  itself as "an architecture that separates presentation, purpose
  and content" (Abstract) and names as its first difference from
  HTML forms "the separation of the data being collected from the
  markup of the controls collecting the individual values" (section
  2). A form control points at a node of the data by a `ref` path
  or by the name of a `bind` (3.2.3). What holds of the data is said
  on the `bind`, in the model: "Other attributes on element bind
  encode model item properties to be applied to each node in the
  node-set" (3.3.4); the properties defined there include type,
  readonly, required, relevant, calculate and constraint (6.1).
  `required` "describes whether a value is required before the
  instance data is submitted" (6.1.3); `constraint` "specifies a
  predicate that needs to be satisfied for the associated instance
  data node to be considered valid" (6.1.6). The control states none
  of this and must show all of it: "Relevant form controls must
  distinguish rendering between valid and invalid states", and "If a
  form control binds to a readonly node, then the form control must
  not allow the user to modify the node value" (8.1.1) [8].
- JSON Forms keeps a data schema and a UI schema apart. A control
  carries "The mandatory scope property, which expects a JSON schema
  reference value" and "defines to which property of the data the
  control should be bound to"; its example is `"scope":
  "#/properties/name"`. What follows from the data is not restated:
  "How a control is rendered depends on the type of the property as
  defined in the JSON Schema", and "By default, controls use the
  name of property they point to as a label" [9]. The page does not
  say where validation comes from.
- The SAP UI vocabulary goes one step further: the interface is
  described as annotations on the entity types and properties of
  the service itself. It holds "Terms for presenting data in user
  interfaces" and "focuses on usage patterns of data in UIs, not on
  UI patterns, and it is completely independent of the UI
  technologies or devices used to visualize the data"; a list is a
  `LineItem`, a "Collection of data fields for representation in a
  table or list" [10].
- Second round. A framework that draws its interface from the domain
  objects needs no reference at all: "When a domain object is
  rendered in the UI or the end-user interacts with the domain
  object through the UI, the framework applies a series of
  precondition business rules to each object member", and the
  simplest way is "to just implement the business rules imperatively
  in the domain object" [17].
- A proof of concept from a university shows the same at run time:
  a form names only the business operation it serves
  (`data-business-context="Report Issue"`) and its fields, and the
  preconditions of that operation are fetched and turned into
  validation: "There are no validation rules in HTML or in
  Javascript" (section 6). Its author names the price, "significant
  initial project overhead" (section 7) [11].
- Second round. On a drawn mockup the same reference is a tag at the
  element; see F9 [21].

**F3. In those forms the description keeps what the user is shown
and does, and cites what holds of the data; where a condition of
showing or enabling lives is contested.** [the division: consensus
across [8], [9] and [10]; the placement of conditions: contested;
evidence: one standard, products' documentation, one research paper;
summarised fetches, quotes compared]

- Kept with the control: its kind and its place; the label, the help
  and the hint; the wording of the error, "The author-optional
  element alert provides a convenient way to attach alert or error
  information to a form control" (8.2.4) [8]; in a UI schema the
  label and presentation options such as a radio group for an
  enumeration [9].
- Cited, never stated at the control: the type, whether a value is
  required, the constraint, whether the value may be changed [8],
  [9].
- An established requirements model for one screen is built the
  same way round the user: the Display-Action-Response model
  documents "the valid ways in which the system displays the screen
  and how the system responds to the actions that a user can take"
  and "is composed of a combination of UI screen layout and
  corresponding element tables" [13]. The page shows the element
  table as a picture only; what its fields are and whether one of
  them points to a data dictionary could not be read, in either
  round.
- Contested, the placement of one thing. XForms puts the condition
  in the model: `relevant` "indicates whether the model item is
  currently relevant. Instance data nodes with this property
  evaluating to false are unavailable in the user interface and can
  be removed from submission serialization" (6.1.4) [8]. JSON Forms
  puts it in the description of the interface with a pointer into
  the data: "Rules allow for dynamic aspects for a form, e.g. by
  hiding or disabling UI schema elements", a rule "may be attached
  to any UI schema element", and its condition holds a scope and a
  schema, where "The schema is validated against the data specified
  in the scope property" [12]. The SAP vocabulary puts it on the
  contract as an annotation of the property: "Properties or facets
  (see UI.Facet) annotated with this term will not be rendered if
  the annotation evaluates to true", and "The annotation value may
  be an expression to dynamically hide or render the annotated
  feature" [10]. Second round: the framework of [17] sides with the
  model and puts visibility, enabling and validity alike in the
  domain object, and the annotated mockups of [21] write a
  constraint at the element of the mockup. No source opened argues
  for one placement against another.

**F4. The errors of a service have a citable form; what the user is
told about them is not part of it.** [single standard for the error
format, a second for the contract; summarised fetches, quotes
compared]

- A contract is expected to name the cases: its "documentation is
  expected to cover a successful operation response and any known
  errors" (Responses Object, 4.8.16) [4].
- RFC 9457 (IETF, Standards Track, July 2023) defines a problem
  detail "to carry machine-readable details of errors in HTTP
  response content" and makes the kind of error an identifier:
  "Consumers MUST use the "type" URI (after resolution, if
  necessary) as the problem type's primary identifier" (3.1.1). A
  new problem type is to be documented with its URI, a title and the
  status code it goes with (section 4). The human-readable members
  are not the interface's text: the title "is advisory and is
  included only for users who are unaware of and cannot discover the
  semantics of the type URI" (3.1.3), the detail "ought to focus on
  helping the client correct the problem, rather than giving
  debugging information", and "Consumers SHOULD NOT parse the
  "detail" member for information" (3.1.4) [6].
- The RFC, as read, says nothing on what an end user is shown. This
  note's inference: the contract supplies the list of cases and
  their identifiers, and what the screen says and does in each case
  is the interface description's own content, keyed by the
  identifier.

**F5. Traceability as a handbook states it: every requirement traces
to a parent, duplication between levels is to be resolved, and the
record is a matrix or a tool.** [consensus in the handbook
literature opened; evidence: one handbook, one template; summarised
fetches, quotes compared]

- "Traceability: A discernible association between two or more
  logical entities such as requirements, system elements,
  verifications, or tasks", and bidirectional traceability is "The
  ability to trace any given requirement/expectation to its parent
  requirement/expectation and to its allocated children
  requirements/expectations" (6.2, Definitions) [7].
- "Each requirement should be traced back to a parent/source
  requirement or expectation"; one with no parent and no accepted
  reason of its own is either a flawed trace or "gold plating"
  (6.2.1.2.3) [7].
- Repetition down the chain is named a defect in the same breath:
  "Duplication between levels should be resolved. If a requirement
  is simply repeated at a lower level and it is not an externally
  imposed constraint, it may not belong at the higher level" [7].
- The form of the record: "Requirements traceability is usually
  recorded in a requirements matrix or through the use of a
  requirements modeling application" [7]. Contradicted on the
  matrix by [15] and [3]; see F8.
- The template says of itself that it "provides a checklist,
  structure and traceability for your requirements" and asks one
  trace in words: the product use cases "must be traceable back to
  the BUCs", the business use cases (section 8) [1].
- IEEE 830-1998 required a specification to "Not be redundant", as
  [14] relays it; the standard itself was not read.
- For traceability from requirements to the elements of an interface
  in particular, see F9; the first round had opened nothing on it.

**F6. Duplication inside specifications is common where it was
measured, the interface is among the three kinds of content most
often found cloned, and the harm of changing copies unevenly is
strongly suspected, not shown.** [single source; evidence: an
industrial case study of 28 specifications, ICSE 2010; read in full]

- The study ran clone detection over 28 requirements specifications
  of 8,667 pages from 11 organisations, counting word-for-word
  repetitions of at least 20 words. "The average specification clone
  coverage is 13.6%"; it ranges from none in two specifications to
  71.6 per cent in one; six of the 28 lie above 20 per cent; the
  specifications are on average 13.5 per cent longer than they would
  be without the copies (Tables 1 and 2, section 4.1) [14]. The
  figures are "only a lower bound for redundancy", since reworded
  copies are not counted (section 6.1).
- What is copied: of 498 category assignments over 404 inspected
  clone groups, "Detailed Use Case Steps" has 100, "Reference" 64
  and "UI" 63; UI is "Information that refers to the (graphical)
  user interface. The specification of which buttons are visible on
  which screen is an example for this category" (section 4.2). The
  longest clone group is "two clones of 1049 words each, describing
  similar input dialogs for different types of data"; the largest
  holds "domain knowledge about roles involved in contracts that has
  been duplicated 42 times" (section 4.1) [14]. The authors warn
  that these are absolute counts: "we cannot deduce if cloning is
  more likely to occur in one category than another" (section 5).
- What it costs: reading and inspection time (about six more hours
  of inspection for the average specification by the study's
  reckoning), and change: "changes to duplicated information are
  costly and error-prone" (section 9). Inconsistent copies were
  found, yet "since we did not validate that the inconsistencies are
  in fact errors, our results are not conclusive" (section 5). Where
  a cloned passage was followed into the code, it had become cloned
  code or the same function built twice, or had been absorbed by a
  shared abstraction (section 4.3) [14].
- What the authors advise: the growth "could often be avoided by
  cross references or different organization of the specifications"
  (section 5); and where a part is repeated on purpose to stand
  alone, "make sure that the duplicated part is maintained only once
  (e. g, by using a macro mechanism in the text processor) and that
  readers can recognize the duplication as such" (section 9). Their
  threshold of 5 per cent as a warning sign is given as "our
  personal opinion" [14].
- A side remark of the same study bears on the links themselves: for
  the step into the code a random sample was impossible because "for
  many study objects, the source code is unavailable or traceability
  between SRS and source code is too poor" (section 3.4) [14]. It is
  a remark on method, not a measured result.

**F7. One rule is applied at several moments of an interface, which
is where a description is drawn into restating it.** [three
independent sources agree on the mechanism, none measures it;
evidence: a student conference paper with a proof of concept, a
framework's documentation, a conference paper; [11] and [20] read in
full, [17] a summarised fetch with quotes compared]

- The paper follows one precondition of a business operation through
  a request: it validates the input in the client, is applied again
  at the entrance to the application layer, and once more "when we
  render UI, we apply preconditions again to hide components and
  action buttons for which the user does not fulfill security
  requirements" (section 2). Validation, a business rule and a
  permission are here one rule seen at three moments [11].
- Its claim on drift is an assertion with citations, not a result:
  current approaches "repeat conditions throughout the whole system,
  from the UI through business services to the persistence layer",
  and "Keeping all places synchronized is very error-prone and
  requires significant efforts"; rules are hard to maintain in many
  places "especially when a single field may occur in multiple
  views, forms, layouts" (sections 1, 2 and 5). The evaluation it
  leans on is its authors' own earlier paper, which was not read
  [11].
- Second round. A framework's documentation sorts its rules by the
  same moments, in the order the user meets them: "is the object
  member visible?", then "is the object member enabled?", then "are
  the supplied values valid"; "These can be summarised as "see it,
  use it, do it"" [17]. A third source lists the same points on one
  form: label, type, greatest length, required, least and greatest
  value, the values of an enumeration, read-only, and which action a
  button may take [20]; see F10.

**F8. The disconfirming query: named practitioners call the
hand-kept matrix not worth its cost and propose one copy in place of
linked copies; they keep traceability where regulation asks for
it.** [contested; evidence: practitioner claims, through a news
report of a mailing-list discussion and one essay; no study;
summarised fetches, quotes compared]

- A news item of 6 June 2008 reports the discussion. Scott Ambler,
  as quoted there: "traceability matrices are highly overrated
  because the total cost of ownership (TCO) to maintain such
  matrices, even if you have specific tools to do so, far outweigh
  the benefits", and "I'm a firm believer in traceability if you
  have actual regulatory compliance needs". Alistair Cockburn, as
  quoted there, of a project that costed the tool and the labour:
  "The cost was so staggeringly high that the client removed the
  traceability requirement from the contract", and he had "NEVER
  seen a traceability matrix pay off". Mike Beedle, as quoted
  there: "traceability from code/design to requirements is done
  through unit and acceptance tests" [15]. The item is a secondary
  source; the original posts were not opened.
- Ambler's own essay gives the reasoning: "you want to record
  information as few times as possible, ideally only once", because
  "With multiple copies the greater your traceability needs will be
  because you'll need to relate each version to its alternate
  representations". It also gives the limit: "you'll never truly be
  able to fully single source all of your software artifacts", and
  "it isn't realistic to expect business stakeholders to be able to
  read program source code". Its executable form: "your customer
  acceptance tests are not only tests they are also requirements
  specifications" [3].
- Contradicted by [7], which requires bidirectional traceability and
  names the matrix as its usual record. Both stand: the handbook
  speaks for work under formal control, the practitioners for work
  without it, and the practitioners themselves except regulated
  work.
- What it did to the answer. The expectation of the card, that
  traceability kept by hand decays, is met as a claim about cost by
  named practitioners; no measurement of decay was opened. Nothing
  found argues against citing by identifier at the item; the
  argument is against a second artefact that has to be kept in step.
- Second round. The query was run again as the card words it, in two
  searches. "traceability matrix is waste" returned the same debate:
  the magazine article behind it, whose host again did not resolve,
  [15], vendors' pages and one practitioner's post on why matrices
  die; nothing of standing that had not been seen. "business rules
  duplicated in UI specification" returned [11], [20], [17] and posts
  on business code in the interface as a fault of code: sources on
  built systems, none on a written specification. One result, seen
  and not opened, is an old newsgroup post arguing that validation
  in the interface should be a hard-coded copy; it is no finding.
  The research literature now stands beside the practitioners; see
  F11.

**F9. From requirements to the elements of an interface, the two
primaries opened describe the link as missing or made by hand, and
both put it at the element.** [emerging; evidence: a preprint with
an evaluation on 210 pairs (2024), a conference paper with an
experiment on 34 developers (2018); summarised fetches, quotes
compared; second round]

- The preprint of 12 June 2024 starts from the cost of the missing
  link: "Time and effort lie in recognizing whether requirements
  have already been implemented and then implementing new
  requirements in GUI prototypes", and "to the best of our
  knowledge, there exists no approach that automatically checks
  requirements (e.g., in the popular form of user stories) against
  implemented components in GUI prototypes". Its approach "aims to
  detect functional user stories that are not implemented in a GUI
  prototype and provides recommendations for suitable GUI components
  directly implementing the requirements" [16].
- What it measured, with a general language model reached in
  February 2024: whether a story is realised in a given interface,
  accuracy .852 without examples, on 210 pairs of a user story and
  an interface; which components realise a story, micro-F1 .681,
  and "the matching task is significantly more difficult for the
  LLMs". The interfaces are 60 screens of mobile applications, "our
  used data set lacks non-mobile GUIs", and the 231 user stories
  were written afterwards for interfaces that existed; the
  recommendations were shown to be feasible, not measured [16]. The
  figures carry the date of the paper.
- The paper of 2018 writes the link on the mockup. Each element is
  annotated in an "End User Grammar", "which focuses on describing
  information source, format and information relationships": a tag
  "Denotes that an object or a list of objects of class Class is
  shown or can be manipulated in the UI", another names the
  attribute and its type, another gives a mockup an identifier "in
  order to be referenced as a destination for navigation/activation
  by other tag" (section 3.2) [21].
- Its evidence: 34 developers, 18 with annotated mockups and 16 with
  plain ones; the annotated group read the requirements more
  precisely and more completely, "In all cases, the p-value was
  lower than the alpha level 0,05", with effect sizes "bigger than
  0.474"; the authors add that "it is required more validation to
  support stronger claims", and the tool that would process the
  annotations was still being built (sections 4 and 5) [21]. The
  table of precision and recall was not read.
- In [21] a tag also states a rule: the example carries "an
  annotation specifying that the quantity of a Product Purchase
  should be 1 as a minimum". The mockup is there a place where
  requirements are written, not only cited, and the paper's subject
  is the conflicts between mockups that follow.
- The same paper states the drift as a premise and cites it: "large
  textual descriptions present in documents and the requirement
  change volatility make it impossible to keep artefacts updated and
  consistent" (section 1) [21].
- A space agency's software engineering handbook has a requirement
  on bidirectional tracing between software requirements and
  software design, by the title of its page; the page refused the
  fetch at two addresses and nothing is cited from it.

**F10. In built systems, restating in the interface what other parts
define is reported as a common cause of defects that static checks
miss; the evidence is a worked example and six interviews.** [single
source; evidence: a conference paper of 2009 with six practitioner
interviews, by authors who were building a tool against the problem;
read in full; second round]

- The thesis: treating the interface as separable "leaves the UI
  having to restate invariants already specified in other subsystems
  of an application, and any discrepancy between the versions in the
  UI and those in the subsystems leads to errors" (Abstract); what
  is restated is "names and types of fields, validation constraints
  and actions" (section I) [20].
- The count on one form: "there are over twenty 'points of
  duplication' with other subsystems for only a simple UI screen
  with 5 fields" (section IV); the list is the one given in F7.
- What the paper leaves to the interface as its own: wording that
  differs from the name of the field; the choice of widget, where
  "There is some flexibility here, but only a little"; and an
  abstraction such as one field shown as two, which is "the
  exception, not the norm" (section IV) [20].
- The evidence: "6 interviews with senior software development
  practitioners from different segments of industry", in three
  countries. "All of the interviewees responded that such defects
  were common." Not all named the duplication unprompted; some did
  only after a probe question the authors themselves mark as biased
  (section V) [20].
- Why the defects last: "these errors can rarely be identified
  statically, such as at compile-time or during application startup.
  The developer must rely on runtime testing to expose them"
  (section IV) [20].
- Two remarks that bear on a description that cites. A restatement
  that can be checked is better than one that cannot: of a mapping
  file that names a property a second time, "the duplication is at
  least able to be validated", which is "an important step in
  reducing the margin for error, even if it doesn't reduce the
  duplication itself" (section III.B). And in code the repetition is
  sometimes required; one interviewee: "you need to validate it both
  in the UI and at the persistence layer if that's a business rule,
  so it's always a problem" (section V) [20].
- The level is code, not specification: the paper compares an
  interface as built with the subsystems of the same application.

**F11. The research literature says of practice what the
practitioners of F8 say: tracing is done after the fact, costs
effort and leaves links incomplete.** [consensus as a statement in
the literature opened, no measurement of decay; evidence: the
abstract of the field's roadmap paper (2014), the introduction of a
preprint (2023) that describes a firm selling automated tracing;
summarised fetches, quotes compared; second round]

- The roadmap of the research community: traceability is "a
  sought-after, yet often elusive quality in software-intensive
  systems", and "In practice, traceability is often conducted in an
  ad-hoc, after-the-fact manner and, therefore, its benefits are not
  always fully realized" [22]. Only the abstract was read.
- The preprint: "creating and maintaining trace links is an
  effort-intensive, time-consuming, error-prone task", "As a result,
  many projects are left with incomplete and inaccurate trace
  links", and "many industry projects in non safety-critical domains
  do not contain any trace links at all due to the additional time
  required to trace artifacts throughout the development process";
  in one public data set it found 26 artifacts with no link and
  reads them so: "orphan artifacts are likely a sign of forgotten
  links" (sections 1, 4.1 and 4.4) [18]. The first two statements
  rest on citations that were not read, and the paper presents a
  firm whose product is automated tracing: an interested source.
- Neither measures links going stale as documents change.

## Unexpected

Citations are themselves copied. In [14] "Reference", a "Fragment in
a requirements specification that refers to another document or
another part of the same document", is the second most frequent kind
of cloned content, one assignment ahead of the interface. A
cross-reference written out as a sentence at every place of use is
duplicated text like any other. The lead, and this note's inference:
a citation should be a bare identifier, and whatever is said about
the cited thing belongs at the thing.

The card assumes that what the description cites is defined
elsewhere before the interface is described; [13] says the interface
model is also where it is found: "DAR models are used to derive
requirements and business rules associated with the UI." A rule
first seen while a screen is being described then has no home above
yet. The second round adds a case: in [21] the constraint is written
on the mockup itself. The card is still answered as put; what this
adds is a direction of flow from the description upward.

Several of the schema-bound forms have no separate description of
the interface for much of its content: in [10] what a list shows,
what identifies an object and what is hidden are annotations on the
service's own definition, and in [17] and in the tool the authors of
[20] were building the interface is drawn from the definitions. For
the idea under test in the frame, an element with a definition of
its own, this is the opposite pole: the field's definition carries
its presentation. A lead for the cards on declarative interface
languages and on pages composed of blocks.

Fear of drift leads to leaving the rule out (second round). In [20]
"developers may choose to simply omit the duplication rather than
risk it becoming inconsistent over time"; the example is a field
built with no limit of length, in the hope that validation elsewhere
catches the overflow. The lead, and this note's inference: a
description that says nothing where it should cite reads to a
builder like no rule at all, so silence and citation have to be told
apart.

A model can recover part of the link that was not written (second
round). In [16] a general language model decides whether a user
story is realised in an interface at .85 accuracy and names the
components at .68. A lead for the cards on the agent that proposes a
description and on how a proposal is judged: coverage of stories can
be checked by a model, while the link at the element is the weaker
half and is better written than recovered. The second half is this
note's inference from two figures of one preprint on mobile screens.

## Not found

- A survey of traceability from requirements to the elements of an
  interface design. The second round found two primaries ([16],
  [21]) and no synthesis; a handbook requirement on tracing
  requirements to design and a repository paper on mockups and
  requirements traceability refused the fetch.
- A study of a written description of an interface drifting from the
  data dictionary, the rules or the contract it cites. [14] measures
  duplication inside requirements specifications; [20] reports
  defects between an interface as built and the rest of a system;
  [11] asserts the same.
- A measurement of traceability links decaying over time. [22] and
  [18] state the condition and do not measure it. The classic paper
  on the traceability problem (Gotel and Finkelstein, 1994) and the
  article "The Trouble with Tracing: Traceability Dissected" could
  not be opened in the first round; the magazine article "Don't
  Enter the Matrix" in neither.
- ISO/IEC/IEEE 29148 and IEEE 830 at source; both are sold. One
  phrase of IEEE 830 is relayed by [14].
- The Business Rules Manifesto, the primary statement that a rule is
  stated apart from the process that enforces it; its host refused
  the connection in the first round.
- The fields of the Display-Action-Response element table and
  whether it points to a data dictionary: [13] shows the table as a
  picture; the book chapter that defines it (Beatty and Chen, 2012,
  chapter 15) refused the fetch; a post of the same firm that a
  search summary describes as listing name, identifier, description,
  display and behaviour for each element returned not found. The
  summary is no finding.
- What the standard handbook of requirements says on where the
  design of an interface stands beside the requirements
  specification. The query worded for it returned the book's
  chapters in a publisher's library, which had refused the fetch,
  and sample files that were not opened; [19] is its guidance on
  the data dictionary only.
- A model of roles and permissions kept as a document of its own and
  cited from screens. Only a heading in [1] and the role names of
  [4] were found.
- A citable form for the states of a service that are not errors
  (loading, empty, stale, partial). [4] and [6] cover responses and
  errors.
- How the spec-driven kits of 2024 to 2026 make a description of an
  interface cite a data model or a contract. Not searched in either
  round; the known note of 2026-10-03 records only that one kit
  keeps a data model and contracts beside its plan.
- The article announced in [2] on detail requirements for user
  interfaces.

## Options

How a citation is made:

- **A. An identifier at the element.** The description names the
  requirement, the rule, the field, the role, the operation and its
  errors by the identifier each already has (F1, F5); the two
  primaries on interfaces put the link there too (F9). Cheap, local,
  checkable by a script (does the identifier exist). The reader,
  human or agent, has to open the cited document to know what the
  identifier says.
- **B. A path into a machine-readable definition** (F2): a pointer
  into a schema, an operation's identifier in a contract. The
  strongest check, and the form the tools of [8], [9] and [10] run
  on. It needs the data model or the contract to exist in a
  machine-readable form; in a chain of Markdown documents where
  nothing is implemented they are prose.
- **C. Citation in the source, the cited text set in when a render
  is made.** The description holds identifiers only; a generated
  output for the build stage carries the cited definitions beside
  them, marked as copies. This is the advice of [14] for deliberate
  repetition: kept once, recognisable as a copy. The cost is a
  render to regenerate and a reader who must know that the render is
  no source.
- **D. A matrix kept beside the documents** (F5, [7]). The form
  asked for under formal control and the one whose cost the
  practitioners of F8 reject; the known note of 2026-10-13 already
  treats a matrix as a view made from the links in the items.
- **E. Repetition.** The measured habit (F6) and, in built systems,
  the reported cause of defects (F10). It keeps each part readable
  alone and is the cause of the drift the card asks about.
- **F. No separate description: the interface drawn from the
  definitions** ([10], [17], the tool of [20]). Nothing is cited
  because nothing is restated. It presupposes definitions a machine
  can read and something that draws from them, and it leaves to a
  description only what cannot be drawn: the layout, the wording,
  the exceptional abstraction.

What the description keeps and what it cites, as a division by kind
(F2, F3, F4, F10):

- keeps: what stands on the screen and where; what each element is
  for; the wording shown (labels, help, hints, the message for each
  error); what happens on each action; the states of the screen as
  the user meets them;
- cites: the definition of a field (type, length, valid values,
  whether required); validation and business rules; who may see or
  do; the operation called and its named errors; the terms;
- open: the condition under which an element is shown, hidden,
  enabled or read-only. The sources place it in the data model, in
  the description with a pointer, on the contract, or on the mockup
  (F3).

Where the cited things live. The practice of F1 assumes a glossary,
a data dictionary, a list of rules, access requirements and a
contract as homes of their own; for the data dictionary the guidance
of [19] allows an appendix of the specification or a document of its
own and prefers the second. The frame names requirements, a solution
design and user stories. Either those documents already hold such
homes with identifiers, or they are given them, or the description
of the interface becomes the home by default, which is what F6 and
the second lead under Unexpected describe.

## Relevance to this project

A proposal; every point is the principal's to decide.

1. Cite at the element by the identifier the cited thing already
   has (option A). It rests on F1, F2, F5 and F9 and on both known
   notes; it is chosen against a matrix kept beside the documents
   (F8, F11) and against repetition (F6, F10).
2. Check the citations by a script, every cited identifier existing,
   and keep no matrix; [20] counts a restatement that can be checked
   as the first gain. For the build stage consider option C: a
   generated output that sets the cited definitions in, marked as
   copies. This note's inference from the advice of [14]; no source
   opened shows it done for an interface.
3. Keep in the description only what no other document can hold: the
   division under Options. It rests on F3, F4 and on what [20]
   leaves to the interface as its own.
4. Decide once where a condition of showing or enabling lives, since
   the sources disagree (F3). This note's inference, offered as a
   test and not as a finding: a condition that would hold whatever
   the interface looked like (who may, when a field applies) is a
   rule and is cited; a condition that exists only because of the
   layout is the description's own.
5. Before a description is written, see that what it will cite has a
   home and an identifier. Where the home is missing the description
   will hold the rule itself, and a rule found while a screen is
   described belongs above first.
6. Write a citation as a bare identifier (Unexpected, first lead).
7. Let an element that shows or enforces a cited rule say so by
   citing it; where it says nothing, a builder may build nothing
   (Unexpected, fourth lead). This note's inference.

Chosen against option B: it needs definitions a machine can read,
which the chain does not have; it becomes possible wherever the
solution design holds a schema or a contract. Option F is out of
reach for the same reason and marks where the field's tools have
gone.

For the idea under test in the frame, this note's inference only: an
element with a definition of its own is the one place where its
citation can stand, since "a single field may occur in multiple
views, forms, layouts" [11]; a page would then cite the element and
the element the field, the rule and the operation. Whether the idea
holds is another card's question.

For the agent that proposes a description, this note's inference
from [16]: whether every user story is met by some screen can be
asked of a model with fair accuracy; which element meets it is the
weaker answer, so the citation written at the element is what makes
that check cheap.

How sure. The mechanisms rest on standards, a handbook, a template
and a handbook author's guidance. The division of content rests on
independent schema-bound forms, none of them a prose specification.
Drift rests on one study of duplication in specifications, one study
of six interviews on built interfaces, and statements of cost by
practitioners and researchers; nothing measures a written
description drifting from what it cites. All seven queries of the
card have now run; the differently worded one still brought sources
that were new, so a source contradicting any of this may exist
unseen.

Consult when: the definition and the template of an interface
description are drafted; it is decided what an element or a page may
cite and in what form; a check on citations is designed; it is asked
whether the chain needs a data dictionary, a list of rules or a
model of permissions; the documents are prepared for a build agent
that will not open what is only cited; a description is found
restating a rule, or silent where a rule applies.

## Sources

Sources 1 to 15 were opened in the first round, 16 to 22 in the
second.

1. *Volere Requirements Specification Template: Extracts and Samples
   from the Template*, Edition 20. James and Suzanne Robertson, the
   Atlantic Systems Guild. Undated; the page's copyright line reads
   2019.
   https://www.volere.org/templates/volere-requirements-specification-template/
   Kind: primary (the authors' own template; the page is their
   extract, the full template is sold). Read: summarised fetch of
   the whole page, the quoted sentences and headings then compared
   with the page text. Original.
2. *Managing Data-Specific Business Needs Using a Data Dictionary*
   (Requirements In Context, Part 5). Dan Tasker, in Modern Analyst.
   Undated on the page; the paths of its images carry 17-09-2019.
   https://www.modernanalyst.com/Resources/Articles/tabid/115/ID/5439/Managing-Data-Specific-Business-Needs-Using-a-Data-Dictionary.aspx
   Kind: primary for the author's own practice, a practitioner
   article in a trade magazine. Read: summarised fetch of the whole
   page, twice, quotes compared with the page text. Original.
3. *Single Source Information: An Agile Core Practice for Effective
   Documentation*. Scott W. Ambler, on the site of the Agile
   Modeling method. Undated; the footer's copyright line reads
   2002-2026.
   https://agilemodeling.com/essays/singleSourceInformation.htm
   Kind: primary for the author's position, a practitioner essay on
   his own method. Read: summarised fetch of the whole page, quotes
   compared with the page text. Original.
4. *OpenAPI Specification v3.1.1*. The OpenAPI Initiative. 24 October
   2024, dated by the title block.
   https://spec.openapis.org/oas/v3.1.1.html
   Kind: primary (standard). Read: summarised fetch in three parts
   that together cover the page, for the Operation, Components,
   Responses, Link, Reference, Schema and Security Requirement
   Objects; quotes compared with the page text. Original.
5. *6.3 Interface Management*, NASA Systems Engineering Handbook,
   web edition. NASA. "Page Last Updated: Jul 26, 2023", dated by
   the page footer.
   https://www.nasa.gov/reference/6-3-interface-management/
   Kind: primary (handbook). Read: summarised fetch of the whole
   page, quotes compared with the page text. Original.
6. *RFC 9457: Problem Details for HTTP APIs*. M. Nottingham, E.
   Wilde, S. Dalal; IETF, Standards Track. July 2023, dated by the
   RFC's header.
   https://www.rfc-editor.org/rfc/rfc9457.html
   Kind: primary (standard). Read: summarised fetch of the whole
   page, quotes compared with the page text. Original.
7. *6.2 Requirements Management*, NASA Systems Engineering Handbook,
   web edition. NASA. "Page Last Updated: Jul 26, 2023", dated by
   the page footer.
   https://www.nasa.gov/reference/6-2-requirements-management/
   Kind: primary (handbook). Read: summarised fetch of the whole
   page, quotes compared with the page text. Original.
8. *XForms 1.1*. W3C Recommendation, 20 October 2009, dated by the
   status line.
   https://www.w3.org/TR/xforms11/
   Kind: primary (standard). Read: partially, by summarised fetch:
   the Abstract and chapters 1 to 3, and chapter 8 with the
   neighbouring parts of chapters 7 and 9; the sentences quoted from
   chapter 6 were found in the page text when the quotes were
   compared. Original.
9. *Controls*, JSON Forms documentation. EclipseSource. Undated; the
   footer's copyright year is 2026.
   https://jsonforms.io/docs/uischema/controls
   Kind: primary (a vendor's documentation of its own product).
   Read: summarised fetch of the whole page, quotes compared with
   the page text. Original.
10. *UI Vocabulary* (namespace com.sap.vocabularies.UI.v1), in the
    repository SAP/odata-vocabularies, main branch. SAP. Undated.
    https://raw.githubusercontent.com/SAP/odata-vocabularies/main/vocabularies/UI.md
    Kind: primary (a vendor's documentation of its own product).
    Read: partially, by summarised fetch: the head of the file and
    the terms HeaderInfo, LineItem, FieldGroup, Identification,
    Hidden and DataField; quotes compared with the file text.
    Original.
11. *Context-aware Input Validation in Information Systems*. Karel
    Cemus, Czech Technical University; the student conference POSTER
    2016, Prague, 24 May 2016, dated by the running head.
    https://poster.fel.cvut.cz/poster2016/proceedings/Section_ICS/ICS_083_Cemus.pdf
    Kind: primary (a conference paper with a proof of concept). Read:
    in full, five pages, the PDF as fetched. Original.
12. *Rules*, JSON Forms documentation. EclipseSource. Undated; the
    footer's copyright year is 2026.
    https://jsonforms.io/docs/uischema/rules
    Kind: primary (a vendor's documentation of its own product).
    Read: summarised fetch of the whole page, quotes compared with
    the page text. Original.
13. *Display-Action-Response Models*. ArgonDigital, the firm of the
    model's authors. Undated; the footer's copyright year is 2026.
    https://argondigital.com/resource/tools-templates/systems-models/display-action-response-models
    Kind: primary for what the model is (its owner's description of
    its own method), a vendor's page. Read: summarised fetch of the
    whole page, quotes compared with the page text; the template and
    the example are pictures and were not read. Original.
14. *Can Clone Detection Support Quality Assessments of Requirements
    Specifications?* E. Juergens, F. Deissenboeck, M. Feilkas, B.
    Hummel, B. Schaetz, S. Wagner, C. Domann, J. Streit. ICSE '10,
    2 to 8 May 2010, dated by the paper's copyright block.
    https://teamscale.com/hubfs/26978363/Publications/2010-can-clone-detection-support-quality-assessments-of-requirements-specifications.pdf
    Kind: primary (an industrial case study). Read: in full, ten
    pages, the PDF as fetched. A copy: the paper as hosted by the
    first author's company; the publisher's page was not opened.
15. *Traceability Matrix in an Agile Project*. Vikas Hazrati, InfoQ.
    Jun 06, 2008, dated by the byline.
    https://www.infoq.com/news/2008/06/agile-traceability-matrix
    Kind: secondary (a news report of a mailing-list discussion; the
    posts it quotes were not opened). Read: summarised fetch of the
    whole page, quotes compared with the page text. Original.
16. *Interlinking User Stories and GUI Prototyping: A Semi-Automatic
    LLM-based Approach*. K. Kolthoff, F. Kretzer, C. Bartelt, A.
    Maedche, S. P. Ponzetto. arXiv 2406.08120, version 1, 12 June
    2024, dated by the page's stamp; no venue is named on the page.
    https://arxiv.org/html/2406.08120v1
    Kind: primary (a preprint with an evaluation). Read: summarised
    fetch of the whole page, quotes and figures compared with the
    page text. Original.
17. *Business Rules*, User Guide of Apache Causeway, version 3.0.0.
    The Apache Software Foundation. Undated; dated only by the
    version.
    https://causeway.apache.org/userguide/3.0.0/business-rules.html
    Kind: primary (a project's documentation of its own product).
    Read: summarised fetch of the whole page, quotes compared with
    the page text. Original.
18. *Understanding the Challenges of Deploying Live-Traceability
    Solutions*. K. R. Dearstyne, A. D. Rodriguez, J. Cleland-Huang,
    University of Notre Dame. arXiv 2306.10972, version 1, 19 June
    2023, dated by the page's stamp.
    https://arxiv.org/html/2306.10972v1
    Kind: primary (a preprint); it describes a firm that sells
    automated tracing, and its statements on practice are
    introductory, with citations that were not read. Read:
    summarised fetch of the whole page, quotes compared with the
    page text. Original.
19. *Guidance for Data Dictionaries*. Karl Wiegers; the footer reads
    "Copyright © 2013 by Karl Wiegers and Seilevel"; dated by that
    line and by the file's properties (created 2 April 2013). By the
    folder it lies in, material that goes with chapter 13 of the
    author's handbook of requirements; the book was not opened.
    https://people.eecs.ku.edu/~saiedian/812/Project/Wiegers-Resources/Chapter%2013/Guidance%20for%20Data%20Dictionaries.docx
    Kind: primary (the author's own guidance). Read: in full, three
    pages, the text taken from the file as fetched. A copy: the
    document as kept on a university course page; the place of first
    publication was not opened.
20. *Separation Anxiety: stresses of developing a modern day
    Separable User Interface*. Richard Kennard, Ernest Edmonds, John
    Leaney, University of Technology, Sydney. 2nd Conference on
    Human System Interactions (HSI '09), May 2009, dated by the
    publisher's notice on the cover page.
    https://opus.lib.uts.edu.au/bitstream/10453/11944/1/2009001883OK.pdf
    Kind: primary (a conference paper with six interviews). Read: in
    full, nine pages, the PDF as fetched. A copy: the paper as
    posted in its authors' university repository with the
    publisher's permission; the publisher's page was not opened.
21. *Improving Mockup-Based Requirement Specification with End-User
    Annotations*. M. Urbieta, N. Torres, J. M. Rivero, G. Rossi, F.
    J. Dominguez-Mayo. Agile Processes in Software Engineering and
    Extreme Programming (XP 2018), pages 19 to 34; first online 17
    May 2018, dated by the page; open access.
    https://link.springer.com/chapter/10.1007/978-3-319-91602-6_2
    Kind: primary (a conference paper with an experiment). Read:
    summarised fetch of the whole page, quotes compared with the
    page text; the table of results was not read. Original.
22. *Software traceability: Trends and future directions*. J.
    Cleland-Huang, O. C. Z. Gotel, J. Huffman Hayes, P. Mäder, A.
    Zisman. Future of Software Engineering, FOSE 2014, pages 55 to
    69; published 31 May 2014, dated by the record.
    https://scholars.uky.edu/en/publications/software-traceability-trends-and-future-directions/
    Kind: primary for the abstract. Read: the abstract only, by
    summarised fetch, the quote compared with the page text. A copy:
    the record of the paper in the research portal of one author's
    university; the publisher's page refused the fetch.

Not opened; nothing is cited from these, and no address is given
because none of them opened.

First round:

- The Business Rules Manifesto, Business Rules Group: the host
  refused the connection.
- J. Beatty and A. Chen, *Visual Models for Software Requirements*
  (2012), chapter 15, in a publisher's online library: refused (403).
- "Don't Enter the Matrix", Dr. Dobb's: the host name did not
  resolve.
- O. Gotel and A. Finkelstein, "An Analysis of the Requirements
  Traceability Problem" (1994), on its second author's university
  page: the host refused the connection.
- "The Trouble with Tracing: Traceability Dissected", Agile
  Connection: redirects to the front page of another site.
- Two pages guessed on the site of [13], for the data dictionary and
  for the roles and permissions matrix of the same modelling
  language: not found (404).

Second round:

- NASA Software Engineering Handbook, SWE-059, Bidirectional
  Traceability Between Software Requirements and Software Design:
  refused (403) at two addresses.
- A post on Display-Action-Response models for user interface
  requirements on the site of [13]: not found (404).
- "Don't Enter the Matrix", Dr. Dobb's, at a second host name: the
  name did not resolve.
- A paper on mockups, requirements traceability and model-driven
  development, as a file in a repository of open papers: refused
  (403).
- The publisher's page of [22]: refused (403).

## Opened and not used

- First round: none.
- Second round: the category listing of the blog of the firm of
  [13], reached when the address of the post on
  Display-Action-Response models was tried with a closing slash: off
  the question, it lists other posts. No address is given.

## Search record

Why there were two rounds. In the first round the session's search
budget was used up and the search tool refused four of the seven
queries tried; the note then said what could not be searched. When
the tool worked again the run was resumed for a second round: the
four refused queries, the disconfirming query as the card words it,
one differently worded query, and at most eight further pages.

First round, queries in order:

1. user interface specification, reference to data dictionary and
   business rules in place of repeated requirements. Ran: practitioner
   posts, course slides, [11], [2].
2. traceability from requirements to user interface design elements,
   literature. Refused: the session's search budget was used up.
3. display-action-response model, data dictionary, UI element
   requirements. Refused, the same.
4. The disconfirming query, as one search: "traceability matrix"
   waste agile, or "business rules" duplicated in UI specification.
   Ran.
5. "display-action-response" model, UI element table, "data
   dictionary". Ran: [13] and the book chapter.
6. user interface design in a software requirements specification,
   data dictionary and business rules referred to, not duplicated.
   Refused.
7. "Software Traceability: Trends and Future Directions". Refused.

Three queries ran of seven. Because of that, primaries whose
addresses were known were opened directly and not found by search
([1], [3] to [10], [12]).

First round, pages opened, fifteen, in order: [8], [9], [6], [7],
[5], [1], [11], [4], [14], [13], [3], [2], [15], [10], [12]. [4] was
read in three parts and [8] in two, [2] twice. [11] and [14] are PDF
files the fetch tool could not read; the files it fetched were read
directly. Seven more addresses were tried and did not open.

First round, results seen and not opened, by kind: posts of vendors
on their own market (two on requirements traceability by the firm of
[13], one on an extended data dictionary by a data consultancy, two
on user interface specifications by training firms), encyclopedia
articles, course slides, posts on community sites, patents.

Second round, queries in order; all seven ran:

1. traceability from requirements to user interface design elements,
   literature (the first round's query 2). Brought the handbook
   requirement that refused the fetch, a review of traceability
   before the requirements specification, an older survey, a paper
   that links regulations to code through the labels of an
   interface; nothing on the elements of an interface as such.
2. display-action-response model, data dictionary, UI element
   requirements (query 3). Brought [13] again, the post that
   returned not found, the book chapter, a glossary, publishers'
   sample files.
3. user interface design in a software requirements specification,
   data dictionary and business rules referred to, not duplicated
   (query 6). Brought [19], the book's chapters in a publisher's
   library, sample files, checklists.
4. "Software Traceability: Trends and Future Directions" (query 7).
   Brought [22], the publisher's page, an aggregator's copy, [18],
   the research community's report on grand challenges.
5. The disconfirming query, first phrase: "traceability matrix is
   waste".
6. The disconfirming query, second phrase: business rules duplicated
   in UI specification. Brought [20] and [17].
7. The differently worded query: linking GUI mockups and wireframes
   to requirements and a domain model, trace links, model-based user
   interface, study. Brought [16], [21] and further papers on
   mockup-driven development and on linking requirements to
   prototypes that were not opened.

Second round, pages opened, eight, in order: [16], [17], [18], [19],
the blog listing that was not used, [20], [21], [22]. [19] is a Word
file and [20] a PDF file the fetch tool could not read; the text of
[19] was taken from the file as fetched and [20] was read directly.
Six more addresses were tried and did not open; they are listed
under Sources.

Second round, results seen and not opened, by kind: a 2023 review
and a 1995 survey of requirements traceability, the report on grand
challenges of traceability, an aggregator's copy of [22], papers on
mockup-driven development and on requirements linked to prototypes,
a paper on regulations traced through interface labels, vendors'
pages on the traceability matrix, a practitioner's post on why
matrices die, encyclopedia articles, sample files of two books on
requirements, a glossary, posts on business code in the interface, a
newsgroup post, product documentation on validation shown in an
interface.

After the last opening of each round every cited address was
requested once more by a plain scripted client, to see that it
answers, and the quoted sentences were compared with the page texts.
At the end of the second round all twenty-two answered the default
client of curl. [2], [14] and [22] refuse a client that names itself
Python-urllib (403), and [13] one that names itself python-requests.

The disconfirming query. First round: it found the debate of 2008 on
the matrix in agile work ([15]) and, through it, the essay [3]: the
matrix is called not worth its cost by named practitioners, who keep
traceability where regulation asks for it and propose one copy and
executable tests. Second round, as the card words it: the first
phrase returned the same debate and nothing of standing that was
new; the second returned sources on built systems ([20], [17], [11])
and none on a written specification. Neither round found a
measurement of decay. With [22] and [18] the expected result, that
traceability kept by hand decays, stands as a statement of
practitioners and researchers alike and as no one's measurement.

Why the run ended. The first round ended on its opening budget,
fifteen pages. The second round ended on its allowance of eight
further pages, which makes twenty-three in all, above the card's ten
to fifteen. The card's stop rule is not met. One half of it is:
every route now has a primary source, the route on traceability from
requirements to the design of an interface in [16] and [21], the
templates that keep a data dictionary apart in [1] and [19], the
descriptions bound to a contract or a schema in [4], [8], [9], [10]
and [17]. The other half is not: the differently worded query
returned sources that were new, two of them opened and several left
unopened, so "nothing new" cannot be said.
