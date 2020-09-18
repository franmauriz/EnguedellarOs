---
date: 2020-09-08T07:50:22+02:00
author: Francisco Mauriz Pereira
title: Que es UEFI , GTP y ESP
categories: [Linux,UEFI]
tags: [Linux, instalación,EFI,UEFI]
draft: false
---

Cuando vamos a instalar GNU/Linux , ya sea en una instalación dual con Windows o en una instalación individual, una de las primeras dificultades que nos encontramos es ¿Que es el **UEFI**? ¿es **EFI** o **UEFI**? ¿**MBR** o **GPT**?

Con este pequeño articulo resumen intentare explicar de la forma más sencilla que significan estos términos  para solventar las instalaciones de nuestros sistema favorito del GNU/Linux.

# EFI , UEFI , GPT y ESP

Por la limitaciones de la Bios, se decidió crear una nueva especificación para sustituirla. Y empezó a desarrollarla **Intel**, durante las primeras fases de desarrollo del **Intel Itanium de HP** por los años 90. Debido a que estos procesadores apuntaban alto, las especificaciones del BIOS resultaban muy limitadas, por ello Intel desarrolló inicialmente lo que sería la **IBI *(Intel Boot Initiative)*** que después se paso a llamar **EFI**.

![Intel Itanium de HP](https://hardzone.es/app/uploads-hardzone.es/2019/02/Intel-Itanium-2-Montecito.jpg)

En 2005, Intel pasó a contribuir en **Unified EFI Forum** y pasó a llamarse **UEFI (Unified Extensible Firmware Interface)**. UEFI es una especificación para una interfaz software entre el sistema operativo y el firmware.

## VENTAJAS

1. Arranque y tiempo de reanudación más rápidos.
2. Uso de unidades cifradas gracias al arranque seguro.
3. Admite unidades de disco de un volumen superior a 2 TB.
4. Compatibilidad con BIOS.
5. Soporte completo para GTP. (DESPUES HABLAREMOS DE QUE ES)
6. Puede hacer uso de módulos para extender su funcionalidad.

Con el avance de las tecnologías a la especificación **UEFI** se necesito añadir características que resultaban difíciles de implementar por las limitaciones de la BIOS.

**UEFI** es capaz de acceder a toda la RAM del sistema y acceder a su propia partición en el disco que se llama ESP.

## ESP
**ESP** es un tipo de partición que parte de la especificación **UEFI** y necesita estar formateada en FAT. Aquí se almacenan los cargadores para todos los sistemas operativos instalados en el sistema, drivers usados en el arranque y los módulos que puede ejecutar UEFI directamente.

En caso de que no se encuentre nada en esta ubicación, o el usuario lo haya indicado así, durante el proceso de arranque se buscará en cada dispositivo de almacenamiento con formato FAT32 en busca de un cargador de SO.

Algunas implementaciones de UEFI no siguen el estándar y solamente ejecutan cargadores que pertenezcan a Windows. Además, éste también ubica su cargador en el disco principal en la ruta de los dispositivos extraíbles para forzar el arranque de Windows.

## BOOTEO DEL SISTEMA
Cuando se enciende el equipo, la **UEFI** inicializa el firmware y el hardware de bajo nivel para después cargar sus propios drivers de los dispositivos de **forma paralela**.

Esto supone una gran ventaja en cuanto a velocidad frente a **BIOS**, que carga los drivers de forma secuencial.

Cumplido esto, el gestor de arranque incorporado en la UEFI consulta la configuración para ejecutar el cargador del sistema operativo o el kernel.

Cada sistema operativo debe tener una entrada en la configuración de la UEFI en la que se especifique la ruta al cargador o kernel del SO.

## GPT
El estándar GPT parte de la especificación de UEFI que pretende solucionar los problemas que había con la antigua tabla de particiones MBR.

Cada partición y disco es representado de forma única mediante un GUID (Globally-Unique Identifier) que es un código alfanumérico de un número de 16 bytes. Los GUID se escriben empleando una palabra de cuatro bytes, tres palabras de dos bytes y un bloque de seis bytes, aunque los dos primeros aparecen separados 024DEE41-33E7-11D3-9D69-0008C781F39F.

Podemos identificar el GUID de nuestras particiones con el siguiente comando desde la terminal:

```bash
sudo blkid
```

Nos devolverá el siguiente resultado:

```bash
/dev/sda1: UUID="A571-0F64" TYPE="vfat" PARTUUID="e336f9be-037b-4d4b-be52-72e35aaee9a3"
/dev/sda2: UUID="5fe46ac5-def1-4a0a-a8f2-f6f329a8fe99" TYPE="ext4" PARTUUID="d50545bf-f892-5043-85cb-1e5b8d590935"
/dev/sda3: UUID="272ee5a8-6705-4663-bb4a-ae4ee85926c1" TYPE="ext4" PARTUUID="b90729b7-fc7e-ea47-a63a-6231179d349a"
/dev/sda4: UUID="d7041be0-850d-4024-b8f7-8adb966d66f2" TYPE="swap" PARTUUID="1b8aa2a2-8408-ea4e-91e0-106ca03c8e73"
```

La estructura de GPT sigue usando MBR por cuestiones de compatibilidad. El MBR contiene una única entrada que comprende todo el disco y así se indica que éste usa GPT. Esto previene que sistemas no compatibles con GPT puedan sobrescribir la tabla de particiones.

### BLOQUES GPT
**PRIMER BLOQUE**: se ubica el MBR con una entrada del tipo protective MBR.

**SEGUNDO BLOQUE**: se ubica la cabecera de GPT. Compuesta por:

    - Número de bloques del disco.
    - Su identificador.
    - Número de particiones que podrian crearse.
    - Su ubicación.
    - Tabla de particiones primaria y secundaria.
    - Un Checksum de la cabecera.
    - Tabla de particiones.

**TERCER BLOQUE**: comienza con la tabla de particiones. Cada entrada tiene:

    - Un tamaño de 128 bytes y puede haber un máximo de 128 entradas.
    - En cada una se especifica el GUID del tipo de partición.
    - El GUID identificador de la partición.
    - su primer y último bloque.
    - Atributos de la partición.
    - El nombre que se almacena en Unicode

En los últimos bloques del disco se almacena una copia de la estructura de la GPT.