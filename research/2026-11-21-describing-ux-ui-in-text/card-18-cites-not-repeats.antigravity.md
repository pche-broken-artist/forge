---
date: 2026-11-21
project: forge
topic: what a description of an interface cites from other documents and does not repeat
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 18; 2026-10-03-how-a-solution-design-is-built.md; 2026-10-13-what-a-brd-contains-and-how-it-is-found-today.md; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":73322,"output_tokens":25774,"thinking_tokens":14163,"cache_read_tokens":322263,"total_tokens":99096}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-18-cites-not-repeats
status: immutable
---

# What the description of an interface cites and does not repeat

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Established requirements engineering, formal UI standards, and
declarative form libraries agree on a strict division of ownership
between the textual description of an interface (how the interface works
and is structured for the user) and the documents around it (business
requirements, the technical solution design, and visual design-system
tokens). The interface description cites four external artefacts by
identifier or path rather than repeating their substance: a data
dictionary or data schema for field types, lengths, formats, and
persistence; a business-rules catalog or requirement IDs for domain
invariants, calculations, and role matrices; a service contract for
operations, security scopes, and error codes; and a shared glossary for
domain terminology. What stays inside the interface description is only
what cannot be read off those four sources: widget selection, screen
composition and layout, labels, interaction triggers (such as on-blur
versus on-submit), visual state transitions (idle, loading, empty,
error recovery), and the presentation effect of a rule or permission
(shown, hidden, enabled, disabled, read-only). The disconfirming queries
confirmed that standalone traceability matrices maintained by hand decay
into unused overhead and that duplicating business rules or schemas in
interface specifications leads to client-server drift, security bypasses,
and—in 2025 trials of AI spec-driven tools—repetitive Markdown files
that reviewers abandon in favour of reading code. One unexpected finding
reconfigures the boundary: conditional UI visibility and enablement
rules ("show field B when field A has value X") straddle the line in
every formal schema language, forcing either the UI specification to
embed a predicate over the data schema or the data model to carry
UI-state bindings.

## Question

#### Card 18: What the description cites and does not repeat
- **Question:** How does a description of an interface refer to what is
  defined elsewhere (the data model and its fields, validation and
  business rules, permissions and roles, the states and errors of the
  services behind it) without repeating it: which mechanisms of
  reference does established specification practice use (identifiers of
  requirements, a data dictionary, a contract between systems, a shared
  glossary), what is kept in the description of the interface and what
  is only cited, and what is reported about the two drifting apart?
- **Why it matters:** the description will stand beside requirements, a
  solution design and user stories, and the framework lets no layer
  repeat another.
- **What would answer it:** requirements engineering and specification
  practice as its standards and handbooks state it.
- **Where to look:** the literature on traceability from requirements to
  the design of an interface; specification templates that keep a data
  dictionary apart from the screens; interface descriptions bound to a
  service contract or a schema. The known notes on the solution design
  and on business requirements.
- **Disconfirming query:** "traceability matrix is waste", "business
  rules duplicated in UI specification"; expected: traceability kept by
  hand decays.
- **Stop rule:** nothing new from a differently worded query and every
  route has a primary source; ten to fifteen pages opened.

What this note must beat (the baseline): the two attached project notes
(`2026-10-03-how-a-solution-design-is-built.md` [1] and
`2026-10-13-what-a-brd-contains-and-how-it-is-found-today.md` [2])
already establish that in the forge's document chain a technical
solution design cites upward requirements by local item identifier
(`REQ.NNNN`, `BR.NNNN`, `UC.NNNN`) rather than a hand-kept matrix, names
realising file paths downward without copying schemas or interfaces into
prose, and relies on automated checks to flag suspect links when either
end moves. They also record that in spec-driven kits (`spec-kit`, Kiro,
OpenSpec, BMad) agents frequently generate repetitive Markdown files
that restate requirements or existing code. Those two notes treat the
business requirements document and the technical solution design; this
note must establish the exact boundary and referencing mechanisms for a
textual description of the user interface and user experience standing
beside them. Throughout this note, the three senses of "design" are kept
apart as asked by the frame: *interface design* means the structure and
behaviour of the user interface (whether held in a visual tool or a
textual specification), *technical design* means the architectural and
solution layer between requirements and implementation tasks, and
*design system* means the visual identity, tokens, and reusable widget
catalog.

