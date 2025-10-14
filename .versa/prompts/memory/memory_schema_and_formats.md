# Memory System Schema and Formats

## Overview
The memory system stores all exploration findings in structured format enabling incremental knowledge building, confidence tracking, and intelligent frontier expansion. All memory entries use YAML frontmatter for metadata and structured content.

## Directory Structure

```
specifications/memory/
├── sessions/           # Exploration session logs
│   ├── bootstrap_[timestamp].md
│   ├── expand_[timestamp].md
│   └── converge_[timestamp].md
├── elements/          # Individual findings
│   ├── skeleton/      # Structural elements
│   ├── component/     # Architectural components
│   ├── assessment/    # Confidence evaluations
│   └── integration/   # Curator syntheses
├── frontier/          # Current exploration state
│   ├── active_frontier.md
│   ├── confidence_map.md
│   └── exploration_log.md
└── schemas/           # Memory format definitions
    └── entry_formats.yaml
```

## Entry Types and Formats

### SKELETON Element Entry
Used by Explorer to record discovered system components.

```yaml
---
entry_id: "SKELETON_[TYPE]_[NAME]_[COUNTER]"
timestamp: "2025-10-14T10:00:00Z"
agent: "explorer"
phase: "skeleton_discovery"
confidence: "high|medium|low"

element_type: "entrypoint|component|boundary|crosscut"
element_name: "MainApp|UserService|HTTPBoundary|AuthCrosscut"
location: "path/to/file.go:line-range"

skeleton_summary:
  role: "Brief description of element's purpose"
  technology: ["Golang", "Gin", "PostgreSQL"]
  responsibilities: ["HTTP server", "request routing", "middleware"]

connections:
  - type: "input_from|output_to|depends_on|protects|coordinates"
    target: "AnotherElementName"
    strength: "strong|medium|weak"
    interface: "function_name|protocol|pattern"

metadata:
  complexity: "low|medium|high"
  criticality: "high|medium|low"
  test_coverage_estimate: "high|medium|low|unknown"
  crosscuts: ["logging", "security", "validation"]
  discovered_at: "filename:line"  # Source of discovery

next_exploration_hints:
  - "Explore X component implementation"
  - "Verify Y connection assumption"
  - "Check Z boundary conditions"

unresolved_questions:
  - "How does this handle error conditions?"
  - "What are the performance characteristics?"
---

# Discovery Details
Brief technical notes about how this element was discovered and validated.
```

### ASSESSMENT Entry
Used by Reflector to evaluate confidence and identify gaps.

```yaml
---
entry_id: "ASSESS_[TARGET_ELEMENT_ID]_[TIMESTAMP]"
timestamp: "2025-10-14T10:15:00Z"
agent: "reflector"
phase: "confidence_assessment"

target_element: "SKELETON_ENTRYPOINT_MAIN_001"
assessment_type: "initial|followup|validation"

confidence_assessment:
  overall_confidence: "high|medium|low"
  confidence_score: 0.85

  evidence_strength:
    direct_evidence: 0.9    # Code directly examined
    pattern_evidence: 0.8   # Matches known patterns
    indirect_evidence: 0.7  # Inferred from context

  completeness_score: 0.8  # How complete is understanding
  consistency_score: 0.9   # Fits with other findings
  risk_level: "low|medium|high"

gaps_identified:
  - category: "structural|connection|evidence|logic"
    description: "Missing database error handling"
    severity: "critical|major|minor"
    evidence_needed: "Database exception paths"

inconsistencies_found:
  - elements: ["ELEM_001", "ELEM_002"]
    inconsistency: "Service depends on component not found"
    resolution_status: "needs_investigation|resolved|acknowledged"
    resolution_action: "Add component discovery"

assumptions_made:
  - assumption: "Follows standard MVC pattern"
    confidence: "medium"
    alternatives: ["Layered", "Event-driven"]
    verification_method: "Examine more controllers"

actionable_insights:
  - priority: "critical|high|medium"
    insight: "HTTP handler missing input validation"
    action_type: "re_explore|verify|document_risk"
    target: "specific_component_path"

metadata:
  assessment_duration: "15 minutes"
  evidence_sources: 3
  follow_up_required: true
---

# Assessment Rationale
Detailed reasoning for confidence levels and gap identification.
```

