---
date: 2020-09-08T07:40:36+02:00
author: Francisco Mauriz Pereira
title: 'Crear USB de instalación de distribución GNU/Linux'
categories: [Linux,instalacion]
tags: [Linux, instalación,empezando]
draft: false
---

# Como crear un USB de instalación para GNU/Linux

Cuando por fin nos decidimos a probar o a instalar una distribución GNU/Linux , ya sea , Ubuntu,Linux mint, Fedora , etc. Esa distribución que hemos visto que nos gusta o se adecua a nuestras necesidades y a nuestro equipo tendremos que crear un USB de instalación o un USB booteable para poder arrancar el instalador en nuestro equipo.

Los pasos a seguir son sencillos y tenemos muchas opciones para realizar el USB ejecutable. Explicaré cómo hacerlo desde Windows y GNU/Linux usando las aplicaciones *Rufus* y *balena Etcher* respectivamente en su Sistema operativo, por que creo que son las aplicaciones que nos lo ponen más fácil a la hora de hacerlo.

![Rufus](/images/ventana_rufus.png "Imagen de Rufus")

![balena Etcher](/images/ventana_balena.jpg "Imagen de balena Etcher")


Lo primero que debemos hacer antes de ponernos a crear el USB es descargarnos la imagen de la distribución que queremos instalar, lo más recomendable, es siempre descargarla de las páginas oficiales que nos ofrecen las distros. Por ejemplo, si queremos instalar Linux Mint , deberemos descargarla de su [página oficial](https://linuxmint.com/download.php).

Una vez ya tenemos la imagen ISO en nuestro ordenador, recomiendo, verificar la descarga de la ISO, normalmente en las páginas oficiales donde nos bajamos la iso, tam0bién tenemos un fichero de texto donde tiene escrito el valor de la  suma  [SHA256](
https://es.m.wikipedia.org/wiki/SHA-2) , lo descargamos también a nuestro equipo.

## <u>Verificación de la imagen ISO descargada.</u>

La verificación de la ISO es importante ,ya que gracias a ella podemos estar seguros de dos cosas:

 - Se descargó sin ningún problema, es decir, el fichero no está corrupto.
 -  La imagen ISO que proporcionan las distribuciones para su uso es la verdadera y no una modificada por terceros.

El método para realizar la comprobación es sencillo, solo tenemos que ejecutar desde una terminal el siguiente comando:

**En GNU/Linux**:
```bash
sha256sum -b tufichero.iso
```

**En Windows**:

Podemos usar la aplicación *Microsoft File Checksum Integrity Verifier* que podemos descargar desde [aquí](https://www.microsoft.com/en-us/download/confirmation.aspx?id=11533).
```cmd
fciv tufichero.iso -sha256
```

Estos dos comandos nos devolverán el resultado de la suma SHA256 de la ISO descargada, por ejemplo:

```bash
2ed14068a18ce404054dfc63e50c28e918a92a14
```

Recordemos que cuando descargamos la ISO de la distro también nos descargamos un fichero de texto que contiene el valor de la suma SHA256, si ese valor del fichero de texto es el mismo valor que obtenemos con la ejecución de los comandos anteriores podemos decir con total seguridad que la ISO esta correcta y podemos pasar al siguiente proceso para crear el USB.

## <u>Crear USB ejecutable en Windows.</u> [Si usas GNU/Linux sigue por aquí](#Crear-USB-ejecutable-en-GNU/Linux)

Una vez que ya sabemos que la ISO no tiene ningún problema ya podremos pasarla al USB.

En Windows usaremos la aplicación [**Rufus**, que puedes descargarla desde aquí](http://rufus.ie/).

 Una vez instalada , la ejecutamos y nos aparece la siguiente imagen:

![](/images/ventana_rufus.png) 

Es una interface muy intuitiva y fácil de usar, pero iré describiendo los distintos apartados que nos ofrece.

### Device o Dispositivo

En este combo aparece los distintivos dispositivos de almacenamiento externos que tengamos conectados en el ordenador. De todos los que nos aparece debemos escoger el nombre de la unidad USB donde queramos grabar la imagen ISO.

### Boot Selection o  Eleccion de arranque

Aquí debemos indicar que imagen ISO vamos a grabar en el USB haciendo click en el botón SELECT y navegando por el gestor de archivos hasta encontrar la imagen.

### Partition Scheme o Esquema de partición

Tenemos dos opciones MBR y GPT.
1. **MBR (Master Boot Record)** ,es el componente del sistema que sirve  como administrador de arranque para iniciar sistemas informáticos basados en BIOS (incluida la instalación de estos sistemas) y como una tabla de particiones para asignar la memoria disponible de manera eficaz. 
2. en los últimos años, el **MBR** se ha ido sustituyendo cada vez más por su sucesor oficial, la tabla de particiones **GUID o GPT (GUID Partition Table)**. Este nuevo estándar de las tablas de particiones forma parte de la especificación UEFI, que no ha dejado de ganar terreno al BIOS desde el año 2000.

En esta opción tenemos que tener en cuenta si nuestra BIOS tiene **UEFI** y si la tiene,si está activada. Si ese es nuestro caso escogeremos la opción de **GPT**. En cambio, si nuestro equipo no tiene *UEFI*  podemos escoger la opción de **MBR**.

Nota:
>Aunque la GPT forma parte de la especificación UEFI, la tabla de particiones GUID también puede utilizarse para particionar el disco duro en ordenadores BIOS. Sin embargo, hay algunas limitaciones, dependiendo del sistema operativo: las versiones de Windows con BIOS, por ejemplo, no pueden arrancarse desde un medio particionado con GPT.

### Target System o Sistema destino

En esta opción debemos indicar el valor *BIOS or UEFI*. Así nos aseguramos que arranca tengamos o no tengamos UEFI.

### Volumen Label o Etiqueta de volumen

Con esta caja de texto le podemos asignar un nombre a nuestra unidad USB, este nombre sera el que muestre el ordenador cuándo lo monte en nuestro sistema.

### File System o Sistema de archivos

Indicaremos el sistema de archivos que usará Rufus para formatear la unidad USB antes de grabar la imagen ISO. Normalmente las unidades USB se formatean con el sistema de archivo FAT32, con lo que dejaremos el valor por defecto.

### Cluster size o Tamaño del clúster

Nos permite cambiar el tamaño del clúster en el momento del formateo. Aquí vuelve a ser recomendable dejar los valores por defecto si no sabemos bien lo que estamos haciendo.

Una vez establecidos todas las opciones, ya podemos comenzar a crear el USB de instalación, el proceso comenzará cuando pulsemos el botón START o EMPEZAR. Entonces aparecerá el progreso de creación sobre la ventana de Rufus como una barra de color verde. Una vez finalizado ya podemos desmontar el USB de nuestro equipo y lo tendremos listo para usarlo.

## Crear USB ejecutable en GNU/Linux.

En GNU/Linux usaremos la aplicación Balena Etcher, puedes descargarla dede [aquí](https://www.balena.io/etcher/).

Se descargará un fichero *.zip* solo tenemos que descomprimirlo en cualquier directorio de nuestro equipo. Cuando este descomprimido aparecerá un fichero:

![AppImage](/images/ico_balena.png)

Si pulsamos dos vees sobre él con el botón izquierdo del botón se ejecutara y aparecerá la siguiente ventana:

![balena Etcher](/images/ventana_balena.jpg "Imagen de balena Etcher")

Nota
> Si al pulsar sobre el fichero AppImage no se ejecuta debemos asegurarnos que el fichero tiene permisos de ejecución. Podemos comprobarlo si pulsamos con el botón derecho del ratón sobre el AppImage y seleccionamos la opción de propiedades que nos muestra el menú modal. Si vemos que el check de "es ejecutable" esta marcado significa que se ejecutará sin problemas, sino lo esta lo marcamos y aceptamos para que los permisos se guarden.

> ![Ventana propiedades](/images/propiedades_balena.png)


El proceso de creación del USB de instalación con **Balena Etcher** es muy sencillo solo son tres secillos pasos:

![](/images/ventana_balena.jpg)

Primero en la opción **Select image** al pulsar el botón le indicamos que imagen ISO vamos a grabar en el USB. Después En **Select Drive** escogeremos nuestro dispositivo USB que vamos a utilizar. Por ultimo pulsaremos el botón **Flash** y empezará el proceso. Pero antes nos pedirá la contraseña root de nuestro sistema para otorgarle permisos a Balena Etcher para que crear el USB ejecutable.

Despues veremos la ventana que nos indica que se esta *Flashing* la unidad USB, cunado termine la barra del proceso, Balena etcher valida que la creación fue correcta. DEspues de eso ya podemos desconectar el USB de nuestro ordenador y ya lo tenemos listo para usarlo.


Estas son las dos formas más utilizadas de crear un USB ejecutable para instalar GNU/Linux tanto para Hacerlo desde Windows como en GNU/Linux. Ahora solo nos queda instalar la distro que más nos guste en el equipo.