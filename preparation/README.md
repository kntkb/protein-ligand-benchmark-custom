# Preparation details
Maestro from Schrodinger2022-2 was used to generate and prepare the initial structures of protein and the ligand.


### 1. Protein preparation: Protein preparation wizard
**Import and Process**
- Assign bond orders (Use CCD database)
- Add hydrogens
- Create zero-order bonds to metals
- Create disulfide bonds
- Fill in missing side chains using Prime
- Fill in missing loops using Prime
- Cap termini
- Delete waters beyond 5.00 Angstroms from het groups
- Generate het states using Epik (pH: 7.0+/-2.0)

If mulitple occupancy for atom/residue exists, then the highest coordinate with the highest occupancy is chosen.

**Review and Modify**
- Run analyze workspace
- Check Het atoms/residues if present and manually inspect the states. Choose the most reasonable state from human perspective.

**Refine**
1. H-bond assignment (Optimize)
- Sample water orentations
- Use PROPKA pH: 7.0

2. Remove waters
- Beyond hets 3.0 Angstorms

3. Restrained minimization
- Converge heavy atoms to RMSD: 0.30 Angstroms
- Force field: OPLS4

**Split moleucles**: Split minizmized complex structure into protein, ligands, water, and others using Maestro
- Export protein structure as `protein.pdb`

### 2. Ligand preparation
**LigPrep**: Load ligand file and generate possible ionization/tautomer states using ligprep (default setting)
- Force field: OPLS4
- Generate possible states at target pH: 7.0+/-2.0 using Epik
- Desalt
- Generate tautomers
- Stereoisomer computaion: Retrain specified chilarities (vary other chiral centers)
- Generate at most 32 per ligands

**Inspect ligand moleulces**
- Visualyl inspect ligand molecules and choose the reasonable ligand state from human perspective.


**Ligand alignment**: Align all ligands to reference structures (default: ligand from minimized complex structure) using `Ligand Alignment` module in Maestro
- Constraint common substructure: Largest common Bemis-Murcko scaffold or MCS (choose the one that best aligns)
- Sampling method: Thorough
- Maximum number of conformers: 1000
- Nonbonded close contact distance: 0.5 Angstroms
- Run energy minimization for each conformer


**Fine-tune ligand poses**
- Manually modify ligand (e.g. orienations or substituent torsions) if necessary.
- If atoms are modified, run `Minimize Selected Atoms` and export ligands as `ligands.sdf`


### 3. Mapping network
Ligand transformation network is define manually by human experts where transformations are grouped into categories to resemble different SAR purposes.



