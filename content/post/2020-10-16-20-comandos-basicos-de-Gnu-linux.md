---
title: "1º parte.20 Comandos básicos de GNU/Linux para noveles."
date: 2020-10-10T18:13:22+02:00
author: Francisco Mauriz Pereira
categories: [Linux,Comandos,Terminal]
tags: [Linux,Comandos,Terminal]
draft: false
---

![Terminal](/EnguedellarOs/images/comandos.png)

Cuando empezamos en el mundo de GNU/Linux y ya hemos superado con éxito las etapas de instalación y de personalización de nuestro sistema y estamos contentos con él. De repente no sabemos por que aparece un error, con lo que nos dirigimos rápidamente a buscar la solución en internet, por medio de los buscadores , por foros , por grupos de Telegram, etc..

Pero si somos noveles , es normal que encontremos en una reseña de un foro, o un usuario de la comunidad nos indique la solución, pero esta venga de la mano los ***temibles comandos de la terminal*** . Empiezan a inundarnos de comandos que no sabemos que significan y debemos confiar en que la solución encontrada o indicada por otra persona sea de confianza y no dañe mas nuestro equipo.

Para tener más seguridad en este escenario recomieindo lo siguiente:
> Si no sabes que hace un comando , **NO LO EJECUTES**. Primero mira en la documentación, ya sea por medio de internet, recomiendo que visitéis la pagina web [https://www.die.net/](https://www.die.net/) donde encontrareis toda la documentación necesaria para cualquier comando linux. O a través de la terminal con el comando **man**.

Aquí os dejo un primer video de una serie de varios donde explicare los comandos más básicos que cualquier novel de linux debe conocer para asi poder interpretar esos comandos que encontramos por internet o nos dicen los usuarios de la comunidad.

{{< youtube rtZ-l5I6grg >}}

Aquí esta la lista de los comandos que aparecen en el video:

1. Comando **ls**.Lista las carpetas y ficheros de un directorio.
2. Comando **cd**. Mueve nuestra posición dentro de un directorio inferior o superior.
3. Comando **cp**. Copia ficheros o directorios en otra ubicación del sistema o unidad externa de almacenamiento.
4. Comando **mv**. Mueve ficheros o directorios en otra ubicación del sistema o unidad externa de almacenamiento.
5. Comando **rm**. Borra ficheros o directorios (rm -R) del equipo.
6. Comando **mkdir**. Crea directorios en el sistema.
7. Comando **rmdir**. Borradirectorios del ordenador.
8. Comando **chown** CAmbia el propietario de in directorio o fichero
9. Comando **chmod** cambia los bits de modo de archivo de cada archivo dado según el modo , que puede ser una representación simbólica de los cambios a realizar o un número octal que representa el patrón de bits para los nuevos bits de modo. chown cambia la propiedad del usuario y / o grupo de cada archivo dado. Si solo se proporciona un propietario (un nombre de usuario o ID de usuario numérico), ese usuario se convierte en el propietario de cada archivo dado y el grupo de archivos no se cambia. Si el propietario va seguido de dos puntos y un nombre de grupo (o ID de grupo numérico), sin espacios entre ellos, la propiedad del grupo de los archivos también cambia. Si dos puntos pero ningún nombre de grupo sigue al nombre de usuario, ese usuario se convierte en el propietario de los archivos y el grupo de archivos se cambia al grupo de inicio de sesión de ese usuario. Si se dan los dos puntos y el grupo, pero se omite el propietario, solo se cambia el grupo de archivos; en este caso, chown realiza la misma función que chgrp. Si solo se dan dos puntos, o si todo el operando está vacío, no se cambia ni el propietario ni el grupo.Comando chmod CAmbia los permisos de ejecucion, escritura y lectura
chmod cambia los bits de modo de archivo de cada archivo dado según el modo , que puede ser una representación simbólica de los cambios a realizar o un número octal que representa el patrón de bits para los nuevos bits de modo. 
10. Comando **Locale**
    	obtenga información específica de la configuración regional
11. Comando **updatedb** .updatedb crea o actualiza una base de datos utilizada por Locate (1) . Si la base de datos ya existe, sus datos se reutilizan para evitar volver a leer los directorios que no han cambiado.updatedb generalmente se ejecuta diariamente por cron (8) para actualizar la base de datos predeterminada. 
12. Comando **date** .Visualice la hora actual en el FORMATO dado o configure la fecha del sistema
13. Comando **tar**. GNU ' tar ' guarda muchos archivos juntos en una sola cinta o archivo de disco, y puede restaurar archivos individuales del archivo. 
14. Comando **cat**.Concatenar ARCHIVO (s), o entrada estándar, a salida estándar. 
15. Comando **less**.Less es un programa similar a more (1) , pero que permite el movimiento hacia atrás en el archivo y hacia adelante. Además, menos no tiene que leer todo el archivo de entrada antes de comenzar, por lo que con archivos de entrada grandes se inicia más rápido que los editores de texto como vi
16. Comando **grep**. grep busca los ARCHIVOS de entrada nombrados(o la entrada estándar si no se nombran archivos, o si se da un solo guión menos ( - ) como nombre de archivo) para líneas que contengan una coincidencia con el PATRÓN dado. De forma predeterminada, grep imprime las líneas coincidentes.s
17. Comando **passwd**. La utilidad passwd se utiliza para actualizar los token (s) de autenticación del usuario . 
18. Comando **du** .estimación del uso del espacio de archivos
19. Comando **reboot**. La llamada reboot () reinicia el sistema, o habilita / deshabilita la pulsación de la tecla de reinicio
20. Comando **halt**. Estos programas permiten al administrador del sistema reiniciar , detener o apagar el sistema.

