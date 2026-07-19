# Sistemas — Módulo 2 — Lección 2.2: La Terminal (Tu Primer Contacto Real)

> **"Todo lo que has visto hasta ahora en este módulo era teoría. Aquí le hablas al sistema operativo directamente, sin íconos, sin ventanas, solo texto y comandos."**
> 
> La terminal (o consola) da miedo la primera vez — se ve como algo de película de hackers. En realidad es solo otra forma de comunicarte con el sistema operativo, más directa y más poderosa que hacer clic en íconos.

---

## 🎚️ Ubicación en el mapa

- **Módulo:** 2 — Root Access (El Sistema Operativo por Dentro)
- **Nivel de esta lección:** Fundamento
- **Requiere haber visto:** Lección 2.1 (sistema de archivos, mencionado brevemente) y Matemáticas 2.1 (sistemas numéricos, en especial octal) — lo vas a necesitar directo para entender permisos en esta lección.

---

## 🔩 Núcleo (lo esencial, no se salta)

### 0. ¿Qué es la terminal, realmente?

La **terminal** (también llamada consola o shell) es una interfaz basada en texto para darle instrucciones al sistema operativo. En vez de hacer doble clic en un ícono, escribes un comando de texto y presionas Enter.

```
Interfaz gráfica (GUI):     haces clic en el ícono de una carpeta
Terminal (CLI):              escribes: cd Documentos
```

**Por qué usarías esto en vez de la interfaz gráfica:** es más rápido para tareas repetitivas, permite automatizar procesos completos (recuerda los bucles de Programación 1.4 — puedes automatizar comandos igual), y es prácticamente la única forma de administrar un servidor remoto, que casi nunca tiene interfaz gráfica.

---

### 1. El sistema de archivos, ahora navegado de verdad

Recuerda la estructura que viste en la 2.1:

```
/
├── home/
│   └── usuario/
```

**Comandos básicos de navegación (sistemas tipo Unix/Linux, que verás con más profundidad en la 2.4):**

```bash
pwd     # "print working directory" → muestra en qué carpeta estás ahora
ls      # "list" → lista los archivos y carpetas de donde estás
cd      # "change directory" → te mueve a otra carpeta

cd Documentos       # entra a la carpeta Documentos
cd ..                # sube un nivel (a la carpeta padre)
cd /                 # te lleva directo a la raíz de todo
cd ~                 # te lleva directo a tu carpeta de usuario (home)
```

**Rutas absolutas vs. relativas:**

```bash
# Ruta absoluta: empieza desde la raíz /, siempre funciona sin importar dónde estés
cd /home/usuario/documentos

# Ruta relativa: depende de dónde estás parado ahora mismo
cd documentos
```

---

### 2. Manipulando archivos y carpetas desde la terminal

```bash
mkdir proyectos       # "make directory" → crea una carpeta nueva
touch archivo.txt     # crea un archivo vacío nuevo
cp archivo.txt copia.txt    # "copy" → copia un archivo
mv archivo.txt carpeta/     # "move" → mueve (o renombra) un archivo
rm archivo.txt         # "remove" → elimina un archivo

rm -r carpeta/          # elimina una carpeta y todo su contenido
                         # (el -r significa "recursivo" — ojo, no hay papelera de reciclaje aquí)
```

**Advertencia real, no exagerada:** `rm` en la terminal no manda nada a una papelera de reciclaje — el archivo se borra directamente. Este es exactamente el tipo de comando donde el modal `must` de Inglés 2.4 aplicaría perfecto: _"You must double-check the path before running `rm -r`."_

---

### 3. Permisos: cerrando el círculo con Matemáticas 2.1

Cada archivo y carpeta en un sistema tipo Unix/Linux tiene **permisos** que determinan quién puede leerlo, escribirlo, o ejecutarlo.

```bash
ls -l archivo.txt

-rw-r--r--  1 usuario  grupo  1024  Jul 18 10:00 archivo.txt
```

Esos primeros 10 caracteres (`-rw-r--r--`) son los permisos. Se dividen en 3 grupos de 3:

```
-  rw-  r--  r--
   ↑    ↑    ↑
 dueño grupo otros
```

Cada grupo de 3 letras representa: **r**ead (leer), **w**rite (escribir), e**x**ecute (ejecutar). Un guion (`-`) significa que ese permiso NO está activo.

