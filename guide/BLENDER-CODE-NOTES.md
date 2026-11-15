# Blender code notes (for the AI)

Read before writing any Blender Python through the `blender` tools.

## Check the version first

Run `import bpy; print(bpy.app.version_string)` once per session. Blender's Python API changes between major versions and older examples break. Write for the version you see.

## Blender 5.x gotchas

- **Video export:** set `scene.render.image_settings.media_type = 'VIDEO'` **before** `file_format = 'FFMPEG'`. Otherwise `'FFMPEG'` is not a valid value.
- **Animation data:** actions are layered. `action.fcurves` no longer exists. Use `action.layers[...].strips[...].channelbags[...].fcurves`, or better, set keyframes with `obj.keyframe_insert(data_path=..., frame=...)` and avoid touching F-curves directly.
- **Render engine name:** check `bpy.context.scene.render.engine` options on the running version (EEVEE has had several identifiers, e.g. `BLENDER_EEVEE_NEXT` in 4.2-4.x, `BLENDER_EEVEE` in others). Read the current value or the enum before setting it.

## Previz video export (adapt to version)

```python
import bpy, os
s = bpy.context.scene
s.render.resolution_x, s.render.resolution_y = 1280, 720
s.render.fps = 24
s.frame_start, s.frame_end = 1, 120          # 5 s at 24 fps
folder = bpy.path.abspath("//") or os.path.expanduser("~/Documents/Blender Shots/")
s.render.filepath = os.path.join(folder, "shot01_previz")
im = s.render.image_settings
if hasattr(im, "media_type"):                 # Blender 5.x
    im.media_type = 'VIDEO'
im.file_format = 'FFMPEG'
s.render.ffmpeg.format = 'MPEG4'
s.render.ffmpeg.codec = 'H264'
bpy.ops.render.render(animation=True)
```

## First-frame still

```python
import bpy, os
s = bpy.context.scene
s.frame_set(s.frame_start)
im = s.render.image_settings
if hasattr(im, "media_type"):
    im.media_type = 'IMAGE'
im.file_format = 'PNG'
s.render.filepath = os.path.join(bpy.path.abspath("//") or os.path.expanduser("~/Documents/Blender Shots/"), "shot01_frame1.png")
bpy.ops.render.render(write_still=True)
```

## Habits

- Save the .blend before long or destructive scripts (`bpy.ops.wm.save_as_mainfile(filepath=...)`). Unsaved files have no `//` folder; save first so exports land next to it.
- Split long scripts into short ones. Long single calls time out.
- Name every object you create (`obj.name = "Hero"`). The director will refer to things by name.
- After rendering, confirm the file exists and is not empty before reporting.
- Keep EEVEE for previews. Cycles takes minutes per frame.
