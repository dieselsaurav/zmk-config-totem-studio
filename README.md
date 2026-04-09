# TOTEM — ZMK Firmware Config

[![Build ZMK firmware](../../actions/workflows/build.yml/badge.svg)](../../actions/workflows/build.yml)

> Miryoku-inspired ZMK configuration for the [TOTEM](https://github.com/GEIGEIGEIST/TOTEM) 38-key split keyboard, with [ZMK Studio](https://zmk.studio/) support for real-time keymap editing.

---

## Keymap

![Keymap](keymap-drawer/totem.svg)

*Auto-generated with [keymap-drawer](https://github.com/caksoylar/keymap-drawer) on every push.*

---

## Layout Philosophy

This config follows the [Miryoku](https://github.com/manna-harbour/miryoku) layout system — a minimal 36-key layout that puts everything within one key of the home row.

- **QWERTY** base with **home row mods** (GACS order)
- **Vim-style** navigation (HJKL arrows)
- **6 thumb-activated layers** — no combos, no chords, just hold a thumb key
- **Symmetric design** — left thumbs activate right-hand layers and vice versa

### Thumb Keys

```
Left hand                          Right hand
┌───────────┬───────────┬────────┐ ┌─────────┬──────────┬─────────┐
│ MEDIA/ESC │  NAV/SPC  │MOUSE/TAB│ │ SYM/ENT │ NUM/BSPC │ FUN/DEL │
└───────────┴───────────┴────────┘ └─────────┴──────────┴─────────┘
```

### Layers at a Glance

| Layer | Activation | Left Hand | Right Hand |
|:------|:-----------|:----------|:-----------|
| BASE | Default | QWERTY + home row mods | QWERTY + home row mods |
| NAV | Hold `Space` | Mods | Vim arrows, clipboard, PgUp/PgDn, Home/End |
| MOUSE | Hold `Tab` | Mods | Mouse move, scroll, L/M/R click |
| MEDIA | Hold `Esc` | Mods | Prev/Next, Vol, Play/Stop, BT profiles |
| NUM | Hold `Bspc` | `[ 7 8 9 ]`, `; 4 5 6 =`, `` ` 1 2 3 \ `` | Mods |
| SYM | Hold `Enter` | `{ & * ( }`, `: $ % ^ +`, `~ ! @ # \|` | Mods |
| FUN | Hold `Del` | F12-F1, PrtSc, ScrLk, Pause | Mods |

### Home Row Mods

```
Left:   GUI / A    ALT / S    CTRL / D    SHFT / F
Right:  SHFT / J   CTRL / K   ALT / L     GUI / '
```

| Setting | Value |
|:--------|:------|
| Flavor | tap-preferred |
| Tapping term | 200 ms |
| Quick tap | 175 ms |
| Require prior idle | 150 ms |

---

## Hardware

| | |
|:--|:--|
| **Keyboard** | [TOTEM](https://github.com/GEIGEIGEIST/TOTEM) — 38-key columnar stagger split |
| **MCU** | Seeeduino XIAO BLE (nRF52840) |
| **Firmware** | [ZMK](https://zmk.dev/) main branch (Zephyr 4.1) |
| **Studio** | Enabled on left half — edit keymap live at [zmk.studio](https://zmk.studio/) |

---

## Getting the Firmware

Firmware builds automatically via GitHub Actions on every push.

1. Go to the [Actions](../../actions) tab
2. Open the latest successful **Build ZMK firmware** run
3. Download the `totem_left` and `totem_right` artifacts (`.uf2` files)

### Flashing

1. Double-tap the reset button on the XIAO BLE to enter bootloader mode
2. A USB drive will appear — drag the `.uf2` file onto it
3. Flash left half first (`totem_left`), then right (`totem_right`)

### ZMK Studio (Live Editing)

Connect the left half via USB, open [zmk.studio](https://zmk.studio/), and edit your keymap in real time — no reflashing needed.

---

## Repository Structure

```
├── config/
│   ├── totem.keymap        # Keymap definition
│   ├── totem.conf          # Firmware config options
│   └── west.yml            # ZMK module manifest
├── boards/shields/totem/   # Board shield definition
├── keymap-drawer/          # Auto-generated keymap diagrams
│   ├── config.yaml         # Diagram styling config
│   ├── totem.yaml          # Parsed keymap data
│   └── totem.svg           # Visual keymap diagram
├── build.yaml              # GitHub Actions build matrix
└── .github/workflows/
    ├── build.yml            # Firmware build workflow
    └── draw-keymaps.yml     # Keymap diagram generator
```

---

## Credits

- [TOTEM](https://github.com/GEIGEIGEIST/TOTEM) keyboard by GEIGEIGEIST
- [Miryoku](https://github.com/manna-harbour/miryoku) layout by Manna Harbour
- [ZMK Firmware](https://zmk.dev/)
- [keymap-drawer](https://github.com/caksoylar/keymap-drawer) by caksoylar
