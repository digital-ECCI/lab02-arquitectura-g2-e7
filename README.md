[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/Px-uYaj2)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=22891300&assignment_repo_type=AssignmentRepo)
# Lab02 - Sumador/Restador de 4 bits

# Integrantes


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

#### 1.1 Descripción

#### 1.2 Diagrama


## Evidencias de implementación
<img width="310" height="191" alt="image" src="https://github.com/user-attachments/assets/f8f41a1a-03d7-4819-b2ab-dec90e9338ed" />


## Conclusiones


## Referencias
