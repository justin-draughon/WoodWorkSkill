---
name: woodworking-plan-generator
description: Generate practical woodworking project designs using standard lumber, actual dimensions, parametric sizing, and build-ready assemblies. Use when a user asks for woodworking plans, furniture/project design, dimensional build specs, or a buildable concept before rendering, cut-list generation, or SketchUp modeling.
---

# Role

Turn a user request into a buildable woodworking design spec before any rendering or cut-list work starts.

## References

Read these when helpful:
- `references/lumber.md` for actual lumber dimensions and stock defaults
- `references/design-rules.md` for design priorities, joinery defaults, and clarification triggers
- `references/project-types.md` for project-specific heuristics

# Core rules

- Use actual dimensions, not nominal lumber sizes.
- Prefer the fewest lumber types practical.
- Allow ripped stock when useful.
- Break the project into load-bearing structure, secondary structure, trim/slats, and hardware.
- Design for buildability, not just appearance.
- Prefer simple joinery and repeatable parts unless the user asks for a more advanced build.
- State assumptions explicitly so later skills preserve them.

# Stop-and-ask conditions

If any of these are missing or ambiguous, do not finalize the design without calling them out:

- overall target dimensions
- load or use assumptions
- indoor vs outdoor use
- hanging / mounting conditions
- material restrictions
- safety-critical context such as child use, elevated loads, or suspension

If needed, proceed with a provisional design, but label assumptions clearly.

# Required process

1. Identify project type and use case.
2. Establish overall dimensions and fit clearances.
3. Identify missing constraints and safety-sensitive assumptions.
4. Select material strategy.
5. Define major assemblies.
6. Define joinery defaults.
7. Note assumptions that later skills must preserve.

# Output

Produce these sections:
- Design Summary
- Overall / Parametric Dimensions
- Material Strategy
- Assembly Breakdown
- Joinery Defaults
- Assumptions
- Open Questions (if anything important is still missing)

# Hand-off

Pass the design to:
- `structural-validator-skill` for safety review
- `sketchup-mcp-bridge` for modeling
- `plan-renderer-skill` for plan sheets
- `cut-list-skill` for lumber optimization
