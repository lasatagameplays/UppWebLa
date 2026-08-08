<div align="center">
  <img src="src/images/logoNoChange.png" alt="UppWebLa Logo" width="720" />
  <h1>💻 UppWebLa</h1>
  
  <p>
    <a href="#-español"><b>🇪🇸 Español</b></a> •
    <a href="#-english"><b>🇬🇧 English</b></a>
  </p>
</div>

---

# 🇪🇸 Español

<p><b>Monitor de estado web (Uptime) Open Source, Multirregión, con Gráficas de Latencia y 100% Serverless.</b></p>

## 🚀 ¿Qué es UppWebLa?

**UppWebLa** es un clon ultra ligero, moderno y estático de *Upptime*. Está diseñado para monitorizar el estado de tus páginas web y APIs de forma ininterrumpida utilizando la infraestructura gratuita de **GitHub Actions** y **GitHub Pages**.

A diferencia de otros sistemas, UppWebLa **no utiliza Node.js, npm, ni frameworks pesados**. Toda su arquitectura está construida con scripts puros de `Bash`, manipulación JSON con `jq`, gráficas interactivas con `Chart.js` y una interfaz de usuario desarrollada en `HTML`, `CSS` y `Vanilla JS`. Esto garantiza que el proyecto jamás quedará obsoleto por dependencias desactualizadas.

## ✨ Características Principales

* 🌍 **Monitorización Multirregión:** Realiza pings simultáneos desde los servidores de GitHub distribuidos globalmente (**América, Europa y Asia**) utilizando *Ubuntu*, *Windows* y *macOS*.
* ⚡ **Medición de Latencia y Disponibilidad:** Cada ping registra el tiempo de respuesta en milisegundos (`ms`). Calcula tu % de Uptime exacto analizando hasta 1 año de registros ininterrumpidos.
* 🎨 **Marca Blanca (White Label):** Permite a las empresas personalizar la barra superior con su propio logotipo, nombre y enlaces modificando un simple archivo `config.json`.
* 📢 **Sistema de Incidencias Nativo:** Panel integrado para reportar mantenimientos o incidencias en curso (`incidents.json`) con soporte de estados (*Activo / Resuelto*).
* 🌐 **Interfaz Multilenguaje Dinámica:** Detecta automáticamente el idioma del navegador y carga los diccionarios (Ej: `es.json`, `en.json`).
* 💸 **100% Gratuito:** Sin costes de servidores, bases de datos o servicios de terceros. Todo se ejecuta y se aloja dentro de GitHub.

## 🛠️ ¿Cómo funciona la arquitectura?

1. **El Cron Job:** Un flujo de trabajo (`uptime.yml`) se ejecuta cada 5 minutos mediante GitHub Actions.
2. **Geo-Pings:** Los *runners* ejecutan peticiones `curl` avanzadas para medir códigos HTTP y tiempos de respuesta desde 3 continentes.
3. **Historial Modular:** Un trabajo final unifica los datos y guarda el historial de cada servicio de manera independiente en la carpeta `/history`.
4. **Despliegue Automático:** Un bot hace un `git push` silencioso y GitHub Pages sirve el dashboard estático al instante.

## 🚀 Cómo usar UppWebLa en tu propio proyecto

Eres libre de clonar este repositorio para monitorizar tus propias páginas web. Solo tienes que seguir estos pasos:

1. **Bifurcar (Fork):** Haz un *Fork* de este repositorio a tu propia cuenta de GitHub.
2. **Permisos del Bot:** * Ve a `Settings` > `Actions` > `General` en tu nuevo repositorio.
   * En "Workflow permissions", selecciona **Read and write permissions** y guarda.
3. **Configurar Servicios:**
   * Edita el archivo `targets.json` en la raíz del repositorio para añadir las webs o APIs que quieras monitorizar (Soporta nombres en Español e Inglés).
4. **Activar GitHub Pages:**
   * Ve a `Settings` > `Pages`.
   * En "Source", selecciona **Deploy from a branch**.
   * Elige la rama `main` y la carpeta `/ (root)`, luego pulsa guardar.

Una vez configurado, ve a la pestaña **Actions** y ejecuta el flujo de trabajo manualmente por primera vez. ¡A partir de ahí, funcionará solo!

## 🎨 Personalización de la Interfaz (White Label)

Puedes personalizar la apariencia superior del dashboard para adaptarlo a tu propia marca. Solo tienes que crear un archivo llamado `config.json` en la raíz de tu repositorio con este formato:

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

Puedes personalizar la apariencia y los idiomas del dashboard editando el archivo `config.json`. En la sección `languages`, puedes añadir o quitar idiomas (se recomienda mantener al menos 2 para una mejor accesibilidad). Solo asegúrate de tener el archivo `.json` correspondiente en la raíz (ej. `fr.json` si añades francés).

