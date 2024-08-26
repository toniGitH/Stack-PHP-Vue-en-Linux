![git_y_github_en_linux](../img/bannerGit.png)

<br>

# 🗃 GIT Y GITHUB EN LINUX MINT

>[!IMPORTANT]
>
>En estas instrucciones doy por hecho que ya tienes creada una cuenta en GitHub, y que por tanto ya tienes **nombre de usuario** e **email de usuario** en Github.
>
>Por otro lado, en estas instrucciones también doy por hecho de que **tienes habilitada en GitHub la protección de email**, por lo que la plataforma te habrá proporcionado un email público (algo como *91548845+miUsuario... @users.noreply.github.com*), que es el que usaré para esta configuración.
>
>Esta configuración de privacidad hará que cualquier contribución que hagas a repositorios propios o ajenos en GitHub quede vinculada con este email público y no con tu email privado.

<br>

## 📖 Tabla de contenidos

<details>
<summary>Mostrar contenidos</summary>
<br>

- [Verificación de credenciales de GitHub](#-verificación-de-credenciales-de-github)
- [Instalación de Git en Linux](#-instalación-de-git-en-linux)
- [Integración de Git y GitHub en tu sistema](#-integración-de-git-y-github-en-tu-sistema)
- [Integración de Github con Visual Studio Code](#-integración-de-github-con-visual-studio-code)
- [Configuración de credenciales de GitHub para operar por Terminal](#-configuración-de-credenciales-de-github-para-operar-por-terminal)
- [Configuración de la Terminal para que muestre información de la rama de Git](#-configuración-de-la-terminal-para-que-muestre-información-de-la-rama-de-git)
- [Cambiar el nombre de la rama principal de master a main](#-cambiar-el-nombre-de-la-rama-principal-de-master-a-main)
- [Pasos para crear un proyecto Laravel con respaldo en Git y Github](#-pasos-para-crear-un-proyecto-laravel-con-respaldo-en-git-y-github)

   
</details>
<br>

↩️ [Volver al README](../README.md)

<br>

## 🔎 Verificación de credenciales de Github

Lo primero que debes hacer, si no lo has hecho ya, es averiguar tus credenciales en GitHub (es decir, tu **nombre de usuario** y tu **email público** en la plataforma).

Este paso es independiente de Linux, y sólo lo menciono para que te asegures de disponer de estos datos.

<br>

[🔝](#-git-y-github-en-linux-mint)
<br>
<br>

## ⚒ Instalación de Git en Linux

1) Realiza una actualización previa de paquetes

   Abre una Terminal, y ejecuta:
   ~~~
   sudo apt update
   ~~~
   Y si existen actualizaciones, instálalas ejecutando:
   ~~~
   sudo apt upgrade
   ~~~

2) Instala git, ejecutando

   ~~~
   sudo apt install git
   ~~~

3) Verifica la instalación de git, ejecutando:

   ~~~
   git --version
   ~~~

<br>

[🔝](#-git-y-github-en-linux-mint)
<br>
<br>

## 🧩 Integración de Git y GitHub en tu sistema

Antes de poder empezar a trabajar con repositorios tanto desde editores de código (como VSC) como desde la Terminal de Linux, es necesario que integres (o vincules) Git con GitHub en tu ordenador.

Para ello, debes tener a mano tu nombre de usuario (por ejemplo, *miUsuario*) y tu email público (por ejemplo, *91548845+miUsuario... @users.noreply.github.com*) en GitHub.

Para configurar el nombre de usuario y el email de GitHub en tu sistema Linux a nivel global, ejecuta los siguientes comandos en la Terminal (los puedes ejecutar en cualquier ubicación, porque los estás ejecutando a nivel grobal):
~~~
git config --global user.name "miUsuario"
~~~
~~~ 
git config --global "91548845+miUsuario@users.noreply.github.com"
~~~

En algunos casos las comillas son opcionales, pero es una buena práctica ponerlas siempre.

<br>

[🔝](#-git-y-github-en-linux-mint)
<br>
<br>

## 🧩 Integración de GitHub con Visual Studio Code

Una vez que hayas completado los pasos anteriores, ya podrás configurar VSC para integrarlo con Git y GitHub.

Aquí te dejo el enlace a las [intrucciones para integrar VSC con Git y GitHub](/Stack%20principal/04-VSC.md).

<br>

[🔝](#-git-y-github-en-linux-mint)
<br>
<br>

## ⚙ Configuración de credenciales de GitHub para operar por Terminal

Para poder hacer las operaciones habituales (push, pull, etc...) desde terminal **sin que te pida las credenciales de GitHub en cada operación**, tienes que tener creado en GitHub un *personal acces token*, y debes hacer lo siguiente:

1) Crea un repo local y uno remoto vinculados.
2) En VSC (una vez que hayas completado la configuración de VSC), haz un cambio en local y haz el commit, pero **sin sincronizarlo** con el repositorio remoto (es decir, sin hacer el *push* a GitHub).
3) Abre una Terminal y ejecuta:
   ~~~
   git config --global credential.helper store
   ~~~
5) También en la Terminal, ejecuta, ahora sí, el *push*:
   ~~~
   git push
   ~~~
   (Te pedirá nombre de usuario y contraseña de GitHub).
7) Ingresa el nombre de usuario (por ejemplo, miUsuario).
8) Ingresa, **en lugar de la contraseña el *personal acces token* de github** que tengas configurado.

   Con esto, ya quedará almacenado el token para todas las operaciones (pull, push, etc...) que hagas desde la Terminal.

9) Comprueba las credenciales que acabas de vincular a tu sistema ejecutando:
   
   ~~~
   cat ~/.git-credentials
   ~~~
   
   Lo que debe devolver algo así:

   `https://tuUsuarioDeLinux:ghp_................@github.com`

   Y ejecuta también:

   ~~~
   git config --global --get credential.helper
   ~~~

   Lo que debe devolver `store`

>[!CAUTION]
>
>Si nadie más tiene acceso a tu ordenador, esta forma de almacenar las credenciales de GitHub es suficiente, pero debes saber que es un método muy poco seguro, puesto que lo hace en texto plano, por lo que te recomiendo que busques una alternativa mejor.
>
>Por ejemplo, puedes utilizar `git-credential-cache` en lugar de `git-credential-store`, que almacena las credenciales sólo temporalmente, o utilizar algún sistema de cifrado, como *libsecret*.
   
<br>

[🔝](#-git-y-github-en-linux-mint)
<br>
<br>

## ⚙ Configuración de la Terminal para que muestre información de la rama de Git

Si quieres que al abrir un directorio en la Terminal de Linux, en ésta te apareaca la información de la rama actual (main, develop, etc...), sigue las siguientes instrucciones.

1) En el explirador de archivos de Linux, accede a la carpeta personal de tu usuario.
2) Selecciona la opción de mostrar los archivos ocultos y busca un archivo llamado **.bashrc**.
3) Abre ese archivo con un editor de textos.
4) Al final del todo, añade todo esto:
   
   ~~~
   # Git branch in prompt
   parse_git_branch() {
     git branch 2>/dev/null | grep '^*' | colrm 1 2
   }
   export PS1="\u@\h \w \[\033[32m\]\$(parse_git_branch)\[\033[00m\]$ "
   ~~~
   
