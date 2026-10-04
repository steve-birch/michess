# Coil drum

This folder contains a single printed 57 mm chess-square tile for a prototype read coil. The coil sits in a 31.5 mm drum wound between the base plate and a thin top flange that the LED ring passes over. Four locating pegs hold the LED ring in place, with a tail notch for the coil lead and a pocket for the perfboard anchor board.

## Key dimensions

These values come from the FreeCAD spreadsheet in `coil-drum.FCStd` rather than being guessed. Some values are still typed in instead of being linked to the spreadsheet; that tidy-up is still pending.

| Parameter | Value | Notes |
|---|---:|---|
| Chess-square tile size | 57 mm | Printed square tile size |
| Drum core diameter | 31.5 mm | Spreadsheet value `core_d` |
| Drum height | 3 mm | Spreadsheet value `drum_h` |
| Top-flange thickness | 1 mm | Spreadsheet value `flange_t` |
| LED ring hole ID | 35 mm | Spreadsheet value `LED_ring_hole` |
| LED ring OD | ~50 mm | Rough design target from the ring specification; not a measured part value |
| LED peg spacing | 32.5 mm | Spreadsheet value `LED_loc_peg_dist` |
| LED hole diameter | 2.2 mm | Spreadsheet value `LED_loc_hole_dia` |
| LED peg diameter | 1.0 mm | Derived from `LED_loc_hole_dia - clearance`, with `clearance = 1 mm` |
| LED peg height | 3 mm | Spreadsheet value `LED_loc_peg_h` |

## Files

- `coil-drum.FCStd` — FreeCAD 1.1 development build; it may not open in FreeCAD 1.0. The model is driven by a Spreadsheet of named values.
- `coil-drum-Body.stl` — committed STL export for review and reproducibility. If the FCStd changes, re-export the STL in the same commit.

## Printing

- Printer: Bambu Lab A1
- Orientation: flat on its base
- Supports: none
- Ask me for the layer height and material rather than guessing.

## History

### Draft 1

- Walled winding channel
- Too hard to wind

### Draft 2

- Top flange added
- No wall, flat bottom
- First coil: 3 turns of 30 AWG, wired directly to the ST25R3916B MINI
- Reads an NTAG213 tag
- Rough check only (not measured): read distance looked at least as good as the stock antenna's ~31 mm
- Placing the LED ring (unpowered) over it seemed to reduce the distance
- Known problem: the anchor-board pocket printed mangled, possibly because of the unsupported roof bridge, and the board does not fit; this is to be fixed in draft 3

## Notes

- The design currently mixes spreadsheet-driven values and a few hard-coded values; a tidy-up is still pending.
- The board anchor pocket and the tail notch are in the model, but the exact pocket dimensions are not yet all spreadsheet-driven and are not being guessed here.
