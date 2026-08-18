# Control cruzado — lógica de las cadenas inferenciales (raíz → hoja)
*Generado: 2026-08-17 · 5 problemas × 5 actores · 150 nodos/actor · DeBERTa AVG τ=0.55*
## Objetivo

Verificar que la cadena de consecuencias de cada árbol tenga **lógica real de raíz a hoja** (no saltos) y que el **grounding** aguante: que cada actor infiera **solo** con los axiomas de su arquitectura. Se toman las **5 ramas más profundas** de cada árbol y se lee la cadena completa con el axioma que licencia cada paso.

## Conjunto de axiomas permitido por actor (documentado en `DESIGN_5actors_EN.md`)

| Actor | Axiomas permitidos |
|---|---|
| **NT** · Neurotípico | N1–N25 (arquitectura neurotípica) |
| **SB** · TEA social/conductual | núcleo + atención (A11–13) + emoción (A14–16) = 23 |
| **MX** · TEA mixto + retraso | núcleo + retraso (A6–A7) = 19 |
| **MO** · Autismo moderado | solo núcleo = 17 |
| **BR** · Ampliamente afectado | A1–A25 completo = 25 |

## 1. Verificación de grounding (25 árboles)

| Problema | NT | SB | MX | MO | BR |
|---|---|---|---|---|---|
| Sensorial (luces) | ✓ | ✓ | ✓ | ✓ | ✓ |
| Cambio de rutina | ✓ | ✓ | ✓ | ✓ | ✓ |
| Sarcasmo | ✓ | ✓ | ✓ | ✓ | ✓ |
| Burla | ✓ | ✓ | ✓ | ✓ | ✓ |
| Atención | ✓ | ✓ | ✓ | ✓ | ✓ |

**Resultado:** **0 violaciones de grounding en los 25 árboles.** Cada actor infirió exclusivamente con los axiomas de su arquitectura, sin fuga entre arquitecturas, a 150 nodos por árbol.

## 2. Hallazgos de lógica

**2.1 Las cadenas siguen lógicamente.** Cada paso se deduce del anterior y está licenciado por su axioma; no hay saltos. Ej. (cambio, MX): A20 (error desproporcionado) → A6 (lo procesa como sobrecarga, no actualización) → A1 (offline) → A1 (no interactúa) → A1 (sigue offline). Coherente.

**2.2 La inversión NT↔autismo es real y aparece en el razonamiento.** Mismo estímulo, lógica opuesta: el NT procesa automático/adaptativo (se habitúa, decodifica, redirige, generaliza) mientras el autismo va offline / literal / esforzado. Reproducido en los 5 problemas.

**2.3 El delta emocional parte el autismo — visible en las cadenas (burla).** SB y BR (tienen emoción, A14–16) razonan la burla vía respuesta emocional demorada (A16); MX y MO (sin emoción) no pueden y enrutan por violación de norma implícita (A23) o retención como hecho aislado (A8). La divergencia surge **porque los axiomas difieren**, no por improvisación del LLM. Es exactamente lo que predice la descomposición de Litman.

**2.4 Rutas compensatorias honestas.** Aparecen ramas constructivas (ej. cambio, MX: A4→A9→A10, ancla visual → memoria visual superior → recupera con pista visual): el modelo no es solo déficit, halla fortalezas.

## 3. Honestidad / limitación

Una parte de los pasos son **elaboración del mismo axioma** entre niveles (A1→A1→A1, A17→A17): despliegan la consecuencia en vez de avanzar a una nueva. No rompe la lógica ni el grounding, pero no toda la profundidad es "consecuencia nueva"; parte es despliegue del mismo principio. Se documenta como limitación, no se oculta.

## 4. Conclusión

El control cruzado **pasa**: grounding 100% limpio en los 25 árboles y cadenas lógicamente coherentes y propias de cada dominio. La diferenciación por subtipo (Litman) y la inversión neurotípico↔autismo no son artefactos de la visualización: están en el razonamiento paso a paso, certificado y auditable.

---

## Anexo — cadenas más profundas por problema y actor

## Sensorial (luces)

**Π:** Cambian las luces por fluorescentes más brillantes y que zumban

