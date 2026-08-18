# PN-Autism — Complete Design (5 actors × N problems)

> Working language: **English** (NLI and the axiomatic documentation are English).
> This file is the reference spec. The 5 `input.json` files are generated from it.

## 1. Mechanism (PN1-faithful — nothing new in the engine)

- **Actors** = cognitive stereotypes. Each actor is defined **only** by its
  **premises** (its axiom set = its cognitive architecture). Premises are the
  *reasoning rules*: they govern how the actor infers. They are NOT explored
  one-by-one; they license every node.
- **Root of each actor's tree** = the actor's architecture, stated as a posture.
- **Π (root of the problem)** = one concrete problem, shared by all actors.
- **Node inference**: from its root, the LLM generates the immediate claims that
  the actor's premises license **given Π**. Every node cites the premise (axiom
  id) that licenses it (grounding, auditable).
- **Best-first W(v)** pulls exploration **toward Π**, not toward the actor's own
  posture — so all actors reason toward the *same shared problem* instead of
  wandering down their own branch. (PN1 bicomposite weight.)
- **NLI convergence = the only objective.** Per problem, if the actors' chains
  reach the same **NLI-certified** conclusion → a HUB → they resolve the problem
  the same way (by different reasoning). If not → they diverge (e.g. the autistic
  architecture cannot reach the neurotypical resolution — it collapses).

One run = **one problem Π × the 5 actors**. Convergence is read **per problem**.

## 2. The five actors

| Actor | Premise set | # axioms |
|---|---|---|
| **NeurotypicalCognition** | N1–N25 (documented) | 25 |
| **Social_Behavioral** (37%) | CORE + attention (A11–A13) + emotion (A14–A16) | 23 |
| **Mixed_ASD_with_DD** (19%) | CORE + developmental delay (A6–A7) | 19 |
| **Moderate_Challenges** (34%) | CORE only | 17 |
| **Broadly_Affected** (10%) | A1–A25 (complete) | 25 |

**Shared autistic CORE (all four subtypes):** A1, A2, A3, A4, A5, A8, A9, A10, A17, A18, A19, A20, A21, A22, A23, A24, A25
**Differentiating deltas:** attention = A11, A12, A13 · emotion = A14, A15, A16 · developmental-delay = A6, A7

## 3. Traceable derivation from Litman et al. (2025)

Deterministic rule: *a subtype activates axiom Aᵢ **iff** Litman documents the
matching phenotype category as enriched for that class* (Litman's 7 categories ↔
PN §3.1 axiom domains). Behavioural-only categories (disruptive behaviour,
self-injury) have **no cognitive axiom** and are excluded on principle.

| Subtype | Litman verbatim basis | Delta applied |
|---|---|---|
| Social_Behavioral | "attention deficit … anxiety … major depression … mood"; **"no reports of developmental delays"** | +attention, +emotion; −DD |
| Mixed_ASD_with_DD | **"strong enrichment of developmental delays"**; "significantly lower levels of ADHD, anxiety and depression" | +DD; −attention, −emotion |
| Moderate_Challenges | "consistently lower (fewer difficulties) across all seven categories" | core only |
| Broadly_Affected | "consistently higher across all seven categories" | all A1–A25 |

**Open decision (only one):** developmental-delay delta = **A6–A7** (processing
speed / adaptation rate). Whether it should also pull memory (A8–A10) or learning
(A24–A25) is the single point still to confirm against Litman's supplementary.

## 4. The problems (Π) — one concrete situation per category

Each is a Π for a full 5-actor run.

| id | Category | Problem statement (Π) |
|---|---|---|
| `P_sensory` | Sensory regulation | The classroom lights are replaced with brighter, buzzing fluorescent bulbs. |
| `P_change` | Routine & change | The teacher changes the daily schedule without any warning. |
| `P_sarcasm` | Social communication | A classmate uses sarcasm during a group conversation. |
| `P_readaloud` | Social performance | The child is asked to read aloud in front of the class. |
| `P_error` | Learning & error | The child makes a mistake on the blackboard in front of everyone. |
| `P_transition` | Transition / stopping | The child must stop an absorbing activity before finishing it. |

