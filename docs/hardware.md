# Hardware

michess is built around a Raspberry Pi 4 reading a 64-antenna NFC matrix. This page covers the component list, the multiplexer topology, and the LED system.

---

## Bill of Materials

| Component | Quantity | Notes |
|---|---|---|
| Raspberry Pi 4 | 1 | Main controller; 2 GB RAM minimum |
| PN532 NFC reader modules | 8 | One per 8-square group |
| CD74HC4067 16-channel multiplexers | 4 | For antenna switching |
| NFC tags (13.56 MHz, NTAG213) | 32 | Embedded in piece bases |
| Custom loop antennas | 64 | One per square, ~1–2 μH |
| WS2812B LEDs | 64+ | For move indication |

See `hardware/bom/` for a full bill of materials with UK suppliers and current pricing.

---

## NFC Matrix Architecture

### Why a matrix of antennas?

Standard NFC readers have a single antenna with a read range of ~4 cm. To cover all 64 squares without moving parts, michess uses 64 small loop antennas - one per square - switched via multiplexers so that a single PN532 module scans 8 squares in sequence.

### Multiplexer topology

```
Raspberry Pi (I²C / SPI)
    │
    ├─ PN532 #1 ── MUX ── antennas a1–a8
    ├─ PN532 #2 ── MUX ── antennas b1–b8
    ├─ PN532 #3 ── MUX ── antennas c1–c8
    ├─ PN532 #4 ── MUX ── antennas d1–d8
    ├─ PN532 #5 ── MUX ── antennas e1–e8
    ├─ PN532 #6 ── MUX ── antennas f1–f8
    ├─ PN532 #7 ── MUX ── antennas g1–g8
    └─ PN532 #8 ── MUX ── antennas h1–h8
```

Each CD74HC4067 16-channel multiplexer connects one PN532 to 8 antenna coils in sequence (only 8 of the 16 channels are used per MUX). The Pi cycles through all 8 reader modules, reading 8 squares each, giving a full 64-square scan in under 2 seconds.

### Antenna design

The loop antennas are custom-designed PCB coils tuned to 13.56 MHz. Each coil sits directly beneath a board square, routed through the multiplexer to its assigned PN532. See `hardware/antenna-design/` for coil dimensions and tuning notes.

---

## LED System

WS2812B addressable LEDs are placed beneath each square. The Raspberry Pi drives the LED strip directly over a single GPIO pin using the `rpi_ws281x` library. The LEDs indicate:

- **Engine move** - highlight the from-square and to-square
- **Check** - flash the king's square
- **Illegal move** - brief red flash on the lifted piece's origin square

---

## PCB Design

The project uses KiCad for PCB design. Source files are in `hardware/pcb/`. Gerber files are not committed - regenerate them from source when needed.

---

## Enclosure

The enclosure is designed in FreeCAD (source in `hardware/enclosure/`). The top surface is a wood veneer panel with LEDs diffused through it. STL files are not committed - export from the FreeCAD source.

---

## Licences

All hardware designs are released under [CERN-OHL-S v2](https://ohwr.org/cern_ohl_s_v2.txt). You are free to manufacture, modify, and sell boards based on this design, but must share modifications under the same licence.
