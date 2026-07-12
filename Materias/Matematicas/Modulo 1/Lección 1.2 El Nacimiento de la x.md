# Matemáticas Aplicadas — Módulo 1 — Lección 1.2: El Nacimiento de la x

> **"Una variable en matemáticas es exactamente lo mismo que una variable en código: una caja con un nombre que guarda un valor que aún no conoces, o que puede cambiar."**
> 
> Esta lección es el puente. Aquí es donde las matemáticas dejan de ser solo contar manzanas y se convierten en una herramienta para resolver cualquier problema del universo. Si alguna vez te preguntaste por qué de repente aparecen letras en las ecuaciones, aquí está la respuesta lógica.

---

## 🎚️ Ubicación en el mapa

- **Módulo:** 1 — El Taller de Reparación (Bases desde Cero)
- **Nivel de esta lección:** Fundamento
- **Requiere haber visto:** Lección 1.1 (Cimientos de la Aritmética) — sin las 4 operaciones y sus inversas, despejar no tiene sentido.

---

## 🔩 Núcleo (lo esencial, no se salta)

### 0. ¿Por qué inventamos las letras en matemáticas?

Imagina que eres un comerciante en el año 800 d.C. y tienes este problema:

> _"Compré una bolsa de trigo. Le vendí 15 kg a un cliente y me quedaron 40 kg. ¿Cuánto pesaba la bolsa original?"_

Con aritmética pura lo resuelves mentalmente: `40 + 15 = 55 kg`. Fácil.

Ahora imagina que tienes 300 problemas similares al día, todos distintos. Necesitas una forma de escribir la **estructura del problema** una sola vez y reutilizarla con cualquier número.

Eso hicieron los matemáticos: inventaron un símbolo para representar "el número que no sé todavía". Le llamaron **incógnita**, y con el tiempo usamos letras para representarla. La más famosa: **x**.

> Esto es literalmente lo mismo que declarar una variable en código:

```python
bolsa_original = None       # aún no sé su valor
bolsa_original = 40 + 15    # ahora lo resuelvo
```

---

### 1. La Incógnita vs. La Variable: ¿Son lo mismo?

Casi, pero hay una diferencia importante:

**Incógnita:** un valor fijo que no conoces _todavía_. El objetivo es encontrarlo.

```
x + 15 = 55    →    x = 40
```

Hay una sola respuesta correcta. La x no cambia, solo la descubrimos.

**Variable:** un valor que _puede cambiar_ dependiendo de la situación.

```
y = x + 15
```

Si x vale 10, y vale 25. Si x vale 30, y vale 45. La y depende de x. Esto es una **función** (lo verás a fondo en la Lección 1.4).

```python
# Incógnita: buscar un valor específico
# Variable: almacenar un valor que cambia
temperatura = 0
temperatura = temperatura + 5   # la variable cambió
```

---

### 2. Expresiones Algebraicas: Hablar el idioma

Una **expresión algebraica** es una combinación de números, variables y operaciones. No tiene signo de igual, solo describe una cantidad.

```
3x + 2
```

Se lee: "tres veces un número, más dos". No sabemos qué es x todavía, pero sabemos la estructura.

**Partes de una expresión:**

- **Término:** cada parte separada por suma o resta. En `3x + 2` hay dos: `3x` y `2`.
- **Coeficiente:** el número que multiplica a la variable. En `3x`, el coeficiente es `3`.
- **Término independiente (constante):** el número solo, sin variable. En `3x + 2`, el `2`.

**Términos semejantes:** los que tienen la misma variable con el mismo exponente. Solo estos se pueden sumar o restar entre sí.

```
3x + 5x = 8x        ✅  (misma variable, se suman los coeficientes)
3x + 5y = 3x + 5y   ✅  (diferente variable, no se combinan)
3x² + 5x = 3x² + 5x ✅  (diferente exponente, no se combinan)
```

Es idéntico a intentar sumar tipos de datos incompatibles en código:

```python
"hola" + 3   # TypeError: no puedes sumar string con int
```

