# The two outside deep-research reports against the synthesis

Made by Claude in the session on 2026-11-21, on the principal's word,
from the texts of this bundle alone: of `00-plan.md` the Summary and,
of the Synthesis, Completeness, Answers side by side, Unexpected, Not
found and Claude's view; `deep-research-prompt.md`;
`deep-research.copilot.md`; `deep-research.gemini.md`. No part of the
synthesis. No source of either report was opened: what a report holds
beyond the bundle is a lead, not a finding. Which names of the reports
stand in the notes was looked up by a search of the notes' text. The
assignment numbers its questions in order: questions 1 to 7 are cards
1 to 7, questions 8 to 22 are cards 22, 8, 9, 10, 11, 17, 21, 12, 13,
14, 15, 16, 18, 19 and 20.

## 1. Coverage

The marks: **yes**, the main question and most of its parts have a
finding or a stated "not found"; **yes°**, answered, but a part ends as
"not found" or the engines differ on it; **in part**, only some parts,
or only a definition or a recommendation without a finding; **no**, not
addressed.

| Q | Topic | Card | Synthesis | Copilot | Gemini | Remark |
|---|---|---|---|---|---|---|
| 1 | The map of the field and its words | 1 | yes | yes | no | Gemini does not say whether a survey exists and has no vocabulary |
| 2 | One screen | 2 | yes° | yes | in part | Europe: the engines differ, Copilot "not found"; Gemini only mentions gamen sekkeisho |
| 3 | The user's path | 3 | yes | in part | in part | the reports define the methods; where a path lives and how it is tied to a screen is missing |
| 4 | Above the screens | 4 | yes | in part | in part | the reports have object-oriented UX only, no information architecture, no navigation |
| 5 | Formal languages | 5 | yes | yes | in part | Copilot gives no reasons for the absence of adoption; Gemini has no XForms, IFML, ISO or W3C |
| 6 | An element defined once | 6 | yes | in part | in part | both lack how description and implementation are kept the same |
| 7 | A page of blocks | 7 | yes | yes | no | |
| 8 | The whole application | 22 | yes° | in part | no | Copilot: a recommendation without a finding |
| 9 | Described for an agent that builds | 8 | yes | in part | in part | Copilot knows no spec-driven kit, no DESIGN.md, no rules file |
| 10 | Measurement | 9 | yes° | in part | no | Copilot has two studies and does not compare the inputs with each other |
| 11 | From text to a preview | 10 | yes | in part | in part | the reports list the routes, without what each needs and what a change costs |
| 12 | Text and the design tool | 11 | yes | yes | no | |
| 13 | The agent that proposes | 17 | yes | in part | no | Copilot: an order of steps of its own, without a source |
| 14 | Where a description becomes code | 21 | yes° | yes | in part | Gemini: the mechanics of previews yes, the border no |
| 15 | The platforms | 12 | yes | in part | in part | the reports say what should be, not what products keep |
| 16 | What the description owes every user | 13 | yes | in part | yes | Copilot: what an instance should carry, not how templates carry it |
| 17 | The place in the process and the roles | 14 | yes° | in part | no | |
| 18 | Judging before the build | 15 | yes | yes | no | Copilot answers the whole, without a source and against the synthesis |
| 19 | Where text failed | 16 | yes° | in part | in part | the reports: general causes, no case |
| 20 | What the description cites | 18 | yes° | yes | no | |
| 21 | After the first build | 19 | yes° | in part | in part | both lack the variation of a shared element and the way back of changes made during the build |
| 22 | The description and the test | 20 | yes | in part | in part | definitions of the patterns; the level of abstraction by assertion only |

The sum: the synthesis 22 yes, eight of them with the mark; Copilot 8
yes and 14 in part; Gemini 1 yes, 12 in part and 9 no.

## 2. Agreement

All three say the same:

- The formal languages of the model-based tradition were not taken up
  by practice.
- Design systems define a component once (anatomy, variants,
  properties, states, accessibility), with tokens beneath it.
- Gamen sekkeisho is the fullest textual specimen of the description
  of a screen.
- Declarative code is itself a readable description, and its preview
  is drawn in isolation.
- Objects before screens are an alternative unit.
- Accessibility and internationalisation are decided at design time.
- What fails is a stale second document, and the critics put the
  prototype or the code in its place.
- Shared definitions are versioned.

The synthesis and Copilot, Gemini being silent:

- No finished shape and no survey of the field exists, and nobody
  publishes a Markdown file per element with pages that compose them.
- The facts of status agree: the W3C group closed in 2014, IFML 1.0 is
  of 2015, the format of tokens is a community group's report and not
  a standard.
