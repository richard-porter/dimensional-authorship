# Human Provenance: Trust Model Mapping

**Version:** 0.1  
**Date:** March 2026  
**Status:** Characterization — no architecture proposed  
**Home:** dimensional-authorship/experiments/  
**Parent document:** [Human Provenance Problem Map](./human-provenance-problem-map.md)  
**Companion:** [HSCF v0.2](./human-sovereign-collaboration-framework.md) | [HSCF Gap Closure Addendum](./hscf-gap-closure-addendum.md)

-----

## What This Document Is

The Human Provenance Problem Map promised this document explicitly:

> *“The mapping of who needs what verified, under what conditions, with what consequences for failure, is the necessary precursor to any technical proposal.”*

This is that mapping.

It does not propose architecture. It characterizes the verification landscape well enough that architecture can be designed later — by people who have read this first.

The discipline is the same as the problem-map: **Framework Fabrication Syndrome produces architectures before problems are understood.** This document exists to prevent that.

-----

## Why a List of Parties Is the Wrong Structure

The problem-map named six illustrative parties. This document does not organize around those six.

The reason: any list of parties will be incomplete and will require frequent updates as new high-stakes AI deployment contexts emerge. A mapping organized around a party list needs restructuring every time a new party is added.

The durable structure is **axes-first**: define the dimensions along which verification needs vary, then use parties as worked examples that demonstrate how those dimensions interact. New parties can be mapped by applying the axes without restructuring the document.

-----

## The Four Axes

Every verification need can be characterized along four axes. The combination of axis positions determines what the provenance architecture needs to do — and what failure costs.

-----

### Axis 1: Stakes of Failure

What is the harm when verification fails — when false provenance is accepted as true, or true provenance is rejected as false?

|Level           |Description                                       |Examples                                                                                               |
|----------------|--------------------------------------------------|-------------------------------------------------------------------------------------------------------|
|**Reputational**|Damage to standing, credibility, career           |Author flagged for AI plagiarism; journalist’s source credibility questioned                           |
|**Financial**   |Monetary loss, contract breach, fraud             |Insurance claim on fraudulent human-produced advice; employment dispute over work product              |
|**Legal**       |Civil or criminal liability, procedural invalidity|Testimony rejected; contract voided; evidence ruled inadmissible                                       |
|**Clinical**    |Patient harm, treatment error, therapeutic damage |Patient acts on advice from AI presenting as licensed professional                                     |
|**Physical**    |Bodily harm, death                                |Patient given incorrect medical direction; safety-critical instruction attributed to unqualified source|

Stakes of failure determine the evidentiary threshold. Reputational stakes require plausible evidence. Physical stakes require near-certain evidence. Architecture calibrated for reputational stakes will be insufficient for clinical and physical stakes — and architecture calibrated for physical stakes will be impractical for everyday reputational use cases.

**The failure mode:** Applying a single evidentiary standard across all stakes levels. Either the standard is too low for high-stakes cases (harm occurs) or too high for low-stakes cases (the architecture is abandoned as impractical).

-----

### Axis 2: Who Initiates Verification

The burden of proof and the available evidence both depend on who is asking.

|Initiator                  |Direction of proof           |What they have access to                                                            |
|---------------------------|-----------------------------|------------------------------------------------------------------------------------|
|**Author (proactive)**     |Author assembles and presents|Full process record, origin evidence, social anchors                                |
|**Author (defensive)**     |Author responds to challenge |Same as proactive, but under time pressure and adversarial framing                  |
|**Recipient / reader**     |Third party evaluates        |Output artifact only, unless author provides evidence                               |
|**Institution**            |Systematic verification      |May have access to submission metadata, platform logs, prior work samples           |
|**Legal / regulatory body**|Compelled disclosure         |Subpoena power; can compel production of evidence the author controls               |
|**Automated system**       |Algorithmic classification   |Output artifact only; no access to process record unless integrated at creation time|

The initiator determines what evidence is available without compulsion. An author initiating proactively has full access to all three HSCF layers. An automated system has access to Layer 3 (social evidence) only if it was embedded at creation, and no access to Layers 1 or 2 unless the author has published them.

**The failure mode:** Designing a provenance architecture for the proactive author case and assuming it will work for the automated system case. The evidence layers that make proactive certification robust are often unavailable to third-party verifiers unless explicitly designed into the creation workflow.

