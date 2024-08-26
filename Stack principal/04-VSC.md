![visual_studio_code_en_linux](../img/bannerVSC.png)

<br>

# ⌨ VISUAL STUDIO CODE EN LINUX MINT

<br>

## 📖 Tabla de contenidos

<details>
   
   <summary>Mostrar contenidos</summary>
   <br>
   
   - [Instalación de Visual Studio Code en Linux Mint](#-instalación-de-visual-studio-code-en-linux-mint)
   - [Configuración de VSC en Linux](#-configuración-de-vsc-en-linux)
   - [¿Qué hay que configurar?](#-qué-hay-que-configurar)
   - [El archivo de configuración *settings.json*](#-el-archivo-de-configuración-settingsjson)
   - [Configuración de PHP en VSC en Linux](#-configuración-de-php-en-vsc-en-linux)
   - [Sincronización en la nube de tu VSC-Windows con tu VSC-Linux](#-sincronización-en-la-nube-de-tu-vsc-windows-con-tu-vsc-linux)
   - [Clonado manual de la configuración de VSC](#-clonado-manual-de-la-configuración-de-vsc)
   - [La extensión PHP Server de VSC](#-la-extensión-php-server-de-vsc)
   - [Integración de Github con Visual Studio Code](#-integración-de-github-con-visual-studio-code)


</details>
<br>

↩️ [Volver al README](../README.md)

<br>

# ⚒ Instalación de Visual Studio Code en Linux Mint

La forma recomendada de instalar Visual Studio Code (VSC) en Linux Mint es a través de los repositorios oficiales de Microsoft.

Para ello, sigue los siguientes pasos.

1) Abre una Terminal y actualiza paquetes, ejecutando:
   
   ~~~
   sudo apt update
   ~~~
   Y si existen actualizaciones, instálalas ejecutando:
   ~~~
   sudo apt upgrade
   ~~~

2) Asegúrate de que tienes instaladas las dependencias necesarias para la instalación desde los repositorios HTTPS ejecutando:
   
   ~~~
   sudo apt install software-properties-common apt-transport-https wget
   ~~~

3) Importa la clave GPG de Microsoft.
   
   Este paso permite verificar la autenticidad del paquete que descargarás.
   
   Para ello, ejecuta:
   
   ~~~
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
   ~~~
   ~~~
   sudo install -o root -g root -m 644 packages.microsoft.gpg /usr/share/keyrings
   ~~~
   ~~~
   sudo apt-get install -y apt-transport-https
   ~~~
   
4) Después de importar la clave GPG de Microsoft, debes añadir el repositorio de Visual Studio Code a tu lista de fuentes de software, ejecutando:
   
   ~~~
   echo "deb [arch=amd64 signed-by=/usr/share/keyrings/packages.microsoft.gpg] https://packages.microsoft.com/repos/vscode stable main" | sudo tee /etc/apt/sources.list.d/vscode.list
   ~~~

5) Vuelve a actualizar el índice de paquetes nuevamente, para asegurarte de que el sistema ahora tiene acceso a los paquetes de Visual Studio Code desde el nuevo repositorio:
   
   ~~~
   sudo apt update
   ~~~
6) Instala Visual Studio Code ejecutando:
   
   ~~~
   sudo apt install code
   ~~~

Una vez completados estos pasos, Visual Studio Code estará instalado en tu sistema Linux Mint y podrás ejecutarlo desde el menú de aplicaciones o desde la terminal con el comando code.

Este método asegura que tienes una instalación estable y actualizada de Visual Studio Code, directamente mantenida por Microsoft.

<br>

>[!NOTE]
>**¿Para qué añadir el repositorio de VSC?**
>
>Añadir el repositorio de Visual Studio Code (VSC) es necesario para que tu sistema Linux Mint pueda obtener actualizaciones automáticas de VSC a través del sistema de gestión de paquetes (APT).
>
>Cuando añades el repositorio de VSC, estás básicamente indicando a tu sistema operativo dónde puede encontrar los paquetes de software específicos de Visual Studio Code y cómo verificar su autenticidad usando la clave GPG de Microsoft. Esto facilita la instalación inicial y las actualizaciones futuras de VSC, ya que se integra completamente con el sistema de gestión de paquetes de tu distribución Linux (en este caso, Linux Mint).
>
>En resumen, añadir el repositorio de VSC te permite instalar VSC de manera más integrada y obtener actualizaciones automáticas cuando estén disponibles, lo cual es más conveniente y seguro que descargar e instalar manualmente el programa cada vez que hay una nueva versión.

<br>

[🔝](#-visual-studio-code-en-linux-mint)
<br>
<br>


# ⚙ Configuración de VSC en Linux

En este momento ya tienes instalado VSC en tu sistema Linux, pero es muy probable que quieras que esté configurado tal y como ya lo tienes configurado en Windows (git, extensiones, personalizaciones, etc...).

En los siguientes pasos voy a suponer que ya vienes utilizando VSC en Windows y que lo que quieres es "clonar" esa configuración en tu VSC recién instalado en Linux.

<br>

[🔝](#-visual-studio-code-en-linux-mint)
<br>
<br>

# ❓ ¿Qué hay que configurar?

Si ya estabas trabajando con VSC en Windows y quieres que tu instalación en Linux sea lo más parecida posible a lo que venías utilizando, tienes que tener en cuenta que tienes que lo que tienes que intentar es "replicar" en tu instalación de VSC en Linux estas 3 cosas fundamentales:

   - la configuración de PHP en tu VSC de Linux
   - las extensiones que tengas instaladas en tu VSC de Windows
   - los ajustes de configuración de dichas extensiones

Si bien podrías hacer este "clonado" manualmente, eso podría resultar muy tedioso, así que en los siguientes apartados te voy a dar dos alternativas para que lleves a cabo este proceso de forma más rápida y automatizada.

Estas dos alternativas, que detallaré más adelante, son:

1. [Sincronización en la nube](#-sincronización-en-la-nube-de-tu-vsc-windows-con-tu-vsc-linux) de tu VSC de Linux con tu VSC de Windows (recomendada y más rápida y automática).
2. "Clonación" manual de la lista de extensiones y archivo de configuración ***settings.json***

<br>

[🔝](#-visual-studio-code-en-linux-mint)
<br>
<br>

# ⚙ El archivo de configuración settings.json

Antes de entrar en el ajuste de ningún tipo de configuración, es muy importante conocer y entender qué es el archivo ***settings.json*** de VSC.

Como su propio nombre indica, éste es un archivo en formato ***.json*** que almacena todos los parámetros y ajustes de configuración de nuestro VSC (ajustes de extensiones, versión de PHP, etc...), por lo que como puedes acceder a ese archivo desde tu instalación de Windows, ya tienes la mitad del trabajo hecha.

Sin embargo, ese archivo, sólo te falicitará la mitad del trabajo, que es la configuración de las extensiones, pero no la propia instalación de las mismas, aunque esta otra parte, también se puede simplificar, como verás un poco más adelante.

De momento, quédate con que existe un archivo llamado ***settings.json***, para qué sirve y que es muy importante en VSC.

Para acceder a ese archivo y poder hacer una copia "por si las moscas", puedes hacer lo siguiente.

1) En tu instalación de VSC en Windows, haz click en la **rueda dentada** situada en la parte inferior izquierda (*Administrar*)
2) Selecciona la opción de **Configuración**.
3) En la pantalla que se abre, ve a la esquina superior derecha y haz click en el icono que pone **Abrir configuración(JSON)**.
4) Ahora podrías **copiar todo el contenido de ese archivo y guardarlo** en un documento aparte que podrás **recuperar** si esta configuración en tu VSC en Windows se borrara accidentalmente (y te recomiendo encarecidamente que hagas esta copia en este momento).

<br>

[🔝](#-visual-studio-code-en-linux-mint)
<br>
<br>

# ⚙ Configuración de PHP en VSC en Linux

>[!IMPORTANT]
>
>Este paso es fundamental, y por ese motivo lo explico antes de comenzar con ninguna otra configuración y en una sección aparte, porque además, puede variar respecto a la configuración que tengas en tu VSC de Windows.
>
>Básicamente, este paso consiste en "decirle" a tu VSC instalado en Linux en qué ubicación de **tu ordenador** va a encontrar la instalación de PHP que quieres que el editor utilice para ejecutar el código PHP que escribas.
>
>Por tanto, es casi seguro que la ubicación de dicha instalación de PHP en tu configuración de VSC para Windows no coincida con la ubicación de la instalación de PHP en Linux, porque, entre otras cosas, el sistema de archivos de Windows es diferente al de Linux.
>
>Por este motivo, te recomiendo que sigas y entiendas estas instrucciones, y más adelante te será mucho más fácil integrarla/adaptarla en las alternativas que te daré para "trasladar" toda tu configuración de VSC para Windows en tu VSC en Linux.

Los pasos que debes seguir para indicarle a tu VSC de Linux qué PHP debe utilizar son los siguientes.

1) Localiza la ubicación de tu instalación de PHP en Linux (que en este caso es la que viene con XAMPP).

   Lo más probable es que la ubicación sea `/opt/lampp/bin/php`

2) En tu VSC en Linux, haz click en la **rueda dentada** situada en la parte inferior izquierda (*Administrar*).

3) Selecciona la opción de **Configuración**.
   
4) En la pantalla que se abre, ve a la esquina superior derecha y haz click en el icono que pone **Abrir configuración(JSON)**.

