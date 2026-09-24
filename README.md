# First-Person Architectural Explorer

A complete, ready-to-play first-person controller for the provided `bar_end.fbx` environment.

## Features

- **First-person camera** at realistic eye height (~1.65 m)
- **WASD** movement with smooth acceleration / deceleration
- **Mouse look** with pointer lock
- **Space** = jump, **Shift** = sprint
- **ESC** releases pointer lock / pauses controls
- **Mobile**: virtual joystick + touch look + on-screen Jump/Sprint buttons
- **Capsule-shaped** player collider
- **Trimesh collision** generated from the actual FBX geometry (walls, furniture, counters, stairs, etc.)
- Gravity, ground detection, and soft step-climbing for stairs / small thresholds
- Head-bob (subtle)
- Automatic spawn placement on the main floor
- Original materials, textures and lighting of the FBX are preserved

## How to run

Any static file server works:

```bash
# Python
python3 -m http.server 8080

# or Node
npx serve .
```

Then open `http://localhost:8080` in a modern browser.

Click the canvas to lock the mouse and start exploring.

## Controls

| Desktop              | Mobile                  |
|----------------------|-------------------------|
| WASD                 | Left virtual joystick   |
| Mouse                | Right-side swipe        |
| Space                | JUMP button             |
| Shift                | SPRINT button           |
| ESC                  | (tap outside)           |

## Technical notes

- Three.js r169 + Cannon-es for physics
- Collision bodies are static `CANNON.Trimesh` derived from every mesh in the FBX
- Player uses a vertical cylinder + end spheres (capsule approximation) with `fixedRotation`
- Grounding and stair assist use Three.js raycasts against the visual meshes for reliability
- No enemies, weapons, inventory or objectives – pure peaceful exploration

## Files

- `index.html` – UI + mobile controls + import map
- `main.js` – scene, loader, physics, controller
- `bar_end.fbx` – the environment (unchanged)
