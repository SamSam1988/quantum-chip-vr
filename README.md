# Flying Photon VR prototype for main_full_v16.gds

Open `index.html` from a local web server, not by double-clicking the file. Example:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000` on desktop, or host the folder and open it on a phone. Use the WebXR / Enter VR button for Cardboard-compatible viewing.

## Implemented
- Parsed uploaded GDS: `main_full_v16.gds`.
- Chip bounding box: 9950.0 µm x 9950.0 µm.
- Silicon substrate: 500 µm thick, top surface at z=0.
- Base Nb layer: 200 nm sheet, with layer 134 treated as etched openings in Nb.
- Layers 136 and 137: added Nb, each 130 nm.
- Layers 146 and 147: translucent raised dielectric crossover geometry.
- HUD: velocity meter and x/y/z position indicator.
- Flying rule: camera moves in look direction at `height / 30 + 3` µm/s.
- Boundaries: chip x/y edges, chip surface, 1 cm max height.

## Notes
- The crossover visual is a first approximation: translucent dielectric slabs above the Nb/added-metal layers. A later version should add bridge curvature, actual metal-over-dielectric stack order, collision geometry, and field/wave overlays.
- Layer 131 is rendered as a faint wireframe auxiliary/annotation layer because its role was not specified.
