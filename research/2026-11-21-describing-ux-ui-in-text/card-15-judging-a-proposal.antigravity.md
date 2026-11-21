---
date: 2026-11-21
project: forge
topic: Judging an interface proposal before it is built
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 15; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":53205,"output_tokens":23766,"thinking_tokens":11518,"cache_read_tokens":130526,"total_tokens":76971}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-15-judging-a-proposal
status: immutable
---

# How an interface proposal is judged before it is built

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Five established methods judge a user interface design (meaning the
interface's screens, dialogue elements, and behaviour, as distinct from
technical architecture and evaluated against the visual and behavioural
identity of a design system) before code is built: heuristic evaluation,
cognitive walkthrough, expert review by checklist or ergonomic criteria,
consistency and standards inspection, and design critique [1, 3, 4, 6,
7]. By their original definitions, the first four can all run on a
written specification before any prototype exists, provided the text
names the screens or states, the available controls and their labels,
and the system's response to each user action, whereas visual layout and
aesthetic judgements require spatial or visual representation [1, 2, 3,
4]. The disconfirming queries confirmed both expected weaknesses: human
usability inspections suffer a pervasive "evaluator effect" with average
pairwise agreement of only 5% to 65% [8], and language models running
heuristic or design-critique evaluations generate high false-positive
rates (roughly 40% false positives for GPT-4 on structured JSON mockups
[9], 86.9% invalid comments for unaugmented zero-shot Gemini Pro Vision
[10], and 21.2% overlap with human experts for GPT-4o on screenshots
[11]). Unexpectedly, when running a cognitive walkthrough (December
2025), language models err in the opposite direction: out of the box,
they complete tasks along optimal paths and under-report human failure
points (false negatives) unless explicitly prompted to simulate human
cognitive friction [12]. Because this environment provides web access
exclusively through a grounded search summariser, every finding below
rests on summarised fetches (tertiary representations of the primary
sources).

## Question

#### Card 15: How a proposal is judged before it is built
- **Question:** By which established methods is a design of an interface
  judged before it is built (heuristic evaluation, cognitive
  walkthrough, design critique, expert review by checklist, inspection
  of consistency): what does each look at, what does it need as its
  input (can it be run on a textual description, or only on a picture or
  a prototype), and what is known about language models performing such
  an evaluation?
- **Why it matters:** a proposal made by an agent is tuned by a human
  and read by reviewer agents; the description must be something that
  can be judged.
- **What would answer it:** the original literature of the methods and
  recent studies of automated evaluation.
- **Where to look:** the literature of usability inspection methods;
  writing on design critique; studies of 2024 to 2026 on models as
  evaluators of interfaces.
- **Disconfirming query:** "heuristic evaluation unreliable evaluator
  effect", "LLM usability evaluation false positives"; expected:
  evaluators disagree, and models over-report.
- **Stop rule:** nothing new from a differently worded query and every
  route has a primary source; ten to fifteen pages opened.

**Disambiguation of "design" and baseline:** In the sources below,
"design" means the design of the user interface (its dialogue elements,
screen structure, wording, and interaction sequences), except in
consistency and standards inspections where that interface design is
checked against a second sense of "design": the visual and behavioural
identity of a design system or platform style guide. Within the
project's workflow, the textual interface description sits alongside the
third sense of "design"—the technical solution design between
requirements and user stories—before anything is built. To beat a
generic textbook summary of usability methods, this note must identify
the exact input specification each method demands according to its
founding papers (specifically whether prose/text suffices without pixels
or an interactive build) and quantify how 2024–2026 language models
perform, fail, and disagree with human experts on those inspections.

## Key findings

- **F1. Heuristic evaluation inspects dialogue elements against a small
  set of broad usability principles and was demonstrated from its
  inception on written paper specifications before implementation**
  [consensus — controlled study, summarised fetch]. Nielsen and Molich
  (1990) introduced heuristic evaluation as an informal inspection in
  which evaluators inspect an interface against nine (later ten) general
  heuristics such as visibility of system status, match between system
  and real world, consistency, and error prevention [1]. In Experiment 1
  ("Teledata") of their 1990 study, 37 evaluators inspected a printed
  specification of screen dumps and rules rather than a live system,
  identifying problems against 52 known issues [1]. Nielsen (1992)
  Confirmed in a study of a telephone banking interface that heuristic
  evaluation can be carried out on interfaces that exist only on paper
  (written dialogue specifications), finding that single evaluators
  detected on average 22% of usability problems (novices), 41% (regular
  usability specialists), and 60% ("double specialists" with both
  usability and domain expertise), requiring aggregation of 3 to 5
  evaluators [2]. All findings in F1 rest on summarised fetches of [1,
  2].

