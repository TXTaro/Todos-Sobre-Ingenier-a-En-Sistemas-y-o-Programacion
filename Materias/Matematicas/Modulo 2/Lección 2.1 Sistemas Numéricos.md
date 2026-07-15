# Matemáticas Aplicadas — Módulo 2 — Lección 2.1: Sistemas Numéricos (El Árbol Genealógico del Decimal)

> **"El sistema decimal no es 'el normal' y el binario 'el raro de las computadoras'. Son la misma idea — valor posicional — contada con distinta cantidad de dedos."**
> 
> En la Lección 1.1 dejamos una pregunta abierta: ¿por qué usamos base 10, y por qué las computadoras usan base 2? Aquí la respondemos, y de paso vas a aprender a leer el idioma nativo de cualquier procesador.

---

## 🎚️ Ubicación en el mapa

- **Módulo:** 2 — La Lógica de la Máquina (Matemáticas Discretas)
- **Nivel de esta lección:** Fundamento (apertura de módulo)
- **Requiere haber visto:** Lección 1.1 (valor posicional, sistema decimal) — vamos a reciclar esa misma lógica, solo que cambiando la base.

---

## 🔩 Núcleo (lo esencial, no se salta)

### 0. Recordando el valor posicional (Lección 1.1)

En la 1.1 viste que el `5` en `500`, `50` y `5` vale distinto según su posición. Eso no es exclusivo del sistema decimal — es una propiedad de **cualquier sistema posicional**, sin importar cuántos símbolos uses.

La fórmula real detrás del decimal es esta (aunque nunca te la hayan mostrado así):

```
500 = 5 × 10² + 0 × 10¹ + 0 × 10⁰
```

Cada posición vale una potencia de la base (aquí, base 10), multiplicada por el dígito que está ahí. Esta es la clave de toda la lección: **cambia la base, y todo lo demás funciona exactamente igual.**

---

### 1. ¿Por qué la computadora usa base 2?

Un interruptor eléctrico solo tiene dos estados posibles: **encendido** o **apagado**. No hay un estado intermedio confiable a nivel de hardware — por eso toda computadora, en su nivel más físico, solo puede representar dos símbolos: `0` y `1`.

```
0 = apagado (sin voltaje)
1 = encendido (con voltaje)
```

A esto se le llama **sistema binario (base 2)**. Cada posición ahora vale una potencia de 2, no de 10:

```
1011 (binario) = 1×2³ + 0×2² + 1×2¹ + 1×2⁰
               = 8 + 0 + 2 + 1
               = 11 (decimal)
```

Cada dígito binario se llama **bit** (binary digit). Un grupo de 8 bits se llama **byte** — y ese es el motivo por el que la RAM y el almacenamiento se miden en potencias de 2 (recuerda el Horizonte-Aplicado de la Lección 1.3: memoria de computadora).

---

### 2. Convertir de Binario a Decimal

Igual que descompusiste `500` arriba, descompones un binario: multiplicas cada dígito por su potencia de 2 correspondiente y sumas.

```
Binario:    1  0  1  1
Posición:   2³ 2² 2¹ 2⁰
Valor:      8  4  2  1

1×8 + 0×4 + 1×2 + 1×1 = 8 + 0 + 2 + 1 = 11
```

```
1011 (binario) = 11 (decimal)
```

---

### 3. Convertir de Decimal a Binario

Aquí usamos **divisiones sucesivas entre 2**, guardando el residuo en cada paso (recuerda el residuo de la Lección 1.1 — el mismo concepto, aplicado en cadena).

```
Convertir 13 a binario:

13 ÷ 2 = 6   residuo 1
 6 ÷ 2 = 3   residuo 0
 3 ÷ 2 = 1   residuo 1
 1 ÷ 2 = 0   residuo 1

Lees los residuos de abajo hacia arriba: 1101
```

```
13 (decimal) = 1101 (binario)
```

**Verificación (regresando por el método de la sección 2):**

```
1101 = 1×8 + 1×4 + 0×2 + 1×1 = 8+4+0+1 = 13   ✅
```

En Python, esto ya viene resuelto, pero saber hacerlo a mano es lo que te permite entender _qué_ está haciendo la función por dentro:

```python
bin(13)      # '0b1101'
int('1101', 2)   # 13
```

---

### 4. Octal (Base 8) y Hexadecimal (Base 16): Atajos para leer binario

Escribir binario largo a mano es tedioso y propenso a errores (`11010110101` — ¿seguro que copiaste bien todos los bits?). Por eso existen dos "atajos" que agrupan bits:

**Hexadecimal (base 16):** agrupa cada **4 bits** en un solo símbolo. Como base 10 no alcanza para 16 símbolos, se usan letras:

```
0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F
                              (A=10, B=11, C=12, D=13, E=14, F=15)
```

```
Binario:  1101 0110
Hex:        D    6
```

`11010110` (binario) = `D6` (hexadecimal). Mucho más corto de escribir, mismo valor exacto.

**Octal (base 8):** agrupa cada **3 bits**. Menos común hoy, pero lo vas a ver en permisos de archivos de Linux (`chmod 755`) — eso es literalmente octal.

```
Binario:  111 101
Octal:     7   5
```

**¿Por qué existen estos atajos y no otros?** Porque 8 = 2³ y 16 = 2⁴ — son potencias exactas de 2, así que la conversión bit-a-símbolo es directa, sin residuos raros. Por eso nadie usa "base 7" como atajo: no divide limpio a la base 2.

```python
hex(214)     # '0xd6'
oct(214)     # '0o326'
```

---

