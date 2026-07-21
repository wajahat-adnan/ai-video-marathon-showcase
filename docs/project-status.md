# Project Status

## Overview

AI Video Marathon is under active development.

The project already contains substantial backend, planner, evaluation, and media-pipeline foundations. The end-user review interface, preview workflow, and final export experience are not yet complete.

This document separates implemented work from work currently in progress and future plans.

## Current Development Stage

The project is transitioning from planner and contract foundations into media-processing implementation and later human-review tooling.

The active development branch currently focuses on media-pipeline foundations while preserving the accepted planner work behind a narrow integration boundary.

## Implemented or Substantially Developed

### Transcript Processing

- Local transcription workflow foundations
- Word-level timing support
- Sentence reconstruction
- Speaker-turn modeling
- Protected-span handling
- Repair and provenance records
- Serialization and validation contracts
- Runtime indexes

### Planner V1

- Consolidated visual-planning baseline
- Context-aware routing improvements
- Open-domain regression coverage
- Software, science, practical-process, and comparison handling
- Conservative A-roll fallback
- Real-video validation workflow

### Planner V2

- Architecture and evaluation strategy
- Transcript reconstruction foundation
- Native contracts and semantic validation
- Diagnostic and provenance reliability
- Runtime indexes and benchmarks
- Stage 1B acceptance work
- Stage 2A design contracts
- Stage 2A1 implementation and audit corrections

### Evaluation

- Focused unit and contract tests
- Context-aware evaluation
- Open-domain evaluation
- Final-routing checks
- Real-video manual review
- Regression protection for previously corrected defects
- Stage-specific acceptance and audit workflows

### Media-Pipeline Foundations

- Configuration models
- Proxy, thumbnail, and audio artifact planning
- Multi-artifact manifest design
- Explicit error and retry boundaries
- Content-based artifact identity
- Deterministic recipe fingerprints
- Stable ordering requirements
- Atomic-write requirements
- FFmpeg and FFprobe toolchain planning
- Python environment snapshot

## In Progress

### Planner Continuation

- Further Planner V2 Stage 2 work
- Additional semantic and visual-planning capabilities
- Continued acceptance testing
- Integration preparation for downstream media requests

### Media Processing

- Source-media inspection
- Proxy generation
- Audio extraction
- Thumbnail generation
- Preview artifact creation
- Cache and manifest implementation
- Failure handling and retry behavior

### Integration Boundary

- Narrow planner-to-media adapter
- Explicit request and response contracts
- Prevention of media-layer reinterpretation of planner semantics

## Planned

### End-User Interface

- Project import workflow
- Transcript and section review
- Beat-level visual recommendations
- Visual replacement controls
- Media-source selection
- Section-level previews
- Approval and override controls

### Short-Form Workflow

- Candidate detection
- Candidate ranking
- Clip review
- Subtitle selection
- Export approval

### Export

- Final timeline assembly
- Long-form rendering
- Short-form rendering
- Subtitle rendering
- Media attribution records
- Packaging and installation

## Not Yet Available

The current public showcase does not claim that the following are complete:

- Production-ready dashboard
- Finished visual review interface
- One-click editing workflow
- Final media rendering pipeline
- Packaged desktop release
- Commercial deployment

## Development Principles

Ongoing work continues to follow these constraints:

- Local-first processing
- Zero-cost baseline
- Human approval
- Domain-agnostic planning
- Deterministic fallback when uncertain
- Explicit stage contracts
- Regression testing
- Independent review for architecture-critical work
- Separation between planner and media-pipeline responsibilities

## Public Showcase Status

The public repository currently demonstrates:

- Product vision
- System architecture
- Testing strategy
- Engineering decisions
- Development status
- Private-source boundary

Screenshots and a product demo will be added when the end-user review workflow is sufficiently complete to show honestly and safely.

## Last Updated

July 2026.
