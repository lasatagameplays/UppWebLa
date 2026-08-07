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
3. **Configurar URLs:**
   * Edita el archivo `.github/workflows/uptime.yml` y añade las URLs de las webs que quieras monitorizar.
4. **Activar GitHub Pages:**
   * Ve a `Settings` > `Pages`.
   * En "Source", selecciona **Deploy from a branch**.
   * Elige la rama `main` y la carpeta `/ (root)`, luego pulsa guardar.

Una vez configurado, ve a la pestaña **Actions** y ejecuta el flujo de trabajo manualmente por primera vez. ¡A partir de ahí, funcionará solo!

## 🎨 Personalización de la Interfaz (White Label)

Puedes personalizar la apariencia superior del dashboard para adaptarlo a tu propia marca. Solo tienes que crear un archivo llamado `config.json` en la raíz de tu repositorio con este formato:

{
"companyName": "Mi Empresa",
"companyLogo": "https://midominio.com/logo.png",
"returnLinkTextES": "Volver a la web principal",
"returnLinkTextEN": "Return to main website",
"returnLinkUrl": "https://midominio.com"
}

> **Aviso importante sobre los logos:** Tus logos personales deben tener un nombre diferente a los originales. **No modifiques ni elimines los archivos que contengan la palabra `NoChange` en su nombre** (ej: `logoNoChange.png`), ya que forman parte de los derechos de autor obligatorios del proyecto.

## 📢 Gestión de Incidencias

El sistema organiza las incidencias en la carpeta incidents/ separadas por subcarpetas de servicios o dominios. Para publicar un reporte de incidencia:

### 1. Crear un reporte de incidencia
Crea un archivo JSON dentro de la subcarpeta correspondiente (ejemplo: incidents/LASATA.EU/2026-08-07-001.json):

{
  "id": "2026-08-07-001",
  "service": "Web Principal (LASATA)",
  "title": "Mantenimiento programado en la base de datos",
  "start_time": "2026-08-07T14:00:00Z",
  "end_time": null,
  "status": "active",
  "description": "Estamos realizando una optimización de índices en el servidor de base de datos. Se esperan interrupciones intermitentes.",
  "updates": [
    {
      "time": "2026-08-07T14:05:00Z",
      "text": "Inicio del mantenimiento. Tareas de respaldo completadas."
    }
  ]
}

### 2. Actualizar o marcar como Resuelta
* Para añadir comentarios en tiempo real a la cronología de la web, agrega elementos al array "updates".
* Para cerrar la incidencia, asigna la fecha y hora final en "end_time" (ej. "2026-08-07T15:30:00Z") y cambia el campo "status" a uno de los valores permitidos:
  * "active": Incidencia en curso.
  * "resolved": Resuelta.
  * "resolved_manual": Resuelta manualmente por el equipo técnico.
  * "resolved_auto": Resuelta automáticamente tras la recuperación del servicio.

Al subir los cambios, el motor indexará la incidencia y aparecerá al instante en el centro de control con su página de detalles completa.

## 🔄 Cómo actualizar tu clon de UppWebLa

Este proyecto está en constante evolución. Para actualizarlo de forma 100% segura:

1. Ve a la página principal de tu repositorio en GitHub.
2. Si hay actualizaciones, verás el mensaje *"This branch is X commits behind lasatagameplays/UppWebLa"*.
3. Haz clic en **"Sync fork"** y luego en **"Update branch"**. ¡Listo! Tu código se actualizará sin borrar tu historial de estado.

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
3. **Configure URLs:**
   * Edit `.github/workflows/uptime.yml` to target your own services.
4. **Enable GitHub Pages:**
   * Go to `Settings` > `Pages`.
   * Under "Source", choose **Deploy from a branch** (`main`, `/ root` folder), and save.

Go to the **Actions** tab and manually run the workflow for the first time. From then on, it will run automatically!

## 🎨 UI Customization (White Label)

You can customize the top appearance of the dashboard to fit your own brand. Just create a file named `config.json` in the root of your repository with this format:

{
"companyName": "My Company",
"companyLogo": "https://mydomain.com/logo.png",
"returnLinkTextES": "Volver a la web principal",
"returnLinkTextEN": "Return to main website",
"returnLinkUrl": "https://mydomain.com"
}

> **Important notice about logos:** Your personal logos must have a different name. **Do not modify or delete files containing the word `NoChange` in their name** (e.g., `logoNoChange.png`), as they are part of the project's mandatory copyright attribution.

## 📢 Incident Management

The system organizes incidents in the incidents/ folder, separated by service or domain subfolders. To publish an incident report:

### 1. Create an incident report
Create a JSON file inside the corresponding subfolder (example: incidents/LASATA.EU/2026-08-07-001.json):

{
  "id": "2026-08-07-001",
  "service": "Main Web (LASATA)",
  "title": "Scheduled database maintenance",
  "start_time": "2026-08-07T14:00:00Z",
  "end_time": null,
  "status": "active",
  "description": "We are performing index optimization on the database server. Intermittent interruptions are expected.",
  "updates": [
    {
      "time": "2026-08-07T14:05:00Z",
      "text": "Maintenance started. Backup tasks completed."
    }
  ]
}

### 2. Update or mark as Resolved
* To add real-time comments to the website's timeline, add elements to the "updates" array.
* To close the incident, assign the final date and time to "end_time" (e.g., "2026-08-07T15:30:00Z") and change the "status" field to one of the allowed values:
  * "active": Ongoing incident.
  * "resolved": Resolved.
  * "resolved_manual": Resolved manually by the technical team.
  * "resolved_auto": Resolved automatically after service recovery.

Once you push the changes, the engine will index the incident and it will instantly appear in the control center with its full details page.

## 🔄 How to update your UppWebLa clone

1. Go to your repository's main page.
2. Click **"Sync fork"** and then **"Update branch"** when updates are available. Your historical data will remain safe.

## 📄 License and Copyright

This project is open-source and freely available under the [MIT License](LICENSE).

Created, designed, and maintained with ❤️ by **[Rubén Castañeda Matute](https://github.com/lasatagameplays) (LASATA.EU)**. 

> **⚠️ COPYRIGHT LEGAL NOTICE:** While you are entirely free to customize the top header and project name in the UI via the `config.json` file, the MIT License of this open-source software **strictly prohibits the alteration, concealment, or removal of the original author credits (Copyright) and files marked as `NoChange` (such as the UppWebLa logo in the footer)**. Failure to comply with this attribution rule will result in the immediate takedown of your repository and website for copyright infringement (DMCA Takedown) by GitHub.