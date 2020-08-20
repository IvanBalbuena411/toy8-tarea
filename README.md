# Arquitectura TOY-8

Nombre y apellido: Ivan Balbuena

## Instrucciones

- Forkear este repo
- Completar nombre y apellido
- Responder editando este mismo archivo
- Pushear a GitHub y pasarme el link de su fork (el repo tiene que ser público)


Tienen un emulador de la computadora y el circuito para el Logisim en el [blog](https://la35.net/orga/emulador.html). Usenlos sabiamente para responder.

**Tip:** si editan en el Atom tienen un _preview_ de Markdown tocando `Ctrl + Shift + M` mientras editan este archivo.
## Ejercicios

1. Considerar el siguiente programa de TOY-8 en lenguaje máquina. Traducir a hexadecimal en la tercer columna y a ensamblador en la cuarta como se muestra en la primera línea. ¿Cuál es el valor de 0xE cuando el programa se detiene? ¿Qué es lo que hace este programa si 0xE es el resultado del mismo?

```
0x1:  1010 1011    #  AB  #  lw B    
0x2:  1110 1010    #  EA  #  brz A   
0x3:  0010 1101    #  2D  #  add D   
0x4:  1100 1011    #  CB  #  sw B    
0x5:  1010 1110    #  AE  #  lw E    
0x6:  0010 1100    #  2C  #  add C   
0x7:  1100 1110    #  CE  #  sw E    
0x8:  1010 0000    #  A0  #  lw 0   
0x9:  1110 0001    #  E1  #  bze 1   
0xA:  0000 0000    #  00  #  halt    
0xB:  0000 0011    #  03  #          
0xC:  0000 0110    #  06  #          
0xD:  1111 1111    #  FF  #          
0xE:  0000 0000    #  00  #          
```
**Respuesta:** El valor de la direccion de memoria 0xE cuando el programa se detiene es 12 (18 en hexadecimal). Este programa multiplica lo que haya en la direccion de memoria 0xB con lo que hay en la direccion de memoria 0xC y asi dar el resultado de 0xE

2. Consideren el siguiente _hexdump_ de la memoria de TOY-8. O sea un volcado de la memoria en hexadecimal. ¿Cuántos programas distintos pueden encontrar? Indicar cuáles bytes interpretan como instrucciones y cuáles como datos.

```
0x0   00 A5 26 C7
0x4   00 08 05 00
0x8   A7 6D 2E C7
0xc   00 FF 01 00
```
**Respuesta:** La memoria tiene 2 programas, el primero pertenece a las direcciones de memoria 0x1, 0x4, 0x5 y 0x6. Mientras que la dirrecion de memoria 0x7 a tanto datos pertenecientes del primer programa como del segundo, este segundo programa utiliza desde la direccion de memoria 0x8 hasta la 0xC. Las memorias restantes corresponden de forma exclusiva al segundo programa

3. Para el primer programa del ejercicio anterior. ¿Qué líneas de control se activan para cada instrucción? ¿Cuál es el valor del bus de datos y de instrucciones en cada instrucción? Completen la siguiente tabla, agreguen las filas que sean necesarias.

|Instrucción|Reloj|Control|Data bus|Address Bus|
|---|---|--------------|---|---|
|A5 |0  |IR en         |A5 |1  |
|A5 |1  |R en, addr mux|08 |5  |
|26 |0  |              |   |   |

4. El siguiente programa suma los números que encuentra en la entrada hasta que aparece un cero, y luego envía el resultado a la salida. Traducirlo a ensamblador y a C siguiendo el ejemplo de las primeras dos líneas.

```
0x1:  A0   #  lw 0  #
0x2:  CE   #  sw E  #  int sum = 0;
0x3:  AF
0x4:  E9
0x5:  2E
0x6:  CE
0x7:  A0
0x8:  E3
0x9:  AE
0xA:  CF
0xB:  00
```

5. Una mejora que le podríamos hacer a esta computadora es duplicar la cantidad de memoria, pasar de 16 bytes a 32 bytes. ¿Cómo lo harían manteniendo la longitud de las instrucciones en 8 bits? ¿Qué partes de la CPU habría que modificar y cómo?