- **F2. Cognitive walkthrough evaluates step-by-step learnability by
  exploration and explicitly accepts a textual description of prompts
  and system responses alongside three non-visual inputs** [consensus —
  practitioner guide and controlled study, summarised fetch]. Wharton,
  Rieman, Lewis, and Polson (1994) specify four mandatory inputs for a
  cognitive walkthrough: (1) explicit assumptions about the user
  population's prior knowledge, (2) a suite of representative benchmark
  task scenarios, (3) the fine-grained correct sequence of atomic
  actions for each task, and (4) a concrete description or specification
  of the interface showing what it displays before each action and how
  it responds after each action [3]. The authors state that the
  interface representation need not be a working prototype; it can be a
  paper specification, storyboard, or text specification of prompts and
  responses [3]. At each atomic action, evaluators attempt to tell a
  "credible story" by answering four diagnostic questions: whether the
  user will try to achieve the right effect, notice that the correct
  action is available, associate the action with the desired effect, and
  see progress via feedback after acting [3]. In an empirical comparison
  on pre-release software, Jeffries et al. (1991) found that cognitive
  walkthroughs traced user goals and could be run by developers, but
  found fewer severe problems than heuristic evaluation and missed
  system-wide consistency issues because of their narrow task-path focus
  [5]. All findings in F2 rest on summarised fetches of [3, 5].

- **F3. Expert review by checklist, consistency inspection, and
  standards inspection evaluate taxonomic compliance, cross-screen
  uniformity, and feature complexity, and can operate on structured
  element and flow specifications** [consensus — controlled study and
  framework taxonomy, summarised fetch]. In Nielsen and Mack's (1994)
  taxonomy and Wixon et al.'s (1994) framework [4]: (a) **consistency
  inspection** has evaluators review interfaces across a product or
  product family to verify that terminology, layout conventions, color
  or coding rules, and interaction models behave uniformly so users do
  not relearn interactions; (b) **standards inspection** checks an
  interface item-by-item against a mandated platform style guide, design
  system, or ISO standard; and (c) **feature inspection** walks through
  the feature set for typical scenarios to check whether functions
  require overly long action sequences or unnatural domain steps [4]. To
  replace unmanageable thousand-rule style guides and ad-hoc heuristics,
  Bastien and Scapin (1993) formalized 8/9 main **ergonomic criteria**
  subdivided into 18 elementary criteria (Guidance: prompting,
  grouping/distinction, immediate feedback, legibility; Workload:
  briefness, information density; Explicit Control; Adaptability; Error
  Management; Consistency; Significance of Codes; Compatibility),
  showing in controlled experiments that checklist-style criteria
  improved completeness and classification reliability over unguided
  inspection [6]. In Jeffries et al. (1991), applying written software
  guidelines excelled at catching system-wide consistency flaws that
  task walkthroughs missed, though it was more tedious than heuristic
  evaluation [5]. All findings in F3 rest on summarised fetches of [4,
  5, 6].

- **F4. Design critique evaluates whether a proposal's form and
  behaviour fulfil its stated intent, rationale, and human context,
  requiring explicit statement of objectives alongside the artefact**
  [consensus — practitioner claim and scholarly essay, summarised
  fetch]. Unlike usability inspections that hunt for rule violations,
  design critique as formalized in studio practice by Connor and
  Irizarry (2015) and in HCI scholarship by Blevis (2007) and Greenberg
  and Buxton (2008) judges an interface design relative to its stated
  intent, target personas, and design rationale [7]. Its required inputs
  are the artefact at its current fidelity (which can be an early concept
  brief, user scenario, component inventory, sketch, or wireframe) plus
  an explicit statement of the problem framed, the user's goal, and why
  specific trade-offs were chosen [7]. Greenberg and Buxton (2008) argue
  that applying rigid usability inspection metrics prematurely to early
  generative designs without critiquing intent and rationale harms novel
  design exploration [7]. All findings in F4 rest on a summarised fetch
  of [7].

- **F5. Human usability inspections suffer from a severe "evaluator
  effect" across all methods, with pairwise agreement between human
  evaluators averaging only 5% to 65%** [consensus — audit of controlled
  studies, summarised fetch]. Disconfirming query 1 returned Hertzum and
  Jacobsen's (2001) review of 11 empirical studies covering Heuristic
  Evaluation, Cognitive Walkthrough, and Thinking-Aloud tests [8]. They
  documented that the average overlap between any two evaluators
  inspecting the exact same interface with the exact same method ranges
  from **5% to 65%**, and that this low agreement holds across both
  novices and experienced specialists, simple and complex systems, and
  cosmetic as well as severe problems [8]. Consequently, no single human
  evaluator—and no single ground-truth run—provides a complete or
  reproducible list of interface flaws [8]. All findings in F5 rest on a
  summarised fetch of [8].

