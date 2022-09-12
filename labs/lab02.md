## Laboratorio 02: Introducción al set de intrsucciones  y al SoC: Caso procesador J1 
# Introducción

En la imagen se observa, los componentes básicos de la unidad de procesamiento, en donde:

1. La unidad Datapath, ejecuta operaciones aritméticas y lógicas.
2. La unidad de control. Ordena al datapath, memoria y dispositivos de I/O lo que hay que hacer de acuerdo al programa
3. La memoria, Almacena las instrucciones del programa y mantiene almacenada la información o los datos


![sigin](https://github.com/unal-edigital2/2022-2/blob/master/labs/figs/0_2.png)

En este contexto, en el laboratorio se tiene como objetivo abordar el concepto de procedador y del SoC , a partir  del caso de estudio del procesador J1, para lo cual se estudia :

1. Componentes del procesador
2. Ciclos de Ejecución de las instrucciones.
3. Interface SW/HW, compilación cruzada 
4. SoC Básico

# Desarrollo

Para este laboratorio, su utiliza el procesador J1, procesador tipo pila de 16 bits, el cual cuenta con 15 operaciones logico-aritmeticas, el resumen se encuetra  en el [ji.pdf](https://www.excamera.com/files/j1.pdf) y el procesor base es de [James Bowman](https://github.com/jamesbowman/j1)

De igual manera, para mas información puede recurir a los siguientes [slides](https://github.com/unal-edigital2/2021-2/tree/master/slides/week02)

## Componentes del procesador J1

El procesador j1, cuenta con una estructura básica, como se observa en la siguiente figura, por favor  revise la documentación del procesador [j1.pdf](https://github.com/unal-edigital2/2022-2/blob/master/labs/figs/j1.pdf) junto con el el archivo j1.v que se encuetra en la la carpeta HDL del paquete de trabajo.

![sigin](https://github.com/unal-edigital2/2022-2/blob/master/labs/figs/j1.png)
 
### Preguntas

1. ¿Según la imagen a continuacíón, identfica estos bloques en el HDL j1.v?
![sigin](https://github.com/unal-edigital2/2022-2/blob/master/labs/figs/j1_10.jpg)
2.  ¿Cúal es el objetivo de la linea 3 de j1.v, `parameter   bootram_file     = "./image.ram"`  ?


## Interface SW/HW, compilación cruzada
para la configuración del software se debe instalar el compilador Gforth, para lo cual se debe seguir los siguietnes pasos  

### Instalar gforth en linux
1. Ejecute el siguiente comando 
    `sudo apt install gforth`

### Instalar gforth en windows

1. Descargar gforth-0.7.0.exe del link https://www.gnu.org/software/gforth/
2. Ejecute e instale gforth-0.7.0.exe y sigas las indicaciones 
3. En el archivo Makefile borre su contenido y   agrege la siguiente linea
  
  `"C:\Program Files (x86)\gforth\gforth.exe" -e 'include main.fs bye' `
  
4. Agrege la extensión .bat al archivo Makefile

# Entregables

Una vez clone el repositorio y lea la anterior guia, realice lo siguiente:

