# Guitar CAD Project — Agent Notes

## What this project is

A KittyCAD Language (KCL) parametric model of an acoustic guitar body, authored in Zoo Design Studio. All units are inches (`@settings(defaultLengthUnit = in)`). The model is structured as separate modules that import from one another; `main.kcl` is the assembly entry point.

While this is a custom design, if you are looking for design inspiration, the design is closest in mindshare to a Gibson Hummingbird.

## Design conventions to keep in mind
- This design is in inches. Under no circumstances you should try to change that. If you encounter metric somewhere, convert it to inches.
- Guitars are organic shapes built from curves and arcs, with the occasional straight line. There is never a time where I want you to approximate a solution for a curved object using chords or lines. Stop immediately instead of presenting that type of solution.
- If I present a DXF, STEP or other reference image, USE IT! Don't guess at what I might want, the reference shows you exactly what I want.
