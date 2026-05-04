---
title: API
---

## Overview
## Camera Actuation Subsystem – Message Handling

The Camera Actuation subsystem receives UART messages in a daisy-chain communication system. It parses incoming packets and determines whether to act on them or forward them downstream.

Each message contains a sender ID, receiver ID, and a message type. The subsystem only responds to messages addressed to its ID (`G`) or to broadcast messages.

- Valid messages → processed
- Unknown messages → forwarded
- Malformed messages → discarded

---

## Message Format

All messages follow the structure below:

| Byte | Description |
|------|------------|
| 0 | `'A'` (Prefix – start wrapper) |
| 1 | `'Z'` (Start Byte) |
| 2 | Sender ID (char) |
| 3 | Receiver ID (char) |
| 4 | Message Type (char) |
| 5 | `'Y'` (End Byte) |
| 6 | `'B'` (Suffix – end wrapper) |

### Example

- Sender: `Z`
- Receiver: `G`
- Type: `U` (Preset 1)

---

## Supported Messages

### Camera Preset Commands

These messages move the camera to predefined positions.

| Message Type | Description |
|-------------|------------|
| `U` | Move to Preset 1 |
| `D` | Move to Preset 2 |
| `C` | Move to Preset 3 |

---

### Roll Call (Broadcast)

| Field | Value |
|------|------|
| Receiver | `X` |

When a message is sent to receiver `X`, the subsystem performs a roll call response (LED sequence).

---

## Behavior

### If Receiver == `G` (This Module)
- Executes camera movement based on `type`

### If Receiver == `X` (Broadcast)
- Executes roll call sequence

### If Receiver != `G`
- Forwards message unchanged

### Error Handling
- Packets from self → discarded
- Malformed packets → discarded
- Buffer overflow → reset

---

## Notes

- Message type is a **single character**, not numeric
- No variable-length payload is used
- Camera positions are **preset-based**, not angle-based


The testing code as a zip folder of the project [*here*](SubsystemMessage.zip).