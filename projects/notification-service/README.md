# Notification Service

## Problem
Deliver email, SMS, and push notifications asynchronously.

## Functional scope
- [ ] Accept notification request
- [ ] Queue and process jobs
- [ ] Retry transient failures
- [ ] Track delivery status
- [ ] Dead-letter failed jobs

## Design concerns
- [ ] At-least-once delivery
- [ ] Idempotency
- [ ] Provider failure
- [ ] Consumer lag
- [ ] Priority queues

## Deliverables
- [ ] Event flow
- [ ] Retry policy
- [ ] Idempotency strategy
- [ ] DLQ design
- [ ] Metrics and alerts

## Design review questions
- What assumptions did I make?
- What is the critical request or event path?
- What fails first as traffic grows 10x?
- What data can be stale, and for how long?
- How does the system recover from partial failure?
- Which parts are intentionally simple for this learning project?
