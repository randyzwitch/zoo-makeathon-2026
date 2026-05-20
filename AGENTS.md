# Guitar CAD Project — Agent Notes

## Project overview

This is a KittyCAD Language (KCL) parametric model of an acoustic guitar body,
authored in Zoo Design Studio.

- All units are inches: `@settings(defaultLengthUnit = in)`.
- Do not change the project to metric. If metric dimensions appear, convert them
  to inches.
- `main.kcl` is the assembly entry point.
- The model is organized as separate modules for the outline, side profile,
  linings, rim, top, back, bridge, rosette, and related subassemblies.
- The design is custom, but closest in spirit to a Gibson Hummingbird.

The current guitar body is considered finalized. Future work may add a neck in
new neck-focused files, but the finalized body geometry should not be modified
unless explicit permission is granted.

## General design conventions

- Treat the `.kcl` files on disk as the source of truth.
- Before significant edits, inspect the current project files rather than relying
  on prior chat state.
- Do not refactor the project unless explicitly asked.
- Prefer minimal, reversible edits that preserve existing geometry, dimensions,
  naming, and module organization.
- Keep separate manufactured or functional parts as separate bodies/modules. Do
  not fuse components together merely to make display easier.
- Guitars are organic shapes built from curves and arcs, with occasional straight
  lines. Do not approximate curved guitar geometry using straight chords or line
  segments. If a curved solution cannot be modeled correctly, stop and ask.
- If a DXF, STEP, image, screenshot, or other reference is provided, use it as
  the source of design intent rather than guessing.
- If reference geometry appears intended to be parallel, perpendicular,
  concentric, symmetric, or tangent, prefer the exact geometric relationship over
  near-miss numeric angles or offsets.

## Display and validation expectations

- After any modeling or visibility change, execute the project and inspect/render
  the result before claiming success.
- For nontrivial visual changes, verify the result with a snapshot from a useful
  angle.
- If the viewport appears inconsistent with the file contents, stop and diagnose
  a possible sync issue before continuing.
- For suspected sync issues, add a harmless marker comment to the edited file and
  ask me to verify whether it appears in Zoo's code editor.
- The default inspection view should preserve all actual solids unless I
  explicitly ask to isolate or hide something.
- For “show all solids except X,” keep every solid visible except the named
  exclusions.
- Construction sketches/drawings should generally be hidden in presentation or
  inspection views.
- Do not hide valid solid edge outlines merely because they look like stray
  lines; distinguish solid edges from construction geometry.
- Do not use masking, hiding, display-only workarounds, or visual tricks to
  represent part fit. The goal is accurate part geometry.

## Temporary files

- Temporary validation files should be avoided unless necessary.
- If temporary files are created, use an obvious `zz*` prefix.
- Delete all `zz*` temporary files before finalizing an edit.
- Do not leave temporary validation, analysis, or review files in the project.

## Brace scalloping design intent

Guitar braces are structural parts, but their ends should generally be scalloped
or feathered for weight reduction and flexibility unless I explicitly request a
straight, full-height brace.

When creating or modifying brace scallops:

- The scallop target applies to the **final visible post-trim brace end**, not
  the raw/pre-trim construction endpoint.
- If a brace terminates at kerfing, lining, a rim, a block, or another brace,
  first extend the raw brace far enough to cross the boundary, then physically
  trim it back to the actual mating part or boundary.
- The brace should terminate exactly at its intended physical boundary with a
  real butt joint or trim.
- Do not merely make the pre-trim endpoint thin if that point will be cut away.
- Do not use visual masking or display-only hiding to fake a butt joint.
- At the post-trim end where a brace butts into kerfing/lining, the brace should
  usually feather down to roughly `1/16in` to `1/8in` thick unless a different
  dimension is specified.
- The brace should smoothly regain full height toward the structurally important
  region, such as the X-brace intersection, bridge area, center span, or other
  load path.
- Scallops should be concave material-removing curves, not convex bulges.
- Use smooth arcs/curves for scallops. Do not replace curved scallops with
  straight-line/chord approximations.
- Preserve the brace’s intended plan-view length, mating boundary,
  intersections, and trim relationships while changing only the
  scallop/profile height.
- Validate scallops from a view that shows the actual post-trim end thickness,
  not just the raw construction profile.

For protected/final braces, this design intent should only be applied if I
explicitly grant permission to modify those protected brace bodies.

## Protected final geometry

The current acoustic-guitar body is finalized. These protections are guardrails
for the completed body, not a project-wide read-only lock.

You may add new neck geometry in new neck-focused files and assemble it with the
body. However, if neck integration appears to require changing any protected
body, block, mortise, binding, lining, soundboard, back, bridge, brace, rosette,
outline, or foundational construction geometry, stop and ask for explicit
permission first.

Do not modify any code, dimensions, sketches, regions, lofts, trims, booleans,
intersections, cutters, appearances, hide/export variables, names, imports,
display-group references, or assembly references related to the protected bodies
or source sections below unless I explicitly grant permission for that exact
body or source section.

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

### Protected source sections

The protected bodies above are driven by these source areas. Do not modify these
areas unless explicitly permitted for the exact protected part or source section:

- body outline and inner outline construction in `guitar_outline.kcl`
- side/top/back profile construction in `guitar_side_profile.kcl`
- top/back lining profiles and lining inner plan construction in
  `guitar_kerfed_linings.kcl`
- binding/rabbet profile construction in
  `guitar_top_binding_rabbet_profiles.kcl`
- soundboard, top binding, brace, bridge plate, and soundhole reinforcement
  construction in `guitar_top.kcl`
- lower side-brace compatibility exports in `guitar_top_side_brace_fixes.kcl`
- rosette construction in `guitar_rosette.kcl`
- rim, block, side block, and kerfed-lining construction in `guitar_rim.kcl`
- backplate, back binding, center seam brace, and back transverse brace
  construction in `guitar_back.kcl`
- bridge, saddle, and bridge-pin construction in `guitar_bridge.kcl`
- shared bridge-pin hole layout values in `guitar_bridge_pin_holes.kcl`
- assembly references to protected bodies in `main.kcl`

If a future request appears to require changing any protected body or protected
source section, stop and ask for explicit permission before making the edit.