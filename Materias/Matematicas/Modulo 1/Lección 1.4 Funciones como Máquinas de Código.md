# Matemáticas Aplicadas — Módulo 1 — Lección 1.4: Funciones como Máquinas de Código

> **"Una función matemática y una función de programación son la misma idea, inventada dos veces por dos disciplinas distintas."**
> 
> Esta es la última lección del Módulo 1, y es donde todo lo que construiste (aritmética, incógnitas, exponentes) se une en un solo concepto: una regla reutilizable que convierte un input en un output. Al terminar esta lección, vas a leer código y matemáticas con el mismo ojo.

---

## 🎚️ Ubicación en el mapa

- **Módulo:** 1 — El Taller de Reparación (Bases desde Cero)
- **Nivel de esta lección:** Fundamento (cierre de módulo)
- **Requiere haber visto:** Lección 1.1 (Aritmética), 1.2 (Álgebra y variables) y 1.3 (Exponentes) — una función es una expresión algebraica con una regla de entrada/salida, y puede incluir cualquier operación de las lecciones anteriores.

---

## 🔩 Núcleo (lo esencial, no se salta)

### 0. ¿Qué es una función? (La máquina de input → output)

En la Lección 1.2 viste esto:

```
y = x + 15
```

Y dijiste: "si x cambia, y cambia con ella". Eso, formalizado, es una **función**. Le damos un nombre a la regla y la escribimos así:

```
f(x) = x + 15
```

Se lee: "f de x". No significa "f multiplicado por x" — significa "la función f, aplicada al valor x". Es exactamente una llamada a función en código:

```python
def f(x):
    return x + 15

f(10)   # 25
f(30)   # 45
```

Una función tiene tres partes, igual en matemáticas que en programación:

```
INPUT (x)  →  [ REGLA / PROCESO ]  →  OUTPUT (f(x))
```

Metes un número, la máquina aplica una regla fija, te regresa otro número. La regla nunca cambia — lo que cambia es el input que le des.

---

### 1. Dominio y Rango: Qué entra y qué puede salir

**Dominio:** todos los valores de `x` que la función puede aceptar sin romperse.

```
f(x) = 1/x
```

Esta función acepta casi cualquier x, **excepto x = 0** (recuerda la Lección 1.1: no puedes dividir entre cero). El dominio de esta función es "todos los números reales, menos el 0".

En programación, esto es exactamente validar el input antes de procesarlo:

```python
def f(x):
    if x == 0:
        raise ValueError("x no puede ser 0")
    return 1 / x
```

**Rango:** todos los valores posibles que puede regresar la función (todos los outputs posibles).

```
f(x) = x²
```

Sin importar qué x metas (positivo o negativo), el resultado nunca es negativo (`(-3)² = 9`, igual que `3² = 9`). El rango de esta función es "cero o positivo".

---

### 2. Funciones Lineales: La máquina más simple

Una función es **lineal** cuando tiene la forma:

```
f(x) = mx + b
```

- `m` es la **pendiente**: qué tan inclinada está la línea (qué tanto cambia `f(x)` por cada unidad que cambia `x`).
- `b` es la **ordenada al origen**: el valor de `f(x)` cuando `x = 0` (dónde "arranca" la función).

```
f(x) = 2x + 3

f(0) = 2(0) + 3 = 3
f(1) = 2(1) + 3 = 5
f(2) = 2(2) + 3 = 7
```

Cada vez que `x` sube 1, `f(x)` sube 2 (el valor de `m`). Esa razón de cambio constante es lo que hace que, al graficarla, sea una **línea recta**.

```
Tabla:           Gráfica (ASCII simplificado):
x | f(x)              f(x)
0 |  3                  |          •
1 |  5                  |       •
2 |  7                  |    •
	                    | •
                        +------ x
```

---

### 3. Funciones Cuadráticas: Cuando aparece la curva