- The text should claim less than the whole truth; a preview is
  derived and never the source.
- Identifiers are the description's own and stable; a layout does not
  make the round trip between text and a design tool without loss.
- Models as evaluators weaken across screens, and inconsistency across
  screens is measured.
- Nobody found a quantitative account of a description drifting from
  the documents it cites.

Copilot supports five findings that stood in the bundle on the session
model alone:

- the rule "state in, events out" of the maker of previews (card 21);
- the process of object-oriented UX is not described in the open
  (card 4);
- the accessible name belongs to the instance, not to the definition
  (card 13);
- a threshold for which elements earn a definition (cards 7 and 20);
- the formats by which an agent sends an interface are not a
  description for a build (card 21).

This is consistency, not validation: whether Copilot read the same
pages is not known.

## 3. Differences and contradictions

Words quoted from Gemini's report, here and below, are translated from
the language it is written in.

1. **Judging before the build.** Copilot says that heuristic
   evaluation needs a picture. The synthesis, on both engines, says
   that by the methods' own literature a detailed description is
   enough. Copilot names no source; the synthesis has two independent
   notes, though nobody read the methods' original papers.
2. **Executable specifications.** Gemini states that a passing BDD
   suite "proves" the match and that specification and code "never
   diverge". The synthesis says that nothing opened checks a build
   against a text directly and that a change of the code does not come
   back without a person. Copilot stands with the synthesis; Gemini
   names no source.
3. **A scenario at the level of the task.** Gemini gives it as
   resilient, as the second engine does. The synthesis holds this
   contested, on a controlled experiment and a doctoral thesis of
   2025, both in the session model's notes only.
4. **Where the elements stand.** Gemini wants layout and breakpoints
   in the text. The synthesis says that no source read states the
   position in text and that this is the part that failed everywhere.
   Copilot stands with the synthesis.
5. **DESIGN.md.** Gemini takes it as an example of definitions of
   elements and as a textual source of truth. The synthesis, on both
   engines, says it is the visual identity and knows no screen. Gemini
   describes it the same way a few paragraphs earlier and so
   contradicts itself.
6. **The closest relative.** Copilot puts A2UI 1.0 highest. The
   synthesis sets such formats aside as formats of run time. A
   difference of weight, not of fact. One date does not fit: Copilot
   gives 20 November 2025, the second engine's note has the
   publication in December 2025.
7. **The platforms.** Gemini calls one abstract specification "the
   key". Copilot keeps the mobile web as a platform. The synthesis
   says that both shapes are documented, that nobody measured them and
   that the four targets are points on three axes. The reports name no
   source; the synthesis has the platform owners' primary sources.
8. **The order of the agent's questions.** Copilot gives nine steps as
   "a safe sequence", without a source. The synthesis says that no
   source prescribes a fixed order and that screens are proposed as
   alternatives.
9. **What follows from objects first.** Both reports state the gains
   as fact. The synthesis says that the methods' authors claim them
   and nobody measured them.
10. **The preview.** Copilot rests its first shape on a generated
    preview and on component stories. The synthesis says that stories
    need coded components and so belong to the build, and that the
    text languages for wireframes have the weakest evidence in the
    bundle.
11. **Why the formal languages were not adopted.** Gemini gives three
    reasons as fact. The synthesis has them as claims of proponents
    only. Copilot gives none.

## 4. What each holds beyond the other

Leads from Copilot's report, not in the bundle:

- **The second direction of question 10:** reading screenshots is said
  to have captured screens and the relations between pages better than
  detailed test cases. The most valuable lead, since it bears on a
  thing the synthesis holds unmeasured; its source is not named.
- The packages of templates of Living-in.EU for public procurement, of
  2025 (the European branch of question 2).
- Carbon gives agents its design system through MCP.
- A2UI: attributes of accessibility across platforms, and a loop of
  generation with validation against the catalogue.
- An audit of 2026 by which general instructions did not prevent a
  manipulative interface; its source is not named.
- ISO 9241-110 "confirmed in 2025".
- Three ideas of shape, not findings: a section "Does not decide" in
  the definition of a component, criteria of success for the pilot,
  typed identifiers.

Leads from Gemini's report:

- The mechanics of previews (Layoutlib, PreviewActivity, hot reload).
- Localisation plugins that keep the keys of texts in the design tool.
- A cultural reading of gamen sekkeisho; a thing to drop rather than
  to verify.

What the bundle holds and the reports lack:

- A rule of variation for a shared element and the reach of a change.
- The type, the instance and the placement kept apart.
- The second copy as the cause of failure, whatever its medium.
- The three axes of the platforms, the section between the application
  and the screen, the screen as no stable unit.
