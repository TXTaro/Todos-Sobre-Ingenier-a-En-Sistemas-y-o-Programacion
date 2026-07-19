# Matemáticas Aplicadas — Módulo 2 — Lección 2.2: Álgebra Booleana (La Lógica de los Circuitos)

> **"Todo `if` que has escrito en tu vida es álgebra booleana disfrazada de código."**
> 
> En la Lección 1.2 dejamos una promesa: "un tipo distinto de álgebra donde las variables solo valen verdadero/falso". Aquí la cumplimos — y de paso vas a entender qué hay literalmente dentro de un procesador cuando evalúa una condición.

---

## 🎚️ Ubicación en el mapa

- **Módulo:** 2 — La Lógica de la Máquina (Matemáticas Discretas)
- **Nivel de esta lección:** Fundamento
- **Requiere haber visto:** Lección 1.2 (variables y expresiones algebraicas) y 2.1 (binario) — el álgebra booleana usa solo dos valores, exactamente los dos símbolos que ya conoces del binario.

---

## 🔩 Núcleo (lo esencial, no se salta)

### 0. ¿Qué es una variable booleana?

En la 1.2 viste variables que pueden valer cualquier número (`x = 7`, `x = -3`, `x = 0.5`...). Una **variable booleana** es mucho más restrictiva: solo puede valer una de dos cosas.

```
Verdadero (True / 1)
Falso     (False / 0)
```

No existe punto medio, no existe "más o menos verdadero". Esta restricción no es una limitación — es justamente lo que la hace perfecta para representar el estado de un interruptor (Lección 2.1): encendido o apagado, nada más.

```python
esta_prendido = True
tiene_permiso = False
```

---

### 1. Las 3 Operaciones Primitivas: AND, OR, NOT

Así como la aritmética tenía sus 4 operaciones básicas (Lección 1.1), el álgebra booleana tiene sus propias operaciones primitivas. Solo necesitas 3 para construir cualquier lógica posible.

#### 1.1 AND (Y): Ambas condiciones deben ser verdaderas

```
A AND B  →  verdadero SOLO SI A es verdadero Y B es verdadero
```

**Tabla de verdad** (todas las combinaciones posibles):

```
A       B       A AND B
False   False   False
False   True    False
True    False   False
True    True    True
```

```python
tiene_18_anos = True
tiene_identificacion = True

puede_entrar = tiene_18_anos and tiene_identificacion   # True
```

#### 1.2 OR (O): Basta con que una sea verdadera

```
A OR B  →  verdadero SI A es verdadero O B es verdadero (o ambos)
```

```
A       B       A OR B
False   False   False
False   True    True
True    False   True
True    True    True
```

```python
tiene_tarjeta = False
tiene_efectivo = True

puede_pagar = tiene_tarjeta or tiene_efectivo   # True
```

#### 1.3 NOT (NO): Invierte el valor

```
NOT A  →  lo opuesto de A
```

```
A       NOT A
False   True
True    False
```

```python
esta_bloqueado = False
puede_acceder = not esta_bloqueado   # True
```

---

### 2. Operaciones Derivadas: NAND, NOR, XOR

Estas no son "nuevas reglas mágicas" — son combinaciones de las 3 primitivas de arriba. Se deducen, no se memorizan.

#### 2.1 XOR (O exclusivo): Una u otra, pero no ambas

```
A XOR B  →  verdadero SOLO SI A y B son distintos entre sí
```

```
A       B       A XOR B
False   False   False
False   True    True
True    False   True
True    True    False
```

Diferencia clave con OR normal: en `A OR B`, si ambas son verdaderas, el resultado es verdadero. En XOR, si ambas son verdaderas, el resultado es **falso** — por eso se llama "exclusivo".

```python
# Ejemplo real: un interruptor de escalera con dos switches
# la luz enciende si EXACTAMENTE uno de los dos switches está activado
switch_arriba = True
switch_abajo = False

luz_encendida = switch_arriba != switch_abajo   # XOR en Python: True
```

#### 2.2 NAND y NOR: "NOT" aplicado después de AND/OR

```
A NAND B  =  NOT (A AND B)
A NOR B   =  NOT (A OR B)
```

