# ADR 0001: Modular monolith for the core API

- Status: Proposed
- Date: 2026-07-22

## Decision

Implement the Spring Boot core as one deployable modular monolith. Express domain
boundaries through packages and architecture tests before considering separate
deployables.

## Consequences

Deployment and local development stay simple. Independent scaling and failure
isolation are deferred until evidence requires them.

