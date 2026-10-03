# Lera — Line Following Robot



**13th Prototype • ESP32-WROOM • Custom 6-Sensor Array • PID Control • Wi-Fi Web Interface**

<br>

**🥇 14× 1st Place &nbsp; | &nbsp; 🥈 12× 2nd Place**

</p>

---

# 🚀 Project Overview

**Lera** is our **13th prototype line following robot**, developed and continuously improved for regional line-following competitions across Uzbekistan.

We competed with **two robots across 12 regions** and achieved:

- 🥇 **14× 1st Place**
- 🥈 **12× 2nd Place**

The robot combines a **custom-built 6-sensor line detection system**, **ESP32-WROOM**, **TB6612FNG motor driver** and a **PID control algorithm**.

One of the main features of Lera is its built-in **Wi-Fi configuration system**, which allows us to connect to the robot from a phone or computer and open a local web interface using the robot's IP address.

Instead of repeatedly uploading new firmware to change PID parameters, we can adjust the robot's settings directly from the web interface.

---

# 🏆 Competition Record

Across **12 regional competitions**, our two robots achieved:

| Result | Number |
|---|---:|
| 🥇 **1st Place** | **14** |
| 🥈 **2nd Place** | **12** |
| 🏅 **Total Podium Finishes** | **23** |

These results came from repeated development, testing, tuning and competition experience with the Lera line-following platform.

---

# ✨ Project Highlights

- 🤖 **13th prototype** of our line-following robot
- 🥇 **41× 1st Place**
- 🥈 **12× 2nd Place**
- 🗺️ Competed across **12 regions**
- 🤖 Used **2 robots** in regional competitions
- 🖐️ Custom-built **6-sensor array**
- 🧠 **PID control algorithm**
- ⚡ **ESP32-WROOM**
- 🔌 **TB6612FNG motor driver**
- 📡 Wi-Fi configuration
- 🌐 Local web interface accessed through IP address
- 🎚️ Real-time PID tuning
- ⚙️ Motor speed adjustment
- 👀 Live sensor-state monitoring
- 💻 No need to repeatedly upload code for basic tuning

---

# 🧠 System Architecture

The main control flow of Lera is:

```text
                 ┌──────────────────────┐
                 │   6 Custom Sensors   │
                 └──────────┬───────────┘
                            │
                            ▼
                    ┌──────────────┐
                    │ ESP32-WROOM  │
                    │              │
                    │ Sensor Read  │
                    │ PID Control  │
                    │ Wi-Fi Server  │
                    └──────┬───────┘
                           │
                ┌──────────┴──────────┐
                │                     │
                ▼                     ▼
         ┌────────────┐      ┌────────────────┐
         │ PID Output │      │ Web Interface  │
         └─────┬──────┘      └────────────────┘
               │
               ▼
         ┌────────────┐
         │ TB6612FNG  │
         │ Motor Driver│
         └─────┬──────┘
               │
          ┌────┴────┐
          ▼         ▼
       Motor L    Motor R
```

---

# 👤 My Role

My main contribution to the Lera project included the development and improvement of the line-following robot platform.

The project involved working with:

- 🤖 Robot development
- 📐 Sensor placement and integration
- ⚡ Electronics
- 🧠 PID tuning
- 🌐 Wi-Fi configuration system
- 🧪 Testing and competition preparation

> Team member roles and individual responsibilities can be added in the `Team/` folder.

---

# 👁️ Custom 6-Sensor System

One of the key features of Lera is its **custom-built 6-sensor line detection system**.

Instead of relying only on a ready-made sensor module, we built and integrated our own sensor array for the robot.

### Sensor Array

![Sensor Array](Sensors/sensor-array.jpg)

### Sensor Layout

![Sensor Layout](Sensors/sensor-layout.png)

The six sensors allow the ESP32 to determine the position of the black line and calculate the correction required for the robot.

---

# 👀 Live Sensor Monitoring

The sensor data can also be viewed from the robot's web interface.

The website shows **which sensors are currently detecting the black line**.

This makes testing and PID tuning much easier because we can see the sensor states while the robot is operating.

### Sensor Status

![Sensor Status](WebInterface/screenshots/sensor-status.jpg)

Example concept:

```text
Sensor 1   Sensor 2   Sensor 3   Sensor 4   Sensor 5   Sensor 6

   0          0          1          1          0          0

                      BLACK LINE
                         ▲
```

The live sensor state is useful for checking whether the sensor array is positioned and calibrated correctly.

---

# 🧠 PID Control

Lera uses a **PID control algorithm** for line tracking.

The PID controller uses the sensor information to calculate the robot's correction and adjust the motor speeds.

The main parameters are:

```text
Kp — Proportional
Ki — Integral
Kd — Derivative
```

