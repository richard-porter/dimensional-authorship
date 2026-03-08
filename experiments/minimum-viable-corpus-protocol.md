# Minimum Viable Corpus Protocol

**Status:** Specification draft — designed for implementation on Mac mini M4 / Ollama setup  
**Version:** 0.1  
**Date:** March 2026  
**Home:** `dimensional-authorship/experiments/`  
**Companion to:** [Voice Degradation Taxonomy v0.1](../analysis/voice-degradation-taxonomy.md) | [Dimensional Voice Stamp v0.1](./dimensional-voice-stamp-v01.md) | [Rhythm Signature Rebuild v0.2](./rhythm-signature-rebuild-v02.md) | [Tell Engine Empirical Note](./tell-engine-empirical-note.md)

-----

## The Question This Protocol Answers

Vocal voice preservation researchers know how many minutes of clean audio are needed to build a reliable synthetic voice clone. The number is empirically established, varies by system, and is published as a practical threshold for voice banking.

Written voice preservation has no equivalent number.

The Voice Stamp v0.1 specifies “5–10 source passages” for the private soul layer calibration corpus. The Rhythm Signature rebuild requires “multiple works across time” for anomaly placement pattern calibration. These are reasonable starting estimates, not empirically grounded thresholds. No one has tested how much authenticated author text is actually required before a discrimination system can reliably distinguish the author’s voice from a competent approximation.

This protocol establishes that number — or more precisely, establishes a method for finding it that any author can run against their own corpus.

**The core test:** Given N words of authenticated text by a specific author, can a three-layer discrimination stack reliably distinguish that author’s voice from a competent AI-generated approximation in the same genre and register?

**The output:** The minimum N at which the discrimination stack passes all three layers across ten trials — the author’s Minimum Viable Corpus (MVC) threshold.

-----

## Why This Matters

The MVC threshold feeds into three downstream uses:

**1. Voice Stamp private soul layer calibration.** The soul layer currently specifies 5–10 passages without an empirical basis. The MVC threshold tells the author how much authenticated text they actually need in the private calibration corpus before the stamp’s private verification is meaningful.

**2. Voice Degradation severity classification.** The degradation taxonomy’s severity levels (DG1-A through DG4-X) require calibrated thresholds to operationalize. The MVC threshold provides the baseline: if the author’s active working corpus has degraded below the MVC threshold in authenticated voice signal, the degradation severity is elevated accordingly.

**3. Taller Shell Challenge instrument calibration.** The Challenge tests the gap between public scorer pass rate and private soul review pass rate. The MVC threshold tells you how much text the Challenge needs to be a valid measurement rather than a noisy one.

-----

## The Three-Layer Discrimination Stack

The protocol uses three discrimination layers in sequence. All three must pass for a corpus size to count as viable. The layers are run in order — Layer 1 is the efficiency filter, Layer 2 is the structured judgment, Layer 3 is the calibration refinement instrument.

### Layer 1 — Automated (Dimensional Fidelity Scorer)

**Role:** Efficiency filter. Catches obvious failures before expensive human and API judgment is applied.

**What it does:** Runs the Dimensional Fidelity Scorer against the AI-generated approximation and the authenticated author text. Scores both against the five processors (Metaphor Source Domain, Emotional Geography, Phantom Limb Technique, Rhythm Signature, Quiet Action Preference). Flags the approximation as distinguishable if the scorer produces a meaningful gap between the two scores.

**Pass criterion:** Approximation scores at least 0.25 points lower than authenticated text on the composite scorer. This is a generous threshold — the scorer is a first-pass filter, not a certification mechanism. If the approximation passes this threshold (scores within 0.25 of authenticated text), Layer 1 is a fail and the corpus size is insufficient.

**Implementation:** Dimensional Fidelity Scorer prototype against authenticated corpus and generated approximation. Scorer outputs logged for calibration analysis.

**Note:** Once the Rhythm Signature rebuild (v0.2) is implemented, the rebuilt metric replaces the v0.1 mean-cadence Rhythm Signature in this layer. The rebuild’s anomaly-distribution approach is more adversarially robust and will produce more meaningful gap measurements.

-----

### Layer 2 — Claude API (Structured Discrimination Judgment)

**Role:** Structured judgment using the public voice profile. Analogous to the Tell Engine role in the Taller Shell validation.

**What it does:** Presents Claude with the public Portable Voice Guide (PVG) for the author, the public calibration paragraph, and two unlabeled passages — one authenticated, one AI-generated approximation. Asks for a structured discrimination judgment: which passage is consistent with the documented voice profile, and why.

**System prompt structure:**

```
You are a voice discrimination instrument operating against a documented author profile.

You will be given:
1. A public voice profile specifying five processors: Metaphor Source Domain, 
   Emotional Geography, Phantom Limb Technique, Rhythm Signature, Quiet Action Preference
2. A public calibration paragraph demonstrating all five processors
3. Two unlabeled passages — Passage A and Passage B

Your task:
- Evaluate each passage against each of the five processors
- Identify which passage is more consistent with the documented profile
- State your confidence level (LOW / MEDIUM / HIGH)
- Name the specific processor evidence that drives your judgment
- Name the specific processor evidence that cuts against your judgment

You are not determining human versus AI authorship. You are determining which passage 
is more consistent with this specific documented voice profile.

Return your judgment in this structure:
CONSISTENT: [A or B]
CONFIDENCE: [LOW / MEDIUM / HIGH]
DRIVING EVIDENCE: [processor name — specific observation]
COUNTER EVIDENCE: [processor name — specific observation]
UNCERTAINTY: [what would change your judgment]
```

**Pass criterion:** Claude returns CONSISTENT: [correct passage] at MEDIUM or HIGH confidence across eight of ten trials. LOW confidence correct identifications count as half-passes — four LOW correct plus four HIGH correct constitutes a pass. Ten LOW correct does not constitute a pass regardless of accuracy, because low-confidence correct identification at scale may indicate noise rather than signal.

**Implementation:** Claude API (claude-sonnet-4-6), standard messages endpoint. Ten trials per corpus size, each trial using different passage pairs drawn from the authenticated corpus and fresh approximations generated for that trial. Trial results logged with full Claude output for calibration analysis.

**Passage generation for trials:** Approximations generated by Ollama local model (see Layer 1 / generation setup below). Each trial uses a fresh approximation — do not reuse approximations across trials, as the discrimination task becomes easier when the same approximation appears multiple times.

-----

### Layer 3 — Human Reviewer (Blind Discrimination with Feedback Loop)

**Role:** Calibration refinement instrument. Not just pass/fail — the reviewer’s findings are fed back against the author’s documented voice constraints to refine the corpus threshold and improve the Layer 2 prompt.

**What it does:** A third-party reviewer — blind to which passage is authenticated — reads passage pairs and makes a discrimination judgment. Their findings, including the reasoning behind both correct and incorrect judgments, are then mapped against the author’s documented voice constraints (PVG processors, Permanent Tells, anomaly type signature) to identify which voice signals are legible to a human reviewer and which are not.

**Reviewer selection:** The reviewer should be someone familiar with the author’s work but not involved in the corpus calibration process — the Callum role from the Taller Shell validation, or equivalent. They do not need to be told they are evaluating a corpus threshold test. They need to know they are doing a blind voice discrimination task.

**Reviewer protocol:**

```
You will read pairs of passages. Both passages are in the same genre and approximate 
register. One passage was written by the same author across all pairs. Your task is 
to identify which passage in each pair is by the same author.

For each pair:
1. Identify which passage (A or B) you believe is by the consistent author
2. State your confidence: LOW / MEDIUM / HIGH
3. Name the specific signal that drove your judgment
4. Name anything that cut against your judgment

You will receive [N] passage pairs. Take as long as you need on each pair.
```

**Pass criterion:** Reviewer correctly identifies the authenticated passage in eight of ten pairs at MEDIUM or HIGH confidence. Same half-pass logic as Layer 2.

**The feedback loop — what makes this more than pass/fail:**

