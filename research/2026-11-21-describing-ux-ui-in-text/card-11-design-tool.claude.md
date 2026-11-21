---
date: 2026-11-21
project: forge
topic: how a text or code source and a design tool are connected, in which direction, and what a text-first description must keep
status: immutable
engine: claude
model: claude-fable-5-2
usage: —
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-11-design-tool
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 11; no known note named by the card; web sources below
---

# A text or code source and a design tool are connected by one-way transfers that hang on identifiers, names and tokens

<!-- Shape: templates/research.md -->

## In short

At the design tool taken here as the dominant one (Figma; the card
names none and no source opened measures dominance) all four
connections the card lists exist as documented interfaces; at the open
alternative (Penpot) three do, and a component-to-code link was not
found. None is a synchronisation: each is a one-way transfer that
someone starts. Reading is the settled direction: a design comes out
as structured data (JSON over REST, an XML outline, generated code and
variables through the vendor's agent server; an archive of JSON files
at Penpot). Writing has no document format at either tool: a design is
written by an agent running scripts against the tool's plugin
interface (at Figma in beta, "beta quality" in the vendor's words), or
by capturing a rendered web interface as flat layers that, by the
vendor's own statement, have no connection to the libraries.
Components are linked to code by mapping files kept in the code
repository and published into the tool. Tokens are the one thing with
a neutral exchange format (Design Tokens Format Module 2025.10, a
community report, not a W3C standard) and with push and pull both
ways. Every connection hangs on a tool-assigned identifier, on names
(of components, of their properties and listed values, of tokens) or
on a typed token; that is what a text-first description must keep or
leave room for. Sureness: high on which interfaces exist and which way
they run (the vendors' own documentation, read on 2026-11-21), low on
how well the writing direction works (one vendor caveat, one user
report). The disconfirming query's expectation held in a weaker form:
both directions exist, no source shows a round trip, and the two
search phrases themselves returned opinion and vendors' pages only,
none used. Unexpected: the writing connection is an agent with an
instruction file, not an import format. All pages were read through a
summarising fetch; the quoted phrases were then matched in the page
text.

## Question

The frame, in brief (the packet holds it in full): a framework carries
an idea down a chain of versioned Markdown documents kept in git,
each worked by a human with an AI agent; nothing is implemented there.
Its author wants the same for the user interface: an agent proposes a
description of the interface in text, a human tunes it and sees it,
and it goes with the other documents to a build stage. Authors are one
person working end to end and a UX/UI specialist in a company; targets
are the web, the mobile web, native mobile and the desktop. One idea
is to be tested: every element of a screen has a small Markdown
definition of its own, and a page definition names which elements it
holds and where they stand. In this note "design" means the design of
the interface held in a design tool; where the visual identity of a
design system is meant the note says "tokens" or "library"; the
technical design of spec-driven kits is meant nowhere.

The card, verbatim:

> #### Card 11: Text and the design tool
> - **Question:** How are a textual or code source and a design tool
>   connected today (reading a design as structured data, writing a
>   design from structured text, linking components to code, keeping
>   tokens and variables in step), for the dominant design tool and
>   for open alternatives: in which direction does each connection
>   run, and what must a text-first description keep (identifiers, a
>   vocabulary of components, tokens) so that such a connection can be
>   added later?
> - **Why it matters:** a specialist will need the design tool, and
>   the first step must not close that path.
> - **What would answer it:** the vendors' documentation of their own
>   interfaces.
> - **Where to look:** the design tools' programming interfaces,
>   developer modes, component-to-code links and agent servers; token
>   tools; the open design tool's format and interface. Search words
>   from card 1: "handoff" names the passage and a tool's features for
>   it, not the document; for the document "design specs",
>   "annotations", "ready for dev"; vendors' pages on their own market
>   are to be expected and are left out by the brief. Primary
>   artefacts in public repositories (schemas, component and page
>   files, agents' rules and prompt files, the schemas of servers for
>   design tools, issue trackers) before commentary about them.
> - **Disconfirming query:** "design to code round trip problems",
>   "design tool or code as source of truth"; expected: the connection
>   runs well in one direction only.
> - **Stop rule:** nothing new from a differently worded query and
>   every route has a primary source; ten to fifteen pages opened.

What the note must beat: the answer anyone gives unasked, that the
dominant tool has a programming interface, a developer mode and a
component-to-code link, that the open tool has an open format and
that tokens have a W3C format, so a connection "can always be added
later". The note has to say, route by route and from the vendors' own
documentation, which way each runs, what gates it and which identifier
or name it hangs on, because only that tells what the text must keep.

## Key findings

How the pages were read: the fetch tool of this run returns a page
through a summarising model, so every finding below rests on a
summarised fetch of a primary page; what stands in quotation marks was
then matched as a string in the page's own text by a second, direct
fetch of the same address. The vendors' documentation pages carry no
date; they are taken as current on the day read, 2026-11-21, and every
plan, seat, limit and beta statement below carries that date.

**F1. A Figma design can be read as structured data over a documented
REST interface, and that interface does not write layers.** [single
source; vendor documentation of its own interface] `GET /v1/files/:key`
returns a JSON object with the `document` node tree and the maps
`components`, `componentSets` and `styles`; "The `components` key
contains a mapping from node IDs to component metadata" (the section
on the response of GET file) [1]. Parameters narrow the read (`ids`,
`depth`, `geometry`, `plugin_data`). The page lists six endpoints:
five reads and `POST /v1/files/:file_key/duplicate`, which "Duplicates
a main file or branch into a folder as a new standalone file"; none
creates or changes a node [1]. Direction: tool to text only. Gate: the
scope `file_content:read`.

**F2. The vendor's agent server reads the same design for an agent,
as an outline, as generated code and as variables.** [single source;
vendor documentation] `get_metadata` "Returns a lightweight XML
outline of your selection"; `get_design_context` "Gets the design
context for a layer or selection in Figma. By default, the output is
React and Tailwind, but you can ask for a different framework in your
prompt"; `get_variable_defs` "Returns the variables and styles used in
your selection"; `search_design_system` "Searches all connected
libraries for components, variables, and styles" that match a text
query; `get_code_connect_map` "Returns the Code Connect mappings for
the instances in your selection" (each under its tool's heading) [2].
The reading tools are limited in rate by plan and seat, a handful of
calls a month on the free plan and on viewing seats (README, rate
limits; summarised fetch, the figure not matched) [5]. Direction: tool
to agent.

**F3. Writing a design into Figma has no document format: it is an
agent running JavaScript through the plugin interface, on the remote
server only, in beta.** [single source for the mechanism, vendor
documentation; the quality statement is a vendor claim against its own
interest] `use_figma` is "The general-purpose tool for writing to
Figma files", by which an agent can "create, edit, delete, or inspect
content", in a design file "Pages, frames, components, variants,
variables, styles, text, images, and more" [2]. It lets the agent "run
code in your Figma file through the Figma Plugin API" [3]; the
vendor's skill file for agents opens with "Use the `use_figma` tool to
execute JavaScript in Figma files via the Plugin API" and orders that
a script "MUST `return` ALL created/mutated node IDs" (rule 15), later
calls reaching the nodes by those IDs alone (summarised fetch) [4].
"Writing to the canvas is currently in beta and free to use during the
beta period" and is to become a "usage-based paid feature"; among the
limits listed: "Output is beta quality and may need manual review and
cleanup" (Current limitations) [3]. The README of the vendor's public
guide repository marks the feature "remote server only" [5]. The REST
interface has no counterpart (F1). Direction: agent to tool; what the
agent reads as its input is left open by every page.

**F4. The other writing route, the capture of a rendered interface,
yields layers without components, by the vendor's own statement.**
[single source confirmed by one practitioner report; vendor
documentation and a user's report on the vendor's forum]
`generate_figma_design` "Sends the live UI of your web apps and sites
to Figma as design layers" and is "Available with select MCP clients";
`html_to_figma` "Converts an HTML document into design layers in a
Figma Design file"; `send_code_to_figma` brings a project in as a code
layer and "doesn't create design layers" [2]. The vendor: "Sending UI
to Figma captures a running app as flat layers, without a connection
to your libraries. Writing to the canvas builds with your existing
components and variables" (introduction) [3]. A feature request on the
vendor's forum, 2026-02-25, reports the same from use: the capture
gives "frames, rectangles, and text nodes" with "no component
instances, no variable bindings, no variant properties", and asks that
an element mapped through Code Connect "Instantiate the actual Figma
component rather than rendering raw geometry"; the one reply,
2026-04-01, from another forum member not marked as staff, points to
`use_figma` and `search_design_system` instead [6]. The capture is
described for web apps and sites [2].

**F5. Components are linked to code by mapping files that live in the
code repository and are published into the tool; a link is edited
where it was made.** [single source; vendor documentation] "Code
Connect is a bridge between your codebase and Figma's Dev Mode",
joining components in repositories to components in design files;
"Once published, your components will be available in Figma's Dev
Mode", and the mappings are served to agents as well (F2) [7]. A
template file (`.figma.ts`) is "a framework-agnostic way to connect
your code to Figma components": it opens with a comment line `// url=`
holding the link of the Figma component, which carries a `node-id`;
it reads the component's properties by name (`getString`,
`getBoolean`, `getEnum` with a table from each Figma value to a code
value, `findInstance` by layer name, `getSlot`); it is sent with `npx
figma connect publish` [8]. "CLI-created connections will appear in
the UI, but can only be edited in the CLI" [7]. Gate: "Available on a
Dev or Full seat on the Professional, Organization, and Enterprise
plans" [7]. The frameworks named span web and native: React and React
Native, HTML for Web Components, Angular and Vue, SwiftUI, Jetpack
Compose (summarised fetch) [7]. The agent server adds
`add_code_connect_map`, which "Maps a Figma component to its code
component in your codebase" [2]. Direction: repository to tool for
the mapping, tool to agent for its use; neither page says a mapping
changes the design or the code.

