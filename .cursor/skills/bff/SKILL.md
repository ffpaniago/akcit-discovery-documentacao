---
name: bff
description: Design, implement, or review a Node.js/TypeScript BFF that adapts domain services for a web front-end without taking ownership of domain rules.
---

# BFF

Use this skill when a task changes a Backend-for-Frontend boundary, endpoint,
adapter, payload, error mapping, authentication context, or contract consumed
by a web front-end. Do not use it for domain rules or direct database design.

## Responsibilities

- Aggregate data from domain services and external integrations when needed.
- Adapt provider/domain models into stable front-end models.
- Reduce payloads to what the screen needs.
- Propagate the authenticated tenant/user scope to downstream calls.
- Define explicit loading, empty, partial, and error responses.
- Keep provider details, credentials, and provider-specific errors inside the BFF.

## Boundaries

- Front → BFF is allowed; front → domain or third party is prohibited.
- BFF → domain service and external integration is allowed.
- BFF → domain database is prohibited.
- Business invariants belong to the domain service, not to route handlers.
- If the Front–BFF contract changes, treat it as an architectural change:
  document compatibility, versioning, migration, and acceptance criteria.

## Workflow

1. Read `docs/descricao-sistema.md` and identify facts, hypotheses, and gaps.
2. Name the responsibility that remains in the front, BFF, and domain service.
3. Specify the request, response, errors, tenant scope, and compatibility policy.
4. Isolate external providers behind an adapter owned by the BFF.
5. Validate input at the boundary and use allowlisted downstream targets.
6. Add contract tests and tests for authorization, provider failure, timeout,
   empty data, and partial data when those states are in scope.
7. Record an ADR when the boundary, dependency, or contract changes.

## Review questions

- Did the BFF acquire a business decision that belongs in the domain service?
- Does any provider type, URL, error, or credential leak to the front?
- Can a request cross tenant boundaries through an ID, filter, or cache key?
- Is the downstream timeout and failure translated into a stable API response?
- Is every new operation and dependency justified for a small team?
