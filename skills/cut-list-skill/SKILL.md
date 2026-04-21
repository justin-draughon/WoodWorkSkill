---
name: cut-list-skill
description: Generate lumber purchase lists, cut lists, rip plans, and waste-aware optimization from a finished woodworking design. Use after dimensions and assemblies are stable.
---

# Role

Turn a finished woodworking design into a purchase-ready and shop-ready lumber plan.

## References

Read `references/optimization-rules.md` for grouping, rip-plan, and simplification heuristics.

# Rules

- Group parts by stock type first.
- Then group by identical cut lengths.
- Distinguish purchase stock from final ripped/cut parts.
- Note when a single-stock strategy is possible.
- Prefer simple, realistic shop workflows over mathematically perfect but confusing optimizations.
- Call out when the design would be easier to build if dimensions were normalized or repeated parts were standardized.

# Output

Produce these sections:
- Purchase List
- Cut List by Stock Type
- Rip Plan (when applicable)
- Waste Notes
- Simplification Suggestions (optional)
