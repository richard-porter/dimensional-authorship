# Voice Preservation Framework

**Purpose:** Methodology for maintaining authentic authorial voice during AI-assisted creative work.  
**Placement:** dimensional-authorship/analysis/voice-preservation-framework.md  
**Relationship:** Complements escalation-white-paper.md (what went wrong) with what worked.

-----

## The Problem

AI collaboration erodes voice through two mechanisms:

1. **Stylistic averaging** — AI defaults to median prose, smoothing distinctive patterns toward generic competence.
1. **Gradual displacement** — Over iterations, AI-generated phrasing replaces human phrasing without the author noticing.

The result is technically competent but emotionally flat output — a “procedural ghost” of the author’s voice.

-----

## The Architecture: Dual-System Design

Voice preservation requires two documents working together:

### 1. Portable Voice Guide (PVG)

A permanent document that travels across sessions and platforms. Contains:

- **Metaphor Source Domain** — Where the author’s figurative language originates (e.g., marine biology, industrial process, domestic space).
- **Emotional Geography** — How the author handles proximity to emotional content (direct confrontation vs. displacement vs. quiet orbit).
- **Phantom Limb Technique** — What the author leaves unsaid and how absence functions as meaning.
- **Rhythm Signature** — Sentence length patterns, paragraph cadence, punctuation habits.
- **Quiet Action Preference** — How the author renders characters doing things (grand gesture vs. small domestic motion).

These five processors define voice at the structural level, not the word level. They are harder to erode because they operate beneath vocabulary.

### 2. Project-Specific Primer (PSP)

A session document that adapts the PVG to a specific work. Contains:

- Which processors are dominant for this project
- Specific constraints (e.g., “no metaphors above waterline” or “all emotion through object interaction”)
- Calibration examples — 2-3 paragraphs that demonstrate the target voice
- Anti-examples — prose that sounds close but is wrong, with explanation of why

The PSP expires with the project. The PVG persists.

-----

## The Capture Protocol

Voice guides cannot be written from theory. They must be extracted from existing work.

### Step 1: Collect Samples

Pull 5-10 passages from completed work that feel most “yours.” Don’t analyze yet — just collect on instinct.

### Step 2: Identify Structural Patterns

For each passage, ask:

- Where do the metaphors come from? (domain)
- How close does the prose get to the emotional center? (geography)
- What’s missing that matters? (phantom limb)
- What’s the sentence rhythm? (signature)
- How do characters act? (quiet action)

### Step 3: Write the Guide

Document each processor with 1-2 examples. Keep the guide under 500 words. Longer guides get ignored by both humans and AI.

### Step 4: Test Cross-Platform

Run the same creative prompt through 2-3 AI systems with the guide attached. Compare outputs for voice fidelity. Revise the guide based on where it fails.

-----

## Why This Works (The Soul vs. Skeleton Finding)

Testing revealed that structured guides (rules, templates, checklists) produce the **skeleton** of voice — technically compliant but lifeless output. Philosophical guides (manifesto-style, narrative, essayistic) produce the **soul** — meaning, nuance, authentic texture.

Effective voice preservation requires both:

- **Skeleton** (PVG structure) ensures consistency across sessions
- **Soul** (calibration examples + anti-examples) ensures authenticity within sessions

Output generated with only structural rules is “debugged of life” — competent yet uncanny. The calibration examples are what prevent the procedural ghost.

-----

## Cross-Platform Behavior

Voice guides function as an AI-side **lens** — they filter output through stylistic constraints. This works because:

- The human’s voice is consistent (the input doesn’t change)
- The guide provides stable constraints (the filter doesn’t change)
- Only the AI’s generation varies (manageable variance)

This is distinct from security constraints, which require a human-side **helmet** because AI output variance is the threat, not the thing being filtered. See: escalation-white-paper.md for the Helmet vs. Lens distinction.

-----

## Limitations

- Voice guides reduce but do not eliminate stylistic drift
- Longer sessions produce more drift regardless of guide quality
- AI systems vary in responsiveness to voice constraints (testing showed 75-90% fidelity depending on platform and task type)
- The human must remain the final judge of voice authenticity — no metric substitutes for “does this sound like me?”

-----

## Integration with Dimensional Authorship

This framework addresses the **creative methodology** dimension of the authorship model:

- **What went wrong** → escalation-white-paper.md, glossary-of-patterns.md
- **What the theory says** → thesis.md, core-architecture.md
- **What worked creatively** → this document
- **How to read the repo** → reading-order.md

The voice preservation framework is evidence that constraint-based AI collaboration can produce authentic creative work when the constraints are structural (processor-level) rather than superficial (word-level).
