# The Principle of Naturality — Autism Cases (open dataset)

Dataset abierto que respalda la visualización **«THE PRINCIPLE OF NATURALITY APLICADO EN AUTISMO»** (Concurso *Contar con Datos 2026*, categoría Exploración interactiva).

Contiene los axiomas de las 5 arquitecturas cognitivas, la definición de los 5 problemas cotidianos, los **grafos de inferencias certificadas** de cada corrida (crudos y en CSV limpio), y las auditorías (test de permutación y control cruzado de grounding). Todo es verificable y reproducible.

---

## 1. Qué se estudia

Cómo **cinco arquitecturas cognitivas** —un niño neurotípico y los cuatro subtipos de autismo— razonan la **misma situación cotidiana**, y **dónde sus razonamientos convergen (terreno común) y dónde no (la diferencia irreducible)**. Cada convergencia se **certifica** por inferencia lógica (NLI), no se afirma.

El **objeto de estudio es el Principio de la Naturalidad (PN)**, marco neuro-simbólico creado por el autor. La IA es un **instrumento**: genera cada inferencia **obligada a citar el axioma que la licencia**; si ninguna premisa la sostiene, se descarta.

## 2. Origen de los axiomas (fuentes)

| Actor | Código | Origen de sus axiomas |
|---|---|---|
| Neurotípico | NT | **Baseline de desarrollo típico**, contrapunto sistemático de cada axioma autista, apoyado en constructos establecidos de la ciencia cognitiva (filtrado de saliencia automático; integración multisensorial; coherencia central —vs. la débil de Frith & Happé—; codificación predictiva proporcional —vs. HIPPEA, Van de Cruys et al.—; acceso interoceptivo —vs. alexitimia, Kinnaird et al.—; pragmática plena; Piaget). **No proviene de Litman.** |
| Social/conductual | SB | Núcleo autista + atención (A11–13) + emoción (A14–16). |
| Mixto + retraso | MX | Núcleo + retraso del desarrollo (A6–A7). |
| Autismo moderado | MO | Solo el núcleo (A1–A5, A8–A10, A17–A25). |
| Ampliamente afectado | BR | Axiomas A1–A25 completos. |

> **Los 4 subtipos de autismo y sus deltas** se derivan de **Litman et al. (2025)** (descomposición fenotípica en 4 clases); regla determinística documentada en `DESIGN_5actors_EN.md`. **Litman aplica solo al autismo.**

## 3. Los 5 problemas (Π)

| id | Situación cotidiana | corrida |
|---|---|---|
| 01_sensorial | Cambian las luces por fluorescentes más brillantes y que zumban. | runs/2026-08-15_20-53-18 |
| 02_cambio | La maestra cambia el horario del día sin aviso. | runs/2026-08-14_14-54-35 |
| 03_sarcasmo | Un compañero usa sarcasmo en una conversación grupal. | runs/2026-08-14_22-33-08 |
| 04_burla | Un compañero se burla abiertamente del niño frente al grupo. | runs/2026-08-15_08-35-41 |
| 07_atencion | El niño debe soltar un foco absorbente y pasar a una tarea grupal. | runs/2026-08-16_19-20-46 |

## 4. Cómo se certifica una convergencia

Dos inferencias (una de cada actor) convergen si **se implican mutuamente** bajo: (1) pre-filtro de similitud por embeddings, (2) **NLI bidireccional** (DeBERTa, criterio AVG, umbral τ = 0.55), (3) verificación por **inversión de roles** (LLM), que descarta falsos positivos.

## 5. Estructura del repositorio

