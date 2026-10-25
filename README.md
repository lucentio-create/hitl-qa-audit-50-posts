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

### 📐 Baseline Quality Evaluation Metrics

Based on the 50-post benchmark audit sample (39 Passed / 11 Failed), baseline classification performance metrics are evaluated as follows:

| Metric | Score | Evaluation Focus |
| :--- | :---: | :--- |
| **Accuracy** | **78.00%** | Overall correct audit classification rate across all criteria (C1–C6). |
| **Precision** | **81.82%** | Measures exactness—minimizes false positive failure flags. |
| **Recall** | **70.00%** | Measures audit coverage—ensures critical failures (C3 urgency, C2 Pidgin) are caught. |
| **F1 Score** | **75.52%** | Harmonic mean balancing Precision and Recall across edge cases. |

---

### 💡 Model Diagnostics (Underfitting vs. Overfitting)

* **Underfitting Risk (Recall < 70%):** Prompt guidelines are too broad, leading the model to miss subtle dialect phrasing (West African Pidgin) or implicit sarcasm. 
  * *Mitigation:* Inject explicit few-shot edge-case examples into model system prompts.
* **Overfitting Risk:** Occurs if rules over-memorize specific training sample phrases, failing on unseen real-world posts.
  * *Mitigation:* Maintain independent validation splits and evaluate against fresh, un-audited customer support streams.

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
### 💡 Model Diagnostics (Underfitting vs. Overfitting Loop)

* **Underfitting Handling (Improving Recall):**
  * *Symptom:* Prompt rules are too simple or broad, causing the model to miss subtle edge cases like West African Pidgin English (C2) or implicit urgency flags (C3).
  * *Optimization:* Inject explicit few-shot edge-case examples into system prompts to train the model on dialect syntax and urgency cues.

* **Overfitting Handling (Ensuring Generalization):**
  * *Symptom:* High accuracy on the 50 practice sample posts, but performance drops on brand-new, unseen customer support posts because the rules over-memorized specific keywords.
  * *Optimization:* Keep rules focused on conceptual intent rather than exact string matching, and regularly evaluate against fresh, un-audited dataset splits.




