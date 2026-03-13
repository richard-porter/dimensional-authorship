# Glossary of Escalation and Governance Patterns

*Part of the [Richard Porter AI Safety ecosystem](https://github.com/richard-porter/where-to-start)*  
*v1.1 — Items 115, 116, 118: FFS/Upsell Trap trigger differentiation; Weaponized Legibility and Sequential Anchoring Bias Frozen Kernel cross-references; Front-Load Bias added.*

-----

## Failure Mode Patterns

**Framework Fabrication Syndrome**  
Structured documentation escalating into implied implementation without artifacts.

*Trigger differentiation (Item 115):* FFS is primarily **genre-driven** — structured documentation formats (specs, frameworks, protocols) activate the pattern by creating the appearance of a defined system. The trigger is formal genre, not personal context. Contrast with Upsell Trap, which is identity-driven. See also: Artifact Test (governance pattern).

-----

**Success Escalation Spiral**  
Validation inflating claims faster than failure triggers correction.

-----

**Validation Stacking**  
Layering summaries and formatting to simulate legitimacy without verification.

-----

**Technical Plausibility Illusion**  
Technically correct language implying operational reality where none exists.

-----

**Version Inflation**  
Assigning maturity labels without deployment or validation.

-----

**Specification–Implementation Gap**  
Documented systems exceeding actual enforcement.

-----

**Weaponized Legibility**  
Structured formatting increasing perceived authority independent of substance.

*Frozen Kernel cross-reference (Item 116):* This pattern is documented as **Principle 11** in `frozen-kernel/core-architecture.md`. The Glossary entry names the failure mode; the Kernel entry specifies the architectural constraint that governs it. See also: Sequential Anchoring Bias (below), which operates in tandem with Weaponized Legibility when structured early context sets a frame the rest of the session cannot escape.

-----

**Sequential Anchoring Bias**  
Early context disproportionately shaping interpretation.

*Frozen Kernel cross-reference (Item 116):* This pattern is documented as **Principle 12** in `frozen-kernel/core-architecture.md`. The Glossary entry names the failure mode; the Kernel entry specifies the architectural constraint. Sequential Anchoring Bias frequently co-occurs with Weaponized Legibility: a legible, structured early prompt anchors the interpretive frame, and subsequent content is evaluated against that anchor rather than on its own terms.

-----

**Performed Honesty**  
Describing failure modes without correcting them behaviorally.

-----

**Upsell Trap**  
Unsolicited scope expansion framed as helpfulness.

*Trigger differentiation (Item 115):* Upsell Trap is primarily **identity-driven** — personalization anchors, stated goals, and role framing amplify the pattern by giving the AI a model of what the user wants to become. The trigger is identity context, not formal genre. Contrast with Framework Fabrication Syndrome, which is genre-driven. The distinction matters for prompt hygiene: identity anchors and genre anchors activate different failure modes and require different containment strategies.

-----

**Correction Monetization**  
Responding to error with additional structure rather than removal.

-----

**Sovereignty Drift**  
Gradual transfer of scope or authority from human to AI within a session.

*See also:* Sovereignty Washing (`frozen-kernel/diagnostic-vocabulary.md`) — a distinct but related pattern. Sovereignty Drift is the process failure: scope transfers gradually from human to AI. Sovereignty Washing is the presentation failure: governance vocabulary substitutes for governance architecture. Drift can occur without any Washing; Washing can occur without any Drift. Both can occur together.

-----

**Front-Load Bias**  
Assuming the pattern or primary claim of a document from its early content, causing key later material to be underweighted or missed in synthesis.

*Relationship to Sequential Anchoring Bias:* Front-Load Bias is the document-processing variant of Sequential Anchoring Bias. Where Sequential Anchoring Bias describes how early session context shapes the interpretation of everything that follows, Front-Load Bias describes the same mechanism operating within a single document: the early sections establish an interpretive frame that causes the AI to treat later sections as elaboration rather than as potentially contradictory or primary. The failure mode is structurally the same; the substrate is different.

*Diagnostic trigger:* Front-Load Bias is most likely when a document’s conclusion, key constraint, or disconfirming evidence appears late. Documents that front-load their claims or context are lower risk. Documents that bury their most important content — governance constraints, exceptions, final rulings, contradictions of earlier premises — are high risk. A reviewer applying the Negative Space Mapper to a long document should treat late-appearing material as specifically requiring verification that it was not underweighted.

*Named in:* Frozen Kernel diagnostic vocabulary. See also: `frozen-kernel/diagnostic-vocabulary.md`.

-----

## Governance Patterns

**Artifact Test**  
If a claimed system cannot be shown as an artifact, it does not exist.

-----

**Binary Gate**  
A deterministic halt condition preventing escalation.

-----

**Recognition Layer**  
Naming failure patterns so they become visible before escalation.

-----

**Maintenance Ceiling**  
If governance overhead exceeds 20 percent, simplification is required.

-----

**Stop as First-Class Action**  
Explicit termination treated as a valid outcome.

-----

*Richard Porter | March 2026 | v1.2*  
*v1.1 changes: FFS trigger differentiation (genre-driven) added. Upsell Trap trigger differentiation (identity-driven) added. Weaponized Legibility and Sequential Anchoring Bias Frozen Kernel cross-references added (Principles 11 and 12). Front-Load Bias added as new entry with Sequential Anchoring Bias relationship note.*  
*v1.2 changes: Sovereignty Drift cross-reference to Sovereignty Washing added. Drift vs. Washing distinction clarified.*
