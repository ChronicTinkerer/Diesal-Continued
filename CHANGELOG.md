# Changelog

All notable changes to **Diesal Continued** are recorded here.
The format is loosely based on
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/).
Versions are sequential build numbers (one increment per `.dev/release.ps1` run).

## [Unreleased]

## [1] — 2026-05-07 — Initial standalone release

### Added

- New addon `Diesal Continued` carrying Diesal's 2014 BSD 3-clause widget
  kit, refreshed for modern WoW.
- Vendored `LibStub` so the addon loads without an external dependency.
- Vendored copies of the libraries (original Diesal LibStub MAJORs):
  - `DiesalTools-1.0`
  - `DiesalStyle-1.0` (with media: icon atlas, fonts, shadow textures)
  - `DiesalGUI-1.0` (12 widgets: Window, ScrollFrame, ScrollingEditBox,
    ScrollingMessageFrame, CheckBox, Button, Spinner, Input, DropDown,
    DropDownItem, ComboBox, ComboBoxItem)
  - `DiesalMenu-1.0`
- License file: BSD 3-clause, with original Diesal copyright preserved.
- Build pipeline: `.pkgmeta` for BigWigs packager + `.dev/release.ps1`
  helper using sequential build numbers.

### Cairn-flavored maintenance fixes carried forward

- Atlas naming corrected (`DiesalGUIcons` consistent across Style media
  registration + widget `texFile` references).
- Modern Retail `SetFont(file, height, flags)` signature: third `flags`
  arg now passed (empty string for none) since Interface 120005 made it
  mandatory.
- Anonymous `CreateFrame` used for adapter listeners to avoid
  `ADDON_ACTION_FORBIDDEN` on `RegisterEvent` in modern Retail named
  frames.
- Widget-specific bugfixes:
  - CheckBox inner texture contrast bumped from near-black to a visible
    gray so the checked state is legible against most backdrops.
  - Button inactive-text color softened to match Diesal's intent (the
    upstream had a literal black that disappeared on dark themes).
  - `PlaySound` calls updated from removed string IDs to current numeric
    constants.

### Notes

- Identical library code to the v1 family that previously lived inside
  the Cairn library bundle. Cairn keeps its own local copy under
  `Cairn-Gui-*-1.0` MAJORs during the transition, so both addons can
  coexist without LibStub MAJOR conflict (different MAJORs entirely).
- All future v1 fixes land here first; Cairn's local copy is frozen.
