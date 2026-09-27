<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="../assets/phoenix-white.svg">
    <img src="../assets/phoenix-black.svg" alt="Firedies Productions" width="76">
  </picture>
</p>

# Audio Meters

**See what you hear.**

Nine studio meters on your deck - level, VU, spectrum, spectrogram, waveform, scope, stereo field,
loudness and musical key - each one on a key or a dial. They listen to everything Windows plays,
or one output, one input, or a single app, and they take their colour from the record.

No driver, no account, nothing to sign into. Audio Meters reads the audio Windows is already
playing through Windows' own loopback capture, the same way a screen recorder hears your PC.

## Quick start

1. Drag **Audio Meter** (under **Audio Meters**) onto any key or dial.
2. Play something. The meter starts moving.
3. Open the key's settings, pick the meter you want under **Meter**, and pick what it listens to
   under **Listen to**. Press **Use this source on every meter** once and the whole page follows.

That's the setup. Everything after this is taste.

## The nine meters

| Meter | What it shows | Its own knob |
|---|---|---|
| **Level** | Stereo peak and RMS bars on a dBFS ladder, with peak-hold marks and a CLIP lamp. | Sample peak or **true peak** (4x oversampled); hold time 0.5-10 s; keep CLIP lit until you press. |
| **VU** | The classic needle - slow ballistics, red past zero, and a peak lamp for what a needle can't catch. | Four looks: **needle**, **twin needle** (L and R on one scale), **bar**, **LED**. Reference -20, -18, -14 or -12 dBFS = 0 VU. |
| **Spectrum** | Frequency bars from 30 Hz to 18 kHz with peak caps. | 12 to 56 bars. |
| **Spectrogram** | Frequency over time - the heat map. Low at the bottom, now at the right. | Scroll speed: fast, normal, slow. |
| **Waveform** | The last few seconds of amplitude, scrolling left like a timeline. | Half a second to thirty seconds across the face. |
| **Scope** | An oscilloscope trace of the last 33 ms, triggered, so a periodic sound holds still. | Zoom. |
| **Stereo** | A vectorscope of the stereo field, plus the L/R correlation on the side. | **Polar sample**, **polar level**, or **Lissajous**. |
| **Loudness** | LUFS, against a target. | Which reading is the big one (below), a second reading underneath, and the target. |
| **Key** | The musical key of what is playing, with a confidence bar. | **Note names** (A minor) or **Camelot** (8A). |

Where a meter offers **Zoom** (1x, 2x, 4x, Auto), Auto follows the signal so a quiet source still fills the face.

### Loudness, in detail

Eight readings, any of which can be the big number, with a second one shown smaller underneath:

| Reading | What it is |
|---|---|
| **Momentary** | The last 400 ms. |
| **Short-term** | The last 3 seconds. |
| **Long** | The last 30 seconds. |
| **Average** | Integrated loudness since the last reset - press the key to reset it. |
| **Max** | The loudest moment since reset. |
| **Range** | Loudness range (LRA), in LU. |
| **True peak** | The highest true peak since reset, in dBTP. |
| **PLR** | Peak to loudness ratio. |

The bar under the number runs against a **target** - pick one of the presets or type your own
between -36 and -6 LUFS.

### The key finder

It listens to the last few seconds, works out the most likely key, and shows it big - **Amin** in
note names, or **8A** in Camelot for anyone mixing by wheel. The bar underneath is its confidence.
When it is not sure, the bar says so; it never prints a key it is guessing at.

## Listen to

Four sources, on every meter:

| Source | What it hears |
|---|---|
| **System** | Everything Windows plays on your default output. The face calls it SYSTEM. |
| **One output** | One output device, whatever plays through it. |
| **One input** | A microphone, a line-in, or your interface's loopback. An input is read as it arrives, so the Windows volume slider has no say in it. |
| **One app** | One application - Spotify, a browser, a game, a DAW running on a Windows driver. |

**Use this source on every meter** stamps your choice on every Audio Meters key and dial, on every
page, and new ones start with it.

**Compensate for the Windows volume slider** is on by default. What Windows plays is already scaled
by its volume slider; on, the meter shows the level as the app sent it, whatever the slider says;
off, it shows what actually reaches the output. An interface loopback follows the slider of the
output it loops.

### A DAW on ASIO

Windows never hears ASIO audio, so **System** and **One app** stay silent for Ableton Live, Cubase,
REAPER and friends while they run on an ASIO driver. The way in is your interface's **hardware
loopback**: the interface plays its own outputs back to itself on an input, and the meter listens
there. It carries everything the interface plays - the DAW and Windows audio together.