## Key findings

Every web source [3]–[17] below was read through the engine's
summarising web fetch tool (`summarised fetch`, a tertiary extraction
that returns grounded summaries and verbatim passages); the two attached
project notes [1], [2] were read in full as local files.

**F1. Established specification practice separates the interface
description from the data model, business rules, service contract, and
domain terms, linking them through four explicit reference mechanisms
rather than prose restatement** [consensus: standard, practitioner
claim; rests on full text in [1], [2] and summarised fetches in
[3]–[15]]. Across software requirements engineering handbooks [3], [4],
W3C and OMG user-interface standards [6], [7], declarative schema-form
libraries [8], [9], and API specifications [11], [12], an interface
specification avoids duplication by using four pointer mechanisms:
1. *Requirement, business-rule, and decision identifiers* (`REQ`, `BR`,
   `UC`, or technical-design spine IDs) cited inline at the screen or
   screen-element definition [1], [2], [3], [4].
2. *Data-dictionary keys or schema paths* (such as JSON Pointer paths
   `#/properties/<field>` or XPath node references) that bind a screen
   control to an external field definition [3], [6], [7], [8], [9].
3. *Service-contract URI references* (such as OpenAPI `$ref` URIs,
   operation identifiers, security scheme names, and HTTP problem-type
   URIs) that bind screen actions and states to backend endpoints and
   error contracts [11], [12].
4. *Shared glossary terms* (the project's Ubiquitous Language [15] or
   arc42 Section 12 Glossary [14]) used verbatim in interface labels and
   descriptions without redefining business meaning on each screen [2],
   [14], [15].

**F2. For the data model and its fields, the data dictionary or data
schema owns data types, lengths, formats, enumerations, and persistence;
the interface description cites the property path and keeps only widget
choice, grouping, layout, and label** [consensus: standard,
practitioner claim; rests on summarised fetches in [3], [5]–[9]]. In
Wiegers and Beatty's *Software Requirements* (3rd ed., 2013), field
properties belong to a single repository: "The data dictionary stores
definitions of the data items and structures associated with the system.
This lets everyone working on the solution use consistent definitions...
the data dictionary provides a detailed view with each attribute's
specific properties" [3]. Formal UI standards enforce the same boundary
mechanically:
- In W3C *XForms 1.1* (2009), the specification "separates presentation,
  purpose and content" (Section 2): the `<model>` holds XML data
  instances and `<bind>` data types, while intent-based UI controls
  (`input`, `select`, `range`) carry only a `ref` attribute pointing to
  the model node and a human label [6].
- In OMG's *Interaction Flow Modeling Language* (IFML 1.0, 2015), a
  `ViewComponent` inside a `ViewContainer` defines no data structure of
  its own; it attaches a `DataBinding` or `ContentBinding` that points
  to an external `DomainModel` (such as a UML class or attribute) [7].
- In `react-jsonschema-form` (RJSF), the documentation states under
  `## uiSchema`: "A UI schema is basically an object literal providing
  information on how the form should be rendered, while the JSON schema
  tells what" [8].
- In EclipseSource's *JSON Forms*, the `Controls` documentation states:
  "The mandatory scope property, which expects a JSON schema reference
  value, defines to which property of the data the control should be
  bound to" (e.g., `"scope": "#/properties/name"`), while layout
  elements (`VerticalLayout`, `HorizontalLayout`, `Group`,
  `Categorization`) arrange controls without restating their data
  types [9].

**F3. For validation and business rules, the business-rules catalog or
data schema owns the invariant, calculation, and threshold; the
interface description cites the rule ID or schema constraint and keeps
only the interaction trigger, dynamic view effect, and user-facing error
presentation** [consensus: standard, practitioner claim; rests on full
text in [2] and summarised fetches in [3], [6], [10], [13]]. Wiegers and
Beatty recommend maintaining policies, calculations, and constraints in
a centralized Business Rules catalog where each rule has a unique
identifier (`BR-xxx`) cited by screens, use cases, and data dictionary
entries rather than copied into each artefact [3]. The OWASP *Input
Validation Cheat Sheet* (under "Common Pitfalls") states the security
reason why an interface description cannot be the authoritative specification
of a validation rule: "Validate on the server even when the browser
checks the same fields. Client-side validation is bypassable; use it for
immediate feedback" [13]. The interface description therefore cites the
authoritative rule or schema constraint and records only three
presentation decisions:
1. *When feedback is shown* in the interaction flow (while typing, on
   focus loss / blur, or on form submission).