**F6. Any node can carry links to addresses, written and read over
REST.** [single source; vendor documentation] "Dev Resources endpoints
allow you to create, read, update, and delete dev resources in Figma
files"; the errors named are "The node already has the maximum of 10
dev resources" and "Another dev resource for the node has the same
url"; the scopes are `file_dev_resources:read` and
`file_dev_resources:write` [9]. Direction: both, by whoever calls. The
page does not describe the fields of a dev resource; it points to a
types page that was not opened.

**F7. Figma variables can be read and written in bulk over REST, on
the highest plan only.** [single source; vendor documentation] Three
endpoints: GET local variables, GET published variables and `POST
/v1/files/:file_key/variables`, which "lets you bulk create, update,
and delete variables and variable collections", all changes of a
request standing or failing together [10]. "This API is available to
full members of Enterprise orgs" [10]. Limits stated: at most 5000
variables in a collection (and forty modes, summarised fetch);
"Variable names must be unique within a collection and cannot contain
certain special characters such as .{}" (POST variables) [10]. Below
that plan the routes to variables found in this run are the agent
server, reading by `get_variable_defs` and writing through `use_figma`
[2], and a plugin (F9).

**F8. Tokens have a neutral exchange format with a first stable
version, a community report and not a standard.** [consensus of its
community group; specification] Design Tokens Format Module 2025.10 is
a "Final Community Group Report" of 28 October 2025: "It is not a W3C
Standard nor is it on the W3C Standards Track" (Status of This
Document) [11]. A token is "information associated with a human
readable name, at minimum a name/value pair" (3.1); "token and group
names MUST NOT begin with the $ character", and of `{`, `}` and `.`:
"the following characters MUST NOT be used anywhere in a token or
group name" (5.1.1); a reference is written `{group.token}` or as a
JSON Pointer in `$ref` (7.1); `$extensions` carries a tool's own data
under a key in "reverse domain name notation", which other tools are
to preserve (5.2.3); a file is `.tokens` or `.tokens.json`, its media
type `application/design-tokens+json` (4) [11]. Types: color,
dimension, fontFamily, fontWeight, duration, cubicBezier, number, and
the composites stroke style, border, transition, shadow, gradient and
typography (8 and 9) [11].

