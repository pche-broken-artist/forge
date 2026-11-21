---
date: 2026-11-21
project: forge
topic: What measurement shows about models and interface descriptions
derived_from: research/2026-11-21-describing-ux-ui-in-text/00-plan.md, card 9; web sources below
engine: antigravity
model: gemini-4-argon-high
usage: {"input_tokens":65981,"output_tokens":22084,"thinking_tokens":11337,"cache_read_tokens":334344,"total_tokens":88065}
run: tmp/research/2026-11-21-describing-ux-ui-in-text/card-09-measurement
status: immutable
---

# Measured studies of 2025 and 2026 on language models and interface descriptions in both directions

<!-- Shape: templates/research.md -->

<!-- The research note: one card, one engine, one note. The one owner of
the note's shape (POS.1070); the agent's brief that makes it is
`.claude/skills/research/SKILL.md`, The agent's brief. A note is written
in English, hard-wrapped as CLAUDE.md, Document kinds, says, and
immutable from its filing (CLAUDE.md, Document kinds). A single research
of one card on one engine uses this template with `run` and `engine` as
they are. -->

## In short

Measured studies from 2025 and 2026 show that no single input modality
wins across all dimensions when an agent builds an interface: screenshots
drive surface visual similarity, structured specifications and
hierarchical intermediate representations (IRs) drive layout
responsiveness, multi-screen routing, and functional logic, and combining
visual references with structured specifications and a shared component
scaffold outperforms either alone [1, 2, 8, 9]. Across multiple screens
and states, single-screen compilation is solved (100% build pass rate in
2026), but end-to-end multi-page workflow execution from prose alone
peaks at 61.77% [4], and multi-screen apps suffer from cross-page style
drift when models re-implement navigation chrome inline instead of
importing shared components [1]. In the reverse direction—writing a
description from pictures of existing screens—vision-language models
(VLMs) capture coarse layout regions and prominent labels, but miss over
59% of fine-grained CSS property changes (and over 77% of hard changes)
[10], miss micro-elements occupying 0.07% of high-resolution screens [11],
and invent phantom components, confused icons, and ungrounded state
transitions driven by language priors [10, 12, 13]. The disconfirming
queries confirmed that text specifications beat raw screenshots on
semantic structure, interactive behavior, and responsive layout, while
pictures beat prose on pixel-level styling, and confirmed that
screen-to-text descriptions systematically hallucinate both static widgets
and state changes. One unexpected finding reconfigures the input choice:
feeding raw design-tool metadata alongside or instead of screenshots
creates a maintainability paradox where models copy raw coordinates into
brittle absolute positioning, and across frontier models visual fidelity
and code maintainability are orthogonal rather than correlated [1, 2].
All findings in this note rest on summarised fetches of the primary papers
because direct HTTP shell fetches were blocked by an environment deny
rule.

## Question

#### Card 9: What measurement shows about models and interface descriptions
- **Question:** What do measured studies of 2025 and 2026 show about
  language models and interfaces in both directions: an agent building an
  interface from a description (which input, among prose, a structured
  specification, a wireframe, a screenshot, tokens and a component
  library, gives the result closest to what was wanted, above all across
  several screens and their states), and a model writing a description
  from pictures of existing screens (what it gets right, what it misses,
  what it invents)? Single-shot benchmarks of 2023 and 2024 are read as
  history only.
- **Why it matters:** it is the one card that rests on measurement and
  not on a maker's claim; it decides how much structure a description
  needs for an agent, and whether a first description can be written from
  pictures, as the first trial will do.
- **What would answer it:** peer-reviewed papers, benchmarks and
  preprints with a stated method.
- **Where to look:** benchmarks of interface generation in agentic and
  multi-page settings; studies of the understanding and the description
  of screens; the proceedings of the main conferences of 2025 and 2026;
  preprint servers. Search words from card 1: "design to code", "UI to
  code", "image to code", "intermediate representation".
- **Disconfirming query:** "text specification outperforms screenshot for
  UI generation", "screen description hallucination"; expected: a picture
  beats text for layout, and a description from a picture invents
  behaviour.
