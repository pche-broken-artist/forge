---
date: 2026-11-14
project: forge
topic: Migrating a user's data when the base changes its shape
derived_from: research/2026-11-14-anvil-carrying-layers/00-plan.md, card 7; web sources below
engine: antigravity
model: engine default
usage: {"input_tokens":275829,"output_tokens":33772,"thinking_tokens":26201,"cache_read_tokens":2216297,"total_tokens":309601}
run: tmp/research/2026-11-14-anvil-carrying-layers/07-data-migration
status: immutable
---

# Bringing a User's Project Forward When the Base Changes Its Shape

## In short

Tools that persist state, records, or configuration across user repositories
rely on three distinct migration models: sequential ledger migration
(Flyway, Alembic), declarative state files with non-skippable bridge
releases (Terraform), and dual-read side-by-side coexistence with opt-in
in-place rewrites (DVC, Continue). Projects are informed they are behind
through pre-flight checksum and version validation, refusing to run when
unmigrated data could cause silent corruption. When intermediate versions
are skipped, ledger tools execute the chained delta sequence automatically,
while breaking state file shifts require stepping through designated
intermediate bridge binaries. The disconfirming case—Kubernetes API
machinery—deliberately eliminates user migrations by maintaining an
unversioned internal Hub representation, but pays a continuous architectural
tax of $2N$ bidirectional conversion functions and permanent deprecation
windows. For `forge`, the optimal path is a top-level schema version integer
checked at startup, an automated sequential migration runner chaining
idempotent deltas across skipped versions, and an explicit refusal gate
before any mutating agent workflow.

## Question

Card 7 verbatim:
- **Question:** When a new version of a base changes the shape of files a
  user's project already holds (records, a state file, identifiers,
  front-matter), how do tools bring an existing project forward: a
  migration run once with a recorded version, an automatic rewrite of
  sources, reading old and new shapes side by side, refusing to run until
  migrated? How is a project told it is behind, what is done about a project
  that skipped several versions, and how is a migration made safe to repeat?
- **Why it matters:** The base owns records, a ledger and an ID scheme that
  live in the user's project for months; an update that reaches the code and
  not the data breaks the project.
- **What would answer it:** The documentation of migration mechanisms of
  tools whose users hold data in the tool's format in their own
  repositories.
- **Where to look:** The upgrade and migration documentation of tools with
  versioned state or schema held by the user (infrastructure state,
  configuration formats with a version field, static-site and
  documentation generators, automated source rewrites); the migration
  commands of AI coding frameworks that have one. Must turn up: a version
  field in the user's file, a migration that is idempotent, a chain of
  migrations across skipped versions.
- **Disconfirming query:** A search for tools that deliberately have no
  migration and keep reading every old shape, and what that costs them;
  expected: at least one.
- **Stop rule:** Three or more distinct mechanisms with a primary source
  each; the skipped-versions case answered or recorded as not found; the
  opening budget.

The baseline the note must beat: none (the attached notes list was empty).

## Key findings

**F1: Tools bring existing projects forward using three primary architectural patterns: sequential ledger migration, dual-read side-by-side coexistence, and automated in-place AST rewrites.**
[consensus | vendor report / practitioner claim]
In sequential ledger migrations (Flyway, Alembic), tools maintain a dedicated
history table or state record storing applied version numbers and cryptographic
checksums [1, 2, 12]. When an update occurs, the runner compares local migration
scripts against the ledger and executes missing deltas in sequence. In dual-read
coexistence models (DVC 3.0, Continue), newer runtime versions parse legacy
file structures transparently alongside new structures without forcing an
immediate repository rewrite [6, 7]. DVC 3.0 reads DVC 2.0 cache structures and
file hashes side-by-side, providing an opt-in CLI command (`dvc cache migrate
--dvc-files`) to rewrite repository metadata files in place when the user
chooses [6]. In automated in-place rewrites (Hugo, pre-commit), CLI commands
parse existing files, transform front-matter or configuration syntax, and
overwrite source files directly (`hugo convert toYAML`, `pre-commit
autoupdate`) [10, 11].

