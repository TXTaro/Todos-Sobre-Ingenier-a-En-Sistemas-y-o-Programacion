# Sistemas — Módulo 2 — Lección 2.3: Procesos, Multitarea y Memoria Virtual

> **"En la 2.1 dijiste que el sistema operativo 'reparte tiempo de CPU entre programas'. Aquí ves exactamente cómo hace eso, y qué pasa cuando la RAM ya no alcanza."**
> 
> Cada vez que ejecutas un comando en la terminal (2.2), o corres un script de Python, el sistema operativo crea algo llamado **proceso**. Esta lección es sobre qué es un proceso, cómo el sistema decide a quién le toca usar la CPU, y el truco que usa cuando la RAM se queda corta.

---

## 🎚️ Ubicación en el mapa

- **Módulo:** 2 — Root Access (El Sistema Operativo por Dentro)
- **Nivel de esta lección:** Fundamento
- **Requiere haber visto:** Lección 2.1 (multitarea, mencionada de forma general) y Sistemas 1.3 (RAM vs. Almacenamiento) — aquí formalizamos ambas ideas juntas.

---

## 🔩 Núcleo (lo esencial, no se salta)

### 0. ¿Qué es un proceso?

Un **proceso** es un programa en ejecución — no el archivo guardado en el disco, sino la instancia activa de ese programa corriendo en este momento, con su propio espacio de memoria y su propio estado.

```python
# Esto es un archivo: script.py (vive en Almacenamiento, Sistemas 1.3)

# Cuando corres:
python script.py

# El sistema operativo crea un PROCESO: una copia activa de ese
# programa corriendo en RAM, con un identificador único (PID)
```

Si abres el mismo programa dos veces (por ejemplo, dos ventanas de tu navegador), el sistema operativo crea **dos procesos distintos**, cada uno con su propio espacio de memoria aislado, aunque ambos vengan del mismo archivo original.

```bash
ps       # lista los procesos activos en tu sistema
```

---

### 1. Estados de un proceso

Un proceso no está siempre "corriendo" activamente — pasa por distintos estados mientras el sistema operativo administra a quién le toca usar la CPU:

```
Nuevo        → el proceso se acaba de crear
Listo        → está esperando su turno para usar la CPU
Ejecutando   → está usando la CPU en este instante
Esperando    → está pausado, esperando algo (como una respuesta de red o un archivo)
Terminado    → ya acabó, el sistema libera sus recursos
```

```
Nuevo → Listo → Ejecutando → (Listo de nuevo, o Esperando, o Terminado)
                    ↑___________________|
                (el ciclo se repite constantemente)
```

Esto conecta directo con la multitarea de la 2.1: el sistema operativo mueve procesos constantemente entre "Listo" y "Ejecutando", dándole a cada uno una pequeña ventana de tiempo de CPU antes de pasar al siguiente.

---

### 2. El Planificador (Scheduler): quién decide el orden

La pieza del kernel encargada de decidir qué proceso pasa de "Listo" a "Ejecutando" en cada momento se llama **planificador (scheduler)**. No es una decisión al azar — usa algoritmos específicos que consideran cosas como:

```
Prioridad del proceso    → algunos procesos son más urgentes que otros
Cuánto tiempo ya esperó   → para evitar que un proceso espere indefinidamente
Tipo de tarea              → un proceso que necesita respuesta inmediata
                             (como mover el mouse) suele tener prioridad
                             sobre uno que corre en segundo plano
```

No necesitas memorizar algoritmos específicos de planificación aquí — lo importante es entender que **no es magia ni es al azar**: hay una lógica de decisión constante ocurriendo miles de veces por segundo, determinando qué proceso avanza y cuál espera.

---

### 3. Procesos en primer plano vs. segundo plano (background)

En la terminal (Lección 2.2), puedes controlar si un proceso "ocupa" tu terminal o corre sin bloquearla:

```bash
python servidor.py       # corre en primer plano: tu terminal queda "ocupada"
                          # hasta que el proceso termine

python servidor.py &      # el & al final lo manda a segundo plano:
                          # tu terminal queda libre para seguir usándola
```

Esto es exactamente cómo funcionan los servidores reales: un programa que corre indefinidamente en segundo plano, atendiendo peticiones, sin bloquear el resto del sistema — recuerda el ejemplo del `while True` gigante mencionado en Programación 1.4 como analogía de un servidor.

