<img width="1600" height="623" alt="image" src="https://github.com/user-attachments/assets/0b73ec01-1223-44eb-9594-7a12a6e3b3d6" />[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/Px-uYaj2)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=22891300&assignment_repo_type=AssignmentRepo)
# Lab02 - Sumador/Restador de 4 bits

# Integrantes
Daniel Buenhombre

Sergio Caicedo

Santiago Muñoz

# Informe

Indice:

1. [Documentación](#documentación-de-los-circuitos-implementados-implementado)
2. [Simulaciones](#simulaciones)
3. [Evidencias de implementación](#evidencias-de-implementación)
4. [Preguntas](#preguntas)
5. [Conclusiones](#conclusiones)
6. [Referencias](#referencias)

## Documentación del diseño implementado

### 1. Sumador/Restador

#### 1.1 Descripción

En este nuevo laboratorio se realizó el diseño e implementación de un sumador de 4 bits utilizando el lenguaje de descripción de hardware Verilog. Para comenzar, se utilizó un esquema proporcionado por el docente, el cual mostraba la estructura general del circuito y la forma en que se conectan varios sumadores de 1 bit para construir un sumador de mayor capacidad.

El sumador de 4 bits permite realizar la suma de dos números binarios de 4 bits, generando como resultado cuatro bits de suma y un posible acarreo de salida (Cout). Este funcionamiento se logra conectando varios sumadores de 1 bit en cascada, donde el acarreo de salida de una etapa se utiliza como acarreo de entrada en la siguiente etapa.

Posteriormente, el diseño fue probado mediante simulación utilizando el simulador Icarus Verilog, verificando el comportamiento del circuito con diferentes combinaciones de entradas. Finalmente, después de comprobar su correcto funcionamiento en la simulación, se procedió a realizar la implementación del sumador de 4 bits para validar su operación en la práctica.

Si quieres, también puedo hacerte una versión más corta (5–6 líneas) que muchos profesores prefieren en los informes de laboratorio.
#### 1.2 Diagramas
<img width="1199" height="450" alt="image" src="https://github.com/user-attachments/assets/87bca2b5-6d05-46f2-9713-f77d0624e3d8" />

# Sumador Completo de 4 Bits (Ripple Carry Adder)

Este repositorio contiene el esquema lógico de un **Sumador de 4 bits con propagación de acarreo** construido mediante compuertas lógicas discretas.

##  Descripción General

El circuito es capaz de sumar dos números binarios de 4 bits cada uno, produciendo una suma de 4 bits y un bit de acarreo de salida. El diseño se basa en la conexión en cascada de cuatro **Sumadores Completos** (Full Adders) de 1 bit.

##  Entradas y Salidas

### Entradas:
* **A [A3:A0]:** Primer operando de 4 bits. `A0` es el bit menos significativo (LSB) y `A3` es el más significativo (MSB).
* **B [B3:B0]:** Segundo operando de 4 bits.
* **Ci (Carry In):** Acarreo de entrada inicial. Normalmente se conecta a `0` para una suma estándar, pero permite encadenar este módulo con otros sumadores para operar con más bits.

### Salidas:
* **S [S3:S0]:** Resultado de la suma de 4 bits.
* **Co (Carry Out):** Acarreo de salida final. Indica si hubo un desbordamiento (overflow) al sumar los bits más significativos.

##  Lógica del Circuito (Por Etapa)

Cada bit individual utiliza un Sumador Completo estándar compuesto por:
* **2 Compuertas XOR:** Calculan la suma de los bits de entrada y el acarreo previo (`A XOR B XOR C_in`).
* **2 Compuertas AND y 1 Compuerta OR:** Calculan el acarreo de salida hacia la siguiente etapa. El acarreo se activa si dos o más de las entradas (`A`, `B`, o `C_in`) son `1`.

## ⚙️ Funcionamiento (Propagación de Acarreo)

El comportamiento de este circuito se caracteriza por el efecto "Ripple" o propagación:
1. La primera etapa (derecha) suma `A0`, `B0` y `Ci`, produciendo el bit de suma `S0` y un acarreo intermedio.
2. Este acarreo viaja a la siguiente etapa actuando como entrada para la suma de `A1` y `B1`.
3. El proceso se propaga secuencialmente hasta llegar a la última etapa (`A3`, `B3`), la cual genera la suma final `S3` y el acarreo de salida `Co`.

## Simulaciones 

### 1. Simulación del sumador/restador
<img width="1600" height="623" alt="image" src="https://github.com/user-attachments/assets/c27683c3-deb6-4dca-86cf-1276b6340f9b" />


#### 1.1 Descripción

un sumador de 4 bits descrito en Verilog, visualizado a través del analizador GTKWave. A diferencia del diseño de un solo bit, esta simulación opera con buses de datos (A[3:0], B[3:0], S[3:0]) representados en formato hexadecimal para agilizar su análisis. La presencia de las señales internas de acarreo (c0, c1, c2) evidencia la implementación de una arquitectura de tipo Ripple-Carry (sumador de propagación de acarreo), donde cuatro sumadores completos se conectan en cascada. Al examinar el comportamiento de las ondas, se comprueba que el módulo realiza las operaciones aritméticas de manera exacta, destacando la correcta activación del acarreo de salida (Cout) en situaciones de desbordamiento continuo (por ejemplo, al sumar A=1 y B=F, que genera una salida S=0 y Cout=1); lo que confirma la funcionalidad integral del diseño estructural para su futura síntesis en un FPGA.

#### 1.2 Diagrama

<img width="1600" height="811" alt="image" src="https://github.com/user-attachments/assets/db5575aa-b293-48f9-bb77-3db419fcccf4" />



## Evidencias de implementación
<img width="310" height="191" alt="image" src="https://github.com/user-attachments/assets/f8f41a1a-03d7-4819-b2ab-dec90e9338ed" />


## Conclusiones

###Validación de la Lógica Base:

La simulación del sumador completo de 1 bit confirmó que el diseño a nivel de compuertas lógicas (estructural) funciona correctamente. Las señales internas comprobaron que la lógica combinacional cumple con la tabla de verdad teórica sin presentar estados indefinidos.

###Escalabilidad del Diseño: 

La evolución hacia el sumador de 4 bits demostró el principio de modularidad en Verilog. La correcta propagación de las señales de acarreo internas (c0, c1, c2) confirma que la conexión en cascada de los módulos de 1 bit (arquitectura Ripple-Carry) se implementó con éxito.

###Gestión de Desbordamiento:

Las pruebas con buses de 4 bits (representados en formato hexadecimal) permitieron verificar que el sistema identifica y maneja los desbordamientos con precisión. La bandera de acarreo de salida (Cout) se activó en los momentos exactos en los que la suma aritmética superó la capacidad máxima de 4 bits (valor 15 o F).

###Viabilidad para Hardware:
El análisis de las formas de onda en GTKWave garantiza que el comportamiento del circuito descrito a nivel de transferencia de registros (RTL) es predecible y estable. Por lo tanto, el código Verilog validado está completamente listo para la fase de síntesis e implementación física en el FPGA.

## Referencias
