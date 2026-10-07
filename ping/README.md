<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="../assets/phoenix-white.svg">
    <img src="../assets/phoenix-black.svg" alt="Firedies Productions" width="76">
  </picture>
</p>

# Ping

**Know before the game tells you.**

Ping puts your connection on your deck - live latency to any server you care about, your real
traffic in and out, and a full speed test on one press. Green when it's healthy, red when it isn't,
and you see it happening rather than finding out mid-fight.

Nothing is guessed. If a server can't be reached the face says so instead of showing you a stale
number that looks fine.

## Quick start

1. Drag **Ping** (under **Ping**) onto any key or dial.
2. It's already live against a starter list - Google, Cloudflare, GitHub.
3. Open its settings and put your own server in. A full URL or just a domain: `google.com` works.

## The four

| Action | What it does |
|---|---|
| **Ping** | Live latency to whichever server you're watching, tinted by health. |
| **Download** | Your real download traffic, live. Press to run a capacity test. |
| **Upload** | The same going out - useful the moment you start streaming. |
| **Speed Test** | Ping, download and upload in one, powered by Cloudflare. Press to run. |

All four work as a **key** or as a **dial**.

## Your servers

Add a server once and it's everywhere - the list is shared by every Ping control on your deck.

| Gesture | What happens |
|---|---|
| **Turn the dial** | Steps through your servers. On a key, press does the same. |
| **Tap the sides** | On a touch strip, left goes back and right goes forward. |
| **Press the dial** | Takes a fresh reading right now, without waiting for the next check. |
| **Press and hold** | Jumps straight back to the first server in your list - your home. |

Each server gets an icon automatically: a bundled brand mark if we have one (**29** are bundled, and **22**
addresses are recognised on sight without asking the network),
otherwise the site's own icon fetched live. Click a server's **icon chip** to override it with any
emoji or a picture of your own.

### Detect my server

You usually don't know the address of the game server you're actually on. **Detect my server**
looks at what your machine is genuinely connected to and offers you the candidates.

It reads **TCP** connections. Many games carry gameplay over UDP and those will not appear - the
panel says so rather than pretending the list is complete. If yours is one of them, watch its login
or matchmaking host instead; it usually sits in the same datacentre.

## Four styles

| Style | What you get |
|---|---|
| **Color bar** | The number plus a bar underneath, coloured by health. |
| **B & W** | Monochrome. The bar is brightest when your ping is best, and darkens as latency climbs. |
| **Clean** | Just the number, large - and the number itself carries the colour. |
| **History** | The bar becomes a live graph. Oldest on the left, now on the right. |

## What counts as good

Out of the box: green under **100 ms**, red over **550 ms**, travelling through amber between them.
Both numbers are yours - a competitive shooter and a video call have very different ideas of
"fine". A server that answers nothing at all counts as down after about **six seconds** - two waiting for the ping, four more for the fallback.

You can pick your own calm / working / busy colours, or turn the health colouring off and have one
fixed colour instead.

Or tick **"good" follows the shared color** and a healthy reading takes the colour every Firedies
plugin on your deck shares: the album cover of whatever is playing, a picture of your own, a link,
or two colours you pick. Amber and red never follow it - a slow or dropped connection always looks
like one.

## The traffic meters

Download and Upload show what is *actually moving* right now, not what your line could do in theory. They add up every network adapter, so with a VPN running you may see the same traffic counted twice.

- **MB/s or Mbps.** Megabytes per second is what a download shows you; megabits per second is what
  your provider sold you. They differ by a factor of eight, which is why one always looks
  disappointing. Pick whichever you think in.
- **Colour runs the other way here.** On Ping a big number is bad; on a speed meter a big number is
  good. Out of the box the meters read the other way round though - calm green when the line is quiet, climbing through amber to red as it fills up. Tick "reverse it: slow = red, fast = green" if you'd rather fast was the green one.

## The speed test

Powered by **Cloudflare**, the same service behind a large share of the web - so the test runs
against real infrastructure near you rather than a server we chose to flatter the result.

On a dial, **turn** to cycle the four views and **press** to run. On a key, press runs it.

## Alerts and feel

- **Chime when the connection drops** - eight sounds included, or point it at a file of your own.
- **Tactile click on press**, so a key feels like it did something.
- **Show the IP** of whatever you're pinging, or hide it. On a key it takes the bar's place.
- **Show the MS unit**, or drop it and let the number have the whole face.
- **Number aligned** left, middle or right on dials - left by default. Keys are always centred.
- **Every label renders in your own script** - Japanese, Chinese, Korean, Arabic, Hindi, Thai,
  Hebrew and more.

## Honest limits

- **It's a real ping first, and a fallback second.** Ping asks Windows to send an actual ICMP echo -
  the same thing the `ping` command does. Plenty of hosts refuse ICMP, so when there's no reply it
  opens a TCP connection to the port instead and times that. Both are honest measurements; the TCP
  one usually reads a few milliseconds higher, because a connection is more work than an echo.
- **UDP game servers can't be detected.** See *Detect my server* above.
- **A speed test is a snapshot.** Run it while a download is going and it will read low, correctly.
  The live meters are the better number to watch.
- **Server icons are fetched from the internet** the first time a server is seen - a brand mark
  from a public icon service, otherwise the site's own favicon. Bundled ones need no network at
  all. There's no analytics and no account - though the lookup does have to name the domain to the icon service it asks, so set your own icon on anything you'd rather keep here.
- **On a Mac (macOS 13 or later), latency is the TCP connection time.** Ping doesn't send an ICMP
  echo there, so the reading runs a few milliseconds higher than a plain `ping` and follows the same
  movement. The Speed Test's ping figure is Windows only for now. Download and Upload read the network
  adapters' own counters, and **Detect my server** reads the connections your apps have open, with no
  administrator prompt.

## If something looks wrong

| Symptom | What it means |
|---|---|
| **The number is a dash** | That server didn't answer inside 4 seconds. Down, blocking us, or the address is wrong. |
| **Higher than my game shows** | That host is refusing ICMP, so the reading is a TCP connection instead. Slightly higher, and it tracks the same movement. If *every* server reads high, it's probably that Windows isn't in English - we read Windows' own ping output and only understand the English wording, so we fall back to TCP everywhere. |
| **A server has no icon** | No bundled mark and no reachable favicon. Give it an emoji or your own picture from its icon chip. |
| **Speed test reads low** | Something else is using the line. That's the honest number - watch the live meters instead. |

---

Windows 10/11 · macOS 13+ · Stream Deck 6.9+ · [Elgato Marketplace](https://marketplace.elgato.com)
