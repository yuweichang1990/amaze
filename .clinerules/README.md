# FrontierExplorer - Code Analysis Rules for Cline

This directory contains Cline-specific rules and workflows for FrontierExplorer, a dynamic code architecture exploration system.

## Overview

FrontierExplorer replaces fixed round-based analysis (R0→R1→R2) with intelligent frontier-based exploration using three AI agents:

- **Explorer**: Discovers system skeleton and boundaries
- **Reflector**: Assesses confidence and identifies gaps
- **Curator**: Integrates knowledge and manages exploration frontier

## Core Principles

### Safety & Control
- **No automatic builds**: Never run build commands unless explicitly approved
- **Static analysis only**: Prefer grep/find over runtime execution
- **Human oversight**: All destructive operations require explicit consent
- **Resource limits**: Respect file limits and size constraints

### Output Management
- **Structured specifications**: Create folder hierarchy under `specifications/`
- **Memory persistence**: Incremental knowledge storage in `specifications/memory/`
- **Template integration**: Use prompts from `prompts/` directory
- **Confidence tracking**: All findings include evidence-based confidence scores

### Exploration Philosophy
- **Incremental understanding**: Build knowledge progressively, avoid context collapse
- **Confidence-driven prioritization**: Focus effort on high-value, low-confidence areas
- **Frontier awareness**: Track exploration boundaries and unknown territories
- **Agent coordination**: Intelligent three-agent workflow orchestration

## Directory Structure

```
.clinerules/
├── README.md                 # This file - overview and principles
├── workflows/
│   └── reverse-analyze.md    # Main analysis workflow definition
├── templates/               # Template references (for future extension)
└── config/                  # Configuration overrides (for future extension)
```

## Workflows

### Main Analysis Workflow: `/reverse-analyze`

Defined in: `workflows/reverse-analyze.md`

**Purpose**: Execute intelligent code architecture exploration with automatic strategy selection.

**Parameters**:

- `--workflow <type>`: Complete agent orchestrations
  - `bootstrap`: Initial system skeleton (Explorer→Reflector→Curator)
  - `expand`: Continue from frontier state
  - `converge`: Final validation and documentation

- `--agent <role>`: Direct single-agent execution
  - `explorer`: Focused discovery (skeleton/boundaries)
  - `reflector`: Quality assessment and gap identification
  - `curator`: Knowledge integration and frontier management

- `--strategy <approach>`: Exploration strategy selection
  - `Bootstrap`: Start from system boundaries
  - `CoverageDriven`: Fill understanding gaps
  - `PriorityBased`: Focus high-value areas
  - `RiskFocused`: Address critical components

- `--target <element>`: Specific exploration target
  - File paths: `pkg/auth/jwt.go`
  - Component IDs: `SERVICE_USER_001`
  - Module paths: `pkg/models`

- `--repo <path>`: Target repository (default: ".")

**Examples**:
```bash
# Bootstrap new project
/reverse-analyze --workflow bootstrap --repo ./my-project

# Direct targeted analysis
/reverse-analyze --agent explorer --target "pkg/auth" --repo ./my-project

# Strategy-driven exploration
/reverse-analyze --strategy RiskFocused --repo ./my-project
```

## Template System

### Role Templates
Located in `../prompts/roles/`:
- `explorer_skeleton_discovery.md`: Entry point and boundary discovery
- `reflector_confidence_assessment.md`: Quality evaluation and gap analysis
- `curator_frontier_management.md`: Knowledge integration

### Workflow Templates
Located in `../prompts/workflows/`:
- `bootstrap_exploration.md`: Complete initial exploration cycle

### Memory Schema
Located in `../prompts/memory/`:
- `memory_schema_and_formats.md`: Structured storage formats and relationships

## Quality Assurance

### Confidence Framework
- **High (0.8-1.0)**: Strong evidence, architecturally sound
- **Medium (0.5-0.7)**: Reasonable evidence, some gaps
- **Low (0.0-0.4)**: Weak evidence, needs verification

### Validation Rules
- Multiple evidence sources required for high confidence
- Consistency checks across all integrated findings
- Gap identification and systematic filling
- Cross-validation of related discoveries

## Output Structure

```
specifications/
├── memory/              # Incremental knowledge base
│   ├── sessions/        # Exploration session logs
│   ├── elements/        # Individual component knowledge
│   └── frontier/        # Exploration state management
├── analysis/            # Derived insights
│   ├── architecture_overview.md
│   ├── confidence_assessment.md
│   └── exploration_log.md
└── artifacts/           # Generated documentation
    ├── system_architecture.md
    ├── code_contracts.md
    └── recommendations.md
```

## Emergency Controls

### When Things Go Wrong
- **Stop immediately**: Use `/stop` or interrupt current analysis
- **Check memory state**: Review `specifications/memory/frontier/`
- **Resume safely**: Use `--resume` with last known good state
- **Fallback mode**: Simple grep-based analysis without agents

### Resource Limits
- **Time boxing**: Max 45 minutes per workflow execution
- **File limits**: Respect --file-limit parameter if provided
- **Memory safety**: No unlimited accumulation, periodic cleanup

## Troubleshooting

### Common Issues

**"Command not recognized"**
- Check `.clinerules/workflows/reverse-analyze.md` exists
- Verify Cline extension loaded properly

**"Templates not found"**
- Confirm `../prompts/` structure intact
- All role, workflow, memory templates present

**"Memory corruption"**
- Use clean slate with `--repo` parameter
- Avoid concurrent analyses on same target

### Getting Help

1. Check this README first
2. Verify all required files present
3. Test with simple commands first
4. Check Cline extension version compatibility

## Best Practices

### Analysis Strategy
- Start with `bootstrap` for new projects
- Use specific `--target` for incremental analysis
- Let system pick `--strategy` for optimal exploration
- Review memory state frequently

### Collaboration
- Share entire `specifications/` directory for team analysis
- Use consistent confidence thresholds across team
- Document human overrides in memory entries

### Maintenance
- Keep templates updated with new patterns
- Review confidence calibration periodically
- Archive completed analyses for reference

---

## Philosophy

> **"Explore with intelligence, document incrementally, understand completely."**

FrontierExplorer transforms code comprehension from a rigid, time-consuming process into an intelligent, adaptive exploration experience. Through AI agent coordination and sophisticated memory management, it maximizes understanding efficiency while maintaining human oversight and control.