**Arturia MiniFuse** (tested on a MiniFuse 4, Ableton and Spotify at once):

1. Open **MiniFuse Control Center**, then **OUTPUTS**.
2. In the **LOOPBACK** panel choose **OUT 1/2** as its source.
3. In the meter's settings: **Listen to** > **One input** > **Loopback Mix Left/Right (MiniFuse)**.
4. Press **Use this source on every meter**.

**Focusrite Scarlett / Clarett** (from Focusrite's own support pages): the Windows driver shows
non-ASIO apps only one recording device until you tell it otherwise, so Loopback is hidden from the
meter by default.

1. Click the **Focusrite Notifier** icon in the tray, then **Expose/Hide Windows Channels**, and tick
   the **Loopback** pair.
2. In **Focusrite Control 2** (4th Gen) or **Focusrite Control** (3rd Gen, Clarett), route what you
   want to hear into the Loopback channels. By default it carries the computer's playback.
3. In the meter's settings: **Listen to** > **One input** > **Loopback**, then **Use this source on
   every meter**.

Loopback exists on Scarlett 4th Gen, Scarlett 3rd Gen 4i4 and up, Clarett and Vocaster. The 3rd Gen
Solo and 2i2, 2nd Gen, and Clarett+ do not have it.

**The general rule:** if your interface's loopback is not in the list, its driver is hiding it from
Windows - look for an option that exposes extra channels to Windows apps.

**No loopback at all?** Set the DAW to a non-ASIO driver (MME, DirectSound or WASAPI shared) and use
**One app**.

## Where the colour comes from

| Palette | What you get |
|---|---|
| **Shared color** | One colour for every Firedies plugin on your deck: the album cover of whatever is playing, a picture of your own, or a link. It is always kept bright enough to read, and a row of meters changes with the record. |
| **Firedies · Ice · Green · Amber · Mono** | Five fixed gradients. |
| **Custom** | Your own two colours. |

The source name on the face can be switched off under **Show** if you want the meter and nothing else.

## The controls

| Gesture | What happens |
|---|---|
| **Tap the key** | Resets the meter - peak hold, CLIP, the average, the key. |
| **Hold the key** (half a second) | Switches to the next meter. |
| **Turn the dial** | Steps the meter's own knob - VU reference, spectrum bars, waveform time, zoom, stereo view, loudness reading - or switches meters, whichever you set under **The dial**. |
| **Press or tap the dial** | Resets the meter. |
| **Hold the dial** (half a second) | Switches to the next meter. |

A **tactile click** on press, with its own volume, the default sound or a file of your own, and a
quieter tick as you turn a dial. It's feedback for your finger, not part of what you're listening
to.

## When there is nothing to show

The face never moves on nothing. That's the rule the whole family is built on: **a face that can't
know something says so.**

| The face says | What it means |
|---|---|
| **QUIET** | The source is open and silent. |
| **APP NOT RUNNING** | You chose One app, and that app is not running. |
| **MUTED** | The output you are listening to is muted in Windows. |
| **NO HELPER** | The audio helper is missing from this install. Reinstall the plugin. |

If a source cannot be opened at all, the face says why rather than drawing a bar that dances on
air.

## Honest limits

- **It hears what Windows hears.** A driver that bypasses Windows (ASIO) is invisible until your
  interface loops it back - see above.
- **The key finder is a listener, not a chart.** It reports the most likely key of the last few
  seconds with its confidence; a long ambient chord or a drum break will keep it unsure, and it
  will say so.
- **Loudness is measured on what reaches the meter.** With the Windows slider compensated (the
  default) the reading is the app's own level; with it off, it is the level after the slider.
- **Windows only, for now.** The loopback capture this reads is a Windows interface.

## Troubleshooting

**The meter says QUIET while music is playing.** The source is not the one that is playing. Check
**Listen to**: a DAW on ASIO needs the loopback route above; a game on a second output needs **One
output** pointed at that output.

**One app lists the app but the meter stays QUIET.** Some apps play through a helper process. Try
**System** or **One output** instead, or the interface loopback.

**The loopback is not in the input list.** The interface's driver is hiding it from Windows. Look
in its control software for an option that exposes extra channels to Windows apps, then press the
refresh arrow next to **Listen to**.

**The VU reads hot on everything.** Change the reference. 0 VU = -18 dBFS is the default; broadcast
and older gear sit at -20, modern loud masters read better at -14 or -12.

---

Windows 10/11 · Stream Deck 6.9+ · [Elgato Marketplace](https://marketplace.elgato.com)
