# Módulo 2: "Root Access" (El Sistema Operativo por Dentro)

> **"En el Módulo 1 conociste el hardware — el cuerpo de la máquina. Aquí conoces el sistema nervioso que lo hace usable: el sistema operativo."**
>
> Bienvenid@ al Módulo 2 de Sistemas. Ya sabes qué es una CPU, cómo funciona la memoria, y cómo tu código termina siendo ejecutado físicamente. Ahora vas a ver la capa de software que administra todo eso, le habla directamente al hardware, y decide cómo se reparten los recursos entre todos los programas que corren al mismo tiempo — cerrando, de paso, la pregunta que quedó abierta desde la Lección 1.1: ¿qué es exactamente el sistema operativo?

## 🎯 Objetivos del Módulo

Al terminar este módulo, serás capaz de:

- **Entender la arquitectura interna de un sistema operativo:** qué es el kernel, la diferencia entre espacio de kernel y espacio de usuario, y cómo funciona la multitarea.
- **Moverte con soltura en la terminal:** navegar el sistema de archivos, manipular archivos y carpetas, y entender permisos usando exactamente el sistema octal que ya dominas desde Matemáticas.
- **Comprender cómo se administran procesos y memoria en tiempo real:** qué es un proceso, cómo decide el sistema operativo a quién le toca la CPU, y qué es la memoria virtual (swap) cuando la RAM no alcanza.
- **Conocer el panorama real de sistemas operativos tipo Unix:** por qué existen tantas distribuciones de Linux, cuál elegir según tu necesidad, y cómo BSD encaja en esta familia — Soberanía Técnica aplicada directamente.

## 🗺️ Mapa de Ruta (Lo que encontrarás aquí)

Para abrir la capa de software que hace usable al hardware, avanzaremos a través de estas lecciones clave:

### 📄 Lección 2.1: ¿Qué es un Sistema Operativo? (La Capa que Todo Conecta)

Cerramos la promesa dejada desde la 1.1. Kernel, espacio de kernel vs. espacio de usuario, y cómo un solo procesador logra la ilusión de correr decenas de programas a la vez.

### 📄 Lección 2.2: La Terminal (Tu Primer Contacto Real)

Navegación de archivos, comandos básicos, y permisos representados en octal — el círculo que se cierra directo con Matemáticas 2.1, donde `chmod` se mencionó por primera vez como ejemplo real de esa base numérica.

### 📄 Lección 2.3: Procesos, Multitarea y Memoria Virtual

Qué es un proceso, cómo decide el planificador quién usa la CPU, y el mecanismo completo de swap — cerrando la promesa dejada en Sistemas 1.3 sobre memoria virtual.

### 📄 Lección 2.4: El Ecosistema Linux (Distros y Alternativas a Windows)

El cierre maestro del módulo. Por qué "Linux" no es una sola cosa, panorama de Mint, Debian, Fedora y Arch según su enfoque, BSD como familia aparte, y el criterio real para elegir sistema operativo en vez de simplemente usar lo preinstalado.

## 🛠️ Práctica con NotebookLM (Tutor IA)

> 💡 **Tip de Estudio:** Este temario está diseñado para que **tú tengas el control de la profundidad**. Sube las lecciones de este módulo a tu cuaderno de "Sistemas" en NotebookLM (el mismo cuaderno del Módulo 1).
>
> Al final de cada lección encontrarás los prompts maestros. Úsalos según lo que necesites hoy:
>
> - ¿Vas con prisa? Usa el **Modo Express**.
> - ¿Quieres conectarlo con sistemas/DevOps real? Usa el **Modo Ingeniero**.
> - ¿Quieres historia y contexto de por qué las cosas son como son? Usa el **Modo Curioso**.
> - ¿Quieres demostrar que de verdad entendiste? Usa el **Modo Escéptico**.
> - ¿Sientes que el tema te quedó corto? Activa el **Modo Expansión**.

⚡ **Ya conoces el cuerpo de la máquina. Ahora conoce el software que le da vida y la hace tuya de verdad. Abre el archivo de la Lección 2.1 y sigamos.**
