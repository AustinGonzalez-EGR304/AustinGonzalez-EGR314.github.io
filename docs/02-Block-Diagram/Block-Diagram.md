---
title: Module's Block Diagram
tags:
- tag1
- tag2
---

## Overview
The purpose of this block diagram is to illustrate the design of the Team 201 Camera Actuation subsystem and how it integrates with the broader scope of the project. This system features two stepper motors that control camera motion, allowing for nearly 180 degrees of viewing range.

Both 12 V and 3.3 V power supplies are used to power the stepper motors, motor drivers, and the ESP32 microcontroller. The subsystem receives commands from the Control subsystem via the ESP32’s UART communication interface and sends digital output signals to the motor drivers to accurately control camera movement.

Debugging features included in the design are on-board debug buttons, status indicator LEDs, and configurable jumpers.
## Requirments
The block diagram was created to fulfill the role of moving the camera and other mounted accessories on the camera arm. This is accomplished through an ESP32-S3 microcontroller sending commands to two stepper motor drivers—one for the horizontal axis and one for the vertical axis. I chose two drivers from Texas Instruments due to their widespread use in stepper control applications for ESP32 projects.

Although the selected stepper motor drivers include a built-in homing feature, I chose to incorporate a Hall-effect sensor used in conjunction with a magnet to detect when the arm is in a defined position, preventing over-rotation.

Since there are multiple power sources in the project, the buck converter I selected can accept multiple input sources, providing power redundancy to ensure the system remains operational.
## Block Diagram 

![Indivial Block diagram ](314AustinBlockDiagram.drawio (1).png)