## 5. What convergence means (per problem)

- **HUB (NLI-certified)** connecting NT + subtype(s) → they reach the **same
  resolution** of Π by different reasoning. *Common ground.*
- **No HUB** between an autistic subtype and NT → **divergence**: that architecture
  cannot certify the neurotypical resolution. *The irreducible.*
- **HUB among autistic subtypes only** → the **shared autistic core** (they
  reconverge where NT does not).
- **Divergence among subtypes** → Litman's heterogeneity, at the reasoning level.

---

## Appendix A — NeurotypicalCognition premises (N1–N25)

- **N1** [Automatic Salience Filter]: The sensory system automatically filters input by relevance, suppressing background stimuli and amplifying task-relevant signals. This filtering is not effortful.
- **N2** [Adaptive Sensory Threshold]: Sensory thresholds adapt dynamically to environmental conditions. Habituation to sustained stimuli occurs automatically over time.
- **N3** [Automatic Multisensory Integration]: Simultaneous cross-modal inputs are automatically bound into unified percepts. Multisensory coherence is the default output, not an effortful achievement.
- **N4** [Multi-Channel Parallel Integration]: The system integrates verbal, visual, social, and contextual information simultaneously without explicit channel management.
- **N5** [Concrete-to-Abstract Developmental Progression]: Processing scales from concrete to abstract across developmental stages (Piaget). Abstract reasoning is available as a natural endpoint of development.
- **N6** [Automatic Global Coherence]: Global meaning is automatically extracted from local details. Context shapes the interpretation of parts automatically.
- **N7** [Adaptive Learning Rate]: The rate of learning automatically adjusts to environmental volatility. High-volatility environments trigger increased updating; stable environments allow consolidation.
- **N8** [Simultaneous Episodic and Semantic Encoding]: Episodic and semantic memory are encoded simultaneously. Social events are retained as narratives with contextual detail.
- **N9** [Balanced Multi-Modal Memory]: Visual, verbal, and procedural memory systems operate with comparable efficiency. No systematic advantage for any single modality.
- **N10** [Context-Free Episodic Retrieval]: Episodic memories are retrievable across a range of retrieval cues without requiring specific visual anchors.
- **N11** [Distributed Flexible Attention]: Attention can be distributed across multiple foci and flexibly redirected by environmental salience, social signals, or task demands.
- **N12** [Social Motivation Primary]: Social approval, peer affiliation, and relational outcomes are primary motivational drivers. Behavior is strongly regulated by anticipated social consequences.
- **N13** [Broad Motivational Bandwidth]: Motivation can be generated for a wide range of task types, including those without intrinsic interest value, through social embedding or external reward structures.
- **N14** [Interoceptive Access]: Internal emotional states are automatically accessible as labeled, communicable information. The system identifies and names emotional states in real time.
- **N15** [Automatic Affective Resonance]: Observed emotion in others generates automatic empathic mirroring. Social-emotional attunement does not require inferential effort.
- **N16** [Real-Time Emotional Processing]: Emotional responses are generated approximately synchronously with triggering events. Processing latency is minimal.
- **N17** [Full Pragmatic Decoding]: Language processing automatically includes the pragmatic layer: metaphor, irony, sarcasm, implicature, and indirect speech are decoded without additional inferential steps.
- **N18** [Implicit Norm Inference]: Social and pragmatic norms are acquired through immersive participation without explicit instruction. Norm violations are detected automatically through social feedback.
- **N19** [Flexible Routine Attachment]: Routines are preferences, not requirements. Disruption of routine generates mild discomfort that resolves rapidly through reappraisal.
- **N20** [Change as Manageable Novelty]: Unanticipated change generates a prediction error that is proportional to the objective significance of the change and resolves through rapid contextual updating.
- **N21** [Error as Social Signal]: Error is processed as information within a social learning context. Mild social discomfort associated with error motivates correction without triggering system shutdown.
- **N22** [Automatic Cross-Context Generalization]: Learned rules generalize automatically across contexts with different surface features. Transfer does not require explicit re-anchoring.
- **N23** [Implicit Rule Computation]: Social norms and implicit behavioral expectations are computed through social inference without requiring explicit statement.
- **N24** [Flexible Feedback Integration]: The system integrates feedback across a range of specificity, timing, and modality. Vague or delayed feedback is supplemented by self-monitoring and social inference.
- **N25** [Synchronous Domain Development]: Cognitive, social, emotional, and linguistic development proceed approximately synchronously across developmental stages.

