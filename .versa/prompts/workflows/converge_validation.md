# Converge Validation Workflow

## Overview
This workflow performs final validation and global optimization after incremental exploration phases. It serves as the concluding synthesis phase that resolves conflicts, eliminates redundancy, and produces final authoritative artifacts.

## Workflow Context
**Triggered by:** `--workflow converge` command
**Prerequisite:** Completed expand cycles with established frontier state
**Goal:** Transform incremental artifacts into coherent, conflict-free final documentation

## Pre-Converge Checks

### Frontier State Validation
**Required Conditions:**
- `active_frontier.md` shows minimal remaining targets (<20% unexplored)
- Confidence distribution shows majority high-confidence elements (>70% >0.7)
- All critical path components have been explored

### Artifact Readiness Assessment
- Verify existence of `specifications/artifacts/` directory
- Confirm presence of all artifact types from expand cycles
- Check for gross inconsistencies across versions

## Workflow Phases

### Phase 1: Global Conflict Resolution (20 minutes)
**Agent: Reflector (Enhanced Global Mode)**

#### Conflict Detection
Scan all artifacts for inconsistencies:
- Component relationship contradictions
- Confidence score discrepancies
- Terminological inconsistencies
- Architectural paradoxes

#### Evidence Reconciliation
For each conflict:
- Compare source evidence across memory entries
- Apply higher-confidence sources to resolve
- Flag unresolvable conflicts for human review
- Update confidence scores based on resolution quality

**Deliverable:** Conflict resolution report and unified evidence base

### Phase 2: Artifact Consolidation (25 minutes)
**Agent: Curator (Global Synthesis Mode)**

#### Redundancy Elimination
- Remove duplicate information across artifacts
- Consolidate overlapping sections
- Rationalize repeated concepts into single authoritative statements

#### Completeness Optimization
- Fill identified knowledge gaps with available memory
- Strengthen weak sections with corroborating evidence
- Add missing cross-references and connections

#### Quality Standardization
- Ensure consistent terminology throughout all artifacts
- Apply uniform formatting and structure
- Verify all confidence claims have supporting evidence

**Deliverable:** Consolidated artifact drafts with integrated knowledge

### Phase 3: Final Validation & Publication (15 minutes)
**Agent: Curator (Final Review Mode)**

#### Comprehensive Review
- Validate all high-confidence (>0.8) claims have multiple evidence sources
- Ensure critical system paths are fully represented
- Confirm architectural consistency across all artifacts

#### Final Optimizations
- Improve readability and flow of consolidated content
- Add executive summaries and navigation aids
- Include final confidence heatmaps and risk assessments

**Deliverable:** Publication-ready final artifacts

## Global Synthesis Guidelines

### Evidence-Based Consolidation
```yaml
consolidation_rules:
  confidence_resolution:
    - prefer_multiple_sources: true
    - latest_evidence_weight: medium
    - human_overrides_preserve: true

  redundancy_handling:
    - merge_similar_concepts: true
    - preserve_unique_insights: true
    - create_summary_sections: true

  gap_filling:
    - use_available_memory: true
    - avoid_speculation: true
    - mark_uncertainties: true
```

### Artifact Regeneration Rules
**Override previous versions:**
- `system_architecture.md`: Complete rewrite with global inconsistencies resolved
- `component_relationships.md`: Unified view eliminating conflicting connections
- `code_contracts.md`: Consolidated interface specifications
- `recommendations.md`: Prioritized based on resolved understanding

### Memory Preservation
- Maintain all original memory entries for audit trails
- Add convergence annotations to relevant entries
- Create comprehensive session log of consolidation decisions

## Success Criteria

### Quality Assurance Metrics
- **Conflict Resolution**: Zero major architectural contradictions
- **Completeness**: All critical components represented (>95% coverage)
- **Consistency**: Unified terminology and architectural model
- **Readability**: Clear, navigable documentation structure

### Evidence Standards
- **High Confidence Claims**: Multiple (>2) independent evidence sources
- **Critical Path Coverage**: 100% confidence >0.8 for core functionality
- ** Gap Awareness**: Remaining uncertainties clearly documented
- **Evidence Traceability**: All claims linkable to source memory entries

## Failure Handling

### Insufficient Evidence
**Symptom:** Critical claims lack supporting evidence
**Action:**
- Downgrade confidence levels appropriately
- Document evidence gaps clearly
- Schedule additional targeted exploration

### Unresolvable Conflicts
**Symptom:** Fundamental contradictions remain
**Action:**
- Flag conflicts for human expert review
- Provide alternative interpretations
- Document decision rationale

### Incomplete Coverage
**Symptom:** Major system areas missing from artifacts
**Action:**
- Identify missing components
- Trigger additional expand cycles
- Note coverage limitations

## Output Structure

### Final Artifacts
```
specifications/artifacts/
├── system_architecture.md       # Authoritative architecture overview
├── component_relationships.md   # Unified relationship diagram
├── code_contracts.md           # Consolidated interface specifications
├── recommendations.md          # Final prioritized recommendations
└── convergence_report.md       # Details of consolidation decisions
```

### Enhanced Artifacts Features
- **Authority Markers**: Clear indication of final authoritative versions
- **Confidence Heatmaps**: Visual confidence assessment overlays
- **Evidence References**: Direct links to supporting memory entries
- **Change Logs**: Track consolidation decisions and rationales

## Integration with Exploration Frontier

### Post-Convergence State
```yaml
convergence_completion_actions:
  - archive_frontier_state: "final_converged_state_[timestamp]"
  - set_exploration_status: "completed_pending_new_requirements"
  - enable_maintenance_mode: "allow_incremental_updates"
  - document_coverage_scope: "specifications/artifacts/convergence_report.md"
```

### Future Expansion Support
- Maintain active frontier for incremental updates
- Version artifacts with convergence timestamps
- Enable selective re-convergence for modified areas

This workflow ensures that incremental exploration culminates in coherent, authoritative documentation that serves as the definitive system understanding.
