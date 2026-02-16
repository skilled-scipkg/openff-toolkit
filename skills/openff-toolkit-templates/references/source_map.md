# openff-toolkit source map: Templates

Generated from source roots:
- `docs`
- `openff/toolkit`

Use this map only after exhausting the topic docs in `doc_map.md`.

## Fast source navigation
- `rg -n "autosummary|autodoc|templates_path" docs/conf.py docs/_templates/autosummary/*.rst`
- `rg -n "class ForceField|class ToolkitRegistry" openff/toolkit/typing/engines/smirnoff/forcefield.py openff/toolkit/utils/toolkit_registry.py`

## Function-level source entry points
- `docs/_templates/autosummary/module.rst` | focus: module-page autosummary section layout and recursive module listings.
- `docs/_templates/autosummary/base.rst` | focus: object-page title/header rendering and body structure.
- `docs/_templates/autosummary/class.rst` | focus: class-page inheritance and member presentation defaults.
- `docs/conf.py` | symbols: `templates_path`, autosummary/autodoc config blocks | focus: Sphinx wiring that controls how template edits are applied.
- `openff/toolkit/utils/toolkit_registry.py` and `openff/toolkit/typing/engines/smirnoff/forcefield.py` | symbols: `ToolkitRegistry`, `ForceField` | focus: representative high-traffic API objects to verify generated pages.

## Behavior checks (docs validation)
- `docs/Makefile` | targets: `html` | validates template rendering in a full docs build.

## Quick validation commands
- `sphinx-build -b html docs docs/_build/html -W --keep-going`
- `python -m pytest openff/toolkit/_tests/test_links.py -q`
