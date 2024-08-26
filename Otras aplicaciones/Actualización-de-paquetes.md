![actualización_de_paquetes_en_Linux](../img/bannerSudoUpdate.png)

# ⚒ ACTUALIZACIÓN DE PAQUETES EN LINUX

>[!TIP]
>
>Mantener la lista de paquetes actualizada es importante porque aseguras que tu sistema tenga información sobre las últimas actualizaciones de seguridad y mejoras de software.
>
>Antes de instalar una nueva aplicación en Linux, te recomiendo ejecutar esta actualización.

<br>

↩️ [Volver al README](../README.md)

<br>

## ⭐ INSTALAR APLICACIONES EN LINUX

En Linux existen **varias formas diferentes de instalar aplicaciones**, en las que no voy a entrar, pero sí podría decirse que se agrupan en estos 4 tipos:
- **instalación "automatizada" mediante gestores de paquetes** de las diferentes distribuciones, como YUM (Red Hat, Fedora y CentOs), Pacman (Arch Linux), APT (Ubuntu, DEbian), etc...
- **instalación "manual" de paquetes de distribuciones específicas**, como los DEB (Debian) o los RPM(Red Hat) 
- **instalación de paquetes universales**, como Flatpack, AppImage y Snap, válidos prácticamente para cualquier distribución de Linux
- **compilación desde el código fuente**

<br>

## ⭐ EL GESTOR DE PAQUETES APT

Dado que este repositorio está centrado en la configuración de un stack de PHP-Vue en una distribución Linux Mint, me limitaré a señalar los aspectos más relevantes del gestor de paquetes más común de esta distribución, que es APT, que es el que se utiliza mayoritariamente en las instalaciones explicadas en este repositorio.

<br>

## ⭐ EL COMANDO SUDO APT UPDATE

Cuando queremos instalar una aplicación en nuestro ordenador, y decidimos que lo haremos mediante el gestor de paquetes APT, lo primero que deberíamos hacer es ejecutar el siguiente comando:

~~~
sudo apt update
~~~

Este comando se utiliza en sistemas basados en Debian y Ubuntu para **actualizar la lista de paquetes disponibles y descarga información sobre las versiones más recientes de los paquetes desde los repositorios configurados en tu sistema**.

Los repositorios son ubicaciones donde se almacenan los paquetes de software.

Sin embargo, es importante tener en cuenta que **este comando no actualiza las aplicaciones en sí**, sino que solo actualiza la lista de paquetes.

Después de ejecutar este comando, normalmente verás una lista de los repositorios que se han actualizado y un resumen del número de paquetes que se pueden actualizar.

<br>

## ⭐ EL COMANDO SUDO APT UPGRADE

Una vez que ya tenemos la información sobre las versiones más recientes de los paquetes, ya podemos actualizar aquellos paquetes instalados que tengan alguna actualización, ejecutando:

~~~
sudo apt upgrade
~~~

<br>

[🔝](#-actualización-de-paquetes-en-linux)
<br>
<br>
