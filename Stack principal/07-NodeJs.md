![nodejs_en_linux](../img/bannerNodejs.png)

<br>

# 🟢 NODE.JS EN LINUX MINT

En esta sección detallo los pasos para instalar Node.js, pero utilizando **nvm**, que es un **gestor de versiones de Node**, que nos premitirá tener instaladas diferentes versiones de Node.js y seleccionar en cada momento la versión que queramos.

El gestor de paquetes de Node.js, llamado **npm**, se instala automáticamente al instalar Node.js.

<br>

## 📖 Tabla de contenidos

<details>
<summary>Mostrar contenidos</summary>
<br>

- [Instalación de NVM](#-instalación-de-nvm)
- [Instalación de Node.JS con NVM](#-instalación-de-nodejs-con-nvm)
- [Comandos de NVM](#-comandos-de-nvm)
- [Comprobación de funcionamiento de NodeJs](#-comprobación-de-funcionamiento-de-nodejs)
   
</details>
<br>

↩️ [Volver al README](../README.md)

<br>

## 🛠 Instalación de nvm

Para instalar el gestor de versiones de Node, debes seguir estos pasos.

1) Realiza una actualización previa de paquetes.

   Abre una Terminal, y ejecuta:
   ~~~
   sudo apt update
   ~~~
   Y si existen actualizaciones, instálalas ejecutando:
   ~~~
   sudo apt upgrade
   ~~~

2) Descarga e instala de NVM, ejecutando en una Terminal:

   ~~~
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
   ~~~

   o, alternativamente:

   ~~~
   wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
   ~~~

   Cualquiera de los dos métodos es válido.
   
   Para instalar la versión más reciente, sustituye el ***v0.39.7*** por la ultima versión que aparezca en el [repositorio oficial de NVM](https://github.com/nvm-sh/nvm)
   
   Este paso anota automáticamente en el archivo .bashrc las variables de entorno correspondientes, por lo que no es necesario hacerlo manualmente.

3) Cierra la terminal para cargar las variables de entorno de NVM.

4) Verifica la instalación de NVM.

   Para verificar que NVM se ha instalado correctamente, abre una Terminal y ejecuta:

   ~~~
   command -v nvm
   ~~~
   
   Y debería devolver un resultado como este:
   
   `nvm`
   
   Y también puedes ejecutar:

   ~~~
   nvm --version
   ~~~
   
   Y debería devolver un resultado como este:
   
   `0.39.7`

<br>

[🔝](#-nodejs-en-linux-mint)
<br>
<br>

## 🛠 Instalación de Node.JS con nvm

1) Realiza una actualización de paquetes si no lo has hecho aún.
   
2) Lista las opciones disponibles de Node.js en el repositorio oficial, ejecutando en una Terminal:

   ~~~
   nvm ls-remote
   ~~~

2) Instala, por ejemplo, la última versión de Node.js, ejecutando en la Terminal:

   ~~~
   nvm install --lts
   ~~~

   Para instalar otra versión específica, ejecuta en su lugar:

   ~~~
   nvm install 14.17.0
   ~~~

   O la versión que prefieras.

   
3) Si quieres, puedes listar las versiones disponibles en tu equipo, ejecutando:

   ~~~
   nvm ls
   ~~~

4) Establece una versión concreta de las que tienes instaladas, como predeterminada.

   Para la última versión LTS que tengas instalada, ejecuta:
   
   ~~~
   nvm use --lts"
   ~~~
   
   Para establecer cualquier otra versión de las que tengas instaladas, ejecuta:
   ~~~
   nvm use 14.17.0
   ~~~
   
   O la versión que prefieras, de las que tengas instaladas.

6) Verifica la instalación de Node.js, ejecutando en la Terminal:

   ~~~
   node -v
   ~~~

   Esto debería mostrar la versión de Node.js que acabas de instalar y seleccionar.


<br>

[🔝](#-nodejs-en-linux-mint)
<br>
<br>

## ⌨ Comandos de nvm

Algunos comandos útiles de **nvm**.

* Cambiar de versión:
  ~~~
  nvm use 14.17.0
  ~~~

* Desinstalar una versión:
~~~
nvm uninstall 14.17.0
~~~

* Listar las versiones instaladas en el ordenador:
~~~
nvm ls
~~~

* Listar las versiones disponibles en el repositorio oficial: 
~~~
nvm ls-remote
~~~
<br>

[🔝](#-nodejs-en-linux-mint)
<br>
<br>

## ✔ Comprobación de funcionamiento de Node.Js

Para verificar que Node.js esté funcionando correctamente, puedes crear un ejemplo simple de "Hola, Mundo".

1) Crea un nuevo archivo llamado, por ejemplo, *hello.js*

2) Agrega el siguiente código a ese archivo:

   ~~~
   console.log("¡Hola, Mundo!");
   ~~~
   
3) Ejecuta el código usando Node.js

   En una Terminal, navega hasta el directorio donde creaste ese archivo *hello.js* y ejecuta:

   ~~~
   node hello.js
   ~~~

   Deberías ver como salida el `¡Hola, Mundo!`

<br>

[🔝](#-nodejs-en-linux-mint)
<br>
<br>