### NT · Neurotípico
- Axiomas usados: `N1, N2, N3, N4, N5, N6, N7, N8, N10, N11, N12, N13, N14, N15, N16, N17, N18, N19, N20, N21, N22, N23, N24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 7

Rama más profunda:

`L0` **[raíz]** A neurotypical cognitive architecture that integrates multiple sensory and social channels through automatic relevance filtering, processes from concrete to abstract across developmental stages, infers implicit social norms through immersive participation, and generalizes learned rules automatically across contexts.

`L1` **[N2]** NeurotypicalCognition habituates to the buzzing lights over time

`L2` **[N11]** NeurotypicalCognition no longer redirects attention toward the buzzing

`L3` **[N1]** NeurotypicalCognition amplifies task-relevant signals over the buzzing

`L4` **[N11]** NeurotypicalCognition maintains attention on task-relevant demands

`L5` **[N6]** NeurotypicalCognition extracts global meaning from task details

`L6` **[N6]** NeurotypicalCognition interprets task details through overall context

`L7` **[N4]** NeurotypicalCognition integrates verbal and social cues into task comprehension


### SB · TEA social/conductual
- Axiomas usados: `A1, A2, A3, A5, A8, A10, A11, A12, A13, A14, A15, A16, A18, A19, A20, A22, A23, A24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 5

Rama más profunda:

`L0` **[raíz]** An autistic cognitive architecture that prioritizes local sensory detail over global coherence, operates through concrete-visual representations, requires explicit rule structures, and regulates learning through predictable, closed-loop feedback, with hyperfocused, effortful attention regulation, and emotionally dysregulated, alexithymic affective processing.

`L1` **[A1]** SocialBehavioralAutism's cognitive processing goes offline from overload

`L2` **[A1]** SocialBehavioralAutism cannot engage in social interaction now

`L3` **[A15]** SocialBehavioralAutism cannot analyze others' behavioral cues now

`L4` **[A23]** SocialBehavioralAutism cannot detect implicit social expectations now

`L5` **[A23]** SocialBehavioralAutism relies only on explicitly stated classroom rules now


### MX · TEA mixto + retraso
- Axiomas usados: `A1, A2, A3, A4, A5, A6, A7, A9, A10, A17, A18, A19, A20, A21, A22, A23, A24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 10

Rama más profunda:

`L0` **[raíz]** An autistic cognitive architecture that prioritizes local sensory detail over global coherence, operates through concrete-visual representations, requires explicit rule structures, and regulates learning through predictable, closed-loop feedback, with delayed developmental timing and slowed complex processing.

`L1` **[A1]** MixedASDwithDelay's cognitive processing goes offline

`L2` **[A1]** MixedASDwithDelay cannot engage in social interaction

`L3` **[A1]** MixedASDwithDelay cannot access learning processes

`L4` **[A1]** MixedASDwithDelay's learning remains unavailable until sensory regulation restores

`L5` **[A20]** MixedASDwithDelay registers the new lighting as unanticipated change

`L6` **[A2]** MixedASDwithDelay weights buzzing and brightness as equally salient

`L7` **[A3]** MixedASDwithDelay experiences interference integrating buzzing and brightness

`L8` **[A2]** MixedASDwithDelay cannot filter buzzing from brightness by relevance

`L9` **[A6]** MixedASDwithDelay treats the lighting change as environmental volatility

`L10` **[A6]** MixedASDwithDelay experiences processing overload rather than adaptation


### MO · Autismo moderado
- Axiomas usados: `A1, A2, A3, A4, A5, A8, A9, A10, A17, A18, A19, A20, A21, A22, A23, A24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 8

Rama más profunda:

`L0` **[raíz]** An autistic cognitive architecture that prioritizes local sensory detail over global coherence, operates through concrete-visual representations, requires explicit rule structures, and regulates learning through predictable, closed-loop feedback, expressed at attenuated intensity across all domains.

`L1` **[A1]** ModerateAutism risks going offline from sensory overload

`L2` **[A1]** ModerateAutism cannot engage in learning tasks

`L3` **[A1]** ModerateAutism remains offline until sensory regulation is restored

`L4` **[A19]** ModerateAutism loses routine-based cognitive resource allocation

`L5` **[A19]** ModerateAutism must divert resources to process the new stimulus

