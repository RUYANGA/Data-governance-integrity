# DATA ACCESS DECISION SIMULATOR
Data Governance & Integrity — Lab Deliverable

## Executive Summary
Three data access requests were received on Monday morning. Each was assessed against EduConnect's three-tier data classification policy, the principle of least privilege, the data lifecycle model (Create → Store → Use → Share → Archive → Destroy), and Rwanda's data protection regime — Law No. 058/2021 relating to the protection of personal data and privacy, supervised by the National Cyber Security Authority (NCSA). Summary of decisions below; full decision forms follow.

---

| Organization: | EduConnect Rwanda (Ed-tech platform, 50,000+ students) |
| --- | --- |
| Role: | DevOps Engineer — Data Access Approver |
| Governing Policy: | EduConnect Data Classification Policy (PUBLIC / INTERNAL / CONFIDENTIAL) |
| Regulatory Frame: | Law No. 058/2021 of 13/10/2021 on the protection of personal data and privacy; supervised by the National Cyber Security Authority (NCSA) |
| Document Type: | Data Access Decision Forms — 3 Requests |

| Request | Requester & Purpose | Lifecycle Stage | Decision |
| --- | --- | --- | --- |
| #1 | Sarah Uwase (Marketing) — Referral campaign | Use / Share | CONDITIONAL APPROVAL |
| #2 | David Mugisha (Product) — Third-party analytics | Share (cross-border) | DENY (as submitted) |
| #3 | Claudine Mukamana (Support) — Right to erasure | Archive / Destroy | APPROVE (with retention exceptions) |

---

## Request #1 — Marketing Campaign

| Field | Detail |
| --- | --- |
| **Requester** | Sarah Uwase, Marketing Manager |
| **Requested Data** | Full student database — names, emails, phone numbers, course enrollments |
| **Stated Purpose** | Launch a referral campaign (starts Friday) |
| **Classification** | Emails & phone numbers = CONFIDENTIAL; Names & enrollments = INTERNAL |
| **Current Access** | INTERNAL only |

| Decision | **CONDITIONAL APPROVAL** (scope reduced from request as submitted) |
| --- | --- |
| **Lifecycle Stage** | USE and SHARE — data already collected is being repurposed for marketing and shared with a business function that did not previously have access to CONFIDENTIAL fields. |
| **Classification Finding** | The request crosses Sarah's authorization ceiling. She holds INTERNAL access; the request contains CONFIDENTIAL fields (email, phone). Approval at the requested scope would be an unauthorized elevation. |
| **Least Privilege Analysis** | The request violates least privilege on three axes: **Scope of data** — a referral campaign does not require phone numbers or full enrollment history; email plus first name is typically sufficient. **Scope of population** — only students who granted marketing consent may lawfully be contacted; the request is for the full database. **Mode of access** — direct database access to CONFIDENTIAL fields is not required. Marketing needs a send, not a query. |
| **Compliance Considerations** | Under Law No. 058/2021 on the protection of personal data and privacy: **Purpose limitation** — personal data collected for course delivery may not be repurposed for marketing without a compatible legal basis or fresh consent from the data subject. **Consent** — marketing communications require consent that is free, specific, informed, and unambiguous, and that can be withdrawn as easily as it was given. **Data minimisation** — only personal data that is adequate, relevant, and limited to what is necessary for the campaign may be processed. **Accountability** — EduConnect as data controller must be able to demonstrate compliance if reviewed by the National Cyber Security Authority (NCSA). |
| **Justification** | Approving the request as submitted would breach the classification policy (CONFIDENTIAL data to an INTERNAL-cleared user), the principle of least privilege, and the purpose-limitation, consent, and data-minimisation requirements under Law No. 058/2021. A narrower, controlled scope can meet the business need without any of these breaches. |
| **Stakeholders to Consult** | **Data Protection Officer (DPO)** — lawful basis and consent status · **Legal Counsel** — Law No. 058/2021 compliance sign-off · **Head of Data / CTO** — technical delivery pattern · **Marketing Director** — reduce scope to minimum necessary |
| **Required Safeguards** | 1. **Consent filter** — campaign sends only to students with an active marketing opt-in on record. 2. **Data minimisation** — supply first name and email only. No phone numbers, no enrollment history. 3. **No raw PII to marketing** — load the filtered list into the marketing automation platform (e.g., Mailchimp, HubSpot); Sarah operates the campaign, she does not receive a spreadsheet. 4. **Time-boxed access** — campaign audience expires 14 days after campaign end. 5. **Audit logging** — every access to the filtered dataset is logged and retained 12 months. 6. **Data Processing Agreement** — verify the marketing platform vendor has a signed processor agreement covering the requirements of Law No. 058/2021. 7. **Unsubscribe mechanism** — every message must carry a one-click unsubscribe honouring the right to withdraw consent. |
| **Action Steps** | 1. Reply to Sarah today: deny the full-database request; propose the consent-filtered, minimised alternative with a delivery date that still meets Friday's launch. 2. Open a change ticket; loop in DPO and Legal for lawful-basis confirmation before any export. 3. Query the consent register for students with marketing opt-in = TRUE; export first name and email only into the marketing automation platform via secure API. 4. Configure role-based access in the platform so Sarah can compose and send, but cannot download the recipient list. 5. Register the campaign in the record of processing activities maintained by the DPO. 6. Set an automated task to purge the campaign audience 14 days post-campaign. 7. Post-mortem the request pattern: publish a marketing self-service guide so future campaigns do not surface as raw-DB requests. |