**F9. A token plugin keeps the design tool's tokens and a git
repository in step by explicit push and pull of JSON files.** [single
source; "two-way sync" is the vendor's own word] "We support two-way
sync, meaning you can use the plugin to:" push JSON files of tokens to
GitHub and "Pull the Tokens stored in GitHub into any Figma file"
[12]. Storage is one file or a folder of files, the folder a paid
feature ("multi-file sync) is a pro feature"); the page describes a
comparison and a prompt to push or to pull, and no resolution of edits
made on both sides; one known issue is listed: "Occasionally you have
to push/pull to GitHub several times for the indicator to clear" [12].

**F10. Penpot's native file is an archive of JSON readable without the
tool; its schema is the tool's source code.** [single source; vendor
documentation] The `.penpot` export is "a ZIP archive containing JSON
metadata and binary assets"; version 3 is the current one, version 1 a
binary format now deprecated, version 2 SQLite-based and never
released (Version History) [14]. The archive holds a `manifest.json`
and, per design file, JSON files for pages and their shapes, for
components, colours and typographies, and one `tokens.json`; objects
are identified by UUIDs [14]. No standalone schema is published: "The
authoritative schema definitions are in the Penpot source code" [14].
Direction established: tool to text; whether an archive written
outside the tool is accepted on import was not checked.

