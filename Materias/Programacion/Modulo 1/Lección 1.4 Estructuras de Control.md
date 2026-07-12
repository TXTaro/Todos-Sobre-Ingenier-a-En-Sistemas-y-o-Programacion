# Programación — Módulo 1 — Lección 1.4: Estructuras de Control (Bucles)

> **"La multiplicación existe para no sumar mil veces a mano. El bucle existe por la misma razón exacta, aplicada a código."**
> 
> Esta es la última lección del módulo, y cierra el círculo de las 3 estructuras universales que viste en la 1.1: ya tienes secuencia (el orden natural del código), selección (`if/else`), y ahora te falta la **iteración** — la capacidad de repetir algo sin escribirlo mil veces.

---

## 🎚️ Ubicación en el mapa

- **Módulo:** 1 — The Core Logic (Fundamentos del Pensamiento)
- **Nivel de esta lección:** Fundamento (cierre de módulo)
- **Requiere haber visto:** Lección 1.1 (estructura de "Iteración"), 1.2 (variables que se reasignan) y 1.3 (condicionales) — un bucle combina las tres cosas.

---

## 🔩 Núcleo (lo esencial, no se salta)

### 0. El problema que resuelve un bucle

Imagina que quieres imprimir "Hola" cinco veces. Sin bucles, tendrías que hacer esto:

```python
print("Hola")
print("Hola")
print("Hola")
print("Hola")
print("Hola")
```

Funciona, pero es absurdo — ¿y si necesitas hacerlo 1,000 veces? ¿O 10,000? Un **bucle (loop)** es la estructura que le dice a la computadora: _"repite este bloque de código N veces, o mientras se cumpla una condición."_

Esto es literalmente la misma lógica de Matemáticas 1.1: la multiplicación es "suma repetida" para no escribir `4+4+4` a mano. Un bucle es "código repetido" para no escribir el mismo `print` cien veces.

---

### 1. `for`: cuando sabes cuántas veces repetir

El bucle `for` en Python recorre una secuencia de valores, uno por uno, ejecutando el bloque de código en cada paso.

```python
for i in range(5):
    print("Hola")
```

Esto imprime "Hola" exactamente 5 veces. Desglosado:

- `range(5)` → genera una secuencia de 5 números: `0, 1, 2, 3, 4`.
- `for i in ...` → en cada vuelta, `i` toma el siguiente valor de esa secuencia.
- El bloque con sangría se ejecuta una vez por cada valor.

**Puedes usar el valor de `i` dentro del bucle:**

```python
for i in range(5):
    print(i)

# Imprime:
# 0
# 1
# 2
# 3
# 4
```

**Recuerda `range()` no empieza en 1 por default** — empieza en 0 y no incluye el número final. `range(5)` da 5 números (0 al 4), no del 1 al 5. Este detalle confunde a casi todo el mundo la primera vez.

Si quieres controlar el inicio, fin y salto:

```python
for i in range(2, 10, 2):
    print(i)

# Imprime: 2, 4, 6, 8   (empieza en 2, no llega a 10, salta de 2 en 2)
```

---

### 2. `for` sobre listas y texto: recorriendo colecciones reales

El `for` no solo sirve con números — puede recorrer cualquier colección de elementos:

```python
nombres = ["Ana", "Luis", "Marco"]

for nombre in nombres:
    print("Hola, " + nombre)

# Imprime:
# Hola, Ana
# Hola, Luis
# Hola, Marco
```

Esto es una probada de listas (que verás a fondo en el Módulo 2), pero es tan común que vale la pena que la reconozcas desde ahora: el `for` recorre elemento por elemento, sin que tengas que saber de antemano cuántos hay.

---

### 3. `while`: cuando no sabes cuántas veces vas a repetir

El bucle `for` es ideal cuando sabes de antemano cuántas repeticiones necesitas. El `while` es para cuando la repetición depende de una **condición** (como el `if` de la Lección 1.3), no de un número fijo.

