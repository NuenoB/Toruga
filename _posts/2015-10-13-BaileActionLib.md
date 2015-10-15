---
layout: post
title:  "Baile Tortuga con action Lib"
date:   2015-10-13 18:00:00
author: Enzo y Sebastian
categories: report
---

# Progreso: El baile de la Tortuga(con actionlib)

En esta actividad se pide implementar conjunto de movimientos para el turtlebot mediante la libreria actionlib. Esta basicamente trabaja con modelo cliente-servidor a traves de mensajes que ejecutan una determinada accion.
Para realizar esto primero se procedio a realizar los tutoriales respectivos, donde se vio que para crear las distintas  accciones (con esto se refiere a archivos .action que representa una de objeto que contiene los parametros que envia el cliente) se tienen que modificar archivos manualmente para que estos sepan de la existencia del nuevo objeto creado, lo cual podria perfectamente podria automatizarse.
La primera tarea que se realizo fue implementar un cliente-servidor que desde el cliente se le envia un string y en el servidor lo muestra, esto sirvio para ver el funcionamiento basico de actionlib.
Siguiendo con el trabajo se creo el action "BaileToruga" la cual tiene como parametros 2 ints para la posicion "x" e "y", un valor que hace referencia al angulo de giro y finalmente un string para indicar explicitamente algun otro procedimiento.
Para realizar el baile practicamente se tomo el codigo del programa echo en python para el baile sin actionlib, y se modifico de manera que la posicion entregada por el goal sea el movimiento que se le indica al robot.
De esta manera si uno le da las coordenas (x,y) el robot se movera del punto inicial donde esta a la posición (x,y) en coordenas de robot en linea recta girando primero hacia esa posicion.

[Enlace del Video](CUANDO_EL_ROBOT_ESTE_VIVO)

[Enlace repositorio GIthub](https://github.com/NuenoB/BailaTorugaActionlib)

