# Optimization Rules

## Priority order

Optimize in this order:
1. clarity
2. realistic shop workflow
3. reduced lumber variety
4. reduced waste
5. mathematical efficiency

## Cut-list grouping

Group by:
1. stock type
2. thickness x width
3. final part name
4. repeated cut length / quantity

## Rip-plan guidance

Include a rip plan when:
- parts are derived from wider stock
- multiple narrow repeated parts are needed
- the build benefits from batching rip operations

Skip elaborate rip plans when the simplification benefit is low.

## Simplification heuristics

Suggest simplification when it would:
- reduce unique cut lengths
- reduce unique stock widths
- turn one-off parts into repeated parts
- reduce oddball dimensions without materially affecting function

## Purchase-list guidance

Distinguish clearly between:
- purchase stock
- rough cut parts
- final dimensioned parts
