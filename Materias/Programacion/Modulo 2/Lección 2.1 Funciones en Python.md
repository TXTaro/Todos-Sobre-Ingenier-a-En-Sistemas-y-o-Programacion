# Programación — Módulo 2 — Lección 2.1: Funciones en Python (De la Máquina Matemática al Código Real)

> **"En Matemáticas 1.4 conociste f(x) como una máquina de input → proceso → output. Aquí esa máquina por fin tiene sintaxis real, y la puedes construir tú mismo con `def`."**
> 
> Esta es la primera lección del Módulo 2, y cierra una promesa que viene arrastrándose desde el inicio del temario. Ya sabes qué es una función conceptualmente — ahora vas a escribirlas de verdad.

---

## 🎚️ Ubicación en el mapa

- **Módulo:** 2 — Structuring the World
- **Nivel de esta lección:** Fundamento
- **Requiere haber visto:** Matemáticas Lección 1.4 (Funciones como Máquinas de Código) y Programación Módulo 1 completo (variables, condicionales, bucles) — una función en Python es literalmente un bloque reutilizable que combina todo lo que ya sabes.

---

## 🔩 Núcleo (lo esencial, no se salta)

### 0. Recordando la máquina de Matemáticas 1.4

```
f(x) = x + 15

f(10)   # 25
f(30)   # 45
```

En Matemáticas ya viste esto en código de ejemplo:

```python
def f(x):
    return x + 15
```

Aquí formalizamos cada pieza de esa sintaxis, y vas a construir funciones propias, con nombres descriptivos, múltiples parámetros, y lógica real dentro.

---

### 1. Anatomía de una función en Python

```python
def saludar(nombre):
    mensaje = "Hola, " + nombre
    return mensaje

resultado = saludar("Ana")
print(resultado)   # Hola, Ana
```

Desglosado:

- `def` → palabra clave que indica "aquí empieza una función".
- `saludar` → el nombre de la función (mismas reglas de nombres que las variables, Lección 1.2).
- `(nombre)` → el **parámetro** — el input que la función espera recibir. Es exactamente la `x` de `f(x)`.
- `:` seguido de código indentado → el cuerpo de la función, lo que hace con el input.
- `return` → el output — lo que la función entrega de vuelta a quien la llamó.

**Sin `return`, una función no "regresa" nada útil** — puede ejecutar código, pero si intentas guardar su resultado en una variable, obtienes `None` (un valor especial que representa "nada").

```python
def saludar_sin_return(nombre):
    print("Hola, " + nombre)   # imprime, pero no regresa nada

resultado = saludar_sin_return("Ana")   # imprime "Hola, Ana"
print(resultado)                         # None
```

---

### 2. Parámetros múltiples y valores por default

Una función puede recibir más de un input, exactamente como una función matemática de varias variables:

```python
def calcular_precio_total(precio, cantidad):
    return precio * cantidad

total = calcular_precio_total(19.99, 3)   # 59.97
```

**Parámetros con valor por default:** si no le pasas ese argumento al llamar la función, usa el valor por default que definiste.

```python
def saludar(nombre, saludo="Hola"):
    return saludo + ", " + nombre

saludar("Ana")              # 'Hola, Ana'
saludar("Ana", "Buenos días")   # 'Buenos días, Ana'
```

---

### 3. Argumentos posicionales vs. argumentos con nombre (keyword arguments)

```python
def describir_servidor(nombre, puerto, activo):
    return f"{nombre} corre en el puerto {puerto}, activo: {activo}"

# Posicional: el orden importa exactamente como lo definiste
describir_servidor("API", 8080, True)

# Con nombre (keyword): el orden ya no importa, porque nombras cada uno
describir_servidor(puerto=8080, activo=True, nombre="API")
```

Los argumentos con nombre son especialmente útiles cuando una función tiene muchos parámetros — hacen el código mucho más legible sin tener que memorizar el orden exacto.

---

### 4. Scope (ámbito): dónde "vive" una variable

Una variable creada **dentro** de una función solo existe dentro de esa función — no se puede acceder desde afuera. Esto se llama **scope local**.

```python
def calcular():
    resultado = 100
    return resultado

calcular()
print(resultado)   # ❌ NameError: resultado no existe fuera de la función
```

Por otro lado, una variable creada **fuera** de cualquier función (scope global) sí se puede leer desde adentro, pero modificarla desde dentro de una función requiere una palabra clave especial (`global`) que casi nunca vas a necesitar como principiante, y que en buenas prácticas se evita.

```python
contador_global = 0

def incrementar():
    print(contador_global)   # ✅ SÍ puede LEER la variable global
    # contador_global = contador_global + 1   # ❌ esto daría error sin la palabra 'global'
```

**Por qué esto importa de verdad:** el scope evita que el código dentro de una función "contamine" o rompa accidentalmente variables de otras partes del programa — cada función trabaja con su propio espacio aislado, a menos que tú decidas explícitamente compartir información (a través de parámetros y `return`).

---

### 5. Funciones que llaman a otras funciones (composición, otra vez)

Recuerda la composición de funciones de Matemáticas 1.4 (`g(f(x))`). En Python es exactamente igual:

```python
def duplicar(x):
    return x * 2

def sumar_diez(x):
    return x + 10

resultado = sumar_diez(duplicar(5))   # duplicar(5)=10, luego sumar_diez(10)=20
print(resultado)   # 20
```

Esto es la base de cómo se construye software real: funciones pequeñas y simples, combinadas entre sí para resolver problemas más grandes — en vez de escribir un bloque gigante de código que hace todo de una vez.

