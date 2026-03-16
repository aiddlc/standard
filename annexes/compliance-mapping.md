# Annex B: Compliance Mapping

*Informative. This annex provides detailed guidance on mapping regulatory obligations to AIDDLC phases and artifacts. The normative compliance integration requirements are in Section 8 of the specification.*

---

## B.1 Purpose

This annex provides clause-level mapping of regulatory obligations to AIDDLC phases and artifacts. It is intended to assist Compliance Officers in completing the Phase 1 Compliance Matrix and in demonstrating compliance to regulatory bodies and auditors.

This mapping is provided as guidance. Regulatory requirements are complex and jurisdiction-specific. Implementations must always verify applicability with qualified legal and regulatory counsel.

---

## B.2 UK GDPR / GDPR

### Applicability
Applies to any implementation that processes personal data of individuals in the UK or EU. Healthcare, fintech, and SaaS implementations will almost universally be in scope.

### Obligation Mapping

| Obligation | Article | AIDDLC Phase | Artifact | Implementation Guidance |
|---|---|---|---|---|
| Lawful basis for processing | Art. 6 | Phase 1: Foundation | Compliance Matrix | Document the lawful basis for each processing activity. For healthcare: legitimate interests or vital interests. For financial services: contractual necessity or legal obligation. Lawful basis must be identified before architecture decisions are made. |
| Special category data | Art. 9 | Phase 1: Foundation | Compliance Matrix | Health data, financial vulnerability data, and biometric data are special category. Additional lawful basis required (Art. 9(2)). Flag in Compliance Matrix; triggers DPIA requirement. |
| Data Protection Impact Assessment | Art. 35 | Phase 1–2: Foundation + Discovery | DPIA Document | Required when processing is likely to result in high risk. Triggers: systematic profiling, large-scale special category processing, systematic monitoring of public areas. Complete before architecture design is finalised. |
| Data minimisation | Art. 5(1)(c) | Phase 3: Architecture | Data Model | AI Supervisor must review AI-generated data models for over-collection. Each data field must be justified against a specific processing purpose. Document in ADR. |
| Storage limitation | Art. 5(1)(e) | Phase 3–4: Architecture + Specification | Data Model + Feature Specifications | Retention periods must be specified for each data category. Automated deletion must be specified as a feature in Phase 4. |
| Privacy by design and default | Art. 25 | Phase 3: Architecture | Architecture Decision Records | Privacy controls must be in the architecture, not added as controls to a completed design. Document privacy-by-design decisions in ADRs. |
| Data subject access rights | Arts. 15–22 | Phase 4: Specification | Feature Specifications | Each data subject right (access, rectification, erasure, portability, objection, restriction) must be specified as a feature in Phase 4. Acceptance criteria must be testable. |
| Records of processing activities | Art. 30 | Phase 1: Foundation | Compliance Matrix | The Compliance Matrix, used as the ROPA, satisfies this requirement if it includes: controller identity, processing purposes, categories of data and subjects, recipients, retention periods, and security measures. |
| Breach notification | Art. 33 | Phase 3: Architecture | Incident Response Runbook | The capability to detect, assess, and notify a personal data breach within 72 hours must be designed into the system. Specify in Phase 4; build and test in Phases 5–6. |
| Data transfers | Arts. 44–49 | Phase 3: Architecture | Data Flow Diagram | Transfers to third countries must be identified in Phase 2 (Integration Map) and appropriate safeguards documented in Phase 3. |

---

## B.3 MHRA — Software as a Medical Device (SaMD)

### Applicability
Applies to software that is intended by its manufacturer to be used for medical purposes without being part of a hardware medical device. AI clinical decision support, patient monitoring software, and diagnostic tools are likely to be in scope. MHRA SaMD guidance and UKCA marking requirements apply.

### Obligation Mapping

