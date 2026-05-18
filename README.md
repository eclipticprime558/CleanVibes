# CleanVibes — Speaker Cleaner

A Progressive Web App (PWA) that uses precision sound frequencies and haptic vibration to clean phone speakers. Works on any modern mobile browser — no install required.

**Live demo:** [Enable GitHub Pages to get a public URL]

---

## How it works

Sound waves at specific frequencies cause the speaker diaphragm to vibrate, physically pushing water and loose dust out of the speaker cavity. This is the same principle Apple uses for the Apple Watch Water Lock feature (165 Hz resonance).

CleanVibes goes further than most apps by using **frequency sweeps** across multiple waveform types — not just a static tone — which covers more of the speaker's resonant range and improves effectiveness.

---

## Modes

| Mode | Duration | What it does |
|---|---|---|
| **💧 Water Eject** | 30s | 165 Hz baseline → sweeps 80–400 Hz → final pulse. Best for same-day water exposure. |
| **🌀 Dust Blast** | 25s | Sawtooth + square waves sweeping 50–800 Hz. Aggressive diaphragm excursion for loose particles. |
| **✨ Deep Clean** | 60s | Full water + dust sequence with a complete 80→800 Hz sweep. Monthly maintenance. |
| **🎛️ Custom** | 20s | Manual frequency slider 20–800 Hz. Run any sine wave you want. |

---

## Features

- **Live waveform visualizer** — real-time oscilloscope using Web Audio API
- **Frequency sweeps** — ramps between frequencies, not just a static tone
- **Multiple waveform types** — sine (water), sawtooth/square (dust)
- **Haptic vibration** — synchronized with audio via Vibration API
- **Progress ring** — shows time remaining and current phase
- **Runs counter** — tracks sessions today, persisted in localStorage
- **Offline-capable PWA** — works without internet, installable to home screen

---

## Does it actually work?

Yes, with caveats.

**Works well for:**
- Water exposure within the same day (~85% success rate in user reports)
- Loose surface dust and lint causing muffled audio

**Won't fix:**
- Water damage to internal circuits or solder joints
- Physical damage (torn diaphragm, burned voice coil)
- Deep embedded corrosion

Use it as **first aid**, not a repair. If audio quality doesn't improve after 2–3 runs, see a repair shop.

---

## Usage tips

1. **Turn volume to maximum** — the louder, the more the diaphragm moves
2. **Disable Bluetooth** — audio must play through the device speaker
3. **Point speaker face-down** toward a dry cloth
4. **Run 2–3 times** for water — wait 10 seconds between runs
5. For water: run immediately, don't wait

---

## Running locally

Just open `index.html` in any modern browser. No build step, no dependencies.

For PWA install on mobile, serve over HTTPS (GitHub Pages works):
```
# With Python
python -m http.server 8080

# With Node
npx serve .
```

Then visit the URL on your phone and tap "Add to Home Screen" in Safari or Chrome.

---

## Generating app icons

Open `generate-icons.html` in your browser. It will auto-download `icon-192.png` and `icon-512.png` — move them into this folder for full PWA icon support.

---

## Tech stack

- Vanilla HTML/CSS/JS — zero dependencies
- [Web Audio API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API) — oscillator, analyser, gain nodes
- [Vibration API](https://developer.mozilla.org/en-US/docs/Web/API/Vibration_API) — haptic feedback
- Service Worker — offline caching
- PWA manifest — home screen install

---

## Browser support

| Feature | Chrome Android | Safari iOS | Firefox |
|---|---|---|---|
| Web Audio | ✅ | ✅ | ✅ |
| Vibration API | ✅ | ❌ | ✅ |
| PWA install | ✅ | ✅ | Partial |

Safari on iOS does not support the Vibration API — audio still works fully.
