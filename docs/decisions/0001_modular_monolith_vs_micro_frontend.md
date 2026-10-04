# Modular monolith vs Micro Frontend

## Status

Accepted - 2026/10/03

## Context

A structure should be chosen in order to organize the code. The code should be secure by design meaning that each part of the application should be clearly split and own only its part in a defined module. If one module is compromised, the scope should not compromise the rest of the application.

For now, there is only one developer with a full time job, the time is limited for the development, maintenance, support, tests, CI/CD, etc. With this in mind, we need a simple architecture that can quickly be set up. We should manage the front and the back in one place to reduce complexity.

## Decision

Modular monolith is a cheaper architecture with the benefit to have modules that can be isolated on demand if necessary and the CI/CD should be simpler to manage. Each module should have an appropriate (being logical with the goal of the feature) folder named in lowercase and have only one access point named `api.ts`.

## Consequences

### Benefits

- Having **less cost** for the infrastructure.
- Having **one CI/CD process** to manage and maintain.
- Having **everything in one place**, every module is easily discoverable.

### Cons

- _(main risk)_ Having **links between modules** making it really difficult to change, to evolve.
  To address that some rule should be set in order to prevent it, with a linter for instance.
- Having a **module that slows down the whole product**. Split the problematic module in its own flow.

## Alternatives considered

- **Micro Frontend** has been considered but since there is no appropriate team for each module, it's less valuable.
- **Microservices** has been considered but it increases the cost of the infra and complexifies the whole CI/CD without giving new benefits.

## Revisit triggers

- If the dev teams increase enough, the micro frontend could be reconsidered.
- If the cost of the infra is not an issue anymore, the microservices could be reconsidered.