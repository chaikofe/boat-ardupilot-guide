# Wiring Diagrams

How everything connects.

## Power side (high current)

Battery (+) - fuse (40A) - bus -+- ESC #1 fat red
                                +- ESC #2 fat red

Battery (-) - bus --------------+- ESC #1 fat black
                                +- ESC #2 fat black

Battery (+ and -) - also -> 5V BEC input

Battery (+ and −) ─ also → 5V BEC input

Use XT60 or XT90 connectors for the main battery. Ring terminals at the bus bar.

## Motor wires

- ESC #1 three phase wires → T500 #1 three phase wires
- ESC #2 three phase wires → T500 #2 three phase wires
- Order doesn't matter — if a thruster spins backward, swap any two

## ESC signal to Cube

| From | To |
|---|---|
| ESC #1 white (signal) | MAIN OUT 1 — signal pin (top) |
| ESC #1 black (ground) | MAIN OUT 1 — ground pin (bottom) |
| ESC #2 white (signal) | MAIN OUT 3 — signal pin (top) |
| ESC #2 black (ground) | MAIN OUT 3 — ground pin (bottom) |

ESC red wires (5V) are **not connected** on the Basic ESC.

## 5V BEC to servo rail

- BEC 5V output → MAIN OUT rail (+ middle pin of any channel)
- BEC ground → MAIN OUT rail (− bottom pin)
- BEC input → main battery

Without this, the ESCs won't see the Cube's signals.

## Telemetry (RFD900x)

| Cube TELEM1 | RFD900x |
|---|---|
| Pin 1 (VCC) | +5V |
| Pin 2 (TX) | RX (crossover) |
| Pin 3 (RX) | TX (crossover) |
| Pin 6 (GND) | GND |

The TX↔RX crossover is critical.

## RC receiver (R9 SX)

| R9 SX | Cube RC IN |
|---|---|
| SBUS_OUT (on 6-pin connector) | Signal pin |
| +5V (V_IN) | +5V pin |
| GND | GND pin |

## GPS (Here2/Here4 on CAN)

- 4-pin CAN cable → CAN1 port on Cube
- Confirm Here2/Here4 mode switch is on **CAN** (not UART)
