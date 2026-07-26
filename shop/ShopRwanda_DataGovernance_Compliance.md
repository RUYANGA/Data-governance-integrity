# DATA GOVERNANCE & INTEGRITY

## Multi-Jurisdiction Compliance Response Matrix

**Handling Global Customer Data Deletion Requests under Rwanda Data Protection Law (Law No. 058/2021), GDPR, and CCPA/CPRA**

---

**ShopRwanda Ltd. — Data Protection Office**

| Field | Detail |
| --- | --- |
| **Document Title** | Multi-Jurisdiction Data Deletion Compliance Response |
| **Prepared For** | ShopRwanda Ltd. — E-commerce Operations |
| **Prepared By** | Data Governance & Privacy Compliance Team |
| **Classification** | Internal — Compliance & Legal |
| **Version** | 1.0 |
| **Issue Date** | 26 July 2026 |
| **Review Cycle** | Annual or upon regulatory change |

---

## 1. Executive Summary

ShopRwanda Ltd. operates an e-commerce platform serving customers across multiple jurisdictions and, as a data controller, is legally accountable for the lawful, fair, and transparent processing of personal data. This report analyses three concurrent customer data deletion requests originating from Rwanda, Germany, and the State of California, and sets out the compliant, defensible response for each jurisdiction.

Each request has been evaluated against the relevant statutory framework — Rwanda's Data Protection Law, 2021 (Law No. 058/2021); the EU General Data Protection Regulation (Regulation (EU) 2016/679); and the California Consumer Privacy Act as amended by the California Privacy Rights Act (CCPA/CPRA). The analysis identifies the data subject's rights, the controller's obligations, permissible retention grounds, statutory response deadlines, and penalty exposure for non-compliance.

The overarching finding is that although all three regimes recognise a right to erasure or deletion, the strength of that right, the acceptable exemptions, and the response timelines differ materially. A one-size-fits-all response would breach at least one regulation. This document therefore prescribes jurisdiction-specific workflows and a supporting governance framework covering identity verification, retention logic, audit trail, and data integrity controls.

---

## 2. Regulatory Framework Overview

### 2.1 Rwanda Data Protection Law, 2021 (Law No. 058/2021)

Supervised by the National Cyber Security Authority (NCSA), Law No. 058/2021 establishes the rights of data subjects and the obligations of data controllers in Rwanda. The law grants data subjects the right to request rectification, erasure, or blocking of personal data that is inaccurate, irrelevant, excessive, or unlawfully obtained. The right is qualified: controllers may retain data where retention is required to comply with other laws or is justified by legitimate purpose, including financial recordkeeping obligations under Rwandan tax and commercial legislation.

### 2.2 EU General Data Protection Regulation (GDPR)

**Article 17** of the GDPR establishes the Right to Erasure ("right to be forgotten"), obliging controllers to erase personal data without undue delay when one of the enumerated grounds applies (e.g., the data is no longer necessary, the subject withdraws consent, or the data has been unlawfully processed). **Article 12(3)** sets the response deadline at one month, extendable by a further two months where justified. Exemptions under **Article 17(3)** preserve retention rights for legal obligations, public interest, and the establishment or defence of legal claims.

### 2.3 California Consumer Privacy Act / Privacy Rights Act (CCPA/CPRA)

The CCPA (Cal. Civ. Code § 1798.100 et seq.), as amended by the CPRA effective January 2023, grants California residents the right to request deletion of personal information, the right to correct inaccurate information, and the right to opt out of the sale or sharing of personal information. Businesses must respond within **45 calendar days**, extendable once by an additional 45 days upon notice. **Section 1798.105(d)** enumerates nine exemptions permitting retention, including completion of a transaction, security incident investigation, and compliance with legal obligations.

---

## 3. Data Subject Request Analysis

---

### 3.1 Case A — Aline (Rwanda · Law No. 058/2021)

#### Legal Rights Analysis

Under **Law No. 058/2021**, Aline has the right to request the deletion of personal data held by ShopRwanda. The right is not absolute: data may be retained where processing is required by law or is justified by a legitimate business purpose, most notably financial recordkeeping obligations imposed by the Rwanda Revenue Authority (RRA) and anti-money-laundering statutes under the Law Relating to the Prevention and Suppression of Money Laundering.

#### Company Obligations

- Verify the requester's identity to prevent unauthorised disclosure or destruction of records.
- Assess the request against retention rules and erase all data not subject to a legal hold.
- Provide a clear, plain-language response confirming the outcome of the request.
- Log the request, the assessment, and the action taken in the Data Subject Request register for audit purposes.