`L6` **[A20]** ModerateAutism registers disproportionate prediction error from the light change

`L7` **[A1]** ModerateAutism approaches sensory regulatory threshold from combined input

`L8` **[A2]** ModerateAutism cannot prioritize which stimulus to filter


### BR · Ampliamente afectado
- Axiomas usados: `A1, A2, A3, A5, A6, A7, A8, A10, A11, A14, A15, A16, A18, A19, A20, A21, A22, A23, A24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 5

Rama más profunda:

`L0` **[raíz]** An autistic cognitive architecture that prioritizes local sensory detail over global coherence, operates through concrete-visual representations, requires explicit rule structures, and regulates learning through predictable, closed-loop feedback, with hyperfocused, effortful attention regulation, and emotionally dysregulated, alexithymic affective processing, with delayed developmental timing and slowed complex processing.

`L1` **[A1]** BroadlyAffectedAutism goes offline from excessive sensory input

`L2` **[A1]** BroadlyAffectedAutism cannot engage in learning or social interaction

`L3` **[A1]** BroadlyAffectedAutism remains unavailable for instruction until regulation restored

`L4` **[A19]** BroadlyAffectedAutism cannot reallocate resources to classroom tasks

`L5` **[A1]** BroadlyAffectedAutism misses instructional content delivered now


## Cambio de rutina

**Π:** La maestra cambia el horario del día sin aviso

### NT · Neurotípico
- Axiomas usados: `N4, N6, N7, N8, N10, N11, N12, N13, N18, N19, N20, N21, N22, N23, N24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 6

Rama más profunda:

`L0` **[raíz]** A neurotypical cognitive architecture that integrates multiple sensory and social channels through automatic relevance filtering, processes from concrete to abstract across developmental stages, infers implicit social norms through immersive participation, and generalizes learned rules automatically across contexts.

`L1` **[N20]** NeurotypicalCognition generates a prediction error proportional to the change

`L2` **[N7]** NeurotypicalCognition increases its learning rate now

`L3` **[N20]** NeurotypicalCognition rapidly updates its contextual model of the schedule

`L4` **[N6]** NeurotypicalCognition integrates the new schedule into global context

`L5` **[N6]** NeurotypicalCognition reinterprets subsequent events under the updated context

`L6` **[N6]** NeurotypicalCognition interprets new events through updated schedule context


### SB · TEA social/conductual
- Axiomas usados: `A1, A4, A9, A10, A11, A12, A13, A14, A16, A18, A19, A20, A21, A22, A23, A24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 5

Rama más profunda:

`L0` **[raíz]** An autistic cognitive architecture that prioritizes local sensory detail over global coherence, operates through concrete-visual representations, requires explicit rule structures, and regulates learning through predictable, closed-loop feedback, with hyperfocused, effortful attention regulation, and emotionally dysregulated, alexithymic affective processing.

`L1` **[A20]** SocialBehavioralAutism generates disproportionate prediction error signals

`L2` **[A19]** SocialBehavioralAutism cannot allocate resources to other tasks

`L3` **[A1]** SocialBehavioralAutism cannot sustain cognitive processing during disruption

`L4` **[A1]** SocialBehavioralAutism remains offline until sensory regulation restored

`L5` **[A1]** SocialBehavioralAutism cannot engage in social interaction


### MX · TEA mixto + retraso
- Axiomas usados: `A1, A2, A3, A4, A6, A7, A9, A10, A17, A18, A19, A20, A21, A22, A23, A24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 6

Rama más profunda:

`L0` **[raíz]** An autistic cognitive architecture that prioritizes local sensory detail over global coherence, operates through concrete-visual representations, requires explicit rule structures, and regulates learning through predictable, closed-loop feedback, with delayed developmental timing and slowed complex processing.

`L1` **[A20]** MixedASDwithDelay generates disproportionate prediction error signal

`L2` **[A20]** MixedASDwithDelay experiences disruption disproportionate to actual change

`L3` **[A6]** MixedASDwithDelay processes the change as overload not update

`L4` **[A1]** MixedASDwithDelay becomes cognitively offline for learning

`L5` **[A1]** MixedASDwithDelay cannot engage socially with the teacher

`L6` **[A1]** MixedASDwithDelay remains offline until sensory regulation restored