| Obligation | Reference | AIDDLC Phase | Artifact | Implementation Guidance |
|---|---|---|---|---|
| Intended purpose definition | MHRA SaMD Guidance §3 | Phase 1: Foundation | Intelligence Brief | The intended purpose must be precise and unambiguous. It must specify: the medical purpose, the patient population, the clinical environment, and any contraindications. The Intelligence Brief serves as the intended purpose declaration. |
| Risk classification | MHRA SaMD Guidance §4 | Phase 1: Foundation | Compliance Matrix | Classify the device using the MHRA risk classification framework. Classification drives the extent of clinical evidence required. Document in Compliance Matrix. |
| Risk management | ISO 14971 | Phases 1–6 (continuous) | Risk Register | Risk management under ISO 14971 is a lifecycle activity. The Phase 2 Risk Register initiates the process; it must be updated at each phase gate. Residual risk must be acceptable before Phase 7 deployment. |
| Software development lifecycle | IEC 62304 | All phases | Context Package | IEC 62304 requires a documented SDLC for medical device software. AIDDLC satisfies this requirement when implemented with full conformance. The Context Package serves as the lifecycle documentation. |
| Clinical evaluation | MHRA Clinical Evidence Guidelines | Phases 2 + 6: Discovery + Validation | Clinical Evidence Report | Clinical evidence of safety and performance must be generated before deployment. For AI/ML software: include algorithm validation, bias assessment, and performance data across relevant patient populations. |
| Usability engineering | IEC 62366 | Phases 2–4: Discovery + Architecture + Specification | Usability Evaluation Report | Human factors and usability must be assessed. Include representative users in Phase 2 discovery; specify usability requirements in Phase 4; validate in Phase 6. |
| Post-market surveillance | MHRA SaMD Guidance §7 | Phase 7: Deploy & Learn | Post-Deployment Report + PMS Plan | A post-market surveillance plan must exist before deployment. The Phase 7 Post-Deployment Report is the first PMS output. Periodic surveillance reports must continue. |
| Vigilance reporting | MHRA Vigilance Guidance | Phase 7: Deploy & Learn | Incident Response Runbook | Serious incidents (death, serious deterioration in health) must be reported to MHRA. The Incident Response Runbook must include MHRA reporting procedures and timelines. |

---

## B.4 CQC — Care Quality Commission

### Applicability
Applies to health and social care providers registered with the CQC in England. Clinical management systems, patient record systems, and AI tools used in CQC-registered settings must support the provider's ability to demonstrate compliance with the Fundamental Standards.

### Obligation Mapping

| CQC Key Question | Regulation | AIDDLC Phase | Artifact | Implementation Guidance |
|---|---|---|---|---|
| Safe | Reg. 12: Safe care and treatment | Phases 1, 4, 6 | Compliance Matrix + Feature Specifications + Validation Report | Safety-critical features must be specified with explicit safety acceptance criteria. Validation must evidence safe operation. Risk Register must be maintained. |
| Effective | Reg. 11: Need for consent + Reg. 9: Person-centred care | Phase 4: Specification | Feature Specifications | Systems must support clinicians in delivering effective, evidence-based care. Features affecting clinical decision-making must be specified with reference to clinical evidence. |
| Caring | n/a | Phase 2: Discovery | Domain Analysis | Understand how the system supports (or could undermine) person-centred care. Include patient experience in the Domain Analysis. |
| Responsive | Reg. 17: Good governance | Phases 1, 7 | Intelligence Brief + Post-Deployment Report | Systems must support the provider's ability to identify and respond to issues. Monitoring and feedback capabilities must be specified. |
| Well-led | Reg. 17: Good governance | All phases | Context Package | CQC expects providers to evidence governance. The Context Package is the governance record. Ensure it is accessible for CQC inspection. |
| Audit readiness | Reg. 17: Good governance | All phases | Audit Log + Context Package | CQC inspectors may request evidence of how clinical decisions are made and audited. The Audit Log and Context Package must be accessible and readable within the timeframe CQC specifies (typically 10–15 minutes notice). |

---

## B.5 GPhC — General Pharmaceutical Council

### Applicability
Applies to pharmacy systems used in GPhC-registered pharmacies (including online pharmacies). Dispensing systems, patient medication records, and pharmacy management software are in scope.

### Obligation Mapping

| Standard | Reference | AIDDLC Phase | Artifact | Implementation Guidance |
|---|---|---|---|---|
| Safe and effective practice | GPhC Standards §1 | Phases 1, 4 | Intelligence Brief + Feature Specifications | Systems must support safe dispensing. Clinical checking features must be specified with explicit safety criteria. The Intelligence Brief must identify patient safety as a primary success criterion. |
| Patient records | GPhC Standards §3 | Phases 3–4 | Data Model + Feature Specifications | Patient medication records must be complete, accurate, and accessible. Data model must support the required record structure. Retention requirements must be specified. |
| Controlled drug records | MDR 2001 + GPhC Guidance | Phase 4: Specification | Feature Specifications | Controlled drug recording requirements are precise. Every required field and every required check must be specified as a feature with testable acceptance criteria. |
| Responsible Pharmacist requirements | Pharmacy Order 2010 | Phase 4: Specification | Feature Specifications | Systems must support RP management: identifying the RP, recording RP absences and closures, ensuring no dispensing occurs without an RP. Specify as explicit features. |
| Superintendent Pharmacist governance | GPhC Standards §7 | Phase 1: Foundation | Stakeholder Map + Compliance Matrix | The Superintendent Pharmacist is the accountable person. Identify in Stakeholder Map. Map SP governance obligations in Compliance Matrix. |

