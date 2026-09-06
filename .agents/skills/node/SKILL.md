---
name: node
description: Implement or review Node.js and TypeScript services with explicit boundaries, failure handling, tests, and operational behavior.
---

# Node.js

Use this skill for Node.js/TypeScript services, workers, BFF modules, integrations,
and runtime behavior. Do not introduce persistence, queues, caches, or frameworks
unless the problem declares the need and the operational cost is documented.

## Service design

- Keep transport, application orchestration, domain rules, and integrations
  distinguishable even when they live in one deployable service.
- Validate untrusted input at the boundary and use typed internal models.
- Keep configuration external, explicit, and validated at startup.
- Make timeouts, cancellation, retries, and idempotency intentional for every
  remote call; retry only operations safe to repeat.
- Map internal failures to stable public errors without exposing stack traces,
  secrets, SQL, tokens, or provider responses.
- Shut down gracefully: stop accepting work, finish or cancel in-flight work,
  then close connections within the runtime's lifecycle policy.

## Reliability and operations

- Preserve tenant/user scope through every downstream call and cache key.
- Log identifiers useful for correlation, but redact personal and secret data.
- Do not claim latency, throughput, cost, or availability without measurement.
- If observability is absent, record it as a gap and propose the smallest useful
  verification rather than inventing instrumentation requirements.
- Prefer a dependency already in the stack; justify a new one by quality
  attribute, constraint, and maintenance cost.

## Workflow

1. Read the project architecture document and separate facts from hypotheses.
2. Identify the service boundary, public contract, owners, and forbidden dependencies.
3. Implement the narrowest change with typed inputs and explicit errors.
4. Test success, validation failure, authorization failure, timeout, dependency
   failure, retry behavior, and shutdown where applicable.
5. Update the contract, ADR, or memory record when the change affects architecture.