Se deducen invirtiendo el resultado de la tabla de AND u OR. Esto importa porque, a nivel de hardware físico, **NAND por sí solo puede construir cualquier otra compuerta lógica** — es la pieza mínima con la que se arman procesadores completos (lo verás con más detalle si sigues hacia Sistemas).

---

### 3. Leyes del Álgebra Booleana: Se deducen, no se memorizan

Igual que con las leyes de exponentes (Lección 1.3), estas leyes no son arbitrarias — se comprueban armando la tabla de verdad de ambos lados y viendo que dan lo mismo.

#### 3.1 Leyes de De Morgan (las más útiles en programación real)

```
NOT (A AND B)  =  (NOT A) OR (NOT B)
NOT (A OR B)   =  (NOT A) AND (NOT B)
```

**Por qué te importa esto de verdad:** simplifica condiciones complicadas en código.

```python
# Antes (difícil de leer):
if not (usuario_activo and tiene_permiso):
    bloquear_acceso()

# Después de aplicar De Morgan (misma lógica, más claro):
if (not usuario_activo) or (not tiene_permiso):
    bloquear_acceso()
```

**Comprobación con tabla de verdad** (para `NOT (A AND B) = (NOT A) OR (NOT B)`):

```
A       B       A AND B   NOT(A AND B)   NOT A   NOT B   (NOT A) OR (NOT B)
False   False   False     True           True    True    True
False   True    False     True           True    False   True
True    False   False     True           False   True    True
True    True    True      False          False   False   False
```

Las columnas `NOT(A AND B)` y `(NOT A) OR (NOT B)` son idénticas en las 4 filas — por eso la ley es verdadera, no porque alguien lo haya decretado.

#### 3.2 Otras leyes útiles (mismo principio: se comprueban con tabla de verdad)

```
Doble negación:    NOT (NOT A) = A
Idempotencia:      A AND A = A         |    A OR A = A
Identidad:         A AND True = A      |    A OR False = A
Dominación:        A AND False = False |    A OR True = True
```

---

### 4. Compuertas Lógicas: Álgebra booleana hecha circuito físico

Cada operación que viste arriba tiene un símbolo estándar en electrónica, y existe como una pieza física real dentro de un chip:

```
AND:   ─┐
        ├── D─── salida
       ─┘

OR:    ─┐
        ├── D>── salida
       ─┘

NOT:   ─▷o── salida  (el círculo pequeño significa "invertido")
```

Un procesador entero — desde una calculadora hasta la CPU de tu computadora — es, en su nivel más físico, **millones de estas compuertas conectadas entre sí**, todas ejecutando AND, OR y NOT a velocidades de miles de millones de veces por segundo. No hay ninguna otra "magia" adicional: todo lo que tu código hace, eventualmente, se reduce a esto.

---

### 5. Recapitulación

```
Variables booleanas (solo 2 valores: True/False)
    ↓
3 operaciones primitivas: AND, OR, NOT
    ↓
Operaciones derivadas: XOR, NAND, NOR
    ↓
Leyes (De Morgan y otras) — se comprueban con tabla de verdad, no se memorizan
    ↓
Compuertas lógicas: la misma álgebra, hecha circuito físico
```

Cada `if`, `and`, `or`, `not` que has escrito en tu vida como programador es exactamente esta lección, con nombres distintos. La diferencia entre tú hoy y tú antes de esta lección es que ahora sabes _por qué_ funciona, no solo que funciona.

---

## 🌌 Horizonte-Aplicado

_(esto no lo cubrimos aquí, pero lo vas a necesitar más adelante en ingeniería/programación)_

- **Circuitos combinacionales y secuenciales** — cómo se combinan compuertas lógicas para construir sumadores binarios, memorias, y eventualmente un procesador completo; es el puente directo hacia Sistemas.
- **Cortocircuito lógico (short-circuit evaluation)** — por qué en la mayoría de lenguajes `A and B` ni siquiera evalúa `B` si `A` ya es falso; es una optimización real que afecta cómo debes ordenar tus condiciones en código.
- **Mapas de Karnaugh** — una herramienta visual para simplificar expresiones booleanas complicadas sin tener que hacer álgebra manual paso a paso; muy usada en diseño de circuitos.
- **Lógica difusa (fuzzy logic)** — un sistema que rompe la regla de "solo dos valores" y permite grados de verdad entre 0 y 1; se usa en control de electrodomésticos y sistemas de inteligencia artificial.

