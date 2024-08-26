![laravel_en_linux](../img/bannerLaravel.png)

<br>

# 🏗 LARAVEL EN LINUX MINT

<br>

## 📖 Tabla de contenidos

<details>
<summary>Mostrar contenidos</summary>
<br>

- [Introducción](#-introducción)
- [Instalación del instalador de Laravel](#-instalación-del-instalador-de-laravel)
- [Cómo crear un proyecto Laravel mediante el instalador](#-cómo-crear-un-proyecto-laravel-mediante-el-instalador)
- [Cómo crear un proyecto Laravel mediante el comando de Composer](#-cómo-crear-un-proyecto-laravel-mediante-el-comando-de-composer)
- [Ejecución de un proyecto Laravel](#-ejecución-de-un-proyecto-laravel)
   
</details>
<br>

↩️ [Volver al README](../README.md)

<br>

## 📋 Introducción

La creación de nuevos proyectos Laravel se puede hacer de dos formas:

1. Con el [Instalador de Laravel](#-cómo-crear-un-proyecto-laravel-mediante-el-instalador), en cuyo caso **SIEMPRE** se creará el proyecto con la **ÚLTIMA versión** de Laravel disponible.
    
2. Manualmente, mediante un [comando específico de Composer](#-cómo-crear-un-proyecto-laravel-mediante-el-comando-de-composer), en cuyo sí **podemos especificar la versión de Laravel** que queremos, que no tiene por qué ser la última.

Se pueden utilizar indistintamente ambas opciones, pero la primera requiere algún paso adicional, que especificaré en estas instrucciones.

Doy por hecho que al tener instalado Xampp, ya dispones de un servidor web (aunque Laravel incorpora uno propio) y un servidor de base de datos.

Además, dado que la **instalación de Composer necesita que tengas una instalación de PHP** en tu ordenador, usaremos la de Xampp.

Se recomienda usar una versión de PHP diferente a la de Xampp, pero dado que ya tenemos esa, es la que usaremos.

En cualquier caso, es **IMPRESCINDIBLE tener instalado COMPOSER para utilizar LARAVEL**.

<br>

[🔝](#-laravel-en-linux-mint)
<br>
<br>

## 🛠 Instalación del instalador de Laravel

>[!NOTE]
>La instalación del instalador de Laravel es algo **opcional**. Sólo es necesario si quieres tener disponible esta opción para crear tus proyectos Laravel.

1) Asegúrate de que tienes instalado Composer, ejecutando en la Terminal:
   
   ~~~
   composer --version
   ~~~

   Deberías obtener un resultado como éste:

   `Composer version 2.6.6 2023-12-08 18:32:26`

2) Realiza una actualización previa de paquetes

   Abre una Terminal, y ejecuta:
   ~~~
   sudo apt update
   ~~~
   Y si existen actualizaciones, instálalas ejecutando:
   ~~~
   sudo apt upgrade
   ~~~
   
3) Instala el "Instalador" de Laravel ejecutando, en cualquier ubicación en la Terminal:
    
   ~~~
   composer global require laravel/installer
   ~~~

   Este comando lo puedes ejecutar en cualquier ubicación, puesto que se ejecuta a nivel **global**.

4) Agrega el directorio de binarios globales de Composer al PATH, ejecutando los siguientes pasos:

    - entra en la carpeta de tu usuario
    - muestra los archivos ocultos
    - abre el archivo ***.bashrc*** con cualquier editor de texto
    - agrega esto al final del archivo:
        ~~~
        # Añadir directorio de binarios globales de Composer al PATH
        export PATH="$HOME/.config/composer/vendor/bin:$PATH"  (esta ruta difiere respecto de algunos tutoriales de internet)
        ~~~
    - finalmente, aplica los cambios en el archivo ***.bashrc***, ejecutando en la terminal:
      ~~~
      source ~/.bashrc
      ~~~

5) Comprueba la instalación del instalador de Laravel ejecutando en la Terminal:

   ~~~
   laravel --version
   ~~~

   Deberás obtener una salida similar a ésto:
   
   `Laravel Installer 5.2.0`

<br>

Si has ejecutado los pasos correctamente pero aún así no se reconoce la instalación, reinicia el sistema antes de buscar otros errores.

<br>

[🔝](#-laravel-en-linux-mint)
<br>
<br>

## 👷 Cómo crear un proyecto Laravel mediante el instalador

**Esta opción SIEMPRE instala la ULTIMA versión de Laravel**.

En una Terminal, ejecuta:

~~~
laravel new mi_proyecto
~~~

<br>

[🔝](#-laravel-en-linux-mint)
<br>
<br>

## 👷 Cómo crear un proyecto Laravel mediante el comando de Composer

**Con esta opción podemos indicar la versión de Laravel que queremos utilizar**.

En una Terminal, ejecuta:

~~~
composer create-project --prefer-dist laravel/laravel:10.* mi_proyecto
~~~

Donde 10.* es la versión que queremos instalar, y que podemos cambiar por la versión que prefiramos.

<br>

[🔝](#-laravel-en-linux-mint)
<br>
<br>

## ▶ Ejecución de un proyecto Laravel

Una vez creado el proyecto, abre una Terminal y entra dentro de la carpeta raíz del proyecto que acabas de crear.

Ejecuta:

~~~
php artisan serve
~~~

Ahora podrás acceder a la aplicación Laravel visitando **http://localhost:8000** en el navegador.

>[!IMPORTANT]
>
>Como Laravel incorpora un servidor propio, que se "pone en marcha" al ejecutar el comando *php artisan serve*, no necesitas ejecutar el servidor Apache incluido en Xampp, aunque probablemente sí necesitarás tener Xampp encendido para tener operativo el servidor de base de datos (a no ser que éste lo ejecutaras de forma independiente).

<br>

[🔝](#-laravel-en-linux-mint)
<br>
<br>
