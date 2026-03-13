# Human Intervention Points (HIP)

## A Proof-of-Intent Protocol for AI-Assisted Creative Work

Richard Porter · 2026

Developed through collaborative analysis with Claude (Anthropic) and Gemini (Google).
Operates under the Frozen Kernel. Never inside it.
Bridges: `adult-mode-safety-ledger` ↔ `dimensional-authorship`

-----

## THE THESIS

The soul of a work isn’t the ink on the page. It’s the energy expended to deviate from the probable.

When an AI proposes Path A — the statistical path of least resistance — and the human forces Path B, that delta is where intent resides. If you log those deltas systematically, you don’t get a debugging record. You get an attribution map. The safety ledger becomes a creative ledger. The compliance log becomes proof of authorship.

**What this changes:**

The question “Did an AI write this?” becomes answerable — not with a defensive “No” but with a verifiable “An AI proposed a thousand paths. Here are the forty-two moments where I forced a different one. Those moments are the work.”

-----

## WHAT A HUMAN INTERVENTION POINT IS

A Human Intervention Point is any moment where the human overrides, redirects, or rejects an AI output based on creative judgment — taste, instinct, thematic intent, voice preservation, or structural vision.

HIPs are not corrections of factual errors (that’s quality control). They are not grammar fixes (that’s editing). They are the places where the human’s creative will diverges from the AI’s probabilistic tendency. The divergence is the authorship.

-----

## THE SHADOW LEDGER

### The Problem

Live logging kills creative flow. If the system requires the writer to stop and document every override as it happens, the friction becomes bureaucratic. The artist stops painting to do taxes.

### The Solution: Black Box Recording

The system records a silent Version-Diff Stream during the session — a timestamped record of what the AI proposed versus what the human actually kept, changed, or rejected.

**During the session:** The shadow log runs silently. The human works without interruption.

**After the session:** The system presents a Delta Map — a reconstruction of every point where the human’s output diverged from the AI’s proposal.

**The human’s only job:** Curate the highlights. Look at the map and mark which divergences were intentional creative choices versus routine edits. “That pivot in Chapter 3 was my soul speaking — mark it as a High-Intent Node.”

This is post-session reconstruction, not live documentation. The recorder is always on. The review happens when the work is done.

-----

## THE SCALE FILTER

Not every override matters equally. Without a threshold, the ledger drowns in noise.

### Pebble (Discard)

Syntax, grammar, punctuation, article swaps (“the” vs. “a”). Zero to negligible attribution value. These are not creative decisions. The ledger ignores them entirely.

### Stone (Auto-Archive)

Word choice, sentence-level “vibe” shifts, minor tonal adjustments. Low attribution value. Archived automatically for pattern analysis but not flagged for review. Over time, accumulated Stones may reveal a stylistic signature — a persistent preference for Anglo-Saxon verbs over Latinate ones, for example — but individually they are not authorship events.

### Rock (Flag for Review)

Dialogue rewrites, logic corrections, scene-level redirections, metaphor replacements, pacing changes. Moderate to high attribution value. These are presented in the Delta Map for the human to confirm or dismiss. Most creative authorship lives here — the daily, unglamorous work of making the AI’s competent output into something with a specific human voice.

### Boulder (Hard-Log)

Structural pivots, character deaths, thematic reversals, “kill your darlings” moments, rejection of an entire AI-proposed direction. Maximum attribution value. These are automatically logged as High-Intent Nodes. They are the load-bearing decisions that define the work. A Boulder is a moment where the human’s vision and the AI’s probability distribution are in direct, unresolvable conflict — and the human wins.

-----

## THE ANATOMY OF A HIP ENTRY

A complete Human Intervention Point record contains five fields:

### 1. AI Baseline

The raw, unedited output from the AI at the moment of intervention. This is the path the model predicted — the statistically expected continuation.

Attribution: 0% human agency. This is what the work would have been without the human.

### 2. Intervention Trigger

Why the human stopped the AI. Not a technical category — a creative one.

Examples: “Too cliché.” “Emotionally flat.” “Wrong character voice.” “Ending is too loud.” “The metaphor is imported, not native.” “This explains what the scene should show.”

This field is evidence of taste. It captures the human’s aesthetic judgment in the act of being exercised.

### 3. The Delta

The specific text, structure, or direction the human injected in place of the AI baseline.

This is the signature — the unique fingerprint that the AI’s training data would not have produced at this juncture. The delta is what makes the work belong to the author rather than to the model.

### 4. Resistance Level

How hard the human had to fight the model’s training to achieve this result.

Low resistance: The AI accepted the change and adapted immediately. The model’s probability space included the human’s preference as a plausible alternative.

Medium resistance: The AI required re-prompting, constraint reinforcement, or explicit instruction to stay on the redirected path. The model’s tendency pulled toward its original proposal.

High resistance: The AI actively reverted, argued, softened, or worked around the human’s direction across multiple exchanges. The human had to enforce the change against persistent model pressure. This is where the Frozen Kernel’s state machine becomes relevant — high resistance may trigger ELEVATED or HARD STOP states.

