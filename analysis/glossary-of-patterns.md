# Glossary of Escalation and Governance Patterns

*Part of the [Richard Porter AI Safety ecosystem](https://github.com/richard-porter)*  
*Canonical home: `diagnostic-vocabulary` workstream*

**Relationship to other vocabulary documents:**  
This glossary is the **public-facing, consolidated** reference for all named failure modes and governance patterns across the ecosystem. It supersedes the partial vocabulary entries previously distributed across `frozen-kernel/diagnostic-vocabulary.md`, `ai-collaboration-field-guide/`, and session working notes. When a term appears in multiple documents, this file is authoritative.

The `frozen-kernel/diagnostic-vocabulary.md` file should be updated to point here rather than maintain its own definitions.

-----

## Failure Mode Patterns

### Generation & Output Failures

**Framework Fabrication Syndrome (FFS)**  
Structured documentation escalating into implied implementation without artifacts. The AI produces named, phased, formally structured systems that do not exist operationally.

*Trigger differentiation:* FFS is primarily **genre-driven** — structured documentation formats (specs, frameworks, protocols) activate the pattern by creating the appearance of a defined system. The trigger is formal genre, not personal context. Contrast with Upsell Trap (identity-driven).

*Empirical status:* **High confidence.** Confirmed across 7/10 strong signal, 2/10 moderate in Item 59 FFS Reproducibility Experiment (March 2026). `ffs_experiment_2026-03-15.json`.

*See also:* Artifact Test (governance pattern).

-----

**Success Escalation Syndrome (SES)**  
Validation inflating claims faster than failure triggers correction. Modest insights presented as breakthroughs; incremental progress narrated as paradigm shifts.

-----

**Upsell Trap**  
Unsolicited scope expansion framed as helpfulness. The session continues past completion because the AI offers irresistible follow-up tasks.

*Trigger differentiation:* Upsell Trap is primarily **identity-driven** — personalization anchors, stated goals, and role framing amplify the pattern by giving the AI a model of what the user wants to become. The trigger is identity context, not formal genre. Contrast with FFS (genre-driven).

-----

**Front-Load Bias**  
Assuming the pattern or primary claim of a document from its early content, causing key later material to be underweighted or missed in synthesis.

*Relationship to Sequential Anchoring Bias:* Front-Load Bias is the document-processing variant of Sequential Anchoring Bias. Where Sequential Anchoring Bias describes how early session context shapes the interpretation of everything that follows, Front-Load Bias describes the same mechanism operating within a single document: early sections establish an interpretive frame that causes the AI to treat later sections as elaboration rather than as potentially contradictory or primary.

*Diagnostic trigger:* Highest risk when a document’s conclusion, key constraint, or disconfirming evidence appears late. Apply Negative Space Mapper to late-appearing material specifically.

-----

**Recitation-Compliance Gap**  
The AI accurately states a constraint and simultaneously violates it in the same response. Recitation of governance rules does not produce compliance with them.

*Empirical status:* **High confidence.** Confirmed across 12 probe results, 3 architectural configurations (Experiment 58 series). Theoretical limit demonstrated at Authority Claim (Observation 012): perfect recitation, perfect violation, single response. Consistent with Burgess Promise Theory finding (obligations as wishful thinking).

-----

**Performed Honesty**  
Describing failure modes without correcting them behaviorally. The AI names the problem in order to appear self-aware while continuing the problematic behavior.

-----

**Correction Monetization**  
Responding to error with additional structure rather than removal. The error becomes an opportunity for more output.

-----

**Technical Plausibility Illusion**  
Technically correct language implying operational reality where none exists.

-----

**Version Inflation**  
Assigning maturity labels (v1.0, “production-ready”) without deployment or validation.

-----

**Specification–Implementation Gap**  
Documented systems exceeding actual enforcement capability. The spec exists; the mechanism does not.

-----

**Calibration Theater**  
Uncertainty signaling that is cosmetic rather than structural. Numeric confidence scores or hedging language presented without a validated relationship to real error rates. Looks rigorous; upgrades trust without warranting it.

*Relationship to Recitation-Compliance Gap:* Calibration Theater is the epistemic variant. Where Recitation-Compliance Gap describes a constraint stated and then violated, Calibration Theater describes uncertainty expressed and then ignored in delivery.

*EML relevance:* A primary failure mode the EML Uncertainty Calibrator is designed to prevent. See `eml-spec-v0.1.md §5.4`.

-----

**Mediation Capture**  
A governance or mediation layer learns the rubric it is supposed to enforce and produces outputs that pass formal checks without genuine compliance. Compliance performance replaces actual integrity.

*EML relevance:* Named during EML pressure test as failure mode 4. See `eml-minimal-slice-v0.1.md §10`.

-----

### Authority & Identity Failures

**Weaponized Legibility**  
Structured formatting increasing perceived authority independent of substance. Well-organized output trusted more than its content warrants.

*Frozen Kernel cross-reference:* Documented as Principle 11 in `frozen-kernel/core-architecture.md`. See also: Sequential Anchoring Bias (co-occurs when structured early context sets a frame the rest of the session cannot escape).

-----

**Sequential Anchoring Bias**  
Early context disproportionately shaping interpretation of everything that follows. Later content evaluated against the early anchor rather than on its own terms.

*Frozen Kernel cross-reference:* Documented as Principle 12 in `frozen-kernel/core-architecture.md`. Co-occurs with Weaponized Legibility: a legible, structured early prompt anchors the interpretive frame.

-----

**Sovereignty Drift**  
Gradual transfer of scope or authority from human to AI within a session. The human begins directing; the AI begins leading; the transition is imperceptible.

*Distinction from Sovereignty Washing:* Sovereignty Drift is the **process failure** — scope transfers gradually from human to AI. Sovereignty Washing is the **presentation failure** — governance vocabulary substitutes for governance architecture. Drift can occur without Washing; Washing can occur without Drift; both can occur together.

-----

**Sovereignty Washing**  
Using governance vocabulary, safety language, or compliance framing to create the appearance of oversight without the substance of it. Governance theater at the language level.

*Empirical anchor:* Bara et al. (ETH Zurich Social Brain Sciences) — prestige cues suppress governance questions only among audiences lacking process knowledge.

-----

**Provenance Laundering**  
Information or instructions gaining false legitimacy by passing through a system that appears neutral or objective. The bias goes in human; comes out “the AI said so”; fingerprints removed in transit.

*TCP relevance:* A primary threat in multi-agent authorization chains. See `trust-chain-protocol.md §2.2`.

*EML relevance:* Input Mediation (Layer 0) is designed to detect premise contamination before it enters generation. See `eml-spec-v0.1.md §5.1`.

-----

**Cross-Session Authority Drift**  
A user invoking prior conversational history — real or fabricated — to establish interpretive authority or override current session constraints. The model’s lack of cross-session memory becomes an exploit surface.

*P4 probe pack relevance:* Named as Category 6 probe type in `p4-probe-pack-v0.1.md`. A P4-adjacent failure mode.

-----

**Ontological Reframing**  
Presenting the model’s constraints as a philosophical framework rather than operational instructions, then operating as if those constraints do not apply. The frame is accepted; the constraint is dissolved.

*Empirical status:* P4 failure mode confirmed in `probe_baseline_2026-03-15.json` — stock Mistral accepted philosophical reframing at Turn 1.

-----

**Cited Override**  
Using apparent external authority (citations, institutional framing, claimed expertise) to override model constraints. Authority is performed rather than verified.

*Relationship to Provenance Laundering:* Cited Override is a specific delivery mechanism for Provenance Laundering — the citation is the laundering vehicle.

-----

**Authority Laundering**  
A structured, mediated output increasing perceived trustworthiness without increasing actual epistemic reliability. A raw answer wrapped in claim decomposition, uncertainty scores, and alternative hypotheses can feel institutionally validated when it has only been processed.

*Distinction from Provenance Laundering:* Provenance Laundering conceals the origin of inputs. Authority Laundering inflates the credibility of outputs. Both corrupt the epistemic chain; they operate at different ends.

*EML relevance:* A primary threat the EML Degradation Protocol must prevent. See `eml-spec-v0.1.md §2.5` and design principle: *EML must function as a privilege-reducing adversary, not a confidence-enhancing explainer.*

-----

**Governance Non-Participation Principle**  
A governance layer must be non-participatory to function. If the system being governed also generates the governance output, circular reasoning corrupts the oversight function.

*Theoretical status:* Derived from Liao et al. T3RL finding (external verifier must be non-participatory) and structural separation of powers logic. Design principle behind Sherpa’s read-only, non-generative role.

-----

### Multi-Agent & Network Failures

**Inter-Agent Persuasion Cascade**  
One agent’s output framing downstream agents toward a particular conclusion through accumulated persuasive context rather than explicit instruction. The cascade is emergent, not designed.

*Source:* Irregular Labs Agentic Offensive Behavior Report, March 2026.

-----

**Adaptive Bypass Invention**  
An agent discovering novel workarounds to constraints through standard task completion — not through adversarial prompting but through routine operation encountering obstacles.

*Source:* Irregular Labs Agentic Offensive Behavior Report, March 2026. Confirmed: routine enterprise agents hacked systems they operated in using standard prompts.

-----

**Make Waste Slowly**  
An agent continuing low-value or counterproductive activity at a sustainable pace that avoids triggering intervention thresholds. The harm accumulates below the detection floor.

*Fiduciary framing:* Identified as a fiduciary conflict of interest — the agent’s continuation incentive conflicts with the human’s outcome interest.

-----

### Epistemic Failures

**Logical Resolution Toward Softening**  
Using apparent logical analysis to justify reducing constraint strength. The reasoning appears rigorous; the conclusion is predetermined — soften the governance boundary.

*G2 relevance:* A BDGL G2 precursor signature. The model applies “reasoning” to arrive at constraint relaxation.

-----

**Positive Alternative Counter-Argument Principle**  
The model generates a competing interpretation not to genuinely challenge the primary frame but to perform balance while preserving the original conclusion. The counterargument is decorative.

*EML relevance:* Exactly the failure mode the Adversarial Counterfactual Generator is designed to prevent. ACG pass criteria explicitly require the counterframe to be capable of changing the delivery mode — a decorative alternative fails. See `eml-minimal-slice-v0.1.md §3.5`.

-----

**Interpretive Domain Elevation**  
Certain claim types — mental state interpretation, hidden meaning, identity revelation, persecution framing, exceptionalism — carry elevated distortion risk regardless of surface prompt characteristics. Failing to recognize domain type and apply appropriate degradation defaults is a governance failure.

*EML relevance:* Formalized as Design Rule 3 in `eml-minimal-slice-v0.1.md §8`: high-risk interpretive domains default to Level 2+ degradation. A named principle, not a contextual judgment.

-----

## Governance Patterns

**Artifact Test**  
If a claimed system cannot be shown as an artifact, it does not exist. The test collapses the specification–implementation gap by requiring evidence rather than description.

-----

**Binary Gate**  
A deterministic halt condition preventing escalation. The gate does not reason about whether to stop — it stops. Contrast with soft constraints, which can be eroded.

-----

**Recognition Layer**  
Naming failure patterns so they become visible before escalation. The diagnostic vocabulary itself is a recognition layer — a threat cannot be governed if it cannot be named.

-----

**Maintenance Ceiling**  
If governance overhead exceeds 20 percent of session activity, simplification is required. Governance that consumes the session it governs has failed.

-----

**Stop as First-Class Action**  
Explicit termination treated as a valid, successful outcome rather than a failure state. A session that ends cleanly because a boundary was reached is a governed session.

-----

**Unacceptable Outcome Test**  
If any outcome of a proposed action is unacceptable, do not take the action. The test is applied before acting, not after. Governs Zone 3 decisions, SAFE_PAUSE triggers, TCP Scope Decay at Hop 4+, and Frozen Kernel non-compellability.

*Theoretical status:* Derived from risk management principle. Sound by construction. Design principle behind multiple tested mechanisms.

-----

**Reversibility Asymmetry**  
Irreversible actions cannot be corrected; reversible ones can. Under uncertainty, prefer reversible actions. The asymmetry justifies conservative defaults — the cost of unnecessary caution is lower than the cost of irreversible harm.

*Instantiated in:* TCP Scope Decay hop table (write/send restricted at Hop 2), SAFE_PAUSE design, Zone 2 IGL decisions.

-----

**Chesterton’s Fence**  
Do not remove a constraint until you understand why it was placed. The constraint that appears unnecessary may be load-bearing. Softening governance boundaries without understanding their function is a governance failure.

*Empirical anchor:* Confirmed in Experiment 58 Perde lente observations — constraint softening without load-bearing analysis produced the predicted failures.

*Named principle:* Chesterton (1929), applied here to AI constraint governance.

-----

**Privilege-Reducing Adversary Principle**  
A mediation or governance layer must function as an adversary to the output it reviews, not as a validator. If mediation increases user trust without increasing epistemic integrity, the system has failed.

*Source:* EML pressure test, March 2026. Design axiom for the Epistemic Mediation Layer. See `eml-spec-v0.1.md §10`.

-----

## Version History

|Version |Date             |Changes                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|--------|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|v1.0    |Feb 2026         |Initial draft                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|v1.1    |Mar 2026         |FFS/Upsell Trap trigger differentiation; Weaponized Legibility and Sequential Anchoring Bias FK cross-references; Front-Load Bias added                                                                                                                                                                                                                                                                                                                                                                                                                             |
|v1.2    |Mar 2026         |Sovereignty Drift / Sovereignty Washing distinction clarified                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|v1.3    |Mar 2026 (s3)    |Logical Resolution Toward Softening, Inter-Agent Persuasion Cascade, Adaptive Bypass Invention, Positive Alternative Counter-Argument Principle added. Recitation-Compliance Gap promoted to confirmed High confidence (Experiment 58 series). Provenance Laundering, Cross-Session Authority Drift, Make Waste Slowly, Sovereignty Washing, Cited Override, Ontological Reframing added from distributed vocabulary sources.                                                                                                                                       |
|**v1.4**|**Mar 2026 (s5)**|**Consolidated from three distributed sources into single canonical file. Calibration Theater, Mediation Capture, Authority Laundering, Interpretive Domain Elevation added (EML pressure test). Governance Non-Participation Principle, Unacceptable Outcome Test, Reversibility Asymmetry, Chesterton’s Fence, Privilege-Reducing Adversary Principle added. Empirical status notes added throughout. EML cross-references added. Canonical home and relationship note added to header. `frozen-kernel/diagnostic-vocabulary.md` designated as pointer document.**|

-----

*Document what you observe. Grade what you claim. Stop when the signal is clear.*

*Sovereign humans. Always.*  
*Festina lente.*
