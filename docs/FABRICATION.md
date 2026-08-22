# Fabrication package

## Stack-up

Two-layer board. Layers present in the PCB document:

| Layer | Purpose |
|---|---|
| `TOP` | Top copper |
| `BOTTOM` | Bottom copper |
| `TOPOVERLAY` | Top silkscreen |
| `KEEPOUT` | Board outline / keep-out |
| `MECHANICAL1` | Mechanical / dimensions |
| `MULTILAYER` | Through-hole pads |

Form factor is the **Arduino Uno shield** outline (`ArduinoUnoShield`
footprint), so the board stacks directly onto an Uno.

## Generated outputs

`manufacturing/CAMtastic1_GERBER_FILES.Cam` bundles eight Gerber layers:

| File | Layer |
|---|---|
| `biosig.gtl` | Top copper |
| `biosig.gbl` | Bottom copper |
| `biosig.gto` | Top overlay (silkscreen) |
| `biosig.gbo` | Bottom overlay |
| `biosig.gts` | Top solder mask |
| `biosig.gbs` | Bottom solder mask |
| `biosig.gko` | Keep-out / board outline |
| `biosig.gm15` | Mechanical 15 |

`manufacturing/CAMtastic2_NCR_Files.Cam` holds the NC drill data.

Both are Altium CAMtastic documents — the imported-and-checked form of the
output, which is the verification step before release to a fabricator.

## Sending this to a fabricator

CAMtastic `.Cam` files are an Altium container, not the raw Gerbers a board
house expects. Re-export from Altium as a plain RS-274X Gerber set plus
Excellon drill, zip that, and send the zip.
