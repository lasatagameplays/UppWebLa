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

<p><b>Monitor de estado web (Uptime) Open Source, Multirregión y 100% Serverless.</b></p>

## 🚀 ¿Qué es UppWebLa?

**UppWebLa** es un clon ultra ligero y estático de *Upptime*. Está diseñado para monitorizar el estado de tus páginas web y APIs de forma ininterrumpida utilizando la infraestructura gratuita de **GitHub Actions** y **GitHub Pages**.

A diferencia de otros sistemas, UppWebLa **no utiliza Node.js, npm, ni frameworks pesados**. Toda su arquitectura está construida con scripts puros de `Bash`, manipulación JSON con `jq` y una interfaz de usuario desarrollada en `HTML`, `CSS` y `Vanilla JS`. Esto garantiza que el proyecto jamás quedará obsoleto por dependencias desactualizadas.

## ✨ Características Principales

* 🌍 **Monitorización Multirregión:** Realiza pings simultáneos utilizando los servidores de GitHub distribuidos globalmente (América, Europa y Asia) a través de *Ubuntu*, *Windows* y *macOS*.
* 🌐 **Interfaz Multilenguaje Nativa:** El dashboard detecta automáticamente el idioma del navegador del usuario (Español o Inglés) y traduce todos los textos y formatos de fecha al instante.
* ⚡ **Ultra Ligero (Zero Dependencies):** Sin pesadas carpetas `node_modules` ni configuraciones complejas. Solo código nativo.
* 🛡️ **Anti-Caché Integrado:** Sistema inteligente en el frontend que rompe la caché de GitHub Pages para mostrar siempre el estado real en el segundo exacto.
* 💸 **100% Gratuito:** Sin costes de servidores, bases de datos o servicios de terceros. Todo se ejecuta y se aloja dentro de GitHub.

## 🛠️ ¿Cómo funciona la arquitectura?

1. **El Cron Job:** Un flujo de trabajo (`uptime.yml`) se ejecuta cada 5 minutos mediante GitHub Actions.
2. **Pings Geográficos:** Los *runners* de GitHub ejecutan peticiones `curl` a los servicios configurados desde 3 continentes distintos.
3. **Unificación:** Un trabajo final recolecta los resultados, los formatea y actualiza un archivo `data.json`.
4. **Despliegue Automático:** Un bot hace un `git push` silencioso al repositorio. GitHub Pages sirve el `index.html` estático que lee este JSON en tiempo real.

## 🚀 Cómo usar UppWebLa en tu propio proyecto

Eres libre de clonar este repositorio para monitorizar tus propias páginas web. Solo tienes que seguir estos pasos:

1. **Bifurcar (Fork):** Haz un *Fork* de este repositorio a tu propia cuenta de GitHub.
2. **Permisos del Bot:** * Ve a `Settings` > `Actions` > `General` en tu nuevo repositorio.
   * En "Workflow permissions", selecciona **Read and write permissions** y guarda.
3. **Configurar URLs:**
   * Edita el archivo `.github/workflows/uptime.yml`.
   * Cambia las URLs `https://lasata.eu` por las páginas web o APIs que quieras monitorizar.
4. **Activar GitHub Pages:**
   * Ve a `Settings` > `Pages`.
   * En "Source", selecciona **Deploy from a branch**.
   * Elige la rama `main` y la carpeta `/ (root)`, luego pulsa guardar.

Una vez configurado, ve a la pestaña **Actions** y ejecuta el flujo de trabajo manualmente por primera vez. ¡A partir de ahí, funcionará solo!

## 🔄 Cómo actualizar tu clon de UppWebLa

Este proyecto está en constante evolución. Si en el futuro lanzamos nuevas versiones de la interfaz gráfica (`index.html`) o del motor de pings (`uptime.yml`), actualizar tu monitorización es extremadamente sencillo y 100% seguro:

1. Ve a la página principal de tu repositorio en GitHub.
2. Si hay actualizaciones disponibles, verás un mensaje debajo del botón de código verde que dice *"This branch is X commits behind lasatagameplays/UppWebLa"*.
3. Haz clic en el botón **"Sync fork"** y luego en **"Update branch"**.
4. ¡Listo! Tu código se actualizará automáticamente con nuestras últimas mejoras manteniendo intactos tus datos históricos de estado (`data.json`).

## 📄 Licencia y Copyright

