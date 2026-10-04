# Public and sensitive zones

## Status

Proposed - 2026/10/04

## Context

- Secure by design: a compromised part of the application must not compromise the rest.
- Payment data and transactions should be isolated from public content (public zone and sensitive zone).
- One developer, working on the project part-time alongside a full-time job.
- Time is limited for development, maintenance, support, tests and CI/CD.
- Simplicity and fast setup are preferred over flexibility that requires operational effort.

## Decision

Cloudfare should be used to block any DDos attacker since it's a matter of integration. 

In order to match the isolation, we will have two separated instance of postgresql, one to manage the data for the payment module and the other for the rest. We should communicate with 

## Consequences

### Benefits

- Cloudfare is easily configurable.
- With Cloudfare we didn't reinvent the wheel.
- Cloudfare is regularly updated and maintained with the last attack.

### Cons

- Cloudfare as dependency and should updated regularly

## Alternatives considered

- Building our own "Cloudfare" protection but it will be too costy to implement for one person.  

## Revisit triggers

- If Cloudfare is compromised or not maintain anymore, building our own solution, could be considered.
- If the team increase and we can have someone on this subject.
- If the cost is not a problem anymore, it could be considered to take the pro version in order to benefit to the "Lossless Image Optimization", and "Accelerated Mobile Pages (AMP)".


## Sources

> (New) I think that section could help to understand the decision

- Cloudfare documentation, [Protect your origin server](https://developers.cloudflare.com/fundamentals/security/protect-your-origin-server/)
- [Cloudfare plans](https://www.cloudflare.com/plans/#application-services)