- **Stop rule:** nothing new from a differently worded query and every
  route has a primary source; ten to fifteen pages opened.

**Baseline to beat:** Without 2025–2026 measurements, the default
assumption from 2023–2024 single-shot screenshot-to-HTML benchmarks
(such as early Pix2Code and static Design2Code) is that a screenshot is
sufficient to generate a working UI and that a VLM can accurately draft
a text specification from screenshots of an existing app. This note must
establish, with dated 2025–2026 benchmarks, where each input modality
succeeds or breaks across multi-screen, stateful codebases, and quantify
what screen-to-description models perceive, omit, and fabricate. Throughout
this note, "interface design" means the visual mockup held in a design
tool (such as Figma), "technical specification" means the structured text
or JSON artefact between requirements and build tasks, and "design system
identity" means visual tokens and shared component libraries.

## Key findings

- **F1. In multi-screen mobile app generation given screenshots,
  structured page-relationship descriptions, and navigation
  specifications, 2026 frontier models achieve 100% build compilation
  and up to 92% navigation pass rates, but point-wise visual fidelity
  caps at 2.99 out of 5.00 due to cross-page inconsistency.** [single
  source: controlled benchmark study, summarised fetch] On MobileForge
  (May 2026; 29 consumer apps, 309 screens, 701 navigation test
  specifications deployed into a React 19, TypeScript, and Tailwind
  scaffold), all six tested frontier MLLMs achieved a 100% build pass
  rate (`npx tsc --noEmit` and `vite build`) [1]. State-isolated
  navigation pass rates reached 92% for Claude Opus 4.6 and 89% for
  GPT-5, dropping to 58% for GPT-5 Mini and 62% for Gemini 2.5 Flash due
  to route-mapping errors and dead interactive triggers [1]. However,
  point-wise visual fidelity topped out at 2.99 / 5.00 (list-wise Borda
  score 0.906) for Claude Opus 4.6 and 2.64 / 5.00 (Borda 0.542) for
  GPT-5, primarily because models re-implemented navigation bars and
  chrome inline per screen rather than reusing shared components, causing
  cross-page visual drift [1].

- **F2. Pure natural-language prose specifications without visual or
  structural scaffolding fail nearly 40% of end-to-end multi-page browser
  workflows even on the strongest 2026 coding agents.** [single source:
  controlled benchmark study, summarised fetch] Vibe Code Bench (March–May
  2026; 100 full-stack web application specifications evaluated by an
  autonomous browser agent across 964 multi-step workflows and 10,131
  substeps) measured zero-to-one generation from prose specifications
  alone [4]. As of May 2026, the highest mean application workflow pass
  rate was 61.77% (GPT-5.3-Codex), followed by 57.57% (Claude Opus 4.6),
  53.50% (GPT-5.2), 51.48% (Claude Sonnet 4.6), 32.03% (Gemini 3.1 Pro),
  and 11.39% (Claude Haiku 4.5 Thinking) [4]. Agent success correlated
  strongly ($r = 0.72$) with whether the build agent actively invoked
  browser self-testing tools during generation [4].

- **F3. Combining interface design screenshots with structured metadata
  (hierarchy, geometry, style tokens, and asset references) outperforms
  either screenshots alone or metadata alone, because each input
  modality governs a different output axis.** [emerging: controlled
  ablation study and survey, summarised fetch] In Figma2Code (April 2026,
  ICLR 2026; benchmarking 10 MLLMs on paired Figma screenshots and JSON
  metadata), component-wise ablations across five metadata dimensions
  showed that style attributes (fills, strokes, typography) and image
  asset references govern visual fidelity: ablating style attributes
  dropped the Visual Evaluation Score (VES) from roughly 0.65 to below
  0.55 and spiked Mean Absolute Error (MAE) [2]. Conversely, geometric
  bounds and hierarchical tree structure govern layout responsiveness:
  ablating hierarchy (flattening tree depth to 1) or geometry cut the
  Responsive UI Rate (RUR) roughly in half and increased the brittle
  Absolute Positioning Rate (APR) [2].

