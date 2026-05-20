# Guitar CAD Project — Agent Notes

## What this project is

A KittyCAD Language (KCL) parametric model of an acoustic guitar body, authored in Zoo Design Studio. All units are inches (`@settings(defaultLengthUnit = in)`). The model is structured as separate modules that import from one another; `main.kcl` is the assembly entry point.

While this is a custom design, if you are looking for design inspiration, the design is closest in mindshare to a Gibson Hummingbird.

## Design conventions to keep in mind
- This design is in inches. Under no circumstances you should try to change that. If you encounter metric somewhere, convert it to inches.
- Guitars are organic shapes built from curves and arcs, with the occasional straight line. There is never a time where I want you to approximate a solution for a curved object using chords or lines. Stop immediately instead of presenting that type of solution.
- If I present a DXF, STEP or other reference image, USE IT! Don't guess at what I might want, the reference shows you exactly what I want.
- If I give you a reference image and it seems like items might be parallel or perpendicular, try to model it that way. It's likely that I would do that in real life, I wouldn't likely choose 89.6 degrees instead of a perfect right angle.

### Brace scalloping design intent

Guitar braces are structural parts, but their ends should generally be scalloped
or feathered for weight reduction and flexibility unless I explicitly request a
straight, full-height brace.

When creating or modifying braces with scalloped ends:

- The scallop target applies to the **final visible post-trim brace end**, not
  the raw/pre-trim construction endpoint.
- If a brace terminates at kerfing, lining, a rim, or a block, first extend the
  raw brace far enough to cross the boundary, then physically trim it back to the
  actual mating part/boundary. Do not merely make the pre-trim endpoint thin.
- The brace should still terminate exactly at its intended physical boundary
  with a real butt joint or trim. Do not use visual masking or display-only
  hiding to fake the result.
- At the post-trim end where a brace butts into kerfing/lining, the brace should
  usually be feathered down to roughly `1/16in` to `1/8in` thick unless a
  different dimension is specified.
- The brace should smoothly regain full height toward the structurally important
  region, such as the X-brace intersection, bridge area, center span, or other
  load path.
- Use smooth arcs/curves for scallops. Do not replace curved scallops with
  straight-line/chord approximations.
- Preserve the brace’s intended plan-view length, mating boundary, intersections,
  and trim relationships while changing only the scallop/profile height.
- Validate scallops from a view that shows the actual post-trim end thickness,
  not just the raw construction profile.

For protected/final braces, this design intent should only be applied if I
explicitly grant permission to modify those protected brace bodies.

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

The current acoustic-guitar body is finalized. These protections are guardrails
for the completed body, not a project-wide read-only lock.

You may add new neck geometry in new neck-focused files and assemble it with the
body. However, if neck integration appears to require changing any protected body,
block, mortise, binding, lining, soundboard, back, bridge, brace, rosette, or
outline geometry, stop and ask for explicit permission first.

The following current body pieces are final geometry:

### Top / soundboard shell

- `topSoundboard`
- `topSoundboardExport`
- `topSoundboardWithRosetteChannel`
- `topBindingTrimmed`
- `topBindingTrimmedExport`

### Rosette

- `rosetteInnerPurfling`
- `rosetteMainInlay`
- `rosetteOuterPurfling`
- `rosetteChannelCutter`

### Top primary braces

- `xBraceBassPlanTrim`
- `xBraceTreblePlanTrim`
- `xBraceBassPlanTrimExport`
- `xBraceTreblePlanTrimExport`
- `upperTransverseBrace`
- `upperTransverseBraceExport`
- `popsicleBrace`
- `popsicleBraceExport`

### Top secondary braces

- `toneBarUpper`
- `toneBarLower`
- `toneBarUpperExport`
- `toneBarLowerExport`
- `topSideBrace1`
- `topSideBrace2`
- `topSideBrace3`
- `topSideBrace4`
- `topSideBrace1Export`
- `topSideBrace2Export`
- `topSideBrace3Export`
- `topSideBrace4Export`
- `topSideBrace3FixedExport`
- `topSideBrace4FixedExport`