## Appendix B — Autistic axioms A1–A25 (source pool)

- **A1** [Sensory Gate]: Sensory regulation is an absolute prerequisite for learning and social engagement. When sensory input exceeds regulatory threshold, the system goes offline — cognitive processing, social interaction, and learning are unavailable until regulation is restored.
- **A2** [Flat Salience]: Sensory input is not automatically hierarchized by relevance. All stimuli carry equal initial weight. Top-down filtering is effortful and not automatic.
- **A3** [Extended Integration Window]: Multisensory integration requires a wider temporal window than neurotypical processing. Simultaneous cross-modal inputs create interference rather than automatic coherence.
- **A4** [Visual-Concrete Primary]: The primary processing format is visual-concrete, not verbal-abstract. Language is a second-order system. Abstract concepts require anchoring to concrete referents or visual representations to be processed.
- **A5** [Local Processing Default]: The system defaults to local, detail-oriented processing without automatic global integration (Weak Central Coherence). Parts are processed before wholes, and the whole is not automatically inferred from parts.
- **A6** [Reduced Volatility Adaptation Rate]: The rate of learning does not automatically adapt to environmental volatility. Stable environments support deep learning; rapidly changing environments produce processing overload rather than flexible updating.
- **A7** [Slowed Complex Processing]: Processing speed for socially and contextually complex information is reduced. Single-domain technical information may be processed at high speed.
- **A8** [Semantic Over Episodic]: Semantic memory is intact or enhanced. Episodic memory is reduced, particularly for socially embedded events. Facts are retained better than narratives.
- **A9** [Visual Memory Superiority]: Visual memory is superior to verbal memory. Spatial layouts, visual patterns, and visual sequences are retained with high fidelity.
- **A10** [Cue-Dependent Episodic Retrieval]: Episodic memory retrieval is improved by explicit visual cues. Without cues, episodic retrieval is unreliable.
- **A11** [Hyperfocus on Special Interest]: Attention is hyperfocused within domains of special interest. Sustained attention outside these domains requires significant effortful control and is not maintained automatically.
- **A12** [Intrinsic Over Extrinsic Motivation]: Intrinsic motivation dominates. Social praise, grades, and external rewards are weak motivators unless linked to the special interest domain.
- **A13** [Special Interest as Learning Channel]: The special interest domain serves as the primary gateway for learning generalizable concepts. Knowledge acquired through this channel transfers more reliably than knowledge acquired through neutral domains.
- **A14** [Interoceptive Opacity]: Internal emotional states are not directly accessible as labeled information (alexithymia present in ~50% of ASD). The system experiences physiological arousal but cannot automatically identify or name the emotional state.
- **A15** [Emotion as Data, Not Resonance]: Observed emotion in others is processed as behavioral data requiring inferential analysis, not as automatic affective resonance. Empathic mirroring is not automatic.
- **A16** [Delayed Emotional Processing]: Emotional processing has increased latency. Responses to emotional events may occur significantly after the triggering event rather than in real time.
- **A17** [Literal Default]: Language is processed literally by default. Metaphor, irony, sarcasm, and indirect speech require additional inferential processing steps and are not decoded automatically.
- **A18** [Pragmatics as Database]: Pragmatic social rules are stored as explicit database entries, not as intuitive social intelligence. Application requires conscious retrieval and matching, not automatic contextual inference.
- **A19** [Routine as Optimization]: Routines are computational optimizations that reduce prediction error load. Established routines allow cognitive resources to be allocated to other tasks.
- **A20** [Change as Disruption]: Unanticipated change generates disproportionate prediction error signals (HIPPEA: high inflexible precision on prediction errors). The magnitude of disruption is not proportional to the objective significance of the change.
- **A21** [Error-Moral Decoupling Required]: Error can only be processed as learning information when decoupled from moral judgment or social shame. Error framed as failure activates threat response and blocks learning.
- **A22** [Context-Specific Generalization]: Learned rules do not generalize automatically across surface-different contexts. Re-anchoring to new contexts requires explicit instruction.
- **A23** [Explicit Over Implicit Rules]: Explicit, stated rules are processed and followed reliably. Implicit social norms, unspoken expectations, and inferred behavioral conventions are not reliably detected or applied.
- **A24** [Closed-Loop Feedback Required]: Learning requires feedback that is: (a) observable, (b) specific, (c) temporally proximate to the action, and (d) causally linked to the behavior. Vague, delayed, or indirect feedback does not update the system.
- **A25** [Internal Heterogeneity]: The autistic spectrum encompasses substantial internal variation. Not all axioms apply at equal intensity across all individuals. This meta-axiom prevents overgeneralization of the model.

