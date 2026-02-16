# Evidence: openff-toolkit-build-and-install

## Primary docs
- `examples/deprecated/liquid_box/create_mol2_pdb/README.md`
- `docs/installation.md`

## Primary source entry points
- `skills/openff-toolkit-build-and-install/references/doc_map.md`
- `openff/toolkit/_tests/create_molecules.py`
- `openff/toolkit/__init__.py`
- `openff/toolkit/utils/__init__.py`
- `openff/toolkit/typing/__init__.py`
- `openff/toolkit/topology/__init__.py`
- `openff/toolkit/typing/engines/__init__.py`
- `openff/toolkit/typing/engines/smirnoff/__init__.py`
- `openff/toolkit/_tests/__init__.py`
- `openff/toolkit/_tests/molecule/__init__.py`
- `openff/toolkit/typing/engines/smirnoff/forcefield.py`
- `openff/toolkit/utils/utils.py`
- `openff/toolkit/utils/toolkits.py`
- `openff/toolkit/utils/toolkit_registry.py`
- `openff/toolkit/utils/serialization.py`
- `openff/toolkit/utils/rdkit_wrapper.py`
- `openff/toolkit/utils/openeye_wrapper.py`
- `openff/toolkit/utils/nagl_wrapper.py`
- `openff/toolkit/utils/exceptions.py`
- `openff/toolkit/utils/constants.py`

## Extracted headings
- Contact:
- Description:
- Dependencies:
- Installation
- Installing via `mamba`
- OS support
- Installing from source
- Optional dependencies (toolkits)
- RDKit
- AmberTools
- OpenEye
- Check installed toolkits

## Executable command hints
- $ mamba create -n openff-toolkit -c conda-forge openff-toolkit
- $ mamba activate openff-toolkit
- $ cd openff-toolkit
- $ python -m pip install .
- $ mamba install -c openeye openeye-toolkits

## Warnings and pitfalls
- (none extracted)