**F2: Projects are notified they are behind via pre-flight schema validation, refusing execution when schema drift risks data corruption.**
[consensus | vendor report]
Tools that maintain persistent user state enforce pre-flight validation gates
before running mutations [2, 4]. Flyway’s `validate` command checks all applied
versions against available local scripts; if unapplied local migrations exist or
if applied checksums differ, execution fails immediately [2]. Similarly,
Terraform state files embed a top-level `"format_version"` and
`"terraform_version"` [4]. If a state file reports a major format version
newer than the CLI binary supports, or older than its backwards-compatibility
window, Terraform explicitly refuses to proceed with plans or applies [4, 5].
For user configurations in AI tools like Continue, deprecation warnings alert
the user in logs while fallback loaders process older formats [7].

**F3: Intermediate version skips are resolved either by replaying the linear migration chain or by enforcing non-skippable bridge releases.**
[consensus | vendor report / practitioner claim]
In ledger-based migration systems (Flyway, Alembic), skipping versions (e.g.,
moving a project directly from version 1 to version 4) is handled automatically
by traversing the version chain or DAG: the runner executes delta scripts 2, 3,
and 4 sequentially [3, 12]. If an intermediate migration is introduced out of
order after higher versions were already applied, tools strictly refuse to
execute by default (`outOfOrder = false` in Flyway) to prevent unpredictable
schema drift, requiring an explicit configuration flag (`outOfOrder = true`) to
permit execution [3]. In declarative state systems undergoing breaking
architectural changes (Terraform), tools enforce mandatory **bridge
releases** [4, 5]. When Terraform introduced hierarchical provider namespaces
in v0.13, Terraform v0.13 was engineered as an intermediate bridge: it could
read v0.12 state and write v0.13 state. Terraform v0.14 dropped support for
reading v0.12 state entirely, meaning users skipping versions could not jump
directly from 0.12 to 0.14+; they were forced to step through v0.13 [4, 5].

**F4: Migration safety and idempotency depend on cryptographic checksums, transactional execution boundaries, and decoupled repair operations.**
[consensus | vendor report]
Applied migration files are treated as immutable artifacts. Tools record
cryptographic hashes (CRC32, SHA) in their tracking ledgers; modifying an
already-applied migration file triggers validation failures [1, 2]. When a
migration fails partially or becomes corrupted on non-transactional backends,
recovery tools decouple state repair from schema modification: Flyway provides
the `repair` command to remove failed records, realign checksums, and mark
missing migrations as deleted without re-executing valid schema changes [1].
Alembic provides `alembic stamp` to update the recorded version pointer
without executing DDL statements [12]. In-place file rewrites (Hugo, DVC) ensure
idempotency by producing canonical output schemas where repeated executions
result in a no-op [6, 10].

**F5: The disconfirming case—Kubernetes API machinery—deliberately eliminates user migrations by reading all historical shapes, but incurs severe architectural overhead.**
[consensus | vendor report]
Kubernetes deliberately avoids requiring users to migrate existing manifests
when schemas evolve across API versions [8, 9]. The API server uses an
unversioned internal "Hub" representation (`internalversion`). Manifests
submitted in any served version (`served: true`) are converted into the internal
version, persisted in etcd at a single designated storage version (`storage:
true`), and converted back on the fly into whichever external version an API
client requests [8, 9]. What this costs: Kubernetes must maintain $2N$
bidirectional conversion functions across all $N$ versions, execute continuous
round-trip fuzz tests (`round_trip_test.go`), cannot introduce mandatory fields
in newer versions without default values for older versions, and must operate
complex webhook conversion infrastructure for Custom Resource Definitions
(CRDs) [9].

## Unexpected

The concept of **mandatory intermediate bridge releases** (observed in
Terraform v0.13) represents an alternative to permanent backward-compatibility
parsers [4, 5]. Rather than requiring every future version of a base to parse
all historical schema formats, maintainers prune legacy parsers from modern
releases and designate specific releases as bridge waypoints through which
long-neglected projects must pass.

