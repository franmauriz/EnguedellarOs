---
date: 2020-09-10T07:40:36+02:00
author: Francisco Mauriz Pereira
title: 'Istalando KDE Neon'
categories: [Linux,instalacion]
tags: [Linux, instalación,empezando]
draft: false
---

# Nuestra primera instalación con Kde Neon.

![Kde Neon](/images/kde_neon01.jpg)

## ¡¡Vamos a instalar nuestra primera distribución GNU/Linux!!

En otros post de **EnguedellarOS** ya he explicado como crear un USB de instalación y las consideraciones que debemos tener  con la partición *UEFI*.

En este articulo explicare los pasos necesarios para instalar la distro [KDE Neon](https://neon.kde.org/index). Entre todas las distros GNU/Linux que existen escogí **KDE Neon** entre estas razones:

1. Esta basada en Ubuntu 20.04 LTS una versión estable de largo plazo.
2. Como entorno de trabajo, evidentemente, usa **Plasma Desktp** en su version más actual que es el escritorio creado por KDE. Para los iniciados en GNU/Linux que están acostumbrados al escritorio de Windows, el cambio entre uno y otro será más sencillo y de una forma más natural.
3. Viene con las aplicaciones de KDE ya preinstaladas con lo que desde el primer inicio ya podremos ponernos a trabajar, navegar por internet y ver nuestros videos.
4. Por la gran comunidad de KDE que existe en internet, que crea una gran multitud de documentación y la comparte libremente para dar soporte a los usuarios que puedan tener un problema o quieran profundizar más en el mundo GNU/Linux.
5. Aunque al principio puede asustar, también una de sus grandes ventajas frente a otros escritorios es que Plasma es altamente configurable dejándonos cambiar las ventanas, los iconos, los paneles, los menús , etc.
6. Los requisitos mínimos del sistema requieren:
   1. 64-bit PC (Intel or AMD).
   2. 2GB memoria.
   3. 10GB espacio en disco.

Una vez que ya hemos creado el USB con la imagen de KDE Neon que puedes descargar desde [aquí](https://neon.kde.org/download) solo tenemos que conectar el USB a nuestro equipo, pero antes debemos de asegurarnos de dos configuraciones en la BIOS.

- ¿El UEFI esta activado o desactivado? sino lo esta recomiendo activarlo
- Tenemos que cambiar la secuencia de arranque en la BIOS en la opción de Boot para indicar que arranque primero desde el USB.

Ya tenemos el equipo configurado para proceder a instalar **KDE Neon**. Conectamos el USB y encendemos el equipo, si todo ha ido bien, aparecerá el escritorio de KDE Neon.

![Escritorio](/EnguedellarOs/images/kde_neon_inicio02.png)

Desde aquí podemos probar el funcionamiento de KDE Neon en nuestros ordenador, por ejemplo, si el wifi funciona y detecta nuestra red de casa, si no consume muchos recursos de nuestra maquina. Si estamos contentos como funciona y no hay problemas con el icono del escritorio **Install System** empezaremos con la instalación.

En primer lugar tenemos la ventana de **Welcome**.

![Welcome](/EnguedellarOs/images/kde_neon_welcome03.png)

Aquí escogeremos el idioma para que el instalador se cambie a nuestra lengua y se instale, es este caso, en Español. Después pulsamos *Siguiente*.

Se cambiara la pantalla a la ventana **Ubicación**.

![Ubicación](/EnguedellarOs/images/kde_neon_location04.png)

Marcaremos en el mapa en el país donde nos encontramos para que el sistema configure nuestra zona horaria.

Ahora pasamos a la siguiente pantalla donde configuraremos el **Teclado** de nuestro equipo.

![Teclado](/EnguedellarOs/images/kde_neon_teclado05.png)

Le indicaremos el lenguaje que debe de usar nuestro teclado, en la parte inferior de la ventana encontramos una caja de texto donde podemos comprobar que las teclas del teclado funciona correctamente sin mostrar caracteres extraños.

Ahora pasaremos al proceso más complicado y delicado de la instalación la creación de particiones en nuestro disco duro o SSD.

![Particiones](/EnguedellarOs/images/kde_neon_particion06.png)

Antes de seguir, tengo que hacer una aclaración, para hacer el articulo estoy usando una *maquina virtual* *QUEMU* para instalar **KDE Neon** ya que no dispongo de un equipo de pruebas. ¿Por qué digo esto? por que en este apartado habréis notado, que a vosotros os aparecen más opciones que las que indico en la imagen.

>En primer opción tendréis **Instalar KDE Neon junto a otro sistema operativo**, en esta opción, es el propio instalador de KDE Neon quien se encargará de crear las particiones y instalar el *Grub* para que nuestro equipo se configure para disponer de los dos sistemas operativos. No me aparecen por hacer la instalación en una maquina virtual.

Pero vamos a concentrarnos en la opción de crear el **Particonado Manual.** Asi tendremos mejor control sobre la instalación y la organización de nuestro disco duro.

Hacemos check en **Particonado Manual.** y después a *Siguiente*, no encontramos ahora en la próxima pantalla.

![Particones](/EnguedellarOs/images/kde_neon_particonado07.png)

Si os fijasteis, en la ventana anterior en la parte superior izquierda el instalador de KDE nos informaba que estamos haciendo una instalación sobre BIOS, es decir, no tenemos UEFI, eso es debido por que usamos la maquina virtual.

![Particones](/EnguedellarOs/images/kde_neon_particion07_1.png)

Explicare la diferencia entre las dos instalaciones. Por ahora vamos a realizar un proceso común a las dos formas, y es crear una tabla de particiones nueva, como es evidente, tendremos que pulsar el botón **Nueva tabla de particiones** y obtendremos la siguiente ventana.

![Tabla de particiones](/EnguedellarOs/images/kde_neon_particonado09.png)

A la pregunta de que tipo de tabla deseamos crear le responderemos un _**Tabla de Particiones GUID(GPT)**_. Aunque GPT es una característica de UEFI también es compatible con BIOS con lo que funciona perfectamente.

Después nos indicara que tenemos una partición creada con *Espacio libre*. Haciendo doble click sobre ese texto ya podremos crear nuestras particiones.

### _Crear partición boot con UEFI_

Voy a explicar como crear la partición EFI si lo tenemos activo en la BIOS.

![EFI](/EnguedellarOs/images/kde_neon_efi10.png)

Como podéis ver cuando creamos una partición nueva nos sale la ventana anterior, y tendremos que cumplimentar los campos que nos solicita:

Tamaño
: Es el tamaño de nuestra partición en megabytes.

>El tamaño para la partición boot/efi es suficiente con 300MiB.

Sistema de archivos
: El sistema de archivos o sistema de ficheros es el componente del sistema operativo encargado de administrar y facilitar el uso de las memorias periféricas, ya sean secundarias o terciarias.

>Es importante que para esta partición el tipo sea FAT32

Punto de Montaje
: es un proceso mediante el cual el sistema operativo hace que los archivos y directorios de un dispositivo de almacenamiento (como un disco duro , CD-ROM o un recurso compartido de red ) estén disponibles para que los usuarios accedan a través del sistema de archivos de la computadora.

>De las opciones que os aparecen escoger /boot/efi

Y ya tenemos la partición de inicio para que el UEFI reconozca nuestro sistema en el arranque del equipo.

### _Crear partición boot sin UEFI_

El proceso es similar al anterior descrito pero cambiando los valores según nuestra necesidades.

1. En el campo _**Tamaño**_ recomiendo unos **500MiB**.
2. En el campo _**Sistema de Archivos**_ seleccionaremos la opción **Ext4**.
3. En el campo _**Punto de Montaje**_ indicaremos **/boot**

## ¡Ahora le toca el turno a las demás particiones de nuestro sistema!

A partir de ahora el proceso es exactamente igual tengamos o no tengamos UEFI.

Crearemos la partición **root** donde se instalara el sistema GNU/Linux.Tan solo tenemos que cambiar el campo _**Punto de Montaje**_ por **/** que significa que es la raíz del sistema e indicarle el tamaño que deseamos en el campo _**Tamaño**_. En el campo _**Sistema de archivos**_ indicaremos el mismo que la partición /boot
>Con el tiempo experimentaras con otros tipos de sistemas de archivos, pero para empezar este formato es más que bueno.

![Root](/EnguedellarOs/images/kde_neon_root11.png)

Una vez ya establecimos el **root** es el turno para la partición **/home**. En esta partición se encontrará el directorio donde guardaremos nuestros datos como archivos ofimáticos, videos, fotográficas, etc. Es muy recomendable crear esta partición ya que nos asegura que nuestros datos están separados del sistema y ante un posible error del mismo siempre podremos recuperar los datos sin problemas.

Como ya sabemos tenemos que cambiar el campo _**Punto de Montaje**_ por **/home** que significa que es la partición donde se guardarán los datos del usuario e indicarle el tamaño que deseamos en el campo _**Tamaño**_. En el campo _**Sistema de archivos**_ indicaremos el formato **ext4**.

![Home](/EnguedellarOs/images/kde_neon_home12.png)

## ¡Ya casi estamos acabando!

No entrare si es necesario o no, esta partición, la polémica **Swap**. Yo solo puedo decir, que por mi experiencia, manejando bases de datos y con otras aplicaciones que han ido a buscar la **Swap** al no encontrarla el sistema se quedo congelado, con lo que siempre la creo.

![Swap](/EnguedellarOs/images/kde_neon_swap13.png)

Indicarle el tamaño que deseamos en el campo _**Tamaño**_. En el campo _**Sistema de archivos**_ indicaremos el formato **linuxswap**. En esta ocasión el campo _**Punto de Montaje**_ no hay que indicarle nada, ya que la **Swap** no se monta en el sistema.

Una vez que ya hemos creado todas las particiones nuestro disco se vera algo parecido a la siguiente imagen.

![Particiones](/EnguedellarOs/images/kde_neon_14.png)

## ¡Ya podemos seguir con la instalación!

Ya solo queda continuar, con lo que pulsamos el botón *Siguiente*.

![Usuario](/EnguedellarOs/images/kde_neon_15.png)

Solo tenemos que indicar el nombre del **Usuario** que queremos crear para el sistema, el **Nombre del Ordenador** y la **Contraseña** con la que entraremos en el sistema. Si marcamos el check de **Conectarse automáticamente** al iniciar el ordenador no preguntara ni usuario ni contraseña. Una vez rellenados pulsamos el boton **Instalar**. Y empezará la instalación.

![Instalando](/EnguedellarOs/images/kde_neon_16.png)

Ahora solo tenemos que esperar que acabe con el proceso. Cuando eso suceda nos mostrara el siguiente mensaje.

![Fin](/EnguedellarOs/images/kde_neon_17.png)

## ¡Ya se ha acabado!

Ahora solo tenemos que reiniciar y ya podemos disfrutar de **KDE Neon** instalado en nuestra maquina.

Se ha hecho largo , pero espero que os haya aclarado las dudas a la hora de instalar un sistema GNU/Linux y a partir de ahora instalarlo sin problemas.