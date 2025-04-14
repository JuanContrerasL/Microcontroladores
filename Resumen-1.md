Cristian sotelo 134770
Juan Pablo Contreras 134126
carlos andres estupiñan 82149

# Presentación detallada: Teclado y Periféricos en Microcontroladores (PIC 18F4550)

## 1. Hardware en microcontroladores

En los sistemas basados en microcontroladores, el hardware se refiere a los dispositivos físicos que interactúan con el entorno. Estos se clasifican en:

- *Dispositivos de entrada*: sensores, potenciómetros, pulsadores, botones, etc.
- *Dispositivos de salida*: LEDs, displays, motores, actuadores, entre otros.

Una correcta implementación garantiza estabilidad y confiabilidad en sistemas embebidos.

---

## 2. Pulsadores y botones: definición y funcionamiento

### 2.1 Pulsadores

- Funcionan aplicando presión mecánica.
- Cambian su estado solo mientras están presionados.
- Tipos:
  - *Normalmente abierto (NO)*: solo conduce al presionarse.
  - *Normalmente cerrado (NC)*: conduce normalmente, se interrumpe al presionar.

### 2.2 Botones

- Mantienen su nuevo estado con un solo clic.
- Requieren otra pulsación para cambiar de nuevo.
- Incluyen dipswitches.

> *Nota:* Su lectura precisa requiere considerar el efecto rebote.

---

## 3. Estructura mecánica y efecto rebote

### 3.1 Construcción mecánica

- Dos láminas metálicas se cierran con presión.
- No aplicable a teclados capacitivos o resistivos.

### 3.2 Efecto rebote (bounce effect)

- Las láminas vibran por su elasticidad, generando oscilaciones.
- Oscila entre abierto y cerrado durante 20–40 ms.
- Puede causar múltiples señales en una sola pulsación.

> *Implicación:* Sin corrección, una sola pulsación puede ser leída múltiples veces.

---

## 4. Soluciones al efecto rebote

### 4.1 Solución por hardware: Filtro RC

- Usa una resistencia (R) y un condensador (C).
- Suaviza los cambios bruscos del contacto mecánico
