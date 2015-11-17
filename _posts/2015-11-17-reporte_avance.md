---
layout: post
title:  "Reporte de proyecto"
date:   2015-11-17 09:00:00
author: Enzo y Sebastián
categories: report
---

Reporte primera iteración:

En este informe se dará a conocer el avance realizado en la primera iteración 
La idea del proyecto es implementar una aplicación que permite guardar una serie de comandos  y configuraciones para distintos modelos de robots que funcionen en ROS y poder ocuparlos como atajos, a partir de esta aplicación se desea poder implementar un Teleop general que sea independiente del robot, facilitando así la interacción entre el programador y el robot.
Una reporte más preciso se encuentra en agregar link
En esta iteración la idea fue implementar el núcleo de la aplicación, es decir que la aplicación tuviera capas para poder enviar y recibir una serie de comandos que provienen de una configuración previa que haya sido creada y configurada por el usuario. Para esta aplicación lo que se está considerando como comando es un botón el cual tiene asociado un mensaje de ROS con su determinado tipo y tópico. Este comando también tendrá asociado un valor determinado "rate" el cual permite configurar cuantas veces se quiere que se repita el mensaje.

Para realizar esta aplicación se procedió a trabajar de la siguiente manera:

Determinar cómo guardar un mensaje de ROS

Como se quiere que la aplicación sea capaz de guardar una determinada configuración, para distintos tipos de robots, es necesario poder guardar los distintos comandos que se han creado y poder cargarlos cada vez que se inicia la aplicación o bien que el usuario desee cambiar de dispositivo.
En un principio se tenía pensado usar JSON para poder guardar los mensajes que se van a  enviar, pero en el proceso de investigación de cómo implementar, se descubrió que estos no pueden guardar elementos serializables lo que impedía guardar un mensaje de manera directa. Mientras se buscaba cómo reemplazar esta implementación se encontró la clase RosBag la cual es utilizada por ROS para guardar los mensajes que se quieren enviar. De esta manera se decidió cambiar la opción de JSON por RosBag de esta manera se encontró una forma más fácil de guardar elementos y poder utilizarlos más adelante.

Teniendo ya establecido como guardar los mensajes se crearon un par de funciones "writeBag" y "readBag" para poder cargar un diccionario que contiene una serie de mensajes guardados. Se utilizará un diccionario pues cumple la idea de que se tiene de asociar una determinada llave (botón) a un mensaje determinado.

Envío y Recepción de Mensajes:

Teniendo listo el guardado de mensajes se procedió a crear un test de como poder enviar un mensaje que estaba guardado en un archivo de configuración. La función readBag permite obtener el contenido de una bolsa, para enviar un mensaje y dado que anteriormente se trabajó en los tutoriales de ROS, se implementó un cliente y un servidor de prueba que era capaz de enviar y recibir un mensaje pre-cargado de un archivo de configuración.

Aplicación:
Pudiendo enviar y recibir mensajes se procedió a implementar una función main que cumpliera con ser una version basica de la aplicacion que se quiere implementar.
Esta aplicación tiene una serie de comandos preestablecidos que corresponden al cuerpo de la aplicación.
Lo primero pide la aplicación es poder elegir entre distintas configuraciones de robot previas o diccionarios. Esto se logra teniendo un RosBag distinto para cada configuración, de esta manera, mediante previa selección del usuario se puede escoger sin problema la bolsa que se quiere cargar por lo cual se pueden obtener los comandos asociados a una cierta configuración 

Luego que ya se tiene una cierta configuración el usuario puede ocupar cualquiera de los comandos establecidos o bien poder cambiar la configuración. Para poder realizar cambios existen tres opciones :

Agregar Comando: elegir una tecla disponible (que no tenga otro comando asociado)   y asignarle un comando creado a partir de especificaciones del usuario. Para eso es necesario que se especifique mediante imput los distintos componentes faltantes que componen el comando (mensaje, tipo, tópico y rate).

Eliminar Comando:
Dado un botón ya existente en el diccionario se puede elegir para eliminarlo del diccionario.

Cambiar Comando:
A un comando ya existente, el usuario puede elegir cambiar la tecla a accionar para enviar el mensaje, en un futuro también se desa poder implementar el cambio en el mensaje para que no sea necesario crear un mensaje nuevo cuando se puede cambiar solo un parametro de mensaje.
