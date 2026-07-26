# QuickLoan Data Governance & Integrity Review

**Lab Deliverable — Data Governance & Integrity**

---

## 1. Context

QuickLoan is a Rwanda-based digital lender that uses a machine learning model to score loan applications and issue near-real-time credit decisions. The pipeline collects personal and financial information from applicants, feeds it into a predictive model, and returns an approval decision that is then acted upon by loan officers and downstream analytics teams.

This review examines the pipeline against core data governance and integrity principles — lawful basis for processing, data quality, classification and minimisation, model fairness, and decision auditability — and proposes a concrete set of controls to close the identified gaps. The regulatory frame of reference is Rwanda's Data Protection Law, 2021 (Law No. 058/2021), supervised by the National Cyber Security Authority (NCSA), supplemented by widely accepted responsible-AI practice.

---

## 2. Governance Review Card

The following card summarises the risks identified across the QuickLoan pipeline, the associated business and regulatory impact, and the recommended mitigations. Each row corresponds to a distinct governance area rather than a single stage of the pipeline, so that controls can be assigned to accountable owners.

| Governance Area | Issue / Definition | Business & Regulatory Impact | Recommended Mitigation |
| --- | --- | --- | --- |
| **1. Data Quality** | Incomplete and inconsistently formatted customer records — e.g. missing income fields, non-standard phone number formats, duplicated national ID entries. | Degrades ML prediction accuracy and produces unreliable loan decisions, which erodes portfolio quality and customer trust. | Enforce validation rules and required fields at the point of capture; standardise formats through a preprocessing pipeline; deduplicate against a canonical customer key. |
| **2. Legal & Compliance** | Sensitive personal and financial data collected without explicit, informed user consent, and no visible audit trail of consent decisions. | Direct violation of Rwanda's Data Protection Law (Law No. 058/2021), exposing QuickLoan to regulatory sanction, reputational damage and civil liability. | Implement a consent management module with opt-in checkboxes, granular purpose statements and immutable audit logs. Apply data minimisation across all collection points. |
| **3. Data Classification** | Customer records combine identifiers (name, national ID, phone) with financial attributes (income, existing debts) and are treated as a single undifferentiated store. | Uniform handling of mixed-sensitivity data increases blast radius of any breach and complicates access reviews. | Classify records as Sensitive / PII; apply encryption at rest and in transit, role-based access control (RBAC) and a defined retention schedule. |
| **4. Bias & Fairness** | Model trained on historical approval data that reflects existing socioeconomic and geographic inequalities in access to credit. | Systematically unfair approvals or rejections for particular demographic groups, reinforcing exclusion and creating discrimination risk. | Introduce pre- and post-training fairness checks; monitor approval and default rates by demographic segment; rebalance training data and apply fairness constraints where warranted. |
| **5. Transparency & Auditability** | ML decisions are returned to the loan officer without stored explanation metadata or a decision log. | Applicants cannot be given a meaningful reason for rejection; internal audit and regulator queries cannot be answered after the fact. | Log every model decision with the input features, model version, score and top contributing factors; retain logs for the statutory audit period. |
| **6. Reporting Metric** | Approval Rate by Demographic Group — the percentage of applications approved, disaggregated by gender, age band and region. | Provides an early-warning signal for disparate impact and supports evidence-based fairness reviews. | Publish the metric on a monthly governance dashboard using a grouped bar chart; set alert thresholds when any group deviates materially from the overall rate. |

---

## 3. Data Classification Decision

All QuickLoan applicant records are classified as **Sensitive**. They combine personally identifiable information (name, national ID number, contact details) with financial attributes (income, existing indebtedness, repayment history), any one of which, if exposed, could cause material harm to the customer. The following controls follow from this classification:

- **Encryption** — at rest using database-level encryption and in transit using TLS 1.2 or higher.
- **Access control** — role-based access with least-privilege defaults; access to raw PII limited to a named group and reviewed quarterly.
- **Retention** — a defined retention schedule aligned to the credit lifecycle plus the statutory record-keeping period, after which records are purged or anonymised.
- **Sharing** — no raw PII leaves the platform; analytics and third-party feeds receive masked or pseudonymised extracts only.

---

## 4. Corrected Data Flow — Annotated Fixes

The original data flow diagram was reviewed stage by stage. The corrections below are the minimum set required to bring the pipeline into alignment with the classification above and with Law No. 058/2021.

| Step | Stage | Correction Applied | Governance Rationale |
| --- | --- | --- | --- |
| **1** | Data collection | Restrict collection to essential attributes only: verified identity, income, credit history, requested amount. | Enforces the data minimisation principle under Law No. 058/2021. |
| **2–3** | Consent & intake | Insert an explicit consent step before any data is persisted; store consent artefacts with the customer record. | Establishes a lawful basis for processing and creates an auditable record. |
| **3** | Storage & classification | Tag records as Sensitive; apply encryption at rest, RBAC and a defined retention period. | Limits exposure of PII and prevents indefinite retention. |
| **4** | Preprocessing | Add validation, cleaning and normalisation as a required pipeline stage before model input. | Improves data quality and downstream model reliability. |
| **7** | ML decision | Log every decision with model version, feature values and top contributing factors. | Supports explainability, internal audit and applicant appeals. |
| **9–10** | Analytics & third-party sharing | Mask or pseudonymise PII before analytics use and before any external transfer. | Protects privacy while preserving analytical value. |

---

## 5. Storytelling & Reporting Recommendation

### Recommended metric

**Approval Rate by Demographic Group** — the percentage of loan applications approved, disaggregated by gender, age band and region.

### Recommended visualisation

A grouped bar chart, with demographic segments on the horizontal axis and approval rate on the vertical axis. A horizontal reference line marks the overall portfolio approval rate, so any bar that diverges from the reference line is immediately visible to a non-technical reader.

### Why it matters

Loan approval is a consequential automated decision. Publishing approval rates by group turns fairness from an abstract commitment into a monitorable, reportable number. It gives management an early-warning signal, gives auditors a defensible artefact, and gives customers confidence that the model is being watched. Combined with the decision logs recommended in Section 2, it also allows any disparity to be traced back to specific features and model versions.

---

## 6. Summary of Review Process

The review followed the data lifecycle from collection through model decision to downstream analytics, evaluating each stage against the principles of lawful basis, minimisation, quality, fairness and auditability. Gaps clustered around three themes.

First, the pipeline collected more data than it needed and did so without a documented consent step, which is the most exposed compliance risk under Law No. 058/2021. Introducing an explicit consent stage and pruning the collected attributes to those genuinely required for scoring closes this gap and, as a side effect, reduces the surface area of any future incident.

Second, data quality issues at intake propagated downstream and undermined the reliability of the model itself. Validation, standardisation and deduplication in the preprocessing stage are inexpensive controls that materially improve decision quality.

Third, the model inherited historical patterns of exclusion from its training data. Bias cannot be fully engineered away, but it can be measured. The proposed Approval Rate by Demographic Group metric, supported by decision logging, turns fairness into an ongoing operational discipline rather than a one-off design commitment.

Taken together, the recommended controls move QuickLoan from an implicit, developer-driven governance posture to an explicit, auditable one — better outcomes for customers, and a defensible position with the regulator.