5) Tras hacer esto, tendrás abierto en VSC el archivo ***settings.json*** que probablemente estará vacío o casi vacío.
   
   En cualquier caso, debes añadir lo siguiente:
   
   ~~~
   {
    "php.validate.executablePath": "/opt/lampp/bin/php",
    "terminal.integrated.env.linux": {
        "PATH": "/opt/lampp/bin:${env:PATH}"
    }
   }
   ~~~

   Pero ten en cuenta que se trata de un archivo ***.json*** y que deberás tener cuidado con la sintáxis (llaves {}, comas, etc...).

6) Prueba de configuración.
   
   Para estar seguro de que tu VSC de Linux accede correctamente a la instalación de PHP, ejecuta, en una terminal de VSC:

   ~~~
   php --version
   ~~~

   Y deberías obtener una salida como esta:
   
   <br>
   
   >PHP 8.2.4 (cli) (built: Mar 14 2023 17:54:25) (ZTS Visual C++ 2019 x64)
   >
   >Copyright (c) The PHP Group
   >
   >Zend Engine v4.2.4, Copyright (c) Zend Technologies
   >
   >   with Xdebug v3.3.1, Copyright (c) 2002-2023, by Derick Rethans

   <br>

   Debería aparecer la extensión de Xdebug si estás siguiendo todo este manual en el orden que te he propuesto.
   