2. *Where and how the message appears* (inline below the field, summary
   banner, or modal) and its user-facing wording where the schema carries
   only a constraint keyword.
3. *Dynamic view effects* (`HIDE`, `SHOW`, `DISABLE`, `ENABLE` in JSON
   Forms `Rules`, or `relevant` and `readonly` in XForms), where the UI
   element declares its visual state change when a referenced data
   property satisfies a condition [6], [10].

**F4. For permissions and roles, and for the states and errors of
backing services, the interface description cites actor definitions and
service contracts while owning the visual state machine and degradation
behaviour** [consensus: standard, practitioner claim; rests on full text
in [1], [2] and summarised fetches in [11], [12], [16]].
- *Permissions and roles:* Actor definitions and role-permission rules
  belong in the business requirements [2] and in the technical service
  contract's `Security Requirement Object` (OpenAPI v3.1.0, which "Lists
  the required security schemes to execute this operation" by referencing
  named schemes under the `Components Object` [11]). The interface
  description cites the actor or permission identifier and states only
  how the screen or element degrades when the role lacks that permission
  (whether a route redirects, an action button is hidden, or a field is
  disabled with an explanation).
- *Service states and errors:* Backend endpoints, HTTP status codes
  (`Responses Object`, Section 4.16 of OpenAPI v3.1.0, covering "a
  successful operation response and any known errors" [11]), and
  machine-readable error payloads (`type` URI, advisory `title`, and
  occurrence-specific `detail` in IETF RFC 9457, Sections 3.1.3–3.1.4
  [12]) belong to the technical design's service contract, while business
  exception branches belong to fully dressed use cases (`UC` extensions
  in [2]). The interface description—exemplified in the BMad Method by
  `EXPERIENCE.md`, which records "how it works (structure, states,
  interactions, accessibility, key flows)" apart from the visual tokens
  in `DESIGN.md` and the technical choices in the architecture spine
  [16]—cites the operation or error identifier and owns the client-side
  state representation: initial/idle state, loading indicator or
  skeleton, empty-result state, optimistic UI state, and recovery
  affordances (retry, undo, draft preservation).

**F5. A shared glossary (Ubiquitous Language) prevents silent
redefinition of domain nouns and state names between requirements, data
models, and screen labels** [consensus: standard, practitioner claim;
rests on full text in [1], [2] and summarised fetches in [14], [15]].
ISO/IEC/IEEE 29148, BABOK, and IREB require a shared definitions list,
and the BRD failure checklist in [2] flags "a term capitalised and not
defined" or "a term redefined" across layers as a primary defect [2].
Martin Fowler (2006-10-31) defines Domain-Driven Design's *Ubiquitous
Language* as "the practice of building up a common, rigorous language
between developers and users. This language should be based on the
Domain Model used in the software" [15]. In arc42 Section 12
(*Glossary*), the glossary holds "The most important domain and
technical terms that your stakeholders use when discussing the system"
and also serves "as source for translations if you work in a
multi-language environment" [14]. In an interface description, screen
titles, field labels, and status badges cite or reuse the glossary term
directly; where user-facing copy intentionally uses a simpler phrase
than the domain entity name, the element maps its display label to the
glossary or data-dictionary key rather than inventing an unmapped
synonym.