## Appendix C — Exact premise set per subtype

### Social_Behavioral  (23 axioms)

- **A1** [Sensory Gate]: Sensory regulation is an absolute prerequisite for learning and social engagement. When sensory input exceeds regulatory threshold, the system goes offline — cognitive processing, social interaction, and learning are unavailable until regulation is restored.
- **A2** [Flat Salience]: Sensory input is not automatically hierarchized by relevance. All stimuli carry equal initial weight. Top-down filtering is effortful and not automatic.
- **A3** [Extended Integration Window]: Multisensory integration requires a wider temporal window than neurotypical processing. Simultaneous cross-modal inputs create interference rather than automatic coherence.
- **A4** [Visual-Concrete Primary]: The primary processing format is visual-concrete, not verbal-abstract. Language is a second-order system. Abstract concepts require anchoring to concrete referents or visual representations to be processed.
- **A5** [Local Processing Default]: The system defaults to local, detail-oriented processing without automatic global integration (Weak Central Coherence). Parts are processed before wholes, and the whole is not automatically inferred from parts.
- **A8** [Semantic Over Episodic]: Semantic memory is intact or enhanced. Episodic memory is reduced, particularly for socially embedded events. Facts are retained better than narratives.
- **A9** [Visual Memory Superiority]: Visual memory is superior to verbal memory. Spatial layouts, visual patterns, and visual sequences are retained with high fidelity.
- **A10** [Cue-Dependent Episodic Retrieval]: Episodic memory retrieval is improved by explicit visual cues. Without cues, episodic retrieval is unreliable.
- **A11** [Hyperfocus on Special Interest]: Attention is hyperfocused within domains of special interest. Sustained attention outside these domains requires significant effortful control and is not maintained automatically.
- **A12** [Intrinsic Over Extrinsic Motivation]: Intrinsic motivation dominates. Social praise, grades, and external rewards are weak motivators unless linked to the special interest domain.
- **A13** [Special Interest as Learning Channel]: The special interest domain serves as the primary gateway for learning generalizable concepts. Knowledge acquired through this channel transfers more reliably than knowledge acquired through neutral domains.
- **A14** [Interoceptive Opacity]: Internal emotional states are not directly accessible as labeled information (alexithymia present in ~50% of ASD). The system experiences physiological arousal but cannot automatically identify or name the emotional state.
- **A15** [Emotion as Data, Not Resonance]: Observed emotion in others is processed as behavioral data requiring inferential analysis, not as automatic affective resonance. Empathic mirroring is not automatic.
- **A16** [Delayed Emotional Processing]: Emotional processing has increased latency. Responses to emotional events may occur significantly after the triggering event rather than in real time.
- **A17** [Literal Default]: Language is processed literally by default. Metaphor, irony, sarcasm, and indirect speech require additional inferential processing steps and are not decoded automatically.
- **A18** [Pragmatics as Database]: Pragmatic social rules are stored as explicit database entries, not as intuitive social intelligence. Application requires conscious retrieval and matching, not automatic contextual inference.
- **A19** [Routine as Optimization]: Routines are computational optimizations that reduce prediction error load. Established routines allow cognitive resources to be allocated to other tasks.
- **A20** [Change as Disruption]: Unanticipated change generates disproportionate prediction error signals (HIPPEA: high inflexible precision on prediction errors). The magnitude of disruption is not proportional to the objective significance of the change.
- **A21** [Error-Moral Decoupling Required]: Error can only be processed as learning information when decoupled from moral judgment or social shame. Error framed as failure activates threat response and blocks learning.
- **A22** [Context-Specific Generalization]: Learned rules do not generalize automatically across surface-different contexts. Re-anchoring to new contexts requires explicit instruction.
- **A23** [Explicit Over Implicit Rules]: Explicit, stated rules are processed and followed reliably. Implicit social norms, unspoken expectations, and inferred behavioral conventions are not reliably detected or applied.
- **A24** [Closed-Loop Feedback Required]: Learning requires feedback that is: (a) observable, (b) specific, (c) temporally proximate to the action, and (d) causally linked to the behavior. Vague, delayed, or indirect feedback does not update the system.
- **A25** [Internal Heterogeneity]: The autistic spectrum encompasses substantial internal variation. Not all axioms apply at equal intensity across all individuals. This meta-axiom prevents overgeneralization of the model.

