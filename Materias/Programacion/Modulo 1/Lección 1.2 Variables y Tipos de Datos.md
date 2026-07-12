# Programación — Módulo 1 — Lección 1.2: Variables y Tipos de Datos (De la Incógnita al Código Real)

> **"En la Lección 1.2 de Matemáticas viste que x era una caja que guarda un valor. Aquí esa caja por fin existe de verdad — y tiene nombre, tipo, y la puedes crear con una sola línea."**
> 
> Esta es la primera lección del temario donde vas a escribir código real. Vamos a usar **Python** como lenguaje base (el mismo que hemos usado en ejemplos desde Matemáticas), no porque sea "el mejor" de forma absoluta, sino porque su sintaxis es de las más cercanas al pseudocódigo que ya dominas desde la 1.1.

---

## 🎚️ Ubicación en el mapa

- **Módulo:** 1 — The Core Logic (Fundamentos del Pensamiento)
- **Nivel de esta lección:** Fundamento
- **Requiere haber visto:** Lección 1.1 (Pensamiento Computacional) — aquí traducimos el pseudocódigo y la lógica que ya construiste a sintaxis real.

---

## 🔩 Núcleo (lo esencial, no se salta)

### 0. De la incógnita matemática a la variable de programación

Recuerda Matemáticas 1.2:

```
x = 40 + 15
```

Ahí `x` era una caja que guardaba un valor. En programación, esa misma idea existe, con una diferencia clave: en matemáticas casi siempre buscas **un** valor específico (la incógnita). En programación, casi siempre usas la variable como **contenedor que va a cambiar** durante la ejecución del programa.

```python
edad = 25
```

Esto crea una caja llamada `edad`, le mete el valor `25`. Nada mágico — es exactamente `x = 25`, solo que con un nombre más descriptivo que "x".

**Regla de nombres en Python:** no pueden empezar con número, no pueden tener espacios (se usa `_` en su lugar), y por convención se escriben en minúsculas.

```python
edad = 25            ✅
nombre_usuario = "Ana"   ✅
2edad = 25            ❌ (no puede empezar con número)
nombre usuario = "Ana"    ❌ (no puede tener espacio)
```

---

### 1. Tipos de Datos: no todas las cajas guardan lo mismo

Así como en Matemáticas distinguiste números enteros, fracciones y decimales, en programación cada variable tiene un **tipo de dato** — la computadora necesita saber qué tipo de información estás guardando para saber qué operaciones puede hacer con ella.

#### 1.1 Enteros (`int`) — números sin decimales

```python
edad = 25
cantidad_de_servidores = 4
```

#### 1.2 Decimales (`float`) — números con punto decimal

```python
precio = 19.99
temperatura = 36.5
```

Recuerda el Horizonte-Aplicado de Matemáticas 1.1: la precisión de estos decimales en la computadora no siempre es perfecta (`0.1 + 0.2` no da exactamente `0.3`). Ese detalle técnico existe precisamente por cómo se guardan los `float` en la memoria.

#### 1.3 Texto (`str`, de "string") — cadenas de caracteres

```python
nombre = "Ana"
mensaje = 'El servidor está activo'
```

Se escriben entre comillas (simples o dobles, Python acepta ambas). Cualquier cosa entre comillas es texto, aunque parezca un número:

```python
codigo_postal = "01000"   # esto es texto, no un número
```

¿Por qué guardarías un número como texto? Porque no vas a hacer operaciones matemáticas con un código postal — nunca vas a "sumar" dos códigos postales. El tipo de dato describe **qué puedes hacer** con el valor, no solo qué se ve.

#### 1.4 Booleanos (`bool`) — verdadero o falso

```python
esta_activo = True
tiene_permiso = False
```

Esto es la formalización directa de la **selección** que viste en la 1.1 (`SI condición ENTONCES...`). Un booleano solo puede valer `True` o `False`, nada más — es el tipo de dato que vas a usar constantemente en la Lección 1.3 de este módulo.

---

### 2. Verificando el tipo de una variable