---

### 6. Recapitulación

```
def nombre(parámetros): → declara una función
    ↓
return → el output (sin esto, la función regresa None)
    ↓
Parámetros con default, argumentos posicionales y con nombre
    ↓
Scope: variables locales (dentro) vs. globales (fuera)
    ↓
Composición: funciones que llaman a otras funciones
```

Con esto ya puedes construir bloques de código reutilizables, en vez de repetir la misma lógica una y otra vez. En la Lección 2.2 vas a empezar a trabajar con estructuras que guardan **muchos** valores a la vez — el siguiente paso natural después de dominar variables individuales y funciones.

---

## 🌌 Horizonte-Aplicado

_(esto no lo cubrimos aquí, pero lo vas a necesitar más adelante en programación real)_

- **Funciones puras vs. con efectos secundarios** — ya lo mencionamos en Matemáticas 1.4; ahora que escribes funciones reales, vas a notar la diferencia entre una función que solo calcula y regresa un valor (pura) versus una que modifica algo fuera de sí misma, como imprimir o cambiar una variable global (efecto secundario).
- **Documentación de funciones (docstrings)** — Python tiene una convención estándar para documentar qué hace una función directamente en el código (`"""Esto describe la función"""`), que vas a ver en prácticamente cualquier proyecto profesional.
- **Funciones lambda (funciones anónimas)** — una forma más corta de escribir funciones simples de una sola línea, sin usar `def`; muy usada junto con listas y estructuras de datos que verás en las siguientes lecciones.
- **Recursión** — una función que se llama a sí misma para resolver un problema dividiéndolo en partes más pequeñas; es una técnica poderosa pero que requiere entender bien el concepto de "caso base" para no crear un bucle infinito (recuerda la Lección 1.4 del Módulo 1).

## 🏛️ Horizonte-Cultural

_(no lo vas a "usar" en un commit, pero te da contexto y entrena tu forma de pensar)_

- **El Cálculo Lambda de Alonzo Church** — mucho antes de que existieran las computadoras modernas, el matemático Alonzo Church (mentor de Alan Turing) desarrolló en los años 1930 un sistema matemático formal basado completamente en funciones, llamado cálculo lambda; es una de las bases teóricas de la programación funcional moderna, y de ahí viene el nombre de las "funciones lambda" que verás más adelante.
- **Por qué "función pura" se llama así** — el término viene directamente de las matemáticas: una función matemática real siempre da el mismo resultado para el mismo input, sin "efectos secundarios" en el resto del universo; los lenguajes de programación tomaron ese ideal prestado como una buena práctica de diseño, aunque no siempre sea posible cumplirlo al 100%.
- **La guerra de paradigmas: funcional vs. orientado a objetos** — a lo largo de la historia de la programación han existido distintas filosofías sobre cómo organizar el código (programación funcional, orientada a objetos, procedural); las funciones que viste aquí son la base de la programación funcional, un estilo que ha ganado mucha popularidad en años recientes por ser más predecible y fácil de probar.

---

## 🧠 Prompts para tu Tutor IA (NotebookLM)

**Modo Express** _(quiero repasar rápido el núcleo)_

> "Actúa como un profesor directo. Basándote únicamente en esta fuente, resume cómo se declara una función en Python, qué son los parámetros con default, y la diferencia entre scope local y global, con un ejemplo de código de cada uno."

**Modo Ingeniero** _(quiero conectar esto con programación real)_

> "De los temas listados en 'Horizonte-Aplicado' de esta fuente, explícame qué es una función lambda con 3 ejemplos simples, comparándola con una función normal escrita con def que haga lo mismo."

**Modo Curioso** _(quiero contexto e historia)_

> "Cuéntame sobre Alonzo Church y el cálculo lambda mencionado en el Horizonte-Cultural de esta fuente, y explícame la conexión con las funciones que aprendí en el núcleo."

**Modo Escéptico** _(quiero que me examinen)_

> "Actúa como un profesor escéptico y directo. Basándote únicamente en esta fuente, dame 5 fragmentos de código con funciones y pídeme predecir qué va a regresar cada una, incluyendo al menos uno donde intente acceder a una variable local desde afuera de la función para ver si reconozco el error. Corrígeme con el porqué, no me des la respuesta antes de que yo intente."

**Modo Expansión** _(quiero más de lo que dice la lección)_

> "Usando esta fuente como piso mínimo, explícame qué es la recursión con un ejemplo simple (como calcular un factorial), incluyendo qué es el 'caso base' y por qué es obligatorio para que no se vuelva un bucle infinito."

---

## 🎯 Reto de la Comunidad

Antes de pasar a la Lección 2.2, responde esto en el canal de la materia:

1. Escribe una función `es_par(numero)` que reciba un número y regrese `True` si es par y `False` si es impar (usa lo que ya sabes de la Lección 1.3 sobre condicionales y el operador `%` de Matemáticas 1.1).
2. Explica con tus propias palabras por qué esta función tiene un error, y corrígelo: `def sumar(a, b): print(a + b)` — luego intenta usar `resultado = sumar(3, 4)` y explica qué valor tiene `resultado`.
3. Escribe dos funciones simples y combínalas por composición (como el ejemplo de `sumar_diez(duplicar(5))`), usando tu propia lógica.

> **Regla de la comunidad:** No postees la respuesta directa de otros. Si alguien se equivoca, dale una pista, no la solución.

---

Siguiente lección → **2.2: Listas — Colecciones Ordenadas**
