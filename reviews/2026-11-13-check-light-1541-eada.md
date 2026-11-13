---
date: 2026-11-13
project: forge
check: light
target: projects/forge
reviewer: check light (scripts/forge-check.py)
---

# Check (light) — projects/forge — 2026-11-13

1 finding

## Findings

### FND.4750 — low — 22 history companions carry the skeleton's comment as it stood before the current `templates/history.md`
- **Where:** `00-brief-brd.history.md:8`; `00-brief-collaboration.history.md:8`; `00-brief-documentation.history.md:8`; `00-brief-elicitation.history.md:8`; `00-brief-next-gen.history.md:8`; `00-brief-pptx-gitignore.history.md:8`; `00-brief-public-engine.history.md:8`; `00-brief-research.history.md:8`; `00-brief-tests.history.md:8`; `00-brief-user-stories.history.md:8`; `10-intent.history.md:8`; `40-solution-design.history.md:8`; `recipes/ba-intro.history.md:8`; `recipes/ceo-pitch.history.md:8`; `recipes/contributing.history.md:8`; `recipes/cto-pitch.history.md:8`; `recipes/executive-pitch.history.md:8`; `recipes/forge-evolution.history.md:8`; `recipes/readme-project.history.md:8`; `recipes/readme.history.md:8`; `recipes/release-notes.history.md:8`; `work/collaboration-cutover.spec.history.md:8`
- **Rule:** CLAUDE.md, Templates; `templates/history.md`, the comment
- **Fix:** immediate fix: the template's comment, as it stands on disk, in each

## Facts
- The script printed four more findings, each settled before and not raised: `work/collaboration-cutover.md:45` cites TBC.0090, settled by FND.2380 (resolved); the header of `00-brief.md`, the placeholder accepted under DEC.0010; the Verdict word of DEC.0430 at `decisions.md:760`, FND.4310 rejected by DEC.0480; the seven `closed` records of a thread that carry a `Was`, FND.4730 rejected by DEC.0500.
