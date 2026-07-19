# Programación — Módulo 2 — Lección 2.4: Tuplas y Sets (Cuándo Usar Cada Estructura)

> **"Ya tienes listas (orden, mutable) y diccionarios (nombre, rápido). Esta lección cierra el módulo con dos estructuras que existen por una razón muy específica: a veces necesitas que los datos NO cambien, y a veces necesitas garantizar que no haya repetidos."**
> 
> Esta es la última lección del Módulo 2. No hay conceptos nuevos de fondo — vas a reconocer inmediatamente la lógica de conjuntos que ya viste en Matemáticas 2.4, ahora como estructura de datos real.

---

## 🎚️ Ubicación en el mapa

- **Módulo:** 2 — Structuring the World
- **Nivel de esta lección:** Fundamento (cierre de módulo)
- **Requiere haber visto:** Lección 2.2 (Listas, para contrastar mutabilidad) y Matemáticas Lección 2.4 (Teoría de Conjuntos) — el `set` de Python es una implementación directa de esa lección, con el mismo nombre y las mismas operaciones.

---

## 🔩 Núcleo (lo esencial, no se salta)

### 0. Tuplas: como una lista, pero inmutable

Una **tupla** se ve casi igual que una lista, pero con paréntesis en vez de corchetes, y con una diferencia fundamental: **no se puede modificar después de creada**.

```python
coordenada = (10, 20)
colores_rgb = (255, 0, 0)
```

```python
coordenada[0] = 15   # ❌ TypeError: las tuplas no soportan asignación de elementos
```

**¿Por qué usar algo que no se puede modificar, si ya tienes listas?** Porque a veces esa restricción es exactamente lo que quieres — una garantía de que ciertos datos no van a cambiar accidentalmente en algún punto del programa. Coordenadas, colores RGB, fechas — datos que representan algo fijo por naturaleza, no una colección que va a crecer o modificarse.

**Se accede igual que una lista (indexado y slicing funcionan idéntico):**

```python
coordenada = (10, 20)
print(coordenada[0])   # 10
```

**Empaquetado y desempaquetado (muy común en Python):**

```python
punto = (10, 20)
x, y = punto   # desempaqueta directo en dos variables

print(x)   # 10
print(y)   # 20
```

Esto también es útil al recorrer diccionarios con `.items()` (Lección 2.3) — cada par clave-valor que obtienes ahí es, técnicamente, una tupla.

---

### 1. Sets: conjuntos reales, la misma lógica de Matemáticas 2.4

Un **set** en Python es, literalmente, la implementación de la teoría de conjuntos que viste en Matemáticas 2.4 — sin orden garantizado, sin elementos repetidos.

```python
frutas = {"manzana", "plátano", "naranja"}
```

**La regla de "sin repetición" se aplica automáticamente:**

```python
numeros = {1, 2, 2, 3, 3, 3}
print(numeros)   # {1, 2, 3}   ← los repetidos desaparecen solos
```

Esto es exactamente por qué un set es tan útil: si necesitas quitar duplicados de una lista, convertirla a set es la forma más simple de hacerlo.

```python
lista_con_repetidos = [1, 2, 2, 3, 3, 3, 4]
sin_repetidos = list(set(lista_con_repetidos))
print(sin_repetidos)   # [1, 2, 3, 4]
```

---

### 2. Las operaciones de Matemáticas 2.4, ahora en código

Recuerda las 3 operaciones principales de conjuntos de Matemáticas 2.4: unión, intersección, diferencia. En Python son literalmente los mismos símbolos:

```python
a = {1, 2, 3}
b = {3, 4, 5}

print(a | b)    # Unión: {1, 2, 3, 4, 5}
print(a & b)    # Intersección: {3}
print(a - b)    # Diferencia: {1, 2}
print(b - a)    # Diferencia: {4, 5}
```

O con nombres de método, si prefieres que se lea más explícito:

```python
a.union(b)
a.intersection(b)
a.difference(b)
```

**Un caso de uso real y común:** encontrar usuarios que están en dos grupos al mismo tiempo.

