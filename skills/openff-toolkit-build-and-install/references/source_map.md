# openff-toolkit source map: Build and Install

Generated from source roots:
- `openff/toolkit`

Use this map only after exhausting the topic docs in `doc_map.md`.

## Fast source navigation
- `rg -n "ToolkitRegistry|GLOBAL_TOOLKIT_REGISTRY|register_toolkit|deregister_toolkit" openff/toolkit/utils`
- `rg -n "class (RDKitToolkitWrapper|AmberToolsToolkitWrapper|OpenEyeToolkitWrapper)" openff/toolkit/utils`

## Function-level source entry points
- `openff/toolkit/utils/toolkit_registry.py` | symbols: `ToolkitRegistry.register_toolkit`, `ToolkitRegistry.deregister_toolkit`, `ToolkitRegistry.registered_toolkit_versions`, `ToolkitRegistry.call`, `toolkit_registry_manager` | focus: installed toolkit discovery, precedence, and deterministic dispatch.
- `openff/toolkit/utils/toolkits.py` | symbols: `GLOBAL_TOOLKIT_REGISTRY` | focus: default registry assembly exposed through the public API.
- `openff/toolkit/utils/rdkit_wrapper.py` | symbols: `RDKitToolkitWrapper` | focus: RDKit availability and wrapper capabilities.
- `openff/toolkit/utils/ambertools_wrapper.py` | symbols: `AmberToolsToolkitWrapper` | focus: AmberTools wrapper availability and charge/typing support surface.
- `openff/toolkit/utils/openeye_wrapper.py` | symbols: `OpenEyeToolkitWrapper`, `requires_openeye_module` | focus: OpenEye gating and license/module failure behavior.

## Behavior checks (targeted tests)
- `openff/toolkit/_tests/test_toolkits.py` | tests: `TestToolkitRegistry::test_toolkit_versions`, `TestToolkitRegistry::test_deregister_toolkit`, `TestToolkitRegistryManager::test_openeye_registry` | validates registry composition, ordering, and scoped overrides.
- `openff/toolkit/_tests/test_toolkits.py` | test: `test_license_check` | validates OpenEye license failure handling.

## Quick validation commands
- `python -c "from openff.toolkit import GLOBAL_TOOLKIT_REGISTRY; print(GLOBAL_TOOLKIT_REGISTRY.registered_toolkit_versions)"`
- `pytest openff/toolkit/_tests/test_toolkits.py -k "toolkit_versions or deregister_toolkit or openeye_registry" -q`