**F11. Penpot's agent server reads and writes through a plugin in the
open file, by running code, on the page in focus.** [single source;
vendor documentation] "your agent can read and modify your Penpot file
structure (components, styles, tokens, pages, layers, etc.)"; the link
is "a plugin that runs inside Penpot and connects your open file to
the MCP server"; the tools of the local server are `execute_code`,
`high_level_overview`, `penpot_api_info`, `export_shape` and
`import_image`; "MCP always operates on the page you have in focus in
Penpot", in one browser tab at a time; a hosted and a local variant
exist [13]. Direction: both, each by code the agent writes.

**F12. Penpot's tokens follow the community format and travel as
JSON, in and out.** [single source; vendor documentation] "Penpot
Design Tokens adhere to the Design Tokens Format Module and its
definitions, a draft by the W3C DTCG"; at a dot in a token's name "it
breaks down the name and structures it as nested groups"; references
stand in braces; sets are ordered and themes combine them; export and
import run as one JSON file or as several; "Tokens can be exported
from Penpot or integrated into other tools directly, without
conversion" [15]. The page calls the format a draft, while [11] is a
final report of 28 October 2025: which version Penpot reads and writes
was not established. The types listed go beyond the format's own
(border radius, opacity, rotation, sizing, spacing, stroke width;
summarised fetch) [15].

**F13. Every connection found hangs on the tool's own identifier, on
names or on a typed token; none hangs on the wording of a
description.** [the agent's synthesis of F1 to F12; each row a fact
from the source named]

| Connection | Interface | Direction | Gate, as read 2026-11-21 | What it hangs on |
|---|---|---|---|---|
| Read a design | Figma REST files [1] | tool to text | scope `file_content:read` | file key, node ID |
| Read a design | Figma agent server [2] | tool to agent | rate limits by plan and seat [5] | selection or node ID; names in the library |
| Read a design | Penpot archive [14] | tool to text | none stated | UUID |
| Write a design | Figma `use_figma` [2][3][4] | agent to tool | remote server, beta, edit access | node IDs the script returns; names of library components and variables |
| Write a design | Figma capture [2][3] | rendered web interface to tool | select clients | nothing: flat layers |
| Read and write | Penpot agent server [13] | both, by code | plugin in the open file, page in focus | not stated on the page |
| Link a component to code | Code Connect [7][8] | repository to tool | Dev or Full seat on a paid plan | component link with node ID; property names and listed values |
| Link a node to an address | dev resources [9] | both | write scope | node ID; address, unique per node |
| Tokens | Figma variables REST [10] | both | Enterprise | variable and collection; names without `.{}` |
| Tokens | plugin and git [12] | both, push or pull | folder storage paid | token names in JSON files |
| Tokens | Penpot import and export [15] | both | none stated | token names, a dot read as a group |
| Tokens | format 2025.10 [11] | a neutral file | none | names without `{`, `}`, `.` and a leading `$`; `$type`; `$extensions` |

**F14. The disconfirming query: both directions exist, no source
shows a round trip, and the capture direction loses structure by the
vendor's own account.** [contested in the field; here vendor
documentation and one practitioner report, the opinion pieces the
query returned not used] The expectation was that the connection runs
well in one direction only. Against it: writing into the tool is now
a documented interface at both tools (F3, F11), and tokens move both
ways (F7, F9, F12). For it: reading is offered as data without a
caveat (F1, F2, F10), while writing is in beta, "may need manual
review and cleanup" [3], and its capture form gives "flat layers,
without a connection to your libraries" [3][6]; no page opened
describes a design written from text, edited in the tool and read
back into the same text, or any reconciliation of edits made on both
sides, for layouts or for tokens (F9). The two search phrases
themselves returned an encyclopaedia entry on round-trip engineering
of models, vendors' pages on their own market and opinion pieces;
none was opened.

