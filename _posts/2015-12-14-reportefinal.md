---
layout: post
title:  "Reporte final de proyecto"
date:   2015-12-14 09:00:00
author: Enzo y Sebastián
categories: report
---

#Reporte Final

Este post corresponde a el informe final del curso Taller de Ingenieria en Software para Robots y corresponde a la continuación de los siguientes post.

[Segundo reporte](http://nuenob.github.io/Toruga/report/2015/11/17/reporte_avance.html)

[Primer reporte](http://nuenob.github.io/Toruga/report/2015/10/22/Reporte%20inicio.html)

##General Teleop

Una herramienta de ros para controlar el movimiento de cualquier robot, bajo la idea de que el usuario va a poder configurar los mensajes necesarios para poder mandar a su robot.

La idea de este nuevo teleop es que el usuario pueda independizarse del modelo que robot que se esté usando, con esto utilizando ciertas características que son comunes para todos los modelos (que se mueven básicamente), una interfaz de usuario simple y cómoda y ciertas especificaciones que brindara el usuario, poder tener una aplicación que permita el movimiento de distintos dispositivos. La aplicacion tambien esta abierta para poder guardar atajos o comandos no relacionados 100% con el movimiento del robot, de tal manera de poder reutilizar cierta configuración importante sin tener que escribir el comando en reiteradas ocasiones. 

Disclaimer: Todo esto fue probado en un Ubuntu 14.04, ROS jade.

####Como instalar ?

1. Descarga la aplicación desde [github](https://github.com/NuenoB/TheTeleop)

1. Copialo a tu `catkin_workspace/src`

1.  Abre una terminal

1. Ejecuta `catkin_make` en catkin_workspace

####Cómo Ocupar ?

Para ocupar la aplicación, primero  se debe ejecutar rosRun para lanzar ros (daaaa), luego se debe ejecutar el siguiente comando :

`Rqt the_teleop theteleop.py`

Lo cual mostrará la interfaz de la aplicación  y esta estará lista para usar.

También se puede usar directamente desde rqt

1. Ejecutan en una terminal `rqt`

1. En el tab de plugins buscar el General Teleop 

Al ejecutar la aplicación el usuario será capaz de ver la siguiente interfaz, la cual funciona de la siguiente manera:

![GUI principal]({{site.baseurl}}/assets/mainUI.jpg)

Para crear una nueva configuración, se debe clickear el botón “new Robot” el cual abrirá una nueva ventana que permitirá al usuario ingresar el nombre de la nueva configuración (siempre y cuando el nombre no pertenezca a un archivo que ya existe).  Realizado lo anterior, se procede apretar el botón “Crear” el cual termina por crear una nueva configuración lista para trabajar.

Teniendo una configuración creada, esta aparecera disponible para ser seleccionada en el “menú” que aparece en la parte superior de la interfaz. Despues de seleccionarla se debe proceder a presionar el botón “load” el cual cargará la configuración y todos los comandos que en ella se encuentren.

Siguiendo con la administración de configuraciones para poder eliminar una determinada configuración se tiene que presionar la opción “delete” la cual eliminará la configuración que está cargada. Al presionar el botón esté procederá a mostrar un mensaje para confirmar la selección. Si se elimina la configuración se procede a dejar como configuración actual la primera la de la lista.

En el centro de la aplicación estará disponible una tabla donde se podrán ver todos los comandos de la configuración, para agregar uno nuevo se debe hacer click en la opción “new command” la cual abrirá una ventana con los campos a llenar para generar un nuevo comando. Los campos a llenar corresponden a tecla de la configuración, mensaje, tipo, rate, tópico.

Para reasignar la tecla que está asignada a un comando se tiene que acceder al menú de “change setting” haciendo click en el botón de mismo nombre, en el se abrirá una interfaz que permite seleccionar una tecla que ya tiene funcionalidad asignada y reemplazarla por otra.

Ahora si se quiere borrar, basta hacer click en la opción delete command que permite elegir un comando y borrarlo de la configuración.

Ahora para utilizar la aplicación, basta hacer click en el sector que dice “bla”, donde la aplicación obtendrá el comando asociado a la tecla y enviará el mensaje correspondiente.


####Como extender 

La forma en que fue implementada esta aplicación permite ver un cierto grado de independencia entre las distintas funcionalidades que existen entre las funciones que realiza cierto comando. Si se quiere agregar una funcionalidad o bien modificar, se debe acceder a la clase correspondiente a cada interfaz creada donde se encuentra implementada su respectiva lógica, ya sea los comandos asociados a los distintos botones o bien ciertas funciones que se usan para sostener la lógica de la aplicación.

Si se quiere agregar un nuevo botón, que tenga una respectiva función, o bien se quiere agregar una nueva interfaz de usuario que contenga cierta lógica del programa , basta modificar el archivo la clase que representa la interfaz (ya sea directamente en la clase de python o bien el archivo .ui mediante un editor como QTdesigner por ejemplo).

La forma en que se trabajo para implementar las distintas ventanas de usuario consiste en diseñar la interfaz mediante QTdesigner, luego compilarla con el comando … , esto generará un archivo de python que representa la interfaz; luego para crear la lógica de la interfaz se procede a crear un nuevo archivo que contendrá las funciones respectivas no sin antes importar la clase de la interfaz creada.

Notar que en las interfaces que exista el espacio Qedit especial que solo permite ingresar un boton a la vez, es necesario abrir el archivo .py creado anteriormente y reemplazar en la línea donde se crea el objeto QlineEdit a un QLineEdit_keyDetecter y además importar la clase en el archivo.

Un ejemplo de esto es el archivo [v4.py](https://github.com/NuenoB/TheTeleop/blob/master/src/the_teleop/v4.py)
La lógica de la aplicación principal se encuentra en el archivo TheTeleop2.py, el resto de las funcionalidades están en los archivos que se llaman igual a la interfaz.


####Enlaces:

[Repositorio](https://github.com/NuenoB/TheTeleop)

####Contacto:
rossengroup@gmail.com


