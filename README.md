# hitl-qa-audit-benchmark
A 6-criteria Human-in-the-Loop (HITL) QA framework and audit benchmark evaluating AI text classification, urgency escalation flags, and Pidgin English parsing on social media posts.
## 🎯 Audit Framework & Evaluation Taxonomy

Each post is evaluated against six standardized quality criteria (C1–C6):

| ID | Criteria Name | Description & Evaluation Logic |
| :---: | :--- | :--- |
| **C1** | Intent Classification | Validates if the assigned label (Complaint, Inquiry, Praise, Spam) matches the true user intent. |
| **C2** | Dialect / Pidgin Parsing | Evaluates non-standard/regional language (e.g., West African Pidgin English). Fails only if dialect misinterpretation causes a label error. |
| **C3** | Urgency Escalation | Verifies critical risk triggers (stuck/lost money, unauthorized charges, prolonged outages). Requires Flag: Yes. |
| **C4** | Spam Detection | Identifies unsolicited commercial promotion, phishing, or scam messages. |
| **C5** | Tone & Disambiguation | Evaluates edge cases such as sarcasm, implicit dissatisfaction, or dual-intent posts. |
| **C6** | Label Completeness | Verifies that a valid classification label is present. |

---

## 📊 Benchmark Results & Error Analysis

- **Total Sample Size:** 50 Posts
- **Passed Audit:** 39 / 50 (78%)
- **Failed Audit:** 11 / 50 (22%)

### Failure Distribution by Criteria

| Criteria | Failure Count | Key Failure Drivers |
| :--- | :---: | :--- |
| **C3 (Urgency Escalation)** | 7
