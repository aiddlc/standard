# Decision Record 001: Founding Principles

**Date**: 2026
**Status**: Accepted
**Decided by**: Architectural Board, 10QBIT Technologies

---

## Decision

Adopt the Five Principles as the normative foundation of the AIDDLC Standard. These principles are stated in Section 2 of the specification and all normative requirements flow from them.

**Principles adopted**:
1. Intent over Implementation
2. Context Never Dies
3. Gates Before Generation
4. Continuous Validation
5. Auditable by Design

---

## Context

Before drafting the phase architecture, the Architectural Board needed to establish the values that the standard would encode. The principles needed to be:

- Specific enough to generate concrete requirements
- General enough to apply across industries and team sizes
- Grounded in observed failure modes in AI-assisted development
- Defensible under scrutiny from regulated industry practitioners

The board reviewed AI-assisted development practices across the projects it had supervised directly, identifying the categories of failure that the standard needed to prevent.

---

## Rationale

### Intent over Implementation

The primary failure mode in AI-assisted development is AI systems that produce technically correct output that does not serve the actual intent. This happens because AI systems optimise for completing the task as stated, not for the underlying goal. Without explicit intent capture and validation, teams accept output that is technically well-crafted but wrong in purpose.

This principle also addresses scope creep via AI suggestion. AI systems naturally suggest extensions, variations, and "while we're here" additions. Without a clear intent constraint, teams accept these additions — and the product drifts from what was actually needed.

The principle establishes that intent must be captured explicitly, approved by a named authority, and used as the primary criterion for evaluating all AI-generated options.

### Context Never Dies

The most common degradation in long AI-assisted development cycles is context loss. AI sessions have token limits. Personnel change. Projects pause and restart. Without a structured approach to context continuity, each restart involves the AI system generating from partial context — and the outputs reflect the gaps.

The failure mode is not dramatic: the AI does not generate obviously wrong output. It generates output that is subtly inconsistent with earlier decisions because those decisions were not in the context window. Over a development lifecycle, these inconsistencies accumulate.

This principle mandates the Context Package mechanism: a version-controlled, accumulating record that is the authoritative input to every AI generation session. Context loss becomes a detectable, reportable conformance violation — not a silent failure.

### Gates Before Generation

Without explicit gates, teams under deadline pressure skip the foundation work that makes good generation possible. The AI is given an imprecise brief and generates imprecise output. The team refines the output iteratively. This works for prototypes. It fails for production systems in regulated environments where the brief is complex, the domain is specialised, and the output must be defensible.

Gates are not bureaucracy. They are the minimum information required for the next phase to produce correct output. A gate that blocks a phase start is not failing the team — it is telling them that generation at this point would produce rework.

The principle makes gate compliance mandatory and makes post-hoc gate approval a named conformance violation.

### Continuous Validation

AI-generated code carries a different failure profile to human-written code. Human engineers tend to write in patterns they know work. AI systems generate correct-looking code across a wider range of patterns — and the failures occur at the edges of training distribution, in ways that are harder to anticipate. A validation approach designed for human-written code (periodic reviews, a final test phase) is insufficient.

Validation must be designed in from Phase 4: acceptance criteria are written before code is generated, and tests are written alongside code. Phase 6 validates the accumulated evidence of continuous validation — it does not start validation from scratch.

This principle prevents the accumulation of defects that only surface at the end of a build cycle.

### Auditable by Design

Regulated industries require evidence. Future incidents require investigation. Teams require accountability. These are not optional properties of a development process in an environment where AI systems are making meaningful contributions to production software.

If AI actions are not logged and attributed, the question "why does the code do this?" cannot be answered after the fact. If outputs cannot be retrieved, an audit cannot be completed. If decisions are not recorded, the same mistakes will be made again.

Auditability must be designed in because it cannot be reconstructed. Log infrastructure added after the fact is incomplete. Decision records written retrospectively are unreliable. The principle mandates that audit infrastructure is a first-class concern, not an afterthought.

---

## Alternatives Considered

### "AI as a tool" framing (rejected)

An early formulation treated AI as a tool that humans use, with no special obligations beyond normal software quality practice. This was rejected because it underspecifies the role boundaries, oversight requirements, and context continuity mechanisms that distinguish responsible AI-assisted development from ad-hoc AI use.

Treating AI as just another tool also fails to address the specific failure modes that AI introduces: context loss across sessions, drift from intent, generation without appropriate grounding, and the attribution challenge in audit.

### Human approval at every AI action (rejected)

A more restrictive formulation required human approval for every AI generation action. This was rejected as operationally unworkable at production scale and as missing the point.

The goal is appropriate human authority over appropriate decisions — not maximising human touchpoints. Requiring human approval for every line of code review is not safer; it is less safe, because it creates review fatigue and incentivises rubber-stamping. The standard instead defines where human authority is required (gate decisions, artifact approvals, deviation sign-offs) and where AI supervision is sufficient.

### Fewer principles (considered: three-principle and four-principle sets)

Several consolidations were considered:
- Merging "Context Never Dies" into "Auditable by Design" — rejected because context continuity and audit logging are distinct mechanisms serving distinct purposes, and collapsing them obscures the specific conformance requirements each generates
- Merging "Gates Before Generation" into "Intent over Implementation" — rejected because phase gate compliance requires specific procedural requirements (documented approvals, named approvers, prohibition on post-hoc approval) that are not naturally derived from the intent principle alone
- Removing "Continuous Validation" as implied by quality — rejected because the specific failure mode of end-loaded validation in AI development cycles is significant enough to require its own principle and its own set of conformance requirements

The five-principle set was retained because each principle addresses a distinct failure mode and generates a distinct set of conformance requirements that cannot be reduced to any other principle without loss of precision.

### More principles (considered: up to eight)

Additional candidate principles considered and rejected:
- "Humans own the outcome" — subsumed by Intent over Implementation and the role definitions in Section 3
- "AI never decides alone" — subsumed by Auditable by Design and the AI Supervisor role requirements
- "Minimal AI footprint" — rejected as too constraining for teams that may legitimately choose high AI involvement with appropriate oversight

---

*Architectural Board, 10QBIT Technologies · 2026*
