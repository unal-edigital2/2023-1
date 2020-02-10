## ELECTRÓNICA DIGITAL 2 2019 -2 UNIVERSIDAD NACIONAL DE COLOMBIA 
## TRABAJO 03- integración controlador OV7670 con SoC

## Introducción 
El driver de captura de datos de la cámara debe adquirir la información de los pixeles y almacenarlos en el buffer de memoria.
La imagen alnacenada en la memoria debe ser enviar via uart por medio del procesador

En este paquete de trabajo los estudiantes deben, en primera instancia, integrar por medio de litex el controlador de la camara.

Luego de la integración deben probar la funcionalidad del diseño. Para ello, deben realizar el firmware respectivo, se recomienda enviar la información de la imagen via uart, para probar la integración

Para este paquete de trabajo, el estudiante debe estar inscrito en un grupo y copiar la información del siguiente link [WP03](https://classroom.github.com/g/).
Debe escribir la documentación en el archivo README.md de la carpeta docs. Recuerde, esta documentación debe ser tal que, cualquier compañero de futuros semestres comprenda sus anotaciones y la relación con los módulos diseñados. Se deben incluir diagramas de conexión de la FPGA, la descripción funcional y estructural, describir las FSM utilizadas, los mapas de memoria, el firmware del LM32. Recuerde incluir las conexiones del puerto I2C y la cámara. Debe incluir imagenes y/o videos del las pruebas e implementación.

***Recuerde: Revisar las instrucciones dadas en metodología y documentación.***

## Material 

Para este paquete de trabajo se debe contar con:

* Pantalla con entrada VGA y cuya resolución sea 640x480.
* FPGA que cuenta con puerto VGA.
* Cable VGA.
* IP controlador de la cámara OV7670.
* Litex. 
* Toolchain del procesador lm32.
* Plantilla del proyecto sugerido [WP03](https://classroom.github.com/g/).


## Desarrollo

Una vez clone el repositorio, en su computador de la plantilla del proyecto [WP03](https://classroom.github.com/g/), realizar lo siguiente:

1. Integrar el controlador de la cámara al SoC.
2. Probar el funcionamiento de la cámara vía lm32 y uart.
3. Diseñar el detector de color de imagenes via Sw o HW (histograma).
4. Enviar vía uart, el texto del color predominante de la imagen.
5. Documentar:
    * En la carpeta HW debe alojar el proyecto realizado en litex y Verilog.
    * En la carpeta SW debe estar el firmware del procesador lm32.
    * En la carpeta SW_arduino, la implementación del código de Arduino utilizado.

***RECUEDE: Es necesario documentar el módulo diseñado con los respectivos diagramas funcionales y estructurales y registrar la información en README.md ***

 ### Coevaluación

Cada grupo debe realizar una coevaluación por cada integrante del mismo. El archivo se encuentra en la carpeta coEvaluation.

***RECUEDE: Es necesario documentar la implementación y registrar la información en README.md, lo puede hacer con ayuda de imágenes o videos***




