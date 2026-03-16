# Annex A: Certification Criteria

*Normative. All "must" statements are requirements. All "should" statements are strong recommendations.*

---

## A.1 Purpose

This annex defines the conformance requirements for AIDDLC certification. Certification is issued solely by 10QBIT Technologies. See [github.com/aiddlc/certification](https://github.com/aiddlc/certification) for the application process.

---

## A.2 Engineering Track Conformance

An implementation achieves **AIDDLC Engineering Track Conformance** when it satisfies all of the following requirements.

### A.2.1 Role Assignment

1. All five roles defined in Section 3 (Intent Authority, Domain Expert, Technical Authority, AI Supervisor, Compliance Officer) must be assigned to named individuals at project initiation.
2. Role assignments must be documented in the Phase 1 Stakeholder Map.
3. A single individual may hold multiple roles unless otherwise prohibited by Regulated Conformance requirements (see A.3.1).

### A.2.2 Phase Execution

4. All seven Engineering Track phases must be executed in sequence: Foundation → Discovery & Intelligence → Architecture & Design → Specification → Build → Validation → Deploy & Learn.
5. Phase skipping is not permitted. A phase may only be abbreviated (with documented rationale) for non-regulated, non-safety-critical implementations where the Architectural Board has published an approved abbreviation policy.
6. Phase execution must be evidenced by the production of all required artifacts for each phase.

### A.2.3 Artifact Production

7. All required artifacts listed in Sections 5.1 through 5.7 must be produced.
8. Each artifact must be: version-controlled, attributed to a named role owner, and approved by the role specified in the phase definition.
9. Artifacts must be complete at the time of gate passage — artifacts completed after gate sign-off do not satisfy phase requirements.

### A.2.4 Gate Compliance

10. Gate criteria must be documented as met before the next phase begins. Documentation must record: the date of gate passage, the name of the approving role holder, and the status of each gate criterion.
11. Post-hoc gate approval is not permitted. An implementation that has begun a phase without the preceding gate being formally documented has not met this requirement, regardless of whether the gate criteria were substantively satisfied.
12. Gate documentation must be preserved in the Context Package.

### A.2.5 Context Package Integrity

13. A Context Package must be created at the end of Phase 1 and updated at each subsequent phase boundary.
14. Context Packages must be version-controlled with a version stamp identifying the phase boundary at which they were updated.
15. Context Packages must contain all required content as defined in Section 7.1.
16. A loading protocol must be documented and followed: no AI generation session begins without the current Context Package being explicitly loaded.

### A.2.6 AI Attribution

17. All AI-generated content in artifacts must be identified as AI-generated. Attribution format is at the implementation's discretion but must be applied consistently.
18. AI generation sessions must be logged: date, model or system used, prompt summary or reference, and output disposition (accepted / modified / rejected).

### A.2.7 Deviation Documentation

19. All deviations from approved specifications must be documented in the Deviation Register before or at the time the deviation is implemented.
20. Each deviation record must include: the specification section departed from, the nature of the departure, the rationale, and the approval of the Technical Authority.
21. Silent deviations (departures from specification without documentation and approval) are conformance violations.

### A.2.8 Audit Log

22. An audit log of all AI generation actions must be maintained throughout the implementation.
23. The audit log must be retained for a minimum of 24 months from the date of deployment, or longer as required by applicable regulation.
24. The audit log must be retrievable and readable without proprietary tooling.

---

## A.3 Regulated Conformance

An implementation in a regulated industry achieves **AIDDLC Regulated Conformance** when it satisfies all Engineering Track Conformance requirements (A.2) plus all of the following.

### A.3.1 Role Independence

1. The Compliance Officer role must be held by an individual who does not also hold the Technical Authority role. These roles must be independent.
2. For implementations subject to MHRA Software as a Medical Device guidance, the Compliance Officer must have documented competence in the applicable regulatory framework.

### A.3.2 Compliance Matrix

3. A Compliance Matrix must be completed as a Phase 1 required artifact.
4. The Compliance Matrix must identify all applicable regulations, map each regulatory obligation to the phase and artifact where it is evidenced, name the accountable party for each obligation, and record the status.
5. The Compliance Matrix must be reviewed and approved by the Compliance Officer.
6. The Compliance Matrix must be updated at each phase boundary to reflect the current compliance posture.

### A.3.3 Pre-Deployment Sign-Off

7. A written Compliance Sign-off must be obtained from the Compliance Officer before Phase 7 deployment.
8. The Compliance Sign-off must assert: that all applicable regulatory obligations have been met, that the evidence is complete and retained, and that the Compliance Officer has reviewed the Validation Report.
9. Deployment without a Compliance Sign-off is a Regulated Conformance violation.

### A.3.4 Retention

10. All Context Packages, phase artifacts, gate documentation, deviation records, and audit logs must be retained for the period required by the most restrictive applicable regulation.
11. In the absence of a specific regulatory retention requirement, the minimum retention period is 7 years from the date of deployment.
12. Retention must be in a format that remains accessible and readable throughout the retention period.

### A.3.5 Human Oversight Protocol

13. A Human Oversight Protocol must be documented before Phase 7 deployment.
14. The Human Oversight Protocol must identify: all AI outputs that inform decisions affecting regulated persons (patients, financial services customers, pharmaceutical dispensing decisions); the specific human review step required before each such output is acted upon; the escalation path when an AI output is uncertain or outside expected parameters.
15. The Human Oversight Protocol must be reviewed and approved by the Compliance Officer.

---

## A.4 Evidence Requirements

### A.4.1 Evidence Package

Applicants for certification must submit an Evidence Package comprising:

- Complete Context Package for one development cycle (all seven phases completed)
- Gate documentation for all seven phases (showing date, approver, criterion-by-criterion status)
- Deviation Register (complete, including zero-deviation declaration if applicable)
- Audit log sample covering a representative 30-day period during the build phase
- AI attribution examples from at least three different artifacts

For Regulated Conformance, additionally:
- Compliance Matrix (complete, with final status column)
- Compliance Sign-off document
- Human Oversight Protocol
- Retention policy documentation

### A.4.2 Self-Assessment

Before submitting an Evidence Package, applicants must complete the AIDDLC Self-Assessment Checklist (published at [github.com/aiddlc/certification/self-assessment](https://github.com/aiddlc/certification/self-assessment/checklist.md)) and include the completed checklist in their submission.

---

## A.5 Certification Period

Certification is valid for 24 months from the date of issue.

Renewal requires submission of:
- A Post-Deployment Report from a cycle completed within the 24-month period
- Updated self-assessment checklist
- A statement of any changes to role assignments or process since initial certification

---

## A.6 Certification Register

Certified organisations are listed at [github.com/aiddlc/certification/register](https://github.com/aiddlc/certification/register/certified-organisations.md).

Listing includes: organisation name, certification level, industry vertical, date of certification, and certificate ID. No further details are published without the organisation's explicit consent.

---

*Annex A is normative. Certification requirements may be updated as Minor changes per the governance process. The current version applies to all applications submitted after its publication date.*
