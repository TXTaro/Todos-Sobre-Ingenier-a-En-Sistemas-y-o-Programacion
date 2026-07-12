# Matemáticas Aplicadas — Módulo 1 — Lección 1.1: El Origen Atómico (Aritmética desde el Átomo)

> **"Antes de correr cualquier script, la máquina aprende a contar."**
> 
> Esta lección no es un repaso aburrido de primaria. Es una reconstrucción lógica. Vas a entender _por qué_ los números se comportan como se comportan, no simplemente _cómo_ usarlos mecánicamente. Si en algún momento sentiste que las mates "no eran lo tuyo", lo más probable es que nadie te explicó la lógica detrás del juego.

---

## 🎚️ Ubicación en el mapa

- **Módulo:** 1 — El Taller de Reparación (Bases desde Cero)
- **Nivel de esta lección:** Fundamento
- **Requiere haber visto:** Nada. Este es el punto cero, el átomo de todo el temario de Matemáticas.

---

## 🔩 Núcleo (lo esencial, no se salta)

### 0. ¿Qué es un número? (El átomo de todo)

Antes de sumar o restar, hay que entender qué es un número.

Un número es una etiqueta que le ponemos a una cantidad. No existe en la naturaleza; lo inventamos los humanos para representar _cuántos_ objetos hay, _qué tan lejos_ está algo, o _cuánto_ tiempo pasó.

El sistema que usamos hoy se llama **sistema decimal** (base 10), y usamos 10 símbolos para representar cualquier cantidad del universo:

```
0, 1, 2, 3, 4, 5, 6, 7, 8, 9
```

Cuando se acaban esos símbolos, los combinamos: 10, 11, 12... hasta el infinito. Esto se llama **valor posicional**: el lugar donde pones el dígito cambia su valor.

Ejemplo:

- El `5` en `500` vale quinientos.
- El `5` en `50` vale cincuenta.
- El `5` en `5` vale cinco.
- El mismo símbolo, tres valores distintos. Eso es el poder de la posición.

> **Pregunta para la comunidad:** ¿Por qué usamos base 10 y no base 8 o base 16? (Spoiler: los dedos. Y spoiler mayor: las computadoras usan base 2. Lo verás en el Módulo 2 de Matemáticas.)

---

### 1. Las 4 Operaciones Básicas: Las instrucciones primitivas

Si el procesador tiene sus instrucciones básicas (MOV, ADD, SUB...), el sistema numérico tiene las suyas. Son cuatro, y todo lo demás en matemáticas es una combinación de ellas.

#### 1.1 Suma (Adición)

**¿Qué significa?** Juntar dos cantidades en una sola.

```
3 + 4 = 7
```

Significa: si tienes 3 objetos y agregas 4 más, ahora tienes 7.

**Propiedades que debes entender (no memorizar):**

**Conmutativa:** el orden no importa.

```
3 + 4 = 7
4 + 3 = 7
```

¿Por qué? Porque juntar 3 cosas con 4 es lo mismo que juntar 4 con 3. La cantidad total no cambia.

**Asociativa:** cómo agrupas tampoco importa.

```
(2 + 3) + 4 = 9
2 + (3 + 4) = 9
```

**Elemento neutro:** el 0 no cambia nada.

```
7 + 0 = 7
```

---

#### 1.2 Resta (Sustracción)

**¿Qué significa?** Quitar una cantidad de otra.

```
9 - 4 = 5
```

La resta es la **operación inversa** de la suma. Si la suma construye, la resta destruye. Esa relación (operación ↔ operación inversa) es la base del álgebra que verás en la 1.2.

```
4 + 5 = 9   →   9 - 5 = 4   →   9 - 4 = 5
```

**Ojo importante:** la resta NO es conmutativa.

```
9 - 4 = 5     ✅
4 - 9 = -5    ← resultado negativo, diferente
```

Aquí aparecen los **números negativos**: cantidades por debajo del cero. Una deuda, una temperatura bajo cero, un índice que va hacia atrás.

```
Línea numérica:   ... -3, -2, -1, 0, 1, 2, 3 ...
```

---

#### 1.3 Multiplicación

**¿Qué significa?** Suma repetida. Nada más.

```
4 × 3 = 12   →   4 + 4 + 4 = 12
```

¿Por qué inventamos la multiplicación si podíamos seguir sumando? Porque es más rápido — el mismo motivo por el que usamos bucles `for` en lugar de copiar y pegar código 100 veces.

**Propiedades:**

- **Conmutativa:** `4 × 3 = 3 × 4`
- **Asociativa:** `(2 × 3) × 4 = 2 × (3 × 4)`
- **Distributiva** (la más poderosa, base del álgebra):

