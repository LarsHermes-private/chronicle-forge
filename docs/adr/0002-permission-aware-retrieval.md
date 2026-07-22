# ADR 0002: Enforce permissions before retrieval context assembly

- Status: Proposed
- Date: 2026-07-22

## Decision

The core API determines effective access constraints. Search and retrieval apply
them before passages can enter ranking, prompts, intermediate results, or answers.

## Consequences

Authorization metadata must be available in search projections. Revocation and
the complete retrieval path require explicit security tests.