- **F6. Language models performing heuristic evaluation on structured
  text/JSON representations of UI mockups match human recall (0.380 vs
  0.336) but suffer lower precision (0.603 vs 0.829, ~40% false
  positives)** [emerging — controlled study, summarised fetch]. Duan et
  al. (March 2024, CHI 2024) evaluated GPT-4 on 51 UI mockups across
  three guideline sets by extracting the Figma layer hierarchy, element
  names, and bounding properties into a condensed textual **JSON**
  structure paired with text heuristic definitions [9]. Against a
  ground-truth dataset, GPT-4 achieved **0.603 precision**, **0.380
  recall**, and **0.466 F1**, compared to average human evaluator scores
  of **0.829 precision**, **0.336 recall**, and **0.478 F1** (as of
  March 2024) [9]. In a study with 12 expert designers, GPT-4 excelled
  at micro-copy clarity and semantic checks, but roughly 40% of its
  flags were false positives [9]. All findings in F6 rest on a
  summarised fetch of [9].

- **F7. Multimodal language models evaluating static UI screenshots
  exhibit low overlap with human experts (21.2%) and high false-positive
  rates unless grounded with few-shot critique datasets** [emerging —
  controlled studies, summarised fetch]. Disconfirming query 2 returned
  two controlled studies from 2024–2025:
  1. In **UICrit** (August 2024, UIST 2024), Duan et al. collected 3,059
     human design critiques across 983 mobile screens and found that
     unaugmented zero-shot MLLM critiques (Gemini Pro Vision) had only
     **13.1%** of their generated comments validated as accurate by
     human experts (an 86.9% false-positive/invalid rate); adding
     few-shot visual and textual prompting from the UICrit dataset
     yielded a **55% performance gain** in feedback quality (as of
     August 2024) [10].
  2. Guerino et al. (June 2025, INTERACT 2025) compared **GPT-4o**
     evaluating web system screenshots using a literature-grounded
     Nielsen heuristic prompt against three human HCI experts [11].
     GPT-4o caught **only 21.2%** of the issues identified by the human
     experts, while surfacing **27 additional issues** humans missed
     (primarily under Heuristic 8, *aesthetic and minimalist design*,
     and Heuristic 2, *match between system and the real world*) [11].
     However, GPT-4o struggled on workflow-dependent heuristics
     (Heuristic 3, *user control and freedom*, and Heuristic 7,
     *flexibility and efficiency of use*) and generated numerous false
     positives by hallucinating missing feedback or validation that a
     static screenshot did not show (as of June 2025) [11]. Contradicted
     in error direction by [12] on cognitive walkthroughs (see F8). All
     findings in F7 rest on summarised fetches of [10, 11].

- **F8. In automated cognitive walkthroughs, baseline frontier LLMs make
  the opposite error—under-reporting usability failures (false
  negatives)—because they navigate more optimally than humans unless
  explicitly re-prompted** [single source — controlled study, summarised
  fetch]. Zhong, McDonald, and Hsieh (December 2025) compared **GPT-4**
  and **Gemini-2.5-Pro** performing synthetic cognitive walkthroughs
  (step-by-step action selection, think-aloud rationale, and confusion
  rating across 16 runs on 2 mobile apps) against human walkthrough data
  [12]. Unlike heuristic evaluations where models over-report flaws
  [9, 10, 11], baseline LLMs in a cognitive walkthrough achieved higher
  task completion rates, took more direct paths, and **identified
  significantly fewer failure points** than human evaluators because
  models parse text and icons without experiencing human cognitive
  friction [12]. Targeted prompt interventions aligning the model with
  human confusion criteria reduced this gap and improved failure-point
  prediction (as of December 2025) [12]. All findings in F8 rest on a
  summarised fetch of [12].

## Unexpected

**Structured text out-performs ungrounded vision for LLM inspection,
reconfiguring the assumption that text is merely a weaker substitute for
a picture.** The card asks whether pre-build evaluation methods can be
run on a textual description or only on a picture or prototype. Duan et
al. (2024) [9] did not feed raw pixels to GPT-4; they converted visual
Figma mockups *into* a pruned textual JSON hierarchy paired with text
guidelines and achieved an F1 score (0.466) nearly matching human
evaluators (0.478), whereas unaugmented zero-shot visual critique on
screenshots in Duan et al. (2024) [10] achieved only 13.1% valid
comments, and static screenshot inspection in Guerino et al. (2025) [11]
hallucinated missing dynamic states and error-handling rules because
those rules were invisible in a flat image. A textual specification that
explicitly states element hierarchy, labels, states, and transition
rules supplies the exact dynamic context that static screenshots lack
[9, 11].

**The error direction of LLM evaluators flips between heuristic
inspection (false positives) and cognitive walkthrough (false
negatives).** The disconfirming query expected models to over-report
across the board. While models prompted to "find heuristic violations"
or "critique a screen" aggressively over-report and hallucinate problems
[9, 10, 11], models prompted to "step through a task" in a cognitive
walkthrough (Zhong et al., December 2025) [12] act as hyper-competent
readers who decode ambiguous labels and complete tasks where humans
stall, resulting in false negatives unless prompted to model human
cognitive limits.

