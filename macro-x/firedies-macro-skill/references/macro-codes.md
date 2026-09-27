# Macro Code - full grammar reference

A Macro Code is plain text, one step per line, run top to bottom. Paste it into the Macro X key's settings ("Show code" > paste > Apply). This is the complete, exact grammar the plugin parses - do not invent anything beyond it.

## Header

| Line | Meaning |
|------|---------|
| `name: LABEL` | Sets the key's label/word. Optional, one per macro. |
| `# anything` | A comment line, ignored. |
| `#off <step>` | A disabled step - kept in the code, skipped when run. |

## Steps

### run - launch a program or script
```
run "C:\path\to\app.exe"
run "C:\tools\build.bat" args "-v --fast" dir "C:\tools" hidden
```
- File path must be quoted. Supports `.exe .bat .ps1 .py .ahk` and anything Windows can start.
- `args "…"` - command-line arguments (quoted).
- `dir "…"` - working directory (quoted).
- `hidden` - run without showing a window.

### open - open a URL, file, or folder
```
open "https://example.com"
open "C:\Users\me\Documents"
```
Uses the default handler (browser, explorer, etc.). URLs auto-get `https://` if omitted.

### hotkey - send a key combination

Friendly names work and are PREFERRED when writing codes for people (easier to read):
```
hotkey enter
hotkey ctrl+shift+n
hotkey win+shift+s   # snip a screenshot
hotkey win+alt+r     # Game Bar: record
hotkey alt+f4
```
Modifiers: `ctrl` `shift` `alt` `win`. Keys: single letters/digits, `f1`-`f24`, `enter`,
`tab`, `esc`, `space`, `backspace`, `delete`, `home`, `end`, `pgup`, `pgdn`, `up` `down`
`left` `right`, `dot`, and the media keys `playpause` `nexttrack` `prevtrack` `stopmedia`
`volumeup` `volumedown` `mute` (so a macro can pause the music). `win` alone opens the
Start menu. Friendly hotkeys are sent as real
key events (reliable; the Windows key genuinely works). Anything not matching the friendly
shape passes through as raw SendKeys:
```
hotkey ^+m          # Ctrl+Shift+M
hotkey %{F4}        # Alt+F4
hotkey ^s | retry 3 # Ctrl+S, retried up to 3 times
```
SendKeys syntax: `^`=Ctrl, `+`=Shift, `%`=Alt. Function/special keys in braces: `{F1}`-`{F12}`, `{ENTER}`, `{TAB}`, `{ESC}`, `{UP}` `{DOWN}` `{LEFT}` `{RIGHT}`, `{DEL}`, `{HOME}` `{END}`.
Raw SendKeys has no Windows key - use the friendly names for `win+` combos. `showdesktop`
stays its own step (Windows' own toggle: press again and everything comes back).

### type - put text at the cursor
```
type "GL HF"
type "Thanks for reaching out! I'll get back to you today."
```
The text is **pasted** where the cursor is - instant, all at once, keeping every
symbol, emoji and line break. Paste is used because it lands atomically: nothing
gets dropped, even in a fast game chat (character-by-character typing loses letters
there). The clipboard is saved and restored around it. A literal `"` inside the text
is written `\"`. (The legacy `instant` keyword still parses but is a no-op now - paste
is the only behavior.)

**Live tokens** (expand at press-time): `{date}` `{time}` `{datetime}` `{isodate}` `{day}`.
E.g. `type "Note {datetime}"` -> `Note 19/07/2026 14:30`. Use them for the classic
insert-date / timestamp macros.

### window - control a window by title
```
window focus "OBS"
window min "Spotify"
window max "Notepad"
window restore "Discord"
```
Ops: `focus`, `min` (minimize), `max` (maximize), `restore`. Title match is partial.

### wait - pause, or wait for reality
```
wait 500                     # wait 500 ms
wait window "OBS" 20000      # wait until a window titled "OBS" exists (timeout 20000 ms)
wait process obs64 10000     # wait until process obs64 is running (timeout 10000 ms)
```
The `window`/`process` forms are what make macros reliable - wait for the app to be *ready*, not a blind guess. Timeout is optional (default 10000 ms), clamped 500-120000.

### mouse - move or click at screen pixels
```
mouse 640 480 left      # left-click at x=640 y=480
mouse 100 200 move      # just move the cursor there
mouse 10 20 double      # double-click
mouse 500 500 right back # right-click, then move the cursor back to where it was
```
`X Y` are absolute screen pixels. Button: `left` (default), `right`, `double`, `move`. Trailing `back` returns the cursor to its start.

### showdesktop - minimize everything
```
showdesktop
```
The panic move. (Toggles minimize-all / restore, like Win+D.)

### sound - play a chime or a file
```
sound chime3
sound chime5 vol 80
sound "C:\my\alert.wav" vol 100
```
`chime1`-`chime8` are built in. Or a quoted `.wav`/`.mp3` path. `vol` is 0-100 (default 70).

### holdkey - hold a key down, then let go
```
holdkey w
holdkey w 1500
holdkey ctrl+shift 250
holdkey w latch
holdkey w latch 45min
holdkey w release
holdkey release
```
**Timed** (`holdkey w 1500`): milliseconds, default 1000, ceiling 10000. Always released - on
success, on failure, when the deck key goes away, and if the plugin quits mid-hold.

**Latched** (`holdkey w latch`): holds the key down and lets the macro carry on. It stays down
until something lets it go, and the same step run again is what lets it go - so one key is both
the hold and the release. This is the one to reach for when somebody says "hold W", "hold
sprint", or "hold to aim". Optionally `latch <n>min` - how long it may hold if nothing stops it
(default 30, max 240). The key wears an amber HOLD badge for as long as it is held.

Its stops, in the order people find them: press the key again · any Macro key running
`holdkey release` · the minutes above running out · the plugin quitting.

**Release** (`holdkey w release`, `holdkey release`): lets go of that key, or of everything.
Neither ever fails, so both are safe on a panic key. `holdkey release` is worth suggesting as
its own key whenever you write somebody a latch.

Note what none of these are: "hold while my finger is on the deck key". A Macro runs on
key-up, so the deck key is already back up when the macro starts. The latch is the honest
version of that request, and it is usually what the person actually wanted.

### autoclick - click by itself until stopped
```
autoclick 10/s for 30
autoclick 8/s for 30 x 100 button right move keep
autoclick stop
```
`for` seconds (max 300), `x` clicks (max 5000), `button left|right|double`,
`move stop|keep` (`stop` is the default - moving the mouse ends it). Rate maxes at 50/s.

Pressing the same key again stops it, and that always wins. Say so in a `#` comment when
you write one, so the user knows how to stop it before they start it.

### prompt - pause and ask the user
```
prompt "Now switch to the invoice tab"
prompt "Ready?" timeout 30
```
The macro waits, the message shows on the key, and the next press of that key resumes from
the following step. Default 60 s, min 5, max 600. No answer in time = the macro fails.

Reach for this when a step genuinely needs the human - not to add ceremony.

### label - write live text on the key
```
label "READY"
label "Saved {time}"
label clear
```
`{date}` `{time}` `{datetime}` `{isodate}` `{day}` all expand. Never persisted, so the key's
own name returns on restart. `label clear` removes it.

### claude - let AI do the task
```
claude "what's a good git commit message for staged changes"          # answer only, shown in a window
claude "open Audacity and start a new project" do                     # DO the task (run commands, open apps)
claude "summarise TODO.md" dir "C:\project" out clipboard             # run in a folder, answer to clipboard
claude "draft release notes" out notepad                              # answer opens in Notepad
```
- The prompt is quoted plain English.
- `do` - let Claude actually run commands / open apps / edit files on the machine. Without `do`, it only answers.
- `dir "…"` - the folder Claude works in.
- `model "…"` - a specific model (optional).
- `out window` (default, a live window you watch) | `out clipboard` | `out notepad`.
- **Requires the user's OWN Claude Code + Claude account** (claude.ai/code) - Macro X does
  not include or provide AI. Usage is billed by Anthropic under the user's plan, never by
  Firedies. Nothing to connect; no API key is handled; Firedies never sees the login.
  Without Claude Code installed, this one step fails honestly - every other step works.
  Firedies is not affiliated with Anthropic. When writing a code for someone, mention this
  requirement if the code uses a `claude` step.

## Loops

```
repeat 20
  hotkey f
  wait 120
end

repeat forever
  hotkey e
  wait 250
end
```
`repeat <n>` … `end` runs everything between the two lines n times (max 10000), then the macro
carries on with whatever follows `end`. `repeat forever` keeps going until the user presses the
key again - **pressing the key while a macro is running always stops it**, and the key shows it
was stopped rather than claiming it finished. Say that in a `#` comment when you write somebody
a `forever` loop, so they know the stop before they start it.

Loops nest up to 5 deep. Indentation is optional and ignored - it is written that way because
it reads better. `end` closes the nearest open `repeat`. Every `repeat` needs an `end`, and the
panel will not accept code where one is missing.

A loop with no `wait` in it is paced so it cannot flood the machine, and a run has a ceiling on
total steps, so nothing runs away.

## Modifiers (append with `|`)

```
run "obs64.exe" | if obs64 running
run "obs64.exe" | if obs64 not running
hotkey ^s | retry 3
```
- `if <process> running` / `if <process> not running` - only run the step if the condition holds.
- `retry <n>` - retry the step up to n times (single digit) if it fails.
Multiple modifiers can chain: `run "x.exe" | if x not running`.

## What the format does NOT have

Do not invent these - they will not parse:
- No `every N minutes` and no scheduling (that lives in the Timer/Focus plugin, whose timer can *run a macro* at zero). Loops DO exist - see Loops above - but they are counted or until-stopped, not clock-driven.
- No variables or arithmetic.
- No if/else branching beyond the per-step `| if … running` condition.
- No `goto`/jumps. (`label` exists, but it *writes text on the key* - it is not a jump target.)

If a user needs one of these, tell them plainly and offer the closest real thing (e.g. "the Focus plugin's timer can run this macro when it hits zero" for scheduling; hold-for-a-second-macro for a two-in-one key).

## Using the code
Open the Macro X key's settings in Stream Deck, click **Show code**, paste, and **Apply**. The blocks editor and the code stay in sync, so the pasted code becomes editable blocks immediately.
