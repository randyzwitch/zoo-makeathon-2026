# Acoustic Guitar — Parametric CAD Model

A parametric 3D model of an acoustic guitar body, authored in [Zoo Design Studio](https://zoo.dev) using KittyCAD Language (KCL). Inspired by the Gibson Hummingbird body style.

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
