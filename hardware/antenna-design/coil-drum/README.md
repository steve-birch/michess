# Coil drum

This folder contains a single printed 57 mm chess-square tile for a prototype read coil. The coil sits in a 31.5 mm drum wound between the base plate and a thin top flange that the LED ring passes over. Four locating pegs hold the LED ring in place, with a tail notch for the coil lead and a pocket for the perfboard anchor board.

## Key dimensions

These values come from the FreeCAD spreadsheet in `coil-drum.FCStd`. Some values are still typed in instead of being linked to the spreadsheet; that tidy-up is still pending, including the unused aliases.

| Parameter | Value | Source | Notes |
|---|---:|---|---|
| Chess-square tile size | 57 mm | Spreadsheet value `square_size` | Printed square tile size |
| Base plate thickness | 3.6 mm | Typed in | Draft 2 geometry |
| Drum overall height | 6.0 mm | Typed in | Winding gap is 2.4 mm |
| Top flange thickness | 0.6 mm | Typed in | Draft 2 geometry |
| LED ring hole ID | 35 mm | Measured | Measured 2 Oct 2026 |
| LED ring OD | 50 mm | Measured | Measured 2 Oct 2026 |
| LED peg spacing | 32.5 mm | Spreadsheet value `LED_loc_peg_dist` | Locates the LED ring |
| LED hole diameter | 2.2 mm | Spreadsheet value `LED_loc_hole_dia` | Hole size |
| LED peg diameter | 1.2 mm | Typed in | Derived from `2.2 mm - 1.0 mm` clearance |
| LED peg height | 5 mm | Typed in | Draft 2 geometry |
| Anchor-board pocket height | 1.6 mm | Typed in | Draft 2 geometry |
| Anchor-board pocket floor | 0.6 mm | Typed in | Draft 2 geometry |

## Files

- `coil-drum.FCStd` — FreeCAD 1.1 development build; it may not open in FreeCAD 1.0. The model is driven by a Spreadsheet of named values.
- `coil-drum-Body.stl` — committed STL export for review and reproducibility. If the FCStd changes, re-export the STL in the same commit.

## Printing

- Printer: Bambu Lab A1
- Orientation: flat on its base
- Supports: none
- Layer height / material: TBD

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
