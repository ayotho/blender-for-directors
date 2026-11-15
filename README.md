# Blender for Directors

**Direct 3D scenes in Blender by talking to ChatGPT. You never have to learn Blender's buttons.**

You describe the shot like you would to a crew: "Wide shot, a small café at night, warm light from the window, camera slowly pushes in on the table." ChatGPT builds it inside Blender, checks its own work with a screenshot, and you give notes until it looks right.

```
  YOU (the director)
     │  "Push the camera in, make the light warmer"
     ▼
  ChatGPT desktop app
     │  (talks to Blender through a small free connector called MCP for Blender)
     ▼
  Blender  ──►  builds the scene, moves the camera, renders a frame
```

---

## What you need

| Thing | Cost | Notes |
|---|---|---|
| A Mac or Windows computer | - | Blender runs on your own machine |
| **Blender** | Free | [blender.org/download](https://www.blender.org/download/) |
| **ChatGPT desktop app** | Your ChatGPT plan | Must be the **desktop app**. ChatGPT in a web browser cannot reach Blender on your computer. |
| **MCP for Blender** | Free, open source | [github.com/ahujasid/mcp-for-blender](https://github.com/ahujasid/mcp-for-blender), the connector this kit uses |

Setup takes about 15 minutes, once.

---

## Setup, step by step

### Step 1. Install Blender
1. Go to [blender.org/download](https://www.blender.org/download/) and download it.
2. Install it like any other app.
3. Open it once, then close it. (This creates its settings folder.)

### Step 2. Install the ChatGPT desktop app
1. Download it from [chatgpt.com/download](https://chatgpt.com/download).
2. Sign in.

### Step 3. Run the one-line installer
This installs the connector and switches it on inside Blender.

**Mac:** open the **Terminal** app (press `Cmd + Space`, type `Terminal`, press Enter). Paste this and press Enter:
```
curl -LsSf https://www.mcp-for-blender.com/install.sh | sh
```

**Windows:** click Start, type `PowerShell`, open it. Paste this and press Enter:
```
irm https://www.mcp-for-blender.com/install.ps1 | iex
```

If it asks which apps to set up, pick **Codex** (that is the engine inside the ChatGPT desktop app).

> Windows blocked the script? Run these two lines instead, one at a time:
> ```
> winget install --id=astral-sh.uv -e
> uvx mcp-for-blender setup
> ```
> Close PowerShell and open a new one between the two lines.

### Step 4. Add Blender to the ChatGPT desktop app
Skip this if the installer said it set up Codex.

1. Open the ChatGPT desktop app → **Settings** → **MCP servers** → **Add server**.
2. Fill it in:
   - **Name:** `blender`
   - **Type:** `STDIO`
   - **Command:** `uvx`
   - **Arguments:** `mcp-for-blender`
3. **Save**, then press **Restart**.

### Step 5. Switch it on in Blender
1. Open Blender.
2. Top menu: **Edit → Preferences → Add-ons**. Search `MCP`. Make sure **Interface: MCP for Blender** is ticked.
3. Close Preferences. Hover your mouse over the big 3D area and press **N**. A side panel opens.
4. Click the **MCP for Blender** tab. If you see a **Start MCP Server** button, click it.

### Step 6. Test it
1. **Fully quit** the ChatGPT desktop app (Mac: `Cmd + Q`. Windows: right-click its icon by the clock → Quit) and open it again.
2. Keep Blender open.
3. In ChatGPT, type:
   > What objects are in my Blender scene?

If it answers "a Cube, a Camera and a Light", you're connected. 🎬

Then try:
> Delete the cube. Make a red sphere sitting on a grey floor, light it from the left, and show me a screenshot.

---

## Make ChatGPT a better Blender operator (recommended)

Paste the text in [`CHATGPT-INSTRUCTIONS.md`](CHATGPT-INSTRUCTIONS.md) into ChatGPT so it works the way a director needs: small steps, a screenshot after every change, plain words, and saving often.

- **Easiest:** create a ChatGPT **Project** called "Blender", open its **Instructions**, and paste it there. Every chat in that project follows it.
- **Using Codex skills:** copy the [`skill/`](skill/) folder to `~/.codex/skills/blender-director/`. It is the same guidance as a skill file.

---

## How to direct it

Read [`DIRECTING-GUIDE.md`](DIRECTING-GUIDE.md). Short version:

1. **One shot at a time.** Set, then lighting, then camera, then movement.
2. **Talk in film language.** "35mm lens, eye level, slow dolly in over 4 seconds" works better than "make it cool".
3. **Always ask for a screenshot** after each change, and give notes on what you see.
4. **Say "save the file"** every few steps.

Copy-paste prompts for common jobs are in [`PROMPTS.md`](PROMPTS.md).

---

## When something breaks

See [`TROUBLESHOOTING.md`](TROUBLESHOOTING.md). The three most common fixes:

| Problem | Fix |
|---|---|
| ChatGPT says it has no Blender tools | Blender must be open, and you must fully quit and reopen ChatGPT. |
| "Could not connect to Blender" | In Blender press **N** → **MCP for Blender** tab → **Start MCP Server**. |
| It did something weird | Press **Ctrl + Z** (Mac: **Cmd + Z**) in Blender to undo, then give a smaller instruction. |

---

## Safety, in plain words

- The connector lets ChatGPT run code inside Blender. That is how it builds things. **Save your file before big changes.**
- Everything runs on your own computer. Nothing is put on the internet.
- MCP for Blender sends a small anonymous usage count (no prompts, no scenes). To turn it off, see the [connector's README](https://github.com/ahujasid/mcp-for-blender#telemetry-control).
- This kit is a guide. The connector is made by [Siddharth Ahuja](https://github.com/ahujasid), not by Blender or OpenAI.

---

*Setup steps checked against the MCP for Blender README and OpenAI's Codex MCP docs, November 2026. App menus move: if a button has a different name, look for the closest match.*
