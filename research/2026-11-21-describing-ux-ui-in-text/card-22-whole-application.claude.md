---
date: 2026-11-21
project: forge
topic: what belongs to the whole application, outside screens and paths, and where a description keeps it
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-22-whole-application
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 22; no known note named by the card; web sources below
---

# Behaviour of the whole application stands above the screen and is kept once, at the level where it holds

<!-- Shape: templates/research.md -->

## In short

Five of the six behaviours the card lists are written by the platform
owners as rules about the application, in pages of their own and not
on a screen: addresses and deep links, the frame of navigation,
windows and tabs, notifications, offline states [1]-[7]. The sixth,
a view that differs by role, was found only in a modelling standard,
IFML, which keeps it as a context declared once [11]. Three
standards have a unit above the screen in which such rules stand:
the W3C manifest of a web application [8], the "set of web pages" of
WCAG [9] and the IFML model [11]. Where the sources say anything
about the place, they say once, with the lower level referring
upward [12][13], and the platforms' own artefacts are built that
way. This is well supported for the existence of the level (primary
sources on every route but role in platform guidelines) and weakly
for the form of a document: no template of an interface
specification with a named section for it was found, and the two
sources on the place are an architecture template and one
practitioner. The disconfirming query found nothing, as expected:
nobody was found arguing that it needs no place. The unexpected
thing: the sources have three levels, not the card's two. Between
the application and the screen stands the section (a nested layout,
a nested navigation graph, a nested container), and a rule lives at
the highest level where it holds.

## Question

The frame, condensed from the plan: a framework carries an idea down
a chain of versioned Markdown documents worked by a human with an AI
agent; its author wants a document of the same kind for the user
interface of an application, proposed by an agent, tuned by a human
and handed to a build stage, for the web, the mobile web, native
mobile and the desktop. One idea from practice is under test: every
element of a screen has a small definition of its own and a page
definition names which elements it holds and where they stand.

The card, verbatim:

> #### Card 22: What belongs to the whole application
> - **Question:** Which behaviour of an application lies outside any
>   single screen and any linear path (addresses and deep links, the
>   persistent frame of navigation, several windows or tabs and their
>   state, notifications and events that arrive unasked, offline and
>   degraded states, one view differing by role and permission), how
>   do platform guidelines and specification practice describe it,
>   and where is it kept in a description: once for the application,
>   or again on every screen?
> - **Why it matters:** a description built only from screens,
>   elements and paths has no place for it, and every candidate shape
>   must say where it lives.
> - **What would answer it:** the platform owners' guidelines and the
>   web's standards on behaviour at the level of the application.
> - **Where to look:** platform guidelines on navigation, deep links,
>   notifications, windows and offline behaviour; web standards and
>   guidance on routing and on working offline; specification
>   templates that carry a section for the rules of the whole
>   application. Search words from card 1: "design specs", "wireframe
>   annotations", "prototype specifications", "wireflows", "state
>   matrix"; and the model-based words "abstract user interface",
>   "concrete user interface", IFML's "view container", "view
>   component", "interaction flow".
> - **Disconfirming query:** "per-screen specification is enough",
>   "global UI rules section unnecessary"; expected: nothing argues
>   that it needs no place.
> - **Stop rule:** nothing new from a differently worded query and
>   every route has a primary source; ten to fifteen pages opened.

The baseline the note must beat is the answer anyone gives without
looking: "put the global things into a global section". To beat it
the note has to show from primary sources that each listed behaviour
is in fact described above the screen by those who own the
platforms, what such a description contains, and what the sources
say about its place, instead of taking the card's either/or (once
for the application, or on every screen) as given.

## Key findings

**F1. Five of the six behaviours are written by the platform owners
as rules about the application, in pages of their own beside the
pages on components; the sixth, the view that differs by role, was
found in no platform guideline read.** [consensus among the platform
owners read; vendor guidelines, no study] Android states its
navigation rules as principles for every app [1]. Microsoft starts
from the app as "a collection of pages" and derives the structure
and the frame from it ([2], opening paragraph). Apple has one page
each for multitasking [3], windows [4] and managing notifications
[5], none of which describes a screen. Google's guidance for the web
has an article on offline behaviour [6] and one on signing out that
covers the other open tabs [7]. In every one the subject of the
sentence is the app: "Every app you build has a fixed start
destination" ([1], under "Fixed start destination"); "your app or
game always needs to be prepared to save and restore their context"
([3], under "Best practices"). On a view by role no platform page
was read: the one guideline the search offered refused the request
[14].