**F6. Hand-maintained traceability matrices and duplicated rules or
schemas across specification files decay rapidly; only local item-level
references verified by automated checks stay current** [consensus on
manual matrix decay and rule drift; emerging on AI spec-driven tools
(youngest source 2025-10-15): audit, practitioner claim; rests on full
text in [1], [2] and summarised fetches in [4], [17]]. The card's two
disconfirming queries ("traceability matrix is waste" and "business
rules duplicated in UI specification") confirmed the expected decay and
exposed its equivalent in AI spec-driven development:
- *Manual matrices decay into documentation theatre:* Wiegers (2013,
  republished 2022-01-16) and the prior forge notes report that
  standalone spreadsheet matrices mapping requirements to design, UI,
  and tests are "cumbersome, error-prone, and often leads to
  traceability information that is of insufficient quality" [1], [2],
  [4]. When a requirement changes mid-sprint, a separate matrix falls
  out of sync unless traceability links live locally inside the items
  themselves ("serves REQ.NNNN") and any matrix is generated and checked
  mechanically [1], [2].
- *Duplicated rules and schemas drift across layers:* In her audit of
  spec-driven AI tools (Kiro, `spec-kit`, and Tessl) on 2025-10-15,
  Birgitta Böckeler reported that `spec-kit` "created a LOT of markdown
  files for me to review. They were repetitive, both with each other,
  and with the code that already existed", that an AI agent took
  descriptions of existing classes and regenerated duplicates in the
  specification, and that she "d rather review code than all these
  markdown files" [1], [17]. A practitioner report on Kiro in [1]
  likewise noted that when developers edit tasks or code directly,
  within two weeks the specification describes a design the code no
  longer follows, and that the hallmark of over-specification is a
  downstream file restating `requirements.md` in different words [1].

## Unexpected

**Conditional UI visibility and enablement rules blur the boundary
between the interface description and the business-rules or data layer**
[6], [10], [17]. The card assumes that validation and business rules can
always be defined elsewhere and merely cited by ID in the interface
description. Both formal declarative UI specifications and practitioner
audits show that *intra-screen state rules*—such as showing or enabling
one field only when another field holds a specific value—resist clean
separation. In EclipseSource's *JSON Forms* (`Rules`), attaching a
`SHOW`, `HIDE`, `ENABLE`, or `DISABLE` effect to a UI element requires
embedding a `SchemaBasedCondition` inside the UI schema itself, with a
`scope` pointer and an inline JSON Schema snippet to evaluate against
the data property [10]. Conversely, W3C *XForms 1.1* keeps the
expression out of the UI control only by pushing UI-state properties
(`relevant` for visibility, `readonly` for editability) back into the
data `<model>` via `<bind>` elements [6]. Böckeler (2025-10-15) reports
the human side of the same friction in spec-driven development: "I
frequently got confused when to stay on the functional level, and when
it was time to add technical details" [1], [17].

**Virtual Windows invert the direction of citation during early
requirements elicitation** [5]. The card frames the data model as
defined elsewhere and cited by the interface description. Søren Lauesen
and Morten Borup Harning (*IEEE Software*, July/August 2001) demonstrate
the opposite order for early elicitation: their "Virtual Windows"
technique specifies simplified screens containing realistic sample data
(with no buttons, menus, or interaction mechanics) first, and the data
requirement then cites the virtual windows (`R1: The product shall store
data corresponding to the following virtual windows`) [5]. They report
that domain experts and users spot missing data attributes far more
reliably in a virtual window than in an entity-relationship diagram or
data dictionary, though they warn of the "Risk of overdoing it and start
designing the user interface" prematurely [5].

## Not found

- **Clause-level text of ISO/IEC/IEEE 29148:2018 and IREB CPRE handbooks
  on external interface specifications:** Looked for through `reqview.com`
  and standards summaries; the standards themselves are sold or
  reproduction-restricted, as already noted in [2], and the targeted
  fetch of ReqView's ISO 29148 template page [18] returned an empty
  summary error from the tool.
- **Controlled empirical studies measuring drift rates specifically
  between textual UI specifications and backend data dictionaries or
  service contracts:** Looked for across requirements engineering and
  spec-driven development literature; while architecture-to-code drift
  is measured in general (Feilkas et al. 2009 and Wan et al. 2023 in
  [1]) and qualitative reports of UI/spec duplication exist [1], [17],
  no quantitative study isolating UI-specification drift was found.

## Options

Wait—Card 18 asks how established practice refers to other documents and
what is kept versus cited, which directly informs how the forge's UX/UI
description layer will link to the BRD, the solution design, and user
stories. Four distinct options follow from the findings:

**Option A. Local inline identifier citations inside screen and element
definitions, backed by an automated link-and-coverage check (no matrix
in the document).** Every screen or element definition in the UX/UI
Markdown document cites upstream requirement, business-rule, and use-case
IDs (`REQ.NNNN`, `BR.NNNN`, `UC.NNNN`) and solution-design part or
contract IDs (`SOL.NNNN`, field/endpoint keys) inline, while owning only
layout, widget kind, interaction triggers, and visual states. An
automated check verifies that every cited ID exists and generates a
coverage view on demand.
- *For:* Matches the mechanism already chosen in the solution-design
  note [1] and BRD note [2]; eliminates manual traceability matrix
  maintenance [4]; maps directly onto the declarative `scope` / `ref`
  binding pattern of JSON Forms [9], RJSF [8], and XForms [6].
- *Against:* Requires the BRD or solution design to expose stable,
  granular identifiers for data fields, business rules, and service
  errors; if the solution design leaves the full data shape to the code
  (as BMad's spine does [1]), the UI element has no formal field ID in
  the design document to cite unless it cites a glossary term or a path
  in the codebase/schema file.

**Option B. A dedicated UI Data & Rule Binding table inside the UX/UI
document.** The UX/UI document includes a central mapping table (as
common in regulated enterprise UI templates) that lists every UI field
ID alongside its target data-model entity/attribute, data type, and
validation rule ID, while screens reference the local UI field ID.
- *For:* Self-contained for a UI reviewer or frontend builder when no
  machine-readable schema (`data-model.md` or OpenAPI file) exists yet.
- *Against:* Directly violates the no-repeat rule whenever a data
  dictionary or schema file exists alongside it; high risk of the
  table drifting from the solution design or backend schema [1], [17].

**Option C. Schema-driven UI binding (the UX/UI description cites paths
in a machine-readable schema or contract file such as JSON Schema /
OpenAPI).** Data shapes and service errors live in `data-model.md` or
`contracts/` (as in `spec-kit` [1]), and element definitions in the
UX/UI document reference JSON Pointers (`#/properties/...`) or OpenAPI
operation IDs.
- *For:* Zero duplication of field constraints or HTTP error structures
  [8], [9], [11]; directly consumable by AI coding agents and mechanical
  validators.
- *Against:* Too low-level when a project is at an early conceptual
  stage or has skipped a detailed technical solution design (which
  three of four spec-driven tools allow [1]).

**Option D. Virtual-window data ownership for small projects that skip a
separate data dictionary.** Where a project has no separate data
dictionary in its BRD or solution design, the element definitions in the
UX/UI description act as Lauesen's virtual windows [5] and own the
user-visible field definitions once for the whole chain, while still
citing `BR` items for domain rules.
- *For:* Avoids forcing a small project to write a separate data-model
  document solely to give the UI document something to point at.
- *Against:* Mixes data-dictionary concerns into the interface layer if
  a technical schema is later added without migrating the field
  constraints out.

## Relevance to this project

**Recommendation (this agent's inference from [1]–[17]): adopt Option A
as the universal referencing rule, with a fallback from schema pointers
(Option C) to glossary terms when no technical schema exists yet, and
never include a traceability matrix or restated field/rule definitions
inside the UX/UI document.**

Specifically, for the proposed framework where each screen element has a
small Markdown definition and a page definition composes them:
1. **What the element or page definition cites (and never repeats):**
   - *Data model and fields:* Cite the field key from the solution
     design's data model or schema (or the BRD's data dictionary /
     glossary term if no technical design exists). Never write `varchar`,
     character limits, regexes, or database column names in the UI
     description [3], [8], [9].
   - *Validation and business rules:* Cite `BR.NNNN` (or the schema
     constraint). Never restate threshold formulas, eligibility rules,
     or domain calculations in the UI description [3], [13].
   - *Permissions and roles:* Cite the actor or role ID from the BRD or
     the security scope from the solution design's contract [2], [11].
     Never redefine who holds which role.
   - *Service states and errors:* Cite the use-case extension (`UC.NNNN`
     step) or the service contract's operation/error key (`SOL.NNNN` or
     RFC 9457 problem type) [2], [11], [12].
   - *Domain terms:* Use the exact capitalised or defined term from the
     shared glossary [2], [14], [15].
2. **What the element or page definition keeps as its own:**
   - *Structure and composition:* Which elements stand on the page,
     their grouping/layout hierarchy, and navigation targets [6], [7],
     [9].
   - *Control and presentation:* The kind of control (text input, select,
     toggle, date picker), its visible label/copy, placeholder, and
     accessibility role [6], [8], [9], [16].
   - *Interaction timing and rule effects:* When validation feedback
     fires (on-blur, on-submit, live), where error messages sit, and how
     a cited rule or permission alters the element's state (`shown`,
     `hidden`, `enabled`, `disabled`, `read-only`) [6], [10], [13].
   - *Client-side view states:* How the screen or component looks across
     `idle`, `loading`, `empty`, `partial`, and `error/retry` states
     [16].