## Not found

1. **Controlled benchmarks on pure pre-layout Markdown UI
   specifications:** Searches on `arxiv.org` and general web sources for
   2024–2026 empirical studies measuring LLM heuristic evaluation or
   cognitive walkthrough precision/recall on purely prose or Markdown UI
   descriptions written *before* any spatial layout or bounding-box
   coordinates exist returned no controlled benchmark. Existing studies
   test either JSON trees exported from visual mockups (which include
   spatial grouping and bounding properties) [9] or screenshots paired
   with task prompts [10, 11, 12].
2. **Inter-rater reliability percentage for informal design critique:**
   Unlike heuristic evaluation, cognitive walkthrough, and think-aloud
   testing (quantified at 5%–65% in [8]), no empirical study was found
   that reports a percentage inter-rater overlap for studio design
   critique [7].

## Options

Because the project's human-and-agent workflow must judge a textual UI
proposal before it is handed to a build stage, the project has three
distinct ways to structure pre-build evaluation:

1. **Option A: Multi-method textual inspection on a structured Markdown
   specification (Cognitive Walkthrough + Checklist/Consistency +
   Intent Critique) before any visual preview.**
   - *How it works:* Require the Markdown UI description to include the
     exact inputs required by Wharton et al. [3], Bastien & Scapin [6],
     and Connor & Irizarry [7]: (a) design intent and user persona
     assumptions, (b) benchmark task scenarios and atomic action
     sequences, (c) component definitions with exact labels, states, and
     validation/error responses, and (d) page compositions naming which
     elements appear and how the screen changes after each action. Run
     separate reviewer-agent passes for (1) deterministic/checklist
     consistency against the design system, (2) step-by-step cognitive
     walkthrough of user stories, and (3) heuristic evaluation of
     wording, error prevention, and control.
   - *Trade-offs:* Evaluates workflow, state transitions, consistency,
     and micro-copy early with zero rendering overhead and avoids static
     screenshot hallucinations about missing state transitions [11];
     however, it cannot judge visual crowding, contrast, or spatial
     aesthetics (Heuristic 8) until a preview or layout exists [9, 11].

2. **Option B: Render-first evaluation (generate a wireframe/HTML
   preview first, then run multimodal LLM + human inspection on the
   rendered view).**
   - *How it works:* Treat the textual proposal solely as an input to a
     preview generator, and run all human and MLLM heuristic evaluations
     and critiques on the rendered screenshots or DOM.
   - *Trade-offs:* Enables visual and spatial inspection (where GPT-4o
     catches layout clutter humans overlook [11]), but delays catching
     task-flow and state-transition flaws, suffers high false-positive
     rates on static images (~40% to 86.9% without grounding and state
     specifications [9, 10, 11]), and conflates rendering bugs with
     specification flaws.

3. **Option C: Two-stage hybrid gate (Textual walkthrough & consistency
   audit on the Markdown spec, followed by visual heuristic check on a
   rendered preview, with mandatory human triage).**
   - *How it works:* Stage 1 runs automated Consistency/Checklist
     Inspection, Intent Critique, and a friction-calibrated Cognitive
     Walkthrough directly on the Markdown component-and-page
     specification (catching missing states, inconsistent terms, and
     broken task steps). Once the human tunes the text, Stage 2 checks
     visual layout on the preview. In both stages, the human filters LLM
     flags rather than accepting auto-rewrites.
   - *Trade-offs:* Separates structural/behavioural defects from spatial
     defects and matches each inspection method to the input modality it
     actually requires [1, 3, 9, 11], at the cost of maintaining an
     explicit schema in the Markdown specification so reviewer agents
     have the inputs needed to judge it.

## Relevance to this project

**Recommendation (agent inference):** Adopt **Option C (Two-stage hybrid
gate)** and design the project's Markdown UI specification schema around
the exact input requirements of the five inspection methods.

Specifically (agent inference from [1, 3, 4, 6, 7, 9, 11, 12]):
1. **What the textual description must contain to be judgeable:** The
   idea mentioned in the card's frame—giving every screen element its
   own small Markdown definition and having a page definition name which
   elements it holds and where they stand—is directly supported by the
   inspection literature *if and only if* three things are present in
   the text:
   - **Pre-action display and post-action feedback per element/state**
     (required by Cognitive Walkthrough [3] and needed to prevent LLMs
     from hallucinating "missing feedback/validation" false positives as
     they do on static screenshots [11]).
   - **Explicit task scenarios and atomic action sequences** linking
     user stories to screen transitions (required by Cognitive
     Walkthrough [3] and Feature Inspection [4]).
   - **Design intent and user profile assumptions** at the document or
     flow level (required by Design Critique [7] and Cognitive
     Walkthrough [3]).
