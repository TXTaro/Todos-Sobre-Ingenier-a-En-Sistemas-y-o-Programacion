# Programación — Módulo 1 — Lección 1.1: Pensamiento Computacional (Qué es un Algoritmo)

> **"Antes de aprender a hablarle a la computadora, aprende a pensar como ella espera que le hables."**
> 
> Esta lección no tiene una sola línea de código real. Y es a propósito. El error número uno de quien "aprende a programar" copiando tutoriales es que aprende sintaxis antes de aprender a pensar en pasos lógicos — y luego, cuando el tutorial no cubre exactamente su problema, se queda perdido. Aquí construimos el pensamiento primero. El código, en la 1.2, va a ser solo la forma de _escribir_ algo que ya sabes pensar.

---

## 🎚️ Ubicación en el mapa

- **Módulo:** 1 — The Core Logic (Fundamentos del Pensamiento)
- **Nivel de esta lección:** Fundamento
- **Requiere haber visto:** Nada de Programación todavía — pero si ya viste Matemáticas Módulo 1 (en especial la 1.4, Funciones como Máquinas), vas a reconocer varias ideas aquí, porque son la misma lógica vista desde otro ángulo.

---

## 🔩 Núcleo (lo esencial, no se salta)

### 0. ¿Qué es un algoritmo? (Nada nuevo, ya has hecho varios en tu vida)

Un **algoritmo** es una secuencia de pasos ordenados y precisos para resolver un problema. No es un concepto exclusivo de computadoras — una receta de cocina es un algoritmo, las instrucciones para armar un mueble son un algoritmo, incluso "cómo lavarte los dientes" es un algoritmo si lo desglosas paso a paso.

```
Algoritmo: "Cómo hacer un café"

1. Llenar la cafetera con agua
2. Poner el filtro
3. Agregar café molido
4. Encender la cafetera
5. Esperar a que termine
6. Servir en una taza
```

Lo que hace que esto sea un algoritmo (y no solo una idea vaga) es que:

- **Está ordenado:** el orden importa. No puedes servir antes de que termine.
- **Es preciso:** cada paso es una acción concreta, no ambigua.
- **Tiene un inicio y un final claro:** sabes cuándo empieza y cuándo termina.
- **Es repetible:** si sigues los mismos pasos, obtienes el mismo resultado.

Una computadora no "entiende" café ni cafeteras — pero si le das una secuencia de pasos igual de ordenada y precisa sobre números, texto, o lo que sea, los puede ejecutar sin fallar, siempre y cuando el algoritmo esté bien construido.

---

### 1. El problema real: las computadoras son extremadamente literales

Una persona puede seguir instrucciones ambiguas y "entender lo que quisiste decir". Una computadora no. Si le dices "prepara algo de comer", no tiene idea de qué hacer. Necesita cada paso desglosado sin ambigüedad.

```
❌ "Prepara un café"                (ambiguo, la máquina no sabe qué es "preparar")

✅ 1. Llenar cafetera con 500ml de agua
   2. Colocar filtro de papel
   3. Agregar 20g de café molido
   4. Presionar botón de encendido
   5. Esperar señal de "listo"
   6. Verter en taza
```

Esta obsesión por la precisión es la habilidad más importante que vas a construir en este módulo — más que cualquier sintaxis de cualquier lenguaje. Un desarrollador que piensa con precisión puede aprender cualquier lenguaje de programación en semanas. Uno que no, se queda copiando código sin entender por qué funciona (o por qué se rompe).

---

### 2. Pseudocódigo: escribir algoritmos sin preocuparte por la sintaxis todavía

El **pseudocódigo** es una forma de escribir algoritmos usando lenguaje casi natural, pero con estructura lógica clara — sin las reglas estrictas de un lenguaje de programación real (paréntesis exactos, punto y coma, etc.). Es el boceto antes del código final.

```
INICIO
    Pedir número al usuario
    SI número es par ENTONCES
        Mostrar "Es par"
    SINO
        Mostrar "Es impar"
    FIN SI
FIN
```

Nadie te va a corregir la sintaxis del pseudocódigo — su único trabajo es que **tú** entiendas la lógica antes de traducirla a un lenguaje real. Vas a usar pseudocódigo constantemente en este módulo antes de que aparezca Python en la 1.2.

---

### 3. Las 3 estructuras universales de cualquier algoritmo

No importa qué tan complejo sea un programa — un videojuego, una red social, un sistema bancario — **todo** algoritmo se construye combinando solamente estas tres estructuras:

#### 3.1 Secuencia: pasos uno detrás de otro

```
Paso 1 → Paso 2 → Paso 3 → Paso 4
```

Como la receta del café de arriba. Cada paso ocurre una vez, en orden, sin repetirse ni saltarse nada.

#### 3.2 Selección (decisión): elegir un camino según una condición

```
SI (condición) ENTONCES
    hacer esto
SINO
    hacer esto otro
FIN SI
```

Esto es literalmente una **inecuación o condición lógica**, como las que ya viste en Matemáticas Lección 1.2. La computadora evalúa si algo es verdadero o falso, y decide qué camino tomar. Lo vas a formalizar a fondo en la Lección 1.3 de este módulo.

#### 3.3 Iteración (repetición): repetir algo mientras se cumpla una condición

```
MIENTRAS (condición sea verdadera)
    repetir esto
FIN MIENTRAS
```

Esto es exactamente lo que ya mencionamos como analogía en Matemáticas (la multiplicación como "suma repetida" usando un `for`). Aquí lo vas a formalizar en la Lección 1.4.

**El punto clave:** con solo estas 3 estructuras (secuencia, selección, iteración) puedes construir cualquier programa que existe. No hay una cuarta estructura mágica escondida — todo lo demás que veas en programación es una combinación más elaborada de estas tres.

---

### 4. Diagramas de flujo: dibujar el algoritmo antes de escribirlo

Un **diagrama de flujo** es la versión visual de un algoritmo. Útil para "ver" la lógica antes de escribirla en pseudocódigo o código real.

```
Símbolos básicos:

  ┌─────────┐
  │ Inicio  │   → Óvalo: inicio o fin
  └────┬────┘
       │
  ┌────▼────┐
  │ Acción  │   → Rectángulo: un paso/acción
  └────┬────┘
       │
    ◇──▼──◇
   ╱ ¿Sí?  ╲   → Rombo: una decisión (sí/no)
   ╲       ╱
    ◇──┬──◇
       │
  ┌────▼────┐
  │   Fin   │
  └─────────┘
```

Ejemplo completo — "¿Puedo cruzar la calle?":

```
[Inicio]
    ↓
[Mirar ambos lados]
    ↓
 ¿Hay carros? ──Sí──→ [Esperar] ──┐
    │No                            │
    ↓                              │
[Cruzar la calle] ◄────────────────┘
    ↓
 [Fin]
```

Fíjate que este diagrama usa las 3 estructuras: secuencia (mirar → decidir → cruzar), selección (¿hay carros?), e iteración implícita (si esperas, vuelves a evaluar la condición).

---

### 5. Practicando: de problema real a algoritmo

Tomemos un problema simple y construyamos su algoritmo paso a paso, sin código, solo lógica:

**Problema:** _"Determinar si una persona puede votar."_

**Paso 1 — Identifica el input (qué información necesitas):**

```
La edad de la persona
```

**Paso 2 — Identifica la lógica de decisión:**

```
Si la edad es 18 o más → puede votar
Si la edad es menor a 18 → no puede votar
```

**Paso 3 — Escríbelo en pseudocódigo:**

```
INICIO
    Pedir edad
    SI edad >= 18 ENTONCES
        Mostrar "Puede votar"
    SINO
        Mostrar "No puede votar"
    FIN SI
FIN
```

Este mismo proceso — identificar input, identificar lógica, escribir pseudocódigo — es el que vas a repetir para CUALQUIER problema de programación que enfrentes, sin importar qué tan complejo se vuelva más adelante.

---

### 6. Recapitulación

```
Algoritmo = secuencia de pasos precisos y ordenados
    ↓
Pseudocódigo = escribir la lógica sin preocuparte de sintaxis todavía
    ↓
3 estructuras universales: Secuencia, Selección, Iteración
    ↓
Diagramas de flujo = versión visual del algoritmo
    ↓
Método: identificar input → identificar lógica → escribir pseudocódigo
```

Con esto ya piensas como programador, aunque todavía no hayas escrito una sola línea de código real. En la Lección 1.2 vas a tomar exactamente este tipo de lógica y traducirla, por primera vez, a Python.

---

## 🌌 Horizonte-Aplicado

_(esto no lo cubrimos aquí, pero lo vas a necesitar más adelante en programación real)_

