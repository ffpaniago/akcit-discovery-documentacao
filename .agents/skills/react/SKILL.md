---
name: react
description: Build or review React and Next.js interfaces with explicit state, accessible components, and data access through the project BFF.
---

# React

Use this skill for React/Next.js screens, components, routing, UI state, and
front-end data contracts. Read `docs/react.md` and
`docs/descricao-sistema.md` before changing an architectural boundary.

## Component design

- Give each component one visible responsibility and a clear data contract.
- Keep presentation components free of direct API calls and business rules.
- Keep state local unless another component genuinely owns or needs it.
- Prefer explicit props and typed view models over leaking domain/provider types.
- Keep loading, error, empty, partial, and success states visible in the design.
- Preserve keyboard access, semantic HTML, focus behavior, and useful labels.

## Data boundary

- The front-end calls only the BFF.
- Never call a domain service or external provider from browser code.
- Treat the BFF response as a versioned contract; do not silently depend on
  undocumented fields or provider-specific details.
- Use the server/client boundary deliberately in Next.js and avoid moving
  secrets or privileged operations into client code.

## Workflow

1. Identify the route, layout, owner, and user-visible states.
2. Define the screen view model and the Front–BFF contract before wiring data.
3. Implement the smallest component structure that expresses the states.
4. Add tests for rendering, interaction, accessibility-critical behavior, and
   contract failures relevant to the screen.
5. Check tenant scope and personal-data handling in loading, caching, and URLs.

## Review questions

- Is business logic duplicated in the component instead of owned by the domain?
- Does client code expose a secret, privileged token, or external API detail?
- Can stale or cross-tenant data appear because of a cache or shared state?
- Are errors actionable without exposing internal implementation details?
- Is a new dependency worth its maintenance cost for the team?