```python
contador = 0

while contador < 5:
    print(contador)
    contador += 1
```

Esto imprime `0, 1, 2, 3, 4` — el mismo resultado que el ejemplo del `for` de arriba, pero construido distinto: aquí el bucle sigue repitiendo **mientras** la condición (`contador < 5`) siga siendo verdadera.

**El paso que NUNCA debes olvidar en un `while`:** algo dentro del bucle tiene que cambiar la condición eventualmente (aquí, `contador += 1`), o el bucle nunca termina.

---

### 4. El bucle infinito: el error más famoso de quien empieza a programar

```python
contador = 0

while contador < 5:
    print(contador)
    # ❌ Falta contador += 1 aquí
```

Sin esa línea, `contador` siempre vale `0`, la condición `0 < 5` siempre es verdadera, y el programa se queda **repitiendo para siempre**, imprimiendo `0` sin parar hasta que fuerces su cierre.

Este es probablemente el primer error real con el que te vas a topar en programación que no es un simple error de sintaxis — es un error de **lógica**. El código es válido, compila, corre... y nunca termina. Por eso el pensamiento computacional de la Lección 1.1 (pensar antes de escribir) es tan importante: un `while` mal pensado se nota hasta que ya está corriendo sin parar.

---

### 5. `break` y `continue`: control fino dentro de un bucle

**`break`:** sale del bucle inmediatamente, sin importar si la condición seguía siendo verdadera.

```python
for i in range(10):
    if i == 5:
        break
    print(i)

# Imprime: 0, 1, 2, 3, 4   (se detiene al llegar a 5)
```

**`continue`:** salta el resto del bloque actual y pasa directo a la siguiente vuelta, sin salir del bucle.

```python
for i in range(5):
    if i == 2:
        continue
    print(i)

# Imprime: 0, 1, 3, 4   (salta el 2, pero sigue con el resto)
```

---

### 6. Bucles anidados: un bucle dentro de otro bucle

Igual que anidaste condicionales en la 1.3, puedes anidar bucles:

```python
for i in range(3):
    for j in range(2):
        print(i, j)

# Imprime:
# 0 0
# 0 1
# 1 0
# 1 1
# 2 0
# 2 1
```

Por cada vuelta del bucle externo (`i`), el bucle interno (`j`) se ejecuta completo. Esto se usa mucho para recorrer estructuras de datos en dos dimensiones (como tablas o matrices), que verás en módulos posteriores.

---

### 7. Recapitulación: las 3 estructuras, completas

```
Secuencia (1.1)     → el código corre en orden, línea por línea
    +
Selección (1.3)     → if/elif/else deciden qué camino tomar
    +
Iteración (1.4)     → for/while repiten código sin copiarlo mil veces
    =
Cualquier programa que exista, sin importar qué tan complejo sea
```

Con esto se cierra el Módulo 1 completo de Programación. Ya piensas en algoritmos, ya escribes variables con tipos correctos, ya tomas decisiones con condicionales, y ya repites procesos con bucles — las cuatro piezas mínimas para construir cualquier lógica de software.

---

## 🌌 Horizonte-Aplicado

_(esto no lo cubrimos aquí, pero lo vas a necesitar más adelante en programación real)_

- **List comprehensions** — Python tiene una forma más compacta de escribir ciertos bucles `for` en una sola línea (`[x*2 for x in range(5)]`); es puramente sintaxis más elegante sobre la misma lógica que ya sabes, la verás cuando trabajes con listas a fondo.
- **Complejidad de bucles anidados** — conecta directo con Big O (ya mencionado en Matemáticas 1.3 y Programación 1.1): un bucle dentro de otro bucle generalmente significa que tu programa crece mucho más lento conforme crecen los datos; es de las primeras cosas que se revisan al optimizar código.
- **Bucles en el mundo real de un servidor** — un servidor que "escucha" peticiones constantemente es, en esencia, un bucle `while True` gigante con condiciones y salidas controladas; lo verás en el Módulo 4 de Programación y en Sistemas.

