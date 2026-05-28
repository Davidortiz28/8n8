# Instalación de n8n y Primer "Hola Mundo"
**Actividad Práctica — Introducción al Backend**

---

| Campo | Detalle |
|-------|---------|
| **Estudiante** | David Fabián Ortiz Vega |
| **Materia** | Introducción al Backend |
| **Docente** | Kevin Jimenez |
| **Método de instalación** | npm local (instalación global) |

---

## Parte 1 — Instalación de n8n

### Requisitos Previos

- Node.js v24.14.1
- npm (incluido con Node.js)
- Terminal / PowerShell

### Versiones Instaladas

- **Node.js:** v24.14.1
- **n8n:** v2.22.4

### Proceso de Instalación

1. Abrir PowerShell y navegar a la carpeta de trabajo:
   ```bash
   cd C:\Users\david\OneDrive\Escritorio\n8n
   ```

2. Instalar n8n de forma global con npm:
   ```bash
   npm install n8n -g
   ```

3. Iniciar n8n:
   ```bash
   n8n start
   ```

4. Abrir el navegador y acceder a: `http://localhost:5678`

### Evidencia de Instalación

> 📸 *Captura de pantalla: instalación con npm*

![Instalación npm](capturas/instalacion.png)

> 📸 *Captura de pantalla: inicialización con n8n start*

![Inicialización n8n](capturas/inicializacion.png)

### Problemas Encontrados

Durante la instalación de n8n no se presentaron inconvenientes. Los únicos problemas surgieron más adelante, durante la configuración del bot de Discord para la integración con el workflow (obtención de IDs del servidor y canal, y configuración de permisos del bot).

---

## Parte 2 — Workflow "Hola Mundo"

### Descripción del Workflow

Se construyó un workflow compuesto por dos nodos que, al ejecutarse manualmente, envía un mensaje **"Hola Mundo"** al canal `#general` de un servidor de Discord a través de la API oficial de Discord usando un Bot Token.

### Nodos Utilizados

#### Nodo 1: Manual Trigger
- **Tipo:** Trigger Manual
- **Función:** Inicia el workflow al hacer clic en "Execute workflow"
- No requiere configuración adicional

#### Nodo 2: Discord (Custom API Call)
- **Tipo:** Discord node — operación Custom API Call
- **Connection Type:** Bot Token
- **Credential:** Discord Bot account (configurada con el Bot Token)
- **Resource:** Message — **Operation:** Send
- **Server ID** y **Channel ID** del servidor de Discord configurados
- **Mensaje enviado:** "Hola Mundo"

### Configuración del Bot de Discord

1. Crear una aplicación en el [Portal de Desarrolladores de Discord](https://discord.com/developers/applications)
2. Habilitar la sección **Bot** y generar el Bot Token
3. Activar los **Privileged Gateway Intents**: Message Content Intent y Server Members Intent
4. Invitar el bot al servidor con permisos de **Send Messages** mediante OAuth2 URL Generator
5. Configurar la credencial en n8n con el Bot Token
6. Obtener el **Server ID** y **Channel ID** activando el Modo Desarrollador en Discord

### Errores Encontrados y Soluciones

#### ❌ Error 1: `Invalid Form Body`
- **Causa:** La operación estaba configurada en "Get" en lugar de "Send"
- **Solución:** Cambiar la Operation a "Send" en la configuración del nodo Discord

#### ❌ Error 2: `Missing Access`
- **Causa:** El bot no tenía permisos para escribir en el canal del servidor
- **Solución:** Configurar correctamente los permisos del bot en el Portal de Desarrolladores y reinvitarlo al servidor con los permisos correctos

#### ❌ Error 3: Dificultad para obtener los IDs
- **Causa:** El Modo Desarrollador de Discord estaba desactivado
- **Solución:** Activar el Modo Desarrollador en Configuración → Avanzado de Discord

---

## Parte 3 — Evidencias de Funcionamiento

> 📸 *Captura de pantalla: workflow ejecutado exitosamente y mensaje en Discord*

![Workflow y Discord](n8n/Img/Idk.png")

El workflow consta de dos nodos conectados: el trigger manual y el nodo de Discord, evidenciando el flujo completo de automatización funcionando correctamente. Se puede observar el mensaje **"Hola Mundo"** enviado por el bot `n8n APP` en el canal `#general`, junto con el estado **"Workflow executed successfully"** en n8n.

 
---

## Parte 4 — Reflexión Técnica

**1. ¿Qué fue lo más difícil de la instalación?**

Lo más difícil no fue la instalación en sí, sino la configuración del bot de Discord para que pudiera enviar mensajes dentro del servidor. Fue necesario entender el sistema de permisos de Discord, cómo obtener los IDs del servidor y del canal, y resolver los errores de acceso que surgieron durante las pruebas.

**2. ¿Qué ventajas tiene n8n?**

n8n es una herramienta muy útil que permite automatizar tareas repetitivas sin necesidad de escribir código complejo. Su interfaz visual facilita la creación de flujos de trabajo, ahorra tiempo y permite integrar múltiples servicios y APIs de forma sencilla.

**3. ¿Qué diferencia encontraron entre Docker y local?**

La instalación local con npm depende directamente de la versión de Node.js instalada en el sistema, lo que puede generar conflictos si se actualiza Node.js o cambian las dependencias. Docker, en cambio, aísla la aplicación en su propio contenedor con sus propias dependencias, lo que la hace más estable y reproducible independientemente del entorno del sistema operativo.

**4. ¿Para qué casos reales usarían automatización?**

La automatización sería muy útil en proyectos que requieren atención constante, como el monitoreo de sistemas, el envío de notificaciones automáticas, la sincronización de datos entre plataformas, o el procesamiento periódico de información sin intervención manual.

**5. ¿Qué les gustaría automatizar en el futuro?**

Por el momento no hay una meta completamente definida, pero a medida que avancen los estudios de backend se espera identificar procesos concretos que puedan beneficiarse de la automatización, como pipelines de datos, notificaciones de eventos o integraciones entre servicios web.

---

*David Fabián Ortiz Vega — Introducción al Backend — 2026*# 8n8
