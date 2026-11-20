# Chat Application

## Problem
Support one-to-one messaging and offline delivery.

## Functional scope
- [ ] Send and receive messages
- [ ] Conversation history
- [ ] Delivery/read receipts
- [ ] Offline message handling

## Design concerns
- [ ] WebSocket connections
- [ ] Message ordering
- [ ] Fanout
- [ ] Presence
- [ ] Connection server failure

## Deliverables
- [ ] Sequence diagrams
- [ ] Data model
- [ ] Connection architecture
- [ ] Ordering and delivery guarantees

## Design review questions
- What assumptions did I make?
- What is the critical request or event path?
- What fails first as traffic grows 10x?
- What data can be stale, and for how long?
- How does the system recover from partial failure?
- Which parts are intentionally simple for this learning project?
