# 🚀 Gonzaga Smart Wing - ¡Bienvenidos a nuestro código! 

¡Hola! Este es el repositorio oficial de **Gonzaga Smart Wing**, el equipo de robótica del **Colegio Gonzaga**. Aquí guardamos todo el código en Java que hemos desarrollado para el robot de esta temporada de la **Copa Ka'i** y **FTC**. 

---

## 🛠️ ¿Cómo organizamos nuestro código? (Nuestra Arquitectura)

Al principio teníamos todo el código amontonado en archivos gigantes, lo que hacía que configurar los motores en el TeleOp y en el Autónomo fuera un dolor de cabeza (¡y muy peligroso si algo fallaba en los pits!). 

Para solucionarlo, decidimos ordenar los archivos y dividir el robot en módulos independientes. Ahora, los programas de competencia no buscan motores sueltos, sino que hablan directamente con un "coordinador maestro" (`OmniRobot`).

### 📦 El Hardware por separado (Not an OpModes)
* **`ChasisMec.java`**: Aquí está guardado todo lo que tiene que ver con mover el robot. Este archivo se encarga de invertir el motor que va al revés, controlar el manejo con el joystick (*Arcade Drive*) y hacer los cálculos matemáticos para que los encoders midan en centímetros reales.
* **`LanzadorMec.java`**: Este módulo controla exclusivamente nuestro sistema de disparo. Sabe en qué puertos están el motor `m3` y los dos servos de las compuertas, y tiene las funciones exactas para encender el motor y abrir o retraer los servos al lanzar.
* **`OmniRobot.java`**: Es el "capitán" del robot. Une al chasis y al lanzador en un solo bloque para que los códigos de la pista sean mucho más limpios y fáciles de leer.

### 🎮 Los Modos de Juego (OpModes de Competencia)
* **`RobotTeleOp_PS4.java` (Modo Conducido)**: El programa para manejar el robot en la pista con el control. Le añadimos una zona muerta a los joysticks para evitar movimientos fantasma, ajustamos una compensación para que el robot avance recto y configuramos una vibración en el control que le avisa al piloto cuando el motor de tiro está listo.
* **`RobotAutoDriveByEncoder_Linear.java` (Modo Autónomo)**: Nuestra estrategia automática de 30 segundos. El robot arranca, avanza exactamente 65 cm usando los encoders, enciende el motor de tiro, abre y cierra las compuertas tres veces de forma secuencial para soltar las 3 pelotas, y finalmente retrocede para quedarse en zona segura.

---

## 📈 Ficha Técnica de Nuestro Robot
* **Controlador**: REV Robotics Control Hub.
* **Motores de Tracción**: goBILDA Yellow Jacket 19.2:1 (537.7 pulsos por revolución).
* **Ruedas**: Diámetro de 9.6 cm.
* **Sistema de Disparo (motores de disparo)**: Un motor directo para máximas RPM y dos servos para controlar las compuertas de retención.

---

## 👨‍💻 Sobre Nosotros

Este algoritmo fue diseñado, programado y probado en la pista por nosotros, los estudiantes de 3er y 4to año de bachillerato del **Colegio Gonzaga**, con el apoyo y la guía de nuestra profesora de Informática. 

Escribir el código de esta manera nos tomó más tiempo y esfuerzo, pero nos demostró que podemos programar como ingenieros reales. ¡Nos vemos en la pista!