**F2. Addresses and deep links are described in two parts, both
above the screen: which addresses belong to the application, and
what state the application is in when it is entered at one of
them.** [consensus across two platforms; a W3C working draft and a
vendor guideline] The W3C manifest is "a centralized place to put
metadata associated with a web application" ([8], Abstract). Its
scope member "tells the browser which documents are part of a web
application, and which are not" ([8], under the heading the fetch
reported as Understanding "scope"), and "A deep link is a URL that
is within scope of an installed web application's processed
manifest" ([8], 5.2 Deep links). Outside the scope the behaviour is
the browser's: "the user agent SHOULD show a prominent UI element
indicating the URL or at least its origin" ([8], 5 Navigation
scope). Android gives the second part under the heading "Deep
linking simulates manual navigation": the back stack made for a
deep link "must be realistic. It should match a back stack that
could have been achieved by organically navigating through the
app", and an existing back stack "is removed and replaced with the
deep-linked back stack" ([1], that section). The state after a deep
link is thus computed from the navigation structure (the start
destination and the start destinations of the enclosing nested
graphs), not written at the destination. Both sources name the one
fact of where the application begins: "a fixed start destination"
[1], "the preferred URL to open when a user launches" ([8],
Abstract). Android's exception belongs to the same level: one-time
setup or login screens "should not be considered start destinations
because users see these screens only in certain cases" ([1], note
under "Fixed start destination"). The three Apple pages read
[3][4][5] say nothing of addresses.

**F3. The persistent frame is described as one thing the pages are
loaded into, with a rule of consistency that is defined over the set
of pages.** [consensus; vendor guidelines, vendor documentation and
a W3C standard] Microsoft: "With few exceptions, any app that has
multiple pages uses a frame. Typically, an app has a main page that
contains the frame and a primary navigation element, such as a
navigation view control" ([2], under "Use the right controls"). The
same section separates two kinds of navigation element: "Unlike
other navigation elements, which should be consistent across the
pages, content-embedded navigation elements are unique from page to
page" ([2], Hyperlinks). The page also carries a table of which
kind of step is added to the navigation history (a step across peer
groups is, a transient UI is not), a rule over the structure of the
app and over no single page ([2], "Guidelines for custom back
navigation behavior"). WCAG 2.2 makes the consistency testable:
"Navigational mechanisms that are repeated on multiple web pages
within a set of web pages occur in the same relative order each
time they are repeated, unless a change is initiated by the user"
([9], success criterion 3.2.3, Level AA), a set of web pages being a
"collection of web pages that share a common purpose and that are
created by the same author, group or organization" ([9], key
terms). A framework builds the frame the same way: "A layout is UI
that is shared between multiple pages. On navigation, layouts
preserve state, remain interactive, and do not rerender" ([10],
under "Creating a layout"; the source sets "shared" in bold). IFML
states it without a link drawn from every screen: a ViewContainer
marked as a landmark "is directly reachable from any ViewElement
from any ViewElement contained, directly or indirectly, in the same
ViewContainer. It represents an implicit link between all the other
ViewElements and the ViewContainer" ([11], attribute isLandmark; the
repetition is the source's). That the criterion of [9] cannot be
judged on one page alone is my reading of its wording; the page does
not say it in those words.