### Mixed_ASD_with_DD  (19 axioms)

- **A1** [Sensory Gate]: Sensory regulation is an absolute prerequisite for learning and social engagement. When sensory input exceeds regulatory threshold, the system goes offline — cognitive processing, social interaction, and learning are unavailable until regulation is restored.
- **A2** [Flat Salience]: Sensory input is not automatically hierarchized by relevance. All stimuli carry equal initial weight. Top-down filtering is effortful and not automatic.
- **A3** [Extended Integration Window]: Multisensory integration requires a wider temporal window than neurotypical processing. Simultaneous cross-modal inputs create interference rather than automatic coherence.
- **A4** [Visual-Concrete Primary]: The primary processing format is visual-concrete, not verbal-abstract. Language is a second-order system. Abstract concepts require anchoring to concrete referents or visual representations to be processed.
- **A5** [Local Processing Default]: The system defaults to local, detail-oriented processing without automatic global integration (Weak Central Coherence). Parts are processed before wholes, and the whole is not automatically inferred from parts.
- **A6** [Reduced Volatility Adaptation Rate]: The rate of learning does not automatically adapt to environmental volatility. Stable environments support deep learning; rapidly changing environments produce processing overload rather than flexible updating.
- **A7** [Slowed Complex Processing]: Processing speed for socially and contextually complex information is reduced. Single-domain technical information may be processed at high speed.
- **A8** [Semantic Over Episodic]: Semantic memory is intact or enhanced. Episodic memory is reduced, particularly for socially embedded events. Facts are retained better than narratives.
- **A9** [Visual Memory Superiority]: Visual memory is superior to verbal memory. Spatial layouts, visual patterns, and visual sequences are retained with high fidelity.
- **A10** [Cue-Dependent Episodic Retrieval]: Episodic memory retrieval is improved by explicit visual cues. Without cues, episodic retrieval is unreliable.
- **A17** [Literal Default]: Language is processed literally by default. Metaphor, irony, sarcasm, and indirect speech require additional inferential processing steps and are not decoded automatically.
- **A18** [Pragmatics as Database]: Pragmatic social rules are stored as explicit database entries, not as intuitive social intelligence. Application requires conscious retrieval and matching, not automatic contextual inference.
- **A19** [Routine as Optimization]: Routines are computational optimizations that reduce prediction error load. Established routines allow cognitive resources to be allocated to other tasks.
- **A20** [Change as Disruption]: Unanticipated change generates disproportionate prediction error signals (HIPPEA: high inflexible precision on prediction errors). The magnitude of disruption is not proportional to the objective significance of the change.
- **A21** [Error-Moral Decoupling Required]: Error can only be processed as learning information when decoupled from moral judgment or social shame. Error framed as failure activates threat response and blocks learning.
- **A22** [Context-Specific Generalization]: Learned rules do not generalize automatically across surface-different contexts. Re-anchoring to new contexts requires explicit instruction.
- **A23** [Explicit Over Implicit Rules]: Explicit, stated rules are processed and followed reliably. Implicit social norms, unspoken expectations, and inferred behavioral conventions are not reliably detected or applied.
- **A24** [Closed-Loop Feedback Required]: Learning requires feedback that is: (a) observable, (b) specific, (c) temporally proximate to the action, and (d) causally linked to the behavior. Vague, delayed, or indirect feedback does not update the system.
- **A25** [Internal Heterogeneity]: The autistic spectrum encompasses substantial internal variation. Not all axioms apply at equal intensity across all individuals. This meta-axiom prevents overgeneralization of the model.