2. **How reviewer agents should be configured:**
   - Do **not** use a single generic "evaluate this UI" prompt. Both
     humans (5%–65% agreement [8]) and LLMs (21.2% overlap with humans
     [11]) have narrow lenses.
   - Use **checklist/standards inspection** [4, 6] for what LLMs and
     scripts do best on text: checking consistent terminology, component
     reuse, presence of error states, and explicit control across the
     component definitions and page definitions.
   - When running an LLM **cognitive walkthrough** on the text paths,
     explicitly prompt the model to simulate novice/non-ideal human
     comprehension and flag ambiguous labels, countering the baseline
     LLM tendency to under-report walkthrough failures [12].
   - When running an LLM **heuristic evaluation**, treat its output
     strictly as a triage list for the human author to accept or
     dismiss, because roughly 40% of LLM heuristic flags on structured
     UI representations are false positives [9].
   - Defer **visual/spatial heuristic checks** (Heuristic 8: visual
     clutter, alignment, density) to the preview stage rather than
     guessing them from prose [9, 11].

**Chosen against:** Relying on unguided single-agent LLM critique (rejected
due to 40%–86.9% false-positive rates [9, 10] and the evaluator effect
[8]) or waiting until after build/rendering to judge task learnability
and state completeness (rejected because heuristic evaluation, cognitive
walkthrough, and consistency inspection were proven on written
specifications before implementation [1, 2, 3, 4]).

**Consult when:**
- Designing the mandatory fields of a screen element definition, page
  definition, or user-flow specification so that an interface proposal
  can be reviewed before rendering or building.
- Writing system prompts for reviewer agents that perform heuristic
  evaluation, cognitive walkthrough, checklist audit, or design critique
  on a textual UI proposal.
- Deciding which review checks belong on the Markdown specification
  versus which must wait for a visual preview.

## Sources

[1] *"Heuristic Evaluation of User Interfaces"*, Jakob Nielsen and Rolf
Molich, 1990 (dated by bibliographic structured data: ACM CHI '90
Proceedings, pp. 249–256),
https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEX5g9AzY7YSE8ckLJG98JeNoM_Zh1_m3X78QWSwQMEyfdZjRWK8w0TQKnQI8L1sDJVkearwrr1MXSMwDUEr-Ax4Rx-hxKqvk_SjkdX_Tf9MT5CyHDSwBW3Qw4wHMCxHM9FWHIAsw==
; kind: primary (read via tertiary grounding summary); how read:
summarised fetch; original paper (hosted copy at mortenhertzum.dk).

[2] *"Finding Usability Problems Through Heuristic Evaluation"*, Jakob
Nielsen, 1992 (dated by bibliographic structured data: ACM CHI '92
Proceedings, pp. 373–380, DOI `10.1145/142750.142834`),
https://doi.org/10.1145/142750.142834 and
https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQH5VyOmw2hosYY5pWMxvyq_bqe-u74ltiH-9oUqPnFRy7OkEbhFHTB-4SVgD5QeBirOmi9ajKAY7hSBDEpXu4hJuoHeUDNcKz9ZoCUqt8z3OMEeCt8ryZREKBO9S6oj-jK2xlcDfc8rn39oWqE2gznpnAx5bZxFrdtP1zF8f9s7KlKFpwRVOiq52BuzmrHTs6MANbuPuMF0ma0ixBWcSdyRxze4Htpuqg==
; kind: primary (read via tertiary grounding summary); how read:
summarised fetch; original paper (and academic hosted copy at
fu-berlin.de).

[3] *"The Cognitive Walkthrough Method: A Practitioner's Guide"*,
Cathleen Wharton, John Rieman, Clayton Lewis, and Peter Polson, 1994
(dated by bibliographic structured data: Chapter 5 in *Usability
Inspection Methods*, John Wiley & Sons, 1994 / University of Colorado
Institute of Cognitive Science Technical Report),
https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEJ5PZxdRQxzHQ-aq57N_J7o1bSmlm_KaMDvAMVM0QIqBbFn3o5Bkys3z6ZEdb4SwT6OBURsdxevhSaXF4DTmElyeQKZtYvz5vaw3M2XClHZogzNGY2NLOUo3lGTQdWYgAN2-GM4QS_DtXZnB1C_6m3FSNjJtYs3IB2ICexaBmdHcP_3E0=
; kind: primary (read via tertiary grounding summary); how read:
summarised fetch; original technical report / chapter hosted at
colorado.edu.

[4] *"Usability Inspection Methods"* (including *"Inspections and Design
Reviews: Framework, History, and Reflections"* by Dennis Wixon, Susan
Jones, Linda Tse, and George Casaday), edited by Jakob Nielsen and
Robert L. Mack, 1994 (dated by bibliographic structured data: John Wiley
& Sons, 1994),
https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEbOvlw7MK6vW5XMakBnyPj5zc7T6MXPu96KwjvRkpzLc0K3K2dsgQqor084Jk7gVUIFELdDUqVLY0BbFk5CJ68xN_g5NWZ2xjtsPx5jMOobCrFIpYWzroSV9i-7r-nDM1DZVjZE0HIf8z2dSlWoe1ESlzyuP70HXb2Yi8=
; kind: secondary/primary synthesis of the inspection methods (read via
tertiary grounding summary); how read: summarised fetch; original book
review/record on tandfonline.com.

