## Laboratorio 02: Introducción al set de intrsucciones  y al SoC: Caso procesador J1 

# Introducción

En la imagen se observa, los componentes básicos de la unidad de procesamiento, en donde:

1. La unidad Datapath, ejecuta operaciones aritméticas y lógicas.
2. La unidad de control. Ordena al datapath, memoria y dispositivos de I/O lo que hay que hacer de acuerdo al programa
3. La memoria, Almacena las instrucciones del programa y mantiene almacenada la información o los datos


![sigin](https://github.com/unal-edigital2/2022-2/blob/master/labs/figs/0_2.png)

En este contexto, en el laboratorio se tiene como objetivo abordar el concepto de procedador y del SoC , a partir  del caso de estudio del procesador J1, para lo cual se estudia :

1. Componentes del procesador y Ciclos de Ejecución de las instrucciones.
2. Interface SW/HW, compilación cruzada 
3. SoC Básico

***Nota: esta guia es un resumen. En clase se da la explicación detallada, recuerde  preguntar siempre***

# Desarrollo

Para este laboratorio, su utiliza el procesador J1, procesador tipo pila de 16 bits, cuenta con 16 operaciones logico-aritmeticas, el resumen se encuetra  en el [ji.pdf](https://www.excamera.com/files/j1.pdf) y el procesor base es de [James Bowman](https://github.com/jamesbowman/j1)

De igual manera, para mas información puede ver los siguientes [slides](https://github.com/unal-edigital2/2021-2/tree/master/slides/week02)

## Componentes del procesador J1 y Ciclos de Ejecución de las instrucciones.

El procesador j1, cuenta con una estructura básica, como se observa en la siguiente figura, por favor  revise la documentación del procesador [j1.pdf](https://github.com/unal-edigital2/2022-2/blob/master/labs/figs/j1.pdf) junto con el el archivo j1.v que se encuetra en la la carpeta HDL del paquete de trabajo.

![sigin](https://github.com/unal-edigital2/2022-2/blob/master/labs/figs/j1.png)
 
### Preguntas

1. ¿Según la imagen a continuacíón, identifca los bloques en el HDL j1.v?
![img2](https://github.com/unal-edigital2/2022-2/blob/master/labs/figs/j1_10.jpg)
2. ¿Cuál es el objetivo de la linea 3 de j1.v, `parameter   bootram_file     = "./image.ram"`  ?
3. ¿Logra identificar las 5 intrucciones en j1.v ?

![img2](https://github.com/unal-edigital2/2022-2/blob/master/labs/figs/j1_3.png)

4. ¿Logra identificar las operaciones de la alu, en j1.v ?

![img2](https://github.com/unal-edigital2/2022-2/blob/master/labs/figs/j1_4.png)

5. ¿A partir de las intrucciones, podrian  proponer  un listado de opcodes, para  realizar  un programa que  ejecute 10+5-2 ?


## Interface SW/HW, compilación cruzada

Para la configuración del software se debe instalar el compilador Gforth, seguir los siguietnes pasos  

### Instalar gforth

##### En linux
  1. Ejecute el siguiente comando 
      `sudo apt install gforth`

#### En windows

  1. Descargar gforth-0.7.0.exe del link https://www.gnu.org/software/gforth/
  2. Ejecute e instale gforth-0.7.0.exe y sigas las indicaciones 
  3. En el archivo Makefile borre su contenido y   agrege la siguiente linea
  
    `"C:\Program Files (x86)\gforth\gforth.exe" -e 'include main.fs bye' `

  4. Agrege la extensión .bat al archivo Makefile

La compilación cruzada hace referencia a la compilación del código, pero  que se ejecuta en plataforma diferente a la del compilador. Por ejemplo, en este laboratorio el compilador esta alojado en nuestro computador, pero el codigo sera ejecutado en el procesador j1, que se aloja en la FPGA.

Se recomieda revisar las [slides](https://github.com/unal-edigital2/2022-2/blob/master/slides/week8_digital2.pdf)

para esta parte no se pide  aprender gforth, ya que solo se usa como herramienta de generación de instrucciones del procesador, en otras palabras lo que buscamos es comprender la frontera de Sw y HW como se ve observa en la siguiente figura.

![img2](https://github.com/unal-edigital2/2022-2/blob/master/labs/figs/0_3.png)

### Preguntas

1. Revise el archivo j1.mem, se encuentra en la carpera `firmware/Hello_World/`. ¿Las lineas 1, 1083 a 1088  de j1.men que instrucciones son?
2. Revise el archivo app.fs, ¿el resultado anterior  coincide con los escrito en este archivo?
3. ¿Qué es un archivo makefile?
4. Diseñe un código que permita ejecutar, 4 operaciones aritméticas (ejemplo; 1 multiplicación, 1 división ,1 suma, 1 resta)  y que el resultado de cada una sea  enviado por la Uart del j1 al computador . para ello:

     * Modificar el app.fs, para agregar las 5 operaciones.
     * Ejecute el makefile correspondiente. (compilación cruzada).
     * Sintetizar el HDL del j1soc.v. cambiando la ruta del path de j1.men (linea 4 de j1soc.v)
     * implemente el procesador j1soc en la FPGA.
     * Instalar y configurar un nonitor del puertor serial (Uart) en el computador.
     * Comprobar el funcionamiento.
     * Documentar con ayuda de imagenes, videos en el README del laboratorio.
     
5. ¿Los bloques Uart, Multiplicadory Divisor,  no hacen parte del DataPath j1.v, entonces como estan conectados ?
6. ¿qué es un SoC?
7. ¿explique el mapa de memoria del SoC del j1 , para ello revisar j1Soc.v y tomar como base la este [link](https://github.com/unal-edigital2/2022-2/blob/master/slides/week03/week4_digital2.pdf) a partir de la diapositiva 52 ?

## Entregables

1. Las respuestas a las preguntas
2. La documentación en el archivo README del lab en github. recuede que puede usar imagenes y videos
3. Los códigos tanto en HW como en SW en el git

