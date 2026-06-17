# HOW TO on LAMMPS
1) For endpoints the respective potential
2) use reftraj on the generated trajectory, and rerun with the opposite potential
3) evaluate the gap
4) for intermediate, say 0.5, use hybrid/scaled to generate the trajectory, then rerun twice for each endpoints potential
5) in case of you train with datatype  1 2 3 4 for X F O H, during the Ti you need to switch from X to H. In this case, you cant change the atom type to 3 as you did where X is train as type 4
6) instead, keep the datatype as 4 but change the X type to H (1 to 4), and in the input file, do not disable it. Since the type 1 or X is not exist, Lammps still run (order of datatype is presented), but does not count it since its not exist
7) as lmp file build with atomsk only care about the different between element, in case for the same model that know 1 2 3 4 for X F O H, while you only have O H (for hydronium), just create a random element for X and F so the lmp will be ordered as 1 for X, 2 for F, etc, once the lmp is build, you can delete it, and do similar to number 5-6

# RECIPE
1) Input
2) topology.lmp
3) nnp.pb
4) run.sh
NOTE : check pair_style, end point pair_coeff * *, ensure the topology consistent with the number

### TOPOLOGY
1) use xyz file and install atomsk
```bash
atomsk system.xyz lmp
```
2) edit the xhi,yhi,zhi similar to the CELL on the input cp2k
3) check the unit, number of atom, etc
4) to make it similar to the order of model list, arrange the atom in xyz file as the order of model list

### REFTRAJ-ENDPOINTS
1) copy input and dump to REFTRAJ, edit the mass commented or out commented based on the opposite topology
2) Edit the pair_style match to the opposite potential
3) Edit the last
```bash
rerun ./surface_2.dump first 0 every 1 dump x y z
```
---
4) Disable the restart. Just in case one want to dump the file then change the name so it will not the same
```bash
dump  1 all custom 1 revt_surface_2.dump id type x y z
```
---
6) copy the opposite potential NNP and topo lmp file to the current REFTRAJ dir
7) Apply the post-processing code, for initial endpoints (to sparse the output match to the dump used in reftraj)
8) On the REFTRAJ, use post-processing, with none sparse, the output will be extracted_data


# DFT
use gap_eval to evaluate the gap of mix energy $5-$4

### REFTRAJ-INTERMEDIATE
1) First run for the intermediate, first generate the trajectory at those configuration and run REFTRAJ twice REFTRAJ_D and REFTRAJ_D
2) For example 0,5
```bash
pair_style  hybrid/scaled 1.00 deepmd ave_lambda0.pb 0.00 deepmd ave_lambda1.pb
```
---
3) For example 0,25
```bash
pair_style  hybrid/scaled 0.75 deepmd ave_lambda0.pb 0.25 deepmd ave_lambda1.pb
```
---
4) For example 0,75
```bash
pair_style   hybrid/scaled 0.75 deepmd ave_lambda0.pb 0.25 deepmd ave_lambda1.pb
```
---

 this going to be generate the configuration at particular intermediate state 
