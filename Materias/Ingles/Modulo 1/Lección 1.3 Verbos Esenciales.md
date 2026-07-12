# Inglés Técnico — Módulo 1 — Lección 1.3: Verbos Esenciales (To Be, Presente Simple e Imperativo)

> **"Si el sustantivo es el dato, el verbo es la función que lo mueve. Sin verbo, no hay acción — solo una lista de cosas quietas."**
> 
> En la 1.2 aprendiste a ordenar las piezas. Aquí es donde esas piezas por fin **hacen algo**. Vamos a ver tres formas verbales — no todas las que existen, solo las tres que vas a usar el 90% del tiempo en documentación técnica, mensajes de error, y conversación básica.

---

## 🎚️ Ubicación en el mapa

- **Módulo:** 1 — The Developer's Syntax (Fundamentos Esenciales)
- **Nivel de esta lección:** Fundamento
- **Requiere haber visto:** Lección 1.1 (Los Cimientos) y 1.2 (Estructura de la Oración) — aquí metemos el verbo real dentro del orden S-V-O que ya conoces.

---

## 🔩 Núcleo (lo esencial, no se salta)

### 0. Por qué empezamos con solo tres formas verbales

El inglés tiene 12 tiempos verbales formales. No los vas a ver todos aquí, y **no los necesitas todos** para empezar a leer documentación o escribir algo funcional. Con **to be**, **presente simple** e **imperativo** ya puedes describir cosas, hablar de hechos generales, y dar/recibir instrucciones — que es literalmente el 90% de lo que hace un manual técnico, un README o un mensaje de error.

---

### 1. El verbo "To Be" — el verbo más importante del idioma

`To be` significa "ser/estar", y es el único verbo en inglés que cambia de forma según quién hace la acción (casi todos los demás verbos no cambian tanto, como verás en la sección 2).

```
I    am     yo soy/estoy
You  are    tú eres/estás
He   is     él es/está
She  is     ella es/está
It   is     eso es/está
We   are    nosotros somos/estamos
They are    ellos son/están
```

**Usos principales:**

**Describir algo (adjetivo):**

```
The code is clean.
I am tired.
```

**Decir dónde está algo (ubicación):**

```
The server is in Germany.
```

**Decir qué es algo (identidad/profesión):**

```
She is a developer.
```

**Forma negativa:** agregas `not` después del verbo.

```
I am not ready.
The server is not responding.
```

**Contracciones (muy comunes, las vas a ver todo el tiempo):**

```
I am        → I'm
You are     → You're
He is       → He's
It is       → It's
is not      → isn't
are not     → aren't
```

---

### 2. Presente Simple — hechos generales y verdades

El presente simple describe cosas que son **verdad en general**, no algo que está pasando ahora mismo. En español no siempre distinguimos esto tan claro, pero en inglés es una distinción real que verás en la Lección 1.4/Módulo 2.

```
I work.        (trabajo, en general, es mi rutina)
She codes.     (ella programa, es su trabajo/hábito)
```

**La regla que sí tienes que memorizar:** con `he/she/it`, el verbo agrega una `-s` (o `-es`) al final.

```
I    work         He   works
You  work         She  codes
We   work         It   runs
They work
```

```
watch → watches      (termina en sonido "ch", agrega -es, igual que los plurales de la 1.2)
```

**Forma negativa:** aquí NO se pone `not` directo después del verbo (como en `to be`) — se usa un verbo "auxiliar" (`do`/`does`) que carga la negación.

```
I do not work.        → I don't work.
She does not code.    → She doesn't code.
```

Fíjate: cuando usas `does`, el verbo principal **pierde** la `-s` (`does not code`, no `does not codes`). Es una regla que se ve rara al inicio pero se vuelve automática rápido.

**Forma de pregunta:** el mismo auxiliar se mueve al frente.

```
Do you work here?
Does she code in Python?
```

---

### 3. Imperativo — dar instrucciones y comandos

Esta es, sin exagerar, **la forma verbal más importante para leer documentación técnica.** Casi cualquier manual, README o tutorial está lleno de imperativos.

**La buena noticia:** el imperativo es la forma MÁS simple de todas — usas el verbo en su forma base, sin conjugar, sin sujeto explícito.

```
Install the package.
Run the command.
Open the terminal.
Save the file.
Don't delete this folder.
```

No hay "tú instala" o "usted instale" como en español — es solo el verbo, directo, sin adornos. El sujeto (`you`, implícito) ni siquiera se escribe.

**Negativo:** se agrega `don't` antes del verbo.

```
Don't run this in production.
Don't forget to commit your changes.
```

**Por qué esto te va a ahorrar dolores de cabeza:** cuando abras documentación en inglés y veas puro verbo al inicio de cada línea (`Install...`, `Configure...`, `Run...`), ya sabes que no es un error de gramática ni te estás perdiendo un sujeto — es la estructura normal y esperada de instrucciones técnicas.

---

### 4. Comparando las tres formas lado a lado

```
TO BE:            The server is slow.
                   (describe un estado)

PRESENTE SIMPLE:   The server processes requests.
                   (describe qué hace, en general)

IMPERATIVO:        Restart the server.
                   (da una instrucción directa)
```

