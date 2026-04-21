# Woodworking AI Repo Template

This repo is a starter template for generating woodworking plans with an AI coding agent plus SketchUp MCP.

It includes:
- modular skills for design, rendering, cut lists, and structural review
- a SketchUp MCP bridge skill
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

## Basic workflow

1. Put the skill folders where your agent can load them.
2. Register your SketchUp MCP server in your local Codex config.
3. Start with the prompt in `prompts/crib-mattress-porch-swing.md`.
4. Let the agent:
   - design the build
   - validate structure
   - create SketchUp components/scenes
   - render plan sheets
   - produce a cut list

## Notes

- This template is intentionally plain text and easy to edit.
- Structural review here is a practical woodworking check, not an engineering stamp.
- For hanging, child-related, or heavily load-bearing projects, require explicit assumptions and conservative warnings.
- Replace any MCP command placeholders with the launch command that works on your machine.
