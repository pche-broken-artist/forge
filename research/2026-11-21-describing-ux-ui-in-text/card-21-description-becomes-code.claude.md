---
date: 2026-11-21
project: forge
topic: where a description of an interface becomes code
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-21-description-becomes-code
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 21; no known note named by the card; web sources below
---

# Declarative interface languages already describe a screen readably, and what stays above the code is what it cannot say

<!-- Shape: templates/research.md -->

## In short

The six languages state, in a form their makers themselves call a
description, which elements a screen holds, how they nest, how they
look and what data each shows; a person can read and rearrange that
much. What they keep apart differs by family. The markup languages
(XAML, the UI files of QML) put logic in a paired file and the look in
resources or styles referred to by name; the component languages
(SwiftUI, Compose, React, Vue's single-file components, MDX) hold
structure, style and local logic together on principle and keep apart
only who owns the state. Previews are of two kinds: an isolated render
of one component from configurations and sample data declared in code,
and a live change of the running application. No maker's page says
outright what a description above the code must still hold. Assembled
from their scattered statements it is: the mockup and the shape of the
data, the names, the states worth showing with their sample data, what
goes into a screen and what events come out of it, the platform's own
interface guidance, and what of the problem did not make it into the
code. What the documentation says is sure (each vendor on its own
product); the list is the agent's own assembly. The disconfirming
query found nothing under its exact words and, reworded, found the
current it expected; that current's classical text itself keeps two
kinds of document above the code. Unexpected: the card takes
structure, state and style as kept apart, and the newer languages
reject that separation by file on principle.

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

Card 21, "Where a description becomes code", verbatim:

- **Question:** What do declarative interface languages (SwiftUI,
  Jetpack Compose, QML, XAML, HTML with components, MDX) show about
  the border between a readable description and code: what of an
  interface do they state in a form a person can read and rearrange,
  what do they keep apart (structure, state, style), how do their
  previews work, and what do their makers and users say a description
  above the code must still hold?
- **Why it matters:** if what the build produces is itself a readable
  description with an instant preview, the layer above it must hold
  only what the code cannot say.
- **What would answer it:** the languages' own documentation and their
  makers' writing.
- **Where to look:** the documentation of the declarative interface
  frameworks of the four platforms and of their preview tools; their
  makers' guidance on going from a design to code. Search words from
  card 1: "generative UI" for formats in which an agent emits an
  interface at run time, kept apart from a description handed to a
  build; "intermediate representation", "structured specification".
- **Disconfirming query:** "the code is the specification declarative
  UI"; expected: a current that holds the code to be the description.
- **Stop rule:** nothing new from a differently worded query and every
  route has a primary source; ten to fifteen pages opened.

Known items: none; the card names no known note of the project.

The baseline the note must beat is the sentence every introduction to
declarative interfaces repeats: such code "describes what, not how" and
is therefore readable. That sentence says nothing of which parts stay
readable once a general programming language enters the notation, of
what a preview needs from outside the code, or of what the makers
themselves leave above the code. The note beats it only where it says
these three from the makers' own pages, language by language.

## Key findings

**F1. All six notations state the same core readably: which elements a
screen holds, how they nest, how they look and what data they show;
their makers call this a description.** [consensus; vendor
documentation of their own products and one maker's conference talk]
Apple: "SwiftUI uses a declarative syntax, so you can simply state what
your user interface should do." (overview page, under "Declarative
syntax") [1]; its session says views "are descriptions of what the
current state of the UI should be" and "The code itself resembles the
hierarchy of views that it creates." (chapter "Fundamentals of views";
summarised fetch) [2]. Google: composable functions "describe the
target screen state instead of constructing UI widgets" (section "An
example composable function") [3]. Microsoft: "You describe your UI
structure and properties in `.xaml` files" (opening paragraph) [5].
Qt: "Declarative languages are strongly suited for defining UIs."
(section "Separate UI from Business Logic"; summarised fetch) [6].
Vue: one file with a template, a script and a style block
(Introduction) [7]. React: a hierarchy of named components, each
returning markup (Step 1 and Step 2) [8]. MDX: running prose with
components named inside it (F9) [9].

**F2. The markup family keeps logic and look out of the structure, by
file and by reference.** [consensus within the family; vendor
documentation] XAML: you "handle logic and events in a paired
code-behind file" (opening paragraph) [5]; the reusable look is
referred to by name: "A `ResourceDictionary` stores reusable objects —
brushes, styles, templates — identified by `x:Key`." (section
"Resource dictionaries") [5]; data arrives through binding markup
(`{x:Bind}`, `{Binding}`) and the theme through `{ThemeResource}`
(table in "Markup extensions") [5]. Its maker gives a division of
labour as the reason: "designers author the visual structure in XAML,
developers wire up logic in code-behind" (section "What is XAML?")
[5]. QML: "Qt Design Studio uses UI files that have the filename
extension .ui.qml to separate the visual parts of the UI from the UI
logic you implement in .qml files." (section "Using Qt Design Studio";
summarised fetch, which returned the sentence in two consecutive
pieces) [6]; the business logic belongs to another language
altogether: "Strongly typed languages, such as C++, are best suited
for an application's business logic, the backend." [6]; state lives in
models: "Don't store a state in a delegate." [6]; the look is a style
chosen for the controls, which the page tells not to customise where
it is the platform's native one (section "Do not customize native
styles") [6]. All of [6] rests on a summarised fetch.

