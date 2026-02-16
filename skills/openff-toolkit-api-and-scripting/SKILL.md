---
name: openff-toolkit-api-and-scripting
description: This skill should be used when users ask about api and scripting in openff-toolkit; it prioritizes documentation references and then source inspection only for unresolved details.
---

# openff-toolkit: API and Scripting

## High-Signal Playbook

### Route Conditions
- Use this skill for toolkit wrapper usage, registry composition, and script-level control of backend selection (`docs/api/toolkits.md`).
- Use this skill for version-aware behavior checks and API change triage (`docs/releasehistory.md`).
- Route force-field science/modeling choices to `openff-toolkit-inputs-and-modeling`.

### Triage Questions
- Is deterministic toolkit precedence required, or is default global registry acceptable?
- Which wrappers must be present (RDKit, AmberTools, OpenEye, NAGL)?
- Should override scope be local to one call, one script block, or process-global?
- Is there an observed behavior difference between wrappers?
- What toolkit version range is in play, and are there known API-breaking changes?
- Are you depending on deprecated/legacy APIs from older releases?

### Canonical Workflow
1. Inspect currently registered toolkits and versions.
2. Create an explicit `ToolkitRegistry` in preferred wrapper order.
3. Pass that registry (or wrapper instance) via `toolkit_registry=` to sensitive calls.
4. Use `toolkit_registry_manager` for temporary global override blocks.
5. Check `docs/releasehistory.md` for relevant behavior/API changes.
6. Lock in tests that run against intended wrapper combinations.

### Minimal Working Example
```python
from openff.toolkit import (
    Molecule,
    ToolkitRegistry,
    RDKitToolkitWrapper,
    AmberToolsToolkitWrapper,
)

registry = ToolkitRegistry([RDKitToolkitWrapper, AmberToolsToolkitWrapper])
mol = Molecule.from_smiles("Cc1ccccc1")
print(registry.call("to_smiles", mol))
```

```python
from openff.toolkit import GLOBAL_TOOLKIT_REGISTRY
from openff.toolkit.utils import toolkit_registry_manager

print(len(GLOBAL_TOOLKIT_REGISTRY.registered_toolkits))
with toolkit_registry_manager(registry):
    print(len(GLOBAL_TOOLKIT_REGISTRY.registered_toolkits))
```

### Pitfalls and Fixes
- Wrapper precedence assumptions hidden in defaults: always make registry order explicit for reproducible scripts (`docs/api/toolkits.md`).
- API drift across releases: check release notes before copying old examples (`docs/releasehistory.md`).
- Reliance on removed/renamed API surfaces (e.g., internalized networkx helper path in 0.18.0): update calls to supported public methods (`docs/releasehistory.md`).
- Silent semantic differences in edge chemistry across wrappers: compare outputs under fixed wrappers and pin behavior in tests (`docs/api/toolkits.md`, `docs/releasehistory.md`).
- Legacy dependency assumptions (e.g., old force-field package expectations): verify against current release notes (`docs/releasehistory.md`).

### Convergence and Validation Checks
- Registry contents and order match intended backend policy.
- Critical calls produce stable output under selected wrapper set.
- No script path relies on APIs marked changed/removed in the release history for target version.
- CI/test matrix covers at least one realistic wrapper combination used in production.

## Scope
- Handle questions about language bindings, APIs, and programmatic interfaces.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/api/toolkits.md`
- `docs/releasehistory.md`
- `docs/_templates/autosummary/class.rst`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- If ambiguity remains after docs, inspect `references/source_map.md` and start with the ranked source entry points.
- Cite exact documentation file paths in responses.

## Source entry points for unresolved issues
- `openff/toolkit/utils/toolkits.py` (registry, wrappers, manager behavior)
- `openff/toolkit/utils/toolkit_registry.py` (dispatch/search semantics)
- `openff/toolkit/utils/rdkit_wrapper.py` (RDKit-specific API surface)
- `openff/toolkit/utils/openeye_wrapper.py` (OpenEye-specific API surface)
- `openff/toolkit/utils/ambertools_wrapper.py` (AmberTools integration)
- `openff/toolkit/_tests/test_toolkits.py` (behavioral contract across wrappers)
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" openff/toolkit`).
