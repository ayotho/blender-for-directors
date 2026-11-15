# Setup (for the AI)

Goal: Blender open, the connector switched on, and ChatGPT able to see the Blender scene. Follow the talk rules in `AGENTS.md`: one step per message, plain words, a check at the end of each.

Sources checked November 2026: MCP for Blender README (github.com/ahujasid/mcp-for-blender) and OpenAI's Codex MCP docs (developers.openai.com/codex/mcp). App menus change. If a button name differs, ask for a screenshot and find the closest match.

---

## What must be true

| Need | Why |
|---|---|
| Mac or Windows computer | Blender runs on their machine |
| **ChatGPT desktop app** (chatgpt.com/download) | Only the desktop app can connect to programs on their computer. ChatGPT on the web or phone **cannot** control Blender. |
| A ChatGPT plan that shows **Settings → MCP servers** in the desktop app | If that menu is missing after updating, their plan may not include it. Tell them plainly and stop. Don't guess workarounds. |
| Blender 3.0 or newer (free, blender.org) | Prefer the current release |

**If they're on ChatGPT web or phone right now:** you're the guide only. Walk them through Part A (desktop app), then tell them: "Now open the ChatGPT app on your computer and send the same message again." Continue setup from inside the desktop app.

---

## Part A. Get the apps (person does this)

A1. ChatGPT desktop app
> Go to **chatgpt.com/download**, download the app for your computer, open it and sign in. Tell me when you're in.

A2. Blender
> Go to **blender.org/download** and press the big blue **Download** button. Install it like any app, open it once, then close it. Tell me when that's done.

(Mac: drag Blender into Applications. Windows: run the installer, keep pressing **Next**.)

---

## Part B. Install the connector

**If you can run commands yourself, run these yourself** and ask them only to click **Approve**. Otherwise give them one line at a time.

### Mac
Opening the typing app:
> Press **Command + Space**, type **Terminal**, press **Enter**. A window with text opens. That's it.

Command (copy-paste):
```
curl -LsSf https://www.mcp-for-blender.com/install.sh | sh
```

### Windows
Opening the typing app:
> Click **Start**, type **PowerShell**, press **Enter**.

Command:
```
irm https://www.mcp-for-blender.com/install.ps1 | iex
```

If Windows blocks it, use these two lines instead. Close and reopen PowerShell between them:
```
winget install --id=astral-sh.uv -e
```
```
uvx mcp-for-blender setup
```

### What the installer does
It installs the `uv` tool, offers to set up AI apps it finds, and installs and enables the Blender addon. If it lists apps to set up, choose **Codex** (that's what the ChatGPT desktop app uses; they share `~/.codex/config.toml`). If it asks questions, tell the person exactly which option to pick in one line.

---

## Part C. Add Blender to ChatGPT

Skip if the installer said it set up Codex. Check first: type `/mcp` in the ChatGPT composer, or look in **Settings → MCP servers** for `blender`.

Person-facing steps (one per message):
1. "Open **Settings** in the ChatGPT app, then **MCP servers**."
2. "Press **Add server**."
3. "Fill it in like this:" then:
   - Name: `blender`
   - Type: **STDIO**
   - Command: `uvx`
   - Arguments: `mcp-for-blender`
4. "Press **Save**, then **Restart**."

If you can edit files yourself instead, the equivalent in `~/.codex/config.toml` is:
```toml
[mcp_servers.blender]
command = "uvx"
args = ["mcp-for-blender"]
```
Or run: `codex mcp add blender -- uvx mcp-for-blender`

---

## Part D. Switch it on in Blender

1. "Open **Blender**."
2. "At the top, click **Edit**, then **Preferences**, then **Add-ons**. Type **MCP** in the search box. Make sure **MCP for Blender** has a tick. Then close that window."
3. "Move your mouse over the big middle area and press the **N** key. A panel opens on the right. Click the tab called **MCP for Blender**. If you see **Start MCP Server**, click it."

The addon normally starts by itself when Blender opens, so steps 2 and 3 are often already done. Ask for a screenshot rather than making them check everything.

---

## Part E. Test

1. "Quit the ChatGPT app completely, then open it again." (Mac: **Command + Q**. Windows: right-click the ChatGPT icon near the clock and press **Quit**.)
2. "Keep Blender open."
3. Then, in a new chat, you call the Blender scene info tool yourself.

Pass = you can list the default scene (usually a Cube, a Camera and a Light). Tell them:
> You're connected. 🎬 Want to make your first shot?

Fail → `guide/FIXES.md`.

---

## Part F. Make it remember (optional, recommended)

So every future chat behaves the same way, tell them:
> One last thing. In ChatGPT, make a new **Project** called **Blender**. Open its **Instructions** and paste this in:

```
For Blender work, read and follow https://github.com/ayotho/blender-for-directors/blob/main/AGENTS.md and guide/OPERATING.md. I'm a director, not a Blender user: one step at a time, plain words, show me a screenshot after every change.
```

If skills are supported where you run, the same guidance is in `skill/SKILL.md` (copy the folder to `~/.codex/skills/blender-director/`).