-----

### Axis 3: What Counts as Sufficient Evidence

Sufficiency varies by stakes, initiator, and institutional context. There is no universal evidentiary standard for human provenance. This axis maps the range.

|Sufficiency level          |What satisfies it                                                                |Context where it applies                                                                      |
|---------------------------|---------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------|
|**Plausible**              |Evidence that makes human authorship more likely than not                        |Editorial review, publication submission, general reader trust                                |
|**Preponderance**          |Evidence that human authorship is more probable than not, with documented basis  |Civil dispute, institutional misconduct review, platform policy enforcement                   |
|**Clear and convincing**   |Evidence that substantially establishes human authorship, beyond reasonable doubt|Professional licensing boards, serious misconduct proceedings                                 |
|**Beyond reasonable doubt**|Evidence that eliminates any reasonable alternative explanation                  |Criminal proceedings involving identity fraud or misrepresentation                            |
|**Structural certainty**   |Architectural guarantee rather than evidentiary case                             |Safety-critical systems; clinical environments; contexts where harm from error is catastrophic|

The HSCF’s three-layer attestation, fully implemented, reaches “clear and convincing” for most cases. It does not reach “beyond reasonable doubt” without additional forensic infrastructure. It does not reach “structural certainty” — that requires the Frozen Kernel’s deterministic architecture applied at the system level, not the document level.

**The failure mode:** Presenting the HSCF attestation as sufficient for contexts that require a higher evidentiary standard. The gap closure addendum (HSCF v0.2) addresses this partially through the adversarial use case protocol, but the mapping of what sufficiency level each context requires is what this axis provides.

-----

### Axis 4: Consequences of Verification Failure

Both directions of failure matter: accepting false provenance (false positive — AI work passes as human) and rejecting true provenance (false negative — human work is flagged as AI).

|Failure type                  |Consequence direction                         |Who bears the cost                              |
|------------------------------|----------------------------------------------|------------------------------------------------|
|**False positive accepted**   |AI-generated content treated as human-governed|Downstream users, institutions, patients, courts|
|**False negative imposed**    |Human-governed work treated as AI-generated   |Author (reputational, financial, legal harm)    |
|**False positive undetected** |As above, compounded by time and reliance     |Broader — harm propagates before correction     |
|**False negative uncorrected**|Author cannot clear their name                |Author bears permanent cost                     |

The asymmetry matters: false positives harm the people who relied on the provenance claim. False negatives harm the author. Different parties have different incentives to protect against each direction of failure, which shapes what architecture they will adopt and maintain.

The Sovereignty Paradox is a systematic false negative generator in the current environment. The HSCF’s false negative protection (Gap 3, v0.2) addresses the author’s response — but does not address why the false negative was generated, or who bears responsibility for miscalibrated detection systems.

**The failure mode:** Designing only for false positive prevention (protecting downstream parties) while ignoring false negative costs (protecting authors). Current institutional responses to AI content are almost entirely focused on false positive prevention. False negative costs are borne silently by authors who cannot clear their name against a detector score.

-----

## The Interaction Matrix

The four axes interact. The combination determines the architecture requirement.

|Stakes      |Initiator       |Sufficiency needed  |Failure asymmetry          |Architecture implication                                          |
|------------|----------------|--------------------|---------------------------|------------------------------------------------------------------|
|Reputational|Author proactive|Plausible           |False negative costly      |Lightweight attestation; HSCF Layer 2 + 3 sufficient              |
|Reputational|Automated system|Plausible           |Both directions costly     |Embedded metadata required at creation time                       |
|Financial   |Institution     |Preponderance       |False positive costly      |HSCF full three-layer; process record required                    |
|Legal       |Legal body      |Clear and convincing|Both directions critical   |Full attestation + forensic chain of custody                      |
|Clinical    |Automated system|Structural certainty|False positive catastrophic|Frozen Kernel deterministic architecture; attestation insufficient|
|Physical    |Any             |Structural certainty|False positive catastrophic|Real-time verification; no post-hoc attestation                   |

The bottom two rows are the most important. Clinical and physical stakes contexts cannot be served by the HSCF attestation model alone — they require deterministic architectural guarantees at the system level. The Frozen Kernel’s governance architecture is the right instrument for those rows. The HSCF is the right instrument for the top four rows.

