# openff-toolkit source map: Examples and Tutorials

Generated from source roots:
- `openff/toolkit`

Use this map only after exhausting the topic docs in `doc_map.md`.

## Fast source navigation
- `rg -n "create_openmm_system|create_interchange|label_molecules" openff/toolkit/typing/engines/smirnoff/forcefield.py`
- `rg -n "from_file|generate_conformers|to_file|to_rdkit|assign_partial_charges" openff/toolkit/topology/molecule.py`
- `rg -n "test_examples|find_example_scripts|run_script_file" openff/toolkit/_tests/test_examples.py`

## Function-level source entry points
- `openff/toolkit/typing/engines/smirnoff/forcefield.py` | symbols: `ForceField.create_openmm_system`, `ForceField.create_interchange`, `ForceField.label_molecules` | focus: runtime backend behind most simulation-oriented examples.
- `openff/toolkit/typing/engines/smirnoff/parameters.py` | symbols: `ParameterHandler.add_parameter`, `ParameterHandler.find_matches` | focus: assigned-parameter inspection and parameter-edit examples.
- `openff/toolkit/typing/engines/smirnoff/io.py` | symbols: `XMLParameterIOHandler.parse_file`, `XMLParameterIOHandler.to_file` | focus: OFFXML round-trip behavior used in modification/export tutorials.
- `openff/toolkit/topology/molecule.py` | symbols: `Molecule.from_file`, `Molecule.generate_conformers`, `Molecule.to_file`, `Molecule.to_rdkit` | focus: common data-loading and conformer workflows used by examples.
- `openff/toolkit/utils/_viz.py` | symbols: `MoleculeNGLViewTrajectory`, `TopologyNGLViewStructure` | focus: visualization hooks used by notebook examples.

## Behavior checks (targeted tests)
- `openff/toolkit/_tests/test_examples.py` | tests: `test_examples`, `test_readme_examples` | validates runnable script and README snippets.
- `openff/toolkit/_tests/test_parameters.py` | tests: `test_add_parameter`, `test_find_matches` | validates parameter-inspection and matching behavior that examples rely on.

## Quick validation commands
- `python examples/conformer_energies/conformer_energies.py --filename openff/toolkit/data/molecules/ruxolitinib_conformers.sdf`
- `pytest openff/toolkit/_tests/test_examples.py -k "test_examples" -q`
- `pytest openff/toolkit/_tests/test_parameters.py -k "add_parameter or find_matches" -q`