**Aquí es donde Matemáticas 2.1 regresa directo:** estos permisos se representan también como un número, usando exactamente el sistema octal (base 8) que ya conoces.

```
r (leer)     = 4
w (escribir) = 2
x (ejecutar) = 1
```

Se suman los valores que aplican para cada grupo:

```
rwx = 4+2+1 = 7    (todos los permisos)
rw- = 4+2+0 = 6    (leer y escribir, no ejecutar)
r-- = 4+0+0 = 4    (solo leer)
```

```bash
chmod 755 script.sh
```

Se lee: dueño = 7 (rwx, todo), grupo = 5 (r-x, leer y ejecutar), otros = 5 (r-x, leer y ejecutar). Esto **no es una coincidencia de diseño ni una convención rara** — es aritmética octal aplicada directamente, exactamente como la viste en Matemáticas 2.1 cuando mencionamos `chmod` como ejemplo de dónde usarías octal en la vida real.

```bash
chmod 644 documento.txt   # dueño: rw-, grupo: r--, otros: r--
chmod 700 privado.txt      # dueño: rwx, grupo: ---, otros: ---   (nadie más puede ni ver esto)
```

---

### 4. Variables de entorno: información que vive fuera de tu programa

El sistema operativo mantiene un conjunto de **variables de entorno** — información disponible para cualquier programa que corra en la terminal, sin que tú la tengas que definir cada vez.

```bash
echo $HOME     # muestra tu carpeta de usuario (ej: /home/usuario)
echo $PATH     # muestra en qué carpetas el sistema busca comandos ejecutables
```

**Por qué te importa esto:** cuando escribes `python` en la terminal y simplemente funciona, es porque el sistema operativo revisó las carpetas listadas en la variable `PATH` hasta encontrar dónde está instalado Python. Si alguna vez ves el error `command not found`, casi siempre significa que ese programa no está en ninguna carpeta listada en `PATH`.

---

### 5. Encadenando comandos: la terminal como mini-lenguaje de programación

La terminal no solo ejecuta un comando a la vez — puedes combinarlos, parecido a cómo combinaste funciones en Programación 2.1:

```bash
comando1 && comando2    # ejecuta comando2 SOLO SI comando1 tuvo éxito (recuerda AND de Matemáticas 2.2)
comando1 || comando2    # ejecuta comando2 SOLO SI comando1 falló (recuerda OR de Matemáticas 2.2)
comando1 | comando2     # "pipe": el resultado de comando1 se convierte en el input de comando2
```

```bash
mkdir proyecto && cd proyecto    # crea la carpeta, y SOLO si funcionó, entra a ella
```

Esto no es una coincidencia de que se parezca al álgebra booleana que ya viste — es exactamente la misma lógica de `AND`/`OR` aplicada al éxito o fracaso de comandos en vez de valores `True`/`False` abstractos.

---

### 6. Recapitulación

```
Terminal = interfaz de texto para hablarle al sistema operativo directamente
    ↓
Navegación: pwd, ls, cd (rutas absolutas vs. relativas)
    ↓
Manipulación de archivos: mkdir, touch, cp, mv, rm (sin papelera de reciclaje)
    ↓
Permisos: rwx por dueño/grupo/otros → representados en octal (Matemáticas 2.1)
    ↓
Variables de entorno: PATH, HOME
    ↓
Encadenar comandos: && / || / | → misma lógica de AND/OR de Matemáticas 2.2
```

Con esto ya puedes moverte y operar dentro de un sistema tipo Unix/Linux sin depender de una interfaz gráfica. En la Lección 2.3 vas a ver qué pasa realmente cuando ejecutas cualquiera de estos comandos: cómo el sistema operativo administra cada uno como un proceso independiente.

---

## 🌌 Horizonte-Aplicado

_(esto no lo cubrimos aquí, pero lo vas a necesitar más adelante en sistemas/DevOps)_