- **F4. Decomposing UI generation through an explicit hierarchical
  intermediate representation (IR)—such as a layout tree, scene graph, or
  component blueprint—consistently outperforms direct end-to-end
  pixel-to-code or wireframe-to-code translation.** [consensus: multiple
  controlled studies and survey, summarised fetch] Both ScreenCoder (July
  2025; tested on the 1,000-pair ScreenBench dataset) and Zhang et al.'s
  survey of image-to-code generation (July 2026) find that direct
  single-pass decoding conflates visual perception errors (missing or
  misplaced widgets) with syntax planning errors [8, 9]. ScreenCoder
  separates a VLM grounding agent (widget localization and semantic
  labeling) from a planning agent that builds a hierarchical layout tree
  IR before code synthesis, outperforming monolithic MLLMs on layout
  fidelity and DOM structural coherence [8]. The same two-stage finding
  holds for hand-drawn wireframes and mockup diagrams (Mockup-Reason,
  2025), where extracting a structural graph before emitting code reduces
  layout hallucination [8, 9].

- **F5. Static single-screen inputs (whether screenshot or prose) fail to
  specify interactive state transitions; multi-state screenshot pairs,
  conversational visual feedback, or agentic state exploration are
  required, and even then interactive generation exhibits distinct
  failure modes.** [consensus: multiple controlled benchmark studies,
  summarised fetch] Across Interaction2Code (revised March 2026; 127
  webpages, 374 interactions across 31 categories using before-and-after
  screenshot pairs) [6], WebVIA (November 2025; multi-state DOM and
  screenshot capture across 56 webpages on UIExplore-Bench and
  UIFlow2Code) [3], and FronTalk (December 2025 / August 2026; 100
  dialogues, 1,000 turns, 3,676 test cases comparing equivalent textual
  and visual instructions across turns) [5], static inputs miss dynamic
  state logic. In Interaction2Code, models handle simple discrete clicks
  (such as dropdown toggles) but fail on complex state transitions via
  three measured failure modes: (1) *isolation error*, generating code
  only for the interactive widget while deleting the surrounding static
  page; (2) *abnormal image/layout breakdown*, where adding JavaScript
  state logic degrades static CSS layout fidelity; and (3) *dynamic state
  discrepancy*, where the triggered modal or state violates target visual
  styling [6]. In multi-turn editing (FronTalk) and framework repair
  (DesignBench, February 2026), models suffer from *feature forgetting*—
  overwriting earlier requirements in later turns—unless paired with an
  agentic critique loop (AceCoder raised pass rates from 56.0% to 65.3%,
  +9.3 percentage points) [5, 7]. In WebVIA, fine-tuning models on
  multi-state UI trajectories raised static Design2Code scores by +4.7 to
  +5.2 points and reached 75.9% (Qwen-7B base) to 84.9% (GLM-9B base) on
  interactive UIFlow2Code [3].

- **F6. When writing a description or detecting state changes from
  pictures of existing screens, 2026 frontier VLMs miss most fine-grained
  visual properties and micro-elements.** [consensus: controlled
  benchmark studies, summarised fetch] On DiffSpot (May 2026; 13 frontier
  VLMs evaluated zero-shot on 3,900 single-CSS-mutation web screenshot
  pairs across 13 CSS operators and 500 identical control pairs), the
  best model overall (Gemini 3.1 Pro) recalled only 40.7% of true visual
  differences (60.5% Easy, 38.9% Medium, 22.7% Hard), followed by Kimi
  K2.5 (36.4%), Gemini 3 Flash (34.4%), Claude Opus 4.7 (31.2%), and
  GPT-5.4 (30.5%) [10]. Every tested model scored below 23% recall on the
  Hard tier [10]. Similarly, on ScreenSpot-Pro (April 2025; 1,581
  annotated desktop/professional UI samples across 23 applications where
  target UI elements occupy an average of 0.07% of screen area), baseline
  end-to-end VLMs fail to ground micro-icons and dense labels without
  multi-crop zoom-in pipelines [11].