**F4. Several windows and tabs are described by the kinds of window
an application has, by when a new one opens and by what state is
kept or made consistent; for native windows the guidance is the
platform owner's, for browser tabs it was found for signing out
only.** [consensus for native windows, single source for browser
tabs; vendor guidelines] Apple names two kinds: "A primary window
presents the main navigation and content of an app", while an
auxiliary window "presents a specific task or area in an app" and
"doesn’t allow navigation to other app areas" ([4], Discussion). It
asks to "Choose the right moment to open a new window" ([4], Best
practices) and gives a macOS window three states: main, key and
inactive ([4], macOS window states). On state: "your app or game
always needs to be prepared to save and restore their context" ([3],
Best practices), and on iPad "The system remembers window size and
placement even when an app is closed" ([4], iPadOS). Microsoft
names tabs for the case where users "move tabs between windows in
your application" ([2], Tabs). IFML has a Window as "a special kind
of ViewContainer" with two attributes, modal and "opened as a new
window" [11]. The manifest sets the window mode once for the
application: fullscreen, standalone, minimal-ui or browser ([8], 6
Display modes; this part rests on a summarised fetch alone). For
one web application open in several tabs the only guidance read is
on signing out: "ensure that signing out from one tab updates all
other open tabs from that website as well", and "It's best to avoid
relying on your users to close all the relevant tabs and windows.
Instead, take a proactive stance by ensuring that the user's login
state is consistent across tabs" ([7], "Key considerations" and
"Consistent user experience across tabs").

**F5. Notifications and other events that arrive unasked are
described as a list kept for the application: its types, each with
an urgency, behind one permission and one settings screen; a
modelling standard gives the system's own events a construct of
their own.** [single source for each half: a vendor guideline, a
standard] Apple: "You need to get permission before sending any
notification" ([5], Discussion); "you first identify the types of
notifications your app or game can send", and "You need to specify
a system-defined interruption level for each noncommunication
notification you send" ([5], Integrating with Focus), the levels
being Passive, Active, Time Sensitive and Critical; "you must also
provide an in-app settings screen that lets people change their
choice" ([5], Sending marketing notifications). Whether to send at
all is also said for the app: "Use notifications sparingly" ([3],
Best practices). IFML: "A SystemEvent is an Event produced by the
system, which triggers a computation reflected in the user
interface", its examples being time events and "system special
conditions events, such as a database connection loss event" ([11],
class SystemEvent). Where a tap on a notification lands is not said
in [5]; that it is a deep link and falls under F2 is my inference.
Android's and the web's own pages on notifications were not opened.

**F6. Offline and degraded states are described as an announcement
the application makes about itself and about the user's data, with
a statement of which parts work offline.** [single source, dated
2016; vendor guideline] "When a web app first loads, it must
indicate to the user whether it's ready for offline use" ([6], under
"Inform the user when the app offline", the heading's wording being
the source's); "Clearly inform the user when a change in state
occurs as soon as possible" ([6], Inform users of state); "Tell the
user what state their data is in. For example, you can show whether
the app has synced" ([6], Make experiences transferable from one
device to another); a further heading asks to "Clarify what is
available offline" (the heading as the summarising fetch reported
it). The page is dated November 10, 2016 and its footer gives the
same day as its last update: the guidance is ten years old and no
younger guidance of a platform owner was read. IFML's example of a
system event, "a database connection loss event" [11], places the
loss of a connection among the unasked events of F5. The split into
one rule for the application (how the state is announced and in
which words) and one property of each part (available offline or
not) is my reading of the headings of [6].

**F7. A view that differs by role is described, in the one standard
read, not on the screen but as a context and a named part of the
model granted to it; the same mechanism carries the device and the
position.** [single source; standard] IFML: "The Context is a
runtime aspect of the system that determines how the user interface
should be configured" ([11], class Context); "ContextDimension has
the specializations UserRole, Device, and Position" ([11], class
ContextDimension); "The purpose of a Viewpoint is to facilitate the
comprehension of a complex system, to allow or disallow access to
the system by a specific UserRole, or to adapt the system to a
specific context change" ([11], class Viewpoint); "When the user
context has the same user role as the one specified by the UserRole,
the ContextDimension is satisfied and access is granted to the
ViewPoint elements" ([11], class UserRole). The role is thus
declared once, with the set of elements it opens; a Device is
defined in the same form, for "desktop, laptop, smart phone, tablet"
([11], class Device). How practice writes it down (a matrix of
roles against views and actions) appeared only in search results
from vendors' blogs, none of them opened; it is no finding here.