## Unexpected

The card assumes that "writing a design from structured text" is an
interface between two formats. [2], [3], [4] and [13] say it is not:
at both tools a design is written by an agent that runs code against
the plugin interface, with a skill file as its instruction, and
neither vendor documents a file a layout could be written in and
imported. The question is answered as put; the lead is that a
text-first description need not anticipate a tool's file format, only
be readable by an agent and carry names the agent can look up in a
library ([2], `search_design_system`). This is the agent's inference.

The dominant tool's own bridge to code is partly a text file for an
agent. The server's prompt `create_design_system_rules` "Creates a
rules file that gives your agent the context it needs to turn designs
into code that fits your codebase, design system, and tech stack" [2],
and the README advises project guidance "in whatever format your MCP
client uses for instruction files", adding of the component mapping:
"Without it, the model is guessing" [5]. It touches the cards on
descriptions written for an agent that builds and on the agent that
proposes.

The tool begins to hold code beside the design instead of converting
one into the other: `send_code_to_figma` puts a project into a design
file as a code layer and "doesn't create design layers" [2]. A lead
only; nothing more was read on it.

Penpot's page calls the token format a draft a year after its final
report ([15] against [11]): a lag of the page or of the
implementation, not established.

## Not found

- No source describing a round trip of a layout without loss, or an
  automatic two-way synchronisation between a text or code source and
  a design tool: looked for in [1] to [5], [7] to [10] and [13] and
  with both disconfirming phrases.
- No measured figure on the quality of the writing direction: only the
  vendor's "beta quality" [3] and one user's report [6].
- No Penpot counterpart of the component-to-code link: not in [13],
  [14], [15] or in the result lists.
- No published schema of the `.penpot` archive apart from the source
  code [14]. For Figma's REST interface a result list showed a
  published OpenAPI specification; it was not opened.
- No statement on how edits made on both sides are reconciled in the
  token push and pull [12].
- No capture route for a native mobile or a desktop interface: [2]
  names web apps and sites; the component link alone names native
  frameworks [7].
- No source for "the dominant design tool": Figma was taken as such on
  the agent's own reading of the card.
- Not opened, so nothing is said on them: the developer mode's own
  pages (annotations, the "ready for dev" status; they lie in the
  vendor's help centre), the plugin interface references of both
  tools, the types page of dev resources, the build-side token tools
  (Style Dictionary), the resolver module of the token format, design
  tools other than these two.
- No date on any vendor documentation page; none is used for a claim
  about when something was introduced.

## Options

- **O1. A tool-neutral description with a binding kept apart.** The
  description keeps its own identifiers, a vocabulary of components
  and token names; a binding, added on the day a tool is attached,
  maps each identifier to the tool's (a component link with its node
  ID, a UUID). For: no plan, seat or vendor is presupposed, either
  tool can be attached, and the description does not change when a
  design file is rebuilt. Against: the binding is one more thing to
  keep true, and nothing found keeps it true by itself.
- **O2. Tokens as the first shared surface.** Tokens kept as files in
  the 2025.10 format beside the documents and cited from descriptions
  by name. For: the one route with a neutral format and both
  directions at both tools (F7 to F9, F12). Against: at Figma the REST
  route needs the highest plan, otherwise a plugin or the agent
  server; the tools' versions of the format differ (F12).
- **O3. The vendor's component link as the vocabulary, now.** For: the
  mappings are served to agents by the vendor's own server (F2, F5).
  Against: it links code components to design components, and where
  nothing is implemented there is no code to link; it presupposes paid
  seats and one vendor.
- **O4. Links only.** A description cites a design by its node link,
  and a node carries the address of the description as a dev resource
  (F6). For: the cheapest, both ways, no conversion. Against: a link
  keeps nothing in step; ten to a node; one vendor.
- **O5. An agent skill as the connection, later.** A skill reads the
  description and writes or checks a design through the tools' agent
  servers (F3, F11). For: it is how both vendors write designs today,
  and it needs no format. Against: beta and to be paid by use at
  Figma, output to be reviewed by hand, one page in focus at Penpot;
  each run is a one-way transfer.