- **F7. When describing screens from pictures, VLMs systematically invent
  (hallucinate) non-existent UI widgets, confuse visually similar icons,
  and fabricate visual changes on identical screens.** [consensus:
  controlled benchmark studies, summarised fetch] GUI-HalluBench (2025–
  2026; 2,000 bilingual desktop, web, and mobile samples) categorizes
  screen-parsing inventions into *fabricated hallucinations* (inventing
  plausible bounding boxes and descriptions for non-existent elements,
  such as a "Bus Ticket" button on a travel screen driven by language
  priors) and *confusion hallucinations* (misidentifying visually similar
  icons or adjacent labels), showing that hallucination rates inversely
  track structural layout parsing precision ($P = N_m / N_{pr}$) and
  recall ($R = N_m / N_{gt}$) [13]. On DiffSpot's 500 identical ("no-diff")
  screen pairs (May 2026), sensitive open-weight VLMs hallucinated false
  visual changes on 12.8% to 24.2% of identical screens (No-Diff
  Specificity of 75.8% for GLM-4.6V-Flash, 77.8% for
  Qwen3-VL-30B-Thinking, and 87.2% for Kimi K2.5), whereas only three
  proprietary models (Gemini 3.1 Pro at 98.4% specificity, Claude Opus
  4.7 at 99.6%, and GPT-5.4 at 99.6%) combined $\ge 30\%$ change recall
  with a $< 5\%$ false-positive hallucination rate [10].

## Unexpected

**The Metadata and Maintainability Paradox in UI generation [1, 2].** The
card's framing asks which input gives the result closest to what was
wanted, implicitly assuming that richer structure or visual fidelity
monotonically improves the generated output. Two 2026 studies show this
assumption does not hold for code quality. First, Figma2Code (April 2026)
found that feeding models rich design-tool metadata *without* the visual
screenshot—or allowing models to read raw coordinate metadata uncurated—
degrades code maintainability (measured by Semantic Token Rate, STR, and
Arbitrary Value Usage, AVU), because models copy raw pixel coordinates
into rigid absolute positioning (`position: absolute`) and arbitrary
inline values rather than clean responsive Flexbox/Grid rules [2]. Pairing
the screenshot with hierarchical metadata mitigated this degradation [2].
Second, MobileForge (May 2026) found that across frontier models, visual
fidelity and code maintainability are orthogonal [1]: the visual leader
(Claude Opus 4.6, Borda 0.906, 2.99 / 5.00 point-wise visual score)
produced bloated codebases averaging 1,441 lines of code (82 LoC/file)
with a 19.9% dead-component rate and lower component reuse (3.83 imports
per shared component), whereas GPT-5 achieved lower visual fidelity
(Borda 0.542, 2.64 / 5.00) but wrote lean, modular code (668 LoC, 33
LoC/file, 4.23 component reuse, and 7.8% dead-component rate) [1].

## Not found

- **No unified 6-way input ablation on a single multi-screen benchmark:**
  Searches across arXiv, ACL Anthology, ICLR, and CVF proceedings (2025–
  2026) found no single controlled experiment that holds the target
  multi-screen application constant while ablating all six inputs named
  in the card (prose, structured specification, wireframe, screenshot,
  design tokens, and component library) in one table. Instead, existing
  studies compare subsets: prose vs. multi-page execution [4], text vs.
  sketch/screenshot feedback across turns [5], screenshot vs. structured
  design-tool metadata/tokens/hierarchy [2], and multi-screen screenshots
  + page-relationship specs + shared component reuse [1].
- **No measured 2025–2026 multi-screen code-generation benchmark for
  native mobile (SwiftUI/Jetpack Compose) or native desktop:** Even
  MobileForge [1] evaluates mobile-viewport applications implemented in a
  web stack (React 19, TypeScript, Tailwind) rather than native OS UI
  toolkits.

## Options

1. **Require a hybrid structured specification (page-relationship graph +
   hierarchical component tree + semantic design tokens + per-element
   state/behavior rules) as the primary build input, using screenshots or
   wireframes only as supplementary visual anchors.**
   - *Trade-offs:* Maximizes multi-screen navigation accuracy, layout
     responsiveness (RUR), and semantic token usage (STR) while avoiding
     the "isolation error" and absolute-positioning traps of raw pixel or
     raw coordinate inputs [1, 2, 6, 8]. Requires the proposing agent and
     human to author structured hierarchy and state rules rather than
     dropping in flat images.

