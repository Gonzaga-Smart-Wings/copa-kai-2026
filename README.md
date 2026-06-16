# 🚀 Gonzaga Smart Wing - Welcome to our code!

Hi there! This is the official repository for **Gonzaga Smart Wing**, the robotics team from **Colegio Gonzaga**. Here, we keep all the Java code we have developed for our robot this season in the **Copa Ka'i** and **FTC**.

---

## 🛠️ How do we organize our code? (Our Architecture)

At first, we had all of our code piled up in giant files, which made configuring the motors in both TeleOp and Autonomous a real headache (and very dangerous if something went wrong in the pits!). 

To fix this, we decided to tidy up our files and split the robot into independent modules. Now, our competition programs don't look for loose motors; instead, they talk directly to a "master coordinator" (`OmniRobot`).

### 📦 Hardware Separated by Modules (Not an OpModes)
* **`ChasisMec.java`**: Everything related to moving the robot is stored here. This file handles reversing the motor that runs backwards, managing the joystick driving (*Arcade Drive*), and doing the math calculations so the encoders can measure in real centimeters.
* **`LanzadorMec.java`**: This module exclusively controls our shooting system. It knows exactly which ports the `m3` motor and the two gate servos are plugged into, and it features the exact functions to power up the motor and open or retract the servos when launching.
* **`OmniRobot.java`**: This is our robot's "captain." It unites the chassis and the launcher into a single block so that our on-track codes look much cleaner and are way easier to read.

### 🎮 Game Modes (Competition OpModes)
* **`RobotTeleOp_PS4.java` (Driver-Controlled Mode)**: The program used to drive the robot on the field using the controller. We added a deadzone to the joysticks to prevent ghost movements, adjusted a compensation value so the robot drives straight, and set up a controller rumble to alert the driver when the shooting motor is ready.
* **`RobotAutoDriveByEncoder_Linear.java` (Autonomous Mode)**: Our 30-second automatic strategy. The robot starts up, drives exactly 65 cm using the encoders, turns on the shooting motor, opens and closes the gates three times sequentially to release the 3 balls, and finally backs up to stay in a safe zone.

---

## 📈 Our Robot's Tech Specs
* **Controller**: REV Robotics Control Hub.
* **Drive Motors**: goBILDA Yellow Jacket 19.2:1 (537.7 pulses per revolution).
* **Wheels**: 9.6 cm diameter.
* **Shooting System**: One direct motor for maximum RPM and two servos to control the holding gates.

---

## 👨‍💻 About Us

This algorithm was designed, programmed, and track-tested by us, the 3rd and 4th-year high school students of **Colegio Gonzaga**, with the support and guidance of our Computer Science teacher.

Writing the code this way took us more time and effort, but it proved to us that we can program like real engineers. See you on the field!