**F3. The component family holds structure, style and local logic
together on principle, and keeps apart only who owns the state.**
[consensus within the family, contested against F2; vendor
documentation] Vue says it in so many words: "separation of concerns
is not equal to the separation of file types", and "Inside a
component, its template, logic, and styles are inherently coupled"
(section "What About Separation of Concerns?") [7]. SwiftUI: the look
is a chain of modifiers on the element, in the same code: "View
modifiers apply modifications onto a base view and can change any
aspect of that view."; state is declared and owned in one place: "the
container view's state becomes the only source of truth" (both
summarised fetch) [2]. Compose: "widgets are relatively stateless and
don't expose setter or getter functions"; data goes down as
parameters, and "the UI raises events such as `onClick`. Those events
should notify the app logic" (section "The declarative paradigm
shift") [3]. React: "Figure out the absolute minimal representation of
the state your application needs and compute everything else
on-demand." (Step 3) [8]. The two families disagree and both are
cited: [5] and [6] separate by file, [7] calls that separation dogma
when applied to file types.

**F4. The border between description and code runs where a general
programming language enters the notation; from there a person or a
tool can no longer simply read and rearrange it.** [emerging; vendor
documentation of four makers; the reading across them is the agent's
own] Compose embraces the language: "Because composable functions are
written in Kotlin instead of XML, they can be as dynamic as any other
Kotlin code." and "You can use `if` statements to decide if you want
to show a particular UI element. You can use loops." (section "Dynamic
content") [3]; and what reads from top to bottom does not run so: "you
might assume that the code is run in the order it appears. But this
isn't necessarily true." (section "Composable functions can execute in
any order") [3]. Qt guards a purely declarative part for its visual
tool: imperative code "interferes with tooling; Qt Quick Designer, for
example, doesn't support JavaScript." (section "Prefer Declarative
Bindings Over Imperative Assignments"), and for code the tool does not
support in a UI file: "Typically, you should move the unsupported code
to a .qml file." (both summarised fetch) [6]. Apple names where
imperative code stays: "imperative code is great when making a change
to state, or when there might not be an existing declarative
component" (summarised fetch) [2]. XAML is not debugged as code is:
"You can't set breakpoints in `.xaml` files" (section "Debug XAML")
[5].