---

## B.6 FCA — Financial Conduct Authority

### Applicability
Applies to FCA-authorised firms and their technology suppliers where the technology materially supports regulated activities. AI in credit decisions, fraud detection, customer communications, and financial advice requires particular attention.

### Obligation Mapping

| Obligation | Reference | AIDDLC Phase | Artifact | Implementation Guidance |
|---|---|---|---|---|
| Explainability of automated decisions | FCA PS19/4; FCA FS21/7 | Phase 3: Architecture | Architecture Decision Records | Automated credit, fraud, or pricing decisions must be explainable to customers and regulators. The architecture must support explainability — black-box models that cannot explain individual decisions may not satisfy FCA requirements. Document in ADR. |
| Senior Manager accountability | SMCR | Phase 1: Foundation | Stakeholder Map | The accountable Senior Management Function (SMF) must be named in the Stakeholder Map. AI-related accountabilities must be clearly assigned. |
| Consumer Duty | FCA PS22/9 | Phases 2–4 | Domain Analysis + Feature Specifications | Systems must deliver good outcomes for retail customers. Include customer outcome testing in Phase 2; specify customer-protection features explicitly in Phase 4; evidence outcomes in Phase 7. |
| Operational resilience | FCA PS21/3 | Phases 3, 6 | Architecture + Validation Report | Important business services must remain within impact tolerances during disruptions. Design for resilience in Phase 3; validate resilience in Phase 6. |
| Audit trails | FCA SYSC 9 | Phases 5, 7 | Build Log + Audit Log | Records of business communications and AI-assisted decisions must be retained. Specify retention requirements in Phase 4; build to spec in Phase 5; validate in Phase 6. FCA retention periods apply (typically 5–7 years). |
| Model risk | FCA DP5/22 | Phase 3: Architecture | ADR + Risk Register | AI/ML models used in regulated decisions must be subject to model risk management: validation, documentation, performance monitoring, and an inventory. |

---

## B.7 HIPAA — Health Insurance Portability and Accountability Act

### Applicability
Applies to covered entities (health plans, providers, clearinghouses) and their business associates processing Protected Health Information (PHI) of US individuals.

### Obligation Mapping

| Rule | Obligation | AIDDLC Phase | Artifact | Implementation Guidance |
|---|---|---|---|---|
| Privacy Rule | PHI minimum necessary | Phases 3–4 | Data Model + Feature Specifications | Access to PHI must be limited to the minimum necessary for the intended purpose. Data model must support role-based access controls with PHI minimum-necessary enforcement. |
| Security Rule | Administrative safeguards | Phase 1: Foundation | Compliance Matrix | Conduct a Security Risk Analysis before architecture. The Risk Register supplements this analysis. |
| Security Rule | Technical safeguards | Phase 3: Architecture | Architecture Decision Records | Access controls, audit controls, integrity controls, and transmission security must be designed into the architecture. |
| Security Rule | Audit controls | Phases 3, 5 | ADR + Audit Log | Audit controls must record and examine activity in information systems containing PHI. Specify in Phase 4; build in Phase 5. |
| Breach Notification Rule | Notification of breach | Phase 3: Architecture | Incident Response Runbook | Breach notification to HHS and individuals within 60 days. Design the breach detection and notification capability in Phase 3; specify in Phase 4. |
| Business Associate Agreements | BAA with vendors | Phase 1: Foundation | Compliance Matrix | All vendors processing PHI on your behalf must have executed BAAs. Identify vendors in Phase 2 (Integration Map); ensure BAAs are in place before Phase 5 build involves PHI. |

---

## B.8 EU AI Act

### Applicability
Applies to AI systems placed on the EU market or used within the EU. Risk classification determines the extent of obligations. High-risk AI systems (Annex III) include AI used in healthcare, education, employment, essential services, law enforcement, border control, justice, and democratic processes.

### Obligation Mapping