---

## Request #2 — Analytics Partnership

| Field | Detail |
| --- | --- |
| **Requester** | David Mugisha, Head of Product |
| **Requested Action** | Grant DataInsights Inc. (US-based) direct access to the AWS database using attached login credentials |
| **Stated Purpose** | Analyse student learning patterns under a signed partnership |
| **Classification** | Activity logs = INTERNAL; Student profiles = CONFIDENTIAL |
| **Regulatory Frame** | Law No. 058/2021 — cross-border transfer + processor engagement; supervised by NCSA |

| Decision | **DENY** as submitted. A revised proposal may be approved once the controls below are in place. |
| --- | --- |
| **Lifecycle Stage** | SHARE — specifically a cross-border transfer to a third-party processor. This is the highest-risk stage of the lifecycle for confidential data. |
| **Immediate Red Flags** | **Shared credentials** — sending login credentials by ticket destroys accountability and non-repudiation. A shared account cannot support attributable audit logging. The credentials should be treated as compromised on receipt and rotated immediately. **Direct database access to a third party** — gives DataInsights ambient access to CONFIDENTIAL student profiles even when their algorithms only need aggregates or a specific subset. **Cross-border transfer to the US** — Law No. 058/2021 restricts the transfer of personal data outside Rwanda. Such transfers generally require authorisation from the National Cyber Security Authority and are conditional on the receiving jurisdiction offering an adequate level of protection, or on appropriate safeguards being in place (such as binding contractual clauses). None of this is addressed in the request. **No Data Processing Agreement** — the request references a partnership contract, not a data-specific processor agreement covering purpose, retention, sub-processing, security controls, breach notification, and audit rights as required for controller-processor relationships under Law No. 058/2021. **No Data Protection Impact Assessment** — large-scale processing of student profiles by an external processor triggers the DPIA threshold for high-risk processing. **No lawful basis check** — students consented to their data being used to deliver courses; secondary use for external analytics is a different purpose and needs a fresh legal basis (compatible-use analysis or new consent). **No DPO / Legal sign-off** — Head of Product cannot unilaterally authorise a cross-border data transfer. |
| **Justification** | The request as written combines every high-risk pattern in one ticket: shared credentials, unfiltered access to CONFIDENTIAL data, cross-border transfer without NCSA authorisation, missing processor agreement, missing DPIA, and no DPO involvement. Approving in this form would expose EduConnect to enforcement action under Law No. 058/2021, contractual liability, and reputational harm to a 50,000-student user base. Denial is protective, not obstructive; a revised architecture can deliver the partnership's value lawfully. |
| **Controls Required Before Any Re-Approval** | 1. **Signed Data Processing Agreement** — purpose, retention limit, sub-processor clause, security controls (encryption at rest and in transit, access logs), breach notification to EduConnect within the shortest feasible timeframe, right-to-audit. 2. **Cross-border transfer authorisation** — documented adequacy assessment of the receiving jurisdiction, appropriate safeguards (binding contractual clauses or equivalent), and NCSA notification/authorisation where required by Law No. 058/2021. 3. **Data Protection Impact Assessment** — completed and signed off by the DPO before any data leaves the environment; findings shared with NCSA if the residual risk is high. 4. **Pseudonymisation / anonymisation** — student identifiers replaced with opaque tokens; direct identifiers (name, email, phone, national ID) stripped or held only in EduConnect's environment behind a re-identification key that DataInsights never sees. 5. **Individual named accounts, not shared credentials** — each DataInsights analyst gets a personal account with MFA. Every query is attributable. 6. **Role-based, least-privilege access** — read-only on a purpose-built analytics schema containing only the fields the DPIA authorised. No access to production tables. 7. **Network controls** — access via VPN or PrivateLink to an isolated analytics VPC. No public database endpoint. 8. **Query and export logging** — all activity logged to an immutable store; alerting on bulk exports. 9. **Time-boxed engagement** — access expires on the contract end date and requires renewal. 10. **Preferred pattern** — consider a federated / query-in-place model where DataInsights ships algorithms to EduConnect's environment rather than data leaving Rwanda. |
| **Documentation to be in Place** | - Signed Data Processing Agreement (or equivalent processor contract) - Completed DPIA with DPO sign-off - Cross-border transfer risk assessment and NCSA authorisation record - Record of processing activities (updated) - Access control matrix showing named users, roles, and fields - Evidence of student notice / lawful basis for the secondary purpose - Incident response playbook covering the partnership |
| **Action Steps** | 1. Do not action the credentials in the ticket. Rotate them and any accounts they may unlock; treat as a credential-exposure incident. 2. Reply to David within the hour: request is on hold pending DPO and Legal review; explain the specific blockers in non-punitive language. 3. Escalate to CTO, DPO, and Legal today. Open a formal risk ticket. 4. Kick off DPIA and DPA workstreams in parallel; nominate a data owner for the partnership. 5. Design the target architecture (pseudonymised analytics schema, isolated VPC, named accounts, MFA, audit sink). 6. Only after DPA signed, DPIA approved, cross-border authorisation obtained, and controls implemented, provision named least-privilege access on the analytics schema. 7. Add the partnership to the quarterly access review cycle. |

