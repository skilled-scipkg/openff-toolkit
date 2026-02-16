# Evidence: openff-toolkit-examples-and-tutorials

## Primary docs
- `examples/deprecated/chemicalEnvironments/README.md`
- `examples/README.md`
- `examples/visualization/README.md`
- `examples/using_smirnoff_in_amber_or_gromacs/README.md`
- `examples/inspect_assigned_parameters/README.md`
- `examples/deprecated/testing/README.md`
- `examples/deprecated/partial_bondorder/README.md`
- `examples/deprecated/check_dataset_parameter_coverage/README.md`
- `examples/deprecated/testing/test_system_conversion/README.md`
- `examples/deprecated/testing/test_impropers/README.md`
- `docs/examples.md`
- `examples/deprecated/chemicalEnvironments/moveTrees.uniq.VdW.txt`

## Primary source entry points
- `skills/openff-toolkit-examples-and-tutorials/references/doc_map.md`
- `openff/toolkit/typing/engines/smirnoff/parameters.py`
- `openff/toolkit/_tests/test_parameters.py`
- `openff/toolkit/typing/engines/smirnoff/__init__.py`
- `openff/toolkit/typing/engines/smirnoff/forcefield.py`
- `openff/toolkit/typing/engines/smirnoff/plugins.py`
- `openff/toolkit/typing/engines/smirnoff/io.py`
- `openff/toolkit/_tests/test_parameter_plugins.py`
- `openff/toolkit/utils/ambertools_wrapper.py`

## Extracted headings
- `ChemicalEnvironment` usage examples
- Demo jupyter notebook
- Creating a `ChemicalEnvironment`
- ANDtypes and ORtypes
- New Atom 1: [#6X3,#7X2;+0:1]
- Change atom2's AND and OR types with the add*type methods
- New Atom 2: [#8,#7+0X3;R1:2]
- SMIRKS Before Changes: '[#6X3,#7;+0:1]~;@[#8;r:2]~;@[#6X3,#7;+0:3]'
- New SMIRKS: '[#6X3,#7X2:1]~;@[#8,#7+0X3;R1:2]~;@[#6X3,#7:3]'
- Adding and removing atoms
- Examples using SMIRNOFF with the toolkit
- Index of provided examples

## Executable command hints
- (none extracted)

## Warnings and pitfalls
- (none extracted)
