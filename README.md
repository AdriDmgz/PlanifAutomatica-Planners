En este documento se recopila información sobre el proceso de instalación y uso de distintos planificadores automáticos que se utilizarán en los laboratorios.

# Planificadores para Ubuntu

## Fast Forward (FF)
* URL (FF): <a href="https://fai.cs.uni-saarland.de/hoffmann/ff.html" target="_blank">https://fai.cs.uni-saarland.de/hoffmann/ff.html</a>
* Compilado (Ubuntu): <https://github.com/AdriDmgz/PlanifAutomatica-Planners/raw/main/ff.tar.xz>

### Instrucciones de instalación/compilación
Descargar código fuente de la web y compilar mediante gcc en Ubuntu:
````
gcc -c *.c
gcc -o ff *.o
````
Es posible que sea necesario añadir opciones adicionales al compilador  o instalar dependencias, según indiquen los errores en la compilación.

### Intrucciones de ejecución
Descargar compilado en Ubuntu y descomprimir. Ejecutar con ``./ff`` para obtener entrada esperada y opciones de ejecución.

## Metric-FF
* URL (FF): <a href="https://fai.cs.uni-saarland.de/hoffmann/metric-ff.html" target="_blank">https://fai.cs.uni-saarland.de/hoffmann/metric-ff.html</a>
* Compilado (Ubuntu): <https://github.com/AdriDmgz/PlanifAutomatica-Planners/raw/main/metricff.tar.xz>

### Instrucciones de instalación/compilación
Descargar código fuente de la web y compilar mediante gcc en Ubuntu:
````
gcc -c *.c
gcc -o metricff *.o
````
Es posible que sea necesario añadir opciones adicionales al compilador o instalar dependencias, según indiquen los errores en la compilación.

### Intrucciones de ejecución
Descargar compilado en Ubuntu y descomprimir. Ejecutar con ``./metricff`` para obtener entrada esperada y opciones de ejecución.

## SATPLAN
* URL: <a href="https://www.cs.rochester.edu/u/kautz/satplan/" target="_blank">https://www.cs.rochester.edu/u/kautz/satplan/</a>
* Compilado (Ubuntu): <https://github.com/AdriDmgz/PlanifAutomatica-Planners/raw/main/satplan.tar.xz>


### Instrucciones de instalación/compilación
Compilado ejecutable en Ubuntu proporcionado por autores en la web del planificador.

### Instrucciones de uso

Descargar compilado en Ubuntu y descomprimir. El compilado incliye varios ficheros, ya que el planificador es modular e incluye distintos 'solvers'. Ejecutar con ``./satplan`` para obtener entrada esperada y opciones de ejecución. Usar opción ``-solver siege`` para usar el mismo solver que en IPC 2004.
````
./satplan -solver siege -domain fichero-dominio.pddl -problem fichero-problema.pddl 
````

## LPG-TD
* URL: <a href="https://lpg.unibs.it/lpg/index.html" target="_blank">https://lpg.unibs.it/lpg/index.html</a>
* Compilado (Ubuntu): <https://github.com/AdriDmgz/PlanifAutomatica-Planners/raw/main/lpg-td.tar.xz>

### Instrucciones de instalación/compilación
Compilado ejecutable en Ubuntu proporcionado por autores en el siguiente enlace: https://lpg.unibs.it/lpg/download-lpg-td.html. En la web se proporciona también una versión más antigua compilada para Windows 2000, pero en Windows 10 no solo no funciona, si no que provoca un bucle infinito de procesos de ejecución en segundo plano, obligando a reiniciar el sistema para poder detenerlos.

### Instrucciones de uso
Descargar compilado en Ubuntu y descomprimir. Ejecutar con ``./lpg-td`` para obtener entrada esperada y opciones de ejecución.

## SGPlan 4 y SGPlan 5
* URL: <a href="https://wah.cse.cuhk.edu.hk/wah/programs/SGPlan/" target="_blank">https://wah.cse.cuhk.edu.hk/wah/programs/SGPlan/</a>
* Compilado SGPlan 4.0 (Ubuntu): <https://github.com/AdriDmgz/PlanifAutomatica-Planners/raw/main/sgplan40.tar.xz>
* Compilado SGPlan 5.2.2 (Ubuntu): <https://github.com/AdriDmgz/PlanifAutomatica-Planners/raw/main/sgplan522.tar.xz>

### Instrucciones de instalación/compilación
Compilado ejecutable en Ubuntu proporcionado por autores en la web del planificador.

### Instrucciones de uso
Descargar compilado en Ubuntu y descomprimir. Ejecutar con ``./sgplan40`` (o versión descargada) para obtener entrada esperada y opciones de ejecución.

## Optic
* URL: <a href="https://nms.kcl.ac.uk/planning/software/optic.html" target="_blank">https://nms.kcl.ac.uk/planning/software/optic.html</a>
* Compilado (Ubuntu): <https://github.com/AdriDmgz/PlanifAutomatica-Planners/raw/main/optic-clp.tar.xz>

