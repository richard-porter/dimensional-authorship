# Rhythm Signature Rebuild — Dimensional Fidelity Scorer v0.2

**Status:** Specification draft — not yet implemented  
**Repo:** `dimensional-authorship/experiments/rhythm-signature-rebuild-v02.md`  
**Supersedes:** Dimensional Voice Stamp v0.1, Appendix A — Rhythm Signature metric (mean-cadence approach)  
*Part of the [dimensional-authorship](https://github.com/richard-porter/dimensional-authorship) project.*

-----

## Why This Rebuild Is Needed

The Dimensional Fidelity Scorer v0.1 Rhythm Signature metric measures sentence-length entropy, punctuation cadence, and paragraph rhythm vectors compared against a public calibration paragraph. It flags text with statistically anomalous rhythm relative to the documented signature.

This is mean-cadence detection. It asks: does this text’s average rhythm match the author’s average rhythm?

The problem is architectural, not calibration-based. AI is effective at matching means. A model given the public calibration paragraph can approximate the average sentence length distribution, the average punctuation cadence, the average paragraph rhythm. Mean-matching is exactly what language models are optimized to do. A scorer built on means will be defeated by any model specifically trained to pass it — and will be defeated without much effort, because the means are in the public layer.

The Appendix A development note in the Voice Stamp v0.1 identified this problem precisely:

> *“A more adversarially robust scorer would measure outliers — the characteristic anomalies that define a voice rather than its average. Human voice is defined by its productive errors: the sentence that runs too long, the metaphor that is slightly broken but emotionally precise, the structural choice that violates craft convention for reasons only the author could explain. AI smooths these out.”*

This document is the full specification for that rebuild.

-----

## The Formant Analogy

Vocal voice preservation does not model average voice. It isolates **formants** — the resonant frequencies that remain stable and distinctive independent of what words are being said. Formants are not average properties of a voice. They are the invariant structural signature underneath the content.

The written analog is the **characteristic anomaly distribution**: the pattern of productive errors, broken-but-precise metaphors, over-long sentences, and convention-violating structural choices that recur across a writer’s work. These are not average properties of the voice. They are the invariant signature underneath the surface.

The rebuild replaces mean-cadence detection with anomaly-distribution detection. The scorer stops asking “does this text’s average rhythm match?” and starts asking “does this text’s anomaly pattern match?”

This is a fundamentally different measurement. A model that successfully matches the mean will still fail the anomaly distribution check — because AI smooths anomalies out, and the smoothing is the tell.

-----

## What the Rebuilt Metric Measures

### Component 1: Anomaly Frequency

**What it measures:** How often does the text produce rhythm events that fall outside the normal distribution for the genre?

Normal distribution here means: sentence lengths, punctuation patterns, and paragraph structures that a competent writer in this genre would produce. Anomalies are events that fall outside that distribution — sentences that are dramatically longer or shorter than genre norms, punctuation patterns that violate standard conventions, paragraph structures that break expected rhythm.

**Why it matters:** Every writer has a characteristic anomaly frequency — how often they depart from genre norms. A writer with low anomaly frequency is disciplined and conventional. A writer with high anomaly frequency takes more risks. AI, absent specific instruction, gravitates toward moderate anomaly frequency — enough variation to avoid sounding mechanical, not enough to risk sounding wrong. The scorer checks whether the candidate text’s anomaly frequency matches the author’s documented frequency, not the genre mean.

**Measurement approach:**

- Establish genre baseline: sentence length distribution, punctuation cadence norms, paragraph rhythm norms for the relevant genre (fiction, memoir, essay)
- Identify anomaly events: text units that fall beyond 1.5 standard deviations from genre baseline
- Calculate anomaly frequency: anomaly events per 1,000 words
- Compare against author’s documented anomaly frequency from private calibration corpus

**Calibration source:** Private soul layer — the full calibration corpus, not the single public paragraph. Anomaly frequency cannot be reliably established from one paragraph.

-----

### Component 2: Anomaly Type Signature

**What it measures:** Not just how often anomalies occur, but what *kind* of anomalies recur. Different writers have different characteristic anomaly types.

Some writers consistently produce over-long sentences when approaching emotionally charged material. Others consistently produce unusually short sentences at moments of resolution. Some writers have a characteristic punctuation anomaly — em-dash overuse, comma splice tolerance, semicolon avoidance. Some have a structural anomaly — paragraphs that end on subordinate clauses, sections that open with fragments.

These anomaly types are more distinctive than frequency alone. They are harder to match because they require knowing not just that anomalies occur but where and what kind.

**Measurement approach:**

Four anomaly type categories, each scored independently:

|Category                 |What It Captures                                                                                                                                 |
|-------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
|**Length anomalies**     |Sentences dramatically longer or shorter than author’s own mean, at characteristic locations (emotional peaks, resolutions, transitions)         |
|**Punctuation anomalies**|Characteristic non-standard punctuation patterns that recur across the author’s work                                                             |
|**Structural anomalies** |Paragraph and section-level rhythm violations that appear consistently (fragments, run-ons, unconventional openings or closings)                 |
|**Density anomalies**    |Passages of unusually high or low semantic density relative to surrounding text — the author’s characteristic rhythm of compression and expansion|

**Calibration source:** Private soul layer — anomaly type signatures require the full archive to establish, not a single calibration paragraph. Anti-examples (passages that passed surface inspection but failed private review) are especially useful for establishing what anomaly types are characteristic versus accidental.

-----

### Component 3: Anomaly Placement Pattern

**What it measures:** Where in the text anomalies occur, relative to content structure. This is the most adversarially robust component because it requires the model to know not just what anomalies look like but when the author deploys them.

**The core observation:** Human writers do not distribute anomalies randomly. They cluster at specific structural and emotional locations — the approach to charged material, the moment of resolution, the pivot between sections, the sentence that carries the most weight. This clustering is not conscious craft in most cases. It is the author’s governing intelligence making decisions that produce a characteristic pattern of when to break the rules.

AI, absent specific instruction, distributes anomalies more uniformly — or places them where anomalies are generically expected (sentence openings, paragraph closings). The characteristic human placement pattern is idiosyncratic to the author and correlates with their emotional and structural priorities, not with generic craft convention.

**Measurement approach:**

- Segment text by structural role: opening, transition, emotional peak, resolution, closing
- Map anomaly events to structural segments
- Compare placement distribution against author’s documented placement pattern from calibration corpus
- Flag text where anomalies are present at the right frequency and type but placed at structurally generic locations rather than author-characteristic locations

**Calibration source:** Private soul layer — placement patterns require multiple works across time to establish reliably. A single work may have idiosyncratic placement due to subject matter. The pattern across works is the signature.

-----

## Scoring Architecture

The rebuilt Rhythm Signature produces a composite score from three components, weighted to reflect adversarial robustness:

|Component                |Weight|Rationale                                                      |
|-------------------------|------|---------------------------------------------------------------|
|Anomaly Frequency        |20%   |Easiest to match; lowest adversarial robustness                |
|Anomaly Type Signature   |35%   |Harder to match; requires knowing characteristic error types   |
|Anomaly Placement Pattern|45%   |Hardest to match; requires knowing when the author breaks rules|

**Score interpretation:**

|Score Range|Interpretation                                                                          |
|-----------|----------------------------------------------------------------------------------------|
|0.8 – 1.0  |Consistent with documented anomaly signature — no flag                                  |
|0.6 – 0.79 |Partial consistency — flag for human review; likely genre drift or extended AI execution|
|0.4 – 0.59 |Low consistency — flag as probable voice drift; recommend private soul review           |
|0.0 – 0.39 |Inconsistent with documented anomaly signature — strong drift signal                    |

**Critical reminder from Voice Stamp v0.1:** The scorer is a first-pass filter, not a certification mechanism. A score of 0.8 does not certify the work as voice-consistent. It certifies that the work does not show obvious anomaly drift and does not require immediate human review. The private soul review remains the only certification layer.

-----

## What This Rebuild Does Not Solve

**The adversarial ceiling problem.** A model specifically trained to pass the anomaly distribution check — given access to the public calibration paragraph plus knowledge of this scorer’s architecture — will eventually learn to produce characteristic anomaly frequencies and types at genre-expected locations. The placement pattern component raises the ceiling significantly, but it does not eliminate it. The soul layer remains the adversarially robust layer.

**The short document problem.** Anomaly frequency and placement patterns require sufficient text to establish statistical reliability. The rebuilt scorer is less reliable on documents under 2,000 words than the mean-cadence approach it replaces. Short documents should be flagged for direct human review rather than scored.

**The voice evolution problem.** The author’s characteristic anomaly signature in 2026 is not identical to 2016 and will not be identical to 2036. The calibration corpus must be updated periodically, and the scorer must be re-calibrated against the updated corpus. The Voice Stamp versioning architecture (continuity attestation model, v0.1.1) handles this at the stamp level; the scorer needs to inherit the same versioning discipline.

**The multi-author problem.** Co-authored works have blended anomaly signatures. The scorer assumes a single governing voice. Multi-author documents should suppress the anomaly placement component, which is the most voice-specific, and rely primarily on anomaly frequency against the primary author’s documented range.

-----

## Relationship to Vocal Voice Preservation

The formant analogy that motivates this rebuild maps onto the rebuilt components as follows:

|Vocal Preservation Concept                                                  |Rhythm Signature Rebuild Analog                                                                               |
|----------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
|Formant frequencies (stable resonant properties independent of content)     |Anomaly type signature (characteristic error types independent of subject matter)                             |
|Formant amplitude (how strongly the formant is expressed)                   |Anomaly frequency (how often characteristic departures occur)                                                 |
|Formant transition patterns (how formants shift across speech events)       |Anomaly placement pattern (where characteristic departures cluster relative to content structure)             |
|Robustness under degradation (formants persist under disease, stress, aging)|Voice Degradation Domain (checks for anomaly signal collapse under collaboration pressure or emotional weight)|

The Voice Degradation Domain extension (negative-space-mapper) and this rebuild are companion instruments. The Degradation Domain flags absence of anomaly signals at the document level. This scorer measures anomaly distribution against the author’s specific signature at the passage level.

-----

## Implementation Notes

**Language:** Python, consistent with existing scorer prototype architecture.

**Dependencies:** The anomaly type and placement components require NLP processing beyond the v0.1 sentence-length entropy approach. Minimum dependencies: `spacy` for syntactic parsing (structural anomaly detection), `numpy` for distribution comparison, existing `anthropic` integration for passages requiring semantic density analysis.

**Calibration data format:** The private soul layer calibration corpus should be structured as:

```json
{
  "author_id": "richard-porter",
  "pvg_version": "1.0",
  "anomaly_frequency": {
    "baseline_per_1000_words": 4.2,
    "standard_deviation": 1.1
  },
  "anomaly_types": {
    "length": ["over-long at emotional approach", "fragment at resolution"],
    "punctuation": ["em-dash mid-clause", "comma splice in dialogue"],
    "structural": ["subordinate clause paragraph ending", "fragment section opening"],
    "density": ["compression before dialogue", "expansion in retrospective passages"]
  },
  "anomaly_placement": {
    "emotional_peak": 0.38,
    "transition": 0.24,
    "resolution": 0.19,
    "opening": 0.11,
    "closing": 0.08
  },
  "calibration_works": ["taller-shell-v1", "taller-shell-v2", "taller-shell-v3"],
  "calibration_date": "2026-03"
}
```

**Scorer output format:** Consistent with existing dimensional fidelity scorer output — per-processor score plus flag/no-flag verdict and passage-level annotations for passages that triggered review.

-----

## Relationship to Existing Ecosystem

|Rebuild Component        |Ecosystem connection                                                                                                |
|-------------------------|--------------------------------------------------------------------------------------------------------------------|
|Anomaly frequency        |Voice Degradation Domain — characteristic anomalies essential                                                       |
|Anomaly type signature   |Permanent Tells Tell 4 (productive incoherence) at metric level                                                     |
|Anomaly placement pattern|Permanent Tells Tell 2 (path-dependence artifacts) — placement reflects governing priorities carried across the work|
|Full composite score     |Voice Stamp v0.1 Appendix A — replaces mean-cadence Rhythm Signature                                                |
|Calibration corpus format|Voice Stamp private soul layer — same data source, different instrument                                             |

-----

## Update Required in Voice Stamp v0.1

Replace the following text in Appendix A, Dimensional Fidelity Scorer, Rhythm Signature entry:

> *“Rhythm Signature — Sentence-length entropy, punctuation cadence, and paragraph rhythm vectors compared against the public calibration paragraph. Flags text with statistically anomalous rhythm relative to the documented signature.”*

With:

> *“Rhythm Signature — Anomaly distribution detection across three components: anomaly frequency, anomaly type signature, and anomaly placement pattern. Measures the author’s characteristic pattern of productive departures from genre norms rather than mean-cadence matching. See `experiments/rhythm-signature-rebuild-v02.md` for full specification. Calibrated against private soul layer corpus, not the public calibration paragraph.”*

And replace the v0.2 development note:

> *“The Rhythm Signature metric in particular should be extended in v0.2 to detect anomaly distribution, not just average cadence. This maps directly onto Tell 4 (productive incoherence) at the metric level — the scorer should look for preserved contradiction, not resolved consistency.”*

With:

> *“The Rhythm Signature rebuild is specified in `experiments/rhythm-signature-rebuild-v02.md`. Implementation pending.”*

-----

## Version History

|Version|Date      |Notes                                                                                                                                                                                                              |
|-------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|0.1    |March 2026|Initial specification. Derived from Voice Stamp v0.1 Appendix A development note and vocal voice preservation formant analogy. Three-component architecture established. Mean-cadence approach formally superseded.|

-----

## Open Questions for v0.2 Implementation

1. **Calibration corpus minimum size:** How many works, and how many words total, are needed to establish a reliable anomaly placement pattern? The frequency and type components can be established from a single long work. The placement component likely requires at least three works across different subject matter to distinguish author-characteristic placement from subject-matter-driven placement.
1. **Genre baseline source:** The anomaly frequency component requires a genre baseline. What corpus establishes the baseline for literary fiction in the marine noir genre? This is a practical implementation question with no obvious off-the-shelf answer.
1. **Semantic density measurement:** The density anomaly type is the least operationalized of the four. Compression and expansion are real phenomena but measuring them reliably from surface features alone is harder than length or punctuation anomalies. The v0.2 implementation should treat density anomalies as lower-confidence than the other three types.
1. **Integration with Taller Shell Challenge:** The Taller Shell Challenge (Voice Stamp v0.1) tests the gap between public scorer pass rate and private soul review pass rate. The rebuilt scorer should be the public instrument in that challenge — it is more adversarially robust than the mean-cadence approach and will produce a more meaningful gap measurement.
1. **Voice evolution across time:** The Taller Shell corpus spans a compressed production period. Does the anomaly type signature change when the authenticated corpus spans years rather than months? Older passages may reflect an earlier voice version — authenticated but not calibrated to the current PVG. The placement component is most vulnerable to this: where the author deploys anomalies relative to emotional content may shift as the author’s relationship to charged material changes.
1. **Temporal variance shape:** The rebuilt scorer measures anomaly distribution per passage — a static snapshot. A companion analysis is needed that graphs register distance from the author’s mean across the full work and examines the shape of the change curve over time. Real human register variance is non-periodic, locally reversing, and correlates with content rather than word count — the graph is jagged with local reversals. Simulated register change produces a step function or smooth sigmoid: a clean before/after transition or a regularly periodic oscillation. This is the written equivalent of scheduled spontaneity — AI mimicking registry change produces systematic variance where human registry change produces organic variance. This temporal variance analysis is a separate instrument from the per-passage scorer and should be specified as a standalone tool in `dimensional-authorship/experiments/`. It is a prerequisite for the Prosodic Envelope as Governance Layer alongside the scorer rebuild and the Minimum Viable Corpus Protocol empirical outputs.

-----

## Version History

|Version|Date      |Notes                                                                                                                                                                                                              |
|-------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|0.1    |March 2026|Initial specification. Derived from Voice Stamp v0.1 Appendix A development note and vocal voice preservation formant analogy. Three-component architecture established. Mean-cadence approach formally superseded.|
|0.1.1  |March 2026|Open question 6 added: temporal variance shape analysis as a companion instrument. Scheduled spontaneity as a simulated registry change signature. Prosodic Envelope prerequisite list updated to three items.     |

-----

*Rhythm Signature Rebuild · v0.1 specification · Dimensional Fidelity Scorer v0.2*  
*Part of the Richard Porter AI Safety ecosystem · Frozen Kernel System*  
*They leave. The knowledge stays.*
