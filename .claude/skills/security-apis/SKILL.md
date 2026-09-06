---
name: security-apis
description: Design or review API and application security for authentication, authorization, tenant isolation, validation, secrets, and safe integrations.
---

# Security and APIs

Use this skill when an API, BFF, integration, data boundary, authentication
flow, or sensitive-data path is created or changed. It provides a review and
design checklist; it does not replace a product-specific threat model.

## Boundary review

- Identify assets, actors, trust boundaries, tenant scope, and the owner of each
  authorization decision.
- Authenticate at the appropriate boundary, then authorize every resource and
  operation using server-side scope; never trust an ID, role, or tenant from the
  browser alone.
- Keep front-end code free of secrets and privileged credentials.
- Validate shape, size, encoding, and allowed values before processing input.
- Use parameterized queries and safe serialization; do not build commands,
  queries, redirects, or provider URLs from unchecked input.
- Allowlist outbound hosts and protocols to reduce SSRF and unintended egress.

## API design

- Return stable error codes/messages without internal details, credentials,
  stack traces, or provider payloads.
- Version breaking changes and define compatibility for Front–BFF contracts.
- Apply rate and abuse controls where the context requires them; do not invent
  quotas, limits, or SLAs.
- Define idempotency for retried writes and protect webhooks with signature,
  replay, timestamp, and authorization checks when applicable.
- Redact personal data and tokens from logs, traces, URLs, and error responses.
- Protect sensitive responses from cross-tenant caching and accidental indexing.

## Workflow

1. Read the architecture document and list facts, hypotheses, and security gaps.
2. Map each endpoint's authentication, authorization, input validation, output,
   downstream calls, and failure behavior.
3. Check dependency and provider changes for contract and operational impact.
4. Add tests for unauthorized access, cross-tenant access, malformed input,
   replay/duplicate requests, secret leakage, and external failure as applicable.
5. Record unresolved decisions as lacunas and create an ADR for boundary or
   contract changes.

## Stop and ask for a decision

Do not silently choose an auth model, tenant-isolation strategy, retention rule,
or security exception when the required facts are missing. Record the gap and
the decision it blocks.
