# Changelog

All notable changes to Aether Compare. Versions follow [Semantic Versioning](https://semver.org/).
The version is shown in the app header and footer.

## [1.0.1] - 2026-11-17

### Changed
- Licence: replaced MIT with a proprietary licence (© 2026 TribalVoice, all rights reserved). Updated the footer, README and LICENSE.
- The production build (`index.html`) is now minified: inline JS and CSS go through esbuild, with comments stripped,
  local names mangled and no source maps.

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