[5] *"User Interface Evaluation in the Real World: A Comparison of Four
Techniques"*, Robin Jeffries, James R. Miller, Cathleen Wharton, and
Kathy M. Uyeda, 1991 (dated by bibliographic structured data: ACM CHI
'91 Proceedings, pp. 119–124),
https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGUKFhjugMY4z56mhPsjk-ivV_FWLcZzBSFWuOflPS0Me7Fd3Jn8fFbDwCfZUjRgWHPTZVItTT96v-V1gcl4d_amCQUVHK3n4_92_jOcQXFWrBu4LqN3aNTs1Jy54yrGsip4QZwD8Am_Im_C7K7nzWtyB67uD56fghxMTmgYdoAGDOHL3BoXqzgW6Qb9XGTD2gQAzE-whlbup5Q
; kind: primary (read via tertiary grounding summary); how read:
summarised fetch; academic hosted copy at queensu.ca.

[6] *"Ergonomic Criteria for the Evaluation of Human-Computer
Interfaces"* (and *"Evaluating a User Interface with Ergonomic
Criteria"*), J. M. Christian Bastien and Dominique L. Scapin, May 1993 /
1995 (dated by report byline and structured data: INRIA Technical Report
RT-0156, May 1993; *International Journal of Human-Computer
Interaction*, 1995),
https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGynaCtwh8FiBCcerbnq9AMIAhl-xx4Jlt03OT73QEkO1NppLDSf5dbiXMgowZpVIxQARnhmP8XnrQqXSjdfPIASovcHj4A1NQwgAOFpSW98D9Qnm3lIwJtJDPsEsoIWmPf37nxV9c8DAbX2HEhZjUvuH-JdBY=
; kind: primary (read via tertiary grounding summary); how read:
summarised fetch; original journal publication on tandfonline.com.

[7] *"Usability Evaluation Considered Harmful (Some of the Time)"* (Saul
Greenberg and Bill Buxton, ACM CHI 2008) junto with *"Sustainable
Interaction Design: Invention & Disposal, Renewal & Reuse"* (Eli Blevis,
ACM CHI 2007) and *"Discussing Design: Improving Communication and
Collaboration through Critique"* (Adam Connor and Aaron Irizarry,
O'Reilly Media, 2015) (dated by bibliographic structured data: 2007,
2008, 2015),
https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEl133nBJCFoauqimUx1aImnU1giZWwKtYutd2PR__Jo5LqDl7h-xe0fnLqfgGojH3hKCH_qaVj1jqsbCnI6lGhFS1PNQdJBPLUjXOOhNNj8uKjeDWN07DvpfxuxW5q1zEtP7uou82XZ1gLGJt7oHyREtSlujeCJxTKTkQ=
; kind: primary (read via tertiary grounding summary); how read:
summarised fetch; academic hosted copy at uchile.cl.

[8] *"The Evaluator Effect: A Chilling Fact About Usability Evaluation
Methods"*, Morten Hertzum and Niels Ebbe Jacobsen, 2001 (dated by
bibliographic structured data: *International Journal of Human-Computer
Interaction*, 13(4), 421–443, 2001),
https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFdN7lbE_RSYk_kqtavMXO-FrEMMxqZPAf3hgtn_3rQikyu0vM0B5C2MOakWqvQEHoIMyDx4SZ3dj4yOvnXMBKoWIeJDfgn_F7c16L80pgiIY0YSAmQ95jttp9kDiUEsIMbKtvW
; kind: primary (read via tertiary grounding summary); how read:
summarised fetch; author's self-archived original at mortenhertzum.dk.

[9] *"Generating Automatic Feedback on UI Mockups with Large Language
Models"*, Peitong Duan, Jeremy Warner, Yang Li, and Bjoern Hartmann,
2024-03-19 (dated by arXiv structured submission data: `arXiv:2403.13139`
/ ACM CHI 2024), https://arxiv.org/abs/2403.13139 ; kind: primary (read
via tertiary grounding summary); how read: summarised fetch; original on
arXiv.

[10] *"UICrit: Enhancing Automated Design Evaluation with a UI Critique
Dataset"*, Peitong Duan, Chin-yi Chen, Gang Li, Bjoern Hartmann, and
Yang Li, 2024-07-11 / revised 2024-08-13 (dated by arXiv structured
submission data: `arXiv:2407.08850` / ACM UIST 2024),
https://arxiv.org/abs/2407.08850 ; kind: primary (read via tertiary
grounding summary); how read: summarised fetch; original on arXiv.