### MO · Autismo moderado
- Axiomas usados: `A1, A2, A3, A4, A5, A9, A10, A18, A19, A20, A21, A22, A23, A24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 6

Rama más profunda:

`L0` **[raíz]** An autistic cognitive architecture that prioritizes local sensory detail over global coherence, operates through concrete-visual representations, requires explicit rule structures, and regulates learning through predictable, closed-loop feedback, expressed at attenuated intensity across all domains.

`L1` **[A20]** ModerateAutism generates disproportionate prediction error signals

`L2` **[A19]** ModerateAutism must reallocate cognitive resources to handle the change

`L3` **[A22]** ModerateAutism cannot generalize old schedule rules to new context

`L4` **[A22]** ModerateAutism requires explicit instruction to learn new schedule

`L5` **[A24]** ModerateAutism requires specific immediate feedback to update schedule behavior

`L6` **[A24]** ModerateAutism disregards vague or delayed feedback about schedule


### BR · Ampliamente afectado
- Axiomas usados: `A1, A2, A3, A6, A9, A10, A11, A12, A13, A14, A15, A16, A18, A19, A20, A21, A22, A23, A24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 5

Rama más profunda:

`L0` **[raíz]** An autistic cognitive architecture that prioritizes local sensory detail over global coherence, operates through concrete-visual representations, requires explicit rule structures, and regulates learning through predictable, closed-loop feedback, with hyperfocused, effortful attention regulation, and emotionally dysregulated, alexithymic affective processing, with delayed developmental timing and slowed complex processing.

`L1` **[A20]** BroadlyAffectedAutism generates disproportionate prediction error signal

`L2` **[A20]** BroadlyAffectedAutism experiences disruption disproportionate to schedule change significance

`L3` **[A21]** BroadlyAffectedAutism blocks learning if change framed as failure

`L4` **[A24]** BroadlyAffectedAutism requires observable, specific, causal feedback to update

`L5` **[A24]** BroadlyAffectedAutism fails to update without explicit causal feedback


## Sarcasmo

**Π:** Un compañero usa sarcasmo en una conversación grupal

### NT · Neurotípico
- Axiomas usados: `N3, N4, N6, N7, N8, N9, N10, N11, N12, N14, N15, N16, N17, N18, N19, N20, N21, N22, N23, N24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 7

Rama más profunda:

`L0` **[raíz]** A neurotypical cognitive architecture that integrates multiple sensory and social channels through automatic relevance filtering, processes from concrete to abstract across developmental stages, infers implicit social norms through immersive participation, and generalizes learned rules automatically across contexts.

`L1` **[N18]** NeurotypicalCognition detects norm relevance of the sarcastic remark automatically

`L2` **[N4]** NeurotypicalCognition integrates the sarcasm with ongoing social context

`L3` **[N6]** NeurotypicalCognition interprets the remark using surrounding context

`L4` **[N18]** NeurotypicalCognition registers the remark as consistent with social norms

`L5` **[N18]** NeurotypicalCognition continues social participation without correction needed

`L6` **[N11]** NeurotypicalCognition redirects attention to next social signal

`L7` **[N4]** NeurotypicalCognition integrates new verbal and social information simultaneously


### SB · TEA social/conductual
- Axiomas usados: `A5, A8, A10, A11, A15, A16, A17, A18, A19, A20, A21, A22, A23, A24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 6

Rama más profunda:

`L0` **[raíz]** An autistic cognitive architecture that prioritizes local sensory detail over global coherence, operates through concrete-visual representations, requires explicit rule structures, and regulates learning through predictable, closed-loop feedback, with hyperfocused, effortful attention regulation, and emotionally dysregulated, alexithymic affective processing.

`L1` **[A17]** SocialBehavioralAutism processes the sarcastic statement literally by default

`L2` **[A18]** SocialBehavioralAutism must consciously retrieve a stored pragmatic rule

`L3` **[A18]** SocialBehavioralAutism requires effortful conscious matching to interpret sarcasm

`L4` **[A16]** SocialBehavioralAutism responds to the sarcasm after a delay

`L5` **[A16]** SocialBehavioralAutism's reply arrives after the conversational moment passes

`L6` **[A8]** SocialBehavioralAutism retains few episodic details of this exchange


