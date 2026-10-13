# Contributing

## Guidelines

### Process / Git

- An issue is closed by a PR (`Closes #N`), no commit on main directly.
- Cross-module imports must go through the module's `api.ts`. A lint rule will enforce this, see [#12](https://github.com/BGuerin-coder/creator-hub/issues/12).

### ADR workflow

- An ADR file is named `000X_short_name.md`, numbered sequentially, lowercase with underscores. Start from [`_0000_template.md`](./docs/decisions/_0000_template.md).
- Status starts at `Proposed` (with a date). It becomes `Accepted` (with a date) once the decision is actually made, and later `Deprecated` or `Superseded` (with a date, and the replacing ADR) if replaced. Do not add `Updated` entries: the git history already tracks edits.
- Unresolved points go in the ADR's "Open questions" section instead of being guessed at; they don't block `Proposed`.

### Issues & Milestones

- A milestone is a demonstrable vertical slice, not a theme.
- Size a milestone by realistic time (roughly 4 to 6 weeks of part-time work), not by a feature list.
- Split a milestone past ~15-20 issues, merge it with the next one below 3-4.
- An issue fits in one work session; needing more than one PR is a sign to split it.
- Write a one-sentence "done when..." for each issue; split it if that sentence needs "and".
- Title an issue by its observable outcome ("Show the donation goal progress bar on the homepage"), not by a module name ("Donations").

### Security

- When a permission should be defined, use the lowest one that permits the action.
- Do not commit any secret or any sensitive information.

### Simple before flexible

- Complexity should be justified in an ADR.

### Design mobile-first

- Use `min-width` for media and container queries instead of `max-width`.
- Test each page or component on a 375px wide screen before testing on desktop.
- Each clickable / touchable element should be at least `44x44px`.

### Accessibility

- Respect WCAG AA color contrast (4.5:1 for text).
- Respect `prefers-color-scheme` and `prefers-reduced-motion`.
- Each `img` should have an `alt` attribute.
- The navigation should be doable using only the keyboard.

### Resilient

- Each API and dependency call must handle its error explicitly (`try/catch`, or the `error` returned by `useFetch`), with a clear fallback or error state. It should never fail silently.

### Dependency

- Before adding a dependency, check if it is really needed over the existing stack or a native feature.

### Tests

- Automated tests are mandatory for the payment and auth flows; optional elsewhere for now.

### Performances / images

- Images are served in a modern format `(WebP/AVIF)` and lazy-loaded below the fold.

### Labels

#### Type

- `type • feature` new user-facing capability
- `type • enhancement` improvement to an existing feature, not a brand new one
- `type • bug` something broken that should already work
- `type • chore` maintenance with no user-facing effect: deps, tooling, refactor
- `type • docs` documentation only
- `type • security` security fix or hardening

#### Area

- `area • frontend` shared UI, layout, design system
- `area • admin` analytics, content management, permission levels
- `area • shop` catalog, cart, checkout
- `area • participation` subscription, gift, crowdfunding, donation goal
- `area • payment` payment provider integration, webhook, sensitive zone
- `area • social-media` Youtube, Twitch, Instagram integration
- `area • publication` blog, articles, comic, poetry
- `area • planning` upcoming publication / live dates
- `area • infra` Docker, CI/CD, hosting
- `area • architecture` ADR-related change

#### Priority

- `priority • urgent` only to jump the queue, e.g. a security issue or a production bug

#### Status

- `status • blocked` waiting on an architecture decision or an external dependency
