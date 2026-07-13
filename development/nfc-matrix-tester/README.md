# nfc-matrix-tester

A practice harness for wiring a PN532 NFC reader to a Raspberry Pi and reading tag UIDs: the first step toward the full 64-antenna matrix described in [`docs/hardware.md`](../../docs/hardware.md).

## Current stage

Single PN532, single antenna, single tag. A Tkinter window shows the last UID read.

## Where this is going

Once the CD74HC4067 multiplexers are wired up, this grows into an 8×8 grid: `mux.py` will cycle antenna channels between reads, and `display.py` swaps from a single-label window to a grid of 64 cells that light up as tags are detected. Useful for spotting cross-talk, dead antennas, or bad solder joints during assembly without needing the chess engine/LED stack running.

## Structure

- `reader.py`: talks to the PN532 hardware. The only thing that changes when you move from I²C to SPI, or add the multiplexer.
- `models.py`: `TagRead`, the plain data shape passed from reader to display.
- `display.py`: Tkinter UI. The only thing that changes when this grows from "one label" to "8×8 grid".
- `main.py`: wires reader → display together and runs the poll loop.

## Setup (on the Pi)

```bash
cd development/nfc-matrix-tester
uv sync
```

`uv sync` creates `.venv/` and installs everything pinned in `uv.lock`.

## Run

```bash
uv run nfc-matrix-tester
```

## Checks

```bash
uv run pytest   # tests
uv run mypy     # type checking (strict mode; see [tool.mypy] in pyproject.toml)
```

## Wiring

TODO: fill in once the PN532 is wired up (interface used: I²C/SPI/UART; pins, address).
