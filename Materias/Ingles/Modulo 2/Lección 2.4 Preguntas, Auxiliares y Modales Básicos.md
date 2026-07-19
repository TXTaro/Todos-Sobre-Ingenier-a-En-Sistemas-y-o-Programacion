# Inglés Técnico — Módulo 2 — Lección 2.4: Preguntas, Auxiliares y Modales Básicos (Can / Must / Should)

> **"Un requerimiento técnico que dice 'must' no es lo mismo que uno que dice 'should'. Uno es obligatorio, el otro es una recomendación. Confundirlos en una spec puede costar tiempo real de desarrollo."**
> 
> Esta es la última lección del módulo. Vas a cerrar dos cosas: cómo formar preguntas correctamente en cualquier tiempo verbal que ya conoces, y el vocabulario exacto que usa cualquier documento de requerimientos técnicos.

---

## 🎚️ Ubicación en el mapa

- **Módulo:** 2 — State Management (El Inglés en Movimiento)
- **Nivel de esta lección:** Fundamento (cierre de módulo)
- **Requiere haber visto:** Lecciones 2.1, 2.2 y 2.3 — aquí unificamos cómo se forman preguntas en cada tiempo verbal que ya viste, y agregamos una pieza nueva: los modales.

---

## 🔩 Núcleo (lo esencial, no se salta)

### 0. Repaso rápido: el patrón de preguntas que ya conocías sin saberlo

A lo largo del módulo ya usaste preguntas sin que las juntáramos todas en un solo lugar. Aquí está el patrón unificado:

```
To Be:              Is the server running?
Presente Simple:    Does she code in Python?          (auxiliar: do/does)
Presente Continuo:  Are you working on this?
Pasado Simple:      Did the build fail?                (auxiliar: did)
Pasado Continuo:    Was the server running when it crashed?
Futuro (will):      Will this fix the bug?
Futuro (going to):  Are we going to deploy today?
```

**El patrón que se repite siempre:** el verbo auxiliar (o `to be`) se mueve al frente de la oración, antes del sujeto. Eso es, literalmente, toda la regla de preguntas en inglés — no hay 7 reglas distintas, hay una sola regla aplicada 7 veces a distintos tiempos.

```
[AUXILIAR/TO BE] + [SUJETO] + [resto de la oración]?
```

---

### 1. Preguntas con palabras interrogativas (Wh- questions)

Además de preguntas de sí/no (arriba), necesitas preguntas que pidan información específica:

```
What    qué        What is the error message?
Where   dónde       Where is the server located?
When    cuándo      When did the crash happen?
Why     por qué     Why is this failing?
Who     quién       Who fixed this bug?
How     cómo        How does this function work?
```

**El orden no cambia** — la palabra interrogativa simplemente se coloca antes del patrón que ya conoces:

```
[PALABRA INTERROGATIVA] + [AUXILIAR/TO BE] + [SUJETO] + [resto]?

What  is    the server    doing?
Why   did   the build     fail?
How   does  this function work?
```

---

### 2. Modales: expresando posibilidad, obligación y recomendación

Los **verbos modales** son un grupo especial de verbos que no describen una acción — modifican el significado de otro verbo, agregando una actitud (posibilidad, obligación, permiso, recomendación).

**Estructura fija (más simple que todo lo anterior):**

```
[SUJETO] + [modal] + [verbo base, SIN -s, SIN -ed, SIN nada]
```

Los modales **nunca cambian de forma**, sin importar el sujeto (igual que viste con `will` en la 2.3, que técnicamente también es un modal).

#### 2.1 Can — capacidad o permiso

```
I can fix this.              (soy capaz de arreglarlo)
You can access the admin panel.   (tienes permiso)
```

Negativo: `cannot` o `can't`

```
This function can't return null.
```

#### 2.2 Must — obligación fuerte, necesidad absoluta

```
The password must contain 8 characters.
This function must return a value.
```

`Must` comunica que algo es **estrictamente necesario**, sin excepción — el nivel más fuerte de obligación en inglés técnico.

**Negativo importante:** `must not` (o `mustn't`) no significa "no es necesario" — significa **prohibido**.

```
You must not delete this file.    → está prohibido, no opcional
```

#### 2.3 Should — recomendación, no obligatorio

```
You should validate user input.
The team should write tests before deploying.
```

`Should` es más suave que `must` — es un consejo o buena práctica, pero no es estrictamente obligatorio ni prohibido no hacerlo.

**Comparación directa (la que más te va a servir leyendo specs):**

```
This field must be a valid email.     → obligatorio, sin esto el sistema falla
This field should be under 50 characters.  → recomendado, pero no rompe nada si no se cumple
```

#### 2.4 May / Might — posibilidad incierta

```
This might cause a memory leak.
The error may be related to the database.
```

Comunican una posibilidad, sin certeza — más débil que `will` de la Lección 2.3.

---

### 3. Los modales en documentos de requerimientos técnicos reales

Este es el uso más importante de esta lección. Los estándares de documentación técnica (como las especificaciones RFC de internet) definen oficialmente qué significa cada palabra:

```
MUST      = obligatorio, absoluto, sin excepción
SHOULD    = recomendado fuertemente, pero hay excepciones válidas
MAY       = opcional, verdaderamente a discreción
MUST NOT  = prohibido, absoluto
```

