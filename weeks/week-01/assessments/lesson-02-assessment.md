# Assessment — Lesson 02: Capacity Estimation (QPS)

## Questions
Given:
- 2 million daily active users
- 20 short URLs opened per user per day
- Peak traffic multiplier of 4×

Calculate daily requests, average QPS, and estimated peak QPS.

## My original attempt
1. `2 million × 40 = 40 million req/day`
2. `40,000,000 ÷ (24 × 60 × 60)`
3. `4 × QPS = 4 × (40,000,000 ÷ (24 × 60 × 60))`

## Review and feedback
There was a small written multiplication slip in the first line: the multiplier should be **20**, not 40. However, the final daily request total (40 million) was correct.

The formulas in Q2 and Q3 were correct.

## Corrected solution
### 1. Daily requests
`2,000,000 × 20 = 40,000,000 requests/day`

### 2. Average QPS
`40,000,000 ÷ 86,400 ≈ 463 QPS`

### 3. Peak QPS
`463 × 4 ≈ 1,852 QPS`

## Outcome
- Daily requests: **40 million**
- Average QPS: **≈ 463**
- Estimated peak QPS: **≈ 1,852**

Score: **3 / 3** for the calculation method (informal coaching score; small notation slip noted).

## Reflection
I learned how to translate daily user activity into average and peak requests per second. I should keep assumptions and units visible in calculations and double-check multipliers.
