# Project Guidelines

## Development Checklist

Before committing any changes, ensure:

- [ ] `uv run ruff check .` passes with no errors
- [ ] `uv run pytest` passes
- [ ] Code follows conventions below (type hints, frozen models, no Simple Browser)

## Overview

**Soc Ops** — Social Bingo (FastAPI + Jinja2 + HTMX). Server-rendered partials, no SPA.

## Conventions

- Pydantic models use `frozen=True` — update via `model_copy(update={...})`, never mutate
- Pure functions in `game_logic.py`; state mutation only in `GameSession`
- Routes return HTMX component fragments (`components/*.html`) via `hx-post`/`hx-swap`
- Custom CSS utilities in `app/static/css/app.css` — see `.github/instructions/css-utilities.instructions.md`
- Type hints on all signatures; use `X | None` (not `Optional`)
- Tests mirror source: `test_api.py` (routes/TestClient), `test_game_logic.py` (pure functions)
- Never use VS Code Simple Browser — HTMX needs a real browser
- Board is fixed 5×5; `CENTER_INDEX = 12` is the free space

## Design Guide — Harry Potter / Wizarding World Theme

The UI uses a **Harry Potter** aesthetic. All new components must follow this visual language.

### Color Palette (CSS variables in `:root`)
- **Primary accent**: `--hp-maroon` (#740001) — buttons, header bar
- **Gold highlights**: `--hp-gold` (#D3A625), `--hp-gold-light` (#EEBA30) — borders, winning states, text accents
- **Parchment backgrounds**: `--hp-parchment` (#F5E6C8), `--hp-parchment-dark`, `--hp-parchment-deep` — cards, page backgrounds
- **Night sky**: `--hp-midnight` (#0D1B2A) — start screen background
- **Ink text**: `--hp-ink` (#2B1810) — body text color
- **Emerald**: `--hp-emerald` (#1A472A) — secondary accent

### Typography (Google Fonts via CDN in `base.html`)
- **Headings**: "Cinzel Decorative" — ornate medieval serif (`.font-hp-title`)
- **Body**: "Crimson Text" — elegant old-world serif (set on `body`)

### Component Patterns
- **Cards**: Use `.parchment-card` (parchment gradient + gold border + inner glow)
- **Board frame**: Use `.board-frame` (gold-bordered parchment wrapper)
- **Bingo squares**: Use `.sq-unmarked`, `.sq-marked`, `.sq-winning`, `.sq-free`
- **Buttons**: `bg-accent text-white font-hp-title border-2 border-gold shadow-magic`
- **Starry backgrounds**: Add `.stars` class on dark containers for twinkling pseudo-elements
- **Dividers**: Use `.gold-ornament` for decorative gold line separators

### Animations
- `golden-pulse` — subtle gold glow on winning squares
- `magic-appear` — scale+fade entrance for modals
- `twinkle` — star opacity cycling on night sky backgrounds

### Rules
- All colors must use `var(--hp-*)` CSS variables, never raw hex
- Buttons use deep maroon background with gold borders — never blue
- Backgrounds are parchment gradients or night sky — never flat white/gray
- Icons use ⚡ (lightning bolt) — never generic emoji like 🎉
- Marked squares show ⚡ instead of ✓
- Free space text is `"⚡"` (set in `data.py`)
