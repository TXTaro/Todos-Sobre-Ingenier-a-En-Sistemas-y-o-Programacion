# Programación — Módulo 1 — Lección 1.3: Estructuras de Control (Condicionales)

> **"En la 1.1 le llamamos 'selección'. Aquí por fin tiene nombre real: if/else. Es la forma en que tu programa deja de hacer siempre lo mismo y empieza a decidir."**
> 
> Esta lección formaliza en código real algo que ya construiste dos veces sin saberlo: en Matemáticas 1.2 con las inecuaciones, y en Programación 1.1 con la estructura de "selección" en pseudocódigo. Aquí se convierte, por fin, en algo que puedes ejecutar.

---

## 🎚️ Ubicación en el mapa

- **Módulo:** 1 — The Core Logic (Fundamentos del Pensamiento)
- **Nivel de esta lección:** Fundamento
- **Requiere haber visto:** Lección 1.1 (Pensamiento Computacional, en especial la estructura de "Selección") y 1.2 (Variables y Tipos de Datos, en especial el tipo `bool`).

---

## 🔩 Núcleo (lo esencial, no se salta)

### 0. De la inecuación matemática al `if` de código

Recuerda Matemáticas 1.2:

```
x > 7
```

Esto no es un número — es una **afirmación que puede ser verdadera o falsa** dependiendo del valor de x. En programación, esa misma afirmación se llama **condición**, y su resultado siempre es del tipo `bool` que viste en la Lección 1.2 (`True` o `False`).

```python
x = 10
print(x > 7)   # True
```

El `if` es simplemente: _"si esta condición es verdadera, ejecuta este bloque de código."_

---

### 1. La estructura básica del `if`

```python
edad = 20

if edad >= 18:
    print("Puedes votar")
```

Desglosado:

- `if` → la palabra clave que arranca la decisión.
- `edad >= 18` → la condición (recuerda los símbolos de Matemáticas 1.2: `>`, `<`, `>=`, `<=`, y aquí también `==` para "igual a").
- `:` → indica que empieza el bloque que se ejecuta si la condición es verdadera.
- La línea con sangría (indentación) debajo → es el código que se ejecuta SOLO si la condición es `True`.

**La indentación en Python no es estética — es obligatoria.** A diferencia de otros lenguajes que usan `{ }` para marcar bloques, Python usa espacios/tabulaciones consistentes. Si te equivocas en la indentación, el programa no corre.

---

### 2. `else`: el camino alternativo

```python
edad = 15

if edad >= 18:
    print("Puedes votar")
else:
    print("No puedes votar")
```

Esto es exactamente el `SINO` que viste en pseudocódigo en la Lección 1.1. Si la condición del `if` es falsa, se ejecuta el bloque del `else` en su lugar. **Nunca se ejecutan ambos** — es uno u otro, nunca los dos.

---

### 3. `elif`: cuando hay más de dos caminos

A veces necesitas más de dos posibilidades. Para eso existe `elif` (contracción de "else if"):

```python
calificacion = 75

if calificacion >= 90:
    print("Excelente")
elif calificacion >= 70:
    print("Aprobado")
else:
    print("Reprobado")
```

**Cómo se evalúa esto (orden importa):** Python revisa las condiciones de arriba hacia abajo, y en cuanto encuentra una verdadera, ejecuta ese bloque y **deja de revisar las demás**, aunque otra condición de más abajo también fuera verdadera.

```python
calificacion = 95

if calificacion >= 90:
    print("Excelente")     # esto se ejecuta
elif calificacion >= 70:
    print("Aprobado")       # esto NUNCA se revisa, aunque 95 >= 70 también es verdadero
```

Este detalle es una fuente común de bugs para quien empieza: el orden de tus condiciones cambia el resultado.

---

### 4. Operadores de comparación (recordatorio directo de Matemáticas)

```python
==   igual a          (ojo: NO confundir con = que es asignación)
!=   distinto de
>    mayor que
<    menor que
>=   mayor o igual que
<=   menor o igual que
```

**El error más común de quien empieza a programar:**

```python
if edad = 18:    ❌ SyntaxError — esto es asignación, no comparación
if edad == 18:   ✅ esto sí compara si edad vale 18
```

Un solo `=` asigna un valor a una variable. Dos `==` preguntan si dos valores son iguales. Son operaciones completamente distintas que se ven parecidas — préstale atención a este detalle desde ahora, te va a ahorrar horas de confusión.

---

### 5. Operadores lógicos: combinando condiciones

Recuerda que en el Horizonte-Aplicado de Matemáticas 1.2 mencionamos el álgebra booleana — aquí es donde la usas directo:

```python
and   → ambas condiciones deben ser verdaderas
or    → al menos una condición debe ser verdadera
not   → invierte el valor (True se vuelve False y viceversa)
```

```python
edad = 25
tiene_identificacion = True

if edad >= 18 and tiene_identificacion:
    print("Puede entrar")
```

Aquí SOLO entra si las dos condiciones son verdaderas al mismo tiempo. Si cualquiera de las dos es falsa, no entra.

```python
es_fin_de_semana = True
es_feriado = False

if es_fin_de_semana or es_feriado:
    print("No hay clases")
```

Aquí basta con que UNA de las dos sea verdadera.

---

### 6. Condicionales anidados: un `if` dentro de otro `if`

```python
edad = 20
tiene_boleto = True

if edad >= 18:
    if tiene_boleto:
        print("Puede entrar al concierto")
    else:
        print("Necesita comprar boleto")
else:
    print("No cumple la edad mínima")
```

Esto es útil cuando la segunda decisión solo tiene sentido si la primera ya se cumplió. Ojo con anidar demasiados niveles — si tu código empieza a verse como una escalera de indentaciones, casi siempre se puede simplificar combinando condiciones con `and`/`or` (como viste arriba).

---

### 7. Recapitulación

```
Condición = una afirmación que evalúa a True o False (booleano)
    ↓
if → ejecuta un bloque SI la condición es verdadera
    ↓
else → ejecuta un bloque alternativo si la condición es falsa
    ↓
elif → evalúa condiciones adicionales, en orden, de arriba hacia abajo
    ↓
Operadores lógicos (and/or/not) → combinan varias condiciones
    ↓
Condicionales anidados → decisiones dentro de decisiones
```

Con esto tu programa ya puede **decidir**, no solo ejecutar pasos en línea recta. En la Lección 1.4 vas a agregar la última pieza que falta: hacer que algo se repita sin tener que escribirlo mil veces.

---

## 🌌 Horizonte-Aplicado

_(esto no lo cubrimos aquí, pero lo vas a necesitar más adelante en programación real)_

- **Match/switch statements** — algunos lenguajes (y Python desde versiones recientes, con `match`) tienen una forma alternativa de escribir muchos `elif` seguidos de forma más limpia cuando comparas una sola variable contra muchos valores posibles.
- **Validación de datos con condicionales** — casi cualquier formulario o input de usuario en software real usa cadenas de `if` para validar que los datos tengan sentido antes de procesarlos (edad no negativa, correo con formato válido, etc.) — es una de las aplicaciones más comunes de todo lo que viste aquí.
- **Cortocircuito lógico (short-circuit evaluation)** — cuando usas `and`/`or`, Python (y la mayoría de los lenguajes) dejan de evaluar condiciones en cuanto ya saben el resultado final; esto tiene implicaciones de eficiencia y hasta se usa como técnica intencional en código avanzado.

## 🏛️ Horizonte-Cultural

_(no lo vas a "usar" en un commit, pero te da contexto y entrena tu forma de pensar)_

- **George Boole y el álgebra que lleva su nombre** — el matemático británico del siglo XIX que formalizó la lógica verdadero/falso como un sistema matemático completo (de ahí "booleano"); no tenía ninguna computadora en mente cuando lo hizo — su trabajo se usó casi un siglo después para diseñar los circuitos digitales.
- **Por qué la indentación de Python genera tanto debate** — la decisión de usar espacios en vez de `{ }` para marcar bloques de código es una de las más controvertidas en la historia del diseño de lenguajes; algunos programadores la aman por forzar código legible, otros la odian por ser más rígida. Vale la pena que formes tu propia opinión con el tiempo.
- **El problema del "árbol de decisiones" en la vida real, no solo en código** — la lógica de if/else/elif que aprendiste aquí es la misma que usan los diagramas de flujo de decisiones médicas, procesos legales, o manuales de reparación; una vez que la entiendes en código, empiezas a notarla en instrucciones de la vida diaria.

---

## 🧠 Prompts para tu Tutor IA (NotebookLM)

**Modo Express** _(quiero repasar rápido el núcleo)_

> "Actúa como un profesor directo. Basándote únicamente en esta fuente, resume if/elif/else, los operadores de comparación y los operadores lógicos (and/or/not), con un ejemplo de código de cada uno."

**Modo Expansión** _(quiero más de lo que dice la lección)_

> "Esta fuente es la base mínima. Dame 8 ejercicios cortos de código con condicionales de dificultad creciente, empezando por if simple hasta condicionales anidados con and/or, sin darme las respuestas."

**Modo Ingeniero** _(quiero conectar esto con programación real)_

> "De los temas listados en 'Horizonte-Aplicado' de esta fuente, dame un ejemplo real de validación de un formulario (como un registro de usuario) usando exactamente la lógica de condicionales que vimos en el núcleo."

**Modo Curioso** _(quiero contexto e historia)_

> "Cuéntame sobre George Boole mencionado en el Horizonte-Cultural de esta fuente, y explícame la conexión directa entre su trabajo del siglo XIX y el 'if' que usé hoy en código."

**Modo Escéptico** _(quiero que me examinen)_

> "Actúa como un profesor escéptico y directo. Basándote únicamente en esta fuente, dame 5 fragmentos de código con condicionales y pídeme que prediga qué va a imprimir cada uno ANTES de ejecutarlos, incluyendo al menos uno con elif mal ordenado a propósito para ver si detecto el error. Corrígeme con el porqué, no me des la respuesta antes de que yo intente."

---

## 🎯 Reto de la Comunidad

Antes de pasar a la Lección 1.4, responde esto en el canal de la materia:

1. Escribe (en pseudocódigo o Python real) un condicional que clasifique una temperatura en "Frío" (menos de 15°C), "Templado" (15-25°C) o "Caluroso" (más de 25°C). Presta atención al orden de tus condiciones.
2. ¿Cuál es la diferencia exacta entre `=` y `==` en Python? Explícalo con un ejemplo de cada uno y qué pasa si los confundes.
3. Escribe una condición usando `and` y otra equivalente usando dos `if` anidados, que hagan exactamente lo mismo. ¿Cuál te parece más clara y por qué?

> **Regla de la comunidad:** No postees la respuesta directa de otros. Si alguien se equivoca, dale una pista, no la solución.

---

Siguiente lección → **1.4: Estructuras de Control — Bucles (for/while)**
