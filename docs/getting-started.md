# Getting Started

This guide covers cloning the repo, setting up the software environment on a Raspberry Pi, and running the board reader for the first time.

---

## Prerequisites

- Raspberry Pi 4 (2 GB RAM or more recommended)
- Raspberry Pi OS (Bookworm or later)
- Python 3.11+
- Git
- [uv](https://docs.astral.sh/uv/) (optional; see Development section)

---

## Software Setup

### 1. Clone the repository

```bash
git clone https://github.com/steve-birch/michess.git
cd michess
```

### 2. Repository-wide or per-harness workflow

The repository contains multiple independent harnesses under `development/`. Each harness is a self-contained Python project with its own `pyproject.toml`, virtual environment, and lockfile. You can either use a single global virtual environment and install needed dependencies, or run each harness in-place using `uv` which will create and manage per-harness virtual environments automatically.

To run the main board reader (if available) via a repo-wide virtual environment:

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python software/main.py
```

To run a development harness using `uv` (recommended for prototypes):

```bash
cd development/nfc-matrix-tester
uv run nfc-matrix-tester
```

`uv run` will create the virtual environment and install dependencies automatically on first use.

---

## Hardware Setup

Before running the software you'll need the physical board assembled and wired. See the [Hardware](hardware.md) page for:

- Component list and sourcing
- Wiring diagram / multiplexer topology
- PCB and antenna assembly

---

## Development Setup

If you want to work on the codebase without physical hardware, the board reader supports a simulated mode when running the harness that provides it (see the specific harness README under `development/`). For example, some harnesses accept a `--simulate` flag to emulate hardware.

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
├── development/            # Throwaway hardware/learning test harnesses (each a self-contained project)
├── docs/
└── tests/
```

---

## Next Steps

- Read the [Hardware](hardware.md) page to understand the physical build
- Read the [Software](software.md) page for architecture details and how to contribute code
- For prototype development, see the README inside each harness under `development/` (for example `development/nfc-matrix-tester/README.md`) for run instructions and available simulate flags
