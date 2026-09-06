---
name: postgres
description: Design or review PostgreSQL schema, access, tenant isolation, and operations owned by the domain service. Use when the task mentions Postgres, SQL, migrations, indexes, RLS, or domain persistence.
---

# PostgreSQL

Use this skill only when the PROBLEMA already declares persistence, or when
the task is to record the gap that blocks choosing a store. Do not introduce
PostgreSQL to satisfy a generic “we will need a database” hypothesis.

## Ownership

- The domain service owns the data, the schema, and the queries.
- The BFF never connects to the domain database.
- The front never sees SQL, table names, or driver errors.

## Design

- Model around invariants and tenant scope, not around screen payloads.
- Prefer explicit foreign keys, constraints, and typed columns over implicit
  conventions in application code.
- Isolate tenants in every query and, when the PROBLEMA requires it, consider
  row-level security as a defense in depth — do not silently choose RLS.
- Use parameterized queries only. Never concatenate identifiers or values
  from untrusted input into SQL.
- Migrations are architectural when they change a contract the BFF or front
  depends on indirectly; document compatibility.

## Operations

- Do not invent pool size, RPO/RTO, storage cost, or query SLAs. Propose how
  to measure them.
- Justify indexes by access path declared in the problem, not by speculation.
- Extensions, logical replication, and extra stores add operational cost for a
  small team; treat them as out-of-stack until justified.

## Workflow

1. Confirm persistence is in the PROBLEMA. If not, register the lacuna.
2. Name what stays in domain vs BFF vs front.
3. Propose schema and access only for the declared use.
4. List tests: constraint, tenant isolation, migration rollback/forward,
   and failure without leaking SQL to the BFF contract.
5. Record an ADR when the store, isolation model, or ownership changes.
