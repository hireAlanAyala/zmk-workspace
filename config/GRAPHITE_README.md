# Graphite Layout Configuration

This configuration implements the **Graphite keyboard layout** for a 3x5 split keyboard (Corne-style).

([Click here](https://raw.githubusercontent.com/hireAlanAyala/zmk-workspace/refs/heads/main/draw/graphite.svg)
for the visual keymap - powered by
[keymap-drawer](https://github.com/caksoylar/keymap-drawer).)

## About Graphite

Graphite is a modern alternative keyboard layout optimized for:
- **Hand alternation**: Maximizes alternating between hands rather than same-hand sequences
- **Low same-finger bigrams**: Minimizes consecutive keystrokes with the same finger
- **Comfortable rolls**: Natural rolling motions when same-hand typing occurs
- **Home row emphasis**: Most common letters on the home row for minimal finger travel

## Layout Overview

### Base Layer (3x5 per split)

**Left Hand:**
```
b  l  d  w  z
n  r  t  s  g
q  x  m  c  v
```

**Right Hand:**
```
'  f  o  u  j
y  h  a  e  i
k  p  .  ,  /
```

### Graphite Shift Layer

The shift layer implements Graphite's shifted characters using mod-morphs:

| Key | Normal | Shifted |
|-----|--------|---------|
| `'` | `'`    | `_`     |
| `.` | `.`    | `>`     |
| `,` | `,`    | `"`     |
| `/` | `/`    | `<`     |

All letter keys shift to uppercase as expected.

### Omitted Characters

Due to the 5-column constraint, the following characters from the 6th column (rightmost) of the full Graphite layout are omitted:
- `;` (semicolon) - available on other layers
- Comma from home row - moved to bottom row for better accessibility

## Features

### Timeless Homerow Mods
- **Home row** (NRTS | HAEI) has modifier keys when held:
  - Left: GUI, Alt, Shift, Ctrl
  - Right: Ctrl, Shift, Alt, GUI
- Uses balanced flavor with positional hold-tap for minimal misfires
- `require-prior-idle-ms` eliminates typing delay

### Magic Shift (Right Thumb)
- **Tap after alpha**: Key repeat
- **Tap after non-alpha**: Sticky shift
- **Hold**: Regular shift
- **Double-tap**: Caps-word

### Smart Layers
- **Nav layer**: Arrow cluster, page navigation, window management
- **Num layer**: Numpad with auto-deactivation (Numword)
- **Fn layer**: Function keys, media controls, desktop management
- **Sys layer**: Bluetooth, bootloader, system reset
- **Mouse layer**: Mouse movement, scrolling, clicks

### Thumb Keys
- **Left thumb**: Space (hold for Nav layer) | Enter (hold for Fn layer)
- **Right thumb**: Smart-Num (Numword) | Magic Shift

## Building

The Graphite configuration is included in `build.yaml`:

```bash
just build graphite
```

Or build all configurations:

```bash
just build all
```

## Files

- **`graphite.keymap`**: Main configuration file (includes graphite_base.keymap)
- **`graphite.conf`**: ZMK config (Bluetooth, sleep timeout, mouse support)
- **`graphite_base.keymap`**: Full layer definitions with Graphite layout
- **`draw/graphite.svg`**: Visual keymap diagram
- **`draw/graphite_config.yaml`**: Keymap-drawer configuration

## Customization

The Graphite layout uses the same base configuration as the other layouts in this repo:
- Combos defined in `combos.dtsi`
- Leader key sequences in `leader.dtsi`
- Mouse emulation in `mouse.dtsi`

All the smart behaviors (timeless HRMs, magic shift, auto-layers) work seamlessly with the Graphite layout.

## Comparison to Vanilla Graphite

This implementation:
- ✅ Matches Graphite base layer (letters)
- ✅ Matches Graphite shift layer (punctuation morphs)
- ✅ Optimized for 3x5 split layout (30 keys)
- ✅ Adds smart behaviors (HRMs, magic shift, auto-layers)
- ⚠️ Omits rightmost column (`;` and `,` from 6th position)
- ✅ Moves comma to bottom row for better accessibility

## Resources

- [Graphite Layout](https://github.com/rdavison/graphite-layout) - Original Graphite layout
- [ZMK Documentation](https://zmk.dev/) - ZMK firmware documentation
- [urob's ZMK Config](https://github.com/urob/zmk-config) - Base configuration this builds upon
