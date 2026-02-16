# Evidence: openff-toolkit-inputs-and-modeling

## Primary docs
- `examples/deprecated/mixedFF_structure/README.md`
- `docs/index.md`
- `examples/deprecated/SMIRNOFF_comparison/README.md`
- `examples/deprecated/host_guest_simulation/README.md`
- `examples/using_smirnoff_with_amber_protein_forcefield/README.md`
- `examples/toolkit_showcase/README.md`
- `examples/forcefield_modification/README.md`
- `examples/conformer_energies/README.md`
- `docs/typing.rst`
- `docs/users/smirnoff.md`

## Primary source entry points
- `skills/openff-toolkit-inputs-and-modeling/references/doc_map.md`
- `openff/toolkit/typing/engines/smirnoff/forcefield.py`
- `openff/toolkit/typing/engines/smirnoff/__init__.py`
- `openff/toolkit/typing/engines/smirnoff/plugins.py`
- `openff/toolkit/typing/engines/smirnoff/parameters.py`
- `openff/toolkit/typing/engines/smirnoff/io.py`
- `openff/toolkit/_tests/test_forcefield.py`
- `openff/toolkit/typing/__init__.py`
- `openff/toolkit/typing/engines/__init__.py`
- `openff/toolkit/_tests/test_energies.py`
- `openff/toolkit/utils/ambertools_wrapper.py`
- `openff/toolkit/__init__.py`
- `openff/toolkit/utils/__init__.py`
- `openff/toolkit/topology/__init__.py`
- `openff/toolkit/_tests/__init__.py`
- `openff/toolkit/_tests/molecule/__init__.py`
- `openff/toolkit/utils/utils.py`
- `openff/toolkit/utils/toolkits.py`
- `openff/toolkit/utils/toolkit_registry.py`
- `openff/toolkit/utils/serialization.py`

## Extracted headings
- Combining a SMIRNOFF parameterized small molecule with an AMBER parameterized protein using ParmEd
- Load the small molecule
- Load the smirnoff99Frosst force field
- Create a ParmEd structure for the molecule
- Load the protein topology
- Load the AMBER protein force field, along with a solvent force field
- Parameterize the protein
- TODO: Can we create an OpenMM ffxml file for the ligand?
- Create a ParmEd Structure for the protein
- Combine the ParmEd Structure objects to produce a fully parameterized complex
- Open Force Field Toolkit
- Compare small molecule parm@frosst energies between SMIRNOFF and AMBER `prmtop/inpcrd`

## Executable command hints
- (none extracted)

## Warnings and pitfalls
- (none extracted)
