# Lesson 03 — Storage Estimation

## 1. Why estimate storage?
Storage estimation helps us approximate how much data a system will accumulate as it grows. It is useful before choosing databases, storage tiers, or infrastructure. The estimate is rough and based on assumptions—not an exact prediction of production usage.

## 2. What we store in the URL shortener
Each URL mapping may contain:
- `short_code`
- `original_url`
- `created_at`

For a simplified exercise, we estimated raw field sizes:
- Short code: ~8 bytes
- Original URL: ~200 bytes (an assumption; real URLs vary)
- Timestamp: ~8 bytes

That totals ~216 bytes before database-specific overhead. We rounded the working estimate to **500 bytes per mapping** to allow for overhead. This 500-byte figure is a convenient assumption, not a universal database row size.

## 3. Basic formula
`Total storage = number of records × estimated size per record`

Using a simplified decimal convention:
- 1 GB ≈ 1,000,000,000 bytes
- 1 TB ≈ 1,000 GB

## 4. Example scenarios at 500 bytes per mapping
- 10 million records: 10M × 500 bytes ≈ **5 GB**
- 100 million records: 100M × 500 bytes ≈ **50 GB**
- 1 billion records: 1B × 500 bytes ≈ **500 GB**

Assuming record size stays constant, a 10× increase in records results in a 10× increase in estimated storage.

## 5. Daily and annual growth exercise
Assumptions:
- Users: 20 million
- URLs created per user each day: 5
- Estimated storage per mapping: 500 bytes
- Retention: keep all mappings; no deletion
- Growth rate: constant for the full year; 365 days

Daily records:
`20M users × 5 URLs/user/day = 100M URL records/day`

Daily storage:
`100M × 500 bytes = 50,000,000,000 bytes ≈ 50 GB/day`

Annual storage:
`50 GB/day × 365 = 18,250 GB ≈ 18.25 TB/year`

This estimate is for the assumed mapping data and simplified per-record allowance. Actual total storage may be higher due to indexes, backups, logs, replication, database overhead, and free-space/headroom requirements. If the 500-byte estimate already included some overhead, avoid counting that overhead twice.

## 6. Replication consideration
If we keep three copies of a dataset estimated at 500 GB, the simple copy-based estimate is:
`500 GB × 3 = 1.5 TB`

Replication is only one factor. Indexes, backups, logs, storage headroom, and how the database implements replication affect the actual capacity requirement.

## 7. Back-of-the-envelope estimation
Back-of-the-envelope estimates use reasonable assumptions and simple arithmetic to approximate scale before building or benchmarking the system. The numbers are not expected to be exact. The value is in making assumptions explicit, checking the order of magnitude, and using the estimate to guide follow-up questions and design decisions.

## 8. Key takeaways
- Estimate a record's size using explicit assumptions.
- Multiply record size by the number of records.
- Project growth over time when creation rate and retention assumptions are known.
- Consider copies and additional storage needs—but understand what is already included in your estimate.
- Estimates inform design discussions; they don't independently prove a database will handle the workload.

## 9. Assessment
See [Lesson 03 Assessment](../assessments/lesson-03-assessment.md).

## 10. Selected resource
- [System Design Primer — Appendix](https://github.com/donnemartin/system-design-primer#appendix): review the Powers of Two table and Latency Numbers Every Programmer Should Know. Focus on building intuition for scale and relative latency; memorization is not required.