```python
usuarios_activos = {"ana", "luis", "marco"}
usuarios_premium = {"luis", "sara"}

usuarios_activos_y_premium = usuarios_activos & usuarios_premium
print(usuarios_activos_y_premium)   # {'luis'}
```

Esto es exactamente el ejercicio que hiciste en el Reto de la Comunidad de Matemáticas 2.4 — pero ahora es código real que puedes ejecutar.

---

### 3. Verificando pertenencia: mucho más rápido que en una lista

```python
frutas_set = {"manzana", "plátano", "naranja"}
frutas_lista = ["manzana", "plátano", "naranja"]

"plátano" in frutas_set     # rápido — usa hashing, igual que los diccionarios (Lección 2.3)
"plátano" in frutas_lista   # más lento si la lista es grande — revisa uno por uno
```

Un `set`, igual que un diccionario, usa hashing por debajo (Matemáticas 2.3) — por eso preguntar "¿esto está en el conjunto?" es casi instantáneo, sin importar qué tan grande sea el set.

---

### 4. Comparando las 4 estructuras del módulo, lado a lado

```
Lista    [ ]   ordenada,  mutable,     permite repetidos,   acceso por posición
Tupla    ( )   ordenada,  INmutable,   permite repetidos,   acceso por posición
Diccionario {}  sin orden garantizado*, mutable,  claves únicas,  acceso por clave
Set      { }   sin orden garantizado,  mutable,   sin repetidos,  verificación rápida
```

*Desde Python 3.7, los diccionarios sí mantienen el orden de inserción como comportamiento garantizado (mencionado en el Horizonte-Cultural de la 2.3), pero conceptualmente no fueron diseñados pensando en el orden como su propósito principal — su fortaleza es el acceso por nombre.

**Guía rápida para elegir cuál usar:**

```
¿Necesitas orden y que se pueda repetir un valor?        → Lista
¿Necesitas datos que NUNCA deben cambiar?                 → Tupla
¿Necesitas buscar valores por nombre, no por posición?    → Diccionario
¿Necesitas garantizar que no haya elementos repetidos,
 o hacer operaciones de unión/intersección?                → Set
```

---

### 5. Recapitulación

```
Tupla ( ) → como lista, pero inmutable → datos fijos por naturaleza
    ↓
Set { } → conjunto real, sin repetidos → operaciones de Matemáticas 2.4 en código
    ↓
Ambos: acceso e indexado con la misma lógica que ya conoces
    ↓
4 estructuras completas: lista, tupla, diccionario, set
    ↓
Cada una resuelve un problema específico — no hay una "mejor" universal
```

Con esto se cierra el Módulo 2 completo de Programación. Ya tienes funciones (bloques reutilizables) y las 4 estructuras de datos fundamentales (listas, diccionarios, tuplas, sets) — con esto puedes representar y organizar prácticamente cualquier tipo de información que un programa real necesite manejar.

---

## 🌌 Horizonte-Aplicado

_(esto no lo cubrimos aquí, pero lo vas a necesitar más adelante en programación real)_

- **Namedtuples y estructuras de datos más avanzadas** — Python tiene formas de crear tuplas con nombres para cada posición (en vez de solo índices numéricos), útil para hacer código más legible sin la complejidad completa de crear una clase.
- **Frozensets** — una versión inmutable de un set (igual que la tupla es la versión inmutable de una lista); útil cuando necesitas usar un conjunto como clave de un diccionario, algo que un set normal (mutable) no puede hacer.
- **Elegir la estructura de datos correcta como habilidad de ingeniería real** — en entrevistas técnicas y en código profesional, elegir la estructura de datos equivocada (por ejemplo, usar una lista cuando debiste usar un set) es una de las causas más comunes de código lento o difícil de mantener; esta lección es la base de esa habilidad.

## 🏛️ Horizonte-Cultural

_(no lo vas a "usar" en un commit, pero te da contexto y entrena tu forma de pensar)_

