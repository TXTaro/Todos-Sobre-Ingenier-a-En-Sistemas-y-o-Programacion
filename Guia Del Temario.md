# 🧭 Guía Maestra: Cómo Usar NotebookLM (y otras IAs) en Este Temario

> **"No te vamos a dar el pescado masticado en cada lección. Te enseñamos a pescar una vez, aquí, y lo usas en las infinitas lecciones que vienen."**
>
> Este documento no es una lección de materia — es el **manual de operación** de tu Tutor IA. Léelo una sola vez, con calma, y de ahí en adelante cada lección del temario te va a rendir el triple, porque vas a saber exactamente qué botones tocar.

---

## 🎯 ¿Por qué existe esta guía?

Porque esto conecta directo con nuestro pilar de **"IA como apoyo, no reemplazo"**: la IA no está aquí para darte respuestas instantáneas, está para acelerar tu proceso de entender, cuestionar y practicar. Pero una IA sin instrucciones claras es solo un chatbot genérico — el valor real está en **cómo la usas**, no en que exista.

Con esta guía, cada quien arma su propio ritmo de estudio: quien quiera solo lo esencial usa el Modo Express, quien quiera hacer 50 ejercicios de práctica los genera él mismo, quien quiera irse por la tangente cultural lo hace sin que nadie tenga que escribirle esa lección aparte. Tú personalizas tu camino; nosotros no tenemos que pre-fabricar una versión distinta del temario para cada tipo de estudiante.

---

## 🐙 Parte 1: Accediendo al Temario desde GitHub

> Antes de meterte a NotebookLM necesitas de dónde sacar las lecciones. Esta parte es justo eso: cómo entrar al repositorio, cómo bajar lo que necesitas, y cómo enterarte cuando sale algo nuevo — sin morir en el intento aunque nunca hayas tocado GitHub en tu vida.

### ¿Qué es GitHub y por qué lo usamos?

GitHub es donde vive la versión oficial del temario. Es un lugar donde se guarda todo el contenido con **historial de versiones** — o sea, cada cambio que se hace queda registrado, y siempre puedes ver o regresar a una versión anterior si hace falta. Es la fuente de verdad: si alguna vez hay duda de "¿esta es la versión más reciente?", la respuesta está aquí, no en un PDF que alguien te pasó por Discord hace tres meses.

> Si GitHub se te complica de plano, el temario también está disponible en MediaFire (link en el Bienvenido) — pero ahí no vas a ver el historial de cambios ni sabrás tan rápido cuándo hay algo nuevo.

### Cómo entrar por primera vez

1. Entra al link del repositorio (lo encuentras en el documento de Bienvenido, sección "El Equipo de Desarrollo").
2. Vas a ver una lista de carpetas y archivos `.md` — esa es la estructura completa del temario, organizada igual que en Obsidian (por materia → módulo → lección).
3. Para leer una lección directo en el navegador, solo dale clic al archivo `.md` que quieras — GitHub lo muestra ya formateado, no como texto plano.

### Cómo bajar el temario completo (sin usar comandos)

No necesitas saber usar Git ni la terminal para esto:

1. En la página principal del repositorio, busca el botón verde que dice **"Code"**.
2. Dale clic → selecciona **"Download ZIP"**.
3. Descomprime el ZIP en tu computadora y abre esa carpeta directo en Obsidian como tu vault (o mételo dentro de tu vault actual).

Con eso ya tienes todo el temario completo en tu máquina, listo para ir subiendo lecciones a NotebookLM conforme avanzas (Parte 2).

### Cómo saber cuándo hay una actualización

Esto es lo que más te va a interesar para no quedarte atrás:

