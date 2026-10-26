# hitl-qa-audit-benchmark

A human QA audit of 50 labelled social media posts, using a 6-point checklist.

> **Data note:** The 50 posts are **synthetic practice data** written for training. They are not real social media data. This is a simulated QC audit, not a production project. No AI model was tested; I audited the labels and priority flags that were already assigned.

## What I did
Acting as QC, I checked each post's assigned label (Complaint, Inquiry, Praise, Spam) and priority flag against six criteria, marked Pass or Fail, and wrote a reason for every Fail.

## Audit checklist

| ID | Criterion | What it checks |
|----|-----------|----------------|
| C1 | Intent label | The label matches the real meaning of the post |
| C2 | Dialect / Pidgin | Pidgin or mixed-language posts are labelled correctly. Fails only if misreading the dialect caused a wrong label |
| C3 | Urgency flag | Urgent complaints (money stuck, failed charges, outages) are flagged Yes |
| C4 | Spam | Spam is labelled Spam |
| C5 | Ambiguity | Sarcasm or dual-intent posts get a sensible label |
| C6 | Completeness | Every post has a label |

## Results (50 posts)
Error rate = posts failed ÷ posts audited × 100

- Posts audited: 50
- Posts with at least one Fail: **11** (**22%**)

*(Note: Total criteria failures sum to more than 11 because a single post can fail multiple criteria, e.g., Post 24 failed C1, C2, and C3).*

**Fails by criterion**

| Criterion | Fails | Failed Posts |
|-----------|-------|--------------|
| C1 | 6 | Posts 1, 23, 24, 32, 40, 43 |
| C2 | 1 | Post 24 |
| C3 | 6 | Posts 3, 5, 15, 24, 28, 38 |
| C4 | 3 | Posts 1, 23, 40 |
| C5 | 1 | Post 32 |
| C6 | 0 | None |

## Findings
- **Most common error:** Missed Urgency Escalation Flags (Criterion C3 — 6 of 50 posts failed: Posts 3, 5, 15, 24, 28, 38).
- **Likely cause:** Annotators consistently omitted `Flag: Yes` on financial losses (missing/stuck refunds, failed debits, agent overcharges) and major service blackouts, despite correctly flagging similar complaints elsewhere (e.g., Posts 37, 46).
- **Recommendation 1 (High Priority — 6 fails):** Update guidelines to mandate `Flag: Yes` for any post citing lost/stuck funds, unauthorized debits, or prolonged network outages (>24 hours).
- **Recommendation 2 (Medium Priority — 3 fails):** Clarify spam rules bidirectionally: prevent commercial scams from being misclassified as genuine Inquiries or Praise (Posts 23, 40), and stop valid product price queries from being wrongly tagged as Spam (Post 1).
- **Recommendation 3 (Lower Priority — 1 fail each):** Add contextual guidelines for sarcasm detection (Post 32) and expand dialect training for West African Pidgin English financial phrases (Post 24).

## Limitations
Synthetic data, one auditor, and a small sample of 50. Results show the method, not real-world error rates.

## Files
- `50_practice_posts_raw.csv`: the 50 practice posts
