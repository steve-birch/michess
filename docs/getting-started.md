# Getting Started

This guide covers cloning the repo, setting up the software environment on a Raspberry Pi, and running the board reader for the first time.

---

## Prerequisites

- Raspberry Pi 4 (2 GB RAM or more recommended)
- Raspberry Pi OS (Bookworm or later)
- Python 3.11+
- Git

---

## Software Setup

### 1. Clone the repository

```bash
git clone https://github.com/steve-birch/michess.git
cd michess
```

### 2. Create a virtual environment

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the board reader

```bash
python software/main.py
```

---

## Hardware Setup

Before running the software you'll need the physical board assembled and wired. See the [Hardware](hardware.md) page for:

- Component list and sourcing
- Wiring diagram
- PCB and antenna assembly

---

## Development Setup

If you want to work on the codebase without physical hardware, the board reader supports a simulated mode:

```bash
python software/main.py --simulate
```

This lets you develop the chess engine integration and LED controller logic without a connected board.

---

## Repository Layout

```
michess/
├── hardware/               # Schematics, PCB layouts, BOM, antenna designs
├── firmware/               # Low-level microcontroller code (if applicable)
├── software/
│   ├── board_reader/       # NFC matrix scanning
│   ├── chess_engine/       # Stockfish/UCI integration
│   └── led_controller/     # LED matrix control
├── docs/
│   └── architecture/       # System diagrams and design notes
└── tests/
```

---

## Next Steps

- Read the [Hardware](hardware.md) page to understand the physical build
- Read the [Software](software.md) page for architecture details and how to contribute code
