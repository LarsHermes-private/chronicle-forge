# Architecture

## Containers and responsibilities

- **Angular web:** interaction and presentation; never the sole authorization layer.
- **Spring Boot core API:** system of record for users, campaigns, memberships,
  documents, visibility, processing status, and binding access decisions.
- **FastAPI knowledge service:** extraction, chunking, embedding, indexing,
  retrieval, and structured answer generation; it owns no parallel identity model.
- **PostgreSQL:** authoritative transactional and business data.
- **OpenSearch:** rebuildable full-text, filter, vector, and hybrid projections.

## Core API technology baseline

- Java 25, configured through a Gradle toolchain
- Spring Boot 4.1 with its managed Spring Framework 7.0 baseline
- Gradle Wrapper 9.6 using the Groovy DSL
- Java preview features disabled for the MVP
- Spock on the JUnit Platform, Testcontainers, and ArchUnit for verification

See [ADR 0004](../adr/0004-gradle-groovy-dsl.md) and
[ADR 0005](../adr/0005-java-25-spring-boot-4.md).

## Initial protected assets and threats

Protected assets include GM-only knowledge, private documents, identities,
credentials, and citation integrity. Initial threats include unauthorized
retrieval, prompt injection in documents, sensitive logs, stale permission
projections, unsupported citations, and processing resource exhaustion.