---

### 4. Memoria Virtual y Swap: la promesa de Sistemas 1.3

En la Lección 1.3 dijiste: _"cuando la RAM se llena por completo, algunos sistemas operativos usan una porción del Almacenamiento como 'RAM de emergencia'"_. Aquí está el mecanismo completo.

**El problema:** la RAM es rápida pero limitada (Sistemas 1.3). Si tienes muchos procesos corriendo a la vez, es posible que, entre todos, necesiten más RAM de la que existe físicamente en la máquina.

**La solución — Memoria Virtual:** el sistema operativo le hace creer a cada proceso que tiene acceso a un espacio de memoria enorme y exclusivo para él, aunque la RAM física sea mucho más pequeña y esté compartida entre todos los procesos. El sistema operativo administra por debajo, de forma invisible para cada programa, cuál dato realmente vive en la RAM física y cuál no en este momento.

**Swap: la pieza que hace esto posible cuando la RAM se agota:**

```
Situación normal:
RAM llena de datos activos → todo rápido (Sistemas 1.3)

RAM se queda sin espacio:
El sistema operativo toma datos de la RAM que no se han usado
recientemente, y los mueve temporalmente al Almacenamiento
(a una zona reservada llamada "swap" o "archivo de paginación")
para liberar espacio en la RAM para lo que sí se necesita ahora.

Si esos datos movidos se vuelven a necesitar:
El sistema operativo los trae de vuelta del Almacenamiento a la RAM
(esto es mucho más lento que si hubieran seguido en RAM,
recuerda la jerarquía de velocidad de Sistemas 1.3)
```

**Por qué tu computadora se vuelve extremadamente lenta cuando se queda sin RAM** (en vez de simplemente fallar): en lugar de negarse a abrir un programa nuevo, el sistema operativo empieza a usar swap constantemente, moviendo datos de un lado a otro entre RAM y Almacenamiento — y como el Almacenamiento es mucho más lento que la RAM, todo el sistema se siente pesado, aunque técnicamente sigue funcionando.

```
Jerarquía de Sistemas 1.3, aplicada aquí:
Registros → Caché → RAM → [swap usa Almacenamiento aquí] → resto del Almacenamiento
```

---

### 5. Conectando con Memory Leaks (promesa de Sistemas 1.3)

Recuerda el Horizonte-Aplicado de la 1.3: un _memory leak_ es cuando un programa sigue reservando RAM sin liberarla cuando ya no la necesita. Ahora que entiendes procesos y swap, la consecuencia completa queda clara:

```
Un proceso con memory leak sigue pidiendo más y más RAM
    ↓
Eventualmente, la RAM física se agota
    ↓
El sistema operativo empieza a usar swap agresivamente para compensar
    ↓
Todo el sistema se vuelve lento — no solo el proceso con el problema,
sino potencialmente todos los demás procesos también
```

Esto es exactamente por qué un servidor con un memory leak sin detectar puede degradar su rendimiento gradualmente durante horas o días, hasta volverse inutilizable — no falla de golpe, se va poniendo cada vez más lento conforme el sistema depende más y más de swap.

---

### 6. Recapitulación

```
Proceso = instancia activa de un programa corriendo, con su propio espacio de memoria
    ↓
Estados: Nuevo → Listo → Ejecutando → Esperando/Terminado
    ↓
Planificador (Scheduler) = decide qué proceso usa la CPU y cuándo
    ↓
Primer plano vs. segundo plano (&) en la terminal
    ↓
Memoria Virtual + Swap = usar Almacenamiento como "RAM de emergencia" cuando se agota
    ↓
Memory leaks + falta de RAM = por qué un sistema se degrada lentamente, no falla de golpe
```

Con esto ya entiendes cómo el sistema operativo administra múltiples programas compitiendo por los mismos recursos limitados de CPU y memoria. En la última lección del módulo vas a ver que "Linux" no es una sola cosa — es toda una familia de sistemas construidos sobre las mismas ideas que acabas de aprender.

---

## 🌌 Horizonte-Aplicado

_(esto no lo cubrimos aquí, pero lo vas a necesitar más adelante en sistemas/DevOps)_

