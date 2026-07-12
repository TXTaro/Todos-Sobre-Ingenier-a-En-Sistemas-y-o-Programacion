# Sistemas — Módulo 1 — Lección 1.1: ¿Qué es una Computadora? (Hardware vs. Software)

> **"Todo el código que escribiste en Programación es puro pensamiento hasta que algo físico lo ejecuta. Esta materia es sobre ese 'algo físico'."**
> 
> Hasta ahora has aprendido a pensar en algoritmos y a escribirlos en Python. Pero nunca nos detuvimos a ver **dónde** corre eso realmente. Esta lección es el mapa general de las partes físicas de una computadora — sin profundizar todavía en ninguna, eso viene en las siguientes lecciones del módulo.

---

## 🎚️ Ubicación en el mapa

- **Módulo:** 1 — The Machine's Anatomy (Hardware y Arquitectura)
- **Nivel de esta lección:** Fundamento
- **Requiere haber visto:** Nada de Sistemas todavía, pero se conecta directo con Programación Módulo 1 (ahí escribiste la lógica; aquí ves dónde vive físicamente).

---

## 🔩 Núcleo (lo esencial, no se salta)

### 0. Hardware vs. Software: la distinción que lo explica todo

**Hardware:** todo lo físico, lo que puedes tocar. El metal, el plástico, los circuitos.

**Software:** las instrucciones (código) que le dicen al hardware qué hacer. No lo puedes tocar — es información, no materia.

```
Hardware sin software  → un ladrillo caro que no hace nada
Software sin hardware  → una idea que nunca se ejecuta
```

Todo lo que escribiste en Programación (variables, condicionales, bucles) es **software**. Esta lección y el resto del módulo son sobre el **hardware** que lo hace realidad.

**Analogía simple:** el hardware es como un instrumento musical; el software es la partitura. El instrumento sin partitura solo hace ruido si lo tocas al azar; la partitura sin instrumento es solo papel con símbolos. Necesitas ambos para que exista música.

---

### 1. Los 4 componentes esenciales (el mapa general)

Cualquier computadora — desde tu celular hasta el servidor más grande del mundo — tiene, en esencia, estas 4 piezas trabajando juntas:

```
┌─────────────────────────────────────────┐
│  CPU (Procesador)                        │
│  → "El cerebro": ejecuta instrucciones   │
└─────────────────────────────────────────┘
┌─────────────────────────────────────────┐
│  RAM (Memoria)                            │
│  → "La mesa de trabajo": guarda lo que    │
│    se está usando ahora mismo             │
└─────────────────────────────────────────┘
┌─────────────────────────────────────────┐
│  Almacenamiento (Disco/SSD)               │
│  → "El archivero": guarda todo de forma   │
│    permanente, aunque apagues la máquina  │
└─────────────────────────────────────────┘
┌─────────────────────────────────────────┐
│  Placa Madre (Motherboard)                │
│  → "El sistema nervioso": conecta todo lo │
│    anterior entre sí                      │
└─────────────────────────────────────────┘
```

Vas a profundizar en la CPU en la Lección 1.2, y en RAM/Almacenamiento en la 1.3. Por ahora, quédate con el mapa general y cómo se relacionan.

---

### 2. La analogía del escritorio (para entender CPU, RAM y Almacenamiento juntos)

Esta analogía te va a acompañar todo el módulo, así que apréndetela bien:

```
Almacenamiento (Disco/SSD)  →  El archivero de tu oficina
                                (guarda TODO, pero es lento de revisar)

RAM                          →  La mesa de trabajo
                                (solo lo que estás usando AHORA,
                                 rápido de alcanzar, pero se vacía
                                 si te levantas — es decir, si
                                 apagas la computadora)

CPU                           →  Tú, trabajando en la mesa
                                (el que realmente hace el trabajo,
                                 tomando cosas de la mesa, no del
                                 archivero directamente)
```

Cuando abres un programa, la computadora saca esa información del archivero (almacenamiento) y la pone en la mesa (RAM) para que tú (CPU) puedas trabajar con ella rápido. Por eso, si tienes muchos programas abiertos a la vez, la "mesa" se llena y todo se vuelve más lento — no porque el archivero esté lleno, sino porque la mesa de trabajo (RAM) ya no tiene espacio.

---

### 3. Otros componentes que vale la pena conocer (sin profundizar aún)

**GPU (Tarjeta gráfica):** un tipo especial de procesador optimizado para hacer muchísimos cálculos simples al mismo tiempo (en paralelo). Originalmente para gráficos/videojuegos, hoy también es clave en Inteligencia Artificial, porque entrenar modelos de IA requiere exactamente ese tipo de cálculo masivo en paralelo.

**Fuente de poder:** convierte la electricidad de tu casa/oficina a la energía que cada componente necesita. Suena aburrido, pero una fuente de poder insuficiente puede limitar qué tan potente puede ser el resto de tu hardware.

**Dispositivos de entrada/salida (I/O):** teclado, mouse, pantalla, micrófono — cualquier forma en que tú le das información a la computadora o ella te la regresa a ti.

---

### 4. Cómo se relacionan hardware, sistema operativo y tu código

```
[ Hardware físico ]
        ↓
[ Sistema Operativo ]   ← lo verás a fondo en Sistemas Módulo 2 (Linux)
        ↓
[ Tu programa en Python ]  ← lo que escribiste en Programación Módulo 1
```

