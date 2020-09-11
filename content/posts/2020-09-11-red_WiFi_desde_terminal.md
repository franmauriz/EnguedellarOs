---
title: "Configurar red WiFi desde la terminal"
date: 2020-09-11T11:59:34+02:00
author: Francisco Mauriz Pereira
categories: [Linux,Wifi]
tags: [Linux, Wifi, Red]
draft: false
---

# Servicio iwd (iNet wireless daemon)

**Iwd** es un demonio inalámbrico para Linux escrito por Intel. El objetivo principal del proyecto es optimizar la utilización de recursos al no depender de ninguna biblioteca externa y, en cambio, utilizar las funciones proporcionadas por el kernel de Linux en la mayor medida posible.

Cabe destacar que **iwd** es compatible con *connman* y *network-manager*, estos pueden gestionar redes a través de **iwd** como backend.

## Instalación de iwd.

Para las principales distros de linux para instalar esta herramienta tan solo tenemos que teclear en el terminal el comando correspondiente a su sistema.

```bash
# Debian y derivadas:
sudo apt install iwd

# Arch y derivadas:

sudo pacman -S iwd

# Fedora y derivadas:

sudo dnf install iwd

# openSUSE:

sudo zypper install iwd
```

Ahora vamos a detener el servicio wpa_supplicant para que no entre en conflicto.

```bash
sudo systemctl stop wpa_supplicant.service
```

Para comprobar que la instalación de **iwd** fue correcta comprobamos el estado de demonio de *iwd*.

```bash
sudo systemctl status iwd.service
```

Si nos muestra que esta todo corriendo sim problemas.Ya podemos ejecutar el comando en la terminal:

```bash
iwctl
```

Esto hará que aparezca una terminal interactiva para usar los comandos de **iwd**.

```bash
[iwd]#
```

En esa terminal ya podremos listar dispositivos y redes a las cuales conectarnos.

## Listar interfaces de red

En nuestro equipo el nombre de la interface de red, o comúnmente llamada, tarjeta de red, el sistema le puede asignar distintos nombres que (wlan0/wlp4s0/wlp5s0) puede variar de acuerdo a la distribución, o al driver en uso.

```bash
[iwd]# device list
```

El resultado que nos devuelve es el nombre de nuestras interface de red.

![list](/EnguedellarOs/images/wifi_listar01.jpg)


## Escanear/Listar redes Wifi


```bash 
[iwd]# station device get-networks
```

En donde indica el comando _**device**_ se refiere al nombre de la interface de red, en este caso, seria *wlan0*.

![list](/EnguedellarOs/images/wifi_scan02.jpg)

## Conectarse a una red Wifi

```bash
[iwd]# station device connect SSID
```

![Connect](/EnguedellarOs/images/wifi_connect01.jpg)

Pedirá la contraseña y la almacenará en: /var/lib/iwd/ bajo el formato: ESSID.psk.

![Connect](/EnguedellarOs/images/wifi_connect02.jpg)

En el futuro recurrirá a este archivo para conectarse automáticamente. Suponiendo que el nombre del ESSID es MiFibra-0543-5G y la contraseña: DoQp3TyL, el archivo de configuración quedaría de la siguiente manera:

```bash
cat /var/lib/iwd/MiFibra-0543-5G.psk

[Security]
PreSharedKey=2bc929bdb167ee3f69abf7fdedb757e685715d4f65e4175583466c30fa2cf34c
Passphrase=DoQp3TyL
```

## Desconectarse de una red wifi

Con este comando desconectamos la interface Wifi.

```bash
[iwd]# station device disconnect
```

*Iwd* es una herramienta muy practica, sencilla de poder gestionar la conexión de la red Wifi de nuestro equipo con las redes Wifi de nuestra casa, despacho , etc.