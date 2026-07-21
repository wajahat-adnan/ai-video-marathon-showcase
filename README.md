# AI Video Marathon

A local-first AI-assisted video-production system for transcript analysis, hierarchical planning, media selection, and human-reviewed editing workflows.

> **Project status:** Active development. The current implementation focuses on transcript reconstruction, hierarchical planning, evaluation, regression testing, and media-pipeline foundations. The end-user interface is not yet complete.

> This repository is a public engineering case study. The production source code is maintained privately because it contains proprietary implementation details.

## Project Overview

AI Video Marathon is being built as a zero-cost, local-first video-production assistant for long-form and short-form content.

The system is designed to analyze spoken content, reconstruct transcript structure, identify meaningful sections and beats, recommend appropriate visual treatments, and support a human editor through a review workflow.

The project prioritizes:

- Local processing
- Human control
- Domain-aware planning
- Deterministic fallbacks
- Evaluation and regression testing
- Reusable media-pipeline infrastructure

## Current Capabilities

The current implementation includes substantial backend and planning foundations.

### Transcript Reconstruction

- Word-level timestamp handling
- Sentence reconstruction
- Speaker-turn and protected-span modeling
- Repair and provenance tracking
- Runtime indexing for efficient lookup
- Serialization and validation contracts

### Hierarchical Planning

- Section and beat modeling
- Semantic and deterministic routing
- Visual-treatment recommendations
- A-roll fallback when confidence is low
- Domain-aware handling of software, science, practical processes, and abstract concepts
- Named-entity and media-type routing rules

### Evaluation and Regression Infrastructure

- Context-aware evaluation cases
- Open-domain evaluation cases
- Final-routing regression checks
- Real-video validation passes
- Focused acceptance suites
- Historical defect tracking
- Cross-stage regression protection

### Media-Pipeline Foundations

- Local FFmpeg and FFprobe integration planning
- Proxy, thumbnail, and audio artifact design
- Deterministic recipe fingerprints
- Content-based artifact identity
- Atomic writes
- Retry and error-contract design
- Multi-artifact manifest architecture

## Planned End-User Workflow

The planned interface will allow an editor to:

1. Import source video
2. Generate a local transcript
3. Review reconstructed sections and beats
4. Inspect suggested visual treatments
5. Choose stock footage, images, A-roll, screen recordings, graphics, or no change
6. Preview section-level edits
7. Review short-form candidates
8. Approve or override recommendations
9. Export final long-form and short-form outputs

## System Workflow

```text
Source Video
      |
      v
Local Transcription
      |
      v
Transcript Reconstruction
      |
      v
Hierarchical Section and Beat Modeling
      |
      v
Visual Planning and Media Routing
      |
      v
Human Review and Overrides
      |
      v
Media Processing and Preview Generation
      |
      v
Final Long-Form and Short-Form Exports
```

## Engineering Highlights

- Local-first architecture with no required cloud processing
- Timestamp-aware transcript reconstruction
- Structured contracts for planner artifacts
- Hybrid deterministic and semantic planning
- Domain-agnostic design goals
- Human-in-the-loop fallback behavior
- Strong regression and acceptance testing
- Explicit provenance and diagnostic modeling
- Narrow adapter boundaries between planner and media pipeline
- Cross-model audit process for architecture-critical work

## Technology

The private implementation uses or evaluates technologies including:

- Python
- Faster-Whisper
- FastEmbed
- spaCy
- NumPy
- FFmpeg
- FFprobe
- PyAV
- ONNX Runtime
- Pytest
- Local media and artifact caching

## Development Status

This project is under active development.

### Implemented

- Transcript-processing foundations
- Planner V1 regression baseline
- Planner V2 reconstruction and contract stages
- Stage 2A design and Stage 2A1 implementation
- Evaluation harnesses
- Media-pipeline architecture foundations
- Environment and dependency snapshots

### In Progress

- Planner V2 Stage 2 continuation
- Media processing implementation
- Narrow planner-to-media adapter
- Preview-generation workflow

### Planned

- End-user dashboard
- Visual-selection interface
- Section-level preview controls
- Short-form candidate review
- Final export workflow
- Packaging and installation

## Testing and Validation

The private repository contains extensive focused, regression, and acceptance testing.

Validation work has included:

- Hundreds of Planner V2 tests
- Established Planner V1 regression suites
- Context-aware evaluation cases
- Open-domain evaluation cases
- Final-routing checks
- Real-video validation runs
- Stage-specific acceptance audits
- Independent architecture and implementation reviews

See [Testing Strategy](docs/testing-strategy.md).

## Architecture

The project separates:

- Transcription
- Transcript reconstruction
- Syntax and semantic analysis
- Runtime indexing
- Hierarchical planning
- Visual routing
- Evaluation
- Media processing
- Artifact caching
- Human review
- Export

See [Architecture](docs/architecture.md).

## Engineering Decisions

Key design decisions include:

- Keeping processing local
- Preserving human review
- Using deterministic fallbacks when uncertain
- Maintaining domain-agnostic planner behavior
- Separating planner contracts from media-pipeline implementation
- Using explicit acceptance and audit boundaries

See [Engineering Decisions](docs/engineering-decisions.md).

## Screenshots

The end-user interface is not yet complete.

Screenshots will be added as the review dashboard and visual-planning interface become available.

See [Screenshots](screenshots/README.md).

## Demonstration

A public product demonstration will be added after the review workflow is ready.

See [Demo Plan](demo/README.md).

## Source Availability

The complete production source code is maintained in a private GitHub repository.

Selected implementation details may be reviewed privately during a technical interview or hiring process.

This public repository intentionally excludes:

- Production planner source code
- Complete routing heuristics
- Scoring formulas
- Private evaluation sets
- Proprietary prompts
- Full media-pipeline orchestration
- Internal stage builders
- Reconstructive patches and archives

## My Contribution

I designed and implemented work across:

- Transcript reconstruction
- Planner architecture
- Visual-routing logic
- Regression evaluation
- Stage contracts
- Diagnostic and provenance modeling
- Media-pipeline architecture
- Local-processing strategy
- Testing and acceptance workflows
- Human-in-the-loop product design

## Project Status

**Active development**

Backend, planner, evaluation, and media-pipeline foundations are implemented or underway. The end-user interface is planned but not yet complete.

## Disclaimer

This repository presents an engineering portfolio case study for an in-development system. It is not a finished commercial release.