The PID output is used to determine the left and right motor speed corrections.

### PID Concept

```text
Line Sensors
     │
     ▼
   Error
     │
     ▼
┌─────────────┐
│ PID Control │
│ Kp + Ki + Kd│
└──────┬──────┘
       │
       ▼
 Motor Correction
       │
   ┌───┴───┐
   ▼       ▼
Left Motor Right Motor
```

---

# 🌐 Wi-Fi Web Interface

One of the most important features of Lera is the **built-in Wi-Fi configuration system**.

The ESP32 creates the connection needed to access a local web interface.

We connect to the robot through Wi-Fi and open its **IP address in a browser**.

From the website, we can adjust the robot without repeatedly uploading new firmware.

### Web Interface Features

The interface allows us to:

- ⚙️ Adjust motor speed
- 🎚️ Adjust **Kp**
- 🎚️ Adjust **Ki**
- 🎚️ Adjust **Kd**
- 👀 View sensor states
- 🧪 Tune the robot during testing

### Why We Built It

Without the web interface, changing PID values would require:

```text
Change Code
   ↓
Compile
   ↓
Upload
   ↓
Test
   ↓
Change Again
   ↓
Upload Again
```

With Lera:

```text
Connect to Wi-Fi
      ↓
Open IP Address
      ↓
Change Settings
      ↓
Test Immediately
```

This made the tuning process much faster and more practical during testing.

---

# ⚙️ Web Interface Dashboard

### Main Dashboard

![Dashboard](WebInterface/screenshots/dashboard.jpg)

### PID Settings

![PID Settings](WebInterface/screenshots/pid-settings.jpg)

### Motor Speed

![Motor Settings](WebInterface/screenshots/motor-settings.jpg)

### Sensor Monitoring

![Sensor Status](WebInterface/screenshots/sensor-status.jpg)

---

# ⚡ Electronics

The main electronic components of Lera include:

| Component | Model | Purpose |
|---|---|---|
| 🧠 Microcontroller | **ESP32-WROOM** | Main control, PID and Wi-Fi |
| 🔌 Motor Driver | **TB6612FNG** | Controls left and right motors |
| 👁️ Sensor Array | **6 Custom Sensors** | Line detection |
| ⚙️ Motors | `MODEL` | Robot movement |
| 🔋 Battery | `MODEL` | Power supply |

### ESP32-WROOM

![ESP32-WROOM](Electronics/esp32-wroom.jpg)

The ESP32-WROOM was selected not only for robot control but also because it allowed us to implement the **Wi-Fi-based configuration interface**.

### TB6612FNG

![TB6612FNG](Electronics/tb6612fng.jpg)

The TB6612FNG is used to control the robot's motors.

### Wiring

![Wiring](Electronics/wiring.jpg)

---

# 🔧 Development Process

Lera is the result of continuous development through multiple prototypes.

The current robot represents our **13th prototype**.

```text
💡 Idea
  ↓
🧪 Early Prototypes
  ↓
🔄 Improvements
  ↓
🤖 Prototype 13 — Lera
  ↓
👁️ Custom Sensor Array
  ↓
🧠 PID Implementation
  ↓
🌐 Wi-Fi Web Interface
  ↓
🧪 Testing & Tuning
  ↓
🏆 Competition
  ↓
🔄 Further Improvements
```

---

## 01 — Concept

We started by defining the requirements for a fast and controllable line-following robot.

![Concept](Development/01-concept.jpg)

---

## 02 — Sensor Development

The custom six-sensor array was developed and integrated into the robot.

![Sensor Development](Development/02-sensor-build.jpg)

---

## 03 — Electronics

The ESP32-WROOM and TB6612FNG were integrated with the sensor and motor systems.

![Electronics](Development/03-electronics.jpg)

---

## 04 — Assembly

The robot was assembled and prepared for testing.

![Assembly](Development/04-assembly.jpg)

---

## 05 — PID Tuning

PID values were repeatedly tested and adjusted to improve line tracking.

![PID Tuning](Development/05-pid-tuning.jpg)

---

## 06 — Web Interface

The Wi-Fi-based configuration interface was developed to make PID and motor tuning easier.

![Web Interface](Development/06-web-interface.jpg)

---

## 07 — Final Robot

The final prototype was prepared for regional competitions.

![Final Robot](Development/07-final-robot.jpg)

---

# 🧪 Testing & Tuning

Testing focused on:

- Sensor calibration
- Sensor positioning
- Motor speed
- PID parameters
- Line tracking stability
- Cornering
- Reaction speed
- Robot consistency

The web interface allowed us to make adjustments much more efficiently during this process.

---

# 🏁 Competition Experience

Lera was used in regional line-following competitions across Uzbekistan.

We participated in **12 regions with two robots** and achieved:

### 🥇 14× First Place
<img width="960" height="1280" alt="photo_2026-06-10_20-59-04" src="https://github.com/user-attachments/assets/32ba3b34-82cc-448d-9bb9-6b964dcf660b" />



### 🥈 12× Second Place

<img width="1920" height="2560" alt="photo_2026-07-18_19-14-20" src="https://github.com/user-attachments/assets/6b324b4c-d3e7-4576-ade8-36d4333bb452" />

---

# 📸 Competition Gallery

<img width="1280" height="960" alt="photo_2026-07-13_19-54-44" src="https://github.com/user-attachments/assets/ded8f85c-7107-438a-a5f5-2cc2c87f76ff" />
<img width="1280" height="720" alt="photo_2026-10-03_10-44-51" src="https://github.com/user-attachments/assets/c3869ef1-f35f-44f1-996b-a4f49f728a85" />
<img width="1280" height="719" alt="photo_2026-10-03_10-44-46" src="https://github.com/user-attachments/assets/1f6332b3-6f54-44a9-8dc2-4f614477ce2d" />


---

# 🎥 Competition & Testing Videos

The project also includes short videos from testing sessions and competitions.

### Testing Video 01

[▶️ Watch Video](https://www.youtube.com/watch?v=BXI1YcyJU3o)

### Competition Highlights

[▶️ Watch Video](https://www.youtube.com/shorts/5Y-Mw3sAbBQ)


# 💻 Firmware

The robot firmware includes the main control logic for:

- Sensor reading
- Line position calculation
- PID control
- Motor speed control
- Wi-Fi communication
- Web interface
- Runtime configuration

Source code:

```text
Firmware/ akbaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaarni  kodi
└── src/
```

---

# 🌐 Web Interface

The web interface is documented separately in:

```text
WebInterface/
└── README.mdbuyoqam akbarni ishiiiiiiiiiiiiiiiiiiiiiiiiiiii
```

The interface is designed around the practical needs of competition tuning.

---

# 🧠 Skills Developed

Through the Lera project, I developed practical experience in:

### 🤖 Robotics
- Line-following robot development
- Sensor integration
- Motor control
- Robot testing
- Competition preparation

### 🧠 Control Systems
- PID algorithm
- PID parameter tuning
- Error calculation
- Motor correction

### ⚡ Electronics
- ESP32-WROOM
- TB6612FNG
- Custom sensor integration
- Wiring and troubleshooting

### 🌐 Embedded Web Development
- ESP32 Wi-Fi
- IP-based local web interface
- Runtime parameter adjustment
- Live sensor monitoring

### 🧪 Testing
- Sensor calibration
- PID tuning
- Speed testing
- Competition testing
- Rapid troubleshooting

---

# 💡 Why ESP32?

The ESP32-WROOM was an important part of the project because we wanted more than basic microcontroller control.

The robot needed a practical way to adjust PID parameters and motor settings **without repeatedly changing and uploading the firmware**.

The ESP32 allowed us to combine:

```text
Robot Control
      +
PID Algorithm
      +
Wi-Fi
      +
Web Interface
```

This made the robot much easier to configure and tune during development and competitions.

---

# 📊 Project Summary

| Category | Details |
|---|---|
| 🤖 Robot | **Lera Line Following Robot** |
| 🔢 Prototype | **13th Prototype** |
| 🗺️ Regions | **12** |
| 🤖 Competition Robots | **2** |
| 🥇 1st Place | **14×** |
| 🥈 2nd Place | **12×** |
| 👁️ Sensors | **6 Custom Sensors** |
| 🧠 Microcontroller | **ESP32-WROOM** |
| 🔌 Motor Driver | **TB6612FNG** |
| 🧠 Control | **PID** |
| 📡 Communication | **Wi-Fi** |
| 🌐 Interface | **Local Web Interface via IP Address** |
| 🎚️ Runtime Tuning | **Kp, Ki, Kd + Motor Speed** |
| 👀 Sensor Monitoring | **Live Sensor Status** |

---

# 🚀 Final Result

**Lera** is our 13th line-following robot prototype and represents the result of continuous development, testing and competition experience.

By combining a **custom six-sensor array**, **ESP32-WROOM**, **TB6612FNG**, **PID control** and a **Wi-Fi web interface**, we created a platform that could be adjusted and tested quickly without repeatedly uploading new firmware for basic parameter changes.

Across **12 regional competitions**, two robots achieved:

**🥇 14× 1st Place**

**🥈 12× 2nd Place**

This project demonstrates practical experience in **robotics, embedded systems, control algorithms, electronics and web-based robot configuration**.

---

<p align="center">

## 🤖 Lera

**Designed • Built • Tuned • Competed**

### Line Following Robot — Prototype 13

</p>
