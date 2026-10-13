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