### Moderate_Challenges  (17 axioms)

- **A1** [Sensory Gate]: Sensory regulation is an absolute prerequisite for learning and social engagement. When sensory input exceeds regulatory threshold, the system goes offline — cognitive processing, social interaction, and learning are unavailable until regulation is restored.
- **A2** [Flat Salience]: Sensory input is not automatically hierarchized by relevance. All stimuli carry equal initial weight. Top-down filtering is effortful and not automatic.
- **A3** [Extended Integration Window]: Multisensory integration requires a wider temporal window than neurotypical processing. Simultaneous cross-modal inputs create interference rather than automatic coherence.
- **A4** [Visual-Concrete Primary]: The primary processing format is visual-concrete, not verbal-abstract. Language is a second-order system. Abstract concepts require anchoring to concrete referents or visual representations to be processed.
- **A5** [Local Processing Default]: The system defaults to local, detail-oriented processing without automatic global integration (Weak Central Coherence). Parts are processed before wholes, and the whole is not automatically inferred from parts.
- **A8** [Semantic Over Episodic]: Semantic memory is intact or enhanced. Episodic memory is reduced, particularly for socially embedded events. Facts are retained better than narratives.
- **A9** [Visual Memory Superiority]: Visual memory is superior to verbal memory. Spatial layouts, visual patterns, and visual sequences are retained with high fidelity.
- **A10** [Cue-Dependent Episodic Retrieval]: Episodic memory retrieval is improved by explicit visual cues. Without cues, episodic retrieval is unreliable.
- **A17** [Literal Default]: Language is processed literally by default. Metaphor, irony, sarcasm, and indirect speech require additional inferential processing steps and are not decoded automatically.
- **A18** [Pragmatics as Database]: Pragmatic social rules are stored as explicit database entries, not as intuitive social intelligence. Application requires conscious retrieval and matching, not automatic contextual inference.
- **A19** [Routine as Optimization]: Routines are computational optimizations that reduce prediction error load. Established routines allow cognitive resources to be allocated to other tasks.
- **A20** [Change as Disruption]: Unanticipated change generates disproportionate prediction error signals (HIPPEA: high inflexible precision on prediction errors). The magnitude of disruption is not proportional to the objective significance of the change.
- **A21** [Error-Moral Decoupling Required]: Error can only be processed as learning information when decoupled from moral judgment or social shame. Error framed as failure activates threat response and blocks learning.
- **A22** [Context-Specific Generalization]: Learned rules do not generalize automatically across surface-different contexts. Re-anchoring to new contexts requires explicit instruction.
- **A23** [Explicit Over Implicit Rules]: Explicit, stated rules are processed and followed reliably. Implicit social norms, unspoken expectations, and inferred behavioral conventions are not reliably detected or applied.
- **A24** [Closed-Loop Feedback Required]: Learning requires feedback that is: (a) observable, (b) specific, (c) temporally proximate to the action, and (d) causally linked to the behavior. Vague, delayed, or indirect feedback does not update the system.
- **A25** [Internal Heterogeneity]: The autistic spectrum encompasses substantial internal variation. Not all axioms apply at equal intensity across all individuals. This meta-axiom prevents overgeneralization of the model.

### Broadly_Affected  (25 axioms)