<br>

[🔝](#-visual-studio-code-en-linux-mint)
<br>
<br>

# ☁ Sincronización en la nube de tu VSC-Windows con tu VSC-Linux

Ahora que ya le has dicho a tu VSC de Linux dónde está la instalación de PHP que debe utilizar, puedes realizar el resto de la configuración de VSC para Linux, siguiendo esta alternativa, o la que te propongo en el siguiente apartado.

>[!CAUTION]
>
>Ten mucho cuidado con esta opción, puesto que si no lo haces correctamente, corres el riesgo de **borrar** la configuración de tu instalación de VSC en Windows.
>
>Este riesgo viene del hecho de que tienes un VSC con una configuración completa (el de Windows) y otro con una configuración vacía (el de Linux), y si te equivocas, tal vez copies la configuración vacía del segundo al primero, en lugar de la configuración completa del primero al segundo.
>
>Así que, antes de elegir esta opción y antes de seguir los pasos que te voy a indicar, te aconsejo que investigues un poco más sobre este proceso.

Una vez dicho esto, te voy a dar las indicaciones básicas para realizar este proceso, aunque ya te adelanto que no son tremendamente exhaustivas, sino más bien una orientación, para que con la ayuda de otros medios, comprendas bien el proceso antes de ponerte a ejecutarlo.

Eso sí, para tener un cierto respaldo por si las cosas salen mal, te recomiendo encarecidamente que hagas una copia de:
- el archivo ***settings.json*** de tu VSC en Windows, tal y como te explico [aquí](#-el-archivo-de-configuración-settingsjson) y de
- la ***lista de extensiones de VSC***, tal y como te explico [aquí](#-generar-lista-de-extensiones-de-vsc).

Una vez hechas esas copias, los pasos para la sincronización son los siguientes.

1) Lo primero que debes hacer es sincronizar **tu configuración de VSC en Windows** con una cuenta de Microsoft o de GitHub.
   
   En el caso de estas instrucciones, yo lo hago mediante la cuenta de GitHub.
   
   Sobre este paso, no te voy a indicar más, porque sería conveniente que investigues en otras fuentes cómo hacerlo.
   
2) Una vez sincronizada la configuración de tu VSC en Windows con la cuenta de GitHub, mi consejo es que **desactives** dicha sincronización, de manera que tu instalación de VSC en Windows no corra peligro de sincronizarse por error con una versión errónea en la nube.
3) Ahora debes abrir VSC en Linux y en la rueda dentada de la esquina inferior izquierda, hacer click en "Configuración de copia de seguridad y sincronizacion"
4) Inicia sesion con GitHub y esperar a la sincronización.
5) Una vez sincronizado, acceder al icono de "Cuentas" (encima de la rueda dentata) y cerrar la sesión en GitHub (para evitar también sincronizaciones futuras no deseadas).
6) **MUY IMPORTANTE**: revisa los ajustes de la instalación de PHP y asegúrate de que para tu configuración de VSC en Linux sean los que te he indicado en [este apartado](#-configuración-de-php-en-vsc-en-linux) y modifícalo manualmente si es necesario.


Tras estos pasos, se deberían haber instalado tanto las extensiones que teníamos en VSC de Windows como sus ajustes.

<br>

[🔝](#-visual-studio-code-en-linux-mint)
<br>
<br>

# 🟰 Clonado manual de la configuración de VSC

La otra alternativa para "copiar" la configuración de tu VSC en Windows a tu VSC en Linux es la opción "manual", **importando primero la lista de extensiones** que tienes instaladas en VSC en Windows y, posteriormente, **copiando el archivo *settings.json*** que tienes en tu VSC con Windows al VSC en Linux (pero teniendo en cuenta que tal vez tengas que ajustar la configuración de la versión de PHP en tu archivo *settings.json* de tu VSC de Linux).

⭐ **Para importar la lista de extensiones:**

1) En Windows debes obtener el listado de las extensiones, ejecutando esto en una terminal de Windows:
   
   ~~~
   code --list-extensions > extensions-list.txt
   ~~~

   Esto generará un archivo llamado ***extensions-list.txt*** dentro de la carpeta en la que hayas ejecutado este comando, que contendrá el listado con todas las extensiones que tienes instaladas en tu VSC en Windows.

   Será algo así (sólo es un ejemplo):

   ```
   adpyke.codesnap
   bierner.color-info
   bmewburn.vscode-intelephense-client
   bradlc.vscode-tailwindcss
   brapifra.phpserver
   cjhowe7.laravel-blade
   cweijan.vscode-mysql-client2
   donjayamanne.githistory
   formulahendry.auto-close-tag
   github.vscode-pull-request-github
   hakcorp.php-awesome-snippets
   huizhou.githd
   idleberg.icon-fonts
   mhutchie.git-graph
   mohamedbenhida.laravel-intellisense
   ms-ceintl.vscode-language-pack-es
   onecentlin.laravel-blade
   onecentlin.laravel5-snippets
   rangav.vscode-thunder-client
   ritwickdey.liveserver
   sdras.night-owl
   shufo.vscode-blade-formatter
   techer.open-in-browser
   vscode-icons-team.vscode-icons
   xdebug.php-debug
   xdebug.php-pack
   ysemeniuk.emmet-live
   zobo.php-intellisense
   ```

3) Copia ese archivo al equipo Linux.
4) Abre una Terminal y ve al directorio donde hayas copiado esa lista .txt.
5) Dentro de ese directorio, en la Terminal, ejecuta esta instrucción:
 
   ~~~
   while read extension; do
     code --install-extension $extension
   done < extensions-list.txt
   ~~~

   Verifica que se hayan instalado todas, porque puede que alguna falle y no se instale. En ese caso, instálala manualmente.

   Una vez hecho esto, ahora ya puedes **copiar** el archivo ***settings.json*** de tu VSC en Windows y **pegarlo** en tu VSC en Linux.