5) Recarga el archivo de configuración ejecutando:
   
   ~~~
   source ~/.bashrc
   ~~~

<br>

[🔝](#-git-y-github-en-linux-mint)
<br>
<br>

## 🔄 Cambiar el nombre de la rama principal de master a main

Por defecto, al inicializar un repositorio de Git con "git init", el nombre de la rama principal es "master".

Puedes cambiar el nombre de "master" a "manin" (o al que prefieras), que es la nomenclatura más utilizada actualmente, de forma que cada vez que inicialices un repositorio de Git, por defecto el mombre de su rama principal sea "main".

Para hacerlo, puedes seguir estos pasos.

1) Verifica la configuración actual de Git, para averiguar qué nombre se está asignando por defecto a la rama principal. Para ello, ejecuta en una Terminal:

   ~~~
   git config --global init.defaultBranch
   ~~~

   Si no responde nada, eso significa que el nombre que se asigna por defecto a la rama principal es "master".

   En cambio, si lo hubieras cambiado en algún momento, la respuesta a esa instrucción sería "main" (o el nombre que le asignaste).

2) Suponiendo que no lo has cambiado hasta ahora, y quieres que el nombre de la rama principal sea siempre por defecto "main" para todos los nuevos repositorios de Git, ejecuta esta instrucción en una Terminal:

   ~~~
   git config --global init.defaultBranch main
   ~~~

   Esto no modifica el nombre de la rama principal en tus repositorios ya existentes, sino que tendrá efecto para todos aquellos que inicialices a partir de este momento.

<br>

[🔝](#-git-y-github-en-linux-mint)
<br>
<br>

## 👣 Pasos para crear un proyecto Laravel con respaldo en Git y Github

Hay diferentes caminos para crear un proyecto en Laravel y darle respaldo a nivel local con Git y remoto con GitHub.

Yo recomiendo seguir los siguientes pasos.

1) En una Terminal, sitúate dentro de la carpeta que va a almacenar tu proyecto (por ejemplo, Proyectos).

