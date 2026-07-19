# Programación — Módulo 2 — Lección 2.2: Listas (Colecciones Ordenadas)

> **"Hasta ahora, una variable guardaba un solo valor. ¿Y si necesitas guardar cien nombres, mil precios, o todos los usuarios de un sistema? Para eso existe la lista."**
> 
> En la 2.1 aprendiste a construir funciones. Aquí aprendes la primera de tres estructuras que van a guardar **muchos** valores organizados — el siguiente nivel después de la variable individual que dominaste en el Módulo 1.

---

## 🎚️ Ubicación en el mapa

- **Módulo:** 2 — Structuring the World
- **Nivel de esta lección:** Fundamento
- **Requiere haber visto:** Lección 1.4 del Módulo 1 (bucles `for`, en especial el ejemplo de `for nombre in nombres`) y 2.1 (funciones) — vas a combinar ambas con listas constantemente.

---

## 🔩 Núcleo (lo esencial, no se salta)

### 0. ¿Qué es una lista?

Una **lista** es una colección ordenada de valores, guardada bajo un solo nombre de variable.

```python
frutas = ["manzana", "plátano", "naranja"]
edades = [25, 30, 45, 19]
mixta = ["Ana", 25, True]   # una lista puede mezclar tipos de dato
```

Se escribe entre corchetes `[ ]`, con los elementos separados por comas. Puede contener cualquier tipo de dato que ya conoces de la Lección 1.2 del Módulo 1 (`int`, `float`, `str`, `bool`), incluso mezclados en la misma lista.

---

### 1. Acceder a elementos: indexado

Cada elemento de una lista tiene una **posición** (índice), y en Python **el conteo empieza en 0**, no en 1 (recuerda `range()` de la Lección 1.4 del Módulo 1 — misma lógica exacta).

```python
frutas = ["manzana", "plátano", "naranja"]

print(frutas[0])   # 'manzana'  ← primer elemento, índice 0
print(frutas[1])   # 'plátano'
print(frutas[2])   # 'naranja'
```

**Índices negativos:** cuentan desde el final de la lista.

```python
print(frutas[-1])   # 'naranja'  ← último elemento
print(frutas[-2])   # 'plátano'  ← penúltimo
```

**Error común:** intentar acceder a un índice que no existe.

```python
print(frutas[5])   # ❌ IndexError: la lista solo tiene 3 elementos (índices 0, 1, 2)
```

---

### 2. Slicing: obteniendo un pedazo de la lista

Puedes extraer una porción de la lista usando `[inicio:fin]` — mismo patrón que viste en `range()`, no incluye el índice final.

```python
numeros = [10, 20, 30, 40, 50]

print(numeros[1:3])    # [20, 30]   ← del índice 1 al 2 (no incluye el 3)
print(numeros[:2])     # [10, 20]   ← desde el inicio hasta el índice 1
print(numeros[2:])     # [30, 40, 50]   ← desde el índice 2 hasta el final
```

---

### 3. Modificando listas: mutabilidad

A diferencia de un `str` o un `int` (que no se pueden modificar directamente, solo reasignar), las listas son **mutables** — puedes cambiar su contenido sin crear una nueva lista.

```python
frutas = ["manzana", "plátano", "naranja"]
frutas[0] = "pera"
print(frutas)   # ['pera', 'plátano', 'naranja']
```

**Métodos más usados para modificar una lista:**

```python
frutas.append("uva")        # agrega al final: ['pera', 'plátano', 'naranja', 'uva']
frutas.remove("plátano")    # quita el primer valor que coincida
frutas.insert(1, "kiwi")    # inserta "kiwi" en la posición 1
frutas.pop()                # quita y regresa el último elemento
frutas.sort()                # ordena la lista (alfabético o numérico según el tipo)
len(frutas)                  # regresa cuántos elementos tiene la lista
```

**Por qué la mutabilidad importa (conexión directa con el scope de la 2.1):** si pasas una lista como argumento a una función y la función la modifica adentro, el cambio **sí** se refleja afuera — a diferencia de un `int` o `str`, que no se modifican al pasarlos a una función.

```python
def agregar_elemento(lista):
    lista.append("nuevo")

mi_lista = ["a", "b"]
agregar_elemento(mi_lista)
print(mi_lista)   # ['a', 'b', 'nuevo']   ← sí cambió, aunque el cambio pasó "dentro" de la función
```

---

### 4. Recorriendo una lista con `for` (repaso directo del Módulo 1)

```python
frutas = ["manzana", "plátano", "naranja"]

for fruta in frutas:
    print(fruta.upper())   # imprime cada fruta en mayúsculas
```

**Si necesitas el índice y el valor al mismo tiempo**, usa `enumerate()`:

```python
for indice, fruta in enumerate(frutas):
    print(indice, fruta)

# Imprime:
# 0 manzana
# 1 plátano
# 2 naranja
```

---

### 5. List Comprehensions: la forma compacta prometida desde el Módulo 1

En la Lección 1.4 del Módulo 1 se prometió esto como Horizonte-Aplicado — aquí lo cumplimos. Una **list comprehension** es una forma de crear una lista nueva a partir de otra, en una sola línea, combinando `for` (y opcionalmente `if`) dentro de los corchetes.

```python
# Forma tradicional con for:
numeros = [1, 2, 3, 4, 5]
duplicados = []
for n in numeros:
    duplicados.append(n * 2)

# Misma lógica, como list comprehension:
duplicados = [n * 2 for n in numeros]
```