- **Revisa el Registro de Cambios:** dentro del repo hay una carpeta dedicada a esto — ahí Taro anota qué cambió, cuándo y por qué en cada versión. Es tu primera parada si quieres saber "¿qué es nuevo desde la última vez que descargué?"
- **Sección "Releases":** cuando el temario llega a una versión oficial (como la actual, Alpha 1.1.1.1), se publica como un "Release" — un snapshot congelado de esa versión específica. Ahí puedes bajar exactamente esa versión en vez de la más reciente en construcción.
- **Botón "Watch" (arriba a la derecha del repo):** si tienes cuenta de GitHub (es gratis y toma dos minutos crearla), dale clic a "Watch" → "All Activity" o "Custom" → "Releases". Así te llega notificación directo cada vez que sale una versión nueva, sin tener que estar checando manualmente.
- **No hace falta bajar el temario entero cada vez:** si solo salió una lección nueva, puedes ir directo a esa carpeta/archivo específico en el repo y descargar solo ese `.md` (botón de tres puntos o "Raw" → guardar página).

### Lo mínimo que necesitas saber, resumido

```
1. Repo = el temario completo con historial.
2. "Code" → "Download ZIP" = bajar todo sin comandos.
3. Registro de Cambios = qué cambió y por qué.
4. Releases = versiones oficiales congeladas (ej: Alpha 1.1.1.1).
5. "Watch" → "Releases" = que GitHub te avise solo, sin estar checando tú.
```

No necesitas volverte experto en Git para aprovechar esto — con saber entrar, bajar, y activar notificaciones de Releases ya estás cubierto para seguirle el paso al temario sin quedarte pasmado esperando que alguien te avise en Discord.

---

## 🛠️ Parte 2: Configurando tu NotebookLM

### ¿Qué es NotebookLM y por qué este y no otro chatbot?

NotebookLM es una IA de Google diseñada para trabajar **basándose únicamente en las fuentes que tú le subes** (tus documentos, PDFs, notas "Este temario :D"). A diferencia de un chat genérico, no está inventando desde su conocimiento general de internet — está leyendo exactamente lo que tú le diste. Esto es clave para este temario: significa que si tu subes la Lección 1.1 de Matemáticas, sus respuestas van a estar ancladas a lo que ahí se explicó, no a una versión random de internet que puede contradecir lo que aprendiste o usar un enfoque distinto al del temario.

**Ventaja:** cero desvíos, cero alucinaciones fuera de tema, una guia que tu mismo creaste.
**Limitante:** si no le subes suficiente material, tampoco puede "inventar" de más — para eso existen los prompts de "Modo Expansión" e IAs externas (Parte 6).

### Cómo organizar tus notebooks (cuadernos)

Recomendación de estructura, no regla obligatoria — ajusta a tu gusto:

```
📓 Un notebook por MATERIA (no por lección individual)
   Ej: "Matemáticas Aplicadas - Temario"
       "Inglés Técnico - Temario"

   Dentro de ese notebook, vas subiendo cada lección
   como una fuente nueva conforme avanzas.
```

¿Por qué por materia y no por módulo o por lección? Porque así, cuando le preguntes algo, NotebookLM puede conectar temas de distintas lecciones ya vistas (ej: relacionar exponentes de la lección 1.3 con funciones de la lección 1.4) sin que tengas que abrir cuadernos distintos. Si el notebook empieza a sentirse muy saturado (después de varios módulos), ahí sí puedes abrir uno nuevo por módulo (Parte 3).

### Cómo subir una lección como fuente

1. Descarga o exporta el archivo `.md` de la lección (desde tu Obsidian/repo del temario).
2. En NotebookLM, botón **"Add source"** → sube el archivo o pega el texto directo.
3. Repite cada vez que avances de lección. No hace falta subir el temario completo desde el día 1 — ve alimentando el cuaderno conforme avanzas sobre la marcha.

---

## 🧠 Parte 3: Los Modos de Estudio — a fondo

Cada lección trae prompts ya armados en 4 (o 5) modos. Aquí te explicamos **la lógica detrás de cada uno**, para que también puedas crear tus propias variaciones cuando quieras algo que no está pre-escrito.

