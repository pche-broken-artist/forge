---
bundle: engine-split
project: forge
date: 2026-11-14
origin: measurements and outputs of checks made in sessions of the forge while the split into a base and layers is worked (brief `engine-split`)
---

# Index — bundle `engine-split`

<!-- Catalogue of one bundle (sources/<slug>/): the rules are
CLAUDE.md's (Document chain, External inputs). This skeleton is the one owner of the
bundle index (POS.1070): the header and the opening paragraph are its
own, the per-file entry is the sources entry of templates/index.md,
cited and not copied. The opening paragraph says whether the bundle
arrived whole or grows (POS.0180). -->

Material for the split of the forge into a base and layers (brief
`engine-split`): measurements and outputs of checks that will be
repeated and compared as the work goes on. A growing bundle: a new
measurement is added as its own file and entry when the principal
ingests it, each file immutable from its registration (POS.0180).

### `context-baseline.md`
- **What:** the output of the Claude Code command `/context all` in a session of the engine on 2026-11-14: tokens by category, the memory files with CLAUDE.md at 18.8k, the skill listing at 7.8k for 65 skills, the custom agents at 1.7k. Paths replaced by placeholders and the table of connected MCP servers left out before registration.
- **Origin:** Claude Code, `/context all`, pasted into the conversation by the principal.
- **Date:** 2026-11-14, from the content
- **Form:** text
- **Role:** the baseline before the rebuild of CLAUDE.md: the figures against which the size of CLAUDE.md, of the skill listing and of the agents is compared after it.
- **Use for:** what the always-loaded context of the forge cost before the rebuild.

### `doctor-baseline.md`
- **What:** the report of the Claude Code command `/doctor`, run read-only on 2026-11-14: the health of the installation, what costs context, the findings check by check, what `/usage` flagged for the last seven days, an estimate of CLAUDE.md section by section (about 235 of 920 lines to stay always loaded), and the usage counters of the 32 skills and of the agents over 50 sessions. Nothing was applied.
- **Origin:** Claude Code, `/doctor`, run in the session by Claude from local data.
- **Date:** 2026-11-14, from the content
- **Form:** text
- **Role:** the baseline before the rebuild of CLAUDE.md: the state of the configuration, the use of the skills and what the context cost.
- **Use for:** which skills are used and how often, the section-by-section estimate of CLAUDE.md, the timings of the hooks.

### `prompt-audit-baseline.md`
- **What:** the report of the Claude Code command `/doctor prompt-audit` over the 60 instruction files of the engine on 2026-11-14: no dated prompt text, three places where an instruction contradicts the repository (two in the research skill, one in the forge skill), a model name written into the setup skill, two skill descriptions too short to route by, and the proposed diff, not applied.
- **Origin:** Claude Code, `/doctor prompt-audit`, run in the session by Claude through the bundled prompt-audit guide.
- **Date:** 2026-11-14, from the content
- **Form:** text
- **Role:** the baseline before the rebuild of CLAUDE.md: the findings in the instruction files, with the proposed diff.
- **Use for:** what the audit found before the rebuild, to compare with the same audit after it; the five proposed edits.

### `claude-md-improver-baseline.md`
- **What:** the quality report of the skill `claude-md-improver` of Anthropic's plugin `claude-md-management` (1.0.0) on the engine's CLAUDE.md on 2026-11-14, run as an audit only: 82/100, grade B, criterion by criterion (commands 18/20, architecture 20/20, non-obvious patterns 13/15, conciseness 5/15, currency 14/15, actionability 12/15), with a note that the rubric rewards the map of the repository and the table of commands the rebuild means to take out. The scores were given by Claude applying the plugin's rubric.
- **Origin:** Claude Code, the plugin `claude-md-management` from Anthropic's official marketplace, its skill run in the session by Claude.
- **Date:** 2026-11-14, from the content
- **Form:** text
- **Role:** the baseline before the rebuild of CLAUDE.md: the score of CLAUDE.md by the rubric of Anthropic's claude-md-management plugin, criterion by criterion.
- **Use for:** the breakdown by criterion to compare with the same rubric after the rebuild; never the sum alone.

