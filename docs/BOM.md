# Bill of materials

26 placed components, read from `hardware/BioSig.PcbDoc`.

| Designator | Part | Footprint | Qty |
|---|---|---|---|
| U1 | INA128 instrumentation amplifier | SOIC127P600X265-8N (SOIC-8) | 1 |
| U2, U4 | UA741 operational amplifier | PDIP8 | 2 |
| R1–R10 | Resistor | Axial_10mm_0.7mm | 10 |
| C1–C8 | Ceramic capacitor | Ceramic_Disc_P3.0 | 8 |
| VR1 | Trim potentiometer (T93YA) | TrimPot | 1 |
| J1 | Stereo jack (XB-PJ-320DB) — electrode cable entry | Stereo_Jack | 1 |
| J2 | 3-pos 5.0 mm terminal block (DG306-5.0) | 3P_5.0mm | 1 |
| H1 | 3-pin header | Pin_Header_3x1_2.54 | 1 |
| H2 | 6-pin header | Pin_Header_6x1_2.54 | 1 |

> **Values not listed.** The zip contains no schematic, and the PCB document
> carries footprints and designators but no populated value fields. Resistor
> and capacitor values must be read off the schematic, which is not in this
> repository — see [Missing files](../README.md#missing-files).

## Nets of interest

| Net | Meaning |
|---|---|
| `RA` | Right-arm electrode |
| `LA` | Left-arm electrode |
| `3V3` | 3.3 V supply rail (from the Uno) |
| `GND` | Ground |

`RA` and `LA` with no third drive electrode makes this a two-electrode,
**Lead I** differential measurement.
