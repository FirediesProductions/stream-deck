<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/phoenix-white.svg">
    <img src="assets/phoenix-black.svg" alt="Firedies Productions" width="76">
  </picture>
</p>

# Firedies - Stream Deck Series

Plugins for the Elgato Stream Deck that look hand-made and never lie about their own state.
Built by [Firedies Productions](https://firedies.productions), Oxford.

## The series

| Plugin | What it is | Price | Docs |
|---|---|---|---|
| **Macro X** | One key that does many things: launch, hotkeys, type, click, wait, AI. The key becomes the answer. | Free | [`macro-x/`](macro-x/) |
| **Metrics** | CPU · RAM · GPU · VRAM · Disk, live every second. No drivers, no admin. | Free | [`metrics/`](metrics/) |
| **Ping** | Live latency to your game server, with *detect your server* and a speed test. | $6.99 | [`ping/`](ping/) |
| **Focus** | Pomodoro, timer, stopwatch, and a clock & calendar that puts your next meeting on a key. | $7.99 | [`focus/`](focus/) |
| **Rank Showcase** | Your rank, league, or level, live on a key. | $4.99 | [`rank-showcase/`](rank-showcase/) |
| **Now Playing** | Album art, track and artist, live progress. The accent is sampled from the cover. | $5.99 | [`now-playing/`](now-playing/) |
| **Audio Meters** | Nine studio meters - level, VU, spectrum, spectrogram, waveform, scope, stereo, loudness, key - on keys and dials. | TBD | [`audio-meters/`](audio-meters/) |

All plugins: Windows 10/11 and macOS 13 or later, Stream Deck 6.9+. Find them on the
[Elgato Marketplace](https://marketplace.elgato.com) under **Firedies Productions**.

> **The house rule: the face never lies.** A tick means it ran. A red cross tells you which
> step failed. A meter shows the real number. If we can't know something, the key says so.

> **Works in your language.** Every label, name, and title renders in your own script - Japanese,
> Chinese, Korean, Arabic, Hindi, Thai, Hebrew, and more - not just Latin. 東京 · 서울 · مدريد · मुंबई.

## Repository layout

Each plugin lives in its own folder: its manual, its reference, its presets.

```
stream-deck/
├─ macro-x/                 the macro key (documented)
│  ├─ README.md             the manual
│  ├─ macro-code-reference.md
│  ├─ write-with-ai.md      let any AI write your codes
│  ├─ presets/              ready-made codes to paste
│  └─ firedies-macro-skill/ the Claude skill (MIT)
├─ metrics/                 the five meters (documented)
│  └─ README.md             the manual
├─ ping/                    live latency + speed test (documented)
│  └─ README.md             the manual
├─ focus/                   pomodoro, timer, stopwatch, calendar
│  └─ README.md             the manual
├─ rank-showcase/           your rank, live on a key
│  └─ README.md             the manual
├─ now-playing/             what is playing, with the cover
│  └─ README.md             the manual
├─ audio-meters/            nine studio meters on keys and dials
│  └─ README.md             the manual
├─ assets/                  the Firedies mark
└─ CONTRIBUTING.md          how to share your codes
```

More packages get their own folder as their docs land.

## Macro X

- **[The manual](macro-x/README.md)** - everything the key does, in plain words
- **[Macro Code reference](macro-x/macro-code-reference.md)** - the full grammar, every verb and option
- **[Presets](macro-x/presets/)** - ready-made codes to paste and make yours

## Metrics

- **[The manual](metrics/README.md)** - the five meters, the four styles, and exactly which
  Windows counter each number comes from

## Ping

- **[The manual](ping/README.md)** - the four actions, your server list, detect-my-server, and
  exactly what the latency number is measuring

## Focus

- **[The manual](focus/README.md)** - the six rhythms, what a pomodoro actually is if you have
  never used one, the three press depths, and the calendar setup

## Rank Showcase

- **[The manual](rank-showcase/README.md)** - the sixty badges, the seven live services, building
  your own ladder, and why the colour comes off the badge

## Now Playing

- **[The manual](now-playing/README.md)** - the three looks, the dial that does two jobs, and the
  one component foobar2000 needs for its progress bar

## Audio Meters

- **[The manual](audio-meters/README.md)** - the nine meters and each one's knob, the eight
  loudness readings, the four sources, and how to meter a DAW that runs on ASIO through your
  interface's loopback

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
- **Claude Code** - the [`firedies-macro-skill/`](macro-x/firedies-macro-skill/) (MIT) teaches Claude
  to write Macro Codes automatically. Point Claude at it and ask.
- **Built in** - Macro X also has an **Ask Claude** step: describe a job in plain words and
  Claude Code does it on your machine.

---

*Docs © Firedies Productions. The Claude skill is MIT. Not affiliated with Elgato or Anthropic.*
