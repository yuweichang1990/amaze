# Single-Pass Analysis Workflow

Perform comprehensive one-shot architecture analysis for medium-scale projects (5k-25k lines). Use single agent to execute complete discovery, assessment, and artifact generation without phase fragmentation.

## Workflow Phases (65 minutes total)

### Phase 1: Comprehensive Discovery (25 minutes)
**Complete System Mapping** - Conduct thorough skeleton discovery across entire codebase

#### Steps:
1. **Full Structural Scan** - Map all entrypoints, components, boundaries in one pass
2. **Comprehensive Relationship Mapping** - Identify all connections and dependencies
3. **Architecture Pattern Recognition** - Detect frameworks, patterns, and design decisions
4. **Data Flow Tracing** - Map complete information flows through the system

**Key Focus:** Ensure no structural element is missed in initial comprehensive pass

### Phase 2: Integrated Assessment & Synthesis (25 minutes)
**Unified Evaluation & Integration** - Merge assessment and curation in single cognitive pass

#### Steps:
1. **Holistic Confidence Evaluation** - Assess entire system understanding quality
2. **Gap Analysis & Validation** - Identify inconsistencies and missing elements
3. **Knowledge Consolidation** - Integrate all discoveries into coherent understanding
4. **Business purpose summarize** - Summarize the business purpose of this project

**Key Optimization:** Single agent performs both reflective analysis and integrative synthesis

### Phase 3: Final Artifact Generation (15 minutes)
**Complete Deliverable Production** - Generate comprehensive product documentation for development and deployment

#### Steps:
1. **System Scope & Requirements** - Define functional/non-functional requirements, acceptance criteria
2. **Architecture Documentation** - Produce thorough architectural overview with design decisions
3. **Component Relationship Mapping** - Create detailed interaction diagrams and data flows
4. **Implementation Guide** - Document interfaces, contracts, and development patterns

**Key Output:** Seven specialized artifacts - requirements, system scope, architecture, patterns, relationships, contracts, and recommendations

## Memory System Optimization

### Consolidated Data Collection
Single output file capturing all architectural discoveries:

```yaml
---
analysis_session: "single_pass_[timestamp]"
project_scale: "medium"
analysis_duration: "65 minutes"
collected_at: "timestamp"

system_discovery:
  entrypoints:
    - id: "main.go"
      type: "application_server"
      exposes: ["http_port_8080"]
      initializes: ["db_connection", "http_server"]

  boundaries:
    - type: "external_api"
      provider: "payment_gateway"
      contracts: ["payment_processing", "refund_handling"]

  components:
    - name: "UserService"
      responsibilities: ["authentication", "profile_management"]
      dependencies: ["database", "auth_middleware"]

relationships:
  - from: "API_Controller"
    to: "UserService"
    type: "service_call"
    data_flow: "user_credentials"

architecture_patterns:
  - pattern: "Layered_Architecture"
    layers: ["presentation", "business", "data"]
    confidence: 0.9

confidence_assessment:
  overall_system_confidence: 0.85
  critical_path_coverage: "95%"
  identified_gaps: []
  risk_factors:
    - "legacy_payment_integration"
    - "single_database_bottleneck"

recommendations:
  - priority: "high"
    concern: "scalability"
    suggestion: "Implement database read replicas"
    impact: "Improve concurrent user handling"
---

# Discovered Architecture Overview
- **System Type**: Web application with REST API
- **Technology Stack**: Go backend, PostgreSQL database, Redis cache
- **Architecture**: Layered architecture with service separation
- **Critical Components**: User management, payment processing, API gateway
- **Data Flow**: Client → API Gateway → Services → Database/Cache

# Key Findings
- Strong separation of concerns between business logic and data access
- Comprehensive error handling and logging framework
- Security middleware properly implemented
- Test coverage adequate for business-critical components

# Architectural Gaps
- No rate limiting on API endpoints
- Single points of failure in service communication
- Limited monitoring and observability

# Development Recommendations
- Implement distributed caching strategy
- Add circuit breakers for external service calls
- Enhance monitoring with application metrics
- Consider microservice decomposition for payment service
```

### Removed Memory Elements
**Skipped for efficiency:**
- ~~Session-by-session logs~~ → Consolidated in single collection
- ~~Incremental assessments~~ → Integrated evaluation
- ~~Frontier state tracking~~ → Complete coverage in one pass
- ~~Intermediate artifacts~~ → Direct final deliverables

## Success Criteria

### Efficiency Metrics
- **⚡ Context Window Utilization**: Complete analysis within single AI context
- **⏱️ Total Analysis Time**: 45-75 minutes for medium-scale projects
- **📊 Output Completeness**: All seven artifacts generated in single pass
- **🎯 Accuracy**: 90%+ confidence on critical architectural elements

### Quality Assurance
- **🏗️ Structural Completeness**: All major system components identified
- **🔗 Relationship Mapping**: Component interactions fully documented
- **📋 Contract Clarity**: Interface specifications complete and accurate
- **💡 Insight Depth**: Recommendations actionable and strategic

## Artifact Output Structure

### Final Deliverables
```
specifications/
├── single_pass_collection.md      # Raw architectural data
├── artifacts/                      # Production-ready documentation
│   ├── requirements.md             # Functional/non-functional requirements & acceptance criteria
│   ├── system_scope.md             # System boundaries, purpose, and business context
│   ├── system_architecture.md      # Comprehensive architectural overview & design decisions
│   ├── architecture_patterns.md    # Identified design patterns and frameworks
│   ├── component_relationships.md  # Detailed interaction diagrams and data flows
│   ├── code_contracts.md          # Interface specifications and contracts
│   └── recommendations.md         # Development guidance and next steps
└── metadata.json                  # Analysis session information
```

## Strategy Selection Logic
**Automatic Strategy**: CoverageDriven - maximizes knowledge coverage for comprehensive understanding in single pass.

**Why CoverageDriven?** Single-pass workflow prioritizes filling all knowledge gaps to produce complete architectural picture, not focusing on specific high-value areas.
