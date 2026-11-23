# Lesson 03 Assessment — Storage Estimation

## Exercise
Given:
- Users: 20 million
- Each user creates 5 short URLs per day
- Estimated storage per URL mapping: 500 bytes
- Assume a constant creation rate for 365 days and no deletion.

## My answers
1. **Records created per day:** 100 million
2. **Storage consumed per day:** 50 GB
3. **Storage after one year:** 18.25 TB

## Evaluation
**Score: 3/3 — all answers correct.**

### Check 1 — Daily records
20M users × 5 URLs/user/day = **100M URL records/day**.

### Check 2 — Daily storage
100M records × 500 bytes = 50,000,000,000 bytes ≈ **50 GB/day** (decimal units).

### Check 3 — Annual storage
50 GB/day × 365 days = 18,250 GB ≈ **18.25 TB/year**.

## Feedback and concepts reinforced
- Back-of-the-envelope estimation is a rough estimate, not a guarantee of exact production storage.
- Explicit assumptions (record size, creation rate, retention, days per year) make the estimate explainable and revisable.
- The 500-byte mapping size is an exercise assumption, not a universal database fact.
- Additional storage may be needed for indexes, backups, replication, logs, and operational headroom. Be careful not to double-count overhead already included in the 500-byte estimate.

## My takeaway
Back-of-the-envelope estimation gives us a reasonable way to estimate scale before we actually build the system. It will not be 100% accurate, but it helps us make rough estimates and guide decisions early.
