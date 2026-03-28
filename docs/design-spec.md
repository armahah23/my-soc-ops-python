# Soc Ops — Arctic UI Design Spec

> **Aesthetic**: Glacial / Polar Night / Deep Sea Ice  
> **Status**: v1.0 — Full frontend redesign complete

---

## 1. Design Philosophy

The theme is **absolute cold**. Not cyberpunk purple. Not warm startup blue. This is -40°C tundra, polar night, deep ocean trenches where bioluminescent light is the only source of colour. Every design decision reinforces that single feeling.

The tension that makes the game come alive: **cold everywhere except where you win**. Marked squares glow teal — present but frozen. Winning squares glow warm amber — a single flame in a blizzard. That contrast is the emotional pay-off of the game.

---

## 2. Colour Palette

| Token | Value | Use |
|---|---|---|
| `--bg-void` | `#01080f` | Document background base |
| `--bg-deep` | `#030d1c` | Gradient target |
| `--surface` | `rgba(5,20,50,0.65)` | Frosted glass cards |
| `--surface-raised` | `rgba(8,28,65,0.78)` | Modal, elevated glass |
| `--surface-header` | `rgba(2,8,26,0.82)` | Navigation header |
| `--border-ice` | `rgba(130,210,255,0.14)` | Default hairline borders |
| `--border-active` | `rgba(0,200,255,0.50)` | Active / focused elements |
| `--accent` | `#00d4ff` | Glacial cyan — primary accent |
| `--text-primary` | `#c8e8ff` | Main body text (ice white) |
| `--text-secondary` | `#5a9abf` | Subdued labels (frost blue) |
| `--text-dim` | `#2b546e` | Hint text (barely visible) |
| `--marked-bg` | `rgba(0,52,72,0.88)` | Marked square background |
| `--marked-border` | `rgba(0,200,255,0.58)` | Marked square border |
| `--win-bg` | `rgba(72,44,0,0.88)` | Winning square — warm contrast |
| `--win-border` | `rgba(255,188,0,0.68)` | Winning square border (gold) |
| `--win-text` | `#ffe082` | Winning square text |

### Background Layering Order (applied on `body`)
1. Four radial aurora glows at document corners (subtle blues/teals)
2. `linear-gradient(160deg, void → deep)` base gradient
3. Two crossing `repeating-linear-gradient` hairlines at ±45° creating an ice-crystal diamond grid (opacity ~0.022 — invisible until high-contrast mode, subliminal otherwise)

---

## 3. Typography

| Role | Font | Weight | Usage |
|---|---|---|---|
| Display / Logo | **Orbitron** | 900 | "SOC OPS" title, BINGO text, banner labels |
| Display / Nav | **Orbitron** | 400–600 | Header name, how-to-play label |
| Body | **Exo 2** | 300–700 | All prose, board squares, instructions |

**Rationale**: Orbitron is angular, geometric, cold — it reads like something etched into permafrost. Exo 2 has slight futuristic edges without the sci-fi excess, keeping readability in small board-square text. System fonts were intentionally avoided — they carry warmth from familiar contexts.

**Logo treatment**: `background-clip: text` gradient `#00dcff → #a8d8ff → #00dcff` + `filter: drop-shadow` glow. This creates the illusion of internal cold light rather than reflected light.

---

## 4. Effects & Interactions

### Frosted Glass
All surface cards use `backdrop-filter: blur()` + semi-transparent backgrounds. This creates depth — you perceive the aurora/grid behind each panel, reinforcing the layered, atmospheric world.

| Component | Blur | Background opacity |
|---|---|---|
| How-to-play card | 14px | 72% |
| Game header | 20px | 82% |
| Modal | 18px | 78% |

### Glow System
- **Default board squares**: No glow. Near-black background, muted ice border.
- **Hover**: Border shifts to `rgba(0,200,255,0.28)`. Subtle — like ice catching a light source.
- **Active press**: `transform: scale(0.94)` + brief cyan glow. Physical depth.
- **Marked**: Teal `box-shadow` outer glow + inset tint. The square is "activated".
- **Winning**: Amber `box-shadow` — the only warm light on screen. Unmissable.

