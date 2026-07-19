# Inglés Técnico — Módulo 2 — Lección 2.1: Presente Continuo (Right Now vs. Habits)

> **"`is running` no es lo mismo que `runs`. Uno describe un proceso vivo en este instante; el otro, una rutina. Confundirlos en inglés técnico cambia el significado por completo."**
> 
> En la Lección 1.3 quedó una promesa pendiente: en español no siempre distinguimos claramente "hago" de "estoy haciendo", pero en inglés esa distinción es real y obligatoria. Aquí la cerramos.

---

## 🎚️ Ubicación en el mapa

- **Módulo:** 2 — State Management (El Inglés en Movimiento)
- **Nivel de esta lección:** Fundamento
- **Requiere haber visto:** Lección 1.3 (Verbos Esenciales, especialmente Presente Simple y To Be) — el presente continuo se construye literalmente combinando ambos.

---

## 🔩 Núcleo (lo esencial, no se salta)

### 0. La diferencia real: rutina vs. proceso en curso

```
I work.          → hecho general: mi trabajo, mi rutina (presente simple, Lección 1.3)
I am working.    → ahora mismo, en este instante, estoy trabajando (presente continuo)
```

En español, "trabajo" y "estoy trabajando" a veces se usan casi indistinto en conversación. En inglés técnico **no puedes intercambiarlos** — describen cosas distintas, y en documentación esa diferencia es la que te dice si algo es un comportamiento esperado (siempre) o un evento sucediendo en este momento (ahora).

```
The server processes requests.       → hecho general: eso es lo que hace un servidor
The server is processing a request.  → ahora mismo, en este instante, hay una petición activa
```

---

### 1. Cómo se construye: to be + verbo-ing

El presente continuo se arma con dos piezas que ya conoces de la Lección 1.3:

```
[SUJETO] + [to be conjugado] + [verbo + -ing]
```

```
I    am   working
You  are  working
He   is   working
She  is   working
It   is   loading
We   are  working
They are  working
```

No hay verbo nuevo que aprender — es el mismo `to be` de la 1.3, combinado con la forma `-ing` del verbo principal.

**Regla de ortografía para el `-ing`:**

```
work  → working       (regla base: solo agregas -ing)
run   → running        (consonante final se duplica si la sílaba es corta y acentuada)
make  → making         (la "e" muda al final se elimina antes de -ing)
```

---

### 2. Forma negativa y de pregunta

**Negativa:** igual que con `to be` en la 1.3, agregas `not` directo después del verbo `to be`.

```
I am not working right now.
The server is not responding.
```

Contracción común:

```
is not     → isn't
are not    → aren't
```

**Pregunta:** el verbo `to be` se mueve al frente, igual que ya viste con `to be` solo.

```
Is the server responding?
Are you working on this ticket?
```

---

### 3. Cuándo se usa el presente continuo (más allá de "ahora mismo")

No es solo para el instante exacto en que hablas — también se usa para:

**Algo temporal, aunque no sea en este segundo exacto:**

```
I am learning English this month.
```

(No estoy aprendiendo inglés en este segundo literal, pero es algo activo, en proceso, temporal — no una verdad permanente como en presente simple.)

**Un plan ya organizado a corto plazo (adelanto de la Lección 2.3):**

```
We are deploying the update tomorrow.
```

**Quejas o patrones molestos, con "always" (uso especial, vale la pena conocerlo):**

```
He is always breaking the build.
```

Aquí `always` con presente continuo no significa literalmente "siempre en este instante" — es una forma común de expresar frustración por algo que pasa demasiado seguido. Es una excepción idiomática, no una regla lógica — tenla identificada si la escuchas.

---

### 4. Verbos que normalmente NO se usan en continuo

Hay un grupo de verbos (llamados **stative verbs**, verbos de estado) que casi nunca aparecen en forma `-ing`, porque describen estados mentales o de percepción, no acciones en proceso:

```
know    (saber)       ❌ I am knowing the answer.   ✅ I know the answer.
want    (querer)      ❌ I am wanting this.          ✅ I want this.
understand (entender) ❌ I am understanding it.      ✅ I understand it.
```

**Por qué te importa esto:** vas a ver `I understand the error` constantemente en documentación y conversación técnica, nunca `I am understanding the error` — si alguna vez dudas si algo "suena raro" en `-ing`, probablemente sea uno de estos verbos de estado.

---

### 5. Recapitulación

