# Digital Door Lock System using Proteus (No Microcontroller)

A basic logic circuit-based digital door lock system built in Proteus without any microcontroller or firmware.

---

## Features

- Keypad input using logic gates
- Manual reset and code comparison flow
- Magnitude comparator-based code verification
- Password storage using latches
- Mode switching with flip-flops
- Green LED for access granted
- Red LED for access denied
- Motor-driven door unlocking
- No microcontroller or software code required

---

## System Overview

The system is divided into seven functional modules. Each module performs a specific task within the overall lock mechanism.

### 1. Keypad Module
- Components:
  - 9 Push Buttons
  - 9 × 10kΩ Resistors
  - 2-input and 4-input OR Gate ICs
- Purpose: Receives numeric user input and processes it into the logic system.

---

### 2. Storage Module
- Components:
  - 2 × 4043 Quad R/S Latch ICs
  - 4-input OR Gates
- Purpose: Stores both the user-entered and the preset password.

---

### 3. Flip-Flop Module
- Components:
  - 2 × 4013 D Flip-Flop ICs
  - AND & NOT Gates
- Purpose: Controls switching between different operational modes (input vs save).

---

### 4. Shift Register & Comparator Module
- Components:
  - 4 × 74194 4-bit Bidirectional Shift Registers
  - 2 × 7485 Magnitude Comparator ICs
- Purpose: Stores and compares user input with the stored password.

---

### 5. Display Module
- Components:
  - 2 × Common Anode 7-Segment Displays
  - 2 × 7447 BCD to 7-Segment Decoders
- Purpose: Displays the digits entered by the user for visual feedback.

---

### 6. Control System Module
- Components:
  - 1 × 4555 Dual 1-to-4 Decoder/Demultiplexer
  - 1 Reset Button
  - 1 Enter Button
- Purpose: Manages reset and compare actions based on user input.

---

### 7. Output Module
- Components:
  - AND and OR Gates
  - 10kΩ Resistors
  - Red LED, Green LED
  - L293D Motor Driver
  - Motor
- Purpose: Provides physical feedback via LEDs and controls the lock motor.

---

## State Machine

| Current State | User Input | Reset | Enter | Next State | Output                 |
|---------------|------------|-------|--------|-------------|-------------------------|
| Idle          | -          | Yes   | -      | Reset       | Clear Input            |
| Idle          | Digit      | -     | -      | UserInput   | Store Digit            |
| UserInput     | Digit      | -     | -      | UserInput   | Append Digit           |
| UserInput     | -          | Yes   | -      | Reset       | Clear Input            |
| UserInput     | -          | -     | Yes    | Compare     | Compare Codes          |
| Compare       | A = B      | -     | -      | Unlock      | Green LED, Unlock Door |
| Compare       | A ≠ B      | -     | -      | Deny        | Red LED                |
| Unlock/Deny   | -          | Yes   | -      | Reset       | Clear Input            |

---

## How It Works

1. User enters digits via the keypad, which are stored in shift registers.
2. Pressing the Reset button clears all input.
3. Pressing the Enter button initiates comparison between user input and the saved password.
4. A match turns on the green LED and activates the motor to unlock the door.
5. A mismatch lights the red LED to indicate access denied.
6. Reset brings the system back to its idle state.

---

## Scalability

This demo uses 2-digit inputs for simplicity, but it can be easily scaled to 4-digit or longer passwords by adding more shift registers, comparators, and display components.

---

## Project Files

- Proteus `.dsn` design file
- Project report in PDF
- Screenshots and simulation results

---

## Credits

Developed as a Digital Logic Design project at Air University, demonstrating logic-based security systems without firmware or software dependencies.

---

## License

For academic and ethical use only. Contributions are welcome.
