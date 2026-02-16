# openff-toolkit source map: Inputs and Modeling

Generated from source roots:
- `openff/toolkit`

Use this map only after exhausting the topic docs in `doc_map.md`.

## Fast source navigation
- `rg -n "create_openmm_system|create_interchange|label_molecules|register_parameter_handler|get_parameter_handler" openff/toolkit/typing/engines/smirnoff/forcefield.py`
- `rg -n "class (vdWHandler|ElectrostaticsHandler|LibraryChargeHandler|ChargeIncrementModelHandler|VirtualSiteHandler)" openff/toolkit/typing/engines/smirnoff/parameters.py`

## Function-level source entry points
- `openff/toolkit/typing/engines/smirnoff/forcefield.py` | symbols: `ForceField.parse_sources`, `ForceField.get_parameter_handler`, `ForceField.register_parameter_handler`, `ForceField.deregister_parameter_handler`, `ForceField.create_openmm_system`, `ForceField.create_interchange`, `ForceField.label_molecules` | focus: end-to-end parametrization and system creation.
- `openff/toolkit/typing/engines/smirnoff/parameters.py` | symbols: `ParameterHandler.add_parameter`, `ParameterHandler.find_matches`, `vdWHandler`, `ElectrostaticsHandler`, `LibraryChargeHandler`, `ChargeIncrementModelHandler`, `VirtualSiteHandler` | focus: handler-level matching and parameter semantics.
- `openff/toolkit/typing/engines/smirnoff/io.py` | symbols: `XMLParameterIOHandler.parse_file`, `XMLParameterIOHandler.parse_string`, `XMLParameterIOHandler.to_file`, `XMLParameterIOHandler.to_string` | focus: OFFXML read/write and schema translation behavior.
- `openff/toolkit/typing/engines/smirnoff/plugins.py` | symbols: `load_handler_plugins` | focus: custom handler plugin loading path.

## Behavior checks (targeted tests)
- `openff/toolkit/_tests/test_forcefield.py` | tests: `test_load_two_sources`, `test_deregister_parameter_handler`, `test_pass_invalid_kwarg_to_create_openmm_system`, `test_charge_increment_model_forward_and_reverse_ethanol` | validates source loading, handler lifecycle, and system creation behavior.
- `openff/toolkit/_tests/test_energies.py` | test: `test_reference` | validates energy regression against reference data.
- `openff/toolkit/_tests/test_parameter_plugins.py` | tests: `test_force_field_custom_handler`, `test_load_handler_plugins` | validates plugin registration behavior.

## Quick validation commands
- `python -c "from openff.toolkit import Molecule, ForceField; mol=Molecule.from_smiles('CCO'); mol.generate_conformers(n_conformers=1); ff=ForceField('openff-2.1.0.offxml'); print(ff.create_openmm_system(mol.to_topology()).getNumParticles())"`
- `pytest openff/toolkit/_tests/test_forcefield.py -k "create_openmm_system or deregister_parameter_handler or charge_increment_model" -q`
- `pytest openff/toolkit/_tests/test_energies.py::test_reference -q`
