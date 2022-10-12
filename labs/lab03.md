## Laboratorio 03:  

## SoC_initial


En este laboratorio se establece en dos partes: 1) Definir los perifericos del proyecto con su respectivo mapa de memoria y 2) se configurar  y probaran las herramientas correspondientes al framework de liteX.

### Definición de perifericos  y mapa de memoria 

Para la definición de los periferios debe seguir las instreucciones dada en laboratorios y tomar como guia:

1. Ejemplo de mapa de memoria de los perifericos del  proyecto [Ejemplo](https://github.com/unal-edigital2/2021-2/blob/master/slides/week-07-proyecto%20Dig2%202021%20-2.pptx). 
2. Que son los prerifericos del SoC [link](https://tutorialbit.com/computer-peripherals/differences-between-memory-mapped-i-o-and-port-mapped-i-o/)

#### Entrega

Una vez se tenga claro que perifericos debe  tener el  proyecto, realizar:

1. Descripción de cada periférico, definir las interconexión de entradas  y salidas. (caja negra)
2. Describir de forma general el funcionamiento de cada bloque en HW y describir en pseudo código la interconexión con el SW.
3. Realizar el mapa de memoria del SoC y de cada periférico.
4. Realizar el diagrama del Soc con los perifericos

### Introducción al SoC con litex 

Litex es un framework para generar con script depython la arquitectura del SoC, y por su facilidad de integración es la herramienta  que se usa para el dearrollo de los proyectos de cada grupo. para mas información se recomienda  visitar la página github de [liteX](https://github.com/enjoy-digital/litex/wiki)

#### 1. Instalación 

 a. Para la instalación del Framework debe seguir los pasos 1 a 4 de la guía de litex de este [link](https://github.com/enjoy-digital/litex/wiki/Installation) 

b. Recuerde configurar los path de Vivado y del compilador para RiscV en el archivo .bachrc que se encuentra en el home de cada usuario

    Nota: Primero acceda al archivo ".bashrc" con el comando "sudo nano ~/.bashrc". Y agregue la ruta de vivado escribiendo "export PATH=$PATH:/opt/Xilinx/Vivado/2020.2/bin" al final del archivo.  (Por supuesto que deberías usar tu propio camino de Vivado).
    
#### 2. Pruebas básicas de sintetización
Una vez se tenga  instaldo el framwork y el compilador  proceda a :
1. Descargar el paquete de trabajo de este laboratorio.
2. Ingresar en un terminal a la carpeta ´SoC_project´
3. Ejecutar       ` python3 buildSoCproject.py `
4. Conectar la tarjeta  y ejecutar `djtgcfg prog -d NexysA7 -i 0 -f ./build/nexys4ddr/gateware/nexys4ddr.bit`

En este punto usted tiene un SoC básico programado en la FPGA, y por lo tanto, se debe configurar y cargar el firmware

#### 3. Pruebas básicas de compilación

Para recordar que es compilación cruzada se recomienda ver este [documento](https://github.com/unal-edigital2/2021-2/blob/master/slides/week8_digital2.pdf) y para cargar el firmware al SoC riscv proceda a 

1. Ir a la carpeta  firmware
2. Ejecutar `make all`  revise el archivo makefile y comprenda se contenido 
3. Salir de la carpeta firmware  
4. Ejecutar `litex_term.py /dev/ttyUSB1 --kernel firmware/firmware.bin` recuerde que el puerto depende de donde este conectada la tarjeta de desarrollo.

***Recuerde que debe estar atento de revisar en consolar que fallos en los paso salen , y correguir antes de continuar con el paso siguiente***

### 4. Compresión de los procesos 
Al terminar los procesos anteriores se debe tener un procesador  con un firmware. En este contexto  se debe
1. Leer los pasos propuestos en la terminal , y ejecutar cada  ejemplo que da 
2. Revisar en el HW que se ejecuta el comando dado en SW
3. Revisar el archivo buildSoCproject.py e intente  generar la arquitectura del SoC
4. Revise el archivo main.c  y comprenda en SW que se esta haciendo. Verifique el SW con la ejecución que realizo en los puntos 1 y 2
