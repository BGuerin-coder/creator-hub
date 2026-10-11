# Payment provider

## Status

Proposed - 2026/10/06

## Context

Payment data must stay in the sensitive zone (see [ADR 0003](./0003_public_sensitive_zones.md)). The application should never receive, use or store banking information.

## Decision

The payment module will rely on a payment provider such as Stripe or Mollie, which hosts the payment page and handles card data. The provider is still to be chosen.

## Consequences

### Benefits

- With a hosted payment provider, the application never sees or stores banking information.

### Cons

- Another dependency to keep up to date.
- The webhook must be protected against forged or man-in-the-middle calls: verify the signature (Stripe) or re-fetch the payment status from the provider's API (Mollie).

## Alternatives considered

- Building our own payment solution, which would require handling banking information carefully.

## Open questions

- Which provider is actually chosen, Stripe or Mollie, and why (fees, EU focus, ease of integration for one developer)?
- Does the chosen provider support recurring payments well enough for the subscription feature, not just one-off donations and purchases?
- Where and how is the amount computed and validated server-side, so the client can never set its own price?
- What exactly do we store about a transaction in our own database versus what stays only in the provider's records (linked to the 0005 open question on whether we need our own transaction storage)?
- How are refunds and disputes handled, and who can trigger them (admin only?)?
- What is the idempotency and retry strategy for both creating a payment and processing its webhook?

## Revisit triggers

- If the chosen provider stops being maintained, or its pricing no longer fits the project.

## Sources

- [Mollie - Accepting Payments](https://docs.mollie.com/docs/accepting-payments)
- [Mollie - Webhooks](https://docs.mollie.com/reference/webhooks)
