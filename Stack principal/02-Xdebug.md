![xdebug_en_linux](../img/bannerXdebugEnLM.png)

<br>

# ⚒ INSTALACIÓN DE XDEBUG EN LINUX MINT

>[!CAUTION]
>
>En estas instrucciones vamos a instalar XDEBUG, pero **UTILIZANDO LA INSTALACIÓN DE PHP QUE VIENE CON XAMPP**.
>
>Estas instrucciones **NO SON LAS MISMAS** que las de la página oficial de Xdebug.
>
>El proceso es muy similar, pero **CAMBIAN COSAS IMPORTANTES** porque **en la página oficial se asume que usamos la versión PHP del sistema**, pero nosotros queremos usar la versión PHP de Xdebug.
>
>Si intentas seguir las instrucciones de la página oficial, pero teniendo sólo la versión PHP de Xampp, no va a funcionar.
>
>La instalación de Xdebug básicamente consiste en instalar la extensión Xdebug dentro de nuestra instalación de PHP.
>
>Por tanto, es importante entender que **si quieres utilizar la instalación de PHP que viene con XAMPP** (que es el caso que explico en estas instrucciones), **la ruta de instalación de la extensión Xdebug está DENTRO de la carpeta de Xampp**, mientras que **si quieres usar una instalación de PHP independiente de Xampp, la ruta de instalación será otra**.
>
>Por ese motivo, las instrucciones de instalación de la Pàgina oficial no funcionan para instalar la extensión Xdebug dentro de la instalación de PHP de Xampp (concretamente, es en el paso 4 de esta guía donde difiere la instalación respecto a la página oficial).

<br>

## 📖 Tabla de contenidos

<details>
<summary>Mostrar contenidos</summary>
<br>

- [Verificaciones previas](#-verificaciones-previas)
- [Instalación de Xdebug](#-instalación-de-xdebug)
- [Activación y desactivación de Xdebug](#-activación-y-desactivación-de-xdebug)
- [Actualización de Xdebug](#-actualización-de-xdebug)
- [Resumen de la instalación](#-resumen-de-la-instalación)
   
</details>
<br>

↩️ [Volver al README](../README.md)

<br>

## 📝 Verificaciones previas

<br>

⭐ **Conocer tu versión actual de PHP**

Para saber la versión de PHP que utiliza tu instalación de XAMPP, abre una Terminal y ejecuta:
~~~
/opt/lampp/bin/php -v
~~~

La salida será parecida a ésta:

>PHP 8.2.4 (cli) (built: Apr  6 2023 08:21:45) (NTS)
>
>Copyright (c) The PHP Group
>
>Zend Engine v4.2.4, Copyright (c) Zend Technologies

<br>

⭐ **Conocer la versión de Xdebug que es compatible con tu versión de PHP**

Para asegurarte de que la versión de Xdebug que quieres instalar sea compatible con la versión de PHP que tengas instalada (en este caso, es la 8.2.4), puedes recurrir a la página oficial de Xdebug para saber qué versión corresponde a nuestra versión de PHP.

Para ello, sigue los siguientes pasos:

1) Enciende Xampp, ve a localhost en el navegador, y entra en **PHPInfo**.
2) Copia **TODO** lo que te aparezca en PHPInfo (*ctrl+a* para seleccionarlo todo y luego *ctrl+c* para copiarlo).
3) En la página oficial de Xdebug, accede al [Wizard](https://xdebug.org/wizard), pega dentro del recuadro toda la información anterior y haz click en el botón de **Analizar**
4) El sistema te dirá, entre otras cosas, qué versión de Xdebug puedes usar con tu versión de PHP

<br>

[🔝](#-instalación-de-xdebug-en-linux-mint)
<br>
<br>

## 🛠 Instalación de Xdebug

1) Realiza una actualización previa de paquetes

   Abre una Terminal, y ejecuta:
   ~~~
   sudo apt update
   ~~~
   Y si existen actualizaciones, instálalas ejecutando:
   ~~~
   sudo apt upgrade
   ~~~

2) Instala las dependencias necesarias

   Asegúrate de tener las herramientas necesarias para compilar Xdebug.

   En la Terminal, ejecuta:
   ~~~
   sudo apt install build-essential autoconf automake libtool"
   ~~~
   
3) Descarga Xdebug

   Este paso consiste en descargar la versión que desees de Xdebug desde su sitio oficial (en este caso la versión 3.3.2).

   Para esta instalación, puedes utilizar, por ejemplo, la carpeta temporal para alojar el archivo comprimido que descargarás desde la página oficial.

   Este archivo debe ser descomprimido, lo que te generará (también dentro de la carpeta temporal) una carpeta llamada xdebug-3.3.2, a la que deberás moverte para continuar aquí dentro con el siguiente paso.

   Para hacer todo esto, entonces:

   -> primero, abre una Terminal y muévete a la carpeta temporal ejecutando:
   ~~~
   cd /tmp
   ~~~
   -> una vez dentro de la carpeta temporal, descarga la versión de xdebug que desees, ejecutando:
   ~~~
   wget https://xdebug.org/files/xdebug-3.3.2.tgz
   ~~~
   -> descomprime el archivo descargado, ejecutando, dentro de la carpeta temporal:
   ~~~
   tar -xvzf xdebug-3.3.2.tgz
   ~~~
   -> en la Terminal, cámbiate a la carpeta `xdebug-3.3.2` que se ha generado al descomprimir el archivo descargado, ejecutando:
   ~~~
   cd xdebug-3.3.2
   ~~~
   
