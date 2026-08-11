<div align="center">
  <img src="src/images/logoNoChange.png" alt="UppWebLa Logo" width="720" />
  <h1>💻 UppWebLa 3.1</h1>
  
  <p>
    <a href="https://github.com/lasatagameplays/UppWebLa/blob/main/LICENSE.ES.md"><img src="https://img.shields.io/badge/Licencia-Español-green?style=flat-square" alt="Licencia en Español" /></a>
    <a href="https://github.com/lasatagameplays/UppWebLa/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-MIT-1f6feb?style=flat-square" alt="License: MIT" /></a>
    <a href="https://github.com/lasatagameplays/UppWebLa/releases/latest"><img src="https://img.shields.io/github/v/release/lasatagameplays/UppWebLa?label=latest%20release&style=flat-square&color=58a6ff" alt="Latest Release" /></a>
    <a href="https://github.com/lasatagameplays/UppWebLa/actions/workflows/uppwebla.yml"><img src="https://img.shields.io/github/actions/workflow/status/lasatagameplays/UppWebLa/uppwebla.yml?label=build&style=flat-square&color=2ea043" alt="Build Status" /></a>
    <a href="https://github.com/lasatagameplays/UppWebLa/stargazers"><img src="https://img.shields.io/github/stars/lasatagameplays/UppWebLa?style=flat-square&color=d29922" alt="GitHub Stars" /></a>
    <img src="https://img.shields.io/github/repo-size/lasatagameplays/UppWebLa?label=repo%20size&style=flat-square&color=8b949e" alt="Repo Size" />
  </p>
  
  <p>
    <a href="#-español"><b>🇪🇸 Español</b></a> •
    <a href="#-english"><b>🇬🇧 English</b></a>
  </p>
</div>

---

# 🇪🇸 Español

<p><b>Monitor de estado web (Uptime) Open Source, Multirregión, con Gráficas de Latencia y 100% Serverless.</b></p>