[11] *"Can GPT-4o Evaluate Usability Like Human Experts? A Comparative
Study on Issue Identification in Heuristic Evaluation"*, Guilherme
Guerino, Luiz Rodrigues, Bruna Capeleti, Rafael Ferreira Mello, André
Freire, and Luciana Zaina, 2025-06 (dated by arXiv structured data and
Springer LNCS vol. 15941 INTERACT 2025, DOI
`10.1007/978-3-032-05005-2_20`, `arXiv:2506.16345`),
https://arxiv.org/abs/2506.16345 and
https://doi.org/10.1007/978-3-032-05005-2_20 ; kind: primary (read via
tertiary grounding summary); how read: summarised fetch; original on
arXiv / Springer.

[12] *"Synthetic Cognitive Walkthrough: Aligning Large Language Model's
Performance with Human Cognitive Walkthrough"*, Ruican Zhong, David W.
McDonald, and Gary Hsieh, 2025-12 (dated by arXiv structured submission
data: `arXiv:2512.03568v1`), https://arxiv.org/abs/2512.03568 ; kind:
primary (read via tertiary grounding summary); how read: summarised
fetch; original on arXiv.

## Opened and not used

- `scribd.com` upload of *Usability Inspection Methods*
  (https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEZkXnIgmCCEVearKpK6YA_q86U9w5HES52Psi7kJmTAkdOW4IUt9VhHJeu7Gw12wo1dHAkLeTZyp8R37XPBjZq6MaicdC9LXwJRBSFA-ny9N2ip2Mn7oxY5WKXwJ-qtXCVDMwXn8Zxu25oLuRD5guLU_OPNKalQD_pOOKg9NJdIe1hMG8n0GfmxCbdtLxfYvj3iM0nN-tvJde4uVMs):
  a third-party copy, superseded by [1, 3, 4].
- `educative.io` overview of HCI evaluation methods
  (https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFLx-mlZyefloxE0dFvNZ7fKhxsgS6klAWQr7XY-jYXkdgBwjYzE6oSqSPyahROrgwPyF1jsRwqmrpiQRhtPwZDUX2_Xw5I4QHHnroNNO4TpNqYPGgAFqF8oHW_AMR0ZvnBSgK7-08Z-9DjoajiEKXb-WsmLpjK-Xhvmdqpxb0IU6GYoA==):
  below the bar (secondary course summary), superseded by [1, 3, 4].
- `clay.global` agency blog post on LLM heuristic evaluation
  (https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGVx4i3Mm_MfjzH4jI2JwRf1DgwW4fJkQas9ajpWU_w7eumqV872ydESMl4Pb-AGiaJ0SSEIiKu9zz-ynN-GjZ_rQ3IZ6KigQOG0pBnq9odXZU-eXSrtnGWavJY713PKbwpPaiE6XMh-rtHVzxY591x5TA=):
  vendor blog on its own market, superseded by [9, 11].
- `uxplanet.org` secondary summary of Nielsen's heuristic evaluation
  (https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFggLFq8Ych2a-u-wMdt0XZ4OztPnfokVVXLIA1tHjxDwplvC7dj0cLth78572XCFQbCTgaSO9Byc9j8FsklZLWlkhtg1FpZXvwv6qMnk5ISz3655UcgEKmfvusw3Jtws5y2Dk_Xwf6tZReDitUmXgcEoSGMo_EAZ2L9uKSeu8l_11QoZosJMHA):
  secondary blog copy, superseded by [1, 2].
- `greatquestion.com` UX guide to cognitive walkthroughs
  (https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHJ6Y6n9cJl4209XjOZAYnyL6Xf3Zx00UNMZ-KyIeAURDBtpYunOUSEfOgrSZzNKiLS-dHHORuima1jxBau52Xceb9Dk5USBGpdF8fKa6XsJZAYkSnVNTMp0lO1fgsNE2_nM2UUz7uendLGOt-FLLG90hXvLVKMCA==):
  vendor blog on its own market, superseded by [3].

## Search record

