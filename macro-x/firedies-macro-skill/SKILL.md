---
name: firedies-macro-x
description: Write Macro Codes - the plain-text automation format for Macro X, the free Firedies plugin for Elgato Stream Deck. Use whenever someone wants to create a Stream Deck macro, automate keypresses / app launches / window control / mouse clicks / typed text, build a one-button routine, or asks for a "Macro X macro", a "macro code", or "a macro that does X". Outputs a paste-ready code block the user drops straight into the plugin's code box.
---

# Macro X - write a macro from a plain-English wish

The **Macro X** plugin (Elgato Stream Deck, Windows) turns one key into a whole routine. Every macro is a **Macro Code**: a few lines of plain text. This skill turns a plain-English request into a valid Macro Code the user can paste straight into the plugin.

## How to respond

1. Read what the user wants the key to do.
2. Write a Macro Code using ONLY the grammar in `references/macro-codes.md` (never invent verbs or options).
3. Put it in a fenced code block so it's one-click copyable.
4. Give the key a short `name:` (it becomes the label on the key).
5. In one line, tell them how to use it: **open the Macro key's settings in Stream Deck, click "Show code", paste, and Apply.**
6. If a path/app/keybind is user-specific (an install path, a Discord mute shortcut), leave a clearly-marked placeholder and say what to swap.

Keep it tight. One code block, one line of instruction, one line of "swap this if…". No lecture.

## The grammar in one screen

One step per line, top to bottom. `name:` sets the key label. Full reference in `references/macro-codes.md`.

```
name: LABEL
run "C:\path\app.exe" [args "…"] [dir "…"] [hidden]   # launch a program / script (.exe .bat .ps1 .py .ahk)
open "https://site.com"                                # open a URL, file, or folder
hotkey ^+m                                             # send keys: ^=Ctrl +=Shift %=Alt, {F1} {ENTER} {TAB}
type "some text"                                       # type text where the cursor is
window focus "OBS"                                     # focus / min / max / restore a window by title
wait 500                                               # wait milliseconds
wait window "OBS" 20000                                # wait until a window exists (timeout ms)
wait process obs64 10000                               # wait until a process is running
mouse 640 480 left                                     # move / click at screen pixels: left|right|double|move [back]
showdesktop                                            # minimize everything (panic)
sound chime3 vol 80                                    # play a built-in chime (chime1-8) or "C:\my.wav"
holdkey w 1500                                         # hold a key or combo down, then always let go (max 10000 ms)
autoclick 10/s for 30                                  # click by itself; the same key pressed again stops it
prompt "Switch to the invoice tab"                     # pause and ask; the next press of the key carries on
label "READY {time}"                                   # write live text on the key (label clear takes it off)
claude "open Audacity and start a new project" do      # let Claude DO the task on the user's own machine
```

**Modifiers, appended after a step with `|`:**
```
run "obs64.exe" | if obs64 not running                 # only run if a process is (not) running
hotkey ^s | retry 3                                    # retry up to N times if it fails
#off wait 500                                          # a disabled step (kept, skipped)
# any line starting with # is a comment
```

## Worked examples

**"A panic button - mute my mic and hide everything"**
```
name: PANIC
hotkey ^+m
showdesktop
```
> Set `Ctrl+Shift+M` as your mic-mute keybind first (Discord: Settings > Keybinds).

**"Open OBS if it isn't already, then bring it up"**
```
name: LIVE
run "C:\Program Files\obs-studio\bin\64bit\obs64.exe" | if obs64 not running
wait window "OBS" 20000
window focus "OBS"
```

**"Start my workday - open mail and calendar"**
```
name: WORK
open "https://mail.google.com"
wait 500
open "https://calendar.google.com"
```

**"A button that asks AI to open Audacity and set up a recording"**
```
name: REC
claude "Open Audacity, create a new project, and arm a mono track for recording" do
```
> The `do` word lets Claude actually run it. Needs Claude Code installed (claude.com/code); it uses the login you're already signed into.

## The one rule that matters

Only emit steps and options that exist in `references/macro-codes.md`. If the user asks for something the format can't do (a loop, a variable, "every 5 minutes"), say so plainly and offer the closest real thing - don't invent syntax that won't parse. The plugin shows a green tick when a macro runs clean and the exact failed step number when it doesn't, so a wrong guess fails loudly on their deck.