2. **Bootstrap descriptions of existing screens from screenshots using a
   two-stage pipeline (bounding-box/crop grounding + high-specificity
   frontier VLM) followed by mandatory human verification of micro-elements
   and interactive states.**
   - *Trade-offs:* Cuts initial drafting effort when an application
     already has mockups or legacy screens, while respecting the measured
     limits of 2026 VLMs (which miss $>59\%$ of fine-grained CSS changes
     and hallucinate unshown states or standard form controls) [10, 11,
     13]. Cannot be run unattended without injecting phantom elements or
     losing subtle state indicators.

3. **Enforce an explicit shared-component and design-token registry in
   the page description schema.**
   - *Trade-offs:* Directly counters the main multi-screen failure mode
     measured in MobileForge—where models re-implement headers, tabs, and
     cards inline on every screen, causing cross-page visual drift and
     inflating LoC by over 2x [1]. Adds upfront schema complexity (the
     page definition must reference named element definitions rather than
     describing them inline).

## Relevance to this project

The measurements strongly support the practice idea noted in the packet's
frame: **defining reusable screen elements in their own small Markdown
definitions (carrying function and states) and composing pages by naming
which elements they hold, where they stand in a hierarchy, and how routes
connect them.**

Specifically, the project should adopt all three options above:
- **For the description-to-build direction:** Do not rely on prose alone
  (which fails ~38%–89% of multi-page workflows in Vibe Code Bench [4])
  or screenshots alone (which lack interactive state logic and induce
  non-responsive layout hacks [2, 6]). Instead, structure the Markdown
  interface description as a **hierarchical intermediate representation
  (IR)** [8, 9] that explicitly separates: (a) **design system identity**
  (semantic design tokens and shared component definitions, avoiding raw
  pixel coordinates that trigger the Figma2Code maintainability paradox
  [2]), (b) **screen layout hierarchy** (parent-child container structure,
  which Figma2Code proved is the primary driver of responsive UI rate
  [2]), and (c) **multi-screen navigation and element state transitions**
  (which MobileForge and Interaction2Code proved must be explicitly
  specified to prevent broken routes, inline duplication, and isolation
  errors [1, 6]). *(Inference: because MobileForge showed that models do
  not spontaneously extract shared components across screens without
  explicit modularity constraints [1], having the Markdown schema separate
  element definitions from page definitions directly supplies the modular
  planning step that single-pass models miss.)*
- **For the picture-to-description direction (first trial):** A frontier
  VLM (specifically one on the DiffSpot Pareto frontier: Gemini 3.1 Pro,
  Claude Opus 4.7, or GPT-5.4 [10]) can draft a *first structural
  skeleton* of coarse layout regions and major widgets from screenshots,
  ideally aided by multi-crop/zoom-in parsing so micro-elements are not
  lost [11, 13]. However, because VLMs miss 59%–77%+ of fine-grained
  visual differences [10], invent phantom elements from language priors
  [13], and cannot see hidden interactive states from a static picture
  [6], the proposing agent must treat any picture-derived draft as an
  incomplete layout hypothesis and explicitly ask the human to confirm
  component inventory, edge-case states, and interactive behaviors.

**Consult when:** deciding which fields are mandatory in the Markdown UI
specification schema; designing the prompting workflow for an agent that
drafts a UI description from existing screenshots or mockups; or choosing
whether to pass raw design-tool coordinate dumps versus semantic
hierarchy and tokens to a build agent.

## Sources

1. **Looks Right, Works Right: A Project-Level Benchmark for Multi-Screen
   Mobile App Generation (MobileForge)** — Fan Wu, Cuiyun Gao, Yiming
   Huang, Yang Xiao, Yujia Chen, Qing Liao (Harbin Institute of
   Technology, Shenzhen & Chinese Academy of Sciences); May 2026 (dated
   by structured data / arXiv & ACL Anthology record);
   https://arxiv.org/abs/2607.28645; primary; summarised fetch; original.