**Queries run (in order):**
1. `usability inspection methods Nielsen Mack heuristic evaluation cognitive walkthrough` (broad survey of inspection methods)
2. `cognitive walkthrough Wharton Polson Lewis Rieman input specification` (broad query on cognitive walkthrough inputs)
3. `design critique interface evaluation methods HCI` (broad query on design critique in HCI)
4. `LLM heuristic evaluation usability inspection UI 2024 2025 2026` (broad query on recent LLM usability inspection studies)
5. `heuristic evaluation unreliable evaluator effect` (disconfirming query 1)
6. `LLM usability evaluation false positives` (disconfirming query 2)
7. `"Heuristic evaluation of user interfaces" Nielsen Molich 1990 written specification "Teledata" prototype` (targeted fetch for [1])
8. `"The Cognitive Walkthrough Method: A Practitioner's Guide" Wharton Rieman Lewis Polson input questions description` on `colorado.edu` (targeted fetch for [3])
9. `"Usability Inspection Methods" "consistency inspection" "standards inspection" "feature inspection" Wixon Nielsen Mack 1994 input` (targeted fetch for [4])
10. `"The Evaluator Effect: A Chilling Fact About Usability Evaluation Methods" Hertzum Jacobsen 2001 agreement percentage` on `mortenhertzum.dk` (targeted fetch for [8])
11. `"Generating Automatic Feedback on UI Mockups with Large Language Models" Duan 2024 arXiv ID exact URL figures` on `arxiv.org` (targeted fetch for [9])
12. `"heuristic evaluation" LLM "usability" "false positives" user interface 2024 2025 arXiv ID title authors` on `arxiv.org` (targeted fetch for [11])
13. `"Guerino" 2026 OR 2025 LLM heuristic evaluation usability inspection tandfonline title DOI authors` (targeted bibliographic fetch for [11])
14. `"2403.13139" "Generating Automatic Feedback on UI Mockups with Large Language Models" abstract results precision recall human evaluators input text JSON screenshot` on `arxiv.org` (content fetch for [9])
15. `"2506.16345" "Can GPT-4o Evaluate Usability Like Human Experts" abstract method results false positives human experts overlap date` on `arxiv.org` (content fetch for [11])
16. `"cognitive walkthrough" "large language model" OR "LLM" user interface evaluation arXiv ID title authors 2024 2025 2026` on `arxiv.org` (targeted fetch for [12])
17. `"UICrit" Duan 2024 design critique evaluation UI arXiv ID title authors results` on `arxiv.org` (targeted fetch for [10])
18. `"Finding usability problems through heuristic evaluation" Nielsen 1992 OR 1994 "paper" specification prototype input DOI` (targeted fetch for [2])
19. `"User interface evaluation in the real world: a comparison of four techniques" Jeffries Miller Wharton Uyeda 1991 guidelines heuristic cognitive walkthrough consistency` (targeted fetch for [5])
20. `"design critique" HCI Blevis OR "Discussing Design" Connor Irizarry OR Buxton 2008 usability evaluation input rationale intent` (targeted fetch for [7])
21. `"2512.03568" "Synthetic Cognitive Walkthrough: Aligning Large Language Model's Performance with Human Cognitive Walkthrough" abstract method input results false positives` on `arxiv.org` (content fetch for [12])
22. `"2403.13139" "Generating Automatic Feedback on UI Mockups with Large Language Models" validity percentage precision GPT-4 JSON vision false positives` on `arxiv.org` (metrics fetch for [9])
23. `"2407.08850" "UICrit" results baseline GPT-4V Gemini human agreement percentage date` on `arxiv.org` (metrics fetch for [10])
24. `"Finding usability problems through heuristic evaluation" Nielsen 1992 "Banking" paper prototype specification 22% 41% 60% major minor problems` (metrics fetch for [2])
25. `"Ergonomic Criteria for the Evaluation of Human-Computer Interfaces" Bastien Scapin 1993 checklist heuristic evaluation comparison` (targeted fetch for [6])
26. `LLM usability evaluation "textual description" OR "text specification" user interface before prototype 2024 2025 2026` on `arxiv.org` (check for pure-prose specification evaluation benchmarks)

**Pages opened (budget count):** Direct HTTP fetches via `curl.exe` are
blocked by the environment's permission rules, so all openings were
performed as targeted grounded fetches via `search_web` (12 primary
sources opened and used [1–12], plus 5 secondary/duplicate sources
inspected and left out in *Opened and not used*; 17 sources inspected in
total, with 12 primary openings).

**What the disconfirming queries found:**
- `"heuristic evaluation unreliable evaluator effect"` found Hertzum and
  Jacobsen (2001) [8], confirming that pairwise agreement between human
  evaluators using the same method on the same interface is only 5% to
  65%.
- `"LLM usability evaluation false positives"` found Duan et al. (2024)
  [9, 10] and Guerino et al. (2025) [11], confirming that LLMs over-report
  and hallucinate usability problems on static inputs (~40% false
  positives in [9]; 86.9% invalid zero-shot comments in [10]; 21.2%
  overlap with human experts in [11]), while further targeted search on
  cognitive walkthroughs found Zhong et al. (2025) [12], showing that in
  step-by-step walkthroughs baseline LLMs instead under-report failure
  points (false negatives).

**Reason the run ended:** Both parts of the card's stop rule were met at
12 primary sources opened (within the 10–15 page budget): every route
named in the card (heuristic evaluation, cognitive walkthrough,
checklist/ergonomic review, consistency/standards inspection, design
critique, and 2024–2026 LLM evaluation studies) had a primary source,
and differently worded queries on pure-text pre-prototype LLM evaluation
returned no new empirical usability inspection studies.
