# Diesal Continued

Continuation maintenance of "Diesal"'s BSD 3-clause WoW widget kit (DiesalGUI / DiesalTools / DiesalStyle / DiesalMenu, c. 2014). Provides a small composable widget framework intended for addon authors who want a stable, dependency-light alternative to Ace3.

The original Diesal libraries went unmaintained after 2014. This addon keeps the kit alive against modern WoW interface versions, with the minimum patches needed for it to load and render correctly on each supported tier (Retail, Mists, TBC Anniversary, Vanilla, XPTR).

## What this addon provides

LibStub libraries (original Diesal MAJOR names preserved):

- **`DiesalTools-1.0`** — small shared utility module: table helpers, callback dispatch, color blending.
- **`DiesalStyle-1.0`** — texture / outline / font registry; vendored media (icon atlas, fonts, shadow textures).
- **`DiesalGUI-1.0`** — the 12-widget framework: Window, ScrollFrame, ScrollingEditBox, ScrollingMessageFrame, CheckBox, Button, Spinner, Input, DropDown, DropDownItem, ComboBox, ComboBoxItem.
- **`DiesalMenu-1.0`** — context-menu widgets layered on top of DiesalGUI.

The libraries are otherwise functionally compatible with the 2014 originals. Cairn-flavored maintenance fixes carried forward into this redistribution include:

- Atlas naming corrected (`DiesalGUIcons` consistent across Style media + widget references).
- Modern Retail `SetFont(file, height, flags)` signature support.
- Anonymous `CreateFrame` for adapter listeners to avoid `ADDON_ACTION_FORBIDDEN` on RegisterEvent in modern Retail.
- A handful of widget-specific bugfixes (CheckBox inner texture contrast, Button inactive-text color, etc.).

## Why a separate addon

Two reasons:

1. **Stability for users who depend on the v1 kit.** Some addons import `LibStub("DiesalGUI-1.0")` directly and need the kit to keep loading. Diesal Continued ships a clean, single-purpose redistribution under the original LibStub names.

2. **Honoring the original license.** The Diesal libraries shipped under New BSD (3-clause). A dedicated single-license redistribution keeps the attribution clean.

## Provenance

Original work © 2014 Diesal (diesal2010), New BSD (3-clause).
Continuation maintenance © 2026 ChronicTinkerer, same license.

The original addon: **[DiesalLibs on CurseForge](https://www.curseforge.com/wow/addons/diesallibs)**. That distribution stopped receiving updates after 2014; this addon is an unofficial continuation under the same BSD 3-clause license, refreshed for modern WoW interface versions.

Each ported file's header preserves the original copyright notice. Modifications by ChronicTinkerer are noted inline where they meaningfully change behavior. See `LICENSE` for the full BSD 3-clause text.

## Usage

```lua
local Gui   = LibStub("DiesalGUI-1.0")
local Tools = LibStub("DiesalTools-1.0")
local Style = LibStub("DiesalStyle-1.0")

local btn = Gui:Create("Button")
btn:SetParent(UIParent)
btn:SetPoint("CENTER")
btn:SetText("Hello")
btn:SetCallback("OnClick", function() print("clicked!") end)
```

See the original Diesal documentation (preserved in each library file's header) for the full API surface.

## Distribution

- **CurseForge:** https://www.curseforge.com/wow/addons/diesal-continued (project ID `1536687`)
- **WoWInterface:** https://www.wowinterface.com/downloads/info27138.html (ID `27138`)

## Install (developer / local)

This repo lives next to the other ChronicTinkerer addons. `Sync-WoWAddons.ps1` will junction it into `Interface\AddOns\Diesal-Continued` automatically.
