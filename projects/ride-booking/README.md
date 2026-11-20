# Ride Booking

## Problem
Match riders and drivers and track trips.

## Functional scope
- [ ] Request ride
- [ ] Find nearby drivers
- [ ] Accept/decline
- [ ] Track trip
- [ ] Complete/cancel

## Design concerns
- [ ] Geospatial index
- [ ] Location freshness
- [ ] Concurrent assignment
- [ ] Trip state machine
- [ ] Surge and peak load

## Deliverables
- [ ] State machine
- [ ] Matching flow
- [ ] Location architecture
- [ ] Double-assignment prevention

## Design review questions
- What assumptions did I make?
- What is the critical request or event path?
- What fails first as traffic grows 10x?
- What data can be stale, and for how long?
- How does the system recover from partial failure?
- Which parts are intentionally simple for this learning project?
