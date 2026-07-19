# Programación — Módulo 2 — Lección 2.3: Diccionarios (Pares Clave-Valor)

> **"Una lista te da valores por posición: el elemento 0, el elemento 1. Un diccionario te da valores por nombre. Y ese 'nombre' se calcula, por debajo, con exactamente el hashing que viste en Matemáticas 2.3."**
> 
> En la 2.2 organizaste datos por posición numérica. Aquí vas a organizar datos por **nombre** — mucho más parecido a cómo piensas en la vida real ("el precio del café", no "el elemento en la posición 4").

---

## 🎚️ Ubicación en el mapa

- **Módulo:** 2 — Structuring the World
- **Nivel de esta lección:** Fundamento
- **Requiere haber visto:** Lección 2.2 (Listas, para contrastar la diferencia clave de acceso por posición vs. por nombre) y Matemáticas Lección 2.3 (Aritmética Modular y Hashing) — un diccionario de Python está construido internamente usando exactamente esa técnica.

---

## 🔩 Núcleo (lo esencial, no se salta)

### 0. El problema que resuelve un diccionario

Imagina que quieres guardar el precio de varios productos usando una lista:

```python
productos = ["café", "té", "agua"]
precios = [45, 30, 15]
```

Para saber el precio del "té", tienes que buscar su posición en `productos` (índice 1) y luego usar ese mismo índice en `precios`. Es incómodo y propenso a errores si las listas se desordenan entre sí.

Un **diccionario** resuelve esto directamente: guarda pares de **clave** (nombre) y **valor** (dato asociado), sin necesidad de recordar posiciones.

```python
precios = {
    "café": 45,
    "té": 30,
    "agua": 15
}

print(precios["té"])   # 30 — accedes directo por el nombre, no por posición
```

---

### 1. Sintaxis básica: creando y accediendo a un diccionario

```python
usuario = {
    "nombre": "Ana",
    "edad": 25,
    "activo": True
}

print(usuario["nombre"])   # 'Ana'
print(usuario["edad"])     # 25
```

Se escribe entre llaves `{ }`, con cada par como `clave: valor`, separados por comas. Las claves suelen ser texto (`str`), pero técnicamente pueden ser cualquier tipo de dato inmutable (números, incluso tuplas — que verás en la 2.4).

**Error común:** acceder a una clave que no existe.

```python
print(usuario["telefono"])   # ❌ KeyError: la clave no existe
```

**Forma más segura de acceder (evita el error de arriba):**

```python
print(usuario.get("telefono"))              # None (en vez de un error)
print(usuario.get("telefono", "No definido"))  # 'No definido' (valor por default si no existe)
```

---

### 2. Modificando un diccionario: mutabilidad, igual que las listas

```python
usuario["edad"] = 26              # modifica el valor de una clave existente
usuario["ciudad"] = "CDMX"        # agrega una clave nueva
del usuario["activo"]              # elimina una clave

print(usuario)
# {'nombre': 'Ana', 'edad': 26, 'ciudad': 'CDMX'}
```

**Métodos útiles:**

```python
usuario.keys()      # todas las claves: dict_keys(['nombre', 'edad', 'ciudad'])
usuario.values()    # todos los valores: dict_values(['Ana', 26, 'CDMX'])
usuario.items()     # pares clave-valor juntos, útil para recorrer con for
```

---

### 3. Recorriendo un diccionario con `for`

```python
usuario = {"nombre": "Ana", "edad": 25, "ciudad": "CDMX"}

for clave in usuario:
    print(clave)   # imprime solo las claves: nombre, edad, ciudad

for clave, valor in usuario.items():
    print(clave, ":", valor)

# Imprime:
# nombre : Ana
# edad : 25
# ciudad : CDMX
```

---

### 4. Diccionarios anidados: estructuras más realistas

En software real, casi nunca vas a tener un diccionario tan simple como los ejemplos de arriba — vas a tener diccionarios dentro de diccionarios, o listas dentro de diccionarios, representando datos más complejos:

```python
usuario = {
    "nombre": "Ana",
    "contacto": {
        "email": "ana@ejemplo.com",
        "telefono": "555-1234"
    },
    "lenguajes": ["Python", "JavaScript"]
}

print(usuario["contacto"]["email"])   # 'ana@ejemplo.com'
print(usuario["lenguajes"][0])         # 'Python'
```

Esta forma de anidar diccionarios y listas es, literalmente, la estructura que vas a ver en **JSON** — el formato más común para intercambiar datos entre aplicaciones web, APIs, y bases de datos. Si esta estructura se te hace familiar, es porque JSON se diseñó tomando como inspiración directa la sintaxis de objetos/diccionarios de lenguajes como Python y JavaScript.

---

### 5. La conexión directa con Matemáticas 2.3: por qué es tan rápido

Recuerda el hashing de Matemáticas 2.3:

```
hash(dato) = (suma_de_valores) % tamaño_de_tabla
```

Un diccionario de Python usa exactamente este principio por debajo: cuando guardas `precios["té"]`, Python no recorre uno por uno buscando "té" como tendría que hacer con una lista — calcula un **hash** de la clave `"té"`, y ese hash le dice directamente en qué posición interna de memoria está guardado el valor. Por eso acceder a un diccionario es, en la inmensa mayoría de los casos, casi instantáneo sin importar qué tan grande sea — a diferencia de buscar un valor específico dentro de una lista larga, que sí tiene que revisar posición por posición.

```python
# Buscar en una lista larga: revisa uno por uno (lento si la lista es enorme)
"té" in ["café", "té", "agua", ...miles de elementos más]

# Buscar en un diccionario: usa el hash directo (rápido sin importar el tamaño)
"té" in precios
```

