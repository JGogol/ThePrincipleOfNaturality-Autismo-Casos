# Un ejemplo real, paso a paso — el Principio de la Naturalidad aplicado al autismo

Este es un caso **real** extraído de las corridas (no un ejemplo inventado): la **convergencia certificada más fuerte** entre el razonamiento neurotípico y el autista, con entailment **AVG = 0,997** (bidireccional, casi perfecto). Sirve para entender cómo PN **genera y calcula** el árbol inferencial, y qué significa que dos arquitecturas "converjan".

---

## 1. El problema (Π)

> **La maestra cambia el horario del día sin ningún aviso.**

El mismo problema se le presenta a las 5 arquitecturas. Acá seguimos a dos: el **neurotípico (NT)** y el subtipo **TEA social/conductual (SB)**.

## 2. Cómo se genera el árbol inferencial (el motor de PN)

1. **Cada actor es su arquitectura.** La raíz del árbol es el actor definido *solo* por su conjunto de axiomas (su forma de razonar). No se exploran los axiomas uno por uno: **licencian** cada inferencia.
2. **Se pide la primera consecuencia.** Ante Π, el motor le pide al LLM las inferencias inmediatas que **los axiomas del actor permiten**. Cada nodo generado **debe citar el axioma que lo licencia** (grounding auditable); si ninguna premisa lo sostiene, se descarta.
3. **El árbol crece por consecuencia.** Cada nodo se expande en sus consecuencias, siempre ancladas a un axioma, empujadas *hacia el problema* (no hacia la postura del actor).
4. **Se buscan convergencias.** El único objetivo es encontrar dónde las cadenas de dos actores **llegan a la misma conclusión, certificada por lógica (NLI)**.

## 3. Las dos cadenas (raíz → nodo), en español

### Neurotípico (NT)

- **L0 · raíz** — *Arquitectura cognitiva neurotípica que integra múltiples canales sensoriales y sociales por filtrado automático de relevancia, procesa de lo concreto a lo abstracto, infiere normas sociales implícitas por participación, y generaliza reglas aprendidas entre contextos.*
- **L1 · [N20]** — **El neurotípico genera un error de predicción proporcional al cambio.**
  - *Axioma N20 (El cambio como novedad manejable): «El cambio inesperado genera un error de predicción proporcional a la significancia objetiva del cambio, y se resuelve por actualización contextual rápida.»*

### TEA social/conductual (SB)

- **L0 · raíz** — *Arquitectura cognitiva autista que prioriza el detalle sensorial local sobre la coherencia global, opera con representaciones visual-concretas, requiere estructuras de regla explícitas, regula el aprendizaje por feedback predecible de lazo cerrado, con atención hiperfocalizada y esforzada, y procesamiento afectivo alexitímico.*
- **L1 · [A4]** — El autista necesita un ancla visual para el nuevo horario.
  - *Axioma A4 (Visual-concreto primario): «El formato primario es visual-concreto; lo abstracto requiere anclaje a referentes concretos.»*
- **L2 · [A20]** — **El autista experimenta un error de predicción desproporcionado por el cambio.**
  - *Axioma A20 (El cambio como disrupción): «El cambio inesperado genera señales de error de predicción desproporcionadas (HIPPEA: precisión inflexible sobre los errores de predicción).»*

## 4. El punto de convergencia (lo que se certificó)

Las dos inferencias marcadas en negrita **se implican mutuamente**:

> **NT [N20]:** «genera un error de predicción … por el cambio»
> **SB [A20]:** «experimenta un error de predicción … por el cambio»

**Terreno común certificado:** ante el cambio de horario, **ambas arquitecturas —la neurotípica y la autista— generan un error de predicción**. Las dos *registran el cambio* como un evento que hay que procesar. Ahí **se encuentran**.

**Dónde divergen (visible en el mismo nodo):** en la **magnitud**. El neurotípico lo estima **proporcional** (N20 → se adapta por actualización rápida); el autista, **desproporcionado** (A20 → se sobrecarga). El punto de encuentro es *que hay un error de predicción*; la diferencia irreducible es *cuánto*.

## 5. Cómo se calculó (la cascada NLI)

La convergencia no se afirma: se **certifica** en tres etapas.

1. **Pre-filtro por similitud** (embeddings, coseno): descarta pares obviamente no relacionados.
2. **NLI bidireccional** (DeBERTa, criterio AVG, umbral τ = 0,55): mide si cada frase **implica** a la otra en ambos sentidos. Acá: **forward = 0,996 · backward = 0,998 · AVG = 0,997**.
3. **Verificación por inversión de roles** (LLM): descarta falsos positivos. Este par **la pasó** → queda en el grafo certificado F.

## 6. Por qué esto ejemplifica PN aplicado al autismo

- **No es opinión ni etiqueta médica:** es una inferencia licenciada por un axioma documentado, y una convergencia certificada por lógica.
- **Muestra el valor humano:** el punto de encuentro (*ambos registran el cambio como error de predicción*) dice que **anticipar y anunciar los cambios** es terreno común entre el niño neurotípico y el autista — le sirve a los dos. La divergencia (magnitud) dice **dónde** el autista necesita apoyo (regular la sobrecarga).
- **Es auditable de punta a punta:** cada nodo cita su axioma; cada convergencia trae su g y su cadena. Todo verificable contra las corridas de este repositorio.

---

*Convergencia certificada por NLI (bidireccional AVG τ=0,55 + verificación por inversión de roles). Corrida: `cambio de rutina`. Los datos crudos están en `runs/2026-08-14_14-54-35/` (árboles + `fusiones.json`).*
