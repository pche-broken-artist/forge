# The ways the base could reach a layer, scored

Scored 2026-11-14. Ten measures, each from 1 to 5; Function, Update
and Context count three times, Cut twice, the rest once; the most is
85. The rules of scoring: `work/ways-scoring.spec.md`. What each way
is: `00-brief-engine-split.md`.

| Way | Function | Update | Context | Cut | Dev | Own | Version | First day | Migration | Changes | Sum |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 The whole kept, the base released apart | 5 | 5 | 4 | 3 | 5 | 3 | 3 | 4 | 4 | 4 | 71 |
| 2 One repository, rules of a kind on demand | 4 | 5 | 4 | 3 | 5 | 3 | 3 | 4 | 4 | 4 | 68 |
| 3 One repository, one CLAUDE.md | 5 | 5 | 1 | 5 | 5 | 3 | 3 | 4 | 4 | 4 | 66 |
| 4 Plugin for the executables, text in the tree | 3 | 3 | 4 | 2 | 3 | 5 | 4 | 3 | 3 | 2 | 54 |
| 5 The base released as a plugin | 2 | 3 | 4 | 2 | 4 | 5 | 4 | 3 | 3 | 2 | 52 |
| 6 Two repositories and an import | 2 | 4 | 4 | 2 | 4 | 4 | 2 | 1 | 3 | 3 | 51 |
| 7 The base a package | 2 | 3 | 4 | 2 | 2 | 4 | 3 | 3 | 3 | 3 | 49 |
| 8 A plugin alone | 1 | 2 | 4 | 2 | 3 | 5 | 4 | 3 | 3 | 1 | 44 |
| 9 User-level configuration | 3 | 2 | 2 | 2 | 3 | 2 | 2 | 3 | 2 | 3 | 40 |

1. **The whole kept, the base released apart by a script.** The forge stays one repository in which everything is developed.
2. **One repository, the rules of a kind loaded only in its projects.** The root CLAUDE.md carries the base alone.
3. **One repository, everything in one CLAUDE.md.** As today, a project that is not the forge a further kind of project.
4. **A plugin for the executable parts, the rule text in the project's tree.** An update writes into no file a user or a layer owns.
5. **The base released in the form of a plugin.** Claude Code checks the version a layer needs.
6. **Two repositories side by side joined by an import.** The layer's CLAUDE.md imports the base's from the folder beside it.
7. **The base a package, each layer a repository.** The cleanest picture.
8. **A plugin alone.** The user's repository stays clean.
9. **User-level configuration.** No dialog.
