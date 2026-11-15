# Copy-paste prompts

Change the words in [brackets]. Send one prompt at a time and look at the screenshot before the next.

## Start of every session
```
Check the Blender scene and tell me in one line what's there. Then wait for my first note.
```

## Fresh start
```
Clear the scene except the camera and one light. Set 24 fps, 1920x1080, metres. Add a plain grey floor. Show me.
```

## Build a set (blocking)
```
Block out a [small café interior]: floor, two walls in an L, a [round table] in the middle with [two chairs]. Simple shapes only. Name each object. Show me from a wide angle.
```

## Place a person
```
Put a person stand-in (a 1.75 m tall capsule) [sitting at the table, facing the window]. Name it "Hero". Show me.
```
or, for a real model:
```
Search Sketchfab or Poly Haven for a [low-poly person sitting]. Import the best free one, scale it to 1.75 m, place it at Hero's position. Show me.
```

## Camera
```
Set up the camera: [medium shot] of Hero, [35mm] lens, [eye level], Hero on the [left third] of the frame. Show me through the camera.
```

## Light a mood
```
Light it like [golden hour]: warm low sun from [the window side], soft cool fill from the opposite side, slight haze. Show me through the camera.
```
Other moods to swap in: `night interior with one practical lamp`, `overcast and flat`, `neon night, magenta and cyan`, `harsh midday sun`.

## Sky and world
```
Add a free HDRI sky from Poly Haven that fits [sunset over a city]. Show me.
```

## Camera move
```
Animate the camera: [slow dolly in from wide to close-up] over [5] seconds at 24 fps, ease in and out. Then show me 4 frames from the move side by side (start, 1/3, 2/3, end).
```

## Depth of field
```
Turn on depth of field. Focus on Hero's face, background soft (f/2). Show me through the camera.
```

## Output
Still:
```
Render frame 1 through the camera with EEVEE at 1920x1080 and save it as [shot01_frame.png] next to the .blend file.
```
Video preview:
```
Render the animation with EEVEE as an MP4 (H.264), 1280x720, and save it as [shot01_previz.mp4] next to the .blend file. Tell me when it's done and where the file is.
```

## Save
```
Save the file as [shot01.blend] in my [Documents/Blender] folder.
```

## When it goes wrong
```
Undo your last change. Then tell me in one line what you were trying to do, and try a simpler way.
```
```
Stop. Take a screenshot, list every object in the scene, and tell me what looks wrong.
```