3. **Where intra-screen visibility predicates live:** When a visibility
   or enablement rule is purely presentational (e.g., expanding an
   "Other, please specify" input when "Other" is chosen), keep the
   condition inside the UI element definition (as JSON Forms `Rules`
   does [10]). When the condition reflects a business invariant across
   channels, define it as a `BR` item in the BRD and cite its ID.
4. **How drift is prevented:** Follow the forge's established pattern
   from [1] and [2]: links live as cited IDs inside each UI item; no
   traceability matrix is stored in the file; and an automated check
   verifies that every cited `REQ`, `BR`, `UC`, `SOL`, or glossary key
   resolves and flags suspect items when an upstream definition changes.

**Consult when:**
- Designing the template, fields, and non-duplication rules for the
  UX/UI specification artefact and its screen/element Markdown blocks.
- Writing the automated check (`check` / `essence` / `clarity` rules)
  that validates references between the UX/UI description, the BRD, the
  solution design, and user stories.
- Deciding whether a conditional field rule or validation message
  belongs in the BRD, the solution design, or the UX/UI description.

## Sources

1. *How a solution design is built*, forge project research note,
   2026-10-03 (structured data: YAML frontmatter),
   `2026-10-03-how-a-solution-design-is-built.md`; kind: secondary
   (project synthesis of primary design and SDD sources); how read: in
   full; original.