El sistema operativo es la capa intermedia que traduce entre "lo que tu código pide" y "lo que el hardware físicamente puede hacer". Sin esa capa, cada programador tendría que escribir instrucciones específicas para cada modelo exacto de hardware — el sistema operativo evita ese caos. Profundizaremos en esto en el Módulo 2 de esta materia.

---

### 5. Recapitulación

```
Hardware (físico) vs. Software (instrucciones)
    ↓
4 componentes esenciales: CPU, RAM, Almacenamiento, Placa Madre
    ↓
Analogía del escritorio: Almacenamiento (archivero) → RAM (mesa) → CPU (tú trabajando)
    ↓
Componentes extra: GPU, fuente de poder, dispositivos I/O
    ↓
El Sistema Operativo conecta tu código con el hardware físico
```

Con este mapa general listo, en la Lección 1.2 nos metemos de lleno a la CPU — el componente que de verdad "ejecuta" cada línea de código que escribes.

---

## 🌌 Horizonte-Aplicado

_(esto no lo cubrimos aquí, pero lo vas a necesitar más adelante en ingeniería/sistemas)_

- **Cómputo en la nube (Cloud Computing)** — servicios como AWS, Google Cloud o Azure básicamente te "rentan" hardware físico (CPU, RAM, almacenamiento) que vive en servidores de alguien más; entender esta lección es la base para entender qué es lo que realmente estás pagando cuando usas la nube.
- **Virtualización** — la tecnología que permite que una sola computadora física "finja" ser varias computadoras separadas al mismo tiempo, cada una con su propio hardware virtual asignado; es la base de casi toda la infraestructura moderna de servidores.
- **Sistemas embebidos (embedded systems)** — computadoras diseñadas para una sola tarea específica, metidas dentro de otros dispositivos (un microondas, un coche, un cajero automático); tienen exactamente los mismos 4 componentes esenciales que viste aquí, solo que muchísimo más pequeños y limitados.

## 🏛️ Horizonte-Cultural

_(no lo vas a "usar" en un commit, pero te da contexto y entrena tu forma de pensar)_

- **La Ley de Moore** — la observación (no una ley física real) de que la cantidad de transistores en un chip se duplicaba aproximadamente cada dos años; explicó décadas de crecimiento exponencial en poder de cómputo, y hoy es tema de debate si sigue cumpliéndose o si ya llegó a su límite físico.
- **ENIAC y las primeras computadoras "gigantes"** — las primeras computadoras electrónicas (años 1940s) ocupaban cuartos completos, pesaban toneladas, y tenían muchísima menos capacidad que el celular más barato de hoy; vale la pena ver fotos de esto para dimensionar qué tan reciente y acelerado ha sido el avance del hardware.
- **Por qué le llamamos "arquitectura" al diseño de una computadora** — el término se popularizó con la "Arquitectura de von Neumann" en los años 1940s, que describe cómo se organizan CPU, memoria y almacenamiento en la mayoría de las computadoras modernas; investigar esto te conecta directo con por qué el mapa de componentes que viste aquí no es arbitrario, sigue un diseño con casi 80 años de historia.

---

## 🧠 Prompts para tu Tutor IA (NotebookLM)

**Modo Express** _(quiero repasar rápido el núcleo)_

> "Actúa como un profesor directo. Basándote únicamente en esta fuente, resume la diferencia entre hardware y software, los 4 componentes esenciales, y la analogía del escritorio, en un resumen rápido."

**Modo Expansión** _(quiero más de lo que dice la lección)_

> "Esta fuente es la base mínima. Explícame con más detalle qué hace cada componente extra mencionado (GPU, fuente de poder, dispositivos I/O), y dame ejemplos de dispositivos reales cotidianos que use cada uno de forma distinta a una computadora de escritorio."

**Modo Ingeniero** _(quiero conectar esto con mi trabajo como dev)_

> "De los temas listados en 'Horizonte-Aplicado' de esta fuente, explícame qué es la virtualización y el cómputo en la nube de forma introductoria, conectándolo con la analogía del escritorio (CPU/RAM/Almacenamiento) que vimos en el núcleo."

**Modo Curioso** _(quiero contexto e historia)_

> "Cuéntame sobre la Arquitectura de von Neumann mencionada en el Horizonte-Cultural de esta fuente, y explícame por qué casi todas las computadoras modernas, incluyendo mi celular, siguen ese mismo diseño básico."

**Modo Escéptico** _(quiero que me examinen)_

> "Actúa como un profesor escéptico y directo. Basándote únicamente en esta fuente, hazme 5 preguntas: clasificar ejemplos como hardware o software, explicar la analogía del escritorio con mis propias palabras, y identificar qué componente de los 4 esenciales cumple cada función descrita. Corrígeme con el porqué, no me des la respuesta antes de que yo intente."

---

## 🎯 Reto de la Comunidad

Antes de pasar a la Lección 1.2, responde esto en el canal de la materia:

1. Clasifica cada uno de estos como Hardware o Software: tu navegador de internet, la memoria RAM de tu laptop, un archivo de Python que escribiste, el teclado.
2. Con tus propias palabras (sin copiar la lección), explica por qué tener "poca RAM" hace que tu computadora se sienta lenta, aunque tu almacenamiento tenga mucho espacio libre.
3. Investiga qué componentes de hardware tiene TU dispositivo actual (laptop/celular/PC) — cuánta RAM, qué procesador, cuánto almacenamiento — y compártelo en el canal.

> **Regla de la comunidad:** No postees la respuesta directa de otros. Si alguien se equivoca, dale una pista, no la solución.

---

Siguiente lección → **1.2: El Cerebro — La CPU a Fondo**
