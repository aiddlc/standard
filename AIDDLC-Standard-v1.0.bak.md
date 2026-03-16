# AIDDLC Standard v1.0
*AI-Driven Development Lifecycle*

*Published by 10QBIT Technologies · 2026 · CC BY 4.0*

---

## Abstract

The AIDDLC Standard defines a structured lifecycle for software development in which artificial intelligence systems and human teams operate with clearly defined roles, responsibilities, and handoff protocols. It establishes the phase architecture, gate criteria, artifact requirements, context continuity model, and compliance obligations that together constitute a complete and auditable AI-assisted development process.

This standard is designed for teams building software in environments where quality, traceability, and accountability are non-negotiable — including regulated industries such as healthcare, financial services, and pharmaceutical delivery. It is equally applicable to any team seeking to move from ad-hoc AI tool use to a systematic, repeatable, and defensible AI-assisted development practice.

---

## Status of This Document

This is the first public release of the AIDDLC Standard, version 1.0.0, published in 2026.

**Normative status**: All sections of this document are normative unless explicitly marked as informative. The words "must", "must not", "required", and "shall" indicate normative requirements. The words "should", "should not", and "recommended" indicate strong recommendations that may be departed from with documented rationale. The words "may" and "optional" indicate permitted but not required behaviour.

**Version stability**: v1.x normative requirements will not change in a breaking manner until v3.0 at the earliest. Patch and minor updates are backwards-compatible by definition. See Section 10 for the full versioning policy.

