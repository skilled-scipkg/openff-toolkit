# openff-toolkit source map: Advanced Topics

Generated from source roots:
- `openff/toolkit`

Use this map only after exhausting the topic docs in `doc_map.md`.

## Fast source navigation
- `rg -n "from_pdb|from_openmm|to_openmm|identical_molecule_groups|hierarchy_iterator" openff/toolkit/topology`
- `rg -n "to_json|from_json|to_yaml|from_yaml|ValidatedList|ValidatedDict" openff/toolkit/utils`
- `rg -n "create_openmm_system|create_interchange" openff/toolkit/typing/engines/smirnoff/forcefield.py`

## Function-level source entry points
- `openff/toolkit/typing/engines/smirnoff/forcefield.py` | symbols: `ForceField.create_openmm_system`, `ForceField.create_interchange` | focus: simulation-system construction internals.
- `openff/toolkit/topology/topology.py` | symbols: `Topology.from_pdb`, `Topology.from_openmm`, `Topology.to_openmm`, `Topology.identical_molecule_groups`, `Topology.hierarchy_iterator` | focus: topology import/export and hierarchy internals.
- `openff/toolkit/topology/molecule.py` | symbols: `Molecule.from_pdb_and_smiles`, `Molecule.perceive_residues`, `Molecule.nth_degree_neighbors` | focus: molecule-level advanced conversion and residue perception.
- `openff/toolkit/utils/serialization.py` | symbols: `Serializable.to_json`, `Serializable.from_json`, `Serializable.to_yaml`, `Serializable.from_yaml` | focus: stable serialization contracts.
- `openff/toolkit/utils/collections.py` | symbols: `ValidatedList`, `ValidatedDict` | focus: validated container behavior for utility-heavy workflows.
- `openff/toolkit/utils/utils.py` | symbols: `get_data_file_path`, `object_to_quantity` | focus: shared helper behavior frequently used in advanced scripts and tests.

## Behavior checks (targeted tests)
- `openff/toolkit/_tests/test_topology.py` | tests: `test_from_pdb`, `test_from_to_openmm_hierarchy_metadata`, `test_identical_molecule_groups_mixed_topology` | validates topology and hierarchy behavior.
- `openff/toolkit/_tests/test_utils_serialization.py` | focus: JSON/YAML and NumPy serialization round trips.
- `openff/toolkit/_tests/test_utils_collections.py` | focus: `ValidatedList`/`ValidatedDict` converter+validator semantics.
- `openff/toolkit/_tests/test_utils.py` | tests: `test_get_data_file_path`, `test_object_to_quantity_accepts_openmm` | validates core utility helpers.

## Quick validation commands
- `pytest openff/toolkit/_tests/test_topology.py -k "from_pdb or hierarchy_metadata or identical_molecule_groups" -q`
- `pytest openff/toolkit/_tests/test_utils_serialization.py -q`
- `pytest openff/toolkit/_tests/test_utils_collections.py -q`