**F5. The first kind of preview renders one component or screen in
isolation, from configurations and sample data that are themselves
declared in code.** [consensus; vendor documentation] Compose: a
second function carrying `@Preview` wraps the composable; "You can see
live updates to your composable preview as you make your edits."; the
annotation takes name, group, API level, width and height, locale,
font scale, system UI, background, UI mode, device and wallpaper
(section "Annotation class `@Preview`"); ready-made sets exist
(`@PreviewScreenSizes`, `@PreviewFontScales`, `@PreviewLightDark`,
`@PreviewDynamicColors`); sample data comes through
`@PreviewParameter`, "one preview per data element in the sequence";
the interactive mode is "isolated in a sandbox environment"; the
render runs in the editor on a ported part of the platform whose goal
is a preview "very close to its rendering on devices" [4]. Xcode: "Add
previews to your SwiftUI views using the preview macro."; in the live
or interactive mode "your view appears and interacts just like it
would on a device or simulator"; in select mode "Selecting a control
in the preview highlights the corresponding line of code in the source
editor."; the device settings cover "Dark Mode, landscape orientation,
or different sized text" (under "Xcode previews") [1]; "It quickly
shows you how your views look, including in different contexts."
(chapter "Built-in capability"; summarised fetch) [2]. For HTML with
components the same role is a separate tool's: "Stories are a
declarative syntax for supplying props and mock data to simulate
component variations." and "You can render a specific variation in
isolation by passing in props, mocking data, or faking events."
(summarised fetch) [10].