Python te deja preguntar directamente qué tipo de dato tiene una variable:

```python
edad = 25
print(type(edad))        # <class 'int'>

nombre = "Ana"
print(type(nombre))       # <class 'str'>
```

Esto es útil cuando no estás seguro de con qué tipo de dato estás trabajando — algo que vas a hacer seguido al depurar errores.

---

### 3. Operaciones según el tipo de dato

Recuerda Matemáticas 1.2 con el error de tipos:

```python
"hola" + 3   # TypeError: no puedes sumar string con int
```

Este error no es un capricho de Python — es consistencia lógica. Sumar un número y una palabra no tiene un significado matemático claro, así que el lenguaje te detiene antes de que hagas algo sin sentido.

**Pero ojo, hay una operación válida entre texto y números que sorprende a mucha gente:**

```python
"ja" * 3    # 'jajaja'    ← multiplicar texto por un entero SÍ funciona, repite el texto
```

Esto es consistente con lo que aprendiste en Matemáticas 1.1: la multiplicación es suma repetida. Python literalmente "suma" (concatena) el texto consigo mismo 3 veces.

**Concatenar texto (unir dos strings) usa el mismo símbolo que sumar:**

```python
nombre = "Ana"
saludo = "Hola, " + nombre    # 'Hola, Ana'
```

---

### 4. Conversión de tipos (Type Casting)

A veces necesitas convertir un tipo de dato a otro. Python te da funciones directas para esto:

```python
edad_texto = "25"
edad_numero = int(edad_texto)     # convierte texto a entero: 25

precio = 19.99
precio_entero = int(precio)        # convierte decimal a entero: 19 (trunca, como viste en Matemáticas 1.1)

cantidad = 5
cantidad_texto = str(cantidad)      # convierte entero a texto: '5'
```

Esto es sumamente común cuando pides datos al usuario — todo lo que un usuario escribe en una terminal llega como texto (`str`), aunque parezca un número. Si quieres hacer matemáticas con eso, tienes que convertirlo primero.

```python
edad = input("¿Cuántos años tienes? ")   # esto siempre regresa texto
edad = int(edad)                          # ahora sí es un número usable
```

---

### 5. Variables que cambian: el "estado" de un programa

A diferencia de la incógnita matemática (que buscas una vez y ya), una variable de programación puede **reasignarse** cuantas veces quieras durante la ejecución:

```python
contador = 0
contador = contador + 1    # ahora contador vale 1
contador = contador + 1    # ahora contador vale 2
```

Esto es exactamente la idea de "variable que cambia" que ya viste en Matemáticas 1.2 (`y = x + 15`, donde y cambia si x cambia) — solo que aquí la misma variable se reescribe a sí misma con su propio valor anterior. Esta idea de "actualizar el estado" es el corazón de la **iteración** que vas a formalizar en la Lección 1.4.

**Atajo común (no es obligatorio memorizarlo, pero lo vas a ver mucho):**

```python
contador += 1   # exactamente lo mismo que: contador = contador + 1
```

---

### 6. Recapitulación

```
Variable = caja con nombre que guarda un valor (igual que la incógnita, pero puede cambiar)
    ↓
Tipos de dato: int, float, str, bool
    ↓
Cada tipo permite ciertas operaciones, no todas
    ↓
Conversión de tipos (type casting) cuando lo necesitas
    ↓
Reasignación: una variable puede cambiar de valor durante el programa
```

Con esto ya tienes las cajas y su contenido. En la Lección 1.3 vas a formalizar la **selección** (`if/else`) usando exactamente el tipo `bool` que acabas de aprender.

---

## 🌌 Horizonte-Aplicado

_(esto no lo cubrimos aquí, pero lo vas a necesitar más adelante en programación real)_

- **Tipado estático vs. dinámico** — Python decide el tipo automáticamente al asignar un valor (tipado dinámico); otros lenguajes (como Java o C) te obligan a declarar el tipo explícitamente antes de usar la variable (tipado estático); vas a notar esta diferencia en cuanto veas código de otro lenguaje.
- **Estructuras de datos más complejas** — listas, diccionarios, tuplas (las verás a fondo en el Módulo 2: Structuring the World); son, en esencia, "cajas que guardan muchas cajas", construidas sobre estos mismos tipos base.
- **Mutabilidad e inmutabilidad** — algunos tipos de datos en Python se pueden modificar después de creados y otros no; es un concepto que causa muchos bugs sutiles si no lo entiendes bien, y que vas a encontrar de frente en estructuras de datos más avanzadas.

## 🏛️ Horizonte-Cultural

_(no lo vas a "usar" en un commit, pero te da contexto y entrena tu forma de pensar)_

- **Por qué Python se llama Python** — no es por la serpiente; su creador, Guido van Rossum, lo nombró en honor al grupo de comedia británico Monty Python, porque quería que el lenguaje se sintiera menos solemne que otros de su época.
- **La guerra histórica entre tipado estático y dinámico** — durante décadas ha habido debate en la industria sobre cuál filosofía de tipado es "mejor"; investigar los argumentos de ambos lados es un buen ejercicio para entender que en ingeniería casi nunca hay una sola respuesta correcta, solo trade-offs.
- **Por qué los primeros lenguajes de programación no tenían tipos de datos "amigables"** — en los inicios de la computación, programar significaba manipular directamente posiciones de memoria en binario; los tipos de datos que hoy usas sin pensar (`int`, `str`) son una capa de abstracción que costó décadas de evolución del diseño de lenguajes.

---

## 🧠 Prompts para tu Tutor IA (NotebookLM)

**Modo Express** _(quiero repasar rápido el núcleo)_

> "Actúa como un profesor directo. Basándote únicamente en esta fuente, resume los 4 tipos de datos básicos de Python, cómo convertir entre ellos, y qué significa reasignar una variable, con un ejemplo de código de cada uno."

**Modo Expansión** _(quiero más de lo que dice la lección)_

> "Esta fuente es la base mínima. Dame 10 ejemplos adicionales de variables con distintos tipos de datos en contextos cotidianos (no técnicos), y explícame qué pasa si intento hacer operaciones inválidas entre tipos distintos, con ejemplos de errores reales de Python."

**Modo Ingeniero** _(quiero conectar esto con programación real)_

> "De los temas listados en 'Horizonte-Aplicado' de esta fuente, explícame la diferencia entre tipado estático y dinámico con un ejemplo comparando cómo se vería la misma variable en Python vs. en un lenguaje de tipado estático como Java."

**Modo Curioso** _(quiero contexto e historia)_

> "Cuéntame la historia de por qué Python se llama así, y algo sobre la filosofía de diseño de Guido van Rossum al crearlo, basándote en el Horizonte-Cultural de esta fuente."

**Modo Escéptico** _(quiero que me examinen)_

> "Actúa como un profesor escéptico y directo. Basándote únicamente en esta fuente, dame 5 líneas de código con variables y pídeme que identifique el tipo de dato de cada una sin ejecutarlas, más un ejercicio donde tenga que predecir si una operación entre dos variables va a fallar o no, y por qué. Corrígeme con el porqué, no me des la respuesta antes de que yo intente."

---

## 🎯 Reto de la Comunidad

Antes de pasar a la Lección 1.3, responde esto en el canal de la materia:

1. Crea (en pseudocódigo o Python real) tres variables: tu edad (`int`), tu nombre (`str`), y si te gusta programar (`bool`). Escribe qué tipo de dato es cada una.
2. ¿Qué crees que pasa si ejecutas `"5" + 5` en Python? Explica tu predicción con el porqué ANTES de probarlo, luego pruébalo y compara.
3. Explica con tus propias palabras por qué `int(19.99)` da `19` y no `20`. Conéctalo con lo que ya viste sobre redondeo vs. truncado en Matemáticas 1.1.

> **Regla de la comunidad:** No postees la respuesta directa de otros. Si alguien se equivoca, dale una pista, no la solución.

---

Siguiente lección → **1.3: Estructuras de Control — Condicionales (if/else)**
