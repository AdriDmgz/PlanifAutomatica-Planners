En este documento se recopila información sobre el proceso de instalación y uso de distintos planificadores automáticos que son, relativamente, fáciles de instalar, ya sea por proporcionar un compilado, por estar desarrollados en Java o por poderse ejecutar mediante contenedores Singularity.

# Planificadores Java

## PDDL4J
* URL: https://github.com/pellierd/pddl4j
* Compilado (.JAR): https://github.com/AdriDmgz/PlanifAutomatica-Planners/raw/main/pddl4j-3.8.3.jar

### Instrucciones de instalación/compilación
Descargar código fuente de la URL dada y compilar código fuente usando herramientas Java. Realicé la compilación sin anotar el proceso, investigando el proyecto y usando herramientas según vi necesario (Visual Code, Gradle, javac, etc.). La compilación se basaba en el uso de Gradle y del fichero gradlew.bat. La compilación incluía una fase de test que no finalizaba, aunque luego descubrí que no era necesario que esta finalizase ya que previamente a los test ya se había generado el fichero .jar en la carpeta ./build/libs del proyecto. Se aceptan pull-request para detallar este proceso.

### Instrucciones de uso
Invocar por consola con ``java -jar ./pddl4j-3.8.3.jar`` para obtener entrada esperada y opciones de ejecución. También puede añadirse como planificador a plugin PDDL de Visual Studio Code con integración automática, indicando únicamente la ruta del .jar. Ver instrucciones del plugin para más información.

## JavaFF (2002 FF Original / 2015 JavaFF V1.0 / 2018 JavaFF V2.1)
* URL: https://github.com/tonyallard/JavaFF (original)
* URL: https://github.com/dpattiso/javaff (versión 2.1)
* Compilado (.JAR): https://github.com/AdriDmgz/PlanifAutomatica-Planners/raw/main/javaff.jar (versión 2.1)

### Instrucciones de instalación/compilación
Descargar código fuente de la URL dada (versión 2.1), abrir con Visual Studio Code para compilar ficheros .class, y, por último, compilar a .JAR mediante javac, usando las opciones del comando necesarias para configurar el CLASSPATH a la carpeta ./bin donde se encuentran los .class y al jgrapht-jdk1.6.jar que está en la carpeta ./lib/jgrapht-0.8.2 del proyecto. Fue necesario usar una versión relativamente antigua del JDK para realizar este proceso, ya que en algún punto (al compilar o al generar el .jar) daba error al hacerlo con la última versión. Se aceptan pull-request para detallar este proceso.

### Instrucciones de uso
Compilar/descargar fichero .JAR e invocar por consola con ``java -jar ./javaff.jar`` para obtener entrada esperada y opciones de ejecución.

## SapaReplan (2002)
* URL: https://rakaposhi.eas.asu.edu/sapa.html/
* Compilado (.JAR): https://github.com/AdriDmgz/PlanifAutomatica-Planners/raw/main/SapaReplan.jar

### Instrucciones de instalación/compilación
Fichero .jar proprocionado por autores en la web.

### Instrucciones de uso

Descargar fichero .JAR e invocar por consola con ``java -jar ./SapaReplan.jar`` para obtener entrada esperada y opciones de ejecución.

# Planificadores para Ubuntu

## SATPLAN
* URL: https://www.cs.rochester.edu/u/kautz/satplan/

### Instrucciones de instalación/compilación
Compilado ejecutable en Ubuntu proporcionado por autores en la web del planificador.

### Instrucciones de uso

Descargar compilado en Ubuntu y descomprimir. El compilado incliye varios ficheros, ya que el planificador es modular e incluye distintos 'solvers'. Ejecutar con ./satplan para obtener entrada esperada y opciones de ejecución. Usar opción ``-solver siegue`` para usar el mismo solver que en IPC 2004.
````
./satplan -solver siege -domain fichero-dominio.pddl -problem fichero-problema.pddl 
````

## LPG-TD (2004)
* URL: https://lpg.unibs.it/lpg/index.html
* Compilado (Ubuntu): https://github.com/AdriDmgz/PlanifAutomatica-Planners/raw/main/lpg-td.zip

### Instrucciones de instalación/compilación
Compilado ejecutable en Ubuntu proporcionado por autores en el siguiente enlace: https://lpg.unibs.it/lpg/download-lpg-td.html. En la web se proporciona también una versión más antigua compilada para Windows 2000, pero en Windows 10 no solo no funciona, si no que provoca un bucle infinito de procesos de ejecución en segundo plano, obligando a reiniciar el sistema para poder detenerlos.

### Instrucciones de uso
Descargar compilado en Ubuntu y descomprimir. Entrar en carpeta y dar permisos de ejecución con ``sudo chmod 755 ./lpg-td``. Ejecutar con ``./lpg-td`` para obtener entrada esperada y opciones de ejecución.

## SGPlan (2007)
* URL: https://wah.cse.cuhk.edu.hk/wah/programs/SGPlan/
* Compilado (Ubuntu): https://github.com/AdriDmgz/PlanifAutomatica-Planners/raw/main/sgplan522.zip

### Instrucciones de instalación/compilación
Compilado ejecutable en Ubuntu proporcionado por autores en la web del planificador.

### Instrucciones de uso
Descargar compilado en Ubuntu y descomprimir. Entrar en carpeta y dar permisos de ejecución con ``sudo chmod 755 ./sgplan522``. Ejecutar con ``./sgplan522`` (o versión descargada) para obtener entrada esperada y opciones de ejecución.

## Optic (2012)
* URL: https://nms.kcl.ac.uk/planning/software/optic.html
* Compilado (Ubuntu): https://github.com/AdriDmgz/PlanifAutomatica-Planners/raw/main/optic-clp.zip

### Instrucciones de instalación/compilación
En la web se proporciona versión parcialmente compilada descargable a través del siguiente enlace: http://sourceforge.net/projects/tsgp/files/OPTIC/optic-clp.tar.bz2/download. Para terminar de compilarla, lo más sencillo es hacerlo con Ubuntu 14, dado que es necesario un compilador de C++ antiguo. En esta versión del SSOO bastará con instalar g++ con el comando ```sudo apt-get install g++``` y posteriormente terminar la compilación de Optic ejecutando el comando ```make``` en la carpeta descargada. El compilado puede ser usado posteriormente en versiones actuales de Ubuntu.

### Instrucciones de uso
Descargar compilado en Ubuntu y descomprimir. Entrar en carpeta y dar permisos de ejecución con ``sudo chmod 755 ./optic-clp``. Ejecutar con ``./optic-clp`` para obtener entrada esperada y opciones de ejecución.

# Planificadores ejecutables vía Singularity

## Singularity

## FastDownward (2004) y planificadores derivados (2011)

````
singularity pull --name downward.sif shub://aibasel/downward
singularity run downward.sif --alias lama-first ./dominio.pddl .problema.pddl
singularity run downward.sif --show-aliases
````