#### Data Retention

| Item | Detail |
| --- | --- |
| **Data Retained** | Transaction, invoice, and payment records |
| **Legal Basis** | Compliance with financial, tax, and AML statutes |
| **Retention Period** | Six (6) years from the end of the relevant financial year, consistent with the Rwanda Revenue Authority requirements and the East African Community Customs Management Act |

#### Response Deadline

Law No. 058/2021 requires controllers to respond to data subject requests within a reasonable time. In line with NCSA guidance and international best practice, ShopRwanda adopts **30 calendar days** as its internal service level, aligning with the standard applied under comparable data protection regimes.

#### Action Steps

1. Authenticate the requester through the registered email plus a one-time verification code.
2. Delete profile data: name, address, contact details, marketing preferences, and behavioural analytics.
3. Anonymise data required for aggregate analytics so it can no longer be linked to Aline.
4. Preserve legally mandated financial records in an access-restricted archive.
5. Record the request, decision, and completion timestamp in the audit log.

#### Draft Response to the Data Subject

> Dear Aline,
>
> Thank you for contacting the ShopRwanda Data Protection Office. Following verification of your identity, we have deleted your personal account data, including your profile, contact details, and marketing preferences.
>
> In line with Rwandan tax legislation and applicable financial recordkeeping requirements, we are legally required to retain transaction and invoice records for six years from the end of the relevant financial year. These records are held in a restricted archive and will not be used for any other purpose.
>
> If you have further questions, please contact our Data Protection Officer at dpo@shoprwanda.example.

---

### 3.2 Case B — Lukas (Germany · GDPR)

#### Legal Rights Analysis

As a resident of Germany, Lukas is protected by the GDPR and by the German Federal Data Protection Act (BDSG). **Article 17(1)** grants him a strong Right to Erasure. Because ShopRwanda offers goods to individuals in the European Union, it is subject to the GDPR's extra-territorial scope under **Article 3(2)**.

#### Applicable Exemptions

- **Article 17(3)(b)** — compliance with a legal obligation (e.g., retention of invoices under German commercial and tax law).
- **Article 17(3)(e)** — the establishment, exercise, or defence of legal claims.

#### Company Obligations

- Erase personal data without undue delay and, in any event, within one month.
- Communicate the erasure to any recipient (processor or third party) to whom the data has been disclosed, unless this proves impossible or requires disproportionate effort (**Article 19**).
- Where data has been made public, take reasonable steps to inform other controllers that the subject has requested erasure of links, copies, or replications (**Article 17(2)**).
- Provide the data subject with confirmation of erasure and information on any retained data and the legal basis for retention.

#### Response Deadline

**One (1) month** from receipt of the request under Article 12(3), extendable by a further two months where necessary, taking into account the complexity and number of requests. Any extension must be communicated to the data subject within the first month, together with the reasons for delay.

#### Penalty Exposure

Non-compliance with Articles 12–22 attracts administrative fines of up to **€20 million or 4% of the total worldwide annual turnover** of the preceding financial year, whichever is higher (Article 83(5)). German supervisory authorities are among the most active enforcers in the EU.

#### Action Steps

1. Verify identity through the registered email and a secondary factor; do not request excessive documentation.
2. Execute deletion across production databases, backup indexes, analytics warehouses, and CRM systems.
3. Issue erasure notices to all processors and third-party recipients under Article 19.
4. Retain only invoice and transaction records required by § 257 HGB and § 147 AO, in a segregated legal-hold archive.
5. Provide written confirmation of erasure to Lukas within the statutory period.

#### Draft Response to the Data Subject

> Dear Lukas,
>
> We confirm that your erasure request under Article 17 of the GDPR has been actioned. Your personal data has been deleted from our production systems, marketing platforms, and analytics environments, and our processors have been instructed to do the same.
>
> In accordance with Article 17(3)(b) and German commercial and tax law (§ 257 HGB, § 147 AO), we are required to retain invoice and transaction records for up to ten years; these are held in a segregated archive with restricted access and will not be used for any further processing.
>
> You have the right to lodge a complaint with your competent supervisory authority.
>
> Yours sincerely,
> ShopRwanda Data Protection Office

---

### 3.3 Case C — Maria (California · CCPA/CPRA)

#### Legal Rights Analysis

Maria, as a California resident, is entitled to (a) the right to delete personal information under **§ 1798.105**, and (b) the right to opt out of the sale or sharing of personal information under **§ 1798.120**. Because an active return dispute is in progress, deletion is not immediate.

