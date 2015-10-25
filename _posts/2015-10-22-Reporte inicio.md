---
layout: post
title:  "Reporte de proyecto"
date:   2015-10-22 18:00:00
author: Enzo y Sebastian
categories: report
---
#Proyecto de aporte a Ros : TheTeleop (nombre a definir) 

## Introducción:

  En este post se daran a conocer las especificaciones correspondientes al proyecto a realizar como contribucion a Ros por parte del grupo conformado por Sebastián Ormeño y Enzo Cerfogli, estudiantes de la carrera Ingerieria Civil en Computación de la Universidad de Chile.

  La idea de este proyecto es tomar cierto elemento que pertenece a Ros, ya sea un modulo existente o una nueva idea a implementar y llevarla a cabo de tal manera que mejore el uso a los usuarios, ya sea para los nuevos o para aquellos que ya son experimentados en este ambito.

## Problema

  Al comenzar a trabajar con un robot, independiente del modelo que este sea, uno de los primeras actividades que se realizan es interactuar con el movimiento de este, ya sea el desplazamiento por un determinado sector, mover alguna de las componentes que lo conforman, etc. Para trabajar en este ambito existe el modulo Teleop, el cual es un modulo que permite trabajar con con el movimiento a distancia de un robot.

  Dentro de la experiencia personal que corresponde al grupo, se trabajo utilizando el modulo turtlebot_teleop, el cual permitia mover un robot del mismo modelo a medida que se apretaban determinadas teclas del teclado, podiendo modificar la velocidad en que este avanzaba (tambien se puede hacer funcionar mediante el uso de distintos mandos de consolas pero no se trabajo en este ambito).

  Si bien el modulo cumple su objetivo y es relativamente facil de usar, existen ciertos elementos que no son del todo comodos al momento de su uso o bien se notaron posibles mejoras que de implementarlas facilitarian aun mas funcioanmiento y podrian hacer mas generico su funcionamiento. 

Dentro de estos se pueden mencionar:

--Las teclas vienen predefinidas y no es posible configurarlas dependiendo de como se quieren usar.

--No es posible apretar mas de una tecla al mismo tiempo, esto es poco intuitivo (segun nuestra opinion) y seria mas comodo poder realizar combinaciones de teclas dependiendo de lo que se quiera realizar.

--Una interfaz grafica podria facilitar el uso de la aplicacion, ya sea dando facilidad al momento de realizar las disntintas configuraciones de velocidad  o bien de como usar el modulo.

--El hecho de que haya un teleop distinto para diferentes robots hace que sea poco generico, por lo que una aplicacion mas general podria ser mas comodo para un usuario que usa distintos prototipos o robot.

  Estos factores si bien no son fundamentales para el funcionamiento del modulo, pues bien la gente sigue usando teleop tal cual como se encuentra implementado, la solucion de los aspectos anteriores solo mejoraria la experiencia del usuario y por lo tanto podria hacer que el trabajo que se realize con el sea mas productivo.

## Solución

  Siguiendo con la idea explicada anteriormente, para brindar solucion a los problemas planteados se ha decidido implementar una propia version de teleop, con la particularidad de que esta sea independiente del robot que se quiera utilizar.

  La idea de este nuevo teleop es que el usuario pueda indenpendisarse del modelo que robot que se este usando, con esto utilizando ciertas caracteristicas que son comunes para todos los modelos (que se mueven basicamente), una interfaz de usuario simple y comoda y ciertas especificaciones del usuario, poder tener una aplicacion que permita el movimiento de distintos dispotivos ademas de ser comoda y facil de usar.

Dentro de las funcionalidades que tendra esta nueva aplicacion, se encuentran los siguientes aspectos:

--Posibilidad de elegir el robot a utilizar

--Poder seleccionar una lista de comandos distintos que permitan movimientos

--Poder manejar de manera comoda los distintos parametros como velocidad de giro o de avance.

--Configuracion de teclado y poder recibir mas de un comando de direccion simultaneamente.

--Interfaz grafica que facilite los aspectos anteriores.

## Diseño de la solución

  Con respecto al diseño de la solucion, se tiene planeado proceder en 3 etapas en las que se abordaran distintos aspectos de de la extension a implementar

--La primera etapa consiste en elaborar el core de la aplicación, con esto se refiere al funcionamiento interno de la nueva implementación. Para esto se basara en el siguiente modelo de implementación, cada robot tendra una lista de posibles topicos (particulares o compartidos para cada robot) a los que pueden recibir un mensaje de determinado tipo con distintos argumentos. Con esta razon se va a crear una aplicacion/función en python que sea capas de mandar distintos mensajes a  topicos determinados, luego estas acciones deben ser guardadas de alguna manera (posiblemente en archivos, mediante formato jasons) y poder cargarlas cada vez que sea necesario. El echo de tener los mensajes en formato jason permite guardarlos de una manera estandar, ya sea para escribirlos o leerlos, por lo cual se espera que no sea un problema crear los comandos y que estos funcionen realmente en la aplicación. En esta etapa se trabajara con pruebas sobre un unico modelo de robot, la idea es que si bien se intentara realizar la aplicacion lo mas extendible posible, en esta etapa el factor principal el el funcionamiento, por lo que el tema de que sea multiplataforma pasara a segundo ambito, mientras se enfocara que la aplicacion funcione como se desea y de manera correcta.

--La segunda etapa correspondera a agregar el factor multiplataforma a la aplicacion, con esto se crearan un funcionamiento predeterminado ya sea para trabajar con modelos ya agregados a al aplicacion despues de un determinado uso, o bien, para comenzar a trabajar con un modelo nuevo. Si bien la idea es hacer la aplicacion lo mas independiente del modelo de robot que se quiera manejar, existen casos que diferentes tipos de mensajes no son recividos o las variables pueden cambiar de un caso a otro. De esta manera es necesaria una cierta participacion del usuario al momento de especificar los elementos con que se trabajara, y la idea es que estos no sea necesario especificarlo cada vez que se quiera trabajar.

--La ultima etapa corresponde a crear la interfaz de usuario que contega la funcionalidad de la aplicacion, esto se realizara mediante el uso del framework RQT (lo cual es lo recomendado por ros). Para esto sera necesario trabajar sobre una  interfaz grafica basada en QWidget como lo dice en la pagina de ros. La idea de esta interfaz de usuario es que le permita interacctuar al usuario de la manera mas simple e intuitiva posible. En esta el usuario podra seleccionar el modelo de robot sobre el cual quiere trabajar, poder determinar los mensajes a enviar, especificar el valor de los distintos parametretos que participaran en la accion (velocidad, distancia), ademas de poder tambien cambiar la configuracion a su conveniencia.

## Conclusión

Si bien la aplicacion intentara llevarse a cabo desde cero, se vera el funcionamiento del teleop ya implementado (particurlarmente el del turtlebot y el del PR2) para tener una base sobre la cual partir a nivel de funcionamiento, al igual que examinar ejemplos de proyectos ya  implementados mediante RQT. Se espera que al finalizar la aplicacion se logre implementar todos los aspectos mencionados anteriormente, los avances seran reportados en distintas instancias a traves de post reportanto tambien los posibles errores y dificultades que puedan surgir.





