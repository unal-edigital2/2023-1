## Laboratorio 03:  

## SoC_initial

### Introducción 

En este laboratorio se establece en dos partes: 1) Definir los perifericos del proyecto con su respectivo mapa de memoria y 2) se configurar las herramientas  correspondientes al framework de liteX.

#### Definición de perifericos  y mapa de memoria 

Para la definición de los periferios debe seguir las instreucciones dada en laboratorios y tomar como guia:

1. Ejemplo de mapa de memoria de los perifericos del  proyecto (Ejemplo)[https://github.com/unal-edigital2/2021-2/blob/master/slides/week-07-proyecto%20Dig2%202021%20-2.pptx]. 
2. Que son los prerifericos del SoC (link)[https://tutorialbit.com/computer-peripherals/differences-between-memory-mapped-i-o-and-port-mapped-i-o/]
3. 

Litex es una herramienta e incluso un entorno que permite construir sistemas digitales basados en FPGA de una manera r´apida debido a la automatizaci´on de ciertas tareas, integraci´on
de herramientas involucradas en el flujo de trabajo con FPGA, as´ı como la posibilidad de
realizar despliegues relativamente r´apidos.
Todo lo relacionado con cores hardware y su integraci´on, sea en sistemas basados en FPGA
independientes o como un System on Chip (SoC), Litex da la facilidad de concentrarse en
ciertas tareas de dise˜no e implementaci´on que suelen ser f´acilmente integradas y probadas
en una FPGA en una implementaci´on final.
En las sesiones de laboratorio restantes dispuestas para el desarrollo del proyecto de Digital
II, se har´a uso de este framework para integrar los dise˜nos de perif´ericos espec´ıficos de cada
proyecto. As´ı mismo, podr´an incorporar la l´ogica para el manejo de informaci´on de estos
perif´ericos y su gesti´on desde el procesador.
La estructura de Litex se podr´ıa dividir en dos partes:
Hardware: la descripci´on de todo el hardware involucrado (procesador, perif´ericos,
buses de comunicaci´on, etc) est´a principalmente apoyada en Python. No obstante, los
dise˜nos en Verilog y VHDL pueden ser integrados sin inconveniente.
Software: En Litex, el software se aglutina en el firmware, all´ı es donde se pueden
construir e implementar las tareas software, que ser´an codificadas en lenguaje C, aunque
pueden incorporarse fragmentos de c´odigo en ensamblador.
La informaci´on sobre Litex, su p´agina oficial es: Wiki de Lite

1. instalar litex https://github.com/enjoy-digital/litex
2. Descargar el paquete WP04
3. ingresar en un terminal a la carpeta ´SoC_project´
4. ejecutar "python3 buildSoCproject.py"
5. djtgcfg prog -d NexysA7 -i 0 -f ./build/nexys4ddr/gateware/nexys4ddr.bit
6. ir a la carpeta  firmware
7. ejecutar "make all"
8. salir de la carpeta firmware  
9. ejecutar litex_term.py /dev/ttyUSB1 --kernel firmware/firmware.bin
10.  enteder el programa que esta  ejecutando el procesardor 