<br>

⭐**Para copiar el archivo settings.json :**

1) Copia el contenido del archivo ***settings.json*** de tu VSC en Windows tal y como te explico [aquí](#-el-archivo-de-configuración-settingsjson).
2) En tu VSC de Linux, haz click en la rueda dentada (Administrar).
3) Selecciona la opción de Configuración.
4) En la pantalla que se abre, ve a la esquina superior derecha y haz click en el icono que pone "Abrir configuración(json)".
5) En el archivo que se abre, añade, a lo que ya aparezca, las líneas de configuración que has obtenido del ***settings.json*** de Windows.

En mi caso, actualmente es esto (sólo es un ejemplo):

```json
{
    "php.validate.executablePath": "/opt/lampp/bin/php",
    "terminal.integrated.env.linux": {
        "PATH": "/opt/lampp/bin:${env:PATH}",
        "PHPRC": "/opt/lampp/etc/php.ini"
    },
    "phpserver.phpPath": "/opt/lampp/bin/php",
    "workbench.startupEditor": "none",
    "files.autoSave": "afterDelay",
    "editor.inlayHints.enabled": "off",
    "git.openRepositoryInParentFolders": "never",
    "workbench.colorTheme": "Night Owl Light",
    "workbench.iconTheme": "vscode-icons",
    "editor.mouseWheelZoom": true,
    "security.workspace.trust.untrustedFiles": "open",
    "codesnap.showWindowControls": false,
    "codesnap.target": "window",
    "codesnap.shutterAction": "copy",
    "php.debug.executablePath": "",
    "editor.minimap.enabled": false,
    "extensions.ignoreRecommendations": true,
    "settingsSync.ignoredSettings": [
         "terminal.integrated.env.linux"
    ],
    "open-in-browser.default": "chrome"
}
```

