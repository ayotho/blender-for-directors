# Previz for AI video (for the AI)

Why this kit exists. AI video models render beautifully but direct badly: they don't hold a fixed camera, stable geometry or space across shots, so text alone gives unpredictable camera moves and layout. Blender gives them what they can't make up: exact camera movement, blocking and timing. **Blender does the directing. The AI video tool does the beauty.**

Works with any AI video tool that takes an image and/or a video reference (for example Kling, Veo, Runway, Seedance, Higgsfield, Luma). Check the tool's current upload options; they change often.

---

## The three inputs

| Input | What it locks | Where it comes from |
|---|---|---|
| **Character reference** | Face, identity, wardrobe | A photo or generated image of the character (the tool's character/reference feature) |
| **Environment image** | Location, light, mood | A generated image of the place, or a styled Blender frame |
| **Blender previz** | Camera move, timing, blocking | The video you render from Blender |

With character and place locked by images, the text prompt only has to describe **what happens**, not what things look like.

## What to export from Blender

When the director says the shot is ready:

1. **Previz video:** EEVEE, MP4 (H.264), 1280×720 (or 720×1280 vertical), 24 fps, the shot length they set. Save next to the .blend file as `<shot>_previz.mp4`.
2. **First frame:** PNG of frame 1 through the camera, `<shot>_frame1.png`. This becomes the composition reference / start frame.
3. Optional: last frame PNG if the tool supports start + end frames.

Check both files exist and play/open before telling them it's done. Some tools reject large reference videos; if an upload fails, re-export smaller (e.g. 854×480) or shorter.

Then tell the director, plainly:
> Done. You've got two files in your **Blender Shots** folder: a short video and a picture. Upload both to your AI video tool, then paste the prompt I'll give you.

## Three ways to use the previz

| Pattern | Use when | How |
|---|---|---|
| **Start frame** | Composition matters most | Restyle `frame1.png` with an image model into the final look, use it as the video's first frame |
| **Motion reference** | Camera move and action matter most | Upload `previz.mp4` as the motion / video reference |
| **Both** | Best control, if the tool allows | Styled start frame + previz as motion reference |

Prompt line for restyling the first frame (image model):
```
Use the provided image as the composition and pose reference. Keep the composition, camera position, framing and character pose exactly the same. Restyle it as: [look].
```

Prompt line when feeding the previz as motion reference:
```
Follow the camera movement, timing and character actions from the reference video.
```

## Writing the video prompt

Order: **Camera → Subject → Action → Light/mood → Sound**

Rules:
1. **Start with the camera.** "Slow dolly in." It sets the space at once.
2. **Name the subject in the first sentence.** Don't open with background.
3. **Physical actions, not feelings.** "Tears run down her cheek", not "she's sad".
4. **20 to 50 words.** Longer prompts get ignored.
5. **Film terms:** tracking shot, dolly, pan, static tripod, drone flyover, handheld.
6. **No contradictions.** Not "extreme close-up" and "full body" together.

Example:
```
Slow dolly in at eye level toward a woman sitting alone at a café table by a rain-streaked window. She lifts her cup, pauses, looks out. Warm lamp light inside, cold blue street outside. Soft rain, low café chatter. 35mm, shallow depth of field.
```

Write the prompt for them from the shot you built together. They copy and paste it.

## Keep blockouts rough

- No finished models, materials or lighting needed.
- Cubes and capsules as stand-ins are enough; the video model keeps the choreography.
- Too much detail confuses the video model. Clean, simple blocking wins.

## Look development (only if they ask to match a look)

When they want a specific look (from a reference image or film) on a locked shot:

1. Treat geometry, blocking, framing and camera move as **locked**. Only appearance is open.
2. Name the rendering approach (photoreal, clay, cel-shaded, painterly).
3. Break the reference into: **Materials → Colour → Lighting (incl. haze) → Camera & lens → Post (grain, bloom, grade)**.
4. For each: what you see, the likely cause, the setting you'll try. Lens and lighting guesses are guesses; say so.
5. Test on one frame, compare side by side with the reference, adjust. Check depth and edges as well as colour: haze, focus and light can change how the space reads.
6. Note: changing focal length can change framing. Changing the camera position changes perspective. Ask before touching either on a locked shot.

---

Sources for the method: Flick, "Blender for AI Filmmaking: The 2026 Guide" (flick.art); community workflows on r/aifilmmaking and r/comfyui; Kling 3.0 prompt guidance. Synthesised and generalised for any tool.
