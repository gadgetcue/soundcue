# Changelog

All notable changes to SoundCue. Format follows [Keep a Changelog](https://keepachangelog.com/), versions follow [Semantic Versioning](https://semver.org/).

## [0.3.9] - 2026-11-21

### Fixed
- Curve EQ graph: while dragging a point, a thin guide line could be painted outside the dialog card. The graph now draws only inside its own box.

## [0.3.8] - 2026-11-21

### Added
- **Curve EQ is now a graph.** Frequency across (log scale), gain up and down. Tap the graph to add a point, drag to move it, double-tap to remove it, or use Remove point. Presets: Flat, Bass boost, Treble boost, Voice clarity, Cut rumble, Telephone. The audio is filtered to follow the drawn curve. Works with touch and mouse.

### Changed
- Effect dialogs: tips are one short line (the full text is in the tooltip); the controls scroll while Apply, Preview, Reset and Cancel stay in view, so the dialogs fit a phone held sideways. Sliders size to the screen and are taller on touch.
- On touch screens, dialogs and Settings have a wide solid scroll bar with a gutter, so a swipe along its edge scrolls even where sliders take the drag.
- Shorter toolbar tooltips.

## [0.3.7] - 2026-11-21

### Changed
- **iPad and iPhone toolbars match Windows.** The pills, groups and spacing are the same full size as on Windows. Where the width is too small the rows scroll sideways (with arrows at the cut-off edge), on iPad and iPhone alike; nothing shrinks, collapses or hides. A row that fits spreads its pills so the last one ends at the same margin as the first starts. This replaces the shrink-to-fit steps of 0.3.6.

## [0.3.6] - 2026-11-21

### Fixed
- **Toolbar fits iPad and iPhone screens.** On touch screens, when a row is too wide the pills shrink a step or two and tighten their gaps, then the Enhance voice pill becomes an icon, and the level meters step aside, before anything scrolls. A row that fits spreads its pills so the last one ends at the same margin as the first starts.
- **Phone held sideways:** File to Analyze collapse into one Menu button, search is a round button that opens a search sheet, and the project name is dropped instead of showing as "Untit...".

## [0.3.5] - 2026-11-21

### Changed
- **AI Voice Enhance learns the noise from the silence before you start talking** (up to 10 s at the start of the clip) and removes it as the first step, again after the EQ and compressor, and once more as the very last step after the loudness normalise. It uses a Wiener filter instead of the old threshold mask. Measured: pauses end up 35 to 80 dB lower for steady noise. Noise mixed with the words is only reduced by a few dB. See docs/noise-reduction-test.md.
- New optional **Use my silence sample** switch (select a noise-only stretch, press Use Selection as Silence Sample) for clips that do not start with silence.

### Added
- Repeatable noise-reduction test (`noise_eval` example and `scripts/make_eval_speech.sh`).

## [0.3.4] - 2026-11-21

### Added
- **File > Import project from another editor…** converts a project into a SoundCue project (tracks, clip positions and trims, gain, pan, mute, solo, markers) and shows what was and was not converted. Reads the project files of the common desktop editors and DAWs (.aup3, .aup, .sesx, .rpp, .als) and the interchange formats FCPXML, XML and EDL. Audio files are found next to the project or by name in its sub-folders. Each track's clips are merged into one track at their original positions.

## [0.3.3] - 2026-11-21

### Added
- **Home button** (a movable toolbar icon) and a **Home page**: new project, open, import, and your recent files. The project you were editing stays open behind it (Continue editing).
- **New effects:** Auto Duck (lowers music under a voice), Blend Tracks (crossfade two tracks), Smooth Join (removes the click at a splice), Curve EQ (12 points), Shelf Filter, Gliding Stretch (tempo and pitch that change gradually), Multi Delay (regular or bouncing), Glitch Repair, Voice Isolation, and a new **Spectral** category (Band Tool, Band EQ, Dual Shelves). Categories were renamed: Volume & Dynamics, Tone & Filters, Space & Delay, Colour & Modulation, Clean-up & Repair.
- **Back up and restore settings** to one file (Settings > About), through the system file pickers, so it works on Windows, iPad and iPhone. Restoring keeps a copy of the previous settings.
- The status bar shows **Auto saving...** while autosave writes, then **All changes saved** with the time, or **Auto save off**.

### Changed
- **Upgrades never reset your settings.** Settings load field by field (an unknown or damaged field falls back on its own), are versioned and migrated, are written safely, and an older file is copied to settings.v<N>.bak first.
- Onboarding: buttons are the same size and in the same place on every page, spacing is even, the page scrolls inside the card instead of being cut off, and it fits a phone on its side.

## [0.3.2] - 2026-11-21

### Changed
- **All pop-up menus** (File, Edit, Select, Tracks, Generate, Effect, Analyze, the toolbar, track, waveform, label and sidebar right-click menus) now open as a sheet in the centre of the window over a dimmed backdrop. Tap the backdrop, press Esc, or choose an item to close it. Sub-menus fold open inside the sheet.

### Fixed
- Right-click on the toolbar > **Customize toolbar...** now opens the customize mode (the menu closed itself before the click registered). The menu is also opaque and the right width.
- The **text size** setting now changes only the text. It no longer scales the whole interface: buttons, pills, panels and spacing stay the same size (the toolbar size has its own setting).

## [0.3.1] - 2026-11-21

### Added
- **Icon-level toolbar customizing**: every icon can sit anywhere in either row. An icon alone is a round circle pill; join icons into pills of 2, 3, 4 or more, split them again, hide icons in a tray (press and hold on touch). Old layouts carry over.
- **Toolbar size** setting (Settings > Appearance): extra small to extra large.

### Changed
- AI Voice Enhance always normalises and limits at the end of its chain: it matches the chosen loudness target and true-peak ceiling (per platform preset), and with loudness matching off it still peak-normalises to the ceiling and limits, so a result is never quiet and never clips.
- AI Voice Enhance cleans the pauses: after compression it pushes the quiet parts between words down (new "Quiet-part cleanup" control, 20 dB by default), so the make-up gain and normalising no longer lift the leftover background noise.
- The sidebar button is the first icon in the toolbar.
- The screenshots in the README use the MacBook frame.

### Fixed
- Toolbar pills line up exactly in both rows on desktop, iPad and phone widths (top-right pills, scroll arrows, bottom bar).
- The text size slider no longer flickers: it applies when you let go.

## [0.3.0] - 2026-11-21

### Added
- **Real-time autosave**: every change is written in the background (safe temp-file-then-rename). A saved project is updated in its own file; a new project gets a recovery copy that SoundCue offers back after a crash or restart. Switch it off in Settings > Editing. A "Saved" indicator shows in the status bar.
- **Customizable toolbar**: drag every single icon to any place in either row (press and hold on touch). An icon alone is a round circle pill; join icons into pills of 2, 3, 4 or more, split them again, and hide icons you do not use in a tray. Reset to the original layout any time. Right-click an empty part of the toolbar or use Settings > Appearance > Customize.
- **Swipeable toolbar rows**: the toolbar scrolls sideways when it does not fit (swipe, drag or wheel) with arrows at the cut-off edges.
- **Right-click menus** on the waveform, on sidebar functions (add to a category) and on tracks in the track list.
- **Storage folder** setting (Windows folder picker; iPad/iPhone folder picker) for where open, save and export start.
- iPad and iPhone: hardware keyboard, mouse and trackpad support, safe-area layout.

### Changed
- All toolbar capsules are exactly the same height with fully round ends, so rows line up; touch layouts use 44 pt buttons.
- The search pill has a focus ring, a larger clear button and Esc to clear.
- The phone status bar drops less important details instead of overlapping.

## [0.2.0] - 2026-11-21

### Added
- **One-click AI Voice Enhance**: automatic noise profile from the quietest speech-free stretch (RNNoise as fallback), 10-band graphic EQ with a draggable voice curve, de-esser, warmth, compressor controls, loudness mastering, limiter and true-peak safety.
- **Export presets** for YouTube, YouTube Shorts, Instagram, TikTok, Facebook, Twitch, X, Snapchat, LinkedIn, Spotify, Apple Music, podcasts, audiobooks (ACX), EBU R128 and ATSC A/85, plus a *Platform Loudness Master* effect.
- **MP3 export** (128 / 192 / 320 kbps) and **OGG Vorbis export**; **metadata tags** in MP3, WAV, FLAC and AIFF files.
- **Custom sidebar categories** with drag and drop (long-press on touch), rename, reorder, delete; every category collapsible and remembered.
- **Spectral selection** in the spectrogram view with *Spectral delete* and *Spectral keep*.
- **Macros** and **batch processing** (macro + optional platform preset over many files).
- **Envelope tool** (F4) for volume curves; envelopes play, export and save with the project.
- **Silence Finder** and **Contrast** analysis tools.
- **Sync-lock** so time edits keep every track aligned.
- **Rebindable keyboard shortcuts** for every command (Settings > Shortcuts).
- **MIDI import** through a built-in synthesizer.
- **Mixer board** (Ctrl+M) with faders, pan, mute, solo and a master meter.
- **App icon** (macOS-style squircle, colour and dark versions), embedded in the Windows app.
- **Single-file Windows installer** (`SoundCue-Setup.exe`) built by GitHub Actions.
- Credits in *Settings > About* and in the README.

### Changed
- The first window now fits the screen it opens on.
- Settings icon redrawn as a macOS-style gear.

### Fixed
- Dialogs resize to small windows.
- Self-test and demo runs no longer write into your real settings.
- Scroll-bar crash on very narrow windows (iPhone layout).

## [0.1.0] - 2026-11-21

### Added
- First release: multitrack editor with import, record, playback, cut / copy / paste, unlimited undo, 41 effects and generators, spectrogram view, labels, export to WAV / FLAC / AIFF, project files, the Siddhant pill-toolbar interface with 12 dark themes, a light theme and 16 accents, welcome tour and settings.
