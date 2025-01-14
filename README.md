# PPS-Unidad1Actividad1-albertoVG
Actividad 1 de la Unidad 1 de Puesta en Producción Segura. Tabajaremos con los Entornos de Desarrollo

Tenemos varios objetivos:

> [Crear un entorno de desarrollo Eclipse con docker](#Eclipse-Docker)

> [Instalar extensiones en un IDE](#Instalar-extensiones)

> [Probar los entornos de Desarrollo](#Prueba-entornos) 
---
## Eclipse Docker

En [este enlace](https://hub.docker.com/r/dockeruc/eclipse) puedes encontrar podemos crear un contenedor docker con un entorno IDE Eclipse

Lee bien las instrucciones y ten en cuenta que tienes que hacer varias operaciones. Las que tienes a continuación son de un entorno Linux:

1. Crear las carpetas necesarias:
~~~
sudo mkdir -p  $HOME/docker/eclipse/datos
sudo chown -R $(whoami) $HOME/docker/eclipse
sudo chgrp -R $(whoami) $HOME/docker/eclipse
~~~

![](Imagenes/Imagen1.png)

2. Configurar el entorno gráfico 

~~~
export DISPLAY=:0
startxwin -- -listen tcp &
xhost + 
~~~

![](Imagenes/Imagen2.png)

3. Lanzar el contenedor

~~~
sudo docker run -ti --rm \
           -e DISPLAY=$DISPLAY \
	       -e artifactory_host='IP:PUERTO'\
		   --name eclipse \
           -v /tmp/.X11-unix:/tmp/.X11-unix \
           -v `pwd`:/workspace \
           -v $HOME/docker/eclipse/datos:/home/developer \
           dockeruc/eclipse	

~~~
 
![](Imagenes/Imagen3)

![](Imagenes/Imagen4)

![](Imagenes/Imagen5)


> __Explica el comando docker que has utilizado__

Este comando de Docker inicia un contenedor con Eclipse configurado para usarse con interfaz gráfica.

   --rm: El contenedor se elimina automáticamente al cerrarlo.

   -ti: Permite interactividad con el terminal.

   -e DISPLAY=$DISPLAY: Permite usar la pantalla del host para aplicaciones gráficas.

   -v /tmp/.X11-unix:/tmp/.X11-unix: Comparte los sockets de X11 para que el contenedor pueda mostrar la interfaz gráfica.

   -v $(pwd):/workspace: Monta el directorio actual del host como /workspace en el contenedor.

   -v $HOME/docker/eclipse/datos:/home/developer: Monta un directorio del host para persistir datos del contenedor.

   dockeruc/eclipse: Es la imagen de Docker utilizada para ejecutar Eclipse.


## Instalar extensiones

Las extensiones de un IDE nos van a facilitar la labor de programar, hacer más flexible nuestro IDE, además de hacer nuestros código más seguro.
Tenemos muchas extensiones, tanto para lenguajes de programación específicos como para el IDE.

__Las siguientes operaciones las puedes hacer desde el entorno Eclipse que hemos creado o puedes utilizar el IDE que prefieras en tu equipo__
>__Busca cuáles son las mejores extensiones de eclipse para programadores y las añades desde la tienda de tu IDE__
>__ Busca y escribe para qué sirven estos plugins: Checkstyle, Sonar Lint.__
>__Instala los plugins y complementos que has encontrado. Además busca e instala los plugins Checkstyle y Sonar Lint.__

Estos son algunas de las extensiones que tengo instaladas en el Visual Studio Code
![](Imagenes/Imagen6)
![](Imagenes/Imagen7)
![](Imagenes/Imagen8)
![](Imagenes/Imagen9)
![](Imagenes/Imagen10)
![](Imagenes/Imagen11)


## Prueba entornos

El entorno de desarrollo nos sirve para crear nuestras aplicaciones y además podemos comprobar los errores que tienen, problemas de seguridad, etc. por lo que desde allí vamos a poder corregirlos.
>__Descarga el código fuente de un proyecto java o python: compila, enlaza y ejecutaló. Tienes algunos ejemplos en la carpeta Sources de este repositorio__
>__Utiliza las herramientas de depuración de Eclipse o Netbeans para depurar el proyecto, y las diferentes extensiones para ver información, problemas, etc.__

---
## ENTREGA
>__Crea un repositorio  con nombre PPS-Unidad1Actividad1-Tu nombre que contenga las respuestas a las preguntas y las evidencias de que has realizado las operaciones indicadas.__

>__Sube a la plataforma, tanto el repositorio comprimido como la dirección a tu repositorio de Github.__