Misma lógica: solo se operan cosas del mismo tipo.

---

### 3. Ecuaciones: Cuando aparece el signo igual

Una **ecuación** es una afirmación de que dos expresiones son iguales. El signo "=" es el corazón de todo.

```
3x + 2 = 14
```

Dice: "existe un valor de x tal que, si lo multiplico por 3 y le sumo 2, obtengo 14".

Imagina una balanza:

```
[ 3x + 2 ]  =  [ 14 ]
```

Regla de oro: **lo que hagas de un lado, lo haces del otro con el signo contrario**. Si no, la balanza se desequilibra y la ecuación deja de ser verdad.

---

### 4. Despejar la Incógnita: El Arte de Aislar la x

Despejar significa dejar la variable sola de un lado del igual, usando las **operaciones inversas** vistas en la 1.1.

Estrategia: **deshacer lo que le hicieron a la x, en orden inverso**.

**Ejemplo 1 — Nivel básico:**

```
x + 5 = 12
x + 5 - 5 = 12 - 5
x = 7

Verificación: 7 + 5 = 12   ✅
```

**Ejemplo 2 — Dos pasos:**

```
3x + 2 = 14
3x + 2 - 2 = 14 - 2   → 3x = 12
3x ÷ 3 = 12 ÷ 3       → x = 4

Verificación: 3(4) + 2 = 14   ✅
```

**Ejemplo 3 — La x en ambos lados:**

```
5x - 3 = 2x + 9
5x - 2x - 3 = 9   → 3x - 3 = 9
3x = 12
x = 4

Verificación: 5(4) - 3 = 17  y  2(4) + 9 = 17   ✅
```

---

### 5. La Propiedad Distributiva: El operador que abre paréntesis

```
2(x + 3) = 2x + 6
```

El número de afuera multiplica a **cada término** de adentro.

```
Ecuación completa:
2(x + 3) = 16
2x + 6 = 16       ← distribuyes primero
2x = 10           ← restas 6
x = 5             ← divides entre 2

Verificación: 2(5 + 3) = 16   ✅
```

---

### 6. Inecuaciones: Cuando no hay igualdad exacta

```
x + 3 > 10
```

Dice: "x es un número tal que, si le sumas 3, el resultado es mayor que 10". La respuesta no es un número, es un conjunto de números.

```
x + 3 > 10
x > 7
```

Cualquier número mayor que 7 funciona: `8, 9, 10, 100, 1000...`

**Los cuatro símbolos:**

```
>   mayor que        <   menor que
≥   mayor o igual     ≤   menor o igual
```

**Regla crítica:** si multiplicas o divides ambos lados por un número **negativo**, el símbolo se invierte.

```
-2x > 8
x < -4     ← el > se convirtió en <
```

¿Por qué? Porque al multiplicar por negativo, el orden numérico se voltea: si `2 > 1`, entonces `-2 < -1`.

```python
if temperatura > 90:
    print("Servidor sobrecalentado")
```

La inecuación vive dentro de cada `if` que escribes.

---

### 7. Recapitulación

```
Aritmética (Lección 1.1)
    → números fijos, operaciones concretas

Álgebra básica (Lección 1.2)
    → variables, expresiones, ecuaciones, inecuaciones
    → estructura general que funciona con cualquier número
```

Ahora describes problemas de forma abstracta, los resuelves una vez, y aplicas la misma lógica a mil situaciones distintas — exactamente lo que hace una función en programación.

---

## 🌌 Horizonte-Aplicado

_(esto no lo cubrimos aquí, pero lo vas a necesitar más adelante en ingeniería/programación)_

