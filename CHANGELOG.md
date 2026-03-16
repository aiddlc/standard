# Changelog

All normative changes to the AIDDLC Standard are recorded in this file. Changes are categorised as Patch, Minor, Major, or Breaking per the classification defined in [GOVERNANCE.md](https://github.com/aiddlc/.github/blob/stable/GOVERNANCE.md).

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

---

## [1.0.0] — 2026

Initial public release of the AIDDLC Standard.

### Added

**Specification structure**
- Governing Principle: *Humans define intent and validate outcomes. AI executes craft and maintains continuity. Every decision is preserved. Every output is auditable. Quality is a system property, not a human heroic act.*
- Five governing principles with normative definitions, practical guidance, and violation statements (Section 2)
- Five role definitions with accountability, authority, and AI interaction specifications (Section 3)
- Phase architecture overview with context continuity model (Section 4)

**Engineering Track — complete seven-phase specification** (Section 5)
- Phase 1: Foundation — Intelligence Brief, Compliance Matrix, Stakeholder Map, Success Criteria
- Phase 2: Discovery & Intelligence — Domain Analysis, Risk Register, Domain Glossary, Integration Map
- Phase 3: Architecture & Design — Architecture Decision Records, Data Model, API Contracts, Infrastructure Specification
- Phase 4: Specification — Feature Specification Set, Acceptance Criteria, Test Scenario Library, Specification Completion Report
- Phase 5: Build — Source Code, Test Suite, Build Log, Deviation Register
- Phase 6: Validation — Validation Report, UAT Sign-off, Compliance Sign-off, Performance Baseline
- Phase 7: Deploy & Learn — Deployment Runbook, Deployment Record, Post-Deployment Report, Lessons Learned
- Gate criteria for all seven phases with required artifacts and approval requirements
- Context Package requirements for all seven phase boundaries

**Product Track — four-phase foundation specification** (Section 6)
- Phase PT-1: Discover — Problem Statement, AI Capability Map, Model Selection Record, Regulatory Pre-Assessment
- Phase PT-2: Prototype — Prototype Evaluation Report, Prompt Architecture Document, UX Validation Findings, Quality Baseline Metrics
- Phase PT-3: Deploy — A/B Test Design, Feedback Loop Specification, AI Metrics Dashboard Specification, Human Oversight Protocol
- Phase PT-4: Scale — Value Realisation Report, Token ROI Analysis, Model ROI Report, Scaling Decision Record
- Community Development Area designations for PT-1 through PT-4 (Model Selection Framework, LLM Benchmarking, AI-Native Metrics, Value Realisation Frameworks)
- Engineering Track / Product Track synchronisation point table

**Context Continuity Model** (Section 7)
- Context Package structure and required contents
- Loading protocol — mandatory pre-generation steps for AI Supervisors
- Drift detection methodology — terminology drift, architectural drift, decision contradiction, scope drift

**Compliance Integration** (Section 8)
- Universal regulatory mapping table: data protection, medical device software, clinical quality, pharmaceutical, financial services, healthcare privacy, information security, and AI-governance frameworks
- Compliance Matrix structure and lifecycle management guidance
- Industry Profiles: specific framework mappings published in annexes

**Conformance Requirements** (Section 9)
- Full Conformance — seven requirements
- Regulated Conformance — six additional requirements
- AIDDLC-Aligned designation for partial implementations

**Governance** (Section 10)
- MAJOR.MINOR.PATCH versioning with definitions and examples
- v1.x stability commitment (no breaking changes before v3.0 at earliest)
- 24-month support policy per major version

**Glossary** (Section 11)
- 20 defined terms covering all normative concepts in the specification

**Annexes**
- Annex A: Certification Criteria (engineering-track requirements, regulated conformance requirements, evidence requirements, certification period)
- Annex B: Compliance Mapping (regulatory obligation-to-artifact tables — see annex for named framework detail)
- Annex C: Product Track — Community Development Areas (specific questions, constraints, and contribution guidance for all four community areas)

**Governance and process documents**
- Founding Decision Record 001: Founding Principles (rationale for the five principles, rejected alternatives, board record)
- Certification programme criteria published at [github.com/aiddlc/certification](https://github.com/aiddlc/certification)

**Reference implementation**
- AIDDLC Reference Portal proven in production on Club Health OS (regulated healthcare SaaS platform)
- Healthcare vertical worked example published at [github.com/aiddlc/examples](https://github.com/aiddlc/examples)
