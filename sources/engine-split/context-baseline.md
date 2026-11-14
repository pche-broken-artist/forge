origin: the output of the Claude Code command `/context all`, pasted into the conversation; paths replaced by `<engine>` and `<config>` and the table of connected MCP servers left out before registration
date: 2026-11-14

## Context Usage

**Model:** claude-fable-5-2
**Tokens:** 504.6k / 1m (50%)

### Estimated usage by category

| Category | Tokens | Percentage |
|----------|--------|------------|
| System prompt | 3.1k | 0.3% |
| System tools | 22.1k | 2.2% |
| MCP server instructions | 717 | 0.1% |
| MCP tools (deferred) | 5k | 0.5% |
| System tools (deferred) | 26.2k | 2.6% |
| Custom agents | 1.7k | 0.2% |
| Memory files | 21.9k | 2.2% |
| Skills | 7.8k | 0.8% |
| Messages | 447.2k | 44.7% |
| Free space | 462.4k | 46.2% |
| Autocompact buffer | 33k | 3.3% |

### Custom Agents

| Agent Type | Source | Tokens |
|------------|--------|--------|
| check-single-source-of-truth | Project | 169 |
| check-user-stories | Project | 168 |
| docs-writer | Project | 126 |
| check-brd | Project | 119 |
| check-engine | Project | 118 |
| check-light | Project | 118 |
| check-boundary | Project | 109 |
| docs-planner | Project | 104 |
| challenger-business-analyst | Project | 101 |
| check-history | Project | 99 |
| and 5 more |  | 424 |

### Memory Files

| Type | Path | Tokens |
|------|------|--------|
| Project | <engine>/CLAUDE.md | 18.8k |
| Local | <engine>/CLAUDE.local.md | 65 |
| AutoMem | <config>/projects/<project>/memory/MEMORY.md | 3k |

### Skills

| Skill | Source | Tokens |
|-------|--------|--------|
| dataviz | Built-in | ~480 |
| code-review | Built-in | ~400 |
| claude-api | Built-in | ~390 |
| docs | claude.ai sync | ~340 |
| pptx | claude.ai sync | ~330 |
| google-workspace | claude.ai sync | ~330 |
| xlsx | claude.ai sync | ~320 |
| computer-use | claude.ai sync | ~320 |
| docx | claude.ai sync | ~320 |
| built-in-browser | claude.ai sync | ~290 |
| and 55 more |  | ~4.3k |
