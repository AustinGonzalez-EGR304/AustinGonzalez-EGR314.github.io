---
title: API
---

## Overview
## Camera Actuation Subsystem – Message Handling

The Camera Actuation subsystem is responsible for interpreting and responding to specific command messages within the daisy chain communication system. It processes incoming data to control the movement and positioning of the camera and its supporting arm. When relevant messages are received, the subsystem extracts the required parameters and adjusts the camera accordingly to achieve the desired orientation.

This subsystem specifically handles messages related to setting the camera’s position and making fine adjustments to its angle. Messages that do not pertain to camera movement are passed through unchanged to the next module in the chain, ensuring seamless communication across subsystems. Any invalid or unrecognized messages are discarded to maintain system reliability and prevent unintended behavior.


---

## Messages

### Set Camera Angle

This message commands the camera to move to a specific predefined angle.

| Byte(s) | Variable Name | Variable Type | Min Value | Max Value | Example |
|--------|--------------|--------------|----------|----------|--------|
| 1–2 | message_type | uint8_t | 3 | 3 | 3 |

### Adjust Angle

This message allows fine adjustment of the camera position using X and Y coordinates.

| Byte(s) | Variable Name | Variable Type | Min Value | Max Value | Example |
|--------|--------------|--------------|----------|----------|--------|
| 1–2 | message_type | uint8_t | 8 | 8 | 8 |
| 3 | x_value | uint16_t | 0 | 360 | 350 |
| 4 | y_value | uint16_t | 0 | 360 | 25 |


