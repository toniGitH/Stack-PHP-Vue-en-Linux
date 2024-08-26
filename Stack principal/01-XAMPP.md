![xampp_en_linux](../img/bannerXamppEnLM.png)

<br>

# ⚒ INSTALACIÓN DE XAMPP EN LINUX MINT

>[!IMPORTANT]
>
>A diferencia de Windows, al instalar XAMPP en Linux no se genera automáticamente ningún acceso directo a esta aplicación.
>
>La ejecución de XAMPP en Linux se hace, por defecto, a través de la Terminal.
>
>Sin embargo, en Linux es posible crear lanzadores que se pueden colocar en cualquier parte (menú, escritorio, etc...), y en estas instrucciones también indico cómo hacerlo para crear un acceso directo a Xampp.

<br>

## 📖 Tabla de contenidos

<details>
<summary>Mostrar contenidos</summary>
<br>

- [Instalación](#-instalación)
- [Conceder permisos a la carpeta htdocs](#-conceder-permisos-a-la-carpeta-htdocs)
- [Ejecución de XAMPP desde la Terminal](#-ejecución-de-xampp-desde-la-terminal)
- [Crear un acceso directo a Xampp](#-crear-un-acceso-directo-a-xampp)
- [Crear un acceso directo a la carpeta htdocs](#-crear-un-acceso-directo-a-la-carpeta-htdocs)
- [Borrar una categoría personalizada creada en el menú principal](#-borrar-una-categoría-personalizada-creada-en-el-menú-principal).
   
</details>
<br>

↩️ [Volver al README](../README.md)

<br>

## ⚒ Instalación

1) Abre una Terminal y actualiza paquetes, ejecutando:
   ~~~
   sudo apt update
   ~~~
   Y si existen actualizaciones, instálalas ejecutando:
   ~~~
   sudo apt upgrade
   ~~~
   
2) Accede a la [web de XAMPP](https://www.apachefriends.org/es/download.html) y descarga la versión deseada (doy por sentado que se descargará en la carpeta Descargas o Downloads).
3) Haz que el archivo que acabas de descargar sea ejecutable.
  Abre una Terminal y sitúate dentro de la carpeta Descargas (o Downloads) y ejecuta:

   ~~~
   chmod +x xampp-linux-x64-8.2.4-0-installer.run
   ~~~
   
   *Si descargas una versión diferente de XAMPP (por ejemplo, la versión 7.2.9), reemplaza "8.2.4" con el número de tu versión de XAMPP.*

4) En la Terminal, dentro de la carpeta Descargas (o Downloads), ejecuta el comando de instalación:
   ~~~
   sudo ./xampp-linux-x64-8.2.4-0-installer.run
   ~~~
   
5) Sigue las instrucciones de instalación (igual que en Windows)

<br>

**IMPORTANTE:** una vez acabada la instalación, es necesario dar los permisos oportunos a la carpeta **htdocs** para que el usuario propietario pueda crear carpetas de proyectos, etc...

<br>

[🔝](#-instalación-de-xampp-en-linux-mint)
<br>
<br>

## 🔑 Conceder permisos a la carpeta htdocs

1) Cambia el propietario de la carpeta htdocs al usuario actual (por ejemplo, *tu_usuario*)

   Para ello, abre una Terminal y ejecuta:

   ~~~
   sudo chown -R tu_usuario:tu_usuario /opt/lampp/htdocs
   ~~~
   Esto hará que *tu_usuario* sea el propietario de la carpeta htdocs y todos sus subdirectorios y archivos.

2) Cambia los permisos

   Ejecuta en la Terminal:

   ~~~
   sudo chmod -R 755 /opt/lampp/htdocs
   ~~~

   Esto asegura que el propietario (*tu_usuario*) tenga permisos completos (lectura, escritura, y ejecución), mientras que otros usuarios tendrán permisos de lectura y ejecución, pero no de escritura.

3) Verifica permisos y propietario
   
   Ejecuta en la Terminal:

   ~~~
   ls -l /opt/lampp | grep htdocs
   ~~~

   Debería devolver este resultado:

   `drwxr-xr-x 2 tu_usuario tu_usuario 4096 fecha htdocs`

   <br>
   
[🔝](#-instalación-de-xampp-en-linux-mint)
<br>
<br>

## ▶ Ejecución de XAMPP desde la Terminal

Aunque es posible crear manualmente un acceso directo a XAMPP, tras la instalación en Linux, a diferencia de Windows, no se genera automáticamente ningún acceso directo para ejecutarlo, por lo que es conveniente aprender a hacerlo directamente desde la Terminal.

1) Abre la Terminal
2) Navega hasta el directorio de XAMPP:
   ~~~
   cd /opt/lampp
   ~~~
3) Desde esa ubicación, en la Terminal, ejecuta el comando para lanzar el **manager de XAMPP**:
   ~~~
   sudo ./manager-linux-x64.run
   ~~~