2. *Research: what a BRD contains and how it is found today*, forge
   project research note, 2026-10-13 (structured data: YAML
   frontmatter),
   `2026-10-13-what-a-brd-contains-and-how-it-is-found-today.md`; kind:
   secondary (project synthesis of primary requirements standards and
   sources); how read: in full; original.
3. *Software Requirements, Third Edition*, Karl E. Wiegers and Joy
   Beatty (Microsoft Press), 2013 (structured data: book publication
   record),
   https://www.oreilly.com/library/view/software-requirements-3rd/9780735679658/ ;
   kind: primary (handbook, read via tertiary summarised fetch); how
   read: summarised fetch; original.
4. *Requirements Traceability: Links in the Requirements Chain, Part 1*,
   Karl Wiegers (Jama Software blog), 2022-01-16 (byline; updated
   republication of 2013 article series),
   https://www.jamasoftware.com/blog/requirements-traceability-links-in-the-requirements-chain-part-1/ ;
   kind: primary (practitioner article, read via tertiary summarised
   fetch); how read: summarised fetch; copy (syndicated republication of
   Wiegers' 2013 *Links in the Requirements Chain* series).
5. *Virtual Windows: Linking User Tasks, Data Models, and Interface
   Design*, Søren Lauesen and Morten Borup Harning (*IEEE Software*,
   Vol. 18, No. 4, pp. 67–75), July/August 2001 (byline),
   https://doi.org/10.1109/52.93774 ; kind: primary (journal article,
   read via tertiary summarised fetch); how read: summarised fetch;
   original.
6. *XForms 1.1*, John M. Boyer, ed. (W3C Recommendation), 2009-10-20
   (byline), https://www.w3.org/TR/xforms11/ ; kind: primary (standard,
   read via tertiary summarised fetch); how read: summarised fetch;
   original.
7. *About the Interaction Flow Modeling Language Specification Version
   1.0*, Object Management Group (OMG), March 2015 (structured data),
   https://www.omg.org/spec/IFML/1.0/About-IFML ; kind: primary
   (standard overview, read via tertiary summarised fetch); how read:
   summarised fetch; original.
8. *uiSchema*, RJSF Team (`react-jsonschema-form` documentation),
   undated,
   https://rjsf-team.github.io/react-jsonschema-form/docs/uiSchema ;
   kind: primary (library documentation, read via tertiary summarised
   fetch); how read: summarised fetch; original.
9. *Controls — JSON Forms Documentation*, EclipseSource (`jsonforms.io`),
   undated, https://jsonforms.io/docs/uischema/controls ; kind: primary
   (library documentation, read via tertiary summarised fetch); how
   read: summarised fetch; original.
10. *Rules — JSON Forms Documentation*, EclipseSource (`jsonforms.io`),
    undated, https://jsonforms.io/docs/uischema/rules ; kind: primary
    (library documentation, read via tertiary summarised fetch); how
    read: summarised fetch; original.
