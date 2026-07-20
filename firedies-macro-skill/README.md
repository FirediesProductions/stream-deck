# Firedies Macro - Claude Skill

Turn a plain-English wish into a **Firedies Macro Code** you can paste straight onto an Elgato Stream Deck key.

> "Make me a button that hides everything and mutes my mic" →
> ```
> name: PANIC
> hotkey ^+m
> showdesktop
> ```

[**Firedies Macro**](https://marketplace.elgato.com) is a Stream Deck plugin (Windows) that turns one key into a whole routine - launch apps, send hotkeys, type, click, control windows, wait for things to be ready, play sounds, and even hand a task to AI. Every macro is a **Macro Code**: a few lines of plain text you can copy, share, and paste. This skill teaches Claude to write them.

## What's in here

| File | What it is |
|------|-----------|
| `SKILL.md` | The skill itself - how Claude responds, the grammar in one screen, worked examples. |
| `references/macro-codes.md` | The complete, exact Macro Code grammar (every step, option, and modifier). |

## Install (Claude Code)

Copy this folder into your skills directory:

```
~/.claude/skills/firedies-macro/
```

Then just ask - *"write me a Firedies macro that opens OBS if it isn't running and brings it up"* - and Claude replies with a paste-ready code block.

## Use it

1. Ask Claude for a macro in plain English.
2. Copy the code block it gives you.
3. In Stream Deck, open your Firedies **Macro** key's settings, click **Show code**, paste, and **Apply**.

The key becomes the answer.

## License

MIT. Free to use, fork, and share. Firedies Productions is not affiliated with Elgato or Anthropic; "Stream Deck" and "Claude" are trademarks of their respective owners.
