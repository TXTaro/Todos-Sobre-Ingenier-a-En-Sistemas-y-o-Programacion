# Matemáticas Aplicadas — Módulo 2 — Lección 2.3: Aritmética Modular y Criptografía Básica

> **"El reloj de tu pared lleva haciendo aritmética modular toda tu vida, mucho antes de que supieras que tenía nombre."**
> 
> Desde la Lección 1.1 conoces el operador `%` como "el residuo de una división". Aquí ese residuo deja de ser un detalle técnico y se convierte en la base matemática de relojes, hashing, y — sí — de cómo se protege tu contraseña cuando la mandas por internet.

---

## 🎚️ Ubicación en el mapa

- **Módulo:** 2 — La Lógica de la Máquina (Matemáticas Discretas)
- **Nivel de esta lección:** Fundamento
- **Requiere haber visto:** Lección 1.1 (división, residuo, números primos) y 1.3 (exponentes) — la aritmética modular es división con residuo llevada a su máximo potencial, y la criptografía que veremos usa exponentes gigantes.

---

## 🔩 Núcleo (lo esencial, no se salta)

### 0. El residuo, otra vez, pero con propósito

En la Lección 1.1 viste esto:

```
13 ÷ 4 = 3, residuo 1
13 % 4 = 1
```

Ahí el residuo era casi un efecto secundario de la división. En **aritmética modular**, el residuo **es el protagonista** — no nos importa el cociente, solo nos importa qué sobra.

```
Notación formal:  13 ≡ 1 (mod 4)
```

Se lee: "13 es congruente con 1, módulo 4". Significa que, si divides 13 entre 4, el residuo es 1. Todo número que, dividido entre 4, deje residuo 1 (`1, 5, 9, 13, 17, 21...`) es **equivalente** dentro del "mundo módulo 4".

---

### 1. El Reloj: La intuición perfecta de la aritmética modular

Un reloj de 12 horas es aritmética modular pura, y probablemente nunca lo pensaste así.

```
Si son las 10:00 y avanzan 5 horas, ¿qué hora es?

10 + 5 = 15   →   15 no existe en un reloj de 12 horas
15 % 12 = 3   →   son las 3:00
```

El reloj "da la vuelta" cada 12 horas — nunca llega a 13, 14 o 15, regresa al 1. Eso es exactamente lo que hace el operador `%`: cuando un número se pasa del límite (el **módulo**), regresa al inicio y sigue contando desde ahí.

```python
hora_actual = 10
horas_a_sumar = 5

nueva_hora = (hora_actual + horas_a_sumar) % 12   # 3
```

**Otro ejemplo cotidiano:** los días de la semana. Si hoy es viernes (día 5) y quieres saber qué día será en 10 días:

```python
dia_actual = 5          # viernes
dias_a_sumar = 10

nuevo_dia = (dia_actual + dias_a_sumar) % 7   # 1 → lunes
```

---

### 2. Propiedades de la Aritmética Modular

La aritmética modular no rompe las reglas que ya conoces (Lección 1.1) — las respeta, solo que "envueltas" dentro de un módulo:

```
Suma modular:            (a + b) % n = ((a % n) + (b % n)) % n
Multiplicación modular:  (a × b) % n = ((a % n) × (b % n)) % n
```

**Por qué esto importa en la práctica:** te permite trabajar con números **enormes** sin tener que calcular el número completo primero. Si necesitas `(847293847 × 928374982) % 100`, no necesitas el producto gigante completo — puedes reducir cada número módulo 100 primero y multiplicar esos residuos. Esto es exactamente lo que hacen las computadoras para trabajar con criptografía de números gigantescos sin quedarse sin memoria.

```python
# Verificación de la propiedad:
a, b, n = 17, 23, 5

directo = (a * b) % n                        # 391 % 5 = 1
por_partes = ((a % n) * (b % n)) % n         # (2 * 3) % 5 = 1
# Mismo resultado: 1 == 1   ✅
```

---

### 3. Hashing: Aritmética modular al servicio de organizar datos

Un **hash** es una función que convierte cualquier dato (un texto, un archivo, una contraseña) en un número de tamaño fijo. La forma más simple de construir uno usa exactamente el operador `%`:

```
Función hash simplificada:
hash(dato) = (suma_de_valores_ASCII_del_dato) % tamaño_de_tabla
```

```python
def hash_simple(texto, tamano_tabla):
    suma = sum(ord(c) for c in texto)   # convierte cada letra a su número ASCII
    return suma % tamano_tabla

hash_simple("hola", 10)   # siempre da un número entre 0 y 9
```

Esto es la base de los **diccionarios/hash tables** que usas en casi cualquier lenguaje de programación (`dict` en Python, `HashMap` en Java): el módulo garantiza que, sin importar qué tan largo sea el dato, el resultado siempre cabe en un rango fijo de "cajones" donde guardar la información.

---

### 4. RSA: Un vistazo real (no completo) a cómo funciona el candado de internet

En la Lección 1.1 mencionamos que los números primos son "el ADN de los números" y que se usan en criptografía moderna (RSA). Aquí vas a ver **la idea central**, sin las matemáticas completas de teoría de números que se necesitan para implementarlo de verdad.

**El problema que resuelve RSA:** ¿cómo mandas un mensaje secreto a alguien por un canal que cualquiera puede espiar, sin haber compartido antes una clave secreta en persona?

**La idea (simplificada):**

1. El candado usa dos números primos **enormes** (de cientos de dígitos) multiplicados entre sí.
2. Es fácil multiplicar dos primos gigantes para obtener el producto.
3. Es _extremadamente difícil_ hacer el proceso inverso: dado el producto, encontrar cuáles eran los dos primos originales (recuerda la factorización en primos de la Lección 1.1 — aquí es donde se vuelve computacionalmente brutal a gran escala).
4. Esa diferencia de dificultad (fácil ir, imposible regresar en tiempo razonable) es la que hace que el sistema sea seguro.

```
Multiplicar 2 primos gigantes:        rápido (milisegundos)
Factorizar el resultado de vuelta:    con las computadoras actuales,
                                       tardaría más que la edad del universo
```

Todo el proceso real de cifrado y descifrado usa **exponenciación modular** (elevar un número a una potencia enorme y sacar el residuo módulo otro número gigante) — exactamente la combinación de la Lección 1.3 (exponentes) con esta lección (módulo). No vas a implementar RSA completo aquí — pero ahora entiendes _por qué_ funciona, en vez de solo saber que "protege tus contraseñas".

```python
# Exponenciación modular (la operación central de RSA), Python la trae integrada:
resultado = pow(base, exponente, modulo)   # (base ** exponente) % modulo, pero mucho más eficiente
```

---

### 5. Recapitulación

```
Residuo (Lección 1.1) → protagonista, no efecto secundario
    ↓
Notación de congruencia: a ≡ b (mod n)
    ↓
El reloj: la intuición perfecta de "dar la vuelta"
    ↓
Propiedades: suma y multiplicación modular por partes
    ↓
Hashing: módulo aplicado a organizar datos
    ↓
RSA: primos gigantes + exponenciación modular = criptografía real
```

Lo que en la 1.1 era "el sobrante de una división" resultó ser la base matemática de relojes, estructuras de datos, y la seguridad de cada compra que haces por internet.

---

## 🌌 Horizonte-Aplicado

_(esto no lo cubrimos aquí, pero lo vas a necesitar más adelante en ingeniería/programación)_

- **Funciones hash criptográficas reales (SHA-256, MD5)** — el hash simplificado que viste aquí es educativo, pero las funciones hash reales usadas en seguridad son mucho más complejas, diseñadas específicamente para que sea casi imposible encontrar dos datos distintos con el mismo hash.
- **Firmas digitales** — el mismo principio de RSA, pero al revés: en lugar de mantener un mensaje en secreto, se usa para probar que un mensaje realmente viene de quien dice venir, sin poder falsificarse.
- **Colisiones de hash y tablas hash en estructuras de datos** — qué pasa cuando dos datos distintos generan el mismo resultado de hash, y cómo los lenguajes de programación resuelven ese conflicto por debajo sin que tú lo notes.
- **Checksum y verificación de integridad** — cómo tu computadora sabe si un archivo descargado se corrompió en el camino, usando exactamente esta misma familia de ideas (una versión simple de hashing aplicada a integridad, no a secreto).

