# Woodworking AI Repo Template

This repo is a starter template for generating woodworking plans with an AI coding agent plus a CAD MCP server.

It includes:
- modular skills for design, rendering, cut lists, and structural review
- two interchangeable CAD bridges: FreeCAD (free) and SketchUp (requires Pro)
- routing instructions in `AGENTS.md`
- sample prompts
- a sample MCP config file you can adapt locally

This repo is intentionally lightweight. The included skills are compact starter skills and can be expanded with `references/` files as the workflow matures.

## Repo layout

```text
.
├── AGENTS.md
├── README.md
├── skills/
│   ├── woodworking-plan-generator/
│   │   └── SKILL.md
│   ├── plan-renderer-skill/
│   │   └── SKILL.md
│   ├── cut-list-skill/
│   │   └── SKILL.md
│   ├── structural-validator-skill/
│   │   └── SKILL.md
│   ├── freecad-mcp-bridge/
│   │   └── SKILL.md
│   └── sketchup-mcp-bridge/
│       └── SKILL.md
├── prompts/
│   ├── crib-mattress-porch-swing.md
│   └── generic-project-template.md
├── examples/
│   └── expected-output-outline.md
└── .codex/
    └── config.toml.example
```

Each skill now includes a compact `references/` folder for the non-obvious rules that help the workflow stay consistent without bloating the main SKILL.md files.

## Choosing a CAD bridge

Both bridges do the same job — turn an approved design into modelling operations. Pick one:

| Bridge | Cost | Requirements |
| --- | --- | --- |
| `freecad-mcp-bridge` | **Free / open source** | FreeCAD + the FreeCADMCP addon. No account or licence. |
| `sketchup-mcp-bridge` | **SketchUp Pro (~$399/yr)** | Desktop SketchUp + the SketchupMCP extension. |

SketchUp's web app cannot host extensions, and extension support is absent from the Free and Go tiers, so
SketchUp needs a **Pro** licence. FreeCAD has no such gate and is the default recommendation.

Not sure which you have? The agent will still produce the full plan — dimensions, component list, view
requirements, cut list, validation summary — even with no CAD tool present.

## Basic workflow

1. Put the skill folders where your agent can load them.
2. Register your CAD MCP server in your local agent config (see `.codex/config.toml.example`).
3. Start with the prompt in `prompts/crib-mattress-porch-swing.md`.
4. Let the agent:
   - design the build
   - validate structure
   - create CAD components and views
   - render plan sheets
   - produce a cut list

## Notes

- This template is intentionally plain text and easy to edit.
- Structural review here is a practical woodworking check, not an engineering stamp.
- For hanging, child-related, or heavily load-bearing projects, require explicit assumptions and conservative warnings.
- Replace any MCP command placeholders with the launch command that works on your machine.
- If a bridge's CAD tool is not running, the agent still emits a high-level action sequence rather than
  inventing tool calls that may not exist locally.
- **Units:** the design is in actual lumber inches (`references/lumber.md`); FreeCAD models in millimetres.
  The FreeCAD bridge includes an explicit conversion table.