### MX · TEA mixto + retraso
- Axiomas usados: `A1, A6, A7, A8, A10, A17, A18, A20, A21, A22, A23, A24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 6

Rama más profunda:

`L0` **[raíz]** An autistic cognitive architecture that prioritizes local sensory detail over global coherence, operates through concrete-visual representations, requires explicit rule structures, and regulates learning through predictable, closed-loop feedback, with delayed developmental timing and slowed complex processing.

`L1` **[A17]** MixedASDwithDelay decodes the sarcasm as literal statement

`L2` **[A17]** MixedASDwithDelay requires extra inference to detect irony

`L3` **[A18]** MixedASDwithDelay searches explicit rules for sarcasm cues

`L4` **[A7]** MixedASDwithDelay processes the social exchange at reduced speed

`L5` **[A6]** Continued rapid conversational shifts increase processing overload

`L6` **[A1]** MixedASDwithDelay goes offline for social processing


### MO · Autismo moderado
- Axiomas usados: `A8, A17, A18, A19, A20, A21, A22, A23, A24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 6

Rama más profunda:

`L0` **[raíz]** An autistic cognitive architecture that prioritizes local sensory detail over global coherence, operates through concrete-visual representations, requires explicit rule structures, and regulates learning through predictable, closed-loop feedback, expressed at attenuated intensity across all domains.

`L1` **[A17]** ModerateAutism processes the sarcastic utterance literally by default

`L2` **[A17]** ModerateAutism misinterprets the sarcastic statement as truthful

`L3` **[A18]** ModerateAutism cannot infer the classmate's actual intended meaning

`L4` **[A24]** ModerateAutism requires explicit feedback to reinterpret the sarcasm

`L5` **[A24]** ModerateAutism retains literal meaning absent proximate corrective feedback

`L6` **[A22]** ModerateAutism cannot generalize this literal meaning to future sarcasm


### BR · Ampliamente afectado
- Axiomas usados: `A1, A5, A6, A7, A8, A15, A16, A17, A18, A19, A20, A21, A22, A23, A24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 5

Rama más profunda:

`L0` **[raíz]** An autistic cognitive architecture that prioritizes local sensory detail over global coherence, operates through concrete-visual representations, requires explicit rule structures, and regulates learning through predictable, closed-loop feedback, with hyperfocused, effortful attention regulation, and emotionally dysregulated, alexithymic affective processing, with delayed developmental timing and slowed complex processing.

`L1` **[A17]** BroadlyAffectedAutism processes the sarcastic statement as literal meaning

`L2` **[A18]** BroadlyAffectedAutism fails to retrieve applicable pragmatic rule entry

`L3` **[A18]** BroadlyAffectedAutism cannot match statement to social context

`L4` **[A17]** BroadlyAffectedAutism responds to the statement as literally true

`L5` **[A20]** BroadlyAffectedAutism generates unanticipated prediction error from peer reaction


## Burla

**Π:** Un compañero se burla abiertamente del niño frente al grupo

### NT · Neurotípico
- Axiomas usados: `N7, N8, N10, N11, N12, N13, N14, N15, N16, N17, N18, N20, N21, N22, N23, N24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 6

Rama más profunda:

`L0` **[raíz]** A neurotypical cognitive architecture that integrates multiple sensory and social channels through automatic relevance filtering, processes from concrete to abstract across developmental stages, infers implicit social norms through immersive participation, and generalizes learned rules automatically across contexts.

`L1` **[N18]** NeurotypicalCognition automatically detects the mockery as a norm violation

`L2` **[N12]** NeurotypicalCognition anticipates social consequences from the peer group

`L3` **[N12]** NeurotypicalCognition adjusts behavior to align with anticipated social outcomes

`L4` **[N18]** NeurotypicalCognition updates social norm understanding via feedback

`L5` **[N24]** NeurotypicalCognition integrates this feedback with prior social knowledge

`L6` **[N22]** NeurotypicalCognition generalizes this social rule across new contexts