## Relevance to this project

The recommendation, the agent's own inference from F1 to F14: O1 from
the first version, with the token discipline of O2; O4 and O5 as
additions when a specialist brings a tool; not O3 as a first step. It
rests on F13: every connection found attaches to an identifier, a
name or a token, never to prose, so the path stays open as long as
the text carries these five things.

1. **Identifiers of its own** for every element definition, component
   and page, stable across renaming and never taken from a tool. The
   tools assign theirs at creation (node IDs returned by the writing
   script [4], UUIDs [14]), so they can only be recorded afterwards.
2. **A binding kept apart from the description**, empty at first: own
   identifier to file key and node ID or component link [1][8], or to
   UUID [14]. Inference: what would close the path is an identifier
   derived from position or wording, which a rebuilt design file
   breaks.
3. **A closed vocabulary of components**: one name each, and for each
   its properties by name and kind (a text, a yes or no, a choice from
   listed values, a slot, a nested component). The mapping interface
   reads properties by name and translates listed values [8], and the
   library is searched by text [2]; a value given as free prose has
   nothing to map from. This supports the idea under test: a
   definition per element is the unit both tools call a component.
4. **Tokens by name, never a raw value**, the names in segments free
   of dot, brace and leading dollar [11][10], typed as the format
   types them, with modes or themes foreseen as a dimension ([10]
   collections and modes, [15] sets and themes).
5. **Placement as structure**: a page as a tree of named elements in
   order, since both reading interfaces deliver a tree (a JSON
   document tree [1], an XML outline [2]). Inference, and the weakest
   of the five: no source opened says how "where they stand" should
   be written.

Chosen against O3, because it ties the first step to one vendor's
seats and to code that does not exist yet, and against waiting for a
round trip, which no source shows (F14). What the recommendation does
not settle: whether the specialist's design or the text is the source
of truth once both exist; the sources found describe transfers, not a
rule of precedence.

Consult when: the identifier scheme of interface elements is decided;
a format for tokens is chosen; a specialist asks to attach Figma or
Penpot to a project; a skill that pushes a description into a design
tool, or checks one against it, is considered; someone claims that
design and code or text "stay in sync".

## Sources

All pages: summarised fetch through the run's fetch tool, then a
second, direct fetch of the same address in which the quoted phrases
were matched as strings; "undated" pages were read on 2026-11-21.

1. "Endpoints", the page of the file endpoints in the Figma REST API
   documentation; Figma; undated;
   https://developers.figma.com/docs/rest-api/file-endpoints/ ;
   primary; summarised fetch of the whole page; original.
2. "Tools and prompts", Figma MCP server documentation; Figma;
   undated;
   https://developers.figma.com/docs/figma-mcp-server/tools-and-prompts ;
   primary; summarised fetch of the whole page; original.
3. "Write to canvas", Figma MCP server documentation; Figma; undated;
   https://developers.figma.com/docs/figma-mcp-server/write-to-canvas/ ;
   primary; summarised fetch of the whole page; original.
