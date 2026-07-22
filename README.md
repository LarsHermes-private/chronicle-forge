# Chronicle Forge

Chronicle Forge is a personal open-source platform for managing, researching,
and using tabletop role-playing game knowledge with source-backed AI support.

The project is intentionally developed as a sequence of small, runnable vertical
slices. Public repository content must use original, synthetic, or suitably
licensed data only.

## Planned applications

- `apps/web`: Angular/TypeScript frontend
- `apps/core-api`: Java 25/Spring Boot 4 core API, built with Gradle 9 Groovy DSL
- `apps/knowledge-service`: Python/FastAPI document and AI service

## Repository map

- `contracts/`: API and event contracts
- `demo/`: safe public demo documents and seed data
- `docs/`: product, requirements, architecture, and decisions
- `infra/`: local infrastructure configuration
- `scripts/`: portable developer and CI entry points

## Current status

The repository is in the product-definition and architecture phase. Application
frameworks have not been generated yet.

## Working principles

- PostgreSQL is the system of record; search indexes are rebuildable projections.
- Authorization is enforced before retrieval, not after answer generation.
- The core API uses Java 25 without preview features and Spring Boot 4.1.
- Stable requirements and decisions live in the repository.
- Stories, tasks, bugs, and spikes are tracked as issues.
- Build and verification commands remain callable outside a specific CI provider.

See [the product definition](docs/product/README.md),
[the requirements](docs/requirements/README.md), and
[the architecture overview](docs/architecture/README.md).