**Reporting issues**: Specification issues, clarification requests, and change proposals are managed at [github.com/aiddlc/standard](https://github.com/aiddlc/standard). See [CONTRIBUTING.md](https://github.com/aiddlc/.github/blob/main/CONTRIBUTING.md) for the contribution process.

---

## 1. Governing Principle

**Humans define intent and validate outcomes. AI executes craft and maintains continuity. Every decision is preserved. Every output is auditable. Quality is a system property, not a human heroic act.**

This principle is not a statement about AI capability. It is a statement about the appropriate division of authority in a system that combines human judgement with AI execution. It holds regardless of how capable AI systems become, because the source of value in AI-assisted development is not the AI system's ability to generate — it is the human team's ability to define what must be generated and to validate that what was generated is correct.

The governing principle has five consequences for how teams work:

1. Human intent — the definition of what the system must achieve and why — must be captured explicitly before AI generation begins. An AI system that generates without an approved intent definition is operating without constraint.

2. AI systems execute the work of translating intent into implementation: architecture, specification, code, tests, documentation. This is craft work. It is valuable. It is also the work that must be directed and supervised.

3. Continuity — the preservation of context across sessions, phases, and personnel changes — is an AI responsibility. Humans should not be required to reconstruct context; AI systems should maintain it.

4. Every decision made in the lifecycle — architectural, technical, product, compliance — must be preserved with its rationale. Decisions that cannot be retrieved cannot be audited, defended, or built upon.

5. Quality in AI-assisted development is achieved through process design, not individual heroics. A well-designed process produces consistent quality. A poorly-designed process produces quality only when the right person happens to be paying attention.

---

## 2. The Five Principles

### 2.1 Intent over Implementation

**Definition**: The intent of a system — what it must achieve, for whom, and why — takes precedence over all implementation choices. No implementation decision is valid without a traceable link to an approved intent.

**In practice**:
- Every development cycle begins with an explicit, approved intent statement before any technical work begins
- AI-generated options (architectures, approaches, algorithms) are evaluated against intent, not only against technical merit
- When AI suggests an approach that is technically elegant but does not serve the stated intent, the approach is rejected
- Scope creep introduced via AI suggestion — features generated that were not in the approved intent — is treated as a deviation requiring explicit approval

**This principle is violated when**: Technical work begins before an intent statement has been approved by the Intent Authority; when AI-generated output is accepted without validation against the approved intent; when the question "does this serve the intent?" is not asked at each gate.

---

### 2.2 Context Never Dies

**Definition**: All decisions, assumptions, constraints, rationale, and approved outputs are preserved and remain accessible throughout the lifecycle. Context is not summarised away; it is accumulated.

**In practice**:
- Context Packages are version-controlled documents that accumulate all project knowledge at each phase boundary
- AI generation sessions begin by loading the current Context Package — generation without a loaded context is a conformance violation
- When a decision is revisited, the original decision record is consulted and the new decision is appended (not replaced)
- Personnel changes do not cause context loss — the Context Package is the single authoritative record, not any individual's memory

**This principle is violated when**: A new AI generation session begins without loading the established context; when a decision is made that contradicts a prior decision without a documented rationale for the change; when context is "reset" between phases because it became unwieldy rather than structured.

---

### 2.3 Gates Before Generation

**Definition**: No phase begins until the preceding phase's exit criteria have been met and documented. Generation without a gate is generation without a foundation.

**In practice**:
- Each phase has a defined set of gate criteria — specific, checkable conditions that must all be met before the next phase begins
- Gate approval is documented, not assumed — a named approver signs off each gate
- Post-hoc gate approval (declaring a gate passed after the next phase has already started) is not permitted
- The gate criteria are not a formality — they represent the minimum information required for the next phase to produce correct output

**This principle is violated when**: A phase begins before the preceding phase's gate criteria are documented as met; when gate criteria are reduced to "good enough" assessments rather than specific checkable conditions; when speed pressure causes gate steps to be skipped with the intention of "catching up" in the next phase.

---

### 2.4 Continuous Validation

**Definition**: Validation is not a final phase — it is an activity that runs in parallel with every build cycle. Defects are identified and resolved at the point of introduction, not accumulated for a single validation gate.

**In practice**:
- Automated tests are generated alongside code, not after it
- Specification acceptance criteria are translated into automated test scenarios before build begins
- AI self-review of generated output is mandatory — AI systems must check their own output against the specification before presenting it for human review
- Human validation checkpoints exist at every phase gate, not only in the Validation phase

**This principle is violated when**: Testing is treated as a Phase 6 activity rather than a continuous one; when code is committed without automated tests covering the relevant acceptance criteria; when the Phase 6 Validation gate is the first time defects are systematically sought.

---

### 2.5 Auditable by Design

**Definition**: Every AI action, prompt, output, decision, and approval is logged, attributed, and retrievable. Auditability is a system design requirement, not a documentation retrospective.

**In practice**:
- AI generation actions are logged with: timestamp, model used, prompt used, output produced, human reviewer, and review decision
- All approved artifacts are version-controlled with named owners
- The Build Log links every code component to the specification entry that required it
- Compliance artifacts (Compliance Matrix, Compliance Sign-off, Human Oversight Protocol) are retained for the period required by applicable regulation

**This principle is violated when**: AI-generated content is committed without a record of what was generated and by whom it was reviewed; when a regulatory inspector could not determine, from the project's artifacts, who made any significant decision and why; when audit trail creation is deferred to after the fact.

---

## 3. Role Definitions

The AIDDLC Standard defines five roles. All five roles must be assigned to named individuals before Phase 1 begins. Roles may be combined where the responsibilities do not conflict — with the exception noted below.

| Role | Typical Position | Accountability | Authority | AI Interaction |
|---|---|---|---|---|
| **Intent Authority** | Product Owner, Founder, Clinical Lead, Executive Sponsor | Defines what the system must achieve and why; holds the vision | Approves phase gates; accepts or rejects final outcomes; approves deviations from intent | Provides intent input to AI; validates AI-surfaced options and recommendations; approves AI-generated intent artefacts |
| **Domain Expert** | Clinician, Compliance Officer, Subject Matter Expert, User Researcher | Validates domain correctness and regulatory alignment | Blocks gate passage when domain requirements are unmet; mandates re-work on domain errors | Reviews AI-generated domain content; provides corrections; validates AI-generated glossaries and domain analyses |
| **Technical Authority** | Lead Engineer, Principal Architect, CTO | Owns all technical decisions and the architecture | Approves technical gate criteria; selects implementation approach from AI-generated options; approves all architectural decisions | Reviews AI-generated architecture, data models, and API contracts; directs AI on technical constraints and non-functional requirements |
| **AI Supervisor** | Senior Engineer, Tech Lead, AI Engineer | Ensures AI outputs are correct, within scope, and free of hallucination or context drift | Can halt AI generation at any point; escalates quality failures; approves AI generation session start | Direct — monitors every prompt, every output, and every model behaviour decision throughout the lifecycle |
| **Compliance Officer** | Legal Counsel, Regulatory Affairs Manager, DPO | Ensures all applicable regulatory obligations are met and evidenced | Blocks deployment; mandates re-work on compliance failures | Reviews AI-generated compliance content; owns Compliance Matrix; signs off compliance gate criteria |

**Note on role combination**: The Compliance Officer role must not be combined with the Technical Authority role in regulated implementations. The independence of compliance oversight from technical delivery is a regulatory requirement in most governed industries (MHRA, FCA, CQC) and must be maintained.

**Note on scale**: In small teams, one person may hold multiple roles. A two-person team might have one person serving as Intent Authority and Domain Expert, and another as Technical Authority, AI Supervisor, and Compliance Officer. This is acceptable provided the responsibilities of each role are genuinely fulfilled and documented as such.

---

## 4. Phase Architecture

### 4.1 Overview

The AIDDLC Standard defines a seven-phase directed development cycle for the Engineering Track. The phases are sequential: each phase produces the artifacts that are required as inputs to the next phase. No phase may begin until the preceding phase's gate criteria are met.

The phases are not waterfall in the traditional sense. Feedback loops are an explicit feature of the architecture: any phase may trigger a return to an earlier phase when new information reveals that a prior phase's output is insufficient. However, such returns must be documented as decisions — they are not informal backtracking. The reason for the return, the artifact being revised, and the scope of revision are all recorded.

Each phase produces artifacts. Artifacts are not optional deliverables — they are required outputs. An artifact that has not been produced means the phase has not been completed, and the gate cannot be passed.

### 4.2 Phase Sequence

```
┌─────────────────────────────────────────────────────────────┐
│                   AIDDLC Engineering Track                  │
│                                                             │
│  ┌──────────────┐                                           │
│  │  Phase 1     │                                           │
│  │  Foundation  │                                           │
│  └──────┬───────┘                                           │
│         │ Gate 1                                            │
│  ┌──────▼───────────────────┐                              │
│  │  Phase 2                 │                              │
│  │  Discovery & Intelligence│                              │
│  └──────┬────────────────────┘                             │
│         │ Gate 2                                            │
│  ┌──────▼───────────────────┐                              │
│  │  Phase 3                 │                              │
│  │  Architecture & Design   │                              │
│  └──────┬────────────────────┘                             │
│         │ Gate 3                                            │
│  ┌──────▼───────────────────┐                              │
│  │  Phase 4                 │                              │
│  │  Specification           │                              │
│  └──────┬────────────────────┘                             │
│         │ Gate 4                                            │
│  ┌──────▼───────────────────┐                              │
│  │  Phase 5                 │                              │
│  │  Build                   │                              │
│  └──────┬────────────────────┘                             │
│         │ Gate 5                                            │
│  ┌──────▼───────────────────┐                              │
│  │  Phase 6                 │                              │
│  │  Validation              │                              │
│  └──────┬────────────────────┘                             │
│         │ Gate 6                                            │
│  ┌──────▼───────────────────┐                              │
│  │  Phase 7                 │                              │
│  │  Deploy & Learn          │                              │
│  └──────┬────────────────────┘                             │
│         │                                                   │
│         └──────────────────────► Next cycle Foundation     │
│                                                             │
│  ◄─────── Documented feedback returns permitted ──────────► │
└─────────────────────────────────────────────────────────────┘
```

### 4.3 Context Continuity

Each phase receives a Context Package from the prior phase and produces an updated Context Package for the next phase. The Context Package is the vehicle by which context never dies.

The Context Package is not a summary. It is a living document that accumulates all approved artifacts, all decisions with rationale, all deviations and their resolutions, all open risks and their current status, and the current compliance posture. At the end of each phase, the AI Supervisor version-stamps the Context Package and commits it to version control.

At the beginning of any AI work session within a phase, the AI Supervisor loads the current Context Package before any generation begins. The AI Supervisor confirms that the loaded context is current. Generation without a loaded, confirmed context is a conformance violation.

Phase 7 produces Context Package v7 — the complete cycle record. This becomes the input to the Foundation phase of the next development cycle, ensuring that nothing learned in one cycle is lost to the next.

---

## 5. Phase Definitions

### Phase 1: Foundation

**Purpose**: Establish the project's intent, compliance posture, stakeholder map, and success criteria before any technical work begins. Phase 1 is the only phase with no required technical input — it begins with human intent and ends with a structured, approved foundation for everything that follows.

**AI Responsibilities**:
- Draft the Intelligence Brief from intent inputs provided by the Intent Authority, for human review and approval
- Surface applicable regulatory obligations based on domain, geography, and system type described in the intent inputs
- Generate an initial stakeholder map for human review and completion
- Propose success criteria based on stated intent, for human approval
- Identify relevant prior art, comparable implementations, and known risks in the stated domain

**Human Responsibilities** (Intent Authority + Domain Expert + Compliance Officer):
- Define and approve the project intent statement — what the system must achieve, for whom, and why
- Validate and approve the compliance obligations surfaced by AI; add obligations not surfaced
- Confirm the stakeholder map and assign named individuals to each role
- Approve the success criteria — which must be measurable and owned by a named party
- Complete and approve Context Package v1

**Required Artifacts**:

| Artifact | Owner | Description |
|---|---|---|
| Intelligence Brief | Intent Authority | Defines what the project is, who it serves, and why it exists. Includes intent statement, scope boundaries, and known constraints. |
| Compliance Matrix | Compliance Officer | Maps all applicable regulations to project scope. For each obligation: applicable phases, evidence artifact, accountable party, and status. |
| Stakeholder Map | Intent Authority | Identifies all five roles, their named holders, their authority, and their AI interaction type. |
| Success Criteria | Intent Authority | Measurable, testable outcomes that define project success. Each criterion must be owned by a named party and have a defined measurement method. |
| Context Package v1 | AI Supervisor | All Phase 1 artifacts, approved and version-stamped. Authoritative input to Phase 2. |

**Gate Criteria** (all must be met and documented before Phase 2 begins):
- [ ] Intelligence Brief reviewed and approved by Intent Authority — signature and date recorded
- [ ] Compliance Matrix reviewed and approved by Compliance Officer (or formally waived with documented rationale for projects with no applicable regulated obligations)
- [ ] All five roles assigned to named individuals — no role left vacant or assigned to "TBD"
- [ ] Success Criteria documented, measurable, and approved by Intent Authority
- [ ] Context Package v1 committed to version control with version stamp

**Context Handoff**: Context Package v1 contains the approved Intelligence Brief, Compliance Matrix, Stakeholder Map, and Success Criteria. It is the sole authoritative input to Phase 2. No Phase 2 work may begin without it.

---

### Phase 2: Discovery & Intelligence

**Purpose**: Map the domain with sufficient depth and precision that the architectural choices made in Phase 3 are well-founded. Surface the risks, constraints, integration points, and edge cases that will determine whether the system succeeds or fails. Phase 2 is where the gap between stated intent and implementation reality is identified and documented.

**AI Responsibilities**:
- Analyse existing systems, documentation, data, and processes provided as inputs
- Surface domain risks and edge cases — specifically those that would not be apparent to a non-domain-expert engineer
- Generate a domain glossary for review by the Domain Expert
- Map all data flows, integration touchpoints, and external dependencies
- Identify compliance obligations at the feature level, not just the system level
- Flag contradictions or ambiguities in the input materials

**Human Responsibilities** (Domain Expert + Technical Authority):
- Validate all AI-surfaced domain analysis against actual domain knowledge
- Approve the risk register, adding risks not surfaced by AI
- Provide domain knowledge that cannot be derived from available documentation
- Sign off the domain glossary — every term used in Phase 3 and beyond must be in the glossary
- Approve the Integration Map against known system boundaries

**Required Artifacts**:

| Artifact | Owner | Description |
|---|---|---|
| Domain Analysis | Domain Expert | Validated map of the problem domain: processes, actors, data entities, and domain-specific constraints. |
| Risk Register | Technical Authority | All identified risks with: likelihood (High/Medium/Low), impact (High/Medium/Low), and mitigation approach. |
| Domain Glossary | Domain Expert | Defined terms for the project. All ambiguous terms must be resolved. All AI and human outputs in subsequent phases must use these definitions. |
| Integration Map | Technical Authority | All external systems, APIs, data sources, and integration protocols. Includes: integration type, data exchanged, ownership, and availability requirements. |
| Context Package v2 | AI Supervisor | Context Package v1 plus all Phase 2 artifacts, approved and version-stamped. |

**Gate Criteria**:
- [ ] Domain Analysis reviewed and approved by Domain Expert
- [ ] Risk Register reviewed and accepted by Technical Authority — no unmitigated High risks without a documented decision
- [ ] Domain Glossary agreed — all ambiguous terms resolved, no undefined terms remain
- [ ] Integration Map complete — all external dependencies documented
- [ ] Context Package v2 committed to version control

**Context Handoff**: Context Package v2 is the authoritative input to Phase 3.

---

### Phase 3: Architecture & Design

**Purpose**: Define the technical architecture, data model, and integration strategy to a level of precision that directly supports specification and code generation. Architectural decisions made in Phase 3 constrain everything that follows — they must be made deliberately, with alternatives considered, trade-offs assessed, and rationale recorded.

**AI Responsibilities**:
- Generate multiple candidate architecture options with explicit trade-off analysis against the Integration Map and Compliance Matrix
- Propose a data model based on the Domain Analysis and Domain Glossary
- Draft API contracts for all integration points identified in the Integration Map
- Surface architectural risks and known anti-patterns relevant to the selected approach
- Validate the candidate architectures against the Compliance Matrix — flag any architectural choice that creates compliance obligations or conflicts
- Generate an Infrastructure Specification based on the selected architecture

**Human Responsibilities** (Technical Authority):
- Select the architecture from AI-generated options — or explicitly reject all options and define a new approach, documenting the rationale
- Approve the data model; make any required adjustments
- Validate API contracts against the Integration Map
- Write or approve Architecture Decision Records for all significant architectural choices
- Ensure the selected architecture is compliant with all obligations in the Compliance Matrix

**Required Artifacts**:

| Artifact | Owner | Description |
|---|---|---|
| Architecture Decision Record (ADR) | Technical Authority | One or more ADRs documenting the selected architecture, rejected alternatives, and rationale for all significant architectural choices. |
| Data Model | Technical Authority | Approved entity-relationship model or equivalent. All entities named using Domain Glossary terms. |
| API Contracts | Technical Authority | Agreed interfaces for all integration points: endpoints, request/response schemas, authentication, error codes, and versioning. |
| Infrastructure Specification | Technical Authority | Compute, storage, network, and security requirements. Includes: availability requirements, disaster recovery approach, and environment specifications (development, staging, production). |
| Context Package v3 | AI Supervisor | Context Package v2 plus all Phase 3 artifacts, approved and version-stamped. |

**Gate Criteria**:
- [ ] ADR completed for all significant architectural choices — no major decision without a decision record
- [ ] Data Model reviewed and approved by Technical Authority
- [ ] API Contracts reviewed against the Integration Map — all integration points covered
- [ ] Infrastructure Specification complete and costed
- [ ] Architecture validated against the Compliance Matrix — no unresolved compliance conflicts
- [ ] Context Package v3 committed to version control

**Context Handoff**: Context Package v3 is the authoritative input to Phase 4.

---

### Phase 4: Specification

**Purpose**: Produce a complete, unambiguous specification of every feature, behaviour, and constraint in scope — sufficient for AI to generate correct code without further human clarification during Phase 5. Phase 4 is where ambiguity is driven out. Every question that could arise during build must be answered in the specification.

**AI Responsibilities**:
- Generate feature specifications from the approved architecture, organised by feature and mapped to the Domain Glossary
- Draft acceptance criteria for each feature — testable, binary, and linked to success criteria
- Surface specification gaps and ambiguities for human resolution — every AI-identified gap is documented and routed to the appropriate role for resolution
- Generate test scenarios from the specifications — one scenario per acceptance criterion at minimum
- Validate specification completeness against the Domain Glossary — flag any glossary term not represented in a feature specification

**Human Responsibilities** (Technical Authority + Domain Expert):
- Review and approve each feature specification — approval requires that the specification is unambiguous, correct, and implementable
- Resolve all AI-surfaced specification gaps — no gap may be deferred without a documented decision and rationale
- Validate acceptance criteria against the success criteria from Phase 1 — every success criterion must be traceable to one or more acceptance criteria
- Approve test scenario coverage

**Required Artifacts**:

| Artifact | Owner | Description |
|---|---|---|
| Feature Specification Set | Technical Authority | Complete specification for every feature in scope. Each specification includes: feature name, purpose, functional requirements, non-functional requirements, acceptance criteria, and edge case handling. |
| Acceptance Criteria | Domain Expert + Technical Authority | Testable, binary criteria for every feature. Each criterion linked to a success criterion. Format: "Given [context], when [action], then [outcome]." |
| Test Scenario Library | AI Supervisor | Generated test scenarios covering all acceptance criteria, reviewed by Technical Authority. Minimum one scenario per acceptance criterion. |
| Specification Completion Report | AI Supervisor | Confirms that every in-scope feature has an approved specification, every acceptance criterion is testable, and every glossary term is represented. |
| Context Package v4 | AI Supervisor | Context Package v3 plus all Phase 4 artifacts, approved and version-stamped. |

**Gate Criteria**:
- [ ] All in-scope features have approved specifications — no feature without a specification enters Phase 5
- [ ] All acceptance criteria are testable, unambiguous, and linked to success criteria
- [ ] No open specification gaps — all AI-surfaced gaps are resolved or explicitly deferred with documented rationale
- [ ] Test scenario coverage reviewed and approved by Technical Authority
- [ ] Specification Completion Report confirms 100% coverage of in-scope features
- [ ] Context Package v4 committed to version control

**Context Handoff**: Context Package v4 is the authoritative input to Phase 5.

---

### Phase 5: Build

**Purpose**: Generate, review, and commit production-quality code. AI generates from the approved specification; humans review, approve, and own. Every line of code has a specification source. Every deviation from specification is documented and approved.

**AI Responsibilities**:
- Generate code from approved specifications, maintaining traceability between every code component and its specification source
- Write unit tests and integration tests from the Test Scenario Library
- Perform self-review of generated code against the specification before presenting for human review — AI must not present code it has not checked
- Surface deviations from specification for human decision — if the specification cannot be implemented as written, this is a deviation requiring explicit approval, not a silent workaround
- Maintain the Build Log throughout: every component, every specification source, every review decision

**Human Responsibilities** (Technical Authority + AI Supervisor):
- Review all AI-generated code before merge — no code merges without human review
- Approve or reject AI-surfaced deviations — approved deviations are documented in the Deviation Register with rationale
- Maintain overall code ownership — the Technical Authority is responsible for the quality of all code, AI-generated or otherwise
- Ensure test coverage meets gate criteria at every stage of the build, not only at the gate

**Required Artifacts**:

| Artifact | Owner | Description |
|---|---|---|
| Source Code | Technical Authority | All code, version-controlled. Every significant component attributed to its specification source in code comments or commit metadata. |
| Test Suite | AI Supervisor | Unit and integration tests covering all acceptance criteria. Tests are version-controlled alongside source code. |
| Build Log | AI Supervisor | Links every code component to its specification source. Records: component name, specification reference, generation session, reviewer, and review decision. |
| Deviation Register | Technical Authority | Documents all approved deviations from specification: what deviated, why, what was done instead, who approved it, and the date of approval. |
| Context Package v5 | AI Supervisor | Context Package v4 plus all Phase 5 artifacts and the current build state, approved and version-stamped. |

**Gate Criteria**:
- [ ] All in-scope features implemented
- [ ] Test suite passes — all tests green, all acceptance criteria covered
- [ ] No unresolved specification deviations — all deviations either resolved or in the Deviation Register with approval
- [ ] Code review completed for all merged code — no unreviewed code in main
- [ ] Build Log complete — every component linked to its specification source
- [ ] Context Package v5 committed to version control

**Context Handoff**: Context Package v5 is the authoritative input to Phase 6.

---

### Phase 6: Validation

**Purpose**: Validate that the built system meets its specifications, acceptance criteria, success criteria, and compliance obligations before deployment. Validation is the comprehensive verification that what was specified was built, and that what was built works correctly, safely, and compliantly.

**AI Responsibilities**:
- Execute the automated test suite and generate a structured Validation Report
- Surface failing tests and compliance gaps with diagnostic information
- Perform regression analysis against the Deviation Register — verify that approved deviations do not create unforeseen consequences
- Generate an audit trail for compliance validation, linking each compliance obligation to the artifact that evidences it

**Human Responsibilities** (all roles as appropriate):
- **Domain Expert**: Conduct user acceptance testing (UAT), validating domain behaviour against the Feature Specification Set. Document findings.
- **Compliance Officer**: Review the compliance audit trail and sign off that all applicable regulatory obligations are evidenced. For regulated implementations, this sign-off is mandatory before Phase 7.
- **Intent Authority**: Validate the built system against the success criteria approved in Phase 1. Confirm that the system achieves what it was intended to achieve.
- **Technical Authority**: Approve infrastructure readiness and performance baseline.

**Required Artifacts**:

| Artifact | Owner | Description |
|---|---|---|
| Validation Report | AI Supervisor | Results of all automated validation: pass/fail per test, coverage metrics, defect summary, and regression analysis. |
| UAT Sign-off | Domain Expert | Documented results of user acceptance testing. Identifies any domain behaviour failures that automated testing did not catch. |
| Compliance Sign-off | Compliance Officer | Formal confirmation that all regulatory obligations are met and evidenced. Required for all regulated implementations. |
| Performance Baseline | Technical Authority | Measured performance against defined thresholds from the Infrastructure Specification. |
| Context Package v6 | AI Supervisor | Context Package v5 plus all Phase 6 artifacts and validation results, approved and version-stamped. |

**Gate Criteria**:
- [ ] All automated tests passing — no failing tests in main
- [ ] UAT completed and signed off by Domain Expert
- [ ] Compliance Sign-off obtained (mandatory for regulated implementations; for non-regulated, document the determination that no compliance sign-off is required)
- [ ] Performance targets met per the Infrastructure Specification
- [ ] No critical or high-severity defects open — all critical and high defects resolved or explicitly accepted with documented rationale
- [ ] Context Package v6 committed to version control

**Context Handoff**: Context Package v6 is the authoritative input to Phase 7.

---

### Phase 7: Deploy & Learn

**Purpose**: Deploy the validated system to production, monitor its behaviour, and feed learnings systematically into the next development cycle. Phase 7 closes the lifecycle loop: what is learned in production becomes the context that informs the next Foundation phase.

**AI Responsibilities**:
- Execute the deployment runbook under human direction and approval
- Monitor deployment health metrics in real time during and after deployment
- Surface anomalies and production incidents as they occur, with diagnostic context
- Generate the Post-Deployment Report from production metrics and incident records
- Update the Context Package with production learnings, ready for the next cycle

**Human Responsibilities** (Technical Authority + Intent Authority):
- Approve the deployment execution — no deployment without explicit approval
- Monitor and respond to production incidents during and after deployment
- Review the Post-Deployment Report and approve the lessons learned
- Decide, based on production data, what the next development cycle will address

**Required Artifacts**:

| Artifact | Owner | Description |
|---|---|---|
| Deployment Runbook | Technical Authority | Step-by-step deployment procedure. Includes: pre-deployment checks, deployment steps, rollback procedure, and success criteria for deployment completion. |
| Deployment Record | AI Supervisor | Timestamped log of deployment execution. Records: each step executed, timestamp, outcome, and any deviations from the runbook. |
| Post-Deployment Report | AI Supervisor | Metrics, incidents, and observations from the first 30 days in production. Includes: performance against baseline, incident summary, user feedback summary, and model behaviour observations (for AI-powered features). |
| Lessons Learned | Intent Authority | Approved summary of learnings to carry into the next cycle: what worked, what did not, what must change, and what should be preserved. |
| Context Package v7 | AI Supervisor | The complete cycle record. Contains all Context Packages v1–v6 plus all Phase 7 artifacts. This is the input to the Foundation phase of the next development cycle. |

**Gate Criteria** (deployment approval):
- [ ] Deployment Runbook reviewed and approved by Technical Authority
- [ ] Rollback procedure tested in a staging environment
- [ ] Monitoring and alerting active and verified
- [ ] Deployment executed and Deployment Record complete
- [ ] Post-Deployment Report generated within 30 days of deployment date

**Context Handoff**: Context Package v7 is the complete cycle record. It becomes the Foundation context for the next development cycle. This is the mechanism by which context never dies across cycles, across personnel changes, and across time.

---

## 6. Product Track

### 6.1 Overview

The Product Track governs the discovery, validation, deployment, and scaling of AI-powered product features. It operates in parallel with or independently of the Engineering Track, depending on the nature of the work. Where a product feature requires engineering infrastructure, the two tracks synchronise at defined integration points.

The Product Track recognises that AI product development has a distinct validation challenge: unlike conventional software, the quality of an AI feature is not fully determinable from its specification alone. Model behaviour, prompt architecture, output quality, and user trust must all be validated empirically before committing to full engineering. The Product Track mandates this validation.

The Product Track has four phases. Each phase contains **[COMMUNITY DEVELOPMENT AREA]** sections — these are open for community contribution under the Minor change process. See [annexes/product-track-community.md](annexes/product-track-community.md) for the specific questions the Architectural Board has posed to the community.

### 6.2 Relationship to Engineering Track

| Product Track Phase | Engineering Track Synchronisation Point |
|---|---|
| PT-1: Discover | Gate 1 (Foundation) — problem-AI fit must be validated before AI features enter the Engineering Track scope |
| PT-2: Prototype | Gate 4 (Specification) — prompt architecture and quality baseline must be documented in the Feature Specification Set before build begins |
| PT-3: Deploy | Gate 6 (Validation) — AI-specific metrics and human oversight protocol must be validated before Phase 7 deployment |
| PT-4: Scale | Context Package v7 — value realisation data informs the next Foundation phase |

---

### Phase PT-1: Discover

**Purpose**: Validate that the identified problem is one where AI adds genuine value over rule-based or human approaches. Define the AI capability required, and select the model or approach that best serves the intent. Do not build until problem-AI fit is demonstrated.

**Activities**:
- Problem definition: what specific problem is being solved, for which users, in which context?
- AI capability mapping: what can AI do in this context? What requires human judgement and cannot be delegated to AI? Where is AI a genuine advance over rule-based or human approaches?
- Model selection: evaluate candidate models against the requirements of this specific problem — capability, cost, compliance obligations, latency, throughput, and data residency requirements
- Data availability assessment: what data is required to implement and validate this AI feature? Is it available? Is it compliant?
- Regulatory pre-assessment: does this AI feature trigger specific AI-related regulatory obligations? (EU AI Act risk classification; MHRA AI/ML guidance for medical software; FCA expectations for automated decision-making)

**Required Artifacts**:
- **Problem Statement** (approved by Intent Authority): what the AI feature is, who it serves, what specific problem it solves, and what "good" looks like
- **AI Capability Map**: structured assessment of what AI can and cannot do in this context
- **Model Selection Record**: documents each model evaluated, the criteria used, and the rationale for the selected model
- **Regulatory Pre-Assessment**: identifies whether this AI feature triggers specific AI-related regulatory obligations, and if so, what they are

**Gate Criteria**:
- [ ] Problem-AI fit validated — evidence that AI adds value over rule-based or human approach (not assertion; evidence)
- [ ] Model selected and rationale documented in Model Selection Record
- [ ] Regulatory obligations specific to the AI feature identified and added to the Compliance Matrix

**[COMMUNITY DEVELOPMENT AREA: Model Selection Framework]**
The AIDDLC community is developing a standardised model selection framework. See [annexes/product-track-community.md](annexes/product-track-community.md) for the specific questions and contribution process.

---

### Phase PT-2: Prototype

**Purpose**: Validate the AI approach against real user needs before committing to full engineering. Build the minimum implementation required to determine whether the approach works and whether users find it valuable. Measure before you build at scale.

**Activities**:
- Rapid prototyping with the selected model, focused on the highest-risk assumptions from PT-1
- LLM quality benchmarking: measure output quality against domain-specific criteria, not just generic benchmarks
- UX validation with representative users: does the AI output genuinely serve users in their context?
- Prompt architecture definition: the systematic design of prompts, context injection, and output formatting required to achieve consistent quality
- Output quality baseline: establish measurable quality metrics that the production implementation must meet or exceed

**Required Artifacts**:
- **Prototype Evaluation Report**: quantitative and qualitative assessment of prototype quality against the success criteria defined in PT-1
- **Prompt Architecture Document**: the prompt design, context injection approach, output formatting requirements, and known failure modes
- **UX Validation Findings**: structured results of user validation sessions with representative users
- **Quality Baseline Metrics**: the specific, measurable quality thresholds the production implementation must meet

**Gate Criteria**:
- [ ] Prototype meets minimum quality threshold defined in the PT-1 gate criteria
- [ ] UX validation completed with representative users — not internal team members only
- [ ] Prompt architecture documented and reviewed
- [ ] Decision to proceed to full build is explicit, approved by Intent Authority, and documented

**[COMMUNITY DEVELOPMENT AREA: LLM Benchmarking for Product Validation]**
The community is developing standardised LLM benchmarking methodology. See [annexes/product-track-community.md](annexes/product-track-community.md).

---

### Phase PT-3: Deploy

**Purpose**: Deploy the validated AI feature with the monitoring, feedback loops, and human oversight mechanisms required for safe, measurable, and improvable operation. AI features in production must be observable in ways that conventional software is not.

**Activities**:
- A/B test framework design: how will the AI feature be tested against the baseline? What constitutes a meaningful performance difference?
- Feedback loop instrumentation: how will user feedback and implicit signals (corrections, abandonment, re-queries) be captured?
- AI-native metrics definition: standard SaaS metrics (DAU, conversion, NPS) do not capture AI product quality. Define the metrics that do: quality drift, user trust indicators, error taxonomy, feedback loop effectiveness
- Human-in-the-loop design: for any AI output that informs a consequential decision, define where a human checkpoint exists and what triggers it
- Model behaviour monitoring: define the alerts that indicate model performance degradation, context drift, or unexpected output distribution

**Required Artifacts**:
- **A/B Test Design**: hypothesis, control/variant definition, success metrics, and minimum detectable effect
- **Feedback Loop Specification**: what feedback signals are captured, how they are stored, and how they inform model improvement
- **AI Metrics Dashboard Specification**: the specific AI-native metrics that will be tracked, their definitions, measurement methods, and alert thresholds
- **Human Oversight Protocol** (required for regulated implementations): defines which AI outputs require human review before acting on, what triggers escalation, and who reviews

**Gate Criteria**:
- [ ] A/B test framework active and instrumented before deployment
- [ ] Feedback loops instrumented and tested
- [ ] AI-native metrics defined, measurable, and accessible from day one of production operation
- [ ] Human oversight protocol documented and in place for all high-stakes AI outputs

**[COMMUNITY DEVELOPMENT AREA: AI-Native Metrics]**
Standard SaaS metrics do not capture AI product quality. The community is developing a standard set of AI-native metrics. See [annexes/product-track-community.md](annexes/product-track-community.md).

---

### Phase PT-4: Scale

**Purpose**: Systematically grow the AI feature based on evidence of value delivery. Scale decisions are based on measurable outcomes, not assumptions. Financial and operational accountability for AI investment is established and maintained.

**Activities**:
- Value realisation measurement: what measurable value is the AI feature delivering? To users, to the business, to the regulated persons it serves?
- Token ROI analysis: what is the cost of AI inference per unit of user value delivered? Is this ratio improving or degrading as usage grows?
- Model ROI analysis: what is the total AI cost (inference, fine-tuning, integration, maintenance) versus the measurable business impact?
- Scaling decision framework: what evidence triggers a decision to scale? What evidence triggers a decision to plateau, pivot, or discontinue?
- Model upgrade assessment: when and how to evaluate whether a newer model version or alternative model would improve the ROI picture

**Required Artifacts**:
- **Value Realisation Report**: measured evidence of value delivered by the AI feature
- **Token ROI Analysis**: the ratio of measurable user value to AI inference cost, trended over time
- **Model ROI Report**: total AI investment versus total measurable business impact, with projection
- **Scaling Decision Record**: the evidence-based decision to scale (or not), with criteria, data, and approval from Intent Authority

**Gate Criteria**:
- [ ] Positive Token ROI demonstrated — scaling without demonstrated ROI requires explicit Intent Authority approval and documented rationale
- [ ] Scaling decision approved by Intent Authority
- [ ] Infrastructure capacity plan for scaled operation — scaling cannot outpace infrastructure readiness

**[COMMUNITY DEVELOPMENT AREA: Value Realisation Frameworks]**
The community is developing sector-specific value metrics and Token ROI calculation templates. See [annexes/product-track-community.md](annexes/product-track-community.md).

---

## 7. Context Continuity Model

### 7.1 Structure

A Context Package is a version-controlled document that contains the accumulated knowledge of the project at a given phase boundary. It is not a summary — it is the authoritative record. Summaries lose information. Context Packages accumulate it.

A complete Context Package contains all of the following:

- **Approved artifacts**: all approved artifacts from all completed phases, in their approved versions
- **Decisions**: all decisions made, with rationale, date, and the role of the person who made or approved the decision
- **Deviations**: all deviations from specification, with the resolution and the approval record
- **Open risks**: all risks from the Risk Register, with their current status and any mitigations applied
- **Compliance posture**: the current Compliance Matrix, with status updated to reflect the current phase
- **Glossary**: the current Domain Glossary, updated with any terms added during the current cycle

The Context Package is the single source of truth for the project. If there is a conflict between the Context Package and any other artifact, the Context Package (as the more recently version-stamped document) takes precedence — or the conflict must be escalated to the appropriate role for resolution.

### 7.2 Loading Protocol

At the start of any AI work session, the AI Supervisor must:

1. Identify the current Context Package version (e.g. "Context Package v3 — phase 3 approved 2026-03-01")
2. Load the full Context Package into the AI session context
3. Confirm that the loaded context matches the version-controlled document — the AI Supervisor must verify this, not assume it
4. Record the confirmation in the session log
5. Only then begin any generation activity

AI generation without a confirmed, loaded Context Package is a conformance violation. It is the AI Supervisor's responsibility to enforce this. An AI system that generates without context is operating without the constraints that make its output trustworthy.

### 7.3 Drift Detection

Context drift occurs when AI-generated output diverges from the established context without a documented decision. Drift is insidious: it begins with small inconsistencies and, if uncorrected, accumulates into a state where the AI's outputs are systematically misaligned with the project's established decisions.

The AI Supervisor monitors for drift by:

- **Terminology drift**: comparing generated output against the Domain Glossary. Any term used that is not in the Glossary, or used differently from the Glossary definition, is a drift indicator and must be corrected.
- **Architectural drift**: comparing generated code and specifications against the Architecture Decision Records. Any output that implies a different architecture from the one approved must be surfaced immediately.
- **Decision contradiction**: comparing generated recommendations against prior decisions. Any output that recommends a course of action already explicitly rejected must be flagged, the prior decision re-presented, and the AI re-directed.
- **Scope drift**: comparing generated output against the approved intent and feature specifications. Any output that introduces features, behaviours, or interfaces not in the approved scope must be rejected and the deviation decision made explicitly.

When drift is detected, the AI Supervisor does not silently correct it. Drift is recorded in the session log, the correction is documented, and if the drift reveals a genuine specification gap, a proposal issue is opened.

---

## 8. Compliance Integration

### 8.1 Regulatory Mapping

The AIDDLC Standard has been designed with explicit reference to the following regulatory frameworks. The mapping below identifies which phases each regulation is most relevant to, and what the key obligations are. This mapping is informative — implementations must conduct their own regulatory assessment based on their specific scope, jurisdiction, and risk profile.

| Regulation | Jurisdiction | Applicable Phases | Key Obligations |
|---|---|---|---|
| **GDPR / UK GDPR** | EU / UK | Foundation, Architecture, Specification, Validation | Data minimisation, lawful basis identification, DPIA for high-risk processing, data subject rights as specified features, privacy by design |
| **MHRA (Software as a Medical Device)** | UK | Foundation, Architecture, Validation, Deploy | Clinical evidence, intended purpose definition, risk management (ISO 14971), post-market surveillance |
| **CQC (Care Quality Commission)** | England | Foundation, Specification, Validation | Safe and effective care standards, governance and audit trail requirements, evidence of clinical oversight |
| **GPhC (General Pharmaceutical Council)** | UK | Foundation, Specification, Validation | Safe dispensing standards, patient safety evidence, prescription handling record-keeping |
| **FCA (Financial Conduct Authority)** | UK | Foundation, Architecture, Validation | Explainability of automated decisions, senior manager accountability (SMCR), audit trail retention |
| **HIPAA** | USA | Foundation, Architecture, Specification, Validation | PHI protection, access controls, audit logging, breach notification procedures |
| **ISO 27001** | International | Architecture, Build, Validation | Information security management, risk treatment, controls against ISMS scope |
| **EU AI Act** | EU | Foundation, Architecture, Validation, Deploy | Risk classification, technical documentation, transparency obligations, human oversight for high-risk AI, accuracy and robustness requirements |

### 8.2 Compliance in Practice

For each applicable regulation, the Compliance Matrix — a Phase 1 required artifact — maps:

- The specific obligations that apply to this project in this jurisdiction, based on the actual scope of the system
- The phase and artifact where each obligation is evidenced (not claimed — evidenced by a specific artifact produced in that phase)
- The named Compliance Officer or Domain Expert accountable for each obligation
- The current status: Met (evidence exists), In Progress (evidence being produced in the current phase), or Not Applicable (with documented rationale)

The Compliance Matrix is not completed once and archived. It is a living document, updated as each phase produces new evidence. At Phase 7, the Compliance Matrix must show all obligations as "Met" before the Compliance Sign-off is issued.

---

## 9. Conformance Requirements

### 9.1 Full Conformance

An implementation is **AIDDLC Fully Conformant** if it meets all of the following requirements:

1. Assigns all five roles defined in Section 3 to named individuals at project initiation, before Phase 1 begins
2. Executes all seven Engineering Track phases in sequence, with no phase skipped
3. Produces all required artifacts for each phase, as listed in the phase definitions in Section 5
4. Meets all gate criteria for each phase before the next phase begins, with gate approval documented
5. Maintains Context Packages as defined in Section 7, version-controlled and committed at each phase boundary
6. Implements audit logging for all AI generation actions throughout the lifecycle
7. Documents all deviations from specification in the Deviation Register, with approval records

### 9.2 Regulated Conformance

An implementation operating in a regulated industry is **AIDDLC Regulated Conformant** if it meets all Full Conformance requirements, plus all of the following:

1. Assigns a named Compliance Officer who is independent of the Technical Authority role
2. Completes a Compliance Matrix in Phase 1 covering all applicable regulations
3. Obtains formal Compliance Sign-off before Phase 7 deployment proceeds
4. Retains all Context Packages and required artifacts for the period required by the most restrictive applicable regulation (minimum 7 years in the absence of a more specific requirement)
5. Implements and documents a Human Oversight Protocol for any AI output that informs a decision affecting a regulated person (patient, financial services customer, prescription recipient, etc.)
6. Produces regulatory evidence artifacts as part of the normal phase artifact set, not as a separate retrospective documentation exercise

### 9.3 AIDDLC-Aligned

There is no partial conformance certification. Implementations that do not meet the full criteria for Section 9.1 may describe their process as "AIDDLC-Aligned" provided:

- They implement at least five of the seven Engineering Track phases
- They document the phases they execute with the required artifacts for those phases
- They do not claim conformance or certification

The AIDDLC-Aligned designation acknowledges a genuine partial adoption of the standard. It is not a lesser tier of certification — it is an honest description of an implementation in progress.

---

## 10. Governance

### 10.1 Versioning

This specification follows `MAJOR.MINOR.PATCH` semantic versioning:

- **PATCH** (`x.y.Z`): Non-normative changes. Clarifications, corrections, example additions, editorial improvements. No normative requirement changes. No implementation impact. Backwards compatible by definition.

- **MINOR** (`x.Y.0`): New normative content that is backwards compatible. New phases, new required artifacts, new compliance mappings, new conformance requirements. An implementation that was conformant before a Minor release remains conformant — it may optionally adopt new requirements. Minor updates do not break existing conformance.

- **MAJOR** (`X.0.0`): Changes to existing normative requirements. An implementation that was conformant before a Major release must update its process to remain conformant. Major releases are preceded by a public draft period and a migration guide.

Current version: **1.0.0**

### 10.2 Stability Commitment

v1.x normative requirements will not change in a breaking manner until v3.0 at the earliest. This means:

- v1.0 implementations can rely on the normative requirements remaining stable through at least v2.x
- If breaking changes are introduced in v2.0, v1.x continues to be supported for 24 months after v2.0 release
- Breaking changes require the full governance process defined in GOVERNANCE.md, including a 90-day public review period

### 10.3 Architectural Authority

The Architectural Board at 10QBIT Technologies holds authority over all normative requirements. Board composition, the change process, and the versioning policy are published at [github.com/aiddlc/.github](https://github.com/aiddlc/.github).

Community contributions are reviewed under the process defined in CONTRIBUTING.md. The Architectural Board's decisions on normative matters are final, made in accordance with the governance model, and recorded as Decision Records.

---

## 11. Glossary

| Term | Definition |
|---|---|
| **Acceptance Criteria** | Testable, binary conditions that a feature must satisfy to be considered complete. Format: "Given [context], when [action], then [outcome]." Acceptance criteria are approved in Phase 4 and used as the basis for automated tests in Phase 5. |
| **AI Supervisor** | The human role responsible for directing, monitoring, and validating AI behaviour throughout the lifecycle. The AI Supervisor is accountable for context loading, drift detection, deviation surfacing, and the integrity of all AI-generated artifacts. |
| **Architecture Decision Record (ADR)** | A document recording a significant architectural decision, its context, the alternatives considered, and the rationale for the decision made. ADRs are required artifacts in Phase 3 and are accumulated in the Context Package. |
| **Artifact** | A defined output of a phase: a document, record, or other deliverable that is version-controlled, owned by a named role, and required before the phase's gate can be passed. |
| **Build Log** | A Phase 5 required artifact that links every code component to the specification entry that required it. The Build Log is the traceability mechanism connecting implementation to intent. |
| **Compliance Matrix** | A Phase 1 required artifact that maps all applicable regulatory obligations to the project scope: the phase and artifact where each obligation is evidenced, the accountable party, and the current status. |
| **Conformance** | The property of an implementation that meets all requirements of a specified conformance level (Full Conformance or Regulated Conformance) as defined in Section 9. |
| **Context Drift** | A condition where AI-generated output diverges from the established project context (decisions, glossary, architecture, specifications) without a documented decision authorising the divergence. Context drift is detected by the AI Supervisor and must be corrected and recorded. |
| **Context Package** | A version-controlled, accumulating document containing all approved artifacts, decisions, deviations, open risks, compliance posture, and the Domain Glossary at a given phase boundary. Context Packages are the mechanism by which Context Never Dies. |
| **Deviation** | An intentional departure from an approved specification, documented in the Deviation Register with rationale and approved by the Technical Authority. Silent deviations (departures from specification without documentation) are conformance violations. |
| **Domain Expert** | The human role with authoritative knowledge of the problem domain — the domain that the system serves. The Domain Expert validates AI-generated domain content, approves the Domain Glossary, and conducts UAT in Phase 6. |
| **Domain Glossary** | The agreed vocabulary for the project, approved by the Domain Expert in Phase 2. All terms used by AI and humans in Phase 3 and beyond must be drawn from the Domain Glossary. Terms not in the Glossary must be added to it before use. |
| **Gate** | A defined checkpoint between phases. A gate consists of a set of criteria, all of which must be documented as met before the next phase begins. Gate approval is recorded with the name of the approver and the date. |
| **Intelligence Brief** | The Phase 1 required artifact that defines the project: what it is, who it serves, why it exists, what it must achieve, and what constraints bound it. The Intelligence Brief is approved by the Intent Authority and becomes the foundation of all subsequent context. |
| **Intent Authority** | The human role that defines what the system must achieve and why. The Intent Authority approves the Intelligence Brief, the Success Criteria, and all phase gates. The Intent Authority's approval is the ultimate validation that outcomes match intent. |
| **Phase** | A discrete stage of the development lifecycle with defined inputs (Context Package), activities, AI responsibilities, human responsibilities, required artifacts, and gate criteria. No phase begins until the preceding phase's gate is passed. |
| **Post-Deployment Report** | A Phase 7 required artifact generated by the AI Supervisor from production metrics and incident records within 30 days of deployment. The Post-Deployment Report feeds into the Lessons Learned and the next cycle's Context Package. |
| **Regulated Conformance** | The higher conformance level, applicable to implementations in regulated industries. Includes all Full Conformance requirements plus Compliance Officer independence, Compliance Matrix, pre-deployment Compliance Sign-off, retention obligations, and Human Oversight Protocol. |
| **Test Scenario Library** | A Phase 4 required artifact containing AI-generated test scenarios — a minimum of one per acceptance criterion — reviewed by the Technical Authority and used as the basis for the automated test suite in Phase 5. |
| **Token ROI** | The ratio of measurable user value delivered by an AI feature to the AI inference cost consumed in delivering it, expressed as value-per-token or equivalent unit. A key metric in PT-4: Scale. |
| **Validation** | The process of confirming that built outputs meet their specifications, acceptance criteria, success criteria, and compliance obligations. In the AIDDLC Standard, validation is a continuous activity throughout the lifecycle, not only a Phase 6 activity. |

---

*AIDDLC Standard v1.0.0 · 10QBIT Technologies · 2026 · CC BY 4.0*

*Cite as: AIDDLC Standard v1.0, 10QBIT Technologies, 2026, https://aiddlc.ai/spec*
