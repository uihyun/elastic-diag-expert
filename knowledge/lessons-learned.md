# Lessons Learned

**This file is a template.** Copy it to your own Claude Project's Files and add your team's lessons there. Real case insights should stay in your Project's Files — not in this public repo.

The diagnostic expert uses this format when generating lessons-learned summaries. The example below shows how entries should look.

---

## [2026-04-02] Case: Template example — how entries should look

**Environment**: ES 8.12.0, self-managed, 12 data nodes, 3 master nodes
**Problem**: User reported intermittent search timeouts during peak hours
**Root Cause**: Old GC running every 8 seconds due to 15,000 shards across 12 nodes (1,250/node). Each shard consumes ~25MB heap overhead, totaling ~366GB across the cluster against 32GB heap per node.
**Key Insight**: The user had set `number_of_shards: 5` as a default for all indices, including tiny daily indices with <100MB of data. 3,000+ indices × 5 shards × 2 (primary + replica) = 30,000 shards. Most shards were under 1MB.
**Detection Rule**: When >50% of shards are under 1MB AND total shards/node > 800, flag as "severe oversharding from default shard count on small indices" — not just generic oversharding.
**Resolution**:

1. Created ILM policy with `max_primary_shard_size: 50gb` rollover to prevent future tiny indices
2. Used reindex + shrink to consolidate historical indices: `POST _reindex { "source": {"index": "logs-2024.01.*"}, "dest": {"index": "logs-2024.01-consolidated"} }`
3. Set `index.number_of_shards: 1` as index template default for small-volume indices
4. Result: Shards dropped from 15,000 to 2,400, heap pressure resolved, old GC stopped

---

<!--
Add new entries above this line.
Follow the template format.
All entries must be reviewed before merging.
-->
