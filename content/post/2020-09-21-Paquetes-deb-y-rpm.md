---
title: "Paquetes deb y rpm"
date: 2020-09-21T16:21:42+02:00
author: Francisco Mauriz Pereira
categories: [Linux,aplicaciones,paquetes]
tags: [Linux,instalación,paquetes]
draft: false
---
Los paquetes deb son archivos **.ar estándar de Unix** que incluyen dos archivos **.tar en formato gzip, bzip2 o lzma**, uno de los cuales alberga la información de control y el otro los datos de los paquetes.

Estos paquetes contienen tres archivos:

- **debian-binary** que es el  número de versión del formato deb.
- **control.tar.gz** contiene toda la meta-información del paquete.
- **data.tar, data.tar.gz, data.tar.bz2 o data.tar.lzma** son todos los archivos a instalar.

## Instalar paquetes .deb

Como ya hemos indicado antes para poder instalar estos paquetes podemos usar interfaces gráficas como Synaptic, PackageKit, Gdebi o en Ubuntu Software Center. Son aplicaciones que nos ayudan a instalar, a actualizar y borrar paquetes muy fácilmente. Pero si nos gusta usar la Terminal, podemos hacer los mismo con los siguientes comandos.

```bash
 # Para instalar paquetes:

    dpkg -i paquete.deb

 #Para verificar que se ha instalado correctamente:

    dpkg -l | grep 'paquete'

 # Para eliminar la instalación:

    dpkg -r paquete.deb
    dpkg -P paquete.deb (esta última borra todos los datos del programa)1​
```
    
## Paquetes .rpm    
    
 RPM Package Manager
 : Es una herramienta de administración de paquetes pensada básicamente para GNU/Linux. Es capaz de instalar, actualizar, desinstalar, verificar y solicitar programas. RPM es el formato de paquete de partida del Linux Standard Base.

Desarrollado por **Red Hat** para Red Hat Linux pero en la actualidad muchas distribuciones GNU/Linux lo usan, las más destacadas son Fedora, Mandriva, Mageia, PCLinuxOS, openSUSE.

Entre las características de RPM podemos mencionar:

- Los paquetes pueden ser cifrados y verificados con GPG y MD5.
- Los archivos de código fuente (por ejemplo .tar.gz, .tar.bz2) están incluidos en SRPMs posibilitando una verificación posterior.
- PatchRPMs y DeltaRPMs, que son equivalentes a ficheros parche, pueden actualizar incrementalmente los paquetes RPM instalados.
- Las dependencias pueden ser resueltas automáticamente por el gestor de paquetes.

Para gestionar los paquetes **.rpm** también podemos usar interfaces gráficas como el centro de software de GNOME. Desde la Terminal podemos gestionar los paquetes con los siguientes comandos:

```bash
rpm -qa  # muestra paquetes instalados.

rpm -qi foo # muestra la información de un paquete RPM.

rpm -ql foo # lista ficheros de un paquete RPM instalado.

rpm -qc foo # lista solo los ficheros de configuración.

rpm --checksig foo # verifica firma de un paquete RPM.

rpm -ivh "localFile.rpm" # instala un paquete.

rpm -e "localFile.rpm" # desinstala un paquete.
```

En grandes rasgos estos son los paquetes más usados en GNU/Linux para instalar programas en nuestro sistema. Aunque actualmente contamos con más opciones para hacerlo como los paquetes Flatpak, las aplicaciones AppImage y otras muchas más que iremos comentando y aprendiendo poco a poco.