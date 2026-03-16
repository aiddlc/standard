# Annex C: Product Track — Community Development Areas

*Informative. This annex describes the open contribution areas within the Product Track and provides context for community contributors.*

---

## C.1 Purpose

The Product Track (Section 6) contains four phases, each with one or more `[COMMUNITY DEVELOPMENT AREA]` sections. These sections are explicitly open for community contribution under the Minor change process defined in CONTRIBUTING.md.

This annex provides context for each community development area, identifies specific questions the Architectural Board wants the community to address, and describes the constraints and format expectations for contributions.

The Engineering Track phases are normatively complete. The Product Track foundation is normatively complete. The community development areas represent gaps in the Product Track where the Architectural Board has chosen not to specify prematurely — the field is moving too quickly for the board to prescribe approaches with appropriate confidence.

---

## C.2 Contribution Process for Community Development Areas

Contributions to community development areas follow the standard Minor change process, with one difference: community development area contributions do not require a competing interpretation to be addressed. The board is actively seeking first-pass content, not refinements to existing content.

Steps:
1. Review the relevant area in Section 6 of the specification
2. Review the questions and constraints in this annex
3. Open a proposal issue using the Proposal template with change type: **Minor**
4. Reference the specific community development area (e.g., "PT-1: Model Selection Framework")
5. Provide proposed specification text, not just principles or intentions
6. Allow the 21-day review period

Accepted contributions will be incorporated into the specification as Minor updates, with credit in the CHANGELOG.md.

---

## C.3 PT-1: Model Selection Framework

**Specification section**: Phase PT-1: Discover

**What the community development area needs to specify**:

The Model Selection Record is a required artifact in Phase PT-1. The community needs to define what a Model Selection Record must contain and what process must be followed to produce it.

### C.3.1 Specific questions to address

**Q1: Benchmarking methodology**
General benchmarks (MMLU, HumanEval, etc.) do not reliably predict domain-specific performance. How should teams benchmark candidate models for specific product applications? What is a minimum credible benchmarking methodology?

**Q2: Total cost of ownership**
API pricing is the visible cost; it is not the total cost. Infrastructure, fine-tuning, prompt engineering, monitoring, and switching costs must also be considered. What cost-modelling template would produce a useful TCO estimate for model selection?

**Q3: Compliance screening**
Different models have different compliance properties: data residency, training data documentation, model transparency, audit capabilities. What questions must be asked and answered for a model to pass compliance screening? Consider: EU AI Act obligations, GDPR data processing restrictions, MHRA/FCA audit requirements.

**Q4: Model Selection Record format**
A Model Selection Record must be useful to future teams who need to understand and potentially revisit the decision. What format maximises usefulness? What must it contain at minimum?

### C.3.2 Constraints

- The framework must be model-agnostic: applicable to OpenAI, Anthropic, Google, open-source, and self-hosted models
- The framework must be applicable to teams without dedicated ML engineers
- Recommendations should differentiate by use case category (RAG, generation, classification, reasoning)
- Do not specify particular models or providers as defaults — these change too quickly

---

## C.4 PT-2: LLM Benchmarking for Product Validation

**Specification section**: Phase PT-2: Prototype

**What the community development area needs to specify**:

The gate criteria for Phase PT-2 require that a prototype "meets minimum quality threshold." The community needs to define how minimum quality threshold is determined and evidenced for different product types.

### C.4.1 Specific questions to address

**Q1: Domain-specific quality rubrics**
For a clinician reviewing an AI-generated clinical note, quality is different from an engineer reviewing AI-generated code. How should domain-specific quality rubrics be constructed for non-technical reviewers? What structure makes a rubric actionable?

**Q2: Human evaluation protocol**
What is a minimum credible human evaluation protocol for prototype assessment? How many evaluators? What qualifications? What rating methodology? How is inter-rater reliability established?

**Q3: Minimum quality threshold definition**
"Minimum quality threshold" must be defined before Phase PT-2 begins (it is a gate criterion from PT-1 that is not yet specified in the standard). How should this threshold be set? What makes a threshold credible and not arbitrary?

**Q4: Automated evaluation frameworks**
Where automated evaluation is possible (code quality, factual accuracy against a ground truth, format compliance), what frameworks are appropriate? How should automated and human evaluation be combined?

### C.4.2 Constraints

