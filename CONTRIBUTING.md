# Contributing to elastic-diag-expert

Thanks for helping make Elastic diagnostics analysis better for everyone.

## Ways to Contribute

### 1. Improve Analysis Rules

Found a threshold that's wrong? A check that's missing? A false positive that keeps coming up?

- Open a GitHub issue describing what should change and why
- Or submit a PR modifying `instructions.md` with clear reasoning

Examples of good rule improvements:

- "Shard size threshold of 50GB is too aggressive for frozen tier — suggest 100GB for frozen"
- "Missing check: `search.max_buckets` set too low causes aggregation failures"
- "GC pause threshold of 500ms triggers too many warnings on large heaps — scale with heap size"
- "Guardrail missing: should warn against X in Y environment"

### 2. Add Knowledge Files

Generic best practices, common patterns, or version migration guides that would help the analysis can be added to `knowledge/`.

Requirements:

- Must be generic and reusable — no customer-specific content
- No content from login-gated sources — reference them by title instead
- No customer data, credentials, or PII
- Markdown format preferred

### 3. Report Issues

If the diagnostic expert gave a wrong recommendation, missed something obvious, or behaved unexpectedly, open a GitHub issue describing:

- What you asked / what data you provided
- What the expert said
- What was wrong and what the correct answer should have been
- (Sanitize any customer data before posting)

## About Lessons Learned

The diagnostic expert will sometimes offer to summarize insights from an analysis session. These lessons learned are intended for your **Project's Files section**, not for this public repo. Real case insights almost always contain traces of customer-specific information, even after sanitization.

The `knowledge/lessons-learned.md` file in this repo is a **template and example only** — it shows the format so you know what to expect when the expert generates one. Your actual lessons learned should be:

1. Reviewed by you for accuracy and data safety
2. Added to your own Claude Project's Files section
3. Shared within your team via your organization's internal channels

If you discover a genuinely generic insight that contains zero customer-specific information and would benefit all users (e.g., "ES 9.x changed the default behavior of setting X"), consider contributing it as an analysis rule improvement (option 1 above) rather than as a lessons-learned entry.

## Review Process

1. You open an issue or PR
2. Maintainer reviews for accuracy, generalizability, and data safety
3. If approved, merged
4. All users benefit when they update their Project instructions

## Data Safety

- **Never** include customer data, credentials, IP addresses, cluster names, or PII in issues, PRs, or any contribution
- When describing a scenario, use generic examples ("a 12-node cluster with 8.x") not real ones
- When in doubt about whether something is safe to share publicly, don't share it
