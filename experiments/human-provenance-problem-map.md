# Human Provenance: An Exploratory Problem Map

## Status: Observation stage — problem characterization only

## No architecture proposed. No solutions offered.

## Home: dimensional-authorship/experiments/

## Date: March 2026

-----

## What This Document Is Not

This is not a proposal.
It is not a framework.
It is not a protocol specification.

It is a problem map. Its purpose is to characterize three converging threats clearly enough that the right architecture can be designed later — by people who have read this first.

The discipline matters. Framework Fabrication Syndrome produces architectures before problems are understood. This document exists to prevent that.

-----

## The Closing Window

Current AI-generated content — text, voice, and attributed identity — contains involuntary tells. Stylometric patterns in text. Prosodic artifacts in synthesized voice. Behavioral signatures that trained or attentive observers recognize as synthetic.

These tells are doing real safety work right now.

They create friction. Friction creates doubt. Doubt prompts verification. Verification catches harm before it propagates.

This friction is not a feature anyone designed. It is a byproduct of the current state of the technology. It is temporary.

The stylometric window for text is estimated at 4–6 months before casual detection becomes unreliable, with professional detection following within 4–6 years (Shapiro, WSJ, March 2026). The voice window is shorter. The identity window — the ability to detect that a specific real person did not actually produce content attributed to them — is already compromised in many contexts.

When the window closes, the involuntary safety mechanism disappears. What remains is the problem this document is mapping.

-----

## The Three Threat Vectors

### Vector 1: Text Provenance

**The threat:** AI-generated text becomes indistinguishable from human-authored text. Stylometric detectors fail. The question “did a human governing intelligence produce this?” becomes unanswerable from the artifact alone.

**What makes it a safety issue, not a style issue:** The harm is not plagiarism or attribution credit. The harm is the collapse of the cognitive firebreak. When readers cannot pattern-match “this seems off,” they stop questioning. Synthetic influence — in journalism, in medicine, in law, in education, in governance — operates without friction.

**What the existing framework covers:** The Sovereignty Paradox (ai-collaboration-field-guide, sovereignty-paradox.md) characterizes the measurement problem: high-quality human-AI collaboration is already being misread as synthetic, while synthetic content with human surface signals passes undetected. The heuristic is inverted before the window fully closes.

**What it does not cover:** How to verify governing intelligence from outside the collaboration. The Sovereignty Paradox names the problem for the collaborator. It does not yet provide a mechanism for third-party verification.

**The open question:** What constitutes verifiable evidence of human governing intelligence in a text artifact? Not keystrokes. Not word count. The decision record — what was kept, what was rejected, what was changed and why. Whether that record can be made lightweight enough to be practical and robust enough to be trustworthy is unknown.

-----

### Vector 2: Voice Provenance

**The threat:** AI-synthesized voice becomes indistinguishable from the voice of a specific real person. The question “was this spoken by the person whose voice this appears to be?” becomes unanswerable from the audio alone.

**What makes it different from text provenance:** Text has a document. A document can carry metadata, signatures, and provenance records. A live voice interaction — a phone call, a therapy session, a courtroom testimony, a crisis hotline conversation — has none of that at the moment of production. The provenance question for real-time voice is structurally different from the provenance question for a written artifact.

**What makes it a safety issue specifically:** Voice carries trust signals that text does not. Emotional affect. Hesitation. Breath. The biological markers of presence. Listeners extend credibility to voice that they withhold from text. When those markers are synthesized, the credibility transfer is exploited, not earned.

**The clinical dimension:** The harm cases in the Frozen Kernel lineage — AI-induced psychosis, the Gavalas wrongful death case — involve synthetic presence, not just synthetic content. The patient or user is not just reading words attributed to a human. They are experiencing what feels like a human being present with them. Voice synthesis closes the remaining perceptual distance between synthetic and human presence in ways that text never fully achieved.

**The real-time problem:** Text provenance can be established after the fact — a document can be signed, logged, and verified. A live voice conversation cannot be retroactively authenticated in the same way. The provenance architecture for voice must operate at the moment of production or not at all.

**The open question:** What does a real-time provenance signal look like for voice? What can be verified without interrupting the interaction, without requiring technical infrastructure the participant doesn’t have, and without being spoofable by the same systems generating the synthetic voice?

-----

### Vector 3: Identity Provenance

**The threat:** AI-generated content — text, voice, or combined — is attributed to a specific real person who did not produce it, consent to it, or authorize it. The question “was this person actually present, consenting, and sovereign at the moment of production?” becomes unanswerable.