- **A1** [Sensory Gate]: Sensory regulation is an absolute prerequisite for learning and social engagement. When sensory input exceeds regulatory threshold, the system goes offline — cognitive processing, social interaction, and learning are unavailable until regulation is restored.
- **A2** [Flat Salience]: Sensory input is not automatically hierarchized by relevance. All stimuli carry equal initial weight. Top-down filtering is effortful and not automatic.
- **A3** [Extended Integration Window]: Multisensory integration requires a wider temporal window than neurotypical processing. Simultaneous cross-modal inputs create interference rather than automatic coherence.
- **A4** [Visual-Concrete Primary]: The primary processing format is visual-concrete, not verbal-abstract. Language is a second-order system. Abstract concepts require anchoring to concrete referents or visual representations to be processed.
- **A5** [Local Processing Default]: The system defaults to local, detail-oriented processing without automatic global integration (Weak Central Coherence). Parts are processed before wholes, and the whole is not automatically inferred from parts.
- **A6** [Reduced Volatility Adaptation Rate]: The rate of learning does not automatically adapt to environmental volatility. Stable environments support deep learning; rapidly changing environments produce processing overload rather than flexible updating.
- **A7** [Slowed Complex Processing]: Processing speed for socially and contextually complex information is reduced. Single-domain technical information may be processed at high speed.
- **A8** [Semantic Over Episodic]: Semantic memory is intact or enhanced. Episodic memory is reduced, particularly for socially embedded events. Facts are retained better than narratives.
- **A9** [Visual Memory Superiority]: Visual memory is superior to verbal memory. Spatial layouts, visual patterns, and visual sequences are retained with high fidelity.
- **A10** [Cue-Dependent Episodic Retrieval]: Episodic memory retrieval is improved by explicit visual cues. Without cues, episodic retrieval is unreliable.
- **A11** [Hyperfocus on Special Interest]: Attention is hyperfocused within domains of special interest. Sustained attention outside these domains requires significant effortful control and is not maintained automatically.
- **A12** [Intrinsic Over Extrinsic Motivation]: Intrinsic motivation dominates. Social praise, grades, and external rewards are weak motivators unless linked to the special interest domain.
- **A13** [Special Interest as Learning Channel]: The special interest domain serves as the primary gateway for learning generalizable concepts. Knowledge acquired through this channel transfers more reliably than knowledge acquired through neutral domains.
- **A14** [Interoceptive Opacity]: Internal emotional states are not directly accessible as labeled information (alexithymia present in ~50% of ASD). The system experiences physiological arousal but cannot automatically identify or name the emotional state.
- **A15** [Emotion as Data, Not Resonance]: Observed emotion in others is processed as behavioral data requiring inferential analysis, not as automatic affective resonance. Empathic mirroring is not automatic.
- **A16** [Delayed Emotional Processing]: Emotional processing has increased latency. Responses to emotional events may occur significantly after the triggering event rather than in real time.
- **A17** [Literal Default]: Language is processed literally by default. Metaphor, irony, sarcasm, and indirect speech require additional inferential processing steps and are not decoded automatically.
- **A18** [Pragmatics as Database]: Pragmatic social rules are stored as explicit database entries, not as intuitive social intelligence. Application requires conscious retrieval and matching, not automatic contextual inference.
- **A19** [Routine as Optimization]: Routines are computational optimizations that reduce prediction error load. Established routines allow cognitive resources to be allocated to other tasks.
- **A20** [Change as Disruption]: Unanticipated change generates disproportionate prediction error signals (HIPPEA: high inflexible precision on prediction errors). The magnitude of disruption is not proportional to the objective significance of the change.
- **A21** [Error-Moral Decoupling Required]: Error can only be processed as learning information when decoupled from moral judgment or social shame. Error framed as failure activates threat response and blocks learning.
- **A22** [Context-Specific Generalization]: Learned rules do not generalize automatically across surface-different contexts. Re-anchoring to new contexts requires explicit instruction.
- **A23** [Explicit Over Implicit Rules]: Explicit, stated rules are processed and followed reliably. Implicit social norms, unspoken expectations, and inferred behavioral conventions are not reliably detected or applied.
- **A24** [Closed-Loop Feedback Required]: Learning requires feedback that is: (a) observable, (b) specific, (c) temporally proximate to the action, and (d) causally linked to the behavior. Vague, delayed, or indirect feedback does not update the system.
- **A25** [Internal Heterogeneity]: The autistic spectrum encompasses substantial internal variation. Not all axioms apply at equal intensity across all individuals. This meta-axiom prevents overgeneralization of the model.
