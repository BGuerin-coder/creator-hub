# Public and sensitive zones

## Status

Updated  - 2026/10/06
Proposed - 2026/10/04

## Context

- Secure by design: a compromised part of the application must not compromise the rest.
- Payment data and transactions should be isolated from public content (public zone and sensitive zone).
- One developer, working on the project part-time alongside a full-time job.
- Time is limited for development, maintenance, support, tests and CI/CD.
- Simplicity and fast setup are preferred over flexibility that requires operational effort.

## Decision

Two zones will be set up: a public zone (content, blog, contact, presentation, videos, etc.) and a sensitive zone (payment, subscription management, transactions).

The payment webhook is the only flow from the public zone to the sensitive zone, and the only aggregated, anonymised data flows back out of it.

The sensitive zone is only reachable through a reverse proxy and is not directly exposed.

As stated in [ADR 0001](./0001_modular_monolith_vs_micro_frontend.md), we keep a single CI/CD, but the payment module is excluded from it to be clearly isolated. This is intended.

Cloudflare blocks DDoS attacks and protects the public zone, since it is a matter of integration.

The payment provider is defined in [ADR 0004](./0004_payment.md), and the databases in [ADR 0005](./0005_bdd.md).

## Consequences

### Benefits

- If a public page is compromised, the attacker cannot access the sensitive information.
- Cloudflare is easily configurable, and we don't reinvent the wheel.
- Cloudflare is regularly updated against the latest attacks.

### Cons

- The payment module must always be up and healthy.
- Cloudflare is a dependency and must be updated regularly.
- A specific CI/CD for the sensitive zone (Docker x2, deployment x2, variables x2).

## Alternatives considered

- Building our own Cloudflare-like protection would be too costly to implement for one person.

## Open questions

- How does the public zone authenticate when it asks the sensitive zone to create a payment (service token, internal network only, mTLS)?
- What is the exact list of endpoints allowed between the two zones, beyond the webhook?
- Where does the admin area live (a subdomain of the public zone, or its own zone), and what can it read from the sensitive zone?
- How should the public zone behave if the sensitive zone is unavailable (degrade gracefully, cache the last known donation progress)?
- Do we need to store transactions ourselves at all, or could the payment provider's own records be enough? This affects whether the sensitive zone needs its own database.
- What is the actual threat model for the boundary between the two zones (for example, a STRIDE pass on the "create payment" flow, and the SSRF risk from the public zone)?

## Revisit triggers

- If Cloudflare is compromised or no longer maintained, building our own solution could be considered.
- If the team grows, someone could be dedicated to this subject.
- If the cost is no longer a problem, the Pro plan could be considered for "Lossless Image Optimization" and "Accelerated Mobile Pages (AMP)".
- If the team grows enough, an expert could be hired to handle the security part exclusively.

## Sources

> (New) I think that section could help to understand the decision

- Cloudflare documentation, [Protect your origin server](https://developers.cloudflare.com/fundamentals/security/protect-your-origin-server/)
- [Cloudflare plans](https://www.cloudflare.com/plans/#application-services)
- [Open Security Architecture - Patterns](https://opensecurityarchitecture.org/patterns/sp-017/)