**Regla importante que se desprende de esto:** las claves de un diccionario deben ser de un tipo **inmutable** (texto, números, tuplas) — no puedes usar una lista como clave, precisamente porque el hash se calcula una sola vez al crear la clave, y si la clave pudiera cambiar después, el hash quedaría desactualizado y el sistema completo se rompería.

---

### 6. Recapitulación

```
Diccionario = pares clave: valor, entre { }
    ↓
Acceso por clave (no por posición) → diccionario["clave"]
    ↓
.get() para acceso seguro sin error si la clave no existe
    ↓
Mutable: se puede modificar, agregar, eliminar claves
    ↓
Anidamiento: diccionarios dentro de diccionarios (base de JSON)
    ↓
Por debajo: usa hashing (Matemáticas 2.3) — acceso casi instantáneo
```

Con esto ya tienes las dos estructuras de datos más usadas en programación real: listas (orden, posición) y diccionarios (nombre, velocidad). En la Lección 2.4 vas a ver dos estructuras más, que resuelven casos específicos donde ni listas ni diccionarios son la herramienta perfecta.

---

## 🌌 Horizonte-Aplicado

_(esto no lo cubrimos aquí, pero lo vas a necesitar más adelante en programación real)_

- **JSON como estándar de intercambio de datos** — casi cualquier API web que consultes va a regresar información en formato JSON, que es prácticamente idéntico a la sintaxis de diccionarios/listas anidadas que acabas de aprender; vas a poder leer respuestas de API casi de inmediato.
- **Bases de datos NoSQL (documento)** — algunas bases de datos modernas (como MongoDB) guardan información directamente en una estructura muy similar a diccionarios anidados, en vez de tablas tradicionales; entender esta lección te da una ventaja directa si trabajas con ese tipo de bases de datos.
- **Diccionarios como "cache" o memoria rápida** — usar un diccionario para guardar resultados ya calculados y evitar recalcularlos (una técnica llamada _memoization_) es una de las optimizaciones más comunes en programación real, y depende directamente de la velocidad de acceso que viste aquí.

## 🏛️ Horizonte-Cultural

_(no lo vas a "usar" en un commit, pero te da contexto y entrena tu forma de pensar)_

- **Hash tables: una de las estructuras de datos más influyentes de la computación** — el concepto detrás de los diccionarios de Python (llamado formalmente _hash table_ o _hash map_) es considerada una de las estructuras de datos más importantes jamás inventadas en ciencias de la computación, usada prácticamente en todo software moderno, desde bases de datos hasta sistemas de caché de internet completos.
- **JSON: nacido de JavaScript, adoptado por todos** — JSON (JavaScript Object Notation) originalmente era solo la forma de representar objetos en JavaScript, pero su simplicidad hizo que se volviera el estándar universal de facto para intercambiar datos en internet, adoptado incluso por lenguajes que no tienen nada que ver con JavaScript, como Python.
- **Diccionarios ordenados: un cambio reciente en la historia de Python** — hasta la versión 3.6 de Python, el orden de los elementos en un diccionario no estaba garantizado (podían aparecer en cualquier orden al recorrerlos); a partir de esa versión, Python garantiza que mantienen el orden en que fueron agregados — un cambio de comportamiento poco común que generó bastante debate en la comunidad de desarrolladores en su momento.

---

## 🧠 Prompts para tu Tutor IA (NotebookLM)

**Modo Express** _(quiero repasar rápido el núcleo)_

> "Actúa como un profesor directo. Basándote únicamente en esta fuente, resume cómo crear, acceder y modificar un diccionario, y por qué es tan rápido comparado con buscar en una lista, con un ejemplo de código de cada uno."

**Modo Ingeniero** _(quiero conectar esto con programación real)_

> "De los temas listados en 'Horizonte-Aplicado' de esta fuente, dame un ejemplo de una respuesta JSON típica de una API real (inventada pero realista), y ayúdame a leerla como si fuera un diccionario anidado de Python."

**Modo Curioso** _(quiero contexto e historia)_

> "Explícame, basándote en el Horizonte-Cultural de esta fuente, por qué las hash tables se consideran una de las estructuras de datos más importantes de la computación, y cómo se relaciona con lo que aprendí sobre hashing en Matemáticas."

**Modo Escéptico** _(quiero que me examinen)_

> "Actúa como un profesor escéptico y directo. Basándote únicamente en esta fuente, dame 5 fragmentos de código con diccionarios (creación, acceso, modificación, y al menos uno con un diccionario anidado) y pídeme predecir el resultado de cada uno antes de ejecutarlos. Corrígeme con el porqué, no me des la respuesta antes de que yo intente."

**Modo Expansión** _(quiero más de lo que dice la lección)_

> "Usando esta fuente como piso mínimo, explícame qué es la técnica de memoization usando un diccionario como cache, con un ejemplo simple de código que muestre la diferencia de velocidad conceptual."

---

## 🎯 Reto de la Comunidad

Antes de pasar a la Lección 2.4, responde esto en el canal de la materia:

1. Crea un diccionario que represente un producto de una tienda (nombre, precio, cantidad en inventario), y escribe el código para acceder a cada uno de sus valores.
2. Usando `.get()`, intenta acceder a una clave que no existe en tu diccionario del punto 1, dando un valor por default razonable en vez de que truene con error.
3. Explica con tus propias palabras por qué no puedes usar una lista como clave de un diccionario, conectándolo con lo que aprendiste sobre hashing en Matemáticas 2.3.

> **Regla de la comunidad:** No postees la respuesta directa de otros. Si alguien se equivoca, dale una pista, no la solución.

---

Siguiente lección → **2.4: Tuplas y Sets — Cuándo Usar Cada Estructura**