Ambas dan exactamente `[2, 4, 6, 8, 10]` — la segunda es solo una forma más compacta de escribir el mismo bucle.

**Con condición (`if`) incluida:**

```python
pares = [n for n in numeros if n % 2 == 0]
print(pares)   # [2, 4]
```

No es obligatorio usarlas — el `for` tradicional siempre funciona igual de bien — pero las vas a ver constantemente en código de otros desarrolladores, así que necesitas poder leerlas aunque no las escribas tú mismo todavía.

---

### 6. Recapitulación

```
Lista = colección ordenada, entre [ ], puede mezclar tipos de dato
    ↓
Indexado (empieza en 0) y slicing ([inicio:fin])
    ↓
Mutabilidad: se puede modificar sin crear una lista nueva
    ↓
Métodos: append, remove, insert, pop, sort, len
    ↓
for + enumerate() para recorrerla
    ↓
List comprehensions: forma compacta de construir listas nuevas
```

Con esto ya puedes guardar y manipular colecciones ordenadas de datos. En la Lección 2.3 vas a ver una estructura distinta — donde en vez de posiciones numeradas, cada valor tiene un **nombre** (clave) propio.

---

## 🌌 Horizonte-Aplicado

_(esto no lo cubrimos aquí, pero lo vas a necesitar más adelante en programación real)_

- **Algoritmos de búsqueda y ordenamiento sobre listas** — ya mencionados en Programación 1.1; ahora que sabes manipular listas reales, vas a poder implementar búsqueda lineal, búsqueda binaria, y algoritmos de ordenamiento clásicos con la sintaxis que acabas de aprender.
- **Listas anidadas (matrices)** — una lista puede contener otras listas adentro (`[[1,2],[3,4]]`), usado para representar tablas, matrices o tableros de juego; combina directamente con los bucles anidados que viste en Programación 1.4.
- **Complejidad de operaciones en listas** — no todas las operaciones sobre una lista cuestan lo mismo en tiempo (agregar al final es rápido, buscar un elemento específico es más lento); esto conecta con Big O, mencionado desde Matemáticas 1.3.

## 🏛️ Horizonte-Cultural

_(no lo vas a "usar" en un commit, pero te da contexto y entrena tu forma de pensar)_

- **Arrays vs. listas: una distinción que varía entre lenguajes** — en muchos lenguajes de programación (como C), un "array" tiene tamaño fijo y todos sus elementos deben ser del mismo tipo; las listas de Python son más flexibles (tamaño dinámico, tipos mezclados), una decisión de diseño que prioriza facilidad de uso sobre control estricto de memoria.
- **Por qué el índice empieza en 0 y no en 1** — esta convención viene de cómo funciona la memoria de una computadora a bajo nivel: el índice 0 representa "cero posiciones de distancia desde el inicio", no "el primer elemento contado desde 1"; es una decisión de diseño que se remonta a los primeros lenguajes de programación como C, y que Python heredó por convención.
- **Guido van Rossum y la filosofía de "legibilidad sobre todo"** — las list comprehensions son un ejemplo de la filosofía de diseño de Python (mencionada en Programación 1.2): dar formas más cortas y legibles de expresar patrones de código extremadamente comunes, en vez de forzar siempre la forma más "explícita" pero verbosa.

---

## 🧠 Prompts para tu Tutor IA (NotebookLM)

**Modo Express** _(quiero repasar rápido el núcleo)_

> "Actúa como un profesor directo. Basándote únicamente en esta fuente, resume cómo crear, indexar y modificar una lista, los métodos más comunes, y qué es una list comprehension, con un ejemplo de código de cada uno."

**Modo Ingeniero** _(quiero conectar esto con programación real)_

> "De los temas listados en 'Horizonte-Aplicado' de esta fuente, explícame la diferencia entre búsqueda lineal y búsqueda binaria sobre una lista, con un ejemplo de código simple de cada una."

**Modo Curioso** _(quiero contexto e historia)_

> "Explícame, basándote en el Horizonte-Cultural de esta fuente, por qué el índice de las listas empieza en 0 en la mayoría de los lenguajes de programación, y cómo se relaciona con la memoria de una computadora."

**Modo Escéptico** _(quiero que me examinen)_

> "Actúa como un profesor escéptico y directo. Basándote únicamente en esta fuente, dame 5 fragmentos de código con listas (indexado, slicing, y al menos un método) y pídeme predecir el resultado de cada uno antes de ejecutarlos. Corrígeme con el porqué, no me des la respuesta antes de que yo intente."

**Modo Expansión** _(quiero más de lo que dice la lección)_

> "Usando esta fuente como piso mínimo, explícame qué son las listas anidadas con un ejemplo de una matriz simple de 2x2, y cómo recorrerla completa usando bucles anidados."

---

## 🎯 Reto de la Comunidad

Antes de pasar a la Lección 2.3, responde esto en el canal de la materia:

1. Crea una lista con los nombres de 5 lenguajes de programación, imprime el primero y el último usando índices (positivo y negativo respectivamente).
2. Usando list comprehension, crea una lista nueva que contenga solo los números pares de esta lista: `numeros = [3, 8, 12, 7, 15, 20, 5]`.
3. Escribe una función que reciba una lista de números y regrese el promedio (usando lo que ya sabes de funciones de la 2.1, `len()`, y `sum()` — investiga qué hace `sum()` si no lo conoces).

> **Regla de la comunidad:** No postees la respuesta directa de otros. Si alguien se equivoca, dale una pista, no la solución.

---

Siguiente lección → **2.3: Diccionarios — Pares Clave-Valor**
