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
