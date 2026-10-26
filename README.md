# hitl-qa-audit-50-posts

A human QA audit of 50 labelled social media posts, using a 6-point checklist.

> **Data note:** The 50 posts are **synthetic practice data** written for training, not real social media data. This is a simulated QC audit, not a production project. No AI model was tested. I audited labels and priority flags that were already assigned.

## What I did
Acting as QC, I checked each post's label (Complaint, Inquiry, Praise, Spam) and priority flag against six criteria, marked Pass or Fail, and wrote a reason for every Fail.

## Audit checklist

| ID | Criterion | What it checks |
|----|-----------|----------------|
| C1 | Intent label | The label matches the real meaning of the post |
| C2 | Dialect / Pidgin | Fails only if misreading the dialect caused a wrong label |
| C3 | Urgency flag | Urgent complaints (money stuck, failed charges, outages) are flagged Yes |
| C4 | Spam handling | Spam is labelled Spam, and genuine posts are not wrongly labelled Spam |
| C5 | Ambiguity | Sarcasm or dual-intent posts get a sensible label |
| C6 | Completeness | Every post has a label |

## Results (50 posts)
Error rate = posts failed ÷ posts audited × 100

- Posts audited: 50
- Posts with at least one Fail: **11 (22%)**
- Total criterion failures: 17 (one post can fail several criteria, e.g. Post 24 failed C1, C2 and C3)

| Criterion | Fails | Failed Posts |
|-----------|-------|--------------|
| C1 | 6 | 1, 23, 24, 32, 40, 43 |
| C2 | 1 | 24 |
| C3 | 6 | 3, 5, 15, 24, 28, 38 |
| C4 | 3 | 1, 23, 40 |
| C5 | 1 | 32 |
| C6 | 0 | None |

## Findings
- **Joint most common errors:** C1 (intent label) and C3 (urgency flag), 6 of 50 posts each.
- **C3 pattern:** `Flag: Yes` was often missing on financial loss (stuck refunds, failed debits, overcharges) and major outages, even though similar complaints elsewhere (Posts 37, 46) were flagged correctly.
- **Example (Post 1):** A genuine price query was labelled Spam. This is a false positive, so it fails C1 and C4.

## Recommendations
1. **High (C3, 6 fails):** Require `Flag: Yes` for any post citing lost or stuck funds, unauthorized debits, or outages over 24 hours.
2. **High (C1, 6 fails):** Add worked examples to the guidelines showing how to tell intent when a post mixes complaint, question and praise.
3. **Medium (C4, 3 fails):** Make spam rules work both ways. Scams must not pass as Inquiries or Praise (Posts 23, 40), and genuine price queries must not be tagged Spam (Post 1).
4. **Lower (1 fail each):** Add sarcasm guidance (Post 32) and Pidgin financial-phrase examples (Post 24).

## Limitations
Synthetic data, one auditor, a sample of 50. Results show the method, not real-world error rates. With a second reviewer, I would have both audit independently, compare Pass/Fail calls, discuss each disagreement against the written guideline, and update the guideline where it was unclear.

## Files
- `50_practice_posts_raw.csv`: the 50 practice posts