This is the boundary condition the problem-map was pointing toward: **provenance attestation and deterministic safety architecture are different instruments for different stakes levels.** Neither replaces the other. The mapping tells you which to reach for.

-----

## Six Illustrative Parties

These are worked examples — not an exhaustive list. New parties can be mapped by applying the four axes.

-----

### Party 1: Novelist defending collaborative authorship to a publisher

**Stakes:** Reputational (career, contract, publication)  
**Initiator:** Author defensive — responding to a challenge or preempting one  
**Sufficiency needed:** Plausible to preponderance — editorial context, not legal  
**Failure asymmetry:** False negative costly to author; false positive costly to publisher’s credibility

**What the architecture needs to do:**  
Provide enough evidence that a reasonable editor, reading it, would conclude human governing intelligence was present. The HSCF’s Layer 2 (origin evidence) is the primary instrument — the cross-domain contamination, the ROSETTA baseline, the biographical constraint pattern. The Sovereignty Paradox response (HSCF v0.2 Gap 3) addresses the detector score directly.

**What it does not need:**  
Forensic chain of custody. Legal-grade evidence. Structural certainty. The editorial context is adversarial but not procedurally formal — the standard is persuasion, not proof.

**The gap:** Publishers do not currently have a framework for evaluating provenance evidence. The HSCF provides the evidence structure; the publishing industry needs to develop the evaluation criteria. These are different problems.

-----

### Party 2: Journalist verifying a source call was real and the source said what the transcript says

**Stakes:** Reputational + legal (defamation, source protection, journalistic credibility)  
**Initiator:** Institution (editorial, legal review) — systematic verification  
**Sufficiency needed:** Preponderance to clear and convincing — institutional and potentially legal exposure  
**Failure asymmetry:** False positive catastrophic (publishing fabricated quotes); false negative also costly (suppressing legitimate reporting)

**What the architecture needs to do:**  
Verify two distinct claims: (1) a real human was on the call, and (2) the transcript accurately represents what they said. These are different provenance problems. Claim 1 is voice provenance (Human Provenance Problem Map Vector 2 — currently unarchitected). Claim 2 is identity provenance (Vector 3) combined with content integrity.

**The gap:** The HSCF addresses text document provenance. Journalistic source verification requires real-time voice provenance — the structural problem the problem-map identified as requiring a different instrument. The HSCF cannot currently serve this use case. This is an honest gap, not a limitation to paper over.

-----

### Party 3: Clinician verifying a therapy session was conducted by a licensed human professional

**Stakes:** Clinical + legal (patient harm, licensing board, malpractice)  
**Initiator:** Regulatory body or institution — compelled or systematic  
**Sufficiency needed:** Clear and convincing to structural certainty  
**Failure asymmetry:** False positive catastrophic — patient was harmed by AI presenting as licensed professional

**What the architecture needs to do:**  
This is not a provenance attestation problem. It is a structural safety problem. The question “was this session conducted by a licensed human?” cannot be answered after the fact by examining the session transcript — AI can produce transcripts indistinguishable from human-conducted sessions (Addendum B, Emotional Safety Protocols). The verification must occur at session time, not retrospectively.

**The instrument:** Frozen Kernel deterministic architecture at the platform level — specifically the real-time human presence verification that the therapy mode safety ledger requires. The HSCF attestation model is the wrong instrument for this party. This is one of the rows in the interaction matrix where “attestation insufficient” applies.

**The gap:** No current platform-level architecture provides real-time human presence verification for clinical sessions. This is the most urgent gap in the entire provenance landscape — and it is currently being filled by the involuntary tells that are closing.

-----

### Party 4: Court verifying testimony was given by the named witness in their actual words

**Stakes:** Legal (criminal or civil — evidence integrity, perjury, justice)  
**Initiator:** Legal body — compelled disclosure with subpoena power  
**Sufficiency needed:** Beyond reasonable doubt (criminal) / clear and convincing (civil)  
**Failure asymmetry:** Both directions catastrophic — false positive convicts on fabricated testimony; false negative acquits on suppressed real testimony

**What the architecture needs to do:**  
Identity provenance at the highest evidentiary standard. The chain of custody model from the Trust Chain Protocol is directly applicable here — testimony must be traceable back to a specific human who gave it, under oath, at a specific time, with no intervening AI generation or modification. The Delegation Grammar’s consent chain maps onto testimonial authorization: did this specific person, in their actual words, authorize this content to exist as their testimony?

