# Copilot Instructions

## Mandatory Development Checklist
Before submitting any changes, ensure the following steps are completed:
1. **Lint**: Run `uv run ruff check .` and fix all linting issues.
2. **Build**: Verify the project builds successfully.
3. **Test**: Run `uv run pytest` and ensure all tests pass.

---

## Instructions for Development

### General Guidelines
- Follow the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
- Use Python 3.13+ and ensure all dependencies are installed via `uv sync`.

### Workflow
1. **Setup**: Install dependencies and verify the environment.
2. **Development**: Use the provided tasks for linting, testing, and running the server.
3. **Testing**: Write and run tests for all new features or changes.
4. **Submission**: Ensure the mandatory checklist is completed before submitting a pull request.

### Notes
- Avoid using the VS Code Simple Browser for previews; use a full browser instead.
- Refer to the [README.md](../README.md) for additional context.

---

## Design Guide

### Aesthetic
**Arctic / Glacial / Polar Night.** The UI evokes deep sea ice, frozen tundra, and polar darkness. All design decisions should reinforce cold, technical precision — not warmth, softness, or generic tech.

### Color Tokens
All colors are defined as CSS custom properties in `app/static/css/app.css`. **Never hardcode hex values in templates — always use a token.**

| Token | Value | Usage |
|---|---|---|
| `--bg-void` | `#01080f` | Document background |
| `--bg-deep` | `#030d1c` | Gradient layer |
| `--surface` | `rgba(5,20,50,0.65)` | Frosted glass cards |
| `--surface-raised` | `rgba(8,28,65,0.78)` | Elevated panels, modal |
| `--surface-header` | `rgba(2,8,26,0.82)` | Sticky header bar |
| `--accent` | `#00d4ff` | Glacial cyan — primary CTA, icons |
| `--accent-dark` | `#009fcc` | Pressed/hover state of accent |
| `--text-primary` | `#c8e8ff` | Body text |
| `--text-secondary` | `#5a9abf` | Labels, subtitles |
| `--text-dim` | `#2b546e` | Hints, placeholders |
| `--border-ice` | `rgba(130,210,255,0.14)` | Default card borders |
| `--border-active` | `rgba(0,200,255,0.50)` | Active / focused borders |
| `--marked-bg` | `rgba(0,52,72,0.88)` | Marked bingo square bg |
| `--marked-border` | `rgba(0,200,255,0.58)` | Marked bingo square border |
| `--win-bg` | `rgba(72,44,0,0.88)` | Winning square bg (warm contrast) |
| `--win-border` | `rgba(255,188,0,0.68)` | Winning square border |
| `--win-text` | `#ffe082` | Winning square text |

### Typography
| Token | Font | Usage |
|---|---|---|
| `--font-display` | `Orbitron` | Logo, BINGO heading, section labels |
| `--font-body` | `Exo 2` | All other text |

- **Never** use system fonts, Inter, Roboto, Arial, or Space Grotesk.
- Orbitron should be used sparingly — only for brand/display moments.
- Exo 2 covers all body, UI labels, and instructional text.

### Surfaces & Depth
- All cards and panels use `backdrop-filter: blur(12px–18px)` frosted glass.
- Use the `.glass` class for standard surfaces and `.glass-raised` for elevated elements (modals, popovers).
- Layer depth via border opacity: `--border-ice` (default) → `--border-active` (focused).

### Background
The body background is a 7-layer CSS composite (no images):
1. Four corner aurora radial glows (`rgba` blues/teals)
2. Deep space `linear-gradient`
3. Two intersecting diagonal `repeating-linear-gradient` ice-crystal hairline grids

Do not replace this with a solid color or image. Extend it by adding radial layers if needed.

### Component Classes
| Class | Purpose |
|---|---|
| `.btn-arctic` | Primary CTA — glacial cyan gradient + glow aura |
| `.btn-ghost` | Secondary/back button — ghost with hover frost |
| `.glass` | Standard frosted surface card |
| `.glass-raised` | Elevated frosted panel (modal card) |
| `.board-square` | Bingo grid cell — base dark glass style |
| `.board-square.is-marked` | Teal glow state |
| `.board-square.is-winning` | Amber/gold glow state (warm contrast) |
| `.board-square.is-free` | Free space — cyan ❄ icon, no interaction |
| `.arctic-header` | Sticky frosted top bar |
| `.bingo-banner` | Amber gradient notification strip |
| `.modal-overlay` | Full-screen dim backdrop for modal |
| `.start-screen` | Centered column layout for start page |

### Animations
- **Start screen elements** use staggered `fadeSlideUp` with `anim-1` / `anim-3` / `anim-4` delay classes.
- **Modal** uses `backdropFadeIn` (overlay) + `modalPop` spring (`cubic-bezier(0.34, 1.56, 0.64, 1)`) on the card.
- Keep animations CSS-only. Do not add JavaScript animation libraries.

### Adding New UI
1. Use existing tokens — do not introduce new hardcoded colors.
2. New surfaces should use `.glass` or `.glass-raised`.
3. New accent elements should use `--accent` + `box-shadow: 0 0 20px var(--accent-glow)`.
4. New buttons follow `.btn-arctic` (primary) or `.btn-ghost` (secondary) patterns.
5. Add any new reusable utility classes to `app/static/css/app.css` following the existing section structure.
