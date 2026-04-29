---
name: wrapped
description: "Launch Claude Code Wrapped — an interactive Spotify Wrapped-style slideshow of your Claude Code usage stats in a new terminal window. Use when the user asks for their Claude Code usage summary, wants a year-in-review recap, mentions 'wrapped', or types /wrapped."
disable-model-invocation: true
allowed-tools: Bash
---

Run the following command exactly, then respond with only this message — nothing else:

**Claude Code Wrapped is opening in a new window** — use `SPACE` / `ENTER` to advance slides, `Q` to quit.

If the command fails, respond: "Wrapped failed to launch — make sure Python 3 is installed and try again."

```bash
python3 -c "
import subprocess, os, sys
script = '${CLAUDE_SKILL_DIR}/wrapped.py'
if not os.path.exists(script):
    print('Error: wrapped.py not found'); sys.exit(1)
kw = {'creationflags': subprocess.CREATE_NEW_CONSOLE} if os.name == 'nt' else {'start_new_session': True}
subprocess.Popen([sys.executable, script], **kw)
"
```