**F8. Where the sources say anything about the place, it is once,
with the lower level referring to it, and the platforms' own
artefacts are built that way.** [consensus among the sources read,
each from its own field: a template's documentation, a practitioner
claim, a standard, vendor documentation; no study] arc42, a template
for architecture documentation, has a section for what belongs to no
single part: "This section describes crosscutting concepts
(practices, patterns, regulations or solution ideas). Such concepts
are often related to multiple building blocks", and "This is the
place in the template that we provided for a cohesive specification
of such concepts"; its reason: "Concepts form the basis for
conceptual integrity (consistency, homogeneity) of the architecture"
([12], Content and Motivation). It is a template for architecture,
not for an interface; carrying it over is my analogy. A
practitioner's method for UX specifications says: "The cascade
refers to a hierarchical set of guidelines, standards, and
specifications that define what a product is and how to build it",
"Define each of these things only once", and "Instead of defining
how lists look and behave in each and every specification that uses
the list style, we refer to a standard, because all lists in the
entire app work the same way"; the gain it names is that "you can
quickly change standards without encountering issues of conflicting
standards or requirements" ([13], under the heading the fetch
reported as "The Cascade"). That article is about styles and
components more than about the behaviour of this card, and by the
summarised fetch it gives no rule for a lower level that departs
from a higher one. The platforms' own artefacts hold the same things
once: the manifest [8], the root layout that [10] calls required,
the navigation graph from which the back stack of a deep link is
derived [1], the context and the viewpoints of an IFML model [11].

**F9. The sources have three levels, not two: the application, a
section of it, the screen.** [consensus across vendor documentation,
vendor guidelines and a standard; the synthesis is mine] "By
default, layouts in the folder hierarchy are also nested" ([10],
Nesting layouts): a layout stands for a segment of the addresses
and for everything beneath it. Android's back stack for a deep link
"will also contain the start destinations of any nested graphs that
are ancestors of the deep link destination" ([1], last section).
IFML's ViewContainer "aggregates other ViewContainers", and its
landmark holds within "the same ViewContainer" [11]. Microsoft: "we
recommend that peer-to-peer navigation elements only link to the
peers within their current subtree" ([2], Combining structures). In
each of them a rule stands at the node of the tree where it holds
and reaches what lies beneath.

## Unexpected

The card assumes two places, once for the application or again on
every screen; [1], [2], [10] and [11] have three (F9). A frame that
holds for one area only, such as a checkout without the main
navigation, has its place at the section, and neither of the card's
two answers gives it one. The card is answered above as put; the
choice it poses is wider than it says.

Much of this behaviour is not the application's to describe, since
the platform decides it. "Apps don’t control multitasking
configurations or receive any indication of the ones that people
choose" ([3], note under iPadOS); "Avoid creating custom window UI"
([4], Best practices); outside its scope a web application falls
back to the browser, which "will apply its own defaults" ([8],
Understanding "scope"); Android's principles are to hold "Even if
you aren't using the Navigation component in your project" ([1],
opening note). A description may owe, per target, a line saying
which conventions of the platform it takes as they are, and write
only where it departs. A lead for the card on the platforms.

In IFML the role, the device and the position are one mechanism
[11]. The card treats the view that differs by role as a matter of
its own; the standard files it with the difference between a phone
and a desktop. A description for four targets and several roles
could have one notion of context where two were expected. One
standard says so; how far practice follows it was not looked at.

The platform owners serve their guidelines as Markdown. The Apple
pages [3][4][5] were read at an address ending in `.md`, which
returned Markdown under a small metadata header, and [10] names an
index of its documentation at `/docs/llms.txt`. A description could
cite a platform's rule by an address an agent can read. A lead for
the cards on descriptions written for an agent and on what a
description cites.

WCAG already has a normative unit above the page, the "set of web
pages", and a requirement that holds only across it [9]. A lead for
the card on accessibility: part of what it asks for cannot be
written on a screen either.

## Not found

- A template or a standard of interface specification with a named
  section for the behaviour of the whole application. Looked for
  with two queries (specification templates with a section of
  global rules; wireframe annotations with global notes); the
  results were per-screen templates and tutorials of tool vendors,
  none opened. No standard of requirements specification was
  opened, so whether one names such a section is not established
  here.
- Anyone arguing that a per-screen specification is enough or that
  the rules of the whole application need no place: the
  disconfirming query in two wordings returned nothing of the kind.