### Instrucciones de instalación/compilación
En la web se proporciona versión parcialmente compilada descargable a través del siguiente enlace: http://sourceforge.net/projects/tsgp/files/OPTIC/optic-clp.tar.bz2/download. Para terminar de compilarla, lo más sencillo es hacerlo con Ubuntu 14, dado que es necesario un compilador de C++ antiguo. En esta versión del SSOO bastará con instalar g++ con el comando ```sudo apt-get install g++``` y posteriormente terminar la compilación de Optic ejecutando el comando ```make``` en la carpeta descargada. El compilado puede ser usado posteriormente en versiones actuales de Ubuntu.

### Instrucciones de uso
Descargar compilado en Ubuntu y descomprimir. Ejecutar con ``./optic-clp`` para obtener entrada esperada y opciones de ejecución.

# Planificadores ejecutables vía Singularity

## Singularity

Instalar última versión de Singularity siguiendo instrucciones: <a href="https://sylabs.io/guides/3.9/user-guide/quick_start.html" target="_blank">https://sylabs.io/guides/3.9/user-guide/quick_start.html</a>

## FastDownward y derivados
* URL: <a href="https://www.fast-downward.org/HomePage" target="_blank">https://www.fast-downward.org/HomePage</a>

### Instrucciones de instalación/compilación

Tras instalar Singularity, descargar container de FastDownward: 

````
singularity pull --name downward.sif shub://aibasel/downward
````
### Instrucciones de uso

Una vez descargado, Singularity permite ejecutar el fichero .sif directamente, como en los siguientes ejemplos:
````
./downward.sif
./downward.sif --show-aliases
./downward.sif --alias lama-first ./dominio.pddl .problema.pddl
````
Ejecutar sin opciones para ver entrada esperada y opciones de ejecución. Mediante opción ``--show-aliases`` se pueden consultar configuraciones predefinidas del planificador, ya que es modular y tiene gran cantidad de configuraciones. Consultar web del planificador para más información.

# Planificadores Java

## PDDL4J
* URL: https://github.com/pellierd/pddl4j
* Compilado (.JAR): <https://github.com/AdriDmgz/PlanifAutomatica-Planners/raw/main/pddl4j-3.8.3.jar>

### Instrucciones de instalación/compilación
Descargar código fuente de la URL dada y compilar código fuente usando herramientas Java. Realicé la compilación sin anotar el proceso, investigando el proyecto y usando herramientas según vi necesario (Visual Code, Gradle, javac, etc.). La compilación se basaba en el uso de Gradle y del fichero gradlew.bat. La compilación incluía una fase de test que no finalizaba, aunque luego descubrí que no era necesario que esta finalizase ya que previamente a los test ya se había generado el fichero .jar en la carpeta ./build/libs del proyecto. Se aceptan pull-request para detallar este proceso.

### Instrucciones de uso
Invocar por consola con ``java -jar ./pddl4j-3.8.3.jar`` para obtener entrada esperada y opciones de ejecución. También puede añadirse como planificador a plugin PDDL de Visual Studio Code con integración automática, indicando únicamente la ruta del .jar. Ver instrucciones del plugin para más información.

## JavaFF (2002 FF Original / 2015 JavaFF V1.0 / 2018 JavaFF V2.1)
* URL: https://github.com/tonyallard/JavaFF (original)
* URL: https://github.com/dpattiso/javaff (versión 2.1)
* Compilado (.JAR): <https://github.com/AdriDmgz/PlanifAutomatica-Planners/raw/main/javaff.jar> (versión 2.1)

### Instrucciones de instalación/compilación
Descargar código fuente de la URL dada (versión 2.1), abrir con Visual Studio Code para compilar ficheros .class, y, por último, compilar a .JAR mediante javac, usando las opciones del comando necesarias para configurar el CLASSPATH a la carpeta ./bin donde se encuentran los .class y al jgrapht-jdk1.6.jar que está en la carpeta ./lib/jgrapht-0.8.2 del proyecto. Fue necesario usar una versión relativamente antigua del JDK para realizar este proceso, ya que en algún punto (al compilar o al generar el .jar) daba error al hacerlo con la última versión. Se aceptan pull-request para detallar este proceso.

### Instrucciones de uso
Compilar/descargar fichero .JAR e invocar por consola con ``java -jar ./javaff.jar`` para obtener entrada esperada y opciones de ejecución.

## SapaReplan (2002)
* URL: https://rakaposhi.eas.asu.edu/sapa.html/
* Compilado (.JAR): <https://github.com/AdriDmgz/PlanifAutomatica-Planners/raw/main/SapaReplan.jar>

### Instrucciones de instalación/compilación
Fichero .jar proprocionado por autores en la web.

### Instrucciones de uso

Descargar fichero .JAR e invocar por consola con ``java -jar ./SapaReplan.jar`` para obtener entrada esperada y opciones de ejecución.
