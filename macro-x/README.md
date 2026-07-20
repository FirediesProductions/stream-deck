# Macro X

**One key. Every job.**

Macro X is the macro key from Firedies Productions, part of the Firedies Toolkit for
Elgato Stream Deck. It launches your apps and scripts, sends your shortcuts, and - the part
nobody else does - the key itself tells you the truth: a progress bar while it runs, a green
tick when it worked, a red cross with the exact step that failed when it didn't.

Nothing is faked. Nothing leaves your PC.

- **[Macro Code reference](macro-code-reference.md)** - the full grammar
- **[Presets](presets/)** - ready-made codes to paste
- **[Share your codes →](../../../discussions)** - the trading post

## Quick start

1. Drag **Macro** (Firedies Toolkit) onto any key.
2. Press it. Every window minimises - a fresh Macro key is the classic panic button out of
   the box. Press again and your windows come back.
3. Open the key's settings and make it yours: a name, your own picture, your own steps.

## The face

- **Your image** - PNG, JPG, SVG, or an **animated GIF** (it really animates on the key).
  Size and position sliders included. No image? You get the Firedies mark, tintable to any
  colour.
- **The name is yours to show or not** - keys stay clean by default. (A panic button doesn't
  need PANIC written on it.)
- **While running** - the key dims, a progress bar fills, and a counter shows which step
  it's on (2/4).
- **Green tick** - every step ran. **Red cross + STEP 3** - it stopped at step 3, and that's
  the honest truth, not a guess.

## Steps

A macro is a list of steps that run top to bottom. Each step is set up with dropdowns and
fields - no code needed.

| Step | What it does |
|---|---|
| **Run script / app** | Opens a program or runs a script: `.exe` `.ps1` `.py` `.ahk` `.bat` and more. Can run hidden. If Python or AutoHotkey isn't installed, the settings say so up front. |
| **Open** | Opens a file, folder, or web address. |
| **Hotkey / type text** | Presses a shortcut (`enter`, `ctrl+shift+n`) or types out saved text wherever your cursor is. |
| **Mouse click** | Moves the mouse to a screen spot and clicks. Press **Grab position**, hover where you want for 3 seconds, and the spot is captured. Tick "put the mouse back" and your cursor returns afterwards. |
| **Window** | Focuses, minimises, maximises, or restores a window by its title. |
| **Wait** | Waits a fixed time - or **until a window exists** or **until a program is running**. Real waits instead of guessed delays, with a timeout that fails honestly. |
| **Show desktop (panic)** | Minimises everything; press again to bring it all back. Works even where sent keystrokes don't. |
| **Ask Claude** | Describe a job in plain words and Claude Code does it on your machine - your login, your rules, a visible window so you watch it work. Needs your own Claude account + [Claude Code](https://claude.ai/code) installed (not included - see below). |

Every step can also have a **condition** - run only if a certain program is (or isn't)
running - and a **retry** for apps that load slowly.

> **Ask Claude - bring your own Claude.** Macro X does not include AI. The Claude step
> drives the **Claude Code** you install and sign into yourself (claude.ai/code); usage is
> billed by Anthropic under your plan, never by Firedies, and we never see your login.
> Without it, that one step fails honestly - everything else works fine.

## Macro Codes - share your macros as text

Every macro can be copied as plain text and pasted anywhere: Discord, Reddit, a note to a
friend. Paste someone else's code and their macro becomes yours. The code box and the blocks
are the same macro, live - edit either and the other follows.

```
name: GL HF
hotkey enter
wait 150
type "gl hf"
hotkey enter
```

The full grammar - every verb, the friendly hotkey names, conditions, the AI step - lives in
the **[Macro Code reference](macro-code-reference.md)**.

## States - one key, more than one face

Switch **Key type** to *Cycles between states* and the key becomes a toggle (or a cycle of
up to six states). Each press runs the current state's steps, then the key wears the next
state's face - its own image, its own word. The classic: a Discord key that shows **MUTED**
after you mute and **LIVE** after you unmute.

For recording keys, tick **live timer** on a state - while it's active the key shows a
pulsing red dot with the time counting up.

Honesty note: for apps that can't be asked (Discord has no way to check), the key shows what
it believes from your presses. Where reality can be checked - is a program running, does a
window exist - Macro X checks reality.

## Hold action

Tick **Hold action** and holding the key for half a second runs a *different* macro than a
quick press. Mute on press, deafen on hold. Clip on press, screenshot on hold. One key, two
pockets.

## Honest limits

## What files work

| Where | Formats |
| --- | --- |
| **Key face** | PNG, JPG, SVG - or an **animated GIF** (it really animates on the key). No image? The Firedies mark, tintable to any colour, or a plain colour fill. |
| **Sounds** | Eight built-in chimes, or your own **WAV / MP3** - most audio Windows can play (M4A, FLAC) works too. |
| **Run step** | `.exe` `.bat` `.cmd` `.ps1` `.py` `.ahk` - the right runner is found for you, with an honest heads-up if Python or AutoHotkey is missing. Anything else opens with whatever Windows would use. |
| **Macro codes** | Plain text. Copy, paste anywhere, share freely. |

We'd rather tell you now than have you find out later:

- **Sent keystrokes can't reach everything.** Programs running as administrator ignore them,
  and many games block fake key presses (anti-cheat). Macro X is not a game-input tool.
  (Save That Clip still works in games because NVIDIA's overlay catches the hotkey, not the
  game.)
- **The Windows key works in friendly names** - `win+e`, `win+shift+s` (snip),
  `win+alt+r` (Game Bar record), `win` alone opens Start. There's a premade picker in
  the settings panel. (Show desktop stays its own step because it uses Windows' own
  toggle - press again and everything comes back.)
- **Toggles show believed state** for apps that can't be queried. Press the key, not the
  app, and the faces stay in sync.
- **Everything else runs locally.** No accounts, no tracking, nothing phones home. The only
  thing that ever leaves your PC is a prompt you wrote for a Claude step - from your machine
  to Anthropic, under your own account.

---

*Firedies Productions · Windows 10/11 · Stream Deck 6.5+*
