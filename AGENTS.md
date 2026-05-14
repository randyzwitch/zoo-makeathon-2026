# Guitar CAD Project — Agent Notes

## What this project is

A KittyCAD Language (KCL) parametric model of an acoustic guitar body, authored in Zoo Design Studio. All units are inches (`@settings(defaultLengthUnit = in)`). The model is structured as separate modules that import from one another; `main.kcl` is the assembly entry point.

While this is a custom design, if you are looking for design inspiration, the design is closest in mindshare to a Gibson Hummingbird.

## Design conventions to keep in mind
- This design is in inches. Under no circumstances you should try to change that. If you encounter metric somewhere, convert it to inches.
- Guitars are organic shapes built from curves and arcs, with the occasional straight line. There is never a time where I want you to approximate a solution for a curved object using chords or lines. Stop immediately instead of presenting that type of solution.
- If I present a DXF, STEP or other reference image, USE IT! Don't guess at what I might want, the reference shows you exactly what I want.
- If I give you a reference image and it seems like items might be parallel or perpendicular, try to model it that way. It's likely that I would do that in real life, I wouldn't likely choose 89.6 degrees instead of a perfect right angle.

## Zookeeper / AI assistant workflow expectations

### Source of truth and sync
- Treat the actual `.kcl` files on disk as the source of truth.
- Before making significant edits, inspect the current project files instead of relying on prior chat state.
- If the Zoo editor/viewport appears inconsistent with file contents, stop and diagnose sync before continuing.
- For suspected sync issues, add a harmless marker comment to the edited file and ask me to verify whether it appears in Zoo's code editor.

### Change safety
- Do not refactor the whole codebase unless I explicitly ask for a refactor.
- Prefer minimal, reversible edits that preserve existing geometry and dimensions.
- For visibility/display requests, edit only the assembly/entrypoint or visibility layer when possible.
- Do not modify geometry-producing modules for a visibility-only request unless there is no other way, and explain why first.
- Never “simplify” guitar curves into straight-line approximations.

### Validation requirements
- After any modeling or visibility change, execute the project and inspect/render the result before claiming success.
- For nontrivial visual changes, compare against the stated goal with a snapshot.
- If hiding sketches/drawings, verify that no construction sketches, planes, helper profiles, or leaked drawing edges remain visible.
- If hiding parts, verify both that the excluded parts are absent and that all requested solids remain visible.

### Guitar project display conventions
- The default useful inspection view should preserve all actual solids unless I explicitly ask to isolate a subset.
- For “show all solids except X,” keep every solid visible except the named exclusions.
- Construction sketches/drawings should generally be hidden in presentation/inspection views.
- Do not hide valid solid edge outlines just because they look like lines; distinguish solid edges from sketch/drawing geometry.

### Assembly/code organization
- Keep separate manufactured/functional parts as separate named bodies or modules.
- Do not fuse assembly components together just to make display easier.
- If a special presentation view is needed, prefer creating or editing a dedicated entrypoint/presentation file rather than damaging the modeling modules.

### Do not trust stale viewport state
If the user reports that the viewport does not match the expected result, do not insist that the model is correct. Re-inspect the active file, render a fresh snapshot, and check for editor/file sync mismatch.

## Protected final geometry

The following visible/back-assembly parts are final geometry:

- `rimNeckBlock`
- `rimTailBlock`
- `rimBackKerfedLining`
- `backCenterGlueSeamBrace`
- `backTransverseBrace1`
- `backTransverseBrace2`
- `backTransverseBrace3`
- `backTransverseBrace4`

Do not modify any code, dimensions, sketches, regions, lofts, trims, booleans,
intersections, cutters, appearances, hide/export variables, names, imports,
display-group references, or assembly references related to those parts.

This includes, but is not limited to:

- neck/tail block construction in `guitar_rim.kcl`, including `neckBlock*`,
  `tailBlock*`, `rimNeckBlock`, and `rimTailBlock`
- back kerfing construction in `guitar_rim.kcl`, including
  `backLiningBlockButtJoint*`, `backLiningPlanBandWithBlockButts`, and
  `rimBackKerfedLining`
- back kerfing source profile construction in `guitar_kerfed_linings.kcl`,
  including `backLiningProfile`, `backLiningProfileRegion`, and
  `backLiningProfilePrism`
- back center seam brace construction in `guitar_back.kcl`, including
  `centerSeamBrace*` and `backCenterGlueSeamBrace*`
- back transverse brace construction in `guitar_back.kcl`, including the related
  `b1*`, `b2*`, `b3*`, and `b4*` profile sketches, regions, half-span
  parameters, bottom-Z parameters, trim-span parameters, and brace construction
  logic

If a future request appears to require changing any of these protected parts,
stop and ask for explicit permission before making the edit.