4) Compila e instala Xdebug usando el PHP de XAMPP (este paso es diferente al que se realiza en las instrucciones en la página oficial de Xdebug)

   Usa las herramientas de desarrollo proporcionadas por XAMPP para compilar Xdebug.

   Asegurate de que en la Terminal que tienes abierta estás dentro de la carpeta **xdebug-3.3.2** que se creó en el paso anterior, y ejecuta las siguientes instrucciones:
   
   -> prepara el entorno de construcción de extensiones PHP ejecutando: 
   ~~~
   /opt/lampp/bin/phpize
   ~~~
   -> configura los parámetros de construcción de la extensión:
   ~~~
   ./configure --with-php-config=/opt/lampp/bin/php-config
   ~~~
   -> compila la extensión mediante el siguiente comando:
   ~~~
   make
   ~~~
   -> finalmente, instala la extensión:
   ~~~
   sudo make install
   ~~~

   Este proceso compilará Xdebug y colocará el archivo **xdebug.so** en el directorio de extensiones de tu instalación de PHP en XAMPP.

5) Encuentra la ruta exacta del archivo **xdebug.so**

   Después de la instalación, hay que encontrar la ubicación del archivo "xdebug.so".
   
   Debería estar en "/opt/lampp/lib/php/extensions", dentro de una carpeta llamada **no-debug-non-zts-20220829* (el número del final puede cambiar).

   Si todo se está instalando correctamente, deberías poder encontrar esa ruta dentro de la salida a la instrucción
   ~~~
   php -i
   ~~~
   como aparece aquí:
   >...
   >
   >expose_php => On => On
   >
   >**extension_dir => /opt/lampp/lib/php/extensions/no-debug-non-zts-20220829** => /opt/lampp/lib/php/extensions/no-debug-non-zts-20220829
   >
   >fiber.stack_size => no value => no value
   >  
   >...
   

