# News Feed

## Problem
Generate personalised feeds from followed accounts.

## Functional scope
- [ ] Follow/unfollow
- [ ] Create post
- [ ] Fetch feed
- [ ] Pagination

## Design concerns
- [ ] Fanout on write/read
- [ ] Celebrity users
- [ ] Ranking
- [ ] Feed cache
- [ ] Consistency

## Deliverables
- [ ] Two strategy comparison
- [ ] Feed generation flow
- [ ] Hot-user analysis
- [ ] Capacity estimate

## Design review questions
- What assumptions did I make?
- What is the critical request or event path?
- What fails first as traffic grows 10x?
- What data can be stale, and for how long?
- How does the system recover from partial failure?
- Which parts are intentionally simple for this learning project?
