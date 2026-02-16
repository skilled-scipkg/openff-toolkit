# openff-toolkit source map: API and Scripting

Generated from source roots:
- `openff/toolkit`

Use this map only after exhausting the topic docs in `doc_map.md`.

## Fast source navigation
- `rg -n "ToolkitRegistry|toolkit_registry_manager|registered_toolkit_versions|resolve|call" openff/toolkit/utils`
- `rg -n "toolkit_registry" openff/toolkit/topology/molecule.py openff/toolkit/typing/engines/smirnoff/forcefield.py`

## Function-level source entry points
- `openff/toolkit/utils/toolkit_registry.py` | symbols: `ToolkitRegistry.call`, `ToolkitRegistry.resolve`, `ToolkitRegistry.register_toolkit`, `ToolkitRegistry.deregister_toolkit`, `ToolkitRegistry.registered_toolkit_versions`, `toolkit_registry_manager` | focus: API dispatch and wrapper precedence control.
- `openff/toolkit/utils/toolkits.py` | symbols: `GLOBAL_TOOLKIT_REGISTRY` | focus: default global registry used by high-level scripting APIs.
- `openff/toolkit/topology/molecule.py` | symbols: `Molecule.from_smiles`, `Molecule.to_smiles`, `Molecule.assign_partial_charges`, `Molecule.generate_conformers` | focus: script-level calls that depend on selected toolkit wrappers.
- `openff/toolkit/typing/engines/smirnoff/forcefield.py` | symbols: `ForceField.create_openmm_system`, `ForceField.create_interchange` | focus: registry-aware parametrization behavior in workflows.
- `openff/toolkit/utils/rdkit_wrapper.py`, `openff/toolkit/utils/ambertools_wrapper.py`, `openff/toolkit/utils/openeye_wrapper.py` | symbols: wrapper classes | focus: backend-specific call implementations.

## Behavior checks (targeted tests)
- `openff/toolkit/_tests/test_toolkits.py` | tests: `TestToolkitRegistry::test_toolkit_versions`, `TestToolkitRegistry::test_call_raise_first_error`, `TestToolkitRegistryManager::test_openeye_registry` | validates dispatch and override semantics.
- `openff/toolkit/_tests/test_forcefield.py` | tests: `test_toolkit_registry_no_charge_methods`, `test_toolkit_registry_bad_charge_method` | validates error handling when wrapper capabilities are constrained.

## Quick validation commands
- `python -c "from openff.toolkit import Molecule, ToolkitRegistry, RDKitToolkitWrapper, AmberToolsToolkitWrapper; registry=ToolkitRegistry([RDKitToolkitWrapper, AmberToolsToolkitWrapper]); mol=Molecule.from_smiles('CCO'); print(registry.call('to_smiles', mol))"`
- `pytest openff/toolkit/_tests/test_toolkits.py -k "call_raise_first_error or toolkit_versions or openeye_registry" -q`
- `pytest openff/toolkit/_tests/test_forcefield.py -k "toolkit_registry_no_charge_methods or toolkit_registry_bad_charge_method" -q`
