# Acoustic Guitar — Parametric CAD Model

A parametric 3D model of an acoustic guitar body, authored in [Zoo Design Studio](https://zoo.dev) using KittyCAD Language (KCL). Inspired by the Gibson Hummingbird body style.

<img width="3840" height="1600" alt="Screenshot (73)" src="https://github.com/user-attachments/assets/e40722be-3683-4aa0-a01e-ce8eeda9937f" />


## Overview

All geometry is defined in KCL — a parametric modeling language where dimensions, curves, and relationships are expressed as code. The model is modular: each file contains a small number of closely related parts, and `main.kcl` is the assembly entry point that imports all modules and controls scene visibility.

All units are **inches**.

## Opening the Project

Open the project folder in [Zoo Design Studio](https://zoo.dev). The active entry point is `main.kcl`, which renders the assembly with construction sketches hidden and the back plate excluded for interior visibility.

## Design Notes

- **Curves only** — no straight-line approximations for organic guitar shapes.
- **Reference files are authoritative** — the DXF defines the body outline; don't deviate from it without updating the reference.
- **Keep modules separate** — each component is its own file; don't fuse parts together.
- **Visibility changes belong in `main.kcl`** — geometry modules should not be edited just to show or hide something.

## Statistics (for the Makeathon submission)

### Open body cluster: 24 pieces
- back plate, back binding, center seam brace
- 4 back transverse braces
- sides, neck block, tail block
- 1- 2 side blocks/braces
- top + back kerfed linings
### Pulled-off soundboard cluster: 40 pieces
- soundboard + top binding
- 18 rosette pieces
- 6 main top braces
- 4 top side/finger braces
- bridge plate + soundhole reinforcement
- bridge + saddle
- 6 bridge pins