>[!IMPORTANT]
>
>XAMPP se ejecuta **SIEMPRE** a través de una Terminal, por lo que no la debes cerrar mientras quieras mantener el XAMPP abierto.

<br>

[🔝](#-instalación-de-xampp-en-linux-mint)
<br>
<br>

## 📌 Crear un acceso directo a XAMPP

Para crear un acceso directo de XAMPP en Linux, dado que la instalación no genera ninguno, se tiene que hacer mediante la creación de lanzadores que ejecuten el comando de lanzamiento del manager de XAMPP.

<br>

>[!IMPORTANT]
>
>Como XAMPP necesita ejecutarse a través de una Terminal, cuando hagas click en el acceso directo (lanzador), primero se abrirá una Terminal que te pedirá la contraseña y luego se ejecutará XAMPP. **La Terminal que se abre se debe mantener abierta mientras estemos ejecutando XAMPP**.

>[!TIP]
>
>Crea un lanzador directamente en el menú principal, y cuando lo tengas, podrás añadir un acceso directo en el escritorio y/o en el panel (barra de tareas), simplemente haciendo click derecho y seleccionando la opción de *Añadir al panel* y *Añadir al escritorio*.

<br>

⭐ **Crear un acceso directo a Xampp en el menú principal**

>[!NOTE]
>
>Estas instrucciones son válidas para el caso de que hayas sustituido el menú por defecto por el ***Cinnamenu***, tal y como explico [aquí](/Personalizaci%C3%B3n%20Linux%20Mint/Personalizaciones-b%C3%A1sicas.md#-sustituir-el-men%C3%BA-principal-por-el-cinnamenu).

1) Coloca el ratón sobre el botón del menú principal y haz click derecho.
2) Selecciona *Editar menu*.
3) Si quieres crear una categoría personalizada nueva (por ejemplo, Desarrollo) donde meter este acceso directo de XAMPP, selecciona la opción de *Menú nuevo*.
4) Si en un futuro quieres borrar esa categoría personalizada, debes eliminarla siguiendo [estas instrucciones](#-borrar-una-categoría-personalizada-creada-en-el-menú-principal).
5) Una vez dentro de la nueva categoría, selecciona *Elemento nuevo* y se abrirá el menu de **Propiedades del lanzador**.
6) En este menú, debes rellenar los siguientes campos:
   
   - **Nombre:** XAMPP (nombre visible que tendrá el acceso directo)
   - **Orden:** ```sudo /opt/lampp/manager-linux-x64.run```
   - **Comentario:** opcional
   - **Icono:** ```/opt/lampp/htdocs/favicon.ico``` si quieres el que viene con la instalación de XAMPP
   - **¿Iniciar en un Terminal?:** hay que marcar que sí

<br>

⭐ **Crear un acceso directo a Xampp en el escritorio**

1) Abre el menú principal.
2) Busca el icono de la aplicación de XAMPP que acabas de crear y haz click derecho sobre él.
3) Selecciona la opción *Añadir al escritorio*.
   
<br>

⭐ **Crear un acceso directo a Xampp en el panel**

1) Abre el menú principal.
2) Busca el icono de la aplicación de XAMPP que acabas de crear y haz click derecho sobre él.
3) Selecciona la opción *Añadir al panel*.
   
<br>

⭐ **Crear un acceso directo a Xampp sólo en el escritorio**

1) Haz click derecho en el escritorio.
2) Selecciona la opción de *+Crear un lanzador nuevo aquí* y se abrirá el menu de **Propiedades del lanzador**.
3) En este menú, debes rellenar los siguientes campos:

   - **Nombre:** XAMPP (nombre visible que tendrá el acceso directo)
   - **Orden:** ```sudo /opt/lampp/manager-linux-x64.run```
   - **Comentario:** opcional
   - **Icono:** ```/opt/lampp/htdocs/favicon.ico``` si quieres el que viene con la instalación de XAMPP
   - **¿Iniciar en un Terminal?:** hay que marcar que sí
 
<br>

[🔝](#-instalación-de-xampp-en-linux-mint)
<br>
<br>

## 📂 Crear un acceso directo a la carpeta htdocs

Se crea igual que el acceso directo a Xampp (en el menú principal y/o en el escritorio), pero la orden que se debe escribir en el campo correspondiente en el menu de **Propiedades del lanzador** es esta:
**Orden:** `nemo /opt/lampp/htdocs` 

[🔝](#-instalación-de-xampp-en-linux-mint)
<br>
<br>

## ❌ Borrar una categoría personalizada creada en el menú principal

1) Primero debes obtener la ruta a ese elemento: selecciona la opción *Editar el erchivo de escritorio* y anota la dirección que aparece.
2) Navega hasta `.local/share/desktop-directories` (está como archivo oculto dentro de la carpeta del usuario).
3) Elimina el archivo correspondiente.

<br>

[🔝](#-instalación-de-xampp-en-linux-mint)
<br>
<br>

