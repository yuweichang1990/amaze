# Round 1 – Focused Deepening (L2 + L3 / depth=3–4)

**Goal**: Select 1–3 **focus modules** and deepen in/out call chains; capture data flows, error paths, state machines, and type contracts. **Static-first**, allow **minimal smoke** only with sandbox or `--run-tests`.

## Expected Inputs
- `repoPath`: `.`
- `focus`: `"moduleA,moduleB"` (from R0 suggestions)
- Params: `level=2,3`, `depth=3–4`, `resume="specifications/R0/checkpoint.json"`, optional `runTests`
- Resource controls: `exclude`, `fileLimit`, `timebox`

## VS Code / LSP Integration
- Use **Call Hierarchy** extensively on the public entry of each focus module.
- Use **References** to detect inbound dependencies and fan-in hubs.
- Use **Definition** for contracts (interfaces/types) and **DocumentSymbol** to map files.

## Tasks & Checklist (R1)
1. **Choose What to Examine Closely**
   - Confirm the public interface for each chosen module (the functions/classes other code can use).
   - **Follow the data path deeper**: Trace 3-4 levels in both directions from the public interface - what leads to these functions being called, and what they call in turn. Capture data structures, how state changes, error handling, and retry logic.
2. **Study the Focus Modules in Detail**
   - Build **flow diagrams**: show the sequence of function calls with what each step is responsible for and what conditions/errors can occur.
   - If the code is object-oriented: create **UML class/interface diagrams** showing inheritance hierarchies, interface implementations, abstract classes, factory patterns, dependency relationships, and polymorphism usage within focus modules.
   - If safe to run simple tests: execute one basic successful scenario per module to confirm the flow works and returns expected data types.
3. **Document How to Interact**
   - Standardize the external interface descriptions: URL endpoints, command-line arguments, event formats, and possible error responses for focus modules.
   - Document **data exchange protocols**: identify OpenAPI/Swagger specs, Protocol Buffers schemas, GraphQL schemas, message formats, and data serialization methods used for external communication.
   - Performance notes: identify timeout settings, connection limits, batch sizes, caching, and potential slowdown points.
4. **Extract Business Logic and Rules** (Domain Understanding)
   - Analyze **business rules in code**: extract validation logic, business constraints, and domain invariants embedded in conditional statements and error handling.
   - Identify **domain terminology**: document bounded contexts, ubiquitous language, and business concept mappings from naming patterns and comments.
   - Infer **user personas and behaviors**: map out implied user workflows, decision points, and business process patterns from code flow and data structures.
5. **Understand How Changes Are Made** (Legacy Code Analysis)
   - Study **feature addition patterns**: whether the code uses wrapper classes, plugins, inheritance extension, or object composition to add new functionality
   - Find **common workarounds**: how the team typically patches problems (overriding settings, conditional code branches, event hooks)
   - Track **modification patterns**: how often and what types of changes (bug fixes, new features, technical improvements) these modules undergo
6. **Review Recent Development History**
   - Examine recent code changes for these modules; classify each change (bug fix, feature addition, technical improvement).
7. **Notes, Diagrams & Diff**
   - Update L2 description; add L3: `code-map.md`, `callchains.md`, `types.md`.
   - Generate `diff_R1_vs_R0.md` (additions/changes, risks).

## Intermediate Progress Checkpoint (if Analysis Takes >5 minutes)
When R1 analysis time exceeds 5 minutes, output a brief summary:
- **Key discoveries so far**: Most important findings about the focus modules
- **Current confidence**: High/Medium/Low for critical findings
- **Estimated completion**: How much more work remains

This helps track progress for long-running analyses without losing track of progress.

## Analysis Quality Assurance (All Rounds)
- **Mark confidence levels**: Label each finding with evidence-based confidence (high/medium/low) indicating how certain the analysis is
- **Track key assumptions**: Explicitly list assumptions that would invalidate current conclusions if proven false
- **Prioritize next investigations**: Suggest what to examine next if time/resources allow

## Expected Outputs
- `specifications/R1/L2/architecture_overview.md` (delta)
- `specifications/R1/L2/functional.md` (focus details)
- `specifications/R1/L2/nonfunctional.md` (focus-specific NFRs)
- `specifications/R1/L3/code-map.md`
- `specifications/R1/L3/callchains.md` (1–3 key paths per focus)
- `specifications/R1/L3/types.md` (key types/fields/constraints)
- `specifications/diff_R1_vs_R0.md`
- `specifications/R1/assumptions.md`
- `specifications/R1/checkpoint.json`