```
DESIGN_5actors_EN.md          Los 50 axiomas (N1–N25, A1–A25) + derivación de Litman.
final_XX_*.json               Definición de cada problema: enunciado Π + premisas (axiomas) por actor.
final_XX_*_result.json        Métricas de la corrida.
runs/<timestamp>/             Grafo certificado CRUDO por corrida:
    arboles/*.json              nodos con su premise_id (grounding).
    fusiones.json               convergencias certificadas (aristas de F).
    hubs.json                   HUBs detectados (estricto/lax).
grafos_certificados/          Capa limpia (CSV) derivada de runs/:
    XX_nodos.csv                una fila por inferencia.
    XX_convergencias.csv        una fila por convergencia certificada.
auditoria/
    null_test.json              Test de permutación de etiquetas (1000×) por problema.
    CONTROL_CRUZADO.md          Verificación de grounding + lógica de cadenas raíz→hoja.
    problem_stats.json          Estadística por problema: matrices de convergencia y contradicción (5×5),
                                stats por actor (nodos, F, %F, g medio, axioma dominante) y nodos más convergentes.
docs/index.html               Visualización interactiva (GitHub Pages).
```

### Diccionario — `grafos_certificados/XX_nodos.csv`
| Campo | Significado |
|---|---|
| `node_id` | Identificador único (actor_nivel_índice). |
| `actor` / `actor_full` | Actor que generó la inferencia. |
| `premise_id` | Axioma que licencia la inferencia (grounding). Vacío = raíz. |
| `converge_F` | 1 si el nodo pertenece a F (participa de ≥1 convergencia certificada). |
| `g_entailment_max` | Máximo score de entailment NLI del nodo (0–1). |
| `nivel` | Profundidad en el árbol (0 = raíz). |
| `texto` | La inferencia, en inglés (NLI opera en inglés). |

### Diccionario — `grafos_certificados/XX_convergencias.csv`
| Campo | Significado |
|---|---|
| `nodo_a_id` / `nodo_b_id` | Los dos nodos que convergen. |
| `actor_a` / `actor_b` | Sus actores. |
| `similitud_sbert` | Similitud de embeddings del par. |

## 6. Resultados clave (auditados)

- Los 4 subtipos autistas convergen densamente entre sí; el neurotípico queda **aislado (converge 20–42× menos)**.
- El aislamiento **sobrevive a un test de azar**: `auditoria/null_test.json` → observado 20–42× vs. máximo del null ~3× → **p < 0.001** en los 5 problemas.
- **HUB estricto (transitividad completa): 0/5** — la convergencia nunca cierra del todo con el neurotípico.
- **Grounding 100% limpio**: cada actor infirió solo con sus axiomas (25 árboles, 0 violaciones). Ver `auditoria/CONTROL_CRUZADO.md`.

## 7. Límites de cómputo (honestidad)

Cada actor se exploró hasta **150 nodos** (inferencias): con 5 actores × 5 problemas, ≈3.750 nodos y ≈9.100 convergencias certificadas. **Ese límite de 150 es una restricción de cómputo, no de diseño.** El ideal habría sido **≥500 nodos/actor**: mayor profundidad de exploración aumenta la probabilidad de detectar convergencias adicionales, **HUBs estrictos (transitividad global)** y más riqueza de datos.

Las 5 corridas sumaron **≈39 horas** (≈8 h por problema; Burla, 11,8 h) en un **i7 de 12ª generación con 16 GB de RAM, sin GPU**.

**Implicación honesta:** el **HUB estricto = 0/5** significa que no se alcanzó transitividad completa **dentro de este presupuesto** — no que sea imposible; con más cómputo podría aparecer. Lo reportado es un **piso, no un techo**. En cambio, el aislamiento del neurotípico (20–42×, **p<0.001**) es robusto: una tendencia fuerte que sobrevive al test de azar.

## 8. Marco teórico y reconocimiento

- Principio de la Naturalidad, Parte I — «Constructing Certified Convergence»: https://zenodo.org/records/20670259
- Principio de la Naturalidad, Parte II — «Certified Convergence Spaces»: https://zenodo.org/records/21904325
- 2º Premio, **GCSP Prize for Transformative Futures in Peace and Security 2026** (Geneva Centre for Security Policy).

## 9. Licencia

Datos publicados bajo **Creative Commons Attribution 4.0 (CC BY 4.0)** — uso y verificación libres con atribución.
Autor: **Ing. E. Javier Gogol Merletti** · ORCID 0009-0004-4294-4816.
