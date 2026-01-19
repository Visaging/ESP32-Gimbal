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
<details>
  <summary><h2>External wiring diagrams</h2></summary>
  
### Battery:
![](https://mermaid.ink/img/pako:eNp1UU1PgzAY_ivNe2IZXUpZB_RgIsOPGL3ozXBp1g7IoF0qOHXbf7eAW5aot_f5Prx7WBmpgAPGONcIrYxeVwXvT4RqYzYclULLzIqdzvVgWtdmtyqFbdHj8-i79paqrlEwwfjqMH1Xh3Qk6JlYjkQ4-Sdw66U9wNkfOnb6jZfiQffSp5efkl8jd15KL0rOmyf93kunF3rm-IeAgA-FrSTwtajflA-Nso3oMex7Xw5tqRqVA3enFHaTQ66PLrQV-tWYBnhrOxezpivKE-i2UrQqq0RhRXNutkpLZZem0y1wFgwVwPfwATyIwtmCkGQxp4tgHjLCfPh0NItnYZwklM3jiAYhYUcfvoZVMmNxGNGIEOoCMUsSH5SsWmOfxocOfz1-AyY-iIE?type=png)
<!--
https://mermaid.live/edit#pako:eNp1UU1PgzAY_ivNe2IZXUpZB_RgIsOPGL3ozXBp1g7IoF0qOHXbf7eAW5aot_f5Prx7WBmpgAPGONcIrYxeVwXvT4RqYzYclULLzIqdzvVgWtdmtyqFbdHj8-i79paqrlEwwfjqMH1Xh3Qk6JlYjkQ4-Sdw66U9wNkfOnb6jZfiQffSp5efkl8jd15KL0rOmyf93kunF3rm-IeAgA-FrSTwtajflA-Nso3oMex7Xw5tqRqVA3enFHaTQ66PLrQV-tWYBnhrOxezpivKE-i2UrQqq0RhRXNutkpLZZem0y1wFgwVwPfwATyIwtmCkGQxp4tgHjLCfPh0NItnYZwklM3jiAYhYUcfvoZVMmNxGNGIEOoCMUsSH5SsWmOfxocOfz1-AyY-iIE
-->
  
### Handle wiring:
![](https://mermaid.ink/img/pako:eNqVkj1vgzAQhv_K6WaI-HIAD1WbkqVqlrZT5cXBDqCAHTlGaYr474Wkzhgpm8_3Ps_dcAOWWkik6Ps-UwClVrumovMToNV6T6HmShSGnxRT_6Fdq09lzY2Fr-KaBHh5HuBY84OkILatXzam9KDlW9lSYPihy7008HlqbFkzhNH3n97CxMGru_BGd1JZbs5zfNVbqxWETpI6R_GwI3KO2x7rhx2xc0TO8b6-v8nUd0yMHlamEUh3vD1KDztpOj7XOMw6hraWnWQ4c4KbPUOmxgk6cPWtdYfUmn7CjO6r2hX9QXAri4ZXhnc3s5FKSPOqe2WREnJRIB3wB2mYxotlEOTLJFqGSUyCqXuevkm2iLM8j0iSpVEYB2T08PcyNViQLE6jNAiiCchInnsoRWO12VyP6XJT4x85e7cJ?type=png)
<!--
https://mermaid.live/edit#pako:eNqVkj1vgzAQhv_K6WaI-HIAD1WbkqVqlrZT5cXBDqCAHTlGaYr474Wkzhgpm8_3Ps_dcAOWWkik6Ps-UwClVrumovMToNV6T6HmShSGnxRT_6Fdq09lzY2Fr-KaBHh5HuBY84OkILatXzam9KDlW9lSYPihy7008HlqbFkzhNH3n97CxMGru_BGd1JZbs5zfNVbqxWETpI6R_GwI3KO2x7rhx2xc0TO8b6-v8nUd0yMHlamEUh3vD1KDztpOj7XOMw6hraWnWQ4c4KbPUOmxgk6cPWtdYfUmn7CjO6r2hX9QXAri4ZXhnc3s5FKSPOqe2WREnJRIB3wB2mYxotlEOTLJFqGSUyCqXuevkm2iLM8j0iSpVEYB2T08PcyNViQLE6jNAiiCchInnsoRWO12VyP6XJT4x85e7cJ
-->
  
### BMI270 Breakout Board:
![](https://mermaid.ink/img/pako:eNqNkctuwjAQRX_FmhVICTIxzsOLSoBR1fRBBbSLKhsLmySC2MhNRFvCv9cJatfs5lrnXGs0Z9gaqYCB7_uZRmhr9K7MWTcidDBmz1AhtORWnHSme2h3MKdtIWyNNvzKITQfzJ4fggij2WoxfVy-bdBsOV3xoe_ftfcvvE1jp_LBYv1KguEtEnknbZp00i30mk_bNLyZnj-1Ke1o8CC3pQS2E4dP5UGlbCW6DOeuKIO6UJXKgLlRCrvPINMXJx2F_jCmAlbbxmnWNHnxF5qjFLXipcitqP6brdJS2blpdA1sjKO-A9gZvlyMyCjEOAknQTieEIqpB9_umcYjEidJQCdxFIwJphcPfvpv8YjGJHLr4cAJMU0SD5Qsa2Ofr9fsj3r5BQMWhVA?type=png)
<!--
https://mermaid.live/edit#pako:eNqNkctuwjAQRX_FmhVICTIxzsOLSoBR1fRBBbSLKhsLmySC2MhNRFvCv9cJatfs5lrnXGs0Z9gaqYCB7_uZRmhr9K7MWTcidDBmz1AhtORWnHSme2h3MKdtIWyNNvzKITQfzJ4fggij2WoxfVy-bdBsOV3xoe_ftfcvvE1jp_LBYv1KguEtEnknbZp00i30mk_bNLyZnj-1Ke1o8CC3pQS2E4dP5UGlbCW6DOeuKIO6UJXKgLlRCrvPINMXJx2F_jCmAlbbxmnWNHnxF5qjFLXipcitqP6brdJS2blpdA1sjKO-A9gZvlyMyCjEOAknQTieEIqpB9_umcYjEidJQCdxFIwJphcPfvpv8YjGJHLr4cAJMU0SD5Qsa2Ofr9fsj3r5BQMWhVA
-->

### Motors:
![](https://mermaid.ink/img/pako:eNp9kstqwzAQRX9FzKoGO1iSH7EW3dTtohC6STfFGxHJDxJLQZVJW8f_XsVJkxKDF4I7c-7cQTA9bLSQwCAIgkIhtNGqbCp2kgjttN4yVHMlcsMPqlCjqdzpw6bmxqJ1fvYh9IpxEDwe397X-Jg_rLTVBmFvSskspXf05iDX9OeLg3hTSmYpvaM3B72mv1wc1JtSMkvpPwo-VKYRwEq--5Q-tNK0_FRDPy4GW8tWFsCcFNxsCyjU4Ib2XH1o3QKzpnNjRndV_Vd0e8GtzBteGd5ek41UQpon3SkLDNN4zADWw5crE7LIsoyE0TKOQ0LSpQ_frh0lC_dwlCURzghOBx9-xq3hIqYhjtIwjROn0oT4IEXj_rQ638h4KsMv4dSfuQ?type=png)
<!--
https://mermaid.live/edit#pako:eNp9kstqwzAQRX9FzKoGO1iSH7EW3dTtohC6STfFGxHJDxJLQZVJW8f_XsVJkxKDF4I7c-7cQTA9bLSQwCAIgkIhtNGqbCp2kgjttN4yVHMlcsMPqlCjqdzpw6bmxqJ1fvYh9IpxEDwe397X-Jg_rLTVBmFvSskspXf05iDX9OeLg3hTSmYpvaM3B72mv1wc1JtSMkvpPwo-VKYRwEq--5Q-tNK0_FRDPy4GW8tWFsCcFNxsCyjU4Ib2XH1o3QKzpnNjRndV_Vd0e8GtzBteGd5ek41UQpon3SkLDNN4zADWw5crE7LIsoyE0TKOQ0LSpQ_frh0lC_dwlCURzghOBx9-xq3hIqYhjtIwjROn0oT4IEXj_rQ638h4KsMv4dSfuQ
-->

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
Handle:
<img width="500" height="500" src="https://github.com/user-attachments/assets/8a1dd7b0-ec15-4932-90e8-a8ea72237f35" />

Handle Enclosure:


  
</details>
<hr></hr>