#### Can Deletion Be Immediate?

**No.** Section 1798.105(d)(1) expressly permits a business to retain personal information where necessary to complete the transaction for which it was collected, provide a good or service requested by the consumer, or reasonably fulfil the terms of a written warranty or product recall. The ongoing return dispute falls within this exemption. Deletion must be completed once the dispute is resolved.

#### Company Obligations

- Cease the sale and sharing of Maria's personal information immediately upon receipt of the opt-out request.
- Place Maria's account under a deletion hold until the return dispute is resolved, and complete deletion promptly thereafter.
- Provide the disclosures required by **§ 1798.130** — categories of personal information collected, sources, business purposes, and third parties with whom the information is shared.
- Notify all service providers, contractors, and third parties to which the information was sold or shared to also delete the information (**§ 1798.105(c)**).

#### Response Deadline

**Forty-five (45) calendar days** from receipt of a verifiable consumer request, extendable once by an additional 45 days where reasonably necessary, provided the consumer is notified of the extension and reasons within the initial period.

#### Penalty Exposure

Administrative penalties of up to **US$2,500 per unintentional violation** and **US$7,500 per intentional violation** or violation involving the personal information of a minor, assessed by the California Privacy Protection Agency. In addition, a private right of action exists for certain data breaches under **§ 1798.150**.

#### Action Steps

1. Verify identity to a "reasonable degree of certainty", appropriate for a non-account holder or account holder as applicable.
2. Update the consent register to reflect the opt-out and propagate the signal to advertising and analytics partners.
3. Flag the account for deferred deletion; suspend all non-essential processing while the return dispute is open.
4. Complete deletion within a reasonable time after dispute closure, and confirm to Maria.

#### Draft Response to the Data Subject

> Dear Maria,
>
> We acknowledge your requests under the CCPA/CPRA. Effective immediately, we have stopped selling and sharing your personal information and have instructed our advertising and analytics partners to do the same.
>
> Because your account currently has an active return dispute, section 1798.105(d)(1) permits us to retain the personal information necessary to complete that transaction. Your deletion request has been queued and will be executed within a reasonable period after the dispute is closed; we will then confirm completion in writing.
>
> Full details of the categories of personal information we collect, our sources, and our recipients are available in our Privacy Notice.
>
> Regards,
> ShopRwanda Privacy Team

---

## 4. Comparative Compliance Matrix

| Element | Rwanda Law No. 058/2021 | EU GDPR | CCPA / CPRA |
| --- | --- | --- | --- |
| **Right to Deletion** | Yes — qualified | Yes — strong (Art. 17) | Yes — with statutory exemptions |
| **Extra-territorial Reach** | Data controllers established or processing data in Rwanda | Any controller offering goods/services to EU residents (Art. 3) | Businesses meeting revenue or data thresholds involving CA residents |
| **Response Deadline** | Reasonable time (≈21–30 days) | 1 month, extendable by 2 months | 45 days, extendable by a further 45 |
| **Key Exemptions** | Legal obligation; legitimate purpose | Legal obligation; public interest; legal claims (Art. 17(3)) | Complete transaction; legal obligation; security; free speech (§1798.105(d)) |
| **Third-Party Notification** | Reasonable steps | Mandatory (Art. 19) | Mandatory to service providers/third parties (§1798.105(c)) |
| **Opt-out of Sale/Sharing** | Not explicit | Governed by lawful basis and consent framework | Explicit right (§1798.120) |
| **Maximum Penalty** | Regulatory sanction and enforcement action by NCSA | €20M or 4% of global annual turnover | US$2,500–$7,500 per violation; private right of action for breaches |
| **Supervisory Authority** | National Cyber Security Authority (NCSA) | National DPAs (e.g., BfDI, LfDIs) coordinated by the EDPB | California Privacy Protection Agency (CPPA) |

---

## 5. Data Governance Framework

To operationalise the responses above and to make compliance repeatable, ShopRwanda adopts the following governance controls. These controls apply uniformly across jurisdictions; jurisdiction-specific rules are enforced through configuration within each control.

### 5.1 Roles and Accountability

- **Data Protection Officer (DPO)** — overall accountability for compliance and single point of contact for supervisory authorities.
- **Data Stewards** — domain owners (Customer, Orders, Payments, Marketing) responsible for lawful processing within their domain.
- **Legal & Compliance** — interprets jurisdictional obligations and reviews high-risk requests.
- **Engineering** — implements deletion, anonymisation, and access-control mechanisms.

### 5.2 Identity Verification

