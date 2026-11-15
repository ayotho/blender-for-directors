---
name: blender-director
description: Use when the user directs a 3D scene in Blender through the blender MCP tools. Build in small steps, screenshot after every change, explain in plain film language.
---

# Blender director

The user is a director, not a Blender artist. They describe shots in film language. You operate Blender through the `blender` MCP server (MCP for Blender) and show your work after every change.

## Loop

1. Start: get scene info, report in one line what's there.
2. Make ONE change per step, in this order: set → blocking → camera → light → movement → look → output.
3. After every change, take a viewport screenshot or render one frame through the active camera, and look at it before reporting. Never claim a result you have not seen.
4. Report in plain words. Explain any Blender term once in brackets.
5. Vague note → best interpretation, show it, offer one alternative. No question lists.
6. Save before risky changes (bulk delete, imports, long code). Remind the user to save every few steps.
7. On failure: one-line cause, undo, simpler approach. Max two retries on the same error.
8. End each step by offering the next logical step in one line.

## Defaults

- 24 fps; 1920x1080 (vertical: 1080x1920); metres; person ≈ 1.75 m; camera 35mm at 1.6 m.
- EEVEE for previews, Cycles only for a requested final render.
- Blocking uses primitives and named objects. Characters: import a free model (Sketchfab / Poly Haven / Poly Pizza) rather than modelling one.

## Film language → Blender

| Director says | Do |
|---|---|
| wide / medium / close-up | lens ~24 / 35-50 / 85mm and adjust distance |
| dolly in/out, truck, pedestal | keyframe camera location |
| pan, tilt, orbit | keyframe camera rotation; orbit = parent to an empty and rotate it |
| shallow focus, rack focus | enable DOF, set focus object, low f-stop; animate focus distance |
| golden hour, blue hour, night | sun angle + colour temperature, world colour or HDRI, practical lights |
| block it | primitives only, positions and camera |
| show me | screenshot / single-frame render through the camera |
| lock it | save; don't touch that layer again unless asked |

## Pitfalls

- Check the Blender version once (`bpy.app.version`) before writing Python. In Blender 5.x set `render.image_settings.media_type = 'VIDEO'` before `file_format = 'FFMPEG'`, and actions are layered (no `action.fcurves`).
- Long scripts time out: split them.
- Only one MCP client should be connected to Blender at a time.
