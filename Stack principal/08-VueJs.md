![vuejs_en_linux](../img/bannerVueJS.png)

<br>

# 🌟 VUE.JS EN LINUX MINT

Para crear un proyecto Vue.js actualmente, las dos formas principales son:

- utilizando **VueCLI**, que es la herramienta oficial de Vue, que hay que instalar, y que utiliza *Webpack*.
- utilizando **Vite**, más moderna y que no requiere la instalación de VueCLI.

En ambos casos, es necesario que tengas instalado **Node.js** y **npm** en tu ordenador.

Si no tienes instalado **Node.js** y **npm** puedes ver las instrucciones en [este enlace](/Stack%20principal/07-NodeJs.md)

<br>

## 📖 Tabla de contenidos
<br>
<details>
<summary>OPCIÓN 1: Vue.js con VueCLI</summary>
<br>
   
   - [Instalación de VueCLI](#-instalación-de-vuecli)
   - [Creación de un nuevo proyecto con VueCLI](#-creación-de-un-nuevo-proyecto-con-vuecli)
   - [Ejemplo de configuración de un proyecto con VueCLI](#-ejemplo-de-configuración-de-un-proyecto-con-vuecli)
   - [Ejecución de un proyecto con VueCLI](#-ejecución-de-un-proyecto-con-vuecli)
   - [Configuración del repositorio de Git](#-configuración-del-repositorio-de-git)
      
</details>
<br>

<details>
<summary>OPCIÓN 2: Vue.js con Vite</summary>
<br>

   - [Instalación](#-instalación)
   - [Creación de un nuevo proyecto con Vite](#-creación-de-un-nuevo-proyecto-con-vite)
   - [Ejemplo de configuración de un proyecto con Vite](#-ejemplo-de-configuración-de-un-proyecto-con-vite)
   - [Instalación de dependencias](#-instalación-de-dependencias)
   - [Ejecución de un proyecto con Vite](#-ejecución-de-un-proyecto-con-vite)

</details>
<br>  

<br>

↩️ [Volver al README](../README.md)

<br>

## 1️⃣ **OPCIÓN 1**: Vue.js con VueCLI

<br>

### 🛠 Instalación de VueCLI

1) Asegúrate de tener instalado **Node.js** y **npm**

   Para comprobar la instalación de **Node.js**, abre una Terminal y ejecuta en cualquier ubicación:
   
   ~~~
   node -v
   ~~~
   
   Y deberías obtener algo así:
   
   `v22.2.0`
   
   Y para comprobar la instalación de **npm**, abre una Terminal y ejecuta en cualquier ubicación:
   
   ~~~
   npm-v
   ~~~
   
   Y deberías obtener algo así:
   
   `10.8.1`

2) Actualiza los repositorios si aún no lo has hecho, ejecutando:

   ~~~
   sudo apt update
   sudo apt upgrade
   ~~~
   
3) Instala Vue CLI de manera global en el ordenador ejecutando en cualquier ubicación de una Terminal:

   ~~~
   npm install -g @vue/cli
   ~~~

4) Verifica la correcta instalación de Vue ejecutando en cualquier ubicación de una Terminal:

   ~~~
   vue --version
   ~~~
   Deberías obtener algo así:
      
   `@vue/cli 5.0.8`
   
<br>

[🔝](#-vuejs-en-linux-mint)
<br>
<br>

### 🪄 Creación de un nuevo proyecto con VueCLI

Para crear un nuevo proyecto de Vue.js mediante el instalador de VueCLI, sigue los siguientes pasos.

1) Abre una Terminal y entra en la ubicación donde quieras crear el proyecto (por ejemplo, htdocs, proyectos, etc...).

2) Dentro de esa ubicación ejecuta:

   ~~~
   vue create nombre-del-proyecto
   ~~~
   
3) Tras ejecutar el anterior comando, aparecerá un "asistente" de configuración de proyecto en el que habrá que ir seleccionando diferentes opciones, y que pasaré a detallar en el siguiente apartado.

   La elección de la configuración dependerá de los conocimientos que tengas sobre VUE y de las necesidades del proyecto.

4) Tras la ejecución del asistente, el proyecto queda configurado y no es necesario ejecutar `npm install`, puesto que VueCLI lo hace automáticamente.

<br>

[🔝](#-vuejs-en-linux-mint)
<br>
<br>

### 💡 Ejemplo de configuración de un proyecto con VueCLI

Un ejemplo incial básico sería el siguiente:

   >**PREGUNTA**:
   >
   >Selección inicial (VUE2 por defecto, VUE3 por defecto o Selección manual de características)
   >
   >*RESPUESTA*:
   >
   >Manually select features + Intro
   >
   >**PREGUNTA**:
   >
   >Selección/deselección de características
   >
   >*RESPUESTA*:
   >
   >Selecciona estas características: Babel, TypeScript y Linter/Formatter (si alguna está deseleccionada, se selecciona con barra espaciadora).
   >
   >Deselecciona el resto de opciones que estén seleccionadas (también se deselecciona con barra espaciadora).
   >
   >Intro
   >
   >En función de las opciones anteriores, se preguntará por configuraciones relacionadas.
   >
   >**PREGUNTA**:
   >
   >Elegir versión de Vue.js deseada para el proyecto
   >
   >*RESPUESTA*:
   >
   >Escoger la 3.x y pulsar Intro
   >
   >**PREGUNTA**:
   >
   >Use class-style component syntax (y/n)
   >
   >*RESPUESTA*:
   >
   >Selecciona N
   >
   >**PREGUNTA**:
   >
   >Use Babel alongside TypeScript (y/n)
   >
   >*RESPUESTA*:
   >
   >Selecciona Y
   >
   >**PREGUNTA**:
   >
   >Pick a linter/formatter config
   >
   >*RESPUESTA*:
   >
   >Selecciona "ESLint with error prevention only"
   >
   >**PREGUNTA**:
   >
   >Pick additional lint features (nos pregunta cuándo queremos "lintear")
   >
   >*RESPUESTA*:
   >
   >Seleccionar Lint on save
   >
   >**PREGUNTA**:
   >
   >Where do you prefer placing config for Babel, ESLint, etc.?
   >
   >*RESPUESTA*:
   >
   >Selecciona la opción de "In dedicated config files" (en general, esto siempre es lo recomendado)
   >
   >**PREGUNTA**:
   >
   >Save this as a preset for future projects?
   >
   >*RESPUESTA*:
   >
   >Contesta que no (N), o contesta que (Y) y dale un nombre a ésta configuración, como por ejemplo, "Babel-TS-Linter config"

<br>

Durante la construcción del proyecto, tal vez VSC te preguntará si quieres añadir la carpeta "node_modules" al gitignore, y deberías responder que SI

Con esto, se habrá creado, dentro de la ubicación que hayas elegido inicialmente (htdocs, proyectos, etc...) una carpeta con el nombre que le diste a tu proyecto (por ejemplo, *nombre-del-proyecto*) y que contendrá todos los archivos y carpetas necesarios para empezar a desarrollar tu proyecto en Vue.js.


[🔝](#-vuejs-en-linux-mint)
<br>
<br>

### ▶ Ejecución de un proyecto con VueCLI

Una vez finalizada la instalación podrás ejecutar el servidor de desarrollo.

Para ello, en una Terminal de Linux o en una terminal de VSC, sitúate en la carpeta raíz de tu proyecto y ejecuta:

~~~
npm run serve
~~~

Este comando **iniciará un servidor local** y podrás ver tu aplicación accediendo a **http://localhost:8080** en tu navegador.

<br>

[🔝](#-vuejs-en-linux-mint)
<br>
<br>

### ⚙ Configuración del repositorio de Git

Tras la creación del proyecto de VueJS, el instalador crea un repositorio de git, pero es posible que lo cree con la nomenclatura antigua de git, es decir, la que a la rama principal la llama ***master***.

Para cambiar este nombre a la nomenclatura actual, que es ***main***, debes hacer lo siguiente.

1) Abre una Terminal y entra en la carpeta raíz del proyecto.

2) Asegurate de que estás en la rama correcta (*master*), y si no, ejecuta:

   ~~~
   git checkout master
   ~~~

3) Cambia el nombre de la rama a ***main***, ejecutando:

   ~~~
   git branch -m master main
   ~~~

<br>

[🔝](#-vuejs-en-linux-mint)
<br>
<br>

## 2️⃣ **OPCIÓN 2**: Vue.js con Vite

<br>

### 🛠 Instalación

Si eliges la opción de Vite para trabajar con VueJS, no es necesario ninguna instalación específica, como sería el caso de la instalación con VueCLI, excepto asegurarte de tener instalado tanto NodeJs como NPM, que sí son imprescindibles.

<br>

[🔝](#-vuejs-en-linux-mint)
<br>
<br>

### 🪄 Creación de un nuevo proyecto con Vite

Para crear un nuevo proyecto Vue.js con la opción de Vite, sigue los siguientes pasos.

1) Abre una Terminal y entra en la ubicación donde quieras crear el proyecto (por ejemplo, htdocs, proyectos, etc...).

2) Dentro de esa ubicación ejecuta:

   ~~~
   npm create vue@latest
   ~~~

   En este paso, aún no le tienes que poner nombre al proyecto.
   
3) Tras ejecutar el anterior comando, aparecerá un "asistente" de configuración de proyecto en el que habrá que ir seleccionando diferentes opciones, y que pasaré a detallar en el siguiente apartado.

<br>

[🔝](#-vuejs-en-linux-mint)
<br>
<br>

### 💡 Ejemplo de configuración de un proyecto con Vite

Tras la ejecución del comando anterior, se mostrarán indicaciones para varias funciones opcionales, como compatibilidad con TypeScript y pruebas.

✔ Project name: … <your-project-name>

✔ Add TypeScript? … No / Yes

✔ Add JSX Support? … No / Yes

✔ Add Vue Router for Single Page Application development? … No / Yes

✔ Add Pinia for state management? … No / Yes

✔ Add Vitest for Unit testing? … No / Yes

✔ Add an End-to-End Testing Solution? … No / Cypress / Nightwatch / Playwright

✔ Add ESLint for code quality? … No / Yes

✔ Add Prettier for code formatting? … No / Yes

✔ Add Vue DevTools 7 extension for debugging? (experimental) … No / Yes

Scaffolding project in ./<your-project-name>...
Done.

<br>

Si no estás seguro de alguna opción, simplemente elige "No" y presiona Enter.

<br>

[🔝](#-vuejs-en-linux-mint)
<br>
<br>

### ⚙ Instalación de dependencias

Una vez creado el proyecto, debes entrar dentro de la carpeta raíz de dicho proyecto y ejecutar:

~~~
npm install
~~~

Cuando se ejecuta este comando, **npm** primero lee el archivo ***package.json*** de tu proyecto para determinar qué paquetes y versiones de éstos necesitas instalar directamente. Esto incluye las dependencias que has definido explícitamente en la sección "dependencies" o "devDependencies" de package.json.

Además del package.json, npm consulta el archivo ***package-lock.json***, si existe. Este archivo especifica la estructura exacta de las dependencias instaladas en tu proyecto, incluyendo las versiones exactas de sus dependencias.

Tras esto, npm utiliza la información de package.json y package-lock.json para resolver las dependencias necesarias y garantizar que las versiones instaladas sean coherentes y compatibles entre sí. Si no hay un package-lock.json presente, npm lo generará automáticamente después de la instalación.

El archivo package-lock.json asegura que cualquier persona que clone tu proyecto o lo instale en otro entorno obtenga exactamente las mismas versiones de dependencias. Esto es crucial para mantener la consistencia y prevenir problemas de compatibilidad que podrían surgir con diferentes versiones de paquetes.

Después de leer/verificar los archivos package.json y package-lock.json, la carpeta ***node_modules*** se crea dentro de tu proyecto si no existe, o se actualiza si ya contiene algunas dependencias. Esta carpeta contiene todos los paquetes y módulos de Node.js que tu proyecto necesita para funcionar.

<br>

[🔝](#-vuejs-en-linux-mint)
<br>
<br>

### ▶ Ejecución de un proyecto con Vite

Una vez finalizada la instalación podrás ejecutar el servidor de desarrollo.

Para ello, en una Terminal de Linux o en una terminal de VSC, sitúate en la carpeta raíz de tu proyecto y ejecuta:

~~~
npm run dev
~~~

Como ves, el comando de ejecución del servidor es diferente del que se utiliza si has creado el proyecto con VueCLI.

La ejecución de este comando inicia un servidor de desarrollo junto con una compilación optimizada para el entorno de desarrollo, suficiente para probar la aplicación en desarrollo.

Ahora podrás ver tu aplicación accediendo a **http://localhost:5173** en tu navegador.

<br>

[🔝](#-vuejs-en-linux-mint)
<br>
<br>
