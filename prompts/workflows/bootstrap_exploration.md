# Bootstrap System Exploration Workflow

## Overview
This workflow coordinates the initial exploration session where no prior knowledge exists. It orchestrates Explorer, Reflector, and Curator agents to establish the foundational understanding of the codebase.

## Project Scale Assessment (First Step)

### Automatic Scale Determination
**Before any exploration begins:**
1. Count total source files in target directory
2. Estimate total lines of code across files
3. Assess technology stack complexity
4. Evaluate domain/business logic complexity

### Strategy Selection Matrix
| Scale | Criteria | Approach | Output |
|-------|----------|----------|--------|
| Tiny | <3 files, <100 loc | Direct summary | README-style report |
| Small | <5 files, <500 loc | Simple analysis | Summary + basic component docs |
| Medium | 5-20 files, 500-5000 loc | Standard workflow | Full memory + reports |
| Large | >20 files, >5000 loc | Complex workflow | Multi-phase analysis |

### Scale-Adaptive Time Allocation
- Tiny: 2-5 minutes
- Small: 5-15 minutes
- Medium: 15-45 minutes
- Large: 45-120 minutes

## Workflow Phases

### Phase 1: Initial Exploration (Scale-dependent)
**Agent: Explorer**

#### For Small Projects (strategy selection based on scale assessment above)
- Use `simple_project_analyzer.md` template
- Generate immediate project overview report
- Skip complex memory system for rapid understanding

#### For Medium/Large Projects (standard workflow)
- Execute skeleton discovery using `explorer_skeleton_discovery.md`
- Target: Complete system skeleton mapping
- Deliverable: Multiple skeleton element entries

**Success Criteria:**
- Multiple entrypoints identified
- System boundaries detected
- Major components mapped
- Cross-cutting concerns noted
- **Simple projects**: Readable overview generated immediately

### Phase 2: Quality Assessment (15 minutes)
**Agent: Reflector**
- Execute confidence assessment using `reflector_confidence_assessment.md`
- Target: Evaluate all skeleton discoveries
- Deliverable: Confidence scores and gap analysis

**Success Criteria:**
- All elements have confidence assessments
- Critical gaps identified
- Risk levels determined
- Next actions prioritized

### Phase 3: Integration & Planning (10 minutes)
**Agent: Curator**
- Execute frontier management using `curator_frontier_management.md`
- Target: Synthesize findings and establish exploration plan
- Deliverable: Coherent memory and prioritized frontier

**Success Criteria:**
- Memory consistency achieved
- Clear exploration frontier defined
- Strategic direction established
- Next targets selected

## Coordination Protocol

### Input Requirements
- **Clean repository**: No existing exploration memory
- **Time allocation**: 45 minutes maximum for bootstrap
- **Exploration boundary**: Initial codebase scope (adjustable)

### Agent Communication Rules
1. **Explorer → Reflector**: Passes raw skeleton elements for assessment
2. **Reflector → Curator**: Passes quality-evaluated elements for integration
3. **Curator → Next Phase**: Provides synthesized understanding and targets

### Decision Points
- **Quick Iteration**: If critical gaps found, immediate targeted re-exploration
- **Scope Adjustment**: If too much/too little discovered, adjust discovery depth
- **Phase Transition**: Bootstrap complete when skeleton foundation solid

## Expected Outputs

### Memory Artifacts
```
specifications/
├── memory/
│   ├── bootstrap_session_[timestamp].md
│   ├── skeleton_elements_[counter].md
│   ├── assessment_results_[counter].md
│   └── frontier_state_initial.md
└── analysis/
    └── bootstrap_summary.md
```

### Content Standards
- All entries follow specified YAML frontmatter formats
- Confidence levels are evidence-based and justified
- Frontier targets are well-prioritized with rationale
- Next phase transition criteria clearly defined

## Completion Criteria

### System Understanding Level
- **Structural**: Major components and boundaries identified
- **Functional**: High-level system purpose understood
- **Confidence**: Average confidence across elements > 0.6
- **Stability**: No critical architectural paradoxes

### Exploration Readiness
- Next exploration targets clearly identified
- Frontier zones properly mapped
- Unknown areas bounded and estimated
- Strategic direction for next phase defined

## Failure Recovery

### Scenario 1: Insufficient Discovery
**Symptom**: Too few skeleton elements found
**Action**: Expand discovery scope or switch to different techniques

### Scenario 2: High Risk Findings
**Symptom**: Critical components have low confidence
**Action**: Immediate targeted re-exploration of risk areas

### Scenario 3: Inconsistent Findings
**Symptom**: Major contradictions between discoveries
**Action**: Deep-dive validation of conflicting elements

## Quality Metrics

### Coverage Metrics
- Entry points discovered: minimum 3 required
- System boundaries: input/output both represented
- Component types: variety indicates architectural diversity
- Cross-cuts: authentication, logging, error handling identified

### Confidence Distribution
- High confidence elements: should dominate critical paths
- Medium confidence: acceptable in peripheral areas
- Low confidence: flagged for immediate attention

### Integration Metrics
- Connection density: should show meaningful system structure
- Frontier clarity: next targets clearly separable from current understanding
- Strategic coherence: exploration plan aligns with system architecture
