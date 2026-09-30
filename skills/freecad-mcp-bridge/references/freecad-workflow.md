# FreeCAD Workflow

## Units

FreeCAD models in **millimetres** by default. The design spec is in **actual lumber inches**, so every
dimension crosses a unit boundary. Make the conversions explicit rather than mental math.

Common actual lumber sizes, in millimetres:

| Nominal | Actual (in) | Actual (mm) |
| --- | --- | --- |
| 1x2 | 0.75 x 1.5 | 19 x 38 |
| 1x3 | 0.75 x 2.5 | 19 x 64 |
| 1x4 | 0.75 x 3.5 | 19 x 89 |
| 1x6 | 0.75 x 5.5 | 19 x 140 |
| 1x8 | 0.75 x 7.25 | 19 x 184 |
| 2x2 | 1.5 x 1.5 | 38 x 38 |
| 2x3 | 1.5 x 2.5 | 38 x 64 |
| 2x4 | 1.5 x 3.5 | 38 x 89 |
| 2x6 | 1.5 x 5.5 | 38 x 140 |
| 4x4 | 3.5 x 3.5 | 89 x 89 |

Round to whole millimetres unless a fit clearance genuinely needs sub-millimetre precision. State the
rounding so the cut list and the model agree.

## Modeling priorities

1. preserve dimensions from the approved spec
2. preserve assembly structure and part names
3. keep names consistent with the cut list and plan labels
4. build parametrically so the design can be re-sized
5. avoid stray geometry and duplicate solids

## Modeling sequence

1. Create the document, named for the project.
2. Establish the driving dimensions — either a variable set or named constraints — for overall length,
   width, height, and member cross-sections.
3. Model the primary structure first (the load-bearing frame), as individual named parts.
4. Add secondary structure (bracing, cleats, rails) referencing the same driving dimensions.
5. Add surfaces — slats, panels, seat/table surfaces — as repeated parts.
6. Add trim and hardware representations only if they help the assembly views.
7. Assemble with placement so the assembled view is meaningful.
8. Generate the required views.
9. Export.

## Object strategy

- Model each distinct real-world part as its own object with a human-readable name.
- Duplicate via copy or a pattern rather than re-modelling identical parts individually.
- Fuse only when the design genuinely treats members as one solid; keep separate members separate so the
  exploded view and cut list stay honest.
- Keep the model tree shallow enough for a builder to follow.

## View strategy

Prepare views matching the plan-sheet renderer. In FreeCAD these come from camera orientations rather
than SketchUp style "scenes" — capture each as a screenshot through the MCP tool rather than expecting
named scenes to exist:

- assembled isometric
- top
- front
- side
- exploded assembly
- critical detail

Use `get_view` with a view name for a one-off capture. If a tool in the local build does not accept a
`view_name` value, fall back to the default view rather than guessing further values.

## Export guidance

| Format | Use when | Notes |
| --- | --- | --- |
| **STL** | 3D printing, mesh tooling, visualisation | Mesh only, **carries no unit metadata** — state millimetres |
| **STEP** | downstream CAD/CAM, true solid geometry | Preferred when the next tool is CAD |
| **OBJ / GLTF** | 3D viewers and web previews | Presentation only |

Export per part or per assembly depending on the consumer. For a cut list, per-part export is usually more
useful; for a client preview, the assembled export is.

## MCP bridge behavior

Describe a **high-level action sequence**, not invented low-level commands. If a specific tool name or
argument is uncertain, output an ordered modelling plan that a local MCP-capable agent can execute, and
let that agent resolve the exact call. This mirrors `sketchup-mcp-bridge` deliberately — the plan should
survive a different MCP build.

## Runtime precondition

FreeCAD MCP drives a running FreeCAD with the FreeCADMCP addon's RPC server started. If FreeCAD is not
open with the RPC server up, modelling tools fail. In that case still produce the full plan: dimension
conversion table, object order, naming plan, view plan, export targets, and action sequence — so the work
can be executed the moment the CAD session is available.
