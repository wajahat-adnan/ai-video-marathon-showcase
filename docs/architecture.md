# Architecture

## Overview

AI Video Marathon is designed as a local-first, human-in-the-loop video-production system.

The production implementation is private. This document describes high-level responsibilities, data flow, and architectural boundaries without exposing proprietary algorithms or complete planner logic.

## High-Level Flow

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
Long-Form and Short-Form Export
```

## Main Subsystems

### 1. Transcription

Responsible for:

- Extracting audio from source media
- Producing word-level timestamps
- Preserving timing information needed by downstream planning
- Remaining replaceable behind a narrow interface

### 2. Transcript Reconstruction

Responsible for:

- Reconstructing sentence boundaries
- Modeling speaker turns
- Preserving protected spans
- Tracking repairs and provenance
- Validating timing and structural contracts
- Building indexes for efficient lookup

### 3. Hierarchical Planning

Responsible for:

- Identifying meaningful sections
- Dividing sections into visual beats
- Preserving semantic relationships
- Producing structured planner artifacts
- Supporting deterministic fallback behavior

### 4. Visual Routing

Responsible for selecting an appropriate treatment category, such as:

- A-roll
- Stock video
- Stock image
- Screen recording
- Diagram or illustration
- Motion graphic
- No visual change

Routing decisions are designed to consider domain, actionability, visual evidence, uncertainty, and editorial context.

### 5. Evaluation

Responsible for:

- Running focused regression suites
- Checking context-aware behavior
- Checking open-domain behavior
- Checking final routing
- Supporting real-video validation
- Preserving previously corrected defects

### 6. Human Review

The planned review layer will allow an editor to:

- Inspect sections and beats
- Review recommended visuals
- Override planner decisions
- Select media alternatives
- Preview changes
- Approve long-form and short-form outputs

### 7. Media Pipeline

Responsible for:

- Inspecting source media
- Generating proxies
- Extracting audio
- Creating thumbnails and previews
- Managing artifact identities
- Avoiding unnecessary recomputation
- Handling retries and failures predictably

### 8. Artifact and Cache Management

The media foundation is designed around:

- Content-based identity
- Deterministic recipe fingerprints
- Explicit artifact schemas
- Atomic writes
- Stable manifest ordering
- Tool-version awareness
- Reproducible outputs

### 9. Export

The planned export layer will support:

- Long-form output
- Short-form clips
- Subtitle rendering
- Selected visual media
- Final timeline assembly
- Source and license attribution where required

## Architectural Boundaries

### Planner Boundary

The planner produces structured recommendations and timing-aware artifacts.

It should not directly own:

- Media transcoding
- File-system cache behavior
- UI rendering
- Final export orchestration

### Media-Pipeline Boundary

The media pipeline consumes explicit requests through a narrow adapter.

It should not silently reinterpret planner semantics or modify planner contracts.

### UI Boundary

The end-user interface will present existing planner and media artifacts for review.

It should preserve human control rather than automatically hiding uncertainty.

## Design Principles

- Local processing by default
- Human approval before irreversible output
- Deterministic fallback when confidence is low
- Explicit contracts between stages
- Domain-agnostic planner behavior
- Reproducible media artifacts
- Clear diagnostic and provenance records
- Independent testing of critical boundaries
- Narrow adapters between major subsystems

## Current Implementation Status

### Implemented or Substantially Developed

- Transcript reconstruction foundations
- Planner V1 regression baseline
- Planner V2 contracts and reconstruction stages
- Runtime indexes
- Diagnostics and provenance
- Stage 2A design
- Stage 2A1 implementation
- Evaluation harnesses
- Media-pipeline architecture and configuration foundations

### In Progress

- Planner V2 continuation
- Media-processing implementation
- Planner-to-media adapter
- Preview generation

### Planned

- End-user dashboard
- Visual selection and replacement controls
- Short-form review workflow
- Final timeline assembly
- Export and packaging

## Private Implementation Boundary

The public repository intentionally excludes:

- Production planner source
- Complete routing heuristics
- Scoring formulas
- Private evaluation corpora
- Internal prompts
- Reconstructive patches
- Stage-builder scripts
- Full media-pipeline orchestration