- Methodologies must be applicable to teams without academic ML research backgrounds
- Must be scalable: applicable both to a small team with a single evaluator and to a larger team with a structured evaluation panel
- Must produce a record that satisfies the Prototype Evaluation Report artifact requirement

---

## C.5 PT-3: AI-Native Metrics

**Specification section**: Phase PT-3: Deploy

**What the community development area needs to specify**:

Standard SaaS metrics (DAU, MAU, conversion rate, NPS) do not capture whether an AI product feature is performing well in the ways that matter. The community needs to define an AI-native metrics framework for the AI Metrics Dashboard Specification artifact.

### C.5.1 Specific questions to address

**Q1: Quality drift detection**
AI model outputs change over time: models are updated, fine-tuned, or replaced; input distributions shift; edge cases accumulate. How should quality drift be detected and measured? What monitoring approach catches drift before users notice it?

**Q2: User trust metrics**
Users can lose trust in an AI system in ways that do not show up in engagement metrics until it is too late. What metrics capture user trust in AI outputs? What constitutes a trust failure that should trigger review?

**Q3: AI-specific error taxonomy**
AI errors are different from software bugs: hallucination, refusal, degradation, over-confidence, under-confidence, format failure, context loss. What is a complete and useful taxonomy of AI-specific errors for product teams? How should each error type be detected and counted?

**Q4: Feedback loop effectiveness**
Feedback loops are a required feature of Phase PT-3 deployment. How should the effectiveness of feedback loops be measured? What indicates a feedback loop that is generating useful signal vs. noise?

### C.5.2 Constraints

- Must be measurable with standard application monitoring infrastructure (not requiring specialised ML monitoring platforms)
- Should include leading indicators (metrics that predict problems before they are visible to users) not only lagging indicators
- Must be appropriate for regulated environments where metric definitions must be stable for audit purposes

---

## C.6 PT-4: Value Realisation Frameworks

**Specification section**: Phase PT-4: Scale

**What the community development area needs to specify**:

The Scaling Decision Record and Value Realisation Report require evidence of value. The community needs to define how value is measured, attributed, and reported for AI product features.

### C.6.1 Specific questions to address

**Q1: Token ROI calculation**
Token ROI (value delivered per token consumed) is a defined term in the standard. The community needs to specify: how "value delivered" is measured for different value types (time saved, error rate reduced, conversion rate increased, revenue generated); how to handle AI features where value accrues to multiple parties (user, organisation, third party); how to calculate ROI when the AI feature is one component of a larger system.

**Q2: Sector-specific value metrics**
Value metrics that are meaningful in healthcare (patient outcomes, clinical time saved, error rates) are different from fintech (risk reduction, compliance cost, fraud prevented) or professional services (hours saved, throughput, quality score). What sector-specific metric templates would be most useful to include in the standard?

**Q3: Model upgrade decision criteria**
When should a deployed AI feature's model be upgraded? What criteria justify the cost, regression risk, and re-validation effort of a model upgrade? The community needs to specify: a minimum evaluation process before upgrade, the re-validation requirements after upgrade, and the decision record format.

**Q4: AI value attribution methodology**
Attribution is difficult when AI is one component of a system. If a customer service system achieves a better NPS score after an AI feature is added, how much of that improvement is attributable to AI vs. other changes? The community needs to propose a practical attribution methodology.

### C.6.2 Constraints

- Must be applicable to organisations without dedicated data science teams
- Token ROI must be calculable from standard API billing data without custom instrumentation
- Attribution methodology must be defensible to finance teams, not just product teams
- Must work for features where value is qualitative (experience quality) as well as quantitative (cost saved)

---

## C.7 Getting Started as a Community Contributor

If you have practical experience implementing AI product features, particularly in regulated industries, the Architectural Board is keen to hear from you. The community development areas are not academic exercises — they will become normative requirements that teams must follow to achieve certification.

The most valuable contributions will be:
- Based on direct experience deploying AI features in production
- Specific enough to be implemented by a team without further interpretation
- Appropriate for regulated-industry contexts (conservative, auditable, defensible)

Start by opening a discussion issue before a proposal issue if you are uncertain whether your approach is in scope. The board is responsive and will engage with serious contributors.

---

*Annex C is informative. Community development area contributions are incorporated as Minor updates to the specification. This annex will be updated as areas are filled.*

*10QBIT Technologies · 2026*