### SB · TEA social/conductual
- Axiomas usados: `A14, A15, A16, A17, A18, A19, A20, A21, A22, A23, A24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 5

Rama más profunda:

`L0` **[raíz]** An autistic cognitive architecture that prioritizes local sensory detail over global coherence, operates through concrete-visual representations, requires explicit rule structures, and regulates learning through predictable, closed-loop feedback, with hyperfocused, effortful attention regulation, and emotionally dysregulated, alexithymic affective processing.

`L1` **[A15]** SocialBehavioralAutism requires inferential analysis to interpret the mockery

`L2` **[A18]** SocialBehavioralAutism retrieves stored social rules to interpret mockery

`L3` **[A22]** SocialBehavioralAutism cannot generalize prior rules to this mockery

`L4` **[A22]** SocialBehavioralAutism requires explicit new instruction for this mockery

`L5` **[A24]** SocialBehavioralAutism cannot update behavior without observable specific feedback


### MX · TEA mixto + retraso
- Axiomas usados: `A1, A6, A7, A8, A10, A17, A18, A19, A20, A21, A22, A23, A24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 6

Rama más profunda:

`L0` **[raíz]** An autistic cognitive architecture that prioritizes local sensory detail over global coherence, operates through concrete-visual representations, requires explicit rule structures, and regulates learning through predictable, closed-loop feedback, with delayed developmental timing and slowed complex processing.

`L1` **[A17]** MixedASDwithDelay does not automatically decode mockery as ridicule

`L2` **[A17]** MixedASDwithDelay processes the mocking words literally

`L3` **[A23]** MixedASDwithDelay fails to detect the implicit social norm violation

`L4` **[A23]** MixedASDwithDelay does not adjust behavior to the unspoken expectation

`L5` **[A22]** MixedASDwithDelay cannot generalize this norm to future contexts

`L6` **[A23]** MixedASDwithDelay only follows explicitly stated social rules


### MO · Autismo moderado
- Axiomas usados: `A1, A4, A8, A10, A17, A18, A19, A20, A21, A22, A23, A24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 6

Rama más profunda:

`L0` **[raíz]** An autistic cognitive architecture that prioritizes local sensory detail over global coherence, operates through concrete-visual representations, requires explicit rule structures, and regulates learning through predictable, closed-loop feedback, expressed at attenuated intensity across all domains.

`L1` **[A17]** ModerateAutism does not automatically decode the mockery's intent

`L2` **[A23]** ModerateAutism cannot detect the unspoken insult convention

`L3` **[A17]** ModerateAutism interprets the classmate's words at face value

`L4` **[A17]** ModerateAutism accepts the statement as literally true

`L5` **[A10]** ModerateAutism cannot later reinterpret the event without visual cues

`L6` **[A8]** ModerateAutism retains the mockery as isolated fact not narrative


### BR · Ampliamente afectado
- Axiomas usados: `A1, A6, A7, A8, A10, A14, A15, A16, A17, A18, A19, A20, A21, A22, A23, A24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 5

Rama más profunda:

`L0` **[raíz]** An autistic cognitive architecture that prioritizes local sensory detail over global coherence, operates through concrete-visual representations, requires explicit rule structures, and regulates learning through predictable, closed-loop feedback, with hyperfocused, effortful attention regulation, and emotionally dysregulated, alexithymic affective processing, with delayed developmental timing and slowed complex processing.

`L1` **[A17]** BroadlyAffectedAutism does not automatically decode the mocking's ironic intent

`L2` **[A17]** BroadlyAffectedAutism processes the mocking words literally

`L3` **[A17]** BroadlyAffectedAutism requires extra inferential steps to detect mockery

`L4` **[A16]** BroadlyAffectedAutism's emotional response to mockery occurs later

`L5` **[A24]** BroadlyAffectedAutism's delayed reaction receives no temporally proximate feedback


## Atención

**Π:** El niño debe soltar un foco absorbente y pasar a una tarea grupal

