# Dimensional Voice Stamp v0.1

**Status:** Specification draft — not yet implemented  
**Repo:** `dimensional-authorship/experiments/dimensional-voice-stamp-v01.md`  
*Part of the [dimensional-authorship](https://github.com/richard-porter/dimensional-authorship) project.*

-----

## What This Is

A mechanism for making human authorship sovereignty *verifiable by others* without exposing the calibration data that makes the verification meaningful.

The HSCF certifies that a work was produced under human sovereign governance. The Permanent Tells framework identifies what durable authorship signals look like. Both operate as documentation — records that travel with the work and can be examined by a verifier who trusts the author’s account.

The Dimensional Voice Stamp adds a layer the documentation alone cannot provide: **asymmetric verifiability**. A verifier with no prior relationship to the author can check the public layer of the stamp and confirm that the work is consistent with a documented human voice signature. The private layer — the calibration data that could be used to defeat the stamp — remains in the author’s possession and is never published.

The asymmetry is the mechanism. Any verifier can confirm the skeleton. Only the author can confirm the soul.

**The stamp’s claim, stated precisely:** The author has attested this artifact as consistent with their documented voice signature, and this attestation can be publicly verified without exposing the private calibration basis. The stamp does not prove human authorship from text alone. It makes a narrower claim: this version of the work was signed by the claimed author as consistent with their documented voice profile, under the referenced public profile version.

**Architectural note on delegated attestation:** In some contexts — editorial relationships, estates, institutional co-authorship — a trusted reviewer, executor, or co-attester may legitimately hold or co-attest against the private layer. v0.1 does not implement delegated attestation, but the architecture should remain open to it. The private layer is the author’s by default, not by necessity.

-----

## The Public / Private Split

The Voice Stamp has two layers that are never combined in a public-facing document.

### Public Layer — The Skeleton

Released once, versioned, cryptographically signed. Contains:

- The five processor definitions from the Portable Voice Guide (Metaphor Source Domain, Emotional Geography, Phantom Limb Technique, Rhythm Signature, Quiet Action Preference)
- A single public calibration paragraph — one passage that demonstrates all five processors operating together, chosen because it is representative but not exhaustive
- The version hash of the public PVG at time of signing
- The author’s public key or Trust Chain root identifier

**What this enables:** A verifier with no prior relationship to the author can take the following concrete actions:

- Inspect the public processor definitions and confirm the work is being presented under a declared profile version
- Compare the artifact against the public calibration paragraph for register and ecological consistency
- Validate the cryptographic signature / manifest to confirm the stamp was issued by the claimed author
- Confirm the PVG version hash matches the published record

This is a structural compatibility check — does this work operate in the same register, the same metaphor ecology, the same emotional geography as the documented voice? It is not a claim that the work could only have been produced by this author. It is a claim that the author has attested it as consistent with their documented profile.

**What this does not enable:** Passing the soul layer. The public calibration paragraph is illustrative, not generative. A model trained on it can approximate the skeleton. It cannot consistently pass the full private verification without the author’s judgment.

### Private Layer — The Soul

Never published. Stored offline or in the author’s personal vault. Contains:

- The full set of calibration examples — 5–10 source passages from the author’s archive, chosen across projects and years
- Anti-examples — passages that demonstrate what the voice is not, including AI-generated approximations that passed surface inspection but failed private review
- The private PVG version, including constraints and biographical notes that explain why specific choices are characteristic
- The author’s final judgment threshold — the internal standard against which all work is measured before the stamp is applied

**What this prevents:** Adversarial calibration. To defeat the soul layer, an adversary would need the private examples. Without them, even a model specifically optimized to pass the public skeleton cannot reliably satisfy the author’s private judgment — because that judgment is grounded in the full archive, not the single public paragraph.

-----

## The Stamp Architecture

At the completion of any project receiving a Voice Stamp:

**Step 1 — Private verification**  
The author reviews the final work against the private PVG. This is a human judgment call, not an automated score. The question: *does this work bear the marks of my governing mind, operating in my characteristic register, making my characteristic choices?* If yes, proceed. If no, rewrite until it does.

**Step 2 — Fidelity scan (first-pass filter, not certification)**  
Run the dimensional fidelity scorer against the five processors. This is a lightweight consistency check — a tool for catching obvious drift before the author’s final review, not a substitute for it. Threshold: the scorer identifies passages that warrant a second look, not passages that fail. See Appendix A for scorer architecture and explicit limitations.

**Step 3 — Stamp generation**  
Hash the following together:

- Final text
- Public PVG version identifier
- Project-Specific Primer (PSP) version identifier
- Timestamp

Sign the hash with the author’s Trust Chain root. This produces the Voice Stamp token.

**Step 4 — Trust Chain record**  
Append a Trust Chain record documenting the collaboration chain: human → AI sessions → human sign-off. The record does not need to be exhaustive — it needs to be accurate about the governance structure. Who initiated, where AI contributed, what the human transformed, and where final authority resided.

**Step 5 — Stamp embedding**  
Embed the stamp token in the published artifact. Options by format:

- Document metadata block
- JSON sidecar file
- Embedded hash in PDF properties
- QR code linking to public verification record

The stamp travels with the work. It survives downstream editing and republication as a verifiable claim attached to the version it was applied to.

-----

## The Taller Shell Challenge

The public PVG + a set of test prompts released for open adversarial testing.

**The challenge:** Produce a passage of 500–1000 words that passes the dimensional fidelity scorer against the public skeleton.

**What this proves:** The gap between “passes the public skeleton” and “passes the author’s private soul review” is the empirical measure of the stamp’s strength. If every submission that passes the scorer also passes private review, the public layer is doing all the work and the stamp is weak. If submissions routinely pass the scorer and fail private review, the soul layer is doing meaningful work the public layer cannot.

**Why to run this publicly:** The H-GAN attack — a system optimized to generate “human-seeming” features — works against feature detection. It does not work against provenance validation. Running the challenge publicly demonstrates this distinction in practice rather than arguing for it in theory. The models that pass the skeleton and fail the soul are the proof.

**Challenge structure:**

1. Publish public PVG v1.0 + one calibration paragraph + scorer specification
1. Accept submissions from any team or system
1. Score all submissions against the public fidelity scorer — results published
1. Apply private soul review to all submissions that pass the scorer — results published as pass/fail without exposing the private calibration data
1. The gap between scorer pass rate and soul review pass rate is the empirical benchmark

This is not a competition. It is a measurement instrument. The goal is to establish what the public layer can and cannot certify, and to demonstrate that the private layer remains a human-only channel.

-----

## What This Does Not Claim

**It does not claim the scorer is the stamp.** The dimensional fidelity scorer is a first-pass filter. Automated metrics operating on surface features are subject to the same compression as stylometric detection — they become easier to game as models improve. The scorer is a tool for catching obvious drift before human review. It is not the certification mechanism.

**It does not claim the stamp is permanent.** Voice evolves. The author’s characteristic processors in 2026 are not identical to those of 2016 and will not be identical to those of 2036. The stamp is versioned for this reason. A Voice Stamp v1.0 certifies consistency with the documented voice at the time of signing, not with all past or future versions of that voice.

**It does not claim the private layer is undefeatable indefinitely.** A sufficiently motivated adversary with access to enough of the author’s private archive could eventually approximate the soul layer. The claim is that this requires becoming the author — which is the same claim the Permanent Tells framework makes. The stamp is not a lock. It is a provenance record with asymmetric verification properties.

**It does not replace the HSCF.** The Voice Stamp certifies voice consistency. The HSCF certifies governance process. These are different claims. A work can bear the voice stamp and still have been produced under drift if the governance record is absent. Both layers are needed for full attestation.

-----

## Relationship to Existing Ecosystem

|Voice Stamp Component               |Ecosystem connection                                                                        |
|------------------------------------|--------------------------------------------------------------------------------------------|
|Public skeleton / private soul split|ROSETTA voice preservation framework — the baseline voice signature this stamp derives from |
|Fidelity scorer                     |Dimensional authorship analysis — the processor framework the scorer operationalizes        |
|Trust Chain record                  |Trust Chain Protocol — delegation grammar and chain-of-custody logic                        |
|Stamp signing                       |Frozen Kernel — root of trust and tamper-evident sequencing                                 |
|Private soul review                 |HSCF Layer 2 (origin evidence) — the human judgment call that no automated layer replaces   |
|Taller Shell Challenge              |Tell Engine empirical note — the case study that generated the initial processor calibration|

-----

## Open Questions for v0.2

1. **Key infrastructure:** What is the minimum viable signing infrastructure for authors without technical backgrounds? The stamp must be capturable on a phone. A cryptographic signing workflow that requires a developer defeats the accessibility requirement.
   
   **Answered (v0.2 candidate):** C2PA 2.3 (released December 2025) added support for unstructured text documents via Section A.7 (“Embedding Manifests into Unstructured Text”), making it a strong candidate substrate for transport, signing, and verification. The standard supports extensible custom assertions — which is what the public PVG hash, fidelity score, and Trust Chain record constitute. Conforming tools are emerging across mobile and desktop platforms, reducing implementation burden significantly. Implementation usability and institutional acceptance remain open questions that v0.2 should address through direct testing against available tooling. C2PA is the leading candidate, not a solved problem.
2. **Version migration:** When the author’s voice evolves significantly, how does a v1.0 stamp relate to v2.0 certification? Is there a continuity attestation or are they treated as distinct voice signatures?
   
   **Answered (v0.2 candidate):** Treat versions as a lineage problem, not an identity problem. Each new PVG version gets its own public skeleton plus a signed continuity attestation: “v1.0 soul is a proper subset of v2.0 soul.” The stamp token includes the active PVG version and a hash chain back to the Frozen Kernel root. Verifiers see the active version and the lineage simultaneously. No retroactive rewriting of prior stamps — they remain valid against the version they were issued under.
3. **Institutional recognition:** The stamp is currently a personal provenance record. What would make it legible to publishers, courts, or platforms as a meaningful authorship claim? The trust-model-mapping work is the foundation for this question.
   
   **Answered (v0.2 candidate):** C2PA manifests support extensible custom assertions and W3C Verifiable Credentials for authorship, making them a promising target for encoding the public PVG hash, fidelity score, and Trust Chain record as a structured provenance claim. The C2PA Conformance Program (live since mid-2025) maintains a public registry. Publishers and platforms already accepting Content Credentials represent a plausible adoption path without requiring new technical standards — but institutional recognition is still a governance and policy question, not just a technical one. C2PA provides compatible infrastructure; it does not guarantee legal or platform-level acceptance for this specific authorship construct. That gap requires direct engagement with adopting institutions and is a v0.2 priority.
4. **Scorer limitations disclosure:** The public fidelity scorer must ship with explicit documentation of what it cannot detect, to prevent it from being treated as the certification layer by downstream users who don’t read the spec.
5.	**Proxy attestation infrastructure:** The architectural note above flags that delegated attestation — a trusted reviewer, executor, or co-attester holding or co-attesting against the private layer — must remain architecturally possible. v0.1 defers this. The open question for v0.2 is what the minimum viable proxy attestation infrastructure looks like: who is authorized to co-attest, under what conditions, how is the delegation documented in the Trust Chain record, and how does a verifier confirm that a proxy attestation was legitimately delegated rather than improperly substituted? The editorial estate use case (author incapacitated or deceased, executor attesting posthumous works) and the institutional co-authorship use case (employer or publisher with joint governance rights) have different trust requirements and may require different delegation grammar. Both should be specified before v0.2 implements the architecture.

-----

## Version History

|Version|Date      |Notes                                                                                                                                                                                                                                                                                                                                                                                |
|-------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|0.1    |March 2026|Initial specification. Architecture derived from Grok adversarial review + HSCF ecosystem integration. Public/private split and Taller Shell Challenge are the primary new contributions. Scorer relegated to appendix with explicit limitations.                                                                                                                                    |
|0.1.1  |March 2026|Open Questions 1–3 answered via external adversarial review (Grok). C2PA 2.3 identified as the signing infrastructure that closes the phone-capturable and institutional recognition questions simultaneously. Continuity attestation model added for version migration. No structural changes to spec.                                                                              |
|0.1.2  |March 2026|Five edits via ChatGPT + Gemini adversarial review: (1) top-line claim narrowed to voice-consistency attestation; (2) delegated attestation architectural note added; (3) concrete verifier action list replaces vague “broadly consistent” language; (4) C2PA claims softened to candidate infrastructure; (5) Characteristic Anomalies development note added to Appendix A scorer.|

-----

## Appendix A — Dimensional Fidelity Scorer

**Status:** Prototype specification. Not yet implemented. Treat as a sketch for v0.2 development, not a deployable tool.

**Purpose:** First-pass consistency filter. Identifies passages that warrant closer human review. Not a certification mechanism.

**Five processor metrics:**

*Metaphor Source Domain* — Embedding cosine similarity between candidate text and a reference corpus drawn from the author’s documented source domains (marine biology, process engineering, domestic precision objects, family heritage). Flags text whose metaphor ecology is inconsistent with the documented domain profile.

*Rhythm Signature* — Sentence-length entropy, punctuation cadence, and paragraph rhythm vectors compared against the public calibration paragraph. Flags text with statistically anomalous rhythm relative to the documented signature.

*Phantom Limb Technique* — Ratio of implied-but-unstated elements, measured via negation detection and coreference gap analysis. Flags text that over-explains or under-implies relative to the documented ratio.

*Emotional Geography* — Distance-from-emotional-center measure: how often does the text approach its most charged material obliquely versus directly? Calibrated against the public calibration paragraph. Flags text with direct emotional statement patterns inconsistent with the documented geography.

*Quiet Action Preference* — Ratio of action rendered through consequence and environment versus explicit statement. Flags text with explicit action rendering patterns inconsistent with the documented preference.

**Critical limitation:** All five metrics operate on surface features that are subject to adversarial optimization. A model specifically trained to pass this scorer will eventually succeed. The scorer’s value is in catching unintentional drift — AI default tendencies bleeding into voice — not in providing adversarial-robust certification. The soul layer is the human judgment call that follows.

**v0.2 development note — Characteristic Anomalies:** The five metrics above measure consistency against a mean. AI is effective at matching means. A more adversarially robust scorer would measure *outliers* — the characteristic anomalies that define a voice rather than its average. Human voice is defined by its productive errors: the sentence that runs too long, the metaphor that is slightly broken but emotionally precise, the structural choice that violates craft convention for reasons only the author could explain. AI smooths these out. The Rhythm Signature metric in particular should be extended in v0.2 to detect anomaly distribution, not just average cadence. This maps directly onto Tell 4 (productive incoherence) at the metric level — the scorer should look for preserved contradiction, not resolved consistency. See experiments/rhythm-signature-rebuild-v02.md for full specification.

-----

*Released for public benefit. Attribution appreciated but not required.*
