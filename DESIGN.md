# Design System — Apple-Inspired

A minimal, refined design language based on Apple's Human Interface Guidelines.  
All components on this site follow these rules consistently.

---

## 1. Typography

### Font Stack
```
Primary:   "SF Pro Display", "SF Pro Text", -apple-system, BlinkMacSystemFont, "Helvetica Neue", Arial, sans-serif
Monospace: "SF Mono", ui-monospace, "Cascadia Code", "Fira Code", monospace
```

### Scale
| Token       | Size   | Weight | Line Height | Usage                    |
|-------------|--------|--------|-------------|--------------------------|
| `display`   | 56px   | 700    | 1.07        | Hero headline            |
| `title-1`   | 36px   | 700    | 1.1         | Section headings         |
| `title-2`   | 24px   | 600    | 1.2         | Card / sub-section heads |
| `title-3`   | 20px   | 600    | 1.3         | Labels, card titles      |
| `body`      | 17px   | 400    | 1.6         | Body copy                |
| `callout`   | 15px   | 400    | 1.55        | Supporting text          |
| `caption`   | 12px   | 400    | 1.4         | Meta, badges             |

### Rules
- Headlines are tight: `letter-spacing: -0.02em` at display/title-1.
- Body text is always `#1d1d1f` on light, `#f5f5f7` on dark.
- Never use more than 3 font weights on one page.

---

## 2. Color

### Light Mode Palette
| Token              | Value     | Usage                              |
|--------------------|-----------|------------------------------------|
| `--bg`             | `#ffffff`  | Page background                   |
| `--bg-secondary`   | `#f5f5f7`  | Section / card backgrounds        |
| `--bg-tertiary`    | `#e8e8ed`  | Dividers, subtle fills            |
| `--text-primary`   | `#1d1d1f`  | Primary text                      |
| `--text-secondary` | `#6e6e73`  | Supporting text, captions         |
| `--text-tertiary`  | `#aeaeb2`  | Placeholders, disabled            |
| `--accent`         | `#0071e3`  | Interactive elements, links       |
| `--accent-hover`   | `#0077ed`  | Hover state of accent             |
| `--accent-tint`    | `#e8f0fb`  | Badge backgrounds, chip fills     |
| `--danger`         | `#ff3b30`  | Errors, destructive actions       |
| `--success`        | `#34c759`  | Confirmations, positive states    |

### Dark Mode Palette
| Token              | Value     |
|--------------------|-----------|
| `--bg`             | `#000000` |
| `--bg-secondary`   | `#1c1c1e` |
| `--bg-tertiary`    | `#2c2c2e` |
| `--text-primary`   | `#f5f5f7` |
| `--text-secondary` | `#aeaeb2` |
| `--accent`         | `#2997ff` |
| `--accent-tint`    | `#1a2f4a` |

Dark mode is activated via `@media (prefers-color-scheme: dark)` — no JS required.

---

## 3. Spacing

Based on an 8px base unit. Always use multiples.

| Token  | Value | Usage                           |
|--------|-------|---------------------------------|
| `--s1` | 4px   | Micro gaps (icon ↔ label)       |
| `--s2` | 8px   | Tight internal padding          |
| `--s3` | 12px  | Small component padding         |
| `--s4` | 16px  | Default padding                 |
| `--s5` | 24px  | Card padding, section sub-gaps  |
| `--s6` | 32px  | Section rhythm                  |
| `--s7` | 48px  | Large vertical gaps             |
| `--s8` | 64px  | Section padding-top             |
| `--s9` | 96px  | Hero / landing spacing          |

---

## 4. Border Radius

| Token       | Value  | Usage                              |
|-------------|--------|------------------------------------|
| `--r-sm`    | 8px    | Badges, chips, small tags          |
| `--r-md`    | 14px   | Cards, inputs, buttons             |
| `--r-lg`    | 20px   | Containers, large cards            |
| `--r-xl`    | 28px   | Modals, sheets                     |
| `--r-full`  | 9999px | Pills, avatars, circular elements  |

---

## 5. Shadows

Apple uses soft, diffuse shadows with low opacity — never hard box-shadows.

| Token         | Value                                           | Usage               |
|---------------|-------------------------------------------------|---------------------|
| `--shadow-sm` | `0 1px 4px rgba(0,0,0,.06)`                    | Subtle card lift    |
| `--shadow-md` | `0 4px 20px rgba(0,0,0,.10)`                   | Cards, dropdowns    |
| `--shadow-lg` | `0 12px 40px rgba(0,0,0,.14)`                  | Overlays, modals    |

In dark mode, replace shadows with `1px solid rgba(255,255,255,.08)` borders — shadows disappear on dark backgrounds.

---

## 6. Navigation

- **Sticky frosted glass bar**: `backdrop-filter: blur(20px) saturate(180%)`, semi-transparent background.
- Height: 52px on desktop, 48px on mobile.
- Brand name on the left, links on the right — right-aligned, no underline.
- Active/hover: `--accent` color, no background highlight.
- Font: `callout` size, weight 500.

---

## 7. Buttons

### Primary
- Background: `--accent`
- Text: white, weight 600, 15px
- Padding: `10px 20px`
- Border-radius: `--r-full`
- Hover: brightness(1.08), subtle scale(1.02)

### Secondary (Ghost)
- Background: `--bg-secondary`
- Text: `--text-primary`, weight 600
- Border: none
- Same padding and radius as Primary

### Outline
- Background: transparent
- Border: `1.5px solid --accent`
- Text: `--accent`

All buttons: `transition: all 0.2s ease`, no hard borders on Primary.

---

## 8. Cards

- Background: `--bg-secondary` (or `--bg` with shadow on dark)
- Border-radius: `--r-lg`
- Padding: `--s5` (`24px`)
- Shadow: `--shadow-md`
- Hover: `translateY(-4px)` + `--shadow-lg`, transition `0.25s ease`
- No hard borders — use shadow + background contrast instead

---

## 9. Hero / Header

- Full-width gradient or solid background using the palette
- Avatar: 120px circle, `border: 3px solid rgba(255,255,255,.25)`, `--r-full`
- Display headline, subtitle in callout size, CTA buttons below
- Generous vertical padding: `--s9` top and bottom

---

## 10. Accessibility

- All interactive elements have visible `:focus-visible` outlines: `3px solid --accent`, `outline-offset: 3px`
- Color contrast ≥ 4.5:1 for body text, ≥ 3:1 for large text (WCAG AA)
- `aria-label` on icon-only buttons
- `role` and `aria-labelledby` on all landmark regions
- Skip-to-main-content link as first focusable element
- Respect `prefers-reduced-motion`: remove transitions/animations when set

---

## 11. Responsive Breakpoints

| Name     | Width      | Notes                           |
|----------|------------|---------------------------------|
| Mobile   | < 600px    | Single column, stacked nav      |
| Tablet   | 600–1024px | 2-column grids                  |
| Desktop  | > 1024px   | Full layout, max-width 900px    |

Max content width: **900px**, centered with `margin: 0 auto`.