```
The API response must include a status code.
The client should retry the request if it fails.
The user may choose to enable notifications.
```

Cuando leas cualquier documentación técnica seria, estas palabras **no son casuales** — cada una comunica un nivel de obligación distinto y preciso.

---

### 4. Recapitulación

```
Preguntas: una sola regla (auxiliar/to be al frente) aplicada a 7 tiempos distintos
    ↓
Wh- questions: palabra interrogativa antes del patrón de pregunta
    ↓
Modales: sujeto + modal + verbo base (sin conjugar, nunca cambia)
    ↓
Can (capacidad/permiso) → Must (obligación) → Should (recomendación) → May/Might (posibilidad)
    ↓
En specs técnicas reales, estas palabras tienen significado oficial y preciso
```

Con esto se cierra el Módulo 2 completo. Ya dominas el timeline completo del inglés (pasado, presente, futuro), sabes formar cualquier pregunta, y conoces el vocabulario exacto de obligación y recomendación que vas a leer en cualquier documento de requerimientos técnicos serio.

---

## 🌌 Horizonte-Aplicado

_(esto no lo cubrimos aquí, pero lo vas a necesitar más adelante como developer)_

- **RFCs y estándares técnicos oficiales** — el estándar RFC 2119 de internet define formalmente el significado exacto de MUST, SHOULD y MAY dentro de documentos técnicos — literalmente la lección que acabas de ver, formalizada como estándar de la industria.
- **User stories y criterios de aceptación** — en metodologías ágiles, los criterios de aceptación de una funcionalidad casi siempre usan "should" y "must" para distinguir lo obligatorio de lo deseable.
- **Mensajes de validación en formularios** — cuando un formulario dice `Password must contain a number`, eso es exactamente el modal de obligación que viste aquí, aplicado directo a UX/UI.

## 🏛️ Horizonte-Cultural

_(no lo vas a "usar" en un commit, pero te da contexto y entrena tu oído)_

- **Por qué los modales no se conjugan** — históricamente, los modales del inglés (can, must, may, will, should) vienen de un grupo de verbos en inglés antiguo que ya eran gramaticalmente distintos de los verbos normales; esa "irregularidad total" (nunca llevan -s, -ed, ni necesitan auxiliar do/does) es un fósil lingüístico de esa categoría antigua.
- **El estándar RFC 2119 como ejemplo de precisión lingüística deliberada** — es poco común que un documento técnico defina explícitamente el significado gramatical de palabras comunes, pero la industria de internet lo hizo justamente porque la ambigüedad entre "debe" y "debería" ha causado errores costosos de interpretación en la historia de la ingeniería de software.
- **"Shall" — el modal que casi desapareció** — en inglés más formal o legal (y en estándares técnicos antiguos), vas a encontrar "shall" en vez de "must" (`The system shall respond within 2 seconds`); en inglés hablado moderno casi no se usa, pero sigue vivo en documentos legales y algunas especificaciones técnicas clásicas.

---

## 🧠 Prompts para tu Tutor IA (NotebookLM)

**Modo Express** _(quiero repasar rápido el núcleo)_

> "Actúa como un profesor directo. Basándote únicamente en esta fuente, resume la regla única de preguntas aplicada a los distintos tiempos, y la diferencia entre can, must, should y may, con un ejemplo técnico de cada modal."

**Modo Ingeniero** _(quiero conectar esto con mi trabajo como dev)_

> "De los temas listados en 'Horizonte-Aplicado' de esta fuente, explícame el estándar RFC 2119 con más detalle, y dame 5 ejemplos de requerimientos técnicos usando must, should y may correctamente según ese estándar."

**Modo Escéptico** _(quiero que me examinen)_

> "Actúa como un profesor escéptico y directo. Basándote únicamente en esta fuente, dame 5 oraciones donde tenga que formar la pregunta correcta en distintos tiempos verbales, y 3 situaciones donde tenga que elegir entre must, should y may según el nivel de obligación. Corrígeme con el porqué, sin darme la respuesta antes de que yo intente."

**Modo Expansión** _(quiero más de lo que dice la lección)_

> "Esta fuente es la base mínima. Explícame la diferencia entre 'must' y 'have to' (ambos expresan obligación pero no son intercambiables), y dame ejemplos de cuándo se usa cada uno."

---

## 🎯 Reto de la Comunidad

Antes de pasar al Módulo 3, responde esto en el canal de la materia:

1. Convierte estas afirmaciones en preguntas: `The server is responding.` / `They fixed the bug yesterday.` / `You are going to deploy this.`
2. Elige el modal correcto según el contexto: `Passwords ___ contain at least 8 characters.` (obligatorio) vs. `You ___ add comments to explain complex code.` (recomendado, no obligatorio).
3. Escribe un mini-requerimiento técnico (real o inventado) usando correctamente must, should y may en tres oraciones distintas, como si fuera parte de una spec real.

> **Regla de la comunidad:** No postees la respuesta directa de otros. Si alguien se equivoca, dale una pista, no la solución.

---

**🏁 Módulo 2 de Inglés Técnico completado.** El siguiente paso en la ruta de Inglés es el **Módulo 3: Git Commit & Writing** (ya prometido desde la Lección 1.3) — pero, siguiendo el orden del temario, toca alternar de materia antes de llegar ahí.
