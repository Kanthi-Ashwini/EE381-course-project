# BioSig — ECG Acquisition Shield

EE381 course project. A two-layer analog front-end PCB, designed in Altium,
that picks up a single-lead ECG and conditions it for sampling by an Arduino
Uno. The board is an **Uno shield**, so it stacks straight onto the host.

---

## Signal path

```
electrodes (RA, LA)  →  stereo jack J1
        →  INA128 instrumentation amp (U1), gain set by trimpot VR1
        →  UA741 conditioning stages (U2, U4)
        →  headers H1 / H2  →  Arduino Uno ADC
```

`RA` and `LA` are the right- and left-arm electrodes; with no third drive
electrode this is a two-electrode **Lead I** measurement. The `INA128` was
chosen for the front end because a biopotential this small has to be extracted
differentially, with common-mode mains interference rejected before any gain is
applied.

## Repository layout

```
hardware/BioSig.PcbDoc              Altium PCB layout (binary)
manufacturing/CAMtastic1_*.Cam      Gerber set, 8 layers
manufacturing/CAMtastic2_NCR*.Cam   NC drill data
docs/BOM.md                         26-component bill of materials + net list
docs/FABRICATION.md                 Stack-up, layer table, how to send to a fab
```

## Board summary

| | |
|---|---|
| Layers | 2 (top + bottom copper) |
| Form factor | Arduino Uno shield |
| Components | 26 |
| Front end | INA128 instrumentation amplifier |
| Gain control | Trim potentiometer (VR1) |
| Electrode input | Stereo jack (J1) + 3-pos 5.0 mm terminal block (J2) |
| Supply | 3.3 V rail from the Uno |
| Outputs | 3-pin and 6-pin headers |

Full parts table in [`docs/BOM.md`](docs/BOM.md); layer stack and Gerber
inventory in [`docs/FABRICATION.md`](docs/FABRICATION.md).

## Opening the design

`hardware/BioSig.PcbDoc` needs **Altium Designer**. There is no free viewer
that renders `.PcbDoc` faithfully; Altium's own free viewer or a trial licence
is the practical route. The Gerbers can be inspected in any Gerber viewer once
re-exported as RS-274X — see [`docs/FABRICATION.md`](docs/FABRICATION.md).

---

## Missing files

The source archive contained only the PCB document and the two CAMtastic
files. Not present, and worth adding before anyone else tries to use this:

- **No schematic (`.SchDoc`)** — so the filter topology, stage gains and every
  resistor/capacitor value are unrecoverable from this repo alone. The PCB
  carries footprints and designators but no populated value fields.
- **No project file (`.PrjPcb`)** — the documents do not open as one project.
- **No component values** in the layout, for the reason above.
- **No test results** — nothing here records whether the board was fabricated,
  populated or measured against a live signal.

Adding the schematic would be the single biggest improvement to this
repository; a photo of the assembled board and a captured ECG trace would be
the next two.
