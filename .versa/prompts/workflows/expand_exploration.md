# Expand Exploration Workflow

## Overview
This workflow continues exploration from existing frontier state, synthesizing accumulated memory into comprehensive artifacts. It extends bootstrap findings with deeper analysis and transforms raw memory into final deliverables.

## Workflow Context
**Triggered by:** `--workflow expand` command
**Input:** Existing memory state (`specifications/memory/`) and active frontier
**Goal:** Transform memory accumulation into human-readable artifacts

## Workflow Phases

### Phase 1: Frontier Analysis (10 minutes)
**Agent: Explorer**

Resume from current frontier state:
- Load `specifications/memory/frontier/active_frontier.md`
- Identify highest-priority unexplored areas
- Execute targeted discovery on frontier elements
- Generate new skeleton/component findings

**Deliverable:** New exploration entries in `specifications/memory/elements/`

### Phase 2: Memory Integration & Assessment (15 minutes)
**Agent: Reflector**

Evaluate new findings and assess overall confidence:
- Analyze new discoveries against existing knowledge
- Identify confidence gaps and inconsistencies
- Update confidence scores for all affected elements
- Flag critical gaps requiring immediate attention

**Deliverable:** Updated confidence assessments in `specifications/memory/assessment/`

### Phase 3: Synthesis & Artifact Generation (20 minutes)
**Agent: Curator (Enhanced)**

Transform memory into final artifacts:
- Load all current memory entries
- Synthesize findings into comprehensive documents
- Generate artifacts in `specifications/artifacts/` directory
- Update exploration frontier for next session

## Enhanced Curator Synthesis Phase

### Memory Aggregation
```
Load all memory elements:
├── elements/skeleton/     # System structure
├── elements/component/    # Implementation components
├── assessment/           # Confidence evaluations
└── frontier/            # Current exploration state
```

### Artifact Generation Rules

#### 📋 system_architecture.md
**Synthesize from:** skeleton elements, high-confidence component relationships

**Content Structure:**
```markdown
# System Architecture Overview

## Executive Summary
[High-level system purpose and scale]

## Architectural Boundaries
- Entry Points: [list from skeleton boundaries]
- System Boundaries: [input/output interfaces]
- Data Flow: [major data transformations]

## Component Architecture
[Major components with confidence scores]
- **Component Name** (Confidence: 0.85)
  - Purpose: [functionality]
  - Responsibilities: [key duties]
  - Dependencies: [critical connections]

## Design Patterns Identified
[Architectural patterns with evidence]

## Confidence Overview
- Overall System Confidence: [average score]
- Critical Path Coverage: [percentage]
- Unknown Areas: [estimated percentage]

## Risk Assessment
[High-risk elements with low confidence]
```

#### 🔗 component_relationships.md
**Synthesize from:** connection data across all memory elements

**Content Structure:**
```markdown
# Component Relationships & Dependencies

## Architecture Layers
```
[Layer Diagram]
┌─────────────────┐    ┌─────────────────┐
│   Presentation  │ -> │ Business Logic │
│   Layer        │    │ Layer          │
└─────────────────┘    └─────────────────┘
         │                      │
         v                      v
┌─────────────────┐    ┌─────────────────┐
│   Data Access   │ <- │   Data Store    │
│   Layer        │    │   Layer        │
└─────────────────┘    └─────────────────┘
```

## Component Dependencies
- **Component A** -> **Component B** (Strength: Strong)
  - Interface: [API/contract details]
  - Data Flow: [what passes between them]
  - Coupling Type: [tight/loose]

## Cross-Cutting Concerns
- **Authentication**: Affects [components list]
- **Logging**: Implemented in [components list]
- **Caching**: Used by [components list]
```

#### 📄 code_contracts.md
**Synthesize from:** interface analysis, function signatures, contracts

**Content Structure:**
```markdown
# Code Contracts & Interfaces

## Public APIs
### Service Endpoints
```
/api/users/{id} [GET]
├── Input: { id: string }
├── Output: { user: UserObject }
├── Error Codes: 404 (Not Found), 500 (Server Error)
├── Authentication: JWT Token Required
```

## Data Contracts
### User Object Schema
```json
{
  "id": "string (UUID)",
  "name": "string (required)",
  "email": "string (email format)",
  "created_at": "ISO 8601 timestamp"
}
```

## Interface Specifications
- **Interface Name**: Contract details
- **Consumers**: [list of components]
- **Providers**: [list of implementations]
```

