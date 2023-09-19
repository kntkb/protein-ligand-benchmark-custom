# Free Energy Benchmark Systems for Small molecules
A set of benchmark systems to validate `Espaloma` force field. This repository was obtained from [OpenFF protein-ligand-benchmark](https://github.com/openforcefield/protein-ligand-benchmark/tree/d3387602bbeb0167abf00dfb81753d8936775dd2) repository (commit hash: d3387602bbeb0167abf00dfb81753d8936775dd2)



## Summary
Summary of the contents of the Protein-Ligand Benchmark Dataset. It contains the available protein targets with corresponding PDB ID and number of ligands.

| Target    |  PDB |# Ligands| # Edges |
| --------- |:----:|--------:|--------:|
| tyk2      | 4GIH | 13      | 12      |
| mcl1      | 4HW3 | 25      | 24      |
| cdk2      | 1H1Q | 10      | 9       |
| p38       | 3FLY | 28      | 27      |


## Note
Note that `ligand_p38a_2ff` from P38 was excluded from the original dataset because of its ambigous stereochemistry.
The experimental result for `ligand_p38a_2ff` is stored in `ligands.yml` as a record.