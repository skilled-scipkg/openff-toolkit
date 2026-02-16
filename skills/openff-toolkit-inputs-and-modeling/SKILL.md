---
name: openff-toolkit-inputs-and-modeling
description: This skill should be used when users ask about inputs and modeling in openff-toolkit; it prioritizes documentation references and then source inspection only for unresolved details.
---

# openff-toolkit: Inputs and Modeling

## High-Signal Playbook

### Route Conditions
- Use this skill for SMIRNOFF/OFFXML-based parameterization, force-field editing, and system setup choices (`docs/users/smirnoff.md`, `docs/typing.rst`).
- Route conversion and hierarchy metadata behavior to `openff-toolkit-users` (`docs/users/molecule_conversion.md`).
- Route runnable cookbook paths to `openff-toolkit-examples-and-tutorials` (`examples/README.md`).

### Triage Questions
- What is the molecular input form (SMILES/SDF/MOL2/PDB) and target output (`System`, `Interchange`, or exported engine files)?
- Which OFFXML force field and SMIRNOFF version are being used?
- Is the workflow small-molecule only, or mixed protein-ligand (OpenFF + Amber)?
- Are you editing parameters (`ParameterType`/`ParameterHandler`) or only applying defaults?
- Is this vacuum or periodic/solvated setup?
- Do you need a reproducibility check against another parametrization route?

### Canonical Workflow
1. Load molecule(s) and create/inspect conformers as needed.
2. Load SMIRNOFF force field data into `ForceField`.
3. Optionally inspect or modify parameters before assignment.
4. Build topology and create a parametrized system.
5. Validate with energy comparison or assigned-parameter inspection.
6. For mixed biomolecular systems, combine OpenFF and Amber-parameterized components using the documented ParmEd workflows.

### Minimal Working Example
```python
from openff.toolkit import Molecule, ForceField

mol = Molecule.from_smiles("CCO")
mol.generate_conformers(n_conformers=1)
ff = ForceField("openff-2.1.0.offxml")
top = mol.to_topology()
system = ff.create_openmm_system(topology=top)
print(system.getNumParticles())
```

```bash
python examples/conformer_energies/conformer_energies.py -f ruxolitinib_conformers.sdf
```

### Pitfalls and Fixes
- New OFFXML with old toolkit: upgrade toolkit to match SMIRNOFF spec version expectations (`docs/users/smirnoff.md`).
- Assuming atom types instead of SMIRKS hierarchy: inspect SMIRKS-mapped parameters and map indices (`docs/users/smirnoff.md`).
- Editing parameters without re-validating energy impact: rerun conformer/system energy checks (`examples/forcefield_modification/README.md`).
- Mixed protein-ligand setup confusion: follow the documented OpenFF-ligand + Amber-protein combination route (`examples/using_smirnoff_with_amber_protein_forcefield/README.md`).
- Deprecated workflows relying on older names (e.g., historical smirnoff99Frosst): migrate to current released OpenFF force fields (`docs/releasehistory.md`).

### Convergence and Validation Checks
- `ForceField` loads without SMIRNOFF/version errors.
- Parameter assignment completes for all intended molecules.
- Energy differences after parameter edits are intentional and explained.
- For mixed systems, combined structure/system can be exported or simulated end-to-end.
- Nonbonded setup is consistent with documented intended methods (`docs/users/developing.md` table).

## Scope
- Handle questions about inputs, system setup, models, and physical parameterization.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/users/smirnoff.md`
- `docs/typing.rst`
- `examples/forcefield_modification/README.md`
- `examples/conformer_energies/README.md`
- `examples/using_smirnoff_with_amber_protein_forcefield/README.md`
- `examples/toolkit_showcase/README.md`
- `examples/deprecated/mixedFF_structure/README.md`
- `examples/deprecated/SMIRNOFF_comparison/README.md`
- `examples/deprecated/host_guest_simulation/README.md`
- `docs/index.md`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- If ambiguity remains after docs, inspect `references/source_map.md` and start with the ranked source entry points.
- Cite exact documentation file paths in responses.

## Source entry points for unresolved issues
- `openff/toolkit/typing/engines/smirnoff/forcefield.py` (ForceField load/assignment path)
- `openff/toolkit/typing/engines/smirnoff/parameters.py` (parameter objects, handler-level logic)
- `openff/toolkit/typing/engines/smirnoff/io.py` (SMIRNOFF serialization/deserialization)
- `openff/toolkit/typing/engines/smirnoff/plugins.py` (plugin/extension registration)
- `openff/toolkit/_tests/test_forcefield.py` (expected ForceField behavior)
- `openff/toolkit/_tests/test_energies.py` (energy comparison regression checks)
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" openff/toolkit`).