### Top internal reinforcement

- `bridgePlate`
- `bridgePlateExport`
- `soundholeReinforcement`
- `soundholeReinforcementExport`

### Rim, blocks, sides, and linings

- `rimSides`
- `rimNeckBlock`
- `rimTailBlock`
- `rimSideBlocks`
- `rimTopKerfedLining`
- `rimBackKerfedLining`
- `rimSidesExport`
- `rimNeckBlockExport`
- `rimTailBlockExport`
- `rimSideBlocksExport`
- `rimTopKerfedLiningExport`
- `rimBackKerfedLiningExport`

### Back shell and back braces

- `backplate`
- `backBinding`
- `backCenterGlueSeamBrace`
- `backTransverseBrace1`
- `backTransverseBrace2`
- `backTransverseBrace3`
- `backTransverseBrace4`
- `backplateExport`
- `backBindingExport`
- `backCenterGlueSeamBraceExport`
- `backTransverseBrace1Export`
- `backTransverseBrace2Export`
- `backTransverseBrace3Export`
- `backTransverseBrace4Export`

### Bridge, saddle, and bridge pins

- `bridge`
- `saddle`
- `bridgePin1`
- `bridgePin2`
- `bridgePin3`
- `bridgePin4`
- `bridgePin5`
- `bridgePin6`
- `bridgeExport`
- `saddleExport`
- `bridgePin1Export`
- `bridgePin2Export`
- `bridgePin3Export`
- `bridgePin4Export`
- `bridgePin5Export`
- `bridgePin6Export`

### Foundational geometry that drives finalized pieces

Do not modify foundational geometry that affects the finalized body, including:

- `sketchGuitar`
- `sketchGuitarInner`
- `guitarBodyRegion`
- `guitarInnerBodyRegion`
- `guitarOuterPlanSolid`
- `guitarInnerPlanSolid`
- `guitarLiningInnerPlanSolid`
- `bodySideProfile`
- `sideTopProfilePrism`
- `sideMiddleProfilePrism`
- `sideBackProfilePrism`
- `topLiningProfile`
- `topLiningProfilePrism`
- `backLiningProfile`
- `backLiningProfilePrism`
- `topBindingRabbetProfile`
- related top/back binding profile prisms
- `backKerfedLiningRemainingProfile`
- related remaining-lining prism
- bridge-pin layout variables in `guitar_bridge_pin_holes.kcl`

Do not modify any code, dimensions, sketches, regions, lofts, trims, booleans,
intersections, cutters, appearances, hide/export variables, names, imports,
display-group references, or assembly references related to the protected bodies
above unless I explicitly grant permission for that exact body or source section.

This includes, but is not limited to:

- body outline and inner outline construction in `guitar_outline.kcl`
- side/top/back profile construction in `guitar_side_profile.kcl`
- top/back lining profiles and lining inner plan construction in
  `guitar_kerfed_linings.kcl`
- binding/rabbet profile construction in
  `guitar_top_binding_rabbet_profiles.kcl`
- all soundboard, top binding, brace, bridge plate, and soundhole reinforcement
  construction in `guitar_top.kcl`
- lower side-brace compatibility exports in `guitar_top_side_brace_fixes.kcl`
- all rosette construction in `guitar_rosette.kcl`
- all rim, block, side block, and kerfed-lining construction in `guitar_rim.kcl`
- all backplate, back binding, center seam brace, and back transverse brace
  construction in `guitar_back.kcl`
- all bridge, saddle, and bridge-pin construction in `guitar_bridge.kcl`
- shared bridge-pin hole layout values in `guitar_bridge_pin_holes.kcl`

If a future request appears to require changing any protected body, stop and ask
for explicit permission before making the edit.