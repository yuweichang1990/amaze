# Reverse Analyze Prompts (R×L, VS Code–aware)

English prompt templates for AI coding agents to **reverse-engineer** an existing codebase across **three rounds (R0–R2)**, with VS Code / LSP call hierarchy integration and clear **Inputs/Outputs** per round.

- **R0 – Global Coarse Pass** (default L2 / depth=2): fast static scan, build symbol index, discover entrypoints, major modules, and bases like cross-cutting features.
- **R1 – Focused Deepening** (L2+L3 / depth=3–4): deepen 1–3 focus modules, produce code map, call chains, and types.
- **R2 – Convergence** (L0–L3 cross-check): align functional, non-functional, and architecture docs into a final deliverable.

> Safe default: **no build / no tests**. Only run minimal smoke tests in a trusted sandbox or when `--run-tests` is explicitly enabled.

**Adaptive Analysis**: Intelligent framework that iteratively refines understanding. R2 quality gates validate findings and guide smart re-analysis when new insights emerge, ensuring comprehensive codebase comprehension without redundant work.

## Features
- ⚡ **Static-only by default**: Safe analysis without running code or tests.
- 🔄 **Adaptive iteration**: Quality gates enable smart re-analysis when needed.
- 🏗️ **VS Code integration**: Uses LSP for precise call hierarchy and symbol analysis.
- 📊 **Multi-level architecture**: C4-like documentation from L0 strategic to L3 code details.
- 🧩 **Replaceable agents**: Works with any AI agent, not locked to specific tools.
- 📈 **Legacy-aware**: Special focus on understanding modification patterns in mature codebases.
- ⏱️ **Scalable performance**: Configurable depth limits and file exclusions for large projects.
- ✅ **Quality tracking**: Confidence scoring and assumption validation throughout.

## Quick Start
1. Download and unzip.
2. Open `prompts/R0_prompt.md` in your AI agent or chat interface.
3. Paste the prompt: `/reverse-analyze --round 0 --repo .` (or equivalent command).
4. Review `specifications/R0/*`, pick 1–3 **focus modules** from the R0 report.
5. Run **R1**: `/reverse-analyze --round 1 --focus "chosen_modules"`
6. Run **R2**: `/reverse-analyze --round 2` (follows any iteration guidance from R2 output).

> **For different AI agents**: Configure your agent to read files from `prompts/` folder and enable slash commands. Each agent platform handles tool configuration differently. See `docs/SlashCommand.md` for suggested parameters and iteration examples. For Cline-specific setup, see Agent Configuration section below.

## Folder Structure
- `prompts/`
  - `R0_prompt.md`
  - `R1_prompt.md`
  - `R2_prompt.md`
- `docs/`
  - `SlashCommand.md`
  - `Parameters.md`

## Real-World Examples

### Basic Analysis
```
/reverse-analyze --round 0 --repo /path/to/project
```

### Focused Analysis
```
/reverse-analyze --round 1 --focus "api,service" --depth 3
```

### Advanced Analysis with Time Limits
```
/reverse-analyze --round 2 --timebox "structure=15m,analysis=20m" --run-tests
```

### Iterative Re-analysis (from R2 guidance)
```
/reverse-analyze --round 1 --focus "problematic_module" --resume "specifications/R2/checkpoint.json"
```

## Validation Checklist ✅

Before starting analysis, verify:
- [ ] Target directory contains source code (not just config files)
- [ ] Your agent has file system access to the project
- [ ] Code is in a compilable state (if `--run-tests` will be used)
- [ ] No exotic build systems (gradle/maven/npm/pip/poetry are well-supported)

During analysis, monitor:
- [ ] Progress checkpoints appear for long-running rounds
- [ ] Confidence levels are assigned to critical findings
- [ ] Assumptions are tracked and validated
- [ ] Quality gates pass before final delivery

## Common Troubleshooting

### Analysis Takes Too Long
- **Reduce depth**: `--depth 1` for faster scanning
- **Increase file limits**: `--file-limit 20000` if system is fast
- **Timebox phases**: `--timebox "r0=5m,r1=10m"` to control duration

### Getting Incomplete Results
- **Check exclusion filters**: `--exclude "test/**,tmp/**"` may exclude important code
- **Adjust recursion limits**: `--depth 4` if analysis seems shallow
- **Resume from checkpoint**: `--resume specifications/R0/checkpoint.json` on interrupted runs

### Quality Issues
- **Low confidence findings**: Use `--depth 3` or R1 re-analysis with specific focus modules
- **Architecture misalignments**: Follow R2 iteration guidance to correct foundational assumptions
- **Missing connections**: Check if `--run-tests` flag provides additional validation

## Contributing 🤝

### Adding New Analysis Patterns
- Test prompts on diverse codebases (open source projects of varying sizes)
- Document assumptions and limitations clearly
- Include confidence scoring for findings

### Improving Templates
- Focus on making analysis more reliable, not just comprehensive
- Add validation steps within prompts when possible
- Consider agent cognitive load when adding complexity

### Reporting Issues
- Include the full command used and codebase type
- Specify which round failed and what error symptoms appeared
- Note agent type and version if applicable

## Agent Configuration Examples

### For Cline (VS Code Extension)
1. **Copy Configuration File**: Copy the included `.clinerules` file to your project root directory. This file contains:
   - Pre-configured tool settings for reverse engineering tasks
   - `/reverse-analyze` slash command with all supported parameters
   - Safety rules and behavior guidelines
   - Template integration settings

2. **Verify Tools**: The `.clinerules` file enables essential tools. Confirm these are available in your Cline installation:
   - `run_terminal_cmd` - For executing analysis commands
   - `grep_search` - For fallback code searching when LSP is unavailable
   - `read_file`, `list_dir` - For reading templates and project files
   - Add any project-specific tools as needed

3. **Working Directory**: Cline will use your project root as the working directory for `run_terminal_cmd` operations.

> **One-Click Setup**: Simply copy `.clinerules` to your project root - no manual configuration needed!

### For Other AI Agents
- **GitHub Copilot Chat**: Use the prompt content directly in chat interface or create workspace custom instructions
- **Claude Desktop**: Configure as a tool and point to the `prompts/` folder
- **Custom Agents**: Implement file reading and command execution capabilities, then load templates from the `prompts/` folder

> **Note**: Template files in `prompts/` are designed to be agent-agnostic. They contain pure analysis logic without platform-specific references. Agent-specific configurations (like slash commands) are handled separately in your agent platform's configuration.

## License
MIT