- **Monitoreo de procesos en producción** — herramientas como `top`, `htop`, o dashboards de monitoreo de servidores muestran en tiempo real exactamente los conceptos que viste aquí (uso de CPU por proceso, uso de RAM, procesos en espera); vas a usar esto constantemente al administrar cualquier servidor real.
- **Deadlocks (interbloqueos)** — una situación donde dos o más procesos quedan esperando indefinidamente uno al otro sin poder avanzar nunca; es uno de los problemas clásicos y más complicados de la programación concurrente, que ya se asomó como tema en Sistemas 1.2.
- **Contenedores y límites de recursos** — tecnologías como Docker (ya mencionada en la 2.1) permiten limitar exactamente cuánta CPU y RAM puede usar un proceso específico, evitando que un solo programa problemático consuma todos los recursos de la máquina.

## 🏛️ Horizonte-Cultural

_(no lo vas a "usar" en un commit, pero te da contexto y entrena tu forma de pensar)_

- **El origen del término "swap"** — viene literalmente de la idea de "intercambiar" (swap) contenido entre dos ubicaciones de memoria; en las primeras computadoras con memoria extremadamente limitada, esta técnica no era una opción de respaldo, era prácticamente obligatoria para correr cualquier programa de tamaño considerable.
- **El caso del gusano Morris (1988)** — uno de los primeros programas maliciosos autopropagados de internet explotó, entre otras cosas, la forma en que los sistemas UNIX de la época administraban procesos; es un ejemplo temprano de por qué entender procesos y memoria a fondo también es una cuestión de seguridad, no solo de rendimiento.
- **Por qué "Blue Screen of Death" y "Kernel Panic" existen** — cuando algo falla catastróficamente en el espacio de kernel (Sistemas 2.1), el sistema completo no puede simplemente "cerrar ese proceso" como haría con un error en espacio de usuario — tiene que detener todo, porque ya no puede confiar en que el hardware esté en un estado seguro; de ahí vienen estas pantallas de error tan temidas.

---

## 🧠 Prompts para tu Tutor IA (NotebookLM)

**Modo Express** _(quiero repasar rápido el núcleo)_

> "Actúa como un profesor directo. Basándote únicamente en esta fuente, resume qué es un proceso, sus estados, qué hace el planificador, y cómo funciona la memoria virtual con swap, con una analogía de cada uno."

**Modo Ingeniero** _(quiero conectar esto con sistemas real)_

> "De los temas listados en 'Horizonte-Aplicado' de esta fuente, explícame qué es un deadlock con un ejemplo simple de dos procesos esperándose mutuamente, y por qué es un problema difícil de resolver en general."

**Modo Curioso** _(quiero contexto e historia)_

> "Cuéntame sobre el gusano Morris de 1988 mencionado en el Horizonte-Cultural de esta fuente, y explícame por qué entender procesos y memoria también es relevante para la seguridad informática."

**Modo Escéptico** _(quiero que me examinen)_

> "Actúa como un profesor escéptico y directo. Basándote únicamente en esta fuente, hazme 5 preguntas: explicar los estados de un proceso con mis propias palabras, por qué el sistema usa swap en vez de simplemente rechazar abrir más programas, y qué relación tiene un memory leak con el rendimiento general del sistema con el tiempo. Corrígeme con el porqué, no me des la respuesta antes de que yo intente."

**Modo Expansión** _(quiero más de lo que dice la lección)_

> "Usando esta fuente como piso mínimo, explícame qué son los threads (hilos) dentro de un proceso, y en qué se diferencian de tener varios procesos separados."

---

## 🎯 Reto de la Comunidad

Antes de pasar a la Lección 2.4, responde esto en el canal de la materia:

1. Con tus propias palabras, explica la diferencia entre un proceso en estado "Listo" y uno en estado "Esperando" — da un ejemplo concreto de cada uno.
2. Investiga y comparte en el canal: ¿cuánta RAM y cuánto swap tiene configurado tu dispositivo actual? (En Linux/Mac puedes investigar el comando `free -h`; en Windows, revisa el Administrador de Tareas).
3. Explica con tus propias palabras por qué una computadora con un memory leak activo se pone "cada vez más lenta" en vez de fallar inmediatamente, conectándolo con swap y la jerarquía de memoria de Sistemas 1.3.

> **Regla de la comunidad:** No postees la respuesta directa de otros. Si alguien se equivoca, dale una pista, no la solución.

---

Siguiente lección → **2.4: El Ecosistema Linux — Distros y Alternativas**
