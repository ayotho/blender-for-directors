# Troubleshooting

Go top to bottom. Most problems are fixed by the first two rows.

| What you see | What to do |
|---|---|
| ChatGPT says it doesn't have Blender tools, or doesn't mention Blender | 1. Open Blender first. 2. **Fully quit** ChatGPT (Mac: Cmd+Q. Windows: right-click its icon by the clock → Quit) and reopen it. 3. In the ChatGPT chat box, type `/mcp` and check `blender` is listed. |
| "Could not connect to Blender" / connection refused | In Blender, hover over the 3D area, press **N**, open the **MCP for Blender** tab, click **Start MCP Server**. |
| No **MCP for Blender** tab in Blender | Edit → Preferences → Add-ons → search `MCP` → tick **Interface: MCP for Blender**. If it's not in the list, run `uvx mcp-for-blender install-addon` in Terminal/PowerShell, then restart Blender. |
| `spawn uvx ENOENT` or "command not found: uvx" | The app can't find the `uvx` tool. In Terminal run `which uvx` (Mac) or in PowerShell `where uvx` (Windows). Copy the full path it prints (like `/opt/homebrew/bin/uvx` or `C:\Users\you\.local\bin\uvx.exe`) and use it as the **Command** in ChatGPT's MCP server settings. Restart ChatGPT. |
| Windows Defender blocked the installer | Run `winget install --id=astral-sh.uv -e`, close and reopen PowerShell, then run `uvx mcp-for-blender setup`. |
| No **MCP servers** option in ChatGPT settings | Update the ChatGPT desktop app. You must use the **desktop app**, not chatgpt.com in a browser. |
| It times out or stops halfway | Ask for smaller steps. "Do only the floor and walls first." |
| It did something strange to the scene | Ctrl+Z in Blender (Mac Cmd+Z), or ask "undo your last change". Save more often. |
| Install fails with Python errors | In ChatGPT's MCP server settings set **Arguments** to `--python 3.11 mcp-for-blender`. Then run `uv cache clean mcp-for-blender` in Terminal and restart ChatGPT. |
| Two AI apps fighting over Blender | Only one AI app should be connected to Blender at a time. Quit the others (Claude Desktop, Cursor and so on). |

Still stuck? Check the issues page of the connector: [github.com/ahujasid/mcp-for-blender/issues](https://github.com/ahujasid/mcp-for-blender/issues), or ask ChatGPT (with web search) to read that page and your error message.
