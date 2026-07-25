# Midnight Flux

Midnight Flux is a chromatic, atmospheric Discord theme framework built on
[Midnight by refact0r](https://github.com/refact0r/midnight-discord).

## Architecture

```text
refact0r Midnight
        |
Midnight Flux Core
        |
Flavor
```

- `midnight-flux.css` contains shared structure, behavior, and the palette engine.
- `flavors/` contains the installable flavor entry points.
- `assets/hd/` contains 1920 x 1080 backgrounds.
- `assets/2k/` contains 2560 x 1440 backgrounds.
- `assets/4k/` contains 3840 x 2160 backgrounds.
- `cyberpunk-*.css` files are preserved legacy references.

A structural fix belongs in the core. A flavor should contain only its palette,
background choices, glow colors, and genuinely flavor-specific tuning.

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

## Installation

Import or download the desired file from `flavors/`. Each flavor imports the
shared core automatically.

## Background resolution

Every flavor exposes three hosted background variables and defaults to HD:

```css
body {
    --flux-background-hd: url("https://codekarstenj.github.io/midnight-flux/assets/hd/purple-neon.jpg");
    --flux-background-2k: url("https://codekarstenj.github.io/midnight-flux/assets/2k/purple-neon.jpg");
    --flux-background-4k: url("https://codekarstenj.github.io/midnight-flux/assets/4k/purple-neon.jpg");

    --cyber-background-image-url: var(--flux-background-hd);
}
```

Change only the final variable to select another tier:

```css
--cyber-background-image-url: var(--flux-background-2k);
```

The files share the same flavor name in every resolution folder; the directory
is the resolution identifier.

## Palette API

Most of a flavor's complete Midnight palette is generated from six primitives:

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

Individual `--cyber-*` colors can still be overridden when a flavor needs a
deliberate exception.

## Component API

```css
body {
    --cyber-panel-border-radius: 12px;
    --cyber-sidebar-opacity: 0.72;
    --cyber-chat-opacity: 0.70;
    --cyber-memberlist-opacity: 0.72;
}
```

Opacity ranges from `0` (transparent) to `1` (opaque) and affects panel
backgrounds without fading their contents.