```
3 × (4 + 2) = (3 × 4) + (3 × 2) = 18
```

- **Elemento neutro:** `7 × 1 = 7`
- **Elemento absorbente:** `7 × 0 = 0`

---

#### 1.4 División

**¿Qué significa?** Repartir una cantidad en partes iguales.

```
12 ÷ 4 = 3
```

La división es la **operación inversa** de la multiplicación.

```
4 × 3 = 12   →   12 ÷ 4 = 3
```

**El residuo:** cuando la división no es exacta, sobran cosas.

```
13 ÷ 4 = 3, residuo 1
```

En programación, el operador `%` (módulo) te da exactamente ese residuo:

```python
13 % 4 = 1
```

**Regla crítica:** no puedes dividir entre cero. ¿En cuántos grupos de 0 puedes repartir 7 cosas? No tiene respuesta lógica. Por eso en programación, dividir entre cero rompe el programa (`ZeroDivisionError` en Python).

---

### 2. Jerarquía de Operaciones: Las reglas de precedencia

```
1. Paréntesis  ()
2. Potencias y raíces  (las verás en la Lección 1.3)
3. Multiplicación y División  (de izquierda a derecha)
4. Suma y Resta  (de izquierda a derecha)
```

```
2 + 3 × 4 = 2 + 12 = 14   ✅  (la multiplicación va antes)
(2 + 3) × 4 = 5 × 4 = 20  ← los paréntesis fuerzan el orden
```

Los paréntesis son como los `()` en el código: le dicen al sistema qué evaluar primero.

---

### 3. Factores, Múltiplos y Divisibilidad

**Factores de un número:** todos los que lo dividen sin residuo.

```
Factores de 12: 1, 2, 3, 4, 6, 12
```

**Múltiplos de un número:** resultados de multiplicarlo por 1, 2, 3, 4...

```
Múltiplos de 3: 3, 6, 9, 12, 15, 18, 21...
```

**Números primos:** solo tienen dos factores, el 1 y ellos mismos.

```
2, 3, 5, 7, 11, 13, 17, 19, 23...
```

Cualquier número puede descomponerse en primos (Teorema Fundamental de la Aritmética). Esto se usa en criptografía moderna (RSA).

**Divisibilidad rápida:**

- Entre 2: si termina en par (0, 2, 4, 6, 8).
- Entre 3: si la suma de sus dígitos es divisible entre 3.
- Entre 5: si termina en 0 o 5.
- Entre 10: si termina en 0.

---

### 4. Fracciones y Decimales: Cuando el entero no alcanza

**Fracción:** parte de un entero. El denominador dice en cuántas partes se dividió el entero; el numerador dice cuántas de esas partes tienes.

**Tipos:**

- **Propia:** numerador menor. `3/4` → 0.75
- **Impropia:** numerador mayor. `5/3` → más de 1
- **Mixta:** entero + fracción. `1 y 2/3`

**Operaciones con fracciones:**

```
Suma (mismo denominador):     1/4 + 2/4 = 3/4
Suma (distinto denominador):  1/2 + 1/3 = 3/6 + 2/6 = 5/6
Multiplicación:                2/3 × 3/4 = 6/12
División (por el inverso):     2/3 ÷ 4/5 = 2/3 × 5/4 = 10/12
```

Para sumar con distinto denominador, buscas el mínimo común múltiplo (MCM) de los denominadores.

**Decimales:** otra forma de escribir fracciones, usando el sistema posicional.

```
0.75 = 75/100 = 3/4
0.5  = 5/10   = 1/2
```

```
0 . 1         2          3
    ↑         ↑          ↑
  décimas centésimas milésimas
```

---

### 5. Porcentajes: La fracción de los 100

```
75% = 75/100 = 0.75
```

**Calcular un porcentaje de un número:**

```
30% de 200 → 200 × 0.30 = 60
```

**Encontrar qué porcentaje representa una parte:**

```
45 de 180 → (45/180) × 100 = 25%
```

Lo usarás constantemente: rendimiento de CPU, porcentaje de batería, métricas de error en servidores.

---

### 6. Redondeo y Estimación

- Si el dígito siguiente es **5 o más** → redondeas hacia arriba.
- Si es **4 o menos** → redondeas hacia abajo.

```
3.67 → 3.7   (el 7 ≥ 5, sube)
3.62 → 3.6   (el 2 < 5, baja)
```

**Truncar vs. redondear** en programación:

- `round(3.7)` → 4 (redondea)
- `int(3.7)` → 3 (trunca, corta el decimal)

---

### 7. Recapitulación