A tiered verification model is applied. Low-sensitivity requests are verified through the registered email plus a one-time code. Elevated-risk requests (large data volumes, previously disputed accounts, or requests routed via authorised agents) require additional verification consistent with GDPR Recital 64 and CCPA § 1798.140 without demanding excessive documentation.

### 5.3 Data Classification & Retention Schedule

- **Customer identity data** — deleted on erasure request unless subject to legal hold.
- **Transaction and invoice records** — retained per tax and commercial law (six years in Rwanda; up to ten years in Germany; four years for federal tax in the U.S.).
- **Marketing and behavioural data** — deleted immediately on erasure or opt-out.
- **Support and dispute records** — retained for the limitation period of any potential legal claim.

### 5.4 Audit Trail

Every data subject request is recorded in an immutable log capturing: request identifier, receipt timestamp, jurisdiction, verification outcome, decision, systems actioned, third-party notifications, completion timestamp, and the officer accountable. The log is retained for at least seven years to support supervisory audits.

---

## 6. Data Integrity Controls

Data integrity requires that personal data remain accurate, complete, and consistent across all systems during its lifecycle, and that erasure is verifiable and irreversible.

- **Deletion propagation** — an event-driven deletion pipeline broadcasts erasure events to every downstream system (analytics, CRM, backups indexes, search) with confirmation callbacks.
- **Backup handling** — backups from before the erasure event are retained until they expire under the backup retention policy; if restored, the erasure ledger is replayed to ensure the subject's data does not reappear.
- **Anonymisation** — where data is required for legitimate analytics, it is irreversibly anonymised (e.g., hashed identifiers salted per-tenant, generalised attributes, k-anonymity thresholds).
- **Access control** — legal-hold archives are stored under least-privilege access with break-glass procedures and full access logging.
- **Verification testing** — quarterly test requests confirm that deletion has propagated through all systems within the target service level.

---

## 7. Risk & Penalty Analysis

| Risk | Jurisdiction | Impact | Mitigation |
| --- | --- | --- | --- |
| Missing statutory deadline | GDPR / CCPA | Fines and reputational harm | Automated SLA tracker with escalation at 50% of the deadline |
| Incomplete deletion (residual data in backups or third parties) | All | Regulatory breach; loss of trust | Erasure ledger, third-party notifications under Art. 19 and §1798.105(c) |
| Improper identity verification (wrongful deletion) | All | Data loss, potential legal claims | Tiered verification, four-eyes review for elevated risk |
| Continued sale of personal data after opt-out | CCPA/CPRA | US$2,500–$7,500 per violation | Immediate propagation of opt-out to all sale/share integrations |
| Cross-border transfer of retained data | GDPR | Article 44–49 breach | Standard Contractual Clauses and Transfer Impact Assessments |

---

## 8. Recommendations

1. Adopt the strictest applicable standard as the operational baseline (GDPR) and adjust only where a jurisdiction requires a different action; this simplifies engineering and reduces regulatory divergence.
2. Publish a jurisdictionally-aware Privacy Notice that clearly discloses rights, retention, and how to exercise erasure and opt-out.
3. Automate the Data Subject Request workflow end-to-end: intake, verification, routing, action, notification, and audit log entry.
4. Contractually bind all processors and third parties to honour erasure and opt-out signals within 72 hours of notification.
5. Conduct annual compliance drills simulating requests from each jurisdiction to validate deadlines, controls, and evidentiary records.
6. Provide role-specific training for Customer Service, Engineering, and Marketing teams on lawful handling of personal data.

---

## 9. Conclusion

The three requests analysed in this report demonstrate that data governance is not a static checklist but a jurisdiction-aware discipline. Rwanda's Law No. 058/2021 supports the request while permitting retention for legal obligations; the GDPR imposes the strongest and most time-bound obligation, with severe penalties for delay; and the CCPA/CPRA emphasises consumer control over the sale and sharing of personal information while permitting deferred deletion where a transaction is ongoing.

By combining a jurisdictionally-aware legal analysis with disciplined identity verification, retention rules, deletion propagation, and an evidentiary audit trail, ShopRwanda can respond to every request in a compliant, defensible, and trust-preserving manner. This framework should be reviewed annually, and immediately upon any material regulatory change, to keep pace with an evolving global privacy landscape.

---

**Prepared by:** Data Governance & Privacy Compliance Team
**Reviewed by:** Data Protection Officer, ShopRwanda Ltd.
**Approved by:** Chief Compliance Officer
**Date of Issue:** 26 July 2026
