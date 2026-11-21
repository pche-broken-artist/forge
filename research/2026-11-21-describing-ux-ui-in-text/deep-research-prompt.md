# Deep research: how a user interface and its use are described in text

Standards, practice and options, across web, mobile web, native
mobile and desktop applications.

## Context

I work with a framework that carries an idea down a chain of
versioned Markdown documents kept in git: what is wanted and why,
then business requirements, a solution design and user stories. A
human works each document with an AI agent: the agent asks, proposes
and writes, the human decides. Nothing is implemented there; the
documents are handed on to be built.

I want the same for the user interface and the user experience of
an application, and no such document exists yet. The working picture:
an AI agent reads the documents above, asks what it lacks and
proposes a description of the interface; a human tunes that proposal
and needs to see it, not only read it; the description then goes,
with the other documents, to a build stage (a human developer, an AI
coding agent, or both), and the cycle runs again when the interface
changes. In a small project one person does all of it end to end; in
a company a UX/UI specialist does, and will later need a connection
to a design tool such as Figma.

Before designing anything I want a wide survey of how this is done
elsewhere. Go for breadth. Do not assume that a textual description
is the right source of truth: test that too. Do not assume either
that a finished shape for this exists: a description that a person
and a language model write together, that tolerates half-structured
text and is shown as a preview at once, is a new situation. Expect
fragments and warnings, and tell me if you find a finished shape.

## What the research must let me decide

1. Which shapes a textual description of an interface can take, by
   its unit: a screen, an object of the domain, an element or
   component, a user's path. For each: what it looks like, who uses
   it, what it is good and bad at.
2. Which is the simplest shape worth trying first on one real web
   application, such that it can grow to the other platforms and to
   a design tool later.

## One idea to test, not to assume

I heard of a practice where every element of a screen (a search
field, say) has a small Markdown definition of its own that carries
its function, and a page definition names which elements it holds
and where they stand; pages are then worked by changing and
rearranging those references. Find its closest relatives, say
whether anyone publishes this practice itself, and say what speaks
for and against it.

## Questions

**A. The field**

1. Does a synthesis already exist: a survey, a taxonomy or a
   comparison of ways to specify user interfaces and user experience
   in text? Which words do practice, the standards and the AI
   tooling of 2024 to 2026 use for it?

**B. What is described, and in what shape**

2. One screen: what do established screen specifications and
   annotated wireframes contain (purpose, regions, elements, data,
   actions, states such as empty, loading and error, rules,
   responsive behaviour), how are elements identified, and how much
   is prose against structure? Look also outside English, where
   textual screen specifications stayed alive: the Japanese screen
   design documents (gamen sekkeisho, within the basic design, kihon
   sekkei), and templates of public procurement and of systems
   engineering in Europe.
3. The user's path: how are paths described in text (use cases, task
   models, user flows, journey maps, story maps, scenarios, state
   machines), what is each for, and do they live in a document of
   their own, inside each screen, or both? How are path and screen
   kept linked?
4. Above the screens: how are the conceptual model (objects,
   attributes, actions, relationships), the information architecture
   and the navigation described, and what follows from describing
   objects before screens (object-oriented UX and its relatives)?