| Modo          | Cuándo usarlo                                                                 | Qué le estás pidiendo a la IA                                                              |
| ------------- | ----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| **Express**   | Vas con prisa, o repasando antes de un reto/examen propio                     | Resumen directo del núcleo, sin rodeos, sin ejemplos de más                                |
| **Ingeniero** | Quieres conectar el tema con programación/hardware/tu carrera                 | Que tome el Horizonte-Aplicado y lo baje a un ejemplo técnico real                         |
| **Curioso**   | Te gusta el contexto, la historia, el "de dónde viene esto"                   | Que tome el Horizonte-Cultural y te lo cuente como anécdota, no como clase                 |
| **Escéptico** | Quieres comprobar que de verdad entendiste (no que memorizaste)               | Que te examine, te pida demostrar el porqué, y NO te dé la respuesta antes de que intentes |
| **Expansión** | El núcleo se sintió corto y quieres más profundidad o vocabulario/temas extra | Que use la lección como piso mínimo y construya más allá, sin salirse del nivel del módulo |

### Cómo armar tu propio prompt cuando ninguno de los 5 encaja

La fórmula base de cualquier buen prompt para este temario es:

```
1. Rol: "Actúa como [tipo de profesor/rol]..."
2. Restricción de fuente: "Basándote únicamente en esta fuente..."
3. Tarea específica: "Hazme / explícame / examíname en [algo concreto]..."
4. Regla de oro: "No me des la respuesta directa antes de que yo intente" (si es examen)
```

Ejemplo armado desde cero:

> *"Actúa como un ingeniero senior escéptico. Basándote únicamente en esta fuente, dame un caso real donde si no entiendo bien este tema, se me rompería un proyecto. No me expliques el tema primero — deja que yo intente explicártelo a ti, y corrígeme donde me equivoque."*

---

## 📝 Parte 4: Generando tus propios ejercicios (sin que nosotros los pre-hagamos):

**Plantilla de generador de ejercicios (cópiala y ajusta lo que está en `[corchetes]`):**

> *"Basándote únicamente en esta fuente, genérame [número] ejercicios de práctica sobre [tema específico de la lección]. Nivel de dificultad: [fácil / intermedio / me quiero morir >:c]. Mezcla estos tipos: opción múltiple, procedimiento paso a paso, y explicación con mis propias palabras. Dame primero SOLO los ejercicios, sin respuestas. Cuando te dé mis respuestas, corrígeme una por una con el porqué, no me des la respuesta correcta directo si me equivoco — dame una pista primero."*

**Variantes útiles:**

- *"Genérame un ejercicio que mezcle esta lección con la lección anterior, para ver si sé conectar ambos temas."*
- *"Dame un solo ejercicio, pero del tipo examen final: que me obligue a usar todo lo que vimos en este módulo, no solo esta lección."*
- *"Convierte este ejercicio en un problema con contexto real de programación/servidor/lo que sea, no un ejercicio de libro de texto."*

Ajustalo,  editalo y darle forma a tu forma de aprender y aplicar estos temas (estos solo fueron ejemplo y plantillas de una forma universal)

---

## 🎙️ Parte 5: Funciones extra de NotebookLM que vale la pena explotar

- **Audio Overview:** genera un podcast conversacional de dos "voces IA" discutiendo las fuentes. Útil para repasar en camión/gym/haciendo otra cosa(tiempos muetos y libres), no como método principal de estudio.
- **Mapas mentales / guías de estudio automáticas:** NotebookLM puede generarte un resumen visual de la estructura de una lección — bueno para repaso rápido antes de un reto.
- **Preguntas sugeridas:** cuando abres una fuente, NotebookLM sugiere preguntas iniciales — no las ignores, a veces detectan ángulos que ni tú ni nosotros pensamos.

---

## 🤝 Parte 6: IAs externas como complemento (no como reemplazo de NotebookLM)

NotebookLM es tu ancla porque no se sale del temario. Pero hay momentos donde SÍ quieres que una IA se salga del temario y traiga contexto de todo internet — para eso usas otras IAs (Claude, ChatGPT, Gemini, etc.), con la misma disciplina de siempre: **la IA acelera, tú piensas**.

