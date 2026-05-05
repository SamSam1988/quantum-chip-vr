# Marble build brief: Flying Photon VR on superconducting qubit chip

Build a mobile/Cardboard VR experience from `main_full_v16.gds`.

## Core concept
The viewer is a flying photon, visually about 5 microns wide, traveling over and through the navigable voids of a superconducting quantum chip.

## Coordinate system and scale
- Use microns as world units.
- Uploaded GDS bounding box is approximately 9950 µm x 9950 µm.
- Silicon chip: 500 µm thick. Top Si surface is z=0; silicon occupies z=-500..0.
- Maximum allowed height: z=10000 µm = 1 cm above chip.
- Lateral boundaries: chip edges.

## Fabrication layers
- Continuous base layer: 200 nm Nb over the chip.
- GDS layer 134: etched holes/openings in the Nb. These are gaps/openings, exposing the Si surface. Treat them as non-metal areas in the base Nb sheet.
- GDS layer 136: additional Nb, 130 nm thick, above base Nb.
- GDS layer 137: additional Nb, 130 nm thick, stacked above previous layers as appropriate.
- GDS layers 146 and 147: dielectric crossovers. Render as raised translucent dielectric bridge/crossover structures. First pass may use flat slabs; later pass should use rounded/arched crossover shapes with correct bridge approaches and collision mesh.
- GDS layer 131: unspecified; render as faint wireframe/auxiliary until clarified.

## Movement
Each frame, move the camera/viewer in the direction they are looking:

    speed_um_per_sec = height_above_chip_um / 30 + 3

Examples:
- At z=0: 3 µm/s.
- At z=10000 µm: 336.33 µm/s.

Looking down should reduce z and therefore slow the photon as it approaches the chip. Looking up should increase z and speed it up.

## HUD
Add a corner HUD visible in non-VR mode and, if possible, as a small fixed in-world panel in VR:
- velocity in µm/s
- x, y, z position in µm
- height above chip in µm
- current/nearby layer label if available

## Rendering language
- Silicon: matte dark gray substrate.
- Nb: cool metallic blue/silver.
- Etched openings: dark exposed Si, with visible edges.
- Added Nb 136/137: warmer metallic highlights so the user can distinguish them from the base layer.
- Dielectric crossovers 146/147: translucent cyan/purple raised structures.
- Include optional labels for probelines, resonators, Josephson junction regions if they can be inferred or manually annotated later.

## Version 2 targets
- Electric-field streamlines around CPW gaps and junctions.
- Traveling microwave waves along resonators/probelines.
- Photon packet visualization.
- Better collision detection for etched regions and crossover bridge clearance.
- Manual semantic labels for resonators, probelines, junctions, pads, and qubit islands.