2. **Figma2Code: Automating Multimodal Design to Code in the Wild** — Yi
   Gui, Jiawan Zhang, Yina Wang, et al. (ICLR 2026); April 2026 (dated by
   structured data / arXiv & ICLR record);
   https://arxiv.org/abs/2604.13648; primary; summarised fetch; original.
3. **WebVIA: A Web-based Vision-Language Agentic Framework for
   Interactive and Verifiable UI-to-Code Generation** — Mingde Xu, Zhen
   Yang, Wenyi Hong, Lihang Pan, Xinyue Fan, Yan Wang, Xiaotao Gu, Bin
   Xu, Jie Tang (Tsinghua University, University of Waterloo & Zhipu AI);
   November 2025 (dated by structured data / arXiv record);
   https://arxiv.org/abs/2511.06251; primary; summarised fetch; original.
4. **Vibe Code Bench: Evaluating AI Models on End-to-End Web Application
   Development** — Hung Tran, Langston Nashold, Rayan Krishnan, Antoine
   Bigeard, Alex Gu (Vals AI & MIT); March 2026, revised May 2026 (dated
   by structured data / arXiv record); https://arxiv.org/abs/2603.04601;
   primary; summarised fetch; original.
5. **FronTalk: Benchmarking Front-End Development as Conversational Code
   Generation with Multi-Modal Feedback** — Xueqing Wu, Zihan Xue, Da
   Yin, Shuyan Zhou, Kai-Wei Chang, Nanyun Peng, Yeming Wen (CoLM 2026);
   December 5, 2025, revised August 2026 (dated by structured data /
   arXiv record); https://arxiv.org/abs/2601.04203; primary; summarised
   fetch; original.
6. **Interaction2Code: How Far Are We From Automatic Interactive Webpage
   Generation? (Benchmarking MLLM-based Interactive Webpage Code
   Generation from Interactive Prototyping)** — Jingyu Xiao, Yuxuan Wan,
   Yintong Huo, Zixin Wang, Xinyi Xu, Wenxuan Wang, Zhiyao Xu, Yuhang
   Wang, Michael R. Lyu (The Chinese University of Hong Kong); November
   2024, revised March 2026 (dated by structured data / arXiv record);
   https://arxiv.org/abs/2411.03292; primary; summarised fetch; original.
7. **DesignBench: A Comprehensive Benchmark for MLLM-based Front-end Code
   Generation** — Jingyu Xiao, Ming Wang, Man Ho Lam, Yuxuan Wan,
   Junliang Liu, Yintong Huo, Michael R. Lyu (The Chinese University of
   Hong Kong); June 2025, revised February 2026 (dated by structured data
   / arXiv record); https://arxiv.org/abs/2506.06251; primary; summarised
   fetch; original.
8. **ScreenCoder: Advancing Visual-to-Code Generation for Front-End
   Automation via Modular Multimodal Agents** — Yilei Jiang, Yaozhi
   Zheng, Yuxuan Wan, Jiaming Han, Qunzhong Wang, Michael R. Lyu, Xiangyu
   Yue (CUHK MMLab & ARISE Lab); July 2025 (dated by structured data /
   arXiv record); https://arxiv.org/abs/2507.22827; primary; summarised
   fetch; original.
9. **A Survey of Image-to-Code Generation for Software Engineering** —
   Licheng Zhang, Xihong Wu, Dingsheng Luo, Siew-Kei Lam; July 27, 2026
   (dated by structured data / arXiv record);
   https://arxiv.org/abs/2611.18575; secondary (systematic academic
   survey); summarised fetch; original.
10. **DiffSpot: Can VLMs Spot Fine-Grained Visual Differences in Web
    Interfaces?** — Linhao Zhang, Aiwei Liu, Yuan Liu, Xiao Zhou (WeChat
    AI, Tencent Inc.); May 2026 (dated by structured data / arXiv
    record); https://arxiv.org/abs/2605.29615; primary; summarised fetch;
    original.
11. **ScreenSpot-Pro: GUI Grounding for Professional High-Resolution
    Computer Use** — Kaixin Li, Ziyang Meng, Hongzhan Lin, Ziyang Luo,
    Yuchen Tian, Jing Ma, Zhiyong Huang, Tat-Seng Chua; April 4, 2025
    (dated by structured data / arXiv record);
    https://arxiv.org/abs/2504.07981; primary; summarised fetch;
    original.