| Obligation | Article | AIDDLC Phase | Artifact | Implementation Guidance |
|---|---|---|---|---|
| Risk classification | Arts. 6–7 | Phase 1: Foundation | Compliance Matrix | Classify the AI system. If high-risk (Annex III), all subsequent obligations apply. If limited-risk (chatbots, deep fakes), transparency obligations apply. Document classification and rationale in Compliance Matrix. |
| Quality management system | Art. 9 | All phases | Context Package | High-risk AI systems require a QMS. AIDDLC with full conformance constitutes a QMS when supplemented by the Compliance Matrix and Compliance Officer role. |
| Technical documentation | Art. 11 | Phases 3–4 | ADR + Feature Specifications + Data Model | Technical documentation must be maintained and updated. The accumulated Context Package satisfies this requirement if it includes all required content (training data description, system architecture, capabilities and limitations, performance metrics). |
| Data governance | Art. 10 | Phases 2–3 | Domain Analysis + Data Model | Training and test data must be subject to governance practices: relevance, representativeness, freedom from errors, completeness. Document in Phase 2; enforce in Phase 3. |
| Transparency | Art. 13 | Phase 4: Specification | Feature Specifications | Users must be informed they are interacting with an AI system. This must be specified as a feature with testable acceptance criteria. |
| Human oversight | Art. 14 | Phases 3–4 | ADR + Human Oversight Protocol | High-risk AI systems must allow natural persons to oversee and intervene. Design human oversight into the architecture in Phase 3; specify override and escalation features in Phase 4. |
| Accuracy, robustness, cybersecurity | Art. 15 | Phase 6: Validation | Validation Report | Performance metrics must be documented and validated before deployment. Include accuracy, robustness under perturbation, and cybersecurity validation. |
| Conformity assessment | Art. 43 | Phases 1 + 6 | Compliance Matrix + Validation Report | High-risk AI systems require conformity assessment before market placement. Initiate process in Phase 1; complete with Validation Report evidence in Phase 6. |
| Registration | Art. 49 | Phase 7: Deploy & Learn | Deployment Record | High-risk AI systems must be registered in the EU AI database before being placed on the market. Record registration in Phase 7. |

---

## B.9 ISO/IEC 27001 — Information Security Management

### Applicability
Applies to any implementation seeking ISO 27001 certification or operating within a certified ISMS. Also applicable as a framework for structured information security management in any context.

### Obligation Mapping

| Control Domain | ISO 27001 Reference | AIDDLC Phase | Artifact | Implementation Guidance |
|---|---|---|---|---|
| Information security policies | A.5 | Phase 1: Foundation | Compliance Matrix | Security policy requirements must be identified and mapped. |
| Risk assessment and treatment | A.6 | Phases 1–2 | Risk Register | The AIDDLC Risk Register, when structured to ISO 27001 requirements, satisfies the risk assessment obligation. Include likelihood, impact, risk owner, and treatment for each risk. |
| Access control | A.8 | Phases 3–4 | Data Model + Feature Specifications | Access control requirements must be specified in Phase 4 and designed in Phase 3. Include role-based access, principle of least privilege, and access review. |
| Cryptography | A.8.24 | Phase 3: Architecture | Architecture Decision Records | Cryptographic controls must be specified and justified. Include: encryption in transit, encryption at rest, key management. Document in ADR. |
| Physical security | A.7 | Phase 3: Architecture | Infrastructure Specification | Physical security requirements for infrastructure must be specified. For cloud deployments, document the shared responsibility model. |
| Operations security | A.8 | Phases 5–7 | Build Log + Deployment Record | Change management, capacity management, malware protection, and logging/monitoring must be documented as part of operations. |
| Incident management | A.5.24–5.28 | Phase 3: Architecture | Incident Response Runbook | Security incident management procedure must be documented and tested. Include: detection, reporting, assessment, escalation, recovery, and lessons learned. |
| Supplier security | A.5.19–5.22 | Phase 2: Discovery | Integration Map | Supplier security obligations must be assessed as part of Integration Map development. Include security requirements in supplier contracts. |
| Business continuity | A.5.29–5.30 | Phase 3: Architecture | Infrastructure Specification | Business continuity requirements must be designed into the architecture. Include RTO and RPO requirements, backup and recovery, and failover. |

---

*Annex B is informative. It does not create additional normative requirements beyond those in Section 8 of the specification. Regulatory requirements change; verify current obligations with qualified counsel.*

*Last updated: 2026 · 10QBIT Technologies*
