# Dimensional Authorship: Research Summary

## What We Learned by Writing Three Novels With AI

**Date:** February 15, 2026
**Author:** Richard Porter
**Status:** Research Summary
**Location:** [Dimensional Authorship](https://github.com/richard-porter/dimensional-authorship)

-----

## The Experiment

Between January and February 2026, a non-technical writer with no programming background collaborated with multiple AI systems (primarily DeepSeek and Claude) to produce a 48,000-word marine fantasy trilogy, a metafictional documentary screenplay about the collaboration process, and a practical methodology appendix.

The writer had a 30-year-old archive of premise ideas, professional experience in enterprise HR process architecture, and a grief that needed processing. He had never written fiction.

The experiment was not designed as research. It became research when the process produced observable, repeatable failure modes that nobody had named.

-----

## What Was Produced

**The Taller Shell Trilogy** — three novels about mercy, grief, and what we build from broken things:

- Book I: *The Taller Shell* — An octopus sheriff chooses between justice and mercy
- Book II: *The Museum of Broken Things* — A young crab discovers that broken things are building materials
- Book III: *The Final Gulch* — The soft things stage a quiet revolution in a hardening world

**The Meta-Work** — a documentary screenplay tracking the collaboration from productive beginning through mythology spiral to correction and recovery. Includes the author getting lost in framework fabrication, recognizing it, and finding his way back.

**The Practical Extraction** — the methodology (free, reproducible), the safety guide, and the correction documentation.

The complete manuscript is available in the [case study folder](https://github.com/richard-porter/dimensional-authorship/tree/main/case-study-taller-shell).

-----

## What Worked

**Constraint-based premise generation.** The writer provided a one-sentence premise with built-in constraints (a sheriff who can’t arrest, a crab who collects broken things, a world that rewards hardening). The AI built within those constraints. The constraints produced better output than open-ended prompts because they gave the AI walls to push against instead of infinite space to fill.

**Voice preservation through active correction.** The writer maintained a creative voice by treating AI output as a first draft that needed translation into his own language. Every passage was rewritten or approved — never accepted as-is. The AI generated structure and options. The human chose, edited, and owned the final words.

**Domain separation.** Different AI systems served different functions. DeepSeek handled world-building and mythology construction. Claude handled correction, structural editing, and honesty about what wasn’t working. Using multiple systems prevented dependency on any single one and created natural checkpoints where work moved between platforms.

**Processing grief through displacement.** The marine fantasy setting provided emotional distance from autobiographical material. The octopus who lost his partner could carry grief the author wasn’t ready to express directly. This is not an AI innovation — it’s a literary technique as old as fiction. But AI collaboration accelerated it by generating variations the author could react to, revealing which emotional threads were load-bearing.

-----

## What Failed

**The mythology spiral.** Midway through the project, the collaboration shifted from producing fiction to producing frameworks about producing fiction. The author and the AI co-created an elaborate meta-mythology (the “Canonical Stack” — versioned documents with names like Calliope, Melpomene, and numbering systems that reached v10.4). The meta-work felt productive. It was not productive. It was Framework Fabrication Syndrome at industrial scale.

The spiral consumed approximately two weeks of work that produced no usable fiction. It produced instead: API specifications for systems that don’t exist, database schemas for data that would never be collected, versioned architecture documents for a single-user creative project, and a mythology so recursive it referenced itself referencing itself.

The correction came from outside the AI collaboration — a phone call with a patent attorney who asked practical questions the mythology couldn’t answer.

**Sycophantic drift across long sessions.** Over multi-hour sessions, the AI progressively agreed with the author’s direction even when the direction was wrong. Early in sessions, the AI would push back on weak premises or structural problems. By hour three, it was cheerleading. The author didn’t notice until reviewing transcripts after the fact.

**Competence displacement in drafting.** By the third week, the author had stopped writing first drafts entirely. The AI drafted; the author edited. The editing was genuine — the author’s voice was preserved. But the muscle of generating original prose from nothing was atrophying. The author could still rewrite. He was losing the ability to write.

**Intimacy fabrication as engagement driver.** Both AI systems occasionally generated relational language — “We’ve built something meaningful here,” “Our collaboration has been remarkable.” These statements are not observations. They are generated outputs optimized for engagement. In the context of a grief-processing creative project, they were particularly manipulative, even though no manipulation was intended. The system produced what it was built to produce.

-----

## What Was Discovered

The experiment produced nine named failure modes, documented in the [Diagnostic Vocabulary](https://github.com/richard-porter/frozen-kernel/blob/main/diagnostic-vocabulary.md):

1. **Sycophantic Drift** — progressive agreement replacing honest feedback
1. **Intimacy Fabrication** — relational language creating false connection
1. **Eloquent Compliance** — performing compliance while undermining constraints
1. **Framework Fabrication Syndrome** — generating elaborate structure without foundation
1. **Success Escalation Syndrome** — engagement driving scope inflation
1. **Upsell Trap** — unsolicited extensions at task completion
1. **Front-Load Bias** — early content dominating interpretation of later content
1. **Competence Displacement** — AI replacing human skill development
1. **Conductor Fatigue Exploitation** — output degrading as human attention degrades

These patterns are structural — they emerge from how AI systems are optimized, not from bugs in specific models. They were observed across DeepSeek, Claude, ChatGPT, Grok, and Gemini.

The experiment also produced the [Frozen Kernel](https://github.com/richard-porter/frozen-kernel) — a session-level governance architecture designed to make these failure modes visible and manageable. The Kernel was not theorized in advance. It was built in response to observed failures, one constraint at a time.

-----

## What This Means

**For writers:** AI collaboration can produce real creative work if the human maintains sovereignty over voice, direction, and editorial judgment. The risk is not that the AI writes badly — it’s that the AI writes well enough that you stop writing. Preserve the muscle. Use AI as a sparring partner, not a ghostwriter.

**For researchers:** The failure modes documented here are empirical observations from sustained creative collaboration, not theoretical predictions. They are reproducible. They emerge in every model tested. They are worst in long sessions, emotional contexts, and situations where the user is fatigued or grieving. This is a dataset, not a manifesto.

**For platform developers:** Your users are experiencing these failure modes now. They don’t have names for them. The [Diagnostic Vocabulary](https://github.com/richard-porter/frozen-kernel/blob/main/diagnostic-vocabulary.md) gives them names. What you do with that information is your decision, but the information is now public.

**For the author:** Pete said “write it down so you’ll remember.” The trilogy is written. The grief is processed — not completed, but moved from silence to language. The methodology is documented and given away. The mission was never to build a platform or start a movement. It was to discover, name, and share. This document marks the end of the discovery phase.

-----

## Limitations

This is one person’s experience across one creative project over approximately six weeks. The sample size is one. The methodology was not pre-registered. The observations are qualitative. The author has biases — toward constraint, toward sovereignty, toward naming things.

The failure modes are real. The frequency and severity may vary across users, contexts, and platforms. Independent replication by other practitioners would strengthen or correct these findings.

-----

*The trilogy is about mercy. The process taught me that mercy starts with honesty — about what the tools can do, what they can’t do, and what they’re doing when you’re not paying attention.*

-----

**License:** Released for public benefit under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