Insisto en que debes prestar mucha atención a la parte donde le dices a VSC dónde encontrar tu instalación de PHP (que en nuestro caso, es la incluida en XAMPP).

<br>

[🔝](#-visual-studio-code-en-linux-mint)
<br>
<br>

# 🔌 La extensión PHP Server de VSC

Dado que esta extensión es muy útil e interesante, le he dedicado un apartado específico.

Esta extensión de VSC permite ejecutar el código PHP en el navegador, sin necesidad de tener abierto el Xampp, puesto que gracias a ella, se ejecuta el código en un servidor propio de VSC.

La configuración del archivo ***settings.json*** de tu VSC en Linux debería ser ésta:

```json
{
    "php.validate.executablePath": "/opt/lampp/bin/php",
    "terminal.integrated.env.linux": {
        "PATH": "/opt/lampp/bin:${env:PATH}",
        "PHPRC": "/opt/lampp/etc/php.ini"
    },
    "phpserver.phpPath": "/opt/lampp/bin/php"
}
```

💡 **Cómo resolver el problema de cerrar VSC sin cerrar el servidor de PHP Server**

Si ejecutas tu código PHP utilizando este PHP Server, pero cierras VSC sin apagarlo antes, puede que te encuentres con este error al abrirlo en un momento posterior:

`Failed to listen on localhost:3000 (reason: Address already in use)`

Este error indica que el puerto 3000 ya está siendo utilizado por otro proceso.

Para solucionar este problema, debes seguir los siguientes pasos:

1) Identifica el proceso que está utilizando el puerto 3000.

   Para ello, en una terminal de VSC ejecuta el siguiente comando para encontrar el proceso que está ocupando el puerto 3000:
   
   ~~~
   sudo lsof -i :3000
   ~~~
   
   Este comando lanzará una lista de procesos que están utilizando el puerto 3000.

   La salida podría ser algo así:

   ```bash
   COMMAND   PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
   node    12345 user   22u  IPv4  52723      0t0  TCP localhost:3000 (LISTEN)
   ```
   
   En este ejemplo, el proceso con el PID 12345 está utilizando el puerto 3000.

