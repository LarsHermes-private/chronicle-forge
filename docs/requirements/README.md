# Requirements

Stable identifiers may be referenced from issues, tests, and decisions.

## Functional

- **REQ-F-001:** A GM can import a permitted document into a campaign.
- **REQ-F-002:** The system records processing status and failures.
- **REQ-F-003:** Authorized users can search document content.
- **REQ-F-004:** Results identify their source and page or section.
- **REQ-F-005:** Authorized users can request source-backed answers.
- **REQ-F-006:** A GM can mark campaign content as GM-only.

## Quality

- **REQ-Q-001:** The local environment starts with documented commands.
- **REQ-Q-002:** Search indexes are rebuildable projections.
- **REQ-Q-003:** Build logic is not exclusive to one CI provider.
- **REQ-Q-004:** Domain rules are testable without a full application context.

## Security, privacy, and copyright

- **REQ-SEC-001:** The core application enforces authorization.
- **REQ-SEC-002:** Unauthorized content is removed before retrieval context exists.
- **REQ-SEC-003:** GM-only content cannot enter player prompts, logs, or answers.
- **REQ-SEC-004:** Imported documents are untrusted input.
- **REQ-SEC-005:** Secrets and private imports stay out of public repositories and issues.
- **REQ-LIC-001:** Public demos use only original, synthetic, public-domain, or
  suitably licensed material with required attribution.

