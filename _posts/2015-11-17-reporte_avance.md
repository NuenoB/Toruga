---
layout: post
title:  "Reporte de proyecto"
date:   2015-11-17 09:00:00
author: Enzo y Sebastián
categories: report
---

Reporte primera iteración:

En este informe se dara a conocer el avance realizado en la primera iteracion 
La idea del proyecto es implementar una aplicacion que permita guardar una serie de comandos  y configuraciones para distintos modelos de robots que funcionen en ROS y poder ocuparlos como atajos, a partir de esta aplicacion se desea poder implementar un Teleop general que sea independiente del robot, facilitando asi la interaccion entre el programador y el robot.

En esta iteracion la idea fue implementar el nucleo de la aplicacion, es decir que la aplicacion fuera capas de poder enviar  y recivir una serie de comandos que provienen de una configuracion previa que haya sido creada y configurada por el usuario. Para esta aplicacion lo que se esta considerando como comando es un boton el cual tiene asociado un mensaje de ROS con su determinado tipo y topico  determinado. Este comando tambien tendra asociado un valor determinado "rate" el cual permite configurar cuantas veces se quiere que se repita el mensaje.

Para realizar esta aplicacion se procedio a trabajar de la siguiente manera:

Determinar como guardar un mensaje  de ROS

Como se quiere que la apliacion sea capas de guardar una determianada configuracion, para distintos tipos de robots, es necesario poder guardar los dinstintos comandos que se han creado y poder cargarlos cada vez que se inicia la aplicacion o bien que el usuario desee cambiar de dispositivo
En  un principio se tenia pensado usar JSON para poder guardar los mensajes que se van a  enviar, pero en el proceso de investigacion de como implementar , se averiguo que estos no pueden guardar elementos serializables  lo que impedira guardar un mensaje de manera directa. Mientras se buscaba como reemplazar esta implementacion se encontro la clase RosBag la cual es utilizada por ROS para guardar los mensajes que se quieren enviar. De esta manera se decidio cambiar la opcion de JSON por RosBag de esta manera se encontro una forma mas facil de guardar elementos y poder utilizarlos más adelante.
Teniendo ya establecido como guardar los mensajes se crearon un par de funciones "writeBag"  y "rosBag" para poder cargar un diccionario que contiene una serie de mensajes guardados. Se utilizara un diccionario pues cumple la idea de que se tiene de asociar una determinada llave (boton) a un mensaje determinado.


Envio y Recepcion de Mensajes:
Teniendo listo el guardado de mensajes se procedio a probar como poder enviar un mensaje que estaba guardado en un archivo de configuracion. La funcion readBag permitia obtener el contenido de una bolsa, de esta manera enviar y recibir un mensaje paso a ser un problema que ya se habia trabajado en ROS que corresponde a crear un cliente y un servidor que sean capas de enviar y recibir un mensaje. Siguiendo con eso se implementaron un cliente y un servidor de prueba que era capas de enviar y recibir un mensaje pre-cargado en un archivo de configuracion.

Aplicacion:

Dificultades:


