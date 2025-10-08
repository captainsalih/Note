# HOW TO
1) For endpoints the respective potential
2) use reftraj on the generated trajectory, and rerun with the opposite potential
3) evaluate the gap
4) for intermediate, say 0.5, use hybrid/scaled to generate the trajectory, then rerun twice for each endpoints potential

# RECIPE
1) Input
2) topology.lmp
3) nnp.pb
4) run.sh
NOTE : check pair_style, end point pair_coeff * *, ensure the topology consistent with the number

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