Una función es **cuadrática** cuando la variable tiene exponente 2 (recuerda la Lección 1.3):

```
f(x) = ax² + bx + c
```

```
f(x) = x²

f(-2) = 4
f(-1) = 1
f(0)  = 0
f(1)  = 1
f(2)  = 4
```

Fíjate: `f(-2)` y `f(2)` dan el mismo resultado. Esto no es coincidencia — es consecuencia directa de que elevar al cuadrado siempre da positivo (Lección 1.3). Esta simetría es lo que hace que, al graficarla, se vea como una curva en forma de "U" llamada **parábola**.

```
Gráfica (ASCII simplificado):

f(x)
 |  •           •
 |    •       •
 |      •   •
 |        •
 +------------- x
```

Esta forma no es solo estética — describe fenómenos reales: la trayectoria de un objeto lanzado al aire, la forma de una antena parabólica, la curva de una gráfica de rendimiento con un punto óptimo.

---

### 4. Evaluar una Función: Solo es sustituir

Evaluar `f(3)` cuando `f(x) = 2x² - 5` es exactamente sustituir `x` por `3` y aplicar la jerarquía de operaciones de la Lección 1.1:

```
f(3) = 2(3)² - 5
     = 2(9) - 5     ← primero la potencia
     = 18 - 5        ← luego la multiplicación
     = 13
```

Cada llamada a la función es una sustitución nueva, igual que llamar una función en código con distintos argumentos.

---

### 5. Composición de Funciones: Máquinas conectadas en cadena

Puedes meter el resultado de una función como input de otra. Esto se llama **composición**:

```
f(x) = x + 1
g(x) = x²

(g ∘ f)(x) = g(f(x))
```

Se lee "g compuesta con f" o "g de f de x". Primero pasas x por `f`, y el resultado lo metes a `g`:

```
(g ∘ f)(3) = g(f(3)) = g(3+1) = g(4) = 4² = 16
```

En programación, esto es literalmente anidar funciones:

```python
def f(x):
    return x + 1

def g(x):
    return x ** 2

resultado = g(f(3))   # 16
```

El orden importa: `g(f(x))` casi nunca da lo mismo que `f(g(x))`. Prueba con los mismos ejemplos y compruébalo.

---

### 6. Recapitulación

```
Variables y ecuaciones (Lección 1.2)
    ↓
Exponentes (Lección 1.3)
    ↓
Función = regla fija que convierte input en output
    ↓
Dominio (qué puede entrar) y Rango (qué puede salir)
    ↓
Lineales (línea recta) y Cuadráticas (parábola)
    ↓
Composición: encadenar funciones
```

Con esto se cierra el Módulo 1. Ya tienes la aritmética, el álgebra y el concepto de función — los tres pilares sobre los que se construye absolutamente todo lo demás en matemáticas, programación y sistemas.

---

## 🌌 Horizonte-Aplicado

_(esto no lo cubrimos aquí, pero lo vas a necesitar más adelante en ingeniería/programación)_

- **Funciones puras vs. funciones con efectos secundarios** — en programación, una función que siempre da el mismo output para el mismo input (como una función matemática real) se llama "pura"; entender esto de raíz te va a ahorrar muchos bugs difíciles de rastrear más adelante.
- **Funciones de orden superior** — funciones que reciben otras funciones como input o las regresan como output (`map`, `filter`, `reduce` en casi cualquier lenguaje); son composición de funciones, exactamente como la viste aquí, aplicada a estructuras de datos completas.
- **Funciones a trozos (piecewise)** — funciones que se comportan distinto según el rango de x en el que estés (por ejemplo, una tarifa que cobra distinto según el rango de consumo); son literalmente un `if/elif/else` escrito en notación matemática.
- **Graficación de funciones con código** — herramientas como matplotlib o desmos te van a permitir ver instantáneamente cómo cambia una gráfica al mover `m`, `b`, `a`, `c`; es la forma más rápida de construir intuición visual sobre lo que viste aquí en abstracto.