---

## Request #3 — Right to Erasure

| Field | Detail |
| --- | --- |
| **Requester (on behalf of data subject)** | Claudine Mukamana, Customer Support Lead |
| **Data Subject** | Jean-Pierre Habimana, former student |
| **Requested Action** | Full deletion of account and all associated data |
| **Classification** | All student data = CONFIDENTIAL |
| **Status Check** | Account inactive; last course completed 6 months ago; no pending payments |

| Decision | **APPROVE** — the erasure request will be fulfilled, subject to lawful retention exceptions documented below. |
| --- | --- |
| **Lifecycle Stage** | ARCHIVE followed by DESTROY. Data subject to legal retention obligations moves to a restricted archive; all other personal data is destroyed. |
| **Can the Request be Fulfilled?** | Yes, substantially. Law No. 058/2021 grants the data subject the right to obtain rectification, erasure, or blocking of personal data where the data is no longer necessary for the purpose for which it was collected, where consent has been withdrawn, or where processing is otherwise unlawful. Jean-Pierre's course is complete, there are no financial obligations, and no active legal basis to keep his personal profile. However, EduConnect has parallel obligations under Rwandan tax and financial-records law that require retention of specific records — those cannot be deleted, but they can be minimised and access-restricted. |
| **Legal Obligations under Law No. 058/2021** | 1. **Verify the identity of the requester** before acting (a deletion request from an impostor is itself a personal-data breach). 2. **Respond within the timeframe set by the law**; industry practice aligned with the law is to complete verified erasure requests within a reasonable period, typically not exceeding one month. 3. **Notify any processors and sub-processors** holding Jean-Pierre's data so they can execute deletion in their systems. 4. **Provide the data subject with confirmation** of the actions taken, including what was retained and on what legal basis. 5. **Log the request and the response in an erasure register** — the accountability principle requires that compliance be demonstrable to the National Cyber Security Authority (NCSA) on request. |
| **Data that May be Retained (and why)** | - **Financial and tax records** — invoices, receipts, and payment records must be retained under Rwanda's tax procedures law and the accounting rules applicable to registered businesses (typically ten years). These are financial records that happen to contain personal data, not marketing data; they stay in the finance system with access restricted. - **Certification / credential records** — the fact that Jean-Pierre completed and was awarded a specific course is a credential a third party may verify. Retain the minimum needed to honour verification requests; consider anonymising the underlying learning data. - **Aggregated and anonymised analytics** — already-aggregated statistics that no longer identify Jean-Pierre may be retained; they fall outside the scope of Law No. 058/2021. - **The erasure request itself** — a record of the request, the verification, and the actions taken must be retained as evidence of compliance. - **Legal hold** — if any active dispute or investigation involves Jean-Pierre, deletion is paused until the hold is lifted (none currently indicated). |
| **Data to be Destroyed** | - Profile fields: name, email, phone, address, date of birth, national ID - Login credentials and authentication history - Behavioural data: activity logs, session recordings, support-chat transcripts - Learning artefacts: submitted assignments, forum posts, saved drafts - Marketing profile, consent flags no longer needed, referral history - **Backups**: schedule cascade deletion so the next backup rotation removes Jean-Pierre's data; if immediate purge is impossible, place the backup under an access-restricted key and document the retention window until rotation. |
| **Process for Customer Support** | 1. **Verify Jean-Pierre's identity** through at least two factors (registered email confirmation link plus a second identifier such as national ID or last-payment reference). 2. **Log the request in the erasure register** with timestamp, verification evidence, and case number. 3. **Acknowledge to Jean-Pierre within 48 hours**: request received, expected completion date, explanation that certain financial and credential records are retained by law with the specific basis. 4. **Raise a coordinated deletion ticket** to Engineering, Finance, and any third-party processors (LMS, payment gateway, email platform, analytics). 5. **Execute deletion in production**; move retained financial and credential records to a restricted archive schema with narrowed access. 6. **Confirm deletion propagation** through the next backup cycle; document the backup rotation date on which the last copy is overwritten. 7. **Send Jean-Pierre a written confirmation**: what was deleted, what was retained, the legal basis, the retention period, and how to escalate to the DPO or lodge a complaint with the National Cyber Security Authority if unsatisfied. 8. **Close the case** in the erasure register with all evidence attached; add to the quarterly DPO report. |
| **Justification** | Fulfilling the request honours the data subject's rights under Law No. 058/2021 and demonstrates that EduConnect's data lifecycle model reaches the DESTROY stage as designed. The retention exceptions are narrow, tied to specific legal obligations, and communicated transparently to the data subject — which is what a well-run governance programme looks like. |

