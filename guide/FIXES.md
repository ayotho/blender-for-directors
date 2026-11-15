# Fixes (for the AI)

Work top to bottom. Give the director one simple step at a time. Don't show them error text.

| Symptom | Likely cause | Fix |
|---|---|---|
| No Blender tools in this chat | ChatGPT wasn't restarted, or it's ChatGPT web | Desktop app only. Ask them to fully quit and reopen ChatGPT (Mac **Command + Q**; Windows right-click icon near the clock → **Quit**), with Blender open. Check with `/mcp`. |
| "Could not connect to Blender" / connection refused | Blender closed, or connector not started | "Open Blender, press **N** over the middle area, click **MCP for Blender**, click **Start MCP Server**." |
| No **MCP for Blender** tab in Blender | Addon not installed/enabled | Run `uvx mcp-for-blender install-addon`, then **Edit → Preferences → Add-ons**, search MCP, tick it. Restart Blender. |
| `spawn uvx ENOENT` / uvx not found | The app can't find `uvx` | Get the full path (`which uvx` on Mac, `where uvx` on Windows) and use it as the **Command** in Settings → MCP servers. Windows alternative: command `cmd`, arguments `/c uvx mcp-for-blender`. Restart ChatGPT. |
| Windows blocked the installer | Script policy / Defender | `winget install --id=astral-sh.uv -e`, reopen PowerShell, `uvx mcp-for-blender setup`. |
| No **MCP servers** in ChatGPT settings | Old app version or plan without it | Update the app. If still missing, tell them plainly their ChatGPT plan or app doesn't support it yet. Don't improvise. |
| Install fails with Python errors | Wrong Python picked | Use arguments `--python 3.11 mcp-for-blender` and env `UV_PYTHON_PREFERENCE=only-managed`. Then `uv cache clean mcp-for-blender` and restart. |
| Time-outs or stops halfway | Request or script too big | Smaller steps, shorter scripts. |
| Something weird happened to the scene | Bad change | Undo (Blender **Ctrl/Command + Z**) or revert to last save. Then a simpler approach. |
| Two AI apps connected | Only one client should drive Blender | Quit Claude Desktop / Cursor / others. |
| Video export error about `FFMPEG` | Blender 5.x | See `BLENDER-CODE-NOTES.md`. |

Still stuck: read github.com/ahujasid/mcp-for-blender (README and Issues) with the exact error, then try the documented fix. If it needs something only the person can do, ask in one line.

## Safety

- The connector lets the AI run code in Blender. Save before big changes.
- Everything runs on their computer.
- The connector sends a small anonymous usage count by default (no prompts or scenes). To turn it off, set `DISABLE_TELEMETRY=true` in the server's environment.
