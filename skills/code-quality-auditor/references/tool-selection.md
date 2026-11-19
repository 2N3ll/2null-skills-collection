# Tool selection

Use installed project tooling first; inspect its configuration and scripts. Select tools for the actual language and version rather than installing every analyzer. Verify official documentation for flags and current compatibility.

| Stack | Existing checks and candidate tools |
|---|---|
| JavaScript / TypeScript | ESLint, Biome, TypeScript compiler, Knip for unused exports/files/dependencies |
| React / Next.js / Vue / Svelte | Framework checks, framework-aware lint rules, typechecks and configured build checks |
| Python | Ruff, Pyright or mypy, existing pytest suite, Vulture as heuristic unused-code input |
| Go | go vet, Staticcheck, existing tests |
| Rust | cargo check, Clippy, existing tests |
| C# / .NET | Roslyn analyzers, project build and tests |
| Java / Kotlin | Existing compiler checks, SpotBugs, PMD, Detekt where configured |

DeepScan (https://deepscan.io/docs/deepscan) is a JavaScript-focused static analysis product. This skill is inspired by its distinction between correctness and quality findings; it is not DeepScan, does not require a subscription, and does not claim equivalent coverage.

## Procedure
- Match the package manager and workspace. Read manifests and existing scripts; prefer the repository's pinned tools rather than downloading arbitrary latest versions.
- Use non-mutating modes. Avoid auto-fix, formatting writes, dependency upgrades, telemetry or source uploads unless authorized.
- Collect diagnostics with exact file/line/rule identifiers when available.
- Group overlapping diagnostics by underlying cause; distinguish compiler errors, linter warnings and heuristic findings.
- Inspect each meaningful result against source before recommending changes. A scanner's absence of findings does not prove correctness.
- If a recommended tool is unavailable, label it as a suggestion, not a completed check.