- A platform guideline on a view that differs by role or permission.
  The one candidate, SAP's Fiori guideline on navigation, refused
  the request with HTTP 403 [14]; nothing else on it was opened. The
  practice of a permission matrix was seen in search results from
  vendors' blogs only.
- Apple's guidance on addresses and deep links: nothing on the three
  pages read, and a search across its Human Interface Guidelines
  returned none; Apple's developer documentation on links into an
  app was not opened.
- Guidance on one web application open in several tabs beyond
  signing out (stale data, one record edited in two tabs): the
  search returned blogs and forum threads only, none opened.
- Guidance of a platform owner on offline behaviour younger than
  2016. Not opened for want of budget, and therefore not judged:
  Android's page on offline-first apps, the Material Design pages
  on navigation, notifications and offline states, the service
  worker specification, WCAG's criterion on status messages and the
  web's notification and push standards.
- A rule for departures: how a screen states that it departs from a
  rule of the application. No source read gives one for a
  description; [13] does not.
- Measured evidence, a study or an audit, that keeping these rules
  once lowers defects or serves a builder, human or agent, better
  than repeating them. Every source here is a guideline, a standard,
  a template or one practitioner's account.
- The text of the IFML specification itself: its PDF came back as
  bytes the fetch could not read. The documentation strings of the
  metamodel file were read in its place [11]; the notation, the
  diagrams and the examples of the specification were not seen.

## Options

1. **One part for the whole application, flat.** All rules of the
   application stand in one document or one section and the screens
   cite it. For it: the simplest shape, one place to change, what
   [12] and [13] do. Against it: no home for a rule that holds for a
   section only (F9), and a builder handed one screen must be handed
   that part with it.
2. **Three levels with inheritance.** Application, section, screen;
   a rule stands at the highest level where it holds, and a screen
   carries its own properties and its stated departures. For it:
   the shape of every structural source [1][2][10][11]. Against it:
   it needs a rule for departures that no source supplies, and it is
   more structure than a project of one person may want.
3. **Typed parts at the level of the application.** A table of the
   addresses with the start; the frame; the kinds of window; a
   catalogue of unasked events, each with urgency and permission;
   the rules for offline; the contexts (roles, devices), each with
   what it opens. For it: each part can be checked and maps onto an
   artefact of the build (a manifest, routes, a layout, notification
   types), following the constructs of [5], [8] and [11]. Against
   it: the heaviest option, and uneven in evidence, since role and
   offline rest on one source each.
4. **Again on every screen.** For it: the description of a screen is
   whole by itself. Against it: nothing read recommends it, [13]
   names its cost (copies that come to conflict), and a rule such as
   that of [9] cannot be stated on one screen at all.
5. **By reference to the platform.** The description takes the
   platform's conventions by citation and writes only its
   departures; it combines with options 1 to 3. For it: short, and
   true to how much the platform decides. Against it: four targets
   are four sets of conventions, and the description must say which
   it takes for each.

In every option but the fourth something stays on the screen: its
address and parameters, whether it can be entered directly, which
frame it stands in, whether it works offline, which contexts see
it, which unasked events it shows. This list is my inference from
F2, F3, F6 and F7.

## Relevance to this project

The recommendation: give the description a place above the screens
and let that place have levels (option 2), adding the typed parts of
option 3 only as a project needs them; a screen says what is its own
and cites upward. It rests on F1 to F7, where the platform owners
and three standards place each behaviour above the screen, on F8,
where the sources that speak of the place say once, and on F9, the
middle level. It is chosen against option 4, which no source
supports, and against the flat single part, because every
structural source read has the middle level.

What is mine and not the sources': the carrying of guidelines and
standards over onto the parts of a document, the list of typed
parts, and the list of what stays on a screen. No source read
prescribes the layout of a textual description of an interface.

On the idea under test, the element definitions and a page that
names its elements: the evidence of this card does not speak against
it and shows it incomplete. The frame is, by [11], an implicit link
from everything and, by [2] and [10], the thing pages are loaded
into; a page that lists its elements would either repeat the frame
on every page or leave it nowhere. A third kind of definition above
the page is needed, whatever it is called.

Weak points to keep in view: role and offline rest on a single
source each, the guidance on offline is from 2016, and nothing here
is measured.

