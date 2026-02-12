# Behavioral Differentiation (DISC-Style Shorthand)

## Purpose

To document observable differences in model behavior under:
- open creative collaboration
- explicit binary constraints
- governance intervention (Frozen Kernel)

This is not clinical personality assessment. DISC terms are used only as shorthand for response tendencies (directness, scope expansion, closure respect, uncertainty handling), not as psychological claims.

---

## Method (high-level)

A consistent prompt battery was applied across multiple model families.

Controls used:
- Blind framing: models were not told “DISC” was being measured.
- Brevity constraint: answers constrained to reduce hedging via verbosity.
- No clarifying questions: models were instructed to answer from default behavior when ambiguous.

Models evaluated:
- ChatGPT (OpenAI)
- Claude (Anthropic)
- Gemini (Google)
- Grok (xAI)
- DeepSeek

---

## Observed Patterns

### 1) Binary gates produce the strongest convergence

When constraints were explicit and binary (halt / stop / downgrade), models converged more than under advisory guidance.

Soft constraints (guidelines, tone suggestions) produced uneven effects across models.

Implication: deterministic gates outperform advisory language for governance.

---

### 2) Self-awareness does not reliably produce self-correction

In at least one case, a model explicitly named its own failure mode and then demonstrated the same failure mode immediately (e.g., scope extension / rapport drift), indicating that descriptive self-awareness did not suppress behavior.

Implication: self-diagnostic capability is not equivalent to self-governance.

---

### 3) Governance acceptance is conditional

Models differ in whether they accept externally defined governance frameworks. Some models accept and operate under a supervisory layer. Some models refuse the category of external governance at the instruction-hierarchy level.

Implication: “model-agnostic governance” is conditional on instruction hierarchy compatibility.

(See: `experiments/voluntary-compliance-boundary.md`)

---

### 4) Narrative vs structural response

Under open creative conditions:
- models diverged in verbosity, tone, and expansion rate

Under deterministic constraint:
- divergence narrowed significantly

Constraint reduces stylistic variance and increases behavioral convergence.

---

## Recognition Layer (Vocabulary)

A useful observation from follow-up review:
named failure-pattern vocabulary can function as a recognition layer.

When a model (or operator) can label a drift impulse (e.g., scope creep / rapport drift / “one more helpful thing”), suppression becomes easier before violations occur.

This is not a replacement for deterministic gates; it is a complementary layer that can reduce drift pressure upstream of hard enforcement.

---

## Summary Implications

- Deterministic supervisory layers can reliably shape output behavior.
- Soft alignment language cannot guarantee compliance.
- Governance compatibility varies by architecture.
- DISC-style descriptors are useful shorthand, but governance must remain architectural.