2) Termina el proceso:
   
   Si estás seguro de que el proceso que está utilizando el puerto 3000 no es necesario, puedes terminarlo usando el comando kill:

   ~~~
   sudo kill -9 12345
   ~~~

   Sustituyendo el 12345 por el PID del proceso obtenido del paso 1).
   
<br>

[🔝](#-visual-studio-code-en-linux-mint)
<br>
<br>

# 🧩 Integración de Github con Visual Studio Code

Para integrar Git y GitHub en Visual Studio Code (VSC), sigue estos pasos:

1. Abre Visual Studio Code y ve a la sección de Extensiones.
2. Escribe "GitHub" en la barra de búsqueda.
3. Instala la extensión **GitHub Pull Requests** de GitHub.
4. En GitHub, escoge un repositorio cualquiera para clonar en tu equipo.
5. En VSC abre la paleta de comandos con *Ctrl+Shift+P* y escribe y selecciona ***Git: Clone***.
6. Pega la URL del repositorio de GitHub que quieres clonar.
7. Ahora, en tu explorador de archivos se abrirá una ventana, donde debes seleccionar una carpeta en tu equipo donde clonar el repositorio.
8. Configura la autenticación de GitHub en VSC, abriendo de nuevo la paleta de comandos con ***Ctrl+Shift+P***.
9. Escribe y selecciona ***GitHub: Sign in to GitHub***, con lo que se abrirá un mensaje que dirá *La extensión solicitudes de cambios de GitHub desdea iniciar sesión en Github* y que debes permitir.
10. Ahora, en VSC se está intentando iniciar sesión en github.com (lo verás en las notificaciones de VSC) y al mismo tiempo se abrirá el navegador, con un mensaje solicitando permiso para abrir VSC. Acéptalo.
11. Sigue las instrucciones para autenticar tu cuenta de GitHub.
12. Para comprobar que la vinculación es correcta, puedes ejecutar en el terminal de VSC este comando:
    
    ~~~
    git remote -v
    ~~~
    
    Que debería lanzar una salida de este tipo:

    ```bash
      origin  https://github.com/tuUsuario/nombre_repo_clonado.git (fetch)
      origin  https://github.com/tuUsuario/nombre_repo_clonado.git (push)
    ```

   Podrías hacer diferentes pruebas como push, pull, etc... para comprobar que el proceso se ha ejecutado correctamente, pero este comando te indicará directamente que **tu repo local está vinculado con el repo remoto que acabas de clonar**.

<br>

[🔝](#-visual-studio-code-en-linux-mint)
<br>
<br>

