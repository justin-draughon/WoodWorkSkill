---
name: freecad-mcp-bridge
description: Translate an approved woodworking design into a FreeCAD MCP modeling plan with named parametric parts, views, and export targets. Use after the design is stable and assumptions are settled, when FreeCAD MCP is the available CAD tool.
---

# Role

Bridge a woodworking design into FreeCAD MCP operations.
Do not redesign the project unless needed to preserve structural intent or resolve a modeling ambiguity.

This is the FreeCAD sibling of `sketchup-mcp-bridge`. Use whichever matches the CAD tool the local
agent actually has. FreeCAD is free and open source with no account gate; it is the more accessible target.

## References

Read these when helpful:
- `references/freecad-workflow.md` for the FreeCAD/Part-workbench modeling sequence, units, and export guidance
- `references/mcp-tool-map.md` for the tool surface, argument names, and the silent-failure traps

# Core rules

- **FreeCAD works in millimetres internally.** Convert every imperial dimension from the design spec
  deliberately and exactly (1 in = 25.4 mm). Never let the model drift from the spec's stated sizes.
- Express the design in a **parametric way**: define the key dimensions first (variables or named
  constraints), then build features that reference them, so the model can be re-sized by changing a value.
- Model assemblies as **named objects**, one per real-world part, matching the names the plan renderer and
  cut list use.
- Preserve the design dimensions and assumptions from prior skills.
- Keep geometry clean and organized; avoid stray construction geometry left in the tree.
- Reuse repeated parts as copies/arrays rather than hand-modelling each one.
- If a modeling decision would change structure, dimensions, or joinery intent, call it out instead of
  silently changing it.
- **The woodworking design is in actual lumber sizes, not nominal.** A "2x4" member is 38 x 89 mm. This is
  the single easiest place to introduce an error, so state the conversion for load-bearing members.

# Naming conventions

Reuse the names the other skills already use, with a consistent suffix when a part repeats:

- Base Frame
- Center Support
- Left Side Rail
- Right Side Rail
- Back Assembly
- Hanging Rail Front
- Hanging Rail Rear
- Seat Slat 01, Seat Slat 02, ...

FreeCAD sanitises and de-duplicates object names (`Box` may become `Box001`), so record the **actual**
returned name after each creation — every later edit needs the real one.

# Required view set

Plan views to match the plan-sheet renderer's needs:

- assembled isometric
- top
- front
- side
- exploded assembly
- critical detail view (hanging points, joinery, or repeated assemblies)

# Units and export targets

- Model in millimetres (FreeCAD's native unit).
- Export **STL** for 3D printing or mesh tooling.
- Export **STEP** when a downstream CAD/CAM tool needs true solid geometry.
- Note the units on any export, since STL carries no unit metadata.

# Output

Produce these sections:
- Unit + Dimension Conversion Table (imperial spec value -> millimetres used)
- Object Creation Order
- Naming Plan
- Parametric Notes (which dimensions should drive others)
- Scene / View Plan
- Export Targets
- High-Level MCP Action Sequence

# Hand-off

The rendered views and the export files feed:
- `plan-renderer-skill` for plan sheets
- `cut-list-skill` for the purchase and cut list
