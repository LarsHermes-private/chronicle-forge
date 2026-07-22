# Core API

Planned Java 25/Spring Boot 4.1 modular monolith using the Gradle 9.6 Wrapper
with the Groovy DSL. Java 25 is configured through a Gradle toolchain; preview
features are not enabled for the MVP.

Spock is the primary test style on the JUnit Platform. Testcontainers will
support infrastructure integration tests and ArchUnit will guard module
boundaries. The application is generated with the first slice.

See [ADR 0004](../../docs/adr/0004-gradle-groovy-dsl.md) for the Gradle DSL
choice and [ADR 0005](../../docs/adr/0005-java-25-spring-boot-4.md) for the Java,
Spring Boot, and Gradle baseline.
