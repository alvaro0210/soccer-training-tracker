# Soccer Training Tracker

Waist-worn ESP32 + IMU tracker for soccer training: sprint detection, step count and jump height, with Python data analysis.

## Goal (version 1)

- Record motion data from a 6-axis IMU worn at the waist during training
- Log the data to a microSD card
- Analyze it in Python (Pandas, NumPy, Matplotlib) to detect sprints, count steps and estimate jump height

## Hardware

| Part | Adafruit # | Purpose |
|---|---|---|
| ESP32 Feather V2 | 5900 | Main board |
| LSM6DSOX 6-DoF IMU | 4438 | Accelerometer + gyroscope |
| STEMMA QT cable | 4210 | Connects the IMU over I2C (no soldering) |
| MicroSD breakout+ | 254 | SD card logging (SPI) |
| LiPo battery 3.7V 400 mAh | 3898 | Portable power |
| Perma-Proto half-size | 1609 | Permanent build |
| Slide switch | 805 | On/off |

## SD card wiring (breadboard test)

| Feather pin | microSD breakout pin | Function |
|---|---|---|
| 3V | 3V | Power |
| GND | GND | Ground |
| SCK | CLK | SPI clock |
| MO | DI | Data from Feather to card |
| MI | DO | Data from card to Feather |
| 33 | CS | Chip select |

## Repository structure

- `firmware/` – Arduino sketches for the ESP32
- `analysis/` – Python analysis (coming soon)
- `data/` – recorded sessions (coming soon)

## Build log

- **2026-11-06** – Ordered parts. Set up Arduino IDE with ESP32 support and the LSM6DS library. Created this repository.
- **2026-11-11** – Test 1: first program (Blink) running on the Feather. Fixed a failed upload by lowering the upload speed to 115200.
- **2026-11-11** – Test 2: read live accelerometer, gyroscope and temperature data from the IMU. Debugged a loose STEMMA QT connector with an I2C scanner (IMU found at 0x6A).
- **2026-11-21** – Remaining parts arrived. Checked the microSD card (FAT32). Prepared the SD card test sketch (CS on pin 33) and the wiring plan.
- **Next** – Solder headers on the microSD breakout, then test SD logging on the breadboard.