# Versa Reverse Analysis Workflow

This workflow performs intelligent code architecture exploration using frontier-based techniques with AI agent coordination.

## Command
```
/reverse-analyze [OPTIONS]
```

## Purpose
Execute systematic code architecture exploration that goes beyond traditional static analysis by using confidence-driven exploration, memory-based knowledge accumulation, and intelligent frontier management.

## Core Features
- **Frontier-Based Exploration**: Dynamically identify and explore unexplored system areas
- **Three-Agent Coordination**: Explorer→Reflector→Curator workflow for quality assurance
- **Incremental Memory**: Build understanding progressively without context collapse
- **Confidence Scoring**: Prioritize exploration based on uncertainty and importance
- **Strategy Selection**: Automatically choose optimal exploration approaches

## Parameters

### CORE WORKFLOW PARAMETERS
- `--repo <path>`: Target repository path (default: ".")
- `--workflow <type>`: Complete workflow execution
  - `bootstrap`: Initial system skeleton discovery (Explorer→Reflector→Curator)
  - `expand`: Continue exploration from current frontier state
  - `converge`: Final validation and comprehensive documentation

### AGENT EXECUTION PARAMETERS
- `--agent <role>`: Execute specific agent role
  - `explorer`: Discover system skeleton, entry points, and boundaries
  - `reflector`: Assess confidence levels and identify knowledge gaps
  - `curator`: Integrate findings and manage exploration frontier

### STRATEGY PARAMETERS
- `--strategy <approach>`: Exploration strategy selection
  - `Bootstrap`: Start from system boundaries and entry points
  - `CoverageDriven`: Fill gaps where confidence is uneven
  - `PriorityBased`: Focus on high-impact, unclear components
  - `RiskFocused`: Address security-critical and high-risk areas

### TARGETING PARAMETERS
- `--target <element>`: Focus exploration on specific element (integrated into workflow logic)

### FRONTIER PARAMETERS
- `--resume <state_file>`: Continue from saved exploration state
  - Default: `specifications/memory/frontier/active_frontier.md`
  - Allows resuming interrupted analysis sessions

### QUALITY CONTROL PARAMETERS
- `--confidence-threshold <0.0-1.0>`: Minimum confidence filter (default: 0.6)
  - Higher values = more conservative, reliable findings
  - Lower values = broader exploration coverage

- `--quality <draft|standard|thorough>`: Unified quality control parameter



### ADDITIONAL PARAMETERS
- `--exclude <patterns>`: Glob patterns to exclude from analysis
- `--file-limit <number>`: Maximum files to analyze (default: 8000)
- `--timebox <limits>`: Time constraints (e.g., `--timebox "structure=10m,analysis=20m"`)
- `--read-only <boolean>`: Analysis only, no modifications (default: true)

## Usage Examples

### BASIC WORKFLOWS
```bash
# Bootstrap analysis for new codebase
/reverse-analyze --workflow bootstrap --repo ./my-project

# Resume interrupted exploration
/reverse-analyze --workflow expand --resume "specifications/memory/frontier/state.backup.md"

# Final comprehensive analysis
/reverse-analyze --workflow converge --repo ./api-service
```

### AGENT EXECUTION
```bash
# Discover system skeleton
/reverse-analyze --agent explorer --repo ./web-app

# Assess quality of existing findings
/reverse-analyze --agent reflector --target "pkg/payment" --repo ./ecommerce

# Integrate new findings with existing knowledge
/reverse-analyze --agent curator --repo ./microservice
```

### TARGETED ANALYSIS
```bash
# Analyze specific component with standard quality
/reverse-analyze --agent explorer --target "pkg/auth" --quality standard --repo ./backend

# Focus on security-critical areas
/reverse-analyze --strategy RiskFocused --target "authentication,middleware" --repo ./app

# Coverage-driven gap filling
/reverse-analyze --strategy CoverageDriven --confidence-threshold 0.8 --repo ./system
```

### ADVANCED CONFIGURATIONS
```bash
# Time-boxed critical path analysis
/reverse-analyze --workflow bootstrap --timebox "total=30m,exploration=15m" --repo ./legacy-code

# Large codebase with resource limits
/reverse-analyze --file-limit 5000 --exclude "node_modules/**,dist/**,test/**" --workflow bootstrap --repo ./monorepo

# Incremental development analysis
/reverse-analyze --strategy PriorityBased --target "pkg/new-feature" --confidence-threshold 0.9 --repo ./product
```

