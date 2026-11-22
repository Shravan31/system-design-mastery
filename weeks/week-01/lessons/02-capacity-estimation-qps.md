# Lesson 02 — Capacity Estimation: QPS

## 1. What is capacity estimation?
Capacity estimation uses reasonable assumptions and simple calculations to approximate the load and resource needs of a system. It helps us reason about scale before choosing infrastructure.

## 2. Latency vs throughput
- **Latency:** time taken for one request or operation to complete.
- **Throughput:** number of operations completed per unit time (such as requests per second).

Restaurant analogy: latency is how long one customer waits for their order; throughput is how many customers the restaurant serves in an hour.

## 3. QPS
QPS means queries/requests per second. In this exercise we use it as requests per second (RPS).

There are:
- 60 seconds per minute
- 60 minutes per hour
- 24 hours per day
- **86,400 seconds per day**

## 4. Useful formulas
**Daily requests**
`Daily requests = DAU × requests per active user per day`

**Average QPS**
`Average QPS = daily requests ÷ 86,400`

**Estimated peak QPS**
`Peak QPS = average QPS × peak traffic multiplier`

Peak multiplier is an assumption representing how much busier a peak period may be than the daily average. Real traffic is not perfectly uniform, and actual peak traffic should be measured when data is available.

## 5. Worked example: URL shortener
Assumptions:
- Daily active users (DAU): 1,000,000
- Redirects per active user per day: 10
- Peak multiplier: 5

Daily requests:
`1,000,000 × 10 = 10,000,000 redirects/day`

Average QPS:
`10,000,000 ÷ 86,400 ≈ 116 requests/second`

Peak QPS:
`116 × 5 ≈ 580 requests/second`

These are illustrative estimates, not measured production traffic or a benchmark.

## 6. Assessment example
Given:
- DAU = 2,000,000
- Redirects per user per day = 20
- Peak multiplier = 4

Daily requests:
`2,000,000 × 20 = 40,000,000 requests/day`

Average QPS:
`40,000,000 ÷ 86,400 ≈ 463 QPS`

Estimated peak QPS:
`463 × 4 ≈ 1,852 QPS`

## 7. Key takeaways
- Start with explicit assumptions.
- Convert daily volume to per-second load to make it easier to reason about service capacity.
- Average QPS is not the same as peak QPS.
- Peak multiplier is an assumption; actual traffic patterns may differ.
- These estimates help guide design. They do not alone tell us how many servers or database instances we need; that requires performance characteristics and testing.

## 8. Common mistakes
- Forgetting the number of seconds in a day (86,400).
- Confusing daily requests with requests per second.
- Treating peak traffic as the average.
- Using assumptions as if they were measured facts.
- Picking server counts before estimating workload or benchmarking.

## 9. My understanding
Explain latency, throughput, average QPS, and peak QPS in your own words.

## 10. Resources
- [System Design Primer](https://github.com/donnemartin/system-design-primer)
- [Free System Design](https://freesystemdesign.com/)