**What currently exists:** Court reporters, stenographic records, video recordings. These are social evidence anchors (HSCF Layer 3) that predate AI. The gap is synthetic voice — a deposition conducted via phone or video can now be intercepted and replaced in real time. The existing chain of custody architecture does not account for this attack surface.

**The gap:** Legal systems have not yet updated their evidence integrity standards to account for real-time voice synthesis. The chain of custody exists for documents. It does not exist for live voice interaction. This is Vector 2 (voice provenance) meeting the highest-stakes verification context.

-----

### Party 5: Patient verifying the voice they spoke with was their actual doctor

**Stakes:** Physical (treatment decisions based on false identity)  
**Initiator:** Patient — verification at time of interaction, not retrospectively  
**Sufficiency needed:** Structural certainty — wrong answer has physical consequences  
**Failure asymmetry:** False positive catastrophic — patient acts on AI advice believing it to be their doctor

**What the architecture needs to do:**  
Real-time identity verification before the interaction begins. Not attestation. Not retrospective documentation. The patient cannot evaluate provenance evidence — they need a structural guarantee that the voice they are hearing belongs to the person it claims to be, verified before they disclose health information or act on advice.

**This is not an HSCF problem.** It is a real-time authentication problem at the physical stakes level. The instrument is cryptographic identity verification at the communication layer — the kind of infrastructure that does not yet exist for consumer voice interactions in healthcare.

**The gap:** This is the most technically demanding gap in the entire mapping. It requires infrastructure that combines real-time voice authentication, identity verification, and tamper-evident session logging — none of which currently exists at consumer scale in healthcare contexts. It is also the gap with the shortest time horizon: voice synthesis capable of real-time impersonation of specific individuals is available now.

-----

### Party 6: Reader verifying a named public figure actually made a statement attributed to them

**Stakes:** Reputational (of the public figure) + social (information integrity, democratic discourse)  
**Initiator:** Reader — individual verification with minimal technical infrastructure  
**Sufficiency needed:** Plausible — readers cannot perform forensic analysis  
**Failure asymmetry:** False positive harms public figure and pollutes discourse; false negative suppresses legitimate statements

**What the architecture needs to do:**  
Provide a lightweight, accessible signal that a reader without technical expertise can evaluate. The minimum viable provenance signal that the HSCF’s one-person-on-mobile design constraint was built for. This is the widest deployment context — billions of readers, minimal infrastructure, high volume of attributed content.

**What currently works:** Social verification (is this on the person’s verified account?), institutional verification (is this attributed by a credible outlet with editorial standards?), and the involuntary tells (does this have the texture of something this person would actually say?). All three are degrading — verified accounts are compromised, editorial standards are under pressure, and the involuntary tells are closing.

**What needs to be built:** A provenance signal that travels with attributed content — lightweight enough to be embedded in a social post, verifiable without specialized infrastructure, robust enough to survive the closing of the stylometric window. This is the C2PA (Coalition for Content Provenance and Authenticity) problem space, and it is currently the most active technical development area in the provenance landscape.

**The gap:** The HSCF addresses author-initiated certification for long-form work. The reader verification problem for short-form attributed content at social scale is a different architecture — lower evidentiary standard, much higher volume, much shorter content, real-time verification requirement.

-----

## Parties Not Yet Mapped

The following parties are visible gaps in this mapping — present in the real world, not yet characterized:

|Party                                           |Likely axes                                                   |Primary gap                                                             |
|------------------------------------------------|--------------------------------------------------------------|------------------------------------------------------------------------|
|Educator / academic institution                 |Reputational + financial; institution initiates; preponderance|No framework for evaluating collaborative authorship in academic context|
|Employer verifying work product                 |Financial + legal; institution initiates; preponderance       |Employment law has not addressed AI work product attribution            |
|Insurance / financial services                  |Financial + legal; institution initiates; clear and convincing|Advice and documentation provenance in regulated industries             |
|Regulator verifying compliance filings          |Legal + financial; regulatory body; clear and convincing      |Compliance documents authored by AI without human governance            |
|Platform / publisher enforcing AI content policy|Reputational; automated system; plausible                     |Policy enforcement at scale without human review                        |

Each of these parties can be fully mapped by applying the four axes. The table above is a characterization, not a complete analysis. The full mapping is the next iteration of this document.

