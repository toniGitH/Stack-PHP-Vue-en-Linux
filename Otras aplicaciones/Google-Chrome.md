![instalación_google_chrome_en_Linux_Mint](../img/bannerChrome.png)

# ⚒️ INSTALACIÓN DE GOOGLE CHROME EN LINUX MINT

## ✔️ Instalación

1. Descarga la última [última versión de Chrome](https://www.google.com/intl/es_es/chrome/?_gl=1*5wdtyh*_up*MQ..&gclid=Cj0KCQjw-uK0BhC0ARIsANQtgGOjfbyuVJO4cOnamoTe48JZ56y0p25P489FH3P9sGYk3Tj8stDjEGkaAmDSEALw_wcB&gclsrc=aw.ds) desde su página oficial.

3. Abre una terminal y sitúate en la carpeta de Descargas (o en la que esté el archivo que hemos descargado).

4. Concede permisos de lectura al archivo que acabas de descargar, ejecutando en la terminal, **dentro** de la carpeta Descargas (o la que corresponda):
~~~
chmod +r ~/Descargas/google-chrome-stable_current_amd64.deb
~~~
4. Ejecuta la instalación: en la terminal, dentro de la carpeta Descargas (o la que corresponda), ejecuta esta instrucción:
~~~
sudo apt install ./google-chrome-stable_current_amd64.deb
~~~

## ❌ Desinstalación

Primero, ejecuta:
~~~
sudo apt remove google-chrome-stable
~~~
y después, ejecuta:
~~~
sudo apt purge google-chrome-stable
~~~

<br>

↩️ [Volver al README](../README.md)

<br>