6) Configura PHP para usar Xdebug

   Abre el archivo php.ini de XAMPP, ejecutando:
   ~~~
   sudo nano /opt/lampp/etc/php.ini
   ~~~
   Esto abrirá el archivo utilizando el editor *nano* para que puedas modificar el archivo **php.ini** para incluir unas líneas necesarias.

   Añade las siguientes líneas al final del archivo **php.ini**, teniendo en cuenta que el número 20220809 pude ser diferente en tu caso:

   ~~~
    [XDebug]
    zend_extension=/opt/lampp/lib/php/extensions/no-debug-non-zts-20220829/xdebug.so
    xdebug.mode=debug
    xdebug.start_with_request=yes
    xdebug.client_host=127.0.0.1
    xdebug.client_port=9003
    xdebug.log=/var/log/xdebug.log
   ~~~

   Una vez añadidas estas líneas, presiona `ctrl+O` para guardar el archivo, luego `intro` y luego `ctrl+X` para salir del editor.

7) Reinicia XAMPP

   Reinicia XAMPP para que los cambios surtan efecto.

8) Verifica la instalación por Terminal

   Una vez instalado y activado Xdebug, si ejecutas de nuevo la instrucción:
   
   ~~~
   /opt/lampp/bin/php -v
   ~~~
   deberías obtener algo como esto:
   
   >PHP 8.2.4 (cli) (built: Apr  6 2023 08:21:45) (NTS)
   >
   >Copyright (c) The PHP Group
   >
   >Zend Engine v4.2.4, Copyright (c) Zend Technologies
   >
   >    with Xdebug v3.3.2, Copyright (c) 2002-2023, by Derick Rethans

9) También puedes verificar la instalación a través del localhost

   Una vez instalado y activado Xdebug, accede al localhost y entra dentro de PHPInfo, y ahí deberías poder encontrar, casi al final, la extensión XDEBUG.

10) Borra el contenido innecesario de la carpeta /tmp

    Si todo se ha instalado correctamente, ya puedes borrar sin problema de la carpeta */tmp*, la carpeta comprimida que se descargó en el paso 3 y la carpeta descomprimida xdebug-3.3.2 que se generó en el paso 3.

<br>

[🔝](#-instalación-de-xdebug-en-linux-mint)
<br>
<br>

## 🔛 Activación y desactivación de Xdebug

Si tienes instalado Xdebug, pero por algún motivo, lo quieres deshabilitar, simplemente sigue estos pasos.

1) Usando la Terminal, entra dentro del archivo **php.ini** ejecutando:
   
   ~~~
   sudo nano /opt/lampp/etc/php.ini
   ~~~
   
2) Al final del archivo encontrarás estas líneas, que incluiste al instalar Xdebug:

   ~~~
   [XDebug]
   zend_extension=/opt/lampp/lib/php/extensions/no-debug-non-zts-20220829/xdebug.so
   xdebug.mode=debug
   xdebug.start_with_request=yes
   xdebug.client_host=127.0.0.1
   xdebug.client_port=9003
   xdebug.log=/var/log/xdebug.log
   ~~~

3) Ahora basta con comentar la línea que "activa" la extensión poniendo un punto y coma ";" delante de esa línea:
   ~~~
   ;zend_extension=/opt/lampp/lib/php/extensions/no-debug-non-zts-20220829/xdebug.so
   ~~~

   El resto de líneas se pueden dejar sin comentar.

   Y si lo que quieres es volver a activar Xdebug, simplemente elimina ese punto y coma ";"

<br>

[🔝](#-instalación-de-xdebug-en-linux-mint)
<br>
<br>

## 🔄 Actualización de Xdebug

Si lo que quieres es actualizar tu versión de Xdebug, sigue los siguientes pasos.

Supongamos que tienes instalada la versión 3.2.1 y quieres actualizar a la versión 3.3.2.

Para actualizar a la última versión de Xdebug (en este caso, la 3.3.2) desde una versión anterior (como la 3.2.1), generalmente puedes seguir un proceso similar al de la instalación inicial, pero teniendo en cuenta algunos pasos adicionales para asegurarte de que la actualización se realice correctamente.

1) Realiza una actualización previa de paquetes

   Abre una Terminal, y ejecuta:
   ~~~
   sudo apt update
   ~~~
   Y si existen actualizaciones, instálalas ejecutando:
   ~~~
   sudo apt upgrade
   ~~~

