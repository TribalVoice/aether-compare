# Aether Compare

A/B listening tool for tape in the Aether series. Load a clean source and its tape-processed version, then switch
between them instantly. Both files play sample-locked and level-matched, so you hear the tape, not the loudness.

**Open it:** https://tribalvoice.github.io/aether-compare/ in Chrome, Edge, Firefox or Safari (desktop, tablet or phone).

![Aether Compare](screenshot.png)

**Privacy:** your audio never leaves your browser. Files are decoded and analysed locally on your device. Nothing is
uploaded, nothing is stored, and the app makes no network requests. The Ko-fi button is a plain link.

## How to use
1. Drag the **original** and the **tape** file onto the page (the first file goes to A, the second to B), or use
   **Load files…**. WAV, AIFF, FLAC, MP3, and anything else your browser can decode all work.
2. Aether Compare measures each file's loudness (ITU-R BS.1770 integrated LUFS) and matches the levels. By default it
   turns files down to the quietest one, so nothing is boosted into clipping. It also auto-aligns the tape file to the
   original, which compensates for transfer latency and corrects inverted polarity.
3. Press **Space** to play. Switch with **Tab** / **X**, **1** / **2** or **A** / **B**. The playhead never jumps.

### Features
- **Instant switching:** sample-locked, with an adjustable crossfade (0 = hard switch, default 5 ms).
- **Level matching:** LUFS and peak for each file, the applied gain, and a clip warning. Per-slot trim. **M** toggles matching.
- **Alignment:** offset in ms or samples, ±1 sample/ms nudges, **Auto-align**, polarity invert.
- **Null mode (N):** plays B − A to reveal exactly what the tape changed, with a null-depth readout.
  The result is only meaningful when the files are aligned.
- **Loop:** drag across the waveform. Click to seek, double-click or press Esc to clear.
- **Blind test:** hidden X/Y labels, pick your favourite, then the answer is revealed. **ABX test:** scored trials with a p-value.
- **Up to 4 slots** for comparing tape formulations or speeds.

### Shortcuts
| Key | Action |
|---|---|
| Space | Play / pause |
| 1–4, A/B/C/D | Select slot (Blind: 1/2 = X/Y; ABX: 1 = A, 2 = B, 3/X = X) |
| Tab or X | Toggle between the last two |
| ← / → | Seek 5 s (Shift: 1 s) |
| ↑ / ↓ | Master volume ±1 dB |
| Home | Start / loop start |
| L · Esc | Loop on/off · clear loop |
| [ · ] | Loop in · out at playhead |
| M · N | Level match · null mode |

**Licence:** © 2026 TribalVoice. All rights reserved. No copying, modification or redistribution without permission.
See [LICENSE](LICENSE).

**Support:** [ko-fi.com/tribalvoice](https://ko-fi.com/tribalvoice)
