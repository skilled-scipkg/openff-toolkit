---
name: openff-toolkit-advanced-topics
description: Consolidated advanced and narrow one-doc topics for openff-toolkit; use after core skills when requests involve developer internals, topology internals, utility internals, or the standalone simulation-workflow example.
---

# openff-toolkit: Advanced Topics

## High-Signal Playbook

### Route Conditions
- Use this skill after first-pass triage when the request is about contributor internals, topology internals, utility internals, or the single simulation workflow notebook.
- Route force-field editing/modeling to `openff-toolkit-inputs-and-modeling`.
- Route backend wrapper precedence/registry behavior to `openff-toolkit-api-and-scripting`.

### Triage Questions
- Is the user blocked on topology translation (`from_pdb`, `from_openmm`, `to_openmm`)?
- Is the issue in utility serialization/collection behavior?
- Is the request about preparing a first runnable simulation from toolkit objects?
- Is the answer expected to be docs-only or code-behavior verified?

### Canonical Workflow
1. Pick the matching advanced bucket doc first.
2. Run a minimal reproducible command with packaged inputs.
3. Validate a concrete checkpoint (particle count, hierarchy metadata, serialization round trip).
4. Use `references/source_map.md` for function-level code and test entry points only when docs are insufficient.

### Minimal Working Example
```bash
python - <<'PY'
from openff.toolkit import Molecule, ForceField

mol = Molecule.from_smiles("CCO")
mol.generate_conformers(n_conformers=1)
ff = ForceField("openff-2.1.0.offxml")
system = ff.create_openmm_system(mol.to_topology())
print(system.getNumParticles())
PY
```

### Validation checkpoints
- `ForceField` load succeeds with no SMIRNOFF/version errors.
- Generated system particle count is non-zero and stable across reruns.
- Topology conversion preserves expected hierarchy metadata where provided.

## Primary documentation references
- `docs/users/developing.md`
- `examples/SMIRNOFF_simulation/README.md`
- `docs/topology.md`
- `docs/utils.rst`

## Workflow
- Start with the exact doc for the matched advanced bucket.
- If details are missing, inspect `references/doc_map.md` for inventory context.
- If behavior details are still ambiguous, inspect `references/source_map.md` and open the listed implementation entry points.
- Cite exact documentation file paths in responses.

## Source entry points for unresolved issues
- `openff/toolkit/typing/engines/smirnoff/forcefield.py` (simulation/system creation internals)
- `openff/toolkit/topology/topology.py` (topology object behavior)
- `openff/toolkit/topology/molecule.py` (molecule representation and conversion internals)
- `openff/toolkit/utils/utils.py` (misc utility functions)
- `openff/toolkit/utils/serialization.py` (serialization interfaces)
- `openff/toolkit/utils/collections.py` (validated collection types)
- `openff/toolkit/_tests/test_topology.py` (topology behavior regressions)
- `openff/toolkit/_tests/test_utils.py` (utility behavior regressions)
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" openff/toolkit`).