#### 🎯 recommendations.md
**Synthesize from:** confidence assessments, gap analysis, reflector insights

**Content Structure:**
```markdown
# Development Recommendations

## Priority Actions
## 🚨 Critical (Confidence < 0.5)
- [Component] needs verification - evidence insufficient
- [Connection] requires validation - assumption-based

## ⚠️ High Priority (Confidence 0.5-0.7)
- [Area] should be explored further - partial understanding
- [Pattern] needs confirmation - pattern recognition only

## 📋 Medium Priority (Confidence 0.7-0.8)
- [Feature] could benefit from deeper analysis
- [Interface] should be documented formally

## Quality Improvements
- Add error handling for [unhandled cases]
- Implement logging for [components without observability]
- Add input validation for [public interfaces]

## Next Exploration Targets
Based on current frontier analysis:
1. [Target 1] - Priority: High, Effort: Medium
2. [Target 2] - Priority: Medium, Effort: Low
```

## Artifact Quality Standards

### Completeness Requirements
- **Evidence-Based**: All statements backed by memory entries
- **Confidence-Calibrated**: Unreliable information clearly marked
- **Gap-Aware**: Unknown areas explicitly documented
- **Actionable**: Specific recommendations, not vague suggestions

### Generation Logic
```yaml
artifact_generation_rules:
  system_architecture:
    input_sources: ["skeleton_elements", "high_confidence_components"]
    synthesis_method: "aggregate_patterns"
    output_format: "architectural_document"
    minimum_confidence: 0.6

  component_relationships:
    input_sources: ["all_connections", "interface_analysis"]
    synthesis_method: "relationship_mapping"
    output_format: "diagrammatic_view"
    minimum_confidence: 0.7

  code_contracts:
    input_sources: ["interface_elements", "type_definitions"]
    synthesis_method: "contract_extraction"
    output_format: "specification_document"
    minimum_confidence: 0.8

  recommendations:
    input_sources: ["reflector_findings", "gap_analysis", "frontier_targets"]
    synthesis_method: "priority_ranking"
    output_format: "actionable_guidance"
    minimum_confidence: 0.5
```

## Success Criteria

### Artifact Quality Metrics
- **Coverage**: Major system elements represented (>80%)
- **Readability**: Clear structure and explanations
- **Confidence**: Low-confidence elements properly flagged
- **Actionability**: Specific next steps recommended

### Memory Integration Metrics
- **Synthesis Ratio**: Artifacts represent substantive memory content
- **Gap Documentation**: Unknown areas clearly identified
- **Confidence Transparency**: Confidence levels communicated to readers
- **Evolutionary Path**: Artifacts evolve with new discoveries

## Integration with Frontier Management

### Post-Artifact Frontier Update
```yaml
artifact_completion_actions:
  - update_frontier_state: "artifacts_generated"
  - confidence_recalibration: "based_on_synthesis"
  - next_target_prioritization: "gap-driven_selection"
  - exploration_metrics_update: "include_artifact_coverage"

frontier_artifacts_generated:
  - "specifications/artifacts/system_architecture.md"
  - "specifications/artifacts/component_relationships.md"
  - "specifications/artifacts/code_contracts.md"
  - "specifications/artifacts/recommendations.md"
```

## Error Handling & Recovery

### Synthesis Failures
- **Insufficient Memory**: Fall back to basic skeleton summary
- **Low Confidence**: Generate draft artifacts with warnings
- **Inconsistent Data**: Flag contradictions and prioritize resolution
- **Missing Elements**: Document gaps as "requires further exploration"

### Resume Capability
- **Artifact Regenerations**: Support updating existing artifacts with new data
- **Incremental Synthesis**: Add to existing artifacts rather than overwrite
- **Version Control**: Track artifact evolution through memory sessions

This workflow ensures that expand explorations produce not just internal memory, but human-consumable artifacts that provide real value for understanding and maintaining the codebase.
