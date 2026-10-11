# High-Speed Autonomous Guided Vehicle (AGV) Using PID Control

An Arduino Nano–based line-following robot that uses six IR sensors to detect a track and adjusts two DC motors to follow it. This project demonstrates embedded C/C++, sensor interfacing, motor-driver control, PWM, and feedback-based steering.

## 🚀 Project Overview

The robot reads six IR sensor channels, estimates its position relative to the line, calculates a correction, and adjusts the motor outputs to steer back toward the track.

### ✨ Features

- Six-channel IR sensor array for line detection
- Arduino Nano as the main controller
- Two DC motors with differential drive
- PWM-based motor speed control
- Proportional and derivative control parameters
- Serial Monitor output for observing sensor readings
- Push-button operating modes
- LED indicators for status feedback
- 
<img width="1672" height="941" alt="High-Speed AGV Hardware Components Infographic" src="https://github.com/user-attachments/assets/f42808b4-f905-4408-bf1d-59083d2ada17" />


## 💻 Software Requirements

- Arduino IDE 2.x
- Arduino C/C++
- Arduino Serial Monitor

### Motor Driver Connections

| Arduino Nano Pin | Variable | Motor Driver Pin |
|---|---|---|
| D4 | `rmf` | IN1 |
| D7 | `rmb` | IN2 |
| D3 | `lmf` | IN3 |
| D2 | `lmb` | IN4 |
| D6 | `rms` | ENA |
| D5 | `lms` | ENB |

ENA and ENB are used for motor speed control through PWM, provided the motor driver and wiring support it.

### IR Sensor Connections

The supplied sketch reads six analog channels using `analogRead(i)`, where `i` ranges from 0 to 5.

| Sensor | Arduino Nano Analog Pin |
|---|---|
| Sensor 1 | A0 |
| Sensor 2 | A1 |
| Sensor 3 | A2 |
| Sensor 4 | A3 |
| Sensor 5 | A4 |
| Sensor 6 | A5 |

The physical left-to-right sensor order depends on the wiring and mounting of the sensor array.

### Push Buttons and LEDs

| Component | Arduino Nano Pin |
| Button 1 | D8 |
| Button 2 | D9 |
| Button 3 | D10 |
| Button 4 | D11 |
| LED | D12 |
| LED | D13 |

The push buttons are configured using `INPUT_PULLUP`. A pressed button will normally read `LOW`.

## ⚙️ Working Principle

The robot operates through the following sequence:

**IR Sensors → Arduino Nano → Error Calculation → Control Correction → Motor Driver → DC Motors**

1. **Sensor Detection:** The six IR sensors detect the contrast between the line and the surrounding surface.
2. **Sensor Processing:** The Arduino reads the sensor values and compares them with a predefined threshold.
3. **Line Position Estimation:** Sensor positions and readings are used to estimate the line's position relative to the robot.
4. **Error Calculation:** The controller determines how far the robot has deviated from the desired path.
5. **Control Calculation:** The control algorithm calculates the correction required to reduce the error.
6. **Motor Control:** The Arduino adjusts motor speed and direction through the motor driver.
7. **Continuous Feedback:** The process repeats as the robot moves along the track.

## 🧠 PID Control Logic

The supplied code declares the following control variables:

```cpp
int kp = 50, kd = 1000;
float error, last_error;
int PID;
```

The proportional term responds to the current error, while the derivative term responds to changes in the error.

A simplified discrete PD control relationship is:

```text
Correction = Kp × Error + Kd × (Error − Previous Error)
```

The exact calculation, correction polarity, speed limits, and scaling depend on the full implementation in the Arduino sketch.

**Note:** The visible code declares `kp` and `kd`. Confirm the complete source before claiming that an integral term is implemented.

## 📥 Installation and Setup

1. Install the Arduino IDE.
2. Clone or download this repository.
3. Open `PID_LINE_FOLLOWER_CODE.ino` in Arduino IDE.
4. Connect the Arduino Nano to your computer using USB.
5. Select **Tools → Board → Arduino Nano**.
6. Select the correct port under **Tools → Port**.
7. Verify the sketch and upload it to the Arduino Nano.
8. Open **Tools → Serial Monitor**.
9. Set the baud rate to **9600**.
10. Place the robot on a suitable high-contrast line track and operate it using the configured buttons.

## 🔍 Calibration and Troubleshooting

| Problem | Possible Solution |
| Sensors do not detect the line | Check sensor height, wiring, orientation, and threshold |
| Robot turns in the wrong direction | Check sensor order, motor wiring, and error polarity |
| Robot oscillates around the line | Reduce speed and tune the control gains gradually |
| One motor does not run | Check motor connections, driver supply, and enable pins |
| Serial output is unreadable | Ensure the Serial Monitor is set to 9600 baud |
| Arduino resets when motors start | Check battery condition, current capacity, and power connections |

Tune the controller on the actual track. Different surfaces, motor loads, and battery conditions may require different control gains.

## 🧪 Testing and Validation

The following tests can be used to evaluate the robot:

- Verify that all six sensor channels respond to the line.
- Check forward, reverse, and turning motor commands where supported.
- Test straight paths, gentle curves, and sharp turns.
- Observe sensor readings through the Serial Monitor.
- Tune the control gains and compare tracking performance.
- Record measured speed and tracking accuracy under repeatable conditions.

Add actual test measurements and demonstration videos after validating the completed build.

## 🔮 Future Improvements

- Improve sensor calibration under different lighting conditions.
- Develop a repeatable control-gain tuning procedure.
- Add battery-voltage monitoring.
- Log sensor data for performance analysis.
- Measure lap time and line-tracking reliability.
- Optimize speed while maintaining stable line tracking.

## 📸 Project Demonstration
<img width="1365" height="768" alt="circuited diagram" src="https://github.com/user-attachments/assets/8bfcff74-4ea0-424a-8b82-41479c3c804b" />
<img width="1672" height="941" alt="Arduino Line-Follower Robot Workbench" src="https://github.com/user-attachments/assets/5f1a9baf-48a7-4d74-b599-efee70d35cad" />
<img width="1673" height="898" alt="1" src="https://github.com/user-attachments/assets/5113bd72-9b28-4861-b8ac-664331db8950" />




## 👨‍💻 Author

**Ajit Pal**

Electronics and Communication Engineering
