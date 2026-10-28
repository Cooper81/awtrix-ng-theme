# AWTRIX NG Theme for Home Assistant

A dark LED-matrix theme inspired by the AWTRIX / Ulanzi pixel clock.

- Black background with an LED dot grid
- Pixel fonts (VT323 for text, Silkscreen for headings)
- Hard stepped pixel corners and glowing borders
- Blinking "indicator LED" in the top-right corner of every card
- Sections are color-coded automatically: Cyan / Green / Orange / Magenta

No `card_mod` is needed inside your dashboards; the theme styles all cards.

## Installation via HACS

1. **HACS → ⋮ → Custom repositories**, Repository: `https://github.com/Cooper81/awtrix-ng-theme`, Type: **Theme** → Add
2. Search for **AWTRIX NG Theme** and click **Download**
3. Run **Developer Tools → Actions → `frontend.reload_themes`** (or restart Home Assistant)
4. **Profile → Theme** → select `Awtrix NG`

## Prerequisites

1. **[card-mod](https://github.com/thomasloven/lovelace-card-mod)** (HACS → Frontend), additionally loaded as a frontend module:

```yaml
frontend:
  themes: !include_dir_merge_named themes
  extra_module_url:
    - /hacsfiles/lovelace-card-mod/card-mod.js
```

2. The pixel fonts as a dashboard resource (*Settings → Dashboards → ⋮ → Resources → Add Resource*):
   - URL: `https://fonts.googleapis.com/css2?family=Silkscreen:wght@400;700&family=VT323&display=swap`
   - Type: **Stylesheet**

## Customization

The section colors are defined at the top of `themes/awtrix-ng.yaml` as RGB values:

```yaml
awtrix-color-1: '0, 220, 255'   # Cyan
awtrix-color-2: '57, 255, 90'   # Green
awtrix-color-3: '255, 160, 0'   # Orange
awtrix-color-4: '255, 50, 200'  # Magenta
```

Single cards can be recolored with `card_mod`:

```yaml
card_mod:
  style: "ha-card { --awtrix-sec-rgb: 40, 120, 255; }"
```

> The automatic section colors use `:host-context()` (Chrome, Edge, Android app). In Safari/iOS and Firefox all cards use the default accent color (`awtrix-accent-rgb`).

## License

MIT
