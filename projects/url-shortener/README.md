# URL Shortener

## Problem
Create short links and redirect reliably.

## Functional scope
- [ ] Create short URL
- [ ] Redirect to original URL
- [ ] Optional expiry and custom alias
- [ ] Basic analytics

## Design concerns
- [ ] Unique ID strategy
- [ ] SQL vs NoSQL
- [ ] Redis cache
- [ ] Hot-key handling
- [ ] Abuse and rate limiting

## Deliverables
- [ ] API spec
- [ ] Schema and indexes
- [ ] Architecture diagram
- [ ] Capacity estimate
- [ ] Cache strategy
- [ ] Failure analysis

## Design review questions
- What assumptions did I make?
- What is the critical request or event path?
- What fails first as traffic grows 10x?
- What data can be stale, and for how long?
- How does the system recover from partial failure?
- Which parts are intentionally simple for this learning project?