> **Aviso importante sobre los logos:** Tus logos personales deben tener un nombre diferente a los originales. **No modifiques ni elimines los archivos que contengan la palabra `NoChange` en su nombre** (ej: `logoNoChange.png`), ya que forman parte de los derechos de autor obligatorios del proyecto.

## 📢 Gestión de Incidencias

El sistema organiza las incidencias en la carpeta incidents/ separadas por subcarpetas de servicios o dominios. Para publicar un reporte de incidencia:

### 1. Crear un reporte de incidencia
Crea un archivo JSON dentro de la subcarpeta correspondiente (ejemplo: incidents/LASATA.EU/2026-08-07-001.json):

```json
{
  "id": "2026-08-07-001",
  "service": "Web Principal (LASATA)",
  "title_es": "Mantenimiento programado en la base de datos",
  "title_en": "Scheduled database maintenance",
  "start_time": "2026-08-07T14:00:00Z",
  "end_time": null,
  "status": "active",
  "description_es": "Estamos realizando una optimización de índices en el servidor de base de datos. Se esperan interrupciones intermitentes.",
  "description_en": "We are performing index optimization on the database server. Intermittent interruptions are expected.",
  "updates": [
    {
      "time": "2026-08-07T14:05:00Z",
      "text_es": "Inicio del mantenimiento. Tareas de respaldo completadas.",
      "text_en": "Maintenance started. Backup tasks completed."
    }
  ]
}
```

### 2. Actualizar o marcar como Resuelta
* Para añadir comentarios en tiempo real a la cronología de la web, agrega elementos al array "updates".
* Para cerrar la incidencia, asigna la fecha y hora final en "end_time" (ej. "2026-08-07T15:30:00Z") y cambia el campo "status" a uno de los valores permitidos:
  * "active": Incidencia en curso.
  * "resolved": Resuelta.
  * "resolved_manual": Resuelta manualmente por el equipo técnico.
  * "resolved_auto": Resuelta automáticamente tras la recuperación del servicio.

Al subir los cambios, el motor indexará la incidencia y aparecerá al instante en el centro de control con su página de detalles completa.

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

## 🔄 Cómo actualizar tu clon de UppWebLa

Este proyecto está en constante evolución. Para actualizarlo de forma 100% segura:

1. Ve a la página principal de tu repositorio en GitHub.
2. Si hay actualizaciones, verás el mensaje *"This branch is X commits behind lasatagameplays/UppWebLa"*.
3. Haz clic en **"Sync fork"** y luego en **"Update branch"**. ¡Listo! Tu código se actualizará sin borrar tu historial de estado.

### 💡 Plantillas de Ejemplo incluidas

Para facilitarte la tarea, este repositorio incluye **6 archivos JSON de ejemplo** (3 de incidencias y 3 de mantenimientos). Estos archivos abarcan todos los estados posibles (`active`, `resolved_manual`, `resolved_auto`, `scheduled`, `in_progress`, `completed`). 
Puedes encontrarlos en las carpetas `incidents/web-principal/` y `maintenances/web-principal/`. ¡Úsalos como plantilla copiando y pegando su estructura para tus propios reportes!

## 📄 Licencia y Copyright

Este proyecto es de código abierto y está disponible gratuitamente bajo los términos de la [Licencia MIT](LICENSE).

