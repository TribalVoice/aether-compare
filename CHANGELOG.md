# Changelog

All notable changes to Aether Compare. Versions follow [Semantic Versioning](https://semver.org/).
The version shown in the app comes from the single `APP_VERSION` constant in `src/app.js`.

## [1.2.0] - 2026-11-18

### Added
- **Download null.** The null banner has a **Download WAV** button. It exports the null exactly as you hear it (current
  wow/flutter compensation, Match tape EQ, level matching and offsets) as a 24-bit WAV at the original sample rate,
  for the whole track or just the loop region. The file is named after file A, for example
  `Song_null_comp_EQ_loop.wav`. It is exported at true level by default. An optional **Normalise** checkbox raises the
  peak to −1 dBFS, and it is clearly marked as not true level. The WAV is built in your browser in small chunks, so
  even long files don't freeze the page, and nothing is uploaded.
- **Spectrum view.** A new panel under the player shows A (blue), B (amber) and the null (grey) on one graph, with a
  log frequency axis from 20 Hz to 20 kHz.
  - **Average** mode: a level-matched long-term spectrum (Welch, 32768-point FFT) of the whole file or the loop region.
    The null uses the same aligned, compensated signal you hear. An optional **B − A** line on its own right-hand axis
    shows the tape's EQ curve (head bump, high-frequency roll-off). Smoothing is 1/3 octave, 1/6 octave or raw.
  - **Live** mode: real-time spectra of A, B and the null path during playback. The slot you are hearing is highlighted.
  - Click the legend to show or hide each trace. Hover over the graph to read the frequency and levels.

## [1.1.1] - 2026-11-18

### Fixed
- **Grainy noise in the null residual with wow/flutter compensation.** The time-varying alignment was not precise enough
  (errors of a fraction of a sample, occasionally several samples). Even a 0.1-sample error stops high frequencies
  cancelling, so cymbals and other bright sounds leaked through as short bursts of noise. A new fine-tracking stage
  (sub-sample least-squares refinement, measured against an EQ-matched copy of the original) cuts the timing error
  by about 20× on a test signal. With Match tape EQ on, a real tape transfer now nulls 5 to 7 dB deeper above 1 kHz.

### Changed
- The drift analysis runs on up to four background threads, so it is about twice as fast: roughly 10 s for a 4-minute
  48 kHz stereo file.

## [1.1.0] - 2026-11-17

### Added
- **Wow/flutter compensation for null mode.** When you enter null mode, Aether Compare tracks how the offset between A
  and B changes over time. It uses GCC-PHAT on 0.25 s windows every 40 ms, followed by two fine passes at sub-sample
  precision (normalised correlation, then smoothing and confidence gating). It then renders a time-corrected copy of B
  that also corrects linear speed error. The work runs in an inline worker with a progress bar, so the page stays
  responsive. About 12 s for a 4-minute 48 kHz stereo file.
- **Drift readout:** whether drift was detected, the offset range, wow % rms and peak, speed error in ppm, the null depth
  with fixed alignment, with compensation and with EQ, and a small offset-over-time plot.
- **Wow/flutter comp toggle.** It switches on automatically when drift is detected (more than 4 samples of movement or
  more than 50 ppm). Otherwise it stays off.
- **Match tape EQ toggle (optional, null mode only).** It estimates the tape's complex transfer function (magnitude and
  phase) from the aligned audio, smooths it, and applies it to A as a per-channel FIR filter. A note explains that this
  removes head bump and high-frequency changes, so the residual is only saturation, noise and other non-linear change.

### Unchanged
- Normal A/B switching still uses the fixed offset and the untouched files. Compensation affects null mode only.

## [1.0.1] - 2026-11-17

### Changed
- Licence: replaced MIT with a proprietary licence (© 2026 TribalVoice, all rights reserved). Updated the footer, README and LICENSE.
- The production build (`index.html`) is now minified: inline JS and CSS go through esbuild, with comments stripped,
  local names mangled and no source maps. The readable source now lives in a private repository.

## [1.0.0] - 2026-11-17

First public release as **Aether Compare**, part of the Aether series.

### Added
- Rebranded from "Tape A/B Compare" to Aether Compare, with the Aether wordmark, mark, palette and footer.
- Version number in the header and footer, driven by `APP_VERSION`.
- Ko-fi support button in the header and a Ko-fi link in the footer, both plain links to `ko-fi.com/tribalvoice`.
- Files for GitHub Pages.

### Core features (from the internal v0 test build)
- Sample-synchronous A/B switching (up to 4 slots), with a crossfade adjustable from 0 to 50 ms.
- BS.1770 integrated-LUFS level matching (match down to the quietest file, or to A), true-peak clip warning, per-slot trim.
- Per-slot latency offset (ms or samples), FFT cross-correlation auto-align, polarity detection.
- Null / difference mode (B − A) with a null-depth readout.
- Waveform overview with click-to-seek and drag-to-loop.
- Blind X/Y preference test and an ABX test with a binomial p-value.
- Works offline from `file://`; audio never leaves the browser.
