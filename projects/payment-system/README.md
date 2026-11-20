# Payment System

## Problem
Model safe payment initiation, processing, refunds, and reconciliation.

## Functional scope
- [ ] Initiate payment
- [ ] Track status
- [ ] Handle timeout
- [ ] Refund
- [ ] Reconcile records

## Design concerns
- [ ] Idempotency
- [ ] Saga/outbox
- [ ] Provider integration
- [ ] Ledger correctness
- [ ] Duplicate charge prevention

## Deliverables
- [ ] State machine
- [ ] Sequence diagrams
- [ ] Failure matrix
- [ ] Reconciliation plan
- [ ] Security considerations

## Design review questions
- What assumptions did I make?
- What is the critical request or event path?
- What fails first as traffic grows 10x?
- What data can be stale, and for how long?
- How does the system recover from partial failure?
- Which parts are intentionally simple for this learning project?