```
Números y valor posicional
    ↓
4 operaciones básicas
    ↓
Jerarquía de operaciones
    ↓
Factores, múltiplos y primos
    ↓
Fracciones y decimales
    ↓
Porcentajes
    ↓
Redondeo
```

Cada bloque es un cimiento. Sin ellos, el álgebra, las funciones, la probabilidad y todo lo que viene después se cae.

---

## 🌌 Horizonte-Aplicado

_(esto no lo cubrimos aquí, pero lo vas a necesitar más adelante en ingeniería/programación)_

- **Notación científica** — cómo se escriben números gigantes o diminutos (`3.2 × 10⁸`) sin morir escribiendo ceros; se usa en cómputo científico y física.
- **Precisión de punto flotante** — por qué `0.1 + 0.2` no da exactamente `0.3` en casi cualquier lenguaje de programación. Tiene que ver con cómo se guardan los decimales en binario.
- **Aritmética modular avanzada** — el `%` que ya viste es la punta del iceberg; es la base de hashing, relojes de 24h, y gran parte de la criptografía.
- **Algoritmos de multiplicación rápida** — la multiplicación "a mano" que aprendiste no es la más eficiente para números gigantescos; existen métodos como Karatsuba que las computadoras usan para ir más rápido.

## 🏛️ Horizonte-Cultural

_(no lo vas a "usar" en un algoritmo, pero te da contexto y entrena tu forma de pensar)_

- **La historia del cero** — el cero como número (no solo como "nada") tardó siglos en inventarse y viajó de la India al mundo árabe antes de llegar a Europa. Sin él, el valor posicional que viste arriba no existiría.
- **Sistemas de numeración antiguos** — los romanos no tenían valor posicional (`IX` vs `XI`), los babilonios contaban en base 60 (por eso el reloj tiene 60 minutos), los mayas en base 20. Ver otros sistemas te hace entender qué tan poderosa es la idea de "posición" que usamos hoy.
- **¿Por qué los primos son "el ADN de los números"?** — el Teorema Fundamental de la Aritmética es una de las ideas más elegantes de las matemáticas, y entender su demostración (no solo su enunciado) es un ejercicio de lógica pura que no necesitas para programar, pero que afila la mente.
- **La guerra entre fracciones y decimales** — culturas distintas resolvieron "la parte de un entero" de formas distintas a lo largo de la historia; ver por qué unas ganaron terreno sobre otras dice mucho de cómo evoluciona una herramienta cuando se vuelve estándar.

---

## 🧠 Prompts para tu Tutor IA (NotebookLM)

Sube esta lección como fuente en tu cuaderno y elige el modo según lo que necesites hoy:

**Modo Express** _(quiero repasar rápido el núcleo)_

> "Actúa como un profesor directo. Basándote únicamente en esta fuente, resume el núcleo de esta lección en 5 minutos de lectura, con un ejemplo por cada operación básica. Sin rodeos."

**Modo Ingeniero** _(quiero conectar esto con programación)_

> "De los temas listados en 'Horizonte-Aplicado' de esta fuente, elige el que más se conecte con programación o hardware y explícamelo con un ejemplo de código real. Luego hazme una pregunta para comprobar que lo entendí."

**Modo Curioso** _(quiero contexto e historia)_

> "De los temas listados en 'Horizonte-Cultural' de esta fuente, elige uno y cuéntame su historia como si fuera una anécdota interesante, no una clase aburrida. Al final, dime por qué eso ayuda a entender mejor el núcleo de la lección."

**Modo Escéptico** _(quiero que me examinen)_

> "Actúa como un profesor de matemáticas escéptico y directo. Basándote únicamente en el contenido de esta fuente, hazme un examen de 5 preguntas. Mezcla opción múltiple, procedimientos paso a paso, y al menos una donde tenga que explicar el concepto con mis propias palabras sin usar fórmulas. Después de cada respuesta mía, dame retroalimentación y el porqué, nunca la respuesta directa antes de que yo intente."

---

## 🎯 Reto de la Comunidad

Antes de pasar a la Lección 1.2, responde esto en el canal de la materia:

1. ¿Por qué `13 % 4 = 1` en Python? Explícalo con la definición de residuo, no con el resultado.
2. Si un servidor tiene el 40% de su RAM usada y la RAM total es 16 GB, ¿cuántos GB están libres?
3. ¿Qué tiene de especial el número 1? (Pista: no es primo. Investiga por qué y demuéstralo lógicamente.)

> **Regla de la comunidad:** No postees la respuesta directa. Si alguien se equivoca, dale una pista, no la solución.

---

Siguiente lección → **1.2: Inventando la Incógnita — El Nacimiento de la x**