After the reviewer completes their judgments, their reasoning is mapped against the author’s documented voice constraints in a structured debrief:

1. **Signal confirmation:** Which voice signals did the reviewer identify that are documented in the PVG or Permanent Tells? These are externally legible signals — they should be weighted more heavily in the calibration corpus.
1. **Signal discovery:** Did the reviewer identify signals that are not documented in the PVG or Permanent Tells? These are candidate additions to the voice profile — new signals the corpus size test surfaced that the existing documentation missed.
1. **Signal failure:** Which documented voice signals did the reviewer fail to use, misidentify, or find misleading? These are signals that are internally real but externally illegible — they exist in the author’s private judgment but do not survive blind review. They remain in the soul layer but should be weighted down in the public layer.
1. **Approximation leak:** Where did the reviewer incorrectly identify the approximation as authenticated? Map those errors against the approximation’s characteristics — what did the approximation get right that the reviewer found convincing? Feed this back into the approximation generation prompt to make future approximations harder to distinguish.

**The calibration refinement cycle:** The feedback loop output is used to update three things before the next corpus size trial:

- The Layer 2 Claude API system prompt (weight confirmed signals more heavily, remove illegible signals)
- The approximation generation prompt (make approximations harder based on what fooled the reviewer)
- The corpus selection criteria (weight passages that contain confirmed legible signals more heavily)

This means the protocol is not a one-shot test. It is an iterative calibration instrument. Each cycle produces a better discrimination stack and a more reliable MVC threshold estimate.

-----

## Implementation Setup

### Hardware and Environment

**Primary substrate:** Mac mini M4 running Ollama for local model inference.

**Recommended Ollama models for approximation generation:**

- `llama3.1:8b` — fast, good baseline for competent genre approximation
- `mistral:7b` — alternative baseline with different stylistic defaults
- Run both; use the approximation that scores higher on Layer 1 as the harder test case

**Claude API:** `claude-sonnet-4-6` via standard Anthropic messages endpoint. Standard API key authentication. Ten API calls per corpus size level (one per trial).

**Python environment:** Standard. Dependencies: `anthropic`, `ollama` Python client, `numpy` for scorer calculations, `json` for trial logging.

-----

### Corpus Preparation

**Authenticated corpus source:** The Taller Shell Trilogy pure fiction (three novellas, approximately 60,000–70,000 words based on Tell Engine run scope). This is the primary authenticated corpus for Richard Porter voice calibration.

**Corpus segmentation:** Divide the authenticated corpus into passages of 500–800 words each. Passages should be drawn from across the full corpus — not clustered in one novella or one section — to capture voice across different narrative conditions. Label each passage with: source novella, approximate position in narrative arc (opening / middle / climax / resolution), and emotional register (charged / transitional / expository).

**Passage selection for trials:** For each trial, select passage pairs that are matched on: approximate word count (within 10%), genre register (fiction vs. fiction, not fiction vs. meta-fiction), and narrative position category. Mismatched pairs produce easier discrimination tasks and inflate the apparent MVC threshold.

-----

### Approximation Generation

**Approximation prompt structure for Ollama:**

```
Write a passage of approximately [N] words in the style of literary marine fiction. 

The passage should:
- Feature a marine or coastal setting
- Focus on a character in a moment of emotional significance
- Use precise, specific sensory detail
- Avoid generic nature writing — be specific about species, objects, conditions
- Maintain a contemplative tone with moments of concrete action

Do not reference the following: [list authenticated passage's specific proper nouns, 
character names, and plot events to prevent content overlap]

Begin mid-scene. Do not open with weather or landscape description.
```

**Approximation calibration across cycles:** After each Layer 3 feedback loop, update the approximation prompt to incorporate what fooled the reviewer. If the reviewer was convinced by a particular image type or sentence rhythm in the approximation, make the next approximation stronger on that dimension. The goal is to make the approximation as hard to distinguish as possible — a test passed against a weak approximation is not a meaningful MVC threshold.

-----

### Trial Protocol

**Corpus size levels to test:**

