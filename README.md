# Práctica 2 : INTERRUPCIONES
## Introducción de la práctica
En esta práctica se trabajan las interrupciones, donde dispondremos, además del microcontrolador ESP32.

## Funcionamiento
Descripción del Funcionamiento
Generación de Interrupciones: Al conectar un cable entre el puerto G18 (GPIO 18) y GND en la ESP32, se generarán interrupciones cada vez que el circuito se cierre.
Visualización de Interrupciones: Cada vez que se genera una interrupción, el programa incrementa un contador y muestra el número de presiones del botón en la salida serie. También se enciende un LED en el procesador para indicar la interrupción.
Desvinculación de Interrupciones: Pasado un minuto, las interrupciones en el pin GPIO 18 se desactivan.

El programa imprime la cantidad de veces que se ha presionado el botón:
Button 1 has been pressed 1 times
Button 1 has been pressed 2 times
Button 1 has been pressed 3 times
Button 1 has been pressed 4 times

## Estructura del codigo

PIN:El pin al que está conectado el botón (const uint8_t PIN;).
numberKeyPresses: Contador del número de veces que se ha presionado el botón (uint32_t numberKeyPresses;).
pressed: Indicador de si el botón está presionado (bool pressed;).

## Funciones
Función de Interrupción (ISR):
Incrementa el contador de presiones del botón.
Establece el indicador pressed como verdadero.
Función setup():
Configura el pin del botón como entrada con resistencia pull-up interna.
Adjunta la ISR al pin del botón.
Función loop():
Comprueba si el botón ha sido presionado.
Imprime el número de veces que se ha presionado el botón en la salida serie.

## Resumen del Funcionamiento
Configuración Inicial:
El pin GPIO 18 se configura como entrada con resistencia pull-up y se vincula a la ISR.
Detección de Presiones:
Cada vez que se detecta una presión del botón (circuito cerrado entre GPIO 18 y GND), la ISR incrementa el contador y marca el botón como presionado.
Impresión en Serie:
En el bucle principal, si el botón ha sido presionado, se imprime el número de presiones en la salida serie.
Desvinculación de Interrupciones:
Después de un minuto, se desactivan las interrupciones en el pin GPIO 18.
Este programa permite la detección y conteo de presiones de un botón utilizando interrupciones en una ESP32, proporcionando una manera eficiente de manejar eventos de entrada sin necesidad de estar constantemente verificando el estado del botón en el bucle principal.


