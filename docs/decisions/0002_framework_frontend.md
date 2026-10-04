# Framework Frontend

## Status

Accepted - 2026/10/03

## Context

- Public pages (creator presentation, blog, articles, comics, poems, products) must be indexable: SEO matters.
- Modules (shop, blog, planning, donations, etc.) can be enabled or disabled, see [0001](./0001_modular_monolith_vs_micro_frontend.md).
- One developer, working on the project part-time alongside a full-time job.
- Time is limited for development, maintenance, support, tests and CI/CD.
- Simplicity and fast setup are preferred over flexibility that requires operational effort.

## Decision

Using Nuxt is aligned with the goal of the application and the Modular Monolith. It will increase the SEO with SSR / SSG / ISR.

## Consequences

### Benefits

- Nuxt Layers make it easy to create modules and feature flag approach.
- Less complexity in the ecosystem
- Simpler learning curve
- Vue ecosystem

### Cons

- Less popular than Next.js
- No rules to respect the only entry point `api.ts` (from a module)

## Alternatives considered

- Next.js has been considered, but there is no equivalent to Nuxt Layers. React ecosystem.

## Revisit triggers

- If Next.js adds a native equivalent to Nuxt Layers, Next.js could be reconsidered.
- If the team needs to be increased and there is no profile for Nuxt.
- If Next.js has a new version simplifying the learning curve for newbies.