- **Scripts de shell (bash)** — puedes guardar una secuencia de comandos de terminal en un archivo y ejecutarlos todos juntos, automatizando tareas completas; es esencialmente aplicar la lógica de Programación (secuencia, selección, iteración) directamente a comandos de terminal.
- **SSH (Secure Shell)** — el protocolo que te permite abrir una terminal de una computadora remota (como un servidor en la nube) desde tu propia máquina, como si estuvieras sentado frente a ella; es la herramienta central de cualquier trabajo con servidores.
- **Permisos especiales: sudo y el usuario root** — un usuario con privilegios totales (llamado `root`) puede saltarse restricciones normales de permisos; el comando `sudo` ("superuser do") te permite ejecutar un comando específico con esos privilegios elevados, algo que verás constantemente al instalar software en Linux.

## 🏛️ Horizonte-Cultural

_(no lo vas a "usar" en un commit, pero te da contexto y entrena tu forma de pensar)_

- **Por qué la terminal "parece" del pasado, pero sigue siendo dominante** — aunque las interfaces gráficas existen desde los años 80, la terminal sigue siendo la herramienta preferida de administradores de sistemas y desarrolladores profesionales décadas después; no es nostalgia, es que para muchas tareas (automatización, servidores remotos, precisión) sigue siendo objetivamente más eficiente que hacer clic.
- **El "filósofo Unix": herramientas pequeñas que hacen una sola cosa bien** — cada comando que viste aquí (`ls`, `cp`, `rm`) sigue una filosofía de diseño deliberada de los creadores originales de UNIX: programas pequeños, simples, que se combinan entre sí (como viste con `|` y `&&`) en vez de programas gigantes que intentan hacer todo.
- **La cultura del "no hay Ctrl+Z" en la terminal** — a diferencia de casi cualquier aplicación gráfica moderna, muchos comandos de terminal (como `rm`) no tienen una función de deshacer incorporada; esta característica ha generado toda una cultura de historias (y memes) de desarrolladores sobre errores costosos, y es parte de por qué la disciplina y precisión importan tanto en este ambiente.

---

## 🧠 Prompts para tu Tutor IA (NotebookLM)

**Modo Express** _(quiero repasar rápido el núcleo)_

> "Actúa como un profesor directo. Basándote únicamente en esta fuente, resume los comandos básicos de navegación y manipulación de archivos, cómo funcionan los permisos en octal, y cómo encadenar comandos, con un ejemplo de cada uno."

**Modo Ingeniero** _(quiero conectar esto con sistemas real)_

> "De los temas listados en 'Horizonte-Aplicado' de esta fuente, explícame qué es SSH y por qué es la herramienta central para trabajar con servidores remotos, conectándolo con lo que aprendí sobre la terminal en el núcleo."

**Modo Curioso** _(quiero contexto e historia)_

> "Explícame, basándote en el Horizonte-Cultural de esta fuente, la filosofía Unix de 'herramientas pequeñas que hacen una sola cosa bien', y por qué sigue siendo relevante en el diseño de software moderno."

**Modo Escéptico** _(quiero que me examinen)_

> "Actúa como un profesor escéptico y directo. Basándote únicamente en esta fuente, hazme 5 preguntas: pídeme convertir permisos rwx a su valor octal y viceversa, predecir qué hace una secuencia de comandos encadenados con && y ||, y explicar la diferencia entre ruta absoluta y relativa con un ejemplo. Corrígeme con el porqué, no me des la respuesta antes de que yo intente."

**Modo Expansión** _(quiero más de lo que dice la lección)_

> "Usando esta fuente como piso mínimo, explícame qué es sudo y el usuario root, con un ejemplo real de cuándo lo necesitarías al instalar software en un sistema Linux."

---

## 🎯 Reto de la Comunidad

Antes de pasar a la Lección 2.3, responde esto en el canal de la materia:

1. Convierte estos permisos a su valor octal: `rwxr-xr--` y `rw-rw-r--`. Muestra la suma para cada grupo (dueño, grupo, otros).
2. Escribe la secuencia de comandos para: crear una carpeta llamada `proyecto`, entrar a ella, y crear un archivo vacío llamado `main.py`, todo encadenado con `&&`.
3. Explica con tus propias palabras por qué `rm -r carpeta/` es un comando peligroso comparado con arrastrar una carpeta a la papelera de reciclaje en una interfaz gráfica.

> **Regla de la comunidad:** No postees la respuesta directa de otros. Si alguien se equivoca, dale una pista, no la solución.

---

Siguiente lección → **2.3: Procesos, Multitarea y Memoria Virtual**