- **Sistemas de ecuaciones** — cuando tienes dos o más incógnitas relacionadas al mismo tiempo (`x + y = 10`, `x - y = 2`); es la base de resolver problemas con múltiples variables, desde física hasta modelos de negocio.
- **Álgebra booleana** — un tipo distinto de "álgebra" donde las variables solo valen verdadero/falso; es literalmente el ADN de cada `if`, `and`, `or` que escribas. Lo verás a fondo en el Módulo 2 (La Lógica de la Máquina).
- **Ecuaciones como restricciones (constraints)** — en optimización y en motores de videojuegos, "despejar" se convierte en resolver sistemas enormes de miles de ecuaciones a la vez; ahí es donde tu computadora hace el trabajo, pero necesitas entender la lógica para saber qué le estás pidiendo.
- **Pseudocódigo y álgebra** — la forma en que despejas paso a paso (`x = 7`) es idéntica a cómo se traza un algoritmo paso a paso antes de programarlo; despejar bien te entrena a pensar en pasos lógicos ordenados.

## 🏛️ Horizonte-Cultural

_(no lo vas a "usar" en un algoritmo, pero te da contexto y entrena tu forma de pensar)_

- **Al-Juabar y el origen de la palabra "álgebra"** — el término viene del árabe _al-jabr_, de un libro escrito en Bagdad en el siglo IX que literalmente significaba "reunificación de partes rotas"; despejar una ecuación es, en el sentido más literal, "reparar" un desequilibrio.
- **Por qué tardamos siglos en usar letras** — durante mucho tiempo los problemas algebraicos se escribían con puras palabras completas (álgebra retórica), sin ningún símbolo; los símbolos que usas hoy (`x`, `=`, `+`) son un invento relativamente reciente en la historia de las matemáticas.
- **¿Por qué específicamente "x"?** — hay una teoría (con bastante debate histórico) de que viene de una mala transliteración de una palabra árabe al español antiguo; investigar esa historia es un buen ejercicio de cómo el lenguaje y las matemáticas se mezclan.
- **La balanza como metáfora universal** — la idea de "equilibrio" que viste en las ecuaciones aparece en física (equilibrio de fuerzas), en economía (oferta y demanda) y hasta en filosofía; es una de esas ideas que, una vez que la entiendes en matemáticas, la empiezas a ver en todos lados.

---

## 🧠 Prompts para tu Tutor IA (NotebookLM)

**Modo Express** _(quiero repasar rápido el núcleo)_

> "Actúa como un profesor directo. Basándote únicamente en esta fuente, resume el núcleo de esta lección en 5 minutos de lectura, con un ejemplo de despeje de cada tipo (básico, dos pasos, x en ambos lados). Sin rodeos."

**Modo Ingeniero** _(quiero conectar esto con programación)_

> "De los temas listados en 'Horizonte-Aplicado' de esta fuente, elige el que más se conecte con programación y explícamelo con un ejemplo de código real. Luego hazme una pregunta para comprobar que lo entendí."

**Modo Curioso** _(quiero contexto e historia)_

> "De los temas listados en 'Horizonte-Cultural' de esta fuente, elige uno y cuéntame su historia como una anécdota interesante, no una clase aburrida. Al final, dime por qué eso ayuda a entender mejor el núcleo de la lección."

**Modo Escéptico** _(quiero que me examinen)_

> "Actúa como un profesor de matemáticas escéptico y directo. Basándote únicamente en esta fuente, hazme un examen de 5 preguntas: mezcla opción múltiple, despejes paso a paso, y al menos una donde tenga que explicar con mis propias palabras por qué el símbolo de una inecuación se invierte al multiplicar por negativo. Después de cada respuesta mía, dame retroalimentación y el porqué, nunca la respuesta directa antes de que yo intente."

---

## 🎯 Reto de la Comunidad

Antes de pasar a la Lección 1.3, responde esto en el canal de la materia:

1. Resuelve y verifica: `4(x - 2) + 3 = 19`
2. ¿Por qué al dividir entre un número negativo en una inecuación se invierte el símbolo? Explícalo con un ejemplo numérico concreto, sin copiar la explicación de la lección.
3. En programación, ¿en qué parte de un `for` o un `while` vive una inecuación? Escribe un ejemplo en el lenguaje que quieras y señala exactamente dónde está.

> **Regla de la comunidad:** No postees la respuesta directa. Si alguien se equivoca, dale una pista, no la solución.

---

Siguiente lección → **1.3: Exponentes y Raíces — Visualizando el Poder**
