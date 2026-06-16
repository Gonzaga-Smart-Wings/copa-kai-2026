# 🚀 Gonzaga Smart Wing - Temporada 2026

¡Bienvenidos al repositorio oficial de desarrollo de software de **Gonzaga Smart Wing**, equipo de robótica del **Colegio Gonzaga**! 

Este repositorio contiene la arquitectura de software diseñada e implementada para competir en la **Copa Ka'i** y la plataforma **FIRST Tech Challenge (FTC)**. Nuestro enfoque para esta temporada se basa en la modularidad, la legibilidad y la precisión cinemática mediante el uso de programación orientada a objetos en Java.

---

## 🛠️ Estructura del Software (Arquitectura Modular)

A diferencia de los scripts planos tradicionales, hemos abstraído el hardware del robot en subsistemas independientes coordinados por una clase maestra. Esto permite realizar reparaciones rápidas en pits y mantener modos de juego sumamente limpios.

### 📦 Módulos de Hardware (Not an OpModes)
* **`ChasisMec.java`**: Controla el tren motriz diferencial. Absorbe las inversiones lógicas de los motores traccionados cara a cara, el algoritmo de control en pista (*Arcade Drive*) y las matemáticas de conversión para los encoders.
* **`LanzadorMec.java`**: Gestiona el motor de tiro de alta velocidad (`m3`) y la sincronización secuencial de los servos encargados de las compuertas del disparador.
* **`OmniRobot.java`**: El "maestro de hardware". Unifica los objetos del chasis y del lanzador en una sola entidad cohesiva para que los programas de competencia interactúen con un único punto de acceso.

### 🎮 Modos de Juego (OpModes de Competencia)
* **`RobotTeleOp_PS4.java` (Teleoperado)**: Permite el control manual del robot durante el período de juego conducido. Cuenta con suavizado de zonas muertas en los joysticks, compensación de tracción lineal y retroalimentación háptica (*Rumble*) en el mando para alertar al operador durante el ciclo de tiro.
* **`RobotAutoDriveByEncoder_Linear.java` (Autónomo)**: Ejecuta de forma 100% automatizada la estrategia inicial de la ronda: salida limpia de la zona de inicio, posicionamiento cinemático mediante conteo de pulsos relativos por encoder (`RUN_TO_POSITION`), vaciado secuencial de las 3 pelotas en el objetivo y retorno lineal a la zona segura.

---

## 📈 Especificaciones de Hardware Controladas
* **Control Central**: REV Robotics Control Hub.
* **Motores de Tracción**: goBILDA Yellow Jacket 19.2:1 (537.7 pulsos por revolución).
* **Ruedas**: Diámetro de 9.6 cm (Configuración diferencial de dos ruedas).
* **Actuadores de Tiro**: Motor directo para RPM máximas y dos servos de posición angular para las compuertas de retención.

---

## 👨‍💻 Desarrollo y Mentoría

Este proyecto es el resultado del esfuerzo, diseño de algoritmos y pruebas en pista realizadas por los estudiantes de bachillerato (3er y 4to año) del equipo de robótica, bajo la coordinación de la dirección de Informática del **Colegio Gonzaga**.

> *"La excelencia no es un acto, es un hábito. Estructurando código para ganar, diseñando el futuro de la robótica educativa."*
