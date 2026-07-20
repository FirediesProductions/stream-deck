# Share your Macro Codes

The two-minute guide.

## Post it

Open **[Discussions](../../discussions)**, pick the **Show and tell** category, and paste
your code in a fenced block with a sentence on what it does:

````
My stream-starter - opens OBS, waits till it's really ready, arms the mic.

```
name: LIVE
run "C:\Program Files\obs-studio\bin\64bit\obs64.exe" | if obs64 not running
wait window "OBS" 20000
window focus "OBS"
```
````

## Make it good

- **Name it** - `name: ...` so the key labels itself when pasted.
- **Comment the change-me parts** - a `#` line pointing at paths or keybinds others must
  swap for their own.
- **No secrets, no personal paths** - codes are plain text for strangers to read. Nothing
  private, ever.
- Test it once from a fresh paste before posting.

## Promotion

Codes the community loves get promoted into [`macro-x/presets/`](macro-x/presets/) - with
your name on the credit line. That's the whole process; there's no paperwork.

## Bugs and ideas

Open an [Issue](../../issues) - say what you pressed, what you expected, and what the key
showed (the step number on the red cross is exactly the clue we need).
