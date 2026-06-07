# 🚀 Riego Automático ESP32 - "NASA Edition" v3.0

Un sistema de riego automatizado de alto rendimiento basado en **ESP32**, diseñado para monitorizar y controlar el riego de huertos y jardines. Cuenta con una interfaz web minimalista (Dark Mode), reloj interno sincronizado por NTP, protección anti-inundación y soporte para sensores de humedad capacitivos.

![Dashboard Web](https://github.com/d4nysj/Esp32_Riego_Automatico/blob/main/Images/1.png?raw=true)

## ✨ Características Principales

* 🕒 **Doble Programación Diaria**: Hasta 2 riegos automáticos independientes sincronizados con la zona horaria automática (Madrid CET/CEST).
* 📱 **Interfaz Web Avanzada**: Panel de control responsive y minimalista ("Dark Mode") servido directamente desde el ESP32.
* 📊 **Estadísticas y Logs**: Registro histórico de los últimos 20 riegos, estimación de litros consumidos y log del sistema con los últimos 60 eventos guardados en RAM/Flash.
* 💧 **Soporte para Sensor de Humedad**: Integración con sensor analógico para evitar riegos innecesarios si el suelo ya está húmedo (umbral configurable).
* 🛡️ **Watchdogs de Seguridad**: Sistema de corte automático si el riego supera la duración máxima configurada (prevención de inundaciones).
* 📡 **Reconexión Inteligente**: Reconexión WiFi automática y resincronización NTP sin bloquear el flujo principal.
* 🛠️ **Página de Diagnóstico**: Monitorización en tiempo real de la RAM libre, temperatura de la CPU, RSSI de la señal WiFi y estado de la partición NVS.

![Página de Configuración y Logs](https://github.com/d4nysj/Esp32_Riego_Automatico/blob/main/Images/2.png?raw=true)

## 🔌 Hardware y Conexiones

El hardware principal consta de una placa ESP32, un módulo de relé y un sensor de humedad opcional.

| Componente | Pin ESP32 | Notas |
| :--- | :--- | :--- |
| **Relé HW-482 (Señal)** | `GPIO26` | Control de la electroválvula o bomba de agua. (HIGH=ON, LOW=OFF) |
| **Sensor de Humedad** | `GPIO34` | Sensor capacitivo analógico (Opcional). |
| **Relé (VCC)** | `5V / VIN` | Alimentación del módulo relé. |
| **Relé (GND)** | `GND` | Masa común. |

## 🚀 Instalación y Uso

1.  Clona este repositorio.
2.  Abre el código `.ino` en el Arduino IDE o VSCode con PlatformIO.
3.  Instala las librerías necesarias (incluidas en el core del ESP32: `WiFi.h`, `WebServer.h`, `Preferences.h`).
4.  Edita las credenciales WiFi en la sección de configuración:
    ```cpp
    const char* WIFI_SSID     = "TU_SSID";
    const char* WIFI_PASS     = "TU_CONTRASENA";
    ```
5.  Sube el código a tu placa ESP32.
6.  Abre el Monitor Serie (115200 baudios) para obtener la dirección IP asignada.
7.  Accede a la IP desde cualquier navegador en tu red local.

![Historial de Riegos](https://github.com/d4nysj/Esp32_Riego_Automatico/blob/main/Images/3.png?raw=true)

## ⚙️ Funcionamiento Interno

El firmware hace uso intensivo de la librería `Preferences` para guardar la configuración, umbrales y estadísticas de litros totales en la memoria NVS flash de la placa. Esto garantiza que ante cortes de luz, los datos persistan y el sistema recupere su programación original de manera autónoma.

---
*By D4Nyos*
