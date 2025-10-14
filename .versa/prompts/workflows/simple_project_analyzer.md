# Simple Project Analyzer

## For Tiny/Small Projects (< 5 files, < 500 lines)

### Scale Determination
**Automatic scale assessment before analysis:**
1. Count source files: `{file_count}` files
2. Count lines of code: `{total_lines}` lines total
3. Identify main technologies from imports/CONFIGs
4. Assess codebase complexity

### When to Use This Template
- **⭐ Tiny projects** (< 3 files, < 100 lines): Direct README-style summary
- **🟢 Small projects** (< 5 files, < 500 lines): Basic project overview with component analysis
- **🟡 Appropriate complexity**: Single service/API, basic domain logic
- **🔧 Suitable stacks**: Go/web frameworks, Python REST APIs, simple Node.js projects

### Analysis Approach
**Direct output generation** - Skip complex memory system for rapid understanding

### Output Format: Adaptive Project Overview

Generate a clean, readable summary in `specifications/project_overview.md` with dynamic content based on project analysis:

```
# {project_name} - Project Overview

## Executive Summary
{executive_summary}

## Architecture Overview
- **Type**: {architecture_type}
- **Primary Technologies**: {primary_technologies}
- **Architecture Pattern**: {architecture_pattern}

## Core Components
{core_components_section}

## Key Files
{key_files_section}

## Implementation Status
{implementation_status}

## Development Recommendations
{development_recommendations}

---

*Analysis generated: {timestamp}*
*Files analyzed: {files_analyzed} | Total lines: {total_lines} | Estimated completion: {completion_percentage}*
```

## Implementation Guidelines

### Content Generation Rules
1. **Executive Summary**: 1-2 sentences describing what the project does, primary tech stack, and architectural approach
2. **Core Components**: Identify and describe main functionalities, APIs, or major features based on code analysis
3. **Key Files**: List most important source files with line counts and brief role descriptions
4. **Implementation Status**: Use emoji indicators (✅⚠️🔧) to show completed features, incomplete features, and missing components

### Output Format Standards
- **Structured**: Use consistent headers and emoji icons for visual clarity
- **Actionable**: Include specific recommendations for next development steps
- **Evidence-based**: Base all claims on actual code analysis, not assumptions
- **Concise**: Keep total length under 800 words for small projects

## Quality Assurance Standards

### Completeness Validation
- **Technology Stack**: Must identify primary languages, frameworks, libraries
- **Architecture Type**: Web API, CLI tool, library, service, etc.
- **Core Functionality**: Must describe what the project actually does
- **Missing Components**: Identify any incomplete features or referenced but unimplemented code

### Confidence Requirements
- **High Confidence**: Direct code evidence for all major claims
- **Evidence-Based**: All analysis backed by source code examination
- **No Assumptions**: Avoid speculative statements about intentions or future features
- **Conservative Estimates**: Prefer under-statement to over-statement

## Success Metrics
- **Developer Understandability**: New developer can understand project purpose within 5 minutes
- **Actionable Guidance**: Clear next steps for development or deployment
- **Missing Parts Identified**: Unimplemented features clearly flagged
- **Technology Clarity**: Tech stack and dependencies clearly explained
