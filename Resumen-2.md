Cristian sotelo 134770
Juan Pablo Contreras 134126
carlos andres estupiñan 82149

#Temporizadores en Microcontroladores (PIC18F4550)

## 1. ¿Qué es un temporizador?
- Módulo de conteo presente en microcontroladores.
- Resoluciones comunes: *8 o 16 bits*.
- Usos:
  - Medición de tiempo.
  - Generación de señales (como reloj).
  - Conteo de eventos.

---

## 2. Aplicaciones
- *Temporizador*: mide intervalos de tiempo.
- *Contador*: cuenta eventos externos.
- Utilizado para sincronización o generación de interrupciones.

---

## 3. Principios de funcionamiento
- Cuenta desde 0 hasta 2ⁿ - 1.
- Al desbordarse, genera una *interrupción*.

---

## 4. Problemas de lectura
- Microcontroladores de 8 bits leyendo timers de 16 bits pueden generar errores.
- Se usan *registros temporales* para evitar inconsistencias en la lectura.

---

## 5. Señales de reloj
- Temporizadores se sincronizan con:
  - *Señales internas* (del oscilador).
  - *Señales externas* (flancos en pines).

---

## 6. Prescaler
- Reduce la frecuencia del reloj para lograr *conteos más largos*.
- Pierde resolución pero permite medir *tiempos más grandes*.

---

## 7. Granularidad
- Resolución mínima de medición.
- Ejemplo:
  - Reloj = 1 MHz.
  - Timer 8 bits sin prescaler: máx. 255 µs de conteo (1 µs por ciclo).

---

## 8. Contador con señal externa
- Cuenta *flancos* (subida o bajada) en pines digitales.
- Útil para conteos *no periódicos*.

---

## 9. Uso del cristal
- Temporizador usa oscilador externo.
- Ideal para aplicaciones de *reloj en tiempo real (RTC)*.

---

## 10. Temporizadores del PIC18F4550
| Timer | Resolución | Modo          | Notas                         |
|-------|-------------|----------------|-------------------------------|
| TMR0  | 8/16 bits   | Timer/Contador | Prescaler, interrupciones     |
| TMR1  | 16 bits     | Timer/Contador |                               |
| TMR2  | 8 bits      | Solo Timer     |                               |
| TMR3  | 16 bits     | Timer/Contador |                               |

---

## 11. Timer 0 en detalle
- Funciona como *temporizador o contador*.
- Prescaler de *8 bits*.
- Registro de conteo: *TMR0H:TMR0L (16 bits)*.
- *Lectura/escritura posible* durante ejecución.
- Genera interrupción por desborde (valor 255 en modo 8 bits).

---

## 12. Cálculos de tiempo

### Fórmulas:
- Fosc / 4 = Frecuencia de instrucción
- T_instrucción = 1 / (Fosc / 4)
- T_desbordamiento = (MaxCount - TMRx) * T_instrucción * Prescaler

## 13. Precarga
Para lograr un retardo de 5 ms:

```text
TMRx = 65536 - (T_conteo / (T_instrucción * Prescaler))
TMRx = 65536 - (5 ms / 1 µs) = 60536
