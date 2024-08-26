![docker_en_linux](../img/bannerDocker.png)

<br>

# 🌟 DOCKER EN LINUX MINT

>[!WARNING]
>
>Existe una gran diferencia en la manera de utilizar Docker en Windows respecto a Linux.
>
>Docker es una tecnología basada en Linux y por tanto, para "correr" Docker en Windows es necesario que éste disponga de algún tipo de "adaptador" como **WSL2**, que consume valiosos recursos del sistema.
>
>Además, Windows necesita una especie de "intérprete" llamado **Docker Desktop**, que igualmente consume bastante memoria, aunque es una interfaz gráfica que permite un manejo de Docker bastante intuitivo.
>
>En cambio, en un sistema Linux, todo esto no es necesario, por lo que el ahorro de recursos es bastante notable, y aunque existen opciones gráficas para manejar Docker, yo recomiendo acostumbrarse a utilizar sólo la Terminal, porque así se ahorran recursos.
>
>En esta guía no explico ninguna interfaz gráfica para utilizar Docker en Linux, sino que me limito a la instalación de Docker y muestro algún comando básico.


## 📖 Tabla de contenidos
<br>
<details>
<summary>Mostrar contenidos</summary>
<br>
   
   - [Instalación de Docker en Linux](#-instalación-de-docker-en-linux)
   - [Ejecutar Docker como no-root](#-ejecutar-docker-como-no-root)
   - [Probar Docker](#-probar-docker)
   - [Comandos básicos de Docker](#-comandos-básicos-de-docker)
      
</details>
<br>

<br>

↩️ [Volver al README](../README.md)

<br>

## 🛠 Instalación de Docker en Linux

1) Actualiza los repositorios si aún no lo has hecho, ejecutando:

   ~~~
   sudo apt update
   sudo apt upgrade
   ~~~

2) Instala las dependencias necesarias.

   Docker necesita algunas dependencias para funcionar correctamente. Para ello, abre una Terminal y ejecuta:
   
   ~~~
   sudo apt install apt-transport-https ca-certificates curl software-properties-common
   ~~~

3) Agrega la clave GPG de Docker para verificar la autenticidad del repositorio de Docker, ejecutando en la Terminal:

   ~~~
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
   ~~~

4) Agrega el repositorio de Docker ejecutando en la terminal:

   ~~~
   echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   ~~~

5) La distribución de Linux Mint que estoy utilizando no tiene un nombre de código directo en el repositorio de Docker. Linux Mint se basa en Ubuntu, y el nombre de código "virginia" no es reconocido por el repositorio de Docker.

   Para solucionar esto, se puede especificar el nombre de código de la versión de Ubuntu en la que se basa tu versión de Linux Mint. Linux Mint 21.3 "Victoria" se basa en Ubuntu 22.04 LTS "Jammy".

   Abre el archivo ***docker.list*** para editarlo ejecutando en una Terminal:

   ~~~
   sudo nano /etc/apt/sources.list.d/docker.list
   ~~~

   Cambia el contenido del archivo para que se vea así:

   ~~~
   deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu jammy stable
   ~~~
   
   Guarda el archivo (Ctrl+O), y luego sal del editor *nano* (Ctrl+X).

6) Actualiza el índice de paquetes ejecutando:

   ~~~
   sudo apt update
   ~~~

7) Instala Docker ejecutando:

   ~~~
   sudo apt install docker-ce docker-ce-cli containerd.io
   ~~~

8) Verifica la instalación ejecutando:

   ~~~
   docker --version
   ~~~

   Deberías ver algo como esto `Docker version 27.0.3, build 7d4bcd8`
 
<br>

[🔝](#-docker-en-linux-mint)
<br>
<br>

## 🔓 Ejecutar Docker como no-root

Este paso es opcional, pero si no lo haces, cada vez que ejecutes un comando Docker deberás añadir "sudo".

Para evitar esto, puedes configurar Docker para que se ejecute como no-root (añadir tu usuario al grupo docker para poder ejecutar Docker sin necesidad de usar sudo)

Abre una Terminal y ejecuta:

~~~
sudo usermod -aG docker $USER
~~~

Finalmente, cierra la sesión en Linux y vuelve a iniciarla para que los cambios surtan efecto.

<br>

[🔝](#-docker-en-linux-mint)
<br>
<br>

## ▶ Probar Docker

Para probar el correcto funcionamiento de Docker, puedes ejecutar un contenedor de prueba.

Ejecuta:

~~~
docker run hello-world
~~~

<br>

[🔝](#-docker-en-linux-mint)
<br>
<br>

## ⌨ Comandos básicos de Docker

>[!IMPORTANT]
>
>Cuando se instala Docker, por defecto está configurado para que se inicie automáticamente al iniciar el ordenador, por lo que esto se puede deshabilitar y volver a habilitar si se desea.
>
>Aunque se desactivE el inicio automático, Docker es capaz de iniciarse de forma automática en el momento el que se teclee cualquier comando de Docker. Esto es muy útil porque no es necesario iniciarlo expresamente, aunque sí de debe parar, porque no se para solo.
>
>En Linux, como no es necesario Docker Desktop (como en Windows), no es necesaria una interfaz gráfica, y por tanto, puede ser difícil encontrar/instalar una interfaz gráfica que no consuma demasiados recursos, por lo que recomiendo acostumbrarse a utilizar Docker diréctamente desde la terminal (gracias a docker.socket).


### Comandos de control

* Deshabilitar inicio automático
    
    ~~~
    sudo systemctl disable docker
    ~~~

* Habilitar inicio automático
    
    ~~~
    sudo systemctl disable docker
    ~~~
    
* Consultar el estado de Docker (para saber si está corriendo o no)
    ~~~
    systemctl status docker
    ~~~

* Iniciar Docker
    ~~~
    sudo systemctl start docker
    ~~~
    
* Parar Docker (este comando devolverá una advertencia, pero sólo para avisar de que Docker puede iniciarse sólo al detectar cualquier comando Docker)
    
    ~~~
    sudo systemctl stop docker
    ~~~
    
* Reiniciar Docker
    
    ~~~
    sudo systemctl restart docker
    ~~~
    
### Comandos de consulta (contenedores, imágenes, volúmenes y networks)

* Consultar contenedores en ejecución
    
    ~~~
    docker ps
    ~~~
    
* Consultar todos los contenedores existentes (en ejecución y detenidos)
    
    ~~~
    docker ps -a
    ~~~
    
* Consultar las imágenes existentes
    
    ~~~
    docker images
    ~~~
    
* Consultar los volúmenes existentes
    
    ~~~
    docker volume ls
    ~~~
    
* Consultar las networks existentes
    
    ~~~
    docker network ls
    ~~~

### Comandos de borrado (contenedores, imágenes, volúmenes y networks)

* Borrar un contenedor concreto
      
    ~~~
    docker rm nombre_del_contenedor ó docker rm id_del_contenedor
    ~~~
    
* Borrar una imagen concreta
    
    ~~~
    docker rmi nombre_del_la_imagen ó docker rmi id_de_la_imagen
    ~~~
    
* Borrar un volumen concreto
    
    ~~~
    docker volume rm nombre_del_volumen ó docker volume rm id_del_volumen
    ~~~
    
* Borrar una network concreta
    
    ~~~
    docker network rm nombre_de_la_network ó docker network rm id_de_la_network
    ~~~

<br>

[🔝](#-docker-en-linux-mint)
<br>
<br>
