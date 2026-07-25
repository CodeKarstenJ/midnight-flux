# Midnight Flux

Midnight Flux is a chromatic, atmospheric Discord theme framework built on
[Midnight by refact0r](https://github.com/refact0r/midnight-discord).

## Development structure

- `midnight-flux.css` is the shared structural core.
- `midnight-flux-*.theme.css` files are flavor entry points.
- `assets/` contains source and optimized flavor artwork.
- `cyberpunk-*.css` files are preserved legacy references and are not edited.

The dependency chain is intentionally one-way:

```text
refact0r Midnight
        ↓
Midnight Flux Core
        ↓
Flavor
```

A structural fix belongs in the core. A flavor should contain only its
palette, background, glow colors, and genuinely flavor-specific tuning.

## Flavors

- Purple Neon
- Crimson Raven
- Ice
- Emerald
- Amber
- Obsidian
- Matrix
- Synthwave
- Ocean
- Arctic

## Palette API

Most of a flavor's complete Midnight palette is generated from six readable
primitives:

```css
:root {
    --flux-primary-hue: 296;
    --flux-secondary-hue: 258;
    --flux-tertiary-hue: 326;
    --flux-surface-hue: 274;
    --flux-surface-saturation: 42%;
    --flux-accent-saturation: 90%;
}
```

Any individual `--cyber-*` color can still be overridden after these values
when a flavor needs a deliberate exception.

## Component API

The initial shared component controls are:

```css
body {
    --cyber-panel-border-radius: 12px;
    --cyber-sidebar-opacity: 0.72;
    --cyber-chat-opacity: 0.70;
    --cyber-memberlist-opacity: 0.72;
}
```

Opacity values range from `0` (transparent) to `1` (opaque). They affect panel
backgrounds without fading panel contents.

The `--cyber-*` prefix is retained during development for compatibility with
the original theme. A future namespace migration can add aliases without
breaking existing flavors.

## Background system

`assets/sources/purple-neon-4k.jpg` is the canonical composition. Every flavor
uses the same flowing-line composition with a flavor-specific recolor.

Each development flavor keeps its optimized 1920×1080 asset URL commented
beside an active embedded JPEG data URL. This works around Electron's local
file restrictions while preserving a readable pointer to the editable asset.

Hosted releases can offer three performance tiers:

```text
assets/
  *-1920x1080.jpg       1080p
  2k/*-2560x1440.jpg    QHD / 2K
  4k/*-3840x2160.jpg    UHD / 4K
```

The 2K and 4K files are intentionally not embedded in the development themes.