### INTEGRATION Entry
Used by Curator to synthesize knowledge and update frontier.

```yaml
---
entry_id: "INTEGRATE_[SESSION_ID]_[COUNTER]"
timestamp: "2025-10-14T10:30:00Z"
agent: "curator"
phase: "frontier_management"

session_id: "20251014_bootstrap_001"
integration_scope: "skeleton_bootstrap|architecture_expansion|deep_dive"

memory_operations:
  - operation: "create|update|merge|supersede"
    element_id: "SKELETON_COMPONENT_USER_001"
    confidence_delta: +0.15
    connections_added: 2
    evidence_integrated: ["DISCOVERY_001", "ASSESSMENT_002"]

frontier_update:
  explored_zone_growth: 3     # New elements mastered
  frontier_expansion: 5       # New elements discovered
  unknowns_discovered: 2      # New regions identified
  current_coverage: "35%"     # Estimated system understanding

priority_targets_selected:
  - target_element: "SKELETON_BOUNDARY_DB_CONNECTION"
    selection_criteria:
      importance: 0.9         # High centrality
      current_confidence: 0.4 # Needs work
      risk_level: 0.8        # Critical path
    priority_score: 0.87
    estimated_effort: "moderate"
    expected_value: "high"

strategy_adjustments:
  - adjustment_type: "phase_transition|scope_change|technique_switch"
    from_state: "skeleton_discovery"
    to_state: "architecture_analysis"
    trigger_condition: "Confidence threshold 0.7 reached"
    rationale: "Solid foundation established"

consistency_operations:
  - operation_performed: "conflict_resolution|pattern_unification"
    elements_affected: ["COMP_001", "COMP_002"]
    resolution_method: "evidence_weighting|consensus_voting"
    stability_improved: 0.1   # Confidence delta

metadata:
  explorer_input_count: 4
  reflector_input_count: 3
  new_connections_created: 6
  conflicts_resolved: 1
  session_quality_score: 0.85
---

# Integration Summary
- **Knowledge growth**: How much new understanding added
- **Frontier evolution**: Current exploration boundaries
- **Strategic direction**: Next major focus areas
- **Integration quality**: Coherence and consistency achieved
```

## Memory Query and Relation System

### Element Relationships
All entries support cross-referencing through structured fields:

```yaml
relationships:
  related_elements:
    - id: "SKELETON_COMPONENT_AUTH_001"
      relationship: "depends_on|coordinates_with|affects"
      strength: "direct|indirect|weak"
    - id: "ASSESS_AUTH_SECURITY_001"
      relationship: "validated_by"
      strength: "complete"

  dependency_chain:
    requires: ["INFRA_DB_CONNECTION"]
    required_by: ["SERVICE_USER_MGMT", "API_PUBLIC"]
    conflicts_with: []

  evidence_chain:
    primary_evidence: ["CODE_REVIEW_001"]
    supporting_evidence: ["PATTERN_ANALYSIS_001"]
    contradictory_evidence: []
```

### Query Categories

**Semantic Queries:**
- Find all elements with confidence < 0.6
- Identify critical path components
- Locate elements affecting specific functionality
- Find unverified assumptions

**Structural Queries:**
- Get all components of type "boundary"
- Find connection patterns between elements
- Identify missing dependencies
- Cluster elements by architectural layer

**Confidence Queries:**
- Rank elements by risk level
- Find assessment inconsistencies
- Track confidence evolution over time
- Identify validation gaps

## Memory Maintenance

### Automatic Operations
- **Dead Link Cleanup**: Remove references to non-existent elements
- **Confidence Decay**: Gradually reduce confidence of unverified elements
- **Relationship Validation**: Verify connection consistency
- **Duplicate Detection**: Merge similar findings

### Manual Curation Points
- **Session Review**: End-of-session quality assessment
- **Conflict Resolution**: Human-guided resolution of assessment conflicts
- **Priority Calibration**: Adjust selection algorithms based on results
- **Scope Redefinition**: Update exploration boundaries

## Quality Assurance

### Completeness Checks
- All elements must have ID and timestamp
- Confidence values must be justified
- Connections must be bidirectional
- Relationships must be specific

### Consistency Validation
- Assessment confidence matches available evidence
- Element relationships are logically sound
- Phase transitions are appropriately triggered
- Frontier targets have clear prioritization