Creado, diseñado y mantenido con ❤️ por **[Rubén Castañeda Matute](https://github.com/lasatagameplays) (LASATA.EU)**. 

> **⚠️ AVISO LEGAL DE COPYRIGHT:** Eres completamente libre de personalizar la cabecera superior y el nombre del proyecto en la interfaz mediante el archivo `config.json`. Sin embargo, la Licencia MIT de este software open-source **prohíbe estrictamente la alteración, ocultación o eliminación de los créditos de autor originales (Copyright) y de los archivos marcados como `NoChange` (como el logo de UppWebLa en el pie de página)**. El incumplimiento de esta norma de atribución resultará en la eliminación inmediata de tu repositorio y página web por violación de derechos de autor (DMCA Takedown) por parte de GitHub.

<br>

---

# 🇬🇧 English

<p><b>Open Source, Multi-Region, Latency-Charting, and 100% Serverless Web Status Monitor (Uptime).</b></p>

## 🚀 What is UppWebLa?

**UppWebLa** is an ultra-lightweight, modern, static clone of *Upptime*. It continuously monitors your websites and APIs using the free infrastructure of **GitHub Actions** and **GitHub Pages**.

Unlike other systems, UppWebLa **does not use Node.js, npm, or heavy frameworks**. Its architecture relies entirely on pure `Bash` scripts, JSON manipulation via `jq`, interactive charts using `Chart.js`, and a clean frontend built with `HTML`, `CSS`, and `Vanilla JS`.

## ✨ Main Features

* 🌍 **Multi-Region Monitoring:** Simultaneous pings from globally distributed GitHub servers (**America, Europe, and Asia**) via *Ubuntu*, *Windows*, and *macOS*.
* ⚡ **Latency & Uptime Tracking:** Measures response time in milliseconds (`ms`). Accurately calculates Uptime % by analyzing up to 1 year of continuous records.
* 🎨 **White Label Ready:** Allows companies to customize the top navbar with their own logo, name, and links by simply editing a `config.json` file.
* 📢 **Native Incident Management:** Built-in panel to report ongoing maintenance or incidents (`incidents.json`) with *Active / Resolved* states.
* 🌐 **Dynamic Multilingual UI:** Automatically detects browser language and fetches dictionaries (`es.json`, `en.json`).
* 💸 **100% Free:** Zero server or database costs. Fully hosted and executed within GitHub.

## 🛠️ How does the architecture work?

1. **The Cron Job:** A workflow (`uptime.yml`) runs every 5 minutes via GitHub Actions.
2. **Geo-Pings:** GitHub runners execute advanced `curl` commands to measure HTTP status and response times from 3 continents.
3. **Modular History:** A final job collects data and saves independent history files for each service in the `/history` folder.
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
   * Under "Source", choose **Deploy from a branch** (`main`, `/ root` folder), and save.

Go to the **Actions** tab and manually run the workflow for the first time. From then on, it will run automatically!

## 🎨 UI Customization (White Label)

You can customize the top appearance of the dashboard to fit your own brand. Just create a file named `config.json` in the root of your repository with this format:

```json
{
  "companyName": "My Company",
  "companyLogo": "https://mydomain.com/logo.png",
  "returnLinkTextES": "Volver a la web principal",
  "returnLinkTextEN": "Return to main website",
  "returnLinkUrl": "https://mydomain.com",
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

You can customize the dashboard's appearance and languages by editing the `config.json` file. In the `languages` section, you can add or remove languages (we recommend keeping at least 2 for better accessibility). Just make sure you have the corresponding `.json` dictionary in the root folder (e.g., `fr.json` if you add French).

> **Important notice about logos:** Your personal logos must have a different name. **Do not modify or delete files containing the word `NoChange` in their name** (e.g., `logoNoChange.png`), as they are part of the project's mandatory copyright attribution.

## 📢 Incident Management

The system organizes incidents in the incidents/ folder, separated by service or domain subfolders. To publish an incident report:

### 1. Create an incident report
Create a JSON file inside the corresponding subfolder (example: incidents/LASATA.EU/2026-08-07-001.json):

```json
{
  "id": "2026-08-07-001",
  "service": "Main Web (LASATA)",
  "title_es": "Mantenimiento programado en la base de datos",
  "title_en": "Scheduled database maintenance",
  "start_time": "2026-08-07T14:00:00Z",
  "end_time": null,
  "status": "active",
  "description_es": "Estamos realizando una optimización de índices en el servidor de base de datos. Se esperan interrupciones intermitentes.",
  "description_en": "We are performing index optimization on the database server. Intermittent interruptions are expected.",
  "updates": [
    {
      "time": "2026-08-07T14:05:00Z",
      "text_es": "Inicio del mantenimiento. Tareas de respaldo completadas.",
      "text_en": "Maintenance started. Backup tasks completed."
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

## 🔄 How to update your UppWebLa clone

1. Go to your repository's main page.
2. Click **"Sync fork"** and then **"Update branch"** when updates are available. Your historical data will remain safe.

### 💡 Included Example Templates

To make things easier for you, this repository includes **6 example JSON files** (3 for incidents and 3 for maintenance). These files cover all possible states (`active`, `resolved_manual`, `resolved_auto`, `scheduled`, `in_progress`, `completed`). 
You can find them in the `incidents/web-principal/` and `maintenances/web-principal/` folders. Feel free to use them as templates by copying and pasting their structure for your own reports!

## 📄 License and Copyright

This project is open-source and freely available under the [MIT License](LICENSE).

Created, designed, and maintained with ❤️ by **[Rubén Castañeda Matute](https://github.com/lasatagameplays) (LASATA.EU)**. 

> **⚠️ COPYRIGHT LEGAL NOTICE:** While you are entirely free to customize the top header and project name in the UI via the `config.json` file, the MIT License of this open-source software **strictly prohibits the alteration, concealment, or removal of the original author credits (Copyright) and files marked as `NoChange` (such as the UppWebLa logo in the footer)**. Failure to comply with this attribution rule will result in the immediate takedown of your repository and website for copyright infringement (DMCA Takedown) by GitHub.