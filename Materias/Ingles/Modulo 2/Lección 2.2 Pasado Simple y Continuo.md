# Inglés Técnico — Módulo 2 — Lección 2.2: Pasado Simple y Continuo (Leyendo el Historial)

> **"Un changelog es, gramaticalmente, una lista de oraciones en pasado. Si dominas esta lección, puedes leer el historial completo de cualquier proyecto sin traductor."**
> 
> En la 2.1 aprendiste a describir el presente en dos velocidades. Aquí hacemos exactamente lo mismo, pero mirando hacia atrás: qué pasó, y qué estaba pasando cuando pasó otra cosa.

---

## 🎚️ Ubicación en el mapa

- **Módulo:** 2 — State Management (El Inglés en Movimiento)
- **Nivel de esta lección:** Fundamento
- **Requiere haber visto:** Lección 1.3 (Presente Simple, para contrastar la regla de conjugación) y 2.1 (Presente Continuo, misma lógica de "to be + -ing" aplicada aquí en pasado).

---

## 🔩 Núcleo (lo esencial, no se salta)

### 0. Pasado Simple: la forma base para contar qué pasó

El pasado simple describe una acción que **ya terminó**, en un punto específico del pasado.

```
I worked yesterday.
The server crashed at midnight.
```

**Verbos regulares:** se forman agregando `-ed` al verbo base — la regla más común, y la buena noticia es que la mayoría de los verbos en inglés son regulares.

```
work   → worked
install → installed
load   → loaded
```

**Regla de ortografía (igual lógica que el `-ing` de la 2.1):**

```
stop  → stopped     (consonante final se duplica en sílaba corta acentuada)
try   → tried        ("y" al final cambia a "i" antes de -ed)
```

---

### 1. Verbos irregulares: se memorizan, no se deducen

Un grupo grande y muy usado de verbos **no** sigue la regla del `-ed`. Estos tienes que memorizarlos por exposición, no hay patrón lógico que deducir (parecido a los plurales irregulares que viste en la 1.2):

```
go    → went        (no "goed")
have  → had
do    → did
make  → made
break → broke
```

**Por qué te importa esto de forma práctica:** los verbos irregulares más comunes en inglés son, precisamente, los que más vas a usar en documentación técnica y conversación (`go`, `have`, `do`, `make`, `break`, `find`, `get`). No es mala suerte — los verbos más usados de cualquier idioma tienden a ser los más irregulares (el mismo fenómeno que viste con `to be` en la Lección 1.3).

```
The build failed because a dependency broke.
The team found the bug yesterday.
```

---

### 2. Negativo y pregunta en pasado simple: mismo patrón que el presente

Igual que en presente simple (Lección 1.3), se usa un auxiliar — aquí es `did`, y **no importa si el verbo es regular o irregular**, el auxiliar siempre es el mismo.

```
Afirmativo:  The server crashed.
Negativo:    The server did not crash.   → The server didn't crash.
Pregunta:    Did the server crash?
```

**Regla crítica:** cuando usas `did`, el verbo principal regresa a su forma base — pierde el `-ed` o la forma irregular.

```
✅ Did you install the update?
❌ Did you installed the update?
```

Es la misma lógica que viste con `does` en presente simple (Lección 1.3): el auxiliar carga toda la información de tiempo, el verbo principal se queda "limpio".

---

### 2. Pasado Continuo: una acción interrumpida por otra

El pasado continuo se construye exactamente igual que el presente continuo de la 2.1, solo que con `was`/`were` en vez de `am`/`is`/`are`:

```
[SUJETO] + [was/were] + [verbo + -ing]

I    was    working
He   was    working
We   were   working
They were   working
```

**Su uso más importante:** describir una acción **en progreso** en el pasado, que fue interrumpida por otra acción (en pasado simple).

```
I was debugging the code when the server crashed.
     [pasado continuo: acción en curso]      [pasado simple: acción que interrumpió]
```

Esta combinación (continuo + simple) es extremadamente común al narrar incidentes técnicos: "estaba pasando X, cuando pasó Y".

```
The application was running fine until the update broke it.
The team was reviewing the code when they found the vulnerability.
```

---

### 3. Conectores de tiempo útiles para narrar una secuencia

Para leer o escribir un historial completo (varios eventos en orden), estos conectores son los que vas a ver constantemente:

```
then       →  luego         First we deployed, then we tested.
after that →  después de eso  We fixed the bug. After that, we redeployed.
before     →  antes          Before the crash, everything was working fine.
while      →  mientras       While the server was restarting, users lost connection.
```

```
First, the team identified the bug. Then, they wrote a fix.
After that, they tested it locally before deploying to production.
```

---

### 4. Leyendo un changelog real (aplicando todo lo del módulo hasta aquí)

```
"Version 2.3.1 fixed a critical bug that was causing the application
to crash when users uploaded large files. The team was investigating
the issue for two days before they found the root cause. After the fix
was deployed, the crash rate dropped significantly."
```

Descompuesto:

- `fixed`, `was causing`, `found`, `was deployed`, `dropped` → mezcla de pasado simple y continuo
- `was causing` → pasado continuo (el problema que venía ocurriendo)
- `was investigating... before they found` → acción en curso interrumpida/seguida por otra
- `after` → conector de secuencia

No necesitaste vocabulario nuevo para leer esto — necesitabas exactamente la gramática de esta lección.

---

### 5. Recapitulación

```
Pasado Simple → -ed (regular) o forma irregular (memorizar) → acción terminada
    ↓
Negativo/pregunta con "did" → el verbo principal regresa a su forma base
    ↓
Pasado Continuo → was/were + verbo-ing → acción en curso, interrumpida
    ↓
Conectores de secuencia (then, after, before, while)
    ↓
Changelog / historial de commits = esta lección aplicada directamente
```

Con esto ya puedes leer cualquier historial de cambios, log de incidentes, o changelog técnico sin depender de traductor — que es, literalmente, uno de los documentos que más vas a leer como developer.

---

## 🌌 Horizonte-Aplicado

_(esto no lo cubrimos aquí, pero lo vas a necesitar más adelante como developer)_

- **Changelogs y release notes reales** — proyectos open source en GitHub publican constantemente notas de versión en pasado simple (`Fixed`, `Added`, `Removed`); ya tienes la base gramatical para leerlas sin esfuerzo.
- **Post-mortems de incidentes técnicos** — los reportes de "qué salió mal" en un incidente de producción se escriben casi siempre en esta mezcla de pasado simple y continuo que acabas de ver, narrando la secuencia exacta de eventos.
- **Present Perfect (adelanto, no lo cubrimos a fondo aquí)** — vas a encontrar frases como `We have fixed this issue`, un tiempo verbal más (ni presente ni pasado puro) que conecta una acción pasada con el presente; lo verás con más profundidad más adelante, pero ya reconoces la diferencia con el pasado simple que sí dominaste aquí.

## 🏛️ Horizonte-Cultural

_(no lo vas a "usar" en un commit, pero te da contexto y entrena tu oído)_

- **Por qué los verbos irregulares sobreviven en un idioma** — lingüísticamente, los verbos más usados de cualquier idioma resisten más la "regularización" con el tiempo, porque se escuchan y repiten tanto que la gente los memoriza tal cual, sin necesidad de aplicarles una regla; por eso "go/went" sigue siendo irregular después de siglos, mientras verbos poco usados tienden a volverse regulares con el tiempo.
- **El inglés antiguo tenía muchos más verbos irregulares** — la mayoría de los verbos regulares actuales alguna vez fueron irregulares; el proceso de "regularización" (que un verbo irregular termine adoptando el patrón `-ed`) sigue ocurriendo lentamente incluso hoy.
- **Cómo otros idiomas narran secuencias de eventos** — algunos idiomas (como el chino mandarín) no marcan el tiempo verbal con conjugaciones en absoluto, y dependen completamente del contexto o de palabras como "ayer" para indicar cuándo pasó algo; comparar esto te ayuda a apreciar por qué el inglés necesita tanto los conectores de secuencia que viste arriba.

---

## 🧠 Prompts para tu Tutor IA (NotebookLM)

**Modo Express** _(quiero repasar rápido el núcleo)_

> "Actúa como un profesor directo. Basándote únicamente en esta fuente, resume pasado simple, pasado continuo, y los conectores de secuencia, con un ejemplo de cada uno."

**Modo Ingeniero** _(quiero conectar esto con mi trabajo como dev)_

> "De los temas listados en 'Horizonte-Aplicado' de esta fuente, dame un changelog real corto (inventado pero realista) de un proyecto de software, y ayúdame a descomponer qué tiempos verbales usa, como hicimos en el ejemplo de la lección."

**Modo Escéptico** _(quiero que me examinen)_

> "Actúa como un profesor escéptico y directo. Basándote únicamente en esta fuente, dame 5 oraciones donde tenga que elegir entre pasado simple y continuo, incluyendo al menos una con un verbo irregular. Corrígeme con el porqué, sin darme la respuesta antes de que yo intente."

**Modo Expansión** _(quiero más de lo que dice la lección)_

> "Esta fuente es la base mínima. Dame una lista de 20 verbos irregulares comunes en contexto técnico con su pasado, y 5 ejemplos adicionales combinando pasado simple y continuo en la misma oración."

---

## 🎯 Reto de la Comunidad

Antes de pasar a la Lección 2.3, responde esto en el canal de la materia:

1. Convierte a negativo y a pregunta: `The team deployed the update.`
2. Completa con la forma correcta (pasado simple o continuo): `The application (to run) ___ fine when the update (to break) ___ it.`
3. Encuentra un changelog o release notes real de cualquier proyecto open source, pega 2-3 líneas en el canal, e identifica qué tiempos verbales usa.

> **Regla de la comunidad:** No postees la respuesta directa de otros. Si alguien se equivoca, dale una pista, no la solución.

---

Siguiente lección → **2.3: Futuro — Will vs. Going To (Predicciones vs. Planes)**