### 5. Recapitulación

```
Valor posicional (Lección 1.1, base 10)
    ↓
Mismo principio, base 2 → Binario (el idioma del hardware)
    ↓
Conversión decimal ↔ binario (multiplicar potencias / dividir sucesivamente)
    ↓
Hexadecimal y Octal → atajos legibles para humanos, exactos en potencias de 2
```

No memorizaste una tabla de conversión — dedujiste que **cualquier base funciona con la misma lógica posicional**, solo cambia el número de símbolos disponibles. Esa es la mentalidad que te va a servir cuando te encuentres, más adelante, con cosas como Base64 en desarrollo web.

---

## 🌌 Horizonte-Aplicado

_(esto no lo cubrimos aquí, pero lo vas a necesitar más adelante en ingeniería/programación)_

- **Direcciones de memoria y colores en hexadecimal** — cuando veas un color web como `#FF5733` o una dirección de memoria como `0x7FFA3C`, ahora sabes exactamente qué representa cada par de símbolos: 4 bits agrupados.
- **Complemento a dos (two's complement)** — cómo representan las computadoras los números _negativos_ en binario, ya que un interruptor no tiene un estado de "signo menos"; es la base de por qué el desbordamiento (_overflow_) de enteros rompe programas.
- **ASCII y Unicode** — cada letra que escribes en un teclado tiene, por debajo, un número binario asignado; entender bases numéricas es el primer paso para entender cómo el texto se convierte en bits.
- **Base64** — un sistema de codificación (no exactamente una "base numérica" pura, pero basado en la misma lógica de agrupar bits) usado constantemente para transmitir imágenes o archivos dentro de texto plano, como en APIs web.

## 🏛️ Horizonte-Cultural

_(no lo vas a "usar" en un algoritmo, pero te da contexto y entrena tu forma de pensar)_

- **Leibniz y el sueño del binario** — Gottfried Leibniz formalizó el sistema binario en el siglo XVII, mucho antes de que existiera la electrónica; le fascinaba la idea filosófica de representar todo el universo con solo dos símbolos (0 y 1, que para él simbolizaban "la nada" y "todo").
- **El I Ching y el binario milenario** — siglos antes que Leibniz, el I Ching chino ya usaba un sistema de líneas partidas/completas (esencialmente binario) para representar 64 combinaciones; Leibniz mismo reconoció esta coincidencia cuando se enteró de su existencia.
- **Por qué los babilonios eligieron base 60** — mencionado brevemente en la 1.1: su sistema sigue vivo hoy en los 60 minutos de una hora y los 360° de un círculo. Comparar por qué esa base "sobrevivió" culturalmente mientras otras desaparecieron es un buen ejercicio de historia de la ciencia.
- **La computadora que no usó binario** — la Setun, una computadora soviética de los años 50, experimentó con lógica _ternaria_ (base 3) en lugar de binaria; nunca se popularizó, pero es un recordatorio de que el binario no era la única opción posible, solo la que ganó por practicidad de hardware.

---

## 🧠 Prompts para tu Tutor IA (NotebookLM)

**Modo Express** _(quiero repasar rápido el núcleo)_

> "Actúa como un profesor directo. Basándote únicamente en esta fuente, resume cómo convertir decimal a binario y binario a hexadecimal en 5 minutos de lectura, con un ejemplo numérico de cada conversión. Sin rodeos."

**Modo Ingeniero** _(quiero conectar esto con programación)_

> "De los temas listados en 'Horizonte-Aplicado' de esta fuente, elige el que más se conecte con desarrollo de software real (memoria, colores, o codificación de texto) y explícamelo con un ejemplo concreto. Luego hazme una pregunta para comprobar que lo entendí."

**Modo Curioso** _(quiero contexto e historia)_

> "De los temas listados en 'Horizonte-Cultural' de esta fuente, elige uno y cuéntame su historia como una anécdota interesante, no una clase aburrida. Al final, dime por qué eso ayuda a entender mejor por qué el binario se volvió el estándar."

**Modo Escéptico** _(quiero que me examinen)_

> "Actúa como un profesor de matemáticas escéptico y directo. Basándote únicamente en esta fuente, hazme un examen de 5 preguntas: mezcla conversiones decimal-binario paso a paso, una conversión a hexadecimal, y al menos una donde tenga que explicar con mis propias palabras por qué la computadora usa base 2 y no base 10. Después de cada respuesta mía, dame retroalimentación y el porqué, nunca la respuesta directa antes de que yo intente."

**Modo Expansión** _(el núcleo se sintió corto y quiero más)_

> "Usando esta fuente como piso mínimo, explícame el complemento a dos (two's complement) para representar números negativos en binario, sin salirte del nivel de esta lección. Dame un ejemplo numérico completo, paso a paso."

---

## 🎯 Reto de la Comunidad

Antes de pasar a la Lección 2.2, responde esto en el canal de la materia:

1. Convierte `29` (decimal) a binario mostrando cada división y su residuo, y verifica tu resultado regresándolo a decimal.
2. Convierte el binario `11110000` directo a hexadecimal (pista: agrupa de 4 en 4 bits, no lo pases por decimal primero).
3. ¿Por qué crees que nadie usa "base 5" o "base 9" como atajo de lectura del binario, a diferencia del octal y el hexadecimal? Explícalo con la lógica de potencias exactas de 2, no adivinando.

> **Regla de la comunidad:** No postees la respuesta directa. Si alguien se equivoca, dale una pista, no la solución.

---

Siguiente lección → **2.2: Álgebra Booleana — La Lógica de los Circuitos** ****
