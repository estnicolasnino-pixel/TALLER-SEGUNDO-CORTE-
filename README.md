# TALLER-SEGUNDO-CORTE
# Real-Time Drone Waypoint Navigation via ESP32 Hardware Controller & PyBullet

[![Python](https://img.shields.io/badge/Python-3.12-blue.svg)](https://www.python.org/)
[![PyBullet](https://img.shields.io/badge/Simulator-PyBullet-orange.svg)](https://github.com/utiasDSL/gym-pybullet-drones)
[![ESP32](https://img.shields.io/badge/Hardware-ESP32-green.svg)](https://www.espressif.com/)

Sistema de control en tiempo real para simulación de drones (`gym-pybullet-drones`) utilizando un microcontrolador **ESP32** como hardware físico de mando mediante comunicación serial (`pyserial`). El sistema permite conmutar dinámicamente la posición de un cuadricóptero entre diferentes waypoints espaciales (A, B y C) a través de pulsadores físicos y un lazo de control PID (`DSLPIDControl`).

---

##  Características Principales
- **Arquitectura Asíncrona (Multihilo):** Un hilo secundario dedicado en Python monitorea continuamente el puerto serial sin bloquear la frecuencia del bucle de control de la simulación física (240 Hz / 48 Hz).
- **Control PID Integrado:** Uso de la cinemática y control de velocidad/posición de `gym-pybullet-drones` para un vuelo estable.
- **Hardware en el Bucle (HIL - Hardware-in-the-Loop):** Interacción física mediante botones conectados a un ESP32 que actúan como comandos de navegación espacial.

---

##  Requisitos de Software y Hardware

### Hardware
- 1x Placa de desarrollo **ESP32**.
- 3x Pulsadores (botones táctiles).
- Cables de conexión.

### Software
- Python 3.12+
- Arduino IDE (para flashear el ESP32)
- Librerías de Python:
  ```bash
  pip install numpy pyserial pybullet gymnasium


## Control HIL (Hardware-in-the-Loop) de Robot Baxter en PyBullet con ESP32

Sistema de control en tiempo real para el efector final del brazo derecho de un modelo robótico **Baxter** simulado en **PyBullet**, operado físicamente mediante un joystick analógico y un microcontrolador **ESP32** a través de comunicación serial (`pyserial`).

---

##  Características del Proyecto
* **Comunicación Serial HIL:** Lectura continua y multihilo de datos analógicos y digitales desde un ESP32 a 115200 baudios.
* **Control Proporcional y Fluido:** Conversión de las coordenadas del joystick en velocidades continuas para el posicionamiento cartesiano.
* **Cinemática Inversa (IK):** Cálculo en tiempo real de las articulaciones del brazo derecho de Baxter mediante PyBullet `calculateInverseKinematics`.
* **Control de Pinza (Gripper):** Conmutación de estado (Abierto/Cerrado) mediante el pulsador integrado del joystick.

---

## Requisitos de Hardware y Software

### Hardware
* Microcontrolador **ESP32**.
* Joystick analógico de doble eje con botón integrado (ej. **KY-023**).
* Cables de conexión.

### Software y Librerías (Python 3.12)
* `pybullet`
* `pyserial`
* `numpy`

---

# Estructura del Repositorio

 # Código fuente para el ESP32
 # Modelos URDF y recursos de Baxter
 # Script principal de simulación y control HIL
 # Documentación del proyecto





## Sistema de Control en Tiempo Real para Simulación Robótica con ESP32 y PyBullet

<p align="center">
  <b>Universidad Militar Nueva Granada</b><br>
  <b>Ingeniería Mecatrónica — Taller del Segundo Corte</b>
</p>

---

##  Descripción del Proyecto
Este proyecto implementa una **consola de mandos física** basada en un microcontrolador **ESP32** y un joystick analógico para gobernar de manera fluida, en tiempo real y bidireccional la movilidad y los efectores finales (pinza) de un robot simulado en el entorno físico de **PyBullet** mediante comunicación serial UART.

---

##  Arquitectura del Sistema

1. **Hardware de Mando:**
   * Microcontrolador **ESP32**.
   * Joystick analógico **KY-023** (conectado a canales ADC y pines digitales para el pulsador).
   * Sistema de filtrado por *deadzone* y normalización de coordenadas.

2. **Comunicación:**
   * Enlace serial USB por **UART** a `115200` baudios.
   * Transmisión de tramas normalizadas en formato CSV: `X, Y, Botón`.

3. **Software de Simulación:**
   * Entorno en **Python** utilizando las librerías `pybullet`, `pybullet_data` y `pyserial`.
   * Búfer serial optimizado en tiempo de ejecución para eliminar latencias y garantizar una respuesta fluida.

---

## Estructura del Repositorio

```text
 Robot-Movilidad-Real
│
├── ESP32_Joystick/
│   └──  codigo_joystick.ino       # Código fuente en C++ para la lectura de la ESP32
│
├──  Python_PyBullet/
│   └── 📄 main.py                   # Script principal de la simulación y control serial
│
├──  assets/
│   └── 🎥 demo_funcionamiento.mp4   # Video demostrativo de la prueba física y simulada
│
└──  README.md                     # Documentación oficial del proyecto
