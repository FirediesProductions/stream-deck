<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="../assets/phoenix-white.svg">
    <img src="../assets/phoenix-black.svg" alt="Firedies Productions" width="76">
  </picture>
</p>

# Metrics

**The real number. Every second.**

Metrics puts your machine on your deck - CPU, memory, graphics, video memory and disk - updating
once a second, calm green when it's idle and warming to red as it works. No drivers to install,
no administrator prompt, nothing to sign into.

It reads the same performance counters Task Manager reads, so the number on the key is the number
Windows itself would show you. If a reading can't be taken, the face says so instead of guessing.

Free, from Firedies Productions.

## Quick start

1. Drag **CPU** (under **Metrics**) onto any key or dial.
2. That's it. It's already live - there is nothing to configure to make it work.
3. Open its settings when you want a different style, your own colors, or a different thing to
   happen when you press it.

## The five

| Meter | What it reads |
|---|---|
| **CPU** | How hard the processor is working, as a percentage. The Task Manager number. |
| **RAM** | Memory in use - in gigabytes, or as a share of the whole. |
| **GPU** | Graphics load. Intel, AMD and NVIDIA alike, no vendor tool needed. |
| **VRAM** | Video memory in use, against your card's own total. |
| **Disk** | How busy a drive is - or, if you prefer, how full it is. |

Every one works as a **key** or as a **dial**, and you can put as many on a deck as you like.

## Four styles

| Style | What you get |
|---|---|
| **Color bar** | The number plus a bar underneath. Green when idle, red under load, glowing when pegged. |
| **B & W** | Monochrome. The bar brightens as the load climbs - the whole story, no color at all. |
| **Clean** | Just the number, large. Leave color on and the number itself carries the load. |
| **History** | The bar becomes a live graph of the last ~15 seconds. Oldest left, now right. |

The style is per face, so a CPU key and a CPU dial on the same deck can look completely different.

## Color that means something

Out of the box the color **is** the reading: calm green below **10%**, travelling through amber,
red above **90%**, and - on the color bar - a red glow at **97%** and over. Both percentages are
yours to move. Left at their defaults, a Disk face set to Capacity uses a wider pair of its own -
70 and 95 - because a drive that is 15% full is not an emergency.

- **Personalize the load colors** - choose your own calm, working and busy shades and the whole
  ramp is rebuilt between them.
- **Reverse it** - busy reads green and idle reads red, for when a meter climbing is the thing you
  *want* to see.
- **One fixed color instead** - turn the load coloring off and the bar stays the color you chose.
- **The glyph has its own color** - each meter arrives with its own accent (CPU amber, RAM blue,
  GPU violet, VRAM green, Disk yellow) and any of them can be changed.
- **Follow the shared color** - calm and working take the color every Firedies plugin on your deck
  shares: the album cover of whatever is playing, a picture of your own, a link, or two colors you
  pick. Busy stays red whatever the shared color is, and the glyph follows it too.

There's a **Reset colors to default** button, so nothing you try is a one-way door.

## When you press it

RAM, VRAM and Disk can each be read two ways - the amount, or the share. So on those three:

| Gesture | What happens |
|---|---|
| **Tap** | Flips the reading. GB becomes %, and on Disk activity becomes capacity. |
| **Hold** | Opens Task Manager - or whatever you chose instead. |

CPU and GPU have only one reading each, so they never gain a gesture that would do nothing. On
those two, **tap** opens your chosen app and **hold** can open a second one.

The choices are Task Manager, Resource Monitor, File Explorer, Control Panel and Settings - plus
**DirectX Diagnostic** on GPU and VRAM, and **Open this drive** on Disk. Or nothing at all, if you
would rather the key just reported. A hold is 450 ms.

## The disk face

- **Which drive** - any single physical disk, or **All disks** together.
- **What to show** - **Activity**, how hard it's working right now, or **Capacity**, how much is
  taken and how much is free.
- **The drive letter replaces the glyph**, so a wall of disk keys tells you which is which at a glance.

Capacity is a fact rather than a rate, so on that setting the History graph steps aside and the bar
returns. A graph of a number that barely moves would be a graph that lies about being interesting.

## Where the numbers come from

Every reading is taken from an interface that ships with Windows - the same performance counters
Task Manager and Resource Monitor read, plus the standard system queries for memory, volumes and
your card's own reported size. There is no kernel driver, no service, no administrator prompt,
and nothing to install beyond the plugin itself.

| Meter | Counter |
|---|---|
| **CPU** | Processor Information · % Processor Utility, across all cores |
| **RAM** | Total visible memory less free physical memory |
| **GPU** | GPU Engine · 3D utilization, summed across engines |
| **VRAM** | GPU Adapter Memory · dedicated usage, against the card's reported size |
| **Disk** | Physical Disk · idle time, inverted. Capacity from the logical volumes |

Readings are sampled about once a second and lightly smoothed across three samples, which is what
stops a meter flickering while still catching a real spike. The History graph holds the last
sixteen of them.

However many meters you place, there is only ever **one** reader running - so a deck with ten
Metrics faces costs the same as a deck with one. The History animation runs only while a History
face is on screen, and the reader shuts down entirely when the last meter is removed.

## Honest limits

- **GPU and VRAM need a modern Windows.** The graphics counters arrived in Windows 10 build 1709.
  On anything older, or on a machine whose driver doesn't publish them, those two faces show a dash
  rather than an invented number.
- **GPU is 3D load, not everything a card does.** Video encoding, decoding and compute run on their
  own engines and are deliberately not folded in - so the number matches Task Manager's 3D graph,
  not a larger figure that would flatter us.
- **VRAM totals come from the driver.** Where a card doesn't report its size, the share is estimated
  against 8 GB and the gigabyte reading stays exact. On a laptop with two graphics
  chips the used figure covers both, while the total is read once from the first adapter Windows
  lists - so the share can read high or low.
- **Disk activity is how busy, not how fast.** A drive can be at 100% while moving very little, if
  what it's moving is scattered. That's the counter's meaning, and we don't dress it up as a speed.
- **On a Mac (macOS 13 or later)** the same five meters read what macOS already reports, still with
  no driver and no administrator prompt. CPU is the processors' own load, RAM is Activity Monitor's
  *Memory Used* (cached files don't count as used), GPU is the graphics driver's own utilization
  figure, and Disk is how busy every disk is, together. The VRAM meter is labeled **GPU MEM** there,
  because on Apple silicon the graphics share one pool of memory with the processor. Choosing a single
  drive is Windows only for now, and a hold opens Activity Monitor, Finder, System Settings or System
  Information instead of their Windows twins.
- **Nothing leaves your PC.** No account, no sign-up, no analytics, no network call of any kind.

## Troubleshooting

**A meter shows a dash.** That reading couldn't be taken - see the limits above. It is deliberately
not replaced with a guess.

**GPU sits at 0 while a game is running.** Some titles do their work on an engine other than 3D.
Check Task Manager's GPU tab: if its 3D graph is flat too, the face is telling you the truth.

**The number differs slightly from Task Manager.** Both smooth their readings, on slightly
different schedules. Watch for a few seconds and they track each other.

**Nothing updates at all.** The reader is a PowerShell process; some locked-down machines block it
by policy. Removing every Metrics key and adding one back restarts it.

---

Windows 10/11 · macOS 13+ · Stream Deck 6.9+ · [Elgato Marketplace](https://marketplace.elgato.com)
