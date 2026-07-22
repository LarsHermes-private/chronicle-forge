# ADR 0005: Use Java 25 and Spring Boot 4 for the core API

- Status: Accepted
- Date: 2026-07-22

## Context

The core API has not been generated yet, so the project can select a current
technology baseline without migrating production code. Java 25 reached general
availability on 2025-09-16 and is offered as a long-term-support release by most
JDK vendors.

Spring Boot 4.1 supports Java versions from 17 through 26. Gradle supports
running on Java 25 from version 9.1 onward. Selecting current compatible
versions avoids an early platform upgrade while the first vertical slices are
being developed.

The project should benefit from the current Java platform without increasing
the MVP learning and maintenance scope through experimental language features.

## Decision

Use the following baseline for the Spring Boot core API:

- Java 25
- Spring Boot 4.1.x
- Spring Framework 7.0.x as managed by Spring Boot
- Gradle Wrapper 9.6.x using the Groovy DSL

Configure Java 25 through the Gradle Java toolchain for compilation, tests, and
execution. Use the Spring Boot dependency-management baseline instead of
independently pinning versions of dependencies managed by Spring Boot.

Do not enable Java preview features for the MVP. Preview features require a
separate decision supported by a concrete use case and explicit build, test,
runtime, and IDE configuration.

Use a maintained Java 25 distribution in local development, CI, and container
images. The concrete vendor may differ as long as the build and runtime remain
compatible and reproducible.

## Consequences

The project starts on a current Java LTS baseline and can use stable Java 25
language, runtime, diagnostics, and performance improvements.

The Gradle Wrapper must be version 9.1 or newer; the initial skeleton pins the
latest verified Gradle 9.6 patch release. Local development and CI need access
to a Java 25 toolchain.

Spring Boot 4 uses the current Spring Framework and Jakarta ecosystem. Examples
and third-party integrations written only for earlier Spring Boot generations
must be checked for compatibility before adoption.

Spock, Groovy, Testcontainers, plugins, and container images must be verified
against Java 25, Spring Boot 4.1, and the selected Gradle Wrapper during the
first runnable slice.
