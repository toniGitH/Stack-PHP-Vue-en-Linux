![composer_en_linux](../img/bannerComposer.png)

<br>

# 👐 COMPOSER EN LINUX MINT

>[!WARNING]
>
>Composer es un gestor de dependencias de PHP, por lo que necesita "encontrar" la versión de PHP en nuestro ordenador.
>
>Estas instrucciones están creadas para que Composer "encuentre" la versión de PHP que viene con la instalación de XAMPP.

<br>

↩️ [Volver al README](../README.md)

<br>

## ⚒ Instalación de Composer en Linux

1) Realiza una actualización previa de paquetes

   Abre una Terminal, y ejecuta:
   ~~~
   sudo apt update
   ~~~
   Y si existen actualizaciones, instálalas ejecutando:
   ~~~
   sudo apt upgrade
   ~~~

2) Abre una Terminal y ejecuta:

   ~~~
   curl -sS https://getcomposer.org/installer | /opt/lampp/bin/php
   ~~~

   Con esto especificamos la ruta a la versión PHP de Xampp.

3) Después, ejecuta:

   ~~~
   sudo mv composer.phar /usr/local/bin/composer
   ~~~

4) Y finalmente, ejecuta:
   ~~~
   chmod +x /usr/local/bin/composer
   ~~~

5) Crea un enlace simbólico a la "verdadera" ubicación del PHP que queremos usar, que es el de Xampp.

   >⚠️ **ATENCIÓN**
   >
   >**Este paso es imprescindible si quieres que Composer use la versión de PHP que hay en Xampp**.
   >
   >Composer espera encontrar un ejecutable de PHP en una ubicación estándar del sistema (generalmente en el PATH, como */usr/local/bin/php*).
   >
   >Sin embargo, en este caso, el ejecutable de PHP que vas a utilizar (php-8.2.4 de Xampp) está en una ubicación específica (***/opt/lampp/bin/php-8.2.4***) que **no está incluida en el PATH por defecto**.
   >
   >Al crear un **enlace simbólico** en ***/usr/local/bin/php*** que **apunta directamente al ejecutable real de PHP** en ***/opt/lampp/bin/php-8.2.4***, estamos creando un "puente" que permite que **cuando Composer o cualquier otro programa busque php en /usr/local/bin**, **encuentre el enlace simbólico y lo siga hasta la ubicación real del ejecutable de PHP** que deseas utilizar.

   Para crear este enlace simbólico debes abrir una Terminal y ejecutar:
   
   ~~~
   sudo ln -s /opt/lampp/bin/php-8.2.4 /usr/local/bin/php
   ~~~

6) Verifica la instalación de Composer ejecutando en la Terminal:

   ~~~
   composer --version
   ~~~

<br>
   
Con estos pasos ya tienes completada la instalación de Composer, y ya puedes proceder, si quieres, a crear tus proyectos con Laravel, ya sea utilizando el instalador de Laravel o mediante el comando de Composer que existe para tal efecto.

Puedes acceder al contenido de esta guía relacionado con Laravel en [este enlace](/Stack%20principal/06-Laravel.md).

<br>

[🔝](#-composer-en-linux-mint)
<br>
<br>
