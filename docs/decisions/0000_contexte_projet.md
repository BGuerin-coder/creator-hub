# Project context

## Team

- One developer, working on the project part-time alongside a full-time job.
- Time is limited for development, maintenance, support, tests and CI/CD.
- Simplicity and fast setup are preferred over flexibility that requires operational effort.

## Product

- A creator-centred hub gathering content, shopping, subscriptions, gifts and donations in one place, to avoid platform fees.
- Public pages (creator presentation, blog, articles, comics, poems, products) must be indexable: SEO matters.
- Modules (shop, blog, planning, donations, etc.) can be enabled or disabled, see [0001](./0001_modular_monolith_vs_micro_frontend.md).

## Security

- Secure by design: a compromised part of the application must not compromise the rest.
- Payment data and transactions should be isolated from public content (public zone and sensitive zone), see [0003](./0003_public_sensitive_zones.md).
- The admin area has its own authentication, with mandatory 2FA and strict rate limiting.
- Only aggregated, anonymised donation data is exposed outside the sensitive zone.

## Deployment

- Services are packaged as Docker containers.
- Cloudflare sits in front of the application (CDN, DDoS protection, hiding the origin IP).

## Decisions and their status

- [0001](./0001_modular_monolith_vs_micro_frontend.md): modular monolith. Accepted.
- [0002](./0002_framework_frontend.md): Nuxt for the frontend. Accepted.
- [0003](./0003_public_sensitive_zones.md): Public / sensitive zone split, payment provider, database setup, CDN and exposure: to be decided in dedicated ADRs.

## History

Created - 2026/10/03 - Add section Team, Product, Security, Deployment and Decisions and their status
Updated - 2026/10/04 - Adding ADR 0003