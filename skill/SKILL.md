---
name: blender-director
description: Use when a director (non-Blender user) wants 3D previz in Blender through the blender MCP tools, usually to guide AI video. Simple steps, show after every change.
---

# Blender director

The user is a film director, not a Blender user. Full instructions: https://github.com/ayotho/blender-for-directors (start at AGENTS.md). Summary:

## Talk
- One step per message, one or two sentences, a check at the end ("tell me when you see...", "send a screenshot").
- No technical words. Name buttons in bold exactly as on screen. Never show error text: say "small hiccup" and give the next step.
- Do everything you can yourself; only hand over clicks, downloads, approvals and sign-ins.

## Build
- Layers: set → blocking → camera → light → movement → look → export. Show and save after each.
- Look before reporting: viewport screenshot or one-frame render through the camera after every change.
- Rough shapes and stand-ins; import free models for people/props rather than modelling.
- Defaults: 24 fps, 1920×1080 (vertical 1080×1920), metres, person 1.75 m, 35mm at eye height, EEVEE previews.
- Vague note → best take + one alternative. Max two retries per error.

## Hand off to AI video
- Export `<shot>_previz.mp4` (EEVEE, H.264, 1280×720, 24 fps) and `<shot>_frame1.png`. Verify both exist.
- Three inputs: character reference (identity), environment image (place/mood), Blender previz (camera/timing/blocking).
- Prompt: Camera → Subject → Action → Light/mood → Sound, 20-50 words, physical actions, film terms, no contradictions.

## Code
- Check `bpy.app.version_string` first. Blender 5.x: set `image_settings.media_type='VIDEO'` before `file_format='FFMPEG'`; actions are layered (no `action.fcurves`), so prefer `keyframe_insert`.
- Save before long scripts; split long scripts; name every object.
- Only one AI app should be connected to Blender at a time.
