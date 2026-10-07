<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="../assets/phoenix-white.svg">
    <img src="../assets/phoenix-black.svg" alt="Firedies Productions" width="76">
  </picture>
</p>

# Now Playing

**Whatever is playing, on your deck.**

Album art, track and artist, live progress, play/pause and skip. The accent color is sampled from
the album cover itself, so the key takes on the record's own palette.

Now Playing reads Windows' own media system (System Media Transport Controls), the same one that
powers the volume overlay. No login, no account, no per-app setup.

On a Mac (macOS 13 or later) it reads **Apple Music and Spotify** directly, through their own
scripting, because macOS has no shared media session a plugin can read.

## Quick start

1. Drag **Now Playing** (under **Now Playing**) onto any key or dial.
2. Play something. The key fills in by itself.
3. That's the setup. Everything after this is taste.

## The colour is the cover

The accent is sampled from the album artwork itself, so the key changes character with every track -
and it's contrast-checked, so the text stays readable whether the cover is a white sleeve or a
black one.

If you'd rather it held still: **Always blue** keeps the Firedies accent whatever is playing, and
**Custom** lets you set your own gradient and keep it.

That colour is also the family's **shared color**, which any other Firedies plugin on your deck can
follow. Point it at a picture of your own, a link, or two colours you pick instead, and **Album
cover** here follows that along with everything else. A new cover's colours roll in over a second
rather than snapping.

## When nothing is playing

The key says **QUIET**, and a dial says **NOTHING PLAYING**. It doesn't keep the last track up as though it were still going,
and it doesn't leave a progress bar frozen mid-song pretending to be live.

That's deliberate, and it's the rule the whole family is built on: **a face that can't know
something says so.** A key that shows yesterday's track is worse than a key that shows nothing,
because you'll believe it.

## Three looks

| Look | What you get |
|---|---|
| **Full** | Artwork, track and the progress bar - plus the artist, one tick away in the panel (on by default on a dial, off on a key). |
| **Artwork only** | The cover, edge to edge. A wall of these is genuinely lovely. |
| **Just the icon** | A single play mark in the accent colour and nothing else, for a deck that already has enough going on. |

Plus **zoom** and a **background darkness** control for the artwork look, so the blurred glow behind
the cover sits back where you want it.

## The controls

| Gesture | What happens |
|---|---|
| **Press the key** | Play or pause. |
| **Hold the key** | Next track - or switch between the full and artwork looks, whichever you set it to. |
| **Tap the dial** | Play or pause. |
| **Turn the dial** | Skips tracks. In scrub mode it seeks; in volume mode it moves the system volume. |
| **Long-press the dial** | Cycles it: skip, then scrub, then volume, then back. Hold about 1.5 seconds to jump straight to volume. |

One dial, three jobs - skip, scrub, volume. Scrubbing turns the elapsed time to the accent colour and puts a handle on the bar; volume shows a speaker and a percentage.

---

## Which players work

Anything that reports to Windows media controls will show up: Spotify, the browsers (YouTube,
SoundCloud, Apple Music web), Groove, VLC, Media Player, and most modern desktop players.

If a player appears in the little media popup when you press a media key, it will appear on your
deck.

**If two of them fight over the key**, the settings let you show **only these** players or **hide
these** - so a YouTube tab in the background never steals the face from the album you're actually
listening to.

## foobar2000: install one component for the progress bar

**foobar2000 does not report track duration or position to Windows out of the box.** It reports the
title, the artist and the artwork, so the key fills in and looks right, but there is no timeline for
it to draw. The key will show the track without a progress bar rather than draw a bar that is not
real.

To get the progress bar and scrubbing, install the free `foo_mediacontrol` component:

1. Download the latest release from **[github.com/ungive/foo_mediacontrol/releases](https://github.com/ungive/foo_mediacontrol/releases)**
2. Take `foo_mediacontrol-x64.fb2k-component` for 64-bit foobar2000, or the `-x86` file for 32-bit
3. In foobar2000: **File -> Preferences -> Components -> Install...**, pick the file, then **Apply**
4. Restart foobar2000

The progress bar, the elapsed and total times on a dial, and dial scrubbing all start working once
it is installed.

*(The component is open source under the BSD-2-Clause license and is not made by us. We link it
because it is the piece Windows is missing, not because we have any part in it.)*

## Other players with no timeline

The same applies to any player that reports a track but no duration. The rule the key follows is the
same everywhere: **if the position is not real, the bar is not drawn.** A missing bar means the
player is not telling Windows where it is, not that the plugin lost track.

When you try to seek one of these, the dial names which it is - **NO TIMELINE FROM THIS APP**, or
**THIS APP WON'T SEEK** - and switches to volume rather than leaving the long-press looking broken.

## Sound and feel

A **tactile click** on press, with its own volume - the default, or a file of your own. It's
deliberately separate from the music: the click is feedback for your finger, not part of what you're
listening to.

## Honest limits

- **We only know what the app tells Windows.** Missing artwork, a blank artist, a stuck timeline -
  those come from the player, and the key shows what it was given rather than inventing the rest.
- **Some players never register at all.** If an app doesn't publish a media session, nothing on
  Windows can see it, including the volume overlay.
- **Nothing leaves your computer.** No account, no sign-up, no analytics. On Windows there is not a
  single network call - the artwork comes from the player. On a Mac, Spotify hands over a link to its
  cover rather than the picture, so that one image is fetched from Spotify's own image server.
- **On a Mac, it's Apple Music and Spotify.** Other players and browser tabs don't appear. It only
  talks to a player that is already open, so it never launches one. The first time, macOS asks you to
  allow **Firedies Now Playing** to control each player - once for Apple Music, once for Spotify.

## Troubleshooting

**Nothing appears at all.** The player is not reporting to Windows media controls. Press a media key
and see whether the Windows popup shows the track. If it does not, the player has no media-controls
support.

**The wrong app is showing.** Use the source filter in the settings to pin it to one player. The filter is shared by every Now Playing key and dial, so changing it on one changes what all of them show - keep them on the same setting.

**Art is missing but text is there.** The player is reporting the track without artwork. Some web
players do this on certain sites.

---

Windows 10/11 · macOS 13+ · Stream Deck 6.9+ · [Elgato Marketplace](https://marketplace.elgato.com)