### CTA Button
Glacial cyan gradient with a `drop-shadow` glow aura. On press: `scale(0.96)` + intensified glow. A highlight shimmer layer (`::before` pseudo-element) fades in on press to simulate a light flash across the button face.

---

## 5. Animations

| Animation | Target | Easing | Duration |
|---|---|---|---|
| `fadeSlideUp` (×4 delay steps) | Start screen elements | `ease-out` | 550ms |
| `backdropFadeIn` | Modal overlay | `ease-out` | 220ms |
| `modalPop` | Modal card | Spring `cubic-bezier(0.34,1.56,0.64,1)` | 420ms |

**Stagger delays**: Logo (50ms) → How-to-play (340ms) → CTA button (520ms). Elements feel like they crystallise into place one by one, not all at once.

**Modal spring**: The overshoot `cubic-bezier(0.34, 1.56, 0.64, 1)` gives the BINGO card a slight bounce past scale(1) before settling. This is the one moment of warmth/celebration in the otherwise cold UI.

---

## 6. Screen Inventory

### Start Screen (`start_screen.html`)
- Centred vertical stack
- `::before` pseudo-element overhead bloom (radial glow, 260px tall, deep blue)
- Logo lockup: title + subtitle + 48px cyan hairline rule
- How-to-play glass card with `◈` icon markers and hairline row dividers
- Full-width CTA button with ❄ prefix symbol

### Game Screen (`game_screen.html`)
- Frosted header: back button (ghost) + centred `SOC OPS` wordmark (Orbitron 0.72rem) + spacer
- Dim hint text (`--text-dim`) beneath header
- Optional amber BINGO banner: fades in via gradient edges, Orbitron caps
- Board occupies remaining flex space, centred

### Bingo Board (`bingo_board.html`)
- 5×5 `aspect-square` grid
- Each cell is `.board-square` — a component class not a utility soup
- Three state classes: `is-marked`, `is-winning`, `is-free`
- Free space renders `❄` with cyan glow filter instead of text
- Checkmark pip (`.sq-check`) in top-right of marked squares; colour matches state

### Bingo Modal (`bingo_modal.html`)
- Full-screen overlay with `modal-overlay` fade-in
- Frosted glass card with `modal-card` spring pop
- Oversized `❄` with `drop-shadow` glow as icon
- `modal-title`: BINGO text in cold→warm gradient (cyan fading to amber)
- CTA button: same `.btn-arctic` as start screen

---

## 7. Accessibility

- All interactive board squares retain `aria-pressed` and `aria-label`
- Free space `❄` icon has `aria-hidden="true"`; `aria-label="Free space"` on the button
- BINGO banner and modal subtitle convey state in text (not emoji-only)
- `backdrop-filter` degrades gracefully — surface still has semi-transparent fallback background

---

## 8. HTMX & Template Invariants

All HTMX attributes (`hx-post`, `hx-target="#game-container"`, `hx-swap="outerHTML"`) are preserved verbatim. All Jinja2 template logic (`{% for %}`, `{% if %}`, `{{ }}`) is unchanged. The `id="game-container"` outer div is preserved on both `start_screen.html` and `game_screen.html` as the HTMX swap target.

---

## 9. Files Changed

| File | Change |
|---|---|
| `app/static/css/app.css` | Complete rewrite — arctic design system |
| `app/templates/base.html` | Added Google Fonts (Orbitron + Exo 2), updated theme-color |
| `app/templates/components/start_screen.html` | Rewritten with arctic layout + animations |
| `app/templates/components/game_screen.html` | Rewritten with frosted header + bingo banner |
| `app/templates/components/bingo_board.html` | Rewritten with component classes, ❄ free space |
| `app/templates/components/bingo_modal.html` | Rewritten with glass modal + spring animation |
| `app/templates/home.html` | **Untouched** |
| All Python app files | **Untouched** |
