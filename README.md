# WRO25-FUTURE-ENGINEERS

# Team Logo
![WhatsApp Image 2025-10-19 at 17 24 52_59760c78](https://github.com/user-attachments/assets/85020a02-1447-4304-8e9d-ff8b65924a06)


---
# Overview
*write an overview of the robot*

---
# Team Members
*insert picture*

---
# Hardware

## 3 Ultrasonic Sensors (HC-SR04)
Overview: Low‑cost, 5 V ultrasonic rangefinders (approx. 2 cm–4 m). Good for simple obstacle detection when used in a front‑left / front‑center / front‑right array.

<img width="292" height="173" alt="image" src="https://github.com/user-attachments/assets/505da7b6-f95d-45e4-9498-076d326b85ef" />

### Advantages:

- Inexpensive, widely available, easy to wire (Trig/Echo) and debug with an LED/oscilloscope.

- Robust to lighting conditions; works in dark/sunlight where vision may struggle.

- Narrow beam (~15°) helps with directional obstacle cues when angled.

**How we use it:**
It gives us a rough estimation of the close-proximity area surrounding the robot so that doesnt bump into walls or obstacles accidentally

## MPU6500 Gyro + Accelerometer Sensor
Overview: InvenSense 6‑DOF IMU for heading estimation, stabilization, and odometry aiding. Combines a 3‑axis gyroscope (±250–2000 °/s) and 3‑axis accelerometer (±2–16 g) with configurable digital low‑pass filters and up to ~1 kHz sampling via I²C or SPI.

<img width="225" height="225" alt="image" src="https://github.com/user-attachments/assets/ce65d78a-7271-49cc-9851-a843849031a7" />

### Advantages

- Low‑noise gyro (for its class) with DLPF → smoother heading estimates.

- SPI support enables high‑rate reads with low latency; broad library support.

- Compact and low‑power; easy to place near the chassis center of rotation.

**How we use it:**
Used to precisely detect the position of the gyrosocpe on the field to enable smooth PID control and increased object avoidance.

## 3-6V DC motor with yellow gearbox (TT Motor)

Overview: Common plastic 1‑stage/2‑stage geared DC motor used for lightweight drivetrains.

Advantages

- Very cheap and available with many gear ratios and wheel hubs.

- Simple to drive via H‑bridge; adequate torque for small chassis.

- Good for rapid prototyping and spares during competition.

**How we use it:**
Used for movement of the rear wheels.

## L298N Dual H-Bridge Motor Driver
Overview: Legacy bipolar H‑bridge (up to ~2 A/channel) for two brushed DC motors.

Advantages

- Dirt cheap; lots of tutorials and schematics.

- On‑board 5 V regulator on many modules simplifies wiring.

- Works from a wide input range, handy in a pinch.

**How we use it:**
Used to control the DC motors.

## DS3240 Servo Motor
Overview: Metal‑gear, high‑torque PWM hobby servo (often rated ≈ 40 kg·cm @ 7.4 V). Useful for steering mechanisms or active sensor mounts.

Advantages

- Excellent stall torque for size; metal gears and aluminum case (on many variants).

- Standard 3‑wire PWM control; drops into typical RC/robot stacks.

- Operates at 6–8.4 V; good match to a dedicated 7.4 V rail.

**How we use it:**
Used to steer the two front wheels.

## PCA9685 Servo Motor Driver
Overview: I²C 12‑bit PWM expander that generates up to 16 hardware PWM channels for servos/LEDs, freeing CPU timers.

Advantages

- Stable, jitter‑free PWM independent of host CPU load.

- Chainable via I²C addresses; simple libraries on Raspberry Pi.

- 3.3 V I²C‑friendly yet can drive 5–7.4 V servo rails (separate V+).

**How we use it:**
Controls the servo motor's output.

## 7.4V Lithium-ion batteries (x2)
Overview: Two independent 2‑cell packs.

Advantages

- Electrical isolation reduces brown‑outs and noise coupling into the Raspberry Pi.

- Native 7.4 V matches high‑torque servos (e.g., DS3240) without heavy conversion losses.

- Modular swaps: replace a depleted pack without shutting down the entire robot.

- Fault containment: an issue on one rail is less likely to take down everything.

**How we use it:**
Power for the whole robot.

## XL4015 Step-down Converter
Overview: Adjustable buck module (typically up to 5 A) to derive stable 12 V/9 V/5 V rails from the traction battery.

Advantages

- High current capacity for price; efficiency far better than linear regulators.

- Screw‑terminal/trim‑pot modules are quick to integrate; common footprints.

- Often includes CC (constant‑current) mode useful for LED loads or battery precharge.

**How we use it:**
It lowers voltage coming from the batteries from 7.4V to 5V.

## Raspberry Pi Camera Module 3

Overview: Autofocus 12 MP camera (Sony IMX708 family) with wide/standard FOV options and HDR variants. Primary sensor for vision and lane detection.

Advantages

- Autofocus improves clarity for varying distances and vibration.

- Great color detection and masking, useful for obstacles.

- High resolution enables cropping/ROI; good low‑light vs older modules.

- Mature drivers and community support; works seamlessly with Raspberry Pi 5.

**How we use it:**
We are using AI vision on the camera to avoid obstacles with it's color detection capability and to calculate how far an object is by counting the amount of pixels it's color occupies on the camera's FOV.

## Raspberry Pi 5

Overview: Quad‑core Cortex‑A76 SBC with significant CPU/GPU uplift, dual 4K HDMI, PCIe, and improved I/O—well‑suited for real‑time perception/planning.

 Advantages

- Big performance headroom for OpenCV, TensorRT‑style inference, and Python control.

- Fast I/O (PCIe, higher USB throughput) for cameras, IMUs, and storage.

- Strong ecosystem: libraries, guides, and accessories.

**How we use it:**
The raspberry pi is the brain of the system, it recieves input from sensors to then act upon it by outputing signals to the actuators. It's great since it has a very high response time as well as being compatible with the camera's AI vision and the rest of the sensors and actuators.
