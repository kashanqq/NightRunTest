# CONTEXT

Detected project type(s): python

## Overview
`gamecore`: a pure-Python 2D game core (ECS, tilemap, dungeon generator, A* pathfinding, collisions,
save/load, console simulator). It is also the test project for the nightrun orchestrator: PLAN.md is
executed by agents overnight.

## Tech stack
- Python 3.12+ (3.14 in WSL, 3.15 on Windows), standard library only, no runtime dependencies.
- pytest 9 for tests (installed globally, no virtualenv).

## Structure
- `src/gamecore/` - the package (created by T-001; `ecs/` and `systems/` subpackages come later).
- `tests/` - pytest tests, one `test_<module>.py` per module. `tests/test_harness.py` keeps the baseline green.
- `pyproject.toml` - project metadata and pytest config (`pythonpath = ["src"]`, `testpaths = ["tests"]`). Protected.
- `nightrun.toml` - orchestrator commands and protected paths. Protected.
- `docs/` - agent memory (this file, PROGRESS.md, DECISIONS.md, agents/).

## Build / run / test
- Build (syntax check): `python3 -m compileall -q src tests`
- Tests: `python3 -m pytest -q`
- Simulator (after T-020): `python3 -m gamecore.sim --seed 7`

## Conventions
- Grid cells: x right, y down, origin top-left. `(x, y)` tuples until T-016 introduces `Vec2`.
- Randomness only through `random.Random(seed)` instances.
- No `conftest.py` / `pytest.ini`; do not edit `pyproject.toml`.

## Current state
Scaffold only: no package code yet. See PLAN.md for the task list.