**Úsalas para:**

- **Investigación más allá del Horizonte:** cuando un tema del Horizonte-Aplicado o Cultural te dejó picado y quieres ir más profundo de lo que cabe en una lección.
- **Revisar código real:** si ya estás practicando programación, una IA de propósito general con capacidad de ejecutar/explicar código es más útil que NotebookLM para esto.
- **Debate/contraste de fuentes:** pídele a una IA externa que **cuestione** lo que aprendiste en la lección (sin decirle qué fuente usar) y compara si su explicación coincide con la del temario. Si no coincide, tráelo al canal de dudas — puede ser un hueco en la lección que hay que arreglar, o algo que tú entendiste mal. Ambos casos son útiles.

**Regla importante:** si usas una IA externa para resolver un reto de la comunidad, dilo. No es trampa, pero sí rompe el espíritu de "aprender enseñando" si la usas para que TE RESUELVA en vez de ayudarte a entender.

**Registro/Guardado de memoria:** La mejor forma en la que no pierdas tu progreso en una conversación o proyecto en tu IA es el registro de memoria que la mayoría de las IAs tienen, solo mencionales  que guarden los datos de tu conversación y/o otra forma de preservar e incluso exportar  el tema de tu conversación de forma sencilla a otras IAs o usuarios es una resumen o registro de todo tu chat que has tenido, este principalmente se usa en las partes conflictivas que se te pueden presentar como el agotamiento de tokens que puedes tener con Claude o los errores que puede cometer Gemini con un chat largo con ella.

---

## 📔 Parte 7: Tu Bitácora Personal (Cuaderno de Registro)

Esto es distinto a "El Laboratorio" (The Sandbox), que es la zona comunitaria de experimentación avanzada. La **Bitácora** es tuya, personal, privada si quieres — el lugar donde guardas todo tu proceso, no el resultado final pulido.

### ¿Qué va aquí?

- **Registro de avance:** qué lección/módulo vas, cuándo lo terminaste.
- **Apuntes personales:** tu propia versión de la explicación de un tema (la mejor prueba de que entendiste algo es poder reescribirlo con tus palabras).
- **Dudas sin resolver:** cosas que te quedaron rondando, aunque no las hayas llevado al canal de la comunidad todavía.
- **Errores y su porqué:** cuando falles un reto de comunidad o un ejercicio generado, anota no solo que fallaste, sino *por qué* fallaste. Eso es oro para no repetir el mismo error.
- **Ideas sueltas:** cosas que se te ocurren a medias, conexiones entre materias que notaste tú solo (ej: "esto de exponentes se parece a lo que vi en Sistemas de binario").

### Plantilla sugerida (Obsidian/Notion, una nota por entrada)

```Bitacora
## [Fecha] — [Materia/Módulo/Lección]

**Qué vi hoy:**


**En mis palabras (sin ver la lección):**


**Dudas que me quedaron:**


**Errores y por qué me equivoqué:**


**Conexión con otro tema que noté:**

```

No hay forma incorrecta de llevar tu bitácora. Algunos la van a llenar todos los días, otros solo cuando algo les vuela la cabeza. Lo único que importa es que sea tuya y la uses de verdad, no que se vea bonita.

---

## ⚡ Cierre

Con esta guía ya no dependes de que nosotros te demos todo pre-hecho. Tienes las herramientas para: alimentar tu IA correctamente, elegir tu profundidad de estudio, generar tu propia práctica ilimitada, salir del temario cuando haga falta, y llevar registro de tu propio proceso.

Eso es exactamente lo que significa **Soberanía del Conocimiento** — no solo que el contenido sea gratis y abierto, sino que tú tengas el control real de cómo lo consumes.

---

_Documento de referencia — no pertenece a ningún módulo específico. Regresa aquí cuando quieras recordar cómo exprimir mejor tu Tutor IA._
