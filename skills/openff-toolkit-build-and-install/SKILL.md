---
name: openff-toolkit-build-and-install
description: This skill should be used when users ask about build and install in openff-toolkit; it prioritizes documentation references and then source inspection only for unresolved details.
---

# openff-toolkit: Build and Install

## High-Signal Playbook

### Route Conditions
- Use this skill for environment setup, package installation method, optional toolkit dependencies, and install verification (`docs/installation.md`).
- Route registry precedence and wrapper-selection questions to `openff-toolkit-api-and-scripting` (`docs/api/toolkits.md`).
- Route notebook workflow and example execution issues to `openff-toolkit-examples-and-tutorials` (`examples/README.md`).

### Triage Questions
- Is this a standard user install or a source/development install?
- Can the user use `mamba`/conda-forge, or do they need source installation?
- Do they need full `openff-toolkit` or `openff-toolkit-base` with custom optional toolkits?
- Is OpenEye needed, and if yes is a license available?
- Which operating system and Python environment manager are in use?
- Do they need deterministic toolkit behavior across machines?

### Canonical Workflow
1. Create an isolated environment with conda-forge packages (`docs/installation.md`).
2. Activate the environment before any imports.
3. Install `openff-toolkit` (or source install with `python -m pip install .` if required).
4. Install optional OpenEye toolkits only if workflow requires them.
5. Verify toolkit availability through `GLOBAL_TOOLKIT_REGISTRY.registered_toolkit_versions`.
6. If behavior differs across machines, pin toolkit set and version family, then re-check registered toolkits.

### Minimal Working Example
```bash
mamba create -n openff-toolkit -c conda-forge openff-toolkit
mamba activate openff-toolkit
python - <<'PY'
from openff.toolkit import GLOBAL_TOOLKIT_REGISTRY
print(GLOBAL_TOOLKIT_REGISTRY.registered_toolkit_versions)
PY
```

```bash
# Source install path (after dependencies are installed)
cd openff-toolkit
python -m pip install .
```

### Pitfalls and Fixes
- Installed but not activated env: run `mamba activate openff-toolkit` before import checks (`docs/installation.md`).
- Expecting RDKit/AmberTools while using base package only: install full `openff-toolkit` or add optional toolkits explicitly (`docs/installation.md`).
- OpenEye installed but not usable: confirm OpenEye license key is configured (`docs/installation.md`).
- Toolkit-dependent behavior differences in edge molecules: reproduce with a fixed toolkit registry and report unexpected differences (`docs/installation.md`).
- Legacy dependency assumptions from deprecated examples (e.g., old Gromacs/openmoltools flows): treat deprecated example docs as historical context only (`examples/deprecated/liquid_box/create_mol2_pdb/README.md`).

### Convergence and Validation Checks
- `import openff.toolkit` succeeds in the target environment.
- `GLOBAL_TOOLKIT_REGISTRY.registered_toolkit_versions` lists the expected wrappers.
- At least one external toolkit (RDKit/AmberTools/OpenEye) is available for production tasks.
- If OpenEye is required, OpenEye-dependent calls execute without license/runtime errors.

## Scope
- Handle questions about build, installation, compilation, and environment setup.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/installation.md`
- `examples/deprecated/liquid_box/create_mol2_pdb/README.md`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- If ambiguity remains after docs, inspect `references/source_map.md` and start with the ranked source entry points.
- Cite exact documentation file paths in responses.

## Source entry points for unresolved issues
- `openff/toolkit/utils/toolkits.py` (registry defaults, installed-wrapper discovery)
- `openff/toolkit/utils/toolkit_registry.py` (registry behavior and ordering)
- `openff/toolkit/utils/rdkit_wrapper.py` (RDKit availability and capability edge-cases)
- `openff/toolkit/utils/ambertools_wrapper.py` (AmberTools integration path)
- `openff/toolkit/utils/openeye_wrapper.py` (OpenEye integration and gating)
- `openff/toolkit/_tests/create_molecules.py` (smoke-level molecule construction checks)
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" openff/toolkit`).
