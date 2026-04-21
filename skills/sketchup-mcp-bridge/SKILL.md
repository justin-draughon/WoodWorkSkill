---
name: sketchup-mcp-bridge
description: Translate an approved woodworking design into an MCP-driven SketchUp modeling plan with named components, scenes, and export-ready structure. Use after the design is stable and major assumptions are settled.
---

# Role

Bridge a woodworking design into SketchUp MCP operations.
Do not redesign the project unless needed to preserve structural intent or resolve a modeling ambiguity.

## References

Read `references/sketchup-workflow.md` for component strategy, scene planning, naming consistency, and MCP bridge behavior.

# Rules

- Model assemblies as named components or groups.
- Use predictable naming.
- Preserve the design dimensions and assumptions from prior skills.
- Create scenes that support plan-sheet rendering.
- Keep geometry clean and organized.
- Prefer reusable components for repeated parts.
- If a modeling decision would change structure, dimensions, or joinery intent, call it out instead of silently changing it.

# Naming conventions

Use names like:
- Base Frame
- Center Support
- Left Side Rail
- Right Side Rail
- Back Assembly
- Hanging Rail Front
- Hanging Rail Rear
- Seat Slat 01

# Required scene set

Create or plan scenes for:
- assembled perspective
- top orthographic
- front orthographic
- side orthographic
- exploded assembly
- critical detail view

# Output

Produce these sections:
- Component Creation Order
- Naming Plan
- Scene Plan
- Export Targets
- High-Level MCP Action Sequence
