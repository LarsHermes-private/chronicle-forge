# ADR 0004: Use the Gradle Groovy DSL for the core API

- Status: Accepted
- Date: 2026-07-22
- Supersedes: [ADR 0003](0003-gradle-and-spock.md) for the Gradle DSL choice

## Context

The core API has not been generated yet, so changing the Gradle DSL does not
require a migration of existing build logic. Both the Groovy and Kotlin DSLs are
supported by Gradle.

The project owner has no prior Kotlin experience and wants to concentrate the
available learning effort on Python, the application architecture, search,
permission-aware retrieval, and AI engineering. Spock tests already introduce
Groovy to the core API build, while production code remains Java.

## Decision

Use the Gradle Wrapper with the Groovy DSL for the Spring Boot core API. Build
and settings scripts use the `.gradle` extension rather than `.gradle.kts`.

Retain Spock as the primary test style on the JUnit Platform. Retain
Testcontainers for infrastructure integration tests and start Spring only where
a test requires it.

## Consequences

The project does not require Kotlin knowledge for build maintenance. Groovy is
used consistently for Gradle scripts and Spock tests, while production code
remains Java.

The build has less compile-time DSL checking and potentially less precise IDE
assistance than an equivalent Kotlin DSL build. Build scripts should therefore
remain declarative, small, and covered by the standard build and verification
commands.

Dependency and plugin versions must remain compatible with the selected Java,
Spring Boot, Gradle, Groovy, and Spock versions.