- The landscape of the AI tooling: the spec-driven kits, delta
  specifications, the three meanings of "design".
- Four rules held as contested.
- A template of structure by role and name that a build can be held
  to.
- The breadboard as a preview of words.
- The whole apparatus: Not found, the dead citations by finding, the
  measure of independence.

## 5. Quality

| | The synthesis and the bundle | Copilot | Gemini |
|---|---|---|---|
| Sources | some hundreds of addresses, not counted here, each with its kind and how it was read | 20 names (17 primary, 3 secondary), no address | none |
| Verifiability | a script for citations and for independence; the content of the pages verified by nothing | not by a script; seven statements that can be compared with the notes agree | none |
| Caution | holds the contested as contested, Claude's view kept apart | a "Counter" on every question, admits gaps; writes recommendations as findings | none, everything given as settled |
| Shape of the report | another shape (the plan's template), no example | all 8 parts; findings without a source and a date each | a summary without a recommendation, the rest missing; not in English, on an assignment written in English |
| Concreteness | high in the findings, the shape in words only | highest in the shape: a finished example of a screen and of a component | textbook generalities |

- **The seven statements:** the date and the sixteen designers of
  SpecifyUI, the figures and the web stack of MobileForge, the status
  of the tokens format, the closing of the W3C group in 2014, IFML 1.0
  of 2015.
- **Copilot's "Counter":** on questions 1 and 2 it is the result of a
  search, elsewhere a counter-argument.
- **Copilot's file:** its Figure 1 is missing and its tables are run
  together.
- **Gemini and the assignment:** by the Notes of the plan it is not
  verified that it ran on this assignment. Its subtitle and its words
  follow the assignment's, so it probably saw it: Claude's estimate.

## 6. The verdict on the idea

| | The synthesis | Copilot | Gemini |
|---|---|---|---|
| Verdict | stands as a model of reference, not at the grain of "every element" | "retain the reference model, reject the granularity" | none on the idea; judges Markdown as a format on the example of DESIGN.md: "promising" |
| Relatives | every system that holds a page as data naming blocks; design systems | A2UI, the numbering of gamen sekkeisho, design systems, Adaptive Cards | not looked for |
| Does anyone publish it? | no (both engines) | no | not addressed |
| What is missing or stands against | the instance with what differs on the page; a rule of variation; a threshold | files per instance fragment and feign reuse; the behaviour of a field belongs to the screen or the path | the limited semantics of Markdown, many files |
| Instead | a definition only for an element that recurs or has states of its own; named instances; stable names of parts | a catalogue only for shared semantic components; named instances; paths apart; stable identifiers | nothing |

## 7. The first shape to try

| | The synthesis (a hypothesis, found whole nowhere) | Copilot ("Screen Contract") | Gemini |
|---|---|---|---|
| Units | the application, a section, paths, screens, definitions of elements | an application contract, paths, screens, a catalogue of components | no shape |
| Screen | identity, purpose, named regions in order, instances of elements, states, actions, citations by identifier | a Markdown file with a YAML header; purpose, regions, components as instances, responsive intent, open decisions | |
| Paths | in words: places, what can be done there, where it leads | Mermaid diagrams outside the screens | |
| Element | what the user does and perceives through it, parts, variants, the surface a page may override | required properties and a list of what the definition does not decide | |
| Preview | the description read as a breadboard, at no cost | a generated preview and component stories | |
| Platforms | a line per target on which conventions are taken as they are | a list of platforms and a responsive intent | |
| Example | none | a search field and a page, as the assignment asked | none |

The skeleton is the same in both: four kinds of item with stable
identifiers that cite each other. The two arose in runs that share the
assignment and nothing else; the assignment itself names these units,
so the agreement is consistency and no more.

## Assessment

- **Gemini's report alone:** an orientation in the vocabulary of the
  field. Neither of the two decisions the research was to allow, and
  several statements the bundle shows contested or mistaken.
- **Copilot's report alone:** would have been enough for the decision.
  Its verdict and its first shape with an example go the way of the
  synthesis at a fraction of the size. It would not have given the
  ground beneath them, the landscape of the AI tooling, a rule of
  variation, or what rebuilt the question itself (the position, the
  three axes, the second copy).
- **What two engines gave:** four rules came out contested only
  because one engine gave the consensus and the other found evidence
  against it. Both outside reports repeat the side of the consensus in
  places, and with one voice it cannot be told which statement is
  contested.
- **What the citation check gave:** it showed what the second engine's
  notes do not rest on. On the reports it cannot be run at all, so
  they are leads throughout.
- **Claude's view, his own:** the bundle bought no other answer than
  Copilot's; it bought knowing how far the answer holds.
