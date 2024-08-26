![personalizacion_linux_mint](../img/bannerConfigLinux.png)

# ⚙ CONFIGURACIONES BÁSICAS DE LINUX MINT

<details>
   <summary>⚙ Índice de configuraciones</summary>
   <br>
   
   - [Activar bloq num al inicio](#-activar-bloq-num-al-inicio)
   
   <br>
</details>

<br>

↩️ [Volver al README](../README.md)

<br>

## ⚙ Activar bloq num al inicio

Por seguridad, una vez instalas Linux en tu ordenador, el ***bloq num*** está desactivado por defecto, por lo que no puedes usar el *numpad* para introducir números en la contraseña.

Para resolver esto, sigue los siguientes pasos.

1) Comprueba si tienes instalada la aplicación **numlockx**
   Abre una terminal y ejecuta:
   ~~~
   numlockx -v
   ~~~
   Si la aplicación está instalada, verás algo así:

   `NumLockX 1.2`

3) Si no está instalada, ejecuta lo siguiente:

   ~~~
   sudo apt-get install numlockx
   ~~~
4) Abre una aplicación llamada **Ventana de inicio de sesión** (pedirá contraseña)
5) En esta aplicación ve a *Configuración*
6) Activa la opción de *Activar el teclado numérico*

[🔝](#-configuraciones-básicas-de-linux-mint)
<br>
<br>
