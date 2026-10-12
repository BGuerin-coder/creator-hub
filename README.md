# creator-hub

## Goal

Centralize all the content related to a creator using different social media for the communication, the shopping part, the subscriptions / gifts while avoiding fees from each platform.

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
  - Showing donator (from any source)
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

All important decisions architecture should be explained in an ADR (Architecture Decision Record) in the folder [docs/decisions](./docs/decisions/).

- [Modular Monolith](./docs/decisions/0001_modular_monolith_vs_micro_frontend.md)

## Stack

- [Nuxt](https://nuxt.com/docs/4.x/getting-started/installation)

## Dependencies

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
