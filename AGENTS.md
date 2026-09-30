# AGENTS.md

Use the skills in this order when a user asks for woodworking plans, build drawings, cut lists, or
CAD-driven project generation.

## Routing order

1. `woodworking-plan-generator`
2. `structural-validator-skill`
3. **CAD bridge** — pick one:
   - `freecad-mcp-bridge` (preferred: free and open source, no account or licence gate)
   - `sketchup-mcp-bridge` (requires SketchUp Pro desktop plus the SketchupMCP extension)
4. `plan-renderer-skill`
5. `cut-list-skill`

If the user names a CAD tool, use that bridge. If none is specified, prefer `freecad-mcp-bridge` — it has
no licence barrier — unless the user already works in SketchUp.

## Default behavior

- Start by turning the request into a parametric design spec.
- Use actual lumber dimensions, not nominal dimensions.
- Prefer the fewest lumber types practical for the build.
- If a CAD MCP is available, create named components/objects and the required views.
- Validate safety-critical or hanging projects before finalizing plans.
- Render outputs as clean plan-sheet style views, not loose prose.
- End with a purchase list and cut list.

## For hanging or load-bearing builds

Always perform an explicit structural review before presenting final plans.
Call out any assumptions about mounting surface, fasteners, and safe load.

## If no CAD MCP is available

Still generate:
- a design spec
- a component list
- plan-sheet view requirements
- a cut list
- a validation summary

Never invent low-level MCP commands for a tool that is not present. Emit a high-level action sequence that
a local MCP-capable agent can execute instead.

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