## 🏛️ Horizonte-Cultural

_(no lo vas a "usar" en un algoritmo, pero te da contexto y entrena tu forma de pensar)_

- **Carl Friedrich Gauss y el nacimiento formal de la aritmética modular** — Gauss formalizó esta rama de las matemáticas en su libro _Disquisitiones Arithmeticae_ (1801), escrito cuando tenía apenas 21 años; es considerado uno de los textos fundacionales de la teoría de números moderna.
- **RSA: el nombre viene de tres apellidos** — Rivest, Shamir y Adleman, quienes publicaron el algoritmo en 1977 en el MIT; lo curioso es que el servicio de inteligencia británico (GCHQ) había descubierto una idea equivalente unos años antes, pero la mantuvo en secreto por motivos de seguridad nacional y no se hizo pública hasta décadas después.
- **La criptografía en la Segunda Guerra Mundial** — mucho antes de RSA, máquinas como Enigma usaban principios matemáticos relacionados (sustitución y permutación) para cifrar mensajes militares; el trabajo de descifrado de Alan Turing en Bletchley Park es considerado uno de los eventos que aceleró el fin de la guerra.
- **Computación cuántica y el futuro de RSA** — existe un algoritmo teórico (el algoritmo de Shor) que, en una computadora cuántica suficientemente potente, podría factorizar números grandes mucho más rápido, lo cual pondría en riesgo la seguridad de RSA tal como existe hoy; es uno de los motivos por los que ya se investiga "criptografía post-cuántica".

---

## 🧠 Prompts para tu Tutor IA (NotebookLM)

**Modo Express** _(quiero repasar rápido el núcleo)_

> "Actúa como un profesor directo. Basándote únicamente en esta fuente, resume qué es la aritmética modular, cómo se relaciona con un reloj, y la idea central de RSA en 5 minutos de lectura. Sin rodeos."

**Modo Ingeniero** _(quiero conectar esto con programación)_

> "De los temas listados en 'Horizonte-Aplicado' de esta fuente, elige el que más se conecte con estructuras de datos o seguridad y explícamelo con un ejemplo de código real. Luego hazme una pregunta para comprobar que lo entendí."

**Modo Curioso** _(quiero contexto e historia)_

> "De los temas listados en 'Horizonte-Cultural' de esta fuente, elige uno y cuéntame su historia como una anécdota interesante. Al final, dime por qué eso ayuda a entender mejor por qué la criptografía moderna se basa en números primos."

**Modo Escéptico** _(quiero que me examinen)_

> "Actúa como un profesor escéptico y directo. Basándote únicamente en esta fuente, hazme un examen de 5 preguntas: pídeme calcular una congruencia módulo n desde cero, resolver un problema de reloj/día de la semana, y explicar con mis propias palabras por qué es fácil multiplicar dos primos gigantes pero difícil factorizar el resultado. Después de cada respuesta mía, dame retroalimentación y el porqué, nunca la respuesta directa antes de que yo intente."

**Modo Expansión** _(el núcleo se sintió corto y quiero más)_

> "Usando esta fuente como piso mínimo, explícame qué es el Pequeño Teorema de Fermat y cómo se relaciona con la exponenciación modular que usa RSA, sin salirte del nivel de esta lección."

---

## 🎯 Reto de la Comunidad

Antes de pasar a la Lección 2.4, responde esto en el canal de la materia:

1. Si hoy es miércoles (día 3, contando lunes=1) y quieres saber qué día será en 100 días, calcula el resultado usando aritmética modular y muestra tu operación completa.
2. Comprueba con números reales pequeños que `(a × b) % n = ((a % n) × (b % n)) % n`, usando `a = 25`, `b = 14`, `n = 6`.
3. Explica con tus propias palabras por qué RSA depende de que la factorización de números primos gigantes sea difícil, y qué pasaría con la seguridad de RSA si alguien inventara una forma súper rápida de factorizar cualquier número. (No necesitas saber matemáticas avanzadas para responder esto — es un problema de lógica, no de cálculo.)

> **Regla de la comunidad:** No postees la respuesta directa. Si alguien se equivoca, dale una pista, no la solución.

---

Siguiente lección → **2.4: Teoría de Conjuntos — Las Cajas que Contienen Todo**