- **Inmutabilidad como filosofía de diseño, no solo una restricción técnica** — varios lenguajes y paradigmas de programación (especialmente la programación funcional, mencionada en Programación 2.1) tratan la inmutabilidad como una virtud deliberada: código que no puede cambiar datos accidentalmente es más fácil de razonar y depurar, incluso si a veces es menos "conveniente" de escribir.
- **Sets en matemáticas vs. sets en programación: la misma idea, dos siglos de diferencia** — Georg Cantor formalizó la teoría de conjuntos en el siglo XIX (Matemáticas 2.4) sin ninguna computadora en mente; que un lenguaje de programación del siglo XXI implemente esa misma idea matemática casi sin cambios, con el mismo nombre y las mismas operaciones, es un ejemplo perfecto de cómo las matemáticas puras terminan siendo la base literal de herramientas de ingeniería un siglo después.
- **Por qué Python eligió llaves para diccionarios Y sets** — puede generar confusión al inicio que tanto `{"a": 1}` (diccionario) como `{1, 2, 3}` (set) usen el mismo símbolo `{ }`; Python los distingue por si hay dos puntos `:` adentro o no — una decisión de diseño que prioriza reutilizar un símbolo visualmente relacionado (ambos son "colecciones sin orden estricto") sobre inventar un símbolo completamente nuevo.

---

## 🧠 Prompts para tu Tutor IA (NotebookLM)

**Modo Express** _(quiero repasar rápido el núcleo)_

> "Actúa como un profesor directo. Basándote únicamente en esta fuente, resume la diferencia entre tupla y lista, las operaciones de sets (unión, intersección, diferencia), y cuándo usar cada una de las 4 estructuras del módulo, con un ejemplo de código de cada una."

**Modo Ingeniero** _(quiero conectar esto con programación real)_

> "De los temas listados en 'Horizonte-Aplicado' de esta fuente, explícame qué es un frozenset y dame un ejemplo real de cuándo lo necesitarías en vez de un set normal."

**Modo Curioso** _(quiero contexto e historia)_

> "Explícame, basándote en el Horizonte-Cultural de esta fuente, cómo la teoría de conjuntos de Cantor del siglo XIX terminó siendo literalmente una estructura de datos de Python, y por qué eso es interesante."

**Modo Escéptico** _(quiero que me examinen)_

> "Actúa como un profesor escéptico y directo. Basándote únicamente en esta fuente, dame 5 situaciones distintas (guardar coordenadas, quitar duplicados de una lista, encontrar usuarios en dos grupos, etc.) y pídeme elegir cuál de las 4 estructuras usar y por qué, antes de decirme si acerté. Corrígeme con el porqué, no me des la respuesta antes de que yo intente."

**Modo Expansión** _(quiero más de lo que dice la lección)_

> "Usando esta fuente como piso mínimo, explícame qué es una namedtuple con un ejemplo simple, comparándola con una tupla normal y con un diccionario que representen el mismo dato."

---

## 🎯 Reto de la Comunidad

Antes de pasar al Módulo 3, responde esto en el canal de la materia:

1. Crea una tupla con las coordenadas (x, y) de un punto, y explica con tus propias palabras por qué usarías una tupla en vez de una lista para este caso específico.
2. Dado `equipo_a = {"ana", "luis", "marco", "sara"}` y `equipo_b = {"marco", "sara", "pedro"}`, calcula usando sets: quiénes están en ambos equipos, quiénes están solo en el equipo A, y quiénes están en cualquiera de los dos equipos.
3. Te dan esta lista con datos repetidos: `visitas = ["home", "about", "home", "contact", "home", "about"]`. Usando lo que sabes de sets, escribe el código para saber cuántas páginas ÚNICAS fueron visitadas (no cuántas visitas en total).

> **Regla de la comunidad:** No postees la respuesta directa de otros. Si alguien se equivoca, dale una pista, no la solución.

---

**🏁 Módulo 2 de Programación completado.** Con esto, Matemáticas, Inglés y Programación ya tienen 2 módulos completos cada uno. El siguiente paso natural sería el **Módulo 1 de Sistemas: The Machine's Anatomy (Hardware y Arquitectura)** — pero, como siempre, tú decides el orden desde aquí.