```
Presente Simple (Lección 1.3) → rutina, hecho general, verdad permanente
    ↓
Presente Continuo (esta lección) → to be + verbo-ing → proceso en curso, temporal
    ↓
Negativo/pregunta → mismo patrón que to be solo
    ↓
Excepción: verbos de estado (know, want, understand) casi nunca van en -ing
```

Con esto ya puedes distinguir con precisión "lo que algo hace siempre" de "lo que algo está haciendo ahora" — una distinción que en logs, dashboards y estado de sistemas cambia completamente lo que se está comunicando.

---

## 🌌 Horizonte-Aplicado

_(esto no lo cubrimos aquí, pero lo vas a necesitar más adelante como developer)_

- **Estados de sistemas en tiempo real** — `Loading...`, `Connecting...`, `Processing...` son presente continuo puro; entender la forma `-ing` te ayuda a leer instantáneamente el estado activo de cualquier interfaz o proceso.
- **Nombres de eventos en programación orientada a eventos** — convenciones como `onLoading`, `isRunning` (variables booleanas que indican un proceso activo) usan directamente esta lógica gramatical aplicada a nombrar código.
- **Present Continuous en reuniones de trabajo (standups)** — cuando reportas avance en un daily standup en inglés (`I am working on the login bug`), esta es la forma verbal exacta que vas a necesitar constantemente.

## 🏛️ Horizonte-Cultural

_(no lo vas a "usar" en un commit, pero te da contexto y entrena tu oído)_

- **El inglés es inusualmente estricto con esta distinción** — muchos idiomas (incluido el español, hasta cierto punto) no marcan tan obligatoriamente la diferencia entre "hago" y "estoy haciendo"; lingüistas consideran esta distinción obligatoria del inglés (llamada _aspecto gramatical_) una de las cosas que más cuesta a hispanohablantes dominar de forma natural.
- **Los verbos de estado y la filosofía detrás de la regla** — la razón lingüística de por qué "know" no va en `-ing` es que el `-ing` implica una acción con principio y fin visible en proceso; "saber algo" no es un proceso que se esté "haciendo" activo a activo, es un estado — de ahí el nombre _stative verbs_.
- **"Always + continuo" como recurso emocional del idioma** — el uso de `always` con presente continuo para quejarse (`he is always breaking things`) es un ejemplo de cómo la gramática no solo comunica hechos, también comunica actitud y emoción del hablante — algo que rara vez se enseña en cursos formales de gramática.

---

## 🧠 Prompts para tu Tutor IA (NotebookLM)

**Modo Express** _(quiero repasar rápido el núcleo)_

> "Actúa como un profesor directo. Basándote únicamente en esta fuente, resume la diferencia entre presente simple y presente continuo, cómo se construye, y los verbos de estado que no van en -ing, con un ejemplo de cada uno."

**Modo Ingeniero** _(quiero conectar esto con mi trabajo como dev)_

> "De los temas listados en 'Horizonte-Aplicado' de esta fuente, ayúdame a practicar reportando avance de trabajo en presente continuo, como si estuviera en un daily standup, usando ejemplos técnicos reales."

**Modo Escéptico** _(quiero que me examinen)_

> "Actúa como un profesor escéptico y directo. Basándote únicamente en esta fuente, dame 5 oraciones donde tenga que elegir entre presente simple y presente continuo según el contexto, y al menos una con un verbo de estado donde el error común sería usar -ing. Corrígeme con el porqué, sin darme la respuesta antes de que yo intente."

**Modo Expansión** _(quiero más de lo que dice la lección)_

> "Esta fuente es la base mínima. Dame 10 ejemplos adicionales contrastando presente simple y continuo en contextos técnicos y cotidianos, y una lista ampliada de verbos de estado más allá de los que aparecen aquí."

---

## 🎯 Reto de la Comunidad

Antes de pasar a la Lección 2.2, responde esto en el canal de la materia:

1. Elige presente simple o continuo según el contexto: `She (to code) ___ in Python.` (hecho general sobre su trabajo) vs. `She (to code) ___ right now, don't interrupt her.`
2. Explica por qué esta oración está mal y corrígela: `I am knowing how to fix this bug.`
3. Escribe 3 oraciones como si estuvieras reportando tu avance en un standup de trabajo, usando presente continuo.

> **Regla de la comunidad:** No postees la respuesta directa de otros. Si alguien se equivoca, dale una pista, no la solución.

---

Siguiente lección → **2.2: Pasado Simple y Continuo — Leyendo el Historial**