**F6. The isolated preview has stated limits, and its maker turns them
into a rule for how a screen is written: state in, events out.**
[vendor claim; one maker's documentation, explicit] The limits: "No
network access", "No file access", "Some `Context` APIs may not be
fully available" (section "Previews limitations") [4]; "The previews
system is not capable of constructing all of the parameters passed to
a `ViewModel`" (section "Previews and `ViewModels`") [4]. The rule:
"To leverage `@Preview` annotation most effectively, make sure to
define your screens in terms of the state it receives as input and the
events that it outputs." (introduction) [4]; a composable coupled to
the object that fetches its data is "less reusable, harder to test,
and unable to preview" (warning in the same section) [4]. A preview is
also not the device: the annotation's arguments "aren't applied to the
preview that is run and deployed" (note under "Run preview") [4]. No
other maker's page opened states the rule; Storybook's props and mock
data [10] are consistent with it.

**F7. The second kind of preview changes the running application, and
its maker says why: real state is hard to imitate at design time.**
[vendor documentation] XAML Hot Reload lets one build and test markup
"with the benefit of the running app's data context, authentication
state, and other real-world complexity that's hard to simulate during
design-time." (opening paragraph) [11]; it covers .NET MAUI, WPF, UWP
and WinUI 3, and "Starting in Visual Studio 2022 version 17.14 Preview
2, XAML Hot Reload and XAML Live Preview are available at design-time
and not just during a debugging session." (section "Where to get XAML
Hot Reload"; page dated 2025-04-24) [11]. The editor side of XAML is
"IntelliSense, auto-completion, and a visual design surface", with
designer-only namespaces that "support design-time tooling and can be
safely ignored at runtime" [5]. Vue lists "Out-of-the-box Hot-Module
Replacement (HMR) support" among the reasons for its file format
(section "Why SFC") [7]. Qt's page mentions "a live-preview for
prototyping applications" among a design tool's features (summarised
fetch; the sentence's subject was not returned) [6]. Apple: "Previews
are interactive even directly on device." (summarised fetch) [2].

**F8. Where a maker shows the way from a design to code, it places
above the code a mockup, the shape of the data and the names, and says
the thinking lies in state and interaction, not in the static
structure.** [single source for the explicit steps, a vendor's
tutorial; one maker's talk consistent on platform guidance] React:
"Imagine that you already have a JSON API and a mockup from a
designer." (section "Start with the mockup"); "If you work with a
designer, they may have already named these components in their design
tool. Ask them!" (Step 1); "UI and data models often have the same
information architecture" (Step 1); "Building a static version
requires a lot of typing and no thinking, but adding interactivity
requires a lot of thinking and not a lot of typing." (Step 2) [8].
"Design" there is the design of the interface held in a design tool.
Apple places the platform's interface guidance outside the framework:
"Every platform is unique in how it is used and therefore in how it is
designed.", "The Human Interface Guidelines describes components,
patterns, and their platform considerations.", and of the framework
itself "it is not Write Once and Run Everywhere" (chapter "Across all
platforms"; summarised fetch) [2]. Two makers disagree on where the
designer's work stands: [8] puts it above the code as a mockup, [5]
puts it inside the markup ("designers author the visual structure in
XAML").

**F9. MDX is the one of the six in which running prose and components
share a file; it is still code that is built, and its author must know
the component notation.** [vendor documentation; summarised fetch]
"More practically MDX can be explained as a format that combines
markdown with JSX" (section "What is MDX?"); "JSX is an extension to
JavaScript that looks like HTML but makes it convenient to use
components (reusable things)." (section "JSX"); "Note that components
must be defined."; the prerequisites paragraph begins "To write and
enjoy MDX, you should be familiar with both markdown" and goes on to
JavaScript and JSX (paraphrase of the fetch); the page's own heading
is "Markdown for the component era" [9]. Page published 2018-08-11,
modified 2025-01-27, by its own statement.

**F10. The current that holds the code to be the description exists.
Its classical text keeps two kinds of document above the code, and a
tool maker claims the title of source of truth for the rendered
states, not for the intent.** [contested; a practitioner's essay of
1992 and vendor documentation; both summarised fetch] Reeves takes as
his assumption that "final source code is the real software design",
and still names two uses of other documents: "to capture important
information from the problem space that did not make it directly into
the design" and "to document those aspects of the design that are
difficult to extract directly from the design itself", adding "Many of
these aspects are best depicted graphically." and "Never forget that
the source code determines what the actual design really is, not the
auxiliary documentation." (closing section) [12]. "Design" there is
the technical design of software, not the design of an interface; its
transfer to interface descriptions is the agent's. For interfaces the
claim is made by a preview tool: "Storybook is the single source of
truth for your UI.", its stories showing "how UIs actually work, not
just a picture of how they're supposed to work" [10]; and Apple calls
views "just declarative descriptions" [2]. None of the three says that
nothing is needed above the code.

**F11. Formats in which an agent emits an interface at run time share
the anatomy, a declarative tree over a catalogue of approved
components, and differ in author and moment; they are not a
description handed to a build.** [vendor claim; a vendor's
announcement, summarised fetch] "A2UI is a declarative data format,
not executable code."; "Your client application maintains a "catalog"
of trusted, pre-approved UI components"; "A2UI separates the UI
structure from the UI implementation."; the description is "generated
on the fly as structured output" by the agent, while the client's
developers own the components and the rendering [13]. Status by the
post of 2025-12-15: "Our format is currently at `v0.8`" [13]; a later
version was announced according to the search result list, not opened.

**F12. One research prototype for generating a whole application with
a model puts three intermediate representations above the code: a
storyboard, a data model and skeletons of the screens.** [single
source; a preprint with a user study, abstract page only, summarised
fetch] "It is challenging to generate the code for a complete user
interface using a Large Language Model (LLM)." (abstract, first
sentence) [14]; by the fetch's paraphrase of the abstract the three
representations are shared between the developer and the model, the
generated code is organised in several files, and 75% of the study's
participants preferred the prototype to a chat-style baseline [14].
The size and the method of the study were not read. Submitted
2025-08-27.

## Unexpected

The card assumes that the languages keep structure, state and style
apart. The newer ones do not, and say so: Vue's documentation calls
separation by file type a dogmatic reading of separation of concerns
and holds that template, logic and styles are "inherently coupled"
inside a component [7]; SwiftUI and Compose write the look as
modifiers on the element in the same code [2][3]. What these languages
separate is one component from another, and the owner of a piece of
state from its readers. The question is answered as put in F2 and F3;
the lead is that a description above the code may have to choose
between the two cuts as well, by concern or by component.

The maker of one preview tool has begun to hand the writing of
previews to an agent: "The AI agent in Android Studio can
automatically generate Compose previews for your composables." [4].
The states worth previewing are then no longer only a person's list; a
lead for the cards on previews and on the agent that proposes.

The live kind of preview exists because sample data is not enough:
Microsoft's page names "the running app's data context, authentication
state, and other real-world complexity that's hard to simulate during
design-time" [11]. For a stage that describes before anything is
built, only the isolated kind is available, and it needs someone to
name the states and supply the data (F5, F6).

The run-time format of F11 has the very shape of the idea under test,
elements defined once in a catalogue and a page that names which of
them it holds, with the difference that a renderer and not a person
reads it [13]. Whether that shape serves a person tuning a proposal is
not answered by its use between an agent and a renderer.

## Not found

- No maker's page that says outright what a description above its
  declarative code must still hold. Looked for in the pages of all six
  languages and in three searches; F8 and the list in "In short" are
  assembled from statements made for other purposes.
- No voice of users of SwiftUI or Compose on what a specification
  above their code must hold was opened. The search with those words
  returned research papers on generated interfaces and vendors' blogs;
  "users" in this note are Reeves [12] alone.
- Apple's reference documentation on previews and on state could not
  be read: its documentation page delivered only a title to the fetch,
  and two Markdown paths under the same host given by a search
  answered 404. SwiftUI rests on the overview page [1] and one session
  transcript [2].
- The web's own component standard (custom elements) was not opened;
  "HTML with components" rests on Vue [7], React [8] and Storybook
  [10].
- No page on theming or design systems in Compose was opened; how
  Compose keeps the look apart is known here only from the code
  samples of [3] and [4].
- Qt's preview tooling beyond one sentence of [6], and any preview for
  MDX, were not looked at.
- No measured study of how well people who do not program read or
  rearrange declarative interface code surfaced in any search; none
  was searched for by name.
- No page uses the phrase "the code is the specification" of
  declarative interfaces; the first query returned none.
- The practitioners' dispute over whether code or the design file is
  the source of truth appeared in one result list only (vendors' and
  practitioners' posts, split between code first, design file first
  and a neutral file between them); none was opened, being vendors'
  blogs on their own market or below the bar, and no finding rests on
  them.

## Options

1. **The layer above holds only what the code cannot say.** Reasons
   and intent, the states of each screen worth showing with their
   sample data, what goes into a screen and what comes out, the paths
   between screens, the names, the differences between platforms; the
   detailed nesting, the layout and the values of the look are left to
   the build's declarative code and its previews. For it: the least
   said twice and the least drift (F1, F10). Against it: before the
   first build nothing can be seen, while the frame wants the human to
   see the proposal before it is handed on; a preview of the
   description then needs a means of its own, which is another card's
   question.
2. **A definition per element in Markdown and a page definition that
   places them (the idea under test).** For it: readable without
   reading code, and one statement for four targets where the code is
   written per platform (F8). Against it: it says again what component
   code already says readably (F1, F3), in two places that will drift,
   and it spends its words on the static structure, where the makers
   put "a lot of typing and no thinking" (F8).
3. **The description is itself written in a declarative notation (MDX
   or HTML with components) and is its own preview.** For it: an
   instant preview and no translation for the web. Against it: one
   platform's notation for four targets, an author who must know the
   notation (F9), and a description that is already an implementation,
   against the frame's "Nothing is implemented there".
4. **A description shaped as the isolated previews demand.** Per
   screen: the state it receives, the events it gives out, the named
   states with their sample data, the elements by name only; each
   named state becomes one preview or one story at the build (F5, F6).
   For it: it maps one to one onto what the build stage must write
   anyway and gives the build something to check against. Against it:
   it asks of the author a discipline about state that a person
   without programming background may lack, and it says nothing of the
   look.

## Relevance to this project

The recommendation, the agent's own inference from F1, F3, F6, F8 and
F10: take options 1 and 4 together. Let the interface document hold
what declarative code cannot say (why, for whom, which paths, which
platform differences are wanted, what names things carry) and shape
its part on each screen the way the isolated previews need it: what
the screen receives, what events it gives out, which states are worth
seeing and with what data. Leave the detailed nesting of elements, the
layout and the values of the look to the build, whose code states them
readably and shows them at once.

This is chosen against option 2 as the default. The idea under test
has one real strength that the findings confirm: the code is written
per platform, and the layer above is the only place where one
statement holds for the web, native mobile and the desktop together
(F8). That argues for platform-neutral names and a list of wanted
differences in the layer above; it does not argue for restating, per
element, a structure that the component code will state again.

What it rests on is thin in one place and should be read so: no maker
says the list outright, the Apple evidence is an overview page and a
talk, the claim that the hard part is state and interaction is one
tutorial's sentence [8], and users are heard through one essay of 1992
on the technical design of software [12]. The frame's wish that the
human sees the proposal before the build is not met by this card's
findings: every preview found here needs code.

Consult when: deciding what the interface document holds and what it
leaves to the build; judging whether a definition per element earns
its place; shaping the per-screen part of a template (state in, events
out, named states, sample data); someone argues that the code is the
specification, or that a design file is; choosing whether a
description may be written in MDX or another notation that is built;
telling a run-time format for agents apart from a description handed
to a build.

## Sources

1. "SwiftUI", Apple Developer overview page; Apple; undated (footer
   copyright 2026 only);
   https://developer.apple.com/swiftui/ ; primary (vendor on its own
   product); read in full through the fetch tool, which returned the
   body text reproduced, navigation and footer links left out;
   original.
2. "SwiftUI essentials", WWDC24 session page with transcript; Apple;
   2024, dated by the session's year in the page;
   https://developer.apple.com/videos/play/wwdc2024/10150/ ; primary
   (the maker's talk); summarised fetch: selected quotations returned
   by the fetch tool's model, quoted here as returned; original.
3. "Thinking in Compose" (title as the search result list gave it; the
   fetch delivered the body without its title); Android Developers,
   Google; undated in the text delivered;
   https://developer.android.com/develop/ui/compose/mental-model ;
   primary (vendor on its own product); read in full, the page's text
   delivered whole; original.
4. Compose tooling page on composable previews and the `@Preview`
   annotation (title not delivered by the fetch); Android Developers,
   Google; undated in the text delivered;
   https://developer.android.com/develop/ui/compose/tooling/previews ;
   primary (vendor on its own product); read in full, the page's text
   delivered whole; original.
5. "XAML overview - Windows apps"; Microsoft Learn; 2026-07-27, dated
   by structured data (ms.date);
   https://learn.microsoft.com/en-us/windows/apps/develop/platform/xaml/xaml-overview ;
   primary (vendor on its own product); read in full, the page's text
   delivered whole; original.
6. "Best Practices for QML and Qt Quick", Qt 6.12.0 documentation (the
   version as the page title gave it); the Qt documentation at
   doc.qt.io; undated;
   https://doc.qt.io/qt-6/qtquick-bestpractices.html ; primary (vendor
   on its own product); summarised fetch, read twice: the list of
   headings and selected quotations, then the sections "Using Qt
   Design Studio", "Separate UI from Business Logic" (first
   paragraph), "Store State in Models", "Don't store state in
   delegates" and "Do not customize native styles" quoted piece by
   piece; original.
7. "Single-File Components", Vue.js guide; the Vue project; undated;
   https://vuejs.org/guide/scaling-up/sfc.html ; primary (the maker's
   documentation); read in full through the fetch tool, which returned
   the body text reproduced, navigation left out; original.