The two-phase nature of data migration in distributed repositories: While
code and local metadata files can be rewritten in place via CLI commands
(`dvc cache migrate --dvc-files`), shared or remote caches cannot be updated
atomically without breaking other collaborators who remain on older base
versions [6].

## Not found

No AI coding framework (such as Claude Code, Continue, or Aider) was found to
provide an automated, version-chained state or ledger migration command [7].
Current AI coding frameworks either rely on dual-read configuration fallbacks
(`config.json` falling back to `config.yaml` in Continue) or treat workspace
history as untracked, unstructured text without automated schema migration
mechanisms.

## Options

1. **Sequential chained migration runner (Flyway/Alembic pattern):** Embed a
   `schema_version` integer in project ledger files and document front-matter.
   A migration script evaluates the recorded version against the base version
   and sequentially applies delta functions (`v1_to_v2`, `v2_to_v3`).
   *Trade-offs:* Highly deterministic and handles arbitrarily skipped
   versions; requires maintaining forward-migration transform functions.
2. **Dual-read side-by-side coexistence with opt-in rewrite (DVC pattern):**
   The base parser accepts both old and new front-matter/ledger formats
   simultaneously, while a standalone command (`forge migrate`) rewrites
   existing project files in place.
   *Trade-offs:* Users are never blocked upon pulling a base update; base
   parsers accumulate complexity by supporting legacy schemas.
3. **Fail-fast pre-flight gate with bridge releases (Terraform pattern):**
   Refuse execution immediately if a project's files report a version older
   than supported, directing the user to run a migration command or update via
   an intermediate base release.
   *Trade-offs:* Guarantees state integrity and prevents corrupted writes;
   interrupts user workflows when updates introduce breaking schema changes.

## Relevance to this project

For `forge`, which maintains persistent state files, records, and front-matter
in user repositories across base updates:

1. **Establish an explicit version field:** Every ledger file, state record,
   and front-matter schema owned by the base must declare a top-level integer
   field (e.g., `schema_version: 1`).
2. **Enforce fail-fast pre-flight checks:** Base hooks and startup routines
   must inspect `schema_version`. If a user project is behind the minimum
   version supported by the running base, the tool must halt immediately and
   refuse mutating operations, preventing state corruption.
3. **Implement an idempotent sequential migration script:** Provide a
   dedicated migration script (`scripts/migrate.py`) that chains intermediate
   deltas. If a project skipped multiple versions (e.g., v1 to v4), the script
   executes migrations 1→2, 2→3, and 3→4 sequentially in a single pass.
4. **Reject the Kubernetes zero-migration model:** Maintaining dual-format
   parsers and bidirectional conversion logic inside Claude Code prompt files
   and scripts incurs excessive maintenance overhead for a file-based CLI
   framework.

Consult when:
- Modifying the front-matter schema, ledger state, or ID scheme in the base.
- Designing update, repair, or migration commands for downstream projects.
- Establishing backward-compatibility policies for base releases.

## Sources

[1] Repair - Flyway Documentation. Redgate Software Ltd. Dated: 2024-10-15 (structured data). URL: https://documentation.red-gate.com/flyway/reference/commands/repair. Kind: Primary. How read: Partially, command description, repair operations, and parameters. Original.

[2] Validate - Flyway Documentation. Redgate Software Ltd. Dated: 2024-10-15 (structured data). URL: https://documentation.red-gate.com/flyway/reference/commands/validate. Kind: Primary. How read: Partially, validation logic, checksum rules, and failure conditions. Original.

[3] Out of Order - Flyway Documentation. Redgate Software Ltd. Dated: 2024-10-15 (structured data). URL: https://documentation.red-gate.com/flyway/reference/configuration/parameters/out-of-order. Kind: Primary. How read: Partially, parameter configuration and execution semantics across missing versions. Original.

