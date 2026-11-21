---
date: 2026-11-21
project: forge
topic: what differs in describing an interface per platform, and whether one description or one per platform
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-12-platforms
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 12; no known notes named by the card; web sources below
---

# The platforms differ in navigation, input, windows and conventions; adaptation is specified by the size class of the window; one description with variants and a description per platform both exist

<!-- Shape: templates/research.md -->

## In short

The owners' guidelines prescribe different things on each platform for
all four matters the card names, and Apple states them in the same
five dimensions for a phone and for a desktop [1][2]. The three native
owners read (Apple, Android, Windows) all specify adaptive behaviour
by named size classes of the app's window and all warn against
deciding by device [3][5][8]; their classes differ (two, five and
three), so no one vocabulary can be borrowed for all. The web
standards name no platform at all, only conditions: the size of the
viewport or of a container, and the kind of pointer [9][10]. Both
shapes the card asks about exist in primary sources: one description
with platform variants (Apple, the first version of Material Design,
one product company) [3][4][15][18], and one design language with
documentation per platform (Fluent 2) [11][12], which Android's own
guide calls "not uncommon" [16]; the one account of a change of shape
runs from a system per platform toward one definition [19]. No source
compares the two by a measured outcome. Four sources agree on what
belongs to the platform and what stays shared: the behaviours of the
system and the controls of input follow the platform, the identity
and the content stay (F9). How sure: the prescriptions and the size
classes rest on the owners' own pages read in full and are firm; the
shapes and the criterion rest on vendors' documentation and two
product companies' accounts, none of them measured. The disconfirming
query, run in both its wordings over two rounds, found both camps, as
expected, and a mixed position on which the owners, the toolkit
vendor, the product companies and the practitioners end [13][14]
[16][17][18][19]. Unexpected: the card's four targets are not four
things of one kind. The owners separate the space available from the
platform's idiom, and the web standard makes the input a third axis,
so the mobile web is the web in a narrow window with a coarse
pointer, not a platform of its own.

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

