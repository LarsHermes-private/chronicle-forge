# ADR 0003: Gradle Kotlin DSL and Spock for the core API

- Status: Superseded
- Date: 2026-07-22
- Superseded by: [ADR 0004](0004-gradle-groovy-dsl.md)

## Decision

Use the Gradle Wrapper with Kotlin DSL for the Spring Boot build. Use Spock as the
primary test style on the JUnit Platform. Use Testcontainers for infrastructure
integration tests and start Spring only where a test requires it.

## Consequences

Production code remains Java while tests use Groovy. Dependency versions must be
compatible with the selected Java and Spring Boot versions.