5. Formal languages and standards that describe an interface
   independently of its implementation: the model-based tradition
   (task, abstract, concrete and final interface; UsiXML, UIML,
   MARIA, XForms, the W3C's work), IFML, ISO 9241. What does each
   describe, what became of it, and why was it adopted or not?
6. An element defined once: how do mature design systems specify a
   component (anatomy, variants, properties, states, behaviour,
   accessibility, content rules), how are patterns and page
   templates built from components, how are visual decisions held as
   design tokens, and how do maintainers keep description and
   implementation the same?
7. A page as a composition of defined blocks: block editors and
   their templates, theme templates made of sections, page builders
   on structured content, server-driven UI, declarative card formats
   and formats by which an agent sends an interface, low-code page
   schemas. How does each divide what a block is and does from where
   it stands, and which troubles do they report?
8. What belongs to the whole application and to no single screen or
   linear path: addresses and deep links, the persistent frame of
   navigation, several windows or tabs, notifications and events
   that arrive unasked, offline and degraded states, one view
   differing by role. How is it described, and where is it kept:
   once for the application, or again on every screen?

**C. The agent and the build**

9. How do the AI coding and design tools of 2025 and 2026 want an
   interface described so that an agent builds it (design files of
   spec-driven kits, design files for agents, rules files, servers
   that give an agent a design system)? What do their makers
   prescribe, and what do practitioners report works or fails?
10. What do measured studies of 2025 and 2026 show about models and
    interfaces in both directions: an agent building an interface
    from a description (which input, among prose, a structured
    specification, a wireframe, a screenshot, tokens and a component
    library, gives the closest result, above all across several
    screens and their states), and a model writing a description
    from pictures of existing screens (what it gets right, misses,
    invents)? Read single-shot benchmarks of 2023 and 2024 as
    history only.
11. From text to something visible: text-to-wireframe languages,
    generated wireframes, generated clickable prototypes, components
    rendered in isolation. What does each need, what does a change
    cost, and at which stage do processes place the preview: with
    the definition or with the build?
12. Text and the design tool: how are a textual or code source and a
    design tool connected today, in which direction does each
    connection run, and what must a text-first description keep
    (identifiers, a component vocabulary, tokens) so that the
    connection can be added later?
13. The agent that proposes the description: how does an AI agent
    get from requirements, user stories and a solution design to a
    first proposal of an interface? What cannot be inferred from
    those documents and must be asked, which questions are asked and
    in which order, and how do published workflows keep the agent
    from inventing arbitrary layout and interaction?
14. Where a description becomes code: what do declarative interface
    languages (SwiftUI, Jetpack Compose, QML, XAML, HTML with
    components, MDX) show about the border between a readable
    description and code, how do their previews work, and what must
    a description above the code still hold?

**D. The breadth of the target**

15. Platforms: what differs in describing an interface for the web,
    the mobile web, native mobile and the desktop, and do products
    on several platforms keep one abstract description with platform
    variants or a description per platform?
16. What the description owes every user: which accessibility
    properties are specified at design time, how are the texts of
    the interface specified, how is internationalisation prepared,
    and how do specification templates carry these?

**E. The process and the judgement**

17. Where does interface work stand between requirements and build,
    what does it take from requirements and user stories and hand to
    the builders, and which outputs do lean and solo practices drop
    and keep, compared with a specialist in a team?
18. How is a design judged before it is built (heuristic evaluation,
    cognitive walkthrough, critique, checklists), can each method be
    run on a textual description or only on a picture or prototype,
    and what is known about models as evaluators?
19. Where did textual specifications of interfaces fail or get
    abandoned, what do their critics propose instead (the prototype
    as the specification, the code as the source of truth), and what
    kept true the descriptions that survive?
20. What the description cites and does not repeat: how does a
    description of an interface refer to the data model, validation
    and business rules, permissions, and the states and errors of
    the services behind it without repeating them, and what is
    reported about the two drifting apart?
21. The description after the first build: how is a change to it
    read and reviewed as a difference in text, how do changes made
    during the build get back into it, how do systems of shared
    definitions handle a screen that needs a variation of a shared
    element and show which pages a change to it touches, and how are
    such definitions versioned?
22. The description and the test: what has automated testing of
    interfaces learned about describing screens in modular text (the
    Page Object and Screenplay patterns, executable specifications),
    at which level of abstraction do such units survive a change of
    the interface, and how is a built interface checked against its
    description?

## Left out on purpose

Visual craft as such, research with users as a method, a comparison
of front-end frameworks or of code generators by vendor, voice and
conversational interfaces, games, AR and VR, embedded interfaces,
prices and licences.

## How to work

- Prefer primary sources: the standard itself, the method's author,
  a tool's own documentation, the paper. For design systems and AI
  tooling read the primary artefacts in public repositories
  (schemas, component and page files, agents' rules and prompt
  files, issue trackers) before commentary about them.
- Working specifications of real products mostly lie in private
  wikis; what is public is often an introduction or a polemic. Say
  so where a finding rests on one.
- Cite a write-up of someone else's result only when the original
  cannot be reached, and say so.
- For the AI tooling use sources of 2025 and 2026 and give their
  dates; for methods and standards use the lasting sources.
- Leave out pages with no author or date, marketing pages on a
  vendor's own market, and content farms.
- For every question run one search for the opposite of what you
  expect, and report what it found, including nothing.
- Where sources disagree, cite both and say that they disagree.
- Say plainly what you did not find. "No reliable source on X" is a
  result.
- Never state a source, a quotation, a date or a figure you did not
  open.

## The report I want

1. A summary of one page: the main findings and the recommendation.
2. The vocabulary of the field: the terms and what each means.
3. The questions 1 to 22 in order, each with its findings, every
   finding with its source and date, and with what was not found.
4. A comparison table of the candidate shapes of a description
   (unit: screen, object, element, path, and combinations): what
   each looks like, who uses it, its strengths and weaknesses, how
   it carries the four platforms, where the user's paths and the
   behaviour of the whole application live in it, how it reaches a
   visible preview, how an AI agent reads and writes it, how it is
   changed on a later cycle. Where you put a shape together from
   fragments and found it whole nowhere, say so and mark which part
   you found where.
5. A verdict on the idea of a definition per element with page
   files that refer to them.
6. A recommendation of the simplest shape to try first, with a short
   example of a search field and of one page that uses it.
7. What surprised you: findings that change the question itself.
8. The full list of sources, marked primary or secondary.
