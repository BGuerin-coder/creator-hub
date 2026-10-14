# creator-hub

## Goal

Centralize everything a creator publishes on different social media (communication, shop, subscriptions, gifts) in one place, while avoiding the fees of each platform.

## Features

- Presents the creator (home page)
  - Brief
  - Photos
- Social Media
  - Youtube videos
  - Twitch reviews / clips
  - Instagram reels / posts
- Shopping
  - Checkout process
  - Shopping cart
  - Product list
  - Product detail
  - Promotion
  - Pack of products
- Participation
  - Subscription
  - Gift
  - Crowdfunding
  - Donation goal
- Acknowledgements
  - Showing donors (from any source)
- Planning
  - Show expected dates for the next publications / lives
- Publication
  - Blog
  - Articles
  - Comic
  - Poetry
- Admin
  - Analytics
  - Content management
  - Permission levels
- Contact
- Recommendation (to support other creators)

## Architecture

All important architecture decisions should be explained in an ADR (Architecture Decision Record) in the folder [docs/decisions](./docs/decisions/).

| ADR                                                                 | Title                              | Status   |
| ------------------------------------------------------------------- | ---------------------------------- | -------- |
| [0001](./docs/decisions/0001_modular_monolith_vs_micro_frontend.md) | Modular monolith vs micro frontend | Accepted |
| [0002](./docs/decisions/0002_framework_frontend.md)                 | Frontend framework (Nuxt)          | Accepted |
| [0003](./docs/decisions/0003_public_sensitive_zones.md)             | Public and sensitive zones         | Proposed |
| [0004](./docs/decisions/0004_payment.md)                            | Payment provider                   | Proposed |
| [0005](./docs/decisions/0005_bdd.md)                                | Databases                          | Proposed |

## Stack

- Architecture: modular monolith — [ADR 0001](./docs/decisions/0001_modular_monolith_vs_micro_frontend.md)
- Frontend: [Nuxt](https://nuxt.com/docs/4.x/getting-started/installation) — [ADR 0002](./docs/decisions/0002_framework_frontend.md)
- Containers: Docker
- CDN / exposure: Cloudflare (free plan); the zone split and reverse proxy are only proposed — [ADR 0003](./docs/decisions/0003_public_sensitive_zones.md) (Proposed)
- Database: not decided yet — [ADR 0005](./docs/decisions/0005_bdd.md) (Proposed)
- Payment provider: not decided yet — [ADR 0004](./docs/decisions/0004_payment.md) (Proposed)

## Getting started

Requires Node 22 (`nvm use`) and [pnpm](https://pnpm.io/).

```bash
pnpm install
pnpm dev
```

The app is served on http://localhost:3000.

## Modules

Each module is a Nuxt layer in `layers/<name>/` (lowercase) and exposes a single access point, `api.ts` — [ADR 0001](./docs/decisions/0001_modular_monolith_vs_micro_frontend.md).

## Principles

### Secure by Design

A module should be limited to its scope, so that a compromised module cannot compromise the rest of the application.

### Simple before flexible

Flexibility comes at the cost of complexity. Any added flexibility must be clearly justified against a simpler solution.

### Design mobile-first

A small screen forces clarity about what's essential, and the result scales up more easily than a desktop design scales down.

### Accessibility

Every feature should be usable by people with disabilities. Accessibility benefits everyone, not just them.

### Resilient

If a module fails, it should not take down the rest of the application. The same applies to the UI: an error should degrade gracefully instead of breaking the whole page.

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for the guidelines, the ADR workflow and the labels.