## Behavior Guidelines

### EXPLORATION STRATEGY SELECTION
- **Bootstrap**: When knowledge base is empty or very sparse (<5 discovered elements)
- **CoverageDriven**: When overall confidence distribution is highly uneven (<60% average confidence)
- **PriorityBased**: When specific components need deep understanding or have high business value
- **RiskFocused**: When security, reliability, or operational risks need immediate attention

### QUALITY ASSURANCE

### QUALITY ASSURANCE
- **Confidence Validation**: All high-confidence claims (>0.8) must have multiple evidence sources
- **Gap Identification**: Actively look for and document architectural inconsistencies
- **Frontier Awareness**: Always identify unexplored areas for next analysis session

### RESOURCE MANAGEMENT
- **Time Boxing**: Respect configured time limits, downgrade scope if approaching limits
- **File Filtering**: Honor exclusion patterns and file limits to avoid analysis paralysis
- **Memory Efficiency**: Use structured formats to maintain efficient context window usage

## Output Structure

### MEMORY FILES (Incremental Knowledge)
```
specifications/memory/
├── sessions/           # Session logs and progress tracking
├── elements/          # Individual findings and discoveries
│   ├── skeleton/      # System structure elements
│   ├── component/     # Implementation components
│   ├── assessment/    # Quality evaluations
│   └── integration/   # Curator syntheses
└── frontier/          # Exploration state management
    ├── active_frontier.md    # Current exploration boundaries
    ├── confidence_map.md     # System understanding confidence
    └── exploration_queue.md  # Prioritized next targets
```

### ANALYSIS OUTPUTS (Derived Insights)
```
specifications/analysis/
├── architecture_overview.md     # High-level system architecture
├── confidence_assessment.md     # Reliability analysis
├── exploration_log.md         # Session-by-session progress
└── risk_assessment.md         # Security and operational risks
```

### DELIVERABLES (Final Documentation)
```
specifications/artifacts/
├── system_architecture.md       # Comprehensive architecture docs
├── component_relationships.md   # System interaction diagrams
├── confidence_heatmap.md        # Visual confidence assessment
└── recommendations.md           # Implementation suggestions
```

## Error Handling

### COMMON ISSUES
- **Template Not Found**: Ensure `../prompts/` directory structure is intact
- **Memory Corruption**: Use `--repo` parameter for clean slate or diagnose state files
- **Timeout Exceeded**: Adjust `--quality` level or increase `--timebox` for next session

### RECOVERY STRATEGIES
- **Interrupted Session**: Use `--resume` with last successful state file
- **Memory Issues**: Start with `--workflow bootstrap` for clean restart
- **Scope Too Large**: Use targeting parameters to focus analysis scope

### FALLBACK MODES
- **Draft Mode**: Use `--quality draft` for fast overview
- **Thorough Mode**: Use `--quality thorough` for deep analysis
- **Conservative Mode**: Increase `--confidence-threshold` to avoid unreliable discoveries

## Integration Points

### EXTERNAL TOOLS
- **File System**: `find`, `grep`, `tree` for structural discovery
- **Git History**: `git log`, `git blame` for evolution analysis
- **Language Tools**: Language-specific analyzers when available

### Cline Integrations
- **Template System**: Uses prompts from `../prompts/` directory
- **Safety Rules**: Respects development safety guidelines
- **Human Oversight**: All destructive operations require explicit approval

### COLLABORATION
- **Multi-session**: Save and resume analysis sessions across developer handoffs
- **Team Sharing**: Share `specifications/` directory for team-wide knowledge
- **Review Process**: Memory entries support collaborative validation

## Success Criteria

### IMMEDIATE FEEDBACK
- **Discovery Rate**: At least 3-5 significant skeleton elements identified
- **Confidence Distribution**: Clear understanding of what is known vs unknown
- **Frontier Definition**: Well-defined next exploration targets

### QUALITY METRICS
- **Confidence Scores**: High-confidence findings for critical paths
- **Gap Awareness**: Systematic identification of architectural unknowns
- **Consistency Checks**: No major contradictions in discoveries

### OUTCOME MEASURES
- **Knowledge Growth**: Measurable increase in system understanding
- **Actionable Insights**: Concrete recommendations for next development steps
- **Risk Reduction**: Identified and mitigated architectural risks

This workflow transforms reverse engineering from a rigid, error-prone process into an intelligent, adaptive exploration experience that scales with codebase complexity while maintaining human insight and control.
