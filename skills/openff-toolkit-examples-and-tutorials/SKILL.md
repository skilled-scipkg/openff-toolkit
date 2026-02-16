---
name: openff-toolkit-examples-and-tutorials
description: This skill should be used when users ask about examples and tutorials in openff-toolkit; it prioritizes documentation references and then source inspection only for unresolved details.
---

# openff-toolkit: Examples and Tutorials

## High-Signal Playbook

### Route Conditions
- Use this skill when the user asks for runnable examples, notebook starting points, or demonstration workflows (`examples/README.md`, `docs/examples.md`).
- Route conceptual modeling questions to `openff-toolkit-inputs-and-modeling`.
- Route environment and dependency setup blockers to `openff-toolkit-build-and-install`.

### Triage Questions
- Which task type: simulation, conformer energies, force-field modification, parameter inspection, or export to engine files?
- Notebook or CLI/script workflow preferred?
- Are optional dependencies available (ParmEd, visualization stack, external engines)?
- Is a modern example required, or is a deprecated historical example acceptable?
- What input data format is available (SMILES/SDF/PDB)?
- What output artifact is required (plots, energies, `prmtop`/`gro`, trajectory)?

### Canonical Workflow
1. Start from `examples/README.md` and choose the closest maintained example.
2. Open the target example README for exact files/notebooks/scripts.
3. Execute the smallest working path (CLI or notebook) before customization.
4. Swap in user data incrementally.
5. Validate with known checks (energy comparison, parameter assignment inspection, expected output files).
6. Escalate to source only if documentation example behavior is unclear.

### Minimal Working Example
```bash
python examples/conformer_energies/conformer_energies.py -f ruxolitinib_conformers.sdf
```

```text
Notebook workflow anchor:
examples/SMIRNOFF_simulation/run_simulation.ipynb
```

### Pitfalls and Fixes
- Starting from deprecated content without checking age/scope: prefer maintained examples in `examples/README.md` first.
- Assuming all notebooks are CI-validated forever: some ParmEd-dependent external examples were dropped from active testing (`docs/releasehistory.md`).
- Visualization example fails in Jupyter: install/configure `nglview` as documented (`examples/visualization/README.md`).
- Export workflow confusion (OpenMM vs AMBER/GROMACS): use the dedicated conversion example path (`examples/using_smirnoff_in_amber_or_gromacs/README.md`).
- Parameter-debug tasks done by manual inspection only: use assigned-parameter inspection example first (`examples/inspect_assigned_parameters/README.md`).

### Convergence and Validation Checks
- Example runs end-to-end without local edits to library internals.
- Output artifacts exist and are structurally correct (energies reported, expected files written).
- Any adaptation from example to user data changes only inputs, not core workflow semantics.
- For conversion workflows, cross-check energies/structure after format translation.

## Scope
- Handle questions about worked examples, tutorials, and cookbook usage.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `examples/README.md`
- `docs/examples.md`
- `examples/toolkit_showcase/README.md`
- `examples/forcefield_modification/README.md`
- `examples/conformer_energies/README.md`
- `examples/SMIRNOFF_simulation/README.md`
- `examples/inspect_assigned_parameters/README.md`
- `examples/using_smirnoff_in_amber_or_gromacs/README.md`
- `examples/using_smirnoff_with_amber_protein_forcefield/README.md`
- `examples/visualization/README.md`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- If ambiguity remains after docs, inspect `references/source_map.md` and start with the ranked source entry points.
- Cite exact documentation file paths in responses.

## Source entry points for unresolved issues
- `openff/toolkit/typing/engines/smirnoff/forcefield.py` (example parameterization backend)
- `openff/toolkit/typing/engines/smirnoff/parameters.py` (parameter assignment details)
- `openff/toolkit/typing/engines/smirnoff/io.py` (OFFXML parse/write semantics)
- `openff/toolkit/utils/ambertools_wrapper.py` (AmberTools-backed flows used in examples)
- `openff/toolkit/_tests/test_parameters.py` (parameter assignment expectations)
- `openff/toolkit/_tests/test_parameter_plugins.py` (plugin behavior checks)
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" openff/toolkit`).