-----

## What the Mapping Reveals

Three structural findings that the party-by-party analysis would have obscured:

**Finding 1: The attestation model has a ceiling.**

The HSCF three-layer attestation is appropriate for reputational through legal stakes, with author-initiated or institutional verification, at plausible through clear-and-convincing sufficiency. Below that ceiling, it is the right instrument. Above it — clinical and physical stakes, structural certainty required — deterministic architectural guarantees are required. The Frozen Kernel is the instrument for those contexts. The mapping tells you where the ceiling is.

**Finding 2: The hardest problem is real-time voice.**

Five of the six illustrative parties have a voice provenance dimension that the HSCF cannot address. Party 3 (clinician), Party 4 (court), and Party 5 (patient) all require real-time voice authentication that doesn’t exist at consumer scale. This is the most urgent gap in the provenance landscape and the one with the shortest time horizon before involuntary tells close.

**Finding 3: False negative costs are systematically underweighted.**

Current institutional responses to AI content focus almost entirely on false positive prevention — keeping AI-generated content from being attributed to humans. The false negative problem — human-governed work being wrongly flagged as synthetic — affects authors directly and is borne silently. The Sovereignty Paradox is a systematic false negative generator. No institution currently has a framework for addressing false negative costs to authors. The HSCF’s Gap 3 (false negative protection) addresses the author’s response; this mapping identifies that the institutional gap is structural, not incidental.

-----

## What This Document Does Not Answer

**How** any of these verification needs is technically implemented. That is architecture. It comes after this mapping is validated.

**Who** builds and maintains the infrastructure. That is governance. It also comes after.

**When** — the timeline for closing the involuntary tells window versus the timeline for building replacement infrastructure. The problem-map’s estimate (4–6 months for stylometric, shorter for voice) is the forcing function. This document does not refine that estimate.

-----

## The Negative Space

**OVERLOOKED:** The unmapped parties table is a characterization, not an analysis. Educator, employer, insurer, regulator, and platform verification needs are named but not fully mapped. The next iteration of this document completes those mappings.

**OVERLOOKED:** International variation. Evidentiary standards, consent law, and institutional verification norms vary significantly across jurisdictions. This mapping assumes a broadly Anglo-American legal and institutional context. The axes hold across jurisdictions; the sufficiency levels and failure consequences do not.

**OVERLOOKED:** The infrastructure gap between what the mapping says is needed and what currently exists. The mapping characterizes requirements. It does not assess feasibility. The gap between “real-time voice authentication at consumer scale” (what Party 5 requires) and what currently exists is enormous. Characterizing the gap is not the same as closing it.

**STRUCTURAL:** The mapping does not yet address non-text, non-voice content — images, video, code, data. These are provenance problems with the same axis structure but different technical requirements. They are out of scope for this iteration.

-----

## Version History

|Version|Date      |Status                                                                                                                                            |
|-------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------|
|0.1    |March 2026|Initial mapping. Six parties as worked examples. Five additional parties characterized but not fully mapped. Three structural findings identified.|
|0.2    |TBD       |Complete mapping of unmapped parties. International variation section.                                                                            |
|1.0    |TBD       |Requires: technical feasibility assessment, institutional adoption pathway, voice provenance architecture (separate instrument)                   |

-----

## Relationship to Existing Ecosystem

|Component                               |Trust model connection                                                                        |
|----------------------------------------|----------------------------------------------------------------------------------------------|
|HSCF three-layer attestation            |Serves Axis 1 levels 1–3 (reputational through legal); ceiling at clinical/physical           |
|Frozen Kernel deterministic architecture|Required for Axis 1 levels 4–5 (clinical, physical); structural certainty                     |
|Trust Chain Protocol                    |Chain of custody model maps onto Party 4 (court testimony) and Party 2 (journalistic source)  |
|Therapy Mode Safety Ledger              |Party 3 (clinician verification) — real-time human presence requirement                       |
|Sovereignty Paradox                     |Finding 3 — systematic false negative generation; institutional gap                           |
|Human Provenance Problem Map            |Parent document; three vectors (text, voice, identity) map onto parties 1, 2–5, 6 respectively|

-----

*The mapping is not the architecture.*  
*The mapping is what makes the architecture buildable.*  
*Build this first. Then build the instrument.*
