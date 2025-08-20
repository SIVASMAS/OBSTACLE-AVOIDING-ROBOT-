# Arduino Obstacle Avoiding Robot using Ultrasonic Sensor

This project demonstrates how to build a **smart autonomous robot** that detects and avoids obstacles using an **HC-SR04 ultrasonic sensor** and **Arduino Uno/Nano**. Ideal for beginners, this robot uses simple embedded logic to detect nearby objects and change direction accordingly.

## 🚀 Features

- Autonomous obstacle avoidance using ultrasonic sensing  
- Utilizes HC-SR04 with real-time distance measurement  
- Motor control using L298N driver module  
- Lightweight, compact, and beginner-friendly  

---

## 🛠️ Hardware Requirements

| Component              | Specification                    |
|------------------------|-----------------------------------|
| Arduino Uno / Nano     | ATmega328P microcontroller        |
| HC-SR04 Sensor         | 2cm–400cm range, ±3mm accuracy    |
| L298N Motor Driver     | 2A per channel, 5–35V input       |
| 5V DC Motors           | 3–12V operating, 100–300 RPM      |
| Robot Chassis + Wheels | 15cm x 12cm (typical)             |
| Battery Pack           | 7.4V Li-Po or 6xAA                |
| Jumper Wires           | For connections                   |

---

## 🔌 Circuit Diagram

![Circuit Diagram](https://circuitdigest.com/sites/default/files/circuitdiagram_mic/Circuit-Diagram-for-Obstacle%20Avoiding-Robot-using-Arduino-and-Ultrasonic-Sensor.png)

- Trig → D9, Echo → D10  
- Motor control pins: D4–D7  
- Connect HC-SR04 Vcc to 5V, GND to GND  
- L298N IN1–IN4 → D4–D7, ENA/ENB connected accordingly  

---

## ⚙️ Working Principle

- Ultrasonic sensor sends out sound pulses and receives reflections.  
- The duration between sending and receiving is converted to distance.  
- If distance < threshold, the robot turns to avoid obstacle.  
- If distance > threshold, the robot moves forward.  

---

## 💾 Arduino Code Snippet

```cpp
int trigPin = 9;
int echoPin = 10;

int revleft4 = 4;
int fwdleft5 = 5;
int revright6 = 6;
int fwdright7 = 7;

void setup() {
  pinMode(revleft4, OUTPUT);
  pinMode(fwdleft5, OUTPUT);
  pinMode(revright6, OUTPUT);
  pinMode(fwdright7, OUTPUT);
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
}

void loop() {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  long duration = pulseIn(echoPin, HIGH);
  int distance = duration / 58.2;

  if (distance > 19) {
    digitalWrite(fwdright7, HIGH); digitalWrite(revright6, LOW);
    digitalWrite(fwdleft5, HIGH);  digitalWrite(revleft4, LOW);
  } else {
    digitalWrite(fwdright7, LOW);  digitalWrite(revright6, LOW);
    digitalWrite(fwdleft5, LOW);   digitalWrite(revleft4, LOW);
    delay(500);

    digitalWrite(revright6, HIGH); digitalWrite(revleft4, HIGH);
    delay(500);

    digitalWrite(revright6, LOW);  digitalWrite(revleft4, LOW);
    delay(100);

    digitalWrite(fwdright7, HIGH); digitalWrite(fwdleft5, LOW);
  }
}
```

---

## 🧠 Troubleshooting

| Issue                       | Cause / Solution                                    |
|----------------------------|-----------------------------------------------------|
| Robot doesn't move         | Check motor wiring and power connections            |
| Sensor not detecting       | Confirm correct pin configuration and 5V power      |
| Random motion              | Ensure sensor is level and not obstructed           |
| Wrong direction            | Reverse motor pins or adjust control logic          |

---

## 📱 Applications

- Autonomous mobile bots  
- Entry-level robotics curriculum  
- STEM education platforms  
- DIY Arduino robotics kits  
- Base model for smart navigation systems  

---

## 🔮 Future Enhancements

- Servo-mounted sensor for 180° scanning  
- Side ultrasonic sensors for multi-directional detection  
- PWM motor speed control  
- Bluetooth or IR remote override  
- OLED display for distance readouts  

---

## 🧪 Technical Specifications

| Parameter             | Value                             |
|----------------------|------------------------------------|
| Microcontroller       | Arduino Uno / Nano (ATmega328P)   |
| Ultrasonic Sensor     | HC-SR04 (2–400 cm, ±3 mm)         |
| Motor Driver IC       | L298N                             |
| Operating Voltage     | 7.4V LiPo or 6xAA battery pack     |
| Motor Speed Range     | 100–300 RPM                       |
| Detection Time        | < 100 ms                          |
| Temperature Range     | –10°C to +70°C                    |

---