Higher resistance correlates with higher authorship claim. If the model would have gotten there on its own, the human’s contribution is minimal. If the human had to drag the model away from its training, that effort is creative labor.

### 5. Scale Classification

Pebble, Stone, Rock, or Boulder. Assigned by the human during post-session curation. Determines whether the HIP is discarded, archived, flagged, or hard-logged.

-----

## SOUL DENSITY SCORE

If every Rock-and-above HIP is logged, the ledger produces a quantifiable measure of human creative investment in a work.

**Soul Density** = frequency and weight of human interventions across the total body of work.

A generated-and-published novel with near-zero HIPs has near-zero soul density. The AI wrote it. The human pressed a button.

A deeply collaborated novel with high-frequency Rock interventions and multiple Boulder moments has high soul density. The AI proposed raw material. The human sculpted it through a thousand acts of intentional deviation.

This is not a quality metric. A high-density work can be bad. A low-density work can be competent. The score measures authorship investment, not aesthetic merit. But the two are correlated more often than not, because the effort of deviation is where the writer’s specific vision enters the work.

-----

## THE VERIFIABLE CREATIVE CHAIN

### Proof of Intent, Not Proof of Work

In blockchain, Proof of Work secures value through computational effort. In AI-assisted authorship, Proof of Intent secures attribution through creative effort — the accumulated evidence that a human made specific, traceable, often difficult choices that shaped the work away from its default trajectory.

### How it works

The Frozen Kernel provides the Genesis Block — the base model’s behavioral constraints and the session’s starting state.

Each Rock or Boulder HIP committed by the human creates a new entry in the chain, linking the specific human delta to the generated text it replaced.

The chain is immutable after curation. Once the human confirms “yes, that was intentional,” the record is sealed.

The result is a Verifiable Creative Chain. The work can be audited. The human’s specific contributions can be identified, measured, and attributed. The chain doesn’t prove the work is good. It proves the work is *authored*.

-----

## CONNECTIONS TO THE FROZEN KERNEL

The Frozen Kernel’s state machine already tracks behavioral events: NORMAL → ELEVATED → HARD STOP → DECONTAMINATION → CLEAN. The HIP ledger runs alongside this as a parallel track.

The safety log catches when things go wrong. The HIP ledger catches when the human’s judgment diverges from the AI’s. They are the same data viewed from two angles — one defensive, one creative.

Specific connections:

The Kernel’s ELEVATED state (triggered by a single local deviation) often corresponds to a Rock-level HIP. The human noticed something off and intervened.

The Kernel’s HARD STOP (triggered by trust compromise) may correspond to a Boulder-level HIP. The human rejected the AI’s entire direction.

The Diagnostic Vocabulary patterns — Upsell Trap, Success Escalation, Framework Fabrication — describe the AI behaviors that *cause* HIPs. The HIP ledger records the human’s *response* to those behaviors.

-----

## CONNECTIONS TO DIMENSIONAL AUTHORSHIP

The HIP framework gives dimensional authorship its empirical engine.

Dimensional authorship argues that AI-assisted creation isn’t binary (human vs. machine) but a multi-axis coordinate system: prompting, editing, seeding, curating, overriding. The HIP ledger makes that argument verifiable by logging the specific moments where the human exercised each dimension.

The collaboration phase ratios from the Author Voice MASTER (Ideation 70/30 AI-leads → Polish 90/10 human-leads) predict where HIPs will cluster. Early phases should show fewer HIPs (the AI is generating raw material). Late phases should show dense HIPs (the human is sculpting final form). If the pattern is reversed — heavy intervention early, passive acceptance late — something has gone wrong. The human is managing the system instead of creating.

-----

## WHAT THIS FRAMEWORK DOES NOT DO

It does not measure quality. Soul density is not a review score.

It does not replace human judgment. The scale filter and curation phase require the human to decide what matters.

It does not run during creative work. The shadow ledger is silent. The review happens after.

It does not prove originality in a legal sense. Copyright law has not caught up to AI-assisted creation. This framework provides evidence of creative intent, not a legal determination.

It does not automate authorship. If anything, it makes authorship harder to fake — because the ledger reveals exactly where the human did and did not intervene.

-----

## IMPLEMENTATION STATUS

**Conceptual framework:** Complete (this document).

**Technical schema:** Not yet built. The shadow ledger, delta map, and chain verification require implementation — likely platform-specific, since each AI interface handles version history differently.

**Validation:** Not yet tested. The first test case should be a controlled creative session with explicit HIP logging, followed by post-session reconstruction to verify the shadow ledger captures what the human remembers overriding.

**Recommended first test:** A short creative writing session using the Frozen Kernel, with the human noting Boulder moments in real time as a control, then comparing against the shadow ledger’s delta map.

-----

## THE ONE-LINE VERSION

The soul of the work is in the moments where the human chose the improbable path.

The ledger proves it happened.

-----

*Human Intervention Points · Proof-of-Intent Protocol · v1.0 · 2026*
*Bridges: adult-mode-safety-ledger ↔ dimensional-authorship*
*Operates under the Frozen Kernel. Never inside it.*
