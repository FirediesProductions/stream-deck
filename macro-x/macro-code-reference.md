# Macro Code - the full reference

A Macro Code is a macro written as plain text: **one line per step**, top to bottom. Paste a
code into the Macro X code box and it becomes the key's steps; the code box and the step
blocks are the same macro, live.

```
name: GL HF
hotkey enter
wait 15
type "gl hf"
hotkey enter
```

Anything in quotes may contain `\"` for a literal quote. Blank lines are ignored.

## The steps

### `name:` - the key's label
```
name: STUDIO
```
Not a step. It names the key. Show or hide it on the key face in settings.

### `open` - a file, folder, app, or site
```
open "https://mail.google.com"
open "C:\Users\you\Documents"
open "audacity"
```

### `run` - a script or program
```
run "C:\path\to\script.py"
run "C:\x\tool.exe" args "-fast" dir "C:\x"
run "C:\path\to\backup.bat" hidden
```
Runs `.exe` `.bat` `.cmd` `.ps1` `.py` `.ahk` and more. Options: `args "..."` (arguments),
`dir "..."` (working folder), `hidden` (no window). Python and AutoHotkey scripts use your
installed interpreter. The settings panel tells you honestly if one is missing.

### `hotkey` - press a shortcut
```
hotkey enter
hotkey ctrl+shift+n
hotkey win+shift+s      # snip a screenshot
hotkey win+alt+r        # Game Bar: record
hotkey alt+f4
```
**Friendly names:** `ctrl` `shift` `alt` `win` plus a key - `enter`, `tab`, `esc`,
`space`, `backspace`, `delete`, `home`, `end`, `pgup`, `pgdn`, arrow keys (`up` `down`
`left` `right`), `dot`, `f1`–`f24`, and the media keys `playpause` `nexttrack` `prevtrack`
`stopmedia` `volumeup` `volumedown` `mute` - so a macro can pause your music on its way to
doing something else. `win` alone opens the Start menu.

Friendly hotkeys are delivered as **real key events**: the modifiers are genuinely held
down, the key pressed, then released. That's why the Windows key works here (`win+e`,
`win+d`, `win+v`...) even though classic SendKeys never could. The settings panel has a
premade picker with the common ones.

Raw [SendKeys syntax](https://learn.microsoft.com/en-us/dotnet/api/system.windows.forms.sendkeys)
also works for anything exotic: `^+m` (Ctrl+Shift+M), `%{F10}` (Alt+F10). Anything that
doesn't match the friendly shape passes through untouched (no Windows key on that road).

### `type` - put text at the cursor
```
type "GL HF"
type "Thanks for reaching out! I'll get back to you today."
```
The text is **pasted** in wherever your cursor is, instantly and all at once, keeping
every symbol, emoji, and line break exactly. Paste is the reliable way to place text:
because it lands in one go, nothing gets dropped even in a fast game chat (which is
where character-by-character typing loses letters). Your clipboard is saved and put
back afterwards.

**Live tokens** - these expand to the real value the moment you press the key:

| Token | Becomes |
| --- | --- |
| `{date}` | today's date (your Windows format) |
| `{time}` | the current time, e.g. `14:30` |
| `{datetime}` | date + time together |
| `{isodate}` | `2026-07-19` (sortable, great for filenames) |
| `{day}` | the weekday, e.g. `Sunday` |

So `type "Note added {datetime}"` types `Note added 19/07/2026 14:30`. The classic
"insert today's date" macro, finally built in.

*(The old `instant` keyword still parses on existing codes - it's the only behavior
now, so you can drop it. A rare app that blocks Ctrl+V paste is the one place this
can't reach.)*

### `wait` - real waits, not guessed delays
```
wait 300                      milliseconds
wait window "OBS"             until a window exists (default timeout 10s)
wait window "OBS" 20000       ...with your own timeout in ms
wait process obs64            until a program is running
```
A wait that times out **fails the step honestly**: the key shows the red cross.

### `window` - control a window by title
```
window focus "OBS"
window min "Spotify"
window max "Notepad"
window restore "Discord"
```

### `mouse` - move and click
```
mouse 1520 830 left
mouse 960 540 double back
```
Buttons: `left` `right` `double` `move`. Add `back` to return the cursor afterwards.
Tip: in the settings panel, **Grab position** captures coordinates for you: hover where
you want for three seconds.

### `sound` - play a chime or your own file
```
sound chime3
sound "C:\my.wav" vol 80
```

### `showdesktop` - the panic button
```
showdesktop
```
Minimizes everything (press again in a fresh key restores). Uses Windows' own mechanism,
so it works even where sent keystrokes don't.

### `claude` - hand the job to AI
```
claude "tidy my desktop and empty the recycle bin" do
claude "what's my local IP" out clipboard
claude "set up my session" do model sonnet
```
Runs the Claude Code you're already signed into, with nothing to connect and no keys to paste.
Options: `do` (let it actually act - run commands, open apps, edit), `dir "C:\folder"`
(working folder), `model sonnet` (pick a model), `out window|clipboard|notepad` (where the
answer goes; `window` streams the work live).

**What this step needs (not included with Macro X):** your own **Claude account** and
**[Claude Code](https://claude.ai/code)** installed on your PC. Install it, run `claude`
once in a terminal to sign in, and the step finds it from then on. Claude usage is billed
by Anthropic under *your* plan (subscription or API). Firedies provides the button, not
the AI, and never sees your login. Without Claude Code this one step fails honestly (red
cross + message); every other step works without it.

## Per-step extras

Append after a `|` at the end of any line:

```
run "C:\obs\obs64.exe" | if obs64 not running
hotkey ctrl+s | retry 3
open "https://example.com" | if chrome running | retry 2
```

- `| if <process> running` / `| if <process> not running` - the step runs only when true
- `| retry <n>` - a failing step gets n more goes (for apps that load slowly)

## Comments

```
# a comment line - ignored
#off hotkey ctrl+s        a step kept but disabled
```

## Sharing rules of thumb

- **Name it** (`name: ...`) so the key labels itself when pasted.
- **Comment it** - a `#` line telling people what to change (paths, keybinds).
- **No secrets** - codes are plain text; never paste tokens, passwords, or private paths.
