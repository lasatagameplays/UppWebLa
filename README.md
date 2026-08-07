<div align="center">
  <img src="src/images/logo.png" alt="UppWebLa Logo" width="720" />
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
* ⚡ **Medición de Latencia y Gráficas:** Cada ping registra el tiempo de respuesta exacto en milisegundos (`ms`). Al hacer clic en cualquier región, se abre una ventana modal con una gráfica de rendimiento interactiva.
* 📢 **Sistema de Incidencias Nativo:** Panel integrado para reportar mantenimientos o incidencias en curso (`incidents.json`) con soporte de estados (*Activo / Resuelto*).
* 🌐 **Interfaz Multilenguaje Dinámica:** Detecta automáticamente el idioma del navegador y carga los diccionarios desde archivos JSON independientes (`lang/es.json`, `lang/en.json`, etc.), permitiendo añadir nuevos idiomas fácilmente.
* 🛡️ **Anti-Caché Integrado:** Sistema inteligente en el frontend que rompe la caché de GitHub Pages para mostrar siempre el estado real en el segundo exacto.
* 💸 **100% Gratuito:** Sin costes de servidores, bases de datos o servicios de terceros. Todo se ejecuta y se aloja dentro de GitHub.

## 🛠️ ¿Cómo funciona la arquitectura?

1. **El Cron Job:** Un flujo de trabajo (`uptime.yml`) se ejecuta cada 5 minutos mediante GitHub Actions.
2. **Pings Geográficos y Latencia:** Los *runners* ejecutan peticiones `curl` avanzadas para medir códigos HTTP y milisegundos de respuesta desde 3 continentes.
3. **Historial Incremental:** Un trabajo final recolecta los datos, actualiza las gráficas de rendimiento y guarda el archivo `data.json`.
4. **Despliegue Automático:** Un bot hace un `git push` silencioso al repositorio. GitHub Pages sirve el dashboard estático en `status.lasata.eu`.

## 🚀 Cómo usar UppWebLa en tu propio proyecto

Eres libre de clonar este repositorio para monitorizar tus propias páginas web. Solo tienes que seguir estos pasos:

1. **Bifurcar (Fork):** Haz un *Fork* de este repositorio a tu propia cuenta de GitHub.
2. **Permisos del Bot:** * Ve a `Settings` > `Actions` > `General` en tu nuevo repositorio.
   * En "Workflow permissions", selecciona **Read and write permissions** y guarda.
3. **Configurar URLs:**
   * Edita el archivo `.github/workflows/uptime.yml` y añade o modifica las URLs de tus servicios.
4. **Activar GitHub Pages:**
   * Ve a `Settings` > `Pages`.
   * En "Source", selecciona **Deploy from a branch** (rama `main`, carpeta `/`).

## 🔄 Cómo actualizar tu clon de UppWebLa

1. Ve a la página principal de tu repositorio en GitHub.
2. Si hay actualizaciones, verás el mensaje *"This branch is X commits behind lasatagameplays/UppWebLa"*.
3. Haz clic en **"Sync fork"** y luego en **"Update branch"**. ¡Listo!

## 📄 Licencia y Copyright

Este proyecto es de código abierto y está disponible gratuitamente bajo los términos de la [Licencia MIT](LICENSE).

Creado, diseñado y mantenido con ❤️ por **[Rubén Castañeda Matute](https://github.com/lasatagameplays) (LASATA.EU)**. 

> **Nota para desarrolladores:** Eres libre de clonar y utilizar este sistema de monitorización. El único requisito legal es que **debes mantener el aviso de copyright original** y los créditos al autor en tu repositorio.

<br>

---

# 🇬🇧 English

<p><b>Open Source, Multi-Region, Latency-Charting, and 100% Serverless Web Status Monitor (Uptime).</b></p>

## 🚀 What is UppWebLa?

**UppWebLa** is an ultra-lightweight, modern, static clone of *Upptime*. It continuously monitors your websites and APIs using the free infrastructure of **GitHub Actions** and **GitHub Pages**.

Unlike other systems, UppWebLa **does not use Node.js, npm, or heavy frameworks**. Its architecture relies entirely on pure `Bash` scripts, JSON manipulation via `jq`, interactive charts using `Chart.js`, and a clean frontend built with `HTML`, `CSS`, and `Vanilla JS`.

## ✨ Main Features

* 🌍 **Multi-Region Monitoring:** Simultaneous pings from globally distributed GitHub servers (**America, Europe, and Asia**) via *Ubuntu*, *Windows*, and *macOS*.
* ⚡ **Latency Tracking & Interactive Charts:** Measures response time in milliseconds (`ms`). Clicking any region opens a modal with a detailed performance chart.
* 📢 **Native Incident Management:** Built-in panel to report ongoing maintenance or incidents (`incidents.json`) with *Active / Resolved* states.
* 100% Extensible Multilingual UI: Automatically detects browser language and fetches dictionaries from independent JSON files (`lang/es.json`, `lang/en.json`, etc.).
* 🛡️ **Built-in Cache-Busting:** Smart frontend mechanism bypassing GitHub Pages caching for real-time accuracy.
* 💸 **100% Free:** Zero server or database costs. Fully hosted and executed within GitHub.

## 🛠️ How does the architecture work?

1. **The Cron Job:** A workflow (`uptime.yml`) runs every 5 minutes via GitHub Actions.
2. **Geo-Pings & Latency:** GitHub runners execute advanced `curl` commands to measure HTTP status and response times from 3 continents.
3. **Incremental History:** A final job collects data, updates performance history, and pushes to `data.json`.
4. **Automated Deployment:** GitHub Pages serves the static dashboard instantly.

## 🚀 How to use UppWebLa in your own project

1. **Fork:** Fork this repository to your GitHub account.
2. **Bot Permissions:** Go to `Settings` > `Actions` > `General`, select **Read and write permissions**, and save.
3. **Configure URLs:** Edit `.github/workflows/uptime.yml` to target your own services.
4. **Enable GitHub Pages:** Go to `Settings` > `Pages`, choose **Deploy from a branch** (`main`, root folder).

## 🔄 How to update your UppWebLa clone

1. Go to your repository's main page.
2. Click **"Sync fork"** and then **"Update branch"** when updates are available.

## 📄 License and Copyright

This project is open-source and freely available under the [MIT License](LICENSE).

Created, designed, and maintained with ❤️ by **[Rubén Castañeda Matute](https://github.com/lasatagameplays) (LASATA.EU)**. 

> **Note for developers:** You are free to clone and use this monitoring system. The only legal requirement is that **you must keep the original copyright notice** and author credits in your repository.