> 🌐 **¿Quieres verlo en acción?** Visita la demo en vivo del software en [uppwebla.lasata.eu](https://uppwebla.lasata.eu/).

## 📋 Índice
1. [🚀 ¿Qué es UppWebLa?](#-qué-es-uppwebla)
2. [✨ Características Principales](#-características-principales)
3. [🌍 Monitorización Multirregión y Límites API](#-monitorización-multirregión-y-límites-api)
4. [🛠️ ¿Cómo funciona la arquitectura?](#️-cómo-funciona-la-arquitectura)
5. [🚀 Cómo usar UppWebLa en tu propio proyecto](#-cómo-usar-uppwebla-en-tu-propio-proyecto)
6. [⏱️ Forzar Pings Exactos (CronJob Externo)](#️-forzar-pings-exactos-cronjob-externo)
7. [🎨 Personalización de la Interfaz (White Label)](#-personalización-de-la-interfaz-white-label)
8. [📢 Gestión de Incidencias](#-gestión-de-incidencias)
9. [🤖 Auto-Incidencias (Automático)](#-auto-incidencias-automático)
10. [⚙️ Tareas Programadas y Reinicios (Cron)](#️-tareas-programadas-y-reinicios-cron)
11. [🔧 Mantenimientos Programados](#-mantenimientos-programados)
12. [🔄 Sistema de Actualizaciones y Copias de Seguridad](#-sistema-de-actualizaciones-y-copias-de-seguridad)
13. [📄 Licencia y Copyright](#-licencia-y-copyright)

## 🚀 ¿Qué es UppWebLa?

**UppWebLa** es un clon ultra ligero, moderno y estático de *Upptime*. Está diseñado para monitorizar el estado de tus páginas web y APIs de forma ininterrumpida utilizando la infraestructura gratuita de **GitHub Actions** y **GitHub Pages**.

A diferencia de otros sistemas, UppWebLa **no utiliza Node.js, npm, ni frameworks pesados**. Toda su arquitectura está construida con scripts puros de `Bash`, manipulación JSON con `jq`, gráficas interactivas con `Chart.js` y una interfaz de usuario desarrollada en `HTML`, `CSS` y `Vanilla JS`. Esto garantiza que el proyecto jamás quedará obsoleto por dependencias desactualizadas.

## ✨ Características Principales

* 🌍 **Monitorización Multirregión:** Realiza pings simultáneos desde los servidores de GitHub distribuidos globalmente (**América, Europa y Asia**) utilizando *Ubuntu*, *Windows* y *macOS*.
* ⚡ **Medición de Latencia y Disponibilidad:** Cada ping registra el tiempo de respuesta en milisegundos (`ms`). Calcula tu % de Uptime exacto analizando hasta 1 año de registros ininterrumpidos.
* 📊 **Gráficas de Alta Precisión:** Filtros interactivos de latencia a corto y largo plazo (1h, 6h, 12h, 24h, 7d...) con *tooltips* milimétricos que muestran la fecha y hora exacta en cada medición.
* 🤖 **Auto-Incidencias:** Si el sistema detecta una caída total en todas las regiones, el bot abrirá un reporte de forma automática y lo cerrará por sí solo cuando el servicio se recupere.
* ⏱️ **Auto-Recarga en Tiempo Real:** Dashboard inteligente con temporizador regresivo que consulta silenciosamente a GitHub y actualiza los gráficos sin recargar la página.
* 🎨 **Marca Blanca (White Label):** Permite a las empresas personalizar el diseño, logotipo, enlaces e idiomas modificando un simple archivo `config.json`.
* 📢 **Sistema de Incidencias Nativo:** Panel integrado y paginado para reportar caídas, mantenimientos o incidencias en curso con soporte de cronograma interactivo.
* 🌐 **Interfaz Multilenguaje 100% Dinámica:** Cambia de idioma al instante. Detecta el idioma del navegador y extrae automáticamente los textos en Español, Inglés (o cualquier otro que añadas).
* 💸 **100% Gratuito:** Sin costes de servidores, bases de datos o servicios de terceros. Todo se ejecuta y se aloja dentro de GitHub.
* 💾 **Almacenamiento Histórico Infinito (Downsampling):** Motor de compresión de datos y particionamiento en tiempo real que convierte registros masivos de pings en promedios mensuales ultra-ligeros. Permite configurar una retención visual de 1 a 200 años sin exceder los límites de tamaño de GitHub ni colapsar la memoria del navegador.

## 🌍 Monitorización Multirregión y Límites API
Este proyecto utiliza la potente y abierta infraestructura de [Globalping by jsDelivr](https://globalping.io/) para comprobar tus servicios reales desde servidores físicos en 3 continentes.

El software viene preconfigurado con una **Degradación Inteligente**:
- **Menos de 6 monitores (Modo Anónimo):** Funciona automáticamente "Out of the box". Sin registros ni configuraciones extra. Verás un ligero aviso amarillo recomendando poner una API Key, pero funcionará perfectamente.
- **6 o más monitores (Modo Bloqueo por Límite):** Si superas el límite de peticiones gratuitas anónimas, el programa detendrá la recolección para no generar errores falsos y mostrará una alerta roja en tu interfaz web.

**⚠️ Cómo desbloquear el modo Premium (Gratis):**
Si quieres monitorizar de 6 a infinitas páginas, [crea una cuenta gratuita en Globalping](https://globalping.io/), obtén un Token de API, y guárdalo en tu repositorio yendo a **Settings > Secrets and variables > Actions > New repository secret** bajo el nombre `GLOBALPING_API_KEY`. ¡El código lo detectará y se actualizará automáticamente sin tocar nada más!

## 🛠️ ¿Cómo funciona la arquitectura?

1. **El Motor de Pings:** Un disparador externo (`Webhook`) ejecuta el flujo de trabajo (`uppwebla.yml`) exactamente **cada 5 minutos** con prioridad máxima en los servidores de GitHub.
2. **Geo-Pings:** Los runners ejecutan peticiones avanzadas para medir códigos HTTP y tiempos de respuesta desde 3 continentes en base a los servicios definidos en `targets.json`.
3. **Historial Modular e Incidencias:** Un trabajo final unifica los datos, guarda el historial de cada servicio y empaqueta las carpetas de incidencias y mantenimientos de forma automática.
4. **Despliegue Automático:** Un bot hace un push silencioso y GitHub Pages sirve el dashboard estático al instante.

## 🚀 Cómo usar UppWebLa en tu propio proyecto

Eres libre de clonar este repositorio para monitorizar tus propias páginas web. Solo tienes que seguir estos pasos:

1. **Bifurcar (Fork):** Haz un Fork de este repositorio a tu propia cuenta de GitHub.
2. **Permisos del Bot:** Ve a Settings > Actions > General en tu nuevo repositorio. En "Workflow permissions", selecciona **Read and write permissions** y guarda.
3. **Configurar Servicios:** Edita el archivo `targets.json` en la raíz del repositorio para añadir las webs o APIs que quieras monitorizar (soporta nombres en Español e Inglés).
4. **Activar GitHub Pages:** Ve a Settings > Pages. En "Source", selecciona **Deploy from a branch**. Elige la rama `main` y la carpeta `/ (root)`, luego pulsa guardar.

Una vez configurado, ve a la pestaña Actions y ejecuta el flujo de trabajo manualmente por primera vez. ¡A partir de ahí, funcionará solo!

## ⏱️ Forzar Pings Exactos (CronJob Externo)

Como los servidores gratuitos de GitHub Actions ejecutan las tareas programadas internas con prioridad baja y provocan retrasos, UppWebLa delega su ejecución en un sistema cron externo para garantizar mediciones exactas cada 5 minutos.

Para configurar el webhook principal en tu repositorio:

1. Ve a GitHub y entra en **Settings > Developer settings > Personal access tokens > Tokens (classic)**.
2. Genera un nuevo token sin caducidad marcando **solamente la casilla `repo`**, y cópialo.
3. Crea una cuenta gratuita en [cron-job.org](https://cron-job.org/).
4. Crea un nuevo Cronjob con los siguientes datos:
   * **URL:** `https://api.github.com/repos/TU_USUARIO/TU_REPOSITORIO/dispatches`
   * **Ejecución (Schedule):** Cada 5 minutos.
5. En la pestaña **Avanzado** (Advanced):
   * **Método:** `POST`
   * Activa **Requiere autenticación HTTP** y pon tu **Usuario** de GitHub y tu **Token** como contraseña.
   * En **Headers**, añade:
     * `Accept` : `application/vnd.github.v3+json`
     * `Content-Type` : `application/json`
   * En el **Body**, elige formato raw y escribe: `{"event_type": "trigger-uptime"}`

¡Con esto tu panel se actualizará de forma profesional sin sufrir los retrasos de la cola de GitHub!

## 🎨 Personalización de la Interfaz (White Label)

Puedes personalizar la apariencia y los idiomas del dashboard editando el archivo `config.json`. En la sección `languages`, puedes añadir o quitar idiomas (se recomienda mantener al menos 2 para una mejor accesibilidad). Solo asegúrate de tener el diccionario `.json` correspondiente en la raíz (ej. `fr.json` si añades francés).

```json
{
  "companyName": "Mi Empresa",
  "companyLogo": "https://midominio.com/logo.png",
  "returnLinkTextES": "Volver a la web principal",
  "returnLinkTextEN": "Return to main website",
  "returnLinkUrl": "https://midominio.com",
  "globalTitleES": "Monitorización Global",
  "globalTitleEN": "Global Monitoring",
  "globalDescES": "Supervisión en tiempo real. Actualizado cada 5 minutos.",
  "globalDescEN": "Real-time supervision. Updated every 5 minutes.",
  "languages": [
    {"code": "es", "name": "Español", "flag": "es"},
    {"code": "en", "name": "English", "flag": "gb"}
  ]
}
```

> **Aviso importante sobre los logos:** Tus logos personales deben tener un nombre diferente a los originales. **No modifiques ni elimines los archivos que contengan la palabra `NoChange` en su nombre** (ej: `logoNoChange.png`), ya que forman parte de los derechos de autor obligatorios del proyecto.

## 📢 Gestión de Incidencias

El sistema organiza las incidencias en la carpeta `incidents/` separadas por subcarpetas de servicios. El sistema creará las subcarpetas automáticamente basado en los ID que configures en `targets.json`.

## 🤖 Auto-Incidencias (Automático)

**No necesitas crear reportes manualmente si el servidor se cae por completo.** El bot de UppWebLa detectará si las 3 regiones (US, EU, ASIA) fallan simultáneamente y generará un reporte automático (`status: active`). Cuando el servicio vuelva a estar online, el bot lo actualizará y cerrará automáticamente (`status: resolved_auto`).

### 1. Crear un reporte de incidencia (Manual)
Si quieres reportar un problema menor o dar explicaciones a tus usuarios, crea un archivo JSON dentro de la subcarpeta del ID (ejemplo: `incidents/web-principal/2026-08-07-001.json`):

```json
{
  "id": "2026-08-07-001",
  "service": "Web Principal (LASATA)",
  "title_es": "🔴 Problema de acceso detectado",
  "title_en": "🔴 Access issue detected",
  "start_time": "2026-08-07T14:00:00Z",
  "end_time": null,
  "status": "active",
  "description_es": "Algunos usuarios están experimentando lentitud al iniciar sesión.",
  "description_en": "Some users are experiencing slow login times.",
  "updates": [
    {
      "time": "2026-08-07T14:05:00Z",
      "text_es": "El equipo técnico está investigando el origen del problema.",
      "text_en": "The technical team is investigating the root cause."
    }
  ]
}
```

### 2. Actualizar o marcar como Resuelta
* Para añadir comentarios en tiempo real al timeline, agrega elementos al array "updates".
* Para cerrar la incidencia, asigna la fecha y hora final en "end_time" (ej. "2026-08-07T15:30:00Z") y cambia el campo "status" a uno de los valores permitidos:
  * "active": Incidencia en curso.
  * "resolved": Resuelta.
  * "resolved_manual": Resuelta manualmente por el equipo técnico.
  * "resolved_auto": Resuelta automáticamente tras la recuperación del servicio.

Al subir los cambios, el motor indexará la incidencia y aparecerá al instante en el centro de control con su página de detalles completa.

## ⚙️ Tareas Programadas y Reinicios (Cron)

Para evitar falsas alarmas durante reinicios semanales o copias de seguridad de tu servidor, puedes añadir tareas programadas (`scheduled_tasks`) en tu archivo `targets.json`. 
El sistema leerá la expresión cron y, si la tarea está en curso, suspenderá las alertas y marcará el estado como "Mantenimiento".

```json
{
  "id": "mi-servidor",
  "name": "Servidor Principal",
  "url": "https://midominio.com",
  "scheduled_tasks": [
    {
      "cron": "0 1 * * 0",
      "duration_minutes": 5,
      "timezone": "Europe/Madrid",
      "desc_es": "Reinicio semanal del sistema",
      "desc_en": "Weekly system reboot"
    }
  ]
}
```

* **cron:** La expresión matemática exacta **(ej: 30 3 * * *)**.
* **duration_minutes:** Tiempo estimado que el servidor estará inaccesible.
* **timezone:** (Opcional) Zona horaria del servidor. Por defecto es **Europe/Madrid**.

## 🔧 Mantenimientos Programados

El sistema organiza los mantenimientos programados en la carpeta `maintenances/` separadas por subcarpetas de servicios. El sistema creará las subcarpetas automáticamente basado en los ID que configures en `targets.json`.

### 1. Crear un reporte de mantenimiento
Para anunciar un mantenimiento, crea un archivo JSON dentro de la subcarpeta del ID correspondiente (ejemplo: `maintenances/web-principal/2026-08-15-maint.json`):

```json
{
  "id": "2026-08-15-maint",
  "service": "Web Principal (LASATA)",
  "title_es": "Actualización del sistema operativo",
  "title_en": "Operating system update",
  "start_time": "2026-08-15T02:00:00Z",
  "end_time": null,
  "status": "scheduled",
  "description_es": "Se realizará una actualización del sistema operativo del servidor. Se esperan breves cortes de conexión durante la madrugada.",
  "description_en": "An operating system update will be performed on the server. Brief connection outages are expected during the early morning hours.",
  "updates": [
    {
      "time": "2026-08-10T12:00:00Z",
      "text_es": "Mantenimiento programado y notificado con 5 días de antelación.",
      "text_en": "Maintenance scheduled and notified 5 days in advance."
    }
  ]
}
```

### 2. Actualizar o marcar como Completado
* Para añadir comentarios sobre el progreso, agrega elementos al array `"updates"`.
* Para finalizar el mantenimiento, asigna la fecha y hora en `"end_time"` y cambia el campo `"status"` a uno de los valores permitidos:
  * `"scheduled"`: Mantenimiento programado (aún no ha empezado).
  * `"in_progress"`: Mantenimiento en proceso.
  * `"completed"`: Mantenimiento completado y servicio restablecido.

## 🔄 Sistema de Actualizaciones y Copias de Seguridad

UppWebLa incluye un **detector automático de versiones**. Si publicamos una nueva actualización con mejoras, el pie de página de tu panel te avisará discretamente con un botón de actualización (ej: *¡Actualización v3.0 disponible!*). Este proyecto está en constante evolución, por lo que actualizar es muy sencillo.

### ¿Cómo actualizar de forma segura (Sin perder tus datos)?
Tus datos históricos (`history/`), reportes (`incidents/`, `maintenances/`) y tu configuración (`config.json` y `targets.json`) son sagrados. Para actualizar el código de la web sin romper tu base de datos, sigue estos pasos:

**Método Automático vía GitHub (Recomendado):**
1. **⚠️ Haz un Backup previo:** Descarga tu repositorio como archivo `.zip` por seguridad.
2. Ve a la página principal de tu repositorio (Fork) en GitHub.
3. Si hay actualizaciones, verás el mensaje *"This branch is X commits behind lasatagameplays/UppWebLa"*.
4. Haz clic en **"Sync fork"** y luego en **"Update branch"**. ¡Listo! GitHub fusionará el nuevo código del motor sin borrar tu historial de estado ni tus archivos personales.

**Método Manual:**
1. **⚠️ Haz un Backup previo:** Descarga tu repositorio como archivo `.zip`.
2. Descarga la nueva versión de UppWebLa y reemplaza **ÚNICAMENTE** estos archivos: `index.html`, `incident.html`, `maintenance.html`, `version.json` y el contenido de `src/`.
3. **⛔ NUNCA reemplaces (durante una actualización):** Tu carpeta `.github`, ni tus archivos `config.json` o `targets.json`, ya que ahí viven tu configuración y contraseñas. Además,**NUNCA** edites el archivo `version.json` ; este está vinculado al núcleo del código, y si lo alteras manualmente, el motor de actualizaciones (OTA) se romperá y dejarás de recibir avisos de mejoras.

### 💡 Plantillas de Ejemplo incluidas

Para facilitarte la tarea, este repositorio incluye **6 archivos JSON de ejemplo** (3 de incidencias y 3 de mantenimientos). Estos archivos abarcan todos los estados posibles (`active`, `resolved_manual`, `resolved_auto`, `scheduled`, `in_progress`, `completed`). 
Puedes encontrarlos en las carpetas `incidents/web-principal/` y `maintenances/web-principal/`. ¡Úsalos como plantilla copiando y pegando su estructura para tus propios reportes!

## 📄 Licencia y Copyright

Este proyecto es de código abierto y está disponible gratuitamente bajo los términos de la [Licencia MIT](LICENSE) ([📖 Ver traducción en Español](LICENSE.ES.md)).

Creado, diseñado y mantenido con ❤️ por **[Rubén Castañeda Matute](https://github.com/lasatagameplays) (LASATA.EU)**. 

> **⚠️ AVISO LEGAL DE COPYRIGHT:** Eres completamente libre de personalizar la cabecera superior y el nombre del proyecto en la interfaz mediante el archivo `config.json`. Sin embargo, la Licencia MIT de este software open-source **prohíbe estrictamente la alteración, ocultación o eliminación de los créditos de autor originales (Copyright) y de los archivos marcados como `NoChange` (como el logo de UppWebLa en el pie de página)**. El incumplimiento de esta norma de atribución resultará en la eliminación inmediata de tu repositorio y página web por violación de derechos de autor (DMCA Takedown) por parte de GitHub.

<br>

---

# 🇬🇧 English

<p><b>Open Source, Multi-Region, Latency-Charting, and 100% Serverless Web Status Monitor (Uptime).</b></p>

> 🌐 **Want to see it in action?** Check out the live demo at [uppwebla.lasata.eu](https://uppwebla.lasata.eu/).

## 📋 Table of Contents
1. [🚀 What is UppWebLa?](#-what-is-uppwebla)
2. [✨ Main Features](#-main-features)
3. [🌍 Multi-Region Monitoring and API Limits](#-multi-region-monitoring-and-api-limits)
4. [🛠️ How does the architecture work?](#️-how-does-the-architecture-work)
5. [🚀 How to use UppWebLa in your own project](#-how-to-use-uppwebla-in-your-own-project)
6. [⏱️ Force Exact Pings (External CronJob)](#️-force-exact-pings-external-cronjob)
7. [🎨 UI Customization (White Label)](#-ui-customization-white-label)
8. [📢 Incident Management](#-incident-management)
9. [🤖 Auto-Incidents (Automatic)](#-auto-incidents-automatic)
10. [⚙️ Scheduled Tasks & Reboots (Cron)](#️-scheduled-tasks--reboots-cron)
11. [🔧 Scheduled Maintenances](#-scheduled-maintenances)
12. [🔄 Updates and Backup System](#-updates-and-backup-system)
13. [📄 License and Copyright](#-license-and-copyright)

## 🚀 What is UppWebLa?

**UppWebLa** is an ultra-lightweight, modern, static clone of *Upptime*. It continuously monitors your websites and APIs using the free infrastructure of **GitHub Actions** and **GitHub Pages**.

Unlike other systems, UppWebLa **does not use Node.js, npm, or heavy frameworks**. Its architecture relies entirely on pure `Bash` scripts, JSON manipulation via `jq`, interactive charts using `Chart.js`, and a dynamic multilingual UI built with `HTML`, `CSS`, and `Vanilla JS`.

## ✨ Main Features

* 🌍 **Multi-Region Monitoring:** Simultaneous pings from globally distributed GitHub servers (**America, Europe, and Asia**) via *Ubuntu*, *Windows*, and *macOS*.
* ⚡ **Latency & Uptime Tracking:** Measures response time in milliseconds (`ms`). Accurately calculates Uptime % by analyzing up to 1 year of continuous records.
* 📊 **High-Precision Charts:** Interactive latency filters for short and long-term analysis (1h, 6h, 12h, 24h, 7d...) with exact tooltips displaying full date and minute-by-minute timestamps.
* 🤖 **Automatic Incidents:** If the system detects a total outage across all regions, the bot will automatically open an incident report and close it when the service recovers.
* ⏱️ **Real-Time Auto-Refresh:** Smart dashboard with a countdown timer that silently queries GitHub and updates charts without reloading the page.
* 🎨 **White Label Ready:** Allows companies to customize the layout, logo, links, and languages by simply editing a `config.json` file.
* 📢 **Native Incident Management:** Built-in paginated panel to report ongoing outages, maintenance, or incidents with an interactive timeline support.
* 🌐 **100% Dynamic Multilingual UI:** Switch languages instantly. Automatically extracts texts in Spanish, English (or any other you add).
* 💸 **100% Free:** Zero server or database costs. Fully hosted and executed within GitHub.
* 💾 **Infinite Historical Storage (Downsampling):** Real-time data compression and partitioning engine that converts massive ping records into ultra-lightweight monthly averages. It allows you to configure a visual retention span from 1 up to 200 years without exceeding GitHub's file size limits or crashing the browser's memory.

## 🌍 Multi-Region Monitoring and API Limits
This project uses the powerful and open infrastructure of [Globalping by jsDelivr](https://globalping.io/) to monitor your real-time services from physical servers on 3 continents.

The software comes pre-configured with **Intelligent Degradation**:
- **Fewer than 6 monitors (Anonymous Mode):** Works automatically "out of the box." No registration or extra configuration is required. You'll see a small yellow warning recommending you enter an API key, but it will work perfectly.

- **6 or more monitors (Limit Blocking Mode):** If you exceed the limit of free anonymous requests, the program will stop collecting data to avoid generating false errors and will display a red alert in your web interface.

**⚠️ How to unlock Premium mode (Free):**
If you want to monitor 6 to unlimited pages, create a free account on Globalping (https://globalping.io/), obtain an API token, and save it in your repository by going to Settings > Secrets and variables > Actions > New repository secret under the name `GLOBALPING_API_KEY`. The code will detect it and update automatically without any further changes!

## 🛠️ How does the architecture work?

1. **The Ping Engine:** An external trigger (`Webhook`) executes the workflow (`uppwebla.yml`) exactly **every 5 minutes** with top priority on GitHub servers.
2. **Geo-Pings:** GitHub runners execute advanced requests to measure HTTP status and response times based on the services defined in `targets.json`.
3. **Modular History & Incidents:** A final job collects data, saves independent history files, and automatically packages incident and maintenance folders.
4. **Automated Deployment:** A bot silently pushes the updates, and GitHub Pages serves the static dashboard instantly.

## 🚀 How to use UppWebLa in your own project

You are free to clone this repository to monitor your own websites. Just follow these steps:

1. **Fork:** Fork this repository to your GitHub account.
2. **Bot Permissions:** * Go to `Settings` > `Actions` > `General`.
   * Under "Workflow permissions", select **Read and write permissions**, and save.
3. **Configure Services:**
   * Edit `targets.json` file in the root of the repository to add the websites or APIs you want to monitor (Supports Spanish and English names).
4. **Enable GitHub Pages:**
   * Go to `Settings` > `Pages`.
   * Under "Source", choose **Deploy from a branch**. Select `main` and `/ root` folder, and save.

Go to the **Actions** tab and manually run the workflow for the first time. From then on, it will run automatically!

## ⏱️ Force Exact Pings (External CronJob)

Since free GitHub Actions servers execute internal scheduled tasks with low priority—causing delays—UppWebLa delegates their execution to an external cron system to ensure accurate measurements every 5 minutes.

To configure the main webhook in your repository:

1. Go to GitHub and open **Settings > Developer settings > Personal access tokens > Tokens (classic)**.
2. Generate a new token with no expiration, checking **only the `repo` box**, and copy it.
3. Create a free account at [cron-job.org](https://cron-job.org/).
4. Create a new Cronjob with the following data:
   * **URL:** `https://api.github.com/repos/TU_USUARIO/TU_REPOSITORIO/dispatches`
   * **Schedule:** Every 5 minutes.
5. In the **Advanced** tab:
   * **Method:** `POST`
   * Enable **Requires HTTP authentication** , enter your GitHub **Username** , and paste your **Token** as the password.
   * In **Headers**, add:
     * `Accept` : `application/vnd.github.v3+json`
     * `Content-Type` : `application/json`
   * In the **Body**, select raw format and write: `{"event_type": "trigger-uptime"}`

With this setup, your dashboard will update professionally without suffering from GitHub's queue delays! The UI includes a smart countdown timer that will automatically fetch and refresh data on the screen without reloading the page.


## 🎨 UI Customization (White Label)

You can customize the dashboard's appearance and languages by editing the `config.json` In the `languages` section, you can add or remove languages (We recommend keeping at least 2 for better accessibility). Just make sure you have the corresponding `.json` dictionary in the root folder (e.g., `fr.json` if you add French).

```json
{
  "companyName": "My Company",
  "companyLogo": "https://mydomain.com/logo.png",
  "returnLinkTextES": "Volver a la web principal",
  "returnLinkTextEN": "Return to main website",
  "returnLinkUrl": "https://midominio.com",
  "globalTitleES": "Monitorización Global",
  "globalTitleEN": "Global Monitoring",
  "globalDescES": "Supervisión en tiempo real. Actualizado cada 5 minutos.",
  "globalDescEN": "Real-time supervision. Updated every 5 minutes.",
  "languages": [
    {"code": "es", "name": "Español", "flag": "es"},
    {"code": "en", "name": "English", "flag": "gb"}
  ]
}
```

> **Important notice about logos:** Your personal logos must have a different name. **Do not modify or delete files containing the word `NoChange` in their name** (e.g., `logoNoChange.png`), as they are part of the project's mandatory copyright attribution.

## 📢 Incident Management

The system organizes incidents in the `incidents/` folder, separated by service subfolders. The system will automatically create the subfolders based on the IDs configured in `targets.json`.

## 🤖 Auto-Incidents (Automatic)

You don't need to manually create reports if the server goes down completely. The UppWebLa bot will detect if all 3 regions (US, EU, ASIA) fail simultaneously and automatically generate a report (`status: active`). When the service comes back online, the bot will auto-update and close it (`status: resolved_auto`).

### 1. Create an incident report (Manual)
If you want to report a minor issue or provide updates to your users, create a JSON file inside the corresponding ID subfolder (example: `incidents/web-principal/2026-08-07-001.json`):

```json
{
  "id": "2026-08-07-001",
  "service": "Main Web (LASATA)",
  "title_es": "🔴 Problema de acceso detectado",
  "title_en": "🔴 Access issue detected",
  "start_time": "2026-08-07T14:00:00Z",
  "end_time": null,
  "status": "active",
  "description_es": "Algunos usuarios están experimentando lentitud al iniciar sesión.",
  "description_en": "Some users are experiencing slow login times.",
  "updates": [
    {
      "time": "2026-08-07T14:05:00Z",
      "text_es": "El equipo técnico está investigando el origen del problema.",
      "text_en": "The technical team is investigating the root cause."
    }
  ]
}
```

### 2. Update or mark as Resolved
* To add real-time comments to the website's timeline, add elements to the "updates" array.
* To close the incident, assign the final date and time to "end_time" (e.g., "2026-08-07T15:30:00Z") and change the "status" field to one of the allowed values:
  * "active": Ongoing incident.
  * "resolved": Resolved.
  * "resolved_manual": Resolved manually by the technical team.
  * "resolved_auto": Resolved automatically after service recovery.

Once you push the changes, the engine will index the incident and it will instantly appear in the control center with its full details page.

## ⚙️ Scheduled Tasks & Reboots (Cron)

To prevent false alarms during weekly reboots or server backups, you can add scheduled tasks (`scheduled_tasks`) to your `targets.json` file.
The system will read the cron expression and, if the task is ongoing, it will suspend alerts and set the status to "Maintenance".

```json
{
  "id": "my-server",
  "name": "Main Server",
  "url": "https://mydomain.com",
  "scheduled_tasks": [
    {
      "cron": "0 1 * * 0",
      "duration_minutes": 5,
      "timezone": "Europe/Madrid",
      "desc_es": "Reinicio semanal del sistema",
      "desc_en": "Weekly system reboot"
    }
  ]
}
```

* **cron:** The exact mathematical expression **(e.g., 30 3 * * *)**.
* **duration_minutes:** Estimated time the server will be unreachable.
* **timezone:** (Optional) Server timezone. Defaults to **Europe/Madrid**.

## 🔧 Scheduled Maintenances

The system organizes scheduled maintenance in the `maintenances/` folder, separated by service subfolders. The system will automatically create the subfolders based on the IDs configured in `targets.json`.

### 1. Create a maintenance report
To announce a maintenance window, create a JSON file inside the corresponding ID subfolder (example: `maintenances/web-principal/2026-08-15-maint.json`):

```json
{
  "id": "2026-08-15-maint",
  "service": "Main Web (LASATA)",
  "title_es": "Actualización del sistema operativo",
  "title_en": "Operating system update",
  "start_time": "2026-08-15T02:00:00Z",
  "end_time": null,
  "status": "scheduled",
  "description_es": "Se realizará una actualización del sistema operativo del servidor. Se esperan breves cortes de conexión durante la madrugada.",
  "description_en": "An operating system update will be performed on the server. Brief connection outages are expected during the early morning hours.",
  "updates": [
    {
      "time": "2026-08-10T12:00:00Z",
      "text_es": "Mantenimiento programado y notificado con 5 días de antelación.",
      "text_en": "Maintenance scheduled and notified 5 days in advance."
    }
  ]
}
```

### 2. Update or mark as Completed
* To add progress comments, add elements to the `"updates"` array.
* To finish the maintenance, assign the date and time in `"end_time"` and change the `"status"` field to one of the allowed values:
  * `"scheduled"`: Maintenance is scheduled (has not started yet).
  * `"in_progress"`: Maintenance is in progress.
  * `"completed"`: Maintenance completed and service restored.

## 🔄 Updates and Backup System

UppWebLa features an **automatic version detector**. If we release a new update with enhancements, your dashboard's footer will discreetly notify you with an update badge (e.g., *Update v3.0 available!*). This project is constantly evolving, so updating is very straightforward.

### How to update safely (Without losing your data)?
Your historical data (`history/`), reports (`incidents/`, `maintenances/`), and configuration (`config.json` and `targets.json`) are sacred. To update the core code without breaking your database, follow these steps:

**Automatic Method via GitHub (Recommended):**
1. **⚠️ Pre-update Backup:** Download your repository as a `.zip` file for safety.
2. Go to your repository's main page (Fork) on GitHub.
3. If there are updates, you will see the message *"This branch is X commits behind lasatagameplays/UppWebLa"*.
4. Click the **"Sync fork"** button, then **"Update branch"**. Done! GitHub will merge the new engine code without deleting your status history or personal files.

**Manual Method:**
1. **⚠️ Pre-update Backup:** Download your repository as a `.zip` file.
2. Download the new UppWebLa version and replace **ONLY** these files: `index.html`, `incident.html`, `maintenance.html`, `version.json`, and the contents of `src/`.
3. **⛔ NEVER replace (during an update):** Your `.github` folder, `config.json`, or `targets.json` files, as they contain your personal layout and setup. Additionally,**NEVER** edit the `version.json` file; it is tied to the core code, and if you alter it manually, the Over-The-Air (OTA) update engine will break and you will stop receiving update notices.      

### 💡 Included Example Templates

To make things easier for you, this repository includes **6 example JSON files** (3 for incidents and 3 for maintenance). These files cover all possible states (`active`, `resolved_manual`, `resolved_auto`, `scheduled`, `in_progress`, `completed`). 
You can find them in the `incidents/web-principal/` and `maintenances/web-principal/` folders. Feel free to use them as templates by copying and pasting their structure for your own reports!

## 📄 License and Copyright

This project is open-source and freely available under the [MIT License](LICENSE) ([📖 Read Spanish translation](LICENSE.ES.md)).

Created, designed, and maintained with ❤️ by **[Rubén Castañeda Matute](https://github.com/lasatagameplays) (LASATA.EU)**. 

> **⚠️ COPYRIGHT LEGAL NOTICE:** While you are entirely free to customize the top header and project name in the UI via the `config.json` file, the MIT License of this open-source software **strictly prohibits the alteration, concealment, or removal of the original author credits (Copyright) and files marked as `NoChange` (such as the UppWebLa logo in the footer)**. Failure to comply with this attribution rule will result in the immediate takedown of your repository and website for copyright infringement (DMCA Takedown) by GitHub.