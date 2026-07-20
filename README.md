# Firedies - Stream Deck Series

Plugins for the Elgato Stream Deck that look hand-made and never lie about their own state.
Built by [Firedies Productions](https://firedies.com), Oxford.

## The series

| Plugin | What it is | Price | Docs |
|---|---|---|---|
| **Macro X** | One key that does many things: launch, hotkeys, type, click, wait, AI. The key becomes the answer. | Free | [`macro-x/`](macro-x/) |
| **System Meters** | CPU · RAM · GPU · VRAM · Disk, live every second. No drivers, no admin. | Free | *soon* |
| **Ping** | Live latency to your game server, with *detect your server* and a speed test. | TBD | *soon* |
| **Focus** | Pomodoro, timer, stopwatch, and a clock & calendar that puts your next meeting on a key. | TBD | *soon* |
| **Rank Showcase** | Your rank, league, or level, live on a key. | TBD | *soon* |

All plugins: Windows 10/11, Stream Deck 6.5+. Find them on the
[Elgato Marketplace](https://marketplace.elgato.com) under **Firedies Productions**.

> **The house rule: the face never lies.** A tick means it ran. A red cross tells you which
> step failed. A meter shows the real number. If we can't know something, the key says so.

## Repository layout

Each plugin lives in its own folder: its manual, its reference, its presets.

```
stream-deck/
├─ macro-x/                 the macro key (documented)
│  ├─ README.md             the manual
│  ├─ macro-code-reference.md
│  ├─ write-with-ai.md      let any AI write your codes
│  └─ presets/              ready-made codes to paste
├─ firedies-macro-skill/    the Claude skill (MIT)
└─ CONTRIBUTING.md          how to share your codes
```

More packages get their own folder as their docs land.

## Macro X

- **[The manual](macro-x/README.md)** - everything the key does, in plain words
- **[Macro Code reference](macro-x/macro-code-reference.md)** - the full grammar, every verb and option
- **[Presets](macro-x/presets/)** - ready-made codes to paste and make yours

## Share your codes

Every macro is a few lines of plain text, a **Macro Code**. Copy it, post it, paste someone
else's and it just applies.

**[→ Discussions](../../discussions)** is the trading post: share what you built, grab what
others made. The best community codes get promoted into [`macro-x/presets/`](macro-x/presets/)
with credit. See [CONTRIBUTING.md](CONTRIBUTING.md) for the two-minute guide.

## Let any AI write your macros

A Macro Code is just plain text, so any assistant can write one.

- **Any AI** (ChatGPT, Gemini, Claude, or a local model) - open
  **[macro-x/write-with-ai.md](macro-x/write-with-ai.md)**, paste the prompt into your
  assistant, and describe what you want. It replies with a paste-ready code.
- **Claude Code** - the [`firedies-macro-skill/`](firedies-macro-skill/) (MIT) teaches Claude
  to write Macro Codes automatically. Point Claude at it and ask.
- **Built in** - Macro X also has an **Ask Claude** step: describe a job in plain words and
  Claude Code does it on your machine.

---

*Docs © Firedies Productions. The Claude skill is MIT. Not affiliated with Elgato or Anthropic.*
