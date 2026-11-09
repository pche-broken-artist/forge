---
project: forge
purpose: the picture of the forge's parts in four steps
audience: anyone the principal explains the plan of the forge to
version: 0.1
---

# Recipe — the picture of the forge's parts in four steps

## Inputs
- threads/THR.0850.md

## Instructions
One picture and its legend, nothing else: no introduction, no
commentary. The names and the four steps are the thread's; where
the thread and the Template differ, say so instead of choosing.
The diagram is pinned: a grid of equal boxes, three rows
(definition, framework, Anvil), the steps left to right, a box
holding a name only. A dashed outline marks a layer not yet
separated from its neighbour.

## Template
# From a monolith to a family of forges

```mermaid
block-beta
  columns 6
  h1["1 to 7.0"] h2["2 at 7.0"] h3["3 next"] h4["4 goal"]:3
  d1["definition<br/>Thought"] d2["definition<br/>Thought"] d3["definition<br/>Thought"] d4["definition<br/>Thought"] d5["definition<br/>Proof"] d6["definition<br/>Form"]
  f1["framework<br/>Thought"] f2["framework<br/>Thought"] f3["framework<br/>Thought"] f4["framework<br/>Thought"] f5["framework<br/>Proof"] f6["framework<br/>Form"]
  a1["Anvil"] a2["Anvil"] a3["Anvil"] a4["Anvil"]:3
  classDef head fill:none,stroke:none
  classDef shared stroke-dasharray: 5 5
  class h1,h2,h3,h4 head
  class d1,f1,a1,f2,a2 shared
```

| Term | Meaning |
|---|---|
| definition | the project in which a framework is designed by its own process |
| framework | the operating layer of one forge: what belongs to its field, built on Anvil |
| Anvil | the general base of every AI project: histories, the ledger, research, the mechanics of critique, challenge and check; from step 3 a plugin of Claude Code |
| Thought | Forge of Thought, the forging of thoughts: elicitation, the chain of artefacts, its critics, challengers and checks |
| Proof | Forge of Proof, tests: content not yet set |
| Form | Forge of Form, UX/UI and the web prototype: content not yet set |
| solid outline | a block of its own, its own repository |
| dashed outline | a layer inside one block, not yet separated |