2) Muévete a la carpeta temporal, ejecutando:
   ~~~
   cd /tmp
   ~~~
3) Descarga la nueva versión:

   Desde la Terminal puedes descargar el archivo de la nueva versión de Xdebug que necesites, ejecutando, dentro de la carpeta temporal:

   ~~~
   wget https://xdebug.org/files/xdebug-3.3.2.tgz
   ~~~
   
4) Descomprime el archivo ejecutando, dentro de la carpeta tmp:
   ~~~
   tar -xzf xdebug-3.3.2.tgz"
   ~~~
5) Muévete a la carpeta resultante, que en este caso es **xdebug-3.3.2** ejecutando:
   ~~~
   cd xdebug-3.3.2
   ~~~
6) Prepara el entorno de construcción de extensiones PHP ejecutando: 
   ~~~
   /opt/lampp/bin/phpize
   ~~~
7) Configura los parámetros de construcción de la extensión:
   ~~~
   ./configure --with-php-config=/opt/lampp/bin/php-config
   ~~~
8) Compila la extensión mediante el siguiente comando:
   ~~~
   make
   ~~~
9) Finalmente, instala la extensión:
   ~~~
   sudo make install
   ~~~
10) Si es necesario, actualiza la configuración en **php.ini**.

    Este paso podría no ser necesario si el nuevo archivo de extensión ha reemplazado al anterior y no cambia ningún nombre.

    En caso contrario, abre */opt/lampp/etc/php.ini* en un editor de texto ejecutando:

    ~~~
    nano /opt/lampp/etc/php.ini
    ~~~

    y actualiza la línea **zend_extension** para apuntar a la nueva versión de **xdebug.so** que acabas de compilar.

    La ruta podría cambiar dependiendo de la versión y la estructura de la instalación, así que asegúrate de verificar la ruta correcta.

12) Reinicia Xampp

13) Verifica la nueva versión de Xdebug

14) Si todo ha ido correctamente, ya puedes borrar el archivo descargado y el archivo descomprimido en /temp al inicio del proceso.

<br>

[🔝](#-instalación-de-xdebug-en-linux-mint)
<br>
<br>

## 📃 Resumen de la instalación

Por si no se ha entendio bien lo que supone la instalación de Xdebug en PHP y sus implicaciones, este es un resumen meramente conceptual del proceso.

1) Descarga la versión de xdebug (en este caso, es la 3.3.2) en formato comprimido.
2) Descomprime el archivo, lo que genera una carpeta llamada xdebug-3.3.2.
3) Muévete a esa carpeta xdebug-3.3.2.
4) Dentro de esa carpeta xdebug-3.3.2, ejecuta */opt/lampp/bin/phpize*, sólo para preparar el entorno de construcción y generar los scripts configure y makefile dentro de la carpeta xdebug-3.3.2.
5) Dentro de la carpeta xdebug-3.3.2 ejecuta *make* para compilar y *sudo make install* para instalar la extensión Xdebug en la instalación de PHP en XAMPP (es decir, que se instala la extensión Xdebug dentro de la instalación de PHP de Xampp, no en la carpeta xdebug-3.3.2).
6) Ahora ya está incluida la extensión de Xdebug en tu instalación de PHP de Xampp, pero no esta, digamos, activada.
7) Activa la extensión entrando en */opt/lampp/etc/php.ini* y añadiendo *zend_extension = /opt/lampp/lib/php/extensions/no-debug-non-zts-xxxxxxx/xdebug.so*
8) Ahora puedes borrar sin problema la carpeta comprimida que se descargó en el paso 1 y la carpeta descomprimida xdebug-3.3.2

<br>

[🔝](#-instalación-de-xdebug-en-linux-mint)
<br>
<br>

