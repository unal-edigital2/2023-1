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

Esta documentación debe estar cargarda en el README del laboratorio.

### Introducción al SoC con litex 

Litex es un framework para generar con script depython la arquitectura del SoC, y por su facilidad de integración es la herramienta  que se usa para el dearrollo de los proyectos de cada grupo. para mas información se recomienda  visitar la página github de [liteX](https://github.com/enjoy-digital/litex/wiki)

#### 1. Instalación 

 a. Para la instalación del Framework debe seguir los pasos 1 a 3 de la guía de litex de este [link](https://github.com/enjoy-digital/litex/wiki/Installation) ***Nota no instalar en la carpeta del usuario***
 
b. Recuerde configurar los path de Vivado y del compilador para RiscV en el archivo .bachrc que se encuentra en el home de cada usuario. 

Nota: Primero acceda al archivo ".bashrc" con el comando `nano ~/.bashrc`. Y agregue la ruta de vivado escribiendo al final del archivo `export PATH=$PATH:/opt/Xilinx/Vivado/2020.2/bin`.  (Por supuesto que deberías usar tu propio path o ruta de Vivado).
 
Si prefiere puede ver este video para la configuración del path de vivado [video](https://drive.google.com/file/d/13SeEx4Z_3RK7wGHfiwuvrs2e9uZLPhrI/view?usp=sharing)

Debe realizar el mismo proceso con la ruta del compilador de riscV, si desea puede ver este [video](https://drive.google.com/file/d/1yv9FQoa4uNp4IZPggvnfchumChwpKurf/view?usp=sharing)
 
#### 2. Pruebas básicas de sintetización y programación del procesador en la FPGA
##### Configuración
Una vez se tenga instaldo el framwork y el compilador  proceda a :
1. Descargar el paquete de trabajo de este laboratorio.
2. Según la tarjeta que use en el archivo `buildSoCproject.py` modifique:

    Para las tarjetas Nexys 4, 4DDR y A7, debe comentar las lineas 9 y 10, como la imagen:
  ![image](https://github.com/unal-edigital2/2022-2/blob/master/labs/figs/im4lab3.png)
  
    Para la tarjeta zybo debe  comentar la linea 8 y 10 descomentando la linea 9. ver imagen a continuación
  ![image](https://github.com/unal-edigital2/2022-2/blob/master/labs/figs/im3lab3.png)
  
     Adicional para la tarjeta zybo  comentar las lineas 58 a 72 como se aprecia en la imagen:
  ![image](https://github.com/unal-edigital2/2022-2/blob/master/labs/figs/im5lab3.png)
 
3. Revise que la configuración del reloj de las tarjetas que esta usando corresponda a lo escrito en el archivo `builSocproject.py`. En la tarjeta ZYBO es de 125Mhz, y para las Nexys de 100Mhz

4. Tenga encuenta que según el boton de que se configure para la cpu_reset, debe quitar la negación en la descripción de Clock Reset Generation  `~platform.request("cpu_reset")` 
##### Sintetización

5. Ingresar en un terminal a la carpeta ´SoC_project´
6. Ejecutar       ` python3 buildSoCproject.py `

##### Load Bitstream

7. Conectar la tarjeta  y ejecutar `djtgcfg prog -d NexysA7 -i 0 -f ./build/gateware/top.bit`. Debe remplazar NexysA7 por el nombre de la tarjeta NexysA7 por la usted tienes. Ahora bien para saber el nombre de su tarjeta, ejecute el comando `djtgcfg enum`.

    Para las tarjetas ZYBO, deben cargar el bitstream, por medio de vivado, por lo que se recomienda  
    ejecutar el script load_zybo.py que se encuentra en el repositorio del laboratorio. 
    En la Terminal escriba: `python3 load_zybo.py`

Nota: Si no tiene instalado los driver de digilent adept o el  comando djtgcfg genera error,  por favor reinstalar las driver de Utilities  y Runtime, para ello descargarlos de este [link](https://digilent.com/reference/software/adept/start)


A esta altura del laboratorio, la tarjeta de desarrollo  cuenta con el SoC basado en el procesado VexRisc, un grupo reducidos de perifericos y con la BIOS cargada en la memoria ROM. (recomiendo ver el inicio del video de funcionamiento que se encuenta al final de esta guia). La documentación del procesador VexRiscv se encuentra en este [link](https://github-com.translate.goog/SpinalHDL/VexRiscv?_x_tr_sl=auto&_x_tr_tl=es&_x_tr_hl=es). VexRiscv se basa en la arquitectura de CPU RISC-V de 32 bits.


Para comprobar si el SoC esta configurado en la FPGA debe abrir el monitor Serial de su preferencia (ej: cutecom) a una tasa de transmisión de 115200 bps, y conectar via puerto serial-USB el SoC. No  olvidar dar los permisos de lectura y escritura a este puerto por medio del comando chmod. Una vez este la conexión establecida reiniciar el procesador por medio del botón reset del mismo. Si en la consola de  monitor serial visualiza texto como en la siguiente imagen, ya se puede interactuar con la BIOS del procesador, como se explica en el video, enviando el comando `leds 7`.  

![imagen](https://github.com/enjoy-digital/litex/blob/master/doc/bios_screenshot.png)

**Recuerde que si tiene la tarjeta de desarrollo ZYBO debe  conectar el puerto serial del adaptador serial2USB.**

Una vez se tenga completo conocimiento que la FPGA aloja el SoC y este funciona correctamente, podemos dar paso a la compilación de la aplicación. Como se observa en la [documentación de litex](https://github.com/enjoy-digital/litex/wiki/Load-Application-Code-To-CPU), el procesador cuenta con el gestor de aranque, bootloader, que permita cargar via puerto serial el código de la aplicación en software que se implementa. Para una mejor comprensión se recomienda ver el segundo video que esta al final de esta  guia.

#### 3. Pruebas básicas de compilación del firware

Para recordar que es compilación cruzada se recomienda ver este [documento](https://github.com/unal-edigital2/2021-2/blob/master/slides/week8_digital2.pdf) y para cargar el firmware al SoC riscv proceda a 

1. Ir a la carpeta  firmware
2. Ejecutar `make all`  revise el archivo makefile y comprenda se contenido 
3. Salir de la carpeta firmware  
4. Ejecutar `litex_term /dev/ttyUSB1 --kernel firmware/firmware.bin` recuerde que el puerto depende de donde este conectada la tarjeta de desarrollo. 
   

***Recuerde que debe estar atento de revisar en consolar que fallos en los paso salen , y correguir antes de continuar con el paso siguiente***

#### 4. Compresión de los procesos y entrega
Al terminar los procesos anteriores se debe tener un procesador  con un firmware. En este contexto  se debe
1. Leer los pasos propuestos en la terminal , y ejecutar cada  ejemplo que da 
2. Revisar en el HW que se ejecuta con comando dado en SW
3. Revisar el archivo buildSoCproject.py e intente  generar la arquitectura del SoC
4. Revise el archivo main.c  y comprenda en SW que se esta haciendo. Verifique el SW con la ejecución que realizo en los puntos 1 y 2

#### Video de la clase  explicando el lab

[Video: Explicación del laboratorio  12 octubre  2022](https://drive.google.com/file/d/1lUn0W8sr-qPIHxGviVugAuhj7UPhIvZW/view?usp=sharing)

[Video: Funcionamiento del SoC 3 de noviembre 2022](https://drive.google.com/file/d/1U3sdJrwGRJ3FJZ1nP9PYL3qFEwdII3Sv/view?usp=sharing)
