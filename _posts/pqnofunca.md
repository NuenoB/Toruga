---
layout: post
title:  "Reporte: Por que no funciona."
date:   2015-09-24 17:00:00
author: Enzo y Sebastian
categories: Reporte
---
##Reporte: Por que no funciona.

En esta actividad se quiere realizar un analisis sobre un bug presente al trabajar con gazibo, simulador de turtlebot de ros.
El error consiste en que al realizar una modificacion en las variables de entorno para cambiar la version del turtlebot, existio un pŕoblema con teleop pues los comandos ingresados no generaban efecto en el simulador, es decir, el turtlebot no se movia.
Para corregir este error, se trator de abordar el problema de dos maneras.

###Primera manera: comparar con el sano

>En esta ocacion se tiene un modelo que funciona correctamente (que corresponde a la version sin modificaciones), la idea de esto es comparar la simulacion que falla con la que funciona y ver donde esta el error.
>Mediante el comando rqt_graph se realizo la comparacion entre los modelos y sin mayor problema se vio que en el modelo que falla, el nodo gazebo no estaba comunicado con teleop (cosa que si ocurre en el modelo que funciona).
>Este metodo fue efectivo pues se tenia una version que funcionaba, pero esto no siempre es posible. Por esta razon se busco otra manera de encontrar que nos llevo al metodo dos.

![Modelo que funciona]({{site.baseurl}}/assets/week-progress/funca.jpg)

![Modelo que no funciona]({{site.baseurl}}/assets/week-progress/nofunca.jpg)

###Segunda manera: Debugging

Suponiendo que no se tiene conocimiento del error, si el simulador no se mueve puede deverse a que el robot no escucha o bien, teleop no envia las señales.
Para chequear esto, se analizo por separado los nodos para  ver cual de estos tenian el problema.
En el caso de teleop, primero se reviso el nodo con rosnode lo cual nos permitio encontrar el topico que publica, luego con rostopic usamos el comando echo para ver si el nodo teleop estaba publicando en el topico encontrado. Lo anterior si realizaba correctamente por lo cual el problema no estaba en teleop.
Revisamos los nodos subcritos a teleop dado que este si estaba enviando mensajes, luego de revisar la la lista de topicos conectados a teleop notamos que no se encontraba el topico de gazebo ni con intermediarios, lo cual nos llevo a revisar con rosnode a gazebo para confirmar la suspechado, el cual solo estaba conectado con si mismo.

Al termiar el analicis se puede afirmar cual es el error:
No hay conecion entre gazebo y teleop
Lo cual se puede arreglar implentando un nodo que sirva de intermediario entre ambos nodos que deberian usar las correctos tipos de los nodos.
Esto se logro gracias a las herramientas de ros en particular: rqt, rostopic, rosnode, roslist. Los cuales nos permitieron revisar si existia una conexion, ademnas de  ver el estado y lo que esta haciendo cada nodo.
Fue dificil comprender las interaciones entre los nodo por el exeso de informacion que da cada comando, como critica que rqt_graph no entrega la informacion clara (Palabra sobrepuestas, sobre-representacion de nodos)