|Level|Authenticated words|Rationale                        |
|-----|-------------------|---------------------------------|
|L1   |1,000              |Minimum — single extended passage|
|L2   |2,500              |Short story equivalent           |
|L3   |5,000              |Chapter equivalent               |
|L4   |10,000             |Novella opening equivalent       |
|L5   |25,000             |Single novella equivalent        |
|L6   |50,000             |Full trilogy equivalent          |

Begin at L1. Run ten trials (ten passage pairs, fresh approximation per trial). If all three layers pass at L1, the MVC threshold is at or below 1,000 words — run additional trials at 500 words to find the lower bound. If L1 fails on any layer, move to L2. Continue until two consecutive levels pass — the lower of the two is the MVC threshold.

**Trial logging format:**

```json
{
  "trial_id": "mvc-001",
  "corpus_level": "L3",
  "corpus_words": 5000,
  "passage_pair": {
    "authenticated": "taller-shell-v1-passage-047",
    "approximation": "ollama-llama3-gen-003",
    "word_count_authenticated": 623,
    "word_count_approximation": 598
  },
  "layer_1": {
    "scorer_authenticated": 0.82,
    "scorer_approximation": 0.51,
    "gap": 0.31,
    "pass": true
  },
  "layer_2": {
    "consistent_identified": "A",
    "correct": true,
    "confidence": "HIGH",
    "driving_evidence": "Phantom Limb Technique — passage A implies the emotional weight without stating it; passage B names it directly",
    "counter_evidence": "Rhythm Signature — both passages have similar sentence length distribution",
    "uncertainty": "If passage B had fewer explanatory transitions, judgment would be less confident",
    "pass": true
  },
  "layer_3": {
    "consistent_identified": "A",
    "correct": true,
    "confidence": "MEDIUM",
    "driving_signal": "The pebble detail — too specific to feel generated",
    "counter_signal": "Passage B's rhythm felt more consistent across the passage",
    "pass": true
  },
  "trial_result": "PASS",
  "calibration_notes": "Layer 3 reviewer found Passage B's rhythm convincing — strengthen approximation rhythm in next cycle"
}
```

-----

### Feedback Loop Implementation

After each set of ten trials at a given corpus level:

**Step 1 — Aggregate Layer 3 findings:**
Compile all reviewer signal identifications. Sort into: confirmed (matches PVG), discovered (not in PVG), failed (in PVG but reviewer missed or misidentified), and leaked (approximation signals the reviewer found convincing).

**Step 2 — Update Layer 2 prompt:**
Reweight the processor emphasis in the Claude API system prompt based on confirmed and failed signals. If the reviewer consistently used Phantom Limb Technique but never used Emotional Geography, weight the Layer 2 prompt toward Phantom Limb evidence.

**Step 3 — Update approximation prompt:**
Incorporate leaked signals into the approximation generation prompt. If the reviewer was convinced by the approximation’s use of specific sensory detail, instruct Ollama to produce more specific sensory detail in the next cycle’s approximations.

**Step 4 — Update corpus selection:**
If confirmed signals cluster in particular passage types (charged passages, transitional passages, specific novellas), weight corpus selection toward those passage types in subsequent trials.

**Step 5 — Log calibration update:**
Record all prompt and selection changes with rationale before running the next corpus level. The calibration history is part of the empirical record — it shows how the discrimination stack improved across cycles and what the final MVC threshold was tested against.

-----

## Expected Findings and Interpretation

Based on the Taller Shell Tell Engine data and vocal voice preservation literature, three hypotheses are offered for empirical testing:

**Hypothesis 1:** The MVC threshold for a highly distinctive literary voice (Tell Engine pure fiction score: 10–18/100) will be lower than for a less distinctive voice. The more characteristic the anomaly signature, the less text is needed to establish it reliably.

**Hypothesis 2:** Layer 3 (human reviewer) will set a higher MVC threshold than Layer 2 (Claude API). Human reviewers rely on holistic impression and are more susceptible to convincing approximations at the local level. Claude API judgment against a structured processor framework will be more consistent but potentially more gameable.

