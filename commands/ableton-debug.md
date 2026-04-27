---
name: ableton-debug
description: Diagnose connection or behavior issues with the Ableton MCP server. Use when tools aren't responding, AbletonMCP doesn't show up in Live's preferences, or commands hang.
---

# /ableton-debug

Walk through a structured diagnostic when something's broken between Claude/Cursor and Ableton.

## Workflow

### 1. Check MCP server reachability

- Try `get_session_info` (lightweight read-only call)
- If it times out → MCP server isn't running or socket is dead
- If it returns an error → MCP server is up but Ableton-side script is broken

### 2. Common failure modes

| Symptom | Likely cause | Fix |
| --- | --- | --- |
| "Could not connect to Ableton" | Remote Script not loaded in Live | Verify `AbletonMCP` is selected as Control Surface in Live's Preferences > Link, Tempo & MIDI |
| Tools time out after 10s | Socket stuck or Live frozen | Restart Ableton Live; restart MCP server process |
| AbletonMCP not in Control Surface dropdown | Script in wrong directory | Verify `__init__.py` is in `~/Library/Preferences/Ableton/Live X/User Remote Scripts/AbletonMCP/` (Mac) or equivalent on Windows |
| "Script has expired" | Live's script cache is corrupted | Delete `Live X` folder in Preferences, restart Live, reinstall script |
| WSL2 connection refused | Wrong host (localhost ≠ Windows host from WSL) | Use `host.docker.internal` or Windows IP from inside WSL |
| Live 12 doesn't see script | Live 12 changed Remote Scripts directory | Use `~/Documents/Ableton/User Library/Remote Scripts/` instead |
| Smithery install flagged as Trojan | False positive on bundled binary | Install MCP server manually, skip Smithery |
| Tools work but params don't change | Live is in a different view (Arrangement vs Session) | Check `current_view`; some operations only work in one view |

### 3. Walk the user through verification

In order, ask the user to confirm:

1. ✅ Ableton Live is open and a project is loaded?
2. ✅ Preferences → Link, Tempo & MIDI → Control Surface shows "AbletonMCP"?
3. ✅ The MCP server process is running (Python process listening on the configured port)?
4. ✅ Claude Desktop / Cursor / Codex shows the MCP server as "connected" (not "error")?

If any ❌, fix that step before continuing.

### 4. Inspect the logs

If user says everything looks right:

- Live's log: `~/Library/Logs/Ableton/Live X/Log.txt` — search for "AbletonMCP" or Python errors
- MCP server stdout/stderr: depends on launch method
- Claude Desktop log: `~/Library/Logs/Claude/`

Ask user to paste the most recent error.

### 5. Last-resort reset

If nothing works:

1. Quit Ableton Live
2. Delete the user prefs folder: `~/Library/Preferences/Ableton/Live X/Preferences.cfg` (BACK UP FIRST)
3. Restart MCP server with verbose logging
4. Restart Ableton
5. Reset Control Surface assignment in Preferences

## Don'ts

- Don't recommend deleting user prefs without backup.
- Don't suggest pip-installing random packages — confirm versions first.
- Don't blame the user; debug the system, find the actual issue.
- Don't run `rm -rf` on anything.