11. *OpenAPI Specification v3.1.0*, Darrel Miller, Jeremy Whitlock,
    Marsh Gardiner, Mike Ralphson, Ron Ratovsky, and Uri Sarid, eds.
    (OpenAPI Initiative), 2021-02-15 (byline),
    https://spec.openapis.org/oas/v3.1.0.html ; kind: primary (standard,
    read via tertiary summarised fetch); how read: summarised fetch;
    original.
12. *RFC 9457: Problem Details for HTTP APIs*, M. Nottingham, E. Wilde,
    and S. Dalal (IETF), July 2023 (byline),
    https://www.rfc-editor.org/rfc/rfc9457.html ; kind: primary
    (standard, read via tertiary summarised fetch); how read: summarised
    fetch; original.
13. *Input Validation Cheat Sheet*, OWASP Cheat Sheet Series, undated,
    https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html ;
    kind: primary (practitioner security standard/guide, read via
    tertiary summarised fetch); how read: summarised fetch; original.
14. *Section 12: Glossary*, Gernot Starke and Peter Hruschka (arc42
    Documentation), undated, https://docs.arc42.org/section-12/ ; kind:
    primary (template documentation, read via tertiary summarised
    fetch); how read: summarised fetch; original.
15. *UbiquitousLanguage*, Martin Fowler (`martinfowler.com`),
    2006-10-31 (byline),
    https://martinfowler.com/bliki/UbiquitousLanguage.html ; kind:
    primary (practitioner article, read via tertiary summarised fetch);
    how read: summarised fetch; original.
16. *Design UX and Architecture*, BMad Method Documentation
    (`docs.bmad-method.org`), undated,
    https://docs.bmad-method.org/plan/design-ux-and-architecture/ ;
    kind: primary (tool documentation, read via tertiary summarised
    fetch); how read: summarised fetch; original.
17. *Understanding Spec-Driven-Development: Kiro, spec-kit, and Tessl*,
    Birgitta Böckeler (Thoughtworks, on `martinfowler.com`), 2025-10-15
    (byline),
    https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html ;
    kind: primary (practitioner tool audit, read via tertiary summarised
    fetch); how read: summarised fetch; original.
18. *ISO/IEC/IEEE 29148 Requirements Specification Templates*, ReqView
    Documentation (`reqview.com`), undated,
    https://www.reqview.com/doc/iso-iec-ieee-29148-templates/ ; kind:
    secondary; how read: not opened, targeted fetch returned an empty
    response error (`no summary returned from GenerateContent`);
    original.

## Opened and not used

- `https://github.com/github/spec-kit/blob/main/templates/plan-template.md` — GitHub `spec-kit` plan template: opened via summarised fetch, superseded by [1] and [17] because the fetch returned only the repository link without text beyond what [1] already recorded.

## Search record