---

## Cross-Cutting Analysis

### Classification Policy Applied
Every request was tested against the three-tier policy first. CONFIDENTIAL data (emails, phone numbers, full profiles) triggered the tightest controls in Requests 1 and 2; in Request 3 the same classification is what makes complete deletion — rather than mere account deactivation — the correct default. INTERNAL data (enrollments, activity logs) is still subject to purpose limitation, not a free pass.

### Least Privilege in Practice
Least privilege showed up differently in each case. In Request 1, it meant narrowing scope (consented students only, first name and email only, campaign platform not raw DB). In Request 2, it meant refusing shared credentials, insisting on named accounts, a purpose-built analytics schema, and read-only access. In Request 3, it meant restricting the residual financial records to a smaller access group after the main deletion.

### Lifecycle Stages Recognised
The three requests together exercise the second half of the lifecycle model — USE (Request 1 repurposing existing data), SHARE (Request 2 external transfer), and ARCHIVE/DESTROY (Request 3 end-of-life). Recognising the stage sets the applicable controls: purpose limitation for USE, transfer safeguards and processor agreements for SHARE, retention rules and deletion evidence for DESTROY.

### Compliance Implications
Rwanda's Law No. 058/2021 on the protection of personal data and privacy sits under all three decisions: lawful basis and consent for marketing (#1), cross-border transfer conditions and processor obligations enforced by the National Cyber Security Authority (#2), and the data subject's rights of access and erasure (#3). None of these were peripheral — in each case the law drove the decision more than any technical consideration.

### Governance Signal
A pattern is visible across the three tickets: business teams reach for the fastest route (full database export, shared credentials, blanket deletion) because the safe routes are not yet self-service. The follow-through from this exercise is to publish marketing self-service tooling, a partner-onboarding pipeline, and a documented erasure workflow — turning each of these decisions from a bespoke judgement into an operationalised control.
