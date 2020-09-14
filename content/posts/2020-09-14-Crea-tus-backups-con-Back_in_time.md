---
title: "Crea Tus Backups Con Back_in_time"
date: 2020-09-14T11:39:25+02:00
author: Francisco Mauriz Pereira
categories: [Linux,Backup,Seguridad]
tags: [Linux, Backup, Seguridad]
draft: false
---

# Crea tus backups con Back In Time.

Seguro que alguna vez te has lamentado de no tener una copia de seguridad de tus documentos de trabajo, las fotos de tus vacaciones o momentos familiares, etc.

Es un sentimiento de impotencia y tristeza por que ya no puedes recuperarlos, con lo que no te daré el sermón de lo importante que es hacer los respaldos de nuestros datos.

Pero te diré una forma sencilla y cómoda de poder realizarlas para que no te pase nunca más.

Con **Back In Time** crearás tus copias de seguridad en el momento o programarlas para que no te tengas que preocupar de hacerlo, ya que la aplicación lo hará automáticamente.

**Back In Time** usa rsync como backend y tiene la característica de usar enlaces físicos para archivos que no han cambiado en una instantánea diferente, por lo que que ocupa espacio en el disco solo una vez para los archivos que no se modificaron.

Es posible utilizar varios perfiles de copia de seguridad.

Las copias de seguridad se guardan en texto plano , con lo que con nuestro gestor de archivos podemos navegar dentro del respaldo.

Las propiedades como los permisos de los archivos se guarda en un archivo comprimido aparte. Esto lo hace para evitar conflictos con el dispositivo donde se guardan los respaldos por si no soporta permisos, Back In Time, utiliza el archivo para restaurar los permisos.

## Instalación de Back In Time

Como en el articulo anterior instalamos KDE Neon, voy a realizar la instalación desde ahi.

Abrimos la terminal, y escribimos el siguiente comando:

```bash
sudo apt install backintime-qt
```

![Instalación](/EnguedellarOs/images/backintime_01.png)

Después de escribir la contraseña de administrador empezará la instalación.

## Proceso para crear copia de seguridad.

![General](/EnguedellarOs/images/backintime_02.png)

### 1. **Pestaña General**:
Aquí le indicaremos el modo en el cual queremos hacer las copias. Para eso disponemos de varios modos:

- _**Local**_: Este modo ha ce referencia a almacenamiento en nuestro propio equipo, o en unidades montadas. Pero tenemos que tener en cuenta que el sistema de archivos de destino como el protocolo utilizado para montar la unidad deben soportar enlaces duros y simbólicos.
- _**Cifrado Local**_: Funciona igual que el modo *Local* pero la copia se guardan cifrados con **EncFS**.
- _**SSH**_: Este modo nos permite guardar nuestras copias de seguridad en un dispositivo remoto utilizando SSH.
- _**Encriptado SSH**_: Es igual que el modo *SSH*, pero los respaldos se guardan cifrados utilizando **EncFS**.

En **Dónde guardar las instantáneas** le indicaremos el dispositivo local o remoto donde guardar el respaldo.

En el grupo **Avanzado** le indicamos el **Nombre del Ordenador* del que queremos hacer la copia de seguridad, el *Usuario*. Aunque estos datos los cumplimentará *Back In Time* automáticamente con lo que dejamos los datos que nos muestra por defecto.

En **Tareas programadas** podremos decidir cuando queremos que realice el respaldo, ya sea indicándole un día y hora concretos, que sea una vez al mes, a la semana o incluso al conectar un dispositivo externo o al encender el equipo, etc. **Back In Time* nos ofrece un gran abanico de posibilidades.

### 2. **Pestaña Incluir y Excluir**:

![Incluir](/EnguedellarOs/images/backintime_03.png)

En la pestaña **Incluir** es donde escogeremos los archivos o directorios de los que queremos realizar la copia de seguridad. Solo tenemos que ir añadiéndolo  pulsando el botón *Añadir archivo* para agregar los archivos o pulsar *Añadir carpeta* en el caso de querer agregar directorios a la copia.

![Excluir](/EnguedellarOs/images/backintime_04.png)
La pestaña **Excluir** funciona igual que la pestaña *Incluir* pero al revés, los archivos y directorios que indiquemos aquí, **NO** se realizara copia de ellos.

### 3. **Pestaña Auto eliminar**:

![Incluir](/EnguedellarOs/images/backintime_05.png)

En esta pestaña podremos eliminar aquellos respaldos según lo configuremos.

- Respaldos que tengan una edad superior a un límite prefijado.
- Cuando el espacio libre sea inferior a un determinado límite.
- Cuando el nodo de inodos libres sea inferior a un valor prefijado.

### 4. **Pestaña Auto Opciones y Opciones Avanzadas**:

Con estas pestañas podremos configurar el funcionamiento de la aplicación.

![Opciones](/EnguedellarOs/images/backintime_06.png)
![Opciones Avanzadas](/EnguedellarOs/images/backintime_07.png)

Cuando ya tenemos la configuración de nuestra copia de seguridad ya podremos realizar la instantánea pulsando el botón **Tomar instantánea**

![Tomar instantánea](/EnguedellarOs/images/backintime_08.png)

Y podremos ver ne la parte inferior de la ventana como va el proceso y que ficheros o directorios esta copiando.

![Finalizado](/EnguedellarOs/images/backintime_09.png)

Y Cuando termine ya tendremos nuestros datos respaldados en el soporte que hayamos usado para almacenarlo y la tranquilidad de que no los vamos a perder. Los respaldos son una medida de seguridad fundamental para evitar problemas futuros, y **Back In Time** te simplificará considerablemente este tedioso trabajo.