Queries run, in order:
1. `UI specification data dictionary business rules reference without repeating` (broad exploratory search)
2. `user interface specification template data model validation rules traceability` (broad exploratory search)
3. `"traceability matrix is waste"` (disconfirming query 1)
4. `"business rules duplicated in UI specification"` (disconfirming query 2)
5. `interface description bound to service contract schema OpenAPI JSON Schema UI specification` (broad search on contract/schema binding)
6. `"Karl Wiegers" "business rules" "data dictionary" "user interface" avoid duplication reference URL quote` (targeted fetch for [3])
7. `JSON Forms data schema UI schema scope reference "#/properties/" documentation exact URL quote` on `jsonforms.io` (discovery for [9])
8. `react-jsonschema-form uiSchema JSON Schema separation documentation exact URL quote` on `rjsf-team.github.io` (discovery for [8])
9. `IFML Interaction Flow Modeling Language domain model binding view component specification exact URL quote` on `omg.org` (discovery for [7])
10. `Karl Wiegers "links in the requirements chain" OR "traceability" OR "business rules" exact URL date quote` on `jamasoftware.com` (discovery for [4])
11. `design UX architecture specification reference requirements data model exact URL quote` on `docs.bmad-method.org` (discovery for [16])
12. `"https://rjsf-team.github.io/react-jsonschema-form/docs/uiSchema" exact title date sections verbatim quotes uiSchema JSON Schema` on `rjsf-team.github.io` (summarised fetch of [8])
13. `"https://jsonforms.io/docs/uischema" OR "https://jsonforms.io/docs/uischema/controls" exact URL title sections verbatim quotes scope rules data schema` on `jsonforms.io` (summarised fetch of [9])
14. `"links-in-the-requirements-chain" Karl Wiegers exact URL title publication date verbatim quotes traceability UI business rules data dictionary` on `jamasoftware.com` (summarised fetch of [4])
15. `"https://docs.bmad-method.org/plan/design-ux-and-architecture/" exact title sections verbatim quotes UX specification architecture spine IDs` on `docs.bmad-method.org` (summarised fetch of [16])
16. `"https://www.omg.org/spec/IFML/1.0/About-IFML" OR "https://www.omg.org/spec/IFML" exact URL title date verbatim quotes ContentBinding DataBinding DomainModel ViewComponent` on `omg.org` (summarised fetch of [7])
17. `"Soren Lauesen" "Virtual Windows" data model user interface requirements specification exact URL date quote` (summarised fetch of [5])
18. `"https://www.w3.org/TR/xforms11/" exact title date authors verbatim quote separation purpose presentation XForms model user interface ref bind` on `w3.org` (summarised fetch of [6])
19. `"https://www.rfc-editor.org/rfc/rfc9457.html" OR "RFC 9457" Problem Details for HTTP APIs exact title date authors verbatim quote type title detail user interface` on `rfc-editor.org` (summarised fetch of [12])
20. `"requirements-traceability-matrix" OR "iso-iec-ieee-29148-templates" exact URL title date verbatim quote traceability user interface business rules data dictionary` on `reqview.com` (attempted fetch of [18]; failed with tool error)
21. `"https://docs.arc42.org/section-12/" exact title verbatim quote Glossary domain terms translation reference` on `docs.arc42.org` (summarised fetch of [14])
22. `"https://jsonforms.io/docs/uischema/rules" exact URL title verbatim quote rule effect SHOW HIDE ENABLE DISABLE condition scope` on `jsonforms.io` (summarised fetch of [10])
23. `"github/spec-kit" "data-model.md" "contracts" "spec-template.md" OR "plan-template.md" exact URL verbatim quote separation` on `github.com` (summarised fetch of unused `spec-kit` page)
24. `"https://spec.openapis.org/oas/v3.1.0.html" exact title date authors verbatim quote Reference Object "$ref" Responses Object Security Requirement Object` on `spec.openapis.org` (summarised fetch of [11])
25. `"https://martinfowler.com/bliki/UbiquitousLanguage.html" exact title date author verbatim quote glossary domain model language` on `martinfowler.com` (summarised fetch of [15])
26. `"https://martinfowler.com/articles/exploring-gen-ai/sdd-3-tools.html" Birgitta Boeckeler exact title date verbatim quote repetitive markdown files functional level technical details duplicates` on `martinfowler.com` (summarised fetch of [17])
27. `"https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html" exact title verbatim quote client-side server-side validation bypass user interface` on `cheatsheetseries.owasp.org` (summarised fetch of [13])

Pages opened: 2 local project notes read in full ([1], [2]) and 15
external web pages targeted via `search_web` summarised fetches ([3]–[17],
plus the one unused `spec-kit` template page; one additional targeted
fetch [18] failed with a tool error and is recorded as not opened).

What the disconfirming queries found:
- `"traceability matrix is waste"` found widespread practitioner
  consensus that manually maintained, static spreadsheet traceability
  matrices degenerate into "documentation theatre" and fall out of date
  as soon as requirements change mid-iteration, whereas automated,
  item-level links used to generate views on demand remain necessary for
  impact analysis and regulated audits.
- `"business rules duplicated in UI specification"` found unanimous
  practitioner and security guidance against stating business logic in
  UI specifications or frontend-only checks, reporting three resulting
  failures: multi-file maintenance drift when rules change, inconsistent
  validation across client channels, and security vulnerabilities when
  client-side validation is bypassed against an unvalidated backend
  [13].

Reason the run ended: both parts of the card's stop rule were met at the
15-page web opening budget—every route in the card (requirements
traceability, data dictionary separation, schema/service-contract
binding, shared glossary, and spec-driven tool practice) had at least
one primary source and differently worded queries returned the same four
reference mechanisms and the same two drift failure modes.
