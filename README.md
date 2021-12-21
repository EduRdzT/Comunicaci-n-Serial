# Comunicación Serial
#### `Comunicación Serial RS-232`

**Índice**
- [Introduccion](#id1)
- [Objetivos](#id2)
- [Marco Teórico](#id3)
- [Desarrollo Experimental](#id4)
   - [Objetivo 1](#id4-1)
   - [Objetivo 2](#id4-2)
- [Análisis y Resultados](#id5)
- [Referencias](#id6)


## INTRODUCCIÓN<a name="id1"></a>
  
La comunicación serial es un protocolo muy común para comunicación entre dispositivos. A pesar de ser es más lenta que la comunicación en paralelo, este método de comunicación es más sencillo y puede alcanzar mayores distancias. En esta práctica analizaremos cómo funciona este tipo de comunicación haciendo uso del PIC18F4550 y diseñando un dispositivo con tres buses (uno de lectura y dos de escritura) para poder elegir a qué salida escribir un dato desde la computadora. 

En este reporte se incluye información sobre: el protocolo de comunicación serial, los microcontroladores y demás materiales para armar el dispositivo anteriormente mencionado, el diagrama eléctrico del hardware a utilizar y los códigos utilizados junto con una explicación.

## OBJETIVOS<a name="id2"></a>
  
### Objetico general

- Diseñar e implementar un sistema que sea capaz de responder al protocolo de comunicación serial.

### Objetivos específicos 

####Objetivo 0: Hardware 

- Programe el nuevo firmware del sistema (Serial.hex) en el chip 18F4550 e instale el nuevo driver que se encuentra en el archivo .zip (solo si el sistema lo solicita), lea las instrucciones de uso en Leeme.pdf. 

#### Objetivo 1: Software 

- Crear un programa en el IDE VS2010 (VC++).
- Pruebe la función de escritura y monitoree la salida. 
- Haga mediciones del Baudrate, latencia, etcétera.
- Haga mediciones del punto anterior por lo menos con dos velocidades diferentes.

#### Objetivo 2: Hardware y software

Diseñe un dispositivo B), con las siguientes especificaciones:

1. Que cuenten con 3 buses: A, B y D. 
   - Bus A (con dirección 0) de escritura (salida 7 bits).
   - Bus B (con dirección 1) de escritura (salida 7 bits).
   - Bus D de lectura (entrada 1 bit `señal serial`).

Basado en el siguiente protocolo: describa, diseñe e implante el circuito B) que solucione:

2. Ser capaz de responder a los protocolos hardware de puerto serial RS232 (entrada). 
3. Descripción de protocolo software de alto nivel : 
El dato leído por B), se interpreta como se muestra en siguiente tabla.
4. Los datos leídos por el teclado de la computadora, deben ser en formato binario {0 y 1}.
5. Los datos mostrados en la pantalla de la computadora deben ser en formato Binario, Octal, Decimal y Hexadecimal. 
6. Instalar Leds, en los registros de salidas, para visualizar los datos enviados. 

_Nota: no utilizar bibliotecas de conversión de datos._

## MARCO TEÓRICO<a name="id3"></a>

#### Comunicación serial

La comunicación serial es un protocolo muy común para comunicación entre dispositivos que se incluye de manera estándar en prácticamente cualquier computadora. La mayoría de las computadoras incluyen dos puertos seriales RS-232. La comunicación serial es también un protocolo común utilizado por varios dispositivos para instrumentación y puede ser utilizada para adquisición de datos si se usa en conjunto con un dispositivo remoto de muestreo.

El concepto de comunicación serial es sencillo. El puerto serial envía y recibe bytes de información un bit a la vez. Aun y cuando esto es más lento que la comunicación en paralelo, que permite la transmisión de un byte completo por vez, este método de comunicación es más sencillo y puede alcanzar mayores distancias. Para realizar la comunicación se utilizan 3 líneas de transmisión: (1) Tierra (o referencia), (2) Transmitir, (3) Recibir. Debido a que la transmisión es asincrónica, es posible enviar datos por una línea mientras se reciben datos por otra.

- Velocidad de transmisión (baud rate): Indica el número de bits por segundo que se transfieren, y se mide en baudios (baudios). Por ejemplo, 300 baudios representan 300 bits por segundo. Cuando se hace referencia a los ciclos de reloj se está hablando de la velocidad de transmisión. Por ejemplo, si el protocolo hace una llamada a 4800 ciclos de reloj, entonces el reloj está corriendo a 4800 Hz, lo que significa que el puerto serial está muestreando las líneas de transmisión a 4800 Hz.
- Bits de datos: Se refiere a la cantidad de bits en la transmisión. Cuando la computadora envía un paquete de información, el tamaño de ese paquete no necesariamente será de 8 bits. Las cantidades más comunes de bits por paquete son 5, 7 y 8 bits.

El protocolo RS-232 es una norma o estándar mundial que rige los parámetros de uno de los modos de comunicación serial. Por medio de este protocolo se estandarizan las velocidades de transferencia de datos, la forma de control que utiliza dicha transferencia, los niveles de voltajes utilizados, el tipo de cable permitido, las distancias entre equipos, los conectores, etc.

#### Microsoft Visual Studio 2010

El programa que utilizamos en esta práctica es Microsoft Visual Studio, un entorno de desarrollo integrado que soporta varios lenguajes, tales como: C++, C#, Visual Basic, Java, Python, etc. Visual Studio permite a los desarrolladores crear sitios y aplicaciones web, así como servicios web en cualquier entorno que soporte la plataforma .NET. 
 
#### PIC18F4550

El PIC18F4550 es uno de los microcontroladores más populares cuando se trata de conectividad USB. Ofrece un alto rendimiento informático con agregado de memoria de programa flash de alta resistencia mejorada, ideal para pequeñas potencias) y aplicaciones de conectividad. 

Algunas de sus características son:
- Opera con un rango de voltaje que va de 2V a 5.5 V
- Puerto  USB V2.
- RAM 1-Kbyte accesible por USB.
- Reloj externo hasta de 48 MHz.
- Oscilador interno de 31 KHz – 8 MHz configurable por software.
- Pines con salida de alta corriente de hasta 25 mA.
- Puerto USART con soporte para  comunicaciones MSSP, SPI e I²C.
- Hasta 13 canales ADC de 10 bits.
- Memoria FLASH con 100,000 ciclos de lecturas escritura típicos.
- Memoria EEPROM con  1, 000,000 ciclos de lectura escritura típicos y retención de datos de hasta 40 años.
- Programación con código de protección.
- Programación ICSP vía dos pines.
- Tiene 40 pines

#### PIC12F675

El PIC12F675 está diseñado siguiendo la arquitectura Harvard, es decir, la memoria de datos está separada de la de programa. Este microcontrolador consta de: 
- 8 pines, de los cuales 6 son usados como entrada o salida.
- 128 bytes de memoria de datos EEPROM
- RAM de 512KB
- Velocidad: 20MHz
- Voltaje de alimentación: 2V ~ 5.5V
- 4 selecciones de oscilador, incluido un oscilador RC de 4 MHz con calibración programable y reinicio de encendido.

#### Biblioteca de puerto serial.

En esta primera práctica se ocupó la biblioteca del puerto serial, la cual realiza la comunicación entre el software y el hardware. La implantación de la biblioteca nos da acceso a las siguientes funciones:
- Construir el objeto “Mi serial”, identificando el puerto y la velocidad de operación.
- Escribir un byte al puerto previamente seleccionado

## DESARROLLO EXPERIMENTAL<a name="id4"></a>

#### Objetivo 0: Hardware

El mismo hardware usado en la práctica 1, pero ahora con el nuevo firmware del sistema (Serial.hex).

#### Objetivo 1: Software<a name="id4-1"></a>

Para poder probar la función de escritura se utilizó el siguiente código:

```c++
#include <stdafx.h>
#include "SerialLIB.h" 
//incluimos El archivo .h de la biblioteca.
#include <windows.h>

int main( void )
{
	
Serial MiSerial( TEXT("COM4"),2400);	
// Con el tipo Serial Crea Objeto serial conectando con puerto COM6	
// con velocidad de 2400 bauderate
// (verificar en ADMINISTRADOR de DISPOSITIVOS)
// podemos elegir El puerto que se encuentre disponible
// y la velocidad standart permitida.

	printf( "\nEscribiendo algo al puerto serial\n") ;

	for(int i = 0; i < 255; i++)
	{
		printf( ".") ;
		MiSerial.write( dec );// Ejemplo de uso de escritura de un valor.
		Sleep(100);
	}
	printf("Listo!!!\n");
	getch();
}
```
La función de escritura se probó al menos dos veces con velocidades de transmisión distintas (300, 1200, 2400,4800).

#### Objetivo 2: Hardware y software<a name="id4-2"></a>

La máquina de estados diseñada para poder cubrir con este objetivo fue la siguiente.
 
_Figura 3. Máquina de estados._

El circuito implementado en esta práctica se muestra en la siguiente figura.

En este circuito se conecto el PIC18F4550 al PIC12F675 y al registro sipo para la comunicación serial, en el PIC12F675 se programo la maquina de estados por lo que manipulaba el reloj de todos los registros utilizados.

En la salida del registro sipo se conectaron los dos registros pipo para cada dispositivo y de ahí se conectaron barras de leds para mostrar el dato enviado.

En la figura 5 se muestra el diagrama de tiempos para la dirección, donde:

TX: comunicación serial.
CLK SIPO: flancos de reloj del registro sipo para detectar la información del TX. 
PIPO 1: habilitación del reloj para el registro pipo 1.
PIPO 2: habilitación del reloj para el registro pipo 2.
CLK PIPO 1: reloj del registro pipo 1. 
CLK PIPO 2: reloj del registro pipo 2.

_Figura 5. Diagrama de tiempos para la dirección_

Al hacer la detección del bit de inicio empieza un contador que dura 614us, el cual es el tiempo que tarda en mantener un bit de dato para hacer la siguiente detección, este proceso se repetirá ocho veces para detectar 1 byte de dato.

Después se detectará el bit más significativo para saber en qué registro se va a trabajar se habilita el reloj del registro, a este proceso se le llama la detección de dirección (figura 5).

_Figura 6. Diagrama de tiempos para el dato_

Como en el caso anterior, después de hacer la detección del bit de inicio se realizan ocho flancos de reloj cada 614us para de detección de información, después de terminar la detección de los datos da un flanco de reloj para el pipo que se habilito en la parte de la detección de dirección (figura 6).

##### CÓDIGO DE LA MAQUINA DE ESTADOS.

A continuación, se presenta el código utilizado para la máquina de estados. 

```c++
void main(){
declaración de variables:
   int cont_5=0,cont_8=0;
   int z=0;
//Se declaran los puertos como entrada o salida:   
   set_tris_a(0x0D);
   output_a(0x00); 
   
   while(true){
//DIRECCION:
//ciclo de detección del bit de inicio con 10 muestras
      while(cont_5 != 10){
         if (input(pin_A0)==0){
            cont_5++;
         }
         else{
            cont_5 = 0;
         }
      }
      cont_5 = 0;
//ciclo de detección de sato, se repite 8 veces
      while(cont_8 != 8){
         delay_us(416);
         output_high(PIN_A1);
         delay_us(10);
         output_low(PIN_A1);
         cont_8++;
      }
      cont_8 = 0;
      delay_us(416);
 //Detección del bit más significativo para saber e que registro vamos a trabajar
         if (input(pin_A3)==1){
            z = 1;
         }
         else{
            z = 0;
         }
         
//DATO:
//ciclo de detección del bit de inicio con 10 muestras         
         while(cont_5 != 10){
         if (input(pin_A0)==0){
            cont_5++;
         }
         else{
            cont_5 = 0;
         }
      }
      cont_5 = 0;
//ciclo de detección de sato, se repite 8 veces
      while(cont_8 != 8){
         delay_us(416);
         output_high(PIN_A1);
         delay_us(10);
         output_low(PIN_A1);
         cont_8++;
      }
      cont_8 = 0;
      delay_us(416);
//flanco de reloj para el registro pipo      
         if (z == 1){
            output_high(PIN_A4);
            delay_us(10);
            output_low(PIN_A4);
         }
         else{
            output_high(PIN_A5);
            delay_us(10);
            output_low(PIN_A5);
         }
}
}
```
## ANÁLISIS Y RESULTADOS<a name="id5"></a>

La función de escritura se ejecutó a una velocidad de transmisión de 2400 baudrate, la velocidad resultante de envío de datos fue de 480µs, esta velocidad se puede observar en la figura 7.

La figura 8 muestra la captura de los datos enviados con la función escritura.

Así mismo podemos observar que el bit de inicio se encuentra en 0 y el bit de paro se encuentra en 1 como lo indicaba el protocolo de comunicación serial propuesto al inicio.

Lo siguiente fue detectar el bit menos significativo para poder seleccionar la dirección a la cual vamos a escribir.

A continuación, se muestra el código en ejecución.

Al seleccionar algunos de los dos registros se accede al siguiente menú.

Finalmente, la figura 11 muestra el circuito ya implementado.
 
## REFERENCIAS<a name="id6"></a>

>	http://digital.ni.com/public.nsf/allkb/039001258CEF8FB686256E0F005888D1 (17 de septiembre del 2018)

>	https://www.microchip.com/wwwproducts/en/PIC18F4550 (17 de septiembre del 2018)

>	https://www.microchip.com/wwwproducts/en/PIC12F675 (17 de septiembre del 2018)
