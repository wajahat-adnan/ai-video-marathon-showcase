# Testing Strategy

## Overview

AI Video Marathon uses layered automated testing and evaluation to protect transcript reconstruction, planner behavior, routing decisions, and media-pipeline contracts.

The production test suite is maintained in the private repository. This document describes the testing approach without exposing proprietary fixtures, scoring rules, or complete implementation details.

## Testing Goals

The testing strategy is designed to verify that:

- Transcript structure remains valid and timing-aware
- Planner artifacts satisfy explicit contracts
- Visual routing behaves consistently across domains
- Uncertain cases fall back safely
- Corrected defects do not reappear
- Media artifacts are reproducible
- Major stages can be accepted independently
- New work does not regress established behavior

## Test Layers

### Unit Tests

Unit tests focus on small deterministic behaviors, including:

- Data-model validation
- Serialization and deserialization
- Timestamp and span handling
- Transcript reconstruction helpers
- Runtime indexes
- Diagnostic identity
- Planner contract invariants
- Media configuration validation
- Artifact identity and recipe inputs

### Contract Tests

Contract tests verify that planner and media artifacts obey stable schemas.

These tests cover areas such as:

- Required fields
- Identifier stability
- Ordering guarantees
- Provenance records
- Error contracts
- Capability declarations
- Boundary ownership
- Serialization round trips

### Regression Tests

Regression suites protect previously corrected behavior across multiple content domains.

Representative categories include:

- Software demonstrations
- Science and technical explanations
- Practical processes
- Comparisons
- Abstract concepts
- Figurative language
- Named entities
- A-roll fallback behavior
- Screen-recording routing
- Diagram and illustration routing

### Evaluation Suites

The planner is evaluated with several complementary suites.

#### Context-Aware Evaluation

Checks whether visual recommendations respect surrounding meaning rather than routing isolated words literally.

#### Open-Domain Evaluation

Checks whether behavior generalizes beyond narrow handcrafted examples.

#### Final-Routing Evaluation

Checks the final selected treatment after all rules, priorities, and fallbacks are applied.

#### Real-Video Validation

Representative full transcripts are processed and manually reviewed to identify defects that synthetic cases may miss.

## Planner V2 Acceptance Testing

Planner V2 work is divided into stages with focused acceptance criteria.

Testing may include:

- Stage-specific focused suites
- Established regression suites
- Full project test runs
- Serialization checks
- Complexity and runtime checks
- Frozen artifact verification
- Independent architecture or implementation audits

A stage is not treated as accepted merely because its focused tests pass. It must also preserve established behavior and satisfy its documented contracts.

## Media-Pipeline Testing

The media-pipeline foundation is designed for tests covering:

- Configuration validation
- Tool-version capture
- Deterministic recipe fingerprints
- Content-based identities
- Stable manifest ordering
- Atomic-write behavior
- Retry classification
- Artifact sub-schema validation
- Cache-hit and cache-miss behavior
- FFmpeg and FFprobe command construction

## Test Data Policy

Public examples use synthetic or non-sensitive content only.

The public repository excludes:

- Private evaluation corpora
- Full real-video transcripts
- Proprietary gold labels
- Internal adversarial cases
- Reconstructive patches
- Client media
- Copyrighted source footage not licensed for redistribution

## Deterministic Validation

Critical planner and media behavior is tested through deterministic assertions wherever possible.

This improves:

- Reproducibility
- Debuggability
- Auditability
- Regression detection
- Cross-stage confidence

Semantic components are evaluated within explicit acceptance boundaries rather than trusted without verification.

## Manual Review

Automated tests are supplemented by manual inspection of:

- Section boundaries
- Beat completeness
- Visual-treatment appropriateness
- Screen-recording recommendations
- A-roll fallbacks
- Real-video planner output
- Planned human-review workflows
- Preview and export behavior as those components are implemented

## Independent Audit Process

Architecture-critical work uses separate authoring and audit passes.

The workflow is designed to preserve reviewer independence for:

- Planner contracts
- Core algorithms
- Stage acceptance
- Corrections after audit findings
- Final critical-stage verification

## Current Evidence

The private repository includes:

- Hundreds of Planner V2 tests
- Established Planner V1 regression suites
- Context-aware evaluation cases
- Open-domain evaluation cases
- Final-routing checks
- Real-video validation runs
- Stage-focused acceptance suites
- Media-pipeline foundation tests in active development

Exact counts change as the project evolves, so this public document emphasizes testing structure rather than presenting a permanently fixed total.

## Private Test Boundary

The public repository intentionally excludes:

- Complete test source
- Proprietary fixtures
- Internal scoring weights
- Private transcripts
- Gold evaluation outputs
- Full benchmark datasets
- Acceptance patches and audit archives

Selected test results and implementation details may be reviewed privately during a technical interview.