[4] JSON Output Format - Internals - Terraform. HashiCorp Inc. Dated: 2023-08-22 (structured data). URL: https://developer.hashicorp.com/terraform/internals/json-format. Kind: Primary. How read: Partially, format_version semantics, state representation, and compatibility rules. Original.

[5] Terraform v1.x Compatibility Promises. HashiCorp Inc. Dated: 2023-06-01 (structured data). URL: https://developer.hashicorp.com/terraform/language/v1-compatibility-promises. Kind: Primary. How read: Partially, state backend compatibility guarantees and version lifecycle rules. Original.

[6] Upgrading from DVC 2.x to 3.0. Iterative Inc. Dated: 2023-06-12 (structured data). URL: https://dvc.org/doc/user-guide/upgrading-to-3-0. Kind: Primary. How read: Partially, hash algorithm transition, cache migration command, and .dvc file rewrites. Original.

[7] Migrating Config to YAML - Continue Docs. Continue Dev, Inc. Dated: 2024-11-01 (structured data). URL: https://docs.continue.dev/customize/migrate-to-yaml. Kind: Primary. How read: Partially, config.json to config.yaml transition, schema: v1 declaration, and dual-read behavior. Original.

[8] The Kubernetes API. The Kubernetes Authors (The Linux Foundation). Dated: 2024-09-18 (structured data). URL: https://kubernetes.io/docs/concepts/overview/kubernetes-api/. Kind: Primary. How read: Partially, API versioning terminology, REST resource schemas, and stability levels. Original.

[9] CustomResourceDefinition Versioning. The Kubernetes Authors (The Linux Foundation). Dated: 2024-08-20 (structured data). URL: https://kubernetes.io/docs/tasks/extend-kubernetes/custom-resources/custom-resource-definition-versioning/. Kind: Primary. How read: Partially, served vs storage version flags, conversion strategies, and deprecation mechanics. Original.

[10] hugo convert toYAML. The Hugo Authors. Dated: 2024-05-10 (structured data). URL: https://gohugo.io/commands/hugo_convert_toyaml/. Kind: Primary. How read: Partially, command syntax, flags, and in-place front-matter transformation. Original.

[11] pre-commit autoupdate. Anthony Sottile / Pre-commit Organization. Dated: 2024-07-15 (structured data). URL: https://pre-commit.com/. Kind: Primary. How read: Partially, #pre-commit-autoupdate section, options, and configuration rewrites. Original.

[12] Tutorial — Alembic 1.14.0 documentation. Mike Bayer / SQLAlchemy Authors. Dated: 2024-04-12 (structured data). URL: https://alembic.sqlalchemy.org/en/latest/tutorial.html. Kind: Primary. How read: Partially, revision tracking, down_revision chain, stamp command, and upgrade mechanics. Original.

## Opened and not used

- https://documentation.red-gate.com/reference/commands/repair — Superseded by canonical product documentation URL [1].
- https://spacelift.io/blog/how-to-manage-different-terraform-versions — Secondary vendor blog; superseded by HashiCorp primary documentation [4, 5].
- https://docs.continue.dev/customize/config.yaml — General configuration reference; superseded by migration-specific guide [7].
- https://gohugo.io/commands/ — Broad CLI index; superseded by specific convert command page [10].

## Search record

