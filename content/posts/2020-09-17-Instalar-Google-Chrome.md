---
title: "Instalar Google Chrome en GNU/Linux"
date: 2020-09-17T19:21:42+02:00
author: Francisco Mauriz Pereira
categories: [Linux,aplicaciones,Google Chrome]
tags: [Linux,instalacion, Google Chrome]
draft: false
---

Últimamente me preguntan muchas personas si en GNU/Linux se puede instalar Google Chrome, y si se
puede, ¿como se haría la instalación?.

Por eso voy a explicar la forma más sencilla de hacerlo y después otra manera ,también sencilla, pero con unos pocos
más de pasos a seguir.


## Instalación desde el Centro de Software de la distro.

Esta es una manera muy sencilla de instalar Google Chrome, incluso, cualquier otro programa que deseemos instalar.

Lo primero que debemos hacer es ejecutar el **Centro de Software**, que su icono estará en el menú de aplicaciones.

Nota:

> _En mi caso usaré el **Centro de Software** de GNOME, ya que ahora mismo tengo instalado FEDORA 32 en mi equipo con
> el entorno GNOME, pero el procedimiento es el mismo con cualquier distro que use GNOME._

Al ejecutarlo nos aparecerá en el Escritorio la aplicación.

![Centro De Software](/EnguedellarOs/images/chrome_01.png)

Si nos fijamos en la esquina superior izquierda, tenemos un **icono de lupa** que al hacer click sobre él no aparecerá una **barra de búsqueda** en donde indicaremos el nombre de la aplicación que vamos a instalar, **Google Chrome**. 

![Centro De Software](/EnguedellarOs/images/chrome_02.png)

Se nos filtran las aplicaciones y nos quedamos con la aplicación de Google Chrome. Ahora, solo queda clickar sobre el nombre y cambiara la pantalla.

![Centro De Software](/EnguedellarOs/images/chrome_03.png)

Nos presentará una pequeña imagen de muestra para ver como es la aplicación , un resumen y datos sobre la licencia de la misma. Pero para conseguir que se instale en nuestro, pulsaremos el botón que nos indica **Instalar** y automáticamente empezará la instalación, eso si, primero nos pedirá que informemos de la contraseña root para seguir.

Y asi de sencillo es instalar Google Chrome dede el **Centro de Software** que ya viene instalado por defecto en nuestras distros linuxeras.


## Instalación desde la página oficial de Google.

Esta es la manera que todo Windosero tiene bien aprendida para instalar cualquier programa. Ir con el navegador a la página web , descargarse el ejecutable e instalarlo en su equipo (Si es una aplicación legal ... sino el Windosero sabe manejar, eso que llaman parches :S ).

En GNU/Linux es igual, pero con la salvedad a la hora de instalarlo. Vamos a verlo, lo primero es ir a la pagina oficial de Google Chrome.

[https://www.google.com/chrome/](https://www.google.com/chrome/)

Una vez en ella, pulsamos el botón **Download Chrome** o **Descargar Chrome**.

![https://www.google.com/chrome/](/EnguedellarOs/images/chrome_04.png)

Aparecerá una ventana dándonos dos opciones de descarga, las dos tienen en común que son de 64Bits, pero el tipo del fichero es diferente, con lo que nos descargaremos el que es compatible con nuestra arquitectura de paquetería:

- **.deb**: Son de la rama **Debian** y sus derivados como **Ubuntu** y los derivados de este como **Linux Mint** y asi con las que su distro madre es Debian.
- **.rpm**: Son de la rama **Red Hat** y sus derivados como **Centos** o **Fedora** y **Open Suse**.

![https://www.google.com/chrome/](/EnguedellarOs/images/chrome_05.png)

Seleccionamos el que nos corresponda y pulsamos el botón de **Aceptar y instalar**. Con lo que se descargará el fichero .deb o .rpm según el caso.

Si nuestra distro no es ninguna de las mencionadas antes debemos seguir las instrucciones que la misma pagina de descarga nos advierte en el siguiente texto:

>Not Debian/Ubuntu or Fedora/openSUSE? There may be a community-supported version for your distribution [here](https://chromium.googlesource.com/chromium/src/+/refs/heads/master/docs/linux/chromium_packages.md).

Si hacemos click en el texto *here* o *aquí* nos llevará a la siguiente página, donde debemos seguir las indicaciones de los enlaces.

![https://chromium.googlesource.com/chromium/src/+/refs/heads/master/docs/linux/chromium_packages.md](/EnguedellarOs/images/chrome_06.png)


Una vez descargado tenemos que instalar el fichero ejecutable. Podemos hacerlo de varias formas:

### Doble click en el fichero ejecutable.

Para hacerlo de esta manera, tenemos que darle permisos de ejecución al fichero, con lo que pulsaremos con el segundo botón del ratón al fichero y en la pestaña *Permisos* activamos el check de *Ejecutable* y aceptamos. Después solo basta con hacer doble click y se ejecutará la instalación.

### Desde la terminal.

Según el fichero que hayamos descargado, en una terminal ejecutamos el siguiente comando.

#### Ejecutable .deb

```bash
sudo dpkg -i fichero.deb
```

#### Ejecutable .rpm

```bash
sudo rpm -i fichero.rpm
```

Como veis estas son dos formas de tener *Google Chrome* en nuestro sistema GNU/Linux. He intentando explicar las dos maneras más fáciles de hacerlo, aunque como siempre en el sistema de Tux, hay muchas más formas de hacerlo y con el tiempo las sabréis controlar todas.  
