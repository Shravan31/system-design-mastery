# Assessment — Lesson 01: Requirements Gathering

## Questions
1. Why are redirects more critical than link creation in this product?
2. If the database temporarily becomes unavailable, which functionality do you think should continue working, if any?
3. Suppose a user creates a short URL and the server crashes one second later. What must be true for that link not to be lost?
4. If we have 10 features requested by the product team, why shouldn't we build all 10 before launching?

## My original answers
### Q1
Redirection is more important because eventually the user wants to go to the correct destination he wished/picked for. So correct redirection is very important; our URL shortening should not change the original URL.

### Q2
Database is where we map the short URLs to the original URLs. If it becomes unavailable, we can't read/write to DB, so none of the functionality will continue working.

### Q3
The database where all the shortened URLs are stored should be persisted even after the server crash.

### Q4
Taking all the features at once will create unnecessary complexity, so we should bound the scope.

## Review and feedback
- **Q1 — Strong:** Correctly identified redirect correctness as core product value. An additional observation is that redirects may occur far more frequently than link creation, influencing future optimization.
- **Q2 — Reasonable for the initial architecture:** If requests depend on database access, creation and uncached redirects may fail during a database outage. A cache could later allow some redirects to continue; this is graceful degradation. The answer was based on the architecture known at that point.
- **Q3 — Correct:** Persistent storage should survive an application-process crash. A database outage or database failure is a distinct scenario from an application server crash.
- **Q4 — Strong:** Keeping MVP scope bounded reduces complexity, implementation effort, and testing burden.

## Outcome
Score: **3.5 / 4** (informal coaching score)

## Reflection
I understood that requirements should be clarified before architecture, that the redirect journey is central to the product, and that a bounded MVP is easier to design and evolve.
