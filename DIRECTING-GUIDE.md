# Directing Blender through ChatGPT

You don't need to know where the buttons are. You need to know what you want to see and how to give a clear note.

## The order to build a shot

Build in this order. Lock each layer before moving on, the way a set gets built before it gets lit.

```
1. SET        what's in the space (floor, walls, table, props)
2. BLOCKING   where people and objects stand (simple shapes are fine)
3. CAMERA     lens, height, angle, framing
4. LIGHT      time of day, key light, mood
5. MOVEMENT   camera moves and object animation, with timing
6. LOOK       colours, materials, fog, depth of field
7. OUTPUT     a still frame or a video file
```

Say "save" after each layer.

## A good note has three parts

**What + where + how much.**

| Weak note | Strong note |
|---|---|
| "Make it better" | "Move the camera lower, about knee height, so the table feels big." |
| "More dramatic" | "Turn off the fill light. One hard light from the right, 45 degrees, so half the face is in shadow." |
| "Camera move" | "Slow dolly in from 4 m to 1.5 m over 5 seconds, ease in and out." |
| "Nicer colours" | "Warm orange from the window, cool blue everywhere else." |

## Film words ChatGPT understands

- **Shot size:** extreme wide, wide, medium, medium close-up, close-up, extreme close-up
- **Lens:** 24mm (wide, distorts), 35mm (natural), 50mm (normal), 85mm (portrait, flat background)
- **Angle:** eye level, low angle, high angle, overhead / top-down, Dutch tilt
- **Moves:** dolly in/out, truck left/right, pedestal up/down, pan, tilt, orbit, crane
- **Light:** key, fill, rim/back light, practical (a lamp in shot), motivated (light that has a source), hard vs soft
- **Time of day:** golden hour, blue hour, midday, overcast, night interior
- **Focus:** shallow depth of field (blurry background), rack focus (focus shifts from A to B)

## Your loop

```
  You give a note ─► ChatGPT changes the scene ─► screenshot ─► you look
        ▲                                                         │
        └────────────────── next note ◄───────────────────────────┘
```

Rules that save hours:
- **One change per message** when you're fixing something. Five notes at once = five chances to break it.
- **Always look at the screenshot.** If it didn't show you one, ask: "show me through the camera".
- **Undo is your friend.** In Blender, Ctrl+Z (Mac Cmd+Z). Or tell ChatGPT "undo that".
- **Name things.** "Call the tall box 'Hero'". Then you can say "move Hero left".
- **Start a new chat** when a scene gets long and ChatGPT starts forgetting. Say: "Check the scene and tell me what's there" first.

## What it's great at, and what it isn't

| Great at | Harder |
|---|---|
| Blocking scenes and camera moves (previz) | Detailed human characters from scratch |
| Lighting setups and moods | Fine sculpting and organic shapes |
| Simple sets and props | Complex character animation (walk cycles) |
| Bringing in free models and HDRI skies (Poly Haven, Sketchfab) | Very large, heavy scenes |
| Rendering stills and short clips | Pixel-perfect matching of a reference |

For characters, ask it to **import a ready-made model** (Sketchfab or Poly Haven) instead of building one.

## Using Blender to direct AI video

Blender is a strong way to control AI video tools (Kling, Veo, Runway, Higgsfield):

1. Block the shot and camera move in Blender with simple shapes.
2. Render a short preview video and one still frame.
3. Feed the still (composition) and the preview (camera motion) into your AI video tool with your prompt.

The AI makes it beautiful. Blender makes it directed.
