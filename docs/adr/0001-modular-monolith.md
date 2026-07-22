# ADR 0001: Modular monolith for the core API

- Status: Accepted
- Date: 2026-07-22

## Context

The core API owns the authoritative business data and binding access decisions
for users, campaigns, memberships, documents, visibility, and processing
status. These responsibilities require explicit boundaries, but the MVP has no
evidence that they require independently deployable services.

Splitting the core into distributed services from the start would introduce
network communication, partial failures, distributed observability, deployment
coordination, and data-consistency concerns before the domain boundaries and
operational requirements have been validated.

This decision applies only to the Java/Spring Boot core API. The Angular web
application and Python knowledge service remain separate applications with
their own deployment artifacts and responsibilities.

## Decision

Implement the Spring Boot core as one process and one deployable artifact while
organizing its business capabilities as explicit modules.

Use the following provisional module boundaries for the MVP:

- `campaign`: campaign identity and lifecycle
- `membership`: users, campaign membership, and campaign roles
- `document`: document metadata, ownership, type, and visibility
- `authorization`: effective access decisions and retrieval constraints
- `processing`: processing requests, status, attempts, and failures
- `search`: search requests and coordination of authorized retrieval

These boundaries may be refined as the domain becomes clearer. Modules should
be organized primarily by business capability rather than as global technical
layers such as `controller`, `service`, and `repository`.

Apply the following dependency rules:

- A module may use another module only through an explicitly exposed module API.
- Internal types and implementation packages are not accessed from other modules.
- A module does not write another module's database state directly.
- Cross-module workflows use exposed application services or internal events.
- Circular module dependencies are prohibited.
- Domain rules remain testable without starting a Spring application context.

Use ArchUnit tests to enforce package boundaries, allowed dependencies, and the
absence of dependency cycles. Spring Modulith may be evaluated separately if its
module verification, documentation, or event support provides concrete value;
it is not required by this decision.

Keep the modules in one deployable until evidence justifies extraction. A module
may be considered for a separate service when one or more of the following are
demonstrated:

- materially different scaling or resource requirements
- independent availability or failure-isolation requirements
- persistent resource contention within the core application
- a genuinely independent release cadence
- stable ownership by an independent team
- a security or compliance boundary that requires process-level isolation

Extraction requires a new ADR based on measured behavior or a concrete
operational requirement. Code size alone is not sufficient justification.

## Alternatives considered

### Unstructured monolith

One Spring Boot deployment without enforced business boundaries would be simple
initially, but coupling would grow without a reliable way to detect violations.
This option is rejected.

### Microservices from the start

Deploying each proposed module independently could provide isolation and
independent scaling, but those benefits are not required by the MVP. The added
network, consistency, testing, deployment, and observability complexity is not
currently justified. This option is rejected for the initial architecture.

### Separate deployment per domain module

Treating every domain boundary as a deployment boundary would prematurely make
provisional domain assumptions expensive to change. This option is deferred
until operational evidence supports a specific extraction.

## Consequences

Deployment and local development remain simple while the code retains explicit,
testable business boundaries. In-process calls and transactions are available
where appropriate, and provisional module boundaries remain comparatively easy
to refine.

The team must actively maintain module APIs and architecture tests. A single
deployment means modules share process resources and a release lifecycle.
Independent scaling and process-level failure isolation are deferred until
evidence requires them.
