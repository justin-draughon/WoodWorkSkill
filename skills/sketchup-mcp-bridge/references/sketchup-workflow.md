# SketchUp Workflow

## Modeling priorities

1. preserve dimensions
2. preserve assembly structure
3. keep names consistent
4. create useful scenes
5. avoid messy duplicate geometry

## Component strategy

- Model repeated parts as reusable components when practical.
- Use groups or higher-level components for assemblies.
- Keep raw geometry organized and avoid loose clutter.

## Scene strategy

Prepare scenes that align with plan rendering:
- assembled perspective
- top orthographic
- front orthographic
- side orthographic
- exploded assembly
- critical detail scene

## Naming guidance

Use names that are:
- human-readable
- stable across outputs
- consistent with the cut list and plan labels

## MCP bridge behavior

The bridge should describe a high-level action sequence, not invent low-level MCP commands that may not exist on the local machine.
If command availability is unclear, output an ordered modeling plan that a local MCP-capable agent can execute.