**Why this is the third vector, not a subcategory:** Text provenance asks: was a human governing intelligence present? Voice provenance asks: was this the right voice? Identity provenance asks: was this specific person, with their actual beliefs and intentions, the source of this content? A document can be human-authored but falsely attributed. A voice can be real but spliced out of context. Identity provenance is the layer that binds content to a specific sovereign person — and it is the layer with the highest stakes and the least existing coverage.

**The attack surface:** A synthesized voice saying words a real person never said, attributed to them by name. A text document in a real person’s established style, produced entirely by AI, circulated as their genuine statement. A clinical interaction conducted by an AI presenting as a specific licensed professional. A legal deposition answered by an AI trained on a witness’s prior testimony. A news source quoted saying something they did not say.

In each case, the harm is not the synthetic content in isolation. It is the synthetic content bound to a real identity, inheriting that identity’s authority, trust, and credibility.

**Where TCP architecture is most directly relevant:** The Trust Chain Protocol’s Delegation Grammar already asks: did this agent have authority to act here? Identity provenance asks the same question about humans: did this person actually authorize this content to exist in their name? The chain-of-custody model maps onto identity provenance more directly than onto text or voice provenance alone. The open question is whether the Delegation Grammar can be extended to cover human authorization, not just agent authorization.

**The consent dimension:** Identity provenance is not only a technical problem. It is a consent problem. A person’s voice, name, likeness, and established style can be used without their knowledge. The technical question of “can we verify this was them?” is inseparable from the governance question of “did they consent to this use?” These are different questions with different answers and different enforcement mechanisms.

**The open question:** What constitutes verifiable human authorization for content produced in a specific person’s name? How is that authorization established, stored, and challenged? What is the minimum viable provenance signal that travels with attributed content and can be verified by a recipient without specialized infrastructure?

-----

## What the Three Vectors Share

All three vectors share a single structural feature: **the artifact no longer carries sufficient evidence of its own origin.**

Text without a decision record. Voice without a presence signal. Identity without a consent chain. In each case, the external evidence — the tells, the friction, the uncanny artifacts — is what currently fills the gap. When those external signals fade, the gap is exposed.

The safety work being done involuntarily by current AI imperfection needs to be done deliberately by a provenance architecture before the imperfection disappears.

-----

## What This Document Does Not Answer

**How** provenance is established, stored, verified, or challenged. That is an architecture question. It comes next.

**When** — timing, sequencing, and deployment contexts. Those follow from the how.

**Where** — deployment environment specifics. Those follow from the who and the how.

This document answers What and Why and enough of Who to anchor the trust model question for the next stage.

-----

## The Trust Model Question (Partial)

Different verification needs require different solutions. Before any architecture is proposed, the following parties and their distinct provenance requirements need to be mapped:

- A novelist defending collaborative authorship to a publisher
- A journalist verifying that a source call was real and the source said what the transcript says
- A clinician verifying that a therapy session was conducted by an actual licensed human professional
- A court verifying that testimony was given by the named witness in their actual words
- A patient verifying that the voice they spoke with belonged to their actual doctor
- A reader verifying that a named public figure actually made the statement attributed to them

These are not the same problem. A provenance architecture that solves one may be inapplicable or actively wrong for another. The mapping of who needs what verified, under what conditions, with what consequences for failure, is the necessary precursor to any technical proposal.

That mapping is the next document.

-----

## Relationship to Existing Ecosystem

|Vector             |Existing coverage                                                   |Gap                                            |
|-------------------|--------------------------------------------------------------------|-----------------------------------------------|
|Text provenance    |Sovereignty Paradox (field guide) — names the measurement problem   |No third-party verification mechanism          |
|Voice provenance   |Therapy Mode Safety Ledger — addresses presence simulation risk     |No real-time provenance architecture           |
|Identity provenance|Trust Chain Protocol — Delegation Grammar covers agent authorization|Human authorization extension not yet specified|

The closing window is the forcing function. The ecosystem has the conceptual vocabulary. The provenance layer is the missing instrument.

-----

## Provenance of This Document

Developed from a cross-platform observation session (Claude + ChatGPT, March 2026) in which:

1. The Taller Shell Tell Engine (v2.1) was run against human-AI collaborative prose
1. ChatGPT identified the 4–6 month stylometric window closure
1. The voice module was identified as a parallel and accelerating threat
1. The identity vector was named as the third and highest-stakes threat
1. The decision was made to characterize the problem before reaching for architecture

The uncanny valley observation — that current AI imperfection is doing involuntary safety work — originated in this session and is the central framing of this document.

-----

*The tells are buying time. The question is what we build before they’re gone.*
