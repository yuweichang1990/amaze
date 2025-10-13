# Round 2 – Convergence (L0–L3 cross-check)

**Goal**: Converge R0/R1 into **deliverable specs** where functional, non-functional, and architecture are mutually consistent. If sandbox or `--run-tests` is enabled, run **minimal smoke** for key paths.

## Expected Inputs
- `repoPath`: `.`
- Params: `level=0,1,2,3`, `resume="specifications/R1/checkpoint.json"`, optional `runTests`, `timebox` (e.g., add `tests=5m`)

## VS Code / LSP Integration
- Use Call Hierarchy and References to **validate** that each functional endpoint/command has a code counterpart.
- Validate NFR claims using configuration/timeouts/pools/logging code evidence.

## Tasks & Checklist (R2)
1. **Verify Everything Connects**
   - **Check feature-to-code alignment**: confirm every documented API endpoint, CLI command, or event handler has actual implementation code behind it.
   - **Check performance-to-code alignment**: verify timeout settings, connection pools, retry logic, health checks, and monitoring dashboards have corresponding code or configuration.
2. **Assess System Constraints** (Legacy Code Analysis)
   - Document **architectural limitations**: design choices that restrict how the system can be modified (legacy database schemas, monolithic architecture, etc.)
   - Identify **modification safety levels**: classify areas as low-risk (safe to change) vs. high-risk (requires extensive testing)
   - Map **change impact paths**: show how modifications in one area affect other parts of the system through dependency chains
   - Identify **extension points**: natural insertion points for new features based on existing architectural patterns
   - Assess **evolutionary feasibility**: evaluate refactoring difficulty, modernization paths, and architectural change costs
3. **Quality Gates and Cross-Validation**
   - **Validate L3-to-L2 alignment**: ensure low-level details support high-level architecture claims
   - **Check assumption quality**: validate critical assumptions from earlier rounds against evidence found
   - **Apply quality criteria**: meet defined success metrics or recommend round repeats with specific improvements

4. **Find Missing Pieces**
   - Suggest **concrete improvements**: tests to add, interfaces to create, large classes to break apart.
   - If safe to test: run 1-2 critical scenarios to verify data types, error handling, and logging work as expected.
5. **Create Deliverables**
   - Link together all the functional, performance, and architecture documentation.
   - Organize findings into tasks with dependencies and estimated complexity.

## Analysis Quality Assurance (All Rounds)
- **Mark confidence levels**: Label each finding with evidence-based confidence (high/medium/low) indicating how certain the analysis is
- **Track key assumptions**: Explicitly list assumptions that would invalidate current conclusions if proven false
- **Prioritize next investigations**: Suggest what to examine next if time/resources allow

## Next Steps Guidance (for Your Agent)

**After completing R2 analysis, determine next action:**

### ✅ If Quality Gates Passed (Analysis Complete)
Analysis is fully validated. Deliver final specifications.

### 🔄 If Selective Re-analysis Needed
- **Focus specific modules**: Copy original command, add `--focus "module1,module2"` and `--resume "specifications/R2/checkpoint.json"`
- **Return to full R1**: Copy original command, change `--round 2` to `--round 1` and add `--resume "specifications/R2/checkpoint.json"`

### 🔁 If Major Architectural Revision Required
- **Return to R0**: Copy original command, change `--round 2` to `--round 0` and add `--resume "specifications/R2/checkpoint.json"`

## Expected Outputs
- `specifications/final/architecture_overview.md`
- `specifications/final/functional.md`
- `specifications/final/nonfunctional.md`
- `specifications/final/tasks.generated_from_code.md`
- `specifications/final/plan.reverse.md`
- `specifications/final/assumptions.md`
- *(If applicable)* `specifications/diff_R2_vs_R1.md`
- `specifications/final/checkpoint.json`
