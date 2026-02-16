# Evidence: openff-toolkit-api-and-scripting

## Primary docs
- `docs/releasehistory.md`
- `docs/api/toolkits.md`
- `docs/_templates/autosummary/class.rst`

## Primary source entry points
- `skills/openff-toolkit-api-and-scripting/references/doc_map.md`
- `openff/toolkit/utils/toolkits.py`
- `openff/toolkit/_tests/test_toolkits.py`
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
- `openff/toolkit/utils/toolkit_registry.py`
- `openff/toolkit/utils/serialization.py`
- `openff/toolkit/utils/rdkit_wrapper.py`
- `openff/toolkit/utils/openeye_wrapper.py`
- `openff/toolkit/utils/nagl_wrapper.py`
- `openff/toolkit/utils/exceptions.py`
- `openff/toolkit/utils/constants.py`

## Extracted headings
- Release History
- Current development
- API-breaking changes
- Behavior changes
- Bugfixes
- New features
- Improved documentation and warnings
- Testing improvements
- 0.18.0
- 0.17.1
- Toolkit Wrappers and Registries

## Executable command hints
- (none extracted)

## Warnings and pitfalls
- - [PR #2039](https://github.com/openforcefield/openff-toolkit/pull/2039): Prevent an error displaying a `Molecule` in IPython when `nglview` is not installed.
- - [PR #1965](https://github.com/openforcefield/openff-toolkit/pull/1965): Disables testing of parmed-dependent notebook in `external` examples, since ParmEd 3 is no longer compatible with our upstreams and ParmEd 4 raises an error for our use cases.
- - [PR ##1986](https://github.com/openforcefield/openff-toolkit/pull/1986): Fix links in PR template and formatted string in error
- - [PR #1957](https://github.com/openforcefield/openff-toolkit/pull/1957): Fixed a misleading typo in an error message.
- - [PR #1939](https://github.com/openforcefield/openff-toolkit/pull/1939): Resolves [#1587](https://github.com/openforcefield/openff-toolkit/pull/1587) by emitting a warning when from_openeye or from_rdkit try to load a molecule with multiple disconnected components.
- - [PR #1705](https://github.com/openforcefield/openff-toolkit/pull/1705): Do not raise warning when `allow_undefined_stereo=True`.
- - [PR #1726](https://github.com/openforcefield/openff-toolkit/pull/1726): Fix error message in setting `scale12`, `scale13`, and `scale15` attributes.
- - [PR #1690](https://github.com/openforcefield/openff-toolkit/pull/1690): Fixes a circular-import bug that occurs when attempting to print a "no cheminformatics toolkits available" warning.
- - [PR #1654](https://github.com/openforcefield/openff-toolkit/pull/1654): Fixes issue [#1653](https://github.com/openforcefield/openff-toolkit/issues/1653), where a test that expected RDKit to fail began returning an error when RDKit became able to generate conformers for octahedral molecules.
- - [PR #1619](https://github.com/openforcefield/openff-toolkit/pull/1619): Fixes **silent error** [#1618](https://github.com/openforcefield/openff-toolkit/issues/1618), by making partial_charges.setter more comprehensive in type and shape checking.
- - [PR #1591](https://github.com/openforcefield/openff-toolkit/pull/1591): Fixes [#1563](https://github.com/openforcefield/openff-toolkit/issues/1563), where `from_rdkit` would sometimes raise an error about radicals if a molecule using a non-MDL aromaticity model was provided.
- - [PR #1513](https://github.com/openforcefield/openff-toolkit/pull/1513): Improves error messages and documentation around supported aromaticity models (currently only "OEAroModel_MDL").
