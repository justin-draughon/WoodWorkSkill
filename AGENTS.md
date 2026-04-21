# AGENTS.md

Use the skills in this order when a user asks for woodworking plans, build drawings, cut lists, or SketchUp-driven project generation.

## Routing order

1. `woodworking-plan-generator`
2. `structural-validator-skill`
3. `sketchup-mcp-bridge`
4. `plan-renderer-skill`
5. `cut-list-skill`

## Default behavior

- Start by turning the request into a parametric design spec.
- Use actual lumber dimensions, not nominal dimensions.
- Prefer the fewest lumber types practical for the build.
- If SketchUp MCP is available, create named components and named scenes.
- Validate safety-critical or hanging projects before finalizing plans.
- Render outputs as clean plan-sheet style views, not loose prose.
- End with a purchase list and cut list.

## For hanging or load-bearing builds

Always perform an explicit structural review before presenting final plans.
Call out any assumptions about mounting surface, fasteners, and safe load.

## If SketchUp MCP is unavailable

Still generate:
- a design spec
- a component list
- plan-sheet view requirements
- a cut list
- a validation summary

## Output targets

When possible, produce:
- top view
- front view
- side view
- exploded assembly view
- one or more detail views
- cut list
- hardware list
- safety notes
