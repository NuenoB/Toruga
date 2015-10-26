---
layout: post
title:  "Reporte de proyecto"
date:   2015-10-22 18:00:00
author: Enzo y Sebastian
categories: report
---
#Proyecto de aporte a Ros : TheTeleop (nombre a definir) 

## Introducción:

  En este post se darán a conocer las especificaciones correspondientes al proyecto a realizar como contribucion a Ros por parte del grupo conformado por Sebastián Ormeño y Enzo Cerfogli, estudiantes de la carrera Ingeniera Civil en Computación de la Universidad de Chile.

  La idea de este proyecto es tomar cierto elemento que pertenece a Ros, ya sea un modulo existente o una nueva idea a implementar y llevarla a cabo de tal manera que mejore el uso a los usuarios, ya sea para los nuevos o para aquellos que ya son experimentados en este ámbito.

## Problema

  Al comenzar a trabajar con un robot, independiente del modelo que este sea, uno de los primeras actividades que se realizan es interactuar con el movimiento de este, ya sea el desplazamiento por un determinado sector, mover alguna de las componentes que lo conforman, etc. Para trabajar en este ámbito existe el modulo Teleop, el cual es un modulo que permite trabajar con con el movimiento a distancia de un robot.

  Dentro de la experiencia personal que corresponde al grupo, se trabajo utilizando el modulo turtlebot_teleop, el cual permitía mover un robot del mismo modelo a medida que se apretaban determinadas teclas del teclado, pudiendo modificar la velocidad en que este avanzaba (también se puede hacer funcionar mediante el uso de distintos mandos de consolas pero no se trabajo en este ámbito).

  Si bien el modulo cumple su objetivo y es relativamente fácil de usar, existen ciertos elementos que no son del todo cómodos al momento de su uso o bien se notaron posibles mejoras que de implementarlas facilitarían aun mas funcionamiento y podrían hacer mas genérico su funcionamiento. 

Dentro de estos se pueden mencionar:

--Las teclas vienen predefinidas y no es posible configurarlas dependiendo de como se quieren usar.

--No es posible apretar mas de una tecla al mismo tiempo, esto es poco intuitivo (según nuestra opinión) y seria mas cómodo poder realizar combinaciones de teclas dependiendo de lo que se quiera realizar.

--Una interfaz gráfica podría facilitar el uso de la aplicación, ya sea dando facilidad al momento de realizar las distintas configuraciones de velocidad  o bien de como usar el modulo.

--El hecho de que haya un teleop distinto para diferentes robots hace que sea poco genérico, por lo que una aplicación mas general podría ser mas cómodo para un usuario que usa distintos prototipos o robot.

  Estos factores si bien no son fundamentales para el funcionamiento del modulo, pues bien la gente sigue usando teleop tal cual como se encuentra implementado, la solución de los aspectos anteriores solo mejoraría la experiencia del usuario y por lo tanto podría hacer que el trabajo que se realice con el sea mas productivo.

## Solución

  Siguiendo con la idea explicada anteriormente, para brindar solución a los problemas planteados se ha decidido implementar una propia versión de teleop, con la particularidad de que esta sea independiente del robot que se quiera utilizar.

  La idea de este nuevo teleop es que el usuario pueda independizarse del modelo que robot que se este usando, con esto utilizando ciertas características que son comunes para todos los modelos (que se mueven básicamente), una interfaz de usuario simple y cómoda y ciertas especificaciones del usuario, poder tener una aplicación que permita el movimiento de distintos dispositivos ademas de ser cómoda y fácil de usar.

Dentro de las funcionalidades que tendrá esta nueva aplicación, se encuentran los siguientes aspectos:

--Posibilidad de elegir el robot a utilizar

--Poder seleccionar una lista de comandos distintos que permitan movimientos

--Poder manejar de manera cómoda los distintos parámetros como velocidad de giro o de avance.

--Configuración de teclado y poder recibir mas de un comando de dirección simultáneamente.

--Interfaz gráfica que facilite los aspectos anteriores.

## Diseño de la solución

  Con respecto al diseño de la solución, se tiene planeado proceder en 3 etapas en las que se abordaran distintos aspectos de de la extensión a implementar

--La primera etapa consiste en elaborar el core de la aplicación, con esto se refiere al funcionamiento interno de la nueva implementación. Para esto se basara en el siguiente modelo de implementación, cada robot tendrá una lista de posibles tópicos (particulares o compartidos para cada robot) a los que pueden recibir un mensaje de determinado tipo con distintos argumentos. Con esta razón se va a crear una aplicación/función en python que sea capas de mandar distintos mensajes a  tópicos determinados, luego estas acciones deben ser guardadas de alguna manera (posiblemente en archivos, mediante formato JSON) y poder cargarlas cada vez que sea necesario. El echo de tener los mensajes en formato JSON permite guardarlos de una manera estándar, ya sea para escribirlos o leerlos, por lo cual se espera que no sea un problema crear los comandos y que estos funcionen realmente en la aplicación. En esta etapa se trabajara con pruebas sobre un único modelo de robot, la idea es que si bien se intentara realizar la aplicación lo mas extensible posible, en esta etapa el factor principal el el funcionamiento, por lo que el tema de que sea multi-plataforma pasara a segundo ámbito, mientras se enfocara que la aplicación funcione como se desea y de manera correcta.

--La segunda etapa corresponderá a agregar el factor multi-plataforma a la aplicación, con esto se crearan un funcionamiento predeterminado ya sea para trabajar con modelos ya agregados a al aplicación después de un determinado uso, o bien, para comenzar a trabajar con un modelo nuevo. Si bien la idea es hacer la aplicación lo mas independiente del modelo de robot que se quiera manejar, existen casos que diferentes tipos de mensajes no son recibidos o las variables pueden cambiar de un caso a otro. De esta manera es necesaria una cierta participación del usuario al momento de especificar los elementos con que se trabajara, y la idea es que estos no sea necesario especificarlo cada vez que se quiera trabajar.

--La ultima etapa corresponde a crear la interfaz de usuario que contenga la funcionalidad de la aplicación, esto se realizara mediante el uso del framework RQT (lo cual es lo recomendado por ros). Para esto sera necesario trabajar sobre una  interfaz gráfica basada en QWidget como lo dice en la pagina de ros. La idea de esta interfaz de usuario es que le permita interactuar al usuario de la manera mas simple e intuitiva posible. En esta el usuario podrá seleccionar el modelo de robot sobre el cual quiere trabajar, poder determinar los mensajes a enviar, especificar el valor de los distintos parámetros que participaran en la acción (velocidad, distancia), ademas de poder también cambiar la configuración a su conveniencia.

## Conclusión

Si bien la aplicación intentara llevarse a cabo desde cero, se vera el funcionamiento del teleop ya implementado (particularmente el del turtlebot y el del PR2) para tener una base sobre la cual partir a nivel de funcionamiento, al igual que examinar ejemplos de proyectos ya  implementados mediante RQT. Se espera que al finalizar la aplicación se logre implementar todos los aspectos mencionados anteriormente, los avances serán reportados en distintas instancias a través de posts reportando también los posibles errores y dificultades que puedan surgir. Cualquier duda o sugerencia hacia el proyecto sera bien recibida por los miembros del equipo  y se espera que al finalizar el proyecto, este se vuelva un aporte útil al funcionamiento de ros.

Contacto:

##Enlaces relacionados:






