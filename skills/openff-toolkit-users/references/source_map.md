# openff-toolkit source map: Users

Generated from source roots:
- `openff/toolkit`

Use this map only after exhausting the topic docs in `doc_map.md`.

## Fast source navigation
- `rg -n "from_pdb_and_smiles|to_rdkit|to_openeye|to_topology|metadata|perceive_residues" openff/toolkit/topology/molecule.py`
- `rg -n "from_pdb|from_openmm|to_openmm|identical_molecule_groups|nth_degree_neighbors" openff/toolkit/topology/topology.py`
- `rg -n "VirtualSiteHandler|label_molecules|create_openmm_system" openff/toolkit/typing/engines/smirnoff`

## Function-level source entry points
- `openff/toolkit/topology/molecule.py` | symbols: `Molecule.from_pdb_and_smiles`, `Molecule.to_rdkit`, `Molecule.to_openeye`, `Molecule.to_topology`, `Molecule.perceive_residues` | focus: molecule conversion and hierarchy metadata behavior.
- `openff/toolkit/topology/topology.py` | symbols: `Topology.from_pdb`, `Topology.from_openmm`, `Topology.to_openmm`, `Topology.nth_degree_neighbors`, `Topology.identical_molecule_groups` | focus: topology conversion and grouping semantics.
- `openff/toolkit/typing/engines/smirnoff/parameters.py` | symbols: `VirtualSiteHandler`, `VirtualSiteHandler.VirtualSiteType` | focus: virtual-site matching policy, naming, and parameter precedence.
- `openff/toolkit/typing/engines/smirnoff/forcefield.py` | symbols: `ForceField.label_molecules`, `ForceField.create_openmm_system` | focus: user-facing parameter assignment and virtual-site application path.
- `openff/toolkit/topology/_mm_molecule.py` | symbols: `_SimpleMolecule.from_molecule` | focus: OpenMM boundary conversion helper behavior.

## Behavior checks (targeted tests)
- `openff/toolkit/_tests/test_molecule.py` | tests: `test_atom_metadata`, `test_from_pdb_metadata`, `test_from_pdb_t4_atom_metadata` | validates atom/residue metadata semantics.
- `openff/toolkit/_tests/test_topology.py` | tests: `test_from_openmm_virtual_sites`, `test_from_to_openmm_hierarchy_metadata`, `test_to_openmm_assign_unique_atom_names` | validates conversion and virtual-site handling boundaries.
- `openff/toolkit/_tests/test_parameters.py` | focus: `TestVirtualSiteHandler` suite | validates virtual-site parameter matching and name/match policy behavior.

## Quick validation commands
- `python -c "from openff.toolkit import Molecule; mol=Molecule.from_smiles('CCO'); mol.metadata['residue_name']='LIG'; mol.metadata['residue_number']='1'; mol.metadata['chain_id']='A'; print(mol.to_rdkit().GetNumAtoms())"`
- `pytest openff/toolkit/_tests/test_molecule.py -k "atom_metadata or from_pdb_metadata" -q`
- `pytest openff/toolkit/_tests/test_topology.py -k "virtual_sites or hierarchy_metadata or assign_unique_atom_names" -q`