2) Una vez dentro de esa carpeta, crea el proyecto Laravel (usando el comando de Composer o el instalador de Laravel).

   Supongamos que quieres crear un proyecto laravel llamado "mi-app" con la versión 9.5.2.

   Para ello, ejecuta:

   ~~~
   composer create-project --prefer-dist laravel/laravel:9.5.2 mi-app
   ~~~

   Tras este paso, ya tendrás tu proyecto Laravel creado en tu ordenador, con toda su estructura básica, pero sin respaldo en Git ni Github.

3) En la Terminal, entra dentro de la carpeta del proyecto (en este caso, "mi-app"), ejecutando:

   ~~~
   cd mi-app
   ~~~

4) Inicializa un repositorio Git, ejecutando:

   ~~~
   git init
   ~~~

   Ahora, en tu proyecto, se ha generado una carpeta oculta llamada ***.git***, lo que significa que Git ya está haciendo seguimiento.

   Sin embargo, si tratas de consultar la rama en la que estás, ejecutando:

   ~~~
   git branch
   ~~~

   verás que el terminal no te responde nada, y eso es porque **para que Git muestre la rama actual, necesitas hacer al menos un commit inicial**.

5) Como dentro de tu carpeta del proyecto (mi-app) ya existe contenido, puedes hacer ese primer commit con todo ese contenido.

   Para ello, en una Terminal, dentro de la carpeta del proyecto (mi-app), ejecuta:

   ~~~
   git add .
   ~~~

   Y justo después, realiza el commit propiamente dicho, ejecutando:

   ~~~
   git commit -m "commit inicial - creación de proyecto"
   ~~~

   El mensaje del commit puede ser el que tú prefieras.

   Ahora sólo falta el respaldo de tu proyecto en remoto, en Github.

7) Crea el repositorio de GitHub que va a estar vinculado a tu proyecto/repositorio local.

   Para ello, entra en tu cuenta de GitHub y crea un repositorio (el nombre del repo remoto no tiene por qué coincidir con el nombre del ptoyecto, pero es recomendable).

   Te recomiendo que le pongas **descripción**, pero no crees un **readme** aún, para evitar conflictos.

   Si quieres crear un archivo **readme** puedes hacerlo en un commit posterior.

   Como en este paso no estás generando contenido dentro del repositorio remoto de GitHub (sólo estás creando un repo vacío), no podrás ver ninguna estructura de carpetas ni archivos aún, pero si verás una serie de opciones que puedes ejecutar.

7) Una vez creado el repositorio de GitHub, deberás ejecutar las tres líneas que aparecen en la opción ***…or push an existing repository from the command line***.

   La primera es para vincular tu repositorio local de Git con tu repositorio remoto de GitHub, ejecutando, en la Terminal, dentro de la carpeta raíz de tu proyecto:

   ~~~
   git remote add origin https://github.com/tuUsuarioGitHub/tuProyecto.git
   ~~~

   Recuerda cambiar *tuUsuarioGitHub* y *tuProyecto* por los valores reales.

   La segunda línea, que es `git branch -M main`, sólo es para renombrar la rama principal del repo de GitHub de "master" a "main", por lo que no hace falta que la ejecutes si ya configuraste Git anteriormente para que la rama principal se llame "main" por defecto.

   Y finalmente, la tercera de las instrucciones de esa opción, para subir los archivos que tienes en tu repo local de Git a tu repo local de Github.

   Para ello, ejecuta, en la terminal:

   ~~~
   git push -u origin main
   ~~~

   Al ser ésta la primera vez que subes contenido desde tu repo local a tu repo remoto, debes ejecutar el comando tal y como te lo he descrito para establecer la rama de seguimiento.

   Esto es así porque la primera vez que empujas una rama nueva al repositorio remoto, Git no sabe a qué rama remota debe empujar los cambios. Por eso, necesitas usar -u para establecer la rama de seguimiento.

   Para futuras subidas, puedes simplemente ejecutar:

   ~~~
   git push origin main
   ~~~

   O incluso:

   ~~~
   git push
   ~~~

<br>

>[!TIP]
>
>Para verificar la correcta vinculación de ambos repositorios, puedes ejecutar:
>
>~~~
>git remote -v
>~~~
>
>Y te debería salir algo así:
>
>`origin	https://github.com/toniGitH/speak-smarter.git (fetch)`
>
>`origin	https://github.com/toniGitH/speak-smarter.git (push)`


<br>

[🔝](#-git-y-github-en-linux-mint)
<br>
<br>