Las tres usan el mismo orden S-V-O que ya conoces de la 1.2 — la diferencia está en la forma del verbo y, en el imperativo, en que el sujeto desaparece.

---

### 5. Recapitulación

```
To Be (am/is/are) → describir, ubicar, identificar
    ↓
Presente Simple (+s con he/she/it) → hechos generales, rutinas
    ↓
Negativo/pregunta con presente simple → auxiliar do/does
    ↓
Imperativo (verbo base, sin sujeto) → instrucciones y comandos
```

Con esto ya puedes leer y escribir la inmensa mayoría de instrucciones técnicas básicas, describir cosas, y hablar de hechos generales. La Lección 1.4 cierra el módulo uniendo todo esto en lectura y vocabulario más amplio.

---

## 🌌 Horizonte-Aplicado

_(esto no lo cubrimos aquí, pero lo vas a necesitar más adelante como developer)_

- **El imperativo en mensajes de commit** — la convención más usada en la industria es escribir commits en imperativo (`Fix bug`, no `Fixed bug` ni `Fixes bug`); ahora ya entiendes por qué esa convención existe y de dónde sale gramaticalmente. La verás a fondo en el Módulo 3 (Git Commit & Writing).
- **"Is/Are" en mensajes de estado de sistemas** — vas a leer constantemente cosas como `Service is running`, `Servers are down`; es literalmente `to be` aplicado a infraestructura.
- **Presente simple en documentación de funciones** — la documentación técnica casi siempre describe qué hace una función en presente simple genérico (`This function returns a value`, no `This function is returning`); es la forma estándar de describir comportamiento esperado, no una acción puntual.

## 🏛️ Horizonte-Cultural

_(no lo vas a "usar" en un commit, pero te da contexto y entrena tu oído)_

- **Por qué "to be" es tan irregular** — casi todos los idiomas indoeuropeos (inglés, español, francés, alemán...) tienen un verbo "ser/estar" extremadamente irregular; se cree que es porque es de los verbos más antiguos y usados del idioma, y los verbos muy usados resisten más los cambios de "regularización" con el tiempo.
- **El imperativo y el poder en el lenguaje** — lingüísticamente, el imperativo es la forma verbal más directa de ejercer autoridad o urgencia en cualquier idioma; pensar en por qué la documentación técnica "manda" en vez de "sugerir" (compara `Install the package` vs `You could install the package`) dice algo interesante sobre la cultura de la ingeniería: directa, sin rodeos.
- **Idiomas donde no existe el verbo "ser/estar" como lo conoces** — el ruso, por ejemplo, casi no usa el verbo "to be" en presente ("I am a doctor" se dice más cercano a "I doctor"); investigar esto te ayuda a notar que ni siquiera un verbo tan "básico" como este es universal en todos los idiomas.

---

## 🧠 Prompts para tu Tutor IA (NotebookLM)

**Modo Express** _(quiero repasar rápido el núcleo)_

> "Actúa como un profesor directo. Basándote únicamente en esta fuente, dame la conjugación completa de to be, la regla de la -s en presente simple, y 3 ejemplos de imperativo, todo en un resumen rápido."

**Modo Expansión** _(quiero más de lo que dice la lección)_

> "Esta fuente es la base mínima. Dame 15 ejemplos adicionales mezclando to be, presente simple e imperativo en contextos cotidianos (no técnicos), y explícame los errores más comunes que cometen hispanohablantes con estas tres formas."

**Modo Ingeniero** _(quiero conectar esto con mi trabajo como dev)_

> "De los temas listados en 'Horizonte-Aplicado' de esta fuente, dame 10 ejemplos reales de mensajes de commit en imperativo correctamente escritos, y explícame por qué esa convención se volvió estándar en la industria."

**Modo Curioso** _(quiero contexto e historia)_

> "Explícame, basándote en el Horizonte-Cultural de esta fuente, por qué el verbo 'to be' es tan irregular comparado con otros verbos del inglés, y dame un ejemplo de otro idioma donde pase algo parecido."

**Modo Escéptico** _(quiero que me examinen)_

> "Actúa como un profesor escéptico y directo. Basándote únicamente en esta fuente, hazme un examen de 5 preguntas: conjugación de to be, formar negativos con does, convertir una oración normal a imperativo, y una donde tenga que explicar con mis palabras por qué el imperativo no lleva sujeto. Corrígeme con el porqué, sin darme la respuesta antes de que yo intente."

---

## 🎯 Reto de la Comunidad

Antes de pasar a la Lección 1.4, responde esto en el canal de la materia:

1. Conjuga correctamente: `She (to be) ___ a developer.` / `They (to be) ___ tired.` / `It (to be) ___ not working.`
2. Convierte a negativo: `He codes every day.` → ?
3. Escribe 3 instrucciones en imperativo como si fueran parte de un mini-manual para instalar algo (real o inventado).

> **Regla de la comunidad:** No postees la respuesta directa de otros. Si alguien se equivoca, dale una pista, no la solución.

---

Siguiente lección → **1.4: Vocabulario y Lectura — Armando y Leyendo Oraciones Completas**
