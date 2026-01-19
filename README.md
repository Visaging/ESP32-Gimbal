# Gimbal
A high-performance, open-source 3-axis smartphone gimbal built from scratch using a custom PCB and the SimpleFOC library. It features real-time stabilization, native USB-C programming, and custom motion modes.

## Hardware Stack
- **MCU:** ESP32-S3-WROOM-1-N8R2
- **Sensors:** BMI270 6-Axis IMU (I2C)
- **Drivers:** 3x DRV8313 Three-Phase Drivers
- **Motors:** 2805 140KV Gimbal BLDC Motors
- **Power:** Custom 3S Li-Ion BMS with CN3303 Charging & TPS563200 Regulation

## Key Features
- **Active Stabilization:** High-frequency FOC loop with smart Yaw/Pan drift cancellation.
- **Native USB-C:** Supports both battery charging (12.6V boost) and firmware upload via the same port.
- **3 Operation Modes:**
   * Stabilize: Standard horizon leveling and pan following.
   * Teaching Mode: Motors disengage for 5 seconds, allowing the user to manually pose the camera before auto-locking the new angle.
   * Selfie/Statue Mode: A dedicated 6 second setup window to lock the gimbal in arbitrary static positions.
<hr></hr>
<details open>
  <summary><h2>External wiring diagrams</h2></summary>
  
  ### Battery:
  ```mermaid
  ---
  config:
    look: handDrawn
  ---
  flowchart LR
      A(Cell 1)-->|+ve|B(Cell 2)-->|+ve|C(Cell 3)---|+ve|D
      A(Cell 1)-->|+ve|F(B1)---D
      A(Cell 1)-->|-ve|E(B-)---D(BMS)
      B(Cell 2)-->|+ve|G(B2)---D
      D-->J10
  ```
  ### Handle wiring:
  ```mermaid
  ---
  config:
    look: handDrawn
  ---
  flowchart TD
      A@{ shape: dbl-circ, label: "Rocker Switch" }-->J14
      B@{ shape: dbl-circ, label: "Momentary
  Button 1" }-->J7
      D@{ shape: dbl-circ, label: "Momentary
  Button 2" }-->J4
      E@{ shape: dbl-circ, label: "Momentary
  Button 3" }-->J2
      LED@{ shape: dbl-circ, label: "LED" }-->J3
  ```
  ### BMI270 Breakout Board:
  ```mermaid
  ---
  config:
    look: handDrawn
  ---
  flowchart TD
      C(BMI BREAKOUT BOARD)-->|GND|J8---D(ESP32)
      C(BMI BREAKOUT BOARD)-->|3V3|J9---D
      C(BMI BREAKOUT BOARD)-->|SDA|J6---D
      C(BMI BREAKOUT BOARD)-->|SCL|J5---D
  ```
  ### Motors:
  ```mermaid
  ---
  config:
    look: handDrawn
  ---
  flowchart TD
      J11-->|OUT1|D(Motor 1)
      J11-->|OUT2|D(Motor 1)
      J11-->|OUT3|D(Motor 1)
  
      J12-->|OUT1|E(Motor 2)
      J12-->|OUT2|E(Motor 2)
      J12-->|OUT3|E(Motor 2)
  
      J13-->|OUT1|F(Motor 3)
      J13-->|OUT2|F(Motor 3)
      J13-->|OUT3|F(Motor 3)
  ```
</details>
<hr></hr>
<details>
  <summary><h2>PCB Schematics</h2></summary>
<img width="3507" height="2480" alt="image" src="https://github.com/user-attachments/assets/a1597c18-d900-4c81-82a0-5f736e6f7ad0" />
<img width="2480" height="1748" alt="image" src="https://github.com/user-attachments/assets/38abb279-5b1a-4a33-9dc9-f7baf6ae8d7d" />
</details>
<hr></hr>
<details>
  <summary><h2>PCB Layout and Render</h2></summary>
<img width="346" height="765" alt="image" src="https://github.com/user-attachments/assets/ac17bc1b-6d54-443e-aa5e-357d01954536" />
<img width="1723" height="892" alt="image" src="https://github.com/user-attachments/assets/a846b01d-ea0d-4b22-bc0f-d6402903df3b" />
</details>
<hr></hr>
<details>
  <summary><h2>3D Printed Body</h2></summary>

  
</details>
<hr></hr>