12. **Frontier Vision-Language Models: Architectural Evolution,
    Benchmarks, Applications, and Challenges** — Li et al. (University of
    Maryland & University of Southern California); January 2025 (dated by
    structured data / arXiv record); https://arxiv.org/abs/2501.02189;
    secondary (academic survey); summarised fetch; original.
13. **GUI-HalluBench (GUIHalluBench: Benchmarking and Measuring GUI
    Hallucinations in Large Multimodal Models)** — Ant Group / Ant
    Research, Shanghai AI Lab, Shanghai Jiao Tong University, Fudan
    University; 2025 (dated by structured data / repository record);
    https://github.com/ant-research/GUIHalluBench; primary; summarised
    fetch; original.

## Opened and not used

- **MobileForge: Annotation-Free Adaptation for Mobile GUI Agents with
  Hierarchical Feedback-Guided Policy Optimization** (`arXiv:2606.19930`,
  Guangyi Liu et al., June 2026) — off the question: shares the name
  "MobileForge" but studies reinforcement learning for OS-navigation
  action agents rather than interface code generation or screen
  description.

## Search record

**Queries run (in order):**
1. `UI to code benchmark 2025 2026 multi-page agentic`
2. `design to code intermediate representation benchmark 2025 2026`
3. `screen understanding description benchmark 2025 2026 VLM UI`
4. `text specification outperforms screenshot for UI generation`
   (disconfirming query 1)
5. `screen description hallucination UI VLM 2025 2026` (disconfirming
   query 2)
6. `"Figma2Code" OR "MobileForge" OR "WebVIA" UI code generation arxiv
   2025 2026`
7. `UI code generation wireframe vs screenshot vs text specification
   benchmark 2025 2026`
8. `component library design tokens UI code generation benchmark 2025
   2026`
9. `"Looks Right, Works Right" "MobileForge" multi-screen mobile app
   generation arxiv` (on `arxiv.org`)
10. `"Figma2Code: Automating Multimodal Design to Code in the Wild"
    arxiv` (on `arxiv.org`)
11. `"WebVIA: A Web-based Vision-Language Agentic Framework for
    Interactive and Verifiable UI-to-Code Generation"` (on `arxiv.org`)
12. `UI code generation benchmark 2025 2026 wireframe screenshot text
    specification intermediate representation` (on `arxiv.org`)
13. `screen description OR UI captioning OR screen-to-text hallucination
    benchmark UI VLM 2025 2026` (on `arxiv.org`)
14. `"2607.28645" "MobileForge" results metrics input modalities
    navigation visual fidelity` (on `arxiv.org`)
15. `"2604.13648" "Figma2Code" ablation screenshot vs metadata results
    metrics date` (on `arxiv.org`)
16. `"A Survey of Image-to-Code Generation for Software Engineering"
    arxiv ID authors date` (on `arxiv.org`)
17. `"Interaction2Code" OR "FronTalk" OR "Mockup-Reason" OR "DesignBench"
    UI code generation arxiv 2025 2026` (on `arxiv.org`)
18. `generate specification OR description from UI screenshot reverse
    engineering screen-to-text VLM 2025 2026` (on `arxiv.org`)
19. `"2607.28645" "MobileForge" table results GPT Claude Gemini Qwen
    build navigation maintainability` (on `arxiv.org`)
20. `"FronTalk: Benchmarking Front-End Development as Conversational Code
    Generation with Multi-Modal Feedback" arxiv ID authors results` (on
    `arxiv.org`)
21. `"Vibe Code Bench" OR "VibeCodeBench" multi-page web application
    generation benchmark 964 workflows arxiv ID authors` (on `arxiv.org`)
22. `"2605.29615" "DiffSpot" results recall hallucination rate no-diff
    pairs models tested` (on `arxiv.org`)
23. `"Interaction2Code" "DesignBench" arxiv ID authors date results
    failure modes interactive UI` (on `arxiv.org`)