8. "Thinking in React", React documentation; the React project;
   undated;
   https://react.dev/learn/thinking-in-react ; primary (the maker's
   tutorial); read in full as to prose through the fetch tool, which
   returned the sentences reproduced and left the code samples out;
   original.
9. "What is MDX?", MDX documentation; the MDX project; published
   2018-08-11, modified 2025-01-27, by the page's own statement;
   https://mdxjs.com/docs/what-is-mdx/ ; primary (the maker's
   documentation); summarised fetch, read twice: a condensed account,
   then the headings and the first sentences of the sections, quoted
   here as returned; original.
10. "Why Storybook?", Storybook documentation, version 10.6 as the
    page showed it; the Storybook project; undated;
    https://storybook.js.org/docs/get-started/why-storybook ; primary
    (vendor on its own product); summarised fetch: selected quotations
    and paraphrase; original.
11. "XAML Hot Reload for WPF and UWP apps - Visual Studio (Windows)";
    Microsoft Learn; 2025-04-24, dated by structured data (ms.date;
    updated_at 2026-04-24);
    https://learn.microsoft.com/en-us/visualstudio/xaml-tools/xaml-hot-reload ;
    primary (vendor on its own product); read in full, the page's text
    delivered whole; original.
12. "What Is Software Design?", Jack W. Reeves; first in C++ Journal,
    Fall 1992; republished by developer.* magazine on 2005-02-23 as
    part one of "Code As Design: Three Essays", both dates by the
    page's own statement;
    https://www.developerdotstar.com/mag/articles/reeves_design.html ;
    primary (the author's essay); summarised fetch: selected
    quotations from the opening, the middle and the closing section; a
    republication of the journal article, the print original not
    reachable.
13. "Introducing A2UI: An open project for agent-driven interfaces";
    Google A2UI Team, Google Developers Blog; 2025-12-15, byline;
    https://developers.googleblog.com/en/introducing-a2ui-an-open-project-for-agent-driven-interfaces/ ;
    primary (vendor's announcement of its own project); summarised
    fetch: selected quotations; original.
14. "Athena: Intermediate Representations for Iterative Scaffolded App
    Generation with an LLM"; Jazbo Beason, Ruijia Cheng, Eldon Schoop,
    Jeffrey Nichols; arXiv:2508.20263, version 1, submitted
    2025-08-27, dated by the arXiv listing;
    https://arxiv.org/abs/2508.20263 ; primary (preprint); partially:
    the abstract page only, and that as a summarised fetch (one
    sentence quoted, the rest paraphrased by the fetch tool's model);
    original.

## Opened and not used

- Apple Developer Documentation page on previews in Xcode,
  https://developer.apple.com/documentation/xcode/previewing-your-apps-interface-in-xcode :
  the fetch received a title only, the body being rendered by script;
  nothing could be read, and previews in Xcode rest on [1] and [2].

## Search record

Queries, in order:

1. declarative UI, separation of structure, state and style, the four
   frameworks compared.
2. "the code is the specification" declarative UI (the card's
   disconfirming query).
3. Thinking in Compose, declarative paradigm, previews.
4. "source code is the design", Reeves, "What is software design" (the
   disconfirming query reworded).
5. Qt Quick best practices, separate UI from logic, .ui.qml.
6. design to code, "single source of truth", prototyping in SwiftUI
   previews.
7. A2UI, declarative generative UI specification.
8. XAML overview, code-behind, styles, resources.
9. UI code cannot express design intent; a specification beside
   SwiftUI or Compose code.
10. "source of truth", design system, code and not the design file
    (the disconfirming query reworded again).
11. "intermediate representation", "structured specification", an LLM
    generating interface code.
12. WWDC, SwiftUI essentials, declarative, compositional,
    state-driven.

Pages opened, fifteen: [3], [4], [6], [5], [1], the Apple
documentation page listed under "Opened and not used", [7], [9], [8],
[12], [2], [10], [13], [14], [11], in that order. Two of them, [9] and
[6], were fetched a second time for exact sentences. Two further
fetches failed and opened nothing: two Markdown paths under
developer.apple.com that a search had returned answered 404.

The disconfirming query: under its exact words (query 2) it found no
page that uses the phrase of declarative interfaces. Reworded (query
4) it found the current it expected in its classical form, Reeves's
essay [12], which was opened and which itself keeps two kinds of
document above the code (F10). Reworded again (query 10) it returned a
list of vendors' and practitioners' posts split between code as the
source of truth, the design file as the source of truth and a neutral
file between the two; none was opened. Among the makers' pages the
claim appears once outright, in a preview tool's documentation [10].

The run ended by the opening budget: fifteen pages were opened. At
that point every route of the card had a primary source, but the last
differently worded queries (10 and 11) still returned material not
seen before, so the first half of the card's stop rule was not met.