## 🏛️ Horizonte-Cultural

_(no lo vas a "usar" en un algoritmo, pero te da contexto y entrena tu forma de pensar)_

- **El origen de la notación f(x)** — fue introducida por Leonhard Euler en el siglo XVIII, uno de los matemáticos más prolíficos de la historia; antes de él, no existía una forma estándar de nombrar una función.
- **¿Por qué una parábola describe una trayectoria de un objeto lanzado?** — Galileo fue de los primeros en demostrar que el movimiento de un proyectil sigue exactamente la forma de una función cuadrática; es uno de los primeros puentes históricos entre álgebra pura y física real.
- **Máquinas de Turing y la idea de "función computable"** — mucho antes de que existieran las computadoras modernas, Alan Turing formalizó matemáticamente qué significa que un problema pueda "resolverse mediante una regla fija paso a paso" — la misma idea de "máquina" que usaste en esta lección, llevada a su extremo filosófico.
- **El concepto de función en distintas culturas matemáticas** — la idea moderna de función tardó siglos en formalizarse (desde tablas babilónicas hasta la definición moderna de Dirichlet en el siglo XIX); ver esa evolución te muestra que hasta las ideas "obvias" de hoy fueron un proceso largo de refinamiento.

---

## 🧠 Prompts para tu Tutor IA (NotebookLM)

**Modo Express** _(quiero repasar rápido el núcleo)_

> "Actúa como un profesor directo. Basándote únicamente en esta fuente, resume qué es una función, dominio, rango, y la diferencia entre lineal y cuadrática en 5 minutos de lectura, con un ejemplo numérico de cada una. Sin rodeos."

**Modo Ingeniero** _(quiero conectar esto con programación)_

> "De los temas listados en 'Horizonte-Aplicado' de esta fuente, elige el que más se conecte con buenas prácticas de programación y explícamelo con un ejemplo de código real, comparándolo con la definición matemática de función que vimos en el núcleo."

**Modo Curioso** _(quiero contexto e historia)_

> "De los temas listados en 'Horizonte-Cultural' de esta fuente, elige uno y cuéntame su historia como una anécdota interesante. Al final, dime por qué eso ayuda a entender mejor el concepto de función que se explica en el núcleo."

**Modo Escéptico** _(quiero que me examinen)_

> "Actúa como un profesor de matemáticas escéptico y directo. Basándote únicamente en esta fuente, hazme un examen de 5 preguntas: mezcla opción múltiple, evaluación de funciones paso a paso, composición de funciones, y al menos una donde tenga que explicar con mis propias palabras por qué el dominio de f(x)=1/x excluye el cero. Después de cada respuesta mía, dame retroalimentación y el porqué, nunca la respuesta directa antes de que yo intente."

---

## 🎯 Reto de la Comunidad

Antes de pasar al Módulo 2, responde esto en el canal de la materia:

1. Dado `f(x) = 3x - 2` y `g(x) = x²`, calcula `(f ∘ g)(2)` y `(g ∘ f)(2)`. ¿Dan el mismo resultado? Explica por qué sí o por qué no.
2. ¿Cuál es el dominio de `f(x) = √x`? (Pista: piensa en la Lección 1.3 sobre raíces de números negativos).
3. Piensa en una situación de la vida real (no de la escuela) que se comporte como una función a trozos (piecewise) — donde la regla cambia según el rango del input. Descríbela y escribe su "función" en palabras.

> **Regla de la comunidad:** No postees la respuesta directa. Si alguien se equivoca, dale una pista, no la solución.

---

**🏁 Módulo 1 completado.** El siguiente paso en la ruta de Matemáticas es el **Módulo 2: La Lógica de la Máquina (Matemáticas Discretas)** — pero, siguiendo el orden del temario, toca alternar de materia. Siguiente parada → **Inglés Técnico, Módulo 1: The Developer's Syntax.**