## 🏛️ Horizonte-Cultural

_(no lo vas a "usar" en un commit, pero te da contexto y entrena tu forma de pensar)_

- **El "Y2K bug" y la importancia de pensar bien los límites de un bucle/condición** — el famoso miedo del año 2000 fue, en esencia, un problema de cómo los programas representaban y evaluaban años con solo 2 dígitos; investigarlo es un buen recordatorio de que errores de lógica simple pueden tener consecuencias enormes a escala.
- **El Halting Problem (Problema de la Parada)** — Alan Turing (el mismo que mencionamos en Matemáticas 1.4) demostró matemáticamente que es imposible crear un programa general que pueda predecir, para cualquier otro programa, si un bucle va a terminar o va a correr para siempre; es una de las limitaciones teóricas más profundas de la computación, y explica por qué "detectar bucles infinitos automáticamente" no es tan simple como suena.
- **Por qué los primeros programadores odiaban los bucles mal optimizados** — en la época en que la memoria y el poder de cómputo eran extremadamente limitados (décadas de 1960-1980), un bucle ineficiente podía literalmente hacer que un programa tardara horas o no cupiera en la memoria disponible; esa escasez forzó una disciplina de optimización que hoy, con hardware potente, muchos programadores nuevos no desarrollan igual.

---

## 🧠 Prompts para tu Tutor IA (NotebookLM)

**Modo Express** _(quiero repasar rápido el núcleo)_

> "Actúa como un profesor directo. Basándote únicamente en esta fuente, resume la diferencia entre for y while, qué son break y continue, y por qué ocurre un bucle infinito, con un ejemplo de código de cada uno."

**Modo Expansión** _(quiero más de lo que dice la lección)_

> "Esta fuente es la base mínima. Dame 8 ejercicios cortos de dificultad creciente usando for y while, incluyendo al menos uno con bucles anidados, sin darme las respuestas."

**Modo Ingeniero** _(quiero conectar esto con programación real)_

> "De los temas listados en 'Horizonte-Aplicado' de esta fuente, explícame qué es la complejidad de bucles anidados conectándolo con Big O, y dame un ejemplo simple de un bucle ineficiente vs uno más eficiente que resuelvan el mismo problema."

**Modo Curioso** _(quiero contexto e historia)_

> "Explícame el Halting Problem de Alan Turing mencionado en el Horizonte-Cultural de esta fuente, en términos simples, y por qué es relevante para entender los bucles infinitos que vi en el núcleo."

**Modo Escéptico** _(quiero que me examinen)_

> "Actúa como un profesor escéptico y directo. Basándote únicamente en esta fuente, dame 5 fragmentos de código con bucles (incluyendo al menos uno con un bucle infinito a propósito) y pídeme identificar qué va a pasar en cada uno ANTES de ejecutarlos. Corrígeme con el porqué, no me des la respuesta antes de que yo intente."

---

## 🎯 Reto de la Comunidad

Antes de pasar al Módulo 2, responde esto en el canal de la materia:

1. Escribe un `for` que imprima los números del 1 al 10 (recuerda cómo funciona `range()`).
2. Escribe un `while` que sume números del 1 al 100 y muestre el resultado total al final. Identifica claramente qué línea evita que sea un bucle infinito.
3. Explica con tus propias palabras qué es un bucle infinito y por qué el Halting Problem dice que no existe una forma general de detectarlos automáticamente en cualquier programa.

> **Regla de la comunidad:** No postees la respuesta directa de otros. Si alguien se equivoca, dale una pista, no la solución.

---

**🏁 Módulo 1 de Programación completado.** Con Matemáticas, Inglés y Programación con su Módulo 1 cerrado, el siguiente paso natural sería el **Módulo 1 de Sistemas: The Machine's Anatomy (Hardware y Arquitectura)** — pero, como siempre, tú decides el orden desde aquí.
