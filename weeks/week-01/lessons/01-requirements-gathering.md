# Lesson 01 — Requirements Gathering

## 1. What is requirements gathering?
Requirements gathering is the process of clarifying what a system should do, who it serves, and what constraints it must satisfy before choosing architecture or implementation details.

## 2. Why do we do it?
A design cannot be judged without knowing the problem it is meant to solve. Requirements establish scope and help prioritize engineering work. They prevent us from designing features or infrastructure that are unnecessary for the initial product.

## 3. Our example: URL shortener
A user submits a long URL. The service creates a short link. When someone opens the short link, the service redirects them to the original destination.

Example:
- Original URL: `https://www.example.com/products/electronics/mobile/iphone?campaign=summer`
- Short URL (example): `https://short.ly/aB92xK`

The short code identifies the stored mapping to the original URL.

## 4. Scope (MVP)

### Included
- Create a short URL from a valid long URL.
- Redirect a visitor from a short URL to the original destination.
- Ensure each short code maps to one destination.
- Persist mappings so they survive application restarts.

### Excluded for the initial version
- Custom aliases
- User accounts
- Analytics dashboard
- Expiration settings
- QR code generation

## 5. Functional requirements (FR)
Functional requirements describe what the product must do.

- **FR-1 — Create short URL:** Accept an original URL and return a short URL.
- **FR-2 — Redirect:** When a short URL is requested, find the original URL and redirect the visitor.
- **FR-3 — Uniqueness:** A short code must identify exactly one stored URL mapping.
- **FR-4 — Persistence:** Created mappings remain available after an application server restart.

## 6. Non-functional requirements (NFR)
Non-functional requirements describe quality attributes and operational expectations—how well the system should work.

| Quality attribute | Meaning for our service |
|---|---|
| Low latency | Redirects should happen quickly |
| Availability | Users should be able to access the service reliably |
| Scalability | Handle growth in users and traffic |
| Durability | Created mappings should not be lost |
| Security | Validate inputs and protect against abuse and unsafe destinations |

These are initial qualitative goals. Later, we should define measurable targets (for example, redirect latency percentiles and availability targets) rather than leaving terms like “fast” vague.

## 7. Prioritization
Redirecting and link creation are the core product functions. Redirects are especially important because they are the main value delivered to people opening the links. Analytics may be useful, but the core service works without it. Keeping the MVP small makes it easier to implement, test, and reason about.

## 8. Failure thinking
Initial assumption: if the database is unavailable, link creation and redirects that require a database lookup may fail. A future cache could allow some redirects to continue for mappings already cached. This is graceful degradation: limited functionality continues during a failure instead of everything failing.

A server process crash and a database outage are different failure cases. Persistent storage is intended to keep mappings beyond the life of an application process.

## 9. Key takeaways
- Clarify the problem before drawing architecture.
- Separate functional requirements from non-functional requirements.
- Keep the initial scope bounded.
- Prioritize the core user journey.
- Consider failure cases early.
- Make vague quality goals measurable when possible.

## 10. My understanding
Write a short explanation in your own words without looking at these notes.

## 11. Resources
- [Free System Design](https://freesystemdesign.com/)
- [System Design Primer](https://github.com/donnemartin/system-design-primer)