## 🏛️ Horizonte-Cultural

_(no lo vas a "usar" en un algoritmo, pero te da contexto y entrena tu forma de pensar)_

- **George Boole y el álgebra que lleva su nombre** — matemático autodidacta del siglo XIX que, sin saberlo, inventó el lenguaje matemático exacto que un siglo después haría posible la computación digital; nunca vio una computadora en su vida.
- **Claude Shannon: el puente entre Boole y el hardware real** — en su tesis de maestría de 1937 (llamada "la tesis más importante del siglo XX" por varios historiadores), Shannon demostró que los circuitos eléctricos podían implementar álgebra booleana directamente — esa idea es, literalmente, el fundamento de toda computadora moderna.
- **Por qué "bit" es la unidad de información, no solo de almacenamiento** — el mismo Shannon, más adelante, fundó la Teoría de la Información usando el bit como unidad matemática de "sorpresa" o incertidumbre — no solo como un 0 o 1 físico.
- **De Morgan y su rivalidad amistosa con Boole** — Augustus De Morgan (de quien vienen las leyes que viste arriba) y Boole se influenciaron mutuamente y llegaron a resultados similares casi al mismo tiempo, un ejemplo clásico de cómo las grandes ideas matemáticas suelen "estar en el aire" de una época.

---

## 🧠 Prompts para tu Tutor IA (NotebookLM)

**Modo Express** _(quiero repasar rápido el núcleo)_

> "Actúa como un profesor directo. Basándote únicamente en esta fuente, resume las 3 operaciones primitivas (AND, OR, NOT) y las leyes de De Morgan en 5 minutos de lectura, con un ejemplo de código para cada una. Sin rodeos."

**Modo Ingeniero** _(quiero conectar esto con programación)_

> "De los temas listados en 'Horizonte-Aplicado' de esta fuente, elige el que más se conecte con optimización de código o diseño de hardware y explícamelo con un ejemplo concreto. Luego hazme una pregunta para comprobar que lo entendí."

**Modo Curioso** _(quiero contexto e historia)_

> "De los temas listados en 'Horizonte-Cultural' de esta fuente, elige uno y cuéntame su historia como una anécdota interesante. Al final, dime por qué eso ayuda a entender mejor la conexión entre álgebra booleana y las computadoras modernas."

**Modo Escéptico** _(quiero que me examinen)_

> "Actúa como un profesor escéptico y directo. Basándote únicamente en esta fuente, hazme un examen de 5 preguntas: pídeme construir tablas de verdad desde cero para al menos dos operaciones, aplicar una ley de De Morgan a una condición de código, y explicar con mis propias palabras por qué XOR es distinto de OR. Después de cada respuesta mía, dame retroalimentación y el porqué, nunca la respuesta directa antes de que yo intente."

**Modo Expansión** _(el núcleo se sintió corto y quiero más)_

> "Usando esta fuente como piso mínimo, explícame qué es un mapa de Karnaugh y cómo se usa para simplificar una expresión booleana de 3 variables, sin salirte del nivel de esta lección. Dame un ejemplo completo paso a paso."

---

## 🎯 Reto de la Comunidad

Antes de pasar a la Lección 2.3, responde esto en el canal de la materia:

1. Construye la tabla de verdad completa de `A NAND B` desde cero (sin buscarla), y compárala con la de `A AND B` para confirmar que son exactamente opuestas.
2. Aplica la ley de De Morgan para simplificar esta condición de código: `not (edad >= 18 or tiene_permiso_padres)`. Escribe el resultado equivalente.
3. Explica con tus propias palabras por qué, en muchos lenguajes de programación, escribir `if usuario and usuario.nombre == "Ana":` es más seguro que `if usuario.nombre == "Ana" and usuario:` cuando `usuario` podría no existir. (Pista: cortocircuito lógico, mencionado en Horizonte-Aplicado — investígalo si hace falta.)

> **Regla de la comunidad:** No postees la respuesta directa. Si alguien se equivoca, dale una pista, no la solución.

---

Siguiente lección → **2.3: Aritmética Modular y Criptografía Básica**
