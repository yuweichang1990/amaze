# Round 0 – Global Coarse Pass (Default L2 / depth=2)

**Goal**: Fast static scan using symbol index + call hierarchy to obtain **system outline** and **major modules**. Produce a report that enables choosing R1 focus modules.

## Expected Inputs
- `repoPath`: `.` (default)
- *(Optional)* DeveloperContext: system purpose, known entrypoints, language/framework hints, known risks
- Suggested params: `level=2`, `depth=2`, `exclude="node_modules/**,dist/**,build/**,.git/**,vendor/**"`, `fileLimit=8000`, `timebox="structure=10m,api=10m,vcs=10m"`, `runTests=false`

## Quick Analysis Tip (for Your Agent)
If the codebase has many auto-detected frameworks (package.json, go.mod, pom.xml, etc.), prioritize analysis of those technologies to understand system capabilities and boundaries.

## Analysis Tools (use appropriate tools for the language/framework)
**Primary approach - Static analysis with simple tools:**
- **File structure analysis**: Use `find`, `ls`, `tree` to understand directory organization
- **Text search**: Use `grep`, `ripgrep`, or `ag` to find patterns, imports, function definitions
- **Symbol extraction**: Use language-agnostic tools like `ctags` or `universal-ctags`
- **Git history**: Use `git log`, `git blame` to identify frequently modified files

**Language-specific tools (optional, when needed):**
- **Go**: `go list`, `go doc`, or simple grep for `func` definitions
- **JavaScript/TypeScript**: grep for `function`, `class`, `export`, or use `jq` for package.json
- **Python**: grep for `def`, `class`, or basic ast parsing
- **Java**: grep for `public class`, `@Controller`, `@Service`

**Advanced tools (optional):**
- VS Code LSP features if available: call hierarchy, symbol providers
- Language servers: tsserver, gopls, pyright (if already configured)

## Tasks & Checklist (R0)
1. **Map the System Structure**
   - Create an overview of all code elements (functions, classes, files); identify the programming languages and frameworks used (look for `go.mod`, `package.json`, etc.).
   - Find the **starting points** of the system: main functions, server startup code, command-line entry points, background job schedulers, or container startup commands.
   - **Explore connections**: For each starting point, trace 2 levels deep - what calls it (incoming connections) and what it calls (outgoing connections). Mark any functions that many parts of the system depend on.
   - *(Optional)* Check recent code changes to see which files have been modified most frequently.
2. **Identify High-Priority Modules**
   - **Focus on the most important parts**: modules that are heavily used by other code, frequently called, or handle critical external connections (web APIs, databases, message queues).
   - Create a **priority reading list**: which modules developers should examine first vs. can skim quickly.
3. **Understand System Behavior**
   - Trace how data flows through the system; find how error messages or UI text connect to code.
   - Suggest simple tests to confirm understanding (describe what each main entry point should do, without running tests).
4. **Identify Structural Challenges** (Legacy Code Analysis)
   - Spot **problematic patterns**: over-reliance on singletons, shared global data, tightly connected components, complex inheritance hierarchies
   - Mark **frequently changed areas**: use version control history to identify files that break often when modified
   - Evaluate **code interconnectedness**: look for circular dependencies between modules, overly large components ("god objects"), and tightly coupled systems that make changes risky
5. **Notes & Sketches**
   - Describe **L2 structure** (containers/modules/dataflow) in text; mark entrypoints and external deps.
6. **Process**
   - Respect timeboxes; on overflow, **downgrade** scope and record in `assumptions.md`.

## Expected Outputs
- `specifications/R0/L2/architecture_overview.md` — entrypoints, major modules, external deps, shallow dataflow
- `specifications/R0/L2/functional.md` — feature list (coarse), each with trigger/behavior/output (brief)
- `specifications/R0/L2/nonfunctional.md` — initial NFR hypotheses (latency/throughput/security/reliability/ops)
- `specifications/R0/tasks.generated_from_code.md` — actionable seeds for R1 (what to deepen)
- `specifications/R0/assumptions.md` — limits, unknowns, candidate focus modules **with reasons**
- `specifications/R0/checkpoint.json` — index summary (languages, entrypoints, modules, hotspots, limits)