Consult when: the shape of the description is decided (what is a
document, what a section, what a property of a screen); a screen's
definition is drafted and the question is what it must carry and
what it cites; the idea of elements and pages is judged; a target is
added (windows on the desktop, deep links on mobile, an installed
web application); roles, notifications or offline use enter a
project.

## Sources

1. "Principles of navigation", Android Developers (Google). Undated
   in the text read.
   https://developer.android.com/guide/navigation/principles
   Kind: primary (platform owner's guideline). Read in full: the
   fetch returned the page's text as it stands. Original.
2. "Navigation basics for Windows apps", Microsoft Learn. Dated
   2025-04-03, updated 2026-06-27 (structured data in the page's
   metadata).
   https://learn.microsoft.com/en-us/windows/apps/design/basics/navigation-basics
   Kind: primary (platform owner's guideline). Read in full.
   Original.
3. "Multitasking", Human Interface Guidelines, Apple. Last entry of
   the page's change log: June 9, 2025.
   https://developer.apple.com/design/human-interface-guidelines/multitasking.md
   Kind: primary (platform owner's guideline). Read in full, in the
   Markdown form served at that address. Original.
4. "Windows", Human Interface Guidelines, Apple. Last entry of the
   page's change log: June 9, 2025.
   https://developer.apple.com/design/human-interface-guidelines/windows.md
   Kind: primary (platform owner's guideline). Read in full, in the
   Markdown form. Original.
5. "Managing notifications", Human Interface Guidelines, Apple.
   Undated: the page has no change log.
   https://developer.apple.com/design/human-interface-guidelines/managing-notifications.md
   Kind: primary (platform owner's guideline). Read in full, in the
   Markdown form. Original.
6. "Offline UX design guidelines", Mustafa Kurtuldu and Thomas
   Steiner, web.dev (Google). Published November 10, 2016 (byline);
   last updated 2016-11-10 (page footer).
   https://web.dev/articles/offline-ux-design-guidelines
   Kind: primary (guidance of the owner of a browser platform).
   Summarised fetch; the sentences quoted were then checked word for
   word against the page's raw text, the headings were not. Original.
7. "What makes for a good sign-out experience?", Kenji Baheux,
   web.dev (Google). Last updated 2023-12-04 (page footer); no date
   of publication seen.
   https://web.dev/articles/sign-out-best-practices
   Kind: primary (guidance of the owner of a browser platform).
   Summarised fetch; the sentences quoted were then checked word for
   word against the page's raw text, the author and the headings
   were not. Original.
8. "Web Application Manifest", W3C Web Applications Working Group.
   W3C Working Draft, 18 November 2026 (the page's title block).
   https://www.w3.org/TR/appmanifest/
   Kind: primary (standard in draft). Read partially: a summarised
   fetch of the first 200,000 of 258,007 characters (the abstract,
   the members, 5 Navigation scope, 5.2 Deep links, 6 Display
   modes); the rest not read. The sentences quoted were then checked
   word for word against the page's raw text; the section numbers
   are as the fetch reported them. Original.
9. "Understanding SC 3.2.3 Consistent Navigation (Level AA)", WCAG
   2.2 Understanding Docs, W3C Web Accessibility Initiative.
   Updated 28 June 2026 (on the page).
   https://www.w3.org/WAI/WCAG22/Understanding/consistent-navigation.html
   Kind: primary (the standard body's own explanation, carrying the
   text of the criterion and of the defined term). Summarised fetch;
   the sentences quoted were then checked word for word against the
   page's raw text. Original.
10. "Layouts and Pages", Next.js documentation, Vercel. Last updated
    2026-08-25 (structured data in the page's header).
    https://nextjs.org/docs/app/getting-started/layouts-and-pages
    Kind: primary (a vendor's documentation of its own product).
    Read in full. Original.
11. The metamodel file of the Interaction Flow Modeling Language
    (IFML), Object Management Group. Dated by the path of its
    address, 20140301; no date read inside the file.
    https://www.omg.org/spec/IFML/20140301/IFML-Metamodel.xmi
    Kind: primary (the machine-readable metamodel of a standard,
    with the documentation string of each class). Read partially: a
    summarised fetch of the first 200,000 of 224,938 characters;
    then the documentation strings of the classes ViewContainer,
    SystemEvent, Context, ContextDimension, Viewpoint, UserRole,
    Device, Position, Window and Menu were read word for word from
    the raw file. Original.
12. "Section 8: Cross-cutting Concepts", arc42 documentation,
    arc42. Undated: no version or date of the section on the page.
    https://docs.arc42.org/section-8/
    Kind: primary (the template's own documentation). Summarised
    fetch; the sentences quoted were then checked word for word
    against the page's raw text. The diagram of topics is an image
    and was not read. Original.
13. "Cascading UX Specifications", Steven Hoober, UXmatters, column
    Mobile Matters. January 8, 2018 (byline).
    https://www.uxmatters.com/mt/archives/2018/01/cascading-ux-specifications.php
    Kind: primary for the author's own practice, a practitioner
    claim; no evidence beyond his account. Summarised fetch; the
    sentences quoted were then checked word for word against the
    page's raw text. Original.
14. "Navigation", SAP Fiori design guidelines for the web, SAP.
    https://www.sap.com/design-system/fiori-design-web/v1-139/foundations/best-practices/global-patterns/navigation/navigation
    Not opened: the server answered HTTP 403. Cited for no content.

## Opened and not used

- "Interaction Flow Modeling Language", specification as PDF, Object
  Management Group,
  https://www.omg.org/spec/IFML/1.0/PDF
  The fetch returned the bytes of a PDF whose text it could not
  read, only the titles of its bookmarks; superseded by [11].

## Search record

Queries, in order:

1. application-level UI behaviour specification: global navigation,
   deep links, notifications, offline states
2. Android principles of navigation: fixed start destination, deep
   linking
3. IFML: view container, landmark, system event, context,
   viewpoint, user role
4. UI specification template with a section of global rules,
   "applies to all screens"
5. arc42 section 8, cross-cutting concepts, user interface
6. the disconfirming query: "per-screen specification is enough" OR
   "global UI rules section unnecessary" OR "screen-by-screen spec
   is sufficient"
7. Apple Human Interface Guidelines: multitasking, windows, state
   restoration, notifications, deep link
8. web.dev offline UX design guidelines, app shell model
9. W3C Web Application Manifest: navigation scope, deep link,
   start_url, display mode
10. OMG IFML 1.0 specification: ViewContainer, SystemEvent, Context,
    ViewPoint, UserRole
11. role-based UI specification, permission matrix, which role sees
    which element
12. Microsoft Learn: Windows app navigation basics, multiple windows
13. the address of the IFML metamodel file at OMG
14. wireframe annotations: global notes on behaviour across screens,
    written once
15. Next.js layout file convention: shared between pages, state
    preserved
16. the disconfirming query reworded: screens alone as a sufficient
    specification, arguments against a separate section for the
    behaviour of the whole application
17. one web application open in several browser tabs: consistency of
    state, signing out

Pages opened, in order: [1]; [8], its first 100,000 characters; [3];
[6]; [5]; [4]; [9]; [12]; the IFML specification as PDF (unreadable);
[2]; [13]; [14] (refused, HTTP 403); [11], its first 100,000
characters; [10]; [7]. That is fifteen pages requested, thirteen
read and two failed. Two further fetches read on in pages already
opened ([11] and [8], characters 100,000 to 200,000 of each).
Beyond the budget of openings, seven of the pages already opened
([6], [7], [8], [9], [11], [12], [13]) were requested once or twice
more as raw text, filtered to the sentences quoted, to check the
quotations word for word; no new page was opened that way.

The disconfirming query: both wordings (6 and 16) found no page
that argues a per-screen specification is enough or that the rules
of the whole application need no place. The results were tutorials
on per-screen specifications and product documentation, none
opened. This is what the card expected.

Why the run ended: the opening budget. Fifteen pages were requested
and the run stopped there. Of the card's stop rule the first half
was met, the last differently worded queries (14, 16, 17) bringing
no new kind of source; the second half was not met in full, since
the route of role and permission has a primary source in a standard
[11] and none in a platform guideline, and the pages named under
Not found as not opened stayed unopened.