- **Complejidad algorítmica (Big O)** — ya lo mencionamos en Matemáticas 1.3 (exponentes); una vez que sepas escribir algoritmos, vas a aprender a medir qué tan "caro" es un algoritmo en tiempo y memoria, y a elegir el más eficiente entre varias soluciones posibles al mismo problema.
- **Algoritmos de búsqueda y ordenamiento** — problemas clásicos (buscar un elemento, ordenar una lista) que se resuelven con las mismas 3 estructuras que viste aquí, pero combinadas de formas cada vez más ingeniosas; son la base de casi cualquier entrevista técnica de programación.
- **Diagramas de flujo profesionales (UML, u otros estándares)** — el diagrama ASCII que viste aquí es una versión simplificada; existen notaciones estándar de la industria para documentar lógica de sistemas completos, que verás si trabajas en equipos grandes.

## 🏛️ Horizonte-Cultural

_(no lo vas a "usar" en un commit, pero te da contexto y entrena tu forma de pensar)_

- **La palabra "algoritmo" viene de una persona real** — se deriva del nombre de Al-Juarismi (Al-Khwarizmi), el mismo matemático persa del siglo IX que ya mencionamos en Matemáticas 1.2 como origen de la palabra "álgebra"; es la misma persona detrás de las dos palabras más importantes de este temario técnico.
- **Ada Lovelace y el primer algoritmo "para máquina"** — en el siglo XIX, antes de que existiera ninguna computadora electrónica, Ada Lovelace escribió lo que se considera el primer algoritmo diseñado específicamente para ser ejecutado por una máquina (el motor analítico de Charles Babbage, que nunca se construyó completo en su época).
- **¿Por qué las 3 estructuras (secuencia, selección, iteración) son "suficientes"?** — esto no es una casualidad de diseño, es un resultado matemático demostrado (el Teorema de la Programación Estructurada, de Böhm y Jacopini, 1966); investigar por qué se puede _demostrar_ matemáticamente que solo necesitas estas 3 es un buen ejercicio de rigor lógico.

---

## 🧠 Prompts para tu Tutor IA (NotebookLM)

**Modo Express** _(quiero repasar rápido el núcleo)_

> "Actúa como un profesor directo. Basándote únicamente en esta fuente, resume qué es un algoritmo, las 3 estructuras universales, y el método de 3 pasos para convertir un problema en pseudocódigo, con un ejemplo de cada una."

**Modo Expansión** _(quiero más de lo que dice la lección)_

> "Esta fuente es la base mínima. Dame 5 problemas cotidianos distintos (no técnicos) y ayúdame a convertir cada uno en pseudocódigo usando el método de esta fuente, sin resolvérmelos tú directamente — solo guíame con preguntas."

**Modo Ingeniero** _(quiero conectar esto con programación real)_

> "De los temas listados en 'Horizonte-Aplicado' de esta fuente, explícame qué es la complejidad algorítmica (Big O) de forma introductoria, conectándolo con la idea de 'iteración' que vimos en el núcleo."

**Modo Curioso** _(quiero contexto e historia)_

> "Cuéntame sobre Ada Lovelace y el Teorema de la Programación Estructurada mencionados en el Horizonte-Cultural de esta fuente, y explícame por qué el segundo es relevante para lo que aprendí en el núcleo sobre las 3 estructuras universales."

**Modo Escéptico** _(quiero que me examinen)_

> "Actúa como un profesor escéptico y directo. Basándote únicamente en esta fuente, dame 3 problemas cotidianos y pídeme que identifique el input, la lógica de decisión, y escriba el pseudocódigo para cada uno, sin resolvérmelos tú primero. Corrígeme con el porqué, no me des la respuesta antes de que yo intente."

---

## 🎯 Reto de la Comunidad

Antes de pasar a la Lección 1.2, responde esto en el canal de la materia:

1. Escribe el algoritmo (en pasos normales, no pseudocódigo todavía) para "cómo instalar una aplicación en tu celular", identificando claramente dónde hay una decisión (selección) y dónde hay una repetición (iteración), si las hay.
2. Convierte a pseudocódigo: "Un programa que revisa si una contraseña tiene al menos 8 caracteres".
3. ¿Por qué crees que la iteración (repetición) es más eficiente que escribir el mismo paso 100 veces seguidas? Conéctalo con lo que ya viste en Matemáticas sobre la multiplicación como suma repetida.

> **Regla de la comunidad:** No postees la respuesta directa de otros. Si alguien se equivoca, dale una pista, no la solución.

---

Siguiente lección → **1.2: Variables y Tipos de Datos — De la Incógnita al Código Real**
