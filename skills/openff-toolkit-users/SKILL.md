---
name: openff-toolkit-users
description: This skill should be used when users ask about users in openff-toolkit; it prioritizes documentation references and then source inspection only for unresolved details.
---

# openff-toolkit: Users

## High-Signal Playbook

### Route Conditions
- Use this skill for user-facing core concepts, molecule/topology conversion behavior, and virtual-site semantics (`docs/users/concepts.md`, `docs/users/molecule_conversion.md`, `docs/users/virtualsites.md`).
- Route force-field editing and parametrization strategy to `openff-toolkit-inputs-and-modeling`.
- Route wrapper precedence and registry mechanics to `openff-toolkit-api-and-scripting`.

### Triage Questions
- Are you converting `Molecule`/`Topology` to OpenMM, RDKit, or OpenEye?
- Is hierarchy metadata (residue/chain/insertion) complete and internally consistent?
- Do you expect hierarchy metadata to affect parameter assignment?
- Are virtual sites present, and if so which `match` policy (`once` vs `all_permutations`) is desired?
- Do multiple virtual-site parameters intentionally share or differ in `name`?
- Are you validating particle ordering/exclusions after v-site application?

### Canonical Workflow
1. Identify the primary object boundary: `Molecule`, `Topology`, `ForceField`, or `Interchange`.
2. Before conversion, set hierarchy metadata consistently on atoms if downstream package expects it.
3. Convert using the target backend and inspect resulting chain/residue behavior.
4. For virtual sites, define parameters with explicit `name` and `match` intent.
5. Re-run assignment and inspect resulting particle count/order and exclusion behavior.
6. If behavior is backend-specific, isolate using explicit toolkit wrapper selection.

### Minimal Working Example
```python
from openff.toolkit import Molecule

mol = Molecule.from_smiles("CCO")
mol.metadata["residue_name"] = "LIG"
mol.metadata["residue_number"] = "1"
mol.metadata["chain_id"] = "A"
rdmol = mol.to_rdkit()
print(rdmol.GetNumAtoms())
```

```xml
<VirtualSites version="0.3">
  <DivalentLonePair smirks="[#1:1]-[#8X2:2]-[#1:3]" name="EP" match="once" />
</VirtualSites>
```

### Pitfalls and Fixes
- Partial hierarchy metadata leads backend-specific defaults: set residue/chain fields as a coherent set (`docs/users/molecule_conversion.md`).
- Assuming metadata controls parameter assignment: it does not; chemistry controls assignment (`docs/users/molecule_conversion.md`).
- Expecting iterator behavior to define conversion mapping: conversion uses atom-level metadata directly (`docs/users/molecule_conversion.md`).
- Virtual-site collisions with same `name`: last matching parameter wins for that name; use distinct names when you want multiple sites (`docs/users/virtualsites.md`).
- Wrong `match` mode for symmetric patterns (e.g., 4-point water): use `once` to avoid duplicate coincident particles (`docs/users/virtualsites.md`).
- Unsupported intramolecular exclusion policies: only `parents` is currently supported (`docs/users/virtualsites.md`).

### Convergence and Validation Checks
- Converted objects preserve expected chemical graph and atom count.
- Residue/chain metadata in target package matches intended defaults or explicit values.
- Virtual-site parent assignment and site multiplicity match `name`/`match` choices.
- Particle iteration outputs are consistent with expected atom + vsite particle ordering.

## Scope
- Handle questions about documentation grouped under the 'users' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/users/concepts.md`
- `docs/users/molecule_conversion.md`
- `docs/users/virtualsites.md`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- If ambiguity remains after docs, inspect `references/source_map.md` and start with the ranked source entry points.
- Cite exact documentation file paths in responses.

## Source entry points for unresolved issues
- `openff/toolkit/topology/molecule.py` (conversion and metadata handling in molecule object model)
- `openff/toolkit/topology/_mm_molecule.py` (OpenMM-oriented molecule interop paths)
- `openff/toolkit/typing/engines/smirnoff/forcefield.py` (v-site application during assignment)
- `openff/toolkit/_tests/test_molecule.py` (round-trip and conversion expectations)
- `openff/toolkit/_tests/test_mm_molecule.py` (OpenMM boundary behavior)
- `openff/toolkit/_tests/molecule/test_state_enumeration.py` (molecule state assumptions)
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" openff/toolkit`).