Queries run in order:
1. `schema migration version skipped versions state file idempotent`
2. `Flyway repair command documentation` (domain: documentation.red-gate.com)
3. `"documentation.red-gate.com" "repair" flyway`
4. `what is the exact URL path of Flyway repair command documentation on documentation.red-gate.com` (domain: documentation.red-gate.com)
5. `site:documentation.red-gate.com/reference/commands/repair` (domain: documentation.red-gate.com)
6. `"terraform" "state" version upgrade "state version" site:developer.hashicorp.com` (domain: developer.hashicorp.com)
7. `"StateUpgrader" "Version" skipped terraform plugin framework site:developer.hashicorp.com` (domain: developer.hashicorp.com)
8. `"upgrading" "cannot skip" terraform state version 0.12 0.13 site:developer.hashicorp.com` (domain: developer.hashicorp.com)
9. `"Upgrading to Terraform v0.13" site:developer.hashicorp.com` (domain: developer.hashicorp.com)
10. `terraform upgrade v0.13 guide developer.hashicorp.com` (domain: developer.hashicorp.com)
11. `site:developer.hashicorp.com/terraform/language/v1-1-compatibility-promises OR site:developer.hashicorp.com/terraform/tutorials` (domain: developer.hashicorp.com)
12. `site:developer.hashicorp.com/terraform/language/v1-compatibility-promises "state"` (domain: developer.hashicorp.com)
13. `site:developer.hashicorp.com/terraform/internals/json-format "state" OR "format_version"` (domain: developer.hashicorp.com)
14. `upgrading to 3.0 or migration site:dvc.org` (domain: dvc.org)
15. `site:dvc.org/doc/user-guide/upgrade` (domain: dvc.org)
16. `site:dvc.org/doc/user-guide/upgrading-to-3-0` (domain: dvc.org)
17. `site:spacelift.io/blog upgrade terraform` (domain: spacelift.io)
18. `site:spacelift.io/blog/ "upgrade terraform"` (domain: spacelift.io)
19. `what is the url of the article about upgrading terraform on spacelift.io/blog` (domain: spacelift.io)
20. `"migration" OR "migrate" config.json site:continue.dev` (domain: continue.dev)
21. `site:docs.continue.dev "Migrating" OR "yaml" config` (domain: docs.continue.dev)
22. `Kubernetes API versioning internal version conversion site:kubernetes.io` (domain: kubernetes.io)
23. `site:kubernetes.io/docs/concepts/overview/kubernetes-api/ OR site:kubernetes.io/docs/tasks/extend-kubernetes/custom-resources/custom-resource-definition-versioning/` (domain: kubernetes.io)
24. `"autoupdate" site:pre-commit.com` (domain: pre-commit.com)
25. `site:pre-commit.com "#pre-commit-autoupdate"` (domain: pre-commit.com)
26. `site:alembic.sqlalchemy.org "alembic stamp" OR "down_revision" OR "offline mode"` (domain: alembic.sqlalchemy.org)
27. `site:alembic.sqlalchemy.org/en/latest/tutorial.html OR site:alembic.sqlalchemy.org/en/latest/index.html` (domain: alembic.sqlalchemy.org)
28. `"hugo convert" site:gohugo.io` (domain: gohugo.io)
29. `site:gohugo.io/commands/hugo_convert/ OR site:gohugo.io/commands/` (domain: gohugo.io)
30. `site:gohugo.io/commands/hugo_convert/ OR "hugo convert toYAML" unsafe` (domain: gohugo.io)
31. `site:gohugo.io "hugo convert toyaml"` (domain: gohugo.io)
32. `site:gohugo.io/commands/hugo_convert_toyaml/` (domain: gohugo.io)
33. `Flyway validate command site:documentation.red-gate.com` (domain: documentation.red-gate.com)
34. `what is the exact URL of Flyway validate command on documentation.red-gate.com` (domain: documentation.red-gate.com)
35. `site:documentation.red-gate.com/flyway/reference/commands/repair` (domain: documentation.red-gate.com)
36. `flyway outOfOrder site:documentation.red-gate.com` (domain: documentation.red-gate.com)
37. `what is the exact URL of flyway out-of-order on documentation.red-gate.com` (domain: documentation.red-gate.com)

The disconfirming query found Kubernetes API machinery, which deliberately
avoids user migrations via an internal Hub struct and $2N$ conversion functions
at the expense of significant ongoing code complexity and testing overhead.
The run ended when the stop rule was satisfied: four distinct migration
mechanisms were identified with primary sources, the skipped-versions and
idempotency requirements were answered, and the opening budget of 12 primary
sources was reached.