Este proyecto es de código abierto y está disponible gratuitamente bajo los términos de la [Licencia MIT](LICENSE).

Creado, diseñado y mantenido con ❤️ por **[Rubén Castañeda Matute](https://github.com/lasatagameplays) (LASATA.EU)**. 

> **Nota para desarrolladores:** Eres libre de clonar, bifurcar (fork) y utilizar este sistema de monitorización para tus propias páginas web o proyectos comerciales. El único requisito legal es que **debes mantener el aviso de copyright original** y los créditos al autor en tu repositorio.

<br>

---

# 🇬🇧 English

<p><b>Open Source, Multi-Region, and 100% Serverless Web Status Monitor (Uptime).</b></p>

## 🚀 What is UppWebLa?

**UppWebLa** is an ultra-lightweight, static clone of *Upptime*. It is designed to continuously monitor the status of your websites and APIs using the free infrastructure of **GitHub Actions** and **GitHub Pages**.

Unlike other systems, UppWebLa **does not use Node.js, npm, or heavy frameworks**. Its entire architecture is built with pure `Bash` scripts, JSON manipulation using `jq`, and a UI developed in `HTML`, `CSS`, and `Vanilla JS`. This ensures the project will never become obsolete due to outdated dependencies.

## ✨ Main Features

* 🌍 **Multi-Region Monitoring:** Performs simultaneous pings using globally distributed GitHub servers (America, Europe, and Asia) via *Ubuntu*, *Windows*, and *macOS*.
* 🌐 **Native Multilingual Interface:** The dashboard automatically detects the user's browser language (Spanish or English) and translates all texts and date formats instantly.
* ⚡ **Ultra Lightweight (Zero Dependencies):** No heavy `node_modules` folders or complex configurations. Pure native code only.
* 🛡️ **Built-in Cache-Busting:** Smart frontend system that breaks the GitHub Pages cache to always display real-time status to the exact second.
* 💸 **100% Free:** No server, database, or third-party service costs. Everything runs and is hosted entirely inside GitHub.

## 🛠️ How does the architecture work?

1. **The Cron Job:** A workflow (`uptime.yml`) runs every 5 minutes via GitHub Actions.
2. **Geographical Pings:** GitHub *runners* execute `curl` requests to the configured services from 3 different continents.
3. **Unification:** A final job collects the results, formats them, and updates a `data.json` file.
4. **Automated Deployment:** A bot performs a silent `git push` to the repository. GitHub Pages serves the static `index.html` which reads this JSON in real time.

## 🚀 How to use UppWebLa in your own project

You are free to clone this repository to monitor your own websites. Just follow these simple steps:

1. **Fork:** Fork this repository to your own GitHub account.
2. **Bot Permissions:** * Go to `Settings` > `Actions` > `General` in your new repository.
   * Under "Workflow permissions", select **Read and write permissions** and save.
3. **Configure URLs:**
   * Edit the `.github/workflows/uptime.yml` file.
   * Change the `https://lasata.eu` URLs to the websites or APIs you want to monitor.
4. **Enable GitHub Pages:**
   * Go to `Settings` > `Pages`.
   * Under "Source", select **Deploy from a branch**.
   * Choose the `main` branch and the `/ (root)` folder, then hit save.

Once configured, go to the **Actions** tab and manually run the workflow for the first time. From then on, it will run on its own!

## 🔄 How to update your UppWebLa clone

This project is constantly evolving. If we release new versions of the UI (`index.html`) or the ping engine (`uptime.yml`) in the future, updating your monitor is extremely simple and 100% safe:

1. Go to your repository's main page on GitHub.
2. If updates are available, you will see a message below the green code button saying *"This branch is X commits behind lasatagameplays/UppWebLa"*.
3. Click the **"Sync fork"** button and then **"Update branch"**.
4. Done! Your code will automatically update with our latest improvements while keeping your historical status data (`data.json`) intact.

## 📄 License and Copyright

This project is open-source and freely available under the terms of the [MIT License](LICENSE).

Created, designed, and maintained with ❤️ by **[Rubén Castañeda Matute](https://github.com/lasatagameplays) (LASATA.EU)**. 

> **Note for developers:** You are free to clone, fork, and use this monitoring system for your own websites or commercial projects. The only legal requirement is that **you must keep the original copyright notice** and author credits in your repository.