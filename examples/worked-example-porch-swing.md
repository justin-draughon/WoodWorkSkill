# Worked Example - Crib Mattress Porch Swing

This example shows the intended flow of the skill chain from prompt to final deliverables.

---

## Example prompt

Design a porch swing sized for a standard crib mattress using pressure-treated lumber.

Project requirements:
- overall dimensions: sized to fit a standard crib mattress with practical fit clearance
- style: simple, sturdy, farmhouse-inspired
- primary use case: outdoor porch swing for lounging
- allowed materials: pressure-treated framing, exterior-rated fasteners, optional slat back/arms
- joinery preference: straightforward shop-friendly joinery
- output format: plan-sheet style diagrams plus cut list

Required deliverables:
- parametric design spec
- named parts/components
- structural review
- SketchUp scene plan
- rendered plan-sheet requirements
- cut list and purchase list
- hardware list
- build assumptions

---

## 1. Design output (woodworking-plan-generator)

### Design Summary
Outdoor porch swing sized around a standard crib mattress, using a simple rectangular base frame, slatted back, arm assemblies, and front/rear hanging rails. The design prioritizes straightforward construction, repeatable parts, and conservative support for seated human load.

### Overall / Parametric Dimensions
- mattress basis: standard crib mattress assumed at approximately 28 x 52 in
- fit clearance: add modest clearance for insertion and removal
- overall seat frame target: approximately 29.5 x 53.5 in
- overall swing width including arms: approximately 60 to 64 in depending on arm style
- seat height / back angle: tuned for lounge comfort, subject to final preference

### Material Strategy
- primary structure: 2x4 stock
- slats / lighter members: 1x4 stock
- hardware: exterior-rated structural fasteners and hanging hardware
- outdoor assumptions: corrosion-resistant fasteners and finish / maintenance plan

### Assembly Breakdown
- base frame
- front rail assembly
- rear rail assembly
- left arm assembly
- right arm assembly
- seat slats
- back slats
- hanging rail members / hanger connection points

### Joinery Defaults
- screwed and glued framing where appropriate
- outdoor-rated fasteners
- simple butt / lap-style framing where practical
- repeatable slat spacing

### Assumptions
- porch or beam structure is adequate for swing loads
- mounting details will be confirmed separately
- mattress dimensions are confirmed before final cut list
- build is for outdoor lounging, not a certified child product

### Open Questions
- preferred back angle
- preferred arm width / cup-holder style or not
- exact hanging method and substrate

---

## 2. Structural review output (structural-validator-skill)

### Validation Summary
The concept is structurally plausible for a porch swing if the mounting structure and hanging hardware are properly specified. The main structural focus is load path through the side assemblies and safe transfer into the hanging points.

### Load / Mounting Assumptions
- hanging from a structurally adequate porch beam or equivalent member
- dynamic human load is expected
- at least two properly sized hanging attachment points
- appropriate chain / rope / hardware selected for outdoor use

### Risks and Weak Points
- side-frame racking if arm and side assemblies are not tied together well
- pull-out or splitting risk at hanging points if hardware is attached too close to edges
- slat-only thinking without adequate frame support
- mounting capacity may be lower than swing-frame capacity

### Recommended Reinforcements
- reinforce hanging-point members
- provide clear through-bolt / lag assumptions
- use triangulation or stiff side connections where needed
- keep hanger placement aligned with major structural members

### Required Changes Before Build
- confirm hanger hardware spec
- confirm porch beam or support substrate
- confirm expected user load range

### Final Safety Caveats
This is a practical woodworking review, not an engineering certification. Hanging-seat safety depends heavily on mounting conditions and hardware selection.

---

## 3. SketchUp bridge output (sketchup-mcp-bridge)

### Component Creation Order
1. Base Frame
2. Front Rail
3. Rear Rail
4. Left Arm Assembly
5. Right Arm Assembly
6. Seat Slat
7. Back Slat
8. Hanging Rail Members
9. Hardware placeholder geometry if desired

### Naming Plan
- Base Frame
- Front Rail
- Rear Rail
- Left Arm Assembly
- Right Arm Assembly
- Seat Slat 01
- Back Slat 01
- Hanging Rail Front
- Hanging Rail Rear

### Scene Plan
- assembled perspective
- top orthographic
- front orthographic
- side orthographic
- exploded assembly
- hanging-point detail

### Export Targets
- scene-based plan references
- printable view set
- cut-list-friendly component naming

### High-Level MCP Action Sequence
- create primary frame geometry
- convert repeated members into components
- assemble named side and rail structures
- create scenes aligned to plan-sheet needs
- confirm dimensions and labels match the design spec

---

## 4. Plan rendering output (plan-renderer-skill)

### View List
- top view
- front view
- side view
- exploded assembly view
- hanging-point detail view
- slat spacing / arm detail if needed

### Dimension List by View
- top view: overall width, overall depth, interior mattress-fit width/depth
- front view: overall height, arm height, hanger location spacing
- side view: seat height, back angle, hanger location relative to frame
- detail view: hanger reinforcement dimensions and fastener placement assumptions

### Labeling Rules
- keep labels short and matched to component names
- label repeated slats only where it improves clarity
- use the same names as the SketchUp component list and cut list

### Exploded-View Instructions
- separate arms, rails, slats, and base frame clearly
- keep exploding distance readable, not dramatic
- show relation of hanging members to main frame

### Printable Sheet Layout Notes
- start with orthographic views
- place exploded view after overall views
- put safety-critical detail views near notes

---

## 5. Cut list output (cut-list-skill)

### Purchase List
- 2x4 pressure-treated stock for frame and main support members
- 1x4 pressure-treated stock for slats and lighter members
- exterior-rated structural screws / bolts
- hanging hardware appropriate to confirmed load and mounting method
- finish / sealing materials as needed

### Cut List by Stock Type
Example structure only; exact dimensions depend on confirmed final design:

#### 2x4 stock
- base long rails x2
- base end rails x2
- back uprights x2
- arm supports x4
- hanging rail members x2

#### 1x4 stock
- seat slats xN
- back slats xN
- optional arm trim / fascia xN

### Rip Plan
- likely minimal if standard 1x4 / 2x4 strategy is preserved
- add only if arm details or trim require nonstandard widths

### Waste Notes
- repeated slat sizing helps reduce waste
- standardizing arm members simplifies both layout and cuts

### Simplification Suggestions
- keep slats to one width
- keep left/right assemblies mirrored
- avoid decorative dimension changes that create one-off parts

---

## 6. Hardware list

- exterior-rated screws
- bolts / washers / nuts where structural hanger attachments require them
- chain or rope rated for outdoor suspended seating
- hangers / swing hardware rated for expected dynamic load

---

## 7. Final note

This example is intentionally compact. It demonstrates the output shape and coordination between the skills, not a stamped or production-verified plan.
