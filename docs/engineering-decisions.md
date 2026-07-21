# Engineering Decisions

## Overview

This document summarizes key engineering decisions made during the development of AI Video Marathon.

The production implementation is private. The goal here is to explain architecture, tradeoffs, and development discipline without exposing proprietary algorithms or reconstructive implementation details.

## 1. Local-First Processing

### Decision

Keep transcription, planning, media analysis, preview generation, and export local by default.

### Why

Video projects may contain private client footage, unpublished content, and sensitive business material. Local processing avoids making cloud upload a requirement.

### Tradeoff

Local execution must work within the available hardware and requires careful dependency, performance, and packaging decisions.

## 2. Human-in-the-Loop Editing

### Decision

Use automation to recommend edits, not to remove editor control.

### Why

Visual selection is subjective and context-sensitive. The editor must be able to review sections, replace recommendations, choose alternatives, or leave footage unchanged.

### Tradeoff

The system is not intended to be a one-click autonomous editor. The review interface becomes a major product component.

## 3. Deterministic Fallbacks

### Decision

Prefer safe deterministic fallbacks, especially A-roll or no visual change, when planner confidence is low.

### Why

A conservative recommendation is better than inserting irrelevant or misleading media.

### Tradeoff

The system may produce fewer aggressive visual changes, but quality and trust are better preserved.

## 4. Structured Planner Artifacts

### Decision

Represent transcript structure, sections, beats, diagnostics, provenance, and visual recommendations as explicit structured artifacts.

### Why

Structured artifacts improve:

- Validation
- Serialization
- Testing
- Debugging
- Stage boundaries
- Reproducibility
- Future UI integration

### Tradeoff

The system requires more schema design and contract maintenance than a loosely connected script pipeline.

## 5. Hierarchical Planning

### Decision

Plan at multiple levels rather than routing isolated transcript phrases independently.

### Why

Good visual decisions depend on section purpose, surrounding context, discourse structure, and the relationship between nearby beats.

### Tradeoff

Hierarchical planning is more complex than keyword-based routing and requires stronger reconstruction and evaluation infrastructure.

## 6. Hybrid Semantic and Deterministic Logic

### Decision

Combine semantic ranking with deterministic rules and explicit priorities.

### Why

Semantic models help with open-domain language, while deterministic rules protect known boundaries such as:

- Software interface actions
- Practical processes
- Scientific explanations
- Named entities
- A-roll fallback
- Literal versus figurative meaning

### Tradeoff

The planner must manage interactions between learned similarity, rule-based constraints, and final-routing precedence.

## 7. Domain-Agnostic Core

### Decision

Avoid building the planner around one narrow video niche.

### Why

The system is intended to support business, software, science, education, practical demonstrations, and other domains.

### Tradeoff

Generalization requires broader evaluation and makes some domain-specific shortcuts unacceptable.

## 8. Explicit Provenance and Diagnostics

### Decision

Track where reconstructed and planned artifacts came from and why uncertain or corrected cases occurred.

### Why

Provenance and diagnostics make failures easier to understand and allow later stages or reviewers to distinguish original input, inferred structure, and repair behavior.

### Tradeoff

Artifacts become richer and more complex, but the system becomes easier to audit and evolve.

## 9. Planner and Media-Pipeline Separation

### Decision

Keep planner contracts separate from media-processing implementation.

### Why

The planner should describe editorial intent, while the media pipeline should produce files and previews from explicit requests.

This prevents transcoding details from leaking into semantic planning and prevents the media layer from silently changing editorial meaning.

### Tradeoff

A narrow adapter is required between the two systems.

## 10. Content-Based Artifact Identity

### Decision

Identify generated media artifacts through source content and deterministic recipe inputs.

### Why

This supports:

- Reliable caching
- Reuse
- Reproducibility
- Change detection
- Avoiding unnecessary recomputation

### Tradeoff

Recipe construction must account for relevant tool versions and configuration fields.

## 11. Atomic Writes

### Decision

Write generated artifacts atomically where possible.

### Why

Interrupted processing should not leave partially written files that look valid.

### Tradeoff

Temporary-file handling and final replacement behavior must be designed explicitly.

## 12. Stable Manifest Ordering

### Decision

Use deterministic ordering for media and artifact records.

### Why

Stable ordering improves reproducible tests, predictable serialization, cleaner diffs, and easier debugging.

### Tradeoff

Ordering rules must be defined and preserved across implementations.

## 13. Stage-Based Development

### Decision

Break architecture-critical work into explicit stages with acceptance criteria.

### Why

The planner is complex enough that large unstructured changes would be difficult to review safely.

Stage boundaries support:

- Focused implementation
- Independent audits
- Regression checks
- Frozen contracts
- Controlled continuation

### Tradeoff

Development is slower and more formal than rapid prototyping, but risk is lower.

## 14. Independent Audits

### Decision

Use separate authoring and audit passes for critical architecture and algorithm work.

### Why

Independent review helps detect hidden assumptions, contract gaps, and implementation errors that the original author may overlook.

### Tradeoff

Critical stages require more review time and process discipline.

## 15. Private Production Source

### Decision

Keep the complete implementation private and maintain a separate public showcase repository.

### Why

This protects proprietary work while still allowing employers to evaluate:

- Architecture
- Testing discipline
- Product direction
- Engineering decisions
- Current project status
- Demonstrated outputs

### Tradeoff

Full code review requires controlled private access during a hiring process.

## 16. Honest Work-in-Progress Status

### Decision

Present the project publicly as active development rather than implying that the end-user application is finished.

### Why

The backend, planner, evaluation, and media-pipeline foundations are substantial, but the final review dashboard and export workflow are not yet complete.

### Tradeoff

The showcase has fewer UI screenshots today, but it remains accurate and credible.

## Future Considerations

Planned or potential future decisions include:

- Desktop UI framework selection
- Preview rendering architecture
- Subtitle rendering system
- Licensing and attribution storage
- Short-form candidate scoring
- Packaging across Windows and Linux
- Local model selection under hardware constraints
- Final timeline interchange and export formats