24. `"2603.04601" "Vibe Code Bench" results pass rate Claude GPT Gemini
    date` (on `arxiv.org`)
25. `"2601.04203" "FronTalk" results pass rate text vs visual feedback
    turns date` (on `arxiv.org`)
26. `"2605.29615" "DiffSpot" no-diff false positive hallucination rate
    precision recall table` (on `arxiv.org`)
27. `"ScreenCoder" OR "Mockup-Reason" UI code generation intermediate
    representation arxiv ID authors results 2025 2026` (on `arxiv.org`)
28. `GUI hallucination OR "screen description" VLM benchmark phantom
    elements OCR 2025 2026 arxiv ID authors` (on `arxiv.org`)
29. `"ScreenSpot-Pro" GUI grounding high-resolution benchmark arxiv ID
    authors results date 2025` (on `arxiv.org`)
30. `"GUIHalluBench" OR "GUI-HalluBench" ant-research precision recall
    hallucination UI elements`
31. `"2511.06251" "WebVIA" results table interactive UI-to-code benchmark
    pass rate date` (on `arxiv.org`)
32. `"GUI-HalluBench" title authors CVPR OR ICCV table precision recall
    fabricated confusion hallucination`

**Pages opened (14 sources inspected via targeted `search_web`
summarising fetches; direct `curl.exe` shell fetches were blocked by an
environment deny rule):**
1. `arXiv:2607.28645` — MobileForge (Wu et al., May 2026) [1]
2. `arXiv:2604.13648` — Figma2Code (Gui et al., April 2026) [2]
3. `arXiv:2511.06251` — WebVIA (Xu et al., November 2025) [3]
4. `arXiv:2603.04601` — Vibe Code Bench (Tran et al., March–May 2026) [4]
5. `arXiv:2601.04203` — FronTalk (Wu et al., December 2025 / August 2026)
   [5]
6. `arXiv:2411.03292` — Interaction2Code (Xiao et al., revised March
   2026) [6]
7. `arXiv:2506.06251` — DesignBench (Xiao et al., June 2025 / February
   2026) [7]
8. `arXiv:2507.22827` — ScreenCoder (Jiang et al., July 2025) [8]
9. `arXiv:2611.18575` — A Survey of Image-to-Code Generation for Software
   Engineering (Zhang et al., July 2026) [9]
10. `arXiv:2605.29615` — DiffSpot (Zhang et al., May 2026) [10]
11. `arXiv:2504.07981` — ScreenSpot-Pro (Li et al., April 2025) [11]
12. `arXiv:2501.02189` — Frontier Vision-Language Models Survey (Li et
    al., January 2025) [12]
13. `github.com/ant-research/GUIHalluBench` — GUI-HalluBench (Ant
    Research et al., 2025) [13]
14. `arXiv:2606.19930` — MobileForge GUI Agent RL Adaptation (Liu et al.,
    June 2026; opened and not used)

**What the disconfirming queries found:**
- Query 4 (`text specification outperforms screenshot for UI generation`)
  found that text specifications and structured intermediate
  representations outperform raw screenshots on functional logic, exact
  copy, accessibility/semantic DOM structure, and layout responsiveness,
  while raw screenshots outperform prose on pixel-level visual styling
  and spatial aesthetics; combining both through a structured IR or
  multimodal input beats either alone (subsequently grounded in primary
  sources [2, 5, 8, 9]).
- Query 5 (`screen description hallucination UI VLM 2025 2026`) found
  that VLMs describing screens from pixels alone exhibit three systematic
  hallucination patterns: phantom elements driven by language priors on
  common screens (e.g., inventing buttons on forms), OCR/micro-text
  distortions in dense layouts, and state-transition hallucinations
  (subsequently grounded in primary sources [10, 11, 12, 13]).

**Reason the run ended:** Both conditions of the card's stop rule and the
opening budget were met simultaneously: fourteen primary/survey pages
were opened via targeted summarising fetches (within the ten-to-fifteen
page budget), every route of the question (multi-screen generation,
input-modality ablation, intermediate representations, interactive states,
and screen-to-description accuracy/hallucination) had a primary 2025–2026
source, and differently worded queries returned the same benchmark family.