> #### Card 12: The platforms
> - **Question:** What differs in describing an interface for the
>   web, the mobile web, native mobile and the desktop: what do the
>   platform guidelines prescribe (navigation, input, windows, the
>   system's conventions), how is responsive and adaptive behaviour
>   specified, and how do products and design systems on several
>   platforms describe one thing: one abstract description with
>   platform variants, or a description per platform?
> - **Why it matters:** the targets are four platforms, and the unit
>   and the layering of the description must carry them.
> - **What would answer it:** the platform owners' guidelines and the
>   documentation of design systems that span platforms.
> - **Where to look:** the human interface guidelines of the mobile
>   and desktop platforms; the adaptive-layout guidance of the large
>   design systems; web standards on responsive design.
> - **Disconfirming query:** "one design for all platforms fails",
>   "platform conventions against cross-platform consistency";
>   expected: both camps exist.
> - **Stop rule:** nothing new from a differently worded query and
>   every route has a primary source; ten to fifteen pages opened.

Known items: none; the card names no known note of the project.

The baseline, what the note must beat: the common knowledge that
mobile and desktop differ, that one follows each platform's human
interface guidelines and that layouts should be responsive. The note
beats it only where it names what each owner prescribes in its own
words, the unit in which adaptive behaviour is specified, and which
shape of description real systems on several platforms use, each from
a primary page opened in this run.

## Key findings

**F1. The owners prescribe different things for navigation, input,
windows and the system's conventions, and one owner states what
distinguishes a platform in the same five dimensions for each.**
[single source per platform: each owner's guideline, the authority
for its own platform; a standard for the web] Apple's pages
"Designing for iOS" and "Designing for macOS" run under the same
headings, Display, Ergonomics, Inputs, App interactions and System
features, followed by Best practices [1][2]. What the pages opened
prescribe, by platform:

| Platform | Navigation | Input | Windows | The system's conventions |
|---|---|---|---|---|
| iOS, the phone [1][3][4] | a tab bar floating at the bottom of the screen; a swipe to navigate back | Multi-Touch gestures, virtual keyboards, voice; controls within reach in the middle or bottom of the display | compact and regular size classes; safe areas around hardware features | widgets, Home Screen quick actions, Spotlight, Shortcuts, activity views; Dark Mode, Dynamic Type |
| iPadOS [3][4] | a tab bar near the top of the screen, convertible to a sidebar | not on the pages opened | resizable windows and multitasking; every combination of size classes | not on the pages opened |
| macOS [2][3] | a menu bar holding every command; more content in fewer nested levels, less modality | keyboard and pointing device first; keyboard shortcuts; high precision; touch for brief interactions on a Mac with a touch display | windows the user resizes, hides, shows and moves; full-screen mode; nothing critical at the bottom edge of a window | menu bar, file management, full screen, Dock menus; toolbars the user customises |
| Android [5][6][16] | a navigation bar at the bottom for the primary destinations, a top app bar with the title at the left; "up" in the app bar apart from the system's "back"; the panes of a canonical layout | back by the system's button or an edge swipe [16][17]; nothing on keyboard, mouse or pen on the pages opened | window size classes; split screen, foldables, freely resizable desktop-type windows | the system's bars at the top and at the bottom, the lower one by gestures or three buttons; bottom sheets and system dialogs; icons where iOS writes Cancel or Done; a motion of its own |
| Windows [7][8] | a navigation pane at the top or at the left; a compact pane on a small window, tabs on a large one | touch, pen, keyboard and mouse, all served by the standard controls | the app's window, not the screen, is the measure; three breakpoints in effective pixels | not on the pages opened (two conventions from a third party in F7) |
| The web and the mobile web [9][10] | nothing prescribed by the standards opened | the pointer (none, coarse, fine) and hover, as testable features | the viewport's width, height, aspect ratio and orientation; a container's own size | nothing prescribed by the standards opened |

In the owner's words: on the phone, "limiting the number of onscreen
controls" and "it’s especially important to let people swipe to
navigate back or initiate actions in a list row" [1, Best practices];
on the desktop, "Use the menu bar to give people easy access to all
the commands they need to do things in your app." and "Let people
resize, hide, show, and move your windows to fit their work style and
device configuration" [2, Best practices]. The youngest entry of the
macOS page's change log is 28 October 2026, "Added guidance for touch
input." [2].

Android's own guide for carrying an iOS design over, read in the
second round, states the differences between the two phones as steps:
"Swap the Tabbar (bottom navigation) for the Navigation Bar", "The
title is left aligned by default in the App Bar for Android.", and
the two ways back, "The up arrow moves the user up a level through an
app's navigation hierarchy in a user flow, while back or edge swipe
lives in the system navigation, moving the user backwards and even
taking the user out of the app." [16, steps 4 and 5].

**F2. Navigation is where the platforms differ in structure and not
in detail, and the owner states the difference as variants of one
component.** [single source: platform owner's guideline] Apple's page
on tab bars gives shared best practices and then, under "Platform
considerations": on iOS "A tab bar floats above content at the bottom
of the screen."; on iPadOS "The system displays a tab bar near the
top of the screen.", with the choice of "a button that converts it to
a sidebar"; on visionOS "a tab bar is always vertical"; and for the
rest one line, "No additional considerations for macOS. Not supported
in watchOS." [4]. The container of navigation also changes with the
space, on one platform: "Consider taking advantage of larger spaces
to switch from a tab bar to a sidebar" [3, Size classes]. Microsoft
says the same of its own control: "the nav pane and its compact,
transient UI works well for a smaller screen, but on a larger screen,
tabs might be a better choice" [7, Adaptive layout].

**F3. All three native owners specify adaptive behaviour by named
size classes of the app's window, never by device, and their classes
are not the same.** [consensus: three platform owners' guidelines
that agree independently]

| Owner | Classes | Thresholds on the page | Unit |
|---|---|---|---|
| Apple, for iOS and iPadOS [3] | compact, regular; one per dimension | none: the system sets the class from the device, the window and the multitasking state | points |
| Android [5] | width: compact, medium, expanded, large, extra-large; height: compact, medium, expanded | width 600, 840, 1200, 1600; height 480, 900 | dp |
| Windows [8] | small, medium, large | 640 and 1008 | effective pixels |

Apple: "Determine layout based on size classes, not device type or
orientation." [3, Size classes]. Android: window size classes "are
explicitly not determined by the size of the device screen", and
"Physical devices do not guarantee a specific window size class."
[5]. Windows: "design for the amount of screen space available to
your app (the app's window), not the physical screen size" [8, the
tip under the introduction]. Android's page says its first three
classes map to Material Design's layout guidance and that "large and
extra-large breakpoints have been added to better target desktop and
connected displays" [5]; the page carries no date in the text read,
so the thresholds are as read on 2026-11-21. A class measures
perceived size, not pixels: Windows files a television under small,
since "although the TV has 1080 physical pixels, it has only 540
effective pixels" [8, Why are TVs considered "small"?]. macOS has no
size classes on the pages read: the user resizes the window freely
[2].

**F4. What changes between the classes is said in a small vocabulary
of operations, in named layouts with a rule per class, and in rules
for the moment a class changes.** [consensus in substance, vocabulary
differing by owner: vendor guidelines] Microsoft names the
operations as headings: Reposition, Resize, Reflow, Show/hide,
Re-architect, and an Adaptive layout that "entirely replaces UI based
on the format it's presented in" [7]. Android names three canonical
layouts, list-detail, feed and supporting pane, "proven, versatile
layouts that provide an optimal user experience on a variety of form
factors", and writes each as a rule per width class: for list-detail
the expanded width shows both panes and "Medium- and compact-width
displays show either the list or the detail, depending on user
interaction with the app."; for the supporting pane "For
compact-width displays, place the supporting content below the main
content or inside a bottom sheet." and "For expanded width, give 70%
of the space to the main content, 30% to the supporting content."
[6]. The same page writes what happens when the class changes while
the app runs, as three rules that keep the state, the first being
that on narrowing "the detail pane remains visible and the list pane
is hidden" [6, List-detail]. Apple sets the limit of all this: "Keep
functionality the same as size classes change", the amount visible
may change and what the app can do may not [3, Size classes]. The
words "responsive" and "adaptive" are not shared: Microsoft
separates them, "*Responsive* design uses just one layout where the
content is fluid" against "*Adaptive* design is similar, but replaces
one layout with another layout" [7], while Android writes them as one
term, "responsive/adaptive layouts" [5].

**F5. For the web the standards specify responsive behaviour as
conditions on the environment or on a container, and input as a
capability; they name no platform.** [standard; both documents read
through a summarising fetch of their first 100,000 characters, the
quotes asked for a second time word for word] Media Queries Level 4,
a W3C Candidate Recommendation Draft of 19 February 2026: "A media
query is a method of testing certain aspects of the user agent or
device that the document is being displayed in." (section 2). Its
features cover the display area (width, height, aspect-ratio,
orientation, section 4) and the interaction (section 7): `pointer`
with the values none, coarse and fine, coarse being "The primary
input mechanism of the device includes a pointing device of limited
accuracy.", and `hover` with none and hover, hover being "Indicates
that the primary pointing device can easily hover over parts of the
page."; `any-pointer` and `any-hover` ask the same of every input
mechanism present [9]. CSS Conditional Rules Module Level 5, a W3C
Working Draft of 30 October 2025, adds container queries, which
"allow testing aspects of elements within the document (such as box
dimensions or computed styles), rather than on the document as a
whole" (section 5), with the example that "Media objects in the main
and sidebar areas will each respond to their own container context."
[10]. It is a Working Draft: the note read its text, not the state of
its support in browsers. The agent's inference, not the standards'
words: in these documents the mobile web is not a platform but a set
of conditions (a narrow viewport, a coarse pointer, no hover), and a
component may carry its own adaptive rule, measured against the place
it stands in.

**F6. Systems that span platforms describe one thing in both ways the
card names; both are documented in primary sources, and the one
account of a change of shape runs from a system per platform toward
one definition.** [contested in practice: three vendors' own
documentation, one owner's guide and two product companies' accounts;
no measured comparison found]
- One description with platform variants: Apple's Human Interface
  Guidelines. The two pages read, one a foundation and one a
  component, give the shared guidance first and close with "Platform
  considerations", one subsection per platform, and a line in words
  where a platform adds nothing or lacks the thing: "No additional
  considerations for iOS or iPadOS." [3], "No additional
  considerations for macOS. Not supported in watchOS." [4]. Two pages
  were read; the whole guideline was not surveyed.
- The same shape in a design system that spans other owners'
  platforms: the first version of Material Design. Its page "Platform
  adaptation" gives a rule under "When to adapt" and then
  recommendations under Toolbars, Iconography, Controls, Gestures and
  Typography, each with a line for Android, for iOS and for the web,
  as the summarising fetch returned its structure [15]. The page
  carries the notice "Material 1 is no longer maintained."; its
  successor's page returned no text and the current version was not
  opened.
- The same shape in a product company: Wealthfront (2022) writes one
  specification per component for Android, iOS and the web, a
  "component sheet", "a design-led exercise to explicitly list the
  specifications, or design tokens", then one proposal of the
  component's interface for all three, and only then does each
  platform build and document its own. "While not entirely accurate,
  you might say this is a “design once, build anywhere” approach." A
  name stays per platform where the platforms differ: a dialog on the
  web and a bottom sheet on mobile, sharing their tokens [18, read
  through a summarising fetch].
- One design language, a description per platform: Microsoft's Fluent
  2. Its page for developers says, as the summarising fetch returned
  it, that "Fluent's cohesive design language is carried through each
  platform-specific Fluent UI library", and names a library each for
  React, Web Components, Apple (iOS, iPadOS, macOS), Android, and
  WinUI for Windows, the last documented on another site [11]. The
  component documentation stands in a tree per platform: the page
  links one for React and one for iOS [11], and the iOS tree lists
  twelve components and calls itself "a customized subset of
  components that fits seamlessly with native Apple components" [12].
  In this shape the platforms do not hold the same set of things: a
  description per platform is not a translation of one list. An
  owner speaks for the shape: "Having platform-specific guidelines is
  not uncommon among multi-platform products and can make your own
  design system more user-centered." [16, Style and component guide].
- A change of shape: Spotify's design system began as systems per
  platform around a shared foundation, one for the web and one for
  the mobile apps. Its design manager writes that "When Encore was in
  its infancy, buttons varied widely across platforms." and that "By
  2022, it was evident that the pendulum had swung too far towards
  flexibility, and a recalibration was necessary." Components are now
  defined across the platforms from the start: people from iOS,
  Android and the web audit each one and agree an outline, which
  "might include a glossary of terms, the anatomy of the component,
  or any variants we need to support", and what differs stays marked,
  as in "custom focus states (platform-dependent)" [19, read through
  a summarising fetch]. It is one company's account, undated on the
  page (it names an event of September 2023), published in a design
  tool vendor's publication and crediting that vendor's product in
  passing.
- A third shape beside the two: one description with a variant per
  size class and none per platform, Android's canonical layouts [6].
Neither Apple's nor Fluent's page argues for its shape against the
other. [19] is the only source read that gives a reason for moving,
the drift of one thing between the platforms, and it is an account,
not a measurement.

**F7. Below the level of the screen, the conventions of single
controls differ by platform.** [consensus on the kind of difference,
not on each item: a toolkit vendor's documentation, one owner's guide
and a design system's guidance; all undated] Flutter's page on
platform idioms lists them: scrollbars, "Mobile users expect smaller
scrollbars that only appear while scrolling, whereas desktop users
generally expect omnipresent, larger scrollbars that they can click
or drag."; the modifier key of multi-selection, one on macOS and
another elsewhere, a single tap on touch; text that can be selected,
expected on the web; the context menu on a right-click and the
tooltip on hover, "essential for mouse users"; the menu bar, "On
Windows and Linux, this menu lives as part of the Chrome title bar,
whereas on macOS, it's located along the top of the primary
screen."; drag and drop, which on touch needs a handle or a long
press; and the order of the buttons of a dialog [13]. None of these
was checked against the owner's own guideline in this run, and on
the last the page disagrees with itself (Unexpected, third entry).
The second round adds differences of the same kind from three more
pages, one of them an owner's. Flutter's page on automatic
adaptations: the way back, "the OS back button" on Android and "an
edge swipe gesture" on iOS; the transition between pages; the
physics of scrolling and what happens past the edge; the system's
font; the overflow icon, whose "three dots are horizontal on iOS and
vertical on Android"; haptic feedback; and what a tap and a long
press do in a text field [17]. Android's guide: icons where "iOS
navbars will use text", tabs where iOS has segmented controls, and
"Android and iOS have distinct motion design, which should be
respected for each platform." [16]. The first version of Material
Design, as summarised: titles at the left on Android and the web and
centred on iOS, and "Edge swipes should not be used on the web."
[15].

**F8. The disconfirming query found both camps, as expected, and a
mixed position on which the sources end.** [contested: vendor
guidance, product companies' accounts and practitioner claims; no
controlled study found]
- For the platform's conventions: Flutter, a toolkit whose offer is
  one codebase for all platforms, says that reflecting platform
  standards serves to "Reduce cognitive load" and "Build trust" and
  advises, "If possible, assign someone as an advocate for each
  platform." [13]. Apple asks to "keep layout changes recognizable
  and familiar to the platform" [3, Size classes].
- For consistency across platforms: the same Flutter page, under
  "Stay unique", "Conforming to expected behaviors doesn't mean that
  your app needs to use default components or styling.", and "The
  more you can consolidate styling and behavior across platforms, the
  easier development and testing will be." [13]. Fluent 2 offers one
  language on every platform [11].
- The mixed position: a case study of 2015 by two practitioners names
  "The Brand-Oriented Approach", "The Platform-Oriented Approach" and
  "The Mixed Approach" with example apps for each, and ends, "Even
  though the mixed method seems to be the way to go, I’d say none of
  the approaches mentioned in this article is perfect.", and "you’re
  most likely to succeed using the platform-oriented approach,
  especially if your app is full of features, and targets a large
  user audience." [14, read through a summarising fetch]. It is old,
  it gives examples and no measurement, and the authors were not
  read laterally.
- The second round: the second wording, "one design for all
  platforms fails", returned opinion pieces on both sides and no
  measurement; none of them was opened, the openings going to
  primaries (Search record). The primaries opened in that round
  stand in both camps at once. Android's guide wants each platform's
  bars and motion respected and lets the brand "come through as
  color, type, and shape" [16]. Wealthfront shares the tokens and the
  component's interface, and "However, the exact positioning respects
  each platform’s existing standards to match user expectations."
  [18]. Spotify pulled its platforms back together and kept what
  depends on the platform marked as such [19].
- What it did to the answer: nothing opened in either round claims
  that one identical interface on all platforms is right as a rule,
  and nothing opened measures a failure of one. The mixed position of
  the first round holds and is firmer: it is what two owners, a
  toolkit vendor and two product companies say, and it now has a
  criterion (F9).

**F9. Four sources draw the same line between what varies by platform
and what stays shared: the behaviours of the system and the controls
of input and selection follow the platform; the identity and the
content stay.** [emerging: a design system's guidance in an
unmaintained version, one owner's guide, a toolkit vendor's
documentation and a product company's account; no study; found in the
second round]
- Material Design, first version, under "When to adapt": "These
  differences in convention can affect the user's ability to
  understand the UI or complete certain tasks.", and against it, "In
  areas where design differences are minimally disruptive, adapting
  to the platform is optional." [15].
- Flutter, under "Adaptation philosophy", separates two cases:
  "Things that are behaviors of the OS environment (such as text
  editing and scrolling) and that would be 'wrong' if a different
  behavior took place.", which the toolkit adapts by itself, and
  "Things that are conventionally implemented in apps using the OEM's
  SDKs", for which it "doesn't adapt automatically when app design
  choices are needed". Of the controls for input and selection it
  says, "Because these controls are tightly integrated with the
  operating system, users have been trained to recognize and respond
  to them. Therefore, we recommend that you follow platform
  conventions.", and of text fields, "Since text fields require user
  input, their design should follow platform conventions." [17].
- Android: "Both Android and iOS adhere to the idea that content
  comes first.", and "After that, branding can come through as
  color, type, and shape." [16, introduction].
- Wealthfront shares tokens and the component's interface and leaves
  the positioning to each platform [18]; where the platforms' minimum
  sizes of a touch target differ, "The simplest is to pick the
  largest minimum since this guarantees the others are met as well."
  [18].
The line is not drawn alike for navigation. Flutter counts the bar of
destinations to the identity, "Since tab bars are persistent across
your app, they should match your own branding." [17], while Apple and
Android prescribe its place and kind per platform (F2, [16]).

## Unexpected

The card assumes that the web, the mobile web, native mobile and the
desktop are four targets of one kind, four platforms the description
must carry. The sources say that this does not hold. Apple separates
the space from the idiom: a resized app changes its size classes
while "its idiom — the device type it’s made for — remains the same"
[3]. Android says that the class "can change throughout the lifetime
of your app" and that a device does not determine it [5]. The web
standard makes the input a thing tested on its own [9]. That is three
axes, the space available, the platform's idiom and the input, and
the four targets are points in them: the mobile web differs from the
web in space and pointer and not in idiom, and a phone app can stand
in a desktop window, by iPhone Mirroring on a Mac [3] or as an
Android app in a resizable window on ChromeOS [5]. The card is
answered above as it was put.

The borders between the platforms moved in the year of this note.
Apple's page for the desktop gained guidance for touch on 28 October
2026, "On a Mac with a touch display, people reach forward to touch
the screen" [2], and Android's classes gained two "to better target
desktop and connected displays" [5]. A convention moves in time as
well: the unmaintained first version of Material Design gave the
swipe from the left edge on Android to a hidden drawer, as its
summary returned it [15], where Android's guide today counts "back or
edge swipe" to the system's navigation [16]. A lead, not a
conclusion: a description that fixes "the desktop means keyboard and
pointer, the phone means touch", or any one convention, as a lasting
fact of the platform would age.

Flutter's page on platform idioms contradicts itself on a convention
it uses as its example. Under "Find a platform advocate": "the
default button in a dialog is typically on the left on Mac and Linux,
but is on the right on Windows". Under "Horizontal button order": "On
Windows, when presenting a row of buttons, the confirmation button is
placed at the start of the row (left side). On all other platforms,
it's the opposite." [13]. Both cannot hold, and the owners' pages
opened here do not settle it. A lead: a platform's convention written
in prose from memory goes wrong even in a vendor's own guide on the
subject.

Some of what a platform does is, by a vendor's own word, hard to put
into words at all: the two phones "have complex scrolling physics
simulations that are difficult to describe verbally" [17, Physics
simulation]. A lead for a description in text: the behaviours of the
system (F9, the first of Flutter's two cases) are named as the
platform's default and not described.

Four targets are few. Spotify's account counts "45 unique platforms,
and over 2,000 types of devices spread across 200 brands" [19]; the
article is undated, written about 2023, and the summary places the
figure in a strategy of 2019. A lead: where the targets are many, a
description per target is no longer a choice, which may be part of
why that company moved (F6).

## Not found

- No source that compares one description with platform variants
  against a description per platform by a measured outcome, in either
  round. The nearest is one company's account of its own move [19].
- No measured study, in either direction, of one identical interface
  on all platforms; [14] gives examples only, and the second
  wording of the disconfirming query returned opinion pieces.
- No owner's guideline for the web or the mobile web as a platform,
  comparable to the human interface guidelines of the native
  platforms, among what was opened. The standards [9][10] give
  mechanisms and prescribe no navigation and no conventions; where
  the web's conventions are written down was not established.
- Material Design's current guidance on adapting across platforms:
  the rule was read in the unmaintained first version only [15]; the
  second version's page returned a title and no text; the current
  version's layout guidance, to which the Android pages point, was
  not opened.
- Spotify's own article on its site about its family of design
  systems: its address answered with a redirect whose target answered
  "not found"; the company's account is read from [19] instead.
- "Finding platform balance in a design system" by a design-systems
  consultancy, returned by the differently worded query: the server
  answered with an error; nothing was read.
- Seen in the second round's result lists and not opened, the eight
  openings being spent on primaries: a product company's article on
  parity between platforms in a design tool vendor's publication; an
  introduction to multi-platform design systems; a known software
  author's short piece on cross-platform mobile development; several
  blogs for and against following native patterns.
- Design tokens as a layer shared under descriptions per platform:
  met in [18] and [19] as the shared part, not researched; the
  subject of the card on components in design systems.
- Guidelines of the Linux desktops; Android's guidance on keyboard,
  mouse and pen; Windows guidance beyond its two pages on layout;
  Fluent 2's trees for Android and the web, so that whether one
  component is described alike in each tree is not known.
- A date for the pages [1], [5], [6], [11], [12], [13], [15], [16],
  [17] and [19]: none in the text returned.
- Flutter's own definitions of "responsive" and "adaptive": seen in a
  search result's summary only, the page not opened, and therefore
  not cited; F4 gives Microsoft's alone.
- Accessibility requirements that bear on reflow and target size were
  left to the card on accessibility and wording.

## Options

1. **One description, closed by a block of platform variants** (the
   shape of [3][4], [15] and [18]). Each element or page is described
   once; a fixed closing section holds what differs on each platform
   and says in words when nothing differs or the thing does not exist
   there. For: one place of truth, the differences side by side,
   cheap where the platforms agree, and a criterion for what enters
   the block (F9). Against: the shared part quietly takes one
   platform as its default, and the block grows heavy where a thing
   differs in structure, as navigation does (F2).
2. **One shared language, a description per platform** (the shape of
   [11][12], spoken for by [16]). Principles and vocabulary are
   shared; elements and pages are described per platform. For: each
   description reads as native, can be handed whole to whoever builds
   that platform, and the platforms may hold different sets of
   things. Against: one intent written several times, drift between
   the copies, which is what one company reports of its own [19], and
   no place that shows what is the same on purpose.
3. **One description with a rule per size class, the idiom kept
   apart** (what [3], [5] and [8] prescribe when read together). The
   description says what is repositioned, resized, reflowed, shown,
   hidden or re-architected in each named class (F4); a separate
   short block holds only what the platform's idiom changes. For: it
   follows all three owners and the web standard, and it carries the
   mobile web without a description of its own. Against: the project
   must fix its own names and thresholds of classes, the owners'
   differing (F3), and two kinds of variation must be kept apart by
   whoever writes.
4. **Named layouts cited by the page** (the shape of [6]). A page
   names a layout such as list-detail and takes over its rule per
   class and its rules of transition. For: the adaptive rules are
   written once and cited. Against: it covers the common patterns
   only, and the vocabulary found is one owner's.

Options 3 and 4 combine with either of the first two; options 1 and 2
exclude each other for any one element.

## Relevance to this project

The recommendation is the agent's own inference from F3, F4, F6, F9
and the first entry under Unexpected: describe each thing once and
give the description two separate places for variation, a rule per
size class in the vocabulary of F4, and a closing block of platform
considerations held to the idiom (the container of navigation, the
input, the behaviour of windows, the system's conventions), in which
"nothing differs here" and "does not exist here" are written out as
Apple writes them; and let a page cite a named layout where one fits.
What enters the block follows the line of F9: the behaviours of the
system and the controls of input and selection, named as the
platform's default and not described; the identity and the content
stay in the shared part. It rests on three owners agreeing that
layout follows the window and not the device, on the owner whose
guideline spans several platforms using exactly such a closing block,
and, since the second round, on a product company that specifies a
component once for three platforms [18] and another that came back
from systems per platform [19]. It is chosen against a description
per platform, whose price in a chain of versioned documents is one
intent kept in several files, and against a single undivided
description, which every owner's guideline read here contradicts. No
source establishes by measurement that this shape works better than
Fluent 2's, and a project whose platforms are built by separate
people may be served better by option 2, as Android's guide allows
[16].

For the idea under test, again the agent's inference: the differences
found do not sit at one level. A control's conventions and its input
sit with the element [13][17]; the layout per size class sits with
the page [6]; the container of navigation and the system's features
sit above the page, with the application [1][2][4][16]. A structure
of element definitions and page definitions alone has no place for
the third. Container queries [10] are evidence that an element can
carry an adaptive rule of its own, measured against the place it
stands in and not against the screen.

Two cautions follow from what was read. A platform's convention is
written from the owner's current guideline with a citation, never
from memory (Unexpected, second and third entries). A size class is
named by space and not by device, a television being "small" [8].

Consult when: the layering of the interface description is decided;
the template of an element or of a page gets its section for
variants; the project fixes its vocabulary of size classes; a project
names more than one target platform; someone proposes a description
per platform, or one identical interface everywhere.

## Sources

1. "Designing for iOS", Human Interface Guidelines, Apple. Undated:
   the page carries no change log, only a copyright line of 2026.
   https://developer.apple.com/design/human-interface-guidelines/designing-for-ios.md
   Primary. Read in full (the publisher's Markdown rendition of the
   page, returned whole). Original.
2. "Designing for macOS", Human Interface Guidelines, Apple. 28
   October 2026, dated by the youngest entry of the page's change
   log.
   https://developer.apple.com/design/human-interface-guidelines/designing-for-macos.md
   Primary. Read in full (the Markdown rendition, returned whole).
   Original.
3. "Layout", Human Interface Guidelines, Apple. 9 September 2026,
   dated by the youngest entry of the page's change log.
   https://developer.apple.com/design/human-interface-guidelines/layout.md
   Primary. Read in full (the Markdown rendition, returned whole).
   Original.
4. "Tab bars", Human Interface Guidelines, Apple. 8 June 2026, dated
   by the youngest entry of the page's change log.
   https://developer.apple.com/design/human-interface-guidelines/tab-bars.md
   Primary. Read in full (the Markdown rendition, returned whole).
   Original.
5. "Use window size classes", Android Developers, Google. Undated in
   the text returned.
   https://developer.android.com/develop/adaptive-apps/guides/use-window-size-classes
   Primary. Read in full (the page's text returned whole). Original.
6. "Canonical layouts", Android Developers, Google. Undated in the
   text returned.
   https://developer.android.com/develop/adaptive-apps/guides/canonical-layouts
   Primary. Read in full (the page's text returned whole). Original.
7. "Responsive design techniques", Windows apps, Microsoft Learn,
   Microsoft. 22 July 2026, dated by the page's metadata (`ms.date`;
   `updated_at` 17 July 2026).
   https://learn.microsoft.com/en-us/windows/apps/design/layout/responsive-design
   Primary. Read in full (the page's text returned whole). Original.
8. "Screen sizes and breakpoints for responsive design", Windows
   apps, Microsoft Learn, Microsoft. 13 July 2026, dated by the
   page's metadata (`ms.date`).
   https://learn.microsoft.com/en-us/windows/apps/design/layout/screen-sizes-and-breakpoints-for-responsive-design
   Primary. Read in full (the page's text returned whole). Original.
9. "Media Queries Level 4", W3C, CSS Working Group. W3C Candidate
   Recommendation Draft, 19 February 2026, dated by the status line
   printed at its head.
   https://www.w3.org/TR/mediaqueries-4/
   Primary. Summarised fetch of the first 100,000 of 137,299
   characters: the status line, sections 2, 4 and 7; the quotes asked
   for a second time word for word. Original.
10. "CSS Conditional Rules Module Level 5", W3C, CSS Working Group.
    W3C Working Draft, 30 October 2025, dated by the status line
    printed at its head.
    https://www.w3.org/TR/css-conditional-5/
    Primary. Summarised fetch of the first 100,000 of 257,083
    characters: the status line, the introduction and the opening of
    section 5; the quotes asked for a second time word for word.
    Original.
11. "Develop", Fluent 2 Design System, Microsoft. Undated.
    https://fluent2.microsoft.design/get-started/develop
    Primary (a vendor's documentation of its own product). Summarised
    fetch of the whole page, its links listed on a second asking; the
    quote is as the summary returned it. Original.
12. "iOS Library Overview", Fluent 2 Design System, Microsoft.
    Undated.
    https://fluent2.microsoft.design/components/ios/
    Primary (a vendor's documentation of its own product). Summarised
    fetch of the whole page; the quote asked for a second time word
    for word. Original.
13. "Platform idioms", Flutter documentation, Google. Undated in the
    text returned.
    https://docs.flutter.dev/ui/adaptive-responsive/idioms.md
    Primary for the toolkit's own guidance, secondary for the
    conventions of the platforms it reports. Read in full (the
    publisher's Markdown rendition of the page, returned whole).
    Original.
14. "Approaches For Multiplatform UI Design Adaptation: A Case
    Study", Sergii Ganushchak and Kate Abrosimova, Smashing Magazine.
    1 September 2015, dated by the byline.
    https://www.smashingmagazine.com/2015/09/approaches-for-multiplatform-ui-design-adaptation/
    Secondary (practitioners' article; primary only for its authors'
    own opinion). Summarised fetch of the whole article; the byline,
    the three headings and the two closing sentences asked for a
    second time word for word. Original.
15. "Platform adaptation", Material Design, first version, Google.
    Undated; the page says of itself that the version is no longer
    maintained. Second round.
    https://m1.material.io/platforms/platform-adaptation.html
    Primary (a design system's own guidance, in a superseded
    version). Summarised fetch of the whole page; the notice and the
    sentences of "When to adapt" asked for a second time word for
    word, the recommendations per platform as summarised. Original.
16. The guide on translating iOS designs to Android (ten numbered
    steps and "Style and component guide"; the fetch returned no
    title), Android Developers, Google. Undated in the text returned.
    Second round.
    https://developer.android.com/design/ui/mobile/guides/foundations/translate-designs
    Primary. Read in full (the page's text returned whole). Original.
17. "Automatic platform adaptations", Flutter documentation, Google.
    Undated in the text returned. Second round.
    https://docs.flutter.dev/ui/adaptive-responsive/platform-adaptations.md
    Primary for the toolkit's own behaviour and guidance, secondary
    for the conventions of the platforms it reports. Read in full
    (the publisher's Markdown rendition of the page, returned whole).
    Original.
18. "Building Wealthfront's multi-platform design system", Spencer
    Miskoviak, Wealthfront Engineering Blog. 10 May 2022, dated by
    the byline and by the address. Second round.
    https://eng.wealthfront.com/2022/05/10/building-wealthfronts-multi-platform-design-system/
    Primary (a product company's account of its own design system).
    Summarised fetch of the whole article; the quotes asked for a
    second time word for word. Original.
19. "How Spotify's design system goes beyond platforms", Juli Sombat
    (Design Manager, Design Systems, Spotify), in "A design systems
    publication by Figma". Undated on the page; it names an event of
    20 September 2023 as ahead. Second round.
    https://www.designsystems.com/how-spotifys-design-system-goes-beyond-platforms/
    Primary for the author's account of her employer's system; the
    venue is a design tool vendor's publication, and the article
    credits that vendor's product. Summarised fetch of the whole
    article; the quotes asked for a second time word for word.
    Original as far as could be told: the page notes a publication on
    the same vendor's blog as well, which was not opened.

## Opened and not used

- First round. "Cross-platform adaptation", Material Design (the
  second version's site), Google,
  https://m2.material.io/design/platform-guidance/cross-platform-adaptation.html
  : the page answered and returned its title and no text, its content
  being drawn by script; nothing to read, so nothing cited. The rule
  it was opened for is cited from the first version [15].
- Second round. Spotify's own article on its family of design
  systems, at its design site: the address answered with a redirect
  to another of the company's hosts, and that target answered "not
  found". Two fetches, nothing read; no address is given here because
  neither opens. Superseded by [19].
- Second round. "Finding platform balance in a design system", a
  design-systems consultancy's article: the server answered with an
  error. One fetch, nothing read; no address is given here because it
  did not open.

## Search record

Why there were two rounds: in the first the search tool refused every
query after the sixth, the session's search budget being spent, so
three queries of the card could not be run, the second wording of the
disconfirming query among them. When search worked again the run's
coordinator ordered a second round: the refused queries, one
differently worded query for the stop rule, and at most eight further
openings.

First round, queries run, in order:
1. Material Design 3 window size classes, canonical layouts, adaptive
   design.
2. Apple Human Interface Guidelines, designing for macOS and iOS,
   platform conventions, navigation, layout.
3. Platform conventions against cross-platform consistency, design
   system, one design for all platforms (the disconfirming query,
   first wording).
4. Fluent 2 design system, component, web, iOS, Android, Windows,
   platform differences, documentation.
5. Flutter documentation, adaptive and responsive design, platform
   idioms, best practices.
6. W3C container queries, media queries, specification, responsive
   design.

First round, pages opened, fifteen openings, in order: [3], [2], [1],
[4], [5], [6], [7], [11], [13], [10], [9], [8], [14], [12], and the
Material Design page of the second version under Opened and not used.
The addresses of [1], [4], [7], [8], [9] and that Material Design
page did not come from a result list; they were tried on the
publishers' own sites and are cited only because they opened. Five
pages, [9], [10], [11], [12] and [14], were asked a second time for
exact wording; the same page each time, not counted as a new opening.
The first round ended by the opening budget.

Second round, queries run, four, in order:
7. "One design" for all platforms fails, native feel, users expect
   platform conventions, identical interface on iOS, Android and the
   web (the disconfirming query, second wording; refused in the first
   round).
8. A product company's family of design systems across the web and
   mobile, Spotify's named (refused in the first round).
9. Material Design, cross-platform adaptation, when to adapt,
   platform conventions, brand (refused in the first round).
10. Multi-platform design system documentation: one shared component
    specification with platform variants against separate guidelines
    per platform (the differently worded query for the stop rule).

Second round, pages opened, eight fetches, in order: [15]; Spotify's
own article, which answered with a redirect; [18]; [16]; [17]; the
redirect's target, which answered "not found"; the consultancy's
article, which answered with a server error; [19]. Five delivered
text and three delivered none. Query 9 led to [15], [16] and [17],
query 10 to [18], queries 8 and 10 to [19]. Three pages, [15], [18]
and [19], were asked a second time for exact wording, not counted as
new openings. At the end of the round every address in this note was
requested once more and each answered.

The disconfirming query. Its first wording (query 3) found the case
study [14] and otherwise blogs and vendors' pages on their own
market, not opened. Its second wording (query 7) found [14] again and
opinion pieces on both sides: for following each platform, among
them a known software author's piece and a press article of 2013;
for one interface everywhere, a blog arguing that native patterns
need not always be followed and a toolkit vendor's post on its own
market. None is a measurement and none was opened. Read with the
primaries of both rounds it shows both camps, as expected, and the
mixed position of F8 and F9.

The stop rule after two rounds. Its first half is not met: the one
differently worded query (query 10) still returned sources not seen
before, two of which changed the note ([18] and [19], in F6, F8 and
F9), and three more that were not read, one answering with a server
error and two left unopened when the eight openings were spent. Its
second half is met: every route has a primary source, the owners'
guidelines, the adaptive-layout guidance, the web standards, and the
design systems on several platforms, these now with three vendors'
documentation and two product companies' accounts. The count of the
rule, ten to fifteen pages, was passed on the coordinator's order:
fifteen openings in the first round and eight in the second. The
second round ended by its opening budget.