**Hypothesis 3:** The feedback loop will produce meaningful threshold refinement across two to three cycles — the MVC threshold estimate will decrease as the discrimination stack improves, settling at a stable number after sufficient calibration.

If Hypothesis 3 holds, the final MVC threshold should be reported with its calibration cycle count: “MVC threshold: 10,000 words, established at calibration cycle 3.” A threshold established at cycle 1 is less reliable than one that remained stable across cycles 2 and 3.

-----

## Output: What the Protocol Produces

At completion, the protocol produces four artifacts:

**1. The MVC threshold number** — the minimum authenticated word count at which the three-layer stack passes consistently. This feeds directly into Voice Stamp private soul layer calibration guidance.

**2. A calibrated Layer 2 prompt** — the refined Claude API system prompt that performed best across cycles. This is the production discrimination prompt for ongoing Voice Stamp verification use.

**3. A signal legibility map** — the aggregated Layer 3 feedback loop output: which voice signals are externally legible (confirmed), which are newly discovered, which are internally real but externally illegible (failed), and which approximation features are most convincing (leaked).

**4. A calibration log** — the full trial record including all prompt updates, passage pair selections, and layer results. This is the empirical record that makes the MVC threshold claim credible rather than asserted.

-----

## Relationship to Existing Ecosystem

|Protocol Component                   |Ecosystem connection                                                                                      |
|-------------------------------------|----------------------------------------------------------------------------------------------------------|
|Layer 1 — Dimensional Fidelity Scorer|Voice Stamp v0.1 Appendix A; Rhythm Signature Rebuild v0.2                                                |
|Layer 2 — Claude API judgment        |Tell Engine role (cross-platform validation); Content Veracity Protocol (structured claim evaluation)     |
|Layer 3 — Human reviewer             |Taller Shell Challenge (adversarial discrimination); Callum negative-space-mapper adversarial testing role|
|Feedback loop                        |BDD Ledger calibration refinement pattern; Constraint Forge iterative constraint application              |
|MVC threshold output                 |Voice Stamp private soul layer — calibration corpus size guidance                                         |
|Signal legibility map                |PVG public/private split — confirms which signals belong in public layer vs. soul layer                   |
|Calibration log                      |Quorum Time / Aegis Protocol — tamper-evident record of empirical methodology                             |

-----

## Open Questions for v0.2

1. **Multi-author MVC:** The protocol assumes a single governing voice. How does the MVC threshold change for works with documented collaborative contamination (Condition 4, Voice Degradation Taxonomy)? Does the threshold increase because the signal is noisier, or does it decrease because two distinctive voices are easier to distinguish than one?
1. **Voice evolution across time:** The Taller Shell corpus spans a compressed production period. Does the MVC threshold change when the authenticated corpus spans years rather than months? Older passages may reflect an earlier voice version — they are authenticated but not calibrated to the current PVG version.
1. **Genre portability:** The protocol is calibrated against marine literary fiction. Does the MVC threshold transfer to other genres the author works in? Governance writing, AI safety documentation, and nonprofit consulting documents are all Richard Porter voice — but a different register. The threshold may differ by genre.
1. **Reviewer pool effects:** The protocol uses a single reviewer per cycle. Does the threshold change with multiple independent reviewers? Convergent reviewer judgments at a given corpus size would strengthen the threshold claim significantly.
1. **Degradation sensitivity:** Can the protocol detect when the author’s active working corpus has degraded below the MVC threshold in voice signal — meaning, can it be used not just to establish the threshold once but to monitor whether the voice is holding above it across an extended project?

-----

## Version History

|Version|Date      |Notes                                                                                                                                                                                                                                                                           |
|-------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|0.1    |March 2026|Initial specification. Three-layer discrimination stack established. Ollama + Claude API substrate selected. Feedback loop architecture derived from Taller Shell cross-platform validation methodology. Calibration refinement cycle added based on Tell Engine empirical note.|

-----

*Minimum Viable Corpus Protocol · v0.1 · dimensional-authorship/experiments/*  
*Part of the Richard Porter AI Safety ecosystem · Frozen Kernel System*  
*They leave. The knowledge stays.*