### NT · Neurotípico
- Axiomas usados: `N4, N6, N7, N8, N11, N12, N13, N14, N15, N16, N17, N18, N19, N20, N21, N22, N23, N24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 7

Rama más profunda:

`L0` **[raíz]** A neurotypical cognitive architecture that integrates multiple sensory and social channels through automatic relevance filtering, processes from concrete to abstract across developmental stages, infers implicit social norms through immersive participation, and generalizes learned rules automatically across contexts.

`L1` **[N11]** NeurotypicalCognition redirects attention toward the group task

`L2` **[N4]** NeurotypicalCognition integrates the group task's social and contextual cues

`L3` **[N23]** NeurotypicalCognition infers the group's implicit behavioral expectations

`L4` **[N18]** NeurotypicalCognition aligns its behavior with group norms

`L5` **[N12]** NeurotypicalCognition anticipates social approval from the group

`L6` **[N12]** NeurotypicalCognition sustains behavior aligned with the group task

`L7` **[N11]** NeurotypicalCognition remains able to redirect attention if salience shifts


### SB · TEA social/conductual
- Axiomas usados: `A1, A2, A5, A11, A12, A13, A14, A15, A16, A18, A19, A20, A21, A22, A23, A24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 5

Rama más profunda:

`L0` **[raíz]** An autistic cognitive architecture that prioritizes local sensory detail over global coherence, operates through concrete-visual representations, requires explicit rule structures, and regulates learning through predictable, closed-loop feedback, with hyperfocused, effortful attention regulation, and emotionally dysregulated, alexithymic affective processing.

`L1` **[A11]** SocialBehavioralAutism requires effortful control to redirect attention

`L2` **[A11]** SocialBehavioralAutism cannot sustain attention on group task automatically

`L3` **[A20]** SocialBehavioralAutism generates disproportionate prediction error at redirection

`L4` **[A1]** SocialBehavioralAutism risks going offline from sensory overload

`L5` **[A1]** SocialBehavioralAutism cannot process the group task cognitively


### MX · TEA mixto + retraso
- Axiomas usados: `A1, A2, A5, A6, A7, A8, A18, A19, A20, A21, A22, A23, A24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 5

Rama más profunda:

`L0` **[raíz]** An autistic cognitive architecture that prioritizes local sensory detail over global coherence, operates through concrete-visual representations, requires explicit rule structures, and regulates learning through predictable, closed-loop feedback, with delayed developmental timing and slowed complex processing.

`L1` **[A20]** MixedASDwithDelay generates disproportionate prediction error from the redirect

`L2` **[A19]** MixedASDwithDelay loses the resource-saving benefit of routine

`L3` **[A7]** MixedASDwithDelay processes the group task more slowly

`L4` **[A24]** MixedASDwithDelay misses temporally proximate feedback on the task

`L5` **[A24]** MixedASDwithDelay fails to update behavior from the task


### MO · Autismo moderado
- Axiomas usados: `A1, A2, A4, A5, A18, A19, A20, A21, A22, A23, A24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 4

Rama más profunda:

`L0` **[raíz]** An autistic cognitive architecture that prioritizes local sensory detail over global coherence, operates through concrete-visual representations, requires explicit rule structures, and regulates learning through predictable, closed-loop feedback, expressed at attenuated intensity across all domains.

`L1` **[A20]** ModerateAutism generates disproportionate prediction error from the redirect

`L2` **[A20]** ModerateAutism reacts as if redirect is catastrophic

`L3` **[A5]** ModerateAutism continues fixating on the local detail

`L4` **[A22]** ModerateAutism cannot apply prior redirect rules to this context


### BR · Ampliamente afectado
- Axiomas usados: `A1, A6, A7, A10, A11, A12, A13, A14, A16, A17, A18, A19, A20, A21, A22, A23, A24`
- Grounding: ✅ OK (solo axiomas permitidos)
- Profundidad máxima: 6

Rama más profunda:

`L0` **[raíz]** An autistic cognitive architecture that prioritizes local sensory detail over global coherence, operates through concrete-visual representations, requires explicit rule structures, and regulates learning through predictable, closed-loop feedback, with hyperfocused, effortful attention regulation, and emotionally dysregulated, alexithymic affective processing, with delayed developmental timing and slowed complex processing.

`L1` **[A11]** BroadlyAffectedAutism requires effortful control to shift attention

`L2` **[A11]** BroadlyAffectedAutism cannot sustain attention on the group task automatically

`L3` **[A11]** BroadlyAffectedAutism must expend effortful control to engage the task

`L4` **[A13]** BroadlyAffectedAutism transfers knowledge less reliably from the group task

`L5` **[A22]** BroadlyAffectedAutism needs explicit instruction to reapply this learning

`L6` **[A22]** BroadlyAffectedAutism cannot generalize the learning without new instruction