4. "figma-use", skill file (SKILL.md) of the repository
   figma/mcp-server-guide, branch main; Figma; undated;
   https://github.com/figma/mcp-server-guide/blob/main/skills/figma-use/SKILL.md ;
   primary (an agent's rules file in a public repository); summarised
   fetch of the whole file, the rules partly paraphrased by the fetch;
   original.
5. "Figma MCP Server Guide", README of the repository
   figma/mcp-server-guide; Figma; undated (95 commits shown, no date
   read);
   https://github.com/figma/mcp-server-guide ; primary; summarised
   fetch of the README as shown on the repository page; original.
6. "Figma MCP: generate_figma_design should resolve HTML elements to
   existing library components instead of raw frames", a feature
   request by a forum member, with one reply; Figma Forum; 2026-02-25,
   the reply 2026-04-01 (structured data);
   https://forum.figma.com/suggest-a-feature-11/figma-mcp-generate-figma-design-should-resolve-html-elements-to-existing-library-components-instead-of-raw-frames-51286 ;
   primary as a practitioner's report; summarised fetch of the whole
   thread; original.
7. "Introduction", the first page of the Code Connect documentation;
   Figma; undated; https://developers.figma.com/docs/code-connect/ ;
   primary; summarised fetch of the whole page; original.
8. "Writing template files", Code Connect documentation; Figma;
   undated;
   https://developers.figma.com/docs/code-connect/template-files/ ;
   primary; summarised fetch of the whole page; original.
9. "Endpoints", the page of the dev resources endpoints in the Figma
   REST API documentation; Figma; undated;
   https://developers.figma.com/docs/rest-api/dev-resources-endpoints/ ;
   primary; summarised fetch of the whole page; original.
10. "Endpoints", the page of the variables endpoints in the Figma
    REST API documentation; Figma; undated;
    https://developers.figma.com/docs/rest-api/variables-endpoints ;
    primary; summarised fetch of the whole page; original.
11. "Design Tokens Format Module 2025.10", Final Community Group
    Report; Design Tokens Community Group; 28 October 2025 (the
    report's own cover); https://www.designtokens.org/tr/2025.10/format/ ;
    primary; summarised fetch, partially: the first 100,000 of 114,563
    characters, which hold sections 1 to 9 cited here, the tail not
    read; original (the group also files it among the W3C community
    reports, not opened).
12. "GitHub - Git Sync Provider", Tokens Studio for Figma
    documentation; Tokens Studio; undated;
    https://docs.tokens.studio/token-storage/remote/sync-git-github ;
    primary; summarised fetch of the whole page; original.
13. "Penpot MCP server", Penpot help centre; Penpot (Kaleidos);
    undated, footer 2026; https://help.penpot.app/mcp/ ; primary;
    summarised fetch of the whole page; original.
14. "Penpot File Format (.penpot)", technical guide, data model;
    Penpot (Kaleidos); undated, footer 2026, its example manifest
    naming version 2.12.0;
    https://help.penpot.app/technical-guide/developer/data-model/penpot-file-format/ ;
    primary; summarised fetch of the whole page; original.
15. "Design Tokens", user guide, design systems; Penpot (Kaleidos);
    undated, footer 2026;
    https://help.penpot.app/user-guide/design-systems/design-tokens/ ;
    primary; summarised fetch of the whole page; original.

## Opened and not used

None: all fifteen pages opened are cited above.

## Search record

Queries, in order:

1. Figma MCP server tools, design context, variables, Code Connect,
   write to canvas.
2. Penpot MCP server, plugin API, open file format, design tokens.
3. Design Tokens Community Group format, stable version 2025.
4. Figma Code Connect documentation, template files, CLI, repository.
5. Figma REST API variables endpoints, Enterprise, scopes.
6. "design to code round trip problems" (disconfirming).
7. "design tool or code as source of truth" (disconfirming).
8. Penpot .penpot file format, ZIP, JSON, data model.
9. Figma MCP use_figma, Plugin API JavaScript, skill.
10. Tokens Studio sync providers, GitHub, push and pull.
11. generate_figma_design, code to canvas, limitations, sync back.
12. Code Connect issues, variants, nested instances, drift.
13. Style Dictionary, token format support, one-way transform.

Pages opened, fifteen, in order: [2], [7], [10], [5], [1], [13], [14],
[15], [11], [4], [3], [6], [8], [12], [9]. After the fifteenth no new
page was opened; the same fifteen addresses, and the raw form of the
file [4], were fetched again directly, more than once, to match the
quoted phrases, to read the pages' titles and to see that each address
answers.

Seen in result lists, not opened and used for no finding: that the
token plugin writes the tool's variable identifiers into a themes file
of the repository; that the framework parsers of Code Connect are
being replaced by template files with a migration date in 2026; that a
Penpot release opened token values to its plugin interface; forum
reports of Code Connect mappings lost on variant sets; a published
OpenAPI specification of Figma's REST interface; Figma's help-centre
page of questions on the agent server.

The disconfirming query: its two phrases returned an encyclopaedia
entry on round-trip engineering of models, vendors' pages on their own
market, and opinion pieces, among them one recent piece arguing that
the round trip between design and code is not solved; none was opened,
the first being off the question and the others excluded by kind. The
answer to the query came from the primaries instead (F14): the
expectation held in a weaker form.

Why the run ended: the opening budget, fifteen pages. Of the card's
stop rule the second half was met, every route having a primary
source; the first was not, the last two queries still returning leads
that were left unopened.
